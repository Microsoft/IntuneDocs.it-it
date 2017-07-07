---
title: "Modalità di recupero delle app per gli utenti di Android"
description: Metodi per rendere disponibili le app Android per gli utenti finali
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4f0364750edf2e97e2b621c27fb25bea8e0f537c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-your-android-users-get-their-apps"></a>Modalità di recupero delle app per gli utenti di Android

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Usare queste informazioni per comprendere come e dove gli utenti Android possono ottenere le app che vengono distribuite tramite Microsoft Intune. Le informazioni possono variare a seconda del tipo di dispositivo, ad esempio dispositivi Android nativi o dispositivi Samsung KNOX Standard.

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivi Android nativi (non Samsung KNOX Standard)

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. Viene visualizzata una notifica, che è possibile toccare per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. | Toccare l'app nel portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa.    | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

## <a name="samsung-knox-standard-android-devices"></a>Dispositivi Android Samsung KNOX Standard

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. L'app viene installata senza ulteriore intervento dell'utente. | Toccare l'app nel portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | L'app viene installata senza ulteriore intervento dell'utente.    | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

Le app possono essere gestite o non gestite, come descritto di seguito. Il processo per rendere le app gestite è lo stesso per tutti i tipi di dispositivi Android.

**App gestite**: queste app possono essere gestite tramite criteri. Sono state integrate in Intune o sono state compilate con l'SDK (Software Development Kit) della gestione delle applicazioni mobili di Intune (MAM). Queste app possono essere gestite da Intune ed è possibile applicarvi criteri dell'applicazione.

**App non gestite**: queste app non possono essere gestite tramite criteri. Non sono state integrate in Intune o non comprendono l'SDK della gestione delle applicazioni mobili di Intune. Non è possibile applicare i criteri dell'applicazione a queste app.

### <a name="see-also"></a>Vedere anche
[Aggiungere app con Microsoft Intune](apps-add.md)

[Modalità di recupero delle app per gli utenti di iOS](end-user-apps-ios.md)

[Modalità di recupero delle app per gli utenti di Windows](end-user-apps-windows.md)