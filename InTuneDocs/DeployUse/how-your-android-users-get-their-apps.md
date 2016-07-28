---
title: "Modalità di recupero delle app per gli utenti di Android | Microsoft Intune"
description: Metodi per rendere disponibili le app Android per gli utenti finali
keywords: 
author: Staciebarker
manager: arob98
ms.date: 7/7/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 376e6c1ae229187ab8ec73390f091f1d534365dd
ms.openlocfilehash: 43b7eb3378d9977b9d19196c91a812d9411752b9


---


# Modalità di recupero delle app per gli utenti di Android
Usare queste informazioni per comprendere come e dove gli utenti Android possono ottenere le app che vengono distribuite tramite Microsoft Intune. Le informazioni possono essere diverse per i dispositivi Android nativi rispetto ai dispositivi Samsung Knox.

## Dispositivi Android nativi (non Samsung KNOX)

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. Viene visualizzata una notifica, che è possibile toccare per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. | Toccare l'app nel portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa.    | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

## Dispositivi Android Samsung KNOX

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. L'app viene installata senza ulteriore intervento dell'utente. | Toccare l'app nel portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | L'app viene installata senza ulteriore intervento dell'utente.    | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

Le app possono essere gestite o non gestite, come descritto di seguito. Il processo per rendere le app gestite è lo stesso per tutti i tipi di dispositivi Android.

**App gestite**: app che possono essere gestite tramite criteri e che sono state "integrate" in Intune o che sono state compilate con l'SDK della gestione di applicazioni mobili (MAM) di Intune. Queste app possono essere gestite da Intune ed è possibile applicarvi criteri dell'applicazione.

**App non gestite**: app che possono essere gestite tramite criteri e che non sono state integrate in Intune o che non incorporano l'SDK del software MAM di Intune. Non è possibile applicare i criteri dell'applicazione a queste app.

### Vedere anche
[Aggiungere app con Microsoft Intune](/intune/deploy-use/add-apps)
[Modalità di recupero delle app per gli utenti di iOS](how-your-ios-users-get-their-apps.md)
[Modalità di recupero delle app per gli utenti di Windows](how-your-windows-users-get-their-apps.md)



<!--HONumber=Jul16_HO3-->


