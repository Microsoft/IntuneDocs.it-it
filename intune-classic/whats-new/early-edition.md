---
title: Edizione anticipata | Microsoft Docs
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 249a902e6e10f799dcff4e1c46da90cd62f2c125
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="the-early-edition-for-microsoft-intune---may-2017"></a>Edizione anticipata per Microsoft Intune - Maggio 2017

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
> Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Supporto Single Sign-On dal portale aziendale per IOS ad Outlook per iOS <!--834012-->

Gli utenti non dovranno più eseguire l'accesso all'app Outlook se sono già connessi all'app Portale aziendale per iOS sullo stesso dispositivo con lo stesso account. Quando gli utenti avviano l'app di Outlook, potranno selezionare il loro account e accedere automaticamente. Si prevede di aggiungere questa funzionalità anche per altre app Microsoft.

### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notifica migliorata per i PIN di avvio Samsung KNOX <!--1087143-->

Quando gli utenti finali devono impostare un PIN di avvio su dispositivi Samsung KNOX per garantire la conformità alla crittografia, toccando la notifica visualizzata, gli utenti finali verranno indirizzati alla posizione esatta nell'app Impostazioni.  In precedenza, la notifica rimandava gli utenti finali alla schermata di modifica della password.

### <a name="promoting-the-most-current-version-of-the-company-portal-for-android---1098661--"></a>Richiesta della versione più recente del Portale aziendale per Android <!--1098661-->

Gli utenti finali visualizzeranno una notifica in-app quando viene rilasciata una nuova versione consigliata dell'app Portale aziendale per Android, nella schermata Notifiche dell'app. Questa notifica indicherà agli utenti che è disponibile un aggiornamento del Portale aziendale. Toccando la notifica verrà aperta una pagina Web con l'elenco di App Store disponibili dove è possibile scaricare la versione aggiornata. 

### <a name="improvements-to-app-syncing-with-windows-10-creators-update----676505---"></a>Miglioramenti alla sincronizzazione di app con Windows 10 Creators Update <!-- 676505 -->

Il Portale aziendale per Windows 10 avvierà automaticamente una sincronizzazione per le richieste di installazione di app per dispositivi con Windows 10 Creators Update (1704). Ciò consente di limitare il problema di installazione di app quando lo stato è "In attesa di sincronizzazione". Gli utenti potranno inoltre avviare manualmente la sincronizzazione dall'app. 

Il Portale aziendale per Windows 10 esporrà anche un pulsante di aggiornamento per consentire all'utente di aggiornare il contenuto nell'app in qualsiasi momento. 

## <a name="notices"></a>Notifiche

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->

A partire dalla primavera 2017, Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->

Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di anteprima di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Sviluppi futuri per Appx in Intune in Azure <!-- 1000270 -->

Nell'ambito della migrazione a Intune in Azure, saranno apportate tre modifiche alle app appx:

1. Aggiunta di un nuovo tipo di app appx nella console di Intune classica distribuibile solo a dispositivi registrati MDM.
2. Reimpiego del tipo di app appx esistente per essere destinata solo a PC gestiti tramite l'agente PC di Intune.
3. Conversione di tutte le app appx esistenti in app appx MDM con la migrazione.

Questa modifica non avrà alcun impatto sulle distribuzioni esistenti ai dispositivi gestiti tramite l'agente PC di Intune. Tuttavia, dopo la migrazione, non sarà più possibile distribuire queste app appx migrate a eventuali nuovi dispositivi gestiti tramite l'agente PC di Intune che non siano stati previsti in precedenza.

Dopo la migrazione, sarà necessario caricare nuovamente l'app appx come app appx per PC se si vuole procedere a nuove distribuzioni su PC. Per altre informazioni, vedere [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Modifiche ad Appx in Intune in Azure) nel blog del team di supporto Intune.  


## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/intune/what-is-intune).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Supporto per le opzioni di configurazione gestita per le app Android <!-- 621621 -->

Sarà possibile configurare app Android nel Play Store che supportano le opzioni di configurazione gestita.  Questa funzionalità consente di visualizzare l'elenco dei valori di configurazione supportati da un'app e fornisce un'interfaccia utente guidata avanzata per la configurazione di tali valori.

