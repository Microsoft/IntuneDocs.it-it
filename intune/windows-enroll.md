---
title: Registrazione di dispositivi Windows
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: abilitare la gestione di dispositivi mobili (MDM) Intune per i dispositivi Windows.'
keywords: 
author: nathbarn
manager: nathbarn
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 687be18cedd063b3c2701937f2522e801e51644b
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-windows-devices"></a>Registrazione di dispositivi Windows

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Questo argomento offre agli amministratori IT informazioni utili per semplificare la registrazione di Windows per gli utenti.  I dispositivi Windows possono essere registrati senza ulteriori passaggi, ma è possibile semplificare la registrazione per gli utenti.

I dispositivi, che hanno Windows 10 Creators Update e che sono aggiunti al dominio di Azure Active Directory, sono ora supportati per la gestione multiutente da Intune. Ciò significa che quando utenti standard diversi accedono al dispositivo con le rispettive credenziali di Azure AD, riceveranno tutte le app e i criteri assegnati al loro nome utente. Gli utenti non possono attualmente usare il portale aziendale per scenari self-service, ad esempio l'installazione di app.

La semplificazione della registrazione dei dispositivi Windows dipende da due fattori:

- **Si usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) è incluso in Enterprise Mobility + Security e altri piani di licenze.
- **Quali versioni di client Windows saranno registrate?** <br>I dispositivi Windows 10 possono essere registrati automaticamente mediante l'aggiunta di un account aziendale o dell'istituto di istruzione. Le versioni precedenti devono essere registrate con l'app del portale aziendale.

||**Azure AD Premium**|**Altro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Registrazione automatica](#enable-windows-10-automatic-enrollment) |[Registrazione utente](#enable-windows-enrollment-without-azure-ad-premium)|
|**Versioni precedenti di Windows**|[Registrazione utente](#enable-windows-enrollment-without-azure-ad-premium)|[Registrazione utente](#enable-windows-enrollment-without-azure-ad-premium)|

[!INCLUDE[AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Abilitare la registrazione di Windows senza Azure AD Premium
È possibile consentire agli utenti di registrare i propri dispositivi senza la registrazione automatica di Azure AD Premium. Una volta assegnate le licenze, gli utenti possono effettuare la registrazione dopo l'aggiunta dell'account aziendale ai dispositivi personali oppure includendo i loro dispositivi di proprietà dell'azienda in Azure Active Directory. La creazione di un alias DNS (tipo di record CNAME) consente agli utenti di registrare facilmente i propri dispositivi. Se si creano record di risorse DNS CNAME, gli utenti potranno connettersi e registrarsi in Intune senza dover immettere il nome del server Intune.

**Passaggio 1: Creare CNAME** (facoltativo)<br>
Creare record di risorse DNS CNAME per il dominio aziendale. Ad esempio, se il sito Web aziendale è contoso.com, si creerà un CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

Anche se la creazione di record CNAME DNS è facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record di registrazione CNAME, agli utenti viene richiesto di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.com.

|Tipo|Nome dell'host|Punta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 ora|

Se si dispone di più suffissi UPN, è necessario creare un CNAME per ciascun nome di dominio e puntare ciascuno a EnterpriseEnrollment-s.manage.microsoft.com. Ad esempio, se gli utenti di Contoso usano name@contoso.com, ma usano anche name@us.contoso.com e name@eu.constoso.com come indirizzo di posta elettronica/UPN, l'amministratore DNS Contoso dovrà creare i CNAME seguenti.

|Tipo|Nome dell'host|Punta a|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 ora|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 ora|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 ora|

`EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non sia stato propagato.

**Passaggio 2: Verificare CNAME** (facoltativo)<br>
Nel portale di Azure Intune scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. Nel pannello Intune scegliere **Registra i dispositivi** > **Registrazione Windows**. Immettere l'URL del dominio verificato del sito Web della società nella casella **Specificare un nome di dominio verificato** e quindi scegliere **Verifica il rilevamento automatico**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informare gli utenti sulla modalità di registrazione dei dispositivi Windows
Informare gli utenti sulla modalità di registrazione dei dispositivi Windows e su cosa accade dopo il loro inserimento nella gestione. Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). È anche possibile invitare gli utenti a leggere [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo in Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

Per altre informazioni sulle attività per gli utenti finali, vedere [Informazioni sull'uso di Microsoft Intune per gli utenti finali](https://docs.microsoft.com/intune-classic/deploy-use/how-to-educate-your-end-users-about-microsoft-intune).

