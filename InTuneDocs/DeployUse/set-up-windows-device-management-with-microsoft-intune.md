---
title: Configurare la gestione dei dispositivi Windows con Microsoft Intune | Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per i PC Windows, inclusi i dispositivi Windows 10, con Microsoft Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: 149508942b89b15308591e17723884add3ac78ae


---

# Configurare la gestione dei dispositivi Windows

In qualità di amministratore di Intune, è possibile abilitare la registrazione e la gestione per i PC Windows in due modi:

- **[Registrazione automatica con Azure AD](#azure-active-directory-enrollment)**: gli utenti Windows 10 e Windows 10 Mobile registrano i propri dispositivi aggiungendo un account aziendale o dell'istituto di istruzione al dispositivo
- **[Registrazione con il portale aziendale](#company-portal-app-enrollment)**: i dispositivi Windows 8.1 e versione successiva vengono registrati scaricando e installando l'app del portale aziendale e quindi immettendo le credenziali dell'account aziendale o dell'istituto di istruzione nell'app.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## Configurare la registrazione dell' app del portale aziendale
È possibile consentire agli utenti di registrare i propri dispositivi mediante l'installazione e la registrazione dei dispositivi con l'app del portale aziendale di Intune. La creazione di DNS CNAME consente agli utenti di connettersi e registrarsi in Intune senza immettere un nome server.

1. **Configurare Intune**<br>
Se non è stato già fatto, preparare la gestione di dispositivi mobili (MDM) [impostando l'autorità di gestione di dispositivi mobili](prerequisites-for-enrollment.md#set-mobile-device-management-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2. **Creare record CNAME** (facoltativo)<br>Creare record di risorse DNS **CNAME** per il dominio aziendale per semplificare la registrazione. Anche se la creazione di record DNS CNAME è facoltativa, la creazione di record CNAME semplifica la registrazione per gli utenti. Se non viene trovato alcun record CNAME per la registrazione, agli utenti viene richiesto di immettere manualmente il nome del server MDM `https://manage.microsoft.com`.  Il record di risorse CNAME deve contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

  `EnterpriseEnrollment-s.manage.microsoft.com` : supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

  `EnterpriseRegistration.windows.net` : supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati con Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

  Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

3.  **Verificare i record CNAME**<br>Nella [console di amministrazione di Intune](http://manage.microsoft.com) fare clic su **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows**. Digitare l'URL del dominio verificato del sito Web aziendale nella casella **Specificare un nome di dominio verificato** e fare clic su **Verifica il rilevamento automatico**.

  ![Finestra di dialogo della gestione dei dispositivi Windows](../media/enroll-intune-winenr.png)

4.  **Passaggi facoltativi**<br>Il passaggio **Aggiungi chiave di sideload** non è necessario per Windows 10. Il passaggio **Caricare il certificato di firma codice** è necessario solo se si prevede di distribuire le app line-of-business ai dispositivi non disponibili da Windows Store. [Altre informazioni](set-up-windows-phone-8.0-management-with-microsoft-intune.md)

6.  **Informare gli utenti**<br>È necessario informare gli utenti riguardo la modalità di registrazione dei dispositivi e riguardo cosa aspettarsi una volta che questi vengono introdotti nella gestione:
      - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Uso del dispositivo Windows con Intune](../enduser/using-your-windows-device-with-intune.md)

### Vedere anche
[Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Sep16_HO4-->


