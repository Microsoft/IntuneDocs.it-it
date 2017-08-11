---
title: Connettersi al data warehouse con Power BI | Microsoft Docs
description: "È possibile scaricare un file per l'uso con Microsoft Power BI che consente di caricare report interattivi, generati in modo dinamico per il tenant di Intune."
keywords: Data warehouse di Intune
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 07/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a9d99b71b9f84eea45ae597ed0f69010f6e95805
ms.sourcegitcommit: addf6a40caa22c22adfd2e2eff7d666cd1877e3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2017
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Connettersi al data warehouse con Power BI

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile scaricare un file per l'uso con Microsoft Power BI che consente di caricare report interattivi, generati in modo dinamico per il tenant di Intune. Il file di Power BI del data warehouse (PBIX) contiene le impostazioni di connessione al tenant e i seguenti report e grafici di esempio: 

  -  Dispositivi
  -  Registrazione
  -  Criterio di protezione dell'app
  -  Criteri di conformità
  -  Profili di configurazione dispositivo
  -  Aggiornamenti software
  -  Log inventario del dispositivo

Sono anche evidenziate le tendenze per la registrazione, la conformità, il profilo di configurazione dispositivo e gli aggiornamenti software. I report e i grafici di esempio applicano filtri semplici all'area di disegno. Per usare i filtri avanzati, vedere il riquadro **Filtro** in Power BI Desktop. 

La procedura seguente illustra come scaricare il file di Power BI e come usare il collegamento OData con Power BI.

## <a name="install-power-bi"></a>Installare Power BI

Installare l'ultima versione di Power BI Desktop. È possibile scaricare Power BI Desktop da: [PowerBI.microsoft.com](https://powerbi.microsoft.com/en-us/desktop) 

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Caricare i dati e i report usando il file di Power BI (PBIX)

Il file di Power BI (PBIX) contiene informazioni di connessione per il tenant e un set di report predefiniti in base al modello di dati del data warehouse. Aprire il file in Power BI Desktop e accedere a Azure AD. Il report carica i dati dal tenant di Intune.

1.  Accedere al portale di Azure e scegliere **Monitoraggio e gestione** > **Intune**. È anche possibile cercare risorse per **Intune**.  
2.  Aprire il pannello **API data warehouse di Microsoft Intune (anteprima)**.
3.  Fare clic su **Scarica file di Power BI**. Il file con estensione .pbix viene scaricato nel percorso specificato.
4.  Aprire il file con Power BI. Viene caricato *Report data warehouse Intune*, ma il recupero dei dati del tenant potrebbe richiedere alcuni secondi.
5.  Fare clic su **Aggiorna** per caricare i dati del tenant e rivedere i report.
6.  Se Power BI non è autenticato con le credenziali di Azure Active Directory, richiederà all'utente di fornire le proprie credenziali. Quando si selezionano le credenziali, scegliere **Account aziendale** come metodo di autenticazione.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Caricare i dati in Power BI usando il collegamento OData

Con un client autenticato in Azure AD, l'URL di OData si connette all'endpoint RESTful dell'API data warehouse che espone il modello di dati al client di creazione di report. Seguire queste istruzioni per usare Power BI Desktop per connettersi e creare report personalizzati. Non si è limitati a Power BI Desktop, ma si può usare lo strumento analitico preferito con l'URL di OData, purché il client supporti l'autenticazione OAUTH2.0 e lo standard OData 4.0.

1.  Recuperare l'**URL OData** nel pannello di creazione di report, ad esempio `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`.
2.  Aprire **Power BI Desktop**.
3.  Scegliere **Home** > **Recupera dati**. Selezionare **Feed OData**.
4.  Scegliere **Basic**.
5.  Digitare o incollare l'**URL OData** nella casella URL.
6.  Fare clic su **OK**.
7.  Se non è stata ancora eseguita l'autenticazione del tenant in Azure AD dal client desktop di Power BI, digitare le credenziali.  
    a.  Selezionare **Account aziendale**.  
    b.  Digitare il nome utente e la password.  
    c.  Fare clic su **Accedi**.  
    d.  Fare clic su **Connetti**.  
8.  Fare clic su **Carica**.

## <a name="next-steps"></a>Passaggi successivi

È possibile trovare le risposte alle domande sull'ambiente, ad esempio il numero di dispositivi registrati per ogni giorno nell'ultima settimana. È possibile esaminare a fondo il popolamento di tenant e client Intune con i report usando il file di Power BI del data warehouse di Intune (pbix) recuperato dal pannello in Azure. Tuttavia, Intune fornisce una serie di altri modi per estendere o riutilizzare i dati. È possibile fare molto di più con Power BI e l'API data warehouse di Intune, ad esempio:

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  I dati del tenant sono organizzati in modo da contribuire all'estrazione di informazioni dettagliate dai dati. Per altre informazioni sull'organizzazione dei dati, vedere [Modello di dati del data warehouse](reports-ref-data-model.md). 
<!-- -  You can also access the data from a RESTful interface and incorporate the data into your own app. For more information, see [Get data from the Data Warehouse API with a REST client](reports-proc-data-rest.md). -->