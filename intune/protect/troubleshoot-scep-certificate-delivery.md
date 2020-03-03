---
title: Risolvere i problemi di consegna dei certificati ai dispositivi quando si usa SCEP con Microsoft Intune | Microsoft Docs
description: Risolvere i problemi di consegna di un certificato a un dispositivo dall'autorità di certificazione quando si usano i profili certificato SCEP con Intune per distribuire i certificati.
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
ms.openlocfilehash: 40075ad3c90f9ce5131d88780d15eec5c258e276
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515255"
---
# <a name="troubleshoot-the-delivery-of-certificates-provisioned-by-scep-to-devices-in-microsoft-intune"></a>Risolvere i problemi di consegna dei certificati con provisioning SCEP ai dispositivi in Microsoft Intune

Usare le informazioni in questo articolo per esaminare la consegna dei certificati ai dispositivi quando si usa Simple Certificate Enrollment Protocol (SCEP) per il provisioning dei certificati in Intune. Dopo che il server del servizio Registrazione dispositivi di rete (NDES) riceve il certificato richiesto per un dispositivo dall'autorità di certificazione (CA), il server restituisce il certificato al dispositivo.

Questo articolo si applica al passaggio 5 del [flusso di lavoro di comunicazione SCEP](troubleshoot-scep-certificate-profiles.md): consegna del certificato al dispositivo che ha inviato la richiesta di certificato.

## <a name="review-the-certification-authority"></a>Esaminare l'autorità di certificazione

Dopo che l'autorità di certificazione ha emesso il certificato, visualizza una voce simile all'esempio seguente:

![Esempio di certificati emessi](../protect/media/troubleshoot-scep-certificate-delivery/certificate-authority.png)

## <a name="review-the-device"></a>Esaminare il dispositivo

### <a name="android"></a>Android

Per i dispositivi registrati dall'amministratore del dispositivo viene visualizzata una notifica simile all'immagine seguente, che richiede di installare il certificato:

![Notifica Android](../protect/media/troubleshoot-scep-certificate-delivery/android-notification.png)

Per Android Enterprise o Samsung Knox, l'installazione del certificato è automatica e invisibile all'utente.

Per visualizzare un certificato installato in Android usare un'app di visualizzazione certificati di terze parti.

