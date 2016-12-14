---
title: "Modalità di recupero delle app per gli utenti di iOS | Microsoft Intune"
description: Metodi per rendere disponibili le app iOS per gli utenti finali
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7e3135c1-df26-48c9-aa4c-cdab6168897a
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 3ba0a5cda91164761c4576df935c54390bc78f8c


---


# <a name="how-your-ios-users-get-their-apps"></a>Modalità di recupero delle app per gli utenti di iOS

Usare queste informazioni per comprendere come e dove gli utenti possono ottenere le app che vengono distribuite tramite Microsoft Intune.

**App richieste**: app richieste dall'amministratore che vengono installate nel dispositivo con un coinvolgimento minimo dell'utente, a seconda della piattaforma.

**App disponibili**: app che vengono messe a disposizione nell'elenco delle app Portale aziendale e che un utente può scegliere di installare.

**App gestite**: app che possono essere gestite tramite criteri e che sono state "integrate" in Intune o che sono state compilate con l'SDK (Software Development Kit) della gestione di applicazioni mobili (MAM) di Intune. Queste app possono essere gestite da Intune ed è possibile applicarvi criteri dell'applicazione.

**App non gestite**: app che possono essere gestite tramite criteri e che non sono state integrate in Intune o che non comprendono l'SDK del software MAM di Intune. Non è possibile applicare i criteri dell'applicazione a queste app.

Le restrizioni di Apple impediscono alle app line-of-business e alle app di App Store gestite di essere elencate nell'app Portale aziendale. Per risolvere questo problema, i riquadri nell'app Portale aziendale per iOS indirizzano gli utenti a visualizzazioni diverse in un'unica posizione, il sito Web del portale aziendale, per tutte le app.

Gli utenti registrati possono ottenere le app toccando i riquadri seguenti nella schermata App dell'app Portale aziendale:

- Il riquadro **Tutte le app** punta all'elenco di tutte le app nella scheda TUTTE del [sito Web del portale aziendale](http://portal.manage.microsoft.com).

- Dal riquadro **App in evidenza** gli utenti vengono indirizzati alla scheda IN EVIDENZA del sito Web del portale aziendale.

- Il riquadro **Categorie** punta alla scheda CATEGORIE del sito Web del portale aziendale.

 
![Schermata delle app nel portale aziendale iOS](./media/ios-cp-app-main-apps-screen.png)

Per informazioni su come aggiungere app e inserirle in questi riquadri, vedere [Aggiungere app per dispositivi registrati in Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune.md).

### <a name="see-also"></a>Vedere anche
[Modalità di recupero delle app per gli utenti di Android](how-your-android-users-get-their-apps.md)

[Modalità di recupero delle app per gli utenti di Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Nov16_HO1-->

