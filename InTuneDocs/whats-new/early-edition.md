---
title: Edizione anticipata | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/13/2017
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
ms.sourcegitcommit: d0b3a883bb307fb06cb8d16500798086f328314a
ms.openlocfilehash: eeebf8b6b3bc5c7c35386eb20c96097af1f6769c
ms.lasthandoff: 02/14/2017


---


# <a name="the-early-edition-for-microsoft-intune---february-2017"></a>Edizione anticipata per Microsoft Intune - Febbraio 2017

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
> Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="modernizing-the-company-portal-website---753980--"></a>Aggiornamento del sito Web del portale aziendale <!--753980-->
A partire da febbraio, il design del sito Web del portale aziendale verrà allineato agli altri prodotti e servizi Microsoft tramite una nuova combinazione di colori a contrasto, illustrazioni dinamiche e un "hamburger menu" ![immagine di "hamburger menu" di piccole dimensioni inserita nell'angolo superiore sinistro del sito Web del portale aziendale](./media/CP_hamburger_menu.png) che conterrà i dettagli di contatto del supporto tecnico e le informazioni sui dispositivi gestiti esistenti. La pagina di destinazione verrà riorganizzata per evidenziare le applicazioni disponibili per gli utenti, con sequenze video per le app in primo piano e aggiornate di recente. Le immagini di prima e dopo sono disponibili nella [pagina degli aggiornamenti dell'interfaccia utente](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Nuova esperienza guidata per il portale aziendale di Windows 10 <!--713927-->
A partire da marzo, il portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate e personalizzate, per la compilazione di Windows 10 in uso, che guidano l'utente nella procedura di registrazione AAD (obbligatoria per l'identificazione per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale ed è facoltativa. Gli utenti possono continuare a usare l'app anche se non completano la registrazione, ma potrebbero disporre di funzionalità limitate.

###

## <a name="notices"></a>Notifiche

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migrazione dei gruppi non richiederà aggiornamenti ai gruppi o ai criteri per i dispositivi iOS <!--898837-->
Per ogni gruppo di dispositivi Intune preassegnato da un profilo Registrazione di dispositivi aziendali, verrà creato un gruppo di dispositivi dinamico corrispondente in AAD basato sul nome del profilo Registrazione di dispositivi aziendali durante la migrazione ai gruppi di dispositivi di Azure Active Directory. In questo modo i dispositivi registrati vengono automaticamente raggruppati e ricevono gli stessi criteri e le app del gruppo Intune originale.

Quando un tenant entra nel processo di migrazione per la creazione del gruppo e la selezione della destinazione, Intune crea automaticamente un gruppo AAD dinamico corrispondente a un gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali. Se l'amministratore Intune elimina il gruppo Intune di destinazione, il gruppo AAD dinamico corrispondente non viene eliminato. I membri del gruppo e la query dinamica vengono cancellati, ma il gruppo viene mantenuto fino a quando l'amministratore IT non lo rimuove tramite il portale AAD.

Analogamente, se l'amministratore IT modifica il gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali, Intune crea un nuovo gruppo dinamico che riflette la nuova assegnazione del profilo ma non rimuove il gruppo dinamico creato per l'assegnazione precedente.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nuovo indirizzo del server MDM per i dispositivi Windows <!--893007-->
Gli utenti di Windows e Windows Phone che tentano di registrare un dispositivo non riusciranno a eseguire la registrazione se immettono __manage.microsoft.com__ come indirizzo del server MDM (se richiesto). L'indirizzo del server MDM __manage.microsoft.com__ è sostituito da __enrollment.manage.microsoft.com__. Comunicare agli utenti di immettere __enrollment.manage.microsoft.com__ come indirizzo del server MDM per la registrazione di un dispositivo Windows o Windows Phone. Questo aggiornamento richiede che ogni CNAME in DNS che reindirizza __EnterpriseEnrollment.contoso.com__ a __manage.microsoft.com__ venga sostituito da un CNAME in DNS che reindirizza __EnterpriseEnrollment.contoso.com__ a __EnterpriseEnrollment-s.manage.microsoft.com__. Per altre informazioni su questa modifica, visitare [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622-->
A partire da marzo, l'app Portale aziendale per Android seguirà le [linee guida di progettazione dei materiali](https://material.io/guidelines/material-design/introduction.html) per creare un aspetto più moderno. La nuova esperienza utente include i seguenti miglioramenti:

* __Colori__: i colori delle intestazioni delle schede possono essere impostati in base alla tavolozza dei colori personalizzata.
* __Interfaccia__: i pulsanti App in evidenza e Tutte le app sono stati aggiornati nella scheda App. Il pulsante Cerca è ora un pulsante di azione mobile.
* __Navigazione__: Tutte le app mostra una visualizzazione a schede di In evidenza, Tutte e Categorie per una navigazione più semplice.
* __Servizio__: la leggibilità delle schede Dispositivi personali e Contatta l'IT è stata migliorata.

Le immagini di prima e dopo sono disponibili nella [pagina degli aggiornamenti dell'interfaccia utente](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Associare più strumenti di gestione con Windows Store per le aziende <!--926135-->
Se si usa più di uno strumento di gestione per distribuire le app di Windows Store per le aziende, in precedenza era possibile associare soltanto un'app a Windows Store per le aziende. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager. Per informazioni dettagliate, vedere [Gestire le app acquistate in Windows Store per le aziende con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure---736542--"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune).

Per qualsiasi domanda in merito alla tempistica per la migrazione del tenant, contattare il team Microsoft responsabile della migrazione all'indirizzo [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="february-2017"></a>Febbraio 2017

#### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilità di limitare la registrazione di dispositivi mobili <!--747600, 795782-->
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.

* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.  
* Solo per iOS e Android è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).

#### <a name="view-all-actions-on-managed-devices---677150--"></a>Visualizzare tutte le azioni nei dispositivi gestiti <!--677150-->
Il nuovo report __Azioni del dispositivo__ mostra gli utenti che hanno eseguito azioni remote come il ripristino delle impostazioni predefinite nei dispositivi e lo stato dell'azione.

#### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->
Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

#### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](/intune-azure/manage-apps/add-apps) (Come aggiungere un'app in Intune).

#### <a name="display-device-categories---814654--"></a>Visualizzare le categorie di dispositivi <!--814654-->
È ora possibile visualizzare la categoria dei dispositivi come colonna dell'elenco dei dispositivi. È inoltre possibile modificare la categoria nella sezione delle proprietà del pannello delle proprietà del dispositivo.

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

