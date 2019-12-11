---
title: Rimuovere un utente da un dispositivo iOS con Microsoft Intune
titleSuffix: ''
description: Informazioni su come rimuovere un utente da un dispositivo iOS condiviso con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 772cdbe203b0489a9b2312a1cc10ea1b3182b35d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73713156"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Rimuovere un utente da un dispositivo iOS condiviso


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'azione **Rimuovi utente** elimina un utente selezionato dalla cache locale di un dispositivo iPad condiviso. Il dispositivo iPad deve essere configurato in modo da gestire l'app Classroom iOS usando un [profilo Education di iOS](../fundamentals/education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità non supportata
- iOS: supportate in iOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="remove-a-user"></a>Rimuovere un utente

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Tutti i dispositivi**.
3. Selezionare un dispositivo iOS dall'elenco dei dispositivi gestiti.
4. Nel riquadro relativo al dispositivo selezionare **Utenti**.
5. Nell'elenco fare clic con il pulsante destro del mouse sull'utente da rimuovere e quindi selezionare **Rimuovi utente**.

## <a name="next-steps"></a>Passaggi successivi

- Per visualizzare lo stato dell'azione **Rimuovi utente**, selezionare **Dispositivi** > **Azioni del dispositivo**.
