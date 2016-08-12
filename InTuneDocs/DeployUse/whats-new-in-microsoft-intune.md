---
title: "Novità | Microsoft Intune"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 68af4d7f0b082f14e6f9c06f8739805f9590384e
ms.openlocfilehash: 64bd2e3c8e8da3949634a544eb2c582e889c8209


---

# Novità di Microsoft Intune
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Agosto 2016
## Aggiornamenti del portale aziendale

### Android
- **App Portale aziendale Android**<br/>
L'app Portale aziendale per Android fornisce supporto immediato (Day 0) per l'imminente sistema operativo Android 7.0 per dispositivi mobili.  

- **Rimozione di Google della funzionalità di reimpostazione remota del passcode nei dispositivi Android 7.0**<br/>
Nei dispositivi Android 7.0 gli amministratori IT di Intune e gli utenti finali non potranno reimpostare in modalità remota il passcode del dispositivo perché Google ha rimosso questa funzionalità per i dispositivi Android 7.0. Per le versioni precedenti ad Android 7.0, gli amministratori IT potranno ancora reimpostare in remoto il passcode di un utente e gli utenti finali potranno ancora reimpostare i passcode dal sito Web del portale aziendale.

## Luglio 2016
## Gestione delle app
### Migliorare l'esperienza di aggiornamento del profilo di provisioning dell'app
Nelle app mobili line-of-business per Apple iOS sono inclusi un profilo di provisioning e un codice firmato con un certificato. Quando si esegue l'app in un dispositivo iOS, iOS conferma l'integrità dell'app e impone i criteri definiti dal profilo di provisioning.

