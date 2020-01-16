---
title: Impostazioni delle funzionalità dei dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare tutte le impostazioni per configurare i dispositivi iOS per le impostazioni di AirPrint, layout della schermata iniziale, notifiche delle app, dispositivi condivisi, Single Sign-On e filtro del contenuto Web in Microsoft Intune. Usare queste impostazioni in un profilo di configurazione del dispositivo per configurare i dispositivi iOS per l'uso di queste funzionalità Apple nell'organizzazione.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 85fc8bf002a4d5d00d2163c0b75c49d11dcd9b61
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206364"
---
# <a name="ios-and-ipados-device-settings-to-use-common-ios-features-in-intune"></a>Impostazioni dei dispositivi iOS e iPadOS per usare le funzionalità iOS comuni in Intune

Intune include alcune impostazioni predefinite per consentire agli utenti di iOS di usare diverse funzionalità di Apple nei dispositivi. Gli amministratori, ad esempio, possono controllare come gli utenti di iOS usano le stampanti AirPrint, aggiungere app e cartelle al dock e alle pagine nella schermata iniziale, visualizzare le notifiche delle app, visualizzare i dettagli dei tag degli asset nella schermata di blocco, usare l'autenticazione Single Sign-On e autenticare gli utenti con i certificati.

Usare queste funzionalità per controllare i dispositivi iOS nella soluzione di gestione di dispositivi mobili (MDM).

L'articolo elenca queste impostazioni e descrive la funzione di ogni impostazione. Per altre informazioni su queste funzionalità, vedere [aggiungere impostazioni della funzionalità del dispositivo iOS o MacOS](../device-features-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione del dispositivo iOS](../device-features-configure.md).

