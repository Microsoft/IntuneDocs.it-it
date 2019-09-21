---
title: Intune nel client PC Intune legacy e Intune in Azure
description: Considerazioni sull'uso di Intune in Azure per gestire i dispositivi di Windows dell'organizzazione.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3891ce150ea740baa3ba18591139c66d78d9d00
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166361"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Intune nella console di Azure e nel client PC Intune legacy

Intune utilizza un'architettura di servizio dell'applicazione SaaS basata su Azure. Azure offre miglioramenti significativi per scalabilità, capacità e prestazioni. Questo scenario garantisce esperienze di amministrazione di Intune migliorate e flussi di lavoro ottimizzati nel portale di Azure. 

Per l'uso di Intune in Azure per gestire i dispositivi di Windows dell'organizzazione, tenere presente i punti seguenti:

## <a name="manage-windows-10-devices-by-using-mdm"></a>Gestire i dispositivi Windows 10 con MDM

È consigliabile usare [Mobile Device Management (MDM) per gestire i dispositivi Windows 10](device-restrictions-windows-10.md) anziché il client PC Intune legacy. La possibilità di gestire i dispositivi Windows 10 tramite MDM è disponibile nel portale di Intune in Azure. La soluzione MDM per Windows 10 offre molte nuove funzionalità per la gestione e la sicurezza, non disponibili tramite il client PC Intune legacy.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>Le funzionalità del client PC legacy sono disponibili solo nella console di Silverlight

I flussi di lavoro di gestione del client PC Intune usano la [console di amministrazione di Intune basata su Silverlight](https://manage.microsoft.com/), con le conseguenze seguenti:

- Per tutte le attività di gestione non di raggruppamento tramite il client PC Intune, è necessario usare la console di Silverlight.
- Per la gestione dei gruppi, è necessario usare il [portale di Intune in Azure](https://portal.azure.com/). Questo requisito è dovuto al fatto che Intune usa ora i gruppi di Azure AD invece dei gruppi di Intune legacy. 

A causa del passaggio ai gruppi di Azure AD, l'applicazione di filtri in base al gruppo nelle visualizzazioni dashboard della console di Silverlight è cambiata leggermente. Per applicare filtri nell'interfaccia aggiornata di Silverlight, seguire questa procedura:

1. Selezionare una visualizzazione.
2. Nella casella **Filtri** immettere il nome del gruppo in base al quale si vuole filtrare i dispositivi e premere INVIO. La visualizzazione elenco verrà così filtrata per mostrare i dispositivi in quel particolare gruppo.

   ![Filtra input elenco a discesa con nessuno selezionato](media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Continuare a gestire i dispositivi Windows 7 con il client PC Intune

Per Windows 7, che non può essere gestito tramite MDM, continueranno a essere supportate solo le funzionalità del client PC Intune esistenti nella console di Silverlight. Valutare la possibilità di eseguire la migrazione alla gestione MDM in seguito all'aggiornamento a Windows 10.

## <a name="mdm-capabilities"></a>Funzionalità MDM

Per un confronto dettagliato tra il client PC e le funzionalità MDM, vedere [Confrontare la gestione dei PC Windows come computer o come dispositivi mobili](pc-management-comparison.md). Gli aggiornamenti per MDM continueranno a introdurre nuove funzionalità di gestione per i dispositivi Windows 10 registrati in MDM, incluse opzioni di valutazione per le app Win 32. Vedere le [Novità](whats-new.md) per informazioni sulle aggiunte nelle versioni più recenti del servizio.

## <a name="switch-from-pc-client-to-mdm"></a>Passare dal client PC a MDM

Per passare dalla gestione dei dispositivi Windows 10 con il client PC Intune alla gestione con MDM, seguire questi passaggi:

1. Nella console di Silverlight, eseguire una **Cancellazione selettiva** per annullare la registrazione del dispositivo dal client PC.
  ![Avviso popup con il pulsante di opzione "cancellazione selettiva del dispositivo" selezionato](media/intune-legacy-pc-client/image02.png)
2. Registrare nuovamente il dispositivo tramite [MDM (e/o l'aggiunta ad Azure AD)](windows-enroll.md).

## <a name="next-steps"></a>Passaggi successivi
[Registrare i dispositivi Windows](windows-enroll.md)
