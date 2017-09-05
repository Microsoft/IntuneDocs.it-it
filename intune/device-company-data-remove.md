---
title: Rimuovere i dati aziendali dai dispositivi con Intune
titleSuffix: Intune on Azure
description: Informazioni su come rimuovere solo i dati aziendali dai dispositivi gestiti con Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f021e95f-157f-4e8a-9253-1cff03d6ee3e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8074d6e7cc0a061a6708f8c8bfae1a4dfcb6daa3
ms.sourcegitcommit: 10e3ab2aeb79a1fb2243bef2748ccc003fdd4cc7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2017
---
# <a name="remove-company-data-from-intune-managed-devices"></a>Rimuovere i dati aziendali dai dispositivi gestiti con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Rimuovi i dati aziendali** consente di rimuovere solo i dati aziendali dai dispositivi gestiti da Intune. Questa azione non rimuove dal dispositivo i dati personali. Dopo la rimozione, il dispositivo non è più gestito da Intune e non è più possibile accedere alle risorse aziendali.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità supportata (non supportata per i dispositivi Windows aggiunti ad Azure Active Directory)
- Windows Phone: funzionalità supportata
- iOS: funzionalità supportata
- macOS: funzionalità supportata
- Android: funzionalità supportata

## <a name="how-to-remove-company-data"></a>Come rimuovere i dati aziendali

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota del dispositivo **Rimuovi i dati aziendali**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
