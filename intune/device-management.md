---
title: Gestire i dispositivi con Intune
titleSuffix: Intune on Azure
description: Informazioni su come visualizzare i dispositivi gestiti con Intune ed eseguire diverse operazioni su tali dispositivi."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f066e62e323fffb7c6954d83b2b55ee63f4be46
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>Informazioni sulla gestione dei dispositivi in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti e consente di eseguire attività remote su tali dispositivi. Per accedere al carico di lavoro:

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.

È ora possibile eseguire le azioni seguenti:

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


## <a name="support-for-each-device-action"></a>Supporto per ogni azione del dispositivo

Usare la tabella seguente per un elenco delle piattaforme per dispositivi supportate da ogni azione.

|||||||
|-|-|-|-|-|-|
|Azione del dispositivo|Windows|Windows Phone|iOS|macOS|Android|
|**Rimuovi i dati aziendali**|sì|Sì|Sì|Sì|Sì|
|**Ripristino impostazioni predefinite**|Windows 8.1 e versioni successive (dispositivi gestiti non EAS)|sì|Sì|No|Android for Work non è supportato|
|**Eliminazione**|sì|Sì|Sì|Sì|sì|
|**Blocco remoto**|No|Windows Phone 8.1 e versioni successive|Sì|No|sì|
|**Reimposta passcode**|No|Aggiornamento da Windows Phone 8.1 a Windows 10 Creators non aggiunto a Azure AD, Windows 10 Creators Update e versioni successive - tutti|sì|No|Android precedenti alla versione 7, Android for Work non supportati|
|**Nuovo passcode** (per dispositivi Windows 10)|No|Windows 10 Creators Update e versioni successive (aggiunto ad Azure AD)|No|No|Android for Work non è supportato|
|**Eseguire il bypass del blocco attivazione**|No|No|Solo dispositivi di proprietà dell'azienda|No|No|
|**Modalità di dispositivo perso**|No|No|iOS 9.3 e versioni successive, con supervisione e di proprietà dell'azienda|No|No|
|**Individua il dispositivo**|No|No|iOS 9.3 in modalità dispositivo perso e versioni successive, con supervisione, di proprietà dell'azienda|No|No|
|**Disconnettere utente corrente**|No|No|iOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)|No|No|
|**Riavvia**|Windows 8.1 e versioni successive|Windows Phone 8.1 e versioni successive|No|No|No|
|**Fresh Start**|Windows 10 Creators Update e versioni successive|No|No|No|No|
|**Nuova sessione di assistenza remota**|No|No|No|No|sì|
|**Rimuovi utente**|No|No|iOS 9.3 e versioni successive (solo in dispositivi iPad condivisi)|No|No|

## <a name="next-steps"></a>Passaggi successivi

- Scegliere **Azioni del dispositivo** per visualizzare lo stato delle azioni eseguite su dispositivi gestiti. 
![Monitorare le azioni del dispositivo](./media/monitor-device-actions.png)