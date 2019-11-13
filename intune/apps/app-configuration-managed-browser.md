---
title: Gestire l'accesso Web aziendale con un browser protetto da criteri
titleSuffix: Microsoft Intune
description: Usare un browser protetto da criteri assegnato da Intune per gestire l'esplorazione Web e il trasferimento dei dati Web aziendali.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: a3fab0b14f8ed68d13021a0e141d5997532df2ec
ms.sourcegitcommit: ae6f2e7812e7fd36f2393b8f4b6cd8de63777b2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2019
ms.locfileid: "73592084"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Gestire l'accesso Web usando un browser protetto con criteri di Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'uso di un browser protetto dai criteri di Intune (Microsoft Edge o Intune Managed Browser) garantisce che l'accesso ai siti Web aziendali venga sempre eseguito con misure di sicurezza applicate.  Quando configurati con Intune, i browser protetti possono sfruttare quanto segue:

- Criteri di protezione delle applicazioni
- Accesso condizionale
- Accesso Single Sign-On
- Impostazioni di configurazione dell'applicazione
- Integrazione del proxy di applicazione di Azure

## <a name="microsoft-edge-support"></a>Supporto di Microsoft Edge

È possibile usare Microsoft Edge per gli scenari aziendali nei dispositivi iOS e Android. Microsoft Edge supporta tutti gli stessi scenari di gestione di Intune Managed Browser con l'aggiunta di miglioramenti all'esperienza utente finale. Le funzionalità aziendali di Microsoft Edge abilitate dai criteri di Intune includono:

- **Doppia identità**: gli utenti possono aggiungere sia un account aziendale che un account personale per l'esplorazione. Le due identità sono completamente separate, in modo analogo all'architettura e all'esperienza utente di Office 365 e Outlook. Gli amministratori di Intune potranno impostare i criteri desiderati per un'esperienza di esplorazione protetta nell'account aziendale. 
- **Integrazione dei criteri di protezione delle app di Intune**: ora gli amministratori possono applicare i criteri di protezione delle app a Microsoft Edge, tra cui controllare le operazioni Taglia, Copia e Incolla, impedire le acquisizioni di schermata e assicurare che i collegamenti selezionati dagli utenti si aprano solo in altre app gestite.
- **Integrazione con il proxy di applicazione di Azure**: gli amministratori possono controllare l'accesso alle app SaaS e alle app Web, per assicurare che le app basate su browser vengano eseguite solo nel browser Microsoft Edge sicuro, sia che gli utenti finali si connettano dalla rete aziendale o da Internet. 
- **Collegamenti a Preferiti gestiti e alla home page**: per facilitare l'accesso, gli amministratori possono impostare gli URL in modo che vengano visualizzati nei preferiti quando gli utenti finali si trovano nel proprio contesto aziendale. Possono impostare un collegamento alla home page che viene visualizzato come collegamento principale quando un utente aziendale apre una nuova pagina o una nuova scheda in Microsoft Edge.

I criteri di protezione di Microsoft Intune per Microsoft Edge contribuiscono a proteggere i dati e le risorse dell'organizzazione. Con Microsoft Edge protetto da Intune le risorse aziendali sono protette non solo all'interno delle app installate in modo nativo, ma anche quando vi si accede tramite il Web browser.

## <a name="getting-started"></a>Guida introduttiva

Microsoft Edge e Intune Managed Browser sono le app Web browser che amministratori e utenti finali possono scaricare dagli app store pubblici per l'uso nell'organizzazione. 

Requisiti del sistema operativo per i criteri di browser:
- Android 4 e versioni successive o
- iOS 8.0 e versioni successive.

Le versioni precedenti di Android e iOS saranno in grado di continuare a usare Managed Browser, ma non sarà possibile installare nuove versioni dell'app e le funzionalità dell'app potrebbero non essere tutte disponibili. Si consiglia di eseguire l'aggiornamento di questi dispositivi a una versione supportata del sistema operativo.

>[!NOTE]
>Managed Browser non supporta il protocollo di crittografia di Secure Sockets Layer versione 3 (SSLv3).


## <a name="application-protection-policies-for-protected-browsers"></a>Criteri di protezione delle applicazioni per i browser protetti

Poiché Microsoft Edge e Managed Browser includono l'integrazione con Intune SDK, è anche possibile applicare i criteri di protezione delle app, inclusi i seguenti:
- Controllare l'uso di taglia, copia e incolla.
- Impedire l'acquisizione di schermate.
- Garantire che i collegamenti aziendali vengano aperti solo all'interno di app e browser gestiti.

