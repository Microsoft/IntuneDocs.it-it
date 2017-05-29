---
title: Abilitare Lookout MTP in Intune | Microsoft Docs
description: Abilitare la protezione dalle minacce per i dispositivi mobili Lookout nella console di amministrazione Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2a99839ece16c56c7bfaacb295796525903f9464
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="enable-lookout-mtd-connection-in-the-intune-classic-console"></a>Abilitare la connessione a Lookout MTD nella console classica di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per abilitare la connessione a Lookout Mobile Threat Defense (MTD) in Intune, è necessario avere già configurato il connettore Intune nella console di Lookout.  Se questa operazione non è stata ancora eseguita, seguire le istruzioni riportate in [Configurare la sottoscrizione di Lookout Mobile Threat Defense](setup-your-lookout-mtd-subscription.md).

Per abilitare la connessione a Lookout MTP in Intune, nella pagina **Amministrazione** nella [console di amministrazione Microsoft Intune](https://manage.microsoft.com) scegliere **Integrazione con un servizio di terze parti**. Scegliere **Stato di Lookout** e abilitare **Sincronizzazione con MTP** usando l'interruttore.

![screenshot della pagina di sincronizzazione con Lookout con l'interruttore per l'abilitazione evidenziato](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> È **necessario** configurare l'app Lookout for Work prima di creare regole dei criteri di conformità e di configurare l'accesso condizionale. Ciò garantisce che l'app sia pronta e disponibile, in modo che gli utenti finali possano installarla prima di poter ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

È così completa la configurazione dell'integrazione di Lookout e Intune nella console di amministrazione Intune.  I passaggi successivi per implementare questa soluzione includono la distribuzione dei criteri delle [app Lookout for Work](/intune-classic/deploy-use/device-threat-protection-policy).


## <a name="next-steps"></a>Passaggi successivi
[Configurare l'app Lookout for Work](/intune-classic/deploy-use/device-threat-protection-apps)

