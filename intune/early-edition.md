---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99b1436fdf718b54f54f7e90835668d4a632b7ce
ms.sourcegitcommit: 390a4be5aa36007c36fb6a5abcfe8d20bc862a4b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="the-early-edition-for-microsoft-intune---march-2018"></a>Edizione anticipata per Microsoft Intune - Marzo 2018

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non condividere queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
>Le seguenti modifiche di Intune sono in fase di sviluppo. Per altre informazioni sulle nuove funzionalità ibride, vedere la pagina delle [Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->

## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Supporto di Exchange Connector multipli <!-- 2070451 -->

Non è più previsto il limite di un Microsoft Intune Exchange Connector per tenant. Intune supporta Exchange Connector multipli per consentire la configurazione dell'accesso condizionale in Intune per più organizzazioni di Exchange locali.

Con un On-premises Exchange Connector di Intune è possibile gestire l'accesso dei dispositivi alle cassette postali di Exchange locali in base al fatto che i dispositivi siano registrati o meno in Intune e siano conformi ai criteri di conformità dei dispositivi di Intune. Per configurare un connettore, scaricare l'On-premises Exchange Connector di Intune dal portale di Azure e installarlo in un server dell'organizzazione di Exchange. Nel dashboard di Microsoft Intune scegliere **Accesso locale**, quindi nella sezione **Installazione**, scegliere **Connettore per Exchange ActiveSync**. Scaricare l'On-premises Exchange Connector e installarlo in un server della propria organizzazione di Exchange. Ora che non vige più il limite di Exchange Connector per tenant, gli utenti che hanno più organizzazioni di Exchange possono seguire lo stesso processo per scaricare e installare un connettore per ogni organizzazione di Exchange aggiuntiva.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Supporto previsto per i nuovi client Cisco AnyConnect per iOS <!-- 1333708 -->

I nuovi profili VPN creati per Cisco AnyConnect per IOS funzioneranno con Cisco AnyConnect 4.0.7 e versioni successive. I profili VPN di Cisco AnyConnect per iOS esistenti verranno contrassegnati con la dicitura **Cisco Legacy AnyConnect** e continueranno a funzionare con Cisco AnyConnect 4.0.5x come accade oggi.

> [!NOTE]
> Questa modifica riguarda solo iOS perché continuerà ad esistere una sola opzione Cisco AnyConnect per Android, Android for Work e macOS.

#### <a name="more-information"></a>Altre informazioni

Per supportare la nuova app è necessario creare un nuovo profilo VPN di Cisco AnyConnect per iOS perché la nuova app Cisco AnyConnect e l'app Cisco Legacy AnyConnect sono due app distinte. Se il client AnyConnect viene gestito nell'ambiente in uso, è necessario distribuire anche la nuova app Cisco AnyConnect. Per completare un aggiornamento, è inoltre necessario eliminare il profilo VPN di Cisco Legacy AnyConnect e rimuovere l'app Cisco Legacy AnyConnect.

Nella versione iniziale, l'integrazione del controllo di accesso alla rete (NAC) per i nuovi client AnyConnect non funziona. È in corso un'operazione congiunta con Cisco per attivare l'integrazione NAC in una futura versione di Intune.

### <a name="enhanced-jailbreak-detection----846515---"></a>Rilevamento ottimizzato per jailbreak <!-- 846515 -->

Il rilevamento ottimizzato per jailbreak è una nuova impostazione di conformità che migliorerà la valutazione dei dispositivi jailbroken da parte di Intune. L'impostazione usa i servizi di posizione per attivare con maggiore frequenza l'archiviazione del dispositivo con Intune. Ciò può influire sull'utilizzo della batteria.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacità di distribuire le app line-of-business (LOB) necessarie a tutti gli utenti nei dispositivi Windows 10 Desktop <!-- 1627835 RS4 -->
I clienti saranno in grado di distribuire le app line-of-business di Windows 10 da installare in contesti di dispositivo. In questo modo le app saranno disponibili per tutti gli utenti del dispositivo. Questa opzione è disponibile solo per i dispositivi Windows 10 Desktop.

### <a name="expiring-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>App line-of-business (LOB) in scadenza per Microsoft Intune <!-- 748789 -->
Intune segnala nel portale di Azure le app line-of-business che stanno per scadere. Dopo che una nuova versione dell'app line-of-business è stata caricata, Intune rimuove la notifica di scadenza dall'elenco delle app.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registrazione con il portale aziendale migliorata <!-- 1874230-->
Gli utenti che registrano un dispositivo tramite il portale aziendale in Windows 10 build 1703 e successive riusciranno a completare il primo passaggio della registrazione senza uscire dall'app.

### <a name="new-management-name-column----1333586---"></a>Nuova colonna Nome di gestione <!-- 1333586 -->
Una nuova colonna denominata **Nome di gestione** verrà aggiunta al pannello Dispositivi. Si tratta di un nome generato automaticamente e non modificabile assegnato a ogni dispositivo, in base alla formula seguente:
- Nome predefinito per tutti i dispositivi: <username>_<devicetype>_<enrollmenttimestamp>
- Per i dispositivi aggiunti in blocco: < PackageId/ProfileId >_<DeviceType>_<EnrollmentTime>

Questa colonna è facoltativa nel pannello Dispositivi. Non sarà disponibile per impostazione predefinita e sarà possibile accedervi solo tramite il selettore di colonna. Il nome del dispositivo non è interessato da questa nuova colonna.

### <a name="new-settings-for-windows-defender-security-center-notifications-device-configuration-profile----1631906---"></a>Nuove impostazioni per il profilo di configurazione del dispositivo di notifiche Windows Defender Security Center (WDSC)<!-- 1631906 -->

Al profilo di configurazione del dispositivo di notifiche Windows Defender Security Center (WDSC) verranno aggiunte tre nuove impostazioni.

Gli amministratori saranno in grado di:

- Nascondere la colonna Identità
- Nascondere la colonna Hardware e le relative impostazioni secondarie
- Nascondere la colonna Ransomware (ripristino dei file di Onedrive for Business)

Quando nell'app WDSC queste colonne sono nascoste, gli utenti finali non potranno configurare queste impostazioni e tutte le notifiche associate ai componenti nascosti non verranno generate.

### <a name="mam-policies-targeted-based-on-management-state----1665993---"></a>Criteri MAM assegnati in base allo stato di gestione <!-- 1665993 -->

Sarà possibile assegnare i criteri MAM sulla base dello stato di gestione del dispositivo:

- **Dispositivi iOS**: sarà possibile includere i dispositivi non gestiti (solo MAM) o i dispositivi gestiti da Intune.
- **Dispositivi Android**: sarà possibile includere i dispositivi non gestiti, i dispositivi gestiti da Intune e i profili Android Enterprise gestiti da Intune (in precedenza denominati Android for Work).

### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459--"></a>Configurare Gatekeeper per controllare l'origine del download delle app macOS <!-- 1690459-->

Sarà possibile configurare Gatekeeper affinché protegga i dispositivi controllando da dove le app possono essere scaricate. Sarà possibile configurare le seguenti origini di download: **Mac App Store**, **Mac App Store e sviluppatori identificati** o **Ovunque**. Sarà inoltre possibile definire se gli utenti possono installare un'app usando CTRL + clic per eseguire l'override di questi controlli di Gatekeeper.

Queste impostazioni sono disponibili in **Configurazione del dispositivo** -> **Crea profilo** -> **macOS** -> **Endpoint protection**.

### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurare il firewall dell'applicazione Mac <!-- 1690461 -->

Sarà possibile configurare il firewall dell'applicazione Mac. Usare questa impostazione per controllare le connessioni in base all'applicazione, anziché in base alla porta. Questo rende più semplice ottenere i vantaggi della protezione con firewall e contribuisce a impedire che app indesiderate assumano il controllo delle porte di rete aperte per app legittime.

Questa funzione è disponibile in **Configurazione del dispositivo** -> **Crea profilo** -> **macOS** -> **Endpoint protection**.

Dopo aver abilitato l'impostazione del firewall, configurare il firewall utilizzando una delle due strategie seguenti:

- Bloccare tutte le connessioni in ingresso

   Vengono bloccate tutte le connessioni in ingresso per i dispositivi di destinazione. Se si sceglie questa opzione, le connessioni in ingresso verranno bloccate per tutte le app.

- Consentire o bloccare app specifiche

   È possibile consentire o bloccare la ricezione di connessioni in ingresso per app specifiche. È inoltre possibile abilitare la modalità mascheramento per impedire l'invio di risposte alle richieste di probe.

#### <a name="more-information"></a>Altre informazioni

- Bloccare tutte le connessioni in ingresso

   Con questa opzione si impedisce a tutti i servizi di condivisione, ad esempio Condivisione file e Condivisione schermo, di ricevere le connessioni in ingresso. I servizi di sistema che rimangono autorizzati a ricevere connessioni in ingresso sono:
   - configd: implementa DHCP e altri servizi di configurazione di rete
   - mDNSResponder: implementa Bonjour
   - racoon: implementa IPSec

   Per utilizzare i servizi di condivisione, assicurarsi che **Connessioni in ingresso** sia impostata su **Non configurato** e non **Blocca**.

- Modalità mascheramento

   Abilitare questa modalità per impedire che il computer risponde alle richieste di probe. Il computer risponde comunque alle richieste in ingresso provenienti da app autorizzate. Le richieste impreviste, ad esempio le richieste ICMP (ping), vengono ignorate.


### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aggiornamento dell'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android <!--1631531 -->

L'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android verrà aggiornata e adattata alle procedure consigliate per le app Android. L'aggiornamento dell'app Portale aziendale per Android che avverrà nei prossimi mesi consisterà nella suddivisione della voce di menu **Guida e commenti e suggerimenti** in due distinte voci di menu **Guida** e **Invia commenti e suggerimenti**. La pagina **Guida** conterrà una sezione **Domande frequenti** e il pulsante **Supporto e-mail** per invitare gli utenti a caricare log in Microsoft e a inviare e-mail al supporto aziendale per descrivere i problemi incontrati. **Invia commenti e suggerimenti** guiderà l'utente nella procedura standard Microsoft per l'invio di commenti e suggerimenti che richiederà all'utente di indicare una preferenza, una mancanza di preferenza o un'idea.

### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Categorie libro personalizzate per eBook di Volume Purchase Program (VPP) <!-- 1488911 -->
Sarà possibile creare categorie eBook personalizzate a cui assegnare eBook VPP. Gli utenti finali potranno vedere le categorie eBook appena create e i libri a esse assegnati.

### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868--"></a>HoloLens e Surface Hub vengono ora visualizzati nell'elenco dei dispositivi <!--1725868-->

Viene aggiunto il supporto per la visualizzazione dei dispositivi HoloLens e Surface Hub registrati in Intune nell'app del portale aziendale per Android.

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Supporto di Edge in dispositivi mobili per i criteri di protezione delle app di Intune <!-- 1817882 -->

Il browser Microsoft Edge per i dispositivi mobili supporterà i criteri di protezione delle app definiti in Intune.

### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763-eeready--"></a>Usare il nome distinto completo come soggetto per il certificato SCEP <!--2221763 eeready-->
Quando si crea un profilo certificato SCEP, immettere il nome del soggetto. Sarà possibile usare il nome distinto completo come soggetto. Per **Nome soggetto**, selezionare **Personalizzato** e immettere `CN={{OnPrem_Distinguished_Name}}`. Usare la variabile `{{OnPrem_Distinguished_Name}}`, assicurarsi di sincronizzare l'attributo utente `onpremisesdistingishedname` usando [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837-eeready--"></a>Ai dispositivi iOS viene richiesto un codice PIN ogni 15 minuti <!--1550837 eeready-->
Dopo che i criteri di conformità o di configurazione vengono applicati a un dispositivo iOS, agli utenti viene richiesto ogni 15 minuti di impostare un codice PIN. Tale richiesta verrà visualizzata continuamente fino a quando non verrà impostato un PIN.

### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983-eeready--"></a>Attivare la condivisione dei contatti Bluetooth - Android for Work <!--1098983 eeready-->
Per impostazione predefinita, Android non consente la sincronizzazione dei contatti nel profilo di lavoro con i dispositivi Bluetooth. Di conseguenza, i contatti del profilo di lavoro non vengono visualizzati nell'ID chiamante per i dispositivi Bluetooth.

Sarà presente una nuova impostazione in **Android for Work** > **Limitazioni del dispositivo** > **Impostazioni del profilo di lavoro**:
- Contact sharing via Bluetooth (Contatto condivisione tramite Bluetooth)

L'amministratore di Intune può configurare queste impostazioni per abilitare la condivisione. Ciò è utile quando si associa un dispositivo a un dispositivo Bluetooth da usare in macchina che visualizza l'ID chiamante per l'uso del viva voce. Quando l'impostazione è abilitata, i contatti del profilo di lavoro vengono visualizzati. Quando l'impostazione non è abilitata, i contatti del profilo di lavoro non vengono visualizzati.

Si applica a: dispositivi di profilo di lavoro Android in sistemi operativi Android 6.0 e versioni successive.

### <a name="schedule-your-automatic-updates---1805514---"></a>Pianificare gli aggiornamenti automatici <!--1805514 -->

Intune offre un controllo sull'installazione di aggiornamenti automatici mediante [le impostazioni degli anelli di Windows Update](windows-update-for-business-configure.md). Sarà possibile pianificare gli aggiornamenti ricorrenti, nonché la settimana, il giorno e l'ora.

### <a name="disable-checks-on-device-restart---1805490---"></a>Disabilitare i controlli al riavvio del dispositivo <!--1805490 -->

Intune consente di [gestire gli aggiornamenti software](windows-update-for-business-configure.md). La proprietà **Verifiche al riavvio** verrà aggiunta e abilitata per impostazione predefinita. Per ignorare i controlli che vengono eseguiti generalmente quando si riavvia un dispositivo, come ad esempio gli utenti attivi, i livelli di batteria e così via, selezionare **Ignora**.

<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuovo grafico di tendenza degli errori di registrazione e tabella dei motivi degli errori <!-- 1471783 -->

Nella pagina della panoramica della registrazione è possibile visualizzare la tendenza degli errori di registrazione e le prime cinque cause degli errori. Facendo clic sul grafico o sulla tabella sarà possibile espandere i dettagli per trovare consigli sulla risoluzione dei problemi e suggerimenti per la correzione.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalizzare i temi del portale aziendale con codici esadecimali <!--1049561 -->

Sarà possibile personalizzare il colore del tema nelle app Portale aziendale usando codici esadecimali. Quando si immette il codice esadecimale, Intune determina il colore del testo che offre il livello di contrasto massimo tra colore del testo e colore di sfondo in base agli [standard WCAG 2.0](http://www.w3.org/TR/WCAG20). È possibile visualizzare in anteprima un confronto tra il colore del testo e il logo della società e il colore in **App per dispositivi mobili** > **Portale aziendale**.

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Nuove impostazioni di Windows Defender Credential Guard aggiunte alle impostazioni di Endpoint Protection <!--1102252 -->

Nuove impostazioni [Windows Defender Credential Guard] (https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] verranno aggiunte a **Configurazione del dispositivo** > **Profili** > **Endpoint Protection**. Verranno aggiunte le impostazioni seguenti:

- Livello di sicurezza della piattaforma: specificare se abilitare il livello di sicurezza della piattaforma al successivo riavvio. La sicurezza basata sulla virtualizzazione richiede l'avvio protetto. La sicurezza basata sulla virtualizzazione può essere abilitata facoltativamente con l'uso di protezioni di accesso diretto alla memoria (DMA). Le protezioni DMA richiedono supporto hardware e verranno abilitate solo nei dispositivi configurati correttamente.
- Sicurezza basata sulla virtualizzazione: specificare se abilitare la sicurezza basata sulla virtualizzazione al successivo riavvio.
- Windows Defender Credential Guard: attivare Credential Guard con la sicurezza basata sulla virtualizzazione per proteggere le credenziali al successivo riavvio quando sono abilitati il livello di sicurezza della piattaforma con avvio protetto e la sicurezza basata sulla virtualizzazione. Le opzioni disponibili sono **Disabilitato**, **Abilitato con blocco UEFI**, **Abilitato senza blocco** e **Non configurato**.
  - L'opzione "Disabilitato" disattiva Credential Guard in modalità remota se attivato precedentemente tramite l'opzione "Abilitato senza blocco".

  - L'opzione "Abilitato con blocco UEFI" garantisce che Credential Guard non possa essere disabilitato con una chiave del Registro di sistema o tramite Criteri di gruppo. Per disabilitare Credential Guard dopo aver usato questa impostazione, è necessario impostare Criteri di gruppo su "Disabilitato" e rimuovere la funzionalità di sicurezza da ogni computer, con un utente fisicamente presente, per cancellare la configurazione mantenuta in UEFI. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

  - L'opzione "Abilitato senza blocco" consente di rimuovere Credential Guard in modalità remota tramite Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 (versione 1511 o successiva).

  - L'opzione "Non configurato" consente di non definire l'impostazione dei criteri. Poiché l'impostazione del criterio non viene scritta nel Registro di sistema, non influisce in alcun modo su computer o utenti. Se è presente un'impostazione corrente nel Registro di sistema, l'impostazione non verrà modificata.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Reimpostare le password per i dispositivi Android O <!-- 1238299 -->
Sarà possibile reimpostare le password per i dispositivi Android O registrati. Quando si invia una richiesta "Reimposta password" in un dispositivo Android O, viene impostata una nuova password di sblocco del dispositivo o una nuova richiesta di verifica del profilo gestito per l'utente corrente. La password o la richiesta di verifica viene inviata in base alla presenza di un proprietario del profilo o di un proprietario del dispositivo e viene resa effettiva immediatamente.

### <a name="local-device-security-option-settings----1251887---"></a>Impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1251887 -->
Sarà possibile abilitare le impostazioni di sicurezza sui dispositivi Windows 10 usando le nuove impostazioni delle opzioni di sicurezza dei dispositivi locali. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nuove impostazioni della stampante per i profili di formazione <!-- 1308900 -->

Per i profili di formazione, le nuove impostazioni saranno disponibili nella categoria **Stampanti**: **Stampanti**, **Stampante predefinita**, **Aggiungi nuove stampanti**.

### <a name="ios-app-provisioning-configuration----1581650---"></a>Configurazione del provisioning delle app iOS <!-- 1581650 -->
Sarà possibile assegnare i profili di provisioning delle app iOS per impedire la scadenza delle app includendo o escludendo i gruppi di sicurezza.

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nuove impostazioni di Windows Defender Application Guard <!-- 1631890 -->

- **Abilitare l'accelerazione grafica**

Gli amministratori potranno attivare un processore di grafica virtuale per Windows Defender Application Guard. Questa impostazione consente alla CPU di passare il rendering della grafica alla vGPU. Ciò può migliorare le prestazioni durante l'uso di siti Web con molta grafica o la riproduzione di video all'interno del contenitore.

- **SaveFilestoHost**

Gli amministratori potranno consentire il passaggio dei file da Microsoft Edge in esecuzione nel contenitore al file system dell'host. L'attivazione di questa impostazione consentirà agli utenti di scaricare i file da Microsoft Edge nel contenitore nel file system dell'host.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusione ed esclusione dell'assegnazione delle app in base ai gruppi per Android Enterprise <!-- 1813081 -->
Durante l'assegnazione delle app e dopo la selezione di un tipo di assegnazione, Android Enterprise (precedentemente noto come Android for Work) supporterà la funzionalità di esclusione.

<!-- the following are present prior to 1802 -->

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Assegnazione dei criteri di conformità a dispositivi in gruppi di dispositivi <!--1307012 -->

Sarà possibile assegnare i criteri di conformità agli utenti in gruppi utenti. Sarà possibile assegnare i criteri di conformità ai dispositivi in gruppi di dispositivi.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Criteri di protezione delle app <!-- 679615 -->
I criteri di Protezione app di Intune offrono la possibilità di creare criteri predefiniti globali per attivare rapidamente la protezione per tutti gli utenti nell'intero tenant.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurare il PIN di un'app iOS <!-- 1586774 -->
Sarà presto possibile richiedere un PIN per le app iOS di destinazione. È possibile configurare la richiesta e la data di scadenza in giorni del PIN tramite il portale di Azure. Quando necessario, all'utente viene richiesto di impostare e usare un nuovo PIN prima di ottenere l'accesso a un'app iOS. Questa funzionalità è supportata solo dalle app iOS con la protezione dell'app abilitata con Intune App SDK.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->   
Usando Azure Active Directory (Azure AD) è possibile limitare l'accesso ai siti Web su dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Reindirizzamento degli utenti macOS alla nuova app Portale aziendale <!--1380728-->   
Quando un utente finale accede al sito Web del portale aziendale per registrare il proprio dispositivo macOS, l'utente viene indirizzato al download della nuova app del portale aziendale per macOS per completare il processo. Ciò si verifica per i dispositivi macOS che usano OS X El Capitan 10.11 o versioni successive. 

<!-- the following are present prior to 1709 -->

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Messaggio di errore migliorato quando un utente raggiunge il numero massimo di dispositivi di cui è consentita la registrazione <!-- 1270370 -->
Invece di un messaggio di errore generico, gli utenti finali con dispositivi Android vedranno un messaggio di errore descrittivo e interattivo: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin." (È stato raggiunto il numero massimo di dispositivi consentiti dall'amministratore IT. Rimuovere un dispositivo registrato o richiedere assistenza all'amministratore IT.)



## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.



### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
