---
title: Configurare Exchange Connector per EAS con Intune
titleSuffix: Azure portal
description: Usare lo strumento Connector per consentire la comunicazione tra Intune ed Exchange Server locale
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39fb4b4b91eb6769eb1d5d95736cbbde141c6812
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Configurare Intune On-Premises Exchange Connector in Microsoft Intune in Azure

Gli ambienti con Exchange Server locale possono usare Intune On-Premises Exchange Connector per gestire l'accesso dei dispositivi alle cassette postali di Exchange locale in base al fatto che i dispositivi siano registrati o meno in Intune e siano conformi ai criteri di conformità dei dispositivi di Intune. On-Premises Exchange Connector supporta anche l'individuazione dei dispositivi mobili che si connettono a server Exchange locali sincronizzando il record EAS (Exchange Active Sync) esistente con Intune.

> [!IMPORTANT]
> Intune supporta solo una connessione con Exchange Connector locale per qualsiasi tipo per ogni sottoscrizione.

Per configurare una connessione che consente a Microsoft Intune di comunicare con Exchange Server locale, è necessario seguire questa procedura:

1.  Scaricare Intune On-Premises Exchange Connector dal portale di Azure.
2.  Installare e configurare Intune On-Premises Exchange Connector.
3.  Convalidare la connessione di Exchange.

## <a name="on-premises-exchange-connector-requirements"></a>Requisiti per On-Premises Exchange Connector
Nella tabella seguente sono elencati i requisiti per il computer in cui viene installato On-premises Exchange Connector.