Per altre informazioni dettagliate, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)

È possibile applicare queste impostazioni ai dispositivi seguenti:

- Dispositivi registrati in Intune
- Dispositivi registrati in altro prodotto MDM
- Dispositivi non gestiti

>[!NOTE]
>Se gli utenti installano Managed Browser dallo store di app e Intune non lo gestisce, è possibile usare questa app come un Web browser semplice con il supporto di Single Sign-On tramite il sito Microsoft MyApps. Gli utenti vengono indirizzati direttamente al sito MyApps, in cui sono visualizzate tutte le applicazioni SaaS di cui è stato eseguito il provisioning.
Fino a quando Managed Browser o Microsoft Edge non sono gestiti da Intune, non potranno accedere ai dati da altre applicazioni gestite da Intune. 


## <a name="conditional-access-for-protected-browsers"></a>Accesso condizionale per i browser protetti

Managed Browser è ora un'app client approvata per l'accesso condizionale. Ciò significa che è possibile limitare l'accesso del browser per dispositivi mobili alle app Web connesse ad Azure AD in cui gli utenti possono usare solo Managed Browser, bloccando l'accesso da eventuali altri browser non protetti, ad esempio Safari o Chrome. Questa protezione può essere applicata a risorse di Azure come Exchange Online e SharePoint Online, l'interfaccia di amministrazione di Microsoft 365 e persino i siti locali esposti agli utenti esterni tramite [Azure AD Application Proxy](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). 

Per fare in modo che le app Web connesse ad Azure AD usino Intune Managed Browser nelle piattaforme mobili, è possibile creare un criterio di accesso condizionale che richiede applicazioni client approvate. 

> [!TIP]  
> L'accesso condizionale è una tecnologia di Azure Active Directory (Azure AD). Il nodo di accesso condizionale accessibile da *Intune* è lo stesso nodo accessibile da *Azure AD*.  


1. Nel portale di Intune selezionare **Accesso condizionale** > **Nuovi criteri**. 
2. Quindi selezionare **Concedi** dalla sezione **Controlli di accesso** del pannello. 
3. Fare clic su **Richiedi app client approvata**. 
4. Fare clic su **Seleziona** nel pannello **Concedi**. Questi criteri devono essere assegnati alle app cloud che si vuole rendere accessibili solo per l'app Intune Managed Browser.

    ![Azure AD - Criteri di accesso condizionale di Managed Browser](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)

