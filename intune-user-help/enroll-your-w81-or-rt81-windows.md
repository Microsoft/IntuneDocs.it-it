---
title: Come registrare il dispositivo Windows 8.1 o Windows RT 8.1 | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28984f26-1070-4f7a-877c-669a59375c0c
searchScope:
- User help
ROBOTS: 
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: aca401cab49230d2bcb9171cf532b52ce5219798
ms.openlocfilehash: 8e030c7b4b4aad7793b55e274a4d022bcf098611
ms.lasthandoff: 02/18/2017


---

# <a name="how-to-enroll-your-windows-81-or-windows-rt-81-device-in-intune"></a>Come registrare il dispositivo Windows 8.1 o Windows RT 8.1 in Intune

Se l'azienda o l'istituto di istruzione usa Microsoft Intune, è possibile registrare i dispositivi per poter accedere a posta elettronica, file e altre risorse aziendali. La registrazione dei dispositivi consente all'azienda di proteggere i suoi dati. Per altre informazioni sulla registrazione, vedere [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md) (Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune?) e [What your IT administrator can and can't see on your device](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md) (Che cosa può o non può vedere l'amministratore IT nel dispositivo?).


Per registrare il dispositivo Windows 8.1 o Windows RT 8.1:

1.  Nel dispositivo toccare **Impostazioni** &gt; **Impostazioni PC** &gt; **Rete** &gt; **Area di lavoro**.

    ![nav-to-workplace](./media/W81-1-workplacejoin.png)

2.  Immettere l'indirizzo di posta elettronica aziendale o dell'istituto di istruzione per l'ID utente, se necessario, e quindi toccare **Aggiungi**.

    Se l'ID utente non è necessario, viene usato l'indirizzo di posta elettronica immesso al momento dell'accesso al dispositivo.

3.  Immettere la password della posta elettronica aziendale o dell'istituto di istruzione.

    ![type-password](./media/W81-2-workplacesettings_signin.png)

4.  Nella sezione per l'**attivazione della gestione dei dispositivi** toccare **Attiva**.

    ![turn-on-device-management](./media/W81-3-dev-mgt-turn-on.png)

5.  Nella finestra di dialogo **Consenti app e servizi dell'amministratore IT** selezionare la casella **Accetto** e toccare **Attiva**.

    ![turn-on-allow-apps-services](./media/W81-4-agree-allow-apps-services.png)

    Al termine della registrazione, verrà visualizzata la schermata seguente.

    ![enrollment-complete](./media/W81-5-enrolled-done.png)

È inoltre consigliabile installare l'app Portale aziendale, che consente di identificare facilmente e ottenere le app aziendali rilevanti per sé e per il proprio ruolo. A seconda di come la società ha configurato Intune, è possibile che l'app Portale aziendale sia stata installata durante il processo di registrazione. Per verificare se l'app è disponibile, cercare **Portale aziendale** nell'elenco delle app. Se l'app Portale aziendale non è visualizzata nell'elenco di app, seguire questa procedura per installarla.

1.  Toccare **Start** &gt; **Store**.

2.  Toccare **Cerca** e quindi digitare **portale aziendale**.

3.  Nell'elenco dei risultati toccare **Portale aziendale**.

4.  Toccare **Installa** o **Gratuito**. L'opzione visualizzata varia a seconda di come la società ha configurato l'app.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).
