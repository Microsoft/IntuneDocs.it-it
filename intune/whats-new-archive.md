---
title: "Novità dei mesi precedenti per Microsoft Intune"
titlesuffix: 
description: "Rileggere gli annunci precedenti dalla pagina delle novità di Intune"
keywords: 
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/19/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7ba6262c1126a421f2e2ca0e5085796c11df8d9a
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novità di Microsoft Intune - mesi precedenti

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="october-2017"></a>Ottobre 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>Il numero di versione delle app line-of-business iOS e Android è visibile <!-- 1380712 -->

Nelle app in Intune viene ora visualizzato il numero di versione per le app line-of-business iOS e Android. Il numero viene visualizzato nel portale di Azure nell'elenco delle app e nel pannello della panoramica dell'app. Gli utenti finali possono visualizzare il numero dell'app nell'app Portale aziendale e nel portale Web.

__Numero di versione completo__ Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800)

Il numero di versione completo include due componenti:

 - **Versione**  
   Il numero di versione è il numero di versione leggibile dell'app. Viene usato dagli utenti finali per identificare diverse versioni dell'app.

 - **Numero di build**  
    Il numero di build è un numero interno che può essere usato nel rilevamento delle app e per gestire l'app a livello di codice. Il numero di build si riferisce a un'iterazione dell'app che fa riferimento alle modifiche nel codice.