5. Nella sezione **Assegnazioni** selezionare **Condizioni** > **App client**. Viene visualizzato il pannello **App client**.
6. Fare clic su **Sì** in **Configura** per applicare i criteri ad app client specifiche.
7. Verificare che sia selezionata l'opzione **Browser** come app client.

    ![Azure AD - Managed Browser - Selezionare le app client](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > Per specificare le app native (app non browser) che possono accedere alle applicazioni cloud, è anche possibile selezionare **App per dispositivi mobili e client desktop**.

8. Nella sezione **Assegnazioni** selezionare **Utenti e gruppi** e quindi scegliere gli utenti o i gruppi a cui si vuole assegnare i criteri. 

    > [!NOTE]
    > Gli utenti devono inoltre essere destinatari dei criteri di Protezione app di Intune per ricevere i criteri di configurazione dell'app. Per altre informazioni sulla creazione dei criteri di Protezione app di Intune, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)

9. Nella sezione **Assegnazioni** selezionare **App cloud** per scegliere le app da proteggere con questi criteri.

Dopo aver configurato i criteri, agli utenti verrà imposto l'uso di Intune Managed Browser per accedere alle app Web connesse ad Azure AD protette con i criteri. Se tentano di usare un browser non gestito in questo scenario, agli utenti viene visualizzata una nota che comunica che è necessario usare Intune Managed Browser.

Managed Browser non supporta i criteri di accesso condizionale classici. Per altre informazioni, vedere [Migrare i criteri classici nel portale di Azure](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration).

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>Accesso Single Sign-on alle app Web connesse ad Azure AD in browser protetti da criteri

Microsoft Edge e Intune Managed Browser in iOS e Android possono usare l'accesso SSO per tutte le app Web (SaaS e locali) connesse ad Azure AD. Quando è presente l'app Microsoft Authenticator in iOS oppure l'app Portale aziendale Intune in Android, gli utenti di un browser protetto da criteri potranno accedere alle app Web connesse ad Azure AD senza dover reimmettere le credenziali.

Per usare l'accesso SSO, è necessario che il dispositivo sia registrato dall'app Microsoft Authenticator in iOS o dall'app Portale aziendale Intune in Android. Se il dispositivo non è già stato registrato da un'altra applicazione, agli utenti con l'app Authenticator o Portale aziendale Intune verrà richiesto di registrare il dispositivo quando accedono a un'app Web connessa ad Azure AD in un browser protetto da criteri. Dopo aver registrato il dispositivo con l'account gestito da Intune, per l'account viene abilitato l'accesso SSO per le app Web connesse ad Azure AD. 

> [!NOTE]
> La registrazione del dispositivo è una semplice procedura di accesso al servizio Azure AD. Non richiede la registrazione del dispositivo completa e non implica la concessione di privilegi aggiuntivi all'IT per il dispositivo.

## <a name="create-a-protected-browser-app-configuration"></a>Creare una configurazione per l'app dei browser protetti

>[!IMPORTANT]
>Per applicare le configurazioni dell'app, è necessario che il browser protetto dell'utente o un'altra app nel dispositivo sia già gestito dai [criteri di protezione delle app di Intune]( ../app-protection-policy.md).

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel pannello **App mobili** dell'elenco di gestione scegliere **Criteri di configurazione dell'app**.
4. Nel pannello **Criteri di configurazione dell'app** scegliere **Aggiungi**.
5. Nel pannello **Aggiungi i criteri di configurazione** immettere **Nome** e **Descrizione** facoltativa per le impostazioni di configurazione dell'app.
6. Per **Tipo di registrazione del dispositivo** scegliere **App gestite**.
7. Scegliere **Selezionare l'app necessaria** e quindi nel pannello **App di destinazione** scegliere **Managed Browser** e/o **Microsoft Edge** per iOS, per Android o per entrambi.
8. Scegliere **OK** per tornare al pannello **Aggiungi i criteri di configurazione**.
9. Scegliere **Impostazioni di configurazione**. Nel pannello **Configurazione** definire le coppie di chiavi e valori per specificare le configurazioni per Managed Browser. Vedere le sezioni più avanti in questo articolo per informazioni sulle varie coppie di chiavi e valori che è possibile definire.
10. Al termine, scegliere **OK**.
11. Nel pannello **Aggiungi i criteri di configurazione** scegliere **Aggiungi**.
12. La nuova configurazione verrà creata e visualizzata nel pannello **Configurazione dell'app**.


## <a name="assign-the-configuration-settings-you-created"></a>Assegnare le impostazioni di configurazione create

Le impostazioni vengono assegnate a gruppi di utenti di Azure AD. Se tale utente ha installato l'app dei browser protetti di destinazione, questa verrà gestita dalle impostazioni specificate.

1. Nel pannello **App client** del dashboard di gestione delle applicazioni per dispositivi mobili di Intune scegliere **Criteri di configurazione dell'app**.
2. Nell'elenco di configurazioni di app selezionare quella che si vuole assegnare.
3. Nel pannello successivo scegliere **Assegnazioni**.
4. Nel pannello **Assegnazioni** selezionare il gruppo di Azure AD a cui si vuole assegnare la configurazione dell'app e scegliere **OK**.

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>Come impostare Microsoft Edge come browser protetto per l'organizzazione

Questa impostazione consente di indicare se gli utenti verranno indirizzati a Microsoft Edge o a Intune Managed Browser, supponendo che entrambi i browser siano destinatari di criteri di protezione delle app. **Questa impostazione dei criteri di configurazione dell'applicazione deve essere destinata alle app gestite da Intune dalle quali viene aperto il collegamento Web.** 

Se impostata su "True":

- All'apertura dei collegamenti dalle app gestite da Intune destinatarie di questa impostazione, gli utenti verranno indirizzati a Microsoft Edge. 
- Se l'utente non ha ancora l'app, verrà richiesto di scaricare Microsoft Edge dallo Store, anche se è stato scaricato Intune Managed Browser.

Se impostata su "False":

- Se l'utente ha scaricato **entrambi** i browser, ovvero Managed Browser e Microsoft Edge, verrà avviato Managed Browser. 
- Se l'utente ha scaricato **uno** dei browser, ovvero Managed Browser **o** Microsoft Edge, verrà avviato quello scaricato. 
- Se l'utente non ha scaricato nessuna delle due app browser, verrà richiesto di scaricare Managed Browser.

Usare la procedura precedente per creare una configurazione dell'app Microsoft Edge. Alla selezione delle **Impostazioni di configurazione** nel pannello **Configurazione** (passaggio 9), specificare la coppia chiave-valore seguente:

| Chiave                              |  Valore   |
|----------------------------------|----------|
| **com.microsoft.intune.useEdge** | **true** |

> [!NOTE]
> Nei criteri di protezione delle app che gestiscono Microsoft Edge e le app associate specificate nella configurazione dell'app, verificare che siano state configurate le impostazioni dei criteri di protezione dati seguenti:
> - Invia i dati dell'organizzazione ad altre app: **App gestite da criteri**
> - Limita il trasferimento di contenuto Web con altre app: **Browser gestiti da criteri**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>Come configurare le impostazioni del proxy di applicazione per i browser protetti

Microsoft Edge, Intune Managed Browser e [Azure AD Application Proxy]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) possono essere usati insieme per supportare gli scenari seguenti per gli utenti di dispositivi iOS e Android:

