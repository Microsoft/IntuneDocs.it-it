---
ms.openlocfilehash: dc86f2c22410236368753acd4dd3b66698037241
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57736848"
---

Questi avvisi forniscono importanti informazioni che consentono di preparare per la funzionalità e le modifiche future di Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Modificare la registrazione del flusso di lavoro con il portale aziendale di Intune nei dispositivi iOS aziendali l'autenticazione con Assistente configurazione <!-- 1927359 -->
È presente una modifica imminente del flusso di lavoro per la registrazione dei dispositivi iOS tramite uno dei metodi registrazione di Apple dispositivo aziendale - di Apple Configurator, il gestore di Business di Apple, Apple School Manager o Apple Device Enrollment Program (DEP), quando si usa il programma di installazione Assistente per l'autenticazione. Questa modifica si applica solo ai dispositivi registrati con l'affinità utente.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Quando questa modifica sarà implementata in ~~marzo~~ aprile, i profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Sarà presente un flusso di lavoro migliorato per registrare i dispositivi iOS tramite i metodi elencati in precedenza. Nota:

- Quando la registrazione dei dispositivi nuovi e l'autenticazione con Assistente configurazione, sarà possibile scegliere di distribuire automaticamente l'app portale aziendale o meno. Gli utenti finali non saranno più vedranno la schermata "Identificazione del dispositivo" e la schermata di "Conferma del dispositivo" nel flusso di registrazione.  
- Nei dispositivi già registrati tramite Assistente configurazione tramite uno dei metodi di registrazione dei dispositivi aziendali di Apple, è necessario eseguire l'azione se si desidera abilitare l'accesso condizionale. È possibile configurare i criteri di configurazione con un formato xml specifico per effettuare il push down questi dispositivi l'App portale aziendale. Le direzioni per eseguire questa operazione sono nel post di blog facendo clic sul collegamento informazioni aggiuntive. Se si sceglie di eseguire il push l'App portale aziendale in questo modo, gli utenti finali non saranno più vedranno la schermata "Identificazione del dispositivo" e la schermata di "Conferma del dispositivo" nel flusso di registrazione. 
- Dopo che viene implementata questa modifica, se è stata ancora distribuita l'App portale aziendale con il profilo di configurazione app indicato in precedenza e se gli utenti finali download archiviare l'app portale aziendale dall'App, sarà possibile accesso, ma verrà visualizzato un messaggio di errore. Non saranno in grado di usare l'app per l'accesso condizionale. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Se si prevede di usare il flusso di lavoro modificato, è necessario aggiornare le linee guida per utenti finali per indicare che:

- Gli utenti finali non vedranno le due schermate indicato in precedenza nel flusso di registrazione. 
- Sarà necessario eseguire l'accesso al portale aziendale quando viene distribuito automaticamente e non scaricarlo dall'app store. 

È possibile creare un criterio di configurazione di app ora, se necessario, in preparazione per la modifica. Quando questo nuovo flusso di lavoro esegue il roll, si noterà i profili di registrazione aggiornata nella console. Si verrà inoltre inviata una comunicazione di questa implementazione tramite il centro messaggi. Successivamente, è necessario intraprendere l'azione in modo che gli utenti finali possono registrare tramite DEP autenticandosi con Assistente configurazione ed è possibile usare il portale aziendale per l'accesso condizionale.

Vedere il blog di supporto post facendo clic sul collegamento informazioni aggiuntive per altri dettagli su questa modifica.

#### <a name="additional-information"></a>Informazioni aggiuntive 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="company-portal-changes-for-ios-122-enrollment-in-intune"></a>Modifiche del portale aziendale per iOS 12.2 registrazione in Intune
Come annunciato in MC172534, Apple ha annunciato alcune modifiche relative alla registrazione dei dispositivi iOS nei servizi di gestione di dispositivi mobili (MDM). La modifica verrà probabilmente in versione di iOS in arrivo nel mese di marzo 2019, nonché tutte le versioni future di iOS. Stiamo rendendo alcuni aggiornamenti nel portale aziendale in modo da riflettere le modifiche di Apple. 
 
