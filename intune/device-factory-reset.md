---
title: Ripristinare le impostazioni predefinite dei dispositivi con Intune
titleSuffix: Intune on Azure
description: Informazioni su come ripristinare le impostazioni predefinite dei dispositivi gestiti con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8eff9b53-eef2-4c50-8aee-556bc49d69f2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 44f69179f76c8d5eeca1594485ca3a9c1b036188
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2017
---
# <a name="reset-intune-managed-devices-to-factory-settings"></a>Ripristinare le impostazioni predefinite dei dispositivi gestiti da Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**Ripristino delle impostazioni predefinite** consente di ripristinare le impostazioni predefinite del dispositivo. Il dispositivo non è più gestito da Intune e vengono rimossi sia i dati aziendali sia i dati personali. Non è possibile annullare questa azione.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità supportata in Windows 8.1 e versioni successive (dispositivi gestiti non EAS)
- Windows Phone: funzionalità supportata
- iOS: funzionalità supportata
- macOS: funzionalità non supportata
- Android: funzionalità supportata (Android for Work non è supportato)

## <a name="how-to-reset-a-device-to-factory-settings"></a>Come ripristinare le impostazioni predefinite del dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota del dispositivo **Ripristino delle impostazioni predefinite**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.

