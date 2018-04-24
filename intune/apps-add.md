---
title: Come aggiungere app in Microsoft Intune
titlesuffix: ''
description: Informazioni su come aggiungere app in Microsoft Intune, in modo da poterle assegnare a utenti e dispositivi. Intune supporta un'ampia gamma di tipi diversi di app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b4e87c36c3aa0aaeae1e1bf265902100612db15
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>Come aggiungere un'app a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Microsoft Intune.

Gli utenti di app e dispositivi nell'azienda (dipendenti della società) potrebbero avere vari requisiti per le app. Prima di aggiungere le app a Intune e renderle disponibili per i dipendenti, è necessario valutare e comprendere alcuni concetti fondamentali per le app. È necessario conoscere i diversi tipi di app disponibili per Intune. È necessario valutare i requisiti delle app, ad esempio le piattaforme necessarie e le funzionalità richieste per i dipendenti. Inoltre, è necessario stabilire se verrà usato Intune per gestire i dispositivi (incluse le app) oppure se gestire le app con Intune senza gestire i dispositivi. È necessario determinare quali dipendenti hanno la necessità di app e funzionalità diverse. Le informazioni fornite in questo articolo sono utili per iniziare.

## <a name="app-types-in-microsoft-intune"></a>Tipi di app in Microsoft Intune

Intune supporta un'ampia gamma di tipi diversi di app. Le opzioni disponibili variano per ogni tipo di app. Intune consente di aggiungere e assegnare i tipi di app seguenti:

| **Tipi di app**                                     | **Installazione**                                                                  | **Aggiornamenti**                       |
|------------------------------------------ |----------------------------------------------------------------------------   |---------------------------    |
| App dallo store (app Store)          | Intune installa l'app nel dispositivo                                       | Gli aggiornamenti dell'app sono automatici     |
| App sviluppate internamente (line-of-business)  | Intune installa l'app nel dispositivo (è necessario fornire il file di installazione)    | È necessario aggiornare l'app       |
| App incluse (app predefinite)    | Intune installa l'app nel dispositivo                                       | Gli aggiornamenti dell'app sono automatici     |
| App sul Web (collegamento Web)                | Intune crea un collegamento all'app Web nella schermata iniziale del dispositivo          | Gli aggiornamenti dell'app sono automatici     |

### <a name="specific-app-type-details"></a>Dettagli sui tipi di app specifici
 
Nella tabella seguente sono elencati i tipi di app specifici e come è possibile aggiungerli dal pannello **Aggiungi app** in Microsoft Intune:

| **Tipo specifico di app**                         | **Tipo generale**             | **Procedure specifiche per l'app**                                                                                                                                                 |
|---------------------------------------------|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| App di Android Store                        | App Store                  | Selezionare **Android** come **tipo di app** e immettere l'URL di Google Play Store per l'app.                                                                                       |
| App di iOS Store                            | App Store                  | Selezionare **iOS** come **tipo di app**, cercare l'app e selezionare l'app in Intune.                                                                                     |
| App di Windows Phone 8.1 Store              | App Store                  | Selezionare **Windows Phone 8.1** come **tipo di app** e immettere l'URL di Microsoft Store per l'app.                                                                               |
| App di Microsoft Store                      | App Store                  | Selezionare **Windows** come **tipo di app** e immettere l'URL di Microsoft Store per l'app.                                                                                         |
| App Android for Work                     | App Store                  | Trovare e approvare l'app Android for Work dallo store Google Play for Work.                                                                                        |
| App di Office 365 per Windows 10            | App Store (Office 365)     | Selezionare **Windows 10** in **Famiglia di prodotti Office 365** come **tipo di app** e quindi selezionare l'app di Office 365 che si vuole installare.                                                |
| App di Office 365 per macOS                 | App Store (Office 365)     | Selezionare **macOS** in **Famiglia di prodotti Office 365** come **tipo di app** e quindi selezionare la suite di app di Office 365.                                                                     |
| App line-of-business Android       | App line-of-business | Selezionare **App line-of-business** come **tipo di app**, selezionare il **File del pacchetto dell'app** e quindi immettere un file di installazione Android con l'estensione **apk**.                    |
| App line-of-business iOS           | App line-of-business | Selezionare **App line-of-business** come **tipo di app**, selezionare il **File del pacchetto dell'app** e quindi immettere un file di installazione iOS con l'estensione **ipa**.                        |
| App line-of-business di Windows Phone | App line-of-business | Selezionare **App line-of-business** come **tipo di app**, selezionare il **File del pacchetto dell'app** e quindi immettere un file di installazione iOS con l'estensione **xap**.                        |
| App line-of-business Windows       | App line-of-business | Selezionare App line-of-business come tipo di app, selezionare il File del pacchetto dell'app e quindi immettere un file di installazione iOS con l'estensione **msi**, **appx** o **appxbundle**. |
| App iOS predefinita                          | App predefinita               | Selezionare **App predefinita** come **tipo di app** e quindi selezionare l'app predefinita nell'elenco delle app fornite.                                                                  |
| App Android predefinita                      | App predefinita               | Selezionare **App predefinita** come **tipo di app** e quindi selezionare l'app predefinita nell'elenco delle app fornite.                                                                  |
| App Web                                  | App Web                    | Selezionare **Collegamento Web** come **tipo di app** e immettere un URL valido che punta all'app Web.                                                                                        |

   
È possibile aggiungere un'app in Microsoft Intune selezionando **App per dispositivi mobili** > **App** > **Aggiungi**. Verrà visualizzato il pannello **Aggiungi app** che consente di selezionare il **tipo di app**. 

