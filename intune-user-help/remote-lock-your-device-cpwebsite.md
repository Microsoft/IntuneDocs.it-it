---
title: Bloccare il dispositivo dal portale aziendale | Microsoft Docs
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
ms.assetid: adc6af23-b22f-42e5-955a-4dffbdb8b42b
searchScope: User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 3976327decf6b1850baed8e781609e458d375aa1
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2017
---
# <a name="remotely-lock-your-device-from-the-company-portal-website"></a>Bloccare il dispositivo in modalità remota dal sito Web del portale aziendale

Può succedere che i dispositivi vengano persi. Se il dispositivo è stato smarrito o rubato, la prima preoccupazione potrebbe essere il possibile accesso alle informazioni sul dispositivo da parte di qualsiasi utente, ovunque si trovi il dispositivo.

[!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

Per ragioni di sicurezza, è possibile bloccarlo usando l'opzione Blocco remoto sul [sito Web del portale aziendale](https://portal.manage.microsoft.com). L'opzione Blocco remoto funziona per:

* Android
* iOS
* macOS
* Windows 10 Mobile (se per il dispositivo è già stato impostato un passcode)
* Windows Phone 8.1 (se per il dispositivo è già stato impostato un passcode)

## <a name="to-use-remote-lock-to-lock-your-device"></a>Per usare Blocco remoto per bloccare il dispositivo

1.  Nel [sito Web del portale aziendale](https://portal.manage.microsoft.com) toccare il pulsante __menu__ ![Piccola immagine del pulsante menu, tre barrette orizzontali parallele.](/Intune/whats-new/media/CP_hamburger_menu.png) e quindi selezionare __Dispositivi personali__.

  ![Immagine del sito Web del portale aziendale con un menu laterale espanso sul lato sinistro della schermata con i pulsanti Home, Tutte le app, Dispositivi personali, Supporto tecnico e Disconnetti.](/media/iwp-expanded-sidebar.png)

2. Nella pagina __Dispositivi personali__ selezionare il nome del dispositivo da bloccare.

  ![Screenshot della pagina Dispositivi personali con un paio di dispositivi non identificati sopra il banner con la richiesta di registrare i dispositivi non inclusi nell'elenco o di identificare quelli non identificati.](./media/macOS_enroll_002_tap_here_banner.png)

3.  Il dispositivo verrà aperto in una finestra popup. Toccare il pulsante **Blocco remoto**.

    ![Tutte le opzioni per un dispositivo selezionato nel sito Web del portale aziendale, tra cui Rinomina, Rimuovi, Reimposta dispositivo, Reimposta passcode e Blocco remoto. ](./media/iwp-screen-with-all-options.png)

4.  Viene visualizzato un avviso che informa che si sta per bloccare il dispositivo. Toccare **Blocco remoto**. Il sito Web del portale aziendale tenterà di bloccare il dispositivo.

    Dopo aver selezionato **Blocco remoto** viene visualizzato il messaggio "Blocco remoto in sospeso".  Quando Blocco remoto ha esito positivo, lo stato passa a "Blocco remoto riuscito."

    Lo stato del blocco remoto viene visualizzato in tre posizioni:

    * L'area delle notifiche del sito Web.
    * La pagina **Dettagli** per il dispositivo.
    * Il riquadro contenente il nome del dispositivo nella sezione **Dispositivi personali** della pagina.

> [!Note]
> Se viene visualizzata la notifica "Blocco remoto non riuscito", attendere qualche minuto e quindi tentare nuovamente di bloccare il dispositivo. Dopo aver iniziato il nuovo tentativo, lo stato diventa nuovamente "Blocco remoto in sospeso". Se il nuovo tentativo non funziona, è necessario contattare il supporto tecnico aziendale.

Se il dispositivo viene ritrovato e si vuole rimuovere il blocco dopo aver usato Blocco remoto, immettere il passcode.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com).
