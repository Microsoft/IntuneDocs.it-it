---
title: Endpoint Protection per i PC Windows
titlesuffix: Microsoft Intune
description: Proteggere i computer gestiti con Endpoint Protection, che fornisce protezione in tempo reale contro minacce malware.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 002241bf-6cd0-4c75-a4f0-891ac7e6721a
ms.reviewer: damionw
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.openlocfilehash: 05cc1971f107c7bc3da371de0a916149c879aae0
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187124"
---
# <a name="help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune"></a>Proteggere i PC Windows con Endpoint Protection per Microsoft Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Microsoft Intune consente di proteggere i computer gestiti con Endpoint Protection che offre protezione in tempo reale contro potenziali minacce di tipo malware, mantenendo aggiornate le definizioni dei malware ed eseguendo analisi automatiche dei computer. Endpoint Protection fornisce inoltre strumenti che consentono di gestire e monitorare gli attacchi malware.

Se il client Intune non è ancora stato installato nei computer, vedere [Install the Windows PC client with Microsoft Intune (Installare il client PC Windows con Microsoft Intune)](install-the-windows-pc-client-with-microsoft-intune.md).

Usare le informazioni delle sezioni seguenti per configurare, distribuire e monitorare Endpoint Protection.

## <a name="choose-when-to-use-endpoint-protection"></a>Quando usare Endpoint Protection
Come amministratore IT, mantenere i computer gestiti privi di virus e malware è una delle priorità più importanti. Prima di distribuire Intune ai PC Windows aziendali, è necessario decidere come proteggerli selezionando una delle opzioni seguenti e configurando le impostazioni dei criteri associate:


|                                                                                                                                                                       Per:                                                                                                                                                                        |                                                                                                       Impostazioni dei criteri di Endpoint Protection                                                                                                        |                                                                                                                                                  Altre informazioni                                                                                                                                                  |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                             Installare Microsoft Intune Endpoint Protection solo se non è stata installata alcuna applicazione di terze parti per la protezione degli endpoint.<br /><br />È possibile usare Microsoft Intune Endpoint Protection in tutti i computer in cui non è installata alcuna applicazione di terze parti per la protezione degli endpoint.                                              | Installa Endpoint Protection = <strong>Sì</strong><br /><br />Abilita Endpoint Protection = <strong>Sì</strong><br /><br />Installa Endpoint Protection anche se è installata un'applicazione di terze parti per la protezione degli endpoint = <strong>No</strong>  |                                                                      Se viene rilevata un'applicazione di terze parti per la protezione degli endpoint, Microsoft Intune Endpoint Protection non verrà installato e verrà disinstallato se è stato installato in precedenza.                                                                       |
| Usare Microsoft Intune Endpoint Protection anche se è stata installata un'applicazione di terze parti per la protezione degli endpoint.<br /><br />Con questo approccio, Microsoft Intune Endpoint Protection e l'applicazione di terze parti per la protezione degli endpoint verranno eseguiti contemporaneamente. A causa di potenziali problemi di prestazioni, questa configurazione non è consigliata. | Installa Endpoint Protection = <strong>Sì</strong><br /><br />Abilita Endpoint Protection = <strong>Sì</strong><br /><br />Installa Endpoint Protection anche se è installata un'applicazione di terze parti per la protezione degli endpoint = <strong>Sì</strong> |                        Usare quando:<br /><br />- Si vuole passare all'uso di Microsoft Intune Endpoint Protection.<br />- Viene distribuito un nuovo client che usa Microsoft Intune Endpoint Protection.<br />- Viene aggiornato un client che usa Microsoft Intune Endpoint Protection.                         |
|                                                                                                             Usare Intune senza Microsoft Intune Endpoint Protection. Si utilizzerà invece un'applicazione Endpoint Protection di terze parti.                                                                                                             |                                                                                                Installa Endpoint Protection = <strong>No</strong>                                                                                                 | Se non si usa un'applicazione di protezione degli endpoint di terze parti, questa configurazione non è consigliata perché potrebbe esporre i computer aziendali a malware o altri attacchi.<br /><br />Microsoft Intune Endpoint Protection non viene installato e se è stato installato in precedenza verrà disinstallato. |

Per passare dall'applicazione di protezione degli endpoint corrente a Microsoft Intune Endpoint Protection, eseguire le operazioni seguenti:

1.  Lasciare l'applicazione di protezione degli endpoint in esecuzione durante la distribuzione del software client di Intune nei computer.