#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se gli utenti finali aggiornano i propri dispositivi a iOS 12.2 e versioni successive, sa che un flusso di lavoro modificato è ed è necessario eseguire passaggi aggiuntivi per completare la registrazione in Intune. Dopo l'aggiornamento di marzo a Intune, ecco cosa verrà fare:  

- Avviare il processo di registrazione nell'app portale aziendale per scaricare un profilo di gestione
- Passare a Impostazioni > generali > profili e cercare una notifica badge rosso
- Selezionare il profilo corretto e fare clic per installare
- Tornare al portale aziendale per completare la registrazione

Per informazioni dettagliate sul flusso di registrazione, fare clic su informazioni aggiuntive.

Non deve dipendere a meno che desidera annullare la registrazione e necessario una registrazione aggiornata, i dispositivi iOS registrati e di eseguire l'aggiornamento alla versione 12.2 già presenti e versioni successive. L'esperienza di registrazione nei dispositivi che eseguono iOS 12.1 o versioni precedenti non verrà modificata con questa nuova versione da Apple. I dispositivi registrati tramite uno o i metodi di registrazione aziendali di Apple (Device Enrollment Program, Apple School Manager o il gestore di Business di Apple) non saranno interessati.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
È consigliabile aggiornare la documentazione e le indicazioni per gli utenti finali. È anche consigliabile informare il supporto tecnico di queste modifiche. Conserveremo informati tramite la pagina delle novità quando questa modifica viene resa disponibile. 

Se si desidera sfruttare le modifiche di portale aziendale verrà introdotta, chiedere agli utenti di aggiornare il dispositivo per la nuova versione di iOS dopo l'aggiornamento di marzo di Intune di servizio quando il portale aziendale 3.9.0 versione dell'app. viene rilasciato.

Fare clic su informazioni aggiuntive per un post di blog di supporto con screenshot di anteprima delle modifiche portale aziendale.

