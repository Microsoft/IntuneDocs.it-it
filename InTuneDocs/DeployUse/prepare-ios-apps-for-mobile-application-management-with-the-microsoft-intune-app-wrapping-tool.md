---
title: Eseguire il wrapping delle app iOS con lo strumento di wrapping delle app di Intune | Microsoft Intune
description: Usare le informazioni in questo argomento per informazioni su come eseguire il wrapping delle app iOS senza modificare il codice dell&quot;app stessa. Preparare le app in modo da applicare i criteri di gestione delle app mobili.
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: oldang
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b25c7d7063ce586bb1cd960534f3e2ed57f6aec4
ms.openlocfilehash: f70a32cf7db4d46f15cdef85e111a8857a1a0215


---

# <a name="prepare-ios-apps-for-mobile-application-management-with-the-intune-app-wrapping-tool"></a>Preparare le app per iOS per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune

Usare lo strumento di wrapping delle app di Microsoft Intune per iOS per modificare il comportamento delle app iOS interne limitandone le funzionalità senza modificarne il codice.

Lo strumento è un'applicazione da riga di comando di macOS che crea un wrapper intorno a un'app. Dopo l'elaborazione è possibile modificare la funzionalità dell'app usando i [criteri di gestione delle applicazioni mobili](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) configurati.

Per scaricare lo strumento, vedere [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) (Strumento di wrapping delle app di Microsoft Intune per iOS).



