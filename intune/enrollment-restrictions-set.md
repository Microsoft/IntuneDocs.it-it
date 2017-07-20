---
title: Impostare restrizioni di registrazione in Intune
titleSuffix: Intune on Azure
description: Limitare la registrazione dalla piattaforma e impostare un limite di registrazione dei dispositivi in Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dfcba8c788f262ce816dcd23dc2921fd57f331b
ms.sourcegitcommit: d1ad84edf4f03cb4c11fe55131556b43fc3a4500
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/05/2017
---
# <a name="set-enrollment-restrictions"></a>Impostare le restrizioni di registrazione

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Gli amministratori di Intune possono determinare quali dispositivi registrare nella gestione con Intune. Usare il portale di Intune per impostare le restrizioni seguenti per la registrazione del dispositivo:

- Numero massimo di dispositivi registrati
- Piattaforme per dispositivi che possono registrare:
  - Android
  - iOS
  - macOS
  - Windows
- Limitare i dispositivi personali (solo iOS e Android)

>[!NOTE]
>Le restrizioni di registrazione non sono una funzionalità di sicurezza. I dispositivi compromessi possano dare risultati non previsti. Queste restrizioni sono una barriera di massimo sforzo per gli utenti legittimi.

## <a name="set-device-type-restrictions"></a>Impostare le restrizioni sul tipo di dispositivi
Le restrizioni di registrazione predefinite si applicano a tutti gli utenti a cui non sono assegnati restrizioni di registrazione di priorità più alta.  
1. Nel portale di Intune scegliere **Registrazione del dispositivo** e scegliere **Restrizioni registrazione**.
![Schermata dell'area di lavoro delle restrizioni del dispositivo con le restrizioni del tipo di dispositivo predefinite e restrizioni di limite del dispositivo.](media/device-restrictions-set-default.png)
2. In **Restrizioni di registrazione** > **Restrizioni del tipo di dispositivo** selezionare **Predefinite**.
3. In **Tutti gli utenti**selezionare **Piattaforme**. Scegliere **Consenti** o **Blocco** per ogni piattaforma:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Fare clic su **Save**.
4. In **Tutti gli utenti** selezionare **Configurazioni piattaforma** e selezionare le configurazioni seguenti:
  - **Personally Owned** (Proprietà personale): specificare se **consentire** o **bloccare** i dispositivi Android e iOS.
  ![Schermata dell'area di lavoro delle restrizioni del dispositivo con le configurazioni predefinite della piattaforma del dispositivo che visualizza le impostazioni personali configurate.](media/device-restrictions-platform-configurations.png)
  Fare clic su **Save**.

>[!NOTE]
>Anche se si bloccano i dispositivi personali Android per la registrazione, i dispositivi con Android for Work possono ancora essere registrati.

## <a name="set-device-limit-restrictions"></a>Impostare le restrizioni sul limite dei dispositivi
Le restrizioni di registrazione predefinite si applicano a tutti gli utenti a cui non sono assegnati restrizioni di registrazione di priorità più alta.  
1. Nel portale di Intune scegliere **Registrazione del dispositivo** e scegliere **Restrizioni registrazione**.
2. Scegliere **Restrizioni registrazione** > **Restrizione sul limite di dispositivi**.
3. In **Tutti gli utenti**, selezionare **Limite di dispositivi**. Specificare il numero massimo di dispositivi registrati per utente.  
![Schermata del pannello Restrizione sul limite di dispositivi con le restrizioni sul limite del dispositivo.](./media/device-restrictions-limit.png)

  Fare clic su **Save**.
