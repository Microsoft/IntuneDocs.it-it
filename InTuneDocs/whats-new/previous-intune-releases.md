---
title: Versioni precedenti | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3206634884807743576f2d9dc1ca17b6bbbc9cc6
ms.openlocfilehash: 996198a2525dc830d229e7143afda3c71f4276b8


---

# Versioni precedenti di Intune
## Agosto 2016
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

### Supporto di iOS 10
Intune supporta completamente iOS 10. Saranno disponibili altre informazioni in seguito al rilascio pubblico di iOS 10.

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

- **Le app del portale aziendale per Windows 8 e Windows Phone 8 verranno deprecate** <br/>
A partire da ottobre 2016, il supporto di Microsoft Intune per le app del portale aziendale di Windows Phone 8 e Windows 8 verrà deprecato. Verrà anche deprecato il supporto di Microsoft Intune per la piattaforma Windows Phone 8. Di conseguenza, non sarà possibile registrare o aggiornare i dispositivi Windows Phone 8. È possibile continuare a gestire i dispositivi Windows Phone 8 e Windows 8 che sono già registrati. Aggiornare i dispositivi Windows Phone 8 e Windows 8 a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi senza interruzioni.
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

## Luglio 2016
### Gestione delle app
#### Migliorare l'esperienza di aggiornamento del profilo di provisioning dell'app
Nelle app mobili line-of-business per Apple iOS sono inclusi un profilo di provisioning e un codice firmato con un certificato. Quando si esegue l'app in un dispositivo iOS, iOS conferma l'integrità dell'app e impone i criteri definiti dal profilo di provisioning.

