---
title: Controllo degli accessi in base al ruolo con Microsoft Intune
description: Informazioni su come il controllo degli accessi in base al ruolo (RBAC) consente di controllare gli utenti che possono eseguire le azioni e apportare modifiche in Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/27/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08e6c7657eeba7a41b9927e736fe7f4fc07e25e6
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848577"
---
# <a name="role-based-administration-control-rbac-with-microsoft-intune"></a>Controllo degli accessi in base al ruolo (RBAC) con Microsoft Intune

RBAC consente di controllare chi esegue varie attività di Intune all'interno dell'organizzazione e a chi si applicano queste attività. È possibile usare i ruoli predefiniti che coprono alcuni scenari comuni in Intune oppure creare ruoli personalizzati. Un ruolo è definito da:

- **Definizione del ruolo**: nome del ruolo, risorse gestite dal ruolo e autorizzazioni concesse per ogni risorsa.
- **Membri**: gruppi di utenti a cui vengono concesse le autorizzazioni.
- **Ambito**: gruppi di utenti o dispositivi che i membri possono gestire.
- **Assignment**: dopo aver configurato la definizione, i membri e l'ambito, il ruolo viene assegnato.

![Esempio di controllo RBAC di Intune](./media/intune-rbac-1.PNG)

A partire dal nuovo portale di Azure, **Azure Active Directory (Azure AD)** offre due ruoli della directory che è possibile usare con Intune. A questi ruoli vengono concesse autorizzazioni complete per eseguire tutte le attività in Intune:

- **Amministratore globale**: gli utenti con questo ruolo hanno accesso a tutte le funzionalità amministrative di Azure AD, nonché ai servizi federati con Azure AD come Exchange Online, SharePoint Online e Skype for Business Online. La persona che si registra per il tenant di Azure AD diventa un amministratore globale. Solo gli amministratori globali possono assegnare altri ruoli di amministratore di Azure AD. Nell'organizzazione vi possono essere più amministratori globali. Gli amministratori globali possono reimpostare la password per tutti gli utenti e tutti gli altri amministratori.

- **Amministratore del servizio Intune**: gli utenti con questo ruolo hanno autorizzazioni globali all'interno di Intune quando il servizio è presente. Inoltre, se non sono presenti altre restrizioni di Azure prioritarie, questo ruolo offre la possibilità di gestire utenti e dispositivi, nonché di creare e gestire gruppi di Intune.

- **Amministratore accesso condizionale**: gli utenti con questo ruolo hanno solo le autorizzazioni per visualizzare, creare, modificare ed eliminare i criteri di accesso condizionale.

    > [!IMPORTANT]
    > Il ruolo Amministratore del servizio Intune non offre la possibilità di gestire le impostazioni di accesso condizionale di Azure AD.
    > Per potergli assegnare un ruolo di Intune, l'utente deve avere una licenza di Intune.

    > [!TIP]
    > Intune mostra inoltre tre estensioni di Azure AD: **Utenti**, **Gruppi** e **Accesso condizionale**, controllate tramite il controllo degli accessi in base al ruolo di Azure AD. Il ruolo **Amministratore account utente**, inoltre, consente di eseguire solo attività su utenti e gruppi di AAD e non dispone delle autorizzazioni complete per eseguire tutte le attività in Intune. Per altre informazioni, vedere [Autorizzazioni del ruolo di amministratore in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles).

## <a name="roles-created-in-the-intune-classic-portal"></a>Ruoli creati nel portale classico di Intune

Solo gli utenti **Amministratori del servizio** con autorizzazioni "Completo" vengono inclusi nella migrazione dal portale classico di Intune a Intune nel portale di Azure. È necessario assegnare nuovamente gli utenti **Amministratori del servizio** di Intune con accesso "Sola lettura" o "Supporto tecnico" nei ruoli di Intune nel portale di Azure e rimuoverli dal portale classico.

> [!IMPORTANT]
> Potrebbe essere necessario mantenere l'accesso Amministratori del servizio Intune nel portale classico, se gli amministratori hanno ancora la necessità di gestire i PC con Intune.

## <a name="built-in-roles"></a>Ruoli predefiniti

È possibile assegnare ruoli predefiniti a gruppi senza ulteriore configurazione. Non è possibile eliminare o modificare un ruolo predefinito.