Altre informazioni [https://aka.ms/CP_changes_iOS12](https://aka.ms/CP_changes_iOS12)

### <a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Modifiche pianificate: modifica del flusso di lavoro per la registrazione di iOS 12 in Intune
Apple ha annunciato alcune modifiche relative alla registrazione dei dispositivi iOS nei servizi di gestione di dispositivi mobili (MDM). La modifica sarà probabilmente presente nella versione di iOS della primavera 2019 e in tutte le versioni future di iOS.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se gli utenti finali eseguono l'aggiornamento dei propri dispositivi a questa nuova versione di iOS 12 in primavera, ricordare che è presente un flusso di lavoro modificato ed è necessario eseguire passaggi aggiuntivi per completare la registrazione in Intune. Quando Apple sono state introdotte queste modifiche, sarà necessario agli utenti finali:

- Avviare il processo di registrazione nell'app portale aziendale per scaricare un profilo di gestione
- Passare a Impostazioni > generali > profili
- Selezionare il profilo corretto e fare clic per installare
- Tornare al portale aziendale per completare la registrazione 

A meno che non si tratti di dispositivi non registrati e che quindi richiedono una registrazione da zero, questa operazione non interessa i dispositivi già registrati e aggiornati alla nuova versione di iOS.

L'esperienza di registrazione nei dispositivi che eseguono iOS 12.1 o versioni precedenti non verrà modificata con questa nuova versione da Apple.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
È consigliabile aggiornare la documentazione e le indicazioni per gli utenti finali. È anche consigliabile informare il supporto tecnico di queste modifiche. Vi informeremo tramite il Centro messaggi e la pagina delle novità quando questa modifica verrà resa disponibile.

#### <a name="additional-information"></a>Informazioni aggiuntive
[Il supporto post di blog con schermate e video del flusso di registrazione prevista](https://aka.ms/iOS_enrollment_changes).

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Modifica prevista: aggiornamento dell'esperienza utente all'app Portale aziendale Intune per iOS
Siamo lieti di annunciare che Intune presto rilascerà un importante aggiornamento dell'esperienza utente all'app Portale aziendale per iOS. L'aggiornamento offrirà una riprogettazione visuale della home page con filtri avanzati e un accesso più rapido ad applicazioni e libri.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
L'aggiornamento dell'esperienza utente, pur conservando le attuali funzionalità del portale aziendale per iOS, conterrà quanto segue:
- Una home page con aspetto di iOS nativo 
- Funzionalità di filtro per gli elenchi di contenuti e ricerca, tra cui la possibilità di filtrare in base al tipo di contenuto (app o eBook) e alla disponibilità (gestione dei dispositivi obbligatoria o disponibile senza registrazione)
- Possibilità di cercare gli eBook
- Cronologia di ricerca per le App e gli eBook

Se si fa parte del programma Apple TestFlight, si riceverà una notifica sulla versione non definitiva dell'app Portale aziendale per iOS aggiornata di Intune quando diventa disponibile. Se non si fa parte del programma Apple TestFlight, si è ancora in tempo per registrarsi. La registrazione consente di usare l'app Portale aziendale aggiornata prima che sia disponibile per gli utenti finali. Si sarà possibile anche fornire commenti e suggerimenti direttamente al team di Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Non è necessario intraprendere alcuna azione. Queste modifiche verranno rilasciate in una versione imminente dell'app Portale aziendale per iOS. 

#### <a name="additional-information"></a>Informazioni aggiuntive
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors----3105122---"></a>Promemoria: Rimozione di esistente Exchange Online per i connettori di Intune <!-- 3105122 -->
In MC165575, è stato annunciato che, potrebbe essere rimosse Exchange Online a funzionalità del connettore Intune 'Service to Service' in un aggiornamento futuro. Con l'aggiornamento di febbraio al servizio Intune, verrà disattivato il pulsante per impostare i nuovi connettori. Ma è previsto rimuovere tutti i esistente Exchange Online per i connettori di Intune in marzo 2019.
 
#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Questo messaggio verrà ricevuto dai clienti che risultano usare la funzionalità del connettore 'da servizio a servizio' nel loro ambiente. Il connettore 'da servizio a servizio' supporta solo la gestione di Intune dei dispositivi Exchange Active Sync per Exchange Online e non supporta l'infrastruttura locale. Questo connettore, a causa del modo in cui è visualizzato nella console, sembra necessario per l'accesso condizionale, ma in realtà non è richiesto. Si potrebbe usano questo connettore per comprendere l'utilizzo di Exchange Online prima di applicare l'accesso condizionale. Queste informazioni sono già fornite per il centro di amministrazione di Microsoft 365. In questo caso, troverai fornisce report di utilizzo per il tipo Exchange Online tra cui l'app usata per tra 7 e 180 giorni. Per altre informazioni, vedere [Office 365 report nell'interfaccia di amministrazione - utilizzo di App di posta elettronica](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage?view=o365-worldwide).  
 
Se si usano questi connettori nel proprio ambiente, non sarà possibile monitorare o cancellare i dispositivi Exchange Active Sync in Intune dopo la disabilitazione dei connettori in febbraio. Durante questa modifica non è previsto alcun impatto per gli utenti finali.
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Se è stato configurato il connettore da servizio a servizio e l'ambiente include dispositivi Exchange Active Sync, passare ad altri metodi per la gestione dei dispositivi. Sono disponibili le seguenti opzioni:

- Registrare i dispositivi nella gestione dei dispositivi mobili (MDM) 
- Usare i criteri di Protezione app di Intune per gestire i dispositivi 
- Usare i controlli di Exchange come descritto nella documentazione disponibile [qui](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) 

#### <a name="additional-information"></a>Informazioni aggiuntive  
https://docs.microsoft.com/intune/exchange-service-connector-configure




### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>Controllare l'impostazione "Visibility ritardo degli aggiornamenti Software" in Intune 

È stato annunciato in MC171466 che abbiamo stavamo muove alcune impostazioni nella console. Con l'aggiornamento di marzo a Intune, si sarà rimuovere completamente l'impostazione "Visibilità di ritardo del Software aggiornamenti" nel pannello dei criteri di aggiornamento iOS. Ciò non modifica il modo in cui si applicano gli aggiornamenti software pianificati ma può influire su quanto tempo la visibilità di un aggiornamento viene ritardata per gli utenti finali. Potrebbe essere necessario intervenire prima della fine del mese di marzo, se si usa questa impostazione. 

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Dopo l'aggiornamento del servizio Intune di febbraio, si noterà che viene visualizzata l'impostazione che entrambi nei profili di restrizione di dispositivo nella console e in iOS aggiornare i criteri nel Pannello di aggiornamento Software. Quando viene visualizzata questa modifica riflessa nella console, ecco ciò che potrebbe essere necessario eseguire.

- Per i criteri esistenti di aggiornamento per iOS: se si dispone di personalizzato configurato questa impostazione su un valore qualsiasi diverso da quello predefinito 30 giorni e vuole che le configurazioni esistenti per l'impostazione di visibilità di ritardo continuare ad applicare dopo la fine del mese di marzo, sarà necessario creare un nuovo profilo di restrizione del dispositivo iOS. In questo caso, l'impostazione di visibilità del ritardo dovrà avere gli stessi valori come i criteri di aggiornamento iOS esistenti e assegnare agli stessi gruppi. Dopo l'aggiornamento di marzo del servizio, non sarà possibile modificare i valori per questa impostazione nei criteri di aggiornamento iOS esistenti poiché non sarà visibile in questo pannello. Al contrario si configurerà questa impostazione nei profili di nuovo.
  Se il valore per il numero di giorni è possibile ritardare la visibilità non corrispondono in entrambe le posizioni per i valori personalizzati impostazione configurata, la visibilità di ritardo di impostazione non funziona, e gli utenti finali visualizzeranno l'aggiornamento nei propri dispositivi, non appena è disponibile. Ciò può avere un impatto minimo per la maggior parte dei clienti, poiché le altre impostazioni nel pannello dei criteri di aggiornamento Software ha sempre la precedenza rispetto a questa impostazione nella console.
- Per i nuovi criteri di aggiornamento per iOS: se si prova a creare nuovi criteri nel pannello degli aggiornamenti Software dopo l'aggiornamento del servizio Intune febbraio, vedrete questa impostazione di grigio. Verrà visualizzata una nota nella console di reindirizzamento al pannello di configurazione del dispositivo se si desidera ritardare la visibilità degli aggiornamenti.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Non devi intraprendere l'azione se si non usa questa impostazione o non si desidera ritardare la visibilità degli aggiornamenti software per gli utenti finali.

Se si desidera ritardare la visibilità degli aggiornamenti, iniziare a configurare l'impostazione in nuovi profili nel Pannello di configurazione del dispositivo in limitazioni del dispositivo > generale. Se hai custom questa impostazione configurata nel iOS esistenti i criteri di aggiornamento, creare un nuovo profilo di restrizione di un dispositivo equivalente con lo stesso valore per "days" ritardare la visibilità degli aggiornamenti per gli utenti, dopo la versione di febbraio e prima di marzo del aggiornamento esegue il roll. 

È possibile aggiornare il materiale sussidiario per professionisti IT e informare il supporto tecnico.

Vedere il blog di supporto post a informazioni aggiuntive per informazioni dettagliate su come configurare questa impostazione.

#### <a name="additional-information"></a>Informazioni aggiuntive 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)
