---
title: Binding Xamarin per Microsoft Intune App SDK
description: I binding Xamarin per Intune App SDK consentono l'uso dei criteri di protezione delle app di Intune nelle app per iOS e Android compilate con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9f9cc117925f59c9fb7c55d0ff10aedf09d26f93
ms.sourcegitcommit: b727b6bd6f138c5def7ac7bf1658068db30a0ec3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2018
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Binding Xamarin per Microsoft Intune App SDK

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

## <a name="overview"></a>Panoramica
I [binding Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) consentono l'uso dei [criteri di protezione delle app di Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) nelle app per iOS e Android compilate con Xamarin. I binding consentono agli sviluppatori di integrare facilmente le funzionalità di protezione delle app di Intune in un'app basata su Xamarin.

I binding Xamarin per Microsoft Intune App SDK consentono di incorporare i criteri di protezione delle app di Intune, anche noti come criteri APP o MAM, nelle app sviluppate con Xamarin. Un'applicazione abilitata per la gestione delle applicazioni mobili è un'applicazione integrata con Intune App SDK. Gli amministratori IT possono distribuire i criteri di protezione all'app per dispositivi mobili quando Intune gestisce attivamente l'app.

## <a name="whats-supported"></a>Elementi supportati

### <a name="developer-machines"></a>Computer di sviluppo
* Windows
* macOS


### <a name="mobile-app-platforms"></a>Piattaforme di app per dispositivi mobili
* Android
* iOS


### <a name="intune-mobile-application-management-scenarios"></a>Scenari di gestione di applicazioni mobili di Intune

* Intune APP-WE (senza registrazione del dispositivo)
* Dispositivi registrati MDM di Intune
* Dispositivi registrati EMM di terze parti

Le app Xamarin compilate con i binding Xamarin per Intune App SDK possono ora ricevere i criteri di protezione delle app di Intune nei dispositivi registrati in Gestione dei dispositivi mobili di Intune e nei dispositivi non registrati.

## <a name="prerequisites"></a>Prerequisiti

Leggere le [condizioni di licenza](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando i binding Xamarin per Intune App SDK, l'utente accetta tali condizioni di licenza. Se non vengono accettate, non usare il software.

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili iOS
1. Aggiungere il [pacchetto Microsoft.Intune.MAM.Xamarin.iOS NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) al progetto Xamarin.iOS.
2.  Seguire i passaggi generali necessari per l'integrazione di Intune App SDK in un'app per dispositivi mobili iOS. È possibile iniziare dal passaggio 3 delle istruzioni di integrazione nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). È possibile ignorare il passaggio finale della sezione sull'esecuzione di IntuneMAMConfigurator poiché lo strumento è incluso nel pacchetto Microsoft.Intune.MAM.Xamarin.iOS e verrà eseguito automaticamente in fase di compilazione.
    **Importante**: l'abilitazione della condivisione del keychain per un'app è leggermente diversa in Visual Studio rispetto a Xcode. Aprire il file Entitlements.plist dell'app e assicurarsi che l'opzione "Abilita Keychain" sia abilitata e che in tale sezione vengano aggiunti i gruppi di condivisione del keychain appropriati. Assicurarsi quindi di specificare il file Entitlements.plist nel campo "Entitlement personalizzati" delle opzioni "Firma del bundle iOS" del progetto per tutte le combinazioni di configurazione/piattaforma appropriate.