>[!TIP]
> Un'app line-of-business è un'app che viene aggiunta da un apposito file di installazione. Per installare un'app line-of-business iOS, ad esempio, aggiungere l'applicazione scegliendo **App line-of-business** come **Tipo di app** nel pannello **Aggiungi app**. Selezionare quindi il file del pacchetto dell'app (con estensione ipa). Questi tipi di app vengono in genere sviluppati internamente.

## <a name="assess-app-requirements"></a>Valutare i requisiti delle app
Il compito dell'amministratore IT non è soltanto quello di individuare le app che il gruppo deve usare, ma anche quello di determinare le funzionalità necessarie per ogni gruppo e sottogruppo. Per ogni app occorre determinare le piattaforme necessarie, i gruppi di utenti che necessitano dell'app, i criteri di configurazione per questi gruppi e i criteri di protezione da applicare.  

Occorre inoltre determinare se è necessario concentrarsi sulla gestione di dispositivi mobili (MDM, Mobile Device Management) o solo sulla gestione di applicazioni mobili (MAM, Mobile Application Management). L'uso di Intune per gestire i dispositivi (MDM) è utile quando:
- Gli utenti necessitano di un profilo di connettività aziendale Wi-Fi o VPN per essere produttivi.
- È necessario effettuare il push di un set di app nei dispositivi degli utenti.
- L'organizzazione deve essere conforme a normative o ad altri criteri che prescrivono controlli MDM specifici, ad esempio la sicurezza o la crittografia.

L'uso di Intune per gestire le app (MAM) senza gestire il dispositivo è utile quando:
- Si vuole consentire agli utenti di usare il proprio dispositivo (BYOD, Bring Your Own Device).
- Si vuole offrire un unico popup per informare gli utenti della presenza delle protezioni MAM, anziché continue notifiche a livello di dispositivo.
- Si vuole essere conformi a criteri che richiedono minori funzionalità di gestione nei dispositivi personali. Ad esempio, si desidera gestire i dati aziendali per le app, anziché gestirli per l'intero dispositivo.

Per altre informazioni, vedere [MDM e MAM a confronto](byod-technology-decisions.md).

### <a name="determine-who-will-use-the-app"></a>Determinare chi userà l'app

Quando si determinano le app necessarie per i dipendenti, prendere in considerazione i diversi gruppi di utenti che usano app differenti. La conoscenza di questi gruppi è utile anche dopo aver aggiunto un'app. Dopo avere aggiunto un'app, assegnare un gruppo di utenti autorizzati a usare l'app. Determinare prima di tutto il gruppo appropriato che deve avere accesso all'app in base alla riservatezza dei dati contenuti nell'app. Potrebbe essere necessario includere o escludere alcuni tipi di ruoli all'interno dell'organizzazione. Il gruppo vendite potrebbe ad esempio avere bisogno solo di alcune app line-of-business, mentre i dipendenti dei reparti progettazione, amministrazione, risorse umane o legale potrebbero non avere la necessità di usare le app line-of-business. Per il gruppo vendite potrebbero inoltre essere necessari una protezione dei dati aggiuntiva e l'accesso ai servizi aziendali interni nei dispositivi mobili. È necessario determinare la modalità di connessione di questo gruppo alle risorse tramite l'app. L'app accederà a dati in tempo reale nel cloud oppure a dati locali? E in che modo gli utenti si connetteranno alle risorse usando l'app? Intune supporta anche l'abilitazione dell'accesso alle applicazioni per dispositivi mobili che richiedono l'accesso protetto ai dati locali, ad esempio i server app line-of-business. Questo tipo di accesso viene in genere eseguito usando [certificati gestiti da Intune](certificates-configure.md) per il controllo di accesso, combinati con un gateway VPN standard o un proxy nel perimetro, ad esempio il proxy di applicazione di Microsoft Azure Active Directory. In Intune sono disponibili lo [strumento di wrapping delle app e App SDK](apps-prepare-mobile-application-management.md) che consentono di contenere i dati a cui si accede all'interno dell'app line-of-business, in modo che non sia possibile passare i dati aziendali alle app o ai servizi consumer.

