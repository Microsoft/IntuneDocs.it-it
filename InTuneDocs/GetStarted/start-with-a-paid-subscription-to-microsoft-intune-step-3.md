---
title: Sincronizzare Active Directory e aggiungere utenti a Intune | Microsoft Intune
description: Sincronizzare gli utenti locali con Azure AD e concedere autorizzazioni di amministratore per la sottoscrizione di Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29b6e5a3d319c741482fcc2b600842e2e42b96e2
ms.openlocfilehash: 33534c685ad3a4ddfd4b605e088132f2b8ff2c36


---


# <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizzare Active Directory e aggiungere utenti a Intune
È possibile configurare la sincronizzazione delle directory per importare account utente dall'istanza locale di Active Directory a Microsoft Azure Active Directory (Azure AD). La connessione del servizio locale Active Directory con tutti i servizi basati su Azure Active Directory consente di semplificare notevolmente la gestione delle identità utente. È anche possibile configurare le funzionalità SSO (Single Sign-On) per semplificare ulteriormente l'autenticazione per tutti gli utenti.

Per semplificare le operazioni quando si usano più servizi con lo stesso [tenant di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/), gli account utente già sincronizzati sono disponibili a tutti i servizi basati su cloud che condividono la stessa sottoscrizione al tenant di Azure AD.

## <a name="synchronize-on-premises-users-with-azure-ad"></a>Sincronizzare gli utenti locali con Azure AD
L'unico strumento necessario per sincronizzare gli account utente con Azure AD è la [procedura guidata di Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). La procedura guidata di Azure AD Connect offre un'esperienza semplificata e guidata per connettere l'infrastruttura di identità locale al cloud.  È sufficiente selezionare la topologia e le esigenze (una o più directory, sincronizzazione delle password o federazione) nella procedura guidata per distribuire e configurare automaticamente tutti i componenti necessari per stabilire la connessione, inclusi i servizi di sincronizzazione, Active Directory Federation Services (AD FS) e il modulo Azure AD PowerShell.

> [!TIP]
> Azure AD Connect include funzionalità disponibili in precedenza con il nome di Dirsync e Azure AD Sync. Altre informazioni sull'[integrazione della directory](http://technet.microsoft.com/library/jj573653.aspx). Per informazioni sui vantaggi della sincronizzazione degli account utente dalla directory locale ad Azure AD, vedere [Analogie tra Active Directory e Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-administrator-permissions"></a>Concedere autorizzazioni di amministratore

Per amministrare Intune occorre usare:
- Due tipi di account amministratore
- Account utente con autorizzazioni aggiuntive
- Due portali/console di amministrazione basati su web per concedere agli amministratori l'accesso agli elementi da gestire.

Dopo aver aggiunto altri utenti alla sottoscrizione, è consigliabile concedere le credenziali amministrative ad alcuni account utente. La console usata per assegnare credenziali amministrative dipende dal tipo di amministratore da assegnare:

-   **Amministratore tenant**: usare il **portale per gli account di Microsoft Intune** per assegnare questo tipo di amministratore in modo da gestire la sottoscrizione, incluse la fatturazione, l'archiviazione cloud e la gestione degli utenti che possono usare Intune.

-   **Amministratore del servizio**: usare la **console di amministrazione di Microsoft Intune** per assegnare questo tipo di amministratore per le attività quotidiane, incluse la gestione di dispositivi mobili o computer, la distribuzione di criteri o software e l'esecuzione di report.

Le sezioni seguenti trattano di questi account e portali.

## <a name="administrator-accounts-and-user-accounts-with-special-permissions"></a>Account amministratore e account utente con autorizzazioni speciali

Di seguito vengono riportati gli account e le autorizzazioni che verranno usati per Intune.

