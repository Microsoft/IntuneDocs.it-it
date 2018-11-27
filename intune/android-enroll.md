---
title: Registrare i dispositivi Android in Intune
titlesuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi Android in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 2b2b3ba5443cd95cd81bdca6d386ab95a2c831eb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190116"
---
# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

In qualità di amministratore di Intune, è possibile gestire i dispositivi Android seguenti:
- I dispositivi Android, inclusi i dispositivi Samsung KNOX Standard.
- I dispositivi Android Enterprise, compresi i [dispositivi del profilo di lavoro Android](#enable-enrollment-of-android-for-work-devices) e i dispositivi Android in modalità tutto schermo.

I dispositivi che eseguono Samsung Knox Standard sono supportati per la gestione multiutente in Intune. Gli utenti finali possono accedere e disconnettersi da un dispositivo con le credenziali di Azure AD. Il dispositivo è gestito a livello centrale indipendentemente dal fatto che sia o meno in uso. Quando gli utenti eseguono l'accesso possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

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

Android Enterprise è un set di funzionalità e servizi dei dispositivi Android che separa le app e i dati personali da quelli lavorativi inclusi in un profilo di lavoro. I dispositivi Android Enterprise includono i dispositivi del profilo di lavoro e i dispositivi in modalità tutto schermo. 

Per configurare la registrazione per i dispositivi Android Enterprise, è necessario prima [connettere Android Enterprise a Intune](connect-intune-android-enterprise.md). Dopo aver completato questo passaggio, è possibile:

[Configurare le registrazioni del profilo di lavoro Android](android-work-profile-enroll.md)
[Configurare le registrazioni dei dispositivi Android in modalità tutto schermo](android-kiosk-enroll.md)

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Esperienza utente finale durante la registrazione di un dispositivo Samsung Knox
Esistono diversi punti da considerare durante la registrazione di dispositivi Samsung Knox:
-   Anche se per i criteri non è necessario un PIN, il dispositivo deve avere almeno un PIN di quattro cifre per essere registrato. Se il dispositivo non ha un PIN, l'utente dovrà crearne uno.
-   Non esiste interazione da parte dell'utente per i certificati Workplace Join (WPJ).
-   L'utente deve specificare le informazioni relative alla registrazione del servizio e le operazioni che l'app può eseguire.
-   L'utente deve specificare le informazioni relative alla registrazione Knox e le operazioni che Knox può eseguire.
-   Se viene applicato un criterio di crittografia, gli utenti devono impostare una password complessa di sei caratteri come passcode del dispositivo.
-   Non sono richieste conferme aggiuntive da parte dell'utente per installare i certificati inseriti da un servizio per l'accesso alle risorse aziendali.
- Alcuni dispositivi Knox meno recenti chiederanno all'utente i certificati aggiuntivi usati per l'accesso alle risorse aziendali.
- Se l'installazione di un dispositivo Samsung Mini non riesce a installare WPJ e vengono visualizzati gli errori **Certificate Not Found** (Certificato non trovato) oppure **Unable to Register Device** (Impossibile registrare il dispositivo), installare gli ultimi aggiornamenti del firmware Samsung.
