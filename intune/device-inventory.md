---
title: Visualizzare i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: "Visualizzare i dettagli relativi al dispositivo, inclusi i sistemi operativi, spazio di archiviazione, produttore, modello e altro ancora. Ottenere un elenco delle app installate, controllare i criteri di conformità, configurare TeamViewer e altro con Microsoft Intune in Azure. Simile alla visualizzazione dell'inventario dei dispositivi gestiti."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 934ba0853f8bee851f7027580c276a9fff911b7f
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="see-device-details-in-intune"></a>Visualizzare i dettagli del dispositivo in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

La funzionalità **Dispositivi** offre ulteriori dettagli per i dispositivi gestiti, inclusi i relativi componenti hardware e le app installate. 

Questo articolo illustra come visualizzare tutti i dispositivi e le relative proprietà nel portale di Azure.

## <a name="view-your-device-details"></a>Visualizzare i dettagli di un dispositivo

1. Accedere al [portale Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi**. In Dispositivi sono disponibili varie opzioni:

  - **Panoramica**: ottenere informazioni sui dispositivi registrati e sui sistemi operativi eseguiti da ogni dispositivo.
  - **Gestisci**: per visualizzare un elenco di tutti i dispositivi gestiti scegliere **Tutti i dispositivi** o **Dispositivi di Azure AD**.
    Selezionare uno dei dispositivi nell'elenco. Questo passaggio apre <*nome del dispositivo*> **Panoramica** in cui è possibile selezionare le opzioni seguenti:
    - **Panoramica**: visualizza il nome del dispositivo, il proprietario, se si tratta di dispositivo Bring-Your-Own-Device (BYOD), quando è stato archiviato e altri dettagli
    - **Hardware**: visualizza lo spazio di archiviazione disponibile, il modello e il produttore e altri dettagli sul dispositivo
    - **App individuate**: visualizza un elenco di tutte le app installate nel dispositivo individuate da Intune
    - **Conformità del dispositivo**: visualizza lo stato di tutti i criteri di conformità assegnati al dispositivo
    - **Configurazione del dispositivo**: visualizza lo stato di conformità di tutti i criteri di configurazione assegnati al dispositivo
- **Monitoraggio**: scegliere **Azioni del dispositivo** per visualizzare un elenco delle azioni eseguite sui dispositivi gestiti e lo stato corrente delle azioni. **Log di controllo** mostra lo stato di attività diverse.
- **Installazione** > **TeamViewer Connector**: consente di configurare l'amministrazione remota nei dispositivi usando il software TeamViewer. Per informazioni dettagliate, vedere [Fornire assistenza remota per i dispositivi Android gestiti da Intune](device-profile-android-teamviewer.md).

Intune raccoglie un elenco di app solo nei dispositivi di proprietà dell'azienda. Le app non vengono controllate nei dispositivi personali. Per i PC Windows 10, solo le app moderne vengono elencate per i dispositivi di proprietà dell'azienda. Intune non raccoglie informazioni sulle app Win32 nel dispositivo. A seconda dell'uso del gestore telefonico da parte dei dispositivi, è possibile che non vengano raccolte tutte le app.

## <a name="next-steps"></a>Passaggi successivi
Vedere le altre operazioni possibili per [gestire i dispositivi](device-management.md) con Intune.
