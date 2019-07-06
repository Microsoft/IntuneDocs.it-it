---
title: Guida a Microsoft Intune App SDK per sviluppatori di Android
description: Microsoft Intune App SDK per Android permette di integrare le funzionalità di gestione delle app mobili (MAM, Mobile App Management) di Intune nell'app Android.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 0100e1b5-5edd-4541-95f1-aec301fb96af
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4530c1ec573560924b54aa8fd21d39a86cefe97e
ms.sourcegitcommit: cb4e71cd48311ea693001979ee59f621237a6e6f
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2019
ms.locfileid: "67558433"
---
# <a name="microsoft-intune-app-sdk-for-android-developer-guide"></a>Guida a Microsoft Intune App SDK per sviluppatori di Android

> [!NOTE]
> Si consiglia di leggere prima [Panoramica di Intune App SDK](app-sdk.md), che illustra le attuali funzionalità dell'SDK e descrive come preparare l'integrazione in ogni piattaforma supportata.

Microsoft Intune App SDK per Android consente di integrare i criteri di protezione delle app di Intune, noti anche come criteri **APP** o MAM, nell'app Android nativa. Un'applicazione gestita da Intune è integrata con Intune App SDK. Gli amministratori di Intune possono distribuire facilmente i criteri di protezione delle app nell'app gestita da Intune quando Intune gestisce attivamente l'app.


## <a name="whats-in-the-sdk"></a>Contenuto dell'SDK

Intune App SDK è costituito dai file seguenti:

