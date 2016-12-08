---
title: Edizione anticipata | Microsoft Intune
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/30/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6dd584397451d38be86fa0780efff435ffb9b2af
ms.openlocfilehash: d70ebf87bc930f853741ddc0d572d2174c636dac


---

# <a name="the-early-edition-for-microsoft-intune---december"></a>Edizione anticipata per Microsoft Intune - Dicembre

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

<!--736542-->
## <a name="public-preview-of-the-new-intune-admin-experience-on-azure"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la nuova documentazione.

Per qualsiasi domanda in merito alla tempistica per la migrazione del tenant, contattare il team Microsoft responsabile della migrazione all'indirizzo [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integrazione della gestione delle spese di telecomunicazione nell'anteprima pubblica del portale di Azure<!--747605-->
Stiamo iniziando a presentare in anteprima l'integrazione con i servizi di gestione delle spese di telecomunicazione di terze parti nel portale di Azure. È possibile usare Intune per imporre limiti al consumo dei dati sia nazionale che in roaming. Queste integrazioni iniziano con [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Autenticazione a più fattori su tutte le piattaforme <!--747590-->
È ora possibile imporre l'autenticazione a più fattori (MFA) per un gruppo selezionato di utenti durante la registrazione di un dispositivo iOS, Android, Windows 8.1+ o Windows Phone 8.1+ dal portale di gestione di Azure configurando MFA nell'applicazione di registrazione di Microsoft Intune in Azure Active Directory.

### <a name="conditional-access-for-mam-with-sharepoint-online---vso-679339--"></a>Accesso condizionale per MAM con SharePoint Online <!--VSO 679339-->
È possibile impedire l'accesso a SharePoint Online alle app non supportate dai criteri di gestione delle app mobili (MAM) di Intune.  È possibile iniziare a usare le funzionalità di gestione delle app mobili di Intune nel portale di Azure. Individuare la sezione __Accesso condizionale__ nel pannello __Impostazioni__ che includerà l'opzione per SharePoint Online. Questa funzionalità verrà fornita separatamente rispetto al resto del rilascio del servizio.

### <a name="ability-to-restrict-intune-mobile-device-enrollment"></a>Possibilità di limitare la registrazione di dispositivi mobili Intune
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile. 
* È possibile limitare la registrazione di macOS e Windows 8.1 o versioni successive come piattaforme per dispositivi mobili. 
* La limitazione della registrazione di dispositivi mobili non limita la registrazione di agenti PC. 
* Solo per iOS: è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali. Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).


## <a name="notices"></a>Notifiche

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Trasferimento di Multi-Factor Authentication per la registrazione nel portale di Azure <!--VSO 750545-->
Per impostare MFA per le registrazioni in Intune, gli amministratori dovevano usare in precedenza la console di Intune o Configuration Manager (prima della versione 1610). Con questa funzionalità aggiornata è ora possibile accedere al [portale di Microsoft Azure](https://manage.windowsazure.com) con le credenziali di Intune e configurare le impostazioni di MFA tramite Azure AD. Per altre informazioni a questo proposito, vedere [qui](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china---vso-658093--"></a>L'app Portale aziendale per Android è ora disponibile in Cina <!--VSO 658093-->
L'app Portale aziendale per Android sta per essere pubblicata per il download in Cina. A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere l'app dai marketplace di app cinesi. L'app Portale aziendale per Android sarà disponibile per il download nei dispositivi 360, Tencent, Xiaomi, Wandoujia e Huawei. 

L'app Portale aziendale per Android usa i servizi Google Play per comunicare con il servizio Microsoft Intune. Dato che i servizi Google Play non sono ancora disponibili in Cina, per completare qualsiasi attività tra le seguenti possono essere richieste fino a 8 ore. 

|Console di amministrazione di Intune| App Portale aziendale di Intune per Android |Sito Web del portale aziendale di Intune|   
|---|---|---|
|Cancellazione completa| Rimozione di un dispositivo remoto| Rimozione di un dispositivo (locale e remoto)|
|Cancellazione selettiva| Reimpostazione del dispositivo| Reimpostazione del dispositivo|
|Distribuzioni di app nuove o aggiornate| Installazione delle app line-of-business disponibili| Reimpostazione del passcode del dispositivo|
|Blocco remoto|||
|Reimpostazione del passcode|||

## <a name="deprecations"></a>Elementi deprecati

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Rimozione del criteri per le cassette postali per dispositivi portatili di Exchange Online <!--770687-->
A partire da dicembre, gli amministratori non potranno più visualizzare o configurare i criteri per le cassette postali per dispositivi portatili di Exchange Online (EAS) all'interno della console di Intune. Questa modifica verrà distribuita in tutti i tenant di Intune nel corso di dicembre e gennaio. La configurazione di tutti i criteri esistenti rimarrà invariata. Per la configurazione dei nuovi criteri, usare Exchange Management Shell. Altre informazioni sono disponibili [qui](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Le app Intune AV Player, Image Viewer e PDF Viewer non sono più supportate in Android <!--747553-->
A partire dalla metà di dicembre 2016, gli utenti non potranno più usare le app Intune AV Player, Image Viewer e PDF Viewer. Queste app sono state sostituite dall'app Azure Information Protection. È possibile trovare altre informazioni sull'app Azure Information Protection [qui](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Nov16_HO5-->


