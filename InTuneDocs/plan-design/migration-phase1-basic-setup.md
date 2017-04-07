---
title: Configurazione di base di Intune | Microsoft Docs
description: "Lo scopo di questo articolo è descrivere i passaggi necessari per configurare Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: b01b68b7587cb91f24285cdffafeab43296886e6
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-basic-setup"></a>Fase 1: Configurazione di base

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Dopo aver valutato l'ambiente, è possibile procedere con la configurazione di Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dipendenze esterne per una distribuzione di Intune

### <a name="identity"></a>Identità

Intune richiede Azure Active Directory (AAD) come provider di identità e di raggruppamento utenti.

-   Altre informazioni sui [i requisiti di identità](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Altre informazioni sui [requisiti di sincronizzazione delle directory](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Altre informazioni sui [requisiti dell'autenticazione a più fattori](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

-   Altre informazioni sulla [pianificazione dei gruppi di utenti e dispositivi](https://docs.microsoft.com/intune/deploy-use/plan-your-user-and-device-groups).

-   Informazioni su [come creare gruppi di utenti e dispositivi](https://docs.microsoft.com/en-us/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

Se l'organizzazione usa già Office 365, è importante che Intune usi lo stesso ambiente Azure Active Directory.

### <a name="pki-optional"></a>Infrastruttura a chiave pubblica (PKI) facoltativa

Se si prevede di usare l'autenticazione basata su certificati per i profili VPN, Wi-Fi o di posta elettronica con Intune, sarà necessario assicurarsi di disporre di un'[infrastruttura PKI](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles) supportata, pronta per la creazione e la distribuzione dei profili certificato.

Altre informazioni sulla configurazione dei certificati in Intune sono disponibili di seguito.

-   [Come configurare l'infrastruttura di certificazione per SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep).

-   [Come configurare l'infrastruttura di certificazione per PFX](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx).

-   [Come configurare i profili certificato di Intune](file:///C:/intune/deploy-use/https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles).

-   [Come configurare i criteri di accesso alle risorse](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

## <a name="task-list-for-an-intune-setup"></a>Elenco di attività per una configurazione di Intune

### <a name="task-1-intune-subscription"></a>Attività 1: Sottoscrizione a Intune

Prima di poter eseguire la migrazione a Intune, è necessaria una sottoscrizione a Intune.

-   È possibile visitare [questa pagina](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0) in cui sono disponibili istruzioni su come:

    -   Creare una nuova sottoscrizione a Intune collegata a un nuovo tenant AAD.

    -   Collegare la sottoscrizione a Intune accedendo a un tenant AAD esistente.

### <a name="task-2-assign-intune-user-licenses"></a>Attività 2: Assegnare le licenze utente di Intune

-   Informazioni su [come assegnare le licenze utente di Intune](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4).

-   Se è stato creato un nuovo tenant di Azure Active Directory, vedere [come creare nuovi utenti o sincronizzare gli utenti da Active Directory locale](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Attività 3: Impostare l'autorità MDM su Intune

È possibile gestire Intune tramite il portale di Azure o la console di Configuration Manager Current Branch. A meno che non sia necessario integrare Intune con una distribuzione di Configuration Manager Current Branch, è consigliabile gestire Intune dal [portale di Azure](https://portal.azure.com).

Impostare l'autorità MDM su **Intune** per abilitare il portale di Intune di Azure. L'uso di un'autorità MDM diversa consente a Intune di trasferire la gestione MDM su console di gestione Microsoft alternative. Questi casi sono poco frequenti.

> [!IMPORTANT]
> Se è la prima volta che si trasferisce la gestione dei dispositivi mobili a Intune, è consigliabile impostare l'autorità MDM su Intune.

-   Vedere [come impostare l'autorità di gestione dei dispositivi mobili](https://docs.microsoft.com/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority).

## <a name="next-step"></a>Passaggio successivo

[Fase 1: Configurare i criteri di gestione di dispositivi e app](https://docs.microsoft.com/intune/plan-design/migration-phase1-configure-device-and-app-management-policies)

