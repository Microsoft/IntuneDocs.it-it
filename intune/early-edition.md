---
title: Edizione anticipata
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/24/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7d54cb060dc44d29c95203138396f771abbb2325
ms.sourcegitcommit: 6d69403266dbcb31c879432719798935c94917fa
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="the-early-edition-for-microsoft-intune---february-2018"></a>Edizione anticipata per Microsoft Intune - Febbraio 2018

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


<!-- 1802 start -->

### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuovo grafico di tendenza degli errori di registrazione e tabella dei motivi degli errori <!-- 1471783 -->

Nella pagina della panoramica della registrazione è possibile visualizzare la tendenza degli errori di registrazione e le prime cinque cause degli errori. Facendo clic sul grafico o sulla tabella sarà possibile espandere i dettagli per trovare consigli sulla risoluzione dei problemi e suggerimenti per la correzione.

### <a name="prevent-end-users-from-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedire agli utenti finali di aggiungere o rimuovere account nel profilo di lavoro <!-- 1728700 -->    
Quando si distribuisce l'app Gmail in un profilo Android for Work, è possibile impedire agli utenti finali di aggiungere o rimuovere account nel profilo di lavoro tramite l'impostazione **Aggiungi o rimuovi account** nel profilo delle restrizioni per dispositivi Android for Work.

### <a name="app-protection-policies-----679615---"></a>Criteri di protezione delle app <!-- 679615 -->
I criteri di Protezione app di Intune offrono la possibilità di creare criteri predefiniti globali per attivare rapidamente la protezione per tutti gli utenti nell'intero tenant.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 -->

Intune supporterà la registrazione di dispositivi da un massimo di 100 account Apple Device Enrollment Program (DEP) o Apple School Manager diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Report sullo stato integrità e lo stato minacce di Windows Defender <!--854704 -->

Per gestire i PC Windows è di fondamentale importanza comprendere l'integrità e lo stato di Windows Defender.  Intune aggiungerà nuovi report e azioni per lo stato e l'integrità dell'agente Windows Defender. Usando un report di rollup dello stato nel carico di lavoro Conformità del dispositivo è possibile visualizzare i dispositivi per i quali è necessario:

- un aggiornamento della firma
- un riavvio
- un intervento manuale
- un'analisi completa
- un intervento per altri stati dell'agente

In alcuni casi, è possono eseguire azioni correttive remote, ad esempio l'attivazione di un aggiornamento della firma.  Il report indica anche il numero di PC per i quali è indicato **Pulisci**.

Un report di analisi per ogni categoria di stato elenca i singoli PC che richiedono attenzione o quelli per i quali è indicato **Pulisci**.

### <a name="protocol-exceptions-for-applications---1035509-eeready--"></a>Eccezioni di protocollo per le applicazioni <!--1035509 eeready-->

Sarà possibile creare eccezioni ai criteri di trasferimento dati della gestione di applicazioni mobili (MAM) di Intune per aprire specifiche applicazioni non gestite. Le applicazioni devono essere considerate attendibile da IT. A differenza delle eccezioni create, il trasferimento dati rimarrà limitato alle applicazioni gestire da Intune quando i criteri di trasferimento dati sono impostati **solo per le app gestite**. È possibile creare le restrizioni tramite protocolli (iOS) o pacchetti (Android).

Ad esempio, è possibile aggiungere il pacchetto Webex come eccezione ai criteri di trasferimento dati MAM. In questo modo i collegamenti Webex in un messaggio di posta elettronica di Outlook gestito possono essere aperti direttamente nell'applicazione Webex. Il trasferimento dati rimarrà limitato nelle altre applicazioni non gestite.

### <a name="customize-your-company-portal-themes-with-hex-codes---1049561-eeready--"></a>Personalizzare i temi del portale aziendale con codici esadecimali <!--1049561 eeready-->

