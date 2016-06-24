---
# required metadata

title: Gestire l'accesso a Internet usando criteri di Managed Browser| Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gestire l'accesso a Internet utilizzando criteri di browser gestiti con Microsoft Intune.
Managed Browser è un'applicazione Web browser che è possibile distribuire nell'organizzazione tramite Microsoft Intune. Un criterio di browser gestito consente di configurare un elenco Consenti o Blocca che limita i siti web che gli utenti del browser gestiti possono visitare.

Poiché questa applicazione è un'applicazione gestita, è inoltre possibile applicare criteri di gestione delle applicazioni per dispositivi mobili per l'applicazione, ad esempio il controllo consente di acquisire l'utilizzo di Taglia, copia e Incolla, impedendo la schermata e inoltre garantire che i collegamenti al contenuto che gli utenti fanno clic solo aprire in altre gestito app. Per informazioni dettagliate, vedere l[Configurare e distribuire i criteri di gestione delle applicazioni mobili nella console di Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Se gli utenti installano Managed Browser dall'Archivio applicazioni e questo non è gestito da Intune, si applica il comportamento seguente:
iOS: l'app Managed Browser può essere usata come Web browser di base, ma alcune funzionalità non saranno disponibili e non riusciranno ad accedere ai dati di altre app gestite da Intune.
Android: l'app Managed Browser non può essere usata.
Se gli utenti installano Managed Browser autonomamente in un dispositivo iOS con una versione precedente a iOS 9, non verrà gestito da alcun criterio creato. Per assicurarsi che il browser viene gestito da Intune, è necessario disinstallare l'applicazione prima di poter distribuire loro come un'applicazione gestita. Nelle versioni iOS 9 e successive, se l'utente installa autonomamente Managed Browser, verrà richiesto di renderlo gestito per criterio.

È possibile creare criteri di browser gestiti per i seguenti tipi di dispositivo:

-   Dispositivi che eseguono Android 4 e versioni successive

-   Dispositivi che eseguono iOS 7.1 e versioni successive

Intune Managed Browser supporta l'apertura di contenuti Web di [partner delle applicazioni di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

## Creare un criterio di browser gestiti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare uno dei seguenti **Software** tipi di criteri

    -   **Criteri di Managed Browser (Android 4 e versioni successive)**

    -   **Criteri di Managed Browser (iOS 7.1 e versioni successive)**

    Per altre informazioni su come creare e distribuire criteri, vedere l'argomento [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Utilizzare la tabella seguente per configurare le impostazioni dei criteri generali:

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per i criteri di Managed browser che consenta di identificarli nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio di conformità dei browser gestiti e altre informazioni rilevanti per consentirne l'individuazione.|
    |**Consentire che un elenco Consenti o un elenco di blocchi per limitare gli URL possano aprire il Browser gestiti**|Selezionare una delle opzioni seguenti:<br /><br />**Consenti al browser gestito di aprire solo gli URL elencati di seguito**: specificare un elenco di URL che è possibile aprire in Managed Browser.<br /><br />**Non consentire al browser gestito di aprire gli URL elencati di seguito **: specificare un elenco di URL di cui bloccare l'apertura in Managed Browser. **Nota:** non è possibile includere URL consentiti e bloccati nello stesso criterio di Managed Browser.<br />Per altre informazioni sui formati di URL che è possibile specificare, vedere **Formato dell'URL per URL consentiti e bloccati** in questo argomento.|

4.  Al termine, fare clic su **Salva criterio**..

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri** .

## Creare una distribuzione per l'app Managed Browser
Dopo aver creato il criterio di browser gestiti, è possibile creare una distribuzione di software per l'applicazione di browser gestiti e associare il criterio di browser gestiti creato.

> [!IMPORTANT]
> I criteri di Managed Browser non vengono distribuiti allo stesso modo degli altri criteri di Intune. Questo tipo di criterio deve essere associato al pacchetto software di browser gestiti.

Distribuire l'applicazione, assicurarsi di selezionare i criteri di browser gestiti nella **gestione di App Mobile** pagina per associare il criterio con l'applicazione.

Per altre informazioni su come distribuire le app, vedere [Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md)..

## Sicurezza e privacy per lo strumento di wrapping delle app