## <a name="fulfill-the-prerequisites-for-using-the-app-wrapping-tool"></a>Soddisfare i prerequisiti per l'uso dello strumento di wrapping delle app
Vedere [Skype for Business Online: Enable your tenant for modern authentication (Skype per Business Online: abilitazione del tenant per l'autenticazione moderna)](http://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) per altre informazioni sui prerequisiti e su come impostarli.

|Requisito|Altre informazioni|
|---------------|--------------------------------|
|Sistema operativo e set di strumenti supportati|È necessario eseguire lo strumento di wrapping delle app in un computer macOS con OS X 10.8.5 o versioni successive e con il set di strumenti XCode versione 5 o successive.|
|Certificato di firma e profilo di provisioning|È necessario avere un certificato di firma e un profilo di provisioning Apple. Vedere la [documentazione per sviluppatori Apple](https://developer.apple.com/).|
|Elaborazione di un'app con lo strumento per la disposizione testo per app|Le app devono essere sviluppate e firmate dalla società o da un fornitore di software indipendente (ISV). Non è possibile usare questo strumento per elaborare le app dell'Apple Store. L'app deve essere scritta per iOS 8.0 o versioni successive. Il formato delle app deve essere PIE (Position Independent Executable). Per altre informazioni sul formato PIE, vedere la documentazione per sviluppatori di Apple. L'estensione dell'app deve essere infine **app** o **ipa**.|
|App che lo strumento non è in grado di elaborare|App crittografate, non firmate e con attributi di file estesi.|
|Impostazione dei diritti per l'app|Prima di eseguire il wrapping dell'app è necessario impostare diritti per concedere all'app autorizzazioni e funzionalità aggiuntive oltre a quelle generalmente concesse. Per istruzioni, vedere [Impostazione dei diritti delle app](#setting-app-entitlements).|

## <a name="install-the-app-wrapping-tool"></a>Installare lo strumento di wrapping delle app

1.  Scaricare i file per lo strumento di wrapping delle app dal repository Microsoft Intune App Wrapping Tool for iOS [ospitato in GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios), in un computer macOS.

2.  Fare doppio clic su **Microsoft Intune App Wrapping Tool for iOS.dmg**. Verrà visualizzata una finestra con il Contratto di licenza con l'utente finale (EULA). Leggere attentamente il documento.

3. Scegliere **Accetto** per accettare il contratto di licenza e procedere al montaggio del pacchetto nel computer.

4.  Aprire IntuneMAMPackager e salvare i file in una cartella locale nel computer macOS in uso. È ora possibile eseguire lo strumento di wrapping delle app.

## <a name="run-the-app-wrapping-tool"></a>Eseguire lo strumento di wrapping delle app
* Aprire un terminale e passare alla cartella in cui sono stati salvati i file dello strumento di wrapping delle app. Lo strumento eseguibile è denominato IntuneMAMPackager e si trova in IntuneMAMPackager/Contents/MacOS. Eseguire il comando come segue:

    ```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]

    ```

    > [!NOTE]
    > Alcuni parametri sono facoltativi, come illustrato nella tabella seguente.

    **Esempio:** il comando di esempio seguente esegue lo strumento di wrapping delle app per l'app denominata MyApp.ipa. Vengono specificati un profilo di provisioning e l'hash SHA-1. L'app elaborata (MyApp_Wrapped.ipa) viene creata e archiviata nella cartella Desktop dell'utente.

    ```
    ./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true
    ```
    Con lo strumento di wrapping delle app è possibile usare le proprietà della riga di comando seguenti:

|Proprietà|Modo d'uso|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. Il nome del file deve terminare con l'estensione app o ipa. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**|Mostra informazioni d'uso dettagliate per le proprietà della riga di comando disponibili per lo strumento di wrapping delle app.|
|**-v**|(Facoltativo) Mostra messaggi dettagliati nella console.|
|**-e**| (Facoltativo) Usare questo flag per fare in modo che lo strumento di wrapping delle app rimuova i diritti mancanti durante l'elaborazione dell'app. Per altri dettagli, vedere Impostazione dei diritti delle app.|
|**-xe**| (Facoltativo) Visualizza informazioni sulle estensioni iOS nell'app e sui diritti necessari per usarle. Per altri dettagli, vedere Impostazione dei diritti delle app. |
|**-x**| (Facoltativo) `<An array of paths to extension provisioning profiles>`. Usare questa opzione se l'app richiede profili di provisioning estensioni.|
|**-f**|(Facoltativo) `<Path to a plist file specifying arguments.>` Usare questo flag prima del file [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html) se si sceglie di usare il modello plist per specificare le altre proprietà IntuneMAMPackager, come: -i, -o e -p. Vedere Usare un file plist per l'input di argomenti. |
|**-b**|(Facoltativo) Usare -b senza argomento se si vuole che l'applicazione di output con wrapper abbia la stessa versione di bundle dell'app di input (scelta non consigliata). <br/><br/> Usare `-b <custom bundle version>` se si vuole che l'app con wrapper abbia un valore CFBundleVersion personalizzato. Se si sceglie di specificare un valore CFBundleVersion personalizzato, è consigliabile incrementare il componente meno significativo del valore CFBundleVersion dell'app nativa, ad esempio 1.0.0 -> 1.0.1. |

### <a name="use-a-plist-to-input-arguments"></a>Usare un file plist per l'input di argomenti
Un modo semplice per eseguire lo strumento di wrapping delle app è l'inserimento di tutti gli argomenti del comando in un file [plist](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/PropertyLists/Introduction/Introduction.html). Il formato plist è simile al formato XML e consente di immettere gli argomenti della riga di comando mediante un'interfaccia di tipo modulo.

Nella cartella IntuneMAMPackager/Contents/MacOS aprire `Parameters.plist`, un modello di file plist vuoto, con un editor di testo o Xcode. Immettere argomenti per le chiavi seguenti:

| Chiave plist |  Valore predefinito| Note |
|------------------|--------------|-----|
| Input Application Package Path  |empty| Uguale a -i|
| Output Application Package Path |empty| Uguale a -o|
| Provisioning Profile Path |empty| Uguale a -p|
| SHA-1 Certificate Hash |empty| Uguale a -c|
| Verbose Enabled |false| Uguale a -v|
| Remove Missing Entitlements | false| Uguale a -c|
| Prevent Default Build |false | Equivalente all'uso di -b senza argomenti|
|Build String Override | empty| Versione personalizzata di CFBundleVersion dell'app di output con wrapper |
|Extension Provisioning Profile Paths | empty| Matrice di profili di provisioning estensioni per l'app.


Eseguire IntuneMAMPackager con il file plist come unico argomento:

```
./IntuneMAMPackager –f Parameters.plist
```

* Al termine dell'elaborazione verrà visualizzato un messaggio che indica che il wrapping dell'applicazione è stato completato.

    Se si verifica un errore, vedere [Messaggi di errore](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) per altre informazioni.

*   L'app di cui è stato eseguito il wrapping viene salvata nella cartella di output specificata in precedenza. È ora possibile caricare l'app in [wit_nextref](../includes/wit_nextref_md.md) e associarla ai criteri di gestione delle applicazioni per dispositivi mobili.

    > [!IMPORTANT]
    > Quando si carica un'app con wrapper è possibile provare a eseguire l'aggiornamento di una versione precedente (con wrapper o nativa) se tale versione era già stata distribuita a Intune. In caso di errore, caricare l'app come nuova app ed eliminare la versione precedente.

    È ora possibile distribuire l'app ai gruppi [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e l'app verrà eseguita nel dispositivo con le restrizioni specificate.

## <a name="error-messages-and-log-files"></a>Messaggi di errore e file di log
Usare le informazioni seguenti per risolvere i problemi dello strumento per la disposizione testo per app.

### <a name="error-messages"></a>Messaggi di errore
Se lo strumento di wrapping delle app non viene eseguito correttamente, nella console viene visualizzato uno dei messaggi di errore seguenti:

|Messaggio di errore|Altre informazioni|
|-----------------|--------------------|
|È necessario specificare un profilo di provisioning iOS valido.|Il profilo di provisioning potrebbe non essere valido. Verificare di avere le autorizzazioni corrette per i dispositivi e che il profilo sia indirizzato correttamente all'ambiente di sviluppo o distribuzione. È anche possibile che il profilo di provisioning sia scaduto.|
|Specificare un nome dell'applicazione di input valido.|Verificare che il nome dell'applicazione di input specificato sia corretto.|
|Specificare un percorso dell'applicazione di output valido.|Verificare che il percorso dell'applicazione di output specificato esista e sia corretto.|
|Specificare un profilo di provisioning di input valido.|Verificare di aver fornito un nome e un'estensione per il profilo di provisioning validi. È possibile che manchino i diritti per il profilo di provisioning o che non sia stata inclusa l'opzione -p della riga di comando.|
|L'applicazione di input specificata non è stata trovata. Specificare un nome e un percorso dell'applicazione di input validi.|Verificare che il percorso dell'app di input sia valido e che esista. Verificare che l'app di input sia presente in tale percorso.|
|Il file del profilo di provisioning di input specificato non è stato trovato. Specificare un file del profilo di provisioning di input valido.|Verificare che il percorso del file del profilo di provisioning di input sia valido e che il file specificato sia presente in tale percorso.|
|La cartella dell'applicazione di output specificata non è stata trovata. Specificare un percorso dell'applicazione di output valido.|Verificare che il percorso di output specificato sia valido e che esista.|
|L'app di output non ha l'estensione **ipa**.|Solo le app con estensione **app** e **ipa** vengono accettate dallo strumento di wrapping delle app. Verificare che l'estensione del file di output sia valida.|
|È stato specificato un certificato di firma non valido. Specificare un certificato di firma Apple valido.|Verificare di aver scaricato il certificato di firma corretto dal portale per sviluppatori di Apple. Il certificato potrebbe essere scaduto o non includere una chiave pubblica o privata. Se il certificato e il profilo di provisioning Apple possono essere usati per firmare correttamente un'app all'interno di Xcode, saranno validi anche per lo strumento di wrapping delle app.|
|L'applicazione di input specificata non è valida. Specificare un'applicazione valida.|Verificare di avere un'applicazione iOS valida compilata come file APP o IPA.|
|L'applicazione di input specificata è crittografata. Specificare un'applicazione non crittografata valida.|Lo strumento di wrapping delle app non supporta le app crittografate. Fornire un'app non crittografata.|
|Il formato dell'applicazione di input specificata non è PIE (Position Independent Executable). Specificare un'applicazione valida in formato PIE.|Le app PIE (Position Independent Executable) possono essere caricate in un indirizzo di memoria casuale quando vengono eseguite, con importanti vantaggi per la sicurezza. Per altre informazioni sui vantaggi per la sicurezza, vedere la documentazione per sviluppatori di Apple.|
|È già stato eseguito il wrapping dell'app di input specificata. Specificare un'applicazione valida di cui non sia stato eseguito il wrapping.|Non è possibile elaborare un'app che sia già stata elaborata dallo strumento. Se si vuole elaborare nuovamente un'app, eseguire lo strumento usando la versione originale dell'app.|
|L'applicazione di input specificata non è firmata. Specificare un'applicazione firmata valida.|Lo strumento di wrapping delle app richiede che le app siano firmate. Consultare la documentazione per sviluppatori per informazioni su come firmare un'app di cui è stato eseguito il wrapping.|
|Il formato dell'applicazione di input specificata deve essere IPA o APP.|Solo le estensioni APP e IPA sono accettate dallo strumento di wrapping delle app. Verificare che il file di input abbia un'estensione valida e che sia stato compilato come file APP o IPA.|
|È già stato eseguito il wrapping dell'app di input specificata e la versione del modello di criteri è la più recente.|Lo strumento di wrapping delle app non eseguirà nuovamente il wrapping di un'app esistente di cui è già stato eseguito il wrapping con la versione più recente del modello di criteri.|
|AVVISO: non è stato specificato un hash SHA1 del certificato. Verificare che l'applicazione di cui è stato eseguito il wrapping è firmata prima della distribuzione.|Verificare di avere specificato un hash SHA1 valido dopo il flag della riga di comando -c. |

### <a name="log-files-for-the-app-wrapping-tool"></a>File di log per lo strumento di wrapping delle app
Le app di cui è stato eseguito il wrapping tramite lo strumento di wrapping delle app generano log che vengono scritti nella console del dispositivo client iOS. Queste informazioni sono utili quando si riscontrano problemi con l'applicazione ed è necessario determinare se il problema è correlato allo strumento di wrapping delle app. Per recuperare queste informazioni, usare i passaggi seguenti:

1.  Riprodurre il problema eseguendo l'app.

2.  Raccogliere l'output della console seguendo le istruzioni di Apple fornite nell'articolo relativo al [debug delle app iOS distribuite](https://developer.apple.com/library/ios/qa/qa1747/_index.html).

3.  Filtrare i log salvati per l'output delle restrizioni dell'app immettendo lo script seguente nella console:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    È possibile inviare i log filtrati a Microsoft.

    > [!NOTE]
    > Nel file di log, l'elemento 'build version' rappresenta la versione build di Xcode.

    Anche nelle app di cui è stato eseguito il wrapping sarà presente un'opzione per inviare i log direttamente dal dispositivo tramite posta elettronica dopo l'arresto anomalo dell'app. Il responsabile potrà analizzare i log inviati dagli utenti e se necessario inoltrarli a Microsoft.


### <a name="certificate-provisioning-profile-and-authentication-requirements"></a>Certificato, profilo di provisioning e requisiti di autenticazione

Lo strumento di wrapping delle app include alcuni requisiti che devono essere soddisfatti per garantire la completa funzionalità.

|Requisito|Dettagli|
|---------------|-----------|
|Profilo di provisioning|Verificare che il profilo di provisioning sia valido prima di includerlo. Lo strumento di wrapping delle app non controlla se il profilo di provisioning è scaduto durante l'elaborazione di un'app iOS. Se viene specificato un profilo di provisioning scaduto, lo strumento di wrapping delle app includerà il profilo di provisioning scaduto e il problema si scoprirà solo durante l'installazione dell'app nel dispositivo iOS, che non riuscirà.|
|Certificato|Verificare che il certificato sia valido prima di specificarlo. Lo strumento non verifica se un certificato è scaduto durante l'elaborazione delle app iOS. Se viene fornito l'hash per un certificato scaduto, lo strumento elaborerà e firmerà l'app, ma l'installazione nei dispositivi non riuscirà.<br /><br />Verificare che il certificato fornito per la firma dell'applicazione in pacchetto abbia una corrispondenza nel profilo di provisioning. Lo strumento non verifica se il profilo di provisioning ha una corrispondenza per il certificato fornito per la firma dell'applicazione con wrapper.|
|Autenticazione|Per usare la crittografia, è necessario che il dispositivo disponga di un PIN. Se si tocca la barra di stato nei dispositivi in cui è stata distribuita un'app di cui è stato eseguito il wrapping, verrà richiesta di nuovo l'autenticazione con [wit_nextref](../includes/wit_nextref_md.md). I criteri predefiniti per un'app con wrapper prevedono l'*autenticazione al riavvio*. iOS gestisce qualsiasi notifica esterna, come una chiamata telefonica, chiudendo e riavviando l'app.


## <a name="setting-app-entitlements"></a>Impostazione dei diritti delle app
Prima di eseguire il wrapping dell'app, è possibile assegnare *diritti* per concedere all'app autorizzazioni e funzionalità aggiuntive superiori alle operazioni normalmente eseguibili da un'app. Durante la firma del codice viene usato un *file dei diritti* per specificare le autorizzazioni speciali all'interno dell'app, ad esempio l'accesso a un portachiavi condiviso. I servizi di app specifici, denominati *funzionalità*, vengono abilitati all'interno di Xcode durante lo sviluppo delle app. Una volta abilitate, le funzionalità vengono riportate nel file dei diritti. Per altre informazioni su funzionalità e diritti, vedere l'articolo relativo all'[aggiunta di funzionalità](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) nella libreria per gli sviluppatori iOS. Per un elenco completo delle funzionalità supportate, vedere [Funzionalità supportate](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html).

### <a name="supported-capabilities-for-the-app-wrapping-tool-for-ios"></a>Funzionalità supportate per lo strumento per la disposizione testo per app per iOS

|Funzionalità|Descrizione|Procedura consigliata|
|--------------|---------------|------------------------|
|Gruppi di app|Usare i gruppi di app per consentire a più app di accedere a contenitori condivisi e favorire la comunicazione interprocesso tra app.<br /><br />Per abilitare i gruppi di app, aprire il riquadro **Capabilities** (Funzionalità) e fare clic su **ON** in **App Groups** (Gruppi di app). È possibile aggiungere gruppi di app o selezionare gruppi esistenti.|Quando si usano gruppi di app, usare la notazione DNS inversa:<br /><br />*group.com.companyName.AppGroup*|
|Modalità di background|L'abilitazione delle modalità di background consente all'app iOS di continuare l'esecuzione in background.||
|Protezione dati|La protezione dei dati aggiunge un livello di sicurezza ai file archiviati su disco dall'app iOS. La protezione dei dati usa l'hardware di crittografia incorporato presente in dispositivi specifici per archiviare i file in formato crittografato su disco. È necessario eseguire il provisioning dell'app per usare la protezione dei dati.||
|Acquisto in-app|L'acquisto in-app incorpora uno store direttamente nell'app, consentendo di connettersi allo store ed elaborare in modo sicuro i pagamenti eseguiti dall'utente. È possibile usare l'acquisto in-app per riscuotere pagamenti per funzionalità avanzate o contenuti aggiuntivi utilizzabili dall'app.||
|Condivisione del portachiavi|L'attivazione della condivisione del portachiavi consente all'app di condividere le password nel portachiavi con altre app sviluppate dal team.|Quando si usa la condivisione del portachiavi, usare la notazione DNS inversa:<br /><br />*com.companyName.KeychainGroup*|
|VPN personale|Abilitare la VPN personale per consentire all'app di creare e controllare una configurazione VPN di sistema personalizzata usando il framework di estensione di rete.||
|Notifiche push|Il servizio Apple Push Notification (APN) consente a un'app che non è in esecuzione in primo piano di notificare all'utente la disponibilità di informazioni.|Per consentire il funzionamento delle notifiche push, è necessario usare un profilo di provisioning specifico dell'app.<br /><br />Seguire i passaggi indicati nella [documentazione per sviluppatori Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html).|
|Configurazione degli accessori wireless|L'abilitazione della configurazione degli accessori wireless aggiunge il framework degli accessori esterni al progetto e consente all'app di configurare accessori MFi Wi-Fi.||

### <a name="steps-to-enable-entitlements"></a>Passaggi per abilitare i diritti

1.  Abilitare le funzionalità nell'app:

    1.  In Xcode passare alla destinazione dell'app e fare clic su **Capabilities** (Funzionalità).

    2.  Attivare le funzionalità appropriate. Per informazioni dettagliate su ogni funzionalità e su come determinare i valori corretti, vedere l'articolo relativo all'[aggiunta di funzionalità](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) nella libreria per sviluppatori iOS.

    3.  Prendere nota di eventuali ID creati durante il processo.

    4.  Creare e firmare l'app di cui eseguire il wrapping.

2.  Abilitare i diritti nel profilo di provisioning:

    1.  Accedere all'area membri degli sviluppatori Apple.

    2.  Creare un profilo di provisioning per l'app. Per istruzioni, vedere [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/) (Come ottenere i prerequisiti per lo strumento per la disposizione testo per app di Intune per iOS).

    3.  Nel profilo di provisioning abilitare gli stessi diritti dell'app. È necessario indicare gli stessi ID specificati durante lo sviluppo dell'app.

    4.  Completare la configurazione guidata del profilo di provisioning e scaricare il file.

3.  Assicurarsi di aver soddisfatto tutti i prerequisiti e quindi eseguire il wrapping dell'app.

### <a name="troubleshooting-common-errors-with-entitlements"></a>Risoluzione di problemi comuni relativi ai diritti
Se lo strumento di wrapping delle app per iOS visualizza un errore relativo ai diritti, provare le procedure seguenti per la risoluzione dei problemi.

|Problema|Causa|Risoluzione|
|---------|---------|--------------|
|Impossibile analizzare i diritti generati dall'applicazione di input.|Lo strumento per la disposizione testo per app non è in grado di leggere il file dei diritti che è stato estratto dall'app. Il file dei diritti potrebbe non essere nel formato corretto.|Esaminare il file dei diritti per l'app. Le istruzioni seguenti spiegano come eseguire questa operazione. Quando si esamina il file dei diritti, verificare se sono presenti errori di sintassi. Il file deve essere in formato XML.|
|I diritti non sono presenti nel profilo di provisioning (sono elencati i diritti mancanti). Ricreare il pacchetto dell'app con un profilo di provisioning a cui sono assegnati tali diritti.|I diritti abilitati nel profilo di provisioning e le funzionalità abilitate nell'app non corrispondono. Questa mancata corrispondenza vale anche per gli ID associati a particolari funzionalità, ad esempio gruppi di app, accesso al portachiavi e così via.|In genere è possibile creare un nuovo profilo di provisioning che abilita le stesse funzionalità dell'app. In caso di mancata corrispondenza tra gli ID del profilo e dell'app, lo strumento per la disposizione testo per app sostituirà gli ID, se è in grado di eseguire l'operazione. Se questo errore viene ancora visualizzato dopo aver creato un nuovo profilo di provisioning, è possibile provare a rimuovere i diritti dall'app usando il parametro -e (vedere la sezione Uso del parametro -e per rimuovere diritti da un'app).|

### <a name="finding-the-existing-entitlements-of-a-signed-app"></a>Trovare i diritti esistenti di un'app firmata
Per rivedere i diritti esistenti di un'app firmata e di un profilo di provisioning:

1.  Trovare il file con estensione IPA e modificare l'estensione in ZIP.

2.  Espandere il file con estensione ZIP. Verrà generata una cartella Payload contenente il bundle .app.

3.  Usare lo strumento codesign per verificare i diritti nel bundle con estensione app, dove `YourApp.app` è il nome effettivo del bundle con estensione app:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```

4.  Usare lo strumento security per verificare i diritti del profilo di provisioning incorporato dell'app, dove `YourApp.app` è il nome effettivo del bundle con estensione app.

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```

### <a name="remove-entitlements-from-an-app-by-using-the-e-parameter"></a>Rimuovere diritti da un'app con il parametro -e
Questo comando rimuove tutte le funzionalità abilitate nell'app che non sono presenti nel file dei diritti. Se si rimuovono le funzionalità usate dall'app si possono verificare interruzioni dell'app. Ad esempio, è possibile rimuovere le funzionalità mancanti in un'app prodotta dal fornitore che ha tutte le funzionalità per impostazione predefinita.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## <a name="security-and-privacy-for-the-app-wrapping-tool"></a>Sicurezza e privacy per lo strumento di wrapping delle app
Quando si usa lo strumento di wrapping delle app, adottare le procedure consigliate seguenti per la sicurezza e la privacy.

-   Il certificato di firma, il profilo di provisioning e l'app line-of-business specificati devono risiedere nello stesso computer macOS usato per eseguire lo strumento di wrapping delle app. Se i file si trovano in un percorso UNC, assicurarsi che siano accessibili dal computer macOS. Il percorso deve essere protetto tramite firma IPsec o SMB.

    L'applicazione di cui è stato eseguito il wrapping importata nella console di [wit_nextref](../includes/wit_nextref_md.md) deve risiedere nello stesso computer in cui viene eseguito lo strumento. Se il file si trova in un percorso UNC, assicurarsi che sia accessibile dal computer che esegue la console di [wit_nextref](../includes/wit_nextref_md.md). Il percorso deve essere protetto tramite firma IPsec o SMB.

-   L'ambiente in cui lo strumento di wrapping delle app viene scaricato dal repository GitHub deve essere protetto tramite firma IPSec o SMB.

-   L'app elaborata deve provenire da una fonte attendibile per garantire la protezione dagli attacchi.

-   Assicurarsi che la cartella di output specificata nello strumento di wrapping delle app sia protetta, soprattutto se è una cartella remota.

-   Le app iOS che includono una finestra di dialogo per il caricamento dei file possono consentire agli utenti di eludere le restrizioni per le operazioni taglia, copia e incolla applicate all'app. Ad esempio, un utente potrebbe usare la finestra di dialogo per il caricamento dei file per caricare una schermata dei dati dell'app.

-   Quando si monitora la cartella dei documenti nel dispositivo dall'app di cui è stato eseguito il wrapping, potrebbe essere visualizzata una cartella denominata .msftintuneapplauncher. Se questo file viene modificato o eliminato, ciò potrebbe influire sul corretto funzionamento delle app con restrizioni.

### <a name="see-also"></a>Vedere anche
- [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Usare l'SDK per abilitare le app per la gestione delle applicazioni mobili](use-the-sdk-to-enable-apps-for-mobile-application-management.md)



<!--HONumber=Nov16_HO1-->


