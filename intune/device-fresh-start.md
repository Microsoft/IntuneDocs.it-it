---
title: Ripristinare i dispositivi Windows 10 con Intune
titlesuffix: Azure portal
description: Informazioni su come usare Fresh Start per ripristinare i PC Windows 10 che eseguono Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b59db6f876e1a7353acda63b6b5acdbb5961cb0
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Usare Fresh Start per ripristinare i dispositivi Windows 10 con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Fresh Start** rimuove tutte le app installate in un PC Windows 10 che esegue Creators Update, quindi aggiorna automaticamente il PC alla versione più recente di Windows.
Questa funzionalità può essere usata per rimuovere le app OEM che spesso sono preinstallate in un nuovo PC. È possibile configurare se i dati utente devono essere conservati quando si esegue questa azione del dispositivo. In questo caso le app e le impostazioni vengono rimosse, ma il contenuto della cartella Home degli utenti viene mantenuto.

## <a name="how-to-use-fresh-start"></a>Come usare Fresh Start

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo desktop Windows 10 e quindi scegliere l'azione remota del dispositivo **Fresh Start**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.

