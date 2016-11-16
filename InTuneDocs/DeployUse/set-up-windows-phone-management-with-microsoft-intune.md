---
title: Configurare la gestione di Windows Phone e Windows 10 Mobile | Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per i dispositivi Windows 10 Mobile o Windows Phone con Microsoft Intune.
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0b4bf6aa6fa9d693c0458562e7fcb71fc8000bb4
ms.openlocfilehash: 46bd457af51d3fac513cfc36af1766e1e37222cd


---


# Configurare la gestione di Windows Phone e Windows 10 Mobile con Microsoft Intune

L'amministratore di Intune può abilitare la registrazione e la gestione per i dispositivi Windows 10 Mobile e Windows Phone in due modi:

- **[Registrazione automatica con Azure Active Directory](#azure-active-directory-enrollment)**: gli utenti Windows 10 e Windows 10 Mobile registrano i propri dispositivi aggiungendo un account aziendale o dell'istituto di istruzione al dispositivo
- **[Registrazione con il portale aziendale](#company-portal-app-enrollment)**: gli utenti Windows Phone 8.1 e versione successiva registrano i propri dispositivi scaricando e installando l'app Portale aziendale e quindi immettendo le credenziali dell'account aziendale o dell'istituto di istruzione nell'app.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Registrare l' app del portale aziendale
È possibile consentire agli utenti di installare e registrare i propri dispositivi tramite l'app Portale aziendale di Intune. Se si creano record CNAME DNS, gli utenti potranno connettersi e registrarsi in Intune senza immettere un nome server. Se si gestiscono i dispositivi Windows Phone 8.0 o per distribuire il Portale aziendale nei dispositivi Windows Phone, è necessario anche scaricare e firmare l'app Portale aziendale. Vedere [Set up device management for Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md) (Configurazione della gestione di Windows Phone 8.0).

1.  **Configurare Intune**<br>Se non lo si è già fatto, preparare la gestione di dispositivi mobili [impostando l'autorità di gestione di dispositivi mobili (MDM, Mobile Device Management)](prerequisites-for-enrollment.md#set-mobile-device-management-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2.  **Creare record CNAME** (facoltativo)<br>Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web della società è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a manage.microsoft.com. Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. Il record di risorse CNAME deve contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

  `EnterpriseEnrollment-s.manage.microsoft.com` : supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

  `EnterpriseRegistration.windows.net` : supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati con Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

  Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

3.  **Verificare i record CNAME**<br>Nella [console di amministrazione di Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

    ![Configurare la gestione dei dispositivi mobili per la finestra di dialogo Windows](../media/windows-phone-enrollment.png)

4.  **Passaggi facoltativi**<br>Il passaggio **Aggiungi chiave di sideload** non è necessario per Windows 10. Il passaggio **Caricare il certificato di firma codice** è necessario solo se si prevede di distribuire ai dispositivi app line-of-business (LOB) non disponibili da Windows Store. [Altre informazioni](set-up-windows-phone-8.0-management-with-microsoft-intune.md).

5.  **Informare gli utenti**<br>Gli utenti dovranno sapere come registrare i propri dispositivi e cosa aspettarsi dopo essere stati introdotti nella gestione.
    - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Uso del dispositivo Windows con Intune](../enduser/using-your-windows-device-with-intune.md)

Non è necessario alcun intervento aggiuntivo a meno che non venga distribuito il Portale aziendale nei dispositivi.  I passaggi 2 e 3 nella console di amministrazione possono essere ignorati.



<!--HONumber=Oct16_HO3-->


