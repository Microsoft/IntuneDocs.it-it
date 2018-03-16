---
title: Componente Xamarin per Microsoft Intune App SDK
description: Il componente Xamarin per Intune App SDK consente l'uso dei criteri di protezione delle app di Intune nelle app per iOS e Android compilate con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9fa0d471f91eeeebd0058417aa437e5469f48e09
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-component"></a>Componente Xamarin per Microsoft Intune App SDK

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

## <a name="overview"></a>Panoramica
Il [componente Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) consente l'uso dei [criteri di protezione delle app di Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) nelle app per iOS e Android compilate con Xamarin. Il componente consente agli sviluppatori di creare con facilità le funzionalità di protezione dell'app Intune nella propria app basata su Xamarin.

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

## <a name="get-started"></a>Operazioni preliminari

1.  Scaricare **Xamarin-component.exe** da [qui](https://components.xamarin.com/submit/xpkg) ed estrarre i file.

2. Leggere le [condizioni di licenza](https://components.xamarin.com/license/microsoft.intune.mam) per il componente Xamarin per le funzionalità MAM di Microsoft Intune.

3.  Scaricare la cartella del componente Xamarin per Intune App SDK da [GitHub](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) o [Nuget.org](https://www.nuget.org/profiles/msintuneappsdk) ed estrarre i file. Entrambi i file scaricati al passaggio 1 e al passaggio 3 devono essere nello stesso livello di directory.

4.  Nella riga di comando come amministratore eseguire `mono Xamarin.Component.exe install <.xam> file`.

5.  In Visual Studio fare clic con il pulsante destro del mouse sui **componenti** nel progetto Xamarin creato in precedenza.

6.  Selezionare **Modifica componenti** e aggiungere il componente Intune App SDK scaricato localmente nel computer.



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili iOS
1.  Seguire i passaggi generali necessari per l'integrazione di Intune App SDK in un'app per dispositivi mobili iOS. È possibile iniziare dal passaggio 3 delle istruzioni di integrazione nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app).
    **Importante**: l'abilitazione della condivisione del keychain per un'app è leggermente diversa in Visual Studio rispetto a Xcode. Aprire il file Entitlements.plist dell'app e assicurarsi che l'opzione "Abilita Keychain" sia abilitata e che in tale sezione vengano aggiunti i gruppi di condivisione del keychain appropriati. Assicurarsi quindi di specificare il file Entitlements.plist nel campo "Entitlement personalizzati" delle opzioni "Firma del bundle iOS" del progetto per tutte le combinazioni di configurazione/piattaforma appropriate.
2.  Dopo l'aggiunta del componente e quando l'app è configurata correttamente, l'app può iniziare a usare le API di Intune SDK. A tale scopo, è necessario includere lo spazio dei nomi seguente:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
3.    Per iniziare a ricevere i criteri di protezione delle app, è necessario registrare l'app nel servizio MAM di Intune. Se l'app usa già la libreria ADAL (Azure Active Directory Authentication Library) per l'autenticazione degli utenti, l'app deve fornire l'UPN dell'utente al metodo registerAndEnrollAccount di IntuneMAMEnrollmentManager dopo che è stato autenticato:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Importante**: assicurarsi di sostituire le impostazioni predefinite per la libreria ADAL di Intune App SDK con quelle dell'app. È possibile farlo tramite il dizionario IntuneMAMSettings nel file Info.plist dell'app, come indicato nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) oppure è possibile usare le proprietà di sostituzione AAD dell'istanza IntuneMAMPolicyManager. L'approccio che prevede il file Info.plist è consigliato per applicazioni con impostazioni ADAL statiche, mentre le proprietà di sostituzione sono consigliate per le applicazioni che determinano questi valori in fase di esecuzione. 
      
      Se l'app non usa ADAL e si vuole gestire l'autenticazione con Intune SDK, l'app deve chiamare il metodo loginAndEnrollAccount di IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

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