- Un utente scarica e accede all'app Microsoft Outlook. I criteri di protezione dell'app di Intune vengono applicati automaticamente. Crittografano i dati salvati e impediscono all'utente il trasferimento di file aziendali ad app non gestite o a percorsi nel dispositivo. Quando l'utente fa quindi clic su un collegamento a un sito intranet in Outlook, è possibile specificare che il collegamento venga aperto in un'applicazione dei browser protetti, anziché in un altro browser. Il browser protetto riconosce che tale sito intranet è stato esposto all'utente tramite il proxy di applicazione. L'utente viene indirizzato automaticamente tramite il proxy di applicazione, per l'autenticazione con il sistema di autenticazione a più fattori applicabile, e l'accesso condizionale prima di raggiungere il sito Intranet. Questo sito, che in precedenza non poteva essere trovato quando l'utente era remoto, è ora accessibile e il collegamento in Outlook funziona come previsto.
- Un utente remoto apre l'applicazione dei browser protetti e passa a un sito intranet tramite l'URL interno. Il browser protetto riconosce che tale sito intranet è stato esposto all'utente tramite il proxy di applicazione. L'utente viene indirizzato automaticamente tramite il proxy di applicazione, per l'autenticazione con il sistema di autenticazione a più fattori applicabile, e l'accesso condizionale prima di raggiungere il sito Intranet. Questo sito, che in precedenza non poteva essere trovato quando l'utente era remoto, è ora accessibile.

### <a name="before-you-start"></a>Prima di iniziare

- Configurare le applicazioni interne tramite il proxy di applicazione di Azure AD.
  - Per configurare il proxy di applicazione e pubblicare le applicazioni, vedere la [documentazione del programma di installazione](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy). 
  - [Gli utenti devono essere assegnati](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing) all'applicazione aziendale per la quale deve avvenire il reindirizzamento. È necessario eseguire questa operazione anche se l'applicazione è impostata sulla modalità Passthrough per la preautenticazione e se il requisito di assegnazione utente è stato disattivato nelle impostazioni del proxy di applicazione.
- È necessario usare almeno la versione 1.2.0 dell'app Managed Browser.
- Gli utenti dell'app Managed Browser o Microsoft Edge hanno un [criterio di protezione delle app di Intune](app-protection-policy.md) assegnato all'app.

    > [!NOTE]
    > Possono essere necessarie fino a 24 ore perché l'aggiornamento dei dati di reindirizzamento del proxy di applicazione sia visibile in Managed Browser e Microsoft Edge.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>Passaggio 1: Abilitare il reindirizzamento automatico a un browser protetto da Outlook
Outlook deve essere configurato con i criteri di protezione di app che consentono l'impostazione **Limita il contenuto Web per la visualizzazione in Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>Passaggio 2: Assegnare i criteri di configurazione delle app assegnati per il browser protetto
Questa procedura configura l'app Managed Browser o Microsoft Edge per l'uso del reindirizzamento proxy dell'app. 

Aprire la scheda **Edge** nelle impostazioni di configurazione per i criteri e selezionare **Abilita** per il valore di reindirizzamento del proxy di applicazione. L'abilitazione di questa impostazione consentirà agli utenti di accedere ai collegamenti aziendali e alle app Web locali pubblicate tramite il proxy di applicazione di Azure.

