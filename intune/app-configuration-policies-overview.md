---
title: Criteri di configurazione delle app per Intune
titlesuffix: Microsoft Intune
description: Informazioni su come usare i criteri di configurazione delle app in un dispositivo iOS o Android in Intune.
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 52e0906b58680fa0b5628b2b5fc7445f8135658a
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="app-configuration-policies-for-intune"></a>Criteri di configurazione delle app per Intune

Specificare le impostazioni quando gli utenti eseguono un'app iOS o Android con i criteri di configurazione delle app in Microsoft Intune. Ad esempio, un'app può richiedere agli utenti di specificare quanto segue:

- Un numero di porta personalizzato.
- Impostazioni della lingua.
- Impostazioni di sicurezza.
- Impostazioni di personalizzazione, ad esempio il logo aziendale.

Se gli utenti immettono queste impostazioni in modo non corretto, si può verificare un aumento del carico dell'help desk e un rallentamento nell'adozione di nuove app.

I criteri di configurazione delle app permettono di evitare questi problemi consentendo di assegnare tali impostazioni agli utenti in un criterio prima dell'esecuzione dell'app. Le impostazioni vengono quindi specificate automaticamente e gli utenti non devono eseguire alcuna azione.

Questi criteri non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi assegnata. Le impostazioni dei criteri vengono usate ogni volta che l'app ne esegue la ricerca (in genere alla prima esecuzione).

Sono disponibili due opzioni per l'uso delle configurazioni delle app con Intune:
 - **Dispositivi gestiti**  
   Il dispositivo è gestito da Intune come provider di gestione di dispositivi mobili.
 - **App gestite**  
   Le app vengono gestite senza registrazione del dispositivo.

## <a name="apps-that-support-app-configuration"></a>App che supportano la configurazione delle app

È possibile usare i criteri di configurazione delle app per le app che li supportano. Per supportare la configurazione delle app in Microsoft Intune, le app devono essere scritte in modo da supportare l'uso delle configurazioni delle app. Per maggiori dettagli, consultare il fornitore dell'app.

È possibile preparare un'app line-of-business includendo Intune App SDK nell'app oppure eseguendo il wrapping dell'app dopo che è stata sviluppata. Intune App SDK, disponibile per iOS e Android, consente di abilitare le app per i criteri di protezione delle app di Intune. Mira a ridurre al minimo la quantità di modifiche del codice richieste da uno sviluppatore di app. Per altre informazioni, vedere [Panoramica di Intune App SDK](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Supporto dell'API Graph per la configurazione delle app

È anche possibile usare l'API Graph per eseguire attività di configurazione delle app. Per informazioni dettagliate, vedere il [riferimento dell'API Graph sulla configurazione di destinazione MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Passaggi successivi

### <a name="managed-devices"></a>Dispositivi gestiti

 - Informazioni sull'uso della configurazione delle app con i dispositivi iOS.  Vedere [Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti](app-configuration-policies-use-ios.md).
 - Informazioni sull'uso della configurazione delle app con i dispositivi Android.  Vedere [Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>App gestite

 - Informazioni sull'uso della configurazione delle app con le app gestite. Vedere [Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi](app-configuration-policies-managed-app.md).