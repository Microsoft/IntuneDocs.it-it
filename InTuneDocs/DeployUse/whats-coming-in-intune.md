---
title: Sviluppi futuri | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 07/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 35ee5d0c8898c95898c0527a623cf13c454387f2
ms.openlocfilehash: 831cec6cd0e02a94c1a3f67d4adf5a5dcbb01449


---

# Sviluppi futuri in Microsoft Intune - Luglio
Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Controllare regolarmente la pagina per conoscere gli sviluppi futuri.

Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Gestione delle app
### Migliorare l'esperienza di aggiornamento del profilo di provisioning dell'app
Nelle app mobili line-of-business per Apple iOS sono inclusi un profilo di provisioning e un codice firmato con un certificato. Quando si esegue l'app in un dispositivo iOS, iOS conferma l'integrità dell'app e impone i criteri definiti dal profilo di provisioning.

La durata del certificato di firma dell'organizzazione usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Con questo aggiornamento, Intune offrirà gli strumenti per distribuire in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza, mentre il certificato è ancora valido.
<!--- TFS 1280247--->

### Supporto di Xamarin
Microsoft Intune App SDK supporta le app Xamarin in questi scenari:

- Scrittura di nuove app o modifica del codice di app line of business esistenti mediante l'SDK di Intune. È possibile ottenere il plug-in nella pagina [Microsoft Intune GitHub](https://github.com/msintuneappsdk).
- Aggiunta del supporto MAM ad app line of business esistenti mediante lo strumento di wrapping delle app di Intune

Per informazioni su come scegliere il metodo da usare, vedere [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).

<!--- TFS 1061478 & TFS 1152340--->

## Gestione dei dispositivi
### Limiti aumentati di registrazione dei dispositivi
Intune aumenterà il limite massimo di registrazione dei dispositivi configurabili da 5 a 15 dispositivi per utente.
<!---TFS 1289896 --->

## Gestione dei gruppi
### Transizione dai gruppi di Intune ai gruppi di Azure Active Directory con inizio ad agosto 2016
Intune sta creando una nuova esperienza di gestione dei gruppi che usa i gruppi di sicurezza di Azure Active Directory (AAD) come gruppi di utenti e dispositivi in Intune. Questi gruppi verranno usati per la gestione dei gruppi, la distribuzione dei criteri e la distribuzione dei profili **con l'introduzione del nuovo portale di amministrazione di Intune basato su Azure**.

Questa nuova esperienza consentirà di evitare di duplicare i gruppi tra i servizi, **garantirà l'accesso ad alcune nuove funzionalità dei gruppi di Azure Active Directory Premium (AADP)** e offrirà estendibilità tramite PowerShell e Graph. Consentirà inoltre di unificare l'esperienza di gestione dei gruppi per tutta la gestione della mobilità aziendale.

Per abilitare il passaggio ai gruppi di sicurezza, la **console di amministrazione corrente** verrà sottoposta ad alcune modifiche. **Queste modifiche e l'uso dei gruppi di sicurezza di AAD saranno indicati nella documentazione di Intune**.

I clienti che non hanno familiarità con Intune visualizzeranno **alcune delle modifiche ai gruppi di sicurezza prima di dei tenant correnti**.

Oltre alle modifiche apportate alla gestione dei gruppi, **verranno deprecate le funzionalità seguenti**:
- Esclusione di membri o gruppi durante la creazione di un nuovo gruppo
- "Gestisci gruppi" nel ruolo di amministratore del servizio
- Avvisi personalizzati in base al gruppo per le regole di notifica
- Calcolo pivot per gruppi nei report


## Portale aziendale

### Aggiunta di "Notifiche" al Portale aziendale per Android
Nel mese di agosto verrà rilasciato un aggiornamento del Portale aziendale per Android che presenterà una nuova icona delle **notifiche** nella home page. Toccando l'icona si avrà accesso alla pagina delle **notifiche** in cui l'utente finale visualizzerà tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. Se si usa l'app Portale aziendale per iOS, è già possibile visualizzare l'esperienza delle notifiche. Con l'introduzione della pagina **Notifiche**, non verrà visualizzata la pagina **Configurazione dell'accesso aziendale** ogni volta che si avvia o si riprende l'esecuzione del Portale aziendale per Android, purché il dispositivo sia già registrato. Molti utenti hanno creato materiale sussidiario per gli utenti finali ed è consigliabile dare tempestiva comunicazione a Microsoft nel caso possa essere necessario aggiornare tale materiale o le relative schermate. Aggiornare la documentazione in modo che rifletta le future modifiche nell'esperienza. Per le schermate aggiornate, visitare https://aka.ms/androidcpupdate  

