---
title: Disconnettere l'utente di un dispositivo iOS
titleSuffix: Microsoft Intune
description: Informazioni su come disconnettere l'utente corrente di un dispositivo iOS con Intune."
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ccb072ac24dafca4f9b2fa6e3fb77445578c0f3a
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727909"
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Disconnettere l'utente corrente nei dispositivi iOS gestiti da Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'azione **Disconnetti l'utente corrente** disconnette l'utente corrente di un dispositivo iPad condiviso. 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità non supportata
- iOS: supportate in iOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="how-to-log-out-the-current-user"></a>Come disconnettere l'utente corrente

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS e quindi scegliere l'azione remota del dispositivo **Disconnetti l'utente corrente**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.