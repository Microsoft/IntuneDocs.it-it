---
title: includere il file
description: includere il file
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 073115d33f9a4f22fe3706ef15860c2a8d8a68ee
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675494"
---
Questi avvisi forniscono importanti informazioni che consentono di preparare per la funzionalità e le modifiche future di Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Modificare la registrazione del flusso di lavoro con il portale aziendale di Intune nei dispositivi iOS aziendali l'autenticazione con Assistente configurazione <!-- 1927359 -->
È presente una modifica imminente del flusso di lavoro per la registrazione dei dispositivi iOS tramite uno dei metodi registrazione di Apple dispositivo aziendale - di Apple Configurator, il gestore di Business di Apple, Apple School Manager o Apple Device Enrollment Program (DEP), quando si usa il programma di installazione Assistente per l'autenticazione. Questa modifica si applica solo ai dispositivi registrati con l'affinità utente.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Quando questa modifica sarà implementata in ~~marzo~~ aprile, i profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Sarà presente un flusso di lavoro migliorato per registrare i dispositivi iOS tramite i metodi elencati in precedenza. 

- Quando la registrazione dei dispositivi nuovi e l'autenticazione con Assistente configurazione, sarà possibile scegliere di distribuire automaticamente l'app portale aziendale o meno. Gli utenti finali non saranno più vedranno la schermata "Identificazione del dispositivo" e la schermata di "Conferma del dispositivo" nel flusso di registrazione.  
- Nei dispositivi già registrati tramite Assistente configurazione tramite uno dei metodi di registrazione dei dispositivi aziendali di Apple, è necessario eseguire l'azione se si desidera abilitare l'accesso condizionale. È possibile configurare i criteri di configurazione con un formato xml specifico per effettuare il push down questi dispositivi l'App portale aziendale. Le direzioni per eseguire questa operazione sono nel post di blog facendo clic sul collegamento informazioni aggiuntive. Se si sceglie di eseguire il push l'App portale aziendale in questo modo, gli utenti finali non saranno più vedranno la schermata "Identificazione del dispositivo" e la schermata di "Conferma del dispositivo" nel flusso di registrazione. 
- Dopo che viene implementata questa modifica, se è stata ancora distribuita l'App portale aziendale con il profilo di configurazione app indicato in precedenza e se gli utenti finali download archiviare l'app portale aziendale dall'App, possono accedere, ma verrà visualizzato un messaggio di errore. Non saranno in grado di usare l'app per l'accesso condizionale. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Se si prevede di usare il flusso di lavoro modificato, è necessario aggiornare le linee guida per utenti finali per indicare che:

- Gli utenti finali non vedranno le due schermate indicato in precedenza nel flusso di registrazione. 
- Sarà necessario eseguire l'accesso al portale aziendale quando viene distribuito automaticamente e non scaricarlo dall'app store. 

È possibile creare un criterio di configurazione di app ora, se necessario, in preparazione per la modifica. Quando questo nuovo flusso di lavoro esegue il roll, si noterà i profili di registrazione aggiornata nella console. Si verrà inoltre inviata una comunicazione di questa implementazione tramite il centro messaggi. Successivamente, è necessario intraprendere l'azione in modo che gli utenti finali possono registrare tramite DEP autenticandosi con Assistente configurazione ed è possibile usare il portale aziendale per l'accesso condizionale.

Vedere il blog di supporto post facendo clic sul collegamento informazioni aggiuntive per altri dettagli su questa modifica.

#### <a name="additional-information"></a>Informazioni aggiuntive 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Modifica prevista: aggiornamento dell'esperienza utente all'app Portale aziendale Intune per iOS
Siamo lieti di annunciare che Intune presto rilascerà un importante aggiornamento dell'esperienza utente all'app Portale aziendale per iOS. L'aggiornamento offrirà una riprogettazione visuale della home page con filtri avanzati e un accesso più rapido ad applicazioni e libri.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
L'aggiornamento dell'esperienza utente, pur conservando le attuali funzionalità del portale aziendale per iOS, conterrà quanto segue:
- Una home page con aspetto di iOS nativo 
- Funzionalità di filtro per gli elenchi di contenuti e ricerca, tra cui la possibilità di filtrare in base al tipo di contenuto (app o eBook) e alla disponibilità (gestione dei dispositivi obbligatoria o disponibile senza registrazione)
- Possibilità di cercare gli eBook
- Cronologia di ricerca per le App e gli eBook

