---
title: Configurare la gestione dei dispositivi Windows con Microsoft Intune | Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per i PC Windows, inclusi i dispositivi Windows 10, con Microsoft Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: fae2aa496ec38d9ddc2cb6800bed10ccb32fd154


---

# Configurare la gestione dei dispositivi Windows
Per informazioni su come configurare il dispositivo Windows, vedere [qui](../enduser/using-your-windows-device-with-intune.md).

Con Intune è possibile abilitare la registrazione di dispositivi PC Windows BYOD (Bring Your Own Device) per concedere l'accesso alla posta elettronica e alle app aziendali. Usato con Azure Active Directory, offre anche un modo veloce e no-touch per gestire i nuovi dispositivi Windows 10 e ottenere l'accesso alle risorse aziendali senza dover ricreare l'immagine del computer. Dopo la registrazione, gli utenti possono accedere mentre ai dispositivi possono essere assegnati criteri, app e impostazioni mediante la console di amministrazione di Intune. È anche possibile [configurare la gestione di Windows Phone con Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md) o [gestire i computer con software client di Intune](manage-windows-pcs-with-microsoft-intune.md) tramite il client Intune.

La creazione di DNS CNAME consente agli utenti di connettersi e registrarsi in Intune senza immettere un nome server.

### Configurare la gestione dei dispositivi Windows

  1.  Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. Anche se la voce DNS CNAME è facoltativa per la registrazione dei dispositivi Windows, è consigliabile creare uno o più record quando necessario, in modo da semplificare le operazioni durante il processo di registrazione dei dispositivi Windows. Se non si trova alcun record CNAME, all'utente viene richiesto di immettere manualmente il nome del server MDM.

  Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. Il record di risorse CNAME deve contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

  La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

  **EnterpriseEnrollment-s.manage.microsoft.com**: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

  **EnterpriseRegistration.windows.net**: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati con Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  2.  Nella [console di amministrazione di Intune](http://manage.microsoft.com) fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows**.
  ![Finestra di dialogo della gestione dei dispositivi Windows](../media/enroll-intune-winenr.png)

  3.  Digitare l'URL del dominio verificato del sito Web aziendale nella casella **Specificare un nome di dominio verificato** e fare clic su **Verifica il rilevamento automatico**.

  4.  Gli utenti dovranno sapere come registrare i propri dispositivi e cosa aspettarsi una volta che vengono introdotti nella gestione.
      - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Uso del dispositivo Windows con Intune](../enduser/using-your-windows-device-with-intune.md)

### Vedere anche
[Prepararsi alla registrazione dei dispositivi in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


