---
title: Distribuire criteri e app
description: "È possibile abilitare le impostazioni dei criteri e distribuire le app che verranno applicate subito dopo la registrazione dei dispositivi nel sistema di gestione."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e0d8e98f-7dd8-4cbf-887c-a9af63ffe970
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d0a0a3670388ec95cff86b09ea81661a0825ba83
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="create-policies-and-publish-apps"></a>Creare criteri e pubblicare app

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento descrive come gli amministratori di Intune possono creare criteri e pubblicare app che possono essere in seguito distribuite nei dispositivi gestiti.

Prima di iniziare a registrare le app in Intune è possibile abilitare le impostazioni dei criteri e le app che verranno distribuite non appena i dispositivi risultano inclusi nella gestione. I criteri di Intune specificano impostazioni che consentono di controllare le impostazioni di sicurezza dei dispositivi mobili, di eseguire la manutenzione delle impostazioni di Windows Firewall ed Endpoint Protection per i computer, nonché di distribuire applicazioni. È possibile configurare criteri, aggiungere app e distribuire tali app, in modo che i dispositivi ricevano le impostazioni e le app non appena vengono registrati in Intune.

Criteri e app sono specifici della piattaforma.

## <a name="manage-device-settings"></a>Gestire le impostazioni dei dispositivi

 Le impostazioni dei criteri per i dispositivi devono essere configurate e gestite separatamente per ogni piattaforma. I collegamenti seguenti consentono di accedere a elenchi delle impostazioni disponibili per le rispettive piattaforme:

- [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune)
- [Android e Samsung KNOX Standard](/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune)
- [Android for Work](/intune-classic/deploy-use/android-for-work-policy-settings-in-microsoft-intune)
- [Windows 10 (PC e dispositivi mobili)](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)
- [Windows 8.1](/intune-classic/deploy-use/windows-configuration-policy-settings-in-microsoft-intune)
- [Windows Phone 8.1](/intune-classic/deploy-use/windows-phone-8-1-policy-settings-in-microsoft-intune)
- [Windows Team](/intune-classic/deploy-use/windows-team-configuration-policy-settings-in-microsoft-intune)
- [PC Windows che eseguono il software client di Intune](/intune-classic/deploy-use/policies-to-protect-windows-pcs-in-microsoft-intune)

Sono disponibili altre informazioni su come [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies).

## <a name="add-and-deploy-apps"></a>Aggiungere e distribuire app

È possibile aggiungere app a Intune e quindi distribuirle ai dispositivi gestiti in due modi:
- **Installazione richiesta** - Le app vengono installate automaticamente nei dispositivi gestiti
- **Installazione disponibile** - Le app vengono visualizzate nel portale aziendale di Intune in modo che gli utenti possano scegliere se installarle nei dispositivi

### <a name="add-apps"></a>Aggiungere app

È prima di tutto necessario rendere disponibili le app in Intune con uno dei metodi seguenti:
- [Aggiungere app per dispositivi registrati](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)
- [Aggiungere app per PC con il software client di Intune](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)

### <a name="deploy-apps"></a>Distribuire le app

Ora che l'app è disponibile in Intune, è possibile distribuirla nei dispositivi gestiti:
- [Distribuire le app nei dispositivi](/intune-classic/deploy-use/deploy-use/deploy-apps-in-microsoft-intune)
- Distribuire app acquistate con Volume Purchase Program:
    - [iOS - Volume Purchase Program](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)
    - [Microsoft Store per le aziende](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)
    - [Android for Work](/intune-classic/deploy-use/android-for-work-apps)

    Dopo aver configurato le app per la distribuzione è possibile [configurare le app](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Organizzare utenti e dispositivi**](.\start-with-a-paid-subscription-to-microsoft-intune-step-5.md)[**Personalizzare il Portale aziendale** &rarr;](/intune/company-portal-customize)  
