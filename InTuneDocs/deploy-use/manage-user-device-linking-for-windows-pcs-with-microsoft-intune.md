---
title: Gestire il collegamento utente-dispositivo per PC Windows | Microsoft Intune
description: Come collegare un utente a un PC Windows gestito da Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 39fec6a2ea8d8c0f4b6ea1460c76a8a6c652d614


---

# <a name="manage-user-device-linking-for-windows-pcs"></a>Gestire il collegamento utente-dispositivo per PC Windows
Prima di distribuire software a un utente, è necessario collegare l'utente a un computer. È possibile collegare un utente a più computer, ma ogni computer può essere collegato a un solo utente. Gli utenti vengono automaticamente collegati a qualsiasi computer che registrano in Intune usando il portale aziendale.

Per collegare un utente a un computer:

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il computer da collegare a un utente.

2.  Selezionare il computer che si vuole collegare a un utente, quindi scegliere **Collega utente**.

    Nella finestra di dialogo **Collega utente** è visualizzato un elenco di utenti disponibili con il rispettivo nome visualizzato, l'ID utente e il numero di computer a cui è attualmente collegato ciascun utente. Se un utente è già collegato al computer selezionato, il nome e l'ID utente vengono visualizzati in **Utente corrente**. Se il computer non è collegato ad alcun utente, **Nessun utente** viene visualizzato sotto **Utente corrente**.

3.  Eseguire una delle operazioni seguenti:

    -   Per lasciare il computer collegato all'utente corrente, se presente, scegliere **Annulla**.

    -   Per rimuovere il collegamento all'utente corrente, se presente, scegliere **Rimuovi collegamento **&gt; **OK**.

    -   Per collegare il computer a un nuovo utente, selezionare un utente nell'elenco **Tutti gli utenti** . Verificare che i dati dell'utente siano corretti e quindi scegliere **OK**.

> [!TIP]
> Per limitare la capacità di collegamento degli utenti finali ai computer, abilitare l'opzione **Limita la capacità utente di collegarsi ai computer** nei criteri **Impostazioni agente di Microsoft Intune**.

### <a name="see-also"></a>Vedere anche

[Attività comuni di gestione di PC Windows con il client software di Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


