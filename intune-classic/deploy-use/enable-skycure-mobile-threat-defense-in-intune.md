---
title: Abilitare Skycure Mobile Threat Defense in Intune
description: Abilitare Skycure Mobile Threat Defense nel portale classico di Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9fe3c59e52d9d7732267ecfb28eac3b5c7368ed9
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Abilitare Skycure Mobile Threat Defense in Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per abilitare Skycure Mobile Threat Defense, è necessario avere già configurato il [connettore Intune nella console di Skycure] (/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Per abilitare la connessione a Skycure MTD in Intune

1.  Passare al [portale classico di Intune](https://manage.microsoft.com/) e immettere le proprie credenziali.

2.  Scegliere **Amministrazione** &gt; **Connettori del servizio di terze parti** e quindi scegliere **Stato di Skycure** e abilitare **Sincronizzazione con MTD** usando l'interruttore.

    ![Abilitare l'interruttore Skycure nel portale classico di Intune](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> È necessario configurare le app Skycure prima di creare regole dei criteri di conformità e di configurare l'accesso condizionale. Ciò garantisce che l'app sia pronta e disponibile, in modo che gli utenti finali possano installarla prima di poter ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

In questo modo viene completata la configurazione dell'integrazione di Skycure e Intune nella console di amministrazione di Intune. I passaggi successivi per implementare questa soluzione includono la distribuzione delle app Skycure e la configurazione dei criteri di conformità.

## <a name="next-steps"></a>Passaggi successivi

[Creare i criteri di conformità di Skycure Mobile Threat Defense](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
