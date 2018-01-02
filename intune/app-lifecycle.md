---
title: Panoramica del ciclo di vita dell'app per Intune
description: Informazioni sul ciclo di vita delle app gestite di Intune, dall'aggiunta all'eventuale ritiro.
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60347012-bc3f-4b9a-a4f4-6d3c5021a6e6
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e50e3af525be48bf058dd32bfb7b93508d500a3
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2017
---
# <a name="overview-of-the-app-lifecycle"></a>Panoramica del ciclo di vita dell'app

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Il ciclo di vita di un'app di Intune inizia quando si aggiunge l'app e termina, dopo alcuni passaggi intermedi, quando si rimuove l'app.

![Ciclo di vita dell'app](./media/app-lifecycle.png "Ciclo di vita di un'app di Intune")

## <a name="add"></a>Aggiunta

Il primo passaggio della distribuzione di app consiste nell'aggiungere a Intune le app da gestire e assegnare. Le procedure di base per i molti tipi di app che possono essere usati sono le stesse. Intune consente di aggiungere app sia per i [dispositivi registrati](apps-add.md) ([portale classico](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune)) che per i [PC Windows gestiti con il software client di Intune](/intune-classic/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune).

## <a name="deploy"></a>Distribuisci

Dopo aver aggiunto l'app a Intune è possibile [assegnarla agli utenti e ai dispositivi gestiti](apps-deploy.md) ([portale classico](/intune-classic/deploy-use/deploy-apps)). Intune semplifica questo processo e, dopo aver distribuito l'app, consente di [monitorare il risultato](apps-monitor.md) ([portale classico](/intune-classic/deploy-use/monitor-apps-in-microsoft-intune)) della distribuzione dalla console di amministrazione di Intune. In alcuni store di app, come quelli di [Apple](vpp-apps-ios.md) ([portale classico](/intune-classic/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)) e [Windows](windows-store-for-business.md) ([portale classico](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)), è anche possibile acquistare licenze di app in blocco per l'azienda. Intune consente di sincronizzare i dati con gli App Store per distribuire e monitorare l'uso delle licenze per determinati tipi di app direttamente dalla console di amministrazione di Intune.

## <a name="configure"></a>Configura

Come parte del ciclo di vita, vengono rilasciate regolarmente nuove versioni delle app. Intune offre strumenti con cui è possibile [aggiornare facilmente le app](apps-add.md) ([portale classico](/intune-classic/deploy-use/update-apps-using-microsoft-intune)) distribuite a una versione più recente. Alcune app consentono anche di configurare funzionalità aggiuntive, ad esempio:
- I [criteri di configurazione delle app iOS](app-configuration-policies-use-ios.md) ([portale classico](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune)) applicano le impostazioni per le app iOS compatibili usate quando si esegue l'app. Ad esempio, un'app potrebbe richiedere impostazioni di personalizzazione specifiche o il nome di un server a cui connettersi.
- Con i [criteri per Managed Browser](app-configuration-managed-browser.md) ([portale classico](/intune-classic/deploy-use/manage-internet-access-using-managed-browser-policies)) è possibile configurare le impostazioni per Intune Managed Browser, che sostituisce il browser predefinito del dispositivo e consente di limitare i siti Web che gli utenti possono visitare.

## <a name="protect"></a>Protezione

Intune offre molti modi per proteggere i dati nelle app. I metodi principali sono:
- L'[accesso condizionale](conditional-access.md) ([portale classico](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)) controlla l'accesso alla posta elettronica e agli altri servizi in base alle condizioni specificate. Le condizioni includono i tipi di dispositivo o la conformità con un [criterio di conformità del dispositivo](device-compliance.md) ([portale classico](/intune-classic/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)) che è stato distribuito.
- I [criteri di protezione delle app](app-protection-policy.md) ([portale classico](/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)) funzionano con singole app e consentono di proteggere i dati aziendali che usano. Ad esempio, è possibile limitare la copia dei dati tra app non gestite e app gestite dall'utente oppure impedire l'esecuzione delle app su dispositivi jailbroken o rooted.

## <a name="retire"></a>Ritiro

È probabile che le app distribuite a un certo punto diventino obsolete e vadano rimosse. Intune semplifica la procedura di [ritiro delle app dal servizio](device-management.md) ([portale classico](/intune-classic/deploy-use/retire-apps-using-microsoft-intune)).
