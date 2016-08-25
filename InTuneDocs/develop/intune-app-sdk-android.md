---
title: Manuale dello sviluppatore di Microsoft Intune App SDK per Android | Microsoft Intune
description: 
keywords: 
author: Msmbaldwin
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 51f7734e2acced469ec3520d74a8079dac8223f2
ms.openlocfilehash: bcb62e9c99c1f5a5b53ada688ef39a59674dea04


---

# Guida a Microsoft Intune App SDK per sviluppatori di Android

> [!NOTE]
> Può essere utile leggere prima [Panoramica di Intune App SDK](intune-app-sdk.md), che illustra le attuali funzionalità dell'SDK e descrive come preparare l'integrazione in ogni piattaforma supportata. 

# Contenuto dell'SDK 

Intune App SDK per Android è una libreria Android standard senza dipendenze esterne. L'SDK è costituito da:  

* **`Microsoft.Intune MAM.SDK.jar`**: interfacce necessarie per abilitare MAM in un'app, nonché l'interoperabilità con l'app Portale aziendale di Microsoft. Le app devono specificare questo file come riferimento alla libreria Android.

*  **`Microsoft.Intune.MAM.SDK.Support.v4.jar`**: interfacce necessarie per abilitare MAM nelle app che usano la libreria di supporto android v4.  Le app che necessitano questo supporto devono fare riferimento al file JAR direttamente. 

* **`Microsoft.Intune.MAM.SDK.Support.v7.jar`**: interfacce necessarie per abilitare MAM nelle app che usano la libreria di supporto android v7.   Le app che necessitano questo supporto devono fare riferimento al file JAR direttamente.

* **Directory delle risorse**: risorse (come le stringhe) su cui è basato l'SDK. 

* **`Microsoft.Intune.MAM.SDK.aar`**: componenti dell'SDK, ad eccezione dei file JAR Support.V4 e Support.V7. Questo file può essere usato al posto dei singoli componenti se il sistema di compilazione supporta i file AAR.

* **`AndroidManifest.xml`**: punti di ingresso aggiuntivi e requisiti della libreria. 

* **`THIRDPARTYNOTICES.TXT`**: avviso di attribuzione che riconosce la presenza di codice OSS e/o di terze parti che verrà compilato nell'app. 

# Requisiti 

Intune App SDK è un progetto Android compilato. Di conseguenza, è altamente indipendente dalla versione di Android usata dall'app per le versioni delle API minime o di destinazione. L'SDK supporta le API da Android 14 (Android 4.0+) ad Android 24. 

# Funzionamento di Intune App SDK 

Intune App SDK richiede l'applicazione di modifiche al codice sorgente di un'app per abilitare i criteri di gestione delle app. A questo scopo, vengono sostituite le classi base per Android con le classi gestite equivalenti, cui viene fatto riferimento nel documento usando il prefisso `MAM`. Le classi dell'SDK si trovano tra la classe base per Android e la versione derivata dell'app di tale classe.  Usando un'attività come esempio, la gerarchia di ereditarietà risultante ha un aspetto simile a questa: `Activity ->MAMActivity->AppSpecificActivity`.

Quando `AppSpecificActivity` vuole interagire con l'elemento padre, ad esempio `super.onCreate())`, `MAMActivity` è la superclasse nonostante si trovi nella gerarchia di ereditarietà e sostituisca alcuni metodi. Le app di Android hanno una modalità singola e possono accedere all'intero sistema tramite l'oggetto Context.  Le app in cui è integrato Intune App SDK, d'altro canto, hanno modalità doppie, in quanto continuano ad accedere al sistema tramite l'oggetto Context, ma, a seconda della classe base Activity usata, l'oggetto Context viene fornito da Android oppure viene sottoposto a multiplex avanzato tra una visualizzazione con restrizioni del sistema e l'oggetto Context fornito da Android.

Intune App SDK per Android è basato sulla presenza dell'app Portale aziendale nel dispositivo per l'abilitazione dei criteri MAM. Quando l'app Portale aziendale non è presente, il comportamento dell'app abilitata per MAM non viene modificato e l'app si comporta come qualsiasi altra app per dispositivi mobili. Quando l'app Portale aziendale è installata e include criteri per l'utente, i punti di ingresso dell'SDK vengono inizializzati in modo asincrono. L'inizializzazione è necessaria solo quando il processo viene creato inizialmente da Android. Durante l'inizializzazione viene stabilita una connessione all'app Portale aziendale e vengono scaricati i criteri di restrizione alle app.  

