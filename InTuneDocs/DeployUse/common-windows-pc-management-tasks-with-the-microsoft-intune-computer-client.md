---
# required metadata

title: Attività comuni di gestione di PC Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: eb912c73-54d2-4d78-ac34-3cbe825804c7

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Attività comuni di gestione di PC Windows con client di Microsoft Intune
Leggere le attività descritte in questo argomento per informazioni sulla gestione dei computer che eseguono il client Intune. Se il client Intune non è ancora stato installato nei computer, vedere [Installare il client PC Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md)..


## Usare i criteri per semplificare la gestione dei PC
### Gestire Windows Firewall
L'utilizzo di criteri consente di semplificare l'amministrazione delle impostazioni di Windows Firewall sui computer gestiti. Per i dettagli, vedere [Proteggere i PC Windows con criteri di Windows Firewall in Microsoft Intune](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md).

### Gestire Microsoft Intune Center
Microsoft Intune Center consente agli utenti di:

-   Ottenere applicazioni dal portale aziendale.

-   Verificare la disponibilità di aggiornamenti.

-   Gestire Microsoft Intune Endpoint Protection.

-   Richiedere assistenza remota.

Microsoft Intune Center viene installato su tutti i computer gestiti. È possibile configurare le seguenti impostazioni in un criterio di Intune e visualizzarle in Microsoft Intune Center:

|Impostazione criterio|Dettagli|
|------------------|--------------------|
|**Nome**|Il nome dell'amministratore che gestisce il computer.<br /><br />Lunghezza massima: 40 caratteri|
|**Numero di telefono**|Il numero di telefono dell'amministratore che gestisce il computer.<br /><br />Lunghezza massima: 20 caratteri|
|**Indirizzo di posta elettronica**|L'indirizzo di posta elettronica dell'amministratore che gestisce il computer.<br /><br />Lunghezza massima: 40 caratteri|
|**Nome sito Web**|Il nome del sito Web di supporto per gli utenti.<br /><br />Lunghezza massima: 40 caratteri|
|**URL sito Web**|L'URL del sito Web di supporto.<br /><br />Lunghezza massima: 150 caratteri|
|**Note**|Una nota che viene visualizzata agli utenti.<br /><br />Lunghezza massima: 120 caratteri|

### Gestire le impostazioni degli aggiornamenti software
Usare criteri per configurare le impostazioni usate dai computer gestiti per cercare e scaricare gli aggiornamenti software di Microsoft e di terze parti. Per altre informazioni, vedere [Mantenere i PC Windows aggiornati con gli aggiornamenti software in Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)..

### Gestire le impostazioni di Endpoint Protection
Usare criteri per configurare le impostazioni per Endpoint Protection da distribuire successivamente ai computer gestiti. I criteri includono le analisi pianificate e le azioni da intraprendere quando viene rilevato malware. Per altre informazioni, vedere [Proteggere i PC Windows con Endpoint Protection per Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)..

## Visualizzare l'inventario hardware e software
Intune raccoglie informazioni dettagliate sull'hardware e sul software dei computer gestiti. Le informazioni delle seguenti procedure consentono di:

-   Creare un report che elenca le informazioni sulle funzionalità hardware dei computer.

-   Creare un report che elenca il software installato in ciascun computer.

-   Aggiornare un inventario di computer per garantire che i dati nel report sia correnti.

### Visualizzare le informazioni sui computer

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Report** &gt; **Report inventario computer**.

2.  Nella pagina **Crea nuovo report** , accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report solo i computer che eseguono Windows 8.1.

3.  Fare clic su **Visualizza rapporto** per aprire il **Report inventario computer** in una nuova finestra.

    È possibile ordinare il report in base a qualsiasi colonna, ad esempio **Nome**, **Tipo di chassis** o **Produttore** selezionando l'intestazione della colonna.

### Per visualizzare il software installato nei computer

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Rapporti** &gt; **Report software rilevato**.

