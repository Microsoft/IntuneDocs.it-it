---
title: Plug-in Cordova per Microsoft Intune App SDK | Microsoft Intune
description: 
keywords: sdk, Cordova, intune
author: oydang
manager: angrobe
ms.author: oydang
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: karthikaraman
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: af7df3fcf50c3508d495522341bb287c638f40a3
ms.openlocfilehash: 2af369cc44c710789ab65eb25f10602882772019


---
# ﻿<a name="microsoft-intune-app-sdk-cordova-plugin"></a>Plug-in Cordova per Microsoft Intune App SDK

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](intune-app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.


## <a name="overview"></a>Panoramica

Il [plug-in Cordova per Intune App SDK](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam) consente l'uso delle [funzionalità di gestione delle app per dispositivi mobili di Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) nelle app per iOS e Android compilate con Cordova. Il plug-in permette agli sviluppatori di integrare le funzionalità di protezione dei dati e delle app di Intune nelle app basate su Cordova.

Le funzionalità SDK possono essere abilitate senza modificare il comportamento dell'app. Dopo avere compilato il plug-in nell'app per dispositivi mobili per Android o iOS, l'amministratore IT potrà distribuire i criteri con la gestione di applicazioni mobili (MAM) di Microsoft Intune, che supporta un'ampia gamma di funzionalità di protezione dei dati. Il plug-in è stato compilato in modo che la maggior parte delle operazioni venga eseguita automaticamente durante il processo di compilazione di Cordova. Di conseguenza, l'utente dovrebbe essere in grado di ottenere rapidamente l'app abilitata per la gestione. Per iniziare, attenersi alla procedura seguente in base alla piattaforma di destinazione.




## <a name="whats-supported"></a>Elementi supportati

### <a name="developer-machines"></a>Computer di sviluppo
* Windows
* Mac OS


### <a name="mobile-app-platforms"></a>Piattaforme di app per dispositivi mobili
* Android 4.0+
* iOS

### <a name="intune-mobile-application-management-scenarios"></a>Scenari di gestione di applicazioni mobili di Intune

* Dispositivi registrati MDM di Intune
* Dispositivi registrati EMM di terze parti
* Dispositivi non gestiti (non registrati con MDM)

Le app Cordova compilate con il plug-in Cordova per Intune App SDK possono ora ricevere i criteri di gestione delle applicazioni per dispositivi mobili (MAM) di Intune sia sui dispositivi registrati per la gestione dei dispositivi mobili (MDM) di Intune che su quelli non registrati.



## <a name="prerequisites"></a>Prerequisiti

### <a name="technical-prerequisites"></a>Prerequisiti tecnici

* **[Solo per Android]** Nel dispositivo deve sempre essere installata l'app Portale aziendale di Microsoft Intune più recente.


* È richiesta la versione 0.8.0+ del [Plug-in delle librerie di autenticazione di Azure Active Directory (ADAL) per Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova).
  * **Importante:** a causa di un bug di Apache Cordova segnalato [qui](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22), le app che hanno già la dipendenza del plug-in non aggiorneranno automaticamente il plug-in alla versione richiesta.


### <a name="before-you-install-and-use-microsoft-intune-app-sdk-cordova-plugin-you-must"></a>Prima di installare e usare il plug-in Cordova per Microsoft Intune App SDK, **è necessario**:

* Rivedere le [Condizioni di licenza del plug-in Cordova per Intune App SDK](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam/blob/master/Intune_App_SDK_Cordova_plugin_RTM_license.pdf).

* Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando il plug-in Cordova per Intune App SDK, l'utente accetta tali condizioni di licenza.  Qualora l'utente non le accetti, non potrà usare il software.


## <a name="quick-start"></a>Avvio rapido

1. Aggiornare la versione di ADAL:

    ```
    cordova plugin remove cordova-plugin-ms-adal
    cordova plugin add cordova-plugin-ms-adal@0.8.x
    ```

2. Aggiungere il plug-in Cordova per Intune App SDK:

    ```
    cordova plugin add cordova-plugin-ms-intune-mam
    ```

## <a name="how-to-build-the-plugin-into-your-ios-app"></a>Come compilare il plug-in nell'app iOS

È necessario completare alcuni passaggi affinché l'app sia abilitata per le funzionalità MAM di Intune. Per ragioni di praticità, questi passaggi vengono eseguiti automaticamente nel processo di compilazione di Cordova come un hook di pre-compilazione. Di conseguenza, i passaggi automatizzati modificheranno i file `*.pbxproj`, `*-Info.plist` e `*.entitlements` associati alla configurazione del progetto. Se il progetto non contiene un file dei diritti, il plug-in ne creerà uno automaticamente.

Questa configurazione supporta solo una singola destinazione ed eseguirà la configurazione nella prima destinazione trovata se sono presenti più destinazioni. Se il processo non viene completato correttamente, verificare quanto segue:

1. Il progetto Xcode dell'app è `[name].xcodeproj` dove `[name]` è il valore definito in `config.xml`.
2. Il progetto usa la [struttura di directory dell'app Cordova standard](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="how-to-build-the-plugin-into-your-android-app"></a>Come compilare il plug-in nell'app Android

1. Importare questo plug-in con i più recenti strumenti Cordova. Il plug-in verrà richiamato automaticamente come un passaggio `after_compile`.

2. Il plug-in creerà una versione abilitata per MAM di un apk compilato (API Android 14+) alla fine del processo di compilazione. L'output di compilazione conterrà un `[Project]-intunewrapped-[Build_Configuration].apk` (ad esempio, `helloWorld-intunewrapped-debug.apk`).

Il plug-in supporta solo le compilazioni Gradle.

A causa di un bug di Cordova segnalato [qui](https://issues.apache.org/jira/browse/CB-9434) che fa sì che alcuni hook di Cordova siano ignorati in `cordova run`, per eseguire l'app sottoposta a wrapping dalla riga di comando, è necessario eseguire le operazioni seguenti:

```
$ cordova build
$ cordova run --nobuild
```


### <a name="signing-your-android-app"></a>Firma dell'app per Android
Per aggiungere informazioni sulla firma per l'apk di cui è stato eseguito il wrapping, modificare `build.json` come si farebbe normalmente per aggiungere informazioni sulla firma. Ad esempio:
```json
{
  "android": {
    "release": {
      "keystore": "your.keystore",
      "storePassword": "yourpassword",
      "alias": "youralias",
      "password" : "yourpassword",
      "keystoreType": ""
    }
  }
}
```

### <a name="build-for-android-test-only"></a>Compilazione solo per il test di Android

1. Aggiungere `android:testOnly="true"` al nodo dell'applicazione del file `AndroidManifest.xml`.


2. **Cordova 6.x.x:** in `[PROJECT_ROOT]/platforms/android/cordova/lib/Adb.js` modificare la riga 60 da

    ```javascript
    var args = ['-s', target, 'install'];
    ```
    su
    ```javascript
    var args = ['-s', target, 'install', '-t'];
    ```

Il risultato consiste nell'esecuzione di `adb install` con il flag "-t" dal momento che le app `testOnly` non sono installabili senza di esso.

### <a name="debugging-from-visual-studio"></a>Debug da Visual Studio
Dopo avere avviato l'app per la prima volta, verrà visualizzata una finestra di dialogo che informa che l'app è gestita da Intune. Fare clic su "Non visualizzare più questo messaggio" e quindi nuovamente sul pulsante di esecuzione/debug da Visual Studio per fare in modo che i punti di interruzione vengano riconosciuti.

## <a name="known-limitations"></a>Limitazioni note
### <a name="android"></a>Android
* Il supporto MultiDex è incompleto.
* L'app deve essere progettata per Android 4.0 (API Android 14) o versione successiva.

### <a name="ios"></a>iOS
* Ogni volta che si modifica l'elenco di UTI in corrispondenza del nodo **CFBundleDocumentTypes** del file **Info.plist**, è necessario deselezionare gli UTI di Intune nella sezione Imported UTI dello stesso file plist (nodo **UTImportedTypeDeclarations**) prima di compilare nuovamente. Tutti gli UTI di Intune inizieranno con il prefisso `com.microsoft.intune.mam`.

* Se si vuole rimuovere il plug-in di Intune dal progetto Cordova, è necessario rimuovere anche la piattaforma iOS e aggiungerla nuovamente per annullare alcune delle configurazioni di Intune nei file con estensione xcodeproj e plist.



<!--HONumber=Nov16_HO4-->


