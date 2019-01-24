---
title: Binding Xamarin per Microsoft Intune App SDK
description: I binding Xamarin per Intune App SDK consentono l'uso dei criteri di protezione delle app di Intune nelle app per iOS e Android compilate con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: 65a461928c377dd4a674f8f3f2eeeef148ab56b2
ms.sourcegitcommit: 912aee714432c4a1e8efeee253ca2be4f972adaa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316900"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Binding Xamarin per Microsoft Intune App SDK

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

## <a name="overview"></a>Panoramica
I [binding Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) consentono l'uso dei [criteri di protezione delle app di Intune](app-protection-policy.md) nelle app per iOS e Android compilate con Xamarin. I binding consentono agli sviluppatori di integrare facilmente le funzionalità di protezione delle app di Intune in un'app basata su Xamarin.

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

L'SDK si basa su [Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) per gli scenari di [autenticazione](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) e avvio condizionale, che richiedono la configurazione delle app con [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Se l’applicazione è già configurata per l’uso di ADAL o MSAL e se per l’autenticazione con Azure Active Directory viene utilizzato il relativo ID client personalizzato, attenersi alla procedura per assegnare le autorizzazioni dell’app Xamarin al servizio Gestione di applicazioni mobili di Intune (MAM). Usare le istruzioni riportate nella sezione [Concedere all'app l'accesso al servizio di protezione delle app di Intune](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional) in [Introduzione a Microsoft Intune SDK](app-sdk-get-started.md).

## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili iOS
1. Aggiungere il [pacchetto Microsoft.Intune.MAM.Xamarin.iOS NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) al progetto Xamarin.iOS.
2.  Seguire i passaggi generali necessari per l'integrazione di Intune App SDK in un'app per dispositivi mobili iOS. È possibile iniziare dal passaggio 3 delle istruzioni di integrazione nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). È possibile ignorare il passaggio finale della sezione sull'esecuzione di IntuneMAMConfigurator poiché lo strumento è incluso nel pacchetto Microsoft.Intune.MAM.Xamarin.iOS e verrà eseguito automaticamente in fase di compilazione.
    **Importante**: l'abilitazione della condivisione del keychain per un'app è leggermente diversa in Visual Studio rispetto a Xcode. Aprire il file Entitlements.plist dell'app e assicurarsi che l'opzione "Abilita Keychain" sia abilitata e che in tale sezione vengano aggiunti i gruppi di condivisione del keychain appropriati. Assicurarsi quindi di specificare il file Entitlements.plist nel campo "Entitlement personalizzati" delle opzioni "Firma del bundle iOS" del progetto per tutte le combinazioni di configurazione/piattaforma appropriate.
3.  Dopo l'aggiunta dei binding e la corretta configurazione dell'app, quest'ultima potrà iniziare a usare le API di Intune SDK. A tale scopo, è necessario includere lo spazio dei nomi seguente:

      ```csharp
      using Microsoft.Intune.MAM;
      ```
4. Per iniziare a ricevere i criteri di protezione delle app, è necessario registrare l'app nel servizio MAM di Intune. Se l'app non usa [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) o [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) per l'autenticazione degli utenti e si vuole che l'autenticazione venga gestita da Intune SDK, è necessario che l'app fornisca l'UPN dell'utente al metodo LoginAndEnrollAccount di IntuneMAMEnrollmentManager:
      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```
      Se al momento della chiamata l'UPN dell'utente non è noto, è possibile che le app passino un valore Null. In questo caso verrà richiesto agli utenti di immettere l'indirizzo di posta elettronica e la password.
      
      Se l'app usa già ADAL o MSAL per l'autenticazione degli utenti, è possibile configurare un accesso Single Sign-On (SSO) tra l'app e Intune SDK. Innanzitutto, sarà necessario configurare ADAL/MSAL per archiviare i token nello stesso gruppo di accesso keychain usato dai binding Intune Xamarin per iOS (com.microsoft.adalcache). Per ADAL, è possibile eseguire questa operazione [impostando la proprietà KeychainSecurityGroup di AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/Token-cache-serialization#enable-token-cache-sharing-across-ios-applications). Per MSAL, è necessario [impostare la proprietà KeychainSecurityGroup di PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/msal-net-2-released#you-can-now-enable-sso-between-adal-and-msal-apps-on-xamarinios). Successivamente sarà necessario eseguire l'override delle impostazioni di AAD predefinite usate da Intune SDK con quelle dell'app. È possibile farlo tramite il dizionario IntuneMAMSettings nel file Info.plist dell'app, come indicato nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) oppure è possibile usare le proprietà di sostituzione AAD dell'istanza IntuneMAMPolicyManager. L'approccio che prevede il file Info.plist è consigliato per applicazioni con impostazioni ADAL statiche, mentre le proprietà di sostituzione sono consigliate per le applicazioni che determinano questi valori in fase di esecuzione. Dopo aver configurato tutte le impostazioni SSO, l'app dovrebbe fornire l'UPN dell'utente al metodo RegisterAndEnrollAccount di IntuneMAMEnrollmentManager dopo essere stata autenticata:
      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```
      Le app possono determinare il risultato di un tentativo di registrazione implementando il metodo EnrollmentRequestWithStatus in una sottoclasse di IntuneMAMEnrollmentDelegate e impostando la proprietà Delegate di IntuneMAMEnrollmentManager su un'istanza della classe. Per un esempio, vedere l'[applicazione Xamarin.iOS di esempio](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

      Dopo aver eseguito la registrazione, le app possono determinare l'UPN dell'account registrato (se precedentemente sconosciuto) eseguendo una query nella proprietà seguente: 
      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
> [!NOTE] 
> Non è disponibile alcun remapper per iOS. L'integrazione in un'app Xamarin.Forms deve essere identica a quella di un progetto Xamarin.iOS regolare. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili Android

Per le app per Android basate su Xamarin che non usano un framework interfaccia utente, è necessario leggere e seguire la [Guida a Microsoft Intune App SDK per sviluppatori Android](app-sdk-android.md). Per l'app per Android basata su Xamarin, è necessario sostituire classe, metodi e attività con i rispettivi equivalenti per MAM in base alla [tabella delle sostituzioni di classi e metodi](app-sdk-android.md#class-and-method-replacements) inclusa nella guida. Se l'app non definisce una classe `android.app.Application`, è necessario crearne una e assicurarsi di ereditare da `MAMApplication`. I valori di configurazione ADAL vengono comunicati all'SDK tramite i metadati di AndroidManifest. Leggere la documentazione in merito alla [configurazione di ADAL per l'app](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).

