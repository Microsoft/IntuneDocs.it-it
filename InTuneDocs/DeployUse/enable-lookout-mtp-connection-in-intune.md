---
title: Abilitare Lookout MTP in Intune | Microsoft Intune
description: Abilitare la protezione dalle minacce per i dispositivi mobili Lookout nella console di amministrazione Intune.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ceaeba74f8671caf4125252fce02fd06752c3fe8
ms.openlocfilehash: 2052aca24baa752bc4fad3bd7a75f8efa109e9e9


---

# Abilitare la connessione a Lookout MTP nella console di amministrazione Intune
Questo argomento illustra come abilitare la connessione a Lookout MTP in Intune. Prima di eseguire questo passaggio, è necessario avere già configurato Intune Connector nella console di Lookout.  Se non è già stato fatto, eseguire i passaggi descritti in [Configurare la sottoscrizione con Lookout MTP](set-up-your-subscription-with-lookout-mtp.md).

Per abilitare la connessione a Lookout MTP in Intune, nella pagina **Amministrazione** nella [console di amministrazione Microsoft Intune](https://manage.microsoft.com) scegliere **Integrazione con un servizio di terze parti**. Scegliere **Stato di Lookout** e abilitare **Sincronizzazione con MTP** usando l'interruttore.

![screenshot della pagina di sincronizzazione con Lookout con l'interruttore per l'abilitazione evidenziato](../media/mtp/lookout-intune-synchronization.png)

È così completa la configurazione dell'integrazione di Lookout e Intune nella console di amministrazione Intune.  I passaggi successivi per implementare questa soluzione includono la distribuzione dell'[app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) e la configurazione dei criteri di [conformità](enable-device-threat-protection-rule-in-compliance-policy.md).

>[!IMPORTANT]
> È **necessario** configurare l'app Lookout for Work prima di creare regole dei criteri di conformità e di configurare l'accesso condizionale. Ciò garantisce che l'app sia pronta e disponibile, in modo che gli utenti finali possano installarla prima di poter ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.
## Passaggi successivi
[Configurare l'app Lookout for Work ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Sep16_HO4-->


