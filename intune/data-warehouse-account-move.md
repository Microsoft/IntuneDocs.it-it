---
title: Spostare i dati dell'account del data warehouse di Intune
titlesuffix: Microsoft Intune
description: Informazioni su come eseguire il backup dei dati del data warehouse di Intune prima di spostare l'account.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0acbde0774b8f3a709fc4e6995393e9845ae07e
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566115"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Spostare i dati dell'account del data warehouse di Intune 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando si richiede lo spostamento di un account, di fatto si richiede che il proprio data center cambi posizione. Dopo lo spostamento, il data warehouse viene reimpostato e inizia a registrare i dati nella nuova posizione a partire dal giorno specificato per l'inizio dello spostamento. Per eseguire il backup dei dati del data warehouse precedente, completare la procedura seguente **prima** di spostare l'account. La maggior parte delle tabelle del data warehouse conserva i dati per 30 giorni, pertanto eventuali dati mancanti in queste tabelle non saranno più disponibili a partire da 30 giorni dopo lo spostamento dell'account. Per altre informazioni sui periodi di mantenimento dati per tabelle specifiche, vedere [Modello di dati del data warehouse](reports-ref-data-model.md). 

## <a name="back-up-your-data-warehouse-data"></a>Eseguire il backup dei dati del data warehouse 

Per eseguire il backup dei dati del data warehouse, è necessario salvare tali dati in un file con estensione *csv* mediante l'API data warehouse:  

1. Se si usa l'API data warehouse per la prima volta, eseguire una sola volta la procedura descritta nell'articolo [Recuperare dati dall'API data warehouse di Intune con un client REST](reports-proc-data-rest.md).
2. Usare l'esempio di PowerShell [Access the Intune Data Warehouse with PowerShell](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell) (Accedere al data warehouse di Intune con PowerShell) per scaricare tutti i dati in file CSV. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Eseguire il backup dei grafici di tendenza dal portale di Azure

Alcuni grafici di tendenza nella visualizzazione del portale di Azure verranno reimpostati. È possibile eseguire un backup di questi grafici eseguendo lo script seguente in **Graph**:   

### <a name="terms--conditions-acceptance-reports"></a>Report Accettazione di termini e condizioni
1. Nel portale di Azure passare a **Microsoft Intune** -> **Registrazione del dispositivo** -> **Condizioni**.
2. Per ogni voce **Condizioni** selezionare **Report accettazione** seguito da **Esporta**.
3. Salvare il report in locale.
 
### <a name="app-protection-reports"></a>Report protezione app  
1. Nel portale di Azure passare a **Microsoft Intune** -> **App client** -> **Stato protezione app**.
2. Fare clic sull'icona di download ( ⤓ )per salvare ogni report.

### <a name="device-configuration-charts"></a>Grafici di configurazione dispositivi 
1. Nel portale di Azure passare a **Microsoft Intune** -> **Configurazione del dispositivo**.
2. Scaricare i dati sottostanti i grafici usando Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer). 
    - Per informazioni sullo stato di distribuzione di tutti i profili di configurazione dispositivo per tutti i dispositivi, vedere [Device deployment status](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content) (Stato distribuzione dispositivi).

    - Per informazioni sullo stato di distribuzione di tutti i profili di configurazione dispositivo per tutti gli utenti, vedere [Device deployment status](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content) (Stato distribuzione utenti).

    - Per informazioni sullo stato di distribuzione dei profili, vedere [Provide deployment status](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview) (Fornire lo stato distribuzione).
  
    > [!NOTE]
    > È necessario avere un token di autenticazione valido per accedere alle informazioni sullo stato di configurazione e distribuzione.

## <a name="device-enrollment-charts"></a>Grafici di registrazione dei dispositivi
1. Nel portale di Azure passare a **Microsoft Intune** -> **Registrazione del dispositivo**.
2. Scaricare i dati sottostanti i grafici usando Microsoft [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
    - Per lo stato di registrazione, copiare questa [query sullo stato della registrazione](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content) e incollarla in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
    - Per i principali errori di registrazione questa settimana, copiare questa [query sugli errori di registrazione](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content) e incollarla in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

    > [!NOTE]
    > È necessario avere un token di autenticazione valido per accedere ai dati di registrazione dei dispositivi. 

## <a name="after-a-data-warehouse-account-move"></a>Dopo lo spostamento di un account del data warehouse

Dopo lo spostamento dell'account del data warehouse, in Intune si vedrà che il data warehouse è stato reimpostato e che i dati sono ora archiviati nella nuova posizione. I grafici e le opzioni di esportazione verranno reimpostati e verrà visualizzata una notifica, facendo clic sulla quale si verrà indirizzati a un articolo che spiega perché i grafici sono stati reimpostati.  

## <a name="data-warehouse-move-example"></a>Esempio di spostamento di data warehouse 

Il cliente X richiede lo spostamento di un account a partire dal 06/01/2018. In risposta alla richiesta, il cliente riceverà un collegamento a una procedura dettagliata della documentazione da seguire in caso voglia eseguire un backup del data warehouse precedente. Il giorno 06/01/2018, il data warehouse e i grafici che supporta verranno reimpostati e inizieranno ad archiviare i dati nel nuovo data center. 

## <a name="next-steps"></a>Passaggi successivi

 - Informazioni sulle [novità di Intune ogni settimana](whats-new.md), oltre a indicazioni su modifiche previste, avvisi importanti sul servizio e informazioni sulle versioni precedenti.
 - Leggere il [blog di Microsoft Intune](https://go.microsoft.com/fwlink/?LinkID=273882).
