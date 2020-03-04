---
title: Bloccare i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Usare l'azione Blocco remoto in Microsoft Intune per bloccare un dispositivo protetto da PIN o password.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a0e3d22e6fe39cd2c0091b0399ea165007fc689
ms.sourcegitcommit: 045ca42cad6f86024af9a38a380535f42a6b4bef
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2020
ms.locfileid: "77781863"
---
# <a name="remotely-lock-devices-with-intune"></a>Bloccare in remoto i dispositivi con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'azione del dispositivo **Blocco remoto** consente di bloccare il dispositivo. Per sbloccarlo, il proprietario del dispositivo immette il passcode. È possibile bloccare in remoto i dispositivi per i quali è impostato un PIN o una password. I dispositivi senza PIN o password non possono essere bloccati in remoto.

## <a name="supported-platforms"></a>Piattaforme supportate

Il **Blocco remoto** è supportato nelle piattaforme seguenti:

- Android
- Dispositivi in modalità tutto schermo di Android Enterprise
- Dispositivi del profilo di lavoro Android Enterprise
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 e versioni successive

La funzionalità **Blocco remoto** non è supportata in:
- Windows 10 Desktop

> [!NOTE]
> Per i dispositivi macOS, impostare un PIN di ripristino di 6 cifre. Quando il dispositivo è bloccato, nella **Panoramica** del dispositivo viene visualizzato il PIN finché non viene inviata un'altra azione del dispositivo.

## <a name="remote-lock-a-device"></a>Blocco remoto un dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selezionare **Dispositivi** > **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi selezionare un dispositivo e quindi l'azione **Blocco remoto**.

## <a name="next-steps"></a>Passaggi successivi

- Per visualizzare lo stato di questa azione, selezionare **Microsoft Intune** > **Dispositivi** > **Azioni del dispositivo**. 
- Per altre azioni utili per la gestione dei dispositivi, vedere [Azioni disponibili](device-management.md).