|Requisito|Altre informazioni|
|---------------|--------------------|
|Sistemi operativi|Intune supporta On-premises Exchange Connector su computer che eseguono qualsiasi edizione di Windows Server 2008 SP2 a 64 bit, Windows Server 2008 R2, Windows Server 2012 o Windows Server 2012 R2.<br /><br />Il connettore non è supportato in tutte le installazioni Server Core.|
|Microsoft Exchange|On-Premises Connector richiede Microsoft Exchange 2010 SP1 o versioni successive oppure l'ambiente legacy Exchange Online dedicato. Per determinare se la configurazione dell'ambiente Exchange Online dedicato è **nuova** o **legacy**, contattare l'account manager.|
|Autorità di gestione dei dispositivi mobili| [Impostare l'autorità di gestione dei dispositivi mobili su Intune](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).|
|Hardware|Il computer in cui si installa il connettore richiede una CPU da 1,6 GHz con 2 GB di RAM e 10 GB di spazio libero sul disco.|users-add.md
|Sincronizzazione di Active Directory|Prima di poter usare il connettore per collegare Intune all'istanza corrente di Exchange Server, è necessario [configurare la sincronizzazione di Active Directory](users-add.md) in modo che gli utenti e i gruppi di sicurezza locali siano sincronizzati con l'istanza di Azure Active Directory.|
|Software aggiuntivo|Nel computer che ospita il connettore deve essere presente un'installazione completa di Microsoft .NET Framework 4.5 e Windows PowerShell 2.0.|
|Rete|Il computer in cui si installa il connettore deve essere in un dominio con una relazione di trust con il dominio che ospita l'istanza di Exchange Server.<br /><br />Il computer deve essere configurato per poter accedere al servizio Intune attraverso firewall e server proxy sulle porte 80 e 443. I domini usati da Intune includono manage.microsoft.com, &#42;manage.microsoft.com e &#42;.manage.microsoft.com.|


### <a name="exchange-cmdlet-requirements"></a>Requisiti dei cmdlet di Exchange

È necessario creare un account utente di Active Directory che viene usato da Intune Exchange Connector. L'account deve avere le autorizzazioni per eseguire i cmdlet Exchange di Windows PowerShell richiesti elencati di seguito.


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

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>Scaricare il pacchetto di installazione di On-premises Exchange Connector

1. In un sistema operativo Windows Server supportato per On-Premises Exchange Connector aprire il [portale di Azure](http://portal.azure.com) ed eseguire l'accesso con un account utente che è un amministratore nel server Exchange locale e dispone di una licenza per l'uso di Exchange Server.

2. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune**. Verrà aperto il dashboard di Intune. Scegliere **Accesso locale**.

4. Nella sezione **Installazione** del pannello **Accesso locale - Connettore per Exchange ActiveSync** scegliere **Scaricare il connettore locale**.

5.  On-premises Exchange Connector è contenuto in una cartella compressa (zip) che può essere aperta o salvata. Nella finestra di dialogo **Download del file** scegliere **Salva** per archiviare la cartella compressa in una posizione protetta.

    > [!IMPORTANT]
    > Non rinominare o spostare file all'interno della cartella di On-Premises Exchange Connector. Se si sposta o si rinomina il contenuto della cartella l'installazione verrà interrotta.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Installare e configurare Intune On-premises Exchange Connector
Eseguire la procedura seguente per installare Intune On-premises Exchange Connector. On-Premises Exchange Connector può essere installato una sola volta per ogni sottoscrizione di Intune e in un solo computer. Se si tenta di configurare un'istanza aggiuntiva di On-Premises Exchange Connector, la connessione originale sarà sostituita da quella nuova.

1.  In un sistema operativo supportato da On-Premises Connector estrarre i file inclusi in **Exchange_Connector_Setup.zip** in un percorso protetto.

2.  Dopo aver estratto i file, aprire la cartella estratta e fare doppio clic su **Exchange_Connector_Setup.exe** per installare On-Premises Exchange Connector.

    > [!IMPORTANT]
    > Se la cartella di destinazione non è una posizione sicura, è necessario eliminare il file di certificato **WindowsIntune.accountcert** dopo aver installato On-Premises Connector.

3.  Nella finestra di dialogo **Microsoft Intune Exchange Connector** selezionare **Microsoft Exchange Server locale** o **Microsoft Exchange Server ospitato**.

  ![Scegliere il tipo di server Exchange](./media/intune-sa-exchange-connector-config.png)

  Per un server Exchange locale specificare il nome del server o il nome di dominio completo del server Exchange in cui è ospitato il ruolo **Server Accesso client**.

  Per un server Exchange ospitato, specificare l'indirizzo del server Exchange. Per trovare l'URL del server Exchange ospitato:

    1. Aprire Outlook Web App per Office 365.

    2. Scegliere l'icona **?** in alto a sinistra e quindi selezionare **Informazioni su**.

    3. Individuare il valore di **Server esterno POP** .

    4. Scegliere **Server Proxy** per specificare le impostazioni del server proxy per il server Exchange ospitato.
        1. Selezionare **Utilizza un server proxy per la sincronizzazione delle informazioni del dispositivo mobile**.

        2. Immettere il **nome del server proxy** e il **numero di porta** da usare per accedere al server.

        3. Se è necessario specificare le credenziali utente per accedere al server proxy, selezionare **Utilizzare le credenziali per connettersi al server proxy** e quindi immettere **dominio\utente** e **password**.

        4. Scegliere **OK**.

    5. Nei campi **Utente (dominio\utente)** e **Password** immettere le credenziali necessarie per la connessione al server Exchange.

    6.  Fornire le credenziali amministrative necessarie per inviare le notifiche alla cassetta postale di Exchange Server di un utente. È possibile configurare queste notifiche con i criteri di accesso condizionale in Intune.

        Verificare che il servizio di individuazione automatica e i servizi Web Exchange siano configurati nel server Accesso client di Exchange. Per altre informazioni, vedere [Server Accesso client](https://technet.microsoft.com/library/dd298114.aspx).

    7.  Nel campo **Password** specificare la password per questo account, per abilitare Intune all'accesso a Exchange Server.

    8. Scegliere **Connetti**.

    > [!NOTE]
    > La configurazione della connessione può richiedere alcuni minuti.

Durante la configurazione, le impostazioni proxy vengono memorizzate da Exchange Connector per abilitare l'accesso a Internet. Se le impostazioni proxy cambiano, sarà necessario riconfigurare Exchange Connector per applicare le impostazioni proxy aggiornate.

Dopo aver configurato la connessione in Exchange Connector, i dispositivi mobili associati agli utenti gestiti in Exchange Connector vengono automaticamente sincronizzati e aggiunti a Exchange Connector. La sincronizzazione potrebbe richiedere parecchio tempo.

> [!NOTE]
> Se è stato installato On-Premises Exchange Connector e a un certo punto si elimina la connessione a Exchange, è necessario disinstallare On-Premises Exchange Connector dal computer in cui è stato installato.

## <a name="on-premises-exchange-connector-high-availability-support"></a>Supporto a disponibilità elevata di Exchange Connector locale 
Dopo che Exchange Connector crea una connessione a Exchange usando il CAS specificato, il connettore è in grado di individuare altri CAS. Se il CAS principale diventa non disponibile, il connettore eseguirà il failover a un altro CAS, se disponibile, fino a quando non diventa disponibile il CAS principale. Questa funzionalità è attivata per impostazione predefinita. È possibile disattivare questa funzionalità usando la procedura seguente:
1. Nel server in cui è installato Exchange Connector, passare a %*ProgramData*%\Microsoft\Windows Intune Exchange Connector. 
2. Aprire **OnPremisesExchangeConnectorServiceConfiguration.xml** in un editor di testo.
3. Modificare &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt; in &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt; per disabilitare la funzionalità.    


## <a name="monitor-the-exchange-connector-activity"></a>Monitorare l'attività di Exchange Connector

Dopo aver configurato correttamente Exchange Connector, è possibile visualizzare lo stato della connessione e l'ultimo tentativo di sincronizzazione riuscito. Per convalidare la connessione di Exchange Connector:

1. Nel dashboard di Intune scegliere **Accesso locale**.
2. In **Gestisci** selezionare **Accesso locale a Exchange** per verificare lo stato della connessione.

È inoltre possibile verificare la data e ora dell'ultimo tentativo di sincronizzazione riuscito.

### <a name="system-center-operations-manager-scom-management-pack"></a>System Center Operations Manager (SCOM) Management Pack

A partire dalla versione 1710 di Intune, è possibile usare [SCOM Management Pack per Exchange Connector e Intune](https://www.microsoft.com/en-us/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True), che consente di eseguire il monitoraggio di Exchange Connector in diversi modi quando è necessario risolvere i problemi.

## <a name="next-steps"></a>Passaggi successivi
[Creare criteri di accesso condizionale per Exchange locale](conditional-access-exchange-create.md)