2.  Nella pagina **Crea nuovo report** , accettare i valori predefiniti oppure personalizzarli per filtrare i risultati che verranno restituiti nel report. Ad esempio, è possibile scegliere di visualizzare nel report solo il software pubblicato da Microsoft.

3.  Scegliere **Visualizza rapporto** per aprire il **Report software rilevato** in una nuova finestra.

    È possibile ordinare il report in base a qualsiasi colonna, ad esempio **Nome**, **Autore** o **Categoria** selezionando ogni intestazione di colonna. È possibile espandere gli aggiornamenti nell'elenco per visualizzare maggiori dettagli, ad esempio i computer in cui gli aggiornamenti sono installati, facendo clic sulla freccia direzionale accanto alla voce dell'elenco.

### Per aggiornare l'inventario dei computer per accertarsi che sia aggiornato

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il computer di cui si vuole aggiornare l'inventario.

2.  Selezionare un computer oppure tenere premuto **CTRL** per selezionare più computer.

3.  Sulla barra delle applicazioni, scegliere **Attività remote** &gt; **Aggiorna inventario**..

4.  Per visualizzare lo stato dell'attività, scegliere il collegamento **Attività remote** nell'angolo inferiore destro della pagina.

    Nella finestra di dialogo **Stato attività** sono elencate le attività remote correnti, il relativo stato, il nome del dispositivo e gli eventuali errori segnalati, nonché un collegamento per consultare le informazioni sulla risoluzione dei problemi.


## Riavviare in remoto un PC Windows

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il computer da riavviare.

2.  Selezionare uno o più computer, quindi scegliere **Attività remote** &gt; **Riavvia il computer**..

3.  Per visualizzare lo stato dell'attività, scegliere il collegamento **Attività remote** nell'angolo inferiore destro della pagina.

4.  Nella finestra di dialogo **Stato attività** , rivedere le attività remote correnti, il relativo stato, il nome del dispositivo e gli eventuali errori segnalati.

## Ritirare un computer

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il computer da ritirare.

2.  Selezionare i dispositivi da ritirare, quindi scegliere **Disattiva/Cancella**..

Per registrare nuovamente un computer in Intune, reinstallare il software client nel computer seguendo la procedura descritta nell'argomento [Installare il client PC Windows con Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Se un computer non è in grado di connettersi a Intune, viene visualizzato un messaggio nell'area di lavoro **Dashboard** .

Quando si ritira un computer:

-   Il computer viene rimosso dall'inventario di Intune e la licenza associata al computer viene resa disponibile per essere riusata.

-   Lo stato del computer non viene più visualizzato nella console di Intune.

-   Intune rimuove il software client dal computer. Se un computer non è connesso al servizio Intune, il software client verrà rimosso alla successiva connessione.

-   Microsoft Intune Endpoint Protection viene rimosso dal computer. Se nel computer è installata un'altra applicazione Endpoint che è disabilitata, sarà possibile abilitarla di nuovo dopo aver rimosso Microsoft Intune Endpoint Protection per garantire che i computer siano protetti.

-   Tutti i criteri vengono rimossi dal computer e i valori impostati dal criterio vengono modificati.

-   Il computer non riceve più aggiornamenti software o aggiornamenti delle definizioni malware dal servizio Intune.

-   A seconda del modo in cui sono configurati, i computer ritirati possono continuare a ricevere gli aggiornamenti tramite Windows Server Update Services, Windows Update o Microsoft Update.

    > [!IMPORTANT]
    > Se il software client è stato installato tramite un oggetto Criteri di gruppo, è necessario rimuovere l'oggetto Criteri di gruppo prima di rimuovere il software client per evitare che il software venga reinstallato.

    Qualora non fosse possibile disinstallare il client, vedere [Risolvere i problemi di Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) per altre informazioni.

