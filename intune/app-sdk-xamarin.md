---
title: Binding Xamarin per Microsoft Intune App SDK
description: I binding Xamarin per Intune App SDK consentono l'uso dei criteri di protezione delle app di Intune nelle app per iOS e Android compilate con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/08/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: d42fab929d6fa3e7fbaed8e9557573ebbaa1f3ad
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59292351"
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

Leggere le [condizioni di licenza](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20Xamarin%20Component.pdf). Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando i binding Xamarin per Intune App SDK, l'utente accetta tali condizioni di licenza. Qualora l'utente non le accetti, non potrà usare il software.

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

1. Aggiungere il [pacchetto Microsoft.Intune.MAM.Xamarin.Android NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) al progetto Xamarin.Android.
    1. Per un'app xamarin. Forms, aggiungere il [mobileengagement Remapper](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) anche al progetto xamarin. Android. 
2. Seguire i passaggi generali necessari per [l'integrazione di Intune App SDK](app-sdk-android.md) in un'app per dispositivi mobili Android per il riferimento a questo documento per altri dettagli.

### <a name="xamarinandroid-integration"></a>Integrazione di Xamarin.Android

Una panoramica completa per l'integrazione di Intune App SDK è reperibile nella [Microsoft Intune App SDK per la Guida per sviluppatori Android](app-sdk-android.md). Leggere la Guida e integrare Intune App SDK con l'app Xamarin le sezioni seguenti sono progettate per evidenziare le differenze tra l'implementazione per un'app Android native sviluppato in Java e ha sviluppato un'app Xamarin in C#. Queste sezioni devono essere considerate come supplementare e non può essere usata in sostituzione di leggere la Guida nel suo complesso.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Metodi rinominati](app-sdk-android.md#renamed-methods)
In molti casi, un metodo disponibile nella classe Android è stato contrassegnato come finale nella classe sostitutiva MAM. In questo caso, la classe sostitutiva MAM fornisce un metodo denominato in modo analogo (con suffisso `MAM`), che deve essere sostituito al suo posto. Ad esempio, quando si deriva da `MAMActivity`, invece di sostituire `OnCreate()` e chiamare `base.OnCreate()`, la classe `Activity` deve sostituire `OnMAMCreate()` e chiamare `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Applicazione MAM](app-sdk-android.md#mamapplication)
L'app è necessario definire un' `Android.App.Application` classe che eredita da `MAMApplication`. Assicurarsi che la sottoclasse sia decorata correttamente con l'attributo `[Application]` ed esegua l'override del costruttore `(IntPtr, JniHandleOwnership)`.
```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```
> [!NOTE]
> Un problema con i binding Xamarin MAM può causare arresti anomali quando vengono distribuiti in modalità di Debug. In alternativa, il `Debuggable=false` attributo deve essere aggiunto al `Application` classe e il `android:debuggable="true"` flag deve essere rimossi dal manifesto se è stato impostato manualmente.

#### <a name="enable-features-that-require-app-participationapp-sdk-androidmdenable-features-that-require-app-participation"></a>[Abilitare le funzionalità che richiedono la partecipazione dell'app](app-sdk-android.md#enable-features-that-require-app-participation)
Esempio: determinare se è necessario il PIN per l'app
```csharp
MAMPolicyManager.GetPolicy(currentActivity).IsPinRequired;
```
Esempio: determinare l'utente primario di Intune
```csharp
IMAMUserInfo info = MAMComponents.Get<IMAMUserInfo>();
return info?.PrimaryUser;
```
Esempio: determinare se il salvataggio nel dispositivo o in un servizio di archiviazione cloud è consentito
```csharp
MAMPolicyManager.GetPolicy(currentActivity).GetIsSaveToLocationAllowed(SaveLocation service, String username);
```

#### <a name="register-for-notifications-from-the-sdkapp-sdk-androidmdregister-for-notifications-from-the-sdk"></a>[Eseguire la registrazione per le notifiche dall'SDK](app-sdk-android.md#register-for-notifications-from-the-sdk)
L'app deve eseguire la registrazione per le notifiche dall'SDK creando un oggetto `MAMNotificationReceiver` e registrandolo con `MAMNotificationReceiverRegistry`. Ciò avviene specificando il ricevente e il tipo di notifica desiderato in `App.OnMAMCreate`, come nell'esempio seguente:
```csharp
public override void OnMAMCreate()
{
    // Register the notification receivers
    IMAMNotificationReceiverRegistry registry = MAMComponents.Get<IMAMNotificationReceiverRegistry>();
    foreach (MAMNotificationType notification in MAMNotificationType.Values())
    {
    registry.RegisterReceiver(new ToastNotificationReceiver(this), notification);
    }
    ...
```

#### <a name="mam-enrollment-managerapp-sdk-androidmdmamenrollmentmanager"></a>[Manager di registrazione MAM](app-sdk-android.md#mamenrollmentmanager)
```csharp
IMAMEnrollmentManager mgr = MAMComponents.Get<IMAMEnrollmentManager>();
```

### <a name="xamarinforms-integration"></a>Integrazione di Xamarin.Forms

Per `Xamarin.Forms` le applicazioni sono disponibili le `Microsoft.Intune.MAM.Remapper` pacchetto da eseguire automaticamente la sostituzione di classe MAM inserendo `MAM` classi nella gerarchia delle classi di uso comune `Xamarin.Forms` classi. 

> [!NOTE]
> L'integrazione di xamarin. Forms è necessario eseguire anche l'integrazione di xamarin. Android come indicato in precedenza.

Dopo aver aggiunto al progetto il Remapper dovrai eseguire le sostituzioni equivalente MAM. Ad esempio, `FormsAppCompatActivity` e `FormsApplicationActivity` possono continuare a usare l'override dell'applicazione fornito per `OnCreate` e `OnResume` vengono sostituiti con gli equivalenti MAM `OnMAMCreate` e `OnMAMResume` rispettivamente.

```csharp
    public class MainActivity : global::Xamarin.Forms.Platform.Android.FormsAppCompatActivity
    {
        protected override void OnMAMCreate(Bundle savedInstanceState)
        {
            base.OnMAMCreate(savedInstanceState);
            global::Xamarin.Forms.Forms.Init(this, savedInstanceState);
            LoadApplication(new App());
        }
```
Se non vengono apportate le sostituzioni è possibile riscontrare gli errori di compilazione seguenti finché non si apportano le sostituzioni:
* [Errore del compilatore CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). questo errore in genere è visualizzato in questo formato ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
È previsto perché quando lo strumento di modifica del mapping modifica l'ereditarietà delle classi Xamarin, determinate funzioni vengono rese `sealed` e viene aggiunta una nuova variante MAM per eseguire l'override.
* [Errore del compilatore CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): questo errore si verifica in genere in questo formato ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Quando lo strumento di modifica del mapping cambia l'ereditarietà di alcune classi di Xamarin, determinate funzioni membro vengono modificate in `public`. Se si esegue l'override di uno qualsiasi di queste funzioni, sarà necessario cambiare i modificatori di accesso per le sostituzioni per essere `public` anche.

> [!NOTE]
> Il Remapper riscrive una dipendenza utilizzata da Visual Studio per il completamento automatico IntelliSense. Di conseguenza, potrebbe essere necessario ricaricare e ricompilare il progetto quando viene aggiunto il Remapper per IntelliSense riconoscere correttamente le modifiche.

## <a name="support"></a>Supporto
Se l'organizzazione è un cliente Intune, contattare il rappresentante del supporto tecnico Microsoft per aprire un ticket di supporto e creare una richiesta [nella pagina Github relativa ai problemi](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). Il supporto verrà fornito tempestivamente. 
