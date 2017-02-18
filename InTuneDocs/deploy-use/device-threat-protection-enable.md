---
title: Abilitare Lookout MTP in Intune | Documentazione Microsoft
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
translationtype: Human Translation
ms.sourcegitcommit: 53862e49c922b75b414fd5aceec3bba2b10299a6
ms.openlocfilehash: 1297522d0f7b52ebe14eb7b938f3458e7308ae27


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Abilitare la connessione a Lookout MTP nella console di amministrazione Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per abilitare la connessione a Lookout MTP (Malicious Threat Protection) in Intune, è necessario avere già configurato Intune Connector nella console di Lookout.  Se non è già stato fatto, seguire le indicazioni in [Configurare la sottoscrizione con Lookout MTP](set-up-your-subscription-with-lookout-mtp.md).

Per abilitare la connessione a Lookout MTP in Intune, nella pagina **Amministrazione** nella [console di amministrazione Microsoft Intune](https://manage.microsoft.com) scegliere **Integrazione con un servizio di terze parti**. Scegliere **Stato di Lookout** e abilitare **Sincronizzazione con MTP** usando l'interruttore.

![screenshot della pagina di sincronizzazione con Lookout con l'interruttore per l'abilitazione evidenziato](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> È **necessario** configurare l'app Lookout for Work prima di creare regole dei criteri di conformità e di configurare l'accesso condizionale. Ciò garantisce che l'app sia pronta e disponibile, in modo che gli utenti finali possano installarla prima di poter ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

È così completa la configurazione dell'integrazione di Lookout e Intune nella console di amministrazione Intune.  I passaggi successivi per implementare questa soluzione includono la distribuzione dell'[app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) e la configurazione dei criteri di [conformità](enable-device-threat-protection-rule-in-compliance-policy.md).


## <a name="next-steps"></a>Passaggi successivi
[Configurare l'app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Jan17_HO2-->


