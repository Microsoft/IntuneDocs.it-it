---
title: Monitorare le informazioni sulle app e le assegnazioni
titleSuffix: Microsoft Intune
description: Dopo avere assegnato un'app agli utenti o ai dispositivi, usare queste informazioni per monitorare lo stato dell'app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee22ee435830137a423423aa692376aabbb6cecb
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585424"
---
# <a name="monitor-app-information-and-assignments-with-microsoft-intune"></a>Monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune offre diversi modi per monitorare le proprietà delle app gestite e per gestire lo stato di assegnazione delle app.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client**.
4. Nella sezione **Gestisci** del menu selezionare **App**.
5. Nell'elenco di app selezionare un'app da monitorare. Verrà quindi visualizzato il riquadro delle app, che include una panoramica dello stato del dispositivo e dello stato dell'utente.

> [!NOTE]
> Le app di Android Store distribuite come **disponibili** non segnalano lo stato dell'installazione.
>
> Per le app Google Play gestite distribuite nei dispositivi del profilo di lavoro Android Enterprise, è possibile visualizzare lo stato e il numero di versione dell'app installata in un dispositivo con Intune. 

## <a name="app-overview-pane"></a>Riquadro di panoramica delle app

Nel riquadro delle app è possibile esaminare i dettagli relativi allo stato di un'app nell'ambiente in uso.

### <a name="essentials"></a>Essentials
La sezione **Informazioni di base** contiene le seguenti informazioni sull'app:

 | **Dettagli dell'app**            | **Descrizione**                                                      |
|------------------------|------------------------------------------------------------------|
| **Autore**          | Autore della pubblicazione dell'app.                                            |
| **Sistema operativo**   | Sistema operativo dell'app (Windows, iOS, Android e così via). |
| **Creato**             | Data e ora di creazione della revisione. <b>**Nota**: questo valore di data viene aggiornato quando un amministratore IT modifica i metadati dell'app, ad esempio cambiando la categoria o la descrizione dell'app.                        |
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
> Tenere presente che le app line-of-business per Android (APK) distribuite come **Disponibile con o senza registrazione** segnalano solo lo stato di installazione delle app per i dispositivi registrati. Lo stato di installazione delle app non è disponibile per i dispositivi non registrati in Intune.

### <a name="device-install-status"></a>Stato dell'installazione del dispositivo

Quando si seleziona **Stato dell'installazione del dispositivo** nella sezione **Monitoraggio** del menu, viene visualizzato un elenco degli stati del dispositivo. La tabella dei dettagli include le colonne seguenti:

| **Colonna dispositivo**      | **Descrizione**                                                                                                                                                                                                                                            |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Nome dispositivo**      | Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non è disponibile per altri dispositivi.                                                                       |
| **Nome utente**        | Nome dell'utente.                                                                                                                                                                                                                                      |
| **Piattaforma**         | Sistema operativo del dispositivo (Windows, iOS, Android e così via).                                                                                                                                                                                           |
| **Versione**          | Numero di versione dell'app. Per le app line-of-business e le app di Microsoft Store per le aziende viene visualizzato il numero di versione completo dell'app. Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800). Per le app dello Store standard la versione non viene visualizzata. |
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

- Per altre informazioni sull'uso dei dati di Intune, vedere [Usare il data warehouse di Intune](../reports-nav-create-intune-reports.md).
- Per altre informazioni sui criteri di configurazione delle app, vedere [Criteri di configurazione delle app per Intune](app-configuration-policies-overview.md).
