---
# required metadata

title: Manuale dello sviluppatore di Microsoft Intune App SDK per iOS | Microsoft Intune
description:
keywords:
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 8e280d23-2a25-4a84-9bcb-210b30c63c0b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Guida a Microsoft Intune App SDK per sviluppatori iOS

> [!NOTE] può essere utile leggere prima la [guida introduttiva a Intune App SDK](intune-app-sdk-get-started.md), che spiega come preparare l'integrazione in ogni piattaforma supportata.* 

Microsoft Intune App SDK per iOS consente di integrare Gestione delle app mobili (MAM, Mobile App Management) di Intune nell'app iOS. Un'applicazione abilitata per MAM si integra con Intune App SDK e consente agli amministratori IT di distribuire criteri all'app per dispositivi mobili quando l'app è attivamente gestita.

# Contenuto dell'SDK

Intune App SDK per iOS include una libreria statica, file di risorse, intestazioni API, un file con estensione plist di impostazioni di debug e uno strumento di configurazione. Le app per dispositivi mobili possono includere semplicemente i file di risorse e un collegamento statico alle librerie per l'applicazione della maggior parte dei criteri. Le funzionalità MAM di Intune avanzate vengono applicate tramite API.
Questa guida illustra l'uso degli elementi seguenti quando viene implementata l'integrazione di Intune App SDK per iOS:

* **`libIntuneMAM.a`**: libreria di Intune App SDK. Collegare la libreria al progetto per abilitare l'app per dispositivi mobili per MAM. Le istruzioni sono disponibili nella sezione "Creazione dell'app con Intune App SDK" in questo argomento.

* **`IntuneMAMResources.Bundle`**: bundle di risorse contenente le risorse usate dall'SDK. 

* **Intestazioni**: espongono le API di Intune App SDK. Se si usa un'API, è necessario includere il file di intestazione contenente l'API. 

# Funzionamento di Intune App SDK

L'obiettivo di Intune App SDK per iOS è quello di aggiungere funzionalità di gestione per le applicazioni iOS con modifiche minime al codice. Riducendo la quantità di modifiche al codice, si accelerano i tempi di immissione sul mercato, aumentando nel contempo la coerenza e la stabilità dell'applicazione per dispositivi mobili. 

L'applicazione deve essere collegata alla libreria statica e includere il bundle di risorse. Il file MAMDebugSettings.plist è facoltativo e può essere incluso nel pacchetto per simulare i criteri MAM applicati all'applicazione senza che sia necessario distribuire l'applicazione con Microsoft Intune. Nelle build di debug, inoltre, i criteri nel file MAMDebugSettings.plist possono essere applicati trasferendo il file MAMDebugSettings.plist alla directory dei documenti dell'applicazione tramite la condivisione di file in iTunes.

# Creazione dell'app con Intune App SDK 

Per abilitare Intune App SDK, eseguire i passaggi seguenti:

1. Creare un collegamento alla libreria `libIntuneMAM.a` nel modo seguente:

    Trascinare la libreria libIntuneMAM.a e rilasciarla nell'elenco "Linked Frameworks and Libraries" della destinazione del progetto.  

    ![Intune App SDK per iOS - Elenco "Linked Frameworks and Libraries"](../media/intune-app-sdk-ios-linked-frameworks-and-libraries.png)
 
    **Nota**: per il rilascio nell'App Store, usare la versione di libIntuneMAM.a creata per il rilascio e non la versione di debug. La versione per il rilascio si trova nella cartella "release". La versione di debug offre output dettagliato utile per i problemi di debug con Intune App SDK.

2. Aggiungere i framework iOS seguenti al progetto (se non presenti).
    * `MessageUI.framework`
    * `Security.framework`
    * `MobileCoreServices.framework`
    * `SystemConfiguration.framework`
    * `libsqlite3.dylib`
    * `libc++.dylib`
    * `ImageIO.framework`
    * `LocalAuthentication.Framework`
    * `AudioToolbox.framework`<br>

    **Nota**: se l'applicazione è destinata a iOS7, impostare l'attributo "Status" di `LocalAuthentication.Framework` su "Optional". 

    Se l'attributo "Status" non è impostato, l'applicazione non verrà avviata in iOS7.

    **Nota**: con Xcode 7 le estensioni `.dylib` vengono sostituite da `.tbd`.

