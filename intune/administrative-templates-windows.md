---
title: Usare i modelli per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Usare i modelli amministrativi di Microsoft Intune per creare gruppi di impostazioni per dispositivi Windows 10. Usare queste impostazioni in un profilo di configurazione del dispositivo per controllare le applicazioni di Office, proteggere le funzionalità di Internet Explorer, controllare l'accesso a OneDrive, usare le funzionalità di desktop remoto, abilitare la riproduzione automatica, impostare le opzioni di risparmio energia, usare la stampa HTTP, usare opzioni di accesso diverse e controllare le dimensioni del registro eventi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0bfad3feed6daef1930c235bec9c25e809da46c5
ms.sourcegitcommit: ce9cae824a79223eab3c291fd5d5e377efac84cb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "67842767"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Usare i modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune

Una soluzione pratica per gestire i dispositivi di un'organizzazione è creare un gruppo di impostazioni da applicare a gruppi di dispositivi diversi. Supponiamo ad esempio di avere vari gruppi di dispositivi. A GruppoA si vuole assegnare un set di impostazioni specifico. A GruppoB si vuole assegnare un set di impostazioni diverso. Si vuole anche disporre di una visualizzazione semplice delle impostazioni che è possibile configurare.

Per completare questa attività, è possibile usare **Modelli amministrativi** in Microsoft Intune. I modelli amministrativi includono centinaia di impostazioni che controllano le funzionalità per Internet Explorer, le applicazioni Microsoft Office, desktop remoto, OneDrive, password e PIN e altro ancora. Queste impostazioni consentono agli amministratori di gruppi di gestire i Criteri di gruppo tramite il cloud.

