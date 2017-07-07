---
title: Rimuovere i dati aziendali dai dispositivi con Intune
titleSuffix: Intune on Azure
description: Informazioni su come rimuovere solo i dati aziendali dai dispositivi gestiti con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/27/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 39acd12333e9685f94d23416fb1a61ce93f45476
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Rimuovere i dati aziendali dai dispositivi gestiti con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'opzione **Rimuovi i dati aziendali** consente di rimuovere solo i dati aziendali dai dispositivi gestiti da Intune. Non rimuove dal dispositivo i dati personali. Il dispositivo non verrà più gestito da Intune e non sarà più in grado di accedere alle risorse aziendali (non supportata per i dispositivi Windows associati a Azure Active Directory).

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota del dispositivo **Rimuovi i dati aziendali**.

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
