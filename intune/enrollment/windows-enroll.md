---
title: Configurare la registrazione dei dispositivi Windows con Microsoft Intune
titleSuffix: ''
description: Configurare la registrazione dei dispositivi Windows.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: add92c038e33ba1b5873eb0e9588242f8f3d0f57
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207435"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Configurare la registrazione dei dispositivi Windows

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo offre agli amministratori IT informazioni utili per semplificare la registrazione dei dispositivi Windows per gli utenti. Dopo aver [configurato Intune](../fundamentals/setup-steps.md) gli utenti registrano i dispositivi Windows [accedendo](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows) con l'account aziendale o dell'istituto di istruzione.  

L'amministratore di Intune può semplificare la registrazione nei modi seguenti:

- [Abilitare la registrazione automatica](#enable-windows-10-automatic-enrollment) (richiede Azure AD Premium)
- [Registrazione CNAME](#simplify-windows-enrollment-without-azure-ad-premium)
- [Abilitare la registrazione in blocco](../windows-bulk-enroll.md) (sono necessari Azure AD Premium e Progettazione configurazione di Windows)

Due fattori determinano in che modo è possibile semplificare la registrazione dei dispositivi Windows:

- **Si usa Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) è incluso in Enterprise Mobility + Security e altri piani di licenze.
- **Quali versioni dei client Windows richiedono la registrazione da parte degli utenti?** <br>I dispositivi Windows 10 possono essere registrati automaticamente mediante l'aggiunta di un account aziendale o dell'istituto di istruzione. Le versioni precedenti devono essere registrate con l'app del portale aziendale.

||**Azure AD Premium**|**Altro AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Registrazione automatica](#enable-windows-10-automatic-enrollment) |Registrazione utenti|
|**Versioni precedenti di Windows**|Registrazione utenti|Registrazione utenti|

Le organizzazioni che possono usare la registrazione automatica possono anche configurare la [registrazione in blocco di dispositivi](../windows-bulk-enroll.md) usando l'app Progettazione configurazione di Windows.

## <a name="device-enrollment-prerequisites"></a>Prerequisiti per la registrazione del dispositivo

Prima che un amministratore possa registrare i dispositivi in Intune per la gestione, le licenze devono essere già state assegnate all'account dell'amministratore. [Informazioni sull'assegnazione delle licenze per la registrazione del dispositivo](../fundamentals/licenses-assign.md)

## <a name="multi-user-support"></a>Supporto di più utenti

Intune supporta più utenti nei dispositivi che:

- eseguono Windows 10 Creator Update
- appartengono a un dominio Azure Active Directory.

Quando gli utenti standard accedono con le proprie credenziali di Azure AD ricevono le app e i criteri assegnati al nome utente. Solo l'[utente primario](../remote-actions/find-primary-user.md) del dispositivo può usare il Portale aziendale per scenari self-service, ad esempio l'installazione di app e l'esecuzione di azioni del dispositivo (rimozione, reimpostazione). Per i dispositivi Windows 10 condivisi a cui non è assegnato un utente primario, il Portale aziendale può comunque essere usato per installare le app disponibili.

[!INCLUDE [AAD-enrollment](../includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Semplificare la registrazione di Windows senza Azure AD Premium
Per semplificare la registrazione, creare un alias DNS (Domain Name Server), un tipo di record CNAME che reindirizza le richieste di registrazione ai server di Intune. In caso contrario, gli utenti che tentano di connettersi a Intune devono immettere il nome del server Intune durante la registrazione.

**Passaggio 1: Creare CNAME** (facoltativo)<br>
Creare record di risorse CNAME DNS per il dominio della società. Ad esempio, se il sito Web della società è contoso.com, si creerà un record CNAME in DNS che reindirizzi EnterpriseEnrollment.contoso.com a enterpriseenrollment-s.manage.microsoft.com.

Sebbene la creazione di voci DNS CNAME sia facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record di registrazione CNAME, agli utenti viene richiesto di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.com.

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
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 ora|

`EnterpriseEnrollment-s.manage.microsoft.com`: supporta un reindirizzamento al servizio Intune con riconoscimento del dominio dal nome di dominio del messaggio di posta elettronica

La propagazione delle modifiche ai record DNS potrebbe richiedere fino a 72 ore. È impossibile verificare la modifica DNS in Intune fino a quando il record DNS non è stato propagato.

## <a name="additional-endpoints-are-supported-but-not-recommended"></a>Gli endpoint aggiuntivi sono supportati ma non consigliati
EnterpriseEnrollment-s.manage.microsoft.com è il nome FQDN preferito per la registrazione, ma esistono altri due endpoint che sono stati usati dai clienti in passato e sono supportati. EnterpriseEnrollment.manage.microsoft.com (senza -s) e manage.microsoft.com entrambi funzionano entrambi come destinazione per il server con rilevamento automatico, ma l'utente dovrà toccare OK su un messaggio di conferma. Se si punta a EnterpriseEnrollment-s.manage.microsoft.com, l'utente non dovrà eseguire il passaggio di conferma aggiuntivo, quindi questa è la configurazione consigliata

## <a name="alternate-methods-of-redirection-are-not-supported"></a>I metodi alternativi di reindirizzamento non sono supportati
L'uso di un metodo diverso dalla configurazione CNAME non è supportato. Ad esempio, l'uso di un server proxy per reindirizzare enterpriseenrollment.contoso.com/EnrollmentServer/Discovery.svc a enterpriseenrollment-s.manage.microsoft.com/EnrollmentServer/Discovery.svc o manage.microsoft.com/EnrollmentServer/Discovery.svcnon è supportato.

**Passaggio 2: Verificare CNAME** (facoltativo)<br>
1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **Windows** > **Registrazione Windows** > **Convalida di CNAME**.
2. Nella casella **Dominio**, immettere il sito Web aziendale e quindi scegliere **Test**.

## <a name="tell-users-how-to-enroll-windows-devices"></a>Informare gli utenti sulla modalità di registrazione dei dispositivi Windows
Informare gli utenti sulla modalità di registrazione dei dispositivi Windows e su cosa accade dopo il loro inserimento nella gestione.

> [!NOTE]
> Gli utenti finali devono accedere al sito Web del portale aziendale attraverso Microsoft Edge per visualizzare le app Windows assegnate per le versioni di Windows specifiche. Altri browser, inclusi Google Chrome, Mozilla Firefox e Internet Explorer, non supportano questo tipo di filtro.

Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo Windows in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows). È anche possibile invitare gli utenti a leggere [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo in Intune?](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows).

>[!IMPORTANT]
> Se la registrazione MDM automatica non è abilitata e vengono usati dispositivi Windows 10 aggiunti ad Azure AD, saranno visibili due record nella console di Intune dopo la registrazione. Per evitare questo problema assicurarsi che gli utenti con dispositivi aggiunti ad Azure AD passino ad **Account** > **Accedi all'azienda o all'istituto di istruzione** e **Connetti** usando lo stesso account. 

Per altre informazioni sulle attività per gli utenti finali, vedere [Informazioni sull'uso di Microsoft Intune per gli utenti finali](../fundamentals/end-user-educate.md).

## <a name="registration-and-enrollment-cnames"></a>CNAME di registrazione
Azure Active Directory ha un CNAME diverso che usa per la registrazione dei dispositivi iOS, Android e Windows. L'accesso condizionale di Intune richiede la registrazione dei dispositivi, chiamata anche"aggiunta all'area di lavoro". Se si prevede di usare l'accesso condizionale, è necessario configurare anche il CNAME EnterpriseRegistration per ogni nome di società.

| Tipo | Nome dell'host | Punta a | TTL |
| --- | --- | --- | --- |
| NAME | EnterpriseRegistration. company_domain.com | EnterpriseRegistration.windows.net | 1 ora|

Per altre informazioni sulla registrazione dei dispositivi, vedere [Gestire le identità dei dispositivi usando il portale di Azure](https://docs.microsoft.com/azure/active-directory/devices/device-management-azure-portal)

## <a name="windows-10-auto-enrollment-and-device-registration"></a>Registrazione automatica di Windows 10 e registrazione dei dispositivi

Questa sezione si applica ai clienti cloud di enti pubblici degli Stati Uniti.

Sebbene la creazione di voci DNS CNAME sia facoltativa, i record CNAME semplificano la registrazione per gli utenti. Se non viene trovato alcun record di registrazione CNAME, agli utenti viene richiesto di immettere manualmente il nome del server MDM, enrollment.manage.microsoft.us.

| Tipo | Nome dell'host | Punta a | TTL |
| --- | --- | --- | --- |
| CNAME | EnterpriseEnrollment.company_domain.com | EnterpriseEnrollment-s.manage.microsoft.us | 1 ora|
|CNAME | EnterpriseRegistration.company_domain.com | EnterpriseRegistration.windows.net | 1 ora |


## <a name="next-steps"></a>Passaggi successivi

- [Considerazioni per la gestione di dispositivi Windows con Intune in Azure](../fundamentals/intune-legacy-pc-client.md).
