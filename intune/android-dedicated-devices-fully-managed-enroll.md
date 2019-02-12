---
title: Registrare dispositivi Android dedicati o completamente gestiti in Intune
titlesuffix: Microsoft Intune
description: Informazioni su come registrare dispositivi Android Enterprise dedicati o completamente gestiti in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a83676f67866bc81ea81f7bb721dec5825a95c9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843443"
---
# <a name="enroll-your-android-dedicated-devices-or-fully-managed-devices-preview"></a>Registrare i dispositivi Android dedicati o completamente gestiti (anteprima)

Dopo aver configurato i [dispositivi Android dedicati](android-kiosk-enroll.md) o [completamente gestiti](android-fully-managed-enroll.md) in Intune, è possibile registrarli. La modalità di registrazione dei dispositivi Android varia a seconda del sistema operativo.

| Metodo di registrazione | Versione minima del sistema operativo Android per i dispositivi dedicati e completamente gestiti |
| ----- | ----- |
| NFC (Near Field Communication) | 5.1 |
| Token | 6.0 |
| Codice a matrice | 7.0 |
| Zero Touch  | 8.0\* |

\* Per i produttori partecipanti.

### <a name="enroll-by-using-near-field-communication-nfc"></a>Registrare con Near Field Communication (NFC)

Per i dispositivi che supportano NFC, è possibile effettuarne il provisioning creando un tag NFC con formattazione speciale. È possibile usare l'app o qualsiasi strumento di creazione di tag NFC. Per altre informazioni, vedere [C-based Android Enterprise device enrollment with Microsoft Intune](https://blogs.technet.microsoft.com/cbernier/2018/10/15/nfc-based-android-enterprise-device-enrollment-with-microsoft-intune/) (Registrazione di dispositivi Android Enterprise basati su C con Microsoft Intune) e la [documentazione relativa all'API di gestione di Android di Google](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Registrare con un token

Per i dispositivi Android 6 e versioni successive, è possibile usare il token per registrare il dispositivo. In Android 6.1 e versioni successive è anche possibile sfruttare la scansione del codice a matrice quando si usa il metodo di registrazione **afw#setup**.

1. Accendere il dispositivo cancellato.
2. Nella schermata **Benvenuto** selezionare la lingua.
3. Connettersi al **Wi-Fi** e quindi scegliere **AVANTI**.
4. Accettare i termini e le condizioni di Google e quindi scegliere **AVANTI**.
5. Nella schermata di accesso di Google immettere **afw#setup** anziché un account Gmail e quindi scegliere **AVANTI**.
6. Scegliere **INSTALLA** per l'app **Android Device Policy**.
7. Continuare l'installazione dei criteri.  Per alcuni dispositivi è necessario accettare condizioni aggiuntive. 
8. Nella schermata **Enroll this device** (Registra questo dispositivo) consentire al dispositivo di eseguire la scansione del codice a matrice oppure scegliere di specificare il token manualmente.
9. Seguire le istruzioni visualizzate per completare la registrazione. 

### <a name="enroll-by-using-a-qr-code"></a>Registrare con un codice a matrice

Nei dispositivi Android 7 e versioni successive è possibile eseguire la scansione del codice a matrice dal profilo di registrazione per registrare il dispositivo.

> [!Note]
> Lo zoom del browser può impedire ai dispositivi di eseguire la scansione del codice a matrice. È possibile risolvere il problema aumentando il livello di zoom del browser.

1. Per avviare la lettura del codice a matrice nel dispositivo Android, toccare più volte nella prima schermata visualizzata dopo la cancellazione.
2. Per i dispositivi Android 7 e 8, verrà richiesto di installare un lettore di codici a matrice. I dispositivi Android 9 e versioni successive includono già un lettore di codici a matrice installato.
3. Usare il lettore di codici a matrice per eseguire la scansione del codice a matrice del profilo di registrazione e quindi seguire le istruzioni visualizzate per effettuare la registrazione.

### <a name="enroll-by-using-google-zero-touch"></a>Registrare con Zero Touch di Google

Per usare il sistema Zero Touch di Google è necessario che il dispositivo lo supporti e sia associato a un fornitore che partecipa al servizio.  Per altre informazioni, vedere il [sito Web del programma Zero Touch di Google](https://www.android.com/enterprise/management/zero-touch/). 

1. Creare una nuova configurazione nella console di Zero Touch.
2. Scegliere **Microsoft Intune** dall'elenco a discesa EMM DPC.
3. Nella console di Zero Touch di Google copiare e incollare il codice JSON seguente nel campo degli elementi aggiuntivi DPC. Sostituire la stringa *YourEnrollmentToken* con il token di registrazione creato come parte del profilo di registrazione. Assicurarsi di racchiudere il token di registrazione tra virgolette doppie.

```
{ 
    "android.app.extra.PROVISIONING_DEVICE_ADMIN_COMPONENT_NAME": "com.google.android.apps.work.clouddpc/.receivers.CloudDeviceAdminReceiver", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_SIGNATURE_CHECKSUM": "I5YvS0O5hXY46mb01BlRjq4oJJGs2kuUcHvVkAPEXlg", 

    "android.app.extra.PROVISIONING_DEVICE_ADMIN_PACKAGE_DOWNLOAD_LOCATION": "https://play.google.com/managed/downloadManagingApp?identifier=setup", 

    "android.app.extra.PROVISIONING_ADMIN_EXTRAS_BUNDLE": { 
        "com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "YourEnrollmentToken" 
    } 
} 
```
4. Scegliere **Applica**.


## <a name="next-steps"></a>Passaggi successivi
- [Distribuire app Android](apps-deploy.md)
- [Aggiungere criteri di configurazione di Android](device-profiles.md)

