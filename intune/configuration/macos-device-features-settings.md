---
title: Impostazioni delle funzionalità dei dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare le impostazioni per configurare i dispositivi macOS per AirPrint e personalizzare la finestra di accesso per visualizzare o nascondere pulsanti di alimentazione in Microsoft Intune. Vedere i passaggi per ottenere l'indirizzo IP, il percorso e le impostazioni della porta di un server AirPrint nella rete. Usare queste impostazioni in un profilo di configurazione del dispositivo per configurare le funzionalità dei dispositivi macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: df5b53be159fd082090e61fd736e4c9329644c85
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512739"
---
# <a name="macos-device-feature-settings-in-intune"></a>Impostazioni relative alle funzionalità dei dispositivi macOS in Intune

Intune include alcune impostazioni integrate per personalizzare le funzionalità nei dispositivi macOS. Ad esempio, gli amministratori possono aggiungere stampanti AirPrint, scegliere la modalità di accesso degli utenti, configurare i controlli di risparmio energia, usare l'autenticazione Single Sign-On e altro ancora.

Usare queste funzionalità per controllare i dispositivi macOS nella soluzione di gestione di dispositivi mobili (MDM).

L'articolo elenca queste impostazioni e descrive la funzione di ogni impostazione. Vengono inoltre elencati i passaggi per ottenere l'indirizzo IP, il percorso e la porta delle stampanti AirPrint tramite l'app Terminale (emulatore). Per altre informazioni sulle funzionalità del dispositivo, vedere [Aggiungere impostazioni relative alle funzionalità dei dispositivi iOS/iPadOS e macOS](device-features-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione dei dispositivi macOS](device-features-configure.md).

