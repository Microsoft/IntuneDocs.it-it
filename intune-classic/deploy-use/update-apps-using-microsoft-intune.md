---
title: Aggiornare le app
description: "Usare le informazioni riportate in questo argomento per comprendere come aggiornare le app quando è richiesta una nuova versione."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d974a3c8fd69ee970991af96afe2011c6d07db2a
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="update-apps-using-microsoft-intune"></a>Aggiornare le app con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune consente di gestire gli aggiornamenti delle app. Usare le informazioni riportate in questo argomento per comprendere come aggiornare le app quando è richiesta una nuova versione.

## <a name="how-to-update-apps"></a>Come aggiornare le app
Quando viene rilasciata una nuova versione di un'app che è stata distribuita, Intune consente di aggiornare e distribuire la versione più recente di tale app. È possibile sostituire una distribuzione solo con una versione più recente della stessa app (contrassegnata dallo stesso identificatore). Non è possibile usare gli aggiornamenti dell'app per aggiornare una distribuzione con un pacchetto dell'app diverso.

### <a name="app-identifiers"></a>Identificatori app
Identificatore app è una proprietà che identifica in modo univoco un'app. Non è possibile installare più copie di un'app con lo stesso identificatore. Di seguito sono riportati alcuni esempi di identificatori di app:

- **iOS**: ID aggregazione (ad esempio: com.microsoft.excel)
- **Android**: ID pacchetto (ad esempio: com.microsoft.excel)
- **Windows Phone**: (programma di installazione xap), usare ID prodotto (GUID)
- **Windows**: (appx/appxbundle), usare il nome completo del pacchetto



> [!IMPORTANT]
> Quando si distribuisce un'app con un'azione di distribuzione **Installazione richiesta** e successivamente si modifica l'azione di distribuzione in **Installazione disponibile**, gli aggiornamenti dell'app non vengono installati automaticamente nei dispositivi in cui l'app è stata installata prima di apportare la modifica alla distribuzione. Per risolvere questo problema, è possibile eseguire le operazioni seguenti:
>
> -   L'utente del dispositivo può accedere al portale aziendale, selezionare l'app installata e scegliere **Installa**.
> -   Modificare l'azione di distribuzione in **Disinstalla**e, una volta disinstallata l'app, distribuirla nuovamente con un'azione di distribuzione **Installazione disponibile**.

### <a name="to-update-an-app"></a>Per aggiornare un'app

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **App**&gt;**App**.

2.  Dall'elenco **App** selezionare l'app da aggiornare e quindi scegliere **Modifica**.

3.  Nella procedura guidata **Modifica software** specificare eventuali nuovi dettagli per il pacchetto dell'app.

4.  Al termine, scegliere **Aggiorna**.

Quando i dispositivi verificano successivamente la disponibilità di app, l'app verrà aggiornata automaticamente alla versione più recente.
Le app installate da un pacchetto (app line-of-business) verranno aggiornate automaticamente sia per le distribuzioni richieste sia per quelle disponibili, a condizione che abbiano lo stesso identificatore.

Per le app distribuite come collegamento a un archivio, l'aggiornamento viene gestito dall'archivio da cui proviene l'applicazione.