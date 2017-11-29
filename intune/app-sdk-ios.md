---
title: Guida per gli sviluppatori di Microsoft Intune App SDK per iOS
description: Microsoft Intune App SDK per iOS consente di integrare i criteri di protezione delle app di Intune, nel formato di gestione di applicazioni mobili (MAM), nell'app iOS.
keywords: 
author: mattbriggs
manager: angrobe
ms.author: mabriggs
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6ccc420b3bf334f15d1036eb83d01a2d228fad19
ms.sourcegitcommit: b2a6678a0e9617f94ee8c65e7981211483b30ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2017
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Guida per gli sviluppatori di Microsoft Intune App SDK per iOS

> [!NOTE]
> È possibile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

Microsoft Intune App SDK per iOS consente di integrare i criteri di protezione delle app di Intune, noti anche come criteri **APP** o **MAM**, nell'app iOS nativa. Un'applicazione abilitata per la gestione delle applicazioni mobili è un'applicazione integrata con Intune App SDK. Gli amministratori IT possono distribuire i criteri di protezione delle app nei dispositivi mobili quando Intune gestisce attivamente l'app.

## <a name="prerequisites"></a>Prerequisiti

* È necessario un computer Mac OS che esegue OS X 10.8.5 o versione successiva e che ha installato Xcode 8 o versione successiva.

* La destinazione dell'app deve essere iOS 9 o versione successiva.

* Rivedere le [condizioni di licenza di Intune App SDK per iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS%20.pdf). Stampare e conservare una copia delle condizioni di licenza. Il download e l'uso di Intune App SDK per iOS implicano l'accettazione delle condizioni di licenza.  Se non vengono accettate, non usare il software.

