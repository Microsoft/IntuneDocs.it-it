---
title: Risolvere i problemi di accesso condizionale
description: Operazioni da eseguire quando gli utenti non riescono ad accedere alle risorse usando l'accesso condizionale di Intune.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 10/24/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3ef3b442c5d2cdb731fc906bb865d280729b163a
ms.sourcegitcommit: ada99fefe9a612ed753420116f8c801ac4bf0934
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238176"
---
# <a name="troubleshoot-conditional-access"></a>Risolvere i problemi di accesso condizionale

In genere, un utente che tenta di accedere alla posta elettronica o a SharePoint riceve una richiesta di registrazione. La richiesta indirizza l'utente al portale aziendale.

Questo articolo descrive le operazioni da eseguire quando gli utenti non riescono ad accedere alle risorse usando l'accesso condizionale di Intune.


## <a name="the-basics-for-success-in-conditional-access"></a>Nozioni di base per il corretto funzionamento dell'accesso condizionale

Per garantire il funzionamento dell'accesso condizionale, devono essere soddisfatte le condizioni seguenti:

-   Il dispositivo deve essere gestito da Intune.
-   Il dispositivo deve essere registrato in Azure Active Directory (AAD). In condizioni normali questa registrazione viene eseguita automaticamente durante la registrazione di Intune.
-   Il dispositivo deve essere conforme ai criteri di conformità di Intune, sia per il dispositivo sia per l'utente del dispositivo.  Se non sono presenti criteri di conformità, è sufficiente la registrazione di Intune.
-   È necessario attivare Exchange ActiveSync sul dispositivo se l'utente recupera la posta usando il client di posta elettronica nativo del dispositivo anziché Outlook. Tale attivazione avviene automaticamente per i dispositivi iOS, Windows Phone e Android/KNOX Standard.
-   Intune Exchange Connector deve essere configurato correttamente. Per altre informazioni, vedere [Troubleshooting the Exchange Connector in Microsoft Intune](troubleshoot-exchange-connector.md) (Risoluzione dei problemi di Exchange Connector in Microsoft Intune).

È possibile visualizzare queste condizioni per ogni dispositivo nel portale di Azure e nel report di inventario dei dispositivi.

## <a name="enrollment-issues"></a>Problemi di registrazione

 -  Il dispositivo non è registrato, quindi la registrazione risolverà il problema.
 -  L'utente ha registrato il dispositivo, ma l'aggiunta all'area di lavoro non è riuscita. L'utente deve aggiornare la registrazione dal portale aziendale.

## <a name="compliance-issues"></a>Problemi di conformità

- Il dispositivo non è conforme ai criteri di Intune. Problemi comuni sono i requisiti di crittografia e password. L'utente verrà reindirizzato al portale aziendale, in cui può configurare il dispositivo in modo che sia conforme.
- La registrazione delle informazioni di conformità per un dispositivo può richiedere tempo. Attendere qualche minuto e riprovare.
- Per i dispositivi iOS:
  - Un profilo di posta elettronica esistente creato dall'utente bloccherà la distribuzione di un profilo creato dall'amministratore di Intune. Si tratta di un problema comune poiché gli utenti di iOS in genere creano un profilo di posta elettronica e poi eseguono la registrazione. Il portale aziendale comunicherà all'utente che esiste un problema di mancata conformità perché il profilo di posta elettronica è stato configurato manualmente e richiederà all'utente di rimuovere il profilo. L'utente deve rimuovere il proprio profilo di posta elettronica in modo da poter distribuire il profilo di Intune. Per evitare il problema, indicare agli utenti di eseguire la registrazione senza installare un profilo di posta elettronica e di consentire a Intune di distribuire il profilo.
  - Un dispositivo iOS può restare bloccato in uno stato di controllo della conformità, impedendo all'utente di avviare un altro check-in. Il riavvio del portale aziendale può risolvere il problema e lo stato di conformità sarà riflesso nello stato del dispositivo in Intune. Dopo che tutti i dati sono stati raccolti con una sincronizzazione del dispositivo, il controllo della conformità viene eseguito in modo rapido, mediamente in meno di mezzo secondo.

    In genere, i dispositivi rimangono bloccati in questo stato perché si verificano problemi di connessione al servizio o perché la sincronizzazione richiede molto tempo.  Se il problema persiste con diverse configurazioni di rete (cellulare, Wi-Fi, VPN), con il riavvio del dispositivo e dopo aver verificato l'aggiornamento del provider di servizi condivisi sul dispositivo, contattare il Supporto tecnico Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](get-support.md).

