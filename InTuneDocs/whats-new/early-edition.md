---
title: Edizione anticipata | Documentazione Microsoft
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 18d47678b0fbdbd98502f2d3b469b202b567b2e7
ms.openlocfilehash: 3c7edc236878232c6f4c0ae993733c967946e765


---

# <a name="the-early-edition-for-microsoft-intune---january"></a>Edizione anticipata per Microsoft Intune - Gennaio

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
> Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="actions-for-non-compliance---730266--"></a>Azioni per la mancata conformità <!--730266-->
Le _azioni per la mancata conformità_ sono una nuova funzionalità dei criteri di conformità che consente di intervenire sui dispositivi non conformi. È possibile specificare una o più azioni e il periodo di tempo in cui devono essere eseguite tali azioni. Ad esempio, è possibile segnalare immediatamente agli utenti i dispositivi non conformi non appena diventano non conformi, tramite posta elettronica, oppure è possibile impedire ai dispositivi non conformi di accedere alle risorse aziendali dopo un periodo di tolleranza di 3 giorni tramite l'accesso condizionale.

### <a name="in-console-reports-for-mam-without-enrollment---677961--"></a>Report nella console per MAM senza registrazione <!--677961-->
Sono stati aggiunti nuovi report relativi alla protezione delle app, sia per i dispositivi registrati che per quelli non registrati. Per altre informazioni in merito, vedere [Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune).

### <a name="conditional-access-for-mam-with-sharepoint-online---679339--"></a>Accesso condizionale per MAM con SharePoint Online <!--679339-->
È possibile impedire l'accesso a SharePoint Online alle app non supportate dai criteri di gestione delle app mobili (MAM) di Intune.  È possibile iniziare a usare le funzionalità di gestione delle app mobili di Intune nel portale di Azure. Individuare la sezione __Accesso condizionale__ nel pannello __Impostazioni__ che includerà l'opzione per SharePoint Online. Questa funzionalità verrà fornita separatamente rispetto al resto del rilascio del servizio. <!--Find out more about this new feature [here](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="android-711-support---694397--"></a>Supporto per Android 7.1.1 <!--694397-->
Intune ora supporta completamente Android 7.1.1 e la relativa gestione.

## <a name="notices"></a>Notifiche

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>La gestione dei dispositivi desktop Windows avviene per impostazione predefinita tramite le impostazioni di Windows <!--663050-->
Il comportamento predefinito per la registrazione dei computer desktop di Windows 10 sta cambiando. Per le nuove registrazioni verrà usato il flusso di registrazione dell'agente MDM tipico anziché tramite l'agente per PC.

Il sito Web del portale aziendale fornirà agli utenti di desktop Windows 10 istruzioni per la registrazione, che consentono di eseguire in modo guidato il processo di aggiunta di computer desktop Windows 10 come dispositivi mobili. Ciò non influirà su PC già registrati e l'organizzazione può comunque decidere di gestire i desktop Windows 10 con l'agente per PC, [se preferibile](https://docs.microsoft.com/en-us/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>I collegamenti al portale aziendale per iOS si aprono all'interno dell'app <!--665954-->
I collegamenti all'interno dell'app Portale aziendale per iOS, inclusi quelli per la documentazione e le app, verranno aperti direttamente nell'app Portale aziendale tramite una visualizzazione in-app di Safari. Questo aggiornamento verrà fornito separatamente rispetto all'aggiornamento del servizio in gennaio.

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Miglioramento del supporto della gestione delle app per dispositivi mobili per la cancellazione selettiva <!--581242-->
Gli utenti finali riceveranno ulteriori indicazioni su come riottenere l'accesso ai dati aziendali o dell'istituto di istruzione se i dati vengono rimossi automaticamente a causa del criterio "Intervallo offline (giorni) prima della cancellazione dei dati dell'app".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="new-documentation-for-app-protection-policies---583398--"></a>Nuova documentazione per i criteri di protezione delle app <!--583398-->
È stata aggiornata la documentazione per gli amministratori e gli sviluppatori di app che vogliono abilitare i criteri di protezione delle app (noti come criteri MAM) nelle loro app iOS e Android usando lo strumento di wrapping delle app di Intune o Intune App SDK.

Sono stati aggiornati gli articoli seguenti:

* [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune)
* [Preparare le app per iOS per la gestione delle app mobili con lo strumento di wrapping delle app di Intune](https://docs.microsoft.com/intune/deploy-use/prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool)
* [Introduzione a Microsoft Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-get-started)
* [Manuale dello sviluppatore di Intune App SDK per iOS](https://docs.microsoft.com/intune/develop/intune-app-sdk-ios)

Gli articoli seguenti sono stati aggiunti alla raccolta della documentazione:

* [Plug-in Cordova per Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-cordova)
* [Componente Xamarin per Intune App SDK](https://docs.microsoft.com/intune/develop/intune-app-sdk-xamarin)

### <a name="progress-bar-when-launching-the-company-portal-on-ios---665978--"></a>Indicatore di stato quando si avvia l'app Portale aziendale in iOS <!--665978-->
Nell'app Portale aziendale per iOS verrà introdotta una barra di stato nella schermata di avvio per fornire all'utente informazioni sui processi di caricamento eseguiti. L'implementazione della barra di stato in sostituzione dell'indicatore di stato rotante avverrà in modo graduale. Questo significa che alcuni utenti visualizzeranno la nuova barra di stato, mentre altri continueranno a vedere l'indicatore rotante.

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune).

Per qualsiasi domanda in merito alla tempistica per la migrazione del tenant, contattare il team Microsoft responsabile della migrazione all'indirizzo [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="january-2017"></a>Gennaio 2017

#### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.

#### <a name="assign-line-of-business-apps-whether-or-not-devices-are-enrolled---748803--"></a>Assegnare app line-of-business indipendentemente dalla registrazione dei dispositivi <!--748803-->
È ora possibile assegnare app line-of-business e app dallo store agli utenti, indipendentemente dal fatto che i loro dispositivi siano o meno registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale.

### <a name="december-2016"></a>Dicembre 2016

#### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integrazione della gestione delle spese di telecomunicazione nell'anteprima pubblica del portale di Azure<!--747605-->
Stiamo iniziando a presentare in anteprima l'integrazione con i servizi di gestione delle spese di telecomunicazione di terze parti nel portale di Azure. È possibile usare Intune per imporre limiti al consumo dei dati sia nazionale che in roaming. Queste integrazioni iniziano con [Saaswedo](http://www.saaswedo.com). Per abilitare questa funzionalità nel tenant di prova, [contattare il supporto tecnico Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Dec16_HO4-->


