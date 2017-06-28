---
title: Gestire il collegamento utente-dispositivo per PC Windows
description: Come collegare un utente a un PC Windows gestito da Intune.
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 9641c40229be52066a97389584e55f2f95bc286d
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017


---

# <a name="manage-user-device-linking-for-windows-pcs"></a>Gestire il collegamento utente-dispositivo per PC Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Le informazioni fornite in questo argomento sono valide solo per i desktop Windows gestiti come PC usando il client software di Intune. 

Prima di distribuire software a un utente, è necessario collegare l'utente a un PC. È possibile collegare un utente a più PC, ma ogni PC può essere collegato a un solo utente. Gli utenti vengono automaticamente collegati a qualsiasi PC che registrano in Intune usando il portale aziendale.

Per collegare un utente a un PC:

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il PC da collegare a un utente.

2.  Selezionare il PC che si vuole collegare a un utente e quindi scegliere **Collega utente**.

    Nella finestra di dialogo **Collega utente** viene visualizzato un elenco di utenti disponibili con il rispettivo nome visualizzato, l'ID utente e il numero di PC a cui è attualmente collegato ciascun utente. Se un utente è già collegato al PC selezionato, il nome e l'ID utente vengono visualizzati in **Utente corrente**. Se il PC non è collegato ad alcun utente, in **Utente corrente** viene visualizzato **Nessun utente**.

3.  Eseguire una delle operazioni seguenti:

    -   Per lasciare il PC collegato all'utente corrente, se presente, scegliere **Annulla**.

    -   Per rimuovere il collegamento all'utente corrente, se presente, scegliere **Rimuovi collegamento**&gt; **OK**.

    -   Per collegare il PC a un nuovo utente, selezionare un utente nell'elenco **Tutti gli utenti** . Verificare che i dati dell'utente siano corretti e quindi scegliere **OK**.

> [!TIP]
> Per limitare la capacità degli utenti finali di collegare se stessi a PC, abilitare l'opzione **Limita la capacità utente di collegarsi ai computer** nei criteri **Impostazioni agente di Microsoft Intune**.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
