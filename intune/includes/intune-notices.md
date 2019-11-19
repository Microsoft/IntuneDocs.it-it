---
title: includere il file
description: includere il file
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/4/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 3d49d31ed08683508d3d231521e578688dd21bac
ms.sourcegitcommit: 737ad6c675deedfc6009f792023ff95981b06582
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74125512"
---
Questi avvisi forniscono importanti informazioni utili per prepararsi per le modifiche e le funzionalità di Intune future.

### <a name="intune-plan-for-change-windows-10-version-1703-company-portal-moving-out-of-support--5026679--"></a>Modifica prevista per Intune: Scadenza del supporto per il Portale aziendale Windows 10, versione 1703<!--5026679-->
Il supporto per Windows 10 versione 1703 (denominato anche Windows 10 RS2) è scaduto l'8 ottobre 2019 per le edizioni Enterprise e EDU. In Intune il supporto dell'app Portale aziendale per RS2/RS1 scadrà il 26 dicembre 2019.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Da questo momento non verranno visualizzate le nuove funzionalità nella versione specifica dell'app Portale aziendale, anche se il supporto di tale versione continuerà fino al 26 dicembre 2019 e includerà la fornitura degli aggiornamenti della sicurezza necessari per l'app Portale aziendale. Tuttavia, dato che dopo la scadenza del supporto Windows 10 versione 1703 non riceverà più aggiornamenti della sicurezza, è consigliabile aggiornare i dispositivi Windows a una versione di Windows più recente e assicurarsi avere la versione più recente dell'app Portale aziendale, in modo da continuare a ricevere le nuove caratteristiche e le funzionalità aggiuntive.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Le operazioni da eseguire dipendono dalla configurazione dell'ambiente in uso. In generale, tuttavia, è necessario identificare i dispositivi con versioni precedenti del sistema operativo e/o del Portale aziendale ed eseguire l'aggiornamento. Per impostare le fasi di aggiornamento di Windows 10, accedere a Intune -> Aggiornamenti software - Fasi di aggiornamento di Windows 10. La versione più recente dell'app Portale aziendale è la versione 10.3.5601.0. Richiedere agli utenti di acquistarla presso il Microsoft Store per rimanere aggiornati con le versioni future. È anche possibile usare Intune per installare la versione più recente nei dispositivi Windows tramite [Microsoft Store per le aziende](https://docs.microsoft.com/intune/windows-store-for-business).

#### <a name="additional-information"></a>Informazioni aggiuntive
[Aggiungere manualmente l'app Portale aziendale di Windows 10 usando Microsoft Intune](https://docs.microsoft.com/intune/store-apps-company-portal-app)


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Azione: Usare Microsoft Edge per l'esperienza protetta del browser di Intune<!--5728447-->
Come descritto nel corso dell'ultimo anno, Microsoft Edge per dispositivi mobili supporta la stessa gamma di funzionalità di gestione supportata da Managed Browser, ma garantisce un'esperienza utente molto migliore. Per lasciare spazio alle esperienze consolidate offerte da Microsoft Edge, Intune Managed Browser verrà ritirato. A partire dal 27 gennaio 2020 Intune non supporterà più Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica? 
A partire dal 1 febbraio 2020 Intune Managed Browser non sarà più disponibile in Google Play Store o nell'App Store iOS. Dopo tale data sarà ancora possibile indirizzare i nuovi criteri di protezione delle app a Intune Managed Browser, ma i nuovi utenti non potranno più scaricare l'app Intune Managed Browser. Inoltre in iOS le nuove clip Web che vengono distribuite a dispositivi registrati in MDM verranno aperte in Microsoft Edge anziché in Intune Managed Browser.  

Il 31 marzo 2020 Intune Managed Browser verrà rimosso dalla console di Azure. Di conseguenza non sarà più possibile creare nuovi criteri per Intune Managed Browser. I criteri di Intune Managed Browser già implementati non subiranno variazioni. Intune Managed Browser verrà visualizzato nella console come applicazione line-of-business senza icone e i criteri esistenti continueranno ad apparire come associati all'app. Verrà anche rimossa l'opzione per reindirizzare il contenuto Web a Intune Managed Browser nel contesto della sezione Protezione dei dati dei criteri di protezione delle app.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica 
Per garantire una transizione ottimale da Intune Managed Browser a Microsoft Edge è consigliabile adottare le seguenti misure con il necessario anticipo: 

1. Impostare Microsoft Edge per iOS e Android come destinazione per i criteri di protezione delle app (detti anche MAM) e le impostazioni di configurazione delle app. Per riusare i criteri di Intune Managed Browser per Microsoft Edge è sufficiente impostare anche Microsoft Edge come destinazione dei criteri esistenti.  
2. Verificare che per tutte le app dell'ambiente protette tramite MAM il criterio di protezione "Limita il trasferimento di contenuto Web con altre app" sia impostato su "Browser gestiti da criteri". 
3. Verificare che per tutte le app protette tramite MAM l'impostazione di configurazione dell'app gestita "com.microsoft.intune.useEdge" sia impostata su True. A partire dal mese prossimo con la versione 1911 sarà possibile completare i passaggi 2 e 3 configurando semplicemente "Limita il trasferimento di contenuto Web con altre app" in modo che "Microsoft Edge" sia selezionato nella sezione Protezione dei dati dei criteri di protezione delle app. 

Il supporto delle clip Web in iOS e Android sarà disponibile a breve. Dopo il rilascio del supporto, sarà necessario reimpostare la destinazione delle clip Web preesistenti, per garantire che vengano aperte in Microsoft Edge anziché in Managed Browser. 

#### <a name="additional-information"></a>Informazioni aggiuntive
Per altre informazioni vedere i documenti relativi all'[uso di Microsoft Edge con i criteri di protezione delle app](../apps/manage-microsoft-edge.md) o visualizzare il [post del blog sul supporto](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


### <a name="plan-for-change-updated-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--5198878--"></a>Modifica prevista: Nuova esperienza di registrazione dei dispositivi Android Enterprise dedicati in Intune<!--5198878-->
Con la versione di novembre o 1911 di Intune, viene aggiunto il supporto per la distribuzione del certificato dispositivo SCEP ai dispositivi Android Enterprise dedicati per abilitare l'accesso basato su certificati ai profili Wi-Fi. Questa modifica comporta anche alcune modifiche secondarie del flusso durante la registrazione dei dispositivi Android Enterprise dedicati.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se si gestiscono dispositivi Android Enterprise dedicati nell'ambiente in uso, si inizieranno a vedere alcune modifiche implementate a novembre.

- Per le nuove registrazioni di dispositivi Android Enterprise dedicati: Gli utenti finali visualizzeranno una procedura diversa nei dispositivi durante la registrazione. La registrazione continuerà a essere eseguita nello stesso modo (con QR, NFC, Zero Touch o identificatore dispositivo), ma dopo la versione del servizio di novembre sarà presente un passaggio obbligatorio per l'installazione dell'app.
- Per i dispositivi Android esistenti registrati come dispositivi dedicati: Intune avvierà l'installazione automatica dell'app Microsoft Intune nei dispositivi a partire dall'inizio di novembre. Non è necessario eseguire alcuna operazione. L'app verrà scaricata e installata automaticamente nei dispositivi. 

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
È consigliabile pianificare l'aggiornamento delle linee guida per gli utenti finali e informare il supporto tecnico di questa modifica. Fare clic su Informazioni aggiuntive per altri dettagli e schermate. La pagina delle novità verrà aggiornata quando questa modifica inizierà a essere implementata.

#### <a name="additional-information"></a>Informazioni aggiuntive
[https://aka.ms/Dedicated_devices_enrollment](https://aka.ms/Dedicated_devices_enrollment)

### <a name="plan-for-change-the-server-side-logging-for-siri-commands-setting-will-be-removed-from-the-intune-console----5468501--"></a>Modifica prevista: L'impostazione "Registrazione lato server per comandi di Siri" verrà rimossa dalla console di Intune <!-- 5468501-->

È prevista la rimozione dell'impostazione "Registrazione lato server per comandi di Siri" dalla console di Intune con l'aggiornamento di novembre del servizio Intune. Questa modifica è allineata ad Apple che ha già rimosso l'impostazione.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Quando l'aggiornamento di novembre o 1911 verrà implementato intorno a metà novembre, si noterà che questa impostazione è stata rimossa dal menu Limitazioni del dispositivo (App predefinite) per i profili di configurazione iOS nella console di Intune. Potrebbe essere presente nei criteri e nel profilo di gestione del dispositivo di destinazione, ma l'impostazione non ha alcun effetto sul dispositivo. Non è previsto un effetto rilevante sulle funzionalità poiché attualmente non funziona nei dispositivi anche se è visibile nel profilo di gestione.

È possibile scegliere una delle due opzioni seguenti:
- Se si vuole eliminare questa impostazione dai criteri, è possibile passare al profilo con questa impostazione, apportare una modifica secondaria e salvare i criteri. I criteri verranno ricalcolati nel back-end e l'impostazione verrà eliminata dai criteri.
- Se si sceglie di non eseguire questa azione, gli utenti finali visualizzeranno questa impostazione nel profilo di gestione del dispositivo, ma l'impostazione non avrà alcun effetto.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
È possibile eseguire l'azione descritta nella sezione precedente o non modificare i criteri. Quando questa modifica verrà implementata, verranno aggiornate la pagina Novità e la documentazione.

### <a name="end-of-support-for-legacy-pc-management"></a>Termine del supporto per la gestione dei PC legacy

La gestione dei PC legacy non sarà più supportata a partire dal 15 ottobre 2020. Aggiornare i dispositivi a Windows 10 e registrarli nuovamente come dispositivi MDM perché continuino a essere gestiti da Intune.

[Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Riduzione del supporto per l'amministratore di dispositivi Android 
L'amministratore di dispositivi Android, a volte denominato gestione Android "legacy" e rilasciato con Android 2.2, è una modalità di gestione dei dispositivi Android. Funzionalità di gestione migliorate, tuttavia, sono ora disponibili in [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (con la versione Android 5.0). Con l'obiettivo di passare a una gestione dei dispositivi moderna, più ricca e sicura, Google sta riducendo il supporto per l'amministratore di dispositivi nelle nuove versioni di Android.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Queste modifiche di Google influiranno sugli utenti di Intune nei modi seguenti:  
- Intune potrà offrire supporto per i dispositivi Android gestiti dall'amministratore di dispositivi che eseguono Android 10 e versioni successive (anche noto come Android Q) solo fino all'estate 2020. È in questo periodo che è previsto il rilascio della prossima versione principale di Android.   
- I dispositivi gestiti dall'amministratore di dispositivi che eseguono Android 10 o versione successiva dopo l'estate 2020 non potranno più essere gestiti interamente.       
- I dispositivi Android gestiti dall'amministratore di dispositivi che continueranno a usare versioni Android precedenti ad Android 10 non saranno interessati e potranno continuare a essere interamente gestiti con l'amministratore di dispositivi.    
- Per tutti i dispositivi con Android 10 e versioni successive, Google ha limitato la capacità degli agenti di gestione dell'amministratore di dispositivi come il Portale aziendale di accedere alle informazioni relative all'identificatore del dispositivo. Dopo l'aggiornamento di un dispositivo ad Android 10 o versione successiva, questa modifica influisce sulle funzionalità di Intune seguenti:  
    - Il controllo di accesso alla rete per la rete VPN non funzionerà più.   
    - L'identificazione dei dispositivi come di proprietà dell'azienda con l'IMEI o il numero di serie non contrassegnerà automaticamente i dispositivi come di proprietà dell'azienda.  
    - L'IMEI e il numero di serie non saranno più visibili agli amministratori IT in Intune. 
        > [!NOTE]
        > Ciò interessa solo i dispositivi gestiti dall'amministratore di dispositivi in Android 10 e versioni successive e non i dispositivi gestiti come Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Per evitare la riduzione di funzionalità prevista per l'estate 2020, è consigliabile attenersi alle indicazioni seguenti:
- Non eseguire l'onboarding di nuovi dispositivi nella gestione di tipo amministratore di dispositivi.
- Se si prevede che un dispositivo riceverà un aggiornamento ad Android 10, eseguirne la migrazione dalla gestione di tipo amministratore di dispositivi alla gestione Android Enterprise e/o ai criteri di protezione delle app.

#### <a name="additional-information"></a>Informazioni aggiuntive
- [Indicazioni di Google per la migrazione da amministratore di dispositivi ad Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentazione di Google sul piano per deprecare l'API amministratore di dispositivi](https://developers.google.com/android/work/device-admin-deprecation)

### <a name="update-your-android-company-portal-app-to-the-latest-version---4536963--"></a>Aggiornare l'app Portale aziendale per Android alla versione più recente <!--4536963-->
Intune rilascia periodicamente aggiornamenti per l'app Portale aziendale per Android. Nel mese di novembre 2018 è stato rilasciato un aggiornamento del portale aziendale, che comprendeva un'opzione di back-end per prepararsi per la modifica di Google dalla piattaforma di notifica esistente a Firebase Cloud Messaging (FCM). Quando Google ritirerà la piattaforma di notifica esistente e passerà a FCM, gli utenti finali dovranno avere aggiornato l'app Portale aziendale almeno alla versione di novembre 2018 per poter continuare a comunicare con Google Play Store.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
I dati di telemetria indicano che esistono dispositivi con una versione dell'app Portale aziendale precedente a 5.0.4269.0. Se non sono installate questa versione o versioni successive dell'app Portale aziendale, le azioni per i dispositivi avviate da professionisti IT come la cancellazione, la reimpostazione della password, l'installazione delle app disponibili e richieste e la registrazione del certificato potrebbero non funzionare come previsto. Se i dispositivi sono registrati nella soluzione MDM di Intune, è possibile visualizzare le versioni e gli utenti dell'app Portale aziendale passando ad App client - App individuate. La selezione di versioni precedenti dell'app Portale aziendale consentirà di vedere quali utenti finali hanno i dispositivi in cui non è stata aggiornata l'app Portale aziendale.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Chiedere agli utenti finali dei dispositivi Android che non sono aggiornati di aggiornare l'app Portale aziendale tramite Google Play. Inviare notifica all'help desk nel caso un utente non abbia mantenuto l'aggiornamento automatico dell'app Portale aziendale. Vedere il collegamento in *Informazioni aggiuntive* per altre informazioni sulla piattaforma FCM di Google e su questa modifica.

#### <a name="additional-information"></a>Informazioni aggiuntive
https://firebase.google.com/docs/cloud-messaging/


### <a name="new-full-screen-experience-coming-to-intune---4593669--"></a>Nuova esperienza a schermo intero presto disponibile in Intune <!--4593669-->
È in corso l'implementazione di esperienze aggiornate dell'interfaccia utente per la creazione e la modifica in Intune nel portale di Azure. Questa nuova esperienza consentirà di semplificare i flussi di lavoro esistenti usando un formato in stile procedura guidata sintetizzato in un solo pannello. Con questo aggiornamento scompariranno la distesa di pannelli o tutti i flussi di lavoro di creazione e modifica che richiedono il drill-down in lunghe sequenze di pannelli annidati. I flussi di lavoro di creazione verranno aggiornati anche per includere le assegnazioni, ad eccezione dell'assegnazione di app.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
L'esperienza a schermo intero verrà implementata in Intune sia in portal.azure.com che in devicemanagement.microsoft.com nei prossimi mesi. Questo aggiornamento dell'interfaccia utente non avrà impatto sulle funzionalità dei criteri e dei profili esistenti, ma si noteranno leggere modifiche del flusso di lavoro. Quando si creano nuovi criteri, ad esempio, sarà possibile impostare alcune assegnazioni nell'ambito di questo flusso anziché dopo aver creato i criteri. Vedere il post di blog in *Informazioni aggiuntive* per visualizzare alcuni screenshot dell'aspetto della nuova esperienza nella console.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Non è necessario intraprendere alcuna azione, ma è possibile valutare la necessità di aggiornare le istruzioni per i professionisti IT. La documentazione verrà aggiornata non appena questa esperienza verrà implementata nei vari pannelli in Intune nel portale di Azure.

#### <a name="additional-information"></a>Informazioni aggiuntive 
https://aka.ms/intune_fullscreen

### <a name="plan-for-change-intune-app-sdk-and-app-protection-policies-for-android-moving-to-support-android-50-and-higher-in-an-upcoming-release---4911065---"></a>Modifica prevista: Intune App SDK e i criteri di protezione delle app per Android includeranno il supporto per Android 5.0 e versioni successive in una versione futura <!--4911065 -->
Intune includerà il supporto per Android 5.x (Lollipop) e versioni successive in una versione futura. Aggiornare le app con wrapping con la versione più recente di Intune App SDK e aggiornare i dispositivi.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Questa modifica non interessa coloro che non usano o non prevedono di usare l'SDK o i criteri di protezione delle app per Android. Coloro che usano Intune App SDK devono invece assicurarsi di eseguire l'aggiornamento alla versione più recente e anche di aggiornare i dispositivi alla versione Android 5.x e successive. Se l'aggiornamento non viene eseguito, le app non riceveranno gli aggiornamenti e la qualità dell'esperienza d'uso andrà nel tempo a deteriorarsi.

Di seguito è riportato un elenco di dispositivi comuni registrati in Intune che eseguono Android versione 4.x. Se si è in possesso di uno di questi dispositivi, adottare le misure appropriate per assicurarsi che il dispositivo supporterà Android versione 5.0 o successive oppure che sarà sostituito da un dispositivo che supporta Android versione 5.0 o successive. L'elenco non è esaustivo di tutti i dispositivi che potrebbe essere necessario valutare:

- Samsung SM-T561  
- Samsung SM-T365
- Samsung GT-I9195
- Samsung SM-G800F
- Samsung SM-G357FZ
- Motorola XT1080
- Samsung GT-I9305
- Samsung SM-T231

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Eseguire il wrapping delle app con la versione più recente di Intune App SDK. È anche possibile configurare l'impostazione di avvio condizionale "Richiedi una versione minima del sistema operativo (solo avviso)" in modo da informare gli utenti finali sui dispositivi personali da aggiornare.

### <a name="intune-plan-for-change-nearing-end-of-support-for-windows-7---3042987---"></a>Modifica prevista per Intune: fine del supporto per Windows 7<!-- 3042987 -->
Come indicato nelle comunicazioni MC148476, pubblicata nel settembre 2018, e MC176794 del marzo 2019, si avvicina la fine del supporto esteso per Windows 7, prevista per il 14 gennaio 2020. In tale data Intune ritirerà il supporto per i dispositivi che eseguono Windows 7, per concentrare gli investimenti sul supporto di tecnologie più recenti e offrire esperienze nuove e ottimali agli utenti finali. Dopo tale data l'assistenza tecnica e gli aggiornamenti automatici che consentono di proteggere i PC con Windows 7 non saranno più disponibili tramite Intune. Microsoft consiglia vivamente di passare a Windows 10 prima di gennaio 2020, per evitare uno scenario in cui un servizio o un supporto necessario non è più disponibile. Altre informazioni sul ciclo di vita di supporto di Windows sono disponibili [qui](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Questo messaggio viene ricevuto quando si gestiscono PC Windows 7 con l'agente software per PC Intune legacy. Dato che manca meno di un anno alla fine del supporto esteso di Windows 7, è vivamente consigliabile che l'organizzazione inizi l'aggiornamento a Windows 10 prima possibile.  

Le funzionalità di gestione dei PC sono incorporate direttamente nel sistema operativo Windows 10 e non è più necessario installare un agente client come il client software Intune per Windows 7. A partire da Windows 8.1 Microsoft usa l'architettura di gestione di dispositivi mobili (MDM) per eseguire il provisioning, la configurazione, l'aggiornamento e la gestione dei PC Windows. Dopo aver configurato Intune, è possibile semplificare la registrazione Windows [registrando i PC Windows 10 in Intune](..\windows-enroll.md) tramite il canale MDM. È consigliabile usare questa soluzione di gestione MDM "senza agente" per gestire i PC Windows 10.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
È consigliabile che l'organizzazione consideri immediatamente questo piano di azione:

- Pianificare e aggiornare i computer con Windows 7 a Windows 10 prima del 14 gennaio 2020.
- Per altre informazioni su come aggiornare i PC con Windows 7 a Windows 10, vedere la pagina di[ supporto della distribuzione di Windows 10](https://docs.microsoft.com/windows/deployment/).
- Esaminare l'offerta [Desktop App Assure](https://www.microsoft.com/fasttrack/microsoft-365/desktop-app-assure?rtc=1) tramite FastTrack, che supporta la promessa di compatibilità delle applicazioni Microsoft.
- Eseguire la transizione dei dispositivi gestiti da client software di Intune legacy esistenti alla soluzione Microsoft consigliata per gestire Windows 10 con MDM. Registrare tutti i nuovi PC Windows 10 usando la gestione MDM per Intune nel portale di Azure.

Per altre informazioni, vedere [questo post di blog](https://aka.ms/Windows7_Intune).
