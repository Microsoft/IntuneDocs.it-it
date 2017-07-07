---
title: Guida alla migrazione alla gestione dei dispositivi mobili di Intune
description: "Lo scopo di questa guida è presentare ai clienti i vari dettagli correlati alla migrazione da un provider MDM di terze parti a Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9e86f342413a0f31c51d7a56f862986c433309eb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="intune-migration-guide"></a>Guida alla migrazione a Intune

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

![Grafica della migrazione all'ambiente MDM di Intune](./media/MDM-migration-guide-art.PNG)

Il successo della migrazione a Intune dipende, per iniziare, da un piano ben articolato che tenga conto dell'ambiente di gestione di dispositivi mobili (MDM) corrente, degli obiettivi aziendali e dei requisiti tecnici. È inoltre necessario l'appoggio delle principali parti interessate, ovvero colore che supporteranno il piano di migrazione e collaboreranno alla sua messa in opera.

Lo scopo di questa guida è presentare i vari dettagli correlati alla migrazione da un provider MDM di terze parti a Intune.

## <a name="whats-included-in-this-guide"></a>Contenuti della guida

La guida è suddivisa in due fasi, che includono entrambe attività, strategie e indicazioni tattiche utili per eseguire passo-passo il processo completo per la migrazione all'ambiente MDM di Intune.

-   [Fase 1: Preparare Intune per la gestione dei dispositivi mobili] (migration-guide-prepare.md)

    -   [Valutare i requisiti per la gestione dei dispositivi mobili](migration-guide-prepare.md#assess-mdm-requirements)

    -   [Configurazione di base](migration-guide-setup.md)

    -   [Configurare i criteri di gestione di dispositivi e app](migration-guide-configure-policies.md)

    -   [Configurare i criteri di protezione delle app] (migration-guide-app-protection-policies.md)

    -   [Considerazioni speciali sulla migrazione](migration-guide-considerations.md)

-   [Fase 2: Campagna di migrazione](migration-guide-campaign.md)

    -   [Piano di comunicazione](migration-guide-communication-plan.md)

    -   [Promuovere l'adozione da parte degli utenti finali con l'accesso condizionale](migration-guide-drive-adoption.md)
    
    -   [Ciclo di migrazione tipico](migration-guide-cycle.md)
        -   [Monitoraggio della migrazione](migration-guide-cycle.md#monitoring-migration)
        -   [Attività post-migrazione](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>Presupposti

-   Il servizio Intune è già stato valutato in un ambiente PoC (modello di verifica) ed è già stata presa la decisione di usarlo come soluzione MDM nell'organizzazione.

-   Familiarità con Intune e le relative funzionalità. 

> [!NOTE]
> Per ottenere una maggiore familiarità con Intune prima di procedere con la migrazione, consultare la [Guida alla valutazione di Intune](/intune-classic/understand-explore/sign-up-for-30-day-trial-microsoft-intune).

## <a name="before-you-begin"></a>Prima di iniziare

È importante tenere presente che la nuova distribuzione di Intune potrebbe essere diversa dalla distribuzione della soluzione MDM precedente. Diversamente dai servizi MDM tradizionali, la soluzione Intune è incentrata sul controllo degli accessi in base all'identità e quindi non richiede un appliance proxy di rete per controllare l'accesso ai dati aziendali da dispositivi mobili all'esterno del perimetro di rete dell'organizzazione. Microsoft offre varie soluzioni per proteggere i servizi dati nel cloud stesso tramite una suite di servizi cloud strettamente integrati, un'offerta nota collettivamente come Enterprise Mobility + Security.

-   Rivedere i [metodi comuni per l'uso di Intune](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="next-steps"></a>Passaggi successivi

[Fase 1: Preparare Intune per la gestione dei dispositivi mobili] (migration-guide-prepare.md)
