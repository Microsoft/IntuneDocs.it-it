---
title: Visualizzare l'inventario dei dispositivi di Intune
titleSuffix: Intune on Azure
description: Informazioni su come visualizzare i dispositivi gestiti con Intune ed esaminare l'hardware e le app installate corrispondenti."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/25/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dae92c117bcf8a4a8ff133ed613f9f77ea0c07c2
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-view-intune-device-inventory"></a>Come visualizzare l'inventario dei dispositivi di Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti, include le caratteristiche hardware e le app installate. 

Per visualizzare l'inventario dei dispositivi:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.

Scegliere una delle opzioni seguenti:

- **Panoramica**: ottenere informazioni sui dispositivi registrati e sui sistemi operativi eseguiti da ogni dispositivo.
- **Gestisci**: scegliere **Tutti i dispositivi** per visualizzare un elenco di tutti i dispositivi gestiti.
    Selezionare uno dei dispositivi nell'elenco per aprire il pannello **Panoramica** di <*nome dispositivo*> , in cui è possibile selezionare una delle opzioni seguenti:
    - **Panoramica**: visualizza informazioni generali sul dispositivo tra cui informazioni sul nome e sul proprietario, se si tratta di un dispositivo BYOD, quando è stato archiviato e altre informazioni.
    ![Panoramica sul dispositivo](./media/device-overview.png)
    - **Hardware**: visualizza informazioni più dettagliate sul dispositivo, incluso lo spazio di archiviazione disponibile, il modello, il produttore e altre informazioni.
    ![Inventario hardware dei dispositivi gestiti](./media/hardware-inventory.png)
    - **Applicazioni rilevate**: visualizza un elenco di tutte le app installate nel dispositivo individuate da Intune.
    ![Nodo delle app individuate](./media/detected-applications.png)
    - **Conformità del dispositivo**: visualizza lo stato di conformità di tutti i criteri di conformità assegnati al dispositivo.
    - **Configurazione del dispositivo**: visualizza lo stato di conformità di tutti i criteri di configurazione assegnati al dispositivo.
- **Monitoraggio**: scegliere **Azioni del dispositivo** per visualizzare un elenco delle azioni del dispositivo che sono state eseguite nei dispositivi gestiti e lo stato corrente delle azioni.
- **Installazione** > **TeamViewer Connector**: consente di configurare l'amministrazione remota nei dispositivi usando il software TeamViewer. Per informazioni dettagliate, vedere [Fornire assistenza remota per i dispositivi Android gestiti da Intune](/intune/device-profile-android-teamviewer).


