---
title: "Novità | Microsoft Intune"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 8e88c14ad77d8fe1b4c0fe2e7676d126e6288146
ms.openlocfilehash: bcd77b751c2059131558e1cbfeebd4d3f71086e5


---
# <a name="whats-new-in-microsoft-intune---november-2016"></a>Novità di Microsoft Intune - Novembre 2016
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## <a name="new-capabilities"></a>Nuove funzionalità

<!--### View App States for All Platforms in Real Time
App installation status is now shown in real-time in the console. When you previously deployed an app, you had to wait for a targeted device to report back before the app install status was displayed in the Intune console.

### Streamline iOS App Management for your End Users
Intune can now automatically take over management of the previously installed app and no end user action is required.

Previously, if the end user of an enrolled iOS device installed an app from the App Store before you deployed that same app with a deployment action of __Available__, then the end user had to:

1. Open the __Company Portal__.
2. Select the app.
3. Tap __Install__ to enable Intune to take over management of the app.-->

<!--### New Microsoft Intune Company Portal App for Windows 10 Devices
Microsoft is releasing a new Intune Company Portal for Windows 10 devices. This app, which leverages the new Windows 10 Universal format, will provide the user with an updated user experience within the app and identical experiences across all Windows 10 devices, PC and Mobile alike - while still enabling all the same functionality that they are using today.

The new app will also allow users to leverage additional platform features like single sign-on and certificate-based authentication on Windows 10 devices. The app will be made available as an upgrade to the existing Windows 8.1 Company Portal and Windows Phone 8.1 Company Portal installs from the Windows Store. It will also be available for sideloading.-->

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



<!--HONumber=Nov16_HO3-->


