---
title: Impostazioni delle funzionalità dei dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare tutte le impostazioni per configurare i dispositivi iOS per le impostazioni di AirPrint, layout della schermata iniziale, notifiche delle app, dispositivi condivisi, Single Sign-On e filtro del contenuto Web in Microsoft Intune. Usare queste impostazioni in un profilo di configurazione del dispositivo per configurare i dispositivi iOS per usare queste diverse funzionalità Apple nell'organizzazione.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2a94be7ebc369005f92809d57c8e55076972df3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799266"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>impostazioni del dispositivo iOS a usare le funzionalità comuni di iOS in Intune

Intune include alcune impostazioni predefinite per consentire agli utenti di iOS di usare diverse funzionalità di Apple nei dispositivi. Gli amministratori, ad esempio, possono controllare come gli utenti di iOS usano le stampanti AirPrint, aggiungere app e cartelle al dock e alle pagine nella schermata iniziale, visualizzare le notifiche delle app, visualizzare i dettagli dei tag degli asset nella schermata di blocco, usare l'autenticazione Single Sign-On e autenticare gli utenti con i certificati.

Usare queste funzionalità per controllare i dispositivi iOS come parte della soluzione mobile device management (MDM).

L'articolo elenca queste impostazioni e descrive la funzione di ogni impostazione.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo iOS](device-features-configure.md#create-a-device-profile).

## <a name="airprint-settings"></a>Impostazioni AirPrint

Questa funzionalità consente agli utenti di iOS di stampare su stampanti AirPrint note.

1. In **Impostazioni** selezionare **AirPrint**. Immettere le proprietà seguenti del server AirPrint:

    - **Indirizzo IP**: immettere l'indirizzo IPv4 o IPv6 della stampante. Se si usano i nomi host per identificare le stampanti, è possibile ottenere l'indirizzo IP effettuando il ping della stampante nel terminale. Per informazioni più dettagliate, vedere Ottenere l'indirizzo IP e il percorso (in questo articolo).
    - **Percorso**: il percorso è in genere `ipp/print` per le stampanti di rete. Per informazioni più dettagliate, vedere Ottenere l'indirizzo IP e il percorso (in questo articolo).
    - **Porta**: immettere la porta di ascolto della destinazione AirPrint. Se si omette questa proprietà, AirPrint usa la porta predefinita. Disponibile in iOS 11.0 e versioni successive.
    - **TLS**: scegliere **Abilita** per proteggere le connessioni AirPrint con Transport Layer Security (TLS). Disponibile in iOS 11.0 e versioni successive.

2. Selezionare **Aggiungi**. Il server AirPrint viene aggiunto all'elenco. È possibile aggiungere più server AirPrint.

    È anche possibile **importare** un file con valori delimitati da virgole (CSV) con queste informazioni. Dopo aver creato l'elenco, è anche possibile **esportare** l'elenco di server AirPrint.

3. Al termine, selezionare **OK** per salvare l'elenco.

Per aggiungere i server AirPrinter, sono necessari l'indirizzo IP della stampante, il percorso della risorsa e la porta. La procedura seguente mostra come ottenere queste informazioni.

1. In un dispositivo Mac connesso alla stessa rete locale (subnet) delle stampanti AirPrint aprire **Terminale** (da **/Applicazioni/Utilità**).
2. Nel terminale digitare `ippfind` e premere INVIO.

    Prendere nota delle informazioni della stampante. Ad esempio, potrebbe restituire un valore simile a `ipp://myprinter.local.:631/ipp/port1`. La prima parte è il nome della stampante. L'ultima parte (`ipp/port1`) è il percorso della risorsa.

3. Nel Terminale digitare `ping myprinter.local` e premere INVIO.

   Prendere nota dell'indirizzo IP. Ad esempio, potrebbe restituire un valore simile a `PING myprinter.local (10.50.25.21)`.

4. Usare i valori del percorso della risorsa e dell'indirizzo IP. In questo esempio l'indirizzo IP è `10.50.25.21` e il percorso della risorsa è `/ipp/port1`.

## <a name="home-screen-layout-settings"></a>Impostazioni di layout della schermata iniziale

