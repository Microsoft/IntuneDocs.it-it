---
title: Usare gruppi per gestire utenti e dispositivi | Microsoft Intune
description: Creare e gestire gruppi usando l'area di lavoro Gruppi.
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: eb9b01ce-9b9b-4c2a-bf99-3879c0bdaba5
ms.reviewer: lpatha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5ab9592c253238fd832f8b48372e5474fcfc5331
ms.openlocfilehash: 96b0cd997544b2013efaca818d614c9802baaa46


---
## Avviso sui miglioramenti che verranno apportati alle funzionalità di amministrazione per i gruppi

Sulla base dei feedback degli utenti in cui venivano richieste funzionalità di raggruppamento e assegnazione in Enterprise Mobility e Enterprise Security, Microsoft ha deciso di convertire i gruppi di Intune in gruppi di sicurezza basati su Azure Active Directory. In questo modo la gestione dei gruppi verrà unificata in Intune e Azure Active Directory (Azure AD). Questa nuova esperienza consentirà di evitare la duplicazione dei gruppi tra i servizi e offrirà estendibilità tramite PowerShell e Graph. 

### Quali sono le conseguenze immediate di questa modifica?
Questa modifica non ha effetti immediati, ma presto saranno effettive le novità seguenti:

-   Nel mese di settembre i nuovi account di cui è stato eseguito il provisioning dopo il rilascio mensile del servizio useranno gruppi di sicurezza di Azure AD anziché gruppi di utenti di Intune.   
-   Nel mese di ottobre i nuovi account di cui è stato eseguito il provisioning dopo il rilascio mensile del servizio gestiranno sia i gruppi basati sugli utenti che quelli basati sui dispositivi nel portale di Azure AD. Nessun impatto sui clienti esistenti
-   Nel mese di novembre i team di prodotto inizieranno la migrazione dei clienti esistenti alla nuova esperienza di gestione dei gruppi basata su Azure AD. Tutti i gruppi di utenti e dispositivi attualmente presenti in Intune verranno migrati a gruppi di sicurezza di Azure AD. La migrazione verrà eseguita in batch a partire da novembre. Microsoft non inizierà la migrazione senza prima aver ridotto al minimo l'impatto sulle attività quotidiane degli utenti. Non è previsto alcun impatto sugli utenti finali. Gli utenti riceveranno una notifica prima della migrazione del loro account.


### Come e quando sarà possibile eseguire la migrazione ai nuovi gruppi?
La migrazione dei clienti correnti verrà eseguita in un certo lasso di tempo. Microsoft sta finalizzando il programma di migrazione. Questo argomento verrà aggiornato tra qualche settimana e verranno forniti ulteriori dettagli. Prima della migrazione, gli utenti riceveranno una notifica. Per domande e chiarimenti sulla migrazione, contattare il team addetto all'indirizzo [intunegrps@microsoft.com](intunegrps@microsoft.com).

### Cosa accade ai gruppi di utenti e dispositivi esistenti?
 I gruppi di utenti e dispositivi creati dagli utenti verranno migrati a gruppi di sicurezza di Azure AD. I gruppi di Intune predefiniti, ad esempio il gruppo All Users (Tutti gli utenti), verranno migrati soltanto se al momento della migrazione sono usati in distribuzioni. La migrazione può rivelarsi più complessa per particolari gruppi. Se sono necessari passaggi aggiuntivi, Microsoft provvederà a inviare una notifica agli utenti.

### Quali saranno le nuove funzionalità disponibili?
Di seguito sono indicate le nuove funzionalità che verranno introdotte:

-    I gruppi di sicurezza di Azure AD saranno supportati in Intune per tutti i tipi di distribuzione.
-    I gruppi di sicurezza di Azure AD supporteranno il raggruppamento sia di dispositivi che di utenti.
-    I gruppi di sicurezza di Azure AD supporteranno i gruppi dinamici con attributi dei dispositivi di Intune. Ad esempio, sarà possibile raggruppare dinamicamente dei dispositivi in base alla piattaforma, ad esempio iOS. In questo modo, quando nell'organizzazione viene registrato un nuovo dispositivo iOS, tale dispositivo verrà aggiunto automaticamente al gruppo dinamico di dispositivi iOS.
-    Esperienze di amministrazione condivisa per la gestione dei gruppi in Azure AD e Intune.
- Ad Azure AD verrà aggiunto il *ruolo di amministratore del servizio di Intune* per consentire agli amministratori del servizio Intune di eseguire attività di gestione dei gruppi in Azure AD.




