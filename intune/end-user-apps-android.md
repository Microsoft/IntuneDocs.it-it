---
title: Modalità di recupero delle app per gli utenti di Android
description: Metodi per rendere disponibili le app Android per gli utenti finali
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 5f8263f06fe33537a74a6d1889b02b89ee6a825f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183401"
---
# <a name="how-your-android-users-get-their-apps"></a>Modalità di recupero delle app per gli utenti di Android

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Usare queste informazioni per comprendere come e dove gli utenti Android possono ottenere le app che vengono distribuite tramite Microsoft Intune. Le informazioni possono variare a seconda del tipo di dispositivo, ad esempio dispositivi Android nativi o dispositivi Samsung KNOX Standard.

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivi Android nativi (non Samsung KNOX Standard)

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. Viene visualizzata una notifica, che è possibile toccare per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. | Toccare l'app nel portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa.    | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

Gli utenti finali devono consentire l'installazione da origini sconosciute per installare [app line-of-business](lob-apps-android.md). A tale scopo, sono disponibili le procedure seguenti:

* **Android 7.1.2 e versioni precedenti**: **Impostazioni** > **Sicurezza** > **Origini sconosciute**
* **Android 8.0 e versioni successive**: **Impostazioni** > **App e notifiche** > **Accesso speciale** > **Installa app sconosciute** > **Portale aziendale** > **Consenti da questa origine**

In questo caso, l'app Portale aziendale informerà l'utente e lo assisterà per selezionare l'impostazione appropriata. 


## <a name="samsung-knox-standard-android-devices"></a>Dispositivi Android Samsung KNOX Standard

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. L'app viene installata senza ulteriore intervento dell'utente. | Toccare l'app nel portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | L'app viene installata senza ulteriore intervento dell'utente.    | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

Le app possono essere gestite o non gestite, come descritto di seguito. Il processo per rendere le app gestite è lo stesso per tutti i tipi di dispositivi Android.

**App gestite**: queste app possono essere gestite tramite criteri. Sono state sottoposte a wrapping da Intune o compilate con Intune App SDK. Queste app possono essere gestite da Intune ed è possibile applicarvi criteri dell'applicazione.

**App non gestite**: queste app non possono essere gestite tramite criteri. Non sono state sottoposte a wrapping da Intune o non includono Intune App SDK. Non è possibile applicare i criteri dell'applicazione a queste app.

### <a name="see-also"></a>Vedere anche
[Aggiungere app con Microsoft Intune](apps-add.md)

[Modalità di recupero delle app per gli utenti di iOS](end-user-apps-ios.md)

[Modalità di recupero delle app per gli utenti di Windows](end-user-apps-windows.md)
