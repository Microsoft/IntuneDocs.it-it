---
title: Introduzione alle app di Microsoft Intune
titlesuffix: 
description: Trovare le app e aggiungerle ai dispositivi per consentire ai propri collaboratori di svolgere il proprio lavoro.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 3/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1542fc3-672e-47c1-a21f-82826a2f8ac4
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0185eebbe436da73e1920d7cd834f0897a143894
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="get-started-with-adding-apps-in-microsoft-intune"></a>Introduzione all'aggiunta di app in Microsoft Intune

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. Intune supporta diversi tipi di app. Inoltre, le opzioni disponibili variano per ogni tipo di app.

Intune consente di aggiungere e assegnare ai dispositivi aziendali i tipi di app seguenti:
- **App dello Store**: per i dispositivi in cui è necessario implementare modalità aggiuntive di gestione applicazioni mobili alle app disponibili nell'App Store.
- **App scritte internamente (line-of-business)**: programmi in cui si carica un file scaricato nei dispositivi degli utenti.
- **App predefinite**: per l'assegnazione di app gestite dedicate, ad esempio le app di Office 365, ai dispositivi iOS e Android. 
- **App sul Web**: Intune crea un collegamento all'app Web nella schermata iniziale del dispositivo.

## <a name="how-do-i-assign-a-public-store-app"></a>Come si assegna un'app di uno store pubblico?

Nell'esempio seguente viene illustrato come aggiungere un'app iOS in Microsoft Intune.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **App** nella sezione **Gestisci**.
5. Scegliere **Aggiungi** sul lato destro del riquadro **App**.
6. Nell'elenco **Tipo di app** selezionare **iOS** dai tipi di **app dello Store** disponibili.
6. Scegliere **Cerca in App Store**.
7. Nel pannello **Cerca in App Store** per prima cosa selezionare le impostazioni locali del paese per App Store.
8. Digitare il nome (o una parte del nome) nella casella di ricerca. Intune esegue la ricerca nello Store e restituisce un elenco di risultati pertinenti.
9. Scegliere l'app dall'elenco e fare clic su **Seleziona**.
10. Selezionare **Informazioni sull'app** per configurare le informazioni sull'app.
11. (Facoltativo) Aggiungere altri dettagli per agevolare l'organizzazione dell'app, ad esempio **Proprietario**, **Note**, **Sviluppatore** e un **URL privacy** che punta all'informativa sulla privacy dell'azienda.
12. Selezionare **Sì** per l'opzione **Visualizza come app in primo piano nel portale aziendale**. 
13. Fare clic su **OK** dopo aver aggiunto tutte le informazioni necessarie sull'app.
14. Fare clic su **Aggiungi** nel pannello **Aggiungi app**. Verrà visualizzata la **Panoramica** dell'app. 

## <a name="next-steps"></a>Passaggi successivi

Dopo avere aggiunto un'app a Intune, è possibile stabilire quali gruppi di dipendenti potranno includere l'app sul proprio dispositivo.

- [Come assegnare app ai gruppi](apps-deploy.md)
- 
## <a name="learn-more"></a>Altre informazioni

* [Che cos'è la gestione delle app con Intune?](app-management.md)
* [Panoramica del ciclo di vita dell'app](app-lifecycle.md)
* [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)