### <a name="xamarinandroid-integration"></a>Integrazione di Xamarin.Android

1. Aggiungere la versione più recente del [pacchetto NuGet Microsoft.Intune.MAM.Xamarin.Android](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) al progetto Xamarin.Android. Il pacchetto mette a disposizione i riferimenti necessari per abilitare l'applicazione per Intune.

2. Leggere e seguire interamente la [Guida a Intune App SDK per Android per gli sviluppatori](app-sdk-android.md), prestando particolare attenzione alle sezioni seguenti:

    1. [Sezione relativa alla sostituzione completa di classi e metodi](app-sdk-android.md#class-and-method-replacements). 
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

2.  Aggiungere una chiamata a `Xamarin.Forms.Forms.Init(Context, Bundle)` nella funzione `OnMAMActivity` della classe `MAMApplication` creata nel passaggio 2.2 precedente. Questa operazione è necessaria perché con la gestione di Intune è possibile avviare l'applicazione in background.

> [!NOTE]
> Poiché questa operazione riscrive una dipendenza usata da Visual Studio per il completamento automatico di Intellisense, perché Intellisense riconosca correttamente le modifiche può essere necessario riavviare Visual Studio dopo la prima esecuzione del remapper. 

## <a name="requiring-intune-app-protection-policies-in-order-to-use-your-xamarin-based-android-lob-app-optional"></a>Richiesta di criteri di protezione delle app di Intune per l'uso dell'app di Android LOB basata su Xamarin (facoltativo) 

Il materiale sussidiario offerto di seguito consente di verificare che le app di Android LOB basate su Xamarin possano essere usate solo dagli utenti protetti da Intune sul loro dispositivo. 
    
### <a name="working-with-the-intune-sdk"></a>Uso di Intune SDK
Queste istruzioni sono specifiche per tutte le app Android e Xamarin che richiederanno i criteri di protezione delle app Intune per l'uso nel dispositivo di un utente finale.

1. Configurare ADAL usando i passaggi definiti nella [Guida a Intune SDK per Android](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal).
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

## <a name="potential-compilation-errors"></a>Potenziali errori di compilazione
Di seguito sono riportati alcuni degli errori di compilazione che appaiono più di frequente durante lo sviluppo di un'applicazione basata su Xamarin.

* [Errore del compilatore CS0239](https://docs.microsoft.com/en-us/dotnet/csharp/misc/cs0239): questo errore in genere è visualizzato in questo formato ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
Quando lo strumento di modifica del mapping modifica l'ereditarietà delle classi Xamarin, alcune funzioni vengono rese `sealed` e viene aggiunta una nuova variante MAM per eseguire l'override. È sufficiente rinominare le sostituzioni come descritto [qui](https://docs.microsoft.com/en-us/intune/app-sdk-android#renamed-methods). Ad esempio `MainActivity.OnCreate()` viene rinominata in `MainActivity.OnMAMCreate()`

* [Errore del compilatore CS0507](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/compiler-messages/cs0507): questo errore in genere è visualizzato in questo formato ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Se lo strumento di modifica del mapping cambia l'ereditarietà di alcune classi di Xamarin, alcune delle funzioni membro vengono modificate in `public`. Se si sostituiscono queste funzioni, può essere necessario modificare anche quelle sostituzioni in modo che siano `public`.

## <a name="support"></a>Support
Se l'organizzazione è un cliente Intune, contattare il rappresentante del supporto tecnico Microsoft per aprire un ticket di supporto e creare una richiesta [nella pagina Github relativa ai problemi](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Il supporto verrà fornito tempestivamente. 
