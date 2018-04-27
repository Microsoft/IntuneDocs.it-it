---
title: Visualizzare i dettagli del dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare i dettagli relativi al dispositivo, inclusi i sistemi operativi, lo spazio di archiviazione, il produttore e il modello. Ottenere un elenco delle app installate, controllare i criteri di conformità e configurare TeamViewer con Microsoft Intune in Azure. Simile alla visualizzazione dell'inventario dei dispositivi gestiti.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e71c6bdb-d75c-404f-8e38-24a663be81c2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a40b855d1dbaeece1dc91648866285c0a01fb338
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="see-device-details-in-intune"></a>Visualizzare i dettagli del dispositivo in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

La funzionalità **Dispositivi** offre ulteriori dettagli sui dispositivi gestiti, inclusi i componenti hardware e le app installate.

Questo articolo illustra come visualizzare tutti i dispositivi e le relative proprietà nel portale di Azure.

## <a name="view-the-device-details"></a>Visualizzare i dettagli del dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** > **Tutti i dispositivi** > selezionare uno dei dispositivi elencati per aprirne i dettagli:

   - **Panoramica** mostra il nome del dispositivo ed elenca alcune delle sue proprietà chiave, ad esempio se è un dispositivo Bring Your Own Device (BYOD), quando è stato registrato e altro ancora. Selezionare **Altro** anche per:
     - Rimuovere i dati aziendali
     - Eliminare il dispositivo
     - Bloccare in remoto il dispositivo
     - Cancellazione
     - Avviare una sessione di assistenza remota
   - Usare **Proprietà** per assegnare una [categoria del dispositivo creata](device-group-mapping.md) e modificare la proprietà del dispositivo scegliendo dispositivo personale o dispositivo aziendale.
   - **Hardware** include molte informazioni sul dispositivo, come l'ID del dispositivo, il sistema operativo e la versione, lo spazio di archiviazione, il modello e il produttore, le impostazioni di accesso condizionale e altro.
   - **App individuate** visualizza un elenco di tutte le app installate nel dispositivo individuate da Intune con relativa versione. È anche possibile **esportare** l'elenco di app in un file CSV.
   - **Conformità del dispositivo** elenca tutti i criteri di conformità assegnati e indica se il dispositivo è conforme o non conforme.
   - **Configurazione del dispositivo** riporta tutti i criteri di configurazione assegnati al dispositivo e indica se il criterio è riuscito o meno.

Intune raccoglie un elenco di app solo nei dispositivi di proprietà dell'azienda. Le app non vengono controllate nei dispositivi personali. Per i PC Windows 10, solo le app moderne vengono elencate per i dispositivi di proprietà dell'azienda. Intune non raccoglie informazioni sulle app Win32 nel dispositivo. A seconda del gestore telefonico usato dai dispositivi, è possibile che non tutte le app vengano raccolte.

## <a name="next-steps"></a>Passaggi successivi
Vedere le altre operazioni possibili per [gestire i dispositivi](device-management.md) con Intune.