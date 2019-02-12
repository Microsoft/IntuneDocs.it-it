---
title: Instradare i log di controllo in Monitoraggio di Azure usando Microsoft Intune - Azure | Microsoft Docs
description: Usare le impostazioni di diagnostica per inviare log di controllo e log operativi in Microsoft Intune all'account di archiviazione di Azure, agli hub eventi o a Log Analytics. Scegliere per quanto tempo si vogliono conservare i dati e verificare i costi stimati per tenant di dimensioni diverse.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f4f93ab1cd2c662cb97dafd19684b353268087f6
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842576"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics in Intune (anteprima)

Microsoft Intune include log predefiniti che forniscono informazioni sull'ambiente. I **log di controllo** mostrano i dettagli su diversi eventi o attività che si verificano in Intune. I **log operativi (anteprima)** mostrano i dettagli su utenti e dispositivi che hanno eseguito (o non sono riusciti a eseguire) la registrazione.

Questi log possono anche essere inviati ai servizi di monitoraggio di Azure, inclusi account di archiviazione, hub eventi e Log Analytics. In particolare, è possibile:

* Archiviare i log di Intune in un account di archiviazione di Azure per conservare i dati o archiviarli per un determinato periodo.
* Trasmettere i log di Intune a un hub eventi di Azure per l'analisi usando diffusi strumenti di informazioni di sicurezza e gestione degli eventi, ad esempio Splunk e QRadar.
* Integrare i log di Intune con le soluzioni di log personalizzate trasmettendoli a un hub eventi.
* Inviare i log di Intune a Log Analytics per abilitare visualizzazioni avanzate, monitoraggio e avvisi sui dati connessi.

Queste funzionalità fanno parte delle **impostazioni di diagnostica** in Intune. 

Questo articolo illustra come usare le **impostazioni di diagnostica** per inviare i dati dei log a servizi diversi, fornisce esempi e stime dei costi e risponde ad alcune domande comuni.

## <a name="prerequisites"></a>Prerequisiti

Per usare questa funzionalità, sono necessari:

