---
title: Gestire il collegamento utente-dispositivo per PC Windows
titlesuffix: Microsoft Intune
description: Come collegare un utente a un PC Windows gestito da Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic-keep
ms.openlocfilehash: 0354bf10601ed9a31cdc3beba1bf6825896a2016
ms.sourcegitcommit: 116be0eaa44fd5518ff34780d39569224ef4746b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2018
ms.locfileid: "36310947"
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Gestire il collegamento utente-dispositivo per PC Windows

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Le informazioni fornite in questo argomento sono valide solo per i desktop Windows gestiti come PC usando il client software di Intune. 

Prima di distribuire software a un utente, è necessario collegare l'utente a un PC. È possibile collegare un utente a più PC, ma ogni PC può essere collegato a un solo utente. Gli utenti vengono automaticamente collegati a qualsiasi PC che registrano in Intune usando il portale aziendale.

Per collegare un utente a un PC:

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il PC da collegare a un utente.

2. Selezionare il PC che si vuole collegare a un utente e quindi scegliere **Collega utente**.

   Nella finestra di dialogo **Collega utente** viene visualizzato un elenco di utenti disponibili con il rispettivo nome visualizzato, l'ID utente e il numero di PC a cui è attualmente collegato ciascun utente. Se un utente è già collegato al PC selezionato, il nome e l'ID utente vengono visualizzati in **Utente corrente**. Se il PC non è collegato ad alcun utente, in **Utente corrente** viene visualizzato **Nessun utente**.

3. Eseguire una delle operazioni seguenti:

   - Per lasciare il PC collegato all'utente corrente, se presente, scegliere **Annulla**.

   - Per rimuovere il collegamento all'utente corrente, se presente, scegliere <strong>Rimuovi collegamento **&gt; **OK</strong>.

   - Per collegare il PC a un nuovo utente, selezionare un utente nell'elenco **Tutti gli utenti** . Verificare che i dati dell'utente siano corretti e quindi scegliere **OK**.

> [!TIP]
> Per limitare la capacità degli utenti finali di collegare se stessi a PC, abilitare l'opzione **Limita la capacità utente di collegarsi ai computer** nei criteri **Impostazioni agente di Microsoft Intune**.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)