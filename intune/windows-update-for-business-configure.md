---
title: Configurare le impostazioni di Windows Update for Business in Intune
titleSuffix: Azure portal
description: Informazioni su come configurare le impostazioni di Windows Update for Business in Intune per controllare gli aggiornamenti ai dispositivi Windows 10."
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: d6ccda2aba0b1383de6c38b7a2fdcfdc742d0e15
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="manage-software-updates"></a>Gestire gli aggiornamenti software

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il servizio Windows as a Service consente di aggiornare i dispositivi Windows 10. A partire da Windows 10, i nuovi aggiornamenti qualitativi e delle funzionalità includeranno il contenuto di tutti gli aggiornamenti precedenti. Ciò significa che, una volta installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 sono aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Usando Windows Update for Business, è possibile semplificare l'esperienza di gestione degli aggiornamenti in modo da non dover approvare singoli aggiornamenti per gruppi di dispositivi. È comunque possibile gestire i rischi nei propri ambienti configurando una strategia di implementazione degli aggiornamenti. In questo modo, Windows Update verifica che gli aggiornamenti vengano installati al momento opportuno. Microsoft Intune offre la possibilità di configurare le impostazioni di aggiornamento sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. I dispositivi accedono direttamente a Windows Update per gli aggiornamenti. Usare Intune per configurare e gestire gli **anelli di aggiornamento di Windows 10**. Un anello di aggiornamento contiene un gruppo di impostazioni che definiscono quando e come vengono installati gli aggiornamenti di Windows 10. È ad esempio possibile configurare le impostazioni seguenti:

- **Canale di manutenzione di Windows 10**: scegliere se si vuole che i gruppi di dispositivi ricevano aggiornamenti dal canale semestrale (mirato) o dal canale semestrale.  
- **Deferral Settings** (Impostazioni di differimento): configurare queste impostazioni per ritardare l'installazione degli aggiornamenti per gruppi di dispositivi. Usare queste impostazioni per implementare gli aggiornamenti per fasi in modo da poter esaminare lo stato di avanzamento.
- **Pausing** (Sospensione): posticipare l'installazione degli aggiornamenti se si rileva un problema in un momento qualsiasi durante l'implementazione.
- **Maintenance window** (Finestra di manutenzione): configurare gli orari in cui possono essere installati gli aggiornamenti.
- **Update type** (Tipo di aggiornamento): scegliere i tipi di aggiornamento da installare. Ad esempio, gli aggiornamenti qualitativi, quelli delle funzionalità o i driver.
- **Installation behavior** (Comportamento di installazione): configurare la modalità di installazione dell'aggiornamento. Ad esempio, il dispositivo viene riavviato automaticamente dopo l'installazione?
- **Peer downloading** (Download peer-to-peer): specificare se configurare il download peer-to-peer. Se è configurata questa modalità di download, quando un dispositivo ha completato il download di un aggiornamento, altri dispositivi possono scaricare l'aggiornamento da tale dispositivo. In questo modo, il processo di download viene completato più velocemente.

