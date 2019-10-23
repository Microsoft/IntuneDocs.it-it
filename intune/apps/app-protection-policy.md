---
title: Panoramica dei criteri di protezione app
titleSuffix: Microsoft Intune
description: In questo articolo viene descritto come i criteri di protezione delle app di Microsoft Intune consentono di proteggere i dati aziendali ed evitare la perdita di dati.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 31bb0e2ff4379c55829afc65fb99b768c9099a47
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72498944"
---
# <a name="app-protection-policies-overview"></a>Panoramica dei criteri di protezione app

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I criteri di protezione delle app sono regole che assicurano che i dati di un'organizzazione rimangano sicuri o contenuti in un'app gestita. Un criterio può essere una regola che viene applicata quando l'utente tenta di accedere o spostare dati "aziendali" o un set di azioni vietate o monitorate quando l'utente è all'interno dell'app. Un'app gestita è un'app a cui sono applicati criteri di protezione delle app e che può essere gestita da Intune.

I criteri di protezione delle app di Gestione di applicazioni mobili (MAM, Mobile Application Management) consentono di gestire e proteggere i dati dell'organizzazione all'interno di un'applicazione. Con **MAM senza registrazione** un'app aziendale o dell'istituto di istruzione contenente dati sensibili può essere gestita in quasi tutti i [dispositivi](app-management.md#app-management-capabilities-by-platform), inclusi i dispositivi personali in scenari **Bring Your Own Device** (BYOD). La maggior parte delle app di produttività, ad esempio le app per Microsoft Office, può essere gestita da MAM di Intune. Vedere l'elenco ufficiale delle [app protette da Microsoft Intune](apps-supported-intune-apps.md) disponibili al pubblico.

## <a name="how-you-can-protect-app-data"></a>Protezione dei dati delle app
I dipendenti usano dispositivi mobili per le attività personali e aziendali. Se da una parte è necessario assicurarsi che i dipendenti possano essere produttivi, dall'altra è indispensabile prevenire la perdita di dati, sia intenzionale sia non intenzionale. È anche opportuno proteggere i dati aziendali a cui si accede da dispositivi non gestiti dall'amministratore.

È possibile usare i criteri di protezione delle app di Intune **in modo indipendente da qualsiasi soluzione di gestione di dispositivi mobili (MDM)** . Questa indipendenza consente di proteggere i dati aziendali con o senza registrazione dei dispositivi in una soluzione di gestione di dispositivi. Implementando i **criteri a livello di app** è possibile limitare l'accesso alle risorse aziendali e mantenere i dati all'interno del reparto IT.

### <a name="app-protection-policies-on-devices"></a>Criteri di protezione delle app nei dispositivi

I criteri di protezione delle app possono essere configurati per app in esecuzione su dispositivi con le caratteristiche seguenti:

- **Registrati in Microsoft Intune:** questi dispositivi sono in genere di proprietà aziendale.

- **Registrati in una soluzione di gestione di dispositivi mobili (MDM) di terze parti:** questi dispositivi sono in genere di proprietà aziendale.

  > [!NOTE]
  > I criteri di gestione delle app per dispositivi mobili non devono essere usati con soluzioni di gestione delle app per dispositivi mobili o di contenitore protetto di terze parti.

- **Non registrati in alcuna soluzione di gestione di dispositivi mobili:** questi dispositivi sono in genere dispositivi di proprietà dei dipendenti non gestiti o registrati in Intune o in altre soluzioni MDM.

> [!IMPORTANT]
> È possibile creare criteri di gestione delle app per dispositivi mobili per le app di Office per dispositivi mobili che si connettono ai servizi di Office 365. È anche possibile proteggere l'accesso alle cassette postali locali di Exchange creando i criteri di protezione delle app di Intune per Outlook per iOS e Android abilitati con l'autenticazione moderna ibrida. Prima di usare questa funzionalità, assicurarsi che siano soddisfatti i [requisiti di Outlook per iOS e Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). I criteri di protezione delle app non sono supportati per le altre app che si connettono ai servizi locali di Exchange o SharePoint.

## <a name="benefits-of-using-app-protection-policies"></a>Vantaggi dell'uso dei criteri di protezione delle app

I vantaggi più rilevanti dell'uso dei criteri di protezione delle app sono i seguenti:

- **Protezione dei dati aziendali a livello di app.** Dal momento che la gestione delle app per dispositivi mobili non richiede la gestione dei dispositivi, è possibile proteggere i dati aziendali su dispositivi sia gestiti sia non gestiti. La gestione dei dati è incentrata sull'identità dell'utente che elimina il requisito della gestione dei dispositivi.

- **La produttività degli utenti finali non è compromessa e i criteri non vengono applicati quando l'app è usata in un contesto personale.** I criteri vengono applicati solo in un contesto aziendale, offrendo così la possibilità di proteggere i dati aziendali senza modificare i dati personali.

- **I criteri di protezione delle app assicurano che le misure di sicurezza a livello di app siano presenti**. Ad esempio, è possibile:
  - Richiedere un PIN per aprire un'app in un contesto aziendale 
  - Controllare la condivisione dei dati tra le app 
  - Impedire il salvataggio dei dati delle app aziendali in un percorso di archiviazione personale

- **MDM in aggiunta a MAM verifica che il dispositivo sia protetto**. Ad esempio, è possibile richiedere un PIN per accedere al dispositivo oppure distribuire le app gestite al dispositivo. È anche possibile distribuire app per dispositivi con la soluzione MDM, per fornire maggiore controllo sulla gestione di app.

