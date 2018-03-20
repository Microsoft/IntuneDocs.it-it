---
title: Rilasciare certificati PKCS Symantec con Intune
titlesuffix: Azure portal
description: Installare e configurare Connettore di certificati di Intune per rilasciare certificati PKCS dal servizio Web PKI Manager di Symantec ai dispositivi gestiti da Intune
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0f2d37a9033464381de5c23a558d0205f85fe56a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Configurare Connettore di certificati di Intune per il servizio Web PKI Manager di Symantec

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo articolo illustra come installare e configurare Connettore di certificati di Intune per rilasciare certificati PKCS dal servizio Web PKI Manager di Symantec ai dispositivi gestiti da Intune.

Il servizio Web PKI Manager di Symantec viene indicato come CA Symantec in questo articolo. Se Connettore di certificati di Intune è già configurato per il rilascio di certificati PKCS e certificati SCEP dall'autorità di certificazione (CA) Microsoft, è possibile usare lo stesso connettore stesso per configurare e rilasciare certificati PKCS da una CA Symantec. In questo caso, Connettore di certificati di Intune può rilasciare i certificati seguenti:

* Certificati PKCS da una CA Microsoft
* Certificati SCEP da una CA Microsoft
* Certificati PKCS da una CA Symantec

Se si vuole usare Connettore di certificati di Intune per la CA Microsoft e la CA Symantec, è necessario completare prima la configurazione di Connettore di certificati di Intune per la CA Microsoft e quindi eseguire questi passaggi per configurarlo per la CA Symantec.  Per altri dettagli sulla configurazione del Connettore di certificati di Microsoft Intune per l'autorità di certificazione Microsoft, vedere [Come configurare i certificati in Microsoft Intune](certificates-configure.md).

## <a name="prepare-to-install-intune-certificate-connector"></a>Preparativi per l'installazione di Connettore di certificati di Intune

Se si usa già Connettore di certificati di Intune per una CA Microsoft esistente e si vuole aggiungere il supporto della CA Symantec, ignorare questo passaggio e continuare con i passaggi rimanenti dopo aver installato la versione più recente di Connettore di certificati di Intune dal portale di amministrazione di Intune. Questo passaggio è richiesto solo quando si vuole usare Connettore di certificati di Intune per una CA Symantec autonoma.

1. Scegliere una delle versioni del sistema operativo Windows nell'elenco seguente e installarla in un computer:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Creare un utente con privilegi amministrativi e usarlo per completare la procedura seguente.

3. Scaricare gli aggiornamenti più recenti di Windows e installarli se disponibili.

   > [!IMPORTANT]
   > Dopo aver installato gli aggiornamenti di Windows, riavviare il computer.

4. Installare .NET Framework 3.5:

    a. Aprire **Pannello di controllo** > **Programmi e funzionalità** > **Attivazione o disattivazione delle funzionalità Windows**.

    b. Selezionare **.NET Framework 3.5** e installarlo.

## <a name="install-the-symantec-registration-authorization-certificate"></a>Installare il certificato di registrazione dell'autorità (RA) Symantec

Usare la procedura seguente per ottenere il certificato di registrazione dell'autorità (RA) dalla CA Symantec. Per ottenere il certificato RA, è necessaria una sottoscrizione attiva per la CA Symantec.

1. Salvare il frammento di codice seguente come file denominato **certreq.ini** e aggiornarlo in base alle esigenze. Ad esempio: sostituire *Subject name in CN format* (Nome soggetto in formato CN).

   ```
    [Version] 
    Signature="$Windows NT$" 

    [NewRequest] 
    ;Change to your,country code, company name and common name 
    Subject = "Subject Name in CN format"

    KeySpec = 1 
    KeyLength = 2048 
    Exportable = TRUE 
    MachineKeySet = TRUE 
    SMIME = False 
    PrivateKeyArchive = FALSE 
    UserProtected = FALSE 
    UseExistingKeySet = FALSE 
    ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
    ProviderType = 12 
    RequestType = PKCS10 
    KeyUsage = 0xa0 

    [EnhancedKeyUsageExtension] 
    OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication

    ;----------------------------------------------- 
   ```

2. Aprire un prompt dei comandi con privilegi elevati e generare contenuto CSR con il comando seguente:

   `Certreq.exe -new certreq.ini request.csr`

