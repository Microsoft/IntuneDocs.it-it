---
title: includere il file
description: includere il file
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/4/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: edef1f43caff97ab75aa3c58034ed4fc2dffd208
ms.sourcegitcommit: ae6f2e7812e7fd36f2393b8f4b6cd8de63777b2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2019
ms.locfileid: "73612090"
---
Questi avvisi forniscono importanti informazioni utili per prepararsi per le modifiche e le funzionalità di Intune future.

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

Si prevede di rimuovere l'impostazione "Registrazione lato server per comandi di Siri" dalla console di Intune con l'aggiornamento di novembre del servizio Intune. Questa modifica è allineata ad Apple che ha già rimosso l'impostazione.

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
