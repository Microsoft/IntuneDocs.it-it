---
title: Edizione anticipata
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 09/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0ac0d1fd2f618339f847201f333d3f32561ca6b1
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="the-early-edition-for-microsoft-intune---september-2017"></a>Edizione anticipata per Microsoft Intune - Settembre 2017

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non condividere queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
>Le seguenti modifiche di Intune sono in fase di sviluppo. Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
   
-->

  

## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure


### <a name="google-play-protect-support-on-android----908720----"></a>Supporto di Google Play Protect in Android <!-- 908720  -->  
Con il rilascio di Android Oreo, Google introduce un gruppo di funzionalità di sicurezza denominato Google Play Protect che consente a utenti e organizzazioni di eseguire app e immagini Android sicure. Intune supporta le funzionalità di Google Play Protect, inclusa l'attestazione remota SafetyNet.  Gli amministratori possono impostare requisiti per i criteri di conformità che richiedono la configurazione e l'integrità di Google Play Protect. L'**attestazione dispositivo SafetyNet** richiede che il dispositivo si connetta a un servizio Google per verificare che il dispositivo sia integro e non compromesso. Gli amministratori possono anche definire un'impostazione del profilo di configurazione per far sì che Android for Work richieda la verifica delle app installate da parte di Google Play Services.  L'accesso condizionale può impedire agli utenti di accedere alle risorse aziendali se un dispositivo non è conforme ai requisiti di Google Play Protect. 

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>Impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo <!-- 1333292 -->
È possibile usare [criteri personalizzati per dispositivi Android](custom-settings-android.md) per impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo.
A tale scopo, configurare criteri personalizzati di Android impostando l'URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange su **TRUE** e quindi assegnarli ai gruppi necessari.

### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>Visualizzare le assegnazioni dei criteri di protezione delle app per la risoluzione dei problemi <!--  1475003 -->
In questa versione futura verrà aggiunta un'opzione per i **criteri di protezione delle app** all'elenco a discesa **Assegnazioni** disponibile nel pannello della risoluzione dei problemi. Sarà ora possibile selezionare Criteri di protezione delle app per visualizzare i criteri assegnati agli utenti selezionati.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creare app iOS limitate ad Apple App Store di aree specifiche<!-- 1281692 -->
Sarà possibile specificare le impostazioni locali del paese durante la creazione di un'app gestita da Apple App Store.

> [!NOTE]  
> Attualmente è possibile creare solo app gestite di Apple App Store presenti nello Store degli Stati Uniti.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selezionare l'Apple Store del paese per la sincronizzazione delle app VPP <!-- 1332311 -->  
È possibile configurare lo Store del paese per il Volume Purchase Program (VPP) quando si carica il token VPP. Intune sincronizza le app VPP per tutte le impostazioni locali dello Store del paese VPP specificato.

> [!NOTE]  
> Attualmente Intune sincronizza solo le app VPP dello Store VPP del paese corrispondenti all'impostazione locale di Intune in cui è stato creato il tenant di Intune.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Aggiornare le app VPP iOS concesse in licenza a utenti e dispositivi <!-- 1305564 -->  
Sarà possibile configurare il token VPP iOS per aggiornare tutte le app acquistate per tale token tramite il servizio Intune. Intune rileverà gli aggiornamenti delle app VPP nell'App Store e li invierà automaticamente al dispositivo quando questo si connette.

### <a name="ios-11-support----1428975---"></a>Supporto di iOS 11 <!-- 1428975 -->
Intune supporterà iOS 11 quando verrà rilasciato da Apple.

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838----"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team <!--- 1308838  -->
In questa versione vengono aggiunte molte nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team per la gestione dei dispositivi Surface Hub.
Per altre informazioni su questo profilo, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="support-for-windows-10-edition-upgrade-policy------903672-1119689---"></a>Supporto dei criteri di aggiornamento edizione di Windows 10 <!-- 903672, 1119689 -->  
Sarà possibile creare criteri di aggiornamento edizione di Windows 10 per l'aggiornamento di dispositivi Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Per informazioni dettagliate sugli aggiornamenti edizione di Windows 10, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

