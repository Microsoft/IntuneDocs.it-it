---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune offre tipi di report specifici con viste mirate che contengono dati coerenti e tempestivi.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391942"
---
# <a name="intune-reports"></a>Report di Intune
I report di Microsoft Intune consentono di monitorare in modo più efficace e proattivo l'integrità e l'attività degli endpoint all'interno dell'organizzazione e offrono anche altri dati di reporting in Intune. Ad esempio, sarà possibile visualizzare i report su conformità del dispositivo, integrità del dispositivo e tendenze del dispositivo. Inoltre, è possibile creare report personalizzati per ottenere dati più specifici. 

> [!NOTE]
> Le modifiche apportate ai report di Intune vengono implementate gradualmente in un periodo di tempo che consente di prepararsi e adattarsi alla nuova struttura.

I tipi di report sono organizzati nelle seguenti aree di interesse:
- **Operativo**: specifica dati tempestivi e mirati che consentono di concentrarsi e intraprendere le azioni. Questi report sono particolarmente utili per gli amministratori, gli esperti in materia e il personale del supporto tecnico.
- **Organizzativo**: offre un riepilogo più ampio di una visualizzazione complessiva, ad esempio lo stato della gestione dei dispositivi. I responsabili e gli amministratori troveranno questi report molto utili.
- **Cronologico**: offre modelli e tendenze nell'arco di un determinato periodo di tempo. I responsabili e gli amministratori troveranno questi report molto utili.
- **Specialistico**: consente di usare i dati non elaborati per creare i propri report personalizzati. Questi report sono particolarmente utili per gli amministratori.

Il framework di reporting offre un'esperienza di coerente e più completa per la creazione dei report. I report disponibili offrono le funzionalità seguenti:
- **Ricerca e ordinamento**: è possibile cercare e ordinare i dati in ogni colonna, indipendentemente dalla dimensione del set di dati.
- **Paging dei dati**: è possibile analizzare i dati in base al paging, pagina per pagina o passando a una pagina specifica.
- **Prestazioni**: è possibile generare e visualizzare rapidamente i report creati da tenant di grandi dimensioni.
- **Esportazione**: è possibile esportare rapidamente i dati dei report generati da tenant di grandi dimensioni.

### <a name="who-can-access-the-data"></a>Utenti autorizzati ad accedere ai dati

Gli utenti con le autorizzazioni seguenti possono esaminare i log:

- Amministratore globale
- Amministratore del servizio Intune
- Amministratori assegnati a un ruolo di Intune con autorizzazioni **Lettura**

## <a name="non-compliant-devices-report-operational"></a>Report relativo ai dispositivi non conformi (operativo)
Il report relativo ai dispositivi non conformi presenta i dati che in genere vengono usati dai ruoli amministratore o supporto tecnico per identificare i problemi e consentirne la risoluzione. I dati trovati in questi report sono tempestivi, segnalano i comportamenti imprevisti e sono pensati per essere interattivi. Il report è disponibile insieme al carico di lavoro, quindi il report relativo ai dispositivi non conformi è accessibile senza uscire dai flussi di lavoro attivi. Questo report offre funzionalità di filtro, ricerca, paging e ordinamento. Inoltre, consente di eseguire il drill-down per agevolare la risoluzione dei problemi.

