---
title: Aggiornamenti software per PC Windows | Documentazione Microsoft
description: "Intune consente di tenere aggiornati i computer garantendo l&quot;installazione veloce delle patch e degli aggiornamenti software più recenti."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 48e9c41a-d2de-424e-9610-cfd1ad514210
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7d1760a10e63233fe7cc7f6fd57a68c5283647c
ms.openlocfilehash: 14ef9f901969449ca8b3c60a187da6b6e654bd67


---

# <a name="keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune"></a>Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune
Microsoft Intune consente di proteggere i computer gestiti in diversi modi, ad esempio con la gestione degli aggiornamenti software, che consente di mantenere i computer aggiornati installando rapidamente le patch e gli aggiornamenti software più recenti.

Se il client Intune non è ancora stato installato nei computer, vedere [Install the Windows PC client with Microsoft Intune (Installare il client PC Windows con Microsoft Intune)](install-the-windows-pc-client-with-microsoft-intune.md).

Quando sono disponibili nuovi aggiornamenti da Microsoft Update applicabili ai computer gestiti oppure è stato creato un aggiornamento di terze parti, nella pagina **Panoramica** dell'area di lavoro **Aggiornamenti** viene visualizzata una notifica. Dopo aver scelto il collegamento della notifica è possibile eseguire varie operazioni, ad esempio visualizzare altre informazioni sull'aggiornamento, accettare o rifiutare l'aggiornamento e visualizzare i computer in cui verrà installato, se approvato.

> [!IMPORTANT]
> L'area di lavoro **Aggiornamenti** non viene visualizzata nella console di amministrazione finché non si installa il client e si gestisce correttamente almeno un client del computer.

Mentre gli aggiornamenti vengono approvati e installati, è possibile verificare il risultato dell'installazione nell'area di lavoro **Aggiornamenti** della console di Intune.

Le sezioni seguenti consentono di mantenere aggiornato il software sui computer gestiti.

## <a name="before-you-start"></a>Prima di iniziare
Prima di iniziare a creare e approvare degli aggiornamenti software, configurare e distribuire ai computer dei criteri che controllino come e quando gli aggiornamenti vengono installati.

### <a name="to-configure-update-policy-settings"></a>Per configurare le impostazioni dei criteri di aggiornamento

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Criteri** &gt; **Panoramica** &gt; **Aggiungi criterio**.

2.  Configurare e distribuire un criterio di **Impostazioni agente di Microsoft Intune** per le impostazioni di aggiornamento. È possibile usare le impostazioni consigliate o personalizzare le impostazioni. Per altre informazioni su come creare e distribuire i criteri, vedere [Attività comuni di gestione di PC Windows con client di Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).

