---
title: Aggiungere utenti e concedere le autorizzazioni
titleSuffix: Microsoft Intune
description: Sincronizzare gli utenti locali con Azure AD e concedere autorizzazioni di amministratore per la sottoscrizione di Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/28/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5b469c759ac34a6d8de09163534a580346e48a1
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73415030"
---
# <a name="add-users-and-grant-administrative-permission-to-intune"></a>Aggiungere utenti e concedere autorizzazioni amministrative a Intune

Come amministratore, è possibile aggiungere direttamente o sincronizzare utenti da Active Directory locale. Una volta aggiunti, gli utenti possono registrare i dispositivi e accedere alle risorse aziendali. È anche possibile assegnare agli utenti autorizzazioni aggiuntive, tra cui *amministratore globale* e *amministratore del servizio*.

## <a name="add-users-to-intune"></a>Aggiungere utenti a Intune

È possibile aggiungere manualmente utenti alla sottoscrizione di Intune tramite l'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) o il [portale di Azure](https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview). Un amministratore può modificare gli account utente per assegnare le licenze di Intune. È possibile assegnare le licenze dall'interfaccia di amministrazione di Microsoft 365 o dal portale di Azure per Intune. Per altre informazioni sull'uso dell'interfaccia di amministrazione di Microsoft 365, vedere [Add users individually or in bulk to the Microsoft 365 admin center](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec) (Aggiungere utenti singolarmente o in blocco all'interfaccia di amministrazione di Microsoft 365).

### <a name="add-intune-users-in-the-microsoft-365-admin-center"></a>Aggiungere gli utenti di Intune nell'interfaccia di amministrazione di Microsoft 365

1. Accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) con un account di amministratore globale o amministratore Gestione utenti.
2. Nel menu di Office 365 selezionare **Amministratore**.
3. Nell'interfaccia di amministrazione selezionare **Aggiungi un utente**.

   ![Screenshot della sezione Aggiungi un utente](./media/users-add/office-add-user.png)

4. Specificare i dettagli utente seguenti:
   - **Nome**
   - **Cognome**
   - **Nome visualizzato**
   - **Nome utente** - Nome dell'entità utente (UPN) archiviato in Azure Active Directory usato per accedere al servizio
   - **Posizione**
   - **Informazioni sui contatti** (facoltativo)
   - **Password**: generata automaticamente oppure specificare

     ![Screenshot della sezione Nuovo utente](./media/users-add/office-add-user-details.png)

5. Assegnare una licenza di Intune. Selezionare **Product licenses** (Licenze del prodotto) e scegliere la licenza del prodotto. È necessaria una licenza che include Intune.
6. Scegliere **Aggiungi** per creare un nuovo utente.

