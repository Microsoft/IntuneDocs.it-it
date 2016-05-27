---
# required metadata

title: Sviluppi futuri | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/03/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Sviluppi futuri in Microsoft Intune
Queste informazioni sono fornite con accordo di riservatezza su base estremamente limitata e sono soggette a modifiche. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al referente di Intune/PM.

Questa pagina viene aggiornata periodicamente. Controllare regolarmente la pagina per conoscere gli sviluppi futuri.

Le seguenti modifiche di Intune sono in fase di sviluppo. Tutte queste funzionalità saranno supportate anche per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, consultare la nostra [pagina delle Novità in arrivo per le funzionalità ibride](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Acquisizione del centro messaggi
Come parte della migrazione di Intune nel [portale di gestione di Office 365](https://portal.office.com/), inizieremo a sfruttare il suo centro messaggi per comunicare le nuove funzionalità e altre notifiche.  Inoltre, installando l'app complementare per dispositivi mobili Office 365 Admin, è possibile ricevere notifiche sul cellulare e inoltrare facilmente qualsiasi messaggio agli utenti o a un alias di distribuzione.<br>  
Inizieremo a usare il centro messaggi con la nostra versione di maggio per notificare quando gli aggiornamenti sono completati e includeremo informazioni sulle funzionalità di Intune nuove e migliorate.  Visitare il centro messaggi oggi stesso eseguendo l'accesso al [portale di gestione di Office 365](https://portal.office.com/) e scegliendo l'opzione **CENTRO MESSAGGI** nel riquadro di spostamento a sinistra.
<!---TFS 1242782--->


## Gestione delle app
- **Accesso condizionale per il browser** Sarà possibile impostare un criterio di accesso condizionale per Exchange Online e SharePoint Online in modo che siano accessibili solo da dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere a siti di Outlook Web Access (OWA) e SharePoint e con dispositivi iOS e Android verrà richiesto di registrare il dispositivo con Intune oltre che di risolvere eventuali problemi di non conformità prima di poter completare l'accesso.
<!---TFS 1175844--->

- **MAM SDK: supporto per la configurazione della lunghezza del PIN.** Sarà possibile specificare la lunghezza del PIN per le app MAM in modo simile al PIN di un dispositivo. Gli utenti finali dovranno perciò conformarsi alle nuove limitazioni imposte. Vedranno la schermata del PIN leggermente modificata per tenere conto della lunghezza del PIN.
<!--- TFS 1104753--->

- **MAM controlla per impedire la sincronizzazione dei contatti di Outlook (iOS).** È disponibile una nuova impostazione per la gestione delle applicazioni mobili senza registrazione del dispositivo. Questa impostazione consente all'amministratore di Intune di impedire a un'applicazione di sincronizzare i contatti con la rubrica nativa nei dispositivi iOS. Quando l'impostazione è abilitata, l'applicazione non potrà più salvare i contatti nella rubrica nativa. Quando l'impostazione è disabilitata, l'applicazione potrà salvare i contatti nella rubrica nativa. Quando un amministratore di Intune cancella un dispositivo in modo selettivo, tutti i contatti che sono già stati salvati nella rubrica nativa verranno rimossi. Questa nuova impostazione è ora supportata dall'applicazione Outlook sui dispositivi iOS.
<!---TFS item 1276166--->

- **Skype for Business per Android.** Gli amministratori di Intune possono ora scegliere come destinazione Skype for Business con MAM senza criteri di registrazione.  Una volta che gli utenti sono connessi, verranno applicati i criteri MAN.
<!--- TFS item 1248444 --->

- **Skype for Business per iOS.** Gli amministratori di Intune possono ora scegliere come destinazione Skype for Business con MAM senza criteri di registrazione.  Una volta che gli utenti sono connessi, verranno applicati i criteri MAN.
<!--- TFS item 1248443 --->

### Supporto di Xamarin
Microsoft Intune App SDK ora supporta le app Xamarin in questi scenari:

- Scrittura di nuove app o modifica del codice di app line of business esistenti mediante l'SDK di Intune. È possibile ottenere il plug-in sulla pagina [Microsoft Intune Github](https://github.com/msintuneappsdk).
- Aggiunta del supporto MAM ad app line of business esistenti mediante lo strumento di wrapping delle app di Intune

Per informazioni su come scegliere il metodo da usare, vedere [Stabilire come preparare le app per la gestione delle applicazioni mobili con Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## Gestione dei dispositivi
- **Sessioni di assistenza remota per i PC Windows.** L'integrazione di TeamViewer per PC Windows gestiti da agenti desktop consentirà di stabilire sessioni di assistenza remota con i computer Windows gestiti da agenti desktop a supporto dei reparti di assistenza all'utente finale. Sono inclusi Windows 7, 8, 8.1 e Windows 10.
<!--- TFS 1284856--->


<!--- TFS item 1274326 --->

## Controllo di accesso
* **Skype for Business Online supporta l'accesso condizionale.** Gli amministratori di Intune potranno impostare un criterio di accesso condizionale per Skype for Business Online in modo che sia accessibile solo da dispositivi gestiti e conformi iOS e Android. Agli utenti finali che tentano di accedere all'applicazione per dispositivi mobili Skype for Business in iOS e Android sarà chiesto di registrarsi con Intune e di risolvere eventuali problemi di non conformità per poter completare l'accesso.
<!---TFS item 1254499--->

## Portale aziendale
* **Il banner di identificazione del dispositivo fornirà maggiori informazioni agli utenti finali.** Gli utenti finali potranno identificare facilmente il dispositivo che hanno selezionato durante l'utilizzo del sito Web del Portale aziendale. Se selezioneranno il dispositivo sbagliato, potranno scegliere quello corretto toccando il collegamento "Toccare qui" nel banner della pagina iniziale.
<!--- TFS 1231157--->

* **Pacchetti delle app Windows disponibili direttamente dal Portale aziendale**: gli utenti dei PC Windows 8, Windows 8.1 e Windows RT ora possono installare i pacchetti delle app Windows (con estensione AppX) direttamente dal sito Web del Portale aziendale. In precedenza, gli amministratori di Intune dovevano distribuire o gli utenti dovevano installare l'app del Portale aziendale sui loro dispositivi per poter installare le app.
<!--- TFS item 1082481 --->

* **Gli utenti possono bloccare il dispositivo da remoto dal Portale aziendale** Una nuova opzione di blocco remoto è stata aggiunta al sito Web del Portale aziendale per consentire agli utenti finali di bloccare da remoto il dispositivo dal portale se il dispositivo viene smarrito o rubato. La tabella seguente riporta i dettagli relativi al supporto della piattaforma per il blocco remoto per Intune e Intune con Configuration Manager.
<!--- TFS item 1195661 --->

|Piattaforma  |Dettagli sul supporto|
|---------|---------|
|iOS | Supportato|
|Android | Supportato|
|Windows Phone 8.1 | Supportato|
|Windows 10 Mobile | Supportato solo se il telefono ha un passcode impostato|
|PC (Windows 8.0 e versioni precedenti) | Non supportato|
|PC (Windows 8.1) | Non supportato|
|Windows Phone 8.0 | Non supportato|
|Windows 10 Desktop | Non supportato|

## Deprecazione del servizio
* **Rimozione della capacità di scegliere gruppi personalizzati come destinazione delle regole di notifica.** All'inizio di giugno 2016 non sarà più possibile usare la Creazione guidata regola di notifica per scegliere gruppi creati dall'utente come destinazione per le regole di notifica.

    Attualmente, per selezionare come destinazione un gruppo creato dall'utente dalla console di amministrazione di Microsoft Intune, è necessario scegliere **Amministrazione** > **Regole di notifica** > **Crea nuova regola**. Nel secondo passaggio della Creazione guidata regola di notifica è necessario selezionare i gruppi di dispositivi a cui sarà destinata la regola. Questo passaggio, **Seleziona gruppi di dispositivi**, sarà deprecato dalla console di Intune.

    **Seleziona gruppi di dispositivi** non sarà più supportato dopo la release 1606 di giugno di Intune. L'opzione rimarrà però visibile fino ad agosto 2016. Dopo agosto verrà avviato il passaggio graduale per i nostri tenant alla nuova esperienza, per un periodo di due mesi. Da ottobre 2016 tutti i clienti esistenti dovrebbero passare alla nuova esperienza. Dopo la migrazione alla nuova esperienza, l'opzione per scegliere un gruppo specifico come destinazione per le regole di notifica non dovrebbe più essere visibile.
<!---   TFS 1278864--->







### Vedere anche
Vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).


<!--HONumber=May16_HO1-->


