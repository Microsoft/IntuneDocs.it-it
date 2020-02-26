---
title: Risolvere i problemi di comunicazione tra dispositivo gestito e NDES in Microsoft Intune | Microsoft Docs
description: Risolvere i problemi di comunicazione tra dispositivo gestito e server NDES quando vengono usati profili di certificato SCEP per distribuire i certificati con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/30/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7945f1df3ddf1a6ff2c42a537e1071d1b5acff24
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514269"
---
# <a name="troubleshoot-device-to-ndes-server-communication-for-scep-certificate-profiles-in-microsoft-intune"></a>Risolvere i problemi di comunicazione tra dispositivo e server NDES per i profili di certificato SCEP in Microsoft Intune

Usare le informazioni seguenti per determinare se un dispositivo che ha ricevuto ed elaborato un profilo di certificato Simple Certificate Enrollment Protocol (SCEP) di Intune è in grado di contattare il servizio Registrazione dispositivi di rete (NDES) per presentare una richiesta di verifica. Nel dispositivo viene generata una chiave privata e la richiesta di firma del certificato (CSR) e la richiesta di verifica vengono passate dal dispositivo al server NDES. Per contattare il server NDES, il dispositivo usa l'URI del profilo di certificato SCEP.

Questo articolo fa riferimento al passaggio 2 della [Panoramica del flusso di comunicazione SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="review-iis-logs-for-a-connection-from-the-device"></a>Esaminare i log di IIS per una connessione dal dispositivo

I log di IIS includono lo stesso tipo di voci per tutte le piattaforme.


1. Nel server NDES aprire il file di log di IIS più recente disponibile nella cartella seguente: *%SystemDrive%\inetpub\logs\logfiles\w3svc1*

2. Cercare nel log voci simili agli esempi seguenti. Entrambi gli esempi contengono uno stato **200**, visualizzato nella parte finale:

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACaps&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 186 0.`

   And

   `fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe operation=GetCACert&message=default 80 - fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 3567 0`

3. Quando il dispositivo contatta IIS, viene registrata una richiesta HTTP GET per mscep.dll.

   Esaminare il codice di stato nella parte finale della richiesta:
   - **Codice di stato 200**: questo stato indica che la connessione al server NDES è riuscita.
   - **Codice di stato 500**: il gruppo IIS_IURS potrebbe non includere le autorizzazioni corrette. Vedere [Codice di stato 500](#status-code-500) più avanti in questo articolo.
   - Se il codice di stato non è 200 o 500:

     - Vedere [Testare l'URL del server SCEP](#test-the-scep-server-url) più avanti in questo articolo per convalidare la configurazione.

     - Per informazioni sui codici di errore meno comuni, vedere [Codice di stato HTTP in IIS 7 e versioni successive](https://support.microsoft.com/help/943891).

   Se la richiesta di connessione non viene registrata, il contatto del dispositivo potrebbe essere bloccato sulla rete tra il dispositivo e il server NDES.

## <a name="review-device-logs-for-connections-to-ndes"></a>Esaminare i log del dispositivo cercando le connessioni a NDES

### <a name="android-devices"></a>Dispositivi Android

Esaminare il [log OMADM dei dispositivi](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Cercare voci simili alle seguenti, che vengono registrate quando il dispositivo si connette a NDES:

```
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  There are 1 requests
2018-02-27T05:16:08.2500000  VERB  Event  com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager  18327    10  Trying to enroll certificate request: ModelName=AC_51bad41f-3854-4eb5-a2f2-0f7a94034ee8%2FLogicalName_39907e78_e61b_4730_b9fa_d44a53e4111c;Hash=1677525787
2018-02-27T05:16:09.5530000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:14.6440000  VERB  Event  org.jscep.transport.UrlConnectionGetTransport  18327    10  Received '200 OK' when sending GetCACaps(ca) to https://<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.8220000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10 Encoding message: org.jscep.message.PkcsReq@2b06f45f[messageData=org.<server>.pkcs.PKCS10CertificationRequest@699b3cd,messageType=PKCS_REQ,senderNonce=Nonce [D447AE9955E624A56A09D64E2B3AE76E],transId=251E592A777C82996C7CF96F3AAADCF996FC31FF]
2018-02-27T05:16:21.8790000  VERB  Event  org.jscep.message.PkiMessageEncoder  18327     10  Signing pkiMessage using key belonging to [dn=CN=<uesrname>; serial=1]
2018-02-27T05:16:21.9580000  VERB  Event  org.jscep.transaction.EnrollmentTransaction  18327     10  Sending org.<server>.cms.CMSSignedData@ad57775
```

Le voci chiave includono le stringhe di testo di esempio seguenti:

- There are 1 requests
- Received '200 OK' when sending GetCACaps(ca) to https://\<server>.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
- Signing pkiMessage using key belonging to [dn=CN=\<username>; serial=1]


La connessione viene registrata anche da IIS nella cartella %SystemDrive%\inetpub\logs\LogFiles\W3SVC1\ del server NDES. Di seguito è riportato un esempio:

```
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACert&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 3909 0
fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll operation=GetCACaps&message=ca 443 - 
fe80::f53d:89b8:c3e8:5fec%13 Dalvik/2.1.0+(Linux;+U;+Android+5.0;+P01M+Build/LRX21V) - 200 0 0 421 
```

### <a name="iosipados-devices"></a>Dispositivi iOS/iPadOS

Esaminare il [log di debug dei dispositivi](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices). Cercare voci simili alle seguenti, che vengono registrate quando il dispositivo si connette a NDES:

```
debug    18:30:53.691033 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\ 
debug    18:30:54.640644 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
default    18:30:55.483977 -0500    profiled    Attempting to retrieve issued certificate...\ 
debug    18:30:55.487798 -0500    profiled    Sending CSR via GET.\  
debug    18:30:55.487908 -0500    profiled    Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQGZwmPoqFMbX3g85CJT8khPaqFW05yGDTPSX9YpuEE0Bmtht9EwOpOZe6O7sd77IhfFZVmHmwy5mIYN7K6mpx/4Cb5zcNmY3wmTBlKEkDQpZDRf5PpVQ3bmQ3we9XxeK1S4UsAXHVdYGD+bg/bCafMIAGCSqGSIb3DQEHATAUBggqhkiG9w0DBwQI5D5J2lwZS5OggASCF6jSG9iZA/EJ93fEvZYLV0v7GVo3JAsR11O7DlmkIqvkAg5iC6DQvXO1j88T/MS3wV+rqUbEhktr8Xyf4sAAPI4M6HMfVENCJTStJw1PzaGwUJHEasq39793nw4k268UV5XHXvzZoF3Os2OxUHSfHECOj
```

Le voci chiave includono le stringhe di testo di esempio seguenti:

- operation=GetCACert
- Attempting to retrieve issued certificate
- Sending CSR via GET
- operation=PKIOperation

### <a name="windows-devices"></a>Dispositivi Windows

In un dispositivo Windows che esegue una connessione a NDES, è possibile aprire il Visualizzatore eventi di Windows e cercare le indicazioni di una connessione riuscita. Le connessioni vengono registrate come ID evento **36** nel log *DeviceManagement-Enterprise-Diagnostics-Provide* > **Admin** dei dispositivi.

Per aprire il log:

1. Nel dispositivo eseguire **eventvwr.msc** per aprire il Visualizzatore eventi di Windows.

2. Espandere **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Admin**.

3. Cercare l'evento **36**, simile all'esempio seguente, con la riga chiave **SCEP: Creazione della richiesta di certificato completata**:

   ```
   Event ID:      36
   Task Category: None
   Level:         Information
   Keywords:
   User:          <UserSid>
   Computer:      <Computer Name>
   Description:
   SCEP: Certificate request generated successfully. Enhanced Key Usage: (1.3.6.1.5.5.7.3.2), NDES URL: (https://<server>/certsrv/mscep/mscep.dll/pkiclient.exe), Container Name: (), KSP Setting: (0x2), Store Location: (0x1).
   ```

## <a name="troubleshoot-common-errors"></a>Risolvere gli errori comuni

Le sezioni seguenti consentono di risolvere i problemi di connessione comuni da tutte le piattaforme del dispositivo a NDES.

### <a name="status-code-500"></a>Codice di stato 500

Le connessioni simili all'esempio seguente, con codice di stato 500, indicano che il diritto utente *Rappresenta un client dopo l'autenticazione* non è assegnato al gruppo IIS_IURS nel server NDES. Il valore di stato **500** viene visualizzato alla fine:

```
2017-08-08 20:22:16 IP_address GET /certsrv/mscep/mscep.dll operation=GetCACert&message=SCEP%20Authority 443 - 10.5.14.22 profiled/1.0+CFNetwork/811.5.4+Darwin/16.6.0 - 500 0 1346 31
```

**Per risolvere il problema**:

1. Nel server NDES eseguire **secpol.msc** per aprire Criteri di sicurezza locali.

2. Espandere **Criteri locali** e fare clic su **Assegnazione diritti utente**.

3. Fare doppio clic su **Rappresenta un client dopo l'autenticazione** nel riquadro di destra.

4. Fare clic su **Aggiungi gruppo o utente**, immettere **IIS_IURS** nella casella **Immettere i nomi degli oggetti da selezionare** e fare clic su **OK**.

5. Fare clic su **OK**.

6. Riavviare il computer, quindi riprovare a connettersi dal dispositivo.

### <a name="test-the-scep-server-url"></a>Testare l'URL del server SCEP

Usare la procedura seguente per testare l'URL specificato nel profilo di certificato SCEP.

1. In Intune modificare il profilo di certificato SCEP e copiare l'URL del server. L'URL dovrebbe essere simile a *https://contoso.com/certsrv/mscep/msecp.dll* .

2. Aprire un Web browser e passare all'URL del server SCEP. Il risultato dovrebbe essere: **Errore HTTP 403.0 - Accesso negato**. Questo risultato indica che l'URL funziona correttamente.

   Se non viene visualizzato questo errore, selezionare il collegamento corrispondente all'errore per visualizzare le indicazioni specifiche per il problema:
   - [Viene visualizzato un messaggio generale relativo al servizio Registrazione dispositivi di rete (NDES)](#general-ndes-message)
   - [Viene visualizzato "Errore: HTTP 503, servizio non disponibile"](#http-error-503)
   - [Viene visualizzato l'errore "GatewayTimeout"](#gatewaytimeout)
   - [Viene visualizzato "HTTP 414 URI della richiesta troppo lungo"](#http-414-request-uri-too-long)
   - [Viene visualizzato "Impossibile visualizzare questa pagina"](#this-page-cant-be-displayed)
   - [Viene visualizzato "500 - Errore interno del server"](#internal-server-error)

#### <a name="general-ndes-message"></a>Messaggio NDES generale

Quando si passa all'URL del server SCEP, viene visualizzato il messaggio del servizio Registrazione dispositivi di rete (NDES) seguente:

![URL server SCEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/ndes-server-url-message.png)

- **Causa**: questo problema rappresenta in genere un problema di installazione del connettore Microsoft Intune.

  Mscep.dll è un'estensione ISAPI che intercetta la richiesta in ingresso e visualizza l'errore HTTP 403 se l'installazione non è corretta.
  
  **Risoluzione**: esaminare il file *SetupMsi.log* per determinare se il connettore Microsoft Intune è stato installato correttamente. Nell'esempio seguente *L'installazione è stata completata* e *Installazione riuscita o stato di errore: 0* indicano un'installazione eseguita correttamente:

  ```
  MSI (c) (28:54) [16:13:11:905]: Product: Microsoft Intune Connector -- Installation completed successfully.
  MSI (c) (28:54) [16:13:11:999]: Windows Installer installed the product. Product Name: Microsoft Intune Connector. Product Version: 6.1711.4.0. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.
  ```

  Se l'installazione non riesce, rimuovere il connettore Microsoft Intune e quindi reinstallarlo.

#### <a name="http-error-503"></a>Errore HTTP 503

Quando si passa all'URL del server SCEP, viene visualizzato l'errore seguente:

![Errore HTTP 503. Il servizio non è disponibile](../protect/media/troubleshoot-scep-certificate-device-to-ndes/service-unavailable.png)

Questo problema in genere è dovuto al fatto che il pool di applicazioni **SCEP** in IIS non è stato avviato. Nel server NDES aprire **Gestione IIS** e passare a **Pool di applicazioni**. Individuare il pool di applicazioni **SCEP** e verificare che sia stato avviato.

Se il pool di applicazioni SCEP non è stato avviato, controllare il registro eventi dell'applicazione nel server:

1. Nel dispositivo eseguire **eventvwr.msc** per aprire **Visualizzatore eventi** e passare a **Registri di Windows** > **Applicazione**.

2. Cercare un evento simile all'esempio seguente in cui il pool di applicazioni si arresta in modo anomalo quando viene ricevuta una richiesta:

   ```
   Log Name:      Application
   Source:        Application Error
   Event ID:      1000
   Task Category: Application Crashing Events
   Level:         Error
   Keywords:      Classic
   Description: Faulting application name: w3wp.exe, version: 8.5.9600.16384, time stamp: 0x5215df96
   Faulting module name: ntdll.dll, version: 6.3.9600.18821, time stamp: 0x59ba86db
   Exception code: 0xc0000005
   ```

**Cause comuni di un arresto anomalo del pool di applicazioni**:

- **Causa 1**: sono presenti certificati della CA intermedi (non autofirmati) nell'archivio certificati Autorità di certificazione radice disponibile nell'elenco locale del server NDES.

  **Risoluzione**: rimuovere i certificati intermedi dall'archivio certificati Autorità di certificazione radice disponibile nell'elenco locale e quindi riavviare il server NDES.
  
  Per identificare tutti i certificati intermedi nell'archivio certificati Autorità di certificazione radice disponibile nell'elenco locale, eseguire il cmdlet di PowerShell seguente: `Get-Childitem -Path cert:\LocalMachine\root -Recurse | Where-Object {$_.Issuer -ne $_.Subject}`

  Un certificato che ha gli stessi valori **Rilasciato a** e **Rilasciato da** è un certificato radice. In caso contrario è un certificato intermedio.

  Dopo aver rimosso i certificati e aver riavviato il server, eseguire di nuovo il cmdlet di PowerShell per verificare che non siano presenti certificati intermedi. Se sono presenti certificati intermedi, verificare se Criteri di gruppo effettua il push di certificati intermedi nel server NDES. In tal caso, escludere il server NDES da Criteri di gruppo e rimuovere di nuovo i certificati intermedi.

- **Causa 2**: gli URL nell'elenco di revoche di certificati (CRL) sono bloccati o irraggiungibili per i certificati usati dal connettore di certificati di Intune.

  **Risoluzione**: abilitare la registrazione aggiuntiva per raccogliere altre informazioni:
  1. Aprire il Visualizzatore eventi, fare clic su **Visualizza**, assicurarsi che sia selezionata l'opzione **Visualizza registri analitici e di debug**.
  2. Passare a **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **CAPI2** > **Operativo**, fare clic con il pulsante destro del mouse su **Operativo**, quindi fare clic su **Attiva registro**.
  3. Dopo aver abilitato la registrazione CAPI2, riprodurre il problema ed esaminare il registro eventi per risolvere il problema.

- **Causa 3**: l'autorizzazione IIS per **CertificateRegistrationSvc** ha l'**Autenticazione di Windows** abilitata.

  **Risoluzione**: abilitare **Autenticazione anonima** e disabilitare **Autenticazione di Windows**, quindi riavviare il server NDES.

  ![Autorizzazioni IIS](../protect/media/troubleshoot-scep-certificate-device-to-ndes/iis-permissions.png)

#### <a name="gatewaytimeout"></a>GatewayTimeout

Quando si passa all'URL del server SCEP, viene visualizzato l'errore seguente:

![Errore Gatewaytimeout](../protect/media/troubleshoot-scep-certificate-device-to-ndes/gateway-timeout.png)

- **Causa**: il servizio **Microsoft AAD Application Proxy Connector** non è stato avviato.

  **Risoluzione**:  eseguire **services.msc** e quindi verificare che il servizio **Microsoft AAD Application Proxy Connector** sia in esecuzione e che **Tipo di avvio** sia impostato su **Automatico**.

#### <a name="http-414-request-uri-too-long"></a>HTTP 414 URI della richiesta troppo lungo

Quando si passa all'URL del server SCEP, viene visualizzato l'errore seguente: `HTTP 414 Request-URI Too Long`

- **Causa**: il filtro delle richieste IIS non è configurato per il supporto degli URL lunghi (query) ricevuti dal servizio NDES. Questo supporto viene configurato quando si [configura il servizio NDES](certificates-scep-configure.md#configure-the-ndes-service) per l'uso con l'infrastruttura per SCEP.

- **Risoluzione**: configurare il supporto degli URL lunghi.

  1. Nel server NDES server aprire Gestione IIS, selezionare **Sito Web predefinito** > **Filtro richieste** > **Modifica impostazioni funzionalità** per aprire la pagina **Modifica impostazioni di filtro richieste**.

  2. Configurare le seguenti impostazioni:
     - **Lunghezza massima URL (byte)** = 65534
     - **Lunghezza massima stringa di query in (byte)** = 65534

  3. Selezionare **OK** per salvare la configurazione e chiudere Gestione IIS.

  4. Convalidare questa configurazione individuando la chiave del Registro di sistema seguente per verificare che abbia i valori indicati:

     HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters

     I valori seguenti sono impostati come voci DWORD:
     - Nome: **MaxFieldLength**, con un valore decimale di **65534**
     - Nome: **MaxRequestBytes**, con un valore decimale di **65534**

  5. Riavviare il server NDES.

#### <a name="this-page-cant-be-displayed"></a>Impossibile visualizzare questa pagina

È stato configurato Azure AD Application Proxy. Quando si passa all'URL del server SCEP, viene visualizzato l'errore seguente:

`This page can't be displayed`

- **Causa**: questo problema si verifica quando l'URL esterno SCEP non è corretto nella configurazione di Application Proxy. Un esempio di questo URL è https://contoso.com/certsrv/mscep/mscep.dll.

  **Risoluzione**: usare il dominio predefinito di *yourtenant.msappproxy.net* per l'URL esterno SCEP nella configurazione di Application Proxy.

#### <a name="internal-server-error"></a>500 - Errore interno del server

Quando si passa all'URL del server SCEP, viene visualizzato l'errore seguente:

![500 - Errore interno del server](../protect/media/troubleshoot-scep-certificate-device-to-ndes/500-internal-server-error.png)

- **Causa 1**: l'account del servizio NDES è bloccato o la password è scaduta.

  **Risoluzione**: sbloccare l'account o reimpostare la password.

- **Causa 2**: i certificati MSCEP-RA sono scaduti.

  **Risoluzione**: se i certificati MSCEP-RA sono scaduti, reinstallare il ruolo NDES o richiedere nuovi certificati di Crittografia CEP e Agente di registrazione di Exchange (richiesta offline).

  Per richiedere nuovi certificati, seguire questa procedura:

  1. Nella CA (Certificate Authority) o nella CA emittente, aprire la MMC Modelli di certificato. Verificare che l'utente connesso e il server NDES abbiano le autorizzazioni **Lettura** e **Registrazione** per i modelli di certificato di Crittografia CEP e Agente di registrazione di Exchange (richiesta offline).

  2. Controllare i certificati scaduti nel server NDES, copiare le informazioni **Oggetto** del certificato.

  3. Aprire la MMC Certificati per l'**Account del computer**.

  4. Espandere **Personale**, fare clic con il pulsante destro del mouse su **Certificati**, quindi selezionare **Tutte le attività** > **Richiedi nuovo certificato**.

  5. Nella pagina **Richiedi certificato** selezionare **Crittografia CEP**, quindi fare clic su **Sono necessarie ulteriori informazioni per registrare il certificato. Per configurare le impostazioni, fare clic qui**.

     ![Selezionare la crittografia CEP](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-scep-encryption.png)

  6. In **Proprietà certificato** fare clic sulla scheda **Soggetto**, specificare il **Nome soggetto** in base alle informazioni raccolte nel passaggio 2, fare clic su **Aggiungi**, quindi su **OK**.

  7. Completare la registrazione certificato.

  8. Aprire la MMC Certificati per l'**Account dell'utente**.

     Quando si esegue la registrazione per il certificato di Agente di registrazione di Exchange (richiesta offline), è necessario eseguirla nel contesto utente poiché il **Subject Type** del modello di certificato è impostato su **Utente**.

  9. Espandere **Personale**, fare clic con il pulsante destro del mouse su **Certificati**, quindi selezionare **Tutte le attività** > **Richiedi nuovo certificato**.

  10. Nella pagina **Richiedi certificato** selezionare **Agente di registrazione di Exchange (richiesta offline)** , quindi fare clic su **Sono necessarie ulteriori informazioni per registrare il certificato. Per configurare le impostazioni, fare clic qui**.

      ![Selezionare l'agente di registrazione di Exchange](../protect/media/troubleshoot-scep-certificate-device-to-ndes/select-exchange-enrollment-agent.png)

  11. In **Proprietà certificato** fare clic sulla scheda **Soggetto**, specificare il **Nome soggetto** in base alle informazioni raccolte nel passaggio 2, fare clic su **Aggiungi**.

      ![Proprietà del certificato](../protect/media/troubleshoot-scep-certificate-device-to-ndes/certificate-properties.png)

      Selezionare la scheda **Chiave privata**, selezionare **Consenti esportazione chiave privata**, quindi fare clic su **OK**.

      ![Chiave privata](../protect/media/troubleshoot-scep-certificate-device-to-ndes/private-key.png)

  12. Completare la registrazione certificato.

  13. Esportare il certificato di Agente di registrazione di Exchange (richiesta offline) dall'archivio certificati dell'utente corrente. Nell'Esportazione guidata certificati selezionare **Sì, esporta la chiave privata**.

  14. Importare il certificato nell'archivio certificati del computer locale.

  15. Nella MMC Certificati eseguire l'azione seguente per ogni nuovo certificato:

      Fare clic con il pulsante destro del mouse sul certificato, fare clic su **Tutte le attività** > **Gestisci chiavi private**, aggiungere l'autorizzazione **Lettura** all'account del servizio NDES.

  16. Eseguire il comando **iisreset** per riavviare IIS.

## <a name="next-steps"></a>Passaggi successivi

Se il dispositivo si connette correttamente al server NDES per presentare la richiesta di certificato, il passaggio successivo è quello di rivedere il [modulo criteri dei connettori di certificato di Intune](troubleshoot-scep-certificate-ndes-policy-module.md).
