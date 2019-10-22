---
title: Risolvere i problemi comuni per Intune Exchange Connector
titleSuffix: Microsoft Intune
description: Risolvere i problemi comuni relativi a Microsoft Intune Exchange Connector locale.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9542212e1b75d97c96c024eed20e20e610e2b5d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503640"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Risolvere i problemi comuni con Intune Exchange Connector
 
Questo articolo può essere utile all'amministratore di Intune per risolvere i problemi comuni relativi al funzionamento di Intune Exchange Connector.  

Prima di iniziare la risoluzione dei problemi, vedere [risolvere i problemi relativi a Intune on-premises Exchange Connector](troubleshoot-exchange-connector.md) per informazioni di base sul connettore. Esaminare anche i problemi comuni per la configurazione del connettore. 

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Un dispositivo Exchange ActiveSync non viene individuato da Exchange

Quando un dispositivo Exchange ActiveSync non viene individuato da Exchange, [monitorare l'attività di Exchange Connector](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) per verificare se Exchange Connector è sincronizzato con il server Exchange. Se non è stata eseguita alcuna sincronizzazione dopo che il dispositivo è stato aggiunto, raccogliere i log di sincronizzazione e associarli a una richiesta di supporto. Se una sincronizzazione completa o una sincronizzazione rapida è stata completata da quando il dispositivo è stato aggiunto, verificare i seguenti problemi: 

- Assicurarsi che gli utenti dispongano di una licenza di Intune. In caso contrario, Exchange Connector non riuscirà a individuare i dispositivi.  

- Se l'indirizzo SMTP primario dell'utente è diverso dal nome dell'entità utente (UPN) in Azure Active Directory (Azure AD), Exchange Connector non sarà in grado di individuare alcun dispositivo per tale utente. Risolvere l'indirizzo SMTP primario per risolvere il problema.  

- Se l'ambiente include server di cassette postali sia di Exchange 2010 che di Exchange 2013, si consiglia di associare Exchange Connector a un server Accesso client (CAS) di Exchange 2013. Se Exchange Connector è configurato per comunicare con un CAS di Exchange 2010, Exchange Connector non individuerà i dispositivi degli utenti in Exchange 2013.  

- Per gli ambienti Exchange Online dedicati, è necessario puntare Exchange Connector a un CAS di Exchange 2013 (non un CAS di Exchange 2010) nell'ambiente dedicato durante l'installazione iniziale. Il connettore comunicherà solo con un CAS di Exchange 2013 quando esegue i cmdlet di PowerShell.  


## <a name="problems-with-the-notification-email-message"></a>Problemi con il messaggio di posta elettronica di notifica  

Per supportare l'accesso condizionale per le cassette postali locali nei dispositivi che non eseguono Android Knox, assicurarsi che la registrazione di Intune venga avviata dal messaggio di posta elettronica "inizia ora" inviato da Intune Exchange Connector. Avviando la registrazione dal messaggio si garantisce che il dispositivo riceva un ActiveSyncID univoco in tutte le piattaforme (Exchange, Azure AD, Intune).  

Un utente potrebbe non ricevere il messaggio di posta elettronica di notifica perché:  

- L'account di notifica è stato configurato in modo errato.
- Individuazione automatica non riuscita per l'account di notifica.
- I servizi Web Exchange (EWS) Request to Send il messaggio di posta elettronica non è riuscito.

Esaminare le sezioni seguenti per risolvere i problemi relativi alle notifiche di posta elettronica.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>Controllare l'account di notifica che recupera le impostazioni di individuazione automatica
1. Verificare che il servizio di individuazione automatica e i servizi Web Exchange siano configurati nei servizi Accesso client di Exchange. Per altre informazioni, vedere [servizi di accesso client](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) e [servizio di individuazione automatica in Exchange Server](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019).


2. Verificare che l'account di notifica soddisfi i requisiti seguenti:

   - L'account dispone di una cassetta postale attiva ospitata dal server Exchange locale.  

   - L'UPN dell'account corrisponde all'indirizzo SMTP.

3. L'individuazione automatica richiede un server DNS che disponga di un record DNS per **autodiscover.SMTPdomain.com** (ad esempio autodiscover.contoso.com) che punta al server Accesso client di Exchange. Per verificare la presenza del record, specificare il nome di dominio completo al posto di *autodiscover.SMTPdomain.com* e seguire questa procedura:

   1. Al prompt dei comandi immettere *nslookup*.  

   2. Immettere *autodiscover.SMTPdomain.com*. L'output dovrebbe essere simile all'immagine seguente:  
      risultati di ![Nslookup](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
)

   È anche possibile testare il servizio di individuazione automatica da Internet in https://testconnectivity.microsoft.com. In alternativa, è necessario eseguirne il test da un dominio locale utilizzando lo strumento Microsoft Connectivity Analyzer. Per ulteriori informazioni, vedere [strumento Microsoft Connectivity Analyzer](https://docs.microsoft.com/en-us/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80)). Se necessario, [scaricare lo strumento Microsoft Connectivity Analyzer](https://go.microsoft.com/fwlink/?LinkID=313782).


### <a name="check-autodiscovery"></a>Controlla individuazione automatica  

Se l'individuazione automatica ha esito negativo, provare a eseguire i passaggi seguenti:
1. [Configurare un record DNS di individuazione automatica valido](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150)). 

2. Impostare come hardcoded l'URL di EWS nel file di configurazione di Intune Exchange Connector:

   1. Determinare l'URL di EWS. L'URL predefinito di EWS per Exchange è `https://<mailServerFQDN>/ews/exchange.asmx`, ma l'URL potrebbe variare. Contattare l'amministratore di Exchange per verificare l'URL corretto per l'ambiente.

   2. Modificare il file *OnPremisesExchangeConnectorServiceConfiguration.xml*. Per impostazione predefinita, il file si trova in *%ProgramData%\Microsoft\Windows Intune Exchange Connector* nel computer in cui è in esecuzione Exchange Connector. Aprire il file in un editor di testo e quindi modificare la riga seguente in modo che corrisponda all'URL di EWS per l'ambiente: `<ExchangeWebServiceURL>https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`
    

3. Salvare il file e quindi riavviare il computer o riavviare il servizio Microsoft Intune Exchange Connector.

>[!NOTE]
> In questa configurazione, Intune Exchange Connector si interrompe usando l'individuazione automatica e si connette direttamente all'URL di EWS.

## <a name="next-steps"></a>Passaggi successivi  

Per informazioni su errori specifici, provare a [risolvere gli errori comuni per Intune Exchange Connector](troubleshoot-exchange-connector-common-errors.md).

Per ottenere supporto o per ottenere assistenza dalla community di Intune:
- Vedere [ottenere supporto](../fundamentals/get-support.md) per usare la console di Intune per risolvere il problema o per aprire un caso di supporto con Microsoft. 
- Pubblicare il problema nei [forum Microsoft Intune](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod).  
