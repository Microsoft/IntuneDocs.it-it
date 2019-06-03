---
title: Registrare un dispositivo Android in Portale aziendale Intune | Microsoft Docs
description: Descrive come registrare un dispositivo Android in Portale aziendale Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0ed3a002-7533-4001-ae24-e10b64b66620
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 736b1d891207a19f281aa1127975de1a55889e8b
ms.sourcegitcommit: d258bcf6716c8a2589d3f8dada819905ee80f233
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2019
ms.locfileid: "66197039"
---
# <a name="enroll-your-device-with-company-portal"></a>Registrare il dispositivo in Portale aziendale  
Registrare il dispositivo Android personale o aziendale per ottenere accesso sicuro alla posta elettronica, alle app e ai dati aziendali. Il portale aziendale supporta i dispositivi Android, incluso Samsung Knox, che eseguono Android 4.4 e versioni successive.  
</br>
> [!VIDEO https://www.youtube.com/embed/k0Q_sGLSx6o?rel=0]

> [!NOTE]
> Samsung Knox è un tipo di sicurezza che alcuni dispositivi Samsung usano per fornire protezione aggiuntiva oltre all'offerta prevista per i dispositivi Android nativi. Per determinare se il dispositivo è di tipo Samsung Knox, passare a **Impostazioni** > **Informazioni sul dispositivo**. Se non viene visualizzata l'indicazione **Versione Knox**, significa che il dispositivo è un dispositivo Android nativo.

## <a name="enroll-device"></a>Registrare il dispositivo  
Assicurarsi di [installare l'app Portale aziendale Intune gratuita da Google Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal). 

Durante la registrazione potrebbe essere richiesto di scegliere la categoria che descrive meglio come viene usato il dispositivo. Il team di supporto tecnico aziendale usa questa risposta per controllare le app a cui è possibile accedere.  

1. Aprire l'app Portale aziendale.  

3. Nella **schermata iniziale** del portale aziendale toccare **Accedi** e quindi accedere con l'account aziendale o dell'istituto di istruzione.

   ![Schermata iniziale dell'app Portale aziendale per Android, che chiede all'utente di accedere con l'account aziendale o dell'istituto di istruzione, segnalando inoltre che gli account Microsoft e altri account personali non sono accettati.](./media/and-enroll-0-welcome-screen.png)   

4. Se viene richiesto di accettare i termini e le condizioni dell'organizzazione, toccare **ACCETTA**. Questa schermata potrebbe essere leggermente diversa dalla schermata di esempio riportata di seguito. 

   ![android-company-portal-sign-in](./media/and-enroll-3-accept-terms.png)

5. Accedere all'app Portale aziendale usando l'account e la password aziendali o dell'istituto di istruzione e toccare **Accedi**.

   ![android-company-portal-sign-in](./media/and-enroll-2-cp-sign-in.png)

6. Nella schermata **Configurazione dell'accesso aziendale** toccare **CONTINUA**.

   ![Schermata di configurazione dell'accesso aziendale](/intune/media/android_cp_enroll_01_1709_new.png)

   > [!NOTE]
   > I triangoli gialli non indicano che si è già verificato un errore, ma che alcuni passaggi del processo di registrazione devono ancora essere completati.

7. Rivedere l'elenco di cosa può e di cosa non può essere visualizzato sul dispositivo dal personale del supporto tecnico aziendale e quindi toccare **CONTINUA**.

   ![Impostazioni di privacy](/intune/media/android_cp_enroll_02_after_1710.png)

8. Nella schermata **Operazioni successive** leggere cosa accade durante la registrazione e quindi toccare **REGISTRA**.

   ![Operazioni successive](/intune/media/android_cp_enroll_03_after_1710.png)

9. Se si usa Android 6.0 o versione successiva, eseguire questo passaggio. In caso contrario, andare al passaggio successivo.

   Se il supporto tecnico aziendale ha configurato criteri specifici, possono essere visualizzati i messaggi seguenti:
   - **Allow Company Portal to make and manage phone calls? (Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?)**

     ![android-company-portal-sign-in](./media/and-enroll-3a-allow-phone-access.png)

   Se viene visualizzato questo messaggio, toccare **CONSENTI**. È consigliabile scegliere questa opzione perché **Microsoft non effettua né gestisce le chiamate telefoniche**. Il testo del messaggio è controllato da Google, quindi Microsoft non può modificarlo. Quando si consente l'accesso, il dispositivo può inviare il codice IMEI (International Mobile Station Equipment Identity) a Intune. Il codice IMEI è un numero, simile a un numero di serie, che identifica in modo univoco un dispositivo mobile.

   Se si nega l'accesso, il messaggio verrà visualizzato nuovamente al successivo accesso al portale aziendale. Per disattivare i messaggi futuri, selezionare **Non visualizzare più questo messaggio**. Per ripristinare l'autorizzazione all'accesso, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.  

   - **Allow Company Portal to access your contacts? (Consentire a Portale aziendale di accedere ai contatti?)**

     ![android-company-portal-sign-in](./media/and-enroll-3b-allow-contacts-access.png)

     Se viene visualizzato questo messaggio, toccare **CONSENTI**. È consigliabile scegliere questa opzione perché **Microsoft non può mai accedere ai contatti**. Il testo del messaggio è controllato da Google, quindi Microsoft non può modificarlo. Quando si concede l'accesso, si consente solo all'app Portale aziendale di creare, usare e gestire il proprio account aziendale.

     Se si nega l'accesso, il messaggio sarà di nuovo visualizzato quando si accederà di nuovo al Portale aziendale. È tuttavia possibile disattivare la visualizzazione futura dei messaggi selezionando la casella **Non visualizzare più questo messaggio**. Se si decide successivamente di consentire l'accesso, andare a **Impostazioni** &gt; **App** &gt; **Portale aziendale** &gt; **Autorizzazioni** &gt; **Telefono**, quindi attivare l'autorizzazione.

10. Nella schermata relativa all'**attivazione dell'amministratore del dispositivo** toccare **Attiva**.

    ![Schermata di attivazione dell'amministratore del dispositivo](./media/and-enroll-5-activate.png)

    Il ruolo di amministratore del dispositivo è un ruolo necessario all'app Portale aziendale per gestire il dispositivo. Consente all'amministratore di osservare determinati comportamenti, come il numero di tentativi di sblocco dello schermo, e di eseguire alcune azioni.    

    Microsoft non controlla questo messaggio ed è consapevole che la sua formulazione può sembrare piuttosto drastica. L'app Portale aziendale non può visualizzare solo le restrizioni e i diritti di accesso che sono rilevanti per l'organizzazione. Tutti i diritti vengono concessi contemporaneamente in questa schermata. Per domande specifiche sulla prassi adottata nella propria organizzazione e per altre informazioni, contattare il supporto tecnico aziendale tramite le informazioni sul contatto riportate nel [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).  

11. Seguire le istruzioni per immettere un PIN o una password. Se sul dispositivo è già stato impostato un PIN o una password, questa schermata non verrà visualizzata o verrà richiesto di immettere un nuovo PIN o una nuova password.  

    ![Immissione di PIN o password](./media/and-enroll-6-PIN-native.png)

12. Se si usa un dispositivo Samsung Knox, toccare **Conferma** per visualizzare un messaggio che conferma la registrazione del dispositivo. Se si usa un dispositivo Android nativo, viene visualizzata semplicemente la schermata seguente che conferma la registrazione del dispositivo.

    ![Informativa sulla privacy di Samsung Knox](./media/and-enroll-7-knox-privacy-policy.png)

    Questa schermata indica che dispositivo è in fase di registrazione.

    ![Schermata di registrazione in corso del dispositivo](./media/and-enroll-8-device-enrolling.png)

13. Quando viene visualizzata la schermata **Configurazione dell'accesso aziendale** toccare **CONTINUA**. Se viene visualizzato un messaggio che indica che il dispositivo non è conforme, seguire le istruzioni per risolvere il problema e toccare **CONTINUA**.

    ![Il dispositivo non è conforme, ma è registrato](/intune/media/android_cp_enroll_05_post_1709.png)

    ![Si verificano problemi di conformità del dispositivo che è necessario risolvere](/intune/media/android_cp_enroll_03_post_1709.png)

    È possibile trovare altre informazioni sui problemi riscontrati toccando le voci corrispondenti.

    ![Problemi di conformità del dispositivo espansi](/intune/media/android_cp_enroll_04_post_1709.png)

    ![Schermata di configurazione dell'accesso aziendale](./media/and-enroll-9d-comp-access-setup.png)  

14. Nella schermata **Configurazione dell'accesso aziendale completato** toccare **FINE**. Il dispositivo è ora registrato.

    ![Schermata di configurazione dell'accesso aziendale completata](./media/and-enroll-10-comp-access-setup-complete.png)

## <a name="next-steps"></a>Passaggi successivi  

Prima di installare app aziendali, assicurarsi di passare a **Impostazioni** > **Sicurezza** e attivare **Origini sconosciute**. Se non si attiva questa opzione prima di installare le app, viene visualizzato un messaggio che indica che l'installazione è bloccata. per motivi di sicurezza che impediscono di installare nel dispositivo app ottenute da origini sconosciute. È possibile toccare **Impostazioni** nella finestra di dialogo di errore per visualizzare l'opzione **Origini sconosciute**.  

> [!Note]
> Se la propria organizzazione usa software per la gestione delle spese per telecomunicazioni, sarà necessario eseguire alcuni passaggi aggiuntivi prima che la registrazione del dispositivo sia completata. Per altre informazioni, vedere [qui](enroll-your-device-with-telecom-expense-management-android.md).

Se si verifica un errore durante la registrazione del dispositivo in Intune, è possibile [inviare un messaggio di posta elettronica al supporto tecnico aziendale](send-logs-to-your-it-admin-by-email-android.md).  

Serve ancora assistenza? Contattare il supporto tecnico aziendale (accedere al [sito Web Portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980) per informazioni sul contatto) oppure scrivere al <a href="mailto:wintunedroidfbk@microsoft.com?subject=I'm having trouble with enrolling my Android device&body=Describe the issue you're experiencing here.">team Microsoft Android</a>.