3.  Dopo l'aggiunta dei binding e la corretta configurazione dell'app, quest'ultima potrà iniziare a usare le API di Intune SDK. A tale scopo, è necessario includere lo spazio dei nomi seguente:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Per iniziare a ricevere i criteri di protezione delle app, è necessario registrare l'app nel servizio MAM di Intune. Se l'app usa già la libreria ADAL (Azure Active Directory Authentication Library) per l'autenticazione degli utenti, l'app deve fornire l'UPN dell'utente al metodo registerAndEnrollAccount di IntuneMAMEnrollmentManager dopo che è stato autenticato:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      **Importante**: assicurarsi di sostituire le impostazioni predefinite per la libreria ADAL di Intune App SDK con quelle dell'app. È possibile farlo tramite il dizionario IntuneMAMSettings nel file Info.plist dell'app, come indicato nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) oppure è possibile usare le proprietà di sostituzione AAD dell'istanza IntuneMAMPolicyManager. L'approccio che prevede il file Info.plist è consigliato per applicazioni con impostazioni ADAL statiche, mentre le proprietà di sostituzione sono consigliate per le applicazioni che determinano questi valori in fase di esecuzione. 
      
      Se l'app non usa ADAL e si vuole gestire l'autenticazione con Intune SDK, l'app deve chiamare il metodo loginAndEnrollAccount di IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

## <a name="enabling-app-protection-policies-in-your-android-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili Android
Aggiungere il [pacchetto Microsoft.Intune.MAM.Xamarin.Android NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) al progetto Xamarin.Android.

Per le app Xamarin.Android è necessario leggere la [Guida a Microsoft Intune App SDK per sviluppatori di Android](app-sdk-android.md) e seguire tutte le istruzioni fornite, inclusa la sostituzione di classi, metodi e attività con il rispettivo equivalente MAM in base alla [tabella](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) disponibile nella guida. 

> [!NOTE]
> Se l'app non definisce una classe `android.app.Application`, è necessario crearne una e assicurarsi di ereditare da `MAMApplication`.

> [!NOTE]
> Quando si tenta di trovare le API equivalenti della [Guida a Microsoft Intune App SDK per sviluppatori di Android](app-sdk-android.md) nei binding `Microsoft.Intune.MAM.Xamarin.Android` o di convertire i frammenti di codice della guida, tenere presente che il generatore di binding Xamarin modifica le API Android nei modi seguenti:
> * Tutti gli identificatori vengono convertiti in maiuscole/minuscole Pascale (com.microsoft.foo -> Com.Microsoft.Foo)
> * Tutte le operazioni get/set vengono convertite in operazioni di proprietà (ad esempio Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * Tutte le interfacce riportano il carattere "I" anteposto al nome (FooInterface -> IFooInterface)

Per le app che usano Xamarin.Forms o altri framework interfaccia utente, Microsoft offre uno strumento denominato `Microsoft.Intune.MAM.Remapper` che esegue automaticamente la sostituzione della classe. Per usarlo, seguire questa procedura:

1.  Aggiungere il pacchetto NuGet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) al progetto.

2.  Impostare l'azione di compilazione del file `remapping-config.json` incluso nel pacchetto Nuget su **RemappingConfigFile**. Il file `remapping-config.json` incluso può essere usato solo con Xamarin.Forms. Per altri framework interfaccia utente, fare riferimento al file leggimi incluso nel pacchetto NuGet del Remapper.

3.  Aggiungere una chiamata a Xamarin.Forms.Forms.Init(Context, Bundle) nella funzione OnMAMCreate di MAMApplication perché, con la gestione Intune, è possibile avviare l'applicazione mentre è in background.

4.  Eseguire il resto dei passaggi descritti nella [Guida a Microsoft Intune App SDK per sviluppatori di Android](app-sdk-android.md) applicabili all'app.

> [!NOTE]
> Quando si aggiorna il pacchetto Microsoft.Intune.MAM.Remapper.Tasks, l'azione di compilazione remapping-config.json può a volte essere reimpostata determinando errori nelle build.

## <a name="next-steps"></a>Passaggi successivi

I passaggi di base per la configurazione dell'app per la gestione Intune sono stati completati. Ora è possibile seguire i passaggi illustrati nelle guide all'integrazione per ognuna delle piattaforme precedentemente indicate.

Se l'organizzazione è un cliente Intune, contattare il rappresentante del supporto tecnico Microsoft per aprire un ticket di supporto e creare una richiesta [nella pagina Github relativa ai problemi](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Il supporto verrà fornito tempestivamente. 