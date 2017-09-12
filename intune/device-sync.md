---
title: Sincronizzare i dispositivi con Intune
titlesuffix: Azure portal
description: "Informazioni su come sincronizzare i dispositivi con Intune per ottenere i criteri e le azioni più recenti.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3906b567935f026202ccf0e81424a1bb36e376ef
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Sincronizzare i dispositivi con Intune per ottenere i criteri e le azioni più recenti


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Sincronizza** forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità supportata
- Windows Phone: funzionalità supportata
- iOS: funzionalità supportata
- macOS: funzionalità supportata
- Android: funzionalità supportata

## <a name="how-to-sync-a-device"></a>Come sincronizzare un dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota **Sincronizza**.
7. Scegliere **Sì** per confermare l'azione.

## <a name="next-steps"></a>Passaggi successivi

Scegliere **Azioni del dispositivo** per visualizzare lo stato dell'azione di sincronizzazione. 
