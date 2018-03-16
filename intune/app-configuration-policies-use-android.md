---
title: Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti
titlesuffix: Microsoft Intune
description: Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni quando gli utenti eseguono un'app Android for Work.
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a448c33e8324492c68d509a12d5901f41ed4873a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni quando gli utenti eseguono un'app Android for Work. Questi criteri non vengono assegnati direttamente agli utenti e ai dispositivi, ma vengono associati a un'app che viene poi assegnata. Le impostazioni dei criteri vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

> [!Note]  
> Non tutte le app supportano la configurazione delle app. Contattare lo sviluppatore dell'app per verificare se l'app è stata compilata in modo da supportare i criteri di configurazione delle app.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Scegliere il carico di lavoro delle **app per dispositivi mobili**.
4. Scegliere **Criteri di configurazione dell'app** nel gruppo **Gestisci** e quindi scegliere **Aggiungi**.
5. Impostare i dettagli seguenti:
    - **Nome**  
      Il nome del profilo che verrà visualizzato nel portale di Azure.
    - **Descrizione**  
      La descrizione del profilo che verrà visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**  
      Scegliere **Dispositivi gestiti**.
6. Selezionare **Android for Work** per **Piattaforma**.
7. Selezionare **App associata** per scegliere l'app per cui definire un criterio di configurazione dell'app. Selezionare dall'elenco di app Android for Work che sono state approvate e sincronizzate con Intune.
8. Selezionare **Impostazioni di configurazione**. È possibile impostare le configurazioni usando quanto segue:
    - [Progettazione configurazione](#Use-the-configuration-designer)
    - [Editor JSON](#Enter-the-JSON-editor)
9. Scegliere **OK** e quindi **Aggiungi**.

## <a name="use-the-configuration-designer"></a>Usare la finestra di progettazione della configurazione

È possibile usare la finestra di progettazione della configurazione per le app disponibili in dispositivi registrati o non registrati in Intune. La finestra di progettazione consente di configurare chiavi e valori di configurazione specifici. È anche necessario specificare il tipo di dati per ogni valore.

Per ogni chiave e valore nella configurazione, impostare:

  - **Chiave di configurazione**  
     Chiave che identifica in modo univoco la configurazione specifica delle impostazioni.
  - **Tipo di valore**  
    Il tipo di dati del valore di configurazione. I tipi includono Integer, Real, String o Boolean.
  - **Valore di configurazione**  
    Il valore per la configurazione. 

## <a name="enter-the-json-editor"></a>Usare l'editor JSON

Alcune impostazioni di configurazione per le app (ad esempio, quelle con tipi Bundle) non possono essere configurate con Progettazione configurazione. Per questi valori è necessario usare l'editor JSON. Le impostazioni vengono fornite automaticamente alle app durante l'installazione.

1. Per **Formato delle impostazioni di configurazione** selezionare **Enter JSON editor** (Immetti editor JSON).
2. Nell'editor è possibile definire i valori JSON per le impostazioni di configurazione. È possibile scegliere **Download JSON template** (Scarica modello JSON) per scaricare un file di esempio che è possibile configurare.
3. Scegliere **OK** e quindi **Aggiungi**.

Il criterio viene creato e visualizzato nel pannello dell'elenco dei criteri.

Quando l'app assegnata viene eseguita in un dispositivo, viene eseguita con le impostazioni configurate nei criteri di configurazione dell'app.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Preconfigurare lo stato di concessione delle autorizzazioni per le app

È anche possibile preconfigurare l'autorizzazione per le app per l'accesso alle funzionalità del dispositivo Android. Per impostazione predefinita le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiedono agli utenti di accettare o rifiutare le autorizzazioni. Se ad esempio un'app usa il microfono del dispositivo, chiede all'utente l'autorizzazione per l'uso del microfono.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Scegliere **App per dispositivi mobili**.
3. In **Gestisci** scegliere **Criteri di configurazione dell'app** e quindi scegliere **Aggiungi**.
4. Impostare i dettagli seguenti:
    - **Nome**. Il nome del profilo che verrà visualizzato nel portale di Azure.
    - **Descrizione**. La descrizione del profilo che verrà visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**. Selezionare **Dispositivi gestiti**.
    - **Piattaforma**. Selezionare **Android for Work**.
5. Selezionare **App associata** per scegliere l'app per cui definire i criteri di configurazione. Selezionare dall'elenco di app Android for Work che sono state approvate e sincronizzate con Intune.
6. Selezionare **Autorizzazioni** e quindi scegliere **Aggiungi**.
7. Selezionare dall'elenco delle autorizzazioni disponibili per le app e quindi scegliere **OK**.
8. Selezionare un'opzione per ogni autorizzazione da concedere con questi criteri:
    - **Messaggio di richiesta**. Chiedere all'utente di accettare o rifiutare
    - **Concedi automaticamente**. Approvare automaticamente l'autorizzazione senza avvisare l'utente.
    - **Nega automaticamente**. Rifiutare automaticamente l'autorizzazione senza avvisare l'utente.
9. Per assegnare i criteri di configurazione delle app, selezionare i criteri di configurazione delle app, selezionare **Assegnazione** e quindi selezionare **Seleziona gruppi**.
10. Selezionare i gruppi di utenti da assegnare e quindi scegliere **Seleziona**.
11. Scegliere **Salva** per assegnare i criteri.

## <a name="next-steps"></a>Passaggi successivi

Procedere con l'[assegnazione](apps-deploy.md) e il [monitoraggio](apps-monitor.md) dell'app.

