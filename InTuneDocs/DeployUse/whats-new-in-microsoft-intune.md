---
title: "Novità | Microsoft Intune"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d70a46d9c13aad1bc0a940836d83a99b93bb95e
ms.openlocfilehash: a753ecfa08adcd27049c70889c50e10618ecddba


---

# Novità di Microsoft Intune
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

## Agosto 2016
## Gestione delle app
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### App nascoste e mostrate per iOS 9.3
Per i dispositivi supervisionati che eseguono iOS 9.3 o versione successiva sarà possibile usare gli elenchi di app nascoste e mostrate nei criteri di configurazione generale di iOS per:
- Specificare un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
- Specificare un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.

Le app selezionabili includono sia le app distribuite che le app predefinite per iOS, ad esempio i Messaggi e Note. Per informazioni dettagliate, vedere [Impostazioni dei criteri di iOS in Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).
<!---TFS 1279009 checked--->
### Criteri delle app consentite e bloccate per i dispositivi Samsung KNOX
È ora possibile configurare un criterio personalizzato per i dispositivi Samsung KNOX che consente di creare:
- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Anche se installata, un'app presente nell'elenco delle app bloccate non può essere attivata nel dispositivo.
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. Le altre app dello Store non possono essere installate.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung KNOX.
Per informazioni dettagliate, vedere [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md) (Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung KNOX).
<!---TFS 1311629 checked --->
### Nuove app compatibili con i criteri di gestione di applicazioni mobili (MAM)
L'app Yammer per [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) è ora compatibile con i [criteri di gestione di applicazioni mobili di Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) a prescindere dal fatto che il dispositivo sia registrato o meno.

