---
title: "Modalità di recupero delle app per gli utenti di iOS | Microsoft Intune"
description: Metodi per rendere disponibili le app iOS per gli utenti finali
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9f1946c02c6267a22844106e8f72555ec5e9cabb
ms.openlocfilehash: 212dcd31697180dae61569dda13b56704a079bf4


---


# Modalità di recupero delle app per gli utenti di iOS

Usare queste informazioni per comprendere come e dove gli utenti possono ottenere le app che vengono distribuite tramite Microsoft Intune.

**App richieste**: app richieste dall'amministratore che vengono installate nel dispositivo con un coinvolgimento minimo dell'utente, a seconda della piattaforma.

**App disponibili**: app che vengono messe a disposizione nell'elenco delle app del Portale aziendale e che un utente può scegliere di installare a propria discrezione.

**App gestite**: app che possono essere gestite tramite criteri e che sono state "integrate" in Intune o che sono state compilate con l'SDK della gestione di applicazioni mobili (MAM) di Intune. Queste app possono essere gestite da Intune ed è possibile applicarvi criteri dell'applicazione.

**App non gestite**: app che possono essere gestite tramite criteri e che non sono state integrate in Intune o che non incorporano l'SDK del software MAM di Intune. Non è possibile applicare i criteri dell'applicazione a queste app.

Le restrizioni di Apple impediscono alle app dell'app store line-of-business e gestite di essere elencate nell'app Portale aziendale, quindi gli utenti devono visitare visualizzazioni diverse per trovare le proprie app. Le app per ogni riquadro visualizzato nella pagina App dell'app Portale aziendale sono disponibili come indicato di seguito:

- Il riquadro **App aziendali** punta all'elenco delle app nella scheda **TUTTE** del [sito Web del portale aziendale](http://portal.manage.microsoft.com).

- Il riquadro **Altre app** attualmente punta a una vista, all'interno dell'app Portale aziendale, che elenca tutte le app che Apple consente all'app Portale aziendale di visualizzare. Sono incluse tutte le app ad eccezione di quelle dell'app store line-of-business e gestite.

- Il riquadro **Categorie** attualmente punta a una vista, all'interno dell'app Portale aziendale, che elenca le categorie delle app.

    ![ios-how-to-sync-device-with-intune](./media/ios-sync-comp-portal-apps.png)


###Vedere anche
[Modalità di recupero delle app per gli utenti di Android](how-your-android-users-get-their-apps.md)</br>
[Modalità di recupero delle app per gli utenti di Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Aug16_HO4-->


