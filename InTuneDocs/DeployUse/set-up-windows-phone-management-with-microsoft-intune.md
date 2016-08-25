---
title: Configurare la gestione di Windows Phone e Windows 10 Mobile | Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per i dispositivi Windows 10 Mobile o Windows Phone con Microsoft Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06d6c8ce97ba6a259055e94f0eba87f7c5a96531
ms.openlocfilehash: 344f1cf4367deb12288f9c361e043d345f9846bb


---


# Configurare la gestione di Windows Phone e Windows 10 Mobile con Microsoft Intune
Per informazioni su come configurare il dispositivo Windows, vedere [qui](../enduser/using-your-windows-device-with-intune.md).

Prima di poter gestire dispositivi Windows 10 Mobile o Windows Phone con Microsoft Intune, questi devono essere in grado di comunicare con Intune. Per semplificare l'operazione, è possibile creare un record DNS in modo che gli utenti non debbano immettere l'indirizzo del server. La procedura descritta di seguito illustra come semplificare la registrazione per gli utenti.  

Per la maggior parte degli scenari, gli utenti possono installare l'app Portale aziendale da Windows Store. Se si gestiscono i dispositivi Windows Phone 8.0 o per distribuire il Portale aziendale nei dispositivi Windows Phone, è necessario anche scaricare e firmare l'app Portale aziendale. Vedere [Set up device management for Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md) (Configurazione della gestione di Windows Phone 8.0).

1.  **Configurare Intune** Se non è stato già fatto, preparare la gestione dei dispositivi mobili [impostando l'autorità di gestione dei dispositivi mobili](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority) come **Microsoft Intune** e configurando MDM.

2.  **Impostare un alias DNS per l'indirizzo del server di registrazione** (facoltativo)

    La creazione di un alias DNS (tipo di record CNAME) consente agli utenti di registrare facilmente i propri dispositivi. Anche se la voce DNS CNAME è facoltativa per la registrazione dei dispositivi Windows, è consigliabile creare uno o più record quando necessario, in modo da semplificare le operazioni durante il processo di registrazione dei dispositivi Windows. Se non si trova alcun record CNAME, all'utente viene richiesto di immettere manualmente il nome del server MDM.

  1.  Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web della società è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a manage.microsoft.com. Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. I record di risorse CNAME devono contenere le informazioni seguenti:

      |TYPE|Nome host|Punta a|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

      La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

      **EnterpriseEnrollment-s.manage.microsoft.com**: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

      **EnterpriseRegistration.windows.net**: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati con Azure Active Directory tramite account aziendale o dell'istituto di istruzione

    2.  Nella [console di amministrazione di Intune](http://manage.microsoft.com) fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone**.

      ![Configurare la gestione dei dispositivi mobili per la finestra di dialogo Windows](../media/windows-device-enrollment.png)

    3.  Digitare l'URL del dominio verificato del sito Web aziendale nella casella **Specificare un nome di dominio verificato** e fare clic su **Verifica il rilevamento automatico**.

    4.  Gli utenti dovranno sapere come registrare i propri dispositivi e cosa aspettarsi una volta che vengono introdotti nella gestione.
        - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)
        - [Uso del dispositivo Windows con Intune](../enduser/using-your-windows-device-with-intune.md)



Non è necessario alcun intervento aggiuntivo a meno che non venga distribuito il Portale aziendale nei dispositivi.  I passaggi 2 e 3 nella console di amministrazione possono essere ignorati.



<!--HONumber=Aug16_HO1-->


