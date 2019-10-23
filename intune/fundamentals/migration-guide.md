---
title: Guida alla migrazione alla gestione dei dispositivi mobili di Intune
titleSuffix: Microsoft Intune
description: Questa guida presenta in dettaglio i diversi aspetti correlati alla migrazione da un provider MDM di terze parti a Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 492b5c0b75bf47f6fbf784939f18964663556315
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505261"
---
# <a name="intune-migration-guide"></a>Guida alla migrazione a Intune

![Grafica della migrazione all'ambiente MDM di Microsoft Intune](./media/migration-guide/MDM-migration-guide-art.PNG)

La riuscita della migrazione a Microsoft Intune dipende per prima cosa da un piano ben articolato che tenga conto dell'ambiente di gestione di dispositivi mobili (MDM) corrente, degli obiettivi aziendali e dei requisiti tecnici. È anche necessario l'appoggio delle principali parti interessate, ovvero coloro che supporteranno il piano di migrazione e collaboreranno alla sua messa in opera.

Questa guida presenta in dettaglio i diversi aspetti correlati alla migrazione da un provider MDM di terze parti a Intune.

## <a name="whats-included-in-this-guide"></a>Contenuti della guida

La guida suddivide la migrazione in due fasi, che includono entrambe attività, strategie e indicazioni tattiche utili per eseguire passo-passo il processo completo per la migrazione all'ambiente MDM di Intune.

- [Fase 1: Preparare Intune per la gestione di dispositivi mobili](migration-guide-prepare.md)

  - [Valutare i requisiti per la gestione dei dispositivi mobili](migration-guide-prepare.md#assess-mdm-requirements)

  - [Configurazione di base](migration-guide-setup.md)

  - [Configurare i criteri di gestione di dispositivi e app](migration-guide-configure-policies.md)

  - [Configurare i criteri di protezione delle app](../apps/app-protection-policies.md)

  - [Considerazioni speciali sulla migrazione](migration-guide-considerations.md)

- [Fase 2: Campagna di migrazione](migration-guide-campaign.md)

  - [Piano di comunicazione](migration-guide-communication-plan.md)

  - [Promuovere l'adozione da parte degli utenti finali con l'accesso condizionale](migration-guide-drive-adoption.md)

  - [Ciclo di migrazione tipico](migration-guide-cycle.md)
    - [Monitoraggio della migrazione](migration-guide-cycle.md#monitoring-migration)
    - [Attività post-migrazione](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Presupposti

- Il servizio Intune è già stato valutato in un ambiente PoC (modello di verifica) ed è già stata presa la decisione di usarlo come soluzione MDM nell'organizzazione.

- Familiarità con Intune e le relative funzionalità.

## <a name="before-you-begin"></a>Prima di iniziare

È importante tenere presente che la nuova distribuzione di Intune potrebbe essere diversa dalla distribuzione della soluzione MDM precedente. Diversamente dai servizi MDM tradizionali, la soluzione Intune è incentrata sul controllo degli accessi in base all'identità e quindi non richiede un appliance proxy di rete per controllare l'accesso ai dati aziendali da dispositivi mobili all'esterno del perimetro di rete dell'organizzazione. Microsoft offre varie soluzioni per proteggere i servizi dati nel cloud stesso tramite una suite di servizi cloud strettamente integrati, un'offerta nota collettivamente come Enterprise Mobility + Security.

- Rivedere i [metodi comuni per l'uso di Intune](common-scenarios.md).

## <a name="next-steps"></a>Passaggi successivi

[Fase 1: Preparare Intune per la gestione di dispositivi mobili](migration-guide-prepare.md)
