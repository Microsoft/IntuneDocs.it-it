---
title: Impostare restrizioni di registrazione in Intune
titlesuffix: Azure portal
description: Limitare la registrazione dalla piattaforma e impostare un limite di registrazione dei dispositivi in Intune. "
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 463278e4dc9ad677f654754d4710b110b376cc2d
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2017
---
# <a name="set-enrollment-restrictions"></a>Impostare le restrizioni di registrazione

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Gli amministratori di Intune possono determinare quali dispositivi registrare nella gestione con Intune. Usare il portale di Azure per impostare le restrizioni seguenti per la registrazione del dispositivo:

- Numero massimo di dispositivi registrati
- Piattaforme per dispositivi che possono registrare:
  - Android
  - iOS
  - macOS
  - Windows
- Versione della piattaforma del sistema operativo per iOS, Android e Windows (è possibile usare solo versioni di Windows 10, lasciare vuoto se è consentito Windows 8.1)
  - Versione minima
  - Versione massima
- Limitare i dispositivi personali (solo iOS, Android e macOS)

>[!NOTE]
>Le restrizioni di registrazione non sono una funzionalità di sicurezza. I dispositivi compromessi possano dare risultati non previsti. Queste restrizioni sono una barriera di massimo sforzo per gli utenti legittimi.

## <a name="set-device-type-restrictions"></a>Impostare le restrizioni sul tipo di dispositivi
Le restrizioni di registrazione predefinite si applicano a tutti gli utenti e alle registrazioni senza utente.
1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Scegliere **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. In **Restrizioni di registrazione** > **Restrizioni del tipo di dispositivo** selezionare **Predefinite**.
5. In **Tutti gli utenti**selezionare **Piattaforme**. Scegliere **Consenti** o **Blocco** per ogni piattaforma:
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  Fare clic su **Save**.
6. In **Tutti gli utenti** selezionare **Configurazioni piattaforma** e selezionare le configurazioni seguenti. Per ogni piattaforma consentita è possibile configurare le opzioni seguenti:
  - **Versioni**: specificare le versioni del sistema operativo della piattaforma **Min** e **Max** per i dispositivi Android, iOS e Windows. Android supporta il formato di versione maggiore.minore.revisione.build. iOS supporta il formato di versione maggiore.minore.revisione. Windows supporta il formato maggiore.minore.revisione.build solo per Windows 10. Le versioni del sistema operativo non si applicano ai dispositivi Apple registrati in Device Enrollment Program, Apple School Manager o nell'app Apple Configurator. 
  - **Di proprietà personale**: specificare se **consentire** o **bloccare** i dispositivi Android, iOS e macOS.
  ![Schermata dell'area di lavoro delle restrizioni del dispositivo con le configurazioni predefinite della piattaforma del dispositivo che visualizza le impostazioni personali configurate.](media/device-restrictions-platform-configurations.png)
  Fare clic su **Save**.

>[!NOTE]
>Anche se si bloccano i dispositivi personali Android per la registrazione, i dispositivi di proprietà personale con Android for Work possono ancora essere registrati.

## <a name="set-device-limit-restrictions"></a>Impostare le restrizioni sul limite dei dispositivi
Le restrizioni di registrazione predefinite si applicano a tutti gli utenti.
1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Scegliere **Registrazione del dispositivo** > **Restrizioni registrazione**.
4. Nel portale di Azure scegliere **Registrazione del dispositivo** e scegliere **Restrizioni registrazione**.
5. Scegliere **Restrizioni registrazione** > **Restrizione sul limite di dispositivi**.
6. In **Tutti gli utenti**, selezionare **Limite di dispositivi**. Specificare il numero massimo di dispositivi registrati per utente.  
![Schermata del pannello Restrizione sul limite di dispositivi con le restrizioni sul limite del dispositivo.](./media/device-restrictions-limit.png)

  Fare clic su **Save**.