La durata del certificato di firma dell'organizzazione usato per firmare le app in genere è di 3 anni. Tuttavia, il profilo di provisioning scade dopo un anno. Con questo aggiornamento, Intune offre gli strumenti per distribuire in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza, mentre il certificato è ancora valido. Per altre informazioni, vedere [ Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Usare i criteri del profilo di provisioning per dispositivi mobili iOS per mantenere aggiornate le app line-of-business)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
#### È disponibile Xamarin SDK per app Intune
Il componente Xamarin SDK per app Intune consente di abilitare le funzionalità di gestione delle app per dispositivi mobili Intune nelle app per dispositivi mobili iOS e Android compilate con Xamarin. È possibile trovare il componente nello [Store Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) o nella [pagina di GitHub di Microsoft Intune](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

### Gestione dei dispositivi
#### Limiti aumentati di registrazione dei dispositivi
Intune ha aumentato il limite massimo di registrazione dei dispositivi configurabili da 5 a 15 dispositivi per utente.
<!---TFS 1289896 --->

#### Integrazione di TeamViewer per PC Windows che eseguono il software client Intune
L'integrazione di [TeamViewer](https://www.teamviewer.com) per PC Windows che eseguono il client di Intune consente di avviare sessioni di assistenza remota con PC Windows per supportare i reparti Help Desk dell'utente finale. Sono inclusi Windows 7, 8, 8.1 e Windows 10. Per informazioni dettagliate, vedere [Attività comuni di gestione di PC Windows con client di Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md).
<!---TFS 1284856--->

### Aggiornamenti del portale aziendale
#### Sito Web del portale aziendale
- **Esperienza dell'utente finale migliorata durante la registrazione di dispositivi Windows**<br/>
Quando si usa l'accesso condizionale, la procedura di registrazione per Windows 8.1, Windows 10 Desktop e Windows 10 Mobile è stata semplificata nel sito Web del portale aziendale. Gli utenti ora visualizzeranno due procedure separate, "Registrazione dispositivi" e "Aggiunta all'area di lavoro". In questo modo sarà più semplice visualizzare lo stato del dispositivo e completare il processo se l'aggiunta all'area di lavoro (WPJ) ha avuto esito negativo. Le procedure separate dovrebbero inoltre semplificare il processo di risoluzione dei problemi per gli amministratori IT. In precedenza, quando gli utenti finali tentavano di registrarsi e tutti i passaggi della registrazione avevano esito positivo eccetto l'aggiunta all'area di lavoro, il dispositivo registrato non veniva visualizzato nell'elenco dei dispositivi per l'identificazione da parte degli utenti, causando confusione.

#### Android
- **App Portale aziendale Android**<br/>
Se gli utenti finali Android visualizzano un messaggio di errore che indica che al dispositivo manca un certificato obbligatorio, è possibile toccare il pulsante per la risoluzione del problema per ottenere la [procedura](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) per l'installazione del certificato mancante. Se gli utenti completano la procedura, ma visualizzano un altro messaggio di errore che indica che manca un certificato, verrà chiesto loro di contattare l'amministratore IT e fornirgli questo [collegamento](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), che contiene la procedura che gli amministratori IT possono usare per risolvere il problema del certificato.

- **Limitare l'installazione di app con trasferimento in locale in dispositivi registrati**<br/>
Nei dispositivi Android non è più possibile installare applicazioni tramite il sito Web del portale aziendale, a meno che i dispositivi siano stati registrati in Intune tramite l'app Portale aziendale per Android.
<!---TFS 1299082--->

#### iOS
- **Modifiche agli account Manager di registrazione dei dispositivi nell'app Portale aziendale per iOS**<br/>
Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi (DEM) nel riquadro **Dispositivi personali** dell'app Portale aziendale per iOS. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale.

L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune. Intune deprecherà anche l'uso degli account Manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi.

Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile. Per altre informazioni, vedere [Registrare i dispositivi di proprietà dell'azienda con Manager di registrazione dispositivi in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

### Modifica dei nomi delle funzionalità Windows
- [Microsoft Passport for Windows](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md) è ora noto come **Windows Hello for Business**.
- [Protezione dei dati aziendali](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) è ora noto come **Windows Information Protection**.

## Giugno 2016
### Integrità del servizio Intune
Le informazioni sull'integrità del servizio per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel portale di gestione di Office 365 in Integrità dei servizi. Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

### Gestione delle app
- **Esperienza avanzata di configurazione dei criteri di dati aziendali di Windows 10.** Sono stati apportati miglioramenti all'esperienza di configurazione dei criteri di protezione dei dati aziendali di Windows 10 con la creazione di regole di app, la definizione di limiti di rete e altre impostazioni di protezione dei dati aziendali. Per altre informazioni, vedere l'articolo relativo alla [creazione di un criterio di protezione dei dati aziendali con Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


### Gestione dei dispositivi
- **Impostazione di Windows Defender per la protezione da app potenzialmente indesiderate.** È stata aggiunta una nuova impostazione di Windows Defender denominata **Potentially Unwanted Application Detection (Rilevamento di applicazioni potenzialmente indesiderate)** ai criteri di configurazione generali per Windows 10 Desktop e Mobile. È possibile usare questa impostazione per la protezione di computer desktop Windows registrati da eventuale software in esecuzione classificato da Windows Defender come potenzialmente indesiderato. È possibile ottenere protezione da tali applicazioni in esecuzione o usare la modalità di controllo per rilevare l'installazione di un'applicazione potenzialmente indesiderata. Per altre informazioni, vedere [Impostazioni dei criteri di Windows 10 in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

### Accesso condizionale
- **Criteri di controllo di accesso di rete Cisco ISE per Intune.**  I clienti che usano Cisco Identity Service Engine (ISE) 2.1 e Microsoft Intune possono impostare i criteri di controllo di accesso di rete in ISE.

    Con l'uso di questi criteri, i dispositivi che devono connettersi alla rete tramite Wi-Fi o VPN devono soddisfare le condizioni seguenti prima di consentire l'accesso:

    * Devono essere gestiti da Intune
    * Devono essere compatibili con i criteri di compatibilità di Intune distribuiti

 Agli utenti finali di dispositivi non conformi verrà richiesto di eseguire la registrazione e risolvere eventuali problemi di conformità per ottenere l'accesso.
- **Accesso condizionale per il browser** È possibile impostare un criterio di accesso condizionale per [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) e [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) in modo che siano accessibili solo dai Web browser supportati su dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere a siti di Outlook Web Access (OWA) e SharePoint e con dispositivi iOS e Android verrà richiesto di registrare il dispositivo con Intune oltre che di risolvere eventuali problemi di non conformità prima di poter completare l'accesso.
<!---TFS 1175844--->

- **Dynamics CRM Online supporta l'accesso condizionale.** È possibile impostare un criterio di accesso condizionale per [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) in modo che sia accessibile solo da dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere all'applicazione per dispositivi mobili Dynamics CRM in iOS e Android sarà chiesto di registrarsi con Intune e di risolvere eventuali problemi di non conformità per poter completare l'accesso.
<!---TFS1295358--->

##Aggiornamenti dell'app Portale aziendale

#### App Portale aziendale Android

- Se gli amministratori IT applicano il nuovo criterio in base al quale i dispositivi impediscono l'installazione di app da origini sconosciute (Android 4.0 +), gli utenti finali con dispositivi Android 4.0 o versioni successive visualizzano il messaggio "L'installazione da origini sconosciute deve essere disabilitata". Gli utenti dovranno passare a  **Impostazioni** > **Sicurezza** e disattivare **Origini sconosciute**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sul messaggio e di sapere perché viene richiesta la disattivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio in base al quale i dispositivi devono abilitare la ricerca di minacce per la sicurezza nelle app (Android 4.0 +), gli utenti finali con dispositivi Android 4.0 o versioni successive visualizzano il messaggio "Cerca minacce per la sicurezza nel dispositivo". Gli utenti dovranno passare a **Impostazioni** > **Google** > **Sicurezza** e attivare **Cerca minacce per la sicurezza nel dispositivo**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sul messaggio e di sapere perché viene richiesta l'attivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio in base al quale il debug USB deve essere disabilitato (Android 4.2 +), gli utenti finali con dispositivi Android 4.2 o versioni successive visualizzano il messaggio "Il debug USB deve essere disabilitato". Gli utenti dovranno passare a **Impostazioni** > **Opzioni per gli sviluppatori** e disattivare **Debug USB**. Un collegamento nel messaggio di conformità consente agli utenti di ottenere altre [informazioni](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sul messaggio e di sapere perché viene richiesta la disattivazione dell'impostazione.

- Se gli amministratori IT applicano il nuovo criterio relativo al livello minimo di patch di protezione per Android (Android 6.0 +), gli utenti finali con dispositivi Android 6.0 o versioni successive visualizzano il messaggio "Questo dispositivo non rispetta il livello minimo di patch di protezione per Android". Gli utenti dovranno installare la patch di protezione richiesta. Un collegamento nel messaggio di conformità consente agli utenti di ottenere [informazioni](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) su come installare la patch di protezione richiesta e di vedere quale patch di protezione è attualmente installata.

#### App del portale aziendale iOS

- Durante l'installazione delle applicazioni line of business ora gli utenti finali vedranno un'esperienza di installazione delle app migliorata. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- L'app Portale aziendale di Microsoft Intune per iOS è stata aggiornata per supportare iOS versione 8.0 e successive. Questo aggiornamento significa che gli utenti finali possono installare l'app Portale aziendale e registrare i nuovi dispositivi in Intune solo se il dispositivo esegue iOS versione 8.0 o successiva. Gli utenti che hanno già iscritto dispositivi che eseguono una versione non supportata di iOS possono continuare a utilizzare l'app portale aziendale sul dispositivo.


## Maggio 2016

Tutte queste funzionalità sono supportate anche per le distribuzioni ibride (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la pagina delle [Novità per le funzionalità ibride](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Documentazione
Benvenuti nella versione di anteprima di [docs.microsoft.com](https://docs.microsoft.com/en-us/intune).
Questa piattaforma moderna completamente nuova è stata progettata per rendere più semplice per i nostri clienti comprendere e usare Intune.
Per informazioni su tutte le nuove funzionalità, vedere [Introducing docs.microsoft.com (Introduzione a docs.microsoft.com)](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Integrità del servizio Intune
Le informazioni sull'integrità del servizio per Intune sono state spostate in una posizione centrale con altri servizi Microsoft. Le informazioni sono ora disponibili nel [portale di gestione di Office 365](https://portal.office.com/Admin/Default.aspx) in **Integrità dei servizi**.
Per altre informazioni, vedere [questo post di blog](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Gestione delle app
- **MAM SDK: supporto per la configurazione della lunghezza del PIN.** Sarà possibile specificare la lunghezza del PIN per le app MAM in modo simile al PIN di un dispositivo. Gli utenti finali dovranno perciò conformarsi alle nuove limitazioni imposte. Vedranno la schermata del PIN leggermente modificata per tenere conto della lunghezza del PIN. Per informazioni dettagliate, vedere [Impostazioni dei criteri di gestione delle app per dispositivi mobili Android in Microsoft Intune](android-mam-policy-settings.md) e [Impostazioni dei criteri di gestione delle app per dispositivi mobili per iOS](ios-mam-policy-settings.md).

- **Skype for Business per iOS e Android.** È ora possibile scegliere come destinazione Skype for Business con [MAM senza criteri di registrazione](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md). Dopo la connessione degli utenti, verranno applicati i criteri MAM.

- **Sono disponibili nuove app per la gestione con criteri MAM.** Le app Microsoft Word, Excel e PowerPoint per Android possono ora essere associate a criteri MAM su dispositivi non registrati in Intune. Per visualizzare l'elenco completo delle app supportate, passare alla raccolta di applicazioni per dispositivi mobili di Microsoft Intune nella pagina dei [partner di Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### Aggiornamenti del portale aziendale

#### App Portale aziendale Android
- **Notifiche di tipo avviso popup per l'utente finale**: per gli utenti finali che registrano un dispositivo o lo rimuovono dal Portale aziendale vengono visualizzate notifiche di tipo avviso popup dell'app Portale aziendale per Android.

- **Modifiche agli account Manager di registrazione dispositivi nell'app Portale aziendale per Android.** Per migliorare le prestazioni e la scalabilità, Intune non mostrerà più tutti i dispositivi dei manager di registrazione dispositivi nel riquadro Dispositivi personali dell'app Portale aziendale per Android. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune.

#### Sito Web del portale aziendale
- **Sito Web del portale aziendale: il banner di identificazione del dispositivo offrirà maggiori informazioni agli utenti finali.** Gli utenti finali possono ora identificare facilmente il dispositivo selezionato durante l'uso del sito Web del portale aziendale. Se viene selezionato il dispositivo errato, gli utenti potranno selezionare il dispositivo corretto toccando il collegamento **Tocca qui** nel banner della pagina iniziale.

## Sviluppi futuri
- **Caricamento dell'interfaccia utente del centro messaggi**. Come parte della migrazione di Intune nel [portale di gestione di Office 365](https://portal.office.com/), inizieremo a sfruttare il suo centro messaggi per comunicare le nuove funzionalità e altre notifiche. Inoltre, installando l'app complementare per dispositivi mobili Office 365 Admin, è possibile ricevere notifiche sul cellulare e inoltrare facilmente qualsiasi messaggio agli utenti o a un alias di distribuzione.
Inizieremo a usare il centro messaggi con la nostra versione di maggio per notificare quando gli aggiornamenti sono completati e includeremo informazioni sulle funzionalità di Intune nuove e migliorate. Visitare il centro messaggi oggi stesso eseguendo l'accesso al [portale di gestione di Office 365](https://portal.office.com/) e scegliendo l'opzione Centro messaggi nel riquadro di spostamento a sinistra.

- **Modifiche agli account Manager di registrazione dispositivi**. Per migliorare le prestazioni e la scalabilità, Intune non visualizza più **tutti** i dispositivi dei manager di registrazione dispositivi nel riquadro **Dispositivi personali** dell'app Portale aziendale iOS. Sarà mostrato solo il dispositivo locale che esegue l'app e solo se viene registrato mediante l'app del Portale aziendale. L'utente del manager di registrazione dispositivi potrà eseguire azioni sul dispositivo locale, ma la gestione remota di altri dispositivi registrati potrà essere eseguita solo dalla console di amministrazione di Intune. Intune deprecherà anche l'uso degli account Manager di registrazione dispositivi con il programma di registrazione del dispositivo mobile di Apple o lo strumento Apple Configurator. Entrambi i metodi di registrazione già supportano la registrazione senza utente per i dispositivi iOS condivisi. Usare gli account manager di registrazione dispositivi solo quando la registrazione senza utente per i dispositivi condivisi non è disponibile.

### Guida di orientamento per il cloud
Per ottenere informazioni sugli sviluppi futuri per Intune, vedere la [guida di orientamento Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Deprecazione del servizio
- **App visualizzatore di Intune.** Con il rilascio della nuova app di condivisione RMS, all'inizio di agosto 2016 verranno rimosse le app visualizzatore di Intune seguenti:
    - Visualizzatore AV di Intune
    - Visualizzatore PDF di Intune
    - Visualizzatore immagini di Intune per Android disponibile in Google Play

  Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova app Rights Management (condivisione RMS) per Android che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Sono disponibili altre informazioni sull'app di condivisione RMS con collegamento alla documentazione.

- **Rimozione della capacità di scegliere gruppi personalizzati come destinazione delle regole di notifica.**
Le regole di notifica di Intune definiscono i destinatari degli avvisi di posta elettronica inviati da Intune. Attualmente è possibile configurare regole di notifica per inviare messaggi di posta elettronica a tutti gli utenti dei dispositivi di un gruppo di dispositivi di Intune creato. A partire dal 1° giugno 2016, la configurazione dei gruppi creati dagli utenti come destinazione non sarà più supportata.

    Attualmente, per impostare come destinazione di una regola di notifica un gruppo creato dalla console di amministrazione di Microsoft Intune, è necessario eseguire i passaggi seguenti:

    Nell'area di lavoro **Amministrazione** fare clic su **Regole di notifica** > **Crea nuova regola**

    Nel secondo passaggio della procedura guidata di creazione di una regola di notifica selezionare i gruppi di dispositivi di destinazione della regola. Il passaggio "Seleziona gruppi di dispositivi" verrà rimosso dalla console di Intune.

    La sequenza temporale preliminare di questa modifica sarà la seguente:
    - Nel giugno 2016 per i nuovi tenant non verrà visualizzato il secondo passaggio della procedura guidata di creazione di una regola di notifica. I tenant esistenti non sono interessati dalla modifica.
    - In agosto 2016 per alcuni tenant esistenti non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.
    - In ottobre 2016 per tutti i tenant non verrà visualizzato il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.


- **Modifiche al supporto dell'app Portale aziendale per iOS**. Nei prossimi mesi verrà eseguito un aggiornamento dell'app Portale aziendale di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 8.0 o versione successiva. Gli utenti non potranno più registrare nuovi dispositivi che eseguono versioni precedenti a iOS 8.0. I dispositivi registrati che eseguono versioni precedenti a iOS 8.0 continueranno a essere gestiti e potranno, per un periodo di tempo limitato, continuare a usare l'app Portale aziendale. È necessario tuttavia che i dispositivi eseguano iOS 8.0 o versione successiva per accedere alle versioni più recenti dell'app Portale aziendale. È consigliabile richiedere agli utenti di eseguire l'aggiornamento a iOS 8.0 o versione successiva per poter usare al meglio le nuove funzionalità di Intune.  


## Aprile 2016
Tutte queste funzionalità sono supportate anche per i clienti ibridi (Configuration Manager con Intune).
### Gestione delle app
- **Conformità utente MAM.**
È ora possibile visualizzare lo [stato](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) dei criteri di gestione delle applicazioni per ogni utente del tenant Azure Active Directory (AAD). Sono inclusi:
   - Dispositivi
   - App sul dispositivo

   Valori di stato:

   **Archiviato**: indica che il criterio è stato distribuito all'utente, l'app è stata usata nel contesto di lavoro e ha ricevuto correttamente i criteri.

    **Non archiviato**: indica che il criterio è stato distribuito all'utente, ma da quel momento l'app non è mai stata usata nel contesto di lavoro.


- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (Android).**
È disponibile una nuova impostazione per la [gestione delle applicazioni per dispositivi mobili](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) senza registrazione del dispositivo. Questa impostazione consente di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi Android. Quando l'impostazione è abilitata, le applicazioni di destinazione non possono più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, le applicazioni di destinazione possono salvare i contatti nella rubrica nativa. Quando [si cancella un dispositivo o un'app da remoto](wipe-managed-company-app-data-with-Microsoft-Intune.md), tutti i contatti che sono già stati salvati nella rubrica nativa vengono rimossi. Questa nuova impostazione è supportata inizialmente dall'applicazione Outlook sui dispositivi Android.

### Gestione dei dispositivi
- **Identificazione del numero di telefono per i dispositivi aziendali.** I telefoni classificati come "aziendali" sono ora identificati con il loro numero di telefono completo quando, per esempio, si esegue un report inventario dei dispositivi mobili. I numeri di telefono BYOD continuano a essere mascherati con **** mostrando solo le ultime 4 cifre.


### Aggiornamenti del Portale aziendale
Gli utenti di **app del Portale aziendale Android** che non hanno registrato il loro dispositivo in Intune e non hanno il certificato corretto installato non potranno accedere all'app del Portale aziendale Android e vedranno il messaggio "Non è possibile accedere. Manca un certificato necessario per il dispositivo". Il messaggio include il collegamento “Risoluzione del problema” che gli utenti possono usare per vedere le istruzioni per l'installazione del certificato. Per i passaggi che gli utenti finali devono eseguire per risolvere il problema vedere [Manca un certificato necessario per il dispositivo](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**App Portale aziendale iOS** È stato aggiunto il supporto per l'azione di scorrimento per aggiornare il contenuto della schermata iniziale, che include le app e i dispositivi elencati e le informazioni di contatto IT. L'azione di scorrimento per l'aggiornamento non controlla la conformità o le informazioni sui criteri, cosa che si può fare selezionando il riquadro per il dispositivo corrente e toccando il pulsante **Sincronizza**.

**App Portale aziendale per Windows 10 Mobile e Windows Phone 8.1** Il processo di installazione delle app line-of-business è stato migliorato. Se l'installazione delle app richiede molto tempo, gli utenti possono sincronizzare manualmente il dispositivo per forzare la ripresa del processo di sincronizzazione. Per le istruzioni per l'utente finale, vedere [Sincronizzare il dispositivo manualmente per velocizzare l'installazione delle app](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Sito Web Portale aziendale** Durante l'installazione delle app line-of-business, gli utenti di Windows 10 Mobile e Windows Phone 8.1 vedranno ora i seguenti stati nuovi, che specificano maggiori dettagli sullo stato della loro installazione:

* **In attesa della sincronizzazione del dispositivo**: l'utente ha toccato “Installa” e il dispositivo ora tenta di sincronizzarsi con l'infrastruttura Intune. La sincronizzazione è necessaria per poter completare l'installazione. Il messaggio "In attesa della sincronizzazione del dispositivo" è anche un collegamento che gli utenti possono toccare per vedere le [istruzioni](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) per sincronizzare manualmente il dispositivo con Intune, se il processo di sincronizzazione impiega troppo tempo o si blocca.
* **Download in corso**: la richiesta di download dell'utente è in fase di elaborazione e il dispositivo sta scaricando e installando l'app.

Prima dell'aggiunta di questi stati, gli utenti potevano essere confusi se l'installazione di un'app impiegava molto tempo, poiché vedevano solo lo stato "Installazione in corso", che poteva rimanere visualizzata sullo schermo per ore. Grazie all'aggiunta dei nuovi stati gli utenti, invece di chiamare il supporto, possono ora toccare il collegamento "In attesa della sincronizzazione del dispositivo" e seguire le istruzioni per forzare la ripresa del processo di sincronizzazione.


## Marzo 2016
### Novità a partire dal 29 marzo 2016
Fatta eccezione per l'aggiornamento dei criteri di configurazione generale di Windows 10, tutte le funzionalità della versione del 29 marzo 2016 sono supportate anche per i clienti ibridi (Configuration Manager con Intune). Il supporto ibrido per l'aggiornamento dei criteri di configurazione generale di Windows 10 sarà presto disponibile. Tenere presente che alcune di queste funzionalità richiedono l'ultima versione di Configuration Manager.

### Gestione delle app
- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (iOS).** È disponibile una nuova impostazione per la gestione delle applicazioni mobili senza registrazione del dispositivo. Questa impostazione consente di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi iOS. Quando l'impostazione è abilitata, l'applicazione non potrà più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, l'applicazione potrà salvare i contatti nella rubrica nativa. Quando si cancella un dispositivo in modo selettivo, tutti i contatti che sono già stati salvati nella rubrica nativa vengono rimossi. Questa nuova impostazione è supportata dall'applicazione Outlook sui dispositivi iOS. Per informazioni dettagliate su questa e altre impostazioni, vedere [Creare e distribuire i criteri MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Controllo di accesso
- **Skype for Business Online supporta l'accesso condizionale.** È possibile impostare un criterio di accesso condizionale per Skype for Business Online in modo che sia accessibile solo da dispositivi iOS e Android gestiti e conformi. Agli utenti finali che tentano di accedere all'applicazione per dispositivi mobili Skype for Business in iOS e Android sarà chiesto di registrarsi con Intune e di risolvere eventuali problemi di non conformità per poter completare l'accesso. Per informazioni dettagliate, vedere [Gestione dell'accesso a Skype for Business Online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Gestione dei dispositivi
- **Supporto Intune per iOS 9.3.** Lunedì 21 marzo Apple ha annunciato la disponibilità di iOS 9.3. Microsoft ha dedicato il massimo impegno a garantire la compatibilità di Microsoft Intune con la versione più recente del sistema operativo mobile di Apple ed [è lieta di annunciare che Intune supporta la gestione dei dispositivi iOS 9.3](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Tutte le funzionalità Intune esistenti attualmente disponibili per la gestione dei dispositivi iOS continueranno a funzionare senza problemi quando gli utenti aggiorneranno i dispositivi a iOS 9.3. Inoltre, iOS 9.3 è oggi supportato anche per i clienti ibridi (Configuration Manager con Intune).

- **I criteri di configurazione generale di Windows 10 includono ora impostazioni per la gestione di Windows Defender su PC Windows 10 registrati.** Per informazioni dettagliate vedere [Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Portale aziendale

- **Pacchetti delle app Windows disponibili direttamente dal Portale aziendale.** Gli utenti dei PC Windows 8, Windows 8.1 e Windows RT possono ora installare i pacchetti delle app Windows (con estensione appx) direttamente dal sito Web del portale aziendale. In precedenza era necessario eseguire la distribuzione, oppure, per poter installare le app, gli utenti dovevano installare l'app Portale aziendale sui loro dispositivi.

- **Gli utenti possono bloccare il dispositivo da remoto dal portale aziendale.** Al sito Web del portale aziendale è stata aggiunta una nuova opzione di blocco remoto che consente agli utenti finali di bloccare da remoto il dispositivo dal portale in caso di furto o smarrimento. Vedere le [istruzioni per l'utente](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). La tabella seguente riporta i dettagli di supporto della piattaforma relativi al blocco remoto per Intune Standalone e Intune con Configuration Manager.

|Piattaforma | Dettagli sul supporto|
|---------|----------------|
|Android |Supportato|
|iOS |Supportato|
|Windows 10 Mobile |Supportato solo se per il telefono è impostato un passcode|
|Windows 10 Desktop |Non supportato|
|Windows Phone 8.1 |Supportato solo se per il telefono è impostato un passcode|
|Windows Phone 8.0 |Non supportato|
|PC (Windows 8.0 e versioni precedenti) |Non supportato|
|PC (Windows 8.1) |Non supportato|

### Novità a partire dal 10 marzo 2016

### Gestione delle app

- **Vantaggi della gestione "Open-In" di iOS per dispositivi registrati in una soluzione MDM di terze parti** È possibile usare il proprio fornitore di gestione dei dispositivi mobili di terze parti (MDM) per godere dei vantaggi della gestione "Open-In"di iOS. È possibile impostare le restrizioni nelle impostazioni del profilo di configurazione e distribuire l'app usando le istruzioni in [Gestire il trasferimento di dati tra app iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

     Questo approccio presenta due vantaggi principali:

     1. Gli utenti devono accedere con l'account aziendale prima di ottenere l'accesso a tutti i dati aziendali dai servizi cloud o da altre app. Ciò garantisce la disponibilità dei criteri di gestione di applicazioni mobili (MAM) quando si accede ai dati.

     2. I profili di posta elettronica gestiti e altre app gestite distribuite con una soluzione MDM di terze parti possono condividere file e dati con le app che hanno criteri MAM di Intune.

- **Gestire l'app Microsoft Outlook con criteri MAM per dispositivi non registrati in Intune** Ora è possibile gestire l'app Microsoft Outlook su dispositivi non registrati in Intune con i criteri di gestione delle applicazioni mobili di Intune. L'app Microsoft Outlook aggiornata con le funzionalità MAM è disponibile per i dispositivi [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook). Usare le istruzioni nell'argomento [Creare e distribuire i criteri di gestione delle app per dispositivi mobili](https://technet.microsoft.com/library/mt627829.aspx) per creare un criterio MAM.  


- **I criteri di configurazione delle app per dispositivi mobili offrono più flessibilità per specificare i dettagli utente per le app iOS** È possibile specificare le impostazioni utente che possono risultare necessarie a un'app iOS quando viene aperta. Ad esempio, è possibile specificare una porta di rete o un nome utente. Per informazioni dettagliate vedere [Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Distribuire Adobe Reader per Microsoft Intune nei dispositivi iOS aziendali gestiti da Intune** Ora è possibile gestire l'app Adobe Reader iOS su dispositivi registrati con i criteri di gestione delle applicazioni mobili di Intune.

- **Verificare che le clip Web distribuite vengano aperte in Managed Browser** È possibile distribuire clip Web specifiche che possono essere aperte solo con Managed Browser nei dispositivi iOS e Android. Ad esempio, se si distribuiscono i collegamenti alle risorse aziendali con il portale aziendale, quando gli utenti accedono ai collegamenti li aprono direttamente in Managed Browser, dove possono essere protetti con i criteri MAM. Per informazioni dettagliate vedere [Distribuire le app](deploy-apps.md).


- **Trovare, gestire e distribuire app Windows Store for Business per dispositivi Windows 10 dalla console di amministrazione di Intune** In Intune è disponibile il supporto per Windows Store for Business, che consente di trovare, gestire e distribuire app ai dispositivi Windows 10 gestiti. Windows Store per le aziende consente di gestire il processo di distribuzione e monitoraggio di queste app dalla console di amministrazione di Intune, la stessa console usata per gestire le altre app. In particolare, Windows Store per le aziende gestisce i contenuti e le licenze delle app con licenze online. Per informazioni dettagliate vedere [Gestire le app acquistate in Windows Store for Business](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Gestione dei dispositivi
- **Distribuzione di certificati PFX per dispositivi iOS** Gli amministratori di Intune possono creare e distribuire certificati PFX di iOS per Wi-Fi, posta elettronica e autenticazione VPN nei dispositivi iOS. Questa funzionalità è già disponibile per i dispositivi Android e Windows 10. Per informazioni dettagliate vedere [Abilitare l'accesso alle risorse aziendali usando i profili certificato](secure-resource-access-with-certificate-profiles.md).


- **Applicare app e criteri a gruppi di dispositivi diversi in base alla selezione di categorie utente** Gli amministratori di Intune possono ora definire categorie di dispositivi personalizzate selezionabili dagli utenti durante la registrazione. Ad esempio, gli amministratori possono consentire agli utenti di specificare se il dispositivo che stanno registrando viene usato per operazioni relative a "Registratore di cassa", "Camion per le consegne" o "Inventario". La selezione della categoria comporta l'inserimento del dispositivo come membro di un gruppo di dispositivi di Intune, che può essere usato per la distribuzione di diverse app e criteri al dispositivo registrato. Per informazioni dettagliate vedere [Classificare i dispositivi con il mapping del gruppo di dispositivi](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Modifiche e aggiornamenti del portale aziendale Microsoft
In questa versione sono state apportate le modifiche seguenti al portale aziendale.

**App Portale aziendale Android**

* Quando gli utenti avviano un'app gestita da Gestione di applicazioni mobili (MAM), visualizzeranno un messaggio di notifica che informa che l'applicazione è gestita dalla propria società. Gli utenti possono ora toccare un collegamento "Altre informazioni" per ottenere [altre informazioni](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) su cosa significa "app gestite". È anche possibile toccare "Non mostrare più" in modo che il messaggio non sia più visualizzato quando si avvia l'applicazione.
* Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
* I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.


**App del portale aziendale iOS**
* Quando gli utenti avviano un'app gestita da Gestione di applicazioni mobili (MAM), visualizzeranno un messaggio di notifica che informa che l'applicazione è gestita dalla propria società. Gli utenti possono ora toccare un collegamento "Altre informazioni" per ottenere [altre informazioni](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) su cosa significa "app gestite". È anche possibile toccare "Non mostrare più" in modo che il messaggio non sia più visualizzato quando si avvia l'applicazione.
* Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).
* I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.




## Febbraio 2016
### Modifiche e aggiornamenti del portale aziendale Microsoft

In questa versione sono state apportate le modifiche seguenti al portale aziendale.

#### App Portale aziendale Android
- Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc).
- I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.

#### App del portale aziendale iOS
 - Sono state aggiunte nuove schermate per guidare gli utenti attraverso il processo di registrazione e fornire altre informazioni sui motivi per cui gli utenti devono registrarsi e cosa possono/non possono vedere gli amministratori IT nei propri dispositivi registrati. Per informazioni dettagliate, vedere le [istruzioni per la registrazione](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device).

 - I messaggi di errore di registrazione sono ora visualizzati nell'App del portale aziendale. In precedenza, questi messaggi erano visualizzati nel sito Web del portale aziendale. Apportando tale modifica, tutti i messaggi di errore saranno ora visualizzati in un unico posto, invece che in due posti diversi.


## Gennaio 2016

### Sfruttare le funzionalità di Windows 10
* **Accesso condizionale con il servizio di attestazione dell'integrità** Gli amministratori possono ora visualizzare lo stato di attestazione dell'integrità dei dispositivi Windows 10 nella console di amministrazione di Intune. L'attestazione dell'integrità dei dispositivi consente all'amministratore di assicurare che i computer client dispongano di configurazioni attendibili di BIOS, TPM e software di avvio. Per supportare l'attestazione dell'integrità dei dispositivi, i dispositivi client devono eseguire Windows 10 con TPM 2 abilitato. L'attestazione dell'integrità dei dispositivi visualizza il numero di dispositivi abilitati per ognuno degli elementi seguenti:
    * Antimalware ad esecuzione anticipata
    * BitLocker
    * Avvio protetto
    * Integrità del codice

    Per altre informazioni sull'attestazione dell'integrità del dispositivo, sui punti dati raccolti e sul report di attestazione dell'integrità, leggere [Gestire i criteri di conformità del dispositivo per Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md). L'articolo relativo al [servizio HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) ne illustra le caratteristiche in modo approfondito.

* **Criteri Passport for Work e gestione dei certificati in Windows 10** Con Intune è possibile [eseguire l'integrazione con Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), un metodo di accesso alternativo per Windows 10 che usa Active Directory o un account Azure Active Directory per sostituire una password, una smart card o una smart card virtuale. Passport consente di eseguire l'accesso usando un movimento dell'utente, anziché una password. Un movimento dell'utente può essere un PIN semplice, l'autenticazione biometrica come Windows Hello o un dispositivo esterno come un lettore di impronte digitali.

* **VPN per app specifiche** È possibile selezionare app che si connettono automaticamente alla rete aziendale tramite VPN. Creare l'elenco di app quando si configura il profilo VPN, come descritto in Consentire agli utenti di connettersi al proprio lavoro tramite profili VPN con Microsoft Intune.

* **Supporto della cancellazione completa di Windows 10** È ora possibile eseguire una cancellazione remota completa nei dispositivi desktop Windows 10 registrati in Intune con la console di amministrazione di Intune. La cancellazione completa di Windows 10 esegue un ripristino delle impostazioni predefinite del dispositivo.


### Aggiornamento di Volume Purchase Program (VPP) di Apple
Intune consente ora di [gestire le app acquistate attraverso il Volume Purchase Program (VPP) di Apple per aziende](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Ciò include la sincronizzazione delle informazioni di licenza tra Apple e Intune e la verifica del numero di copie di ogni app distribuito.

### Usare i numeri IMEI per identificare i dispositivi di proprietà dell'azienda
È ora possibile [importare i numeri IMEI (International Mobile Equipment Identity)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) per le piattaforme per dispositivi mobili dotate di un numero IMEI per identificare i dispositivi mobili aziendali. Una volta registrati in Intune, i dispositivi con numeri IMEI importati vengono contrassegnati come aziendali, che possono essere usati per l'applicazione di criteri diversi da quelli applicati ai dispositivi personali.

### Un numero maggiore di app è ora compatibile con i criteri MAM di Intune
Le app aggiuntive dei partner Microsoft sono ora compatibili con i criteri di gestione di applicazioni mobili di Intune (MAM) per i dispositivi gestiti da Intune:
* Box for EMM (di Box Inc): solo iOS
* Adobe Reader (di Adobe): solo Android
* Foxit PDF Reader (di Foxit Corporation): iOS e Android


### Il supporto di Internet Explorer 9 termina a gennaio
A partire da febbraio 2016, Internet Explorer 9 non verrà più supportato come browser ufficiale per l'accesso al sito Web del portale aziendale di Microsoft Intune, al portale per gli account di Intune e alla console di amministrazione di Intune. Sarà necessario eseguire la migrazione a Internet Explorer 10 o versioni successive.


>[!div class="step-by-step"]

>[&larr; **Novità in Intune**](whats-new-in-microsoft-intune.md)    



<!--HONumber=Sep16_HO2-->