Se si fa parte del programma Apple TestFlight, si riceverà una notifica sulla versione non definitiva dell'app Portale aziendale per iOS aggiornata di Intune quando diventa disponibile. Se non si fa parte del programma Apple TestFlight, si è ancora in tempo per registrarsi. La registrazione consente di usare l'app Portale aziendale aggiornata prima che sia disponibile per gli utenti finali. È anche possibile fornire commenti e suggerimenti direttamente al team di Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Non è necessario intraprendere alcuna azione. Queste modifiche verranno rilasciate in una versione imminente dell'app Portale aziendale per iOS. 

#### <a name="additional-information"></a>Informazioni aggiuntive
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

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

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>Modifiche pianificate: correzione disponibile a breve per i profili di posta elettronica di Windows 10 in Intune <!--3904031-->
Stiamo aggiornando il modo in cui che Intune scrive posta elettronica, aggiornare i profili per Windows 10 nel mese di aprile al servizio Intune per correggere un bug anche per assicurarsi che i profili di posta elettronica continuano a funzionare nelle prossime versioni di Windows 10. Azione da eseguire dopo la distribuzione di questa correzione è.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Questa modifica interessa è se si utilizzano profili di posta elettronica di Windows 10 con
- Il client di posta elettronica nativo in Windows 10 desktop o
- Il client di posta elettronica di Outlook in Windows 10 Mobile

Questo influisce sulle entrambi clienti Mobile Device Management (MDM) Intune autonomo e ibrido.

Dopo l'aggiornamento di aprile esegue il roll, è necessario creare nuovamente tali profili nella console di Intune (nella console di amministrazione di Configuration Manager se si usa una soluzione MDM ibrida).

Se non si eseguono azioni, ecco cosa verrà visualizzato per i profili creati prima dell'aggiornamento di aprile:

- Profili di posta elettronica esistenti verranno visualizzati in stato di errore nella console di Intune o console di amministrazione di Configuration Manager, ma gli utenti finali avranno comunque accesso alla posta elettronica. Tuttavia, dopo che ha apportato un aggiornamento successivo di Windows, questi profili non funzionerà correttamente. Gli utenti finali dei dispositivi di destinazione con questi profili perderanno l'accesso alla posta elettronica.
- Modifiche apportate a tali profili dopo mese di aprile non si rifletteranno dispositivi di destinazione.
- La cancellazione selettiva non funzionerà per la rimozione di questi profili anche dopo la correzione viene implementata nel mese di aprile.

Se si esegue azioni e ricreare i profili di posta elettronica, sarà necessario seguire passaggi simili a quelle quando viene distribuito un profilo di posta elettronica per la prima volta gli utenti finali. Posta elettronica verrà impedita la sincronizzazione fino a quando non si accetta l'aggiornamento che si applica il nuovo profilo.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
È necessario intervenire solo dopo la correzione viene implementata con l'aggiornamento di aprile. Microsoft si metterà all'utente tramite il centro messaggi durante la modifica viene resa disponibile ed è possibile iniziare a creare di nuovo i profili in Intune.

Se si utilizzano profili di posta elettronica di Windows 10 in Intune, è necessario procedere come segue:

1. Acquisire le impostazioni di profilo di Windows 10
2. Annullare l'assegnazione e/o eliminazione di profili esistenti
3. Creare nuovi profili utilizzando le impostazioni acquisite e assegnare i profili di nuovo agli stessi gruppi

Potrebbe essere necessario informare gli utenti finali e informare il supporto tecnico di questa modifica. Vedere il post di blog di supporto a informazioni aggiuntive per i dettagli dell'errore e istruzioni per ricreare questi profili.

#### <a name="additional-information"></a>Informazioni aggiuntive
https://aka.ms/Win10EmailProfiles

