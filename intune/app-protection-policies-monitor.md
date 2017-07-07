---
title: Come monitorare i criteri di protezione delle app
titleSuffix: Intune on Azure
description: Vedere quanti utenti dispongono di criteri ed eseguire il drill-down per accedere ad altri dettagli."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: de40d149818b2655a8fc3b647a7e850973814165
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-monitor-app-protection-policies"></a>Come monitorare i criteri di protezione delle app
[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**Se non ci si trova nel portale di Azure**, questo argomento spiega [come creare i criteri di protezione delle app](https://docs.microsoft.com/intune-classic/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) nella console di Intune classica.


È possibile monitorare lo stato di conformità dei criteri di gestione delle app mobili (MAM) applicati agli utenti nel pannello di protezione delle app di Intune nel [portale di Azure](https://portal.azure.com). Verranno visualizzate informazioni sugli utenti interessati dai criteri MAM, lo stato di conformità ed eventuali problemi riscontrati dagli utenti.

Lo stato di conformità può essere monitorato in tre posizioni diverse:

-   Visualizzazione di riepilogo

-   Visualizzazione dettagliata

-   Visualizzazione Rapporti

## <a name="summary-view"></a>Visualizzazione di riepilogo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Monitoraggio** > **Stato dell'utente con protezione delle app** per esaminare la visualizzazione di riepilogo:

![Riquadro Riepilogo del pannello Gestione di applicazioni mobili di Intune](./media/app-protection-user-status-summary.png)

-   **Utenti**: numero totale di utenti dell'azienda che usano le app associate ai criteri.

-   **Criteri Gestito da**: numero di utenti che hanno usato almeno una delle app nel contesto aziendale.

-   **Nessun criterio**: numero di utenti che usano le app associate ai criteri, ma non sono interessati dai criteri. È consigliabile aggiungere questi utenti ai criteri.

- **Utenti contrassegnati**: numero di utenti che riscontrano problemi. Al momento, in **Utenti contrassegnati** vengono indicati solo gli utenti con dispositivi jailbroken.


## <a name="detailed-view"></a>Visualizzazione dettagliata
Per accedere alla visualizzazione dettagliata del riepilogo, scegliere il riquadro **Stato utente**, a seconda della piattaforma del sistema operativo del dispositivo, e il riquadro **Utenti contrassegnati**.

### <a name="user-status"></a>Stato utente
È possibile eseguire la ricerca di un singolo utente e controllare il relativo stato di conformità. Il pannello **Segnalazione app** mostra le informazioni seguenti per un utente selezionato:
- Dispositivi associati all'account utente

- App con criteri MAM nel dispositivo

- Stato:

  - **Archiviazione eseguita**: il criterio è stato distribuito all'utente e l'app è stata usata almeno una volta nel contesto aziendale.

  - **Archiviazione non eseguita**: il criterio è stato distribuito all'utente, ma l'app non è stata usata nel contesto aziendale da quel momento.

>[!NOTE]
> Se per l'utente cercato non è stato distribuito il criterio MAM, verrà visualizzato un messaggio che informa che all'utente non è applicato alcun criterio MAM.

Per visualizzare i report generati per un utente, seguire questa procedura:

1.  Per selezionare un utente, scegliere il riquadro **Riepilogo**.

    ![Screenshot 3](./media/MAM-reporting-6.png)

2. Nel pannello **Segnalazione app** che viene aperto scegliere **Seleziona utente** per cercare un utente di Azure Active Directory.

    ![Opzione Selezione utente nel pannello Segnalazione app](./media/MAM-reporting-2.png)

3. Selezionare un utente nell'elenco. Verranno visualizzati i dettagli dello stato di conformità per l'utente.

### <a name="flagged-users"></a>Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del sistema operativo del dispositivo interessato e un timestamp.

## <a name="reporting-view"></a>Visualizzazione Rapporti

Sono visualizzati gli stessi rapporti della visualizzazione dettagliata e ulteriori rapporti relativi allo stato di conformità dei criteri MAM:

![Screenshot-4](./media/MAM-reporting-7.png)

-   **App protection user report** (Rapporto utente protezione app): offre le stesse informazioni del rapporto **Stato utente** descritte nella sezione precedente relativa alla visualizzazione dettagliata .

-   **App protection app report** (Rapporto app protezione app): offre due stati di protezione app diversi che gli amministratori possono selezionare prima di generare il rapporto. Lo stato può essere protetto o non protetto.

    -   User status for managed MAM activity (Protected) (Stato utente per attività MAM gestita (Protetto)): questo rapporto descrive l'attività di ogni app MAM gestita per ogni utente.

        -   Visualizza tutte le app di destinazione dei criteri MAM per ogni utente e suddivide lo stato di ogni app archiviata con i criteri MAM o di destinazione di un criterio MAM ma mai archiviata.
<br></br>
    -   User status for unmanaged MAM activity (Unprotected) (Stato utente per attività MAM non gestita (Non protetto)): questo rapporto descrive l'attività delle app abilitate per MAM attualmente non gestite per ogni utente. Questa situazione può verificarsi per i motivi seguenti:

        -   Le app sono usate da un utente o un'app che attualmente non è destinazione di un criterio MAM.

        -   Tutte le app sono archiviate, ma non ricevono alcun criterio MAM.

![Screenshot-2](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Raggruppamento tabelle

Dopo la visualizzazione dei dati del **report utente sulla protezione delle app**, è possibile aggregare i dati nel modo seguente:

- **Risultato della convalida:** i dati visualizzati sono raggruppati in base allo stato di protezione delle app con indicazione di operazione completata, errore o avviso.
- **Nome app:** i dati visualizzati sono raggruppati in base alle app (nome effettivo dell'app) con indicazione di operazione completata, errore o avviso.

## <a name="export-app-protection-activities-to-csv"></a>Esportare le attività di protezione delle app in formato CSV

È possibile esportare tutte le attività relative ai criteri di protezione delle app in un singolo file con estensione csv. Questa opzione può rivelarsi utile per analizzare tutti gli stati di protezione delle app segnalati dagli utenti.

Seguire questi passaggi per generare il report sulla protezione delle app:

1. Nel pannello Gestione di applicazioni mobili di Intune scegliere il report sulla protezione delle app.

    ![Screenshot 6](./media/app-protection-report-csv-2.png)

2. Scegliere Sì per salvare il report, quindi scegliere Salva con nome e selezionare la cartella in cui eseguire il salvataggio.

    ![Screenshot 7](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Vedere anche
[Gestire il trasferimento di dati tra app iOS](data-transfer-between-apps-manage-ios.md)

* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)
