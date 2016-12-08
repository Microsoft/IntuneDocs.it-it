---
title: Registrare il dispositivo macOS in Intune | Microsoft Intune
description: Descrive come registrare un dispositivo macOS in Intune
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 162d176c5f272f5f19ba18cdd07fe815ac1bcce7
ms.openlocfilehash: fc0efceb8a0c3e1323f7d94625bc5f618d35bfd6


---

# <a name="enroll-your-macos-device-in-intune"></a>Registrare il dispositivo macOS in Intune

La possibilità di accedere alle app, ai dati e alle risorse dell'organizzazione significa poter svolgere il proprio lavoro. Se si usa un dispositivo macOS in ufficio, sarà necessario installare un __profilo di gestione__. Si tratta semplicemente di un file configurato dall'amministratore IT che carica le impostazioni e le informazioni di accesso nel dispositivo Mac dell'utente. Per saperne di più Scoprire [cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md).

  > [!NOTE]
  > Se si sta in effetti tentando di registrare un dispositivo iOS, ad esempio un iPhone o iPad, [usare invece queste istruzioni](enroll-your-device-in-intune-ios.md).

1. Trovare __Safari__ nel __Dock__ e aprire una nuova finestra, quindi aprire il [sito Web del portale aziendale](http://portal.manage.microsoft.com).
2. Accedere al sito Web del portale aziendale con l'account aziendale o dell'istituto di istruzione.

  [!INCLUDE[wit_nextref](../includes/end-user-password-guidance.md)]

3. Quando si effettua l'accesso, verranno visualizzati le __App__ e i __Dispositivi personali__ disponibili, oltre alle eventuali __informazioni di contatto__ per il personale IT. Nella parte superiore della pagina sarà visualizzato l'avviso **Il dispositivo non è registrato o l'app Portale aziendale non riesce a identificarlo. <u>Toccare qui</u> per selezionare un dispositivo diverso.** Fare clic su __Toccare qui__.

 ![Pagina di destinazione macOS del portale aziendale](./media/macOS_enroll_001_landing_page.png)

4. Verrà visualizzata una finestra popup con una breve spiegazione del motivo per cui è necessario __identificare o registrare il dispositivo__. Leggere le informazioni e quindi fare clic su __Registra__ per continuare.

 ![Identifica o registra il dispositivo macOS](./media/macOS_enroll_002_IDenroll_popup.png)

5. Verrà visualizzata una seconda finestra popup con una breve spiegazione di cosa accade quando si __registra il dispositivo__. Leggere le informazioni e quindi fare clic su __Installa__ per continuare.

 ![Registra il dispositivo macOS](./media/macOS_enroll_003_enroll_popup.png)

  > [!NOTE]
  > Intune deve accedere al computer per assicurarsi che il dispositivo sia sufficientemente sicuro per accedere alle risorse dell'organizzazione. Altre informazioni su [cosa avviene quando si registra il dispositivo in Intune](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios).

6. Verrà aperta la finestra __Preferenze di sistema__ in cui viene richiesto se si vuole __installare il profilo di gestione__. Fare clic su __Installa__ per procedere oppure su __Mostra profilo__ per visualizzare altri dettagli.

 ![Installare il profilo di gestione](./media/macOS_enroll_004_sysprefs_mgmt_profile.png)

7. Verrà visualizzata una finestra popup di macOS. Confermare che si vuole apportare modifiche specificando __nome utente__ e __password__ per il computer, quindi fare clic su __OK__. Il profilo di gestione verrà installato nel Mac.

 ![Finestra popup di installazione del profilo macOS](./media/macOS_enroll_005_sysprefs_admin_login.png)

8. Potrebbero essere visualizzati alcuni messaggi aggiuntivi da Mac con altri dettagli relativi al profilo o per chiedere conferma per procedere con l'__installazione__. Fare clic su __Continua__ e __Installa__ nelle varie finestre per procedere. Al termine dell'installazione, sarà possibile visualizzare il __profilo di gestione__ appena installato nell'elenco dei __profili di dispositivo__.

 ![Profilo macOS installato](./media/macOS_enroll_006_sysprefs_installed_profile.png)

Serve ancora assistenza? Rivolgersi all'amministratore IT. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](http://portal.manage.microsoft.com).



<!--HONumber=Nov16_HO4-->