* Una sottoscrizione di Azure: se non si ha una sottoscrizione di Azure, è possibile [iscriversi per una versione di valutazione gratuita](https://azure.microsoft.com/free/).
* Ambiente (tenant) di Microsoft Intune in Azure
* Un utente che sia **amministratore globale** o **amministratore del servizio Intune** per il tenant di Intune.

A seconda della destinazione scelta per instradare i dati dei log di controllo, è necessario uno dei servizi seguenti:

* Un [account di archiviazione di Azure](https://docs.microsoft.com/azure/storage/common/storage-account-overview) con autorizzazioni *ListKeys*. È consigliabile usare un account di archiviazione generale e non un account di archiviazione BLOB. Per informazioni sui prezzi di archiviazione, vedere il [calcolatore dei prezzi di Archiviazione di Azure](https://azure.microsoft.com/pricing/calculator/?service=storage). 
* Uno [spazio dei nomi di Hub eventi di Azure](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace) per l'integrazione con le soluzioni di terze parti.
* Un'[area di lavoro di Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) per inviare i log a Log Analytics.

## <a name="send-logs-to-azure-monitor"></a>Inviare i log a Monitoraggio di Azure

1. Nel [portale di Azure](https://portal.azure.com/) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. In **Monitoraggio** selezionare **Impostazioni di diagnostica**. La prima volta che si apre la diagnostica, attivarla:

    ![Attivare Impostazioni di diagnostica in Intune per inviare i log a Monitoraggio di Azure](media/diagnostics-settings-turn-on.png)

3. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome per le impostazioni di diagnostica. Questa impostazione include tutte le proprietà immesse. Immettere ad esempio `Route audit logs to storage account`.
    - **Archivia in un account di archiviazione**: salva i dati dei log in un account di archiviazione di Azure. Usare questa opzione se si vogliono salvare o archiviare i dati.

        1. Selezionare questa opzione > **Configura**. 
        2. Scegliere un account di archiviazione esistente dall'elenco > **OK**.

    - **Streaming in un hub eventi**: trasmette i log a un hub eventi di Azure. Per analizzare i dati dei log usando strumenti di informazioni di sicurezza e gestione degli eventi, ad esempio QRadar e Splunk, scegliere questa opzione.

        1. Selezionare questa opzione > **Configura**. 
        2. Scegliere un criterio e uno spazio dei nomi dell'hub eventi esistenti dall'elenco > **OK**.

    - **Invia a Log Analytics**: invia i dati ad Azure Log Analytics. Per usare visualizzazioni, monitoraggio e avvisi per i log, scegliere questa opzione.

        1. Selezionare questa opzione > **Configura**. 
        2. Creare una nuova area di lavoro e immettere i dettagli dell'area di lavoro oppure scegliere un'area di lavoro esistente dall'elenco > **OK**.

            L'[area di lavoro di Azure Log Analytics](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace) fornisce altri dettagli su queste impostazioni.

    - **LOG** > **AuditLogs**: scegliere questa opzione per inviare i [log di controllo di Intune](monitor-audit-logs.md) all'account di archiviazione, all'hub eventi o a Log Analytics. I log di controllo mostrano la cronologia di ogni attività che genera una modifica in Intune, inclusi chi l'ha eseguita e quando.

      Se si sceglie di usare un account di archiviazione, immettere anche il numero di giorni per cui si vogliono mantenere i dati (conservazione). Per mantenere i dati per sempre, impostare **Conservazione (giorni)** su `0` (zero).

    - **LOG** > **OperationalLogs**: I log operativi (anteprima) mostrano l'esito positivo o negativo di utenti e dispositivi che eseguono la registrazione in Intune. Scegliere questa opzione per inviare i log di registrazione di Intune all'account di archiviazione, all'hub eventi o a Log Analytics.

      Se si sceglie di usare un account di archiviazione, immettere anche il numero di giorni per cui si vogliono mantenere i dati (conservazione). Per mantenere i dati per sempre, impostare **Conservazione (giorni)** su `0` (zero).

      > [!NOTE]
      > I log operativi sono in anteprima. Per fornire commenti e suggerimenti, tra cui le informazioni incluse nei log operativi, passare a [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback). Il collegamento apre un nuovo sito Web.

    Al termine, le impostazioni saranno simili alle seguenti: 

    ![Immagine di esempio che mostra l'invio dei log di controllo di Intune a un account di archiviazione di Azure](media/diagnostics-settings-example.png)

4. **Salvare** le modifiche. L'impostazione viene visualizzata nell'elenco. Dopo aver creato le impostazioni, è possibile modificarle selezionando **Modifica l'impostazione** > **Salva**.

## <a name="cost-considerations"></a>Considerazioni sui costi

Se si ha già una licenza di Microsoft Intune, è necessaria una sottoscrizione di Azure per configurare l'account di archiviazione e l'hub eventi. La sottoscrizione di Azure è in genere gratuita, ma si paga per usare le risorse di Azure, inclusi l'account di archiviazione per l'archiviazione e l'hub eventi per lo streaming. La quantità di dati e i costi variano a seconda delle dimensioni del tenant.

### <a name="storage-size-for-activity-logs"></a>Dimensioni di archiviazione per i log attività

Ogni evento di un log di controllo usa circa 2 KB di spazio di archiviazione dati. Per un tenant con 100.000 utenti, potrebbero verificarsi circa 1,5 milioni di eventi al giorno. Potrebbero essere necessari circa 3 GB di spazio di archiviazione dati al giorno. Poiché in genere le operazioni di scrittura vengono eseguite in batch di cinque minuti, è possibile prevedere circa 9.000 operazioni di scrittura al mese.

Le tabelle seguenti indicano una stima dei costi che varia a seconda delle dimensioni del tenant. Includono anche un account di archiviazione per utilizzo generico v2 negli Stati Uniti occidentali per almeno un anno di conservazione dei dati. Per ottenere una stima del volume di dati previsto per i log, usare il [calcolatore dei prezzi di Archiviazione di Azure](https://azure.microsoft.com/pricing/details/storage/blobs/).

**Log di controllo con 100.000 utenti**

| | |
|---|---|
|Eventi al giorno| 1,5 milioni|
|Volume stimato di dati al mese| 90 GB|
|Costo stimato al mese (USD)| $ 1,93|
|Costo stimato all'anno (USD)| $ 23,12|

**Log di controllo con 1.000 utenti**

| | |
|---|---|
|Eventi al giorno| 15.000|
|Volume stimato di dati al mese| 900 MB|
|Costo stimato al mese (USD)| $ 0,02|
|Costo stimato all'anno (USD)| $ 0,24|

### <a name="event-hub-messages-for-activity-logs"></a>Messaggi dell'hub eventi per i log attività

Gli eventi vengono in genere raggruppati in batch ogni cinque minuti e inviati come singolo messaggio contenente tutti gli eventi verificatisi entro tale periodo di tempo. Un messaggio nell'hub eventi ha una dimensione massima di 256 KB. Se le dimensioni totali di tutti i messaggi compresi nell'intervallo di tempo superano tale volume, vengono inviati più messaggi.

In un tenant di grandi dimensioni con più di 100.000 utenti, ad esempio, si verificano in genere circa 18 eventi al secondo, pari a 5.400 eventi ogni cinque minuti (300 secondi x 18 eventi). I log di controllo sono pari a circa 2 KB per evento, ovvero 10,8 MB di dati. In tale intervallo di cinque minuti vengono quindi inviati 43 messaggi all'hub eventi.

La tabella seguente contiene i costi stimati al mese per un hub eventi di base negli Stati Uniti occidentali, a seconda del volume dei dati degli eventi. Per ottenere una stima del volume di dati previsto per i log, usare il [calcolatore dei prezzi di Hub eventi](https://azure.microsoft.com/pricing/details/event-hubs/).

**Log di controllo con 100.000 utenti**

| | |
|---|---|
|Eventi al secondo| 18|
|Eventi per ogni intervallo di cinque minuti| 5.400|
|Volume per intervallo| 10,8 MB|
|Messaggi per intervallo| 43|
|Messaggi al mese| 371.520|
|Costo stimato al mese (USD)| $ 10,83|

**Log di controllo con 1.000 utenti**

| | |
|---|---|
|Eventi al secondo|0,1 |
|Eventi per ogni intervallo di cinque minuti| 52|
|Volume per intervallo|104 KB |
|Messaggi per intervallo|1 |
|Messaggi al mese|8.640 |
|Costo stimato al mese (USD)|$ 10,80 |

### <a name="log-analytics-cost-considerations"></a>Considerazioni sui costi di Log Analytics

Per esaminare i costi relativi alla gestione dell'area di lavoro di Log Analytics, vedere [Gestire i costi controllando il volume e la conservazione dei dati in Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage).

## <a name="frequently-asked-questions"></a>Domande frequenti

Di seguito sono elencate le risposte alle domande frequenti e le informazioni sui problemi noti con i log di Intune in Monitoraggio di Azure.

#### <a name="which-logs-are-included"></a>Quali log sono inclusi?

I log di controllo e i log operativi (anteprima) sono entrambi disponibili per il routing tramite questa funzionalità.

#### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>Dopo un'azione, quando vengono visualizzati i log corrispondenti nell'hub eventi?

I log vengono in genere visualizzati nell'hub eventi entro alcuni minuti dopo l'esecuzione dell'azione. Per altre informazioni, vedere [Informazioni su Hub eventi di Azure](https://docs.microsoft.com/azure/event-hubs/).

#### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>Dopo un'azione, quando vengono visualizzati i log corrispondenti nell'account di archiviazione?

Per gli account di archiviazione di Azure, la latenza è ovunque da 5 a 15 minuti dopo l'esecuzione dell'azione.

#### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>Che cosa accade se un amministratore modifica il periodo di conservazione di un'impostazione di diagnostica?

Il nuovo criterio di conservazione viene applicato ai log raccolti dopo la modifica. I log raccolti prima della modifica del criterio non sono interessati.

#### <a name="how-much-does-it-cost-to-store-my-data"></a>Quanto costa archiviare i dati?

I costi di archiviazione dipendono dalle dimensioni dei log e dal periodo di conservazione scelto. Per un elenco dei costi stimati per i tenant, che dipendono dal volume di log generato, vedere [Dimensioni di archiviazione per i log attività](#storage-size-for-activity-logs) (in questo articolo).

#### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>Quanto costa trasmettere i dati a un hub eventi?

I costi di streaming dipendono dal numero di messaggi ricevuti al minuto. Per informazioni dettagliate su come vengono calcolati i costi e sulle stime dei costi basate sul numero di messaggi, vedere [Messaggi dell'hub eventi per i log attività](#event-hub-messages-for-activity-logs) (in questo articolo).

#### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Come integrare i log di controllo di Intune con il sistema di informazioni di sicurezza e gestione degli eventi?

Usare Monitoraggio di Azure con Hub eventi per trasmettere i log al sistema di informazioni di sicurezza e gestione degli eventi. Prima di tutto, [trasmettere i log a un hub eventi](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub), quindi [configurare lo strumento di informazioni di sicurezza e gestione degli eventi](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub) con l'hub eventi configurato. 

#### <a name="what-siem-tools-are-currently-supported"></a>Quali strumenti di informazioni di sicurezza e gestione degli eventi sono attualmente supportati?

Monitoraggio di Azure è attualmente supportato da [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar e [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory) (apre un nuovo sito Web). Per altre informazioni sul funzionamento dei connettori, vedere [Trasmettere i dati di monitoraggio di Azure a un hub eventi per l'utilizzo da parte di uno strumento esterno](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs).

#### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>È possibile accedere ai dati da un hub eventi senza usare uno strumento di informazioni di sicurezza e gestione degli eventi esterno?

Sì. Per accedere ai log dall'applicazione personalizzata, è possibile usare l'[API di Hub eventi](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph).

#### <a name="what-data-is-stored"></a>Quali dati vengono archiviati?

Intune non archivia i dati inviati attraverso la pipeline. Intune instrada i dati alla pipeline di Monitoraggio di Azure, sotto l'autorità del tenant. Per altre informazioni, vedere [Panoramica di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview).

## <a name="next-steps"></a>Passaggi successivi

* [Archiviare i log attività in un account di archiviazione](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Instradare i log attività a un hub eventi](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [Integrare i log attività con Log Analytics](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
