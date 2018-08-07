---
title: Binding Xamarin per Microsoft Intune App SDK
description: I binding Xamarin per Intune App SDK consentono l'uso dei criteri di protezione delle app di Intune nelle app per iOS e Android compilate con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
manager: dougeby
ms.author: erikre
ms.date: 06/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1cfbaa0cbdcc2263f6e8d1d3fc8562678e410537
ms.sourcegitcommit: e8aaa0955d13fa6c9d5f35a730ad06509ce88d0b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/01/2018
ms.locfileid: "39400318"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Binding Xamarin per Microsoft Intune App SDK

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

## <a name="overview"></a>Panoramica
I [binding Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) consentono l'uso dei [criteri di protezione delle app di Intune](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) nelle app per iOS e Android compilate con Xamarin. I binding consentono agli sviluppatori di integrare facilmente le funzionalità di protezione delle app di Intune in un'app basata su Xamarin.

I binding Xamarin per Microsoft Intune App SDK consentono di incorporare i criteri di protezione delle app di Intune, anche noti come criteri APP o MAM, nelle app sviluppate con Xamarin. Un'applicazione abilitata per la gestione delle applicazioni mobili è un'applicazione integrata con Intune App SDK. Gli amministratori IT possono distribuire i criteri di protezione all'app per dispositivi mobili quando Intune gestisce attivamente l'app.

## <a name="whats-supported"></a>Elementi supportati

### <a name="developer-machines"></a>Computer di sviluppo
* Windows (Visual Studio versione 15.7+)
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
      
> [!NOTE] 
> Non è disponibile alcun remapper per iOS. L'integrazione in un'app Xamarin.Forms deve essere identica a quella di un progetto Xamarin.iOS regolare. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili Android

Per le app per Android basate su Xamarin che non usano un framework interfaccia utente, è necessario leggere e seguire la [Guida a Microsoft Intune App SDK per sviluppatori Android](app-sdk-android.md). Per l'app per Android basata su Xamarin, è necessario sostituire classe, metodi e attività con i rispettivi equivalenti per MAM in base alla [tabella](app-sdk-android.md#replace-classes-methods-and-activities-with-their-mam-equivalent) inclusa nella guida. Se l'app non definisce una classe `android.app.Application`, è necessario crearne una e assicurarsi di ereditare da `MAMApplication`.

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

Le operazioni principali per la compilazione del componente nell'app sono state completate. A questo punto è possibile seguire i passaggi inclusi nell'app di esempio Xamarin Android. Sono disponibili due esempi, rispettivamente per Xamarin.Forms e per Android.

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Richiesta di criteri di protezione delle app di Intune per l'uso dell'app di Android LOB basata su Xamarin (facoltativo) 

Il materiale sussidiario offerto di seguito consente di verificare che le app di Android LOB basate su Xamarin possano essere usate solo dagli utenti protetti da Intune sul loro dispositivo. 

### <a name="general-requirements"></a>Requisiti generali
* Il team di Intune SDK richiederà l'ID applicazione dell'app. Si può trovare questo elemento nel [portale di Azure](https://portal.azure.com/) in **Tutte le applicazioni**, colonna **ID applicazione**. Un buon metodo per contattare il team di Intune SDK è tramite l'invio di un messaggio di posta elettronica all'indirizzo msintuneappsdk@microsoft.com.
     
### <a name="working-with-the-intune-sdk"></a>Uso di Intune SDK
Queste istruzioni sono specifiche per tutte le app Android e Xamarin che richiederanno i criteri di protezione delle app Intune per l'uso nel dispositivo di un utente finale.

1. Configurare ADAL usando i passaggi definiti nella [Guida a Intune SDK per Android](https://docs.microsoft.com/en-us/intune/app-sdk-android#configure-azure-active-directory-authentication-library-adal).
> [!NOTE] 
> Il termine "ID client" equivale al termine "ID applicazione" del portale di Azure associato all'app. 
* Per abilitare SSO, vedere il punto 2 della sezione "Configurazioni comuni di ADAL".

2. Abilitare la registrazione predefinita inserendo il valore seguente nel manifesto: ```xml <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />```
> [!NOTE] 
> Questa deve essere l'unica integrazione MAM-WE nell'app. Altri tentativi di chiamare le API MAMEnrollmentManager possono determinare conflitti.

3. Abilitare i criteri MAM richiesti inserendo il valore seguente nel manifesto: ```xml <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />```
> [!NOTE] 
> In questo modo, l'app viene obbligata a scaricare il Portale aziendale nel dispositivo e completare le fasi della registrazione predefinita prima dell'uso.

### <a name="working-with-adal"></a>Uso di ADAL
Queste istruzioni sono specifiche per le app .NET e Xamarin che richiedono i criteri di protezione delle app Intune per l'uso nel dispositivo di un utente finale.

1. Seguire tutti i passaggi definiti nella documentazione di ADAL in [Brokered Authentication for Android](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/tree/dev/adal#brokered-authentication-for-android) (Autenticazione negoziata per Android).
> [!NOTE] 
> La versione che ADAL .NET rilascerà prossimamente (3.17.4) conterrà la correzione necessaria per eseguire questa operazione.

Se l'organizzazione è un cliente Intune, contattare il rappresentante del supporto tecnico Microsoft per aprire un ticket di supporto e creare una richiesta [nella pagina Github relativa ai problemi](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Il supporto verrà fornito tempestivamente. 

