---
title: Creare un report dal feed OData con Power BI
titlesuffix: Microsoft Intune
description: Creare una visualizzazione ad albero usando Power BI Desktop con un filtro interattivo dall'API data warehouse di Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 9c93554fd6750459aacc154165e7a58e160534fb
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429713"
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Creare un report dal feed OData con Power BI

Questo articolo spiega come creare una visualizzazione ad albero usando Power BI Desktop con un filtro interattivo. È possibile ad esempio che il CFO desideri visualizzare la distribuzione generale dei dispositivi confrontando dispositivi di proprietà dell'azienda e dispositivi personali. La visualizzazione ad albero offre informazioni dettagliate sul totale dei tipi di dispositivi. È possibile esaminare il numero di dispositivi iOS, Android e Windows di proprietà dell'azienda o personali.

### <a name="overview-of-creating-the-chart"></a>Panoramica della creazione del grafico

Per creare il grafico, è necessario:
1. Installare Power BI Desktop se non è già stato installato.
2. Connettersi al modello di dati del data warehouse di Intune e recuperare i dati correnti del modello.
3. Creare o gestire le relazioni dei modelli di dati.
4. Creare il grafico con i dati della tabella **devices**.
5. Creare un filtro interattivo.
6. Visualizzare il grafico completato.

### <a name="a-note-about-tables-and-entities"></a>Nota sulle tabelle e sulle entità

In Power BI vengono usate le tabelle. Una tabella contiene campi dati. Ogni campo dati ha un tipo di dati. Il campo può contenere solo dati del tipo di dati del campo. I tipi di dati possono essere numeri, testo, date e così via. Quando si carica il modello, i dati cronologici recenti del tenant vengono inseriti nelle tabelle in Power BI. Sebbene i dati specifici vengano modificati con il tempo, la struttura della tabella non viene modificata a meno che non venga aggiornato il modello di dati sottostante.

È importante non confondere l'uso dei termini _entità_ e _tabella_. Il modello di dati è accessibile attraverso un feed OData. In OData i contenitori chiamati tabelle in Power BI sono chiamati entità. Entrambi i termini si riferiscono al medesimo elemento che contiene i dati.

## <a name="install-power-bi-desktop"></a>Installare Power BI Desktop

Installare l'ultima versione di Power BI Desktop. È possibile scaricare Power BI Desktop da: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>Connettersi al feed OData del data warehouse di Intune per il tenant

> [!Note]  
> È necessario disporre dell'autorizzazione per l'accesso ai **report** in Intune. Per altre informazioni, vedere [Autorizzazione](reports-api-url.md).

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Aprire il riquadro **Data warehouse** di Intune.
4. Copiare l'URL del feed personalizzato. ad esempio `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`
5. Aprire Power BI Desktop.
6. Scegliere **Recupera dati** > **Feed OData**.
7. Incollare l'URL del feed personalizzato nella casella URL nella finestra **Feed OData**.
8. Selezionare **Di base**.

    ![Feed OData](media/reports-create-01-odatafeed.png)

9. Selezionare **OK**.
10. Selezionare **account aziendale** e quindi accedere con le credenziali di Intune.

    ![Credenziali dell'account aziendale](media/reports-create-02-org-account.png)

11. Selezionare **Connetti**. Viene visualizzato lo strumento di navigazione con l'elenco delle tabelle del data warehouse di Intune.

    ![Strumento di navigazione](media/reports-create-02-loadentities.png)

12. Selezionare le tabelle **devices** e **ownerTypes**.  Selezionare **Carica**. Power BI carica i dati nel modello.

## <a name="create-a-relationship"></a>Creare una relazione

È possibile importare più tabelle per analizzare i dati correlati di più tabelle anziché i dati di una singola tabella.  PowerBI include una funzionalità denominata **Rilevamento automatico** che rileva e crea le relazioni automaticamente. Le tabelle del data warehouse sono state progettate per essere usate con la funzionalità di rilevamento automatico di PowerBI. Tuttavia, anche nel caso in cui PowerBI non rilevi automaticamente le relazioni, è possibile gestire le relazioni.

![Gestire le relazioni](media/reports-create-03-managerelationships.png)

1. Selezionare **Gestione relazioni**.
2. Selezionare **Rileva automaticamente...** se PowerBI non ha ancora individuato le relazioni.

La relazione è visualizzata dalla colonna Da alla colonna A. In questo esempio il campo dati **ownerTypeKey** della tabella **devices** viene collegato al campo dati **ownerTypeKey** della tabella **ownerTypes**. È possibile usare la relazione per cercare il nome del codice del tipo di dispositivo nella tabella **devices**.

## <a name="create-a-treemap-visualization"></a>Creare una visualizzazione ad albero

Un grafico ad albero mostra i dati gerarchici come caselle all'interno di caselle. Ogni ramo della gerarchia è una casella contenente caselle più piccole che mostrano rami secondari. È possibile usare Power BI Desktop per creare una mappa ad albero dei dati di Intune.

![Visualizzazioni > Mappa ad albero](media/reports-create-03-treemap.png)

1. Selezionare un tipo di grafico. Selezionare **Mappa ad albero**.
2. Nel modello di dati cercare la tabella **devices**.
3. Espandere la tabella **devices** e selezionare il campo dati **manufacturer** nel pannello **Campi**.
4. Trascinare il campo dati **manufacturer** nel grafico Mappa ad albero nell'area di disegno report.
5. Trascinare il campo dati **deviceKey** dalla tabella **devices** alla sezione **Valori** nel riquadro **Visualizzazioni** e rilasciarlo nella casella **Trascinare qui i campi dati**.  

È ora disponibile una visualizzazione della distribuzione dei produttori di dispositivi all'interno dell'organizzazione.

![Mappa ad albero con dati](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>Aggiungere un filtro

È possibile aggiungere un filtro alla mappa ad albero per poter rispondere a domande aggiuntive usando l'app.


1. Per aggiungere un filtro, selezionare l'area di disegno report e quindi selezionare l'**icona Filtro dei dati** (![Mappa ad albero con dati e relazioni supportate](media/reports-create-slicer.png)) in **Visualizzazioni**.
2. Cercare la tabella **ownerTypes** e trascinare il campo dati **ownerTypeName** nella sezione **Filtri** nel pannello **Visualizzazioni**.  

   Nella tabella devices è incluso un campo dati denominato **OwnerTypeKey** che contiene un codice che indica se il dispositivo è aziendale o personale. Per visualizzare i nomi descrittivi nel filtro, cercare la tabella **ownerTypes** e trascinare **ownerTypeName**. Questo esempio illustra come il modello di dati supporta le relazioni tra le tabelle.

![Mappa ad albero con filtro](media/reports-create-08_ownertype.png)

È ora disponibile un filtro interattivo che consente di passare dai dispositivi aziendali ai dispositivi personali. Usare questo filtro per vedere in che modo cambia la distribuzione.

1. Selezionare **Società** per visualizzare la distribuzione dei dispositivi aziendali.
2. Selezionare **Personale** per visualizzare i dispositivi personali.

## <a name="next-steps"></a>Passaggi successivi

 - Altre informazioni sulla [creazione e la gestione delle relazioni](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/) sono disponibili in Power BI Desktop nella documentazione di Power BI.
 - Vedere [Modello di dati del data warehouse](https://docs.microsoft.com/intune/reports-ref-data-model).