Per altre informazioni su come Managed Browser, Microsoft Edge e Azure AD Application Proxy possono essere usate insieme per un accesso semplice e protetto alle app Web locali, vedere il post del blog Enterprise Mobility + Security [Better together: Intune and Azure Active Directory team up to improve user access](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access) (Meglio insieme: Intune e Azure Active Directory insieme per migliorare l'accesso utente).

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>Come configurare la home page per un browser protetto

Questa impostazione consente di configurare la home page visualizzata agli utenti quando viene avviato un browser protetto o viene creata una nuova scheda. 
- Questa impostazione consentirà di visualizzare la pagina Web in Managed Browser.  Microsoft Edge visualizzerà invece un collegamento alla home page.
- Il collegamento alla home page viene visualizzato come icona sotto il controllo di ricerca.  Non può essere modificata o eliminata.
- Il collegamento alla home page visualizzerà il nome dell'azienda per poterlo distinguere.  Verrà sempre visualizzato come la prima icona.

Usando la procedura per creare una configurazione per l'app Managed Browser o Microsoft Edge, specificare la coppia di chiave-valore seguente:

|                                Chiave                                |                                                           Valore                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | Specificare un URL valido. Come misura di sicurezza, gli URL non corretti vengono bloccati.<br>Esempio: `https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>Come configurare i segnalibri per un browser protetto

Questa impostazione consente di configurare un set di segnalibri disponibili per gli utenti di Microsoft Edge o Managed Browser.

- Questi segnalibri non possono essere eliminati o modificati dagli utenti
- I segnalibri vengono visualizzati nella parte superiore dell'elenco. Eventuali segnalibri creati dagli utenti vengono visualizzati sotto questi segnalibri.
- Se è stato abilitato il reindirizzamento di proxy app, è possibile aggiungere le app Web di proxy app usando il relativo URL interno o esterno.

Usando la procedura per creare una configurazione per l'app Managed Browser o Microsoft Edge, specificare la coppia di chiave-valore seguente:

|                                Chiave                                 |                                                                                                                                                                                                                                                         Valore                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | Il valore per questa configurazione è un elenco di segnalibri. Ogni segnalibro consiste di un titolo del segnalibro e di un URL. Separare il titolo e l'URL con il carattere <strong>&#124;</strong>.<br><br>Esempio:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>Per configurare più segnalibri, separarli con due caratteri, ovvero <strong>&#124;&#124;</strong><br><br>Esempio:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>Come specificare gli URL consentiti e bloccati per un browser protetto

Usando la procedura per creare una configurazione per l'app Managed Browser o Microsoft Edge, specificare la coppia di chiave-valore seguente:

|Chiave|Valore|
|-|-|
|Scegliere tra:<br><ul><li>Specificare gli URL consentiti. Sono consentiti solo questi URL e nessun altro sito è accessibile:<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>Specificare gli URL bloccati (tutti gli altri siti sono accessibili):<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|Il valore corrispondente per la chiave è un elenco di URL. Tutti gli URL da consentire o bloccare vengono immessi come valore singolo, separati da un carattere barra verticale **&#124;** .<br><br>Esempi:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>Non specificare entrambe le chiavi. Se entrambe le chiavi sono destinate allo stesso utente, viene usata la chiave consentita, essendo l'opzione più restrittiva.
>Assicurarsi inoltre di non bloccare pagine importanti come i siti Web della società.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Formato dell'URL per URL consentite e bloccate
Usare le informazioni seguenti per saperne di più sui formati e i caratteri jolly consentiti che possono essere usati quando si specificano gli URL negli elenchi Consenti e Blocca:

- È possibile usare il carattere jolly ( **&#42;** ) secondo le regole dell'elenco seguente di modelli consentiti:

- Assicurarsi che tutte le URL abbiano con prefisso **http** o **https** quando immetterle nell'elenco.

- È possibile specificare numeri di porta nell'indirizzo. Se non si specifica un numero di porta, i valori usati sono:

  - Porta 80 per http

  - Porta 443 per https

  Non è possibile usare i caratteri jolly per il numero di porta. Ad esempio, `http://www.contoso.com:;` e `http://www.contoso.com: /;` non sono supportati.

- Per altre informazioni sui modelli consentiti che è possibile usare quando si specificano gli URL, vedere la tabella seguente:

|                  URL                  |                     Dettagli                      |                                                Corrispondenze                                                |                                Non corrisponde                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              Corrisponde a una singola pagina               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              Corrisponde a una singola pagina               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | Cerca una corrispondenza con tutti gli URL che iniziano con `www.contoso.com` |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     Cerca una corrispondenza con tutti i sottodomini in contoso.com     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             Corrisponde a una singola cartella              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  Cerca una corrispondenza con una singola pagina usando un numero di porta   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          Corrisponde a una singola pagina protetta           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    Corrisponde a una singola cartella e a tutte le sottocartelle    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- Di seguito sono riportati esempi di alcuni input che non è possibile specificare:

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - Indirizzi IP

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>Transizioni temporanee da account aziendali ad account personali

L'elemento fondamentale dell'esperienza Enterprise per dispositivi mobili di Microsoft Edge è il modello a doppia identità. Microsoft Edge supporta infatti identità aziendali e personali. Analogamente alle app di Office 365 e Outlook, questo modello a doppia identità consente agli utenti finali di usare Microsoft Edge per tutte le esigenze di esplorazione e di passare facilmente da un'esperienza all'altra in base ai criteri di contenuto definiti dall'amministratore. L'esplorazione nel contesto personale è completamente indipendente e le informazioni aziendali vengono mantenute totalmente separate nel contesto aziendale all'interno di Microsoft Edge. 

Uno dei vantaggi di questo modello è la possibilità per gli utenti di aprire, nel proprio contesto personale, un collegamento a un sito non consentito dall'organizzazione, ad esempio un articolo di giornale o altro. Il contesto personale viene infatti mantenuto totalmente separato dal contesto aziendale. Queste transizioni temporanee sono abilitate per impostazione predefinita. 

Usando la procedura per creare una configurazione per l'app Managed Browser o Microsoft Edge, specificare la coppia di chiave-valore seguente:

| Chiave                                                                | Valore                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock** | **False** blocca la possibilità di eseguire queste transizioni temporanee |

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>Come accedere a log di app gestite tramite Managed Browser in iOS

Gli utenti che hanno installato Managed Browser nel dispositivo iOS possono visualizzare lo stato di gestione di tutte le app pubblicate da Microsoft. Possono anche inviare log per la risoluzione dei problemi delle app iOS gestite installate.

1. Aprire **Impostazioni** in iOS.
2. Selezionare le impostazioni dell'applicazione **Managed Browser**.
3. Attivare **Abilita la diagnostica di Intune** per impostare la modalità di risoluzione dei problemi.
4. Aprire **Managed Browser**. Fare clic su **Visualizza lo stato dell'app Intune** per controllare le impostazioni dei singoli criteri dell'applicazione.
5. Fare clic su **Attività iniziali** e quindi su **Condividi i log** o su **Invia i log a Microsoft** per inviare i log di risoluzione dei problemi all'amministratore IT o a Microsoft.

È anche possibile aprire Managed Browser in modalità di risoluzione dei problemi dall'interno dell'app.

1. Aprire Managed Browser.
2. Digitare `about:intunehelp` nella casella dell'indirizzo.
Managed Browser viene avviato in modalità di risoluzione dei problemi.

Per un elenco delle impostazioni archiviate nei log delle app, vedere [Esaminare i log di protezione delle app nel Managed Browser](app-protection-policy-settings-log.md).

## <a name="security-and-privacy-for-the-managed-browser"></a>Sicurezza e privacy per Managed Browser

- Manager Browser non usa le impostazioni create dagli utenti per il browser predefinito nei dispositivi. Managed Browser non può accedere a queste impostazioni.

- Se si configura l'opzione **Richiedi PIN semplice per l'accesso** o **Richiedi credenziali aziendali per l'accesso** nei criteri di protezione dell'app associati a Managed Browser e si seleziona il collegamento alla Guida nella pagina di autenticazione, è possibile esplorare tutti i siti Internet, anche quelli aggiunti a un elenco Blocca nei criteri.

- Managed Browser può bloccare l'accesso ai siti solo quando vi si accede direttamente. Non blocca l'accesso quando i servizi intermedi (ad esempio, un servizio di traduzione) vengono usati per accedere al sito.

- Per consentire l'autenticazione e accedere alla documentazione di Intune, il sito **&#42;.microsoft.com** è esente dalle impostazioni degli elenchi Blocca o Consenti, perché è sempre consentito.

### <a name="turn-off-usage-data"></a>Disattivare la raccolta dati
Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso di Managed Browser per migliorare prodotti e servizi Microsoft. Gli utenti possono disattivare la raccolta dei dati usando l'impostazione **Dati di utilizzo** nei propri dispositivi. L'utente non ha alcun controllo sulla raccolta di tali dati.

- Nei dispositivi iOS i siti Web visitati dagli utenti che hanno un certificato scaduto o non attendibile non possono essere aperti.

## <a name="next-steps"></a>Passaggi successivi

- [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md) 
