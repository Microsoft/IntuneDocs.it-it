---
title: Aggiungere utenti e concedere le autorizzazioni
description: Sincronizzare gli utenti locali con Azure AD e concedere autorizzazioni di amministratore per la sottoscrizione di Intune
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/07/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4289fdbdadbef34f06514b62722f84354534ae65
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2017
---
# <a name="add-users-and-give-administrative-permission-to-intune"></a>Aggiungere utenti e concedere autorizzazioni amministrative a Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Questo argomento descrive agli amministratori come possono aggiungere utenti a Intune e quali autorizzazioni amministrative sono disponibili nel servizio di Intune.

Come amministratore, è possibile aggiungere direttamente o sincronizzare utenti da Active Directory locale. Una volta aggiunti, gli utenti possono registrare i dispositivi e accedere alle risorse aziendali. È anche possibile assegnare agli utenti autorizzazioni aggiuntive, tra cui *amministratore globale* e *amministratore del servizio*.

## <a name="add-users-to-intune"></a>Aggiungere utenti a Intune
È possibile aggiungere manualmente utenti alla sottoscrizione di Intune attraverso il [portale di Office 365](https://www.office.com/signin) o il [portale di Azure Intune](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). Un amministratore può modificare gli account utente per assegnare le licenze di Intune. È possibile assegnare le licenze dal portale di Office 365 o dal portale di Azure Intune. Per altre informazioni sull'uso del portale di Office 365, vedere [Aggiungere utenti singolarmente o in blocco al portale di Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="add-intune-users-in-the-office-365-admin-center"></a>Aggiungere gli utenti di Intune nell'interfaccia di amministrazione di Office 365
1. Accedere al [portale di Office 365](https://www.office.com/signin).
2. Nel menu di Office 365 selezionare **Amministratore**.
3. Nell'interfaccia di amministrazione selezionare **Aggiungi un utente**.

  ![Schermata di amministrazione di Office 365](media/office-add-user.png)

4. Specificare i dettagli utente seguenti:
  - **Nome**
  - **Cognome**
  - **Nome visualizzato**: visualizzato nel portale di Intune
  - **Nome utente**: nome UPN nel portale di Intune
  - **Posizione**
  - **Informazioni sui contatti** (facoltativo)
  - **Password**: generata automaticamente oppure specificare

     ![Schermata di amministrazione di Office 365](media/office-add-user-details.png)

5. Assegnare una licenza di Intune. Selezionare **Product licenses** (Licenze del prodotto) e scegliere la licenza del prodotto.
6. Scegliere **Aggiungi** per creare un nuovo utente.

### <a name="add-intune-users-in-the-azure-intune-portal"></a>Aggiungere utenti Intune nel portale di Azure Intune
1. Accedere al [portale di Azure](https://portal.azure.com). Passare a **Monitoraggio e gestione** > **Intune**. È anche possibile *cercare risorse* per **Intune**.
2. Fare clic su **Utenti**.
3. Nell'interfaccia di amministrazione selezionare **Aggiungi un utente**.
  ![Schermata di amministrazione di Office 365](media/intune-add-user.png)
4. Specificare i dettagli utente seguenti:
  - **Nome**
  - **Nome utente**: il nuovo nome nel portale di Azure Active Directory ![Schermata di amministrazione di Office 365](media/intune-add-user-info.png) Scegliere **OK** per continuare.
5. Facoltativamente, è possibile specificare le proprietà utente seguenti:
  - **Profilo**: informazioni di lavoro come **Posizione** e **Reparto**
  -  **Gruppi**: selezionare i gruppi da aggiungere per l'utente
  - **Ruolo della directory**: assegnare all'utente le autorizzazioni amministrative per Intune

  Selezionare **Crea** per aggiungere il nuovo utente a Intune.
6. Selezionare **Profilo** e quindi scegliere una **Località di utilizzo** per il nuovo utente. È necessario specificare la località di utilizzo prima di poter assegnare al nuovo utente una licenza di Intune. Scegliere **Salva** per continuare.
    ![Schermata di amministrazione di Office 365](media/intune-add-user-loc.png)
7. Selezionare **Licenze** e quindi scegliere **Assegna** per assegnare una licenza di Intune per questo utente. Una licenza di Intune è necessaria per registrare i dispositivi o accedere alle risorse aziendali. Selezionare **Prodotti**, scegliere il tipo di licenza, scegliere **Seleziona** e quindi **Assegna**.

## <a name="grant-admin-permissions"></a>Concedere le autorizzazioni di amministratore

Dopo aver aggiunto altri utenti alla sottoscrizione, è consigliabile concedere le autorizzazioni amministrative ad alcuni utenti:
-   [Amministratore globale](#tenant-administrator): usare il portale di Office 365 per assegnare questo tipo di amministratore. L'amministratore globale può gestire la sottoscrizione, incluse fatturazione, archiviazione cloud e gestione degli utenti che possono usare Intune.
-   [Amministratore personalizzato o con limitazioni](#service-administrator): usare la console di Office 365 o Azure Intune per assegnare questo tipo di amministratore per le attività quotidiane, incluse gestione di dispositivi e computer, distribuzione di criteri e app ed esecuzione di report.

![Immagine dei ruoli di assegnazione del portale di Office 365.](./media/office-assign-roles.png)

### <a name="types-of-administrators"></a>Tipi di amministratori

Assegnare agli utenti una o più autorizzazioni di amministratore. Queste autorizzazioni definiscono l'ambito amministrativo per gli utenti e le attività che possono gestire. Le autorizzazioni di amministratore sono comuni tra i vari servizi cloud di Microsoft, anche se alcuni servizi potrebbero non supportare alcune autorizzazioni. Intune usa le autorizzazioni di amministratore seguenti:

- **Amministratore globale**: (Office 365 e Intune) accede a tutte le funzionalità amministrative in Intune. Per impostazione predefinita, la persona che si registra a Intune diventa un amministratore globale. Gli amministratori globali sono gli unici amministratori che possono assegnare altri ruoli di amministratore. Nell'organizzazione vi possono essere più amministratori globali. Come procedura consigliata, solo alcuni utenti dell'azienda dovrebbero avere questo ruolo per ridurre il rischio per l'azienda.
- **Amministratore fatturazione**: (Office 365 e Intune) effettua acquisti, gestisce sottoscrizioni, gestisce ticket di supporto ed esegue il monitoraggio dell'integrità dei servizi.
- **Amministratore password**: (Office 365 e Intune) reimposta le password, gestisce le richieste di servizio ed esegue il monitoraggio dell'integrità dei servizi. Gli amministratori password sono limitati alla reimpostazione delle password per gli utenti.
- **Amministratore dei servizi**: (Office 365 e Intune) apre le richieste di supporto a Microsoft e visualizza il dashboard servizi e il centro messaggi. Ha autorizzazioni di "solo visualizzazione", tranne per l'apertura e la lettura dei ticket di supporto.
- **Amministratore Gestione utenti**: (Office 365 e Intune) reimposta le password, esegue il monitoraggio dell'integrità dei servizi, aggiunge ed elimina account utente e gestisce richieste di servizio. L'amministratore Gestione utenti non può eliminare un amministratore globale, creare altri ruoli di amministratore o reimpostare le password per altri amministratori.

Per impostazione predefinita, l'account usato per creare la sottoscrizione Microsoft Intune è un amministratore globale. È consigliabile non usare un amministratore globale per attività di gestione quotidiane. Un amministratore non deve avere una licenza per Intune per accedere alla console di amministrazione di Intune. Per altre informazioni, vedere la sezione relativa al tenant di Azure AD in [Che cos'è una directory di Azure AD?](http://technet.microsoft.com/library/jj573650.aspx).

Per accedere al portale di Office 365, per l'account deve essere impostato lo stato **Utenti con accesso consentito**. Nel portale di Intune in **Profilo** impostare **Blocca l'accesso** su **No** per consentire l'accesso. Questo stato non equivale a ricevere una licenza per la sottoscrizione. Per impostazione predefinita, tutti gli account utente hanno lo stato **Consentito**. Gli utenti senza privilegi di amministratore possono usare il portale di Office 365 per reimpostare le password di Intune.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizzare Active Directory e aggiungere utenti a Intune
È possibile configurare la sincronizzazione delle directory per importare account utente dall'istanza locale di Active Directory a Microsoft Azure Active Directory (Azure AD) che include gli utenti di Intune. La connessione del servizio locale Active Directory con tutti i servizi basati su Azure Active Directory consente di semplificare notevolmente la gestione delle identità utente. È anche possibile configurare le funzionalità SSO (Single Sign-On) per semplificare ulteriormente l'autenticazione per tutti gli utenti. Collegando lo stesso [tenant di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) con più servizi, gli account utente già sincronizzati sono disponibili a tutti i servizi basati su cloud.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Come sincronizzare gli utenti locali con Azure AD
L'unico strumento necessario per sincronizzare gli account utente con Azure AD è la [procedura guidata di Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). La procedura guidata di Azure AD Connect offre un'esperienza semplificata e guidata per connettere l'infrastruttura di identità locale al cloud.  Scegliere la topologia e le esigenze (una o più directory, sincronizzazione delle password o federazione). La procedura guidata distribuisce e configura tutti i componenti necessari per stabilire la connessione, inclusi i servizi di sincronizzazione, Active Directory Federation Services (AD FS) e il modulo Azure AD PowerShell.

> [!TIP]
> Azure AD Connect include funzionalità disponibili in precedenza con il nome di Dirsync e Azure AD Sync. Altre informazioni sull'[integrazione della directory](http://technet.microsoft.com/library/jj573653.aspx). Per informazioni sulla sincronizzazione degli account utente da una directory locale ad Azure AD, vedere [Analogie tra Active Directory e Azure AD](http://technet.microsoft.com/library/dn518177.aspx).