- Per dispositivi Android:
   - È possibile che alcuni dispositivi Android sembrino crittografati, nonostante l'app Portale aziendale non li riconosca come tali. 
    
       -   In caso di dispositivi che presentano questo stato, l'utente deve impostare un passcode di avvio sicuro. L'utente visualizzerà una notifica del dispositivo inviata nell'app Portale aziendale in cui viene chiesto di impostare un passcode di avvio per il dispositivo. Dopo aver toccato la notifica del dispositivo e confermato il PIN o la password esistente, scegliere l'opzione **Require PIN to start device** (Richiedi PIN per avviare il dispositivo) nella schermata **Secure start-up** (Avvio sicuro). Toccare poi il pulsante **Controlla conformità** corrispondente al dispositivo nell'app Portale aziendale. Il dispositivo sarà riconosciuto come crittografato.
    
       -   Alcuni produttori di dispositivi eseguono la crittografia dei propri dispositivi usando un PIN predefinito anziché il PIN segreto impostato dall'utente. Intune riconosce la crittografia che usa il PIN predefinito come non sicura poiché questo metodo di crittografia può mettere i dati nel dispositivo a rischio di utenti malintenzionati con accesso fisico al dispositivo. Per questo tipo di problema, usare i [criteri di protezione delle app](app-protection-policies.md).

## <a name="policy-issues"></a>Problemi relativi ai criteri

Quando si crea un criterio di conformità e lo si collega a un criterio di posta elettronica, entrambi i criteri devono essere distribuiti allo stesso utente, occorre quindi prestare attenzione quando si stabilisce quali criteri verranno distribuiti e a quali gruppi. Agli utenti per i quali viene applicato un solo criterio probabilmente risulterà che i dispositivi in uso non sono conformi.


## <a name="exchange-activesync-issues"></a>Problemi relativi a Exchange ActiveSync

### <a name="compliant-android-device-gets-quarantine-notice"></a>Un dispositivo Android conforme riceve un avviso di quarantena
- Un dispositivo Android registrato e conforme può comunque ricevere un avviso di quarantena quando tenta di accedere alle risorse aziendali. Prima di scegliere il collegamento **Inizio**, l'utente deve verificare che il portale aziendale non fosse aperto quando ha tentato di accedere alle risorse. Gli utenti devono chiudere il portale aziendale, tentare nuovamente di accedere alle risorse e quindi scegliere il collegamento **Inizio**.

### <a name="retired-device-continues-to-have-access"></a>Un dispositivo ritirato continua a disporre dei diritti di accesso
- Quando si usa Exchange Online, un dispositivo ritirato può continuare a disporre dei diritti di accesso per diverse ore dopo il ritiro. Questo avviene perché Exchange memorizza nella cache i diritti di accesso per 6 ore. Prendere in considerazione altri metodi di protezione dei dati nei dispositivi ritirati in questo scenario.

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>Il dispositivo è conforme e registrato con AAD ma risulta ancora bloccato
- In alcuni casi, il provisioning dell'ID di Exchange ActiveSync (EASID) a AAD viene ritardato. Una causa comune di questo problema è la limitazione, quindi attendere qualche minuto e riprovare.

### <a name="device-blocked"></a>Dispositivo bloccato

