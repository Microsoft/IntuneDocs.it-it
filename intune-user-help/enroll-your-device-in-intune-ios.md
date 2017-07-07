---
title: Registrare il dispositivo iOS in Intune | Microsoft Docs
description: Descrive come registrare un dispositivo iOS in Intune
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: af3313e6ba5cbf9184aaaa9b197f7a3b2b9d4c3e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-your-ios-device-in-intune"></a>Registrare il dispositivo iOS in Intune

Se l'azienda o l'istituto di istruzione usa Microsoft Intune, è possibile registrare il dispositivo iOS per poter accedere a posta elettronica, file e altre risorse aziendali. La registrazione dei dispositivi consente al reparto IT di gestire e proteggere le risorse aziendali o dell'istituto di istruzione, offrendo al tempo stesso la possibilità di scegliere il dispositivo più adatto per svolgere il proprio lavoro. Per altre informazioni sulla registrazione , vedere [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md) (Cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune)

<iframe src="https://channel9.msdn.com/Series/IntuneEnrollment/iOS-Enrollment/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

> [!NOTE]
> Se si sta in effetti tentando di registrare un dispositivo macOS, ad esempio un MacBook Pro o iMac, [usare invece queste istruzioni](enroll-your-device-in-intune-macos.md).

**Prima di iniziare:**

- Assicurarsi di aver terminato la registrazione prima di iniziare la procedura. Se si sospende l'esecuzione per alcuni minuti, in genere il processo viene arrestato e sarà necessario riavviarlo.
- Se per qualsiasi motivo la registrazione ha esito negativo, è necessario tornare all'app Portale aziendale per riprovare.
- Assicurarsi che il Wi-Fi funzioni. In caso contrario, la registrazione avrà esito negativo.
- Se Safari è stato bloccato nel dispositivo, sbloccarlo. Per eseguire la registrazione, è necessario usare Safari.


**Per registrare il dispositivo iOS:**

1.  Seguire la procedura in [Install and sign in to the Intune Company Portal app](install-and-sign-in-to-the-intune-company-portal-app-ios.md) (Installare e accedere all'app Portale aziendale di Intune).

2. Nella pagina **Configurazione dell'accesso aziendale** toccare **Inizia**.

    ![ios-enroll-comp-access-setup-begin](./media/ios-enroll-1a-comp-access-setup.png)

3. Nella schermata **Perché registrare il dispositivo?** leggere le informazioni sulle operazioni che possono essere eseguite durante la registrazione del dispositivo e quindi toccare **Continua**.

    ![ios-enroll-why-enroll](./media/ios-enroll-1b-why-enroll.png)

> [!NOTE]
> I triangoli gialli non indicano che si è già verificato un errore, ma che alcuni passaggi del processo di registrazione devono ancora essere completati.

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

> [!Note]
> Se la propria organizzazione usa software per la gestione delle spese per telecomunicazioni, sarà necessario eseguire alcuni passaggi aggiuntivi prima che la registrazione del dispositivo sia completata. Per altre informazioni, vedere [qui](enroll-your-device-with-telecom-expense-management-ios.md).

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).
