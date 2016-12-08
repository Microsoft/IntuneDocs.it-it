---
title: "Novità | Microsoft Intune"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8ef3b7e4eec5a520c93fb3f70c8e5b6ee7d2c3aa
ms.openlocfilehash: e0b0c7eb3ddc07f05fc0c2e4caa6726ed052c9d8


---
# <a name="whats-new-in-microsoft-intune---november-2016"></a>Novità di Microsoft Intune - Novembre 2016
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

> [!Note]
> Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

__Nuovo portale aziendale di Microsoft Intune disponibile per dispositivi Windows 10__ Microsoft ha rilasciato una nuova app [Portale aziendale di Microsoft Intune per dispositivi Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Questa app, che sfrutta il nuovo formato universale di Windows 10, offrirà un'esperienza utente aggiornata all'interno dell'app ed esperienze identiche in tutti i dispositivi Windows 10, sia PC che mobili, senza variazioni alle funzionalità già in uso.

La nuova app consentirà anche agli utenti di sfruttare altre funzionalità della piattaforma come Single Sign-On (SSO) e l'autenticazione basata su certificato nei dispositivi Windows 10. L'app verrà resa disponibile come aggiornamento delle installazioni del portale aziendale di Windows 8.1 e del portale aziendale di Windows Phone 8.1 da Windows Store. Per altre informazioni, vedere [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

<!--### Support for Windows Store for Business Apps Being Deployed as Available
You can now deploy apps you synchronized from the Windows Store for Business (WSfB) with a deployment action of __Available__ or __Required__. After syncing WSfB apps into Intune, administrators will be able to target those apps as available installs to groups of users. End users will see the deployed WSfB apps as available for install in the Universal Company Portal, where they can choose whether they would like to acquire the apps.

### Conditional Access for MAM with SharePoint Online

You can block apps that are not supported by Intune mobile app management (MAM) policies from accessing SharePoint online.  You can get started in Intune mobile app management via the Azure portal. Look for the  Conditional Access section in the “Settings” blade which now includes the option for SharePoint online.-->

> [!IMPORTANT]

> __Aggiornamento di Intune e Android for Work__

> Se da una parte è possibile distribuire app Android for Work con un'azione di __Richiesto__, un'app può essere distribuita solo come __Disponibile__ se i gruppi di Intune sono stati migrati alla nuova esperienza dei gruppi di Azure AD.

### <a name="intune-app-sdk-for-cordova-plugin-now-supports-mam-without-enrollment"></a>Il plug-in Cordova per Intune App SDK attualmente supporta la gestione di applicazioni mobili senza registrazione
Gli sviluppatori di app possono ora usare il plug-in Cordova per Intune App SDK per abilitare funzionalità di gestione di applicazioni mobili senza registrazione del dispositivo nelle proprie app basate su Cordova per iOS e Android. Il plug-in Cordova per Intune App SDK è disponibile [qui](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

### <a name="intune-app-sdk-xamarin-component-now-supports-mam-without-enrollment"></a>Il componente Xamarin per Intune App SDK attualmente supporta la gestione di applicazioni mobili senza registrazione
Gli sviluppatori di app possono ora usare il componente Xamarin per Intune App SDK per abilitare funzionalità di gestione di applicazioni mobili senza registrazione del dispositivo nelle proprie app basate su Xamarin per iOS e Android. Il componente Xamarin per Intune App SDK è disponibile [qui](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

## <a name="notices"></a>Notifiche

### <a name="symantec-signing-certificate-no-longer-requires-signed-windows-phone-8-company-portal-for-upload"></a>Il certificato di firma Symantec non richiede più un'app Portale aziendale di Windows Phone 8 firmata per il caricamento
Per il caricamento del certificato di firma Symantec non è più necessaria un'app Portale aziendale di Windows Phone 8 firmata. Il certificato può essere caricato in modo indipendente.

## <a name="deprecations"></a>Elementi deprecati

### <a name="support-for-the-windows-phone-8-company-portal"></a>Supporto per l'app Portale aziendale di Windows Phone 8
Il supporto per il portale aziendale di Windows Phone 8 sarà deprecato. Il supporto per le piattaforme Windows Phone 8 e WinRT è stato deprecato a ottobre 2016. Il supporto per il portale aziendale di Windows 8 è stato deprecato a ottobre 2016.


### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versioni precedenti di Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO1-->


