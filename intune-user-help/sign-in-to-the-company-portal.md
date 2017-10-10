---
title: Come accedere all'app del portale aziendale | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope: User help
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ca6d811d884b5405bdb4e5f096366c123d8e00d1
ms.sourcegitcommit: db7a7bbead3a3fa78c4d643607f709a2909eb608
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/28/2017
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>Come accedere all'app del portale aziendale? <!--User Story 1132123-->

L'app del portale aziendale consente di accedere alle risorse aziendali, ad esempio alla posta elettronica e alle app aziendali. Esistono due metodi principali per accedere al portale aziendale:

* Usando l'indirizzo di posta elettronica aziendale e la password
* Eseguendo l'accesso da un altro dispositivo

Sebbene le immagini seguenti si riferiscano a iOS, il processo è praticamente identico per i dispositivi Android e Windows.

## <a name="signing-in-with-your-email-address-and-password"></a>Accesso con l'indirizzo di posta elettronica e la password

1. Aprire l'app del portale aziendale nel dispositivo e toccare **Accedi**.

  ![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](/intune/media/cp_ios_aad_signin_after_1704_001.png)

  Se l'app del portale aziendale non è disponibile, vedere le istruzioni per installarla e scaricarla per [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) o [Android](install-the-company-portal-app-android.md).

2. Immettere l'**Account aziendale o dell'istituto di istruzione**.

  ![Viene chiesto all'utente di indicare solo l'indirizzo di posta elettronica anziché l'indirizzo di posta elettronica e la password nella stessa schermata.](/intune/media/cp_ios_aad_signin_after_1704_002.png)

3. Attendere qualche istante che l'indirizzo di posta elettronica venga accettato e quindi immettere la password.

  ![La password verrà richiesta all'utente dopo che l'indirizzo di posta elettronica è stato accettato.](/intune/media/cp_ios_aad_signin_after_1704_003.png)

4. Dopo che il portale aziendale ha accettato l'accesso, viene eseguito l'accesso ed è possibile iniziare ad accedere alle risorse aziendali.   

  ![Terminato il processo di autenticazione, l'app portale aziendale esegue l'accesso, visualizzando una barra di caricamento.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="signing-in-from-another-device"></a>Eseguendo l'accesso da un altro dispositivo

Se non si usa una password per accedere alle risorse aziendali, è possibile usare un altro dispositivo per confermare la propria identità e i propri livelli di accesso. Se la società usa smart card per accedere ai computer, è probabile che sia necessario accedere con un altro dispositivo.

1. Anziché immettere l'indirizzo di posta elettronica, selezionare il collegamento **Accesso da un altro dispositivo** sotto la casella di testo della posta elettronica.

  ![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

2. Si riceve un codice univoco e monouso per accedere al portale aziendale.

  ![Viene indicato come passare alla pagina aka.ms/devicelogin con un passcode univoco dal computer di lavoro, quindi come usare il codice per l'accesso.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

3. Nell'altro dispositivo aprire il browser e passare a [https://aka.ms/devicelogin](https://aka.ms/devicelogin) per immettere il codice.

  ![Un'immagine del browser dell'utente nel computer di lavoro anziché nell'app portale aziendale. Nella pagina "Accesso dispositivo" visualizzata viene chiesto all'utente di immettere il codice ricevuto nell'app portale aziendale.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Dopo che la pagina **Accesso dispositivo** ha verificato il codice, selezionare __Continua__ per consentire al portale aziendale di accedere all'altro dispositivo.

  ![L'utente ha immesso il codice univoco nel campo e il sito "Accesso dispositivo" ha chiesto di confermare che il portale aziendale di Intune è l'app corretta per la ricezione dell'autorizzazione ad accedere.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. Dopo la verifica del codice, è possibile chiudere la finestra.

  ![Una pagina di conferma indica che l'utente ha eseguito l'accesso all'app portale aziendale sul proprio dispositivo e che questa pagina può essere chiusa.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. Nel dispositivo originale l'app del portale aziendale inizia l'accesso.

  ![Dopo aver completato il processo di autenticazione, l'app del portale aziendale esegue l'accesso visualizzando una barra di caricamento.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com).
