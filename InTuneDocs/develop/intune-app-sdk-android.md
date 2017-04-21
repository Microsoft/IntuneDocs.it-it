---
title: Manuale dello sviluppatore di Microsoft Intune App SDK per Android | Documentazione Microsoft
description: "Microsoft Intune App SDK per Android permette di integrare le funzionalità di gestione delle app mobili (MAM, Mobile App Management) di Intune nell&quot;app Android."
keywords: SDK
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: 17fa23f1d04e22a2cb10452fe3a9425f7482a6de
ms.lasthandoff: 04/14/2017


---


# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guida a Microsoft Intune App SDK per sviluppatori di Android

> [!NOTE]
> Si consiglia di leggere prima [Panoramica di Intune App SDK](intune-app-sdk.md), che illustra le attuali funzionalità dell'SDK e descrive come preparare l'integrazione in ogni piattaforma supportata.

Microsoft Intune App SDK per Android permette di integrare le funzionalità di gestione delle app mobili (MAM, Mobile App Management) di Intune nell'app Android. Un'applicazione abilitata per MAM è integrata con Intune App SDK. Consente agli amministratori IT di distribuire i criteri all'app per dispositivi mobili quando Intune gestisce attivamente l'app.

## <a name="whats-in-the-sdk"></a>Contenuto dell'SDK

Intune App SDK per Android è una libreria Android standard senza dipendenze esterne. L'SDK è costituito da:  

* **Microsoft.Intune.MAM.SDK.jar**: interfacce necessarie per abilitare MAM e l'interoperabilità con l'app Portale aziendale di Intune. Le app devono specificare questo file come riferimento alla libreria Android.

* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: interfacce necessarie per abilitare MAM nelle app che usano la libreria di supporto Android v4. Le app che richiedono questo supporto devono fare riferimento al file JAR direttamente.

* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: interfacce necessarie per abilitare MAM nelle app che usano la libreria di supporto Android v7. Le app che richiedono questo supporto devono fare riferimento al file JAR direttamente.

* **Directory delle risorse**: risorse (come le stringhe) su cui è basato l'SDK.

* **Microsoft.Intune.MAM.SDK.aar**: componenti dell'SDK, ad eccezione dei file JAR Support.V4 e Support.V7. Questo file può essere usato al posto dei singoli componenti se il sistema di compilazione supporta i file AAR.

* **AndroidManifest.xml**: punti di ingresso aggiuntivi e requisiti della libreria.

* **THIRDPARTYNOTICES.TXT**: comunicazione di attribuzione che riconosce la presenza di codice OSS e/o di terze parti che verrà compilato nell'app.

## <a name="requirements"></a>Requisiti

Intune App SDK è un progetto Android compilato. Di conseguenza, è sostanzialmente non interessato dalla versione di Android usata dall'app per le versioni delle API minime o di destinazione. L'SDK supporta le API da Android 14 (Android 4.0+) ad Android 24.

Intune App SDK per Android è basato sulla presenza dell'app [Portale aziendale](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) nel dispositivo per l'abilitazione dei criteri MAM. Per l'uso di MAM senza registrazione del dispositivo, *non* è richiesta la registrazione del dispositivo con l'app Portale aziendale.


## <a name="how-the-intune-app-sdk-works"></a>Funzionamento di Intune App SDK

###<a name="entry-points"></a>Punti di ingresso

Intune App SDK richiede la modifica del codice sorgente di un'app per abilitare i criteri di gestione delle app di Intune. A questo scopo, vengono sostituite le classi base di Android con le classi base di Intune equivalenti, che hanno nomi con il prefisso `MAM`. Le classi dell'SDK si trovano tra la classe base per Android e la versione derivata dell'app di tale classe. Usando un'attività come esempio, la gerarchia di ereditarietà risultante ha un aspetto simile a questa: `Activity` > `MAMActivity` > `AppSpecificActivity`.

Ad esempio, quando `AppSpecificActivity` interagisce con il relativo padre (ad esempio, chiamando `super.onCreate()`), `MAMActivity` è la superclasse.

Le app Android tipiche hanno una modalità singola e possono accedere al sistema tramite l'oggetto [Context](https://developer.android.com/reference/android/content/Context.html). Le app con Intune App SDK incorporato, invece, hanno due modalità. Continuano ad accedere al sistema tramite l'oggetto `Context`, ma, a seconda della classe base `Activity` usata, l'oggetto `Context` viene fornito da Android oppure viene sottoposto a multiplexing avanzato tra una visualizzazione con restrizioni del sistema e l'oggetto `Context` fornito da Android.

