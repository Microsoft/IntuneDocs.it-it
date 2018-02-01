---
title: Bloccare in remoto i dispositivi gestiti con Intune
titlesuffix: Azure portal
description: Informazioni su come usare Intune per bloccare in remoto i dispositivi gestiti."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ecd7fa03b35e91b5a77906858fb251348796704d
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="remotely-lock-managed-devices-with-intune"></a>Bloccare in remoto i dispositivi gestiti con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Blocco remoto** consente di bloccare il dispositivo selezionato. Per sbloccarlo, il proprietario del dispositivo deve usare il passcode. È possibile bloccare solo in modalità remota un dispositivo che dispone di un PIN o di una password impostati.

## <a name="supported-platforms"></a>Piattaforme supportate

Il blocco remoto è supportato nelle piattaforme seguenti:

|Piattaforma|Stato del supporto|
|---|---|
|Android|Sì|
|iOS|Sì|
|macOS|Sì|
|Windows 10|Sì|
|Windows 10 Mobile|Sì|
|Windows Phone|Sì, per Windows Phone 8.1 e versioni successive|

> [!NOTE]  
> Per i dispositivi macOS, impostare un PIN di ripristino di 6 cifre. Quando il dispositivo è bloccato, il pannello **Device overview** (Panoramica dispositivo) visualizza il PIN fino a quando non viene inviata un'altra azione del dispositivo.

## <a name="how-to-remote-lock-a-device"></a>Come bloccare un dispositivo in remoto

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota del dispositivo **Blocco remoto**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
