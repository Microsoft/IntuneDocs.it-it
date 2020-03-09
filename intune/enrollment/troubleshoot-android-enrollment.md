---
title: Risoluzione dei problemi dei dispositivi Android Enterprise in Microsoft Intune
description: Suggerimenti per la risoluzione di alcuni dei problemi più comuni quando si registrano dispositivi Android in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/25/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04c726c1dc6af7e92b75335d105de605ef00e712
ms.sourcegitcommit: 8b716db3c0fdbb7dff62497ec283902a5069a343
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652369"
---
# <a name="troubleshoot-android-enterprise-device-problems-in-microsoft-intune"></a>Risoluzione dei problemi dei dispositivi Android Enterprise in Microsoft Intune

Questo articolo aiuta gli amministratori di Intune a comprendere e risolvere i problemi relativi ai dispositivi Android Enterprise in Intune.

## <a name="apps-on-android-enterprise-devices"></a>App in dispositivi Android Enterprise

### <a name="managed-google-play-apps-that-arent-deployed-through-intune-are-displayed-in-the-work-profile"></a>Le app di Google Play gestito non distribuite tramite Intune vengono visualizzate nel profilo di lavoro
Le app di sistema possono essere abilitate nel profilo di lavoro dall'OEM del dispositivo al momento della creazione del profilo di lavoro. Questo non è controllato dal provider MDM.

Per risolvere il problema, seguire questa procedura:

  1. Raccogliere i log del Portale aziendale.
  2. Prendere nota delle app non previste visualizzate nel profilo di lavoro.
  3. Annullare la registrazione del dispositivo da Intune e disinstallare il Portale aziendale.
  4. Installare l'app [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc), che consente di creare un profilo di lavoro senza EMM per il test.
  5. Seguire le istruzioni di [Test DPC](https://play.google.com/store/apps/details?id=com.afwsamples.testdpc) per creare un profilo di lavoro nel dispositivo.
  6. Esaminare le app visualizzate nel profilo di lavoro. 
  7. Se le stesse applicazioni vengono visualizzate nell'app test DPC, le app sono previste dall'OEM per tale dispositivo.

### <a name="unapproved-managed-google-play-for-work-store-apps-arent-being-removed-from-the-client-apps-page-in-intune"></a>Le app dello store Google Play for Work gestito non vengono rimosse dalla pagina App client in Intune
Si tratta di un comportamento previsto.

### <a name="managed-google-play-apps-arent-being-reported-under-the-discovered-apps-blade-in-the-intune-portal"></a>Le app di Google Play gestito non vengono segnalate nel pannello App individuate nel portale di Intune
Si tratta di un comportamento previsto. Solo le app di sistema installate nel profilo di lavoro vengono inventariate nel pannello App individuate. Per visualizzare le applicazioni di Google Play gestito installate, usare il pannello **App gestite**.

### <a name="are-web-applications-supported-for-work-profile-enrolled-devices"></a>Le applicazioni Web sono supportate per i dispositivi registrati con il profilo di lavoro?
Sì. Per altre informazioni, vedere [Collegamenti Web di Google Play gestito](../apps/apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="device-management"></a>Gestione dei dispositivi

### <a name="file-path-internal-storageandroiddatacommicrosoftwindowsintunecompanyportalfiles-missing-on-work-profile-enrolled-devices"></a>Percorso file Internal storage/Android/Data.com.microsoft.windowsintune.companyportal/files mancante nei dispositivi registrati con il profilo di lavoro

  **Risposta**: Si tratta di un comportamento previsto. Questo percorso viene creato solo per lo scenario di amministrazione del dispositivo (registrazione Android legacy).

  Per raccogliere i log del Portale aziendale, seguire questa procedura:

  1. Nell'app Portale aziendale con il badge toccare **Menu** > **Guida** > **Invia messaggio di posta elettronica al supporto** e quindi toccare **Invia messaggio di posta elettronica & Carica i log**. 
  2. Quando viene visualizzato **Inviare una richiesta di supporto con**, selezionare una delle app di posta elettronica.
  3. Viene generato un messaggio di posta elettronica per l'amministratore IT con un ID evento imprevisto che può essere fornito al Servizio Supporto tecnico del prodotto Microsoft.

### <a name="managed-google-play-last-sync-time--hasnt-been-updated-in-days"></a>L'ora dell'ultima sincronizzazione di Google Play gestito non viene aggiornata da giorni
Si tratta di un comportamento previsto. La sincronizzazione viene attivata solo se eseguita manualmente.

### <a name="encryption-is-required-when-a-device-is-enrolled-can-it-be-turned-off"></a>La crittografia è obbligatoria quando viene registrato un dispositivo. Può essere disattivata?
No, Google richiede che il dispositivo sia crittografato per creare un profilo di lavoro. 

### <a name="samsung-devices-are-blocking-the-use-of-third-party-keyboards-like-swiftkey"></a>I dispositivi Samsung bloccano l'uso di tastiere di terze parti, ad esempio SwiftKey
Samsung ha iniziato ad applicare questa restrizione nei dispositivi Android 8.0 e versioni successive. Microsoft sta attualmente collaborando con Samsung per risolvere questo problema e pubblicherà nuove informazioni non appena saranno disponibili.

## <a name="remote-actions"></a>Azioni remote

### <a name="wipe-factory-reset-option-isnt-available-for-work-profile-enrolled-device"></a>L'opzione di cancellazione (Ripristino delle impostazioni predefinite) non è disponibile per il dispositivo registrato con il profilo di lavoro
Si tratta di un comportamento previsto. Nello scenario del profilo di lavoro, il provider MDM non ha il controllo completo sul dispositivo. L'unica opzione disponibile è Ritiro (Rimuovi i dati aziendali) che rimuove l'intero profilo di lavoro e tutto il contenuto.

### <a name="is-device-passcode-reset-supported"></a>La reimpostazione del passcode del dispositivo è supportata?
Per i dispositivi registrati con il profilo di lavoro, è possibile reimpostare il passcode del profilo di lavoro solo nei dispositivi Android 8.0 o versione successiva nei casi seguenti:
- Il passcode del profilo di lavoro è gestito.
- L'utente finale ha consentito che venga reimpostato.

Per i dispositivi dedicati (COSU) e completamente gestiti, la reimpostazione del passcode del dispositivo è supportata.


## <a name="next-steps"></a>Passaggi successivi

- [Risolvere i problemi di registrazione dei dispositivi in Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Porre una domanda nel forum di Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Controllare il blog del team di supporto di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Controllare il blog di Microsoft Enterprise Mobility + Security](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)