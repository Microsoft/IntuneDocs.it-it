---
title: Rimuovere un utente da un dispositivo iOS con Intune
titlesuffix: Azure portal
description: Informazioni su come rimuovere un utente da un dispositivo iOS condiviso con Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f16d42406fa7961cc165adcbd1e7c4c7ab5d78b4
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="remove-a-user-from-a-shared-ios-device-with-intune"></a>Rimuovere un utente da un dispositivo iOS condiviso con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione **Rimuovi utente** elimina l'utente selezionato dalla cache locale in un dispositivo iPad condiviso configurato per la gestione dell'app Classroom iOS con un [profilo di formazione iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità non supportata
- iOS: supportate in iOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="how-to-remove-a-user"></a>Come rimuovere un utente

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS.
6. Nel pannello per il dispositivo scegliere **Utenti**.
7. Nell'elenco, fare clic con il pulsante destro del mouse sull'utente che si vuole rimuovere e quindi scegliere **Rimuovi utente**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