3. Aggiungere il bundle di risorse `IntuneMAMResources.bundle` al progetto trascinandolo in "Copy Bundle Resources" nella scheda "Build Phases". 

    ![Intune App SDK per iOS - Opzione "Copy Bundle Resources"](../media/intune-app-sdk-ios-copy-bundle-resources.png)

4. Aggiungere `-force_load {PATH_TO_LIB}/libIntuneMAM.a` in una delle posizioni seguenti, sostituendo `{PATH_TO_LIB}` con il percorso di Intune App SDK:
    * Impostazione di configurazione della build OTHER_LDFLAGS del progetto 
    * Opzione "Other Linker Flags" nell'interfaccia utente<br>

    **Nota**: per trovare il valore di `PATH_TO_LIB`, selezionare il file `libIntuneMAM.a` e scegliere "Get Info" dal menu "File". Copiare e incollare le informazioni indicate in "Where" (il percorso) dalla sezione "General" della finestra "Info".

5. Se l'app per dispositivi mobili definisce un file NIB o uno storyboard principale in `info.plist`, rimuovere i relativi campi. Aggiungere i valori dello storyboard o del file NIB, rimossi in precedenza, in un nuovo dizionario denominato `IntuneMAMSettings` , con i nomi chiave seguenti, come applicabile:
    * `MainStoryboardFile`
    * `MainStoryboardFile~ipad`
    * `MainNibFile`
    * `MainNibFile~ipad `
    
    Se l'app per dispositivi mobili non definisce un file NIB o uno storyboard principale in `info.plist`, queste impostazioni **non sono necessarie**. 

    **Nota**: è possibile visualizzare il file `info.plist` in formato non elaborato (per vedere i nomi chiave) facendo clic con il pulsante destro del mouse in un punto qualsiasi nel corpo del documento e modificando il tipo di visualizzazione in "Show Raw Keys/Values".

6. Abilitare la condivisione Keychain (se non è già abilitata) facendo clic su "Capabilities" in ogni destinazione del progetto e abilitando l'opzione "Keychain Sharing". La condivisione Keychain è necessaria per procedere con il passaggio successivo.

    **Nota**: è necessario che il profilo di provisioning supporti i nuovi valori di condivisione Keychain. I gruppi di accesso a Keychain devono supportare un carattere jolly. Per verificare questo aspetto, aprire il file `.mobileprovision` in un editor di testo, cercare 'keychain-access-groups' e verificare che sia presente un carattere jolly, ad esempio: 

       <key>keychain-access-groups</key>
       <array>
       <string>YOURBUNDLESEEDID.*</string>
       </array>

7. Dopo avere abilitato la condivisione Keychain, completare i passaggi seguenti per creare un gruppo di accesso separato in cui verranno archiviati i dati di Intune App SDK. È possibile creare un gruppo di accesso a Keychain usando l'interfaccia utente o il file dei diritti:

    Uso dell'interfaccia utente per creare un gruppo di accesso a Keychain: 
    
    * Se per l'app per dispositivi mobili non sono definiti gruppi di accesso a Keychain, aggiungere l'ID bundle dell'app come primo gruppo.
    * Aggiungere il gruppo di accesso a Keychain condiviso com.microsoft.intune.mam. Questo gruppo di accesso è usato da Intune App SDK per archiviare i dati.  
    * Aggiungere il bundle di risorse `com.microsoft.adalcache` ai gruppi di accesso esistenti. 
 
    ![Intune App SDK iOS - Condivisione Keychain](../media/intune-app-sdk-ios-keychain-sharing.png)

    Se si usa il file dei diritti per creare il gruppo di accesso a Keychain invece della normale interfaccia utente, è necessario anteporre il prefisso `$(AppIdentifierPrefix)` al gruppo di accesso a Keychain nel file dei diritti. Ad esempio: `$(AppIdentifierPrefix)com.microsoft.intune.mam` e `$(AppIdentifierPrefix)com.microsoft.adalcache`.

    **Nota**: un file dei diritti è un file XML univoco dell'applicazione per dispositivi mobili, usato per specificare funzionalità e autorizzazioni speciali nell'app iOS.