### <a name="tenant-administrator"></a>Amministratore tenant
|Livelli di autorizzazione|Altre informazioni|
|--------------------------|-------------------------|
|A un amministratore tenant vengono assegnati un ruolo di amministratore, che definisce l'ambito amministrativo per tale utente, e le attività che può gestire.<br /><br />I ruoli di amministratore sono comuni tra i vari servizi cloud di Microsoft, anche se alcuni servizi potrebbero non supportare alcuni ruoli.<br /><br /> Microsoft Intune usa i ruoli seguenti:<br /><br />- Amministratore globale<br />- Amministratore fatturazione<br />- Amministratore password<br />- Amministratore del servizio supporto tecnico<br />- Amministratore Gestione utenti|Per impostazione predefinita, l'account usato per creare la sottoscrizione Microsoft Intune è un amministratore tenant con il ruolo di amministratore globale.<br /></br>  Gli amministratori tenant usano [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] per gestire la sottoscrizione per Intune e assegnare gli amministratori tenant da [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Usare un amministratore tenant con il ruolo Amministratore globale per accedere alla [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] e assegnare il primo amministratore del servizio. È consigliabile non usare un amministratore tenant per attività di gestione quotidiane. Un amministratore tenant non ha la necessità di disporre di una licenza per Intune per accedere a [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Il concetto dell'amministratore tenant è comune tra i servizi cloud Microsoft. Quando si esegue la sottoscrizione a Intune, il servizio ottenuto è un tenant di Microsoft Azure AD. Vedere la sezione relativa al tenant di Azure AD in [Che cos'è una directory di Azure AD?](http://technet.microsoft.com/library/jj573650.aspx).|


### <a name="service-administrator"></a>Amministratore dei servizi
|Livelli di autorizzazione|Altre informazioni|
|--------------------------|-------------------------|
|Agli amministratori del servizio viene assegnata una delle seguenti autorizzazioni:<br /><br />**Accesso completo**: concede l'accesso a tutte le aree della [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], senza alcuna restrizione. È anche possibile aggiungere e gestire altri amministratori del servizio.<br /><br />**Accesso in sola lettura**: concede l'autorizzazione di lettura a tutte le aree della [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. Un amministratore del servizio in sola lettura non può modificare i dati, ma può eseguire report.<br /><br />**Supporto tecnico - Nodo Gruppi**: concede le autorizzazioni che consentono all'amministratore del servizio di eseguire solo un set di attività generalmente associato a scenari di supporto tecnico. Per informazioni su questo set di autorizzazioni, vedere [Personalizzare le visualizzazioni della console di Intune in base ai ruoli di amministratore](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console).|Per impostazione predefinita, Intune non assegna un amministratore del servizio. Al contrario, è necessario usare un amministratore tenant con il ruolo di amministratore globale per assegnare il primo amministratore del servizio per la sottoscrizione. </br></br> Come amministratore del servizio, si usa la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] per le attività di gestione quotidiane di Intune.<br /><br />Gli amministratori del servizio vengono assegnati dalla console di amministrazione. Un amministratore del servizio deve disporre di una licenza per Intune prima che l'account possa accedere alla console di amministrazione.|



### <a name="device-enrollment-managers"></a>Manager di registrazione dispositivi
|Livelli di autorizzazione|Altre informazioni|
|--------------------------|-------------------------|
|I manager di registrazione dispositivi sono account utente standard che dispongono dell'autorizzazione aggiuntiva per registrare più di cinque dispositivi.|Per impostazione predefinita, ogni utente di [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] può registrare fino a cinque dispositivi. È comunque possibile assegnare a un account utente l'autorizzazione di manager di registrazione dispositivi e quindi usare tale account per registrare gruppi di dispositivi di proprietà dell'azienda di grandi dimensioni. Questo è utile quando i dispositivi possono essere assegnati agli utenti su base temporanea oppure vengono usati in modalità tutto schermo in cui non è richiesta l'associazione di un utente a un dispositivo.|




>[!div class="step-by-step"]

>[&larr; **Impostazioni dominio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Gestire le licenze di Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Nov16_HO4-->


