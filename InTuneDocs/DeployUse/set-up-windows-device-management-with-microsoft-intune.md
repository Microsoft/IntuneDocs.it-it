---
title: Configurare la gestione dei dispositivi Windows con Microsoft Intune | Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per i PC Windows, inclusi i dispositivi Windows 10, con Microsoft Intune.
keywords: 
author: staciebarker
manager: stabar
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3f28cce75626df1115283dc98547adcb97ee1cb4
ms.openlocfilehash: 9929294dd93e7bad47e6674ccafab0c036a1f89c


---

# <a name="set-up-windows-device-management"></a>Configurare la gestione dei dispositivi Windows

L'amministratore di Intune può abilitare la registrazione e la gestione per i PC Windows in due modi:

- **[Registrazione automatica con Azure Active Directory](#azure-active-directory-enrollment)**: gli utenti Windows 10 e Windows 10 Mobile registrano i propri dispositivi aggiungendo un account aziendale o dell'istituto di istruzione al dispositivo
- **[Registrazione con il portale aziendale](#company-portal-app-enrollment)**: gli utenti Windows 8.1 e versioni successive registrano i propri dispositivi scaricando e installando l'app Portale aziendale e quindi immettendo le credenziali dell'account aziendale o dell'istituto di istruzione nell'app.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-company-portal-app-enrollment"></a>Configurare l'app Portale aziendale
È possibile consentire agli utenti di installare e registrare i propri dispositivi tramite l'app Portale aziendale di Intune. Se si creano record CNAME DNS, gli utenti potranno connettersi e registrarsi in Intune senza immettere un nome server.

1. **Configurare Intune**<br>
Se non lo si è già fatto, preparare la gestione di dispositivi mobili [impostando l'autorità di gestione di dispositivi mobili (MDM, Mobile Device Management)](prerequisites-for-enrollment.md#set-mobile-device-management-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2. **Creare record CNAME** (facoltativo)<br>Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

    Se si dispone di un CNAME in DNS che reindirizza EnterpriseEnrollment.contoso.com a manage.microsoft.com, si consiglia di sostituirlo con un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com. Questa modifica è consigliata, perché l'endpoint manage.microsoft.com è deprecato per le registrazioni in una versione futura.

    I record di risorse CNAME devono contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

  `EnterpriseRegistration.windows.net`: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati in Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

  Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

3.  **Verificare i record CNAME**<br>Nella [console di amministrazione di Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

  ![Finestra di dialogo della gestione dei dispositivi Windows](../media/enroll-intune-winenr.png)

4.  **Passaggi facoltativi**<br>Il passaggio **Aggiungi chiave di sideload** non è necessario per Windows 10. Il passaggio **Caricare il certificato di firma codice** è necessario solo se si prevede di distribuire ai dispositivi app line-of-business (LOB) non disponibili da Windows Store.

6.  **Informare gli utenti della modalità di registrazione dei dispositivi e di cosa aspettarsi dopo l'introduzione dei dispositivi nella gestione.**

    Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](../enduser/enroll-your-device-in-intune-windows.md).

    Per altre informazioni sulle attività dell'utente finale, vedere gli articoli seguenti:
      - [Informazioni sull'uso di Microsoft Intune per gli utenti finali](what-to-tell-your-end-users-about-using-microsoft-intune.md)
      - [Linee guida per utenti finali per i dispositivi Windows](../enduser/using-your-windows-device-with-intune.md)

### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md)



<!--HONumber=Nov16_HO3-->