### <a name="review-policy-compliance-for-windows-10-update-rings----1352223---"></a>Esaminare la conformità ai criteri per gli anelli di aggiornamento di Windows 10 <!-- 1352223 -->  
Sarà possibile esaminare un report sui criteri per gli anelli di aggiornamento di Windows 10 da **Aggiornamenti software** > **Stato di distribuzione per ogni anello di aggiornamento**. Il report sui criteri include lo stato di distribuzione degli anelli di aggiornamento configurati. 

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>App del portale aziendale di Windows 10 aggiunta ai criteri per il consenso di Windows Information Protection<!-- 677129 -->  
L'app del portale aziendale di Windows 10 verrà aggiornata per supportare Windows Information Protection (WIP). L'app può essere aggiunta ai criteri per il consenso di WIP. Con questa modifica non è più necessario aggiungere l'app all'elenco **Esente**. 

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Supporto remoto per dispositivi Windows e Windows Mobile <!-- 1070473 -->    
Intune potrà usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per poter offrire assistenza remota agli utenti che eseguono dispositivi Windows e Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>Analizzare dispositivi con Windows Defender <!-- 1280988  1280990   -->
Sarà possibile eseguire un'**analisi veloce**, un'**analisi completa** e **aggiornare le firme** con Windows Defender Antivirus nei dispositivi Windows 10 gestiti. Dal pannello della panoramica del dispositivo, scegliere l'azione da eseguire nel dispositivo. Verrà chiesto di confermare l'azione prima che il comando venga inviato al dispositivo. 

**Analisi veloce**: l'analisi veloce analizza i percorsi in cui il malware si registra per l'avvio, ad esempio le chiavi del Registro di sistema e le cartelle di avvio di Windows note. L'analisi veloce richiede in media cinque minuti. Unita all'impostazione della **protezione in tempo reale Always On** che analizza i file quando vengono aperti, chiusi e ogni volta che un utente passa a una cartella, l'analisi veloce consente di fornire protezione da software dannoso che potrebbe trovarsi nel sistema o nel kernel. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Analisi completa**: l'analisi completa può essere utile nei dispositivi in cui sono state riscontrate minacce malware per identificare se sono presenti componenti inattivi che richiedono una pulizia più approfondita ed è utile per l'esecuzione di analisi su richiesta. L'analisi completa può richiedere un'ora. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Aggiornare le firme**: il comando di aggiornamento delle firme aggiorna le definizioni e le firme malware di Windows Defender Antivirus, garantendo l'efficacia nel rilevamento di malware. Questa funzionalità è applicabile solo ai dispositivi Windows 10 con connettività Internet. 