Un dispositivo può essere bloccato da accesso condizionale senza che venga inviato un messaggio di posta elettronica di attivazione.

- Esiste una regola predefinita di Exchange che mette in quarantena o blocca i dispositivi? Se una regola predefinita blocca o mette in quarantena i dispositivi, questi non saranno in grado di ricevere il messaggio di posta elettronica di attivazione da Exchange Connector. Si tratta di un problema di progettazione.
- L'account di notifica è configurato correttamente come descritto nella configurazione di base?
- Il dispositivo è presente nella console di amministrazione di Intune come dispositivo Exchange ActiveSync? Se la risposta è negativa, è probabile che il dispositivo non venga individuato, a causa di un problema di sincronizzazione di Exchange Connector. Vedere la sezione relativa al dispositivo Exchange ActiveSync non individuato da Exchange.
- Controllare la presenza di attività di invio di posta elettronica nei log di Exchange Connector e verificare l'eventuale presenza di errori. Un esempio del comando da cercare è InviaMessaggioPostaElettronica inviato dall'account di notifica a PostaElettronicaUtente.
- Prima di bloccare il dispositivo, Exchange Connector invia il messaggio di posta elettronica di attivazione. Se il dispositivo è offline, potrebbe non ricevere questo messaggio. Controllare se il client di posta elettronica del dispositivo recupera i messaggi di posta elettronica tramite Push anziché Poll. La perdita del messaggio da parte dell'utente potrebbe infatti dipendere anche da questa impostazione. Passare a Poll per vedere se il dispositivo riceve il messaggio di posta elettronica.

## <a name="noncompliant-device-not-blocked"></a>Dispositivo non conforme non bloccato

Nel caso di un dispositivo che non è conforme ma che continua a disporre dei diritti di accesso, procedere come segue.

- Esaminare i gruppi di destinazione e di esclusione. Se un utente non fa parte del gruppo di destinazione corretto o fa parte del gruppo di esclusione, non verrà bloccato. Viene verificata la conformità solo dei dispositivi degli utenti di un gruppo di destinazione.
- Assicurarsi che il dispositivo venga individuato. Exchange Connector punta a un server Accesso client di Exchange 2010 mentre l'utente è su un server di Exchange 2013? In questo caso, se la regola predefinita di Exchange è Consenti, anche se l'utente è incluso nel gruppo di destinazione, Intune non può riconoscere la connessione del dispositivo a Exchange.
- Verificare l'esistenza o lo stato di accesso del dispositivo in Exchange:
    - Usare il cmdlet PowerShell seguente per visualizzare un elenco di tutti i dispositivi mobili relativi a una cassetta postale: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Se il dispositivo non è incluso nell'elenco, non accede a Exchange.
    - Se il dispositivo è incluso nell'elenco, usare il cmdlet Get-CASmailbox -identity:’upn’ | fl per ottenere informazioni dettagliate sullo stato di accesso del dispositivo e passare tali informazioni al Supporto tecnico Microsoft.

## <a name="before-you-open-a-support-ticket"></a>Operazioni preliminari all'apertura di un ticket di supporto
Se le procedure descritte non consentono di risolvere il problema riscontrato, potrebbe essere necessario fornire alcune informazioni al Supporto tecnico Microsoft, ad esempio i log delle cassette postali OWA o i log di Exchange Connector.

### <a name="collecting-owa-mailbox-logs"></a>Raccolta dei log delle cassette postali OWA

