---
title: includere il file
description: Includere file
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: e745290991da4d80c7e3839250edbfdd64ef1b7a
ms.sourcegitcommit: 01c57ac880dcb5f474908977c89810f5bedaf326
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75760968"
---
Questi avvisi forniscono importanti informazioni utili per prepararsi per le modifiche e le funzionalità di Intune future.

### <a name="updated-feature-new-rbac-role-coming-to-intune--4253397--"></a>Funzionalità aggiornata: Nuovo ruolo del controllo degli accessi in base al ruolo in Intune<!--4253397-->
Nell'aggiornamento del servizio Intune di gennaio è previsto il rilascio di un nuovo ruolo di sicurezza in Intune. Questo ruolo verrà elencato come "Endpoint Security Manager" (Gestore sicurezza endpoint) in Intune ed è un'espansione del ruolo "Amministratore della sicurezza" di Azure Active Directory.
 
#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Attualmente in Azure Active Directory sono disponibili tre ruoli per i professionisti della sicurezza:
- Ruolo con autorizzazioni di lettura per la sicurezza in Azure AD che consente l'accesso in sola lettura a Intune.
- Ruolo Operatore per la sicurezza in Azure AD che consente l'accesso in sola lettura a Intune.
- Amministratore della sicurezza in Azure AD. Nell'aggiornamento di gennaio di Intune, oltre alle autorizzazioni di sola lettura per Intune, le nuove autorizzazioni incluse nel ruolo Endpoint Security Manager (Gestione sicurezza endpoint) sono le seguenti:
    - Read, Create, Update, Delete, and Assign Device Compliance Policies (Lettura, Creazione, Aggiornamento, Eliminazione e Assegnazione di criteri di conformità del dispositivo)
    - Read, Delete, and Update Managed devices (Lettura, Eliminazione e Aggiornamento di dispositivi gestiti)
    - Read, Create, Update, Delete, and Assign Security baselines (Lettura, Creazione, Aggiornamento, Eliminazione e Assegnazione di baseline di sicurezza)
    - Read and Update Security tasks (Lettura e Aggiornamento delle attività di sicurezza)
 
### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Esaminare oggi stesso i ruoli di controllo degli accessi in base al ruolo di Intune. Se al momento l'unico ruolo disponibile è Amministratori globali, non sono necessarie modifiche. Se si usano i ruoli e si vuole disporre della granularità offerta da Endpoint Security Manager (Gestore sicurezza endpoint), assegnare tale ruolo quando diventa disponibile. Per informazioni aggiornate sulla versione di Intune, vedere la pagina [Novità](../fundamentals/whats-new.md) di Intune. 

### <a name="updated-support-statement-for-adobe-acrobat-reader-for-intune-mobile-app--5746776--"></a>È stata aggiornata l'informativa di supporto per l'app per dispositivi mobili 'Adobe Acrobat Reader per Intune'<!--5746776-->
Nel documento MC188653 della fine di agosto è stato comunicato che l'app per dispositivi mobili Adobe Acrobat Reader per Intune stava avvicinandosi alla scadenza dell'1 dicembre 2019 e che Adobe prevedeva di includere il supporto dei criteri di protezione delle app di Intune all'interno dell'app Acrobat Reader principale. Da allora, abbiamo ricevuto il feedback dei clienti che richiedeva più tempo per continuare a consentire agli amministratori IT di impostare l'app come destinazione e agli utenti finali di iniziare a usare Adobe Acrobat Reader per Intune. Considerato l'utilizzo elevato di Adobe Acrobat Reader per Intune nei dispositivi degli utenti finali e la sua importanza negli scenari aziendali, vogliamo assicurarci che qualsiasi esperienza soddisfi le esigenze di protezione delle app dell'organizzazione. 

