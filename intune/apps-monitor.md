---
title: Come monitorare le informazioni sulle app e le assegnazioni
titlesuffix: Microsoft Intune
description: Dopo avere assegnato un'app agli utenti o ai dispositivi, usare queste informazioni per monitorarne lo stato.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d1ca013b7000282316a17e02dcb38b3d4f27958
ms.sourcegitcommit: 820f950d1fc80b1eb5db1b0cf77f44d92a969951
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Come monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune offre alcuni metodi per monitorare le proprietà delle app gestite, nonché il rispettivo stato di assegnazione.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nel gruppo **Monitoraggio e gestione**.
3. Nel pannello **App per dispositivi mobili** scegliere **App** nel gruppo **Gestisci**.
5. Selezionare l'app che si vuole monitorare dall'elenco delle app. Viene visualizzato il pannello delle app con informazioni sullo stato del dispositivo e lo stato dell'utente.

## <a name="app-overview-blade"></a>Pannello di panoramica delle app

È possibile usare il pannello dell'app specifica per esaminare i dettagli relativi allo stato di un'app nell'ambiente in uso.

### <a name="essentials"></a>Essentials
La sezione **Informazioni di base** contiene le seguenti informazioni sull'app:

 | **Dettagli dell'app**            | **Descrizione**                                                      |
|------------------------|------------------------------------------------------------------|
| **Autore**          | Autore della pubblicazione dell'app.                                            |
| **Sistema operativo**   | Sistema operativo dell'app (Windows, iOS, Android, ecc.) |
| **Creato**             | Data e ora di creazione della revisione.                         |
| **Assegnato**           | **Sì** o **No** a seconda che l'app sia stata assegnata o meno.                  |

### <a name="device-and-user-status-graphs"></a>Grafici dello stato utente e dispositivo
I grafici visualizzano il numero per gli stati seguenti:

| **Stato dispositivo**       | **Descrizione**                                       |
|-----------------------|-------------------------------------------------------|
| **Installato**         | Numero di app installate.                         |
| **Non installato**     | Numero di app non installate.                     |
| **Operazione non riuscita**            | Numero di installazioni non riuscite.                   |
| **L'installazione è in sospeso**   | Numero di app in corso d'installazione. |
| **Non applicabile**           | Numero di app in cui lo stato non è applicabile.            |

### <a name="device-install-status"></a>Stato dell'installazione del dispositivo

Quando si seleziona **Stato dell'installazione del dispositivo** nella sezione **Monitoraggio** viene visualizzato un elenco degli stati di dispositivo. La tabella dei dettagli include le colonne seguenti:

| **Colonna dispositivo**      | **Descrizione**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nome dispositivo**      | Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Nelle altre piattaforme Intune crea un nome in base ad altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi.                                                                       |
| **Nome utente**        | Nome dell'utente.                                                                                                                                                                                                                                      |
| **Piattaforma**         | Sistema operativo del dispositivo (Windows, iOS, Android, ecc.)                                                                                                                                                                                           |
| **Versione**          | Numero di versione dell'app. Per le app line-of-business, viene visualizzato il numero di versione completo dell'app. Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800) |
| **Stato**           | Stato dell'app.                                                                                                                                                                                                                                     |
| **Dettagli stato**   | Dettagli dello stato.                                                                                                                                                                                                                                     |
| **Ultima archiviazione**    | Data dell'ultima sincronizzazione del dispositivo con Intune.                                                                                                                                                                                                                  |


### <a name="user-install-status"></a>Stato dell'installazione dell'utente

Quando si seleziona **Stato dell'installazione dell'utente** nella sezione **Monitoraggio** viene visualizzato un elenco degli stati utente. La tabella dei dettagli include le colonne seguenti:

| **Colonna utente**     | **Descrizione**                           |
|---------------------|-------------------------------------------|
| **Nome**            | Nome dell'utente in Azure AD.         |
| **Nome utente**       | Nome univoco dell'utente.              |
| **Installazioni**   | Numero di installazioni di app usato dall'utente. |
| **Errori**        | Numero di installazioni non riuscite eseguite dall'utente.     |
| **Non installato**   | Numero di app non installate dall'utente. |


## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sull'uso dei dati di Intune, vedere [Usare il data warehouse di Intune](reports-nav-create-intune-reports.md).
- Per altre informazioni sui criteri di configurazione delle app, vedere [Criteri di configurazione delle app per Intune](app-configuration-policies-overview.md).