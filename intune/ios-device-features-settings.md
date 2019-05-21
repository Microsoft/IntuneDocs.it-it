---
title: Impostazioni delle funzionalità dei dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare tutte le impostazioni per configurare i dispositivi iOS per le impostazioni di AirPrint, layout della schermata iniziale, notifiche delle app, dispositivi condivisi, Single Sign-On e filtro del contenuto Web in Microsoft Intune. Usare queste impostazioni in un profilo di configurazione del dispositivo per configurare i dispositivi iOS per usare queste diverse funzionalità Apple nell'organizzazione.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2019
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
ms.openlocfilehash: 1bcd3a5d0b9f7abc1aa2e0b4d96c30c956b6b4c7
ms.sourcegitcommit: b0cf661145ccc6e3518db620af199786a623a0d9
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 04/28/2019
ms.locfileid: "64764889"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>Impostazioni dei dispositivi iOS per usare le funzionalità iOS comuni in Intune

Intune include alcune impostazioni predefinite per consentire agli utenti di iOS di usare diverse funzionalità di Apple nei dispositivi. Gli amministratori, ad esempio, possono controllare come gli utenti di iOS usano le stampanti AirPrint, aggiungere app e cartelle al dock e alle pagine nella schermata iniziale, visualizzare le notifiche delle app, visualizzare i dettagli dei tag degli asset nella schermata di blocco, usare l'autenticazione Single Sign-On e autenticare gli utenti con i certificati.

Usare queste funzionalità per controllare i dispositivi iOS nella soluzione di gestione di dispositivi mobili (MDM).

L'articolo elenca queste impostazioni e descrive la funzione di ogni impostazione.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo iOS](device-features-configure.md#create-a-device-profile).

## <a name="airprint"></a>AirPrint

- **Indirizzo IP**: immettere l'indirizzo IPv4 o IPv6 della stampante. Se si usano i nomi host per identificare le stampanti, è possibile ottenere l'indirizzo IP effettuando il ping della stampante nel terminale. Per informazioni più dettagliate, vedere Ottenere l'indirizzo IP e il percorso (in questo articolo).
- **Percorso**: il percorso è in genere `ipp/print` per le stampanti di rete. Per informazioni più dettagliate, vedere Ottenere l'indirizzo IP e il percorso (in questo articolo).
- **Porta**: immettere la porta di ascolto della destinazione AirPrint. Se si omette questa proprietà, AirPrint usa la porta predefinita. Disponibile in iOS 11.0 e versioni successive.
- **TLS**: scegliere **Abilita** per proteggere le connessioni AirPrint con Transport Layer Security (TLS). Disponibile in iOS 11.0 e versioni successive.

**Aggiungi** aggiunge il server AirPrint all'elenco. È possibile aggiungere più server AirPrint. È anche possibile **importare** un file con valori delimitati da virgole (CSV) con queste informazioni. Dopo aver creato l'elenco, è anche possibile **esportare** l'elenco di server AirPrint.

Selezionare **OK** per salvare l'elenco.

### <a name="get-server-ip-address-resource-path-and-port"></a>Ottenere indirizzo IP del server, percorso della risorsa e porta

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

È possibile aggiungere fino a **sei** elementi (app e cartelle in combinazione) per il dock del dispositivo.

- **Aggiungi**: consente di aggiungere app o cartelle al dock nel dispositivo.
- **Tipo**: aggiungere un'**App** o una **Cartella**:

  - **App**: scegliere questa opzione per aggiungere le app al dock nella schermata. Immettere

    - **Nome app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
    - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

    Selezionare **OK** per salvare le modifiche.

  - **Cartella**: scegliere questa opzione per aggiungere una cartella al dock nella schermata.

    Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra e nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

    - **Nome della cartella**: immettere il nome della cartella. Questo nome viene visualizzato nel dispositivo degli utenti.
    - **Elenco di pagine**: selezionare **Aggiungi** per aggiungere una pagina e immettere le proprietà seguenti:

      - **Nome pagina** : immettere un nome per la pagina. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
      - **Nome app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
      - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

      È possibile aggiungere fino a **20** pagine per il dock del dispositivo.

    Selezionare **OK** per salvare le modifiche.

> [!NOTE]
> Quando si aggiungono icone usando le impostazioni del Dock, le icone nella schermata iniziale e le pagine vengono bloccate e non possono essere spostate. Può essere previsto da iOS e dai criteri MAM di Apple.

#### <a name="example"></a>Esempio

Nell'esempio seguente la schermata del dock mostra solo le app Safari, Mail e Borsa. L'app Mail viene selezionata per visualizzarne le proprietà:

![Impostazioni di esempio del dock iOS](./media/FfFiUcP.png)