Dopo aver creato anelli di aggiornamento, assegnarli a gruppi di dispositivi. Usando anelli di aggiornamento, è possibile creare una strategia di aggiornamento adatta alle esigenze aziendali. Per altre informazioni, vedere [Gestire gli aggiornamenti con Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="before-you-start"></a>Prima di iniziare

- Per aggiornare i PC Windows 10, è necessario che sia in esecuzione almeno Windows 10 Pro con l'aggiornamento dell'anniversario di Windows.

- Windows Update supporta le versioni di Windows 10 seguenti:
    - Windows 10
    - Windows 10 Team (per dispositivi Surface Hub)
    - [Windows Holographic for Business](#windows-holographic-for-business-support)

 I dispositivi che eseguono Windows 10 Mobile non sono supportati.

- Nei dispositivi Windows, **Feedback e diagnostica** > **Dati di diagnostica e di utilizzo** deve essere impostato almeno su **Di base**.

    ![Impostazione di Windows per i dati di diagnostica e di utilizzo](./media/telemetry-basic.png)

    È possibile configurare manualmente questa impostazione oppure usare un profilo di restrizione dei dispositivi di Intune per Windows 10 e versioni successive. A tale scopo, configurare l'impostazione **Generale** > **Invio dati di diagnostica** almeno su **Di base**. Per altre informazioni sui profili di dispositivo, vedere [Come configurare le impostazioni relative alle restrizioni dei dispositivi](device-restrictions-configure.md).

- Nella console di amministrazione di Intune sono disponibili quattro impostazioni che controllano il comportamento degli aggiornamenti software. Queste impostazioni fanno parte dei criteri di configurazione generale per dispositivi Windows 10 Desktop e Mobile:
    - **Consenti aggiornamenti automatici**
    - **Consenti funzionalità di versioni non definitive**
    - **Giorno pianificato per l'installazione**
    - **Ora pianificata per l'installazione**

  Il portale classico include anche un numero limitato di altre impostazioni per gli aggiornamenti di Windows 10 nel profilo di configurazione del dispositivo. Se una qualsiasi di queste impostazioni è configurata nella console di amministrazione di Intune quando si esegue la migrazione al portale di Azure, è fortemente consigliato procedere nel modo seguente:

1. Creare gli anelli di aggiornamento di Windows 10 nel portale di Azure con le impostazioni necessarie. L'impostazione **Consenti funzionalità di versioni non definitive** non è supportata nel portale di Azure perché non è più applicabile alle build più recenti di Windows 10. È possibile configurare le altre tre impostazioni, e anche quelle relative agli aggiornamenti di Windows 10, quando si creano gli anelli aggiornamento.

  > [!NOTE]
  > Le impostazioni relative agli aggiornamenti di Windows 10 configurate nel portale classico non vengono visualizzate nel portale di Azure dopo la migrazione, ma continuano a essere applicate. Se è stata eseguita la migrazione di una qualsiasi di queste impostazioni e si modificano i criteri migrati dal portale di Azure, l'impostazione viene rimossa dai criteri.

2. Eliminare le impostazioni di aggiornamento nel portale classico. Dopo avere eseguito la migrazione al portale di Azure e aver aggiunto le stesse impostazioni in un anello di aggiornamento, è necessario eliminare le impostazioni nel portale classico per evitare possibili conflitti di criteri. Ad esempio, quando la stessa impostazione è configurata con valori diversi, si verifica un conflitto che non è facile identificare perché l'impostazione configurata nel portale classico non viene visualizzata nel portale di Azure.

## <a name="how-to-create-and-assign-update-rings"></a>Come creare e assegnare anelli di aggiornamento

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Aggiornamenti software**.
4. Nel riquadro **Aggiornamenti software** scegliere **Gestisci** > **Anelli di aggiornamento di Windows 10**.
5. Nel riquadro contenente l'elenco degli anelli di aggiornamento scegliere **Crea**.
6. Nel riquadro **Crea l'anello di aggiornamento** specificare un nome e una descrizione (facoltativa) per l'anello di aggiornamento e quindi scegliere **Impostazioni - Configura**.
7. Nel riquadro **Impostazioni** configurare le informazioni seguenti:
    - **Canale di manutenzione**: impostare il canale per il quale il dispositivo riceve gli aggiornamenti di Windows: semestrale mirato(destinazione) o semestrale.
    - **Aggiornamenti ai prodotti Microsoft**: scegliere se cercare gli aggiornamenti di app da Microsoft Update.
    - **Driver di Windows**: scegliere se escludere i driver di Windows Update durante gli aggiornamenti.
    - **Comportamento di aggiornamento automatico**: scegliere come gestire il comportamento di aggiornamento automatico per cercare, scaricare e installare gli aggiornamenti. Per informazioni dettagliate, vedere [Update/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Periodo di differimento dell'aggiornamento qualitativo (giorni)**: specificare il numero di giorni per cui vengono posticipati gli aggiornamenti qualitativi. È possibile posticipare la ricezione di questi aggiornamenti per un periodo massimo di 30 giorni dalla data di rilascio.  

    Gli aggiornamenti qualitativi includono in genere correzioni e miglioramenti alle funzionalità esistenti di Windows e vengono normalmente pubblicati il primo martedì del mese, anche se possono essere rilasciati da Microsoft in qualsiasi momento. È possibile definire se, e per quanto tempo, posticipare la ricezione degli aggiornamenti qualitativi dopo che sono stati resi disponibili.

    - **Periodo di differimento dell'aggiornamento delle funzionalità (giorni)**: specificare il numero di giorni per cui vengono posticipati gli aggiornamenti delle funzionalità. È possibile posticipare la ricezione di questi aggiornamenti per un periodo massimo di 180 giorni dalla data di rilascio.

    Gli aggiornamenti delle funzionalità includono in genere nuove funzionalità per Windows. Dopo aver configurato l'impostazione **Canale di manutenzione** (canale semestrale (mirato) o canale semestrale), è possibile definire se, e per quanto tempo, posticipare la ricezione degli aggiornamenti delle funzionalità dopo che sono stati resi disponibili da Microsoft in Windows Update.

    Ad esempio: **Se il Canale di manutenzione è impostato su Canale semestrale (mirato) e il periodo di differimento è di 30 giorni**: si supponga che l'aggiornamento delle funzionalità X sia disponibile pubblicamente su Windows Update come Canale semestrale (mirato) a gennaio. Il dispositivo non riceverà l'aggiornamento fino a febbraio, 30 giorni più tardi.

    **Se il Canale di manutenzione è impostato su Canale semestrale e il periodo di differimento è di 30 giorni**: si supponga che l'aggiornamento delle funzionalità X sia disponibile pubblicamente su Windows Update come Canale semestrale (mirato) a gennaio. Quattro mesi dopo, in aprile, l'aggiornamento della funzionalità X sarà rilasciato come Canale semestrale. Il dispositivo riceverà l'aggiornamento 30 giorni dopo il rilascio del canale semestrale e verrà aggiornato nel mese di maggio.

    - **Modalità di download con ottimizzazione recapito**: scegliere il metodo in base al quale i dispositivi devono scaricare gli aggiornamenti di Windows. Per informazioni dettagliate, vedere [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).
1. Al termine della configurazione, fare clic su **OK** e nel riquadro **Crea l'anello di aggiornamento** fare clic su **Crea**.

Il nuovo anello di aggiornamento viene visualizzato nell'elenco degli anelli di aggiornamento.

1. Per assegnare un anello, selezionarlo dall'elenco e nella scheda <*nome anello*> scegliere **Assegnazioni**.
2. Nella scheda successiva scegliere **Selezionare i gruppi da includere** e quindi selezionare i gruppi a cui assegnare l'anello.
3. Al termine dell'operazione, scegliere **Seleziona** per completare l'assegnazione.

## <a name="update-compliance-reporting"></a>Creazione di report di conformità degli aggiornamenti
È possibile visualizzare la conformità degli aggiornamenti in Intune oppure usando la soluzione gratuita Conformità aggiornamenti disponibile in Operations Management Suite (OMS).

### <a name="review-update-compliance-in-intune"></a>Verificare la conformità degli aggiornamenti in Intune 
<!-- 1352223 -->
Rivedere un report sui criteri per visualizzare lo stato di distribuzione per gli anelli di aggiornamento di Windows 10 configurati. 
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Aggiornamenti software**.
4. Nel riquadro **Aggiornamenti software** scegliere **Panoramica**. Vengono visualizzate informazioni generali sullo stato di tutte le fasi di aggiornamento assegnate.
5. Aprire uno dei report seguenti: 
     
   **Per tutti gli anelli di distribuzione:**
   1. Passare al riquadro **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10**. 
   2. Nella sezione **Monitoraggio** scegliere **Stato di distribuzione per ogni anello di aggiornamento**.
                   
   **Per anelli di distribuzione specifici:** 
   1. Nel riquadro **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10** scegliere l'anello di distribuzione da rivedere.
   2. Nella sezione **Monitoraggio** scegliere uno dei report seguenti per visualizzare informazioni dettagliate sull'anello di aggiornamento:
      - **Stato del dispositivo**
      - **Stato utente**

### <a name="review-update-compliance-using-oms"></a>Verificare la conformità degli aggiornamenti usando OMS
È possibile monitorare le implementazioni degli aggiornamenti di Windows 10 usando la soluzione gratuita Update Compliance disponibile in Operations Management Suite (OMS). Per informazioni dettagliate, vedere [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Monitorare gli aggiornamenti di Windows con Update Compliance). Quando si usa questa soluzione, è possibile distribuire un ID commerciale a uno qualsiasi dei dispositivi Windows 10 gestiti da Intune per il quale si vuole creare un report di conformità degli aggiornamenti.

Nella console di Intune è possibile usare le impostazioni URI OMA di un criterio personalizzato per configurare l'ID commerciale. Per informazioni dettagliate, vedere [Impostazioni dei criteri di Intune per i dispositivi Windows 10 in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Questo è il percorso dell'URI OMA (con distinzione tra maiuscole e minuscole) per configurare l'ID commerciale: ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

È ad esempio possibile usare i valori seguenti in **Aggiungi o modifica impostazione URI OMA**:

- **Nome dell'impostazione**: ID commerciale di Windows Analytics
- **Descrizione dell'impostazione**: configurazione dell'ID commerciale per le soluzioni Windows Analytics
- **URI OMA** (maiuscole/minuscole): ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID
- **Tipo di dati**: String
- **Valore**: <*Usare il GUID visualizzato nella scheda Telemetria di Windows nell'area di lavoro OMS*>

![Impostazione di Windows per i dati di diagnostica e di utilizzo](./media/commID.png)

## <a name="how-to-pause-updates"></a>Come sospendere gli aggiornamenti
È possibile sospendere la ricezione degli aggiornamenti qualitativi o delle funzionalità su un dispositivo per un periodo massimo di 35 giorni dall'inizio della sospensione. Dopo che è trascorso il numero massimo di giorni, la funzionalità di sospensione verrà disattivata automaticamente e il dispositivo eseguirà la ricerca degli aggiornamenti applicabili in Windows Updates. Dopo questa ricerca, è possibile sospendere nuovamente gli aggiornamenti.
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Aggiornamenti software**.
4. Nel riquadro **Aggiornamenti software** scegliere **Gestisci** > **Anelli di aggiornamento di Windows 10**.
5. Nel riquadro con l'elenco degli anelli di aggiornamento, scegliere l'anello per cui impostare la sospensione e quindi scegliere **...** > **Sospendi l'aggiornamento qualitativo** > o **Sospendi gli aggiornamenti delle funzionalità**, a seconda del tipo di aggiornamenti da sospendere.

> [!IMPORTANT]
> Quando si esegue un comando di sospensione, i dispositivi ricevono tale comando non appena controllano la disponibilità di aggiornamenti nel servizio. È quindi possibile che, prima di effettuare questo controllo, installino un aggiornamento pianificato.
> Inoltre, se un dispositivo è spento quando si esegue il comando di sospensione, all'accensione tale dispositivo potrebbe scaricare e installare gli aggiornamenti pianificati prima di controllare la disponibilità di nuovi aggiornamenti con Intune.

## <a name="windows-holographic-for-business-support"></a>Supporto di Windows Holographic for Business

Windows Holographic for Business supporta le impostazioni seguenti:

- **Comportamento di aggiornamento automatico**
- **Aggiornamenti ai prodotti Microsoft**
- **Canale di manutenzione**