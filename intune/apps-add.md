---
title: Aggiungere app in Microsoft Intune
titlesuffix: ''
description: Informazioni su come aggiungere app in Microsoft Intune, in modo da poterle assegnare a utenti e dispositivi. Intune supporta un'ampia gamma di tipi di app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2db9d991c476d89399058137adb972c06029befc
ms.sourcegitcommit: 391755a4c8a38e3a22744516fd27d75e40438899
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/13/2018
ms.locfileid: "39028729"
---
# <a name="add-apps-to-microsoft-intune"></a>Aggiungere app in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Microsoft Intune.

Gli utenti di app e dispositivi nell'azienda (il personale della società) potrebbero avere vari requisiti per le app. Prima di aggiungere le app a Intune e renderle disponibili per i dipendenti, è necessario valutare e comprendere alcuni concetti fondamentali per le app. È fondamentale conoscere i diversi tipi di app disponibili per Intune. Occorre valutare i requisiti delle app, ad esempio le piattaforme e le funzionalità di cui il personale ha bisogno. È necessario stabilire se usare Intune per gestire i dispositivi (incluse le app) oppure se gestire le app con Intune senza gestire i dispositivi. Infine, occorre determinare quali sono le app e le funzionalità di cui il personale avrà bisogno e chi se ne dovrà servire. Le informazioni contenute in questo articolo sono utili per iniziare.

## <a name="app-types-in-microsoft-intune"></a>Tipi di app in Microsoft Intune

Intune supporta un'ampia gamma di tipi di app. Le opzioni disponibili variano per ogni tipo di app. Intune consente di aggiungere e assegnare i tipi di app seguenti:

| Tipi di app | Installazione | Aggiornamenti |
|---|---|---|
| App dallo store (app Store) | Intune installa l'app nel dispositivo.  | Gli aggiornamenti dell'app sono automatici.   |
| App sviluppate internamente (line-of-business)  | Intune installa l'app nel dispositivo (il file di installazione viene fornito dall'utente).     | È necessario aggiornare l'app.  |
| App incluse (app predefinite)    | Intune installa l'app nel dispositivo.  | Gli aggiornamenti dell'app sono automatici.  |
| App sul Web (collegamento Web) | Intune crea un collegamento all'app Web nella schermata iniziale del dispositivo.  | Gli aggiornamenti dell'app sono automatici.    |

### <a name="specific-app-type-details"></a>Dettagli sui tipi di app specifici
 
La tabella seguente elenca i tipi di app specifici e descrive come aggiungerli nel riquadro **Aggiungi app** di Intune:

| **Tipo specifico di app** | **Tipo generale** | **Procedure specifiche per l'app** |
| --- | --- | --- |
| App di Android Store  | App Store  | Selezionare **Android** come **tipo di app** e immettere l'URL di Google Play Store per l'app. |
| App di iOS Store  | App Store  | Selezionare **iOS** come **tipo di app**, cercare l'app e selezionarla in Intune. |
| App di Windows Phone 8.1 Store  | App Store  | Selezionare **Windows Phone 8.1** come **tipo di app** e immettere l'URL di Microsoft Store per l'app. |
| App di Microsoft Store  | App Store  | Selezionare **Windows** come **tipo di app** e immettere l'URL di Microsoft Store per l'app. |
| App del profilo di lavoro Android | App Store  | Trovare e approvare l'app del profilo di lavoro Android dalla versione gestita di Google Play Store.  |
| App di Office 365 per Windows 10  | App Store (Office 365) | Selezionare **Windows 10** in **Famiglia di prodotti Office 365** come **tipo di app** e quindi selezionare l'app di Office 365 che si vuole installare.  |
| App di Office 365 per macOS | App Store (Office 365) | Selezionare **macOS** in **Famiglia di prodotti Office 365** come **tipo di app** e quindi selezionare la famiglia di app di Office 365. |
| App line-of-business Android | App line-of-business | Selezionare **App line-of-business** come **tipo di app**, selezionare il **file del pacchetto dell'app** e quindi immettere un file di installazione Android con estensione **apk**.  |
| App line-of-business iOS | App line-of-business | Selezionare **App line-of-business** come **tipo di app**, selezionare il **file del pacchetto dell'app** e quindi immettere un file di installazione iOS con estensione **ipa**.  |
| Applicazioni line-of-business di Windows Phone | App line-of-business | Selezionare **App line-of-business** come **tipo di app**, selezionare il **file del pacchetto dell'app** e quindi immettere un file di installazione Windows Phone con estensione **xap**.  |
| App line-of-business di Windows | App line-of-business | Selezionare **App line-of-business** come tipo di app, selezionare il **file del pacchetto dell'app** e quindi immettere un file di installazione Windows con estensione **msi**, **appx** o **appxbundle**. |
| App iOS predefinita  | App predefinita | Selezionare **App predefinita** come **tipo di app** e quindi selezionare l'app predefinita nell'elenco delle app fornite.  |
| App Android predefinita  | App predefinita | Selezionare **App predefinita** come **tipo di app** e quindi selezionare l'app predefinita nell'elenco delle app fornite.  |
| App Web  | App Web  | Selezionare **Collegamento Web** come **tipo di app** e quindi immettere un URL valido che punta all'app Web.  |