2.  Verificare che Microsoft Intune Endpoint Protection sia installato e funzioni correttamente per proteggere i computer client.

3.  Rimuovere il software Endpoint Protection di terze parti in uno dei seguenti modi:

    -   Tramite la distribuzione del software di Intune, distribuire uno strumento di rimozione software offerto dal produttore dell'applicazione di protezione degli endpoint di terze parti. Per altre informazioni, vedere [Deploy apps in Microsoft Intune (Distribuire app in Microsoft Intune)](apps-deploy.md).

    -   Tramite la rimozione manuale dell'applicazione Endpoint Protection di terze parti.

> [!NOTE]
> Intune non eseguirà automaticamente la disinstallazione delle applicazioni di protezione degli endopoint di terze parti.

## <a name="configure-microsoft-intune-endpoint-protection"></a>Configurare Microsoft Intune Endpoint Protection
Attenersi alla procedura seguente per configurare Endpoint Protection per Microsoft Intune.

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) fare clic su **Criteri** > **Aggiungi criterio**.

2.  Espandere **Gestione Computer** e quindi selezionare **Impostazioni agente di Microsoft Intune**. Selezionare **Creare e distribuire criteri personalizzati** per specificare criteri per le impostazioni di Endpoint Protection. Scegliere quindi il pulsante **Crea criterio**.

È possibile usare le impostazioni consigliate o personalizzare le impostazioni. Per altre informazioni su come creare e distribuire i criteri, vedere l'argomento [Attività comuni di gestione di PC Windows con client di Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

  ![Impostazioni di Endpoint Protection](media/pol-sa-pc-endpoint-policy.png)

È possibile visualizzare i criteri di Endpoint Protection distribuiti nella pagina **Tutti i criteri** dell'area di lavoro **Criteri**.

## <a name="specify-endpoint-protection-service-settings"></a>Specificare le impostazioni del servizio Endpoint Protection

|                                                 Impostazione criterio                                                  |                                                                                                                                                                                                                                                                                                                                                                                                             Dettagli                                                                                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                  <strong>Installa Endpoint Protection</strong>                                   | Impostare su <strong>Sì</strong> per installare Endpoint Protection nei computer gestiti. Se durante l'installazione viene rilevata un'applicazione di protezione endpoint di terze parti, Endpoint Protection non verrà installato, a meno che l'opzione <strong>Installa Endpoint Protection anche se è installata un'applicazione Endpoint Protection di terze parti</strong> non sia impostata su <strong>Sì</strong>. <strong>Nota</strong>: Intune Endpoint Protection è installato nei computer gestiti per impostazione predefinita. Se non si vuole installare Endpoint Protection nei computer gestiti, impostare questo criterio in modo esplicito su <strong>No</strong>. Se Endpoint Protection è stato installato precedentemente e il criterio è stato aggiornato impostandolo su <strong>No</strong>, il client di Endpoint Protection verrà disinstallato.<br />Impostazione consigliata: <strong>Sì</strong> |
| <strong>Installa Endpoint Protection anche se è installata un'applicazione Endpoint Protection di terze parti</strong> |                                                                                                                                                                                                                                                                                                                Impostare su <strong>Sì</strong> per installare Microsoft Intune Endpoint Protection anche se è stata rilevata un'applicazione di terze parti per la protezione degli endpoint.<br /><br />Impostazione consigliata: <strong>Sì</strong>                                                                                                                                                                                                                                                                                                                |
|                                   <strong>Abilita Endpoint Protection</strong>                                   |                                                                                                                                                                                                            Impostare su <strong>Sì</strong> per abilitare Microsoft Intune Endpoint Protection nei computer in cui è presente il client Endpoint Protection.<br /><br />Se il criterio viene impostato su <strong>No</strong> e se è stato installato Microsoft Intune Endpoint Protection, l'interfaccia utente del client di Endpoint Protection non verrà visualizzata agli utenti e tutte le funzionalità di protezione risulteranno inattive.<br /><br />Impostazione consigliata: <strong>Sì</strong>                                                                                                                                                                                                             |
|                                       <strong>Disattiva interfaccia utente client</strong>                                        |                                                                                                                                                                                                                                                                                                      Impostare su <strong>Sì</strong> per nascondere l'interfaccia utente del client di Endpoint Protection. Sarà necessario riavviare il computer client perché la modifica abbia effetto.<br /><br />Impostazione consigliata: <strong>No</strong>                                                                                                                                                                                                                                                                                                       |
| <strong>Installa Endpoint Protection anche se è installata un'applicazione Endpoint Protection di terze parti</strong> |                                                                                                                                                                                                                                                                                                       Impostare su <strong>Sì</strong> per forzare l'installazione di Microsoft Intune Endpoint Protection, anche se è stata rilevata un'applicazione di terze parti per la protezione degli endpoint.<br /><br />Impostazione consigliata: <strong>No</strong>                                                                                                                                                                                                                                                                                                       |
|                    <strong>Crea un punto di ripristino del sistema prima della rimozione del malware</strong>                    |                                                                                                                                                                                                                                                                                                                                 Impostare su <strong>Sì</strong> per creare un punto di ripristino del sistema Windows prima di iniziare qualsiasi correzione di malware.<br /><br />Impostazione consigliata: <strong>Sì</strong>                                                                                                                                                                                                                                                                                                                                  |
|                                 <strong>Rileva malware risolto (giorni)</strong>                                  |                                                                                                                                                                                                                                                                                      Consente a Endpoint Protection di rilevare il malware risolto per un periodo di tempo specificato in modo da controllare manualmente i computer precedentemente infetti.<br /><br />È possibile specificare un valore qualsiasi compreso tra 0 e 30 giorni.<br /><br />Impostazione consigliata: <strong>7 giorni</strong>                                                                                                                                                                                                                                                                                       |

