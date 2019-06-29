---
title: Filtrare i criteri con tag di ambito in Microsoft Intune - Azure | Microsoft Docs
description: Usare i tag di ambito per filtrare i profili di configurazione in base a ruoli specifici.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba1d7669e80fd91398f41c57ca2d27ce78a06041
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403781"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti

È possibile usare il controllo degli accessi in base al ruolo e i tag di ambito per assicurarsi che gli amministratori appropriati abbiano accesso e visibilità per gli oggetti di Intune corretti. I ruoli determinano quale accesso hanno gli amministratori a quali oggetti. I tag di ambito determinano quali oggetti possono vedere gli amministratori.

Ad esempio, si supponga che a un amministratore della filiale di Milano venga assegnato il ruolo di gestore dei criteri e dei profili. Si vuole che questo amministratore possa visualizzare e gestire solo i profili e i criteri applicabili esclusivamente ai dispositivi di Milano. A tale scopo, è necessario:

1. Creare un tag di ambito denominato Milano.
2. Creare un'assegnazione di ruolo per il ruolo di gestore dei criteri e dei profili: 
    - Membri (gruppi) = un gruppo di sicurezza denominato Amministratori IT Milano. Tutti gli amministratori in questo gruppo saranno autorizzati a gestire i criteri e i profili per gli utenti/dispositivi in Ambito (gruppi).
    - Ambito (gruppi) = un gruppo di sicurezza denominato Utenti Milano. I profili e i criteri per tutti gli utenti/dispositivi in questo gruppo possono essere gestiti dagli amministratori in Membri (gruppi). 
    - Ambito (tag) = Milano. Gli amministratori in Membri (gruppi) possono vedere i dispositivi che hanno anche il tag di ambito Milano.
3. Aggiungere il tag di ambito Milano ai criteri e profili a cui si vuole possano accedere gli amministratori in Membri (gruppi).
4. Aggiungere il tag di ambito Milano ai dispositivi che si vuole siano visibili per gli amministratori in Membri (gruppi). 


## <a name="to-create-a-scope-tag"></a>Per creare un tag di ambito

1. In Intune scegliere **Ruoli** > **Ambito (tag)**  > **Crea**.

    ![Screenshot della creazione di un tag di ambito.](./media/scope-tags/create-scope-tag.png)

3. Se si desidera che tutti i dispositivi in gruppi specifici, scegliere **assegnare tag di ambito per tutti i dispositivi nei gruppi selezionati**.
    1. Nel **selezionare i gruppi da includere** , scegliere i gruppi che i dispositivi che si desidera assegnare il tag di ambito su pagina.
    2. Scegliere **Seleziona**.
4. Scegliere **Crea**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Per assegnare un tag di ambito a un ruolo

1. In Intune, scegliere **Ruoli** > **Tutti i ruoli** > scegliere un ruolo > **Assegnazioni** > **Assegna**.

    ![Screenshot dell'assegnazione dell'ambito a un ruolo.](./media/scope-tags/assign-scope-to-role.png)

2. Specificare **Nome dell'assegnazione** e **Descrizione**.
3. Scegliere **Membri (gruppi)**  > **Aggiungi** > scegliere i gruppi desiderati per questa assegnazione > **selezionare** > **OK**. Gli utenti in questo gruppo saranno autorizzati a gestire i criteri e i profili per gli utenti/dispositivi in Ambito (gruppi).

    ![Screenshot della selezione dei gruppi membri.](./media/scope-tags/select-member-groups.png)

4. Se si vogliono gestire gli utenti o i dispositivi in un set specifico di gruppi, scegliere **Ambito (gruppi)**  > **Gruppi selezionati** > **Selezionare i gruppi da includere**> **scegliere i gruppi** > **OK**. I profili e i criteri per tutti gli utenti/dispositivi in questo gruppo possono essere gestiti dagli amministratori in Membri (gruppi).

    ![Screenshot della selezione dei gruppi di ambito.](./media/scope-tags/select-scope-groups.png)

    In alternativa, è possibile scegliere **Tutti i dispositivi**, **Tutti gli utenti** o **Tutti gli utenti e tutti i dispositivi**.

    ![Screenshot di altre opzioni per la selezione di gruppi di ambito.](./media/scope-tags/scope-group-other-options.png)
    
