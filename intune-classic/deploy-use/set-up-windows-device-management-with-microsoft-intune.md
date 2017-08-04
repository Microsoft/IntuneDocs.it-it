---
title: Configurare la gestione dei dispositivi Windows con Microsoft Intune
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
ms.openlocfilehash: 9066414bcef1ba312db64aef077db8f8bfbbdb44
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="set-up-windows-device-management"></a>Configurare la gestione dei dispositivi Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento offre agli amministratori IT informazioni utili per semplificare la registrazione di Windows per gli utenti.  I dispositivi Windows possono essere registrati senza ulteriori passaggi, ma è possibile semplificare la registrazione per gli utenti.

La semplificazione della registrazione dei dispositivi Windows dipende da due fattori:
- **Si usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) è incluso in Enterprise Mobility + Security e altri piani di licenze.
- **Quali versioni di client Windows saranno registrate?** <br>I dispositivi Windows 10 possono essere registrati automaticamente mediante l'aggiunta di un account aziendale o dell'istituto di istruzione. Le versioni precedenti devono essere registrate con l'app del portale aziendale.

||**Azure AD Premium**|**Altro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Registrazione automatica](#enable-windows-10-automatic-enrollment) |[Registrazione utente](#enable-windows-enrollment-without-automatic-enrollment)|
|**Versioni precedenti di Windows**|[Registrazione utente](#enable-windows-enrollment-without-automatic-enrollment)|[Registrazione utente](#enable-windows-enrollment-without-automatic-enrollment)|

[!INCLUDE[AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-automatic-enrollment"></a>Abilitare la registrazione di Windows senza la registrazione automatica
È possibile consentire agli utenti di registrare i propri dispositivi senza la registrazione automatica di Azure AD Premium. Una volta assegnate le licenze, gli utenti possono effettuare la registrazione dopo l'aggiunta dell'account aziendale ai dispositivi personali oppure includendo i loro dispositivi di proprietà dell'azienda in Azure Active Directory. La creazione di un alias DNS (tipo di record CNAME) consente agli utenti di registrare facilmente i propri dispositivi. Se si creano record di risorse DNS CNAME, gli utenti potranno connettersi e registrarsi in Intune senza dover immettere il nome del server Intune.

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
Nella [console di amministrazione di Intune](https://manage.microsoft.com) scegliere **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Windows**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informare gli utenti sulla modalità di registrazione dei dispositivi Windows
Informare gli utenti sulla modalità di registrazione dei dispositivi Windows e su cosa accade dopo il loro inserimento nella gestione.
Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). È anche possibile invitare gli utenti a leggere [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo in Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Per altre informazioni sulle attività per gli utenti finali, vedere [Informazioni sull'uso di Microsoft Intune per gli utenti finali](/intune/end-user-educate).

### <a name="see-also"></a>Vedere anche
[Prerequisiti per la registrazione dei dispositivi in Microsoft Intune](prerequisites-for-enrollment.md)
