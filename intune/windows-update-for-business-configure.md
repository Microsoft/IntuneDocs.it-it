---
title: Configurare Windows Update for Business in Microsoft Intune - Azure | Microsoft Docs
description: Aggiornare le impostazioni di aggiornamento software in un profilo per la creazione di un anello di aggiornamento, esaminare la conformità e sospendere gli aggiornamenti in Windows Update for Business con Microsoft Intune nei dispositivi Windows 10.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 11/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: a715fe518331d20b9a47d8374a37ce66ec59055d
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189288"
---
# <a name="manage-software-updates-in-intune"></a>Gestire gli aggiornamenti software in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Il servizio Windows as a Service consente di aggiornare i dispositivi Windows 10. In Windows 10 i nuovi aggiornamenti qualitativi e delle funzionalità includono il contenuto di tutti gli aggiornamenti precedenti. Se è stato installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 siano aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Tramite Windows Update for Business si semplifica l'esperienza di gestione degli aggiornamenti. Non è necessario approvare gli aggiornamenti singoli per i gruppi di dispositivi. È possibile gestire i rischi negli ambienti configurando una strategia di implementazione degli aggiornamenti. Windows Update verifica che gli aggiornamenti vengano installati al momento giusto. Microsoft Intune offre la possibilità di configurare le impostazioni di aggiornamento sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. I dispositivi accedono direttamente a Windows Update per gli aggiornamenti. Usare Intune per configurare e gestire gli **anelli di aggiornamento di Windows 10**. Un anello di aggiornamento include un gruppo di impostazioni che definiscono quando e come vengono installati gli aggiornamenti di Windows 10. È ad esempio possibile configurare le seguenti impostazioni:

- **Canale di manutenzione di Windows 10**: scegliere il canale di manutenzione da cui si vuole che i gruppi di dispositivi ricevano gli aggiornamenti. Sono disponibili i canali seguenti: 
  - Canale semestrale
  - Canale semestrale (mirato)
  - Windows Insider &#8208; Veloce
  - Windows Insider &#8208; Lenta
  - Versione di Windows Insider 
      
  Per informazioni dettagliate sui canali di manutenzione disponibili, vedere [Panoramica di Windows as a Service](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels).
- **Deferral Settings** (Impostazioni di differimento): configurare queste impostazioni per ritardare l'installazione degli aggiornamenti per gruppi di dispositivi. Usare queste impostazioni per implementare gli aggiornamenti per fasi in modo da poter esaminare lo stato di avanzamento.
- **Sospensione**: se si verifica un problema durante l'implementazione dell'aggiornamento, è possibile posticipare l'installazione dell'aggiornamento. 
- **Maintenance window** (Finestra di manutenzione): configurare gli orari in cui possono essere installati gli aggiornamenti.
- **Update type** (Tipo di aggiornamento): scegliere i tipi di aggiornamento da installare. Ad esempio, gli aggiornamenti qualitativi, quelli delle funzionalità o i driver.
- **Comportamento installazione**: consente di configurare la modalità di installazione dell'aggiornamento. Ad esempio, il dispositivo viene riavviato automaticamente dopo l'installazione?
- **Peer downloading** (Download peer-to-peer): specificare se configurare il download peer-to-peer. Se è configurata questa modalità di download, quando un dispositivo ha completato il download di un aggiornamento, altri dispositivi possono scaricare l'aggiornamento da tale dispositivo. Con questa impostazione il processo di download viene completato più velocemente.

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

    È possibile configurare manualmente questa impostazione o usare un profilo di Intune per Windows 10 e versioni successive (**Limitazioni del dispositivo** > **Creazione report e Telemetria** > Impostare **Condividi i dati di utilizzo** almeno su **Livello minimo**). Per altre informazioni sui profili di dispositivo, vedere la pagina che spiega come [configurare le impostazioni di restrizione dei dispositivi](device-restrictions-configure.md).