Quando si assegnano i criteri a un iPhone, il dock è simile all'immagine seguente:

![Esempio di layout del dock su iPhone](./media/bAgCe8F.png)

### <a name="pages"></a>.NET

Aggiungere le pagine che verranno visualizzate nella schermata iniziale e le app che verranno visualizzate in ogni pagina. Le app aggiunte a una pagina vengono disposte da sinistra a destra, nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

> [!TIP]
> Per riordinare gli elementi di qualsiasi schermata iniziale e qualsiasi elenco di pagine, è possibile trascinarli e rilasciarli.

È possibile aggiungere fino a **40** pagine in un dispositivo.

- **Elenco di pagine**: selezionare **Aggiungi** per aggiungere una pagina e immettere le proprietà seguenti:

  - **Nome pagina** : immettere un nome per la pagina. Questo nome viene usato come riferimento nel portale di Azure e *non* viene visualizzato nel dispositivo iOS.

  È possibile aggiungere fino a **60** elementi (app e cartelle in combinazione) in un dispositivo.

  - **Aggiungi**: consente di aggiungere app o cartelle a una pagina nel dispositivo.

    - **Tipo**: aggiungere un'**App** o una **Cartella**:

      - **App**: scegliere questa opzione per aggiungere le app a una pagina nella schermata. Specificare anche:

        - **Nome app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
        - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

      Selezionare **OK** per salvare le modifiche.

      - **Cartella**: scegliere questa opzione per aggiungere una cartella al dock nella schermata.

        Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra e nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

        - **Nome cartella**: immettere un nome per la cartella. Questo nome viene visualizzato agli utenti nel dispositivo.
        - **Aggiungi**: consente di aggiungere pagine alla cartella. Immettere anche le proprietà seguenti:

          - **Nome pagina** : immettere un nome per la pagina. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
          - **Nome app**: immettere un nome per l'app. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo iOS.
          - **ID Bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

      Selezionare **OK** per salvare le modifiche.

#### <a name="example"></a>Esempio

Nell'esempio seguente viene aggiunta una nuova pagina denominata **Contoso**. La pagina visualizza le app Trova amici e Impostazioni. L'app Impostazioni viene selezionata per visualizzarne le proprietà:

![Esempio di impostazioni della schermata iniziale iOS](./media/Jc2OxyX.png)

Quando si assegnano i criteri a un iPhone, la pagina è simile all'immagine seguente:

