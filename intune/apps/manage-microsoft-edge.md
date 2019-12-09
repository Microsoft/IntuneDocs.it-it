---
title: Gestire Microsoft Edge per iOS e Android con Intune
titleSuffix: ''
description: Usare i criteri di protezione delle app di Intune con Microsoft Edge per garantire che l'accesso ai siti Web aziendali venga sempre eseguito con misure di sicurezza applicate.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e4761e2565402b4c3cdc993ff89cbedea8273609
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563888"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Gestire l'accesso Web usando Microsoft Edge con Microsoft Intune

L'uso dei criteri di protezione delle app di Intune con Microsoft Edge è utile per garantire che l'accesso ai siti Web aziendali avvenga sempre con le dovute misure di sicurezza. Sono disponibili le seguenti funzionalità aziendali di Microsoft Edge abilitate dai criteri di Intune:

- **Doppia identità.** Gli utenti possono aggiungere sia un account aziendale che un account personale per l'esplorazione. Le due identità sono completamente separate, in modo analogo all'architettura e all'esperienza utente di Office 365 e Outlook. Gli amministratori di Intune possono impostare i criteri desiderati per un'esperienza di esplorazione protetta nell'ambito dell'account aziendale.
- **Integrazione dei criteri di protezione delle app di Intune.** Poiché Microsoft Edge si integra con Intune SDK, è possibile assegnare i criteri di protezione delle app per la protezione da perdite di dati. Queste funzionalità includono il controllo delle operazioni taglia, copia e incolla, il blocco delle acquisizioni di schermate e l'apertura dei collegamenti selezionati dagli utenti solo in altre app gestite.
- **Integrazione di Azure Application Proxy.** È possibile controllare l'accesso alle app SaaS (software come un servizio) e alle app Web. Ciò consente di assicurarsi che le app basate su browser vengano eseguite solo nel browser Microsoft Edge sicuro, sia che gli utenti finali si connettano dalla rete aziendale che da Internet.
- **Configurazione delle applicazioni.** È possibile usare le impostazioni di configurazione delle applicazioni per rafforzare la sicurezza delle organizzazioni e configurare funzionalità facili da usare per gli utenti finali. È ad esempio possibile definire segnalibri, un collegamento alla home page, siti consentiti o bloccati e Azure Active Directory (Azure AD) Application Proxy.

I criteri di protezione di Microsoft Intune per Microsoft Edge contribuiscono a proteggere i dati e le risorse dell'organizzazione. Usando questi criteri con Microsoft Edge le risorse aziendali sono protette non solo all'interno delle app installate in modo nativo, ma anche in caso di accesso tramite il Web browser.

## <a name="getting-started"></a>Guida introduttiva

È possibile scaricare Microsoft Edge dagli app store pubblici per l'uso nelle organizzazioni. I requisiti del sistema operativo per i criteri del browser sono i seguenti:
- Android 4 e versioni successive
- iOS 8.0 e versioni successive

## <a name="application-protection-policies-for-microsoft-edge"></a>Criteri di protezione delle applicazioni per Microsoft Edge

Poiché Microsoft Edge si integra con Intune SDK, è possibile applicare anche a questa soluzione i criteri di protezione delle applicazioni.

È possibile applicare queste impostazioni ai dispositivi seguenti:
- Dispositivi registrati in Intune.
- Dispositivi registrati in un altro prodotto di gestione di dispositivi mobili.
- Dispositivi non gestiti.

Se a Microsoft Edge non sono assegnati criteri di Intune, gli utenti non possono usarlo per accedere ai dati da altre applicazioni gestite da Intune, ad esempio le app di Office. 

## <a name="conditional-access-for-microsoft-edge"></a>Accesso condizionale per Microsoft Edge

È possibile usare l'accesso condizionale di Azure AD per reindirizzare gli utenti in modo da accedere ai contenuti aziendali solo attraverso Microsoft Edge. L'accesso tramite browser per dispositivi mobili alle app Web connesse ad Azure AD viene così limitato a Microsoft Edge protetto da criteri. Questo blocca l'accesso da altri browser non protetti, ad esempio Safari o Chrome. È possibile applicare l'accesso condizionale a risorse di Azure come Exchange Online e SharePoint Online, l'interfaccia di amministrazione di Microsoft 365 e anche siti locali esposti agli utenti esterni tramite [Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started).

