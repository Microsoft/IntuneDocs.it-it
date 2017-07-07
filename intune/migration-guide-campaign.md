---
title: Avviare una campagna di migrazione a Intune
description: "Lo scopo di questo articolo è fornire indicazioni su come avviare una campagna di migrazione."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f781b029-50f2-46ee-8ff7-03b4a6719e80
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9690572fd5f17fece0de7b533c98bfc52d77615b
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="phase-2-migration-campaign"></a>Fase 2: Campagna di migrazione

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Le organizzazioni devono scegliere l'approccio di migrazione più adatto alle specifiche esigenze e adattare le strategie di implementazione ai requisiti individuati. Nel resto di questa guida verranno forniti gli strumenti necessari per raggiungere l'obiettivo di completare la registrazione dei dispositivi degli utenti in Intune.

## <a name="keys-to-a-successful-migration"></a>Fattori chiave per una migrazione di successo

Questi sono gli elementi chiave di cui tenere conto per la migrazione da un provider MDM di terze parti a Intune:

-   La comunicazione è fondamentale per ridurre al minimo i tempi di inattività e l'insoddisfazione degli utenti finali.

-   Assicurarsi di disporre di istruzioni specifiche e concrete per la migrazione.

-   Prima della registrazione in Intune, è necessario annullare la registrazione di tutti i dispositivi gestiti dal provider MDM esistente.

-   Fornire indicazioni agli utenti finali su come annullare la registrazione dei propri dispositivi dal provider MDM esistente.

-   Adottare un approccio graduale. Iniziare con un piccolo gruppo di utenti pilota e aggiungere in modo incrementale altri gruppi di utenti fino a completare la distribuzione.

-   Monitorare il carico per l'help desk e l'esito della registrazione per ogni ciclo. Includere nella pianificazione il tempo necessario per valutare l'esito dell'operazione per ogni gruppo prima di procedere alla migrazione del gruppo successivo. Per la distribuzione pilota è consigliabile valutare gli aspetti seguenti:

    -   I tassi di riuscita/non riuscita della registrazione rientrano nei parametri previsti.

    -   Produttività degli utenti:

        -   Le risorse aziendali, ad esempio VPN, Wi-Fi, posta elettronica e certificati funzionano.

        -   Le app di cui è stato eseguito il provisioning sono accessibili.

    -   Sicurezza dei dati:

        -   Report di conformità

        -   Protezioni delle app per dispositivi mobili applicate

-   Quando si è soddisfatti della prima fase della migrazione, ripetere il ciclo di migrazione (descritto di seguito in Ciclo di migrazione tipico) per la fase successiva.

-   Ripetere i cicli progressivamente fino a completare la migrazione di tutti gli utenti a Intune.

-   Assicurarsi che il team dell'help desk sia pronto per supportare gli utenti finali per tutta la durata della campagna di migrazione. Eseguire una migrazione volontaria in modo da poter stimare il carico di lavoro per le chiamate al supporto tecnico.

-   Non impostare scadenze per la registrazione fino a quando la popolazione rimanente può essere gestita dall'help desk

> [!IMPORTANT] 
> Non configurare sia Intune che la soluzione MDM di terze parti esistente per applicare i controlli di accesso alle risorse, ad esempio Exchange o SharePoint Online. Inoltre, i dispositivi devono essere registrati solo in un'unica soluzione alla volta.

## <a name="next-steps"></a>Passaggi successivi

[Piano di comunicazione](migration-guide-communication-plan.md)
