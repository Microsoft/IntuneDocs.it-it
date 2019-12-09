---
title: Configurare Windows Update for Business in Microsoft Intune - Azure | Microsoft Docs
description: Gestire gli aggiornamenti software di Windows 10 usando gli anelli di aggiornamento e i criteri degli aggiornamenti delle funzionalità. È possibile esaminare la conformità e sospendere l'installazione degli aggiornamenti con le impostazioni di Windows Update per le aziende con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7c3398f28d7c396c873dd29f3e3fdd719c1a7c6
ms.sourcegitcommit: f26039d674eb4d61ab68264dd1a10b2e5e1d842c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/02/2019
ms.locfileid: "74691782"
---
# <a name="manage-windows-10-software-updates-in-intune"></a>Gestire gli aggiornamenti software di Windows 10 in Intune

Usare Intune per gestire l'installazione degli aggiornamenti software di Windows 10 da Windows Update per le aziende.

Tramite Windows Update for Business si semplifica l'esperienza di gestione degli aggiornamenti. Non è necessario approvare gli aggiornamenti singoli per i gruppi di dispositivi. È possibile gestire i rischi negli ambienti configurando una strategia di implementazione degli aggiornamenti. Intune offre la possibilità di [configurare le impostazioni di aggiornamento](windows-update-settings.md) sui dispositivi e di posticipare l'installazione degli aggiornamenti. È anche possibile impedire ai dispositivi di installare le funzionalità di nuove versioni di Windows per mantenerli stabili, consentendo al tempo stesso ai dispositivi di continuare a installare gli aggiornamenti per la qualità e la sicurezza.

Intune archivia solo le assegnazioni dei criteri di aggiornamento, non gli aggiornamenti. I dispositivi accedono direttamente a Windows Update per gli aggiornamenti.

Intune offre i tipi di criteri seguenti per gestire gli aggiornamenti:

- **Anello di aggiornamento di Windows 10**: Questi criteri sono una raccolta di impostazioni che viene configurata quando vengono installati gli aggiornamenti di Windows 10.

- **Aggiornamenti delle funzionalità di Windows 10 (anteprima pubblica)** : Questi criteri aggiornano i dispositivi alla versione di Windows specificata e bloccano il set di funzionalità nei dispositivi fino a quando non si sceglie di aggiornarli a una versione successiva di Windows.  Anche se la versione delle funzionalità rimane statica, i dispositivi possono continuare a installare gli aggiornamenti di qualità e sicurezza disponibili per la versione delle funzionalità.

I criteri per gli anelli di aggiornamento di Windows 10 e gli aggiornamenti delle funzionalità di Windows 10 vengono assegnati a gruppi di dispositivi. È possibile usare entrambi i tipi di criteri nello stesso ambiente di Intune per gestire gli aggiornamenti software per i dispositivi Windows 10 e per creare una strategia di aggiornamento che rispecchi le esigenze aziendali.