### Quali funzionalità di Intune non saranno disponibili?
Anche se l'esperienza di raggruppamento registrerà dei miglioramenti, alcune funzionalità di Intune non saranno disponibili dopo la migrazione.

#### Funzionalità di gestione dei gruppi

-   Non sarà possibile escludere membri o gruppi quando si crea un nuovo gruppo. I gruppi dinamici di Azure AD, tuttavia, consentiranno di usare gli attributi per creare regole avanzate di esclusione di membri sulla base di criteri.
-   I gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati** non saranno supportati. La migrazione di tali gruppi non verrà eseguita.


#### Funzionalità dipendenti dai gruppi

-   Il ruolo Amministratore del servizio non disporrà delle autorizzazioni di tipo **Gestisci gruppi**.
-   Non sarà possibile raggruppare dispositivi Exchange ActiveSync.  Il gruppo **All EAS Managed Devices** (Tutti i dispositivi gestiti da EAS) verrà convertito in visualizzazione di report.
-  La trasformazione in report tramite Pivot con gruppi non sarà disponibile.
-  La possibilità di scegliere gruppi personalizzati come destinazione delle regole di notifica non sarà supportata.

### Quali operazioni è necessario eseguire in preparazione del cambiamento?
 Di seguito sono indicati alcuni accorgimenti che consentiranno di facilitare la migrazione:

- Prima della migrazione, eliminare i gruppi di Intune non desiderati o non necessari.
- Valutare la possibilità di usare la funzionalità di esclusione nei gruppi e di riprogettare i gruppi stessi in modo che non sia necessario fare ricorso all'esclusione.
-  Se sono presenti amministratori che non dispongono delle autorizzazioni per la creazione di gruppi in Azure AD, chiedere all'amministratore di Azure AD di aggiungerli al ruolo di **amministratore del servizio di Intune** di Azure AD.


# Creare gruppi per gestire utenti e dispositivi con Microsoft Intune

Questa sezione descrive come creare gruppi di Intune nella console di amministrazione di Intune.

Per creare e gestire gruppi, usare l'area di lavoro **Gruppi** nella console di amministrazione Microsoft Intune. La pagina **Panoramica gruppi** contiene un riepilogo dello stato che consente di identificare e definire le priorità dei problemi che richiedono un'attenzione per:

-   Avvisi
-   Aggiornamenti software
-   Endpoint Protection
-   Criteri
-   Gestione software

Inoltre, la gerarchia dei gruppi viene visualizzata con i riepiloghi dello stato che consentono di identificare e risolvere i problemi per i membri di un gruppo selezionato.


> [!TIP]
> Quando si crea no gruppi di considerare la modalità di applicazione dei criteri. Ad esempio, si potrebbe disporre di criteri specifici per i sistemi operativi per dispositivi e i criteri specifici per ruoli diversi all'interno dell'organizzazione o nelle unità organizzative che sono già state definite nell’Active Directory. Alcuni considerano utile disporre di gruppi di dispositivi specifici di Windows, iOS e Android, nonché gruppi di utenti per ogni ruolo dell'organizzazione.
>
> È opportuno creare un criterio predefinito che si applica a tutti i gruppi e i dispositivi, per stabilire i requisiti di conformità di base della società. Quindi creare criteri più specifici per le categorie più ampie di criteri di posta elettronica di utenti e dispositivi, ad esempio, per ciascuno dei sistemi operativi di dispositivo.
>
> Prestare attenzione ai criteri di denominazione in modo che sia possibile identificare facilmente in un secondo momento. Ad esempio, un nome descrittivo corretto del criterio è **WP criteri di posta elettronica per l'intera azienda**.
>
> Ogni volta che è possibile creare un criterio restrittivo sarà poi importante comunicarlo agli utenti, così che dopo aver creato gruppi più generali e criteri, si deve prestare attenzione a come creare gruppi più piccoli in modo che sia possibile ridurre le comunicazioni non necessarie.


## Creare un gruppo di dispositivi

1.  Nella console di amministrazione di Intune scegliere **Gruppi** &gt; **Panoramica** &gt; **Crea gruppo**.

2.  Specificare un nome e una descrizione facoltativa del gruppo e selezionare un gruppo di dispositivi come gruppo padre. Scegliere **Avanti**.

