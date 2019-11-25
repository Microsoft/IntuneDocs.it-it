---
title: Configurare Microsoft Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Usare Intune On-Premises Connector per Exchange per gestire l'accesso dei dispositivi alle cassette postali di Exchange in base alla registrazione in Intune e a Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 62db99fc2e47bdfa1a767db3bb2916649dedc074
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164699"
---
# <a name="set-up-the-on-premises-intune-exchange-connector"></a>Configurare Intune On-Premises Connector per Exchange
Per proteggere l'accesso a Exchange, Intune si affida a un componente locale noto come Microsoft Intune Exchange Connector. Questo connettore è denominato anche *connettore locale per Exchange ActiveSync* in alcune posizioni della console di Intune. 

Le informazioni contenute in questo articolo possono essere utili per installare e monitorare Intune Exchange Connector. È possibile usare il connettore con i [criteri di accesso condizionale](conditional-access-exchange-create.md) per consentire o bloccare l'accesso alle cassette postali locali di Exchange. 

Il connettore viene installato ed eseguito nell'hardware locale. Individua i dispositivi che si connettono a Exchange, comunicando le relative informazioni al servizio Intune. Il connettore consente o blocca i dispositivi a seconda se sono registrati e conformi. Queste comunicazioni usano il protocollo HTTPS.

