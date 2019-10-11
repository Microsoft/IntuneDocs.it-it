---
title: Rilasciare certificati DigiCert PKCS con Microsoft Intune
titleSuffix: Microsoft Intune
description: Installare e configurare il Connettore di certificati di Microsoft Intune per rilasciare certificati PKCS dalla piattaforma DigiCert PKI nei servizi gestiti da Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1679eb656e04296e53d8994dcd47144621c99d0c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721773"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>Configurare il Connettore di certificati di Intune per la piattaforma DigiCert PKI  

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usare il Connettore di certificati di Intune per rilasciare certificati PKCS dalla piattaforma DigiCert PKI nei servizi gestiti da Intune. È possibile usare il Connettore solo con un'autorità di certificazione (CA) DigiCert o con una CA DigiCert e una CA Microsoft.  
> [!TIP]  
> DigiCert ha acquisito il settore della sicurezza dei siti Web di Symantec e le soluzioni PKI correlate. Per altre informazioni su questa modifica, vedere l'[articolo del supporto tecnico Symantec](https://support.symantec.com/en_US/article.INFO4722.html).

Se si usa già il Connettore di certificati di Intune per rilasciare certificati da una CA Microsoft usando PKCS o System Center Endpoint Protection, è possibile usare lo stesso connettore per configurare e rilasciare certificati PKCS da una CA DigiCert. Dopo aver completato la configurazione per supportare la CA DigiCert, il Connettore di certificati di Intune può rilasciare i certificati seguenti:

* Certificati PKCS da una CA Microsoft
* Certificati PKCS da una CA DigiCert
* Certificati Endpoint Protection da una CA Microsoft

Se il connettore non è installato ma si prevede di usarlo sia per una CA Microsoft che per una CA DigiCert, completare prima la configurazione del connettore per la CA Microsoft. Tornare quindi a questo articolo per configurarlo anche per il supporto di DigiCert. Per altre informazioni sui profili certificato e sul connettore, vedere [Configurare un profilo certificato per i dispositivi in Microsoft Intune](certificates-configure.md).  

Se si usa il connettore solo con la CA DigiCert, è possibile usare le istruzioni in questo articolo per installare e configurare il connettore. 

## <a name="prerequisites"></a>Prerequisiti  
- **Una sottoscrizione attiva alla CA DigiCert**: la sottoscrizione è necessaria per ottenere un certificato dell'autorità di registrazione dalla CA DigiCert.

## <a name="install-the-digicert-ra-certificate"></a>Installare il certificato dell'autorità di registrazione DigiCert  
 
1. Salvare il frammento di codice seguente come file denominato **certreq.ini** e aggiornarlo in base alle esigenze. Ad esempio: *Nome soggetto in formato CN*.
 
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

2. Aprire un prompt dei comandi con privilegi elevati e generare una richiesta di firma del certificato usando il comando seguente:

   `Certreq.exe -new certreq.ini request.csr`

3. Aprire il file request.csr nel Blocco note e copiare il contenuto della richiesta di firma del certificato con il formato seguente:


        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. Accedere alla CA DigiCert e passare a **Get a RA Cert** (Ottieni certificato autorità di registrazione).

   a. Nella casella di testo specificare il contenuto della richiesta di firma del certificato del passaggio 3. 

   b. Immettere un nome descrittivo per il certificato.

   c. Selezionare **Continua**. 

   d. Usare il collegamento visualizzato per scaricare il certificato autorità di registrazione nel computer locale.

5. Importare il certificato autorità di registrazione nell'archivio certificati di Windows:

   a. Aprire una console MMC.

   b. Selezionare **File** > **Aggiungi o rimuovi snap-in** > **Certificato** > **Aggiungi**. 

   c. Selezionare **Account del computer** > **Avanti**.

   d. Selezionare **Computer locale** > **Fine**. 

   e. Selezionare **OK** nella finestra di dialogo **Aggiungi o rimuovi snap-in**. Espandere **Certificati (computer locale)** > **Personale** > **Certificati**.

   f. Fare clic con il pulsante destro del mouse sul nodo **Certificati** e scegliere **Tutte le attività** > **Importa**.  

   g. Selezionare il percorso del certificato autorità di registrazione scaricato dalla CA DigiCert e fare clic su **Avanti**.

   h. Selezionare **Personal Certificate Store** (Archivio certificati personali) > **Avanti**. 

   i. Selezionare **Fine** per importare il certificato autorità di registrazione e la chiave privata relativa nell'archivio **Computer locale-Personale**.  

