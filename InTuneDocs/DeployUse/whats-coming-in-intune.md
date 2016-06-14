---
# required metadata

title: Sviluppi futuri | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/17/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Sviluppi futuri in Microsoft Intune
Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Controllare regolarmente la pagina per conoscere gli sviluppi futuri.

Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate anche per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Comunicazioni Intune
- **Informazioni sull'integrità del servizio Intune.** per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) in Integrità dei servizi. Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Caricamento dell'interfaccia utente del centro messaggi.** Come parte della migrazione di Intune nel [portale di gestione di Office 365](https://portal.office.com/), inizieremo a sfruttare il suo centro messaggi per comunicare le nuove funzionalità e altre notifiche. Inoltre, installando l'app complementare per dispositivi mobili Office 365 Admin, è possibile ricevere notifiche sul cellulare e inoltrare facilmente qualsiasi messaggio agli utenti o a un alias di distribuzione.
Inizieremo a usare il centro messaggi con la nostra versione di maggio per notificare quando gli aggiornamenti sono completati e includeremo informazioni sulle funzionalità di Intune nuove e migliorate. Visitare il centro messaggi oggi stesso eseguendo l'accesso al [portale di gestione di Office 365](https://portal.office.com/) e scegliendo l'opzione **Centro messaggi** nel riquadro di spostamento a sinistra.

## Gestione delle app
- **Sono disponibili nuove app per la gestione con criteri MAM.** Le app Microsoft Word, Excel e PowerPoint per Android possono ora essere associate a criteri MAM su dispositivi non registrati in Intune. Per visualizzare l'elenco completo delle app supportate, passare alla raccolta di applicazioni per dispositivi mobili di Microsoft Intune nella [pagina dei partner di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


- **Accesso condizionale per il browser** Sarà possibile impostare un criterio di accesso condizionale per Exchange Online e SharePoint Online in modo che siano accessibili solo da dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere a siti di Outlook Web Access (OWA) e SharePoint e con dispositivi iOS e Android verrà richiesto di registrare il dispositivo con Intune oltre che di risolvere eventuali problemi di non conformità prima di poter completare l'accesso.
<!---TFS 1175844--->

- **MAM SDK: supporto per la configurazione della lunghezza del PIN.** Sarà possibile specificare la lunghezza del PIN per le app MAM in modo simile al PIN di un dispositivo. Gli utenti finali dovranno perciò conformarsi alle nuove limitazioni imposte. Vedranno la schermata del PIN leggermente modificata per tenere conto della lunghezza del PIN.
<!--- TFS 1104753--->

- **Skype for Business per Android.** Gli amministratori di Intune possono ora scegliere come destinazione Skype for Business con MAM senza criteri di registrazione.  Una volta che gli utenti sono connessi, verranno applicati i criteri MAN.
<!--- TFS item 1248444 --->

- **Skype for Business per iOS.** Gli amministratori di Intune possono ora scegliere come destinazione Skype for Business con MAM senza criteri di registrazione.  Una volta che gli utenti sono connessi, verranno applicati i criteri MAN.
<!--- TFS item 1248443 --->

### Supporto di Xamarin
Microsoft Intune App SDK ora supporta le app Xamarin in questi scenari:

- Scrittura di nuove app o modifica del codice di app line of business esistenti mediante l'SDK di Intune. È possibile ottenere il plug-in sulla pagina [Microsoft Intune Github](https://github.com/msintuneappsdk).
- Aggiunta del supporto MAM ad app line of business esistenti mediante lo strumento di wrapping delle app di Intune

Per informazioni su come scegliere il metodo da usare, vedere [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## Gestione dei dispositivi
- **Sessioni di assistenza remota per i PC Windows.** L'integrazione di TeamViewer per PC Windows gestiti da agenti desktop consentirà di stabilire sessioni di assistenza remota con i computer Windows gestiti da agenti desktop a supporto dei reparti di assistenza all'utente finale. Sono inclusi Windows 7, 8, 8.1 e Windows 10.
<!--- TFS 1284856--->



## Portale aziendale

- **Notifiche di tipo avviso popup per l'utente finale.** Per gli utenti finali che registrano un dispositivo o lo rimuovono dal Portale aziendale vengono visualizzate notifiche di tipo avviso popup dell'app Portale aziendale Android.
- **Il banner di identificazione del dispositivo fornirà maggiori informazioni agli utenti finali.** Gli utenti finali potranno identificare facilmente il dispositivo che hanno selezionato durante l'utilizzo del sito Web del Portale aziendale. Se selezioneranno il dispositivo sbagliato, potranno scegliere quello corretto toccando il collegamento "Toccare qui" nel banner della pagina iniziale.
<!--- TFS 1231157--->

- **Modifiche agli account Manager di registrazione dispositivi nell'app Portale aziendale Android.** Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro **Dispositivi personali** dell'app Portale aziendale Android. Verrà visualizzato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app Portale aziendale. L'utente Manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.

- **Modifiche agli account Manager di registrazione dispositivi nell'app Portale aziendale iOS.** Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro Dispositivi personali dell'app Portale aziendale iOS. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.  Intune inoltre deprecherà l'uso degli account Manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi.  Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile.



## Deprecazione del servizio
**Rimozione della capacità di scegliere gruppi personalizzati come destinazione delle regole di notifica.**
Le regole di notifica di Intune definiscono i destinatari degli avvisi di posta elettronica inviati da Intune. Attualmente è possibile configurare regole di notifica per inviare messaggi di posta elettronica a tutti gli utenti dei dispositivi di un gruppo di dispositivi di Intune creato. A partire dal 1° giugno 2016, la configurazione dei gruppi creati dagli utenti come destinazione non sarà più supportata.

Attualmente, per impostare come destinazione di una regola di notifica un gruppo creato dalla console di amministrazione di Microsoft Intune, è necessario eseguire i passaggi seguenti:

Nell'area di lavoro **Amministrazione** fare clic su **Regole di notifica** > **Crea nuova regola**

Al secondo passaggio della procedura guidata di creazione di una regola di notifica selezionare i gruppi di dispositivi di destinazione della regola. Il passaggio "Seleziona gruppi di dispositivi" verrà rimosso dalla console di Intune.

La sequenza temporale preliminare di questa modifica sarà le seguente:
- Nel giugno 2016, per i nuovi tenant non verrà visualizzato il secondo passaggio della procedura guidata di creazione di una regola di notifica. I tenant esistenti non sono interessati dalla modifica.
- In agosto 2016, per alcuni tenant esistenti non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.
- In ottobre 2016 per tutti i tenant non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.

<!---   TFS 1278864--->
**Modifiche al supporto dell'app Portale aziendale iOS.**
Nei prossimi mesi ci sarà un aggiornamento dell'app Portale aziendale di Microsoft Intune per iOS che supporterà i dispositivi che eseguono iOS 8.0 o versione successiva. Gli utenti non potranno più registrare nuovi dispositivi che eseguono versione precedenti a iOS 8.0. I dispositivi registrati che eseguono versioni precedenti a iOS 8.0 continueranno a essere gestiti e potranno, per un periodo di tempo limitato, continuare a usare l'app Portale aziendale. È necessario tuttavia che i dispositivi eseguano iOS 8.0 o versione successiva per accedere alle versioni più recenti dell'app Portale aziendale. È consigliabile richiedere agli utenti di eseguire l'aggiornamento a iOS 8.0 o versione successiva per poter usare al meglio le nuove funzionalità di Intune.  

- **App visualizzatore di Intune.** Con il rilascio della nuova app di condivisione RMS, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
    - Visualizzatore AV di Intune
    - Visualizzatore PDF di Intune
    - Visualizzatore immagini di Intune per Android disponibile in Google Play

  Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova app Rights Management (condivisione RMS) per Android che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Altre informazioni sull'app di condivisione RMS con collegamento alla documentazione.






### Vedere anche
Vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).


<!--HONumber=May16_HO5-->


