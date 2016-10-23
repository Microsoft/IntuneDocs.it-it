---
title: "Novità | Microsoft Intune"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 503719953031bf5079b2bf5bc84a0497d708f79a
ms.openlocfilehash: 730809e0841a248b90f5fe157f2c6338bfd32b2d


---
# Novità di Microsoft Intune -- Ottobre 2016
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## Novità

### Accesso condizionale per la gestione di applicazioni mobili
Sarà possibile limitare l'accesso a Exchange Online in modo che l'accesso possa essere eseguito solo da app che supportano i criteri di gestione delle applicazioni mobili di Intune, ad esempio Outlook. [Questa nuova funzionalità](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) si abbina perfettamente con i criteri di gestione delle app per dispositivi mobili di Intune perché è possibile bloccare l'accesso ai client di posta predefiniti o ad altre app che non sono state configurate con i criteri di gestione delle app per dispositivi mobili di Intune. In questo modo gli utenti accedono ai dati dell'organizzazione con app che possono essere protette con MAM Intune. Per un'introduzione alla gestione delle app per dispositivi mobili Intune, visitare il portale di Azure. Cercare la nuova sezione Accesso condizionale nel pannello "Impostazioni".

### Accesso condizionale per i PC Windows
È ora possibile creare criteri di accesso condizionale tramite la console di amministrazione di Intune per impedire l'accesso a [Exchange Online](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune) e [SharePoint Online](/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) ai PC Windows. È inoltre possibile creare criteri di accesso condizionale per bloccare l'accesso alle applicazioni universali e desktop di Office.