> [!NOTE]
> Queste impostazioni si applicano a diversi tipi di registrazione, con alcune impostazioni che si applicano a tutte le opzioni di registrazione. Per altre informazioni sui diversi tipi di registrazione, vedere [Registrazione di macOS](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: Registrazione dei dispositivi e registrazione automatica dei dispositivi 

- **Indirizzo IP**: immettere l'indirizzo IPv4 o IPv6 della stampante. Se si usano i nomi host per identificare le stampanti, è possibile ottenere l'indirizzo IP effettuando il ping della stampante nell'app Terminale. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
- **Percorso**: immettere il percorso della stampante. il percorso è in genere `ipp/print` per le stampanti di rete. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
- **Porta** (iOS 11.0+, iPadOS 13.0+): immettere la porta di ascolto della destinazione AirPrint. Se si omette questa proprietà, AirPrint usa la porta predefinita.
- **TLS** (iOS 11.0+, iPadOS 13.0+): selezionare **Abilita** per proteggere le connessioni AirPrint con Transport Layer Security (TLS).

- **Aggiungere** il server AirPrint. È possibile aggiungere più server AirPrint.

È anche possibile **importare** un file delimitato da virgole (CSV) che include un elenco delle stampanti AirPrint. Dopo aver aggiunto le stampanti AirPrint in Intune, è anche possibile **esportare** questo elenco.

### <a name="get-the-ip-address-and-path"></a>Ottenere l'indirizzo IP e il percorso

Per aggiungere i server AirPrinter, sono necessari l'indirizzo IP della stampante, il percorso della risorsa e la porta. La procedura seguente mostra come ottenere queste informazioni.

1. In un dispositivo Mac connesso alla stessa rete locale (subnet) delle stampanti AirPrint aprire **Terminale** (da **/Applicazioni/Utilità**).
2. Nell'app Terminale digitare `ippfind` e premere INVIO.

    Prendere nota delle informazioni della stampante. Ad esempio, potrebbe restituire un valore simile a `ipp://myprinter.local.:631/ipp/port1`. La prima parte è il nome della stampante. L'ultima parte (`ipp/port1`) è il percorso della risorsa.

3. Nel Terminale digitare `ping myprinter.local` e premere INVIO.

   Prendere nota dell'indirizzo IP. Ad esempio, potrebbe restituire un valore simile a `PING myprinter.local (10.50.25.21)`.

4. Usare i valori del percorso della risorsa e dell'indirizzo IP. In questo esempio l'indirizzo IP è `10.50.25.21` e il percorso della risorsa è `/ipp/port1`.

## <a name="login-items"></a>Elementi di accesso

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: Tutti i tipi di registrazione

- **File, cartelle e app personalizzate**: **aggiungere** il percorso di un file, una cartella, un'app personalizzata o un'app di sistema che si vuole aprire quando un utente accede al dispositivo. Le app di sistema o le app compilate o personalizzate per l'organizzazione si trovano in genere nella cartella `Applications`, con un percorso simile a `/Applications/AppName.app`. 

  È possibile aggiungere molti file, cartelle e app. Ad esempio, immettere:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Quando si aggiunge un'app, una cartella o un file, assicurarsi di immettere il percorso corretto. Non tutti gli elementi si trovano nella cartella `Applications`. Se un utente sposta un elemento da una posizione a un'altra, il percorso viene modificato. Questo elemento spostato non verrà aperto quando l'utente accede.

## <a name="login-window"></a>Finestra di accesso

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: Registrazione dei dispositivi e registrazione automatica dei dispositivi

#### <a name="window-layout"></a>Layout della finestra

- **Mostra informazioni aggiuntive sulla barra dei menu**: quando viene selezionata l'area del tempo nella barra dei menu, **Consenti** mostra il nome host e la versione di macOS. **Non configurato** (impostazione predefinita) non visualizza queste informazioni nella barra dei menu.
- **Banner**: immettere un messaggio che viene visualizzato nella schermata di accesso del dispositivo. Ad esempio, immettere le informazioni sull'organizzazione, un messaggio di benvenuto, le informazioni perse e trovate e così via.
- **Scegliere il formato di accesso**: scegliere la modalità di accesso degli utenti al dispositivo. Le opzioni disponibili sono:
  - **Richiedi nome utente e password** (impostazione predefinita): richiede agli utenti di immettere un nome utente e una password.
  - **Elenca tutti gli utenti e richiedi la password**: richiede agli utenti di selezionare il nome utente da un elenco di utenti e quindi di immettere la password. Configurare inoltre:

    - **Utenti locali**: **Nascondi** non mostra gli account utente locali nell'elenco degli utenti, che può includere gli account standard e amministratore. Vengono visualizzati solo gli account utente di rete e del sistema. **Non configurato** (impostazione predefinita) mostra gli account utente locali nell'elenco degli utenti.
    - **Account per dispositivi mobili**: **Nascondi** non mostra gli account per dispositivi mobili nell'elenco degli utenti. **Non configurato** (impostazione predefinita) mostra gli account utente per dispositivi mobili nell'elenco degli utenti. Alcuni account per dispositivi mobili possono essere visualizzati come utenti della rete.
    - **Utenti di rete**: selezionare **Mostra** per elencare gli utenti di rete nell'elenco degli utenti. **Non configurato** (impostazione predefinita) non mostra gli account degli utenti di rete nell'elenco degli utenti.
    - **Utenti amministratori**: **Nascondi** non mostra gli account utente amministratori nell'elenco degli utenti. **Non configurato** (impostazione predefinita) mostra gli account utente amministratori nell'elenco degli utenti.
    - **Altri utenti**: selezionare **Mostra** per elencare **Altri...** utenti nell'elenco degli utenti. **Non configurato** (impostazione predefinita) non mostra gli altri account utente nell'elenco degli utenti.

#### <a name="login-screen-power-settings"></a>Impostazioni di risparmio energia della schermata di accesso

- **Pulsante Arresta**: **Nascondi** non mostra il pulsante di arresto nella schermata di accesso. **Non configurata** (impostazione predefinita) mostra il pulsane di arresto.
- **Pulsante Riavvia**: **Nascondi** non mostra il pulsante di riavvio nella schermata di accesso. **Non configurata** (impostazione predefinita) mostra il pulsane di riavvio.
- **Pulsante Sospendi**: **Nascondi** non mostra il pulsante di sospensione nella schermata di accesso. **Non configurata** (impostazione predefinita) mostra il pulsante di sospensione.

#### <a name="other"></a>Altro

- **Disabilita l'accesso utente dalla console**: **Disabilitare** nasconde la riga di comando macOS usata per accedere. Per gli utenti tipici **disabilitare** questa impostazione. **Non configurata** (impostazione predefinita) consente agli utenti esperti di accedere usando la riga di comando di macOS. Per passare alla modalità console, gli utenti immettono `>console` nel campo Nome utente e devono autenticarsi nella finestra della console.

#### <a name="apple-menu"></a>Apple Menu

Dopo che gli utenti hanno effettuato l'accesso ai dispositivi, le impostazioni seguenti influiscono cosa possono fare.

- **Disabilita Arresta**: **Disabilita** impedisce agli utenti di selezionare l'opzione **Arresta** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Arresta** sul dispositivo.
- **Disabilita Riavvia**: **Disabilita** impedisce agli utenti di selezionare l'opzione **Riavvia** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Riavvia** sul dispositivo.
- **Disabilita Spegni**: **Disabilita** impedisce agli utenti di selezionare l'opzione **Spegni** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Spegni** sul dispositivo.
- **Disabilita Disconnetti** (macOS 10.13 e versioni successive): **Disabilita** impedisce agli utenti di selezionare l'opzione **Disconnetti** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Disconnetti** sul dispositivo.
- **Disabilita la schermata di blocco** (macOS 10.13 e versioni successive): **Disabilita** impedisce agli utenti di selezionare l'opzione **Schermata di blocco** dopo aver effettuato l'accesso. **Non configurata** (impostazione predefinita) consente agli utenti di selezionare la voce di menu **Schermata di blocco** sul dispositivo.

## <a name="single-sign-on-app-extension"></a>Estensione dell'app Single Sign-On

Questa funzionalità si applica a:

- macOS 10.15 e versioni successive

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: Tutti i tipi di registrazione 

- **Tipo di estensione dell'app per accesso Single Sign-On**: scegliere il tipo di estensione dell'app per l'accesso Single Sign-On per le credenziali. Le opzioni disponibili sono:

  - **Non configurato**: non vengono usate le estensioni dell'app. Per disabilitare un'estensione dell'app, impostare il tipo di estensione dell'app per l'accesso Single Sign-On su **Non configurato**.
  - **Reindirizzamento**: usare un'estensione dell'app di reindirizzamento generica e personalizzabile per eseguire l'accesso Single Sign-On con flussi di autenticazione moderni. Assicurarsi di conoscere l'estensione e l'ID team dell'estensione dell'app dell'organizzazione.
  - **Credenziali**: usare un'estensione dell'app per le credenziali personalizzabile e generica per eseguire l'accesso Single Sign-On con i flussi di autenticazione challenge-and-response (richiesta e risposta). Assicurarsi di conoscere l'ID estensione e l'ID team dell'estensione dell'app per l'accesso Single Sign-On dell'organizzazione.  
  - **Kerberos**: usare l'estensione Kerberos predefinita di Apple, inclusa in macOS Catalina 10.15 e versioni successive. Questa opzione è una versione specifica di Kerberos dell'estensione dell'app **Credenziali**.

  > [!TIP]
  > Con i tipi **Reindirizzamento** e **Credenziali** è possibile aggiungere i propri valori di configurazione per passare l'estensione. Se si usa il tipo **Credenziali**, può essere utile usare le impostazioni di configurazione predefinite di Apple nel tipo **Kerberos**.

- **ID estensione** (Reindirizzamento e Credenziali): immettere l'identificatore del bundle che identifica l'estensione dell'app per l'accesso Single Sign-On, ad esempio `com.apple.ssoexample`.
- **ID team** (Reindirizzamento e Credenziali): immettere l'identificatore del team dell'estensione dell'app per l'accesso Single Sign-On. Un identificatore del team è una stringa alfanumerica (numeri e lettere) di 10 caratteri generata da Apple, ad esempio `ABCDE12345`. 

  [Locate your Team ID](https://help.apple.com/developer-account/#/dev55c3c710c) (Individuare l'ID team) (apre il sito Web di Apple) include ulteriori informazioni.

- **Area di autenticazione** (Credenziali e Kerberos): immettere il nome dell'area di autenticazione. Il nome dell'area di autenticazione deve essere in lettere maiuscole, ad esempio `CONTOSO.COM`. In genere, il nome dell'area di autenticazione corrisponde al nome di dominio DNS, ma in lettere maiuscole.

- **Domini** (Credenziali e Kerberos): immettere il nome di dominio o il nome host dei siti che possono eseguire l'autenticazione tramite SSO. Ad esempio, se il sito Web è `mysite.contoso.com`, `mysite` è il nome host e `contoso.com` è il nome di dominio. Quando gli utenti si connettono a uno di questi siti, l'estensione dell'app gestisce la richiesta di autenticazione. Questa autenticazione consente agli utenti di usare Face ID, Touch ID o il pincode/passcode Apple per accedere.

  - Tutti i domini nei profili di Intune dell'estensione dell'app Single Sign-On devono essere univoci. Non è possibile ripetere un dominio in un profilo di estensione dell'app di accesso, anche se si usano tipi diversi di estensioni dell'app per l'accesso Single Sign-On.
  - Questi domini non fanno distinzione tra maiuscole e minuscole.

- **URL** (solo Reindirizzamento): immettere i prefissi URL dei provider di identità per cui l'estensione dell'app di reindirizzamento esegue l'accesso Single Sign-On. Quando un utente viene reindirizzato a questi URL, l'estensione dell'app per l'accesso Single Sign-On interviene e richiede l'accesso Single Sign-On.

  - Tutti gli URL nei profili di estensione dell'app per l'accesso Single Sign-On di Intune devono essere univoci. Non è possibile ripetere un dominio in un profilo di estensione dell'app per l'accesso Single Sign-On, anche se si usano tipi diversi di estensioni dell'app per l'accesso Single Sign-On.
  - Gli URL devono iniziare con http://o https://.

- **Configurazione aggiuntiva** (Reindirizzamento e Credenziali): immettere i dati aggiuntivi specifici dell'estensione da passare all'estensione dell'app per l'accesso Single Sign-On:
  - **Chiave**: immettere il nome dell'elemento che si vuole aggiungere, ad esempio `user name`.
  - **Tipo**: immettere il tipo di dati. Le opzioni disponibili sono:

    - Stringa
    - Booleano: in **Valore di configurazione** immettere `True` o `False`.
    - Intero: in **Valore di configurazione** immettere un numero.
    
  - **Valore**: immettere i dati.
  
  - **Aggiungi**: selezionare questa impostazione per aggiungere le chiavi di configurazione.

- **Utilizzo di Keychain** (solo Kerberos): scegliere **Blocca** per impedire il salvataggio e l'archiviazione delle password in Keychain. **Non configurato** (impostazione predefinita) consente il salvataggio e l'archiviazione delle password in Keychain.  
- **Face ID, Touch ID o passcode** (solo Kerberos): **Richiedi** impone agli utenti di immettere il proprio Face ID, Touch ID o passcode Apple per accedere ai domini aggiunti. **Non configurato** (impostazione predefinita) non richiede agli utenti di usare la biometria o il passcode per accedere.
- **Area di autenticazione predefinita** (solo Kerberos): scegliere **Abilita** per impostare il valore **Area di autenticazione** immesso come area di autenticazione predefinita. **Non configurato** (impostazione predefinita) non imposta un'area di autenticazione predefinita.

  > [!TIP]
  > - **Abilitare** questa impostazione se si stanno configurando più estensioni dell'app per l'accesso Single Sign-On Kerberos nell'organizzazione.
  > - **Abilitare** questa impostazione se si usano più aree di autenticazione. Imposta il valore **Area di autenticazione** immesso come area di autenticazione predefinita.
  > - Se si ha una sola area di autenticazione, lasciare l'impostazione **Non configurato** (impostazione predefinita).

- **Individuazione automatica** (solo Kerberos): se impostata su **Blocca**, l'estensione Kerberos non usa automaticamente LDAP e DNS per determinare il nome del sito Active Directory. **Non configurato** (impostazione predefinita) consente all'estensione di individuare automaticamente il nome del sito Active Directory.
- **Modifiche password** (solo Kerberos): **Blocca** impedisce agli utenti di modificare le password usate per accedere ai domini immessi. **Non configurato** (impostazione predefinita) consente le modifiche delle password.  
- **Sincronizzazione password** (solo Kerberos): scegliere **Abilita** per sincronizzare le password locali degli utenti per Azure AD. **Non configurato** (impostazione predefinita) disabilita la sincronizzazione delle password in Azure AD. Usare questa impostazione come alternativa o backup per l'accesso Single Sign-On. Questa impostazione non funziona se gli utenti hanno eseguito l'accesso con un account per dispositivi mobili Apple.
- **Complessità della password di Windows Server Active Directory** (solo Kerberos): scegliere **Richiedi** per fare in modo che le password utente soddisfino i requisiti di complessità delle password di Active Directory. Per altre informazioni, vedere [Le password devono essere conformi ai requisiti di complessità](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements). **Non configurato** (impostazione predefinita) non richiede che gli utenti soddisfino i requisiti delle password di Active Directory.
- **Lunghezza minima password** (solo Kerberos): immettere il numero minimo di caratteri della password di un utente. **Non configurato** (impostazione predefinita) non impone la lunghezza minima della password per gli utenti.
- **Limite di riutilizzo password** (solo Kerberos): immettere il numero di nuove password, da 1 a 24, che devono essere usate prima che una password precedente possa essere usata nuovamente nel dominio. **Non configurato** (impostazione predefinita) non impone un limite di riutilizzo delle password.
- **Validità minima della password** (solo Kerberos): immettere il numero di giorni per cui è necessario usare una password nel dominio prima che un utente possa modificarla. **Non configurato** (impostazione predefinita) non impone una validità minima delle password prima che possano essere modificate.
- **Notifica della scadenza della password** (solo Kerberos): immettere il numero di giorni prima della scadenza di una password per cui gli utenti riceveranno una notifica della scadenza della password. **Non configurato** (impostazione predefinita) usa `15` giorni.
- **Scadenza password** (solo Kerberos): immettere il numero di giorni che devono trascorrere prima che sia necessario cambiare la password del dispositivo. **Non configurato** (impostazione predefinita) indica che le password utente non scadono mai.
- **URL di modifica della password** (solo Kerberos): immettere l'URL aperto quando l'utente avvia una modifica della password Kerberos.
- **Nome entità** (solo Kerberos): immettere il nome utente dell'entità Kerberos. Non è necessario includere il nome dell'area di autenticazione. Ad esempio, in `user@contoso.com` `user` è il nome dell'entità e `contoso.com` è il nome dell'area di autenticazione.

  > [!TIP]
  > - È anche possibile usare le variabili nel nome dell'entità immettendo parentesi graffe `{{ }}`. Ad esempio, per visualizzare il nome utente, immettere `Username: {{username}}`. 
  > - Prestare tuttavia attenzione alla sostituzione delle variabili poiché le variabili non vengono convalidate nell'interfaccia utente e fanno distinzione tra maiuscole e minuscole. Assicurarsi di immettere le informazioni corrette.
  
- **Codice del sito di Active Directory** (solo Kerberos): immettere il nome del sito Active Directory che deve essere usato dall'estensione Kerberos. Potrebbe non essere necessario modificare questo valore poiché l'estensione Kerberos potrebbe trovare automaticamente il codice del sito Active Directory.
- **Nome cache** (solo Kerberos): immettere il nome GSS (Generic Security Services) della cache Kerberos. Probabilmente non è necessario impostare questo valore.  
- **Messaggio relativo ai requisiti per le password** (solo Kerberos): immettere una versione in formato testo dei requisiti per le password dell'organizzazione visualizzati agli utenti. Il messaggio viene visualizzato se non sono richiesti i requisiti di complessità delle password di Active Directory o non si immette la lunghezza minima della password.  
- **ID aggregazione di app** (solo Kerberos): **aggiungere** gli identificatori del bundle delle app che devono usare l'accesso Single Sign-On nei dispositivi. Queste app ricevono l'accesso al Ticket Granting Ticket Kerberos, il ticket di autenticazione, ed eseguono l'autenticazione degli utenti per i servizi a cui sono autorizzati ad accedere.
- **Mapping dell'area di autenticazione dei domini** (solo Kerberos): **aggiungere** i suffissi DNS di dominio che devono essere mappati all'area di autenticazione. Usare questa impostazione quando i nomi DNS degli host non corrispondono al nome dell'area di autenticazione. Probabilmente non è necessario creare questo mapping da dominio ad area di autenticazione personalizzato.
- **Certificato PKINIT** (solo Kerberos): **selezionare** il certificato PKINIT (Public Key Cryptography for Initial Authentication) che può essere usato per l'autenticazione Kerberos. È possibile scegliere tra i certificati [PKCS](../protect/certficates-pfx-configure.md) o [SCEP](../protect/certificates-scep-configure.md) aggiunti in Intune. Per altre informazioni sui certificati, vedere [Usare i certificati per l'autenticazione in Microsoft Intune](../protect/certificates-configure.md).

## <a name="associated-domains"></a>Domini associati

Con Intune, è possibile:

- Aggiungere molte associazioni da app a dominio.
- Associare molti domini alla stessa app.

Questa funzionalità si applica a:

- macOS 10.15 e versioni successive

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: Tutti i tipi di registrazione

- **ID app**: immettere l'identificatore dell'app da associare a un sito Web. L'identificatore dell'app include l'ID team e un ID bundle: `TeamID.BundleID`.

  L'ID team è una stringa alfanumerica (lettere e numeri) di 10 caratteri generata da Apple per gli sviluppatori di app, ad esempio `ABCDE12345`. [Locate your Team ID](https://help.apple.com/developer-account/#/dev55c3c710c) (Individuare l'ID team) (apre il sito Web di Apple) include ulteriori informazioni.

  L'ID bundle identifica in modo univoco l'app ed è in genere formattato in notazione del nome di dominio inverso. Ad esempio, l'ID bundle di Finder è `com.apple.finder`. Per trovare l'ID bundle, usare AppleScript nel terminale:

  `osascript -e 'id of app "ExampleApp"'`

