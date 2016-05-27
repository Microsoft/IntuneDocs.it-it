---
# required metadata

title: Configurare la gestione di Windows 10 Mobile e Windows Phone con Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Configurare la gestione di Windows Phone e Windows 10 Mobile con Microsoft Intune
Prima di poter gestire dispositivi Windows 10 Mobile o Windows Phone con Microsoft Intune, questi devono essere in grado di comunicare con Intune. Per semplificare l'operazione, è possibile creare un record DNS in modo che gli utenti non debbano immettere l'indirizzo del server. La procedura descritta di seguito illustra come semplificare la registrazione per gli utenti.  

Per la maggior parte degli scenari, gli utenti possono installare l'app Portale aziendale da Windows Store. Se si gestiscono i dispositivi Windows Phone 8.0 o per distribuire il Portale aziendale nei dispositivi Windows Phone, è necessario anche scaricare e firmare l'app Portale aziendale. Vedere l'articolo relativo alla [configurazione della gestione di Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

1.  **Configurare Intune**
    Se non è stato già fatto, preparare la gestione di dispositivi mobili (MDM) [impostando l'autorità di gestione di dispositivi mobili](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2.  **Impostare un alias DNS per l'indirizzo del server di registrazione** (facoltativo)

    La creazione di un alias DNS (tipo di record CNAME) consente agli utenti di registrare facilmente i propri dispositivi. Se non viene creato un alias DNS, gli utenti devono

  1.  Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web della società è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a manage.microsoft.com. Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. I record di risorse CNAME devono contenere le informazioni seguenti:

      |TYPE|Nome host|Punta a|TTL|
      |--------|-------------|-------------|-------|
      |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
      |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

      La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

      **EnterpriseEnrollment-s.manage.microsoft.com**: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

      **EnterpriseRegistration.windows.net**: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati con Azure Active Directory tramite account aziendale o dell'istituto di istruzione

    2.  Nella [console di amministrazione di Intune](http://manage.microsoft.com), fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone**.

      ![Configurare la gestione dei dispositivi mobili per la finestra di dialogo Windows](../media/windows-device-enrollment.png)

    3.  Digitare l'URL del dominio verificato del sito Web aziendale nella casella **Specificare un nome di dominio verificato** e fare clic su **Verifica il rilevamento automatico**.



Non è necessario alcun intervento aggiuntivo a meno che non venga distribuito il Portale aziendale nei dispositivi.  I passaggi 2, 3 e 4 nella console di amministrazione possono essere tranquillamente ignorati.


<!--HONumber=May16_HO1-->


