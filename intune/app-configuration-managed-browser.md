---
title: Gestire l'accesso Web con l'app Managed Browser
titlesuffix: Azure portal
description: Distribuire l'applicazione Managed Browser per limitare l'esplorazione del Web e il trasferimento dei dati Web ad altre app."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7619efc305881f1ad56a7c14e5d92c05fb0c6d77
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="manage-internet-access-using-managed-browser-policies-with-microsoft-intune"></a>Gestire l'accesso a Internet usando criteri di Managed Browser con Microsoft Intune.

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Managed Browser è un'app per l'esplorazione Web che è possibile scaricare dagli store di app pubblici e usarla nell'organizzazione. Quando è configurata con Intune, l'app Managed Browser può essere:
- Usata per accedere ai siti aziendali e alle app SaaS con Single Sign-On tramite il servizio MyApps mantenendo protetti i dati Web.
- Preconfigurata con un elenco di URL e domini per limitare i siti che gli utenti possono visitare nel contesto aziendale.
- Pre-configurata con una home page e i segnalibri specificati.

Poiché questa app include l'integrazione con Intune SDK, è anche possibile applicarle i criteri di protezione delle app, oltre ai seguenti criteri:
- Controllare l'uso di taglia, copia e incolla
- Impedire l'acquisizione di immagini dello schermo
- Assicurarsi che i collegamenti ai contenuti selezionati dagli utenti vengano aperti solo in altre app gestite.

Per altre informazioni dettagliate, vedere [Che cosa sono i criteri di protezione delle app?](/intune/app-protection-policy)

È possibile applicare queste impostazioni ai dispositivi seguenti:

- Dispositivi registrati in Intune
- Dispositivi registrati in altro prodotto MDM
- Dispositivi non gestiti

Se gli utenti installano Managed Browser dallo store di app e Intune non lo gestisce, è possibile usare questa app come un Web browser semplice con il supporto di Single Sign-On tramite il sito Microsoft MyApps. Gli utenti vengono indirizzati direttamente al sito MyApps, in cui sono visualizzate tutte le applicazioni SaaS di cui è stato eseguito il provisioning.
Fino a quando Managed Browser non è gestita da Intune, non sarà in grado di accedere ai dati da altre applicazioni gestite da Intune. 

Managed Browser non supporta il protocollo di crittografia di Secure Sockets Layer versione 3 (SSLv3).

È possibile creare criteri di Managed Browser per i tipi di dispositivo seguenti:

-   Dispositivi che eseguono Android 4 e versioni successive

-   Dispositivi che eseguono iOS 8.0 e versione successiva

>[!IMPORTANT]
>A partire da ottobre 2017, l'app Intune Managed Browser per Android supporta solo i dispositivi che eseguono Android 4.4 e versioni successive. L'app Intune Managed Browser per iOS supporta solo i dispositivi che eseguono iOS 9.0 e versioni successive.
>Le versioni precedenti di Android e iOS saranno in grado di continuare a usare Managed Browser, ma non sarà possibile installare nuove versioni dell'app e le funzionalità dell'app potrebbero non essere tutte disponibili. Si consiglia di eseguire l'aggiornamento di questi dispositivi a una versione supportata del sistema operativo.


Intune Managed Browser supporta l'apertura di contenuti Web di [partner delle applicazioni di Microsoft Intune](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx).

## <a name="create-a-managed-browser-app-configuration"></a>Creare una configurazione per l'app Managed Browser

1.  Accedere al portale Azure.
2.  Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3.  Nel pannello **App mobili** dell'elenco di gestione, scegliere **Criteri di configurazione dell'app**.
4.  Nel pannello **Criteri di configurazione dell'app** scegliere **Aggiungi**.
5.  Nel pannello **Aggiungi la configurazione dell'app** immettere **Nome** e **Descrizione** facoltativa per le impostazioni di configurazione dell'app.
6.  Per **Tipo di registrazione del dispositivo** scegliere **App gestite**.
7.  Scegliere **Selezionare le app richieste** e quindi, nel pannello **App di destinazione**, scegliere **Managed Browser** per iOS, Android o per entrambi.
8.  Scegliere **OK** per tornare al pannello **Aggiungi la configurazione dell'app**.
9.  Scegliere **Impostazioni di configurazione**. Nel pannello **Configurazione** definire le coppie di chiavi e valori per specificare le configurazioni per Managed Browser. Vedere le sezioni più avanti in questo articolo per informazioni sulle varie coppie di chiavi e valori che è possibile definire.
10. Al termine, scegliere **OK**.
11. Nel pannello **Aggiungi la configurazione dell'app** scegliere **Crea**.
12. La nuova configurazione verrà creata e visualizzata nel pannello **Configurazione dell'app**.