* Scaricare i file per Intune App SDK per iOS in [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk"></a>Contenuto dell'SDK

Intune App SDK per iOS include una libreria statica, file di risorse, intestazioni API, un file di impostazioni di debug con estensione plist e uno strumento di configurazione. Le app per dispositivi mobili possono includere semplicemente i file di risorse e un collegamento statico alle librerie per l'applicazione della maggior parte dei criteri. Le funzionalità MAM di Intune avanzate vengono applicate tramite API.

Questa guida illustra l'uso dei componenti seguenti di Intune App SDK per iOS:

* **libIntuneMAM.a**: libreria statica di Intune App SDK. Se l'app non usa estensioni, collegare questa libreria al progetto per abilitare l'app per la gestione delle applicazioni mobili di Intune.

* **IntuneMAM.framework**: framework di Intune App SDK. Collegare questo framework al progetto per abilitare l'app per la gestione delle applicazioni mobili di Intune. Usare il framework anziché la libreria statica se l'app usa estensioni, in modo che il progetto non crei più copie della libreria statica.

* **IntuneMAMResources.bundle**: bundle di risorse contenente le risorse usate dall'SDK.

* **Intestazioni**: espongono le API di Intune App SDK. Se si usa un'API, è necessario includere il file di intestazione contenente l'API. I file di intestazione seguenti includono API, tipi di dati e protocolli resi disponibili agli sviluppatori da Intune App SDK:

    * IntuneMAMAppConfig.h
    * IntuneMAMAppConfigManager.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMDefs.h
    * IntuneMAMEnrollmentDelegate.h
    * IntuneMAMEnrollmentManager.h
    * IntuneMAMEnrollmentStatus.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMLogger.h
    * IntuneMAMPolicy.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMPolicyManager.h
    * IntuneMAMVersionInfo.h
    
Gli sviluppatori possono rendere disponibile il contenuto di tutte le intestazioni importando IntuneMAM.h


## <a name="how-the-intune-app-sdk-works"></a>Funzionamento di Intune App SDK

L'obiettivo di Intune App SDK per iOS è quello di aggiungere funzionalità di gestione per le applicazioni iOS con modifiche minime al codice. Riducendo le modifiche al codice, si velocizza l'immissione dell'app sul mercato, mantenendo nel contempo la coerenza e la stabilità dell'applicazione mobile.


## <a name="build-the-sdk-into-your-mobile-app"></a>Compilare l'SDK nell'app per dispositivi mobili

Per abilitare Intune App SDK, seguire questa procedura:

1. **Opzione 1 (consigliata)**: collegare `IntuneMAM.framework` al progetto. Trascinare `IntuneMAM.framework` nell'elenco **Embedded Binaries** (File binari incorporati) della destinazione del progetto.

    > [!NOTE]
    > Se si usa il framework, prima di inviare l'app all'App Store, è necessario eliminare manualmente le architetture del simulatore dal framework universale. Per altri dettagli, vedere [Inviare l'app all'App Store](#Submit-your-app-to-the-App-Store).

2. **Opzione 2**: collegarsi alla libreria `libIntuneMAM.a`. Trascinare la libreria `libIntuneMAM.a` nell'elenco **Linked Frameworks and Libraries** (Framework e librerie collegati) di destinazione del progetto.

    ![Intune App SDK per iOS: Linked Frameworks and Libraries (Framework e librerie collegati)](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Aggiungere `-force_load {PATH_TO_LIB}/libIntuneMAM.a` in una delle posizioni seguenti, sostituendo `{PATH_TO_LIB}` con il percorso di Intune App SDK:
      * Impostazione di configurazione della build `OTHER_LDFLAGS` del progetto
      * Opzione **Other Linker Flags** (Altri contrassegni del linker) nell'interfaccia utente

        > [!NOTE]
        > Per trovare `PATH_TO_LIB`, selezionare il file `libIntuneMAM.a` e scegliere **Get Info** (Ottieni informazioni) dal menu **File**. Copiare e incollare le informazioni indicate in **Where** (Dove), ovvero il percorso, dalla sezione **General** (Generale) della finestra **Info** (Informazioni).

    Aggiungere il bundle di risorse `IntuneMAMResources.bundle` al progetto trascinandolo in **Copy Bundle Resources** (Copia risorse bundle) in **Build Phases** (Compila fasi).

    ![Intune App SDK iOS: copiare il bundle di risorse](./media/intune-app-sdk-ios-copy-bundle-resources.png)

3. Aggiungere i framework iOS seguenti al progetto:
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.tbd
    * libc++.tbd
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework

4. Se l'app per dispositivi mobili definisce un file nib o un file storyboard nel file Info.plist, tagliare i campi **Main Storyboard** (Storyboard principale) o **Main Nib** (Nib principale). Nel file Info.plist incollare questi campi e i rispettivi valori in un nuovo dizionario denominato **IntuneMAMSettings** con i nomi di chiave seguenti, secondo le esigenze:
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    > [!NOTE]
  > Se l'app per dispositivi mobili non definisce un file nib o un file storyboard principale nel file Info.plist, queste impostazioni non sono necessarie.

    Per vedere i nomi chiave, è possibile visualizzare il file Info.plist in un formato non elaborato. Fare clic con il pulsante destro del mouse in un punto qualsiasi nel corpo del documento e modificare il tipo di visualizzazione in **Show Raw Keys/Values** (Mostra chiavi/valori non elaborati).

5. Abilitare la condivisione Keychain, se non è già abilitata, scegliendo **Capabilities** (Funzionalità) in ogni destinazione del progetto e abilitando l'opzione **Keychain Sharing** (Condivisione Keychain). La condivisione Keychain è necessaria per procedere con il passaggio successivo.

  > [!NOTE]
    > È necessario che il profilo di provisioning supporti i nuovi valori della condivisione Keychain. I gruppi di accesso a Keychain devono supportare un carattere jolly. Per verificare, aprire il file .mobileprovision in un editor di testo, cercare **keychain-access-groups** e assicurarsi che sia presente un carattere jolly. Ad esempio:
    ```xml
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```

6. Dopo avere abilitato la condivisione Keychain, seguire questa procedura per creare un gruppo di accesso separato in cui Intune App SDK archivierà i dati. È possibile creare un gruppo di accesso a Keychain usando l'interfaccia utente o il file di diritti. Se si usa l'interfaccia utente per creare un gruppo di accesso a Keychain, seguire questa procedura:

    1. Se per l'app per dispositivi mobili non sono definiti gruppi di accesso a Keychain, aggiungere l'ID bundle dell'app come primo gruppo.

    2. Aggiungere il gruppo di Keychain condiviso `com.microsoft.intune.mam` ai gruppi di accesso esistenti. Questo è il gruppo di accesso usato da Intune App SDK per archiviare i dati.

    3. Aggiungere `com.microsoft.adalcache` ai gruppi di accesso esistenti.

        ![Intune App SDK per iOS: condivisione Keychain](./media/intune-app-sdk-ios-keychain-sharing.png)

    4. Se si modifica il file dei diritti direttamente, anziché tramite l'interfaccia utente di Xcode illustrata in precedenza per creare i gruppi di accesso keychain, anteporre il prefisso `$(AppIdentifierPrefix)` ai gruppi di accesso keychain (Xcode gestisce questo aspetto automaticamente). Ad esempio:

            * `$(AppIdentifierPrefix)com.microsoft.intune.mam`
            * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    > [!NOTE]
    > Un file di diritti è un file XML specifico per l'applicazione mobile. Consente di specificare autorizzazioni e funzionalità speciali nell'app iOS. Se l'app non aveva in precedenza un file dei diritti, in seguito all'abilitazione della condivisione del keychain (passaggio 6) Xcode dovrebbe averne generato uno per l'app.

7. Se l'app definisce schemi URL nel file Info.plist, aggiungere un altro schema, con un suffisso `-intunemam`, per ogni schema URL.

8. Se l'app definisce i tipi di documento nel file Info.plist, per la matrice "UTI dei tipi di contenuto documento" di ogni elemento, aggiungere una voce duplicata per ogni stringa con prefisso "com.microsoft.intune.mam".

9. Per le app per dispositivi mobili sviluppate in iOS 9 o versione successiva, includere ogni protocollo passato dall'app a `UIApplication canOpenURL` nella matrice `LSApplicationQueriesSchemes` del file Info.plist dell'app. Per ogni protocollo elencato è anche necessario aggiungere un nuovo protocollo seguito da `-intunemam`. Nella matrice includere anche `http-intunemam`, `https-intunemam` e `ms-outlook-intunemam`.

10. Se nei diritti dell'app sono definiti gruppi di app, aggiungere questi gruppi al dizionario **IntuneMAMSettings** nella chiave `AppGroupIdentifiers` come matrice di stringhe.

## <a name="using-the-intune-mam-configurator-tool"></a>Uso dello strumento Intune MAM Configurator

Lo strumento Intune MAM Configurator gestisce tutte le elaborazioni di info.plist necessarie per l'integrazione manuale del SDK. Lo strumento è disponibile nel repository Intune App SDK per iOS. Le impostazioni aggiuntive specifiche delle app quali ID multipli, impostazioni AAD e così via non vengono gestite da questo strumento. Lo strumento include 3 parametri:
 
|Proprietà|Modo d'uso|
|---------------|--------------------------------|
|- i |  `<Path to the input plist>` |
|- e | File dei diritti |
|- o |  (Facoltativo) `<Path for the changed input plist>` |
    
Lo strumento Intune MAM Configurator può essere usato per aggiornare:
* I file dello storyboard principale o i file con estensione nib principali in IntuneMAMSettings.
* Gli schemi URL definiti dell'app nel file Info.plist corrispondente con il suffisso -intunemam per ogni schema URL.
* I tipi di documento definiti nel file Info.plist per la matrice "UTI dei tipi di contenuto documento" di ogni elemento; aggiungere una voce duplicata per ogni stringa con prefisso "com.microsoft.intune.mam".
* I gruppi di app definiti nei diritti dell'app. Aggiungere questi gruppi al dizionario IntuneMAMSettings nella chiave AppGroupIdentitifiers come matrice di stringhe.

    
>[!NOTE] Se si decide di usare questo strumento invece della modifica manuale di info.plist, è consigliabile eseguire nuovamente lo strumento dopo ogni modifica apportata al file info.plist o ai diritti dell'app.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurare Azure Active Directory Authentication Library (ADAL)

Intune App SDK usa [Azure Active Directory Authentication Library](https://github.com/AzureAD/azure-activedirectory-library-for-objc) per gli scenari di autenticazione e di avvio condizionale. Si basa su ADAL anche per registrare l'identità utente con il servizio MAM per la gestione senza scenari di registrazione del dispositivo.

ADAL richiede in genere che le app eseguano la registrazione con Azure Active Directory (AAD) e ottengano un ID univoco (ID client) e altri identificatori per garantire la sicurezza dei token concessi all'app. Se non diversamente specificato, Intune App SDK usa i valori di registrazione predefiniti per mettersi in contatto con Azure AD.  

Se l'app usa già ADAL per l'autenticazione degli utenti, deve usare i valori di registrazione esistenti e sostituire i valori predefiniti di Intune App SDK. In questo modo agli utenti non viene richiesta la doppia autenticazione, una di Intune App SDK e una dell'app.

### <a name="recommendations"></a>Consigli

È consigliabile collegare l'app alla [versione più recente di ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) nel suo ramo master. Intune App SDK usa attualmente il ramo broker di ADAL per supportare le app che richiedono l'accesso condizionale. Queste app dipendono di conseguenza dall'app Microsoft Authenticator. L'SDK è tuttavia ancora compatibile con il ramo master di ADAL. Usare il ramo più adatto all'app.

### <a name="link-to-adal-binaries"></a>Collegamento ai file binari di ADAL

Seguire questa procedura per collegare l'app ai file binari di ADAL:

1. Scaricare [Azure Active Directory Authentication Library (ADAL) per Objective-C](https://github.com/AzureAD/azure-activedirectory-library-for-objc) da GitHub e seguire le [istruzioni](https://github.com/AzureAD/azure-activedirectory-library-for-objc/blob/master/README.md) su come scaricare ADAL usando i moduli secondari Git o CocoaPods.

2. Includere il bundle di risorse `ADALiOSBundle.bundle` al progetto trascinandolo in **Copy Bundle Resources** (Copia risorse bundle) in **Build Phases** (Compila fasi).

3. Aggiungere `-force_load {PATH_TO_LIB}/libADALiOS.a` all'impostazione di configurazione della build `OTHER_LDFLAGS` del progetto o a **Other Linker Flags** (Altri contrassegni del linker) nell'interfaccia utente. Sostituire `PATH_TO_LIB` con la posizione dei file binari ADAL.



### <a name="share-the-adal-token-cache-with-other-apps-signed-with-the-same-provisioning-profile"></a>Condividere la cache dei token ADAL con altre app firmate con lo stesso profilo di provisioning**

Per condividere i token ADAL tra le app firmate con lo stesso profilo di provisioning, attenersi alle istruzioni seguenti:

1. Se per l'app non sono definiti gruppi di accesso a Keychain, aggiungere l'ID bundle dell'app come primo gruppo.

2. Abilitare Single Sign-On (SSO) di ADAL aggiungendo i gruppi di accesso `com.microsoft.adalcache` e `com.microsoft.workplacejoin` ai diritti di Keychain.

3. Nel caso in cui si stia impostando in modo esplicito il gruppo Keychain della cache condivisa di ADAL, assicurarsi di impostarlo su `<app_id_prefix>.com.microsoft.adalcache`. A meno che venga sostituito, ADAL imposterà tale valore. Se si vuole specificare un gruppo Keychain personalizzato per sostituire `com.microsoft.adalcache`, specificarlo nel file Info.plist in IntuneMAMSettings usando la chiave `ADALCacheKeychainGroupOverride`.

### <a name="configure-adal-settings-for-the-intune-app-sdk"></a>Configurare le impostazioni di ADAL per Intune App SDK

Se l'app usa già ADAL per l'autenticazione e contiene impostazioni di ADAL proprie, è possibile forzare l'uso delle stesse impostazioni in Intune App SDK durante l'autenticazione con Azure Active Directory. Ciò garantisce che l'app non richieda due volte all'utente di autenticarsi. Vedere [Configurare le impostazioni per Intune App SDK](#configure-settings-for-the-intune-app-sdk) per informazioni sull'inserimento delle impostazioni seguenti:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Se l'app usa già ADAL, sono necessarie le configurazioni seguenti:

1. Nel file Info.plist del progetto, in un dizionario **IntuneMAMSettings** con il nome di chiave `ADALClientId`, specificare l'ID client da usare per le chiamate ad ADAL.

2. Nel dizionario **IntuneMAMSettings** con il nome di chiave `ADALAuthority` specificare anche l'autorità di Azure AD.

3. Nel dizionario **IntuneMAMSettings** con il nome di chiave `ADALRedirectUri` specificare anche l'URI di reindirizzamento da usare per le chiamate ad ADAL. A seconda del formato dell'URI di reindirizzamento dell'app, potrebbe essere necessario specificare anche `ADALRedirectScheme`.


È anche possibile sostituire l'URL dell'autorità di Azure AD con un URL specifico del tenant in fase di runtime. A tale scopo, impostare semplicemente la proprietà `aadAuthorityUriOverride` nell'istanza `IntuneMAMPolicyManager`.

> [!NOTE]
> L'impostazione dell'URL dell'autorità AAD è richiesta dai criteri [APP senza registrazione del dispositivo](#App-protection-policy-without-device-enrollment) per consentire all'SDK di usare nuovamente il token di aggiornamento ADAL recuperato dall'app.

L'SDK continuerà a usare questo URL dell'autorità per l'aggiornamento dei criteri ed eventuali richieste di registrazione successive a meno che il valore venga cancellato o modificato.  È quindi importante cancellare il valore quando un utente gestito si disconnette dall'app e reimpostare il valore quando un nuovo utente gestito esegue l'accesso.

### <a name="if-your-app-does-not-use-adal"></a>Se l'applicazione non usa ADAL

Se l'app non usa ADAL, Intune App SDK specifica i valori predefiniti per i parametri ADAL e gestisce l'autenticazione con Azure AD. Non è necessario specificare valori per le impostazioni ADAL elencate in precedenza.

## <a name="app-protection-policy-without-device-enrollment"></a>Criteri di protezione delle app senza registrazione del dispositivo

### <a name="overview"></a>Panoramica
I criteri di protezione delle app di Intune senza registrazione del dispositivo, noti anche come **APP-WE** o MAM-WE, consentono la gestione delle app in Intune senza richiedere la registrazione del dispositivo nella gestione di dispositivi mobili (MDM) di Intune. Per supportare questa nuova funzionalità, l'app deve partecipare alla registrazione degli account utente per la gestione. Per usare le nuove API, seguire questa procedura:

1. Usare la versione più recente di Intune App SDK che supporta la gestione di app con o senza registrazione del dispositivo.

2. Aggiungere IntuneMAMEnrollment.h ai file che chiameranno le API.

### <a name="register-user-accounts"></a>Registrare gli account utente

Un'app può ricevere criteri di protezione delle app dal servizio di Intune se esegue la registrazione al servizio APP-WE per conto di un account utente specificato. L'app deve registrare tutti i nuovi utenti che eseguono l'accesso con l'SDK. Al termine dell'autenticazione del nuovo account utente, l'app deve chiamare il metodo `registerAndEnrollAccount` in Headers/IntuneMAMEnrollment.h:

```objc
/**


 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;

```
Chiamando il metodo `registerAndEnrollAccount`, l'SDK registra l'account utente e prova a registrare l'app per conto di questo account. Se la registrazione non riesce per qualsiasi motivo, l'SDK riproverà automaticamente la registrazione dopo 24 ore. A scopo di debug, l'app può ricevere notifiche sui risultati di tutte le richieste di registrazione attraverso un delegato.

Dopo aver richiamato l'API, l'app può continuare a funzionare normalmente. Se la registrazione avviene correttamente, l'SDK comunicherà all'utente che è necessario un riavvio dell'app. A questo punto, l'utente può riavviare immediatamente l'app.

### <a name="deregister-user-accounts"></a>Annullare la registrazione degli account utente

Prima di disconnettere un utente da un'app, è necessario che l'app ne annulli la registrazione dall'SDK. In questo modo:

1. Non si verificheranno nuovi tentativi di registrazione per l'account utente.

2. I criteri di protezione delle app verranno rimossi.

3. Se l'app avvia una cancellazione selettiva (facoltativa), tutti i dati aziendali verranno eliminati.

Prima della disconnessione dell'utente, l'app deve chiamare l'API seguente in `Headers/IntuneMAMEnrollment.h`:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune MAM AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */

(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Questo metodo deve essere chiamato prima che i token di Azure AD dell'account utente vengano eliminati. L'SDK richiede che i token AAD dell'account utente eseguano richieste specifiche al servizio APP-WE per conto dell'utente.

Se l'app eliminerà i dati aziendali dell'utente in modo autonomo, il contrassegno `doWipe` può essere impostato su false. In caso contrario, l'SDK può avviare automaticamente una cancellazione selettiva. Ciò comporta una chiamata al delegato per la cancellazione selettiva dell'app.

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

### <a name="apps-that-do-not-use-adal"></a>App che non usano ADAL

Le app che non eseguono l'accesso dell'utente con ADAL possono comunque ricevere i criteri di protezione delle app dal servizio di Intune chiamando l'API per consentire all'SDK di gestire l'autenticazione. Le app devono usare questa tecnica quando l'utente non è stato autenticato con Azure AD, ma è comunque necessario recuperare i criteri di protezione delle app per proteggere i dati. Ad esempio, si applica questa tecnica quando viene usato un altro servizio di autenticazione per l'accesso all'app o se l'app non supporta l'accesso. A tale scopo, l'applicazione deve chiamare il metodo `loginAndEnrollAccount` in Headers/IntuneMAMEnrollment.h:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;

```

Chiamando questo metodo, l'SDK chiederà le credenziali dell'utente se non vengono trovati token esistenti. L'SDK proverà quindi a registrare l'app con il servizio APP-WE per conto dell'account utente specificato. Il metodo può essere chiamato con l'identità "nil". In questo caso l'SDK eseguirà la registrazione con l'utente gestito esistente nel dispositivo o chiederà di specificare un nome utente se non trova utenti esistenti.

Se la registrazione non riesce, l'app deve considerare la necessità di chiamare l'API in un secondo momento, a seconda dei dettagli dell'errore. L'app può ricevere le [notifiche](#Status-result-and-debug-notifications) sui risultati di tutte le richieste di registrazione attraverso un delegato.

Dopo aver richiamato l'API, l'app può continuare a funzionare normalmente. Se la registrazione avviene correttamente, l'SDK comunicherà all'utente che è necessario un riavvio dell'app.

## <a name="status-result-and-debug-notifications"></a>Notifiche di stato, risultato e debug

L'app può ricevere notifiche di stato, risultato e debug riguardanti le richieste seguenti al servizio MAM di Intune:

 - Richieste di registrazione
 - Richieste di aggiornamento dei criteri
 - Richieste di annullamento della registrazione

Le notifiche vengono presentate tramite metodi delegati in `Headers/IntuneMAMEnrollmentDelegate.h`:

```objc
/**
 *  Called when an enrollment request operation is completed.
 * @param status status object containing debug information
 */

(void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a MAM policy request operation is completed.
 *  @param status status object containing debug information
 */
(void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

/**
 *  Called when a un-enroll request operation is completed.
 *  @Note: when a user is un-enrolled, the user is also de-registered with the SDK
 *  @param status status object containing debug information
 */

(void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status;

```

Questi metodi delegati restituiscono un oggetto `IntuneMAMEnrollmentStatus` che contiene le informazioni seguenti:

- Identità dell'account associato alla richiesta
- Codice di stato che indica il risultato della richiesta
- Stringa di errore con una descrizione del codice di stato
- Oggetto `NSError`

Questo oggetto viene definito in `IntuneMAMEnrollmentStatus.h` insieme ai codici di stato specifici che possono essere restituiti.


### <a name="sample-code"></a>Codice di esempio

Di seguito sono illustrate implementazioni di esempio dei metodi delegati:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}


- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus *)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

```

## <a name="app-restart"></a>Riavvio dell'app

Quando un'app riceve i criteri di protezione delle app per la prima volta, deve essere riavviata per poter applicare gli hook obbligatori. Per comunicare all'app che è necessario un riavvio, l'SDK offre un metodo delegato in Headers/IntuneMAMPolicyDelegate.h.

```objc
 - (BOOL) restartApplication
```
Il valore restituito da questo metodo indica all'SDK se l'applicazione deve gestire il riavvio richiesto:   

 - Se viene restituito true, l'applicazione deve gestire il riavvio.   

 - Se viene restituito false, l'SDK riavvierà l'applicazione. L'SDK visualizzerà immediatamente una finestra di dialogo per indicare all'utente che è necessario riavviare l'applicazione.

## <a name="customize-your-apps-behavior"></a>Personalizzare il comportamento dell'app

Intune App SDK include varie API che è possibile chiamare per ottenere informazioni sui criteri di protezione delle app di Intune distribuiti nell'app. È possibile usare questi dati per personalizzare il comportamento dell'app. La maggior parte delle impostazioni dei criteri di protezione delle app viene applicata automaticamente dall'SDK e non dall'applicazione. L'unica impostazione che deve implementare l'app è il salvataggio.

### <a name="get-app-protection-policy"></a>Ottenere i criteri di protezione delle app

#### <a name="intunemampolicymanagerh"></a>IntuneMAMPolicyManager.h
La classe IntuneMAMPolicyManager espone i criteri di protezione delle app di Intune distribuiti nell'applicazione. In particolare, espone le API utili per l'[abilitazione di identità multiple](#-enable-multi-identity-optional).

#### <a name="intunemampolicyh"></a>IntuneMAMPolicy.h
La classe IntuneMAMPolicy espone i criteri di protezione delle app di Intune distribuiti nell'applicazione. La maggior parte delle impostazioni dei criteri esposte in questa classe viene applicata dall'SDK, ma è sempre possibile personalizzare il comportamento dell'app in base alla modalità di applicazione delle impostazioni dei criteri.

Questa classe espone alcune API necessarie per implementare i controlli di salvataggio, descritti in dettaglio nella sezione successiva.

### <a name="implement-save-as-controls"></a>Implementare i controlli di salvataggio

Intune consente agli amministratori IT di selezionare le posizioni di archiviazione in cui possono essere salvati i dati di un'app gestita. Le app possono eseguire una query in Intune App SDK per recuperare le posizioni di archiviazione consentite usando l'API **isSaveToAllowedForLocation** definita in **IntuneMAMPolicy.h**.

Prima di salvare i dati gestiti in un'archiviazione cloud o in un percorso locale, le app devono usare l'API **isSaveToAllowedForLocation** per verificare se l'amministratore IT ha consentito il salvataggio dei dati in quel percorso.

Quando si usa l’API **isSaveToAllowedForLocation**, le app devono passare l’UPN usato per la posizione di archiviazione, se disponibile.

#### <a name="supported-save-locations"></a>Percorsi di salvataggio supportati

L'API **isSaveToAllowedForLocation** specifica le costanti per verificare se l'amministratore IT autorizza il salvataggio dei dati nei percorsi seguenti definiti in IntuneMAMPolicy.h:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Le app devono usare le costanti nell’API **isSaveToAllowedForLocation** per verificare se i dati possano essere salvati in percorsi considerati "gestiti", come ad esempio OneDrive for Business, o "personali". L'API deve essere usata anche quando l'app non riesce a determinare se un percorso è "gestito" o "personale".

I percorsi notoriamente "personali" sono rappresentati dalla costante `IntuneMAMSaveLocationOther`.

La costante `IntuneMAMSaveLocationLocalDrive` deve essere usata quando l'app salva i dati in un percorso qualsiasi del dispositivo locale.

## <a name="configure-settings-for-the-intune-app-sdk"></a>Configurare le impostazioni per Intune App SDK

Per configurare Intune App SDK, è possibile usare il dizionario **IntuneMAMSettings** incluso nel file Info.plist dell'applicazione. Se il dizionario IntuneMAMSettings non è disponibile nel file Info.plist, è consigliabile crearne uno nel file Info.plist dell'app con il nome campo "IntuneMAMSettings".

Nel dizionario IntuneMAMSettings è possibile aggiungere righe di chiave/valore di impostazioni di configurazione per configurare l'SDK. La tabella seguente elenca tutte le impostazioni supportate.

È possibile che alcune di queste impostazioni siano state descritte nelle sezioni precedenti. Alcune non riguardano tutte le app.

Impostazioni  | Tipo  | Definizione | Necessaria?
--       |  --   |   --       |  --
ADALClientId  | String  | Identificatore del client di Azure AD dell'app. | Obbligatoria se l'app usa ADAL. |
ADALAuthority | String | Autorità di Azure AD dell'app in uso. È necessario usare l'ambiente specifico in cui sono stati configurati gli account AAD. | Obbligatoria se l'app usa ADAL. Se questo valore è assente, viene usato un valore predefinito di Intune.|
ADALRedirectUri  | String  | URI di reindirizzamento di Azure AD dell'app. | L'impostazione ADALRedirectUri o ADALRedirectScheme è obbligatoria se l'app usa ADAL.  |
ADALRedirectScheme  | String  | Schema di reindirizzamento di Azure AD dell'app. Può essere usata al posto di ADALRedirectUri se l'URI di reindirizzamento dell'applicazione è nel formato `scheme://bundle_id`. | L'impostazione ADALRedirectUri o ADALRedirectScheme è obbligatoria se l'app usa ADAL. |
ADALLogOverrideDisabled | Boolean  | Specifica se l'SDK indirizzerà tutti i log ADAL, incluse le eventuali chiamate ad ADAL dall'app, al proprio file di log. L'impostazione predefinita è NO. Impostare il valore su YES (Sì) se l'app imposta la richiamata al log ADAL. | Facoltativo. |
ADALCacheKeychainGroupOverride | String  | Specifica il gruppo Keychain da usare per la cache ADAL al posto di "com.microsoft.adalcache". Si noti che non contiene il prefisso app-id che verrà aggiunto alla stringa specificata in fase di runtime. | Facoltativa. |
AppGroupIdentifiers | Matrice di stringa  | Matrice di gruppi di app della sezione com.apple.security.application-groups dei diritti dell'app. | Necessaria se l'applicazione usa i gruppi di applicazioni. |
ContainingAppBundleId | String | Specifica l'ID bundle dell'applicazione che contiene l'estensione. | Necessaria per le estensioni iOS. |
DebugSettingsEnabled| Boolean | Se è impostata su YES (Sì), è possibile applicare i criteri di test nell'ambito del bundle delle impostazioni. Le applicazioni *non* devono essere inviate con questa impostazione abilitata. | Facoltativo. |
MainNibFile<br>MainNibFile~ipad  | String  | Questa impostazione deve avere il nome del file nib principale dell'applicazione.  | È obbligatoria se l'applicazione definisce MainNibFile in Info.plist. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | String  | Questa impostazione deve avere il nome del file di storyboard principale dell'applicazione. | È obbligatoria se l'applicazione definisce UIMainStoryboardFile in Info.plist. |
AutoEnrollOnLaunch| Boolean| Specifica se l'app deve tentare di registrarsi automaticamente all'avvio se viene rilevata un'identità gestita esistente e se tale operazione non è ancora stata compiuta. L'impostazione predefinita è NO. <br><br> Note: se non viene trovata alcuna identità gestita o non è disponibile alcun token valido per l'identità nella cache ADAL, il tentativo di registrazione avrà esito negativo senza chiedere le credenziali, a meno che l'app non abbia configurato anche MAMPolicyRequired su YES. | Facoltativa. |
MAMPolicyRequired| Boolean| Specifica se verrà impedito l'avvio dell'app se l'app non include i criteri di protezione delle app di Intune. L'impostazione predefinita è NO. <br><br> Note: le app non possono essere inviate ad App Store se MAMPolicyRequired è impostato su YES. Quando si imposta MAMPolicyRequired su YES, anche AutoEnrollOnLaunch deve essere impostato su YES. | Facoltativa. |
MAMPolicyWarnAbsent | Boolean| Specifica se l'app avvisa l'utente durante l'avvio se non ha i criteri di protezione delle app di Intune. <br><br> Nota: gli utenti potranno ancora usare l'app senza criterio dopo aver ignorato l'avviso. | Facoltativa. |
MultiIdentity | Boolean| Specifica se l'app è compatibile con identità multiple. | Facoltativa. |
SplashIconFile <br>SplashIconFile~ipad | String  | Specifica il file icona per la schermata iniziale (avvio) di Intune. | Facoltativa. |
SplashDuration | Numero | Durata minima in secondi per la visualizzazione della schermata iniziale di Intune all'avvio dell'applicazione. Il valore predefinito è 1,5. | Facoltativa. |
BackgroundColor| String| Specifica il colore di sfondo per le schermate di avvio e di immissione del PIN. Accetta una stringa RGB esadecimale nel formato #XXXXXX, dove X può variare da 0 a 9 o da A a F. Il segno del cancelletto può essere omesso.   | Facoltativa. L'impostazione predefinita è grigio chiaro. |
ForegroundColor| String| Specifica il colore di primo piano per le schermate di avvio e di immissione del PIN, come il colore del testo. Accetta una stringa RGB esadecimale nel formato #XXXXXX, dove X può variare da 0 a 9 o da A a F. Il segno del cancelletto può essere omesso.  | Facoltativa. L'impostazione predefinita è nero. |
AccentColor | String| Specifica il colore principale della schermata di immissione del PIN, ad esempio il colore del testo del pulsante e il colore di evidenziazione della casella. Accetta una stringa RGB esadecimale nel formato #XXXXXX, dove X può variare da 0 a 9 o da A a F. Il segno del cancelletto può essere omesso.| Facoltativa. L'impostazione predefinita è blu. |
MAMTelemetryDisabled| Boolean| Specifica se l'SDK non invierà i dati di telemetria al relativo back-end.| Facoltativo |
WebViewHandledURLSchemes | Matrice di stringhe | Specifica gli schemi URL gestiti dalla visualizzazione Web dell'app. | Obbligatoria se l'app usa una WebView che gestisce gli URL tramite collegamenti e/o JavaScript. |  

> [!NOTE]
> Se l'app verrà rilasciata nell'App Store, `MAMPolicyRequired` deve essere impostato su "NO" come previsto dagli standard per App Store.

## <a name="enabling-mam-targeted-configuration-for-your-ios-applications"></a>Abilitazione della configurazione di destinazione MAM per le applicazioni iOS
La configurazione di destinazione MAM consente a un'app di ricevere i dati di configurazione tramite Intune App SDK. Il proprietario o lo sviluppatore dell'applicazione deve comunicare ai clienti Intune il formato e le varianti di tali dati. Gli amministratori di Intune possono trovare e distribuire i dati di configurazione tramite il portale di Azure di Intune. A partire da Intune App SDK per iOS (v 7.0.1) le applicazioni incluse nella configurazione di destinazione MAM possono ricevere dati di configurazione MAM tramite il servizio MAM. I dati di configurazione dell'applicazione vengono inviati tramite il servizio MAM direttamente all'app invece che tramite il canale MDM. Intune App SDK include una classe per l'accesso ai dati recuperati da queste console. I seguenti elementi possono essere considerati come prerequisiti: <br>
* Per l'accesso all'interfaccia utente della configurazione di destinazione MAM, l'app deve essere registrata in MAM-WE. Per altre informazioni su MAM-WE, vedere [Criteri di protezione delle app senza registrazione del dispositivo](https://docs.microsoft.com/en-us/intune/app-sdk-ios#app-protection-policy-without-device-enrollment) nella Guida di Intune App SDK.
* Includere ```IntuneMAMAppConfigManager.h``` nel file di origine dell'app.
* Chiamare ```[[IntuneMAMAppConfig instance] appConfigForIdentity:]``` per ottenere l'oggetto Configurazione applicazione.
* Chiamare il selettore appropriato per l'oggetto ```IntuneMAMAppConfig```. Ad esempio se la chiave dell'applicazione è una stringa è opportuno usare ```stringValueForKey``` o ```allStringsForKey```. Il file ```IntuneMAMAppConfig.h header``` illustra le condizioni di errore e i valori restituiti.

Per altre informazioni sulle funzionalità dell'API Graph relative ai valori di configurazione MAM di destinazione, vedere [Configurazione MAM di destinazione di riferimento per l'API Graph](https://graph.microsoft.io/en-us/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create). <br>

Per altre informazioni su come creare un criterio di configurazione app di destinazione MAM in iOS, vedere la sezione relativa alla configurazione di app di destinazione MAM in [Come usare i criteri di configurazione delle app di Microsoft Intune per iOS](https://docs.microsoft.com/en-us/intune/app-configuration-policies-use-ios).

## <a name="telemetry"></a>Telemetria

Per impostazione predefinita, Intune App SDK per iOS registra i dati di telemetria sugli eventi di uso seguenti. Questi dati vengono inviati a Microsoft Intune.

* **Avvio dell'app**: per offrire informazioni a Microsoft Intune sull'uso dell'app abilitata per MAM in base al tipo di gestione (MAM con MDM, MAM senza registrazione MDM e così via).

* **Chiamate di registrazione**: per offrire a Microsoft Intune informazioni sulla frequenza di esecuzione senza errori e su altre metriche delle prestazioni che riguardano le chiamate di registrazione avviate dal lato client.

> [!NOTE]
> Se si sceglie di non inviare i dati di telemetria di Intune App SDK a Microsoft Intune dall'applicazione per dispositivi mobili, è necessario disabilitare l'acquisizione della telemetria di Intune App SDK. Impostare la proprietà `MAMTelemetryDisabled` su YES (Sì) nel dizionario IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Abilitare identità multiple (facoltativo)

Per impostazione predefinita, l'SDK applica i criteri all'intera app. La funzionalità MAM per l'uso delle identità multiple può essere abilitata per applicare i criteri a livello di singola identità. Ciò richiede una partecipazione dell'app più attiva rispetto ad altre funzionalità di gestione delle applicazioni mobili.

L'app deve informare l'SDK dell'app quando intende modificare l'identità attiva. L'SDK comunica anche all'app quando è necessaria una modifica di identità. Attualmente è supportata solo un'identità gestita. Dopo che l'utente registra il dispositivo o l'app, l'SDK usa questa identità, considerandola l'identità primaria gestita. Gli altri utenti dell'app vengono trattati come non gestiti con impostazioni di criteri senza restrizioni.

Si noti che un'identità viene semplicemente definita come stringa. Le identità non fanno distinzione tra maiuscole e minuscole. Le richieste di identità all'SDK potrebbero non restituire la stessa combinazione di maiuscole e minuscole usata originariamente durante l'impostazione dell'identità.

### <a name="identity-overview"></a>Panoramica dell'identità

Un'identità è costituita semplicemente dal nome utente di un account, ad esempio user@contoso.com. Gli sviluppatori possono impostare l'identità dell'app sui livelli seguenti:

* **Identità del processo**: imposta l'identità per l'intero processo e viene usata principalmente per applicazioni a identità singola. Questa identità influisce su attività, file e interfaccia utente.

* **Identità dell'interfaccia utente**: determina quali criteri vengono applicati alle attività dell'interfaccia utente nel thread principale, ad esempio taglia/copia/incolla, PIN, autenticazione e condivisione dati. L'identità dell'interfaccia utente non influisce su attività di file, come la crittografia e il backup.

* **Identità del thread**: influisce sui criteri applicati al thread corrente. Questa identità influisce su attività, file e interfaccia utente.

L'app deve impostare le identità in modo appropriato, indipendentemente dal fatto che l'utente sia gestito.

In qualsiasi momento, ogni thread ha un'identità effettiva per le attività dell'interfaccia utente e le attività di file. Si tratta dell'identità usata per determinare i criteri da applicare, se presenti. Se l'identità non esiste o l'utente non è gestito, non viene applicato alcun criterio. I diagrammi seguenti illustrano come vengono determinate le identità effettive.

  ![Intune App SDK per iOS: Linked Frameworks and Libraries (Framework e librerie collegati)](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>Code di thread

Le app inviano spesso attività sincrone e asincrone alle code del thread. L'SDK intercetta le chiamate a Grand Central Dispatch (GCD) e associa l'identità del thread corrente alle attività inviate. Al termine delle attività, l'SDK modifica temporaneamente l'identità del thread nell'identità associata alle attività, completa le attività e ripristina l'identità del thread originale.


`NSOperationQueue` si basa su GCD, di conseguenza `NSOperations` verrà eseguito sull'identità del thread nel momento in cui sono state aggiunte le attività a `NSOperationQueue`. `NSOperations` o le funzioni inviate direttamente con GCD possono anche modificare l'identità del thread corrente durante l'esecuzione. Questa identità sovrascrive l'identità ereditata dal thread di invio.

### <a name="file-owner"></a>Proprietario dei file

L'SDK tiene traccia delle identità dei proprietari dei file locali e di conseguenza applica i criteri. Un proprietario del file viene stabilito al momento della creazione del file o quando un file viene aperto in modalità di troncamento. Il proprietario viene impostato sull'identità dell'attività di file effettiva del thread che esegue l'attività.

In alternativa, le app possono impostare l'identità del proprietario del file in modo esplicito usando `IntuneMAMFilePolicyManager`. Le app possono usare `IntuneMAMFilePolicyManager` per recuperare il proprietario del file e impostare l'identità dell'interfaccia utente prima di visualizzare il contenuto del file.

### <a name="shared-data"></a>Dati condivisi

Se l'app crea file che contengono dati di utenti gestiti e non gestiti, l'app deve crittografare i dati dell'utente gestito. È possibile crittografare i dati usando le API `protect` e `unprotect` in `IntuneMAMDataProtectionManager`.

Il metodo `protect` accetta un'identità che può corrispondere a un utente gestito o non gestito. Se l'utente è gestito, i dati verranno crittografati. Se l'utente non è gestito, verrà aggiunta un'intestazione ai dati per la codifica dell'identità, ma i dati non verranno crittografati. Il metodo `protectionInfo` può essere usato per recuperare il proprietario dei dati.

### <a name="share-extensions"></a>Condividere le estensioni

Se l'app contiene un'estensione per condivisione, il proprietario dell'elemento condiviso può essere recuperato con il metodo `protectionInfoForItemProvider` in `IntuneMAMDataProtectionManager`. Se l'elemento condiviso è un file, l'SDK gestirà l'impostazione del proprietario del file. Se l'elemento condiviso è costituito da dati, l'app deve impostare il proprietario del file se questi dati vengono salvati in un file e deve chiamare l'API `setUIPolicyIdentity` prima di visualizzare i dati nell'interfaccia utente.

### <a name="turning-on-multi-identity"></a>Abilitazione delle identità multiple

Per impostazione predefinita, le app sono considerate a identità singola. L'SDK imposta l'identità del processo per l'utente registrato. Per abilitare il supporto per le identità multiple, aggiungere un'impostazione booleana denominata `MultiIdentity` e un valore YES (Sì) al dizionario IntuneMAMSettings nel file Info.plist dell'app.

> [!NOTE]
> Quando vengono abilitate le identità multiple, l'identità del processo, l'identità dell'interfaccia utente e le identità del thread vengono impostate su nil. L'app deve impostare correttamente questi elementi.

### <a name="switching-identities"></a>Cambio di identità

* **Cambio di identità avviato dall'app**:

    All'avvio, si considera che le app con identità multiple siano in esecuzione con un account sconosciuto e non gestito. L'interfaccia utente dell'avvio condizionale non verrà eseguita e all'app non verrà applicato alcun criterio. L'app deve comunicare all'SDK ogni volta che l'identità deve essere modificata. In genere, succede ogni volta che l'app sta per visualizzare i dati di un account utente specifico.

    Si verifica ad esempio quando l'utente prova ad aprire un documento, una cassetta postale o una scheda in un notebook. L'app deve inviare una notifica all'SDK prima che venga effettivamente aperto il file, la cassetta postale o la scheda. Questa operazione viene eseguita tramite l'API `setUIPolicyIdentity` in `IntuneMAMPolicyManager`. Questa API deve essere chiamata indipendentemente dal fatto che l'utente sia gestito. Se l'utente è gestito, l'SDK eseguirà le verifiche di avvio condizionale, ad esempio rilevamento jailbreak, PIN e autenticazione.

    Il risultato del cambio d'identità viene restituito all'app in modo sincrono tramite un gestore di completamento. L'app deve rimandare l'apertura del documento, della cassetta postale o della scheda finché non viene restituito un codice risultato positivo. Se il cambio di identità non riesce, l'app deve annullare l'attività.

* **Cambio di identità avviato dall'SDK**:

    In alcuni casi l'SDK deve chiedere all'app di passare a un'identità specifica. Le app con identità multiple devono implementare il metodo `identitySwitchRequired` in `IntuneMAMPolicyDelegate` per gestire tale richiesta.

    Quando viene chiamato questo metodo, se l'app può gestire la richiesta per passare all'identità specificata, deve passare `IntuneMAMAddIdentityResultSuccess` al gestore di completamento. Se l'app non può gestire il cambio di identità, deve passare `IntuneMAMAddIdentityResultFailed` al gestore di completamento.

    L'app non deve chiamare `setUIPolicyIdentity` in risposta a questa chiamata. Se l'SDK chiede all'app di passare a un account utente non gestito, la stringa vuota verrà passata alla chiamata `identitySwitchRequired`.

* **Cancellazione selettiva**:

    Quando all'app viene applicata la cancellazione selettiva, l'SDK chiama il metodo `wipeDataForAccount` in `IntuneMAMPolicyDelegate`. L'app deve rimuovere l'account utente specificato ed eventuali dati associati. L'SDK può rimuovere tutti i file dell'utente e può eseguire questa operazione se l'app restituisce FALSE dalla chiamata a `wipeDataForAccount`.

    Si noti che questo metodo viene chiamato da un thread in background. L'app non deve restituire un valore finché non vengono rimossi tutti i dati dell'utente, ad eccezione dei file, se l'applicazione restituisce FALSE.

## <a name="test-app-protection-policy-settings-in-xcode"></a>Testare le impostazioni dei criteri di protezione delle app in Xcode

Prima di testare manualmente l'app abilitata per Intune in ambiente di produzione, è possibile usare il file Settings.bundle in Xcode. In questo modo, sarà possibile impostare i criteri di protezione delle app per scopi di test senza che sia necessaria una connessione a Intune.

### <a name="enable-policy-testing"></a>Abilitare i test dei criteri

Seguire questa procedura per abilitare i test dei criteri in Xcode:

1. Assicurarsi di usare una build di debug. Aggiungere un file Settings.bundle facendo clic con il pulsante destro del mouse sulla cartella di primo livello nel progetto. Scegliere **Add** > **New File** (Aggiungi > Nuovo file) dal menu. In **Resources** (Risorse) scegliere il modello **Settings Bundle** (Bundle impostazioni).

2.  Copiare il blocco seguente nel file Settings.bundle/**Root.plist** per la build di debug:
    ```xml
    <key>PreferenceSpecifiers</key>
    <array>
        <dict>
            <key>Type</key>
            <string>PSChildPaneSpecifier</string>
            <key>Title</key>
            <string>MDM Debug Settings</string>
            <key>Key</key>
            <string>MAMDebugSettings</string>
            <key>File</key>
            <string>MAMDebugSettings</string>
        </dict>
    </array>
    ```

3. Aggiungere un valore booleano denominato "DebugSettingsEnabled." nel dizionario **IntuneMAMSettings** nel file Info.plist dell'app. Impostare il valore DebugSettingsEnabled su "YES" (Sì).



### <a name="app-protection-policy-settings"></a>Impostazioni dei criteri di protezione delle app

La tabella seguente descrive le impostazioni dei criteri di protezione delle app che è possibile testare tramite MAMDebugSettings.plist. Per abilitare un'impostazione, aggiungerla in MAMDebugSettings.plist.

| Nome dell'impostazione dei criteri | Descrizione | Valori possibili |
| -- | -- | -- |
| AccessRecheckOfflineTimeout | Durata in minuti per la quale l'app può rimanere offline prima che Intune impedisca l'avvio o la ripresa dell'app se è abilitata l'autenticazione. | Qualsiasi numero intero maggiore di 0 |
|   AccessRecheckOnlineTimeout | Durata in minuti per la quale l'app può essere eseguita prima che all'utente venga richiesto un PIN o l'autenticazione in fase di avvio o ripresa, se è abilitata l'immissione del PIN o l'autenticazione per l'accesso. | Qualsiasi numero intero maggiore di 0 |
| AppSharingFromLevel | Specifica le app da cui questa app può accettare i dati. | 0 = |
## <a name="ios-best-practices"></a>Procedure consigliate per iOS

Di seguito alcune procedure consigliate per lo sviluppo per iOS:

* Il file system iOS distingue tra maiuscole e minuscole. Verificare che l'uso di minuscole e maiuscole sia corretto per i nomi di file come `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

* Se Xcode non trova `libIntuneMAM.a`, è possibile risolvere il problema aggiungendo il percorso di questa libreria ai percorsi di ricerca del linker.

## <a name="faqs"></a>Domande frequenti


**Tutte le API sono indirizzabili tramite Swift nativo o l'interoperabilità tra Objective-C e Swift?**

Le API di Intune App SDK sono disponibili solo in Objective-C e non supportano Swift **nativo**. È necessaria l'interoperabilità di Swift con Objective-C.


**Tutti gli utenti dell'applicazione devono essere registrati con il servizio APP-WE?**

No. Solo gli account aziendali o dell'istituto di istruzione devono essere registrati con Intune App SDK. Le app devono determinare se un account viene usato in un contesto aziendale o dell'istituto di istruzione.   

**Gli utenti che hanno già eseguito l'accesso all'applicazione devono essere registrati?**

L'applicazione deve registrare gli utenti dopo che sono stati autenticati. L'applicazione deve anche registrare tutti gli account esistenti presenti prima che l'applicazione includesse la funzionalità MAM senza MDM.   

A tale scopo, l'applicazione userà il metodo `registeredAccounts:`. Questo metodo restituisce NSDictionary che contiene tutti gli account registrati nel servizio MAM di Intune. Se eventuali account esistenti nell'applicazione non sono presenti nell'elenco, l'applicazione deve registrarli con `registerAndEnrollAccount:`.

**Con quale frequenza l'SDK riprova a eseguire le registrazioni?**

L'SDK riprova automaticamente a eseguire tutte le registrazioni non riuscite in precedenza in un intervallo di 24 ore. L'SDK esegue questa operazione per verificare che l'utente registri e riceva correttamente i criteri se l'organizzazione ha abilitato MAM dopo l'accesso dell'utente all'applicazione.

L'SDK smette di riprovare quando rileva che un utente ha registrato correttamente l'applicazione. Questo perché solo un utente può registrare un'applicazione in un determinato momento. Se viene annullata la registrazione di un utente, i nuovi tentativi inizieranno nuovamente nello stesso intervallo di 24 ore.

**Perché è necessario annullare la registrazione dell'utente?**

L'SDK esegue periodicamente queste azioni in background:

 - Se l'applicazione non è ancora registrata, l'SDK tenterà di registrare tutti gli account registrati ogni 24 ore.
 - Se l'applicazione è registrata, l'SDK controllerà la presenza di aggiornamenti dei criteri di protezione delle app ogni 8 ore.

Annullando la registrazione di un utente, viene comunicato all'SDK che l'utente non userà più l'applicazione. L'SDK può quindi arrestare gli eventi periodici per tale account utente. Se necessario, viene anche attivata una procedura di annullamento della registrazione e di cancellazione selettiva.

**È necessario impostare il contrassegno doWipe su true nel metodo deregister?**

Questo metodo deve essere chiamato prima che l'utente venga disconnesso dall'applicazione.  Se i dati dell'utente vengono eliminati dall'applicazione durante la disconnessione, è possibile impostare `doWipe` su false. Tuttavia, se l'applicazione non rimuove i dati dell'utente, `doWipe` deve essere impostato su true in modo che l'SDK possa eliminare i dati.

**Sono disponibili altre modalità di annullamento della registrazione dell'applicazione?**

Sì. L'amministratore IT può inviare un comando di cancellazione selettiva all'applicazione. Il comando annulla la registrazione dell'utente e cancella selettivamente i dati dell'utente. L'SDK gestisce questo scenario automaticamente e invia una notifica usando un metodo delegato di annullamento della registrazione.



## <a name="submit-your-app-to-the-app-store"></a>Inviare l'app all'App Store

Sia la libreria statica che le build del framework di Intune App SDK sono file binari universali. Ciò significa che hanno un codice per tutte le architetture del dispositivo e del simulatore. Apple rifiuta le app inviate all'App Store se contengono codice del simulatore. Durante la compilazione con la libreria statica per le build del dispositivo, il linker rimuove automaticamente il codice del simulatore. Seguire questa procedura per rimuovere tutto il codice del simulatore prima di caricare l'app nell'App Store.

1. Assicurarsi che `IntuneMAM.framework` sia presente nel desktop.

2. Eseguire i comandi seguenti:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```
    Il primo comando rimuove le architetture del simulatore dal file DYLIB del framework. Il secondo comando copia il file DYLIB del dispositivo nella directory del framework.