- **Help Desk Operator** (Operatore help desk): consente di eseguire attività remote su utenti e dispositivi e assegnare applicazioni o criteri a utenti o dispositivi.
- **Policy and Profile Manager** (Gestione criteri e profili): consente di gestire i criteri di conformità, i profili di configurazione, la registrazione Apple e gli identificatori dei dispositivi aziendali.
- **Read Only Operator** (Operatore sola lettura): consente di visualizzare informazioni su utenti, dispositivi, registrazione, configurazione e applicazioni. Non consente di apportare modifiche a Intune.
- **Application Manager** (Gestione applicazioni): consente di gestire le applicazioni per dispositivi mobili e gestite, di leggere le informazioni sui dispositivi e di visualizzare i profili di configurazione dei dispositivi.
- **Intune Role Administrator** (Amministratore dei ruoli di Intune): consentire di gestire i ruoli di Intune personalizzati e di aggiungere assegnazioni per i ruoli di Intune predefiniti. È l'unico ruolo di Intune che può assegnare autorizzazioni agli amministratori.
- **School Administrator** (Amministratore di istituto di istruzione): consente di gestire i dispositivi Windows 10 in [Intune per Education](introduction-intune-education.md) e di eseguire le azioni seguenti: 

    |Autorizzazione|Operazione|
    |---|---|
    |Dati controllo|Lettura|
    |DeviceConfigurations|Assegnazione, creazione, eliminazione, lettura, aggiornamento|
    |Manager di registrazione dispositivi|Lettura, aggiornamento|
    |Dispositivi gestiti|Lettura, aggiornamento<!--, Delete [To be added in 1803]-->|
    |App per dispositivi mobili|Assegnazione, creazione, eliminazione, lettura, aggiornamento|
    |Reports|Lettura|
    |Azioni remote|Pulizia PC, riavvio, blocco remoto, ritiro, sincronizzazione dispositivi, cancellazione|
    |Organizzazione|Lettura|

### <a name="to-assign-a-built-in-role"></a>Per assegnare un ruolo predefinito

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Ruoli** > **Tutti i ruoli**.
4. Nel riquadro **Ruoli di Intune - Tutti i ruoli** scegliere il ruolo predefinito da assegnare.

5. Nel riquadro <*nome ruolo*> - **Panoramica** scegliere **Gestisci** e quindi **Assegnazioni**.

6. Nel riquadro del ruolo personalizzato scegliere **Assegna**.

7. Nel riquadro **Assegnazioni di ruolo** immettere un **nome** e una **descrizione** facoltativa per l'assegnazione.

8. Per **Membri** scegliere un gruppo contenente l'utente a cui si vogliono assegnare le autorizzazioni.

9. Per **Ambito** scegliere un gruppo contenente gli utenti che il membro indicato in precedenza è autorizzato a gestire.
<br></br>
10. Al termine, scegliere **OK**. La nuova assegnazione viene visualizzata nell'elenco di assegnazioni.

### <a name="intune-rbac-table"></a>Tabella del controllo RBAC di Intune

- Scaricare la [tabella del controllo RBAC di Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) per visualizzare altri dettagli sulle operazioni consentite per ogni ruolo.

## <a name="custom-roles"></a>Ruoli personalizzati

È possibile creare un ruolo personalizzato che include le autorizzazioni necessarie per un ruolo professionale specifico. Ad esempio, se un gruppo del reparto IT gestisce le applicazioni, i criteri e i profili di configurazione, è possibile aggiungere tutte queste autorizzazioni insieme in un ruolo personalizzato.

> [!IMPORTANT]
> Per creare, modificare o assegnare ruoli, l'account deve disporre di una delle seguenti autorizzazioni in Azure AD:
> - **Amministratore globale**
> - **Amministratore del servizio Intune**

### <a name="to-create-a-custom-role"></a>Per creare un ruolo personalizzato

1. Accedere al [portale di Azure](https://portal.azure.com) con le credenziali di Intune.

2. Scegliere **Tutti i servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune** > **Ruoli** > **Tutti i ruoli** > **Aggiungi personalizzato**.

4. Nel riquadro **Aggiungi un ruolo personalizzato** immettere un nome e una descrizione per il nuovo ruolo e quindi fare clic su **Autorizzazioni**.

5. Nel riquadro **Autorizzazioni** scegliere le autorizzazioni da usare con il ruolo. Usare la [tabella del controllo RBAC di Intune](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a) per decidere le autorizzazioni da applicare.

6. Al termine, scegliere **OK**.

7. Nel riquadro **Aggiungi un ruolo personalizzato** fare clic su **Crea**. Il nuovo ruolo verrà visualizzato nell'elenco del riquadro **Ruoli di Intune- Tutti i ruoli**.

### <a name="to-assign-a-custom-role"></a>Per assegnare un ruolo personalizzato

1. Nel riquadro **Ruoli di Intune - Tutti i ruoli** scegliere il ruolo personalizzato da assegnare.

2. Nel riquadro <*nome ruolo*> - **Panoramica** scegliere **Gestisci** e quindi **Assegnazioni**. In questo riquadro è anche possibile modificare o eliminare ruoli esistenti.

3. Nel riquadro del ruolo personalizzato scegliere **Assegna**.

4. Nel riquadro **Assegnazioni di ruolo** immettere un **nome** e una **descrizione** facoltativa per l'assegnazione.

5. Per **Membri** scegliere un gruppo contenente l'utente a cui si vogliono assegnare le autorizzazioni.

6. Per **Ambito** scegliere un gruppo contenente gli utenti che il membro indicato in precedenza è autorizzato a gestire.

7. Al termine, scegliere **OK**. La nuova assegnazione viene visualizzata nell'elenco di assegnazioni.

## <a name="next-steps"></a>Passaggi successivi

[Usare il ruolo di operatore del supporto tecnico con il portale per la risoluzione dei problemi](help-desk-operators.md)

## <a name="see-also"></a>Vedere anche

[Assegnare i ruoli con Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)