Se si impostano i valori dei criteri per le opzioni **Installa Endpoint Protection** e **Abilita Endpoint Protection** su **Sì** e il valore del criterio **Installa Endpoint Protection anche se è installata un'applicazione Endpoint Protection di terze parti** su **No**, Microsoft Intune Endpoint Protection rileva la presenza di un'altra applicazione di protezione degli endpoint installata. Ciò significa che Endpoint Protection non verrà installato o verrà disinstallato se è già presente. Tuttavia, Microsoft Intune Endpoint Protection genera un report sull'integrità dell'altra applicazione di protezione degli endpoint in Intune.

  Microsoft Security Essentials avvisa l'utente con la funzionalità di protezione in tempo reale quando minacce potenziali, ad esempio virus e spyware, stanno per essere installate o eseguite nel PC. Nel momento in cui ciò si verifica, viene visualizzato un messaggio nell'area di notifica sul lato destro della barra delle applicazioni.

### <a name="specify-real-time-protection-settings"></a>Specificare le impostazioni di protezione in tempo reale

|Impostazione criterio|Dettagli|
|------------------|--------------------|
|**Abilita protezione in tempo reale**|Abilita il monitoraggio e l'analisi di tutti i file e di tutte le applicazioni a cui si accede. Consente inoltre di bloccare eventuali file e applicazioni dannosi prima che vengano eseguiti nei computer.<br /><br />Impostazione consigliata: **Sì**|
|**Analizza tutti i download**|Abilita l'analisi di tutti i file e di tutti gli allegati che vengono scaricati da Internet nei computer.<br /><br />Impostazione consigliata: **Sì**|
|**Monitorizza attività di file e programmi nei computer**|Consente il monitoraggio dei file in ingresso e in uscita, nonché delle attività dei programmi sui computer. Con questa impostazione, Endpoint Protection è in grado di monitorare quando vengono eseguiti file e programmi nonché di notificare l'utente in merito alle operazioni relative a questi file e programmi.<br /><br />Impostazione consigliata: **Sì**|
|**File monitorati**|Consente di scegliere se monitorare solo i file in ingresso, quelli in uscita o tutti.<br /><br />Impostazione consigliata: **Monitora tutti i file**|
|**Abilita monitoraggio del comportamento**|Consente a Microsoft Intune Endpoint Protection di verificare la presenza di alcuni modelli di attività sospette nei computer client.<br /><br />Impostazione consigliata: **Sì**|
|**Abilita Network Inspection System**|Abilita Network Inspection System (NIS) nei computer client. Con NIS vengono usate firme di vulnerabilità note ottenute da [Microsoft Malware Protection Center](https://go.microsoft.com/fwlink/?LinkId=234249) per rilevare e bloccare il traffico di rete dannoso.<br /><br />Impostazione consigliata: **Sì**|

  ![Impostazioni in tempo reale per Endpoint Protection](media/pol-sa-pc-policy-realtime.png)

### <a name="specify-scan-schedule-settings"></a>Specificare le impostazioni di pianificazione dell'analisi

|Impostazione criterio|Altre informazioni|
|------------------|--------------------|
|**Pianifica analisi veloce giornaliera**|Pianifica un'analisi veloce giornaliera dei file usati di frequente e di importanti file di sistema sui computer. Questa analisi veloce ha un effetto minimo sulle prestazioni.<br /><br />Impostazione consigliata: **Sì**|
|**Esegui un'analisi veloce se sono state saltate due analisi veloci consecutive**|Configura Endpoint Protection per eseguire automaticamente un'analisi veloce dei computer che hanno saltato le analisi veloci per due volte consecutive.<br /><br />Impostazione consigliata: **Sì**|
|**Pianifica un'analisi completa**|Consente di configurare un'analisi completa di tutti i file e di tutte le risorse nei dischi rigidi locali dei computer locali. A seconda del numero di file e risorse da analizzare, questa analisi potrebbe richiedere tempo e influire sulle prestazioni del computer.<br /><br />Impostazione consigliata: **No**|
|**Esegui un'analisi completa se sono state saltate due analisi complete consecutive**|Configura Endpoint Protection per eseguire automaticamente un'analisi completa dei computer che hanno saltato l'analisi per due volte consecutive.<br /><br />Valore consigliato: Non configurata|

### <a name="specify-scan-options-settings"></a>Specificare le impostazioni per le opzioni di analisi

|Impostazione criterio|Dettagli|
|------------------|--------------------|
|**Esegui analisi completa dopo l'installazione di Endpoint Protection**|Impostare su **Sì** per consentire a Endpoint Protection di eseguire automaticamente un'analisi completa del sistema dopo l'installazione nei computer. Per ridurre l'effetto sulla produttività degli utenti, questa analisi viene eseguita solo quando i computer sono inattivi.<br /><br />Impostazione consigliata: **Sì**|
|**Se necessario, esegui automaticamente un'analisi completa per completare la rimozione di malware**|Impostare su **Sì** per consentire a Endpoint Protection di eseguire automaticamente un'analisi completa del sistema nei computer dopo la rimozione di malware per verificare che altri file non siano stati interessati.<br /><br />Impostazione consigliata: **Sì**|
|**Avvia un'analisi pianificata solo quando il computer è inattivo**|Impostare su **Sì** per impedire l'avvio di analisi pianificate quando i computer sono in uso ed evitare così una perdita di produttività dell'utente.<br /><br />Impostazione consigliata: **Sì**|
|**Prima di avviare un'analisi, controllare di disporre delle definizioni malware più recenti**|Impostare su **Sì** per consentire a Endpoint Protection di verificare automaticamente le definizioni dei malware più recenti prima di iniziare la scansione dei computer.<br /><br />Impostazione consigliata: **Sì**|
|**Analizza file di archivio**|Impostare su **Sì** per configurare Endpoint Protection in modo che esegua la scansione alla ricerca di malware nei file di archivio, ad esempio file con estensione zip o cab, nei computer.<br /><br />Impostazione consigliata: **No**|
|**Analisi dei messaggi di posta elettronica**|Impostare su **Sì** per configurare Endpoint Protection in modo che analizzi i messaggi di posta elettronica quando vengono ricevuti nei computer.<br /><br />Impostazione consigliata: **Sì**|
|**Analizza file aperti da cartelle di rete condivise**|Impostare su **Sì** per configurare Endpoint Protection in modo che analizzi i file aperti da cartelle condivise in rete. Generalmente si tratta di file accessibili tramite un percorso UNC (Universal Naming Convention). L'abilitazione di questa funzionalità può causare problemi agli utenti che dispongono di accesso in sola lettura poiché gli utenti non sono in grado di rimuovere il malware.<br /><br />Impostazione consigliata: **No**|
|**Analizza unità di rete mappate**|Impostare su **Sì** per configurare Endpoint Protection per l'analisi dei file nelle unità di rete mappate. L'abilitazione di questa funzionalità può causare problemi agli utenti che dispongono di accesso in sola lettura poiché gli utenti non sono in grado di rimuovere il malware.<br /><br />Impostazione consigliata: **No**|
|**Analizza unità rimovibili**|Impostare su **Sì** per configurare Endpoint Protection in modo che esegua la scansione alla ricerca di malware e software indesiderato nel contenuto delle unità rimovibili, ad esempio le unità flash USB, durante l'esecuzione di un'analisi completa dei computer.<br /><br />Impostazione consigliata: **Sì**|
|**Limita utilizzo CPU durante un'analisi a**|Impostare la percentuale massima di utilizzo della CPU durante le analisi pianificate dei computer. È possibile impostare questo valore da 1 a 100%.<br /><br />Impostazione consigliata: **50%**|

### <a name="choose-default-actions-settings"></a>Scegliere le impostazioni delle azioni predefinite

L'impostazione **Scegliere l'azione eseguita da Endpoint Protection sul malware con i seguenti livelli di attenzione** specifica l'azione predefinita eseguita da Endpoint Protection quando viene rilevato malware di vari livelli di attenzione. Per ogni livello di attenzione, è possibile rimuovere il malware, metterlo in quarantena o intraprendere le azioni consigliate di Microsoft.

Valore consigliato: **Azione consigliata** che consente a Endpoint Protection di consigliare l'azione.   

### <a name="decide-whether-to-choose-the-excluded-files-and-folders-settings"></a>Decidere se scegliere le impostazioni per escludere file e cartelle

L'impostazione **File e cartelle da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale** consente di escludere cartelle o file specifici durante un'analisi o quando si usa la protezione in tempo reale nei computer.

### <a name="decide-whether-to-choose-the-excluded-processes-settings"></a>Decidere se scegliere le impostazioni per escludere processi

L'impostazione **Processi da escludere quando si esegue un'analisi o si usa la protezione in tempo reale** consente di escludere processi specifici quando si esegue un'analisi o si usa la protezione in tempo reale nei computer. È possibile escludere solo i file con le estensioni seguenti: **exe**, **com** o **scr**.

### <a name="decide-whether-to-choose-the-excluded-file-types-settings"></a>Decidere se scegliere le impostazioni per escludere tipi di file

L'impostazione **Estensioni di file da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale** consente di escludere estensioni di file specifiche quando si esegue un'analisi o si usa la protezione in tempo reale nei computer.

### <a name="specify-microsoft-active-protection-service-settings"></a>Specificare le impostazioni di Microsoft Active Protection Service
Microsoft Active Protection Service è una comunità online che fornisce informazioni utili per decidere come rispondere a potenziali rischi. La comunità contribuisce inoltre ad arrestare la diffusione di nuove infezioni di malware. È possibile abilitare **Partecipa a Microsoft Active Protection Service** selezionando **Sì** e quindi specificando il **Livello di appartenenza**:
  - **Base**: invia a Microsoft informazioni di base sul malware rilevato. Le informazioni includono la provenienza del software, le azioni applicate dall'utente o automaticamente da Endpoint Protection e l'eventuale riuscita di tali azioni.
  - **Avanzato**: invia a Microsoft altre informazioni su malware, spyware e software potenzialmente indesiderato. Le informazioni includeranno il percorso del software, i nomi dei file, il funzionamento del software e gli effetti sul computer.

È possibile anche attivare l'opzione **Ricevi definizioni dinamiche in base ai report di Microsoft Active Protection Service**.

## <a name="choose-management-tasks-for-endpoint-protection"></a>Scegliere le attività di gestione per Endpoint Protection
Le attività seguenti consentono di eseguire varie operazioni di gestione sui computer gestiti che eseguono Endpoint Protection:
- Aggiorna definizioni malware
  - Console di Intune: dall'area di lavoro **Gruppi** selezionare i computer da aggiornare. Scegliere **Attività remote** &gt; **Aggiorna definizioni malware**.
  - Computer gestiti: avviare il software client di Endpoint Protection dall'area di notifica di Windows. Scegliere la scheda **Aggiornamento** e quindi **Aggiorna**.
- Eseguire un'analisi di malware:
  - Console di Intune: dall'area di lavoro **Gruppi** selezionare i computer da analizzare. Scegliere **Esegui un'analisi completa di malware** oppure **Esegui un'analisi rapida di malware**.
  - Computer gestiti: avviare il software client di Endpoint Protection dall'area di notifica di Windows. Selezionare **Veloce**, **Completa** oppure **Personalizzata** e quindi scegliere **Avvia analisi**.

Per visualizzare lo stato di un'attività remota, scegliere il collegamento **Attività remote** nell'angolo inferiore destro della console di Intune. La finestra di dialogo **Stato attività in remoto** elenca le attività remote correnti, il relativo stato, il nome del dispositivo e gli eventuali errori segnalati. Include inoltre un collegamento a informazioni per la risoluzione dei problemi, se appropriato.

## <a name="monitor-endpoint-protection"></a>Monitorare Endpoint Protection
È possibile monitorare lo stato del malware nei computer usando l'area di lavoro **Protezione** della [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/). Quest'area di lavoro contiene due pagine:
- **Panoramica Endpoint Protection**: visualizza i problemi importanti come collegamenti che è possibile scegliere per accedere ad altre informazioni. I problemi che potrebbero essere visualizzati includono:
  - **Istanze di malware che richiedono completamento**: fare clic sul collegamento per visualizzare un elenco di problemi malware, incluse le azioni da intraprendere per risolverli. È possibile esplorare ulteriormente questo elenco per visualizzare i computer interessati.
  - **Computer con malware che richiedono completamento**: fare clic sul collegamento per visualizzare tutti i computer che presentano problemi malware non risolti, oltre alle azioni da intraprendere per risolverli.
  - **Dispositivi non protetti**: fare clic sul collegamento per visualizzare tutti i computer che non sono protetti da un qualsiasi software di protezione degli endpoint perché non è installato alcun software o perché si è verificato un errore. Selezionare un computer per visualizzare ulteriori dettagli.
  - **Dispositivi che eseguono un'altra applicazione di protezione degli endpoint**: fare clic sul collegamento per visualizzare i computer che eseguono un'applicazione di terze parti per la protezione degli endpoint.
- **Tutti i malware**: consente di visualizzare un elenco di tutti i malware attivi trovati nei computer. È possibile esplorare l'elenco per visualizzare tutti i computer in cui è presente un malware particolare oppure è possibile selezionare una delle attività seguenti:
  - **Visualizza proprietà**: apre una pagina con altre informazioni sul malware selezionato.
  - **Informazioni sul malware**: apre un argomento di Microsoft Malware Protection Center che contiene altre informazioni sul malware.

> [!IMPORTANT]
> L'area di lavoro **Protezione** non viene visualizzata nella console di amministrazione finché non si installa il client e si gestisce almeno un client del computer.

  ![Monitorare Endpoint Protection](media/pol-sa-ep-monitor.png)

### <a name="how-to-view-recent-detection-paths-for-malware-on-computers"></a>Come visualizzare recenti percorsi di rilevamento di malware nel computer.
Intune consente di visualizzare i percorsi per fino a 10 istanze di malware rilevate più di recente in un dispositivo. Il **recente rilevamento percorso** è disabilitato per impostazione predefinita. Per abilitare questa visualizzazione:

1. Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** > **Tutti i dispositivi** > **Tutti i computer**.
2. Fare clic con il pulsante destro del mouse sul computer di cui si vuole visualizzare i recenti percorsi di rilevamento e selezionare **Proprietà**.
3. Selezionare **Malware** tra le schede visualizzate nella parte superiore.

   ![Selezionare la scheda Malware e quindi fare clic sulla casella di controllo Percorsi di rilevamento recenti.](media/malware-path-column.png)
4. Fare clic con il pulsante destro del mouse sull'intestazione di colonna. Verrà visualizzato un elenco delle colonne disponibili. Selezionare la casella di controllo **Percorsi di rilevamento recenti** nell'elenco. Viene visualizza la colonna **Percorsi di rilevamento recenti** che riporta fino a 10 delle istanze di malware monitorate più di recente nel dispositivo.

## <a name="run-a-malware-scan-or-update-malware-definitions-on-a-computer"></a>Eseguire un'analisi del malware o aggiornare le definizioni di malware in un computer
Intune consente di eseguire un'analisi completa o veloce del malware usando Endpoint Protection o Windows Defender in un PC gestito in remoto in cui è installato il client Intune.

1. Nella [console di amministrazione Microsoft Intune](https://manage.microsoft.com/) passare a **Gruppi** > **Panoramica** > **Tutti i dispositivi** > **Tutti i computer** e quindi selezionare il computer di destinazione.

2. Scegliere l'elenco a discesa **Attività remote** e quindi selezionare l'attività da eseguire nel computer remoto.

## <a name="need-more-help"></a>Ulteriore assistenza?
Per altre informazioni e supporto, vedere [Troubleshoot Endpoint Protection in Microsoft Intune (Risoluzione dei problemi di Endpoint Protection in Microsoft Intune)](troubleshoot-endpoint-protection-in-microsoft-intune.md).

### <a name="see-also"></a>Vedere anche
[Criteri per la protezione dei PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)
