---
title: Risolvere i problemi di accesso condizionale
description: Operazioni da eseguire quando gli utenti non riescono ad accedere alle risorse usando l'accesso condizionale di Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 642a4da6a1ca3c368e90f2d3007c1fc6a068af78
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189232"
---
# <a name="troubleshoot-conditional-access"></a>Risolvere i problemi di accesso condizionale

È possibile proteggere l'accesso ai servizi di Office 365 come Exchange Online, SharePoint Online, Skype for Business Online, Exchange locale e altri servizi tramite Intune e l'accesso condizionale. Questa funzionalità consente di assicurarsi che l'accesso alle risorse aziendali sia limitato ai dispositivi registrati con Intune e conformi alle regole di accesso condizionale impostate nella console di amministrazione di Intune o in Azure Active Directory. Questo articolo descrive cosa fare quando gli utenti non riescono ad accedere alle risorse protette con accesso condizionale o quando gli utenti possono accedere alle risorse protette mentre in realtà dovrebbero essere bloccati.

## <a name="requirements-for-conditional-access"></a>Requisiti per l'accesso condizionale

Il funzionamento dell'accesso condizionale è subordinato al rispetto dei requisiti seguenti:

- Il dispositivo deve essere registrato con Intune e gestito da Intune.
- Sia il dispositivo che l'utente devono essere conformi ai criteri di conformità assegnati in Intune.
- Per impostazione predefinita, all'utente deve essere assegnato un criterio di conformità del dispositivo. Ciò può dipendere dalla configurazione dell'impostazione **Contrassegna i dispositivi senza criteri di conformità assegnati come** in **Conformità del dispositivo** > **Impostazioni dei criteri di conformità** nel portale di amministrazione di Intune.
-   È necessario attivare Exchange ActiveSync sul dispositivo se l'utente usa il client di posta elettronica nativo del dispositivo anziché Outlook. Tale attivazione avviene automaticamente per i dispositivi iOS, Windows Phone e Android.
-   Intune Exchange Connector deve essere configurato correttamente. Per altre informazioni, vedere [Troubleshooting the Exchange Connector in Microsoft Intune](troubleshoot-exchange-connector.md) (Risoluzione dei problemi di Exchange Connector in Microsoft Intune).

È possibile visualizzare queste condizioni per ogni dispositivo nel portale di Azure e nel report di inventario dei dispositivi.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>I dispositivi vengono visualizzati come conformi, ma gli utenti sono comunque bloccati

- I dispositivi Android non Knox non potranno accedere fino a quando l'utente non fa clic sul collegamento **Get Started Now** (Inizia ora) nel messaggio di quarantena ricevuto. Questo vale anche se l'utente è già registrato in Intune. Se l'utente non riceve il messaggio di posta elettronica con il collegamento sul telefono, può usare un PC per accedere alla posta elettronica e inoltrare il messaggio a un account di posta elettronica nel proprio dispositivo.
- In occasione della prima registrazione del dispositivo, la registrazione delle informazioni di conformità può richiedere tempo. Attendere qualche minuto e riprovare.
- Nei dispositivi iOS un profilo di posta elettronica esistente potrebbe bloccare la distribuzione di un profilo di posta elettronica creato dall'amministratore di Intune assegnato all'utente, rendendo in tal modo il dispositivo non conforme. In questo caso, il Portale aziendale comunicherà all'utente che esiste un problema di mancata conformità, perché il profilo di posta elettronica è stato configurato manualmente, e richiederà all'utente di rimuovere il profilo. Una volta rimosso il profilo di posta elettronica esistente, il profilo di posta elettronica di Intune verrà distribuito correttamente. Per prevenire questo problema, indicare agli utenti di rimuovere i profili di posta elettronica esistenti nel dispositivo prima della registrazione.
- Un dispositivo può restare bloccato in uno stato di controllo della conformità, impedendo all'utente di avviare un altro check-in. Se un dispositivo è in questo stato, procedere come segue:
  - Assicurarsi che il dispositivo usi la versione più recente dell'app Portale aziendale.
  - Riavviare il dispositivo.
  - Vedere se il problema esiste su altre reti, ad esempio cellulare, Wi-Fi e così via.

  Se il problema esiste, contattare il supporto tecnico Microsoft, come descritto in [Come ottenere supporto per Microsoft Intune](get-support.md).
- È possibile che alcuni dispositivi Android sembrino crittografati, ma l'app Portale aziendale non li riconosce come tali e li contrassegna come non conformi. In questa circostanza, l'utente visualizzerà una notifica nell'app Portale aziendale in cui viene chiesto di impostare un passcode di avvio per il dispositivo. Dopo aver toccato la notifica e confermato il PIN o la password esistente, scegliere l'opzione **Require PIN to start device** (Richiedi PIN per avviare il dispositivo) nella schermata **Secure start-up** (Avvio sicuro) e selezionare il pulsante **Controlla conformità** del dispositivo nell'app Portale aziendale. Il dispositivo sarà riconosciuto come crittografato. 
  > [!NOTE]
  > Alcuni produttori di dispositivi eseguono la crittografia dei propri dispositivi usando un PIN predefinito anziché un PIN impostato dall'utente. Intune considera la crittografia tramite il PIN predefinito come non sicura e contrassegna i dispositivi che la utilizzano come non conformi fino a quando l'utente non crea un nuovo PIN non predefinito.