È anche possibile esaminare il [log OMADM dei dispositivi](troubleshoot-scep-certificate-profiles.md#logs-for-android-devices). Cercare voci simili alle seguenti, che vengono registrate quando si installano i certificati:

**Certificato radice**:

```
2018-02-27T04:50:52.1890000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        9    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALL_REQUESTED
2018-02-27T04:53:31.1300000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595        0    Root cert '17…' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T04:53:32.0390000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeRootCertInstallStateMachine     9595       14    Root cert '17…' state changed from CERT_INSTALLING to CERT_INSTALL_SUCCESS
```

**Certificato con provisioning tramite SCEP**

```
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    There are 1 requests
2018-02-27T05:16:08.2500000    VERB    Event     com.microsoft.omadm.platforms.android.certmgr.CertificateEnrollmentManager    18327       10    Trying to enroll certificate request: ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787
2018-02-27T05:16:20.6150000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:20.6530000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACert(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=ca
2018-02-27T05:16:21.7460000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:21.7890000    VERB    Event     org.jscep.transport.UrlConnectionGetTransport    18327       10    Received '200 OK' when sending GetCACaps(ca) to https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=ca
2018-02-27T05:16:28.0340000    VERB    Event     org.jscep.transaction.EnrollmentTransaction    18327       10    Response: org.jscep.message.CertRep@3150777b[failInfo=<null>,pkiStatus=SUCCESS,recipientNonce=Nonce [GUID],messageData=org.spongycastle.cms.CMSSignedData@27cc8998,messageType=CERT_REP,senderNonce=Nonce [GUID],transId=TRANSID]
2018-02-27T05:16:28.2440000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       10    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ENROLLED to CERT_INSTALL_REQUESTED
2018-02-27T05:18:44.9820000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327        0    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALL_REQUESTED to CERT_INSTALLING
2018-02-27T05:18:45.3460000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       14    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_INSTALLING to CERT_ACCESS_REQUESTED
2018-02-27T05:20:15.3520000    INFO    Event     com.microsoft.omadm.platforms.android.certmgr.state.NativeScepCertInstallStateMachine    18327       21    SCEP cert 'ModelName=AC_51…%2FLogicalName_39907…;Hash=1677525787' state changed from CERT_ACCESS_REQUESTED to CERT_ACCESS_GRANTED
```

### <a name="iosipados"></a>iOS/iPadOS

Nel dispositivo iOS/iPadOS o iPadOS è possibile visualizzare il certificato nel profilo di gestione dei dispositivi. Eseguire il drill-in per visualizzare i dettagli dei certificati installati.

![Certificato iOS](../protect/media/troubleshoot-scep-certificate-delivery/ios-certificate.png)

È anche possibile trovare voci simili alle seguenti nel [log di debug iOS](troubleshoot-scep-certificate-profiles.md#logs-for-ios-and-ipados-devices):

```
Debug 18:30:53.691033 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACert&message=SCEP%20Authority\  
Debug 18:30:54.640644 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=GetCACaps&message=SCEP%20Authority\ 
Debug 18:30:55.487908 -0500 profiled Performing synchronous URL request: https://<server>-contoso.msappproxy.net/certsrv/mscep/mscep.dll?operation=PKIOperation&message=MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgMFADCABgkqhkiG9w0BBwGggCSABIIZfzCABgkqhkiG9w0BBwOggDCAAgEAMYIBgjCCAX4CAQAwZjBPMRUwEwYKCZImiZPyLGQBGRYFbG9jYWwxHDAaBgoJkiaJk/IsZAEZFgxmb3VydGhjb2ZmZWUxGDAWBgNVBAMTD0ZvdXJ0aENvZmZlZSBDQQITaAAAAAmaneVjEPlcTwAAAAAACTANBgkqhkiG9w0BAQEFAASCAQCqfsOYpuBToerQLkw/tl4tH9E+97TBTjGQN9NCjSgb78fF6edY0pNDU+PH4RB356wv3rfZi5IiNrVu5Od4k6uK4w0582ZM2n8NJFRY7KWSNHsmTIWlo/Vcr4laAtq5rw+CygaYcefptcaamkjdLj07e/Uk4KsetGo7ztPVjSEFwfRIfKv474dLDmPqp0ZwEWRQG 
Debug 18:30:57.285730 -0500 profiled Adding dependent Microsoft.Profiles.MDM to parent www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295 in domain ManagedProfileToManagingProfile to system\ 
Default 18:30:57.320616 -0500 profiled Profile \'93www.windowsintune.com.SCEP.ModelName=AC_51bad41f.../LogicalName_1892fe4c...;Hash=-912418295\'94 installed.\ 
```

### <a name="windows"></a>Windows

Nel dispositivo Windows verificare che il certificato sia stato consegnato:

- Eseguire **eventvwr.msc** per aprire il Visualizzatore eventi. Passare **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Amministrazione** e cercare l'**evento 39**. Questo evento deve avere la descrizione generale seguente: **SCEP: Certificate installed successfully.** (SCEP: Certificato installato correttamente)

   ![Evento 39 nel Registro applicazioni di Windows](../protect/media/troubleshoot-scep-certificate-delivery/device-app-log.png)

Per visualizzare il certificato nel dispositivo, eseguire **certmgr.msc** per aprire MMC Certificati e verificare che i certificati radice e SCEP siano installati correttamente nel dispositivo, nell'archivio personale:

   1. Passare a **Certificati (Computer locale)** > **Autorità di certificazione radice attendibili** > **Certificati** e verificare che sia presente il certificato radice dell'autorità di certificazione. I valori *Rilasciato a* e *Rilasciato da* sono uguali.
   2. In MMC Certificati passare a **Certificati - Utente corrente** > **Personale** > **Certificati** e verificare che sia presente il certificato richiesto e che *Rilasciato da* corrisponda al nome dell'autorità di certificazione.

## <a name="troubleshoot-failures"></a>Risolvere i problemi in caso di errori

### <a name="android"></a>Android

Per risolvere i problemi relativi a questo passaggio, esaminare gli errori registrati nel log DM OMA.

### <a name="iosipados"></a>iOS/iPadOS

Per risolvere i problemi relativi a questo passaggio, esaminare gli errori registrati nel log di debug dei dispositivi.

### <a name="windows"></a>Windows

Per risolvere i problemi relativi alla mancata installazione del certificato nel dispositivo, controllare se nel Registro eventi di Windows sono presenti errori che suggeriscono problemi:

- Nel dispositivo eseguire **eventvwr.msc** per aprire il Visualizzatore eventi, quindi passare a **Registri applicazioni e servizi** > **Microsoft** > **Windows** > **DeviceManagement-Enterprise-Diagnostic-Provider** > **Amministrazione**.

Gli errori di consegna e di installazione del certificato nel dispositivo sono in genere correlati alle operazioni di Windows e non a Intune.

## <a name="next-steps"></a>Passaggi successivi

Quando il certificato viene distribuito correttamente nel dispositivo ma Intune non segnala l'esito positivo, vedere [Segnalazioni del servizio Registrazione dispositivi di rete a Intune](troubleshoot-scep-certificate-reporting.md) per risolvere i problemi relativi alle segnalazioni.
