---
title: Connettersi al data warehouse con Power BI
titleSuffix: Microsoft Intune
description: È possibile scaricare un file per l'uso con Microsoft Power BI che consente di caricare report interattivi, generati in modo dinamico per il tenant di Microsoft Intune.
keywords: Data warehouse di Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/14/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7bc3247399341a59533e87fc5e21a44c061acddd
ms.sourcegitcommit: b30a2ba2b67aa2fc3421f0b2f6c5f361a0de612a
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2019
ms.locfileid: "71303194"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Connettersi al data warehouse con Power BI

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

È possibile usare l'app Compliance di Power BI per caricare report interattivi e generati in modo dinamico per il tenant di Intune. Inoltre, è possibile caricare i dati del tenant in Power BI usando il collegamento OData. Intune include impostazioni di connessione per il tenant che consentono di visualizzare grafici e report di esempio relativi a:  

- Dispositivi
- Registrazione
- Criterio di protezione dell'app
- Criteri di conformità
- Profili di configurazione dispositivo
- Aggiornamenti software
- Log inventario del dispositivo

Sono anche evidenziate le tendenze per la registrazione, la conformità, il profilo di configurazione dispositivo e gli aggiornamenti software. I report e i grafici di esempio applicano filtri semplici all'area di disegno. Per usare i filtri avanzati, vedere il riquadro **Filtro** in Power BI Desktop.

La procedura seguente illustra come scaricare il file di Power BI e come usare il collegamento OData con Power BI.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Installare Power BI

Installare l'ultima versione di [Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi). Per altre informazioni, vedere [Power BI Desktop](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>Caricare i dati e report tramite l'app Intune Compliance (Data Warehouse) di Power BI

L'app [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) di Power BI contiene informazioni per il tenant e un set di report predefiniti basati sul modello di dati del data warehouse.

1. Passare alla pagina **AppSource** dell'app [Intune Compliance (Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) per avviare il processo di installazione.
2. Fare clic sul pulsante **Get it Now (Ottieni ora** ) e quindi su **continue (continua**).
3. Quando viene richiesto di installare l'app Power BI, fare clic su **Installa**.
4. Al termine dell'installazione, fare clic sul riquadro dell'app **conformità a Intune (data warehouse)** .
5. Fare clic sul pulsante **Connetti**. Viene visualizzata la finestra di dialogo **Connect to Intune Compliance (Data Warehouse)** (Connetti a Intune Compliance (Data Warehouse).
6. Fare clic sul pulsante **Accedi**.
7. Eseguire l'accesso con un account utente che disponga di accesso al data warehouse di Intune per il tenant che ospita i report da visualizzare.
8. Per visualizzare il dashboard incluso, fare clic sulla scheda **Dashboard** , quindi fare clic sul dashboard **Panoramica conformità** .
9. Per visualizzare tutti i report disponibili, fare clic sulla scheda **report** , quindi fare clic sul report **conformità v 1.0** . Scorrere le pagine del report facendo clic sulle schede nella parte inferiore.
10. Per passare nuovamente a questi report con facilità in un secondo momento, fare clic sull'asterisco accanto al report **Compliance V1.0**. In questo modo il report verrà aggiunto ai preferiti di Power BI.

In alternativa, è possibile installare l'app dal portale di Intune:

1. Accedere al portale di Azure e scegliere **Monitoraggio e gestione** > **Intune**. È anche possibile cercare risorse per Intune.
2. Aprire il pannello **Configura il data warehouse di Intune**.
3. Selezionare **Scarica l'app Power BI** per accedere a report di Power BI creati in precedenza per il tenant e condividerli nel browser.
4. Seguire i passaggi 2-10 riportati in precedenza.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>Caricare i dati in Power BI usando il collegamento OData

Con un client autenticato in Azure AD, l'URL di OData si connette all'endpoint RESTful dell'API data warehouse che espone il modello di dati al client di creazione di report. Seguire queste istruzioni per usare Power BI Desktop per connettersi e creare report personalizzati. Non si è limitati a Power BI Desktop, ma si può usare lo strumento analitico preferito con l'URL di OData, purché il client supporti l'autenticazione OAUTH2.0 e lo standard OData 4.0.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Fare clic su **Configura Intune data warehouse** nella sezione **altre attività** sul lato destro del pannello panoramica. Verrà visualizzato il pannello **data warehouse di Intune** .
3. Recuperare l'URL feed personalizzato nel pannello Report, ad esempio `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. Aprire **Power BI Desktop**.
5. Scegliere **Home** > **Recupera dati**. Selezionare **Feed OData**.
6. Scegliere **Basic**.
7. Digitare o incollare l'**URL OData** nella casella URL.
8. Selezionare **OK**.
9. Se non è stata ancora eseguita l'autenticazione del tenant in Azure AD dal client desktop di Power BI, digitare le credenziali. Per ottenere l'accesso ai dati, è necessario concedere l'autorizzazione con Azure Active Directory (Azure AD) usando OAuth 2.0.  
    1. Selezionare **Account aziendale**.  
    2. Digitare il nome utente e la password.  
    3. Selezionare **Accedi**.  
    4. Selezionare **Connetti**.  
10. Selezionare **Carica**.

## <a name="next-steps"></a>Passaggi successivi

È possibile trovare le risposte alle domande sull'ambiente, ad esempio il numero di dispositivi registrati per ogni giorno nell'ultima settimana. È possibile esaminare a fondo il tenant di Intune e il gruppo di client con i report di Power BI del data warehouse di Intune recuperati dal pannello in Azure. Tuttavia, Intune fornisce una serie di altri modi per estendere o riutilizzare i dati. Power BI e l'API data warehouse di Microsoft Intune offrono funzionalità aggiuntive, ad esempio:

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- I dati del tenant sono organizzati in modo da contribuire all'estrazione di informazioni dettagliate dai dati. Per altre informazioni sull'organizzazione dei dati, vedere [Modello di dati del data warehouse](reports-ref-data-model.md).
- È anche possibile accedere ai dati da un'interfaccia RESTful e incorporarli nell'app. Per altre informazioni, vedere [Recuperare dati dall'API data warehouse con un client REST](reports-proc-data-rest.md).