3. Aprire il file request.csr nel Blocco note e copiare il contenuto CSR con il formato seguente:

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Accedere alla CA Symantec e passare a **Get an RA Cert** (Ottieni certificato RA) dalle attività.

   a. Specificare il contenuto CSR dal passaggio 3 nella casella di testo designata.

   b. Specificare il nome descrittivo del certificato nella casella di testo designata.

   c. Fare clic su **Continue**.

      Verrà visualizzato un collegamento di download per il certificato RA.

   d. Scaricare il certificato RA nel computer locale.

5. Importare il certificato RA nell'archivio certificati di Windows:

    a. Aprire una console MMC.

    b. Fare clic su **File** > **Aggiungi o rimuovi snap-in** > **Certificato** e quindi fare clic su **Aggiungi**.

    c. Selezionare **Account computer** e quindi fare clic su **Avanti**.

    d. Selezionare **Computer locale** e quindi fare clic su **Fine**.

    e. Fare clic su **OK** nella finestra **Aggiungi o rimuovi snap-in**. Espandere **Certificati (computer locale)** > **Personale** > **Certificati**.

    f. Fare clic con il pulsante destro del mouse sul nodo **Certificati** e scegliere **Tutte le attività** > **Importa**.

    g. Selezionare il percorso del certificato RA scaricato dalla CA Symantec e fare clic su **Avanti**.

    h. Selezionare **Archivio certificati personali** e quindi fare clic su **Avanti**.

    i. Fare clic su **Fine**. Verrà così importato il certificato RA nell'archivio Computer locale-Personale, insieme alla relativa chiave privata.  

6. Esportare e importare il certificato di chiave privata:

    a. Espandere **Certificati (computer locale)** > **Personale** > **Certificati**.

    b. Selezionare il certificato importato nel passaggio precedente.

    c. Fare clic con il pulsante destro del mouse sul certificato e scegliere **Tutte le attività** > **Esporta**.

    d. Fare clic su **Avanti** e digitare la password.

    e. Selezionare il percorso per l'esportazione e fare clic su **Fine**.

    f. Seguire la stessa procedura nel passaggio 5 per importare il certificato di chiave privata nell'archivio Computer locale-Personale.

7. Copiare l'identificazione personale del certificato RA senza spazi.  Di seguito è riportata un'identificazione personale di esempio:

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > In caso di problemi durante il recupero del certificato RA dalla CA Symantec, contattare il supporto tecnico clienti Symantec.

## <a name="install-intune-certificate-connector"></a>Installare Connettore di certificati di Intune

