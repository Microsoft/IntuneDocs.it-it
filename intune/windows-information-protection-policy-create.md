---
title: Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune
titlesuffix: Azure portal
description: Creare e distribuire criteri di protezione delle app WIP con Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3cf11c53a5f1ce78dda9c703da32270b0b07874a
ms.sourcegitcommit: 001577b700f634da2fec0b44af2a378150d1f7ac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2017
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

A partire dalla versione 1704 di Intune, è possibile usare i criteri di protezione delle app con Windows 10 per proteggere le app senza registrare i dispositivi.

## <a name="before-you-begin"></a>Prima di iniziare

Di seguito vengono presentati prima di tutto alcuni concetti fondamentali per l'aggiunta di criteri WIP.

### <a name="list-of-allowed-and-exempt-apps"></a>Elenco delle app consentite ed escluse

-   **App consentite:** si tratta delle app che devono essere conformi al criterio.

-   **App escluse**: queste app sono escluse dal criterio e possono accedere ai dati aziendali senza restrizioni.

### <a name="types-of-apps"></a>Tipi di app

-   **App consigliate**: un elenco precompilato di app (principalmente Microsoft Office) che è possibile importare facilmente nei criteri. <!---I really don't know what you mean by "easily import into policy"--->

-   **App Store**: è possibile aggiungere qualsiasi app da Windows Store al criterio.

-   **Windows desktop apps** (App desktop di Windows): è possibile aggiungere qualsiasi app desktop di Windows tradizionale al criterio (ad esempio, exe e dll)

## <a name="pre-requisites"></a>Prerequisiti

Configurare il provider MAM prima di creare un criterio di protezione dell'app di WIP. Altre informazioni su [come configurare il provider MAM con Intune](https://docs.microsoft.com/app-protection-policies-configure-windows-10.md).

È inoltre necessario disporre di quanto segue:

-   Una licenza di [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium).
-   [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)

> [!IMPORTANT]
> WIP non supporta più identità e può essere presente una sola identità gestita alla volta.
<!---Should you be linking to a topic that explains what multi-identity is?--->

## <a name="to-add-a-wip-policy"></a>Per aggiungere criteri WIP

Dopo aver configurato Intune nell'organizzazione, è possibile creare criteri specifici di WIP tramite il [portale Azure](https://docs.microsoft.com/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies). <!---Is there an azure topic you can use instead of a classic? if not, should this topic be moved into the azure docset?--->

1.  Passare al dashboard **Gestione di applicazioni mobili di Intune**, scegliere **Tutte le impostazioni** > **Criteri per le app**.

2.  Nel pannello **Criteri per le app** scegliere **Aggiungi criteri** e quindi immettere i valori seguenti:

    a.  **Nome:** digitare un nome (obbligatorio) per il nuovo criterio.

    b.  **Descrizione:** digitare una descrizione facoltativa.

    c.  **Piattaforma:** scegliere **Windows 10** come piattaforma supportata per i criteri di protezione delle app.

    d.  **Stato della registrazione:** scegliere **Senza registrazione** come stato di registrazione per il criterio.

3.  Scegliere **Crea**. Il criterio viene creato e visualizzato nella tabella nel pannello **Criteri per le app**.

## <a name="to-add-recommended-apps-to-your-allowed-apps-list"></a>Per aggiungere app consigliate all'elenco delle app consentite

1.  Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **App consentite** nel pannello **Aggiungi criteri**. Verrà aperto il pannello **App consentite** che mostra tutte le app già incluse nell'elenco per i criteri di protezione delle app.

2.  Nel pannello **App consentite** scegliere **Aggiungi app**. Verrà aperto il pannello **Aggiungi app** che mostra tutte le app che fanno parte di questo elenco.

3.  Selezionare tutte le app a cui si vuole concedere l'accesso ai dati aziendali e quindi scegliere **OK**. Il pannello **App consentite** verrà aggiornato con tutte le app selezionate.

## <a name="add-a-store-app-to-your-allowed-apps-list"></a>Aggiungere un'app dello Store all'elenco delle app consentite

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

## <a name="add-a-desktop-app-to-your-allowed-apps-list"></a>Aggiungere un'app desktop all'elenco delle app consentite

**Per aggiungere un'app desktop**

1.  Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **App consentite**. Verrà aperto il pannello **App consentite** che mostra tutte le app già incluse nell'elenco per i criteri di protezione delle app.

2.  Nel pannello **App consentite** scegliere **Aggiungi app**.

3.  Nel pannello **Aggiungi app** scegliere **App desktop** nell'elenco a discesa.