8. Per le app per dispositivi mobili sviluppate per iOS 9+, è necessario includere ogni protocollo passato dall'app per dispositivi mobili a `UIApplication canOpenURL` nella matrice `LSApplicationQueriesSchemes` del file `info.plist` dell'app per dispositivi mobili. Inoltre, per ogni protocollo elencato, è necessario aggiungere un nuovo protocollo seguito da `-intunemam`. Nella matrice è anche necessario includere `http-intunemam`, `https-intunemam`e `ms-outlook-intunemam` . 

9. Se l'app definisce schemi URL nel `info.plist file`, aggiungere un altro schema, con un suffisso `-intunemam` , per ogni schema URL.

10. Se nei diritti dell'app sono definiti gruppi di app, aggiungere questi gruppi al dizionario `IntuneMAMSettings` nella chiave `AppGroupIdentitifiers` come matrice di stringhe.

11. Collegare l'applicazione per dispositivi mobili alla libreria ADAL. La libreria ADAL per Objective C è [disponibile in Github](https://github.com/AzureAD/azure-activedirectory-library-for-objc).

    **Nota**: Intune App SDK è stato testato con il codice del ramo broker ADAL del 19/06/2015. Assicurarsi di collegarsi alla versione funzionante/più recente della libreria ADAL.

12. Includere il bundle di risorse `ADALiOSBundle.bundle resource` nel progetto trascinandolo in "Copy Bundle Resources" nella scheda "Build Phases".

13. Usare l'opzione linker `-force_load PATH_TO_ADAL_LIBRARY` per il collegamento alla libreria.

    Aggiungere `-force_load {PATH_TO_LIB}/libADALiOS.a` all'impostazione di configurazione della build OTHER_LDFLAGS del progetto o in "Other Linker Flags" nell'interfaccia utente. Sostituire "PATH_TO_LIB" con il percorso dei file binari ADAL. 

Se l'applicazione per dispositivi mobili usa ADAL per l'autenticazione, vedere la sezione "Configurazione delle impostazioni di Azure Directory Authentication Library (ADAL)" in questo articolo.

## Telemetria 

Intune App SDK per iOS registra, per impostazione predefinita, i dati di telemetria sugli eventi di uso, che vengono inviati a Microsoft Intune.

Vengono registrati i dati sugli eventi di uso seguenti: 

1. Avvio dell'app, per fornire informazioni a Microsoft Intune sull'utilizzo dell'app abilitata per MAM in base al tipo di gestione.

2. Chiamata all'API EnrollApplication, per fornire a Microsoft Intune informazioni sulla frequenza di esecuzioni riuscite e diverse altre metriche sulle prestazioni della chiamata a enrollApplication dal lato client.

**Nota**: se si sceglie di non inviare i dati di telemetria di Intune App SDK a Microsoft Intune dall'applicazione per dispositivi mobili, è **necessario disabilitare** l'acquisizione della telemetria di Intune App SDK impostando la proprietà `MAMTelemetryDisabled` su "YES" in `IntuneMAMSettings`.

## Configurazione delle impostazioni di Azure Directory Authentication Library (ADAL) (facoltativo)

Intune App SDK usa ADAL per lo scenario di autenticazione e avvio condizionale. ADAL richiede in genere che le app eseguano la registrazione e ottengano un ID univoco, noto come `ClientID`, e altri identificatori, per garantire la sicurezza dei token concessi all'app. Intune App SDK usa i valori di registrazione predefiniti per contattare Azure Active Directory.  Se l'app usa ADAL per lo scenario di autenticazione, deve usare i valori di registrazione esistenti e sostituire il valore predefinito di Intune App SDK, per garantire che agli utenti finali non venga chiesto di eseguire l'autenticazione due volte (una volta da Intune App SDK e una volta dall'app). 