### <a name="bitlocker-device-configuration----1397398---"></a>Configurazione di BitLocker per il dispositivo <!-- 1397398 -->  
**Crittografia di Windows > Impostazioni di base** includerà la nuova impostazione **Avviso per la crittografia dischi di altro tipo** che consente di disabilitare il [prompt di avviso](https://docs.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) per crittografie disco di altro tipo che possono essere in uso nel dispositivo dell'utente.  Il prompt di avviso richiede il consenso dell'utente finale prima di configurare BitLocker nel dispositivo e blocca la configurazione di BitLocker fino alla conferma dell'utente finale.  La nuova impostazione disabilita l'avviso per l'utente finale.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Passaggio del portale aziendale per Windows 8.1 e Windows Phone 8.1 alla modalità di mantenimento <!--1428681-->
A partire da ottobre 2017, le app del portale aziendale per Windows 8.1 e Windows Phone 8.1 passeranno alla modalità di mantenimento. Le app e gli scenari esistenti, ad esempio la registrazione e la conformità, continueranno a essere supportati per queste piattaforme. Queste app rimarranno disponibili per il download tramite i canali di rilascio esistenti, ad esempio Microsoft Store. 

Nella modalità di mantenimento, queste app riceveranno solo aggiornamenti della sicurezza critici. Non verranno rilasciati altri aggiornamenti o funzionalità per queste app. Per le nuove funzionalità è consigliabile aggiornare i dispositivi a Windows 10 o Windows 10 Mobile. 

###  <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloccare la funzionalità di copia e incolla tra i profili di lavoro e i profili personali in Android for Work <!-- 1098994 -->   
Con questa versione è possibile configurare il profilo di lavoro di Android for Work per bloccare l'operazione di copia e incolla tra le app di lavoro e le app personali. Questa nuova impostazione è disponibile nel profilo **Limitazioni del dispositivo** per la piattaforma **Android for Work** in **Impostazioni del profilo di lavoro**.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuovi comportamenti dell'app del portale aziendale per Android con i profili di lavoro <!---1485783--->
Quando si registra un dispositivo Android for Work con un profilo di lavoro, è l'app del portale aziendale nel profilo di lavoro a eseguire attività di gestione nel dispositivo. A meno che non si usi un'app abilitata per MAM nel profilo personale, l'app del portale aziendale per Android non è più utile. Per migliorare l'esperienza con i profili di lavoro, Intune nasconderà automaticamente l'app del portale aziendale personale dopo la registrazione del profilo di lavoro.

L'app del portale aziendale per Android può essere abilitata in qualsiasi momento nel profilo personale passando al [portale aziendale in Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e selezionando **Abilita**.

### <a name="intune-mam--outlook-for-android-add-ins-----1450688---"></a>Componenti aggiuntivi MAM di Intune e Outlook per Android <!-- 1450688 -->
Tra alcune settimane, il team di Office annuncerà componenti aggiuntivi per Outlook in Android. Questo set di funzionalità aggiuntive è già presente in Outlook in Windows, iOS, Web e Mac. Poiché i componenti aggiuntivi vengono gestiti tramite Exchange, gli utenti potranno condividere dati e messaggi in Outlook e applicazioni aggiuntive non gestite, a meno che l'accesso ai componenti aggiuntivi non venga disattivato dall'amministratore di Exchange. 

Per gestire le autorizzazioni di accesso ai componenti aggiuntivi, rivolgersi all'amministratore di Exchange per verificare che i criteri di protezione dati MAM vengano applicati ai componenti aggiuntivi.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se i criteri di Exchange sono già impostati per impedire il caricamento o l'installazione di componenti aggiuntivi da parte dell'utente, non proseguire la lettura. I criteri MAM verranno applicati come previsto. Se in MAM sono stati tuttavia impostati criteri per limitare le operazioni Taglia, Copia e Incolla all'interno di Outlook in Android e i criteri per i componenti aggiuntivi non sono stati impostati in Exchange, gli utenti potranno installare componenti aggiuntivi in Outlook per impostazione predefinita. Questi componenti aggiuntivi possono accedere al corpo del messaggio, all'oggetto e ad altre proprietà del messaggio. Per impedire all'utente finale di installare componenti aggiuntivi, l'amministratore di Exchange deve rimuovere i ruoli "App del Marketplace" e "App personalizzate". Per altri dettagli, vedere il collegamento per le informazioni aggiuntive di seguito.

Si noti che la modifica dell'impostazione in Exchange verrà applicata ad Outlook in Windows, iOS, Web, Mac e Mobile. 

#### <a name="what-do-i-need-to-do"></a>Cosa fare
Verificare subito i criteri di Exchange. Informare lo staff IT e il supporto tecnico. Contattare il team di supporto per eventuali dubbi o domande specifiche. 

### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Raccolta di entità di associazione dei dispositivi degli utenti aggiunta al modello di dati di Data Warehouse di Intune<!-- 1187917 -->
Sarà possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi. Il modello di dati è accessibile tramite il file di Power BI (PBIX) recuperato dalla pagina Data warehouse di Intune, tramite l'endpoint OData oppure sviluppando un client personalizzato.


<!-- the following are present prior to 1709 -->

### <a name="actions-for-non-compliance----730266--"></a>Azioni per la non conformità <!--730266-->     
Le *azioni per la mancata conformità* sono una nuova funzionalità dei criteri di conformità che consente di intervenire sui dispositivi non conformi. È possibile specificare una o più azioni e il periodo di tempo in cui devono essere eseguite tali azioni. Ad esempio, è possibile segnalare immediatamente agli utenti i dispositivi non conformi non appena diventano non conformi, tramite posta elettronica, oppure è possibile impedire ai dispositivi non conformi di accedere alle risorse aziendali dopo un periodo di tolleranza di 3 giorni tramite l'accesso condizionale.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuovo report che elenca i dispositivi iOS con versioni precedenti di iOS <!-- 1352223 -->
Il report **Out-of-date iOS Devices** (Dispositivi iOS non aggiornati) sarà disponibile dall'area di lavoro **Aggiornamenti software**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento di iOS e con aggiornamenti disponibili. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente. 

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10
<!--- 978575, 1308849, -->
Sono state aggiunte nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 nella categoria Windows Defender SmartScreen.

Per informazioni dettagliate sul profilo di restrizione dei dispositivi Windows 10, vedere [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).

### <a name="android-for-work-support-for-lookout----1087312---"></a>Supporto di Android for Work per Lookout <!-- 1087312 -->   
Il connettore di Intune con Lookout supporterà i dispositivi Android for Work quando si usa l'app Lookout for Work. È possibile distribuire l'app Lookout all'interno o all'esterno del contenitore.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Protezione app di Intune e strumenti di sviluppo MDX Citrix <!-- 709185 -->
È possibile gestire i dispositivi e le app usando in combinazione Citrix XenMobile MDX e Microsoft Intune. Ciò consente di gestire le app con i criteri di protezione delle app di Intune usando allo stesso tempo la tecnologia mVPN di Citrix.

È disponibile un repository di codice che contiene lo strumento di wrapping delle app di Intune e Intune App SDK per iOS e Android, per l'integrazione con la tecnologia mVPN MDX di Citrix.

### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuovo partner di Mobile Threat Defense  <!-- 954681 -->
È ora possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Zimperium, una soluzione di Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Zimperium. È possibile configurare criteri di accesso condizionale EMS in base alla valutazione dei rischi di Zimperium abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Nuovo collegamento all'interfaccia utente per i criteri di accesso condizionale di Azure AD da Intune<!-- 1016201 -->
Gli amministratori IT possono impostare criteri condizionali basati su app tramite la nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Azure AD. I criteri di accesso condizionale basati su app disponibili nella sezione Protezione app di Intune in Azure rimangono in tale posizione per il momento e vengono applicati in affiancamento. Sarà disponibile un altro collegamento per comodità alla nuova interfaccia utente per i criteri di accesso condizionale in Azure AD dal carico di lavoro Intune.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale<!-- 676614 -->   
È possibile avere più ruoli server Accesso client per Exchange Connector locale. Ad esempio, se il server Accesso client principale smette di funzionare, Exchange Connector riceve una query per eseguire il fallback in altri server Accesso client. Questa funzionalità garantisce che il servizio non venga interrotto.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->   
Sarà disponibile il Management Pack di System Center Operations Manager per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questo Management Pack consente di eseguire il monitoraggio di Intune in diversi modi quando è necessario risolvere i problemi.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fine del supporto per iOS 8.0 <!---1164477--->
Le app gestite e l'app Portale aziendale per iOS richiederanno iOS 9.0 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati entro settembre non potranno accedere al Portale aziendale o a tali app.  

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fine del supporto per Android 4.3 e versioni precedenti <!---1171127, 1326920 --->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati prima dell'inizio del mese di ottobre non potranno accedere al Portale aziendale o a tali app. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Promemoria di supporto della piattaforma: il supporto Mainstream di Windows Phone 8.1 termina l'11 luglio 2017 <!-- 1327781 -->  
L'11 luglio 2017, termina il supporto Mainstream per la piattaforma di Windows Phone 8.1. Il supporto per PC Windows 8.1 viene mantenuto.

Ciò non ha alcun impatto immediato sui dispositivi Windows Phone 8.1 gestiti dal servizio di Intune. I dispositivi registrati continuano a funzionare regolarmente e tutti i criteri, le configurazioni e le app continuano a funzionare come previsto. Si noti che non sono previsti miglioramenti destinati alla piattaforma Windows Phone 8.1 nel servizio di Intune e all'app Portale aziendale di Windows Phone 8.1.

È consigliabile aggiornare a Windows 10 Mobile i dispositivi Windows Phone 8.1 idonei, appena possibile. 





## <a name="intune-apps"></a>App di Intune
### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Azione di aggiornamento aggiunta all'app del portale aziendale per Windows 10 <!--1132468-->
L'app del portale aziendale per Windows 10 consentirà agli utenti di aggiornare i dati nell'app trascinando verso il basso oppure, nei sistemi desktop, premendo F5.


### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Le app disponibili con o senza registrazione possono essere ora installate senza richiesta di registrazione. <!-- 1334712 -->
Le app aziendali rese disponibili con o senza registrazione nell'app del portale aziendale Android possono essere installate senza richiesta di registrazione.

### <a name="ios-company-portal-display-large-icons----1454593---"></a>Il portale aziendale iOS visualizza icone grandi <!-- 1454593 -->
È in corso la correzione di un problema noto relativo alla visualizzazione delle icone nel riquadro app del portale aziendale iOS. Se si caricano icone di app di almeno 120 x 120 pixel, le icone vengono ora visualizzate nel [sito Web del portale aziendale] (https://portal.manage.microsoft.com) e nelle pagine delle app del portale aziendale iOS occupando l'intero riquadro app.

### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android------1396349---"></a>Testo più comprensibile per l'app del portale aziendale per Android <!---1396349--->    
Il processo di registrazione per l'app del portale aziendale per Android è ora più semplice per gli utenti finali, grazie all'uso di un nuovo testo più comprensibile. 


<!-- the following are present prior to 1709 -->


### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Supporto di Intune Managed Browser per iOS e Android <!---1374196--->
A partire da ottobre 2017, l'app Intune Managed Browser per Android supporta solo i dispositivi che eseguono Android 4.4 e versioni successive. L'app Intune Managed Browser per iOS supporta solo i dispositivi che eseguono iOS 9.0 e versioni successive. Le versioni precedenti di Android e iOS saranno in grado di continuare a usare Managed Browser, ma non sarà possibile installare nuove versioni dell'app e le funzionalità dell'app potrebbero non essere tutte disponibili. Si consiglia di eseguire l'aggiornamento di questi dispositivi a una versione supportata del sistema operativo.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Consentire agli utenti di accedere all'app Portale aziendale per Android senza registrazione <!---1169910--->  
Gli utenti finali potranno presto non avere l'obbligo di registrare il dispositivo per accedere all'app Portale aziendale per Android. Agli utenti finali di organizzazioni che usano criteri di protezione delle app non verrà più richiesto di registrare il dispositivo quando aprono l'app Portale aziendale. Gli utenti finali potranno anche installare app dal Portale aziendale senza registrare il dispositivo. 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Messaggio di errore migliorato quando un utente raggiunge il numero massimo di dispositivi di cui è consentita la registrazione <!-- 1270370 -->
Invece di un messaggio di errore generico, gli utenti finali vedranno un messaggio di errore descrittivo e interattivo: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin." (È stato raggiunto il numero massimo di dispositivi consentiti dall'amministratore IT. Rimuovere un dispositivo registrato o richiedere assistenza all'amministratore IT.)

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate per iOS<!--739894-->
Verrà aggiunta l'opzione **Ownership Type** (Tipo di proprietà) nella schermata Dettagli dispositivo nell'app Portale aziendale per iOS. In questo modo gli utenti possono ottenere ulteriori informazioni sulla privacy direttamente da questa pagina dalla documentazione finale di Intune. Potranno accedere a queste informazioni anche nella schermata Informazioni su.

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>Le pagine dei dettagli delle app visualizzano nuove informazioni per i dispositivi Android <!--1287476-->
La pagina dei dettagli dell'app nell'app Portale aziendale per Android visualizzerà le categorie di app definite dall'amministratore IT per l'app.

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>Le finestre di dialogo per la gestione delle applicazioni mobili di Intune hanno ora un'interfaccia moderna <!-- 1199015 -->
Le finestre di dialogo per la gestione delle applicazioni mobili di Intune sono state aggiornate per lo stile moderno. Le finestre di dialogo funzionano nello stesso modo dello stile precedente.

Nei dispositivi Android moderni, le finestre di dialogo di errore o di notifica visualizzate da Intune avranno ora il nuovo aspetto aggiornato.



## <a name="notices"></a>Notifiche
### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->   
A partire dalla primavera 2017, Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Modifiche pianificate: Intune ha intenzione di modificare l'esperienza del portale per i partner di Intune <!-- 1050016 -->
A partire dall'aggiornamento del servizio previsto per la metà di maggio 2017, la pagina Intune Partner verrà rimossa dal sito manage.microsoft.com.  

Gli amministratori di partner non saranno più in grado di visualizzare e agire per conto dei clienti dalla pagina Intune Partner, ma dovranno invece effettuare l'accesso a uno degli altri due altri portali Microsoft per i partner.

Il [Centro per i partner Microsoft](https://partnercenter.microsoft.com/) e l'[interfaccia di amministrazione partner di Office 365](https://portal.office.com/) consentiranno entrambi di accedere agli account cliente gestiti. Procedendo come partner, usare uno di questi siti per gestire i clienti.



### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