4.  Dopo aver immesso le informazioni nei campi, scegliere **OK** per aggiungere l'app all'elenco **App consentite**.

> [!NOTE]
> Per aggiungere più **app desktop** contemporaneamente, è possibile fare clic sul menu **(...)** alla fine della riga dell'app e quindi continuare ad aggiungere altre app. Al termine dell'operazione scegliere **OK**.

## <a name="wip-learning"></a>Apprendimento WIP
<!---You've already defined WIP earlier in the topic. You don't need to keep doing so. --->
Dopo aver aggiunto le app che si vuole proteggere con WIP, è necessario applicare una modalità di protezione usando **Apprendimento WIP**.

### <a name="before-you-begin"></a>Prima di iniziare

Apprendimento WIP è un report che consente di monitorare le app sconosciute WIP. Con app sconosciute si intendono quelle non distribuite dal reparto IT dell'organizzazione. È possibile esportare queste app dal report e quindi aggiungerle ai criteri WIP per evitare disservizi con effetti sulla produttività prima dell'applicazione di WIP in modalità "Nascondi sostituzioni".

È consigliabile iniziare con **Invisibile all'utente** o **Consenti sostituzioni** mentre si verifica con un piccolo gruppo di avere incluso le app appropriate nell'elenco delle app consentite. Quando si è pronti, è possibile passare al criterio di applicazione finale, ovvero **Nascondi sostituzioni**.

### <a name="what-are-the-protection-modes"></a>Caratteristiche delle modalità di protezione

#### <a name="hide-overrides"></a>Nascondi sostituzioni
WIP rileva eventuali procedure di condivisione dei dati non appropriate e impedisce all'utente di completare l'azione. Può trattarsi, ad esempio, della condivisione di informazioni tra app non protette dall'azienda e della condivisione di dati aziendali tra altri utenti e dispositivi all'esterno dell'organizzazione.

#### <a name="allow-overrides"></a>Consenti sostituzioni
WIP rileva eventuali procedure di condivisione dei dati non appropriate e avvisa gli utenti nel caso eseguano operazioni considerate potenzialmente non sicure. Questa modalità consente tuttavia all'utente di ignorare il criterio e di condividere i dati, con registrazione dell'azione nel log di controllo.

#### <a name="silent"></a>Invisibile all'utente
WIP viene eseguito in modo invisibile all'utente e registra attività di condivisione dei dati non appropriate senza bloccare alcuna operazione che richiederebbe l'interazione con il dipendente in modalità Consenti sostituzioni. Le azioni non consentite, ad esempio app che tentano l'accesso in modo non appropriato a una risorsa di rete o a dati protetti da WIP, vengono bloccate.

#### <a name="off-not-recommended"></a>Disattivato (scelta non consigliata)
WIP viene disattivato e non consente di proteggere oppure di controllare i dati.

Dopo la disattivazione di WIP, viene effettuato un tentativo di decrittografare gli eventuali file contrassegnati da WIP nei dischi collegati in locale. Tenere presente che le informazioni precedenti relative a decrittografia e criteri non vengono riapplicate automaticamente se si riattiva la protezione WIP.

### <a name="add-a-protection-mode"></a>Aggiungere una modalità di protezione

1.  Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **Impostazioni obbligatorie**.

    ![Screenshot della modalità di protezione](./media/learning-mode-sc1.png)

1.  Scegliere **Salva**.

### <a name="use-wip-learning"></a>Usare Apprendimento WIP

1. Aprire il portale di Azure. Scegliere **Altri servizi**. Digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune** > **App per dispositivi mobili**.

4. Scegliere **Stato di protezione dell'App** > **Report** > **Apprendimento Windows Information Protection**.  
 
    Quando le app sono visualizzate nel report di registrazione di Apprendimento WIP, sarà possibile aggiungerle ai criteri di protezione delle app.

## <a name="deploy-your-wip-app-protection-policy"></a>Distribuire i criteri di protezione delle app WIP

> [!IMPORTANT]
> Queste informazioni si applicano a WIP senza registrazione del dispositivo.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

Dopo aver creato i criteri di protezione delle app WIP, è necessario distribuirli all'organizzazione tramite MAM.

1.  Nel pannello **Criteri per le app** scegliere il nuovo criterio di protezione per le app, scegliere**Gruppi utenti** > **Aggiungi gruppo utenti**.

    Nel pannello **Aggiungi un gruppo di utenti** verrà visualizzato un elenco dei gruppi di utenti composto da tutti i gruppi di sicurezza in Azure Active Directory.

1.  Scegliere il gruppo a cui si vuole applicare il criterio e quindi scegliere **Seleziona** per distribuire il criterio.
