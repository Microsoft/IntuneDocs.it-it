---
title: Gestire gli aggiornamenti software
titleSuffix: Configure Windows Update for Business settings - Intune
description: Informazioni su come configurare le impostazioni di Windows Update for Business in Intune per controllare gli aggiornamenti ai dispositivi Windows 10."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 08/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08f659cf-715e-4e10-9ab2-1bac3c6f2366
ms.reviewer: coryfe
ms.suite: ems
ms.openlocfilehash: 6d88fd62b84c0cc7c3678692cef5ab547bfb8c5d
ms.sourcegitcommit: f9b01976c0fc479ac8bc3998eb55bbc517ed2d84
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2017
---
# <a name="manage-software-updates"></a>Gestire gli aggiornamenti software

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il servizio Windows as a Service consente di aggiornare i dispositivi Windows 10. A partire da Windows 10, i nuovi aggiornamenti qualitativi e delle funzionalità includeranno il contenuto di tutti gli aggiornamenti precedenti. Ciò significa che, una volta installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 sono perfettamente aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Usando Windows Update for Business, è possibile semplificare l'esperienza di gestione degli aggiornamenti in modo da non dover approvare singoli aggiornamenti per gruppi di dispositivi. È comunque possibile gestire i rischi nei propri ambienti configurando una strategia di implementazione degli aggiornamenti. In questo modo, Windows Update verifica che gli aggiornamenti vengano installati al momento opportuno. Microsoft Intune offre la possibilità di configurare le impostazioni di aggiornamento sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. Per gli aggiornamenti i dispositivi accedono direttamente a Windows Update. Usare Intune per configurare e gestire gli **anelli di aggiornamento di Windows 10**. Un anello di aggiornamento contiene un gruppo di impostazioni che definiscono quando e come vengono installati gli aggiornamenti di Windows 10. È ad esempio possibile configurare le impostazioni seguenti:

- **Windows 10 Servicing Branch** (Ramo di manutenzione di Windows 10): scegliere se determinati gruppi di dispositivi dovranno ricevere gli aggiornamenti da Current Branch o da Current Branch for Business.  
- **Deferral Settings** (Impostazioni di differimento): configurare queste impostazioni per ritardare l'installazione degli aggiornamenti per gruppi di dispositivi. Sarà quindi possibile implementare gli aggiornamenti per fasi in modo da poter esaminare lo stato di avanzamento.
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

 I dispositivi che eseguono Windows 10 Mobile e Windows 10 Holographic non sono supportati.

- Nei dispositivi Windows, **Feedback e diagnostica** > **Dati di diagnostica e di utilizzo** deve essere impostato almeno su **Di base**.

    ![Impostazione di Windows per i dati di diagnostica e di utilizzo](./media/telemetry-basic.png)

    È possibile configurare manualmente questa impostazione oppure usare un profilo di restrizione dei dispositivi di Intune per Windows 10 e versioni successive. A tale scopo, configurare l'impostazione **Generale** > **Invio dati di diagnostica** almeno su **Di base**. Per altre informazioni sui profili di dispositivo, vedere [Come configurare le impostazioni relative alle restrizioni dei dispositivi](device-restrictions-configure.md).

- Nella console di amministrazione classica di Intune sono disponibili quattro impostazioni che controllano il comportamento degli aggiornamenti software. Queste impostazioni fanno parte dei criteri di configurazione generale per dispositivi Windows 10 Desktop e Mobile:
    - **Consenti aggiornamenti automatici**
    - **Consenti funzionalità di versioni non definitive**
    - **Giorno pianificato per l'installazione**
    - **Ora pianificata per l'installazione**

  La console classica include anche un numero limitato di altre impostazioni per gli aggiornamenti di Windows 10 nel profilo di configurazione del dispositivo. Se una qualsiasi di queste impostazioni è configurata nella console di amministrazione classica di Intune quando si esegue la migrazione al portale di Azure, è fortemente consigliato procedere nel modo seguente:

1. Creare gli anelli di aggiornamento di Windows 10 nel portale di Azure con le impostazioni necessarie. L'impostazione **Consenti funzionalità di versioni non definitive** non è supportata nel portale di Azure perché non è più applicabile alle build più recenti di Windows 10. È possibile configurare le altre tre impostazioni, e anche quelle relative agli aggiornamenti di Windows 10, quando si creano gli anelli aggiornamento.

  > [!NOTE]
  > Le impostazioni relative agli aggiornamenti di Windows 10 configurate nella console classica non vengono visualizzate nel portale di Azure dopo la migrazione, ma continuano a essere applicate. Se è stata eseguita la migrazione di una qualsiasi di queste impostazioni e si modificano i criteri migrati dal portale di Azure, l'impostazione verrà rimossa dai criteri.

