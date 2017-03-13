---
title: Come reimpostare il passcode dal sito Web del portale aziendale | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: 
ms.reviewer: mamoriss
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: f293901d3865f0b10ed876e83b151cf59a046cba
ms.openlocfilehash: 68725bb63ae2750e89a03c16027f8b4fd9111255
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Come reimpostare il passcode del dispositivo dal sito Web del portale aziendale

Se il PIN o la password di un dispositivo registrati in Intune viene smarrita, è possibile usare il [sito Web del portale aziendale](http://portal.manage.microsoft.com) per reimpostarla. È possibile usare il sito Web del portale aziendale per gestire computer e dispositivi registrati in Intune e per svolgere la maggior parte delle attività eseguibili tramite l'app Portale aziendale.

> [!NOTE]
> È possibile che non venga visualizzato il pulsante **Reimposta passcode** sul sito Web del portale aziendale. In questo caso, contattare l'amministratore IT per supporto tramite il sito Web del portale aziendale.

Per reimpostare il passcode:

1.    Nel [sito Web del portale aziendale](http://portal.manage.microsoft.com) toccare il pulsante __menu__ ![Piccola immagine del pulsante menu, tre barrette orizzontali parallele.](/Intune/whats-new/media/CP_hamburger_menu.png) e quindi selezionare __Dispositivi personali__.

2. Nella pagina __Dispositivi personali__ selezionare il nome del dispositivo da reimpostare.

  ![Screenshot della pagina Dispositivi personali con un paio di dispositivi non identificati sopra il banner con la richiesta di registrare i dispositivi non inclusi nell'elenco o di identificare quelli non identificati.](./media/macOS_enroll_002_tap_here_banner.png)

3.    Il dispositivo verrà aperto in una finestra popup. Selezionare il pulsante **Reimposta passcode**.

    ![Tutte le opzioni per un dispositivo selezionato nel sito Web del portale aziendale, tra cui Rinomina, Rimuovi, Reimposta dispositivo, Reimposta passcode e Blocco remoto. ](./media/iwp-screen-with-all-options.png)

4.  Verrà visualizzato un banner che richiede di confermare che si vuole reimpostare il passcode e che il dispositivo verrà disconnesso dopo tale operazione. Sarà quindi necessario attendere 5 minuti prima di eseguire nuovamente l'accesso.

  ![Banner di reimpostazione del passcode con il relativo avviso sulla reimpostazione del passcode del dispositivo e sulla disconnessione dell'utente. I pulsanti per l'input dell'utente sono Disconnetti e Annulla.](./media/iwp-reset-passcode-popup.png)

4.  Selezionare **Disconnetti**. Verrà visualizzato un messaggio finale con informazioni sulla rimozione del passcode dal dispositivo. Non rimuovere il passcode se il dispositivo non è a portata di mano, perché chiunque abbia accesso fisico al dispositivo potrà accedere alla maggior parte delle informazioni in esso contenute, sia personali che aziendali.

  ![Secondo banner di reimpostazione del passcode con il relativo avviso sulla reimpostazione del passcode del dispositivo e sulla rimozione del passcode dal dispositivo. Viene anche indicato come impostare un nuovo passcode accedendo alle impostazioni del dispositivo per farlo.](./media/iwp-reset-passcode-2nd-popup.png)


Dato che dispositivi diversi hanno tipi differenti di passcode, nella tabella seguente sono indicati i possibili effetti della reimpostazione del passcode sul dispositivo specifico. 

    |Tipo di dispositivo|Cosa accade con la reimpostazione|
    |------------|-----------|
    |Android|Viene rimosso il passcode esistente e viene creato un passcode temporaneo con lettere e numeri|
    |iOS|Viene rimosso il passcode esistente senza crearne uno temporaneo. Se si usa il sensore di impronte digitali Touch ID per aprire il dispositivo o effettuare acquisti, sarà necessario reimpostarlo.|
    |Windows 10 Mobile|Viene rimosso il passcode esistente e viene creato un passcode temporaneo con lettere e numeri. Se si usa il riconoscimento facciale di Windows Hello per eseguire l'accesso, la funzione continuerà a essere supportata.|
    |Windows Phone 8.1|Viene rimosso il passcode esistente e viene creato un passcode temporaneo con numeri.|

    5.  Sbloccare il dispositivo e impostare un nuovo passcode o modificare il passcode temporaneo in **Impostazioni** sul dispositivo.

    Per visualizzare una notifica di conferma della reimpostazione della password, fare clic sul flag di notifica nella parte superiore destra del sito Web del portale aziendale.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

