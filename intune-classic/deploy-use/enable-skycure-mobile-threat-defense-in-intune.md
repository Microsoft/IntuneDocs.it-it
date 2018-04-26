---
title: Abilitare Skycure Mobile Threat Defense in Intune
description: Abilitare Skycure Mobile Threat Defense nel portale classico di Intune.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: da4197a41798f4e47ff35d2dfab36c5317f92e21
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>Abilitare Skycure Mobile Threat Defense in Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Per abilitare Skycure Mobile Threat Defense, è necessario avere già configurato [Intune Connector nella console di Skycure](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune).

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>Per abilitare la connessione a Skycure MTD in Intune

1.  Passare al [portale classico di Intune](https://manage.microsoft.com/) e immettere le proprie credenziali.

2.  Scegliere **Amministrazione** &gt; **Connettori del servizio di terze parti** e quindi scegliere **Stato di Skycure** e abilitare **Sincronizzazione con MTD** usando l'interruttore.

    ![Abilitare l'interruttore Skycure nel portale classico di Intune](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> È necessario configurare le app Skycure prima di creare regole dei criteri di conformità e di configurare l'accesso condizionale. Ciò garantisce che l'app sia pronta e disponibile, in modo che gli utenti finali possano installarla prima di poter ottenere l'accesso alla posta elettronica o ad altre risorse aziendali.

In questo modo viene completata la configurazione dell'integrazione di Skycure e Intune nella console di amministrazione di Intune. I passaggi successivi per implementare questa soluzione includono la distribuzione delle app Skycure e la configurazione dei criteri di conformità.

## <a name="next-steps"></a>Passaggi successivi

[Creare i criteri di conformità di Skycure Mobile Threat Defense](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
