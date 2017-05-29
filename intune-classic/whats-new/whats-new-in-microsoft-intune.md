---
title: "Novità | Microsoft Docs"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 2e6452a066aa7eaeb295a3b531d83dc3b632bcf5
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---
# <a name="whats-new-in-microsoft-intune---april-2017"></a>Novità di Microsoft Intune - Aprile 2017
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

> [!Note]
> Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="myapps-available-for-managed-browser---822308-822303--"></a>MyApps disponibile per Managed Browser <!--822308, 822303-->

Microsoft MyApps dispone ora di un supporto migliorato all'interno di Managed Browser. Gli utenti di Managed Browser che non sono assegnati alla gestione saranno indirizzati direttamente al servizio MyApps, da dove potranno accedere alle loro app SaaS con provisioning dell'amministratore. Gli utenti assegnati alla gestione di Intune continueranno a essere in grado di accedere a MyApps dal segnalibro di Managed Browser predefinito.

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431-971473--"></a>Nuove icone per Managed Browser e il portale aziendale <!--918433, 918431, 971473-->

Managed Browser disporrà di icone aggiornate per le versioni Android e iOS dell'app. La nuova icona conterrà il logo di Intune aggiornato, in modo da renderla più coerente con le altre app in Enterprise Mobility + Security (EM+S). È possibile visualizzare la nuova icona per Managed Browser nella [pagina delle novità dell'interfaccia utente dell'app di Intune](whats-new-in-intune-app-ui.md).

Il portale aziendale disporrà inoltre di icone aggiornate per le versioni Android, iOS e Windows dell'app, per migliorare la coerenza con le altre app in EM+S. Queste icone verranno rilasciate gradualmente tra le piattaforme da aprile a fine maggio.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicatore di stato dell'accesso nel portale aziendale Android <!--953374-->

Un aggiornamento all'app Portale aziendale Android mostra un indicatore di stato dell'accesso quando l'utente avvia o riprende l'app. L'indicatore indica una progressione attraverso nuovi stati, a partire da "Connessione in corso...", ad "Accesso in corso..." e infine "Verifica dei requisiti di sicurezza in corso..." prima di consentire all'utente di accedere all'app. È possibile visualizzare le nuove schermate per l'app portale aziendale per Android nella [pagina delle novità dell'interfaccia utente dell'app di Intune](whats-new-in-intune-app-ui.md).

### <a name="block-apps-from-accessing-sharepoint-online----679339---"></a>Bloccare l'accesso delle app a SharePoint Online <!-- 679339 -->

È ora possibile creare un criterio di accesso condizionale basato su app per impedire alle app a cui non sono stati applicati criteri di protezione delle app di accedere a [SharePoint Online](/intune-classic/deploy-use/mam-ca-for-sharepoint-online). Nello scenario di accesso condizionale basato su applicazioni è possibile specificare le app che dovranno accedere a SharePoint Online usando il portale di Azure.

### <a name="single-sign-on-support-from-the-company-portal-for-ios-to-outlook-for-ios---834012--"></a>Supporto Single Sign-On dal portale aziendale per IOS ad Outlook per iOS <!--834012-->
Gli utenti non devono più eseguire l'accesso all'app di Outlook se sono già connessi all'app Portale aziendale per IOS sullo stesso dispositivo con lo stesso account. Quando gli utenti avviano l'app di Outlook, potranno selezionare il loro account e accedere automaticamente. Si prevede di aggiungere questa funzionalità anche per altre app Microsoft.

### <a name="improved-status-messaging-in-the-company-portal-app-for-ios---744866--"></a>Messaggi di stato migliorati nell'app Portale aziendale per iOS <!--744866-->
All'interno dell'app Portale aziendale per iOS verranno ora visualizzati nuovi messaggi di errore più specifici per fornire informazioni più accessibili su ciò che accade nei dispositivi. Questi casi di errore erano precedentemente inclusi in un messaggio di errore generale analogo a "Portale aziendale temporaneamente non disponibile". Inoltre, se un utente avvia il portale aziendale in iOS in assenza di una connessione Internet, ora verrà visualizzata una barra di stato permanente nella home page con il messaggio "Nessuna connessione Internet".

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Stato di installazione delle app migliorato per l'app Portale aziendale di Windows 10 <!--676495-->

I nuovi miglioramenti per le installazioni di app avviate nell'app Portale aziendale di Windows 10 includono:
-    Segnalazione dello stato dell'installazione più veloce per i pacchetti MSI
-    Segnalazione dello stato dell'installazione più veloce per le app moderne in dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 e versioni successive
-    Nuova barra di stato per le installazioni di app moderne in dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 e versioni successive

È possibile visualizzare la nuova barra di stato nella [pagina delle novità dell'interfaccia utente dell'app di Intune](whats-new-in-intune-app-ui.md).

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Registrazione in blocco di dispositivi Windows 10 <!-- 747607 -->

È ora possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune con Progettazione configurazione di Windows /intune-classic/deploy-use/bulk-enroll-windows) per il tenant di Azure AD, creare un pacchetto di provisioning che associa i dispositivi al tenant di Azure AD tramite Progettazione configurazione di Windows e applicare il pacchetto ai dispositivi di proprietà dell'azienda che si intende registrare in blocco e gestire. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento non sono supportati scenari self-service o con il portale aziendale.

