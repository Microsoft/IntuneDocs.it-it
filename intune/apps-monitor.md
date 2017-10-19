---
title: Come monitorare le informazioni sulle app e le assegnazioni
titlesuffix: Azure portal
description: Dopo avere assegnato un'app agli utenti o ai dispositivi, usare queste informazioni per monitorarne lo stato."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fbb1d3e11f8ba3e508a261981e461f35c99ca110
ms.sourcegitcommit: f8672ff73066c2d8bcb78c30f84fda8aa3057a1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/11/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Come monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune offre alcuni metodi per monitorare le proprietà delle app gestite, nonché il rispettivo stato di assegnazione.

1. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
2. Nel pannello dell'elenco delle app scegliere l'app per cui visualizzare le informazioni. Verrà visualizzato il pannello <*Nome app*> **Stato dell'installazione del dispositivo**: pannello ![Stato di installazione dell'app](./media/monitor-apps.png)

Eseguire una delle operazioni seguenti per ottenere altre informazioni sulle app e sulle rispettive assegnazioni.

## <a name="general"></a>Generale

- **Panoramica**: contiene una panoramica di base dell'app, con informazioni sullo stato di qualsiasi assegnazione. È possibile scegliere uno dei grafici per aprire il pannello **Stato dell'installazione del dispositivo** o **Stato dell'installazione dell'utente** per ottenere maggiori dettagli.

## <a name="manage"></a>Gestire

- **Proprietà**: permette di visualizzare e modificare le informazioni sull'app selezionata. Per altre informazioni sulle proprietà dell'app, vedere [Come aggiungere un'app a Microsoft Intune](apps-add.md).
- **Assegnazioni**: fornisce informazioni sulle assegnazioni per l'app. Per altre informazioni, vedere [How to assign apps to groups with Microsoft Intune](apps-deploy.md) (Come assegnare app ai gruppi con Microsoft Intune).

## <a name="monitor"></a>Monitoraggio

- **Stato dell'installazione del dispositivo**: fornisce informazioni dettagliate per ogni dispositivo cui è stata assegnata l'app selezionata, tra cui il nome del dispositivo, il sistema operativo, la data e l'ora dell'ultima archiviazione del dispositivo in Intune e lo stato dell'installazione dell'app.
- **Stato dell'installazione dell'utente**: offre informazioni dettagliate per l'utente cui è stata assegnata l'app selezionata, tra cui il numero di installazioni dell'app che l'utente ha su tutti i dispositivi e gli eventuali errori di installazione.