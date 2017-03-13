---
title: "Novità | Documentazione Microsoft"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: cb1679deda0ba325ee3bd7288713f12317489006
ms.openlocfilehash: 37d44dc2752815ef7abf47e5d4a658a126892a86
ms.lasthandoff: 02/18/2017


---
# <a name="whats-new-in-microsoft-intune---february-2017"></a>Novità di Microsoft Intune - Febbraio 2017
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

> [!Note]
> Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="modernizing-the-company-portal-website---753980--"></a>Aggiornamento del sito Web del portale aziendale <!--753980-->
Il sito Web del portale aziendale supporterà le app destinate agli utenti che non hanno dispositivi gestiti. Il sito Web verrà allineato ad altri prodotti e servizi Microsoft tramite una nuova combinazione di colori a contrasto, illustrazioni dinamiche e un "hamburger menu" ![immagine di "hamburger menu" di piccole dimensioni inserita nell'angolo superiore sinistro del sito Web del portale aziendale](./media/CP_hamburger_menu.png) che conterrà i dettagli di contatto del supporto tecnico e le informazioni sui dispositivi gestiti esistenti. La pagina di destinazione verrà riorganizzata per evidenziare le applicazioni disponibili per gli utenti, con sequenze video per le app in primo piano e aggiornate di recente. Le immagini di prima e dopo sono disponibili nella [pagina degli aggiornamenti dell'interfaccia utente](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="new-guided-experience-for-windows-10-company-portal---713927--"></a>Nuova esperienza guidata per il portale aziendale di Windows 10 <!--713927-->
A partire da marzo, il portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate e personalizzate, per la compilazione di Windows 10 in uso, che guidano l'utente nella procedura di registrazione AAD (obbligatoria per l'identificazione per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale ed è facoltativa. Gli utenti possono continuare a usare l'app anche se non completano la registrazione, ma potrebbero disporre di funzionalità limitate.

## <a name="notices"></a>Notifiche

### <a name="group-migration-will-not-require-any-updates-to-groups-or-policies-for-ios-devices---898837--"></a>La migrazione dei gruppi non richiederà aggiornamenti ai gruppi o ai criteri per i dispositivi iOS <!--898837-->
Per ogni gruppo di dispositivi Intune preassegnato da un profilo Registrazione di dispositivi aziendali, verrà creato un gruppo di dispositivi dinamico corrispondente in AAD basato sul nome del profilo Registrazione di dispositivi aziendali durante la migrazione ai gruppi di dispositivi di Azure Active Directory. In questo modo i dispositivi registrati vengono raggruppati automaticamente e ricevono gli stessi criteri e le stesse app del gruppo Intune originale.

Quando un tenant entra nel processo di migrazione per la creazione del gruppo e la selezione della destinazione, Intune crea automaticamente un gruppo AAD dinamico corrispondente a un gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali. Se l'amministratore Intune elimina il gruppo Intune di destinazione, il gruppo AAD dinamico corrispondente non viene eliminato. I membri del gruppo e la query dinamica vengono cancellati, ma il gruppo viene mantenuto fino a quando l'amministratore IT non lo rimuove tramite il portale AAD.

Analogamente, se l'amministratore IT modifica il gruppo Intune di destinazione di un profilo Registrazione di dispositivi aziendali, Intune crea un nuovo gruppo dinamico che riflette la nuova assegnazione del profilo ma non rimuove il gruppo dinamico creato per l'assegnazione precedente.

### <a name="defaulting-to-managing-windows-desktop-devices-through-windows-settings---663050--"></a>La gestione dei dispositivi desktop Windows avviene per impostazione predefinita tramite le impostazioni di Windows <!--663050-->
Il comportamento predefinito per la registrazione dei computer desktop di Windows 10 sta cambiando. Per le nuove registrazioni verrà usato il flusso di registrazione dell'agente MDM tipico anziché tramite l'agente per PC. Il sito Web del portale aziendale fornirà agli utenti di desktop Windows 10 istruzioni per la registrazione, che consentono di eseguire in modo guidato il processo di aggiunta di computer desktop Windows 10 come dispositivi mobili. Ciò non influirà su PC già registrati e l'organizzazione può comunque decidere di gestire i desktop Windows 10 con l'agente per PC, [se preferibile](https://docs.microsoft.com/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune).

### <a name="improving-mobile-app-management-support-for-selective-wipe---581242--"></a>Miglioramento del supporto della gestione delle app per dispositivi mobili per la cancellazione selettiva <!--581242-->
Gli utenti finali riceveranno ulteriori indicazioni su come riottenere l'accesso ai dati aziendali o dell'istituto di istruzione se i dati vengono rimossi automaticamente a causa del criterio "Intervallo offline (giorni) prima della cancellazione dei dati dell'app".<!--, or the removal of the Intune Company Portal on Android.-->

### <a name="company-portal-for-ios-links-open-inside-the-app---665954--"></a>I collegamenti al portale aziendale per iOS si aprono all'interno dell'app <!--665954-->
I collegamenti all'interno dell'app Portale aziendale per iOS, inclusi quelli per la documentazione e le app, verranno aperti direttamente nell'app Portale aziendale tramite una visualizzazione in-app di Safari. Questo aggiornamento verrà fornito separatamente rispetto all'aggiornamento del servizio in gennaio.

### <a name="new-mdm-server-address-for-windows-devices---893007--"></a>Nuovo indirizzo del server MDM per i dispositivi Windows <!--893007-->
Gli utenti di Windows e Windows Phone che tentano di registrare un dispositivo non riusciranno a eseguire la registrazione se immettono __manage.microsoft.com__ come indirizzo del server MDM (se richiesto). L'indirizzo del server MDM __manage.microsoft.com__ è sostituito da __enrollment.manage.microsoft.com__. Comunicare agli utenti di immettere __enrollment.manage.microsoft.com__ come indirizzo del server MDM per la registrazione di un dispositivo Windows o Windows Phone. Non sono necessarie modifiche alla configurazione CNAME. Per altre informazioni su questa modifica, visitare [aka.ms/intuneenrollsvrchange](https://aka.ms/intuneenrollsvrchange).

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622-->
A partire da marzo, l'app Portale aziendale per Android seguirà le [linee guida di progettazione dei materiali](https://material.io/guidelines/material-design/introduction.html) per creare un aspetto più moderno. La nuova esperienza utente include i seguenti miglioramenti:

* __Colori__: i colori delle intestazioni delle schede possono essere impostati in base alla tavolozza dei colori personalizzata.
* __Interfaccia__: i pulsanti App in evidenza e Tutte le app sono stati aggiornati nella scheda App. Il pulsante Cerca è ora un pulsante di azione mobile.
* __Navigazione__: Tutte le app mostra una visualizzazione a schede di In evidenza, Tutte e Categorie per una navigazione più semplice.
* __Servizio__: la leggibilità delle schede Dispositivi personali e Contatta l'IT è stata migliorata.

Le immagini di prima e dopo sono disponibili nella [pagina degli aggiornamenti dell'interfaccia utente](https://docs.microsoft.com/intune/whats-new/whats-new-in-intune-app-ui).

### <a name="associate-multiple-management-tools-with-the-windows-store-for-business---926135--"></a>Associare più strumenti di gestione con Windows Store per le aziende <!--926135-->
Se si usa più di uno strumento di gestione per distribuire le app di Windows Store per le aziende, in precedenza era possibile associare soltanto un'app a Windows Store per le aziende. È ora possibile associare più strumenti di gestione allo Store, ad esempio Intune e Configuration Manager. Per informazioni dettagliate, vedere [Gestire le app acquistate in Windows Store per le aziende con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune#associate-your-windows-store-for-business-account-with-intune).

## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novità dell'anteprima pubblica dell'esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/whats-new).

Per qualsiasi domanda in merito alla tempistica per la migrazione del tenant, contattare il team Microsoft responsabile della migrazione all'indirizzo [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

Le novità dell'anteprima di Intune in Azure sono descritte [qui](https://docs.microsoft.com/intune-azure/introduction/whats-new).

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novità dell'anteprima di Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [What's new in the Company Portal UI](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui) (Novità nell'interfaccia utente del portale aziendale)
* [Archivio delle novità](whats-new-archive.md)

