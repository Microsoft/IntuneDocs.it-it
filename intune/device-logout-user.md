---
title: Disconnettere l'utente di un dispositivo iOS con Intune
titlesuffix: Azure portal
description: Informazioni su come disconnettere l'utente corrente di un dispositivo iOS con Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 702bc46c-1a6f-4689-bd53-3b778a447baa
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5e59eee3660f56fdd967237563e69324b8307e3a
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="logout-the-current-user-on-intune-managed-ios-devices"></a>Disconnettere l'utente corrente nei dispositivi iOS gestiti da Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


L'azione **Disconnetti l'utente corrente** disconnette l'utente corrente in un dispositivo iPad condiviso configurato per la gestione dell'app Classroom iOS con un [profilo Istruzione iOS](education-settings-configure-ios.md). 

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità non supportata
- iOS: supportate in iOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="how-to-logout-the-current-user"></a>Come disconnettere l'utente corrente

1.  Accedere al portale di Azure.
2.  Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3.  Nel pannello **Intune** scegliere **Dispositivi**.
4.  Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5.  Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS e quindi scegliere l'azione remota del dispositivo **Disconnetti l'utente corrente**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
