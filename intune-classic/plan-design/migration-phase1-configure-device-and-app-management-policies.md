---
title: "Configurare i criteri di conformità del dispositivo e di gestione delle app durante una migrazione a Intune | Microsoft Docs"
description: "Lo scopo di questo articolo è descrivere i passaggi necessari per configurare i criteri di conformità del dispositivo e di gestione delle app durante una migrazione a Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0062d08e-e5b3-4f73-8b64-5ad95adbe945
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 50a8929ef31e0a322e9460f82af3ed821ade69cf
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-configure-device-compliance-and-app-management-policies"></a>Fase 1: Configurare i criteri di conformità del dispositivo e di gestione delle app

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

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

Il [portale classico di Intune](https://manage.microsoft.com/) offre la possibilità di creare gruppi di dispositivi, quando è necessario eseguire una serie di attività amministrative in base all'identità del dispositivo, invece che all'identità dell'utente.

I gruppi di dispositivi sono utili per la gestione dei dispositivi senza utenti dedicati, come i dispositivi a tutto schermo, oppure dei dispositivi condivisi da dipendenti che lavorano a turno o assegnati a una posizione specifica.

La configurazione di gruppi di dispositivi prima della registrazione del dispositivo consente di sfruttare le categorie di dispositivi per raggruppare automaticamente i dispositivi al momento della registrazione, in modo che ricevano automaticamente i criteri per i dispositivi del gruppo a cui appartengono.

-   Informazioni su [come aggiungere gruppi di dispositivi](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5).

-   Informazioni su [come configurare le categorie di dispositivi](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune).

### <a name="task-2-use-resource-access-profiles-wi-fi-vpn-and-email-certificates"></a>Attività 2: Usare i profili di accesso alle risorse (certificati per Wi-Fi, VPN e posta elettronica)

I profili di accesso alle risorse eseguono il provisioning dei certificati e delle configurazioni di accesso nei dispositivi registrati.

Come illustrato in precedenza nella sezione relativa alla valutazione dei requisiti per la gestione dei dispositivi mobili, è necessario avere a disposizione un'[infrastruttura a chiave pubblica (PKI)](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles) per distribuire i certificati per VPN, Wi-Fi e posta elettronica, se si usa l'autenticazione basata su certificati.

#### <a name="direct-import-of-resource-access-profiles-optional"></a>Importazione diretta dei profili di accesso alle risorse (facoltativo)

Se la soluzione MDM esistente offre un meccanismo per esportare i profili di posta elettronica, Wi-Fi e VPN in formato XML, potrebbe essere possibile sfruttare il file XML e importarlo semplicemente in Intune tramite URI OMA per creare profili personalizzati per i dispositivi iOS, Android e Windows.

-   Informazioni su come aggiungere criteri personalizzati per dispositivi [iOS](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).

### <a name="task-3-create-and-deploy-device-configuration-profiles"></a>Attività 3: Creare e distribuire profili di configurazione dei dispositivi

È necessario creare un profilo di configurazione del dispositivo per applicare le impostazioni a livello di dispositivo, ad esempio disabilitare la fotocamera o l'accesso allo store per le app, configurare la modalità applicazione singola e la schermata iniziale e così via.

- Informazioni sui [profili di configurazione dei dispositivi](https://docs.microsoft.com/intune/device-profile-create).

####  <a name="direct-import-of-ios-configuration-profiles-optional"></a>Importazione diretta di profili di configurazione iOS (facoltativo)

-   **Profili iOS di Apple Configurator (iOS 7.1 e versione successiva):** se la soluzione MDM esistente usa profili di Apple Configurator (file con estensione mobileconfig), Intune può importarli direttamente come criteri di configurazione personalizzati.

-   **Criteri di configurazione delle applicazioni per dispositivi mobili iOS:** se la soluzione MDM esistente usa criteri di configurazione delle applicazioni per dispositivi mobili iOS, Intune può importarli direttamente, a condizione che siano conformi al formato XML specificato da Apple per gli elenchi di proprietà.

- Informazioni su come aggiungere criteri personalizzati per [iOS](/intune-classic/deploy-use/ios-policy-settings-in-microsoft-intune#custom-policy-settings)

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

La registrazione rende possibile la gestione eseguendo il provisioning del controllo nel dispositivo.

-   Informazioni su come [prepararsi per la registrazione dei dispositivi di proprietà dell'azienda e personali degli utenti](/intune-classic/deploy-use/enroll-devices-in-microsoft-intune).

-   Informazioni su [come registrare i dispositivi di proprietà dell'azienda](/intune-classic/deploy-use/manage-corporate-owned-devices).

Se è necessario registrare dispositivi condivisi o senza utenti, è possibile usare un account manager di registrazione dispositivi.

## <a name="next-steps"></a>Passaggi successivi 

[Fase 1: Configurare i criteri di protezione delle app (facoltativo)

