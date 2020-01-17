---
title: Impostazioni delle funzionalità dei dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare le impostazioni per configurare i dispositivi macOS per AirPrint e personalizzare la finestra di accesso per visualizzare o nascondere pulsanti di alimentazione in Microsoft Intune. Vedere i passaggi per ottenere l'indirizzo IP, il percorso e le impostazioni della porta di un server AirPrint nella rete. Usare queste impostazioni in un profilo di configurazione del dispositivo per configurare le funzionalità dei dispositivi macOS.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
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
ms.openlocfilehash: 791e2a1313480bdf1ad95988d48664d6620ba0b3
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206347"
---
# <a name="macos-device-feature-settings-in-intune"></a>Impostazioni relative alle funzionalità dei dispositivi macOS in Intune

Intune include alcune impostazioni integrate per personalizzare le funzionalità nei dispositivi macOS. Ad esempio, gli amministratori possono aggiungere stampanti AirPrint, scegliere la modalità di accesso degli utenti, configurare i controlli di risparmio energia, usare Single Sign-On l'autenticazione e altro ancora.

Usare queste funzionalità per controllare i dispositivi macOS nella soluzione di gestione di dispositivi mobili (MDM).

L'articolo elenca queste impostazioni e descrive la funzione di ogni impostazione. Vengono inoltre elencati i passaggi per ottenere l'indirizzo IP, il percorso e la porta delle stampanti AirPrint tramite l'app Terminale (emulatore). Per altre informazioni sulle funzionalità del dispositivo, vedere [aggiungere impostazioni della funzionalità del dispositivo iOS o MacOS](device-features-configure.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione dei dispositivi macOS](device-features-configure.md).

> [!NOTE]
> Queste impostazioni si applicano a tipi di registrazione diversi, con alcune impostazioni che si applicano a tutte le opzioni di registrazione. Per ulteriori informazioni sui diversi tipi di registrazione, vedere la pagina relativa alla [registrazione MacOS](../enrollment/macos-enroll.md).

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi 