Se l'app usa ADAL per l'autenticazione, sono necessari i passaggi seguenti. Se l'app per dispositivi mobili non usa ADAL, non sono necessarie ulteriori operazioni. 

1. Nel file `Info.plist`del progetto, in un dizionario `IntuneMAMSettings` con il nome chiave `ADALClientId`, specificare il valore `ClientID` da usare per le chiamate ad ADAL. 

2. Nel file `Info.plist`del progetto, nel dizionario `IntuneMAMSettings` con il nome chiave `ADALRedirectUri`, specificare l'URI di reindirizzamento da usare per le chiamate ad ADAL. Potrebbe essere anche necessario specificare `ADALRedirectScheme` , a seconda del formato dell'URI di reindirizzamento dell'app.

## Creazione delle estensioni (facoltativo) 

Durante la creazione delle estensioni, seguire le stesse istruzioni usate per creare l'app per dispositivi mobili, come descritto nella sezione "Creazione dell'app con Intune App SDK" in questo argomento. Aggiornare inoltre il file info.plist di ogni estensione per aggiungere una chiave ContainingAppBundleId nel dizionario IntuneMAMSettings con il valore dell'ID bundle dell'applicazione contenitore.

## Creazione dei framework (facoltativo)

Con le più recenti modifiche apportate a Intune App SDK, non è necessario compilare l'app per dispositivi mobili con alcun flag linker specifico se l'app contiene framework applicazione incorporati. 

## File di immagine all'avvio (facoltativo)

Quando un'app abilitata per MAM è gestita attivamente da Microsoft Intune, Intune App SDK visualizza una schermata di avvio quando l'app viene avviata, per indicare all'utente che l'app è gestita. È possibile aggiungere file di immagine da visualizzare nella pagina di avvio "Gestito dall'azienda". Per le immagini, attenersi alle linee guida seguenti:

* Aggiungere i nomi file nel dizionario `IntuneMAMSettings` nel file info.plist dell'app con i nomi chiave `SplashIconFile` e `SplashIconFile~ipad`. 

* Requisiti e dimensioni delle immagini:

    * 180 x 180 per iPhone 6s Plus e iPhone 6 Plus, 120x120 per gli altri modelli di iPhone e 152x152 per iPad. 
    
    * Rimuovere l'estensione `.png` dai nomi file. 
    
    * Usare l'opzione linker `@2x` per le versioni in scala 2x e il suffisso `@3x` per le versioni in scala 3x dei file di immagine. Se le immagini non hanno le dimensioni corrette, vengono ridimensionate per essere adattate. Se i valori di SplashIconFile non vengono specificati, Intune App SDK seleziona una delle icone dell'app (60x60 per tutti i modelli di iPhone, 76x76 per tutti i modelli di iPad).

**Nota**: questa schermata viene visualizzata all'avvio, ma l'utente può eliminarla in modo permanente.

# Configurare le impostazioni di Intune App SDK

Il dizionario `IntuneMAMSettings` incluso nel file `info.plist` dell'applicazione viene usato per configurare Intune App SDK. Di seguito è riportato un elenco di tutte le impostazioni supportate. 

Alcune di queste impostazioni potrebbero essere state descritte nelle sezioni precedenti e alcune non riguardano tutte le applicazioni. 

