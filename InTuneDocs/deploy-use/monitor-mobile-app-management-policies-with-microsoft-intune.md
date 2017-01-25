---
title: Monitorare i criteri MAM con Microsoft Intune | Documentazione Microsoft
description: Vedere quanti utenti dispongono di criteri ed eseguire il drill-down per accedere ad altri dettagli.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fe44466fbcef67d02b16d3d2d335f657251451d3
ms.openlocfilehash: e60d707833ee276971000411e50564f39b41b207


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune
È possibile monitorare lo stato di conformità dei criteri di gestione delle app mobili (MAM) applicati agli utenti nel pannello di protezione delle app di Intune nel [portale di Azure](https://portal.azure.com). Verranno visualizzate informazioni sugli utenti interessati dai criteri MAM, lo stato di conformità ed eventuali problemi riscontrati dagli utenti.

Lo stato di conformità può essere monitorato in tre posizioni diverse:

-   Visualizzazione di riepilogo

-   Visualizzazione dettagliata

-   Visualizzazione Rapporti

## <a name="summary-view"></a>Visualizzazione di riepilogo

Seguire i tre passaggi seguenti per aprire la visualizzazione di riepilogo:

1. Passare al [portale di Azure](https://portal.azure.com) e immettere le proprie credenziali.
2. Scegliere **Altri servizi** e digitare "Intune".
3. Scegliere **Intune App Protection** (Protezione app Intune).

Nel pannello di **gestione di applicazioni mobili Intune** è disponibile un riepilogo dello stato di conformità:

![Riquadro Riepilogo del pannello Gestione di applicazioni mobili di Intune](../media/mam-azure-portal-user-status-summary.png)

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

    ![Screenshot 3](../media/MAM-reporting-6.png)

2. Nel pannello **Segnalazione app** che viene aperto scegliere **Seleziona utente** per cercare un utente di Azure Active Directory.

    ![Opzione Selezione utente nel pannello Segnalazione app](../media/MAM-reporting-2.png)

3. Selezionare un utente nell'elenco. Verranno visualizzati i dettagli dello stato di conformità per l'utente.

### <a name="flagged-users"></a>Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del sistema operativo del dispositivo interessato e un timestamp.

## <a name="reporting-view"></a>Visualizzazione Rapporti

Sono visualizzati gli stessi rapporti della visualizzazione dettagliata e ulteriori rapporti relativi allo stato di conformità dei criteri MAM:

![Screenshot-4](../media/MAM-reporting-7.png)

-   **App protection user report** (Rapporto utente protezione app): offre le stesse informazioni del rapporto **Stato utente** descritte nella sezione precedente relativa alla visualizzazione dettagliata .

-   **App protection app report** (Rapporto app protezione app): offre due stati di protezione app diversi che gli amministratori possono selezionare prima di generare il rapporto. Lo stato può essere protetto o non protetto.

    ![Screenshot-1](../media/MAM-reporting-1.png)

    -   User status for managed MAM activity (Protected) (Stato utente per attività MAM gestita (Protetto)): questo rapporto descrive l'attività di ogni app MAM gestita per ogni utente.

        -   Visualizza tutte le app di destinazione dei criteri MAM per ogni utente e suddivide lo stato di ogni app archiviata con i criteri MAM o di destinazione di un criterio MAM ma mai archiviata.
<br></br>
    -   User status for unmanaged MAM activity (Unprotected) (Stato utente per attività MAM non gestita (Non protetto)): questo rapporto descrive l'attività delle app abilitate per MAM attualmente non gestite per ogni utente. Questa situazione può verificarsi per i motivi seguenti:

        -   Le app sono usate da un utente o un'app che attualmente non è destinazione di un criterio MAM.

        -   Tutte le app sono archiviate, ma non ricevono alcun criterio MAM.

![Screenshot-2](../media/MAM-reporting-4.png)

## <a name="see-also"></a>Vedere anche
[Gestire il trasferimento di dati tra app iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Aspettative dalla gestione dell'app per Android con criteri MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Aspettative dalla gestione dell'app per iOS con criteri MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Jan17_HO2-->


