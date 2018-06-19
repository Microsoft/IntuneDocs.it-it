---
title: Come reimpostare il passcode dal sito Web del portale aziendale | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 45b087b9617b783517f8296f1726891392764d5f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31019331"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>Come reimpostare il passcode del dispositivo dal sito Web del portale aziendale

Se il PIN o la password di un dispositivo registrati in Intune viene smarrita, è possibile usare il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog) per reimpostarla. È possibile usare il sito Web del portale aziendale per gestire computer e dispositivi registrati in Intune e per svolgere la maggior parte delle attività eseguibili tramite l'app Portale aziendale.

> [!NOTE]
> Se si usa un dispositivo aziendale registrato è possibile che non venga visualizzato il pulsante Reimposta passcode nel sito Web del portale aziendale. In caso contrario, è necessario contattare il supporto tecnico dell'azienda per reimpostare il passcode.

Per reimpostare il passcode:

1. Nel [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog) toccare il pulsante __menu__ ![Piccola immagine del pulsante menu, tre barrette orizzontali parallele.](/intune/media/CP_hamburger_menu.png) e quindi selezionare __Dispositivi personali__.

2. Nella pagina __Dispositivi personali__ selezionare il nome del dispositivo da reimpostare.

   ![Screenshot della pagina Dispositivi personali con un paio di dispositivi non identificati sopra il banner con la richiesta di registrare i dispositivi non inclusi nell'elenco o di identificare quelli non identificati.](./media/macOS_enroll_002_tap_here_banner.png)

3. Il dispositivo verrà aperto in una finestra popup. Selezionare il pulsante **Reimposta passcode**.

   ![Tutte le opzioni per un dispositivo selezionato nel sito Web del portale aziendale, tra cui Rinomina, Rimuovi, Reimposta dispositivo, Reimposta passcode e Blocco remoto. ](./media/iwp-screen-with-all-options.png)

4. Verrà visualizzato un banner che richiede di confermare che si vuole reimpostare il passcode e che il dispositivo verrà disconnesso dopo tale operazione. Sarà quindi necessario attendere 5 minuti prima di eseguire nuovamente l'accesso.

   ![Banner di reimpostazione del passcode con il relativo avviso sulla reimpostazione del passcode del dispositivo e sulla disconnessione dell'utente. I pulsanti per l'input dell'utente sono Disconnetti e Annulla.](./media/iwp-reset-passcode-popup.png)

5. Selezionare **Disconnetti**. Verrà visualizzato un messaggio finale con informazioni sulla rimozione del passcode dal dispositivo. Non rimuovere il passcode se il dispositivo non è a portata di mano, perché chiunque abbia accesso fisico al dispositivo potrà accedere alla maggior parte delle informazioni in esso contenute, sia personali che aziendali. 

   ![Secondo banner di reimpostazione del passcode con il relativo avviso sulla reimpostazione del passcode del dispositivo e sulla rimozione del passcode dal dispositivo. Viene anche indicato come impostare un nuovo passcode accedendo alle impostazioni del dispositivo per farlo.](./media/iwp-reset-passcode-2nd-popup.png)

   Dispositivi diversi hanno tipi diversi di passcode.

   **Android**: rimuove il passcode esistente e crea un passcode temporaneo con lettere e numeri. 
  
   > [!NOTE]
   > Non è possibile reimpostare il passcode per i dispositivi con Android 7.0 e versioni successive. Se si dimentica il passcode è necessario ripristinare le impostazioni del produttore nei dispositivi.

   **iOS**: rimuove il passcode esistente senza crearne uno temporaneo. Se si usa il sensore di impronte digitali Touch ID per aprire il dispositivo o effettuare acquisti, sarà necessario reimpostarlo.

   **Windows 10 Mobile**: rimuove il passcode esistente e crea un passcode temporaneo con lettere e numeri. Se si usa il riconoscimento facciale di Windows Hello per eseguire l'accesso, la funzione continuerà a essere supportata.
    
   **Windows Phone 8.1**: rimuove il passcode esistente e crea un passcode temporaneo con numeri.

   Per i dispositivi Android e Windows, la password temporanea verrà visualizzata in **Dettagli dispositivo**. 

6. Sbloccare il dispositivo e impostare un nuovo passcode o modificare il passcode temporaneo in **Impostazioni** sul dispositivo.

Per visualizzare una notifica di conferma della reimpostazione della password, fare clic sul flag di notifica nella parte superiore destra del sito Web del portale aziendale.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