È possibile aggiungere un'app in Microsoft Intune selezionando **App per dispositivi mobili** > **App** > **Aggiungi**. Verrà visualizzato il riquadro **Aggiungi app** che consente di selezionare il **tipo di app**. 

>[!TIP]
> Un'app line-of-business è un'app che viene aggiunta da un apposito file di installazione. Per installare un'app line-of-business iOS, ad esempio, aggiungere l'applicazione selezionando **App line-of-business** come **tipo di app** nel riquadro **Aggiungi app**. Selezionare quindi il file del pacchetto dell'app (con estensione ipa). Questi tipi di app vengono in genere sviluppati internamente.

## <a name="assess-app-requirements"></a>Valutare i requisiti delle app
Il compito dell'amministratore IT non è soltanto quello di individuare le app che il gruppo deve usare, ma anche quello di determinare le funzionalità necessarie per ogni gruppo e sottogruppo. Per ogni app occorre determinare le piattaforme necessarie, i gruppi di utenti che necessitano dell'app, i criteri di configurazione per questi gruppi e i criteri di protezione da applicare.  

Occorre inoltre determinare se è necessario concentrarsi sulla gestione di dispositivi mobili (MDM, Mobile Device Management) o solo sulla gestione di applicazioni mobili (MAM, Mobile Application Management). 

L'uso di Intune per gestire i dispositivi con MDM è utile quando:
- Gli utenti necessitano di un profilo di connettività aziendale Wi-Fi o VPN per essere produttivi.
- È necessario effettuare il push di un set di app nei dispositivi degli utenti.
- L'organizzazione deve essere conforme a normative o ad altri criteri che prescrivono controlli MDM specifici, ad esempio la sicurezza o la crittografia.

L'uso di Intune per gestire le app con MAM senza gestire il dispositivo è utile quando:
- Si vuole consentire agli utenti di usare il proprio dispositivo (BYOD, Bring Your Own Device).
- Si vuole offrire un unico messaggio popup che informi gli utenti della presenza delle protezioni MAM, anziché continue notifiche a livello di dispositivo.
- Si vuole essere conformi a criteri che richiedono una minore capacità di gestione nei dispositivi personali. Ad esempio, si desidera gestire i dati aziendali per le app, anziché gestirli per l'intero dispositivo.

