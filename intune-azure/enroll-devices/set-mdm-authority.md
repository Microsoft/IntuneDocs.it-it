---
title: "Impostare l&quot;autorità di gestione dei dispositivi mobili"
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle modalità di impostazione dell&quot;autorità di gestione dei dispositivi mobili in Intune. "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 9d7a1a934188f0a40553d3c6b8b567ba8f6af034
ms.lasthandoff: 02/18/2017

---

# <a name="set-the-mobile-device-management-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

L'impostazione dell'autorità di gestione dei dispositivi mobili determina la modalità di gestione dei dispositivi. Le configurazioni possibili sono:

- **Intune autonomo**: gestione solo cloud, che viene configurata tramite il portale di Azure. Include il set completo di funzionalità offerte da Intune.

- **Intune ibrido**: integrazione della soluzione cloud di Intune con System Center Configuration Manager. Intune viene configurato tramite la console di Configuration Manager.

- **Gestione dei dispositivi mobili per Office 365**: integrazione di Office 365 con la soluzione cloud di Intune. Intune viene configurato dall'interfaccia di amministrazione di Office 365. Include un sottoinsieme delle funzionalità disponibili con Intune autonomo.

>[!IMPORTANT]
>Dopo aver impostato l'autorità di gestione dei dispositivi mobili, per modificarla è necessario contattare il [supporto Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune), quindi scegliere con attenzione.

**Per impostare l'autorità di gestione dei dispositivi mobili:**

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi scegliere **Panoramica**.

3. Nel pannello **Inizia a gestire dispositivi** scegliere **Imposta l'autorità MDM su Intune**. Un messaggio indica che l'autorità MDM è stata impostata su Intune.

