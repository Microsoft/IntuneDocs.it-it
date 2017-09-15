---
title: Usare i criteri di configurazione delle app di Intune per Android for Work
titlesuffix: Azure portal
description: Informazioni su come usare i criteri di configurazione delle app per fornire i dati di configurazione a un'app Android for Work in esecuzione."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4b73202a1a68bd2dd3dcbfa86c21cb09ae00056c
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-use-microsoft-intune-app-configuration-policies-for-android-for-work"></a>Come usare i criteri di configurazione delle app di Microsoft Intune per Android for Work

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni che possono essere disponibili quando gli utenti eseguono un'app Android for Work. Non tutte le app supportano la configurazione delle app. Contattare lo sviluppatore dell'app per verificare se l'app è stata progettata o meno per supportare i criteri di configurazione delle app.

I criteri di configurazione delle app consentono di preconfigurare le impostazioni delle app disponibili per gli utenti prima dell'esecuzione dell'app. Alcune app Android supportano opzioni per le configurazioni gestite che è possibile configurare nel portale di Azure con [Progettazione configurazione](#use-configuration-designer). Alcune impostazioni di configurazione per le app (ad esempio, quelle con tipi Bundle) non possono essere configurate con Progettazione configurazione.  Sarà necessario usare l'[editor JSON](#use-json-editor) per tali valori.   Le impostazioni vengono fornite automaticamente alle app durante l'installazione.

Questi criteri non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi assegnata. Le impostazioni dei criteri vengono usate quando l'app ne esegue la ricerca (in genere, alla prima esecuzione).

## <a name="use-configuration-designer"></a>Usare Progettazione configurazione

1. Nel portale di Azure scegliere **App per dispositivi mobili**. In **Gestisci** scegliere **Criteri di configurazione dell'app** e quindi fare clic su **Aggiungi**.
2. Impostare i dettagli seguenti:
    - **Nome**: il nome del profilo che verrà visualizzato nel portale di Azure
    - **Descrizione**: la descrizione del profilo che verrà visualizzata nel portale di Azure
    - **Piattaforma** - Selezionare **Android**
    - **Tipo di registrazione del dispositivo** -  È preselezionata l'opzione **Registrato in Intune**.
3. Selezionare **App associata** per scegliere l'app per cui definire i criteri di configurazione.  Selezionare dall'elenco di app Android for Work che sono state approvate e sincronizzate con Intune
4. Selezionare **Impostazioni di configurazione**.
5. Per **Formato delle impostazioni di configurazione** selezionare **Usa progettazione configurazione**.
6. Scegliere **Aggiungi**. Verrà visualizzato un elenco delle impostazioni di configurazione disponibili. L'elenco include:
    - **Chiavi di configurazione** - Nome dell'impostazione.
    - **Tipo di valore** - L'impostazione che può essere configurata, ad esempio **Booleano** o **Stringa**.
    - **Descrizione** - Una descrizione dell'impostazione di configurazione.
7. Selezionare le caselle di controllo relative alle impostazioni da configurare con questo profilo e quindi fare clic su **OK**.
8. Verrà visualizzato un elenco delle impostazioni selezionate con il **Valore di configurazione** disponibile. Specificare un valore per ogni impostazione e quindi fare clic su **OK**.

## <a name="use-json-editor"></a>Usare l'editor JSON

1. Nel portale di Azure scegliere **App per dispositivi mobili**. In **Gestisci** scegliere **Criteri di configurazione dell'app** e quindi fare clic su **Aggiungi**.
2. Impostare i dettagli seguenti:
    - **Nome**: il nome del profilo che verrà visualizzato nel portale di Azure
    - **Descrizione**: la descrizione del profilo che verrà visualizzata nel portale di Azure
    - **Piattaforma** - Selezionare **Android**
    - **Tipo di registrazione del dispositivo** -  È preselezionata l'opzione **Registrato in Intune**.
3. Selezionare **App associata** per scegliere l'app per cui definire i criteri di configurazione.  Selezionare dall'elenco di app Android for Work che sono state approvate e sincronizzate con Intune.
5. Selezionare **Impostazioni di configurazione**.
6. Per **Formato delle impostazioni di configurazione** selezionare **Enter JSON editor** (Immetti editor JSON).
7. Nell'editor è possibile definire i valori JSON per le impostazioni di configurazione. È possibile scegliere **Download JSON template** (Scarica modello JSON) per scaricare un file di esempio che è possibile configurare.
8. Al termine, scegliere **OK** e quindi fare clic su **Aggiungi**.

Il criterio verrà creato e visualizzato nel pannello dell'elenco dei criteri.



Quando l'app assegnata viene eseguita in un dispositivo, verrà eseguita con le impostazioni configurate nel criterio di configurazione delle app.

## <a name="preconfigure-permissions-grant-state-for-apps"></a>Preconfigurare lo stato di concessione delle autorizzazioni per le app

È anche possibile preconfigurare l'autorizzazione per le app per l'accesso alle funzionalità del dispositivo Android. Per impostazione predefinita, le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiedono agli utenti di accettare o rifiutare le autorizzazioni. Se ad esempio un'app usa il microfono del dispositivo, all'utente finale viene chiesto di concedere all'app l'autorizzazione per l'uso del microfono.

1. Nel portale di Azure scegliere **App per dispositivi mobili**. In **Gestisci** scegliere **Criteri di configurazione dell'app** e quindi fare clic su **Aggiungi**.
2. Impostare i dettagli seguenti:
    - **Nome**: il nome del profilo che verrà visualizzato nel portale di Azure
    - **Descrizione**: la descrizione del profilo che verrà visualizzata nel portale di Azure
    - **Piattaforma** - Selezionare **Android**
    - **Tipo di registrazione del dispositivo** -  È preselezionata l'opzione **Registrato in Intune**.
3. Selezionare **App associata** per scegliere l'app per cui definire i criteri di configurazione.  Selezionare dall'elenco di app Android for Work che sono state approvate e sincronizzate con Intune.
5. Selezionare **Autorizzazioni** e quindi scegliere **Aggiungi**.
6. Selezionare dall'elenco delle autorizzazioni disponibili per le app e quindi scegliere **OK**.
7. Selezionare un'opzione per ogni autorizzazione da concedere con questi criteri:
    - **Messaggio di richiesta** - Chiedere all'utente di accettare o rifiutare.
    - **Concedi automaticamente** - Approvare automaticamente l'autorizzazione senza avvisare l'utente.
    - **Nega automaticamente** - Rifiutare automaticamente l'autorizzazione senza avvisare l'utente.
8. Per assegnare i criteri di configurazione delle app, selezionare i criteri di configurazione delle app, selezionare **Assegnazione** e quindi selezionare **Seleziona gruppi**.
9. Selezionare i gruppi di utenti da assegnare e quindi scegliere **Seleziona**.
10. Scegliere **Salva** per assegnare i criteri.

## <a name="next-steps"></a>Passaggi successivi

Procedere ad [assegnare](apps-deploy.md) e [monitorare](apps-monitor.md) normalmente l'app.

