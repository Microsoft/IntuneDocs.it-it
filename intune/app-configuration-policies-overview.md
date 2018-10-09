---
title: Criteri di configurazione delle app per Microsoft Intune
titlesuffix: ''
description: Informazioni su come usare i criteri di configurazione delle app in un dispositivo iOS o Android in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 834B4557-80A9-48C0-A72C-C98F6AF79708
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 66258a79e0a73a60dc7e4c1b0c67ab4761bc37ec
ms.sourcegitcommit: 28262384ec94e43970cc7a33e5d9063972bdf468
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2018
ms.locfileid: "48799541"
---
# <a name="app-configuration-policies-for-microsoft-intune"></a>Criteri di configurazione delle app per Microsoft Intune

Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni di configurazione per un'app iOS o Android. Queste impostazioni di configurazione consentono di personalizzare un'app. Questi criteri di configurazione non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi assegnata. Le impostazioni dei criteri di configurazione vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

È possibile assegnare un criterio di configurazione dell'app a un gruppo di utenti e dispositivi tramite una combinazione di assegnazioni di inclusione ed esclusione. Dopo aver aggiunto un criterio di configurazione dell'app, è possibile impostare le assegnazioni per i criteri di configurazione dell'app. Quando si impostano le assegnazioni per i criteri, è possibile scegliere di includere ed escludere i gruppi di utenti ai quali vengono applicati i criteri. Quando si sceglie di includere uno o più gruppi, è possibile selezionare i gruppi specifici da includere o selezionare i gruppi predefiniti. I gruppi predefiniti includono **Tutti gli utenti**, **Tutti i dispositivi** e **Tutti gli utenti + Tutti i dispositivi**.

Ad esempio, un'app potrebbe richiedere di specificare i dettagli seguenti:

- Un numero di porta personalizzato
- Impostazione della lingua
- Impostazioni di sicurezza
- Impostazioni di personalizzazione, ad esempio il logo aziendale

Se gli utenti immettono queste impostazioni in modo non corretto, si può verificare un aumento del carico dell'help desk e un rallentamento nell'adozione di nuove app.

I criteri di configurazione delle app permettono di evitare questi problemi consentendo di assegnare tali impostazioni agli utenti in un criterio prima dell'esecuzione dell'app. Le impostazioni vengono quindi specificate automaticamente e gli utenti non devono eseguire alcuna azione.

Le impostazioni di configurazione vengono usate ogni volta che l'app controlla se sono presenti. In genere, un'app controlla se sono presenti impostazioni di configurazione quando viene eseguita per la prima volta dall'utente.

Sono disponibili due opzioni per l'uso delle configurazioni delle app con Intune:
 - **Dispositivi gestiti**: il dispositivo è gestito da Intune come provider di gestione di dispositivi mobili (MDM).
 - **App gestite**: le app vengono gestite senza registrazione del dispositivo.

## <a name="apps-that-support-app-configuration"></a>App che supportano la configurazione delle app

È possibile usare i criteri di configurazione delle app per le app che li supportano. Per supportare la configurazione delle app in Microsoft Intune, le app devono essere scritte in modo da supportare l'uso delle configurazioni delle app. Per maggiori dettagli, consultare il fornitore dell'app.

È possibile preparare un'app line-of-business includendo Intune App SDK nell'app oppure eseguendo il wrapping dell'app dopo che è stata sviluppata. Intune App SDK, disponibile per iOS e Android, consente di abilitare le app per i criteri di configurazione delle app di Intune. Mira a ridurre al minimo la quantità di modifiche del codice richieste da uno sviluppatore di app. Per altre informazioni, vedere [Panoramica di Intune App SDK](app-sdk.md).

## <a name="graph-api-support-for-app-configuration"></a>Supporto dell'API Graph per la configurazione delle app

È anche possibile usare l'API Graph per eseguire attività di configurazione delle app. Per informazioni dettagliate, vedere il [riferimento dell'API Graph sulla configurazione di destinazione MAM](https://graph.microsoft.io/docs/api-reference/beta/api/intune_mam_targetedmanagedappconfiguration_create).

## <a name="next-steps"></a>Passaggi successivi

### <a name="managed-devices"></a>Dispositivi gestiti

 - Informazioni sull'uso della configurazione delle app con i dispositivi iOS.  Vedere [Aggiungere criteri di configurazione delle app per i dispositivi iOS gestiti](app-configuration-policies-use-ios.md).
 - Informazioni sull'uso della configurazione delle app con i dispositivi Android.  Vedere [Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti](app-configuration-policies-use-android.md).

### <a name="managed-apps"></a>App gestite

 - Informazioni sull'uso della configurazione delle app con le app gestite. Vedere [Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi](app-configuration-policies-managed-app.md).
