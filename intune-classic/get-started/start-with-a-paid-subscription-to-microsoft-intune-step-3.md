---
title: Aggiungere utenti e concedere le autorizzazioni | Documentazione Microsoft
description: Sincronizzare gli utenti locali con Azure AD e concedere autorizzazioni di amministratore per la sottoscrizione di Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 4a90d0bdebafeb8a9e5c73892b6f1f11b76eb9f6
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="add-users-and-give-administrative-permission-to-intune"></a>Aggiungere utenti e concedere autorizzazioni amministrative a Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento descrive agli amministratori come possono aggiungere utenti a Intune e quali autorizzazioni amministrative sono disponibili nel servizio di Intune.

Come amministratore, è possibile aggiungere direttamente o sincronizzare utenti da Active Directory locale. Una volta aggiunti, gli utenti possono registrare i dispositivi e accedere alle risorse aziendali. È anche possibile assegnare agli utenti autorizzazioni aggiuntive, tra cui *amministratore tenant*, *amministratore del servizio* e *autorizzazioni di manager di registrazione dispositivi*.

Questo argomento illustra come:

- [Aggiungere utenti a Intune](#add-users-to-intune)
- [Concedere autorizzazioni di Intune aggiuntive](#grant-intune-permissions) tra cui:
  - [Amministratore tenant](#tenant-administrator)
  - [Amministratore del servizio](#service-administrator)
  - [Manager di registrazione dispositivi](#device-enrollment-managers)

## <a name="add-users-to-intune"></a>Aggiungere utenti a Intune
È possibile aggiungere manualmente utenti alla sottoscrizione di Intune attraverso il [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), ma le licenze di Intune non vengono assegnate automaticamente. In un secondo momento, un amministratore tenant di Intune dovrà modificare l'account utente per assegnare una licenza all'utente dal portale di Office 365. Per altre informazioni, vedere [Aggiungere utenti singolarmente o in blocco a Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizzare Active Directory e aggiungere utenti a Intune
È possibile configurare la sincronizzazione delle directory per importare account utente dall'istanza locale di Active Directory a Microsoft Azure Active Directory (Azure AD) che include gli utenti di Intune. La connessione del servizio locale Active Directory con tutti i servizi basati su Azure Active Directory consente di semplificare notevolmente la gestione delle identità utente. È anche possibile configurare le funzionalità SSO (Single Sign-On) per semplificare ulteriormente l'autenticazione per tutti gli utenti. Collegando lo stesso [tenant di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) con più servizi, gli account utente già sincronizzati sono disponibili a tutti i servizi basati su cloud.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Come sincronizzare gli utenti locali con Azure AD
L'unico strumento necessario per sincronizzare gli account utente con Azure AD è la [procedura guidata di Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). La procedura guidata di Azure AD Connect offre un'esperienza semplificata e guidata per connettere l'infrastruttura di identità locale al cloud.  È sufficiente selezionare la topologia e le esigenze (una o più directory, sincronizzazione delle password o federazione) nella procedura guidata per distribuire e configurare automaticamente tutti i componenti necessari per stabilire la connessione, inclusi i servizi di sincronizzazione, Active Directory Federation Services (AD FS) e il modulo Azure AD PowerShell.

> [!TIP]
> Azure AD Connect include funzionalità disponibili in precedenza con il nome di Dirsync e Azure AD Sync. Altre informazioni sull'[integrazione della directory](http://technet.microsoft.com/library/jj573653.aspx). Per informazioni sui vantaggi della sincronizzazione degli account utente dalla directory locale ad Azure AD, vedere [Analogie tra Active Directory e Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-intune-permissions"></a>Concedere le autorizzazioni di Intune

Dopo aver aggiunto altri utenti alla sottoscrizione, è consigliabile concedere le autorizzazioni amministrative ad alcuni account utente. Per amministrare Intune, è possibile concedere agli utenti tre tipi di autorizzazione di Intune
-   **Amministratore tenant**: usare il portale di Office 365 per assegnare questo tipo di amministratore in modo da gestire la sottoscrizione, incluse la fatturazione, la memoria cloud e la gestione degli utenti che possono usare Intune.
-   **Amministratore del servizio**: usare la console di amministrazione di Microsoft Intune per assegnare questo tipo di amministratore per le attività quotidiane, incluse la gestione di dispositivi e computer, la distribuzione di criteri e app e l'esecuzione di report.
-   **Manager di registrazione dispositivi**: usare la console di amministrazione di Microsoft Intune per assegnare questo tipo di amministratore per le attività quotidiane, incluse la gestione di dispositivi e computer, la distribuzione di criteri e app e l'esecuzione di report.


### <a name="tenant-administrator"></a>Amministratore tenant


A un amministratore tenant vengono assegnati un ruolo di amministratore, che definisce l'ambito amministrativo per tale utente, e le attività che può gestire. I ruoli di amministratore sono comuni tra i vari servizi cloud di Microsoft, anche se alcuni servizi potrebbero non supportare alcuni ruoli. Intune usa i ruoli seguenti:
- **Amministratore globale**: accede a tutte le funzionalità amministrative in Intune. Per impostazione predefinita, la persona che si registra a Intune diventa un amministratore globale. Gli amministratori globali sono gli unici amministratori che possono assegnare altri ruoli di amministratore. Nell'organizzazione vi possono essere più amministratori globali. Come procedura consigliata, solo alcuni utenti dell'azienda dovrebbero avere questo ruolo per ridurre il rischio per l'azienda.
- **Amministratore fatturazione**: effettua acquisti, gestisce sottoscrizioni, gestisce ticket di supporto ed esegue il monitoraggio dell'integrità dei servizi.
- **Amministratore password**: reimposta le password, gestisce le richieste di servizio ed esegue il monitoraggio dell'integrità dei servizi. Gli amministratori password sono limitati alla reimpostazione delle password per gli utenti.
- **Amministratore del servizio supporto tecnico**: apre le richieste di supporto a Microsoft e visualizza il dashboard servizi e il centro messaggi. Ha autorizzazioni di "solo visualizzazione", tranne per l'apertura e la lettura dei ticket di supporto.
- **Amministratore Gestione utenti**: recupera password, esegue il monitoraggio dell'integrità dei servizi, aggiunge ed elimina account utente e gestisce richieste di servizio. L'amministratore Gestione utenti non può eliminare un amministratore globale, creare altri ruoli di amministratore o reimpostare le password per gli amministratori di fatturazione, globali e del servizio.

Per impostazione predefinita, l'account usato per creare la sottoscrizione Microsoft Intune è un amministratore tenant con il ruolo di amministratore globale. Gli amministratori tenant usano la console di amministrazione di Intune per gestire la sottoscrizione per Intune e assegnare gli amministratori tenant dal [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854). Usare un amministratore tenant con il ruolo Amministratore globale per accedere al portale e assegnare il primo amministratore del servizio. È consigliabile non usare un amministratore tenant per attività di gestione quotidiane. Un amministratore tenant non deve avere una licenza per Intune per accedere alla console di amministrazione di Intune. Il concetto dell'amministratore tenant è comune tra i servizi cloud Microsoft. Quando si esegue la sottoscrizione a Intune, il servizio ottenuto è un tenant di Azure AD. Per altre informazioni, vedere la sezione relativa al tenant di Azure AD in [Che cos'è una directory di Azure AD?](http://technet.microsoft.com/library/jj573650.aspx).

L'amministratore tenant usa il [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) per gestire la propria sottoscrizione, incluse le seguenti attività, quando il proprio ruolo di amministratore lo consente:

- Gestire gli account utente e configurare la sincronizzazione delle directory da Active Directory locale
- Gestire gruppi di utenti, denominati gruppi di sicurezza
- Assegnare licenze agli utenti di Intune
- Configurare il nome di dominio per la sottoscrizione usata quando gli utenti accedono (ad esempio contoso.com)
- Gestire la fatturazione e gli acquisti, incluse le licenze e lo spazio di archiviazione nel cloud
- Trovare collegamenti per visualizzare lo stato del servizio Intune

Per accedere al portale di Office 365, lo stato di accesso dell'account deve essere **Consentito**. Questo stato non equivale a ricevere una licenza per la sottoscrizione. Per impostazione predefinita, tutti gli account utente hanno lo stato **Consentito**. Gli utenti senza privilegi di amministratore possono usare il portale di Office 365 per reimpostare le password di Intune.

### <a name="service-administrator"></a>Amministratore dei servizi

Per impostazione predefinita, Intune non assegna un amministratore del servizio. Al contrario, è necessario usare un amministratore tenant con il ruolo di amministratore globale per assegnare il primo amministratore del servizio per la sottoscrizione. Come amministratore del servizio, si usa la [console di amministrazione di Intune](https://manage.microsoft.com/) per le attività di gestione quotidiane di Intune. Gli amministratori del servizio vengono assegnati dalla console di amministrazione. Un amministratore del servizio deve avere una licenza per Intune per accedere alla console di amministrazione.

Agli amministratori del servizio viene assegnata una delle seguenti autorizzazioni:
- **Accesso completo**: accesso illimitato a tutte le aree della console di amministrazione di Intune, aggiunta e gestione di altri amministratori del servizio
- **Accesso in sola lettura**: autorizzazione di lettura per tutte le aree della console di amministrazione di Intune, non è possibile modificare i dati, ma è possibile eseguire report
- **Supporto tecnico - Nodo Gruppi**: consente all'amministratore del servizio di eseguire solo le attività associate a scenari di supporto tecnico; vedere [Personalizzare le visualizzazioni della console di Intune in base ai ruoli di amministratore](/intune-classic/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)

L'amministratore del servizio usa questo portale per gestire le operazioni quotidiane tra cui:

- Creare e gestire criteri per computer e dispositivi mobili
- Caricare e distribuire aggiornamenti software e app
- Gestire Endpoint Protection nei computer
- Visualizzare lo stato dei dispositivi ed eseguire report

### <a name="device-enrollment-managers"></a>Manager di registrazione dispositivi

I manager di registrazione dispositivi sono account utente standard con l'autorizzazione aggiuntiva per registrare molti dispositivi senza utente. Per impostazione predefinita, ogni utente di Intune può registrare fino a quindici dispositivi. Come amministratore, è possibile assegnare a un account utente l'autorizzazione di manager di registrazione dispositivi. L'account può registrare un numero elevato di dispositivi di proprietà dell'azienda. Questo è utile quando i dispositivi possono essere assegnati agli utenti su base temporanea oppure vengono usati in modalità tutto schermo in cui non è richiesta l'associazione di un utente a un dispositivo. Per altre informazioni, vedere [Manager di registrazione dispositivi](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Impostazioni dominio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Gestire le licenze di Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  

