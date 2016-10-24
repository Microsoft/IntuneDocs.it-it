---
title: Registrare il dispositivo Android in Intune | Microsoft Intune
description: Descrive come registrare un dispositivo Android in Intune
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/09/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
ms.reviewer: arnab
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7eefcefa5e1cd0f789c77bf020c256e449099273
ms.openlocfilehash: 5d7507d9c09867b5c302caba409f1a7347fae4b6


---


# Registrare il dispositivo Android in Intune

Se l'azienda o l'istituto di istruzione usa Microsoft Intune, è possibile registrare il dispositivo Android per poter accedere a posta elettronica, file e altre risorse aziendali. La registrazione dei dispositivi consente al reparto IT di gestire e proteggere le risorse aziendali o dell'istituto di istruzione, offrendo al tempo stesso la possibilità di scegliere il dispositivo più adatto per svolgere il proprio lavoro. Per altre informazioni sulla registrazione, vedere [What happens when I install and Company Portal app and enroll my device?](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-android.md) (Che cosa succede quando si installa l'app Portale aziendale e si registra il dispositivo?).

Queste istruzioni sono valide per la registrazione di dispositivi Android Samsung Knox e Android nativi, esclusi i dispositivi Samsung Knox. Per sapere se il dispositivo è di tipo Samsung Knox, andare in **Impostazioni** &gt; **Info dispositivo**. Se non viene visualizzata la versione Knox, significa che il dispositivo è un dispositivo Android nativo.

Prima o dopo la registrazione potrebbe essere necessario scegliere la categoria che descrive meglio come viene usato il dispositivo. Questa categoria consente all'amministratore IT di controllare le app a cui è possibile accedere.