L'uso di soluzioni MDM con criteri di protezione delle app comporta vantaggi aggiuntivi e le aziende possono usare contemporaneamente criteri di protezione delle app con o senza soluzioni MDM. Si consideri ad esempio un dipendente che usa sia un telefono assegnato dall'azienda che il tablet personale. Il telefono aziendale è registrato in MDM e protetto dai criteri di protezione delle app, mentre il dispositivo personale è protetto solo dai criteri di protezione delle app.

Se si applica un criterio MAM per l'utente senza impostare lo stato del dispositivo, l'utente riceverà il criterio MAM sia nel dispositivo BYOD che nel dispositivo gestito da Intune. È anche possibile applicare un criterio MAM basato sullo stato gestito. Quando si crea un criterio di protezione dell'app, selezionare quindi **No** accanto a **Includi tutti i tipi di app**. Effettuare quindi una delle operazioni seguenti:
- Applicare un criterio MAM meno rigoroso ai dispositivi gestiti da Intune e applicare un criterio MAM più restrittivo ai dispositivi non registrati in MDM.
- Applicare un criterio MAM solo ai dispositivi non registrati.

## <a name="supported-platforms-for-app-protection-policies"></a>Piattaforme supportate per i criteri di protezione delle app

Intune offre un'ampia gamma di funzionalità che consente di usare le app necessarie nei dispositivi in cui le si vuole eseguire. Per altre informazioni, vedere [Funzionalità di gestione delle app per piattaforma](app-management.md#app-management-capabilities-by-platform).