- Un dispositivo Android registrato e conforme può comunque essere bloccato e ricevere un avviso di quarantena quando tenta di accedere alle risorse aziendali. In questo caso, assicurarsi che l'app Portale aziendale non sia in esecuzione, quindi scegliere il collegamento **Get Started Now** (Inizia ora) nel messaggio di posta elettronica di quarantena per attivare la valutazione. Questa operazione è necessaria solo quando l'accesso condizionale viene abilitato per la prima volta.

## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>I dispositivi sono bloccati e non è stato ricevuto alcun messaggio di posta elettronica di quarantena

- Verificare che il dispositivo sia presente nella console di amministrazione di Intune come dispositivo Exchange ActiveSync. In caso negativo, è probabile che il dispositivo non venga individuato, a causa di un problema di Exchange Connector. Vedere [Risolvere i problemi di Intune On-Premises Exchange Connector](troubleshoot-exchange-connector.md) per altre informazioni.
- Prima di bloccare il dispositivo, Exchange Connector invia un messaggio di posta elettronica di attivazione (quarantena). Se il dispositivo è offline, potrebbe non ricevere il messaggio di attivazione. 
- Controllare se il client di posta elettronica nel dispositivo è configurato per recuperare la posta elettronica usando **Push** invece di **Polling**. In caso affermativo, ciò potrebbe essere la causa del mancato recapito del messaggio di posta elettronica. Passare a **Polling** per vedere se il dispositivo riceve il messaggio di posta elettronica.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>I dispositivi non sono conformi, ma gli utenti non sono bloccati

- Nei PC Windows, l'accesso condizionale blocca solo le app native di posta elettronica, Office 2013 con autenticazione moderna o Office 2016. Il blocco delle versioni precedenti di Outlook o di tutte le app di posta elettronica nei PC Windows richiede le configurazioni Registrazione dispositivo Azure AD e Active Directory Federation Services (AD FS) come spiegato in [Configurare SharePoint Online ed Exchange Online per l'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication). 
- Se viene cancellato o ritirato da Intune in modo selettivo, il dispositivo potrebbe continuare ad avere accesso per alcune ore dopo il ritiro. Questo avviene perché Exchange memorizza nella cache i diritti di accesso per 6 ore. Prendere in considerazione altri metodi di protezione dei dati nei dispositivi ritirati in questo scenario.
- I dispositivi Surface Hub supportano l'accesso condizionale, tuttavia, per eseguire una corretta valutazione, è necessario distribuire i criteri di conformità ai gruppi di dispositivi e non ai gruppi di utenti.
- Controllare le assegnazioni per i criteri di conformità e i criteri di accesso condizionale. Un utente che non fa parte del gruppo a cui viene assegnato il criterio oppure che fa parte di un gruppo da escludere viene bloccato. Viene verificata la conformità solo dei dispositivi di utenti che fanno parte di un gruppo di destinazione.

## <a name="noncompliant-device-is-not-blocked"></a>Il dispositivo non conforme non è bloccato

Nel caso di un dispositivo che non è conforme ma che continua a disporre dei diritti di accesso, procedere come segue.
- Esaminare i gruppi di destinazione e di esclusione. Se un utente non fa parte del gruppo di destinazione corretto o fa parte del gruppo di esclusione, non verrà bloccato. Viene verificata la conformità solo dei dispositivi degli utenti di un gruppo di destinazione.
- Assicurarsi che il dispositivo venga individuato. Exchange Connector punta a un server Accesso client di Exchange 2010 mentre l'utente è su un server di Exchange 2013? In questo caso, se la regola predefinita di Exchange è Consenti, anche se l'utente è incluso nel gruppo di destinazione, Intune non può riconoscere la connessione del dispositivo a Exchange.
- Verificare l'esistenza o lo stato di accesso del dispositivo in Exchange:
  - Usare il cmdlet PowerShell seguente per visualizzare un elenco di tutti i dispositivi mobili relativi a una cassetta postale: "Get-ActiveSyncDeviceStatistics -mailbox mbx'. Se il dispositivo non è incluso nell'elenco, non accede a Exchange.
  - Se il dispositivo è incluso nell'elenco, usare il cmdlet Get-CASmailbox -identity:’upn’ | fl per ottenere informazioni dettagliate sullo stato di accesso del dispositivo e passare tali informazioni al Supporto tecnico Microsoft.

## <a name="next-steps"></a>Passaggi successivi
Se queste informazioni non risultano utili, è anche possibile [ottenere supporto per Microsoft Intune](get-support.md).