3.  Nella pagina **Definisci criteri appartenenza** selezionare il tipo di dispositivi che il gruppo includerà. Le opzioni aggiuntive per configurare il gruppo dipendono dal tipo di dispositivi selezionati:

    -   **Computer:** specificare se includere tutti i membri del gruppo padre, le unità organizzative (OU, Organizational Unit) e i domini da includere o escludere. Le informazioni sulle unità organizzative e sul dominio per un computer si possono trovare nell'inventario.

    -   **Dispositivi mobili:** specificare se includere solo i dispositivi mobili gestiti da Intune, quelli gestiti da Exchange ActiveSync o entrambe le opzioni.

    -   **Tutti i dispositivi:** questa opzione include tutti i dispositivi senza esclusioni in base ai criteri.

4.  Nella pagina **Definisci appartenenza diretta** , includere o escludere i singoli dispositivi specificati facendo clic su **Sfoglia**. Se si usa l'opzione di selezionare i dispositivi che non sono nel gruppo padre specificato, quei dispositivi verranno aggiunti automaticamente al gruppo padre.


5.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite. Scegliere **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** nel gruppo padre. Da qui è possibile inoltre modificare o eliminare il gruppo.

## Creare un gruppo di utenti

1.  Nella console di amministrazione di Intune scegliere **Gruppi** &gt; **Panoramica** &gt; **Crea gruppo**.

2.  Specificare un nome e una descrizione facoltativa del gruppo e selezionare un gruppo di utenti come gruppo padre. Scegliere **Avanti**.

