---
title: Binding Xamarin per Microsoft Intune App SDK
description: I binding Xamarin per Intune App SDK consentono l'uso dei criteri di protezione delle app di Intune nelle app per iOS e Android compilate con Xamarin.
keywords: sdk, Xamarin, intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 275d574b-3560-4992-877c-c6aa480717f4
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: de367f28f3f1c7731e5ab67d904aec799925cc03
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733725"
---
# <a name="microsoft-intune-app-sdk-xamarin-bindings"></a>Binding Xamarin per Microsoft Intune App SDK

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

## <a name="overview"></a>Panoramica
I [binding Xamarin per Intune App SDK](https://github.com/msintuneappsdk/intune-app-sdk-xamarin) consentono l'uso dei [criteri di protezione delle app di Intune](../apps/app-protection-policy.md) nelle app per iOS e Android compilate con Xamarin. I binding consentono agli sviluppatori di integrare facilmente le funzionalità di protezione delle app di Intune in un'app basata su Xamarin.

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

Intune SDK si basa su [Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) per gli scenari di [autenticazione](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) e avvio condizionale, che richiedono la configurazione delle app con [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). 

Se l’applicazione è già configurata per l’uso di ADAL o MSAL e se per l’autenticazione con Azure Active Directory viene utilizzato il relativo ID client personalizzato, attenersi alla procedura per assegnare le autorizzazioni dell’app Xamarin al servizio Gestione di applicazioni mobili di Intune (MAM). Usare le istruzioni riportate nella sezione [Concedere all'app l'accesso al servizio di protezione delle app di Intune](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional) in [Introduzione a Microsoft Intune SDK](app-sdk-get-started.md).



## <a name="enabling-intune-app-protection-polices-in-your-ios-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili iOS
1. Aggiungere il [pacchetto Microsoft.Intune.MAM.Xamarin.iOS NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.iOS) al progetto Xamarin.iOS.
2. Seguire i passaggi generali necessari per l'integrazione di Intune App SDK in un'app per dispositivi mobili iOS. È possibile iniziare dal passaggio 3 delle istruzioni di integrazione nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#build-the-sdk-into-your-mobile-app). È possibile ignorare il passaggio finale della sezione sull'esecuzione di IntuneMAMConfigurator poiché lo strumento è incluso nel pacchetto Microsoft.Intune.MAM.Xamarin.iOS e verrà eseguito automaticamente in fase di compilazione.
    **Importante**: l'abilitazione della condivisione del keychain per un'app è leggermente diversa in Visual Studio rispetto a Xcode. Aprire il file Entitlements.plist dell'app e assicurarsi che l'opzione "Abilita Keychain" sia abilitata e che in tale sezione vengano aggiunti i gruppi di condivisione del keychain appropriati. Assicurarsi quindi di specificare il file Entitlements.plist nel campo "Entitlement personalizzati" delle opzioni "Firma del bundle iOS" del progetto per tutte le combinazioni di configurazione/piattaforma appropriate.
3. Dopo l'aggiunta dei binding e la corretta configurazione dell'app, quest'ultima potrà iniziare a usare le API di Intune SDK. A tale scopo, è necessario includere lo spazio dei nomi seguente:

      ```csharp
      using Microsoft.Intune.MAM;
      ```

4. Per iniziare a ricevere i criteri di protezione delle app, è necessario registrare l'app nel servizio MAM di Intune. Se l'app non usa [Azure Active Directory Authentication Library](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) (ADAL) o [Microsoft Authentication Library](https://www.nuget.org/packages/Microsoft.Identity.Client) (MSAL) per l'autenticazione degli utenti e si vuole che l'autenticazione venga gestita da Intune SDK, è necessario che l'app fornisca l'UPN dell'utente al metodo LoginAndEnrollAccount di IntuneMAMEnrollmentManager:

      ```csharp
       IntuneMAMEnrollmentManager.Instance.LoginAndEnrollAccount([NullAllowed] string identity);
      ```

      Se al momento della chiamata l'UPN dell'utente non è noto, è possibile che le app passino un valore Null. In questo caso verrà richiesto agli utenti di immettere l'indirizzo di posta elettronica e la password.
      
      Se l'app usa già ADAL o MSAL per l'autenticazione degli utenti, è possibile configurare un accesso Single Sign-On (SSO) tra l'app e Intune SDK. Innanzitutto, sarà necessario configurare ADAL/MSAL per archiviare i token nello stesso gruppo di accesso keychain usato dai binding Intune Xamarin per iOS (com.microsoft.adalcache). Per ADAL è possibile eseguire questa operazione [impostando la proprietà iOSKeychainSecurityGroup di AuthenticationContext](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet/wiki/iOS-Keychain-Access). Per MSAL è necessario [impostare la proprietà iOSKeychainSecurityGroup di PublicClientApplication](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet/wiki/Xamarin-iOS-specifics#enable-keychain-access). Successivamente sarà necessario eseguire l'override delle impostazioni di AAD predefinite usate da Intune SDK con quelle dell'app. È possibile farlo tramite il dizionario IntuneMAMSettings nel file Info.plist dell'app, come indicato nel [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md#configure-settings-for-the-intune-app-sdk) oppure è possibile usare le proprietà di sostituzione AAD dell'istanza IntuneMAMPolicyManager. L'approccio che prevede il file Info.plist è consigliato per applicazioni con impostazioni ADAL statiche, mentre le proprietà di sostituzione sono consigliate per le applicazioni che determinano questi valori in fase di esecuzione. Dopo aver configurato tutte le impostazioni SSO, l'app dovrebbe fornire l'UPN dell'utente al metodo RegisterAndEnrollAccount di IntuneMAMEnrollmentManager dopo essere stata autenticata:

      ```csharp
      IntuneMAMEnrollmentManager.Instance.RegisterAndEnrollAccount(string identity);
      ```

      Le app possono determinare il risultato di un tentativo di registrazione implementando il metodo EnrollmentRequestWithStatus in una sottoclasse di IntuneMAMEnrollmentDelegate e impostando la proprietà Delegate di IntuneMAMEnrollmentManager su un'istanza della classe. 

      Dopo aver eseguito la registrazione, le app possono determinare l'UPN dell'account registrato (se precedentemente sconosciuto) eseguendo una query nella proprietà seguente: 

      ```csharp
       string enrolledAccount = IntuneMAMEnrollmentManager.Instance.EnrolledAccount;
      ```      
### <a name="sample-applications"></a>Applicazioni di esempio
Applicazioni di esempio che evidenziano la funzionalità MAM nelle app Novell. iOS sono disponibili su [GitHub](https://github.com/msintuneappsdk/sample-intune-xamarin-ios).

> [!NOTE] 
> Non è disponibile alcun remapper per iOS. L'integrazione in un'app Xamarin.Forms deve essere identica a quella di un progetto Xamarin.iOS regolare. 

## <a name="enabling-intune-app-protection-policies-in-your-android-mobile-app"></a>Abilitazione dei criteri di protezione delle app di Intune nell'app per dispositivi mobili Android
1. Aggiungere il [pacchetto Microsoft.Intune.MAM.Xamarin.Android NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Xamarin.Android) al progetto Xamarin.Android.
    1. Per un app Xamarin.Forms, aggiungere anche il [pacchetto Microsoft.Intune.MAM.Remapper.Tasks NuGet](https://www.nuget.org/packages/Microsoft.Intune.MAM.Remapper.Tasks) al progetto Xamarin.Android. 
2. Seguire la procedura generale necessaria per [l'integrazione di Intune App SDK](app-sdk-android.md) in un'app per dispositivi mobili Android e al tempo stesso fare riferimento a questo documento per informazioni dettagliate aggiuntive.

### <a name="xamarinandroid-integration"></a>Integrazione di Xamarin.Android

In [Guida per sviluppatori di Microsoft Intune App SDK per Android](app-sdk-android.md) è disponibile una panoramica completa sull'integrazione di Intune App SDK. Durante la lettura della guida e l'integrazione di Intune App SK con l'app Xamarin, è possibile leggere le sezioni seguenti, che servono a evidenziare le differenze tra l'implementazione per un'app nativa per Android sviluppata in Java e un'app Xamarin sviluppata in C#. Queste sezioni devono essere considerate supplementari e non possono sostituire l'intera guida.

#### <a name="remapper"></a>Remapper
A partire dalla versione 1.4428.1, il pacchetto `Microsoft.Intune.MAM.Remapper` può essere aggiunto a un'applicazione Novell. Android come [strumento di compilazione](app-sdk-android.md#build-tooling) per eseguire le sostituzioni di classe Mam, metodo e servizi di sistema. Se il mapping è incluso, le parti sostitutive di MAM equivalenti dei metodi rinominati e delle sezioni dell'applicazione MAM verranno eseguite automaticamente al momento della compilazione dell'applicazione.

Per escludere una classe da MAM-Unity tramite il file di mapping, è possibile aggiungere la proprietà seguente nel file di progetto `.csproj`.

```xml
  <PropertyGroup>
    <ExcludeClasses>Semicolon separated list of relative class paths to exclude from MAM-ification</ExcludeClasses>
  </PropertyGroup>
```

> [!NOTE]
> A questo punto, un problema con il remapper impedisce il debug nelle app Novell. Android. L'integrazione manuale è consigliata per eseguire il debug dell'applicazione fino a quando il problema non viene risolto.

#### <a name="renamed-methodsapp-sdk-androidmdrenamed-methods"></a>[Metodi rinominati](app-sdk-android.md#renamed-methods)
In molti casi, un metodo disponibile nella classe Android è stato contrassegnato come finale nella classe sostitutiva MAM. In questo caso, la classe sostitutiva MAM fornisce un metodo denominato in modo analogo (con suffisso `MAM`), che deve essere sostituito al suo posto. Ad esempio, quando si deriva da `MAMActivity`, invece di sostituire `OnCreate()` e chiamare `base.OnCreate()`, la classe `Activity` deve sostituire `OnMAMCreate()` e chiamare `base.OnMAMCreate()`.

#### <a name="mam-applicationapp-sdk-androidmdmamapplication"></a>[Applicazione MAM](app-sdk-android.md#mamapplication)
L'app deve definire una classe `Android.App.Application`. Se si integra manualmente MAM, deve ereditare da `MAMApplication`. Assicurarsi che la sottoclasse sia decorata correttamente con l'attributo `[Application]` ed esegua l'override del costruttore `(IntPtr, JniHandleOwnership)`.

```csharp
    [Application]
    class TaskrApp : MAMApplication
    {
    public TaskrApp(IntPtr handle, JniHandleOwnership transfer)
        : base(handle, transfer) { }
```

> [!NOTE]
> In caso di problema con i binding Xamarin MAM, l'applicazione potrebbe arrestarsi in modo anomalo quando viene distribuita in modalità di debug. Per risolvere il problema, aggiungere l'attributo `Debuggable=false` alla classe `Application` e rimuovere il flag `android:debuggable="true"` dal manifesto se è stato impostato manualmente.

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

Per le applicazioni `Xamarin.Forms` il pacchetto `Microsoft.Intune.MAM.Remapper` esegue automaticamente la sostituzione delle classi MAM inserendo le classi `MAM` nella gerarchia di classi `Xamarin.Forms` usate comunemente. 

> [!NOTE]
> È necessario completare l'integrazione di Xamarin.Forms oltre all'integrazione di Xamarin.Android descritta in precedenza. Il comportamento di remapper è diverso per le app Novell. Forms in modo che le sostituzioni MAM manuali debbano essere comunque eseguite.

Dopo aver aggiunto il remapper al progetto, sarà necessario eseguire le sostituzioni MAM equivalenti. Ad esempio, è possibile continuare a usare `FormsAppCompatActivity` e `FormsApplicationActivity` nell'applicazione, purché `OnCreate` e `OnResume` siano sostituite rispettivamente dagli equivalenti MAM `OnMAMCreate` e `OnMAMResume`.

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

In caso di mancata sostituzione, è possibile che si verifichino gli errori di compilazione seguenti finché non viene eseguita la sostituzione:
* [Errore del compilatore CS0239](https://docs.microsoft.com/dotnet/csharp/misc/cs0239). questo errore in genere è visualizzato in questo formato ``'MainActivity.OnCreate(Bundle)': cannot override inherited member 'MAMAppCompatActivityBase.OnCreate(Bundle)' because it is sealed``.
È previsto perché quando lo strumento di modifica del mapping modifica l'ereditarietà delle classi Xamarin, determinate funzioni vengono rese `sealed` e viene aggiunta una nuova variante MAM per eseguire l'override.
* [Errore del compilatore CS0507](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0507): questo errore in genere è visualizzato in questo formato ``'MyActivity.OnRequestPermissionsResult()' cannot change access modifiers when overriding 'public' inherited member ...``. Quando lo strumento di modifica del mapping cambia l'ereditarietà di alcune classi di Xamarin, determinate funzioni membro vengono modificate in `public`. Se si sostituiscono queste funzioni, sarà necessario modificare anche i modificatori di accesso perché quelle sostituzioni siano `public`.

> [!NOTE]
> Il remapper riscrive una dipendenza usata da Visual Studio per il completamento automatico di IntelliSense. Potrebbe essere poi necessario ricaricare e ricompilare il progetto quando il remapper viene aggiunto per IntelliSense affinché le modifiche siano riconosciute correttamente.

#### <a name="troubleshooting"></a>Risoluzione dei problemi
* Se viene visualizzata una schermata bianca vuota nell'applicazione all'avvio, potrebbe essere necessario forzare l'esecuzione delle chiamate di navigazione sul thread principale.
* Le associazioni Novell di Intune SDK non supportano le app che usano un Framework multipiattaforma, ad esempio MvvmCross, a causa di conflitti tra le classi MAM MvvmCross e Intune. Sebbene alcuni clienti abbiano avuto successo con l'integrazione dopo aver spostato le proprie app in Plain Novell. Forms, non sono disponibili linee guida esplicite o plug-in per gli sviluppatori di app che usano MvvmCross.

### <a name="company-portal-app"></a>App Portale aziendale
Le associazioni Novell di Intune SDK si basano sulla presenza dell'app [portale aziendale](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) Android sul dispositivo per abilitare i criteri di protezione delle app. Il Portale aziendale recupera i criteri di protezione delle app dal servizio Intune. Al momento dell'inizializzazione, l'app carica i criteri e il codice per applicare i criteri dal Portale aziendale. Non è necessario che l'utente sia connesso.

> [!NOTE]
> Quando l'app Portale aziendale non è presente nel dispositivo **Android**, un'app gestita da Intune si comporta analogamente a una normale app che non supporta i criteri di protezione delle app di Intune.

Per la protezione delle app senza registrazione del dispositivo, _**non**_ è richiesta la registrazione del dispositivo con l'app Portale aziendale.

### <a name="sample-applications"></a>Applicazioni di esempio
Applicazioni di esempio che evidenziano la funzionalità MAM nelle app Novell. Android e Novell. Forms sono disponibili su [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps).

## <a name="support"></a>Support
Se l'organizzazione è un cliente di Intune esistente, contattare il rappresentante del supporto tecnico Microsoft per aprire un ticket di supporto e creare un problema [nella pagina GitHub relativa ai problemi](https://github.com/msintuneappsdk/intune-app-sdk-xamarin/issues). L'operazione sarà utile non appena possibile. 
