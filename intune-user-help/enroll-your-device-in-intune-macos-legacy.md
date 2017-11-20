---
title: Registrare il dispositivo macOS legacy in Intune | Microsoft Docs
description: Descrive come registrare un dispositivo macOS in Intune
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope: User help
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 115f32989cfbb991e097404c5297e7997f28f796
ms.sourcegitcommit: e692be57ec7044dfc224b70941affbfd7efba421
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/08/2017
---
# <a name="enroll-your-legacy-macos-device-in-intune"></a>Registrare il dispositivo macOS legacy in Intune

Queste istruzioni sono relative a dispositivi macOS con OS X Yosemite 10.10 e versioni precedenti. Vedere [qui](enroll-your-device-in-intune-macos-cp.md) istruzioni per la registrazione dei dispositivi macOS nelle versioni successive di macOS.

La possibilità di accedere alle app, ai dati e alle risorse dell'organizzazione significa poter svolgere il proprio lavoro. Se si usa un dispositivo macOS in ufficio, sarà necessario installare un __profilo di gestione__. Si tratta semplicemente di un file configurato dal supporto tecnico dell'azienda che carica le impostazioni e le informazioni di accesso nel dispositivo Mac. Per saperne di più Scoprire [cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)

1. Trovare __Safari__ nel __Dock__ e aprire una nuova finestra, quindi aprire il [sito Web del portale aziendale](https://portal.manage.microsoft.com).
2. Accedere al sito Web del portale aziendale con l'account aziendale o dell'istituto di istruzione.

  [!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. Dopo aver eseguito l'accesso, fare clic su **Menu** in alto a sinistra e selezionare **Dispositivi personali**.

 ![Screenshot della pagina di destinazione per il portale Web con il portale Web che mostra che non è possibile installare alcuna app, con il pulsante Dispositivi personali sotto.](./media/macOS_enroll_001_landing_page.png)

4. Nella pagina __Dispositivi personali__ verrà visualizzato un elenco di dispositivi registrati o semplicemente un banner. Ciò dipende dal fatto di avere già un dispositivo macOS registrato o meno. Per registrare un dispositivo che non è elencato, selezionare il banner che indica __If your device is listed, tap here to identify it. You can also tap here to enroll your device if it is not listed__ (Se il dispositivo è elencato, toccare qui per identificarlo. È anche possibile toccare qui per registrare il dispositivo se non è elencato). Se non si hanno dispositivi registrati, verrà visualizzato il banner **Non è stato registrato alcun dispositivo. Registrare questo dispositivo toccando qui.**

  ![Screenshot della pagina Dispositivi personali con un paio di dispositivi non identificati sopra il banner con la richiesta di registrare i dispositivi non inclusi nell'elenco o di identificare quelli non identificati.](./media/macOS_enroll_002_tap_here_banner.png)

5. Verrà visualizzata una finestra popup con una breve spiegazione del motivo per cui è necessario __identificare o registrare il dispositivo__. Leggere le informazioni e quindi fare clic su __Registra__ per continuare.

 ![Identifica o registra il dispositivo macOS](./media/macOS_enroll_003_IDenroll_popup.png)

6. Verrà visualizzata una seconda finestra popup con una breve spiegazione di cosa accade quando si __registra il dispositivo__. Leggere le informazioni e quindi fare clic su __Installa__ per continuare.

 ![Registra il dispositivo macOS](./media/macOS_enroll_004_enroll_popup.png)

  > [!NOTE]
  > Intune deve accedere al computer per assicurarsi che il dispositivo sia sufficientemente sicuro per accedere alle risorse dell'organizzazione. Altre informazioni su [cosa avviene quando si registra il dispositivo in Intune](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md).

7. Verrà aperta la finestra __Preferenze di sistema__ in cui viene richiesto se si vuole __installare il profilo di gestione__. Fare clic su __Installa__ per procedere oppure su __Mostra profilo__ per visualizzare altri dettagli.

 ![Installare il profilo di gestione](./media/macOS_enroll_005_sysprefs_mgmt_profile.png)

8. Verrà visualizzata una finestra popup di macOS. Confermare che si vuole apportare modifiche specificando __nome utente__ e __password__ per il computer, quindi fare clic su __OK__. Il profilo di gestione verrà installato nel Mac.

 ![Finestra popup di installazione del profilo macOS](./media/macOS_enroll_006_sysprefs_admin_login.png)

9. Potrebbero essere visualizzati alcuni messaggi aggiuntivi da Mac con altri dettagli relativi al profilo o per chiedere conferma per procedere con l'__installazione__. Fare clic su __Continua__ e __Installa__ nelle varie finestre per procedere. Al termine dell'installazione, sarà possibile visualizzare il __profilo di gestione__ appena installato nell'elenco dei __profili di dispositivo__.

 ![Profilo macOS installato](./media/macOS_enroll_007_sysprefs_installed_profile.png)

È possibile che alcuni profili risultino **Unverified** (Non verificato). Se sono profili aziendali, questo è normale.

Serve ancora assistenza? Rivolgersi al personale del supporto tecnico dell'azienda. È possibile trovare le informazioni di contatto nel [sito Web del portale aziendale](https://portal.manage.microsoft.com).
