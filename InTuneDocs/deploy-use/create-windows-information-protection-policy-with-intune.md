---
title: Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune | Microsoft Docs
description: Creare e distribuire criteri di protezione delle app WIP con Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 51e53e28-5c34-4d0f-a4b1-6390a337514c
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 8221f8ccc9aa07c67cd08b3ceb5f10d192cb6aa7
ms.lasthandoff: 04/27/2017


---

# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

A partire dalla versione 1704 di Intune, è possibile usare i criteri di protezione delle app con Windows 10 in scenari di gestione di applicazioni mobili (MAM) senza registrazione.

## <a name="before-you-begin"></a>Prima di iniziare

Di seguito vengono presentati prima di tutto alcuni concetti fondamentali per l'aggiunta di criteri WIP.

### <a name="list-of-allowed-and-exempt-apps"></a>Elenco delle app consentite ed escluse

-   **App consentite:** si tratta delle app che devono essere conformi al criterio.

-   **App escluse**: queste app sono escluse dal criterio e possono accedere ai dati aziendali senza restrizioni.

### <a name="types-of-apps"></a>Tipi di app

-   **App consigliate**: un elenco precompilato di app (principalmente Microsoft Office) che gli amministratori possono importare facilmente nei criteri.

-   **Store apps** (App dello Store): l'amministratore può aggiungere qualsiasi app da Windows Store al criterio.

-   **Windows desktop apps** (App desktop di Windows): l'amministratore può aggiungere qualsiasi app desktop di Windows tradizionale al criterio (ad esempio, exe, dll e così via).

## <a name="pre-requisites"></a>Prerequisiti

È necessario configurare il provider MAM prima di poter creare un criterio di protezione delle app WIP.

-   Altre informazioni su [come configurare il provider MAM con Intune](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-app-protection-policies-for-windows-10).

È inoltre necessario disporre di quanto segue:

-   Una licenza di [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium).
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP non supporta più identità e può essere presente una sola identità gestita alla volta.

## <a name="to-add-a-wip-policy"></a>Per aggiungere criteri WIP

Dopo aver configurato Intune nell'organizzazione, è possibile creare criteri specifici di WIP tramite il [portale Azure](https://docs.microsoft.com/intune/deploy-use/azure-portal-for-microsoft-intune-mam-policies).

1.  Passare al dashboard **Gestione di applicazioni mobili di Intune**, scegliere **Tutte le impostazioni** e quindi scegliere **Criteri per le app**.

2.  Nel pannello **Criteri per le app** scegliere **Aggiungi criteri** e quindi immettere i valori seguenti:

    a.  **Nome:** digitare un nome (obbligatorio) per il nuovo criterio.

    b.  **Descrizione:** digitare una descrizione facoltativa.

    c.  **Piattaforma:** scegliere **Windows 10** come piattaforma supportata per i criteri di protezione delle app.

    d.  **Stato della registrazione:** scegliere **Senza registrazione** come stato di registrazione per il criterio.

3.  Scegliere **Crea**. Il criterio viene creato e visualizzato nella tabella nel pannello **Criteri per le app**.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Per aggiungere app consigliate all'elenco App consentite

1.  Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **App consentite** nel pannello **Aggiungi criteri**. Verrà aperto il pannello **App consentite** che mostra tutte le app già incluse nell'elenco per i criteri di protezione delle app.

2.  Nel pannello **App consentite** scegliere **Aggiungi app**. Verrà aperto il pannello **Aggiungi app** che mostra tutte le app che fanno parte di questo elenco.

3.  Selezionare tutte le app a cui si vuole concedere l'accesso ai dati aziendali e quindi scegliere **OK**. Il pannello **App consentite** verrà aggiornato con tutte le app selezionate.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Aggiungere un'app dello Store all'elenco App consentite

**Per aggiungere un'app dello Store**

1.  Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **App consentite** nel menu visualizzato che mostra tutte le app già incluse nell'elenco per questo criterio di protezione delle app.

2.  Nel pannello **App consentite** scegliere **Aggiungi app**.

3.  Nel pannello **Aggiungi app** scegliere **App Store** nell'elenco a discesa. Il pannello cambia per visualizzare le caselle per l'aggiunta di un **editore** e un **nome** per l'app.

4.  Digitare il nome dell'app e del relativo editore, quindi scegliere **OK**.

    > [!TIP]
    > Ecco un esempio di app con **Editore** *CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US* e **Nome** prodotto *Microsoft.MicrosoftAppForWindows*.

5.  Dopo aver immesso le informazioni nei campi, scegliere **OK** per aggiungere l'app all'elenco **App consentite**.

> [!NOTE]
> Per aggiungere più app dello Store contemporaneamente, è possibile fare clic sul menu **(...)**  alla fine della riga dell'app e quindi continuare ad aggiungere altre app. Al termine dell'operazione scegliere **OK**.

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Aggiungere un'app desktop all'elenco App consentite

**Per aggiungere un'app desktop**

1.  Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **App consentite**. Verrà aperto il pannello **App consentite** che mostra tutte le app già incluse nell'elenco per i criteri di protezione delle app.

