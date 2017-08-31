---
title: Bloccare in remoto i dispositivi gestiti con Intune
titleSuffix: Intune on Azure
description: Informazioni su come usare Intune per bloccare in remoto i dispositivi gestiti."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ab885fa6f693e65295986c182353f4918024281f
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2017
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Bloccare in remoto i dispositivi gestiti con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Blocco remoto** consente di bloccare il dispositivo selezionato. Per sbloccarlo, il proprietario del dispositivo deve usare il passcode. È possibile bloccare solo in modalità remota un dispositivo che dispone di un PIN o di una password impostati.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità supportata in Windows Phone 8.1 e versioni successive
- iOS: funzionalità supportata
- macOS: funzionalità non supportata
- Android: funzionalità supportata

## <a name="how-to-remote-lock-a-device"></a>Come bloccare un dispositivo in remoto

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota del dispositivo **Blocco remoto**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
