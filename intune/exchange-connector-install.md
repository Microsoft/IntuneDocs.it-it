---
title: Configurare Microsoft Intune On-Premises Exchange Connector
titleSuffix: Microsoft Intune
description: Usare Exchange Connector locale per gestire l'accesso dei dispositivi alle cassette postali di Exchange in base alla registrazione in Intune e a Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5cf6299f46ed8db4fdca02947ce15a920816d110
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/30/2019
ms.locfileid: "68660952"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune"></a>Configurare Intune Exchange Connector locale in Microsoft Intune
Le informazioni di questo articolo consentono di installare e quindi monitorare il connettore locale di Exchange Active Sync per Intune.  È possibile usare Intune Exchange Connector locale con i [criteri di accesso condizionale per consentire o bloccare l'accesso alle cassette postali locali di Exchange](conditional-access-exchange-create.md). 

Quando un dispositivo cerca di accedere a Exchange locale, Exchange Connector esegue il mapping dei record di Exchange Active Sync (EAS) in Exchange Server ai record di Intune per controllare la registrazione del dispositivo con Intune e la conformità ai criteri di conformità del dispositivo. A seconda dei criteri di accesso condizionale, è possibile consentire o bloccare l'accesso per il dispositivo. Per altre informazioni, vedere [Quali sono i modi comuni per usare l'accesso condizionale con Intune?](conditional-access-intune-common-ways-use.md)

Intune supporta l'installazione di più istanze di Exchange Connector locale per ogni sottoscrizione. Se si hanno più organizzazioni di Exchange locali, è possibile configurare un connettore separato per ognuna di esse. Tuttavia, è possibile installare un solo un connettore per l'uso in ogni singola organizzazione di Exchange. 

Di seguito sono illustrati i passaggi generali per configurare una connessione che consente a Intune di comunicare con l'istanza di Exchange Server locale:

1. Scaricare Intune Exchange Connector locale dal portale di Intune.
2. Installare e configurare Exchange Connector in un computer dell'organizzazione di Exchange locale.
3. Convalidare la connessione di Exchange.
4. Ripetere i passaggi per ogni organizzazione di Exchange aggiuntiva che si vuole connettere a Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Requisiti di Intune On-Premises Exchange Connector
È necessario un account con una licenza di Intune che possa essere usato dal connettore per connettersi a Exchange. L'account viene specificato quando si installa il connettore.  

La tabella seguente elenca i requisiti per il computer in cui viene installato Exchange Connector locale.  