2. Eliminare le impostazioni di aggiornamento nella console classica. Dopo avere eseguito la migrazione al portale di Azure e aver aggiunto le stesse impostazioni in un anello di aggiornamento, è necessario eliminare le impostazioni nel portale classico per evitare possibili conflitti di criteri. Ad esempio, quando la stessa impostazione è configurata con valori diversi, si verifica un conflitto che non è facile identificare perché l'impostazione configurata nella console classica non viene visualizzata nel portale di Azure.

## <a name="how-to-create-and-assign-update-rings"></a>Come creare e assegnare anelli di aggiornamento

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Aggiornamenti software**.
4. Nel pannello **Aggiornamenti software** scegliere **Gestisci** > **Anelli di aggiornamento di Windows 10**.
5. Nel pannello contenente l'elenco degli anelli di aggiornamento scegliere **Crea**.
6. Nel pannello **Crea l'anello di aggiornamento** specificare un nome e una descrizione facoltativa per l'anello di aggiornamento e quindi scegliere **Impostazioni**.
7. Nel pannello **Impostazioni** configurare le informazioni seguenti:
    - **Ramo di manutenzione**: impostare il ramo per cui il dispositivo riceverà gli aggiornamenti di Windows (Current Branch o Current Branch for Business).
    - **Aggiornamenti Microsoft**: scegliere se cercare gli aggiornamenti di app da Microsoft Update.
    - **Driver di Windows**: scegliere se escludere i driver di Windows Update durante gli aggiornamenti.
    - **Comportamento di aggiornamento automatico**: scegliere come gestire il comportamento di aggiornamento automatico per cercare, scaricare e installare gli aggiornamenti. Per informazioni dettagliate, vedere [Update/AllowAutoUpdate](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#update-allowautoupdate).
    - **Periodo di differimento dell'aggiornamento qualitativo (giorni)**: specificare il numero di giorni per cui verranno posticipati gli aggiornamenti qualitativi. È possibile posticipare la ricezione di questi aggiornamenti per un periodo massimo di 30 giorni dalla data di rilascio.  

    Gli aggiornamenti qualitativi includono in genere correzioni e miglioramenti alle funzionalità esistenti di Windows e vengono normalmente pubblicati il primo martedì del mese, anche se possono essere rilasciati da Microsoft in qualsiasi momento. È possibile definire se, e per quanto tempo, posticipare la ricezione degli aggiornamenti qualitativi dopo che sono stati resi disponibili.
    - **Periodo di differimento dell'aggiornamento delle funzionalità (giorni)**: specificare il numero di giorni per cui verranno posticipati gli aggiornamenti delle funzionalità. È possibile posticipare la ricezione di questi aggiornamenti per un periodo massimo di 180 giorni dalla data di rilascio.

    Gli aggiornamenti delle funzionalità includono in genere nuove funzionalità per Windows. Dopo aver configurato l'impostazione **Ramo di manutenzione** (**CB** o **CBB**), è possibile definire se, e per quanto tempo, posticipare la ricezione degli aggiornamenti delle funzionalità dopo che sono stati resi disponibili da Microsoft in Windows Update.

    Ad esempio:  
    **Se Ramo di manutenzione è impostato su CB e il periodo di differimento è di 30 giorni**: si supponga che l'aggiornamento delle funzionalità X sia pubblicamente disponibile in Windows Update come CB nel mese di gennaio. Il dispositivo non riceverà l'aggiornamento fino a febbraio, 30 giorni più tardi.

    **Se Ramo di manutenzione è impostato su CBB e il periodo di differimento è di 30 giorni**: si supponga che l'aggiornamento delle funzionalità X sia pubblicamente disponibile in Windows Update come CB nel mese di gennaio e che venga rilasciato come CBB quattro mesi dopo, nel mese di aprile. Il dispositivo riceverà l'aggiornamento 30 giorni dopo il rilascio come CBB e verrà aggiornato nel mese di maggio.

    - **Ottimizzazione recapito**: scegliere il metodo in base al quale i dispositivi scaricheranno gli aggiornamenti di Windows. Per informazioni dettagliate, vedere [DeliveryOptimization/DODownloadMode](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#deliveryoptimization-dodownloadmode).
8. Al termine della configurazione, fare clic su **OK** e nel pannello **Crea l'anello di aggiornamento** fare clic su **Crea**.

Il nuovo anello di aggiornamento viene visualizzato nell'elenco degli anelli di aggiornamento.

1. Per assegnare un anello, selezionarlo dall'elenco e nella scheda <*nome anello*> scegliere **Assegnazioni**.
2. Nella scheda successiva scegliere **Seleziona gruppi** e quindi selezionare i gruppi a cui assegnare l'anello.
3. Al termine dell'operazione, scegliere **Seleziona** per completare l'assegnazione.



## <a name="update-compliance-reporting"></a>Creazione di report di conformità degli aggiornamenti
È possibile monitorare le implementazioni degli aggiornamenti di Windows 10 usando la soluzione gratuita Update Compliance disponibile in Operations Management Suite (OMS). Per informazioni dettagliate, vedere [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Monitorare gli aggiornamenti di Windows con Update Compliance). Quando si usa questa soluzione, è possibile distribuire un ID commerciale a uno qualsiasi dei dispositivi Windows 10 gestiti da Intune per il quale si vuole creare un report di conformità degli aggiornamenti.

Nella console di Intune è possibile usare le impostazioni URI OMA di un criterio personalizzato per configurare l'ID commerciale. Per informazioni dettagliate, vedere [Impostazioni dei criteri di Intune per i dispositivi Windows 10 in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Questo è il percorso dell'URI OMA (con distinzione tra maiuscole e minuscole) per configurare l'ID commerciale: ./Vendor/MSFT/DMClient/Provider/ProviderID/CommercialID

È ad esempio possibile usare i valori seguenti in **Aggiungi o modifica impostazione URI OMA**:

- **Nome dell'impostazione**: ID commerciale di Windows Analytics
- **Descrizione dell'impostazione**: configurazione dell'ID commerciale per le soluzioni Windows Analytics
- **Tipo di dati**: String
- **OMA-URI** (maiuscole/minuscole): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Valore**: <*Usare il GUID visualizzato nella scheda Telemetria di Windows nell'area di lavoro OMS*>

![Impostazione di Windows per i dati di diagnostica e di utilizzo](./media/commID.png)

<!--
1. Sign into the Azure portal.
2. Choose **More Services** > **Monitoring + Management** > **Intune**.
3. On the **Intune** blade, choose **Software Updates**.
4. On the **Software Updates** blade, choose **Overview**. From here you can see general information about the status of any update rings you assigned.
4. On the **Windows 10 Updates** blade, choose **Monitor** > **Update ring deployment for devices**, **Update ring deployment for users**, or **Per-setting deployment state** to view more detailed information about update ring assignments.
-->





## <a name="how-to-pause-updates"></a>Come sospendere gli aggiornamenti
È possibile sospendere la ricezione degli aggiornamenti qualitativi o delle funzionalità su un dispositivo per un periodo massimo di 35 giorni dall'inizio della sospensione. Dopo che è trascorso il numero massimo di giorni, la funzionalità di sospensione verrà disattivata automaticamente e il dispositivo eseguirà la ricerca degli aggiornamenti applicabili in Windows Updates. Dopo questa ricerca, è possibile sospendere nuovamente gli aggiornamenti.
1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Aggiornamenti software**.
4. Nel pannello **Aggiornamenti software** scegliere **Gestisci** > **Anelli di aggiornamento di Windows 10**.
5. Nel pannello con l'elenco degli anelli di aggiornamento, selezionare l'anello per cui impostare la sospensione e quindi scegliere **...** > **Sospendi l'aggiornamento qualitativo** o **Sospendi gli aggiornamenti delle funzionalità**, a seconda del tipo di aggiornamenti da sospendere.

> [!IMPORTANT]
> Quando si esegue un comando di sospensione, i dispositivi ricevono tale comando non appena controllano la disponibilità di aggiornamenti nel servizio. È quindi possibile che, prima di effettuare questo controllo, installino un aggiornamento pianificato.
> Inoltre, se un dispositivo è spento quando si esegue il comando di sospensione, all'accensione tale dispositivo potrebbe scaricare e installare gli aggiornamenti pianificati prima di controllare la disponibilità di nuovi aggiornamenti con Intune.