Per altre informazioni, vedere [Gestire gli aggiornamenti con Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

## <a name="prerequisites"></a>Prerequisiti

Per l'uso degli aggiornamenti di Windows per i dispositivi Windows 10 in Intune, è necessario siano soddisfatti i prerequisiti seguenti.

- I PC Windows 10 devono eseguire le versioni di Windows 10 seguenti:
  - **Anelli di aggiornamento di Windows 10**: versione 1607 o successiva
  - **Aggiornamenti delle funzionalità di Windows 10**: versione 1703 o successiva

- Windows Update supporta le edizioni di Windows 10 seguenti:
  - Windows 10
  - Windows 10 Team: per i dispositivi Surface Hub (non supporta gli *aggiornamenti delle funzionalità di Windows 10*)
  - Windows Holographic for Business

    Windows Holographic for Business supporta un subset di impostazioni per gli aggiornamenti di Windows, tra cui:
    - **Comportamento di aggiornamento automatico**
    - **Aggiornamenti ai prodotti Microsoft**
    - **Canale di manutenzione**: Supporta le opzioni **Canale semestrale** e **Canale semestrale (mirato)** . Per altre informazioni, vedere [Gestire Windows Holographic](../fundamentals/windows-holographic-for-business.md).

  > [!NOTE]
  > **Edizioni e versioni di Windows non supportate**:
  > - Windows 10 Mobile  
  > - Windows 10 Enterprise LTSC. Windows Update for Business (WUfB) attualmente non supporta le versioni *Long Term Service Channel*. Pianificare l'utilizzo di metodi di applicazione di patch alternativi, ad esempio WSUS o Configuration Manager.

- Nei dispositivi Windows, **Feedback e diagnostica** > **Dati di diagnostica e di utilizzo** deve essere impostato su **Base**, **Avanzato** o **Completo**.  

  È possibile configurare manualmente l'impostazione dei *dati di diagnostica e utilizzo* per i dispositivi Windows 10 oppure usare un profilo di restrizione dei dispositivi di Intune per Windows 10 e versioni successive. Se si usa un profilo di restrizione dei dispositivi, impostare la [restrizione dei dispositivi](../configuration/device-restrictions-windows-10.md#reporting-and-telemetry) **Condividi i dati di utilizzo** almeno su **Base**. Questa impostazione si trova nella categoria **Creazione di report e telemetria** quando si configura un criterio di restrizione dei dispositivi per Windows 10 o versione successiva.

  Per altre informazioni sui profili di dispositivo, vedere la pagina che spiega come [configurare le impostazioni di restrizione dei dispositivi](../configuration/device-restrictions-configure.md).

- Se si usa il portale di Azure classico, [eseguire la migrazione delle impostazioni nel portale di Azure](#migrate-update-settings-to-the-azure-portal).


## <a name="windows-10-update-rings"></a>Anelli di aggiornamento di Windows 10

Creare gli anelli di aggiornamento che specificano come e quando Windows as a Service aggiorna i dispositivi Windows 10 con aggiornamenti delle funzionalità e della qualità. In Windows 10 i nuovi aggiornamenti qualitativi e delle funzionalità includono il contenuto di tutti gli aggiornamenti precedenti. Se è stato installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 siano aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Gli anelli di aggiornamento di Windows 10 supportano i [tag di ambito](../fundamentals/scope-tags.md). È possibile usare i tag di ambito con gli anelli di aggiornamento per filtrare e gestire più facilmente i set di configurazioni in uso.

### <a name="create-and-assign-update-rings"></a>Creare e assegnare anelli di aggiornamento

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager]( https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Windows** > **Anelli di aggiornamento di Windows 10** > **Crea**.

3. In *Informazioni di base* specificare un nome, una descrizione (facoltativa) e quindi selezionare **Avanti**.
  ![Creare un anello di aggiornamento]( ./media/windows-update-for-business-configure/basics-tab.png)
  
4. In **Impostazioni per la fase di aggiornamento** configurare le impostazioni per le proprie esigenze aziendali. Per informazioni sulle impostazioni disponibili, vedere Impostazioni di aggiornamento di Windows. Dopo aver configurato le impostazioni *Aggiorna ed Esperienza utente* selezionare **Avanti**.

5. In **Tag di ambito** selezionare **+ Selezionare i tag di ambito** per aprire il riquadro *Selezionare i tag* per applicarli all'anello di aggiornamento. Scegliere uno o più tag, quindi fare clic su **Seleziona** per aggiungerli all'anello di aggiornamento e tornare alla pagina *Tag di ambito*.

   Quando si è pronti, selezionare **Avanti** per procedere ad *Assegnazioni*.

6. In **Assegnazioni** scegliere **+ Selezionare i gruppi da includere** e quindi assegnare l'anello di aggiornamento a uno o più gruppi. Usare **+ Selezionare i gruppi da escludere** per mettere a punto l'assegnazione. Selezionare **Avanti** per continuare.

7. In **Rivedi e crea** esaminare le impostazioni e selezionare **Crea** quando si è pronti per salvare l'anello di aggiornamento di Windows 10. Il nuovo anello di aggiornamento viene visualizzato nell'elenco degli anelli di aggiornamento.

### <a name="manage-your-windows-10-update-rings"></a>Gestire gli anelli di aggiornamento di Windows 10

Nel portale passare a **Dispositivi** > **Windows** > **Anelli di aggiornamento di Windows 10** e selezionare i criteri che si vuole gestire.  I criteri vengono aperti nella pagina **Panoramica**.

In questa pagina è possibile visualizzare lo stato di assegnazione degli anelli e selezionare le azioni seguenti nella parte superiore del riquadro Panoramica per la gestione dell'anello di aggiornamento:

- [Eliminazione](#delete)
- [Sospendi](#pause)
- [Riprendi](#resume)
- [Estendi](#extend)
- [Disinstalla](#uninstall)

![Operazioni disponibili](./media/windows-update-for-business-configure/overview-actions.png)

#### <a name="delete"></a>Eliminazione

Selezionare **Elimina** per arrestare l'applicazione delle impostazioni dell'anello di aggiornamento di Windows 10 selezionato. L'eliminazione di un anello rimuove la relativa configurazione da Intune, in modo che tali impostazioni non vengano più applicate.

L'eliminazione di un anello da Intune non modifica le impostazioni nei dispositivi cui è stato assegnato l'anello di aggiornamento.  Al contrario, il dispositivo mantiene le impostazioni correnti. I dispositivi non mantengono un record cronologico delle impostazioni precedenti. I dispositivi possono ricevere le impostazioni anche da anelli di aggiornamento aggiuntivi che rimangono attivi.

##### <a name="to-delete-a-ring"></a>Per eliminare un anello

1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento, selezionare **Elimina**.
2. Selezionare **OK**.

#### <a name="pause"></a>Sospendi

Selezionare **Sospendi** per impedire la ricezione di aggiornamenti qualitativi o delle funzionalità sui dispositivi per un periodo massimo di 35 giorni dall'inizio della sospensione dell'anello. Dopo che è trascorso il numero massimo di giorni, la funzionalità di sospensione scade automaticamente e il dispositivo esegue la ricerca degli aggiornamenti applicabili in Windows Update. Dopo questa ricerca, è possibile sospendere nuovamente gli aggiornamenti.
Se si ripristina un anello di aggiornamento sospeso e quindi si sospende di nuovo, il periodo di sospensione viene reimpostato su 35 giorni.

##### <a name="to-pause-a-ring"></a>Per sospendere un anello

1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento, selezionare **Sospendi**.
2. Selezionare **Funzionalità** o **Qualità** per definire il tipo di aggiornamento da sospendere e quindi selezionare **OK**.
3. Dopo la sospensione di un tipo di aggiornamento, è possibile selezionare di nuovo Sospendi per sospendere anche l'altro tipo.

Quando un tipo di aggiornamento viene sospeso, il riquadro Panoramica per tale anello mostra il numero di giorni che devono trascorrere prima del ripristino del tipo di aggiornamento.

> [!IMPORTANT]
> Dopo l'esecuzione di un comando Sospendi, i dispositivi ricevono tale comando al successivo controllo della disponibilità di aggiornamenti nel servizio. È quindi possibile che, prima di effettuare questo controllo, installino un aggiornamento pianificato. Inoltre, se un dispositivo è spento quando si esegue il comando di sospensione, all'accensione tale dispositivo potrebbe scaricare e installare gli aggiornamenti pianificati prima di controllare la disponibilità di nuovi aggiornamenti con Intune.

#### <a name="resume"></a>Riprendere

Quando un anello di aggiornamento è stato sospeso, è possibile selezionare **Riprendi** per ripristinare lo stato attivo degli aggiornamenti qualitativi e delle funzionalità per tale anello. Dopo aver ripristinato un anello di aggiornamento è possibile sospenderlo di nuovo.

##### <a name="to-resume-a-ring"></a>Per ripristinare un anello

1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento sospeso, selezionare **Riprendi**.
2. Tra le opzioni disponibili selezionare il tipo **Funzionalità** o **Qualità** per gli aggiornamenti da ripristinare e quindi selezionare **OK**.
3. Dopo il ripristino di un tipo di aggiornamento, è possibile selezionare di nuovo Riprendi per ripristinare anche l'altro tipo.

#### <a name="extend"></a>Extend  

Quando un anello di aggiornamento è sospeso, è possibile selezionare **Estendi** in modo da reimpostare su 35 giorni il periodo di sospensione per gli aggiornamenti qualitativi e delle funzionalità relativi a tale anello di aggiornamento.

##### <a name="to-extend-the-pause-period-for-a-ring"></a>Per estendere il periodo di sospensione per un anello

1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento sospeso, selezionare **Estendi**.
2. Tra le opzioni disponibili selezionare il tipo **Funzionalità** o **Qualità** per gli aggiornamenti da ripristinare e quindi selezionare **OK**.
3. Dopo aver esteso il periodo di sospensione per un tipo di aggiornamento, è possibile selezionare di nuovo Estendi per estendere l'altro tipo di aggiornamento.

#### <a name="uninstall"></a>Uninstall  

Un amministratore di Intune può usare il comando **Disinstalla** per disinstallare l'aggiornamento di tipo *Funzionalità* o *Qualità* più recente (eseguirne il rollback) per un anello di aggiornamento attivo o sospeso. Dopo aver disinstallato un tipo, è possibile disinstallare l'altro tipo. Intune non supporta né gestisce la capacità degli utenti di disinstallare gli aggiornamenti.  

> [!IMPORTANT]
> Quando si usa l'opzione *Disinstalla* , Intune passa immediatamente la richiesta di disinstallazione ai dispositivi.
>
> - I dispositivi Windows avviano la rimozione degli aggiornamenti non appena ricevono la modifica nei criteri di Intune. La rimozione degli aggiornamenti non si limita ai programmi di manutenzione, anche quando sono configurati come parte dell'anello di aggiornamento.
> - Se la rimozione degli aggiornamenti richiede il riavvio del dispositivo, il dispositivo viene riavviato senza offrire agli utenti del dispositivo la possibilità di ritardarlo.

Per una corretta disinstallazione è necessario che siano soddisfatti i requisiti seguenti:

- In un dispositivo deve essere in esecuzione l'aggiornamento di Windows 10 di aprile 2018 (1803) o una versione successiva.

In un dispositivo deve essere installato l'ultimo aggiornamento. Poiché gli aggiornamenti sono cumulativi, nei dispositivi in cui è installato l'ultimo aggiornamento deve essere presente l'aggiornamento qualitativo e delle funzionalità più recente. Questa opzione può ad esempio essere utile quando è necessario eseguire il rollback dell'ultimo aggiornamento perché è stato rilevato un problema rilevante nei computer Windows 10.

Quando si usa Disinstalla, prendere in considerazione i seguenti aspetti:

- La disinstallazione di un aggiornamento delle funzionalità o di un aggiornamento qualitativo è disponibile solo per il canale di manutenzione su cui è attivo il dispositivo.

- La disinstallazione di aggiornamenti qualitativi e delle funzionalità attiva i criteri per il ripristino dell'aggiornamento precedente nei computer Windows 10.

- In un dispositivo Windows 10, al termine del rollback di un aggiornamento qualitativo, gli utenti del dispositivo continuano a vedere l'aggiornamento elencato in **Impostazioni di Windows** > **Aggiornamenti** > **Cronologia degli aggiornamenti**.

- Per gli aggiornamenti delle funzionalità in particolare, il tempo per cui è possibile disinstallare l'aggiornamento è limitato a un periodo da 2 a 60 giorni. Questo periodo viene configurato tramite l'impostazione di aggiornamento degli anelli di aggiornamento **Configura il periodo di disinstallazione degli aggiornamenti delle funzionalità (da 2 a 60 giorni)** . Non è possibile eseguire il rollback di un aggiornamento delle funzionalità installato in un dispositivo dopo che l'aggiornamento è rimasto installato più a lungo del periodo di disinstallazione configurato.

  Si consideri ad esempio un anello di aggiornamento che ha un periodo di disinstallazione degli aggiornamenti delle funzionalità di 20 giorni. Dopo 25 giorni si decide di eseguire il rollback dell'aggiornamento delle funzionalità più recente e di usare l'opzione di disinstallazione.  I dispositivi che hanno installato l'aggiornamento delle funzionalità oltre 20 giorni prima non possono disinstallare l'aggiornamento perché sono stati rimossi i bit necessari come parte della manutenzione. I dispositivi che invece hanno installato l'aggiornamento delle funzionalità non oltre 19 giorni prima possono disinstallare l'aggiornamento, verificando di aver ricevuto il comando di disinstallazione prima di aver superato il periodo di disinstallazione di 20 giorni.

Per altre informazioni sui criteri di Windows Update, vedere [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (Provider del servizio di configurazione degli aggiornamenti) nella documentazione relativa alla gestione dei client di Windows.

##### <a name="to-uninstall-the-latest-windows-10-update"></a>Per disinstallare l'aggiornamento più recente di Windows 10

1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento sospeso, selezionare **Disinstalla**.
2. Tra le opzioni disponibili selezionare il tipo **Funzionalità** o **Qualità** per gli aggiornamenti da disinstallare e quindi selezionare **OK**.
3. Dopo aver attivato la disinstallazione di un tipo di aggiornamento, è possibile selezionare di nuovo Disinstalla per disinstallare l'altro tipo di aggiornamento.

## <a name="windows-10-feature-updates"></a>Aggiornamenti delle funzionalità di Windows 10

*Questa funzionalità è disponibile nella versione di anteprima pubblica.*

Con gli *aggiornamenti delle funzionalità di Windows 10*, è possibile selezionare la versione delle funzionalità di Windows da mantenere nei dispositivi, ad esempio Windows 10 versione 1803 o versione 1809. È possibile impostare un livello di funzionalità di 1803 o versione successiva.

Quando un dispositivo riceve i criteri di aggiornamento delle funzionalità di Windows 10:

- Il dispositivo viene aggiornato alla versione di Windows specificata nei criteri. Per un dispositivo che esegue già una versione successiva di Windows viene mantenuta la versione corrente. Con il blocco della versione, il set di funzionalità dei dispositivi rimane stabile per la durata dei criteri.

- Mentre la versione installata di Windows rimane impostata, i dispositivi possono comunque ricevere e installare aggiornamenti di qualità e sicurezza per la versione di Windows per la durata del supporto per la versione consentendo di mantenere i dispositivi aggiornati e protetti.

- Diversamente dall'uso di *Sospendi* con un anello di aggiornamento, che scade dopo 35 giorni, i criteri di aggiornamento delle funzionalità di Windows 10 restano attivi. I dispositivi non installano una nuova versione di Windows fino a quando non vengono modificati o rimossi i criteri di aggiornamento delle funzionalità di Windows 10. Se si modificano i criteri per specificare una versione più recente, i dispositivi potranno quindi installare le funzionalità della versione di Windows.

### <a name="limitations-for-windows-10-feature-updates"></a>Limitazioni per gli aggiornamenti delle funzionalità di Windows 10

- Quando si distribuiscono criteri di *aggiornamento delle funzionalità di Windows 10* in un dispositivo che riceve anche criteri *Fase di aggiornamento di Windows 10*, verificare nell'anello di aggiornamento le configurazioni seguenti:
  - **Periodo di differimento dell'aggiornamento delle funzionalità (giorni)** deve essere impostato su **0**.
  - Gli aggiornamenti delle funzionalità per l'anello di aggiornamento devono essere *in esecuzione*. Non devono essere sospesi.

- I criteri di aggiornamento delle funzionalità di Windows 10 non possono essere applicati durante la configurazione guidata e verranno applicati solo alla prima analisi del Windows Update dopo il completamento del provisioning di un dispositivo (in genere un giorno). Inoltre, i dispositivi di cui è stato effettuato il provisioning con Autopilot non riceveranno i criteri.

  Questa limitazione è in fase di esame per verificare se è possibile un supporto futuro.


### <a name="create-and-assign-windows-10-feature-updates"></a>Creare e assegnare gli aggiornamenti delle funzionalità di Windows 10

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Windows** > **Aggiornamenti delle funzionalità di Windows 10** > **Crea**.

3. In **Informazioni di base** specificare un nome, una descrizione (facoltativa) e per **Aggiornamento delle funzionalità da distribuire** selezionare la versione di Windows con il set di funzionalità desiderato e quindi selezionare **Avanti**.

4. In **Assegnazioni** scegliere **+ Selezionare i gruppi da includere** e quindi assegnare l'anello di aggiornamento a uno o più gruppi. Selezionare **Avanti** per continuare.

5. In **Rivedi e crea** esaminare le impostazioni e selezionare **Crea** quando si è pronti per salvare i criteri di aggiornamento delle funzionalità di Windows 10.  

### <a name="manage-windows-10-feature-updates"></a>Gestire gli aggiornamenti delle funzionalità di Windows 10

Nell'interfaccia di amministrazione passare a **Dispositivi** > **Windows** > **Aggiornamenti delle funzionalità di Windows 10** e selezionare i criteri che si vuole gestire. I criteri vengono aperti nella pagina **Panoramica**.

Da questa pagina è possibile effettuare le seguenti operazioni:

- Selezionare **Elimina** per eliminare i criteri da Intune e rimuoverli dai dispositivi.
- Selezionare **Proprietà** per modificare la distribuzione.  Nel riquadro *Proprietà* selezionare **Modifica** per aprire *Impostazioni di distribuzione o Assegnazioni* dove è possibile modificare la distribuzione.
- Selezionare **Stato di aggiornamento dell'utente finale** per visualizzare le informazioni relative ai criteri.

## <a name="migrate-update-settings-to-the-azure-portal"></a>Eseguire la migrazione delle impostazioni di aggiornamento nel portale di Azure

Il portale di Azure classico include anche un numero limitato di altre impostazioni per gli aggiornamenti di Windows 10 nel profilo di configurazione del dispositivo. Se una qualsiasi di queste impostazioni è configurata quando si esegue la migrazione al portale di Azure, è fortemente consigliata una delle azioni seguenti:

1. Creare gli anelli di aggiornamento di Windows 10 nel portale di Azure con le impostazioni necessarie. L'impostazione **Consenti funzionalità di versioni non definitive** non è supportata nel portale di Azure perché non è più applicabile alle build più recenti di Windows 10. È possibile configurare le altre tre impostazioni e quelle relative agli aggiornamenti di Windows 10 quando si creano gli anelli di aggiornamento.

   > [!NOTE]
   > Le impostazioni relative agli aggiornamenti di Windows 10 configurate nel portale classico non vengono visualizzate nel portale di Azure dopo la migrazione, Queste impostazioni vengono tuttavia applicate. Se si esegue la migrazione di una qualsiasi di queste impostazioni e si modificano i criteri migrati dal portale di Azure, l'impostazione viene rimossa dai criteri.

2. Eliminare le impostazioni di aggiornamento nel portale classico. Dopo aver eseguito la migrazione al portale di Azure e aver aggiunto le stesse impostazioni in un anello di aggiornamento, è necessario eliminare le impostazioni nel portale classico per evitare possibili conflitti di criteri. Ad esempio, si verifica un conflitto quando la stessa impostazione viene configurata con valori diversi. Non esiste un modo semplice per scoprire il motivo per cui l'impostazione configurata nel portale classico non viene visualizzata nel portale di Azure.

## <a name="next-steps"></a>Passaggi successivi

[Impostazioni di aggiornamento di Windows supportate da Intune](../windows-update-settings.md)

[Report di conformità di Intune per gli aggiornamenti](../windows-update-compliance-reports.md)

[Risoluzione dei problemi degli anelli di aggiornamento di Windows 10](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

