---
# required metadata

title: Domande frequenti | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a8126cca-9ec4-454b-a20b-dc1bb6797327

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Domande frequenti relative a Intune
Questo articolo offre una risposta alle domande più frequenti su Intune. Se non trovate la risposta alla vostra domanda, [contattateci](https://microsoftintune.uservoice.com/).

## Problemi generali

-   **Come posso sapere quando è stato aggiornato il servizio Intune?**

    Accedere all’account su manage.microsoft.com. In Panoramica amministrazione selezionare **Visualizza stato del servizio**. Vengono elencate la posizione del tenant e la pianificazione della manutenzione. Leggere le informazioni sugli aggiornamenti del servizio nell'articolo sulle [novità](/intune/deploy-use/whats-new-in-microsoft-intune).

-   **Se un utente rinomina un dispositivo all'interno dell'app Portale aziendale, tale nome cambierà in Intune o Configuration Manager?**

    No, tale modifica del nome è solo per comodità dell'utente.

-   **È disponibile una funzionalità di assistenza remota in Intune per i dispositivi mobili?**

    Non non è disponibile. Possono risultare utili applicazioni di terze parti, ad esempio [Bomgar](http://www.bomgar.com/) e [TeamViewer](https://www.teamviewer.com/).

## Account

-   **Se si avvia la valutazione Intune e si crea un nuovo tenant per la versione di prova, è possibile aggiungere Office 365 alla valutazione usando lo stesso tenant?**

    Sì. È sufficiente accedere come amministratore globale dal tenant o dalla sottoscrizione di Intune esistente, ad esempio *globaladmin@&lt;società&gt;.onmicrosoft.com*.

-   **Se si assegna autorità MDM a Intune durante una sottoscrizione di valutazione, diventa difficile passare al servizio di un'altra società se si cambia idea su Intune?**

    Sebbene sia difficile immaginare come sia possibile non trovarsi bene con Intune, la scelta dell’autorità MDM non influisce sulla capacità di passare a un altro servizio. Si tratta di scegliere Intune o Intune con System Center Configuration Manager.

-   **È possibile utilizzare il nome di dominio esistente di Office 365 per l'account Intune successivo?**

    Sì, se quando si crea la versione di valutazione di Intune o si attivano le licenze si accede con l'ID organizzazione associato al tenant o al dominio verificato esistente di Office 365.

    Intune userà quindi lo stesso dominio/gli stessi utenti/e così via dell’account Office 365. Si noti che ogni utente di Office 365 deve essere abilitato come utente di Intune che usa una licenza di Intune. Tale operazione deve essere eseguita dall'amministratore globale che gestisce il tenant.

## Registrazione

-   **Dove possono imparare a registrare i propri dispositivi gli utenti?**

    È possibile usare o personalizzare le informazioni contenute in [End-user Intune enrollment instructions for IT administrators](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) (Istruzioni per la registrazione a Intune per amministratori IT)..

-   **Come è possibile risolvere i problemi di registrazione dei dispositivi?**

    Le soluzioni ai problemi di registrazione più comuni sono indicate nella pagina [Troubleshoot device enrollment in Intune](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune) (Risoluzione dei problemi di registrazione dei dispositivi in Intune)..

-   **In che modo è possibile raccogliere i log di registrazione se un utente ha un problema di registrazione?**

    Seguire [queste istruzioni](http://www.microsoft.com/en-us/download/46391).

## Gestione dispositivi mobili

-   **MDM generale**

    -   **Intune consente di rilevare se un dispositivo è jailbroken?**

        Sì, per alcuni sistemi operativi. Per informazioni sulla gestione dei dispositivi jailbroken, vedere [Create a device compliance policy](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune.md) (Creare criteri di conformità dei dispositivi).

    -   **È possibile cancellare selettivamente i dati aziendali da un dispositivo?**

        Sì. Per informazioni sulla cancellazione selettiva, vedere [Help protect your data with remote wipe, remote lock, or passcode reset](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune.md) (Proteggere i dati con cancellazione remota, blocco remoto o reimpostazione passcode).

    -   **Esiste un modo per bloccare determinati siti Web nel browser del dispositivo mobile tramite Intune?**

        Non nel browser nativo di qualsiasi piattaforma. Tuttavia, è possibile accettare o bloccare gli URL se è stato distribuito il Web browser gestito di Intune nei dispositivi iOS e Android. Per altre informazioni, vedere [Manage Internet access using managed browser policies](/intune/Deploy-Use/Manage-Internet-access-using-managed-browser-policies-with-Microsoft-Intune.md) (Gestire l'accesso a Internet usando i criteri di Managed Browser)..

    -   **È possibile impedire a un utente di disinstallare un'applicazione?**

        In generale, no. Tuttavia, in un dispositivo iOS supervisionato è possibile impedire un utente la disinstallazione di un'applicazione che è stata distribuita utilizzando Apple Configurator. 

    -   **Esiste un modo per gestire l'utilizzo della rete dati?**

        Non direttamente, ma è possibile assicurarsi che il Wi-Fi sia il metodo preferito per la connessione mediante il push dei profili Wi-Fi ai dispositivi, come descritto in [Help users connect to company networks using Wi-Fi profiles](/intune/Deploy-Use/wi-fi-connections-in-microsoft-intune.md) (Consentire agli utenti di connettersi alle reti aziendali usando profili Wi-Fi). Inoltre, alcune piattaforme (ad esempio, iOS e Android KNOX) consentono di controllare impostazioni quali il roaming delle chiamate e dei dati.

    -   **Esiste un modo per impedire a un utente di registrare un dispositivo? E se si tratta di un dispositivo di proprietà dell'azienda?**

        In generale, no. Tuttavia, con le impostazioni personalizzate di Windows Phone, è possibile evitare l'annullamento della registrazione degli utenti in Windows Phone 8.1. Inoltre, per i dispositivi iOS supervisionati e registrati con il programma DEP (Device Enrollment Program) di Apple, è possibile impedire a un utente di annullare la registrazione di un dispositivo.

    -   **È possibile cambiare l’autorità di gestione dei dispositivi mobili scelta?**

        In alcune situazioni, è possibile cambiare l’autorità di gestione dei dispositivi mobili. A questo scopo, contattare il supporto tecnico, come descritto in [How to get support for Microsoft Intune](/intune/Troubleshoot/How-to-get-support-for-Microsoft-Intune.md) (Come ottenere supporto per Microsoft Intune). La tabella seguente descrive le modifiche possibili. Le modifiche nell'autorità di gestione dei dispositivi mobili richiedono una nuova registrazione dei dispositivi.

        ||**A:** Intune!**A:** O365|**A:** Configuration Manager con Intune|
        |**Da:** Intune| |Sì&#42;|Sì|
        |**Da:** O365||Sì&#42;||Sì|
        |**Da:** Configuration Manager con Intune|Sì|Sì| |
        
        &#42;Le autorità di gestione dei dispositivi mobili di Office 365 e Intune possono coesistere, per cui non è necessario registrare nuovamente i dispositivi mobili.



-   **Windows**

    -   **È possibile trasferire localmente un'applicazione Windows Store?**

        Le app disponibili pubblicamente non possono essere trasferite localmente. Sebbene sia possibile scaricare il file XAP, è impossibile caricarlo in Intune perché si tratta di un file XAP pubblico, crittografato e firmato con il certificato di firma codice dello sviluppatore. Solo le app sviluppate e firmate con il proprio certificato di firma codice possono essere trasferite localmente.

    -   **Le app Windows Phone Store distribuite tramite il portale aziendale richiedono che l’utente finale disponga di un account Microsoft?**

        Sì, l'utente finale non sarà in grado di ottenere app senza un account Microsoft. Fanno eccezione le app LOB private trasferite localmente, che possono essere distribuite a un dispositivo senza un account Microsoft.

    -   **Per gestire Windows Phone 8.1 con Intune è necessario un account Microsoft?**

        No. Tuttavia, sarà necessario installare la maggior parte delle applicazioni dall'archivio pubblico.

        **Perché Windows Phone richiede un certificato Symantec per la gestione?**
        Windows Phone controlla come installare le app. Qualsiasi utente con un account Microsoft può installare le app da Windows Phone Store oppure le società possono installare o trasferire localmente le app LOB (line of business) sviluppate internamente tramite uno speciale processo descritto nella documentazione di Windows Phone. Quando si installano app LOB, Windows Phone accetta solo un tipo speciale di certificato rilasciato da Symantec. Non è possibile utilizzare nessun altro certificato generato commercialmente o privatamente. Questo requisito vale per tutte le soluzioni di gestione dei dispositivi mobili, non solo per Intune.

        Il certificato Symantec crea un token di registrazione applicazione (AET, Application Enrollment Token). AET può essere installato in un dispositivo quando esegue la registrazione alla gestione dei dispositivi mobili oppure può essere installato fuori programma da un sito Web protetto o da un allegato di posta elettronica. Gli amministratori devono firmare tutte le applicazioni LOB con il certificato Symantec, usando gli strumenti forniti in [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=268439). Quando gli utenti tentano di installare le app LOB, il sistema operativo Windows Phone verifica la firma in AET in base alla firma nell'app. Se le firme corrispondono, l'installazione può continuare. Se non è possibile verificare AET, l'installazione non riesce. La verifica di AET potrebbe non riuscire per diversi motivi:

        -   AET non è stato mai installato nel dispositivo

        -   AET è scaduto

        -   AET non è stato creato con lo stesso certificato Symantec usato per firmare l'app

        Windows Phone non richiede AET durante la registrazione MDM, ma prima del rilascio di novembre 2014 Intune richiedeva AET e il file ssp.xap firmato perché non esistevano altri modi per installare AET e il file ssp.xap se non durante la registrazione.

    **Come viene creato AET per gli utenti Intune?**
  Quando gli amministratori caricano il file con estensione PFX per il certificato Symantec, Intune crea automaticamente il token AET e lo distribuisce nei dispositivi Windows Phone registrati. Non è necessario che gli amministratori di Intune usino lo strumento AET Generator in Windows Phone SDK.

      > [!IMPORTANT]
        > Intune non consente di creare manualmente il token AET e di distribuirlo fuori programma.

    **Quali modifiche riducono la necessità di un certificato Symantec?**
       Per il rilascio di novembre 2014 sono state apportate modifiche che consentono l'uso alle società che non dispongono di un certificato Symantec.

       -   Il Portale aziendale per Windows Phone 8.1 è disponibile per l'installazione dallo Store, quindi non è necessario che sia firmato con un certificato Symantec e convalidato in base a un token AET. L'app, invece, viene convalidata nel processo di pubblicazione dello Store.

        -   I dispositivi Windows Phone 8.1 possono eseguire la registrazione con o senza un token AET nel telefono. Se AET è disponibile, verrà installato alla prima sincronizzazione del dispositivo con Intune. Se non AET non è disponibile, è comunque possibile gestire il dispositivo con Intune e gli utenti possono installare il Portale aziendale dallo Store e usare la maggior parte delle funzionalità del Portale aziendale senza un certificato Symantec per firmare le app.

        Per i dispositivi Windows Phone 8 non sono previste modifiche al requisito relativo a Symantec. I dispositivi Windows Phone 8 devono disporre del file ssp.xap firmato e del token AET durante la registrazione, che altrimenti verrà bloccata.

        **Quali funzionalità sono supportate se un dispositivo Windows Phone 8.1 viene registrato ma non è disponibile un certificato Symantec?**
        Se un dispositivo Windows Phone 8.1 viene registrato ma non è disponibile un certificato Symantec, è possibile:

        -   Creare i criteri e inviarli al dispositivo

        -   Configurare le informazioni di contatto per il reparto IT che verrà visualizzato nel Portale aziendale

        -   Creare collegamenti diretti allo Store e distribuirli al Portale aziendale

        -   Creare collegamenti a pagine Web e distribuirli al Portale aziendale

        -   Creare i termini e le condizioni che devono essere accettate dagli utenti per poter usare il Portale aziendale

        L'unica funzionalità che non è possibile eseguire senza un certificato Symantec è la distribuzione di app LOB.

        > [!IMPORTANT]
        > Il distributore del software Intune non verifica che le app siano firmate quando vengono caricate. Se si distribuiscono app non firmate, il tentativo di installazione da parte degli utenti non riuscirà.

        **Cosa possono fare gli utenti se hanno il Portale aziendale, ma non è disponibile alcun certificato Symantec?**
        I dispositivi Windows Phone 8.1 non devono essere registrati prima di poter installare il Portale aziendale dallo Store. Se il dispositivo non è registrato, agli utenti viene richiesto di eseguire la registrazione. Toccando il prompt nel portale aziendale viene visualizzata direttamente la schermata **Impostazioni/Azienda** in cui è possibile registrare i dispositivi.

        Anche senza la registrazione del dispositivo, gli utenti possono eseguire le azioni seguenti con il Portale aziendale installato dallo Store:

        -   Accettare o rifiutare i termini e le condizioni configurati dall'amministratore. Se gli utenti rifiutano i termini e le condizioni, il Portale aziendale si chiude.

        -   Visualizzare le informazioni di contatto per il reparto IT

        -   Visualizzare eventuali dispositivi registrati, inclusi i dispositivi iOS, Android e Windows

        -   Usare i collegamenti diretti alle applicazioni nello Store

        -   Usare i collegamenti Web per aprire le pagine Web

        Se il dispositivo è registrato, gli utenti possono visualizzarlo nell'elenco **Dispositivi personali** . Una volta registrato, il dispositivo è soggetto a tutti i criteri Intune distribuiti. I dispositivi devono essere registrati per ottenere il token AET e installare le app LOB. Un dispositivo non registrato che tenti di installare un'app LOB verrà indirizzato alla procedura di registrazione.

        L'unica funzionalità preclusa agli utenti se la società non dispone di un certificato Symantec è l'installazione di app LOB distribuite dall'amministratore.

        **L'azienda dispone già di un certificato e sta registrando dispositivi Windows Phone 8.1. Devo eseguire operazioni particolari ora che il Portale aziendale è disponibile nello Store?**
        Nei dispositivi Windows Phone 8.1 funziona comunque il file ssp.xap corrente dall'Area download. È possibile continuare a indirizzare gli utenti alla procedura di registrazione e acquisire il Portale aziendale durante l'installazione.

        **Quali sono i vantaggi e gli svantaggi per gli utenti collegati all'acquisizione del Portale aziendale dallo Store?**
        Vantaggi:

        -   Gli utenti ottengono collegamenti diretti e collegamenti Web anche se il dispositivo Windows Phone 8.1 non è registrato

        -   Quando Microsoft aggiorna il Portale aziendale, l'App Store viene aggiornato automaticamente senza dover scaricare, firmare e ridistribuire il file ssp.xap

        -   La documentazione per gli utenti di Windows Phone 8.1, iOS, Android e Windows è coerente: "Vai allo Store e installa il Portale aziendale".

        -   Gli utenti visualizzano l'installazione dell'app e ottengono le istruzioni di registrazione quando si apre

        Svantaggi:

        -   Gli utenti visualizzano una casella di controllo per installare un "**hub aziendale**" ma non vengono indirizzati al Portale aziendale nell'elenco di app del dispositivo

        -   Gli utenti non sono tenuti ad accettare i termini e le condizioni personalizzati fino a quando non aprono il Portale aziendale

        Nelle seguenti circostanze è possibile continuare a indirizzare gli utenti alla procedura di registrazione e installare il file ssp.xap durante la registrazione:

        -   Se i blocchi aziendali accedono allo Store dai dispositivi Windows Phone, gli utenti devono installare il file ssp.xap durante la registrazione.

        -   Se gli utenti non dispongono di account Microsoft configurati nei dispositivi Windows Phone, non potranno installare il Portale aziendale dallo Store.

        -   Se la documentazione esistente per la registrazione di Windows Phone specifica di andare prima in Impostazioni, Area di lavoro, l'aggiornamento dei documenti e l'indirizzamento degli utenti allo Store potrebbero richiedere alcuni minuti.

        **Qual è la differenza tra il file ssp.xap nell'Area download e l'app nello Store?**

        -   Il Portale aziendale nello Store non deve essere firmato da un certificato Symantec per essere installato

        -   Diversamente dal file ssp.xap nell'Area download, il Portale aziendale nello Store specifica i termini e le condizioni per l'utente

        -   Il Portale aziendale nello Store è ha un'estensione appx anziché xap

        **È possibile ottenere e inviare agli utenti il file del portale aziendale invece di indirizzarli allo Store?**
        Sì. È possibile scaricare l'app Portale aziendale per i sistemi operativi seguenti dall'Area download:

        -   Windows Phone 8.1: [http://go.microsoft.com/fwlink/?LinkId=615799](http://go.microsoft.com/fwlink/?LinkId=615799)

        -   Windows Phone 8.0 : [http://go.microsoft.com/fwlink/?LinkId=268440](http://go.microsoft.com/fwlink/?LinkId=268440)

        -   Windows 8.1: [http://go.microsoft.com/fwlink/?LinkId=615800](http://go.microsoft.com/fwlink/?LinkId=615800)

        **Le società possono comunque usare lo strumento di supporto per la gestione della versione di valutazione di Windows Intune di Windows Phone se non dispongono di un certificato Symantec e i loro utenti possono comunque installare il Portale aziendale dallo Store?**
        Sì. Se è necessario eseguire un modello di prova che include l'installazione di app LOB, lo strumento di gestione di valutazione funziona con la versione dello Store del Portale aziendale. Tuttavia, poiché il token AET dal certificato Symantec non è più necessario per registrare i dispositivi Windows Phone 8.1, le società possono testare l'installazione dell'app usando collegamenti diretti alle applicazioni nello Store.

        Lo strumento di supporto per la gestione della versione di valutazione di Windows Intune di Windows Phone è solo per le sottoscrizioni di valutazione di Intune.

        > [!IMPORTANT]
        > Usare solo i test dello strumento di gestione di valutazione. I dispositivi registrati con il token AET dallo strumento di gestione di valutazione devono annullare e ripetere la registrazione se il certificato Symantec per lo strumento di gestione di valutazione non è più disponibile o se l'azienda ottiene il proprio certificato Symantec per la firma delle app.

        **Le società possono iniziare senza alcun certificato Symantec e aggiungerlo successivamente, anche dopo aver registrato i dispositivi Windows Phone 8.1?**
        Sì. Anche se i dispositivi Windows Phone 8.1 sono già stati registrati, è possibile ottenere un certificato Symantec, firmare il file ssp.xap e caricare questo file e il file pfx. Intune genera quindi il token AET. I dispositivi Windows Phone 8.1 otterranno il token AET alla successiva sincronizzazione, dopo un massimo di otto ore. Far trascorrere almeno otto ore prima di distribuire le app LOB dopo aver caricato i file xap e pfx.


-   **Android**

    -   **Quanto tempo è necessario per crittografare un dispositivo Android?**

        Dipende principalmente dalla velocità del processore del dispositivo e dalla quantità di memoria utilizzata e totale, e non si tratta di una funzione di Intune.

-   **iOS**

    -   **Quando si distribuiscono le app iOS con Intune, se sono stati caricati il file IPA e il file manifesto dell'applicazione, per continuare l'installazione del dispositivo è necessario un ID Apple?**

        No. Quando Intune fornisce i bit (con IPA caricato in Intune), le applicazioni vengono trasferite localmente e non richiedono un ID Apple.

    -   **Esiste un modo per consentire l'installazione di app in iOS senza consentire l'accesso all'Apple Store?**

        No, ma è possibile abilitare l'App Store e usare le app consentite e bloccate in iOS per tenere sotto controllo le azioni eseguite dagli utenti. Le app LOB trasferite localmente non richiedono l'accesso all'App Store Apple.

    -   **Le app di Apple Store distribuite tramite il portale aziendale richiedono che l'utente finale abbia un account iTunes?**

        Sì, l'utente finale non potrà ottenere le app senza un account iTunes.

    -   **È possibile bloccare l'App Store?**

        Sì, è possibile, ma in questo modo tutte le installazioni e gli aggiornamenti delle app dall’App Store verranno bloccate, non solo quelle avviate dall'utente finale. Ciò significa che anche la distribuzione di qualsiasi app dell'App Store pubblico da Intune non riuscirà.

## Distribuzione di app

-   **In che modo è possibile aggiungere un'app consigliata?**

    In Intune sono dette "app in primo piano" e sono documentate in [Deploy apps in Microsoft Intune](/Intune/Deploy-Use/deploy-apps-in-microsoft-intune.md) (Distribuire le app in Microsoft Intune).

-   **È possibile ottenere spazio di archiviazione cloud aggiuntivo per le applicazioni che si desidera distribuire?**

    Sì. Le informazioni su questo argomento sono disponibili in [Deploy apps](/Intune/Deploy-Use/deploy-apps.md) (Distribuire app), nella sezione relativa ai *requisiti di spazio di archiviazione*.

## Sicurezza

-   **BitLocker può essere applicata da Intune?**

    L'agente OMA-DM in Windows 8.1/RT consente di leggere (ottenere) lo stato della crittografia. Tuttavia non è possibile impostarlo. Questo vale per Intune e per altri servizi di gestione di dispositivi mobili.

-   **Se si crittografa un tablet Windows 8 con BitLocker, è possibile applicare la cancellazione dei dati dispositivo completa nel caso in cui un utente non riesce a eseguire l’accesso più volte consecutivamente?**

    Non esiste alcuna opzione per la cancellazione completa dei dati sui dispositivi Windows 8.1/RT per qualsiasi servizio di gestione dispositivi mobili, tra cui Intune. Intune fornisce la cancellazione selettiva per tali dispositivi. Per altre informazioni sulla cancellazione/cancellazione selettiva in Intune, vedere [Protect apps and data with Microsoft Intune](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md) (Proteggere applicazioni e dati con Microsoft Intune).

## Portale aziendale

-   **È possibile personalizzare il portale aziendale?**

    Sì. Nella console di amministrazione di Intune, accedere a **Amministrazione&gt;Portale aziendale** per tali impostazioni.

## Microsoft Intune con Configuration Manager

-   **Quando si usa Configuration Manager con Intune, da dove si gestiscono i dispositivi?**

    Tutti i dispositivi vengono gestiti dalla console di Configuration Manager, anche se i dispositivi in cui è installato l'agente di Intune verranno visualizzati nella console di Intune. I dispositivi mobili non verranno visualizzati nella console di Intune.

-   **È possibile eseguire una cancellazione selettiva sui dispositivi?**

    Se si usa System Center 2012 R2 Configuration Manager o versione successiva con Intune, è possibile eseguire una cancellazione selettiva che rimuove i dati aziendali. Per altre informazioni, vedere [Protect apps and data with Microsoft Intune](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md) (Proteggere applicazioni e dati con Microsoft Intune).

-   **Se si usa Configuration Manager con Intune, è possibile comunque usare il portale di amministrazione di Intune?**

    È possibile, ma da tale portale potranno essere gestiti solo i PC in cui è installato l'agente di Intune. Nel portale sono inoltre disponibili altre informazioni utili relative ad avvisi sul servizio, lo stato del servizio e così via, ma le impostazioni di gestione dispositivo disponibili non verranno applicate ai dispositivi registrati.



<!--HONumber=May16_HO1-->