La tabella seguente mostra i valori che possono essere configurati nei criteri e i valori consigliati che vengono usati se i criteri non vengono personalizzati. È possibile trovare queste impostazioni nella sezione **Aggiornamenti** .

  |Impostazione criterio|Dettagli|
    |------------------|--------------------|
    |**Frequenza rilevamento aggiornamenti e applicazioni (ore)** |Specifica la frequenza (da 8 a 22 ore) con cui Intune verifica la disponibilità di nuovi aggiornamenti e applicazioni.<br /><br />Impostazione consigliata: **8** ore.|
    |**Installazione automatica o richiesta di aggiornamenti e applicazioni** |Specifica se gli aggiornamenti vengono installati automaticamente o se viene chiesto all'utente prima dell'installazione. Tale impostazione consente inoltre di pianificare l'installazione degli aggiornamenti e delle applicazioni.<br /><br />**Installa gli aggiornamenti e le applicazioni automaticamente come pianificato** installa aggiornamenti e applicazioni in base alla pianificazione specificata.<br /><br />L'impostazione del criterio dipendente **Utilizzare la manutenzione automatica per i computer Windows**  specifica se installare aggiornamenti e applicazioni come parte della funzionalità di manutenzione automatica di Windows.<br /><br />**Chiedi all'utente prima di installare** consente di chiedere conferma all'utente prima di installare gli aggiornamenti disponibili.<br /><br />Valori consigliati:<br /><br />Opzione **Installa gli aggiornamenti e le applicazioni automaticamente come pianificato** selezionata<br /><br />**Giorno pianificato: Ogni giorno**<br /><br />**Ora pianificata: 3.00**<br /><br />Opzione **Utilizzare la manutenzione automatica per i computer Windows** selezionata|
    |**Installazione immediata di aggiornamenti che non interrompono Windows** |**Consenti** installa gli aggiornamenti immediatamente dopo il download, ad eccezione degli aggiornamenti che causano l'interruzione o il riavvio di Windows. Gli aggiornamenti vengono installati in base alla configurazione dell'impostazione **Installazione automatica o richiesta di aggiornamenti** .<br /><br />**Non consentire** installa gli aggiornamenti in base alla configurazione dell'impostazione **Installazione automatica o richiesta di aggiornamenti e applicazioni**.<br /><br />Impostazione consigliata: **Consenti** |
    |**Posticipa il riavvio di Windows dopo l'installazione di applicazioni e aggiornamenti pianificati (minuti)** |Specifica (da 1 a 30 minuti) il tempo di attesa per riavviare Windows dopo l'installazione delle applicazioni e degli aggiornamenti pianificati.<br /><br />Impostazione consigliata: **15 minuti** |
    |**Ritardo dopo il riavvio di Windows per l'installazione di applicazioni e aggiornamenti pianificati non completati (minuti)** |Specifica (da 1 a 60 minuti) il tempo atteso per l'installazione degli aggiornamenti e delle applicazioni dopo il riavvio di Windows quando un aggiornamento pianificato non è stato completato.<br /><br />Impostazione consigliata: **5 minuti**|
    |**Consenti all'utente connesso di controllare il riavvio di Windows dopo l'installazione di aggiornamenti pianificati** |Specifica se l'utente connesso può posticipare il riavvio di Windows (se impostata su **Sì**) o se riceverà una notifica del riavvio automatico di Windows (se impostata su **No**). Se, tuttavia, nessun utente è connesso al termine dell'installazione pianificata di aggiornamenti e applicazioni, Windows verrà riavviato automaticamente, se necessario. Se l'impostazione è configurata su **No**, per impostazione predefinita, il periodo di tempo atteso prima che venga riavviato Windows è impostato su 5 minuti.<br /><br />Impostazione consigliata: **Sì**|
    |**Chiedi all'utente di riavviare Windows durante gli aggiornamenti obbligatori dell'agente client di Microsoft Intune** |Questa impostazione consente di determinare se viene chiesto agli utenti connessi di riavviare Windows quando è necessario farlo in seguito a un aggiornamento obbligatorio del client di Intune.<br /><br />Impostazione consigliata: **Sì**|
    |**Pianificazione delle installazioni degli aggiornamenti obbligatori dell'agente client di Microsoft Intune** |Consente di pianificare l'installazione degli aggiornamenti del client.<br /><br />Valore consigliato: non configurato|
    |**Ritardo tra le richieste di riavviare Windows dopo l'installazione di applicazioni e aggiornamenti pianificati (minuti)** |Questa impostazione consente di specificare la frequenza (da 1 a 1440 minuti) con cui l'utente riceve la richiesta di riavviare Windows quando viene installato un aggiornamento pianificato o un'applicazione che richiede il riavvio di Windows e l'utente decide di posticipare il riavvio.<br /><br />Impostazione consigliata: **30 minuti** |

## <a name="update-software-made-by-microsoft"></a>Aggiornare il software Microsoft
L'aggiornamento del software Microsoft richiede un intervento minimo da parte dell'utente. Tuttavia, prima di iniziare, è necessario configurare:

-   **Categorie di prodotti e classificazioni degli aggiornamenti** : consente di definire le categorie e le classificazioni degli aggiornamenti che si desidera rendere disponibili ai computer. Ad esempio, si può scegliere di installare solo gli aggiornamenti critici per Microsoft Office.

