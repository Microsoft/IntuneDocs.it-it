---
title: Registrazione di dispositivi Windows
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: abilitare la gestione di dispositivi mobili (MDM) Intune per i dispositivi Windows.'
keywords: 
author: staciebarker
manager: stabar
ms.date: 02/15/17
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 7262093700dab3a7befd5b82ac9f8ee3dde22dcf


---

# <a name="enroll-windows-devices"></a>Registrazione di dispositivi Windows 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Per configurare la registrazione per i dispositivi Windows, usare uno dei metodi seguenti:

- [**Registrazione automatica di Windows 10 e Windows 10 Mobile con Azure Active Directory Premium**](#set-up-windows-10-and-windows-10-mobile-automatic-enrollment-with-azure-active-directory-premium)
 -  Questo metodo è applicabile solo ai dispositivi Windows 10 e Windows 10 Mobile.
 -  Per usare questo metodo, è necessario disporre di Azure Active Directory Premium. In caso contrario, usare il metodo di registrazione per Windows 8.1 e Windows Phone 8.1.
 -  Se si sceglie di non abilitare la registrazione automatica, usare il metodo di registrazione per Windows 8.1 e Windows Phone 8.1.

- [**Registrazione di Windows 8.1 e Windows Phone 8.1 configurando CNAME**](#set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname)
 - È necessario usare questo metodo per registrare i dispositivi Windows 8.1 e Windows Phone 8.1.


## <a name="prerequisites"></a>Prerequisiti

Se alcuni dei prerequisiti seguenti non sono ancora presenti nell'anteprima di Intune in Azure, è necessario completarli dalla console di amministrazione di Intune classica.

- [Configurare un nome di dominio personalizzato](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Impostare l'autorità di gestione dei dispositivi mobili (MDM)](set-mdm-authority.md) come **Microsoft Intune**
- [Configurare l'app Portale aziendale](/intune-azure/manage-apps/company-portal-app.md)
- Assegnare licenze agli utenti

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="set-up-windows-81-and-windows-phone-81-enrollment-by-configuring-cname"></a>Impostare la registrazione di Windows 8.1 e Windows Phone 8.1 configurando CNAME

È possibile consentire agli utenti di installare e registrare i propri dispositivi tramite il portale aziendale di Intune. Se si creano record CNAME DNS, gli utenti potranno connettersi e registrarsi in Intune senza immettere un nome server.

1. **Creare record CNAME** (facoltativo)<br>
 Creare record di risorse DNS **CNAME** per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

    Anche se la creazione di record CNAME DNS è facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record CNAME, viene richiesto all'utente di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.com.

    Se è presente più di un dominio verificato, creare un record CNAME per ciascun dominio. Il record di risorse CNAME deve contenere le informazioni seguenti:

    I record di risorse CNAME devono contenere le informazioni seguenti:

  |TYPE|Nome host|Punta a|TTL|
  |--------|-------------|-------------|-------|
  |CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com |1 ora|
  |CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

  `EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

  `EnterpriseRegistration.windows.net`: supporta i dispositivi Windows 8.1 e Windows 10 Mobile che verranno registrati in Azure Active Directory tramite account aziendale o dell'istituto di istruzione

  Se la società usa più domini per le credenziali dell'utente, creare record CNAME per ciascun dominio.

  Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a EnterpriseEnrollment-s.manage.microsoft.com. La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

2.  **Verificare i record CNAME**<br>Nella [console di amministrazione di Intune](http://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows Phone**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

3.  **Passaggi facoltativi**<br>Il passaggio **Aggiungi chiave di sideload** non è necessario per Windows 10. <br>Il passaggio **Caricare il certificato di firma codice** è necessario solo se si prevede di distribuire ai dispositivi app line-of-business non disponibili da Windows Store.

4.  **Informare gli utenti della modalità di registrazione dei dispositivi e di cosa aspettarsi dopo l'introduzione dei dispositivi nella gestione.**

    Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/en-us/intune/enduser/enroll-your-device-in-intune-windows). È anche possibile invitare gli utenti a leggere [What can my IT admin see on my devic](https://docs.microsoft.com/intune/enduser/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows) (Quali sono i dettagli visibili all'amministratore IT sul mio dispositivo?).

    Per altre informazioni sulle attività per gli utenti finali, vedere [Informazioni sull'uso di Microsoft Intune per gli utenti finali](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune).

Non è necessario alcun intervento aggiuntivo a meno che non venga distribuito il Portale aziendale nei dispositivi.  I passaggi 2 e 3 nella console di amministrazione possono essere ignorati.



<!--HONumber=Feb17_HO3-->


