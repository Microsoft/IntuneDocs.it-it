---
title: Filtrare i criteri con tag di ambito in Microsoft Intune - Azure | Microsoft Docs
description: Usare i tag di ambito per filtrare i profili di configurazione in base a ruoli specifici.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb57ea2ef5c99c58968ee25b3a75b2165ece787a
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658550"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>Usare il controllo di accesso basato sui ruoli (RBAC) e i tag di ambito per distribuite IT

È possibile usare i tag di controllo e l'ambito di accesso basato sui ruoli per assicurarsi che gli amministratori a destra dispongono dell'accesso a destra e la visibilità agli oggetti di Intune a destra. I ruoli determinano quale accesso degli amministratori hanno a quali oggetti. I tag di ambito determinano quali oggetti gli amministratori possono vedere.

Ad esempio, si supponga che un amministratore di office a livello di area di Seattle viene assegnato il ruolo Gestione profili e criteri. Si desidera che questo amministratore di visualizzare e gestire solo i profili e i criteri che si applicano solo ai dispositivi di Seattle. A tale scopo, è necessario:

1. Creare un tag di ambito denominato Seattle.
2. Creare un'assegnazione di ruolo per il ruolo Gestione profili e criteri con: 
    - Membri (gruppi) = un gruppo di sicurezza denominato gli amministratori IT di Seattle. Tutti gli amministratori di questo gruppo sarà autorizzato a gestire i criteri e profili per utenti o dispositivi nell'ambito (gruppi).
    - Ambito (gruppi) = un sicurezza gruppo utenti di Seattle denominata. Tutti gli utenti/dispositivi di questo gruppo può avere i profili e criteri gestiti dagli amministratori dei membri (gruppi). 
    - Ambito (tag) = Seattle. Gli amministratori del membro (gruppi) è possono visualizzare i dispositivi che hanno anche il tag di ambito di Seattle.
3. Aggiungere il tag di ambito Seattle ai criteri e profili da amministratori in membri (gruppi) sia in grado di accedere.
4. Aggiungere il tag di ambito Seattle ai dispositivi che devono essere visibili agli amministratori dei membri (gruppi). 


## <a name="to-create-a-scope-tag"></a>Per creare un tag di ambito

1. In Intune, scegliere **ruoli** > **ambito (tag)** > **Create**.

    ![Screenshot di crea un tag di ambito.](./media/scope-tags/create-scope-tag.png)

2. Specificare un **nome** e una **descrizione**.
3. Scegliere **Crea**.

## <a name="to-assign-a-scope-tag-to-a-role"></a>Per assegnare un tag di ambito a un ruolo

