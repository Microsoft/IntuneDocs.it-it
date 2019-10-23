---
title: Preparare Intune per la gestione dei dispositivi mobili
titleSuffix: Microsoft Intune
description: Valutare i requisiti tecnici e aziendali prima della migrazione a Microsoft Intune.
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
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe44d2215c3c70de504e9bf95596b274a613f42a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505271"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>Fase 1: Preparare Microsoft Intune per la gestione di dispositivi mobili (MDM)

Prima di affrontare nei dettagli la configurazione di Intune, è importante esaminare i requisiti dell'organizzazione per la gestione dei dispositivi mobili. Potrebbe essere utile eseguire report degli utenti attivi nel provider MDM corrente per identificare i gruppi di utenti critici. Sarà quindi possibile iniziare a rispondere alle domande della sezione [Valutare i requisiti per la gestione dei dispositivi mobili](migration-guide-prepare.md#assess-mdm-requirements).

## <a name="assess-mdm-requirements"></a>Valutare i requisiti per la gestione dei dispositivi mobili

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>Quali tipi di dispositivi è necessario gestire?

- Quali [piattaforme](supported-devices-browsers.md) è necessario supportare?

- I dispositivi che è necessario supportare sono personali o di proprietà dell'azienda?

- Quale tipo di connettività si usa? Wi-Fi, cellulare, VPN?

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>Cosa devono fare gli utenti nei dispositivi gestiti?

- È necessario eseguire il provisioning di app per gli utenti finali?

- Si usano app line-of-business personalizzate? Oppure sono necessarie solo app da store pubblici?

- È necessario eseguire il provisioning di account di posta elettronica?

### <a name="what-kinds-of-users"></a>Quali tipi di utenti?

- Quanti utenti useranno un singolo dispositivo?

- Quali sono i requisiti per le condizioni per l'utilizzo?

  - Assicurarsi di coinvolgere l'ufficio legale con il dovuto anticipo per questo aspetto.
  - Quali interventi di localizzazione sono necessari?

- Gli utenti hanno familiarità con la tecnologia e l'IT in generale?

### <a name="what-is-your-device-security-policy"></a>Quali sono i criteri di sicurezza per i dispositivi esistenti?

- È richiesta la crittografia a livello di dispositivo?

- Quali sono le lunghezze correnti per passcode/PIN dei dispositivi?

- È necessario disabilitare funzionalità dei dispositivi o limitare particolari comportamenti? Con i profili di configurazione dei dispositivi è possibile controllare un'ampia gamma di impostazioni specifiche della piattaforma, ad esempio:
  - Disabilitazione della fotocamera
  - Blocco del dispositivo in modalità applicazione singola<br/>

- Quali tipi di autenticazione è necessario supportare? Se è necessaria l'autenticazione basata su certificati, di quali tipi di certificati è necessario effettuare il provisioning?
  - Intune consente di eseguire il provisioning dei certificati con i profili di accesso alle risorse per i dispositivi registrati.
  - Quale tipo di infrastruttura a chiave pubblica (PKI) è necessario supportare?
  <br></br>
- È necessario il supporto di rete privata virtuale (VPN) a livello di dispositivo o app?

  - Intune consente di eseguire il provisioning di configurazioni VPN per provider VPN di terze parti.
  <br/><br/>
- Sono accettabili eccezioni temporanee per determinati requisiti per evitare tempi di inattività? Oppure i dispositivi con accesso continuo devono essere conformi a tutti i requisiti di sicurezza?

## <a name="next-steps"></a>Passaggi successivi
Vedere questi [case study](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune) relativi a diversi settori per scoprire in che modo le organizzazioni hanno valutato i requisiti per la gestione dei dispositivi mobili.

Vedere la [configurazione di Intune di base](migration-guide-setup.md).