2.  Nel pannello **App consentite** scegliere **Aggiungi app**.

3.  Nel pannello **Aggiungi app** scegliere **App desktop** nell'elenco a discesa.

4.  Dopo aver immesso le informazioni nei campi, scegliere **OK** per aggiungere l'app all'elenco **App consentite**.

> [!NOTE]
> Per aggiungere più **app desktop** contemporaneamente, è possibile fare clic sul menu **(...)** alla fine della riga dell'app e quindi continuare ad aggiungere altre app. Al termine dell'operazione scegliere **OK**.

## <a name="windows-information-protection-wip-learning"></a>Apprendimento WIP (Windows Information Protection)

Dopo aver aggiunto le app che si vuole proteggere con WIP, è necessario applicare una modalità di protezione usando **Apprendimento WIP**.

### <a name="before-you-begin"></a>Prima di iniziare

Apprendimento WIP (Windows Information Protection) è un report che consente agli amministratori di monitorare le app sconosciute WIP. Con app sconosciute si intendono quelle non distribuite dal reparto IT dell'organizzazione. L'amministratore può esportare queste app dal report e quindi aggiungerle ai criteri WIP per evitare disservizi con effetti sulla produttività prima dell'applicazione di WIP in modalità "Nascondi sostituzioni".

È consigliabile iniziare con **Invisibile all'utente** o **Consenti sostituzioni** mentre si verifica con un piccolo gruppo di avere incluso le app appropriate nell'elenco delle app consentite. Quando si è pronti, è possibile passare al criterio di applicazione finale, ovvero **Nascondi sostituzioni**.

#### <a name="what-the-protection-modes-are"></a>Caratteristiche delle modalità di protezione

- **Nascondi sostituzioni:**
    - WIP rileva eventuali procedure di condivisione dei dati non appropriate e impedisce all'utente di completare l'azione.
    - Può trattarsi, ad esempio, della condivisione di informazioni tra app non protette dall'azienda e della condivisione di dati aziendali tra altri utenti e dispositivi all'esterno dell'organizzazione.
<br></br>

- **Consenti sostituzioni:**
    - WIP rileva eventuali procedure di condivisione dei dati non appropriate e avvisa gli utenti nel caso eseguano operazioni considerate potenzialmente non sicure.
    - Questa modalità consente tuttavia all'utente di ignorare il criterio e di condividere i dati, con registrazione dell'azione nel log di controllo.
<br></br>
- **Invisibile all'utente:**
    - WIP viene eseguito in modo invisibile all'utente e registra attività di condivisione dei dati non appropriate senza bloccare alcuna operazione che richiederebbe l'interazione con il dipendente in modalità Consenti sostituzioni.
    - Le azioni non consentite, ad esempio app che tentano l'accesso in modo non appropriato a una risorsa di rete o a dati protetti da WIP, vengono bloccate.
<br></br>
- **Disattivato (scelta non consigliata):**
    - WIP viene disattivato e non consente di proteggere oppure di controllare i dati.
    - Dopo la disattivazione di WIP, viene effettuato un tentativo di decrittografare gli eventuali file contrassegnati da WIP nei dischi collegati in locale. Tenere presente che le informazioni precedenti relative a decrittografia e criteri non vengono riapplicate automaticamente se si riattiva la protezione WIP.

### <a name="to-add-a-protection-mode"></a>Per aggiungere una modalità di protezione

1.  Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **Impostazioni obbligatorie** nel pannello **Aggiungi criteri**.

    ![Screenshot della modalità di protezione](../media/AppManagement/learning-mode-sc1.png)

1.  Scegliere **Salva**.

### <a name="to-use-wip-learning"></a>Per usare Apprendimento WIP

1. Passare al dashboard di Azure.

2. Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune**. Verrà aperto il **dashboard di Intune**. Scegliere **App per dispositivi mobili**.

4. Scegliere **Apprendimento WIP** nella sezione **Monitoraggio**. Verranno visualizzate le app sconosciute registrate da Apprendimento WIP.

> [!IMPORTANT]
> Quando le app sono visualizzate nel report di registrazione di Apprendimento WIP, sarà possibile aggiungerle ai criteri di protezione delle app.

## <a name="to-deploy-your-wip-app-protection-policy"></a>Per distribuire i criteri di protezione delle app WIP

> [!IMPORTANT]
> Questa procedura è valida per lo scenario WIP con gestione di applicazioni mobili (MAM) senza registrazione.

Dopo aver creato i criteri di protezione delle app WIP, è necessario distribuirli all'organizzazione tramite MAM.

1.  Nel pannello **Criteri per le app** scegliere il nuovo criterio di protezione per le app, scegliere **Gruppi di utenti** e quindi scegliere **Aggiungi un gruppo di utenti**.

    Nel pannello **Aggiungi un gruppo di utenti** verrà visualizzato un elenco dei gruppi di utenti composto da tutti i gruppi di sicurezza in Azure Active Directory.

1.  Scegliere il gruppo a cui si vuole applicare il criterio e quindi fare clic su **Seleziona** per distribuire il criterio.