* **Microsoft.Intune.MAM.SDK.aar**: componenti dell'SDK, a eccezione dei file JAR della libreria di supporto.
* **Microsoft.Intune.MAM.SDK.Support.v4.jar**: classi necessarie per abilitare MAM nelle app che usano la libreria di supporto Android v4.
* **Microsoft.Intune.MAM.SDK.Support.v7.jar**: classi necessarie per abilitare MAM nelle app che usano la libreria di supporto Android v7.
* **Microsoft.Intune.MAM.SDK.Support.v17.jar**: classi necessarie per abilitare MAM nelle app che usano la libreria di supporto Android v17. 
* **Microsoft.Intune.MAM.SDK.Support.Text.jar**: classi necessarie per abilitare MAM nelle app che usano le classi della libreria di supporto Android nel pacchetto `android.support.text`.
* **Microsoft.Intune.MDM.SDK.DownlevelStubs.jar**: questo file con estensione jar contiene gli stub per le classi di sistema Android presenti solo nei dispositivi più recenti ma a cui viene fatto riferimento dai metodi in MAMActivity. I dispositivi più recenti ignorano queste classi stub. Il file con estensione jar è necessario solo se l'app esegue la reflection sulle classi che derivano da MAMActivity e nella maggior parte delle app non è necessario. Se si usa il file con estensione jar, fare attenzione a escludere tutte le classi di ProGuard. Tutte le classi si trovano nel pacchetto radice "android"
* **com.microsoft.intune.mam.build.jar**: plugin di Gradle [utile per l'integrazione dell'SDK](#build-tooling).
* **CHANGELOG.txt**: fornisce un record delle modifiche apportate in ogni versione dell'SDK.
* **THIRDPARTYNOTICES.TXT**: comunicazione di attribuzione che riconosce la presenza di codice OSS e/o di terze parti che verrà compilato nell'app.

## <a name="requirements"></a>Requisiti

### <a name="android-versions"></a>Versioni di Android
L'SDK supporta le API da Android 19 (Android 4.4+) ad Android 28 (Android 9.0).

### <a name="company-portal-app"></a>App Portale aziendale
Intune App SDK per Android richiede la presenza dell'app [Portale aziendale](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) nel dispositivo per abilitare i criteri di protezione delle app. Il Portale aziendale recupera i criteri di protezione delle app dal servizio Intune. Al momento dell'inizializzazione, l'app carica i criteri e il codice per applicare i criteri dal Portale aziendale.

> [!NOTE]
> Quando l'app Portale aziendale non è presente nel dispositivo, un'app gestita da Intune si comporta analogamente a una normale app che non supporta i criteri di protezione delle app di Intune.

Per la protezione delle app senza registrazione del dispositivo, _**non**_ è richiesta la registrazione del dispositivo con l'app Portale aziendale.

## <a name="sdk-integration"></a>Integrazione dell'SDK

### <a name="sample-app"></a>App di esempio
Un esempio di come gestire correttamente l'integrazione con Intune App SDK è disponibile in [GitHub](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App). Questo esempio usa il [plug-in di compilazione Gradle](#gradle-build-plugin).

### <a name="referencing-intune-app-libraries"></a>Librerie dell'app di Intune di riferimento

Intune App SDK è una libreria Android standard senza dipendenze esterne. **Microsoft.Intune.MAM.SDK.aar** contiene entrambe le interfacce necessarie per l'abilitazione dei criteri di protezione di un'app e il codice necessario per interagire con l'app Portale aziendale di Microsoft Intune.

**Microsoft.Intune.MAM.SDK.aar** deve essere specificata come un riferimento alla libreria Android. A tale scopo, aprire il progetto di app in Android Studio, passare a **File > New > New module** (File > Nuovo > Nuovo modulo) e selezionare **Import .JAR/.AAR Package** (Importa pacchetto JAR/AAR). Quindi, selezionare il pacchetto di archiviazione Android Microsoft.Intune.MAM.SDK.aar per creare un modulo per il nostro AAR. Fare clic con il pulsante destro del mouse sul modulo o sui moduli contenenti il codice dell'app e passare a **Impostazioni modulo** > **scheda Dipendenze** >  **+ fare clic sull'icona**  > **Dipendenza modulo** > Selezionare il modulo AAR SDK MAM appena creato > **OK**. Ciò garantisce che il modulo venga compilato con l'SDK MAM quando si compila il progetto.

Le librerie **Microsoft.Intune.MAM.SDK.Support.XXX.jar** contengono anche le varianti di Intune delle librerie `android.support.XXX` corrispondenti. Questi file sono integrati in Microsoft.Intune.MAM.SDK.aar nel caso in cui non sia necessario che un'app dipenda dalle librerie di supporto.

#### <a name="proguard"></a>ProGuard

Se [ProGuard](http://proguard.sourceforge.net/) (o un altro meccanismo di compattazione/offuscamento) viene usato come passaggio di compilazione, l'SDK ha regole di configurazione aggiuntive che devono essere incluse. Quando si include il file AAR nella compilazione, le regole vengono integrate automaticamente nel passaggio ProGuard e i file di classe necessari vengono mantenuti.

Le librerie ADAL (Azure Active Directory Authentication Library) possono avere le proprie restrizioni per ProGuard. Se l'app integra ADAL, è necessario seguire la documentazione di ADAL in merito a tali restrizioni.

### <a name="build-tooling"></a>Strumenti di compilazione
Intune App SDK è una libreria di Android che consente all'app di supportare e partecipare all'imposizione dei criteri di Intune. Alcuni criteri richiedono l'[imposizione della partecipazione esplicita dall'app](#enable-features-that-require-app-participation), ma la maggior parte viene imposta in modo semiautomatico. Questa imposizione automatica richiede che le app sostituiscano l'ereditarietà da diverse classi base di Android con l'ereditarietà dagli equivalenti MAM e che allo stesso modo sostituiscano le chiamate a determinate classi di servizio di sistema Android con le chiamate agli equivalenti MAM. Le sostituzioni specifiche necessarie vengono illustrate in dettaglio [più avanti](#class-and-method-replacements).

L'esecuzione manuale di queste sostituzioni può essere un processo laborioso. Al contrario, l'SDK fornisce strumenti di compilazione (un plug-in per le compilazioni Gradle e uno strumento da riga di comando per le compilazioni non Gradle) che eseguono automaticamente le sostituzioni. Questi strumenti trasformano i file di classe generati dalla compilazione Java e non modificano il codice sorgente originale.

Gli strumenti eseguono solo [sostituzioni dirette](#class-and-method-replacements). Non eseguono integrazioni SDK più complesse, ad esempio [criteri di salvataggio con nome](#enable-features-that-require-app-participation), [identità multiple](#multi-identity-optional), [registrazione App-WE](#app-protection-policy-without-device-enrollment), [modifiche di AndroidManifest](#manifest-replacements) o [configurazione ADAL](#configure-azure-active-directory-authentication-library-adal), che devono quindi essere completate prima che l'app venga completamente abilitata per Intune. Esaminare con attenzione la parte restante della documentazione per conoscere i punti di integrazione pertinenti all'app.

> [!NOTE]
> È possibile eseguire gli strumenti su un progetto che ha già eseguito l'integrazione di origine completa o parziale di MAM SDK tramite sostituzioni manuali. Il progetto deve comunque elencare MAM SDK come dipendenza.

### <a name="gradle-build-plugin"></a>Plug-in di compilazione Gradle
Se l'app non viene compilata con Gradle, passare a [Integrazione con lo strumento da riga di comando](#command-line-build-tool). 

Il plug-in SDK dell'app viene distribuito come parte dell'SDK come **GradlePlugin/com.microsoft.intune.mam.build.jar**. Per consentire a Gradle di trovare il plug-in, è necessario aggiungerlo all'elemento classpath di buildscript. Il plug-in dipende da [Javassist](https://jboss-javassist.github.io/javassist/), da aggiungere anch'esso. Per aggiungerli a classpath, aggiungere il codice seguente all'elemento `build.gradle` radice

```groovy
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath "org.javassist:javassist:3.22.0-GA"
        classpath files("$PATH_TO_MAM_SDK/GradlePlugin/com.microsoft.intune.mam.build.jar")
    }
}
```

È quindi sufficiente aggiungere nel file `build.gradle` del progetto APK il plug-in come
```groovy
apply plugin: 'com.microsoft.intune.mam'
```

Per impostazione predefinita, il plug-in opererà **solo** sulle dipendenze di `project`.
La compilazione di test non è interessata. Può essere fornita la configurazione per elencare
* Progetti da escludere.
* [Dipendenze esterne da includere](#usage-of-includeexternallibraries). 
* Classi specifiche da escludere dall'elaborazione.
* Varianti da escludere dall'elaborazione, che possono fare riferimento a un nome di variante completo o a una versione singola. Ad esempio
     * se l'app ha i tipi di compilazione `debug` e `release` con le versioni {`savory`, `sweet`} e {`vanilla`, `chocolate`} è possibile specificare
     * `savory` per escludere tutte le varianti con la versione savory o `savoryVanillaRelease` per escludere solo la variante esatta.

#### <a name="example-partial-buildgradle"></a>Esempio build.gradle parziale

```groovy

apply plugin: 'com.microsoft.intune.mam'

dependencies {
    implementation project(':product:FooLib')
    implementation project(':product:foo-project')
    implementation fileTree(dir: "libs", include: ["bar.jar"])
    implementation fileTree(dir: "libs", include: ["zap.jar"])
    implementation "com.contoso.foo:zap-artifact:1.0.0"
    implementation "com.microsoft.bar:baz:1.0.0"

    // Include the MAM SDK
    implementation files("$PATH_TO_MAM_SDK/Microsoft.Intune.MAM.SDK.aar")
}
intunemam {
    excludeProjects = [':product:FooLib']
    includeExternalLibraries = ['bar.jar', "com.contoso.foo:zap-artifact", "com.microsoft.*", "!com.microsoft.qux*"]
    excludeClasses = ['com.contoso.SplashActivity']
    excludeVariants=['savory']
}

```
Questo codice avrebbe gli effetti seguenti:
* `:product:FooLib` non viene riscritto perché è incluso in `excludeProjects`
* `:product:foo-project` viene riscritto, tranne `com.contoso.SplashActivity` che viene ignorato perché non è in `excludeClasses`
* `bar.jar` viene riscritto perché è incluso in `includeExternalLibraries`
* `zap.jar` **non** viene riscritto perché non è un progetto e non è incluso in `includeExternalLibraries`
* `com.contoso.foo:zap-artifact:1.0.0` viene riscritto perché è incluso in `includeExternalLibraries`
* `com.microsoft.bar:baz:1.0.0` viene riscritto perché è incluso in `includeExternalLibraries` tramite un carattere jolly (`com.microsoft.*`).
* `com.microsoft.qux:foo:2.0` non viene riscritto anche se corrisponde allo stesso carattere jolly dell'elemento precedente perché viene escluso in modo esplicito tramite un modello di negazione.

#### <a name="usage-of-includeexternallibraries"></a>Utilizzo di includeExternalLibraries

Poiché il plug-in opera solo sulle dipendenze dei progetti (in genere fornite dalla funzione `project()`) per impostazione predefinita, le dipendenze specificate da `fileTree(...)` o ottenute da maven o ad altre origini di pacchetto (ad esempio, "`com.contoso.bar:baz:1.2.0`") devono essere fornite alla proprietà `includeExternalLibraries` se è necessario elaborarle con MAM in base ai criteri illustrati sotto. I caratteri jolly ("*") sono supportati. Un elemento che inizia con `!` è una negazione e può essere usato per escludere le raccolte che verrebbero altrimenti incluse da un carattere jolly.

Quando si specificano dipendenze esterne con la notazione dell'elemento, è consigliabile omettere il componente della versione nel valore `includeExternalLibraries`. Se si include la versione, deve essere quella esatta. Non è possibile specificare versioni dinamiche (ad esempio, `1.+`).

La regola generale da seguire per determinare se è necessario includere librerie in `includeExternalLibraries` si basa su due domande:
1. La libreria contiene classi di cui esistono equivalenti MAM? Esempi: `Activity`, `Fragment`, `ContentProvider`, `Service` e così via.
2. In caso affermativo, l'app usa tali classi?

Se la risposta a entrambe le domande è "sì", è necessario includere tale libreria in `includeExternalLibraries`. 

| Scenario | Da includere |
|--|--|
| Si include una libreria di visualizzatore PDF nell'app e si usa l'elemento `Activity` del visualizzatore nell'applicazione quando gli utenti provano a visualizzare documenti PDF | Sì |
| Si include una libreria HTTP nell'app per migliorare le prestazioni Web | No |
| Si include una libreria come React Native contenente classi derivate da `Activity`, `Application` e `Fragment` e si usano o si derivano ulteriormente tali classi nell'app | Sì |
| Si include una libreria come React Native contenente classi derivate da `Activity`, `Application` e `Fragment`, ma si usano solo helper statici o classi di utilità | No |
| Si include una libreria contenente classi di visualizzazione derivate da `TextView` e si usano o si derivano ulteriormente tali classi nell'app | Sì |

#### <a name="reporting"></a>Reporting
Il plug-in di compilazione può generare un report HTML delle modifiche apportate. Per richiedere la generazione di questo report, specificare `report = true` nel blocco di configurazione `intunemam`. Se generato, il report verrà scritto in `outputs/logs` nella directory di compilazione.

```groovy
intunemam {
    report = true
}
```

#### <a name="dependencies"></a>Dipendenze

Il plug-in Gradle ha una dipendenza da [Javassist](https://jboss-javassist.github.io/javassist/), che deve essere disponibile per la risoluzione delle dipendenze di Gradle (come descritto sopra). Javassist viene usato esclusivamente in fase di compilazione quando si esegue il plug-in. Nessun codice Javassist verrà aggiunto all'app.

> [!NOTE] 
> È necessario usare la versione 3.0 o successiva del plug-in Android Gradle e Gradle 4.1 o versione successiva.

### <a name="command-line-build-tool"></a>Strumento di compilazione da riga di comando
Se la compilazione usa Gradle, passare alla [sezione successiva](#class-and-method-replacements).

Lo strumento di compilazione da riga di comando è disponibile nella cartella `BuildTool` del rilascio dell'SDK. Esegue la stessa funzione del plug-in Gradle illustrato in dettaglio in precedenza, ma può essere integrato in sistemi di compilazione personalizzati o non Gradle. Essendo più generico, è più complesso da richiamare, quindi il plug-in Gradle dovrebbe essere usato solo quando è possibile.

#### <a name="using-the-command-line-tool"></a>Uso dello strumento da riga di comando

Lo strumento da riga di comando può essere richiamato usando gli script helper forniti, disponibili nella directory `BuildTool\bin`.

Lo strumento prevede i parametri seguenti.

| Parametro | Descrizione |
| -- | -- |
| `--input` | Elenco di file con estensione jar e di directory di file di classe da modificare separati da punti e virgola. Deve includere tutti i file con estensione jar e le directory che si prevede di riscrivere. |
| `--output` | Elenco di file con estensione jar e di directory in cui archiviare le classi modificate separati da punti e virgola. Deve esistere una voce di output per ogni voce di input e tali voci devono essere elencate in ordine. |
| `--classpath` | Percorso delle classi di compilazione. Può contenere sia file con estensione jar che directory di classi. |
| `--excludeClasses`| Elenco contenente i nomi delle classi da escludere dalla riscrittura separati da punti e virgola. |

Tutti i parametri sono obbligatori tranne `--excludeClasses` che è facoltativo.

> [!NOTE] 
> Nei sistemi Unix il punto e virgola è un separatore di comandi. Per evitare che la shell divida i comandi, assicurarsi di eseguire l'escape di ogni punto e virgola con '\' o di racchiudere il parametro completo tra virgolette.

#### <a name="example-command-line-tool-invocation"></a>Chiamata allo strumento da riga di comando di esempio

``` batch
> BuildTool\bin\BuildTool.bat --input build\product-foo-project;libs\bar.jar --output mam-build\product-foo-project;mam-build\libs\bar.jar --classpath build\zap.jar;libs\Microsoft.Intune.MAM.SDK\classes.jar;%ANDROID_SDK_ROOT%\platforms\android-27\android.jar --excludeClasses com.contoso.SplashActivity
```

Questo codice avrebbe gli effetti seguenti:

* la directory `product-foo-project` viene riscritta come `mam-build\product-foo-project`
* `bar.jar` viene riscritto come `mam-build\libs\bar.jar`
* `zap.jar` **non** viene riscritto perché è elencato solo in `--classpath`
* La classe `com.contoso.SplashActivity` **non** viene riscritta anche se è in `--input`

> [!NOTE] 
> Lo strumento di compilazione non supporta attualmente i file AAR. Se il sistema di compilazione non estrae già `classes.jar` quando gestisce i file AAR, sarà necessario eseguire questa operazione prima di richiamare lo strumento di compilazione.


## <a name="class-and-method-replacements"></a>Sostituzione di classi e metodi

Le classi base di Android devono essere sostituite con il rispettivo equivalente MAM per abilitare la gestione di Intune. Le classi dell'SDK si trovano tra la classe base per Android e la versione derivata dell'app di tale classe. Un'attività dell'app, ad esempio, potrebbe terminare con una gerarchia di ereditarietà con un aspetto simile a questa: `Activity` > `MAMActivity` >
`AppSpecificActivity`. Il livello MAM filtra le chiamate alle operazioni di sistema per offrire all'app una visualizzazione trasparente gestita dell'ambiente.

Oltre alle classi base, anche alcune classi che l'app potrebbe usare senza derivazione (ad esempio, `MediaPlayer`) hanno equivalenti MAM obbligatori e [devono essere sostituite anche le chiamate ad alcuni metodi](#wrapped-system-services). I dettagli esatti sono indicati di seguito.

Tutte le sostituzioni illustrate in dettaglio in questa sezione possono essere eseguite automaticamente dagli [strumenti di compilazione](#build-tooling) dell'SDK. 



| Classe base Android | Sostituzione di Intune App SDK |
|--|--|
| android.app.Activity | MAMActivity |
| android.app.ActivityGroup | MAMActivityGroup |
| android.app.AliasActivity | MAMAliasActivity |
| android.app.Application | MAMApplication |
| android.app.Dialog | MAMDialog |
| android.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.app.DialogFragment | MAMDialogFragment |
| android.app.ExpandableListActivity | MAMExpandableListActivity |
| android.app.Fragment | MAMFragment |
| android.app.IntentService | MAMIntentService |
| android.app.LauncherActivity | MAMLauncherActivity |
| android.app.ListActivity | MAMListActivity |
| android.app.ListFragment | MAMListFragment |
| android.app.NativeActivity | MAMNativeActivity |
| android.app.PendingIntent | MAMPendingIntent (vedere [PendingIntent](#pendingintent)) |
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
| android.media.MediaPlayer | MAMMediaPlayer |
| android.media.MediaMetadataRetriever | MAMMediaMetadataRetriever |
| android.provider.DocumentsProvider | MAMDocumentsProvider |
| android.preference.PreferenceActivity | MAMPreferenceActivity |
| android.support.multidex.MultiDexApplication | MAMMultiDexApplication |
| android.widget.TextView | MAMTextView |
| android.widget.AutoCompleteTextView | MAMAutoCompleteTextView |
| android.widget.CheckedTextView | MAMCheckedTextView |
| android.widget.EditText | MAMEditText |
| android.inputmethodservice.ExtractEditText | MAMExtractEditText |
| android.widget.MultiAutoCompleteTextView | MAMMultiAutoCompleteTextView |

> [!NOTE]
> Anche se l'applicazione non richiede una classe `Application` derivata specifica, [vedere `MAMApplication` di seguito](#mamapplication)

### <a name="microsoftintunemamsdksupportv4jar"></a>Microsoft.Intune.MAM.SDK.Support.v4.jar:

| Classe Android | Sostituzione di Intune App SDK |
|--|--|
| android.support.v4.app.DialogFragment | MAMDialogFragment
| android.support.v4.app.FragmentActivity | MAMFragmentActivity
| android.support.v4.app.Fragment | MAMFragment
| android.support.v4.app.JobIntentService | MAMJobIntentService
| android.support.v4.app.TaskStackBuilder | MAMTaskStackBuilder
| android.support.v4.content.FileProvider | MAMFileProvider
| android.support.v4.content.WakefulBroadcastReceiver | MAMWakefulBroadcastReceiver

### <a name="microsoftintunemamsdksupportv7jar"></a>Microsoft.Intune.MAM.SDK.Support.v7.jar:

|Classe Android | Sostituzione di Intune App SDK |
|--|--|
| android.support.v7.app.AlertDialog.Builder | MAMAlertDialogBuilder |
| android.support.v7.app.AppCompatActivity | MAMAppCompatActivity |
| android.support.v7.widget.AppCompatAutoCompleteTextView | MAMAppCompatAutoCompleteTextView |
| android.support.v7.widget.AppCompatCheckedTextView | MAMAppCompatCheckedTextView |
| android.support.v7.widget.AppCompatEditText | MAMAppCompatEditText |
| android.support.v7.widget.AppCompatMultiAutoCompleteTextView | MAMAppCompatMultiAutoCompleteTextView |
| android.support.v7.widget.AppCompatTextView | MAMAppCompatTextView |

### <a name="microsoftintunemamsdksupportv17jar"></a>Microsoft.Intune.MAM.SDK.Support.v17.jar:
|Classe Android | Sostituzione di Intune App SDK |
|--|--|
| android.support.v17.leanback.widget.SearchEditText | MAMSearchEditText |

### <a name="microsoftintunemamsdksupporttextjar"></a>Microsoft.Intune.MAM.SDK.Support.Text.jar:
|Classe Android | Sostituzione di Intune App SDK |
|--|--|
| android.support.text.emoji.widget.EmojiAppCompatEditText | MAMEmojiAppCompatEditText |
| android.support.text.emoji.widget.EmojiAppCompatTextView | MAMEmojiAppCompatTextView |
| android.support.text.emoji.widget.EmojiEditText | MAMEmojiEditText |
| android.support.text.emoji.widget.EmojiTextView | MAMEmojiTextView |

### <a name="renamed-methods"></a>Metodi rinominati
In molti casi, un metodo disponibile nella classe Android è stato contrassegnato come finale nella classe sostitutiva MAM. In questo caso, la classe sostitutiva MAM fornisce un metodo denominato in modo analogo (in genere con suffisso `MAM`), che deve essere sostituito al suo posto. Ad esempio, quando si deriva da `MAMActivity`, invece di sostituire `onCreate()` e chiamare `super.onCreate()`, la classe `Activity` deve sostituire `onMAMCreate()` e chiamare `super.onMAMCreate()`. Il compilatore Java deve applicare le restrizioni finali per impedire la sostituzione accidentale del metodo originale invece dell'equivalente MAM.

### <a name="mamapplication"></a>MAMApplication
Se l'app crea una sottoclasse di `android.app.Application`, al suo posto è **necessario** creare una sottoclasse di `com.microsoft.intune.mam.client.app.MAMApplication`. Se l'app non crea una sottoclasse di `android.app.Application`, è **necessario** impostare `"com.microsoft.intune.mam.client.app.MAMApplication"` come attributo `"android:name"` nel tag `<application>` di AndroidManifest.xml.

### <a name="pendingintent"></a>PendingIntent
Invece di `PendingIntent.get*`, è necessario usare il metodo `MAMPendingIntent.get*`. Successivamente, è possibile usare la classe `PendingIntent` risultante come di consueto.

### <a name="wrapped-system-services"></a>Servizi di sistema con wrapping
Per alcune classi di servizi di sistema, è necessario chiamare un metodo statico su una classe wrapper MAM invece di richiamare direttamente il metodo desiderato sull'istanza del servizio. Una chiamata a `getSystemService(ClipboardManager.class).getPrimaryClip()`, ad esempio, deve diventare una chiamata a `MAMClipboardManager.getPrimaryClip(getSystemService(ClipboardManager.class)`. È consigliabile non eseguire manualmente queste sostituzioni. Usare invece BuildPlugin.

| Classe Android | Sostituzione di Intune App SDK |
|--|--|
| android.content.ClipboardManager | MAMClipboard |
| android.content.ContentProviderClient | MAMContentProviderClientManagement |
| android.content.ContentResolver | MAMContentResolverManagement |
| android.content.pm.PackageManager | MAMPackageManagement |
| android.app.DownloadManager | MAMDownloadManagement |
| android.print.PrintManager | MAMPrintManagement |
| android.support.v4.print.PrintHelper | MAMPrintHelperManagement |
| android.view.View | MAMViewManagement |
| android.view.DragEvent | MAMDragEventManagement |

Per alcune classi la maggior parte dei metodi è sottoposta a wrapping, ad esempio `ClipboardManager`, `ContentProviderClient`, `ContentResolver` e `PackageManager`, mentre in altre classi il wrapping viene eseguito solo per uno o due metodi, ad esempio `DownloadManager`, `PrintManager`, `PrintHelper`, `View` e `DragEvent`. Consultare le API esposte dalle classi equivalenti MAM per individuare il metodo esatto se non si usa BuildPlugin. 

### <a name="manifest-replacements"></a>Sostituzioni per il manifesto
Potrebbe essere necessario eseguire alcune delle sostituzioni di classi indicate in precedenza nel file manifesto e nel codice Java. Importante:
* I riferimenti del manifesto a `android.support.v4.content.FileProvider` devono essere sostituiti con `com.microsoft.intune.mam.client.support.v4.content.MAMFileProvider`.

## <a name="androidx-libraries"></a>Librerie AndroidX
Con Android P, Google ha annunciato un set nuovo (ridenominato) di librerie di supporto chiamato AndroidX e la versione 28 è l'ultima versione principale delle librerie android.support esistenti.

A differenza delle librerie di supporto per Android, non sono previste varianti MAM delle librerie AndroidX. Al contrario, AndroidX deve essere trattato come qualsiasi altra libreria esterna e deve essere configurato per essere riscritto dallo strumento o dal plug-in di compilazione. Per le compilazioni Gradle, è possibile eseguire questa operazione includendo `androidx.*` nel campo `includeExternalLibraries` della configurazione del plug-in. Le chiamate dello strumento da riga di comando devono elencare tutti i file con estensione jar in modo esplicito.
## <a name="sdk-permissions"></a>Autorizzazioni dell'SDK

Intune App SDK richiede tre [autorizzazioni di sistema Android](https://developer.android.com/guide/topics/security/permissions.html) per le app che lo integrano:

* `android.permission.GET_ACCOUNTS` (richiesta in fase di esecuzione se necessario)

* `android.permission.MANAGE_ACCOUNTS`

* `android.permission.USE_CREDENTIALS`

La libreria [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) (Azure Active Directory Authentication Library) richiede queste autorizzazioni per eseguire l'autenticazione negoziata. Se queste autorizzazioni non vengono concesse all'app o vengono revocate dall'utente, verranno disabilitati i flussi di autenticazione che richiedono il broker (l'app Portale aziendale).

## <a name="logging"></a>Registrazione

La registrazione deve essere inizializzata presto per ottenere il massimo valore dai dati registrati. `Application.onMAMCreate()` rappresenta in genere la posizione migliore per inizializzare la registrazione.

Per ricevere i log MAM nell'app, creare un [gestore Java](https://docs.oracle.com/javase/7/docs/api/java/util/logging/Handler.html) e aggiungerlo a `MAMLogHandlerWrapper`. Ciò consentirà di richiamare `publish()` sul gestore dell'applicazione per ogni messaggio di log.

```java
/**
 * Global log handler that enables fine grained PII filtering within MAM logs.  
 *
 * To start using this you should build your own log handler and add it via
 * MAMComponents.get(MAMLogHandlerWrapper.class).addHandler(myHandler, false);  
 *
 * You may also remove the handler entirely via
 * MAMComponents.get(MAMLogHandlerWrapper.class).removeHandler(myHandler);
 */
public interface MAMLogHandlerWrapper {
    /**
     * Add a handler, PII can be toggled.
     *
     * @param handler handler to add.
     * @param wantsPII if PII is desired in the logs.    
     */
    void addHandler(final Handler handler, final boolean wantsPII);

    /**
     * Remove a handler.
     *
     * @param handler handler to remove.
     */
    void removeHandler(final Handler handler);
}
```



## <a name="enable-features-that-require-app-participation"></a>Abilitare le funzionalità che richiedono la partecipazione dell'app

Alcuni criteri di protezione delle app non possono essere implementati direttamente dall'SDK. L'app può controllare il suo comportamento per queste funzionalità usando varie API disponibili nell'interfaccia di `AppPolicy` seguente. Per recuperare un'istanza `AppPolicy`, usare `MAMPolicyManager.getPolicy`.

```java
/**
 * External facing application policies.
 */
public interface AppPolicy {

/**
 * Restrict where an app can save personal data.
 * This function is now deprecated. Please use getIsSaveToLocationAllowed(SaveLocation, String) instead
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
 *           the username/email associated with the cloud service being saved to. Use null if a mapping between
 *           the AAD username and the cloud service username does not exist or the username is not known.
 * @return true if the location can be saved to by the identity, false if otherwise.
 */
boolean getIsSaveToLocationAllowed(SaveLocation service, String username);

/**
 * Checks whether any activities which could handle the given intent are allowed by policy. Returns false only if all
 * activities which could otherwise handle the intent are blocked. If there are no activities which could handle the intent
 * regardless of policy, returns true. If some activities are allowed and others blocked, returns true. Note that it is not
 * necessary to use this method for policy enforcement. If your app attempts to launch an intent for which there are no
 * allowed activities, MAM will display a dialog explaining the situation to the user.
 *
 * @param intent
 *         intent to check
 *
 * @return whether any activities which could handle this intent are allowed.
*/
boolean areIntentActivitiesAllowed(Intent intent);

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
 * This method is intended for diagnostic/telemetry purposes only. It can be used to discover whether
 * file encryption is in use. File encryption is transparent to the app, and the app should not need
 * to make any business logic decisions based on this.
 * 
 * @return True if file encryption is in use.
 */
boolean diagnosticIsFileEncryptionInUse();

/**
 * Return the policy in string format to the app.
 *  
 * @return The string representing the policy.
 */
String toString();

}
```

> [!NOTE]
> `MAMPolicyManager.getPolicy` restituisce sempre criteri per le app diversi da Null, anche se l'app o il dispositivo non è controllato da criteri di gestione di Intune.

### <a name="example-determine-if-pin-is-required-for-the-app"></a>Esempio: determinare se è necessario il PIN per l'app

Se l'app prevede un'esperienza utente specifica per l'uso del PIN, è consigliabile disabilitarla se l'amministratore IT ha configurato l'SDK in modo da chiedere il PIN per l'app. Per determinare se l'amministratore IT ha distribuito i criteri relativi al PIN per l'app per l'utente finale corrente, chiamare il metodo seguente:

```java

MAMPolicyManager.getPolicy(currentActivity).getIsPinRequired();
```

### <a name="example-determine-the-primary-intune-user"></a>Esempio: determinare l'utente primario di Intune

Oltre che dalle API esposte in AppPolicy, il nome dell'entità utente (**UPN**) è esposto anche dall'API `getPrimaryUser()` definita nell'interfaccia `MAMUserInfo`. Per ottenere il nome dell'entità utente, eseguire questa chiamata:

```java
MAMUserInfo info = MAMComponents.get(MAMUserInfo.class);
if (info != null) return info.getPrimaryUser();
```

Di seguito è riportata la definizione completa dell'interfaccia MAMUserInfo:

```java
/**
 * External facing user informations.
 *
 */
public interface MAMUserInfo {
       /**
        * Get the primary user name.
        *
        * @return the primary user name or null if the device is not enrolled.
        */
       String getPrimaryUser();
}
```

### <a name="example-determine-if-saving-to-device-or-cloud-storage-is-permitted"></a>Esempio: determinare se il salvataggio nel dispositivo o in un servizio di archiviazione cloud è consentito

Molte app implementano funzionalità che consentono all'utente finale di salvare file in locale o in un altro servizio di archiviazione cloud. Intune App SDK permette agli amministratori IT di prevenire la perdita dei dati applicando restrizioni di criteri nel modo che ritengono appropriato all'interno dell'organizzazione.  Uno dei criteri che gli amministratori IT possono controllare determina se l'utente finale possa o meno eseguire salvataggi in un archivio dati non gestito "personale". È incluso il salvataggio in un percorso locale, una scheda SD o un servizio di backup di terze parti.

**La partecipazione dell'app è necessaria per l'abilitazione della funzionalità.** Se l'app consente il salvataggio in percorsi personali o nel cloud direttamente dall'app stessa, è necessario implementare questa funzionalità per garantire che l'amministratore IT possa controllare se il salvataggio in una determinata posizione è consentito o meno. L'API seguente consente all'app di stabilire se il salvataggio in un archivio personale è consentito o meno dai criteri correnti dell'amministratore di Intune. L'app può quindi applicare i criteri, in quanto è in grado di determinare che è disponibile un archivio dati personale per l'utente finale attraverso se stessa.  

Per determinare se i criteri vengono applicati, eseguire questa chiamata:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(
SaveLocation service, String username);
```

Per il parametro `service` è necessario impostare uno dei valori `SaveLocation` seguenti:


- `SaveLocation.ONEDRIVE_FOR_BUSINESS`
- `SaveLocation.SHAREPOINT`
- `SaveLocation.LOCAL`
- `SaveLocation.OTHER`

`username` deve essere l'UPN/nome utente/indirizzo di posta elettronica associato al servizio cloud in cui viene salvato (*non* necessariamente lo stesso dell'utente proprietario del documento salvato). Usare Null se non esiste un mapping tra l'UPN di AAD e il nome utente del servizio cloud o se il nome utente non è noto.

Il metodo precedente per determinare se i criteri di un utente consentivano il salvataggio dei dati in diverse posizioni era la presenza di `getIsSaveToPersonalAllowed()` all'interno della stessa classe **AppPolicy**. Questa funzione è ora **deprecata** e non deve essere usata. La chiamata seguente è equivalente a `getIsSaveToPersonalAllowed()`:

```java
MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(SaveLocation.LOCAL, userNameInQuestion);
```

>[!NOTE]
> Usare `SaveLocation.OTHER` se la posizione in questione non è elencata nell'enumerazione **SaveLocations**.


## <a name="register-for-notifications-from-the-sdk"></a>Eseguire la registrazione per le notifiche dall'SDK

### <a name="overview"></a>Panoramica
Intune App SDK consente all'app di controllare il comportamento di determinati criteri, come una cancellazione selettiva, quando vengono distribuiti dall'amministratore IT. Quando un amministratore IT distribuisce criteri di questo tipo, il servizio Intune invia una notifica all'SDK.

L'app deve eseguire la registrazione per le notifiche dall'SDK creando un oggetto `MAMNotificationReceiver` e registrandolo con `MAMNotificationReceiverRegistry`. Ciò avviene specificando il ricevente e il tipo di notifica desiderato in `App.onCreate`, come nell'esempio seguente:

```java
@Override
public void onCreate() {
  super.onCreate();
  MAMComponents.get(MAMNotificationReceiverRegistry.class)
    .registerReceiver(
      new ToastNotificationReceiver(),
      MAMNotificationType.WIPE_USER_DATA);
  }
```

### <a name="mamnotificationreceiver"></a>MAMNotificationReceiver

L'interfaccia `MAMNotificationReceiver` riceve semplicemente le notifiche dal servizio Intune. Alcune notifiche vengono gestite direttamente dall'SDK, mentre altre richiedono la partecipazione dell'app. Un'app **deve** restituire true o false da una notifica. L'app deve sempre restituire true, a meno che un'azione che l'app tenta di eseguire come risultato della notifica non riesca.

* Questo errore può essere segnalato al servizio Intune. Uno dei casi in cui la segnalazione è appropriata è quando un'app non riesce a cancellare i dati utente dopo che l'amministratore IT avvia una cancellazione.

>[!NOTE]
> Il blocco in `MAMNotificationReceiver.onReceive` è sicuro, in quanto il callback non viene eseguito nel thread dell'interfaccia utente.

L'interfaccia `MAMNotificationReceiver` come definita nell'SDK è inclusa di seguito:

```java
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
```

### <a name="types-of-notifications"></a>Tipi di notifiche

Le notifiche seguenti vengono inviate all'app e alcune possono richiedere la partecipazione dell'app:

* **WIPE_USER_DATA**: questa notifica viene inviata in una classe `MAMUserNotification`. Alla ricezione della notifica, è previsto che l'app elimini tutti i dati associati all'identità "aziendale" passata con `MAMUserNotification`. Questa notifica viene attualmente inviata durante l'annullamento della registrazione del servizio APP-WE. Il nome primario dell'utente viene in genere specificato durante il processo di registrazione. Se si effettua la registrazione per questa notifica, l'app deve garantire che tutti i dati utente siano stati eliminati. Se la registrazione non viene effettuata, verrà usato il comportamento di cancellazione selettiva predefinito.

* **WIPE_USER_AUXILIARY_DATA**: le app possono eseguire la registrazione per questa notifica se vogliono che Intune App SDK usi il comportamento predefinito di cancellazione selettiva, ma vogliono comunque poter rimuovere alcuni dati ausiliari quando viene eseguita la cancellazione. Questa notifica non è disponibile per le app con identità singola e verrà inviata solo alle app con identità multiple.

* **REFRESH_POLICY**: questa notifica viene inviata in un oggetto `MAMUserNotification`. Alla ricezione di questa notifica, qualsiasi decisione relativa ai criteri di Intune memorizzata nella cache deve essere invalidata e aggiornata. Se l'app non archivia alcun presupposto per i criteri, non occorre la registrazione per questa notifica.

* **REFRESH_APP_CONFIG**: questa notifica viene inviata in una `MAMUserNotification`. Alla ricezione di questa notifica, gli eventuali dati di configurazione dell'applicazione memorizzati nella cache devono essere invalidati e aggiornati.

* **MANAGEMENT_REMOVED**: questa notifica viene inviata in un oggetto `MAMUserNotification` e informa l'app che sta per diventare non gestita. Quando non è gestita, l'app non può più leggere i file crittografati, leggere i dati crittografati con MAMDataProtectionManager, interagire con gli Appunti crittografati o partecipare in altro modo all'ecosistema di app gestite. Vedere altri dettagli di seguito.

* **MAM_ENROLLMENT_RESULT**: questa notifica viene inviata in una `MAMEnrollmentNotification` per informare l'app che è stato eseguito un tentativo di registrazione APP-WE e per comunicare lo stato di tale tentativo.

* **COMPLIANCE_STATUS**: questa notifica viene inviata in una `MAMComplianceNotification` per informare l'app del risultato di un tentativo di correzione di conformità.

> [!NOTE]
> Un'app non deve mai eseguire la registrazione sia per le notifiche `WIPE_USER_DATA` che per le notifiche `WIPE_USER_AUXILIARY_DATA`.

### <a name="managementremoved"></a>MANAGEMENT_REMOVED

La notifica `MANAGEMENT_REMOVED` indica che un utente precedentemente gestito tramite criteri non verrà più gestito da criteri MAM di Intune. Questa condizione non richiede la cancellazione dei dati utente o la disconnessione dell'utente (se fosse necessaria la cancellazione, verrebbe inviata una notifica `WIPE_USER_DATA`). È possibile che molte app non debbano gestire tale notifica. Le app che usano `MAMDataProtectionManager`, tuttavia, dovrebbero [considerare con attenzione questa notifica](#data-protection).

Quando MAM chiama il ricevente `MANAGEMENT_REMOVED` dell'app, saranno vere le condizioni seguenti:
* MAM ha già decrittografato file crittografati in precedenza (ma non i buffer di dati protetti) appartenenti all'app. I file nei percorsi pubblici nella scheda SD che non appartengono direttamente all'app (ad esempio, le cartelle Documenti o Download) non vengono decrittografati.
* I nuovi file o buffer di dati protetti creati dal metodo ricevente (o qualsiasi altro codice in esecuzione dopo l'avvio del ricevente) non verranno crittografati.
* L'app ha comunque accesso alle chiavi di crittografia, quindi le operazioni come la decrittografia dei buffer di dati avranno esito positivo.

Quando il ricevente dell'app restituisce il controllo, non avrà più accesso alle chiavi di crittografia.

## <a name="configure-azure-active-directory-authentication-library-adal"></a>Configurare Azure Active Directory Authentication Library (ADAL)

Leggere prima di tutto le linee guida sull'integrazione di ADAL disponibili nel [repository ADAL su GitHub](https://github.com/AzureAD/azure-activedirectory-library-for-android).

L'SDK si basa su [ADAL](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/) per gli scenari di [autenticazione](https://azure.microsoft.com/documentation/articles/active-directory-authentication-scenarios/) e avvio condizionale, che richiedono la configurazione delle app con [Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-whatis/). I valori di configurazione vengono comunicati all'SDK tramite i metadati di AndroidManifest.

Per configurare l'app e abilitare l'autenticazione appropriata, aggiungere il codice seguente al nodo dell'app in AndroidManifest.xml. Alcune di queste configurazioni sono necessarie solo se l'app usa ADAL per l'autenticazione in generale. In questo caso, saranno necessari i valori specifici usati dall'app per registrare se stessa con AAD. Questo avviene per evitare che all'utente finale venga chiesta l'autenticazione due volte, a causa del fatto che AAD riconosce due valori di registrazione separati, uno dall'app e uno dall'SDK.

```xml
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
```

### <a name="adal-metadata"></a>Metadati ADAL

* **Authority** rappresenta l'autorità AAD in uso. Se questo valore è assente, viene utilizzato l'ambiente pubblico AAD.
    > [!NOTE]
    > Non impostare questo campo se l'applicazione è compatibile con cloud sovrani.

* **ClientID** è l'ID client AAD (noto anche come ID applicazione) da usare. È necessario usare l'ID client dell'app, se è stata eseguita la registrazione con Azure AD. Se questo valore è assente, viene usato un valore predefinito di Intune.

* **NonBrokerRedirectURI** è l'URI di reindirizzamento di AAD da usare in assenza del broker. Se non è specificato alcun valore, viene usato il valore predefinito `urn:ietf:wg:oauth:2.0:oob`. Questo valore predefinito è appropriato per la maggior parte delle app.

    * NonBrokerRedirectURI viene usato solo quando SkipBroker è "true".

* **SkipBroker** viene usato per sostituire il comportamento di partecipazione di SSO ADAL predefinito. SkipBroker deve essere specificato solo per le app che specificano un ID client **e** non supportano l'autenticazione negoziata o l'accesso SSO a livello di dispositivo. In questo caso deve essere impostato su "true". La maggior parte delle app non deve impostare il parametro SkipBroker.

    * È **necessario** specificare un ID client nel manifesto per specificare un valore SkipBroker.

    * Quando viene specificato un ID client, il valore predefinito è "false".

    * Se SkipBroker è "true", verrà usato NonBrokerRedirectURI. Anche per le app che non integrano ADAL (e pertanto non hanno un ID client) verrà usata l'impostazione predefinita "true".

### <a name="common-adal-configurations"></a>Configurazioni comuni di ADAL

Di seguito sono indicati alcuni modi comuni di configurazione di un'app con ADAL. Trovare la configurazione dell'app e assicurarsi di impostare i parametri dei metadati ADAL (illustrati in precedenza) sui valori necessari. In tutti i casi, se lo si desidera, si può specificare l'autorità per gli ambienti non predefiniti. Se non specificato, verrà usata l'autorità AAD di produzione pubblica.

#### <a name="1-app-does-not-integrate-adal"></a>1. ADAL non è integrato nell'app
I metadati ADAL **non devono** essere presenti nel manifesto.

#### <a name="2-app-integrates-adal"></a>2. ADAL è integrato nell'app

|Parametro ADAL obbligatorio| Valore |
|--|--|
| ClientID | ID client dell'app (generato da Azure AD al momento della registrazione dell'app) |

L'autorità può essere specificata se necessario.

È necessario registrare l'app in Azure AD e concedere all'app l'accesso al servizio dei criteri di protezione delle app:
* Vedere [qui](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications) per informazioni sulla registrazione di un'applicazione con Azure AD.
* Assicurarsi di seguire i passaggi per concedere le autorizzazioni delle app Android al servizio dei criteri di protezione delle app. Usare le istruzioni in [Introduzione a Microsoft Intune App SDK](https://docs.microsoft.com/intune/app-sdk-get-started#next-steps-after-integration) in "Concedere all'app l'accesso al servizio di protezione delle app di Intune (facoltativo)". 

Vedere anche i requisiti per l'[Accesso condizionale](#conditional-access) di seguito.


#### <a name="3-app-integrates-adal-but-does-not-support-brokered-authenticationdevice-wide-sso"></a>3. App che integra ADAL ma non supporta l'autenticazione negoziata/SSO a livello di dispositivo

|Parametro ADAL obbligatorio| Valore |
|--|--|
| ClientID | ID client dell'app (generato da Azure AD al momento della registrazione dell'app) |
| SkipBroker | **True** |

Se necessario, è possibile specificare Authority e NonBrokerRedirectURI.

### <a name="conditional-access"></a>Accesso condizionale

L'accesso condizionale è una [funzionalità](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer) di Azure Active Directory che può essere usata per controllare l'accesso alle risorse AAD. [Gli amministratori di Intune possono definire le regole dell'accesso condizionale](https://docs.microsoft.com/intune/conditional-access) che concedono l'accesso alle risorse solo a dispositivi o app gestite da Intune. Per fare in modo che l'app possa accedere alle risorse quando necessario, è necessario seguire la procedura riportata di seguito. Se l'app non acquisisce i token di accesso AAD o accede solo alle risorse che non possono essere protette dall'accesso condizionale, ignorare questi passaggi.

1. Seguire le [linee guida per l'integrazione di ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-android#how-to-use-this-library). 
   Vedere in particolare il passaggio 11 per l'utilizzo del broker.
2. [Registrazione dell'applicazione con Azure Active Directory] (https://docs.microsoft.com/azure/active-directory/active-directory-app-registration). 
   L'URI di reindirizzamento è reperibile nelle linee guida per l'integrazione ADAL precedenti.
3. Impostare i parametri dei metadati del manifesto in base alla procedura [Configurazioni comuni di ADAL](#common-adal-configurations), passaggio 2, esposta prima.
4. Testare che tutto sia configurato correttamente abilitando l'[accesso condizionale basato su dispositivo](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use) nel [portale di Azure](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExchangeConnectorMenu/aad/connectorType/2) e verificare che
    - L'accesso alle app richieda l'installazione e la registrazione del portale aziendale di Intune
    - Dopo la registrazione, l'accesso all'app avvenga correttamente.
5. Dopo che l'app ha completato l'integrazione di Intune APP SDK, contattare msintuneappsdk@microsoft.com per essere aggiunti all'elenco delle app approvate per [l'accesso condizionale basato su app](https://docs.microsoft.com/intune/conditional-access-intune-common-ways-use#app-based-conditional-access).
6. Dopo aver aggiunto l'app all'elenco approvato, convalidare con [Configurare criteri di accesso condizionale basato su app](https://docs.microsoft.com/intune/app-based-conditional-access-intune-create) e assicurarsi che l'accesso all'app avvenga correttamente.

## <a name="app-protection-policy-without-device-enrollment"></a>Criteri di protezione delle app senza registrazione del dispositivo

### <a name="overview"></a>Panoramica
I criteri di protezione delle app di Intune senza registrazione del dispositivo, noti anche come APP-WE o MAM-WE, consentono la gestione delle app da Intune senza richiedere la registrazione del dispositivo nella soluzione MDM di Intune. APP-WE funziona con o senza registrazione del dispositivo. Il Portale aziendale deve comunque essere installato nel dispositivo, ma l'utente non deve necessariamente accedervi e registrare il dispositivo.

> [!NOTE]
> Tutte le app devono supportare i criteri di protezione delle app senza registrazione del dispositivo.

### <a name="workflow"></a>Flusso di lavoro

Quando un'app crea un nuovo account utente, deve registrare l'account per la gestione con Intune App SDK. L'SDK gestisce i dettagli della registrazione dell'app nel servizio APP-WE. Se necessario, in caso di errore, esegue nuovi tentativi di registrazione a intervalli di tempo appropriati.

L'app può anche eseguire una query su Intune App SDK in relazione allo stato di un utente registrato per determinare se all'utente deve essere impedito l'accesso al contenuto aziendale. È possibile registrare più account per la gestione, ma attualmente è possibile registrare attivamente con il servizio APP-WE un solo account per volta. Ciò significa che nell'app un solo account per volta può ricevere i criteri di protezione delle app.

L'app deve fornire un callback per acquisire il token di accesso appropriato da Azure Active Directory Authentication Library (ADAL) per conto dell'SDK. Si presuppone che l'app usi già ADAL per l'autenticazione utente e per acquisire i propri token di accesso.

Quando l'app rimuove completamente un account, deve annullare la registrazione dell'account per indicare che l'app non deve più applicare i criteri per tale utente. Se l'utente è stato registrato nel servizio MAM, la sua registrazione sarà annullata e l'app verrà cancellata.


### <a name="overview-of-app-requirements"></a>Panoramica dei requisiti dell'app

Per implementare l'integrazione APP-WE, l'app deve registrare l'account utente con MAM SDK:

1. L'app _deve_ implementare e registrare un'istanza dell'interfaccia `MAMServiceAuthenticationCallback`. L'istanza di callback deve essere registrata il prima possibile nel ciclo di vita dell'app (in genere nel metodo `onMAMCreate()` della classe dell'applicazione).

2. Quando viene creato un account utente e l'utente accede correttamente con ADAL, l'app _deve_ chiamare `registerAccountForMAM()`.

3. Quando un account utente viene rimosso, l'app deve chiamare `unregisterAccountForMAM()` per rimuovere l'account dalla gestione di Intune.

    > [!NOTE]
    > Se un utente si disconnette temporaneamente dall'app, non è necessario che l'app chiami `unregisterAccountForMAM()`. La chiamata può avviare una cancellazione per rimuovere completamente i dati aziendali per l'utente.


### <a name="mamenrollmentmanager"></a>MAMEnrollmentManager

Tutte le API di autenticazione e registrazione necessarie sono disponibili nell'interfaccia `MAMEnrollmentManager`. È possibile ottenere un riferimento a `MAMEnrollmentManager` come indicato di seguito:

```java
MAMEnrollmentManager mgr = MAMComponents.get(MAMEnrollmentManager.class);

// make use of mgr
```

L'istanza di `MAMEnrollmentManager` restituita non è sicuramente Null. I metodi API rientrano in due categorie: **autenticazione** e **registrazione dell'account**.

```java
package com.microsoft.intune.mam.policy;

public interface MAMEnrollmentManager {
    public enum Result {
        AUTHORIZATION_NEEDED,
        NOT_LICENSED,
        ENROLLMENT_SUCCEEDED,
        ENROLLMENT_FAILED,
        WRONG_USER,
        MDM_ENROLLED,
        UNENROLLMENT_SUCCEEDED,
        UNENROLLMENT_FAILED,
        PENDING,
        COMPANY_PORTAL_REQUIRED;
    }

    //Authentication methods
    interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
    }
    void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
    void updateToken(String upn, String aadId, String resourceId, String token);

    //Registration methods
    void registerAccountForMAM(String upn, String aadId, String tenantId);
    void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
    void unregisterAccountForMAM(String upn);
    Result getRegisteredAccountStatus(String upn);
}
```

### <a name="account-authentication"></a>Autenticazione di account

Questa sezione descrive i metodi API di autenticazione in `MAMEnrollmentManager` e come usarli.

```java
interface MAMServiceAuthenticationCallback {
        String acquireToken(String upn, String aadId, String resourceId);
}
void registerAuthenticationCallback(MAMServiceAuthenticationCallback callback);
void updateToken(String upn, String aadId, String resourceId, String token);
```

1. L'app deve implementare l'interfaccia `MAMServiceAuthenticationCallback` per consentire all'SDK di richiedere un token ADAL per l'utente e l'ID risorsa specifici. L'istanza di callback deve essere fornita a `MAMEnrollmentManager` chiamando il relativo metodo `registerAuthenticationCallback()`. Potrebbe essere necessario un token presto nel ciclo di vita dell'app per i nuovi tentativi di registrazione o le archiviazioni di aggiornamento dei criteri di protezione delle app, quindi la posizione ideale per registrare il callback è all'interno del metodo `onMAMCreate()` della sottoclasse `MAMApplication` dell'app.

2. Il metodo `acquireToken()` deve acquisire il token di accesso per l'ID risorsa richiesto per l'utente specificato. Se non è possibile acquisire il token richiesto, il metodo deve restituire Null.

    > [!NOTE]
    > Assicurarsi che l'app usi i parametri `resourceId` e `aadId` passati a `acquireToken()` in modo che venga acquisito il token corretto.

    ```java
    class MAMAuthCallback implements MAMServiceAuthenticationCallback {
        public String acquireToken(String upn, String aadId, String resourceId) {
            return mAuthContext.acquireTokenSilentSync(resourceId, ClientID, aadId).getAccessToken();
        }
    }
    ```

3. Nel caso in cui l'app non sia in grado di fornire un token quando l'SDK chiama `acquireToken()`, ad esempio, se si verifica un errore nel processo di autenticazione invisibile all'utente e non è il momento adatto per visualizzare un'interfaccia utente, l'app può fornire un token in un secondo momento chiamando il metodo `updateToken()`. Gli stessi valori di UPN, ID di AAD e ID risorsa richiesti dalla chiamata precedente di `acquireToken()` devono essere passati a `updateToken()`, insieme al token acquisito. L'app deve chiamare questo metodo non appena possibile dopo la restituzione di Null dal callback fornito.

    > [!NOTE]
    > L'SDK chiamerà `acquireToken()` periodicamente per ottenere il token, quindi la chiamata di `updateToken()` non è strettamente necessaria. È tuttavia fortemente consigliabile, perché può essere utile per consentire di completare in modo tempestivo le registrazioni e le archiviazioni dei criteri di protezione delle app.


### <a name="account-registration"></a>Registrazione dell'account

Questa sezione descrive i metodi API di registrazione degli account in `MAMEnrollmentManager` e come usarli.

```java
void registerAccountForMAM(String upn, String aadId, String tenantId);
void registerAccountForMAM(String upn, String aadId, String tenantId, String authority);
void unregisterAccountForMAM(String upn);
Result getRegisteredAccountStatus(String upn);
```

1. Per registrare un account per la gestione, l'app deve chiamare `registerAccountForMAM()`. Un account utente è identificato dal relativo UPN e dall'ID utente AAD. L'ID tenant è anch'esso necessario per associare i dati di registrazione al tenant AAD dell'utente. L'autorità dell'utente può inoltre essere fornita per consentire la registrazione in cloud sovrani specifici. Per altre informazioni, vedere [Registrazione in cloud sovrani](#sovereign-cloud-registration).  L'SDK può cercare di registrare l'app per l'utente specifico nel servizio MAM. Se la registrazione non riesce, viene eseguito periodicamente un nuovo tentativo fino a quando la registrazione dell'account non viene annullata. L'intervallo tra tentativi è in genere di 12-24 ore. L'SDK fornisce lo stato dei tentativi di registrazione in modo asincrono tramite notifiche.

2. Poiché l'autenticazione di AAD è necessaria, il momento migliore per registrare l'account utente è dopo che l'utente ha eseguito l'accesso nell'app e viene autenticato correttamente usando ADAL. L'ID AAD e l'ID tenant dell'utente vengono restituiti dalla chiamata di autenticazione ADAL come parte dell'oggetto [`AuthenticationResult`](https://github.com/AzureAD/azure-activedirectory-library-for-android).
    * L'ID tenant proviene dal metodo `AuthenticationResult.getTenantID()`.
    * Le informazioni sull'utente sono disponibili in un oggetto secondario di tipo `UserInfo` proveniente da `AuthenticationResult.getUserInfo()` e l'ID utente AAD viene recuperato da tale oggetto chiamando `UserInfo.getUserId()`.

3. Per annullare la registrazione di un account dalla gestione di Intune, l'app deve chiamare `unregisterAccountForMAM()`. Se l'account è stato registrato correttamente e viene gestito, l'SDK annullerà la registrazione dell'account e ne cancellerà i dati. I tentativi periodici di registrazione per l'account verranno arrestati. L'SDK fornisce lo stato della richiesta di annullamento della registrazione in modo asincrono tramite una notifica.

### <a name="sovereign-cloud-registration"></a>Registrazione in cloud sovrani

Le applicazioni che sono [compatibili con i cloud sovrani](https://www.microsoft.com/trustcenter/cloudservices/nationalcloud) **devono** fornire `authority` a `registerAccountForMAM()`.  Ciò può essere ottenuto fornendo `instance_aware=true` in acquireToken extraQueryParameters [1.14.0+](https://github.com/AzureAD/azure-activedirectory-library-for-android/releases/tag/v1.14.0) di ADAL e chiamando `getAuthority()` su AuthenticationCallback AuthenticationResult.

```java
mAuthContext.acquireToken(this, RESOURCE_ID, CLIENT_ID, REDIRECT_URI, PromptBehavior.FORCE_PROMPT, "instance_aware=true",
        new AuthenticationCallback<AuthenticationResult>() {
            @Override
            public void onError(final Exception exc) {
                // authentication failed
            }

            @Override
            public void onSuccess(final AuthenticationResult result) {
                mAuthority = result.getAuthority();
                // handle other parts of the result
            }
        });
```

> [!NOTE]
> Non impostare l'elemento di metadati `com.microsoft.intune.mam.aad.Authority` in AndroidManifest.xml.

> [!NOTE]
> Assicurarsi che l'autorità sia impostata correttamente nel metodo `MAMServiceAuthenticationCallback::acquireToken()`.

#### <a name="currently-supported-sovereign-clouds"></a>Cloud sovrani attualmente supportati

1. Arlington

### <a name="important-implementation-notes"></a>Note di implementazione importanti

#### <a name="authentication"></a>Autenticazione

* Quando l'app chiama `registerAccountForMAM()`, può ricevere un callback nell'interfaccia `MAMServiceAuthenticationCallback` poco dopo, in un thread diverso. Idealmente, l'app ha acquisito il proprio token da ADAL prima della registrazione dell'account per accelerare l'acquisizione del token richiesto. Se l'app restituisce un token valido dal callback, la registrazione continua e l'app ottiene il risultato finale tramite una notifica.

* Se l'app non restituisce un token AAD valido, il risultato finale del tentativo di registrazione è `AUTHENTICATION_NEEDED`. Se l'app riceve il risultato tramite notifica, è consigliabile accelerare il processo di registrazione acquisendo il token per l'utente e la risorsa richiesto precedentemente da `acquireToken()` e chiamando il metodo `updateToken()` per avviare di nuovo il processo di registrazione.

* L'oggetto `MAMServiceAuthenticationCallback` registrato dell'app verrà chiamato anche per acquisire un token per le archiviazioni di aggiornamento dei criteri di protezione delle app periodiche. Se l'app non è in grado di fornire un token quando richiesto, non riceve una notifica, ma deve tentare di acquisire un token e chiamare `updateToken()` al successivo momento opportuno per accelerare il processo di archiviazione. Se non viene fornito un token, il callback verrà comunque chiamato al successivo tentativo di archiviazione.

* Il supporto dei cloud sovrani richiede la specifica dell'autorità.

#### <a name="registration"></a>Registrazione

* Per praticità, i metodi di registrazione sono idempotenti. Ad esempio, `registerAccountForMAM()` registra un account ed esegue un tentativo di registrazione dell'app solo se l'account non è già registrato e `unregisterAccountForMAM()` annulla la registrazione di un account solo se è attualmente registrato. Le chiamate successive non hanno effetto, quindi se i metodi vengono chiamati più di una volta non ci sono problemi. Inoltre, non è garantita la corrispondenza tra le chiamate a questi metodi e le notifiche dei risultati: ad esempio, se viene chiamato il metodo `registerAccountForMAM` per un'identità già registrata, potrebbe non venire inviata di nuovo la notifica per tale identità. È possibile che vengano inviate notifiche che non corrispondono alle chiamate a questi metodi, perché l'SDK può eseguire periodicamente tentativi di registrazione in background e possono essere avviate operazioni di annullamento della registrazione da richieste di cancellazione ricevute dal servizio Intune.

* I metodi di registrazione possono essere chiamati per un numero qualsiasi di identità diverse, ma attualmente può venire registrato correttamente un solo account utente. Se più account utente con licenza per Intune e interessati dai criteri di protezione delle app vengono registrati contemporaneamente o quasi, non è garantito quale account verrà registrato correttamente.

* Infine, è possibile eseguire una query su `MAMEnrollmentManager` per verificare se un account specifico è stato registrato e ottenere il suo stato corrente usando il metodo `getRegisteredAccountStatus`. Se l'account fornito non è registrato, questo metodo restituisce **Null**. Se l'account è registrato, questo metodo restituisce lo stato dell'account come uno dei membri dell'enumerazione `MAMEnrollmentManager.Result`.

### <a name="result-and-status-codes"></a>Codici di risultato e stato

Quando un account viene registrato per la prima volta, ha uno stato iniziale `PENDING`, che indica che il tentativo di registrazione del servizio MAM iniziale è incompleto. Al termine del tentativo di registrazione, viene inviata una notifica con uno dei codici di risultato indicati nella tabella seguente. Il metodo `getRegisteredAccountStatus()` restituisce inoltre lo stato dell'account, in modo che l'app possa sempre determinare se l'accesso al contenuto aziendale è bloccato per l'utente. Se il tentativo di registrazione non riesce, lo stato dell'account può cambiare nel tempo in quanto l'SDK esegue nuovi tentativi di registrazione in background.

|Codice di risultato | Spiegazione |
| -- | -- |
|AUTHORIZATION_NEEDED | Questo risultato indica che non è stato fornito un token dall'istanza di `MAMServiceAuthenticationCallback` registrata dell'app o che il token fornito non è valido.  L'app deve acquisire un token valido e chiamare `updateToken()`, se possibile. |
| NOT_LICENSED | L'utente non ha una licenza per Intune oppure il tentativo di contattare il servizio MAM di Intune non è riuscito.  L'app deve continuare in uno stato non gestito (normale) e l'utente non deve essere bloccato.  Verranno eseguiti periodicamente nuovi tentativi di registrazione, nel caso in cui in futuro l'utente disponga di una licenza. |
| ENROLLMENT_SUCCEEDED | Il tentativo di registrazione ha avuto esito positivo oppure l'utente è già registrato.  Nel caso di una registrazione con esito positivo, verrà inviata una notifica di aggiornamento dei criteri prima di questa notifica.  L'accesso ai dati aziendali deve essere consentito. |
| ENROLLMENT_FAILED | Il tentativo di registrazione non è riuscito.  Maggiori dettagli sono disponibili nei log del dispositivo.  L'app non deve consentire l'accesso alle risorse aziendali in questo stato, perché è stato stabilito in precedenza che l'utente ha una licenza per Intune.|
| WRONG_USER | Un solo utente per dispositivo può registrare un'app con il servizio MAM.  Per eseguire correttamente la registrazione come utente diverso, è prima necessario annullare la registrazione di tutte le app registrate.  In caso contrario, l'app deve eseguire la registrazione come utente primario.  Questo controllo viene eseguito dopo il controllo della licenza, quindi all'utente deve essere impedito l'accesso ai dati aziendali fino a quando la registrazione dell'app non avviene correttamente.|
| UNENROLLMENT_SUCCEEDED | L'annullamento della registrazione è avvenuto correttamente.|
| UNENROLLMENT_FAILED | La richiesta di annullamento della registrazione non è riuscita.  Maggiori dettagli sono disponibili nei log del dispositivo. |
| PENDING | Il tentativo di registrazione iniziale per l'utente è in corso.  L'app può bloccare l'accesso ai dati aziendali fino a quando non è noto il risultato della registrazione, ma ciò non è necessario. |
| COMPANY_PORTAL_REQUIRED | L'utente ha la licenza per Intune, ma l'app non può essere registrata fino a quando non viene installata l'app Portale aziendale nel dispositivo. Intune App SDK tenta di bloccare l'accesso all'app per l'utente specificato, chiedendo di installare l'app Portale aziendale (vedere di seguito per informazioni dettagliate). |


### <a name="company-portal-requirement-prompt-override-optional"></a>Override della richiesta di installazione del Portale aziendale (facoltativo)

Se viene ricevuto il risultato `COMPANY_PORTAL_REQUIRED`, l'SDK blocca le attività che usano l'identità per cui è stata richiesta la registrazione. L'SDK farà in modo che tali attività visualizzino una richiesta di download del Portale aziendale. Se si vuole impedire questo comportamento nell'app, le attività possono implementare `MAMActivity.onMAMCompanyPortalRequired`.

Questo metodo viene chiamato prima che l'SDK visualizzi l'interfaccia utente di blocco predefinita. Se l'app modifica l'identità dell'attività o annulla la registrazione dell'utente che ha tentato di eseguire la registrazione, l'SDK non bloccherà l'attività. In questo caso, è compito dell'app evitare la perdita di dati aziendali. Solo le app con identità multiple, illustrate più avanti, saranno in grado di modificare l'identità dell'attività.

Se non si eredita in modo esplicito `MAMActivity` (perché gli strumenti di compilazione apporteranno tale modifica), ma è comunque necessario gestire questa notifica, è invece possibile implementare `MAMActivityBlockingListener`.

### <a name="notifications"></a>Notifiche

Se l'app si registra per le notifiche di tipo **MAM_ENROLLMENT_RESULT**, verrà inviata una `MAMEnrollmentNotification` per informare l'app che la richiesta di registrazione è stata completata. L'oggetto `MAMEnrollmentNotification` verrà ricevuto tramite l'interfaccia `MAMNotificationReceiver`, come descritto nella sezione [Eseguire la registrazione per le notifiche dall'SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMEnrollmentNotification extends MAMUserNotification {
    MAMEnrollmentManager.Result getEnrollmentResult();
}
```

Il metodo `getEnrollmentResult()` restituisce il risultato della richiesta di registrazione.  Poiché `MAMEnrollmentNotification` estende `MAMUserNotification`, è disponibile anche l'identità dell'utente per cui è stato eseguito il tentativo di registrazione. L'app deve implementare l'interfaccia `MAMNotificationReceiver` per ricevere queste notifiche, come descritto nella sezione [Eseguire la registrazione per le notifiche dall'SDK](#register-for-notifications-from-the-sdk).

Lo stato dell'account utente registrato può cambiare quando viene ricevuta una notifica di registrazione, ma non cambia in tutti i casi (ad esempio, se la notifica `AUTHORIZATION_NEEDED` viene ricevuta dopo un risultato più informativo, come `WRONG_USER`, come stato dell'account viene mantenuto il risultato più informativo).  Dopo la corretta registrazione dell'account, lo stato rimarrà `ENROLLMENT_SUCCEEDED` fino a quando non viene annullata la registrazione dell'account o l'account non viene cancellato.

Lo stato dell'account utente registrato può cambiare quando viene ricevuta una notifica di registrazione, ma non cambia in tutti i casi (ad esempio, se la notifica `AUTHORIZATION_NEEDED` viene ricevuta dopo un risultato più informativo, come `WRONG_USER`, come stato dell'account viene mantenuto il risultato più informativo).  Dopo la corretta registrazione dell'account, lo stato rimarrà `ENROLLMENT_SUCCEEDED` fino a quando non viene annullata la registrazione dell'account o l'account non viene cancellato.

## <a name="app-ca-with-policy-assurance"></a>Accesso condizionale di Protezione app di Intune con garanzia di applicazione dei criteri

### <a name="overview"></a>Panoramica
Con l'accesso condizionale di Protezione app di Intune con garanzia di applicazione dei criteri, l'accesso alle risorse dipende dall'applicazione dei criteri di Protezione app di Intune.  AAD impone tale restrizione richiedendo che l'app sia registrata e gestita da Protezione app di Intune prima di concedere un token per accedere a una risorsa protetta con l'accesso condizionale di Protezione app di Intune con garanzia di applicazione dei criteri.  L'app deve usare il broker di ADAL per l'acquisizione del token e la configurazione è identica a quello descritta in precedenza in [Accesso condizionale](#conditional-access)

### <a name="adal-changes"></a>Modifiche per ADAL
La libreria ADAL include un nuovo codice di errore che informa l'app che l'errore di acquisizione di un token è stato causato dalla mancata conformità con la gestione di Protezione app di Intune.  Se l'app riceve questo codice di errore, deve chiamare l'SDK per tentare di ottenere la conformità tramite la registrazione dell'app e l'applicazione dei criteri. Il metodo `onError()` dell'`AuthenticationCallback` ADAL riceverà un'eccezione con il codice di errore `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  In questo caso, è possibile eseguire il cast dell'eccezione in `IntuneAppProtectionPolicyRequiredException`, da cui è possibile estrarre parametri aggiuntivi da usare per la correzione della conformità (vedere l'esempio di codice riportato di seguito). Dopo la correzione, l'app può tentare di nuovo l'acquisizione del token tramite ADAL.

> [!NOTE]
> Per questo nuovo codice di errore e per il supporto dell'accesso condizionale di Protezione app di Intune con garanzia di applicazione dei criteri è richiesta la versione 1.15.0 (o successiva) della libreria ADAL.

### <a name="mamcompliancemanager"></a>MAMComplianceManager

L'interfaccia `MAMComplianceManager` viene usata quando ADAL riceve l'errore di richiesto dai criteri.  Contiene il metodo `remediateCompliance()` che deve essere chiamato per tentare di ottenere uno stato conforme per l'app. È possibile ottenere un riferimento a `MAMComplianceManager` come indicato di seguito:

```java
MAMComplianceManager mgr = MAMComponents.get(MAMComplianceManager.class);

// make use of mgr
```

L'istanza di `MAMComplianceManager` restituita non è sicuramente Null.

```java
package com.microsoft.intune.mam.policy;

public interface MAMComplianceManager {
    void remediateCompliance(String upn, String aadId, String tenantId, String authority, boolean showUX);
}
```

Il metodo `remediateCompliance()` viene chiamato per tentare di inserire l'app nella gestione per soddisfare le condizioni richieste affinché AAD possa concedere il token richiesto.  I primi quattro parametri possono essere estratti dall'eccezione ricevuta dal metodo `AuthenticationCallback.onError()` di ADAL (vedere l'esempio di codice riportato di seguito).  Il parametro finale è un valore booleano che controlla se viene visualizzata un'esperienza utente durante il tentativo di conformità.  Questa è una semplice interfaccia di blocco di operazione in corso, fornita come impostazione predefinita pe le app che non hanno l'esigenza di visualizzare un'esperienza utente personalizzata durante questa operazione.  Il blocco verrà attivato solo mentre è in corso la correzione per la conformità e non verrà visualizzato il risultato finale.  L'app deve registrare un destinatario delle notifiche per gestire l'esito positivo o negativo del tentativo di correzione per la conformità (vedere sotto).

Il metodo `remediateCompliance()` potrebbe eseguire una registrazione MAM come parte delle procedure per ottenere la conformità.  L'app può ricevere una notifica di registrazione se ha registrato un destinatario per le notifiche di registrazione.  Per il `MAMServiceAuthenticationCallback` registrato dell'app verrà chiamato il metodo `acquireToken()` per ottenere un token per la registrazione MAM. `acquireToken()` verrà chiamato prima che l'app abbia acquisito il token, in modo che qualsiasi attività di gestione o di creazione di account che l'app esegue dopo la corretta acquisizione del token non possa ancora essere stata eseguita.  Il callback deve essere in grado di acquisire un token in questo caso.  Se non è possibile restituire un token da `acquireToken()`, il tentativo di correzione per la conformità avrà esito negativo.  Se si chiama `updateToken()` in un secondo momento con un token valido per la risorsa richiesta, il tentativo di correzione per la conformità verrà ripetuto immediatamente con il token specificato.

> [!NOTE]
> L'acquisizione di token invisibile all'utente sarà comunque possibile in `acquireToken()`, perché l'utente avrà già ricevuto indicazione di installare il broker e registrare il dispositivo prima di ricevere l'errore `ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED`.  In questo modo il broker avrà a disposizione un token di aggiornamento valido nella cache, che consente l'esito positivo dell'acquisizione invisibile all'utente del token richiesto.

Di seguito è riportato un esempio di ricezione dell'errore di richiesto dai criteri nel metodo `AuthenticationCallback.onError()` e di chiamata di `MAMComplianceManager` per gestire l'errore.

```java
public void onError(@Nullable Exception exc) {
    if (exc instanceof AuthenticationException && 
        ((AuthenticationException) exc).getCode() == ADALError.AUTH_FAILED_INTUNE_POLICY_REQUIRED) {

        final IntuneAppProtectionPolicyRequiredException policyRequiredException = 
            (IntuneAppProtectionPolicyRequiredException) ex;

        final String upn = policyRequiredException.getAccountUpn();
        final String aadId = policyRequiredException.getAccountUserId();
        final String tenantId = policyRequiredException.getTenantId();
        final String authority = policyRequiredException.getAuthorityURL();

        MAMComplianceManager complianceManager = MAMComponents.get(MAMComplianceManager.class);
        complianceManager.remediateCompliance(upn, aadId, tenantId, authority, showUX);
    }
}
```

### <a name="status-notifications"></a>Notifiche di stato

Se l'app si registra per le notifiche di tipo **COMPLIANCE_STATUS**, verrà inviata una `MAMComplianceNotification` per informare l'app dello stato finale del tentativo di correzione per la conformità. L'oggetto `MAMComplianceNotification` verrà ricevuto tramite l'interfaccia `MAMNotificationReceiver`, come descritto nella sezione [Eseguire la registrazione per le notifiche dall'SDK](#register-for-notifications-from-the-sdk).

```java
public interface MAMComplianceNotification extends MAMUserNotification {
    MAMCAComplianceStatus getComplianceStatus();
    String getComplianceErrorTitle();
    String getComplianceErrorMessage();
}
```

Il metodo `getComplianceStatus()` restituisce il risultato del tentativo di correzione per la conformità come valore dall'enum `MAMCAComplianceStatus`.

|Codice di stato | Spiegazione |
| -- | -- |
| UNKNOWN | Lo stato è sconosciuto. Potrebbe indicare un motivo dell'errore imprevisto. Potrebbero essere disponibili informazioni aggiuntive nei log del portale aziendale. |
| COMPLIANT | La correzione per la conformità ha avuto esito positivo e l'app è ora conforme ai criteri. Deve essere eseguito un nuovo tentativo di acquisizione del token ADAL. |
| NOT_COMPLIANT | Il tentativo di correzione per la conformità ha avuto esito negativo.  L'app non è conforme e non deve essere eseguito un nuovo tentativo di acquisizione del token ADAL finché non viene risolta la condizione di errore.  Vengono inviate informazioni aggiuntive sull'errore insieme a MAMComplianceNotification. |
| SERVICE_FAILURE | Si è verificato un errore durante il tentativo di recuperare i dati di conformità dal servizio Intune. Potrebbero essere disponibili informazioni aggiuntive nei log del portale aziendale. |
| NETWORK_FAILURE | Si è verificato un errore durante la connessione al servizio Intune. L'app deve eseguire un nuovo tentativo di acquisizione del token dopo il ripristino della connessione di rete. |
| CLIENT_ERROR | Il tentativo di correzione per la conformità non è riuscito per qualche motivo correlato al client.  Ad esempio, nessun token o utente non corretto. Vengono inviate informazioni aggiuntive sull'errore insieme a MAMComplianceNotification. |
| PENDING | Il tentativo di correzione per la conformità non è riuscito perché il servizio non aveva ancora ricevuto la risposta di stato quando è stato superato il limite di tempo. L'app deve ritentare più tardi l'acquisizione del token. |
| COMPANY_PORTAL_REQUIRED | L'app Portale aziendale deve essere installata nel dispositivo in ordine per completare la correzione per la conformità.  Se l'app Portale aziendale è già installata nel dispositivo, è necessario riavviarla.  In questo caso, verrà visualizzata una finestra di dialogo per richiedere all'utente di riavviare l'app. |

Se lo stato di conformità è `MAMCAComplianceStatus.COMPLIANT`, l'app deve avviare nuovamente l'acquisizione del token originale (per la propria risorsa). Se il tentativo di correzione per la conformità non è riuscito, i metodi `getComplianceErrorTitle()` e `getComplianceErrorMessage()` restituiranno stringhe localizzate che l'app può visualizzare facoltativamente all'utente finale.  La maggior parte dei casi di errore non può essere corretta dall'app, quindi in generale potrebbe essere preferibile generare un errore per la creazione dell'account o l'accesso e consentire all'utente di riprovare più tardi.  Se un errore persiste, i log MAM possono essere utili per determinare la causa.  L'utente finale può inviare i log usando le istruzioni riportate [qui](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android "Inviare i log al supporto tecnico dell'azienda tramite posta elettronica").

Poiché `MAMComplianceNotification` estende `MAMUserNotification`, è disponibile anche l'identità dell'utente per cui è stato eseguito il tentativo di correzione.

Di seguito è riportato un esempio di registrazione di un destinatario usando una classe anonima per implementare l'interfaccia MAMNotificationReceiver:

```java
final MAMNotificationReceiverRegistry notificationRegistry = MAMComponents.get(MAMNotificationReceiverRegistry.class);
// create a receiver
final MAMNotificationReceiver receiver = new MAMNotificationReceiver() {
    public boolean onReceive(MAMNotification notification) {
        if (notification.getType() == MAMNotificationType.COMPLIANCE_STATUS) {
            MAMComplianceNotification complianceNotification = (MAMComplianceNotification) notification;
            
            // take appropriate action based on complianceNotification.getComplianceStatus()
            
            // unregister this receiver if no longer needed
            notificationRegistry.unregisterReceiver(this, MAMNotificationType.COMPLIANCE_STATUS);
        }
        return true;
    }
};
// register the receiver
notificationRegistry.registerReceiver(receiver, MAMNotificationType.COMPLIANCE_STATUS);
```

> [!NOTE]
> Il destinatario delle notifiche deve essere registrato prima di chiamare `remediateCompliance()` per evitare una race condition che potrebbe causare la mancata ricezione della notifica.

### <a name="implementation-notes"></a>Note sull'implementazione

> [!NOTE]
> Il metodo `MAMServiceAuthenticationCallback.acquireToken()` dell'app deve passare *true* per il nuovo flag `forceRefresh` a `acquireTokenSilentSync()` per forzare un aggiornamento dal broker.  Ciò consente di risolvere un problema di memorizzazione nella cache con i token di ADAL che può influire sui token del servizio MAM. Il codice è in generale simile al seguente:
```java
AuthenticationResult result = acquireTokenSilentSync(resourceId, clientId, userId, /* forceRefresh */ true);
```

> [!NOTE]
> Se si vuole visualizzare un'esperienza utente di blocco personalizzata durante il tentativo di correzione, è necessario passare *false* per il parametro showUX a `remediateCompliance()`. È necessario assicurarsi di visualizzare l'esperienza utente e registrare il listener delle notifiche prima di chiamare `remediateCompliance()`.  Ciò impedirà situazioni di race condition a causa delle quali la notifica potrebbe non essere visualizzata se `remediateCompliance()` ha esito negativo molto rapidamente.  Ad esempio, il metodo `onCreate()` o `onMAMCreate()` di una sottoclasse Activity è la posizione ideale per registrare il listener delle notifiche e quindi chiamare `remediateCompliance()`.  I parametri per `remediateCompliance()` possono essere passati all'esperienza utente come funzionalità aggiuntive per Intent.  Quando viene ricevuta la notifica sullo stato di conformità, è possibile visualizzare il risultato o semplicemente terminare l'attività.

> [!NOTE]
> `remediateCompliance()` registrerà l'account e tenterà la registrazione.  Dopo aver acquisito il token principale, la chiamata di `registerAccountForMAM()` non è necessaria, ma non crea alcun problema. D'altra parte, se l'app non riesce ad acquisire il token e vuole rimuovere l'account utente, deve chiamare `unregisterAccountForMAM()` per rimuovere l'account e impedire i tentativi di registrazione in background.

## <a name="protecting-backup-data"></a>Protezione dei dati di backup

A partire da Android Marshmallow (API 23), Android offre due modi in cui un'app può eseguire il backup dei dati. Ogni opzione è disponibile e richiede procedure diverse per garantire l'implementazione corretta della protezione dati di Intune. È possibile consultare la tabella di seguito per informazioni sulle azioni corrispondenti necessarie per il corretto comportamento di protezione dati.  Per altre informazioni sui metodi di backup, vedere la [guida alle API di Android](https://developer.android.com/guide/topics/data/backup.html).

### <a name="auto-backup-for-apps"></a>Backup automatico per le app

Android ha iniziato a offrire [backup completi automatici](https://developer.android.com/guide/topics/data/autobackup.html) in Google Drive per le app nei dispositivi Android Marshmallow, indipendentemente dall'API di destinazione dell'app. Nel file AndroidManifest.x ls, se si imposta in modo esplicito `android:allowBackup` su **false**, l'app non verrà mai accodata per i backup da Android e i dati "aziendali" rimarranno all'interno dell'app. In questo caso non è necessaria alcuna azione ulteriore.

Tuttavia, per impostazione predefinita l'attributo `android:allowBackup` viene impostato su true, anche se `android:allowBackup` non è specificato nel file manifesto. Questo significa che viene eseguito automaticamente il backup di tutti i dati dell'app nell'account Google Drive dell'utente, un comportamento predefinito che comporta il **rischio di perdite di dati**. Per questo motivo l'SDK richiede l'applicazione delle modifiche indicate di seguito per garantire una corretta protezione dei dati.  È importante seguire le linee guida seguenti per proteggere i dati dei clienti in modo appropriato, se si vuole eseguire l'app in dispositivi Android Marshmallow.  

Intune consente di usare tutte le [funzionalità di backup automatico](https://developer.android.com/guide/topics/data/autobackup.html) disponibili da Android, inclusa la possibilità di definire regole personalizzate in XML, ma è necessario attenersi alla procedura seguente per proteggere i dati:

1. Se l'app **non** usa il proprio oggetto BackupAgent personalizzato, usare l'oggetto MAMBackupAgent predefinito per consentire backup completi automatici conformi ai criteri di Intune. Inserire quanto segue nel manifesto dell'app:

    ```xml
    android:fullBackupOnly="true"
    android:backupAgent="com.microsoft.intune.mam.client.app.backup.MAMDefaultBackupAgent"
    ```


2. **[Facoltativo]** Se è stato implementato un oggetto BackupAgent personalizzato facoltativo, è necessario assicurarsi di usare MAMBackupAgent o MAMBackupAgentHelper. Vedere le sezioni seguenti. Valutare se usare **MAMDefaultFullBackupAgent** di Intune (descritto nel passaggio 1), che offre un semplice backup su Android M e versioni successive.

3. Quando si decide quale tipo di backup completo deve ricevere l'app (non filtrato, filtrato o nessuno) è necessario impostare l'attributo `android:fullBackupContent` su true, false o su una risorsa XML all'interno dell'app.

4. È quindi _**necessario**_ copiare il contenuto di `android:fullBackupContent` in un tag di metadati denominato `com.microsoft.intune.mam.FullBackupContent` nel manifesto.

    **Esempio 1**: se si vuole che l'app abbia backup completi senza esclusioni, impostare l'attributo `android:fullBackupContent` e il tag di metadati `com.microsoft.intune.mam.FullBackupContent` su **true**:

    ```xml
    android:fullBackupContent="true"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="true" />  
    ```

    **Esempio 2**: se si vuole che l'app usi l'oggetto BackupAgent personalizzato e rifiuti esplicitamente i backup automatici completi conformi ai criteri di Intune, è necessario impostare l'attributo e il tag di metadati su **false**:

    ```xml
    android:fullBackupContent="false"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:value="false" />  
    ```

    **Esempio 3**: se si vuole che l'app abbia backup completi in base a regole personalizzate definite in un file XML, impostare l'attributo e il tag di metadati sulla stessa risorsa XML:

    ```xml
    android:fullBackupContent="@xml/my_scheme"
    ...
    <meta-data android:name="com.microsoft.intune.mam.FullBackupContent" android:resource="@xml/my_scheme" />  
    ```


### <a name="keyvalue-backup"></a>Backup di chiave/valore

L'opzione di [backup di chiave/valore](https://developer.android.com/guide/topics/data/keyvaluebackup.html) è disponibile per tutte le API 8+ e carica i dati dell'app nel [servizio di backup Android](https://developer.android.com/google/backup/index.html). La quantità di dati per ogni utente dell'app è limitata a 5 MB. Se si usa il backup di chiave/valore, è necessario usare un oggetto **BackupAgentHelper** o **BackupAgent**.

### <a name="backupagenthelper"></a>BackupAgentHelper

BackupAgentHelper è più semplice da implementare rispetto a BackupAgent in termini sia di funzionalità Android native sia di integrazione MAM di Intune. BackupAgentHelper consente allo sviluppatore di registrare interi file e preferenze condivise rispettivamente in un oggetto **FileBackupHelper** e **SharedPreferencesBackupHelper**, che vengono quindi aggiunti a BackupAgentHelper subito dopo la creazione. Attenersi alla procedura seguente per usare BackupAgentHelper con MAM di Intune:

1. Per usare il backup di identità multiple con BackupAgentHelper, seguire la guida di Android per l'[estensione di BackupAgentHelper](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgentHelper).

2. Fare in modo che la classe estenda l'equivalente MAM di BackupAgentHelper, FileBackupHelper e SharedPreferencesBackupHelper.

|Classe Android | Equivalente MAM |
|--|--|
|BackupAgentHelper |MAMBackupAgentHelper |
|FileBackupHelper | MAMFileBackupHelper
|SharedPreferencesBackupHelper| MAMSharedPreferencesBackupHelper|

Attenendosi a queste indicazioni sarà possibile implementare un processo di backup e ripristino di identità multiple.

### <a name="backupagent"></a>BackupAgent

Un oggetto BackupAgent consente di definire in modo molto più esplicito i dati di cui eseguire il backup. Dato che lo sviluppatore è responsabile dell'implementazione, sono necessari altri passaggi per garantire una protezione appropriata dei dati da Intune. Poiché il maggior carico di lavoro ricade sullo sviluppatore, l'integrazione di Intune è leggermente più coinvolta.

**Integrare MAM:**

1. Leggere attentamente la guida di Android per il [backup di chiave/valore](https://developer.android.com/guide/topics/data/keyvaluebackup.html) e in particolare per l'[estensione di BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent) per assicurarsi che l'implementazione di BackupAgent segua le linee guida Android.

2. Fare in modo che la classe estenda `MAMBackupAgent`.

**Backup di identità multiple:**

1. Prima di iniziare il backup, controllare che per i file o i buffer di dati di cui si prevede di eseguire il backup **l'amministratore IT abbia consentito il backup** in scenari con identità multiple. Per eseguire il controllo, è disponibile la funzione `isBackupAllowed` in `MAMFileProtectionManager` e `MAMDataProtectionManager`. Se per il file o il buffer di dati non è consentito il backup, non continuare a includere l'elemento nel backup.

2. Se a un certo punto durante il backup si vuole eseguire il backup delle identità per i file controllati nel passaggio 1, è necessario chiamare `backupMAMFileIdentity(BackupDataOutput data, File … files)` con i file da cui si prevede di estrarre i dati. In questo modo, verranno automaticamente create entità di backup, che verranno scritte in `BackupDataOutput` . Queste entità verranno utilizzate automaticamente al momento del ripristino.

**Ripristino di identità multiple:**

La guida al backup dei dati specifica un algoritmo generale per il ripristino dei dati dell'applicazione e fornisce un esempio di codice nella sezione relativa all'[estensione di BackupAgent](https://developer.android.com/guide/topics/data/keyvaluebackup.html#BackupAgent). Per un corretto ripristino di identità multiple, è necessario seguire la struttura generale fornita in questo esempio di codice con particolare attenzione a quanto segue:

1. È necessario usare un ciclo `while(data.readNextHeader())`* per scorrere le entità di backup.

2. È necessario chiamare `data.skipEntityData()`* se `data.getKey()`* non corrisponde alla chiave scritta in `onBackup`. Senza questo passaggio, le operazioni di ripristino potrebbero non riuscire.

3. Evitare di restituire il risultato mentre si utilizzano le entità di backup nel costrutto `while(data.readNextHeader())`*, in quanto le entità scritte automaticamente andranno perse.

* Dove `data` è il nome della variabile locale per l'oggetto **MAMBackupDataInput** passato all'app subito dopo il ripristino.

## <a name="multi-identity-optional"></a>Identità multiple (facoltativo)

### <a name="overview"></a>Panoramica
Per impostazione predefinita, Intune App SDK applicherà i criteri all'app nel suo complesso. Le identità multiple sono una funzionalità facoltativa di protezione delle app di Intune, che è possibile abilitare per consentire l'applicazione dei criteri a un livello specifico per identità. Ciò richiede una partecipazione dell'app molto più attiva rispetto ad altre funzionalità di protezione delle app.

> [!NOTE]
> Una mancanza di partecipazione dell'app corretta può causare perdite di dati e altri problemi di protezione.

Una volta che l'utente registra il dispositivo o l'app, l'SDK registra questa identità e la considera l'identità primaria gestita di Intune. Gli altri utenti dell'app verranno trattati come non gestiti con impostazioni dei criteri senza restrizioni.

> [!NOTE]
> Attualmente è supportata solo un'identità gestita di Intune per volta.

Un'identità viene definita come stringa. Le identità **non fanno distinzione tra maiuscole e minuscole** e le richieste all'SDK per un'identità possono non restituire un risultato in cui maiuscole e minuscole corrispondono a quelle usate in origine durante l'impostazione dell'identità.

L'app *deve* informare l'SDK quando intende modificare l'identità attiva. In alcuni casi, l'SDK invia anche una notifica all'app quando è necessaria una modifica di identità. Nella maggior parte dei casi, tuttavia, MAM non conosce i dati visualizzati nell'interfaccia utente o usati in un thread in un determinato momento e si basa sull'app per impostare l'identità corretta per evitare la perdita di dati. Nelle sezioni che seguono vengono descritti alcuni scenari specifici che richiedono azioni a livello di app.

### <a name="enabling-multi-identity"></a>Abilitazione di identità multiple

Per impostazione predefinita, tutte le app sono considerate app a identità singola. È possibile dichiarare che un'app supporta le identità multiple inserendo i metadati seguenti in AndroidManifest.xml.

```xml
  <meta-data
    android:name="com.microsoft.intune.mam.MAMMultiIdentity"
    android:value="true" />
```

### <a name="setting-the-identity"></a>Impostazione dell'identità

Gli sviluppatori possono impostare l'identità dell'utente dell'app sui livelli seguenti con priorità decrescente:

  1. A livello di thread
  2. A livello di `Context` (in genere `Activity`)
  3. A livello di processo

Un'identità impostata a livello di thread ha una priorità maggiore rispetto a un'identità impostata a livello di `Context` che sostituisce a sua volta un'identità impostata a livello di processo. Un'identità impostata a livello di `Context` viene usata solo negli scenari associati appropriati. Alle operazioni di I/O su file, ad esempio, non è associato un `Context`. In genere, le app imposteranno l'identità `Context` su `Activity`. Un'app non *deve* visualizzare i dati per un'identità gestita, a meno che l'identità `Activity` non sia impostata sulla stessa identità. In generale, l'identità a livello di processo è utile unicamente se l'app funziona solo con un singolo utente alla volta su tutti i thread. Per molte app potrebbe non essere necessaria.

Se l'app usa il contesto `Application` per acquisire servizi di sistema, verificare che sia stata impostata l'identità del thread o del processo oppure di aver impostato l'identità dell'interfaccia utente per il contesto `Application` dell'app.

Per gestire i casi speciali quando si aggiorna l'identità dell'interfaccia utente con `setUIPolicyIdentity` oppure `switchMAMIdentity`, a entrambi i metodi può essere passato un set di valori `IdentitySwitchOption`.

* `IGNORE_INTENT`: usare per richiedere un cambio di identità che deve ignorare la finalità associata all'attività corrente.
  Ad esempio:

  1. L'app riceve una finalità da un'identità gestita che contiene un documento gestito e l'app visualizza il documento.
  2. L'utente passa all'identità personale, quindi l'app richiede un cambio di identità dell'interfaccia utente. Nell'identità personale l'app non visualizza più il documento, quindi si usa `IGNORE_INTENT` quando viene richiesto il cambio di identità.

  Se non impostato, l'SDK presupporrà che nell'app è ancora in uso la finalità più recente. In questo modo, i criteri di ricezione per la nuova identità tratteranno la finalità come dati in ingresso e ne useranno l'identità.

>[!NOTE]
> Dato che `CLIPBOARD_SERVICE` viene usato per le operazioni dell'interfaccia utente, l'SDK usa l'identità dell'interfaccia utente dell'attività in primo piano per le operazioni `ClipboardManager`.
> È possibile usare i metodi seguenti in `MAMPolicyManager` per impostare l'identità e recuperare i valori di identità impostati in precedenza.

```java
  public static void setUIPolicyIdentity(final Context context, final String identity, final MAMSetUIIdentityCallback mamSetUIIdentityCallback);

  public static String getUIPolicyIdentity(final Context context);

  public static MAMIdentitySwitchResult setProcessIdentity(final String identity);

  public static String getProcessIdentity();

  public static MAMIdentitySwitchResult setCurrentThreadIdentity(final String identity);

  public static String getCurrentThreadIdentity();

/**
   * Get the current app policy. This does NOT take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use the overload below.
   */
  public static AppPolicy getPolicy();

  /**
  * Get the current app policy. This DOES take the UI (Context) identity into account.
   * If the current operation has any context (e.g. an Activity) associated with it, use this function.
   */
  public static AppPolicy getPolicy(final Context context);


  public static AppPolicy getPolicyForIdentity(final String identity);

  public static boolean getIsIdentityManaged(final String identity);
  ```

>[!NOTE]
> È possibile cancellare l'identità dell'app impostandola su Null.
>
> Una stringa vuota può essere usata come un'identità che non avrà mai criteri di protezione delle app.

#### <a name="results"></a>Risultati
Tutti i metodi usati per impostare l'identità restituiscono valori di risultato tramite `MAMIdentitySwitchResult`. Possono essere restituiti quattro valori:

| Valore restituito | Scenario |
|--|--|
| SUCCEEDED | La modifica dell'identità è riuscita. |
| NOT_ALLOWED  | La modifica dell'identità non è consentita. Si verifica in seguito al tentativo di impostare l'identità (contesto) dell'interfaccia utente quando è impostata un'identità diversa sul thread corrente. |
| CANCELLED | L'utente ha annullato la modifica di identità, in genere premendo il pulsante Indietro in una richiesta di PIN o autenticazione. |
| FAILED | La modifica dell'identità non è riuscita per un motivo non specificato.|

L'app dovrebbe verificare l'esito positivo di un cambio di identità prima di visualizzare o usare dati aziendali. Attualmente, i cambi di identità di processo e thread avranno sempre esito positivo per un'app con il supporto per identità multiple abilitato, tuttavia Microsoft si riserva il diritto di aggiungere le condizioni di errore. Il cambio di identità dell'interfaccia utente potrebbe non riuscire per argomenti non validi, se genera un conflitto con l'identità del thread o se l'utente cancella i requisiti di avvio condizionale (ad esempio, premendo il pulsante Indietro nella schermata del PIN).


Nel caso dell'impostazione di un'identità a livello di contesto, il risultato viene restituito in modo asincrono. Se il contesto è un'attività, l'SDK sa se la modifica dell'identità è riuscita solo dopo l'avvio condizionale, che potrebbe richiedere l'immissione di un PIN o di credenziali aziendali da parte dell'utente. È previsto che l'app implementi un oggetto `MAMSetUIIdentityCallback` per ricevere questo risultato. Per questo parametro è possibile passare Null.

```java
    public interface MAMSetUIIdentityCallback {
        void notifyIdentityResult(MAMIdentitySwitchResult identitySwitchResult);
  }
```

È anche possibile impostare l'identità di un'attività direttamente tramite un metodo in `MAMActivity` invece di chiamare `MAMPolicyManager.setUIPolicyIdentity`. A tale scopo, usare il metodo seguente:

```java
     public final void switchMAMIdentity(final String newIdentity, final EnumSet<IdentitySwitchOption> options);
```

È anche possibile eseguire l'override di un metodo in `MAMActivity` se si vuole che l'app riceva una notifica del risultato dei tentativi di modifica dell'identità per tale attività.

``` java
    public void onSwitchMAMIdentityComplete(final MAMIdentitySwitchResult result);
```

Se non si esegue l'override di `onSwitchMAMIdentityComplete` (o si chiama il metodo `super`), un cambio di identità non riuscito per un'attività causerà il completamento dell'attività. Se si esegue l'override del metodo, è necessario prestare attenzione a che i dati aziendali non vengano visualizzati dopo un cambio di identità non riuscito.

>[!NOTE]
> Il cambio di identità potrebbe rendere necessario ricreare l'attività. In questo caso, il callback `onSwitchMAMIdentityComplete` verrà recapitato alla nuova istanza dell'attività.


### <a name="implicit-identity-changes"></a>Modifiche di identità implicite

Oltre alla possibilità di impostare l'identità tramite l'app, l'identità di un thread o un contesto può cambiare anche in base all'ingresso di dati da un'altra app gestita da Intune che usa criteri di protezione delle app.

#### <a name="examples"></a>Esempi

  1. Se un'attività viene avviata da un oggetto `Intent` inviato da un'altra app MAM, l'identità dell'attività verrà impostata in base all'identità effettiva nell'altra app al momento dell'invio di `Intent`.

  2. Per i servizi, l'identità del thread verrà impostata in modo analogo per la durata di una chiamata di `onStart` o `onBind`. Anche le chiamate all'oggetto `Binder` restituito da `onBind` impostano temporaneamente l'identità del thread.

  3. Le chiamate a `ContentProvider` imposteranno l'identità del thread in modo analogo per la loro durata.


  Inoltre, l'interazione dell'utente con un'attività può causare un cambio di identità implicito.

  **Esempio:** se un utente annulla una richiesta di autenticazione durante l'esecuzione di `Resume`, il risultato è un passaggio implicito a un'identità vuota.

  L'app ha la possibilità di essere messa a conoscenza di queste modifiche e, se necessario, di impedirle. `MAMService` e `MAMContentProvider` espongono il metodo seguente che può essere sottoposto a override dalle sottoclassi:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchResultCallback callback);
  ```

  Nella classe `MAMActivity` è presente un parametro aggiuntivo nel metodo:

  ```java
  public void onMAMIdentitySwitchRequired(final String identity,
    final AppIdentitySwitchReason reason,
    final AppIdentitySwitchResultCallback callback);
  ```

  * `AppIdentitySwitchReason` acquisisce l'origine del cambio implicito e può accettare i valori `CREATE`, `RESUME_CANCELLED` e `NEW_INTENT`.  Il motivo `RESUME_CANCELLED` viene usato quando la ripresa di un'attività comporta la visualizzazione dell'interfaccia utente per l'immissione del PIN, per l'autenticazione o per altre esigenze di conformità e l'utente tenta di eliminare tale interfaccia, in genere usando il pulsante Indietro.


  * L'oggetto `AppIdentitySwitchResultCallback` è come segue:

    ```java
    public interface AppIdentitySwitchResultCallback {
        /**
         * @param result
         *            whether the identity switch can proceed.
         */
        void reportIdentitySwitchResult(AppIdentitySwitchResult result);
    }
    ```

    Dove ```AppIdentitySwitchResult``` è `SUCCESS` o `FAILURE`.

Il metodo `onMAMIdentitySwitchRequired` viene chiamato per tutte le modifiche di identità implicite ad eccezione di quelle effettuate tramite un Binder restituito da `MAMService.onMAMBind`. Le implementazioni predefinite di `onMAMIdentitySwitchRequired` chiamano immediatamente:

* `reportIdentitySwitchResult(FAILURE)` quando il motivo è `RESUME_CANCELLED`.

* `reportIdentitySwitchResult(SUCCESS)` in tutti gli altri casi.

  Si prevede che la maggior parte delle app non abbia l'esigenza di bloccare o ritardare un cambio di identità in un modo diverso, ma se un'app deve farlo, è necessario prendere in considerazione i punti seguenti:

  * Se un cambio di identità è bloccato, il risultato è lo stesso che si sarebbe avuto se le impostazioni di condivisione di `Receive` avessero vietato l'ingresso dei dati.

  * Se un servizio è in esecuzione sul thread principale, è **necessario** chiamare `reportIdentitySwitchResult` in modo sincrono altrimenti il thread dell'interfaccia utente si blocca.

  * Per la creazione di **`Activity`** , `onMAMIdentitySwitchRequired` verrà chiamato prima di `onMAMCreate`. Se l'app deve visualizzare l'interfaccia utente per determinare se consentire il cambio di identità, tale interfaccia utente deve essere visualizzata usando un'attività *diversa*.

  * In una **`Activity`** , quando viene richiesto il passaggio all'identità vuota con il motivo `RESUME_CANCELLED`, l'app deve modificare l'attività ripresa in modo che visualizzi dati coerenti con il cambio di identità.  Se ciò non è possibile, l'app deve rifiutare il cambio e all'utente verrà chiesto di nuovo di conformarsi ai criteri per l'identità di ripresa, ad esempio con la visualizzazione della schermata per l'immissione del PIN dell'app.

    > [!NOTE]
    > Un'app con identità multiple riceverà sempre dati in arrivo sia da app gestite che non gestite. È responsabilità dell'app trattare i dati provenienti da identità gestite in modo gestito.

  Se un'identità richiesta è gestita (usare `MAMPolicyManager.getIsIdentityManaged` per controllare), ma l'app non è in grado di usare tale account (ad esempio, perché gli account, come gli account di posta elettronica, devono essere prima di tutto configurati nell'app), il cambio di identità deve essere rifiutato.

#### <a name="build-plugin--tool-considerations"></a>Considerazioni sul plug-in o sullo strumento di compilazione
Se non si eredita in modo esplicito da `MAMActivity`, `MAMService` o `MAMContentProvider` (perché si consente agli strumenti di compilazione di apportare tale modifica), ma è comunque necessario elaborare i cambi di identità, è invece possibile implementare `MAMActivityIdentityRequirementListener` (per una `Activity`) o `MAMIdentityRequirementListener` (per un `Service` o `ContentProviders`).
Il comportamento predefinito per `MAMActivity.onMAMIdentitySwitchRequired` è accessibile chiamando il metodo statico `MAMActivity.defaultOnMAMIdentitySwitchRequired(activity, identity,
reason, callback)`.

Analogamente, se è necessario eseguire l'override di `MAMActivity.onSwitchMAMIdentityComplete`, è possibile implementare `MAMActivityIdentitySwitchListener` senza ereditare in modo esplicito da `MAMActivity`.

### <a name="preserving-identity-in-async-operations"></a>Mantenimento dell'identità nelle operazioni asincrone
Le operazioni nel thread dell'interfaccia utente inviano spesso attività in background a un altro thread. Un'app multi-identità dovrà verificare che queste attività in background vengano eseguite con l'identità appropriata, che spesso corrisponde all'identità usata dall'attività che ha inviato le operazioni. L'SDK MAM offre `MAMAsyncTask` e `MAMIdentityExecutors`, utili per il mantenimento dell'identità.
Devono essere usati se l'operazione asincrona potrebbe scrivere i dati aziendali in un file o comunicare con altre app.

#### <a name="mamasynctask"></a>MAMAsyncTask

Per usare `MAMAsyncTask`, è sufficiente ereditare da essa anziché da `AsyncTask` e sostituire gli override di `doInBackground` e `onPreExecute` rispettivamente con `doInBackgroundMAM` e `onPreExecuteMAM`. Il costruttore `MAMAsyncTask` accetta un contesto di attività. Ad esempio:

```java
  AsyncTask<Object, Object, Object> task = new MAMAsyncTask<Object, Object, Object>(thisActivity) {

    @Override
    protected Object doInBackgroundMAM(final Object[] params) {
        // Do operations.
    }

    @Override
    protected void onPreExecuteMAM() {
        // Do setup.
    };
```

### <a name="mamidentityexecutors"></a>MAMIdentityExecutors
`MAMIdentityExecutors` consente di eseguire il wrapping di un'istanza `Executor` o `ExecutorService` esistente come `Executor`/`ExecutorService` di mantenimento dell'identità con i metodi `wrapExecutor` e `wrapExecutorService`. Ad esempio

```java
  Executor wrappedExecutor = MAMIdentityExecutors.wrapExecutor(originalExecutor, activity);
  ExecutorService wrappedService = MAMIdentityExecutors.wrapExecutorService(originalExecutorService, activity);
```
### <a name="file-protection"></a>Protezione dei file

A ogni file è associata un'identità al momento della creazione in base all'identità a livello di processo e thread. Questa identità verrà usata sia per la crittografia dei file che per la cancellazione selettiva. Verranno crittografati solo i file la cui identità è gestita e ha criteri che richiedono la crittografia. La cancellazione selettiva predefinita dell'SDK cancellerà solo i file associati all'identità per cui è stata richiesta una cancellazione. L'app può richiedere o modificare l'identità di un file usando la classe `MAMFileProtectionManager`.

```java
public final class MAMFileProtectionManager {

   /**
    * Protect a file or directory. This will synchronously trigger whatever protection is required for the file, and will tag the
    * file for future protection changes. If an identity is set on a directory, it is set recursively on all files and
    * subdirectories. New files or directories will inherit their parent directory's identity. If MAM is operating in offline mode,
    * this method will silently do nothing.
    *
    * @param identity
    *        Identity to set.
    * @param file
    *        File to protect.
    *
    * @throws IOException
    *         If the file cannot be protected.
    */
   public static void protect(final File file, final String identity) throws IOException;

   /**
     * Protect a file obtained from a content provider. This is intended to be used for
     * sdcard (whether internal or removable) files accessed through the Storage Access Framework.
     * It may also be used with descriptors referring to private files owned by this app.
     * It is not intended to be used for files owned by other apps and such usage will fail. If
     * creating a new file via a content provider exposed by another MAM-integrated app, the new
     * file identity will automatically be set correctly if the ContentResolver in use was
     * obtained via a Context with an identity or if the thread identity is set.
     *
     * This will synchronously trigger whatever protection is required for the file, and will tag
     * the file for future protection changes. If an identity is set on a directory, it is set
     * recursively on all files and subdirectories. If MAM is operating in offline mode, this
     * method will silently do nothing.
     *
     * @param identity
     *            Identity to set.
     * @param file
     *            File to protect.
     *
     * @throws IOException
     *             If the file cannot be protected.
     */
    public static void protect(final ParcelFileDescriptor file, final String identity) throws IOException;

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

   /**
    * Get the protection info on a file.
    *
    * @param file
    *            File or directory to get information on.
    * @return File protection info, or null if there is no protection info.
    * @throws IOException
    *             If the file cannot be read or opened.
    */
    public static MAMFileProtectionInfo getProtectionInfo(final ParcelFileDescriptor file) throws IOException;

}

public interface MAMFileProtectionInfo {
    String getIdentity();
}
 ```

#### <a name="app-responsibility"></a>Responsabilità dell'app
MAM non può dedurre automaticamente una relazione tra i file in lettura e i dati visualizzati in una `Activity`. L'app *deve* impostare l'identità dell'interfaccia utente in modo appropriato prima di visualizzare i dati aziendali, inclusi i dati letti dai file. Se un file proviene dall'esterno dell'app (da un `ContentProvider` o letto da un percorso pubblicamente accessibile in scrittura), l'app *deve* tentare di determinare l'identità di file (usando `MAMFileProtectionManager.getProtectionInfo`) prima di visualizzare le informazioni lette dal file. Se `getProtectionInfo` segnala un'identità non Null e non vuota, l'identità dell'interfaccia utente *deve* essere impostata in base a questa identità (usando `MAMActivity.switchMAMIdentity` o `MAMPolicyManager.setUIPolicyIdentity`). Se il cambio di identità ha esito negativo, i dati dal file *non devono* essere visualizzati.

Il flusso potrebbe essere simile al seguente:
  * L'utente seleziona un documento da aprire nell'app.
  * Durante il flusso aperto, prima della lettura dei dati dal disco, l'app conferma l'identità da usare per visualizzare il contenuto
    * Info MAMFileProtectionInfo = MAMFileProtectionManager.getProtectionInfo(docPath)
    * if(Info) MAMPolicyManager.setUIPolicyIdentity (attività, info.getIdentity(), callback)
    * L'app attende finché non viene restituito un risultato al callback
    * Se il risultato restituito è un errore, l'app non visualizza il documento.
  * L'app si apre ed esegue il rendering del file.
  
#### <a name="single-identity-to-multi-identity-transition"></a>Transizione da identità singola a identità multiple
Se un'app rilasciata in precedenza con l'integrazione in Intune con identità singola usa in un secondo tempo l'integrazione con identità multiple, per le app installate in precedenza verrà eseguita una transizione (non visibile all'utente perché non è disponibile alcuna esperienza utente associata). L'app non *deve* eseguire alcuna azione esplicita per gestire questa transizione. Tutti i file creati prima della transizione continueranno a essere considerati gestiti (quindi rimarranno crittografati se i criteri per la crittografia sono attivi). Se si desidera, è possibile rilevare l'aggiornamento e usare `MAMFileProtectionManager.protect` per contrassegnare determinati file o directory con l'identità vuota (che consente di rimuovere la crittografia se applicata).

#### <a name="offline-scenarios"></a>Scenari offline

La modalità offline influisce sull'aggiunta di tag di identità ai file. Tenere in considerazione i punti seguenti:

  * Se l'app Portale aziendale non è installata, non è possibile assegnare tag di identità ai file.

  * Se l'app Portale aziendale è installata, ma non ha criteri MAM di Intune, non è possibile assegnare tag di identità ai file in modo affidabile.

  * Quando diventa disponibile la possibilità di assegnare tag di identità ai file, tutti i file creati in precedenza vengono considerati come personali/non gestiti (appartenenti all'identità con stringa vuota), a meno che l'app non sia stata installata in precedenza come app gestita con identità singola. In questo caso, i file vengono considerati appartenenti all'utente registrato.

### <a name="directory-protection"></a>Protezione delle directory

Le directory possono essere protette usando lo stesso metodo `protect` usato per proteggere i file. La protezione delle directory si applica in modo ricorsivo a tutti i file e le sottodirectory presenti nella directory e ai nuovi file creati all'interno della directory. Poiché la protezione delle directory viene applicata in modo ricorsivo, la chiamata di `protect` può richiedere tempo per il completamento in caso di directory di dimensioni molto grandi. Per questo motivo, è consigliabile che le app che applicano la protezione a una directory contenente un numero elevato di file eseguano `protect` in modo asincrono in un thread in background.

### <a name="data-protection"></a>Protezione dati

Non è possibile assegnare un tag a un file appartenente a più identità. Le app che devono archiviare dati appartenenti a utenti diversi nello stesso file possono farlo manualmente, usando le funzionalità fornite da `MAMDataProtectionManager`. Questo permette all'app di crittografare i dati e associarli a un utente specifico. I dati crittografati sono adatti per l'archiviazione su disco in un file. È possibile recuperare i dati associati all'identità e i dati possono essere decrittografati in un secondo momento.

Le app che usano `MAMDataProtectionManager` devono implementare un ricevitore per la notifica `MANAGEMENT_REMOVED`. Dopo il completamento della notifica, i buffer protetti tramite questa classe non saranno più leggibili se la crittografia dei file è stata abilitata quando i buffer erano protetti. Un'app può risolvere questa situazione chiamando `MAMDataProtectionManager.unprotect` su tutti i buffer durante la notifica. Si noti che è anche possibile chiamare protect durante questa notifica, se lo si desidera, per mantenere le informazioni di identità. Durante la notifica la crittografia viene sicuramente disabilitata.


```java

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

### <a name="content-providers"></a>Provider di contenuto

Se l'app fornisce dati aziendali diversi da `ParcelFileDescriptor` tramite un oggetto `ContentProvider`, l'app deve chiamare il metodo `isProvideContentAllowed(String)` in `MAMContentProvider`, passando l'UPN (nome dell'entità utente) dell'identità del proprietario per il contenuto. Se questa funzione restituisce false, il contenuto *non deve* essere restituito al chiamante. I descrittori di file restituiti tramite un provider di contenuti vengono gestiti automaticamente in base all'identità del file.

Se non si eredita `MAMContentProvider` in modo esplicito e invece si consente agli strumenti di compilazione di apportare tale modifica, è possibile chiamare una versione statica dello stesso metodo: `MAMContentProvider.isProvideContentAllowed(provider, contentIdentity)`.

### <a name="selective-wipe"></a>Cancellazione selettiva

Se si registra un'app con identità multiple per la notifica `WIPE_USER_DATA`, è responsabilità dell'app rimuovere tutti i dati per l'utente in corso di cancellazione, inclusi tutti i file la cui identità è stata contrassegnata come appartenente a tale utente. Se l'applicazione cancella i dati utente da un file ma gli altri dati devono rimanere, è *necessario* che l'app cambi l'identità del file tramite `MAMFileProtectionManager.protect` assegnandola a un utente personale o lasciando l'identità vuota. Se i criteri di crittografia sono in uso, tutti i file rimanenti che appartengono all'utente in corso di cancellazione non verranno decrittografati e non saranno più accessibili per l'app dopo la cancellazione.

Se esegue la registrazione per `WIPE_USER_DATA`, un'app non potrà usufruire dei vantaggi del comportamento di cancellazione selettiva predefinito dell'SDK. Per le app che supportano identità multiple, questa perdita può essere più significativa in quanto la cancellazione selettiva predefinita di MAM cancellerà solo i file la cui identità è interessata da una cancellazione. Se un'applicazione che supporta identità multiple vuole che venga eseguita la cancellazione selettiva predefinita di MAM _**e**_ vuole eseguire operazioni personalizzate sulla cancellazione, deve eseguire la registrazione per le notifiche `WIPE_USER_AUXILIARY_DATA`. Questa notifica verrà inviata immediatamente dall'SDK prima di eseguire la cancellazione selettiva predefinita di MAM. Un'app non deve mai registrarsi sia per `WIPE_USER_DATA` che per `WIPE_USER_AUXILIARY_DATA`.

La cancellazione selettiva predefinita chiuderà l'app normalmente, completando le attività e terminando il processo dell'app. Se l'app esegue l'override della cancellazione selettiva predefinita, è possibile provare a chiudere l'app manualmente per impedire all'utente di accedere ai dati in memoria dopo l'esecuzione di una cancellazione.


## <a name="enabling-mam-targeted-configuration-for-your-android-applications-optional"></a>Abilitazione della configurazione di destinazione MAM per le applicazioni Android (facoltativo)
È possibile configurare coppie chiave-valore specifiche dell'applicazione nella console di Intune per [MAM-WE](https://docs.microsoft.com/intune/app-configuration-policies-managed-app) e le [app del profilo di lavoro Android](https://docs.microsoft.com/intune/app-configuration-policies-use-android).
Queste coppie chiave-valore non vengono interpretate affatto da Intune, ma vengono passate all'app. Le applicazioni per le quali si vuole ricevere questo tipo di configurazione possono usare le classi `MAMAppConfigManager` e `MAMAppConfig` a tale scopo. Se più criteri sono destinati alla stessa app, potrebbero essere presenti più valori in conflitto per la stessa chiave.

> [!NOTE] 
> Le configurazioni per il recapito tramite MAM-WE non possono essere recapitate in `offline`.  Solo le AppRestrictions Android Enterprise verranno recapitate tramite `MAMUserNotification` per un'identità vuota in questo caso.

### <a name="example"></a>Esempio
```java
MAMAppConfigManager configManager = MAMComponents.get(MAMAppConfigManager.class);
String identity = "user@contoso.com"
MAMAppConfig appConfig = configManager.getAppConfig(identity);
LOGGER.info("App Config Data = " + appConfig.getFullData());
String valueToUse = null;
if (appConfig.hasConflict("foo")) {
    List<String> values = appConfig.getAllStringsForKey("foo");
    for (String value : values) {
        if (isCorrectValue(value)) {
            valueToUse = value;
        }
    }
} else {
    valueToUse = appConfig.getStringForKey("foo", MAMAppConfig.StringQueryType.Any);
}
LOGGER.info("Found value " + valueToUse);
```

### <a name="notification"></a>Notifica
La configurazione dell'app aggiunge un nuovo tipo di notifica:
* **REFRESH_APP_CONFIG**: questa notifica viene inviata in una `MAMUserNotification` e informa l'app che sono disponibili nuovi dati di configurazione dell'app.

### <a name="further-reading"></a>Letture di approfondimento
Per altre informazioni sulle funzionalità dell'API Graph, vedere [Informazioni di riferimento sull'API Graph](https://developer.microsoft.com/graph/docs/concepts/overview). <br>

Per altre informazioni su come creare un criterio di configurazione dell'app di destinazione MAM in Android, vedere la sezione relativa alla configurazione di app di destinazione MAM in [Come usare i criteri di configurazione delle app di Microsoft Intune per Android](https://docs.microsoft.com/intune/app-configuration-policies-use-android).

## <a name="style-customization-optional"></a>Personalizzazione dello stile (facoltativo)

Le viste generate da MAM SDK possono essere personalizzate visivamente per ottenere una maggiore corrispondenza con l'app in cui sono integrate. È possibile personalizzare i colori primari, secondari e di sfondo, oltre che le dimensioni del logo dell'app. La personalizzazione dello stile è facoltativa e, se non viene configurato uno stile personalizzato, verranno usati i valori predefiniti.


### <a name="how-to-customize"></a>Modalità di personalizzazione
Per applicare le modifiche dello stile alle viste MAM di Intune, è prima necessario creare un file XML di override dello stile. Questo file deve essere inserito nella directory "/res/xml" dell'app e può avere un nome qualsiasi. Di seguito è riportato un esempio del formato necessario per questo file.
```xml
<?xml version="1.0" encoding="utf-8"?>
<styleOverrides>
    <item
        name="foreground_color"
        resource="@color/red"/>
    <item
        name="accent_color"
        resource="@color/blue"/>
    <item
        name="background_color"
        resource="@color/green"/>
    <item
        name="logo_image"
        resource="@drawable/app_logo"/>
</styleOverrides>
```

È necessario riutilizzare le risorse già presenti all'interno dell'app. È ad esempio necessario definire il colore verde nel file colors.xml e farvi riferimento qui. Non è possibile usare il codice colore esadecimale "#0000ff". Le dimensioni massime per il logo dell'app sono di 110 DIP (dp). È possibile usare un'immagine del logo più piccola, ma rispettando le dimensioni massime si otterranno risultati migliori. Se si supera il limite di 110 DIP, l'immagine verrà ridotta con una possibile sfocatura.

Di seguito è riportato l'elenco completo degli attributi di stile consentiti, degli elementi dell'interfaccia utente da essi controllati, dei nomi di elemento degli attributi XML e dei tipi di risorsa previsti per ognuno di essi.

|Attributo di stile | Elementi dell'interfaccia utente interessati | Nome dell'elemento dell'attributo | Tipo di risorsa previsto |
| -- | -- | -- | -- |
| Colore di sfondo | Colore di sfondo della schermata del PIN <Br>Colore di riempimento della casella del PIN | background_color | Colore |
| Colore primo piano | Colore del testo in primo piano <br> Bordo della casella del PIN nello stato predefinito <br> Caratteri (compresi i caratteri offuscati) nella casella del PIN quando l'utente immette un PIN| foreground_color | Colore|
| Colore principale | Bordo della casella del PIN quando la casella è evidenziata <br> Collegamenti ipertestuali |accent_color | Colore |
| Logo dell'app | Icona grande visualizzata nella schermata del PIN dell'app Intune | logo_image | Risorsa drawable |

## <a name="default-enrollment-optional"></a>Registrazione predefinita (facoltativo)

Di seguito è riportato materiale sussidiario per la richiesta di un prompt utente all'avvio dell'app per la registrazione automatica al servizio APP-WE (denominata **registrazione predefinita** in questa sezione) e la richiesta dei criteri di protezione delle app Intune per consentire solo agli utenti protetti da Intune di usare un'app line-of-business per Android integrata con SDK. Viene anche illustrato come abilitare SSO per un'app line-of-business per Android integrata con SDK. Questa funzionalità **non** è supportata per le app dello Store che possono essere usate da utenti non Intune.

> [!NOTE] 
> Uno dei vantaggi della **registrazione predefinita** è il metodo semplificato per ottenere i criteri dal servizio APP-WE per un'app presente nel dispositivo.

> [!NOTE] 
> La **registrazione predefinita** riconosce i cloud sovrani.

Abilitare la registrazione predefinita seguendo questa procedura:

1. Se l'app integra ADAL o è necessario abilitare l'accesso SSO, [configurare ADAL](#configure-azure-active-directory-authentication-library-adal) seguendo la [configurazione comune di ADAL](#common-adal-configurations) n. 2. In caso contrario, è possibile saltare questo passaggio.
   
2. Abilitare la registrazione predefinita inserendo il valore seguente nel manifesto:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.DefaultMAMServiceEnrollment" android:value="true" />
   ```
   > [!NOTE] 
   > Questa deve essere l'unica integrazione MAM-WE nell'app. Altri tentativi di chiamare le API MAMEnrollmentManager possono determineranno conflitti.

3. Abilitare i criteri MAM richiesti inserendo il valore seguente nel manifesto:
   ```xml 
   <meta-data android:name="com.microsoft.intune.mam.MAMPolicyRequired" android:value="true" />
   ```
   > [!NOTE] 
   > In questo modo, l'utente dovrà scaricare il Portale aziendale nel dispositivo e completare le fasi della registrazione predefinita prima dell'uso.


## <a name="limitations"></a>Limitazioni

### <a name="file-size-limitations"></a>Limitazioni relative alle dimensioni dei file

Per codebase di grandi dimensioni eseguite senza [ProGuard](http://proguard.sourceforge.net/), le limitazioni del formato di file eseguibile Dalvik diventano un problema. In particolare, possono essere previste le limitazioni seguenti:

1. Limite a 65.000 per i campi.
2. Limite a 65.000 per i metodi.

### <a name="policy-enforcement-limitations"></a>Limitazioni relative all'applicazione di criteri

* **Uso di resolver di contenuto**: i criteri di trasferimento o ricezione di Intune possono bloccare interamente o parzialmente l'uso di un resolver di contenuto per accedere al provider di contenuti in un'altra app. Questo comportamento può far sì che i metodi `ContentResolver` restituiscano null o generino un valore di errore. Ad esempio, `openOutputStream` genera `FileNotFoundException` se è bloccato. L'app può determinare se un errore di scrittura dei dati tramite un resolver di contenuto è stato provocato dai criteri (o verrebbe provocato dai criteri) effettuando questa chiamata:
    ```java
    MAMPolicyManager.getPolicy(currentActivity).getIsSaveToLocationAllowed(contentURI);
    ```
    o se non è presente alcuna attività associata

    ```java
    MAMPolicyManager.getPolicy().getIsSaveToLocationAllowed(contentURI);
    ```

    In quest'ultimo caso, è necessario prestare particolare attenzione alle app che supportano le identità multiple per impostare l'identità del thread in modo appropriato (o passare a un'identità esplicita per la chiamata `getPolicy`).

### <a name="exported-services"></a>Servizi esportati

 Il file AndroidManifest.xml incluso in Intune App SDK contiene **MAMNotificationReceiverService**, che deve essere un servizio esportato per consentire al Portale aziendale di inviare notifiche a un'app gestita. Il servizio verifica il chiamante per garantire che l'invio di notifiche sia consentito solo all'app Portale aziendale.

### <a name="reflection-limitations"></a>Limitazioni della reflection
Alcune delle classi di base MAM, ad esempio MAMActivity e MAMDocumentsProvider, contengono metodi basati sulle classi di base Android originali, che usano parametri o tipi restituiti presenti solo al di sopra di determinati livelli API. Per questo motivo, potrebbe non essere sempre possibile usare la reflection per enumerare tutti i metodi dei componenti dell'app. Questa restrizione non è limitata a MAM, ma si applica anche se l'app ha implementato questi metodi delle classi di base Android.

### <a name="robolectric"></a>Robolectric
Il test del comportamento dell'SDK MAM in Robolectric non è supportato. Esistono alcuni problemi noti causati dall'esecuzione dell'SDK MAM in Robolectric dovuti a comportamenti presenti in Robolectric che non simulano in modo accurato i comportamenti di dispositivi reali o emulatori.

Se è necessario testare l'applicazione in Roboelectric, la soluzione alternativa consigliata è spostare la logica di classe dell'applicazione in un file di supporto e creare l'apk per lo unit test con una classe di applicazione che non eredita da MAMApplication.
## <a name="expectations-of-the-sdk-consumer"></a>Aspettative del consumer di SDK

Intune SDK mantiene il contratto fornito dall'API Android, ma è possibile che vengano generate condizioni di errore più frequentemente come conseguenza dell'applicazione dei criteri. Queste procedure consigliate per Android riducono la probabilità di errore:

* Le funzioni di Android SDK che possono restituire Null hanno una maggiore probabilità di essere Null.  Per ridurre al minimo i problemi, assicurarsi che i controlli dei valori Null vengano eseguiti nei punti corretti.

* Le funzionalità che è possibile controllare devono essere controllate tramite le rispettive API di sostituzione MAM.

* Tutte le funzioni derivate devono effettuare chiamate tramite le rispettive versioni delle superclassi.

* Evitare un uso ambiguo di qualsiasi API. L'uso di `Activity.startActivityForResult` senza controllare requestCode causa ad esempio un comportamento anomalo.

## <a name="telemetry"></a>Telemetria

Intune App SDK per Android non controlla la raccolta di dati dall'app. L'applicazione Portale aziendale registra dati generati dal sistema per impostazione predefinita. Questi dati vengono inviati a Microsoft Intune. In base ai criteri Microsoft, non vengono raccolte informazioni personali.

> [!NOTE]
> Se l'utente finale sceglie di non inviare questi dati, deve disattivare la telemetria in Impostazioni nell'app Portale aziendale. Per altre informazioni, vedere [Disattivare la raccolta dati di utilizzo di Microsoft](https://docs.microsoft.com/intune-user-help/turn-off-microsoft-usage-data-collection-android). 

## <a name="recommended-android-best-practices"></a>Procedure consigliate per Android

* Tutti i progetti di libreria devono condividere lo stesso elemento android:package ogni volta che è possibile. Ciò non comporta errori sporadici in fase di esecuzione, ma è esclusivamente un problema in fase di compilazione. Nelle versioni più recenti di Intune App SDK verranno rimossi alcuni aspetti ridondanti.

* Usare gli strumenti di compilazione di Android SDK più recenti.

* Rimuovere tutte le librerie non necessarie e non in uso, ad esempio android.support.v4.
