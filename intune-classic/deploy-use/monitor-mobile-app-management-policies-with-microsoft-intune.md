---
title: Monitorare i criteri MAM con Microsoft Intune
description: Vedere quanti utenti dispongono di criteri ed eseguire il drill-down per accedere ad altri dettagli.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: de26b7614578b275802ca048ed17bfa5969f0387
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021519"
---
# <a name="monitor-app-protection-policies-with-microsoft-intune"></a>Monitorare i criteri di protezione delle app con Microsoft Intune
È possibile monitorare lo stato di conformità dei criteri di protezione delle app applicati agli utenti. Sono disponibili informazioni sugli utenti interessati dai criteri di protezione delle app, sullo stato di conformità e su eventuali problemi riscontrati dagli utenti.

Lo stato di conformità può essere monitorato in tre posizioni diverse:

-   Visualizzazione di riepilogo

-   Visualizzazione dettagliata

-   Visualizzazione Rapporti

## <a name="summary-view"></a>Visualizzazione di riepilogo

Seguire i tre passaggi seguenti per aprire la visualizzazione di riepilogo:

1. Passare al [portale di Azure](https://portal.azure.com) e immettere le proprie credenziali.
2. Scegliere **Altri servizi** e digitare **Intune** nella casella di testo filtro.
3. Scegliere **Protezione app di Intune**.

Nel pannello di **gestione di applicazioni mobili Intune** è disponibile un riepilogo dello stato di conformità:

![Riquadro Riepilogo del pannello Gestione di applicazioni mobili di Intune](../media/mam-azure-portal-user-status-summary.png)

-   **Utenti**: numero totale di utenti dell'azienda che usano un'app associata a un criterio in un contesto aziendale.

-   **Criteri Gestito da**: numero di utenti che hanno usato un'app e ai quali è associato un criterio in un contesto aziendale.

-   **Nessun criterio**: numero di utenti che usano un'app non associata ad alcun criterio in un contesto aziendale. È consigliabile aggiungere questi utenti ai criteri.
    > [!NOTE]
    > Se esistono più criteri per ogni piattaforma, un utente viene considerato gestito da criteri quando ha almeno un criterio assegnato.

- **Utenti contrassegnati**: numero di utenti che riscontrano problemi. Al momento, in **Utenti contrassegnati** vengono indicati solo gli utenti con dispositivi jailbroken.


## <a name="detailed-view"></a>Visualizzazione dettagliata
Per accedere alla visualizzazione dettagliata del riepilogo, scegliere il riquadro **Stato utente**, a seconda della piattaforma del sistema operativo del dispositivo, e il riquadro **Utenti contrassegnati**.

### <a name="user-status"></a>Stato utente
È possibile eseguire la ricerca di un singolo utente e controllare il relativo stato di conformità. Il pannello **Segnalazione app** mostra le informazioni seguenti per un utente selezionato:
- Dispositivi associati all'account utente

- Applicazioni con un criterio di protezione delle app sul dispositivo

- Stato:

  - **Archiviazione eseguita**: il criterio è stato distribuito all'utente e l'app è stata usata almeno una volta nel contesto aziendale.

  - **Archiviazione non eseguita**: il criterio è stato distribuito all'utente, ma l'app non è stata usata nel contesto aziendale da quel momento.

>[!NOTE]
> Se il criterio di protezione delle app non è stato distribuito agli utenti cercati, un messaggio informa che a tali utenti non è assegnato alcun criterio di protezione delle app.

Per visualizzare i report generati per un utente, seguire questa procedura:

1.  Per selezionare un utente, scegliere il riquadro **Riepilogo**.

    ![Screenshot 3](../media/MAM-reporting-6.png)

2. Nel pannello **Segnalazione app** che viene aperto scegliere **Seleziona utente** per cercare un utente di Azure Active Directory.

    ![Opzione Selezione utente nel pannello Segnalazione app](../media/MAM-reporting-2.png)

3. Selezionare un utente nell'elenco. Verranno visualizzati i dettagli dello stato di conformità per l'utente.

### <a name="flagged-users"></a>Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del sistema operativo del dispositivo interessato e un timestamp.

## <a name="reporting-view"></a>Visualizzazione Rapporti

Sono visualizzati gli stessi rapporti della visualizzazione dettagliata e altri rapporti relativi allo stato di conformità dell'app con criteri di protezione delle app:

![Screenshot-4](../media/MAM-reporting-7.png)

-   **App protection user report** (Rapporto utente protezione app): offre le stesse informazioni del rapporto **Stato utente** descritte nella sezione precedente relativa alla visualizzazione dettagliata .

-   **App protection app report** (Rapporto app protezione app): offre due stati di protezione app diversi che gli amministratori possono selezionare prima di generare il rapporto. Lo stato può essere protetto o non protetto.

    -   User status for managed MAM activity (Protected) (Stato utente per attività MAM gestita (Protetto)): questo rapporto descrive l'attività di ogni app MAM gestita per ogni utente.

        -   Visualizza tutte le app di ciascun utente alle quali sono assegnati criteri di protezione e indica lo stato di ogni app, distinguendo tra app archiviate con criteri di protezione e app con criteri di protezione assegnati, ma non archiviate con tali criteri.
<br></br>
    -   User status for unmanaged MAM activity (Unprotected) (Stato utente per attività MAM non gestita (Non protetto)): questo rapporto descrive l'attività delle app abilitate per MAM attualmente non gestite per ogni utente. Questa situazione può verificarsi per i motivi seguenti:

        -   Le app sono usate da un utente o un'app a cui non è assegnato un criterio di protezione delle app.

        -   Tutte le app sono archiviate, ma non ricevono alcun criterio di protezione.

![Screenshot-2](../media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Raggruppamento tabelle

Dopo la visualizzazione dei dati del **report utente sulla protezione delle app**, è possibile aggregare i dati nel modo seguente:

- **Risultato della convalida:** i dati visualizzati sono raggruppati in base allo stato di protezione delle app con indicazione di operazione completata, errore o avviso.
- **Nome app:** i dati visualizzati sono raggruppati in base alle app (nome effettivo dell'app) con indicazione di operazione completata, errore o avviso.

## <a name="export-app-protection-activities-to-csv"></a>Esportare le attività di protezione delle app in formato CSV

È possibile esportare tutte le attività relative ai criteri di protezione delle app in un singolo file con estensione csv. Questa opzione può rivelarsi utile per analizzare tutti gli stati di protezione delle app segnalati dagli utenti.

Seguire questi passaggi per generare il report sulla protezione delle app:

1. Nel pannello Gestione di applicazioni mobili di Intune scegliere il report sulla protezione delle app.

    ![Screenshot 6](../media/app-protection-report-csv-2.png)

2. Scegliere Sì per salvare il report, quindi scegliere Salva con nome e selezionare la cartella in cui eseguire il salvataggio.

    ![Screenshot 7](../media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Vedere anche
[Gestire il trasferimento di dati tra app iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](/intune/end-user-mam-apps-android)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](/intune/end-user-mam-apps-ios)
