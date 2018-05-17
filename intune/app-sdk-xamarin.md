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
ms.openlocfilehash: 5c9f81761e7e24393471f44da4cf619f017e9bbd
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
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

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili Android

### <a name="xamarinandroid-integration"></a>Integrazione di Xamarin.Android

1. Aggiungere la versione più recente del [pacchetto NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) al progetto Xamarin.Android. Il pacchetto mette a disposizione i riferimenti necessari per abilitare l'applicazione per Intune.

2. Leggere e seguire interamente la [Guida a Intune App SDK per Android per gli sviluppatori](app-sdk-android.md), prestando particolare attenzione alle sezioni seguenti:
    1. [Sezione relativa alla sostituzione completa di classi e metodi](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent). 
    2. [Sezione su MAMApplication](app-sdk-android.md#mamapplication). Assicurarsi che la sottoclasse sia decorata correttamente con l'attributo `[Application]` ed esegua l'override del costruttore `(IntPtr, JniHandleOwnership)`.
    3. [Sezione relativa all'integrazione ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) se l'app esegue l'autenticazione ad AAD.
    4. [Sezione sulla registrazione MAM-WE](app-sdk-android.md#app-protection-policy-without-device-enrollment) se si prevede di ottenere criteri dal servizio MAM nell'applicazione.

> [!NOTE]
> Quando si tenta di trovare API equivalenti della [Guida a Intune App SDK per Android per gli sviluppatori](app-sdk-android.md) nei binding `Microsoft.Intune.MAM.Xamarin.Android` o quando si convertono frammenti di codice della guida, tenere presente che il generatore di binding Xamarin modifica le API Android nei modi seguenti:
> * Tutti gli identificatori vengono convertiti in notazione Pascal (com.foo.bar -> Com.Foo.Bar)
> * Tutte le operazioni get/set vengono convertite in operazioni di proprietà (ad esempio Foo.getBar() -> Foo.Bar, Foo.setBar("zap") -> Foo.Bar = "zap")
> * Tutte le interfacce riportano il carattere "I" anteposto al nome (FooInterface -> IFooInterface)

### <a name="xamarinforms-integration"></a>Integrazione di Xamarin.Forms

**Oltre all'esecuzione di tutti i passaggi sopra riportati**, per le applicazioni `Xamarin.Forms` è stato fornito il pacchetto `Microsoft.Intune.MAM.Remapper`. Questo pacchetto esegue la sostituzione delle classi inserendo classi `MAM` nella gerarchia delle classi `Xamarin.Forms` di uso comune, come `FormsAppCompatActivity` e `FormsApplicationActivity`. È quindi possibile continuare a usare queste classi tramite override per le funzioni MAM equivalenti, ad esempio `OnMAMCreate` e `OnMAMResume`. Per usarlo, seguire questa procedura:

1.  Aggiungere il pacchetto NuGet [Microsoft.Intune.MAM.Remapper.Tasks](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) al progetto. In questo modo i binding Xamarin di Intune APP SDK vengono aggiunti automaticamente, se non sono ancora stati aggiunti.

2.  Aggiungere una chiamata a `Xamarin.Forms.Forms.Init(Context, Bundle)` nella funzione `OnMAMCreate` della classe `MAMApplication` creata nel passaggio 2.2 precedente. Questa operazione è necessaria perché con la gestione di Intune è possibile avviare l'applicazione in background.

> [!NOTE]
> Poiché questa operazione riscrive una dipendenza usata da Visual Studio per il completamento automatico di Intellisense, perché Intellisense riconosca correttamente le modifiche può essere necessario riavviare Visual Studio dopo la prima esecuzione del remapper. 

## <a name="support"></a>Support

Se l'organizzazione è un cliente Intune, contattare il rappresentante del supporto tecnico Microsoft per aprire un ticket di supporto e creare una richiesta [nella pagina Github relativa ai problemi](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Il supporto verrà fornito tempestivamente. 