Quando un dispositivo tenta di accedere a Exchange Server locale, Exchange Connector esegue il mapping dei record di Exchange Active Sync (EAS) in Exchange Server ai record di Intune per verificare che il dispositivo sia registrato con Intune e conforme ai criteri del dispositivo. In base ai criteri di accesso condizionale, è possibile consentire o bloccare il dispositivo. Per altre informazioni, vedere [Quali sono i modi comuni per usare l'accesso condizionale con Intune?](conditional-access-intune-common-ways-use.md)

Le operazioni di *individuazione* e *consenso e blocco* vengono eseguite usando i cmdlet Exchange standard di PowerShell. Queste operazioni usano l'account del servizio specificato durante l'installazione iniziale di Exchange Connector. 

Intune supporta l'installazione di più istanze di Intune Exchange Connector per ogni sottoscrizione. Se si hanno più organizzazioni di Exchange locali, è possibile configurare un connettore separato per ognuna di esse. Tuttavia, è possibile installare un solo connettore per ogni organizzazione di Exchange.  

Seguire questi passaggi generali per configurare una connessione che consente a Intune di comunicare con l'istanza di Exchange Server locale:

1. Scaricare il connettore locale dal portale di Intune.
2. Installare e configurare Exchange Connector in un computer dell'organizzazione di Exchange locale.
3. Convalidare la connessione di Exchange.
4. Ripetere i passaggi per ogni organizzazione di Exchange aggiuntiva che si vuole connettere a Intune.

## <a name="intune-exchange-connector-requirements"></a>Requisiti per Intune Exchange Connector

Per connettersi a Exchange, è necessario un account che ha una licenza di Intune che può essere usata dal connettore. L'account viene specificato quando si installa il connettore.  

Nella tabella seguente sono indicati i requisiti per il computer in cui viene installato Intune Exchange Connector.  

|  Requisito  |   Altre informazioni     |
|---------------|------------------------|
|  Sistemi operativi        | Intune supporta Intune Exchange Connector in computer che eseguono qualsiasi edizione di Windows Server 2008 SP2 a 64 bit, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 o Windows Server 2016.<br /><br />Il connettore non è supportato in tutte le installazioni Server Core.  |
| Microsoft Exchange          | I connettori locali richiedono Microsoft Exchange 2010 SP3 o versioni successive oppure l'ambiente legacy Exchange Online dedicato. Per determinare se la configurazione dell'ambiente Exchange Online dedicato è *nuova* o *legacy*, contattare l'account manager. |
| Autorità di gestione dei dispositivi mobili           | [Impostare l'autorità di gestione dei dispositivi mobili su Intune](../fundamentals/mdm-authority-set.md). |
| Hardware              | Il computer in cui si installa il connettore richiede una CPU da 1,6 GHz con 2 GB di RAM e 10 GB di spazio libero sul disco. |
|  Sincronizzazione di Active Directory             | Prima di usare il connettore per connettere Intune a Exchange Server, [impostare la sincronizzazione di Active Directory](../fundamentals/users-add.md). Gli utenti e i gruppi di sicurezza locali devono essere sincronizzati con l'istanza di Azure Active Directory. |
| Software aggiuntivo         | Nel computer che ospita il connettore deve essere presente un'installazione completa di Microsoft .NET Framework 4.5 e Windows PowerShell 2.0. |
| Rete               | Il computer in cui si installa il connettore deve essere in un dominio con una relazione di trust con il dominio che ospita l'istanza di Exchange Server.<br /><br />Configurare il computer in modo che sia in grado di accedere al servizio Intune attraverso firewall e server proxy sulle porte 80 e 443. Intune usa questi domini: <br> - manage.microsoft.com <br> - \*manage.microsoft.com<br> - \*.manage.microsoft.com <br><br> Intune Exchange Connector comunica con i servizi seguenti: <br> - Servizio Intune: Porta HTTPS 443 <br> - Server Accesso client di Exchange (CAS): Porta del servizio WinRM 443<br> - Individuazione automatica di Exchange 443<br> - Servizi Web Exchange (EWS) 443  |

### <a name="exchange-cmdlet-requirements"></a>Requisiti dei cmdlet di Exchange

Creare un account utente di Active Directory per Intune Exchange Connector. L'account deve avere le autorizzazioni per eseguire i cmdlet Exchange di Windows PowerShell elencati di seguito:  

- `Get-ActiveSyncOrganizationSettings`, `Set-ActiveSyncOrganizationSettings`
- `Get-CasMailbox`, `Set-CasMailbox`
- `Get-ActiveSyncMailboxPolicy`, `Set-ActiveSyncMailboxPolicy`, `New-ActiveSyncMailboxPolicy`, `Remove-ActiveSyncMailboxPolicy`
- `Get-ActiveSyncDeviceAccessRule`, `Set-ActiveSyncDeviceAccessRule`, `New-ActiveSyncDeviceAccessRule`, `Remove-ActiveSyncDeviceAccessRule`
- `Get-ActiveSyncDeviceStatistics`
- `Get-ActiveSyncDevice`
- `Get-ExchangeServer`
- `Get-ActiveSyncDeviceClass`
- `Get-Recipient`
- `Clear-ActiveSyncDevice`, `Remove-ActiveSyncDevice`
- `Set-ADServerSettings`
- `Get-Command`

## <a name="download-the-installation-package"></a>Scaricare il pacchetto di installazione

In un server Windows in grado di supportare Intune Exchange Connector:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).  Usare un account che sia un amministratore nell'istanza di Exchange Server locale e abbia una licenza per l'uso di Exchange Server.

2. Selezionare **Amministrazione del tenant** > **Accesso ad Exchange**.  

3. In **Installazione** scegliere **Connettore locale per Exchange ActiveSync** e quindi selezionare **Aggiungi**.

4. Nella pagina **Aggiungi il connettore** selezionare **Scaricare il connettore locale**. Intune Exchange Connector è contenuto in una cartella compressa (ZIP) che può essere aperta o salvata. Nella finestra di dialogo **Download del file** scegliere **Salva** per archiviare la cartella compressa in una posizione protetta.

## <a name="install-and-configure-the-intune-exchange-connector"></a>Installare e configurare Intune Exchange Connector

Per installare Intune Exchange Connector, seguire questa procedura. Se sono presenti più organizzazioni di Exchange, ripetere questi passaggi per ogni Exchange Connector da configurare.

1. In un sistema operativo supportato per Intune Exchange Connector estrarre i file inclusi in **Exchange_Connector_Setup.zip** in un percorso protetto.
   > [!IMPORTANT]
   > Non rinominare o spostare i file della cartella *Exchange_Connector_Setup*. Queste operazioni causerebbero l'esito negativo dell'installazione del connettore.

2. Dopo aver estratto i file, aprire la cartella estratta e fare doppio clic su **Exchange_Connector_Setup.exe** per installare il connettore.

   > [!IMPORTANT]
   > Se la cartella di destinazione non è una posizione sicura, al termine dell'installazione dei connettori locali eliminare il file di certificato *MicrosoftIntune.accountcert*.

3. Nella finestra di dialogo **Microsoft Intune Exchange Connector** selezionare **Microsoft Exchange Server locale** o **Microsoft Exchange Server ospitato**.

   ![Immagine che illustra dove scegliere il tipo di Exchange Server](./media/exchange-connector-install/intune-sa-exchange-connector-config.png)

   Per un server Exchange locale specificare il nome del server o il nome di dominio completo del server Exchange in cui è ospitato il ruolo **Server Accesso client**.

   Per un server Exchange ospitato, specificare l'indirizzo del server Exchange. Per trovare l'URL del server Exchange ospitato:

   1. Aprire Outlook per Office 365.

   2. Scegliere l'icona **?** in alto a sinistra e quindi selezionare **Informazioni su**.

   3. Individuare il valore di **Server esterno POP** .

   4. Scegliere **Server Proxy** per specificare le impostazioni del server proxy per il server Exchange ospitato.

       1. Selezionare **Utilizza un server proxy per la sincronizzazione delle informazioni del dispositivo mobile**.

       1. Immettere il **nome del server proxy** e il **numero di porta** da usare per accedere al server.

       1. Se sono richieste le credenziali utente per accedere al server proxy, selezionare **Utilizzare le credenziali per connettersi al server proxy** e quindi immettere **dominio\utente** e **password**.

       1. Scegliere **OK**.

4. Nei campi **Utente (dominio\utente)** e **Password** immettere le credenziali per la connessione a Exchange Server. L'account specificato deve avere una licenza per l'uso di Intune. 

5. Specificare le credenziali per l'invio delle notifiche alla cassetta postale di Exchange Server di un utente. L'utente può essere dedicato solo alle notifiche. L'utente delle notifiche deve avere una cassetta postale di Exchange per inviare le notifiche tramite posta elettronica. È possibile configurare queste notifiche usando i criteri di accesso condizionale in Intune.  

   Verificare che il servizio di individuazione automatica e i servizi Web Exchange siano configurati nel server CAS di Exchange. Per altre informazioni, vedere [Server Accesso client](https://technet.microsoft.com/library/dd298114.aspx).

6. Nel campo **Password** specificare la password per questo account, per abilitare Intune all'accesso a Exchange Server.

   > [!NOTE]
   > L'account usato per accedere al tenant deve essere almeno un amministratore del servizio Intune. Senza questo account amministratore, si otterrà una connessione non riuscita con il messaggio "Errore del server remoto: (400) Richiesta non valida".

7. Scegliere **Connetti**.

   > [!NOTE]
   > La configurazione della connessione può richiedere alcuni minuti.

Durante la configurazione, le impostazioni proxy vengono memorizzate da Exchange Connector per abilitare l'accesso a Internet. Se le impostazioni proxy cambiano, sarà necessario riconfigurare Exchange Connector per applicare le impostazioni proxy aggiornate.

Dopo che Exchange Connector imposta la connessione, i dispositivi mobili associati agli utenti gestiti in Exchange vengono automaticamente sincronizzati e aggiunti a Exchange Connector. La sincronizzazione potrebbe richiedere parecchio tempo.

> [!NOTE]
> Se si installa Intune Exchange Connector e successivamente è necessario eliminare la connessione a Exchange, il connettore dovrà essere disinstallato dal computer in cui è stato installato.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installare connettori per più organizzazioni di Exchange

Intune supporta più istanze di Intune Exchange Connector per ogni sottoscrizione. Per un tenant con più organizzazioni di Exchange, è possibile impostare un solo connettore per ogni organizzazione di Exchange. 

Per installare i connettori per connettersi a più organizzazioni di Exchange, scaricare la cartella ZIP una volta. Riutilizzare lo stesso download per ogni connettore installato. Per ogni connettore aggiuntivo, seguire la procedura nella sezione precedente per estrarre ed eseguire il programma di installazione in un server nell'organizzazione di Exchange.

Ogni organizzazione di Exchange che si connette a Intune supporta la disponibilità elevata, il monitoraggio e la sincronizzazione manuale. Nelle sezioni seguenti sono descritte tali funzionalità.

## <a name="on-premises-intune-exchange-connector-high-availability-support"></a>Supporto a disponibilità elevata di Intune On-Premises Connector per Exchange  

Per il connettore locale, disponibilità elevata significa che se il server CAS di Exchange usato dal connettore non è più disponibile, il connettore può passare a un altro server CAS per tale organizzazione di Exchange. Exchange Connector non supporta la disponibilità elevata. Se il connettore non riesce, non si verifica alcun failover automatico. È necessario [installare un nuovo connettore](#reinstall-the-intune-exchange-connector) per sostituire il connettore con errore.

Per failover il connettore usa il server CAS specificato per creare una connessione riuscita a Exchange. Individua quindi ulteriori server CAS per l'organizzazione di Exchange. L'individuazione consente al connettore di eseguire il failover a un altro server CAS, finché il server CAS primario non diventa disponibile.

Per impostazione predefinita, l'individuazione di server Accesso client aggiuntivi è abilitata. Se è necessario disattivare il failover:

1. Nel server in cui è installato Exchange Connector, passare a **%*ProgramData*%\Microsoft\Windows Intune Exchange Connector**.

2. Aprire **OnPremisesExchangeConnectorServiceConfiguration.xml** in un editor di testo.

3. Modificare **\<IsCasFailoverEnabled>*true*\</IsCasFailoverEnabled>** to **\<IsCasFailoverEnabled>*false*\</IsCasFailoverEnabled>** .

## <a name="performance-tune-the-exchange-connector-optional"></a>Ottimizzare le prestazioni di Exchange Connector (facoltativo)

Quando Exchange ActiveSync supporta 5000 o più dispositivi, è possibile configurare un'impostazione facoltativa per migliorare le prestazioni del connettore. Il miglioramento delle prestazioni si ottiene consentendo a Exchange di usare più istanze di uno spazio di esecuzione dei comandi di PowerShell.

Prima di apportare questa modifica, verificare che l'account usato per eseguire Exchange Connector non venga usato per altre operazioni di gestione di Exchange. Un account di Exchange ha un numero limitato di spazi di esecuzione e il connettore ne usa la maggior parte.

L'ottimizzazione delle prestazioni non è adatta per i connettori eseguiti su hardware meno recenti o più lenti.

Per migliorare le prestazioni di Exchange Connector:

1. Nel server in cui è installato il connettore aprire la directory di installazione del connettore.  Il percorso predefinito è *C:\Programmi\Microsoft\Windows Intune Exchange Connector*.

2. Modificare il file *OnPremisesExchangeConnectorServiceConfiguration.xml*.

3. Trovare **EnableParallelCommandSupport** e impostare il valore su **true**:

   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>

4. Salvare il file, quindi riavviare il servizio Microsoft Intune Exchange Connector.

## <a name="reinstall-the-intune-exchange-connector"></a>Reinstallare Intune Exchange Connector

Potrebbe essere necessario reinstallare Intune Exchange Connector. Poiché è possibile connettere un solo connettore a ogni organizzazione di Exchange, se si installa un secondo connettore per l'organizzazione, il nuovo connettore installato sostituisce il connettore originale.

1. Per installare il nuovo connettore, seguire i passaggi descritti nella sezione [Installare e configurare Exchange Connector](#install-and-configure-the-intune-exchange-connector).

2. Quando richiesto, selezionare **Sostituisci** per installare il nuovo connettore.
   ![Avviso di configurazione per sostituire un connettore](./media/exchange-connector-install/prompt-to-replace.png)

3. Continuare la procedura della sezione [Installare e configurare Intune Exchange Connector](#install-and-configure-the-intune-exchange-connector) e accedere di nuovo a Intune.

4. Nella finestra finale selezionare **Chiudi** per completare l'installazione.
   ![Completare la configurazione](./media/exchange-connector-install/successful-reinstall.png)

## <a name="monitor-an-exchange-connector"></a>Monitorare Exchange Connector

Dopo aver configurato correttamente Exchange Connector, è possibile visualizzare lo stato delle connessioni e l'ultimo tentativo di sincronizzazione riuscito.

Per convalidare la connessione di Exchange Connector:

1. Nel dashboard di Intune scegliere **Accesso ad Exchange**.

2. Selezionare **Accesso locale a Exchange** per verificare lo stato della connessione per ogni istanza di Exchange Connector.

È inoltre possibile verificare la data e ora dell'ultimo tentativo di sincronizzazione riuscito.

A partire dalla versione 1710 di Intune, è possibile usare [System Center Operations Manager Management Pack per Exchange Connector e Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True), che consente di eseguire il monitoraggio di Exchange Connector in diversi modi quando è necessario risolvere i problemi.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forzare manualmente una sincronizzazione rapida o una sincronizzazione completa

Intune Exchange Connector sincronizza automaticamente EAS e i record dei dispositivi Intune a intervalli regolari. Se viene modificato lo stato di conformità di un dispositivo, il processo di sincronizzazione automatica aggiorna periodicamente i record, in modo che l'accesso al dispositivo possa essere bloccato o consentito.

- La **sincronizzazione rapida** si verifica a intervalli regolari più volte al giorno. Una sincronizzazione rapida recupera le informazioni sul dispositivo relative agli utenti con licenza di Intune e gli utenti di Exchange locale configurati con l'accesso condizionale e che sono cambiate dall'ultima sincronizzazione.

- Per impostazione predefinita la **sincronizzazione completa** viene eseguita una volta al giorno. Una sincronizzazione completa recupera le informazioni sul dispositivo per tutti gli utenti con licenza di Intune e gli utenti di Exchange locale configurati con l'accesso condizionale. Una sincronizzazione completa recupera anche informazioni sul server Exchange e verifica che la configurazione specificata da Intune nel portale di Azure sia aggiornata nel server Exchange.

È possibile forzare un connettore a eseguire una sincronizzazione usando le opzioni **Sincronizzazione rapida** o **Sincronizzazione completa** nel dashboard di Intune:

   1. Nel dashboard di Intune scegliere **Accesso ad Exchange**.

   2. Selezionare **Accesso locale a Exchange**.

   3. Selezionare il connettore da sincronizzare e scegliere **Sincronizzazione rapida** o **Sincronizzazione completa**.

## <a name="next-steps"></a>Passaggi successivi

Creare [criteri di accesso condizionale per Exchange Server locale](conditional-access-exchange-create.md).
