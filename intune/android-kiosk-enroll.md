---
title: Registrare i dispositivi in modalità tutto schermo Android Enterprise in Intune
titlesuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi in modalità tutto schermo Android Enterprise in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 6/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 637fe2d2c764cf78e67e728bfa77567cf12e88ce
ms.sourcegitcommit: fff179f59bd542677cbd4bf3bacc24bb880e2cb6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53031994"
---
# <a name="set-up-intune-enrollment-of-android-enterprise-kiosk-devices"></a>Configurare la registrazione in Intune dei dispositivi in modalità tutto schermo Android Enterprise

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android supporta i dispositivi in modalità tutto schermo tramite il set di soluzioni Corporate-Owned, Single-Use. Questo tipo di dispositivi vengono usati per un singolo scopo, ad esempio la firma digitale, la stampa di biglietti o la gestione di inventari. Gli amministratori bloccano l'utilizzo di un dispositivo per un set limitato di app e collegamenti Web. Viene anche impedito agli utenti di aggiungere altre app o eseguire altre azioni sul dispositivo.

Intune consente di distribuire app e impostazioni nei dispositivi in modalità tutto schermo Android. Per informazioni dettagliate su Android Enterprise, vedere [Android enterprise requirements](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) (Requisiti di Android Enterprise).

I dispositivi gestiti in questo modo vengono registrati in Intune senza un account utente e non sono associati ad alcun utente finale. Non sono progettati per le applicazioni o le app a uso personale che richiedono dati di account specifici dell'utente, ad esempio Outlook o Gmail.

## <a name="device-requirements"></a>Requisiti dei dispositivi

Per essere gestiti come dispositivi in modalità tutto schermo Android Enterprise è necessario che i dispositivi soddisfino i requisiti seguenti:

- Sistema operativo Android versione 5.1 e successive.
- I dispositivi devono eseguire una distribuzione di Android che include la connettività Google Mobile Services (GMS). I dispositivi devono includere GMS e devono essere in grado di connettersi a GMS.

## <a name="set-up-android-kiosk-management"></a>Configurare la gestione della modalità tutto schermo per Android

Per configurare la gestione della modalità tutto schermo di Android, seguire questa procedura:

