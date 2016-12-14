---
title: Configurare la gestione di Windows Phone e Windows 10 Mobile | Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per i dispositivi Windows 10 Mobile o Windows Phone con Microsoft Intune.
keywords: 
author: staciebarker
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f5615051-2dd1-453b-9872-d3fdcefb2cb8
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c59707ba2967b069dc30aee71d2642e91d71b23b
ms.openlocfilehash: 3141d4b2ad1a21e2ac5ba7b6cafb74f567d07f7a


---


# <a name="set-up-windows-phone-and-windows-10-mobile-management-with-microsoft-intune"></a>Configurare la gestione di Windows Phone e Windows 10 Mobile con Microsoft Intune

L'amministratore di Intune può abilitare la registrazione e la gestione per i dispositivi Windows 10 Mobile e Windows Phone in due modi:

- **[Registrazione automatica con Azure Active Directory](#azure-active-directory-enrollment)**: gli utenti Windows 10 e Windows 10 Mobile registrano i propri dispositivi aggiungendo un account aziendale o dell'istituto di istruzione al dispositivo
- **[Registrazione con il portale aziendale](#company-portal-app-enrollment)**: gli utenti Windows Phone 8.1 e versione successiva registrano i propri dispositivi scaricando e installando l'app Portale aziendale e quindi immettendo le credenziali dell'account aziendale o dell'istituto di istruzione nell'app.


[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="company-portal-app-enrollment"></a>Registrare l' app del portale aziendale
È possibile consentire agli utenti di installare e registrare i propri dispositivi tramite l'app Portale aziendale di Intune. Se si creano record CNAME DNS, gli utenti potranno connettersi e registrarsi in Intune senza immettere un nome server.

1.  **Configurare Intune**<br>Se non lo si è già fatto, preparare la gestione di dispositivi mobili [impostando l'autorità di gestione di dispositivi mobili (MDM, Mobile Device Management)](prerequisites-for-enrollment.md#step-2-set-mdm-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2.  **Creare record CNAME** (facoltativo)<br>Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

    Anche se la creazione di record CNAME DNS è facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record CNAME per la registrazione, agli utenti viene richiesto di immettere manualmente il nome del server MDM https://manage.microsoft.com.

    Se si dispone di un CNAME in DNS che reindirizza EnterpriseEnrollment.contoso.com a manage.microsoft.com, si consiglia di sostituirlo con un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com. Questa modifica è consigliata, perché l'endpoint manage.microsoft.com è deprecato per le registrazioni in una versione futura.

    Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. Il record di risorse CNAME deve contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

  `EnterpriseRegistration.windows.net`: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati in Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

  Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

3.  **Verificare i record CNAME**<br>Nella [console di amministrazione di Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

    ![Configurare la gestione dei dispositivi mobili per la finestra di dialogo Windows](../media/windows-phone-enrollment.png)

4.  **Passaggi facoltativi**<br>Il passaggio **Aggiungi chiave di sideload** non è necessario per Windows 10. Il passaggio **Caricare il certificato di firma codice** è necessario solo se si prevede di distribuire ai dispositivi app line-of-business non disponibili da Windows Store.

5.  **Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali.**

    Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](../enduser/enroll-your-device-in-intune-windows.md). È inoltre possibile indirizzare gli utenti a [Quali sono i dettagli visibili all'amministratore IT quando si registra il dispositivo in Intune?](../enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md).

    Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:
    - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [Linee guida per utenti finali per i dispositivi Windows](../enduser/using-your-windows-device-with-intune.md)

Non è necessario alcun intervento aggiuntivo a meno che non venga distribuito il Portale aziendale nei dispositivi.  I passaggi 2 e 3 nella console di amministrazione possono essere ignorati.



<!--HONumber=Dec16_HO2-->