3.  Nella pagina **Definisci criteri appartenenza** , specificare se includere tutti i membri del gruppo padre o iniziare con un gruppo vuoto.  È possibile quindi includere o escludere i membri in base ai **gruppi di sicurezza** degli utenti che si configurano manualmente nell'[interfaccia di amministrazione di Office 365](http://go.microsoft.com/fwlink/?LinkId=698854) o che si sincronizzano da Active Directory locale. Se cambia l'appartenenza di un gruppo di sicurezza, è possibile modificare anche l'appartenenza dei gruppi di utenti che si basa su quel gruppo di sicurezza.

    > [!IMPORTANT]
    > Attualmente, se il gruppo include i membri da specifici gruppi di sicurezza o gestione e si escludono i membri da gruppi specifici, i membri inizialmente inclusi verranno rimossi. Per creare un gruppo in cui siano presenti membri inclusi ed esclusi, è consigliabile creare innanzitutto un gruppo padre con i membri inclusi e quindi creare un elemento figlio di tale gruppo in cui siano elencati i membri esclusi. È quindi possibile usare tale gruppo figlio nel modo opportuno per i criteri, i profili e la distribuzione di app di Intune.

    > [!NOTE]
    > Nel portale di gestione di Azure è possibile creare un gruppo in base al responsabile a cui gli utenti fanno riferimento. Il gruppo sarà dinamico e verrà modificato man mano che i dipendenti vengono aggiunti o rimossi dal team del responsabile in Azure Active Directory. La procedura per la creazione di un gruppo di Azure basato su un responsabile è descritta in [Uso di attributi per la creazione di regole avanzate](https://azure.microsoft.com/en-us/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) nella sezione denominata **Per configurare un gruppo come gruppo "Manager"**.


4.  Nella pagina **Definisci appartenenza diretta** , includere o escludere i singoli utenti specificati facendo clic su **Sfoglia**. Se si usa l'opzione di selezionare gli utenti che non sono nel gruppo padre specificato, quei dispositivi verranno aggiunti automaticamente al gruppo padre. Nella parte inferiore della finestra di dialogo **Seleziona membri** è possibile trovare l'opzione per l'aggiunta manuale di un utente. Ciò è utile se si desidera aggiungere un utente che non dispone ancora di un dispositivo registrato.


5.  Nella pagina **Riepilogo** esaminare le azioni che verranno eseguite. Scegliere **Fine**.

Per trovare il gruppo appena creato, andare nell'elenco **Gruppi** nell'area di lavoro **Gruppi** nel gruppo padre. Da qui è possibile inoltre modificare o eliminare il gruppo.

> [!TIP]
> I Gruppi di sicurezza sono un'ottima risorsa per il popolamento dei gruppi di utenti. Poiché i gruppi di sicurezza definiscono chi ha accesso a quali risorse, tali gruppi possono essere convertiti perfettamente in gruppi di utenti di Intune. I gruppi di sicurezza sincronizzati da Active Directory in Azure Active Directory, o creati direttamente in Azure Active Directory con l'interfaccia di amministrazione di Office 365 o il portale di amministrazione di Azure, sono tutti disponibili per la creazione di gruppi di utenti in Intune.

## Personalizzare le visualizzazioni per i ruoli di amministratore
Le visualizzazioni di gruppi filtrati consentono di personalizzare la visualizzazione che gli amministratori possono vedere in base al proprio ruolo e limitare i gruppi che ogni amministratore IT può gestire. Questa impostazione può essere utile nei casi seguenti:

-   Gli amministratori IT devono solo distribuire elementi a utenti e dispositivi specifici.

-   Si vuole che per ogni amministratore IT vengano visualizzati solo i gruppi di dispositivi e utenti pertinenti.

È possibile configurare le visualizzazioni di gruppi filtrati per gli amministratori del servizio nella console di amministrazione di Intune. Per informazioni dettagliate, vedere [Informazioni preliminari per l'uso di Microsoft Intune](/intune/get-started/what-to-know-before-you-start-microsoft-intune).

Dopo la configurazione delle visualizzazioni di gruppi filtrati per un amministratore del servizio, quest'ultimo:

-   Può visualizzare e selezionare solo i gruppi specificati quando distribuisce software o criteri oppure quando usa i report

-   Non riceve informazioni sullo stato nelle pagine seguenti della console di amministrazione:

    -   **Panoramica sistema**

    -   **Panoramica gruppi**

    -   **Panoramica Endpoint Protection**

    -   **Panoramica avvisi**

    -   **Panoramica software**

    -   **Panoramica criteri**

### Configurare le visualizzazioni di gruppi filtrati

1.  Nella console di amministrazione di Microsoft Intune scegliere **Amministrazione** &gt; **Gestione amministratori** &gt; **Amministratori del servizio**.

2.  Selezionare l'amministratore del servizio per il quale filtrare i gruppi e quindi fare clic su **Gestisci gruppi**.

3.  Nella finestra di dialogo **Seleziona i gruppi visualizzabili dall'amministratore del servizio** aggiungere i gruppi cui l'amministratore del servizio selezionato potrà accedere e quindi fare clic su **OK**.

Dopo aver configurato le visualizzazioni di gruppi filtrati, l'amministratore IT sarà in grado di visualizzare e selezionare solo i gruppi selezionati.

## Gestione dei gruppi
Dopo aver creato i gruppi, si continuerà a gestirli in base alle esigenze dell'organizzazione.

È possibile modificare il gruppo per modificare il nome e la descrizione e che appartiene al gruppo.

È possibile eliminare un gruppo che non è più necessario per l'organizzazione. La cancellazione di un gruppo non elimina gli utenti che appartengono a tale gruppo.

## Passaggi successivi

### Controllare la progettazione
Dopo aver impostato i gruppi e i criteri, controllare le implicazioni pratiche di progettazione esaminando il **Valore previsto** e lo **Stato**.

1. Selezionare qualsiasi dispositivo da un gruppo di dispositivi e visualizzare le categorie di informazioni nella parte superiore della schermata.
2. Selezionare **criteri** . Verrà visualizzato qualcosa di simile a questa schermata delle impostazioni di criteri di un dispositivo Android.

![Esempio di criterio di impostazioni iOS](../media/Intune-Device-Policy-v.2.jpg)

Ogni criterio dispone di un **previsto valore** e **stato**. Il valore previsto è quello che si intende ottenere quando si assegnano i criteri. Lo stato è ciò che effettivamente si ottiene quando tutti i criteri applicati al dispositivo, oltre alle restrizioni e ai requisiti di hardware e del sistema operativo, vengono considerati insieme.  Nella schermata è possibile visualizzare due chiari esempi:

-   **Consentire password semplici** è impostato su **Sì**, come illustrato nella colonna **del valore previsto** ma lo **stato** è **non applicabile**. Infatti, le password semplici non sono supportate per i dispositivi Android.

-   Analogamente, l'elemento dei criteri espanso, **Impostazioni posta elettronica per i dispositivi iOS**, non viene applicato al dispositivo, visto che è un dispositivo Android.

> [!NOTE]
> Tenere presente che quando due criteri con livelli di restrizione diversi vengono applicati allo stesso dispositivo o utente, viene di fatto applicato il criterio più restrittivo.



<!--HONumber=Aug16_HO3-->


