---
title: Come monitorare i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Monitorare lo stato di conformità dei criteri di gestione delle app per dispositivi mobili in Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9b0afb7d-cd4e-4fc6-83e2-3fc0da461d02
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7efa888344b91c74672563730bbdea6c7424214b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835096"
---
# <a name="how-to-monitor-app-protection-policies"></a>Come monitorare i criteri di protezione delle app
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Monitorare lo stato di conformità dei criteri di gestione delle app mobili (MAM) applicati agli utenti nel riquadro Protezione app di Intune nel [portale di Azure](https://portal.azure.com). Vengono visualizzate informazioni sugli utenti interessati dai criteri MAM, lo stato di conformità ed eventuali problemi riscontrati dagli utenti.

Lo stato di conformità può essere monitorato in tre posizioni diverse:

-   Visualizzazione di riepilogo

-   Visualizzazione dettagliata

-   Visualizzazione Rapporti

> [!NOTE]
> Per informazioni sulla creazione di criteri di protezione delle app, vedere [Come creare e assegnare criteri di protezione delle app](app-protection-policies.md).

## <a name="summary-view"></a>Visualizzazione di riepilogo

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App client**.
4. Nel carico di lavoro **App client** scegliere **Stato protezione app** nella sezione **Monitoraggio** per esaminare la visualizzazione di riepilogo:

![Riquadro Riepilogo del riquadro Gestione di applicazioni mobili di Intune](./media/app-protection-user-status-summary.png)

-   **Utenti assegnati**: numero totale di utenti assegnati dell'azienda che usano un'app associata a un criterio in un contesto aziendale. Comprende sia gli utenti protetti e con licenza, sia gli utenti non protetti e senza licenza.
-   **Utenti contrassegnati**: numero di utenti che riscontrano problemi. Gli utenti con dispositivi jailbroken vengono indicati in **Utenti contrassegnati**.
-   **Stato utente per iOS** e **Stato utente per Android**: numero di utenti che hanno usato un'app e ai quali è associato un criterio in un contesto aziendale per la relativa piattaforma. Questa informazione mostra il numero di utenti gestiti dal criterio e il numero di utenti che usano un'app non associata ad alcun criterio in un contesto aziendale. È consigliabile aggiungere questi utenti ai criteri.

    > [!NOTE]
    > Se esistono più criteri per ogni piattaforma, un utente viene considerato gestito da criteri quando ha almeno un criterio assegnato.

## <a name="detailed-view"></a>Visualizzazione dettagliata
Per accedere alla visualizzazione dettagliata del riepilogo, scegliere il riquadro **Stato utente**, a seconda della piattaforma del sistema operativo del dispositivo, e il riquadro **Utenti contrassegnati**.

### <a name="user-status"></a>Stato utente
È possibile eseguire la ricerca di un singolo utente e controllare il relativo stato di conformità. Il riquadro **Segnalazione app** visualizza le informazioni seguenti per un utente selezionato:
- Dispositivi associati all'account utente

- App con criteri MAM nel dispositivo

- Stato:

  - **Archiviazione eseguita**: i criteri sono stati distribuiti all'utente e l'app è stata usata almeno una volta nel contesto aziendale.

  - **Archiviazione non eseguita**: i criteri sono stati distribuiti all'utente, ma l'app non è stata usata nel contesto aziendale da quel momento.

>[!NOTE]
> Se per l'utente cercato non è stato distribuito il criterio MAM, verrà visualizzato un messaggio che informa che all'utente non è applicato alcun criterio MAM.

Per visualizzare i report generati per un utente, seguire questa procedura:

1.  Per selezionare un utente, scegliere il riquadro di riepilogo **Stato utente**.

    ![Schermata del riquadro Riepilogo della funzionalità di gestione di applicazioni mobili di Intune](./media/MAM-reporting-6.png)

2. Nel riquadro **Segnalazione app** che viene aperto scegliere **Selezionare l'utente** per cercare un utente di Azure Active Directory.

    ![Schermata dell'opzione Selezionare l'utente nel riquadro Segnalazione app](./media/MAM-reporting-2.png)

3. Selezionare un utente nell'elenco. È possibile visualizzare i dettagli dello stato di conformità per l'utente.

### <a name="flagged-users"></a>Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del sistema operativo del dispositivo interessato e un timestamp.

## <a name="reporting-view"></a>Visualizzazione Rapporti

Sono visualizzati gli stessi report del pannello **Stato protezione app**.

> [!NOTE]
> Intune offre campi aggiuntivi per i report relativi ai dispositivi, tra cui ID di registrazione app, produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. In Intune questi campi sono disponibili selezionando **App client** > **Stato protezione app** e scegliendo **Report sulla protezione dell'app: iOS, Android**. Inoltre, questi parametri consentiranno di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della versione minima della patch di sicurezza Android. 

Sono disponibili altri report relativi allo stato di conformità dei criteri MAM. Per visualizzare questi report, selezionare **App client** > **Stato protezione app** > **Report**. 

Il pannello **Report** fornisce diversi report in base all'utente e all'app, tra cui:


-   **Report utenti**: Questo report offre le stesse informazioni del report **Stato utente** descritte nella sezione precedente relativa alla visualizzazione dettagliata.

-   **Report app**: Questo report offre due stati di protezione dell'app diversi tra cui gli amministratori possono scegliere prima di generare il report. Lo stato può essere protetto o non protetto.

    -   Stato utente per attività MAM gestita (Protetta): questo report descrive l'attività di ogni app MAM gestita per ogni utente.

        -   Visualizza tutte le app di destinazione dei criteri MAM per ogni utente e suddivide lo stato di ogni app archiviata con i criteri MAM o di destinazione di un criterio MAM ma mai archiviata.
<br><br>
    -   Stato utente per attività MAM non gestita (Non protetta): questo report descrive l'attività delle app abilitate per MAM attualmente non gestite per ogni utente. Questa situazione può verificarsi per i motivi seguenti:

        -   Le app sono usate da un utente o un'app che attualmente non è destinazione di un criterio MAM.

        -   Tutte le app sono archiviate, ma non ricevono alcun criterio MAM.

![Screenshot del pannello Segnalazione app di un utente con i dettagli di tre app](./media/MAM-reporting-4.png)

## <a name="table-grouping"></a>Raggruppamento tabelle

Dopo la visualizzazione dei dati del **report utente sulla protezione delle app**, è possibile aggregare i dati nel modo seguente:

- **Risultato convalida:** i dati visualizzati sono raggruppati in base allo stato di protezione dell'app, che può corrispondere a operazione completata, errore o avviso.
- **Nome app:** i dati visualizzati sono raggruppati in base all'app (identificata dal nome effettivo) con indicazione dello stato, che può corrispondere a operazione completata, errore o avviso.

## <a name="export-app-protection-activities-to-csv"></a>Esportare le attività di protezione delle app in formato CSV

È possibile esportare tutte le attività relative ai criteri di protezione delle app in un singolo file con estensione csv. Questa opzione può rivelarsi utile per analizzare tutti gli stati di protezione delle app segnalati dagli utenti.

Seguire questi passaggi per generare il report sulla protezione delle app:

1. Nel pannello Gestione di applicazioni mobili di Intune scegliere **Report protezione app**.

    ![Screenshot del collegamento per il download di Protezione app](./media/app-protection-report-csv-2.png)

2. Scegliere Sì per salvare il report, quindi scegliere Salva con nome e selezionare la cartella in cui eseguire il salvataggio.

    ![Schermata della finestra di conferma Salva report](./media/app-protection-report-csv-1.png)

## <a name="see-also"></a>Vedere anche
[Gestire il trasferimento di dati tra app iOS](data-transfer-between-apps-manage-ios.md)

* [Aspettative dalla gestione dell'app per Android con criteri di protezione delle app](app-protection-enabled-apps-android.md)
* [Aspettative dalla gestione dell'app per iOS con criteri di protezione delle app](app-protection-enabled-apps-ios.md)
