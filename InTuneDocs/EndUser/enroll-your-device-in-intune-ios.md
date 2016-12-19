---
title: Registrare il dispositivo iOS in Intune | Microsoft Intune
description: Descrive come registrare un dispositivo iOS in Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2f92ce22c9e6a87bccc7ab17144d0d52ff6cfc7b
ms.openlocfilehash: 4daf13d683ada52b098ef24363d2d409dc501c06


---


# <a name="enroll-your-ios-device-in-intune"></a>Registrare il dispositivo iOS in Intune

Se l'azienda o l'istituto di istruzione usa Microsoft Intune, è possibile registrare il dispositivo iOS per poter accedere a posta elettronica, file e altre risorse aziendali. La registrazione dei dispositivi consente al reparto IT di gestire e proteggere le risorse aziendali o dell'istituto di istruzione, offrendo al tempo stesso la possibilità di scegliere il dispositivo più adatto per svolgere il proprio lavoro. Per altre informazioni sulla registrazione , vedere [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md) (Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune).

Se si sta registrando un dispositivo macOS, vedere [Registrare il dispositivo macOS in Intune](enroll-your-device-in-intune-macos.md).

**Prima di iniziare:**

- Assicurarsi di aver terminato la registrazione prima di iniziare la procedura. Se si inizia prima di aver terminato la registrazione, è possibile che la registrazione non risulti corretti all'accesso successivo.
- Assicurarsi che il Wi-Fi funzioni. In caso contrario, la registrazione avrà esito negativo.
- Se Safari è stato bloccato nel dispositivo, sbloccarlo. Per eseguire la registrazione, è necessario usare Safari.


**Per registrare il dispositivo iOS:**

1.  Seguire la procedura in [Install and sign in to the Intune Company Portal app](install-and-sign-in-to-the-intune-company-portal-app-ios.md) (Installare e accedere all'app Portale aziendale di Intune).

2. Nella pagina **Configurazione dell'accesso aziendale** toccare **Inizia**.

    ![ios-enroll-comp-access-setup-begin](./media/ios-enroll-1a-comp-access-setup.png)

3. Nella schermata **Perché registrare il dispositivo?** leggere le informazioni sulle operazioni che possono essere eseguite durante la registrazione del dispositivo e quindi toccare **Continua**.

    ![ios-enroll-why-enroll](./media/ios-enroll-1b-why-enroll.png)

4. Rivedere l'elenco di cosa può e non può vedere l'amministratore IT nel dispositivo registrato e toccare **Continua**.

    ![ios-enroll-what-it-can-see](./media/ios-enroll-1c-we-care-privacy.png)

5.  Nella schermata **Operazioni successive** leggere cosa accade durante la registrazione, quindi toccare **Registra**.

    ![ios-enroll-what-comes-next](./media/ios-enroll-1d-what-comes-next.png)

6.  Nella schermata **Installa profilo** toccare **Installa** e, se richiesto, immettere il passcode.

    ![ios-enroll-install-profile](./media/ios-enroll-2-mgt-profile-install.png)

7.  Toccare **Installa**.

    ![ios-enroll-tap-install](./media/ios-enroll-3-mgt-profile-install-2.png)    

8.  Toccare **Installa** per indicare che il messaggio di avviso è stato letto.

    ![ios-enroll-tap-install-after-warning](./media/ios-enroll-4-warning.png)

9.  Toccare **Attendibilità**.

    ![ios-enroll-tap-trust](./media/ios-enroll-5-trust.png)

10.  Quando la schermata cambia a indicare che il profilo è stato installato, toccare **Fine**.

    ![ios-enroll-tap-done](./media/ios-enroll-6-done.png)

    Viene visualizzato un messaggio che indica la registrazione in corso del dispositivo.

11.  Alla visualizzazione di un messaggio che chiede se si vuole aprire la pagina nel Portale aziendale, toccare **Apri**.

    ![ios-enroll-open-comp-portal](./media/ios-enroll-7-open-cp.png)

12. Nella schermata **Company Access Setup** (Configurazione accesso aziendale) toccare **Continua**. Se l'amministratore IT ha impostato altri requisiti di sicurezza, ad esempio la necessità di impostare una password, seguire le istruzioni visualizzate fino a soddisfare tutti i requisiti di conformità, tornare alla schermata Configurazione dell'accesso aziendale e toccare **Continua**.

    ![ios-enroll-comp-access-tap-continue](./media/ios-enroll-8-comp-access-setup-compliance.png)

13. Toccare **Fine**.

    ![ios-enroll-tap-done](./media/ios-enroll-9-comp-access-setup-complete.png)

Il dispositivo è ora registrato in Intune e si riapre l'app Portale aziendale.


Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).



<!--HONumber=Dec16_HO2-->


