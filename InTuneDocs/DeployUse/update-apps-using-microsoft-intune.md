---
title: Aggiornare le app | Microsoft Intune
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: beee6933-876a-4be0-b395-4c24cfbd519b
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: 0581d1476fba5bedcdd4446df20f8f92b151f41b
ms.openlocfilehash: 9e5b8f4a467e8e58cc2f8fa495b5f008eee7e35b


---

# Aggiornare le app con Microsoft Intune
Microsoft Intune consente di gestire gli aggiornamenti delle app. Usare le informazioni in questo argomento per comprendere come aggiornare le app quando è richiesta una nuova versione.

## Come aggiornare le app
Quando viene rilasciata una nuova versione di un'app che è stata distribuita, Intune consente di aggiornare e distribuire la versione più recente dell'app. È possibile sostituire una distribuzione solo con una versione più recente della stessa app (usando lo stesso identificatore). Non è possibile usare gli aggiornamenti dell'app per aggiornare una distribuzione con un pacchetto dell'app diverso.

> [!IMPORTANT]
> Quando si distribuisce un'app con un'azione di distribuzione **Installazione richiesta** e successivamente si modifica l'azione di distribuzione in **Installazione disponibile**, gli aggiornamenti dell'app non vengono installati automaticamente nei dispositivi in cui l'app è stata installata prima di apportare la modifica alla distribuzione. Per risolvere questo problema, è possibile eseguire le operazioni seguenti:
> 
> -   L'utente del dispositivo può accedere al portale aziendale, selezionare l'app installata e scegliere **Installa**.
> -   Modificare l'azione di distribuzione in **Disinstalla**e, una volta disinstallata l'app, distribuirla nuovamente con un'azione di distribuzione **Installazione disponibile**.

### Per aggiornare un'app

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **App** &gt; **App**.

2.  Dall'elenco **App** selezionare l'app da aggiornare e quindi scegliere **Modifica**.

3.  Nella procedura guidata **Modifica software** specificare eventuali nuovi dettagli per il pacchetto dell'app.

4.  Al termine, scegliere **Aggiorna**.

Quando i dispositivi verificano successivamente la disponibilità di app, l'app verrà aggiornata automaticamente alla versione più recente.
Le app installate da un pacchetto (app line-of-business) verranno aggiornate automaticamente sia per le distribuzioni richieste, sia per quelle disponibili, purché abbiano lo stesso identificatore.
Per le app distribuite come collegamento a un archivio, l'aggiornamento viene gestito dall'archivio da cui proviene l'applicazione.






<!--HONumber=Jul16_HO2-->