Usare la [Guida alla pianificazione, progettazione e implementazione della distribuzione di Intune](planning-guide.md) per stabilire come identificare i gruppi dell'organizzazione associati a ogni scenario di caso d'uso e di caso d'uso secondario per l'app. Per informazioni dettagliate sull'assegnazione delle app ai gruppi, vedere [Come assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

### <a name="determine-the-type-of-app-for-your-solution"></a>Determinare il tipo di app per la soluzione

È possibile scegliere tra i tipi di app seguenti:
- **App dello Store**: un'app dello Store è un'app che è stata caricata in Microsoft Store, iOS Store o Android Store. Il provider dell'app dello Store gestisce l'app e ne fornisce gli aggiornamenti. Selezionare l'app nell'elenco dello Store e aggiungerla come app disponibile per gli utenti usando Intune.
- **App sviluppate internamente (line-of-business)**: le app create internamente sono app line-of-business. La funzionalità di questo tipo di app è stata creata per una delle piattaforme supportate da Intune, ad esempio Windows, iOS o Android. L'organizzazione crea e fornisce gli aggiornamenti come file separato. Gli aggiornamenti dell'app vengono forniti agli utenti aggiungendoli e distribuendoli tramite Intune.
- **App sul Web**: un'app Web è un'applicazione client-server. Il server fornisce l'app Web che include interfaccia utente, contenuto e funzionalità. Le moderne piattaforme di hosting Web in genere offrono inoltre sicurezza, bilanciamento del carico e altri vantaggi. Questo tipo di app viene gestito separatamente sul Web. Usare Intune per puntare a questo tipo di app. Assegnare anche i gruppi di utenti autorizzati ad accedere all'app. Si noti che Android non supporta le app Web.

Al momento di determinare le app necessarie per l'organizzazione, valutare le modalità di integrazione con i servizi cloud, i dati a cui accedono, la disponibilità o meno per gli utenti BYOD e se richiedono o meno l'accesso a Internet.

Per altre informazioni su come determinare il tipo di app necessario per l'organizzazione, vedere **App** nella sezione **Requisiti per le funzionalità** di [Creare una progettazione](planning-guide-design.md#feature-requirements).

### <a name="understanding-app-management-and-protection-policies"></a>Informazioni sui criteri di gestione delle app e di protezione
Intune consente di modificare la funzionalità delle app distribuite per allinearle ai criteri aziendali di conformità e sicurezza. Questo controllo consente di determinare le modalità di protezione dei dati aziendali. Le app gestite da Intune vengono abilitate con un set avanzato di criteri di protezione per applicazioni mobili, ad esempio:

- Limitazioni delle funzioni di copia e incolla e salva con nome
- Configurazione dei collegamenti Web per l'apertura all'interno dell'app Intune Managed Browser
- Abilitazione dell'uso di identità multiple e dell'accesso condizionale a livello di app

Le app gestite da Intune possono anche abilitare la protezione dell'app senza richiedere la registrazione, consentendo così di scegliere di applicare i criteri di prevenzione della perdita dei dati senza gestire il dispositivo dell'utente. Nelle app line-of-business e per dispositivi mobili è inoltre possibile incorporare la gestione delle app per dispositivi mobili usando Intune App SDK e lo strumento di wrapping delle app. Per altre informazioni su questi strumenti, vedere [Panoramica di Intune App SDK](app-sdk.md).

