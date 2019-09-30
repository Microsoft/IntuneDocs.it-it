---
title: Modalità di recupero delle app per gli utenti di Android
description: Metodi per rendere disponibili le app Android per gli utenti finali
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 960c440372613fed2c92ce00c604d97e1f122e8f
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71239831"
---
# <a name="how-your-android-users-get-their-apps"></a>Modalità di recupero delle app per gli utenti di Android

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Questo articolo consente di comprendere come e dove gli utenti finali Android possono ottenere le app che vengono distribuite tramite Microsoft Intune. Le informazioni possono variare a seconda del tipo di dispositivo, ad esempio dispositivi Android nativi o dispositivi Samsung KNOX Standard.

## <a name="native-non-samsung-knox-standard-android-devices"></a>Dispositivi Android nativi (non Samsung KNOX Standard)

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. Viene visualizzata una notifica, che è possibile toccare per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. | Toccare l'app nel Portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | Viene visualizzata una notifica che non è possibile chiudere, indicante la necessità di installare un'app. Toccare la notifica per avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa.    | Viene visualizzata una notifica che non è possibile chiudere, in cui viene indicata la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

Per installare [app line-of-business](lob-apps-android.md), gli utenti finali devono consentire l'installazione da origini sconosciute. Questa impostazione è solitamente disponibile in due posizioni diverse:

* **Android 7.1.2 e versioni precedenti**: **Impostazioni** > **Sicurezza** > **Origini sconosciute**
* **Android 8.0 e versioni successive**: **Impostazioni** > **App e notifiche** > **Accesso speciale** > **Installa app sconosciute** > **Portale aziendale** > **Consenti da questa origine**

In questo caso, l'app Portale aziendale informerà l'utente e lo assisterà per selezionare l'impostazione appropriata. 

## <a name="samsung-knox-standard-android-devices"></a>Dispositivi Android Samsung KNOX Standard

| Tipo di app | App line-of-business | App di Play Store  |
| ------------- |-------------| -----|
| App disponibili      | Toccare **Installa** nel portale aziendale. L'app viene installata senza ulteriore intervento dell'utente. | Toccare l'app nel Portale aziendale per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione.|
| Required apps      | L'app viene installata senza ulteriore intervento dell'utente.    | Viene visualizzata una notifica che non è possibile chiudere, in cui viene indicata la necessità di installare un'app. Toccare la notifica per essere reindirizzati a una pagina dell'app in Play Store, in cui è possibile avviare l'installazione. Al termine dell'installazione, la notifica viene rimossa. |

Le app possono essere gestite o non gestite, come descritto di seguito. Il processo per rendere le app gestite è lo stesso per tutti i tipi di dispositivi Android.

**App gestite**: queste app sono gestite tramite criteri. Sono state sottoposte a wrapping da Intune o compilate con Intune App SDK. Queste app possono essere gestite da Intune ed è possibile applicarvi criteri dell'applicazione.

**App non gestite**: queste app non sono gestite tramite criteri. Non sono state sottoposte a wrapping da Intune o non includono Intune App SDK. Non è possibile applicare i criteri dell'applicazione a queste app.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Dispositivi Zebra con Mobility Extensions di Zebra

Intune usa il toolkit Mobility Extensions (MX) di Zebra per installare automaticamente le app in dispositivi Zebra gestiti dall'amministratore del dispositivo. Questa funzionalità consente di distribuire e aggiornare le app nei dispositivi Zebra senza l'intervento dell'utente. Se nel dispositivo è installata la versione di MX 4.2 o una versione precedente, le app non vengono installate automaticamente. Per altre informazioni, vedere [Full MX Feature Matrix](http://techdocs.zebra.com/mx/compatibility/) (Matrice completa della funzionalità MX) sul sito Web di Zebra.

Le app line-of-business distribuite in dispositivi Zebra devono essere installate da un percorso pubblico nel dispositivo. Il pacchetto dell'app con estensione apk può essere accessibile ad altre app e servizi che hanno anche accesso all'archivio pubblico nel dispositivo. In genere è possibile accedere in un breve intervallo di tempo compreso tra il completamento del download dell'app e l'inizio dell'installazione. In questo arco di tempo si può verificare un attacco temporale. È ad esempio possibile modificare un pacchetto con estensione apk durante questo intervallo. Intune riduce al minimo la quantità di tempo che il file con estensione apk trascorre nell'archivio pubblico e non consente l'installazione di app senza firma. Per ridurre al minimo i rischi per la sicurezza, assicurarsi che i file con estensione apk caricati non contengano informazioni riservate.

## <a name="see-also"></a>Vedere anche

[Aggiungere app con Microsoft Intune](apps-add.md)

[Modalità di recupero delle app per gli utenti di iOS](end-user-apps-ios.md)

[Modalità di recupero delle app per gli utenti di Windows](end-user-apps-windows.md)
