---
title: Abilitare Lookout MTP in Intune | Microsoft Intune
description: Abilitare la protezione dalle minacce per i dispositivi mobili Lookout nella console di amministrazione Intune.
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 1bef6c15387309e1b36bc85758ca699acd54fdd0


---

# <a name="enable-lookout-mtp-connection-in-the-intune-admin-console"></a>Abilitare la connessione a Lookout MTP nella console di amministrazione Intune
Questo argomento illustra come abilitare la connessione a Lookout MTP in Intune. Prima di eseguire questo passaggio, è necessario avere già configurato Intune Connector nella console di Lookout.  Se non è già stato fatto, eseguire i passaggi descritti in [Configurare la sottoscrizione con Lookout MTP](set-up-your-subscription-with-lookout-mtp.md).

Per abilitare la connessione a Lookout MTP in Intune, nella pagina **Amministrazione** nella [console di amministrazione Microsoft Intune](https://manage.microsoft.com) scegliere **Integrazione con un servizio di terze parti**. Scegliere **Stato di Lookout** e abilitare **Sincronizzazione con MTP** usando l'interruttore.

![screenshot della pagina di sincronizzazione con Lookout con l'interruttore per l'abilitazione evidenziato](../media/mtp/lookout-intune-synchronization.png)

È così completa la configurazione dell'integrazione di Lookout e Intune nella console di amministrazione Intune.  I passaggi successivi per implementare questa soluzione includono la distribuzione dell'[app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md) e la configurazione dei criteri di [conformità](enable-device-threat-protection-rule-in-compliance-policy.md).

>[!IMPORTANT]
> È **necessario** configurare l'app Lookout for Work prima di creare regole dei criteri di conformità e di configurare l'accesso condizionale. Ciò garantisce che l'app sia pronta e disponibile, in modo che gli utenti finali possano installarla prima di poter ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.
## <a name="next-steps"></a>Passaggi successivi
[Configurare l'app Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Dec16_HO2-->


