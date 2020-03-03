---
title: Configurare Microsoft Intune
description: Requisiti e prerequisiti per iniziare a usare la sottoscrizione di Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/20/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d158503c-1276-422b-ab81-5f66c1cd7e7a
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b12781c55abc3ce7d9e964b0f139fc4c1d1fd69b
ms.sourcegitcommit: 67f926ba83f8a955e16b741a610ad84d6044f8f9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77529363"
---
# <a name="set-up-intune"></a>Configurare Intune

Questa procedura di configurazione consente di abilitare la gestione di dispositivi mobili (MDM) tramite Intune. Prima di poter concedere agli utenti l'accesso alle risorse aziendali o gestire le impostazioni nei dispositivi, i dispositivi devono essere gestiti.

Alcuni passaggi, ad esempio la configurazione di una sottoscrizione di Intune e l'impostazione di un'autorità MDM, sono obbligatori per la maggior parte degli scenari. Altre procedure,ad esempio la configurazione di un dominio personalizzato o l'aggiunta di app, sono facoltative e dipendono dalle esigenze specifiche dell'azienda.

Se attualmente si usa Microsoft Endpoint Configuration Manager per gestire computer e server, è possibile [collegare Configuration Manager al cloud con la co-gestione](https://docs.microsoft.com/configmgr/comanage/overview).

>[!TIP]
>Se si acquistano almeno 150 licenze per Intune con un piano idoneo, è possibile usare *FastTrack Center Benefit*. Con questo servizio, gli specialisti Microsoft collaborano con gli utenti per preparare l'ambiente per Intune. Vedere [FastTrack Center Benefit per Enterprise Mobility + Security (EMS)](https://docs.microsoft.com/enterprise-mobility-security/Solutions/enterprise-mobility-fasttrack-program).

| Passaggi | Stato  |
|---|---|
|   1   | [Configurazioni supportate](supported-devices-browsers.md): informazioni da leggere prima di iniziare. Sono inclusi i requisiti di rete e le configurazioni supportate.|
|   2   |  [Accedere a Intune](account-sign-up.md): eseguire l'accesso alla sottoscrizione di valutazione oppure creare una nuova sottoscrizione di Intune. |
|   3   | [Configurare il nome di dominio](custom-domain-name-configure.md): impostare la registrazione DNS per la connessione al nome di dominio aziendale dell'azienda con Intune. Questo consente di offrire agli utenti un dominio noto per la connessione a Intune e per l'uso delle risorse. |
|   4   | [Aggiungere utenti](users-add.md) e [gruppi](../groups-add.md): aggiungere utenti e gruppi o connettere Active Directory per la sincronizzazione con Intune. Questo passaggio è obbligatorio a meno che i dispositivi non siano dispositivi chiosco "senza utente". I gruppi consentono di assegnare app, impostazioni e altre risorse.|
|   5   | [Assegnare le licenze](../licenses-assign.md): concedere agli utenti l'autorizzazione a usare Intune. Ogni utente o dispositivo senza utente richiede una licenza di Intune per accedere al servizio. |
|   6   | [Impostare l'autorità di gestione di dispositivi mobili](../mdm-authority-set.md): usare gruppi di utenti e dispositivi per semplificare le attività di gestione. I gruppi consentono di assegnare app, impostazioni e altre risorse. |
|   7   | [Aggiungere le app](../apps/apps-add.md): le app possono essere assegnate a gruppi e installate automaticamente o facoltativamente. |
|   8   | [Configurare i dispositivi](../configuration/device-profiles.md): configurare i profili che gestiscono le impostazioni dei dispositivi. I profili dei dispositivi possono preconfigurare le impostazioni per la posta elettronica, la VPN, la connessione Wi-Fi e le funzionalità dei dispositivi. Possono anche limitare i dispositivi per la protezione di dispositivi e dati. |
|   9   |  [Personalizzare il portale aziendale](../apps/company-portal-app.md): personalizzare il Portale aziendale Intune che verrà usato dagli utenti per registrare i dispositivi e installare le app. Queste impostazioni vengono visualizzate sia nell'app Portale aziendale sia nel sito Web Portale aziendale Intune.       |
|  10   | [Abilitare la registrazione dei dispositivi](mdm-authority-set.md): abilitare la gestione in Intune di dispositivi iOS/iPadOS, Windows, Android e Mac impostando l'autorità MDM e abilitando piattaforme specifiche. |
|  11   |  [Configurare i criteri delle app](../apps/app-protection-policy.md): specificare impostazioni specifiche in base ai criteri di protezione delle app in Microsoft Intune. |
