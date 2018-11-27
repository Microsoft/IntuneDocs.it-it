---
title: Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti
titlesuffix: Microsoft Intune
description: Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni quando gli utenti eseguono un'app del profilo di lavoro Android.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4b76625276a34c027ae8c74f1c6a3977c4a7e8bd
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179950"
---
# <a name="add-app-configuration-policies-for-managed-android-devices"></a>Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni per le app del profilo di lavoro Android. Lo sviluppatore dell'app deve esporre le impostazioni di configurazione dell'app gestita Android per specificare le impostazioni di configurazione per l'app. Assegnare i criteri di configurazione dell'app al gruppo di utenti al quale devono essere applicate le impostazioni.  Le impostazioni dei criteri vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

> [!Note]  
> Non tutte le app supportano la configurazione delle app. Contattare lo sviluppatore dell'app per verificare se l'app è stata compilata in modo da supportare i criteri di configurazione delle app.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Scegliere il carico di lavoro **App client**.
4. Scegliere **Criteri di configurazione dell'app** nel gruppo **Gestisci** e quindi scegliere **Aggiungi**.
5. Impostare i dettagli seguenti:
    - **Nome**: il nome del profilo che verrà visualizzato nel portale di Azure.
    - **Descrizione**: la descrizione del profilo che verrà visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**: scegliere **Dispositivi gestiti**.
6. Selezionare **Android** per **Piattaforma**.
7. Selezionare **App associata** per scegliere l'app per cui definire un criterio di configurazione dell'app. Selezionare dall'elenco di app del profilo di lavoro Android che sono state approvate e sincronizzate con Intune.
8. Selezionare **Autorizzazioni**. È possibile impostare le configurazioni usando quanto segue:
    - [Progettazione configurazione](#Use-the-configuration-designer)
    - [Editor JSON](#Enter-the-JSON-editor)
9. Scegliere **OK** e quindi **Aggiungi**.

## <a name="use-the-configuration-designer"></a>Usare la finestra di progettazione della configurazione

È possibile usare la progettazione configurazione per le app Android che supportano la configurazione. La configurazione verrà applicata ai dispositivi registrati in Intune. La progettazione consente di configurare i valori di configurazione specifici per le impostazioni esposte da un'app.

Selezionare **Aggiungi** per selezionare l'elenco delle impostazioni di configurazione che si vuole specificare per l'app.  
Per ogni chiave e valore nella configurazione, impostare:

  - **Tipo di valore**  
    Il tipo di dati del valore di configurazione. Per i tipi di valore di stringa, è possibile scegliere facoltativamente tra un profilo di certificato e una variabile come tipo di valore.
  - **Valore di configurazione**  
    Il valore per la configurazione. Se si seleziona una variabile o un certificato per il tipo di valore, è possibile scegliere da un elenco di variabili o i profili di certificato nell'elenco a discesa dei valori di configurazione.  Se si sceglie un certificato, l'alias del certificato del certificato distribuito nel dispositivo sarà popolato in fase di esecuzione.
    
### <a name="supported-variables-for-configuration-values"></a>Variabili supportate per i valori di configurazione

Se si sceglie una variabile come tipo di valore, è possibile scegliere le opzioni seguenti:
- Nome dell'entità utente, ad esempio **John@contoso.com**
- Posta elettronica, ad esempio **John@contoso.com**
- Nome dell'entità utente parziale, ad esempio **John**
- ID account, ad esempio **fc0dc142-71d8-4b12-bbea-bae2a8514c81**
- ID dispositivo, ad esempio **b9841cd9-9843-405f-be28-b2265c59ef97**
- ID utente, ad esempio **3ec2c00f-b125-4519-acf0-302ac3761822**
- Nome utente, ad esempio **John Doe**

### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Consentire solo gli account dell'organizzazione configurati nelle app con identità multiple 

Per i dispositivi Android, usare le coppie chiave/valore seguenti:

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Valori** | <ul><li>Uno o più UPN delimitati da <code>;</code>.</li><li>Solo gli account consentiti sono gli account utente gestiti definiti da questa chiave.</li><li> Per i dispositivi registrati in Intune, è possibile usare il token <code>{{userprincipalname}}</code> per rappresentare l'account utente registrato.</li></ul> |

   > [!NOTE]
   > È necessario usare Outlook per Android 2.2.222 o versioni successive quando si consentono solo gli account dell'organizzazione configurati con identità multiple.<p></p>
   > L'amministratore di Microsoft Intune può controllare gli account utente che vengono aggiunti alle applicazioni di Microsoft Office nei dispositivi gestiti. Può limitare l'accesso agli account utente consentiti dell'organizzazione e bloccare gli account personali nei dispositivi registrati. Le applicazioni di supporto elaborano la configurazione dell'app e rimuovono e bloccano gli account non approvati.<p></p>
   > Per Microsoft Word, Microsoft Excel, Microsoft PowerPoint è necessario usare la versione 16.0.9327.1000 e successive dell'app. 

## <a name="enter-the-json-editor"></a>Usare l'editor JSON

Alcune impostazioni di configurazione per le app (ad esempio, quelle con tipi Bundle) non possono essere configurate con Progettazione configurazione. Per questi valori è necessario usare l'editor JSON. Le impostazioni vengono fornite automaticamente alle app durante l'installazione.

1. Per **Formato delle impostazioni di configurazione** selezionare **Enter JSON editor** (Immetti editor JSON).
2. Nell'editor è possibile definire i valori JSON per le impostazioni di configurazione. È possibile scegliere **Download JSON template** (Scarica modello JSON) per scaricare un file di esempio che è possibile configurare.
3. Scegliere **OK** e quindi **Aggiungi**.

Il criterio viene creato e visualizzato nel pannello dell'elenco dei criteri.

Quando l'app assegnata viene eseguita in un dispositivo, viene eseguita con le impostazioni configurate nei criteri di configurazione dell'app.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Preconfigurare lo stato di concessione delle autorizzazioni per le app

È anche possibile preconfigurare l'autorizzazione per le app per l'accesso alle funzionalità del dispositivo Android. Per impostazione predefinita le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiedono agli utenti di accettare o rifiutare le autorizzazioni. Se ad esempio un'app usa il microfono del dispositivo, chiede all'utente l'autorizzazione per l'uso del microfono.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Scegliere **App client**.
3. In **Gestisci** scegliere **Criteri di configurazione dell'app** e quindi scegliere **Aggiungi**.
4. Impostare i dettagli seguenti:
    - **Nome**. Il nome del profilo che verrà visualizzato nel portale di Azure.
    - **Descrizione**. La descrizione del profilo che verrà visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**. Selezionare **Dispositivi gestiti**.
    - **Piattaforma**. Selezionare **Android**.
5. Selezionare **App associata** per scegliere l'app per cui definire i criteri di configurazione. Selezionare dall'elenco di app del profilo di lavoro Android che sono state approvate e sincronizzate con Intune.
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

