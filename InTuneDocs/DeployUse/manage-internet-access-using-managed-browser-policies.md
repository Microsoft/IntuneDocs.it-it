---
title: Gestire l&quot;accesso Web con il browser gestito | Microsoft Intune
description: Distribuire l&quot;applicazione Managed Browser per limitare l&quot;esplorazione del Web e il trasferimento dei dati Web ad altre app.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: maxles
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: a85aa3ce78425f2e00479ab0e48338e5eef8aec3


---

# Gestire l'accesso a Internet utilizzando criteri di browser gestiti con Microsoft Intune.
Managed Browser è un'applicazione per Web browser che è possibile distribuire nell'organizzazione usando Microsoft Intune. Un criterio di Managed Browser consente di configurare un elenco Consenti o Blocca che limita i siti Web che gli utenti di Managed Browser possono visitare.

I criteri di gestione di applicazioni mobili possono anche essere applicati all'app dato che si tratta di un'app gestita. Questi criteri possono includere il controllo delle operazioni taglia, copia e incolla, il blocco delle acquisizioni di schermata e la verifica dei collegamenti al contenuto selezionati dagli utenti, che possono essere aperti solo in altre app gestite. Per informazioni dettagliate, vedere [Configurare e distribuire i criteri di gestione delle applicazioni mobili nella console di Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Se gli utenti installano Managed Browser dall'App Store e questo non è gestito da Intune, si applica il comportamento seguente:<br /><br />
iOS: l'app Managed Browser può essere usata come Web browser di base, ma alcune funzionalità non saranno disponibili e non riusciranno ad accedere ai dati di altre app gestite da Intune.<br />
Android: l'app Managed Browser non può essere usata.<br /><br />
Se gli utenti installano Managed Browser autonomamente in un dispositivo iOS con una versione precedente a iOS 9, Managed Browser non verrà gestito dai criteri creati dall'utente. Per assicurarsi che il browser sia gestito da Intune, è necessario disinstallare l'app prima di poterla distribuire come app gestita. Nelle versioni iOS 9 e successive, se l'utente installa autonomamente Managed Browser, verrà richiesto di gestirlo con i criteri.

È possibile creare criteri di browser gestiti per i seguenti tipi di dispositivo:

-   Dispositivi che eseguono Android 4 e versioni successive

-   Dispositivi che eseguono iOS 8.0 e versione successiva

Intune Managed Browser supporta l'apertura di contenuti Web di [partner delle applicazioni di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

## Creare un criterio di browser gestiti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Criteri** &gt; **Aggiungi criterio**.

2.  Configurare uno dei seguenti **Software** tipi di criteri

    -   **Managed Browser (Android 4 e versioni successive)**

    -   **Managed Browser (iOS 8.0 e versioni successive)**

    Per altre informazioni su come creare e distribuire criteri, vedere l'argomento [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Usare la tabella seguente per configurare le impostazioni dei criteri di Managed Browser:

    - **Nome**. Immettere un nome univoco per i criteri di Managed browser che consenta di identificarli nella console di Intune.
    - **Descrizione**. Fornire una descrizione di carattere generale sul criterio di conformità dei browser gestiti e altre informazioni rilevanti per consentirne l'individuazione.
    - **Abilita un elenco di URL consentiti o bloccati per limitare gli URL che possono essere aperti da Managed Browser**. Selezionare una delle opzioni seguenti:
        - **Consenti a Manager Browser di aprire solo gli URL elencati di seguito**. Specificare un elenco di URL che possono essere aperti da Manager Browser.
        - **Non consentire a Managed Browser di aprire gli URL elencati di seguito**. Specificare un elenco di URL che non potranno essere aperti da Manager Browser.
**Nota:** non è possibile includere URL consentiti e bloccati nello stesso criterio di Managed Browser.
Per altre informazioni sui formati di URL che è possibile specificare, vedere **Formato dell'URL per URL consentiti e bloccati** in questo argomento.

4.  Al termine, scegliere **Salva criterio**.

Il nuovo criterio viene visualizzato nel nodo **Criteri di configurazione** dell'area di lavoro **Criteri**.

## Creare una distribuzione per l'app Managed Browser
Dopo aver creato il criterio di Manager Browser, è possibile creare una distribuzione software per l'app di Manager Browser e associarla al criterio di Manager Browser creato.

> [!IMPORTANT]
> I criteri di Managed Browser non vengono distribuiti allo stesso modo degli altri criteri di Intune. Questo tipo di criterio deve essere associato al pacchetto software di browser gestiti.

Distribuire l'applicazione, assicurarsi di selezionare i criteri di browser gestiti nella **gestione di App Mobile** pagina per associare il criterio con l'applicazione.

Per altre informazioni su come distribuire le app, vedere [Distribuire app in Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## Sicurezza e privacy per lo strumento di wrapping delle app

-   Nei dispositivi iOS i siti Web visitati dagli utenti che hanno un certificato scaduto o non attendibile non possono essere aperti.

-   Manager Browser non usa le impostazioni create dagli utenti per il browser predefinito nei dispositivi. Infatti, il browser gestito non dispone dell'accesso a queste impostazioni.

-   Se si configura l'opzione **Richiedi PIN semplice per l'accesso** o **Richiedi credenziali aziendali per l'accesso** nei criteri di gestione di applicazioni mobili associati a Managed Browser e un utente fa clic sul collegamento alla Guida nella pagina di autenticazione, è possibile navigare in tutti i siti Internet, anche quelli aggiunti a un elenco Blocca nei criteri di Managed Browser.

-   Managed Browser può bloccare l'accesso ai siti solo quando vi si accede direttamente. È possibile bloccare l'accesso quando servizi intermedi (ad esempio, un servizio di traduzione) vengono utilizzati per accedere al sito.

-   Per consentire l'autenticazione e per assicurarsi di poter accedere alla documentazione di Intune,**&#42;.microsoft.com** è esente dalle impostazioni degli elenchi Blocca o Consenti, perché è sempre consentito.

### Disattivare la raccolta dati
Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso di Managed Browser per migliorare prodotti e servizi Microsoft. Gli utenti possono disattivare la raccolta dei dati usando l'impostazione **Dati di utilizzo** nei propri dispositivi. L'utente non ha alcun controllo sulla raccolta di tali dati.

## Informazioni di riferimento

### Formato dell'URL per URL consentite e bloccate
Usare le informazioni seguenti per saperne di più sui formati e i caratteri jolly consentiti che possono essere usati quando si specificano gli URL negli elenchi Consenti e Blocca:

-   È possibile usare il carattere jolly asterisco **&#42;** secondo le regole nell'elenco di modelli consentiti seguente.

-   Assicurarsi che tutte le URL abbiano con prefisso **http** o **https** quando immetterle nell'elenco.

-   È possibile specificare numeri di porta nell'indirizzo. Se non si specifica un numero di porta, i valori utilizzati sono:

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
    |http://www.contoso.com:80|Cerca una corrispondenza con una singola pagina usando un numero di porta|http://www.contoso.com:80||
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



<!--HONumber=Oct16_HO4-->


