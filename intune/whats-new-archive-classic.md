---
title: Novità nell'archivio del portale classico di Microsoft Intune
description: Annunci archiviati delle novità per Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/08/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 34b219b48e5bc9e3ee688895c071b230886183eb
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38225426"
---
# <a name="whats-new-in-the-intune-classic-portal---previous-months"></a>Novità del portale di Intune classico - mesi precedenti

[!INCLUDE [classic-portal](./includes/classic-portal.md)]

Questa pagina elenca le nuove funzionalità e le notifiche annunciate in precedenza nella [pagina delle novità](whats-new.md) per il portale di Intune classico.

## <a name="april-2017"></a>Aprile 2017

### <a name="new-capabilities"></a>Nuove funzionalità

#### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps disponibile per Managed Browser <!--822308, 822303-->

Microsoft MyApps dispone ora di un supporto migliorato all'interno di Managed Browser. Gli utenti di Managed Browser che non sono assegnati alla gestione saranno indirizzati direttamente al servizio MyApps, da dove potranno accedere alle loro app SaaS con provisioning dell'amministratore. Gli utenti assegnati alla gestione di Intune continueranno a essere in grado di accedere a MyApps dal segnalibro di Managed Browser predefinito.

#### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nuove icone per Managed Browser e il portale aziendale <!--918433, 918431, 971473-->

Managed Browser disporrà di icone aggiornate per le versioni Android e iOS dell'app. La nuova icona conterrà il logo di Intune aggiornato, in modo da renderla più coerente con le altre app in Enterprise Mobility + Security (EM+S). È possibile visualizzare la nuova icona per Managed Browser nella [pagina delle novità dell'interfaccia utente dell'app di Intune](whats-new-app-ui.md).

Anche il portale aziendale riceve icone aggiornate per le versioni di Android, iOS e Windows dell'app per migliorare la coerenza con altre applicazioni in EM+S. Queste icone verranno rilasciate gradualmente tra le piattaforme da aprile a fine maggio.

#### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicatore di stato dell'accesso nel portale aziendale Android <!--953374-->

Un aggiornamento all'app Portale aziendale Android mostra un indicatore di stato dell'accesso quando l'utente avvia o riprende l'app. L'indicatore indica una progressione attraverso nuovi stati, a partire da "Connessione in corso...", ad "Accesso in corso..." e infine "Verifica dei requisiti di sicurezza in corso..." prima di consentire all'utente di accedere all'app. È possibile visualizzare le nuove schermate per l'app portale aziendale per Android nella [pagina delle novità dell'interfaccia utente dell'app di Intune](whats-new-app-ui.md).

#### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Bloccare l'accesso delle app a SharePoint Online <!-- 679339 -->

È ora possibile creare un criterio di accesso condizionale basato su app per impedire alle app a cui non sono stati applicati criteri di protezione delle app di accedere a [SharePoint Online](/intune-classic/deploy-use/mam-ca-for-sharepoint-online). Nello scenario di accesso condizionale basato su applicazioni è possibile specificare le app che dovranno accedere a SharePoint Online usando il portale di Azure.

#### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Supporto Single Sign-On dal portale aziendale per IOS ad Outlook per iOS <!--834012-->
Gli utenti non devono più eseguire l'accesso all'app di Outlook se sono già connessi all'app Portale aziendale per IOS sullo stesso dispositivo con lo stesso account. Quando gli utenti avviano l'app di Outlook, potranno selezionare il loro account e accedere automaticamente. Si prevede di aggiungere questa funzionalità anche per altre app Microsoft.

#### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Messaggi di stato migliorati nell'app Portale aziendale per iOS <!--744866-->
All'interno dell'app Portale aziendale per iOS verranno ora visualizzati nuovi messaggi di errore più specifici per fornire informazioni più accessibili su ciò che accade nei dispositivi. Questi casi di errore erano precedentemente inclusi in un messaggio di errore generale analogo a "Portale aziendale temporaneamente non disponibile". Inoltre, se un utente avvia il portale aziendale in iOS in assenza di una connessione Internet, ora verrà visualizzata una barra di stato permanente nella home page con il messaggio "Nessuna connessione Internet".

#### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Stato di installazione delle app migliorato per l'app Portale aziendale di Windows 10 <!--676495-->

