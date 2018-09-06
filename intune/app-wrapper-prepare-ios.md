---
title: Eseguire il wrapping delle app iOS con lo strumento di wrapping delle app di Intune
description: Informazioni su come eseguire il wrapping delle app iOS senza modificarne il codice. Preparare le app in modo da applicare i criteri di gestione delle app mobili.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99ab0369-5115-4dc8-83ea-db7239b0de97
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: daaed6ded0c20551567a63890d324abcbaaf41d7
ms.sourcegitcommit: 9f99b4a7f20ab4175d6fa5735d9f4fd6a03e0d3a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2018
ms.locfileid: "40251849"
---
# <a name="prepare-ios-apps-for-app-protection-policies-with-the-intune-app-wrapping-tool"></a>Preparare le app iOS per i criteri di protezione delle app con lo strumento di wrapping delle app di Intune

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Usare lo strumento di wrapping delle app di Microsoft Intune per iOS per abilitare i criteri di protezione delle app di Intune senza modificare il codice dell'app stessa.

Lo strumento è un'applicazione da riga di comando di macOS che crea un wrapper intorno a un'app. Dopo l'elaborazione di un'app, è possibile modificarne la funzionalità distribuendo i [criteri di protezione delle app](/intune-classic/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) in tale app.

Per scaricare lo strumento, vedere [Microsoft Intune App Wrapping Tool for iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) (Strumento di wrapping delle app di Microsoft Intune per iOS) in GitHub.



## <a name="general-prerequisites-for-the-app-wrapping-tool"></a>Prerequisiti generali per lo strumento di wrapping delle app

Prima di eseguire lo strumento di wrapping delle app, è necessario soddisfare alcuni prerequisiti generali:

* Scaricare lo [strumento di wrapping delle app di Microsoft Intune per iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) da GitHub.

* Un computer macOS che esegue OS X 10.8.5 o versioni successive e con il set di strumenti XCode versione 5 o successive.

