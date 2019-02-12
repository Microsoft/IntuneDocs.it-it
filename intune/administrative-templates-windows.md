---
title: Usare i modelli per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Usare i modelli amministrativi di Microsoft Intune per creare gruppi di impostazioni per dispositivi Windows 10. Usare queste impostazioni in un profilo di configurazione del dispositivo per controllare le applicazioni di Office, proteggere le funzionalità di Internet Explorer, controllare l'accesso a OneDrive, usare le funzionalità di desktop remoto, abilitare la riproduzione automatica, impostare le opzioni di risparmio energia, usare la stampa HTTP, usare opzioni di accesso diverse e controllare le dimensioni del log eventi.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 36076aab02f16937066cb3d47d573f7c74dd6277
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55833617"
---
# <a name="windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune

Una soluzione pratica per gestire i dispositivi di un'organizzazione è creare un gruppo di impostazioni da applicare a gruppi di dispositivi diversi. Supponiamo ad esempio di avere vari gruppi di dispositivi. A GruppoA si vuole assegnare un set di impostazioni specifico. A GruppoB si vuole assegnare un set di impostazioni diverso. Si vuole anche disporre di una visualizzazione semplice delle impostazioni che è possibile configurare.

Per completare questa attività, è possibile usare **Modelli amministrativi** in Microsoft Intune. I modelli amministrativi includono centinaia di impostazioni che controllano le funzionalità per Internet Explorer, le applicazioni Microsoft Office, il desktop remoto, l'accesso a OneDrive, l'uso di una password grafica o di un PIN per accedere e altro ancora. Questi modelli sono simili alle impostazioni dei Criteri di gruppo in Active Directory (AD) e sono [impostazioni basate su ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies) che usano il linguaggio XML. I modelli di Intune sono però completamente basati sul cloud. Offrono un modo più semplice e immediato di configurare le impostazioni e trovare quelle che interessano.

La funzionalità **Modelli amministrativi** è incorporata in Intune e non richiede alcuna personalizzazione, incluso l'uso di OMA-URI. Usare queste impostazioni dei modelli nella propria soluzione di gestione di dispositivi mobili (MDM) per gestire i dispositivi Windows 10 da una posizione centralizzata.

Questo articolo illustra i passaggi da eseguire per creare un modello per dispositivi Windows 10 e mostra come filtrare tutte le impostazioni disponibili in Microsoft Intune. Con la creazione del modello viene creato un profilo di configurazione del dispositivo. È quindi possibile assegnare o distribuire questo profilo ai dispositivi Windows 10 dell'organizzazione.

> [!NOTE]
> I modelli amministrativi sono supportati per i dispositivi autonomi. Attualmente non sono supportati per i dispositivi in co-gestione con System Center Configuration Manager (SCCM).

## <a name="create-a-template"></a>Creare un modello

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome per il profilo.
    - **Description**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
    - **Tipo di profilo**: selezionare **Modelli amministrativi (anteprima)**.

4. Selezionare **Crea**. Nella nuova finestra selezionare **Impostazioni**. Vengono elencate tutte le impostazioni ed è possibile usare le frecce avanti e indietro per visualizzare più impostazioni:

    ![Esempio di un elenco di impostazioni con le frecce avanti e indietro](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. Selezionare un'impostazione qualsiasi, ad esempio **Consenti download dei file**. Viene visualizzata una descrizione dettagliata dell'impostazione. Scegliere **Abilita**, **Disabilita** oppure lasciare l'opzione **Non configurata** (impostazione predefinita). La descrizione dettagliata spiega anche cosa accade quando si sceglie **Abilita**, **Disabilita** o **Non configurata**.
6. Selezionare **OK** per salvare le modifiche.

Continuare a scorrere l'elenco delle impostazioni e configurare quelle che si vogliono implementare nell'ambiente. Ecco alcuni esempi:

- Usare l'impostazione **Impostazioni notifiche macro VBA** per gestire le macro VBA in diverse applicazioni Microsoft Office, tra cui Word ed Excel.
- Usare l'impostazione **Consenti download dei file** per consentire o impedire i download da Internet Explorer.
- Usare l'impostazione **Richiedi password alla riattivazione del computer (alimentazione da rete elettrica)** per richiedere agli utenti una password quando il dispositivo torna attivo dopo uno stato di inattività.
- Usare l'impostazione **Scarica controlli ActiveX non firmati** per impedire agli utenti di scaricare controlli ActiveX non firmati da Internet Explorer.
- Usare l'impostazione **Disattiva Ripristino configurazione di sistema** per consentire o impedire agli utenti di eseguire un ripristino del sistema sul dispositivo.
- E molte altre...

## <a name="find-some-settings"></a>Trovare alcune impostazioni

In questi modelli sono disponibili centinaia di impostazioni. Per trovare più facilmente determinate impostazioni, usare le funzionalità predefinite:

- Nel modello selezionare la colonna **Impostazioni**, **Stato** o **Percorso** per ordinare l'elenco. Ad esempio, selezionare la colonna **Percorso** per visualizzare tutte le impostazioni disponibili nel percorso `Microsoft Excel`:

  ![Fare clic su Percorso per elencare le impostazioni in ordine alfabetico](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- Usare la **casella di ricerca** del modello per trovare impostazioni specifiche. Ad esempio, cercare `copy`. Vengono visualizzate tutte le impostazioni che contengono `copy`:

  ![Fare clic su Percorso per elencare le impostazioni in ordine alfabetico](./media/administrative-templates-windows/search-copy-settings.png)

  In un altro esempio cercare `microsoft word`. Vengono visualizzate tutte le impostazioni che è possibile configurare per l'applicazione Microsoft Word. Cercare `explorer` per visualizzare tutte le impostazioni di Internet Explorer che è possibile aggiungere al modello.

## <a name="next-steps"></a>Passaggi successivi

Il modello è stato creato, ma non è ancora operativo. [Assegnare il modello, detto anche profilo](device-profile-assign.md), e [monitorarne lo stato](device-profile-monitor.md).