> [!NOTE]
> Queste impostazioni si applicano a tipi di registrazione diversi, con alcune impostazioni che si applicano a tutte le opzioni di registrazione. Per altre informazioni sui diversi tipi di registrazione, vedere [registrazione iOS](../ios-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: tutti i tipi di registrazione

> [!NOTE]
> Assicurarsi di aggiungere tutte le stampanti allo stesso profilo. Apple impedisce a più profili AirPrint di puntare allo stesso dispositivo.

- **Indirizzo IP**: immettere l'indirizzo IPv4 o IPv6 della stampante. Se si usano i nomi host per identificare le stampanti, è possibile ottenere l'indirizzo IP effettuando il ping della stampante nel terminale. Per informazioni più dettagliate, vedere Ottenere l'indirizzo IP e il percorso (in questo articolo).
- **Percorso**: il percorso è in genere `ipp/print` per le stampanti di rete. Per informazioni più dettagliate, vedere Ottenere l'indirizzo IP e il percorso (in questo articolo).
- **Porta**: immettere la porta di ascolto della destinazione AirPrint. Se si omette questa proprietà, AirPrint usa la porta predefinita. Disponibile in iOS 11.0 e versioni successive.
- **TLS**: scegliere **Abilita** per proteggere le connessioni AirPrint con Transport Layer Security (TLS). Disponibile in iOS 11.0 e versioni successive.

Per aggiungere server AirPrint, è possibile:

- **Aggiungi** aggiunge il server AirPrint all'elenco. È possibile aggiungere molti server AirPrint.
- **Importare** un file con valori delimitati da virgole (CSV) con queste informazioni. In alternativa, **Esporta** per creare un elenco dei server AirPrint aggiunti.

### <a name="get-server-ip-address-resource-path-and-port"></a>Ottenere indirizzo IP del server, percorso della risorsa e porta

Per aggiungere i server AirPrinter, sono necessari l'indirizzo IP della stampante, il percorso della risorsa e la porta. La procedura seguente mostra come ottenere queste informazioni.

1. In un dispositivo Mac connesso alla stessa rete locale (subnet) delle stampanti AirPrint aprire **Terminale** (da **/Applicazioni/Utilità**).
2. Nel terminale digitare `ippfind` e premere INVIO.

    Prendere nota delle informazioni della stampante. Ad esempio, potrebbe restituire un valore simile a `ipp://myprinter.local.:631/ipp/port1`. La prima parte è il nome della stampante. L'ultima parte (`ipp/port1`) è il percorso della risorsa.

3. Nel Terminale digitare `ping myprinter.local` e premere INVIO.

   Prendere nota dell'indirizzo IP. Ad esempio, potrebbe restituire un valore simile a `PING myprinter.local (10.50.25.21)`.

4. Usare i valori del percorso della risorsa e dell'indirizzo IP. In questo esempio l'indirizzo IP è `10.50.25.21` e il percorso della risorsa è `/ipp/port1`.

## <a name="home-screen-layout"></a>Layout della schermata iniziale

Questa funzionalità si applica a:

- iOS 9,3 o versione successiva

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Impostazioni applicabili a: registrazione automatica dei dispositivi (supervisione)

### <a name="dock"></a>Dock

Usare le impostazioni di **Dock** per aggiungere fino a sei elementi o cartelle al dock della schermata iOS. Molti dispositivi supportano un minor numero di elementi. I dispositivi iPhone, ad esempio, supportano al massimo quattro elementi. In questo caso, nel dispositivo verranno visualizzati solo i primi quattro elementi aggiunti.

È possibile aggiungere fino a **sei** elementi (app e cartelle in combinazione) per il dock del dispositivo.

- **Aggiungi**: consente di aggiungere app o cartelle al dock nel dispositivo.
- **Tipo**: aggiungere un'**App** o una **Cartella**:

  - **App**: scegliere questa opzione per aggiungere le app al dock nella schermata. Immettere:

    - **Nome app**: immettere un nome per l'app. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo iOS.
    - **ID bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

  - **Cartella**: scegliere questa opzione per aggiungere una cartella al dock nella schermata.

    Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra e nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

    - **Nome cartella**: immettere il nome della cartella. Questo nome viene visualizzato nel dispositivo degli utenti.
    - **Elenco di pagine**: selezionare **Aggiungi** per aggiungere una pagina e immettere le proprietà seguenti:

      - **Nome della pagina**: Immettere un nome per la pagina. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo iOS.
      - **Nome app**: immettere un nome per l'app. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo iOS.
      - **ID bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

      È possibile aggiungere fino a **20** pagine per il dock del dispositivo.

> [!NOTE]
> Quando si aggiungono icone usando le impostazioni del Dock, le icone nella schermata iniziale e le pagine vengono bloccate e non possono essere spostate. Può essere previsto da iOS e dai criteri MAM di Apple.

#### <a name="example"></a>Esempio

Nell'esempio seguente la schermata del dock mostra solo le app Safari, Mail e Borsa. L'app Mail viene selezionata per visualizzarne le proprietà:

![Impostazioni di esempio del dock iOS](./media/ios-device-features-settings/FfFiUcP.png)

Quando si assegnano i criteri a un iPhone, il dock è simile all'immagine seguente:

![Esempio di layout del dock su iPhone](./media/ios-device-features-settings/bAgCe8F.png)

### <a name="pages"></a>.NET

Aggiungere le pagine che verranno visualizzate nella schermata iniziale e le app che verranno visualizzate in ogni pagina. Le app aggiunte a una pagina vengono disposte da sinistra a destra, nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

> [!TIP]
> Per riordinare gli elementi di qualsiasi schermata iniziale e qualsiasi elenco di pagine, è possibile trascinarli e rilasciarli.

È possibile aggiungere fino a **40** pagine in un dispositivo.

- **Elenco di pagine**: selezionare **Aggiungi** per aggiungere una pagina e immettere le proprietà seguenti:

  - **Nome della pagina**: Immettere un nome per la pagina. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager e *non* viene visualizzato nel dispositivo iOS.

  È possibile aggiungere fino a **60** elementi (app e cartelle in combinazione) in un dispositivo.

  - **Aggiungi**: consente di aggiungere app o cartelle a una pagina nel dispositivo.

    - **Tipo**: aggiungere un'**App** o una **Cartella**:

      - **App**: scegliere questa opzione per aggiungere le app a una pagina nella schermata. Specificare anche:

        - **Nome app**: immettere un nome per l'app. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo iOS.
        - **ID bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

      - **Cartella**: scegliere questa opzione per aggiungere una cartella al dock nella schermata.

        Le app aggiunte a una pagina in una cartella vengono disposte da sinistra a destra e nello stesso ordine dell'elenco. Se si aggiungono più app di quelle che può contenere una pagina, le app vengono spostate in un'altra pagina.

        - **Nome cartella**: immettere un nome per la cartella. Questo nome viene visualizzato agli utenti nel dispositivo.
        - **Aggiungi**: consente di aggiungere pagine alla cartella. Immettere anche le proprietà seguenti:

          - **Nome della pagina**: Immettere un nome per la pagina. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo iOS.
          - **Nome app**: immettere un nome per l'app. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo iOS.
          - **ID bundle dell'app**: immettere l'ID bundle dell'app. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).

#### <a name="example"></a>Esempio

Nell'esempio seguente viene aggiunta una nuova pagina denominata **Contoso**. La pagina visualizza le app Trova amici e Impostazioni. L'app Impostazioni viene selezionata per visualizzarne le proprietà:

![Esempio di impostazioni della schermata iniziale iOS](./media/ios-device-features-settings/Jc2OxyX.png)

Quando si assegnano i criteri a un iPhone, la pagina è simile all'immagine seguente:

![Dispositivo iOS con schermata iniziale modificata](./media/ios-device-features-settings/Bd37PHa.png)

## <a name="app-notifications"></a>Notifiche delle app

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Impostazioni applicabili a: registrazione automatica dei dispositivi (supervisione)

- **Aggiungi**: consente di aggiungere notifiche per le app:

    ![Aggiungere la notifica dell'app nel profilo iOS in Intune](./media/ios-device-features-settings/ios-macos-app-notifications.png)

  - **ID bundle dell'app**: immettere l'**ID bundle dell'app** che si vuole aggiungere. Per alcuni esempi, vedere [ID di bundle per le app iOS predefinite](bundle-ids-built-in-ios-apps.md).
  - **Nome app**: immettere il nome dell'app che si vuole aggiungere. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo.
  - **Autore**: immettere l'autore dell'app da aggiungere. Questo nome viene usato per il riferimento nell'interfaccia di amministrazione di Microsoft Endpoint Manager. *Non* verrà visualizzato nel dispositivo.
  - **Notifiche**: **abilitare** o **disabilitare** l'invio di notifiche al dispositivo da parte dell'app.
    - **Mostra nel centro notifiche**: **Abilita** consente all'app di visualizzare notifiche nel centro notifiche del dispositivo. **Disabilita** impedisce all'app di visualizzare notifiche nel centro notifiche.
    - **Mostra nella schermata di blocco**: selezionare **Abilita** per visualizzare le notifiche dall'app nella schermata di blocco del dispositivo. **Disabilita** impedisce all'app di visualizzare notifiche nella schermata di blocco.
    - **Tipo di avviso**: quando il dispositivo è sbloccato, scegliere come visualizzare la notifica. Le opzioni disponibili sono:
      - **Nessuno**: non vengono visualizzate notifiche.
      - **Banner**: viene brevemente viene visualizzato un banner con la notifica.
      - **Modale**: la notifica viene visualizzata e l'utente deve chiuderla manualmente prima di continuare a usare il dispositivo.
    - **Badge sull'icona dell'app**: selezionare **Abilita** per aggiungere un badge all'icona dell'app. Il badge indica che l'app ha inviato una notifica.
    - **Suoni**: selezionare **Abilita** per riprodurre un suono quando viene recapitata una notifica.

## <a name="lock-screen-message"></a>Messaggio della schermata di blocco

Questa funzionalità si applica a:

- iOS 9.3 e versioni successive

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Impostazioni applicabili a: registrazione automatica dei dispositivi (supervisione)

- **Informazioni sui tag asset**: immettere informazioni sul tag asset del dispositivo. Ad esempio, immettere `Owned by Contoso Corp` o `Serial Number: {{serialnumber}}`.

  Il testo immesso viene visualizzato nella finestra di accesso e nella schermata di blocco di accesso del dispositivo.

- **Nota a piè di pagina della schermata di blocco**: immettere una nota che può contribuire alla restituzione del dispositivo in caso di furto o smarrimento. È possibile immettere qualsiasi testo. Ad esempio, `If found, call Contoso at ...`.

  Per aggiungere informazioni specifiche del dispositivo in questi campi è anche possibile usare token di dispositivo. Per visualizzare, ad esempio, il numero di serie, immettere `Serial Number: {{serialnumber}}`. Nella schermata di blocco il testo è simile a `Serial Number 123456789ABC`. Quando si immettono le variabili, assicurarsi di usare le parentesi graffe `{{ }}`. I [token di configurazione delle app](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) includono un elenco delle variabili che è possibile usare. È anche possibile usare `deviceName` o qualsiasi altro valore specifico del dispositivo.

  > [!NOTE]
  > Le variabili non vengono convalidate nell'interfaccia utente e fanno distinzione tra maiuscole e minuscole. Di conseguenza possono essere visualizzati dei profili salvati con input non corretto. Ad esempio, se si immette `{{DeviceID}}` invece di `{{deviceid}}`, viene visualizzata la stringa letterale anziché l'ID univoco del dispositivo. Assicurarsi di immettere le informazioni corrette.

## <a name="single-sign-on"></a>Single Sign-On

### <a name="settings-apply-to-device-enrollment-automated-device-enrollment-supervised"></a>Le impostazioni si applicano a: registrazione del dispositivo, registrazione automatica dei dispositivi (supervisione)

- **Attributo nome utente da AAD**: Intune cerca questo attributo per ogni utente in Azure AD e quindi popola il campo corrispondente (ad esempio UPN) prima di generare il file XML da installare nel dispositivo. Le opzioni disponibili sono:

  - **Nome entità utente**: l'UPN viene analizzato nel modo seguente:

    ![Attributo nome utente](./media/ios-device-features-settings/User-name-attribute.png)

    È anche possibile sovrascrivere l'area di autenticazione con il testo immesso nella casella di testo **Area di autenticazione**.

    Contoso, ad esempio, ha più aree, tra cui Europa, Asia e America del Nord. Contoso vuole che gli utenti in Asia usino SSO e l'app richiede l'UPN nel formato `username@asia.contoso.com`. Quando si seleziona **Nome entità utente**, l'area di autenticazione per ogni utente viene recuperata da Azure AD e corrisponde a `contoso.com`. Per gli utenti in Asia, selezionare quindi **Nome entità utente** e immettere `asia.contoso.com`. L'UPN dell'utente finale diventa `username@asia.contoso.com` invece di `username@contoso.com`.

  - **ID dispositivo Intune**: Intune seleziona automaticamente l'ID dispositivo di Intune.

    Per impostazione predefinita, le app devono usare solo l'ID del dispositivo. Se l'app usa l'area di autenticazione e l'ID del dispositivo, tuttavia, è possibile digitare l'area di autenticazione nella casella di testo Area di autenticazione.

    > [!NOTE]
    > Per impostazione predefinita, mantenere vuoto il campo dell'area di autenticazione se si usa l'ID del dispositivo.

  - **ID dispositivo di Azure AD**

- **Area di autenticazione**: immettere la parte del dominio dell'URL. Immettere ad esempio `contoso.com`.
- **Prefissi di URL che useranno l'accesso Single Sign-On**: **aggiungere** tutti gli URL all'interno dell'organizzazione che richiedono l'autenticazione Single Sign-On per gli utenti.

  Quando un utente si connette a uno di questi siti, ad esempio, il dispositivo iOS usa le credenziali Single Sign-On. L'utente non deve immettere credenziali aggiuntive. Se è abilitata l'autenticazione a più fattori, gli utenti devono immettere la seconda autenticazione.

  > [!NOTE]
  > Questi URL devono essere nomi di dominio completi formattati in modo appropriato. Apple richiede che siano nel formato `http://<yourURL.domain>`.

  I criteri di corrispondenza per gli URL devono iniziare con `http://` o `https://`. Viene eseguito un confronto di stringhe semplice e quindi il prefisso URL `http://www.contoso.com/` non corrisponde a `http://www.contoso.com:80/`. Con iOS 10.0 o versioni successive è possibile immettere tutti i valori corrispondenti usando un solo carattere jolly \*. Ad esempio, `http://*.contoso.com/` corrisponde sia a `http://store.contoso.com/` che a `http://www.contoso.com`.

  I criteri `http://.com` e `https://.com` corrispondono rispettivamente a tutti gli URL HTTP e HTTPS.

- **App che useranno l'accesso Single Sign-On**: **aggiungere** le app dei dispositivi degli utenti finali che potranno usare l'accesso Single Sign-On.

  La matrice `AppIdentifierMatches` deve includere stringhe corrispondenti agli ID dei bundle dell'app. Queste stringhe possono essere corrispondenze esatte, ad esempio `com.contoso.myapp`. In alternativa, immettere una corrispondenza di prefisso per l'ID del bundle usando il carattere jolly \*. Il carattere jolly deve essere visualizzato dopo un punto (.) e può comparire una sola volta alla fine della stringa, ad esempio `com.contoso.*`. Quando si include un carattere jolly, viene concesso all'account l'accesso a qualsiasi app il cui ID di bundle inizia con il prefisso.

  Usare **Nome app** per immettere un nome descrittivo per facilitare l'identificazione dell'ID bundle.

- **Certificato di rinnovo delle credenziali**: Se si usano i certificati per l'autenticazione (non le password), selezionare il certificato SCEP o PFX esistente come certificato di autenticazione. In genere, questo certificato è lo stesso distribuito all'utente per altri profili, ad esempio VPN, Wi-Fi o posta elettronica.

## <a name="web-content-filter"></a>Filtro contenuto Web

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Impostazioni applicabili a: registrazione automatica dei dispositivi (supervisione)

- **Tipo di filtro**: scegliere se consentire specifici siti Web. Le opzioni disponibili sono:

  - **Configurare gli URL**: usare il filtro Web predefinito di Apple che cerca termini per adulti, incluso un linguaggio volgare e sessualmente esplicito. Questa funzionalità valuta ogni pagina Web quando viene caricata e identifica e blocca i contenuti non appropriati. È anche possibile aggiungere gli URL che si preferisce non vengano controllati dal filtro oppure bloccare URL specifici, indipendentemente dalle impostazioni di filtro di Apple.

    - **URL autorizzati**: **aggiungere** gli URL che si vuole consentire. Questi URL ignorano il filtro Web di Apple.

        > [!NOTE]
        > Gli URL immessi sono quelli che non devono essere valutati dal filtro Web di Apple. Questi URL non sono un elenco di siti Web consentiti. Per creare un elenco di siti Web consentiti, impostare **Tipo filtro** su **Solo siti Web specifici**.

    - **URL bloccati**: **aggiungere** gli URL di cui si vuole impedire l'apertura, indipendentemente dalle impostazioni del filtro Web di Apple.

  - **Solo siti Web specifici** (solo per il Web browser Safari): questi URL vengono aggiunti ai segnalibri del browser Safari. Viene consentito all'utente di visitare **solo** questi siti e non è possibile aprire altri siti. Usare questa opzione solo se si conosce l'elenco esatto degli URL a cui gli utenti possono accedere.

    - **URL**: immettere l'URL del sito Web che si vuole consentire. Immettere ad esempio `https://www.contoso.com`.
    - **Percorso segnalibro**: Apple ha modificato questa impostazione. Tutti i segnalibri vengono inseriti nella cartella **siti approvati** . I segnalibri non passano al percorso del segnalibro immesso.
    - **Titolo**: immettere un titolo descrittivo per il segnalibro.

    Se non si immettono URL, gli utenti finali possono accedere solo ai siti Web `microsoft.com`, `microsoft.net` e `apple.com`. Questi URL sono automaticamente consentiti da Intune.

## <a name="single-sign-on-app-extension"></a>Estensione dell'app Single Sign-On

Questa funzionalità si applica a:

- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: tutti i tipi di registrazione

- **Tipo di estensione dell'app SSO**: scegliere il tipo di estensione dell'app SSO. Le opzioni disponibili sono:

  - **Non configurato**: non vengono usate le estensioni dell'app. Per disabilitare un'estensione dell'app, è possibile impostare il tipo di estensione dell'app SSO su **non configurato**.
  - **Reindirizzamento**: usare un'estensione di app di reindirizzamento generica e personalizzabile per eseguire l'accesso SSO con flussi di autenticazione moderni. Assicurarsi di conoscerne l'ID estensione per l'estensione dell'app dell'organizzazione.
  - **Credenziale**: usare un'estensione di app per le credenziali personalizzabile e generica per eseguire l'accesso SSO con i flussi di autenticazione di richiesta-risposta. Assicurarsi di conoscerne l'ID estensione per l'estensione dell'app dell'organizzazione.
  - **Kerberos**: usare l'estensione Kerberos predefinita di Apple, inclusa in iOS 13,0 (e versioni successive) e ipados 13,0 (e versioni successive). Questa opzione è una versione specifica di Kerberos dell'estensione dell'app per le **credenziali** .

  > [!TIP]
  > Con i tipi **Reindirizzamento** e **credenziali** è possibile aggiungere i propri valori di configurazione per passare attraverso l'estensione. Se si usano le **credenziali**, provare a usare le impostazioni di configurazione predefinite fornite da Apple nel tipo **Kerberos** .

- **ID estensione** (Reindirizzamento e credenziali): immettere l'identificatore del bundle che identifica l'estensione dell'app SSO, ad esempio `com.apple.extensiblesso`.

- **ID team** (Reindirizzamento e credenziali): immettere l'identificatore del team dell'estensione dell'app SSO. Un identificatore del team è una stringa alfanumerica (numeri e lettere) di 10 caratteri generata da Apple, ad esempio `ABCDE12345`. L'ID team non è obbligatorio.

  [Individuare l'ID del team](https://help.apple.com/developer-account/#/dev55c3c710c) (aprire il sito Web di Apple) con ulteriori informazioni.

- **Area** di autenticazione (credenziale e Kerberos): immettere il nome dell'area di autenticazione. Il nome dell'area di autenticazione deve essere in maiuscolo, ad esempio `CONTOSO.COM`. In genere, il nome dell'area di autenticazione corrisponde al nome di dominio DNS, ma in maiuscolo.

- **Domini** (Credential e Kerberos): immettere il dominio o i nomi host dei siti che possono eseguire l'autenticazione tramite SSO. Ad esempio, se il sito Web è `mysite.contoso.com`, `mysite` è il nome host e `contoso.com` è il nome di dominio. Quando gli utenti si connettono a uno di questi siti, l'estensione dell'app gestisce la richiesta di autenticazione. Questa autenticazione consente agli utenti di usare l'ID del viso, l'ID tocco o il pincode/codice Apple per accedere.

  - Tutti i domini nei profili di Intune dell'estensione dell'app Single Sign-On devono essere univoci. Non è possibile ripetere un dominio in nessun profilo di estensione dell'app di accesso, anche se si usano tipi diversi di estensioni di app SSO.
  - Questi domini non fanno distinzione tra maiuscole e minuscole.

- **URL** (solo Reindirizzamento): immettere i prefissi URL dei provider di identità per conto del quale l'estensione di reindirizzamento app esegue l'accesso SSO. Quando un utente viene reindirizzato a questi URL, l'estensione dell'app SSO interviene e richiede l'accesso SSO.

  - Tutti gli URL nei profili di estensione dell'app Single Sign-On di Intune devono essere univoci. Non è possibile ripetere un dominio in nessun profilo di estensione dell'app SSO, anche se si usano tipi diversi di estensioni di app SSO.
  - Gli URL devono iniziare con http://o https://.

- **Configurazione aggiuntiva** (Reindirizzamento e credenziali): immettere dati aggiuntivi specifici dell'estensione da passare all'estensione dell'app SSO:
  - **Chiave**: immettere il nome dell'elemento che si vuole aggiungere, ad esempio `user name`.
  - **Tipo**: immettere il tipo di dati. Le opzioni disponibili sono:

    - Stringa
    - Booleano: in **valore di configurazione**immettere `True` o `False`.
    - Integer: in **valore di configurazione**immettere un numero.
    
  - **Valore**: immettere i dati.

  - **Aggiungi**: selezionare questa impostazione per aggiungere le chiavi di configurazione.

- **Utilizzo Keychain** (solo Kerberos): scegliere **blocco** per impedire il salvataggio e l'archiviazione delle password nel keychain. **Non configurato** (impostazione predefinita) consente il salvataggio e l'archiviazione delle password nel keychain.
- **ID viso, ID tocco o codice** di accesso (solo Kerberos): **Richiedi** impone agli utenti di immettere il proprio ID viso, ID tocco o il codice di accesso Apple per accedere ai domini aggiunti. **Non configurato** (impostazione predefinita) non richiede agli utenti di usare la biometria o il codice di accesso per accedere.
- **Area di autenticazione predefinita** (solo Kerberos): scegliere **Abilita** per impostare il valore dell' **area di autenticazione** immesso come area di autenticazione predefinita. **Non configurato** (impostazione predefinita) non imposta un'area di autenticazione predefinita.

  > [!TIP]
  > - **Abilitare** questa impostazione se si stanno configurando più estensioni dell'app SSO Kerberos nell'organizzazione.
  > - **Abilitare** questa impostazione se si usano più aree di autenticazione. Imposta il valore dell' **area di autenticazione** immesso come area di autenticazione predefinita.
  > - Se si dispone solo di un'area di autenticazione, lasciarla **non configurata** (impostazione predefinita).

- **Nome entità** (solo Kerberos): immettere il nome utente dell'entità Kerberos. Non è necessario includere il nome dell'area di autenticazione. Ad esempio, in `user@contoso.com`, `user` è il nome dell'entità e `contoso.com` è il nome dell'area di autenticazione.

  > [!TIP]
  > - È anche possibile usare le variabili nel nome principale immettendo parentesi graffe `{{ }}`. Ad esempio, per visualizzare il nome utente, immettere `Username: {{username}}`. 
  > - Tuttavia, prestare attenzione con la sostituzione delle variabili perché le variabili non vengono convalidate nell'interfaccia utente e fanno distinzione tra maiuscole e minuscole. Assicurarsi di immettere le informazioni corrette.

- **Active Directory codice sito** (solo Kerberos): immettere il nome del sito Active Directory che deve essere utilizzato dall'estensione Kerberos. Potrebbe non essere necessario modificare questo valore, perché l'estensione Kerberos potrebbe trovare automaticamente il codice del sito Active Directory.
- **Nome cache** (solo Kerberos): immettere il nome GSS (Generic Security Services) della cache Kerberos. Probabilmente non è necessario impostare questo valore.
- **ID bundle dell'app** (solo Kerberos): **aggiungere** gli identificatori del bundle dell'app che devono usare Single Sign-on nei dispositivi. A queste app viene concesso l'accesso al ticket di concessione ticket Kerberos, il ticket di autenticazione e l'autenticazione degli utenti ai servizi a cui sono autorizzati ad accedere.
- **Mapping dell'area di autenticazione del dominio** (solo Kerberos): **aggiungere** i suffissi DNS di dominio che devono essere mappati all'area di autenticazione. Usare questa impostazione quando i nomi DNS degli host non corrispondono al nome dell'area di autenticazione. Probabilmente non è necessario creare questo mapping da dominio a area di autenticazione personalizzato.
- **Certificato PKINIT** (solo Kerberos): **selezionare** il certificato di crittografia a chiave pubblica per l'autenticazione iniziale (PKINIT) che può essere usato per l'autenticazione Kerberos. È possibile scegliere tra i certificati [PKCS](../protect/certficates-pfx-configure.md) o [SCEP](../protect/certificates-scep-configure.md) aggiunti in Intune. Per altre informazioni sui certificati, vedere [usare i certificati per l'autenticazione in Microsoft Intune](../protect/certificates-configure.md).

## <a name="wallpaper"></a>Wallpaper

Può verificarsi un comportamento imprevisto quando un profilo senza immagine viene assegnato a dispositivi con un'immagine esistente. Ad esempio, si crea un profilo senza un'immagine. Il profilo viene assegnato a dispositivi che dispongono già di un'immagine. In questo scenario è possibile che l'immagine assuma il valore predefinito del dispositivo o che l'immagine originale rimanga nel dispositivo. Questo comportamento è controllato e limitato dalla piattaforma MDM di Apple.

### <a name="settings-apply-to-automated-device-enrollment-supervised"></a>Impostazioni applicabili a: registrazione automatica dei dispositivi (supervisione)

- **Posizione di visualizzazione dello sfondo**: Scegliere una posizione nel dispositivo per visualizzare l'immagine. Le opzioni disponibili sono:
  - **Non configurata**: un'immagine personalizzata non viene aggiunta al dispositivo. Il dispositivo usa l'impostazione predefinita del sistema operativo.
  - **Schermata di blocco**: aggiunge l'immagine alla schermata di blocco.
  - **Home screen** (Schermata iniziale): aggiunge l'immagine alla schermata iniziale.
  - **Schermata di blocco e schermata iniziale**: usa la stessa immagine nella schermata di blocco e nella schermata iniziale.
- **Immagine di sfondo**: caricare un'immagine PNG, JPG o JPEG esistente che si vuole usare. Assicurarsi che le dimensioni del file siano inferiori a 750 KB. È anche possibile **rimuovere** un'immagine aggiunta.

> [!TIP]
> Per visualizzare immagini diverse nella schermata di blocco e nella schermata iniziale, creare un profilo con l'immagine della schermata di blocco. Creare un altro profilo con l'immagine della schermata iniziale. Assegnare entrambi i profili ai gruppi di utenti o dispositivi iOS.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](../device-profile-monitor.md).

È anche possibile creare profili di funzionalità dei dispositivi per i dispositivi [macOS](macos-device-features-settings.md).
