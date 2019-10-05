---
title: Creare un report di Intune dal feed OData con Power BI
titleSuffix: Microsoft Intune
description: Creare una visualizzazione ad albero usando Power BI Desktop con un filtro interattivo dall'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/15/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: b1a508a6c9bf834268a797f028a32c7651cf394c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733478"
---
# <a name="create-an-intune-report-from-the-odata-feed-with-power-bi"></a>Creare un report di Intune dal feed OData con Power BI

Questo articolo illustra come creare una visualizzazione mappa ad albero dei dati di Intune usando Power BI Desktop che consente agli utenti un filtro interattivo. Ad esempio, il CFO potrebbe voler capire come viene confrontata la distribuzione complessiva dei dispositivi tra dispositivi di proprietà dell'azienda e dispositivi personali. La visualizzazione ad albero offre informazioni dettagliate sul totale dei tipi di dispositivi. È possibile esaminare il numero di dispositivi iOS, Android e Windows di proprietà dell'azienda o personali.

## <a name="overview-of-creating-the-chart"></a>Panoramica della creazione del grafico

Per creare il grafico:
1. Installare Power BI Desktop se non è già stato installato.
2. Connettersi al modello di dati del data warehouse di Intune e recuperare i dati correnti del modello.
3. Creare o gestire le relazioni dei modelli di dati.
4. Creare il grafico con i dati della tabella **devices**.
5. Creare un filtro interattivo.
6. Visualizzare il grafico completato.

### <a name="a-note-about-tables-and-entities"></a>Nota sulle tabelle e sulle entità

In Power BI vengono usate le tabelle. Una tabella contiene campi dati. Ogni campo dati ha un tipo di dati. Il campo può contenere solo dati del tipo di dati del campo. I tipi di dati possono essere numeri, testo, date e così via. Quando si carica il modello, i dati cronologici recenti del tenant vengono inseriti nelle tabelle in Power BI. Sebbene i dati specifici vengano modificati con il tempo, la struttura della tabella non viene modificata a meno che non venga aggiornato il modello di dati sottostante.

È importante non confondere l'uso dei termini *entità* e *tabella*. Il modello di dati è accessibile tramite un feed OData (Open Data Protocol). In OData i contenitori chiamati tabelle in Power BI sono chiamati entità. Entrambi i termini si riferiscono al medesimo elemento che contiene i dati. Per ulteriori informazioni su OData, vedere la [Panoramica di OData](/odata/overview).

## <a name="install-power-bi-desktop"></a>Installare Power BI Desktop

Installare l'ultima versione di Power BI Desktop. È possibile scaricare Power BI Desktop da: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Connettersi al feed OData del data warehouse di Intune per il tenant

> [!Note]  
> È necessario disporre dell'autorizzazione per l'accesso ai **report** in Intune. Per altre informazioni, vedere [Autorizzazione](../reports-api-url.md).

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Aprire il riquadro **Data warehouse di Intune** selezionando il collegamento Data warehouse in **Altre attività** sul lato destro del pannello **Microsoft Intune - Panoramica**.
3. Copiare l'URL del feed personalizzato. ad esempio `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
4. Aprire Power BI Desktop.
5. Dalla barra dei menu selezionare **File** > **Ottieni dati** > **feed OData**.
6. Incollare l'URL del feed personalizzato copiato dal passaggio precedente nella casella URL della finestra **feed OData** .
7. Selezionare **Di base**.

    ![Feed OData del data warehouse di Intune per il tenant](./media/reports-proc-create-with-odata/reports-create-01-odatafeed.png)

