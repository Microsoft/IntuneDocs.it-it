---
title: "Modalità di recupero delle app per gli utenti di Android | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d3bcf89636f9da8fd8bfa5cc52391742a9ce9f92
ms.openlocfilehash: 25571ce1b214c927f3dc2ea3968d00970621e474


---


# Modalità di recupero delle app per gli utenti di Android
Usare queste informazioni per comprendere come e dove gli utenti possono ottenere le app che vengono distribuite tramite Microsoft Intune. 

**App richieste**: app richieste dall'amministratore che vengono installate nel dispositivo con un coinvolgimento minimo dell'utente, a seconda della piattaforma.
 
- **Dispositivi Samsung Knox**: se si distribuisce un'app obbligatoria a dispositivi Samsung Knox, questa viene installata nei dispositivi in modo automatico e invisibile all'utente.
- **Dispositivi nativi (non Samsung Knox)**: se si distribuisce un'app obbligatoria a dispositivi Samsung Knox, questa non viene installata nei dispositivi degli utenti in modo automatico e invisibile all'utente. Agli utenti viene invece richiesto di confermare l'installazione dell'app. Dopo la conferma l'app viene scaricata. Gli utenti ricevono quindi una notifica che li informa della necessità di procedere con l'installazione manuale. 

**App disponibili**: app che vengono messe a disposizione nell'elenco delle app del Portale aziendale e che un utente può scegliere di installare a propria discrezione.

**App gestite**: app che possono essere gestite tramite criteri e che sono state "integrate" in Intune o che sono state compilate con l'SDK della gestione di applicazioni mobili (MAM) di Intune. Queste app possono essere gestite da Intune ed è possibile applicarvi criteri dell'applicazione.

**App non gestite**: app che possono essere gestite tramite criteri e che non sono state integrate in Intune o che non incorporano l'SDK del software MAM di Intune. Non è possibile applicare i criteri dell'applicazione a queste app.

###Vedere anche
[Aggiungere app con Microsoft Intune](/intune/deploy-use/add-apps)
[Modalità di recupero delle app per gli utenti di iOS](how-your-ios-users-get-their-apps.md)
[Modalità di recupero delle app per gli utenti di Windows](how-your-windows-users-get-their-apps.md)


<!--HONumber=Jul16_HO1-->


