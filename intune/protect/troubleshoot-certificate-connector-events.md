---
title: Risolvere i problemi relativi a Connettore di certificati di Microsoft Intune e agli ID evento | Microsoft Docs
description: Risolvere i problemi relativi a Connettore di certificati di Microsoft Intune esaminando gli ID e le descrizioni degli eventi ed esaminare i codici di diagnostica per il servizio Intune Connector.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/01/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 682d51269798dff181a3bd8384268da862118a70
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71721760"
---
# <a name="intune-certificate-connector-events-and-diagnostic-codes"></a>Eventi di Connettore di certificati di Intune e codici di diagnostica

A partire dalla versione 6.1806.x.x, il servizio Intune Connector registra gli eventi nel **Visualizzatore eventi** (**Registri applicazioni e servizi** > **Microsoft Intune Connector**). Questi eventi consentono di risolvere potenziali problemi nella configurazione di Intune Connector, registrano le operazioni riuscite e non riuscite e contengono anche i codici di diagnostica e i messaggi con i quali l'amministratore IT può risolvere i problemi.

> [!TIP]  
> Per risolvere i problemi e verificare l'installazione di Intune Connector, vedere gli [esempi di script di Autorità di certificazione](https://aka.ms/intuneconnectorverificationscript).

## <a name="event-ids-and-descriptions"></a>ID eventi e descrizioni

| ID evento      | Nome evento    | Descrizione evento | Codici di diagnostica correlati |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | Servizio Connector avviato | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | Servizio Connector arrestato | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | Certificato di registrazione a Connector rinnovato | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | Certificato di registrazione a Connector non rinnovato. Reinstallare il connettore. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | Non è possibile recuperare il certificato di registrazione al connettore dal Registro di sistema. Esaminare i dettagli evento per l'identificazione personale del certificato corrispondente a questo evento. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | Controllare le informazioni di diagnostica nei dettagli evento. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | È stato rilasciato un certificato PKCS. Esaminare i dettagli evento per ID dispositivo, ID utente, nome CA, nome modello certificato e identificazione personale del certificato corrispondenti a questo evento. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | Non è possibile rilasciare un certificato PKCS. Esaminare i dettagli evento per ID dispositivo, ID utente, nome CA, nome modello certificato e identificazione personale del certificato corrispondenti a questo evento. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | Il certificato è stato revocato. Esaminare i dettagli evento per ID dispositivo, ID utente, nome CA e numero di serie del certificato corrispondenti a questo evento. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | Non è possibile revocare il certificato. Esaminare i dettagli evento per ID dispositivo, ID utente, nome CA e numero di serie del certificato corrispondenti a questo evento. Per altre informazioni, vedere i registri SVC NDES.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | Upload eseguito della richiesta di certificato o dei dati di revoca. Esaminare i dettagli evento per i dettagli sul caricamento. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | Non è possibile caricare la richiesta di certificato o i dati di revoca. Esaminare i dettagli evento nello stato di caricamento per determinare il punto in cui si è verificato l'errore.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | Download della richiesta eseguito per firmare un certificato, scaricare un certificato client o revocare un certificato. Esaminare i dettagli evento per i dettagli sul download.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | Non è possibile scaricare la richiesta per firmare un certificato, scaricare un certificato client o revocare un certificato. Esaminare i dettagli evento per i dettagli sul download. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | Il punto di registrazione certificati ha riscontrato un problema di client | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | Il punto di registrazione certificati è stato completato, ma ha rifiutato la richiesta. Vedere il codice di diagnostica e il messaggio per altri dettagli. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | Il punto di registrazione certificati non ha riscontrato un problema di client. Vedere il codice di diagnostica e il messaggio per altri dettagli. Vedere i dettagli del messaggio dell'evento per l'ID dispositivo corrispondente alla richiesta. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | Il punto di registrazione certificati ha terminato il processo di notifica e ha inviato il certificato al dispositivo client. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | Il punto di registrazione certificati non ha terminato il processo di notifica. Vedere i dettagli del messaggio dell'evento per informazioni sulla richiesta. Verificare la connessione tra il server NDES e l'autorità di certificazione. | 0x00000000, 0x0FFFFFFF |

## <a name="diagnostic-codes"></a>Codici di diagnostica

| Codice di diagnostica | Nome diagnostica | Messaggio di diagnostica |
| -------------   | -------------   | -------------      |
| 0x00000000 | Operazione completata  | Operazione completata |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | L'autorità di certificazione non è valida o non è raggiungibile. Verificare che l'autorità di certificazione sia disponibile e che il server possa comunicare con essa. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | Il certificato di autenticazione client Symantec non è stato trovato nell'archivio certificati locale. Vedere [Installare il certificato di registrazione dell'autorità (RA) Symantec](certificates-digicert-configure.md#install-the-digicert-ra-certificate) per altre informazioni.  |
| 0x00000402 | RevokeCert_AccessDenied  | L'account specificato non dispone delle autorizzazioni per revocare un certificato dall'autorità di certificazione. Vedere il campo Nome CA nei dettagli del messaggio dell'evento per determinare l'autorità di certificazione emittente.  |
| 0x00000403 | CertThumbprint_NotFound  | Non è possibile trovare un certificato corrispondente all'input. Registrare il connettore di certificati, quindi riprovare. |
| 0x00000404 | Certificate_NotFound  | Non è possibile trovare un certificato corrispondente all'input specificato. Registrare nuovamente il connettore di certificati, quindi riprovare. |
| 0x00000405 | Certificate_Expired  | Certificato scaduto. Registrare nuovamente il connettore di certificati per rinnovare il certificato, quindi riprovare. |
| 0x00000408 | CRPSCEPCert_NotFound  | Non è possibile trovare il certificato di crittografia CRP. Verificare che NDES e Intune Connector siano configurati correttamente. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | Non è possibile recuperare il certificato di firma. Verificare che il servizio Intune Connector sia configurato correttamente e sia in esecuzione. Verificare anche che gli eventi di download del certificato siano stati completati. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | Non è possibile deserializzare la richiesta di verifica SCEP. Verificare che NDES e Intune Connector siano configurati correttamente. |
| 0x00000411 | CRPSCEPChallenge_Expired  | Richiesta rifiutata. La richiesta di verifica certificato è scaduta. Il dispositivo client può riprovare dopo aver ottenuto una nuova richiesta di verifica dal server di gestione. |
| 0x0FFFFFFFF | Unknown_Error  | Non è possibile completare la richiesta. Si è verificato un errore sul lato server. Riprovare. |


## <a name="next-steps"></a>Passaggi successivi
Per assistenza aggiuntiva, usare la guida [Troubleshooting SCEP certificate profile deployment in Microsoft Intune](https://support.microsoft.com/help/4457481/troubleshooting-scep-certificate-profile-deployment-in-intune) (Risoluzione dei problemi di distribuzione del profilo certificato SCEP in Microsoft Intune).