-   Sui dispositivi iOS, non è possibile aprire i siti web che gli utenti visitano che dispone di un certificato scaduto o non attendibile.

-   Impostazioni apportate dall'utente per il browser predefinito sui dispositivi non vengono utilizzate dal browser gestiti. Infatti, il browser gestito non dispone dell'accesso a queste impostazioni.

-   Se si configurano le opzioni **Richiedi PIN semplice per l'accesso** o **richiede credenziali aziendali per l'accesso** in un'applicazione per dispositivi mobili nei Criteri di gestione associato con il browser gestito e un utente fa clic sul collegamento Guida nella pagina autenticazione, è possibile passare tutti i siti Internet indipendentemente dal fatto che sono stati aggiunti a un elenco di blocco nei criteri di browser gestiti.

-   Il Browser gestito può bloccare l'accesso ai siti solo quando vi si accede direttamente. È possibile bloccare l'accesso quando servizi intermedi (ad esempio, un servizio di traduzione) vengono utilizzati per accedere al sito.

-   Per consentire l'autenticazione e per assicurarsi di poter accedere alla documentazione di Intune,**&#42;.microsoft.com** è esente dalle impostazioni degli elenchi Blocca o Consenti, perché è sempre consentito.

### Disattivare la raccolta dati
Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso di Managed Browser per migliorare prodotti e servizi Microsoft, ma gli utenti possono disattivare la raccolta dati con l'impostazione **Dati sull'utilizzo** nel dispositivo. L'utente non ha alcun controllo sulla raccolta di tali dati.

## Informazioni di riferimento

### Formato dell'URL per URL consentite e bloccate
Utilizzare le seguenti informazioni per ulteriori informazioni sui formati consentiti e i caratteri jolly, che è possibile utilizzare quando si specificano le URL negli elenchi consentiti e bloccati.

-   È possibile usare il carattere jolly asterisco **&#42;** secondo le regole nell'elenco di modelli consentiti sottostante.

-   Assicurarsi che tutte le URL abbiano con prefisso **http** o **https** quando immetterle nell'elenco.

-   È possibile specificare numeri di porta nell'indirizzo. Se non si specifica un numero di porta, i valori utilizzati sono:

    -   Porta 80 per http

    -   Porta 443 per https

    Uso dei caratteri jolly per il numero di porta non supportato, ad esempio, **http://www.contoso.com:*;** e **http://www.contoso.com: /*;**

-   Per ulteriori informazioni sui modelli consentiti che è possibile utilizzare quando si specificano gli URL, utilizzare la tabella seguente:

|URL|Dettagli|Corrispondenze|Non corrisponde|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Corrisponde a una singola pagina|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|Corrisponde a una singola pagina|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Corrisponde a tutte le URL a partire da www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|Corrisponde a tutti i sottodomini in contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|Corrisponde a una singola cartella|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|Corrisponde a una singola pagina utilizzando un numero di porta|http://www.contoso.com:80||
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

### Come vengono risolti i conflitti tra l'elenco Consenti e blocca
Se distribuiti diversi criteri browser gestito a un dispositivo e si verifica un conflitto di impostazioni, sia per modalità (Consenti o blocca) e per elenchi di URL, che vengono poi valutati a livello di conflitti. In caso di conflitto si applica il comportamento seguente:

-   Se le modalità disponibili in tutti i criteri sono uguali, ma gli elenchi di URL sono diversi, le URL non verranno applicate al dispositivo.

-   Se le modalità disponibili in tutti i criteri sono diverse, ma gli elenchi di URL sono uguali,le URL non verranno applicate al dispositivo.

-   Se un dispositivo riceve i criteri di browser gestiti per la prima volta ed il conflitto nei due criteri, le URL non verranno applicate al dispositivo Utilizzare il nodo **conflitti tra criteri** dei **criteri** nell’area di lavoro per visualizzare i conflitti.

-   Se un dispositivo ha già ricevuto un criterio di browser gestiti e un secondo criterio è distribuito con le impostazioni in conflitto, le impostazioni originali rimangono sul dispositivo. Utilizzare il nodo **conflitti tra criteri** dei **criteri** nell’area di lavoro per visualizzare i conflitti.


<!--HONumber=May16_HO1-->


