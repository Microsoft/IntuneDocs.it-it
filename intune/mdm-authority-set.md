---
title: "Impostare l'autorità di gestione dei dispositivi mobili"
titleSuffix: Intune on Azure
description: "Informazioni sulle modalità di impostazione dell'autorità di gestione dei dispositivi mobili in Intune. \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 97dede1ac393a434342f62d1f8488389dcb28d44
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="set-the-mobile-device-management-authority"></a>Impostare l'autorità di gestione dei dispositivi mobili

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.

Le configurazioni possibili sono:

- **Intune autonomo**: gestione solo cloud, che viene configurata tramite il portale di Azure. Include il set completo di funzionalità offerte da Intune. [Impostare l'autorità MDM nella console di Intune](#set-mdm-authority-to-intune).

- **Intune ibrido**: integrazione della soluzione cloud di Intune con System Center Configuration Manager. Intune viene configurato tramite la console di Configuration Manager. [Impostare l'autorità MDM in Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription).

- **Gestione dei dispositivi mobili per Office 365**: integrazione di Office 365 con la soluzione cloud di Intune. Intune viene configurato dall'interfaccia di amministrazione di Office 365. Include un sottoinsieme delle funzionalità disponibili con Intune autonomo. Impostare l'autorità MDM nell'interfaccia di amministrazione di Office 365.

>[!IMPORTANT]    
In Configuration Manager versione 1610 o successiva e Microsoft Intune versione 1705 è possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Per informazioni dettagliate, vedere [Cosa fare se si sceglie l'impostazione dell'autorità MDM sbagliata](/intune-classic/deploy-use/prerequisites-for-enrollment#what-to-do-if-you-choose-the-wrong-mdm-authority-setting).

## <a name="set-mdm-authority-to-intune"></a>Impostare l'autorità MDM su Intune

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
  ![Screenshot del carico di lavoro Troubleshoot (Risoluzione dei problemi) di Intune con il collegamento Seleziona utente](media/set-mdm-auth.png)
2. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Panoramica**.

3. Nel pannello **Inizia a gestire dispositivi** scegliere **Imposta l'autorità MDM su Intune**. Un messaggio indica che l'autorità MDM è stata impostata su Intune.

## <a name="mobile-device-cleanup-after-mdm-certificate-expiration"></a>Pulizia dei dispositivi mobili dopo la scadenza del certificato MDM

Il certificato MDM viene rinnovato automaticamente quando i dispositivi mobili comunicano con il servizio Intune. In caso di cancellazione dei dispositivi mobili o se questi non riescono a comunicare con il servizio Intune per un determinato periodo di tempo, il certificato MDM non verrà rinnovato. Il dispositivo viene rimosso dal portale di Azure 180 giorni dopo la scadenza del certificato MDM.
