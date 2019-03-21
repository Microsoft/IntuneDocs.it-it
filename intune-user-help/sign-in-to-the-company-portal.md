---
title: Come accedere all'app del portale aziendale | Microsoft Docs
description: Informazioni su come accedere all'app Portale aziendale su più piattaforme.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 370d6372cf3df2ff807069fe8d54f30da23e7ba2
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "55842610"
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>Come accedere all'app del portale aziendale? <!--User Story 1132123-->

L'app del portale aziendale consente di accedere alle risorse aziendali, ad esempio alla posta elettronica e alle app aziendali. Esistono due metodi principali per accedere al portale aziendale:

* Usando l'indirizzo di posta elettronica aziendale e la password
* Eseguendo l'accesso da un altro dispositivo

Sebbene le immagini seguenti si riferiscano a iOS, il processo è praticamente identico per i dispositivi Android e Windows.

## <a name="signing-in-with-your-email-address-and-password"></a>Accesso con l'indirizzo di posta elettronica e la password

1. Aprire l'app del portale aziendale nel dispositivo e toccare **Accedi**.

   ![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Il testo "Ottenere l'accesso alle risorse dell'organizzazione e mantenerle sicure" e il pulsante "Accedi" sono visualizzati sotto. Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)

   Se l'app del portale aziendale non è disponibile, vedere le istruzioni per installarla e scaricarla per [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) o [Android](install-the-company-portal-app-android.md).

2. Immettere l'**account aziendale o dell'istituto di istruzione** e toccare **Avanti**.

   ![Viene chiesto all'utente di indicare solo l'indirizzo di posta elettronica anziché l'indirizzo di posta elettronica e la password nella stessa schermata.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Immettere la password e toccare **Accedi**.

   ![La password verrà richiesta all'utente dopo che l'indirizzo di posta elettronica è stato accettato.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. Dopo che il portale aziendale ha accettato l'accesso, viene eseguito l'accesso ed è possibile iniziare ad accedere alle risorse aziendali.   

   ![Terminato il processo di autenticazione, l'app portale aziendale esegue l'accesso, visualizzando una barra di caricamento.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="signing-in-with-certificate-based-authentication"></a>Accesso con l'autenticazione basata su certificati

1.  Aprire l'app Portale aziendale nel dispositivo.

2.  Immettere l'**Account aziendale o dell'istituto di istruzione**.

3.  Toccare il collegamento **Sign in with a certificate** (Accedi con un certificato).

4.  Toccare **Continua** per usare il certificato.

## <a name="signing-in-from-another-device"></a>Eseguendo l'accesso da un altro dispositivo

Se non si usa una password per accedere alle risorse aziendali, è possibile usare un altro dispositivo per confermare la propria identità e i propri livelli di accesso. Se la società usa smart card per accedere ai computer, è probabile che sia necessario accedere con un altro dispositivo.

1. Anziché immettere l'indirizzo di posta elettronica, selezionare il collegamento **Accesso da un altro dispositivo** sotto la casella di testo della posta elettronica.

   ![La pagina di accesso del portale aziendale chiede all'utente di immettere l'indirizzo di posta elettronica.  Il pulsante "Avanti" e il collegamento "Accesso da un altro dispositivo" sono visualizzati sotto. È incluso anche il collegamento "Problemi di accesso all'account?" Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Si riceve un codice univoco e monouso per accedere al portale aziendale.

   ![Viene indicato come passare alla pagina https://microsoft.com/devicelogin con un passcode univoco dal computer di lavoro, quindi come usare il codice per l'accesso.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. Nell'altro dispositivo aprire il browser e passare a [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin) per immettere il codice.

   ![Un'immagine del browser dell'utente nel computer di lavoro anziché nell'app portale aziendale. Nella pagina "Accesso dispositivo" visualizzata viene chiesto all'utente di immettere il codice ricevuto nell'app portale aziendale.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Dopo che la pagina **Accesso dispositivo** ha verificato il codice, selezionare __Continua__ per consentire al portale aziendale di accedere all'altro dispositivo.

   ![L'utente ha immesso il codice univoco nel campo e il sito "Accesso dispositivo" ha chiesto di confermare che il portale aziendale di Intune è l'app corretta per la ricezione dell'autorizzazione ad accedere.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. Dopo la verifica del codice, è possibile chiudere la finestra.

   ![Una pagina di conferma indica che l'utente ha eseguito l'accesso all'app portale aziendale sul proprio dispositivo e che questa pagina può essere chiusa.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. Nel dispositivo originale l'app del portale aziendale inizia l'accesso.

   ![Dopo aver completato il processo di autenticazione, l'app del portale aziendale esegue l'accesso visualizzando una barra di caricamento.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://go.microsoft.com/fwlink/?linkid=2010980).
