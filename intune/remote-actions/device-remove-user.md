---
title: Rimuovere un utente da un dispositivo iOS/iPadOS con Microsoft Intune
titleSuffix: ''
description: Informazioni su come rimuovere un utente da un dispositivo iOS/iPadOS condiviso con Intune.
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
ms.openlocfilehash: 8b6b2b3492b9edece6b69e4b302741c0443c0a3e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415559"
---
# <a name="remove-a-user-from-a-shared-iosipados-device"></a>Rimuovere un utente da un dispositivo iOS/iPadOS condiviso


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'azione **Rimuovi utente** elimina un utente selezionato dalla cache locale di un dispositivo iPad condiviso. Il dispositivo iPad deve essere configurato in modo da gestire l'app Classroom iOS/iPadOS usando un [profilo Education di iOS/iPadOS](../fundamentals/education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità non supportata
- iOS/iPadOS: supportata in iOS/iPadOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="remove-a-user"></a>Rimuovere un utente

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Tutti i dispositivi**.
3. Selezionare un dispositivo iOS/iPadOS dall'elenco dei dispositivi gestiti.
4. Nel riquadro relativo al dispositivo selezionare **Utenti**.
5. Nell'elenco fare clic con il pulsante destro del mouse sull'utente da rimuovere e quindi selezionare **Rimuovi utente**.

## <a name="next-steps"></a>Passaggi successivi

- Per visualizzare lo stato dell'azione **Rimuovi utente**, selezionare **Dispositivi** > **Azioni del dispositivo**.
