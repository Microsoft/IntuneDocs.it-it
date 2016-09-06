---
title: Registrare il dispositivo Windows 10 in Intune | Microsoft Intune
description: Descrive come registrare un dispositivo Windows 10 Mobile o Desktop in Intune
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 06/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 36250832-c6fd-4e8d-b681-de735023ebc3
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 02287eb01598c28906045fd8def9e8b4660e3da5
ms.openlocfilehash: 8806231f8d02885a192053a35559694a8984d2f5


---


# Registrare il dispositivo Windows 10 Mobile o Windows 10 Desktop in Intune

Se l'azienda o l'istituto di istruzione usa Microsoft Intune, è possibile registrare i dispositivi per poter accedere a posta elettronica, file e altre risorse aziendali. La registrazione dei dispositivi consente all'azienda di proteggere i suoi dati. Per altre informazioni sulla registrazione, vedere [What happens if you install the Company Portal app and enroll your device in Intune?](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows.md) (Che cosa avviene quando si installa l'app Portale aziendale e si registra il dispositivo in Intune?) e [What your IT administrator can and can't see on your device](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md) (Che cosa può o non può vedere l'amministratore IT nel dispositivo?).


Per registrare il dispositivo Windows 10 Mobile o Windows 10:

1.  Passare a Windows **Impostazioni** e toccare **Account**.

    ![settings-accounts](./media/w10-enroll-rs1-settings-accounts.png)

2.  Esaminare le due schermate seguenti e trovare quella simile a quanto viene visualizzato sul dispositivo. Seguire i passaggi corrispondenti alla schermata visualizzata sul dispositivo.

    Se si visualizza questa schermata, seguire i passaggi in [Passaggi da seguire se si visualizza Access work or school (Accesso azienda o istituto di istruzione)](#steps-to-follow-if-you-see-access-work-or-school).

    ![connect-to-work-or-school](./media/w10-enroll-rs1-connect-to-work-or-school.png)

    Se si visualizza questa schermata, seguire i passaggi in [Passaggi da seguire se si visualizza Il tuo account](#steps-to-follow-if-you-see-your-account).

    ![your-account](./media/w10-enroll-2-accounts-your-account.png)

## Passaggi da seguire se si visualizza Access work or school (Accesso azienda o istituto di istruzione)

1.  Toccare **Access work or school** (Accesso azienda o istituto di istruzione).

    ![tap-access-work-school-account](./media/w10-enroll-rs1-connect-to-work-or-school.png)

2.  Immettere il messaggio di posta elettronica aziendale o dell'istituto di istruzione e toccare **Avanti**.

    ![enter-your-work-or-school-account](./media/w10-enroll-rs1-set-up-work-or-school-account.png)

3. Accedere a Intune con l'account aziendale o dell'istituto di istruzione.

    ![add-work-school-account](./media/w10-enroll-rs1-enter-your-credentials.png)

    Verrà visualizzato un messaggio che indica che la società o l'istituto di istruzione sta registrando il dispositivo.

4. Quando viene visualizzata la pagina **La configurazione è completata.** toccare **Chiudi**. La procedura è stata completata.

  ![tap-close-on-you-are-all-set-screen](./media/w10-enroll-rs1-youre-all-set.png)

5. Se si vuole verificare che la connessione sia corretta, tornare a **Impostazioni** e controllare che l'account aziendale o dell'istituto di istruzione sia presente nell'elenco.

    ![validate-that-connection-was-set-up-correctly](./media/w10-enroll-rs1-validate-successful-enrollment.png)

Se è stata seguita la procedura descritta sopra, ma non è ancora possibile accedere alla posta elettronica e ai file aziendali o dell'istituto di istruzione, seguire i passaggi in [Passaggi di risoluzione dei problemi da seguire se si visualizza Access work or school (Accesso azienda o istituto di istruzione)](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-access-work-or-school).


## Passaggi da seguire se si visualizza Il tuo account

1.  Passare a Windows **Impostazioni** e toccare **Account**.

    ![go-to-settings-accounts](./media/W10-enroll-1-settings-accounts.png)

2.  Toccare **Account**.

    ![tap-your-account](./media/W10-enroll-2-accounts-your-account.png)

3.  Toccare **Aggiungi un account aziendale o dell'istituto di istruzione**.

    ![add-work-or-school-account](./media/w10-enroll-3-add-work-school-acct.png)

4.  Accedere con le credenziali aziendali o dell'istituto di istruzione.

    ![sign-in](./media/W10-enroll-4-sign-in.png)

Se è stata seguita la procedura descritta sopra, ma non è ancora possibile accedere alla posta elettronica, ai file e ad altri dati aziendali o dell'istituto di istruzione, provare a eseguire i passaggi di risoluzione dei problemi in [Passaggi di risoluzione dei problemi da seguire se si visualizza Il tuo account](troubleshoot-your-windows-10-device-windows.md#troubleshooting-steps-to-follow-if-you-see-your-account).

È inoltre consigliabile installare l'app Portale aziendale, che consente di identificare facilmente e ottenere le app aziendali rilevanti per sé e per il proprio ruolo. A seconda di come la società ha configurato Intune, l'app Portale aziendale potrebbe essere stata installata durante il processo di registrazione. Per verificare se l'app è disponibile, cercare **Portale aziendale** nell'elenco delle app. Se l'app Portale aziendale non è visualizzata nell'elenco di app, seguire questa procedura per installarla.

1.  Toccare **Start** &gt; **Store**.

2.  Toccare **Cerca** e digitare **portale aziendale**.

3.  Nell'elenco dei risultati toccare **Portale aziendale** &gt; **Installa**.

4.  Toccare **Installa** o **Gratuito**. L'opzione visualizzata varia a seconda di come la società ha configurato l'app.

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).

### Vedere anche
[Uso del dispositivo Windows con Intune](using-your-windows-device-with-intune.md)



<!--HONumber=Aug16_HO3-->