-   **Regole di approvazione automatica** : queste regole consentono di approvare automaticamente specifici tipi di aggiornamento e ridurre in questo modo il sovraccarico amministrativo. Ad esempio, si può scegliere di approvare automaticamente tutti gli aggiornamenti software critici.

Usare le due procedure seguenti per usare gli aggiornamenti software:

### <a name="configure-the-product-categories-and-update-classifications-you-want-to-make-available-to-managed-computers"></a>Configurare le categorie di prodotti e le classificazioni degli aggiornamenti che si desidera rendere disponibili ai computer gestiti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Amministrazione**&gt;**Aggiornamenti**.

2.  Nella pagina **Impostazioni servizio: aggiornamenti** , nell'elenco **Categoria prodotto** , selezionare le categorie di aggiornamenti da rendere disponibili per i computer. Si noti che gli aggiornamenti più comuni sono selezionati per impostazione predefinita.

    > [!IMPORTANT]
    > Per garantire che i computer ricevano gli aggiornamenti approvati dall'amministratore nell'impostazione dei criteri di gruppo di Windows Server Update Services (WSUS), l'impostazione **Specifica il percorso del servizio di aggiornamento Microsoft nella rete Intranet** non deve essere applicata ai computer che sono stati registrati con Intune.

3.  Nell'elenco **Classificazione aggiornamento** , selezionare le classificazioni di aggiornamento che si desidera rendere disponibili ai computer gestiti. Le opzioni più comuni sono selezionate per impostazione predefinita.

4.  Scegliere **Salva** per memorizzare le selezioni.

### <a name="to-configure-automatic-approval-rules-for-software-updates"></a>Per configurare le regole di approvazione automatica degli aggiornamenti software

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Amministrazione**&gt;**Aggiornamenti**.

2.  Nella sezione **Regole di approvazione automatica** della pagina **Impostazioni server: aggiornamenti** scegliere **Nuovo**.

3.  Nella pagina **Generale** della procedura guidata Crea regola di approvazione automatica, digitare il nome della nuova regola di approvazione automatica ed eventualmente una descrizione.

4.  Nella pagina **Categorie prodotti** , selezionare i prodotti per cui si desidera approvare automaticamente gli aggiornamenti.

5.  Nella pagina **Classificazioni di aggiornamento** specificare le classificazioni di aggiornamento che si desidera vengano approvate automaticamente.

6.  Nella pagina **Distribuzione** , eseguire le seguenti operazioni:

    -   Selezionare il gruppo di computer a cui distribuire la nuova regola, quindi scegliere **Aggiungi**.

    -   Per specificare una scadenza di installazione degli aggiornamenti, selezionare la casella di controllo **Imporre una scadenza per l'installazione di questi aggiornamenti** , quindi selezionare la scadenza dell'installazione nell'elenco **Scadenza dell'installazione** .

        > [!NOTE]
        > Se si specifica una scadenza di installazione, potrebbe essere necessario riavviare il computer gestito una o più volte dopo che l'intervallo di scadenza è trascorso.

    -   Al termine, scegliere **Avanti**.

7.  Nella pagina **Riepilogo** rivedere le impostazioni della nuova regola, quindi scegliere **Fine**.

La nuova regola viene mostrata nella sezione **Regole di approvazione automatica** della pagina **Impostazioni servizio: aggiornamenti** .

> [!NOTE]
> Quando si crea una regola di approvazione automatica, verranno approvati soltanto gli aggiornamenti futuri e non quelli precedenti che esistono già in Intune. Per approvare gli aggiornamenti è necessario eseguire la regola di approvazione automatica.


### <a name="to-edit-run-or-delete-an-automatically-approved-update-rule"></a>Per modificare, eseguire o eliminare una regola di approvazione automatica degli aggiornamenti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Amministrazione**&gt;**Aggiornamenti**.

2.  Nella sezione **Regole di approvazione automatica** , selezionare una regola e quindi eseguire una delle seguenti operazioni:

    -   Per modificare la regola, scegliere **Modifica**, quindi modificare i parametri della regola nella **procedura guidata Aggiorna regola di approvazione automatica**.

    -   Per eseguire la regola scegliere **Esegui selezione**.

    -   Per eliminare la regola scegliere **Elimina**.

        > [!NOTE]
        > L'eliminazione di una regola non influisce sugli aggiornamenti precedenti approvati da tale regola eliminata.

