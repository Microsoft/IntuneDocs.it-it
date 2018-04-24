---
title: Plug-in Cordova per Microsoft Intune App SDK
description: Il plug-in Intune App SDK Cordova permette agli sviluppatori di integrare le funzionalità di protezione dei dati e delle app di Intune nelle app basate su Cordova.
keywords: sdk, Cordova, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bb940cb9-d43f-45ca-b065-ac0adc61dc6f
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d32c024d6cd526062c373b56dd18bca9480c32fa
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-app-sdk-cordova-plugin"></a>Plug-in Cordova per Microsoft Intune App SDK

> [!IMPORTANT]
> Intune terminerà il supporto per il plug-in Cordova per Microsoft Intune App SDK il 1 maggio 2018. È consigliabile usare lo strumento di wrapping delle app di Intune. Per altre informazioni sullo strumento di wrapping delle app, vedere [Strumento di wrapping delle app per iOS](app-wrapper-prepare-ios.md) e [Strumento di wrapping delle app per Android](app-wrapper-prepare-android.md). Per altre informazioni su questa modifica, vedere la sezione [Notifiche](whats-new.md#notices) in [Novità di Microsoft Intune](whats-new.md).

## <a name="overview"></a>Panoramica

[Plugin Cordova per Intune App SDK](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) nelle app iOS e Android compilate con Cordova. Il plug-in permette agli sviluppatori di integrare le funzionalità di protezione dei dati e delle app di Intune nelle app basate su Cordova.

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

Le funzionalità SDK possono essere abilitate senza modificare il comportamento dell'app. Dopo avere compilato il plug-in nell'app Android o iOS, l'amministratore di Microsoft Intune potrà distribuire i criteri di protezione delle app di Intune, costituiti da un'ampia gamma di funzionalità per la protezione dei dati. Il plug-in è compilato in modo che la maggior parte delle operazioni venga eseguita automaticamente durante il processo di compilazione di Cordova. Di conseguenza, l'utente dovrebbe essere in grado di ottenere rapidamente l'app abilitata per la protezione delle app di Intune. Per iniziare, attenersi alla procedura seguente in base alla piattaforma di destinazione.

## <a name="supported-platforms"></a>Piattaforme supportate

* Il plug-in funziona nei sistemi operativi Windows, Mac e Linux
* Il plug-in funziona per le app Android con `minSdkVersion` >= 14 e `targetSdkVersion` <= 24
* Il plug-in funziona per le app iOS destinate a iOS 9.0 e versioni successive.

## <a name="intune-mobile-application-management-scenarios"></a>Scenari di gestione di applicazioni mobili di Intune

* Dispositivi registrati MDM di Intune
* Dispositivi registrati EMM di terze parti
* Dispositivi non gestiti (non registrati con MDM)

Le app Cordova compilate con il plug-in Cordova per Intune App SDK possono ora ricevere i criteri di protezione delle app di Intune sia sui dispositivi registrati per la gestione dei dispositivi mobili (MDM) di Intune che su quelli non registrati.

## <a name="prerequisites"></a>Prerequisiti

### <a name="android"></a>Android

* Nel dispositivo deve sempre essere installata l'app Portale aziendale di Microsoft Intune più recente.
* È necessario che sia disponibile come minimo Java 7 nel percorso di esecuzione della compilazione Cordova quando si usa il plug-in.

### <a name="ios"></a>iOS

* Nel dispositivo deve sempre essere installata l'app Portale aziendale di Microsoft Intune più recente per le funzionalità MDM. *Non* è necessaria per i criteri di protezione delle app senza funzionalità di registrazione del dispositivo.

### <a name="both-platforms"></a>Entrambe le piattaforme

* È richiesta la versione 0.8.0+ del [Plug-in delle librerie di autenticazione di Azure Active Directory (ADAL) per Cordova](https://github.com/AzureAD/azure-activedirectory-library-for-cordova).

> [!NOTE]
> A causa di un bug di Apache Cordova segnalato [qui](https://issues.apache.org/jira/browse/CB-6227?jql=text%20~%20%22plugin%20dependency%22), le app che hanno già la dipendenza del plug-in non aggiorneranno automaticamente il plug-in alla versione necessaria.



## <a name="quickstart"></a>Guida introduttiva

1. Aggiornare la versione di ADAL:

   ```shell
   cordova plugin remove cordova-plugin-ms-adal
   cordova plugin add cordova-plugin-ms-adal@0.8.x
   ```

2. Aggiungere il plug-in Cordova per Intune App SDK:

   ```shell
   cordova plugin add cordova-plugin-ms-intune-mam
   ```

## <a name="build-the-plugin-into-your-ios-app"></a>Compilare il plug-in nell'app iOS

È necessario completare alcuni passaggi per abilitare l'app per i criteri di protezione delle app di Intune. Per ragioni di praticità, questi passaggi vengono eseguiti automaticamente nel processo di compilazione di Cordova come un hook di pre-compilazione. Di conseguenza, i passaggi automatizzati modificheranno i file `*.pbxproj`, `*-Info.plist` e `*.entitlements` associati alla configurazione del progetto. Se il progetto non contiene un file dei diritti, il plug-in ne creerà uno automaticamente.

Questa configurazione supporta solo una singola destinazione ed eseguirà la configurazione nella prima destinazione trovata se sono presenti più destinazioni. Se il processo non viene completato correttamente, verificare quanto segue:

1. Il progetto Xcode dell'app è `[name].xcodeproj` dove `[name]` è il valore definito in `config.xml`.
2. Il progetto usa la [struttura di directory dell'app Cordova standard](https://cordova.apache.org/docs/en/latest/reference/cordova-cli/index.html#directory-structure).

## <a name="build-the-plugin-into-your-android-app"></a>Compilare il plug-in nell'app Android

1. Importare questo plug-in con i più recenti strumenti Cordova. Il plug-in verrà richiamato automaticamente come un passaggio `after_compile`.

2. Il plug-in creerà una versione abilitata per Intune di un apk compilato (API Android 14+) alla fine del processo di compilazione. L'output di compilazione conterrà un `[Project]-intunewrapped-[Build_Configuration].apk` (ad esempio, `helloWorld-intunewrapped-debug.apk`).

> [!NOTE]
> Il plug-in supporta solo le compilazioni Gradle.

A causa di un bug di Cordova segnalato [qui](https://issues.apache.org/jira/browse/CB-9434) che fa sì che alcuni hook di Cordova siano ignorati in `cordova run`, per eseguire l'app sottoposta a wrapping dalla riga di comando, è necessario eseguire le operazioni seguenti:

```shell
$ cordova build
$ cordova run --nobuild
```

## <a name="sign-your-android-app"></a>Firmare l'app Android

Il plug-in riconosce automaticamente le informazioni di firma fornite a Cordova nelle posizioni seguenti:

* platforms/android/debug-signing.properties
* platforms/android/release-signing.properties
* res/native/android/ant.properties

Per altre informazioni sul formato previsto, vedere le [informazioni sulla firma di Gradle di Cordova](https://cordova.apache.org/docs/en/latest/guide/platforms/android/#using-gradle).

Attualmente Intune non supporta la possibilità di fornire informazioni sulla firma in `build.json` o in posizioni arbitrarie specificate tramite parametri per la compilazione di Cordova.

## <a name="debugging-from-visual-studio"></a>Debug da Visual Studio

Dopo avere avviato l'app per la prima volta, viene visualizzata una finestra di dialogo che informa che l'app è gestita da Intune. Fare clic su "Non visualizzare più questo messaggio" e quindi nuovamente sul pulsante di esecuzione/debug da Visual Studio per fare in modo che i punti di interruzione vengano riconosciuti.

## <a name="known-limitations"></a>Limitazioni note

### <a name="android"></a>Android

* Il supporto MultiDex è incompleto.
* L'app deve avere `minSdkVersion` 14 e `targetSdkVersion` 24 o versioni precedenti. Attualmente Intune non supporta app destinate ad API 25
* Intune non firma di nuovo le app firmate con lo schema di firma V2. Quando si esegue il wrapping delle app con firma V2 dal plug-in, il file apk di output sottoposto a wrapping sarà non firmato.
  *
  * È possibile disabilitare la firma V2 predefinita di Cordova aggiungendo il codice seguente al file `build-extras.gradle`:

  ```gradle
  android {
      signingConfigs {
          release {
              v2SigningEnabled false
          }
          debug {
              v2SigningEnabled false
          }
      }
      buildTypes {
          release {
              signingConfig signingConfigs.release
          }
          debug {
              signingConfig signingConfigs.debug
          }
      }
  }
  ```

### <a name="ios"></a>iOS

* Ogni volta che si modifica l'elenco di UTI in corrispondenza del nodo **CFBundleDocumentTypes** del file **Info.plist**, è necessario deselezionare gli UTI di Intune nella sezione Imported UTI dello stesso file plist (nodo **UTImportedTypeDeclarations**) prima di compilare nuovamente. Tutti gli UTI di Intune inizieranno con il prefisso `com.microsoft.intune.mam`.

* Se si vuole rimuovere il plug-in Intune App SDK per Cordova, è necessario rimuovere anche la piattaforma iOS e aggiungerla nuovamente per annullare alcune delle configurazioni di Intune nei file con estensione xcodeproj e plist.