8. Selezionare **OK**.
9. Selezionare **account aziendale** e quindi accedere con le credenziali di Intune.

    ![Credenziali dell'account aziendale](./media/reports-proc-create-with-odata/reports-create-02-org-account.png)

10. Selezionare **Connetti**. Viene visualizzato lo strumento di navigazione con l'elenco delle tabelle del data warehouse di Intune.

    ![Screenshot dello strumento di navigazione: elenco delle tabelle del data warehouse](./media/reports-proc-create-with-odata/reports-create-02-loadentities.png)

11. Selezionare le tabelle **devices** e **ownerTypes**.  Selezionare **Carica**. Power BI carica i dati nel modello.

## <a name="create-a-relationship"></a>Creare una relazione

È possibile importare più tabelle per analizzare i dati correlati di più tabelle anziché i dati di una singola tabella. Power BI include una funzionalità denominata **Rilevamento automatico** che rileva e crea le relazioni automaticamente. Le tabelle del data warehouse sono state progettate per interagire con la funzionalità di rilevamento automatico in Power BI. Tuttavia, anche nel caso in cui Power BI non rilevi automaticamente le relazioni, è possibile gestire le relazioni.

![Gestire le relazioni di dati correlati tra tabelle](./media/reports-proc-create-with-odata/reports-create-03-managerelationships.png)

1. Selezionare **Gestione relazioni**.
2. Selezionare **Rileva automaticamente** se Power BI non ha ancora individuato le relazioni.

La relazione è visualizzata dalla colonna Da alla colonna A. In questo esempio il campo dati **ownerTypeKey** della tabella **devices** viene collegato al campo dati **ownerTypeKey** della tabella **ownerTypes**. È possibile usare la relazione per cercare il nome del codice del tipo di dispositivo nella tabella **devices**.

## <a name="create-a-treemap-visualization"></a>Creare una visualizzazione ad albero

Un grafico ad albero mostra i dati gerarchici come caselle all'interno di caselle. Ogni ramo della gerarchia è una casella contenente caselle più piccole che mostrano rami secondari. È possibile usare Power BI desktop per creare una mappa ad albero dei dati del tenant di Intune che mostra le quantità relative di tipi di produttore di dispositivi.

![Visualizzazioni mappa ad albero di Power BI](./media/reports-proc-create-with-odata/reports-create-03-treemap.png)

1. Nel riquadro **visualizzazioni** individuare e selezionare **mappa ad albero**. Il grafico **mappa ad albero** verrà aggiunto all'area di disegno report.
2. Individuare la `devices` tabella nel riquadro **campi**.
3. Espandere la tabella `devices` e selezionare il campo dati `manufacturer`.
4. Trascinare il campo dati `manufacturer` nell'area di disegno report e rilasciarlo nel grafico **mappa ad albero** .
5. Trascinare il campo dati `deviceKey` dalla tabella `devices` al riquadro **visualizzazioni** e rilasciarlo nella sezione **valori** della casella **Aggiungi campi dati qui**.  

È ora disponibile una visualizzazione della distribuzione dei produttori di dispositivi all'interno dell'organizzazione.

![Mappa ad albero con dati: distribuzione dei produttori di dispositivi](./media/reports-proc-create-with-odata/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Aggiungere un filtro

È possibile aggiungere un filtro alla mappa ad albero per poter rispondere a domande aggiuntive usando l'app.

1. Per aggiungere un filtro, selezionare l'area di disegno report e quindi selezionare l'**icona Filtro dei dati** (![Mappa ad albero con dati e relazioni supportate](./media/reports-proc-create-with-odata/reports-create-slicer.png)) in **Visualizzazioni**. Verrà visualizzata la visualizzazione **filtro dei dati** vuota nell'area di disegno.
2. Individuare la `ownerTypes` tabella nel riquadro **campi**.
3. Espandere la tabella `ownerTypes` e selezionare il campo dati `ownerTypeName`.
4. Trascinare il campo dati `onwerTypeName` dalla tabella `ownerTypes` al riquadro **filtri** e rilasciarlo nella sezione **filtri in questa pagina** della casella etichetta **Aggiungi campi dati qui**.  

   Nella tabella `OwnerTypes` è disponibile un campo dati denominato `OwnerTypeKey` che che contiene i dati relativi al fatto che un dispositivo sia di proprietà dell'azienda o personale. Per visualizzare i nomi descrittivi nel filtro, cercare la tabella `ownerTypes` e trascinare **ownerTypeName** nel filtro dei dati. Questo esempio illustra come il modello di dati supporta le relazioni tra le tabelle.

![Mappa ad albero con filtro: supporto di relazioni tra tabelle](./media/reports-proc-create-with-odata/reports-create-08_ownertype.png)

È ora disponibile un filtro interattivo che consente di passare dai dispositivi aziendali ai dispositivi personali. Usare questo filtro per vedere in che modo cambia la distribuzione.

1. Selezionare **azienda** nel filtro dei dati per vedere la distribuzione dei dispositivi di proprietà dell'azienda.
2. Selezionare **personale** nel filtro dei dati per visualizzare i dispositivi di proprietà personale.

## <a name="next-steps"></a>Passaggi successivi

- Altre informazioni sulla [creazione e la gestione delle relazioni](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) sono disponibili in Power BI Desktop nella documentazione di Power BI.
- Vedere [Modello di dati del data warehouse](reports-ref-data-model.md).
