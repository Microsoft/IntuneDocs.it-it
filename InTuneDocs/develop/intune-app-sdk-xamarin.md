---
title: Componente Xamarin per Microsoft Intune App SDK | Microsoft Intune
description: 
keywords: sdk, Xamarin, intune
author: oydang
manager: karthikaraman
ms.author: oydang
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: karthikaraman
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4623db80d711f3543b6d688fb1bb1ef228c62c
ms.openlocfilehash: e2d43fff8772046fe7426b267e39d53b278d4e5c


---

# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin per Microsoft Intune App SDK

## <a name="overview"></a>Panoramica
Il [componente Xamarin per Intune App SDK](https://components.xamarin.com/view/microsoft.intune.mam) consente l'uso delle [funzionalità di gestione delle app per dispositivi mobili di Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) nelle app per iOS e Android compilate con Xamarin. Il componente consente agli sviluppatori di compilare con facilità usando le funzionalità di protezione dei dati e restrizione dell'app nella propria app basata su Xamarin.

Le funzionalità SDK possono essere abilitate senza modificare il comportamento dell'app. Dopo avere compilato il componente nell'app per dispositivi mobili per Android o iOS, l'amministratore IT sarà in grado di distribuire i criteri tramite Microsoft Intune supportando un'ampia gamma di funzionalità che consentono la protezione dei dati.

## <a name="supported-scenarios"></a>Scenari supportati

### <a name="platforms"></a>Piattaforme
* Android
* iOS


### <a name="emm-scenarios"></a>Scenari di EMM

* Funzionalità MAM di Intune in dispositivi registrati MDM di Intune
* Funzionalità MAM di Intune in dispositivi registrati EMM di terze parti
* Funzionalità MAM di Intune in dispositivi non gestiti e non registrati

Le app Xamarin compilate con il componente Xamarin per Intune App SDK possono ora ricevere i criteri di gestione delle applicazioni per dispositivi mobili (MAM) di Intune sia sui dispositivi registrati per la gestione dei dispositivi mobili (MDM) di Intune che su quelli non registrati.

## <a name="prerequisites"></a>Prerequisiti

* **[Solo per Android]** Nel dispositivo deve sempre essere installata l'app Portale aziendale di Microsoft Intune più recente.

## <a name="get-started"></a>Introduzione

1.  Scaricare **Xamarin-component.exe** da [qui](https://components.xamarin.com/submit/xpkg) ed estrarre i file.

2. Leggere le [condizioni di licenza](https://components.xamarin.com/license/microsoft.intune.mam) per il componente Xamarin per le funzionalità MAM di Microsoft Intune.

3.  Scaricare la cartella del componente Xamarin per Intune App SDK da [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) o [Xamarin](https://components.xamarin.com/license/microsoft.intune.mam) ed estrarre i file. Entrambi i file scaricati al passaggio 1 e al passaggio 2 devono essere nello stesso livello di directory.

4.  Nella riga di comando come amministratore eseguire `Xamain.Component.exe install <.xam> file`.

5.  In Visual Studio fare clic con il pulsante destro del mouse sui **componenti** nel progetto Xamarin creato in precedenza.

6.  Selezionare **Modifica componenti** e aggiungere il componente Intune App SDK scaricato localmente nel computer.



## <a name="enabling-intune-mam-in-your-ios-mobile-app"></a>Abilitazione delle funzionalità MAM di Intune nell'app per dispositivi mobili per iOS
1.  Per inizializzare Intune App SDK, è necessario chiamare un'API nella classe `AppDelegate.cs`. Ad esempio:

      ```csharp
      public override bool FinishedLaunching (UIApplication application, NSDictionary launchOptions)
      {
            Console.WriteLine ("Is Managed: {0}", IntuneMAMPolicyManager.Instance.PrimaryUser != null);
            return true;
      }

      ```

2.  Ora che il componente è stato aggiunto e inizializzato, è possibile seguire i passaggi generali necessari per la compilazione di App SDK in un'app per dispositivi mobili per iOS. La documentazione completa per l'abilitazione delle app native per iOS è disponibile nella [Guida a Microsoft Intune App SDK per sviluppatori iOS](intune-app-sdk-ios).
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

È stata completata la procedura necessaria per compilare il componente in un'app per iOS basata su Xamarin. Se si usa Xcode per la compilazione del progetto, è possibile usare `Intune App SDK Settings.bundle`. In questo modo sarà possibile attivare e disattivare le impostazioni dei criteri di Intune quando si compila il progetto per il test e il debug. Per sfruttare i vantaggi di questo bundle, seguire i passaggi della [Guida a Microsoft Intune App SDK per sviluppatori iOS](intune-app-sdk-ios) e leggere la sezione relativa al [debug in Xcode](intune-app-sdk-ios#debug-information).

## <a name="enabling-mam-in-your-android-mobile-app"></a>Abilitazione delle funzionalità MAM nell'app per dispositivi mobili per Android
Per le app per Android basate su Xamarin che non usano un framework interfaccia utente, è necessario leggere e seguire la [Guida a Microsoft Intune App SDK per sviluppatori Android]. Per l'app per Android basata su Xamarin, è necessario sostituire classe, metodi e attività con i rispettivi equivalenti per MAM in base alla [tabella](intune-app-sdk-android#replace-classes-methods-and-activities-with-their-mam-equivalent-required) inclusa nella guida. Se l'app non definisce una classe `android.app.Application`, sarà necessario crearne una e assicurarsi di ereditare da `MAMApplication`.

Per Xamarin Forms e altri framework interfaccia utente, Microsoft offre uno strumento denominato `MAM.Remapper`, che eseguirà automaticamente la sostituzione della classe. L'utente dovrà tuttavia eseguire le operazioni seguenti:

1.  Aggiungere un riferimento al pacchetto NuGet ` Microsoft.Intune.MAM.Remapper.Tasks` versione 0.1.0.0 o successiva.

2.  Aggiungere la riga seguente al file csproj per Android:
  ```xml
  <Import
  Project="$(NugetPack)\\Microsoft.Intune.MAM.Remapper.Tasks.0.1.X.X\\build\\MonoAndroid10\\Microsoft.Intune.MAM.Remapper.targets" />
  ```

3.  Impostare l'azione di compilazione del file `remapping-config.json` aggiunto su **RemappingConfigFile**. Il file `remapping-config.json` incluso può essere usato solo con Xamarin.Forms. Per altri framework interfaccia utente, fare riferimento al file leggimi incluso nel pacchetto NuGet del Remapper.

## <a name="test-your-app"></a>Test dell'app

Le operazioni principali per la compilazione del componente nell'app sono state completate. A questo punto è possibile seguire i passaggi inclusi nell'app di esempio Xamarin Android. Sono disponibili due esempi, rispettivamente per Xamarin.Forms e per Android.



<!--HONumber=Nov16_HO3-->