## <a name="update-software-not-made-by-microsoft"></a>Aggiornare software non Microsoft
È possibile distribuire gli aggiornamenti per il software non Microsoft. A questo scopo, usare la procedura guidata **Caricamento aggiornamento** per copiare l'aggiornamento nello spazio di memorizzazione nel cloud, dopo di che è possibile approvare o rifiutare l'aggiornamento nello stesso modo usato per il software Microsoft.

### <a name="to-upload-and-configure-a-third-party-update"></a>Per caricare e configurare un aggiornamento di terze parti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Aggiornamenti** &gt; **Panoramica** &gt; **Carica**.

2.  Nella pagina **File di aggiornamento** scegliere **Sfoglia** per selezionare i file di installazione necessari per installare il pacchetto di aggiornamento. Il file potrebbe essere un file di Windows Installer (MSI), un file di correzione di Windows Installer (MSP) o un file di programma con estensione EXE. È inoltre possibile includere qualsiasi file o cartelle aggiuntivi presenti nella stessa cartella del file di installazione.

    Verranno visualizzate le dimensioni totali dei file selezionati per il caricamento, escludendo le dimensioni non compresse o espanse dei file di installazione.

3.  Dopo aver specificato i file di installazione, nella pagina **Descrizione aggiornamento** verranno visualizzati il nome, la descrizione e la classificazione delle informazioni sul software, estratti tramite Intune dai file di installazione del software stesso. È possibile selezionare una classificazione per definire il tipo di aggiornamento da distribuire (aggiornamenti, aggiornamenti critici, aggiornamenti della sicurezza, aggiornamenti cumulativi o Service Pack). Al termine, scegliere **Avanti**.

4.  Nella pagina **Requisiti** della procedura guidata scegliere l'architettura (a 32 bit, a 64 bit o entrambe) e i sistemi operativi dei computer gestiti ai quali è applicabile l'aggiornamento.

5.  Nella pagina **Regole di rilevamento** è possibile specificare in che modo Intune stabilisce se l'aggiornamento è già presente nei computer gestiti. Se si seleziona l'opzione predefinita **Usa le regole di rilevamento predefinite** Intune installa sempre una volta il pacchetto di aggiornamento in ogni computer di destinazione.

    > [!NOTE]
    > Se il file di installazione dell'aggiornamento specificato è un file di Windows Installer o un file MSP, la pagina **Regole di rilevamento** della procedura guidata non verrà visualizzata. Questo si verifica perché i file di Windows Installer e MSP contengono istruzioni proprie per il rilevamento di precedenti installazioni degli aggiornamenti.

    Selezionare una o più delle seguenti regole per stabilire se l'aggiornamento è già installato nei computer gestiti:

    -   **File esistente**

    -   **Codice prodotto MSI esistente**

    -   **Chiave del Registro di sistema esistente**

6.  Specificare qualsiasi altra informazione necessaria per configurare la regola di rilevamento, ad esempio il nome e il percorso di un file, il codice prodotto Windows Installer o una chiave del Registro di sistema, quindi scegliere **Avanti**.

7.  Nella pagina **Prerequisiti** della procedura guidata, specificare il software da installare prima che possa essere installato l'aggiornamento. È possibile specificare **Nessuno** e selezionare un pacchetto software che è già stato aggiunto a Intune ed è gestito da Intune stesso. Oppure è possibile specificare una delle seguenti regole per descrivere il software:

    -   **File esistente**

    -   **Codice prodotto MSI esistente**

    -   **Chiave del Registro di sistema esistente**

8.  Specificare qualsiasi altra informazione necessaria per configurare la regola di rilevamento, ad esempio il nome e il percorso di un file, il codice prodotto Windows Installer o una chiave del Registro di sistema, quindi scegliere **Avanti**.

