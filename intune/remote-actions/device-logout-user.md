---
title: Disconnettere l'utente di un dispositivo iOS/iPadOS
titleSuffix: Microsoft Intune
description: Informazioni su come disconnettere l'utente corrente di un dispositivo iOS/iPadOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e23f95d169a95244abc8669eb9a19150cff8138
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413698"
---
# <a name="logout-the-current-user-on-intune-managed-iosipados-devices"></a>Disconnettere l'utente corrente nei dispositivi iOS/iPadOS gestiti da Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'azione **Disconnetti l'utente corrente** disconnette l'utente corrente di un dispositivo iPad condiviso. 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità non supportata
- iOS/iPadOS: supportata in iOS/iPadOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="how-to-log-out-the-current-user"></a>Come disconnettere l'utente corrente

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) e selezionare **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS/iPadOS, quindi scegliere l'azione remota del dispositivo **Disconnetti l'utente corrente**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
