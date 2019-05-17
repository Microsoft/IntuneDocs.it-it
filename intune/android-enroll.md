---
title: Registrare i dispositivi Android in Intune
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi Android in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/31/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 363a7d0ef32aee0c21c6e5cecbd55cc3087f4613
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "59568674"
---
# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In qualità di amministratore di Intune, è possibile gestire i dispositivi Android seguenti:
- I dispositivi Android, inclusi i dispositivi Samsung KNOX Standard.
- I dispositivi Android Enterprise, inclusi:
    - **Dispositivi con profilo di lavoro Android Enterprise**: Dispositivi personali con autorizzazione ad accedere ai dati aziendali. Gli amministratori possono gestire gli account aziendali, le app e i dati. I dati personali nel dispositivo vengono tenuti separati dai dati di lavoro e gli amministratori non controllano le impostazioni o i dati personali. 
    - **Dispositivi dedicati Android Enterprise**: Dispositivi a uso singolo di proprietà dell'azienda, ad esempio per insegna digitale, stampa di biglietti o gestione dell'inventario. Gli amministratori bloccano l'utilizzo di un dispositivo per un set limitato di app e collegamenti Web. Viene anche impedito agli utenti di aggiungere altre app o eseguire altre azioni sul dispositivo.
    - **Dispositivi completamente gestiti Android Enterprise**: Dispositivi con utente singolo di proprietà dell'azienda, usati esclusivamente per lavoro e non per uso personale. Gli amministratori possono gestire interamente tali dispositivi e applicare controlli di criteri non disponibili nei profili di lavoro. 

## <a name="prerequisite"></a>Prerequisito

Per preparare la gestione dei dispositivi mobili è necessario impostare l'autorità per la gestione dei dispositivi mobili su **Microsoft Intune**. Vedere [Impostare l'autorità MDM](mdm-authority-set.md) per le istruzioni. Questo elemento viene impostato una sola volta quando si configura Intune per la gestione dei dispositivi mobili per la prima volta.

## <a name="set-up-android-enrollment"></a>Configurare la registrazione di Android

Per impostazione predefinita, Intune permette la registrazione di dispositivi Android e Samsung Knox Standard. Dopo aver soddisfatto i prerequisiti, gli amministratori devono semplicemente [indicare agli utenti come registrare i propri dispositivi](/intune-user-help/enroll-your-device-in-intune-android).

Dopo che un utente ha eseguito la registrazione, è possibile iniziare a gestirne i dispositivi in Intune con attività quali, ad esempio, [l'assegnazione dei criteri di conformità](compliance-policy-create-android.md), [la gestione delle app](app-management.md) e così via.

Per informazioni su altre attività dell'utente, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](end-user-educate.md)
- [Uso del dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

Per bloccare la registrazione dei dispositivi Android o la registrazione dei soli dispositivi Android di proprietà personale, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).

## <a name="set-up-android-enterprise-enrollment"></a>Configurare la registrazione di Android Enterprise

Android Enterprise offre un set di opzioni di registrazione che forniscono agli utenti le funzionalità più aggiornate e sicure. Le opzioni di registrazione di Android Enterprise includono dispositivi con profilo di lavoro, dispositivi completamente gestiti e dispositivi dedicati.

- [Configurare la registrazione dei dispositivi del profilo di lavoro Android Enterprise](android-work-profile-enroll.md)
- [Configurare la registrazione in Intune di dispositivi Android Enterprise dedicati](android-kiosk-enroll.md)
- [Configurare la registrazione in Intune per dispositivi Android Enterprise completamente gestiti](android-fully-managed-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Esperienza utente finale durante la registrazione di un dispositivo Samsung Knox

I dispositivi con Samsung Knox Standard sono supportati da Intune per la gestione multiutente. Gli utenti finali possono accedere e disconnettersi da un dispositivo con le credenziali di Azure AD. Il dispositivo è gestito a livello centrale indipendentemente dal fatto che sia o meno in uso. Quando gli utenti eseguono l'accesso possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

Esistono diversi punti da considerare durante la registrazione di dispositivi Samsung Knox:
-   Anche se per i criteri non è necessario un PIN, il dispositivo deve avere almeno un PIN di quattro cifre per essere registrato. Se il dispositivo non ha un PIN, l'utente dovrà crearne uno.
-   Non esiste interazione da parte dell'utente per i certificati Workplace Join (WPJ).
-   L'utente deve specificare le informazioni relative alla registrazione del servizio e le operazioni che l'app può eseguire.
-   L'utente deve specificare le informazioni relative alla registrazione Knox e le operazioni che Knox può eseguire.
-   Se viene applicato un criterio di crittografia, gli utenti devono impostare una password complessa di sei caratteri come passcode del dispositivo.
-   Non sono richieste conferme aggiuntive da parte dell'utente per installare i certificati inseriti da un servizio per l'accesso alle risorse aziendali.
- Alcuni dispositivi Knox meno recenti chiederanno all'utente i certificati aggiuntivi usati per l'accesso alle risorse aziendali.
- Se l'installazione di un dispositivo Samsung Mini non riesce a installare WPJ e vengono visualizzati gli errori **Certificate Not Found** (Certificato non trovato) oppure **Unable to Register Device** (Impossibile registrare il dispositivo), installare gli ultimi aggiornamenti del firmware Samsung.

## <a name="next-steps"></a>Passaggi successivi

- [Configurare la registrazione dei dispositivi del profilo di lavoro Android Enterprise](android-work-profile-enroll.md)
- [Configurare la registrazione in Intune di dispositivi Android Enterprise dedicati](android-kiosk-enroll.md)
- [Configurare la registrazione in Intune per dispositivi Android Enterprise completamente gestiti](android-fully-managed-enroll.md)
