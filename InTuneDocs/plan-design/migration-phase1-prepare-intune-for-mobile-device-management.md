---
title: Preparare Intune per la gestione dei dispositivi mobili | Microsoft Docs
description: "Lo scopo di questo articolo è supportare i lettori nella valutazione dei requisiti aziendali e tecnici prima della migrazione a Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8da2695c4c6dc8b45559323b83a4bb77167303b7
ms.openlocfilehash: 2e7bcedebdf777db64a9ec90aa758822634ed435
ms.lasthandoff: 03/28/2017


---

# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>Fase 1: Preparare Intune per la gestione dei dispositivi mobili (MDM)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Prima di affrontare nei dettagli la configurazione di Intune, è importante esaminare i requisiti dell'organizzazione per la gestione dei dispositivi mobili. Può essere utile eseguire report per gli utenti attivi nel provider MDM corrente per identificare i gruppi di utenti cruciali e quindi iniziare a rispondere alle domande presentate nella sezione [Valutare i requisiti per la gestione dei dispositivi mobili](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements).

## <a name="assess-mdm-requirements"></a>Valutare i requisiti per la gestione dei dispositivi mobili

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Quali tipi di dispositivi è necessario gestire?

-   Quali [piattaforme](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers) è necessario supportare?

-   È necessario che i dispositivi supportino l'uso aziendale o BYOD?

-   Quale tipo di connettività viene usata? Wi-Fi, cellulare, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>Cosa devono fare gli utenti nei dispositivi gestiti?

-   È necessario eseguire il provisioning di app per gli utenti finali?

-   Si usano app line-of-business personalizzate? Oppure sono necessarie solo app da store pubblici?

-   È necessario eseguire il provisioning di account di posta elettronica?

### <a name="what-kinds-of-users"></a>Quali tipi di utenti?

-   Quanti utenti useranno un singolo dispositivo?

-   Quali sono i requisiti per le Condizioni per l'utilizzo?

    -   Assicurarsi di coinvolgere l'ufficio legale con il dovuto anticipo per questo aspetto.

    -   Quali interventi di localizzazione sono necessari?

-   Gli utenti hanno familiarità con la tecnologia e l'IT in generale?

### <a name="what-is-your-device-security-policy"></a>Quali sono i criteri di sicurezza per i dispositivi esistenti? 

-   È richiesta la crittografia a livello di dispositivo?

-   Sono previste lunghezze specifiche per passcode/PIN dei dispositivi?

-   È necessario disabilitare funzionalità dei dispositivi o limitare particolari comportamenti?

    -   Con i profili di configurazione dei dispositivi è possibile controllare un'ampia gamma di impostazioni specifiche della piattaforma, ad esempio la disabilitazione della fotocamera e il blocco del dispositivo in modalità applicazione singola.
<br></br>
-   Quali tipi di autenticazione è necessario supportare?

    -   Se è necessaria l'autenticazione basata su certificati, di quali tipi di certificati è necessario eseguire il provisioning?

        -   Intune consente di eseguire il provisioning dei certificati con i profili di accesso alle risorse per i dispositivi registrati.
<br></br>
    -   Quale tipo di infrastruttura a chiave pubblica (PKI) è necessario supportare?
<br></br>
-   È necessario il supporto di rete privata virtuale (VPN) a livello di dispositivo o app?

    -   Intune consente di eseguire il provisioning di configurazioni VPN per provider VPN di terze parti.
<br></br>
-   Sono accettabili eccezioni temporanee per determinati requisiti per evitare tempi di inattività? Oppure i dispositivi con accesso continuo devono essere conformi a tutti i requisiti di sicurezza?

## <a name="additional-information"></a>Informazioni aggiuntive

-   Per esempi più dettagliati, vedere questi [case study](https://customers.microsoft.com/en-US/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) relativi a diversi settori per scoprire in che modo le organizzazioni hanno valutato i requisiti per la gestione dei dispositivi mobili.

## <a name="next-steps"></a>Passaggi successivi

[Fase 1: Configurazione di base](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

