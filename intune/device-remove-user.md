---
title: Rimuovere un utente da un dispositivo iOS con Microsoft Intune
titlesuffix: ''
description: Informazioni su come rimuovere un utente da un dispositivo iOS condiviso con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 67a5f60e0877ebc8994ed7d3191a81f51d19c40a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>Rimuovere un utente da un dispositivo iOS condiviso


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'azione **Rimuovi utente** elimina un utente selezionato dalla cache locale di un dispositivo iPad condiviso. Il dispositivo iPad deve essere configurato in modo da gestire l'app Classroom iOS usando un [profilo Education di iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità non supportata
- iOS: supportate in iOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="remove-a-user"></a>Rimuovere un utente

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **Dispositivi**.
4. Nel riquadro **Dispositivi** selezionare **Tutti i dispositivi**.
5. Selezionare un dispositivo iOS dall'elenco dei dispositivi gestiti.
6. Nel riquadro relativo al dispositivo selezionare **Utenti**.
7. Nell'elenco fare clic con il pulsante destro del mouse sull'utente da rimuovere e quindi selezionare **Rimuovi utente**.

## <a name="next-steps"></a>Passaggi successivi

- Per visualizzare lo stato dell'azione **Rimuovi utente**, selezionare **Dispositivi** > **Azioni del dispositivo**.
