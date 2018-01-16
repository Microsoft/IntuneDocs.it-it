---
title: Edizione anticipata
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ac9cb0ad7d1b5e2c29e80f16c172f41c08d3a15d
ms.sourcegitcommit: 5fd17a57989c6da3d325ed2e0018ce16fe20bb79
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="the-early-edition-for-microsoft-intune---january-2018"></a>Edizione anticipata per Microsoft Intune - Gennaio 2018

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non condividere queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
>Le seguenti modifiche di Intune sono in fase di sviluppo. Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices 
-->


## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546---"></a>Risoluzione dei problemi di conformità più facile per l'app Portale aziendale per Windows 10 <!--676546 -->

Gli utenti finali con dispositivi Windows potranno toccare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema. 

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nuova opzione per l'autenticazione utente per la registrazione in blocco Apple <!-- 747625 -->
Intune offre la possibilità di autenticare i dispositivi con l'app Portale aziendale per i metodi di registrazione seguenti:

- Programma di registrazione del dispositivo mobile di Apple:
- Apple School Manager
- Registrazione di Apple Configurator

Quando si usa l'opzione Portale aziendale, l'autenticazione a più fattori di Azure Active Directory può essere applicata senza bloccare questi metodi di registrazione.

Quando si usa l'opzione Portale aziendale, Intune ignora l'autenticazione utente nell'Assistente configurazione di iOS per la registrazione dell'affinità utente. Questo significa che il dispositivo viene inizialmente registrato come dispositivo senza utente e pertanto non riceverà le configurazioni o i criteri dei gruppi utenti, ma solo le configurazioni e i criteri per i gruppi di dispositivi. Tuttavia, Intune installerà automaticamente l'app Portale aziendale nel dispositivo. Il primo utente che avvia l'app Portale aziendale e vi accede verrà associato al dispositivo in Intune. A questo punto l'utente riceverà le configurazioni e i criteri dei gruppi utenti. L'associazione dell'utente non può essere modificata senza eseguire di nuovo la registrazione.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 -->
Intune supporterà la registrazione di dispositivi da un massimo di 100 account Apple Device Enrollment Program (DEP) o Apple School Manager diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eeready---"></a>Selezionare le categorie di dispositivi usando le impostazioni Accedi all'azienda o all'istituto di istruzione <!-- 1058963 eeready --> 
Se è stato abilitato il [mapping dei gruppi di dispositivi](https://docs.microsoft.com/en-us/intune/device-group-mapping), agli utenti in Windows 10 verrà richiesto di selezionare una categoria di dispositivi dopo la registrazione tramite il pulsante **Connetti** in **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione** o durante la Configurazione guidata.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Assegnazione dei criteri di conformità a dispositivi in gruppi di dispositivi <!--1307012 -->

Sarà possibile assegnare i criteri di conformità agli utenti in gruppi utenti. Sarà possibile assegnare i criteri di conformità ai dispositivi in gruppi di dispositivi. 

### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusione ed esclusione per l'assegnazione di app in base ai gruppi <!-- 1406920 -->

Durante l'assegnazione di app e dopo aver selezionato un tipo di assegnazione, sarà possibile selezionare i gruppi da includere, così come i gruppi da escludere. Sarà anche possibile usare i gruppi creati in precedenza (Tutti gli utenti, Tutti i dispositivi e Tutti gli utenti+Tutti i dispositivi) come gruppi inclusi.

### <a name="remote-erase-command-support----1438084---"></a>Supporto del comando "Cancella" remoto <!-- 1438084 -->

Gli amministratori potranno eseguire un comando di cancellazione in remoto.

> [!IMPORTANT]
> Il comando di cancellazione non può essere annullato e deve essere usato con cautela.

Il comando di cancellazione rimuove tutti i dati, incluso il sistema operativo, da un dispositivo. Rimuove anche il dispositivo dalla gestione di Intune. Non viene visualizzato alcun avviso all'utente e la cancellazione viene eseguita immediatamente.

Sarà possibile configurare un PIN di ripristino di 6 cifre. Questo PIN può essere usato per sbloccare il dispositivo cancellato e a quel punto verrà avviata la reinstallazione del sistema operativo. Dopo l'avvio della cancellazione, il PIN viene visualizzato in una barra di stato nel pannello della panoramica del dispositivo in Intune. Il PIN verrà mantenuto per tutta la durata del processo di cancellazione. Dopo il completamento della cancellazione, il dispositivo scompare del tutto dalla gestione di Intune. Assicurarsi di registrare il PIN di ripristino in modo che possa essere usato da chiunque esegua il ripristino del dispositivo.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dati crittografati di Windows Information Protection (WIP) nei risultati di ricerca di Windows <!-- 1469193 -->

Una nuova impostazione nei criteri di Windows Information Protection (WIP) consentirà di controllare se i dati crittografati WIP vengono inclusi nei risultati di ricerca di Windows.

### <a name="website-learning-mode----1631908---"></a>Modalità di apprendimento del sito Web <!-- 1631908 -->

Intune introdurrà un'estensione della modalità di apprendimento WIP (Windows Information Protection). Oltre a visualizzare informazioni sulle app abilitate per WIP, sarà possibile visualizzare un riepilogo dei dispositivi che hanno condiviso dati di lavoro con siti Web. Con queste informazioni, è possibile determinare quali siti Web devono essere aggiunti ai criteri WIP per gruppi e utenti.

### <a name="updates-to-compliance-emails---1637547---"></a>Aggiornamenti per i messaggi di posta elettronica di conformità <!--1637547 -->

Quando viene inviato un messaggio di posta elettronica per segnalare un dispositivo non conforme, verranno inclusi dettagli sul dispositivo non conforme. L'articolo seguente verrà aggiornato per indicare questo fatto: [Automatizzare le azioni per la non conformità](#actions-for-noncompliance).

### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>I criteri di accesso condizionale per Intune sono disponibili solo dal portale di Azure <!-- 1737088 1634311 --> 
Verranno semplificate le posizioni da cui è possibile configurare e gestire l'accesso condizionale. Sarà possibile configurare e gestire i criteri solo nel [portale di Azure](https://portal.azure.com) da **Azure Active Directory** > **Accesso condizionale**. Per praticità, sarà possibile accedere a questo pannello anche da Intune nel portale di Azure in **Intune** > **Accesso condizionale**.

###  <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Avvisi per i token scaduti e i token che scadranno a breve <!-- 1639263 -->
Nella pagina di panoramica verranno visualizzati avvisi per i token scaduti e i token che scadranno a breve. Facendo clic su un avviso per un singolo token si passerà alla pagina dei dettagli del token.  Se si fa clic su un avviso con più token, verrà visualizzato un elenco di tutti i token con il relativo stato. Gli amministratori devono rinnovare i relativi token prima della scadenza.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Stampa remota su una rete protetta <!-- 1709994  -->
Le soluzioni di stampa mobile wireless di PrinterOn consentiranno agli utenti di eseguire stampe in modalità remota da qualsiasi posizione e in qualsiasi momento tramite una rete protetta. PrinterOn verrà integrato in Intune APP SDK sia per iOS che per Android. Sarà possibile assegnare i criteri di protezione delle app a questa app tramite il pannello **Criteri di protezione delle app** di Intune nella console di amministrazione. Gli utenti finali potranno scaricare l'app 'PrinterOn per Microsoft' tramite Play Store o iTunes da usare all'interno del loro ecosistema di Intune.

### <a name="approve-the-company-portal-app-for-android-for-work---1797090---"></a>Approvare l'app Portale aziendale per Android for Work <!--1797090 -->
Se l'organizzazione usa Android for Work, sarà necessario approvare manualmente l'app Portale aziendale per Android in modo che continui a ricevere gli aggiornamenti automatici dalla versione gestita di Google Play Store.

### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>API Microsoft Graph per Intune - Disponibilità generale <!-- 1833289 -->
Le API di Intune in Microsoft Graph consentiranno l'accesso programmatico a dati e metodi per l'automazione di azioni amministrative per il servizio Intune.  Con la **disponibilità generale** di queste API, clienti, partner e sviluppatori potranno sfruttare le API per l'integrazione con soluzioni interne o commerciali correlate a o che richiedono il supporto di Intune o altri servizi Microsoft disponibili tramite Microsoft Graph. 

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Criteri di protezione delle app <!-- 679615 -->
I criteri di Protezione app di Intune offrono la possibilità di creare criteri predefiniti globali per attivare rapidamente la protezione per tutti gli utenti nell'intero tenant.

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revoca delle app Volume Purchase Program iOS <!-- 820863 -->
Per un determinato dispositivo con una o più app Volume Purchase Program (VPP) iOS, sarà possibile revocare la licenza per app basata su dispositivo associata per il dispositivo. La revoca di una licenza per app non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. Per altre informazioni, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revocare le licenze per un token Volume Purchasing Program iOS <!-- 820870 -->
Sarà possibile revocare la licenza di tutte le app Volume Purchasing Program (VPP) iOS per un determinato token VPP.

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>Segnalazione dell'archiviazione di un dispositivo gestito con NAC (Network Access Control) <!-- 1232250 -->
Prima di questa modifica, gli amministratori IT non potevano determinare dal lato Intune se un dispositivo gestito con NAC era o meno in comunicazione con la propria soluzione NAC. Quando un dispositivo gestito con NAC non comunica con una soluzione NAC, il dispositivo viene considerato non conforme dalla soluzione NAC e quindi bloccato dalla stessa e successivamente bloccato dai criteri di accesso condizionale che si basano sullo stato di conformità del dispositivo.

Con questa modifica, gli amministratori IT possono visualizzare i dispositivi gestiti con NAC che sono riusciti o meno a comunicare con la propria soluzione NAC. Questa nuova funzionalità è costituita da due nuove funzioni di monitoraggio disponibili nel carico di lavoro Conformità del dispositivo in Intune. Le statistiche sono indicate di seguito:
- **Average NAC calls in the last hour** (Numero medio di chiamate NAC nell'ultima ora)
- **Last NAC incoming request (date/time)** (Ultima richiesta NAC in ingresso -data/ora)

### <a name="new-ios-device-action------1244701---"></a>Nuova azione per dispositivi iOS <!-- 1244701 -->
È possibile arrestare i dispositivi iOS 10.3 con supervisione. Questa azione arresta il dispositivo immediatamente senza avviso all'utente finale. L'azione **Shut down (supervised only)** (Arresta - solo con supervisione) è disponibile nelle proprietà del dispositivo quando si seleziona un dispositivo nel carico di lavoro **Dispositivo**.


### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune offre ora l'operazione Account Move (Spostamento account) <!-- 1573558, 1579830 -->
L'operazione **Account Move** (Spostamento account) esegue la migrazione di un tenant da un'unità di scala di Azure (ASU) a un'altra. L'operazione **Account Move** (Spostamento account) può essere usata per entrambi gli scenari avviati dall'utente, quando si chiama il team di supporto di Intune per richiederla, e può anche essere uno scenario basato su Microsoft nei casi in cui Microsoft deve apportare modifiche al servizio nel back-end. Durante un'operazione **Account Move** (Spostamento account), il tenant passa alla modalità di sola lettura (ROM). Durante il periodo ROM, le operazioni sui servizi come la registrazione, la ridenominazione di dispositivi e l'aggiornamento dello stato di conformità avranno esito negativo.




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Assegnare le app per dispositivi mobili Office 365 a dispositivi iOS e Android usando il tipo di app predefinito <!-- 1332318 -->
Il tipo di app **Predefinito** consente di creare e assegnare in modo semplice le app Office 365 a dispositivi iOS e Android gestiti. Le app includono le app 0365 come Word, Excel, PowerPoint e OneDrive. È possibile assegnare app specifiche al tipo di app e modificare la configurazione delle informazioni sull'app.


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>Risoluzione dei conflitti di assegnazione modificata per le app di iOS Store <!-- 1480316 -->
Gli utenti finali potrebbero rilevare una modifica alla disponibilità delle app di iOS Store. Attualmente, un'app assegnata a due gruppi con un conflitto tra **Richiesto e disponibile** e **Non applicabile** viene risolta in **Richiesto e disponibile**. Con la modifica, un'app per la quale si verifica questo conflitto verrà risolta in **Non applicabile**.

La modifica elimina la confusione che si verifica quando la stessa app viene assegnata a più gruppi con finalità di app diverse.

Se si vuole rendere disponibile l'app nel portale di Information Worker e nel portale aziendale prima del rilascio di novembre del servizio, sono disponibili due opzioni:

1. Rimuovere l'assegnazione **Non applicabile** per il gruppo.
2. Creare un nuovo gruppo che non contiene membri con la finalità **Richiesto e disponibile** e assegnare il gruppo come **Non applicabile**.

Per altre informazioni, vedere [Come assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

> [!Note]
> Dopo il rilascio non sarà più possibile visualizzare o modificare le assegnazioni delle app MDM (Mobile Device Management) nella console classica di Intune. È possibile tuttavia usare la console di Azure o l'API Graph di Intune per eseguire le assegnazioni delle app.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>Gestire i dispositivi Android for Work indipendentemente dai dispositivi Android <!-- 1490731 -->
Intune supporta la gestione della registrazione di dispositivi Android for Work indipendentemente dalla piattaforma Android. Queste impostazioni vengono gestite in **Registrazione del dispositivo** > **Restrizioni registrazione** > **Restrizioni sul tipo di dispositivi**. In precedenza erano disponibili in **Registrazione del dispositivo** > **Registrazione di Android for Work** > **Impostazioni di registrazione per Android for Work**.

Per impostazione predefinita, le impostazioni dei dispositivi Android for Work corrispondono alle impostazioni dei dispositivi Android. Tuttavia, dopo la modifica delle impostazioni Android for Work questa corrispondenza andrà persa.
 
Se si blocca la registrazione dei dispositivi Android for Work personali, solo i dispositivi Android aziendali possono essere registrati come Android for Work.

Durante l'uso delle nuove impostazioni, considerare quanto segue:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work non è mai stata caricata in precedenza
La nuova piattaforma Android for Work è bloccata nelle Restrizioni sul tipo di dispositivi predefinite. Dopo aver caricato la funzionalità, è possibile consentire la registrazione dei dispositivi con Android for Work. A tale scopo, modificare il valore predefinito o creare una nuova restrizione dei tipi di dispositivo per sostituire la restrizione predefinita.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work è stata caricata
Se la registrazione è stata caricata in precedenza, la situazione varia a seconda dell'impostazione selezionata:

| Impostazione | Stato di Android for Work nella restrizione dei tipi di dispositivo predefinita | Note |
| --- | --- | --- |
| **Gestisci tutti i dispositivi come Android** | Bloccato | Tutti i dispositivi Android devono essere registrati senza Android for Work. |
| **Gestisci i dispositivi supportati come Android for Work** | Consentito | Tutti i dispositivi Android che supportano Android for Work devono essere registrati con Android for Work. |
| **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work** | Bloccato | Per sostituire l'impostazione predefinita è stato creato un criterio Restrizione dei tipi di dispositivo separato. Questo criterio definisce i gruppi precedentemente selezionati per consentire la registrazione di Android for Work. Gli utenti inclusi nei gruppi selezionati continueranno a essere autorizzati a registrare i loro dispositivi Android for Work. A tutti gli altri utenti non è consentita la registrazione con Android for Work. |

In tutti i casi, viene mantenuto il regolamento previsto. Per mantenere l'autorizzazione globale o per i singoli gruppi di Android for Work nel proprio ambiente non è necessario eseguire alcuna operazione.

Sebbene la distribuzione di queste modifiche abbia inizio con l'aggiornamento di novembre, potrebbe richiedere del tempo per essere resa esecutiva nel proprio account. Quando queste modifiche vengono rese effettive per il proprio account, si riceverà una notifica di conferma nel portale di Office 365.


### <a name="configure-an-ios-app-pin----1586774---"></a>Configurare il PIN di un'app iOS <!-- 1586774 -->
Sarà presto possibile richiedere un PIN per le app iOS di destinazione. È possibile configurare la richiesta e la data di scadenza in giorni del PIN tramite il portale di Azure. Quando necessario, all'utente viene richiesto di impostare e usare un nuovo PIN prima di ottenere l'accesso a un'app iOS. Questa funzionalità è supportata solo dalle app iOS con la protezione dell'app abilitata con Intune App SDK.


<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->   
Usando Azure Active Directory (Azure AD) è possibile limitare l'accesso ai siti Web su dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure.


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Supporto dei criteri di aggiornamento edizione di Windows 10 <!-- 903672(archived), 1119689 -->  
È possibile creare criteri di aggiornamento edizione di Windows 10 per l'aggiornamento di dispositivi Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Per informazioni dettagliate sugli aggiornamenti edizione di Windows 10, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>Supporto di Android for Work per Lookout <!-- 1087312 -->   
Il connettore di Intune con Lookout supporterà i dispositivi Android for Work quando si usa l'app Lookout for Work. È possibile distribuire l'app Lookout all'interno o all'esterno del contenitore.

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Protezione app di Intune e strumenti di sviluppo MDX Citrix <!-- 709185 -->
È possibile gestire i dispositivi e le app usando in combinazione Citrix XenMobile MDX e Microsoft Intune. Ciò consente di gestire le app con i criteri di protezione delle app di Intune usando allo stesso tempo la tecnologia mVPN di Citrix.

È disponibile un repository di codice che contiene lo strumento di wrapping delle app di Intune e Intune App SDK per iOS e Android, per l'integrazione con la tecnologia mVPN MDX di Citrix.




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>Reindirizzamento degli utenti macOS alla nuova app del portale aziendale <!--1380728-->   
Quando un utente finale accede al sito Web del portale aziendale per registrare il proprio dispositivo macOS, l'utente viene indirizzato al download della nuova app del portale aziendale per macOS per completare il processo. Ciò si verifica per i dispositivi macOS che usano OS X El Capitan 10.11 o versioni successive. 



<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>Supporto di Intune Managed Browser per iOS e Android <!-- 1374196 -->
A partire da ottobre 2017, l'app Intune Managed Browser per Android supporta solo i dispositivi che eseguono Android 4.4 e versioni successive. L'app Intune Managed Browser per iOS supporta solo i dispositivi che eseguono iOS 9.0 e versioni successive. Le versioni precedenti di Android e iOS saranno in grado di continuare a usare Managed Browser, ma non sarà possibile installare nuove versioni dell'app e le funzionalità dell'app potrebbero non essere tutte disponibili. Si consiglia di eseguire l'aggiornamento di questi dispositivi a una versione supportata del sistema operativo.


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Messaggio di errore migliorato quando un utente raggiunge il numero massimo di dispositivi di cui è consentita la registrazione <!-- 1270370 -->
Invece di un messaggio di errore generico, gli utenti finali con dispositivi Android vedranno un messaggio di errore descrittivo e interattivo: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin." (È stato raggiunto il numero massimo di dispositivi consentiti dall'amministratore IT. Rimuovere un dispositivo registrato o richiedere assistenza all'amministratore IT.)




## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.




### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
