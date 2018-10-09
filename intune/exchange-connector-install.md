---
title: Configurare Microsoft Intune On-Premises Exchange Connector
titleSuffix: ''
description: Usare Exchange Connector locale per gestire l'accesso dei dispositivi alle cassette postali di Exchange in base alla registrazione in Intune e a Exchange Active Sync (EAS).
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e12ab106b44d217d7e7b4b1a466fd5b12a9fb528
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231832"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Configurare Intune On-Premises Exchange Connector in Azure

In un ambiente Exchange Server locale è possibile usare l'accesso condizionale di Intune per consentire o bloccare l'accesso alle cassette postali locali di Exchange. Usare i connettori Exchange Active Sync locali per connettere Intune alle organizzazioni di Exchange e configurare l'accesso condizionale di Intune insieme ai criteri di conformità dei dispositivi. Se dopo questa operazione un dispositivo prova a connettersi a Exchange, Intune stabilisce se il dispositivo è registrato in Intune ed è conforme. Per determinare quali dispositivi sono registrati in Intune, Exchange Connector locale esegue il mapping tra i record Exchange Active Sync (EAS) in Exchange Server e i record di Intune. Per altre informazioni su questa funzionalità, vedere [Quali sono i modi comuni per usare l'accesso condizionale con Intune?](conditional-access-intune-common-ways-use.md)

> [!IMPORTANT]
> Intune ora supporta più Exchange Connector locali per ogni sottoscrizione. Se sono presenti più organizzazioni di Exchange locali, è possibile configurare un connettore separato per ogni organizzazione di Exchange.

Per configurare una connessione che consente a Microsoft Intune di comunicare con l'istanza Exchange Server locale, seguire questa procedura generale:

1.  Scaricare Intune On-Premises Exchange Connector dal portale di Azure.
2.  Installare e configurare Exchange Connector in un computer dell'organizzazione di Exchange locale.
3.  Convalidare la connessione di Exchange.
4. Ripetere questi passaggi per ogni organizzazione di Exchange che si vuole connettere a Intune.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Requisiti di Intune On-Premises Exchange Connector
La tabella seguente elenca i requisiti per il computer in cui viene installato Exchange Connector locale.