>[!IMPORTANT]
>Attualmente, Managed Browser si basa sulla registrazione automatica. Per applicare le configurazioni dell'app, è necessario che un'altra applicazione nel dispositivo venga già gestita dai criteri di protezione delle app di Intune.

## <a name="assign-the-configuration-settings-you-created"></a>Assegnare le impostazioni di configurazione create

Le impostazioni vengono assegnate a gruppi di utenti di Azure AD. Se tale utente ha installato l'app Managed Browser, questa verrà gestita dalle impostazioni specificate.

1. Nel pannello **Impostazioni** del dashboard di gestione delle applicazioni per dispositivi mobili di Intune scegliere **Configurazione dell'app**.
2. Nell'elenco di configurazioni di app selezionare quella che si vuole assegnare.
3. Nel pannello successivo scegliere **Gruppi di utenti**.
4. Nel pannello **Gruppi di utenti** selezionare il gruppo di Azure AD a cui si vuole assegnare la configurazione dell'app e quindi scegliere **OK**.


## <a name="how-to-configure-application-proxy-settings-for-the-managed-browser"></a>Come configurare le impostazioni proxy di applicazione per Managed Browser

Intune Managed Browser e il [proxy di applicazione Azure AD]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) possono essere usati insieme per supportare gli scenari seguenti per gli utenti di dispositivi iOS e Android:

- Un utente scarica e accede all'app Microsoft Outlook. I criteri di protezione dell'app di Intune vengono applicati automaticamente. Crittografano i dati salvati e impediscono all'utente il trasferimento di file aziendali ad app non gestite o a percorsi nel dispositivo. Quando l'utente fa quindi clic su un collegamento a un sito intranet in Outlook, è possibile specificare che il collegamento venga aperto nell'app Managed Browser, anziché in un altro browser. Managed Browser riconosce che tale sito intranet è stato esposto all'utente tramite il proxy di applicazione. L'utente viene automaticamente indirizzato tramite il proxy di applicazione ad autenticarsi con un'autenticazione applicabile a più fattori e con un accesso condizionale, prima di aprire il sito intranet. Questo sito, che in precedenza non poteva essere trovato quando l'utente era remoto, è ora accessibile e il collegamento in Outlook funziona come previsto.
- Un utente remoto apre l'app Managed Browser e passa a un sito intranet tramite l'URL interno. Managed Browser riconosce che tale sito intranet è stato esposto all'utente tramite il proxy di applicazione. L'utente viene automaticamente indirizzato tramite il proxy di applicazione ad autenticarsi con un'autenticazione applicabile a più fattori e con un accesso condizionale, prima di aprire il sito intranet. Questo sito, che in precedenza non poteva essere trovato quando l'utente era remoto, è ora accessibile.

### <a name="before-you-start"></a>Prima di iniziare

- Configurare le applicazioni interne tramite il proxy di applicazione di Azure AD.
    - Per configurare il proxy di applicazione e pubblicare le applicazioni, vedere la [documentazione del programma di installazione]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started#how-to-get-started). 
- È necessario usare almeno la versione 1.2.0 dell'app Managed Browser.
- Gli utenti dell'app Managed Browser hanno i [criteri di protezione delle app di Intune]( app-protection-policy.md) assegnati all'app.
Nota: possono essere necessarie fino a 24 ore perché l'aggiornamento dei dati di reindirizzamento del proxy dell'applicazione sia visibile in Managed Browser.