Queste impostazioni configurano il layout delle app e le cartelle nel dock e nelle schermate iniziali dei dispositivi iOS. Per usare questa funzionalità, i dispositivi iOS devono essere in modalità di supervisione ed eseguire iOS 9.3 o versione successiva.

### <a name="dock"></a>Dock

Usare le impostazioni di **Dock** per aggiungere fino a sei elementi o cartelle al dock della schermata iOS. Molti dispositivi supportano un minor numero di elementi. I dispositivi iPhone, ad esempio, supportano al massimo quattro elementi. In questo caso, nel dispositivo verranno visualizzati solo i primi quattro elementi aggiunti.

1. In **Impostazioni** selezionare **Layout della schermata iniziale (solo con supervisione)** > **Dock** > **Aggiungi**. È possibile aggiungere fino a **sei** elementi (app e cartelle in combinazione) per il dock del dispositivo.
2. In **Tipo** scegliere se aggiungere un'**app** o una **cartella**.

    - **Aggiungi un'app**: scegliere questa opzione per aggiungere le app al dock nella schermata. Immettere

      - **Nome dell'app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
      - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](#bundle-ids-for-built-in-ios-apps) (in questo articolo).

      Selezionare **OK** per salvare le modifiche.

    - **Aggiungi una cartella**: scegliere questa opzione per aggiungere una cartella al dock nella schermata. 

      Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra e nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

      1. Specificare un **nome di cartella**. Questo nome viene visualizzato nel dispositivo degli utenti.
      2. Scegliere **Aggiungi** e immettere le proprietà seguenti:

          - **Nome della pagina**: immettere un nome per la pagina. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
          - **Nome dell'app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
          - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](#bundle-ids-for-built-in-ios-apps) (in questo articolo).

      3. Scegliere **Aggiungi**. È possibile aggiungere fino a **20** pagine per il dock del dispositivo.
      4. Selezionare **OK** per salvare le modifiche.

> [!NOTE]
> Quando si aggiungono icone utilizzando le impostazioni di ancoraggio, le icone nella schermata Home e di pagine sono bloccate e non possono essere spostate. È possibile per impostazione predefinita con iOS e i criteri MDM di Apple.

#### <a name="example"></a>Esempio

Nell'esempio seguente la schermata del dock mostra solo le app Safari, Mail e Borsa. L'app Mail viene selezionata per visualizzarne le proprietà:

![Impostazioni di esempio del dock iOS](./media/FfFiUcP.png)

Quando si assegnano i criteri a un iPhone, il dock è simile all'immagine seguente:

![Esempio di layout del dock su iPhone](./media/bAgCe8F.png)

### <a name="pages"></a>.NET

Aggiungere le pagine che verranno visualizzate nella schermata iniziale e le app che verranno visualizzate in ogni pagina. Le app aggiunte a una pagina vengono disposte da sinistra a destra, nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

> [!TIP]
> Per riordinare gli elementi di qualsiasi schermata iniziale e qualsiasi elenco di pagine, è possibile trascinarli e rilasciarli.

1. In **Impostazioni** selezionare **Layout della schermata iniziale (solo con supervisione)** > **Pagine** > **Aggiungi**. È possibile aggiungere fino a **40** pagine in un dispositivo.
2. Immettere un **nome di pagina**. Questo nome viene usato come riferimento nel portale di Azure e *non* viene visualizzato nel dispositivo iOS. 

    Selezionare **Aggiungi**. È possibile aggiungere fino a **60** elementi (app e cartelle in combinazione) in un dispositivo.

3. In **Tipo** scegliere se aggiungere un'**app** o una **cartella**.

    - **Aggiungi un'app**: scegliere questa opzione per aggiungere le app a una pagina nella schermata. Immettere

      - **Nome dell'app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
      - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](#bundle-ids-for-built-in-ios-apps) (in questo articolo).

      Selezionare **OK** per salvare le modifiche.

    - **Aggiungi una cartella**: scegliere questa opzione per aggiungere una cartella al dock nella schermata. 

      Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra e nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

      1. Specificare un **nome di cartella**. Questo nome viene visualizzato nel dispositivo degli utenti.
      2. Scegliere **Aggiungi** e immettere le proprietà seguenti:

          - **Nome della pagina**: immettere un nome per la pagina. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
          - **Nome dell'app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
          - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](#bundle-ids-for-built-in-ios-apps) (in questo articolo).

      3. Scegliere **Aggiungi**.
      4. Selezionare **OK** per salvare le modifiche.

#### <a name="example"></a>Esempio

Nell'esempio seguente viene aggiunta una nuova pagina denominata **Contoso**. La pagina visualizza le app Trova amici e Impostazioni. L'app Impostazioni viene selezionata per visualizzarne le proprietà:

![Esempio di impostazioni della schermata iniziale iOS](./media/Jc2OxyX.png)

Quando si assegnano i criteri a un iPhone, la pagina è simile all'immagine seguente:

![Dispositivo iOS con schermata iniziale modificata](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Impostazioni delle notifiche delle app

Scegliere la modalità in cui le app installate nei dispositivi iOS devono inviare notifiche. Queste impostazioni supportano dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

1. In **Impostazioni** selezionare **Notifiche app (solo con supervisione)** > **Aggiungi**:

    ![Aggiungere la notifica dell'app nel profilo iOS in Intune](./media/ios-macos-app-notifications.png)

2. Immettere le proprietà seguenti:

    - **ID bundle dell'app**: immettere l'**ID bundle dell'app** che si vuole aggiungere. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](#bundle-ids-for-built-in-ios-apps) (in questo articolo).
    - **Nome app**: immettere il nome dell'app che si vuole aggiungere. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo.
    - **Autore**: immettere l'autore dell'app da aggiungere. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo.
    - **Notifiche**: **abilitare** o **disabilitare** l'invio di notifiche al dispositivo da parte dell'app.
       - **Mostra nel centro notifiche**: **Abilita** consente all'app di visualizzare notifiche nel centro modifiche del dispositivo. **Disabilita** impedisce all'app di visualizzare notifiche nel centro notifiche.
       - **Mostra nella schermata di blocco**: selezionare **Abilita** per visualizzare le notifiche dall'app nella schermata di blocco del dispositivo. **Disabilita** impedisce all'app di visualizzare notifiche nella schermata di blocco.
       - **Tipo avviso**: quando il dispositivo è sbloccato, scegliere come visualizzare la notifica. Le opzioni disponibili sono:
         - **Nessuno**: non vengono visualizzate notifiche.
         - **Banner**: viene brevemente visualizzato un banner con la notifica.
         - **Modale**: la notifica viene visualizzata e l'utente deve chiuderla manualmente prima di continuare a usare il dispositivo.
       - **Badge sull'icona di app**: selezionare **abilitare** per aggiungere un badge all'icona dell'app. Il badge indica che l'app ha inviato una notifica.
       - **Suoni**: selezionare **Abilita** per riprodurre un suono quando viene recapitata una notifica.

3. Selezionare **OK** per salvare le modifiche. Continuare ad aggiungere le app desiderate. Al termine, selezionare **OK**.

## <a name="lock-screen-message-settings"></a>Impostazioni del messaggio della schermata di blocco

Usare queste impostazioni per visualizzare un messaggio o un testo personalizzato nella finestra di accesso e nella schermata di blocco. È ad esempio possibile immettere il messaggio "In caso di ritrovamento, restituire a" e informazioni sul tag asset. 

Questa funzionalità supporta i dispositivi con supervisione che eseguono:

- iOS 9.3 e versioni successive

1. In **Impostazioni** selezionare **Messaggio della schermata di blocco (solo con supervisione)**.
2. Immettere le impostazioni seguenti:

    - **Informazioni sui tag asset**: immettere informazioni sul tag asset del dispositivo. Ad esempio, immettere `Owned by Contoso Corp` o `Serial Number: {{serialnumber}}`. 

      Il testo immesso viene visualizzato nella finestra di accesso e nella schermata di blocco di accesso del dispositivo.

    - **Nota a piè di pagina della schermata di blocco**: immettere una nota che può contribuire alla restituzione del dispositivo in caso di furto o smarrimento. È possibile immettere qualsiasi testo. Ad esempio, `If found, call Contoso at ...`.

    Per aggiungere informazioni specifiche del dispositivo in questi campi è anche possibile usare token di dispositivo. Per visualizzare, ad esempio, il numero di serie, immettere `Serial Number: {{serialnumber}}`. Nella schermata di blocco il testo è simile a `Serial Number 123456789ABC`. Quando si immettono le variabili, assicurarsi di usare le parentesi graffe `{{ }}`. I [token di configurazione delle app](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) includono un elenco delle variabili che è possibile usare. È anche possibile usare `deviceName` o qualsiasi altro valore specifico del dispositivo.

    > [!NOTE]
    > Le variabili non vengono convalidate nell'interfaccia utente. Di conseguenza possono essere visualizzati dei profili salvati con input non corretto. Se ad esempio si immette `{{Devicename}}` invece di `{{devicename}}`, viene visualizzata la stringa letterale anziché il nome univoco del dispositivo.

3. Al termine, selezionare **OK** per salvare le modifiche.

## <a name="single-sign-on-settings"></a>Impostazioni di Single Sign-On

La maggior parte delle app line-of-business (LOB) richiedono un certo livello di autenticazione utente per il supporto della sicurezza. In molti casi, l'autenticazione richiede di immettere ripetutamente le stesse credenziali e ciò può essere frustrante per gli utenti. Per migliorare l'esperienza utente, gli sviluppatori possono creare app che usano l'accesso Single Sign-On (SSO). L'uso dell'accesso Single Sign-On riduce il numero di volte in cui un utente deve immettere le credenziali.

Per usare l'accesso Single Sign-On, assicurarsi di avere:

- Un'app sviluppata in modo da cercare l'archivio delle credenziali utente in Single Sign-On sul dispositivo.
- Intune configurato per l'accesso Single Sign-On al dispositivo iOS.

1. In **Impostazioni** selezionare **Single Sign-On**:

   ![Riquadro Single Sign-On](./media/sso-blade.png)

2. Immettere le impostazioni seguenti:

    - **Attributo nome utente da AAD**: Intune cerca questo attributo per ogni utente in Azure AD e quindi popola il campo corrispondente (ad esempio UPN) prima di generare il file XML da installare nel dispositivo. Le opzioni disponibili sono:

      - **Nome entità utente**: l'UPN viene analizzato nel modo seguente:

        ![Attributo nome utente](media/User-name-attribute.png)

        È anche possibile sovrascrivere l'area di autenticazione con il testo immesso nella casella di testo **Area di autenticazione**.

        Contoso, ad esempio, ha più aree, tra cui Europa, Asia e America del Nord. Contoso vuole che gli utenti in Asia usino SSO e l'app richiede l'UPN nel formato `username@asia.contoso.com`. Quando si seleziona **Nome entità utente**, l'area di autenticazione per ogni utente viene recuperata da Azure AD e corrisponde a `contoso.com`. Per gli utenti in Asia, selezionare quindi **Nome entità utente** e immettere `asia.contoso.com`. L'UPN dell'utente finale diventa `username@asia.contoso.com` invece di `username@contoso.com`.

      - **ID dispositivo Intune**: Intune seleziona automaticamente l'ID dispositivo di Intune.

        Per impostazione predefinita, le app devono usare solo l'ID del dispositivo. Se l'app usa l'area di autenticazione e l'ID del dispositivo, tuttavia, è possibile digitare l'area di autenticazione nella casella di testo Area di autenticazione.

        > [!NOTE]
        > Per impostazione predefinita, mantenere vuoto il campo dell'area di autenticazione se si usa l'ID del dispositivo.

      - **ID dispositivo di Azure AD**

    - **Area autenticazione**: immettere la parte del dominio dell'URL. Immettere ad esempio `contoso.com`.
    - **Prefissi di URL che useranno l'accesso Single Sign-On**: **aggiungere** tutti gli URL dell'organizzazione che richiedono l'autenticazione Single Sign-On.

        Quando un utente si connette a uno di questi siti, ad esempio, il dispositivo iOS usa le credenziali Single Sign-On. L'utente non deve immettere credenziali aggiuntive. Se è abilitata l'autenticazione a più fattori, gli utenti devono immettere la seconda autenticazione.

        > [!NOTE]
        > Questi URL devono essere nomi di dominio completi formattati in modo appropriato. Apple richiede che siano nel formato `http://<yourURL.domain>`.

        I criteri di corrispondenza per gli URL devono iniziare con `http://` o `https://`. Viene eseguito un confronto di stringhe semplice e quindi il prefisso URL `http://www.contoso.com/` non corrisponde a `http://www.contoso.com:80/`. Con iOS 10.0 o versioni successive è possibile immettere tutti i valori corrispondenti usando un solo carattere jolly \*. Ad esempio, `http://*.contoso.com/` corrisponde sia a `http://store.contoso.com/` che a `http://www.contoso.com`.

        I criteri `http://.com` e `https://.com` corrispondono rispettivamente a tutti gli URL HTTP e HTTPS.

    - **App che useranno l'accesso Single Sign-On**: **aggiungere** le app dei dispositivi degli utenti finali che potranno usare l'accesso Single Sign-On.

        La matrice `AppIdentifierMatches` deve includere stringhe corrispondenti agli ID dei bundle dell'app. Queste stringhe possono essere corrispondenze esatte, ad esempio `com.contoso.myapp`. In alternativa, immettere una corrispondenza di prefisso per l'ID del bundle usando il carattere jolly \*. Il carattere jolly deve essere visualizzato dopo un punto (.) e può comparire una sola volta alla fine della stringa, ad esempio `com.contoso.*`. Quando si include un carattere jolly, viene concesso all'account l'accesso a qualsiasi app il cui ID di bundle inizia con il prefisso.

        Usare **Nome app** per immettere un nome descrittivo per facilitare l'identificazione dell'ID bundle.

    - **Certificato di rinnovo delle credenziali**: se si usano i certificati per l'autenticazione (non le password), selezionare il certificato SCEP o PFX esistente come certificato di autenticazione. In genere, questo certificato è lo stesso distribuito all'utente per altri profili, ad esempio VPN, Wi-Fi o posta elettronica.

3. Al termine, selezionare **OK** per salvare le modifiche.

## <a name="web-content-filter-settings"></a>Impostazioni del filtro contenuto Web

Queste impostazioni controllano l'accesso all'URL del browser nei dispositivi iOS.

1. In **Impostazioni** selezionare **Filtro contenuto Web (solo con supervisione)**.
2. Scegliere il **tipo di filtro**. Le opzioni disponibili sono:

    - **Configura gli URL**: usare il filtro Web predefinito di Apple che cerca termini per adulti, incluso un linguaggio volgare e sessualmente esplicito. Questa funzionalità valuta ogni pagina Web quando viene caricata e identifica e blocca i contenuti non appropriati. È anche possibile aggiungere gli URL che si preferisce non vengano controllati dal filtro oppure bloccare URL specifici, indipendentemente dalle impostazioni di filtro di Apple.

      - **URL autorizzati**: **Add** gli URL si vuole consentire. Questi URL ignorano il filtro Web di Apple.

        > [!NOTE]
        > Gli URL immessi sono quelli che non devono essere valutati dal filtro Web di Apple. Questi URL non sono un elenco di siti Web consentiti. Per creare un elenco di siti Web consentiti, impostare **Tipo filtro** su **Solo siti Web specifici**.

        Selezionare **OK** per salvare le modifiche.

      - **URL bloccati**: **aggiungere** gli URL di cui si vuole impedire l'apertura, indipendentemente dalle impostazioni del filtro Web di Apple.

        Selezionare **OK** per salvare le modifiche.

    - **Specificare solo i siti Web** (solo per il Web browser Safari): questi URL vengono aggiunti ai segnalibri del browser Safari. Viene consentito all'utente di visitare **solo** questi siti e non è possibile aprire altri siti. Usare questa opzione solo se si conosce l'elenco esatto degli URL a cui gli utenti possono accedere.

      - **URL**: immettere l'URL del sito Web che si vuole consentire. Immettere ad esempio `https://www.contoso.com`.
      - **Percorso del segnalibro**: immettere il percorso per archiviare il segnalibro. Immettere ad esempio `/Contoso/Business Apps`. Se non si aggiunge un percorso, il segnalibro verrà aggiunto alla cartella dei segnalibri predefiniti nel dispositivo.
      - **Titolo**: immettere un titolo descrittivo per il segnalibro.

      Se non si immettono URL, gli utenti finali possono accedere solo ai siti Web `microsoft.com`, `microsoft.net` e `apple.com`. Questi URL sono automaticamente consentiti da Intune.

      Selezionare **OK** per salvare le modifiche.

## <a name="wallpaper-settings"></a>Impostazioni dello sfondo

Aggiungere un'immagine PNG, JPG o JPEG personalizzata ai dispositivi iOS con supervisione. Usare, ad esempio, un logo aziendale nella schermata di blocco.

Può verificarsi un comportamento imprevisto quando un profilo senza immagine viene assegnato a dispositivi con un'immagine esistente. Ad esempio, si crea un profilo senza un'immagine. Il profilo viene assegnato a dispositivi che dispongono già di un'immagine. In questo scenario è possibile che l'immagine assuma il valore predefinito del dispositivo o che l'immagine originale rimanga nel dispositivo. Questo comportamento è controllato e limitato dalla piattaforma MDM di Apple.

- **Dello sfondo di visualizzazione Location**: scegliere un percorso nel dispositivo per visualizzare l'immagine. Le opzioni disponibili sono:
  - **Non configurato**: un'immagine personalizzata non è aggiunto al dispositivo. Il dispositivo usa l'impostazione predefinita del sistema operativo.
  - **Schermata di blocco**: aggiunge l'immagine nella schermata di blocco.
  - **Schermata iniziale**: aggiunge l'immagine alla schermata iniziale.
  - **Schermata di blocco e nella schermata iniziale**: Usa la stessa immagine per la schermata di blocco mentre schermata iniziale.
- **Immagine di sfondo**: caricare un'immagine PNG, JPG o JPEG esistente che si vuole usare. Assicurarsi che le dimensioni del file siano inferiori a 750 KB. È anche possibile **rimuovere** un'immagine aggiunta.

> [!TIP]
> Per visualizzare immagini diverse nella schermata di blocco e nella schermata iniziale, creare un profilo con l'immagine della schermata di blocco. Creare un altro profilo con l'immagine della schermata iniziale. Assegnare entrambi i profili ai gruppi di utenti o dispositivi iOS.

## <a name="bundle-ids-for-built-in-ios-apps"></a>ID bundle per le app iOS predefinite

L'elenco seguente include l'ID bundle di alcune app comuni iOS predefinite. Per l'ID bundle di altre app rivolgersi al fornitore del software.

| ID bundle                   | Nome dell'app     | Pubblicazione |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | App Store    | Apple     |
| com.apple.calculator        | Calcolatrice   | Apple     |
| com.apple.mobilecal         | Calendario     | Apple     |
| com.apple.camera            | Fotocamera       | Apple     |
| com.apple.mobiletimer       | Orologio        | Apple     |
| com.apple.compass           | Bussola      | Apple     |
| com.apple.MobileAddressBook | Contatti     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | File        | Apple     |
| com.apple.mobileme.fmf1     | Trova amici | Apple     |
| com.apple.mobileme.fmip1    | Trova il mio iPhone  | Apple     |
| com.apple.gamecenter        | Area giochi  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | Integrità       | Apple     |
| com.apple.Home              | Home         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | Keynote      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | Maps         | Apple     |
| com.apple.MobileSMS         | Messaggi     | Apple     |
| com.apple.Music             | Musica        | Apple     |
| com.apple.news              | Notizie         | Apple     |
| com.apple.mobilenotes       | Note        | Apple     |
| com.apple.Numbers           | Numeri      | Apple     |
| com.apple.Pages             | .NET        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | Foto       | Apple     |
| com.apple.podcasts          | Podcast     | Apple     |
| com.apple.reminders         | Reminders    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | Impostazioni     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | Stocks       | Apple     |
| com.apple.tips              | Suggerimenti         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | Video       | Apple     |
| com.apple.VoiceMemos        | VoiceMemos   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | Video        | Apple     |
| com.apple.weather           | Weather      | Apple     |

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili di funzionalità dei dispositivi per i dispositivi [macOS](macos-device-features-settings.md).