9. Nella pagina **Argomenti della riga di comando** della procedura guidata, è possibile aggiungere eventuali altre proprietà di installazione alla riga di comando di installazione per modificare il comportamento del file di installazione. Ad esempio, alcuni software supportano la proprietà **/q** per abilitare l'installazione invisibile all'utente. Per altre informazioni sugli argomenti della riga di comando supportati, vedere la documentazione del proprio pacchetto software. Specificare eventuali argomenti della riga di comando necessari, quindi scegliere **Avanti**.

    > [!NOTE]
    > Se l'aggiornamento non supporta la modalità di installazione invisibile all'utente, non sarà possibile installarlo tramite Intune.

10. Nella pagina **Codici restituiti** della procedura guidata, è possibile specificare come vengono interpretati i codici restituiti dall'installazione dell'aggiornamento. Per impostazione predefinita, Intune usa i codici restituiti standard del settore per segnalare un'installazione corretta o non riuscita di un pacchetto di aggiornamenti. I codici restituiti forniti sono:

|Codice restituito|Dettagli|
|---------------|------------------|
|**0**|Operazione completata|
|**3010**|Operazione completata con riavvio|

11. Eventuali codici restituiti non presenti nell'elenco rappresentano errori.
Alcuni aggiornamenti usano interpretazioni non standard per i codici restituiti. In questo caso, è possibile specificare interpretazioni proprie del codice restituito.

12. Specificare o modificare i codici restituiti necessari, quindi scegliere **Avanti**.

13. Nella pagina **Riepilogo** della procedura guidata, esaminare le azioni che verranno eseguite, quindi scegliere **Carica** per completare la procedura guidata.

L'aggiornamento caricato viene archiviato nella memoria cloud di Intune. Se lo spazio disponibile non è sufficiente per caricare il pacchetto di aggiornamento, si riceverà una notifica durante il processo di caricamento. Intune non è in grado di stabilire se lo spazio disponibile è sufficiente fino al momento dell'avvio del caricamento, poiché i file di installazione compressi richiedono una quantità di spazio maggiore quando vengono decompressi.

Una volta caricato in Intune, un aggiornamento di terze parti viene visualizzato nell'area di lavoro **Aggiornamenti** nel riquadro **Tutti gli aggiornamenti**. È possibile quindi approvare e distribuire l'aggiornamento. Per altre informazioni, vedere la sezione "Approvare e rifiutare gli aggiornamenti".

## <a name="approve-and-decline-updates"></a>Approvare e rifiutare gli aggiornamenti
Quando gli aggiornamenti sono pronti per essere installati, un messaggio viene visualizzato sulla pagina **Panoramica aggiornamenti** dell'area di lavoro **Aggiornamenti** , in corrispondenza di **Stato aggiornamento**. Scegliere questo messaggio per aprire la pagina **Tutti gli aggiornamenti** e verificare quali aggiornamenti sono pronti per l'approvazione.

È possibile usare l'elenco **Filtri** per semplificare la ricerca degli aggiornamenti. Ad esempio, è possibile visualizzare solo gli aggiornamenti non riusciti o gli aggiornamenti sostituiti.

Quando si seleziona un aggiornamento dall'elenco, sono disponibili ulteriori comandi che consentono di gestire gli aggiornamenti, come illustrato nella tabella riportata di seguito:

|Attività|Dettagli|
|--------|--------------------|
|**Visualizza proprietà**|Visualizza informazioni dettagliate sull'aggiornamento, incluso il numero di computer a cui è applicabile.|
|**Modifica**|Solo per gli aggiornamenti non Microsoft. Consente di modificare le proprietà dell'aggiornamento.|
|**Approva**|Approva l'aggiornamento selezionato e consente di configurare i gruppi a cui sarà distribuito. Per altre informazioni, vedere la procedura **Per approvare gli aggiornamenti** in questo argomento.|
|**Rifiuta**|Rimuove tutte le approvazioni precedenti per l'aggiornamento e nasconde l'aggiornamento dalle visualizzazioni predefinite. Inoltre, l'opzione rimuove tutti i dati di report per l'aggiornamento.<br /><br />Se si desidera individuare un aggiornamento rifiutato in un secondo tempo, impostare il filtro su **Rifiutato** nella pagina **Tutti gli aggiornamenti**. È possibile quindi approvare questo aggiornamento come obbligatorio.<br /><br />Se un aggiornamento è stato rifiutato perché è scaduto in Microsoft Update, l'aggiornamento non può essere approvato nella console di amministrazione di Intune.<br /><br />Se si elimina un criterio Aggiornamenti distribuito nei computer, le impostazioni del criterio Aggiornamenti vengono reimpostate sullo stato predefinito per il sistema operativo installato nei computer.|
|**Eliminazione**|Solo per gli aggiornamenti non Microsoft. Elimina l'aggiornamento selezionato.|
|**Carica**|Avvia la procedura guidata **Caricamento aggiornamento** che consente di caricare gli aggiornamenti non Microsoft da distribuire.|