È possibile visualizzare il report relativo ai **dispositivi non conformi** attenendosi alla procedura seguente:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Conformità del dispositivo** > **Dispositivi non conformi**.

    ![Report sul dispositivo non conforme](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>Report di conformità del dispositivo (organizzativo)
I report di conformità dei dispositivi sono ad ampio raggio e offrono una visualizzazione dei dati più tradizionale per identificare le metriche aggregate. Questo report è progettato per funzionare con grandi set di dati in modo da ottenere un'immagine completa della conformità del dispositivo. Ad esempio, nel report per la conformità dei dispositivi sono visualizzati tutti gli stati di conformità per i dispositivi, in modo da offrire una visualizzazione più ampia dei dati, indipendentemente dalla dimensione del set di dati. Questo report offre la suddivisione completa dei record oltre a una comoda visualizzazione delle metriche aggregate. Può essere generato applicando filtri e selezionando il pulsante "Genera report". I dati verranno aggiornati in modo da indicare lo stato più recente con la possibilità di visualizzare i singoli record che costituiscono i dati aggregati. Come la maggior parte dei report nel nuovo framework, questi record possono essere ordinati e sottoposti a ricerca per concentrarsi sulle informazioni necessarie. 

Per visualizzare un report generato sullo stato del dispositivo, è possibile seguire questa procedura:
1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Report** per visualizzare il riepilogo dei report.
3. Selezionare **Conformità del dispositivo**.
4. Selezionare lo **stato di conformità**, il **sistema operativo** e i filtri **proprietà** per perfezionare il report.
5. Fare clic su **Genera report** (o **Genera di nuovo**) per recuperare i dati correnti.

    ![Report di conformità del dispositivo](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > Questo report di **conformità del dispositivo** contiene un timestamp relativo all'ultima generazione del report. 

Per le informazioni correlate, vedere [Applicare la conformità per Microsoft Defender ATP con l'accesso condizionale in Intune](~/protect/advanced-threat-protection.md).

## <a name="reports-summary"></a>Riepilogo dei report 

Il report di conformità del dispositivo è disponibile come report di riepilogo nel carico di lavoro **Report**. Per visualizzare il report di conformità del dispositivo, attenersi alla procedura seguente:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Report** per visualizzare il riepilogo dei report.

    ![Riepilogo dei report di Intune](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>Report tendenza di conformità del dispositivo (cronologico)
I rapporti tendenza di conformità del dispositivo vengono usati più spesso dagli amministratori e dai progettisti per identificare le tendenze a lungo termine per la conformità dei dispositivi. I dati aggregati vengono visualizzati nell'arco di un determinato periodo di tempo e possono essere utili per prendere decisioni di investimento future, agevolare i miglioramenti dei processi o richiedere l'analisi di eventuali anomalie. Si possono anche applicare filtri per visualizzare tendenze specifiche. I dati contenuti in questo report sono uno snapshot dello stato attuale del tenant (quasi in tempo reale). 

Un report per la tendenza di conformità del dispositivo può indicare la tendenza degli stati di conformità del dispositivo in un determinato periodo di tempo. È possibile identificare i punti in cui si sono verificati i picchi di conformità e concentrare le proprie attività di conseguenza.

È possibile visualizzare il report **Tendenze** attenendosi alla procedura seguente:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Report** > **Tendenze** per visualizzare la compatibilità del dispositivo in base a una tendenza di 60 giorni.

    ![Report tendenza di Intune](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Report di integrazione di Monitoraggio di Azure (specialistico)
È possibile personalizzare i report in modo da ottenere dati specifici. I dati contenuti nei report, se necessario, potranno essere disponibili via [Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/overview) usando [Log Analytics](reports.md#log-analytics) e le [cartelle di lavoro di Monitoraggio di Azure](reports.md#workbooks). Queste soluzioni consentono di creare query personalizzate, configurare avvisi e fare in modo che nei dashboard i dati sulla conformità del dispositivo siano visualizzati nel modo più adeguato. Inoltre, è possibile conservare i log attività nell'account di archiviazione di Azure, eseguire l'integrazione con i report usando gli [strumenti SIEM per le informazioni di sicurezza e la gestione degli eventi](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration) e correlare i report ai log attività di Azure AD. Le cartelle di lavoro di Monitoraggio di Azure possono essere usate in aggiunta all'importazione dei dashboard per la creazione di report personalizzati.

> [!NOTE]
> La funzionalità di reporting complessa richiede una sottoscrizione di Azure.

Un report specialistico, ad esempio, può correlare i dati di proprietà del dispositivo con i dati di registrazione della piattaforma in un report personalizzato. Quindi, si potrebbe visualizzare questo report personalizzato in un dashboard esistente nel portale di Azure Active Directory.

È possibile creare e visualizzare i report personalizzati attenendosi alla procedura seguente:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Report** > **Impostazioni di diagnostica** Aggiungi [impostazione di diagnostica](reports.md#diagnostic-settings).

    ![Riepilogo dei report di Intune](./media/intune-reports/intune-reports-04.png)

3. Fare clic su **Aggiungi impostazione di diagnostica** per visualizzare il riquadro **Impostazioni di diagnostica**. 
4. Aggiungere un **nome** per le impostazioni di diagnostica. 
5. Selezionare le impostazioni **Invia a Log Analytics** e **DeviceComplianceOrg**.

    ![Riepilogo dei report di Intune](./media/intune-reports/intune-reports-04a.png)

6. Fare clic su **Save**.
7. Selezionare quindi **Analisi log** per creare ed eseguire una nuova query di log usando [Log Analytics](reports.md#log-analytics).

   ![Log Analytics - Query di log](./media/intune-reports/intune-reports-05.png)

8. Selezionare **Cartelle di lavoro** per creare o aprire un report interattivo usando le [cartelle di lavoro di Monitoraggio di Azure](reports.md#workbooks).

   ![Cartelle di lavoro - Report interattivi](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>Impostazioni di diagnostica
Ogni risorsa di Azure richiede la propria impostazione di diagnostica. L'impostazione di diagnostica definisce i seguenti elementi per una risorsa:

- Categorie di log e dati di metriche inviati alle destinazioni definite nell'impostazione. Le categorie disponibili variano per i diversi tipi di risorsa.
- Una o più destinazioni per inviare i log. Le destinazioni correnti includono l'area di lavoro di Log Analytics, Hub eventi e Archiviazione di Azure.
- Criteri di conservazione per i dati archiviati in Archiviazione di Azure.

Una sola impostazione di diagnostica può definire un solo tipo di destinazione. Se si vogliono inviare dati a più tipi specifici di destinazione (ad esempio, due diverse aree di lavoro di Log Analytics), creare più impostazioni. Ogni risorsa può avere al massimo 5 impostazioni di diagnostica.

Per altre informazioni sulle impostazioni di diagnostica, vedere [Creare un'impostazione di diagnostica per raccogliere i log e le metriche della piattaforma in Azure](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings).

### <a name="log-analytics"></a>Log Analytics
Log Analytics è lo strumento principale nel portale di Azure per la scrittura di query di log e l'analisi interattiva dei risultati delle query. Anche se una query di log viene utilizzata altrove in Monitoraggio di Azure, normalmente la query viene prima scritta e testata usando Log Analytics. Per i dettagli sull'uso di Log Analytics e sulla creazione delle query di log, vedere la [panoramica delle query di log in Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview). 

### <a name="workbooks"></a>Cartelle di lavoro
Le cartelle di lavoro combinano testo, query di Analytics, metriche di Azure e parametri all'interno di report interattivi avanzati. Le cartelle di lavoro possono essere modificate dagli altri membri del team che hanno accesso alle stesse risorse di Azure. Per altre informazioni sulle cartelle di lavoro, vedere [Cartelle di lavoro di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks). Inoltre, l'utente può usare i modelli di cartelle di lavoro e contribuire agli stessi. Per altre informazioni, vedere l'articolo relativo ai [modelli di cartella di lavoro di Monitoraggio di Azure](https://go.microsoft.com/fwlink/?linkid=867045).

## <a name="next-steps"></a>Passaggi successivi

Altre informazioni sulle tecnologie seguenti:
- [Blog - Post sul framework di reporting di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Monitoraggio di Azure](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [Informazioni su Log Analytics](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [Query di log](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Introduzione a Log Analytics in Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Cartelle di lavoro di Monitoraggio di Azure](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [Strumenti SIEM (Security information and event management)](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