5. Scegliere **Ambito (tag)**  > **Aggiungi** > scegliere i tag che si vuole aggiungere a questo ruolo >**selezionare** > **OK**. Gli utenti in Membri (gruppi) avranno accesso ai criteri e ai profili con lo stesso tag di ambito.

    ![Screenshot della selezione dei tag di ambito.](./media/scope-tags/select-scope-tags.png)

6. Scegliere **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Per aggiungere un tag di ambito a un profilo di configurazione
1. In Intune scegliere **Configurazione del dispositivo** > **Profili** > scegliere un profilo.

    ![Screenshot della selezione di un profilo.](./media/scope-tags/choose-profile.png)

2. Scegliere **Proprietà** > **Ambito (tag)**  > **Aggiungi**.

    ![Screenshot dell'aggiunta di tag di ambito.](./media/scope-tags/add-scope-tags.png)

3. In **Seleziona tag** scegliere i tag che si vuole aggiungere al profilo.
4. Scegliere **Seleziona** > **OK** > **Salva**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Per assegnare un tag di ambito ai criteri di configurazione dell'app
Per i dispositivi con **Tipo di registrazione del dispositivo** impostato su **Dispositivi gestiti**:
1. Scegliere **App client** > **Criteri di configurazione dell'app** > scegliere i criteri di configurazione dell'app.
2. Scegliere **Proprietà** > **Ambito (tag)** > scegliere i tag che si vuole assegnare ai criteri.

Per i dispositivi con **Tipo di registrazione del dispositivo** impostato su **App gestite**:
1. Scegliere **App client** > **Criteri di configurazione dell'app** > scegliere i criteri di configurazione dell'app.
2. Scegliere **Ambito (tag)** > scegliere i tag che si vuole assegnare ai criteri.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Per assegnare un tag di ambito a un profilo di provisioning delle app iOS
1. In Intune scegliere **App client** > **Profili di provisioning delle app iOS** > scegliere un profilo.
2. Scegliere **Proprietà** > **Ambito (tag)** > scegliere i tag che si vuole assegnare al profilo.
3. Scegliere **Seleziona** > **OK** > **Salva**.

## <a name="to-assign-a-scope-tag-to-an-apple-volume-purchase-program-vpp-token"></a>Per assegnare un tag di ambito a un token Volume Purchase Program (VPP) di Apple
1. In Intune scegliere **App client** > **Token VPP Apple** > scegliere un token VPP.
2. Selezionare **Ambito (tag)** > scegliere i tag che si vuole assegnare al profilo. Le app VPP e gli eBook associati al token VPP ereditano i tag assegnati.
3. Scegliere **Seleziona** > **OK** > **Salva**.

## <a name="scope-tag-details"></a>Dettagli dei tag di ambito
Quando si lavora con i tag di ambito, tenere presente questi dettagli:

- È attualmente possibile assegnare i tag di ambito a:
    - Assegnazioni di ruolo
    - Criteri di conformità dei dispositivi
    - Profili di configurazione dispositivo
    - Anelli di aggiornamento di Windows 10
    - Dispositivi gestiti
    - App
    - Criteri di configurazione delle app - dispositivi gestiti
    - Script PowerShell
    - Token DEP
    - Profilo di provisioning delle app iOS
    - Token Volume Purchase Program (VPP) di Apple
- Quando un amministratore crea un oggetto in Intune, tutti i tag di ambito assegnati a tale amministratore verranno assegnati automaticamente al nuovo oggetto.
- Il controllo degli accessi in base al ruolo di Intune non si applica ai ruoli di Azure Active Directory. I ruoli di amministratore del servizio e amministratore globale di Intune hanno quindi accesso amministrativo completo a Intune, indipendentemente dai tag di ambito assegnati.
- Gli amministratori in un'assegnazione di ruolo con tag di ambito possono anche vedere gli oggetti di Intune senza tag di ambito.
- È solo possibile assegnare un tag di ambito incluso nelle assegnazioni di ruolo.
- I gruppi di destinazione possono essere solo quelli inclusi in Ambito (gruppi) nell'assegnazione di ruolo.
- Se al ruolo è assegnato un tag di ambito, non è possibile eliminare tutti i tag di ambito per un oggetto di Intune. È necessario almeno un tag di ambito.

## <a name="next-steps"></a>Passaggi successivi

Gestire i propri [ruoli](role-based-access-control.md) e [profili](device-profile-assign.md).
