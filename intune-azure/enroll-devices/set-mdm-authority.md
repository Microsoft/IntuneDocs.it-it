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
translationtype: Human Translation
ms.sourcegitcommit: dc08ba96eeea0ce2aad78e4d6ca0d94e709d885d
ms.openlocfilehash: 6cf7c56924091713f55fe8824fb11e522825b98f
ms.lasthandoff: 04/21/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.

Le configurazioni possibili sono:

- **Intune autonomo**: gestione solo cloud, che viene configurata tramite il portale di Azure. Include il set completo di funzionalità offerte da Intune. [Impostare l'autorità MDM nella console di Intune](#set-mdm-authority-to-Intune).

- **Intune ibrido**: integrazione della soluzione cloud di Intune con System Center Configuration Manager. Intune viene configurato tramite la console di Configuration Manager. [Impostare l'autorità MDM in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestione dei dispositivi mobili per Office 365**: integrazione di Office 365 con la soluzione cloud di Intune. Intune viene configurato dall'interfaccia di amministrazione di Office 365. Include un sottoinsieme delle funzionalità disponibili con Intune autonomo. Impostare l'autorità MDM nell'interfaccia di amministrazione di Office 365.

>[!IMPORTANT]
>Dopo aver impostato l'autorità di gestione dei dispositivi mobili, per modificarla è necessario contattare il [supporto Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune), quindi scegliere con attenzione.

## <a name="set-mdm-authority-to-intune"></a>Impostare l'autorità MDM su Intune

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
  ![Screenshot del carico di lavoro Troubleshoot (Risoluzione dei problemi) di Intune con il collegamento Seleziona utente](media/set-mdm-auth.png)
2. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Panoramica**.

3. Nel pannello **Inizia a gestire dispositivi** scegliere **Imposta l'autorità MDM su Intune**. Un messaggio indica che l'autorità MDM è stata impostata su Intune.