### Aiutare gli utenti nella risoluzione dei problemi di registrazione quando l'aggiunta all'area di lavoro ha esito negativo
Quando si usa l'accesso condizionale, la procedura di registrazione per Windows 8.1, Windows 10 Desktop e Windows 10 Mobile è stata semplificata nel sito Web del portale aziendale per gli utenti finali per i quali l'aggiunta all'area di lavoro (WPJ) ha avuto esito negativo. In precedenza, quando gli utenti finali tentavano di registrarsi ed eseguire un'aggiunta all'area di lavoro e la registrazione aveva esito positivo ma l'aggiunta all'area di lavoro aveva esito negativo, il dispositivo registrato non veniva visualizzato nell'elenco dei dispositivi per l'identificazione da parte degli utenti, causando confusione. Gli utenti ora visualizzeranno due procedure separate, "Registrazione dispositivi" e "Aggiunta all'area di lavoro". In questo modo, sarà più semplice visualizzare lo stato del dispositivo e completare la procedura dopo l'errore dell'aggiunta all'area di lavoro. Le procedure separate dovrebbero inoltre semplificare il processo di risoluzione dei problemi per gli amministratori IT.

### Modifiche agli account Manager di registrazione dei dispositivi nell'app Portale aziendale per iOS
Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro Dispositivi personali dell'app del Portale aziendale iOS. Verrà visualizzato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.  Intune deprecherà anche l'uso degli account Manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi. Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile.
<!---TFS 1233681--->
### Limitare l'installazione di app con trasferimento in locale in dispositivi Android registrati
Nei dispositivi Android non è più possibile installare applicazioni tramite il sito Web del portale aziendale, a meno che i dispositivi siano stati registrati in Intune tramite l'app Portale aziendale per Android. 
<!---TFS 1299082--->

## Deprecazione del servizio
**Le app del portale aziendale per Windows 8 e Windows Phone 8 sono deprecate a partire da settembre 2016.** Da settembre 2016, Microsoft Intune terminerà il supporto per le app del portale aziendale di Microsoft Intune per le piattaforme Windows Phone 8 e Windows 8. Aggiornare i dispositivi a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi.
<!---TFS 1255391--->

**Rimozione della capacità di scegliere gruppi personalizzati come destinazione delle regole di notifica.**
Le regole di notifica di Intune definiscono i destinatari degli avvisi di posta elettronica inviati da Intune. Attualmente è possibile configurare regole di notifica per inviare messaggi di posta elettronica a tutti gli utenti dei dispositivi di un gruppo di dispositivi di Intune creato. A partire dal 1° giugno 2016, la configurazione dei gruppi creati dagli utenti come destinazione non sarà più supportata.

La sequenza temporale preliminare di questa modifica sarà la seguente:
- Da agosto 2016 per i nuovi tenant non verrà visualizzato il secondo passaggio della procedura guidata di creazione di una regola di notifica. I tenant esistenti non sono interessati dalla modifica.
- Da settembre 2016 per alcuni tenant esistenti non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.
- Da novembre 2016 per tutti i tenant non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.

<!---   TFS 1278864--->

**Modifiche al supporto dell'app Portale aziendale iOS.**
Da luglio tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS dovranno usare la versione più recente dell'app. I nuovi utenti potranno scaricare solo la versione più recente e gli utenti attuali dovranno aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, pertanto gli utenti dei dispositivi che eseguono versioni precedenti di iOS non saranno in grado di usare il portale aziendale o di eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.  

**App visualizzatore di Intune.** Con il rilascio della nuova app di condivisione RMS, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
- Visualizzatore AV di Intune
- Visualizzatore PDF di Intune
- Visualizzatore immagini di Intune per Android disponibile in Google Play

Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova app Rights Management (condivisione RMS) per Android che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Sono disponibili altre informazioni sull'app di condivisione RMS con collegamento alla documentazione.



### Vedere anche
Vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Jul16_HO3-->