#### <a name="step-1-enable-automatic-redirection-to-the-managed-browser-from-outlook"></a>Passaggio 1: abilitare il reindirizzamento automatico a Managed Browser da Outlook
Outlook deve essere configurato con i criteri di protezione di app che consentono l'impostazione **Limita il contenuto Web per la visualizzazione in Managed Browser**.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-managed-browser"></a>Passaggio 2: assegnare i criteri di configurazione dell'app assegnati per Managed Browser.
Questa procedura configura l'app Managed Browser per usare il reindirizzamento proxy dell'app. Usando la procedura per creare una configurazione per l'app Managed Browser, specificare la coppia di chiave e valore seguente:

|||
|-|-|
|Chiave|Valore|
|**com.microsoft.intune.mam.managedbrowser.AppProxyRedirection**|**true**|


## <a name="how-to-configure-the-homepage-for-the-managed-browser"></a>Come configurare la home page per Managed Browser

Questa impostazione consente di configurare la home page visualizzata agli utenti quando viene avviato Managed Browser o viene creata una nuova scheda. Usando la procedura per creare una configurazione per l'app Managed Browser, specificare la coppia di chiave e valore seguente:

|||
|-|-|
|Chiave|Valore|
|**com.microsoft.intune.mam.managedbrowser.homepage**|Specificare un URL valido. Come misura di sicurezza, gli URL non corretti vengono bloccati.<br>Esempio: **https://www.bing.com**|


## <a name="how-to-configure-bookmarks-for-the-managed-browser"></a>Come configurare i segnalibri per Managed Browser

Questa impostazione consente di configurare un set di segnalibri disponibili per gli utenti di Managed Browser.

- Questi segnalibri non possono essere eliminati o modificati dagli utenti
- I segnalibri vengono visualizzati nella parte superiore dell'elenco. Eventuali segnalibri creati dagli utenti vengono visualizzati sotto questi segnalibri.
- Se è stato abilitato il reindirizzamento di proxy app, è possibile aggiungere le app Web di proxy app usando il relativo URL interno o esterno.

Usando la procedura per creare una configurazione per l'app Managed Browser, specificare la coppia di chiave e valore seguente:

|||
|-|-|
|Chiave|Valore|
|**com.microsoft.intune.mam.managedbrowser.bookmarks**|Il valore per questa configurazione è un elenco di segnalibri. Ogni segnalibro consiste di un titolo del segnalibro e di un URL. Separare il titolo e l'URL con il carattere **&#124;**.<br><br>Esempio: **Microsoft Bing&#124;https://www.bing.com**<br><br>Per configurare più segnalibri, separarli con due caratteri, ovvero **&#124;&#124;**<br><br>Esempio: **Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com**|

## <a name="how-to-specify-allowed-and-blocked-urls-for-the-managed-browser"></a>Come specificare gli URL consentiti e bloccati per Managed Browser

Usando la procedura per creare una configurazione per l'app Managed Browser, specificare la coppia di chiave e valore seguente:

|||
|-|-|
|Chiave|Valore|
|È possibile scegliere tra:<br><br>- Specificare gli URL consentiti (sono consentiti solo questi URL e nessun altro sito è accessibile): **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br>- Specificare gli URL bloccati (tutti gli altri siti sono accessibili): <br><br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**|Il valore corrispondente per la chiave è un elenco di URL. Tutti gli URL da consentire o bloccare vengono immessi come valore singolo, separati da un carattere barra verticale **&#124;**.<br><br>Esempi:<br><br>**URL1&#124;URL2&#124;URL3**<br>**http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com**|

>[!IMPORTANT]
>Non specificare entrambe le chiavi. Se entrambe le chiavi sono destinate allo stesso utente, viene usata la chiave consentita, essendo l'opzione più restrittiva.
>Assicurarsi inoltre di non bloccare pagine importanti come i siti Web della società.

### <a name="url-format-for-allowed-and-blocked-urls"></a>Formato dell'URL per URL consentite e bloccate
Usare le informazioni seguenti per saperne di più sui formati e i caratteri jolly consentiti che possono essere usati quando si specificano gli URL negli elenchi Consenti e Blocca:

