---
title: Sviluppi futuri | Microsoft Intune
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecf43b38e9593375981770583220d4ce2dfd709f
ms.openlocfilehash: b5da0aca366a24f2f0ccf62a3661b0b91db9b01a


---

# Sviluppi futuri in Microsoft Intune - Agosto
Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Controllare regolarmente la pagina per conoscere gli sviluppi futuri.

Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Gestione delle app
### App nascoste e mostrate per iOS 9.3
Per i dispositivi supervisionati che eseguono iOS 9.3 o versioni successive sarà possibile usare gli elenchi di app nascoste e visualizzate nei criteri di configurazione generale di iOS per:
- Specificare un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
- Specificare un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.

Le app selezionabili includono sia le app distribuite che le app predefinite per iOS, ad esempio i Messaggi e Note.
<!---TFS 1279009--->

### Criteri delle app consentite e bloccate per i dispositivi Samsung KNOX

È ora possibile configurare un criterio personalizzato per i dispositivi Samsung KNOX che consente di creare:
- Un elenco di app la cui esecuzione è bloccata nel dispositivo. Anche se installata, un'app presente nell'elenco delle app bloccate non può essere attivata nel dispositivo.
- Un elenco di app che gli utenti del dispositivo sono autorizzati a installare da Google Play Store. Le altre app dello Store non possono essere installate.

Queste impostazioni possono essere usate solo dai dispositivi che eseguono Samsung KNOX.
<!--- For details, see [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md)--->
<!---TFS 1311629 --->

### Nuove app compatibili con i criteri di gestione di applicazioni mobili (MAM)
L'applicazione di Yammer per [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) sarà compatibile con i [criteri di gestione di applicazioni mobili di Intune](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune) a prescindere che il dispositivo sia o meno registrato.

Per un elenco completo di app MAM compatibili, vedere il sito dei [partner che forniscono applicazioni per Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336--->

## Gestione dei dispositivi
### Supporto per Android 7.0
Nel mese di agosto verrà fornito il supporto immediato (Day 0) per l'imminente sistema operativo Android 7.0 per dispositivi mobili.
<!---TFS 1262053--->
### Rimozione di Google della funzionalità di reimpostazione remota del passcode nei dispositivi Android 7.0
Google sta rimuovendo la possibilità per gli amministratori IT e gli utenti finali di reimpostare in modalità remota il passcode dei dispositivi Android 7.0. In precedenza, gli amministratori IT potevano reimpostare in modalità remota il passcode di un utente e gli utenti finali potevano reimpostare i propri passcode dal sito Web del portale aziendale.

## Gestione dei gruppi
### Transizione dai gruppi di Intune ai gruppi di Azure Active Directory a partire dal mese di settembre 2016
Intune sta creando una nuova esperienza di gestione dei gruppi che usa i gruppi di sicurezza di Azure Active Directory (AAD) come gruppi di utenti e dispositivi in Intune. Questi gruppi verranno usati per la gestione dei gruppi, la distribuzione dei criteri e la distribuzione dei profili **con l'introduzione del nuovo portale di amministrazione di Intune basato su Azure**.

Questa nuova esperienza consentirà di evitare di duplicare i gruppi tra i servizi, **garantirà l'accesso ad alcune nuove funzionalità dei gruppi di Azure Active Directory Premium (AADP)** e offrirà estendibilità tramite PowerShell e Graph. Consentirà inoltre di unificare l'esperienza di gestione dei gruppi per tutta la gestione della mobilità aziendale.

Per abilitare il passaggio ai gruppi di sicurezza, la **console di amministrazione corrente** verrà sottoposta ad alcune modifiche. **Queste modifiche e l'uso dei gruppi di sicurezza di AAD saranno indicati nella documentazione di Intune**.

I clienti che non hanno familiarità con Intune visualizzeranno **alcune delle modifiche ai gruppi di sicurezza prima di dei tenant correnti**.

Oltre alle modifiche apportate alla gestione dei gruppi, **verranno deprecate le funzionalità seguenti**:
- Esclusione di membri o gruppi durante la creazione di un nuovo gruppo
- Gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati**
- **Gestisci gruppi** nel ruolo di amministratore del servizio
- Avvisi personalizzati in base al gruppo per le regole di notifica
- Calcolo pivot per gruppi nei report
<!--- TFS 1295329--->

## Deprecazione del servizio
### Le app del portale aziendale per Windows 8 e Windows Phone 8 verranno deprecate a partire da settembre 2016
A partire da ottobre 2016, il supporto di Microsoft Intune per le app del portale aziendale di Windows Phone 8 e Windows 8 verrà deprecato. Verrà anche deprecato il supporto di Microsoft Intune per la piattaforma Windows Phone 8. Di conseguenza, non sarà possibile registrare o aggiornare i dispositivi Windows Phone 8. È possibile continuare a gestire i dispositivi Windows Phone 8 e Windows 8 che sono già registrati. Aggiornare i dispositivi Windows Phone 8 e Windows 8 a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi senza interruzioni.
<!---TFS 1255391--->

### Rimozione della capacità di scegliere gruppi personalizzati come destinazione delle regole di notifica
Le regole di notifica di Intune definiscono i destinatari degli avvisi di posta elettronica inviati da Intune. Attualmente è possibile configurare regole di notifica per inviare messaggi di posta elettronica a tutti gli utenti dei dispositivi di un gruppo di dispositivi di Intune creato. A partire da giugno 2016, la scelta dei gruppi creati dall'utente come destinazione non sarà più supportata.

La sequenza temporale preliminare di questa modifica sarà la seguente:
- Da settembre 2016, i nuovi tenant non visualizzeranno più il secondo passaggio della procedura guidata di creazione di una regola di notifica. I tenant esistenti non sono interessati dalla modifica.
- Da ottobre 2016 alcuni tenant esistenti non visualizzeranno più il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.
- Successivamente, nessun tenant visualizzerà più il passaggio "Seleziona gruppi di dispositivi" della procedura guidata.

<!---   TFS 1278864--->
### Modifiche al supporto per l'app Portale aziendale per iOS
Da settembre, tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS dovranno usare la versione più recente dell'app. I nuovi utenti potranno scaricare solo la versione più recente e gli utenti attuali dovranno aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, pertanto gli utenti dei dispositivi che eseguono versioni precedenti di iOS non saranno in grado di usare il portale aziendale o di eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.

<!---TFS 1283165--->


### App visualizzatore di Intune
Con il rilascio della nuova app di condivisione RMS, nel mese di agosto 2016 verranno rimosse le app del visualizzatore di Intune seguenti:
- Visualizzatore AV di Intune
- Visualizzatore PDF di Intune
- Visualizzatore immagini di Intune per Android disponibile in Google Play

Anziché usare le app visualizzatore di Intune, è consigliabile usare la nuova app Rights Management (condivisione RMS) per Android che consente di distribuire un'unica app anziché tre app separate per visualizzare in sicurezza i file aziendali sui dispositivi Android. Altre informazioni sulle [app RMS sharing](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app).
<!--- goes in 1608 What's New--->


### Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Sep16_HO5-->