## <a name="notices"></a>Notifiche

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->

Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di anteprima di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="whats-coming-for-appx-in-intune-on-azure----1000270---"></a>Sviluppi futuri per Appx in Intune in Azure <!-- 1000270 -->

Nell'ambito della migrazione a Intune in Azure, saranno apportate tre modifiche alle app appx:

1. Aggiunta di un nuovo tipo di app appx nella console di Intune classica distribuibile solo a dispositivi registrati MDM.
2. Reimpiego del tipo di app appx esistente per essere destinata solo a PC gestiti tramite l'agente PC di Intune.
3. Conversione di tutte le app appx esistenti in app appx MDM con la migrazione.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?

Questa modifica non avrà alcun impatto sulle distribuzioni esistenti ai dispositivi gestiti tramite l'agente PC di Intune. Tuttavia, dopo la migrazione, non sarà più possibile distribuire queste app appx migrate a eventuali nuovi dispositivi gestiti tramite l'agente PC di Intune che non siano stati previsti in precedenza.

#### <a name="what-action-do-i-need-to-take"></a>Quali misure è necessario adottare?

Dopo la migrazione, sarà necessario caricare nuovamente l'app appx come app appx per PC se si vuole procedere a nuove distribuzioni su PC. Per altre informazioni, vedere [Appx changes in Intune on Azure](https://aka.ms/appxchange) (Modifiche ad Appx in Intune in Azure) nel blog del team di supporto Intune.  

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novità dell'anteprima pubblica dell'esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](/intune/whats-new).

> [!Note]
> È in corso l'implementazione degli aggiornamenti di questo mese per il portale di anteprima di Azure. Queste modifiche, tuttavia, potrebbero non essere disponibili immediatamente a causa della modalità di implementazione del servizio Intune.  Alcuni componenti del servizio devono essere aggiornati in sequenza prima che le nuove funzionalità del portale siano disponibili. Cercare gli aggiornamenti relativi al portale di anteprima di Azure a mano a mano che verranno implementati nel corso del mese. Per l'elenco completo delle modifiche, vedere [Novità dell'anteprima di Microsoft Intune](/intune/whats-new).

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Ruoli di amministrazione in corso di sostituzione nel portale di Azure

I ruoli di amministrazione di gestione delle applicazioni per dispositivi mobili (MAM) esistenti (Collaboratore, Proprietario e Sola lettura) usati nel portale classico di Intune (Silverlight) verranno sostituiti con un set completo di nuovi controlli di amministrazione in base al ruolo nel portale di Intune di Azure. Dopo aver completato la migrazione al portale di Azure, sarà necessario riassegnare gli amministratori a questi nuovi ruoli di amministrazione. Per altre informazioni sul controllo degli accessi in base al ruolo e i nuovi ruoli, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo) per Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Sviluppi futuri

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Migliorata l'esperienza di accesso nelle app del portale aziendale per tutte le piattaforme <!--User Story 1132123-->

Microsoft ha annunciato una modifica che verrà introdotta nei prossimi mesi e consentirà di migliorare l'esperienza di accesso per le app Portale aziendale di Intune per Android, iOS e Windows. Non appena questa modifica viene apportata con Azure AD, la nuova esperienza utente apparirà automaticamente su tutte le piattaforme per l'app del portale aziendale. Ora gli utenti possono anche accedere al portale aziendale da un altro dispositivo con un codice generato monouso. Ciò è particolarmente utile nei casi in cui gli utenti devono accedere senza credenziali.

È possibile trovare le schermate dell'esperienza di accesso precedente, della nuova esperienza di accesso con credenziali e della nuova esperienza di accesso da un altro dispositivo nella pagina delle [novità dell'interfaccia utente dell'app](whats-new-in-intune-app-ui.md).

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Modifiche pianificate: Intune ha intenzione di modificare l'esperienza del portale per i partner di Intune <!-- 1050016 -->

A partire dall'aggiornamento del servizio previsto per la metà di maggio 2017, la pagina Intune Partner verrà rimossa dal sito manage.microsoft.com.  

Gli amministratori di partner non saranno più in grado di visualizzare e agire per conto dei clienti dalla pagina Intune Partner, ma dovranno invece effettuare l'accesso a uno degli altri due altri portali Microsoft per i partner.

Il [Centro per i partner Microsoft](https://partnercenter.microsoft.com/) e l'[interfaccia di amministrazione partner di Office 365](https://portal.office.com/) consentiranno entrambi di accedere agli account cliente gestiti. Procedendo come partner, usare uno di questi siti per gestire i clienti.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->

Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS.

Microsoft ha reso disponibile una versione dell'app Portale aziendale per iOS tramite il programma Apple TestFlight che applica i nuovi requisiti ATS. Se si desidera provarla in modo da poterne verificare la conformità con ATS, inviare un messaggio di indirizzo elettronica all'indirizzo <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con nome, cognome, indirizzo di posta elettronica e nome della società. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novità dell'anteprima di Azure](https://docs.microsoft.com/intune/whats-new)
* [What's new in the Company Portal UI](/intune-classic/whats-new/whats-new-in-company-portal-ui) (Novità nell'interfaccia utente del portale aziendale)
* [Archivio delle novità](whats-new-archive.md)