-   È possibile usare il carattere jolly (**&#42;**) secondo le regole dell'elenco seguente di modelli consentiti:

-   Assicurarsi che tutte le URL abbiano con prefisso **http** o **https** quando immetterle nell'elenco.

-   È possibile specificare numeri di porta nell'indirizzo. Se non si specifica un numero di porta, i valori usati sono:

    -   Porta 80 per http

    -   Porta 443 per https

    Non è possibile usare i caratteri jolly per il numero di porta. Ad esempio, **http&colon;//www&period;contoso&period;com:*;** e **http&colon;//www&period;contoso&period;com: /*;** non sono supportati.

-   Per altre informazioni sui modelli consentiti che è possibile usare quando si specificano gli URL, vedere la tabella seguente:

|URL|Dettagli|Corrispondenze|Non corrisponde|
|-------|---------------|-----------|------------------|
|http://www.contoso.com|Corrisponde a una singola pagina|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
|http://contoso.com|Corrisponde a una singola pagina|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
|http://www.contoso.com/&#42;|Cerca una corrispondenza con tutti gli URL che iniziano con www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
|http://&#42;.contoso.com/&#42;|Cerca una corrispondenza con tutti i sottodomini in contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
|http://www.contoso.com/images|Corrisponde a una singola cartella|www.contoso.com/images|www.contoso.com/images/dogs|
|http://www.contoso.com:80|Cerca una corrispondenza con una singola pagina usando un numero di porta|http://www.contoso.com:80|
|https://www.contoso.com|Corrisponde a una singola pagina protetta|https://www.contoso.com|http://www.contoso.com|
|http://www.contoso.com/images/&#42;|Corrisponde a una singola cartella e a tutte le sottocartelle|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Di seguito sono riportati esempi di alcuni input che non è possibile specificare:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   Indirizzi IP

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

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

-   Manager Browser non usa le impostazioni create dagli utenti per il browser predefinito nei dispositivi. Managed Browser non può accedere a queste impostazioni.

-   Se si configura l'opzione **Richiedi PIN semplice per l'accesso** o **Richiedi credenziali aziendali per l'accesso** nei criteri di protezione dell'app associati a Managed Browser e si seleziona il collegamento alla Guida nella pagina di autenticazione, è possibile esplorare tutti i siti Internet, anche quelli aggiunti a un elenco Blocca nei criteri.

-   Managed Browser può bloccare l'accesso ai siti solo quando vi si accede direttamente. Non blocca l'accesso quando i servizi intermedi (ad esempio, un servizio di traduzione) vengono usati per accedere al sito.

-   Per consentire l'autenticazione e accedere alla documentazione di Intune, il sito **&#42;.microsoft.com** è esente dalle impostazioni degli elenchi Blocca o Consenti, perché è sempre consentito.

### <a name="turn-off-usage-data"></a>Disattivare la raccolta dati
Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso di Managed Browser per migliorare prodotti e servizi Microsoft. Gli utenti possono disattivare la raccolta dei dati usando l'impostazione **Dati di utilizzo** nei propri dispositivi. L'utente non ha alcun controllo sulla raccolta di tali dati.


-   Nei dispositivi iOS i siti Web visitati dagli utenti che hanno un certificato scaduto o non attendibile non possono essere aperti.
-   Manager Browser non usa le impostazioni create dagli utenti per il browser predefinito nei dispositivi. Managed Browser non può accedere a queste impostazioni.

-   Se si configura l'opzione **Richiedi PIN semplice per l'accesso** o **Richiedi credenziali aziendali per l'accesso** nei criteri di protezione dell'app associati a Managed Browser e si seleziona il collegamento alla Guida nella pagina di autenticazione, è possibile esplorare tutti i siti Internet, anche quelli aggiunti a un elenco Blocca nei criteri.

-   Managed Browser può bloccare l'accesso ai siti solo quando vi si accede direttamente. Non blocca l'accesso quando i servizi intermedi (ad esempio, un servizio di traduzione) vengono usati per accedere al sito.

-   Per consentire l'autenticazione e accedere alla documentazione di Intune, il sito **&#42;.microsoft.com** è esente dalle impostazioni degli elenchi Blocca o Consenti, perché è sempre consentito.

### <a name="turn-off-usage-data"></a>Disattivare la raccolta dati
Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso di Managed Browser per migliorare prodotti e servizi Microsoft. Gli utenti possono disattivare la raccolta dei dati usando l'impostazione **Dati di utilizzo** nei propri dispositivi. L'utente non ha alcun controllo sulla raccolta di tali dati.
