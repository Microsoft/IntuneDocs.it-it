---
title: "Configurare i criteri di conformità del dispositivo e di gestione delle app durante una migrazione a Intune"
description: "Lo scopo di questo articolo è descrivere i passaggi necessari per configurare i criteri di conformità del dispositivo e di gestione delle app durante una migrazione a Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5e848dda6643a28141a8f5f1d0bdc01f2bd9d390
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="configure-device-compliance-and-app-management-policies"></a>Configurare i criteri di conformità del dispositivo e di gestione delle app

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

L'obiettivo principale durante la migrazione a Intune è registrare tutti i dispositivi e fare in modo che siano conformi ai criteri corrispondenti. I criteri per i dispositivi non sono utili solo per gestire i dispositivi usati da singoli utenti e di proprietà dell'azienda, ma anche i dispositivi personali (BYOD) e condivisi, come i dispositivi per la modalità a tutto schermo, i computer per punti vendita, i tablet condivisi da più studenti in una classe o i dispositivi senza utente (solo iOS).

Ogni piattaforma di dispositivi può offrire impostazioni diverse, ma i criteri per i dispositivi di Intune supportano ogni piattaforma e offrono le funzionalità seguenti per la gestione dei dispositivi:

-   Regolare il numero di dispositivi registrati da ogni utente.

-   Gestire le impostazioni di dispositivi (ad esempio crittografia a livello di dispositivo, lunghezza delle password, uso della fotocamera).

-   Distribuire app, profili di posta elettronica, profili VPN e così via.

-   Valutare i criteri a livello di dispositivo per i criteri di conformità di sicurezza.

> [!IMPORTANT]
> I criteri di gestione dei dispositivi non vengono assegnati direttamente a singoli dispositivi o utenti, ma vengono invece assegnati a gruppi di utenti. I criteri possono essere applicati direttamente a un gruppo di utenti, e quindi al dispositivo degli utenti, oppure a un gruppo di dispositivi, e quindi ai relativi membri.

## <a name="task-list-for-device-compliance-policies"></a>Elenco di attività per i criteri di conformità del dispositivo

### <a name="task-1-add-device-groups-optional"></a>Attività 1: Aggiungere gruppi di dispositivi (facoltativa)

È possibile creare gruppi di dispositivi, quando è necessario eseguire una serie di attività amministrative in base all'identità del dispositivo, invece che all'identità dell'utente.

I gruppi di dispositivi sono utili per la gestione dei dispositivi senza utenti dedicati, come i dispositivi a tutto schermo, oppure dei dispositivi condivisi da dipendenti che lavorano a turno o assegnati a una posizione specifica.

La configurazione di gruppi di dispositivi prima della registrazione del dispositivo consente di sfruttare le categorie di dispositivi per raggruppare automaticamente i dispositivi al momento della registrazione, in modo che ricevano automaticamente i criteri per i dispositivi del gruppo a cui appartengono. [Introduzione ai gruppi](/intune/groups-get-started).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Attività 2: Usare i profili di accesso alle risorse (certificati per Wi-Fi, VPN e posta elettronica)

I profili di accesso alle risorse eseguono il provisioning dei certificati e delle configurazioni di accesso nei dispositivi registrati.

Come descritto in precedenza nella sezione Valutare i requisiti per la gestione dei dispositivi mobili, se si usa l'autenticazione basata sui certificati, [configurare i certificati](/intune/certificates-configure).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Attività 3: Creare e distribuire profili di configurazione dei dispositivi

È necessario creare un profilo di configurazione del dispositivo per applicare le impostazioni a livello di dispositivo, ad esempio disabilitare la fotocamera o l'accesso allo store per le app, configurare la modalità applicazione singola e la schermata iniziale e così via.

- Informazioni sui [profili di dispositivo](/intune/device-profiles).

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>Importazione diretta di profili di configurazione iOS (facoltativo)

-   **Profili iOS di Apple Configurator (iOS 7.1 e versione successiva):** se la soluzione MDM esistente usa profili di Apple Configurator (file con estensione mobileconfig), Intune può importarli direttamente come criteri di configurazione personalizzati.

-   **Criteri di configurazione delle applicazioni per dispositivi mobili iOS:** se la soluzione MDM esistente usa criteri di configurazione delle applicazioni per dispositivi mobili iOS, Intune può importarli direttamente, a condizione che siano conformi al formato XML specificato da Apple per gli elenchi di proprietà.

- Informazioni su come aggiungere criteri personalizzati per [iOS](/intune/custom-settings-ios)

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Attività 4: Creare e distribuire criteri di conformità del dispositivo (facoltativo)

I criteri di conformità del dispositivo valutano le impostazioni relative alle sicurezza e generano report che indicano se i dispositivi sono conformi o meno agli standard aziendali. I criteri di conformità del dispositivo valutano fattori correlati alla sicurezza, come:

-   Lunghezza PIN

-   Stato jail-broken

-   Versione sistema operativo

Vedere le risorse aggiuntive seguenti per le impostazioni di conformità dei dispositivi:

-   Informazioni sui [criteri di conformità del dispositivo](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune).

-   Informazioni su [come creare criteri di conformità del dispositivo](/intune-classic/deploy-use/create-a-device-compliance-policy-in-microsoft-intune).

### <a name="task-5-publish-and-deploy-apps"></a>Attività 5: Pubblicare e distribuire le app

Quando si usa la soluzione MDM di Intune, è possibile eseguire il provisioning delle app richiedendone l'installazione automatica o rendendole disponibili nel portale aziendale.

-   Informazioni su [come aggiungere le app](/intune-classic/deploy-use/add-apps).

-   Informazioni su [come distribuire le app](/intune-classic/deploy-use/deploy-apps).

### <a name="task-6-enable-device-enrollment"></a>Attività 6: Abilitare la registrazione dei dispositivi

La registrazione rende possibile la gestione eseguendo il provisioning del controllo nel dispositivo. Informazioni su come [prepararsi per la registrazione dei dispositivi di proprietà dell'azienda e personali degli utenti](/intune/device-enrollment).

## <a name="next-steps"></a>Passaggi successivi 

[Configurare i criteri di protezione delle app (facoltativo)](migration-guide-app-protection-policies.md)