Il supporto della piattaforma dei criteri di protezione delle app di Intune è allineato al supporto della piattaforma delle applicazioni per dispositivi mobili di Office per dispositivi Android e iOS. Per informazioni dettagliate, vedere la sezione **App per dispositivi mobili** in [Requisiti di sistema per Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

> [!IMPORTANT]
> Il portale aziendale di Intune deve essere presente nel dispositivo per ricevere i criteri di protezione delle app in Android. Per altre informazioni, vedere [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](../fundamentals/end-user-mam-apps-android.md#access-apps).

## <a name="how-app-protection-policies-protect-app-data"></a>Come i criteri di protezione delle app proteggono i dati dell'app

### <a name="apps-without-app-protection-policies"></a>App senza criteri di protezione delle app

Quando le app vengono usate senza restrizioni, può crearsi una commistione di dati aziendali e personali. I dati aziendali possono finire in percorsi come l'archivio personale o essere trasferiti ad app esterne al proprio ambito, causando la perdita di dati. Le frecce nell'immagine seguente indicano lo spostamento senza restrizioni dei dati tra le app sia aziendali che personali e i percorsi di archiviazione.

![Immagine concettuale dello spostamento dati tra app senza criteri attivi](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>Protezione dei dati con i criteri di protezione delle app

È possibile usare i criteri di protezione delle app per impedire il salvataggio dei dati aziendali nell'archiviazione locale del dispositivo (vedere l'immagine seguente). È anche possibile limitare lo spostamento dei dati ad altre app non protette dai criteri di protezione delle app. Le impostazioni dei criteri di protezione delle app includono:
- Criteri di rilocazione dei dati, ad esempio **Impedisci Salva con nome** e **Limita le operazioni taglia, copia e incolla**.
- Impostazioni dei criteri di accesso, ad esempio **Richiedi PIN semplice per l'accesso** e **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**.

![Immagine concettuale dei dati aziendali protetti da criteri](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>Protezione dei dati con i criteri di protezione delle app nei dispositivi gestiti da una soluzione MDM

L'immagine precedente illustra i livelli di protezione offerti sia da una soluzione MDM sia dai criteri di protezione delle app.

![Immagine che mostra il funzionamento dei criteri di protezione delle app sui dispositivi BYOD](./media/app-protection-policy/app-protection-policies-with-mdm.png)

La soluzione MDM aggiunge valore nel modo seguente:

- Registra il dispositivo
- Distribuisce le app al dispositivo
- Permette la conformità e la gestione continua del dispositivo

I criteri di protezione delle app aggiungono valore nel modo seguente:

- Aiutano a proteggere i dati aziendali dalla divulgazione ad app e a servizi consumer
- Applicano restrizioni, ad esempio *Salva con nome*, *Appunti* o *PIN*, ad app client
- Se necessario, cancellano i dati aziendali dalle app senza rimuovere le app dal dispositivo

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>Protezione dei dati con i criteri di protezione delle app senza registrazione

L'immagine seguente illustra il funzionamento dei criteri di protezione dei dati a livello di app senza MDM.

![Immagine che illustra il funzionamento dei criteri di protezione delle app nei dispositivi senza registrazione (dispositivi non gestiti)](./media/app-protection-policy/app-protection-policies-without-mdm.png)

Per i dispositivi BYOD non registrati in alcuna soluzione MDM, i criteri di protezione delle app possono aiutare a proteggere i dati aziendali a livello di app.
Esistono tuttavia alcune limitazioni da tenere in considerazione, ad esempio:

- Non è possibile distribuire le app al dispositivo. L'utente finale deve ottenere le app dall'archivio.
- Non è possibile eseguire il provisioning dei profili certificato in questi dispositivi.
- Non è possibile eseguire il provisioning delle impostazioni Wi-Fi e VPN aziendali in questi dispositivi.

## <a name="apps-you-can-manage-with-app-protection-policies"></a>App gestibili con i criteri di protezione delle app

Qualsiasi app integrata con [Intune App SDK](../developer/app-sdk.md) o di cui è stato eseguito il wrapping tramite lo [strumento di wrapping delle app di Intune](../developer/apps-prepare-mobile-application-management.md) può essere gestita mediante i criteri di protezione delle app di Intune. Vedere l'elenco ufficiale delle [app protette di Microsoft Intune](apps-supported-intune-apps.md) che sono state compilate usando questi strumenti e sono disponibili al pubblico.

Il team di sviluppo di Intune SDK verifica e gestisce attivamente il supporto per le app compilate con la piattaforme native Android, iOS (Obj-C, Swift), Xamarin, Xamarin.Forms e Cordova. Anche se alcuni clienti sono riusciti a integrare Intune SDK con altre piattaforme, ad esempio React Native e NativeScript, Microsoft non offre linee guida o plug-in specifici per gli sviluppatori di app che usano piattaforme diverse da quelle supportate da Microsoft.

[Intune App SDK](../developer/app-sdk.md) usa alcune funzionalità di autenticazione moderne e avanzate delle [librerie di autenticazione di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) per le versioni dell'SDK sia di Microsoft che di terze parti. Di conseguenza, [Microsoft Authentication Library](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) (MSAL) non funziona correttamente con molti degli scenari di base, ad esempio l'autenticazione nel servizio Protezione app di Intune e l'avvio condizionale. Dato che le linee guida generali del team per le identità di Microsoft prevedono il passaggio a MSAL per tutte le app Microsoft Office, [Intune App SDK](../developer/app-sdk.md) dovrà prima o poi supportare questa libreria, ma non esistono piani precisi al momento.

## <a name="end-user-requirements-to-use-app-protection-policies"></a>Requisiti dell'utente finale per l'uso dei criteri di protezione delle app

L'elenco seguente contiene i requisiti dell'utente finale per poter usare i criteri di protezione delle app in un'app gestita da Intune:

- L'utente finale deve avere un account Azure Active Directory (AAD). Per imparare a creare gli utenti Intune in Azure Active Directory, vedere [Aggiungere utenti e concedere autorizzazioni amministrative a Intune](../fundamentals/users-add.md).

- L'utente finale deve avere una licenza per Microsoft Intune assegnata all'account Azure Active Directory. Per informazioni su come assegnare le licenze di Intune agli utenti finali, vedere [Gestire le licenze di Intune](../fundamentals/licenses-assign.md).

- L'utente finale deve appartenere a un gruppo di sicurezza che è la destinazione dei criteri di protezione dell'app. Gli stessi criteri di protezione devono avere come destinazione l'app specifica in uso. I criteri di protezione delle app possono essere creati e distribuiti nella console di Intune nel [portale di Azure](https://portal.azure.com). È possibile creare gruppi di sicurezza simultaneamente nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com).

- L'utente finale deve accedere all'app usando il proprio account AAD.

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Criteri di protezione delle app per app Microsoft Office

Quando si usano i criteri di protezione delle app con app Microsoft Office, è necessario tenere presenti alcuni requisiti aggiuntivi.

### <a name="outlook-mobile-app"></a>App Outlook per dispositivi mobili
Per poter usare l'[app Outlook per dispositivi mobili](https://products.office.com/outlook), sono necessari i requisiti aggiuntivi elencati di seguito:

- L'utente finale deve avere l'app Outlook per dispositivi mobili installata nel dispositivo.
- L'utente finale deve avere una licenza e una cassetta postale di [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) collegata al proprio account Azure Active Directory.

  >[!NOTE]
  > L'app Outlook per dispositivi mobili attualmente supporta solo Protezione app di Intune per Microsoft Exchange Online e [Exchange Server con autenticazione moderna ibrida](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). Non supporta Exchange in Office 365 dedicato.

### <a name="word-excel-and-powerpoint"></a>Word, Excel e PowerPoint
Per poter usare le app [Word, Excel e PowerPoint](https://products.office.com/business/office), sono necessari i requisiti aggiuntivi elencati di seguito:

- L'utente finale deve avere una licenza per [Office 365 Business o Enterprise](https://products.office.com/business/compare-more-office-365-for-business-plans) collegata all'account Azure Active Directory. La sottoscrizione deve includere le app di Office nei dispositivi mobili e può includere un account di archiviazione cloud con [OneDrive for Business](https://onedrive.live.com/about/business/). È possibile assegnare licenze di Office 365 nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) seguendo queste [istruzioni](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc).

- L'utente finale deve aver configurato un percorso gestito usando la funzionalità Salva con nome granulare nell'impostazione dei criteri di protezione delle applicazioni "Impedisci Salva con nome". Se il percorso gestito è OneDrive, ad esempio, l'app [OneDrive](https://onedrive.live.com/about/) deve essere configurata nell'app Word, Excel o PowerPoint dell'utente finale.

- Se il percorso gestito è OneDrive, l'app deve essere impostata come destinazione dei criteri di protezione delle app distribuiti all'utente finale.

  >[!NOTE]
  > Le app per dispositivi mobili di Office attualmente supportano solo SharePoint Online e SharePoint locale.

### <a name="managed-location-needed-for-office"></a>Percorso gestito per Office
È un percorso gestito, ad esempio OneDrive, per Office. Intune contrassegna tutti i dati nell'app come "aziendali" o "personali". Quando hanno origine da una sede aziendale, i dati vengono considerati "aziendali". Per le app di Office, Intune considera come sedi aziendali la posta elettronica (Exchange) o l'archiviazione cloud (app OneDrive con un account OneDrive for Business).

### <a name="skype-for-business"></a>Skype for Business
Per poter usare Skype for Business, sono necessari requisiti aggiuntivi. Vedere i requisiti della licenza per [Skype for Business](https://products.office.com/skype-for-business/it-pros). Per le configurazioni ibride e locali di Skype for Business, vedere rispettivamente [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (Disponibilità generale pe l'autenticazione moderna ibrida per Skype for Business) [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (Autenticazione moderna per Skype for Business locale con AAD).

## <a name="app-protection-global-policy"></a>Criteri globali per la protezione delle app

Un amministratore di OneDrive che passa ad **admin.office.com** e seleziona l'accesso **Dispositivo** può impostare i controlli **Gestione di applicazioni mobili** sulle app client di OneDrive e SharePoint. 

Tali impostazioni, rese disponibili nella console di amministrazione di OneDrive, configurano uno speciale criterio di protezione delle app Intune denominato **globale**. Questi criteri globali si applicano a tutti gli utenti del tenant e non è possibile controllarne la destinazione. 

Dopo l'abilitazione, le app OneDrive e SharePoint per iOS e Android vengono protette con le impostazioni selezionate per impostazione predefinita. Un professionista IT può modificare questi criteri nella console di Intune per aggiungere più app di destinazione, oltre che modificare qualsiasi impostazione dei criteri. 

Per impostazione predefinita, può essere presente un solo criterio **globale** per ogni tenant. È comunque possibile usare le [API Graph di Intune](../developer/intune-graph-apis.md) per creare criteri globali aggiuntivi per ogni tenant, ma questa operazione non è consigliata. La creazione di criteri globali aggiuntivi non è consigliata perché la risoluzione dei problemi di implementazione di tali criteri può diventare complicata.

Il criterio **globale** si applica a tutti gli utenti del tenant, ma qualsiasi criterio standard di protezione delle app di Intune sostituirà tali impostazioni.

## <a name="app-protection-features"></a>Funzionalità di protezione delle app

### <a name="multi-identity"></a>Supporto per identità multiple

Il supporto di identità multiple consente a un'app di supportare più destinatari, che possono essere sia "aziendali" sia "personali". Gli account aziendali e dell'istituto di istruzione vengono usati dai destinatari "aziendali", mentre gli account personali vengono usati per i destinatari di tipo consumer, ad esempio da utenti di Microsoft Office. Un'app che supporta identità multiple può essere rilasciata pubblicamente. In questo caso i criteri di protezione delle app vengono applicati solo quando l'app è usata nel contesto aziendale e dell'Istituto di istruzione ("aziendale"). Il supporto di identità multiple usa [Intune App SDK](../developer/app-sdk.md) per applicare i criteri di protezione delle app solo all'account aziendale o dell'istituto di istruzione registrato nell'app. Se nell'app viene registrato un account personale, i dati rimangono invariati.

Per un esempio di contesto "personale", si consideri un utente che ha iniziato un nuovo documento di Word. Questo viene considerato di contesto personale e pertanto i criteri di Protezione app di Intune non vengono applicati. Dopo che sarà salvato nell'account di OneDrive "aziendale", il documento verrà considerato di contesto "aziendale" e verranno quini applicati i criteri di Protezione app di Intune.

Per un esempio di contesto di lavoro o "aziendale", si consideri un utente che avvia l'app OneDrive usando l'account aziendale. Nel contesto di lavoro, non può spostare i file in una posizione di archiviazione personale. Quando in seguito tale utente usa OneDrive con il proprio account personale, può copiare e spostare i dati da OneDrive senza restrizioni.

Outlook offre una visualizzazione combinata sia dei messaggi di posta elettronica "personali" che di quelli "aziendali". In questa situazione l'app Outlook richiede il PIN di Intune all'avvio.

Per altre informazioni sulle identità multiple in Intune, vedere [MAM e identità multiple](apps-supported-intune-apps.md).

### <a name="intune-app-pin"></a>PIN dell'app Intune

Il PIN è un codice di accesso usato per verificare che l'accesso ai dati dell'organizzazione in un'applicazione venga eseguito dall'utente appropriato.

**Richiesta di PIN**<br>
Intune richiede l'immissione del PIN dell'app dell'utente quando quest'ultimo sta per accedere ai dati "aziendali". Nelle app a identità multipla, ad esempio Word,Excel o PowerPoint, all'utente viene richiesto il PIN quando tenta di aprire un file o un documento "aziendale". Nelle app a identità singola, ad esempio app line-of-business gestite tramite lo [strumento di wrapping delle app di Intune](../developer/apps-prepare-mobile-application-management.md), il PIN viene richiesto all'avvio, poiché [Intune App SDK](../developer/app-sdk.md) riconosce che l'esperienza dell'utente nell'app è sempre "aziendale".

**Frequenza di richiesta del PIN**<br>
L'amministratore IT può definire l'impostazione dei criteri di protezione delle app di Intune **Controlla di nuovo i requisiti di accesso dopo (minuti)** nella console di amministrazione di Intune. Questa impostazione specifica il periodo di tempo che deve trascorrere prima che i requisiti di accesso vengano controllati nel dispositivo e prima che venga nuovamente visualizzata la schermata del PIN dell'applicazione. Ecco tuttavia alcuni dettagli importanti sul PIN che influiscono sulla frequenza con cui viene richiesto il PIN all'utente:

- **Il PIN viene condiviso tra le app dello stesso server di pubblicazione per migliorare l'usabilità:**<br> in iOS, un solo PIN viene condiviso da tutte le app **dello stesso server di pubblicazione**. In Android un solo PIN viene condiviso da tutte le app.
  - **Il comportamento di *Controlla di nuovo i requisiti di accesso dopo (minuti)* dopo un riavvio del dispositivo:**<br> un "timer del PIN" tiene traccia del numero di minuti di inattività che determinano quando visualizzare di nuovo il PIN dell'app di Intune. In iOS, il timer del PIN è indipendente dal riavvio del dispositivo. Di conseguenza, il riavvio del dispositivo non ha effetto sul numero di minuti durante i quali l'utente è rimasto inattivo da un'app iOS con i criteri PIN di Intune. In Android, il timer del PIN viene reimpostato al riavvio del dispositivo. Di conseguenza, le app Android con criteri di Intune richiederanno probabilmente un PIN dell'app indipendentemente dal valore dell'impostazione 'Controlla di nuovo i requisiti di accesso dopo (minuti)' **dopo un riavvio del dispositivo**.  
  - **Il timer associato al PIN è di natura sequenziale:**<br> quando si immette il PIN per accedere a un'app (app A) e quest'ultima lascia la posizione in primo piano (area di input principale) nel dispositivo, il timer del PIN immesso viene reimpostato. Le app (ad esempio l'app B) che condividono questo PIN non richiederanno all'utente di immettere il PIN, perché il timer è stato reimpostato. La richiesta di immissione del PIN verrà visualizzata di nuovo quando il valore di 'Controlla di nuovo i requisiti di accesso dopo (minuti)' verrà nuovamente raggiunto.

Per i dispositivi iOS, anche se il PIN è condiviso tra app di diversi server di pubblicazione, la richiesta verrà nuovamente visualizzata quando il valore di **Controlla di nuovo i requisiti di accesso dopo (minuti)** verrà nuovamente raggiunto per l'app che non è l'area di input principale. Quindi, ad esempio, un utente ha l'app _A_ dal server di pubblicazione _X_ e l'app _B_ dal server di pubblicazione _Y_ e queste due app condividono lo stesso PIN. L'utente è concentrato sull'app _A_ (in primo piano) e l'app _B_ è ridotta a icona. Quando si raggiunge il valore di **Controlla di nuovo i requisiti di accesso dopo (minuti)** e si passa all'app _B_, è necessario il PIN.

  >[!NOTE]
  > Per verificare più spesso i requisiti di accesso dell'utente (ad esempio tramite la richiesta del PIN), in particolare per le app usate di frequente, è consigliabile ridurre il valore dell'impostazione 'Controlla di nuovo i requisiti di accesso dopo (minuti)'.

**PIN predefiniti delle app per Outlook e OneDrive**<br>
Il funzionamento del PIN di Intune si basa su un timer basato sull'inattività, vale a dire il valore di **Controlla di nuovo i requisiti di accesso dopo (minuti)** . Di conseguenza, le richieste del PIN di Intune vengono visualizzate in modo indipendente dalle richieste dei PIN delle app predefiniti per Outlook e OneDrive spesso associate all'avvio dell'app per impostazione predefinita. Se l'utente riceve entrambe le richieste di PIN contemporaneamente, il comportamento predefinito prevede che il PIN di Intune abbia la precedenza.

**Sicurezza del PIN di Intune**<br>
Il PIN consente l'accesso ai dati aziendali nell'app solo all'utente appropriato. Pertanto, un utente finale deve accedere con il proprio account aziendale o dell'istituto di istruzione prima di poter impostare o reimpostare il PIN dell'app Intune. Questa autenticazione viene gestita da Azure Active Directory tramite scambio di token di sicurezza e non è trasparente per [Intune App SDK](../developer/app-sdk.md). Dal punto di vista della sicurezza, il modo migliore per proteggere i dati aziendali o dell'istituto di istruzione è la crittografia. La crittografia non è correlata al PIN dell'app, ma costituisce i criteri di protezione delle app.

**PIN di Intune - Protezione da attacchi di forza bruta**<br>
Nell'ambito dei criteri del PIN dell'app, l'amministratore IT può impostare il numero massimo di volte in cui un utente può provare a eseguire l'autenticazione del PIN prima di bloccare l'app. Dopo aver raggiunto il numero di tentativi, [Intune App SDK](../developer/app-sdk.md) può cancellare i dati "aziendali" nell'app.
  
**Impostazione di due PIN in app dello stesso editore**<br>
MAM (in iOS) consente attualmente un PIN a livello di applicazione con caratteri alfanumerici e caratteri speciali denominato "passcode", che richiede la partecipazione di applicazioni, ad esempio WXP, Outlook, Managed Browser, Yammer, per integrare [Intune App SDK per iOS](../developer/app-sdk-ios.md). In caso contrario, le impostazioni del passcode non vengono applicate correttamente per le applicazioni di destinazione. Questa è una funzionalità rilasciata in Intune SDK per iOS versione 7.1.12.

Per supportare questa funzionalità e garantire la compatibilità con le versioni precedenti di Intune SDK per iOS, tutti i PIN (numerici o passcode) nella versione 7.1.12 e versioni successive vengono gestiti separatamente dal PIN numerico nelle versioni precedenti dell'SDK. Pertanto, se un dispositivo dispone di applicazioni con le versioni di Intune SDK per iOS prima e dopo la versione 7.1.12 dallo stesso editore, è necessario impostare due PIN. I due PIN (per ogni app) non sono correlati in alcun modo, vale a dire che devono soddisfare i criteri di protezione delle app applicati all'app. Di conseguenza, *solo* se alle app A e B sono applicati gli stessi criteri (in riferimento al PIN), l'utente può configurare lo stesso PIN due volte. 

Questo comportamento è specifico per il PIN per le applicazioni iOS abilitate per la gestione delle app mobili di Intune. Nel corso del tempo, man mano che le applicazioni adottano versioni successive di Intune SDK per iOS, la necessità di impostare un PIN due volte per le app dallo stesso editore diventa un problema minore. Vedere la nota di seguito per un esempio.

  >[!NOTE]
  > Ad esempio, se l'app A è compilata con una versione precedente alla 7.1.12 e l'app B viene compilata con una versione maggiore o uguale a 7.1.12 dallo stesso editore, l'utente finale dovrà configurare separatamente i PIN per A e B, se entrambe le app vengono installate in un dispositivo iOS.
  > Se viene installata nel dispositivo un'app C con la versione 7.1.9 dell'SDK, questa app condividerà lo stesso PIN dell'app A. Un'app D compilata con la versione 7.1.14 condividerà lo stesso PIN dell'app B.  
  > Se in un dispositivo vengono installate solo le app A e C, sarà necessario impostare un solo PIN. Lo stesso vale se in un dispositivo vengono installate solo le app B e D.

### <a name="app-data-encryption"></a>Crittografia dati dell'app
Gli amministratori IT possono distribuire criteri di protezione che richiedono di crittografare i dati dell'app. Nell'ambito dei criteri, l'amministratore IT può specificare anche il momento in cui il contenuto viene crittografato.

**Funzionamento del processo di crittografia dei dati di Intune**<br> Per informazioni dettagliate sulle impostazioni di crittografia dei criteri di protezione delle app, vedere [Impostazioni dei criteri di protezione delle app per Android](app-protection-policy-settings-android.md) e [Impostazioni dei criteri di protezione delle app iOS](app-protection-policy-settings-ios.md).

**Dati crittografati**<br>
Vengono crittografati solo i dati contrassegnati come "aziendali" in base ai criteri di protezione delle app dell'amministratore IT. Quando hanno origine da una sede aziendale, i dati vengono considerati "aziendali". Per le app Office, Intune considera quanto segue come sedi aziendali:

- Posta elettronica (Exchange) 
- Archiviazione nel cloud (app OneDrive con un account OneDrive for Business)

Per le app line-of-business gestite dallo [strumento di wrapping delle app di Intune](../developer/apps-prepare-mobile-application-management.md), tutti i dati delle app vengono considerati "aziendali".

**Cancellazione remota dei dati**<br>

Intune può cancellare i dati dell'app in tre modi diversi: 
- Cancellazione completa nel dispositivo
- Cancellazione selettiva per MDM 
- Cancellazione selettiva per MAM

Per altre informazioni sulla cancellazione remota per MDM, vedere [Rimuovere i dispositivi tramite il ripristino delle impostazioni predefinite, la rimozione dei dati aziendali o l'annullamento manuale della registrazione del dispositivo](../remote-actions/devices-wipe.md). Per altre informazioni sulla cancellazione selettiva usando MAM, vedere [l'azione Ritira](../remote-actions/devices-wipe.md#retire) e [Come cancellare solo i dati aziendali dalle app](apps-selective-wipe.md).

La [cancellazione](../remote-actions/devices-wipe.md) rimuove tutti i dati dell'utente e le impostazioni dal **dispositivo** ripristinando le impostazioni predefinite di fabbrica. Il dispositivo verrà rimosso da Intune.

  >[!NOTE]
  > La cancellazione può essere eseguita solo sui dispositivi registrati con la gestione di dispositivi mobili (MDM) di Intune.

**Cancellazione selettiva per MDM**<br>
Vedere [l'azione Ritira nella sezione Rimuovere i dispositivi](../remote-actions/devices-wipe.md#retire) per informazioni sulla rimozione dei dati aziendali.

**Cancellazione selettiva per MAM**<br>
La cancellazione selettiva per MAM rimuove semplicemente i dati aziendali da un'app. La richiesta viene avviata tramite Intune nel portale di Azure. Per informazioni su come avviare una richiesta di cancellazione, vedere [Come cancellare solo i dati aziendali dalle app](apps-selective-wipe.md).

Se l'utente sta usando l'app quando viene avviata la cancellazione selettiva, [Intune App SDK](../developer/app-sdk.md) controlla ogni 30 minuti la presenza di una richiesta di cancellazione selettiva dal servizio MAM di Intune. L'SDK verifica inoltre la presenza della cancellazione selettiva quando l'utente avvia l'app per la prima volta e accede con l'account aziendale o dell'istituto di istruzione.

**Quando i servizi locali non funzionano con le app protette di Intune**<br>
La protezione delle app di Intune dipende dalla coerenza dell'identità dell'utente tra l'applicazione e [Intune App SDK](../developer/app-sdk.md). L'unico modo per garantire questo scenario è tramite l'autenticazione moderna. Esistono scenari in cui le app possono funzionare con una configurazione locale, ma non sono garantiti, né coerenti.

**Modo sicuro per aprire i collegamenti Web da app gestite**<br>
L'amministratore IT può distribuire e impostare i criteri di protezione delle app per l'[app Intune Managed Browser](app-configuration-managed-browser.md), un Web browser sviluppato da Microsoft Intune che è possibile gestire facilmente con Intune. L'amministratore IT può richiedere che tutti i collegamenti Web nelle app gestite da Intune vengano aperti tramite l'app Managed Browser.

## <a name="examples-of-app-protection-policies"></a>Esempi di criteri di protezione delle app

Per altre informazioni su esempi di criteri di protezione delle app e dettagli sulle singole impostazioni dei criteri di protezione delle app, vedere [Impostazioni dei criteri di protezione delle app per Android](app-protection-policy-settings-android.md) e [Impostazioni dei criteri di protezione delle app per iOS](app-protection-policy-settings-ios.md).

## <a name="app-protection-experience-for-ios-devices"></a>Esperienza di protezione delle app per dispositivi iOS

### <a name="device-fingerprint-or-face-ids"></a>Impronta digitale del dispositivo o Face ID 
I criteri di Protezione app di Intune consentono l'accesso alle app solo all'utente dotato di licenza per Intune. Uno dei modi per controllare l'accesso alle app consiste nel richiedere Apple Touch ID o Face ID per i dispositivi supportati. Intune implementa un comportamento in base al quale, se viene apportata una modifica al database di biometria del dispositivo e viene raggiunto il valore del timeout di inattività successivo, viene richiesto un PIN. Esempi di modifiche ai dati biometrici sono l'aggiunta o la rimozione di un'impronta digitale o di un viso. Se in Intune non è impostato un PIN, l'utente viene indirizzato alla configurazione di un PIN di Intune.
 
La finalità di questa procedura è di continuare a assicurare la protezione e la sicurezza a livello di app dei dati dell'organizzazione all'interno dell'app stessa. Questa funzionalità è disponibile solo per iOS e richiede la partecipazione delle applicazioni che integrano Intune APP SDK per iOS, versione 9.0.1 o successive. L'integrazione dell'SDK è necessaria in modo che il comportamento possa essere applicato nelle applicazioni di destinazione. Questa integrazione avviene sistematicamente e dipende dai team delle applicazioni specifiche. Tra le app partecipanti sono inclusi WXP, Outlook, Managed Browser e Yammer.
  
### <a name="ios-share-extension"></a>Estensione di condivisione iOS
È possibile usare l'estensione di condivisione iOS per aprire i dati aziendali o dell'istituto di istruzione nelle app non gestite, anche con i criteri di trasferimento dei dati impostati su **solo app gestite** o **Nessuna app**. I criteri di protezione delle app di Intune non possono controllare l'estensione di condivisione di iOS senza la gestione del dispositivo. Pertanto, Intune _**crittografa i dati "aziendali" prima che vengano condivisi all'esterno dell'app**_ . È possibile convalidare il comportamento di crittografia provando ad aprire il file "aziendale" all'esterno dell'app gestita. Il file deve essere crittografato e non deve poter essere aperto all'esterno dell'app gestita.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Più impostazioni di accesso della protezione delle app di Intune per lo stesso set di app e utenti
I criteri di protezione delle app di Intune relativi all'accesso vengono applicati in un ordine specifico nei dispositivi degli utenti finali quando cercano di accedere a un'app di destinazione dall'account aziendale. In generale, una cancellazione ha la precedenza, seguita da un avviso che può essere ignorato. Ad esempio, se possibile per l'app o l'utente specifici, un'impostazione di versione minima del sistema operativo iOS che avvisa l'utente che può essere eseguito un aggiornamento della versione di iOS verrà applicata dopo l'impostazione di versione minima del sistema operativo iOS che impedisce all'utente di accedere. Quindi, nello scenario in cui l'amministratore IT configura la versione minima del sistema operativo iOS su 11.0.0.0 e la versione minima del sistema operativo iOS (solo avvisi) su 11.1.0.0, se il dispositivo che tenta di accedere all'app usa iOS 10, l'utente finale verrebbe bloccato in base all'impostazione più restrittiva per la versione minima del sistema operativo iOS che comporta il blocco dell'accesso.

Quando si usano tipi diversi di impostazioni, un requisito di versione di Intune App SDK ha la precedenza, seguito dal requisito di versione dell'app e dal requisito relativo alla versione del sistema operativo iOS. Quindi, vengono controllati tutti gli avvisi per tutti i tipi di impostazioni nello stesso ordine. Si consiglia di configurare il requisito di versione di Intune App SDK solo attenendosi alle istruzioni del team del prodotto Intune per gli scenari di blocco essenziali.

## <a name="app-protection-experience-for-android-devices"></a>Esperienza di protezione delle app per dispositivi Android

### <a name="company-portal-app-and-intune-app-protection"></a>App Portale aziendale e protezione delle app di Intune
Gran parte delle funzionalità di protezione dell'app viene compilata nell'app Portale aziendale. La registrazione dei dispositivi _non è necessaria_ anche se l'app Portale aziendale è sempre obbligatoria. Per la gestione delle app per dispositivi mobili senza registrazione, è sufficiente che l'utente finale installi l'app Portale aziendale nel dispositivo.

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>Più impostazioni di accesso della protezione delle app di Intune per lo stesso set di app e utenti
I criteri di protezione delle app di Intune relativi all'accesso vengono applicati in un ordine specifico nei dispositivi degli utenti finali quando cercano di accedere a un'app di destinazione dall'account aziendale. In generale, un blocco ha la precedenza, seguito da un avviso che può essere ignorato. Ad esempio, se possibile per l'app o l'utente specifici, un'impostazione di versione minima della patch di Android che avvisa l'utente che può essere eseguito un upgrade della patch verrà applicata dopo l'impostazione di versione minima della patch di Android che impedisce all'utente di accedere. Quindi, nello scenario in cui l'amministratore IT configura la versione minima della patch di Android su 2018-03-01 e la versione minima della patch di Android (solo avvisi) su 2018-02-01, se il dispositivo che tenta di accedere all'app usa la versione 2018-01-01 della patch, l'utente finale verrebbe bloccato in base all'impostazione più restrittiva per la versione minima della patch di Android che comporta il blocco dell'accesso. 

Quando si usano tipi diversi di impostazioni, un requisito di versione app ha la precedenza, seguito dal requisito di versione del sistema operativo Android e dal requisito relativo alla versione della patch di Android. Quindi, vengono controllati tutti gli avvisi per tutti i tipi di impostazioni nello stesso ordine.

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>Criteri di protezione delle app di Intune e attestazione SafetyNet di Google per dispositivi Android 
I criteri di protezione delle app di Intune consentono agli amministratori di richiedere che i dispositivi degli utenti finali ottengano l'attestazione SafetyNet di Google per dispositivi Android. Una nuova determinazione del servizio Google Play verrà segnalata all'amministratore IT a un intervallo definito dal servizio Intune. La frequenza con cui viene effettuata la chiamata del servizio è limitata a causa del carico e di conseguenza questo valore viene gestito internamente e non può essere configurato. Qualsiasi azione configurata dall'amministratore IT per l'impostazione dell'attestazione SafetyNet di Google viene adottata in base all'ultimo risultato segnalato al servizio Intune al momento dell'avvio condizionale. Se non sono presenti dati, l'accesso verrà consentito se nessun altro controllo dell'avvio condizionale non riesce e viene avviato nel back-end un "round trip" di Google Play Service per determinare i risultati di attestazione, indicando all'utente in modo sincrono se il dispositivo non ha superato il controllo. In caso di dati non aggiornati, l'accesso verrà bloccato o consentito a seconda dell'ultimo risultato segnalato e, analogamente, verrà avviato un "round trip" di Google Play Service per determinare i risultati di attestazione, indicando all'utente in modo asincrono se il dispositivo non ha superato il controllo.

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>Criteri di protezione delle app di Intune e API di verifica delle app di Google per dispositivi Android
I criteri di protezione delle app di Intune consentono agli amministratori di richiedere che i dispositivi degli utenti finali inviino segnali tramite l'API di verifica delle app di Google per dispositivi Android. Le istruzioni su come eseguire questa operazione variano leggermente a seconda del dispositivo. Il processo generale consiste nel passare a Google Play Store, fare clic su **Le mie app e i miei giochi** e quindi fare clic sul risultato dell'ultima analisi delle app, che permette di accedere al menu Play Protect. Verificare che l'interruttore per **Cerca minacce alla sicurezza** sia attivato.

### <a name="googles-safetynet-attestation-api"></a>API di attestazione SafetyNet di Google 
Intune sfrutta le API SafetyNet di Google Play Protect per potenziare i controlli di rilevamento dei dispositivi rooted esistenti per i dispositivi non registrati. Google ha sviluppato e gestito questo set di API per app per Android da adottare se non si vuole che le app vengano eseguite su dispositivi rooted. L'app Android Pay, ad esempio, ha integrato questa funzionalità. Mentre Google non condivide pubblicamente l'interezza dei controlli di rilevamento dei dispositivi rooted eseguiti, queste API dovrebbero rilevare gli utenti che hanno eseguito accesso root ai propri dispositivi. Sarà quindi possibile impedire a questi utenti di accedere oppure cancellarne gli account aziendali dalle app con i criteri abilitati. L'opzione **Verifica l'integrità di base** dà informazioni sull'integrità generale del dispositivo. Dispositivi rooted, emulatori, dispositivi virtuali e dispositivi con segni di manomissione non superano la verifica dell'integrità di base. L'opzione **Verifica l'integrità di base e i dispositivi certificati** dà informazioni sulla compatibilità del dispositivo con i servizi di Google. Solo i dispositivi non modificati che hanno ottenuto la certificazione di Google possono superare questo controllo. I dispositivi che non superano il controllo includono i seguenti:

- Dispositivi che non soddisfano l'integrità di base
- Dispositivi con bootloader sbloccato
- Dispositivi con ROM/immagine del sistema personalizzata
- Dispositivi per cui il produttore non ha richiesto o non ha soddisfatto la certificazione Google
- Dispositivi con un'immagine del sistema creata direttamente da file del codice sorgente Android Open Source Program
- Dispositivi con un'immagine del sistema beta/di anteprima per sviluppatori

Per informazioni tecniche, vedere la [documentazione di Google sull'attestazione SafetyNet](https://developer.android.com/training/safetynet/attestation).

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>Impostazione Attestazione del dispositivo SafetyNet o impostazione "Dispositivi jailbroken/rooted"
I controlli delle API SafetyNet di Google Play Protect richiedono che l'utente finale sia online, almeno per l'intera durata dell'esecuzione del "round trip" per determinare i risultati di attestazione. Se l'utente finale è offline, l'amministratore IT può comunque aspettarsi l'applicazione di un risultato dall'impostazione **Dispositivi jailbroken/rooted**. In ogni caso, se l'utente finale è rimasto offline per troppo tempo, entra in gioco il valore **Periodo di prova offline** e l'intero accesso ai dati aziendali o dell'istituto di istruzione viene bloccato una volta raggiunto il valore del timer, finché non è disponibile accesso di rete. L'attivazione di entrambe le impostazioni consente un approccio a più livelli per mantenere integri i dispositivi degli utenti finali, un aspetto importante quando questi accedono a dati aziendali o dell'istituto di istruzione su un dispositivo mobile.

### <a name="google-play-protect-apis-and-google-play-services"></a>API di Google Play Protect e Google Play Services
Le impostazioni dei criteri di protezione delle app che sfruttano le API di Google Play Protect richiedono il funzionamento di Google Play Services. Le impostazioni **Attestazione del dispositivo SafetyNet** e **Analisi delle minacce nelle app** richiedono entrambe una versione determinata da Google di Google Play Services per funzionare correttamente. Poiché si tratta di impostazioni che rientrano nell'ambito della sicurezza, l'utente finale verrà bloccato se sono state assegnate queste impostazioni e l'utente non soddisfa i requisiti per la versione appropriata di Google Play Services o non ha accesso a Google Play Services.

## <a name="next-steps"></a>Passaggi successivi

[Come creare e distribuire i criteri di protezione delle app con Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Vedere anche
Le app di terze parti, ad esempio l'app per dispositivi mobili Salesforce, interagiscono con Intune in modi specifici per proteggere i dati aziendali. Per altre informazioni sul funzionamento dell'app Salesforce con Intune (incluse le impostazioni di configurazione delle app MDM), vedere [Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) (App Salesforce e Microsoft Intune).
