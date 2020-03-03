---
title: Configurazione di base di Microsoft Intune
description: Questo articolo descrive i passaggi necessari per configurare Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08041a57ab52f395283e57cda596d00ba168aba1
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556483"
---
# <a name="basic-setup"></a>Configurazione di base

Dopo aver valutato l'ambiente, è possibile procedere con la configurazione di Microsoft Intune.

## <a name="external-dependencies-for-an-intune-deployment"></a>Dipendenze esterne per una distribuzione di Intune

### <a name="identity"></a>Identità

Intune richiede Azure Active Directory (AAD) come provider di identità e di raggruppamento utenti. Sono disponibili altre informazioni su:

- [Identity requirements](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview) (Requisiti di identità)

- [Determinare i requisiti di sincronizzazione delle directory](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [Multi-Factor Authentication (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [Planning your user and device groups](users-add.md) (Pianificazione di gruppi di utenti e dispositivi)

- [Come creare gruppi di utenti e dispositivi](groups-get-started.md)

Se l'organizzazione usa già Office 365, Intune deve usare lo stesso ambiente Azure Active Directory.

### <a name="pki-optional"></a>Infrastruttura a chiave pubblica (PKI) facoltativa

Se si prevede di usare l'autenticazione basata su certificati per i profili VPN, Wi-Fi o di posta elettronica con Intune, sarà necessario assicurarsi di disporre di un'[infrastruttura PKI](../protect/certificates-configure.md) supportata, pronta per la creazione e la distribuzione dei profili certificato. Altre informazioni sulla configurazione dei certificati in Intune:

- [Come configurare l'infrastruttura di certificazione per SCEP](/intune/certificates-scep-configure)

- [Come configurare l'infrastruttura di certificazione per PFX](/intune/certficates-pfx-configure).

## <a name="task-list-for-an-intune-setup"></a>Elenco di attività per una configurazione di Intune

### <a name="task-1-intune-subscription"></a>Attività 1: Sottoscrizione a Intune

Prima di poter eseguire la migrazione a Intune, è necessaria una [sottoscrizione a Intune](account-sign-up.md).

### <a name="task-2-assign-intune-user-licenses"></a>Attività 2: Assegnare le licenze utente di Intune

- Informazioni su [come assegnare le licenze utente di Intune](licenses-assign.md).

- Se è stato creato un nuovo tenant di Azure Active Directory, vedere [come creare nuovi utenti o sincronizzare gli utenti da Active Directory locale](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

### <a name="task-3-set-your-mdm-authority-to-intune"></a>Attività 3: Impostare l'autorità MDM su Intune

È consigliabile gestire Intune usando l'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

Impostare l'autorità MDM su **Intune**. L'uso di un'autorità MDM diversa consente a Intune di trasferire la gestione MDM su console di gestione Microsoft alternative. Questi casi sono poco frequenti.

> [!IMPORTANT]
> Se è la prima volta che si trasferisce la gestione dei dispositivi mobili a Intune, è consigliabile impostare l'autorità MDM su Intune.

Vedere [come impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md).

## <a name="next-step"></a>Passaggio successivo

Configurare i [criteri di gestione di dispositivi e app](../migration-guide-configure-policies.md).