### <a name="to-approve-updates"></a>Per approvare gli aggiornamenti

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Aggiornamenti** &gt; **Panoramica** &gt; **Nuovi aggiornamenti da approvare**.

    Nell'area di lavoro **Aggiornamenti** scegliere **Panoramica** &gt; **Nuovi aggiornamenti da approvare**.

    > [!NOTE]
    > Il collegamento **Nuovi aggiornamenti da approvare** verrà visualizzato nell'area **Stato aggiornamento** solo se è presente almeno un computer gestito per il quale è necessario approvare un aggiornamento.

2.  Selezionare un aggiornamento, esaminarne le proprietà nella parte inferiore della pagina per confermare che si vuole approvare l'aggiornamento, quindi scegliere **Approva**. È possibile selezionare più aggiornamenti tenendo premuto **CTRL** mentre si selezionano i singoli elementi.

3.  Nella pagina **Seleziona gruppi**, selezionare un gruppo a cui si vogliono distribuire gli aggiornamenti, quindi scegliere **Aggiungi**. Dopo aver specificato i gruppi scegliere **Avanti**.

4.  Nella pagina **Azione di distribuzione** attenersi alla seguente procedura per ciascun gruppo nell'elenco:

    -   Nell'elenco **Approvazione** , selezionare una delle seguenti opzioni:

        -   **Installazione richiesta**: installa l'aggiornamento nei computer del gruppo specificato.

        -   **Non installare**: indica solo l'applicabilità e non installa l'aggiornamento.

        -   **Installazione disponibile** consente all'utente di installare l'applicazione su richiesta dal portale aziendale.

        -   **Disinstalla**: rimuove gli aggiornamenti dai computer nel gruppo di destinazione.

            > [!IMPORTANT]
            > L'aggiornamento viene rimosso anche se non è stato installato da Intune.

    -   Nell'elenco **Scadenza** , selezionare una delle seguenti opzioni:

        -   **Nessuno**: indica che non viene applicata alcuna scadenza per l'installazione dell'aggiornamento e che gli utenti possono rifiutare continuativamente l'aggiornamento.

        -   **Appena possibile**: installa l'aggiornamento appena possibile in tutti i computer di destinazione.

        -   **Personalizzato**: specifica la data e l'ora per l'installazione degli aggiornamenti approvati.

        -   **Una settimana**, **Due settimane**, **Un mese** consentono di installare l'aggiornamento entro il periodo di tempo specificato.

5.  Scegliere **Fine** per salvare le impostazioni o **Annulla** per annullare le impostazioni e tornare all'elenco degli aggiornamenti.

    > [!IMPORTANT]
    > A meno che per un gruppo figlio non sia stata esplicitamente configurata l'azione **Non installare**, **Installazione richiesta**o **Disinstalla** , un'azione configurata per un gruppo padre verrà ereditata da tutti i relativi gruppi figlio.

6.  È possibile controllare il riquadro dei dettagli nella parte inferiore della pagina **Tutti gli aggiornamenti** per i messaggi di promemoria sull'aggiornamento.


### <a name="see-also"></a>Vedere anche
[Criteri per la protezione dei PC Windows](policies-to-protect-windows-pcs-in-microsoft-intune.md)



<!--HONumber=Dec16_HO5-->


