---
title: Riavviare i dispositivi in remoto con Intune
titlesuffix: Azure portal
description: Informazioni su come riavviare in remoto i dispositivi con l'azione di riavvio del dispositivo."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7177616d654ca9af0b7e7276a1a4b5453117f36c
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="remotely-restart-devices-with-intune"></a>Riavviare i dispositivi in remoto con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Riavvia** causa il riavvio del dispositivo scelto. Il proprietario del dispositivo non viene avvisato automaticamente del riavvio, pertanto potrebbe perdere il lavoro.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità supportata in Windows 8.1 e versioni successive
- Windows Phone: funzionalità supportata in Windows Phone 8.1 e versioni successive
- iOS: funzionalità supportata

    > [!Note]  
    > Per eseguire questo comando sono necessari un dispositivo supervisionato e il diritto di accesso **Device Lock** (Blocco dispositivo). Il dispositivo viene riavviato immediatamente. I dispositivi iOS bloccati con passcode non si ricollegano a una rete Wi-Fi dopo il riavvio. È possibile che dopo il riavvio non siano in grado di comunicare con il server.
- macOS: funzionalità non supportata
- Android: funzionalità non supportata

## <a name="how-to-restart-a-device"></a>Come riavviare un dispositivo

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota del dispositivo **Riavvia**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