Quando è stato eseguito l'override di un [punto di ingresso](https://developer.android.com/guide/components/fundamentals.html) Android con l'equivalente MAM, deve essere usata la versione MAM del ciclo di vita del punto di ingresso (con l'eccezione della classe `MAMApplication`).

Ad esempio, quando si deriva da `MAMActivity`, invece di sostituire `onCreate` e chiamare `super.onCreate`, la classe `Activity` deve sostituire `onMAMCreate` e chiamare `super.onMAMCreate`. Ciò consente a Intune di limitare il lancio di `Activity` (tra gli altri) in alcuni casi.


###<a name="sdk-permissions"></a>Autorizzazioni dell'SDK

Intune App SDK richiede tre [autorizzazioni di sistema Android](https://developer.android.com/guide/topics/security/permissions.html) per le app che lo integrano:

* `android.permission.GET_ACCOUNTS` (richiesta in fase di esecuzione se necessario)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

La libreria [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) (Azure Active Directory Authentication Library) richiede queste autorizzazioni per eseguire l'autenticazione negoziata. Se queste autorizzazioni non vengono concesse all'app o vengono revocate dall'utente, verranno disabilitati i flussi di autenticazione che richiedono il broker (l'app Portale aziendale).


###<a name="company-portal-app"></a>App Portale aziendale

Perché è necessaria l'app Portale aziendale? Dopo l'installazione dell'app Portale aziendale nel dispositivo e il recupero dei criteri di restrizione di un'applicazione per l'utente dal servizio Intune, i punti di ingresso dell'SDK vengono inizializzati in modo asincrono. L'inizializzazione è necessaria solo quando Android crea inizialmente il processo. Durante l'inizializzazione viene stabilita una connessione all'app Portale aziendale e vengono recuperati i criteri dall'app.  

> [!NOTE]
> Quando l'app Portale aziendale non è presente nel dispositivo, il comportamento dell'app abilitata per Intune non viene modificato e l'app si comporta come una normale app.


## <a name="how-to-integrate-with-the-intune-app-sdk"></a>Come implementare l'integrazione con Intune App SDK

Come indicato in precedenza, l'SDK richiede l'applicazione di modifiche al codice sorgente dell'app per abilitare i criteri di gestione delle app. Ecco i passaggi necessari per abilitare MAM nell'app.

### <a name="replace-classes-methods-and-activities-with-their-mam-equivalent-required"></a>Sostituire classi, metodi e attività con i rispettivi equivalenti MAM (obbligatorio)

Le classi base di Android devono essere sostituite con il rispettivo equivalente MAM. A questo scopo, trovare tutte le istanze delle classi elencate nella tabella seguente e sostituirle con l'equivalente di Intune App SDK.

| Classe base Android | Sostituzione di Intune App SDK |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent* |
| android.app.Service | MAMService |
| android.app.TabActivity | MAMTabActivity |
| android.app.TaskStackBuilder | MAMTaskStackBuilder |
| android.app.backup.BackupAgent | MAMBackupAgent |
| android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
| android.app.backup.FileBackupHelper | MAMFileBackupHelper |
| android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
| android.content.BroadcastReceiver | MAMBroadcastReceiver |
| android.content.ContentProvider | MAMContentProvider |
| android.os.Binder | MAMBinder (necessaria solo se il binder non viene generato da un'interfaccia AIDL (Android Interface Definition Language)) |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |


**Microsoft.Intune.MAM.SDK.Suppot.v4.jar**:

| Classe Android    MAM di Intune | Sostituzione di Intune App SDK |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider

**Microsoft.Intune.MAM.SDK.Suppot.v7.jar**:

|Classe Android | Sostituzione di Intune App SDK |
|--|--|
|android.support.v7.app.ActionBarActivity | MAMActionBarActivity |

>[!NOTE]
>Tenere presente che quando è stato eseguito l'override di un [punto di ingresso](https://developer.android.com/guide/components/fundamentals.html) Android con l'equivalente MAM, deve essere usata la versione MAM del ciclo di vita del punto di ingresso (con l'eccezione della classe `MAMApplication`).
>
>Ad esempio, quando si deriva da `MAMActivity`, invece di sostituire `onCreate` e chiamare `super.onCreate`, la classe `Activity` deve sostituire `onMAMCreate` e chiamare `super.onMAMCreate`. Ciò consente a Intune di limitare il lancio di `Activity` (tra gli altri) in alcuni casi.

#### <a name="pendingintent-classes-and-renamed-methods"></a>Classi PendingIntent e metodi rinominati

In seguito alla derivazione da uno dei punti di ingresso MAM, è sicuro usare l'oggetto `PackageManager` come di consueto, ad esempio per avviare classi `Context` e usare `Activity`.  

Le classi `PendingIntent` costituiscono un'eccezione a questa regola. Quando si chiamano queste classi, è necessario modificare il nome di classe. Ad esempio, invece di `PendingIntent.get*`, è necessario usare il metodo `MAMPendingIntent.get*`. Successivamente, è possibile usare la classe `PendingIntent` risultante come di consueto.

In alcuni casi, un metodo disponibile nella classe Android è stato contrassegnato come finale nella classe sostitutiva MAM. In questo caso, la classe sostitutiva MAM fornisce un metodo denominato in modo analogo (in genere con suffisso `MAM`), che deve essere sostituito al suo posto. Ad esempio, invece di sostituire `ContentProvider.query`, è necessario sostituire `MAMContentProvider.queryMAM`. Il compilatore Java deve applicare le restrizioni finali per impedire la sostituzione accidentale del metodo originale invece dell'equivalente MAM.

###<a name="enable-features-that-require-app-participation"></a>Abilitare le funzionalità che richiedono la partecipazione dell'app

L'SDK non può implementare alcuni criteri autonomamente. L'app può controllare il suo comportamento per queste funzionalità usando varie API disponibili nell'interfaccia di `AppPolicy` seguente.

```
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * <strong>This function is now deprecated. Please use {@link #getIsSaveToLocationAllowed(SaveLocation, String)} instead</strong>
 * @return True if the app is allowed to save to personal data stores; false otherwise.
 */
@Deprecated
boolean getIsSaveToPersonalAllowed();

/**
 * Check if policy prohibits saving to a content provider location.
 *
 * @param location
 *            a content URI to check
 * @return True if location is not a content URI or if policy does not prohibit saving to the content location.
 */
boolean getIsSaveToLocationAllowed(Uri location);

/**
 * Determines if the SaveLocation passed in can be saved to by the username associated with the cloud service.
 *
 * @param service
 *           see {@link SaveLocation}.
 * @param username
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Whether the SDK PIN prompt is enabled for the app.
 *
 * @return True if the PIN is enabled. False otherwise.
 */
boolean getIsPinRequired();

/**
 * Whether the Intune Managed Browser is required to open web links.
 * @return True if the Managed Browser is required, false otherwise
 */
boolean getIsManagedBrowserRequired();

/**
 * Check if policy allows Contact sync to local contact list.
 *
 * @return True if Contact sync is allowed to save to local contact list; false otherwise.
 */
boolean getIsContactSyncAllowed();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();


}

```

### <a name="enable-it-control-over-app-saving-behavior"></a>Abilitare il controllo dell'amministratore IT sul comportamento di salvataggio dell'app

Molte app implementano funzionalità che permettono all'utente di salvare file in locale o in un altro servizio di archiviazione cloud. Intune App SDK aiuta gli amministratori IT a prevenire la perdita dei dati applicando restrizioni di criteri nel modo che ritengono appropriato all'interno dell'organizzazione.  Uno dei criteri che gli amministratori IT possono controllare determina se l'utente possa o meno eseguire salvataggi in un archivio dati non gestito "personale". È incluso il salvataggio in un percorso locale, una scheda SD o un servizio di backup di terze parti.

La partecipazione dell'app è necessaria per l'abilitazione della funzionalità. Se l'app consente il salvataggio in percorsi personali o nel cloud direttamente dall'app stessa, è necessario implementare questa funzionalità per garantire che l'amministratore IT possa controllare se il salvataggio in una determinata posizione sia consentito.   

Per determinare se i criteri vengono applicati, l'app può effettuare la chiamata seguente. Questa chiamata consente all'app di stabilire se i criteri correnti dell'amministratore di Intune consentono il salvataggio in un archivio personale. L'app può quindi applicare i criteri, perché può determinare che è disponibile un archivio dati personale per l'utente attraverso se stessa.

```
MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();
```

> [!NOTE]
> `MAMComponents.get(AppPolicy.class)` restituisce sempre criteri di app diversi da Null, anche se l'app o il dispositivo non è gestito con criteri di Intune.

### <a name="let-the-app-detect-if-a-pin-policy-is-required"></a>Permettere all'app di rilevare se è necessario un criterio PIN

Per alcune restrizioni per le app di Intune può essere necessario che l'app disabiliti alcune delle proprie funzionalità in modo da non duplicare funzionalità in Intune App SDK. Ad esempio, se l'app è dotata di un'esperienza utente specifica per l'uso del PIN, è consigliabile disabilitarla se l'SDK è configurato in modo da richiedere all'utente di immettere un PIN.

Per determinare se sono configurati criteri relativi ai PIN di Intune per richiedere l'immissione di un PIN all'avvio di un'app, l'app può effettuare questa chiamata:

```
MAMComponents.get(AppPolicy.class).getIsPinRequired();
```

### <a name="register-for-notifications-from-the-sdk"></a>Eseguire la registrazione per le notifiche dall'SDK  

Intune App SDK permette all'app di controllare il comportamento di determinati criteri, come una cancellazione selettiva, quando l'amministratore IT li distribuisce. Quando un amministratore IT distribuisce criteri di questo tipo, il servizio Intune invia una notifica all'SDK.

L'app deve effettuare la registrazione per le notifiche dall'SDK creando una classe `MAMNotificationReceiver` e registrandola con `MAMNotificationReceiverRegistry`. Ciò avviene specificando il ricevente e il tipo di notifica desiderato in `App.onCreate`, come illustra questo esempio:

```
@Override
public void onCreate() {
    super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class)
.registerReceiver(
                new ToastNotificationReceiver(),
MAMNotificationType.WIPE_USER_DATA);
    }
```

`MAMNotificationReceiver` riceve semplicemente le notifiche dal servizio Intune. L'SDK gestisce alcune notifiche direttamente. Altre notifiche richiedono la partecipazione dell'app.

Un'app *deve* restituire true o false da una notifica. L'app deve sempre restituire true, a meno che un'azione che l'app prova a eseguire come risultato della notifica non riesca. Questo errore può essere segnalato al servizio Intune. Uno dei casi in cui la segnalazione è appropriata è quando un'app non riesce a cancellare i dati utente dopo che l'amministratore IT avvia una cancellazione.

Il blocco in `MAMNotificationReceiver.onReceive` è sicuro, in quanto il callback non viene eseguito nel thread dell'interfaccia utente.

L'interfaccia di `MAMNotificationReceiver` seguente è definita nell'SDK:

```
/**
 * The SDK is signaling that a WG event has occurred.
 *
 */
public interface MAMNotificationReceiver {

    /**
     * A notification was received.
     *
     * @param notification
     *            The notification that was received.
     * @return The receiver should return true if it handled the
     *   notification without error (or if it decided to ignore the
     *   notification). If the receiver tried to take some action in
     *   response to the notification but failed to complete that
     *   action it should return false.
     */
    boolean onReceive(MAMNotification notification);
}

```

###<a name="types-of-notifications"></a>Tipi di notifiche

All'app vengono inviate le notifiche seguenti. Alcune di esse richiedono la partecipazione dell'app.

* **`WIPE_USER_DATA`**: questa notifica viene inviata in una classe `MAMUserNotification`. Alla ricezione della notifica, è previsto che l'app elimini tutti i dati associati all'identità "aziendale" passata con la classe `MAMUserNotification`. Questa notifica viene attualmente inviata durante l'annullamento della registrazione del servizio Intune. Il nome primario dell'utente viene in genere specificato durante il processo di registrazione. Se si effettua la registrazione per questa notifica, l'app deve garantire che tutti i dati utente siano stati eliminati. Se la registrazione non viene effettuata, l'app eseguirà il comportamento di cancellazione selettiva predefinito.

* **`WIPE_USER_AUXILIARY_DATA`**: le app possono effettuare la registrazione per questa notifica se vogliono che Intune App SDK usi il comportamento predefinito di cancellazione selettiva, ma vogliono comunque rimuovere alcuni dati ausiliari quando viene eseguita la cancellazione.  

* **`REFRESH_POLICY`**: questa notifica viene inviata in `MAMUserNotification`. Alla ricezione di questa notifica, qualsiasi criterio di Intune memorizzato nella cache deve essere invalidato e aggiornato. L'SDK gestisce in genere questa attività, ma l'app deve gestire questa attività se il criterio viene usato in modo permanente.



### <a name="protection-of-backup-data"></a>Protezione dei dati di backup

A partire da Android Marshmallow (API 23), Android offre due modi in cui un'app può eseguire il backup dei dati. Ogni opzione è disponibile e richiede procedure diverse per garantire l'implementazione corretta della protezione dati di Intune. Per altre informazioni sui metodi di backup, vedere la [guida alle API di Android](http://developer.android.com/guide/topics/data/backup.html).

#### <a name="automatic-backup-for-apps"></a>Backup automatico per le app

Android ha iniziato a offrire [backup completi automatici](https://developer.android.com/guide/topics/data/autobackup.html) per le app nei dispositivi Android Marshmallow, indipendentemente dall'API di destinazione dell'app. Se si imposta in modo esplicito `android:allowBackup` su false nel file AndroidManifest.xml, Android non accoderà mai l'app per i backup e i dati "aziendali" rimarranno all'interno dell'app. In questo caso non è necessaria alcuna azione ulteriore.

Per impostazione predefinita, l'attributo `android:allowBackup` viene impostato su true, anche se `android:allowBackup` non è specificato nel file manifesto. Questo significa che viene eseguito automaticamente il backup di tutti i dati dell'app nell'account Google Drive dell'utente, un comportamento predefinito che comporta il *rischio di perdite di dati*. L'SDK richiede l'applicazione delle modifiche seguenti per garantire una corretta protezione dei dati. È importante seguire queste linee guida per proteggere i dati dei clienti in modo appropriato, se si vuole eseguire l'app in dispositivi Android Marshmallow.  

Se non è stato scritto un agente di backup per eseguire il backup dell'app usando `MAMBackupAgent` o `MAMBackupAgentHelper`, sarà necessario prendere in considerazione e controllare la modalità di caricamento dei dati dell'app usata dal backup automatico. Intune permette di usare tutte le [funzionalità di backup automatico](https://developer.android.com/guide/topics/data/autobackup.html) disponibili da Android, inclusa la possibilità di definire regole personalizzate in XML, ma è necessario seguire la procedura seguente per proteggere i dati:

1. Usare il `MAMBackupAgent` predefinito per consentire backup completi automatici conformi ai criteri di Intune. Inserire `android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"` nel manifesto dell'app.

2. Quando si decide quale tipo di backup completo deve ricevere l'app (non filtrato, filtrato o nessuno) impostare l'attributo `android:fullBackupContent` su true, false o su una risorsa XML all'interno dell'applicazione. Copiare tutto il contenuto di `android:fullBackupContent` in un tag di metadati denominato `com.microsoft.intune.mam.FullBackupContent`.

    Ad esempio, se si vuole che l'app riceva backup completi in base a regole personalizzate in un file XML, fornire una risorsa nel tag di metadati `com.microsoft.intune.mam.FullBackupContent` nel manifesto simile al seguente:
    ```
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```



#### <a name="keyvalue-backup"></a>Backup di chiave/valore

Questa opzione di backup di chiave/valore è disponibile per tutte le API e usa `BackupAgentHelper` e `BackupAgent`.

##### <a name="backupagenthelper"></a>BackupAgentHelper

`BackupAgentHelper` è molto più semplice dell'implementazione di `BackupAgent` in termini sia di funzionalità di Android native sia di integrazione di MAM. `BackupAgentHelper` permette di registrare interi file e preferenze condivise in `FileBackupHelper` o `SharedPreferencesBackupHelper`, rispettivamente. Questi vengono quindi aggiunti a `BackupAgentHelper` al momento della creazione.

##### <a name="backupagent"></a>BackupAgent

`BackupAgent` permette di definire in modo molto più esplicito i dati di cui eseguire il backup. Questa opzione implica che non sarà possibile trarre vantaggio dal framework di backup di Android. Dato che lo sviluppatore è responsabile dell'implementazione, sono necessari altri passaggi per garantire una protezione dati tramite MAM appropriata. Il maggior carico di lavoro ricade sullo sviluppatore e questo fa sì che l'integrazione di MAM sia leggermente più coinvolta.

###### <a name="app-does-not-have-a-backup-agent"></a>L'app non ha un agente di backup

Queste sono le opzioni per lo sviluppatore quando `android:allowBackup =true`.

####### <a name="full-backup-according-to-a-configuration-file"></a>Backup completo in base a un file di configurazione

Specificare una risorsa all'interno del tag dei metadati `com.microsoft.intune.mam.FullBackupContent` nel manifesto. Ad esempio:     `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Aggiungere questo attributo nel tag `<application>` : `android:fullBackupContent="@xml/my_scheme"`, dove `my_scheme` è una risorsa XML nell'app.

####### <a name="full-backup-without-exclusions"></a>Backup completo senza esclusioni

Specificare un tag nel manifesto, ad esempio `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />`.

Aggiungere questo attributo nel tag `<application>`: `android:fullBackupContent="true"`.

###### <a name="app-has-a-backup-agent"></a>L'app ha un agente di backup

Seguire i consigli riportati in precedenza in questa guida per `BackupAgent` e `BackupAgentHelper`.

Valutare se passare a usare `MAMDefaultFullBackupAgent`, che offre un semplice backup su Android Marshmallow.

##### <a name="before-your-backup"></a>Prima del backup

Prima di avviare il backup, è necessario verificare che i file o i buffer di dati di cui si prevede di eseguire il backup siano abilitati per il backup. A tale scopo è disponibile una funzione `isBackupAllowed` in `MAMFileProtectionManager` e `MAMDataProtectionManager`. Se il file o il buffer di dati non è abilitato per il backup, non è possibile continuare a usarlo nel backup.

Se a un certo punto durante il backup si vuole eseguire il backup delle identità per i file verificati nel passaggio 1, è necessario chiamare `backupMAMFileIdentity(BackupDataOutput data, File … files)` con i file da cui si prevede di estrarre dati. In questo modo, verranno automaticamente create entità di backup, che verranno scritte in `BackupDataOutput`. Queste entità verranno utilizzate automaticamente al momento del ripristino.

#### <a name="azure-directory-authentication-library-setup"></a>Configurazione di Active Directory Authentication Library  

L'SDK si basa su ADAL per lo scenario di autenticazione e avvio condizionale. Questi scenari richiedono che le app siano parte della configurazione di Azure Active Directory (Azure AD). I valori di configurazione vengono comunicati all'SDK tramite i metadati `AndroidManifest` .

Per configurare l'app e abilitare l'autenticazione appropriata, aggiungere il codice seguente al nodo dell'app in `AndroidManifest`. Alcune di queste configurazioni sono necessarie solo se l'app usa ADAL per l'autenticazione in generale. In tal caso, saranno necessari i valori specifici usati dall'applicazione per registrarsi con Azure AD. Ciò garantisce che all'utente finale non venga chiesta l'autenticazione due volte, perché Azure AD riconosce due valori di registrazione separati, uno dall'app e uno dall'SDK.

        <meta-data
            android:name="com.microsoft.intune.mam.aad.Authority"
            android:value="https://AAD authority/" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.ClientID"
            android:value="your-client-ID-GUID" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.NonBrokerRedirectURI"
            android:value="your-redirect-URI" />
        <meta-data
            android:name="com.microsoft.intune.mam.aad.SkipBroker"
            android:value="[true | false]" />

I GUID non devono avere la parentesi graffa iniziale o finale.

##### <a name="common-adal-configurations"></a>Configurazioni comuni di ADAL

Di seguito sono indicate le configurazioni comuni per i valori descritti in precedenza.

###### <a name="app-does-not-integrate-adal"></a>ADAL non è integrato nell'app

* L'autorità deve essere impostata sull'ambiente desiderato in cui sono stati configurati gli account Azure AD.

* SkipBroker deve essere impostato su true.

###### <a name="app-integrates-adal"></a>ADAL è integrato nell'app

* L'autorità deve essere impostata sull'ambiente desiderato in cui sono stati configurati gli account Azure AD.

* L'ID client deve essere impostato sull'ID client dell'app.

* `NonBrokerRedirectURI` deve essere impostato su un URI di reindirizzamento valido per l'app. Oppure `urn:ietf:wg:oauth:2.0:oob` deve essere configurato come URI di reindirizzamento valido di Azure AD.

* SkipBroker deve essere impostato su false (o essere assente).

* Azure AD deve essere configurato in modo da accettare l'URI di reindirizzamento del broker.

###### <a name="app-integrates-adal-but-does-not-support-the-azure-ad-authenticator-app"></a>ADAL è integrato nell'app, ma l'app non supporta l'app Azure AD Authenticator

* L'autorità deve essere impostata sull'ambiente desiderato in cui sono stati configurati gli account Azure AD.

* L'ID client deve essere impostato sull'ID client dell'app.

* `NonBrokerRedirectURI` deve essere impostato su un URI di reindirizzamento valido per l'app. Oppure `urn:ietf:wg:oauth:2.0:oob` deve essere configurato come URI di reindirizzamento valido di Azure AD.

#### <a name="logging-in-the-sdk"></a>Registrazione nell'SDK

La registrazione viene eseguita tramite il framework `java.util.logging` . Per ricevere i log, configurare la registrazione globale come descritto nella [guida tecnica di Java](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). A seconda dell'app, `App.onCreate` è in genere il punto migliore in cui avviare la registrazione. I messaggi dei registri vengono codificati in base al nome di classe, che potrebbe essere nascosto.

###<a name="multi-identity"></a>Supporto per identità multiple

Per impostazione predefinita, Intune App SDK applicherà i criteri all'app nel suo complesso. La funzionalità MAM per l'uso delle identità multiple può essere abilitata per applicare un criterio a livello delle singole identità. Ciò richiede una partecipazione dell'app molto più attiva rispetto ad altre funzionalità di gestione delle applicazioni mobili. L'app deve informare l'SDK dell'app quando intende modificare l'identità attiva. L'SDK deve anche inviare una notifica all'app quando è necessaria una modifica di identità.

Attualmente è supportata solo l'identità gestita. Dopo che l'utente registra il dispositivo o l'app, l'SDK usa questa identità e la considera l'identità primaria gestita. Gli altri utenti dell'app vengono trattati come non gestiti con impostazioni di criteri limitate.

Si noti che un'identità viene semplicemente definita come stringa. Le identità non fanno distinzione tra maiuscole e minuscole. Le richieste di identità all'SDK potrebbero non restituire la stessa distinzione usata originariamente durante l'impostazione dell'identità.

####<a name="enabling-multi-identity"></a>Abilitazione di identità multiple

Per impostazione predefinita, tutte le app sono considerate app a identità singola. Un'app dichiara di poter riconoscere identità multiple inserendo i metadati seguenti nel manifesto Android.

```
<meta-data
            android:name="com.microsoft.intune.mam.MAMMultiIdentity"
            android:value="true" />
```
####<a name="setting-the-identity"></a>Impostazione dell'identità

È possibile impostare l'identità dell'app sui livelli seguenti:

1. A livello di processo

2. A livello di contesto (in genere `Activity`)

3. A livello di thread

Un'identità impostata a livello di thread ha una priorità maggiore rispetto a un'identità impostata a livello di `Context` che sostituisce a sua volta un'identità impostata a livello di processo. Un'identità impostata a livello di `Context` viene usata solo nei casi appropriati. Alle attività di I/O su file, ad esempio, non è associato un `Context`. È possibile usare i metodi seguenti in `MAMPolicyManager` per impostare l'identità e recuperare i valori di identità impostati in precedenza.

```
public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

public static String getUIPolicyIdentity(final Context context);

public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

public static String getProcessIdentity();

public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

public static String getCurrentThreadIdentity();

/**
 * Get the currently applicable app policy. Same as MAMComponents.get(AppPolicy.class). This method does
    not take the context identity into account.
 */
public static AppPolicy getPolicy();

/**
 * Get the currently applicable app policy, taking the context
 * identity into account.
 */
public static AppPolicy getPolicy(final Context context);


public static AppPolicy getPolicyForIdentity(final String identity);

public static boolean getIsIdentityManaged(final String identity);

```
È anche possibile cancellare l'identità dell'app impostandola su Null. Una stringa vuota può essere usata come un'identità che non avrà mai restrizioni. Tutti i metodi per impostare l'identità restituiscono valori di risultato tramite ``` MAMIdentitySwitchResult```. Possono essere restituiti quattro valori:

* **SUCCEEDED**: la modifica di identità è riuscita.

* **NOT_ALLOWED**: la modifica di identità non è consentita. Questa condizione si verifica se viene eseguito un tentativo di passare a un utente aziendale diverso che appartiene alla stessa società dell'utente registrato. Può anche verificarsi in seguito al tentativo di impostare l'identità dell'interfaccia utente (`Context`) quando un'identità diversa è impostata sul thread corrente.

* **CANCELLED**: l'utente ha annullato la modifica di identità, in genere scegliendo il pulsante Indietro in una richiesta di PIN/autenticazione.

* **FAILED**: la modifica di identità non è riuscita per un motivo non specificato.

Nel caso dell'impostazione di un'identità a livello di `Context`, il risultato viene restituito in modo asincrono. Se `Context` è una classe `Activity`, non sarà noto se la modifica di identità è riuscita fino a dopo il lancio condizionale. Un avvio condizionale potrebbe richiedere all'utente di immettere un PIN o le proprie credenziali aziendali complete. È previsto che l'app implementi ```MAMSetUIIdentityCallback``` per ricevere questo risultato, nonostante sia possibile passare Null per questo parametro.

```
public interface MAMSetUIIdentityCallback {
    void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
}
```

È anche possibile impostare l'identità di un'attività direttamente tramite un metodo su `MAMActivity` invece di chiamare ```MAMPolicyManager.setUIPolicyIdentity```. Per eseguire questa operazione, è possibile usare il metodo seguente:

 ```public final void switchMAMIdentity(final String newIdentity);```

Le app possono anche eseguire l'override di un metodo su `MAMActivity` per ricevere la notifica del risultato di tentativi di modifica dell'identità per tale attività.

```public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);```

> [!NOTE]
> Il cambio di identità potrebbe rendere necessario ricreare l'attività. In questo caso, il callback ```onSwitchMAMIdentityComplete``` verrà recapitato alla nuova istanza dell'attività.


####<a name="implicit-identity-changes"></a>Modifiche di identità implicite

Oltre alla possibilità di impostare l'identità tramite l'app, l'identità a livello di thread o contesto può cambiare anche in base all'ingresso di dati da un'altra app abilitata per MAM. Ad esempio, se un'attività viene avviata da una classe `Intent` inviata da un'altra app MAM, l'identità dell'attività verrà impostata in base all'identità effettiva nell'altra app al momento dell'invio della classe `Intent`.

Per i servizi, l'identità del thread verrà impostata in modo analogo per la durata di una chiamata `onStart` o `onBind`. Anche le chiamate al `Binder` restituito da `onBind` imposteranno temporaneamente l'identità del thread. Le chiamate a ```ContentProvider``` imposteranno l'identità del thread in modo analogo per la loro durata.

Inoltre, l'interazione dell'utente con un'attività potrebbe causare un cambio di identità implicito. Se un utente annulla una richiesta di autorizzazione durante ```Resume```, ad esempio, il risultato sarà il passaggio implicito a un'identità vuota.
L'app ha la possibilità di essere messa a conoscenza di queste modifiche e, in alcuni casi, di impedirle se necessario. ```MAMService``` e ```MAMContentProvider``` espongono il metodo seguente che può essere sottoposto a override dalle sottoclassi:

```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
```
Nel caso di ```MAMActivity```, nel metodo è presente un parametro aggiuntivo:
```
public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
```
La parte ```AppIdentitySwitchReason``` acquisisce l'origine del cambio implicito e può accettare i valori ```CREATE```, ```RESUME_CANCELLED``` e ```NEW_INTENT```.  Il motivo ```RESUME_CANCELLED``` viene usato quando la ripresa di un'attività comporta la visualizzazione dell'interfaccia utente per l'immissione del PIN, per l'autenticazione o per altre esigenze di conformità e l'utente prova a eliminare tale interfaccia, in genere usando il pulsante Indietro.
```AppIdentitySwitchResultCallback``` è come segue:
```
public interface AppIdentitySwitchResultCallback {
    /**
     * @param result
     *            whether the identity switch can proceed.
     */
    void reportIdentitySwitchResult(AppIdentitySwitchResult result);
}
```
```AppIdentitySwitchResult``` corrisponde a ```SUCCESS``` o ```FAILURE```.

Il metodo ```onMAMIdentitySwitchRequired``` viene chiamato per tutte le modifiche di identità implicite ad eccezione di quelle effettuate tramite un `Binder` restituito da ```MAMService.onMAMBind```. L'implementazione predefinita di ```onMAMIdentitySwitchRequired``` chiama immediatamente ```reportIdentitySwitchResult(FAILURE)``` quando il motivo è ```RESUME_CANCELLED``` e ```reportIdentitySwitchResult(SUCCESS)``` in tutti gli altri casi.

La maggior parte delle app non dovrà probabilmente bloccare o ritardare un cambio di identità in modo diverso, tuttavia, in caso sia necessario, tenere presente quanto segue:

* Se un cambio di identità è bloccato, il risultato è lo stesso che si sarebbe avuto se le impostazioni di condivisione di ```Receive``` avessero vietato l'ingresso dei dati.

* Se un servizio è in esecuzione sul thread principale, è *necessario* chiamare ```reportIdentitySwitchResult``` in modo sincrono o il thread dell'interfaccia utente si bloccherà.

* Per la creazione di ```Activity```, ```onMAMIdentitySwitchRequired``` verrà chiamato prima di ```onMAMCreate```. Se l'app deve visualizzare l'interfaccia utente per controllare se consentire il cambio di identità, tale interfaccia utente deve essere visualizzata usando un'attività diversa.

* In ```Activity```, quando viene richiesto il passaggio all'identità vuota con il motivo ```RESUME_CANCELLED```, l'app deve cambiare l'attività ripresa in modo da mostrare dati coerenti con il cambio di identità. In caso contrario, l'app deve rifiutare il cambio e all'utente verrà richiesto di nuovo di conformarsi ai criteri per l'identità di ripresa, ad esempio con la visualizzazione della schermata per l'immissione del PIN.

> [!NOTE]
> Un'app con identità multiple riceverà sempre dati in arrivo sia da app gestite che non gestite. È responsabilità dell'app trattare i dati provenienti da identità gestite in modo gestito. Se un'identità richiesta è ```(MAMPolicyManager.getIsIdentityManaged)``` gestita, ma l'app non può usare tale account (ad esempio, perché gli account, come gli account di posta elettronica, devono essere prima di tutto configurati nell'app) il cambio di identità deve essere rifiutato.

###<a name="file-protection"></a>Protezione dei file

A ogni file è associata un'identità al momento della creazione in base all'identità a livello di processo e thread. Questa identità viene usata sia per la crittografia dei file che per la cancellazione selettiva. Verranno crittografati solo i file per la cui identità sono previsti criteri che richiedono la crittografia. La cancellazione selettiva predefinita dell'SDK eseguirà la cancellazione solo dei file associati all'identità per la quale è stata richiesta una cancellazione. L'app può richiedere o modificare l'identità di un file con ```MAMFileProtectionManager```.
```
public final class MAMFileProtectionManager {

    /**
     * Protect a file. This will synchronously trigger whatever protection is required for the file, and will tag the file for
     * future protection changes.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     * @throws IOException
     *             If the file cannot be changed.
     */
    public static void protect(final File file, final String identity) throws IOException;

    /**
     * Get the protection info on a file.
     *
     * @param file
     *            File or directory to get information on.
     * @return File protection info, or null if there is no protection info.
     * @throws IOException
     *             If the file cannot be read or opened.
     */
    public static MAMFileProtectionInfo getProtectionInfo(final File file) throws IOException;
}

public interface MAMFileProtectionInfo {
String getIdentity();
}
```

> [!NOTE]
> La modalità offline influisce sull'aggiunta di tag di identità ai file. Occorre tenere conto dei punti seguenti:
> * Se l'app Portale aziendale non è installata, non è possibile assegnare tag di identità ai file.
>
> * Se l'app Portale aziendale è installata, ma non ha criteri, non è possibile assegnare tag di identità ai file in modo affidabile.
>
> * Quando diventa disponibile la possibilità di assegnare tag di identità ai file, tutti i file creati in precedenza sono considerati personali (appartenenti all'identità con stringa vuota), a meno che l'app non sia stata installata in precedenza come app gestita con identità singola. In questo caso i file vengono considerati appartenenti all'utente registrato.

####<a name="data-protection"></a>Protezione dati

Non è possibile assegnare un tag a un file appartenente a più identità. Le app che devono archiviare dati appartenenti a utenti diversi nello stesso file possono farlo manualmente usando le funzionalità fornite da ```MAMDataProtectionManager```. Questo permette all'app di crittografare i dati e associarli a un utente specifico. I dati crittografati sono adatti per l'archiviazione su disco in un file. È possibile recuperare i dati associati all'identità e i dati possono essere decrittografati in un secondo momento.

```
public final class MAMDataProtectionManager {
    /**
     * Protect a stream. This will return a stream containing the protected
 * input.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect, read sequentially. This function
 *            will change the position of the stream but may not have
     *            read the entire stream by the time it returns. The
 *            returned stream will wrap this one. Calls to read on the
     *            returned stream may cause further reads on the original
 *            input stream. Callers should not expect to read directly
     *            from the input stream after passing it to this method.
 *            Calling close on the returned stream will close this one.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static InputStream protect(final InputStream input, final String identity);

    /**
     * Protect a byte array. This will return protected bytes.
     *
     * @param identity
     *            Identity to set.
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be protected
     */
    public static byte[] protect(final byte[] input, final String identity) throws IOException;

    /**
     * Unprotect a stream. This will return a stream containing the
 * unprotected input.
     *
     * @param input
     *            Input data to protect, read sequentially.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static InputStream unprotect(final InputStream input) throws IOException;

    /**
     * Unprotect a byte array. This will return unprotected bytes.
     *
     * @param input
     *            Input data to protect.
     * @return Protected input data.
     * @throws IOException
     *             If the data could not be unprotected
     */
    public static byte[] unprotect(final byte[] input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input stream to get information on. Either this input
 *            stream must have been returned by a previous call to
      *            protect OR input.markSupported() must return true.
 *            Otherwise it will be impossible to get protection info
 *            without advancing the stream position. The stream must be
 *            positioned at the beginning of the protected data.
     * @return Data protection info, or null if there is no protection
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final InputStream input) throws IOException;

    /**
     * Get the protection info on a stream.
     *
     * @param input
     *            Input bytes to get information on. These must be bytes
 *            returned by a previous call to protect() or a copy of
 *            such bytes.
     * @return Data protection info, or null if there is no protection
 *            info.
     * @throws IOException
     *             If the input cannot be read.
     */
    public static MAMDataProtectionInfo getProtectionInfo(final byte[] input) throws IOException;
}
```
###<a name="content-providers"></a>Provider di contenuto

Se l'app fornisce potenzialmente dati aziendali diversi da un ```ParcelFileDescriptor``` tramite un ```ContentProvider```, l'app deve chiamare il metodo ```isProvideContentAllowed(String)``` di ```MAMContentProvider``` passando l'```UPN``` del proprietario per il contenuto. Se questa funzione restituisce false, il contenuto non può essere restituito al chiamante. I descrittori di file restituiti tramite un provider di contenuti vengono gestiti automaticamente in base all'identità del file.

###<a name="selective-wipe"></a>Cancellazione selettiva

Se un'app si registra per la notifica ```WIPE_USER_DATA```, non potrà usufruire dei vantaggi del comportamento di cancellazione selettiva predefinito dell'SDK. Per le app che supportano identità multiple, questo aspetto potrebbe essere più significativo perché la cancellazione selettiva predefinita di MAM comporterà la cancellazione solo dei file che corrispondono all'identità da cancellare.

Se si sta creando un'app che supporta identità multiple, è possibile registrarsi per ```WIPE_USER_AUXILIARY_DATA```. Questa notifica consente di sfruttare il comportamento di cancellazione predefinito dell'SDK. Questa notifica verrà inviata immediatamente prima di eseguire la cancellazione selettiva predefinita dell'SDK. Si noti che un'app non deve mai registrarsi sia per ```WIPE_USER_DATA``` che per ```WIPE_USER_AUXILIARY_DATA```.

### <a name="known-platform-limitations"></a>Limitazioni note della piattaforma

#### <a name="file-size-limitations"></a>Limitazioni relative alle dimensioni dei file

In Android le limitazioni del formato di file eseguibile Dalvik potrebbero diventare un problema per codebase di grandi dimensioni eseguite senza ProGuard. Nello specifico, potrebbero esistere le limitazioni seguenti:

* Limite a 65.000 per i campi

* Limite a 65.000 per i metodi

Quando si includono molti progetti, ogni elemento `android:package` ottiene una copia di R, aumentando notevolmente il numero di campi man mano che vengono aggiunte librerie. Le indicazioni seguenti potrebbero aiutare a ridurre questo limite:

* Tutti i progetti di libreria devono condividere lo stesso elemento `android:package` ogni volta che è possibile. Questo comportamento non genera occasionalmente errori nel campo, perché si tratta puramente di un problema in fase di compilazione. Inoltre, le nuove versioni di Android SDK pre-elaborano i file DEX per rimuovere parte della ridondanza. In questo modo, la distanza dai campi viene ulteriormente ridotta.

* Usare gli strumenti di compilazione di Android SDK più recenti disponibili.

* Rimuovere tutte le librerie non necessarie e inutilizzate, ad esempio `android.support.v4`.

#### <a name="policy-enforcement-limitations"></a>Limitazioni relative all'applicazione di criteri

**Acquisizione schermo**: l'SDK non riesce ad applicare un nuovo valore dell'impostazione di acquisizione schermo nelle classi `Activity` già passate attraverso `Activity.onCreate`. Questo limite può provocare un periodo di tempo in cui l'app è stata configurata per la disabilitazione degli screenshot, ma è comunque possibile acquisire screenshot.

**Resolver di contenuto**: i criteri di trasferimento o di ricezione potrebbero bloccare interamente o parzialmente l'uso di un resolver di contenuto per accedere al provider di contenuti in un'altra app. Questo comportamento può far sì che i metodi `ContentResolver` restituiscano null o generino un valore di errore. Ad esempio, `openOutputStream` genera `FileNotFoundException` se è bloccato. L'applicazione può effettuare la chiamata per verificare se un criterio ha causato (o potrebbe causare) un errore durante la scrittura di dati attraverso un resolver di contenuto:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Servizi esportati**: il file `AndroidManifest.xml` incluso in Intune App SDK ha `MAMNotificationReceiverService`. Deve trattarsi di un servizio esportato per consentire all'app Portale aziendale di inviare notifiche a un'app abilitata. Il servizio verifica il chiamante per garantire che l'invio di notifiche sia consentito solo all'app Portale aziendale.

### <a name="android-best-practices"></a>Procedure consigliate per Android

Intune SDK mantiene il contratto fornito dall'API Android, ma potrebbero essere generate condizioni di errore più frequentemente come conseguenza dell'applicazione dei criteri. Queste procedure consigliate per Android riducono la probabilità di errore:

* Le funzioni di Android SDK che potrebbero restituire null hanno una maggiore probabilità di essere già null. Per ridurre al minimo i problemi, assicurarsi che i controlli dei valori null vengano eseguiti nei punti corretti.

* Per le funzionalità che è possibile verificare, usare le API SDK.

* Tutte le funzioni derivate devono effettuare chiamate attraverso le rispettive versioni delle superclassi.

* Evitare un uso ambiguo di qualsiasi API. Ad esempio, usare `Activity.startActivityForResult/onActivityResult` senza il controllo di `requestCode` provocherà un comportamento anomalo.