### <a name="remote-assistance-for-android-devices----675418---"></a>Assistenza remota per i dispositivi Android <!-- 675418 -->

Intune userà il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per consentire agli amministratori di offrire assistenza remota agli utenti che eseguono dispositivi Android.

### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Preconfigurazione delle autorizzazioni dei dispositivi per le app Android for Work <!-- 621614 -->

Per le app distribuite in profili di lavoro di dispositivi Android For Work, sarà possibile configurare lo stato delle autorizzazioni per le singole app. Per impostazione predefinita, le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiederanno agli utenti di accettare o rifiutare le autorizzazioni.  Se ad esempio un'app usa il microfono del dispositivo, all'utente finale viene chiesto di concedere all'app l'autorizzazione per l'uso del microfono. Questa funzionalità consentirà di definire le autorizzazioni per conto dell'utente finale.  L'amministratore può configurare le autorizzazioni per:

- Rifiutare automaticamente l'autorizzazione senza avvisare l'utente
- Approvare automaticamente l'autorizzazione senza avvisare l'utente
- Chiedere all'utente di accettare o rifiutare

### <a name="define-app-specific-pin-for-android-for-work-devices---728976--"></a>Definizione del PIN specifico dell'app per i dispositivi Android for Work <!--728976-->

Sarà possibile definire criteri di passcode che si applicano solo alle app nel profilo di lavoro per i dispositivi Android 7.0 e versioni successive gestiti come dispositivo Android for Work.  Le opzioni includono:

- Definire solo criteri di passcode a livello di dispositivo: si tratta del passcode che l'utente finale deve usare per sbloccare l'intero dispositivo.
- Definire solo criteri di passcode del profilo di lavoro: agli utenti finali verrà chiesto di immettere un passcode ogni volta che viene aperta un'app nel profilo di lavoro.
- Definire criteri sia del dispositivo che del profilo di lavoro: il personale IT può scegliere di definire sia criteri di passcode del dispositivo che criteri di passcode del profilo di lavoro con complessità diverse (ad esempio, un PIN di 4 cifre per sbloccare il dispositivo, ma un PIN di 6 cifre per aprire un'app di lavoro).

>[!NOTE]
> Questa funzionalità sarà disponibile solo in Android 7.0 e versioni successive.  Per impostazione predefinita, l'utente finale avrà la possibilità di usare i due PIN definiti separatamente oppure di scegliere di combinare i due PIN definiti in quello più complesso.

### <a name="manage-password-and-other-android-for-work-settings---1102534--"></a>Gestione delle impostazioni delle password e di altre impostazioni di Android for Work <!--1102534-->

Verranno aggiunti nuovi criteri di restrizione dei dispositivi Android for Work che consentono di gestire le impostazioni delle password e dei profili di lavoro nei dispositivi Android for Work.

###  <a name="new-web-content-filter-policy-for-ios-devices----723832---"></a>Nuovi criteri di filtro dei contenuti Web per dispositivi iOS <!-- 723832 -->

Sarà possibile controllare i siti Web che gli utenti di dispositivi iOS possono visitare tramite uno dei due metodi seguenti:

  - Aggiungere URL consentiti e bloccati tramite il filtro predefinito dei contenuti Web di Apple.
  - Consentire l'accesso dal browser Safari solo ai siti Web specificati. Per ogni sito specificato verrà creato il segnalibro corrispondente in Safari.

### <a name="apple-school-manager-asm-support---748864--"></a>Supporto di Apple School Manager (ASM) <!--748864-->

Intune supporterà l'uso di Apple School Manager (ASM) al posto di Apple Device Enrollment Program per fornire funzionalità di registrazione pronte all'uso per i dispositivi iOS. L'onboarding di ASM è necessario usare l'app Classroom per iPad condivisi e per consentire la sincronizzazione dei dati da ASM ad Azure Active Directory tramite Microsoft School Data Sync (SDS).  

### <a name="shared-ipad-support---770395-1044681---"></a>Supporto di iPad condivisi <!--770395, 1044681 -->

Intune supporterà la configurazione in modalità iPad condiviso nel profilo di registrazione per Apple Device Enrollment Program o Apple School Manager. Questa impostazione consente l'accesso di più ID Apple gestiti allo stesso dispositivo.

Verrà inoltre espanso il supporto per la gestione dell'app iOS Classroom per includere gli studenti che accedono agli iPad condivisi usando il proprio ID Apple gestito.

### <a name="new-windows-device-restriction-settings---978585--"></a>Nuove impostazioni relative alle restrizioni dei dispositivi Windows <!--978585-->

Verranno aggiunte impostazioni al profilo di restrizione dei dispositivi Windows che controllano funzionalità come schermi wireless, individuazione dei dispositivi, passaggio da un'attività a un'altra e messaggi di errore della scheda SIM.

### <a name="office-365-proplus-app-available-for-windows-10-devices---1121362--"></a>App Office 365 ProPlus disponibile per dispositivi Windows 10 <!--1121362-->

Verrà aggiunto un nuovo tipo di app Office 365 ProPlus che semplifica l'assegnazione delle app Office 365 ProPlus ai dispositivi Windows 10. Sarà inoltre possibile installare Microsoft Project e Microsoft Visio, se si hanno le relative licenze. Le app desiderate verranno unite in bundle e visualizzate come un'unica app nell'elenco delle app nella console di Intune.

### <a name="new-allowblock-list-for-the-managed-browser---682960--"></a>Nuovo elenco di elementi consentiti o bloccati per Managed Browser <!--682960-->

Sarà possibile configurare l'elenco di domini e URL consentiti o bloccati per Managed Browser con le impostazioni di configurazione delle applicazioni Intune nel portale di Azure. È possibile eseguire la configurazione per Managed Browser indipendentemente dal fatto che questa soluzione venga usata in un dispositivo gestito o non gestito.

### <a name="new-app-configuration-capabilities----677969---"></a>Nuove funzionalità di configurazione delle app <!-- 677969 -->

Questa funzionalità sarà equivalente alla configurazione delle app in Gestione dei dispositivi mobili (MDM). Consente agli amministratori di applicare più valori di configurazione delle app rispetto a quelli disponibili tramite i criteri di protezione delle app in MAM senza canale di registrazione.

### <a name="new-app-protection-policies-conditions-for-mam---679864--"></a>Nuove condizioni dei criteri di protezione delle app per MAM <!--679864-->

Sarà possibile impostare un requisito per MAM senza registrare gli utenti tramite la console di amministrazione che consente di applicare quanto segue:

- Versione minima dell'applicazione
- Versione minima del sistema operativo
- Versione minima di Intune App SDK per l'applicazione di destinazione (solo iOS)

Questa funzionalità è disponibile sia per Android che per iOS. Intune supporta l'imposizione della versione minima per le versioni delle piattaforme del sistema operativo, per le versioni delle applicazioni e per Intune App SDK. In iOS applicazioni con SDK integrato possono anche imporre la versione minima a livello di SDK.

L'utente non potrà accedere all'applicazione di destinazione se i requisiti minimi definiti tramite i criteri di protezione delle app non vengono soddisfatti ai tre diversi livelli definiti in precedenza. A questo punto, l'utente può rimuovere l'account (per le applicazioni con identità multiple), chiudere l'applicazione e/o aggiornare la versione del sistema operativo o dell'applicazione per soddisfare il requisito.

Sarà inoltre possibile configurare impostazioni aggiuntive tramite la console di amministrazione per fornire una notifica che non causa blocchi per consigliare un aggiornamento del sistema operativo o dell'applicazione. Questa notifica può essere chiusa e l'applicazione può essere usata normalmente.

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Modifica dell'autorità MDM senza annullare la registrazione dei dispositivi gestiti <!--1103950-->

Sarà possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Nella console di Configuration Manager è possibile modificare l'autorità MDM da Imposta su Configuration Manager (ibrida) a Microsoft Intune (autonoma) o viceversa.


### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).

