---
title: Configurare i criteri di protezione delle app durante una migrazione a Intune | Microsoft Docs
description: "Lo scopo di questo articolo è descrivere i passaggi necessari per configurare i criteri di protezione delle app durante una migrazione a Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 35543604ed68393e859517e32f5186247be001df
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-configure-app-protection-policies-optional"></a>Fase 1: Configurare i criteri di protezione delle app (facoltativo)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

I criteri di protezione delle app consentono di crittografare le app, definire un PIN per l'accesso all'app, impedire l'esecuzione di app in dispositivi jail-broken o rooted e supportano molte altre protezioni. In caso di smarrimento o furto del telefono di un utente, è possibile cancellare selettivamente i dati aziendali da remoto mantenendo intatti i dati personali applicando i criteri di protezione delle app per dispositivi mobili.

I criteri di protezione delle app consentono di imporre la sicurezza a livello di app e non richiedono la registrazione dei dispositivi, quindi possono essere usati nei dispositivi indipendentemente dal fatto che siano registrati in Intune. È anche possibile usarli con dispositivi registrati in un provider MDM di terze parti.

## <a name="app-protection-policies-with-lob-apps"></a>Criteri di protezione delle app con app LOB

I criteri di protezione delle app per dispositivi mobili possono anche essere estesi alle app line-of-business (LOB) tramite [Microsoft Intune App SDK](https://docs.microsoft.com/intune/deploy-use/use-the-sdk-to-enable-apps-for-mobile-application-management) o lo strumento di wrapping delle app di Microsoft Intune per entrambe le piattaforme [iOS](https://www.microsoft.com/en-us/download/details.aspx?id=45218&751be11f-ede8-5a0c-058c-2ee190a24fa6=True) e [Android](https://www.microsoft.com/en-us/download/details.aspx?id=47267).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Utilità dei criteri di protezione delle app durante la migrazione

La migrazione richiede la rimozione dei dispositivi dal provider MDM precedente e la loro registrazione in Intune. È necessario pianificare questo passaggio e invitare gli utenti finali a lasciare il vecchio provider MDM e registrarsi immediatamente in Intune. È tuttavia possibile che, durante la migrazione, alcuni utenti ritardino il processo di registrazione e che i loro dispositivi rimangano non gestiti da alcun provider MDM.

Durante questo periodo l'organizzazione può essere più vulnerabile per il furto dei dispositivi e la perdita dei dati aziendali, se è ancora consentito l'accesso alle risorse aziendali e/o soggetta a una riduzione della produttività degli utenti se l'accesso alle risorse aziendali è bloccato.

Intune può offrire misure di protezione dei dati aziendali durante la migrazione, in modo da poter contare ancora su una copertura per la sicurezza dei dati aziendali anche se non è presente una soluzione di gestione a livello di dispositivi.

Dopo aver disabilitato l'accesso condizionale nel provider MDM precedente, gli utenti possono rimanere produttivi durante il processo di onboarding in Intune.

## <a name="task-list-for-app-protection-policies"></a>Elenco di attività per i criteri di protezione delle app

-   Attività 1: Scoprire [come prepararsi alla configurazione dei criteri di protezione delle app](https://docs.microsoft.com/en-us/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)

-   Attività 2: Scoprire [come creare e distribuire i criteri di protezione delle app](https://docs.microsoft.com/en-us/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

## <a name="next-steps"></a>Passaggi successivi 

[Fase 1: Considerazioni speciali sulla migrazione](https://docs.microsoft.com/intune/plan-design/migration-phase1-special-migration-considerations)

