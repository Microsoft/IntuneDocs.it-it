---
title: Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti
titleSuffix: Microsoft Intune
description: Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni quando gli utenti eseguono un'app Google Play gestita.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d0b6f3fe-2bd4-4518-a6fe-b9fd115ed5e0
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9561c50e21a9667ccec3f9de3627e7a933cf0736
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72584987"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I criteri di configurazione delle app in Microsoft Intune specificano le impostazioni nelle app Google Play gestite nei dispositivi Android Enterprise gestiti. Lo sviluppatore di app espone le impostazioni di configurazione delle app gestite da Android. Intune usa queste impostazioni esposte per consentire all'amministratore di configurare le funzionalità per l'app. I criteri di configurazione dell'app vengono assegnati ai gruppi di utenti. Le impostazioni dei criteri vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

> [!NOTE]  
> Non tutte le app supportano la configurazione delle app. Contattare lo sviluppatore dell'app per verificare se l'app supporta i criteri di configurazione.

1. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) selezionare **App client** > **Criteri di configurazione dell'app** >  **Aggiungi**.
2. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di criterio valido è **Criterio app Nine Work Android Enterprise per l'intera azienda**.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Tipo di registrazione del dispositivo**: Selezionare **Dispositivi gestiti**.
    - **Piattaforma**: Selezionare **Android**.