### <a name="understanding-licensed-apps"></a>Informazioni sulle app con licenza
Oltre alle app Web, alle app dello Store e alle app line-of-business, è utile tenere presente anche la destinazione delle app acquisite tramite Volume Purchase Program e di quelle con licenza, ad esempio:     
- **Volume Purchase Program di Apple per le imprese (iOS e MacOS)**: l'App Store iOS consente di acquistare più licenze per un'app da usare in azienda. L'acquisto di più copie favorisce una gestione più efficiente delle app presenti in azienda. Per altre informazioni, vedere [Gestire le app iOS acquistate con Volume Purchase Program](vpp-apps-ios.md).
- **Android for Work (Android)**: l'assegnazione di app a dispositivi Android for Work avviene in modo diverso rispetto all'assegnazione di app a dispositivi Android standard. Tutte le app installate per Android for Work provengono da Google Play for Work. Accedere allo store, cercare le app desiderate e approvarle. L'app viene quindi visualizzata nel nodo App con licenza del portale di Azure. Da qui è possibile gestire l'assegnazione dell'app allo stesso modo in cui si assegnano le altre app.
- **Microsoft Store per le aziende (Windows 10)**: in Microsoft Store per le aziende è possibile trovare e acquistare app per l'organizzazione, singolarmente o a volume. Collegando lo Store a Microsoft Intune è possibile gestire dal portale di Azure le app acquistate con Volume Purchase Program. Per altre informazioni, vedere [Gestire le app di Microsoft Store per le aziende](windows-store-for-business.md).

## <a name="before-you-add-apps"></a>Prima di aggiungere le app
Tenere presente quanto segue prima di iniziare ad aggiungere e assegnare le app.

- Quando si aggiunge e si assegna un'app da uno Store, gli utenti finali devono avere un account in tale Store per poter installare l'app.
- Alcune app o elementi assegnati potrebbero dipendere da app iOS predefinite. Ad esempio, se si assegna un libro dallo Store iOS, è necessario che l'app iBooks sia disponibile nel dispositivo. Se l'app iBooks predefinita è stata rimossa, non è possibile usare Intune per ripristinarla.

## <a name="cloud-storage-space"></a>Spazio di archiviazione nel cloud
Tutte le app create con il tipo di installazione del programma di installazione software, ad esempio un'app line-of-business, vengono compresse e caricate nello spazio di archiviazione cloud di Intune. Una sottoscrizione di valutazione di Intune comprende 2 gigabyte (GB) di archiviazione nel cloud per l'archiviazione delle app gestite e degli aggiornamenti. Una sottoscrizione completa include 20 GB di spazio di archiviazione.

È possibile acquistare spazio di archiviazione aggiuntivo per Intune usando il metodo di acquisto originale. Se il pagamento è stato effettuato con fattura o carta di credito, visitare il [portale di gestione delle sottoscrizioni](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions). Negli altri casi, contattare il partner o l'assistente alle vendite di riferimento.

I requisiti dello spazio di archiviazione nel cloud sono i seguenti:

-   Tutti i file di installazione delle app devono trovarsi nella stessa cartella.
-   La dimensione massima dei file caricati è di 2 GB.

## <a name="how-to-create-and-edit-categories-for-apps"></a>Come creare e modificare le categorie di app

Le categorie di app consentono di ordinare le app in modo da consentire agli utenti di trovarle più facilmente nel portale aziendale. È possibile assegnare una o più categorie a un'app, ad esempio **App per sviluppatori** o **App di comunicazione**.
Quando si aggiunge un'app in Intune, è possibile selezionare la categoria desiderata. Usare gli argomenti specifici della piattaforma per aggiungere un'app e assegnare le categorie. Per creare e modificare le categorie, usare la procedura seguente:

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Categorie di app** nella sezione **Installazione**. 
5. Nel pannello **Categorie di app** viene visualizzato un elenco delle categorie correnti. Scegliere una delle azioni seguenti:
    - **Creare una categoria**: selezionare **Aggiungi** per visualizzare il pannello **Crea la categoria** e aggiungere un nome per la nuova categoria. I nomi possono essere immessi in una sola lingua e non vengono tradotti da Intune. Al termine, fare clic su **Crea**.
    - **Modificare una categoria**: per qualsiasi categoria nell'elenco, scegliere "**...**". Questa opzione visualizza un menu a comparsa in cui è possibile selezionare le voci **Aggiungi al dashboard** o **Elimina** per la categoria.

## <a name="apps-added-automatically-by-intune"></a>App aggiunte automaticamente da Intune

Intune conteneva in precedenza un numero di app predefinite che era possibile assegnare rapidamente. In base ai commenti e suggerimenti ricevuti, questo elenco è stato rimosso e le app predefinite non vengono più visualizzate.
Tuttavia, se sono già state assegnate app predefinite, queste saranno ancora visibili nell'elenco delle app. È possibile continuare ad assegnare queste app in base alle proprie esigenze.

## <a name="next-steps"></a>Passaggi successivi

Per informazioni su come aggiungere a Intune app per ciascuna piattaforma, scegliere uno degli argomenti seguenti:

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
