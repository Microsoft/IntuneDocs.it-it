---
title: Gestire i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Esaminare i dispositivi gestiti con Microsoft Intune, per operazioni come esportare un elenco di dispositivi in formato CSV, visualizzare i dispositivi aggiunti ad Azure Active Directory, esaminare un log delle modifiche delle azioni sul dispositivo, usare TeamViewer Connector per consentire agli amministratori IT di risolvere i problemi dei dispositivi Android in modalità remota e visualizzare tutte le azioni che si possono eseguire nei dispositivi.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: dbed5ee5ca31a85f1ab227916619b0750a1b84e5
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57393987"
---
# <a name="what-is-microsoft-intune-device-management"></a>Informazioni sulla gestione dei dispositivi in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Un amministratore IT deve verificare che i dispositivi gestiti offrano agli utenti le risorse necessarie alle loro attività e al tempo stesso che i dati siano protetti da rischi.

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti e consente di eseguire attività remote su tali dispositivi.

## <a name="get-to-your-devices"></a>Accedere ai dispositivi

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi**. Questa visualizzazione contiene informazioni dettagliate sui singoli dispositivi e come utilizzarli, tra cui:

   - **Panoramica** contiene uno snapshot dei dispositivi registrati e indica quanti dispositivi usano le diverse piattaforme, tra cui Android, iOS e altro.
   - **Tutti i dispositivi** elenca i dispositivi registrati gestiti.

     Usare la funzione **Esporta** per creare un elenco in formato CSV di tutti i dispositivi, in incrementi di 10.000 (Internet Explorer) o 30.000 (Microsoft Edge, Chrome).

     Selezionare un qualsiasi dispositivo per [visualizzare ulteriori dettagli su di esso](device-inventory.md), inclusi dettagli sull'hardware, le app installate, lo stato dei criteri di conformità e altro ancora.

   - **Dispositivi di Azure AD** elenca i dispositivi registrati o aggiunti ad Azure Active Directory (Azure AD). Altre informazioni sulla [gestione dei dispositivi in Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-introduction).
   - **Azioni del dispositivo** include la cronologia delle azioni remote eseguite nei vari dispositivi, tra cui l'azione, il relativo stato, l'autore e l'ora in cui è avvenuta.

     ![Screenshot del monitoraggio delle azioni del dispositivo](./media/monitor-device-actions.png)

   - I **Log di controllo** sono una registrazione delle attività che generano una modifica in Intune. I [Log di controllo](monitor-audit-logs.md) forniscono ulteriori dettagli.
   - **TeamViewer Connector** è un servizio che consente agli utenti dei dispositivi Android gestiti da Intune di ottenere assistenza remota dal proprio amministratore IT. Altre informazioni su [TeamViewer](device-profile-android-teamviewer.md).
   - **Guida e supporto tecnico** collega ai suggerimenti per la risoluzione dei problemi, a informazioni per la richiesta di supporto o alla verifica dello stato di Intune.

## <a name="available-device-actions"></a>Azioni del dispositivo disponibili
Le azioni disponibili dipendono dalla piattaforma del dispositivo e dalla configurazione del dispositivo.

- [Visualizzare l'inventario dei dispositivi](device-inventory.md)
- Eseguire azioni remote sui dispositivi:
    - [Ritira](devices-wipe.md#retire)
    - [Cancellazione](devices-wipe.md#wipe)
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

- In **Tutti i dispositivi** selezionare il dispositivo per cui visualizzare ulteriori dettagli.
- Scegliere **Azioni del dispositivo** per visualizzare lo stato delle azioni eseguite su dispositivi gestiti.