6. Esportare e importare il certificato di chiave privata: 

   a. Espandere **Certificati (computer locale)** > **Personale** > **Certificati**.

   b. Selezionare il certificato importato nel passaggio precedente.

   c. Fare clic con il pulsante destro del mouse sul certificato e selezionare **Tutte le attività** > **Esporta**.

   d. Selezionare **Avanti** e immettere la password.

   e. Selezionare il percorso per l'esportazione e quindi **Fine**.

   f. Usare la procedura a partire dal passaggio 5 per importare il certificato della chiave privata nell'archivio **Computer locale-Personale**.

   g. Registrare una copia dell'identificazione personale del certificato dell'autorità di registrazione senza spazi. Di seguito è riportata un'identificazione personale di esempio: 

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
    
    > [!NOTE]
    > Se si necessita di assistenza per ottenere il certificato dell'autorità di registrazione dalla CA DigiCert, contattare il [supporto tecnico DigiCert](mailto:enterprise-pkisupport@digicert.com).  

## <a name="prepare-to-install-intune-certificate-connector"></a>Preparativi per l'installazione di Connettore di certificati di Intune
> [!TIP]  
> Questa sezione si applica se si usa il Connettore di certificati di Intune solo con una CA DigiCert. Se si usa il Connettore di certificati di Intune con una CA Microsoft e si vuole aggiungere il supporto della CA DigiCert, passare a [Configurare il connettore per supportare DigiCert](#configure-the-connector-to-support-digicert).  

1. Scegliere una delle versioni del sistema operativo Windows dall'elenco seguente e installarla in un computer:
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. Creare un utente con privilegi amministrativi e usarlo per completare la procedura seguente.

3. Verificare gli aggiornamenti più recenti di Windows e installarli se disponibili. Dopo aver installato gli aggiornamenti di Windows, riavviare il computer.

4. Installare .NET Framework 3.5:

   a. Aprire **Pannello di controllo** > **Programmi e funzionalità** > **Attivazione o disattivazione delle funzionalità Windows**.

   b. Selezionare **.NET Framework 3.5** e installarlo.  

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>Installare il Connettore di certificati di Intune per l'uso con DigiCert  

> [!TIP]  
> Se si usa il Connettore di certificati di Intune con una CA Microsoft e si vuole aggiungere il supporto della CA DigiCert, passare a [Configurare il connettore per supportare DigiCert](#configure-the-connector-to-support-digicert).  

Scaricare la versione più recente del Connettore di certificati di Intune dal portale di amministrazione di Intune e seguire queste istruzioni.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  

2. Selezionare **Configurazione del dispositivo** > **Connettori di certificati** > **+ Aggiungi**.  

3. Selezionare **Scaricare il software del connettore del certificato**. Salvare il software in un percorso a cui è possibile accedere dal server in cui verrà installato.  

   ![Scaricare il software del connettore](./media/certificates-digicert-configure/connector-download.png)
   
4. Nel server in cui si vuole installare il connettore eseguire **NDESConnectorSetup.exe** con privilegi elevati. 

5. Nella pagina **Opzioni di installazione** selezionare **PFX Distribution** (Distribuzione PFX).  
   
   ![Selezionare la distribuzione PFX](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Se si vuole usare il Connettore di certificati di Intune per rilasciare certificati da una CA Microsoft e una CA DigiCert, selezionare **Distribuzione dei profili SCEP e PFX**. 

6. Usare le selezioni predefinite per completare la configurazione del connettore.

## <a name="configure-the-connector-to-support-digicert"></a>Configurare il connettore per supportare DigiCert

Per impostazione predefinita, il Connettore di certificati di Intune è installato in **%Programmi%\Microsoft Intune\NDESConnectorSvc**.

1. Nella cartella **NDESConnectorSvc** aprire il file **NDESConnector.exe.config** nel Blocco note.

   a. Aggiornare il valore della chiave `RACertThumbprint` con il valore di identificazione personale del certificato copiato nella sezione precedente. Ad esempio:

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   
   b. Salvare e chiudere il file.

2. Aprire **services.msc**:

   a. Selezionare **Servizio Intune Connector**.

   b. Arrestare il servizio e quindi avviarlo.

   c. Chiudere la finestra del servizio.

## <a name="set-up-the-intune-administrator-account"></a>Configurare l'account amministratore di Intune  

> [!TIP]  
> Se si usa il Connettore di certificati di Intune con una CA Microsoft e si vuole aggiungere il supporto della CA DigiCert, passare a [Creare un profilo certificato attendibile](#create-a-trusted-certificate-profile).   
 
1. Aprire l'interfaccia utente NDES Connector da **%Programmi%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**.  

2. Nella scheda **Registrazione** selezionare **Accedi**.

3. Specificare le credenziali di amministratore del tenant di Intune.

4. Selezionare **Accedi** e quindi selezionare **OK** per confermare la registrazione. A questo punto è possibile chiudere l'interfaccia utente NDES Connector.
   
   ![Interfaccia NDES Connector con messaggio "Registrazione completata"](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)



## <a name="create-a-trusted-certificate-profile"></a>Creare un profilo certificato attendibile

I certificati PKCS distribuiti per i dispositivi gestiti di Intune devono essere concatenati a un certificato radice trusted. Per stabilire tale concatenazione, creare un profilo certificato attendibile di Intune con il certificato radice ottenuto dalla CA DigiCert.

1. Ottenere un certificato radice trusted dalla CA DigiCert:

    a. Accedere al portale di amministrazione della CA DigiCert.

    b. Selezionare **Manage CAs** (Gestione CA) da **Tasks** (Attività). 

    c. Selezionare la CA appropriata dall'elenco.  

    d. Selezionare **Download root certificate** (Scarica certificato radice) per scaricare il certificato radice trusted.

2. Creare un profilo certificato attendibile nel portale di Intune:

   a. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).

   b. Selezionare **Configurazione del dispositivo** > **Gestisci** > **Profili** > **Crea profilo**.

   c. Immettere **Nome** e **Descrizione** per il profilo di certificato attendibile.

   d. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo per questo certificato attendibile.

   e. Dall'elenco a discesa **Tipo di profilo** selezionare **Certificato attendibile**.

   f. Individuare il file CA radice trusted con estensione cer ottenuto dalla CA DigiCert nel passaggio precedente e selezionare **OK**.

   g. Solo per i dispositivi Windows 8.1 e Windows 10, selezionare l'archivio di destinazione per il certificato attendibile da:    
      - **Archivio certificati computer - Radice**  
      - **Archivio certificati computer - Intermedio**  
      - **Archivio certificati utente - Intermedio** 

   h. Al termine selezionare **OK**, tornare alla pagina **Crea profilo** e scegliere **Crea**.  
 
Il profilo viene visualizzato nell'elenco dei profili nel riquadro **Configurazione del dispositivo - Profili** con il tipo di profilo **Certificato attendibile**.  Assicurarsi di assegnare questo profilo ai dispositivi che riceveranno certificati. Per assegnare il profilo ai gruppi, vedere [Assegnare i profili di dispositivo](../configuration/device-profile-assign.md).


## <a name="get-the-certificate-profile-oid"></a>Ottenere l'OID del profilo certificato  

L'OID del profilo certificato viene associato a un modello di profilo certificato nella CA DigiCert. Per creare un profilo certificato PKCS in Intune è necessario che il nome del modello di certificato sia l'OID di un profilo certificato associato a un modello di certificato nella CA DigiCert.

1. Accedere al portale di amministrazione della CA DigiCert.
2. Selezionare **Manage Certificate Profiles** (Gestisci profili certificato).
3. Selezionare il profilo certificato che si vuole usare.
4. Copiare l'OID del profilo certificato. Questo ID è simile al seguente:

 
       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
 

> [!NOTE]
> Se si ha bisogno di assistenza per ottenere l'OID del profilo certificato, contattare il [supporto tecnico DigiCert](mailto:enterprise-pkisupport@digicert.com).

## <a name="create-a-pkcs-certificate-profile"></a>Creare un profilo certificato PKCS

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).  

2. Accedere a **Configurazione del dispositivo** >  **Profili** e selezionare **Crea profilo**.

3. Immettere **Nome** e **Descrizione** per il profilo di certificato PKCS.  

4. Nell'elenco a discesa **Piattaforma** selezionare una piattaforma di dispositivo supportata.

5. Nell'elenco a discesa **Tipo di profilo** selezionare **Certificato PKCS**.
 
6. Nel riquadro **Certificato PKCS** configurare i parametri con i valori della tabella seguente. Questi valori sono necessari per emettere certificati PKCS da una CA DigiCert, tramite il Connettore di certificati di Intune. 

   |Parametro del certificato PKCS | Valore | Descrizione |
   | --- | --- | --- |
   | Autorità di certificazione | pki-ws.symauth.com | Questo valore deve essere il nome di dominio completo (FQDN) del servizio di base della CA DigiCert senza barre finali. Se non si è sicuri che il nome di dominio completo del servizio di base della sottoscrizione della CA DigiCert sia corretto, contattare il supporto tecnico DigiCert. <br><br>*Con la modifica da Symantec a DigiCert, questo URL rimane invariato*. <br><br> Se il nome di dominio completo non è corretto, il Connettore di certificati di Intune non rilascerà certificati PKCS dalla CA DigiCert.| 
   | Nome autorità di certificazione | Symantec | Questo valore deve essere la stringa **Symantec**. <br><br> Se questo valore viene modificato, il Connettore di certificati di Intune non rilascerà certificati PKCS dalla CA DigiCert.|
   | Nome modello di certificato | OID del profilo certificato dalla CA DigiCert. Ad esempio: **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| Questo valore deve essere un OID del profilo certificato [ottenuto nella sezione precedente](#get-the-certificate-profile-oid) dal modello di profilo certificato della CA DigiCert. <br><br> Se il Connettore di certificati di Intune non riesce a trovare un modello di certificato associato a questo OID del profilo certificato nella CA DigiCert, non rilascerà certificati PKCS dalla CA DigiCert.|  

   ![Selezioni per CA e modello del certificato](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)  

   > [!NOTE]
   > Il profilo certificato PKCS per le piattaforme Windows non deve necessariamente essere associato a un profilo certificato attendibile, ma questo è un requisito per profili per piattaforme non Windows, come Android.
7. Completare la configurazione del profilo per soddisfare le esigenze aziendali e quindi selezionare **OK** per salvare il profilo. 

8. Selezionare **Assegnazioni** e configurare un gruppo appropriato che riceverà questo profilo. Il gruppo assegnato deve includere almeno un utente o un dispositivo.
 
Dopo aver completato i passaggi precedenti, il Connettore di certificati di Intune rilascerà i certificati PKCS dalla CA DigiCert ai dispositivi gestiti da Intune nel gruppo assegnato. Questi certificati saranno disponibili nell'archivio **Personale** dell'archivio certificati **Utente corrente** del dispositivo gestito da Intune.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>Attributi supportati per il profilo certificato PKCS

|Attributo | Formati supportati da Intune | Formati supportati dalla CA cloud DigiCert | result |
| --- | --- | --- | --- |
| Nome oggetto |Intune supporta il nome soggetto solo nei tre formati seguenti: <br><br> 1. Nome comune <br> 2. Nome comune che include l'indirizzo di posta elettronica <br> 3. Nome comune come indirizzo di posta elettronica <br><br> Ad esempio: <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | La CA DigiCert supporta più attributi.  Per selezionare attributi aggiuntivi, è necessario che siano definiti con valori fissi nel modello di profilo certificato DigiCert.| Per la richiesta di certificato PKCS viene usato il nome comune o l'indirizzo di posta elettronica. <br><br> In presenza di una selezione di attributi non corrispondenti per il profilo certificato di Intune e il modello di profilo certificato DigiCert, la CA DigiCert non rilascia alcun certificato.|
| SAN | Intune supporta solo i valori seguenti per il campo SAN: <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName** (valore codificato) | Anche la CA cloud DigiCert supporta questi parametri. Per selezionare attributi aggiuntivi, è necessario che siano definiti con valori fissi nel modello di profilo certificato DigiCert. <br><br> **AltNameTypeEmail**: se questo tipo non viene trovato nel nome alternativo del soggetto, il Connettore di certificati di Intune usa il valore di **AltNameTypeUpn**.  Se anche il valore di **AltNameTypeUpn** non viene trovato nel nome alternativo del soggetto, il Connettore di certificati di Intune usa il valore del nome soggetto se è in formato di indirizzo di posta elettronica.  Se il valore non viene ancora trovato, il Connettore di certificati di Intune non rilascia i certificati. <br><br> Esempio: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: se questo tipo non viene trovato nel nome alternativo del soggetto, il Connettore di certificati di Intune usa il valore di **AltNameTypeEmail**. Se anche il valore di **AltNameTypeEmail** non viene trovato nel nome alternativo del soggetto, il Connettore di certificati di Intune usa il valore del nome soggetto se è in formato di indirizzo di posta elettronica. Se il valore non viene ancora trovato, il Connettore di certificati di Intune non rilascia i certificati.  <br><br> Esempio: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: se questo tipo non viene trovato nel nome alternativo del soggetto, il Connettore di certificati di Intune non rilascia i certificati. <br><br> Esempio: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  Si noti che il valore di questo campo è supportato solo in formato codificato (valore esadecimale) dalla CA DigiCert. Qualsiasi valore in questo campo viene quindi convertito dal Connettore di certificati di Intune nel formato con codifica Base64 prima di inviare la richiesta di certificato. *Connettore di certificati di Intune non verifica se questo valore è già codificato o meno.* | Nessuno |

## <a name="troubleshooting"></a>Risoluzione dei problemi

I log del servizio del Connettore di certificati di Intune sono disponibili in **%Programmi%\Microsoft Intune\NDESConnectorSvc\Logs\Logs** nel computer NDES Connector. Aprire i log in [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) e cercare i messaggi di eccezione o errore.

| Problema/Messaggio di errore | Procedura per la risoluzione |
| --- | --- |
| Impossibile eseguire l'accesso con l'account di amministratore tenant di Intune nell'interfaccia utente di NDES Connector. | Questa situazione può verificarsi quando il connettore di certificati locale non è abilitato nel portale di amministrazione di Intune. Per risolvere questo problema, eseguire una delle procedure seguenti: <br><br> Dall'interfaccia utente di Silverlight: <br> 1. Accedere al [portale di amministrazione di Intune](https://admin.manage.microsoft.com). <br> 2. Selezionare **Amministrazione**. <br> 3. Selezionare **Gestione dei dispositivi mobili** > **Connettore di certificati**. <br> 4. Selezionare **Configura Connettore di certificati locale**. <br> 5. Selezionare la casella di controllo **Abilita Connettore di certificati**. <br> 6. Selezionare **OK**. <br><br> Dall'interfaccia utente del portale di Azure: <br> 1. Accedere al [portale di Azure](https://portal.azure.com). <br> 2. Passare a Microsoft Intune. <br> 3. Selezionare **Configurazione dispositivo** > **Autorità di certificazione**. <br> 4. e selezionare **Abilita**. <br><br> Dopo aver completato i passaggi precedenti dall'interfaccia utente di Silverlight o dal portale di Azure, provare a eseguire l'accesso con lo stesso account amministratore tenant di Intune nell'interfaccia utente di NDES Connector. |
| Impossibile trovare il certificato di NDES Connector. <br><br> System.ArgumentNullException: Il valore non può essere Null. | Connettore di certificati di Intune mostra questo errore se l'account amministratore tenant di Intune non ha mai eseguito l'accesso all'interfaccia utente di NDES Connector. <br><br> Se l'errore persiste, riavviare il connettore del servizio Intune. <br><br> 1. Aprire **services.msc**. <br> 2. Selezionare **Servizio Intune Connector**. <br> 3. Fare clic con il pulsante destro del mouse e scegliere **Riavvia**.|
| NDES Connector - IssuePfx -Eccezione generica: <br> System.NullReferenceException: Riferimento oggetto non impostato su un'istanza di un oggetto. | Questo errore è temporaneo. Riavviare il connettore del servizio Intune. <br><br> 1. Aprire **services.msc**. <br> 2. Selezionare **Servizio Intune Connector**. <br> 3. Fare clic con il pulsante destro del mouse e scegliere **Riavvia**. |
| Provider DigiCert: impossibile ottenere il criterio DigiCert. <br><br>"Timeout dell'operazione." | Il Connettore di certificati di Intune ha ricevuto l'errore di timeout dell'operazione durante la comunicazione con la CA DigiCert. Se l'errore persiste, aumentare il valore di timeout della connessione e riprovare. <br><br> Per aumentare il timeout della connessione: <br> 1. Accedere al computer NDES Connector. <br>2. Aprire il file **%Programmi%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** nel Blocco note. <br> 3. Aumentare il valore di timeout per il parametro seguente: <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Riavviare il servizio Connettore di certificati di Intune. <br><br> Se il problema persiste, contattare il supporto tecnico DigiCert. |
| Provider DigiCert: impossibile ottenere il certificato client. | Il Connettore di certificati di Intune non è riuscito a recuperare il certificato di autorizzazione delle risorse dall'archivio certificati Computer locale-Personale. Per risolvere il problema, installare il certificato di autorizzazione delle risorse nell'archivio certificati Computer locale-Personale insieme alla relativa chiave privata. <br><br> Il certificato di autorizzazione delle risorse deve essere ottenuto dalla CA DigiCert. Per altri dettagli, contattare il supporto tecnico DigiCert. | 
| Provider DigiCert: impossibile ottenere il criterio DigiCert. <br><br>"Richiesta terminata: Impossibile creare un canale sicuro SSL/TLS". | Questo errore si verifica negli scenari seguenti: <br><br> 1. Il servizio Connettore di certificati di Intune non ha le autorizzazioni sufficienti per leggere il certificato di autorizzazione delle risorse insieme alla relativa chiave privata dall'archivio certificati Computer locale-Personale. Per risolvere questo problema, controllare l'account del contesto di esecuzione del servizio del connettore in services.msc. Il servizio del connettore deve essere eseguito nel contesto NT AUTHORITY\SYSTEM. <br><br> 2. Il profilo certificato PKCS nel portale di amministrazione di Intune potrebbe essere configurato con un nome di dominio completo del servizio di base della CA DigiCert non valido. Il nome di dominio completo è simile a **pki-ws.symauth.com**. Per risolvere il problema, rivolgersi al supporto tecnico DigiCert per verificare se l'URL è corretto per la sottoscrizione. <br><br> 3. Il Connettore di certificati di Intune non riesce a eseguire l'autenticazione con la CA DigiCert usando il certificato di autorizzazione delle risorse perché non riesce a recuperare la chiave privata. Per risolvere il problema, installare il certificato di autorizzazione delle risorse nell'archivio certificati Computer locale-Personale insieme alla relativa chiave privata. <br><br> Se il problema persiste, contattare il supporto tecnico DigiCert. |
| Provider DigiCert: impossibile ottenere il criterio DigiCert. <br><br>"Elemento richiesta incomprensibile." | Il Connettore di certificati di Intune non è riuscito a ottenere il modello di profilo certificato di DigiCert, perché l'OID del profilo client non corrisponde al profilo del certificato di Intune. In un altro caso, il Connettore di certificati di Intune non riesce a trovare il modello di profilo certificato associato all'OID di profilo client specificato nella CA DigiCert. <br><br> Per risolvere questo problema, ottenere l'OID di profilo client corretto dal modello di certificato DigiCert nella CA DigiCert. Aggiornare quindi il profilo del certificato PKCS nel portale di amministrazione di Intune. <br><br> Ottenere l'OID del profilo certificato dalla CA DigiCert: <br> 1. Accedere al portale di amministrazione della CA DigiCert. <br> 2. Selezionare **Manage Certificate Profiles** (Gestisci profili certificato). <br> 3. Selezionare il profilo certificato che si vuole usare. <br> 4. Ottenere l'OID del profilo certificato. Questo ID è simile al seguente: <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> Aggiornare il profilo certificato PKCS con l'OID del profilo certificato corretto: <br>1. Accedere al portale di amministrazione di Intune. <br> 2. Passare al profilo certificato PKCS e selezionare **Modifica**. <br> 3. Aggiornare l'OID del profilo certificato nel campo del nome modello di certificato. <br> 4. Salvare il profilo certificato PKCS. |
| Provider DigiCert: verifica dei criteri non riuscita. <br><br> L'attributo non rientra nell'elenco degli attributi per i modelli di certificato supportati da DigiCert. | La CA DigiCert visualizza questo messaggio quando è presente una discrepanza tra il modello di profilo certificato DigiCert e il profilo certificato di Intune. Questo problema si è verificato probabilmente a causa di attributi non corrispondenti in **SubjectName** o **SubjectAltName**. <br><br> Per risolvere il problema, selezionare attributi supportati da Intune per **SubjectName** e **SubjectAltName** nel modello di profilo certificato di DigiCert. Per altre informazioni, vedere gli attributi supportati da Intune nella sezione relativa ai **parametri del certificato**. |
| Alcuni dispositivi utente non ricevono i certificati PKCS dalla CA DigiCert. | Questo problema si verifica quando il nome dell'entità utente contiene caratteri speciali come il carattere di sottolineatura, ad esempio: `global_admin@intune.onmicrosoft.com`. <br><br> La CA DigiCert non supporta i caratteri speciali in **mail_firstname** e **mail_lastname**. <br><br> La procedura seguente consente di risolvere il problema: <br><br> 1. Accedere al portale di amministrazione della CA DigiCert. <br> 2. Fare clic su **Manage Certificate Profiles** (Gestisci profili certificato). <br> 3. Selezionare il profilo di certificato usato per Intune. <br> 4. Selezionare il collegamento **Customize options** (Opzioni di personalizzazione). <br> 5. Selezionare il pulsante **Advanced options** (Opzioni avanzate). <br> 6. In **Certificate fields – Subject DN** (Campi certificato - DN soggetto) aggiungere il campo **Common Name (CN) (Nome comune - CN)** ed eliminare il campo **Common Name (CN)** (Nome comune - CN) esistente. Le operazioni di aggiunta ed eliminazione devono essere eseguite insieme. <br> 7. Selezionare **Salva**. <br><br> Con la modifica precedente, il profilo certificato DigiCert richiede **"CN=<upn>"** anziché **mail_firstname** e **mail_lastname**. |
| L'utente ha eliminato manualmente un certificato già distribuito dal dispositivo. | Intune ridistribuisce lo stesso certificato durante l'archiviazione o l'applicazione dei criteri successiva. In questo caso NDES Connector non riceve una richiesta di certificato PKCS. |

## <a name="next-steps"></a>Passaggi successivi

Usare le informazioni illustrate in questo articolo oltre a quelle incluse in [Informazioni sui profili di dispositivo in Microsoft Intune](../configuration/device-profiles.md) per gestire i dispositivi dell'organizzazione e i relativi certificati.

