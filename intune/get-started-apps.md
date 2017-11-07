---
title: Introduzione alle app
titlesuffix: Azure portal
description: Ttrovare le app e aggiungerle ai dispositivi per consentire ai dipendenti di svolgere il proprio lavoro.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c5c12c988f1181887c10f6ed14353365546e743b
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2017
---
# <a name="get-started-with-adding-apps"></a>Introduzione all'aggiunta di app

Intune supporta vari metodi per la distribuzione di app nei dispositivi aziendali:

* **Programmi di installazione del software**: programmi in cui si carica un file che viene scaricato nei dispositivi degli utenti
* __Collegamenti esterni__: utili quando l'app risiede in un app store pubblico o è un'app Web
* **App gestite**: utili per i dispositivi iOS in cui è necessario implementare modalità aggiuntive di gestione applicazioni mobili alle app disponibili nell'App Store

Di seguito viene illustrato uno dei metodi più rapidi di distribuzione app ovvero l'assegnazione di un'app da uno store pubblico.

## <a name="how-do-i-assign-a-public-store-app"></a>Come si assegna un'app di uno store pubblico?

1. Accedere al [portale di Azure](https://portal.azure.com).
2. In **Cerca risorse** cercare **Intune**.
3. Selezionare **App per dispositivi mobili** e quindi selezionare **App**.
4. Selezionare **Aggiungi**, quindi **App Store iOS** come **Tipo di app**.
5. Nella casella di testo, cercare l'app da assegnare al dispositivo. Scegliere l'app e selezionare **OK**.
6. Nel pannello **Aggiungi app** selezionare **Informazioni sull'app** e verificare che tutte le informazioni sull'app siano compilate. È possibile aggiungere altri dettagli facoltativi per definire l'app, ad esempio **Proprietario**, **Note**, **Sviluppatore** e un **URL privacy** per l'informativa sulla privacy dell'azienda.
7. Verificare di avere selezionato Sì per Visualizza come app in primo piano nel portale aziendale, quindi scegliere OK.
8. Selezionare **Aggiungi** per aggiungere l'app. Viene visualizzata la **Panoramica** dell'app. Scegliere **Assegnazioni**, quindi fare clic su **Selezione gruppi** per assegnare l'app al gruppo di test. Impostare l'app come **Disponibile** per il download. L'app viene visualizzata come **App in primo piano** nel dispositivo di test.

## <a name="learn-more"></a>Altre informazioni

* [Che cos'è la gestione delle app con Intune?](app-management.md)
* [Panoramica del ciclo di vita dell'app](app-lifecycle.md)
* [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)
