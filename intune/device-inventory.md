---
title: Visualizzare l'inventario dei dispositivi di Intune
titlesuffix: Azure portal
description: Informazioni su come visualizzare i dispositivi gestiti con Intune ed esaminare l'hardware e le app installate corrispondenti."
keywords: 
author: arob98
ms.author: angrobe
nmanager: angrobe
ms.date: 11/10/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9cd8c3362fc8e2006b847a4cfc6fda09f2936a6a
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-view-intune-device-inventory"></a>Come visualizzare l'inventario dei dispositivi di Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti, include le caratteristiche hardware e le app installate. 

Per visualizzare l'inventario dei dispositivi:

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.

Scegliere una delle opzioni seguenti:

- **Panoramica**: ottenere informazioni sui dispositivi registrati e sui sistemi operativi eseguiti da ogni dispositivo.
- **Gestisci**: scegliere **Tutti i dispositivi** per visualizzare un elenco di tutti i dispositivi gestiti.
    Selezionare uno dei dispositivi nell'elenco per aprire il pannello **Panoramica** di <*nome dispositivo*> , in cui è possibile selezionare una delle opzioni seguenti:
    - **Panoramica**: visualizza informazioni generali sul dispositivo tra cui informazioni sul nome e sul proprietario, se si tratta di un dispositivo BYOD, quando è stato archiviato e altre informazioni.
    - **Hardware**: visualizza informazioni più dettagliate sul dispositivo, incluso lo spazio di archiviazione disponibile, il modello, il produttore e altre informazioni.
    - **Applicazioni rilevate**: visualizza un elenco di tutte le app installate nel dispositivo individuate da Intune.
    - **Conformità del dispositivo**: visualizza lo stato di conformità di tutti i criteri di conformità assegnati al dispositivo.
    - **Configurazione del dispositivo**: visualizza lo stato di conformità di tutti i criteri di configurazione assegnati al dispositivo.
- **Monitoraggio**: scegliere **Azioni del dispositivo** per visualizzare un elenco delle azioni del dispositivo che sono state eseguite nei dispositivi gestiti e lo stato corrente delle azioni.
- **Installazione** > **TeamViewer Connector**: consente di configurare l'amministrazione remota nei dispositivi usando il software TeamViewer. Per informazioni dettagliate, vedere [Fornire assistenza remota per i dispositivi Android gestiti da Intune](/intune/device-profile-android-teamviewer).

Intune raccoglie l'inventario solo delle app dei dispositivi di proprietà dell'azienda. Le app dei dispositivi personali non sono incluse nell'inventario. Per i PC Windows 10, viene raccolto solo l'inventario delle app moderne nei dispositivi di proprietà dell'azienda. Intune non raccoglie informazioni sulle app Win32 del dispositivo. In base al gestore telefonico utilizzato con i dispositivi, è possibile che non siano raccolti tutti gli elementi dell'inventario.
