---
title: Registrare dispositivi Android in Intune | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: informazioni su come registrare dispositivi Android nell&quot;anteprima di Intune in Azure.'
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 12/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 990062ecf03a117dad74eb71e3f40abb79f22be6
ms.openlocfilehash: edd6303f3bb05dfff758cbb7d4bd08e21f083998


---

# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

In qualità di amministratore di Intune, è possibile abilitare la gestione di dispositivi Android dal portale aziendale, inclusi i dispositivi Samsung KNOX Standard. Gli utenti possono quindi registrare i propri dispositivi usando l'app Portale aziendale disponibile da Google Play.

## <a name="prerequisite"></a>Prerequisito

È necessario impostare l'autorità MDM su **Microsoft Intune** per preparare la gestione dei dispositivi mobili. Vedere [Impostare l'autorità MDM](set-mdm-authority.md) per le istruzioni. Questo elemento viene impostato solo quando si configura Intune per la gestione dei dispositivi mobili per la prima volta. Pertanto è possibile che sia già stato impostato. 

## <a name="set-up-android-enrollment"></a>Configurare la registrazione di Android

Per impostazione predefinita, Intune è configurato per consentire la registrazione di dispositivi Android e Samsung Knox Standard. 

Per visualizzare l'impostazione che consente o blocca la registrazione di dispositivi Android, passare al pannello Intune nel portale di Azure e scegliere **Registrazione** > **Restrizioni registrazione**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali

Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Android in Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-android). Il processo di registrazione indica agli utenti cosa possono aspettarsi e i dati visibili o meno agli amministratori IT nei propri dispositivi.

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Uso del dispositivo Android con Intune](https://docs.microsoft.com/intune/enduser/using-your-android-device-with-intune)


<!--HONumber=Feb17_HO1-->


