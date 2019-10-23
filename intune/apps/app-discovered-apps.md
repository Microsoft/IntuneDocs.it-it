---
title: App individuate
titleSuffix: Microsoft Intune
description: Informazioni dettagliate sulle app individuate da Intune in un dispositivo.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07dd262f-13e7-4cb2-9cc2-b755d1c276cf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5cadba411ea4aab74c70583062fcb90eccf19aa
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507476"
---
# <a name="intune-discovered-apps"></a>App individuate da Intune

**App individuate** di Intune è un elenco di app rilevate nei dispositivi registrati in Intune nel tenant dell'utente. Svolge la funzione di inventario software per il tenant. **App individuate** è un report diverso dai report di [installazione delle app](apps-monitor.md). Per i dispositivi personali, Intune non raccoglie mai le informazioni sulle applicazioni non gestite. Nei dispositivi aziendali questo report rileva qualsiasi app, indipendentemente dal fatto che sia un'app gestita. Di seguito è riportata la tabella che mappa il comportamento previsto. In generale il report viene aggiornato ogni 7 giorni dal momento della registrazione (non viene eseguito un aggiornamento settimanale per l'intero tenant). L'unica eccezione a questo periodo di aggiornamento è costituita dalle informazioni sulle applicazioni che vengono raccolte tramite l'estensione di gestione di Intune per le app Win32. Questa raccolta di informazioni avviene ogni 24 ore.

## <a name="monitor-discovered-apps-with-intune"></a>Monitorare le app individuate con Intune

Intune offre un elenco aggregato di app rilevate nei dispositivi registrati in Intune nel tenant dell'utente.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel riquadro **Intune** selezionare **App client** > **App individuate**.

>[!NOTE]
>È possibile esportare l'elenco delle app individuate in un file con estensione csv selezionando **Esporta** nel pannello **App individuate**.
>
>Per le app Win32 individuate, il conteggio aggregato non è attualmente disponibile. Questo tipo di dati può essere visualizzato solo per singolo dispositivo.

Intune offre anche l'elenco delle app individuate per il singolo dispositivo presente nel tenant.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel riquadro Intune selezionare **Dispositivi** > **Tutti i dispositivi**.
3. Selezionare un dispositivo.
4. Per visualizzare le app rilevate per questo dispositivo, selezionare **App individuate** nella sezione **Monitoraggio**.

## <a name="details-of-discovered-apps"></a>Dettagli delle app individuate

L'elenco seguente include il tipo di piattaforma app, le app monitorate per i dispositivi personali, le app monitorate per i dispositivi di proprietà dell'azienda e il ciclo di aggiornamento. Per altre informazioni sui tipi di app supportati da Intune, vedere [Tipi di app in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune).

| Piattaforma | Per i dispositivi di proprietà personale | Per i dispositivi di proprietà dell'azienda | Ciclo di aggiornamento |
|------------------------------------------------------------------------|----------------------------------|--------------------------------------------------|---------------------------------------|
| Nota per le app Windows 10 (app Win32): [Richiede l'estensione di gestione di Intune](intune-management-extension.md) nel dispositivo | Non applicabile | Tutte le app Win32 disponibili nell'elenco Installazione applicazioni | Ogni 24 ore dalla registrazione del dispositivo |
| Windows 10 (app moderne) | Solo app moderne gestite | Tutte le app moderne installate nel dispositivo | Ogni 7 giorni dalla registrazione del dispositivo |
| Windows 8.1 | Solo le app gestite | Solo le app gestite | Ogni 7 giorni dalla registrazione del dispositivo |
| Windows Phone 8 | Solo le app gestite | Solo le app gestite | Ogni 7 giorni dalla registrazione del dispositivo |
| Windows RT | Solo le app gestite | Solo le app gestite | Ogni 7 giorni dalla registrazione del dispositivo |
| iOS | Solo le app gestite | Tutte le app installate nel dispositivo | Ogni 7 giorni dalla registrazione del dispositivo |
| macOS | Tutte le app installate nel dispositivo | Tutte le app installate nel dispositivo | Ogni 7 giorni dalla registrazione del dispositivo |
| Android | Solo le app gestite | Tutte le app installate nel dispositivo | Ogni 7 giorni dalla registrazione del dispositivo |
| Android Enterprise | Solo le app gestite | Solo le app installate nel profilo di lavoro | Ogni 7 giorni dalla registrazione del dispositivo |

> [!NOTE]
> I dispositivi aggiunti ad Azure AD ibrido in Windows 10, come indicato nel carico di lavoro di gestione delle app in Configuration Manager, attualmente non raccolgono l'inventario delle app con l'estensione di gestione di Intune in base alla pianificazione precedente. Per attenuare questo problema, il carico di lavoro di gestione delle app in Configuration Manager deve passare a Intune per consentire l'installazione di IME nel dispositivo. IME è necessario per l'inventario di Win32 e la distribuzione di PowerShell. Si noti che eventuali modifiche o aggiornamenti per questo comportamento vengono annunciati in [in fase di sviluppo](../fundamentals/in-development.md) e/o [novità](../fundamentals/whats-new.md).

Il numero di app individuate potrebbe non corrispondere al conteggio degli stati di installazione delle app. Le possibilità delle incoerenze includono:

- Una modifica di destinazione di un'app gestita installata può far sì che il conteggio delle installazioni nel pannello di stato diminuisca, mentre rimane segnalato nelle app individuate.
- Più istanze di destinazione della stessa app in un tenant comporterà conteggi diversi a causa della potenziale sovrapposizione di utenti o dispositivi. Ogni istanza dell'app includerà nel conteggio utenti sovrapposti, mentre le app individuate avranno conteggi duplicati.
- Le app individuate e lo stato delle app vengono raccolti con intervalli di tempo diversi causando una discrepanza nei conteggi delle app.

## <a name="next-steps"></a>Passaggi successivi

- [Tipi di app in Microsoft Intune](apps-add.md#app-types-in-microsoft-intune)
- [Monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune](apps-monitor.md)