1. Accedere a OWA e scegliere il simbolo delle impostazioni (ingranaggio) accanto al nome nell'angolo superiore destro.
2. Scegliere **Opzioni**.
3. Scegliere **Telefono** (può essere **Dispositivi mobili**) nella colonna a sinistra.
4. Scegliere **Dispositivi mobili** dal menu in alto.
5. Scegliere il dispositivo dall'elenco, quindi **Avvia registrazione**.
6. Quando richiesto, scegliere **Sì** nella finestra di dialogo popup.
7. Eseguire l'azione che ha causato il problema, in modo da riprodurlo.
8. Attendere uno o due minuti e tornare all'elenco dei telefoni in OWA. Verificare che il proprio telefono sia selezionato nell'elenco e quindi scegliere **Recupera il log** dal menu principale.
9. Si dovrebbe ricevere un messaggio di posta elettronica dal proprio indirizzo con un allegato. Quando si apre un ticket di supporto, indicare il contenuto del messaggio al supporto Microsoft.

### <a name="exchange-connector-logs"></a>Log di Exchange Connector

#### <a name="general-log-information"></a>Informazioni generali sui log
Per visualizzare i log di Exchange Connector, usare lo [strumento Visualizzatore di tracce dei servizi](https://docs.microsoft.com/en-us/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe). Per questo strumento è necessario scaricare l'SDK di Windows Server.

>[!NOTE]
>I log si trovano in C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs. Sono contenuti in una serie di 30 file di log che inizia da *Connector0.log* e termina con *Connector29.log*. Il rollover da un log all'altro avviene nel momento in cui si accumulano 10 MB di dati in un log. Dopo aver generato il log Connector29, il meccanismo riparte dal log Connector0, sovrascrivendo i file di log precedenti.

#### <a name="locating-sync-logs"></a>Individuazione dei log di sincronizzazione

- Per individuare una sincronizzazione completa nei log, è necessario cercare **full sync** (sincronizzazione completa). L'inizio di una sincronizzazione completa è contrassegnato dal testo seguente:

  'Handling command: Getting the mobile device list without a time filter (full sync) for <number> users` ('Gestione comando: recupero dell'elenco di dispositivi mobili senza filtro temporale (sincronizzazione completa) per X utenti')

  La parte finale del log relativo a una sincronizzazione completa è simile al seguente:

  Getting the mobile device list without a time filter (full sync) for 4 users completed successfully. (Recupero dell'elenco di dispositivi mobili senza filtro temporale (sincronizzazione completa) per 4 utenti eseguito.) Details: Inventory command result - Devices synced: 0 Command ID: commandIDGUID' Exchange health: 'Server health 'Name: 'PowerShellExchangeServer: <Name=mymailservername>' Status: Connected',' (Dettagli: risultati comando inventario - Dispositivi sincronizzati: 0 ID comando: commandIDGUID' Integrità Exchange: 'Integrità server 'Nome: 'PowerShellExchangeServer: <Nome=nomeserverposta>' Stato: Connesso',')

- Individuare una sincronizzazione rapida (delta) nei log eseguendo la ricerca di **quick sync** (sincronizzazione rapida).

##### <a name="exceptions-in-get-next-command"></a>Eccezioni in Get next command (Recupera comando successivo)
Verificare nei log di Exchange Connector l'eventuale presenza di eccezioni in **Get next command** (Recupera comando successivo) e comunicarne il contenuto al Supporto tecnico Microsoft.

#### <a name="verbose-logging"></a>Registrazione dettagliata

Per abilitare la registrazione dettagliata:

1.  Aprire il file di configurazione di traccia di Exchange Connector. Il file si trova in: %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml.
2.  Individuare TraceSourceLine con la chiave seguente: OnPremisesExchangeConnectorService
3.  Modificare il valore del nodo **SourceLevel** da **Warning ActivityTracing** (predefinito) a **Verbose ActivityTracing**, come illustrato di seguito.

    <TraceSourceLine> <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key> <Value xsi:type="TraceSource"> <SourceLevel>All</SourceLevel> <Listeners> <Listener> <ListenerType>CircularTraceListener</ListenerType> <SourceLevel>Verbose ActivityTracing</SourceLevel> <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes> <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName> <FileQuota>30</FileQuota> </Listener> </Listeners> </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni non risultano utili, è anche possibile [ottenere supporto per Microsoft Intune](get-support.md).
