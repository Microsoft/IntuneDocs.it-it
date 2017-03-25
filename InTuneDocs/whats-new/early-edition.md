---
title: Edizione anticipata | Microsoft Docs
description: 
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 1ba0dab35e0da6cfe744314a4935221a206fcea7
ms.openlocfilehash: 3b355d43d4be05535f256d88a8648c2e67035882
ms.lasthandoff: 03/13/2017


---


# <a name="the-early-edition-for-microsoft-intune---march-2017"></a>Edizione anticipata per Microsoft Intune - Marzo 2017

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
> Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622-->

L'interfaccia utente dell'app Portale aziendale per Android verrà aggiornata per offrire un aspetto più moderno e una migliore esperienza utente. Di seguito sono illustrati gli aggiornamenti più significativi:

- Colori: le intestazioni delle schede dell'app Portale aziendale possono avere un colore personalizzato definito dal personale IT.
- App: nella scheda **App** i pulsanti **App in evidenza** e **Tutte le app** sono stati aggiornati.
- Ricerca: nella scheda **App** il pulsante **Cerca** è un pulsante di azione mobile.
- Navigazione tra le app: in **Tutte le app** è disponibile una visualizzazione a schede di **In evidenza**, **Tutte** e **Categorie** per una navigazione più semplice.
- Supporto: le schede **Dispositivi personali** e **Contatta l'IT** sono state aggiornate per migliorare la leggibilità.

Per altre informazioni su queste modifiche, vedere la [pagina degli aggiornamenti dell'interfaccia utente dell'app] (whats-new-in-intune-app-ui.md].

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script di firma per l'app Portale aziendale di Windows 10<!--941642-->

Per i clienti che devono scaricare e trasferire localmente l'app Portale aziendale di Windows 10 è ora disponibile uno script per semplificare e ottimizzare il processo di firma dell'app per l'organizzazione.   Per scaricare lo script e le relative istruzioni d'uso, vedere [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Script di firma di Microsoft Intune per l'app Portale aziendale di Windows 10) nella raccolta TechNet. Per altre informazioni su questo annuncio, vedere [Updating your Windows 10 Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) (Aggiornamento dell'app Portale aziendale di Windows 10) nel blog del team di supporto di Intune. 

## <a name="notices"></a>Notifiche

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Supporto migliorato per gli utenti Android in Cina <!--720444-->

A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere le app dai marketplace cinesi. L'app Portale aziendale supporterà questo flusso di lavoro reindirizzando gli utenti Android in Cina per scaricare le app Portale aziendale e Outlook dagli app store locali. Ciò consentirà di migliorare l'esperienza utente quando sono abilitati i criteri di accesso condizionale, per la gestione dei dispositivi e delle applicazioni mobili. Le app Portale aziendale e Outlook per Android sono disponibili negli app store cinesi seguenti:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->

A partire dalla primavera 2017, Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->

Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

### <a name="improvements-to-device-actions-report---677150--"></a>Miglioramenti al report Azioni del dispositivo <!--677150-->

Le prestazioni del report Azioni del dispositivo sono state migliorate. È inoltre possibile filtrare il report in base allo stato. Si possono ad esempio mostrare solo le azioni del dispositivo che sono state completate.

### <a name="actions-for-non-compliance---730266--"></a>Azioni per la mancata conformità <!--730266-->

Le **azioni per la mancata conformità** sono una nuova funzionalità dei criteri di conformità che consente di intervenire sui dispositivi non conformi. È possibile specificare una o più azioni e il periodo di tempo in cui devono essere eseguite tali azioni. Ad esempio, è possibile segnalare immediatamente agli utenti i dispositivi non conformi non appena diventano non conformi, tramite posta elettronica, oppure è possibile impedire ai dispositivi non conformi di accedere alle risorse aziendali dopo un periodo di tolleranza di 3 giorni tramite l'accesso condizionale.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->

È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Come aggiungere un'app in Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Assegnare app line-of-business agli utenti con dispositivi non registrati <!--748823-->

È ora possibile assegnare app line-of-business dallo store agli utenti, indipendentemente dal fatto che i loro dispositivi siano registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale.

### <a name="new-compliance-reports---846671--"></a>Nuovi report di conformità <!--846671-->

Sono ora disponibili report di conformità che definiscono il comportamento di conformità dei dispositivi in ambito aziendale e consentono di risolvere rapidamente i problemi correlati alla conformità riscontrati dagli utenti. È possibile visualizzare le informazioni seguenti:

- Stato di conformità generale dei dispositivi
- Stato di conformità per una singola impostazione
- Stato di conformità per singoli criteri

È inoltre possibile usare questi report per eseguire il drill-down in un singolo dispositivo e visualizzare impostazioni e criteri specifici che influiscono su tale dispositivo.

### <a name="additional-windows-10-upgrade-paths---903672--"></a>Percorsi di aggiornamento aggiuntivi per Windows 10 <!--903672-->

È ora possibile creare criteri di aggiornamento dell'edizione per aggiornare i dispositivi alle edizioni di Windows 10 seguenti:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->

Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di anteprima di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).