### Supporto di Android for Work
Intune ora è incluso nel programma Android for Work. L'implementazione del supporto delle funzionalità Android for Work in Intune sarà avviata questo mese.
[Leggere l'annuncio Microsoft relativo al supporto di Android for Work in Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/12/microsoft-intune-support-for-android-for-work/).

Gli argomenti seguenti relativi a Intune seguenti sono nuovi o aggiornati con le informazioni su Android for Work:

Per i professionisti IT:
- [Set up Android for Work (Impostare Android for Work)](/intune/deploy-use/set-up-android-for-work)
<!--- [Nathan Bigman's resource access topics]()-->
- [Limitare l'accesso alla posta elettronica per Exchange Online e il nuovo ambiente Exchange Online dedicato](/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
- [Limitare l'accesso alla posta elettronica per Exchange locale e l'ambiente legacy Exchange Online dedicato con Intune](/intune/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
- [Android for Work compliance policy settings (Impostazioni dei criteri di conformità di Android for Work)](/intune/deploy-use/afw-compliance-policy-settings-in-microsoft-intune)
- [How to deploy Android for Work apps (Come distribuire le app Android for Work)](/intune/deploy-use/android-for-work-apps)
- [Configurare le app Android for Work con i criteri di configurazione delle app per dispositivi mobili](/intune/deploy-use/afw-app-configuration-policy)
- [Impostazioni dei criteri di Android for Work](/intune/deploy-use/android-for-work-policy-settings-in-microsoft-intune)

Per gli utenti finali:
- [Cosa accade quando si crea un profilo di lavoro](/intune/enduser/what-happens-when-you-create-a-work-profile-android)
- [Create a work profile and enroll your device in Intune (Creare un profilo di lavoro e registrare il dispositivo in Intune)](/intune/enduser/create-a-work-profile-and-enroll-your-device-in-intune-android)

### Integrazione di Lookout per proteggere i dispositivi iOS
A ottobre Microsoft prevede di integrare la soluzione di protezione dalle minacce per dispositivi mobili Lookout per proteggere i dispositivi mobili iOS grazie al rilevamento di malware, app rischiose e altro ancora. La soluzione Lookout consente di determinare il livello di minaccia, che è configurabile. È possibile creare una regola dei criteri di conformità in Intune per determinare la conformità del dispositivo in base alla valutazione del rischio da parte di Lookout. Con i criteri di accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali in base allo stato di conformità del dispositivo.

Agli utenti finali con dispositivi iOS non conformi verrà richiesto di eseguire la registrazione e di installare l'applicazione Lookout for Work, attivare l'app e correggere le minacce segnalate nell'applicazione Lookout for Work per ottenere l'accesso ai dati aziendali. Vedere le informazioni su come [Configurare e distribuire l'app Lookout for Work](/intune/deploy-use/configure-and-deploy-lookout-for-work-apps).
<!--TFS 1319493-->

<!--### New Microsoft Intune Company Portal available for Windows 10 devices
Microsoft is releasing a new [Microsoft Intune Company Portal for Windows 10 devices](https://go.microsoft.com/fwlink/?linkid=830663). This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike, while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on (SSO) and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store.-->

### Strumento per la disposizione testo per app di Intune
È possibile consentire alle app di usare i criteri di gestione del app per dispositivi mobili di Intune tramite lo strumento per la disposizione testo per app di Intune. È ora disponibile il supporto per i criteri di gestione delle app per dispositivi mobili di Intune che non richiede la registrazione del dispositivo.

### Gestire la stampa dalle app gestite con criteri di gestione delle app per dispositivi mobili
Ora è possibile impedire la stampa di dati aziendali dalle app che includono criteri di gestione delle app per dispositivi mobili. Questa impostazione è disponibile nel [portale di Azure](/Intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) ed è supportata in dispositivi [iOS](/Intune/deploy-use/ios-mam-policy-settings) e [Android](/Intune/deploy-use/android-mam-policy-settings).
<!--TFS 1014328-->

## Notifiche

### Compatibilità di Android Samsung KNOX con Intune
Alcuni modelli di telefoni Samsung Galaxy Ace non possono essere gestiti da Intune come dispositivi Samsung KNOX. Quando verranno registrati con Intune, questi dispositivi verranno invece gestiti come dispositivi Android standard.

I numeri di modello interessati sono:

* SM-G313HU
* SM-G313HY
* SM-G313M
* SM-G313MY
* SM-G313U

Non sono richieste altre azioni da parte dell'amministratore o degli utenti. Per altre informazioni, visitare il sito Web [Samsung KNOX](https://www.samsungknox.com).

### L'app Portale aziendale per Windows 8 è deprecata e il supporto per le piattaforme Windows Phone 8 e Windows RT sarà deprecato
A partire da ottobre 2016, il supporto di Microsoft Intune per il portale aziendale di Windows Phone 8 verrà deprecato. Verrà anche deprecato il supporto di Microsoft Intune per le piattaforme Windows Phone 8 e Windows RT. Di conseguenza, non sarà possibile registrare o aggiornare dispositivi Windows Phone 8 o Windows RT.

È possibile continuare a gestire i dispositivi Windows Phone 8, Windows RT e Windows 8 che sono già registrati. Aggiornare i dispositivi Windows Phone 8 e Windows 8 a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi senza interruzioni.

A partire da novembre 2016, il supporto per il portale aziendale di Windows Phone 8 verrà deprecato.
<!--TFS 1255391-->

## Sviluppi futuri

### Nuovo Portale aziendale di Microsoft Intune disponibile per dispositivi Windows 10
Microsoft sta rilasciando un nuovo Portale aziendale di Microsoft Intune per dispositivi Windows 10. Questa app, che sfrutta il nuovo formato universale di Windows 10, offrirà un'esperienza utente aggiornata all'interno dell'app ed esperienze identiche in tutti i dispositivi Windows 10, sia PC che mobili, senza variazioni alle funzionalità già in uso.

La nuova app consentirà anche agli utenti di sfruttare altre funzionalità della piattaforma come Single Sign-On (SSO) e l'autenticazione basata su certificato nei dispositivi Windows 10. L'app verrà resa disponibile come aggiornamento delle installazioni del portale aziendale di Windows 8.1 e del portale aziendale di Windows Phone 8.1 da Windows Store. Per altre informazioni, vedere [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).
<!--TFS 1016502-->

### Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versioni precedenti di Intune](previous-intune-releases.md)



<!--HONumber=Oct16_HO3-->