1. Per preparare la gestione dei dispositivi mobili è necessario [impostare l'autorità MDM (Mobile Device Management) su **Microsoft Intune**](mdm-authority-set.md). Questa opzione viene impostata una sola volta, ovvero quando si configura per la prima volta Intune per la gestione dei dispositivi mobili.
2. [Connettere l'account del tenant di Intune all'account Android Enterprise](connect-intune-android-enterprise.md).
3. [Creare un profilo di registrazione.](#create-an-enrollment-profile)
4. [Creare un gruppo di dispositivi](#create-a-device-group).
5. [Registrare i dispositivi in modalità tutto schermo](#enroll-the-kiosk-devices).

### <a name="create-an-enrollment-profile"></a>Creare un profilo di registrazione

È necessario creare un profilo di registrazione per poter registrare i dispositivi in modalità tutto schermo. Il profilo creato fornisce un token di registrazione (stringa casuale) e un codice a matrice (codice QR). A seconda del sistema operativo Android e della versione del dispositivo, è possibile usare il token o il codice a matrice per [registrare il dispositivo in modalità tutto schermo](#enroll-the-kiosk-devices).

1. Passare al [portale di Intune](https://portal.azure.com) e scegliere **Registrazione del dispositivo** > **Registrazione Android** > **Registrazioni dei dispositivi per uso in modalità tutto schermo e per attività**.
2. Scegliere **Crea** e compilare i campi obbligatori.
    - **Nome**: digitare un nome che verrà usato per l'assegnazione del profilo al gruppo di dispositivi dinamico.
    - **Data di scadenza del token**: data in cui il token scade. Google impone un massimo di 90 giorni.
3. Scegliere **Crea** per salvare il profilo.

### <a name="create-a-device-group"></a>Creare un gruppo di dispositivi

È possibile assegnare le app e i criteri a gruppi di dispositivi assegnati o dinamici. Per configurare gruppi di dispositivi AAD dinamici per popolare automaticamente i dispositivi registrati con un profilo di registrazione specifico, seguire questa procedura:

1. Passare al [portale di Intune](https://portal.azure.com) e scegliere **Gruppi** > **Tutti i gruppi** > **Nuovo gruppo**.
2. Nel pannello **Gruppo** compilare i campi obbligatori come segue:
    - **Tipo di gruppo**: Sicurezza
    - **Nome gruppo**: digitare un nome intuitivo, ad esempio Factory 1
    - **Tipo di appartenenza**: Dispositivo dinamico
3. Scegliere **Aggiungi query dinamica**.
4. Nel pannello **Regole di appartenenza dinamica** compilare i campi come segue:
    - **Aggiungi regola di appartenenza dinamica**: Regola semplice
    - **Aggiungi dispositivi dove**: enrollmentProfileName
    - Nella casella centrale scegliere **Corrispondenza**.
    - Nell'ultimo campo immettere il nome del profilo di registrazione creato in precedenza.
    Per altre informazioni sulle regole di appartenenza dinamica, vedere [Regole di appartenenza dinamica per i gruppi in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership). 
5. Scegliere **Aggiungi query** > **Crea**.

### <a name="replace-or-remove-tokens"></a>Sostituire o rimuovere i token

È possibile sostituire o rimuovere i token e i codici a matrice.

- **Sostituisci il token**: è possibile generare un nuovo token o codice a matrice all'approssimarsi della scadenza usando Sostituisci il token.
- **Revoca il token**: è possibile far scadere immediatamente il token o il codice a matrice. Il token o codice a matrice non sarà più utilizzabile. È possibile usare questa opzione se:
    - il token o codice a matrice viene condiviso accidentalmente con un'entità non autorizzata
    - si completano tutte le registrazioni e il token o codice a matrice non è più necessario

La sostituzione o la revoca di un token o codice a matrice non avrà alcun effetto sui dispositivi già registrati.

1. Passare al [portale di Intune](https://portal.azure.com) e scegliere **Registrazione del dispositivo** > **Registrazione Android** > **Registrazioni dei dispositivi per uso in modalità tutto schermo e per attività**.
2. Scegliere il profilo che si vuole usare.
3. Scegliere **Token**.
4. Per sostituire il token, scegliere **Sostituisci il token**.
5. Per revocare il token, scegliere **Revoca il token**.

## <a name="enroll-the-kiosk-devices"></a>Registrare i dispositivi in modalità tutto schermo

Dopo aver creato il profilo di registrazione e il gruppo di dispositivi dinamico, è possibile registrare i dispositivi in modalità tutto schermo. La modalità di registrazione dei dispositivi Android varia a seconda del sistema operativo.

| Metodo di registrazione | Versione del sistema operativo Android minima supportata |
| ----- | ----- |
| NFC (Near Field Communication) | 5.1 |
| Token | 6.0 |
| Codice a matrice | 7.0 |
| Zero Touch | 8.0, su produttori partecipanti |

### <a name="enroll-by-using-near-field-communication-nfc"></a>Registrare con Near Field Communication (NFC)

Per i dispositivi Android 5.1 e versioni successive che supportano NFC, è possibile eseguire il provisioning dei dispositivi creando un tag NFC con formattazione speciale. È possibile usare l'app o qualsiasi strumento di creazione di tag NFC. Per altre informazioni, vedere la [documentazione relativa ad Android Management API di Google](https://developers.google.com/android/management/provision-device#nfc_method).

### <a name="enroll-by-using-a-token"></a>Registrare con un token

Per i dispositivi Android 6 e versioni successive, è possibile usare il token per registrare il dispositivo. In Android 6.1 e versioni successive è anche possibile sfruttare la scansione del codice a matrice quando si usa il metodo di registrazione **aft#setup**.

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

## <a name="managing-apps-on-android-kiosk-devices"></a>Gestione delle app nei dispositivi in modalità tutto schermo Android

Nei dispositivi in modalità schermo intero Android è possibile installare soltanto le app con il tipo di assegnazione [impostato su Obbligatorio](apps-deploy.md#to-assign-an-app). Le app vengono installate da Google Play Store gestito allo stesso modo dei dispositivi del profilo di lavoro Android.

Le app vengono aggiornate automaticamente sui dispositivi gestiti quando lo sviluppatore pubblica un aggiornamento in Google Play.

Per rimuovere un'app dai dispositivi in modalità tutto schermo Android, è possibile eseguire una delle operazioni seguenti:
-   Eliminare la distribuzione dell'app obbligatoria.
-   Creare una distribuzione di disinstallazione per l'app.


## <a name="next-steps"></a>Passaggi successivi
- [Distribuire le app in modalità tutto schermo Android](apps-deploy.md)
- [Aggiungere criteri di configurazione in modalità tutto schermo per Android](device-profiles.md)