1. In Intune, scegliere **ruoli** > **tutti i ruoli** > scegliere un ruolo > **assegnazioni** > **assegnare**.

    ![Screenshot di assegnare l'ambito a un ruolo.](./media/scope-tags/assign-scope-to-role.png)

2. Fornire un' **nome dell'assegnazione** e **descrizione**.
3. Scegli **membri (gruppi)** > **Add** > scegliere i gruppi desiderati nell'ambito di questa assegnazione > **selezionare**  >   **OK**. mUsers in questo gruppo saranno autorizzati a gestire i criteri e profili per utenti o dispositivi nell'ambito (gruppi).

    ![Screenshot dei gruppi membro selezionato.](./media/scope-tags/select-member-groups.png)

4. Se si desidera gestire utenti o dispositivi in un set specifico di gruppi, scegliere **ambito (gruppi)** > **gruppi selezionati** > **selezionare i gruppi da includere**> scegliere i gruppi > **selezionate** > **OK**. Tutti gli utenti/dispositivi di questo gruppo può avere i profili e criteri gestiti dagli amministratori dei membri (gruppo).

    ![Screenshot dei gruppi di ambito select.](./media/scope-tags/select-scope-groups.png)

    In alternativa, è possibile scegliere **tutti i dispositivi**, **tutti gli utenti**, o **tutti gli utenti e tutti i dispositivi**.

    ![Schermata di altre opzioni per i gruppi di ambito select.](./media/scope-tags/scope-group-other-options.png)
    
5. Scegli **ambito (tag)** > **Add** > scegliere i tag che si desidera aggiungere a questo ruolo > **selezionare** > **OK**. Gli utenti di membri (gruppi) saranno possibile accedere a criteri e profili che presentano lo stesso tag di ambito.

    ![Schermata di tag di ambito select.](./media/scope-tags/select-scope-tags.png)

6. Scegliere **OK**. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>Per aggiungere un tag di ambito a un profilo di configurazione
1. In Intune, scegliere **configurazione del dispositivo** > **profili** > scegliere un profilo.

    ![Screenshot del profilo di selezione.](./media/scope-tags/choose-profile.png)

2. Scegli **delle proprietà** > **ambito (tag)** > **aggiungere**.

    ![Screenshot di Aggiungi tag di ambito.](./media/scope-tags/add-scope-tags.png)

3. Sotto **selezionare i tag**, scegliere i tag che si desidera aggiungere al profilo.
4. Scegli **selezionate** > **OK** > **Salva**.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>Per assegnare un tag di ambito per i criteri di configurazione
Per i dispositivi con **tipo di registrazione del dispositivo** impostata su **i dispositivi gestiti**:
1. Scegli **App Client** > **i criteri di configurazione App** > scegliere un criterio di configurazione app.
2. Scegli **delle proprietà** > **ambito (tag)** > scegliere i tag che si desidera assegnare al criterio.

Per i dispositivi con **tipo di registrazione del dispositivo** impostata su **le app gestite**:
1. Scegli **App Client** > **i criteri di configurazione App** > scegliere un criterio di configurazione app.
2. Scegli **ambito (tag)** > scegliere i tag che si desidera assegnare al criterio.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>Per assegnare un tag di ambito a una profilo di provisioning delle app iOS
1. In Intune, scegliere **App Client** > **app per iOS i profili di provisioning** > scegliere un profilo.
2. Scegli **delle proprietà** > **ambito (tag)** > scegliere i tag che si desidera assegnare al profilo.
3. Scegli **selezionate** > **OK** > **Salva**.

## <a name="scope-tag-details"></a>Dettagli dei tag di ambito
Quando si lavora con i tag di ambito, tenere presente questi dettagli:

- È attualmente possibile assegnare i tag di ambito per:
    - Assegnazioni di ruolo
    - Criteri di conformità dei dispositivi
    - Profili di configurazione dispositivo
    - Anelli gli aggiornamenti di Windows 10
    - Dispositivi gestiti
    - App
    - Criteri di configurazione: i dispositivi gestiti
    - Script PowerShell
    - Token DEP
    - Profilo di provisioning delle app iOS
- Quando un amministratore crea un oggetto in Intune, tutti i tag di ambito assegnati a ogni amministratore verranno assegnati automaticamente al nuovo oggetto.
- Intune RBAC non si applica ai ruoli di Azure Active Directory. Pertanto, i ruoli del servizio Intune e gli amministratori globali hanno accesso amministrativo completo a Intune, indipendentemente dal quale hanno i tag di ambito.
- Gli amministratori in un'assegnazione di ruolo con i tag di ambito è anche possono visualizzare gli oggetti di Intune senza tag di ambito.
- È possibile assegnare solo un tag di ambito che si dispone di assegnazioni di ruolo.
- È possibile solo i gruppi di destinazione che sono elencati nell'ambito (gruppi) dell'assegnazione di ruolo.
- Se si dispone di un tag di ambito assegnato al ruolo, è possibile eliminare tutti i tag di ambito su un oggetto di Intune. È necessario almeno un ambito tag.

## <a name="next-steps"></a>Passaggi successivi

Gestire i propri [ruoli](role-based-access-control.md) e [profili](device-profile-assign.md).
