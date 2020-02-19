---
title: includere il file
description: Includere file
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 11/19/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: d360fa5efe2deba2d19cd67e6ed9f8cbb7f864d9
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415083"
---
Questi avvisi forniscono importanti informazioni utili per prepararsi per le modifiche e le funzionalità di Intune future.

### <a name="plan-for-change-change-in-experience-when-enrolling-android-enterprise-dedicated-devices-in-intune--6114580--"></a>Modifica prevista: Modifica nell'esperienza di registrazione dei dispositivi Android Enterprise dedicati in Intune<!--6114580-->
Con la versione di novembre abbiamo comunicato l'aggiunta del supporto per la distribuzione del certificato dispositivo SCEP ai dispositivi Android Enterprise dedicati per abilitare l'accesso basato su certificati ai profili Wi-Fi. Questa modifica ha comportato alcune modifiche secondarie del flusso di registrazione per i dispositivi Android Enterprise dedicati. Con l'imminente aggiornamento del servizio di marzo o 2003, sono presenti altre modifiche di cui è necessario essere al corrente.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se si gestiscono dispositivi Android Enterprise dedicati nell'ambiente in uso, si inizieranno a vedere alcune modifiche implementate a marzo.
- Per i dispositivi Android dedicati esistenti registrati prima dell'aggiornamento del servizio del 22 novembre 2019 o 1911: In questi dispositivi è installata l'app Microsoft Intune. Dopo la distribuzione delle modifiche back-end nel servizio Intune a marzo, inizieranno a essere applicati i certificati SCEP distribuiti ai dispositivi e associati ai profili Wi-Fi.
- Per i dispositivi registrati dopo il 22 novembre 2019 e prima dell'implementazione di questa modifica a marzo: In questi dispositivi è installata l'app Microsoft Intune. I certificati SCEP distribuiti ai dispositivi e associati ai profili Wi-Fi continueranno a essere applicati.
- Per le nuove registrazioni di dispositivi Android Enterprise dedicati dopo la distribuzione delle modifiche a marzo: Gli utenti finali visualizzeranno una procedura diversa nei dispositivi durante la registrazione. La registrazione continuerà a essere eseguita nello stesso modo (con QR, NFC, Zero Touch o identificatore dispositivo), ma non sarà presente alcun passaggio obbligatorio per l'installazione dell'app. L'app Microsoft Intune verrà invece installata automaticamente nei dispositivi. Gli utenti finali non dovranno toccare "Enable Intune Agent" (Abilita agente di Intune) durante il flusso. I certificati SCEP associati ai profili Wi-Fi possono essere distribuiti a questi dispositivi.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
È possibile eseguire l'aggiornamento delle linee guida per gli utenti finali e informare il supporto tecnico di questa modifica. La pagina Novità verrà aggiornata e verrà inviata una notifica tramite il Centro messaggi quando questa modifica inizierà a essere implementata.

#### <a name="additional-information"></a>Informazioni aggiuntive
[Supporto per i certificati SCEP nei dispositivi Android Enterprise dedicati](https://aka.ms/Dedicated_devices_enrollment)

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
Dopo il 20 febbraio 2020 questi dispositivi non riceveranno aggiornamenti della sicurezza e non sarà possibile registrare nuovi dispositivi. I dispositivi Windows Phone 8.1 esistenti rimarranno registrati (criteri, app, report). Si noti però che dopo tale data non sarà supportata la risoluzione dei problemi di una registrazione esistente, poiché per molti componenti, ad esempio i certificati di terze parti, è già terminato il supporto per la piattaforma. Intune interromperà i test di compatibilità con Intune e Windows Phone 8.1.

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
Per altre informazioni vedere la documentazione relativa all'[uso di Microsoft Edge con i criteri di protezione delle app](../apps/manage-microsoft-edge.md) o visualizzare il [post del blog sul supporto](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Use-Microsoft-Edge-for-your-Protected-Intune-Browser-Experience/ba-p/1004269).


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


