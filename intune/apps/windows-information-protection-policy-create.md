---
title: Criteri di protezione delle app Windows Information Protection (WIP)
titleSuffix: Microsoft Intune
description: Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Microsoft Intune
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4e3627bd-a9fd-49bc-b95e-9b7532f0ed55
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0c28deaccbfcc63c87b7cce8862675e704d5d1a2
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724347"
---
# <a name="create-and-deploy-windows-information-protection-wip-app-protection-policy-with-intune"></a>Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

È possibile usare i criteri di protezione delle app con app Windows 10 per proteggere le app senza registrare i dispositivi.

## <a name="before-you-begin"></a>Prima di iniziare

È necessario conoscere alcuni concetti fondamentali per l'aggiunta di criteri WIP:

### <a name="list-of-allowed-and-exempt-apps"></a>Elenco delle app consentite ed escluse

- **App protette:** app che devono essere conformi ai criteri.

- **App escluse:** app escluse dai criteri. Possono accedere ai dati aziendali senza restrizioni.

### <a name="types-of-apps"></a>Tipi di app

- **App consigliate:** elenco precompilato di app (principalmente Microsoft Office) che è possibile importare facilmente nei criteri.
- **App Store:** è possibile aggiungere qualsiasi app da Windows Store ai criteri.
- **Windows desktop apps** (App desktop di Windows): è possibile aggiungere qualsiasi app desktop di Windows tradizionale (ad esempio con estensione exe e dll) ai criteri

## <a name="prerequisites"></a>Prerequisiti

Configurare il provider MAM prima di creare un criterio di protezione dell'app di WIP. Altre informazioni su [come configurare il provider MAM con Intune](app-protection-policies-configure-windows-10.md).  

> [!IMPORTANT]
> WIP non supporta più identità e può essere presente una sola identità gestita alla volta.

È inoltre necessario avere la licenza e l'aggiornamento seguenti:

- Una licenza di [Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)
- [Windows Creators Update](https://blogs.windows.com/windowsexperience/2017/04/11/how-to-get-the-windows-10-creators-update/#o61bC2PdrHslHG5J.97)





## <a name="to-add-a-wip-app-protection-policy"></a>Per aggiungere criteri di protezione delle app WIP

Dopo aver configurato Intune nell'organizzazione, è possibile creare criteri specifici di WIP.

> [!TIP]  
> Per informazioni correlate sulla creazione di criteri WIP per Intune, incluse le impostazioni disponibili e come configurarle, vedere [Creare criteri di Windows Information Protection (WIP) con il software MAM usando il portale di Azure per Microsoft Intune](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-mam-intune-azure) nella raccolta di documenti sulla sicurezza di Windows. 


1. Accedere al [portale di Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**.
3. Selezionare **App client** nel pannello **Microsoft Intune**.
4. Selezionare **Criteri di protezione delle app** nel pannello **App client**.
5. Selezionare **Aggiungi criteri** per visualizzare il pannello **Aggiungi criteri**.
6. Aggiungere i valori seguenti:
    - **Nome:** digitare un nome (obbligatorio) per i nuovi criteri.
    - **Descrizione:** (facoltativo) digitare una descrizione.
    - **Piattaforma:** scegliere **Windows 10** come piattaforma supportata per i criteri di protezione delle app.
    - **Stato registrazione:** scegliere **Senza registrazione** come stato di registrazione per i criteri.
7. Scegliere **Crea**. I criteri vengono creati e visualizzati nella tabella nel pannello **Criteri di protezione delle app**.

## <a name="to-add-recommended-apps-to-your-protected-apps-list"></a>Per aggiungere app consigliate all'elenco delle app protette

1. Selezionare **App client** nel pannello **Microsoft Intune**.
2. Selezionare **Criteri di protezione delle app** nel pannello **App client**.
3. Nel pannello **Criteri di protezione delle app** scegliere i criteri che si vuole modificare. Viene visualizzato il pannello **Protezione app di Intune**.
4. Scegliere **App protette** nel pannello **Protezione app di Intune**. Verrà aperto il pannello **App protette** che mostra tutte le app già incluse nell'elenco per i criteri di protezione delle app.
5. Selezionare **Aggiungi app**. Le informazioni per **Aggiungi app** mostrano un elenco filtrato di app. L'elenco nella parte superiore del pannello consente di modificare il filtro dell'elenco.
6. Selezionare tutte le app a cui si vuole concedere l'accesso ai dati aziendali.
7. Fare clic su **OK**. Il pannello **App protette** viene aggiornato per visualizzare tutte le app selezionate.
8. Fare clic su **Save**.

## <a name="add-a-store-app-to-your-protected-apps-list"></a>Aggiungere un'app dello Store all'elenco delle app protette

**Per aggiungere un'app dello Store**
1. Selezionare **App client** nel pannello **Microsoft Intune**.
2. Selezionare **Criteri di protezione delle app** nel pannello **App client**.
3. Nel pannello **Criteri di protezione delle app** scegliere i criteri che si vuole modificare. Viene visualizzato il pannello **Protezione app di Intune**.
4. Scegliere **App protette** nel pannello **Protezione app di Intune**. Verrà aperto il pannello **App protette** che mostra tutte le app già incluse nell'elenco per i criteri di protezione delle app.
5. Selezionare **Aggiungi app**. Le informazioni per **Aggiungi app** mostrano un elenco filtrato di app. L'elenco nella parte superiore del pannello consente di modificare il filtro dell'elenco.
6. Nell'elenco selezionare **App Store**.
7. Immettere i valori per **Nome**, **Editore**, **Nome prodotto** e **Azione**. Assicurarsi di impostare il valore di **Azione** su **Consenti**, in modo che l'app possa accedere ai dati aziendali.
9. Fare clic su **OK**. Il pannello **App protette** viene aggiornato per visualizzare tutte le app selezionate.
10. Fare clic su **Save**.

## <a name="add-a-desktop-app-to-your-protected-apps-list"></a>Aggiungere un'app desktop all'elenco delle app protette

**Per aggiungere un'app desktop**
1. Selezionare **App client** nel pannello **Microsoft Intune**.
2. Selezionare **Criteri di protezione delle app** nel pannello **App client**.
3. Nel pannello **Criteri di protezione delle app** scegliere i criteri che si vuole modificare. Viene visualizzato il pannello **Protezione app di Intune**.
4. Scegliere **App protette** nel pannello **Protezione app di Intune**. Verrà aperto il pannello **App protette** che mostra tutte le app già incluse nell'elenco per i criteri di protezione delle app.
5. Selezionare **Aggiungi app**. Le informazioni per **Aggiungi app** mostrano un elenco filtrato di app. L'elenco nella parte superiore del pannello consente di modificare il filtro dell'elenco.
6. Nell'elenco selezionare **App desktop**.
7. Immettere i valori per **Nome**, **Editore**, **Nome prodotto**, **File**, **Versione minima**, **Versione massima** e **Azione**. Assicurarsi di impostare il valore di **Azione** su **Consenti**, in modo che l'app possa accedere ai dati aziendali.
9. Fare clic su **OK**. Il pannello **App protette** viene aggiornato per visualizzare tutte le app selezionate.
10. Fare clic su **Save**.

## <a name="wip-learning"></a>Apprendimento WIP
Dopo aver aggiunto le app che si vuole proteggere con WIP, è necessario applicare una modalità di protezione usando **Apprendimento WIP**.

### <a name="before-you-begin"></a>Prima di iniziare

Apprendimento WIP è un report che consente di monitorare le app abilitate per WIP e le app sconosciute WIP. Con app sconosciute si intendono quelle non distribuite dal reparto IT dell'organizzazione. È possibile esportare queste app dal report e quindi aggiungerle ai criteri WIP per evitare disservizi con effetti sulla produttività prima dell'applicazione di WIP in modalità "Blocca".

<!-- 1631908 -->
Oltre a visualizzare informazioni sulle app abilitate per WIP, è possibile visualizzare un riepilogo dei dispositivi che hanno condiviso dati di lavoro con siti Web. Con queste informazioni, è possibile determinare quali siti Web devono essere aggiunti ai criteri WIP per gruppi e utenti. Il riepilogo mostra gli URL di siti Web a cui hanno accesso le app abilitate per WIP.

Quando si usano app abilitate per WIP e app sconosciute WIP, è consigliabile iniziare con **Invisibile all'utente** o **Consenti sostituzioni** e verificare con un piccolo gruppo di avere incluso le app appropriate nell'elenco delle app protette. Quando si è pronti, è possibile passare al criterio di applicazione finale, ovvero **Blocca**.

### <a name="what-are-the-protection-modes"></a>Caratteristiche delle modalità di protezione

#### <a name="block"></a>Blocca
WIP rileva eventuali procedure di condivisione dei dati non appropriate e impedisce all'utente di completare l'azione. Le azioni bloccate possono includere la condivisione di informazioni tra app non protette dall'azienda e la condivisione di dati aziendali tra altri utenti e dispositivi all'esterno dell'organizzazione.

#### <a name="allow-overrides"></a>Consenti sostituzioni
WIP rileva eventuali procedure di condivisione dei dati non appropriate e avvisa gli utenti quando eseguono operazioni considerate potenzialmente non sicure. Questa modalità consente tuttavia all'utente di ignorare il criterio e di condividere i dati, con registrazione dell'azione nel log di controllo.

#### <a name="silent"></a>Invisibile all'utente
WIP viene eseguito in modo invisibile all'utente e registra attività di condivisione dei dati non appropriate senza bloccare alcuna operazione che richiederebbe l'interazione con il dipendente in modalità Consenti sostituzioni. Le azioni non consentite, ad esempio app che tentano l'accesso in modo non appropriato a una risorsa di rete o a dati protetti da WIP, vengono bloccate.

#### <a name="off-not-recommended"></a>Disattivato (scelta non consigliata)
WIP viene disattivato e non consente di proteggere oppure di controllare i dati.

Dopo la disattivazione di WIP, viene effettuato un tentativo di decrittografare gli eventuali file contrassegnati da WIP nei dischi collegati in locale. Si noti che le informazioni precedenti relative a decrittografia e criteri non vengono riapplicate automaticamente se si riattiva la protezione WIP.

### <a name="add-a-protection-mode"></a>Aggiungere una modalità di protezione

1. Nel pannello **Criteri per le app** scegliere il nome del criterio e quindi scegliere **Impostazioni obbligatorie**.

    ![Screenshot del riquadro della modalità di apprendimento](./media/windows-information-protection-policy-create/learning-mode-sc1.png)

1. Selezionare un'impostazione e quindi scegliere **Salva**.

### <a name="use-wip-learning"></a>Usare Apprendimento WIP

1. Aprire il [portale di Azure](https://portal.azure.com). Scegliere **Tutti i servizi**. Digitare **Intune** nel filtro della casella di testo.

3. Scegliere **Intune** > **App client**.

4. Scegliere **Stato di protezione dell'App** > **Report** > **Apprendimento Windows Information Protection**.  

    Quando le app sono visualizzate nel report di registrazione di Apprendimento WIP, sarà possibile aggiungerle ai criteri di protezione delle app.

## <a name="allow-windows-search-indexer-to-search-encrypted-items"></a>Consentire all'indicizzatore di Ricerca di Windows di cercare elementi crittografati
Consente o impedisce l'indicizzazione di elementi. Questa opzione è per l'indicizzatore di Ricerca di Windows, che stabilisce se deve essere eseguita l'indicizzazione degli elementi che vengono crittografati, ad esempio i file protetti di Windows Information Protection (WIP).

Questa opzione dei criteri di protezione dell'app si trova nelle **impostazioni avanzate** dei criteri di Windows Information Protection. I criteri di protezione dell'app devono essere impostati sulla piattaforma *Windows 10* e lo **stato di registrazione** dei criteri dell'app deve essere impostato su **Con registrazione**.

Quando i criteri sono abilitati, gli elementi protetti da WIP vengono indicizzati e i relativi metadati vengono archiviati in un percorso non crittografato. I metadati includono elementi come percorso del file e data di modifica.

Quando i criteri sono disabilitati, gli elementi protetti da WIP non vengono indicizzati e non appaiono nei risultati di Cortana o Esplora file. Si può inoltre avere un impatto sulle prestazioni delle app Foto e Groove se nel dispositivo sono presenti molti file multimediali protetti con WIP.

## <a name="add-encrypted-file-extensions"></a>Aggiungere estensioni di file crittografati

Oltre a impostare l'opzione che **consente all'indicizzatore di ricerca di Windows di cercare gli elementi crittografati**, è possibile specificare un elenco di estensioni di file. I file con queste estensioni vengono crittografati durante la copia da una condivisione di Server Message Block (SMB) all'interno dell'azienda, come definito nell'elenco dei percorsi di rete. Quando questo criterio non viene specificato, viene applicato il comportamento di crittografia automatica esistente. Quando il criterio è configurato, vengono crittografati solo i file con le estensioni indicate nell'elenco.

## <a name="deploy-your-wip-app-protection-policy"></a>Distribuire i criteri di protezione delle app WIP

> [!IMPORTANT]
> Queste informazioni si applicano a WIP senza registrazione del dispositivo.

<!---not sure why you need the Important note. Isn't this what the topic is about? app protection w/o enrollment?--->

Dopo aver creato i criteri di protezione delle app WIP, è necessario distribuirli all'organizzazione tramite MAM.

1. Nel pannello **Criteri per le app** scegliere il nuovo criterio di protezione per le app, scegliere**Gruppi utenti** > **Aggiungi gruppo utenti**.

    Nel pannello **Aggiungi un gruppo di utenti** verrà visualizzato un elenco dei gruppi di utenti composto da tutti i gruppi di sicurezza in Azure Active Directory.

2. Scegliere il gruppo a cui si vuole applicare il criterio e quindi scegliere **Seleziona** per distribuire il criterio.

## <a name="next-steps"></a>Passaggi successivi

Per maggiori dettagli su Windows Information Protection, vedere [Proteggere i dati aziendali con Windows Information Protection (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip).
