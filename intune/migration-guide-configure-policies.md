---
title: Configurare i criteri di conformità del dispositivo e delle app durante una migrazione a Intune
titlesuffix: Microsoft Intune
description: In questo articolo vengono descritte le procedure necessarie per configurare i criteri di conformità del dispositivo e di gestione delle app durante una migrazione a Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1880d580a8719dcf72f54f9c22306bea001bc3b0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55834577"
---
# <a name="configure-device-compliance-and-app-management-policies-when-migrating-to-microsoft-intune"></a>Configurare i criteri di conformità del dispositivo e di gestione delle app durante una migrazione a Microsoft Intune

L'obiettivo principale durante la migrazione a Intune è registrare tutti i dispositivi in Intune e fare in modo che siano conformi ai criteri corrispondenti. I criteri per i dispositivi non sono utili solo per gestire i dispositivi usati da singoli utenti e di proprietà dell'azienda, ma anche i dispositivi personali (BYOD) e condivisi, come i dispositivi per la modalità a tutto schermo, i computer per punti vendita, i tablet condivisi da più studenti in una classe o i dispositivi senza utente (solo iOS).

Ogni piattaforma di dispositivi può offrire impostazioni diverse, ma i criteri per i dispositivi di Intune supportano ogni piattaforma e offrono le funzionalità seguenti per la gestione dei dispositivi:

-   Regolare il numero di dispositivi registrati da ogni utente.

-   Gestire le impostazioni dei dispositivi, ad esempio la crittografia a livello di dispositivo, la lunghezza delle password e l'uso della fotocamera.

-   Distribuire app, profili di posta elettronica, profili VPN e così via.

-   Valutare i criteri a livello di dispositivo per i criteri di conformità di sicurezza.

> [!IMPORTANT]
> I criteri di gestione dei dispositivi non vengono assegnati direttamente a singoli dispositivi o utenti, ma vengono invece assegnati a gruppi di utenti. I criteri possono essere applicati direttamente a un gruppo di utenti, e quindi al dispositivo degli utenti, oppure a un gruppo di dispositivi, e quindi ai relativi membri.

## <a name="task-list-for-device-compliance-policies"></a>Elenco di attività per i criteri di conformità del dispositivo

### <a name="task-1-add-device-groups-optional"></a>Attività 1: Aggiungere gruppi di dispositivi (facoltativa)

È possibile creare gruppi di dispositivi quando è necessario eseguire attività amministrative in base all'identità del dispositivo, invece che all'identità dell'utente.

I gruppi di dispositivi sono utili per la gestione dei dispositivi senza utenti dedicati, come i dispositivi a tutto schermo, i dispositivi condivisi da dipendenti che lavorano a turno o quelli assegnati a una posizione specifica.

La configurazione di gruppi di dispositivi prima della registrazione del dispositivo consente di usare le categorie di dispositivi per raggruppare automaticamente i dispositivi al momento della registrazione. I dispositivi riceveranno così i criteri del rispettivo gruppo automaticamente. [Introduzione ai gruppi](groups-get-started.md).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Attività 2: Usare i profili di accesso alle risorse (certificati per Wi-Fi, VPN e posta elettronica)

I profili di accesso alle risorse forniscono i certificati e le configurazioni di accesso ai dispositivi registrati. Se si usa l'autenticazione basata su certificato, [configurare i certificati](certificates-configure.md).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Attività 3: Creare e distribuire profili di configurazione dei dispositivi

È necessario creare un profilo di configurazione del dispositivo per applicare le impostazioni a livello di dispositivo, ad esempio disabilitare la fotocamera o l'accesso allo store per le app, configurare la modalità applicazione singola e la schermata iniziale e così via. Informazioni sui [profili di dispositivo](device-profiles.md).

####  <a name="directly-import-ios-configuration-profiles-optional"></a>Importare direttamente i profili di configurazione iOS (facoltativo)

-   **Profili iOS di Apple Configurator (iOS 7.1 e versioni successive):** se la soluzione MDM esistente usa profili di Apple Configurator (file con estensione mobileconfig), Intune può importarli direttamente come criteri di configurazione personalizzati.

-   **Criteri di configurazione delle applicazioni per dispositivi mobili iOS:** se la soluzione MDM esistente usa criteri di configurazione delle applicazioni per dispositivi mobili iOS, Intune può importarli direttamente, a condizione che siano conformi al formato XML specificato da Apple per gli elenchi di proprietà.

- Informazioni su come aggiungere criteri personalizzati per [iOS](custom-settings-ios.md).

### <a name="task-4-create-and-deploy-device-compliance-policies-optional"></a>Attività 4: Creare e distribuire criteri di conformità del dispositivo (facoltativa)

I criteri di conformità del dispositivo valutano le impostazioni relative alle sicurezza e generano report che indicano se i dispositivi sono conformi o meno agli standard aziendali. Queste impostazioni includono:

-   Lunghezza PIN

-   Stato jail-broken

-   Versione sistema operativo

Vedere le risorse aggiuntive seguenti per le impostazioni di conformità dei dispositivi:

-   Informazioni sui [criteri di conformità del dispositivo](device-compliance.md).

-   Informazioni su [come creare criteri di conformità del dispositivo](device-compliance-get-started.md).

### <a name="task-5-publish-and-deploy-apps"></a>Attività 5: Pubblicare e distribuire le app

Quando si usa la soluzione MDM di Intune, è possibile fornire le app richiedendone l'installazione automatica o rendendole disponibili nel portale aziendale.

-   [Come aggiungere le app](apps-add.md).

-   [Come distribuire le app](apps-deploy.md).

### <a name="task-6-enable-device-enrollment"></a>Attività 6: Abilitare la registrazione dei dispositivi

La registrazione del dispositivo è necessaria per gestirlo. Informazioni su come [prepararsi per la registrazione dei dispositivi di proprietà dell'azienda e personali degli utenti](device-enrollment.md).

## <a name="next-steps"></a>Passaggi successivi

[Configurare i criteri di protezione delle app (facoltativo)](migration-guide-app-protection-policies.md).