Le impostazioni di Windows sono simili alle impostazioni di Criteri di gruppo (GPO) in Active Directory (AD). Queste impostazioni sono incluse in Windows e sono [impostazioni supportate da ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) (il collegamento apre un altro sito Microsoft) che usano XML. Le impostazioni di Office sono inserite con ADMX e usano le impostazioni ADMX nei [file dei modelli amministrativi di Office](https://www.microsoft.com/download/details.aspx?id=49030). Tuttavia, i modelli di Intune sono completamente basati sul cloud. Offrono un modo semplice e immediato di configurare le impostazioni e trovare quelle che interessano.

La funzionalità **Modelli amministrativi** è incorporata in Intune e non richiede alcuna personalizzazione, incluso l'uso di OMA-URI. Usare queste impostazioni dei modelli nella propria soluzione di gestione di dispositivi mobili (MDM) per gestire i dispositivi Windows 10 da una posizione centralizzata.

Questo articolo illustra i passaggi da eseguire per creare un modello per dispositivi Windows 10 e mostra come filtrare tutte le impostazioni disponibili in Intune. Con la creazione del modello viene creato un profilo di configurazione del dispositivo. È quindi possibile assegnare o distribuire questo profilo ai dispositivi Windows 10 dell'organizzazione.

## <a name="before-you-begin"></a>Prima di iniziare

- Alcune di queste impostazioni sono disponibili a partire da Windows 10 versione 1703 (RS2). Per un'esperienza ottimale, è consigliabile usare Windows 10 Enterprise versione 1903 (19H1) e versioni successive.

- Le impostazioni di Windows usano [i provider di servizi di configurazione (CSP) dei criteri di Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) (il collegamento apre un altro sito Microsoft). I provider CSP funzionano in diverse edizioni di Windows, ad esempio Home, Professional, Enterprise e così via. Per verificare se un provider CSP funziona in un'edizione specifica, vedere i [provider di servizi di configurazione (CSP) di criteri di Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies) (il collegamento apre un altro sito Microsoft).

## <a name="create-a-template"></a>Creare un modello

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome per il profilo.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
    - **Tipo di profilo**: selezionare **Modelli amministrativi**.

4. Selezionare **Crea**. Nella nuova finestra selezionare **Impostazioni**. Vengono elencate tutte le impostazioni ed è possibile usare le frecce avanti e indietro per visualizzare più impostazioni:

    ![Esempio di un elenco di impostazioni con le frecce avanti e indietro](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Le impostazioni di Windows in Intune sono correlate al percorso dei Criteri di gruppo locali visualizzato in Editor Criteri di gruppo locali (`gpedit`).

5. Per impostazione predefinita, l'elenco a discesa mostra **Tutti i prodotti**. Dall'elenco è anche possibile filtrare le impostazioni in modo da visualizzare solo le impostazioni di **Windows** o solo le impostazioni di **Office**:

    ![Filtrare l'elenco per visualizzare tutte impostazioni di Windows o di Office nei modelli amministrativi in Intune](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

6. Selezionare un'impostazione qualsiasi, Ad esempio, filtrare in base a **Office** e selezionare **Attivazione esplorazione con restrizioni**. Viene visualizzata una descrizione dettagliata dell'impostazione. Scegliere **Abilitata**, **Disabilitata** oppure lasciare l'opzione **Non configurata** (impostazione predefinita). La descrizione dettagliata spiega anche cosa accade quando si sceglie **Abilitata**, **Disabilitata** o **Non configurata**.
7. Selezionare **OK** per salvare le modifiche.

Continuare a scorrere l'elenco delle impostazioni e configurare quelle che si vogliono implementare nell'ambiente. Ecco alcuni esempi:

- Usare l'impostazione **Impostazioni notifiche macro VBA** per gestire le macro VBA in diverse applicazioni Microsoft Office, tra cui Word ed Excel.
- Usare l'impostazione **Consenti download dei file** per consentire o impedire i download da Internet Explorer.
- Usare l'impostazione **Richiedi password alla riattivazione del computer (alimentazione da rete elettrica)** per richiedere agli utenti una password quando il dispositivo torna attivo dopo uno stato di inattività.
- Usare l'impostazione **Scarica controlli ActiveX non firmati** per impedire agli utenti di scaricare controlli ActiveX non firmati da Internet Explorer.
- Usare l'impostazione **Disattiva Ripristino configurazione di sistema** per consentire o impedire agli utenti di eseguire un ripristino del sistema sul dispositivo.
- E molte altre...

## <a name="find-some-settings"></a>Trovare alcune impostazioni

In questi modelli sono disponibili centinaia di impostazioni. Per trovare più facilmente determinate impostazioni, usare le funzionalità predefinite:

- Nel modello selezionare la colonna **Impostazioni**, **Stato**, **Tipo di impostazione** o **Percorso** per ordinare l'elenco. Ad esempio, selezionare la colonna **Percorso** per visualizzare tutte le impostazioni disponibili nel percorso `Microsoft Excel`:

  ![Fare clic sul percorso per visualizzare tutte le impostazioni raggruppate in base ai Criteri di gruppo o al percorso ADMX nei modelli amministrativi in Intune.](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Usare la **casella di ricerca** del modello per trovare impostazioni specifiche. È possibile eseguire la ricerca di impostazioni in base al titolo o al percorso. Ad esempio, cercare `copy`. Vengono visualizzate tutte le impostazioni che contengono `copy`:

  ![Ricerca di copy per visualizzare tutte le impostazioni di Windows e Office nei modelli amministrativi in Intune](./media/administrative-templates-windows/search-copy-settings.png) 

  In un altro esempio cercare `microsoft word`. Vengono visualizzate tutte le impostazioni che è possibile configurare per l'applicazione Microsoft Word. Cercare `explorer` per visualizzare tutte le impostazioni di Internet Explorer che è possibile aggiungere al modello.

## <a name="next-steps"></a>Passaggi successivi

Il modello è stato creato, ma non è ancora operativo. [Assegnare il modello, detto anche profilo](device-profile-assign.md), e [monitorarne lo stato](device-profile-monitor.md).
