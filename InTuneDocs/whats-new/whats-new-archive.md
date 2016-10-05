---
title: "Archivio novità | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecf43b38e9593375981770583220d4ce2dfd709f
ms.openlocfilehash: 8b0f393da727b433a926e780d6de42cf7b4c6034


---
## Dicembre 2015
### Modifiche e aggiornamenti del portale aziendale Microsoft
In questa versione sono state apportate le modifiche seguenti al portale aziendale.

**App Portale aziendale Android**

Sono state apportate le modifiche seguenti ai fini della conformità con i nuovi requisiti di Google. Nei dispositivi con Android 6.0 e versioni successive, vengono visualizzati due nuovi messaggi agli utenti:
* Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?
* Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?

Per informazioni dettagliate su questi due messaggi vedere le tabelle seguenti.



Testo del messaggio  |Consentire a Portale aziendale di effettuare e gestire chiamate telefoniche?  
---------|---------
Significato del messaggio     |  Consente l'invio del numero di telefono e del codice IMEI del dispositivo dell'utente al servizio Intune e la relativa visualizzazione nella console di amministrazione nella pagina Hardware.   </br></br>**NOTA: l'app Portale aziendale non effettua o gestisce mai chiamate telefoniche.** Il testo del messaggio è controllato da Google e non può essere modificato. </br></br>Per visualizzare la pagina **Hardware**, accedere a **Gruppi** > **Tutti i dispositivi mobili** > **Dispositivi**. Selezionare il dispositivo dell'utente e passare a **Visualizza proprietà** > **Hardware**.    
Dove e quando viene visualizzato il messaggio  | Il messaggio viene visualizzato quando l'utente accede per la prima volta all'app Portale aziendale per iniziare la registrazione del dispositivo.|         
Cosa accade se gli utenti consentono l'accesso  |  Il numero di telefono e il codice IMEI del dispositivo verranno visualizzati nella pagina Hardware nella console di amministrazione. |         
Cosa accade se gli utenti negano l'accesso     | Possono continuare a usare l'app Portale aziendale e registrare il dispositivo, ma il numero di telefono e il codice IMEI del loro dispositivo non compariranno nella pagina Hardware nella console di amministrazione.       </br></br> Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio.</br></br>Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato al successivo accesso all'app Portale aziendale dopo la registrazione.</br></br>Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Telefono** e quindi attivare l'autorizzazione.
Altre informazioni     |  Per gli utenti: [Accedere al Portale aziendale](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>Per i professionisti IT: le informazioni contenute in questa tabella sono disponibili anche in [Aiutare gli utenti a comprendere i messaggi dell'app Portale aziendale](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   

Testo del messaggio  |Consentire a Portale aziendale di accedere a foto, elementi multimediali e file nel dispositivo?  
---------|---------
Significato del messaggio     |  Consente al dispositivo di scrivere log di dati nella scheda SD del dispositivo, in modo da rendere possibile lo spostamento dei log tramite un cavo USB.   </br></br>**NOTA: l'app Portale aziendale non accede mai a foto, elementi multimediali e file degli utenti.** Il testo del messaggio è controllato da Google e non può essere modificato.     
Dove e quando viene visualizzato il messaggio  | Il messaggio viene visualizzato quando gli utenti toccano **Invia dati** per inviare i log di dati al loro amministratore IT.|         
Cosa accade se gli utenti consentono l'accesso  |  I log verranno copiati nella scheda SD. |         
Cosa accade se gli utenti negano l'accesso     | Possono comunque inviare i log di dati, ma questi non verranno copiati nella scheda SD del dispositivo.       </br></br> Al secondo accesso all'app Portale aziendale dopo aver negato l'accesso, nel messaggio sarà visualizzata la casella di controllo **Non visualizzare più questo messaggio** che gli utenti potranno selezionare per evitare di visualizzare di nuovo il messaggio.</br></br>Se gli utenti consentono l'accesso e in seguito lo negano, il messaggio verrà visualizzato al successivo tentativo di invio dei log.</br></br>Se si decide di consentire l'accesso in un secondo momento, passare a **Impostazioni** > **App** > **Portale aziendale** > **Autorizzazioni** > **Archiviazione** e quindi attivare l'autorizzazione.
Altre informazioni     |  Per gli utenti: [Inviare i log dei dati di diagnostica all'amministratore IT tramite posta elettronica](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>Per i professionisti IT: le informazioni contenute in questa tabella sono disponibili anche in [Aiutare gli utenti a comprendere i messaggi dell'app Portale aziendale](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   


**App del portale aziendale iOS**
* Gli utenti possono ora usare Microsoft Outlook o altre app di posta elettronica per inviare i log di diagnostica all'amministratore IT. In precedenza, era possibile usare solo l'app nativa.
* Il supporto è stato migliorato per i dispositivi del programma di registrazione dispositivi (DEP) di Apple e per i dispositivi registrati dall'azienda. Per informazioni dettagliate, vedere [Viene richiesto di identificare il dispositivo durante il tentativo di registrazione](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* Nell'elenco dei dispositivi registrati dell'utente viene ora visualizzato un segno di spunta verde accanto al dispositivo attualmente in uso. Prima dell'aggiunta del segno di spunta, non era possibile per gli utenti stabilire quale dispositivo registrato stavano usando.

**App Portale aziendale Windows**

Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso del Portale aziendale per migliorare prodotti e servizi Microsoft. Gli utenti finali possono disattivare la raccolta dati tramite l'impostazione relativa ai dati di uso del dispositivo. Tuttavia, gli amministratori non dispongono di controllo sulla raccolta dati e non possono modificare la selezione dell'utente relativa a questa impostazione.



## Novembre 2015
### Gestione delle app
Intune supporta criteri di gestione delle applicazioni mobili (MAM) che consentono di impedire la divulgazione dei dati aziendali alle app o ai servizi consumer. In passato, questi criteri venivano applicati solo nelle app mobili in esecuzione nei dispositivi che erano registrati anche per la gestione dei dispositivi mobili (MDM) in Intune.

Con l'aggiornamento di questo mese, Intune estende le sue funzionalità MAM a nuove classi di dispositivi. Oltre ai dispositivi registrati in Intune, è possibile ora applicare i criteri MAM in:
* dispositivi gestiti da qualsiasi altra soluzione di gestione dei dispositivi (MDM)
* dispositivi che non sono registrati in nessun sistema di gestione del dispositivo, in genere dispositivi personali (BYO)

Altre informazioni su queste nuove funzionalità MAM sono disponibili nei seguenti post di blog:
* [Miglioramento della produttività dei dispositivi mobili gestiti](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Annuncio delle nuove funzionalità di Microsoft Enterprise Mobility](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Di seguito sono evidenziate e ulteriormente illustrate alcune funzionalità MAM di Intune:
* I dati aziendali sono isolati dai dati consumer all'interno di applicazioni abilitate per Intune, tra cui App Office Mobile, app di terze parti che hanno adottato l'SDK di Intune o app line-of-business integrate in Intune.
* I dati aziendali possono essere condivisi (**Taglia/Copia/Incolla**) tra le app aziendali, impedendo la condivisione dei dati aziendali in app personali. Per altre informazioni, leggere [Protezione dei dati delle app con i criteri MAM](https://technet.microsoft.com/library/mt627825.aspx). Questo scenario di esempio, [Uso dell'app Microsoft Word per attività professionali e personali](https://technet.microsoft.com/library/mt627827.aspx), illustra come impedire la condivisione di dati aziendali nelle app personali.
* Criteri chiave di prevenzione della perdita di dati, come PIN per app, controlli salvataggio con nome e condivisione di dati gestiti tra app. Per vedere un elenco di tutti i criteri, leggere [Creare e distribuire i criteri di gestione delle app mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Word, Excel, PowerPoint, Outlook, OneNote e OneDrive for Business sono tutti dotati di queste nuove funzionalità e possono essere gestiti con o senza la registrazione del dispositivo. Le funzionalità di protezione dalla perdita di dati sono incorporate in modo nativo nelle app Office standard nell'Apple Store o in Google Play Store e non richiedono il wrapping o il sideload delle app.
* Per informazioni su come iniziare, vedere [Introduzione ai criteri di gestione delle app mobili nel portale di Azure](https://technet.microsoft.com/library/mt627830.aspx). Per informazioni su come configurare e distribuire i criteri di gestione di applicazioni mobili, vedere [Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Quando gli utenti finali si autenticano nell'app con le proprie credenziali aziendali, le funzionalità di protezione da perdita di dati vengono configurate automaticamente. L'argomento [Esperienza dell'utente finale per le app associate ai criteri di gestione delle app per dispositivi mobili di Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx) contiene alcuni scenari di esempio di accesso a OneDrive nei dispositivi iOS e Android.
* Funziona nei dispositivi iOS e Android.

L'elenco delle [app Microsoft che è possibile usare con i criteri di gestione delle applicazioni mobili di Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx) è stato aggiornato con le app più recenti.

### Gestione dei dispositivi
 **Gestione dei dispositivi Mac OS X** Con Intune ora è possibile registrare e gestire i dispositivi Mac OS X. Con i dispositivi Mac OS X è possibile eseguire le operazioni seguenti:
* Registrare i dispositivi da gestire in Intune. Vedere [Configurare la gestione dei dispositivi iOS con Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx).
* Controllare le impostazioni del dispositivo con un criterio di configurazione generale. Vedere [Impostazioni dei criteri di configurazione di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Distribuire le impostazioni di Mac OS X create con Apple Configurator. Vedere [Impostazioni dei criteri personalizzati di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Raccogliere l'inventario hardware e software dai dispositivi Mac OS X. Vedere [Informazioni sui dispositivi con inventario in Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx).
* Eseguire nuovi report che mostrino i dettagli sui dispositivi Mac OS X gestiti. Vedere [Comprendere le operazioni di Microsoft Intune con l'uso dei report](https://technet.microsoft.com/library/dn646977.aspx).

**Nuove impostazioni del browser Edge per i dispositivi Windows 10** Sono state aggiunte ai criteri di configurazione generale di Windows 10 nuove impostazioni che consentono di gestire le impostazioni e le funzionalità del browser Microsoft Edge. Vedere [Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx).

**Profili di posta elettronica** È stato aggiunto un nuovo criterio dei profili di posta elettronica per i dispositivi Windows 10 Desktop e Windows 10 Mobile. Vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](https://technet.microsoft.com/library/dn646984.aspx).

**Nuove impostazioni dei criteri di conformità** Sono state aggiunte le seguenti nuove impostazioni di sicurezza e dei criteri di sistema all'elenco dei criteri di conformità:
* Per accertarsi che nei dispositivi con Windows 8.1 o versioni successive che accedono alle risorse aziendali siano installati gli ultimi aggiornamenti, usare l'impostazione **Richiedi aggiornamenti automatici**. È anche possibile specificare il tipo di aggiornamenti da installare automaticamente, contrassegnandoli tutti come importanti o consigliati. Per l'elenco completo delle impostazioni dei criteri di conformità, vedere [Gestire criteri di conformità del dispositivo per Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx).
* La nuova impostazione **Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività** combinata all'impostazione **Minuti di inattività prima che venga richiesta la password** esistente consente di creare un'impostazione di conformità che richiede all'utente finale di immettere una password per usare un dispositivo che è rimasto inattivo per un determinato periodo di tempo.

**Nuove opzioni dei criteri di accesso condizionale** È possibile applicare criteri di accesso condizionale a **tutti gli utenti** nei criteri di accesso condizionale nuovi o esistenti. A tutti gli utenti con licenza per Intune e Office 365 verrà richiesto di registrare i propri dispositivi e, se la piattaforma del dispositivo non è supportata da Intune, l'accesso è bloccato per le applicazioni client che usano [l'accesso basato sull'autenticazione di Active Directory (autenticazione moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/).

È anche possibile specificare che venga applicato il criterio di accesso condizionale a **tutte le piattaforme**.  Tutte le applicazioni client che usano l'[accesso basato sull'autenticazione di Active Directory (autenticazione moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) sono soggette ai criteri di accesso condizionale e, se la piattaforma non è supportata da Intune, verranno bloccate.

### Modifiche e aggiornamenti del portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale:

* **Android**: è stata aggiunta una schermata di benvenuto all'app del portale aziendale Android per aiutare gli utenti a comprenderne lo scopo. Questa schermata mira a ridurre i download dell'app da parte degli utenti le cui le aziende non sono sottoscrittori Intune.

* **iOS**: Intune supporta ora la registrazione di dispositivi Mac OS X con il [sito Web del portale aziendale](https://portal.manage.microsoft.com). Per istruzioni, vedere [Registrare il dispositivo Mac OS X in Intune](https://technet.microsoft.com/library/mt598622.aspx).

* **Sito Web del portale aziendale**: gli utenti che hanno registrato il dispositivo in Intune possono ora reimpostare il passcode con l'opzione **Reimposta passcode** nel sito Web del portale aziendale. In precedenza, solo gli amministratori IT potevano ripristinare i passcode degli utenti. L'opzione Reimposta passcode non è supportata nei dispositivi Windows 8.1 e Windows RT e viene visualizzata solo quando i dispositivi sono registrati in una soluzione di gestione dei dispositivi mobili (MDM) o in MDM con Exchange ActiveSync. Per istruzioni per gli utenti, vedere [Reimpostare il passcode](https://technet.microsoft.com/library/mt590895.aspx).

### Modifiche alle licenze degli amministratori globali
Nel mese di ottobre, è stato annunciato che gli amministratori globali (noti anche come amministratori tenant) potevano continuare a eseguire attività di ordinaria amministrazione senza una licenza separata di Intune o Enterprise Mobility Suite (EMS). Tuttavia, se gli amministratori globali vogliono usare il servizio, ad esempio per registrare il proprio dispositivo, un dispositivo aziendale oppure usare il portale aziendale di Intune, avranno bisogno di una licenza Intune o EMS, esattamente come qualsiasi altro utente. Di seguito sono riportati alcuni dettagli aggiuntivi.
* Nel portale aziendale di Intune gli utenti finali possono:
    * iscrivere il proprio dispositivo
    * visualizzare lo stato del dispositivo
    * scaricare il software distribuito da un amministratore globale all'organizzazione
    * trovare i collegamenti pubblicati dall'amministratore globale per informazioni su come contattare il reparto IT

    [Altre informazioni sul portale aziendale](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) e su [come personalizzare il portale aziendale](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* La persona che effettua l'iscrizione per l'acquisto di Intune o EMS per conto di un'organizzazione diventa automaticamente il primo amministratore globale nel tenant. Quest'autunno, Intune ha iniziato ad assegnare automaticamente una licenza di Intune o EMS al primissimo amministratore globale, come parte del passaggio al [portale di Office 365](http://portal.office.com/) e la disattivazione del [Portale per gli account di Intune](http://account.manage.microsoft.com/). Tutti gli altri amministratori globali aggiunti possono continuare a usare l'amministrazione quotidiana senza una licenza separata di Intune o EMS. Agire da utente finale e registrare il dispositivo personale (o aziendale) o scaricare software dal portale aziendale comporterà la necessità di una licenza, esattamente come qualsiasi altro utente.
* La modifica verrà gradualmente implementata a partire da gennaio 2016.
* Per i Partner Microsoft, questa modifica non dovrebbe incidere sulla possibilità di amministrare il servizio per conto dei clienti. Per le attività dell'utente finale, un utente dovrà avere una licenza Intune o EMS per poter registrare un dispositivo e accedere al software o scaricarlo dal portale aziendale.

In caso di domande su questa modifica, è possibile contattare il team di supporto di Intune:
* [Canali di supporto di Microsoft Intune](https://technet.microsoft.com/library/jj839713.aspx)
* [Supporto della community](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Per commenti generali su Microsoft Intune, tra cui la creazione di richieste di modifica del design (DCR, Design Change Request) o di bug, visitare l'apposito [sito per i commenti degli utenti di Intune](https://microsoftintune.uservoice.com/).


### Novità nella documentazione di Intune - Novembre 2015
**Nuovo contenuto**
* [Impostazioni dei criteri di configurazione di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): come controllare le impostazioni e le funzionalità dei dispositivi Mac OS X.
* [Impostazioni dei criteri personalizzati di Mac OS X in Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): come distribuire le impostazioni del dispositivo Mac OS X create con lo strumento Apple Configurator.
* [Configurare i criteri delle app per la prevenzione della perdita di dati con Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): contiene informazioni sugli scenari supportati dai criteri di gestione delle app mobili e sul funzionamento dei criteri per la protezione dei dati.
* [Introduzione ai criteri di gestione delle app per dispositivi mobili nel portale di Azure](https://technet.microsoft.com/library/mt627830.aspx): informazioni necessarie per iniziare a usare il portale di anteprima di Azure per i criteri di gestione delle app mobili.
* [Creare e distribuire i criteri di gestione delle app mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): contiene una procedura dettagliata su come creare criteri di gestione delle app mobili nel portale di anteprima di Azure.
* [Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): informazioni su come è possibile monitorare i criteri di gestione delle app mobili con il portale di anteprima di Azure.
* [Criteri di gestione delle app per dispositivi mobili di Microsoft Intune e funzionalità Open In di iOS](https://technet.microsoft.com/library/mt627821.aspx): informazioni sul funzionamento dei criteri di gestione delle app mobili con la funzionalità Open In di iOS.
* [Esperienza dell'utente finale per le app associate ai criteri di gestione delle app per dispositivi mobili di Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx): informazioni sull'esperienza dell'utente finale quando si usano le app associate ai criteri di gestione delle app mobili.
* [Cancellare i dati dell'app aziendale gestita con Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): come è possibile rimuovere i dati dall'app aziendale.

**Contenuto aggiornato**
* [Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): aggiunte le nuove impostazioni del browser Microsoft Edge.
* [Configurare la gestione dei dispositivi iOS con Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): aggiunte informazioni su come registrare i dispositivi Mac OS X.
* [Informazioni sui dispositivi con inventario in Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): aggiunte informazioni sull'inventario raccolto dai dispositivi Mac OS X. Aggiornato anche l'argomento con le ultime informazioni per tutte le piattaforme per dispositivi.
* [Comprendere le operazioni di Microsoft Intune con l'uso dei report](https://technet.microsoft.com/library/dn646977.aspx): aggiunte informazioni sui due nuovi report usati per visualizzare informazioni sui dispositivi Mac OS X gestiti.
* [Gestire i criteri di conformità del dispositivo per Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): aggiunte informazioni sui nuovi criteri di conformità per richiedere aggiornamenti automatici e la password quando un dispositivo torna attivo dopo uno stato di inattività.
* [Gestire l'accesso alla posta elettronica con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): aggiunte informazioni sulla capacità di applicare i criteri di accesso condizionale a tutte le piattaforme e a tutti gli utenti.
* [Gestire l'accesso a SharePoint Online con Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): aggiunte informazioni sulla capacità di applicare i criteri di accesso condizionale a tutte le piattaforme e a tutti gli utenti.

## Ottobre 2015

### Aggiornamenti all'accesso condizionale per Exchange locale
**È ora possibile consentire l'accesso alla posta elettronica di Exchange Active Sync per i dispositivi conformi registrati in Intune quando la regola globale di Exchange è impostata su blocco o quarantena** Fino ad ora, per consentire l'accesso alla posta elettronica nei dispositivi registrati e conformi era necessario impostare la regola globale di Exchange predefinita su **Consenti**.

Grazie a questo aggiornamento del servizio, tale impostazione non è più un requisito per l'accesso condizionale. Se l'ambiente Exchange richiede che la regola globale predefinita sia impostata su **Blocco/Quarantena**, è sufficiente selezionare la casella di controllo **Override regola predefinita** nella pagina dei criteri di Exchange locale per l'accesso condizionale. L'argomento [ Gestire l'accesso alla posta elettronica con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) include informazioni dettagliate sulle regole e le notifiche risultanti per l'utente finale.

**Nuova esperienza della quarantena in un solo clic** È stata semplificata l'esperienza per il messaggio di posta elettronica di quarantena in modo da consentire la registrazione in un solo clic. Grazie a questo aggiornamento del servizio, gli utenti finali possono fare clic su un singolo collegamento nel messaggio di posta elettronica di quarantena per completare il processo di registrazione nell'app Portale aziendale.
### Aggiornamenti per la gestione di dispositivi mobili e app
**Android** Tutte le funzionalità di gestione di Intune supportano ora Android 6.0 (Marshmallow) come descritto in questo post di blog relativo al [supporto di 0 giorni di Microsoft Intune per Android Marshmallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx)

**iOS** Non è più possibile creare nuove distribuzioni di app nei dispositivi iOS che eseguono una versione precedente a iOS 7.1. Tutte le distribuzioni nei dispositivi che eseguono una versione precedente a iOS 7.1 continueranno a funzionare e ad essere gestite da Intune.

**Windows 10** Intune supporta ora la distribuzione a Windows 10 Universal con il tipo di programma di installazione software **Pacchetto app Windows**. Per informazioni dettagliate e requisiti vedere [Introduzione alla distribuzione dell'app in Microsoft Intune](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Modifiche e aggiornamenti alle app del Portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale: **iOS** Sono stati aggiunti nuovi pulsanti all'app Portale aziendale per rendere più facile agli utenti l'invio di log di diagnostica agli amministratori IT:

|Nome pulsante|Posizione di visualizzazione|
|------------|---------------|
|Report|Messaggi di avviso errore|
|Invia report di diagnostica|Schermata Informazioni dell'app Portale aziendale|



## Settembre 2015
### Aggiornamenti per la gestione di dispositivi mobili e app
**Tutte le funzionalità di gestione iOS per Intune ora supportano iOS 9** Per informazioni dettagliate sulle funzionalità di gestione di iOS 9, vedere [questo post di blog](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx).

**Nuovi criteri di configurazione di app per dispositivi mobili per iOS** Usare i nuovi criteri di configurazione di app per dispositivi mobili per specificare automaticamente le impostazioni che possono essere utili a un'app per iOS quando viene eseguita. Ad esempio, è possibile specificare una porta di rete o un nome utente. Per informazioni dettagliate, vedere [Configurare le app con i criteri di configurazione delle app per dispositivi mobili in Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx).

**Gestione di app semplificata per gli utenti di iOS 9**
 In questa versione è possibile fare in modo che le app già distribuite vengano gestite da Intune per gli utenti di iOS 9. Per le versioni precedenti di iOS, quando si distribuisce un'app e sul dispositivo è già installata una versione non gestita dell'applicazione, è necessario chiedere all'utente di disinstallare manualmente l'app prima che sia possibile installare le app gestite con Intune.

 Tuttavia, a partire da questa release di Intune, è possibile richiedere agli utenti dei dispositivi iOS 9 di consentire che Intune si occupi della gestione dell'app e applichi tutti i criteri di gestione delle applicazioni mobili pertinenti.

 **Gestione di Windows 10** Usare i nuovi [criteri di configurazione generale di Windows 10](https://technet.microsoft.com/library/mt404697.aspx) per configurare password, dispositivi, browser e altre impostazioni per i dispositivi registrati che eseguono Windows 10 e Windows 10 Mobile.

 **Creare e distribuire app a dispositivi Windows 10 registrati** Un nuovo tipo di programma di installazione software, Windows Installer tramite MDM (&#42;.msi), consente di creare e distribuire le app di Windows Installer nei dispositivi registrati che eseguono Windows 10. Per informazioni dettagliate, vedere [Introduzione alla distribuzione dell'app in Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

### Modifiche e aggiornamenti alle app del Portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale:

**iOS**
* Microsoft raccoglie automaticamente dati anonimi sulle prestazioni e sull'uso del Portale aziendale per migliorare prodotti e servizi Microsoft. Gli utenti finali possono disattivare la raccolta dati tramite l'impostazione Dati sull'utilizzo del dispositivo. Gli amministratori invece non hanno controllo sulla raccolta dati e non possono modificare la selezione dell'utente relativa a questa impostazione.
* Supporto per la risoluzione a schermo intero in iPhone 6 e 6 Plus
* Correzioni dei bug per migliorare la sicurezza

### Novità della documentazione di Intune - Settembre 2015
**Nuovi argomenti**

|Nome|Dettagli|
|----|--------|
|[Impostazioni di criteri di configurazione di Windows 10 in Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)|Si tratta di nuovi criteri di configurazione che consentono di gestire le impostazioni e le funzionalità dei dispositivi che eseguono Windows 10 e Windows 10 Mobile.
| [Configurare le app con i criteri di configurazione delle app mobili in Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)|Si tratta di nuovi tipi di criteri che consentono di specificare automaticamente le impostazioni che possono essere necessarie quando l'utente esegue un'app iOS. |

**Argomenti aggiornati**

|Nome|Dettagli|
|----|-------|
|[Usare i criteri per gestire computer e dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)|Aggiornato per includere le informazioni più recenti che consentono di comprendere e creare i criteri.|

## Agosto 2015
### Aggiornamenti per la gestione di dispositivi mobili e app
* I**Termini e condizioni** per la registrazione di Intune e l'accesso aziendale ora vengono [gestiti tramite i criteri](https://technet.microsoft.com/library/mt405893.aspx). È possibile usare diversi tipi di termini e condizioni per soddisfare specifici requisiti per i gruppi di utenti. Ad esempio, è possibile distribuire termini e condizioni in lingue diverse ai gruppi di utenti definiti geograficamente. È anche possibile [modificare i termini e le condizioni](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) e specificare se aumentare i numeri di versione richiedendo agli utenti di accettare i nuovi termini e condizioni per poter usare il Portale aziendale.
* **Diversi criteri di Intune sono stati rinominati** per renderli più uniformi all'interno del prodotto e per semplificarne l'individuazione. Per un elenco di tutti i criteri di Intune disponibili, vedere [Usare i criteri per gestire computer e dispositivi mobili con Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx).
* I **profili certificati PKCS #12 (PFX)** sono disponibili per Android 4.0 o versioni successive e per Windows 10 (Desktop e Mobile) e versioni successive. L'uso di .PFX non richiede un server NDES. Per altre informazioni su come usare i profili certificato PFX, vedere [Abilitare l'accesso alle risorse aziendali usando i profili certificato con Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx).
* Le impostazioni **Limiti aziendali per Windows 10 Desktop e Mobile** abilitano impostazioni VPN granulari, come descritto in [Consentire agli utenti di connettersi al proprio lavoro tramite profili VPN con Microsoft Intune](https://technet.microsoft.com/library/dn818905.aspx).
* **L'app OneDrive per Android ora supporta più identità**. Questo e altri criteri di gestione delle app mobili sono descritti nell' [elenco di applicazioni Microsoft che è possibile gestire](https://technet.microsoft.com/library/dn708489.aspx).
* **Bypass del blocco attivazione iOS**. Se i dispositivi iOS di proprietà dell'azienda sono protetti dal blocco attivazione, è necessario immettere l'ID e la password Apple dell'utente per formattare o riattivare il dispositivo. Questo può costituire un problema se gli utenti lasciano la società e restituiscono un dispositivo aziendale senza aver prima disattivato Blocco attivazione. Per risolvere questo problema, si può usare [Bypass del blocco attivazione di Intune](https://technet.microsoft.com/library/mt414176.aspx).

### Accesso condizionale per i PC
Ora è possibile configurare i criteri di accesso condizionale per i PC. Questi criteri consentono alle app desktop di Office di accedere ai servizi di Exchange Online e SharePoint Online.
Per abilitare i criteri di accesso condizionale per i PC, è necessario che questi ultimi siano aggiunti a un dominio oppure che siano conformi.
* Vedere la sezione **Guida introduttiva** in [ Gestire l'accesso alla posta elettronica e a SharePoint con Microsoft Intune](http://technet.microsoft.com/library/dn818907).aspx) per un elenco completo di requisiti per abilitare l'accesso condizionale per i PC.
* Vedere [ Gestire l'accesso alla posta elettronica con Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) per le opzioni che è possibile impostare per abilitare l'accesso condizionale per l'accesso alla posta elettronica.
* Vedere [Gestire l'accesso a SharePoint Online con Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) per le opzioni che è possibile impostare per abilitare l'accesso condizionale per SharePoint Online.

### Modifiche e aggiornamenti alle app del Portale aziendale Microsoft
In questa versione sono state apportate le seguenti modifiche alle app del portale aziendale:

**Android**

Se il dispositivo non è ancora stato registrato per la gestione, dopo aver eseguito l'accesso gli utenti visualizzeranno le istruzioni di registrazione.

### Novità nella documentazione di Intune -- Agosto 2015
**Nuovi argomenti**

|Titolo|Dettagli|
|-----|-------|
|[Proteggere i dispositivi iOS con il bypass di Blocco attivazione per Microsoft Intune](https://technet.microsoft.com/library/mt414176.aspx)|Informazioni su come usare Intune per ignorare il blocco attivazione iOS quando un utente lascia l'azienda e restituisce un dispositivo bloccato.|

**Argomenti aggiornati**

|Titolo|Dettagli|
|-----|-------|
|[App Microsoft che è possibile usare con i criteri di gestione delle applicazioni mobili di Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx)|Aggiornato con le ultime informazioni sulle app che è possibile gestire con i criteri di gestione delle applicazioni mobili.
|[Usare i criteri per gestire computer e dispositivi mobili con Microsoft Intune](http://technet.microsoft.com/library/dn743712.aspx)|Aggiornato con i criteri più recenti aggiunti a Intune.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Sep16_HO5-->