## Gestire il collegamento utente-dispositivo
Prima di distribuire software a un utente, è necessario collegare l'utente a un computer. È possibile collegare un utente a più computer, ma ogni computer può essere collegato a un solo utente. Gli utenti vengono automaticamente collegati a qualsiasi computer che registrano in Intune usando il portale aziendale.

### Per collegare un utente a un computer

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Gruppi** &gt; **Tutti i dispositivi** oppure un altro gruppo che contiene il computer da collegare a un utente.

2.  Selezionare il computer da collegare a un utente e scegliere **Collega utente**..

    Nella finestra di dialogo **Collega utente** è visualizzato un elenco di utenti disponibili con il rispettivo nome visualizzato, l'ID utente e il numero di computer a cui è attualmente collegato ciascun utente. Se un utente è già collegato al computer selezionato, il nome e l'ID utente vengono visualizzati in **Utente corrente**. Se il computer non è collegato ad alcun utente, sotto **Utente corrente ** viene visualizzato **Nessun utente**..

3.  Eseguire una delle operazioni seguenti:

    -   Per lasciare il computer collegato all'utente corrente, se ne esiste uno, scegliere **Annulla**..

    -   Per rimuovere il collegamento all'utente corrente, se presente, scegliere **Rimuovi collegamento**&gt;**OK**..

    -   Per collegare il computer a un nuovo utente, selezionare un utente nell'elenco **Tutti gli utenti** . Verificare che i dati dell'utente siano corretti e quindi scegliere **OK**..

> [!TIP]
> Per limitare la capacità di collegamento degli utenti finali ai computer, abilitare l'opzione **Limita la capacità utente di collegarsi ai computer** nei criteri **Impostazioni agente di Microsoft Intune**.

## Rispondere a una richiesta di assistenza remota
Gli utenti possono richiedere assistenza usando Assistenza remota tramite Microsoft Easy Assist che viene installato automaticamente nei computer gestiti. Quando viene effettuata una richiesta, viene visualizzato un avviso nella console di amministrazione di Intune.

> [!IMPORTANT]
> Assistenza remota non è supportata nei computer che eseguono Windows 8 o versioni successive.
>
> Se si accetta una richiesta di Assistenza remota di un utente da un computer in cui non è installato Microsoft Easy Assist, l'utente riceverà una richiesta di installare Easy Assist. Dopo l'installazione, è necessario riavviare il computer. Per evitare questo riavvio, si consiglia di precaricare Microsoft Easy Assist nei computer degli utenti.

### Per gestire una richiesta di Assistenza remota

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com/) scegliere **Avvisi** &gt; **Assistenza remota**..

2.  Selezionare una richiesta di assistenza remota nell'elenco **Avvisi** per aprire la pagina delle proprietà della richiesta.

3.  Scegliere **Approva la richiesta e apri Assistenza remota** per aprire una finestra di dialogo che contiene indicazioni per la risoluzione dell'avviso.

4.  Eseguire una delle operazioni seguenti:

    -   **Accettare la richiesta**: per partecipare alla sessione remota, scegliere **Accettare la richiesta di Assistenza remota**..

        L'utente visualizza il messaggio: "**La richiesta è stata accettata. Seguire le istruzioni in Easy Assist per condividere un programma o il desktop con l'amministratore di sistema**..

        > [!IMPORTANT]
        > Non è possibile accettare una richiesta di assistenza remota su un computer Mac che esegue la console di amministrazione di Intune.

    -   **Rifiutare la richiesta**: chiudere la finestra **Visualizza informazioni sulla risoluzione del problema**, quindi scegliere **Chiudi questo avviso** nella finestra delle proprietà dell'avviso.

        La richiesta viene chiusa e l'utente visualizza un messaggio che informa che la richiesta è stata rifiutata. Per richiedere assistenza remota, l'utente deve inviare una nuova richiesta di assistenza remota. Se si chiude accidentalmente un avviso di Assistenza remota, contattare l'utente che ha inviato la richiesta di Assistenza remota e richiedere di inviare una nuova richiesta.


<!--HONumber=May16_HO1-->