# Come implementare l'integrazione con Intune App SDK
 
Come indicato in precedenza, l'SDK richiede l'applicazione di modifiche al codice sorgente dell'app per abilitare i criteri di gestione delle app. Ecco i passaggi necessari per abilitare MAM nell'app: 

## Sostituire classi, metodi e attività con i rispettivi equivalenti MAM (obbligatorio) 

* Le classi base di Android devono essere sostituite dal rispettivo equivalente MAM. A questo scopo, trovare tutte le istanze delle classi elencate nella tabella seguente e sostituirle con l'equivalente di Intune App SDK.  

    | Classe Android | Sostituzione di Intune App SDK |
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
    | android.app.PendingIntent | MAMPendingIntent |
    | android.app.Service | MAMService |
    | android.app.TabActivity | MAMTabActivity |
    | android.app.TaskStackBuilder | MAMTaskStackBuilder |
    | android.app.backup.BackupAgent | MAMBackupAgent |
    | android.app.backup.BackupAgentHelper | MAMBackupAgentHelper |
    | android.app.backup.FileBackupHelper | MAMFileBackupHelper |
    | android.app.backup.SharePreferencesBackupHelper | MAMSharedPreferencesBackupHelper |
    | android.content.BroadcastReceiver | MAMBroadcastReceiver |
    | android.content.ContentProvider | MAMContentProvider |
    | android.os.Binder | MAMBinder* |
    | android.provider.DocumentsProvider | MAMDocumentsProvider |
    | android.preference.PreferenceActivity | MAMPreferenceActivity |

    *È necessario sostituire Binder con MAMBinder solo se il binder non è generato da un'interfaccia AIDL.

    **Microsoft.Intune.MAM.SDK.Suppot.v4.jar**:

    | MAM di Intune - Classe Android | Sostituzione dell'SDK |
    |--|--|
    | android.support.v4.app.DialogFragment | MAMDialogFragment
    | android.support.v4.app.FragmentActivity | MAMFragmentActivity
    | android.support.v4.app.Fragment | MAMFragment
    | android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
    | android.support.v4.content.FileProvider | MAMFileProvider
    
    **Microsoft.Intune.MAM.SDK.Suppot.v7.jar**:

    |Classe Android | Sostituzione dell'SDK per MAM Intune |
    |--|--|
    |android.support.v7.app.ActionBarActivity | MAMActionBarActivity |


* Quando si usa un punto di ingresso Android sostituito dall'equivalente MAM, deve essere usata una versione alternativa del ciclo di vita del punto di ingresso (ad eccezione della classe `MAMApplication`).

    Ad esempio, quando si deriva da `MAMActivity`, invece di sostituire `onCreate` e chiamare `super.onCreate`, la classe Activity deve sostituire `onMAMCreate` e chiamare`uper.onMAMCreate`. In questo modo l'avvio di Activity (tra le altre operazioni) viene limitato in alcuni casi. 

# Abilitare le funzionalità che richiedono la partecipazione dell'app 

Alcuni criteri non possono essere implementati direttamente dall'SDK. Per consentire all'app di controllare il proprio comportamento per queste funzionalità, è necessario esporre diverse API, che è possibile trovare nell'interfaccia `AppPolicy` inclusa di seguito.  

    /**
     * External facing app policies.
     */
    public interface AppPolicy {
        /**
         * Restrict where an app can save personal data.
         * 
         * @return True if the app is allowed to save to personal data stores;
         *         false otherwise.
         */
        boolean getIsSaveToPersonalAllowed();
    
        /**
         * Check if policy prohibits saving to a content provider location.
         * 
         * @param location
         *            a content URI to check
         * @return True if location is not a content URI or if policy does not 
         *         prohibit saving to the content location.
         */
        boolean getIsSaveToLocationAllowed(android.net.Uri location); 
    
        /**
         * Whether the SDK PIN prompt is enlightened for the app.
         * 
         * @return True if the PIN is enabled. False otherwise.
         */
        boolean getIsPinRequired();
        /**
         * Whether the Intune Managed Browser is required to open web links.
         *
         * @return True if the Managed Browser is required, false otherwise
         */
        boolean getIsManagedBrowserRequired();
    }