Sebbene sia ancora consigliabile impostare come destinazione l'app per dispositivi mobili Acrobat Reader generale nei criteri poiché l'app per dispositivi mobili Acrobat Reader supporta i criteri di protezione delle app e include l'SDK Intune integrato, l'app Adobe Acrobat Reader per Intune continuerà a essere supportata fino al 31 marzo 2020. 

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Si riceve questo messaggio poiché risulta che uno o più criteri dell'organizzazione includono come destinazione l'applicazione Adobe Acrobat Reader per Intune e/o si potrebbe aver ricevuto la comunicazione EOL precedente. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Informare gli utenti finali e il supporto tecnico di questa modifica. È possibile usare la [funzionalità delle informazioni sul supporto del Portale aziendale](../apps/company-portal-app.md#support-information) per stabilire un canale per le domande correlate a Intune.

#### <a name="additional-information"></a>Informazioni aggiuntive
https://helpx.adobe.com/acrobat/kb/intune-app-end-of-life.html


### <a name="end-support-for-windows-phone-81--3544909--"></a>Supporto terminato per Windows Phone 8.1<!--3544909-->
Il supporto Mainstream di Microsoft per Windows Phone 8.1 è terminato a luglio 2017 e il supporto "Extended" è terminato a giugno 2019. L'app Portale aziendale per Windows Phone 8.1 è inattiva da ottobre 2017. Microsoft Intune terminerà ora il supporto per Windows Phone 8.1 il 20 febbraio 2020.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Dopo il 20 febbraio 2020 questi dispositivi non riceveranno aggiornamenti della sicurezza e non sarà possibile registrare nuovi dispositivi. I dispositivi Windows Phone 8.1 esistenti rimarranno registrati (criteri, app, reporting). Si noti però che dopo tale data non sarà supportata la risoluzione dei problemi di una registrazione esistente, poiché molti componenti, ad esempio i certificati di terze parti, hanno già terminato il supporto per la piattaforma. Intune interromperà i test di compatibilità con Intune e Windows Phone 8.1.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
È possibile controllare i report di Intune per vedere quali dispositivi o utenti potrebbero essere interessati. Andare a Dispositivi > Tutti i dispositivi e filtrare in base al sistema operativo. È possibile aggiungere altre colonne per facilitare l'identificazione degli utenti dell'organizzazione che hanno dispositivi che eseguono Windows Phone 8.1. Richiedere agli utenti finali di aggiornare i dispositivi a una versione supportata del sistema operativo.


### <a name="take-action-use-microsoft-edge-for-your-protected-intune-browser-experience--5728447--"></a>Azione: Usare Microsoft Edge per l'esperienza protetta del browser di Intune<!--5728447-->
Come descritto nel corso dell'ultimo anno, Microsoft Edge per dispositivi mobili supporta la stessa gamma di funzionalità di gestione supportata da Managed Browser, ma garantisce un'esperienza utente molto migliore. Per lasciare spazio alle esperienze consolidate offerte da Microsoft Edge, Intune Managed Browser verrà ritirato. A partire dal 27 gennaio 2020 Intune non supporterà più Intune Managed Browser.  

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica? 
A partire dal 1 febbraio 2020 Intune Managed Browser non sarà più disponibile in Google Play Store o nell'App Store iOS. Dopo tale data sarà ancora possibile indirizzare i nuovi criteri di protezione delle app a Intune Managed Browser, ma i nuovi utenti non potranno più scaricare l'app Intune Managed Browser. Inoltre in iOS le nuove clip Web che vengono distribuite a dispositivi registrati in MDM verranno aperte in Microsoft Edge anziché in Intune Managed Browser.  

Il 31 marzo 2020 Intune Managed Browser verrà rimosso dalla console di Azure. Di conseguenza non sarà più possibile creare nuovi criteri per Intune Managed Browser. I criteri di Intune Managed Browser già implementati non subiranno variazioni. Intune Managed Browser verrà visualizzato nella console come applicazione line-of-business senza icone e i criteri esistenti continueranno ad apparire come associati all'app. Verrà anche rimossa l'opzione per reindirizzare il contenuto Web a Intune Managed Browser nel contesto della sezione Protezione dei dati dei criteri di protezione delle app.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica 
Per garantire una transizione ottimale da Intune Managed Browser a Microsoft Edge è consigliabile adottare le seguenti misure con il necessario anticipo: 

1. Impostare Microsoft Edge per iOS e Android come destinazione per i criteri di protezione delle app (detti anche MAM) e le impostazioni di configurazione delle app. Per riusare i criteri di Intune Managed Browser per Microsoft Edge, impostare anche Microsoft Edge come destinazione dei criteri esistenti.  
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

### <a name="end-of-support-for-legacy-pc-management"></a>Termine del supporto per la gestione dei PC legacy

La gestione dei PC legacy non sarà più supportata a partire dal 15 ottobre 2020. Aggiornare i dispositivi a Windows 10 e registrarli nuovamente come dispositivi MDM perché continuino a essere gestiti da Intune.

[Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2107122)

### <a name="decreasing-support-for-android-device-administrator"></a>Riduzione del supporto per l'amministratore di dispositivi Android 
L'amministratore di dispositivi Android, a volte denominato gestione Android "legacy" e rilasciato con Android 2.2, è una modalità di gestione dei dispositivi Android. Funzionalità di gestione migliorate, tuttavia, sono ora disponibili in [Android Enterprise](../enrollment/connect-intune-android-enterprise.md) (con la versione Android 5.0). Con l'obiettivo di passare a una gestione dei dispositivi moderna, più ricca e sicura, Google sta riducendo il supporto per l'amministratore di dispositivi nelle nuove versioni di Android.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Queste modifiche di Google influiranno sugli utenti di Intune nei modi seguenti:  
- Intune potrà offrire supporto completo per i dispositivi Android gestiti dall'amministratore di dispositivi che eseguono Android 10 e versioni successive solo fino al secondo trimestre del 2020. I dispositivi gestiti dall'amministratore di dispositivi che eseguono Android 10 o versione successiva in seguito non potranno più essere gestiti interamente. In particolare, i dispositivi interessati non riceveranno nuovi requisiti per le password.
    - I dispositivi Samsung Knox non saranno interessati in questo intervallo di tempo perché viene fornito il supporto esteso tramite l'integrazione di Intune con la piattaforma Knox. In questo modo si ottiene più tempo per pianificare la transizione dalla gestione dei dispositivi da parte dell'amministratore.    
- I dispositivi Android gestiti dall'amministratore di dispositivi che continueranno a usare versioni di Android precedenti ad Android 10 non saranno interessati e potranno continuare a essere interamente gestiti con l'amministratore di dispositivi.    
- Per tutti i dispositivi con Android 10 e versioni successive, Google ha limitato la capacità degli agenti di gestione dell'amministratore di dispositivi come il Portale aziendale di accedere alle informazioni relative all'identificatore del dispositivo. Dopo l'aggiornamento di un dispositivo ad Android 10 o versione successiva, questa limitazione influisce sulle funzionalità di Intune seguenti:  
    - Il controllo di accesso alla rete per la rete VPN non funzionerà più.   
    - L'identificazione dei dispositivi come di proprietà dell'azienda con l'IMEI o il numero di serie non contrassegnerà automaticamente i dispositivi come di proprietà dell'azienda.  
    - L'IMEI e il numero di serie non saranno più visibili agli amministratori IT in Intune. 
        > [!NOTE]
        > Ciò interessa solo i dispositivi gestiti dall'amministratore di dispositivi in Android 10 e versioni successive e non i dispositivi gestiti come Android Enterprise. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Per evitare la riduzione di funzionalità prevista per il terzo trimestre del 2020, è consigliabile attenersi alle indicazioni seguenti:
- Non eseguire l'onboarding di nuovi dispositivi nella gestione di tipo amministratore di dispositivi.
- Se si prevede che un dispositivo riceverà un aggiornamento ad Android 10, eseguirne la migrazione dalla gestione di tipo amministratore di dispositivi alla gestione Android Enterprise e/o ai criteri di protezione delle app.

#### <a name="additional-information"></a>Informazioni aggiuntive
- [Indicazioni di Google per la migrazione da amministratore di dispositivi ad Android Enterprise](http://static.googleusercontent.com/media/android.com/en/enterprise/static/2016/pdfs/enterprise/Android-Enterprise-Migration-Bluebook_2019.pdf)
- [Documentazione di Google sul piano per deprecare l'API amministratore di dispositivi](https://developers.google.com/android/work/device-admin-deprecation)

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


