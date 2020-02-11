---
title: Risolvere i problemi relativi al modulo criteri del Connettore di certificati di Microsoft Intune | Microsoft Docs
description: Risolvere i problemi di funzionamento del modulo criteri del servizio Registrazione dispositivi di rete quando il modulo elabora una richiesta di certificato mentre si usano i profili certificato SCEP per distribuire certificati con Intune.
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
ms.openlocfilehash: be53f6102226b004cab2bd953357e8c360a00f67
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76915837"
---
# <a name="troubleshoot-the-ndes-policy-module-in-microsoft-intune"></a>Risolvere i problemi del modulo criteri NDES in Microsoft Intune

Le informazioni contenute in questo articolo consentono di convalidare il funzionamento del modulo criteri del servizio Registrazione dispositivi di rete (NDES) che viene installato con il Connettore di certificati di Microsoft Intune. Quando il servizio Registrazione dispositivi di rete riceve una richiesta per un certificato inoltra la richiesta al modulo criteri, che convalida la richiesta per il dispositivo. Dopo la convalida il servizio Registrazione dispositivi di rete contatta l'autorità di certificazione (CA) per richiedere il certificato per conto del dispositivo.

Questo articolo si applica sia al passaggio 3 che al passaggio 4 del [flusso di lavoro di comunicazione SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="ndes-communication-to-the-policy-module"></a>Comunicazione tra il servizio Registrazione dispositivi di rete e il modulo criteri

Dopo aver ricevuto la richiesta di certificato da un dispositivo, il servizio Registrazione dispositivi di rete convalida la richiesta con Intune tramite il modulo criteri installato con il Connettore di certificati di Microsoft Intune. Queste voci fanno riferimento al *punto di registrazione certificati*.

**Voci di log che indicano l'esito positivo**:

Per confermare che la richiesta di convalida è stata inviata al modulo, cercare una voce simile agli esempi seguenti nei log del server del servizio Registrazione dispositivi di rete:

- **Log di IIS**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 - 
  fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 201 0 0 341 875
  ```

- **Log NDESPlugin**:

  ```
  Calling VerifyRequest ...  
  Sending request to certificate registration point.
  ```

  L'esempio seguente visualizza una convalida corretta della richiesta di verifica dei dispositivi e conferma che il servizio Registrazione dispositivi di rete ora può contattare l’autorità di certificazione:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`


**Quando non sono presenti indicatori di operazione riuscita**:

Se non si trovano queste voci, vedere le linee guida per la risoluzione dei problemi delle [comunicazioni dal dispositivo al server NDES](troubleshoot-scep-certificate-device-to-ndes.md#troubleshoot-common-errors).

Se le informazioni contenute in questo articolo non consentono di risolvere il problema, di seguito sono riportate voci aggiuntive che possono indicare problemi.

### <a name="ndespluginlog-contains-an-error-12175"></a>NDESPlugin.log contiene un errore 12175

Se il log contiene un errore 12175 simile al seguente, potrebbe essersi verificato un problema con il certificato SSL:

```
WINHTTP_CALLBACK_STATUS_FLAG_CERT_CN_INVALID
Failed to send http request /CertificateRegistrationSvc/Certificate/VerifyRequest. Error 12175
```

I browser moderni e i browser nei dispositivi mobili ignorano la voce *Nome comune* in un certificato SSL se sono presenti voci *Subject Alternative Name* (Nome alternativo del soggetto).

**Risoluzione**:  Rilasciare il certificato SSL del server Web con gli attributi seguenti per *Nome comune* e *Nome alternativo del soggetto*, quindi associarlo alla porta 443 in IIS:

  - **Nome soggetto**  
    CN (Nome comune) = nome del server esterno
  - **Nome alternativo del soggetto**  
     Nome = nome del server esterno  
     Nome DNS = nome del server interno

### <a name="ndespluginlog-contains-an-error-403--forbidden-access-is-denied"></a>NDESPlugin.log contiene un errore 403 - Non consentito: Accesso negato

Quando i log seguenti contengono un errore 403 simile a quello visualizzato di seguito, il certificato client potrebbe non essere attendibile o non essere valido:

**NDESPlugin.log**:

```
Sending request to certificate registration point.
Verify challenge returns <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> <html xmlns="http://www.w3.org/1999/xhtml"> <head><meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1"/>
<title>403 - Forbidden: Access is denied.</title>
```

**Log IIS**:

```
POST /CertificateRegistrationSvc/Certificate/VerifyRequest - 443 -<IP_address>
NDES_Plugin - 403 16 2148204809 453  
```

Questo problema si verifica se sono presenti certificati dell’autorità di certificazione intermedia nell'archivio certificati Autorità di certificazione radice attendibili del server NDES.

Se un certificato ha gli stessi valori *Rilasciato a* e *Rilasciato da* è un certificato radice. In caso contrario è un certificato intermedio.

**Risoluzione**: Per risolvere il problema, identificare e rimuovere i certificati dell’autorità di certificazione intermedia dall'archivio certificati Autorità di certificazione radice attendibili.

### <a name="ndespluginlog-indicates-the-challenge-returns-false"></a>NDESPlugin.log indica che la richiesta di verifica restituisce false

Quando il risultato della richiesta di verifica è **false** controllare il file *CertificateRegistrationPoint.svclog* per trovare eventuali errori. Ad esempio, è possibile che venga visualizzato un errore di tipo "Impossibile recuperare il certificato di firma" simile alla voce seguente:

```
Signing certificate could not be retrieved. System.Security.Cryptography.CryptographicException: m_safeCertContext is an invalid handle. at System.Security.Cryptography.X509Certificates.X509Certificate.ThrowIfContextInvalid() at System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString() at Microsoft.ConfigurationManager.CertRegPoint.CRPCertificate.RetrieveSigningCert(String certThumbprint
```

**Risoluzione**: Nel server in cui è installato il connettore aprire l'editor del Registro di sistema, trovare la chiave del Registro di sistema `HKLM\SOFTWARE\Microsoft\MicrosoftIntune\NDESConnector` e quindi controllare se è presente il valore SigningCertificate.

Se questo valore non esiste, riavviare il servizio Intune Connector in services.msc, quindi verificare se il valore viene visualizzato nel Registro di sistema. Se il valore è ancora mancante, un motivo frequente è rappresentato da problemi di connettività di rete tra il server NDES e il servizio Intune.

## <a name="ndes-passes-the-request-to-issue-the-certificate"></a>NDES passa la richiesta di emissione del certificato

Dopo una convalida corretta da parte del punto di registrazione certificati (il modulo criteri), NDES passa la richiesta di certificato all’autorità di certificazione per conto del dispositivo.

**Voci di log che indicano l'esito positivo**:

- **Log NDESPlugin**:

  ```
  Verify challenge returns true
  Exiting VerifyRequest with 0x0
  ```

- **Log di IIS**:

  ```
  fe80::f53d:89b8:c3e8:5fec%13 GET /certsrv/mscep/mscep.dll/pkiclient.exe ... 80 - 
  fe80::f53d:89b8:c3e8:5fec%13 Mozilla/4.0+(compatible;+Win32;+NDES+client) - 200 0 0 2713 1296
  ```

- **CertificateRegistrationPoint.svclog**:

  `Validation Phase 1 finished with status True.`  
  `Validation Phase 3 finished with status True.`  
  `VerifyRequest Finished with status True`

**Quando non sono presenti indicatori di operazione riuscita**:

Se non vengono visualizzate voci che indicano l'esito positivo, seguire questa procedura:

1. Trovare i problemi registrati in *CertificateRegistrationPoint.svclog* quando il punto di registrazione certificati esamina la richiesta di verifica. Cercare le voci incluse tra le righe seguenti:

   - VerifyRequest Started.
   - VerifyRequest Finished with status False

2. Aprire MMC Autorità di certificazione nell’autorità di certificazione e selezionare **Richieste non riuscite** per cercare gli errori che contribuiscono a identificare un problema. L'immagine seguente è un esempio:

   ![Esempio di richiesta non riuscita](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/failed-requests.png)

3. Esaminare il registro eventi dell'applicazione nell’autorità di certificazione per trovare eventuali errori. In genere si rilevano errori corrispondenti a quanto visualizzato in **Richieste non riuscite** nel passaggio precedente. L'immagine seguente è un esempio:

   ![Esaminare il registro applicazioni](../protect/media/troubleshoot-scep-certificate-ndes-policy-module/application-log-errors.png)

## <a name="next-steps"></a>Passaggi successivi

Se il modulo criteri del servizio Registrazione dispositivi di rete convalida la richiesta e questa viene trasmessa all'autorità di certificazione, il passaggio successivo è l’esame della [consegna del certificato al dispositivo](troubleshoot-scep-certificate-delivery.md).