* L'app iOS di input deve essere sviluppata e firmata dalla società o da un fornitore di software indipendente (ISV).

  * Il file dell'app di input deve avere estensione **ipa** o **app**.

  * L'app di input deve essere compilata per iOS 8.0 o versione successiva.

  * L'app di input non può essere crittografata.

  * L'app di input non può avere attributi di file estesi.

  * L'app di input deve avere i diritti impostati prima dell'elaborazione con lo strumento di wrapping delle app di Intune. I [diritti](https://developer.apple.com/library/content/documentation/Miscellaneous/Reference/EntitlementKeyReference/Chapters/AboutEntitlements.html) concedono all'app autorizzazioni e funzionalità aggiuntive oltre a quelle generalmente concesse. Per istruzioni, vedere [Impostazione dei diritti delle app](#setting-app-entitlements).

## <a name="apple-developer-prerequisites-for-the-app-wrapping-tool"></a>Prerequisiti per sviluppatori Apple per lo strumento di wrapping delle app

Per distribuire le app di cui viene eseguito il wrapping in modo esclusivo agli utenti dell'organizzazione, è necessario un account per il programma [Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/) e più entità per la firma delle app collegate al proprio account per sviluppatori di Apple.

Per altre informazioni sulla distribuzione di app iOS internamente per gli utenti dell'organizzazione, leggere la guida ufficiale [Distributing Apple Developer Enterprise Program Apps](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/DistributingEnterpriseProgramApps/DistributingEnterpriseProgramApps.html#//apple_ref/doc/uid/TP40012582-CH33-SW1) (Distribuzione di app Apple Developer Enterprise Program).

È necessario quanto segue per distribuire le app di cui è stato eseguito il wrapping con Intune:

* Account per sviluppatori per Apple Developer Enterprise Program.

* Certificato di firma della distribuzione interno e ad hoc con identificatore del team valido.

  * L'hash SHA1 del certificato di firma sarà necessario come parametro per lo strumento di wrapping delle app di Intune.


* Profili di provisioning della distribuzione interno.

### <a name="steps-to-create-an-apple-developer-enterprise-account"></a>Procedura per creare un account Apple Developer Enterprise
1. Passare al [sito Apple Developer Enterprise Program](https://developer.apple.com/programs/enterprise/).

2. In alto a destra nella pagina fare clic su **Enroll** (Registra).

3. Leggere l'elenco di controllo delle informazioni necessarie per la registrazione. Fare clic su **Start Your Enrollment** (Avvia registrazione) nella parte inferiore della pagina.

4. Accedere (**Sign in**) con l'ID Apple dell'organizzazione. Se non è disponibile, fare clic su **Create Apple ID** (Crea ID Apple).

5. Selezionare **Entity Type** (Tipo di entità) e fare clic su **Continue** (Continua).

6. Compilare il modulo con le informazioni dell'organizzazione. Fare clic su **Continue**. A questo punto, Apple contatterà l'utente per verificare che sia autorizzato a registrare l'organizzazione.

8. Dopo la verifica, fare clic su **Agree to License** (Accettazione licenza).

9. Dopo aver accettato la licenza, completare la registrazione con **acquisto e attivazione del programma**.

10. Se si è l'agente del team (ovvero la persona che partecipa al programma Apple Developer Enterprise Program per conto dell'organizzazione), comporre prima di tutto il team invitando i membri e assegnando i ruoli. Per informazioni su come gestire il team, leggere la documentazione di Apple [Managing Your Developer Account Team](https://developer.apple.com/library/content/documentation/IDEs/Conceptual/AppDistributionGuide/ManagingYourTeam/ManagingYourTeam.html#//apple_ref/doc/uid/TP40012582-CH16-SW1) (Gestione del team di account per sviluppatori).

### <a name="steps-to-create-an-apple-signing-certificate"></a>Procedura per creare un certificato di firma Apple

1. Passare al [portale per sviluppatori Apple](https://developer.apple.com/).

2. In alto a destra nella pagina fare clic su **Account**.

3. Accedere (**Sign in**) con l'ID Apple dell'organizzazione.

4. Fare clic su **Certificates, IDs & Profiles** (Certificati, ID e profili).

   ![Portale per sviluppatori Apple](./media/iOS-signing-cert-1.png)

5. Fare clic su ![segno più nel portale per sviluppatori Apple](./media/iOS-signing-cert-2.png) nell'angolo in alto a destra per aggiungere un certificato iOS.

6. Scegliere di creare un certificato **In-House and Ad Hoc** (Interno e ad hoc) in **Production** (Produzione).

   ![Selezionare il certificato interno e ad hoc](./media/iOS-signing-cert-3.png)

   >[!NOTE]
   >Se non si prevede di distribuire l'app e si vuole solo testarla internamente, è possibile usare un certificato per lo sviluppo di app iOS invece di un certificato per la produzione. Se si usa un certificato di sviluppo, assicurarsi che il profilo di provisioning per dispositivi mobili faccia riferimento ai dispositivi in cui verrà installata l'app.

7. Fare clic su **Next** (Avanti) nella parte inferiore della pagina.

8. Leggere le istruzioni per la creazione di una **richiesta di firma del certificato (CSR, Certificate Signing Request)** mediante l'applicazione Accesso Portachiavi nel computer macOS.

   ![Leggere le istruzioni per creare una richiesta CSTR](./media/iOS-signing-cert-4.png)

9. Seguire le istruzioni sopra riportate per creare una richiesta di firma del certificato. Nel computer macOS in uso avviare l'applicazione **Accesso Portachiavi**.

10. Nel menu macOS nella parte superiore della schermata, passare a **Accesso Portachiavi > Assistente Certificato > Richiedi un certificato da una Autorità di Certificazione**.  

    ![Richiedere un certificato a un'Autorità di certificazione in Accesso Portachiavi](./media/iOS-signing-cert-5.png)

11. Seguire le istruzioni nel sito per sviluppatori Apple sopra indicato su come creare un file CSR. Salvare il file CSR nel computer macOS in uso.

    ![Richiedere un certificato a un'Autorità di certificazione in Accesso Portachiavi](./media/iOS-signing-cert-6.png)

12. Tornare al sito per sviluppatori Apple. Fare clic su **Continue**. Caricare quindi il file CSR.

13. Il certificato di firma viene generato da Apple. Scaricarlo e salvarlo in un percorso facile da ricordare nel computer macOS.

    ![Scaricare il certificato di firma](./media/iOS-signing-cert-7.png)

14. Fare doppio clic sul file di certificato appena scaricato per aggiungere il certificato a un portachiavi.

15. Aprire di nuovo **Accesso Portachiavi**. Individuare il certificato cercandone il nome nella barra di ricerca in alto a destra. Fare clic con il pulsante destro del mouse su un elemento per visualizzare il menu e scegliere **Ottieni informazioni**. Nelle schermate di esempio viene usato un certificato di sviluppo anziché un certificato di produzione.

    ![Aggiungere il certificato a un portachiavi](./media/iOS-signing-cert-8.png)

16. Viene visualizzata una finestra informativa. Scorrere verso il basso fino alla sezione **Impronte digitali**. Copiare la stringa **SHA1** (sfocata) da usare come argomento per "-c" per lo strumento di wrapping delle app.

    ![Aggiungere il certificato a un portachiavi](./media/iOS-signing-cert-9.png)



### <a name="steps-to-create-an-in-house-distribution-provisioning-profile"></a>Procedura per creare un profilo di provisioning della distribuzione interno

1. Tornare al [portale per gli account per sviluppatori di Apple](https://developer.apple.com/account/) e **accedere** con l'ID Apple dell'organizzazione.

2. Fare clic su **Certificates, IDs & Profiles** (Certificati, ID e profili).

3. Fare clic su ![segno più nel portale per sviluppatori Apple](./media/iOS-signing-cert-2.png) nell'angolo in alto a destra per aggiungere un profilo di provisioning iOS.

4. Scegliere **In House** (Interna) in **Distribution** (Distribuzione) per creare un profilo di provisioning interno.

   ![Selezionare un profilo di provisioning interno](./media/iOS-provisioning-profile-1.png)

5. Fare clic su **Continue**. Assicurarsi di collegare il certificato di firma generato in precedenza al profilo di provisioning.

6. Seguire le istruzioni per scaricare il profilo (con estensione mobileprovision) nel computer macOS.

7. Salvare il file in una posizione facile da ricordare. Questo file verrà usato per il parametro -p durante l'uso dello strumento di wrapping delle app.



## <a name="download-the-app-wrapping-tool"></a>Scaricare lo strumento di wrapping delle app

1.  Scaricare i file per lo strumento di wrapping delle app da [GitHub](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios) in un computer macOS.

2.  Fare doppio clic su **Microsoft Intune App Wrapping Tool for iOS.dmg**. Verrà visualizzata una finestra con il Contratto di licenza con l'utente finale (EULA). Leggere attentamente il documento.

3. Scegliere **Accetto** per accettare il contratto di licenza e procedere al montaggio del pacchetto nel computer.

## <a name="run-the-app-wrapping-tool"></a>Eseguire lo strumento di wrapping delle app

### <a name="use-terminal"></a>Usare il terminale

Aprire il terminale macOS ed eseguire il comando seguente:

```
/Volumes/IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioning profile paths>]
```

> [!NOTE]
> Alcuni parametri sono facoltativi, come illustrato nella tabella seguente.

**Esempio:** il comando di esempio seguente esegue lo strumento di wrapping delle app sull'app denominata MyApp.ipa. Per firmare l'app di cui è stato eseguito il wrapping vengono specificati e usati un profilo di provisioning e l'hash SHA-1 del certificato di firma. L'app di output (MyApp_Wrapped.ipa) viene creata e archiviata nella cartella Desktop dell'utente.

```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c "12 A3 BC 45 D6 7E F8 90 1A 2B 3C DE F4 AB C5 D6 E7 89 0F AB"  -v true
```

### <a name="command-line-parameters"></a>Parametri della riga di comando
Con lo strumento di wrapping delle app è possibile usare i parametri della riga di comando seguenti:

|Proprietà|Modo d'uso|
|---------------|--------------------------------|
|**-i**|`<Path of the input native iOS application file>`. Il nome del file deve terminare con l'estensione app o ipa. |
|**-o**|`<Path of the wrapped output application>` |
|**-p**|`<Path of your provisioning profile for iOS apps>`|
|**-c**|`<SHA1 hash of the signing certificate>`|
|**-h**|Mostra informazioni d'uso dettagliate per le proprietà della riga di comando disponibili per lo strumento di wrapping delle app.|
|**-v**|(Facoltativo) Mostra messaggi dettagliati nella console. È consigliabile usare questo flag per il debug di eventuali errori.|
|**-e**| (Facoltativo) Usare questo flag per fare in modo che lo strumento di wrapping delle app rimuova i diritti mancanti durante l'elaborazione dell'app. Per altri dettagli, vedere [Impostazione dei diritti delle app](#setting-app-entitlements).|
|**-xe**| (Facoltativo) Visualizza informazioni sulle estensioni iOS nell'app e sui diritti necessari per usarle. Per altri dettagli, vedere [Impostazione dei diritti delle app](#setting-app-entitlements). |
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

```bash
./IntuneMAMPackager –f Parameters.plist
```

### <a name="post-wrapping"></a>Dopo il wrapping

Al termine del processo di wrapping verrà visualizzato un messaggio simile al seguente: "Wrapping dell'applicazione completato". Se si verifica un errore, vedere [Messaggi di errore](#error-messages-and-log-files) per altre informazioni.

L'app di cui è stato eseguito il wrapping viene salvata nella cartella di output specificata in precedenza. È ora possibile caricare l'app nella console di amministrazione di Intune e associarla ai criteri di gestione di applicazioni mobili.

> [!IMPORTANT]
> Quando si carica un'app con wrapper è possibile provare a eseguire l'aggiornamento di una versione precedente (con wrapper o nativa) se tale versione era già stata distribuita a Intune. In caso di errore, caricare l'app come nuova app ed eliminare la versione precedente.

È ora possibile distribuire l'app ai gruppi di utenti e assegnare i criteri di protezione delle app all'app. L'app verrà eseguita nel dispositivo con i criteri di protezione delle app specificati.

## <a name="how-often-should-i-rewrap-my-ios-application-with-the-intune-app-wrapping-tool"></a>Con quale frequenza è necessario eseguire nuovamente il wrapping dell'applicazione iOS con lo strumento di wrapping delle app di Intune?
Gli scenari principali in cui è necessario eseguire nuovamente il wrapping delle applicazioni sono i seguenti:
* L'applicazione ha rilasciato una nuova versione. La versione precedente dell'app è stata sottoposta a wrapping e caricata nella console di Intune.
* Lo strumento di wrapping delle app di Intune per iOS ha rilasciato una nuova versione che consente di eseguire le principali correzioni di bug o che dispone di nuove e specifiche funzionalità con criteri di protezione per applicazioni Intune. Ciò avviene dopo 6-8 settimane tramite il repository GitHub per lo [strumento di wrapping delle app di Microsoft Intune per iOS](https://github.com/msintuneappsdk/intune-app-wrapping-tool-ios).

Per iOS, sebbene sia possibile eseguire il wrapping con un profilo di certificato/provisioning diverso rispetto a quello originale usato per firmare l'app, se i diritti specificati nell'app non sono inclusi nel nuovo profilo di provisioning, l'operazione di wrapping avrà esito negativo. L'uso dell'opzione della riga di comando "-e", che rimuove i diritti mancanti dall'app, per imporre la corretta esecuzione del wrapping in questo scenario può determinare problemi di funzionamento nell'app.

Alcune procedure consigliate per eseguire nuovamente il wrapping comprendono:
* Assicurarsi che un profilo di provisioning diverso includa tutti i diritti necessari come il profilo di provisioning precedente. 

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

Lo strumento di wrapping delle app per iOS include alcuni requisiti che devono essere soddisfatti per garantire la completa funzionalità.

|Requisito|Dettagli|
|---------------|-----------|
|Profilo di provisioning iOS|Verificare che il profilo di provisioning sia valido prima di includerlo. Lo strumento di wrapping delle app non controlla se il profilo di provisioning è scaduto durante l'elaborazione di un'app iOS. Se viene specificato un profilo di provisioning scaduto, lo strumento di wrapping delle app includerà il profilo di provisioning scaduto e il problema si scoprirà solo durante l'installazione dell'app nel dispositivo iOS, che non riuscirà.|
|Certificato di firma iOS|Assicurarsi che il certificato di firma sia valido prima di specificarlo. Lo strumento non verifica se un certificato è scaduto durante l'elaborazione delle app iOS. Se viene fornito l'hash per un certificato scaduto, lo strumento elaborerà e firmerà l'app, ma l'installazione nei dispositivi non riuscirà.<br /><br />Verificare che il certificato fornito per la firma dell'app di cui è stato eseguito il wrapping abbia una corrispondenza nel profilo di provisioning. Lo strumento non verifica se il profilo di provisioning ha una corrispondenza per il certificato fornito per la firma dell'applicazione con wrapper.|
|Autenticazione|Per usare la crittografia, è necessario che il dispositivo disponga di un PIN. Se si tocca la barra di stato nei dispositivi in cui è stata distribuita un'app di cui è stato eseguito il wrapping, verrà richiesto di eseguire di nuovo l'accesso con un account aziendale o dell'istituto di istruzione. I criteri predefiniti per un'app con wrapper prevedono l'*autenticazione al riavvio*. iOS gestisce qualsiasi notifica esterna, come una chiamata telefonica, chiudendo e riavviando l'app.


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

    a.  In Xcode passare alla destinazione dell'app e fare clic su **Capabilities** (Funzionalità).

    b.  Attivare le funzionalità appropriate. Per informazioni dettagliate su ogni funzionalità e su come determinare i valori corretti, vedere l'articolo relativo all'[aggiunta di funzionalità](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/AppDistributionGuide/AddingCapabilities/AddingCapabilities.html) nella libreria per sviluppatori iOS.

    c.  Prendere nota di eventuali ID creati durante il processo. Questi possono anche essere denominati valori `AppIdentifierPrefix`.

    d.  Creare e firmare l'app di cui eseguire il wrapping.

2.  Abilitare i diritti nel profilo di provisioning:

    a.  Accedere all'area membri degli sviluppatori Apple.

    b.  Creare un profilo di provisioning per l'app. Per istruzioni, vedere [How to Obtain the Prerequisites for the Intune App Wrapping Tool for iOS](https://blogs.technet.microsoft.com/enterprisemobility/2015/02/25/how-to-obtain-the-prerequisites-for-the-intune-app-wrapping-tool-for-ios/) (Come ottenere i prerequisiti per lo strumento per la disposizione testo per app di Intune per iOS).

    c.  Nel profilo di provisioning abilitare gli stessi diritti dell'app. È necessario indicare gli stessi ID, i valori `AppIdentifierPrefix`, specificati durante lo sviluppo dell'app. 

    d.  Completare la configurazione guidata del profilo di provisioning e scaricare il file.

3.  Assicurarsi di aver soddisfatto tutti i prerequisiti e quindi eseguire il wrapping dell'app.

### <a name="troubleshoot-common-errors-with-entitlements"></a>Risoluzione di problemi comuni relativi ai diritti
Se lo strumento di wrapping delle app per iOS visualizza un errore relativo ai diritti, provare le procedure seguenti per la risoluzione dei problemi.

|Problema|Causa|Soluzione|
|---------|---------|--------------|
|Impossibile analizzare i diritti generati dall'applicazione di input.|Lo strumento per la disposizione testo per app non è in grado di leggere il file dei diritti che è stato estratto dall'app. Il file dei diritti potrebbe non essere nel formato corretto.|Esaminare il file dei diritti per l'app. Le istruzioni seguenti spiegano come eseguire questa operazione. Quando si esamina il file dei diritti, verificare se sono presenti errori di sintassi. Il file deve essere in formato XML.|
|I diritti non sono presenti nel profilo di provisioning (sono elencati i diritti mancanti). Ricreare il pacchetto dell'app con un profilo di provisioning a cui sono assegnati tali diritti.|I diritti abilitati nel profilo di provisioning e le funzionalità abilitate nell'app non corrispondono. Questa mancata corrispondenza vale anche per gli ID associati a particolari funzionalità, ad esempio gruppi di app, accesso al portachiavi e così via.|In genere è possibile creare un nuovo profilo di provisioning che abilita le stesse funzionalità dell'app. In caso di mancata corrispondenza tra gli ID del profilo e dell'app, lo strumento per la disposizione testo per app sostituirà gli ID, se è in grado di eseguire l'operazione. Se questo errore viene ancora visualizzato dopo aver creato un nuovo profilo di provisioning, è possibile provare a rimuovere i diritti dall'app usando il parametro -e (vedere la sezione Uso del parametro -e per rimuovere diritti da un'app).|

### <a name="find-the-existing-entitlements-of-a-signed-app"></a>Trovare i diritti esistenti di un'app firmata
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

    L'applicazione di cui è stato eseguito il wrapping importata nella console di amministrazione deve trovarsi nello stesso computer in cui viene eseguito lo strumento. Se il file si trova in un percorso UNC, assicurarsi che sia accessibile dal computer che esegue la console di amministrazione. Il percorso deve essere protetto tramite firma IPsec o SMB.

-   L'ambiente in cui lo strumento di wrapping delle app viene scaricato dal repository GitHub deve essere protetto tramite firma IPSec o SMB.

-   L'app elaborata deve provenire da una fonte attendibile per garantire la protezione dagli attacchi.

-   Assicurarsi che la cartella di output specificata nello strumento di wrapping delle app sia protetta, soprattutto se è una cartella remota.

-   Le app iOS che includono una finestra di dialogo per il caricamento dei file possono consentire agli utenti di eludere le restrizioni per le operazioni taglia, copia e incolla applicate all'app. Ad esempio, un utente potrebbe usare la finestra di dialogo per il caricamento dei file per caricare una schermata dei dati dell'app.

-   Quando si monitora la cartella dei documenti nel dispositivo dall'app di cui è stato eseguito il wrapping, potrebbe essere visualizzata una cartella denominata .msftintuneapplauncher. Se questo file viene modificato o eliminato, ciò potrebbe influire sul corretto funzionamento delle app con restrizioni.

## <a name="intune-app-wrapping-tool-for-ios-with-citrix-mdx-mvpn"></a>Strumento di wrapping delle app di Intune per iOS con tecnologia mVPN MDX di Citrix
Questa funzionalità è un'integrazione con il wrapper di app Citrix MDX per iOS. L'integrazione è semplicemente un flag della riga di comando facoltativo aggiuntivo, `-citrix` per gli strumenti di wrapping delle app di Intune generali.

### <a name="requirements"></a>Requisiti

Per usare il flag `-citrix` è necessario installare anche il [wrapper di app Citrix MDX per iOS](https://docs.citrix.com/en-us/mdx-toolkit/10/xmob-mdx-kit-app-wrap-ios.html) nello stesso computer macOS. I download sono disponibili in [Citrix XenMobile Downloads](https://www.citrix.com/downloads/xenmobile/) e sono limitati ai clienti Citrix solo dopo l'accesso. Assicurarsi che questo componente venga installato nel percorso predefinito: `/Applications/Citrix/MDXToolkit`. 

> [!NOTE] 
> Il supporto per l'integrazione di Intune e Citrix è limitato solo ai dispositivi iOS 10+.

### <a name="use-the--citrix-flag"></a>Usare il flag `-citrix`
Eseguire semplicemente il comando di wrapping delle app generale con il flag `-citrix` aggiunto. Il flag `-citrix` attualmente non accetta alcun argomento.

**Formato di utilizzo**:
```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i /<path of input app>/<app filename> -o /<path to output folder>/<app filename> -p /<path to provisioning profile> -c <SHA1 hash of the certificate> [-b [<output app build string>]] [-v] [-e] [-x /<array of extension provisioing profile paths>] [-citrix]
```

**Comando di esempio**:
```
./IntuneMAMPackager/Contents/MacOS/IntuneMAMPackager -i ~/Desktop/MyApp.ipa -o ~/Desktop/MyApp_Wrapped.ipa -p ~/Desktop/My_Provisioning_Profile_.mobileprovision -c 12A3BC45D67EF8901A2B3CDEF4ABC5D6E7890FAB  -v true -citrix
```

## <a name="getting-logs-for-your-wrapped-applications"></a>Recupero dei log per le applicazioni di cui è stato eseguito il wrapping
Usare questa procedura per ottenere i log per le applicazioni di cui è stato eseguito il wrapping durante la risoluzione dei problemi.

1. Passare all'app Impostazioni iOS nel dispositivo e selezionare l'app LOB.
2. Impostare **Diagnostics Console** (Console diagnostica) su **On**.
3. Avviare l'applicazione LOB.
4. Fare clic sul collegamento "Get Started" (Per iniziare).
5. È ora possibile condividere i log tramite posta elettronica o copiarli in un percorso di OneDrive.

> [!NOTE]
> La funzionalità di registrazione è abilitata per le app di cui è stato eseguito il wrapping con la versione 7.1.13 dello strumento di wrapping delle app di Intune, o versione successiva.

### <a name="see-also"></a>Vedere anche
- [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](apps-prepare-mobile-application-management.md)</br>
- [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)</br>
- [Usare l'SDK per abilitare le app per la gestione delle applicazioni mobili](/intune-classic/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management)