3. Selezionare **App associata**. Scegliere l'app per cui si vogliono definire i criteri di configurazione dell'app. Selezionare dall'elenco di app Google Play gestite che sono state approvate e sincronizzate con Intune.
4. Selezionare **Autorizzazioni**. È possibile impostare le configurazioni usando quanto segue:

    - [Progettazione configurazione](#use-the-configuration-designer)
    - [Editor JSON](#enter-the-json-editor)

5. Selezionare **OK** > **Aggiungi**.

## <a name="use-the-configuration-designer"></a>Usare la finestra di progettazione della configurazione

È possibile usare la finestra di progettazione della configurazione per le app Google Play gestite che sono state progettate per supportare le impostazioni di configurazione. La configurazione si applica ai dispositivi registrati in Intune. La finestra di progettazione consente di configurare i valori di configurazione specifici per le impostazioni esposte dall'app.

1. Selezionare **Aggiungi**. Scegliere l'elenco delle impostazioni di configurazione che si vuole specificare per l'app.

    Se si usa Gmail o Nine Work per l'app di posta elettronica, vedere [Impostazioni dei dispositivi Android Enterprise per configurare la posta elettronica](../email-settings-android-enterprise.md) per altre informazioni su queste impostazioni.

2. Per ogni chiave e valore nella configurazione, impostare:

    - **Tipo di valore**: Il tipo di dati del valore di configurazione. Per i tipi di valore di stringa, è possibile scegliere facoltativamente tra un profilo di certificato e una variabile come tipo di valore.
    - **Valore di configurazione**: Il valore per la configurazione. Se si seleziona una variabile o un certificato per **Tipo di valore**, scegliere da un elenco di variabili o profili di certificato. Se si sceglie un certificato, l'alias del certificato distribuito nel dispositivo viene popolato in fase di esecuzione.

### <a name="supported-variables-for-configuration-values"></a>Variabili supportate per i valori di configurazione

Se si sceglie una variabile come tipo di valore, è possibile scegliere le opzioni seguenti:

| Opzione | Esempio |
|----|----|
| ID dispositivo AAD | dc0dc142-11d8-4b12-bfea-cae2a8514c82 |
| ID account | fc0dc142-71d8-4b12-bbea-bae2a8514c81 |
| ID dispositivo di Intune | b9841cd9-9843-405f-be28-b2265c59ef97 |
| Dominio | contoso.com |
| Mail | john@contoso.com |
| Nome entità utente parziale | john |
| ID utente | 3ec2c00f-b125-4519-acf0-302ac3761822 |
| Nome utente | John Doe |
| Nome entità utente | john@contoso.com |


### <a name="allow-only-configured-organization-accounts-in-multi-identity-apps"></a>Consentire solo gli account dell'organizzazione configurati nelle app con identità multiple 

Per i dispositivi Android, usare le coppie chiave/valore seguenti:

| **Key** | com.microsoft.intune.mam.AllowedAccountUPNs |
|---|---|
| **Valori** | <ul><li>Uno o più UPN delimitati da <code>;</code>.</li><li>Solo gli account consentiti sono gli account utente gestiti definiti da questa chiave.</li><li> Per i dispositivi registrati in Intune, è possibile usare il token <code>{{userprincipalname}}</code> per rappresentare l'account utente registrato.</li></ul> |

   > [!NOTE]
   > Se si consentono solo account dell'organizzazione configurati con identità multiple, è necessario usare Outlook per Android 2.2.222 o versione successiva, Word, Excel, PowerPoint per Android 16.0.9327.1000 o versione successiva o OneDrive per Android 5.28 o versione successiva.<p></p>
   > L'amministratore di Microsoft Intune può controllare gli account utente che vengono aggiunti alle applicazioni di Microsoft Office nei dispositivi gestiti. Può limitare l'accesso agli account utente consentiti dell'organizzazione e bloccare gli account personali nei dispositivi registrati. Le applicazioni di supporto elaborano la configurazione dell'app e rimuovono e bloccano gli account non approvati.<p></p>

## <a name="enter-the-json-editor"></a>Usare l'editor JSON

Alcune impostazioni di configurazione per le app (ad esempio, quelle con tipi Bundle) non possono essere configurate con la finestra di progettazione della configurazione. Per questi valori, usare l'editor JSON. Le impostazioni vengono fornite automaticamente alle app durante l'installazione.

1. Per **Formato delle impostazioni di configurazione** selezionare **Enter JSON editor** (Immetti editor JSON).
2. Nell'editor è possibile definire i valori JSON per le impostazioni di configurazione. È possibile scegliere **Download JSON template** (Scarica modello JSON) per scaricare un file di esempio che è possibile configurare.
3. Scegliere **OK** e quindi **Aggiungi**.

Il criterio viene creato e visualizzato nell'elenco.

Quando l'app assegnata viene eseguita in un dispositivo, viene eseguita con le impostazioni configurate nei criteri di configurazione dell'app.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Preconfigurare lo stato di concessione delle autorizzazioni per le app

È anche possibile preconfigurare le autorizzazioni per le app per l'accesso alle funzionalità del dispositivo Android. Per impostazione predefinita, le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiedono agli utenti di accettare o rifiutare le autorizzazioni.

Ad esempio, per un'app che usa il microfono del dispositivo, all'utente viene richiesto di concedere l'autorizzazione per l'uso del microfono.

1. In [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) selezionare **App client** > **Criteri di configurazione dell'app** >  **Aggiungi**.
2. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di criterio valido è **Criterio app per richiesta autorizzazioni Android Enterprise per l'intera azienda**.
    - **Descrizione**. Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Tipo di registrazione del dispositivo**: Selezionare **Dispositivi gestiti**.
    - **Piattaforma**: Selezionare **Android**.

3. Selezionare **App associata**. Scegliere l'app per cui si vogliono definire i criteri di configurazione. Selezionare dall'elenco di app con profilo di lavoro Android che sono state approvate e sincronizzate con Intune.
4. Selezionare **Autorizzazioni** > **Aggiungi**. Nell'elenco selezionare le autorizzazioni dell'app disponibili > **OK**.
5. Selezionare un'opzione per ogni autorizzazione da concedere con questi criteri:
    - **Messaggio di richiesta**. Chiedere all'utente di accettare o rifiutare
    - **Concedi automaticamente**. Approvare automaticamente l'autorizzazione senza avvisare l'utente.
    - **Nega automaticamente**. Rifiutare automaticamente l'autorizzazione senza avvisare l'utente.
6. Per assegnare i criteri di configurazione delle app, selezionare i criteri > **Assegnazione** > **Seleziona gruppi**. Scegliere i gruppi di utenti per l'assegnazione > **Seleziona**.
7. Scegliere **Salva** per assegnare i criteri.

## <a name="additional-information"></a>Informazioni aggiuntive

- [Assegnazione di un'app Google Play gestita a dispositivi Android Enterprise](apps-add-android-for-work.md#assigning-a-managed-google-play-app-to-android-enterprise-work-profile-devices)
- [Distribuzione delle impostazioni di configurazione delle app di Outlook per iOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Passaggi successivi

Procedere con l'[assegnazione](apps-deploy.md) e il [monitoraggio](apps-monitor.md) dell'app.
