---
title: Gestire i dispositivi con Intune
titleSuffix: Intune on Azure
description: Informazioni su come visualizzare i dispositivi gestiti con Intune ed eseguire diverse operazioni su tali dispositivi."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/31/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0686b3ece3a929cb06a29f4e58046872b70ec926
ms.sourcegitcommit: b8987b8dfb009ea55678d7f640ac5f18a6ab167e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Informazioni sulla gestione dei dispositivi in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Un amministratore IT deve verificare che i dispositivi gestiti offrano agli utenti finali le risorse necessarie alle loro attività e al tempo stesso i dati siano protetti da rischi.

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti e consente di eseguire attività remote su tali dispositivi. Per accedere al carico di lavoro:

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. In **Intune** scegliere **Dispositivi**.
4. È possibile visualizzare informazioni sui dispositivi ed eseguire le azioni remote per il dispositivo come descritto di seguito:
    - **Panoramica**: snapshot dei dispositivi registrati che è possibile gestire.
    - **Tutti i dispositivi**: elenco dei dispositivi registrati che è possibile gestire. Scegliere **Filtro** o **Colonne** per perfezionare le informazioni visualizzate. Selezionare un dispositivo [per visualizzare l'inventario dei dispositivi](device-inventory.md).
    - **Dispositivi di Azure AD**: elenco dei dispositivi registrati o aggiunti con Azure Active Directory (AD). Altre informazioni sulla [gestione dei dispositivi in Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
    - **Azioni del dispositivo**: cronologia delle azioni remote eseguite nei dispositivi, tra cui l'azione, il relativo stato, l'autore e l'ora dell'azione.

    ![Monitorare le azioni del dispositivo](./media/monitor-device-actions.png)

    - **TeamViewer**: il servizio TeamViewer consente agli utenti dei dispositivi Android gestiti da Intune di ottenere assistenza remota dai rispettivi amministratori IT. Altre informazioni su [TeamViewer](device-profile-android-teamviewer.md).

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
