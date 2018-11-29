---
title: Monitorare le informazioni sulle app e le assegnazioni
titlesuffix: Microsoft Intune
description: Dopo avere assegnato un'app agli utenti o ai dispositivi, usare queste informazioni per monitorare lo stato dell'app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 457b5b97bd13caddb5c60836940dd491eac752f8
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181888"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune offre diversi modi per monitorare le proprietà delle app gestite e per gestire lo stato di assegnazione delle app.

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Dal menu **Intune** scegliere **App client**.
4. Nella sezione **Gestisci** del menu selezionare **App**.
5. Nell'elenco di app selezionare un'app da monitorare. Verrà quindi visualizzato il riquadro delle app, che include una panoramica dello stato del dispositivo e dello stato dell'utente.

> [!NOTE]
> Le app di Android Store distribuite come **disponibili** non segnalano lo stato dell'installazione.

## <a name="app-overview-pane"></a>Riquadro di panoramica delle app

Nel riquadro delle app è possibile esaminare i dettagli relativi allo stato di un'app nell'ambiente in uso.

### <a name="essentials"></a>Essentials
La sezione **Informazioni di base** contiene le seguenti informazioni sull'app:

 | **Dettagli dell'app**            | **Descrizione**                                                      |
|------------------------|------------------------------------------------------------------|
| **Autore**          | Autore della pubblicazione dell'app.                                            |
| **Sistema operativo**   | Sistema operativo dell'app (Windows, iOS, Android e così via). |
| **Creato**             | Data e ora di creazione della revisione.                         |
| **Assegnato**           | Indica se l'app è stata assegnata (**Sì** o **No**).                  |

### <a name="device-and-user-status-graphs"></a>Grafici dello stato utente e dispositivo
I grafici visualizzano il numero di app per gli stati seguenti:

| **Stato del dispositivo**       | **Descrizione**                                       |
|-----------------------|-------------------------------------------------------|
| **Installato**         | Numero di app installate.                         |
| **Non installato**     | Numero di app non installate.                     |
| **Operazione non riuscita**            | Numero di installazioni non riuscite.                   |
| **L'installazione è in sospeso**   | Numero di app in corso d'installazione. |
| **Non applicabile**           | Numero di app per cui lo stato non è applicabile.            |

> [!NOTE]
> Il numero di app individuate potrebbe non corrispondere al conteggio degli stati di installazione delle app. Le possibilità delle incoerenze includono:
>    - Una modifica di destinazione di un'app gestita installata può far sì che il conteggio delle installazioni nel pannello di stato diminuisca, mentre rimane segnalato nelle app individuate.
>    - Più istanze di destinazione della stessa app in un tenant comporterà conteggi diversi a causa della potenziale sovrapposizione di utenti o dispositivi. Ogni istanza dell'app includerà nel conteggio utenti sovrapposti, mentre le app individuate avranno conteggi duplicati.
>    - Le app individuate e lo stato delle app vengono raccolti con intervalli di tempo diversi causando una discrepanza nei conteggi delle app.
> 
> Tenere anche presente che le app per Android distribuite come **Disponibile con o senza registrazione** segnalano solo lo stato di installazione delle app per i dispositivi registrati. Lo stato di installazione delle app non è disponibile per i dispositivi non registrati in Intune.

### <a name="device-install-status"></a>Stato dell'installazione del dispositivo

Quando si seleziona **Stato dell'installazione del dispositivo** nella sezione **Monitoraggio** del menu, viene visualizzato un elenco degli stati del dispositivo. La tabella dei dettagli include le colonne seguenti:

| **Colonna dispositivo**      | **Descrizione**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nome dispositivo**      | Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non è disponibile per altri dispositivi.                                                                       |
| **Nome utente**        | Nome dell'utente.                                                                                                                                                                                                                                      |
| **Piattaforma**         | Sistema operativo del dispositivo (Windows, iOS, Android e così via).                                                                                                                                                                                           |
| **Versione**          | Numero di versione dell'app. Per le app line-of-business, viene visualizzato il numero di versione completo dell'app. Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800). |
| **Stato**           | Stato dell'app.                                                                                                                                                                                                                                     |
| **Dettagli stato**   | Dettagli dello stato.                                                                                                                                                                                                                                     |
| **Ultima archiviazione**    | Data dell'ultima sincronizzazione del dispositivo con Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Stato dell'installazione dell'utente

Quando si seleziona **Stato dell'installazione dell'utente** nella sezione **Monitoraggio** del menu, viene visualizzato un elenco degli stati dell'utente. La tabella dei dettagli include le colonne seguenti:

| **Colonna utente**     | **Descrizione**                           |
|---------------------|-------------------------------------------|
| **Nome**            | Nome dell'utente in Azure Active Directory.         |
| **Nome utente**       | Nome univoco dell'utente.              |
| **Installazioni**   | Numero di app installate dall'utente. |
| **Errori**        | Numero di installazioni di app non riuscite per l'utente.     |
| **Non installato**   | Numero di app non installate dall'utente. |


## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sull'uso dei dati di Intune, vedere [Usare il data warehouse di Intune](reports-nav-create-intune-reports.md).
- Per altre informazioni sui criteri di configurazione delle app, vedere [Criteri di configurazione delle app per Intune](app-configuration-policies-overview.md).