La durata del certificato di firma dell'organizzazione usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Con questo aggiornamento, Intune offre gli strumenti per distribuire in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza, mentre il certificato è ancora valido. Per altre informazioni, vedere [ Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Usare i criteri del profilo di provisioning per dispositivi mobili iOS per mantenere aggiornate le app line-of-business)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
### È disponibile Xamarin SDK per app Intune
Il componente Xamarin SDK per app Intune consente di abilitare le funzionalità di gestione delle app per dispositivi mobili Intune nelle app per dispositivi mobili iOS e Android compilate con Xamarin. È possibile trovare il componente nello [Store Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) o nella [pagina di GitHub di Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

## Gestione dei dispositivi
### Limiti aumentati di registrazione dei dispositivi
Intune ha aumentato il limite massimo di registrazione dei dispositivi configurabili da 5 a 15 dispositivi per utente.
<!---TFS 1289896 --->

### Integrazione di TeamViewer per PC Windows che eseguono il software client Intune
L'integrazione di [TeamViewer](https://www.teamviewer.com) per PC Windows che eseguono il client di Intune consente di avviare sessioni di assistenza remota con PC Windows per supportare i reparti Help Desk dell'utente finale. Sono inclusi Windows 7, 8, 8.1 e Windows 10. Per informazioni dettagliate, vedere [Attività comuni di gestione di PC Windows con client di Microsoft Intune](intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

## Aggiornamenti del portale aziendale
### Sito Web del portale aziendale
- **Esperienza dell'utente finale migliorata durante la registrazione di dispositivi Windows**<br/>
Quando si usa l'accesso condizionale, la procedura di registrazione per Windows 8.1, Windows 10 Desktop e Windows 10 Mobile è stata semplificata nel sito Web del portale aziendale. Gli utenti ora visualizzeranno due procedure separate, "Registrazione dispositivi" e "Aggiunta all'area di lavoro". In questo modo sarà più semplice visualizzare lo stato del dispositivo e completare il processo se l'aggiunta all'area di lavoro (WPJ) ha avuto esito negativo. Le procedure separate dovrebbero inoltre semplificare il processo di risoluzione dei problemi per gli amministratori IT. In precedenza, quando gli utenti finali tentavano di registrarsi e tutti i passaggi della registrazione avevano esito positivo eccetto l'aggiunta all'area di lavoro, il dispositivo registrato non veniva visualizzato nell'elenco dei dispositivi per l'identificazione da parte degli utenti, causando confusione.

### Android
- **App Portale aziendale Android**<br/>
Se gli utenti finali Android visualizzano un messaggio di errore che indica che al dispositivo manca un certificato obbligatorio, è possibile toccare il pulsante per la risoluzione del problema per ottenere la [procedura](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) per l'installazione del certificato mancante. Se gli utenti completano la procedura, ma visualizzano un altro messaggio di errore che indica che manca un certificato, verrà chiesto loro di contattare l'amministratore IT e fornirgli questo [collegamento](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), che contiene la procedura che gli amministratori IT possono usare per risolvere il problema del certificato.

- **Limitare l'installazione di app con trasferimento in locale in dispositivi registrati**<br/>
Nei dispositivi Android non è più possibile installare applicazioni tramite il sito Web del portale aziendale, a meno che i dispositivi siano stati registrati in Intune tramite l'app Portale aziendale per Android.
<!---TFS 1299082--->

### iOS
- **Modifiche agli account Manager di registrazione dei dispositivi nell'app Portale aziendale per iOS**<br/>
Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi (DEM) nel riquadro **Dispositivi personali** dell'app Portale aziendale per iOS. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale.

    L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune. Intune deprecherà anche l'uso degli account Manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi.

    Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile. Per altre informazioni, vedere [Registrare i dispositivi di proprietà dell'azienda con Manager di registrazione dispositivi in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

## Modifica dei nomi delle funzionalità Windows
- [Microsoft Passport for Windows](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) è ora noto come **Windows Hello for Business**.
- [Protezione dei dati aziendali](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) è ora noto come **Windows Information Protection**.

## Sviluppi futuri
### Transizione dai gruppi di Intune ai gruppi di Azure Active Directory con inizio ad agosto 2016
Intune sta creando una nuova esperienza di gestione dei gruppi che usa i gruppi di sicurezza di Azure Active Directory (AAD). Questi gruppi di sicurezza basati su Azure AD possono contenere utenti e dispositivi e verranno usati per la gestione dei gruppi, la distribuzione dei criteri e la distribuzione dei profili con l'introduzione del nuovo portale di amministrazione di Intune basato su Azure.

Questa nuova esperienza consentirà di:
- Evitare di duplicare i gruppi tra i servizi.
- Avere accesso ad alcune nuove funzionalità dei gruppi di Azure Active Directory Premium (AADP).
- Offrire estendibilità tramite PowerShell e Graph.
- Unificare l'esperienza di gestione dei gruppi per la gestione della mobilità aziendale.

Per abilitare il passaggio ai gruppi di sicurezza, l'esperienza nella console di amministrazione corrente verrà sottoposta ad alcune modifiche. Queste modifiche e l'uso dei gruppi di sicurezza di Azure AD saranno indicati nella documentazione di Intune.

I clienti che non hanno familiarità con Intune visualizzeranno alcune delle modifiche ai gruppi di sicurezza prima dei tenant correnti.

Oltre alle modifiche apportate alla gestione dei gruppi, verranno deprecate le funzionalità seguenti:
- Esclusione di membri o gruppi durante la creazione di un nuovo gruppo
- Gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati**
- **Gestisci gruppi** nel ruolo di amministratore del servizio
- Avvisi personalizzati in base al gruppo per le regole di notifica
- Calcolo pivot per gruppi nei report

Maggiori informazioni sulle modalità di migrazione di questi elementi deprecati verranno rilasciate nel mese di agosto.

### Aggiunta di "Notifiche" al Portale aziendale per Android
Nel mese di settembre verrà rilasciato un aggiornamento del portale aziendale per Android che presenterà una nuova icona delle **notifiche** nella home page. Toccando l'icona si avrà accesso alla pagina delle **notifiche** in cui l'utente finale visualizzerà tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. Se si usa l'app Portale aziendale per iOS, è già possibile visualizzare l'esperienza delle notifiche. Con l'introduzione della pagina **Notifiche**, non verrà visualizzata la pagina **Configurazione dell'accesso aziendale** ogni volta che si avvia o si riprende l'esecuzione del Portale aziendale per Android, purché il dispositivo sia già registrato. Molti utenti hanno creato materiale sussidiario per gli utenti finali ed è consigliabile dare tempestiva comunicazione a Microsoft nel caso possa essere necessario aggiornare tale materiale o le relative schermate. Aggiornare la documentazione in modo che rifletta le future modifiche nell'esperienza. Per le schermate aggiornate, visitare https://aka.ms/androidcpupdate.  



### Guida di orientamento per il cloud
Per ottenere informazioni sugli sviluppi futuri per Intune, vedere la [guida di orientamento Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Deprecazione del servizio
- **Modifiche al supporto per l'app Portale aziendale per iOS**<br/>
Da settembre, tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS dovranno usare la versione più recente dell'app. I nuovi utenti potranno scaricare solo la versione più recente e gli utenti attuali dovranno aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, pertanto gli utenti dei dispositivi che eseguono versioni precedenti di iOS non saranno in grado di usare il portale aziendale o di eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.  

- **Versione minima di Managed Browser per iOS aggiornata a 8.0**<br/>
Nel mese di agosto Intune rilascerà un'app aggiornata di Managed Browser di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 8.0 o versione successiva. I dispositivi iOS 7.1 saranno ancora in grado di usare l'app Managed Browser esistente, tuttavia è consigliabile invitare gli utenti a eseguire l'aggiornamento a iOS 8.0 o versione successiva per accedere a Managed Browser e sfruttare i vantaggi delle nuove funzionalità.  
<!---TFS 1313253--->

- **Le app del portale aziendale per Windows 8 e Windows Phone 8 verranno deprecate a partire da settembre 2016** <br/>
Da settembre 2016, Microsoft Intune terminerà il supporto per le app del portale aziendale di Microsoft Intune per le piattaforme Windows Phone 8 e Windows 8. Aggiornare i dispositivi a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi.
<!---TFS 1255391--->

- **App visualizzatore di Intune** <br/>
Con il rilascio della nuova app di condivisione RMS, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
    - Visualizzatore AV di Intune
    - Visualizzatore PDF di Intune
    - Visualizzatore immagini di Intune per Android disponibile in Google Play

  Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova [app Rights Management (RMS sharing) per Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app) che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Quando l'app visualizzatore di Intune non sarà più supportata, verrà rimossa da Google Store e non sarà disponibile per l'uso futuro.

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->



## Versioni precedenti di Intune
Per vedere cosa è stato rilasciato in Intune negli ultimi sei mesi, leggere l'articolo [Versioni precedenti di Intune](previous-intune-releases.md).

### Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Aug16_HO2-->


