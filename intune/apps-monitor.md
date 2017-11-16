---
title: Come monitorare le informazioni sulle app e le assegnazioni
titlesuffix: Azure portal
description: Dopo avere assegnato un'app agli utenti o ai dispositivi, usare queste informazioni per monitorarne lo stato."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3736b6d43f5cd3b6c75097a2ceabebffd75f0caa
ms.sourcegitcommit: e9f9fccccef691333143b7523d1b325ee7d1915a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Come monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune offre alcuni metodi per monitorare le proprietà delle app gestite, nonché il rispettivo stato di assegnazione.

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** + **Intune**.
3. Nel carico di lavoro di **App per dispositivi mobili** scegliere **App** dal gruppo **Gestisci**.
     
    ![Pannello stato di installazione app.](./media/monitor-apps.png)
5. Nel pannello con l'elenco di app scegliere un'app. Verrà visualizzato il pannello <*nome app*> **Stato dell'installazione del dispositivo**.

Il report sullo stato dell'installazione del dispositivo contiene le colonne seguenti:

1.  **Nome dispositivo** Il nome del tipo di dispositivo.
2.  **Nome utente** Il nome dell'utente.
3.   **Piattaforma** Il sistema operativo installato nel dispositivo.
4.  **Versione** Il numero di versione dell'applicazione.
5.   **Stato** Gli stati possibili per le app sono: **Installato**, **Non installato**, **Installazione in sospeso** ed **Errore**.
6. **Dettagli stato** Una descrizione leggibile dello stato dell'app nel dispositivo.
7. **Ultima archiviazione** Quando il dispositivo ha eseguito l'ultimo accesso a Intune.

Eseguire una delle operazioni seguenti per ottenere altre informazioni sulle app e sulle rispettive assegnazioni.

## <a name="general"></a>Generale

- **Panoramica**: contiene una panoramica di base dell'app, con informazioni sullo stato di qualsiasi assegnazione. È possibile scegliere uno dei grafici per aprire il pannello **Stato dell'installazione del dispositivo** o **Stato dell'installazione dell'utente** per ottenere maggiori dettagli.

## <a name="manage"></a>Gestire

- **Proprietà**: permette di visualizzare e modificare le informazioni sull'app selezionata. Per altre informazioni sulle proprietà dell'app, vedere [Come aggiungere un'app a Microsoft Intune](apps-add.md).
- **Assegnazioni**: fornisce informazioni sulle assegnazioni per l'app. Per altre informazioni, vedere [How to assign apps to groups with Microsoft Intune](apps-deploy.md) (Come assegnare app ai gruppi con Microsoft Intune).

## <a name="monitor"></a>Monitoraggio

- **Stato dell'installazione del dispositivo**: fornisce informazioni dettagliate per ogni dispositivo cui è stata assegnata l'app selezionata, tra cui il nome del dispositivo, il sistema operativo, la data e l'ora dell'ultima archiviazione del dispositivo in Intune e lo stato dell'installazione dell'app.
- **Stato dell'installazione dell'utente**: offre informazioni dettagliate per l'utente cui è stata assegnata l'app selezionata, tra cui il numero di installazioni dell'app che l'utente ha su tutti i dispositivi e gli eventuali errori di installazione.