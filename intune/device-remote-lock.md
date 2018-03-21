---
title: Bloccare i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Usare l'azione Blocco remoto in Microsoft Intune per bloccare un dispositivo protetto da PIN o password.
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 59a55de54a5a18f5fd1080fefa15c0e4801a1456
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2018
---
# <a name="remotely-lock-devices-with-intune"></a>Bloccare in remoto i dispositivi con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Blocco remoto** consente di bloccare il dispositivo. Per sbloccarlo, il proprietario del dispositivo immette il passcode. È possibile bloccare in remoto i dispositivi per i quali è impostato un PIN o una password. I dispositivi senza PIN o passcode non possono essere bloccati in remoto.

## <a name="supported-platforms"></a>Piattaforme supportate

Il blocco remoto è supportato nelle piattaforme seguenti:

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 e versioni successive

Questa funzionalità **non** è supportata per:
- Windows 10 Desktop

> [!NOTE]
> Per i dispositivi macOS, impostare un PIN di ripristino di 6 cifre. Quando il dispositivo è bloccato, nella **Panoramica** del dispositivo viene visualizzato il PIN fino a quando non viene inviata un'altra azione del dispositivo.

## <a name="remote-lock-a-device"></a>Blocco remoto un dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi selezionare un dispositivo e quindi selezionare l'azione **Blocco remoto**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato di questa azione, aprire **Azioni del dispositivo** (Microsoft Intune > Dispositivi). Vedere [Azioni disponibili](device-management.md) per altre azioni utili per la gestione dei dispositivi.