- **Dominio**: immettere il dominio del sito Web da associare a un'app. Il dominio include un tipo di servizio e un nome host completo, ad esempio `webcredentials:www.contoso.com`.

  È possibile cercare tutti i sottodomini di un dominio associato immettendo `*.` (un carattere jolly asterisco e un punto) prima dell'inizio del dominio. Il punto è obbligatorio. I domini esatti hanno una priorità più alta rispetto ai domini con caratteri jolly. Di conseguenza, i modelli dei domini padre vengono individuati *se* non viene trovata una corrispondenza nel sottodominio completo.

  Il tipo di servizio può essere:

  - **authsrv**: Estensione dell'app Single Sign-On
  - **AppLink**: collegamento universale
  - **webcredentials**: riempimento automatico della password

- **Aggiungi**: selezionare per aggiungere le app e i domini associati.

> [!TIP]
> Per risolvere i problemi, nel dispositivo macOS aprire **Preferenze di sistema** > **Profili**. Verificare che il profilo creato sia presente nell'elenco profili del dispositivo. Se il profilo è incluso, assicurarsi che la **configurazione dei domini associati** si trovi nel profilo e includa i domini e l'ID app corretti.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile configurare le funzionalità del dispositivo in [iOS/iPadOS](ios-device-features-settings.md).
