---
title: Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti
titleSuffix: Microsoft Intune
description: Usare i criteri di configurazione delle app in Microsoft Intune per specificare le impostazioni quando gli utenti eseguono un'app Google Play gestita.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/28/2020
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
ms.openlocfilehash: 7650230e419a639adfe02cd6c01f6170a4eb878b
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181843"
---
# <a name="add-app-configuration-policies-for-managed-android-enterprise-devices"></a>Aggiungere criteri di configurazione delle app per i dispositivi Android gestiti

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

I criteri di configurazione delle app in Microsoft Intune specificano le impostazioni nelle app Google Play gestite nei dispositivi Android Enterprise gestiti. Lo sviluppatore di app espone le impostazioni di configurazione delle app gestite da Android. Intune usa queste impostazioni esposte per consentire all'amministratore di configurare le funzionalità per l'app. I criteri di configurazione dell'app vengono assegnati ai gruppi di utenti. Le impostazioni dei criteri vengono usate quando l'app ne esegue la ricerca, in genere alla prima esecuzione.

> [!NOTE]  
> Non tutte le app supportano la configurazione delle app. Contattare lo sviluppatore dell'app per verificare se l'app supporta i criteri di configurazione.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Scegliere **App** > **Criteri di configurazione dell'app** > **Aggiungi** > **Dispositivi gestiti**. Si noti che è possibile scegliere tra **Dispositivi gestiti** e **App gestite**. Per altre informazioni, vedere [App che supportano la configurazione delle app](~/apps/app-configuration-policies-overview.md#apps-that-support-app-configuration).
3. Nella pagina **Informazioni di base** impostare i dettagli seguenti:
    - **Nome** - Nome del profilo che viene visualizzato nel portale di Azure.
    - **Descrizione** - Descrizione del profilo che viene visualizzata nel portale di Azure.
    - **Tipo di registrazione del dispositivo**: questo valore è impostato su **Dispositivi gestiti**.
4. In **Piattaforma** selezionare **Android Enterprise**.
5. Fare clic su **Selezionare l'app** accanto ad **App interessate**. Verrà visualizzato il riquadro **App associata**. 
6. Nel riquadro **App associata** scegliere l'app gestita da associare ai criteri di configurazione e fare clic su **OK**.
7. Fare clic su **Avanti** per visualizzare la pagina **Impostazioni**.
8. Fare clic su **Aggiungi** per visualizzare il riquadro **Aggiungi autorizzazioni**.
9. Fare clic sulle autorizzazioni che si vogliono sostituire. Le autorizzazioni concesse sostituiranno i criteri "Autorizzazioni delle app predefinite" per le app selezionate.
10. Impostare **Stato dell'autorizzazione** per ogni autorizzazione. È possibile scegliere tra **Chiedi conferma**, **Concedi automaticamente** o **Nega automaticamente**. Per altre informazioni sulle autorizzazioni, vedere [Impostazioni di Android Enterprise per contrassegnare un dispositivo come conforme o non conforme in Intune](~/protect/compliance-policy-create-android-for-work.md).
11. Nella casella a discesa selezionare **Formato delle impostazioni di configurazione**. Per aggiungere informazioni di configurazione, selezionare uno dei metodi seguenti:
    - **Usare la finestra di progettazione della configurazione**
    - **Immettere dati JSON**<br><br>
    Per informazioni dettagliate sull'uso della finestra di progettazione della configurazione, vedere [Usare Progettazione configurazione](#use-the-configuration-designer). Per informazioni dettagliate sull'immissione di dati XML, vedere [Immettere i dati JSON](#enter-json-data). 
12. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.
13. Nella casella a discesa accanto ad **Assegna a** selezionare **Gruppi selezionati**, **Tutti gli utenti**, **Tutti i dispositivi** o **Tutti gli utenti e tutti i dispositivi** per assegnare i criteri di configurazione dell'app.

    ![Screenshot della scheda Includi in Assegnazioni](./media/app-configuration-policies-use-ios/app-config-policy01.png)

14. Selezionare **Tutti gli utenti** nella casella a discesa.

    ![Screenshot delle assegnazioni dei criteri - opzione di elenco a discesa Tutti gli utenti](./media/app-configuration-policies-use-ios/app-config-policy02.png)

15. Fare clic su **Selezionare i gruppi da escludere** per visualizzare il riquadro correlato.

    ![Screenshot delle assegnazioni dei criteri - Riquadro Selezionare i gruppi da escludere](./media/app-configuration-policies-use-ios/app-config-policy03.png)

16. Scegliere i gruppi da escludere e quindi fare clic su **Seleziona**.

    >[!NOTE]
    >Quando si aggiunge un gruppo, se sono già stati inclusi altri gruppi per un tipo di assegnazione specifico, tale gruppo risulterà preselezionato e non potrà essere modificato per gli altri tipi di assegnazione di inclusione. Di conseguenza, tale gruppo non potrà essere usato come gruppo escluso.

17. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**.
18. Fare clic su **Crea** per aggiungere i criteri di configurazione dell'app a Intune.

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

## <a name="enter-json-data"></a>Immettere dati JSON

Alcune impostazioni di configurazione per le app (ad esempio, quelle con tipi Bundle) non possono essere configurate con la finestra di progettazione della configurazione. Per questi valori, usare l'editor JSON. Le impostazioni vengono fornite automaticamente alle app durante l'installazione.

1. Per **Formato delle impostazioni di configurazione** selezionare **Enter JSON editor** (Immetti editor JSON).
2. Nell'editor è possibile definire i valori JSON per le impostazioni di configurazione. È possibile scegliere **Download JSON template** (Scarica modello JSON) per scaricare un file di esempio che è possibile configurare.
3. Scegliere **OK** e quindi **Aggiungi**.

Il criterio viene creato e visualizzato nell'elenco.

Quando l'app assegnata viene eseguita in un dispositivo, viene eseguita con le impostazioni configurate nei criteri di configurazione dell'app.

## <a name="preconfigure-the-permissions-grant-state-for-apps"></a>Preconfigurare lo stato di concessione delle autorizzazioni per le app

È anche possibile preconfigurare le autorizzazioni per le app per l'accesso alle funzionalità del dispositivo Android. Per impostazione predefinita, le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiedono agli utenti di accettare o rifiutare le autorizzazioni.

Ad esempio, per un'app che usa il microfono del dispositivo, all'utente viene richiesto di concedere l'autorizzazione per l'uso del microfono.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **App** > **Criteri di configurazione dell'app** >  **Aggiungi** > **Dispositivi gestiti**.
2. Aggiungere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un nome di criterio valido è **Criterio app per richiesta autorizzazioni Android Enterprise per l'intera azienda**.
    - **Descrizione**. Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Tipo di registrazione del dispositivo**: Questo valore è impostato su **Dispositivi gestiti**.
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
- [Distribuzione delle impostazioni di configurazione delle app di Outlook per iOS/iPadOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)

## <a name="next-steps"></a>Passaggi successivi

Procedere con l'[assegnazione](apps-deploy.md) e il [monitoraggio](apps-monitor.md) dell'app.
