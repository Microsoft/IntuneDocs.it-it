---
title: Risolvere i problemi relativi alla segnalazione della riuscita della distribuzione di certificati ai dispositivi quando si usa SCEP con Microsoft Intune | Microsoft Docs
description: Risolvere i problemi relativi alla segnalazione a Intune da parte del servizio Registrazione dispositivi di rete della corretta distribuzione dei certificati di cui è stato eseguito il provisioning con i profili certificato SCEP.
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
ms.openlocfilehash: 2ccc738626efc140efca46d1b997164ed36dd37f
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76916019"
---
# <a name="troubleshoot-ndes-reporting-of-certificate-deployments-in-microsoft-intune"></a>Risolvere i problemi relativi alla segnalazione del servizio Registrazione dispositivi di rete della distribuzione di certificati in Microsoft Intune

Usare le informazioni seguenti per confermare che il servizio Registrazione dispositivi di rete e il Connettore di certificati di Microsoft Intune segnalano correttamente a Intune che il certificato è stato consegnato a un dispositivo. La segnalazione a Intune è l'ultima fase dell'uso dei profili certificato SCEP per il provisioning di un certificato ai dispositivi Windows.

Questo articolo si applica al passaggio 6 del [flusso di lavoro di comunicazione SCEP](troubleshoot-scep-certificate-profiles.md).

## <a name="review-for-signs-of-successful-reporting"></a>Verifica dei segnali della segnalazione riuscita

Se la segnalazione ha avuto esito positivo, nel servizio Registrazione dispositivi di rete saranno disponibili voci simili agli esempi seguenti:

- **Log IIS**:

  `fe80::f53d:89b8:c3e8:5fec%13 POST /CertificateRegistrationSvc/Certificate/Notify - 443 - fe80::f53d:89b8:c3e8:5fec%13 NDES_Plugin - 204 0 0 277 62`

- **NDESPlugin.log**:

  ```
  Calling Notifyrequest ...
  Sending request to certificate registration point.
  Exiting Notify with 0x0
  ```

- **CertificateRegistrationPoint.svclog**:

  ![Log Connettore di certificati di Intune](../protect/media/troubleshoot-scep-certificate-reporting/certificate-registration-point-log.png)

- **NDESConnector.svclog**:

  ![Log Connettore di certificati di Intune](../protect/media/troubleshoot-scep-certificate-reporting/ndesconnector-log.png)

- **CertificateRequestStatus**:

  Passare alla cartella *%ProgramFiles%\Microsoft Intune\CertificateRequestStatus* nelle cui sottocartelle **Failed** (Non riusciti), **Processing** (In corso) e **Succeed** (Riusciti) sono presenti i file di stato delle richieste di certificati.

  Se la richiesta di certificato viene elaborata correttamente, i nuovi file vengono visualizzati nella cartella **Succeed**. È possibile usare *Notepad.exe* per aprire i file e visualizzare i dati caricati nel servizio Intune dal Connettore di certificati di Intune. I dati caricati includono dettagli come **CertificateSerialNumber**, **UserID**, **DeviceID** e **Thumbprint**.

### <a name="troubleshoot-stuck-files"></a>Risolvere i problemi relativi ai file bloccati

Se non viene visualizzato nessun nuovo file creato nella cartella *Succeed* controllare se sono presenti file bloccati nella cartella *Processing*.

Verificare che il servizio Intune Connector sia stato avviato nel server NDES e che non siano presenti errori in Ndesconnector.svclog.

## <a name="next-steps"></a>Passaggi successivi

[Come ottenere supporto per Microsoft Intune](../fundamentals/get-support.md)
