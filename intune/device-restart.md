---
title: Riavviare i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: È possibile riavviare i dispositivi Windows e iOS con Microsoft Intune nel portale di Azure usando l'azione Riavvia in remoto.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b09a4d528a95d682bf12e6610480b1aa1bcbdb83
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Riavviare i dispositivi in remoto con Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Riavvia** causa il riavvio del dispositivo scelto. Il proprietario del dispositivo non viene avvisato automaticamente del riavvio e può perdere il proprio lavoro.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità supportata in Windows 8.1 e versioni successive
- Windows Phone: funzionalità supportata in Windows Phone 8.1 e versioni successive
- iOS: funzionalità supportata

    > [!Note]  
    > Per eseguire questo comando sono necessari un dispositivo supervisionato e il diritto di accesso **Device Lock** (Blocco dispositivo). Il dispositivo viene riavviato immediatamente. I dispositivi iOS bloccati con passcode non vengono di nuovo aggiunti a una rete Wi-Fi dopo il riavvio. Dopo il riavvio il dispositivo potrebbe non essere in grado di comunicare con il server.
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="restart-a-device"></a>Riavviare un dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** > **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti selezionare un dispositivo, selezionare **Altro** e quindi selezionare l'azione remota del dispositivo **Riavvia**.

## <a name="next-steps"></a>Passaggi successivi

- Per visualizzare lo stato dell'azione del dispositivo **Riavvia**, selezionare **Dispositivi** > **Azioni del dispositivo**.
