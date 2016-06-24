---
# required metadata

title: Gestire gli avvisi | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 74dc4ce4-21da-4f40-a07f-3eea34561eee

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gestire gli avvisi in Microsoft Intune
Usare l'area di lavoro **Avvisi** nella console di amministrazione di Intune per valutare l'integrità generale dei dispositivi nell'organizzazione e identificare i problemi.

#### Per visualizzare gli avvisi attivi

1.  Nella console di amministrazione di Intune eseguire una delle operazioni seguenti:

    -   **Per visualizzare informazioni generali sugli avvisi**, inclusi i tre avvisi principali e il numero totale di avvisi attivi, fare clic su **Panoramica sistema**. È possibile fare clic sui collegamenti in questi avvisi per visualizzare informazioni più dettagliate.

    -   **Per visualizzare i dati di riepilogo degli avvisi**, fare clic su **Avvisi &gt; Panoramica**. Nella pagina **Panoramica avvisi** l'area **Riepilogo del tipo di avviso** visualizza un riepilogo degli avvisi. Gli avvisi critici vengono visualizzati per primi. È possibile fare clic sui collegamenti in questi avvisi per visualizzare informazioni più dettagliate.

        > [!NOTE]
        > In alcuni casi, un tipo di avviso può essere visualizzato nell'elenco **Riepilogo del tipo di avviso** più di una volta.
        > 
        > Ad esempio, possono essere visualizzate nell'elenco le istanze seguenti del tipo di avviso Spazio logico libero su disco:
        > 
        > -   3 Spazio logico libero su disco
        > -   2 Spazio logico libero su disco
        > 
        > Questo comportamento si verifica quando viene generato lo stesso tipo di avviso per dispositivi in cui sono in esecuzione sistemi operativi diversi. Nell'esempio, la prima istanza del tipo di avviso Spazio logico libero su disco, 3 Spazio logico libero su disco, potrebbe essere stata generata da computer in cui è in esecuzione Windows® 7. La seconda istanza del tipo di avviso Spazio logico libero su disco potrebbe essere stata generata da computer in cui è in esecuzione Windows Vista®.

    -   **Per visualizzare tutti gli avvisi attivi**, fare clic su **Avvisi &gt; Tutti gli avvisi**. La pagina **Avvisi** visualizza l'elenco di tutti gli avvisi attivi, con le colonne seguenti:

        1.  **Nome** : il nome del tipo di avviso che ha generato l'avviso.

        2.  **Origine** : un collegamento all'origine dell'avviso. Se la soglia di visualizzazione del tipo di avviso è impostata su **Visualizza tutto**, in questo collegamento viene visualizzato un unico dispositivo. Se per la soglia di visualizzazione del tipo di avviso è stato impostato un valore, in questo collegamento viene visualizzato l'elenco di tutti i dispositivi che sono interessati dall'avviso.

        3.  **Ultimo aggiornamento**: indica l'ora dell'ultima modifica apportata all'avviso. Se un avviso è chiuso, viene visualizzata l'ora della chiusura.

        4.  **Gravità**: indica la gravità dell'avviso

## Visualizzazione degli avvisi in bacheca
Gli avvisi in bacheca forniscono importanti annunci di servizio, ad esempio un aggiornamento, la manutenzione o un'interruzione imminente. Usare questa procedura per visualizzare e gestire gli avvisi in bacheca.

#### Per visualizzare e gestire gli avvisi in bacheca

1.  Nella console di amministrazione di Intune fare clic su **Panoramica sistema**.

2.  Gli eventuali annunci di servizio importanti vengono visualizzati nell'area **Bacheca**.

3.  Se si vuole esportare un avviso in bacheca in un file con valori delimitati da virgole (.csv) o in un file HTML, fare clic su **Avvisi &gt; Tutti gli avvisi &gt; Notifiche**. Selezionare una notifica, fare clic sull'icona dell'elenco di esportazione e quindi seguire le istruzioni.

## Verifica degli stati di Intune
Nell'area di lavoro **Panoramica sistema** vengono visualizzati i riepiloghi sullo stato di sistema per Endpoint Protection, Aggiornamenti, Integrità agente, Criteri e Software, tramite i quali è possibile individuare i problemi e assegnare la priorità a quelli che richiedono attenzione immediata. Quando si verifica un'interruzione del sistema, viene specificato un collegamento al riepilogo **Stato del servizio** anche nei messaggi di errore. Il riepilogo **Stato del servizio** visualizza i dettagli relativi al problema in ogni posizione, oltre a indicare sempre quando è stato eseguito l'ultimo aggiornamento.

#### Per visualizzare lo stato della sottoscrizione

1.  Nella console di amministrazione di Intune fare clic su **Panoramica sistema**.

2.  Nell'area **Stato sistema** è possibile esaminare lo stato dei vari componenti di Microsoft Intune. Molti degli elementi contengono collegamenti che consentono di visualizzare altre informazioni. Ad esempio, quando si seleziona il numero di istanze in **Endpoint Protection** viene visualizzata l'area di lavoro **Endpoint Protection** contenente l'elenco del malware rilevato. Quando si seleziona il numero di dispositivi, viene visualizzata l'area di lavoro **Gruppi**, contenente l'elenco dei dispositivi in cui è stato rilevato malware.

## Chiusura e riattivazione di avvisi
Gli avvisi di Intune restano attivi fino a quando non si verifica uno degli eventi seguenti:

-   Il problema per il quale è stato generato l'avviso viene risolto.

-   L'avviso viene chiuso manualmente.

-   Passano 5 giorni dal momento della generazione dell'avviso. Dopo 45 giorni l'avviso scade e viene chiuso automaticamente.

Gli avvisi contrassegnati come chiusi vengono eliminati definitivamente dopo 90 giorni.

#### Per chiudere manualmente un avviso

1.  Nella console di amministrazione di Intune eseguire una delle operazioni seguenti:

    1.  **Per chiudere un avviso dall'elenco Avvisi**: fare clic su **Avvisi &gt; Tutti gli avvisi**. Selezionare un avviso e quindi fare clic su **Chiudi avviso**..

    2.  **Per chiudere un avviso per un dispositivo specifico**: fare clic su **Gruppi &gt; Tutti i dispositivi**. Selezionare un dispositivo e fare clic su **Visualizza proprietà**. Quindi, nella scheda **Avvisi** selezionare un avviso e fare clic su **Chiudi avviso**..

    3.  **Per chiudere un avviso in bacheca**: fare clic su **Panoramica sistema**. Fare clic sulla **X** accanto all'avviso in bacheca.

#### Per visualizzare e riattivare gli avvisi chiusi

1.  Nella console di amministrazione di Intune fare clic su **Avvisi &gt; Tutti gli avvisi**..

2.  Nell'elenco **Filtri** fare clic su **Chiuso**..

    Nel riquadro dell'elenco di gestione vengono visualizzati il nome e le informazioni aggiuntive relative agli avvisi. I dettagli relativi all'avviso selezionato vengono visualizzati nel riquadro di anteprima.

3.  Per riattivare l'avviso selezionato, fare clic su **Riattiva avviso**..

### Vedere anche
[Ricevere notifiche tramite gli avvisi di Microsoft Intune](get-notified-by-microsoft-intune-alerts.md)



<!--HONumber=May16_HO1-->


