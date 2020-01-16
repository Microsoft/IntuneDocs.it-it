---
title: Usare il controllo degli accessi in base al ruolo e i tag di ambito per distribuirlo in Intune | Microsoft Docs
description: Usare i tag di ambito per filtrare i profili di configurazione in base a ruoli specifici.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1f81d26227bb206aa55ca495f4a4ee5e8ae9907
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548133"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti

È possibile usare il controllo degli accessi in base al ruolo e i tag di ambito per assicurarsi che gli amministratori appropriati abbiano accesso e visibilità per gli oggetti di Intune corretti. I ruoli determinano quale accesso hanno gli amministratori a quali oggetti. I tag di ambito determinano quali oggetti possono vedere gli amministratori.

Ad esempio, si supponga che un amministratore della filiale di Milano abbia il ruolo di gestore dei criteri e dei profili. Si vuole che questo amministratore possa visualizzare e gestire solo i profili e i criteri applicabili esclusivamente ai dispositivi di Milano. Per configurare questo accesso, è necessario:

1. Creare un tag di ambito denominato Milano.
2. Creare un'assegnazione di ruolo per il ruolo di gestore dei criteri e dei profili: 
    - Membri (gruppi) = un gruppo di sicurezza denominato Amministratori IT Milano. Tutti gli amministratori in questo gruppo saranno autorizzati a gestire i criteri e i profili per gli utenti/dispositivi in Ambito (gruppi).
    - Ambito (gruppi) = un gruppo di sicurezza denominato Utenti Milano. I profili e i criteri per tutti gli utenti/dispositivi in questo gruppo possono essere gestiti dagli amministratori in Membri (gruppi). 
    - Ambito (tag) = Milano. Gli amministratori in Membri (gruppi) possono vedere gli oggetti di Intune che hanno anche il tag di ambito Milano.
3. Aggiungere il tag di ambito Milano ai criteri e profili a cui si vuole abbiano accesso gli amministratori in Membri (gruppi).
4. Aggiungere il tag di ambito Milano ai dispositivi che si vuole siano visibili per gli amministratori in Membri (gruppi). 

## <a name="default-scope-tag"></a>Tag di ambito predefinito
Il tag di ambito predefinito viene aggiunto automaticamente a tutti gli oggetti senza tag che supportano i tag di ambito.

La funzionalità per il tag di ambito predefinito è simile alla funzionalità degli ambiti di sicurezza in Microsoft Endpoint Configuration Manager. 

## <a name="to-create-a-scope-tag"></a>Per creare un tag di ambito

1. Nell'interfaccia [di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)scegliere **Amministrazione Tenant** > **ruoli** > **ambito (tag)**  > **Crea**.

    ![Screenshot della creazione di un tag di ambito.](./media/scope-tags/create-scope-tag.png)

2. Specificare un **Nome** e una **Descrizione** facoltativa.
3. Se si vogliono tutti i dispositivi in gruppi specifici, scegliere **Assegna tag ambito a tutti i dispositivi nei gruppi selezionati**.
    1. Nella pagina **Seleziona gruppi da includere** scegliere i gruppi che contengono i dispositivi a cui si vuole assegnare questo tag ambito.
    2. Scegliere **Seleziona**.
4. Scegliere **Crea**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Per assegnare un tag di ambito a un ruolo

1. Nell'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)scegliere **amministrazione Tenant** **ruoli** >  > **tutti i ruoli** > scegliere un ruolo > **assegnazioni** > **assegna**.
2. Specificare **Nome dell'assegnazione** e **Descrizione**.
3. Scegliere **Membri (gruppi)**  > **Aggiungi** > scegliere i gruppi desiderati per questa assegnazione > **selezionare** > **OK**. Gli utenti di questo gruppo avranno le autorizzazioni per gestire utenti/dispositivi nell'ambito (gruppi).

    ![Screenshot della selezione dei gruppi membri.](./media/scope-tags/select-member-groups.png)

