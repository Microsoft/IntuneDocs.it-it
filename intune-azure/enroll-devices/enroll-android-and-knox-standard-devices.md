---
title: Registrare i dispositivi Android in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come registrare dispositivi Android nell&quot;anteprima di Intune in Azure.'
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: b2cbabea781840df0a2a283f803dc76520590aba
ms.lasthandoff: 04/19/2017


---

# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune consente di gestire i dispositivi Android, inclusi i dispositivi Samsung Knox Standard. Per abilitare la gestione dei dispositivi gli utenti devono registrarli scaricando l'app Portale aziendale di Intune, disponibile in Google Play, quindi aprire l'app e seguire le istruzioni per la registrazione. Dopo aver registrato per la gestione i dispositivi Android, è possibile [creare criteri di conformità](https://docs.microsoft.com/intune-azure/set-device-compliance/create-a-compliance-policy-for-android), [gestire le app](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-management) e altro ancora.

I dispositivi che eseguono Samsung KNOX Standard sono ora supportati per la gestione multiutente in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure AD e il dispositivo viene gestito centralmente e indipendentemente dal fatto che sia o meno in uso. Quando gli utenti finali eseguono l'accesso, possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

## <a name="prerequisite"></a>Prerequisito

È necessario impostare l'autorità MDM su **Microsoft Intune** per preparare la gestione dei dispositivi mobili. Vedere [Impostare l'autorità MDM](set-mdm-authority.md) per le istruzioni. Questo elemento viene impostato solo quando si configura Intune per la gestione dei dispositivi mobili per la prima volta. Pertanto è possibile che sia già stato impostato.

## <a name="set-up-android-enrollment"></a>Configurare la registrazione di Android

Per impostazione predefinita, Intune consente già la registrazione di dispositivi Android e Samsung Knox Standard.

Per bloccare la registrazione dei dispositivi Android o la registrazione dei soli dispositivi Android di proprietà personale, vedere [Impostare le restrizioni sul tipo di dispositivi](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-type-restrictions).

Per impostare il numero massimo di dispositivi che un utente può registrare, vedere [Impostare le restrizioni sul limite dei dispositivi](https://docs.microsoft.com/intune-azure/enroll-devices/set-enrollment-restrictions#set-device-limit-restrictions).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali

È necessario indicare agli utenti di accedere a Google Play, scaricare l'app Portale aziendale di Intune e aprire l'app, quindi seguire le istruzioni per la registrazione del dispositivo. L'app indica agli utenti le operazioni da eseguire per la registrazione, spiegando cosa possono aspettarsi e quali dati del dispositivo saranno visibili o meno agli amministratori IT.

È anche possibile inviare loro un collegamento alla procedura di registrazione online: [Registrare il dispositivo Android in Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android).

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Uso del dispositivo Android con Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)