## Abilitare il controllo dell'amministratore IT sul comportamento di salvataggio dell'app

Molte app implementano funzionalità che consentono all'utente finale di salvare file in locale o in un altro servizio. Intune App SDK permette agli amministratori IT di prevenire la perdita dei dati applicando restrizioni di criteri nel modo che ritengono appropriato all'interno dell'organizzazione.  Uno dei criteri che gli amministratori possono controllare determina se l'utente finale possa o meno salvare in un archivio dati personale. È incluso il salvataggio in un percorso locale, una scheda SD o un servizio di backup. La partecipazione dell'app è necessaria per l'abilitazione della funzionalità. Se l'app consente il salvataggio in percorsi personali o nel cloud direttamente dall'app stessa, è necessario implementare questa funzionalità per garantire che l'amministratore IT possa controllare se il salvataggio in una determinata posizione sia o meno consentito. L'API seguente consente all'app di riconoscere se il salvataggio in un archivio personale è o meno consentito in base agli attuali criteri dell'amministratore. L'app può quindi applicare i criteri, in quanto è in grado di determinare che è disponibile un archivio dati personale per l'utente finale attraverso se stessa.  

Per determinare se i criteri vengono applicati, l'app può effettuare la chiamata seguente: 

    MAMComponents.get(AppPolicy.class).getIsSaveToPersonalAllowed();

**Nota**: MAMComponents.get(AppPolicy.class) restituisce sempre criteri di app diversi da null, anche se l'app o il dispositivo non è gestito. 

## Consentire all'app di rilevare se sono necessari criteri PIN
 
 Esistono criteri aggiuntivi in base ai quali l'app può voler disabilitare alcune delle proprie funzionalità in modo da non duplicare funzionalità in Intune App SDK. Ad esempio, se l'app un'esperienza utente tramite PIN, potrebbe voler disabilitarla se l'SDK è configurato in modo che l'utente finale debba immettere un PIN. 

Per determinare se sono configurati criteri PIN per richiedere l'immissione periodica di un PIN, l'app può effettuare la chiamata seguente: 

    MAMComponents.get(AppPolicy.class).getIsPinRequired();

## Registrazione per le notifiche dall'SDK  

Intune App SDK consente all'app di controllare il comportamento quando determinati criteri, come quelli per la cancellazione remota, vengono usati dall'amministratore IT. A questo scopo, è necessario effettuare la registrazione per le notifiche dall'SDK creando una classe `MAMNotificationReceiver` e registrandola con `MAMNotificationReceiverRegistry`. Ciò avviene specificando il ricevente e il tipo di notifica che questi vuole ricevere in  `App.onCreate`, come nell'esempio seguente:
 
    @Override
      public void onCreate() {
            super.onCreate();
    MAMComponents.get(MAMNotificationReceiverRegistry.class).registerReceiver(
    new ToastNotificationReceiver(), MAMNotificationType.WIPE_USER_DATA);
    }

`MAMNotificationReceiver` riceve semplicemente le notifiche. Alcune notifiche vengono gestite direttamente dall'SDK, altre richiedono la partecipazione dell'app. Un'app deve restituire true o false da una notifica. L'app deve sempre restituire true, a meno che un'azione che l'app tenta di eseguire come risultato della notifica non riesca. Questo errore può essere segnalato al servizio Intune, ad esempio quando l'app indica che non è riuscita a cancellare i dati utente. Il blocco in `MAMNotificationReceiver.onReceive`è sicuro, in quanto il callback non viene eseguito nel thread dell'interfaccia utente. 

