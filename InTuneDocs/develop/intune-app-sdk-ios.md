---
title: Manuale dello sviluppatore di Microsoft Intune App SDK per iOS | Microsoft Intune
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 09/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6b998728b3db60d10cadbcd34b5412fa76cb586f
ms.openlocfilehash: ddc47ef5846bf448cf0de1e57b527e8ec4c562cc


---

# Guida a Microsoft Intune App SDK per sviluppatori iOS

> [!NOTE]
> Può essere utile leggere prima la guida [Introduzione a Microsoft Intune App SDK](intune-app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata*. 

Microsoft Intune App SDK per iOS consente di integrare Gestione delle app mobili (MAM, Mobile App Management) di Intune nell'app iOS. Un'applicazione abilitata per la gestione delle applicazioni mobili si integra con Intune App SDK e consente agli amministratori IT di distribuire criteri all'app mobile quando l'app è attivamente gestita da Intune.


# Contenuto dell'SDK 

Intune App SDK per iOS include una libreria statica, file di risorse, intestazioni API, un file con estensione plist di impostazioni di debug e uno strumento di configurazione. Le app per dispositivi mobili possono includere semplicemente i file di risorse e un collegamento statico alle librerie per l'applicazione della maggior parte dei criteri. Le funzionalità MAM di Intune avanzate vengono applicate tramite API.

Questa guida illustra l'uso dei componenti seguenti di Intune App SDK per iOS:

* **libIntuneMAM.a**: libreria statica di Intune App SDK. Se l'app non usa le estensioni, collegare la libreria al progetto per abilitare l'app per la gestione delle applicazioni mobili di Intune. Le istruzioni sono disponibili nella sezione "Building your app with Intune App SDK" (Creazione dell'app con Intune App SDK).

* **IntuneMAM.framework**: framework di Intune App SDK. Collegare questo framework al progetto per abilitare l'app per la gestione delle applicazioni mobili di Intune. Usare il framework anziché la libreria statica se l'app usa le estensioni, in modo che il progetto non crei più copie della libreria statica.

* **IntuneMAMResources.bundle**: bundle di risorse contenente le risorse usate dall'SDK. 

* **Intestazioni**: espongono le API di Intune App SDK. Se si usa un'API, è necessario includere il file di intestazione contenente l'API. I file di intestazione seguenti includono le chiamate di funzioni API necessarie per abilitare le funzionalità di Intune App SDK. 
    
    * IntuneMAMAsyncResult.h
    * IntuneMAMDataProtectionInfo.h
    * IntuneMAMDataProtectionManager.h
    * IntuneMAMFileProtectionInfo.h
    * IntuneMAMFileProtectionManager.h
    * IntuneMAMPolicyDelegate.h
    * IntuneMAMLogger.h 


# Funzionamento di Intune App SDK

L'obiettivo di Intune App SDK per iOS è quello di aggiungere funzionalità di gestione per le applicazioni iOS con modifiche minime al codice. Minori sono le modifiche apportate al codice, minore risulta il time to market, garantendo comunque la coerenza e la stabilità dell'applicazione mobile. 

L'applicazione deve essere collegata alla libreria statica e deve includere il bundle di risorse. Il file MAMDebugSettings.plist è facoltativo e può essere incluso nel pacchetto per simulare i criteri MAM applicati all'applicazione senza che sia necessario distribuire l'applicazione con Microsoft Intune. Nelle build di debug, inoltre, i criteri nel file MAMDebugSettings.plist possono essere applicati trasferendo il file alla directory dei documenti dell'app tramite la condivisione di file in iTunes.

# Creazione dell'SDK nell'app mobile 

Per abilitare Intune App SDK, eseguire i passaggi seguenti:

1. **Opzione 1**: creare un collegamento alla libreria `libIntuneMAM.a` nel modo seguente:

    Trascinare la libreria `libIntuneMAM.a` e rilasciarla nell'elenco "Linked Frameworks and Libraries" (Framework e librerie collegati) della destinazione del progetto.
    ![Intune App SDK per iOS - Elenco "Linked Frameworks and Libraries"](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png) 

    **Nota**: se si intende rilasciare l'app nell'App Store, usare la versione di `libIntuneMAM.a` creata per il rilascio e non la versione di debug. La versione per il rilascio si trova nella cartella "release". La versione di debug offre output dettagliato utile per la risoluzione di problemi con Intune App SDK.
    
    **Opzione 2**: collegare `IntuneMAM.framework` al progetto. Trascinare la libreria `IntuneMAM.framework` e rilasciarla nell'elenco "Linked Frameworks and Libraries" (Framework e librerie collegati) della destinazione del progetto.
    
    **Nota**: se si usa il framework, prima di inviare l'app all'App Store, è necessario eliminare manualmente le architetture del simulatore dal framework universale. Vedere la sezione intitolata "Invio dell'app all'App Store".

2. Aggiungere i framework iOS seguenti al progetto:
    * MessageUI.framework
    * Security.framework
    * MobileCoreServices.framework
    * SystemConfiguration.framework
    * libsqlite3.dylib
    * libc++.dylib
    * ImageIO.framework
    * LocalAuthentication.framework
    * AudioToolbox.framework

    **Nota**: se l'applicazione è destinata a iOS 7, impostare l'attributo "Status" (Stato) di `LocalAuthentication.framework` su "Optional" (Facoltativo). Se l'attributo "Status" (Stato) non è impostato, l'applicazione non verrà avviata in iOS 7.

    **Nota**: con Xcode 7 le estensioni `.dylib` vengono sostituite da `.tbd`.

3. Aggiungere il bundle di risorse `IntuneMAMResources.bundle` al progetto trascinandolo in "Copy Bundle Resources" (Copia le risorse del bundle) nella scheda "Build Phases" (Crea fasi).
![Intune App SDK per iOS - Opzione "Copy Bundle Resources"](../media/intune-app-sdk-ios-copy-bundle-resources.png)
 
4. Aggiungere `-force_load {PATH_TO_LIB}/libIntuneMAM.a` in una delle posizioni seguenti, sostituendo `{PATH_TO_LIB}` con il percorso di Intune App SDK:
    * Impostazione di configurazione della build `OTHER_LDFLAGS` del progetto 
    * Opzione "Other Linker Flags" nell'interfaccia utente<br>

    **Nota**: per trovare il valore di `PATH_TO_LIB`, selezionare il file `libIntuneMAM.a` e scegliere "Get Info" (Ottieni informazioni) dal menu "File". Copiare e incollare le informazioni indicate in "Where" (Dove), ossia il percorso, dalla sezione "General" (Generale) della finestra "Info" (Informazioni).

5. Se l'app mobile definisce un file NIB o uno storyboard principale in Info.plist, rimuovere i relativi campi. Aggiungere i valori dello storyboard o del file NIB, rimossi in precedenza, in un nuovo dizionario denominato IntuneMAMSettings, con i nomi chiave seguenti, in base alle esigenze:
    * MainStoryboardFile
    * MainStoryboardFile~ipad
    * MainNibFile
    * MainNibFile~ipad
    
   **Nota**: se l'app mobile non definisce un file NIB o uno storyboard principale in Info.plist, queste impostazioni **non sono necessarie**. 

    **Nota**: è possibile visualizzare il file Info.plist in formato non elaborato (per vedere i nomi chiave) facendo clic con il pulsante destro del mouse in un punto qualsiasi nel corpo del documento e modificando il tipo di visualizzazione in "Show Raw Keys/Values" (Visualizza chiavi/valori non elaborati).

6. Abilitare la condivisione Keychain (se non è già abilitata) facendo clic su "Capabilities" (Funzionalità) in ogni destinazione del progetto e abilitando l'opzione "Keychain Sharing" (Condivisione Keychain). La condivisione Keychain è necessaria per procedere con il passaggio successivo.

    **Nota**: è necessario che il profilo di provisioning supporti i nuovi valori di condivisione Keychain. I gruppi di accesso a Keychain devono supportare un carattere jolly. Per verificare questo aspetto, aprire il file .mobileprovision in un editor di testo, cercare 'keychain-access-groups' e verificare che sia presente un carattere jolly, ad esempio: 
    ```
    <key>keychain-access-groups</key>
    <array>
    <string>YOURBUNDLESEEDID.*</string>
    </array>
    ```
7. Dopo avere abilitato la condivisione Keychain, completare i passaggi seguenti per creare un gruppo di accesso separato in cui verranno archiviati i dati di Intune App SDK. È possibile creare un gruppo di accesso a Keychain usando l'interfaccia utente o il file dei diritti:

    Uso dell'interfaccia utente per creare un gruppo di accesso a Keychain: 
    
    * Se per l'app per dispositivi mobili non sono definiti gruppi di accesso a Keychain, aggiungere l'ID bundle dell'app come primo gruppo.
    * Aggiungere il gruppo Keychain condiviso `com.microsoft.intune.mam`. Questo gruppo di accesso è usato da Intune App SDK per archiviare i dati.  
    * Aggiungere `com.microsoft.adalcache` ai gruppi di accesso esistenti. 

    ![Intune App SDK iOS - Condivisione Keychain](../media/intune-app-sdk-ios-keychain-sharing.png) 

    Se si usa il file dei diritti per creare il gruppo di accesso a Keychain invece della normale interfaccia utente, è necessario anteporre il prefisso `$(AppIdentifierPrefix)` al gruppo di accesso a Keychain nel file dei diritti. Ad esempio:  
    * `$(AppIdentifierPrefix)com.microsoft.intune.mam` 
    * `$(AppIdentifierPrefix)com.microsoft.adalcache`

    **Nota**: un file dei diritti è un file XML univoco dell'applicazione per dispositivi mobili, usato per specificare funzionalità e autorizzazioni speciali nell'app iOS.

8. Se l'app definisce schemi URL nel file Info.plist, aggiungere un altro schema, con un suffisso `-intunemam`, per ogni schema URL.

9. Per le app mobili sviluppate per iOS 9 o versione successiva, è necessario includere ogni protocollo passato dall'app a `UIApplication canOpenURL` nella matrice `LSApplicationQueriesSchemes` del file Info.plist dell'app. Inoltre, per ogni protocollo elencato, è necessario aggiungere un nuovo protocollo seguito da `-intunemam`. Nella matrice è anche necessario includere `http-intunemam`, `https-intunemam` e `ms-outlook-intunemam`. 

10. Se nei diritti dell'app sono definiti gruppi di app, aggiungere questi gruppi al dizionario IntuneMAMSettings nella chiave `AppGroupIdentitifiers` come matrice di stringhe.

11. Collegare l'applicazione mobile ad Azure Directory Authentication Library (ADAL). La libreria ADAL per Objective C è [disponibile in Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).

    **Nota**: Intune App SDK è stato testato con il codice del ramo broker ADAL del 19/06/2015. Assicurarsi di collegarsi alla versione funzionante/più recente della libreria ADAL.

12. Includere il bundle di risorse `ADALiOSBundle.bundle` al progetto trascinandolo in "Copy Bundle Resources" (Copia le risorse del bundle) nella scheda "Build Phases" (Crea fasi).

13. Usare l'opzione linker `-force_load PATH_TO_ADAL_LIBRARY` per il collegamento alla libreria.

    Aggiungere `-force_load {PATH_TO_LIB}/libADALiOS.a` all'impostazione di configurazione della build `OTHER_LDFLAGS` del progetto o a "Other Linker Flags" (Altri contrassegni del linker) nell'interfaccia utente. `PATH_TO_LIB` deve essere sostituito con la posizione dei file binari ADAL. 

# Configurazione delle impostazioni di Azure Directory Authentication Library (ADAL) nell'app 

Intune App SDK usa ADAL per lo scenario di autenticazione e avvio condizionale. Si basa inoltre su ADAL per registrare l'identità dell'utente al servizio di gestione delle applicazioni mobili per la gestione senza scenari di registrazione dei dispositivi. 

ADAL richiede in genere che le app eseguano la registrazione e ottengano un ID univoco, noto come ClientID, e altri identificatori per garantire la sicurezza dei token concessi all'app. Intune App SDK usa i valori di registrazione predefiniti per contattare Azure Active Directory.  

Se l'app usa ADAL per lo scenario di autenticazione, deve usare i valori di registrazione esistenti e sostituire i valori predefiniti di Intune App SDK, per garantire che agli utenti finali non venga chiesto di eseguire l'autenticazione due volte (una volta da Intune App SDK e una volta dall'app). 

##Domande frequenti su Active Directory Authentication Library

**Quali file binari di ADAL è necessario usare?** 

Intune App SDK usa attualmente il ramo broker di [ADAL su GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-objc) per supportare le app che richiedono l'accesso condizionale (app che, di conseguenza, dipendono dall'app Microsoft Authenticator). Tuttavia, l'SDK è ancora compatibile con il ramo master di ADAL. Usare il ramo più adatto all'applicazione.

**Come si esegue il collegamento ai file binari di ADAL?**

Aggiungere `-force_load {PATH_TO_LIB}/libADALiOS.a` all'impostazione di configurazione della build `OTHER_LDFLAGS` del progetto o a "Other Linker Flags" (Altri contrassegni del linker) nell'interfaccia utente. `PATH_TO_LIB` deve essere sostituito con la posizione dei file binari ADAL. Assicurarsi inoltre di copiare il bundle ADAL nell'app.  

Per altre informazioni dettagliate, vedere le istruzioni di [ADAL su Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).


**Com'è possibile condividere cache ADAL con altre app registrate con lo stesso profilo di provisioning?**

Se per l'app non sono definiti gruppi di accesso a Keychain, aggiungere l'ID bundle dell'app come primo gruppo.
Abilitare SSO ADAL aggiungendo i gruppi di accesso `com.microsoft.adalcache` e `com.microsoft.workplacejoin` ai diritti di Keycheain. 

Nel caso in cui si stia impostando in modo esplicito il gruppo Keychain della cache condivisa, assicurarsi di impostarlo su `<app_id_prefix>.com.microsoft.adalcache`. ADAL eseguirà questa operazione per conto dell'utente se quest'ultimo non esegue la sostituzione. Se si vuole specificare un gruppo Keychain personalizzato per sostituire `com.microsoft.adalcache`, specificarlo in Info.plist in "IntuneMAMSettings", usando la chiave `ADALCacheKeychainGroupOverride`.

**Com'è possibile forzare Intune App SDK affinché usi le impostazioni ADAL già in uso nell'app?** 

Se l'app usa già ADAL, vedere la sezione su IntuneMAMSettings di seguito per informazioni sulla compilazione delle impostazioni seguenti:  

* ADALClientId
* ADALRedirectUri
* ADALRedirectScheme
* ADALCacheKeychainGroupOverride

**Com'è possibile passare dalla produzione di AAD agli ambienti di test interni?**

L'impostazione `AadAuthorityURI` in `MAMPolicies.plist` può essere usata per specificare l'ambiente di AAD usato per le chiamate ADAL. L'impostazione corrente consente di usare l'ambiente di pre-produzione AAD per impostazione predefinita a meno che non venga sostituito.
    
Per testare l'ambiente di pre-produzione, è possibile usare un'opzione in fase di compilazione o di runtime. 

Per un'opzione di ambiente in fase di compilazione di AAD e degli URL del servizio di gestione delle applicazioni mobili, impostare il contrassegno booleano `UsePPE` su true in MAMEnvironment.plist. **Nota**: l'esecuzione di questa operazione tramite Info.plist non è supportata. 

Per un'opzione di ambiente in fase di runtime, impostare `com.microsoft.intune.mam.useppe` in base alle impostazioni predefinite dell'utente standard su "1" per usare l'ambiente di pre-produzione. Questa impostazione sostituisce l'impostazione `com.microsoft.intune.mam.AADAuthorityEnvironment` esistente. 

**Com'è possibile eseguire l'override dell'URL dell'autorità AAD con un URL specifico del tenant fornito in fase di runtime?** 

Impostare la proprietà `aadAuthorityUriOverride` nell'istanza IntuneMAMPolicyManager.

**Nota**: nella gestione delle applicazioni mobili senza scenario di registrazione dei dispositivi questa impostazione è utile per consentire all'SDK di riutilizzare il token di aggiornamento ADAL recuperato dall'app.

**Nota:** l'SDK continuerà a usare l'URL dell'autorità per l'aggiornamento dei criteri ed eventuali richieste di registrazione successive a meno che il valore non venga cancellato o modificato.  È quindi importante cancellare il valore quando un utente aziendale si disconnette dall'app e reimpostarlo quando un nuovo utente aziendale esegue nuovamente l'accesso.


**Cosa fare se l'app usa ADAL per l'autenticazione?**

Se l'app usa già ADAL per l'autenticazione, sono necessari i passaggi seguenti. Se l'app non si basa su ADAL, esaminare la sezione su come registrarsi al servizio Intune, se l'app non usa ADAL.

* Nel file Info.plist del progetto, in un dizionario IntuneMAMSettings con il nome chiave `ADALClientId`, specificare il valore ClientID da usare per le chiamate a ADAL. 

* Nel file Info.plist del progetto, in un dizionario IntuneMAMSettings con il nome chiave `ADALRedirectUri`, specificare l'URI di reindirizzamento da usare per le chiamate a ADAL. Può essere necessario specificare anche `ADALRedirectScheme`, a seconda del formato dell'URI di reindirizzamento dell'app.



#Registrazione dell'app con il servizio di gestione delle applicazioni mobili 

## Uso delle API
Intune App SDK offre ora la possibilità per le app per iOS di ricevere i criteri di gestione delle applicazioni mobili da Intune senza la necessità di iscriversi a gestione dei dispositivi mobili con Intune. Per supportare questa nuova funzionalità, l'SDK fornisce nuove API che consentono all'app di ricevere i criteri di gestione delle applicazioni mobili. Per usare le nuove API, completare i passaggi seguenti:

1. Usare la versione più recente di Intune App SDK che supporta la gestione delle app con o senza la registrazione del dispositivo. Se l'app ha usato una versione precedente dell'SDK senza questa funzionalità, è necessario aggiornare la libreria di gestione delle applicazioni mobili di Intune, nonché la cartella delle intestazioni con le intestazioni dell'SDK più recenti.

2. Aggiungere IntuneMAMEnrollment.h a qualsiasi file che chiamerà l'API. 

3. Per testare l'ambiente di pre-produzione, è possibile includere l'uso di un'opzione in fase di compilazione o di runtime. 

    Per un'opzione di ambiente in fase di compilazione di AAD e degli URL del servizio di gestione delle applicazioni mobili, impostare il contrassegno booleano `UsePPE` su true in MAMEnvironment.plist. **Nota**: l'esecuzione di questa operazione tramite Info.plist non è supportata. 

    Per un'opzione di ambiente in fase di runtime, impostare `com.microsoft.intune.mam.useppe` in base alle impostazioni predefinite dell'utente standard su "1" per usare l'ambiente di pre-produzione. Questa impostazione sostituisce l'impostazione `com.microsoft.intune.mam.AADAuthorityEnvironment` esistente. 


##Registrazione degli account 

Un'app può ricevere criteri di gestione delle applicazioni mobili dal servizio Intune se l'app viene registrata per conto di un account utente specificato.  L'app deve registrare qualsiasi utente che esegue l'accesso con Intune App SDK.  Al termine dell'autenticazione del nuovo account utente, l'app deve chiamare il metodo `registerAndEnrollAccount` in Headers/IntuneMAMEnrollment.h: 

```
/** 


 *  This method will add the account to the list of registered accounts. 
 *  An enrollment request will immediately be started.
 *  @param identity The UPN of the account to be registered with the SDK 
 */ 

(void)registerAndEnrollAccount:(NSString *)identity; 

```
Chiamando tale metodo, l'SDK registra l'account utente e tenta di registrare l'app per conto di questo account.  Se la registrazione ha esito negativo per qualsiasi motivo, l'SDK riproverà automaticamente la registrazione dopo 24 ore.  A scopo di debug, l'app può ricevere le notifiche, tramite un delegato, sui risultati di tutte le richieste di registrazione. Vedere i dettagli di seguito.

Dopo aver chiamato l'API, l'applicazione può continuare a funzionare normalmente.  Se la registrazione ha esito positivo, l'SDK notificherà all'utente che è necessario un riavvio dell'app.  A questo punto, l'utente può riavviare l'app.


##Annullamento della registrazione degli account 


Prima che un utente di disconnetta da un'app, questa deve annullare la registrazione dell'utente dall'SDK.  In questo modo: 

1. Non si verificheranno nuovi tentativi di registrazione per l'account utente. 
2. Se l'utente ha registrato correttamente l'applicazione, la registrazione dell'utente e dell'app verrà annullata dal servizio di gestione delle applicazioni mobili Intune e i criteri di gestione delle applicazioni mobili verranno rimossi.
3. Facoltativamente, è possibile avviare una cancellazione selettiva per verificare che qualsiasi dato aziendale o dell'istituto di istruzione venga eliminato. 

Prima che l'utente si disconnetta, l'app deve chiamare l'API seguente in Headers/IntuneMAMEnrollment.h: 

```
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

Questo metodo deve essere chiamato prima che i token AAD dell'account utente vengano eliminati.  L'SDK richiede che il token dell'app dell'utente effettui richieste specifiche al servizio di gestione delle applicazioni mobili di Intune per conto dell'utente. 

Se l'app eliminerà i dati aziendali o dell'istituto di istruzione dell'utente in modo autonomo, il contrassegno `doWipe` può essere impostato su false.  In caso contrario, l'SDK può avviare una cancellazione selettiva, che determinerà una chiamata al delegato di cancellazione selettiva dell'app. 

```
[[IntuneMAMEnrollmentManager instance] deRegisterAndUnenrollAccount:@”user@foo.com” withWipe:YES]; 
```


##Registrazione senza accesso preventivo 

Un'app che non esegue l'accesso dell'utente con Azure Active Directory può comunque ricevere criteri di gestione delle applicazioni mobili dal servizio Intune chiamando l'API seguente in modo che l'SDK gestisca l'autenticazione. Le app devono usare questo metodo se non hanno eseguito l'autenticazione dell'utente con AAD, ma devono comunque recuperare i criteri di gestione delle applicazioni mobili per proteggere i dati nell'app; ad esempio se viene usato un altro servizio di autenticazione per l'accesso all'app o se l'app non supporta l'accesso. A tale scopo, l'applicazione deve chiamare il metodo `loginAndEnrollAccount` che si trova in Headers/IntuneMAMEnrollment.h:

```
/** 
 *  Creates an enrollment request which is started immediately. 
 *  If no token can be retrieved for the identity, the user will be prompted 
 *  to enter their credentials, after which enrollment will be retried. 
 *  @param identity The UPN of the account to be logged in and enrolled. 
 */ 
 (void)loginAndEnrollAccount: (NSString *)identity; 

```
Chiamando questo metodo, l'SDK richiederà le credenziali dell'utente se non è possibile trovare alcun token esistente e quindi tenterà di registrare l'applicazione per conto dell'account. Il metodo può essere chiamato con l'identità "nil", in questo caso l'SDK eseguirà la registrazione con l'utente di gestione delle applicazioni mobili esistente nel dispositivo o chiederà all'utente un nome utente se non è presente alcun utente. 

Se la registrazione ha esito negativo, l'app deve prendere in considerazione la necessità di chiamare l'API in un secondo momento, a seconda dei dettagli dell'errore. L'app può ricevere le notifiche, tramite un delegato, sui risultati di tutte le richieste di registrazione. Vedere i dettagli. 

Dopo aver chiamato l'API, l'app può continuare a funzionare normalmente.  Se la registrazione ha esito positivo, l'SDK informerà l'utente che è richiesto il riavvio di un'app, come illustrato nella sezione precedente sulla registrazione degli account. 

##Informazioni di debug 

L'app può ricevere notifiche di debug sulle richieste seguenti al servizio di gestione delle applicazioni mobili di Intune: 

 - Richieste di registrazione 
 - Richieste di aggiornamento dei criteri 
 - Richieste di annullamento della registrazione 

Le notifiche vengono presentate tramite i metodi delegato che si trovano in Headers/IntuneMAMEnrollmentDelegate.h: 

```
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

Questi metodi delegato restituiscono un oggetto ```IntuneMAMEnrollmentStatus``` che contiene le informazioni seguenti: 

- Identità dell'account associate alla richiesta 
- Codice di stato indicante il risultato della richiesta 
- Stringa di errore con una descrizione del codice di stato 
- Oggetto NSError 

Questo oggetto viene definito in Headers/IntuneMAMEnrollmentStatus.h con i codici di stato specifici che possono essere restituiti. 

È importante notare che queste informazioni sono destinate al debug e che nessuna logica di business dell'app deve essere basata su queste notifiche.  L'idea è che l'app possa inviare queste informazioni a un servizio di telemetria a scopo di debug o di monitoraggio. 


##Codice di esempio 

Di seguito sono illustrate implementazioni di esempio dei metodi delegato: 

```
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


##Riavvio dell'app 

Quando un'app riceve i criteri di gestione delle applicazioni mobili per la prima volta, deve riavviarsi per applicare gli hook obbligatori.  Per informare l'app che è necessario un riavvio, l'SDK fornisce un metodo delegato in Headers/IntuneMAMPolicyDelegate.h. 
```
 - (BOOL) restartApplication 
```
Il valore restituito da questo metodo indicherà all'SDK se l'applicazione gestirà il riavvio richiesto.   

 - Se viene restituito true, l'applicazione si occuperà della gestione del riavvio.   
 - Se viene restituito false, l'SDK riavvierà l'applicazione.  L'SDK visualizzerà immediatamente una finestra di dialogo che informa l'utente della necessità di riavviare l'applicazione. 

#Implementazione dei controlli di salvataggio

Intune consente agli amministratori IT di selezionare il percorso di archiviazione in cui possono essere salvati i dati di un’app gestita. Le app possono eseguire una query in Intune App SDK per i percorsi di archiviazione consentiti tramite l’API **isSaveToAllowedForLocation**.

Prima di salvare i dati gestiti in un’archiviazione cloud o in percorsi in locale, le app devono usare l’API **isSaveToAllowedForLocation** per verificare se l’amministratore IT ha consentito il salvataggio di dati in quel percorso.

Quando si usa l’API **isSaveToAllowedForLocation**, le app devono passare l’UPN usato per il percorso di archiviazione, se disponibile.

##Percorsi supportati

L’API **isSaveToAllowedForLocation** specifica delle costanti per verificare i percorsi seguenti:

* IntuneMAMSaveLocationOther 
* IntuneMAMSaveLocationOneDriveForBusiness 
* IntuneMAMSaveLocationSharePoint 
* IntuneMAMSaveLocationBox 
* IntuneMAMSaveLocationDropbox 
* IntuneMAMSaveLocationGoogleDrive 
* IntuneMAMSaveLocationLocalDrive 

Le app devono usare le costanti nell’API **isSaveToAllowedForLocation** per verificare se i dati possano essere salvati in percorsi considerati "gestiti", come ad esempio OneDrive for Business, o "personali". L'API deve essere usata anche quando l'app non riesce a determinare se un percorso è "gestito" o "personale". 

Quando un percorso è noto come "personale", le app usano il valore **IntuneMAMSaveLocationOther**. 

La costante **IntuneMAMSaveLocationLocalDrive** deve essere usata quando l'app salva i dati in qualsiasi percorso nel dispositivo locale.



# Configurare le impostazioni di Intune App SDK

Il dizionario IntuneMAMSettings incluso nel file Info.plist dell'applicazione viene usato per configurare Intune App SDK. Di seguito è riportato un elenco di tutte le impostazioni supportate. 

Alcune di queste impostazioni possono essere state descritte nelle sezioni precedenti e alcune non riguardano tutte le app. 

Impostazioni  | Tipo  | Definizione | Necessaria?
--       |  --   |   --       |  --
ADALClientId  | Stringa  | Identificatore del client AAD dell'app. | Obbligatoria se l'app usa ADAL.
ADALRedirectUri  | Stringa  | URI di reindirizzamento AAD dell'app. | ADALRedirectUri o ADALRedirectScheme è obbligatoria se l'app usa ADAL. 
ADALRedirectScheme  | Stringa  | Schema di reindirizzamento AAD dell'app. Questa impostazione può essere usata al posto di ADALRedirectUri se l'URI di reindirizzamento dell'applicazione è nel formato `scheme://bundle_id`. | ADALRedirectUri o ADALRedirectScheme è obbligatoria se l'app usa ADAL. 
ADALLogOverrideDisabled | Boolean  | Specifica se l'SDK indirizzerà tutti i log ADAL (incluse le eventuali chiamate ad ADAL dall'app) al proprio file di log. L'impostazione predefinita è NO. Impostare il valore su YES se l'app deve impostare la richiamata al log ADAL. | Facoltativa.
ADALCacheKeychainGroupOverride | Stringa  | Specifica il gruppo Keychain da usare per la cache ADAL al posto di "com.microsoft.adalcache". Si noti che non contiene il prefisso app-id che verrà aggiunto alla stringa fornita in fase di runtime. | Facoltativa.
AppGroupIdentifiers | Matrice di stringhe  | Matrice di gruppi di app della sezione com.apple.security.application-groups dei diritti dell'app. | Necessaria se l'applicazione usa i gruppi di applicazioni.
ContainingAppBundleId | Stringa | Specifica l'ID bundle dell'applicazione contenitore dell'estensione. | Necessaria per le estensioni iOS.
DebugSettingsEnabled| Boolean | Se impostata su Sì, è possibile applicare i criteri di test nell'ambito del bundle delle impostazioni. Le applicazioni **non** dovrebbero essere inviate con questa impostazione abilitata. | Facoltativa.
MainNibFile<br>MainNibFile~ipad  | Stringa  | Questa impostazione deve contenere il nome del file NIB principale dell'applicazione.  | È obbligatoria se l'applicazione definisce MainNibFile in Info.plist.
MainStoryboardFile<br>MainStoryboardFile~ipad  | Stringa  | Questa impostazione deve contenere il nome del file di storyboard principale dell'applicazione. | È obbligatoria se l'applicazione definisce UIMainStoryboardFile in Info.plist.
MAMPolicyRequired| Boolean| Specifica se all'app viene impedito l'avvio se non dispone dei criteri di gestione delle applicazioni mobili di Intune. L'impostazione predefinita è "no". 
MAMPolicyWarnAbsent | Boolean| Specifica se l'app avvisa l'utente durante l'avvio se non dispone dei criteri di gestione delle applicazioni mobili di Intune. Nota: le app non possono essere inviate all'archivio se questa impostazione è definita su Sì. | Facoltativa.
MultiIdentity | Boolean| Specifica se l'app è compatibile o meno con le identità multiple. | Facoltativa.
SplashIconFile <br>SplashIconFile~ipad | Stringa  | Specifica il file dell'icona per la schermata iniziale di Intune. Per altre informazioni, vedere la sezione "File di immagine all'avvio" in questo argomento. | Facoltativa.
SplashDuration | Numero | Quantità minima di tempo, in secondi, per la visualizzazione della schermata iniziale di Intune all'avvio dell'applicazione. Il valore predefinito è 1,5. | Facoltativa.
BackgroundColor| Stringa| Specifica il colore di sfondo della schermata iniziale e di quella del PIN. Accetta una stringa RGB esadecimale nel formato '#XXXXXX', dove 'X' può variare da 0 a 9 o da A ad F. Il segno di cancelletto può essere omesso.   | Facoltativa. Il valore predefinito è grigio chiaro.
ForegroundColor| Stringa| Specifica il colore di primo piano della schermata iniziale e di quella del PIN, ad esempio il colore del testo. Accetta una stringa RGB esadecimale nel formato '#XXXXXX', dove 'X' può variare da 0 a 9 o da A ad F. Il segno di cancelletto può essere omesso.  | Facoltativa. Il valore predefinito è nero.
AccentColor | Stringa| Specifica il colore della schermata del PIN, ad esempio il colore del testo del pulsante e il colore di evidenziazione della casella.  Accetta una stringa RGB esadecimale nel formato '#XXXXXX', dove 'X' può variare da 0 a 9 o da A ad F. Il segno di cancelletto può essere omesso.| Facoltativa. Il valore predefinito è blu.
MAMTelemetryDisabled| Boolean| Specifica se l'SDK non invierà i dati di telemetria al relativo back-end.| Facoltativa.
MAMTelemetryUsePPE | Boolean | Specifica se l'SDK invierà dati al back-end dell'ambiente di pre-produzione. Usare questa impostazione durante il test delle app con i criteri di Intune in modo che i dati di telemetria di test non vengano confusi con i dati dei clienti. | Facoltativa.

## Telemetria 

Per impostazione predefinita, Intune App SDK per iOS registra i dati di telemetria sugli eventi di utilizzo, che vengono inviati a Microsoft Intune. Vengono registrati i dati sugli eventi di uso seguenti: 

1. **Avvio dell'app**: per fornire informazioni a Microsoft Intune sull'utilizzo dell'app abilitata per la gestione delle applicazioni mobili in base al tipo di gestione (gestione delle applicazioni mobili con o senza la registrazione a gestione dei dispositivi mobili e così via).

2. **Chiamata all'API EnrollApplication**: per fornire a Microsoft Intune informazioni sulla frequenza di esecuzioni riuscite e diverse altre metriche sulle prestazioni della chiamata a `enrollApplication` dal lato client.

**Nota**: se si sceglie di non inviare i dati di telemetria di Intune App SDK a Microsoft Intune dall'applicazione mobile, è necessario disabilitare l'acquisizione della telemetria di Intune App SDK impostando la proprietà `MAMTelemetryDisabled` su "Sì" nel dizionario IntuneMAMSettings.


## Creazione dell'SDK nell'estensione (facoltativo) 

Durante la creazione delle estensioni, seguire le stesse istruzioni usate per creare l'app mobile, come descritto nella sezione "Creazione dell'SDK nell'app mobile". Aggiornare inoltre il file Info.plist di ogni estensione aggiungendo una chiave `ContainingAppBundleId` nel dizionario IntuneMAMSettings con il valore dell'ID bundle dell'applicazione contenitore.

## Creazione dell'SDK nel framework (facoltativo)

Con gli aggiornamenti più recenti apportati a Intune App SDK, non è necessario compilare l'app mobile con alcun contrassegno linker specifico se l'app contiene framework applicazione incorporati. 

## File di immagine all'avvio (facoltativo)

Quando un'app abilitata per MAM è gestita attivamente da Microsoft Intune, Intune App SDK visualizza una schermata di avvio quando l'app viene avviata, per indicare all'utente che l'app è gestita. È possibile aggiungere file di immagine da visualizzare nella pagina di avvio "Gestito dall'azienda". Per le immagini, attenersi alle linee guida seguenti:

* Aggiungere i nomi file nel dizionario IntuneMAMSettings nel file Info.plist dell'app con i nomi chiave `SplashIconFile` e `SplashIconFile~ipad`. 

* Requisiti e dimensioni delle immagini:

    * 180 x 180 per iPhone 6s Plus e iPhone 6 Plus, 120x120 per gli altri modelli di iPhone e 152x152 per iPad. 
    
    * Rimuovere l'estensione png dai nomi file. 
    
    * Usare l'opzione linker `@2x` per le versioni in scala 2x e il suffisso `@3x` per le versioni in scala 3x dei file di immagine. Se le immagini non hanno le dimensioni corrette, vengono ridimensionate per essere adattate. Se i valori di SplashIconFile non vengono specificati, Intune App SDK seleziona una delle icone dell'app (60x60 per tutti i modelli di iPhone, 76x76 per tutti i modelli di iPad).

**Nota**: questa schermata viene visualizzata all'avvio, ma l'utente può eliminarla in modo permanente.



#Abilitazione di identità multiple (facoltativo)

Per impostazione predefinita, l'SDK applicherà i criteri all'app nel suo complesso. Le identità multiple sono una funzionalità della gestione delle applicazioni mobili che può essere attivata per consentire ai criteri di essere applicati a un livello specifico per ogni identità.  Ciò richiede una partecipazione dell'app più attiva rispetto ad altre funzionalità di gestione delle applicazioni mobili. 

L'app deve informare l'SDK dell'app quando intende modificare l'identità attiva. L'SDK invierà una notifica all'app quando è necessaria una modifica di identità. Attualmente è supportata solo l'identità gestita. Una volta che l'utente registra il dispositivo o l'app, l'SDK usa questa identità e la considera l'identità primaria gestita. Gli altri utenti dell'app verranno trattati come non gestiti con impostazioni di criteri limitate. 

Si noti che un'identità viene semplicemente definita come stringa. Le identità fanno distinzione tra maiuscole e minuscole e le richieste per l'SDK di un'identità non possono restituire la stessa distinzione originariamente usata durante l'impostazione dell'identità.


##Informazioni approfondite sulle identità 
  
Un'identità è semplicemente costituita dal nome utente di un account (ad esempio, utente@contoso.com). Gli sviluppatori possono impostare l'identità dell'app nei livelli seguenti: 

* **Identità del processo**: l'identità del processo imposta l'identità a livello di processo e viene usata principalmente per applicazioni a identità singola. Questa identità influisce su operazioni, file e interfaccia utente.
* **Identità dell'interfaccia utente**: determina quali criteri vengono applicati alle operazioni dell'interfaccia utente nel thread principale, ad esempio taglia/copia/incolla, PIN, autenticazione, condivisione dati e così via. L'identità dell'interfaccia utente non influisce sulle operazioni di file (crittografia, backup e così via).
* **Identità del thread**: l'identità del thread influisce sui criteri applicati al thread corrente. Influisce su tutte le operazioni, i file e l'interfaccia utente.

L'app deve impostare l'identità in modo appropriato, indipendentemente dal fatto che l'utente sia gestito.

In qualsiasi momento, ogni thread dispone di un'identità effettiva per le operazioni dell'interfaccia utente e le operazioni di file. Si tratta dell'identità usata per determinare i criteri, se presenti, da applicare. Se non vi è alcuna identità o l'utente non è gestito, non verrà applicato alcun criterio. 
 
 

##Code di thread
 
Le app inviano spesso attività sincrone e asincrone alle code del thread. L'SDK intercetta le chiamate a Grand Central Dispatch (GCD) e associa l'identità del thread corrente alle attività inviate. Quando le attività vengono eseguite, l'SDK modifica temporaneamente l'identità del thread nell'identità associata all'attività, esegue le attività e quindi ripristina l'identità del thread originale. Poiché `NSOperationQueue` si basa su GCD, `NSOperations` verrà eseguito sull'identità del thread nel momento in cui viene aggiunto a `NSOperationQueue`. `NSOperations` o le funzioni inviate tramite GCD direttamente hanno anche la possibilità di modificare l'identità del thread corrente durante l'esecuzione. Questa identità sovrascrive l'identità ereditata dal thread di invio. 

##Proprietario del file
 
L'SDK tiene traccia dell'identità del proprietario del file locale e applica i criteri di conseguenza. Il proprietario del file viene stabilito al momento della creazione del file o quando il file viene aperto in modalità di troncamento. Il proprietario viene impostato sull'identità dell'operazione del file effettiva del thread che esegue l'operazione. In alternativa, le app possono impostare l'identità del proprietario del file in modo esplicito usando `IntuneMAMFilePolicyManager`. Le app possono usare `IntuneMAMFilePolicyManager` per recuperare il proprietario del file e impostare l'identità dell'interfaccia utente prima di visualizzare il contenuto del file.


##File di dati condivisi
 
Se l'app crea file che contengono dati di utenti gestiti e non gestiti, l'app deve crittografare i dati dell'utente gestito. I dati possono essere crittografati usando le API `protect` e `unprotect` di `IntuneMAMDataProtectionManager`. Il metodo `protect` accetta un'identità che può corrispondere a un utente gestito o non gestito. Se l'utente è gestito, i dati verranno crittografati. Se l'utente non è gestito, verrà aggiunta un'intestazione ai dati crittografando l'identità, ma non i dati.  Il metodo `protectionInfo` può essere usato per recuperare il proprietario dei dati.

##Condividere estensioni
 
Se l'app contiene un'estensione di condivisione, il proprietario dell'elemento condiviso può essere recuperato tramite il metodo `protectionInfoForItemProvider` in `IntuneMAMDataProtectionManager`. Se l'elemento condiviso è un file, l'SDK gestirà l'impostazione del proprietario del file. Se l'elemento condiviso è costituito da dati, l'app deve impostare il proprietario del file se questi dati vengono salvati in un file e richiamare l'API `setUIPolicyIdentity` (come descritto di seguito) prima di visualizzare i dati nell'interfaccia utente.
 
##Abilitazione di identità multiple
 
Per impostazione predefinita, le app sono considerate a identità singola e l'SDK è imposta l'identità del processo sull'utente registrato. Per abilitare il supporto per le identità multiple, è necessario aggiungere al dizionario **IntuneMAMSettings** in Info.plist delle app un'impostazione booleana con nome `MultiIdentity` e valore "Yes". 

> [!NOTE]
> Quando vengono abilitate le identità multiple, l'identità del processo, l'identità dell'interfaccia utente e le identità del thread verranno impostate su nil. Spetta all'app impostarle in modo appropriato.

 
##Passaggio da un'identità all'altra
 
###Cambio di identità avviato dall'app
All'avvio, si considera che le app con identità multiple sono in esecuzione con un account sconosciuto e non gestito. L'interfaccia utente di avvio condizionale non verrà eseguita e all'app non verrà applicato alcun criterio. L'app deve notificare l'SDK ogni volta che l'identità deve essere modificata. In genere, ciò si verifica ogni volta che l'app sta per visualizzare i dati di un account utente specifico.

Un esempio tipico è dato dal caso in cui l'utente tenta di aprire un documento, la cassetta postale o una scheda in un notebook. L'app deve notificare l'SDK prima che il file, la cassetta postale o la scheda venga effettivamente aperta. Questa operazione viene eseguita tramite l'API `setUIPolicyIdentity` in `IntuneMAMPolicyManager`. Questa API deve essere chiamata indipendentemente dal fatto che l'utente sia gestito. Se l'utente è gestito, l'SDK eseguirà le verifiche di avvio condizionale (rilevamento jailbreak, PIN, autenticazione e così via). Il risultato del cambio d'identità viene restituito all'app in modo sincrono tramite un gestore di completamento. L'app deve rinviare l'apertura del documento della cassetta postale, della scheda e così via, fino a quando non viene restituito un codice di risultato di esito positivo. Se il cambio di identità ha esito negativo, l'app deve annullare l'operazione. 

###Cambio di identità avviato dall'SDK
In alcuni casi l'SDK deve richiedere all'app di passare a un'identità specifica. Le app con identità multiple devono implementare il metodo `identitySwitchRequired` in `IntuneMAMPolicyDelegate` per gestire la richiesta. Quando il metodo viene chiamato, se l'app è in grado di gestire la richiesta per passare all'identità specificata, deve passare `IntuneMAMAddIdentityResultSuccess` al gestore di completamento. Se l'app non è in grado di gestire l'identità di commutazione, deve passare `IntuneMAMAddIdentityResultFailed` al gestore di completamento. L'applicazione non deve chiamare `setUIPolicyIdentity` in risposta a questa chiamata. Se l'SDK richiede all'app di passare a un account utente non gestito, la stringa vuota verrà passata alla chiamata `identitySwitchRequired`. 
 
###Cancellazione selettiva
Quando all'app viene applicata la cancellazione selettiva, l'SDK chiama il metodo `wipeDataForAccount` in `IntuneMAMPolicyDelegate`. L'app deve rimuovere l'account dell'utente specificato ed eventuali dati associati. L'SDK è in grado di rimuovere tutti i file dell'utente e può eseguire questa operazione se l'app restituisce "FALSE" dalla chiamata a `wipeDataForAccount`. Si noti che questo metodo viene chiamato da un thread in background e che l'app non deve inviare alcun risultato fino a quando tutti i dati dell'utente non sono stati rimossi (ad eccezione dei file se l'app restituisce "FALSE").

# Debug di Intune App SDK in Xcode

Prima di testare manualmente l'app abilitata per la gestione delle applicazioni mobili con Microsoft Intune, è possibile usare il file **Settings.bundle** in Xcode. In questo modo, sarà possibile impostare criteri di test senza che sia necessaria una connessione a Intune. Per abilitare lo scenario:

* Aggiungere un file Settings.bundle facendo clic con il pulsante destro del mouse sulla cartella di livello principale nel progetto. Selezionare "Add -> New File" dal menu. Selezionare il modello "Settings Bundle" in "Resources" per aggiungerlo.

* Solo nelle build di debug, copiare il file MAMDebugSettings.plist in Settings.bundle.

* In Root.plist (in Settings.bundle) aggiungere una preferenza scegliendo come tipo Child Pane e come nome file MAMDebugSettings.

* In **Settings -> Your-App-Name** (Impostazioni -> Nome app), attivare "Enable Test Policies" (Abilita criteri di test).

* Avviare l'app (all'interno o all'esterno di Xcode). 

* In **Settings -> Your-App-Name -> Enable Test Policies** (Impostazioni -> Nome app -> Abilita criteri di test) attivare un criterio, ad esempio "PIN."

* Avviare l'app (all'interno o all'esterno di Xcode). Verificare che il PIN funzioni come previsto.

> [!NOTE]
> A questo punto è possibile usare **Settings -> Your-App-Name -> Enable Test Policies** (Impostazioni -> Nome app -> Abilita criteri di test) per abilitare e attivare/disattivare le impostazioni.

# Procedure consigliate per iOS

Di seguito sono illustrate alcune procedure consigliate per lo sviluppo per iOS:

Il file system iOS fa distinzione tra maiuscole e minuscole. Assicurarsi di usare la combinazione corretta di maiuscole e minuscole per i nomi file, ad esempio `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

Se Xcode non trova `libIntuneMAM.a`, è possibile correggere il problema aggiungendo il percorso di questa libreria nei percorsi di ricerca del linker.



##Domande frequenti 

 **Tutti gli utenti dell'applicazione devono essere registrati con il servizio di gestione delle applicazioni mobili?**

No.  Solo gli account aziendali o dell'istituto di istruzione devono essere registrati con Intune App SDK.  Le app devono determinare se un account viene usato in un contesto aziendale o dell'istituto di istruzione.   
 
**Gli utenti che hanno già eseguito l'accesso all'applicazione  devono essere registrati?** 

L'applicazione deve registrare gli utenti dopo l'autenticazione e deve anche registrare tutti gli account esistenti presenti prima che l'applicazione disponesse della funzionalità di gestione delle applicazioni mobili, ma non di quella di gestione dei dispositivi mobili.   


A tale scopo, l'applicazione deve usare il metodo `registeredAccounts:`.  Questo metodo restituisce NSDictionary contenente tutti gli account registrati nel servizio di gestione delle applicazioni mobili di Intune.  Se eventuali account esistenti nell'applicazione non sono presenti nell'elenco, l'applicazione deve registrare tali account tramite `registerAndEnrollAccount:`. 


 

**Con quale frequenza l'SDK ritenta l'esecuzione delle registrazioni?** 

L'SDK ritenterà automaticamente tutte le registrazioni non riuscite in precedenza in un intervallo di 24 ore.  L'SDK esegue questa operazione per verificare che, se l'organizzazione di un utente ha abilitato la gestione delle applicazioni mobili dopo che quest'ultimo ha eseguito l'accesso all'applicazione, l'utente eseguirà correttamente la registrazione e riceverà i criteri. 

L'SDK interromperà i nuovi tentativi quando rileva che un utente ha registrato correttamente l'applicazione.  Questo perché solo un utente può registrare un'applicazione in qualsiasi momento. Se viene annullata la registrazione di un utente, i nuovi tentativi inizieranno nuovamente nello stesso intervallo di 24 ore. 


 
**Perché è necessario annullare la registrazione dell'utente?** 

L'SDK eseguirà le azioni seguenti in background periodicamente:

 - Se l'applicazione non è ancora registrata, l'SDK tenterà di registrare tutti gli account registrati ogni 24 ore. 
 - Se l'applicazione è registrata, l'SDK controllerà la presenza di aggiornamenti dei criteri di gestione delle applicazioni mobili ogni 8 ore. 

Annullando la registrazione di un utente, viene inviata una notifica all'SDK relativa al fatto che l'utente non userà più l'applicazione e uno qualsiasi degli eventi periodici precedenti può essere arrestato per l'account utente.  Se necessario, viene inoltre attivata una procedura di annullamento della registrazione e di cancellazione selettiva. 

**È necessario impostare il contrassegno doWipe su true nel metodo deregister?** Questo metodo deve essere chiamato prima che l'utente venga disconnesso dall'applicazione.  Se, durante il processo di disconnessione, i dati dell'utente vengono eliminati dall'applicazione, è possibile impostare `doWipe` su false.  Tuttavia, se l'applicazione non rimuove i dati dell'utente, questo parametro deve essere impostato su true in modo che l'SDK possa eliminare manualmente i dati stessi. 

**Sono disponibili altre modalità di annullamento della registrazione dell'applicazione?** Sì, l'amministratore IT può inviare un comando di cancellazione selettiva all'applicazione, che comporterà l'annullamento della registrazione dell'utente e la cancellazione dei dati dell'utente.  L'SDK gestisce questo scenario automaticamente e invia una notifica tramite un metodo delegato di annullamento della registrazione. 

#Invio dell'app all'App Store
Sia la libreria statica che le compilazioni del framework di Intune App SDK sono file binari universali, ovvero contengono codice per tutte le architetture di dispositivo e del simulatore. Apple rifiuterà le app inviate ad App Store se contengono codice del simulatore. Durante la compilazione con la libreria statica per le build solo dispositivo, il linker rimuoverà automaticamente il codice del simulatore.

Se l'app usa la **build framework** di Intune App SDK, prima di inviare l'app all'App Store, è necessario eliminare manualmente le architetture del simulatore dal framework universale. Di seguito alcune istruzioni utili a questo scopo:

1. Assicurarsi che `IntuneMAM.framework` sia presente nel desktop.
2. Eseguire i comandi seguenti:
    
    ```
    lipo ~/Desktop/IntuneMAM.framework/IntuneMAM -remove i386 -remove x86_64 -output ~/Desktop/IntuneMAM.device_only
    ```
    Il primo comando rimuove le architetture del simulatore dal file dylib del framework.
    ```
    cp ~/Desktop/IntuneMAM.device_only ~/Desktop/IntuneMAM.framework/IntuneMAM 
    ```
    Il secondo comando copia il file dylib del dispositivo nella directory del framework.



<!--HONumber=Oct16_HO3-->