I nuovi miglioramenti per le installazioni di app avviate nell'app Portale aziendale di Windows 10 includono:
-   Segnalazione dello stato dell'installazione più veloce per i pacchetti MSI
-   Segnalazione dello stato dell'installazione più veloce per le app moderne in dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 e versioni successive
-   Nuova barra di stato per le installazioni di app moderne in dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 e versioni successive

È possibile visualizzare la nuova barra di stato nella [pagina delle novità dell'interfaccia utente dell'app di Intune](whats-new-app-ui.md).

#### <a name="bulk-enroll-windows-10-devices----747607---"></a>Registrazione in blocco di dispositivi Windows 10 <!-- 747607 -->

È ora possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune con Windows Configuration Designer (WCD). Per abilitare la [registrazione MDM in blocco](/intune-classic/deploy-use/bulk-enroll-windows) del tenant di Azure AD, creare un pacchetto di provisioning che aggiunga i dispositivi al tenant di Azure AD usando Windows Configuration Designer e applicare il pacchetto ai dispositivi di proprietà dell'azienda che si vuole registrare e gestire in blocco. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento non sono supportati scenari self-service o con il portale aziendale.

### <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal--736542--"></a>Novità dell'anteprima pubblica di Intune nel portale di Azure<!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](whats-new.md).

Le novità dell'anteprima di Intune in Azure sono descritte [qui](whats-new.md).

### <a name="notices"></a>Notifiche

#### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->

Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di anteprima di Azure. In precedenza, l'anteprima della registrazione di Apple era accessibile solo dai collegamenti nel portale di Azure. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

#### <a name="whats-coming-for-appx-in-intune-in-the-azure-portal----1000270---"></a>Sviluppi futuri per Appx in Intune nel portale di Azure <!-- 1000270 -->

Nell'ambito della migrazione a Intune nel portale di Azure, saranno apportate tre modifiche alle app appx:

1. Aggiunta di un nuovo tipo di app appx nella console di Intune distribuibile solo a dispositivi registrati in MDM.
2. Reimpiego del tipo di app appx esistente per essere destinata solo a PC gestiti tramite l'agente PC di Intune.
3. Conversione di tutte le app appx esistenti in app appx MDM con la migrazione.

##### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?

Questa modifica non avrà alcun impatto sulle distribuzioni esistenti ai dispositivi gestiti tramite l'agente PC di Intune. Tuttavia, dopo la migrazione, non sarà più possibile distribuire queste app appx migrate a eventuali nuovi dispositivi gestiti tramite l'agente PC di Intune che non siano stati previsti in precedenza.

##### <a name="what-action-do-i-need-to-take"></a>Quali misure è necessario adottare?

Dopo la migrazione, sarà necessario caricare nuovamente l'app appx come app appx per PC se si vuole procedere a nuove distribuzioni su PC. Per altre informazioni, vedere [Appx changes in Intune in the Azure portal](https://aka.ms/appxchange) (Modifiche ad Appx in Intune nel portale di Azure) nel blog del team di supporto Intune.  

#### <a name="administration-roles-being-replaced-in-azure-portal"></a>Ruoli di amministrazione in corso di sostituzione nel portale di Azure

I ruoli di amministrazione di gestione delle applicazioni per dispositivi mobili (MAM) esistenti (Collaboratore, Proprietario e Sola lettura) usati nel portale classico di Intune (Silverlight) verranno sostituiti con un set completo di nuovi controlli di amministrazione in base al ruolo nel portale di Intune di Azure. Dopo aver completato la migrazione al portale di Azure, sarà necessario riassegnare gli amministratori a questi nuovi ruoli di amministrazione. Per altre informazioni sul controllo degli accessi in base al ruolo e i nuovi ruoli, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo) per Microsoft Intune](role-based-access-control.md).

### <a name="whats-coming"></a>Sviluppi futuri

#### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Migliorata l'esperienza di accesso nelle app del portale aziendale per tutte le piattaforme <!--User Story 1132123-->

Microsoft ha annunciato una modifica che verrà introdotta nei prossimi mesi e consentirà di migliorare l'esperienza di accesso per le app Portale aziendale di Intune per Android, iOS e Windows. Non appena questa modifica viene apportata con Azure AD, la nuova esperienza utente apparirà automaticamente su tutte le piattaforme per l'app del portale aziendale. Ora gli utenti possono anche accedere al portale aziendale da un altro dispositivo con un codice generato monouso. Ciò è particolarmente utile nei casi in cui gli utenti devono accedere senza credenziali.

