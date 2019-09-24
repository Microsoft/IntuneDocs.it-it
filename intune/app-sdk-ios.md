---
title: Guida per gli sviluppatori di Microsoft Intune App SDK per iOS
description: Microsoft Intune App SDK per iOS consente di integrare i criteri di protezione delle app di Intune, noti anche come criteri APP o MAM, nell'app iOS nativa.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/17/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea31c06019643a3eaf10d79857dfdc319a8453c3
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167222"
---
# <a name="microsoft-intune-app-sdk-for-ios-developer-guide"></a>Guida per gli sviluppatori di Microsoft Intune App SDK per iOS

> [!NOTE]
> Può essere utile leggere prima l'articolo [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.

Microsoft Intune App SDK per iOS consente di integrare i criteri di protezione delle app di Intune, noti anche come criteri APP o MAM, nell'app iOS nativa. Un'applicazione abilitata per la gestione delle applicazioni mobili è un'applicazione integrata con Intune App SDK. Gli amministratori IT possono distribuire i criteri di protezione all'app per dispositivi mobili quando Intune gestisce attivamente l'app.

## <a name="prerequisites"></a>Prerequisiti

* È necessario un computer Mac OS che esegua OS X 10.8.5 o versione successiva e in cui sia anche installato Xcode 9 o versione successiva.

* L'app deve essere destinata a iOS 10 o versione successiva.

* Rivedere le [Condizioni di licenza di Intune App SDK per iOS](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios/blob/master/Microsoft%20License%20Terms%20Intune%20App%20SDK%20for%20iOS.pdf). Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando Intune App SDK per iOS, l'utente accetta tali condizioni di licenza.  Se non vengono accettate, non usare il software.

* Scaricare i file per Intune App SDK per iOS in [GitHub](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios).

## <a name="whats-in-the-sdk-repository"></a>Contenuti nel repository SDK

I file seguenti sono rilevanti per le app o le estensioni che non contengono codice Swift oppure sono compilate con una versione di Xcode precedente alla 10,2:

* **IntuneMAM.framework**: framework di Intune App SDK. È consigliabile collegare questo Framework alle app/estensioni per abilitare la gestione delle applicazioni client di Intune. Tuttavia, è possibile che alcuni sviluppatori preferisca sfruttare i vantaggi delle prestazioni della libreria statica. Vedere di seguito.

* **libIntuneMAM.a**: libreria statica di Intune App SDK. Gli sviluppatori possono scegliere di collegare la libreria statica anziché il Framework. Poiché le librerie statiche sono incorporate direttamente nel file binario di estensione/app in fase di compilazione, l'uso della libreria statica presenta alcuni vantaggi a livello di prestazioni in fase di avvio. Tuttavia, l'integrazione nell'app è un processo più complesso. Se l'app include tutte le estensioni, il collegamento della libreria statica all'app e le estensioni comporteranno dimensioni del bundle dell'app maggiori, perché la libreria statica verrà incorporata in ogni file binario di app/estensione. Quando si usa il Framework, le app e le estensioni possono condividere lo stesso file binario di Intune SDK, ottenendo dimensioni di app inferiori.

* **IntuneMAMResources.bundle**: bundle di risorse contenente le risorse da cui dipende l'SDK. Il bundle di risorse è necessario solo per le app che integrano la libreria statica (libIntuneMAM. a).

I file seguenti sono rilevanti per app/estensioni che contengono codice Swift e vengono compilati con Xcode 10.2 +:

* **IntuneMAMSwift. Framework**: Framework Swift di INTUNE App SDK. Questo Framework contiene tutte le intestazioni per le API che verrà chiamata dall'app. Collegare questo Framework alle app/estensioni per abilitare la gestione delle applicazioni client di Intune.

* **IntuneMAMSwiftStub. Framework**: Framework dello stub Swift di INTUNE App SDK. Si tratta di una dipendenza obbligatoria di IntuneMAMSwift. Framework che deve essere collegata a app/estensioni.


I file seguenti sono rilevanti per tutte le app/extent:

* **IntuneMAMConfigurator**: uno strumento usato per configurare il file INFO. plist dell'app o dell'estensione con le modifiche minime necessarie per la gestione di Intune. A seconda della funzionalità dell'applicazione o dell'estensione, potrebbe essere necessario apportare altre modifiche manuali al file INFO. plist.

* **Intestazioni**: espongono le API pubbliche di Intune App SDK. Queste intestazioni sono incluse nei framework IntuneMAM/IntuneMAMSwift, quindi gli sviluppatori che utilizzano uno dei Framework non devono aggiungere manualmente le intestazioni al progetto. Gli sviluppatori che scelgono di eseguire il collegamento alla libreria statica (libIntuneMAM. a) dovranno includere manualmente queste intestazioni nel progetto.

I file di intestazione seguenti includono API, tipi di dati e protocolli resi disponibili agli sviluppatori da Intune App SDK:

-  IntuneMAMAppConfig.h
-  IntuneMAMAppConfigManager.h
-  IntuneMAMDataProtectionInfo.h
-  IntuneMAMDataProtectionManager.h
-  IntuneMAMDefs.h
-  IntuneMAMDiagnosticConsole.h
-  IntuneMAMEnrollmentDelegate.h
-  IntuneMAMEnrollmentManager.h
-  IntuneMAMEnrollmentStatus.h
-  IntuneMAMFileProtectionInfo.h
-  IntuneMAMFileProtectionManager.h
-  IntuneMAMLogger.h
-  IntuneMAMPolicy.h
-  IntuneMAMPolicyDelegate.h
-  IntuneMAMPolicyManager.h
-  IntuneMAMVersionInfo.h

Gli sviluppatori possono rendere disponibile il contenuto di tutte le intestazioni precedenti importando IntuneMAM.h


## <a name="how-the-intune-app-sdk-works"></a>Funzionamento di Intune App SDK

L'obiettivo di Intune App SDK per iOS è quello di aggiungere funzionalità di gestione per le applicazioni iOS con modifiche minime al codice. Riducendo la quantità di modifiche al codice, si accelerano i tempi di immissione sul mercato, preservando nel contempo la coerenza e la stabilità dell'applicazione per dispositivi mobili.


## <a name="build-the-sdk-into-your-mobile-app"></a>Compilare l'SDK nell'app per dispositivi mobili

Per abilitare Intune App SDK, seguire questa procedura:

1. **Opzione 1-Framework (scelta consigliata)** : se si usa Xcode 10.2 + e l'app o l'estensione contiene codice Swift `IntuneMAMSwift.framework` , `IntuneMAMSwiftStub.framework` collegamento e alla destinazione: `IntuneMAMSwift.framework` trascinare `IntuneMAMSwiftStub.framework` e nell'elenco dei **file binari incorporati** del destinazione progetto.

    In caso contrario `IntuneMAM.framework` , collegarsi alla destinazione `IntuneMAM.framework` : trascinare nell'elenco dei **file binari incorporati** della destinazione del progetto.

   > [!NOTE]
   > Se si usa il framework, prima di inviare l'app all'App Store, è necessario eliminare manualmente le architetture del simulatore dal framework universale. Per altri dettagli, vedere [Inviare l'app all'App Store](#submit-your-app-to-the-app-store).

   **Opzione 2-libreria statica**: questa opzione è disponibile solo per le app/estensioni che non contengono codice Swift oppure sono state compilate con Xcode < 10,2. eseguire il collegamento alla libreria `libIntuneMAM.a`. Trascinare la libreria `libIntuneMAM.a` e rilasciarla nell'elenco **Linked Frameworks and Libraries** (Framework e librerie collegate) della destinazione del progetto.

    ![Intune App SDK iOS: framework e librerie collegati](./media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)

    Aggiungere `-force_load {PATH_TO_LIB}/libIntuneMAM.a` in una delle posizioni seguenti, sostituendo `{PATH_TO_LIB}` con il percorso di Intune App SDK:
   * Impostazione di configurazione della build `OTHER_LDFLAGS` del progetto.
   * Opzione **Other Linker Flags** (Altri contrassegni del linker) nell'interfaccia utente di Xcode.

     > [!NOTE]
     > Per trovare `PATH_TO_LIB`, selezionare il file `libIntuneMAM.a` e scegliere **Get Info** (Ottieni informazioni) dal menu **File**. Copiare e incollare le informazioni indicate in **Where** (Dove), ovvero il percorso, dalla sezione **General** (Generale) della finestra **Info** (Informazioni).

     Aggiungere il bundle di risorse `IntuneMAMResources.bundle` al progetto trascinandolo in **Copy Bundle Resources** (Copia le risorse del bundle) in **Build Phases** (Crea fasi).

     ![Intune App SDK iOS: opzione Copy Bundle Resources (Copia le risorse del bundle)](./media/intune-app-sdk-ios-copy-bundle-resources.png)
         
2. Aggiungere i framework iOS seguenti al progetto:  
-  MessageUI.framework  
-  Security.framework  
-  MobileCoreServices.framework  
-  SystemConfiguration.framework  
-  libsqlite3.tbd  
-  libc++.tbd  
-  ImageIO.framework  
-  LocalAuthentication.framework  
-  AudioToolbox.framework  
-  QuartzCore.framework  
-  WebKit.framework

3. Abilitare la condivisione Keychain, se non è già abilitata, facendo clic su **Capabilities** (Funzionalità) in ogni destinazione del progetto e abilitando l'opzione **Keychain Sharing** (Condivisione Keychain). La condivisione Keychain è necessaria per procedere con il passaggio successivo.

   > [!NOTE]
   > Il profilo di provisioning deve supportare i nuovi valori di condivisione Keychain. I gruppi di accesso a Keychain devono supportare un carattere jolly. Per verificarlo, aprire il file .mobileprovision in un editor di testo, cercare **keychain-access-groups** e verificare che sia presente un carattere jolly. Ad esempio:
   >
   >  ```xml
   >  <key>keychain-access-groups</key>
   >  <array>
   >  <string>YOURBUNDLESEEDID.*</string>
   >  </array>
   >  ```

4. Dopo avere abilitato la condivisione Keychain, completare i passaggi seguenti per creare un gruppo di accesso separato in cui Intune App SDK archivierà i dati. È possibile creare un gruppo di accesso a Keychain usando l'interfaccia utente o il file di diritti. Se si usa l'interfaccia utente per creare un gruppo di accesso a Keychain, assicurarsi di eseguire questi passaggi:

     a. Se per l'app per dispositivi mobili non sono definiti gruppi di accesso a Keychain, aggiungere l'ID bundle dell'app come **primo** gruppo.
    
    b. Aggiungere il gruppo di Keychain condiviso `com.microsoft.intune.mam` ai gruppi di accesso esistenti. Questo è il gruppo di accesso usato da Intune App SDK per archiviare i dati.
    
    c. Aggiungere `com.microsoft.adalcache` ai gruppi di accesso esistenti.
    
      ![Intune App SDK per iOS: condivisione Keychain](./media/intune-app-sdk-ios-keychain-sharing.png)
    
    d. Se si modifica il file dei diritti direttamente, anziché tramite l'interfaccia utente di Xcode illustrata in precedenza per creare i gruppi di accesso keychain, anteporre il prefisso `$(AppIdentifierPrefix)` ai gruppi di accesso keychain (Xcode gestisce questo aspetto automaticamente). Ad esempio:
    
      - `$(AppIdentifierPrefix)com.microsoft.intune.mam`
      - `$(AppIdentifierPrefix)com.microsoft.adalcache`
    
      > [!NOTE]
      > Un file di diritti è un file XML specifico per l'applicazione mobile. Consente di specificare autorizzazioni e funzionalità speciali nell'app per iOS. Se l'app non aveva in precedenza un file dei diritti, in seguito all'abilitazione della condivisione del keychain (passaggio 3) Xcode dovrebbe averne generato uno per l'app. Verificare che l'ID bundle dell'app sia la prima voce nell'elenco.

5. Includere ogni protocollo passato dall'app a `UIApplication canOpenURL` nella matrice `LSApplicationQueriesSchemes` del file Info.plist dell'app. Assicurarsi di salvare le modifiche prima di procedere al passaggio successivo.

6. Se l'app non usa già FaceID, verificare che la [chiave NSFaceIDUsageDescription Info.plist](https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/CocoaKeys.html#//apple_ref/doc/uid/TP40009251-SW75) sia configurata con un messaggio predefinito. Ciò è necessario affinché iOS possa comunicare all'utente il modo in cui l'app intende usare FaceID. Un'impostazione dei criteri di protezione delle app di Intune consente l'uso di FaceID come metodo di accesso all'app, se configurato dall'amministratore IT.

7. Usare lo strumento IntuneMAMConfigurator incluso nel [repository SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-ios) per completare la configurazione del file Info.plist dell'app. Lo strumento ha tre parametri:

   |Proprietà|Modo d'uso|
   |---------------|--------------------------------|
   |- i |  `<Path to the input plist>` |
   |- e | `<Path to the entitlements file>` |
   |- o |  (Facoltativo) `<Path to the output plist>` |

Se il parametro '-o' viene omesso, il file di input verrà modificato sul posto. Lo strumento è idempotente e deve essere eseguito di nuovo dopo ogni modifica del file Info.plist o dei diritti dell'app. È anche consigliabile scaricare ed eseguire la versione più recente dello strumento quando si aggiorna Intune SDK, nel caso i requisiti di configurazione di Info.plist siano cambiati nella versione più recente.

## <a name="configure-adalmsal"></a>Configurare ADAL/MSAL

Intune App SDK può usare la libreria di [autenticazione Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) o [Microsoft Authentication Library](https://github.com/AzureAD/microsoft-authentication-library-for-objc) per gli scenari di autenticazione e avvio condizionale. Si basa su ADAL/MSAL anche per registrare l'identità utente nel servizio MAM per la gestione senza scenari di registrazione del dispositivo.

ADAL/MSAL richiedono in genere che le app eseguano la registrazione in Azure Active Directory (AAD) e creino un ID client univoco e un URI di reindirizzamento per garantire la sicurezza dei token concessi all'app. Se l'app usa già ADAL o MSAL per l'autenticazione degli utenti, l'app deve usare i valori di registrazione esistenti ed eseguire l'override dei valori predefiniti di Intune App SDK. In questo modo agli utenti non viene richiesta la doppia autenticazione, una di Intune App SDK e una dell'app.

Se l'app non usa già ADAL o MSAL e non è necessario accedere a una risorsa di AAD, non è necessario configurare una registrazione dell'app client in AAD se si sceglie di integrare ADAL. Se si decide di integrare MSAL, è necessario configurare una registrazione per l'app ed eseguire l'override dell'ID client di Intune e dell'URI di reindirizzamento predefiniti.  

È consigliabile collegare l'app alla versione più recente di [adal](https://github.com/AzureAD/azure-activedirectory-library-for-objc/releases) o [MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases).

### <a name="link-to-adal-or-msal-binaries"></a>Collegamento ai file binari di ADAL o MSAL

**Opzione 1-** Seguire [questa procedura](https://github.com/AzureAD/azure-activedirectory-library-for-objc#download) per collegare l'app ai file binari di adal.

**Opzione 2-** In alternativa, è possibile seguire [queste istruzioni](https://github.com/AzureAD/microsoft-authentication-library-for-objc#installation) per collegare l'app ai file binari di MSAL.

1. Se per l'app non sono definiti gruppi di accesso a Keychain, aggiungere l'ID bundle dell'app come primo gruppo.

2. Abilitare Single Sign-On (SSO) di ADAL/MSAL aggiungendo `com.microsoft.adalcache` ai gruppi di accesso al keychain.

3. Nel caso in cui si stia impostando in modo esplicito il gruppo Keychain della cache condivisa, assicurarsi di impostarlo su `<appidprefix>.com.microsoft.adalcache`. ADAL eseguirà questa operazione per conto dell'utente se quest'ultimo non esegue la sostituzione. Se si vuole specificare un gruppo Keychain personalizzato per sostituire `com.microsoft.adalcache`, specificarlo nel file Info.plist in IntuneMAMSettings usando la chiave `ADALCacheKeychainGroupOverride`.

### <a name="configure-adalmsal-settings-for-the-intune-app-sdk"></a>Configurare le impostazioni di ADAL/MSAL per Intune App SDK

Se l'app usa già ADAL o MSAL per l'autenticazione e ha impostazioni di Azure Active Directory proprie, è possibile forzare l'uso delle stesse impostazioni in Intune App SDK durante l'autenticazione con AAD. Ciò garantisce che l'app non richieda due volte l'intervento dell'utente per l'autenticazione. Vedere [Configurare le impostazioni per Intune App SDK](#configure-settings-for-the-intune-app-sdk) per informazioni sulla compilazione delle impostazioni seguenti:  

* ADALClientId
* ADALAuthority
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

Se l'app usa già ADAL o MSAL, sono necessarie le configurazioni seguenti:

1. Nel file Info.plist del progetto, in un dizionario **IntuneMAMSettings** con il nome di chiave `ADALClientId`, specificare l'ID client da usare per le chiamate ADAL.

2. Nel dizionario **IntuneMAMSettings** con il nome di chiave `ADALAuthority`, specificare inoltre l'autorità di Azure AD.

3. Nel dizionario **IntuneMAMSettings** con il nome di chiave `ADALRedirectUri`, specificare inoltre l'URI di reindirizzamento da usare per le chiamate a ADAL. In alternativa è possibile specificare `ADALRedirectScheme`, se l'URI di reindirizzamento dell'applicazione è nel formato `scheme://bundle_id`.

Inoltre, le app possono ignorare queste impostazioni di Azure AD in fase di esecuzione. A tale scopo, impostare semplicemente le proprietà `aadAuthorityUriOverride`, `aadClientIdOverride` e `aadRedirectUriOverride` nell'istanza `IntuneMAMPolicyManager`.

4. Assicurarsi di seguire i passaggi per concedere le autorizzazioni delle app iOS al servizio dei criteri di protezione delle app. Usare le istruzioni in [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md#next-steps-after-integration) in "[Concedere all'app l'accesso al servizio di protezione delle app di Intune (facoltativo)](app-sdk-get-started.md#give-your-app-access-to-the-intune-app-protection-service-optional)".  

> [!NOTE]
> L'approccio basato sul file Info.plist è consigliato per tutte le impostazioni statiche, che non è necessario determinare in fase di esecuzione. I valori assegnati alle proprietà `IntuneMAMPolicyManager` hanno la precedenza su qualsiasi altro valore corrispondente specificato nel file Info.plist e verranno mantenuti anche dopo il riavvio dell'app. L'SDK continuerà a usarli per le archiviazioni dei criteri finché non viene annullata registrazione dell'utente o fino a quando i valori non vengono cancellati o modificati.

### <a name="if-your-app-does-not-use-adal-or-msal"></a>Se l'applicazione non usa ADAL o MSAL

Come indicato in precedenza, Intune App SDK può usare la [libreria di autenticazione Azure Active Directory](https://github.com/AzureAD/azure-activedirectory-library-for-objc) o [Microsoft Authentication Library](https://github.com/AzureAD/microsoft-authentication-library-for-objc) per gli scenari di autenticazione e avvio condizionale. Si basa su ADAL/MSAL anche per registrare l'identità utente nel servizio MAM per la gestione senza scenari di registrazione del dispositivo. Se **l'app non usa adal o MSAL per il proprio meccanismo di autenticazione**, potrebbe essere necessario configurare le impostazioni di AAD personalizzate, a seconda della libreria di autenticazione che si sceglie di integrare:   

ADAL - Intune App SDK specifica i valori predefiniti per i parametri ADAL e gestisce l'autenticazione con Azure AD. Gli sviluppatori non devono specificare alcun valore per le impostazioni ADAL citate in precedenza. 

MSAL: gli sviluppatori devono creare una registrazione dell'app in AAD con un URI di reindirizzamento personalizzato nel formato specificato [qui](https://github.com/AzureAD/microsoft-authentication-library-for-objc/wiki/Migrating-from-ADAL-Objective-C-to-MSAL-Objective-C#app-registration-migration). Gli sviluppatori devono impostare `ADALClientID` le `ADALRedirectUri` impostazioni e indicate in precedenza oppure le `aadClientIdOverride` proprietà `aadRedirectUriOverride` e `IntuneMAMPolicyManager` equivalenti dell'istanza. Gli sviluppatori devono anche assicurarsi che seguano il passaggio 4 della sezione precedente, per concedere l'accesso alla registrazione dell'app al servizio di protezione delle app di Intune.

### <a name="special-considerations-when-using-msal"></a>Considerazioni speciali sull'uso di MSAL 

1. **Controllare la visualizzazione WebView** : è consigliabile che le applicazioni non usino SFSafariViewController, SFAuthSession o ASWebAuthSession come WebView per tutte le operazioni di autenticazione interattive MSAL avviate dall'app. Se per qualche motivo l'app deve usare una di queste Webviews per tutte le operazioni di autenticazione MSAL interattive, è necessario `SafariViewControllerBlockedOverride` impostare `true` anche su `IntuneMAMSettings` sotto il dizionario nel file INFO. plist dell'applicazione. AVVISO: gli hook SafariViewController di Intune vengono disabilitati per abilitare la sessione di autenticazione. Ciò consente di evitare perdite di dati in un'altra posizione nell'app se l'applicazione usa SafariViewController per visualizzare i dati aziendali, quindi l'applicazione non deve visualizzare i dati aziendali in nessuno di questi tipi di WebView.
2. **Collegamento di adal e MSAL** : gli sviluppatori devono acconsentire esplicitamente se desiderano che Intune preferisca MSAL su Adal in questo scenario. Per impostazione predefinita, Intune preferisce le versioni di ADAL supportate per le versioni MSAL supportate, se entrambe sono collegate in fase di esecuzione. Intune preferisce solo una versione di MSAL supportata quando, al momento della prima operazione di autenticazione di Intune, `IntuneMAMUseMSALOnNextLaunch` si `true` trova `NSUserDefaults`in. Se `IntuneMAMUseMSALOnNextLaunch` è `false` o non è impostato, Intune verrà eseguito il fallback al comportamento predefinito. Come suggerisce il nome, una modifica apportata a `IntuneMAMUseMSALOnNextLaunch` verrà applicata al successivo avvio.


## <a name="configure-settings-for-the-intune-app-sdk"></a>Configurare le impostazioni per Intune App SDK

Per installare e configurare Intune App SDK è possibile usare il dizionario **IntuneMAMSettings** incluso nel file Info.plist dell'applicazione. Se il dizionario IntuneMAMSettings non è visibile nel file Info.plist, è necessario crearlo.

Nel dizionario IntuneMAMSettings è possibile usare le seguenti impostazioni supportate per configurare Intune App SDK.

Alcune di queste impostazioni possono essere state descritte nelle sezioni precedenti e alcune non riguardano tutte le app.

Impostazione  | Tipo  | Definizione | Necessaria?
--       |  --   |   --       |  --
ADALClientId  | Stringa  | Identificatore del client Azure AD dell'app. | Obbligatorio per tutte le app che usano MSAL e qualsiasi app ADAL che accede a una risorsa AAD non Intune. |
ADALAuthority | Stringa | Autorità di Azure AD dell'app in uso. È necessario usare l'ambiente specifico in cui sono stati configurati gli account Azure AD. | Obbligatoria se l'app usa ADAL o MSAL per accedere a una risorsa AAD non Intune. Se questo valore è assente, viene usato un valore predefinito di Intune.|
ADALRedirectUri  | Stringa  | URI di reindirizzamento di Azure AD dell'app. | ADALRedirectUri o ADALRedirectScheme è obbligatorio per tutte le app che usano MSAL e qualsiasi app ADAL che accede a una risorsa AAD non Intune.  |
ADALRedirectScheme  | Stringa  | Schema di reindirizzamento di Azure AD dell'app. Può essere usata al posto di ADALRedirectUri se l'URI di reindirizzamento dell'applicazione è nel formato `scheme://bundle_id`. | ADALRedirectUri o ADALRedirectScheme è obbligatorio per tutte le app che usano MSAL e qualsiasi app ADAL che accede a una risorsa AAD non Intune. |
ADALLogOverrideDisabled | Boolean  | Specifica se l'SDK indirizzerà tutti i log ADAL/MSAL, incluse le eventuali chiamate ADAL dall'app, al proprio file di log. L'impostazione predefinita è NO. Impostare il valore su YES se l'app imposta la richiamata al log ADAL/MSAL. | Facoltativo. |
ADALCacheKeychainGroupOverride | Stringa  | Specifica il gruppo keychain da usare per la cache ADAL/MSAL al posto di "com.microsoft.adalcache". Si noti che non contiene il prefisso app-id. che verrà aggiunto alla stringa specificata in fase di runtime. | Facoltativo |
AppGroupIdentifiers | Matrice di stringhe  | Matrice di gruppi di app della sezione com.apple.security.application-groups dei diritti dell'app. | Necessaria se l'applicazione usa i gruppi di applicazioni. |
ContainingAppBundleId | Stringa | Specifica l'ID bundle dell'applicazione che contiene l'estensione. | Necessaria per le estensioni iOS. |
DebugSettingsEnabled| Boolean | Se impostata su Sì, è possibile applicare i criteri di test nell'ambito del bundle delle impostazioni. Le applicazioni *non* dovrebbero essere inviate con questa impostazione abilitata. | Facoltativo. L'impostazione predefinita è No. |
MainNibFile<br>MainNibFile~ipad  | Stringa  | Questa impostazione deve avere il nome del file NIB principale dell'applicazione.  | È obbligatoria se l'applicazione definisce MainNibFile in Info.plist. |
MainStoryboardFile<br>MainStoryboardFile~ipad  | Stringa  | Questa impostazione deve avere il nome del file di storyboard principale dell'applicazione. | È obbligatoria se l'applicazione definisce UIMainStoryboardFile in Info.plist. |
AutoEnrollOnLaunch| Boolean| Specifica se l'app deve tentare di registrarsi automaticamente all'avvio se viene rilevata un'identità gestita esistente e se tale operazione non è ancora stata compiuta. L'impostazione predefinita è NO. <br><br> Note: se non viene trovata alcuna identità gestita o non è disponibile alcun token valido per l'identità nella cache ADAL/MSAL, il tentativo di registrazione avrà esito negativo senza chiedere le credenziali, a meno che l'app non abbia configurato anche MAMPolicyRequired su YES. | Facoltativo. L'impostazione predefinita è No. |
MAMPolicyRequired| Boolean| Specifica se viene impedito l'avvio dell'app se non ha i criteri di protezione delle app di Intune. L'impostazione predefinita è NO. <br><br> Note: le app non possono essere inviate ad App Store se MAMPolicyRequired è impostato su YES. Quando si imposta MAMPolicyRequired su YES, anche AutoEnrollOnLaunch deve essere impostato su YES. | Facoltativo. L'impostazione predefinita è No. |
MAMPolicyWarnAbsent | Boolean| Specifica se l'app avvisa l'utente durante l'avvio se non ha i criteri di protezione delle app di Intune. <br><br> Nota: gli utenti potranno ancora usare l'app senza criterio dopo aver ignorato l'avviso. | Facoltativo. L'impostazione predefinita è No. |
MultiIdentity | Boolean| Specifica se l'app è compatibile con identità multiple. | Facoltativo. L'impostazione predefinita è No. |
SafariViewControllerBlockedOverride | Boolean| Disabilita gli hook SafariViewController di Intune per abilitare l'autenticazione MSAL tramite SFSafariViewController, SFAuthSession o ASWebAuthSession. | Facoltativo. L'impostazione predefinita è No. AVVISO: può causare la perdita di dati se utilizzata in modo errato. Abilitare solo se assolutamente necessario. Per informazioni dettagliate, vedere [considerazioni speciali sull'uso di MSAL](#special-considerations-when-using-msal) .  |
SplashIconFile <br>SplashIconFile~ipad | Stringa  | Specifica il file dell'icona per la schermata iniziale (avvio) di Intune. | Facoltativo |
SplashDuration | Numero | Quantità minima di tempo, in secondi, per la visualizzazione della schermata iniziale di Intune all'avvio dell'applicazione. Il valore predefinito è 1,5. | Facoltativo |
BackgroundColor| Stringa| Specifica il colore di sfondo per le schermate di avvio e PIN. Accetta una stringa RGB esadecimale nel formato #XXXXXX, dove X può variare da 0 a 9 o da A a F. Il segno di cancelletto può essere omesso.   | Facoltativo L'impostazione predefinita è grigio chiaro. |
ForegroundColor| Stringa| Specifica il colore di primo piano per le schermate di avvio e PIN, ad esempio il colore del testo. Accetta una stringa RGB esadecimale nel formato #XXXXXX, dove X può variare da 0 a 9 o da A a F. Il segno di cancelletto può essere omesso.  | Facoltativo L'impostazione predefinita è nero. |
AccentColor | Stringa| Specifica il colore principale della schermata del PIN, ad esempio il colore del testo del pulsante e il colore di evidenziazione della casella. Accetta una stringa RGB esadecimale nel formato #XXXXXX, dove X può variare da 0 a 9 o da A a F. Il segno di cancelletto può essere omesso.| Facoltativo L'impostazione predefinita è blu. |
MAMTelemetryDisabled| Boolean| Specifica se l'SDK non invierà i dati di telemetria al relativo back-end.| Facoltativo. L'impostazione predefinita è No. |
MAMTelemetryUsePPE | Boolean | Specifica se MAM SDK invierà dati al back-end dati di telemetria PPE. Usare questa impostazione durante il test delle app con i criteri di Intune in modo che i dati di telemetria di test non vengano confusi con i dati dei clienti. | Facoltativo. L'impostazione predefinita è No. |
MaxFileProtectionLevel | Stringa | Facoltativo. Consente all'app di specificare il massimo `NSFileProtectionType` che può supportare. Questo valore sostituirà il criterio inviato dal servizio se il livello è superiore rispetto a ciò che l'applicazione può supportare. Valori possibili: `NSFileProtectionComplete`, `NSFileProtectionCompleteUnlessOpen`, `NSFileProtectionCompleteUntilFirstUserAuthentication`, `NSFileProtectionNone`.|
OpenInActionExtension | Boolean | Impostare su YES per le estensioni Open In Action. Vedere la sezione Condividere dati tramite UIActivityViewController per maggiori informazioni. |
WebViewHandledURLSchemes | Matrice di stringhe | Specifica gli schemi URL gestiti dalla visualizzazione Web dell'app. | Obbligatoria se l'app usa una WebView che gestisce gli URL tramite collegamenti e/o JavaScript. |

## <a name="receive-app-protection-policy"></a>Ricevere i criteri di protezione delle app

### <a name="overview"></a>Panoramica

Per ricevere i criteri di protezione delle app di Intune, le app devono avviare una richiesta di registrazione nel servizio MAM di Intune. Le app possono essere configurate nella console di Intune per ricevere i criteri di protezione delle app con o senza registrazione del dispositivo. I criteri di protezione delle app senza registrazione, noti anche come **APP-WE** o MAM-WE, consentono la gestione delle app in Intune senza richiedere la registrazione del dispositivo nella gestione dei dispositivi mobili (MDM) di Intune. In entrambi i casi, la registrazione nel servizio MAM di Intune è obbligatoria per ricevere i criteri.

> [!Important]
> Intune App SDK per iOS usa le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. Tutte le app devono avere una versione corrente dell'SDK per consentire la condivisione dei dati protetta.

### <a name="apps-that-already-use-adal-or-msal"></a>App che usano già ADAL o MSAL

Le app che usano già ADAL o MSAL devono chiamare il metodo `registerAndEnrollAccount` sull'istanza `IntuneMAMEnrollmentManager` dopo che l'utente è stato autenticato:

```objc
/*
 *  This method will add the account to the list of registered accounts.
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK
 */

(void)registerAndEnrollAccount:(NSString *)identity;
```

Chiamando il metodo `registerAndEnrollAccount`, l'SDK registra l'account utente e prova a registrare l'app per conto di questo account. Se la registrazione non riesce per qualsiasi motivo, l'SDK riproverà automaticamente la registrazione dopo 24 ore. A scopo di debug, l'app può ricevere [notifiche](#status-result-and-debug-notifications) sui risultati di tutte le richieste di registrazione attraverso un delegato.

Dopo aver richiamato l'API, l'app può continuare a funzionare normalmente. Se la registrazione riesce, l'SDK notificherà all'utente che è necessario un riavvio dell'app. A questo punto, l'utente può riavviare l'app.

```objc
[[IntuneMAMEnrollmentManager instance] registerAndEnrollAccount:@”user@foo.com”];
```

### <a name="apps-that-do-not-use-adal-or-msal"></a>App che non usano ADAL o MSAL

Le app che non eseguono l'accesso utente con ADAL o MSAL possono comunque ricevere i criteri di protezione delle app dal servizio MAM di Intune chiamando l'API, perché l'autenticazione sia gestita dall'SDK. Le app devono usare questa tecnica quando l'utente non è stato autenticato con Azure AD, ma è comunque necessario recuperare i criteri di protezione delle app per proteggere i dati. Ad esempio, viene applicata quando viene usato un altro servizio di autenticazione per l'accesso dell'app o se l'app non supporta l'accesso. A tale scopo, l'applicazione può chiamare il metodo `loginAndEnrollAccount` sull'istanza `IntuneMAMEnrollmentManager`:

```objc
/**
 *  Creates an enrollment request which is started immediately.
 *  If no token can be retrieved for the identity, the user will be prompted
 *  to enter their credentials, after which enrollment will be retried.
 *  @param identity The UPN of the account to be logged in and enrolled.
 */
 (void)loginAndEnrollAccount: (NSString *)identity;
```

Chiamando questo metodo, l'SDK chiederà le credenziali dell'utente se non viene trovato alcun token esistente. L'SDK proverà quindi a registrare l'app nel servizio MAM di Intune per conto dell'account utente specificato. Il metodo può essere chiamato con l'identità "nil". In questo caso l'SDK eseguirà la registrazione con l'utente gestito esistente nel dispositivo (nel caso di MDM) o chiederà di specificare un nome se non trova utenti esistenti.

Se la registrazione ha esito negativo, l'app deve prendere in considerazione la necessità di chiamare l'API in un secondo momento, a seconda dei dettagli dell'errore. L'app può ricevere le [notifiche](#status-result-and-debug-notifications) sui risultati delle richieste di registrazione attraverso un delegato.

Dopo aver chiamato l'API, l'app può continuare a funzionare normalmente. Se la registrazione riesce, l'SDK notificherà all'utente che è necessario un riavvio dell'app.

Esempio:

```objc
[[IntuneMAMEnrollmentManager instance] loginAndEnrollAccount:@”user@foo.com”];
```

### <a name="let-intune-handle-authentication-and-enrollment-at-launch"></a>Consentire a Intune di gestire l'autenticazione e la registrazione al momento del lancio

Se si vuole che Intune SDK gestisca tutte le attività di registrazione e autenticazione tramite ADAL/MSAL prima del completamento dell'avvio dell'app e l'app richiede sempre i criteri APP, non è necessario usare l'API `loginAndEnrollAccount`. È sufficiente limitarsi a impostare le due impostazioni seguenti su YES nel dizionario IntuneMAMSettings all'interno del file Info.plist dell'app.

Impostazione  | Tipo  | Definizione |
--       |  --   |   --       |  
AutoEnrollOnLaunch| Boolean| Specifica se l'app deve tentare di registrarsi automaticamente all'avvio se viene rilevata un'identità gestita esistente e se tale operazione non è ancora stata compiuta. L'impostazione predefinita è NO. <br><br> Nota: se non viene trovata alcuna identità gestita o non è disponibile alcun token valido per l'identità nella cache ADAL/MSAL, il tentativo di registrazione avrà esito negativo senza chiedere le credenziali, a meno che l'app non abbia configurato anche MAMPolicyRequired su YES. |
MAMPolicyRequired| Boolean| Specifica se viene impedito l'avvio dell'app se non ha i criteri di protezione delle app di Intune. L'impostazione predefinita è NO. <br><br> Nota: le app non possono essere inviate all'App Store se MAMPolicyRequired è impostato su YES. Quando si imposta MAMPolicyRequired su YES, anche AutoEnrollOnLaunch deve essere impostato su YES. |

Se si sceglie questa opzione per l'app, non sarà necessario riavviare l'app dopo la registrazione.

### <a name="deregister-user-accounts"></a>Annullare la registrazione degli account utente

Prima della disconnessione di un utente da un'app, questa deve annullare la registrazione dell'utente dall'SDK. In questo modo:

1. Non si verificheranno nuovi tentativi di registrazione per l'account utente.

2. I criteri di protezione delle app verranno rimossi.

3. Se l'app avvia una cancellazione selettiva (facoltativa), tutti i dati aziendali vengono eliminati.

Prima della disconnessione dell'utente, l'app deve chiamare il metodo seguente sull'istanza `IntuneMAMEnrollmentManager`:

```objc
/*
 *  This method will remove the provided account from the list of
 *  registered accounts.  Once removed, if the account has enrolled
 *  the application, the account will be un-enrolled.
 *  @note In the case where an un-enroll is required, this method will block
 *  until the Intune APP AAD token is acquired, then return.  This method must be called before  
 *  the user is removed from the application (so that required AAD tokens are not purged
 *  before this method is called).
 *  @param identity The UPN of the account to be removed.
 *  @param doWipe   If YES, a selective wipe if the account is un-enrolled
 */
(void)deRegisterAndUnenrollAccount:(NSString *)identity withWipe:(BOOL)doWipe;
```

Questo metodo deve essere chiamato prima che i token di Azure AD dell'account utente vengano eliminati. L'SDK richiede che i token AAD dell'account utente inviino richieste specifiche al servizio MAM di Intune per conto dell'utente.

Se l'app eliminerà i dati aziendali dell'utente in modo autonomo, il contrassegno `doWipe` può essere impostato su false. In caso contrario, l'SDK può avviare automaticamente una cancellazione selettiva. Ciò comporta una chiamata al delegato per la cancellazione selettiva dell'app.

Esempio:

```objc
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES];
```

## <a name="status-result-and-debug-notifications"></a>Notifiche di stato, risultato e debug

L'app può ricevere notifiche di stato, risultato e debug sulle richieste seguenti al servizio MAM di Intune:

* Richieste di registrazione
* Richieste di aggiornamento dei criteri
* Richieste di annullamento della registrazione

Le notifiche vengono presentate tramite metodi delegato in `IntuneMAMEnrollmentDelegate.h`:

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

Questi metodi delegato restituiscono un oggetto `IntuneMAMEnrollmentStatus` che contiene le informazioni seguenti:

* Identità dell'account associate alla richiesta
* Codice di stato che indica il risultato della richiesta
* Stringa di errore con una descrizione del codice di stato
* Oggetto `NSError`. Questo oggetto viene definito in `IntuneMAMEnrollmentStatus.h` con gli specifici codici di stato che possono essere restituiti.

### <a name="sample-code"></a>Codice di esempio

Di seguito sono illustrate implementazioni di esempio dei metodi delegato:

```objc
- (void)enrollmentRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"enrollment result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)policyRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"policy check-in result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}

- (void)unenrollRequestWithStatus:(IntuneMAMEnrollmentStatus*)status
{
    NSLog(@"un-enroll result for identity %@ with status code %ld", status.identity, (unsigned long)status.statusCode);
    NSLog(@"Debug Message: %@", status.errorString);
}
```

## <a name="application-restart"></a>Riavvio dell'applicazione

Quando un'app riceve i criteri MAM per la prima volta, deve riavviarsi per applicare gli hook obbligatori. Per comunicare all'app che è necessario un riavvio, l'SDK prevede un metodo delegato in `IntuneMAMPolicyDelegate.h`.

```objc
 - (BOOL) restartApplication
```

Il valore restituito da questo metodo indica all'SDK se l'applicazione deve gestire il riavvio richiesto:

* Se viene restituito true, l'applicazione deve gestire il riavvio.

* Se viene restituito false, l'SDK riavvierà l'applicazione. L'SDK visualizzerà immediatamente una finestra di dialogo per indicare all'utente che è necessario riavviare l'applicazione.

## <a name="customize-your-apps-behavior-with-apis"></a>Personalizzare il comportamento dell'app mediante le API

Intune App SDK include varie API che è possibile chiamare per ottenere informazioni sui criteri APP di Intune distribuiti all'app. È possibile usare questi dati per personalizzare il comportamento dell'app. La tabella seguente contiene informazioni su alcune classi Intune essenziali che verranno usate.

Class | Descrizione
----- | -----------
IntuneMAMPolicyManager.h | La classe IntuneMAMPolicyManager espone i criteri APP di Intune distribuiti all'applicazione. In particolare, espone le API utili per l'[abilitazione di identità multiple](app-sdk-ios.md#enable-multi-identity-optional). |
IntuneMAMPolicy.h | La classe IntuneMAMPolicy espone alcune impostazioni dei criteri MAM applicati all'app. Queste impostazioni dei criteri vengono esposte per consentire la personalizzazione dell'interfaccia utente dell'app. La maggior parte delle impostazioni dei criteri vengono applicate dall'SDK e non dall'app. L'unica impostazione che deve implementare l'app è il controllo di salvataggio. Questa classe espone alcune API necessarie per implementare il controllo di salvataggio. |
IntuneMAMFileProtectionManager.h | La classe IntuneMAMFileProtectionManager espone le API che l'app può usare per proteggere in modo esplicito i file e le directory sulla base di un'identità fornita. L'identità può essere gestita da Intune o non essere gestita e l'SDK applicherà i criteri MAM appropriati. L'utilizzo di questa classe è facoltativo. |
IntuneMAMDataProtectionManager.h | La classe IntuneMAMDataProtectionManager espone le API che l'app può usare per proteggere i buffer dei dati sulla base di un'identità fornita. L'identità può essere gestita da Intune o non essere gestita e l'SDK applicherà la crittografia appropriata. |

## <a name="implement-save-as-controls"></a>Implementare i controlli di salvataggio

Intune consente agli amministratori IT di selezionare le posizioni di archiviazione in cui possono essere salvati i dati di un'app gestita. Le app possono eseguire una query in Intune App SDK per conoscere le posizioni di archiviazione consentite usando l'API `isSaveToAllowedForLocation`definita in `IntuneMAMPolicy.h`.

Prima di salvare i dati gestiti in un'archiviazione cloud o in percorsi locali, le app devono usare l'API `isSaveToAllowedForLocation` per verificare se l'amministratore IT ha consentito il salvataggio dei dati in quel percorso.

Quando si usa l’API `isSaveToAllowedForLocation`, le app devono passare l’UPN usato per la posizione di archiviazione, se disponibile.

### <a name="supported-save-locations"></a>Percorsi di salvataggio supportati

L'API `isSaveToAllowedForLocation` specifica delle costanti per verificare se l'amministratore IT ha autorizzato il salvataggio dei dati nei percorsi seguenti definiti in `IntuneMAMPolicy.h`:

* IntuneMAMSaveLocationOther
* IntuneMAMSaveLocationOneDriveForBusiness
* IntuneMAMSaveLocationSharePoint
* IntuneMAMSaveLocationLocalDrive

Le app devono usare le costanti di `isSaveToAllowedForLocation` per verificare se i dati possano essere salvati in percorsi considerati "gestiti", come ad esempio OneDrive for Business, o "personali". L'API deve essere usata anche quando l'app non riesce a determinare se un percorso è "gestito" o "personale".

I percorsi notoriamente personali sono rappresentati dalla costante `IntuneMAMSaveLocationOther`.

La costante `IntuneMAMSaveLocationLocalDrive` deve essere usata quando l'app salva i dati in qualsiasi percorso nel dispositivo locale.

## <a name="share-data-via-uiactivityviewcontroller"></a>Condividere dati tramite UIActivityViewController

A partire dalla versione 8.0.2, Intune App SDK consente di filtrare le azioni `UIActivityViewController` in modo che siano disponibili per la selezione solo percorsi di condivisione gestiti di Intune. Questo comportamento verrà controllato dai criteri di trasferimento dei dati dell'applicazione.

### <a name="copy-to-actions"></a>Azioni "Copy To" (Copia in)

Quando si condividono documenti tramite `UIActivityViewController` e `UIDocumentInteractionController`, iOS visualizza le azioni "Copy to" (Copia in) per ogni applicazione che supporta l'apertura del documento da condividere. Le applicazioni dichiarano i tipi di documenti supportati tramite l'impostazione `CFBundleDocumentTypes` in Info.plist. Questo tipo di condivisione non sarà più disponibile se i criteri proibiscono la condivisione con applicazioni non gestite. In sostituzione, l'utente dovrà aggiungere un'estensione per Azione non dell'interfaccia utente alla propria applicazione e collegarla a Intune App SDK. L'estensione per Azione è un semplice stub. L'SDK implementerà il comportamento di condivisione file. Seguire la procedura descritta di seguito:

1. Nell'applicazione deve essere stato definito almeno un elemento schemeURL in `CFBundleURLTypes` di Info.plist.

2. L'applicazione e l'estensione per Azione devono condividere almeno un gruppo di app e il gruppo di app deve essere elencato sotto la matrice `AppGroupIdentifiers` nei dizionari IntuneMAMSettings dell'app e dell'estensione.

3. Assegnare all'estensione per Azione il nome "Open in" seguito dal nome dell'applicazione. Localizzare Info.plist in base alle esigenze.

4. Fornire un'icona del modello per l'estensione, come illustrato nella [documentazione per gli sviluppatori di Apple](https://developer.apple.com/ios/human-interface-guidelines/extensions/sharing-and-actions/). In alternativa, è possibile usare lo strumento IntuneMAMConfigurator per generare queste immagini dalla directory APP dell'applicazione. A tale scopo, eseguire:

    ```bash
    IntuneMAMConfigurator -generateOpenInIcons /path/to/app.app -o /path/to/output/directory
    ```

5. Sotto IntuneMAMSettings nel file Info.plist dell'estensione aggiungere un'impostazione booleana denominata `OpenInActionExtension` con il valore YES.

6. Configurare `NSExtensionActivationRule` per il supporto di un singolo file e di tutti i tipi definiti in `CFBundleDocumentTypes` dell'applicazione con il prefisso `com.microsoft.intune.mam`. Se ad esempio l'applicazione supporta public.text e public.image, la regola di attivazione sarà:

    ```objc
    SUBQUERY (
        extensionItems,
        $extensionItem,
        SUBQUERY (
            $extensionItem.attachments,
            $attachment,
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.text” ||
            ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image”).@count == 1
    ).@count == 1
    ```

### <a name="update-existing-share-and-action-extensions"></a>Aggiornare le estensioni per Condivisione e Azione esistenti

Se l'app contiene già le estensioni per Condivisione o Azione, `NSExtensionActivationRule` dovrà essere modificata per consentire i tipi di Intune. Per ogni tipo supportato dall'estensione, aggiungere un altro tipo con il prefisso `com.microsoft.intune.mam`. Se ad esempio la regola di attivazione esistente è:  

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data"
    ).@count > 0
).@count > 0
```

Dovrà essere modificata in:

```objc
SUBQUERY (
    extensionItems,
    $extensionItem,
    SUBQUERY (
        $extensionItem.attachments,
        $attachment,
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "public.data" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.url" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.plain-text" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.image" ||
        ANY $attachment.registeredTypeIdentifiers UTI-CONFORMS-TO "com.microsoft.intune.mam.public.data
    ).@count > 0
).@count > 0
```

> [!NOTE]
> Per aggiungere i tipi di Intune alla regola di attivazione, si può usare lo strumento IntuneMAMConfigurator. Se la regola di attivazione esistente usa le costanti stringa predefinite (ad esempio NSExtensionActivationSupportsFileWithMaxCount, NSExtensionActivationSupportsText e così via), la sintassi del predicato può diventare piuttosto complessa. Lo strumento IntuneMAMConfigurator può essere usato anche per convertire la regola di attivazione dalle costanti stringa in una stringa di predicato durante l'aggiunta dei tipi di Intune.

### <a name="what-the-ui-should-look-like"></a>Aspetto dell'interfaccia utente

Interfaccia utente precedente:

![Condivisione dati - Interfaccia utente precedente di condivisione di iOS](./media/sharing-UI-old.png)

Nuova interfaccia utente:

![Condivisione dati - Nuova interfaccia utente di condivisione di iOS](./media/sharing-UI-new.png)

## <a name="enable-targeted-configuration-appmam-app-config-for-your-ios-applications"></a>Abilitare la configurazione di destinazione (configurazione app APP/MAM) per le applicazioni iOS

La configurazione di destinazione MAM, denominata anche configurazione app MAM, consente a un'app di ricevere i dati di configurazione tramite Intune SDK. Il proprietario o lo sviluppatore dell'app deve comunicare ai clienti Intune il formato e le varianti di tali dati.

Gli amministratori di Intune possono trovare e distribuire i dati di configurazione tramite il portale di Azure di Intune e l'API Graph di Intune. A partire dalla versione 7.0.1 di Intune App SDK per iOS, le applicazioni incluse nella configurazione di destinazione MAM possono ricevere dati di configurazione MAM tramite il servizio MAM. I dati di configurazione dell'applicazione vengono inviati tramite il servizio MAM direttamente all'app invece che tramite il canale MDM. Intune App SDK include una classe per l'accesso ai dati recuperati da queste console. Gli elementi seguenti sono prerequisiti:

* Per l'accesso all'interfaccia utente per la configurazione della destinazione MAM, l'app deve essere registrata nel servizio MAM di Intune. Per altre informazioni, vedere [Ricevere i criteri di protezione delle app](#receive-app-protection-policy).

* Includere `IntuneMAMAppConfigManager.h` nel file di origine dell'app.

* Chiamare `[[IntuneMAMAppConfigManager instance] appConfigForIdentity:]` per ottenere l'oggetto Configurazione applicazione.

* Chiamare il selettore appropriato per l'oggetto `IntuneMAMAppConfig`. Ad esempio se la chiave dell'applicazione è una stringa è opportuno usare `stringValueForKey` o `allStringsForKey`. Vedere `IntuneMAMAppConfig.h` per una descrizione dettagliata delle condizioni di errore e dei valori restituiti.

Per altre informazioni sulle funzionalità dell'API Graph, vedere [Informazioni di riferimento sull'API Graph](https://developer.microsoft.com/graph/docs/concepts/overview).

Per altre informazioni su come creare un criterio di configurazione app di destinazione MAM in iOS, vedere la sezione relativa alla configurazione di app di destinazione MAM in [Come usare i criteri di configurazione delle app di Microsoft Intune per iOS](app-configuration-policies-use-ios.md).

## <a name="telemetry"></a>Telemetria

Per impostazione predefinita, Intune App SDK per iOS raccoglie i dati di telemetria sui seguenti tipi di eventi:

* **Avvio dell'app**: per fornire informazioni a Microsoft Intune sull'utilizzo dell'app abilitata per MAM in base al tipo di gestione (MAM con MDM, MAM senza registrazione MDM e così via).

* **Chiamate di registrazione**: per fornire a Microsoft Intune informazioni sulla frequenza di esecuzioni riuscite e diverse altre metriche sulle prestazioni delle chiamate di registrazione avviate dal lato client.

* **Azioni di Intune**: per diagnosticare i problemi e garantire la funzionalità di Intune, vengono raccolte informazioni sulle azioni di Intune SDK.

> [!NOTE]
> Se si sceglie di non inviare i dati di telemetria di Intune App SDK a Microsoft Intune dall'applicazione per dispositivi mobili, è necessario disabilitare l'acquisizione della telemetria di Intune App SDK. Impostare la proprietà `MAMTelemetryDisabled` su YES nel dizionario IntuneMAMSettings.

## <a name="enable-multi-identity-optional"></a>Abilitare identità multiple (facoltativo)

Per impostazione predefinita, l'SDK applicherà i criteri all'app nel suo complesso. La funzionalità MAM per l'uso delle identità multiple può essere abilitata per applicare un criterio a livello delle singole identità. Ciò richiede una partecipazione dell'app più attiva rispetto ad altre funzionalità di gestione delle applicazioni mobili.

L'app deve informare l'SDK dell'app quando intende modificare l'identità attiva. L'SDK invierà anche una notifica all'app quando è necessaria una modifica di identità. Attualmente è supportata solo l'identità gestita. Dopo che l'utente registra il dispositivo o l'app, l'SDK usa questa identità e la considera l'identità primaria gestita. Gli altri utenti dell'app verranno trattati come non gestiti con impostazioni di criteri limitate.

Si noti che un'identità viene semplicemente definita come stringa. Le identità non fanno distinzione tra maiuscole e minuscole. Le richieste di identità all'SDK potrebbero non restituire la stessa distinzione usata originariamente durante l'impostazione dell'identità.

### <a name="identity-overview"></a>Panoramica dell'identità

Un'identità è costituita semplicemente dal nome utente di un account (ad esempio, user@contoso.com). Gli sviluppatori possono impostare l'identità dell'app sui livelli seguenti:

* **Identità del processo**: imposta l'identità a livello di processo e viene usata principalmente per applicazioni a identità singola. Questa identità influisce su attività, file e interfaccia utente.

* **Identità dell'interfaccia utente**: determina quali criteri vengono applicati alle attività dell'interfaccia utente nel thread principale, ad esempio taglia/copia/incolla, PIN, autenticazione e condivisione dati. L'identità dell'interfaccia utente non influisce sulle attività di file come crittografia e backup.

* **Identità del thread**: influisce sui criteri applicati al thread corrente. Questa identità influisce su attività, file e interfaccia utente.

L'app deve impostare le identità in modo appropriato, indipendentemente dal fatto che l'utente sia gestito.

In qualsiasi momento, ogni thread ha un'identità effettiva per le attività dell'interfaccia utente e le attività di file. Si tratta dell'identità usata per determinare i criteri da applicare, se presenti. Se l'identità non esiste o l'utente non è gestito, non verrà applicato alcun criterio. I diagrammi seguenti mostrano come vengono determinate le identità effettive.

  ![Intune App SDK per iOS: processo di determinazione delle identità](./media/ios-thread-identities.png)

### <a name="thread-queues"></a>Code di thread

Le app inviano spesso attività sincrone e asincrone alle code del thread. L'SDK intercetta le chiamate a Grand Central Dispatch (GCD) e associa l'identità del thread corrente alle attività inviate. Al termine delle attività, l'SDK modifica temporaneamente l'identità del thread nell'identità associata alle attività, esegue le attività e quindi ripristina l'identità del thread originale.


`NSOperationQueue` si basa su GCD, di conseguenza `NSOperations` verrà eseguito sull'identità del thread nel momento in cui sono state aggiunte le attività a `NSOperationQueue`. `NSOperations` o le funzioni inviate direttamente con GCD possono anche modificare l'identità del thread corrente durante l'esecuzione. Questa identità sovrascrive l'identità ereditata dal thread di invio.

### <a name="file-owner"></a>Proprietario dei file

L'SDK tiene traccia delle identità dei proprietari dei file locali e applica i criteri di conseguenza. Un proprietario del file viene stabilito al momento della creazione del file o quando un file viene aperto in modalità di troncamento. Il proprietario viene impostato sull'identità dell'attività di file effettiva del thread che esegue l'operazione.

In alternativa, le app possono impostare l'identità del proprietario del file in modo esplicito usando `IntuneMAMFilePolicyManager`. Le app possono usare `IntuneMAMFilePolicyManager` per recuperare il proprietario del file e impostare l'identità dell'interfaccia utente prima di visualizzare il contenuto del file.

### <a name="shared-data"></a>Dati condivisi

Se l'app crea file che contengono dati di utenti gestiti e non gestiti, l'app deve crittografare i dati dell'utente gestito. È possibile crittografare i dati usando le API `protect` e `unprotect` in `IntuneMAMDataProtectionManager`.

Il metodo `protect` accetta un'identità che può corrispondere a un utente gestito o non gestito. Se l'utente è gestito, i dati verranno crittografati. Se l'utente non è gestito, verrà aggiunta un'intestazione ai dati per la codifica dell'identità, ma i dati non verranno crittografati. Il metodo `protectionInfo` può essere usato per recuperare il proprietario dei dati.

### <a name="share-extensions"></a>Condividere estensioni

Se l'app contiene un'estensione di condivisione, il proprietario dell'elemento condiviso può essere recuperato con il metodo `protectionInfoForItemProvider` in `IntuneMAMDataProtectionManager`. Se l'elemento condiviso è un file, l'SDK gestirà l'impostazione del proprietario del file. Se l'elemento condiviso è costituito da dati, l'app deve impostare il proprietario del file se questi dati vengono archiviati in un file e deve chiamare l'API `setUIPolicyIdentity` prima di visualizzare i dati nell'interfaccia utente.

### <a name="turn-on-multi-identity"></a>Abilitare identità multiple

Per impostazione predefinita, tutte le app sono considerate a identità singola. L'SDK imposta l'identità del processo per l'utente registrato. Per abilitare il supporto per le identità multiple, un'impostazione booleana denominata `MultiIdentity` e con un valore YES al dizionario IntuneMAMSettings nel file Info.plist delle app.

> [!NOTE]
> Quando vengono abilitate le identità multiple, l'identità del processo, l'identità dell'interfaccia utente e le identità del thread vengono impostate su nil. L'app deve impostare correttamente questi elementi.

### <a name="switch-identities"></a>Cambio di identità

* **Cambio di identità avviato dall'app**:

    All'avvio, si considera che le app con identità multiple sono in esecuzione con un account sconosciuto e non gestito. L'interfaccia utente dell'avvio condizionale non verrà eseguita e all'app non verrà applicato alcun criterio. L'app deve notificare l'SDK ogni volta che l'identità deve essere modificata. In genere, ciò si verifica ogni volta che l'app sta per visualizzare i dati di un account utente specifico,

    ad esempio, quando l'utente prova ad aprire un documento, una cassetta postale o una scheda in un notebook. L'app deve inviare una notifica all'SDK prima che venga effettivamente aperto il file, la cassetta postale o la scheda. Questa operazione viene eseguita tramite l'API `setUIPolicyIdentity` in `IntuneMAMPolicyManager`. Questa API deve essere chiamata indipendentemente dal fatto che l'utente sia gestito. Se l'utente è gestito, l'SDK eseguirà le verifiche di avvio condizionale, ad esempio rilevamento jailbreak, PIN e autenticazione.

    Il risultato del cambio d'identità viene restituito all'app in modo sincrono tramite un gestore di completamento. L'app deve rimandare l'apertura del documento, della cassetta postale o della scheda finché non viene restituito un codice risultato di esito positivo. Se il cambio di identità non riesce, l'app deve annullare l'attività.

* **Cambio di identità avviato dall'SDK**:

    In alcuni casi l'SDK deve richiedere all'app di passare a un'identità specifica. Le app con identità multiple devono implementare il metodo `identitySwitchRequired` in `IntuneMAMPolicyDelegate` per gestire tale richiesta.

    Quando viene chiamato questo metodo, se l'app riesce a gestire la richiesta per passare all'identità specificata, deve passare `IntuneMAMAddIdentityResultSuccess` al gestore di completamento. Se l'app non riesce a gestire il cambio di identità, deve passare `IntuneMAMAddIdentityResultFailed` al gestore di completamento.

    L'app non deve chiamare `setUIPolicyIdentity` in risposta a questa chiamata. Se l'SDK richiede all'app di passare a un account utente non gestito, la stringa vuota verrà passata alla chiamata `identitySwitchRequired`.

* **Cancellazione selettiva**:

    Quando all'app viene applicata la cancellazione selettiva, l'SDK chiama il metodo `wipeDataForAccount` in `IntuneMAMPolicyDelegate`. L'app deve rimuovere l'account dell'utente specificato ed eventuali dati associati. L'SDK può rimuovere tutti i file dell'utente e può eseguire questa operazione se l'app restituisce FALSE dalla chiamata a `wipeDataForAccount`.

    Questo metodo viene chiamato da un thread in background. L'app non deve restituire un valore finché non vengono rimossi tutti i dati dell'utente, ad eccezione dei file, se l'applicazione restituisce FALSE.

## <a name="ios-best-practices"></a>Procedure consigliate per iOS

Ecco alcune procedure consigliate per lo sviluppo per iOS:

* Il file system iOS fa distinzione tra maiuscole e minuscole. Verificare che l'uso di minuscole e maiuscole sia corretto per i nomi di file come `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

* Se Xcode non trova `libIntuneMAM.a`, è possibile correggere il problema aggiungendo il percorso di questa libreria nei percorsi di ricerca del linker.

## <a name="faqs"></a>Domande frequenti

### <a name="are-all-of-the-apis-addressable-through-native-swift-or-the-objective-c-and-swift-interoperability"></a>Tutte le API sono indirizzabili tramite Swift nativo o l'interoperabilità tra Objective-C e Swift?

Le API di Intune App SDK sono solo in Objective-C e non supportano Swift **nativo**. L'interoperabilità di Swift con Objective-C è necessaria.

### <a name="do-all-users-of-my-application-need-to-be-registered-with-the-app-we-service"></a>Tutti gli utenti dell'applicazione devono essere registrati con il servizio APP-WE?

No. Solo gli account aziendali o dell'istituto di istruzione devono essere registrati con Intune App SDK. Le app devono determinare se un account viene usato in un contesto aziendale o dell'istituto di istruzione.

### <a name="what-about-users-that-have-already-signed-in-to-the-application-do-they-need-to-be-enrolled"></a>Gli utenti che hanno già eseguito l'accesso all'applicazione devono essere registrati?

L'applicazione deve registrare gli utenti dopo che sono stati autenticati correttamente. L'applicazione deve anche registrare tutti gli account esistenti presenti prima che l'applicazione includesse la funzionalità MAM senza MDM.

A tale scopo, l'applicazione userà il metodo `registeredAccounts:`. Questo metodo restituisce NSDictionary che contiene tutti gli account registrati nel servizio MAM di Intune. Se eventuali account esistenti nell'applicazione non sono presenti nell'elenco, l'applicazione deve registrarli con `registerAndEnrollAccount:`.

### <a name="how-often-does-the-sdk-retry-enrollments"></a>Con quale frequenza l'SDK ritenta l'esecuzione delle registrazioni?

L'SDK ritenterà automaticamente tutte le registrazioni non riuscite in precedenza in un intervallo di 24 ore. L'SDK esegue questa operazione per verificare che l'utente registri e riceva correttamente i criteri se l'organizzazione ha abilitato MAM dopo l'accesso dell'utente all'applicazione.

L'SDK interrompe ulteriori tentativi quando rileva che un utente ha registrato correttamente l'applicazione. Questo perché solo un utente può registrare un'applicazione in un determinato momento. Se viene annullata la registrazione di un utente, i nuovi tentativi inizieranno nuovamente nello stesso intervallo di 24 ore.

### <a name="why-does-the-user-need-to-be-deregistered"></a>Perché è necessario annullare la registrazione dell'utente?

L'SDK eseguirà queste azioni in background periodicamente:

* Se l'applicazione non è ancora registrata, l'SDK tenterà di registrare tutti gli account registrati ogni 24 ore.
* Se l'applicazione è registrata, l'SDK controllerà la presenza di aggiornamenti dei criteri di gestione delle applicazioni mobili ogni 8 ore.

Annullando la registrazione di un utente, viene inviata una notifica all'SDK che indica che l'utente non userà più l'applicazione, quindi l'SDK può arrestare gli eventi periodici per l'account utente. Se necessario, viene anche attivata una procedura di annullamento della registrazione e di cancellazione selettiva.

### <a name="should-i-set-the-dowipe-flag-to-true-in-the-deregister-method"></a>È necessario impostare il contrassegno doWipe su true nel metodo deregister?

Questo metodo deve essere chiamato prima che l'utente venga disconnesso dall'applicazione.  Se i dati dell'utente vengono eliminati dall'applicazione durante la disconnessione, è possibile impostare `doWipe` su false. Tuttavia, se l'applicazione non rimuove i dati dell'utente, `doWipe` deve essere impostato su true in modo che l'SDK possa eliminare i dati.

### <a name="are-there-any-other-ways-that-an-application-can-be-un-enrolled"></a>Sono disponibili altre modalità di annullamento della registrazione dell'applicazione?

Sì. L'amministratore IT può inviare un comando di cancellazione selettiva all'applicazione. Il comando annulla la registrazione dell'utente e cancella selettivamente i dati dell'utente. L'SDK gestisce questo scenario automaticamente e invia una notifica usando un metodo delegato di annullamento della registrazione.

### <a name="is-there-a-sample-app-that-demonstrates-how-to-integrate-the-sdk"></a>È disponibile un'app di esempio che illustra come integrare l'SDK?

Sì. È appena stata resa disponibile una versione rinnovata dell'app di esempio open source [Wagr for iOS](https://github.com/Microsoft/Wagr-Sample-Intune-iOS-App). Wagr ora supporta i criteri di protezione dell'app mediante Intune App SDK.

### <a name="how-can-i-troubleshoot-my-app"></a>Come è possibile risolvere I problemi dell'app?

Intune SDK per iOS 9.0.3 + supporta la possibilità di aggiungere una console di diagnostica nell'app per dispositivi mobili per il test dei criteri e la registrazione degli errori. `IntuneMAMDiagnosticConsole.h`definisce l' `IntuneMAMDiagnosticConsole` interfaccia della classe, che gli sviluppatori possono usare per visualizzare la console di diagnostica di Intune. Ciò consente agli utenti finali o agli sviluppatori durante i test di raccogliere e condividere i log di Intune per facilitare la diagnosi di eventuali problemi. Questa API è facoltativa per gli integratori.

## <a name="submit-your-app-to-the-app-store"></a>Inviare l'app all'App Store

Sia la libreria statica che le build del framework di Intune App SDK sono file binari universali. Ciò significa che hanno un codice per tutte le architetture del dispositivo e del simulatore. Apple rifiuterà le app inviate all'App Store se contengono codice del simulatore. Durante la compilazione con la libreria statica per le build del dispositivo, il linker rimuove automaticamente il codice del simulatore. Seguire la procedura seguente per rimuovere tutto il codice simulatore prima di caricare l'app in App Store.

1. Assicurarsi che `IntuneMAM.framework` sia presente nel desktop.

2. Eseguire questi comandi:

    ```bash
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```

    ```bash
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM
    ```

    Il primo comando rimuove le architetture del simulatore dal file DYLIB del framework. Il secondo comando copia il file DYLIB del dispositivo nella directory del framework.