- Il portale di Azure classico include anche un numero limitato di altre impostazioni per gli aggiornamenti di Windows 10 nel profilo di configurazione del dispositivo. Se una di queste impostazioni viene configurata quando si esegue la migrazione al portale di Azure, è fortemente consigliato procedere nel modo seguente:

  1. Creare gli anelli di aggiornamento di Windows 10 nel portale di Azure con le impostazioni necessarie. L'impostazione **Consenti funzionalità di versioni non definitive** non è supportata nel portale di Azure perché non è più applicabile alle build più recenti di Windows 10. È possibile configurare le altre impostazioni e quelle relative agli aggiornamenti di Windows 10, quando si creano gli anelli aggiornamento.

   > [!NOTE]
   > Le impostazioni relative agli aggiornamenti di Windows 10 configurate nel portale classico non vengono visualizzate nel portale di Azure dopo la migrazione, Queste impostazioni vengono tuttavia applicate. Se si esegue la migrazione di una qualsiasi di queste impostazioni e si modificano i criteri migrati dal portale di Azure, l'impostazione viene rimossa dai criteri.

  2. Eliminare le impostazioni di aggiornamento nel portale classico. Dopo aver eseguito la migrazione al portale di Azure e aver aggiunto le stesse impostazioni in un anello di aggiornamento, eliminare le impostazioni nel portale classico per evitare possibili conflitti di criteri. Quando, ad esempio, la stessa impostazione viene configurata con valori diversi, si verifica un conflitto. Non esiste un modo semplice per scoprire il motivo per cui l'impostazione configurata nel portale classico non viene visualizzata nel portale di Azure.

