---
title: Configurare la registrazione dei dispositivi Windows con Microsoft Intune
titlesuffix: ''
description: Configurare la registrazione dei dispositivi Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2192b6d653bfb51503b006a5045d454c202618f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57234110"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Configurare la registrazione dei dispositivi Windows

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo offre agli amministratori IT informazioni utili per semplificare la registrazione dei dispositivi Windows per gli utenti. Dopo aver [configurato Intune](setup-steps.md) gli utenti registrano i dispositivi Windows [accedendo](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) con l'account aziendale o dell'istituto di istruzione.  

L'amministratore di Intune può semplificare la registrazione nei modi seguenti:
- [Abilitare la registrazione automatica](#enable-windows-10-automatic-enrollment) (richiede Azure AD Premium)
- [Registrazione CNAME](#simplify-windows-enrollment-without-azure-ad-premium)
- [Abilitare la registrazione in blocco](windows-bulk-enroll.md) (sono necessari Azure AD Premium e Progettazione configurazione di Windows)

La semplificazione della registrazione dei dispositivi Windows dipende da due fattori:

- **Si usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) è incluso in Enterprise Mobility + Security e altri piani di licenze.
- **Quali versioni dei client Windows richiedono la registrazione da parte degli utenti?** <br>I dispositivi Windows 10 possono essere registrati automaticamente mediante l'aggiunta di un account aziendale o dell'istituto di istruzione. Le versioni precedenti devono essere registrate con l'app del portale aziendale.

||**Azure AD Premium**|**Altro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Registrazione automatica](#enable-windows-10-automatic-enrollment) |[Registrazione utente](#enable-windows-enrollment-without-azure-ad-premium)|
|**Versioni precedenti di Windows**|[Registrazione utente](#enable-windows-enrollment-without-azure-ad-premium)|[Registrazione utente](#enable-windows-enrollment-without-azure-ad-premium)|

Le organizzazioni che possono usare la registrazione automatica possono anche configurare la [registrazione in blocco di dispositivi](windows-bulk-enroll.md) usando l'app Progettazione configurazione di Windows.

## <a name="multi-user-support"></a>Supporto di più utenti

Intune supporta la gestione multiutente per i dispositivi che eseguono Windows 10 Creators Update e sono aggiunti al dominio di Azure Active Directory. Quando gli utenti standard accedono con le proprie credenziali di Azure AD ricevono le app e i criteri assegnati al nome utente. Gli utenti non possono attualmente usare il Portale aziendale per scenari self-service, ad esempio l'installazione di app.

[!INCLUDE [AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Semplificare la registrazione di Windows senza Azure AD Premium
Per semplificare la registrazione, creare un alias DNS (Domain Name Server), un tipo di record CNAME che reindirizza le richieste di registrazione ai server di Intune. In caso contrario, gli utenti che tentano di connettersi a Intune devono immettere il nome del server Intune durante la registrazione.

**Passaggio 1: Creare CNAME** (facoltativo)<br>
Creare record di risorse DNS CNAME per il dominio aziendale. Ad esempio, se il sito Web della società è contoso.com, si creerà un record CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

Anche se la creazione di record CNAME DNS è facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record di registrazione CNAME, agli utenti viene richiesto di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.com.

|Tipo|Nome dell'host|Punta a|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 ora|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1 ora|

Se l'azienda usa più suffissi UPN, è necessario creare un CNAME per ciascun nome di dominio e puntare ciascuno a EnterpriseEnrollment-s.manage.microsoft.com. Ad esempio, gli utenti di Contoso usano i formati seguenti come indirizzo di posta elettronica/UPN:

- name@contoso.com
- name@us.contoso.com
- name@eu.contoso.com

L'amministratore DNS di Contoso deve creare i CNAME seguenti:

|Tipo|Nome dell'host|Punta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 ora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 ora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 ora|

`EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non è stato propagato.

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>Gli endpoint aggiuntivi sono supportati ma non consigliati
EnterpriseEnrollment-s.manage.microsoft.com è il nome FQDN preferito per la registrazione, ma esistono altri due endpoint che sono stati usati dai clienti in passato e sono supportati. EnterpriseEnrollment.manage.microsoft.com (senza -s) e manage.microsoft.com entrambi funzionano entrambi come destinazione per il server con rilevamento automatico, ma l'utente dovrà toccare OK su un messaggio di conferma. Se si punta a EnterpriseEnrollment-s.manage.microsoft.com, l'utente non dovrà eseguire il passaggio di conferma aggiuntivo, quindi questa è la configurazione consigliata

## <a name="alternate-methods-of-redirection-are-not-supported"></a>I metodi alternativi di reindirizzamento non sono supportati
L'uso di un metodo diverso dalla configurazione CNAME non è supportato. Ad esempio, l'uso di un server proxy per reindirizzare enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc a enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc o manage.microsoft.com/EnrollmentServer/Discovery.svcnon è supportato.

**Passaggio 2: Verificare CNAME** (facoltativo)<br>
1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Convalida di CNAME**.
2. Nella casella **Dominio**, immettere il sito Web aziendale e quindi scegliere **Test**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informare gli utenti sulla modalità di registrazione dei dispositivi Windows
Informare gli utenti sulla modalità di registrazione dei dispositivi Windows e su cosa accade dopo il loro inserimento nella gestione.

> [!NOTE]
> Gli utenti finali devono accedere al sito Web del portale aziendale attraverso Microsoft Edge per visualizzare le app Windows assegnate per le versioni di Windows specifiche. Altri browser, inclusi Google Chrome, Mozilla Firefox e Internet Explorer, non supportano questo tipo di filtro.

Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). È anche possibile invitare gli utenti a leggere [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo in Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Se la registrazione MDM automatica non è abilitata e vengono usati dispositivi Windows 10 aggiunti ad Azure AD, saranno visibili due record nella console di Intune dopo la registrazione. Per evitare questo problema assicurarsi che gli utenti con dispositivi aggiunti ad Azure AD passino ad **Account** > **Accedi all'azienda o all'istituto di istruzione** e **Connetti** usando lo stesso account. 

Per altre informazioni sulle attività per gli utenti finali, vedere [Informazioni sull'uso di Microsoft Intune per gli utenti finali](end-user-educate.md).

## <a name="next-steps"></a>Passaggi successivi

- [Considerazioni per la gestione di dispositivi Windows con Intune in Azure](intune-legacy-pc-client.md).