Per altre informazioni, vedere [MDM e MAM a confronto](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Determinare chi userà l'app

Per determinare le app necessarie per il personale dell'azienda, è opportuno considerare i vari gruppi di utenti e le varie app che usano. La conoscenza di questi gruppi è utile anche dopo aver aggiunto un'app. Dopo avere aggiunto un'app, assegnare un gruppo di utenti autorizzati a usarla. 

Prima di tutto occorre determinare il gruppo che deve avere accesso all'app in base alla riservatezza dei dati contenuti nell'app. Potrebbe essere necessario includere o escludere alcuni tipi di ruoli all'interno dell'organizzazione. Il gruppo vendite potrebbe ad esempio avere bisogno solo di alcune app line-of-business, mentre i dipendenti dei reparti progettazione, amministrazione, risorse umane o legale potrebbero non avere la necessità di usare le app line-of-business. Per il gruppo vendite potrebbero inoltre essere necessari una protezione dei dati aggiuntiva e l'accesso ai servizi aziendali interni nei dispositivi mobili. È necessario determinare la modalità di connessione di questo gruppo alle risorse tramite l'app. L'app accederà a dati nel cloud oppure a dati locali? E in che modo gli utenti si connetteranno alle risorse usando l'app? 

Intune supporta anche l'abilitazione dell'accesso alle applicazioni per dispositivi mobili che richiedono l'accesso protetto ai dati locali, ad esempio i server app line-of-business. Questo tipo di accesso viene in genere fornito usando [certificati gestiti da Intune](certificates-configure.md) per il controllo di accesso, combinati con un gateway VPN standard o un proxy nel perimetro, ad esempio Azure Active Directory Application Proxy. In Intune sono disponibili lo [strumento di wrapping delle app e App SDK](apps-prepare-mobile-application-management.md) che consentono di contenere i dati a cui si accede all'interno dell'app line-of-business, in modo che non sia possibile passare i dati aziendali alle app o ai servizi consumer.

Usare la [Guida alla pianificazione, progettazione e implementazione della distribuzione di Intune](planning-guide.md) per stabilire come identificare i gruppi dell'organizzazione associati a ogni scenario di caso d'uso e di caso d'uso secondario per l'app. Per informazioni sull'assegnazione delle app ai gruppi, vedere [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

### <a name="determine-the-type-of-app-for-your-solution"></a>Determinare il tipo di app per la soluzione

È possibile scegliere uno dei tipi di app seguenti:
- **App dello Store**: sono app dello Store le app che sono state caricate in Microsoft Store, iOS Store o Android Store. Il provider di un app dello Store gestisce l'app e ne fornisce gli aggiornamenti. Selezionare l'app nell'elenco dello Store e aggiungerla come app disponibile per gli utenti usando Intune.
- **App sviluppate internamente (line-of-business)**: le app create internamente sono app line-of-business (LOB). La funzionalità di questo tipo di app è stata creata per una delle piattaforme supportate da Intune, ad esempio Windows, iOS o Android. L'organizzazione crea e fornisce gli aggiornamenti come file separato. Gli aggiornamenti dell'app vengono forniti agli utenti aggiungendoli e distribuendoli tramite Intune.
- **App sul Web**: le app Web sono applicazioni client-server. Il server fornisce l'app Web che include interfaccia utente, contenuto e funzionalità. Le moderne piattaforme di hosting Web in genere offrono inoltre sicurezza, bilanciamento del carico e altri vantaggi. Questo tipo di app viene gestito separatamente sul Web. Usare Intune per puntare a questo tipo di app. Assegnare anche i gruppi di utenti autorizzati ad accedere all'app. Si noti che Android non supporta le app Web.

Al momento di determinare le app necessarie per l'organizzazione, considerare il modo in cui si integrano con i servizi cloud, a quali dati accedono, se sono disponibili o meno per gli utenti BYOD e se richiedono o meno l'accesso a Internet.

Per altre informazioni sui tipi di app necessari per l'organizzazione, vedere "App" nella sezione "Requisiti per le funzionalità" di [Creare una progettazione](planning-guide-design.md#feature-requirements).

### <a name="understanding-app-management-and-protection-policies"></a>Informazioni sui criteri di gestione delle app e di protezione
Intune consente di modificare la funzionalità delle app distribuite per allinearle ai criteri aziendali di conformità e sicurezza. Questo controllo consente di determinare le modalità di protezione dei dati aziendali. Le app gestite da Intune vengono abilitate con un set avanzato di criteri di protezione per applicazioni mobili, ad esempio:

- Limitazioni delle funzioni di copia e incolla e salvataggio con nome.
- Configurazione dei collegamenti Web per l'apertura all'interno dell'app Intune Managed Browser.
- Abilitazione dell'uso di identità multiple e dell'accesso condizionale a livello di app.

Le app gestite da Intune possono anche abilitare la protezione dell'app senza richiedere la registrazione, consentendo così di scegliere di applicare i criteri di prevenzione della perdita dei dati senza gestire il dispositivo dell'utente. Nelle app line-of-business e per dispositivi mobili è inoltre possibile incorporare la gestione delle app per dispositivi mobili usando Intune App SDK e lo strumento di wrapping delle app. Per altre informazioni su questi strumenti, vedere [Panoramica di Intune App SDK](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Informazioni sulle app con licenza
Oltre a conoscere le app Web, le app dello Store e le app line-of-business, è utile conoscere anche la destinazione delle app acquisite tramite Volume Purchase Program e di quelle con licenza, ad esempio: 
- **Volume Purchase Program di Apple per le imprese (iOS e MacOS)**: l'App Store iOS consente di acquistare più licenze per un'app da usare in azienda. L'acquisto di più copie favorisce una gestione più efficiente delle app presenti in azienda. Per altre informazioni, vedere [Gestire le app iOS acquistate con Volume Purchase Program](vpp-apps-ios.md).
- **Profili di lavoro Android**: l'assegnazione di app a dispositivi con profili di lavoro Android avviene in modo diverso rispetto all'assegnazione di app a dispositivi Android standard. Tutte le app installate per i profili di lavoro Android provengono dalla versione gestita di Google Play Store. Accedere allo store, cercare le app desiderate e approvarle. L'app viene quindi visualizzata nel nodo **App con licenza** del portale di Azure ed è possibile gestire l'assegnazione dell'app allo stesso modo di qualsiasi altra app.
- **Microsoft Store per le aziende (Windows 10)**: in Microsoft Store per le aziende è possibile trovare e acquistare app per l'organizzazione, singolarmente o a volume. Collegando lo Store a Microsoft Intune è possibile gestire nel portale di Azure le app acquistate con Volume Purchase Program. Per altre informazioni, vedere [Gestire le app di Microsoft Store per le aziende](windows-store-for-business.md).

## <a name="before-you-add-apps"></a>Prima di aggiungere le app
Prima di iniziare ad aggiungere e assegnare le app, tenere presente quanto segue:

- Quando si aggiunge e si assegna un'app da uno Store, gli utenti devono avere un account in tale Store per poter installare l'app.
- Alcune app o elementi assegnati potrebbero dipendere da app iOS predefinite. Ad esempio, se si assegna un libro nell'App Store iOS, è necessario che l'app iBooks sia disponibile nel dispositivo. Se l'app iBooks predefinita è stata rimossa, non è possibile usare Intune per ripristinarla.

## <a name="cloud-storage-space"></a>Spazio di archiviazione nel cloud
Tutte le app create con il tipo di installazione del programma di installazione software, ad esempio un'app line-of-business, vengono compresse e caricate nello spazio di archiviazione cloud di Intune. Una sottoscrizione di valutazione di Intune comprende 2 gigabyte (GB) di archiviazione nel cloud per l'archiviazione delle app gestite e degli aggiornamenti. Una sottoscrizione completa non limita la quantità totale di spazio di archiviazione.

I requisiti dello spazio di archiviazione nel cloud sono i seguenti:

- Tutti i file di installazione delle app devono trovarsi nella stessa cartella.
- La dimensione massima dei file caricati è di 2 GB.

## <a name="create-and-edit-categories-for-apps"></a>Creare e modificare le categorie di app

Le categorie di app consentono di ordinare le app in modo da consentire agli utenti di trovarle più facilmente nel portale aziendale. È possibile assegnare una o più categorie a un'app, ad esempio *App per sviluppatori* o *App di comunicazione*.

Quando si aggiunge un'app in Intune, è possibile selezionare la categoria desiderata. Usare gli argomenti specifici della piattaforma per aggiungere un'app e assegnare le categorie. Per creare e modificare le categorie, usare la procedura seguente:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App per dispositivi mobili**.
4. Nel riquadro del carico di lavoro **App per dispositivi mobili**, in **Configurazione**, selezionare **Categorie di app**.  
    Il riquadro **Categorie di app** contiene un elenco delle categorie correnti. 
5. Effettuare una delle operazioni riportate di seguito:
    - Per aggiungere una categoria, nel riquadro **Crea la categoria** selezionare **Aggiungi** e quindi immettere un nome per la categoria.  
    I nomi possono essere immessi in una sola lingua e non vengono tradotti da Intune.
    - Per modificare una categoria, selezionare i puntini di sospensione (**...**) accanto alla categoria, quindi selezionare **Aggiungi al dashboard** o **Elimina**.
6. Selezionare **Crea**.

## <a name="apps-that-are-added-automatically-by-intune"></a>App aggiunte automaticamente da Intune

Intune conteneva in precedenza un numero di app predefinite che era possibile assegnare rapidamente. In seguito al feedback dei clienti di Intune, questo elenco è stato rimosso e le app predefinite non vengono più visualizzate. Tuttavia, se sono già state assegnate app predefinite, queste rimangono visibili nell'elenco delle app. È possibile continuare ad assegnare le app in base alle esigenze.

> [!NOTE]
> Per l'installazione di un'applicazione non line-of-business obbligatoria, Intune proverà a installare l'app mediante l'invio di un comando di installazione ogni volta che il dispositivo si connetterà, dato che l'app non viene rilevata e lo stato di installazione dell'app non è *Installazione in sospeso*.

## <a name="installing-updating-or-removing-required-apps"></a>Installazione, aggiornamento o rimozione di app necessarie

Intune reinstallerà, aggiornerà o rimuoverà automaticamente l'app necessaria entro 24 ore invece di attendere il ciclo di rivalutazione di 7 giorni.

Intune reinstallerà, aggiornerà o rimuoverà automaticamente l'app necessaria in base alle condizioni seguenti:
- Se un utente finale disinstalla un'app che deve essere installata nel suo dispositivo, Intune la reinstallerà automaticamente alla scadenza della pianificazione.
- Se l'installazione dell'app necessaria ha esito negativo o per qualsiasi altro motivo l'app non è presente nel dispositivo, Intune valuta la conformità e reinstalla l'app alla scadenza della pianificazione.  
- Un amministratore definisce un'app come disponibile per un gruppo di utenti e un utente finale installa l'app dal portale aziendale nel dispositivo. Dopo di ché l'amministratore aggiorna l'app dalla versione 1 alla versione 2. Intune aggiornerà l'app alla scadenza della pianificazione, a condizione che nel dispositivo sia ancora presente una qualsiasi altra versione precedente.
- Se l'amministratore distribuisce la finalità di distallazione, ma l'applicazione è presente nel dispositivo e non viene disinstallata, Intune valuta la conformità e disinstalla l'app alla scadenza della pianificazione.   

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su come aggiungere app per ogni piattaforma in Intune, vedere:

- [App di Android Store](store-apps-android.md)
- [App di Android LOB](lob-apps-android.md)
- [App di iOS Store](store-apps-ios.md)
- [App line-of-business iOS](lob-apps-ios.md)
- [App Web (per tutte le piattaforme)](web-app.md)
- [App di Windows Phone 8.1 Store](store-apps-windows-phone-8-1.md)
- [Applicazioni line-of-business di Windows Phone](lob-apps-windows-phone.md)
- [App di Microsoft Store](store-apps-windows.md)
- [App line-of-business di Windows](lob-apps-windows.md)
- [Applicazioni di Office 365 per Windows 10](apps-add-office365.md)
- [App di Office 365 per macOS](apps-add-office365-macos.md)
- [App predefinite](apps-add-built-in.md)