### <a name="add-intune-users-in-the-azure-portal"></a>Aggiungere utenti Intune nel portale di Azure

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Utenti** > **Tutti gli utenti**.
3. Nell'interfaccia di amministrazione selezionare **Nuovo utente**.
   ![Screenshot dell'aggiunta di un nuovo utente](./media/users-add/intune-add-user.png)
4. Specificare i dettagli utente seguenti:
   - **Nome**
   - **Nome utente**: il nuovo nome nel portale di Azure Active Directory ![Screenshot di aggiunta di un nome e nome utente](./media/users-add/intune-add-user-info.png) Scegliere **OK** per continuare.
5. Facoltativamente, è possibile specificare le proprietà utente seguenti:
   - **Profilo**: informazioni di lavoro come **Posizione** e **Reparto**
   - **Gruppi**: selezionare i gruppi da aggiungere per l'utente
   - **Ruolo della directory**: assegnare all'utente le autorizzazioni amministrative incluso un ruolo di amministratore del servizio Intune.

   Selezionare **Crea** per aggiungere il nuovo utente a Intune.
6. Selezionare **Profilo** e quindi scegliere una **Località di utilizzo** per il nuovo utente. È necessario specificare la località di utilizzo prima di poter assegnare al nuovo utente una licenza di Intune. Scegliere **Salva** per continuare.
    ![Screenshot di Località di utilizzo](./media/users-add/intune-add-user-loc.png)
7. Selezionare **Licenze** e quindi scegliere **Assegna** per assegnare una licenza di Intune per questo utente. Una licenza di Intune è necessaria per registrare i dispositivi o accedere alle risorse aziendali. Selezionare **Prodotti**, scegliere il tipo di licenza, scegliere **Seleziona** e quindi **Assegna**.

## <a name="grant-admin-permissions"></a>Concedere le autorizzazioni di amministratore

Dopo aver aggiunto altri utenti alla sottoscrizione di Intune, è consigliabile concedere le autorizzazioni di amministratore ad alcuni utenti.  Per concedere le autorizzazioni di amministratore, seguire questa procedura:

### <a name="give-admin-permissions-in-office-365"></a>Assegnare le autorizzazioni di amministratore in Office 365

1. Accedere all'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com) con un account di amministratore globale.
2. Nel menu di Office 365 selezionare **Amministratore**.
3. Nell'interfaccia di amministrazione scegliere **Utenti attivi** e quindi scegliere l'utente a cui concedere le autorizzazioni di amministratore.

4. Nella colonna **Ruoli** scegliere **Modifica**.

    ![Screenshot di Utente amministratore](./media/users-add/office-assign-roles-open.png)

5. Scegliere l'autorizzazione di amministratore da concedere nell'elenco dei ruoli disponibili.
![Screenshot di assegnazione ruoli](./media/users-add/office-assign-roles.png)
6. Scegliere **Salva**.

### <a name="give-admin-permissions-in-the-azure-portal"></a>Assegnare le autorizzazioni di amministratore nel portale di Azure

1. Accedere al [portale di Azure](https://portal.azure.com) con un account di amministratore globale.
2. Nel portale di Azure scegliere **Utente** e quindi scegliere l'utente a cui concedere le autorizzazioni di amministratore.
3. Selezionare **Ruolo della directory** e quindi selezionare l'autorizzazione.
  ![Screenshot di Ruolo della directory](./media/users-add/add-intune-directory-role.png)
4. Scegliere **Salva**.

### <a name="types-of-administrators"></a>Tipi di amministratori

Assegnare agli utenti una o più autorizzazioni di amministratore. Queste autorizzazioni definiscono l'ambito amministrativo per gli utenti e le attività che possono gestire. Le autorizzazioni di amministratore sono comuni tra i vari servizi cloud di Microsoft e alcuni servizi potrebbero non supportare alcune autorizzazioni. Sia nel portale di Azure che nell'interfaccia di amministrazione di Microsoft 365 sono elencati ruoli di amministratore limitati che non vengono usati da Intune. Le opzioni disponibili per le autorizzazioni di amministratore di Intune sono le seguenti:

- **Amministratore globale**: (Office 365 e Intune) accede a tutte le funzionalità amministrative in Intune. Per impostazione predefinita, la persona che si registra a Intune diventa un amministratore globale. Gli amministratori globali sono gli unici amministratori che possono assegnare altri ruoli di amministratore. Nell'organizzazione vi possono essere più amministratori globali. Come procedura consigliata, solo alcuni utenti dell'azienda dovrebbero avere questo ruolo per ridurre il rischio per l'azienda.
- **Amministratore password**: (Office 365 e Intune) reimposta le password, gestisce le richieste di servizio ed esegue il monitoraggio dell'integrità dei servizi. Gli amministratori password sono limitati alla reimpostazione delle password per gli utenti.
- **Amministratore dei servizi**: (Office 365 e Intune) apre le richieste di supporto a Microsoft e visualizza il dashboard servizi e il centro messaggi. Ha autorizzazioni di "solo visualizzazione", tranne per l'apertura e la lettura dei ticket di supporto.
- **Amministratore fatturazione**: (Office 365 e Intune) effettua acquisti, gestisce sottoscrizioni, gestisce ticket di supporto ed esegue il monitoraggio dell'integrità dei servizi.
- **Amministratore utenti**: (Office 365 e Intune) reimposta le password, esegue il monitoraggio dell'integrità dei servizi, aggiunge ed elimina account utente e gestisce richieste di servizio. L'amministratore Gestione utenti non può eliminare un amministratore globale, creare altri ruoli di amministratore o reimpostare le password per altri amministratori.
- **Amministratore del servizio Intune**: tutte le autorizzazioni di amministratore globale di Intune ad eccezione dell'autorizzazione per creare gli amministratori con le opzioni **Ruolo della directory**.

L'account usato per creare la sottoscrizione di Microsoft Intune è un amministratore globale. È consigliabile non usare un amministratore globale per attività di gestione quotidiane. Un amministratore non deve avere necessariamente una licenza per Intune per accedere al portale di Azure, ma per poter eseguire determinate attività di gestione come l'impostazione del connettore del servizio Exchange, la licenza di Intune è necessaria.

Per accedere all'interfaccia di amministrazione di Microsoft 365, per l'account deve essere impostato **Accesso consentito**. Nel portale di Azure in **Profilo** impostare **Blocca l'accesso** su **No** per consentire l'accesso. Questo stato non equivale a ricevere una licenza per la sottoscrizione. Per impostazione predefinita, tutti gli account utente hanno lo stato **Consentito**. Gli utenti senza privilegi di amministratore possono usare l'interfaccia di amministrazione di Microsoft 365 per reimpostare le password di Intune.

## <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizzare Active Directory e aggiungere utenti a Intune

È possibile configurare la sincronizzazione delle directory per importare account utente dall'istanza locale di Active Directory a Microsoft Azure Active Directory (Azure AD) che include gli utenti di Intune. La connessione del servizio locale Active Directory con tutti i servizi basati su Azure Active Directory consente di semplificare notevolmente la gestione delle identità utente. È anche possibile configurare le funzionalità SSO (Single Sign-On) per semplificare ulteriormente l'autenticazione per tutti gli utenti. Collegando lo stesso [tenant di Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) con più servizi, gli account utente già sincronizzati sono disponibili a tutti i servizi basati su cloud.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Come sincronizzare gli utenti locali con Azure AD

L'unico strumento necessario per sincronizzare gli account utente con Azure AD è la [procedura guidata di Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). La procedura guidata di Azure AD Connect offre un'esperienza semplificata e guidata per connettere l'infrastruttura di identità locale al cloud. Scegliere la topologia e le esigenze (una o più directory, sincronizzazione degli hash delle password, autenticazione pass-through o federazione). La procedura guidata distribuisce e configura tutti i componenti necessari per stabilire la connessione, inclusi i servizi di sincronizzazione, Active Directory Federation Services (AD FS) e il modulo Azure AD PowerShell.

> [!TIP]
> Azure AD Connect include funzionalità disponibili in precedenza con il nome di Dirsync e Azure AD Sync. Altre informazioni sull'[integrazione della directory](https://technet.microsoft.com/library/jj573653.aspx). Per informazioni sulla sincronizzazione degli account utente da una directory locale ad Azure AD, vedere [Analogie tra Active Directory e Azure AD](https://technet.microsoft.com/library/dn518177.aspx).
