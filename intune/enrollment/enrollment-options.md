---
title: Opzioni di registrazione per i dispositivi gestiti da Microsoft Intune
titleSuffix: ''
description: Elenco delle opzioni di registrazione che gli amministratori possono impostare per i dispositivi gestiti da Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cf4ad6d4-423f-4826-ab8d-6eb7a7cfb559
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7c1ff18a7923d7502e12a9bdb33931089fada6e3
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414234"
---
# <a name="enrollment-options-for-devices-managed-by-intune"></a>Opzioni di registrazione per i dispositivi gestiti da Intune

Gli amministratori di Intune possono configurare la registrazione dei dispositivi per agevolare gli utenti e abilitare le funzionalità di Intune.  Intune include le opzioni di registrazione seguenti:

## <a name="terms-and-conditions"></a>Termini e condizioni

È possibile richiedere agli utenti di accettare i termini e le condizioni dell'azienda prima di poter usare il portale aziendale per registrare i propri dispositivi e accedere a risorse, come app e posta elettronica aziendali. La configurazione dei termini e delle condizioni è facoltativa. Altre informazioni su [termini e condizioni](terms-and-conditions-create.md).

## <a name="enrollment-restrictions"></a>Restrizioni di registrazione

È possibile scegliere di limitare la registrazione di dispositivi tramite:
- Piattaforma per i dispositivi
- Numero di dispositivi per utente
- Blocco dei dispositivi personali

Altre informazioni sulle [restrizioni di registrazione](enrollment-restrictions-set.md).

## <a name="enable-apple-device-enrollment"></a>Abilitare la registrazione dei dispositivi di Apple

Per la registrazione di dispositivi iOS/iPadOS e macOS, è necessario un certificato push MDM. Altre informazioni sui [certificati push MDM](apple-mdm-push-certificate-get.md).

## <a name="corporate-identifiers"></a>Identificatori aziendali

Per identificare i dispositivi di proprietà dell'azienda, è possibile elencare i numeri IMEI (International Mobile Equipment Identifier) e i numeri di serie. Altre informazioni sugli [identificatori aziendali](corporate-identifiers-add.md).
## <a name="multi-factor-authentication"></a>Multi-Factor Authentication

È possibile richiedere agli utenti di usare un metodo di verifica aggiuntivo, ad esempio un telefono, un PIN o informazioni biometriche, quando registrano un dispositivo. Altre informazioni sull'[autenticazione a più fattori](multi-factor-authentication.md).

## <a name="device-enrollment-manager"></a>Manager di registrazione dispositivi
È possibile impostare gli utenti come manager di registrazione dispositivi.  Gli utenti manager di registrazione dispositivi possono registrare un numero elevato di dispositivi mobili con un singolo account utente. L'account del manager di registrazione dispositivi consente di registrare fino a 1.000 dispositivi. Altre informazioni sui [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="device-categories"></a>Categorie di dispositivi

È possibile usare le categorie di dispositivi per aggiungere automaticamente i dispositivi a gruppi basati su categorie definite dall'utente. L'organizzazione in gruppi consente di gestire più facilmente i dispositivi. Altre informazioni sulle [categorie di dispositivi](device-group-mapping.md).