Per altre informazioni sui numeri di versione e lo sviluppo di app line-of-business, vedere [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integrazione della gestione delle applicazioni e dei dispositivi <!-- 677972 -->   
Ora che la gestione di dispositivi mobili (MDM) e la gestione di applicazioni mobili (MAM) di Intune sono entrambe accessibili dal portale di Azure, in Intune è stata iniziata l'integrazione dell'esperienza di amministrazione IT nella gestione delle applicazioni e dei dispositivi. Queste modifiche hanno lo scopo di rendere più semplice l'esperienza di gestione dei dispositivi e delle app.

Per altre informazioni sulle modifiche MDM e MAM annunciate, vedere il [blog del team di supporto di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nuovi avvisi di registrazione per i dispositivi Apple <!-- 1471790 -->
Nella pagina di panoramica per la registrazione verranno visualizzati avvisi utili per gli amministratori IT riguardanti la gestione dei dispositivi Apple. Gli avvisi verranno visualizzati nella pagina Panoramica quando il certificato per le notifiche push MDM Apple sta per scadere o è già scaduto, quando il token di Device Enrollment Program sta per scadere o è già scaduto e quando vi sono dispositivi non assegnati in Device Enrollment Program.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Sostituzione dei token di supporto per la configurazione di app senza registrazione del dispositivo <!-- 1080364 -->

È possibile usare i token per i valori dinamici nelle configurazioni di app per le app nei dispositivi che non sono registrati. Per altre informazioni, vedere [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md) (Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Aggiornamenti all'app Portale aziendale per Windows 10 <!--1299474-->
La pagina Impostazioni dell'app Portale aziendale per Windows 10 è stata aggiornata in modo da rendere più coerenti le impostazioni e le azioni previste dall'utente sui vari tipi di impostazioni. Ne è stato aggiornato anche il layout per uniformarlo a quello delle altre app Windows. È possibile trovare le immagini "Prima/Dopo" nella pagina sulle [novità nell'interfaccia utente delle app](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Comunicare agli utenti finali quali informazioni possono essere visualizzate per i dispositivi Windows 10 <!--1337920-->
È stata aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo nell'app Portale aziendale per Windows 10. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente da questa pagina dalla documentazione di Intune per gli utenti finali. Potranno accedere a queste informazioni anche dalla schermata **Informazioni**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Richiesta di commenti e suggerimenti per l'app Portale aziendale per Android <!--1165249-->
L'app Portale aziendale per Android richiede ora commenti e suggerimenti da parte degli utenti finali. I commenti vengono inviati direttamente a Microsoft e offrono agli utenti finali la possibilità di valutare l'app nello store pubblico Google Play. L'invio di commenti e suggerimenti non è comunque obbligatorio e può essere facilmente ignorato per continuare a usare regolarmente l'app.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Consentire agli utenti di usare l'app del portale aziendale per Android <!-- 1573324, 1573150, 1558616, 1564878 -->

L'app Portale aziendale per Android include ora istruzioni per gli utenti finali per consentire di comprendere e, dove possibile, risolvere autonomamente nuovi casi d'uso.
- Gli utenti finali verranno indirizzati al [portale di Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) per rimuovere un dispositivo se è stato raggiunto il numero massimo di dispositivi che sono autorizzati ad aggiungere.
- Agli utenti finali verranno indicati i passaggi da eseguire per [correggere gli errori di attivazione sui dispositivi Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) o per [disattivare la modalità di risparmio energia](/intune-user-help/power-saving-mode-android). Se nessuna delle soluzioni proposte corregge il problema, verrà descritto come [inviare i log a Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nuova azione 'Risolvi' disponibile per i dispositivi Android <!-- 1583480 -->

L'app del portale aziendale per Android include ora una nuova azione 'Risolvi' nella pagina _Aggiorna impostazioni del dispositivo_. La selezione di questa opzione indirizza l'utente finale direttamente all'impostazione che rende il dispositivo non conforme. L'app del portale aziendale per Android supporta attualmente questa opzione per le impostazioni di [passcode del dispositivo](/intune-user-help/set-your-pin-or-password-android), [debug USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [origini sconosciute](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicatore dello stato di avanzamento della configurazione del dispositivo in Portale aziendale Android <!-- 1565657 -->
Quando un utente registra un dispositivo, nell'app Portale aziendale per Android viene visualizzato un indicatore dello stato di avanzamento del processo di configurazione del dispositivo. L'indicatore elenca i nuovi stati nell'ordine seguente: "Configurazione del dispositivo...", "Registrazione del dispositivo...", "Completamento della registrazione del dispositivo..." e "Completamento della configurazione del dispositivo...".

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Supporto dell'autenticazione basata sui certificati nel portale aziendale per iOS <!--1029830-->
È stato aggiunto il supporto dell'autenticazione basata sui certificati (CBA) nell'app del portale aziendale per iOS. Gli utenti con autenticazione basata sui certificati immettono il nome utente e quindi toccano il collegamento "Sign in with a certificate" (Accedi con un certificato). L'autenticazione basata sui certificati è già supportata nelle app del portale aziendale per Android e Windows. Altre informazioni sono disponibili nella pagina di [accesso all'app del portale aziendale](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Le app disponibili con o senza registrazione possono essere ora installate senza richiesta di registrazione. <!-- 1334712 -->

Le app aziendali rese disponibili con o senza registrazione nell'app Portale aziendale Android possono essere ora installate senza richiesta di registrazione.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Supporto del programma AutoPilot Deployment di Windows in Microsoft Intune  <!-- 747617  -->
Ora è possibile usare Microsoft Intune con il programma AutoPilot Deployment di Windows per consentire agli utenti di attivare e gestire i dispositivi aziendali senza interventi del personale IT. È possibile personalizzare la Configurazione guidata con informazioni che consentono agli utenti di aggiungere il dispositivo ad Azure AD e di registrarlo in Intune. Microsoft Intune e AutoPilot di Windows eseguiti insieme eliminano la necessità di distribuire, gestire e aggiornare le immagini del sistema operativo. Per informazioni dettagliate, vedere [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot) (Registrare dispositivi Windows con il programma AutoPilot Deployment).

### <a name="quick-start-for-device-enrollment-----1425655---"></a>Avvio rapido per la registrazione del dispositivo  <!-- 1425655 --> 
In **Registrazione del dispositivo** ora è disponibile una sezione di avvio rapido che include una tabella di riferimenti per la gestione delle piattaforme e la configurazione del processo di registrazione. L'esecuzione delle fasi iniziali della registrazione è facilitata mediante una breve descrizione di ciascun elemento e collegamenti ad argomenti di documentazione con procedure dettagliate.

### <a name="device-categorization----1427491---"></a>Categorizzazione dei dispositivi <!-- 1427491 -->
Il grafico della piattaforma dei dispositivi registrati nella scheda **Dispositivi > Panoramica** organizza i dispositivi per piattaforma e include Android, iOS, macOS, Windows e Windows Mobile.  I dispositivi che eseguono altri sistemi operativi vengono inclusi in "Altro".  Questa categoria include i dispositivi prodotti da Blackberry, NOKIA e altri produttori.  

Per informazioni sui dispositivi interessati nel tenant, scegliere **Gestisci > Tutti i dispositivi** e quindi usare **Filtra** per limitare il campo **Sistema operativo**.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuovo partner di Mobile Threat Defense  <!-- 954681 -->  
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi condotta da Zimperium, una soluzione Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Zimperium. È possibile configurare criteri di accesso condizionale EMS in base alla valutazione dei rischi di Zimperium abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10  <!--- 978575, 1308849, -->  
Sono state aggiunte nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 nella categoria Windows Defender SmartScreen.

Per informazioni dettagliate sul profilo di restrizione dei dispositivi Windows 10, vedere [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).

### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>Supporto remoto per dispositivi Windows e Windows Mobile   <!-- 1070473 -->  
Intune ora supporta l'uso del software [TeamViewer](https://www.teamviewer.com), acquistabile separatamente, per l'assistenza remota agli utenti con dispositivi Windows e Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analizzare dispositivi con Windows Defender <!-- 1280988  1280990   -->
Ora è possibile eseguire un'**analisi veloce**, un'**analisi completa** e l'**aggiornamento delle firme** con Windows Defender Antivirus nei dispositivi Windows 10 gestiti. Dal pannello della panoramica del dispositivo, scegliere l'azione da eseguire nel dispositivo. Verrà chiesto di confermare l'azione prima che il comando venga inviato al dispositivo. 

**Analisi veloce**: l'analisi veloce analizza i percorsi in cui il malware si registra per l'avvio, ad esempio le chiavi del Registro di sistema e le cartelle di avvio di Windows note. L'analisi veloce richiede in media cinque minuti. Unita all'impostazione della **protezione in tempo reale Always On** che analizza i file quando vengono aperti, chiusi e ogni volta che un utente passa a una cartella, l'analisi veloce consente di fornire protezione da software dannoso che potrebbe trovarsi nel sistema o nel kernel. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Analisi completa**: l'analisi completa può essere utile nei dispositivi in cui sono state riscontrate minacce malware per identificare se sono presenti componenti inattivi che richiedono una pulizia più approfondita ed è utile per l'esecuzione di analisi su richiesta. L'analisi completa può richiedere un'ora. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Aggiornare le firme**: il comando di aggiornamento delle firme aggiorna le definizioni e le firme malware di Windows Defender Antivirus, garantendo l'efficacia nel rilevamento di malware. Questa funzionalità è applicabile solo ai dispositivi Windows 10 con connettività Internet. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Il pulsante Abilita/Disabilita viene rimosso dalla pagina Autorità di certificazione nel portale di Intune di Azure  <!-- 1400455 -->
 È stato eliminato un passaggio aggiuntivo nella configurazione del Connettore di certificati di Intune. Attualmente è necessario scaricare il Connettore di certificati e quindi abilitarlo nella console di Intune. Se tuttavia si disattiva il connettore nella console di Intune, questo continua a emettere certificati.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
A partire da ottobre, il pulsante Abilita/Disabilita non viene più visualizzato nella pagina Autorità di certificazione del portale di Azure. La funzionalità del connettore resta invariata. I certificati vengono ancora distribuiti ai dispositivi registrati in Intune. È possibile continuare a scaricare e installare il Connettore di certificati. Per interrompere l'emissione di certificati ora è necessario disinstallare il Connettore di certificati anziché disattivarlo.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Se il Connettore di certificati è disattivato, è necessario disinstallarlo.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team   <!--- 1308838 -->
In questa versione vengono aggiunte molte nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team per la gestione dei dispositivi Surface Hub.

Per altre informazioni su questo profilo, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo <!-- 1333292 -->
È possibile usare [criteri personalizzati per dispositivi Android](custom-settings-android.md) per impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo.

A tale scopo, configurare criteri personalizzati di Android impostando l'URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange su **TRUE** e quindi assegnarli ai gruppi necessari.

### <a name="bitlocker-device-configuration----1397398---"></a>Configurazione di BitLocker per il dispositivo <!-- 1397398 -->
**Crittografia di Windows > Impostazioni di base** include la nuova impostazione **Avviso per la crittografia dischi di altro tipo** che consente di disabilitare il [prompt di avviso](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) per crittografie dischi di altro tipo eventualmente in uso nel dispositivo dell'utente.  Il prompt di avviso richiede il consenso dell'utente finale prima di configurare BitLocker nel dispositivo e blocca la configurazione di BitLocker fino alla conferma dell'utente finale.  La nuova impostazione disabilita l'avviso per l'utente finale.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Le app Volume Purchase Program per le aziende ora vengono sincronizzate con il tenant Intune <!-- 800882 -->  
Gli sviluppatori di terze parti possono distribuire privatamente le app ai membri del Volume Purchase Program di Apple per le aziende indicati in iTunes Connect. I membri VPP per le aziende possono accedere a Volume Purchase Program App Store e acquistare le app.

A partire dalla versione corrente le app VPP per le aziende acquistate dall'utente finale vengono sincronizzate con il rispettivo tenant Intune.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selezionare l'Apple Store del paese per la sincronizzazione delle app VPP <!-- 1332311 -->  
È possibile configurare lo Store del paese per il Volume Purchase Program (VPP) quando si carica il token VPP. Intune sincronizza le app VPP per tutte le impostazioni locali dello Store del paese VPP specificato.

> [!NOTE]  
> Attualmente Intune sincronizza solo le app VPP dello Store VPP del paese corrispondenti all'impostazione locale di Intune in cui è stato creato il tenant di Intune.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloccare la funzionalità di copia e incolla tra i profili di lavoro e i profili personali in Android for Work <!-- 1098994 -->
Con questa versione è possibile configurare il profilo di lavoro di Android for Work per bloccare l'operazione di copia e incolla tra le app di lavoro e le app personali. Questa nuova impostazione è disponibile nel profilo **Limitazioni del dispositivo** per la piattaforma **Android for Work** in **Impostazioni del profilo di lavoro**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creare app iOS limitate ad Apple App Store di aree specifiche<!-- 1281692 -->
Sarà possibile specificare le impostazioni locali del paese durante la creazione di un'app gestita da Apple App Store.

> [!Note]  
> Attualmente è possibile creare solo app gestite di Apple App Store disponibili nello Store degli Stati Uniti.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Aggiornare le app VPP iOS concesse in licenza a utenti e dispositivi <!-- 1305564 -->  
Sarà possibile configurare il token VPP iOS per aggiornare tutte le app acquistate per tale token tramite il servizio Intune. Intune rileverà gli aggiornamenti delle app VPP nell'App Store e li invierà automaticamente al dispositivo quando questo si connette.

Per la descrizione dettagliata dell'impostazione di un token VPP e dell'attivazione degli aggiornamenti automatici, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune] (/intune/vpp-app-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Raccolta di entità di associazione dei dispositivi degli utenti aggiunta al modello di dati di Data Warehouse di Intune<!-- 1187917 -->
Ora è possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi. Il modello di dati è accessibile tramite il file di Power BI (PBIX) recuperato dalla pagina Data warehouse di Intune, tramite l'endpoint OData oppure sviluppando un client personalizzato.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Esaminare la conformità ai criteri per gli anelli di aggiornamento di Windows 10 <!-- 1067886 -->
È possibile esaminare un report sui criteri per gli anelli di aggiornamento di Windows 10 in Aggiornamenti software > Stato di distribuzione per ogni anello di aggiornamento. Il report sui criteri include lo stato di distribuzione degli anelli di aggiornamento configurati. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuovo report che elenca i dispositivi iOS con versioni precedenti di iOS <!-- 1352223 -->
Il report **Dispositivi iOS non aggiornati** è disponibile nell'area di lavoro **Aggiornamenti software**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento di iOS e con aggiornamenti disponibili. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visualizzare le assegnazioni dei criteri di protezione delle app per la risoluzione dei problemi <!--  1475003 -->
In questa versione futura verrà aggiunta un'opzione per i **criteri di protezione delle app** all'elenco a discesa **Assegnazioni** disponibile nel pannello della risoluzione dei problemi. Sarà ora possibile selezionare Criteri di protezione delle app per visualizzare i criteri assegnati agli utenti selezionati.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Miglioramenti del flusso di lavoro di installazione dei dispositivi nel Portale aziendale <!--1490692-->
È stato migliorato il flusso di lavoro di installazione dei dispositivi nell'app Portale aziendale per Android. Il linguaggio è più semplice e specifico per l'azienda e sono state inserite schermate dove possibile. È possibile visualizzare i miglioramenti nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Miglioramento delle linee guida per la richiesta di accesso ai contatti nei dispositivi Android <!--1484985-->

L'app Portale aziendale per Android richiede spesso all'utente finale di accettare l'autorizzazione per i contatti. Se un utente finale rifiuta l'accesso, ora viene visualizzata una notifica in-app che avvisa dell'autorizzazione per l'accesso condizionale. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Correzione dell'avvio sicuro per Android <!--1490712-->

Gli utenti finali con dispositivi Android potranno selezionare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notifiche push aggiuntive per gli utenti finali dell'app Portale aziendale per Android Oreo <!--1475932-->

Gli utenti visualizzeranno notifiche aggiuntive che indicano quando l'app Portale aziendale per Android Oreo sta eseguendo attività in background, ad esempio il recupero di criteri dal servizio Intune. Questa funzionalità aumenta la trasparenza per gli utenti finali, che sapranno quando sono in corso attività amministrative del Portale aziendale nei loro dispositivi, È uno degli aspetti dell'intera [ottimizzazione dell'interfaccia utente del portale aziendale](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) per l'app Portale aziendale per Android Oreo. 

Sono disponibili altre ottimizzazioni per i nuovi elementi dell'interfaccia utente che sono abilitate in Android Oreo.  Gli utenti finali visualizzeranno notifiche aggiuntive che indicheranno loro quando l'app Portale aziendale sta eseguendo attività in background, ad esempio il recupero di criteri dal servizio di Intune.  In questo modo per gli utenti finali sarà più chiaro quando l'app Portale aziendale sta eseguendo attività amministrative nel dispositivo.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuovi comportamenti dell'app del portale aziendale per Android con i profili di lavoro <!-- 1485783 -->

Quando si registra un dispositivo Android for Work con un profilo di lavoro, è l'app del portale aziendale nel profilo di lavoro a eseguire attività di gestione nel dispositivo. 

A meno che non si usi un'app abilitata per MAM nel profilo personale, l'app del portale aziendale per Android non è più utile. Per migliorare l'esperienza con i profili di lavoro, Intune nasconderà automaticamente l'app del portale aziendale personale dopo la registrazione del profilo di lavoro.

L'app del portale aziendale per Android può essere abilitata in qualsiasi momento nel profilo personale passando al [portale aziendale in Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e selezionando **Abilita**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Passaggio del portale aziendale per Windows 8.1 e Windows Phone 8.1 alla modalità di mantenimento <!--1428681-->

A partire da ottobre 2017, le app del portale aziendale per Windows 8.1 e Windows Phone 8.1 passeranno alla modalità di mantenimento. Le app e gli scenari esistenti, ad esempio la registrazione e la conformità, continueranno a essere supportati per queste piattaforme. Queste app rimarranno disponibili per il download tramite i canali di rilascio esistenti, ad esempio Microsoft Store. 

Nella modalità di mantenimento, queste app ricevono solo aggiornamenti della sicurezza critici. Non verranno rilasciati altri aggiornamenti o funzionalità per queste app. Per le nuove funzionalità è consigliabile aggiornare i dispositivi a Windows 10 o Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>Bloccare la registrazione di dispositivi Samsung Knox non supportata <!-- 1490695 -->

L'app Portale aziendale tenta di registrare solo i dispositivi Samsung Knox supportati. Per evitare errori di attivazione Knox che impediscono la registrazione MDM, la registrazione del dispositivo viene eseguita solo se il dispositivo viene visualizzato nell'[elenco di dispositivi pubblicato da Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). I dispositivi Samsung possono avere numeri di modello che supportano Knox oppure no. Verificare la compatibilità Knox con il rivenditore del dispositivo prima dell'acquisto e della distribuzione. È possibile trovare l'elenco completo dei dispositivi verificati nelle [impostazioni dei criteri Android e Samsung Knox Standard](/intune/supported-devices-browsers.md#intune-supported-devices).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Fine del supporto per Android 4.3 e versioni precedenti <!-- 1171126, 1326920 -->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate nei dispositivi registrati <!--1165314-->
Verrà aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo in tutte le app Portale aziendale. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente dall'articolo [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Questa opzione verrà presto implementata in tutte le app Portale aziendale. Per iOS, l'annuncio è stato fatto a [settembre](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).

## <a name="september-2017"></a>Settembre 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune supporta iOS 11 <!--1428975-->
Intune supporta iOS 11. Annuncio precedentemente fatto nel [blog del supporto tecnico di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fine del supporto per iOS 8.0 <!-- 1164477 -->
Le app gestite e l'app Portale aziendale per iOS richiederanno iOS 9.0 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati entro settembre non potranno accedere al Portale aziendale o a tali app. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Azione di aggiornamento aggiunta all'app del portale aziendale per Windows 10 <!--1132468-->
L'app Portale aziendale per Windows 10 consente agli utenti di aggiornare i dati nell'app trascinando verso il basso per aggiornare o, nei desktop, premendo F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate per iOS<!--739894-->

È stata aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo nell'app Portale aziendale per iOS. In questo modo gli utenti potranno ottenere maggiori informazioni sulla privacy direttamente da questa pagina dai documenti per gli utenti finali di Intune. Potranno accedere a queste informazioni anche nella schermata Informazioni su.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Consentire agli utenti di accedere all'app Portale aziendale per Android senza registrazione <!---1169910--->

Gli utenti finali potranno presto non avere l'obbligo di registrare il dispositivo per accedere all'app Portale aziendale per Android. Agli utenti finali di organizzazioni che usano criteri di protezione delle app non verrà più richiesto di registrare il dispositivo quando aprono l'app Portale aziendale. Gli utenti finali potranno anche installare app dal Portale aziendale senza registrare il dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Testo più comprensibile per l'app Portale aziendale per Android <!---1396349--->  

Il processo di registrazione per l'app del portale aziendale per Android è ora più semplice per gli utenti finali, grazie all'uso di un nuovo testo più comprensibile. Se si usa una documentazione personalizzata per la registrazione, è consigliabile aggiornarla sulla base delle nuove schermate. È possibile trovare immagini di esempio nella pagina [Aggiornamenti dell'interfaccia utente per le app degli utenti finali in Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>App del portale aziendale di Windows 10 aggiunta ai criteri per il consenso di Windows Information Protection<!-- 677129 -->

L'app Portale aziendale di Windows 10 è stata aggiornata per supportare Windows Information Protection (WIP). L'app può essere aggiunta ai criteri Consenti di WIP. Con questa modifica non è più necessario aggiungere l'app all'elenco **Esente**.


## <a name="august-2017"></a>Agosto 2017

### <a name="improvements-to-device-overview----1404453---"></a>Miglioramenti alla panoramica del dispositivo <!-- 1404453 -->  
In seguito ai miglioramenti, la panoramica del dispositivo ora visualizza i dispositivi registrati ma esclude i dispositivi gestiti da Exchange ActiveSync. I dispositivi Exchange ActiveSync non hanno le stesse opzioni di gestione dei dispositivi registrati. Per visualizzare il numero di dispositivi registrati e il numero di dispositivi registrati per piattaforma in Intune nel portale di Azure, scegliere **Dispositivi** > **Panoramica**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Miglioramenti dell'inventario dei dispositivi gestito da Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
In questa versione sono stati apportati i miglioramenti seguenti alle informazioni di inventario raccolte dai dispositivi gestiti dall'utente:
 
-   Per i dispositivi Android ora è possibile aggiungere all'inventario dei dispositivi una colonna che mostra il livello di patch più recente per ogni dispositivo. Aggiungere la colonna **Security patch level** (Livello patch di protezione) all'elenco di dispositivi per visualizzare il risultato.
-   Quando si applica un filtro alla visualizzazione dei dispositivi ora è possibile filtrare i dispositivi per data di registrazione. Ad esempio, è possibile visualizzare solo i dispositivi registrati dopo una data specificata.
-   Sono stati apportati miglioramenti al filtro usato per l'elemento **Last Check-in Date** (Data ultima archiviazione).
-   Nell'elenco dei dispositivi ora è possibile visualizzare il numero di telefono dei dispositivi di proprietà dell'azienda.
È inoltre possibile usare il riquadro del filtro per cercare i dispositivi in base al numero di telefono.
 
Per altri dettagli sull'inventario dei dispositivi, vedere [Come visualizzare l'inventario dei dispositivi di Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Supporto dell'accesso condizionale per dispositivi macOS 
<!-- 720172 -->
Ora è possibile impostare un criterio di accesso condizionale che richiede che i dispositivi Mac vengano registrati in Intune e siano conformi ai relativi criteri di conformità dei dispositivi. Ad esempio, gli utenti possono scaricare l'app Portale aziendale Intune per macOS e registrare i propri dispositivi Mac in Intune. Intune valuta se il dispositivo Mac è conforme a requisiti come PIN, crittografia, versione del sistema operativo e integrità del sistema.

- Altre informazioni sul [supporto dell'accesso condizionale per dispositivi macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>L'app Portale aziendale per macOS è disponibile in anteprima pubblica <!---1484796--->
L'app Portale aziendale per macOS è ora disponibile come parte dell'anteprima pubblica dell'accesso condizionale in Enterprise Mobility + Security. Questa versione supporta macOS 10.11 e versioni successive. È possibile ottenerla all'indirizzo [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nuove impostazioni per le restrizioni dei dispositivi per Windows 10    
<!--1063965, 1308850  -->
In questa versione sono state aggiunte nuove impostazioni per il [profilo di restrizione dei dispositivi Windows 10](/intune/device-restrictions-windows-10) nelle categorie seguenti:

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Aggiornamenti delle impostazioni del profilo dispositivo Endpoint Protection di Windows 10 per BitLocker
<!--1459533 -->    
In questa versione sono stati apportati i miglioramenti seguenti al funzionamento delle impostazioni BitLocker in un profilo di dispositivo Endpoint Protection di Windows 10:
 
In **Impostazioni dell'unità del sistema operativo BitLocker** per l'impostazione **BitLocker con chip TPM non compatibile**, quando in precedenza si selezionava **Blocca** in realtà BitLocker veniva autorizzato. Questo problema è stato risolto e ora quando si seleziona questa opzione BitLocker viene bloccato.
In **Impostazioni dell'unità del sistema operativo BitLocker**, per l'impostazione **Agente di recupero dati basato su certificati** ora è possibile bloccare in modo esplicito l'agente di recupero dati basato su certificati. Per impostazione predefinita l'agente è consentito.
In **Impostazioni delle unità dati fisse BitLocker**, per l'impostazione **Agente di recupero dati** ora è possibile bloccare in modo esplicito l'agente di recupero dati.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nuova esperienza di accesso per gli utenti dell'app Portale aziendale per Android e gli utenti dei criteri di protezione delle app <!-- 621669 -->
Gli utenti finali possono ora visualizzare le app, gestire i dispositivi e accedere a informazioni sui contatti IT tramite l'app Portale aziendale Android senza registrare i dispositivi Android personali. Inoltre, se un utente finale usa già un'app protetta tramite i criteri di protezione app di Intune e avvia l'app Portale aziendale per Android, l'utente finale non riceve più la richiesta di registrare il dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nuova impostazione nell'app Portale aziendale per Android per attivare/disattivare l'ottimizzazione della memoria <!--1405990-->
La pagina **Impostazioni** nell'app Portale aziendale per Android include una nuova impostazione che consente agli utenti di disattivare facilmente l'ottimizzazione della batteria per le app Portale aziendale e Microsoft Authenticator. Il nome dell'app visualizzato nell'impostazione varia a seconda dell'app usata per gestire l'account aziendale. È consigliabile che gli utenti disattivino l'ottimizzazione della batteria per migliorare le prestazioni delle app aziendali che sincronizzano posta elettronica e dati. 

### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Supporto di più identità in OneNote per iOS      <!-- 1234281 -->
Ora gli utenti finali possono usare account diversi (aziendali e personali) con Microsoft OneNote per iOS. I criteri di protezione app possono essere applicati ai dati aziendali nei notebook di lavoro senza influire sul notebook personale dell'utente. Ad esempio un criterio può consentire a un utente di trovare informazioni nei notebook aziendali, ma impedirà all'utente di copiare e incollare dati aziendali dal notebook aziendale a un notebook personale.
 
- Altre informazioni sulle app che supportano la [protezione delle app e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nuove impostazioni per consentire e bloccare app nei dispositivi Samsung Knox Standard
<!-- 1305423 822899-->  
In questa versione vengono aggiunte nuove [impostazioni di restrizione dei dispositivi](device-restrictions-android.md) che consentono di specificare gli elenchi di app seguenti:
 
- App che gli utenti sono autorizzati a installare
- App che gli utenti non possono eseguire
- App che sono nascoste all'utente nel dispositivo
 
È possibile specificare l'app in base all'URL, al nome del pacchetto o dall'elenco di app che si gestiscono.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nuovo collegamento da Intune all'interfaccia utente per i criteri di accesso condizionale basati su app di Azure AD
<!-- 1016201 -->
Ora gli amministratori IT possono impostare criteri condizionali basati su app tramite la nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Azure AD. Per ora l'accesso condizionale basato su app disponibile nella sezione Protezione app di Intune del portale Azure resta in tale posizione e viene applicato in affiancamento. Per comodità è anche disponibile un collegamento alla nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Intune.

- Altre informazioni sull'[accesso condizionale basato su app in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Luglio 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restrizione della registrazione dei dispositivi Android e iOS in base alla versione del sistema operativo <!--- 1333256,  1245463 --->
Intune ora supporta la restrizione della registrazione di Android e iOS in base al numero di versione del sistema operativo. In **Restrizione dei tipi di dispositivo** l'amministratore IT può ora impostare una configurazione della piattaforma per limitare la registrazione tra un valore minimo e massimo del sistema operativo. Le versioni del sistema operativo Android devono essere specificate come Principale.Secondaria.Build.Rev, dove Secondaria, Build e Rev sono facoltativi. Le versioni di iOS devono essere specificate come Principale.Secondaria.Build, dove Build è facoltativa. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

>[!NOTE]
>Non limitare la registrazione tramite i programmi DEP Apple o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Limitare la registrazione dei dispositivi personali Android, iOS e macOS <!--- 1333272,  1333275, 1245709 --->
Intune può limitare la registrazione dei dispositivi personali creando un elenco dei dispositivi aziendali consentiti con i relativi numeri IMEI. Intune ha ora esteso questa funzionalità a iOS, Android e macOS usando i numeri di serie del dispositivo. Caricando i numeri di serie in Intune, è possibile predichiarare i dispositivi come proprietà dell'azienda. Tramite le restrizioni della registrazione, è possibile bloccare i dispositivi personali (BYOD, Bring Your Own Device), consentendo così la registrazione solo per i dispositivi di proprietà dell'azienda. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

Per importare i numeri di serie, passare a **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**, fare clic su **Aggiungi** e quindi caricare un file con estensione csv senza intestazione ma con due colonne per il numero di serie e i dettagli come i numeri IMEI.  Per limitare i dispositivi personali, accedere a **Registrazione del dispositivo** > **Restrizioni registrazione**. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinita** e **Configurazioni della piattaforma**. È possibile scegliere **Consenti** o **Blocca** per i dispositivi personali per iOS, Android e macOS. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nuova azione del dispositivo per forzare la sincronizzazione con Intune <!-- 711369 -->
In questa versione è stata aggiunta una nuova azione del dispositivo che forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.
Per informazioni dettagliate, vedere [Sincronizzare il dispositivo](device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzare i dispositivi iOS supervisionati per installare automaticamente l'aggiornamento software più recente disponibile <!-- 777100 -->
È disponibile un nuovo criterio dall'area di lavoro degli aggiornamenti software, che consente di forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione. Per informazioni dettagliate, vedere [Configurare i criteri di aggiornamento per iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile: nuovo partner di Mobile Threat Defense  <!-- 954651, 1172027 -->
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Checkpoint SandBlast Mobile, una soluzione di Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Checkpoint SandBlast Mobile. È possibile configurare criteri di accesso condizionale EMS basati sulla valutazione dei rischi di Checkpoint SandBlast Mobile e abilitati tramite i criteri di conformità dei dispositivi di Intune. È possibile consentire o bloccare l'accesso alle risorse aziendali ai dispositivi non conformi in base alle minacce rilevate.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Distribuire un'app come disponibile in Microsoft Store per le aziende <!-- 748101 -->
Con questa versione, gli amministratori possono ora assegnare Microsoft Store per le aziende come disponibile. Con questa impostazione, gli utenti finali possono installare l'app dall'app Portale aziendale o dal sito Web del portale aziendale senza essere reindirizzati a Microsoft Store.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Aggiornamenti dell'interfaccia utente del sito Web del portale aziendale <!--1313244 part 1-->
Sono stati introdotti vari aggiornamento all'interfaccia utente del [sito Web portale aziendale](https://portal.manage.microsoft.com) per migliorare l'esperienza per gli utenti finali.

- __Miglioramenti per i riquadri delle app__: le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente in base al colore dominante dell'icona, se rilevabile. Se applicabile, questo sfondo sostituisce il bordo grigio precedentemente visibile nei riquadri delle app.

    In una versione futura è previsto che il sito Web del portale aziendale visualizzi le icone grandi ogniqualvolta possibile. È consigliabile che gli amministratori IT pubblichino app con icone ad alta risoluzione di dimensioni minime pari a 120x120 pixel. 

- __Modifiche alla struttura di spostamento__: gli elementi della barra di spostamento sono stati spostati nel menu hamburger in alto a sinistra. La pagina delle categorie è stata rimossa. Gli utenti possono ora filtrare il contenuto in base alla categoria durante l'esplorazione.

- __Aggiornamenti per le app in primo piano__: è stata aggiunta una pagina dedicata nel sito, nella quale gli utenti possono visualizzare le app che hanno scelto di mettere in primo piano e sono state apportate alcune modifiche all'interfaccia utente della sezione In primo piano nella home page.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Supporto di iBooks per il sito Web del portale aziendale <!--1231841-->
È stata aggiunta una pagina dedicata al sito Web del portale aziendale che consente agli utenti di visualizzare e scaricare iBooks. 


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Dettagli aggiuntivi per la risoluzione dei problemi dell'help desk <!---  Applies to 1263399, 1326964, 1341642 --->
Intune ha aggiornato la visualizzazione della risoluzione dei problemi e aggiunto le informazioni che fornisce agli amministratori e al personale dell'help desk. È ora disponibile una tabella **Assegnazioni** che fornisce un riepilogo di tutte le assegnazioni dell'utente in base all'appartenenza a gruppi. L'elenco include:
- App per dispositivi mobili
- Criteri di conformità
- Profili di configurazione
 
Inoltre, la tabella **Dispositivi** ora include le colonne **Tipo di join per Azure AD** e **Conforme con Azure AD**. Per altre informazioni, vedere [Aiutare gli utenti nella risoluzione dei problemi](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Data warehouse di Intune (anteprima pubblica)
Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologica dell'ambiente. È possibile accedere ai dati tramite un file di Power BI (PBIX), un collegamento OData compatibile con molti strumenti di analisi oppure interagendo con l'API REST. Per altre informazioni, vedere [Usare il data warehouse di Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modalità chiara e modalità scura disponibili per l'app Portale aziendale per Windows 10 <!---676547--->
Gli utenti finali potranno personalizzare la modalità di colore per l'app Portale aziendale per Windows 10. L'utente potrà apportare la modifica nella sezione delle impostazioni dell'app Portale aziendale. La modifica verrà visualizzata dopo che l'utente avrà riavviato l'app. Per Windows 10 versione 1607 e successive, la modalità dell'app predefinita sarà l'impostazione di sistema. Per Windows 10 versione 1511 e precedenti, la modalità dell'app predefinita sarà la modalità chiara.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Consentire agli utenti finali di contrassegnare il gruppo di dispositivi nell'app Portale aziendale per Windows 10 <!---807046-->
Gli utenti finali possono ora selezionare il gruppo a cui appartiene il dispositivo contrassegnandolo direttamente dall'app Portale aziendale per Windows 10.



## <a name="june-2017"></a>Giugno 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nuovo accesso di amministrazione basato su ruoli per gli amministratori di Intune  <!-- 1099990 -->  
È stato aggiunto un nuovo ruolo di amministrazione dell'accesso condizionale per visualizzare, creare, modificare ed eliminare i criteri di accesso condizionale di Azure AD. In precedenza, solo gli amministratori globali e gli amministratori della sicurezza disponevano di questa autorizzazione. È possibile concedere l'autorizzazione di questo ruolo agli amministratori di Intune, in modo che possano accedere ai criteri di accesso condizionale.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Contrassegno dei dispositivi di proprietà dell'azienda con i numeri di serie <!-- 1215070 -->  
Intune supporta ora il caricamento di numeri di serie iOS, macOS e Android come identificatori dei dispositivi aziendali. Attualmente non è possibile usare i numeri di serie per bloccare la registrazione dei dispositivi personali, perché i numeri di serie non vengono verificati durante la registrazione. La funzionalità di blocco dei dispositivi personali in base al numero di serie sarà disponibile a breve.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nuove azioni remote per i dispositivi iOS <!-- 854689 -->
In questa versione sono state aggiunte due nuove azioni remote dei dispositivi per i dispositivi iPad condivisi che gestiscono l'app Classroom Apple:

-   [Disconnetti l'utente corrente](device-logout-user.md): disconnette l'utente corrente di un dispositivo iOS selezionato.
-   [Rimuovi utente](device-remove-user.md): elimina un utente selezionato dalla cache locale di un dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Supporto per gli iPad condivisi con l'app Classroom iOS <!-- 1044681 -->
In questa versione è stato esteso il supporto per la gestione dell'app Classroom per iOS per includere gli studenti che accedono agli iPad condivisi usando il proprio ID Apple gestito.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Modifiche alle app Intune predefinite <!-- 1332306 -->
Intune conteneva in precedenza un numero di app predefinite che era possibile assegnare rapidamente. In base ai commenti e suggerimenti ricevuti, abbiamo rimosso l'elenco e le app predefinite non verranno più visualizzate.
Tuttavia, se sono già state assegnate app predefinite, le app assegnate saranno ancora visibili nell'elenco delle app. È possibile continuare ad assegnare queste app in base alle proprie esigenze.
In una versione successiva si prevede di aggiungere un metodo più semplice per la selezione e l'assegnazione delle app predefinite dal portale di Azure.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Installazione più semplice delle app di Office 365 <!--- 1121362 --->
Un nuovo tipo di applicazioni **Office 365 ProPlus** semplifica l'assegnazione delle app Office 365 ProPlus 2016 ai dispositivi gestiti che eseguono la versione più recente di Windows 10. È anche possibile installare Microsoft Project e Microsoft Visio, se si hanno le relative licenze. Le app desiderate vengono unite in bundle e visualizzate come un'unica app nell'elenco di app della console di Intune.
Per altre informazioni, vedere [How to add Office 365 apps for Windows 10](apps-add-office365.md) (Come aggiungere app di Office 365 per Windows 10).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Supporto per le app offline da Microsoft Store per le aziende <!--- 777044 --->
Le app offline acquistate da Microsoft Store per le aziende verranno ora sincronizzate nel portale di Azure. È possibile quindi distribuire tali app a gruppi di dispositivi o di utenti. Le app offline vengono installate da Intune, non dallo Store.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>L'app Microsoft Teams è ora inclusa nell'elenco CA basato su app delle app approvate   <!-- 1257019 -->
L'app Microsoft Teams per iOS e Android fa ora parte delle app approvate per i criteri di accesso condizionale basati su app per Exchange e SharePoint Online. L'app può essere configurata tramite il pannello Protezione app di Intune nel portale di Azure di tutti i tenant che usano attualmente l'accesso condizionale basato su app.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integrazione di Managed Browser e del proxy di applicazione <!-- 1287310 -->
Intune Managed Browser può essere ora integrato con il servizio proxy di applicazione di Azure AD per consentire agli utenti di accedere ai siti Web interni, anche quando lavorano in remoto. Gli utenti del browser immettono l'URL nel modo consueto e Managed Browser instrada la richiesta attraverso il gateway Web del proxy di applicazione. Per altre informazioni, vedere [Manage Internet access using Managed browser policies](app-configuration-managed-browser.md) (Gestire l'accesso a Internet usando i criteri di Managed Browser).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nuove impostazioni di configurazione dell'app per Intune Managed Browser<!-- 682951 -->
In questa versione sono state aggiunte altre configurazioni per l'app Intune Managed Browser per iOS e Android. È possibile ora usare i criteri di configurazione delle app per configurare la home page predefinita e i segnalibri del browser.
Per altre informazioni, vedere [Manage Internet access using managed browser policies](app-configuration-managed-browser.md) (Gestire l'accesso a Internet usando i criteri di Managed Browser).

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Impostazioni BitLocker per Windows 10  <!-- 951707 -->
È ora possibile configurare le impostazioni BitLocker per i dispositivi Windows 10 con un nuovo profilo di dispositivo di Intune. Ad esempio, è possibile richiedere che i dispositivi vengano crittografati e anche configurare altre impostazioni che vengono applicate quando BitLocker è attivato.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
In questa versione sono stati aggiunte nuove impostazioni per il profilo di restrizione del dispositivo Windows 10, nelle categorie seguenti:

-  Windows Defender
-  Rete cellulare e connettività
-  Esperienza della schermata bloccata
-  Privacy
-  Cerca
-  Contenuti in evidenza di Windows
-  Microsoft Edge

Per altre informazioni sulle impostazioni di Windows 10, vedere [Windows 10 and later device restriction settings](device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>L'app Portale aziendale per Android ora include una nuova esperienza utente finale per i criteri di protezione delle app <!--1305217-->
In base ai suggerimenti dei clienti, l'app Portale aziendale per Android è stata modificata e ora include un pulsante **Accesso al contenuto aziendale**. Lo scopo è impedire che gli utenti finali eseguano inutilmente il processo di registrazione quando hanno solo necessità di accedere alle app che supportano i criteri di protezione delle app, una funzionalità di gestione delle applicazioni mobili di Intune. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nuova azione di menu per rimuovere facilmente Portale aziendale <!--1164569-->
In risposta al feedback degli utenti, per l'app Portale aziendale per Android è stata aggiunta una nuova azione di menu per eseguire la rimozione di Portale aziendale dal dispositivo. Questa azione rimuove il dispositivo dalla gestione di Intune in modo che l'utente possa rimuovere l'app dal dispositivo. È possibile visualizzare queste modifiche nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md) e nella [documentazione per gli utenti finali di Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Miglioramenti alla sincronizzazione di app con Windows 10 Creators Update <!--676505-->
L'app Portale aziendale per Windows 10 avvierà ora automaticamente una sincronizzazione per le richieste di installazione di app per dispositivi con Windows 10 Creators Update (1703). Ciò consente di limitare il problema di installazione di app quando lo stato è "In attesa di sincronizzazione". Inoltre, gli utenti saranno in grado di avviare manualmente la sincronizzazione all'interno dell'app. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nuova esperienza guidata per il portale aziendale di Windows 10 <!---1058938--->
L'app Portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate che guidano l'utente nella procedura di registrazione in Azure Active Directory (obbligatoria per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale. Gli utenti possono continuare a usare l'app se non completano la registrazione, ma le funzionalità saranno limitate.

Questo aggiornamento è visibile solo nei dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 (build 1607) o versioni successive. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Disponibilità generale delle console di amministrazione di Microsoft Intune e dell'accesso condizionale
Questo è l'annuncio della disponibilità generale sia della nuova console di amministrazione di Intune nel portale di Azure che della nuova console di amministrazione dell'accesso condizionale. Con Intune nel portale di Azure è ora possibile gestire tutte le funzionalità MAM e MDM di Intune con un'esperienza di amministrazione consolidata, sfruttando allo stesso tempo le funzioni di raggruppamento e targeting di Azure AD. L'accesso condizionale in Azure offre funzionalità avanzate per Azure AD e Intune in un'unica console unificata. Per quanto riguarda l'esperienza di amministrazione, inoltre, il passaggio alla piattaforma Azure consente di usare browser moderni.

Intune è ora visibile senza l'etichetta di **anteprima** nel portale di Azure all'indirizzo portal.azure.com.

Al momento non è richiesto alcun intervento da parte dei clienti esistenti, a meno che non si riceva uno di una serie di messaggi nel centro messaggi che richiede di intervenire in modo da consentire a Microsoft di eseguire la migrazione dei gruppi. È anche possibile che si riceva una notifica nel centro messaggi che informa che la migrazione richiede più tempo a causa di errori di Microsoft. Stiamo continuando a lavorare con impegno per completare la migrazione di tutti i clienti interessati.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Miglioramenti dei riquadri dell'app Portale aziendale per iOS
È stata aggiornata la progettazione dei riquadri dell'app nella home page in modo che rispecchino il colore personalizzato impostato per Portale aziendale. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Selezione account ora disponibile per l'app Portale aziendale per iOS
Gli utenti di dispositivi iOS potrebbero ora visualizzare la nuova selezione account quando accedono al Portale aziendale se usano l'account aziendale o dell'istituto di istruzione per accedere ad altre app Microsoft. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

## <a name="may-2017"></a>Maggio 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Modifica dell'autorità MDM senza annullare la registrazione dei dispositivi gestiti <!--1103950-->
È ora possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Nella console di Configuration Manager è possibile [modificare l'autorità MDM](/sccm/mdm/deploy-use/change-mdm-authority) da Imposta su Configuration Manager (ibrida) a Microsoft Intune (autonoma) o viceversa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notifica migliorata per i PIN di avvio Samsung Knox <!--1087143-->
Quando gli utenti finali devono impostare un PIN di avvio su dispositivi Samsung Knox per garantire la conformità alla crittografia, toccando la notifica visualizzata, gli utenti finali verranno indirizzati alla posizione esatta nell'app Impostazioni.  In precedenza, la notifica rimandava gli utenti finali alla schermata di modifica della password.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Supporto di Apple School Manager (ASM) con iPad condiviso <!-- 748864, 770395-->

Intune supporta ora l'uso di Apple School Manager (ASM) al posto di Apple Device Enrollment Program per fornire funzionalità di registrazione pronte all'uso per i dispositivi iOS. L'onboarding di ASM è necessario usare l'app Classroom per iPad condivisi e per consentire la sincronizzazione dei dati da ASM ad Azure Active Directory tramite Microsoft School Data Sync (SDS). Per altre informazioni, vedere [Abilitare la registrazione di dispositivi iOS con Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> La configurazione di iPad condivisi per l'uso dell'app Classroom richiede configurazioni di iOS Education in Azure non ancora disponibili.  Questa funzionalità verrà aggiunta presto.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Fornire assistenza remota ai dispositivi Android con TeamViewer <!-- 675418 -->

Intune può ora usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per consentire agli amministratori di offrire assistenza remota agli utenti che eseguono dispositivi Android. Per altre informazioni, vedere [Fornire assistenza remota per i dispositivi Android gestiti da Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Gestione delle app

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nuove condizioni dei criteri di protezione delle app per MAM <!-- 679864 -->

È ora possibile impostare un requisito per MAM senza registrare gli utenti, che consente di applicare i criteri seguenti:

- Versione minima dell'applicazione
- Versione minima del sistema operativo
- Versione minima di Intune App SDK per l'applicazione di destinazione (solo iOS)

Questa funzionalità è disponibile sia per Android che per iOS. Intune supporta l'imposizione della versione minima per le versioni delle piattaforme del sistema operativo, per le versioni delle applicazioni e per Intune App SDK. In iOS applicazioni con SDK integrato possono anche imporre la versione minima a livello di SDK. L'utente non potrà accedere all'applicazione di destinazione se i requisiti minimi definiti tramite i criteri di protezione delle app non vengono soddisfatti ai tre diversi livelli definiti in precedenza. A questo punto, l'utente può rimuovere l'account (per le applicazioni con identità multiple), chiudere l'applicazione o aggiornare la versione del sistema operativo o dell'applicazione.

È anche possibile configurare impostazioni aggiuntive per fornire una notifica che non causa blocchi per consigliare un aggiornamento del sistema operativo o dell'applicazione. Questa notifica può essere chiusa e l'applicazione può essere usata normalmente.

Per altre informazioni, vedere [Impostazioni dei criteri di protezione delle app per iOS](app-protection-policy-settings-ios.md) e [Impostazioni dei criteri di protezione delle app per Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configurare le configurazioni delle app per Android for Work <!-- 621621 -->
Alcune app Android dallo store supportano opzioni di configurazione gestite che consentono a un amministratore IT di controllare l'esecuzione di un'app nel profilo di lavoro. Con Intune è ora possibile visualizzare le configurazioni supportate da un'app e definirle dal portale di Azure con una finestra di progettazione della configurazione o un editor JSON. Per altre informazioni, vedere [Usare configurazioni di app per Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nuove funzionalità di configurazione delle app per MAM senza registrazione <!-- 677969 -->
È ora possibile creare criteri di configurazione delle app tramite MAM senza canale di registrazione. Questa funzionalità equivale ai criteri di configurazione delle app disponibili per la configurazione delle app di gestione di dispositivi mobili (MDM). Per un esempio di configurazione di app con MAM senza registrazione, vedere [Gestire l'accesso a Internet usando criteri di Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configurare elenchi di URL consentiti e bloccati per Managed Browser <!-- 682960 -->
È ora possibile configurare un elenco di domini e URL consentiti o bloccati per Managed Browser con le impostazioni di configurazione delle app nel portale di Azure. Queste impostazioni possono essere configurate indipendentemente dal fatto che questa soluzione venga usata in un dispositivo gestito o non gestito. Per altre informazioni, vedere [Gestire l'accesso a Internet usando i criteri di Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Visualizzazione per il supporto tecnico dei criteri di protezione delle app <!-- 1069473 -->
Gli utenti del supporto tecnico IT possono ora controllare lo stato delle licenze utente e lo stato delle app con criteri di protezione delle app assegnati agli utenti nel pannello Risoluzione dei problemi. Per informazioni dettagliate, vedere [Risoluzione dei problemi](./help-desk-operators.md).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Controllare le visite ai siti Web nei dispositivi iOS<!-- 723832 -->
È ora possibile controllare i siti Web che gli utenti di dispositivi iOS possono visitare tramite uno dei due metodi seguenti:

- Aggiungere URL consentiti e bloccati tramite il filtro predefinito dei contenuti Web di Apple.

- Consentire l'accesso dal browser Safari solo ai siti Web specificati. Per ogni sito specificato viene creato il segnalibro corrispondente in Safari.

Per altre informazioni, vedere [Impostazioni di filtraggio del contenuto Web di Intune per i dispositivi iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Preconfigurazione delle autorizzazioni dei dispositivi per le app Android for Work <!-- 621614 -->
Per le app distribuite in profili di lavoro di dispositivi Android For Work, è ora possibile configurare lo stato delle autorizzazioni per le singole app.  Per impostazione predefinita, le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiederanno agli utenti di accettare o rifiutare le autorizzazioni.  Se ad esempio un'app usa il microfono del dispositivo, all'utente finale viene chiesto di concedere all'app l'autorizzazione per l'uso del microfono. Questa funzionalità consente di definire le autorizzazioni per conto dell'utente finale.  È possibile configurare le autorizzazioni per a) negare automaticamente senza avvisare l'utente, b) approvare automaticamente senza avvisare l'utente o c) richiedere all'utente di accettare o negare. Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Definizione del PIN specifico dell'app per i dispositivi Android for Work <!-- 728976, 1102534 -->
I dispositivi Android 7.0 e versioni successive con un profilo di lavoro gestito come dispositivo Android for Work consentono all'amministratore di definire criteri di passcode applicabili solo alle app nel profilo di lavoro.  Le opzioni includono:

- Definire solo criteri di passcode a livello di dispositivo: si tratta del passcode che l'utente deve usare per sbloccare l'intero dispositivo.
- Definire solo criteri di passcode del profilo di lavoro: agli utenti finali viene chiesto di immettere un passcode ogni volta che viene aperta un'app nel profilo di lavoro.
- Definire criteri sia del dispositivo che del profilo di lavoro: l'amministratore IT può scegliere di definire sia criteri di passcode del dispositivo che criteri di passcode del profilo di lavoro con complessità diverse (ad esempio, un PIN di 4 cifre per sbloccare il dispositivo, ma un PIN di 6 cifre per aprire un'app di lavoro).

Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Questa funzionalità è disponibile solo in Android 7.0 e versioni successive.  Per impostazione predefinita, l'utente finale può usare i due PIN definiti separatamente oppure scegliere di combinare i due PIN definiti in quello più complesso.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nuove impostazioni per i dispositivi Windows 10 <!-- 978585 -->
Sono state aggiunte nuove [impostazioni di restrizione dei dispositivi Windows](device-restrictions-windows-10.md) che controllano funzionalità come schermi wireless, individuazione dei dispositivi, passaggio da un'attività a un'altra e messaggi di errore della scheda SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Aggiornamenti della configurazione del certificato <!-- 918991 and 823198 -->
Per la creazione di un profilo di certificato SCEP, l'opzione **Personalizzato** per **Formato nome soggetto** è disponibile per i dispositivi iOS, Android e Windows. Prima dell'aggiornamento, il campo **Personalizzato** era disponibile solo per i dispositivi iOS. Per altre informazioni, vedere [Come creare un profilo certificato SCEP] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile).

Per la creazione di un profilo di certificato PKCS, è disponibile l'opzione **Custom Azure AD attribute** (Attributo Azure AD personalizzato) per **Nome alternativo soggetto**. È disponibile l'opzione **Reparto** quando si seleziona **Custom Azure AD attribute** (Attributo Azure AD personalizzato). Per altre informazioni, vedere [Come creare un profilo certificato PKCS](certficates-pfx-configure.md#create-a-device-configuration-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configurare più app che possono essere eseguite quando un dispositivo Android è in modalità tutto schermo<!-- 662059 -->
Quando un dispositivo Android è in modalità tutto schermo, in precedenza era possibile configurare una sola app per consentirne l'esecuzione. È ora possibile configurare più app usando l'ID, l'URL dello store oppure selezionando un'app Android già gestita. Per altre informazioni vedere [Impostazioni della modalità tutto schermo](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>Aprile 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Supporto per la gestione dell'app Classroom Apple
È ora possibile gestire l'app Classroom iOS nei dispositivi iPad. Configurare l'app Classroom nell'iPad degli insegnanti con la classe e i dati sugli studenti corretti, quindi configurare gli iPad degli studenti registrati in una classe, in modo da poterli controllare tramite l'app.
Per altri dettagli, vedere [Configurare le impostazioni di iOS relative alla formazione](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Supporto per le opzioni di configurazione gestita per le app Android <!-- 621621 -->
Le app Android nel Play Store che supportano le opzioni di configurazione gestita ora possono essere configurate da Intune.  Questa funzionalità consente ai responsabili IT di visualizzare l'elenco dei valori di configurazione supportati da un'app e fornisce un'interfaccia utente guidata avanzata per consentire la configurazione di tali valori.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nuovi criteri Android per PIN complessi <!-- 722069 -->
È ora possibile impostare una [password](device-restrictions-android.md#password) obbligatoria di tipo Complessa numerica in un profilo di dispositivo Android per i dispositivi che eseguono Android 5.0 e versioni successive.  Usare questa impostazione per impedire agli utenti dei dispositivi di creare un PIN contenente numeri ripetuti o consecutivi, ad esempio 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Supporto aggiuntivo per i dispositivi Android for Work
- **Gestire le impostazioni delle password e dei profili di lavoro** <!-- 612808 -->

  Questo nuovo criterio di restrizione dei dispositivi Android for Work ora consente di gestire le impostazioni delle password e dei profili di lavoro nei dispositivi Android for Work gestiti.

- **Consentire la condivisione dei dati tra i profili di lavoro e personali** <!-- 1045102 -->

Questo profilo di restrizione dei dispositivi Android for Work ora offre nuove opzioni che consentono di configurare la condivisione dei dati tra i profili di lavoro e quelli personali.

- **Limitare il copia e incolla tra i profili di lavoro e personali** <!-- 1046094 -->

  Un nuovo profilo di dispositivo personalizzato per i dispositivi Android for Work consente ora di limitare le operazioni di copia e incolla tra app di lavoro e personali.

Per altre informazioni, vedere l'articolo sulle [restrizioni dei dispositivi per Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Assegnazione di app LOB a dispositivi iOS e Android <!-- 1057568 -->
È ora possibile assegnare a utenti o dispositivi app line-of-business (LOB) per [iOS](lob-apps-ios.md) (file con estensione ipa) e per [Android](lob-apps-android.md) (file con estensione apk).


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nuovi criteri dei dispositivi per iOS <!-- 723774, 723815, 723826, 723830 -->
- **App nella schermata iniziale**: stabilisce quali sono le app visualizzate dagli utenti nella [schermata iniziale dei loro dispositivi iOS](home-screen-settings-ios.md). Questo criterio modifica il layout della schermata iniziale ma non distribuisce nessuna app.

- **Connessioni ai dispositivi AirPrint**: specifica i [dispositivi AirPrint](air-print-settings-ios-macos.md) (stampanti di rete) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Connessioni ai dispositivi AirPlay**: specifica i [dispositivi AirPlay](airplay-settings-ios.md) (come Apple TV) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Messaggio personalizzato della schermata di blocco**: consente di configurare un messaggio personalizzato che gli utenti visualizzeranno nella schermata di blocco del loro dispositivo iOS, in sostituzione del messaggio della schermata di blocco predefinito. Per altre informazioni, vedere [Attivare la modalità di dispositivo perso nei dispositivi iOS](device-lost-mode.md).

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Limitazione delle notifiche push per le app per iOS <!-- 723767 -->
In un profilo di restrizione del dispositivo di Intune è possibile configurare le [impostazioni di notifica](app-notification-settings-ios.md) seguenti per i dispositivi iOS:

- Attivare o disattivare completamente la notifica per un'app specificata.
- Attivare o disattivare la notifica nel Centro notifiche per un'app specificata.
- Specificare il tipo di avviso, ovvero **Nessuno**, **Banner** o **Modal Alert** (Avviso modale).
- Specificare se sono consentite le notifiche per questa app.
- Specificare se sono consentite le notifiche audio.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurazione delle app per iOS per l'esecuzione in modo autonomo in Modalità applicazione singola <!-- 737837 -->
È possibile usare un profilo di dispositivo di Intune per configurare i dispositivi iOS per l'esecuzione delle applicazioni specificate in [Modalità applicazione singola autonoma](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quando questa modalità è configurata e l'app è in esecuzione, il dispositivo è bloccato in modo che possa eseguire solo quell'app. Un esempio è quando si configura un'app che consente agli utenti di eseguire un test nel dispositivo. Quando le operazioni dell'app sono state completate o si rimuove questo criterio, il dispositivo torna allo stato normale.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurazione di domini trusted per posta elettronica ed esplorazione Web nei dispositivi iOS <!-- 723765 -->
Da un profilo di restrizione del dispositivo iOS è ora possibile configurare le [impostazioni di dominio](device-restrictions-ios.md#domains) seguenti:

- **Domini di posta elettronica non contrassegnati**: i messaggi inviati o ricevuti dall'utente che non corrispondono ai domini specificati qui verranno contrassegnati come non attendibili.

- **Domini Web gestiti**: i documenti scaricati dagli URL specificati qui verranno considerati gestiti (solo Safari).  

- **Domini con riempimento automatico della password di Safari**: gli utenti possono salvare le password in Safari solo dagli URL corrispondenti ai modelli specificati qui. Per usare questa impostazione, il dispositivo deve essere in modalità con supervisione e non deve essere configurato per più utenti (iOS 9.3 e versioni successive).


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>App VPP disponibili nel portale aziendale iOS <!-- 748782 -->
È ora possibile assegnare app per iOS acquistate con Volume Purchase Program (VPP) come installazioni **disponibili** per gli utenti finali. Gli utenti finali avranno bisogno di un account Apple Store per installare l'app.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizzazione di eBook dallo Store VPP di Apple <!-- 800878 -->
È ora possibile [sincronizzare i libri](vpp-apps-ios.md) acquistati nello store Apple Volume Purchase Program con Intune e assegnarli agli utenti.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestione di più utenti per i dispositivi Samsung Knox Standard <!-- 971988 -->
I dispositivi che eseguono Samsung Knox Standard sono ora supportati per la [gestione multiutente](android-enroll.md) in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure Active Directory e il dispositivo è gestito centralmente indipendentemente dal fatto che sia o meno in uso.  Dopo aver eseguito l'accesso gli utenti finali possono accedere alle app e implementare i criteri loro assegnati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Altre impostazioni relative alle restrizioni dei dispositivi per Windows <!-- 818566 -->
Sono ora supportate altre [impostazioni di restrizione dei dispositivi per Windows](device-restrictions-windows-10.md) come maggiore supporto per il browser Edge, personalizzazione della schermata di blocco del dispositivo, personalizzazioni del menu Start, sfondo per la ricerca Windows Spotlight e impostazione del proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Supporto multiutente per Windows 10 Creators Update <!-- 822547 -->
È stato aggiunto il supporto per la [gestione multiutente](windows-enroll.md) per i dispositivi che eseguono Windows 10 Creators Update e sono aggiunti al dominio di Azure Active Directory. Ciò significa che quando utenti standard diversi accedono al dispositivo con le credenziali di Azure AD ricevono tutte le app e i criteri assegnati al loro nome utente. Gli utenti non possono attualmente usare il portale aziendale per scenari self-service, ad esempio l'installazione di app.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start per i PC Windows 10<!-- 1004830 -->
È ora disponibile una nuova [azione del dispositivo Fresh Start](device-fresh-start.md) per i PC Windows 10.  Quando si esegue questa azione, vengono rimosse tutte le app precedentemente installate nel PC e il computer è aggiornato automaticamente alla versione più recente di Windows. Questa funzionalità può essere usata per rimuovere le app OEM che spesso sono preinstallate in un nuovo PC. È possibile configurare se i dati utente devono essere conservati quando si esegue questa azione del dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Percorsi di aggiornamento aggiuntivi per Windows 10 <!-- 903672 -->
È ora possibile creare [criteri di aggiornamento dell'edizione per aggiornare i dispositivi](edition-upgrade-configure-windows-10.md) alle seguenti edizioni aggiuntive di Windows 10:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Registrazione in blocco di dispositivi Windows 10 <!-- 747607 -->
È ora possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune con Windows Configuration Designer (WCD). Per abilitare la [registrazione MDM in blocco](windows-bulk-enroll.md) del tenant di Azure AD, creare un pacchetto di provisioning che aggiunga i dispositivi al tenant di Azure AD usando Windows Configuration Designer e applicare il pacchetto ai dispositivi di proprietà dell'azienda che si vuole registrare e gestire in blocco. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento gli scenari di tipo self-service o portale aziendale non sono supportati.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nuove impostazioni MAM per PIN e percorsi di archiviazione gestita <!-- 581122, 736644 -->
Sono ora disponibili due nuove impostazioni dell'app per semplificare gli scenari di gestione di applicazioni mobili (MAM):

- **Disabilitare il PIN dell'app quando il PIN del dispositivo è gestito**: consente di rilevare se nel dispositivo registrato è presente un PIN del dispositivo e, in tal caso, di ignorare il PIN dell'app attivato dai criteri di protezione delle app. Questa impostazione consentirà di ridurre il numero di volte in cui gli utenti visualizzeranno un prompt di richiesta del PIN all'apertura di un'applicazione abilitata per MAM in un dispositivo registrato. Questa funzionalità è disponibile per sia per Android che per iOS.

- **Selezionare i servizi di archiviazione in cui è possibile salvare i dati aziendali**: consente di specificare i percorsi di archiviazione in cui salvare i dati aziendali. Gli utenti possono eseguire il salvataggio nei servizi di posizione di archiviazione selezionati, il che significa che tutti gli altri servizi di posizione di archiviazione non elencati verranno bloccati.

  I servizi di posizione di archiviazione supportati sono i seguenti:

  - OneDrive
  - Business SharePoint Online
  - Archiviazione locale

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portale del Supporto tecnico per la risoluzione dei problemi <!-- 907448 -->
Il nuovo [portale per la risoluzione dei problemi](help-desk-operators.md) consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare utenti e dispositivi e di eseguire attività per la risoluzione dei problemi tecnici di Intune.

## <a name="march-2017"></a>Marzo 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Supporto per la modalità di dispositivo perso di iOS <!--431695-->
Per i dispositivi iOS 9.3 e versioni successive, Intune ha aggiunto il supporto per la **modalità di dispositivo perso**. È ora possibile bloccare un dispositivo per impedirne l'uso e visualizzare un messaggio e un numero di telefono di contatto nella schermata di blocco del dispositivo.

L'utente finale non sarà in grado di sbloccare il dispositivo finché la modalità di dispositivo perso non verrà disabilitata da un amministratore. Quando la modalità di dispositivo perso è abilitata, è possibile usare l'azione **Individua il dispositivo** per visualizzare la posizione geografica del dispositivo su una mappa nella console di Intune.

Deve trattarsi di un dispositivo iOS di proprietà dell'azienda, registrato con DEP, in cui sia attiva la modalità con supervisione.

Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).

### <a name="improvements-to-device-actions-report---677150--"></a>Miglioramenti al report Azioni del dispositivo <!--677150-->
Le prestazioni del report Azioni del dispositivo sono state migliorate. È inoltre possibile filtrare il report in base allo stato. Si possono ad esempio mostrare solo le azioni del dispositivo che sono state completate.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Assegnare app line-of-business agli utenti con dispositivi non registrati <!--748823-->
Ora è possibile assegnare app line-of-business dallo store agli utenti anche se i dispositivi degli utenti non sono registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale.

### <a name="new-compliance-reports---846671--"></a>Nuovi report di conformità <!--846671-->
Sono ora disponibili report di conformità che definiscono il comportamento di conformità dei dispositivi in ambito aziendale e consentono di risolvere rapidamente i problemi correlati alla conformità riscontrati dagli utenti. È possibile visualizzare le informazioni seguenti:

- Stato di conformità generale dei dispositivi
- Stato di conformità per una singola impostazione
- Stato di conformità per singoli criteri

È anche possibile usare questi report per eseguire il drill-down in un singolo dispositivo e visualizzare le impostazioni e i criteri specifici che hanno effetto su tale dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima della registrazione di Apple era accessibile solo dai collegamenti nel portale di Azure. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.


## <a name="february-2017"></a>Febbraio 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilità di limitare la registrazione di dispositivi mobili <!--747600, 795782-->
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.

* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.  
* Solo per iOS e Android è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Visualizzare tutte le azioni nei dispositivi gestiti <!--677150-->
Il nuovo report __Azioni del dispositivo__ mostra gli utenti che hanno eseguito azioni remote come il ripristino delle impostazioni predefinite nei dispositivi e lo stato dell'azione. Vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->
Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="display-device-categories---814654--"></a>Visualizzare le categorie di dispositivi <!--814654-->
È ora possibile visualizzare la categoria dei dispositivi come colonna dell'elenco dei dispositivi. È inoltre possibile modificare la categoria nella sezione delle proprietà del pannello delle proprietà del dispositivo. Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurare le impostazioni di Windows Update for Business <!--776716-->

Windows as a Service è il nuovo modo per distribuire gli aggiornamenti per Windows 10. A partire da Windows 10, i nuovi aggiornamenti qualitativi e delle funzionalità includeranno il contenuto di tutti gli aggiornamenti precedenti. Ciò significa che, una volta installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 sono perfettamente aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Usando Windows Update for Business, è possibile semplificare l'esperienza di gestione degli aggiornamenti in modo da non dover approvare singoli aggiornamenti per gruppi di dispositivi. È comunque possibile gestire i rischi nei propri ambienti configurando una strategia di implementazione degli aggiornamenti. In questo modo, Windows Update verificherà che gli aggiornamenti vengano installati al momento opportuno. Microsoft Intune offre la possibilità di configurare le impostazioni di aggiornamento sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. Per gli aggiornamenti i dispositivi accedono direttamente a Windows Update. Usare Intune per configurare e gestire gli **anelli di aggiornamento di Windows 10**. Un anello di aggiornamento contiene un gruppo di impostazioni che definiscono quando e come vengono installati gli aggiornamenti di Windows 10. Per informazioni dettagliate, vedere [Configurare le impostazioni di Windows Update for Business](windows-update-for-business-configure.md).
