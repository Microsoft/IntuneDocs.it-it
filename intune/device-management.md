---
title: Gestire i dispositivi con Microsoft Intune
titleSuffix: ''
description: Visualizzare i dispositivi gestiti con Intune ed eseguire diverse operazioni su tali dispositivi.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 436eeb306bf4ba343ae4d88a824aeed2077a3426
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="what-is-microsoft-intune-device-management"></a>Informazioni sulla gestione dei dispositivi in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Un amministratore IT deve verificare che i dispositivi gestiti offrano agli utenti finali le risorse necessarie alle loro attività e al tempo stesso i dati siano protetti da rischi.

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti e consente di eseguire attività remote su tali dispositivi. Per accedere al carico di lavoro:

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. In **Intune** scegliere **Dispositivi**.
4. È possibile visualizzare informazioni sui dispositivi ed eseguire le azioni remote per il dispositivo come descritto di seguito:
    - **Panoramica**: snapshot dei dispositivi registrati che è possibile gestire.
    - **Tutti i dispositivi**: elenco dei dispositivi registrati che è possibile gestire. Scegliere **Filtro** o **Colonne** per perfezionare le informazioni visualizzate. Selezionare un dispositivo [per visualizzare l'inventario dei dispositivi](device-inventory.md).
    - **Dispositivi di Azure AD**: elenco dei dispositivi registrati o aggiunti con Azure Active Directory (AD). Altre informazioni sulla [gestione dei dispositivi in Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
    - **Azioni del dispositivo**: cronologia delle azioni remote eseguite nei dispositivi, tra cui l'azione, il relativo stato, l'autore e l'ora dell'azione.

        ![Screenshot del monitoraggio delle azioni del dispositivo](./media/monitor-device-actions.png)

    - **Log di controllo**: i log di controllo offrono una registrazione delle attività che generano una modifica in Microsoft Intune. Altre informazioni sui [log di controllo](monitor-audit-logs.md).
    - **TeamViewer Connector**: il servizio TeamViewer consente agli utenti dei dispositivi Android gestiti da Intune di ottenere assistenza remota dai rispettivi amministratori IT. Altre informazioni su [TeamViewer](device-profile-android-teamviewer.md).
    - **Guida e supporto tecnico**: consente di risolvere i problemi, richiedere supporto o visualizzare lo stato di Intune.  
    
## <a name="available-device-actions"></a>Azioni del dispositivo disponibili
Le azioni disponibili dipendono dalla piattaforma del dispositivo e dalla configurazione del dispositivo.

- [Visualizzare l'inventario dei dispositivi](device-inventory.md)
- Eseguire azioni remote per i dispositivi:
    - [Rimuovi i dati aziendali](devices-wipe.md#remove-company-data)
    - [Ripristino impostazioni predefinite](devices-wipe.md#factory-reset)
    - [Blocco remoto](device-remote-lock.md)
    - [Reimposta passcode](device-passcode-reset.md)
    - [Bypass del blocco attivazione](device-activation-lock-bypass.md) (solo iOS)
    - [Fresh Start](device-fresh-start.md) (solo Windows)
    - [Modalità di dispositivo perso](device-lost-mode.md) (solo iOS)
    - [Individua il dispositivo](device-locate.md) (solo iOS)
    - [Riavvia](device-restart.md) (solo Windows)
    - [Reimpostazione del PIN di Windows 10](device-windows-pin-reset.md)
    - [Controllo remoto per Android](device-profile-android-teamviewer.md)
    - [Sincronizzare il dispositivo](device-sync.md)


## <a name="next-steps"></a>Passaggi successivi

- Scegliere **Azioni del dispositivo** per visualizzare lo stato delle azioni eseguite su dispositivi gestiti.