Per un elenco completo di app MAM compatibili, vedere il sito dei [partner che forniscono applicazioni per Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### App visualizzatore di Intune
Con il rilascio della nuova app RMS sharing, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
- Visualizzatore AV di Intune
- Visualizzatore PDF di Intune
- Visualizzatore immagini di Intune per Android disponibile in Google Play

Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova [app Rights Management (RMS sharing) per Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app) che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Quando l'app visualizzatore di Intune non sarà più supportata, verrà rimossa da Google Store e non sarà disponibile per l'uso futuro.

## Gestione dei dispositivi
### Supporto per Android 7.0
Intune fornirà il supporto immediato (Day 0) per l'imminente sistema operativo Android 7.0 per dispositivi mobili.
<!---TFS 1262053--->
### Rimozione di Google della funzionalità di reimpostazione remota del passcode nei dispositivi Android 7.0
Google sta rimuovendo la possibilità per gli amministratori IT e gli utenti finali di reimpostare in modalità remota il passcode dei dispositivi Android 7.0. In precedenza, gli amministratori IT potevano reimpostare in modalità remota il passcode di un utente e gli utenti finali potevano reimpostare i propri passcode dal sito Web del portale aziendale.



## Aggiornamenti del portale aziendale
### Sito Web del portale aziendale
- **Collegamento Commenti e suggerimenti di Microsoft dal portale aziendale** <br/>
Il sito Web del portale aziendale consente agli utenti finali di toccare un nuovo collegamento "Commenti e suggerimenti" nella parte inferiore della pagina per inviare commenti e suggerimenti a Microsoft relativamente alla propria esperienza con il sito. I commenti raccolti in modo anonimo consentiranno a Microsoft di migliorare l'esperienza del sito Web del portale aziendale per gli utenti.
<!--- TFS 1313657 checked--->

### iOS
- **Versione minima di Managed Browser per iOS aggiornata a 8.0**<br/>
L'app Managed Browser di Microsoft Intune per iOS è stata aggiornata per il supporto di dispositivi che eseguono iOS 8.0 o versione successiva. I dispositivi iOS 7.1 possono ancora usare l'app Managed Browser esistente. È tuttavia consigliabile invitare gli utenti a eseguire l'aggiornamento a iOS 8.0 o versione successiva per accedere a Managed Browser e sfruttare i vantaggi delle nuove funzionalità.  
<!---TFS 1313253 checked--->

## Sviluppi futuri
### Transizione dai gruppi di Intune ai gruppi di Azure Active Directory a partire dal mese di settembre 2016
Intune sta creando una nuova esperienza di gestione dei gruppi che usa i gruppi di sicurezza di Azure Active Directory (AAD) come gruppi di utenti e dispositivi in Intune. Questi gruppi verranno usati per la gestione dei gruppi, la distribuzione dei criteri e la distribuzione dei profili **con l'introduzione del nuovo portale di amministrazione di Intune basato su Azure**.

Questa nuova esperienza consentirà di evitare di duplicare i gruppi tra i servizi, **garantirà l'accesso ad alcune nuove funzionalità dei gruppi di Azure Active Directory Premium (AADP)** e offrirà estendibilità tramite PowerShell e Graph. Consentirà inoltre di unificare l'esperienza di gestione dei gruppi per tutta la gestione della mobilità aziendale.

Per abilitare il passaggio ai gruppi di sicurezza, la **console di amministrazione corrente** verrà sottoposta ad alcune modifiche. **Queste modifiche e l'uso dei gruppi di sicurezza di AAD saranno indicati nella documentazione di Intune**.

I clienti che non hanno familiarità con Intune visualizzeranno **alcune delle modifiche ai gruppi di sicurezza prima di dei tenant correnti**.

Oltre alle modifiche apportate alla gestione dei gruppi, **verranno deprecate le funzionalità seguenti**:
- Esclusione di membri o gruppi durante la creazione di un nuovo gruppo
- Gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati**
- **Gestisci gruppi** nel ruolo di amministratore del servizio
- Avvisi personalizzati in base al gruppo per le regole di notifica
- Calcolo pivot per gruppi nei report
<!--- TFS 1295329--->

### Aggiunta di "Notifiche" al Portale aziendale per Android
Nel mese di settembre verrà rilasciato un aggiornamento del portale aziendale per Android che presenterà una nuova icona delle **notifiche** nella home page. Toccando l'icona si avrà accesso alla pagina delle **notifiche** in cui l'utente finale visualizzerà tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. Se si usa l'app Portale aziendale per iOS, è già possibile visualizzare l'esperienza delle notifiche. Con l'introduzione della pagina **Notifiche**, non verrà visualizzata la pagina **Configurazione dell'accesso aziendale** ogni volta che si avvia o si riprende l'esecuzione del Portale aziendale per Android, purché il dispositivo sia già registrato. Molti utenti hanno creato materiale sussidiario per gli utenti finali ed è consigliabile dare tempestiva comunicazione a Microsoft nel caso possa essere necessario aggiornare tale materiale o le relative schermate. Aggiornare la documentazione in modo che rifletta le future modifiche nell'esperienza. Per le schermate aggiornate, visitare https://aka.ms/androidcpupdate.  

### Miglioramenti della modalità di recupero delle app per gli utenti finali di iOS
Le modifiche seguenti verranno apportate nel mese di settembre ai riquadri delle app nell'app Portale aziendale in modo che iOS indirizzi gli utenti con visualizzazioni diverse per tutte le app in un'unica posizione, il sito Web del portale aziendale. Attualmente, le restrizioni di Apple impediscono alle app dell'app store line-of-business e gestite di essere elencate nell'app Portale aziendale e richiedono agli utenti di visitare visualizzazioni diverse per trovare le proprie app.

- Il riquadro **App aziendali** attualmente fa riferimento a un elenco di tutte le app nella scheda TUTTE del sito Web del portale aziendale e continuerà a funzionare allo stesso modo. Il nome del riquadro verrà modificato in **Tutte le app**.
- Il riquadro **Altre app** attualmente punta a una vista, all'interno dell'app Portale aziendale, che elenca tutte le app che Apple consente all'app Portale aziendale di visualizzare. Il nome del riquadro verrà modificato in **App in evidenza** e toccandolo gli utenti verranno indirizzati alla scheda IN EVIDENZA del sito Web del portale aziendale.
-  Il riquadro **Categorie** attualmente punta a una vista, all'interno dell'app Portale aziendale, che elenca le categorie delle app. Il nome del riquadro non verrà modificato, ma ora punterà alla scheda CATEGORIE del sito Web del portale aziendale. È possibile trovare [qui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186) le schermate aggiornate.
<!---TFS 1317133--->

### Guida di orientamento per il cloud
Per ottenere informazioni sugli sviluppi futuri per Intune, vedere la [guida di orientamento Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Deprecazione del servizio
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Modifiche al supporto per l'app Portale aziendale per iOS**<br/>
Da settembre, tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS dovranno usare la versione più recente dell'app. I nuovi utenti potranno scaricare solo la versione più recente e gli utenti attuali dovranno aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, pertanto gli utenti dei dispositivi che eseguono versioni precedenti di iOS non saranno in grado di usare il portale aziendale o di eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.  

- **Versione minima di Managed Browser per iOS aggiornata a 8.0**<br/>
Nel mese di agosto Intune rilascerà un'app aggiornata di Managed Browser di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 8.0 o versione successiva. I dispositivi iOS 7.1 saranno ancora in grado di usare l'app Managed Browser esistente, tuttavia è consigliabile invitare gli utenti a eseguire l'aggiornamento a iOS 8.0 o versione successiva per accedere a Managed Browser e sfruttare i vantaggi delle nuove funzionalità.  
<!---TFS 1313253--->

- **Le app del portale aziendale per Windows 8 e Windows Phone 8 verranno deprecate a partire da settembre 2016** <br/>
Da settembre 2016, Microsoft Intune terminerà il supporto per le app del portale aziendale di Microsoft Intune per le piattaforme Windows Phone 8 e Windows 8. Aggiornare i dispositivi a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi.
<!---TFS 1255391--->

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



<!--HONumber=Aug16_HO4-->


