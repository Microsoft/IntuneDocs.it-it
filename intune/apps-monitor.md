---
title: Come monitorare le informazioni sulle app e le assegnazioni
titlesuffix: Microsoft Intune
description: Dopo avere assegnato un'app agli utenti o ai dispositivi, usare queste informazioni per monitorarne lo stato.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b88530ef790dd181e81e420c158867d29d1d0d58
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Come monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune offre alcuni metodi per monitorare le proprietà delle app gestite, nonché il rispettivo stato di assegnazione.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel pannello **App per dispositivi mobili** scegliere **App** nel gruppo **Gestisci**.
5. Nel pannello con l'elenco di app scegliere un'app. Verrà visualizzato il pannello <*nome app*> **Stato dell'installazione del dispositivo**.

## <a name="app-overview-blade"></a>Pannello di panoramica delle app

È possibile usare il pannello <*nome app*> **Stato dell'installazione del dispositivo** per esaminare i dettagli relativi allo stato di un'app nel proprio ambiente.

### <a name="essentials"></a>Essentials

La sezione **Informazioni di base** contiene le seguenti informazioni sull'app:

 - **Autore**  
Autore della pubblicazione dell'app.
 - **Sistema operativo**  
Sistema operativo dell'app (Windows, iOS, Android, ecc.)
 - **Crea**  
Ora di creazione della revisione.
 - **Assegnato**  
**Sì** o **No** a seconda che l'app sia stata assegnata o meno.

### <a name="status"></a>Stato
Ogni grafico mostra i conteggi per gli stati seguenti:

 - **Installato**  
Numero di app installate.
 - **Non installato**  
Numero di app non installate.
 - **L'installazione è in sospeso**  
Numero di app in corso d'installazione.
 - **Operazione non riuscita**  
Numero di installazioni non riuscite.
 - **Sconosciuto**  
Numero di app con stato sconosciuto.

### <a name="device-status"></a>Stato dispositivo

Stato del dispositivo. Grafico ad anello che visualizza lo stato di installazione dell'app nei dispositivi. Fare clic sul grafico per aprire un elenco dei dettagli relativi allo stato del dispositivo. La tabella dei dettagli include le colonne seguenti:

 - **Nome dispositivo**  
Nome del dispositivo su piattaforme che consentono la denominazione di un dispositivo. Su altre piattaforme, Intune crea un nome da altre proprietà. Questo attributo non può essere disponibile per tutti i dispositivi.
 - **Nome utente**  
Nome dell'utente.
 - **Piattaforma**  
Sistema operativo del dispositivo (Windows, iOS, Android, ecc.)
 - **Versione**  
Numero di versione dell'app. Per le app line-of-business, viene visualizzato il numero di versione completo dell'app. Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800)
 - **Stato**  
Stato dell'app.
 - **Dettagli stato**  
Dettagli dello stato.
 - **Ultima archiviazione**  
Data dell'ultima sincronizzazione del dispositivo con Intune.


### <a name="user-status"></a>Stato utente

Stato dell'utente. Grafico ad anello che visualizza lo stato di installazione dell'app per gli utenti. Fare clic sul grafico per aprire un elenco dei dettagli relativi allo stato del dispositivo. La tabella dei dettagli include le colonne seguenti:
 - **Nome**  
Nome dell'utente in Azure AD.
 - **Nome utente**  
Nome univoco dell'utente.
 - **Installazioni**  
Numero di installazioni di app usato dall'utente.
 - **Errori**  
Numero di installazioni non riuscite eseguite dall'utente.
 - **Non installato**  
Numero di app non installate dall'utente.


## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sull'uso dei dati di Intune, vedere [Usare il data warehouse di Intune](reports-nav-create-intune-reports.md).
