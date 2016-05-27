---
# required metadata

title: Account amministrativi, siti Web e autorizzazioni in Microsoft Intune | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Account amministrativi, siti Web e autorizzazioni in Microsoft Intune

Prima di configurare Microsoft Intune, leggere questo argomento e i requisiti indicati nelle [Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md).

Per amministrare Intune occorre usare:
- Due tipi di account amministratore
- Account utente con autorizzazioni aggiuntive
- Due portali/console di amministrazione basati su web per concedere agli amministratori l'accesso agli elementi da gestire.

Le sezioni seguenti trattano di questi account e portali.

## Account amministratore e account utente con autorizzazioni speciali

Di seguito vengono riportati gli account e le autorizzazioni che verranno usati per Intune.

### Amministratore tenant
|Livelli di autorizzazione|Altre informazioni|
|--------------------------|-------------------------|
|A un amministratore tenant vengono assegnati un ruolo di amministratore, che definisce l'ambito amministrativo per tale utente, e le attività che può gestire.<br /><br />I ruoli di amministratore sono comuni tra i vari servizi cloud di Microsoft, anche se alcuni servizi potrebbero non supportare alcuni ruoli.<br /><br /> Microsoft Intune usa i ruoli seguenti:<br /><br />- Amministratore globale<br />- Amministratore fatturazione<br />- Amministratore password<br />- Amministratore del servizio supporto tecnico<br />- Amministratore Gestione utenti|Per impostazione predefinita, l'account usato per creare la sottoscrizione Microsoft Intune è un amministratore tenant con il ruolo di amministratore globale.<br /></br>  Come amministratore tenant, usare [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] per gestire la sottoscrizione per [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e assegnare gli amministratori tenant da [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Usare un amministratore tenant con il ruolo Amministratore globale per accedere alla [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] e assegnare il primo amministratore del servizio. È consigliabile non usare un amministratore tenant per attività di gestione quotidiane. Un amministratore tenant non ha la necessità di disporre di una licenza per [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] per accedere al [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)].<br /><br />Il concetto dell'amministratore tenant è comune tra i servizi cloud Microsoft. Quando si esegue la sottoscrizione a [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], il servizio ottenuto è un tenant di Microsoft Azure Active Directory. Vedere la sezione relativa al tenant di Azure AD in [Informazioni su Azure Active Directory](http://technet.microsoft.com/library/jj573650.aspx)..|


### Amministratore dei servizi
|Livelli di autorizzazione|Altre informazioni|
|--------------------------|-------------------------|
|Agli amministratori del servizio viene assegnata una delle seguenti autorizzazioni:<br /><br />**Accesso completo**: concede l'accesso a tutte le aree della [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)], senza alcuna restrizione. È anche possibile aggiungere e gestire altri amministratori del servizio.<br /><br />**Accesso in sola lettura**: concede l'autorizzazione di lettura a tutte le aree della [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]. Un amministratore del servizio in sola lettura non può modificare i dati, ma può eseguire report.<br /><br />**Supporto tecnico - Nodo Gruppi**: concede le autorizzazioni che consentono all'amministratore del servizio di eseguire solo un set di attività generalmente associato a scenari di supporto tecnico. Per informazioni su questo set di autorizzazioni, vedere [Customize Intune console views according to admin roles](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console) (Personalizzare le visualizzazioni della console di Intune in base ai ruoli di amministratore).|Per impostazione predefinita, [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] non assegna un amministratore del servizio. Al contrario, è necessario usare un amministratore tenant con il ruolo di amministratore globale per assegnare il primo amministratore del servizio per la sottoscrizione. </br></br> L'amministratore del servizio usa la [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] per le attività di gestione quotidiane di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].<br /><br />Gli amministratori del servizio vengono assegnati dalla console di amministrazione. Un amministratore del servizio deve disporre di una licenza per [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] prima che l'account possa accedere alla console di amministrazione.|



### Manager di registrazione dispositivi
|Livelli di autorizzazione|Altre informazioni|
|--------------------------|-------------------------|
|I manager di registrazione dispositivi sono account utente standard che dispongono dell'autorizzazione aggiuntiva per registrare più di cinque dispositivi.|Per impostazione predefinita, ogni utente di [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] può registrare fino a cinque dispositivi. È comunque possibile assegnare a un account utente l'autorizzazione di manager di registrazione dispositivi e quindi usare tale account per registrare gruppi di dispositivi di proprietà dell'azienda di grandi dimensioni. Questo è utile quando i dispositivi possono essere assegnati agli utenti su base temporanea oppure vengono usati in modalità tutto schermo in cui non è richiesta l'associazione di un utente a un dispositivo.|


## Siti Web di amministrazione per Intune
 Diverse attività amministrative richiedono di usare uno dei siti Web amministrativi seguenti, accessibili da un [Web browser supportato](supported-web-browsers.md).

- [Portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Console di amministrazione di Microsoft Intune](https://admin.manage.microsoft.com/)

### [Portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**L'amministratore tenant usa questo portale per gestire la propria sottoscrizione**, incluse le seguenti attività, quando il proprio ruolo di amministratore lo consente:

- Gestire gli account utente per la sottoscrizione e configurare la sincronizzazione delle directory da Active Directory locale.
- Gestire gruppi di utenti, denominati gruppi di sicurezza.
- Assegnare licenze agli utenti per usare [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Configurare il nome di dominio da usare con la sottoscrizione. Il nome di dominio definisce l'account con cui gli utenti effettuano l'accesso.
- Gestire la fatturazione e i dettagli di acquisto della propria sottoscrizione, incluso il numero di licenze disponibili o la quantità di spazio di archiviazione cloud usabile.
- Trovare collegamenti per visualizzare lo stato del servizio [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Come amministratore tenant è possibile accedere al portale di Office 365 per gestire la sottoscrizione anche quando il proprio account non dispone di una licenza per usare [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)].
- Qualsiasi utente che dispone di una licenza per Intune ma non è un amministratore può usare il portale per ripristinare la password del proprio account e modificare il proprio profilo.
- Per accedere al portale di Office 365, lo stato di accesso dell'account deve essere **Consentito**. Questo stato non equivale a ricevere una licenza per la sottoscrizione. Per impostazione predefinita, tutti gli account utente hanno lo stato **Consentito**..


### [Console di amministrazione di Microsoft Intune](https://admin.manage.microsoft.com/)

**L'amministratore del servizio usa questo portale per gestire le operazioni quotidiane** tra cui:

- Impostare i criteri per computer e dispositivi mobili.
- Caricare e distribuire software come app e aggiornamenti software.
- Gestire [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Endpoint Protection sui computer.
- Visualizzare lo stato dei dispositivi ed eseguire report.
- Accedere a questo portale. Per accedere al portale è necessario avere le autorizzazioni di amministratore del servizio o essere un amministratore tenant con il ruolo Amministratore globale.


Solo gli utenti con autorizzazioni di amministratore del servizio o di amministratore tenant con il ruolo Amministratore globale possono accedere al portale. Per accedere alla console di amministrazione, è necessario che il proprio account abbia una licenza per l'uso di [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] e uno stato di accesso **Consentito**..

Altre informazioni sull'[aggiunta di utenti alla sottoscrizione ](start-with-a-paid-subscription-to-microsoft-intune-step-3.md)e l'[assegnazione delle licenze per la sottoscrizione](start-with-a-paid-subscription-to-microsoft-intune-step-4.md).

 ### Vedere anche
 [Informazioni preliminari per l'uso di Microsoft Intune](what-to-know-before-you-start-microsoft-intune.md)


<!--HONumber=May16_HO1-->


