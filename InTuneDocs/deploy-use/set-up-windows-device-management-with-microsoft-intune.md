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
ms.sourcegitcommit: 771aed4e1c57171183b9a9ea7d9e0f702dc1859c
ms.openlocfilehash: f6014c5500b05762d123b2285ef859d67382e402
ms.lasthandoff: 04/06/2017


---

# <a name="set-up-windows-device-management"></a>Configurare la gestione dei dispositivi Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per configurare la registrazione per i dispositivi Windows, usare uno dei metodi seguenti:

- [**Registrazione automatica di Windows 10 con Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Questo metodo è disponibile solo per i dispositivi Windows 10.
 -  Per usare questo metodo, è necessario disporre di Azure Active Directory Premium.
 -  Se si sceglie di non abilitare la registrazione automatica, usare il metodo di registrazione per Windows 8.1 e Windows Phone 8.1.

- [**Registrazione senza la funzionalità automatica di Azure AD Premium**](#enable-windows-enrollment-without-azure-ad-premium)
 - È necessario usare questo metodo per registrare i dispositivi Windows 8.1 e Windows Phone 8.1.
 - Se non si vuole usare Azure Active Directory (AD) Premium, è possibile eseguire questo metodo per i dispositivi Windows 8.1 e versioni successive.

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Abilitare la registrazione di Windows senza la registrazione automatica
È possibile consentire agli utenti di installare e registrare i propri dispositivi senza la registrazione automatica di Azure AD Premium. Dopo avere assegnato una licenza all'account degli utenti, è possibile aggiungere tale account a un dispositivo Windows e accettare di registrare il dispositivo nella gestione. Se si creano record CNAME DNS, gli utenti potranno connettersi e registrarsi in Intune senza immettere un nome server.

**Passaggio 1: Creare CNAME** (facoltativo)<br>
Creare record di risorse DNS CNAME per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

Anche se la creazione di record CNAME DNS è facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record CNAME, viene richiesto all'utente di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.com.

Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. Il record di risorse CNAME deve contenere le informazioni seguenti:

I record di risorse CNAME devono contenere le informazioni seguenti:

|TYPE|Nome host|Punta a|TTL|
|--------|-------------|-------------|-------|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

`EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

**Passaggio 2: Verificare CNAME** (facoltativo)<br>
Nella [console di amministrazione di Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informare gli utenti sulla modalità di registrazione dei dispositivi Windows
Informare gli utenti sulla modalità di registrazione dei dispositivi Windows e su cosa accade dopo il loro inserimento nella gestione.
Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). È anche possibile invitare gli utenti a leggere [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo in Intune?](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Per altre informazioni sulle attività per gli utenti finali, vedere [Informazioni sull'uso di Microsoft Intune per gli utenti finali](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md)

