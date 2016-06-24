---
# required metadata

title: Preparare le app per iOS per la gestione con lo strumento per la disposizione testo per app | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Preparare le app per iOS per la gestione di applicazioni per dispositivi mobili con lo strumento per la disposizione testo per app di Intune
Usare lo **strumento per la disposizione testo per app di Microsoft Intune per iOS** per modificare il comportamento delle app iOS interne in modo da limitare le funzionalità dell'app senza modificare il codice dell'app stessa.

Lo strumento è un'applicazione da riga di comando di Mac OS che crea un 'wrapper' intorno a un'app. Dopo l'elaborazione è possibile modificare la funzionalità dell'app usando i [criteri di gestione dell'applicazione per dispositivi mobili](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) configurati.

Per scaricare lo strumento, vedere l'articolo relativo allo [strumento per la disposizione testo per app di Microsoft Intune per iOS](http://www.microsoft.com/en-us/download/details.aspx?id=45218)..

## Passaggio 1: Soddisfare i prerequisiti per l'uso dello strumento per la disposizione testo per app

|Requisito|Altre informazioni|
|---------------|--------------------------------|
|Sistema operativo e set di strumenti supportati|È necessario eseguire lo strumento di wrapping delle app in un computer Mac che esegue OS X 10.8.5 o versioni successive, con il set di strumenti XCode versione 5 o versioni successive.|
|Certificato di firma e profilo di provisioning|È necessario avere un certificato di firma e un profilo di provisioning Apple. Vedere la [documentazione per sviluppatori Apple](https://developer.apple.com/)..|
|Elaborazione di un'app con lo strumento per la disposizione testo per app|Le app devono essere sviluppate e firmate dalla società o da un fornitore di software indipendente (ISV). Non è possibile usare questo strumento per elaborare le app dell'Apple Store. L'app deve essere scritta per iOS 7.0 o versioni successive. Il formato delle app deve essere PIE (Position Independent Executable). Per altre informazioni sul formato PIE, vedere la documentazione per sviluppatori di Apple. Il formao dell'estensione dell'app deve essere **.app** o **.ipa**.|
|App che lo strumento per la disposizione testo non è in grado di elaborare|App crittografate, non firmate e con attributi di file estesi.|
|App che usano Azure Active Directory Library (ADAL)|Se l'app usa ADAL, deve includere una versione ADAL superiore o uguale a 1.0.2 e lo sviluppatore deve concedere accesso app alla risorsa di gestione delle applicazioni per dispositivi mobili Intune.<br /><br />Per informazioni dettagliate sull'uso di ADAL, vedere [Informazioni per le app che usano Azure Active Directory Library](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#information-for-apps-that-use-the-azure-active-directory-library) in questo articolo.|
|Impostazione dei diritti per l'app|È necessario impostare diritti per concedere all'app autorizzazioni e funzionalità aggiuntive oltre a quelle generalmente concesse, prima di eseguire il wrapping dell'app. Per istruzioni, vedere [Impostazione dei diritti delle app](#setting-app-entitlements).|

## Passaggio 2: Installare lo strumento per la disposizione testo per app

1.  Dalla pagina dello **strumento per la disposizione testo per app di Microsoft Intune per iOS** nell'[Area download Microsoft](https://www.microsoft.com/download/details.aspx?id=45218), scaricare il file di installazione dello strumento in un computer Mac.

2.  Nel computer Mac fare doppio clic sul file di installazione **Microsoft Intune App Wrapping Tool for iOS.dmg**..

3.  Fare clic su **Accetto** per accettare il contratto di licenza con l'utente finale. Il programma di installazione verrà montato e visualizzato nel computer Mac.

4.  Aprire il programma di installazione e copiare i file visualizzati in una nuova cartella nel computer Mac. È ora possibile disconnettere l'unità del programma di installazione montata.

    È ora possibile eseguire lo strumento di wrapping delle app.

## Passaggio 3: Eseguire lo strumento per la disposizione testo per app

1.  Nel computer Mac, aprire una finestra Terminale e spostarsi nella cartella in cui è stato salvato il file. Poiché il file eseguibile si trova all'interno del pacchetto, è necessario eseguire il comando come segue:
```
    ./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -a <client ID of input app> -r <reply URI of input app> -v true
```
    > [!NOTE]
    > Some parameters are optional as shown in the table below.

    **Example:** The following example command runs the app wrapping tool on an app named **MyApp.ipa**. A provisioning profile and SHA-1 hash are specified. The processed app is created and stored in the **/users/myadmin/Documents** on the Mac computer.

    ```
    /users/myadmin/Downloads/IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager -i /users/myadmin/Downloads/MyApp.ipa -o /users/myadmin/Documents/MyApp_Wrapped.ipa -p /users/myadmin/Downloads/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB –a 20e1cd0d-268e-4308-9583-02ae97dd353e –r https://contoso/ -v true
    ```
    You can use the following command line properties with the app wrapping tool:

|Proprietà|Altre informazioni|
  |------------|--------------------|
  |**-h**|Visualizza le proprietà della riga di comando disponibili per lo strumento di wrapping delle app:|
  |**-i**|Specifica il percorso e il nome file dell'app di input.|
  |**-o**|Specifica il percorso in cui salvare l'app elaborata.|
  |**-p**|Specifica il percorso del profilo di provisioning per le app iOS.|
  |**-c**|Specifica l'hash SHA1 del certificato di firma.|
  |**-a**|ID client dell'app di input (in formato GUID) se l'app usa librerie di Azure Active Directory (facoltativo).|
  |**-r**|URI di reindirizzamento dell'app di input se l'app usa librerie di Azure Active Directory (facoltativo).|
  |**-v**|Messaggi dettagliati di output alla console (facoltativo).|

2. Al termine dell'elaborazione, verrà visualizzato un messaggio simile al seguente: **Wrapping dell'applicazione completato** .

    Se si verifica un errore, vedere [Messaggi di errore](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md#error-messages) per altre informazioni.

3.  L'app di cui è stato eseguito il wrapping viene salvata nella cartella di output specificata in precedenza. È ora possibile caricare l'app in [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e associarla ai criteri di gestione delle applicazioni mobili.

    > [!IMPORTANT]
    > È necessario caricare l'app come una nuova app. Non è possibile aggiornare una versione precedente dell'app di cui non è stato eseguito il wrapping.

    È ora possibile distribuire l'app ai gruppi [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e l'app verrà ora eseguita sul dispositivo con le restrizioni specificate.

## Messaggi di errore e file di log
Usare le informazioni seguenti per risolvere i problemi dello strumento per la disposizione testo per app.

### Messaggi di errore
Se lo strumento di wrapping delle app non viene eseguito correttamente, verrà visualizzato uno dei messaggi di errore seguenti:

|Messaggio di errore|Altre informazioni|
|-----------------|--------------------|
|È necessario specificare un profilo di provisioning iOS valido.|Il profilo di provisioning potrebbe non essere valido. Verificare di avere le autorizzazioni corrette per i dispositivi e che il profilo sia stato indirizzato correttamente all'ambiente di sviluppo o distribuzione. È anche possibile che il profilo di provisioning sia scaduto.|
|Specificare un nome dell'applicazione di input valido.|Verificare che il nome dell'applicazione di input specificato sia corretto.|
|Specificare un percorso dell'applicazione di output valido.|Verificare che il percorso dell'applicazione di output specificato esista e sia corretto.|
|Specificare un profilo di provisioning di input valido.|Verificare di aver fornito un nome e un'estensione per il profilo di provisioning validi. È possibile che manchino i diritti per il profilo di provisioning o che non sia stata inclusa l'opzione **–p** della riga di comando.|
|L'applicazione di input specificata non è stata trovata. Specificare un nome e un percorso dell'applicazione di input validi.|Verificare che il percorso dell'app di input sia valido e che esista. Verificare che l'app di input sia presente in tale percorso.|
|Il file del profilo di provisioning di input specificato non è stato trovato. Specificare un file del profilo di provisioning di input valido.|Verificare che il percorso del file del profilo di provisioning di input sia valido e che il file specificato sia presente in tale percorso.|
|La cartella dell'applicazione di output specificata non è stata trovata. Specificare un percorso dell'applicazione di output valido.|Verificare che il percorso di output specificato sia valido e che esista.|
|L'app di output non ha l'estensione IPA.|Solo le app con estensione **APP** e **IPA** vengono accettate dallo strumento di wrapping delle app. Verificare che l'estensione del file di output sia valida.|
|È stato specificato un certificato di firma non valido. Specificare un certificato di firma Apple valido.|Verificare di aver scaricato il certificato di firma corretto dal portale per sviluppatori di Apple. È anche possibile che il certificato sia scaduto. Se il certificato e il profilo di provisioning Apple possono essere usati per firmare correttamente un'app all'interno di Xcode, saranno validi anche per lo strumento di wrapping delle app.|
|L'applicazione di input specificata non è valida. Specificare un'applicazione valida.|Verificare di avere un'applicazione iOS valida compilata come file APP o IPA.|
|L'applicazione di input specificata è crittografata. Specificare un'applicazione non crittografata valida.|Lo strumento di wrapping delle app non supporta le app crittografate. Specificare un'app non crittografata.|
|Il formato dell'applicazione di input specificata non è PIE (Position Independent Executable). Specificare un'applicazione valida in formato PIE.|Le app PIE (Position Independent Executable) possono essere caricate in un indirizzo di memoria casuale quando vengono eseguite con importanti vantaggi per la sicurezza. Per altre informazioni, vedere la documentazione per sviluppatori di Apple.|
|È già stato eseguito il wrapping dell'app di input specificata. Specificare un'applicazione valida di cui non sia stato eseguito il wrapping.|Non è possibile elaborare un'app che sia già stata elaborata dallo strumento. Se si vuole elaborare nuovamente un'app, eseguire lo strumento usando la versione originale dell'app.|
|L'applicazione di input specificata non è firmata. Specificare un'applicazione firmata valida.|Lo strumento di wrapping delle app richiede che le app siano firmate. Consultare la documentazione per sviluppatori per informazioni su come firmare un'app di cui è stato eseguito il wrapping.|
|Il formato dell'applicazione di input specificata deve essere IPA o APP.|Solo le estensioni APP e IPA sono accettate dallo strumento di wrapping delle app. Verificare che il file di input abbia un'estensione valida e che sia stato compilato come file APP o IPA.|
|È già stato eseguito il wrapping dell'app di input specificata e la versione del modello di criteri è la più recente.|Lo strumento di wrapping delle app non eseguirà nuovamente il wrapping di un'app esistente di cui è già stato eseguito il wrapping con la versione più recente del modello di criteri.|
|L'ID client di Azure Active Directory specificato non è un GUID corretto. Specificare un ID client valido.|Quando si usa il parametro ID client, verificare di aver fornito un ID client valido in formato GUID.|
|L'URI di risposta di Azure Active Directory specificato non è un URI corretto. Specificare un URI di risposta valido.|Quando si usa la proprietà della riga di comando per l'URI di risposta, verificare di aver fornito un URI di risposta valido.|
|AVVISO: non è stato specificato un hash SHA1 del certificato. Verificare che l'applicazione di cui è stato eseguito il wrapping è firmata prima della distribuzione.|Verificare di avere specificato un hash SHA valido (usando la proprietà **–c** della riga di comando).|

### File di log per lo strumento di wrapping delle app
Le app di cui è stato eseguito il wrapping tramite lo strumento di wrapping delle app generano dei log che vengono scritti nella console del dispositivo client iOS. Queste informazioni sono utili nelle situazioni in cui si sono verificati problemi con l'applicazione ed è necessario diagnosticare se il problema è correlato allo strumento di wrapping delle app. Per recuperare queste informazioni, usare i passaggi seguenti:

1.  Riprodurre il problema eseguendo l'app.

2.  Raccogliere l'output della console seguendo le istruzioni di Apple fornite nell'articolo relativo al [debug delle app iOS distribuite](https://developer.apple.com/library/ios/qa/qa1747/_index.html)..

3.  Filtrare i log salvati per l'output delle restrizioni dell'app immettendo lo script seguente nella console:

    ```
    grep “IntuneAppRestrictions” <text file containing console output> > <required filtered log file name>
    ```
    È possibile inviare i log filtrati a Microsoft.

    > [!NOTE]
    > Nel file di log, l'elemento 'build version' rappresenta la versione build di Xcode.

    Anche nelle app di cui è stato eseguito il wrapping sarà presente un'opzione per inviare i log direttamente dal dispositivo tramite posta elettronica dopo l'arresto anomalo dell'app. Gli utenti potranno inviare il log a un responsabile per l'analisi e inoltrarlo a Microsoft se necessario.

## Informazioni per le app che usano Azure Active Directory Library
Le informazioni contenute in questa sezione si applicano solo alle app che usano Azure Active Directory Library (ADAL). Se non si è sicuri se l'app usa questa libreria, contattare lo sviluppatore dell'app.

L'app deve includere una versione di ADAL maggiore o uguale a 1.0.2.

Per le app che usano ADAL, devono verificarsi le condizioni seguenti:

-   L'app deve includere una versione ADAL superiore o uguale alla versione 1.0.2

-   Lo sviluppatore deve concedere all'app l'accesso alla risorsa di gestione delle applicazioni per dispositivi mobili di Intune, come descritto in [Passaggi da seguire per le app che usano ADAL](#steps-to-follow-for-apps-that-use-adal)..

### Panoramica degli identificatori che è necessario ottenere
Le app che usano ADAL devono essere registrate tramite il portale di gestione di Azure per ottenere due identificatori univoci per le app:

|Identificatore|Altre informazioni|Valore predefinito|
|--------------|--------------------|-----------------|
|**ID client**|Dopo la registrazione con Azure Active Directory per ogni app viene generato un identificatore GUID univoco.<br /><br />Se si conosce l'ID client specifico dell'app, è possibile specificare questo valore. In caso contrario, usare il valore predefinito.|6c7e8096-f593-4d72-807f-a5f86dcc9c77|
|**URI di reindirizzamento**|Valore URI che gli sviluppatori possono fornire quando si registra l'app con Azure Active Directory per assicurarsi che vengano restituiti i token di autenticazione specifici di tale endpoint.<br /><br />L'URI di reindirizzamento rappresenta un parametro facoltativo per lo strumento di wrapping delle app. Se non viene specificato, verrà usato un URI predefinito.|urn:ietf:wg:oauth:2.0:oob|


### Passaggi da seguire per le app che usano ADAL

1.  Per identificare i valori necessari, consultare [Panoramica degli identificatori che è necessario ottenere](#overview-of-identifiers-you-need-to-get).

2.  Configurare l'accesso alla gestione delle applicazioni mobili in Azure Active Directory eseguendo le operazioni seguenti:

    1. Accedere a un account di Azure Active Directory esistente nel portale di gestione di Azure.

    2.  Fare clic su **Registrazione applicazione LOB esistente** in Azure Active Directory.

    3.  Nella sezione per la configurazione scegliere **Configura l'accesso ad API Web di altre applicazioni**..

    4.  Nella sezione **Autorizzazioni per altre applicazioni** scegliere **Gestione di applicazioni mobili Intune** dal primo elenco a discesa..

        Ora è possibile usare l'ID client dell'app nello strumento per la disposizione testo per app. L'ID client dell'app è disponibile nel portale di gestione di Azure Active Directory, come descritto nella sezione [Panoramica degli identificatori che è necessario ottenere](#overview-of-identifiers-you-need-to-get).

3.  Usare i valori **Client-ID** (tramite la proprietà **–a**) e **Redirect-URI** come proprietà della riga di comando nello strumento per la disposizione testo per app. Se non si hanno a disposizione questi valori, verranno usati i valori predefiniti. È necessario specificare entrambi i valori, altrimenti l'utente finale non potrà autenticare correttamente l'app elaborata.

### Certificato, profilo di provisioning e requisiti di autenticazione

|Requisito|Dettagli|
|---------------|-----------|
|Profilo di provisioning|**Verificare che il profilo di provisioning sia valido prima di includerlo**: lo strumento per la disposizione testo per app non controlla se il profilo di provisioning è scaduto durante l'elaborazione di un'app per iOS. Se viene specificato un profilo di provisioning scaduto, lo strumento di wrapping delle app includerà il profilo di provisioning scaduto e il problema si scoprirà solo durante l'installazione dell'app nel dispositivo iOS, che non riuscirà.|
|Certificato|**Verificare che il certificato sia valido prima di specificarlo**: lo strumento non controlla se un certificato è scaduto durante l'elaborazione delle app iOS. Se viene fornito l'hash per un certificato scaduto, lo strumento elaborerà e firmerà l'app, ma l'installazione nei dispositivi non riuscirà.<br /><br />**Verificare che il certificato fornito per firmare l'applicazione compressa abbia una corrispondenza nel profilo di provisioning**: lo strumento non esegue la convalida se il profilo di provisioning ha una corrispondenza per il certificato fornito per la firma dell'applicazione di cui è stata eseguita la disposizione testo.|
|Authentication|Per usare la crittografia, è necessario impostare un PIN per il dispositivo. Se nei dispositivi in cui è stata distribuita un'applicazione di cui è stato eseguito il wrapping si tocca la barra di stato, verrò richiesto di eseguire di nuovo l'autenticazione con [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. I criteri predefiniti per un'applicazione di cui è stata eseguita la disposizione testo prevedono l'*autenticazione al riavvio*. iOS gestisce qualsiasi notifica esterna, ad esempio una chiamata telefonica, come se chiudesse l'app e la riavviasse.<br /><br />Il primo utente che accede a un'app di cui è stato eseguito il wrapping dello stesso autore viene memorizzato nella cache. A questo punto, solo tale utente potrà accedere all'app. Per reimpostare l'utente, annullare la registrazione del dispositivo e quindi rieseguirla.|

### Risoluzione dei problemi e note tecniche su ADAL

-   Se viene trovata alcuna risorsa ADAL, lo strumento includerà la libreria ADAL dinamica. Lo strumento cercherà nella cartella radice la libreria ADAL denominata **ADALiOS.bundle** .

-   Lo strumento non cerca i file binari di ADAL (se presenti) all'interno dell'app. Se l'app si collega a una versione obsoleta, possono verificarsi errori di runtime durante l'accesso se sono abilitati i criteri di autenticazione.

-   [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] recupera il token AAD nell'ID risorsa MAM di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per l'autenticazione. Tuttavia, il token non viene usato nelle chiamate eseguite a loro volta per verificare la validità del token stesso. [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] legge solo il nome dell'entità utente dell'utente connesso per determinare l'accesso all'app. Il token AAD non viene usato per altre chiamate dei servizi.

-   I token di autenticazione vengono condivisi tra le app dallo stesso autore poiché sono archiviati nel portachiavi condiviso. Se si vuole isolare un'app specifica, sarà necessario usare un certificato di firma e un profilo di provisioning diversi per tale app.

-   Se si forniscono l'ID client e l'URI di reindirizzamento dell'applicazione client, si evitano richieste di accesso doppie. Questo ID client deve essere registrato per accedere all'ID risorsa Gestione di applicazioni mobili [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]nel Dashboard di AAD. In caso contrario, si verificherà un errore di accesso quando viene eseguita l'app.

## Impostazione dei diritti delle app
Prima di eseguire la disposizione testo per l'app, è possibile assegnare **diritti** per concedere all'app autorizzazioni e funzionalità aggiuntive superiori alle operazioni normalmente eseguibili da un'app.  Durante la firma del codice viene usato un **file dei diritti** per specificare le autorizzazioni speciali all'interno dell'app, ad esempio l'accesso a un portachiavi condiviso. I servizi di app specifici, denominati **funzionalità**, sono abilitati all'interno di Xcode durante lo sviluppo delle app. Una volta abilitate, le funzionalità vengono riportate nel file dei diritti. Per altre informazioni su funzionalità e diritti, vedere l'articolo relativo all'[aggiunta di funzionalità](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) nella libreria per gli sviluppatori iOS. Per un elenco completo delle funzionalità supportate, vedere [Funzionalità supportate](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/SupportedCapabilities/SupportedCapabilities.html)..

### Funzionalità supportate per lo strumento per la disposizione testo per app per iOS

|Funzionalità|Descrizione|Procedura consigliata|
|--------------|---------------|------------------------|
|Gruppi di app|Usare i gruppi di app per consentire a più app di accedere a contenitori condivisi e favorire la comunicazione interprocesso tra app.<br /><br />Per abilitare i gruppi di app, aprire il riquadro **Funzionalità** e fare clic su **ON** nella sezione **Gruppi di app**. È possibile aggiungere gruppi di app o selezionare gruppi esistenti.|Quando si usano gruppi di app, usare la notazione DNS inversa:<br /><br />*group.com.companyName.AppGroup*|
|Modalità di background|L'abilitazione delle modalità di background consente all'app iOS di continuare l'esecuzione in background.||
|Protezione dati|La protezione dei dati aggiunge un livello di sicurezza ai file archiviati su disco dall'app iOS. La protezione dei dati usa l'hardware di crittografia incorporato presente in dispositivi specifici per archiviare i file in formato crittografato su disco. È necessario eseguire il provisioning dell'app per usare la protezione dei dati.||
|Acquisto in-app|L'acquisto in-app incorpora uno store direttamente nell'app, in quanto consente di connettersi allo store ed elaborare in modo sicuro i pagamenti eseguiti dall'utente. È possibile usare l'acquisto in-app per riscuotere pagamenti per funzionalità avanzate o contenuti aggiuntivi utilizzabili dall'app.||
|Condivisione di portachiavi|L'attivazione della condivisione di portachiavi consente all'app di condividere le password nel portachiavi con altre app sviluppate dal team.|Quando si usa la condivisione di portachiavi, usare la notazione DNS inversa:<br /><br />*com.companyName.KeychainGroup*|
|VPN personale|Abilitare la VPN personale per consentire all'app di creare e controllare una configurazione VPN di sistema personalizzata usando il framework di estensione di rete.||
|Notifiche push|Il servizio Apple Push Notification (APN) consente a un'app che non è in esecuzione in primo piano di notificare all'utente la disponibilità di informazioni.|Per consentire il funzionamento delle notifiche push, è necessario usare un profilo di provisioning specifico dell'app.<br /><br />Seguire i passaggi indicati nella [documentazione per sviluppatori Apple](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html)..|
|Configurazione degli accessori wireless|L'abilitazione della configurazione degli accessori wireless aggiunge il framework degli accessori esterni al progetto e consente all'app di configurare accessori MFi Wi-Fi.||

### Passaggi per abilitare i diritti

1.  Abilitare le funzionalità nell'app:

    1.  In Xcode, passare alla destinazione dell'app e fare clic sul riquadro **Funzionalità**.

    2.  Attivare le funzionalità appropriate. Per informazioni dettagliate su ogni funzionalità e su come determinare i valori corretti, vedere l'articolo relativo all'[aggiunta di funzionalità](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) nella libreria per sviluppatori iOS.

    3.  Prendere nota di eventuali ID creati durante il processo.

    4.  Creare e firmare l'app di cui eseguire il wrapping.

2.  Abilitare i diritti nel profilo di provisioning:

    1.  Accedere all'area membri degli sviluppatori Apple.

    2.  Creare un profilo di provisioning per l'app. Per istruzioni, vedere l'articolo relativo a [come ottenere i prerequisiti per lo strumento per la disposizione testo per app di Intune per iOS](http://blogs.technet.com/b/microsoftintune/archive/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios.aspx)..

    3.  Nel profilo di provisioning abilitare gli stessi diritti dell'app. È necessario indicare gli stessi ID specificati durante lo sviluppo dell'app.

    4.  Completare la configurazione guidata del profilo di provisioning e scaricare il file.

3.  Assicurarsi di aver soddisfatto tutti i prerequisiti e quindi eseguire il wrapping dell'app.

### Risoluzione di problemi comuni relativi ai diritti
Se lo strumento per la disposizione testo per app per iOS visualizza un errore relativo ai diritti, provare le procedure seguenti per la risoluzione dei problemi.

|Problema|Causa|Risoluzione|
|---------|---------|--------------|
|Impossibile analizzare i diritti generati dall'applicazione di input.|Lo strumento per la disposizione testo per app non è in grado di leggere il file dei diritti che è stato estratto dall'app. Il file dei diritti potrebbe non essere nel formato corretto.|Esaminare il file dei diritti per l'app. A tale scopo, seguire le istruzioni descritte di seguito. Quando si esamina il file dei diritti, verificare se sono presenti errori di sintassi. Il file deve essere in formato XML.|
|I diritti non sono presenti nel profilo di provisioning (sono elencati i diritti mancanti). Ricreare il pacchetto dell'app con un profilo di provisioning a cui sono assegnati tali diritti.|I diritti abilitati nel profilo di provisioning e le funzionalità abilitate nell'app non corrispondono. Questa mancata corrispondenza vale anche per gli ID associati a particolari funzionalità, ad esempio gruppi di app, accesso ai portachiavi e così via.|In genere è possibile creare un nuovo profilo di provisioning che abilita le stesse funzionalità dell'app. In caso di mancata corrispondenza tra gli ID del profilo e dell'app, lo strumento per la disposizione testo per app sostituirà gli ID, se è in grado di eseguire l'operazione. Se questo errore viene ancora visualizzato dopo aver creato un nuovo profilo di provisioning, è possibile provare a rimuovere i diritti dall'app usando il parametro **–e**. Vedere la sezione "Uso del parametro –e per rimuovere diritti da un'app" di seguito.|

### Trovare i diritti esistenti di un'app firmata
Per rivedere i diritti esistenti di un'app firmata e di un profilo di provisioning:

1.  Trovare il file con estensione IPA e modificare l'estensione in ZIP.

2.  Espandere il file con estensione ZIP. Verrà generata una cartella Payload contenente il bundle .app.

3.  Usare lo strumento codesign per verificare i diritti nel bundle .app, come segue:

    ```
    $ codesign -d --entitlements :- "Payload/YourApp.app"
    ```
    dove `YourApp.app` è il nome effettivo del bundle .app.

4.  Usare lo strumento security per verificare i diritti del profilo di provisioning incorporato dell'applicazione:

    ```
    $ security -D -i "Payload/YourApp.app/embedded.mobileprovision"
    ```
    dove `YourApp.app` è il nome effettivo del bundle .app.

### Uso del parametro –e per rimuovere diritti da un'app
Questo comando rimuove tutte le funzionalità abilitate nell'app che non sono presenti nel file dei diritti. Se si rimuovono le funzionalità usate dall'app si possono verificare interruzioni dell'app. È possibile rimuovere le funzionalità mancanti se si dispone di un'app prodotta dal fornitore che ha tutte le funzionalità per impostazione predefinita.

```
./IntuneMAMPackager.app/Contents/MacOS/IntuneMAMPackager –i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> –p /<path to provisioning profile> –c <SHA1 hash of the certificate> -e
```

## Sicurezza e privacy per lo strumento di wrapping delle app
Quando si usa lo strumento di wrapping delle app, adottare le procedure consigliate seguenti per la sicurezza e la privacy.

-   Il certificato di firma, il profilo di provisioning e l'app line-of-business specificati devono risiedere nello stesso computer Mac usato per eseguire lo strumenti di wrapping delle app. Se i file si trovano in un percorso UNC, assicurarsi che siano accessibili dal computer Mac. Il percorso deve essere protetto tramite firma IPsec o SMB.

    L'applicazione di cui è stato eseguito il wrapping importata nella console di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] deve risiedere nello stesso computer in cui viene eseguito lo strumento. Se il file si trova in un percorso UNC, assicurarsi che sia accessibile dal computer in cui viene eseguita la console di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)]. Il percorso deve essere protetto tramite firma IPsec o SMB.

-   L'ambiente in cui lo strumento di wrapping delle app viene scaricato dall'Area download Microsoft deve essere protetto tramite firma IPsec o SMB.

-   L'app elaborata deve provenire da una fonte attendibile per garantire la protezione dagli attacchi.

-   Assicurarsi che la cartella di output specificata nello strumento di wrapping delle app sia protetta, soprattutto se è una cartella remota.

-   Le app iOS che includono una finestra di dialogo per il caricamento dei file possono consentire agli utenti di eludere le restrizioni per le operazioni taglia, copia e incolla applicate all'app. Ad esempio, un utente potrebbe usare la finestra di dialogo per il caricamento dei file per caricare una schermata dei dati dell'app.

-   Quando gli utenti monitorano la cartella dei documenti sul dispositivo dall'app di cui è stato eseguito il wrapping, potrebbero visualizzare una cartella denominata **.msftintuneapplauncher**. Se questa cartella viene modificata o eliminata, ciò potrebbe influire sul corretto funzionamento delle app con restrizioni.

### Vedere anche
- [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md)</br>
- [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)</br>
- [Usare l'SDK per abilitare le app per la gestione delle applicazioni per dispositivi mobili](use-the-sdk-to-enable-apps-for-mobile-application-management.md)


<!--HONumber=May16_HO1-->