## <a name="create-and-assign-update-rings"></a>Creare e assegnare anelli di aggiornamento

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
2. Selezionare **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10** > **Crea**.
3. Immettere un nome e una descrizione (facoltativo) e quindi fare clic su **Configura**.
4. In **Impostazioni** immettere le impostazioni seguenti:

   - **Canale di manutenzione**: impostare il canale da cui il dispositivo riceve gli aggiornamenti di Windows.
   - **Aggiornamenti ai prodotti Microsoft**: scegliere se cercare gli aggiornamenti di app da Microsoft Update.
   - **Driver di Windows**: scegliere se escludere i driver di Windows Update durante gli aggiornamenti.
   - **Comportamento di aggiornamento automatico**: scegliere la modalità di installazione degli aggiornamenti automatici e quando riavviare. Per informazioni dettagliate, vedere [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate).
     - **Frequenza del comportamento automatico**: se si seleziona **Installa e riavvia automaticamente all'ora pianificata** per il comportamento di aggiornamento, viene visualizzata questa impostazione. Usare questa impostazione per pianificare il momento in cui vengono installati gli aggiornamenti, inclusi settimana, data e ora.

   - **Verifiche al riavvio**: abilitata per impostazione predefinita. Quando si riavvia un dispositivo, vengono eseguite alcune verifiche, ad esempio la ricerca di utenti attivi, i livelli di batteria, eventuali giochi in esecuzione e altro ancora. Per ignorare queste verifiche quando si riavvia un dispositivo, selezionare **Ignora**.

   - **Periodo di differimento dell'aggiornamento qualitativo (giorni)**: immettere il numero di giorni per cui vengono posticipati gli aggiornamenti qualitativi. È possibile posticipare la ricezione di questi aggiornamenti per un massimo di 30 giorni dalla data di rilascio.

     Gli aggiornamenti qualitativi includono in genere correzioni e miglioramenti alle funzionalità esistenti di Windows e vengono pubblicati il secondo martedì del mese. Gli aggiornamenti qualitativi tramite Windows Update per le aziende ricevono solo questi aggiornamenti (versione 'B') sebbene Microsoft possa rilasciare altri aggiornamenti in qualsiasi momento. Una volta disponibili in Windows Update, è possibile definire se e per quanto tempo posticipare la ricezione degli aggiornamenti qualitativi. Per altre informazioni, vedere [Distribuire gli aggiornamenti tramite Windows Update per le aziende](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb).

   - **Periodo di differimento dell'aggiornamento delle funzionalità (giorni)**: immettere il numero di giorni per cui vengono posticipati gli aggiornamenti delle funzionalità. È possibile posticipare la ricezione di questi aggiornamenti per un massimo di 180 giorni dalla data di rilascio.

     Gli aggiornamenti delle funzionalità includono in genere nuove funzionalità per Windows. Dopo aver configurato l'impostazione **Canale di manutenzione**, è possibile definire se e per quanto tempo posticipare la ricezione degli aggiornamenti delle funzionalità dopo che sono stati resi disponibili in Windows Update.

     Ad esempio: **Se il Canale di manutenzione è impostato su Canale semestrale (mirato) e il periodo di differimento è di 30 giorni**: si supponga che l'aggiornamento delle funzionalità X sia disponibile pubblicamente su Windows Update come Canale semestrale (mirato) a gennaio. Il dispositivo non riceve l'aggiornamento fino a febbraio, 30 giorni più tardi.

     **Se il Canale di manutenzione è impostato su Canale semestrale e il periodo di differimento è di 30 giorni**: si supponga che l'aggiornamento delle funzionalità X sia disponibile pubblicamente su Windows Update come Canale semestrale (mirato) a gennaio. Quattro mesi dopo, in aprile, l'aggiornamento della funzionalità X sarà rilasciato come Canale semestrale. Il dispositivo riceve l'aggiornamento 30 giorni dopo il rilascio del canale semestrale e viene aggiornato nel mese di maggio.

   - **Modalità di download con ottimizzazione recapito**: scegliere il metodo in base al quale i dispositivi devono scaricare gli aggiornamenti di Windows. Per informazioni dettagliate, vedere [DeliveryOptimization/DODownloadMode](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#download-mode).

5. Al termine, selezionare **OK**. In **Crea l'anello di aggiornamento** selezionare **Crea**.

Il nuovo anello di aggiornamento viene visualizzato nell'elenco degli anelli di aggiornamento.

1. Per assegnare un anello, selezionarlo dall'elenco e nella scheda <*nome anello*> scegliere **Assegnazioni**.
2. Nella scheda successiva scegliere **Selezionare i gruppi da includere** e quindi selezionare i gruppi a cui assegnare l'anello.
3. Al termine, scegliere **Seleziona** per completare l'assegnazione.

## <a name="update-compliance-reporting"></a>Creazione di report di conformità degli aggiornamenti
È possibile visualizzare la conformità degli aggiornamenti in Intune oppure usando la soluzione gratuita Conformità aggiornamenti.

### <a name="review-update-compliance-in-intune"></a>Verificare la conformità degli aggiornamenti in Intune 
<!-- 1352223 --> Rivedere un report sui criteri per visualizzare lo stato di distribuzione per gli anelli di aggiornamento di Windows 10 configurati.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
2. Selezionare **Aggiornamenti software** > **Panoramica**. Vengono visualizzate informazioni generali sullo stato di tutti gli anelli di aggiornamento assegnati.
3. Aprire uno dei report seguenti:

   **Per tutti gli anelli di distribuzione**:  
   1. In **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10**
   2. Nella sezione **Monitoraggio** scegliere **Stato di distribuzione per ogni anello di aggiornamento**.

   **Per anelli di distribuzione specifici**:  
   1. In **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10** scegliere l'anello di distribuzione da rivedere.
   2. Nella sezione **Monitoraggio** scegliere uno dei report seguenti per visualizzare informazioni dettagliate sull'anello di aggiornamento:
      - **Stato del dispositivo**
      - **Stato utente**

### <a name="review-update-compliance-using-oms"></a>Verificare la conformità degli aggiornamenti usando OMS
È possibile monitorare le implementazioni degli aggiornamenti di Windows 10 usando la soluzione gratuita Update Compliance. Per informazioni dettagliate, vedere [Monitor Windows Updates with Update Compliance](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor) (Monitorare gli aggiornamenti di Windows con Update Compliance). Quando si usa questa soluzione, è possibile distribuire un ID commerciale a uno qualsiasi dei dispositivi Windows 10 gestiti da Intune per il quale si vuole creare un report di conformità degli aggiornamenti.

In Intune è possibile usare le impostazioni OMA-URI di un criterio personalizzato per configurare l'ID commerciale. Per informazioni dettagliate, vedere [Impostazioni dei criteri di Intune per i dispositivi Windows 10 in Microsoft Intune](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune).   

Il percorso dell'URI OMA (con distinzione tra maiuscole e minuscole) per configurare l'ID commerciale è: ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID

È ad esempio possibile usare i valori seguenti in **Aggiungi o modifica impostazione URI OMA**:

- **Nome dell'impostazione**: ID commerciale di Windows Analytics
- **Descrizione dell'impostazione**: configurazione dell'ID commerciale per le soluzioni Windows Analytics
- **OMA-URI** (maiuscole/minuscole): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **Tipo di dati**: String
- **Valore**: <*Usare il GUID visualizzato nella scheda Telemetria di Windows nell'area di lavoro OMS*>

![Impostazioni URI OMA - Modifica riga](./media/commID-edit.png)

> [!NOTE]
> Per altre informazioni su MS DM Server, vedere [DMClient configuration service provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp) (Provider di servizi di configurazione per DMClient).

## <a name="pause-updates"></a>Sospendere gli aggiornamenti
È possibile sospendere la ricezione degli aggiornamenti qualitativi o delle funzionalità su un dispositivo per un periodo massimo di 35 giorni dall'inizio della sospensione. Dopo che è trascorso il numero massimo di giorni, la funzionalità di sospensione scade automaticamente e il dispositivo esegue la ricerca degli aggiornamenti applicabili in Windows Update. Dopo questa ricerca, è possibile sospendere nuovamente gli aggiornamenti.

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
2. Selezionare **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10**.
3. Nell'elenco degli anelli di aggiornamento scegliere l'anello per cui impostare la sospensione e quindi scegliere **...** > **Sospendi l'aggiornamento qualitativo** > o **Sospendi gli aggiornamenti delle funzionalità**, a seconda del tipo di aggiornamenti da sospendere.

> [!IMPORTANT]
> Quando si esegue un comando di sospensione, i dispositivi ricevono tale comando al successivo controllo della disponibilità di aggiornamenti nel servizio. È quindi possibile che, prima di effettuare questo controllo, installino un aggiornamento pianificato.
> Inoltre, se un dispositivo è spento quando si esegue il comando di sospensione, all'accensione tale dispositivo potrebbe scaricare e installare gli aggiornamenti pianificati prima di controllare la disponibilità di nuovi aggiornamenti con Intune.

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Disinstallare gli aggiornamenti più recenti dagli aggiornamenti software di Windows 10 
Se si verifica un problema di rilievo nei computer Windows 10, è possibile scegliere di disinstallare l'ultimo aggiornamento delle funzionalità oppure l'ultimo aggiornamento qualitativo. La disinstallazione di un aggiornamento delle funzionalità o di un aggiornamento qualitativo è disponibile solo per il canale di manutenzione su cui è attivo il dispositivo. La disinstallazione attiva un criterio per il ripristino dell'aggiornamento precedente nei computer Windows 10. In particolare per gli aggiornamenti delle funzionalità, è possibile limitare a un intervallo di giorni compreso tra 2 e 60 la disinstallazione dell'ultima versione. Per impostare le opzioni di disinstallazione degli aggiornamenti software:

1. In Intune selezionare **Aggiornamenti software**.
2. Select **Anelli di aggiornamento di Windows 10** > selezionare una fase di aggiornamento esistente > **Disinstalla**.

> [!NOTE]
> Nei computer Windows 10, al termine del rollback dell'aggiornamento qualitativo, gli utenti finali continuano a vedere l'aggiornamento elencato in **Impostazioni di Windows** > **Aggiornamenti**  >  **Cronologia degli aggiornamenti**.

## <a name="windows-holographic-for-business-support"></a>Supporto di Windows Holographic for Business

Windows Holographic for Business supporta le impostazioni seguenti:

- **Comportamento di aggiornamento automatico**
- **Aggiornamenti ai prodotti Microsoft**
- **Canale di manutenzione**: supporta le opzioni **Canale semestrale** e **Canale semestrale (mirato)**
