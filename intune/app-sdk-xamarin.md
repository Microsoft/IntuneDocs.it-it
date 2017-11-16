---
title: Componente Xamarin per Microsoft Intune App SDK
description: 
keywords: sdk, Xamarin, intune
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 11/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f50ecfbf5a0ac0b05de38e0ad29b27a729ab824b
ms.sourcegitcommit: 0f877251e6adf4e45b918cc8dc9193626727f2d9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/03/2017
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin per Microsoft Intune App SDK

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.



## <a name="overview"></a>Panoramica
Il [componente Xamarin per Intune App SDK](https://components.xamarin.com/view/microsoft.intune.mam) consente l'uso dei [criteri di protezione delle app di Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) nelle app per iOS e Android compilate con Xamarin. Il componente consente agli sviluppatori di creare con facilità le funzionalità di protezione dell'app Intune nella propria app basata su Xamarin.

> [!NOTE]
> Il supporto per l'SDK di Intune per Xamarin è attualmente disponibile in anteprima. 

Il componente Xamarin per Microsoft Intune App SDK consente di incorporare i criteri di protezione delle app di Intune, definiti anche criteri APP o MAM, nelle app sviluppate con Xamarin. Un'applicazione abilitata per MAM è integrata con Intune App SDK. Gli amministratori IT possono distribuire i criteri di protezione all'app per dispositivi mobili quando Intune gestisce attivamente l'app.

## <a name="whats-supported"></a>Elementi supportati

### <a name="developer-machines"></a>Computer di sviluppo
* macOS


### <a name="mobile-app-platforms"></a>Piattaforme di app per dispositivi mobili
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Scenari di gestione di applicazioni mobili di Intune

* Dispositivi registrati MDM di Intune
* Dispositivi registrati EMM di terze parti
* Dispositivi non gestiti (non registrati con MDM)

Le app Xamarin compilate con il componente Xamarin per Intune App SDK possono ora ricevere i criteri di protezione delle app di Intune nel dispositivi registrati in Gestione dei dispositivi mobili di Intune e nei dispositivi non registrati.

## <a name="prerequisites"></a>Prerequisiti

* **[Solo per Android]** Nel dispositivo deve essere installata l'app Portale aziendale di Microsoft Intune più recente.

## <a name="get-started"></a>Introduzione

1.  Scaricare **Xamarin-component.exe** da [qui](https://components.xamarin.com/submit/xpkg) ed estrarre i file.

2. Leggere le [condizioni di licenza](https://components.xamarin.com/license/microsoft.intune.mam) per il componente Xamarin per le funzionalità MAM di Microsoft Intune.

3.  Scaricare la cartella del componente Xamarin per Intune App SDK da [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) o [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) ed estrarre i file. Entrambi i file scaricati al passaggio 1 e al passaggio 3 devono essere nello stesso livello di directory.

4.  Nella riga di comando come amministratore eseguire `Xamarin.Component.exe install <.xam> file`.

5.  In Visual Studio fare clic con il pulsante destro del mouse sui **componenti** nel progetto Xamarin creato in precedenza.

6.  Selezionare **Modifica componenti** e aggiungere il componente Intune App SDK scaricato localmente nel computer.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili iOS
1.  Per inizializzare Intune App SDK, è necessario chiamare un'API nella classe `AppDelegate.cs`. Ad esempio:

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  Ora che il componente è stato aggiunto e inizializzato, è possibile seguire i passaggi generali necessari per la compilazione di App SDK in un'app per dispositivi mobili per iOS. La documentazione completa per l'abilitazione delle app native per iOS è disponibile nella [Guida a Microsoft Intune App SDK per sviluppatori iOS](app-sdk-ios.md).
3. **Importante**: sono disponibili diverse modifiche specifiche delle applicazioni per iOS basate su Xamarin. Ad esempio, quando si abilitano gruppi di portachiavi, è necessario aggiungere il codice seguente per includere l'app di esempio di Xamarin inclusa nel componente. Di seguito è riportato un esempio dei gruppi di cui è necessario disporre nei gruppi di accesso portachiavi:

      ```xml
      <?xml version="1.0" encoding="UTF-8"?>
      <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
      <plist version="1.0">
            <dict>
                  <key>keychain-access-groups</key>
                  <array>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample</string>
                        <string>$(AppIdentifierPrefix)com.xamarin.microsoftintunesample.intunemam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.intune.mam</string>
                        <string>$(AppIdentifierPrefix)com.microsoft.adalcache</string>
                  </array>
            </dict>
      </plist>
      ```

È stata completata la procedura necessaria per compilare il componente in un'app per iOS basata su Xamarin. Se si usa Xcode per la compilazione del progetto, è possibile usare `Intune App SDK Settings.bundle`. In questo modo è possibile attivare e disattivare le impostazioni dei criteri di Intune quando si compila il progetto per il test e il debug. Per sfruttare i vantaggi di questo bundle, seguire i passaggi della [Guida a Microsoft Intune App SDK per sviluppatori iOS](app-sdk-ios.md) e leggere la sezione relativa al [debug in Xcode](app-sdk-ios.md#status-result-and-debug-notifications).

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili Android
Per le app per Android basate su Xamarin che non usano un framework interfaccia utente, è necessario leggere e seguire la [Guida a Microsoft Intune App SDK per sviluppatori Android](app-sdk-android.md). Per l'app per Android basata su Xamarin, è necessario sostituire classe, metodi e attività con i rispettivi equivalenti per MAM in base alla [tabella](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) inclusa nella guida. Se l'app non definisce una classe `android.app.Application`, è necessario crearne una e assicurarsi di ereditare da `MAMApplication`.

Per Xamarin Forms e altri framework interfaccia utente, Microsoft offre uno strumento denominato `MAM.Remapper`, che esegue automaticamente la sostituzione della classe. L'utente deve tuttavia eseguire le operazioni seguenti:

1.  Aggiungere un riferimento al pacchetto NuGet `Microsoft.Intune.MAM.Remapper.Tasks` versione 0.1.0.0 o successiva.

2.  Aggiungere la riga seguente al file csproj per Android:
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Impostare l'azione di compilazione del file `remapping-config.json` aggiunto su **RemappingConfigFile**. Il file `remapping-config.json` incluso può essere usato solo con Xamarin.Forms. Per altri framework interfaccia utente, fare riferimento al file leggimi incluso nel pacchetto NuGet del Remapper.

## <a name="next-steps"></a>Passaggi successivi

Le operazioni principali per la compilazione del componente nell'app sono state completate. A questo punto è possibile seguire i passaggi inclusi nell'app di esempio Xamarin Android. Sono disponibili due esempi, rispettivamente per Xamarin.Forms e per Android.