|  Requisito  |   Altre informazioni     |
|---------------|------------------------|
|  Sistemi operativi        | Intune supporta Exchange Connector locale su computer che eseguono qualsiasi edizione di Windows Server 2008 SP2 a 64 bit, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 o Windows Server 2016.<br /><br />Il connettore non è supportato in tutte le installazioni Server Core.  |
| Microsoft Exchange          | I connettori locali richiedono Microsoft Exchange 2010 SP3 o versioni successive oppure l'ambiente legacy Exchange Online dedicato. Per determinare se la configurazione dell'ambiente Exchange Online dedicato è <strong>nuova</strong> o <strong>legacy</strong>, contattare l'account manager. |
| Autorità di gestione dei dispositivi mobili           | [Impostare l'autorità di gestione dei dispositivi mobili su Intune](mdm-authority-set.md). |
| Hardware              | Il computer in cui si installa il connettore richiede una CPU da 1,6 GHz con 2 GB di RAM e 10 GB di spazio libero sul disco. |
|  Sincronizzazione di Active Directory             | Prima di poter usare il connettore per collegare Intune all'istanza corrente di Exchange Server, è necessario [configurare la sincronizzazione di Active Directory](users-add.md) in modo che gli utenti e i gruppi di sicurezza locali siano sincronizzati con l'istanza di Azure Active Directory. |
| Software aggiuntivo         | Nel computer che ospita il connettore deve essere presente un'installazione completa di Microsoft .NET Framework 4.5 e Windows PowerShell 2.0. |
| Rete               | Il computer in cui si installa il connettore deve essere in un dominio con una relazione di trust con il dominio che ospita l'istanza di Exchange Server.<br /><br />Il computer deve essere configurato per poter accedere al servizio Intune attraverso firewall e server proxy sulle porte 80 e 443. I domini usati da Intune includono manage.microsoft.com, &#42;manage.microsoft.com e &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Requisiti dei cmdlet di Exchange

Creare un account utente di Active Directory che verrà usato da Exchange Connector locale. L'account deve avere le autorizzazioni per eseguire i cmdlet Exchange di Windows PowerShell richiesti elencati di seguito.


- Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
- Get-CasMailbox, Set-CasMailbox
- Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
- Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
- Get-ActiveSyncDeviceStatistics
- Get-ActiveSyncDevice
- Get-ExchangeServer
- Get-ActiveSyncDeviceClass
- Get-Recipient
- Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
- Set-ADServerSettings
- Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Scaricare il pacchetto di installazione di Exchange Connector locale

1. In un sistema operativo Windows Server supportato da Exchange Connector locale aprire il [portale di Azure](https://portal.azure.com) ed eseguire l'accesso con un account utente che è un amministratore nel server Exchange locale e dispone di una licenza per l'uso di Exchange Server.

2. Passare a **Intune** > **Accesso ad Exchange**  

3. In **Installazione** scegliere **Connettore locale per Exchange ActiveSync** e quindi selezionare **Aggiungi**.

4. Nella pagina **Aggiungi il connettore** selezionare **Scaricare il connettore locale**. Exchange Connector locale è contenuto in una cartella compressa (con estensione zip) che può essere aperta o salvata. Nella finestra di dialogo **Download del file** scegliere **Salva** per archiviare la cartella compressa in una posizione protetta.

    > [!IMPORTANT]
    > Non rinominare o spostare file all'interno della cartella di Exchange Connector locale. Se si sposta o si rinomina il contenuto della cartella, l'installazione di Exchange Connector viene interrotta.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installare e configurare Intune On-Premises Exchange Connector
Per installare Intune On-Premises Exchange Connector seguire questa procedura. Se sono presenti più organizzazioni di Exchange, ripetere questi passaggi per ogni Exchange Connector aggiuntivo che si vuole configurare.

1. In un sistema operativo supportato da Exchange Connector locale, estrarre i file inclusi in **Exchange_Connector_Setup.zip** in un percorso protetto.

2. Dopo aver estratto i file, aprire la cartella estratta e fare doppio clic su **Exchange_Connector_Setup.exe** per installare Exchange Connector locale.

   > [!IMPORTANT]
   > Se la cartella di destinazione non è una posizione sicura, al termine dell'installazione dei connettori locali è necessario eliminare il file di certificato **MicrosoftIntune.accountcert**.

3. Nella finestra di dialogo **Microsoft Intune Exchange Connector** selezionare **Microsoft Exchange Server locale** o **Microsoft Exchange Server ospitato**.

   ![Immagine che illustra dove scegliere il tipo di Exchange Server](./media/intune-sa-exchange-connector-config.png)

   Per un server Exchange locale specificare il nome del server o il nome di dominio completo del server Exchange in cui è ospitato il ruolo **Server Accesso client**.

   Per un server Exchange ospitato, specificare l'indirizzo del server Exchange. Per trovare l'URL del server Exchange ospitato:

   1. Aprire Outlook sul Web per Office 365.

   2. Scegliere l'icona **?** in alto a sinistra e quindi selezionare **Informazioni su**.

   3. Individuare il valore di **Server esterno POP** .

   4. Scegliere **Server Proxy** per specificare le impostazioni del server proxy per il server Exchange ospitato.
       1. Selezionare **Utilizza un server proxy per la sincronizzazione delle informazioni del dispositivo mobile**.

       2. Immettere il **nome del server proxy** e il **numero di porta** da usare per accedere al server.

       3. Se è necessario specificare le credenziali utente per accedere al server proxy, selezionare **Utilizzare le credenziali per connettersi al server proxy** e quindi immettere **dominio\utente** e **password**.

       4. Scegliere **OK**.

4. Nei campi **Utente (dominio\utente)** e **Password** immettere le credenziali necessarie per la connessione al server Exchange. L'account specificato deve avere una licenza per l'uso di Intune. 

5. Specificare le credenziali necessarie per inviare le notifiche alla cassetta postale di Exchange Server di un utente. L'utente può essere dedicato solo alle notifiche. L'utente delle notifiche deve avere una cassetta postale di Exchange per inviare le notifiche tramite posta elettronica. È possibile configurare queste notifiche con i criteri di accesso condizionale in Intune.  

   Verificare che il servizio di individuazione automatica e i servizi Web Exchange siano configurati nel server Accesso client di Exchange. Per altre informazioni, vedere [Server Accesso client](https://technet.microsoft.com/library/dd298114.aspx).

6. Nel campo **Password** specificare la password per questo account, per abilitare Intune all'accesso a Exchange Server.

7. Scegliere **Connetti**.

   > [!NOTE]
   > La configurazione della connessione può richiedere alcuni minuti.

Durante la configurazione, le impostazioni proxy vengono memorizzate da Exchange Connector per abilitare l'accesso a Internet. Se le impostazioni proxy cambiano, sarà necessario riconfigurare Exchange Connector per applicare le impostazioni proxy aggiornate.

Dopo che Exchange Connector attiva la connessione, i dispositivi mobili associati agli utenti gestiti in Exchange vengono automaticamente sincronizzati e aggiunti a Exchange Connector. La sincronizzazione potrebbe richiedere parecchio tempo.

> [!NOTE]
> Se è stato installato Exchange Connector locale e successivamente si elimina la connessione a Exchange, è necessario disinstallare Exchange Connector locale dal computer in cui è stato installato.



## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installare connettori per più organizzazioni di Exchange
Intune supporta più Exchange Connector locali per ogni sottoscrizione. Per un tenant con più organizzazioni di Exchange, è possibile configurare un connettore per ogni organizzazione di Exchange, ma solo un singolo connettore per un'organizzazione specifica. 

Se si prevede di installare i connettori per connettersi a più organizzazioni di Exchange, scaricare la cartella ZIP una sola volta e quindi riutilizzare il download per ogni connettore installato. Per ogni connettore aggiuntivo, seguire la procedura nella sezione precedente per estrarre ed eseguire il programma di installazione in un server nell'organizzazione di Exchange.

Le funzionalità di disponibilità elevata, monitoraggio e sincronizzazione manuale descritte nelle sezioni seguenti sono supportate per ogni organizzazione di Exchange connessa a Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Supporto a disponibilità elevata di Exchange Connector locale 
Disponibilità elevata per Exchange Connector locale significa che se il server Accesso client di Exchange usato dal connettore smette di essere disponibile, il connettore può passare a un server Accesso client diverso per tale organizzazione di Exchange. Exchange Connector non supporta la disponibilità elevata. In caso di errore del connettore, non è previsto il failover automatico ed è necessario sostituire il connettore [installando un nuovo connettore](#reinstall-the-on-premises-exchange-connector). 

Per ottenere funzionalità di failover, dopo che il connettore stabilisce una connessione a Exchange usando il server Accesso client specificato, il connettore individua altri server Accesso client per tale organizzazione di Exchange. La conoscenza dei server Accesso client aggiuntivi consente al connettore di eseguire il failover a un altro server Accesso client, fino a quando il server primario non diventa disponibile. Per impostazione predefinita, l'individuazione di server Accesso client aggiuntivi è abilitata. È possibile disattivare il failover seguendo questa procedura:  
1. Nel server in cui è installato Exchange Connector, passare a %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Aprire **OnPremisesExchangeConnectorServiceConfiguration.xml** in un editor di testo.
3. Modificare &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; in &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; per disabilitare la funzionalità.  
 
## <a name="optional-performance-tuning-for-the-exchange-connector"></a>Ottimizzazione delle prestazioni facoltativa per Exchange Connector  

Quando si supportano 5000 o più dispositivi con Exchange ActiveSync, è possibile configurare un'impostazione facoltativa per migliorare le prestazioni del connettore. Il miglioramento delle prestazioni si ottiene consentendo a Exchange di usare più istanze di uno spazio di esecuzione dei comandi di PowerShell. 

Prima di apportare questa modifica, verificare che l'account usato per eseguire Exchange Connector non venga usato per altre operazioni di gestione di Exchange. Il motivo è che Exchange prevede un numero limitato di spazi di esecuzione per ogni account, la maggior parte dei quali verrà usata dal connettore. 

Questa modifica delle prestazioni non è adatta per i connettori eseguiti su hardware meno recenti o più lenti.  

1. Nel server in cui è installato il connettore aprire la directory di installazione dei connettori.  Il percorso predefinito è *C:\Programmi\Microsoft\Windows Intune Exchange Connector*. 
2. Modificare il file *OnPremisesExchangeConnectorServiceConfiguration.xml*.
3. Trovare **EnableParallelCommandSupport** e impostare il valore su **true**:  
     
   \<EnableParallelCommandSupport>true\</EnableParallelCommandSupport>
4. Salvare il file, quindi riavviare il servizio Microsoft Intune Exchange Connector.

## <a name="reinstall-the-on-premises-exchange-connector"></a>Reinstallare Exchange Connector locale
Potrebbe essere necessario reinstallare Exchange Connector. Poiché è supportato un solo connettore per la connessione a ogni organizzazione di Exchange, se si installa un secondo connettore per un'organizzazione, il nuovo connettore installato sostituisce il connettore originale.

1. Seguire la procedura in [Installare e configurare Intune Exchange Connector locale](#install-and-configure-the-intune-on-premises-exchange-connector) per avviare l'installazione del nuovo connettore. 
2. Quando richiesto, selezionare **Sostituisci** per installare il nuovo connettore.  
   ![Richiesta di sostituzione di un connettore durante la configurazione](./media/exchange-connector-install/prompt-to-replace.png)

3. Continuare a seguire i passaggi della procedura precedente e accedere di nuovo a Intune.
4. Quando viene visualizzata la schermata finale, selezionare **Chiudi** per completare l'installazione.  
   ![Completare l'installazione](./media/exchange-connector-install/successful-reinstall.png)
 

## <a name="monitor-the-exchange-connector-activity"></a>Monitorare l'attività di Exchange Connector

Dopo aver configurato correttamente Exchange Connector, è possibile visualizzare lo stato delle connessioni e l'ultimo tentativo di sincronizzazione riuscito. Per convalidare la connessione di Exchange Connector:

1. Nel dashboard di Intune scegliere **Accesso ad Exchange**.
2. Selezionare **Accesso locale a Exchange** per verificare lo stato della connessione per ogni istanza di Exchange Connector.

È inoltre possibile verificare la data e ora dell'ultimo tentativo di sincronizzazione riuscito.
--> 

### <a name="system-center-operations-manager-management-pack"></a>System Center Operations Manager Management Pack

A partire dalla versione 1710 di Intune, è possibile usare [Operations Manager Management Pack per Exchange Connector e Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True), che consente di eseguire il monitoraggio di Exchange Connector in diversi modi quando è necessario risolvere i problemi.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forzare manualmente una sincronizzazione rapida o una sincronizzazione completa
Exchange Connector locale sincronizza automaticamente EAS e i record dei dispositivi Intune a intervalli regolari. Se viene modificato lo stato di conformità di un dispositivo, il processo di sincronizzazione automatica aggiorna periodicamente i record, in modo che l'accesso al dispositivo possa essere bloccato o consentito.

- La **sincronizzazione rapida** si verifica a intervalli regolari più volte al giorno. Una sincronizzazione rapida recupera le informazioni sul dispositivo relative a utenti con licenza di Intune e configurati con l'accesso condizionale a Exchange locale che sono cambiate dall'ultima sincronizzazione.

- Per impostazione predefinita la **sincronizzazione completa** viene eseguita una volta al giorno. Una sincronizzazione completa recupera le informazioni sul dispositivo relative a tutti gli utenti con licenza di Intune e configurati con l'accesso condizionale a Exchange locale. Una sincronizzazione completa recupera anche informazioni sul server Exchange e verifica che la configurazione specificata da Intune nel portale di Azure sia aggiornata nel server Exchange. 


È possibile forzare un connettore a eseguire una sincronizzazione usando le opzioni **Sincronizzazione rapida** o **Sincronizzazione completa** nel dashboard di Intune seguendo questa procedura:

   1. Nel dashboard di Intune scegliere **Accesso ad Exchange**.
   2. Selezionare **Accesso locale a Exchange**.
   3. Selezionare il connettore da sincronizzare e scegliere **Sincronizzazione rapida** o **Sincronizzazione completa**.

## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di accesso condizionale per Exchange locale](conditional-access-exchange-create.md)