Sarà possibile personalizzare il colore del tema nelle app Portale aziendale usando codici esadecimali. Quando si immette il codice esadecimale, Intune determina il colore del testo che offre il livello di contrasto massimo tra colore del testo e colore di sfondo in base agli [standard WCAG 2.0](http://www.w3.org/TR/WCAG20). È possibile visualizzare in anteprima un confronto tra il colore del testo e il logo della società e il colore in **App per dispositivi mobili** > **Portale aziendale**. 

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252---"></a>Nuove impostazioni di Windows Defender Credential Guard aggiunte alle impostazioni di Endpoint Protection <!--1102252 --> 

Nuove impostazioni di [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard] verranno aggiunte in **Configurazione del dispositivo** > **Profili** > **Endpoint Protection**. Verranno aggiunte le impostazioni seguenti: 

- Livello di sicurezza della piattaforma: specificare se abilitare il livello di sicurezza della piattaforma al successivo riavvio. La sicurezza basata sulla virtualizzazione richiede l'avvio protetto. La sicurezza basata sulla virtualizzazione può essere abilitata facoltativamente con l'uso di protezioni di accesso diretto alla memoria (DMA). Le protezioni DMA richiedono supporto hardware e verranno abilitate solo nei dispositivi configurati correttamente.
- Sicurezza basata sulla virtualizzazione: specificare se abilitare la sicurezza basata sulla virtualizzazione al successivo riavvio. 
- Windows Defender Credential Guard: attivare Credential Guard con la sicurezza basata sulla virtualizzazione per proteggere le credenziali al successivo riavvio quando sono abilitati il livello di sicurezza della piattaforma con avvio protetto e la sicurezza basata sulla virtualizzazione. Le opzioni disponibili sono **Disabilitato**, **Abilitato con blocco UEFI**, **Abilitato senza blocco** e **Non configurato**. 
  - L'opzione "Disabilitato" disattiva Credential Guard in modalità remota se attivato precedentemente tramite l'opzione "Abilitato senza blocco".

  - L'opzione "Abilitato con blocco UEFI" garantisce che Credential Guard non possa essere disabilitato con una chiave del Registro di sistema o tramite Criteri di gruppo. Per disabilitare Credential Guard dopo aver usato questa impostazione, è necessario impostare Criteri di gruppo su "Disabilitato" e rimuovere la funzionalità di sicurezza da ogni computer, con un utente fisicamente presente, per cancellare la configurazione mantenuta in UEFI. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

  - L'opzione "Abilitato senza blocco" consente di rimuovere Credential Guard in modalità remota tramite Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 (versione 1511 o successiva).

  - L'opzione "Non configurato" consente di non definire l'impostazione dei criteri. Poiché l'impostazione del criterio non viene scritta nel Registro di sistema, non influisce in alcun modo su computer o utenti. Se è presente un'impostazione corrente nel Registro di sistema, l'impostazione non verrà modificata.

### <a name="synchronize-and-deploy-sparsely-bundled-windows-store-for-business-apps---1222672---"></a>Sincronizzare e distribuire Windows Store in bundle per le app aziendali <!--1222672 -->
Le app offline acquistate da Windows Store per le aziende verranno sincronizzate nel portale di Intune. Sarà quindi possibile quindi distribuire le app ai gruppi di dispositivi o ai gruppi di utenti. Le app offline vengono installate da Intune, non dallo Store.

### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Reimpostare le password per i dispositivi Android O <!-- 1238299 -->
Sarà possibile reimpostare le password per i dispositivi Android O registrati. Quando si invia una richiesta "Reimposta password" in un dispositivo Android O, viene impostata una nuova password di sblocco del dispositivo o una nuova richiesta di verifica del profilo gestito per l'utente corrente. La password o la richiesta di verifica viene inviata in base alla presenza di un proprietario del profilo o di un proprietario del dispositivo e viene resa effettiva immediatamente.

### <a name="local-device-security-option-settings----1251887---"></a>Impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1251887 -->
Sarà possibile abilitare le impostazioni di sicurezza sui dispositivi Windows 10 usando le nuove impostazioni delle opzioni di sicurezza dei dispositivi locali. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nuove impostazioni della stampante per i profili di formazione <!-- 1308900 -->

Per i profili di formazione, le nuove impostazioni saranno disponibili nella categoria **Stampanti**: **Stampanti**, **Stampante predefinita**, **Aggiungi nuove stampanti**. 

### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nuove impostazioni di privacy per le restrizioni dei dispositivi <!--1308926 -->

Saranno disponibili due nuove impostazioni di privacy per i dispositivi:

- **Pubblica le attività utente**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità per l'attività.

- **Solo attività locali**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità solo per l'attività locale.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Supporto del portale aziendale macOS per le registrazioni che usano il manager di registrazione dispositivi <!-- 1352411 -->

Gli utenti potranno usare il manager di registrazione dispositivi durante la registrazione nel portale aziendale macOS.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nuove impostazioni per il browser Edge <!--1469166 -->

Le due nuove impostazioni per il **percorso di Preferiti** e le **modifiche a Preferiti** saranno disponibili per i dispositivi con browser Microsoft Edge. 

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dati crittografati di Windows Information Protection (WIP) nei risultati di ricerca di Windows <!-- 1469193 -->

Una nuova impostazione nei criteri di Windows Information Protection (WIP) consentirà di controllare se i dati crittografati WIP vengono inclusi nei risultati di ricerca di Windows.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Supporto di app line-of-business (LOB) per macOS <!-- 1473977 -->
Intune offrirà la possibilità di installare le app LOB macOS. Le app LOB sono le app per le quali viene fornito il file di installazione e viene usato Intune per installare l'app nel dispositivo. Per offrire il supporto delle app LOB macOS, è necessario usare lo strumento per la disposizione testo per app di Microsoft Intune per macOS per pre-elaborare le app line-of-business (LOB) macOS.

### <a name="configure-resource-account-settings-for-surface-hubs----1475674---"></a>Configurare le impostazioni dell'account della risorsa per i dispositivi Surface Hub <!-- 1475674 -->

Sarà possibile configurare in modalità remota le impostazioni dell'account della risorsa per i dispositivi Surface Hub.

L'account della risorsa viene usato dal dispositivo Surface Hub per l'autenticazione con Skype/Exchange per poter partecipare a una riunione. Creare un account della risorsa univoco in modo che il dispositivo Surface Hub compaia nella riunione come sala riunioni. Ad esempio, l'account della risorsa potrebbe essere visualizzato come **Sala riunioni B41/6233**.

> [!NOTE]
> - Se non si specifica alcun valore nei campi, gli attributi configurati in precedenza sul dispositivo verranno sostituiti.
>
> - Le proprietà dell'account della risorsa possono essere modificate dinamicamente nel dispositivo Surface Hub. Ad esempio, nel caso in cui sia attivata la rotazione delle password. Di conseguenza, è possibile che i valori nella console di Azure non riflettano immediatamente la realtà del dispositivo. 
>
>   Per individuare la configurazione corrente nel dispositivo Surface Hub, i dati dell'account della risorsa possono essere inclusi nell'inventario hardware (per il quale è già impostato un intervallo di 7 giorni) o come proprietà di sola lettura. Per una maggior precisione dopo l'esecuzione dell'azione remota, è possibile ottenere lo stato dei parametri subito dopo l'esecuzione dell'azione per aggiornare l'account e i parametri nel dispositivo Surface Hub.

### <a name="ios-app-provisioning-configuration----1581650---"></a>Configurazione del provisioning delle app iOS <!-- 1581650 -->
Sarà possibile assegnare i profili di provisioning delle app iOS per impedire la scadenza delle app includendo o escludendo i gruppi di sicurezza.

### <a name="new-windows-defender-exploit-guard-settings----631893---"></a>Nuove impostazioni di Windows Defender Exploit Guard <!-- 631893 -->

Saranno disponibili sei nuove impostazioni di **Riduzione della superficie di attacco** e funzionalità **Accesso controllato alle cartelle: Protezione delle cartelle** avanzate. Queste impostazioni sono disponibili in: Configurazione del dispositivo\Profili\
Crea profilo\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco

|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Protezione ransomware avanzata|Abilitato, Controllo, Non configurato|Usare una protezione ransomware aggressiva.|
|Flag della sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows|Abilitato, Controllo, Non configurato|Impostare flag per la sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows (lsass.exe).|
|Creazione di processi dai comandi PSExec e WMI|Blocca, Controllo, Non configurato|Bloccare le creazioni di processi originate dai comandi PSExec e WMI.|
|Processi non attendibili e non firmati eseguiti da USB|Blocca, Controllo, Non configurato|Bloccare i processi non attendibili e non firmati eseguiti da USB.|
|File eseguibili che non soddisfano i criteri di prevalenza, età o elenco attendibile|Blocca, Controllo, Non configurato|Bloccare l'esecuzione dei file eseguibili se non soddisfano i criteri di prevalenza, età o elenco attendibile.|

#### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Protezione delle cartelle (già implementata)|Non configurato, Abilita, Solo controllo (già implementata)<br><br> **Nuove**<br>Blocco della modifica del disco, controllo della modifica del disco|
Proteggere file e cartelle da modifiche non autorizzate eseguite da applicazioni non compatibili.<br><br>**Abilitare**: impedire alle app non attendibili di modificare o eliminare file nelle cartelle protette e di scrivere nei settori del disco.<br><br>
**Bloccare solo la modifica del disco**:<br>Impedire alle app non attendibili di scrivere nei settori del disco. Le app non attendibili possono ancora modificare o eliminare i file nelle cartelle protette.|

### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nuove impostazioni di Windows Defender Application Guard <!-- 1631890 -->

- **Abilitare l'accelerazione grafica**

Gli amministratori potranno attivare un processore di grafica virtuale per Windows Defender Application Guard. Questa impostazione consente alla CPU di passare il rendering della grafica alla vGPU. Ciò può migliorare le prestazioni durante l'uso di siti Web con molta grafica o la riproduzione di video all'interno del contenitore.

- **SaveFilestoHost**

Gli amministratori potranno consentire il passaggio dei file da Microsoft Edge in esecuzione nel contenitore al file system dell'host. L'attivazione di questa impostazione consentirà agli utenti di scaricare i file da Microsoft Edge nel contenitore nel file system dell'host.

### <a name="see-enrollment-restrictions-per-user----1634444---"></a>Visualizzare le restrizioni di registrazione per i singoli utenti <!-- 1634444 -->
Nel pannello della risoluzione dei problemi saranno visibili le restrizioni di registrazione attive per ogni utente.

### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurazione di un'app MSI per dispositivi mobili con aggiornamento automatico <!-- 1740840 -->
Sarà possibile configurare un'app MSI per dispositivi mobili con aggiornamento automatico per ignorare il processo di controllo delle versioni. Questa funzionalità consente di evitare una race condition. Ad esempio, questa situazione può verificarsi quando l'app viene aggiornata automaticamente dallo sviluppatore di app e anche da Intune. In entrambi i casi è possibile che si tenti di forzare una versione dell'app nel client di Windows creando un conflitto.

### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133---"></a>Nuove impostazioni di sicurezza del sistema per Windows 10 e nuovi criteri di conformità <!--1704133 -->

Saranno disponibili nuove impostazioni di conformità di Windows 10, inclusa la richiesta di Firewall e Windows Defender Antivirus.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusione ed esclusione dell'assegnazione delle app in base ai gruppi per Android Enterprise <!-- 1813081 -->
Durante l'assegnazione delle app e dopo la selezione di un tipo di assegnazione, Android Enterprise (precedentemente noto come Android for Work) supporterà la funzionalità di esclusione.


### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Insiemi correlati di licenze per le app supportati in Intune <!-- 1864117 -->
Intune nel portale di Azure supporterà gli insiemi correlati di licenze per le app come elemento app singolo nell'interfaccia utente. Inoltre, tutte le app con licenza offline sincronizzate da Microsoft Store per le aziende verranno consolidate in una singola voce di app e verrà eseguita la migrazione di tutti i dettagli di distribuzione dei singoli pacchetti nella singola voce. Per visualizzare gli insiemi correlati di licenze per le app nel portale di Azure, selezionare **Licenze dell'app** dal pannello **App per dispositivi mobili**.

<!-- the following are present prior to 1802 -->

### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625---"></a>Nuova opzione per l'autenticazione utente per la registrazione in blocco Apple <!-- 747625 -->
Intune offre la possibilità di autenticare i dispositivi con l'app Portale aziendale per i metodi di registrazione seguenti:

- Programma di registrazione del dispositivo mobile di Apple:
- Apple School Manager
- Registrazione di Apple Configurator

Quando si usa l'opzione Portale aziendale, l'autenticazione a più fattori di Azure Active Directory può essere applicata senza bloccare questi metodi di registrazione.

Quando si usa l'opzione Portale aziendale, Intune ignora l'autenticazione utente nell'Assistente configurazione di iOS per la registrazione dell'affinità utente. Questo significa che il dispositivo viene inizialmente registrato come dispositivo senza utente e pertanto non riceverà le configurazioni o i criteri dei gruppi utenti, ma solo le configurazioni e i criteri per i gruppi di dispositivi. Tuttavia, Intune installerà automaticamente l'app Portale aziendale nel dispositivo. Il primo utente che avvia l'app Portale aziendale e vi accede verrà associato al dispositivo in Intune. A questo punto, l'utente riceverà le configurazioni e i criteri dei gruppi utenti. L'associazione dell'utente non può essere modificata senza eseguire di nuovo la registrazione.

### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 -->
Intune supporterà la registrazione di dispositivi da un massimo di 100 account Apple Device Enrollment Program (DEP) o Apple School Manager diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963---"></a>Selezionare le categorie di dispositivi usando le impostazioni Accedi all'azienda o all'istituto di istruzione <!-- 1058963 -->
Se è stato abilitato il [mapping dei gruppi di dispositivi](https://docs.microsoft.com/intune/device-group-mapping), agli utenti in Windows 10 verrà richiesto di selezionare una categoria di dispositivi dopo la registrazione tramite il pulsante **Connetti** in **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione** o durante la Configurazione guidata.

### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Assegnazione dei criteri di conformità a dispositivi in gruppi di dispositivi <!--1307012 -->

Sarà possibile assegnare i criteri di conformità agli utenti in gruppi utenti. Sarà possibile assegnare i criteri di conformità ai dispositivi in gruppi di dispositivi.

### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dati crittografati di Windows Information Protection (WIP) nei risultati di ricerca di Windows <!-- 1469193 -->

Una nuova impostazione nei criteri di Windows Information Protection (WIP) consentirà di controllare se i dati crittografati WIP vengono inclusi nei risultati di ricerca di Windows.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Stampa remota su una rete protetta <!-- 1709994  -->
Le soluzioni di stampa mobile wireless di PrinterOn consentiranno agli utenti di eseguire stampe in modalità remota da qualsiasi posizione e in qualsiasi momento tramite una rete protetta. PrinterOn verrà integrato in Intune APP SDK sia per iOS che per Android. Sarà possibile assegnare i criteri di protezione delle app a questa app tramite il pannello **Criteri di protezione delle app** di Intune nella console di amministrazione. Gli utenti finali potranno scaricare l'app 'PrinterOn per Microsoft' tramite Play Store o iTunes da usare all'interno del loro ecosistema di Intune.



### <a name="microsoft-graph-api-for-intune---general-availability-----1833289---"></a>API Microsoft Graph per Intune - Disponibilità generale <!-- 1833289 -->
Le API di Intune in Microsoft Graph consentiranno l'accesso programmatico a dati e metodi per l'automazione di azioni amministrative per il servizio Intune.  Con la **disponibilità generale** di queste API, clienti, partner e sviluppatori potranno sfruttare le API per l'integrazione con soluzioni interne o commerciali correlate a o che richiedono il supporto di Intune o altri servizi Microsoft disponibili tramite Microsoft Graph.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Criteri di protezione delle app <!-- 679615 -->
I criteri di Protezione app di Intune offrono la possibilità di creare criteri predefiniti globali per attivare rapidamente la protezione per tutti gli utenti nell'intero tenant.

### <a name="new-ios-device-action------1244701---"></a>Nuova azione per dispositivi iOS <!-- 1244701 -->
È possibile arrestare i dispositivi iOS 10.3 con supervisione. Questa azione arresta il dispositivo immediatamente senza avviso all'utente finale. L'azione **Shut down (supervised only)** (Arresta - solo con supervisione) è disponibile nelle proprietà del dispositivo quando si seleziona un dispositivo nel carico di lavoro **Dispositivo**.

### <a name="intune-provides-the-account-move-operation-----1573558-1579830---"></a>Intune offre l'operazione Account Move (Spostamento account) <!-- 1573558, 1579830 -->
L'operazione **Account Move** (Spostamento account) esegue la migrazione di un tenant da un'unità di scala di Azure (ASU) a un'altra. L'operazione **Account Move** (Spostamento account) può essere usata per entrambi gli scenari avviati dall'utente, quando si chiama il team di supporto di Intune per richiederla, e può anche essere uno scenario basato su Microsoft nei casi in cui Microsoft deve apportare modifiche al servizio nel back-end. Durante un'operazione **Account Move** (Spostamento account), il tenant passa alla modalità di sola lettura (ROM). Durante il periodo ROM, le operazioni sui servizi come la registrazione, la ridenominazione di dispositivi e l'aggiornamento dello stato di conformità avranno esito negativo.

La modifica elimina la confusione che si verifica quando la stessa app viene assegnata a più gruppi con finalità di app diverse.

Se si vuole rendere disponibile l'app nel portale di Information Worker e nel portale aziendale prima del rilascio di novembre del servizio, sono disponibili due opzioni:

1. Rimuovere l'assegnazione **Non applicabile** per il gruppo.
2. Creare un nuovo gruppo che non contiene membri con la finalità **Richiesto e disponibile** e assegnare il gruppo come **Non applicabile**.

Per altre informazioni, vedere [How to assign apps to groups with Microsoft Intune](apps-deploy.md) (Come assegnare app ai gruppi con Microsoft Intune).

> [!Note]
> Dopo il rilascio non sarà più possibile visualizzare o modificare le assegnazioni delle app MDM (Mobile Device Management) nella console classica di Intune. È possibile tuttavia usare la console di Azure o l'API Graph di Intune per eseguire le assegnazioni delle app.

### <a name="configure-an-ios-app-pin----1586774---"></a>Configurare il PIN di un'app iOS <!-- 1586774 -->
Sarà presto possibile richiedere un PIN per le app iOS di destinazione. È possibile configurare la richiesta e la data di scadenza in giorni del PIN tramite il portale di Azure. Quando necessario, all'utente viene richiesto di impostare e usare un nuovo PIN prima di ottenere l'accesso a un'app iOS. Questa funzionalità è supportata solo dalle app iOS con la protezione dell'app abilitata con Intune App SDK.

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS <!--1412866-->

Verrà rilasciato un importante aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS. L'aggiornamento include una riprogettazione grafica completa che conferisce all'app un aspetto moderno, maggiore usabilità e accessibilità. Tutte le attuali funzionalità del Portale aziendale per iOS saranno mantenute.

Tramite il programma Apple TestFlight viene offerta una versione non definitiva dell'app Portale aziendale aggiornata per iOS che l'utente può usare e per la quale può inviare i propri commenti e suggerimenti. Effettuare l'iscrizione in https://aka.ms/intune_ios_cp_testflight per l'accesso a TestFlight. 

![immagini teaser per la nuova app del Portale aziendale per ios](./media/ios-cp-app-redesign-1801-teaser.png)

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->   
Usando Azure Active Directory (Azure AD) è possibile limitare l'accesso ai siti Web su dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure.

<!-- the following are present prior to 1709 -->
### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Protezione app di Intune e strumenti di sviluppo MDX Citrix <!-- 709185 -->
È possibile gestire i dispositivi e le app usando in combinazione Citrix XenMobile MDX e Microsoft Intune. Ciò consente di gestire le app con i criteri di protezione delle app di Intune usando allo stesso tempo la tecnologia mVPN di Citrix.

È disponibile un repository di codice che contiene lo strumento di wrapping delle app di Intune e Intune App SDK per iOS e Android, per l'integrazione con la tecnologia mVPN MDX di Citrix.

<!-- the following are present prior to 1711 -->

### <a name="redirecting-macos-users-to-the-new-company-portal-app---1380728--"></a>Reindirizzamento degli utenti macOS alla nuova app Portale aziendale <!--1380728-->   
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


