---
# required metadata

title: Sincronizzare Active Directory e aggiungere utenti a Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Sincronizzare Active Directory e aggiungere utenti a Intune
È possibile configurare la sincronizzazione delle directory per importare account utente dall'istanza locale di Active Directory a Microsoft Azure Active Directory (Azure AD). La connessione del servizio locale Active Directory con tutti i servizi basati su Azure Active Directory consente di semplificare notevolmente la gestione delle identità utente. È anche possibile configurare le funzionalità SSO (Single Sign-On) per semplificare ulteriormente l'autenticazione per tutti gli utenti.

Per semplificare le operazioni quando si usano più servizi con lo stesso [tenant di Azure AD](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant), gli account utente già sincronizzati sono disponibili a tutti i servizi basati su cloud che condividono la stessa sottoscrizione al tenant di Azure AD.

## Sincronizzare gli utenti locali con Azure AD
L'unico strumento necessario per sincronizzare gli account utente con Azure AD è la [procedura guidata di Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). La procedura guidata di Azure AD Connect offre un'esperienza semplificata e guidata per connettere l'infrastruttura di identità locale al cloud.  È sufficiente selezionare la topologia e le esigenze (una o più directory, sincronizzazione delle password o federazione) nella procedura guidata per distribuire e configurare automaticamente tutti i componenti necessari per stabilire la connessione, inclusi i servizi di sincronizzazione, Active Directory Federation Services (AD FS) e il modulo Azure AD PowerShell.

> [!TIP]
> Azure AD Connect include funzionalità disponibili in precedenza con il nome di Dirsync e Azure AD Sync. Altre informazioni sull'[integrazione della directory](http://technet.microsoft.com/library/jj573653.aspx). Per informazioni sui vantaggi della sincronizzazione degli account utente dalla directory locale ad Azure AD, vedere [Analogie tra Active Directory e Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## Concedere autorizzazioni di amministratore
Dopo aver aggiunto altri utenti alla sottoscrizione, è consigliabile concedere le [credenziali amministrative](administrative-accounts-websites-perms.md) ad alcuni account utente. La console usata per assegnare credenziali amministrative dipende dal tipo di amministratore da assegnare:

-   **Amministratore tenant**: usare il **[!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)]** per assegnare questo tipo di amministratore in modo da gestire la sottoscrizione, incluse la fatturazione, la memoria cloud e la gestione degli utenti che possono usare [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].

-   **Amministratore del servizio**: usare la **[!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]** per assegnare questo tipo di amministratore in modo da gestire attività quotidiane, incluse la gestione di dispositivi mobili o computer, la distribuzione di criteri o software e l'esecuzione di report.


### Passaggi successivi
A questo punto, Passaggio 3 della *Guida introduttiva di Intune* completato.

>[!div class="step-by-step"]

>[&larr; **Impostazioni dominio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Gestire le licenze di Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  


<!--HONumber=May16_HO1-->


