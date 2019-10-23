---
title: Usare i modelli per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Usare i modelli amministrativi di Microsoft Intune per creare gruppi di impostazioni per dispositivi Windows 10. Usare queste impostazioni in un profilo di configurazione del dispositivo per controllare le applicazioni di Office, Microsoft Edge, proteggere le funzionalità di Internet Explorer, controllare l'accesso a OneDrive, usare le funzionalità di desktop remoto, abilitare la riproduzione automatica, impostare le opzioni di risparmio energia, usare la stampa HTTP, usare opzioni di accesso diverse e controllare le dimensioni del registro eventi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7f5a85896a2e6e7be845b2314c4f837dcaeb7b0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507029"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Usare i modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune

Per gestire i dispositivi di un'organizzazione, può essere utile creare un gruppo di impostazioni da applicare a gruppi di dispositivi diversi. Supponiamo ad esempio di avere vari gruppi di dispositivi. A GruppoA si vuole assegnare un set di impostazioni specifico. A GruppoB si vuole assegnare un set di impostazioni diverso. Si vuole anche disporre di una visualizzazione semplice delle impostazioni che è possibile configurare.

Per completare questa attività, è possibile usare **Modelli amministrativi** in Microsoft Intune. I modelli amministrativi includono centinaia di impostazioni che controllano le funzionalità in Microsoft Edge versione 77 e successive, Internet Explorer, applicazioni Microsoft Office, Desktop remoto, OneDrive, password e PIN e altro ancora. Queste impostazioni consentono agli amministratori di gruppi di gestire i Criteri di gruppo tramite il cloud.

Le impostazioni di Windows sono simili alle impostazioni di Criteri di gruppo (GPO) in Active Directory (AD). Queste impostazioni sono incluse in Windows e sono [impostazioni supportate da ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) che usano XML. Le impostazioni di Office e Microsoft Edge vengono inserite in ADMX e usano le impostazioni di ADMX nei [file dei modelli amministrativi di Office](https://www.microsoft.com/download/details.aspx?id=49030) e nei [file dei modelli amministrativi di Microsoft Edge](https://www.microsoftedgeinsider.com/enterprise). Tuttavia, i modelli di Intune sono completamente basati sul cloud. Offrono un modo semplice e immediato di configurare le impostazioni e trovare quelle che interessano.

La funzionalità **Modelli amministrativi** è incorporata in Intune e non richiede alcuna personalizzazione, incluso l'uso di OMA-URI. Usare queste impostazioni dei modelli nella propria soluzione di gestione di dispositivi mobili (MDM) per gestire i dispositivi Windows 10 da una posizione centralizzata.

Questo articolo illustra i passaggi da eseguire per creare un modello per dispositivi Windows 10 e mostra come filtrare tutte le impostazioni disponibili in Intune. Con la creazione del modello viene creato un profilo di configurazione del dispositivo. È quindi possibile assegnare o distribuire questo profilo ai dispositivi Windows 10 dell'organizzazione.

## <a name="before-you-begin"></a>Prima di iniziare

- Alcune di queste impostazioni sono disponibili a partire da Windows 10 versione 1703 (RS2). Alcune impostazioni non sono incluse in tutte le edizioni di Windows. Per un'esperienza ottimale, è consigliabile usare Windows 10 Enterprise versione 1903 (19H1) e versioni successive.

- Le impostazioni di Windows usano i [provider di servizi di configurazione (CSP) dei criteri di Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies). I provider CSP funzionano in diverse edizioni di Windows, ad esempio Home, Professional, Enterprise e così via. Per verificare se un provider CSP funziona in un'edizione specifica, vedere i [provider di servizi di configurazione (CSP) di criteri di Windows](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#policies-supported-by-group-policy-and-admx-backed-policies).

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

5. Per impostazione predefinita, l'elenco a discesa mostra **Tutti i prodotti**. Dall'elenco è anche possibile filtrare le impostazioni in modo da visualizzare solo quelle di **Windows**, solo quelle di **Office** o solo quelle di **Edge versione 77 o successiva**:

    ![Filtrare l'elenco per visualizzare tutte impostazioni di Windows o di Office nei modelli amministrativi in Intune](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > Le impostazioni di Microsoft Edge si applicano a:
    >
    > - Microsoft Edge versione 77 e successive. Per configurare Microsoft Edge versione 45 e precedenti, vedere le [impostazioni relative alle restrizioni dei dispositivi per il browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).
    > - Windows 10 RS4 e versioni successive con [KB 4512509](https://support.microsoft.com/kb/4512509) installato
    > - Windows 10 RS5 e versioni successive con [KB 4512534](https://support.microsoft.com/kb/4512534) installato
    > - Windows 10 19H1 e versioni successive con [KB 4512941](https://support.microsoft.com/kb/4512941) installato

6. Selezionare un'impostazione qualsiasi, Ad esempio, filtrare in base a **Office** e selezionare **Attivazione esplorazione con restrizioni**. Viene visualizzata una descrizione dettagliata dell'impostazione. Scegliere **Abilitata**, **Disabilitata** oppure lasciare l'opzione **Non configurata** (impostazione predefinita). La descrizione dettagliata spiega anche cosa accade quando si sceglie **Abilitata**, **Disabilitata** o **Non configurata**.
7. Selezionare **OK** per salvare le modifiche.

Continuare a scorrere l'elenco delle impostazioni e configurare quelle che si vogliono implementare nell'ambiente. Ecco alcuni esempi:

- Usare l'impostazione **Impostazioni notifiche macro VBA** per gestire le macro VBA in diverse applicazioni Microsoft Office, tra cui Word ed Excel.
- Usare l'impostazione **Consenti download dei file** per consentire o impedire i download da Internet Explorer.
- Usare **Richiedi password alla riattivazione del computer (alimentazione da rete elettrica)** per richiedere agli utenti una password quando il dispositivo torna attivo dopo uno stato di inattività.
- Usare l'impostazione **Scarica controlli ActiveX non firmati** per impedire agli utenti di scaricare controlli ActiveX non firmati da Internet Explorer.
- Usare l'impostazione **Disattiva Ripristino configurazione di sistema** per consentire o impedire agli utenti di eseguire un ripristino del sistema sul dispositivo.
- Usare l'impostazione **Allow importing of favorites** (Consenti importazione Preferiti) per consentire o impedire agli utenti di importare i Preferiti da un altro browser in Microsoft Edge.
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