4. Se si vogliono gestire gli utenti o i dispositivi in un set specifico di gruppi, scegliere **Ambito (gruppi)**  > **Gruppi selezionati** > **Selezionare i gruppi da includere**> **scegliere i gruppi** > **OK**. Tutti gli utenti e i dispositivi di questo gruppo verranno gestiti dagli amministratori nei membri (gruppo).

    ![Screenshot della selezione dei gruppi di ambito.](./media/scope-tags/select-scope-groups.png)

    In alternativa, è possibile scegliere **Tutti i dispositivi**, **Tutti gli utenti** o **Tutti gli utenti e tutti i dispositivi**.

    ![Screenshot di altre opzioni per la selezione di gruppi di ambito.](./media/scope-tags/scope-group-other-options.png)
    
5. Scegliere **Ambito (tag)**  > **Aggiungi** > scegliere i tag che si vuole aggiungere a questo ruolo >**selezionare** > **OK**. Gli utenti dei membri (gruppi) avranno accesso agli oggetti di Intune che hanno anche lo stesso tag di ambito.

    ![Screenshot della selezione dei tag di ambito.](./media/scope-tags/select-scope-tags.png)

6. Scegliere **OK**. 

## <a name="assign-scope-tags-to-other-objects"></a>Assegnare i tag dell'ambito ad altri oggetti

Per gli oggetti che supportano i tag di ambito, i tag di ambito vengono in genere visualizzati in **Proprietà**. Ad esempio, per assegnare un tag scope a un profilo di configurazione, seguire questa procedura:

1. Nell'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)scegliere **dispositivi** > **profili di configurazione** > scegliere un profilo.

2. Scegliere **Proprietà** > **Ambito (tag)**  > **Aggiungi**.

    ![Screenshot dell'aggiunta di tag di ambito.](./media/scope-tags/add-scope-tags.png)

3. In **Seleziona tag** scegliere i tag che si vuole aggiungere al profilo.
4. Scegliere **Seleziona** > **OK** > **Salva**.


## <a name="scope-tag-details"></a>Dettagli dei tag di ambito
Quando si lavora con i tag di ambito, tenere presente questi dettagli: 

- È possibile assegnare tag di ambito a un tipo di oggetto Intune se il tenant può avere più versioni di tale oggetto, ad esempio le assegnazioni di ruolo o le app.
  Gli oggetti di Intune seguenti sono eccezioni a questa regola e attualmente non supportano i tag di ambito:
    - Profili ESP di Windows
    - Categorie di dispositivi
    - Restrizioni di registrazione
    - Identificatori dei dispositivi Corp
    - Dispositivi Autopilot
    - Percorsi di conformità del dispositivo
    - Dispositivi JAMF
- Le app VPP e gli eBook associati al token VPP ereditano i tag di ambito assegnati al token VPP associato.
- I dispositivi Device Enrollment Program (DEP) e i profili DEP associati al token DEP ereditano i tag di ambito assegnati al token DEP associato.
- Quando un amministratore crea un oggetto in Intune, tutti i tag di ambito assegnati a tale amministratore verranno assegnati automaticamente al nuovo oggetto.
- Il controllo degli accessi in base al ruolo di Intune non si applica ai ruoli di Azure Active Directory. I ruoli di amministratore del servizio e amministratore globale di Intune hanno quindi accesso amministrativo completo a Intune, indipendentemente dai tag di ambito assegnati.
- Se un'assegnazione di ruolo non dispone di un tag scope, l'amministratore IT può visualizzare tutti gli oggetti in base alle autorizzazioni dell'amministratore IT. Gli amministratori senza tag di ambito hanno essenzialmente tutti i tag di ambito.
- È solo possibile assegnare un tag di ambito incluso nelle assegnazioni di ruolo.
- I gruppi di destinazione possono essere solo quelli inclusi in Ambito (gruppi) nell'assegnazione di ruolo.
- Se al ruolo è assegnato un tag di ambito, non è possibile eliminare tutti i tag di ambito per un oggetto di Intune. È necessario almeno un tag di ambito.

## <a name="next-steps"></a>Passaggi successivi

Informazioni sul comportamento dei tag di ambito quando sono presenti [più assegnazioni di ruolo](role-based-access-control.md#multiple-role-assignments).
Gestire i propri [ruoli](role-based-access-control.md) e [profili](../configuration/device-profile-assign.md).