|            Requisito             |                                                                                                                                                                                                        Altre informazioni                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         Sistemi operativi          |                                                               Intune supporta Exchange Connector locale su computer che eseguono qualsiasi edizione di Windows Server 2008 SP2 a 64 bit, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 o Windows Server 2016.<br /><br />Il connettore non è supportato in tutte le installazioni Server Core.                                                                |
|         Microsoft Exchange         |                                                                           I connettori locali richiedono Microsoft Exchange 2010 SP1 o versioni successive oppure l'ambiente legacy Exchange Online dedicato. Per determinare se la configurazione dell'ambiente Exchange Online dedicato è <strong>nuova</strong> o <strong>legacy</strong>, contattare l'account manager.                                                                           |
| Autorità di gestione dei dispositivi mobili |                                                                                                                              [Impostare l'autorità di gestione dei dispositivi mobili su Intune](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).                                                                                                                               |
|              Hardware              |                                                                                                                                                     Il computer in cui si installa il connettore richiede una CPU da 1,6 GHz con 2 GB di RAM e 10 GB di spazio libero sul disco.                                                                                                                                                      |
|  Sincronizzazione di Active Directory  |                                                                                      Prima di poter usare il connettore per collegare Intune all'istanza corrente di Exchange Server, è necessario [configurare la sincronizzazione di Active Directory](users-add.md) in modo che gli utenti e i gruppi di sicurezza locali siano sincronizzati con l'istanza di Azure Active Directory.                                                                                      |
|        Software aggiuntivo         |                                                                                                                                           Nel computer che ospita il connettore deve essere presente un'installazione completa di Microsoft .NET Framework 4.5 e Windows PowerShell 2.0.                                                                                                                                           |
|              Rete               | Il computer in cui si installa il connettore deve essere in un dominio con una relazione di trust con il dominio che ospita l'istanza di Exchange Server.<br /><br />Il computer deve essere configurato per poter accedere al servizio Intune attraverso firewall e server proxy sulle porte 80 e 443. I domini usati da Intune includono manage.microsoft.com, &#42;manage.microsoft.com e &#42;.manage.microsoft.com. |

### <a name="exchange-cmdlet-requirements"></a>Requisiti dei cmdlet di Exchange

È necessario creare un account utente di Active Directory che viene usato da Exchange Connector locale. L'account deve avere le autorizzazioni per eseguire i cmdlet Exchange di Windows PowerShell richiesti elencati di seguito.


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Scaricare il pacchetto di installazione di Exchange Connector locale

1. In un sistema operativo Windows Server supportato da Exchange Connector locale aprire il [portale di Azure](http://portal.azure.com) ed eseguire l'accesso con un account utente che è un amministratore nel server Exchange locale e dispone di una licenza per l'uso di Exchange Server.

2. Scegliere **Tutti i servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune**. Quando viene aperto il dashboard di Intune scegliere **Accesso locale**.

4. In **Installazione** scegliere **Connettori per Exchange ActiveSync** e quindi scegliere **Scaricare il connettore locale**.

5.  Exchange Connector locale è contenuto in una cartella compressa ( con estensione zip) che può essere aperta o salvata. Nella finestra di dialogo **Download del file** scegliere **Salva** per archiviare la cartella compressa in una posizione protetta.

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

   5. Nei campi **Utente (dominio\utente)** e **Password** immettere le credenziali necessarie per la connessione al server Exchange.

   6.  Specificare le credenziali necessarie per inviare le notifiche alla cassetta postale di Exchange Server di un utente. L'utente può essere dedicato solo alle notifiche. Perché l'utente delle notifiche sia in grado di inviare notifiche tramite posta elettronica, deve avere una cassetta postale di Exchange. È possibile configurare queste notifiche con i criteri di accesso condizionale in Intune.  

       Verificare che il servizio di individuazione automatica e i servizi Web Exchange siano configurati nel server Accesso client di Exchange. Per altre informazioni, vedere [Server Accesso client](https://technet.microsoft.com/library/dd298114.aspx).

   7.  Nel campo **Password** specificare la password per questo account, per abilitare Intune all'accesso a Exchange Server.

   8. Scegliere **Connetti**.

   > [!NOTE]
   > La configurazione della connessione può richiedere alcuni minuti.

Durante la configurazione, le impostazioni proxy vengono memorizzate da Exchange Connector per abilitare l'accesso a Internet. Se le impostazioni proxy cambiano, sarà necessario riconfigurare Exchange Connector per applicare le impostazioni proxy aggiornate.

Dopo che Exchange Connector attiva la connessione, i dispositivi mobili associati agli utenti gestiti in Exchange vengono automaticamente sincronizzati e aggiunti a Exchange Connector. La sincronizzazione potrebbe richiedere parecchio tempo.

> [!NOTE]
> Se è stato installato Exchange Connector locale e successivamente si elimina la connessione a Exchange, è necessario disinstallare Exchange Connector locale dal computer in cui è stato installato.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>Installare connettori per più organizzazioni di Exchange
Intune supporta più Exchange Connector locali per ogni sottoscrizione. Per un tenant con più organizzazioni di Exchange, è possibile impostare un connettore per ogni organizzazione di Exchange. Scaricare la cartella con estensione zip una sola volta, quindi per ogni organizzazione di Exchange seguire la procedura della sezione precedente per estrarre ed eseguire il programma di installazione in un server dell'organizzazione.

Le funzionalità di disponibilità elevata, monitoraggio e sincronizzazione descritte nelle sezioni seguenti sono supportate per ogni organizzazione di Exchange connessa a Intune.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Supporto a disponibilità elevata di Exchange Connector locale 
Dopo che Exchange Connector crea una connessione a Exchange usando il CAS specificato, il connettore è in grado di individuare altri CAS. Se il CAS principale diventa non disponibile, il connettore eseguirà il failover a un altro CAS, se disponibile, fino a quando non diventa disponibile il CAS principale. Questa funzionalità è attivata per impostazione predefinita. È possibile disattivare questa funzionalità usando la procedura seguente:
1. Nel server in cui è installato Exchange Connector, passare a %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Aprire **OnPremisesExchangeConnectorServiceConfiguration.xml** in un editor di testo.
3. Modificare &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; in &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; per disabilitare la funzionalità.    


## <a name="monitor-the-exchange-connector-activity"></a>Monitorare l'attività di Exchange Connector

Dopo aver configurato correttamente Exchange Connector è possibile visualizzare lo stato della connessione e l'ultimo tentativo di sincronizzazione riuscito. Per convalidare la connessione di Exchange Connector:

1. Nel dashboard di Intune scegliere **Accesso locale**.
2. In **Installazione** selezionare **Connettori per Exchange ActiveSync** per verificare lo stato di connessione delle singole istanze di Exchange Connector.

È inoltre possibile verificare la data e ora dell'ultimo tentativo di sincronizzazione riuscito.

### <a name="system-center-operations-manager-scom-management-pack"></a>System Center Operations Manager (SCOM) Management Pack

A partire dalla versione 1710 di Intune, è possibile usare [SCOM Management Pack per Exchange Connector e Intune](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True), che consente di eseguire il monitoraggio di Exchange Connector in diversi modi quando è necessario risolvere i problemi.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>Forzare manualmente una sincronizzazione rapida o una sincronizzazione completa
Exchange Connector locale sincronizza automaticamente EAS e i record dei dispositivi Intune a intervalli regolari. Se viene modificato lo stato di conformità di un dispositivo, il processo di sincronizzazione automatica aggiorna periodicamente i record, in modo che l'accesso al dispositivo possa essere bloccato o consentito di conseguenza.

   - La **sincronizzazione rapida** si verifica a intervalli regolari più volte al giorno. Una sincronizzazione rapida recupera le informazioni sul dispositivo relative a utenti con licenza di Intune e destinazione di accesso condizionale Exchange locale che sono cambiate dall'ultima sincronizzazione.

   - Per impostazione predefinita la **sincronizzazione completa** viene eseguita una volta al giorno. Una sincronizzazione completa recupera le informazioni sul dispositivo relative a tutti gli utenti con licenza di Intune e destinazione di accesso condizionale Exchange locale. Una sincronizzazione completa recupera anche informazioni sul server Exchange e verifica che la configurazione specificata da Intune nel portale di Azure sia aggiornata nel server Exchange. 

È possibile forzare un connettore a eseguire una sincronizzazione usando le opzioni **Sincronizzazione rapida** o **Sincronizzazione completa** nel dashboard di Intune seguendo questa procedura:

   1. Nel dashboard di Intune scegliere **Accesso locale**.
   2. In **Installazione** scegliere **Exchange Active Sync Connectors** (Connettori Exchange Active Sync).
   3. Selezionare il connettore da sincronizzare e scegliere **Sincronizzazione rapida** o **Sincronizzazione completa**.

## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di accesso condizionale per Exchange locale](conditional-access-exchange-create.md)