Se si usa già la versione più recente di Connettore di certificati di Intune per una CA Microsoft esistente e si vuole aggiungere il supporto della CA Symantec, ignorare questo passaggio. In caso contrario, scaricare la versione più recente di Connettore di certificati di Intune dal portale di amministrazione di Intune e seguire queste istruzioni.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **Configurazione dispositivo**.
4. Nel riquadro **Configurazione dispositivo** selezionare **Autorità di certificazione**.
5. Fare clic su **Aggiungi** e selezionare **Scaricare il file del connettore**. Salvare il file scaricato in un percorso a cui è possibile accedere dal server in cui verrà installato. 
3. Eseguire NDESConnectorSetup.exe con privilegi elevati.

    a. Nella schermata **Opzioni di installazione** selezionare **Distribuzione PFX** come illustrato nello screenshot seguente.  Completare il resto dell'installazione con le selezioni predefinite.

   > [!IMPORTANT]
   > Se si vuole configurare Connettore di certificati di Intune per rilasciare certificati da una CA Microsoft e una CA Symantec, selezionare **Distribuzione dei profili SCEP e PFX**. Completare il resto dell'installazione con le selezioni predefinite.

   ![InstallConnector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Configurare Connettore di certificati di Intune

Connettore di certificati di Intune viene installato in `%ProgramFiles%\Microsoft Intune` per impostazione predefinita.

1. Aprire il file %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config nel Blocco note.

    a. Aggiornare il valore della chiave RACertThumbprint con il valore di identificazione personale del certificato copiato nella sezione precedente.  Di seguito viene riportato un esempio.

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. Salvare e chiudere il file.

2. Aprire services.msc.

    a. Selezionare **Servizio Intune Connector**.

    b. Arrestare il servizio e quindi avviarlo.

    c. Chiudere la finestra Servizi.

## <a name="setup-the-intune-administrator-account"></a>Configurare l'account amministratore di Intune

Se si usa già la versione più recente di Connettore di certificati di Intune per una CA Microsoft esistente e si vuole aggiungere il supporto della CA Symantec, ignorare questo passaggio e continuare con i rimanenti. 

1. Avviare l'interfaccia utente di NDES Connector da ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe `

    a. Fare clic sulla scheda **Registrazione** e quindi su **Accedi**.

    b. Specificare le credenziali di amministratore del tenant di Intune nelle caselle di testo designate.

    c. Fare clic su **Accedi**.  Verrà visualizzata una finestra di dialogo di conferma con un messaggio **Registrazione completata** come illustrato nello screenshot seguente.
2. Chiudere l'interfaccia utente di NDES Connector.

![ConfigureConnector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

I certificati PKCS distribuiti per i dispositivi gestiti di Intune devono essere concatenati a un certificato radice attendibile. Per questo è necessario creare un profilo certificato attendibile di Intune con il certificato radice ottenuto dalla CA Symantec.

1. Ottenere un certificato radice attendibile dalla CA Symantec:

    a. Accedere al portale di amministrazione della CA Symantec.

    b. Fare clic su Manage CAs (Gestisci CA) in Tasks (Attività):

    c. Selezionare la CA appropriata nell'elenco delle CA.

    d. Fare clic su Download root certificate (Scarica certificato radice) per scaricare il certificato radice attendibile.

2. Creare un profilo certificato attendibile nel portale di amministrazione di Intune:

    a. Accedere al [portale di Azure](https://portal.azure.com) usando le credenziali di amministratore del tenant di Intune e cercare le risorse di Intune.

    b. Creare un profilo certificato attendibile da **Microsoft Intune** > **Configurazione dispositivo** > **Profili** > **Crea profilo**.

    c. Specificare le informazioni richieste nei campi **Nome** e **Descrizione**, quindi selezionare la piattaforma di destinazione. 

    d. Selezionare il profilo certificato attendibile nell'elenco a discesa Tipo di profilo.

    e. Caricare il certificato radice attendibile ottenuto dalla CA Symantec nel passaggio precedente.

    f. Completare i passaggi rimanenti per la creazione del profilo. 

    g. Fare clic su **Assegnazioni** e selezionare il gruppo appropriato.  Il gruppo assegnato deve includere almeno un utente o un dispositivo.

## <a name="get-the-certificate-profile-oid"></a>Ottenere l'OID del profilo certificato

L'OID del profilo certificato viene associato a un modello di profilo certificato nella CA Symantec.  Per creare un profilo certificato PKCS nel portale di amministrazione di Intune, è necessario specificare il nome del modello di certificato sotto forma di OID del profilo certificato associato a un modello di certificato nella CA Symantec.

1. Accedere al portale di amministrazione della CA Symantec.
2. Fare clic su Manage Certificate Profiles (Gestisci profili certificato).
3. Selezionare il profilo certificato che si vuole usare.
4. Copiare l'OID del profilo certificato. Questo ID è simile al seguente:

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > In caso di problemi con il recupero dell'OID del profilo certificato, contattare il supporto tecnico clienti di Symantec.

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Accedere al [portale di Azure](https://portal.azure.com) usando le credenziali di amministratore del tenant di Intune e cercare le risorse di Intune.
2. Creare un profilo certificato PKCS da **Microsoft Intune** > **Configurazione dispositivo > Profili** > **Crea profilo**.

    a. Specificare le informazioni richieste nei campi **Nome** e **Descrizione**, quindi selezionare la piattaforma di destinazione.

    b. Selezionare **Profilo certificato PKCS** nell'elenco a discesa **Tipo di profilo**.  

    c. Completare i passaggi rimanenti per creare il profilo.

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > I parametri seguenti del profilo certificato PKCS devono essere configurati con valori specificati nella tabella seguente, come illustrato nello screenshot, per rilasciare certificati PKCS tramite Connettore di certificati di Intune dalla CA Symantec. 

    |Parametro del certificato PKCS | Valore | Descrizione |
    | --- | --- | --- |
    | Autorità di certificazione | pki-ws.symauth.com | Questo valore deve essere il nome di dominio completo (FQDN) del servizio di base dell'autorità di certificazione Symantec senza barre finali.  Se non si è sicuri di conoscere l'FQDN del servizio di base della sottoscrizione dell'autorità di certificazione Symantec, contattare il supporto tecnico clienti Symantec. <br><br> Se l'FQDN non è corretto, il Connettore di certificati di Microsoft Intune non rilascerà certificati PKCS dell'autorità di certificazione Symantec.| 
    | Nome autorità di certificazione | Symantec | Questo valore deve essere la stringa **Symantec**. <br><br> Se questo valore viene modificato, Connettore di certificati di Intune non rilascerà certificati PKCS dalla CA Symantec.|
    | Nome modello di certificato | OID del profilo certificato dalla CA Symantec. <br><br> Ad esempio: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| Questo valore deve essere un OID del profilo certificato ottenuto nella sezione precedente dal modello di profilo certificato della CA Symantec. <br><br> Se Connettore di certificati di Intune non riesce a trovare un modello di certificato associato a questo OID del profilo certificato nella CA Symantec, non rilascerà certificati PKCS dalla CA Symantec.|

   > [!NOTE]
   > I profili certificato PKCS per le piattaforme Windows non devono essere associati a un profilo certificato attendibile, ma questo è un requisito per profili per piattaforme non Windows, come Android.

3. Fare clic su **Assegnazioni** e selezionare il gruppo appropriato.  Il gruppo assegnato deve includere almeno un utente o un dispositivo.
 
Dopo aver completato i passaggi precedenti, Connettore di certificati di Intune rilascerà i certificati PKCS dalla CA Symantec ai dispositivi gestiti da Intune nel gruppo assegnato. Questi certificati saranno disponibili nell'archivio Personale dell'archivio certificati Utente corrente del dispositivo gestito da Intune.

### <a name="pkcs-certificate-profile-supported-attributes"></a>Attributi supportati per il profilo certificato PKCS

|Attributo | Formati supportati da Intune | Formati supportati dalla CA cloud Symantec | Risultato |
| --- | --- | --- | --- |
| Nome soggetto |Intune supporta il nome soggetto solo nei tre formati seguenti: <br><br> 1. Nome comune <br> 2. Nome comune include l'indirizzo di posta elettronica <br> 3. Nome comune come indirizzo di posta elettronica <br><br> Di seguito viene riportato un esempio. <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | La CA Symantec supporta attributi aggiuntivi.  Per selezionare attributi aggiuntivi, è necessario che siano definiti con valori fissi nel modello di profilo certificato di Symantec.| Per la richiesta di certificato PKCS viene usato il nome comune o l'indirizzo di posta elettronica. <br><br> In presenza di una selezione di attributi non corrispondenti per il profilo certificato di Intune e il modello di profilo certificato di Symantec, la CA Symantec non rilascerà alcun certificato.|
| SAN | Intune supporta solo i valori seguenti per il campo SAN: <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName (valore codificato) | Anche la CA cloud Symantec supporta questi parametri. Per selezionare attributi aggiuntivi, è necessario che siano definiti con valori fissi nel modello di profilo certificato di Symantec. <br><br> AltNameTypeEmail: se questo tipo non viene trovato nel nome alternativo del soggetto, viene usato il valore da AltNameTypeUpn.  Se anche il valore AltNameTypeUpn non viene trovato nel nome alternativo del soggetto, viene usato il valore da Nome soggetto se è in formato di indirizzo di posta elettronica.  Se il valore non viene ancora trovato, Connettore di certificati di Intune non riesce a rilasciare i certificati. <br><br> Ad esempio: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: se questo tipo non viene trovato nel nome alternativo del soggetto, viene usato il valore da AltNameTypeEmail. Se anche AltNameTypeEmail non viene trovato nel nome alternativo del soggetto, viene usato il valore da Nome soggetto se è in formato di indirizzo di posta elettronica.  Se il valore non viene ancora trovato, Connettore di certificati di Intune non riesce a rilasciare i certificati.  <br><br> Ad esempio: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: se questo tipo non viene trovato nel nome alternativo del soggetto, Connettore di certificati di Intune non riesce a rilasciare i certificati. <br><br> Ad esempio: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **Nota importante:** il valore di questo campo è supportato solo in formato codificato (valore esadecimale) dalla CA Symantec. Qualsiasi valore in questo campo viene quindi convertito da Connettore di certificati di Intune nel formato con codifica in base 64 prima di inviare la richiesta di certificato. **Connettore di certificati di Intune non verifica se questo valore è già codificato o meno.** | Nessuno |

## <a name="troubleshooting"></a>Risoluzione dei problemi

Sono disponibili log del servizio Connettore di certificati di Intune in `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs` nel computer di NDES Connector. Aprire i log in [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) e cercare i messaggi di eccezione o errore.

| Problema/Messaggio di errore | Procedura per la risoluzione |
| --- | --- |
| Impossibile effettuare l'accesso con l'account di amministratore tenant di Intune nell'interfaccia utente di NDES Connector | Questa situazione può verificarsi quando Connettore di certificati locale non è abilitato nel portale di amministrazione di Intune. Per risolvere questo problema, effettuare la procedura seguente: <br><br> Dall'interfaccia utente di Silverlight: <br> 1. Accedere al [portale di amministrazione di Intune](https://admin.manage.microsoft.com) <br> 2. Fare clic su Amministrazione <br> 3. Selezionare Gestione di dispositivi mobili > Connettore di certificati <br> 4. Fare clic su **Configura Connettore di certificati locale** <br> 5. Selezionare la casella di controllo **Abilita Connettore di certificati** <br> 6. Fare clic su **OK**. <br><br>Oppure <br><br> Dall'interfaccia utente del portale di Azure: <br> 1. Accedere al [portale di Azure](https://portal.azure.com) <br> 2. Passare a Microsoft Intune <br> 3. Selezionare **Configurazione del dispositivo** > **Autorità di certificazione** <br> 4. Fare clic su **Abilita**. <br><br> Dopo aver completato i passaggi precedenti dall'interfaccia utente di Silverlight o dal portale di Azure, provare a eseguire l'accesso con lo stesso account amministratore tenant di Intune nell'interfaccia utente di NDES Connector. |
| Impossibile trovare il certificato di NDES Connector. <br><br> System.ArgumentNullException: Il valore non può essere Null. | Connettore di certificati di Intune mostra questo errore se l'account amministratore tenant di Intune non ha mai eseguito l'accesso all'interfaccia utente di NDES Connector. <br><br> Se l'errore persiste, riavviare Connettore del servizio Intune. <br><br> 1. Aprire services.msc <br> 2. Selezionare **Servizio Intune Connector**. <br> 3. Fare clic con il pulsante destro del mouse e scegliere **Riavvia**.|
| NDES Connector - IssuePfx -Eccezione generica: <br> System.NullReferenceException: Riferimento oggetto non impostato su un'istanza di un oggetto. | Questo errore è temporaneo. Riavviare Connettore del servizio Intune. <br><br> 1. Aprire services.msc <br> 2. Selezionare **Servizio Intune Connector** <br> 3. Fare clic con il pulsante destro del mouse e scegliere **Riavvia**. |
| Provider Symantec: Impossibile ottenere i criteri Symantec "Timeout dell'operazione" | Connettore di certificati di Intune ha ricevuto l'errore di timeout dell'operazione durante la comunicazione con la CA Symantec. Se l'errore persiste, aumentare il valore di timeout di connessione e riprovare. <br><br> Per aumentare il timeout della connessione: <br> 1. Passare al computer NDES Connector. <br>2. Aprire il file `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` nel Blocco note. <br> 3. Aumentare il valore di timeout per il parametro seguente: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Riavviare il servizio Intune Connector. <br><br> Se il problema persiste, contattare il supporto tecnico clienti Symantec. |
| Provider Symantec: Impossibile ottenere il certificato client | Connettore di certificati di Intune non è riuscito a recuperare il certificato RA dall'archivio certificati Computer locale-Personale. Per risolvere questo problema, assicurarsi di installare il certificato RA nell'archivio certificati Computer locale-Personale insieme alla relativa chiave privata. <br><br> **Nota:** il certificato RA deve essere ottenuto dalla CA Symantec. Per altri dettagli, contattare il supporto tecnico clienti Symantec. | 
| Provider Symantec: Impossibile ottenere i criteri Symantec "Richiesta interrotta: Impossibile creare il canale sicuro SSL/TLS." | Questo errore si verifica negli scenari seguenti: <br><br> 1. Il servizio Connettore di certificati di Intune non dispone di autorizzazioni sufficienti per leggere il certificato RA insieme alla relativa chiave privata dall'archivio certificati Computer locale-Personale. Per risolvere questo problema, controllare l'account del contesto di esecuzione del servizio Connettore in services.msc. Il servizio Connettore deve essere eseguito nel contesto di NT AUTHORITY\SYSTEM. <br><br> 2. Il profilo certificato PKCS nel portale di amministrazione di Intune potrebbe essere configurato con nome di dominio completo del servizio di base della CA Symantec. Il nome di dominio completo è simile a `pki-ws.symauth.com`. Per risolvere questo problema, rivolgersi al supporto tecnico clienti Symantec per verificare se l'URL è corretto per la sottoscrizione. <br><br> 3. Connettore di certificati di Intune non riesce a eseguire l'autenticazione con la CA Symantec usando il certificato RA perché non è in grado di recuperare la chiave privata. Per risolvere questo problema, assicurarsi di installare il certificato RA nell'archivio e la relativa chiave privata nell'archivio certificati Computer locale-Personale. <br><br> Se il problema persiste, contattare il supporto tecnico clienti Symantec. |
| Provider Symantec: Impossibile ottenere i criteri Symantec "Un elemento della richiesta non è comprensibile." | Connettore di certificati di Intune non è riuscito a ottenere il modello di profilo certificato di Symantec, perché l'OID del profilo client non corrisponde al profilo del certificato di Intune. In un altro caso, Connettore di certificati di Intune non riesce a trovare il modello di profilo certificato associato all'OID di profilo client specificato nella CA Symantec. <br><br> Per risolvere questo problema, assicurarsi di ottenere l'OID di profilo client corretto dal modello di certificato Symantec nella CA Symantec. Aggiornare quindi il profilo del certificato PKCS nel portale di amministrazione di Intune. <br><br> Ottenere l'OID del profilo client dalla CA Symantec: <br> 1. Accedere al portale di amministrazione della CA Symantec. <br> 2. Fare clic su Manage Certificate Profiles (Gestisci profili certificato). <br> 3. Selezionare il profilo certificato che si vuole usare. <br> 4. Ottenere l'OID del profilo certificato. Questo ID è simile al seguente: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Aggiornare il profilo certificato PKCS con l'OID del profilo certificato corretto: <br>1. Accedere al portale di amministrazione di Intune. <br> 2. Passare al profilo certificato PKCS e fare clic su **Modifica**. <br> 3. Aggiornare l'OID del profilo certificato nel campo Nome modello di certificato. <br> 4. Salvare il profilo certificato PKCS. |
| Provider Symantec: Verifica dei criteri non riuscita. <br><br> L'attributo non rientra nell'elenco degli attributi per i modelli di certificato supportati di Symantec | La CA Symantec mostra questo messaggio quando è presente una discrepanza tra il modello di profilo certificato Symantec e il profilo certificato di Intune. Questo problema si è verificato probabilmente a causa di attributi non corrispondenti in SubjectName o SubjectAltName. <br><br> Per risolvere questo problema, assicurarsi di selezionare attributi supportati da Intune per SubjectName e SubjectAltName nel modello di profilo certificato di Symantec. Per altre informazioni, vedere gli attributi supportati da Intune nella sezione relativi ai parametri del certificato. |
| Alcuni dispositivi utente non ricevono certificati PKCS dalla CA Symantec. | Questo problema si verifica quando il nome dell'entità utente contiene caratteri speciali come il carattere di sottolineatura, ad esempio: `global_admin@intune.onmicrosoft.com`. <br><br> La CA Symantec non supporta caratteri speciali in mail_firstname e mail_lastname. <br><br> La procedura seguente consente di risolvere il problema: <br><br> 1.   Accedere al portale di amministrazione della CA Symantec. <br> 2. Passare a Manage Certificate Profiles (Gestisci profili certificato). <br> 3.   Fare clic sul profilo di certificato usato per Intune. <br> 4.  Fare clic sul collegamento Customize options (Opzioni di personalizzazione). <br> 5.   Fare clic sul pulsante Advanced options (Opzioni avanzate). <br> 6.  In Certificate fields – Subject DN (Campi certificato - DN soggetto) aggiungere il campo Common Name (CN) (Nome comune - CN) ed eliminare il campo esistente Common Name (CN) (Nome comune - CN). L'aggiunta e l'eliminazione devono essere eseguite insieme. <br> 7.    Fare clic su Save (Salva). <br><br> Con la modifica precedente, il profilo certificato di Symantec richiede "CN =<upn>" anziché mail_firstname e mail_lastname. |
| L'utente ha eliminato manualmente un certificato già distribuito dal dispositivo. | Intune ridistribuisce lo stesso certificato durante la successiva archiviazione o applicazione dei criteri. In questo caso, NDES Connector non riceve una richiesta di certificato PKCS. |

## <a name="next-steps"></a>Passaggi successivi

- Usare le informazioni fornite in questo articolo oltre alle informazioni in [Informazioni sui profili di dispositivo in Microsoft Intune](device-profiles.md) per gestire i dispositivi dell'organizzazione e i relativi certificati.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Installare Connettore di certificati di Intune e selezionare Distribuzione PFX"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Configurare Connettore di certificati di Intune"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Creare un profilo certificato PKCS nel portale di Azure"
