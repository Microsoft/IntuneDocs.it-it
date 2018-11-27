---
title: Modalità di recupero delle app per gli utenti di iOS
description: Metodi per rendere disponibili le app iOS per gli utenti finali
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/28/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: b8694596851c231c4c7d1a8a5edd448a7506f829
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186308"
---
# <a name="how-your-ios-users-get-their-apps"></a>Modalità di recupero delle app per gli utenti di iOS

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Usare queste informazioni per comprendere come e dove gli utenti possono ottenere le app che vengono distribuite tramite Microsoft Intune.

**App richieste**: app richieste dall'amministratore che vengono installate nel dispositivo con un coinvolgimento minimo dell'utente, a seconda della piattaforma.

**App disponibili**: app che vengono messe a disposizione nell'elenco delle app Portale aziendale e che un utente può scegliere di installare.

**App gestite**: app che possono essere gestite usando i criteri e sono state sottoposte a "wrapping" in Intune o sono state compilate con Intune App Software Development Kit (SDK). Queste app possono essere gestite da Intune ed è possibile applicarvi criteri di protezione delle app.

**App non gestite**: app che possono essere gestite tramite criteri e che non sono state integrate in Intune o che non comprendono Intune App SDK. Non è possibile applicare i criteri dell'applicazione a queste app.

Le restrizioni di Apple impediscono alle app line-of-business e alle app di App Store gestite di essere elencate nell'app Portale aziendale. Per risolvere questo problema, i riquadri nell'app Portale aziendale per iOS indirizzano gli utenti a visualizzazioni diverse in un'unica posizione, il sito Web del portale aziendale, per tutte le app.

Gli utenti registrati possono ottenere le app toccando i riquadri seguenti nella schermata App dell'app Portale aziendale:

- Il riquadro **Tutte le app** punta all'elenco di tutte le app nella scheda TUTTE del [sito Web del portale aziendale](https://portal.manage.microsoft.com).

- Dal riquadro **App in evidenza** gli utenti vengono indirizzati alla scheda IN EVIDENZA del sito Web del portale aziendale.

- Il riquadro **Categorie** punta alla scheda CATEGORIE del sito Web del portale aziendale.


![Schermata delle app nel portale aziendale iOS](./media/ios-cp-app-main-apps-screen.png)

Per informazioni su come aggiungere app, vedere [Come aggiungere un'app a Microsoft Intune](apps-add.md).

### <a name="see-also"></a>Vedere anche
[Modalità di recupero delle app per gli utenti di Android](end-user-apps-android.md)

[Modalità di recupero delle app per gli utenti di Windows](end-user-apps-windows.md)