Per fare in modo che le app Web connesse ad Azure AD usino solo Microsoft Edge in iOS e Android:
1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Nel nodo Intune selezionare **Accesso condizionale** > **Nuovi criteri**.
3. Selezionare **Concedi** dalla sezione **Controlli di accesso** del riquadro.
4. Selezionare **Richiedi app client approvata**.
5. Scegliere **Seleziona** nel riquadro **Concedi**. Questi criteri devono essere assegnati alle app cloud che si vuole rendere accessibili solo per l'app Intune Managed Browser.

    ![Screenshot dei criteri di accesso condizionale - Concedi](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. Nella sezione Assegnazioni selezionare **Condizioni** > **App**. Viene visualizzato il riquadro**App**.
7. Selezionare **Sì** in **Configura** per applicare i criteri ad app client specifiche.
8. Verificare che sia selezionata l'opzione **Browser** come app client.

    ![Screenshot dei criteri di accesso condizionale - Selezione delle app client](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > Per specificare le app native (app non browser) che possono accedere alle applicazioni cloud, è anche possibile selezionare **App per dispositivi mobili e client desktop**.

9. Nella sezione **Assegnazioni** selezionare **Utenti e gruppi** e quindi scegliere gli utenti o i gruppi a cui si vogliono assegnare i criteri.

10. Nella sezione **Assegnazioni** selezionare **App cloud** per scegliere le app da proteggere con questi criteri.

Dopo aver configurato i criteri, agli utenti verrà imposto l'uso di Microsoft Edge per accedere alle app Web connesse ad Azure AD protette con i criteri. Se gli utenti cercano di usare un browser non gestito in questo scenario, verrà visualizzato un messaggio che segnala che devono usare Microsoft Edge.

> [!TIP]
> L'accesso condizionale è una tecnologia di Azure AD. Il nodo di accesso condizionale accessibile da Intune è lo stesso nodo a cui si accede da Azure AD.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Accesso Single Sign-On alle app Web connesse ad Azure AD in browser protetti da criteri

Microsoft Edge in iOS e Android può usare l'accesso Single Sign-On (SSO) per tutte le app Web (SaaS e locali) connesse ad Azure AD. L'accesso SSO consente agli utenti di accedere alle app Web connesse ad Azure AD tramite Microsoft Edge senza dover immettere nuovamente le proprie credenziali.

Per usare l'accesso SSO, è necessario che il dispositivo sia registrato tramite l'app Microsoft Authenticator per i dispositivi iOS oppure nel Portale aziendale Intune in Android. Quando gli utenti hanno a disposizione una di queste configurazioni, viene loro richiesto di registrare il dispositivo quando accedono a un'app Web connessa ad Azure AD in un browser protetto da criteri. (Ciò vale solo se il dispositivo non è già stato registrato.) Dopo aver registrato il dispositivo con l'account gestito da Intune dell'utente, per l'account viene abilitato l'accesso SSO per le app Web connesse ad Azure AD.

> [!NOTE]
> La registrazione del dispositivo è una semplice procedura di accesso al servizio Azure AD. Non richiede la registrazione del dispositivo completa e non implica la concessione di privilegi aggiuntivi al personale IT per il dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Creare una configurazione per l'app dei browser protetti

Per creare la configurazione dell'app per Microsoft Edge:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Criteri di configurazione dell'app** > **Aggiungi**.
3. Nel riquadro **Aggiungi i criteri di configurazione** immettere **Nome** e **Descrizione** facoltativa per le impostazioni di configurazione dell'app.
4. Per **Tipo di registrazione del dispositivo** scegliere **App gestite**.
5. Scegliere **Selezionare l'app necessaria**. Nel riquadro **App di destinazione** scegliere quindi **Managed Browser** o **Edge** per iOS, Android o per entrambi.
6. Selezionare **OK** per tornare al riquadro **Aggiungi i criteri di configurazione**.
7. Selezionare **Impostazioni di configurazione**. Nel riquadro **Configurazione** definire le coppie di chiavi e valori per specificare le configurazioni per Microsoft Edge. Vedere le sezioni più avanti in questo articolo per informazioni sulle varie coppie di chiavi e valori che è possibile definire.

    > [!NOTE]
    > Microsoft Edge usa le stesse coppie chiave-valore di Managed Browser. Perché i criteri di configurazione app in Android abbiano effetto, Microsoft Edge deve essere configurato con criteri di protezione delle app.

8. Al termine, selezionare **OK**.
9. Nel pannello **Aggiungi i criteri di configurazione** scegliere **Aggiungi**.<br>
    La nuova configurazione viene creata e visualizzata nel riquadro **Configurazione dell'app**.

## <a name="assign-the-configuration-settings-you-created"></a>Assegnare le impostazioni di configurazione create 

Le impostazioni vengono assegnate a gruppi di utenti in Azure AD. Se tale utente ha installato l'app dei browser protetti di destinazione, questa verrà gestita dalle impostazioni specificate.

1. Nel riquadro **App** del dashboard di gestione delle applicazioni per dispositivi mobili di Intune selezionare **Criteri di configurazione dell'app**.
2. Nell'elenco di configurazioni di app selezionare quella che si vuole assegnare.
3. Nel riquadro successivo selezionare **Assegnazioni**.
4. Nel riquadro **Assegnazioni** selezionare il gruppo di Azure AD a cui si vuole assegnare la configurazione dell'app e quindi selezionare **OK**.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Indirizzare gli utenti a Microsoft Edge invece che a Intune Managed Browser 

È possibile usare sia Intune Managed Browser che Microsoft Edge come browser protetti dai criteri. Per garantire che gli utenti vengano reindirizzati in modo da usare l'app browser corretta, assegnare a tutte le app gestite da Intune (ad esempio Outlook, OneDrive e SharePoint) l'impostazione di configurazione seguente:

|    Chiave    |    Valore    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    Il valore `true` indicherà agli utenti di scaricare e usare Microsoft Edge.<br>Il valore `false` consentirà agli utenti di usare Intune Managed Browser.    |

Se questo valore di configurazione dell'app **non** viene impostato, il browser usato per aprire i collegamenti aziendali verrà definito dalla logica seguente.

In Android:
- Se un utente ha scaricato nel dispositivo sia Intune Managed Browser che Microsoft Edge, viene avviato Intune Managed Browser. 
- Microsoft Edge viene avviato solo se è l'unico browser scaricato nel dispositivo e vi sono assegnati criteri di Intune.
- Managed Browser viene avviato solo se è l'unico browser installato nel dispositivo e vi sono assegnati criteri di Intune.

In iOS, per le app in cui è integrato Intune SDK per iOS versione 9.0.9+:
- Se nel dispositivo sono presenti sia Intune Managed Browser che Microsoft Edge, viene avviato Intune Managed Browser.  
- Microsoft Edge viene avviato solo se è l'unico browser presente nel dispositivo e vi sono assegnati criteri di Intune.
- Managed Browser viene avviato solo se è l'unico browser installato nel dispositivo e vi sono assegnati criteri di Intune.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Configurare le impostazioni di Application Proxy per Microsoft Edge

È possibile usare Microsoft Edge e [Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) in combinazione per consentire agli utenti l'accesso ai siti Intranet nei dispositivi mobili. 

Ecco alcuni esempi degli scenari resi possibili da Azure AD Application Proxy: 

- Un utente sta usando l'app per dispositivi mobili Outlook, protetta da Intune. L'utente fa clic su un collegamento a un sito Intranet in un messaggio di posta elettronica e Microsoft Edge riconosce che tale sito Intranet è stato esposto all'utente tramite Application Proxy. L'utente viene automaticamente indirizzato tramite Application Proxy, per autenticarsi con l'autenticazione a più fattori applicabile e con l'accesso condizionale prima di accedere al sito Intranet. L'utente può così accedere ai siti interni anche da dispositivi mobili e il collegamento in Outlook funziona come previsto.
- Un utente apre Microsoft Edge nel dispositivo iOS o Android. Se Microsoft Edge è protetto con Intune e Application Proxy è abilitato, l'utente può passare a un sito Intranet usando l'URL interno che è abituato a usare. Microsoft Edge riconosce che tale sito Intranet è stato esposto all'utente tramite Application Proxy. L'utente viene automaticamente indirizzato tramite Application Proxy, per eseguire l'autenticazione prima di raggiungere il sito Intranet. 

### <a name="before-you-start"></a>Prima di iniziare

- Configurare le applicazioni interne tramite Azure AD Application Proxy.
  - Per configurare il proxy di applicazione e pubblicare le applicazioni, vedere la [documentazione del programma di installazione](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy).
- All'app Microsoft Edge devono essere assegnati i [criteri di protezione delle app di Intune](app-protection-policy.md).

> [!NOTE]
> Possono essere necessarie fino a 24 ore perché l'aggiornamento dei dati di reindirizzamento del proxy di applicazione sia visibile in Managed Browser e Microsoft Edge.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>Passaggio 1: Abilitare il reindirizzamento automatico a Microsoft Edge da Outlook
Configurare Outlook con criteri di protezione delle app che abilitano l'impostazione **Condividi il contenuto Web con browser gestiti da criteri**.

![Screenshot di Criteri di protezione delle app - Condividi il contenuto Web con browser gestiti da criteri](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>Passaggio 2: Specificare l'impostazione di configurazione dell'app per abilitare Application Proxy
Scegliere come destinazione Microsoft Edge con la coppia chiave/valore seguente per abilitare Application Proxy per Microsoft Edge:

|    Chiave    |    Valore    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

Per altre informazioni su come è possibile usare Microsoft Edge e Azure AD Application Proxy in combinazione per un accesso semplice e protetto alle app Web locali, vedere [Better togher: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Meglio insieme: Intune e Azure Active Directory insieme per migliorare l'accesso utente). Questo post di blog fa riferimento a Intune Managed Browser, ma il contenuto si applica anche a Microsoft Edge.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Configurare un collegamento alla home page per Microsoft Edge

Questa impostazione consente di configurare un collegamento alla home page per Microsoft Edge. Il collegamento alla home page configurato verrà visualizzato come prima icona sotto la barra di ricerca quando l'utente apre una nuova scheda in Microsoft Edge. L'utente non può modificare o eliminare questo collegamento nel contesto gestito. Nel collegamento alla home page viene visualizzato il nome dell'organizzazione per poterlo distinguere. 

Usare la coppia chiave/valore seguente per configurare un collegamento alla home page:

|    Chiave    |    Valore    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    Specificare un URL valido. Come misura di sicurezza, gli URL non corretti vengono bloccati.<br>**Esempio:**  <`https://www.bing.com`>

## <a name="configure-your-organizations-logo-and-brand-color-for-new-tab-pages-in-microsoft-edge"></a>Configurare il logo dell'organizzazione e il colore del marchio per le pagine Nuova scheda in Microsoft Edge

Queste impostazioni consentono di personalizzare la pagina Nuova scheda per Microsoft Edge per visualizzare il logo e il colore del marchio dell'organizzazione come sfondo della pagina.

Per caricare il logo e il colore dell'organizzazione, seguire prima di tutto questa procedura:
- All'interno del portale di Azure passare a Intune-> App client-> Personalizzazione -> Company Identity Branding (Personalizzazione dell'identità aziendale)
- Per impostare il logo del marchio, in "Display" (Visualizza) scegliere "Company Logo only" (Solo logo aziendale). Sono consigliati logo con sfondo trasparente. 
- Per impostare il colore di sfondo del marchio, in "Display" (Visualizza) scegliere "Theme Color" (Colore del tema). Microsoft Edge applica una sfumatura più chiara del colore nella pagina Nuova scheda, che garantisce una maggiore leggibilità della pagina. 

Usare quindi le coppie chiave/valore seguenti per eseguire il pull degli elementi personalizzati dell'organizzazione in Microsoft Edge:

|    Chiave    |    Valore    |
|--------------------------------------------------------------------|------------|
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandLogo    |    True    |
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandColor    |    True    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Configurare segnalibri gestiti per Microsoft Edge

Per semplificare l'accesso, è possibile configurare segnalibri da mettere a disposizione degli utenti quando usano Microsoft Edge. 

Ecco alcune informazioni:

- Questi segnalibri vengono visualizzati dagli utenti solo quando usano la [modalità aziendale](https://docs.microsoft.com/intune/apps/app-configuration-managed-browser#how-to-configure-bookmarks-for-a-protected-browser) di Microsoft Edge. 
- Questi segnalibri non possono essere eliminati o modificati dagli utenti.
- I segnalibri vengono visualizzati nella parte superiore dell'elenco. Eventuali segnalibri creati dagli utenti vengono visualizzati sotto questi segnalibri.
- Se è stato abilitato il reindirizzamento di Application Proxy, è possibile aggiungere le app Web di Application Proxy usando il relativo URL interno o esterno.

Per configurare i segnalibri gestiti, usare la coppia chiave/valore seguente:

|    Chiave    |    Valore    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    Il valore per questa configurazione è un elenco di segnalibri. Ogni segnalibro è costituito da titolo e URL. Separare titolo e URL con il carattere `|`.      Esempio:<br>`Microsoft Bing|https://www.bing.com`<br>Per configurare più segnalibri, separare ogni coppia con il doppio carattere `||`.<p>Esempio:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Visualizzare MyApps nei segnalibri di Microsoft Edge

Per impostazione predefinita, gli utenti visualizzano i siti MyApps configurati per loro in una cartella all'interno dei segnalibri di Microsoft Edge. Il nome della cartella corrisponde a quello dell'organizzazione.

|    Chiave    |    Valore    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True** mostra MyApps nei segnalibri di Microsoft Edge.<p>**False** nasconde MyApps in Microsoft Edge.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Specificare l'elenco dei siti consentiti o bloccati per Microsoft Edge
È possibile usare la configurazione dell'app per definire i siti a cui gli utenti possono accedere quando usano il profilo di lavoro. Se si usa un elenco di siti consentiti, gli utenti possono accedere solo ai siti inseriti in modo esplicito nell'elenco. Se si usa un elenco di siti bloccati, gli utenti possono accedere a tutti i siti esclusi quelli esplicitamente bloccati. Imporre solo un elenco di siti consentiti o uno di siti bloccati e non entrambi. Se vengono applicati entrambi, viene rispettato l'elenco dei siti consentiti.  

Usare le coppie chiave/valore seguenti per configurare un elenco di siti consentiti o bloccati per Microsoft Edge. 

|    Chiave    |    Valore    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Scegliere tra:<p>1. Specificare gli URL consentiti. Sono consentiti solo questi URL e nessun altro sito è accessibile:<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. Specificare gli URL bloccati (tutti gli altri siti sono accessibili):<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    Il valore corrispondente per la chiave è un elenco di URL. Immettere tutti gli URL da consentire o bloccare come singolo valore, separandoli tramite un carattere di barra verticale `|`.<br>**Esempi:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>Formati di URL per gli elenchi dei siti consentiti e bloccati 
È possibile usare diversi formati di URL per creare gli elenchi dei siti consentiti e bloccati. I modelli che è possibile usare sono descritti in dettaglio nella tabella seguente. Di seguito sono indicate alcune note: 
- Assicurarsi che tutte le URL abbiano con prefisso **http** o **https** quando immetterle nell'elenco.
- È possibile usare il carattere jolly (\*) secondo le regole nell'elenco di modelli consentiti seguente.
- Un carattere jolly può corrispondere solamente a un componente intero del nome host (separato da punti) o a parti intere del percorso (separate da barre). Ad esempio, `http://*contoso.com` **non** è supportato.
- È possibile specificare numeri di porta nell'indirizzo. Se non si specifica un numero di porta, i valori usati sono:
  - Porta 80 per http
  - Porta 443 per https
- L'uso di caratteri jolly per il numero di porta **non** è supportato. Ad esempio, `http://www.contoso.com:*` e `http://www.contoso.com:*/` non sono supportati. 

    |    URL    |    Dettagli    |    Corrispondenze    |    Non corrisponde    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    Corrisponde a una singola pagina    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    Corrisponde a una singola pagina    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    Cerca una corrispondenza con tutti gli URL che iniziano con `www.contoso.com`    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    Corrisponde a tutti i sottodomini in `contoso.com`    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`
    |    `http://*contoso.com/*`    |    Corrisponde a tutti i sottodomini che terminano con `contoso.com/`    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    Corrisponde a una singola cartella    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    Corrisponde a una singola pagina, tramite un numero di porta    |    `http://www.contoso.com:80`    |         |
    |    `https://www.contoso.com`    |    Corrisponde a una singola pagina protetta    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    Corrisponde a una singola cartella e a tutte le sottocartelle    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
- Di seguito sono riportati esempi di alcuni input che non è possibile specificare:
  - `*.com`
  - `*.contoso/*`
  - `www.contoso.com/*images`
  - `www.contoso.com/*images*pigs`
  - `www.contoso.com/page*`
  - Indirizzi IP
  - `https://*`
  - `http://*`
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="define-behavior-when-users-try-to-access-a-blocked-site"></a>Definire il comportamento quando gli utenti cercano di accedere a un sito bloccato

Con il modello a doppia identità integrato in Microsoft Edge, è possibile offrire agli utenti finali un'esperienza più flessibile rispetto a quanto possibile con Intune Managed Browser. Quando gli utenti tentano di accedere a un sito bloccato in Microsoft Edge, è possibile richiedere loro di aprire il collegamento nel contesto personale anziché nel contesto aziendale. Ciò consente loro di rimanere protetti, mantenendo al sicuro le risorse aziendali. Ad esempio, se un utente riceve un collegamento a un articolo di notizie tramite Outlook, può aprire il collegamento nel contesto personale o in una scheda InPrivate. Il contesto aziendale non consente l'accesso a siti Web di notizie. Per impostazione predefinita, queste transizioni sono consentite.

Usare la coppia chiave/valore seguente per definire se abilitare o meno queste transizioni:

|    Chiave    |    Valore    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True** consente a Microsoft Edge di effettuare la transizione degli utenti al contesto personale per aprire i siti bloccati.<p>**Block** impedisce a Microsoft Edge di effettuare la transizione degli utenti. Per gli utenti viene semplicemente visualizzato un messaggio che informa che il sito a cui stanno tentando di accedere è bloccato.    |

## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>Usare Microsoft Edge in iOS per accedere ai log delle app gestite 

Gli utenti che hanno installato Microsoft Edge nel dispositivo iOS possono visualizzare lo stato di gestione di tutte le app pubblicate da Microsoft. Possono anche inviare log per la risoluzione dei problemi delle app iOS gestite installate. Ecco come:
1. Aprire Microsoft Edge nel dispositivo iOS.
2. Digitare `about:intunehelp` nella casella dell'indirizzo. 
3. Microsoft Edge viene avviato in modalità di risoluzione dei problemi.

Per un elenco delle impostazioni archiviate nei log delle app, vedere [Esaminare i log di protezione delle app nel Managed Browser](app-protection-policy-settings-log.md).

Per informazioni su come visualizzare i log nei dispositivi Android, vedere [Inviare i log al supporto tecnico dell'azienda tramite posta elettronica](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android). 

## <a name="security-and-privacy-for-microsoft-edge"></a>Sicurezza e privacy per Microsoft Edge

Di seguito sono riportate alcune altre considerazioni su sicurezza e privacy per Microsoft Edge:

- Microsoft Edge non utilizza le impostazioni che gli utenti definiscono per il browser nativo nei propri dispositivi, perché Microsoft Edge non può accedere a tali impostazioni.
- È possibile configurare l'opzione **Richiedi PIN semplice per l'accesso** oppure **Richiedi credenziali aziendali per l'accesso** nei criteri di protezione delle app associati a Microsoft Edge. Se un utente seleziona il collegamento alla Guida nella pagina di autenticazione, può esplorare tutti i siti Internet, indipendentemente dal fatto che siano stati aggiunti a un elenco di siti bloccati nei criteri.
- Microsoft Edge può bloccare l'accesso ai siti solo quando vi si accede direttamente. Non blocca l'accesso quando gli utenti usano servizi intermedi (ad esempio, un servizio di traduzione) per accedere al sito.
- Per consentire l'autenticazione e l'accesso alla documentazione di Intune, il sito * **.microsoft.com** non è interessato dalle impostazioni degli elenchi di elementi consentiti o bloccati. È sempre consentito.
- Gli utenti possono disattivare la raccolta dei dati. Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso di Managed Browser per migliorare prodotti e servizi Microsoft. Gli utenti possono disattivare la raccolta dei dati usando l'impostazione **Dati di utilizzo** nei propri dispositivi. L'utente non ha alcun controllo sulla raccolta di tali dati. Nei dispositivi iOS i siti Web visitati dagli utenti che hanno un certificato scaduto o non attendibile non possono essere aperti.

## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md) 
