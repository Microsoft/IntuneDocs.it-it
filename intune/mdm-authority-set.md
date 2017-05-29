---
title: "Impostare l&quot;autorità di gestione dei dispositivi mobili"
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle modalità di impostazione dell&quot;autorità di gestione dei dispositivi mobili in Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.

Le configurazioni possibili sono:

- **Intune autonomo**: gestione solo cloud, che viene configurata tramite il portale di Azure. Include il set completo di funzionalità offerte da Intune. [Impostare l'autorità MDM nella console di Intune](#mdm-authority-set-to-intune).

- **Intune ibrido**: integrazione della soluzione cloud di Intune con System Center Configuration Manager. Intune viene configurato tramite la console di Configuration Manager. [Impostare l'autorità MDM in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestione dei dispositivi mobili per Office 365**: integrazione di Office 365 con la soluzione cloud di Intune. Intune viene configurato dall'interfaccia di amministrazione di Office 365. Include un sottoinsieme delle funzionalità disponibili con Intune autonomo. Impostare l'autorità MDM nell'interfaccia di amministrazione di Office 365.

>[!IMPORTANT]
>Dopo aver impostato l'autorità di gestione dei dispositivi mobili, per modificarla è necessario contattare il [supporto Microsoft](https://docs.microsoft.com/intune-classic/troubleshoot/get-support), quindi scegliere con attenzione.

## <a name="set-mdm-authority-to-intune"></a>Impostare l'autorità MDM su Intune

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
  ![Screenshot del carico di lavoro Troubleshoot (Risoluzione dei problemi) di Intune con il collegamento Seleziona utente](media/set-mdm-auth.png)
2. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Panoramica**.

3. Nel pannello **Inizia a gestire dispositivi** scegliere **Imposta l'autorità MDM su Intune**. Un messaggio indica che l'autorità MDM è stata impostata su Intune.