L'interfaccia `MAMNotificationReceiver è inclusa di seguito come definito nell'SDK: 

    /**
     * The SDK is signaling that a MAM event has occurred. 
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

Le notifiche seguenti vengono inviate all'app e alcune possono richiedere la partecipazione dell'app: 

* **Notifica `WIPE_USER_DATA`**: questa notifica viene inviata in una classe `MAMUserNotification`. Alla ricezione della notifica, l'app deve eliminare tutti i dati associati all'identità passata con la classe `MAMUserNotification`. Questa notifica viene attualmente inviata durante l'annullamento della registrazione del servizio Intune. Il nome primario dell'utente viene in genere specificato durante il processo di registrazione. Se si effettua la registrazione per questa notifica, l'app deve garantire che tutti i dati utente siano stati eliminati. Se la registrazione non viene effettuata, verrà usato il comportamento di cancellazione selettiva predefinito. 

* **Notifica `WIPE_USER_AUXILIARY_DATA`**: le app possono effettuare la registrazione per questa notifica se vogliono che Intune App SDK esegua la cancellazione predefinita, ma devono comunque rimuovere dati ausiliari durante la cancellazione.  

* **Notifica `REFRESH_POLICY`**: questa notifica viene inviata in una classe MAMNotification senza informazioni aggiuntive. Alla ricezione di questa notifica, tutti i criteri memorizzati nella cache devono essere considerati non più invalidati e di conseguenza è necessario verificare di quale criteri si tratti. Questa operazione viene gestita in genere dall'SDK,ma deve essere gestita dall'app se i criteri vengono usati in un modo permanente. 

## Tipi e metodi in sospeso 

In seguito alla derivazione da uno dei punti di ingresso MAM, è possibile usare l'oggetto Context normalmente per avviare attività, usando `PackageManager`e così via.  Gli oggetti  `PendingIntents` costituiscono un'eccezione a questa regola. Quando si chiamano queste classi, è necessario modificare il nome di classe. Ad esempio, invece di usare `PendingIntent.get*`, `MAMPendingIntents.get*` . 

In alcuni casi, un metodo disponibile nella classe Android è stato contrassegnato come finale nella classe sostitutiva MAM. In questo caso, la classe sostitutiva MAM fornisce un metodo denominato in modo analogo (in genere con suffisso "MAM"), che deve essere sostituito al suo posto. Ad esempio, invece di sostituire `ContentProvider.query`, è necessario sostituire `MAMContentProvider.queryMAM`. Il compilatore Java deve applicare le restrizioni finali per impedire la sostituzione accidentale del metodo originale invece dell'equivalente MAM. 

# Protezione dei dati di backup 

A partire da Android Marshmallow (API 23), Android offre ora due modi in cui un'app può eseguire il backup dei dati. Queste opzioni sono disponibili per l'uso nell'app e richiedono diversi passaggi per garantire l'applicazione corretta della protezione dati MAM. È possibile esaminare la tabella di seguito per una rapida panoramica delle azioni corrispondenti necessarie per il corretto comportamento di protezione dati.  Altre informazioni sul backup di Android sono disponibili nella [guida al backup dei dati per sviluppatori di Android](http://developer.android.com/guide/topics/data/backup.html). 

## Backup completo automatico

A partire da Android M, Android ha iniziato a offrire backup completi automatici per le app indipendentemente dall'API di destinazione in caso di esecuzione in un dispositivo Android M. A condizione che l'attributo `android:allowBackup` non sia false, un'app riceverà backup completi non filtrati dei propri dati. Poiché questo comportamento pone un rischio di perdita dei dati, l'SDK richiede l'applicazione delle modifiche indicate nella tabella seguente per garantire una corretta protezione dati.  È importante seguire le linee guida indicate di seguito per proteggere i dati dei clienti in modo appropriato.  Se si imposta `android:allowBackup=false` , l'app non verrà mai accodata per i backup dal sistema operativo e non saranno necessarie altre azioni per MAM, perché non verrà eseguito alcun backup.
 
 ## Backup di "chiave/valore"

Questa opzione è disponibile per tutte le API e usa `BackupAgent` e `BackupAgentHelper`. 

### Uso di BackupAgentHelper

`BackupAgentHelper` è molto più semplice dell'implementazione di `BackupAgent` sia per le funzionalità di Android native sia per l'integrazione MAM. `BackupAgentHelper` consente allo sviluppatore di registrare interi file e preferenze condivise rispettivamente in un oggetto `FileBackupHelper` o `SharedPreferencesBackupHelper`, che viene quindi aggiunto a `BackupAgentHelper` durante la creazione. 

### Uso di BackupAgent

`BackupAgent` consente di definire in modo molto più esplicito i dati di cui eseguire il backup. Tuttavia, questa opzione implica che non sarà possibile trarre vantaggio dal framework di backup di Android.  Dato che lo sviluppatore è responsabile dell'implementazione, sono necessari altri passaggi per garantire una protezione dati tramite MAM appropriata. Il maggior carico di lavoro ricade sullo sviluppatore e questo fa sì che l'integrazione di MAM sia leggermente più coinvolta. 

#### L'app non ha un agente di backup
  
Queste sono le opzioni per lo sviluppatore quando `Android:allowbBackup =true`:

##### Backup completo in base a un file di configurazione: 

Specificare una risorsa all'interno del tag dei metadati `com.microsoft.intune.mam.FullBackupContent` nel manifesto. Ad esempio:
    `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />`

Aggiungere questo attributo nel tag `<application>` : `android:fullBackupContent="@xml/my_scheme"`, dove `my_scheme` è una risorsa XML nell'app. 

##### Backup completo senza esclusioni 

Specificare un tag nel manifesto, ad esempio `<meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />` 
 
Aggiungere questo attributo nel tag `<application>`: `android:fullBackupContent="true"`.

#### L'app ha un agente di backup

Seguire le indicazioni nelle sezioni `BackupAgent` e `BackupAgentHelper` in base a quanto indicato sopra. 

Valutare se passare a usare `MAMDefaultFullBackupAgent`, che offre un semplice backup su Android M. 

### Prima del backup

Prima di avviare il backup, è necessario verificare che i file o i buffer di dati di cui si prevede di eseguire il backup siano davvero abilitati per il backup. È disponibile una funzione `isBackupAllowed` in `MAMFileProtectionManager` e `MAMDataProtectionManager` per eseguire questa verifica. Se il file o il buffer di dati non è abilitato per il backup, non è possibile continuare a utilizzarlo nel backup.

Se a un certo punto durante il backup si vuole che venga eseguito il backup delle identità per i file verificati nel passaggio 1, è necessario chiamare `backupMAMFileIdentity(BackupDataOutput data, File … files)` con i file da cui si prevede di estrarre dati. In questo modo, verranno automaticamente create entità di backup, che verranno scritte in `BackupDataOutput` . Queste entità verranno utilizzate automaticamente al momento del ripristino. 

## Configurare Azure Directory Authentication Library (ADAL)  

L'SDK si basa su ADAL per gli scenari di autenticazione e avvio condizionale, per cui è necessario che per le app siano state eseguite alcune attività di configurazione di Azure Active Directory. I valori di configurazione vengono comunicati all'SDK tramite i metadati `AndroidManifest` . Per configurare l'app e abilitare l'autenticazione appropriata, aggiungere il codice seguente al nodo dell'app in `AndroidManifest`. Alcune di queste configurazioni sono necessarie solo se l'app usa ADAL per l'autenticazione in generale. In questo caso, saranno necessari i valori specifici usati dall'app per registrare se stessa con Azure AD. Questo avviene per evitare che all'utente finale venga chiesta l'autenticazione due volte, a causa del fatto che Azure AD riconosce due valori di registrazione separati, uno dall'app e uno dall'SDK. 

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

### Configurazioni comuni di ADAL 

Di seguito sono indicate le configurazioni comuni per i valori descritti sopra. 

#### ADAL non è integrato nell'app

* L'autorità deve essere impostata sull'ambiente desiderato in cui sono stati configurati gli account Azure AD.

* SkipBroker deve essere impostato su true.

#### ADAL è integrato nell'app

* L'autorità deve essere impostata sull'ambiente desiderato in cui sono stati configurati gli account Azure AD.

* L'ID client deve essere impostato sull'ID client dell'app.

* `NonBrokerRedirectURI` deve essere impostato su un URI di reindirizzamento valido per l'app.
    * Oppure `urn:ietf:wg:oauth:2.0:oob` deve essere configurato come URI di reindirizzamento valido di Azure AD.

* SkipBroker deve essere impostato su false (o essere assente).

* Azure AD deve essere configurato in modo da accettare l'URI di reindirizzamento del broker.

#### ADAL è integrato nell'app, ma l'app non supporta l'app Azure AD Authenticator.

* L'autorità deve essere impostata sull'ambiente desiderato in cui sono stati configurati gli account Azure AD.

* L'ID client deve essere impostato sull'ID client dell'app.

* `NonBrokerRedirectURI` deve essere impostato su un URI di reindirizzamento valido per l'app.

    * Oppure `urn:ietf:wg:oauth:2.0:oob` deve essere configurato come URI di reindirizzamento valido di Azure AD.

## Come abilitare la registrazione nell'SDK 

La registrazione viene eseguita tramite il framework `java.util.logging` . Per ricevere i log, configurare la registrazione globale come descritto nella [guida tecnica di Java](http://docs.oracle.com/javase/6/docs/technotes/guides/logging/overview.html). A seconda dell'app, `App.onCreate` è in genere il punto migliore in cui avviare la registrazione. I messaggi dei registri vengono codificati in base al nome di classe, che potrebbe essere offuscato.

# Limitazioni note della piattaforma 

## Limitazioni relative alle dimensioni dei file 

In Android le limitazioni del formato di file eseguibile Dalvik possono diventare un problema per codebase di grandi dimensioni eseguite senza ProGuard. Nello specifico, possono esistere le limitazioni seguenti: 

* Limite a 65.000 per i campi.

* Limite a 65.000 per i metodi.

Quando si includono molti progetti, ogni elemento android:package ottiene una copia di R, che aumenta notevolmente il numero di campi man mano che vengono aggiunte librerie. Le indicazioni seguenti possono aiutare a ridurre questo limite:
 
* Tutti i progetti di libreria devono condividere lo stesso elemento android:package ogni volta che è possibile. Questo comportamento non genera occasionalmente errori nel campo, perché si tratta puramente di un problema in fase di compilazione.   Inoltre, le nuove versioni di Android SDK pre-elaborano i file DEX per rimuovere parte della ridondanza. In questo modo, la distanza dai campi viene ulteriormente ridotta.

* Usare gli strumenti di compilazione di Android SDK più recenti disponibili.

* Rimuovere tutte le librerie non necessarie e inutilizzate, ad esempio `android.support.v4`.

## Limitazioni relative all'applicazione di criteri

**Acquisizione schermo**: l'SDK non è in grado di applicare un nuovo valore dell'impostazione di acquisizione schermo nelle attività passate attraverso Activity.onCreate. Questo limite può provocare un periodo di tempo in cui l'app è stata configurata per la disabilitazione degli screenshot, ma è comunque possibile acquisire screenshot.

**Uso di resolver di contenuto*: i criteri di trasferimento o di ricezione possono bloccare interamente o parzialmente l'uso di un resolver di contenuto per accedere al provider di contenuti in un'altra app. Questo comportamento può far sì che i metodi ContentResolver restituiscano null o generino un valore di errore. Ad esempio, `openOutputStream` genera `FileNotFoundException` se è bloccato. L'app può determinare se un errore di scrittura dei dati tramite un resolver di contenuto è stato provocato dai criteri (o verrebbe provocato dai criteri) effettuando questa chiamata:

    MAMComponents.get(AppPolicy.class).getIsSaveToLocationAllowed(contentURI)

**Servizi esportati**: il file `AndroidManifest.xml` incluso in Intune App SDK contiene `MAMNotificationReceiverService`, che deve essere un servizio esportato per consentire all'app Portale aziendale di inviare notifiche a un'app abilitata. Il servizio verifica il chiamante per garantire che l'invio di notifiche sia consentito solo all'app Portale aziendale. 

# Procedure consigliate per Android 

Intune SDK mantiene il contratto fornito dall'API Android, ma è possibile che vengano generate condizioni di errore più frequentemente come conseguenza dell'applicazione dei criteri. Queste procedure consigliate per Android riducono la probabilità di errore: 

* Le funzioni di Android SDK che possono restituire null hanno una maggiore probabilità di essere già null.  Per ridurre al minimo i problemi, assicurarsi che i controlli dei valori null vengano eseguiti nei punti corretti.

* Le funzionalità che possono essere verificate devono essere verificate tramite le rispettive API dell'SDK.

* Tutte le funzioni derivate devono effettuare chiamate tramite le rispettive versioni delle superclassi.

* Evitare un uso ambiguo di qualsiasi API. Ad esempio, `Activity.startActivityForResult/onActivityResult` senza il controllo di requestCode provocherà un comportamento anomalo.



<!--HONumber=Jul16_HO3-->