![Dispositivo iOS con schermata iniziale modificata](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>Impostazioni delle notifiche delle app

Scegliere la modalità in cui le app installate nei dispositivi iOS devono inviare notifiche. Queste impostazioni supportano dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

- **Aggiungi**: consente di aggiungere notifiche per le app:

    ![Aggiungere la notifica dell'app nel profilo iOS in Intune](./media/ios-macos-app-notifications.png)

  - **ID bundle dell'app**: immettere l'**ID bundle dell'app** che si vuole aggiungere. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).
  - **Nome app**: immettere il nome dell'app che si vuole aggiungere. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo.
  - **Autore**: immettere l'autore dell'app da aggiungere. Questo nome viene usato come riferimento nel portale di Azure. *Non* verrà visualizzato nel dispositivo.
  - **Notifiche**: **abilitare** o **disabilitare** l'invio di notifiche al dispositivo da parte dell'app.
    - **Mostra nel centro notifiche**: **Abilita** consente all'app di visualizzare notifiche nel centro modifiche del dispositivo. **Disabilita** impedisce all'app di visualizzare notifiche nel centro notifiche.
    - **Mostra nella schermata di blocco**: selezionare **Abilita** per visualizzare le notifiche dall'app nella schermata di blocco del dispositivo. **Disabilita** impedisce all'app di visualizzare notifiche nella schermata di blocco.
    - **Tipo avviso**: quando il dispositivo è sbloccato, scegliere come visualizzare la notifica. Le opzioni disponibili sono:
      - **Nessuno**: non vengono visualizzate notifiche.
      - **Banner**: viene brevemente visualizzato un banner con la notifica.
      - **Modale**: la notifica viene visualizzata e l'utente deve chiuderla manualmente prima di continuare a usare il dispositivo.
    - **Badge sull'icona dell'app**: selezionare **Abilita** per aggiungere un badge all'icona dell'app. Il badge indica che l'app ha inviato una notifica.
    - **Suoni**: selezionare **Abilita** per riprodurre un suono quando viene recapitata una notifica.

Selezionare **OK** per salvare le modifiche.

## <a name="lock-screen-message-settings"></a>Impostazioni del messaggio della schermata di blocco

Usare queste impostazioni per visualizzare un messaggio o un testo personalizzato nella finestra di accesso e nella schermata di blocco. È ad esempio possibile immettere il messaggio "In caso di ritrovamento, restituire a" e informazioni sul tag asset. 

Questa funzionalità supporta i dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

- **Informazioni sui tag asset**: immettere informazioni sul tag asset del dispositivo. Ad esempio, immettere `Owned by Contoso Corp` o `Serial Number: {{serialnumber}}`.

  Il testo immesso viene visualizzato nella finestra di accesso e nella schermata di blocco di accesso del dispositivo.

- **Nota a piè di pagina della schermata di blocco**: immettere una nota che può contribuire alla restituzione del dispositivo in caso di furto o smarrimento. È possibile immettere qualsiasi testo. Ad esempio, `If found, call Contoso at ...`.

  Per aggiungere informazioni specifiche del dispositivo in questi campi è anche possibile usare token di dispositivo. Per visualizzare, ad esempio, il numero di serie, immettere `Serial Number: {{serialnumber}}`. Nella schermata di blocco il testo è simile a `Serial Number 123456789ABC`. Quando si immettono le variabili, assicurarsi di usare le parentesi graffe `{{ }}`. I [token di configurazione delle app](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) includono un elenco delle variabili che è possibile usare. È anche possibile usare `deviceName` o qualsiasi altro valore specifico del dispositivo.

  > [!NOTE]
  > Le variabili non vengono convalidate nell'interfaccia utente. Di conseguenza possono essere visualizzati dei profili salvati con input non corretto. Se ad esempio si immette `{{Devicename}}` invece di `{{devicename}}`, viene visualizzata la stringa letterale anziché il nome univoco del dispositivo.

Selezionare **OK** per salvare le modifiche.

## <a name="single-sign-on-settings"></a>Impostazioni di Single Sign-On

La maggior parte delle app line-of-business (LOB) richiedono un certo livello di autenticazione utente per il supporto della sicurezza. In molti casi, l'autenticazione richiede di immettere ripetutamente le stesse credenziali e ciò può essere frustrante per gli utenti. Per migliorare l'esperienza utente, gli sviluppatori possono creare app che usano l'accesso Single Sign-On (SSO). L'uso dell'accesso Single Sign-On riduce il numero di volte in cui un utente deve immettere le credenziali.

Per usare l'accesso Single Sign-On, assicurarsi di avere:

- Un'app sviluppata in modo da cercare l'archivio delle credenziali utente in Single Sign-On sul dispositivo.
- Intune configurato per l'accesso Single Sign-On al dispositivo iOS.

![Riquadro Single Sign-On](./media/sso-blade.png)

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

Selezionare **OK** per salvare le modifiche.

## <a name="web-content-filter-settings"></a>Impostazioni del filtro contenuto Web

Queste impostazioni controllano l'accesso all'URL del browser nei dispositivi iOS.

- **Tipo di filtro**: scegliere se consentire specifici siti Web. Le opzioni disponibili sono:

  - **Configura gli URL**: usare il filtro Web predefinito di Apple che cerca termini per adulti, incluso un linguaggio volgare e sessualmente esplicito. Questa funzionalità valuta ogni pagina Web quando viene caricata e identifica e blocca i contenuti non appropriati. È anche possibile aggiungere gli URL che si preferisce non vengano controllati dal filtro oppure bloccare URL specifici, indipendentemente dalle impostazioni di filtro di Apple.

    - **URL autorizzati**: **aggiungere** gli URL che si vuole consentire. Questi URL ignorano il filtro Web di Apple.

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

- **Posizione di visualizzazione dello sfondo**: scegliere una posizione nel dispositivo per visualizzare l'immagine. Le opzioni disponibili sono:
  - **Non configurata**: un'immagine personalizzata non viene aggiunta al dispositivo. Il dispositivo usa l'impostazione predefinita del sistema operativo.
  - **Schermata di blocco**: aggiunge l'immagine alla schermata di blocco.
  - **Schermata iniziale**: aggiunge l'immagine alla schermata iniziale.
  - **Schermata di blocco e schermata iniziale**: usa la stessa immagine nella schermata di blocco e nella schermata iniziale.
- **Immagine di sfondo**: caricare un'immagine PNG, JPG o JPEG esistente che si vuole usare. Assicurarsi che le dimensioni del file siano inferiori a 750 KB. È anche possibile **rimuovere** un'immagine aggiunta.

> [!TIP]
> Per visualizzare immagini diverse nella schermata di blocco e nella schermata iniziale, creare un profilo con l'immagine della schermata di blocco. Creare un altro profilo con l'immagine della schermata iniziale. Assegnare entrambi i profili ai gruppi di utenti o dispositivi iOS.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile creare profili di funzionalità dei dispositivi per i dispositivi [macOS](macos-device-features-settings.md).
