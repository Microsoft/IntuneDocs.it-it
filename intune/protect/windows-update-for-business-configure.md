---
title: Configurare Windows Update for Business in Microsoft Intune - Azure | Microsoft Docs
description: Aggiornare le impostazioni di aggiornamento software in un profilo per la creazione di un anello di aggiornamento, esaminare la conformità e sospendere gli aggiornamenti in Windows Update for Business con Microsoft Intune nei dispositivi Windows 10.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: aa8cc396c05150006799c1e9b86ecb63351cdb36
ms.sourcegitcommit: 45d7c76e760c5117bf134fb57f7e248e5b6c4ad5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314710"
---
# <a name="manage-software-updates-in-intune"></a>Gestire gli aggiornamenti software in Intune

Usare Intune per definire gli anelli di aggiornamento che specificano come e quando Windows as a Service aggiorna i dispositivi Windows 10. Gli anelli di aggiornamento sono i criteri che vengono assegnati ai gruppi di dispositivi. Usando anelli di aggiornamento, è possibile creare una strategia di aggiornamento adatta alle esigenze aziendali. Per altre informazioni, vedere [Gestire gli aggiornamenti con Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

In Windows 10 i nuovi aggiornamenti qualitativi e delle funzionalità includono il contenuto di tutti gli aggiornamenti precedenti. Se è stato installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 siano aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.


Tramite Windows Update for Business si semplifica l'esperienza di gestione degli aggiornamenti. Non è necessario approvare gli aggiornamenti singoli per i gruppi di dispositivi. È possibile gestire i rischi negli ambienti configurando una strategia di implementazione degli aggiornamenti. Intune offre la possibilità di [configurare le impostazioni di aggiornamento](../windows-update-settings.md) sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. I dispositivi accedono direttamente a Windows Update per gli aggiornamenti. Questa raccolta di impostazioni che viene configurata quando vengono installati gli aggiornamenti di Windows 10 è definita *anello di aggiornamento di Windows 10*.

Gli anelli di aggiornamento di Windows 10 supportano i [tag di ambito](../fundamentals/scope-tags.md). È possibile usare i tag di ambito con gli anelli di aggiornamento per filtrare e gestire più facilmente i set di configurazioni in uso.

## <a name="prerequisites"></a>Prerequisiti  

Per l'uso degli aggiornamenti di Windows per i dispositivi Windows 10 in Intune, è necessario siano soddisfatti i prerequisiti seguenti.  

- I PC Windows 10 devono eseguire almeno Windows 10 Pro con l'aggiornamento dell'anniversario di Windows o versione successiva (1607 o successiva)
- Windows Update supporta le edizioni di Windows 10 seguenti:
  - Windows 10
  - Windows 10 Team (per dispositivi Surface Hub)
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


## <a name="create-and-assign-update-rings"></a>Creare e assegnare anelli di aggiornamento

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Selezionare **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10** > **Crea**.
4. Immettere un nome e una descrizione (facoltativo) e quindi fare clic su **Configura**.
5. In **Impostazioni** configurare le impostazioni in base alle esigenze aziendali. Per informazioni sulle impostazioni disponibili, vedere [Impostazioni di aggiornamento di Windows](../windows-update-settings.md).  
6. Al termine, selezionare **OK**. In **Crea l'anello di aggiornamento** selezionare **Crea**. Il nuovo anello di aggiornamento viene visualizzato nell'elenco degli anelli di aggiornamento.
7. Per assegnare l'anello, selezionarlo dall'elenco e nella scheda <\<nome anello> scegliere **Assegnazioni**.
8. Usare le schede **Includi** ed **Escludi** per definire i gruppi cui è assegnato l'anello, quindi selezionare **Salva** per completare l'assegnazione.

## <a name="manage-your-windows-10-update-rings"></a>Gestire gli anelli di aggiornamento di Windows 10
Nel portale è possibile selezionare un anello di aggiornamento Windows 10 per aprire il riquadro **Panoramica** corrispondente. In questo riquadro è possibile visualizzare lo stato di assegnazione degli anelli ed eseguire altre azioni per gestire l'anello. 
### <a name="to-view-an-updates-rings-overview-pane"></a>Per visualizzare un riquadro Panoramica degli anelli di aggiornamento: 
1. Accedere al portale di Azure.
2. Passare a **Intune** > **Aggiornamenti software** > **Anelli di aggiornamento di Windows 10**.
3. Selezionare l'anello di aggiornamento da visualizzare o gestire.  

Oltre a visualizzare lo stato di assegnazione, nella parte superiore del riquadro Panoramica è possibile selezionare le azioni seguenti per la gestione dell'anello di aggiornamento:  
- [Eliminazione](#delete)  
- [Sospendi](#pause)  
- [Riprendi](#resume)  
- [Estendi](#extend)  
- [Disinstalla](#uninstall)  

![Operazioni disponibili](./media/windows-update-for-business-configure/overview-actions.png)

### <a name="delete"></a>Eliminazione  
Selezionare **Elimina** per arrestare l'applicazione delle impostazioni dell'anello di aggiornamento di Windows 10 selezionato. L'eliminazione di un anello rimuove la relativa configurazione da Intune, in modo che tali impostazioni non vengano più applicate.  

L'eliminazione di un anello da Intune non modifica le impostazioni nei dispositivi cui è stato assegnato l'anello di aggiornamento.  Al contrario, il dispositivo mantiene le impostazioni correnti. I dispositivi non mantengono un record cronologico delle impostazioni precedenti. I dispositivi possono ricevere le impostazioni anche da anelli di aggiornamento aggiuntivi che rimangono attivi.  

#### <a name="to-delete-a-ring"></a>Per eliminare un anello  
1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento, selezionare **Elimina**.  
2. Selezionare **OK**.  

### <a name="pause"></a>Sospendi  
Selezionare **Sospendi** per impedire la ricezione di aggiornamenti qualitativi o delle funzionalità sui dispositivi per un periodo massimo di 35 giorni dall'inizio della sospensione dell'anello. Dopo che è trascorso il numero massimo di giorni, la funzionalità di sospensione scade automaticamente e il dispositivo esegue la ricerca degli aggiornamenti applicabili in Windows Update. Dopo questa ricerca, è possibile sospendere nuovamente gli aggiornamenti. Se si ripristina un anello di aggiornamento sospeso e quindi si sospende di nuovo, il periodo di sospensione viene reimpostato su 35 giorni.  

#### <a name="to-pause-a-ring"></a>Per sospendere un anello  
1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento, selezionare **Sospendi**.  
2. Selezionare **Funzionalità** o **Qualità** per definire il tipo di aggiornamento da sospendere e quindi selezionare **OK**.  
3. Dopo la sospensione di un tipo di aggiornamento, è possibile selezionare di nuovo Sospendi per sospendere anche l'altro tipo.  

Quando un tipo di aggiornamento viene sospeso, il riquadro Panoramica per tale anello mostra il numero di giorni che devono trascorrere prima del ripristino del tipo di aggiornamento.

> [!IMPORTANT]  
> Dopo l'esecuzione di un comando Sospendi, i dispositivi ricevono tale comando al successivo controllo della disponibilità di aggiornamenti nel servizio. È quindi possibile che, prima di effettuare questo controllo, installino un aggiornamento pianificato. Inoltre, se un dispositivo è spento quando si esegue il comando di sospensione, all'accensione tale dispositivo potrebbe scaricare e installare gli aggiornamenti pianificati prima di controllare la disponibilità di nuovi aggiornamenti con Intune.

### <a name="resume"></a>Riprendere  
Quando un anello di aggiornamento è stato sospeso, è possibile selezionare **Riprendi** per ripristinare lo stato attivo degli aggiornamenti qualitativi e delle funzionalità per tale anello. Dopo aver ripristinato un anello di aggiornamento è possibile sospenderlo di nuovo.  

#### <a name="to-resume-a-ring"></a>Per ripristinare un anello  
1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento sospeso, selezionare **Riprendi**.  
2. Tra le opzioni disponibili selezionare il tipo **Funzionalità** o **Qualità** per gli aggiornamenti da ripristinare e quindi selezionare **OK**.  
3. Dopo il ripristino di un tipo di aggiornamento, è possibile selezionare di nuovo Riprendi per ripristinare anche l'altro tipo.  

### <a name="extend"></a>Extend  
Quando un anello di aggiornamento è sospeso, è possibile selezionare **Estendi** in modo da reimpostare su 35 giorni il periodo di sospensione per gli aggiornamenti qualitativi e delle funzionalità relativi a tale anello di aggiornamento.  

#### <a name="to-extend-the-pause-period-for-a-ring"></a>Per estendere il periodo di sospensione per un anello  
1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento sospeso, selezionare **Estendi**. 
2. Tra le opzioni disponibili selezionare il tipo **Funzionalità** o **Qualità** per gli aggiornamenti da ripristinare e quindi selezionare **OK**.  
3. Dopo aver esteso il periodo di sospensione per un tipo di aggiornamento, è possibile selezionare di nuovo Estendi per estendere l'altro tipo di aggiornamento.  

### <a name="uninstall"></a>Uninstall  
Un amministratore di Intune può usare il comando **Disinstalla** per disinstallare l'aggiornamento di tipo *Funzionalità* o *Qualità* più recente (eseguirne il rollback) per un anello di aggiornamento attivo o sospeso. Dopo aver disinstallato un tipo, è possibile disinstallare l'altro tipo. Intune non supporta né gestisce la capacità degli utenti di disinstallare gli aggiornamenti.  

> [!IMPORTANT] 
> Quando si usa l'opzione *Disinstalla* , Intune passa immediatamente la richiesta di disinstallazione ai dispositivi. 
> - I dispositivi Windows avviano la rimozione degli aggiornamenti non appena ricevono la modifica nei criteri di Intune. La rimozione degli aggiornamenti non si limita ai programmi di manutenzione, anche quando sono configurati come parte dell'anello di aggiornamento. 
> - Se la rimozione degli aggiornamenti richiede il riavvio del dispositivo, il dispositivo viene riavviato senza offrire agli utenti del dispositivo la possibilità di ritardarlo.


Per una corretta disinstallazione è necessario che siano soddisfatti i requisiti seguenti:  
- In un dispositivo deve essere in esecuzione l'aggiornamento di Windows 10 di aprile 2018 (1803) o una versione successiva.  

In un dispositivo deve essere installato l'ultimo aggiornamento. Poiché gli aggiornamenti sono cumulativi, nei dispositivi in cui è installato l'ultimo aggiornamento deve essere presente l'aggiornamento qualitativo e delle funzionalità più recente. Questa opzione può ad esempio essere utile quando è necessario eseguire il rollback dell'ultimo aggiornamento perché è stato rilevato un problema rilevante nei computer Windows 10.  

Quando si usa Disinstalla, prendere in considerazione i seguenti aspetti:  
- La disinstallazione di un aggiornamento delle funzionalità o di un aggiornamento qualitativo è disponibile solo per il canale di manutenzione su cui è attivo il dispositivo.  

- La disinstallazione di aggiornamenti qualitativi e delle funzionalità attiva i criteri per il ripristino dell'aggiornamento precedente nei computer Windows 10.  

- In un dispositivo Windows 10, al termine del rollback di un aggiornamento qualitativo, gli utenti finali continuano a vedere l'aggiornamento elencato in **Impostazioni di Windows** > **Aggiornamenti** > **Cronologia degli aggiornamenti**.  

- Per gli aggiornamenti delle funzionalità in particolare, il periodo in cui è possibile disinstallare l'aggiornamento è limitato a un intervallo compreso tra 2 e 60 giorni, come definito dall'impostazione **Configura il periodo di disinstallazione degli aggiornamenti delle funzionalità (da 2 a 60 giorni)** per gli anelli di aggiornamento. Non è possibile eseguire il rollback di un aggiornamento delle funzionalità installato in un dispositivo dopo che questo è rimasto installato più a lungo del periodo di disinstallazione configurato.  

  Si consideri ad esempio un anello di aggiornamento che ha un periodo di disinstallazione degli aggiornamenti delle funzionalità di 20 giorni. Dopo 25 giorni si decide di eseguire il rollback dell'aggiornamento delle funzionalità più recente e di usare l'opzione di disinstallazione.  Nei dispositivi in cui l'aggiornamento delle funzionalità è installato da oltre 20 giorni non è possibile disinstallare l'aggiornamento perché sono stati rimossi i bit necessari nell'ambito della procedura di manutenzione. I dispositivi che invece hanno installato l'aggiornamento delle funzionalità non oltre 19 giorni prima possono disinstallare l'aggiornamento, verificando di aver ricevuto il comando di disinstallazione prima di aver superato il periodo di disinstallazione di 20 giorni.  

Per altre informazioni sui criteri di Windows Update, vedere [Update CSP](https://docs.microsoft.com/windows/client-management/mdm/update-csp) (Provider del servizio di configurazione degli aggiornamenti) nella documentazione relativa alla gestione dei client di Windows.  

#### <a name="to-uninstall-the-latest-windows-10-update"></a>Per disinstallare l'aggiornamento più recente di Windows 10  
1. Quando è visualizzata la pagina di panoramica per un anello di aggiornamento sospeso, selezionare **Disinstalla**.  
2. Tra le opzioni disponibili selezionare il tipo **Funzionalità** o **Qualità** per gli aggiornamenti da disinstallare e quindi selezionare **OK**.  
3. Dopo aver attivato la disinstallazione di un tipo di aggiornamento, è possibile selezionare di nuovo Disinstalla per disinstallare l'altro tipo di aggiornamento.  

## <a name="migrate-update-settings-to-the-azure-portal"></a>Eseguire la migrazione delle impostazioni di aggiornamento nel portale di Azure  
Il portale di Azure classico include anche un numero limitato di altre impostazioni per gli aggiornamenti di Windows 10 nel profilo di configurazione del dispositivo. Se una qualsiasi di queste impostazioni è configurata quando si esegue la migrazione al portale di Azure, è fortemente consigliata una delle azioni seguenti:  

1. Creare gli anelli di aggiornamento di Windows 10 nel portale di Azure con le impostazioni necessarie. L'impostazione **Consenti funzionalità di versioni non definitive** non è supportata nel portale di Azure perché non è più applicabile alle build più recenti di Windows 10. È possibile configurare le altre tre impostazioni, e anche quelle relative agli aggiornamenti di Windows 10, quando si creano gli anelli aggiornamento.  

   > [!NOTE]  
   > Le impostazioni relative agli aggiornamenti di Windows 10 configurate nel portale classico non vengono visualizzate nel portale di Azure dopo la migrazione, Queste impostazioni vengono tuttavia applicate. Se si esegue la migrazione di una qualsiasi di queste impostazioni e si modificano i criteri migrati dal portale di Azure, l'impostazione viene rimossa dai criteri.  

2. Eliminare le impostazioni di aggiornamento nel portale classico. Dopo aver eseguito la migrazione al portale di Azure e aver aggiunto le stesse impostazioni in un anello di aggiornamento, è necessario eliminare le impostazioni nel portale classico per evitare possibili conflitti di criteri. Quando, ad esempio, la stessa impostazione viene configurata con valori diversi, si verifica un conflitto. Non esiste un modo semplice per scoprire il motivo per cui l'impostazione configurata nel portale classico non viene visualizzata nel portale di Azure.  

## <a name="next-steps"></a>Passaggi successivi
[Impostazioni di aggiornamento di Windows supportate da Intune](../windows-update-settings.md)  

[Report di conformità di Intune per gli aggiornamenti](../windows-update-compliance-reports.md)

[Risoluzione dei problemi degli anelli di aggiornamento di Windows 10](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-Windows-10-Update-Ring-Policies/ba-p/714046)

