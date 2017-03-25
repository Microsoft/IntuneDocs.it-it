---
title: Configurare la gestione dei dispositivi Windows con Microsoft Intune | Documentazione Microsoft
description: Abilitare la gestione di dispositivi mobili (MDM) per i dispositivi Windows con Microsoft Intune.
keywords: 
author: NathBarn
manager: angrobe
ms.date: 03/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9a18c0fe-9f03-4e84-a4d0-b63821bf5d25
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e76d66768ac58df25313e102b7f60d2bc7bbc59b
ms.openlocfilehash: f66bc5a26f137f62defef4a83a36b22247be4ec1
ms.lasthandoff: 03/22/2017


---

# <a name="set-up-windows-device-management"></a>Configurare la gestione dei dispositivi Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per configurare la registrazione per i dispositivi Windows, usare uno dei metodi seguenti:

- [**Registrazione automatica di Windows 10 e Windows 10 Mobile con Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Questo metodo è applicabile solo ai dispositivi Windows 10 e Windows 10 Mobile.
 -  Per usare questo metodo, è necessario disporre di Azure Active Directory Premium. In caso contrario, usare il metodo di registrazione per Windows 8.1 e Windows Phone 8.1.
 -  Se si sceglie di non abilitare la registrazione automatica, usare il metodo di registrazione per Windows 8.1 e Windows Phone 8.1.


- [**Registrazione di Windows 8.1 e Windows Phone 8.1 configurando CNAME**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - È necessario usare questo metodo per registrare i dispositivi Windows 8.1 e Windows Phone 8.1.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Impostare la registrazione di Windows 8.1 e Windows Phone 8.1 configurando CNAME
È possibile consentire agli utenti di installare e registrare i propri dispositivi tramite il portale aziendale di Intune. Se si creano record CNAME DNS, gli utenti potranno connettersi e registrarsi in Intune senza immettere un nome server.

### <a name="step-1-set-up-intune"></a>Passaggio 1: Impostare Intune

Se non lo si è già fatto, preparare la gestione di dispositivi mobili [impostando l'autorità di gestione di dispositivi mobili (MDM, Mobile Device Management)](prerequisites-for-enrollment.md#step-2-set-mdm-authority), ad esempio **Microsoft Intune**, e configurando MDM.

### <a name="step-2-create-cnames-optional"></a>Passaggio 2: Creare CNAME (facoltativo)

Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.


   Anche se la creazione di record CNAME DNS è facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record CNAME, viene richiesto all'utente di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.com.

   I record di risorse CNAME devono contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

  `EnterpriseRegistration.windows.net`: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati in Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

  Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

### <a name="step-3-verify-cname"></a>Passaggio 3: Verificare CNAME

Nella [console di amministrazione di Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

### <a name="step-4-tell-your-users-how-to-enroll-their-devices-and-what-to-expect-after-theyre-brought-into-management"></a>Passaggio 4: Informare gli utenti sulla modalità di registrazione dei dispositivi e su cosa accade dopo il loro inserimento nella gestione.

   Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows).

   Per altre informazioni sulle attività dell'utente finale, vedere [Come informare gli utenti finali su Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) e [Uso del dispositivo Windows con Intune](https://docs.microsoft.com/intune-user-help/using-your-windows-device-with-intune).

### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md)