Se si verifica un errore durante la registrazione del dispositivo in Intune, è possibile [inviare gli errori di registrazione all'amministratore IT](send-enrollment-errors-to-your-it-administrator-android.md).

**Per registrare il dispositivo Android:**

1.  Installare l'app Portale aziendale di Intune da [Google Play](http://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal).

2.  Aprire l'app Portale aziendale di Microsoft Intune.

3.  Nella **schermata iniziale** del portale aziendale toccare **Accedi** e quindi accedere con l'account aziendale o dell'istituto di istruzione.

    ![android-company-portal-sign-in](./media/and-enroll-0-welcome-screen.png)   

4.  Se l'amministratore IT ha impostato i termini e le condizioni aziendali, toccare **ACCETTO** per accettarli.

    ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5.  Accedere all'app Portale aziendale usando l'account e la password aziendali o dell'istituto di istruzione e toccare **Accedi**.

    ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6.  Nella schermata **Configurazione dell'accesso aziendale** toccare **INIZIA**.

    ![Schermata di configurazione dell'accesso aziendale](./media/and-enroll-4a-comp-access-setup.png)

7.  Nella schermata **Perché registrare il dispositivo?** leggere le informazioni sulle operazioni che possono essere eseguite durante la registrazione del dispositivo e quindi toccare **CONTINUA**.

    ![Schermata Perché registrare il dispositivo?](./media/and-enroll-4b-why-enroll.png)

8.  Rivedere cosa può e non può visualizzare l'amministratore IT nel dispositivo e toccare **CONTINUA**.

    ![Impostazioni di privacy](./media/and-enroll-4c-we-care-privacy.png)

9.  Nella schermata **Operazioni successive** leggere cosa accade durante la registrazione, quindi toccare **REGISTRA**.

    ![Operazioni successive](./media/and-enroll-4d-what-comes-next.png)

10.  Se si usa Android 6.0 o versione successiva, eseguire questo passaggio. In caso contrario, andare al passaggio successivo.

    Se l'amministratore IT ha configurato determinati criteri, saranno visualizzati i messaggi seguenti:
    -   **Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?**

        ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

    Se viene visualizzato questo messaggio, toccare **CONSENTI**. È consigliabile scegliere questa opzione perché **Microsoft non effettua né gestisce le chiamate telefoniche**. Il testo del messaggio è controllato da Google, quindi Microsoft non può modificarlo. Quando si consente l'accesso, il dispositivo può inviare il codice IMEI (International Mobile Station Equipment Identity) a Intune. Il codice IMEI è un numero, simile a un numero di serie, che identifica in modo univoco un dispositivo mobile.

    Se si nega l'accesso, il messaggio sarà di nuovo visualizzato quando si accederà di nuovo al Portale aziendale. È tuttavia possibile disattivare la visualizzazione futura dei messaggi selezionando la casella **Non visualizzare più questo messaggio**. Se si decide successivamente di consentire l'accesso, andare a **Impostazioni** &gt; **App** &gt; **Portale aziendale** &gt; **Autorizzazioni** &gt; **Telefono**, quindi attivare l'autorizzazione.

    -   **Allow Company Portal to access your contacts? (Consenti al Portale aziendale l'accesso ai contatti?)**

        ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

    Se viene visualizzato questo messaggio, toccare **CONSENTI**. È consigliabile scegliere questa opzione perché **Microsoft non può mai accedere ai contatti**. Il testo del messaggio è controllato da Google, quindi Microsoft non può modificarlo. Quando si concede l'accesso, si consente solo all'app Portale aziendale di creare, usare e gestire il proprio account aziendale.

    Se si nega l'accesso, il messaggio sarà di nuovo visualizzato quando si accederà di nuovo al Portale aziendale. È tuttavia possibile disattivare la visualizzazione futura dei messaggi selezionando la casella **Non visualizzare più questo messaggio**. Se si decide successivamente di consentire l'accesso, andare a **Impostazioni** &gt; **App** &gt; **Portale aziendale** &gt; **Autorizzazioni** &gt; **Telefono**, quindi attivare l'autorizzazione.

11.  Nella schermata relativa all'**attivazione dell'amministratore del dispositivo** toccare **Attiva**.

    ![Schermata di attivazione dell'amministratore del dispositivo](./media/and-enroll-5-activate.png)

12.  Seguire le istruzioni per immettere un PIN o una password. Se sul dispositivo è già stato impostato un PIN o una password, questa schermata non verrà visualizzata o verrà richiesto di immettere un nuovo PIN o una nuova password.

    ![Immissione di PIN o password](./media/and-enroll-6-PIN-native.png)

13.  Se si usa un dispositivo Samsung Knox, toccare **Conferma** per visualizzare un messaggio che conferma la registrazione del dispositivo. Se si usa un dispositivo Android nativo, viene visualizzata semplicemente la schermata seguente che conferma la registrazione del dispositivo.

    ![Informativa sulla privacy di Samsung KNOX](./media/and-enroll-7-knox-privacy-policy.png)

    Questa schermata indica che dispositivo è in fase di registrazione.

    ![Schermata di registrazione in corso del dispositivo](./media/and-enroll-8-device-enrolling.png)

14. Quando viene visualizzata la schermata **Configurazione dell'accesso aziendale** toccare **CONTINUA**. Se viene visualizzato un messaggio che indica che il dispositivo non è conforme, seguire le istruzioni per risolvere il problema e toccare **CONTINUA**.

    ![Schermata di configurazione dell'accesso aziendale](./media/and-enroll-9-comp-access-setup.png)  

11. Nella schermata **Configurazione dell'accesso aziendale completato** toccare **FINE**. Il dispositivo è ora registrato.

    ![Schermata di configurazione dell'accesso aziendale completata](./media/and-enroll-10-comp-access-setup-complete.png)

Prima di installare app aziendali, andare in **Impostazioni**&gt;**Sicurezza** e attivare **Origini sconosciute**. Se non si attiva questa opzione prima di installare le app, viene visualizzato un messaggio che indica che l'installazione è bloccata. per motivi di sicurezza che impediscono di installare nel dispositivo app ottenute da origini sconosciute. È possibile toccare **Impostazioni** nella finestra di dialogo di errore per visualizzare l'opzione **Origini sconosciute**.

Serve ancora assistenza? Contattare l'amministratore IT (accedere al [sito Web del portale aziendale](http://portal.manage.microsoft.com) per informazioni sui contatti) oppure scrivere al team Microsoft Android all'indirizzo wintunedroidfbk@microsoft.com.



<!--HONumber=Oct16_HO2-->