È possibile trovare le schermate dell'esperienza di accesso precedente, della nuova esperienza di accesso con credenziali e della nuova esperienza di accesso da un altro dispositivo nella pagina delle [novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

#### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Modifiche pianificate: Intune ha intenzione di modificare l'esperienza del portale per i partner di Intune <!-- 1050016 -->

A partire dall'aggiornamento del servizio previsto per la metà di maggio 2017, la pagina Intune Partner verrà rimossa dal sito manage.microsoft.com.  

Gli amministratori di partner non saranno più in grado di visualizzare e agire per conto dei clienti dalla pagina Intune Partner, ma dovranno invece effettuare l'accesso a uno degli altri due altri portali Microsoft per i partner.

Il [Centro per i partner Microsoft](https://partnercenter.microsoft.com/) e l'[interfaccia di amministrazione partner di Office 365](https://portal.office.com/) consentiranno entrambi di accedere agli account cliente gestiti. Procedendo come partner, usare uno di questi siti per gestire i clienti.


#### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->

Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS.

Microsoft ha reso disponibile una versione dell'app Portale aziendale per iOS tramite il programma Apple TestFlight che applica i nuovi requisiti ATS. Se si desidera provarla in modo da poterne verificare la conformità con ATS, inviare un messaggio di indirizzo elettronica all'indirizzo <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con nome, cognome, indirizzo di posta elettronica e nome della società. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

## <a name="march-2017"></a>Marzo 2017

### <a name="new-capabilities"></a>Nuove funzionalità

#### <a name="support-for-skycure"></a>Supporto per Skycure

È ora possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Skycure, una soluzione di protezione dalle minacce per dispositivi mobili integrata in Microsoft Intune. La valutazione dei rischi viene effettuata in base ai dati di telemetria raccolti dai dispositivi che eseguono Skycure, inclusi i seguenti:

- Difesa fisica
- Difesa della rete
- Difesa delle applicazioni
- Difesa delle vulnerabilità

È possibile configurare criteri di accesso condizionale EMS basati sulla valutazione dei rischi di Skycure e abilitati tramite i criteri di conformità dei dispositivi di Intune. È possibile usare questi criteri per consentire o negare l'accesso alle risorse aziendali ai dispositivi non conformi in base alle minacce rilevate. Per altre informazioni, vedere [Connettore Skycure Mobile Threat Defense](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622-->

L'interfaccia utente dell'app Portale aziendale per Android verrà aggiornata per offrire un aspetto più moderno e una migliore esperienza utente. Di seguito sono illustrati gli aggiornamenti più significativi:

- Colori: le intestazioni delle schede dell'app Portale aziendale possono avere un colore personalizzato definito dal personale IT.
- App: nella scheda **App** i pulsanti **App in evidenza** e **Tutte le app** sono stati aggiornati.
- Ricerca: nella scheda **App** il pulsante **Cerca** è un pulsante di azione mobile.
- Navigazione tra le app: in **Tutte le app** è disponibile una visualizzazione a schede di **In evidenza**, **Tutte** e **Categorie** per una navigazione più semplice.
- Supporto: le schede **Dispositivi personali** e **Contatta l'IT** sono state aggiornate per migliorare la leggibilità.

Per altre informazioni su queste modifiche, vedere [Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune](whats-new-app-ui.md).

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->

Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

#### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script di firma per l'app Portale aziendale di Windows 10<!--941642-->

Se è necessario scaricare e trasferire localmente l'app Portale aziendale di Windows 10, è ora disponibile uno script per semplificare e ottimizzare il processo di firma dell'app per l'organizzazione.   Per scaricare lo script e le relative istruzioni d'uso, vedere [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Script di firma di Microsoft Intune per l'app Portale aziendale di Windows 10) nella raccolta TechNet. Per altre informazioni su questo annuncio, vedere [Updating your Windows 10 Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) (Aggiornamento dell'app Portale aziendale di Windows 10) nel blog del team di supporto di Intune.


### <a name="notices"></a>Notifiche

#### <a name="support-for-ios-103"></a>Supporto per iOS 10.3

La distribuzione della versione 10.3 di iOS è iniziata il 27 marzo 2017 agli utenti di iOS. Tutti gli scenari MDM e MAM di Intune esistenti sono compatibili con la versione più recente del sistema operativo Apple. È previsto che tutte le funzionalità di Intune esistenti attualmente disponibili per la gestione dei dispositivi iOS continueranno a funzionare dopo l'aggiornamento dei dispositivi a iOS 10.3.

Non ci sono attualmente problemi noti da condividere. Se si riscontrano problemi con iOS 10.3, non esitare a contattare il [team di supporto di Intune](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune).

#### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Supporto migliorato per gli utenti Android in Cina <!--720444-->

A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere le app dai marketplace cinesi. L'app Portale aziendale supporterà questo flusso di lavoro reindirizzando gli utenti Android in Cina per scaricare le app Portale aziendale e Outlook dagli app store locali. Ciò consentirà di migliorare l'esperienza utente quando sono abilitati i criteri di accesso condizionale, per la gestione dei dispositivi e delle applicazioni mobili. Le app Portale aziendale e Outlook per Android sono disponibili negli app store cinesi seguenti:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

#### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Procedura consigliata: verificare che le app Portale aziendale siano aggiornate <!--879465-->

Nel mese di dicembre 2016 è stato rilasciato un aggiornamento che imponeva l'uso di Multi-Factor Authentication (MFA) a un gruppo di utenti che registrano un dispositivo iOS, Android, Windows 8.1+ o Windows Phone 8.1+. Questa funzionalità non può essere usata senza determinate versioni di base dell'app Portale aziendale per Android (5.0.3419.0+) e iOS (2.1.17+).

Microsoft è costantemente impegnata a migliorare Intune introducendo nuove funzioni sia per la console sia per le app Portale aziendale su tutte le piattaforme supportate. Pertanto, Microsoft rilascia solo le correzioni relative ai problemi rilevati nella versione corrente dell'app Portale aziendale. Per un'esperienza utente ottimale è quindi consigliabile usare le versioni più recenti delle app Portale aziendale.

>[!Tip]
> Chiedere agli utenti di impostare i dispositivi in modo da aggiornare automaticamente le app dallo Store appropriato. Se si è resa disponibile l'app Portale aziendale di Android su una condivisione di rete, è possibile scaricare la versione più recente dall'[Area download Microsoft](https://www.microsoft.com/download/details.aspx?id=49140).

#### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams è ora abilitato per MAM su iOS e Android

Microsoft ha annunciato la disponibilità generale di Microsoft Teams. Nelle app Microsoft Teams aggiornate per iOS e Android sono ora abilitate le funzionalità di gestione delle app mobili (MAM, Mobile App Management) di Intune. È così possibile consentire ai team di passare liberamente da un dispositivo all'altro, garantendo la protezione delle conversazioni e dei dati aziendali a ogni cambio di dispositivo. Per altre informazioni, vedere [l'annuncio relativo a Microsoft Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) nel blog di Enterprise Mobility + Security.


## <a name="february-2017"></a>Febbraio 2017

### <a name="new-capabilities"></a>Nuove funzionalità

### <a name="modernizing-the-company-portal-website---753980--"></a>Aggiornamento del sito Web del portale aziendale <!--753980-->
Il sito Web del portale aziendale supporterà le app destinate agli utenti che non hanno dispositivi gestiti. Il sito Web verrà allineato agli altri prodotti e servizi Microsoft con una nuova combinazione colori a contrasto, illustrazioni dinamiche e un "hamburger menu". ![Immagine dell'"hamburger menu" aggiunto nell'angolo superiore sinistro del sito Web del portale aziendale](./media/CP_hamburger_menu.png).

### <a name="notices"></a>Notifiche

#### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migrazione dei gruppi non richiederà aggiornamenti ai gruppi o ai criteri per i dispositivi iOS <!--898837-->
Per ogni gruppo di dispositivi Intune preassegnato da un profilo Registrazione di dispositivi aziendali, verrà creato un gruppo di dispositivi dinamico corrispondente in AAD basato sul nome del profilo Registrazione di dispositivi aziendali durante la migrazione ai gruppi di dispositivi di Azure Active Directory. In questo modo i dispositivi registrati vengono raggruppati automaticamente e ricevono gli stessi criteri e le stesse app del gruppo Intune originale.

Quando un tenant entra nel processo di migrazione per la creazione del gruppo e la selezione della destinazione, Intune crea automaticamente un gruppo AAD dinamico corrispondente a un gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali. Se l'amministratore Intune elimina il gruppo Intune di destinazione, il gruppo AAD dinamico corrispondente non viene eliminato. I membri del gruppo e la query dinamica vengono cancellati, ma il gruppo viene mantenuto fino a quando l'amministratore IT non lo rimuove tramite il portale AAD.

Analogamente, se l'amministratore IT modifica il gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali, Intune crea un nuovo gruppo dinamico che riflette la nuova assegnazione del profilo ma non rimuove il gruppo dinamico creato per l'assegnazione precedente.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>La gestione dei dispositivi desktop Windows avviene per impostazione predefinita tramite le impostazioni di Windows <!--663050-->
Il comportamento predefinito per la registrazione dei computer desktop di Windows 10 sta cambiando. Per le nuove registrazioni verrà usato il flusso di registrazione dell'agente MDM tipico anziché tramite l'agente per PC. Il sito Web del portale aziendale fornirà agli utenti di desktop Windows 10 istruzioni per la registrazione, che consentono di eseguire in modo guidato il processo di aggiunta di computer desktop Windows 10 come dispositivi mobili. Ciò non influirà su PC già registrati e l'organizzazione può comunque decidere di gestire i desktop Windows 10 con l'agente per PC, [se preferibile](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Miglioramento del supporto della gestione delle app per dispositivi mobili per la cancellazione selettiva <!--581242-->
Gli utenti finali riceveranno ulteriori indicazioni su come riottenere l'accesso ai dati aziendali o dell'istituto di istruzione se i dati vengono rimossi automaticamente a causa del criterio "Intervallo offline (giorni) prima della cancellazione dei dati dell'app".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>I collegamenti al portale aziendale per iOS si aprono all'interno dell'app <!--665954-->
I collegamenti all'interno dell'app Portale aziendale per iOS, inclusi quelli per la documentazione e le app, verranno aperti direttamente nell'app Portale aziendale tramite una visualizzazione in-app di Safari. Questo aggiornamento verrà fornito separatamente rispetto all'aggiornamento del servizio in gennaio.

#### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nuovo indirizzo del server MDM per i dispositivi Windows <!--893007-->
Gli utenti di Windows e Windows Phone che tentano di registrare un dispositivo non riusciranno a eseguire la registrazione se immettono __manage.microsoft.com__ come indirizzo del server MDM (se richiesto). L'indirizzo del server MDM __manage.microsoft.com__ è sostituito da __enrollment.manage.microsoft.com__. Comunicare agli utenti di immettere __enrollment.manage.microsoft.com__ come indirizzo del server MDM per la registrazione di un dispositivo Windows o Windows Phone. Non sono necessarie modifiche alla configurazione CNAME. Per altre informazioni su questa modifica, visitare [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

#### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622-->
A partire da marzo, l'app Portale aziendale per Android seguirà le [linee guida di progettazione dei materiali](https://material.io/guidelines/material-design/introduction.html) per creare un aspetto più moderno. La nuova esperienza utente include i seguenti miglioramenti:

* __Colori__: i colori delle intestazioni delle schede possono essere impostati in base alla tavolozza dei colori personalizzata.
* __Interfaccia__: i pulsanti App in evidenza e Tutte le app sono stati aggiornati nella scheda App. Il pulsante Cerca è ora un pulsante di azione mobile.
* __Navigazione__: Tutte le app mostra una visualizzazione a schede di In evidenza, Tutte e Categorie per una navigazione più semplice.
* __Servizio__: la leggibilità delle schede Dispositivi personali e Contatta l'IT è stata migliorata.

Le immagini di prima e dopo sono disponibili nella [pagina degli aggiornamenti dell'interfaccia utente](whats-new-app-ui.md).

### <a name="associate-multiple-management-tools-with-the-microsoft-store-for-business---926135--"></a>Associare più strumenti di gestione con Microsoft Store per le aziende <!--926135-->
Se si usa più di uno strumento di gestione per distribuire le app di Microsoft Store per le aziende, in precedenza era possibile associare soltanto un'app a Microsoft Store per le aziende. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager. Per informazioni dettagliate, vedere [Gestire le app acquistate in Microsoft Store per le aziende con Microsoft Intune](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-intune-in-the-azure-portal---736542--"></a>Novità dell'anteprima pubblica di Intune nel portale di Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](whats-new.md).

Le novità dell'anteprima di Intune in Azure sono descritte [qui](whats-new.md).

## <a name="january-2017"></a>Gennaio 2017

### <a name="new-capabilities"></a>Nuove funzionalità

#### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Report nella console per MAM senza registrazione <!--677961-->
Sono stati aggiunti nuovi report relativi alla protezione delle app, sia per i dispositivi registrati che per quelli non registrati. Per altre informazioni in merito, vedere [Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](/intune-classic/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

#### <a name="android-711-support---694397--"></a>Supporto per Android 7.1.1 <!--694397-->
Intune ora supporta completamente Android 7.1.1 e la relativa gestione.

#### <a name="resolve-issue-where-ios-devices-are-inactive-or-the-admin-console-cannot-communicate-with-them---unknown--"></a>Risolvere il problema laddove i dispositivi iOS non sono attivi o la console di amministrazione non riesce a comunicare con i dispositivi <!--unknown-->
Quando i dispositivi degli utenti perdono la connessione con Intune è possibile indicare nuovi passaggi per la risoluzione dei problemi per ripristinare l'accesso alle risorse aziendali. Vedere [I dispositivi sono inattivi o la console di amministrazione non è in grado di comunicare con i dispositivi](/intune-classic/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="notices"></a>Notifiche

#### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>La gestione dei dispositivi desktop Windows avviene per impostazione predefinita tramite le impostazioni di Windows <!--663050-->
Il comportamento predefinito per la registrazione dei computer desktop di Windows 10 sta cambiando. Per le nuove registrazioni verrà usato il flusso di registrazione dell'agente MDM tipico anziché tramite l'agente per PC.

Il sito Web del portale aziendale fornirà agli utenti di desktop Windows 10 istruzioni per la registrazione, che consentono di eseguire in modo guidato il processo di aggiunta di computer desktop Windows 10 come dispositivi mobili. Ciò non influirà su PC già registrati e l'organizzazione può comunque decidere di gestire i desktop Windows 10 con l'agente per PC, [se preferibile](/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune).

#### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Miglioramento del supporto della gestione delle app per dispositivi mobili per la cancellazione selettiva <!--581242-->
Gli utenti finali riceveranno ulteriori indicazioni su come riottenere l'accesso ai dati aziendali o dell'istituto di istruzione se i dati vengono rimossi automaticamente a causa del criterio "Intervallo offline (giorni) prima della cancellazione dei dati dell'app".<!--, or the removal of the Intune Company Portal on Android.-->

#### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>I collegamenti al portale aziendale per iOS si aprono all'interno dell'app <!--665954-->
I collegamenti all'interno dell'app Portale aziendale per iOS, inclusi quelli per la documentazione e le app, verranno aperti direttamente nell'app Portale aziendale tramite una visualizzazione in-app di Safari. Questo aggiornamento verrà fornito separatamente rispetto all'aggiornamento del servizio in gennaio.

#### <a name="modernizing-the-company-portal-website---753980--"></a>Aggiornamento del sito Web del portale aziendale <!--753980-->
A partire da febbraio, il sito Web del portale aziendale supporterà le app destinate agli utenti che non hanno dispositivi gestiti. Il sito Web verrà allineato agli altri prodotti e servizi Microsoft con una nuova combinazione colori a contrasto, illustrazioni dinamiche e un "hamburger menu". ![Menu Hamburger del sito Web del portale aziendale](./media/CP_hamburger_menu.png).

#### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nuova documentazione per i criteri di protezione delle app <!--583398-->
È stata aggiornata la documentazione per gli amministratori e gli sviluppatori di app che vogliono abilitare i criteri di protezione delle app (noti come criteri MAM) nelle loro app iOS e Android usando lo strumento di wrapping delle app di Intune o Intune App SDK.

Sono stati aggiornati gli articoli seguenti:

* [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](apps-prepare-mobile-application-management.md)
* [Preparare le app per iOS per la gestione delle app mobili con lo strumento di wrapping delle app di Intune](app-wrapper-prepare-ios.md)
* [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md)
* [Manuale dello sviluppatore di Intune App SDK per iOS](app-sdk-ios.md)

Gli articoli seguenti sono stati aggiunti alla raccolta della documentazione:

* [Plug-in Cordova per Intune App SDK](app-sdk-cordova.md)
* [Componente Xamarin per Intune App SDK](app-sdk-xamarin.md)

#### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Indicatore di stato quando si avvia l'app Portale aziendale in iOS <!--665978-->
Nell'app Portale aziendale per iOS verrà introdotta una barra di stato nella schermata di avvio per fornire all'utente informazioni sui processi di caricamento eseguiti. L'implementazione della barra di stato in sostituzione dell'indicatore di stato rotante avverrà in modo graduale. Questo significa che alcuni utenti visualizzeranno la nuova barra di stato, mentre altri continueranno a vedere l'indicatore rotante.

## <a name="december-2016"></a>Dicembre 2016

### <a name="public-preview-of-intune-in-the-azure-portal--736542--"></a>Anteprima pubblica di Intune nel portale di Azure<!--736542-->
All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile usando le API Graph. Prima della disponibilità generale di questo portale per tutti i tenant di Intune, siamo lieti di annunciare che verrà introdotta un'anteprima di questa nuova esperienza di amministrazione in seguito durante il mese a tenant selezionati.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, per scoprire cosa abbiamo in serbo per Microsoft Intune nel portale di Azure, vedere la [nuova documentazione](/intune/what-is-intune).

__Integrazione con i servizi di gestione delle spese di telecomunicazione nell'anteprima pubblica del portale di Azure__ <!--747605--> Microsoft sta iniziando a presentare in anteprima l'integrazione con i servizi di gestione delle spese di telecomunicazione di terze parti nel portale di Azure. È possibile usare Intune per imporre limiti al consumo dei dati sia nazionale che in roaming. Queste integrazioni iniziano con [Saaswedo](http://www.saaswedo.com/). Per abilitare questa funzionalità nel tenant di prova, [contattare il supporto tecnico Microsoft](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="new-capabilities"></a>Nuove funzionalità

__Autenticazione a più fattori su tutte le piattaforme__ <!--747590--> È ora possibile imporre l'autenticazione a più fattori (MFA) per un gruppo selezionato di utenti durante la registrazione di un dispositivo iOS, Android, Windows 8.1+ o Windows Phone 8.1+ dal portale di gestione di Azure configurando MFA nell'applicazione di registrazione di Microsoft Intune in Azure Active Directory.

__Possibilità di limitare la registrazione dei dispositivi mobili__ <!--747596--> Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.
* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.
* Solo per iOS: è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="notices"></a>Notifiche

__Trasferimento di Multi-Factor Authentication per la registrazione nel portale di Azure__ <!--VSO 750545--> Per impostare MFA per le registrazioni in Intune, gli amministratori dovevano usare in precedenza la console di Intune o Configuration Manager (prima della versione di ottobre 2016). Con questa funzionalità aggiornata è ora possibile accedere al [portale di Microsoft Azure](https://manage.windowsazure.com) con le credenziali di Intune e configurare le impostazioni di MFA tramite Azure AD. Per altre informazioni a questo proposito, vedere [qui](https://aka.ms/mfa_ad).

__App Portale aziendale per Android ora disponibile in Cina__ <!--VSO 658093--> L'app Portale aziendale per Android sta per essere pubblicata per il download in Cina. A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere l'app dai marketplace di app cinesi. L'app Portale aziendale per Android sarà disponibile per il download negli store seguenti:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

L'app Portale aziendale per Android usa i servizi Google Play per comunicare con il servizio Microsoft Intune. Dato che i servizi Google Play non sono ancora disponibili in Cina, per completare qualsiasi attività tra le seguenti possono essere richieste fino a 8 ore. 

|Console di amministrazione di Intune| App Portale aziendale di Intune per Android |Sito Web del portale aziendale di Intune|   
|---|---|---|
|Cancellazione completa| Rimozione di un dispositivo remoto| Rimozione di un dispositivo (locale e remoto)|
|Cancellazione selettiva| Reimpostazione del dispositivo| Reimpostazione del dispositivo|
|Distribuzioni di app nuove o aggiornate| Installazione delle app line-of-business disponibili| Reimpostazione del passcode del dispositivo|
|Blocco remoto|||
|Reimpostazione del passcode|||

### <a name="deprecations"></a>Elementi deprecati

__Supporto per Silverlight non più disponibile in Firefox__ <!--VSO TBA--> Mozilla rimuoverà il supporto per Silverlight nella versione 52 del [browser Firefox](https://www.mozilla.org/firefox) a partire da marzo 2017. Di conseguenza, non sarà più possibile accedere alla console di Intune esistente usando versioni di Firefox superiori alla 51. Si consiglia di usare Internet Explorer 10 o 11 per accedere alla console di amministrazione o una [versione di Firefox precedente alla versione 52](https://ftp.mozilla.org/pub/firefox/releases/). La transizione di Intune al portale di Azure consentirà di supportare una serie di [browser moderni](/azure/azure-preview-portal-supported-browsers-devices) che non dipendono da Silverlight.

__Rimozione dei criteri per le cassette postali per dispositivi portatili di Exchange Online__ <!--770687--> A partire da dicembre, gli amministratori non potranno più visualizzare né configurare i criteri per le cassette postali per dispositivi portatili di Exchange Online (EAS) all'interno della console di Intune. Questa modifica verrà distribuita in tutti i tenant di Intune nel corso di dicembre e gennaio. La configurazione di tutti i criteri esistenti rimarrà invariata. Per la configurazione dei nuovi criteri, usare Exchange Management Shell. Altre informazioni sono disponibili [qui](https://technet.microsoft.com/library/bb123783%28v=exchg.150%29.aspx).

__Supporto per le app Intune AV Player, Image Viewer e PDF Viewer non più disponibile in Android__ <!--747553--> A partire dalla metà di dicembre 2016, gli utenti non potranno più usare le app Intune AV Player, Image Viewer e PDF Viewer. Queste app sono state sostituite dall'app Azure Information Protection. È possibile trovare altre informazioni sull'app Azure Information Protection [qui](/information-protection/rms-client/mobile-app-faq).

## <a name="november-2016"></a>Novembre 2016

### <a name="new-capabilities"></a>Nuove funzionalità

__Nuovo portale aziendale di Microsoft Intune disponibile per dispositivi Windows 10__ Microsoft ha rilasciato una nuova app [Portale aziendale di Microsoft Intune per dispositivi Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Questa app, che sfrutta il nuovo formato universale di Windows 10, offrirà un'esperienza utente aggiornata all'interno dell'app ed esperienze identiche in tutti i dispositivi Windows 10, sia PC che mobili, senza variazioni alle funzionalità già in uso.

La nuova app consentirà anche agli utenti di sfruttare altre funzionalità della piattaforma come Single Sign-On (SSO) e l'autenticazione basata su certificato nei dispositivi Windows 10. L'app verrà resa disponibile come aggiornamento delle installazioni esistenti dell'app Portale aziendale di Windows 8.1 e l'app Portale aziendale di Windows Phone 8.1 viene installata da Microsoft Windows Store. Per altre informazioni, vedere [aka.ms/intunecp_universalapp](http://aka.ms/intunecp_universalapp).

> [!IMPORTANT]
> __Un aggiornamento in Intune e Android for Work__ Anche se è possibile distribuire app Android for Work con l'azione __Richiesto__, un'app può essere distribuita solo come __Disponibile__ se è stata eseguita la migrazione dei gruppi di Intune alla nuova esperienza dei gruppi di Azure AD.

__Il plug-in Cordova per Intune App SDK attualmente supporta la gestione di applicazioni mobili senza registrazione__ Gli sviluppatori di app possono ora usare il plug-in Cordova per Intune App SDK per abilitare funzionalità di gestione di applicazioni mobili senza registrazione del dispositivo nelle proprie app basate su Cordova per iOS e Android. Il plug-in Cordova per Intune App SDK è disponibile [qui](https://github.com/msintuneappsdk/cordova-plugin-ms-intune-mam).

__Il componente Xamarin per Intune App SDK attualmente supporta la gestione di applicazioni mobili senza registrazione__ Gli sviluppatori di app possono ora usare il componente Xamarin per Intune App SDK per abilitare funzionalità di gestione di applicazioni mobili senza registrazione del dispositivo nelle proprie app basate su Xamarin per iOS e Android. Il componente Xamarin per Intune App SDK è disponibile [qui](https://github.com/msintuneappsdk/intune-app-sdk-xamarin).

### <a name="notices"></a>Notifiche

__Il certificato di firma Symantec non richiede più un'app Portale aziendale di Windows Phone 8 firmata per il caricamento__ Per il caricamento del certificato di firma Symantec non è più necessaria un'app Portale aziendale di Windows Phone 8 firmata. Il certificato può essere caricato in modo indipendente.

### <a name="deprecations"></a>Elementi deprecati

__Supporto per l'app Portale aziendale di Windows Phone 8__ Il supporto per il portale aziendale di Windows Phone 8 sarà deprecato. Il supporto per le piattaforme Windows Phone 8 e WinRT è stato deprecato a ottobre 2016. Il supporto per il portale aziendale di Windows 8 è stato deprecato a ottobre 2016.


### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
