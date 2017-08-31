---
title: Gestire i dispositivi con Intune
titleSuffix: Intune on Azure
description: Informazioni su come visualizzare i dispositivi gestiti con Intune ed eseguire diverse operazioni su tali dispositivi."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0fc5337b92ac604a448038f685b27623b6153f9
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Informazioni sulla gestione dei dispositivi in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti e consente di eseguire attività remote su tali dispositivi. Per accedere al carico di lavoro:

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. È ora possibile eseguire le azioni remote elencate sui dispositivi. Le azioni disponibili dipendono dalla piattaforma del dispositivo e dalla configurazione del dispositivo:

## <a name="available-device-actions"></a>Azioni del dispositivo disponibili

- [Visualizzare l'inventario dei dispositivi](device-inventory.md)
- Eseguire azioni remote per i dispositivi:
    - [Rimuovi i dati aziendali](device-company-data-remove.md) 
    - [Ripristino impostazioni predefinite](device-factory-reset.md)
    - [Blocco remoto](device-remote-lock.md)
    - [Reimposta passcode](device-passcode-reset.md)
    - [Eseguire il bypass del blocco attivazione](device-activation-lock-bypass.md)
    - [Fresh Start](device-fresh-start.md)
    - [Modalità di dispositivo perso](device-lost-mode.md)
    - [Individua il dispositivo](device-locate.md)
    - [Riavvia](device-restart.md)
    - [Reimpostazione del PIN di Windows 10](device-windows-pin-reset.md)
    - [Controllo remoto per Android](device-profile-android-teamviewer.md)
    - [Sincronizzare il dispositivo](device-sync.md)


## <a name="next-steps"></a>Passaggi successivi

- Scegliere **Azioni del dispositivo** per visualizzare lo stato delle azioni eseguite su dispositivi gestiti. 
![Monitorare le azioni del dispositivo](./media/monitor-device-actions.png)