Impostazione  | Tipo  | Definizione | Necessaria?
--|--|--|--
ADALClientId  | Stringa  | Identificatore del client AAD dell'applicazione. | Necessaria se l'applicazione usa ADAL.
ADALRedirectUri  | Stringa  | URI di reindirizzamento AAD dell'applicazione. | Necessaria se l'applicazione usa ADAL. 
AppGroupIdentifier | Matrice di stringhe  | Matrice di gruppi di app della sezione com.apple.security.application-groups dei diritti dell'app. | Necessaria se l'applicazione usa i gruppi di applicazioni.
ContainingAppBundleId  | Stringa | Specifica l'ID bundle dell'applicazione contenitore dell'estensione. | Necessaria per le estensioni iOS.
MainNibFile<br>MainNibFile~ipad  | Stringa  | Questa impostazione deve contenere il nome del file NIB principale dell'applicazione.  | Necessaria se l'applicazione definisce MainNibFile in info.plist.
MainStoryboardFile<br>MainStoryboardFile~ipad  | Stringa  | Questa impostazione deve contenere il nome del file di storyboard principale dell'applicazione. | Necessaria se l'applicazione definisce UIMainStoryboardFile in info.plist.
SplashIconFile <br>SplashIconFile~ipad  | Stringa  | Specifica il file dell'icona per la schermata iniziale di Intune. Per altre informazioni, vedere la sezione "File di immagine all'avvio" in questo argomento. | Facoltativa.
SplashDuration | Numero | Quantità minima di tempo, in secondi, per la visualizzazione della schermata iniziale di Intune all'avvio dell'applicazione. Il valore predefinito è 1,5. | Facoltativa.
ADALLogOverrideDisabled | Boolean  | Specifica se l'SDK indirizzerà tutti i log ADAL (incluse le eventuali chiamate ad ADAL dall'app) al proprio file di log. L'impostazione predefinita è NO. Impostare il valore su YES se l'app deve impostare la richiamata al log ADAL. | Facoltativa.

# Intestazioni per Intune App SDK 

Le intestazioni seguenti includono le chiamate di funzioni API necessarie per abilitare le funzionalità di Intune App SDK. 

    IntuneMAMAsyncResult.h
    IntuneMAMDataProtectionInfo.h
    IntuneMAMDataProtectionManager.h
    IntuneMAMFileProtectionInfo.h
    IntuneMAMFileProtectionManager.h
    IntuneMAMPolicyDelegate.h
    IntuneMAMLogger.h

# Debug di Intune App SDK in Xcode

Prima di testare l'app abilitata per MAM con Microsoft Intune, è possibile usare `Settings.bundle` in Xcode. In questo modo, sarà possibile impostare criteri di test senza che sia necessaria una connessione a Intune. Per abilitare lo scenario:

* Aggiungere un elemento `Settings.bundle` facendo clic con il pulsante destro del mouse sulla cartella di livello principale nel progetto. Selezionare "Add -> New File" dal menu. Selezionare il modello "Settings Bundle" in "Resources" per aggiungerlo.

* Solo nelle build di debug, copiare `MAMDebugSettings.plist` in `Settings.bundle`.

* In `Root.plist` (in Settings.bundle) aggiungere una preferenza scegliendo come tipo Child Pane e come nome file `MAMDebugSettings`.

* In "Settings -> Your-App-Name", attivare "Enable Test Policies".

* Avviare l'app (all'interno o all'esterno di Xcode). 

* In "Settings -> Your-App-Name -> Enable Test Policies" attivare un criterio, ad esempio 'PIN'.

* Avviare l'app (all'interno o all'esterno di Xcode). Verificare che il PIN funzioni come previsto.

> [!NOTE] a questo punto è possibile usare "Settings -> Your-App-Name -> Enable Test Policies" per abilitare e attivare/disattivare le impostazioni.

# Procedure consigliate per iOS

Di seguito sono illustrate alcune procedure consigliate per lo sviluppo per iOS:

Il file system iOS fa distinzione tra maiuscole e minuscole. Assicurarsi di usare la combinazione corretta di maiuscole e minuscole per i nomi file, ad esempio `libIntuneMAM.a` e `IntuneMAMResources.bundle`.

Se Xcode non trova `libIntuneMAM.a`, è possibile correggere il problema aggiungendo il percorso di questa libreria nei percorsi di ricerca del linker.



<!--HONumber=May16_HO2-->