- **Indirizzo IP**: immettere l'indirizzo IPv4 o IPv6 della stampante. Se si usano i nomi host per identificare le stampanti, è possibile ottenere l'indirizzo IP effettuando il ping della stampante nell'app Terminale. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
- **Percorso**: immettere il percorso della stampante. il percorso è in genere `ipp/print` per le stampanti di rete. Per informazioni più dettagliate, vedere [Ottenere l'indirizzo IP e il percorso](#get-the-ip-address-and-path) (in questo articolo).
- **Porta** (iOS 11.0 e versioni successive): immettere la porta di ascolto della destinazione AirPrint. Se si omette questa proprietà, AirPrint usa la porta predefinita.
- **TLS** (iOS 11.0 e versioni successive): selezionare **Abilita** per proteggere le connessioni AirPrint con Transport Layer Security (TLS).

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

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: tutti i tipi di registrazione

- **File, cartelle e app personalizzate**: **aggiungere** il percorso di un file, una cartella, un'app personalizzata o un'app di sistema che si vuole aprire quando un utente accede al dispositivo. Le app di sistema o le app compilate o personalizzate per l'organizzazione si trovano in genere nella cartella `Applications`, con un percorso simile a `/Applications/AppName.app`. 

  È possibile aggiungere molti file, cartelle e app. Ad esempio, immettere:  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  Quando si aggiunge un'app, una cartella o un file, assicurarsi di immettere il percorso corretto. Non tutti gli elementi si trovano nella cartella `Applications`. Se un utente sposta un elemento da una posizione a un'altra, il percorso viene modificato. Questo elemento spostato non verrà aperto quando l'utente accede.

## <a name="login-window"></a>Finestra di accesso

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

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

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: tutti i tipi di registrazione 

- **Tipo di estensione dell'app SSO**: scegliere il tipo di estensione dell'app SSO per le credenziali. Le opzioni disponibili sono:

  - **Non configurato**: non vengono usate le estensioni dell'app. Per disabilitare un'estensione dell'app, impostare il tipo di estensione dell'app SSO su **non configurato**.
  - **Reindirizzamento**: usare un'estensione di app di reindirizzamento generica e personalizzabile per eseguire l'accesso SSO con flussi di autenticazione moderni. Assicurarsi di conoscerne l'estensione e l'ID del team per l'estensione dell'app dell'organizzazione.
  - **Credenziale**: usare un'estensione di app per le credenziali personalizzabile e generica per eseguire l'accesso SSO con i flussi di autenticazione di richiesta-risposta. Assicurarsi di avere familiarità con l'ID estensione e l'ID del team per l'estensione dell'app SSO dell'organizzazione.  
  - **Kerberos**: usare l'estensione Kerberos predefinita di Apple, inclusa in macOS Catalina 10,15 e versioni successive. Questa opzione è una versione specifica di Kerberos dell'estensione dell'app per le **credenziali** .

  > [!TIP]
  > Con i tipi **Reindirizzamento** e **credenziali** è possibile aggiungere i propri valori di configurazione per passare attraverso l'estensione. Se si usano le **credenziali**, provare a usare le impostazioni di configurazione predefinite fornite da Apple nel tipo **Kerberos** .

- **ID estensione** (Reindirizzamento e credenziali): immettere l'identificatore del bundle che identifica l'estensione dell'app SSO, ad esempio `com.apple.ssoexample`.
- **ID team** (Reindirizzamento e credenziali): immettere l'identificatore del team dell'estensione dell'app SSO. Un identificatore del team è una stringa alfanumerica (numeri e lettere) di 10 caratteri generata da Apple, ad esempio `ABCDE12345`. 

  [Individuare l'ID del team](https://help.apple.com/developer-account/#/dev55c3c710c) (aprire il sito Web di Apple) con ulteriori informazioni.

- **Area** di autenticazione (credenziale e Kerberos): immettere il nome dell'area di autenticazione. Il nome dell'area di autenticazione deve essere in maiuscolo, ad esempio `CONTOSO.COM`. In genere, il nome dell'area di autenticazione corrisponde al nome di dominio DNS, ma in maiuscolo.

- **Domini** (Credential e Kerberos): immettere il dominio o i nomi host dei siti che possono eseguire l'autenticazione tramite SSO. Ad esempio, se il sito Web è `mysite.contoso.com`, `mysite` è il nome host e `contoso.com` è il nome di dominio. Quando gli utenti si connettono a uno di questi siti, l'estensione dell'app gestisce la richiesta di autenticazione. Questa autenticazione consente agli utenti di usare l'ID del viso, l'ID tocco o il pincode/codice Apple per accedere.

  - Tutti i domini nei profili di Intune dell'estensione dell'app Single Sign-On devono essere univoci. Non è possibile ripetere un dominio in nessun profilo di estensione dell'app di accesso, anche se si usano tipi diversi di estensioni di app SSO.
  - Questi domini non fanno distinzione tra maiuscole e minuscole.

- **URL** (solo Reindirizzamento): immettere i prefissi URL dei provider di identità per conto del quale l'estensione di reindirizzamento app esegue l'accesso SSO. Quando un utente viene reindirizzato a questi URL, l'estensione dell'app SSO interviene e richiede l'accesso SSO.

  - Tutti gli URL nei profili di estensione dell'app Single Sign-On di Intune devono essere univoci. Non è possibile ripetere un dominio in nessun profilo di estensione dell'app SSO, anche se si usano tipi diversi di estensioni di app SSO.
  - Gli URL devono iniziare con http://o https://.

- **Configurazione aggiuntiva** (Reindirizzamento e credenziali): immettere dati aggiuntivi specifici dell'estensione da passare all'estensione dell'app SSO:
  - **Chiave**: immettere il nome dell'elemento che si vuole aggiungere, ad esempio `user name`.
  - **Tipo**: immettere il tipo di dati. Le opzioni disponibili sono:

    - Stringa
    - Booleano: in **valore di configurazione**immettere `True` o `False`.
    - Integer: in **valore di configurazione**immettere un numero.
    
  - **Valore**: immettere i dati.
  
  - **Aggiungi**: selezionare questa impostazione per aggiungere le chiavi di configurazione.

- **Utilizzo Keychain** (solo Kerberos): scegliere **blocco** per impedire il salvataggio e l'archiviazione delle password nel keychain. **Non configurato** (impostazione predefinita) consente il salvataggio e l'archiviazione delle password nel keychain.  
- **ID viso, ID tocco o codice** di accesso (solo Kerberos): **Richiedi** impone agli utenti di immettere il proprio ID viso, ID tocco o il codice di accesso Apple per accedere ai domini aggiunti. **Non configurato** (impostazione predefinita) non richiede agli utenti di usare la biometria o il codice di accesso per accedere.
- **Area di autenticazione predefinita** (solo Kerberos): scegliere **Abilita** per impostare il valore dell' **area di autenticazione** immesso come area di autenticazione predefinita. **Non configurato** (impostazione predefinita) non imposta un'area di autenticazione predefinita.

  > [!TIP]
  > - **Abilitare** questa impostazione se si stanno configurando più estensioni dell'app SSO Kerberos nell'organizzazione.
  > - **Abilitare** questa impostazione se si usano più aree di autenticazione. Imposta il valore dell' **area di autenticazione** immesso come area di autenticazione predefinita.
  > - Se si dispone solo di un'area di autenticazione, lasciarla **non configurata** (impostazione predefinita).

- **Individuazione** automatica (solo Kerberos): se impostato su **blocca**, l'estensione Kerberos non usa automaticamente LDAP e DNS per determinare il nome del sito Active Directory. **Non configurato** (impostazione predefinita) consente all'estensione di individuare automaticamente il nome del sito Active Directory.
- **Modifiche della password** (solo Kerberos): il **blocco** impedisce agli utenti di modificare le password usate per accedere ai domini immessi. **Non configurato** (impostazione predefinita) consente le modifiche delle password.  
- **Sincronizzazione password** (solo Kerberos): scegliere **Abilita** per sincronizzare le password locali degli utenti per Azure ad. **Non configurato** (impostazione predefinita) Disabilita la sincronizzazione delle password con Azure ad. Usare questa impostazione come alternativa o backup per SSO. Questa impostazione non funziona se gli utenti hanno eseguito l'accesso con un account Apple Mobile.
- **Complessità delle password di Windows Server Active Directory** (solo Kerberos): scegliere **Richiedi** per forzare le password utente per soddisfare i requisiti di complessità delle password di Active Directory. Per ulteriori informazioni, vedere la [password deve soddisfare i requisiti di complessità](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) . **Non configurato** (impostazione predefinita) non richiede che gli utenti soddisfino il requisito per la password di Active Directory.
- **Lunghezza minima password** (solo Kerberos): immettere il numero minimo di caratteri che possono creare la password di un utente. **Non configurato** (impostazione predefinita) non impone la lunghezza minima della password per gli utenti.
- **Limite di riutilizzo delle password** (solo Kerberos): immettere il numero di nuove password, da 1-24, che devono essere utilizzate fino a quando non sarà possibile riutilizzare una password precedente nel dominio. **Non configurato** (impostazione predefinita) non impone un limite di riutilizzo delle password.
- **Validità minima password** (solo Kerberos): immettere il numero di giorni per cui è necessario usare una password nel dominio prima che un utente possa modificarlo. **Non configurato** (impostazione predefinita) non impone una validità minima delle password prima che possano essere modificate.
- **Notifica di scadenza password** (solo Kerberos): immettere il numero di giorni prima della scadenza di una password per la quale gli utenti riceveranno una notifica della scadenza della password. **Non configurato** (impostazione predefinita) USA `15` giorni.
- **Scadenza password** (solo Kerberos): immettere il numero di giorni che devono trascorrere prima che sia necessario cambiare la password del dispositivo. **Non configurato** (impostazione predefinita) indica che le password utente non scadono mai.
- **URL di modifica password** (solo Kerberos): immettere l'URL che viene avviato quando l'utente avvia una modifica della password Kerberos.
- **Nome entità** (solo Kerberos): immettere il nome utente dell'entità Kerberos. Non è necessario includere il nome dell'area di autenticazione. Ad esempio, in `user@contoso.com`, `user` è il nome dell'entità e `contoso.com` è il nome dell'area di autenticazione.

  > [!TIP]
  > - È anche possibile usare le variabili nel nome principale immettendo parentesi graffe `{{ }}`. Ad esempio, per visualizzare il nome utente, immettere `Username: {{username}}`. 
  > - Tuttavia, prestare attenzione con la sostituzione delle variabili perché le variabili non vengono convalidate nell'interfaccia utente e fanno distinzione tra maiuscole e minuscole. Assicurarsi di immettere le informazioni corrette.
  
- **Active Directory codice sito** (solo Kerberos): immettere il nome del sito Active Directory che deve essere utilizzato dall'estensione Kerberos. Potrebbe non essere necessario modificare questo valore, perché l'estensione Kerberos potrebbe trovare automaticamente il codice del sito Active Directory.
- **Nome cache** (solo Kerberos): immettere il nome GSS (Generic Security Services) della cache Kerberos. Probabilmente non è necessario impostare questo valore.  
- **Messaggio requisiti password** (solo Kerberos): immettere una versione in formato testo dei requisiti per le password dell'organizzazione visualizzati dagli utenti. Il messaggio viene visualizzato se non sono richiesti i requisiti di complessità delle password di Active Directory o non si immette la lunghezza minima della password.  
- **ID bundle dell'app** (solo Kerberos): **aggiungere** gli identificatori del bundle dell'app che devono usare Single Sign-on nei dispositivi. A queste app viene concesso l'accesso al ticket di concessione ticket Kerberos, il ticket di autenticazione e l'autenticazione degli utenti ai servizi a cui sono autorizzati ad accedere.
- **Mapping dell'area di autenticazione del dominio** (solo Kerberos): **aggiungere** i suffissi DNS di dominio che devono essere mappati all'area di autenticazione. Usare questa impostazione quando i nomi DNS degli host non corrispondono al nome dell'area di autenticazione. Probabilmente non è necessario creare questo mapping da dominio a area di autenticazione personalizzato.
- **Certificato PKINIT** (solo Kerberos): **selezionare** il certificato di crittografia a chiave pubblica per l'autenticazione iniziale (PKINIT) che può essere usato per l'autenticazione Kerberos. È possibile scegliere tra i certificati [PKCS](../protect/certficates-pfx-configure.md) o [SCEP](../protect/certificates-scep-configure.md) aggiunti in Intune. Per altre informazioni sui certificati, vedere [usare i certificati per l'autenticazione in Microsoft Intune](../protect/certificates-configure.md).

## <a name="associated-domains"></a>Domini associati

Con Intune, è possibile:

- Aggiungere molte associazioni da app a dominio.
- Associare molti domini alla stessa app.

Questa funzionalità si applica a:

- macOS 10.15 e versioni successive

### <a name="settings-apply-to-all-enrollment-types"></a>Le impostazioni si applicano a: tutti i tipi di registrazione

- **ID app**: immettere l'identificatore dell'app da associare a un sito Web. L'identificatore dell'app include l'ID del team e un ID bundle: `TeamID.BundleID`.

  Il team ID è una stringa alfanumerica (lettere e numeri) a 10 caratteri generata da Apple per gli sviluppatori di app, ad esempio `ABCDE12345`. [Individuare l'ID Team](https://help.apple.com/developer-account/#/dev55c3c710c) (apre il sito Web di Apple) con ulteriori informazioni.

  L'ID bundle identifica in modo univoco l'app ed è in genere formattato in notazione del nome di dominio inverso. Ad esempio, l'ID bundle di Finder viene `com.apple.finder`. Per trovare l'ID bundle, usare AppleScript nel terminale:

  `osascript -e 'id of app "ExampleApp"'`

- **Dominio**: immettere il dominio del sito Web da associare a un'app. Il dominio include un tipo di servizio e un nome host completo, ad esempio `webcredentials: www.contoso.com`.

  È possibile trovare la corrispondenza con tutti i sottodomini di un dominio associato immettendo `*.` (un carattere jolly asterisco e un punto) prima dell'inizio del dominio. Il periodo è obbligatorio. I domini esatti hanno una priorità più alta rispetto ai domini con caratteri jolly. Di conseguenza, i modelli dei domini padre vengono confrontati *se* una corrispondenza non viene trovata nel sottodominio completo.

  Il tipo di servizio può essere:

  - **authsrv**: Estensione dell'app Single Sign-On
  - **AppLink**: collegamento universale
  - **webcredentials**: riempimento automatico password

- **Aggiungi**: selezionare questa aggiunta per aggiungere le app e i domini associati.

> [!TIP]
> Per risolvere i problemi, nel dispositivo macOS aprire **Preferenze di sistema** > **profili**. Verificare che il profilo creato sia presente nell'elenco profili dispositivo. Se è elencato, assicurarsi che la **configurazione dei domini associati** sia nel profilo e che includa i domini e l'ID app corretti.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È anche possibile configurare le funzionalità del dispositivo in [iOS](ios-device-features-settings.md).
