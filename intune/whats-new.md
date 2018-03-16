---
title: "Novità di Microsoft Intune"
titlesuffix: Azure portal
description: "Informazioni sulle novità nel portale di Intune di Azure"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 01/02/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7490302c7bd928417cdf946cbbf74f8b8b7531ed
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre a indicazioni sulle [modifiche previste](#whats-coming), [notifiche importanti](#notices) sul servizio e informazioni sulle [versioni precedenti](whats-new-archive.md).

> [!Note]
> Per informazioni sulle nuove funzionalità di gestione ibrida dei dispositivi mobili (MDM), vedere la [pagina Novità della gestione ibrida di dispositivi mobili](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   


## <a name="week-of-february-19-2018"></a>Settimana del 19 febbraio 2018
### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 -->
 
Intune supporta ora la registrazione di dispositivi da un massimo di 100 account Apple Device Enrollment Program (DEP) o Apple School Manager diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Visualizzare le restrizioni di registrazione per i singoli utenti <!-- 1634444 eeready wnready -->
Nel pannello **Risoluzione dei problemi** è ora possibile visualizzare le restrizioni di registrazione applicate per ogni utente selezionando **Restrizioni registrazione** dall'elenco **Assegnazioni**.

### <a name="device-management"></a>Gestione dei dispositivi
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Report sullo stato integrità e lo stato minacce di Windows Defender <!--854704 -->

Per gestire i PC Windows è di fondamentale importanza comprendere l'integrità e lo stato di Windows Defender.  Con questo aggiornamento Intune aggiunge nuovi report e azioni per lo stato e l'integrità dell'agente Windows Defender. Usando un report di rollup dello stato nel carico di lavoro Conformità del dispositivo è possibile visualizzare i dispositivi per i quali è necessario:
- un aggiornamento della firma
- Riavvia
- un intervento manuale
- un'analisi completa
- un intervento per altri stati dell'agente

Un report di analisi per ogni categoria di stato elenca i singoli PC che richiedono attenzione o quelli per i quali è indicato **Pulisci**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nuove impostazioni di privacy per le restrizioni dei dispositivi <!--1308926 -->
Sono ora disponibili due nuove impostazioni di privacy per i dispositivi:
- **Pubblica le attività utente**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità per l'attività.
- **Solo attività locali**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità solo per l'attività locale.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nuove impostazioni per il browser Microsoft Edge <!--1469166 -->
Le due nuove impostazioni per il **percorso di Preferiti** e le **modifiche a Preferiti** sono ora disponibili per i dispositivi con browser Microsoft Edge. 

### <a name="app-management"></a>Gestione delle app
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Eccezioni di protocollo per le applicazioni <!--1035509 -->

Ora è possibile creare eccezioni ai criteri di trasferimento dati della gestione di applicazioni mobili (MAM) di Intune per aprire specifiche applicazioni non gestite. Le applicazioni devono essere considerate attendibile da IT. A differenza delle eccezioni create, il trasferimento dati rimane limitato alle applicazioni gestire da Intune quando i criteri di trasferimento dati sono impostati **solo per le app gestite**. È possibile creare le restrizioni tramite protocolli (iOS) o pacchetti (Android).
 
Ad esempio, è possibile aggiungere il pacchetto Webex come eccezione ai criteri di trasferimento dati MAM. In questo modo i collegamenti Webex in un messaggio di posta elettronica di Outlook gestito possono essere aperti direttamente nell'applicazione Webex. Il trasferimento dati rimarrà limitato nelle altre applicazioni non gestite. Per altre informazioni, vedere [Eccezioni dei criteri di trasferimento dei dati per le app](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dati crittografati di Windows Information Protection (WIP) nei risultati di ricerca di Windows <!-- 1469193 -->
Un'impostazione nei criteri di Windows Information Protection (WIP) consente ora di controllare se i dati crittografati WIP vengono inclusi nei risultati di ricerca di Windows. Impostare questa opzione dei criteri di protezione dell'app selezionando l'impostazione che **consente all'indicizzatore di Ricerca di Windows di cercare gli elementi crittografati** nelle **impostazioni avanzate** dei criteri di Windows Information Protection. I criteri di protezione dell'app devono essere impostati sulla piattaforma *Windows 10* e lo **stato di registrazione** dei criteri dell'app deve essere impostato su **Con registrazione**. Per altre informazioni, vedere [Consentire all'indicizzatore di Ricerca di Windows di cercare elementi crittografati](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurazione di un'app MSI per dispositivi mobili con aggiornamento automatico <!-- 1740840 -->
È possibile configurare un'app MSI per dispositivi mobili con aggiornamento automatico nota in modo che ignori il processo di controllo delle versioni. Questa funzionalità consente di evitare una race condition. Ad esempio, questo tipo di race condition può verificarsi quando l'app viene aggiornata automaticamente dallo sviluppatore di app e anche da Intune. In entrambi i casi è possibile che si tenti di imporre una versione dell'app in un client di Windows creando un conflitto. Per queste app MSI con aggiornamento automatico, è possibile configurare l'impostazione **Ignora la versione dell'app** nel pannello **Informazioni sull'app**. Se questa impostazione viene cambiata in **Sì**, Microsoft Intune ignorerà la versione dell'app installata nel client Windows. 

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Insiemi correlati di licenze per le app supportati in Intune <!-- 1864117 -->
Intune nel portale di Azure ora supporta gli insiemi correlati di licenze per le app come elemento app singolo nell'interfaccia utente. Inoltre, tutte le app con licenza offline sincronizzate da Microsoft Store per le aziende verranno consolidate in una singola voce di app e verrà eseguita la migrazione di tutti i dettagli di distribuzione dei singoli pacchetti nella singola voce. Per visualizzare gli insiemi correlati di licenze per le app nel portale di Azure, selezionare **Licenze dell'app** dal pannello **App per dispositivi mobili**.

### <a name="device-configuration"></a>Configurazione del dispositivo
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Estensioni di file di Windows Information Protection (WIP) per la crittografia automatica <!-- 1463582 -->
Un'impostazione nei criteri di Windows Information Protection (WIP) ora consente di specificare le estensioni di file che vengono automaticamente crittografate quando si esegue la copia da una condivisione di Server Message Block (SMB) all'interno dell'azienda, come definito nei criteri di WIP.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurare le impostazioni dell'account della risorsa per i dispositivi Surface Hub

Ora è possibile configurare in modalità remota le impostazioni dell'account della risorsa per i dispositivi Surface Hub.

L'account della risorsa viene usato dal dispositivo Surface Hub per l'autenticazione con Skype/Exchange per poter partecipare a una riunione. Creare un account della risorsa univoco in modo che il dispositivo Surface Hub compaia nella riunione come sala riunioni. Ad esempio, l'account della risorsa potrebbe essere visualizzato come **Sala riunioni B41/6233**.

> [!NOTE]
> - Se non si specifica alcun valore nei campi, gli attributi configurati in precedenza sul dispositivo verranno sostituiti.
>
> - Le proprietà dell'account della risorsa possono essere modificate dinamicamente nel dispositivo Surface Hub. Ad esempio, nel caso in cui sia attivata la rotazione delle password. Di conseguenza, è possibile che i valori nella console di Azure non riflettano immediatamente la realtà del dispositivo. 
>
>   Per individuare la configurazione corrente nel dispositivo Surface Hub, i dati dell'account della risorsa possono essere inclusi nell'inventario hardware (per il quale è già impostato un intervallo di 7 giorni) o come proprietà di sola lettura. Per una maggior precisione dopo l'esecuzione dell'azione remota, è possibile ottenere lo stato dei parametri subito dopo l'esecuzione dell'azione per aggiornare l'account e i parametri nel dispositivo Surface Hub.


##### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco


|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Esecuzione dalla posta elettronica del contenuto eseguibile protetto da password|Blocca, Controllo, Non configurato|Evitare l'esecuzione dei file eseguibili protetti da password scaricati usando la posta elettronica.|
|Protezione ransomware avanzata|Abilitato, Controllo, Non configurato|Usare una protezione ransomware aggressiva.|
|Flag della sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows|Abilitato, Controllo, Non configurato|Impostare flag per la sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows (lsass.exe).|
|Creazione di processi dai comandi PSExec e WMI|Blocca, Controllo, Non configurato|Bloccare le creazioni di processi originate dai comandi PSExec e WMI.|
|Processi non attendibili e non firmati eseguiti da USB|Blocca, Controllo, Non configurato|Bloccare i processi non attendibili e non firmati eseguiti da USB.|
|File eseguibili che non soddisfano i criteri di prevalenza, età o elenco attendibile|Blocca, Controllo, Non configurato|Bloccare l'esecuzione dei file eseguibili se non soddisfano i criteri di prevalenza, età o elenco attendibile.|

##### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Protezione delle cartelle (già implementata)|Non configurato, Abilita, Solo controllo (già implementata)<br><br> **Nuove**<br>Blocco della modifica del disco, controllo della modifica del disco|
Proteggere file e cartelle da modifiche non autorizzate eseguite da applicazioni non compatibili.<br><br>**Abilitare**: impedire alle app non attendibili di modificare o eliminare file nelle cartelle protette e di scrivere nei settori del disco.<br><br>
**Bloccare solo la modifica del disco**:<br>Impedire alle app non attendibili di scrivere nei settori del disco. Le app non attendibili possono ancora modificare o eliminare i file nelle cartelle protette.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Nuove impostazioni di sicurezza del sistema per Windows 10 e nuovi criteri di conformità <!--1704133-->

Sono ora disponibili nuove impostazioni di conformità di Windows 10, inclusa la richiesta di Firewall e Windows Defender Antivirus. 


### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli
### <a name="intune-apps"></a>App di Intune
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Supporto per le app offline da Microsoft Store per le aziende <!--1222672-->
Le app offline acquistate da Microsoft Store per le aziende ora vengono sincronizzate nel portale di Azure. È quindi possibile distribuire le app ai gruppi di dispositivi o ai gruppi di utenti. Le app offline vengono installate da Intune, non dallo Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro <!-- 1728700 -->

Quando si distribuisce l'app Gmail in un profilo Android for Work, è ora possibile impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro usando l'impostazione **Aggiungi o rimuovi account** nel profilo delle restrizioni per dispositivi Android for Work.

## <a name="week-of-february-5-2018"></a>Settimana del 5 febbraio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nuova opzione per l'autenticazione utente per la registrazione in blocco Apple <!-- 747625 eeready -->

> [!NOTE]
> I nuovi tenant la vedono immediatamente. Per i tenant esistenti, questa funzionalità verrà implementata nel corso del mese di aprile. Fino al termine dell'implementazione, non è possibile accedere a queste nuove funzionalità.

Intune offre ora la possibilità di autenticare i dispositivi con l'app Portale aziendale per i metodi di registrazione seguenti:

- Programma di registrazione del dispositivo mobile di Apple
- Apple School Manager
- Registrazione di Apple Configurator

Quando si usa l'opzione Portale aziendale, l'autenticazione a più fattori di Azure Active Directory può essere applicata senza bloccare questi metodi di registrazione.

Quando si usa l'opzione Portale aziendale, Intune ignora l'autenticazione utente nell'Assistente configurazione di iOS per la registrazione dell'affinità utente. Questo significa che il dispositivo viene inizialmente registrato come dispositivo senza utente e pertanto non riceve le configurazioni o i criteri dei gruppi utenti, ma solo le configurazioni e i criteri per i gruppi di dispositivi. Tuttavia, Intune installerà automaticamente l'app Portale aziendale nel dispositivo. Il primo utente che avvia l'app Portale aziendale e vi accede verrà associato al dispositivo in Intune. A questo punto, l'utente riceverà le configurazioni e i criteri dei gruppi utenti. L'associazione dell'utente non può essere modificata senza eseguire di nuovo la registrazione.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 eeready -->

Intune supporta ora la registrazione di dispositivi da un massimo di 100 account Apple Device Enrollment Program (DEP) o Apple School Manager diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Stampa remota su una rete protetta <!-- 1709994  -->
Le soluzioni di stampa mobile wireless di PrinterOn consentiranno agli utenti di eseguire stampe in modalità remota da qualsiasi posizione e in qualsiasi momento tramite una rete protetta. PrinterOn verrà integrato in Intune APP SDK sia per iOS che per Android. Sarà possibile assegnare i criteri di protezione delle app a questa app tramite il pannello **Criteri di protezione delle app** di Intune nella console di amministrazione. Gli utenti finali potranno scaricare l'app 'PrinterOn per Microsoft' tramite Play Store o iTunes da usare all'interno del loro ecosistema di Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Supporto del portale aziendale macOS per le registrazioni che usano il manager di registrazione dispositivi <!-- 1352411 -->

Gli utenti ora possono usare il manager di registrazione dispositivi durante la registrazione con il portale aziendale macOS.

## <a name="week-of-january-29-2018"></a>Settimana del 29 gennaio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Avvisi per i token scaduti e i token che scadranno a breve <!-- 1639263 -->
Nella pagina di panoramica vengono visualizzati ora avvisi per i token scaduti e i token che scadranno a breve. Facendo clic su un avviso per un singolo token si passerà alla pagina dei dettagli del token.  Se si fa clic su un avviso con più token, verrà visualizzato un elenco di tutti i token con il relativo stato. Gli amministratori devono rinnovare i relativi token prima della scadenza.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Supporto del comando di cancellazione remoto per dispositivi macOS <!-- 1438084 -->

Gli amministratori possono eseguire un comando di cancellazione in remoto da dispositivi macOS.

> [!IMPORTANT]
> Il comando di cancellazione non può essere annullato e deve essere usato con cautela.

Il comando di cancellazione rimuove tutti i dati, incluso il sistema operativo, da un dispositivo. Rimuove anche il dispositivo dalla gestione di Intune. Non viene visualizzato alcun avviso all'utente e la cancellazione viene eseguita immediatamente.

È necessario configurare un PIN di ripristino di 6 cifre. Questo PIN può essere usato per sbloccare il dispositivo cancellato e a quel punto verrà avviata la reinstallazione del sistema operativo. Dopo l'avvio della cancellazione, il PIN viene visualizzato in una barra di stato nel pannello della panoramica del dispositivo in Intune. Il PIN verrà mantenuto per tutta la durata del processo di cancellazione. Dopo il completamento della cancellazione, il dispositivo scompare del tutto dalla gestione di Intune. Assicurarsi di registrare il PIN di ripristino in modo che possa essere usato da chiunque esegua il ripristino del dispositivo.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revocare le licenze per un token Volume Purchasing Program iOS <!-- 820870 --> 
È possibile revocare la licenza di tutte le app Volume Purchasing Program (VPP) iOS per un determinato token VPP.

### <a name="app-management"></a>Gestione delle app

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revoca delle app Volume Purchase Program iOS <!-- 820863 -->
Per un dispositivo specifico con una o più app Volume Purchase Program (VPP) iOS, è possibile revocare la licenza per app basata su dispositivo associata al dispositivo stesso. La revoca di una licenza per app non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. Per altre informazioni, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Assegnare le app per dispositivi mobili Office 365 a dispositivi iOS e Android usando il tipo di app predefinito <!-- 1332318 -->
Il tipo di app **Predefinito** consente di creare e assegnare in modo semplice le app Office 365 a dispositivi iOS e Android gestiti. Le app includono le app 0365 come Word, Excel, PowerPoint e OneDrive. È possibile assegnare app specifiche al tipo di app e modificare la configurazione delle informazioni sull'app.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusione ed esclusione per l'assegnazione di app in base ai gruppi <!-- 1406920 -->

Durante l'assegnazione di app e dopo aver selezionato un tipo di assegnazione, è possibile selezionare i gruppi da includere, così come i gruppi da escludere.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>È possibile assegnare un criterio di configurazione dell'applicazione ai gruppi includendo ed escludendo le assegnazioni  <!-- 1480316 --> 

È possibile assegnare un criterio di configurazione dell'applicazione a un gruppo di utenti e dispositivi tramite una combinazione di assegnazioni di inclusione ed esclusione. È possibile scegliere le assegnazioni come selezione personalizzata di gruppi o come gruppo virtuale. Un gruppo virtuale può includere **Tutti gli utenti**, **Tutti i dispositivi** o **Tutti gli utenti + Tutti i dispositivi**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Supporto dei criteri di aggiornamento edizione di Windows 10 <!-- 903672(archived), 1119689 -->  
È possibile creare criteri di aggiornamento edizione di Windows 10 per l'aggiornamento di dispositivi Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Per informazioni dettagliate sugli aggiornamenti edizione di Windows 10, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>I criteri di accesso condizionale per Intune sono disponibili solo dal portale di Azure <!-- 1737088 1634311 -->

A partire da questa versione, è necessario configurare e gestire i criteri di accesso condizionale nel [portale di Azure](https://portal.azure.com) da **Azure Active Directory** > **Accesso condizionale**. Per praticità, è possibile accedere a questo pannello anche da Intune nel portale di Azure in **Intune** > **Accesso condizionale**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Aggiornamenti per i messaggi di posta elettronica di conformità <!--1637547 -->

Quando viene inviato un messaggio di posta elettronica per segnalare un dispositivo non conforme, vengono inclusi dettagli sul dispositivo non conforme. 


## <a name="week-of-january-22-2018"></a>Settimana del 22 gennaio 2018

### <a name="intune-apps"></a>App di Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nuove funzionalità per l'azione "Risolvi" per i dispositivi Android <!--1583480-->

L'app Portale aziendale per Android sta estendendo l'azione "Risolvi" di **Aggiorna impostazioni del dispositivo** in modo da risolvere i [problemi di crittografia del dispositivo](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Blocco remoto disponibile nell'app Portale aziendale per Windows 10 <!--676506-->
Gli utenti possono ora bloccare i dispositivi in modalità remota dall'app Portale aziendale per Windows 10. L'opzione non verrà visualizzata per il dispositivo locale in uso.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Risoluzione dei problemi di conformità più facile per l'app Portale aziendale per Windows 10 <!--676546-->
Gli utenti finali con dispositivi Windows potranno toccare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema.

## <a name="week-of-december-11-2017"></a>Settimana del 11 dicembre 2017

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nuova impostazione per la ridistribuzione automatica <!-- 1469168 -->
L'impostazione **Ridistribuzione automatica** consente agli utenti con diritti amministrativi di eliminare tutti i dati utente e tutte le impostazioni utente usando **CTRL+tasto WINDOWS+R** nella schermata di blocco del dispositivo. Il dispositivo viene automaticamente riconfigurato e registrato di nuovo nella gestione. Questa impostazione è disponibile in Windows 10 > Limitazioni del dispositivo > Generale > Ridistribuzione automatica. Per i dettagli, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Supporto di edizioni di origine aggiuntivi nei criteri di aggiornamento dell'edizione di Windows 10 <!-- 903672,  1119689 -->
È ora possibile usare i criteri di aggiornamento dell'edizione di Windows 10 per l'aggiornamento da altre edizioni di Windows 10 (Windows 10 Pro, Windows 10 Pro Education, Windows 10 Cloud e così via). Prima di questa versione, i percorsi di aggiornamento delle edizioni supportati erano più limitati. Per altri dettagli, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Nuove impostazioni per il profilo di configurazione del dispositivo Windows Defender Security Center (WDSC)<!-- 1335507 -->

Intune aggiunge una nuova sezione alle impostazioni per il profilo di configurazione del dispositivo in Endpoint Protection denominata **Windows Defender Security Center**. Gli amministratori IT possono configurare gli elementi chiave dell'app Windows Defender Security Center accessibili per gli utenti finali. Se un amministratore IT nasconde un elemento chiave nell'app Windows Defender Security Center, tutte le notifiche correlate all'elemento nascosto non vengono visualizzate nel dispositivo dell'utente.

Questi sono gli elementi chiave che gli amministratori possono nascondere dalle impostazioni del profilo di configurazione del dispositivo per Windows Defender Security Center:
- Protezione da virus e minacce
- Prestazioni e integrità del dispositivo
- Protezione firewall e della rete
- Controllo delle app e del browser
- Opzioni famiglia

Gli amministratori IT possono anche personalizzare le notifiche ricevute dagli utenti. Ad esempio, è possibile specificare se gli utenti ricevono tutte le notifiche generate dagli elementi chiave visibili in WDSC o solo le notifiche critiche. Le notifiche non critiche includono riepiloghi periodici delle attività di Windows Defender Antivirus e notifiche per il completamento delle analisi. Tutte le altre notifiche sono considerate critiche. È inoltre possibile personalizzare il contenuto della notifica, ad esempio specificare informazioni di contatto IT da incorporare nelle notifiche visualizzate sui dispositivi degli utenti.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Supporto di più connettori per la gestione dei certificati SCEP e PFX <!-- 1361755 -->

I clienti che usano NDES Connector in locale per il recapito dei certificati ai dispositivi possono ora configurare più connettori in un singolo tenant.

Questa nuova funzionalità supporta lo scenario seguente:

- **Disponibilità elevata**

Ogni istanza di NDES Connector esegue il pull delle richieste di certificato da Intune.  Se un'istanza di NDES Connector risulta offline, l'altro connettore può continuare a elaborare le richieste.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Per il nome soggetto del cliente è possibile usare la variabile AAD_DEVICE_ID <!-- 1468599 -->

Quando si crea un profilo certificato SCEP in Intune, è ora possibile usare la variabile AAD_DEVICE_ID quando si compila il nome soggetto personalizzato.   Quando viene richiesto il certificato con questo profilo SCEP, la variabile viene sostituita con l'ID del dispositivo AAD del dispositivo che effettua la richiesta di certificato.


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gestire dispositivi macOS registrati in Jamf con il motore di conformità dei dispositivi di Intune <!-- 1592747 -->
È ora possibile usare Jampf per inviare informazioni sullo stato dei dispositivi macOS a Intune, che ne valuterà la conformità ai criteri definiti nella console di Intune. In base allo stato di conformità dei dispositivi e ad altre condizioni (ad esempio la posizione, il rischio utente e così via), l'accesso condizionale imporrà la conformità ai dispositivi macOS che accedono alle applicazioni cloud e locali connesse ad Azure AD, incluso Office 365. Altre informazioni sulla [configurazione dell'integrazione Jamf](conditional-access-integrate-jamf.md) e l'[applicazione della conformità per i dispositivi gestiti Jamf](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nuova azione per dispositivi iOS <!-- 1424701 -->

È ora possibile arrestare i dispositivi iOS 10.3 con supervisione. Questa azione arresta il dispositivo immediatamente senza avviso all'utente finale. L'azione **Shut down (supervised only)** (Arresta - solo con supervisione) è disponibile nelle proprietà del dispositivo quando si seleziona un dispositivo nel carico di lavoro **Dispositivo**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Impedire modifiche di data/ora nei dispositivi Samsung Knox <!-- 1468103 -->

È stata aggiunta a una nuova funzionalità che consente di bloccare le modifiche di data e ora nei dispositivi Samsung Knox. Questa impostazione è disponibile in **Profili di configurazione dei dispositivi** > **Limitazioni del dispositivo (Android)** > **Generale**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Supporto dell'account della risorsa per Surface Hub <!-- 1566442  -->

È stata aggiunta una nuova azione del dispositivo in modo gli amministratori possano definire e aggiornare l'account della risorsa associato a un dispositivo Surface Hub.

L'account della risorsa viene usato da Surface Hub per l'autenticazione con Skype/Exchange in modo da poter partecipare a una riunione. È possibile creare un account della risorsa univoco in modo che il dispositivo Surface Hub compaia nella riunione come sala riunioni. Ad esempio, l'account della risorsa potrebbe essere visualizzato come *Sala riunioni B41/6233*. L'account della risorsa (noto come account del dispositivo) per Surface Hub in genere deve essere configurato per la posizione della sala riunione e quando occorre modificare altri parametri dell'account della risorsa.

Quando gli amministratori vogliono aggiornare l'account della risorsa in un dispositivo, devono specificare le credenziali correnti di Active Directory o Azure Active Directory associate al dispositivo. Se la rotazione delle password è attivata per il dispositivo, gli amministratori devono passare ad Azure Active Directory per trovare la password.

> [!NOTE]
> Tutti i campi vengano inviati in blocco e sovrascrivono tutti i campi configurati in precedenza. Anche i campi vuoti sovrascrivono i campi esistenti.

L'elenco seguente include le impostazioni configurabili dagli amministratori:

- **Account della risorsa**
   - **Utente di Active Directory**

      NomeDominio\NomeUtente o nome dell'entità utente (UPN): user@domainname.com

   - **Password**

- **Parametri facoltativi per l'account della risorsa** (devono essere impostati tramite l'account della risorsa specificato)

   - **Periodo di rotazione delle password**

     Assicura che la password dell'account venga aggiornata automaticamente da Surface Hub ogni settimana per motivi di sicurezza. Per configurare eventuali parametri dopo aver abilitato questo account, è prima di tutto necessario reimpostare la password dell'account in Azure Active Directory.

   - **Indirizzo SIP (Session Initiation Protocol)**

     Usato solo quando l'individuazione automatica ha esito negativo.

   - **Posta elettronica**

     Indirizzo di posta elettronica di dispositivo/account della risorsa.

   - **Exchange Server**

     Necessario solo quando l'individuazione automatica ha esito negativo.

   - **Sincronizzazione calendario**

     Specifica se sono abilitati la sincronizzazione del calendario e altri servizi di Exchange Server. Ad esempio, la sincronizzazione delle riunioni.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installare app di Office in dispositivi macOS <!-- 1494311 -->
È ora possibile installare app di Office nei dispositivi macOS. Questo nuovo tipo di app consentirà di installare Word, Excel, PowerPoint, Outlook e OneNote. Queste app includono anche Microsoft AutoUpdater (MAU), per mantenere più facilmente sicure e aggiornate le app.

### <a name="app-management"></a>Gestione delle app

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminare un token Volume Purchasing Program iOS <!-- 820879 -->
È possibile eliminare il token Volume Purchasing Program (VPP) iOS tramite la console. Ciò potrebbe risultare necessario in presenza di istanze duplicate di un token VPP.

### <a name="intune-apps"></a>App di Intune

#### <a name="end-user-messaging-for-accounts---1573558-for-1712--"></a>Messaggi per gli utenti finali per gli account <!--1573558 for 1712-->

Gli utenti del sito Web Portale aziendale non potranno eseguire azioni che richiedono l'accesso in scrittura al tenant. Verranno visualizzati messaggi di errore appropriati per spiegare che l'account di tali utenti è in manutenzione. È prevista a breve l'introduzione di modifiche simili per le app Portale aziendale per Android, iOS, macOS e Windows. È possibile visualizzare questo errore in [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).



### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Una nuova raccolta di entità denominata Current User è limitata ai dati degli utenti attualmente attivi <!-- 1667026 -->

La raccolta di entità **Users** contiene tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione. Nel corso dell'ultimo mese, ad esempio, è possibile che un utente sia stato aggiunto e rimosso da Intune. Pertanto, se anche l'utente non è presente al momento del report, l'utente e lo stato sono comunque presenti nei dati. In questo caso, è possibile creare un report che mostri la durata della presenza storica dell'utente nei dati.

La nuova raccolta di entità **Current User**, invece, contiene solo gli utenti che non sono stati rimossi. La raccolta di entità **Current User**, quindi, è limitata agli utenti attualmente attivi. Per informazioni sulla raccolta di entità **Current User**, vedere [Informazioni di riferimento per l'entità User corrente](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>API Graph aggiornate <!-- 1736360 -->

In questa versione sono state aggiornate alcune delle API Graph per Intune in versione beta. Vedere il [log delle modifiche delle API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) mensile per altre informazioni.

## <a name="week-of-december-4-2017"></a>Settimana del 4 dicembre 2017

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune supporta le app non consentite di Windows Information Protection (WIP) <!-- 1479103 -->
È possibile specificare app non consentite in Intune. Le app non consentite non possono accedere alle informazioni aziendali e si tratta in effetti della condizione opposta alle app incluse nell'elenco delle app consentite. Per altre informazioni, vedere la [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Elenco consigliato delle app non consentite per Windows Information Protection).


## <a name="week-of-november-27-2017"></a>Settimana del 27 novembre 2017

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>Risolvere i problemi di registrazione  <!-- 746324 -->

L'area di lavoro **Risoluzione dei problemi** ora visualizza i problemi di registrazione dell'utente. Informazioni dettagliate sul problema e i passaggi suggeriti per la correzione possono essere utili ad amministratori e operatori di help desk per la risoluzione dei problemi. Alcuni problemi di registrazione non vengono rilevati ed è possibile che per alcuni errori non siano disponibili suggerimenti per la correzione.

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrizioni di registrazione assegnate ai gruppi <!-- 747598 -->

L'amministratore di Intune ora può [creare restrizioni di registrazione Tipo di dispositivo e Limite di dispositivi personalizzate per i gruppi di utenti](enrollment-restrictions-set.md).

Il portale di Azure di Intune consente di creare fino a 25 istanze di ogni tipo di restrizione, che possono essere successivamente assegnate ai gruppi di utenti. Le restrizioni assegnate ai gruppi sostituiscono le restrizioni predefinite.

Tutte le istanze di un tipo di restrizione vengono mantenute in un elenco nell'ordine. L'ordine definisce un valore di priorità per la risoluzione dei conflitti. Un utente interessato da più istanze di restrizione viene limitato solo dall'istanza con il valore di priorità più alto. È possibile modificare la priorità di un'istanza specifica trascinandola in una posizione diversa nell'elenco.

Questa funzionalità verrà rilasciata con la migrazione delle impostazioni di Android for Work dal menu di registrazione di Android for Work al menu Restrizioni registrazione. Poiché la migrazione può richiedere diversi giorni, è possibile che l'account venga aggiornato per altre parti del rilascio di novembre prima che l'assegnazione dei gruppi risulti abilitata per le restrizioni di registrazione.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Supporto di più connettori del servizio Registrazione dispositivi di rete <!-- 1528104 -->

Il servizio Registrazione dispositivi di rete (NDES, Network Device Enrollment Service) consente ai dispositivi mobili in esecuzione senza credenziali di dominio di ottenere certificati basati sul protocollo SCEP (Simple Certificate Enrollment Protocol).
Con questo aggiornamento, sono supportati più connettori del servizio Registrazione dispositivi di rete.

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gestire i dispositivi Android for Work indipendentemente dai dispositivi Android <!-- 1490731 EEready-->

**Nota**: la distribuzione di queste modifiche avrà inizio con l'aggiornamento di novembre, ma eseguirla nel proprio account può richiedere tempo. Quando queste modifiche vengono rese effettive per il proprio account, si riceverà una notifica di conferma nel portale di Office 365. Dopo l'implementazione, saranno disponibili opzioni aggiuntive per la gestibilità. L'esperienza dell'utente finale non subirà variazioni durante la distribuzione.

Intune supporta la gestione della registrazione di dispositivi Android for Work indipendentemente dalla piattaforma Android. Queste impostazioni vengono gestite in **Registrazione del dispositivo** > **Restrizioni registrazione** > **Restrizioni sul tipo di dispositivi**. In precedenza erano disponibili in **Registrazione del dispositivo** > **Registrazione di Android for Work** > **Impostazioni di registrazione per Android for Work**.

Per impostazione predefinita, le impostazioni dei dispositivi Android for Work corrispondono alle impostazioni dei dispositivi Android. Tuttavia, dopo la modifica delle impostazioni Android for Work questa corrispondenza andrà persa.

Se si blocca la registrazione dei dispositivi Android for Work personali, solo i dispositivi Android aziendali possono essere registrati come Android for Work.

Durante l'uso delle nuove impostazioni, considerare i punti seguenti:

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work non è mai stata caricata in precedenza

La nuova piattaforma Android for Work è bloccata nelle Restrizioni sul tipo di dispositivi predefinite. Dopo aver caricato la funzionalità, è possibile consentire la registrazione dei dispositivi con Android for Work. A tale scopo, modificare il valore predefinito o creare una nuova restrizione dei tipi di dispositivo per sostituire la restrizione predefinita.

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work è stata caricata

Se la registrazione è stata caricata in precedenza, la situazione varia a seconda dell'impostazione selezionata:

| Impostazione | Stato di Android for Work nella restrizione dei tipi di dispositivo predefinita | Note |
| --- | --- | --- |
| **Gestisci tutti i dispositivi come Android** | Bloccato | Tutti i dispositivi Android devono essere registrati senza Android for Work. |
| **Gestisci i dispositivi supportati come Android for Work** | Consentito | Tutti i dispositivi Android che supportano Android for Work devono essere registrati con Android for Work. |
| **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work** | Bloccato | Per sostituire l'impostazione predefinita è stato creato un criterio Restrizione dei tipi di dispositivo separato. Questo criterio definisce i gruppi precedentemente selezionati per consentire la registrazione di Android for Work. Gli utenti inclusi nei gruppi selezionati continueranno a essere autorizzati a registrare i loro dispositivi Android for Work. A tutti gli altri utenti non è consentita la registrazione con Android for Work. |

In tutti i casi, viene mantenuto il regolamento previsto. Per mantenere l'autorizzazione globale o per i singoli gruppi di Android for Work nel proprio ambiente non è necessario eseguire alcuna operazione.

### <a name="app-management"></a>Gestione delle app

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Report sull'installazione delle app aggiornato per includere lo stato Installazione in sospeso <!-- 1249446 -->  

Il report **Stato di installazione dell'app**, accessibile per ogni app attraverso l'elenco **App** nel carico di lavoro **App per dispositivi mobili** ora contiene il conteggio **L'installazione in sospeso** per utenti e dispositivi.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API di inventario delle app iOS 11 per il rilevamento delle minacce per i dispositivi mobili<!-- 1391759 -->

Intune raccoglie le informazioni degli inventari delle app dei dispositivi personali e aziendali e le rende disponibili per i provider del servizio di rilevamento delle minacce per i dispositivi mobili (MTD, Mobile Threat Detection), ad esempio Lookout for Work. Si possono raccogliere gli inventari delle app dagli utenti di dispositivi iOS 11 e versioni successive.

**Inventario delle app**  
Gli inventari dei dispositivi aziendali e personali iOS 11 e versioni successive vengono inviati al provider del servizio MTD. I dati dell'inventario delle app includono:

 - ID dell'app
 - Versione dell'app
 - Versione breve dell'app
 - Nome dell'app
 - Dimensione del bundle dell'app
 - Dimensione dinamica dell'app
 - Indicazione sulla convalida dell'app
 - Indicazione sulla gestione dell'app


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Eseguire la migrazione di dispositivi e utenti dalla soluzione MDM ibrida alla versione autonoma di Intune <!-- 1463747 wnready -->
Sono ora disponibili nuovi strumenti e processi per lo spostamento di utenti e dei relativi dispositivi dalla soluzione MDM ibrida a Intune nel portale di Azure, che consentono di eseguire le attività seguenti:
- Copiare criteri e profili dalla console di Configuration Manager a Intune nel portale di Azure
- Spostare un sottoinsieme di utenti a Intune nel portale di Azure, mantenendo il resto nella soluzione MDM ibrida
- Eseguire la migrazione di dispositivi a Intune nel portale di Azure senza la necessità di registrarli nuovamente

Per informazioni dettagliate, vedere [Eseguire la migrazione di dispositivi e utenti dalla soluzione MDM ibrida alla versione autonoma di Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale<!-- 676614 -->
Dopo che Exchange Connector crea una connessione a Exchange usando il CAS specificato, il connettore è ora in grado di individuare altri CAS. Se il CAS principale diventa non disponibile, il connettore eseguirà il failover a un altro CAS, se disponibile, fino a quando non diventa disponibile il CAS principale. Per altri dettagli, vedere [Supporto a disponibilità elevata di Exchange Connector locale](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Riavvio remoto del dispositivo iOS (solo supervisionato) <!-- 1424595 -->

È ora possibile riavviare un dispositivo iOS 10.3 e versioni successive supervisionato usando un'azione del dispositivo. Per altre informazioni sull'uso dell'azione di riavvio del dispositivo, vedere [Riavviare i dispositivi in remoto con Intune](device-restart.md).

> [!Note]
> Per eseguire questo comando sono necessari un dispositivo supervisionato e il diritto di accesso **Device Lock** (Blocco dispositivo). Il dispositivo viene riavviato immediatamente. I dispositivi iOS bloccati con passcode non si ricollegano a una rete Wi-Fi dopo il riavvio. È possibile che dopo il riavvio non siano in grado di comunicare con il server.

#### <a name="single-sign-on-support-for-ios----1333645---"></a>Supporto Single Sign-On per iOS <!-- 1333645 -->  

È possibile usare Single Sign-On per gli utenti iOS. Le app iOS codificate per la ricerca delle credenziali dell'utente nel payload Single Sign-on funzionano con questo aggiornamento della configurazione del payload. È anche possibile usare l'UPN e l'ID dispositivo di Intune per configurare il nome dell'entità e l'area di autenticazione. Per informazioni dettagliate, vedere [Configurare Intune per l'accesso Single Sign-On al dispositivo iOS](sso-ios.md).

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Aggiungere "Trova il mio iPhone" per i dispositivi personali <!--1427287-->
È ora possibile verificare se i dispositivi iOS hanno il Blocco attivazione attivato. Questa funzionalità era disponibile in precedenza nel portale classico di Intune.


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloccare in remoto un dispositivo macOS gestito con Intune <!-- 1437691 -->

È possibile bloccare un dispositivo macOS smarrito e impostare un PIN di ripristino di 6 cifre. Quando il dispositivo è bloccato, il pannello **Device overview** (Panoramica dispositivo) visualizza il PIN fino a quando non viene inviata un'altra azione del dispositivo.

Per altre informazioni, vedere [Bloccare in remoto i dispositivi gestiti con Intune](device-remote-lock.md).

#### <a name="new-scep-profile-details-supported----1559808---"></a>Nuovi dettagli del profilo SCEP supportati <!-- 1559808 -->

Gli amministratori ora possono configurare impostazioni aggiuntive durante la creazione di un profilo SCEP nelle piattaforme Windows, iOS, macOS e Android.  Gli amministratori possono impostare IMEI, numero di serie o nome comune, inclusa la posta elettronica nel formato del nome soggetto.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>Mantenere i dati durante il ripristino delle impostazioni predefinite  <!--1588489 -->
Quando si reimposta Windows 10 versione 1709 e successive ripristinando le impostazioni predefinite, è disponibile una nuova funzionalità. Gli amministratori possono specificare se la registrazione del dispositivo e altri dati di provisioning vengono mantenuti nel dispositivo quando viene eseguito il ripristino delle impostazioni predefinite.

Quando viene eseguito il ripristino delle impostazioni predefinite vengono mantenuti i dati seguenti:
- Account utente associati al dispositivo
- Stato del computer (aggiunto a un dominio, aggiunto ad Azure Active Directory)
- Registrazione MDM
- App installate OEM (app dello Store e Win32)
- Profilo utente
- Dati utente esterni al profilo utente
- Accesso automatico dell'utente

I dati seguenti non vengono mantenuti:
- File dell'utente
- App installate dell'utente (app dello Store e Win32)
- Impostazioni del dispositivo non predefinite

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Assegnazioni degli anelli di aggiornamento di Windows 10 visualizzate <!-- 1621837 -->
Durante la **Risoluzione dei problemi** per l'utente visualizzato le assegnazioni degli anelli di aggiornamento di Windows 10 sono visibili.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Impostazioni della frequenza di creazione di report di Windows Defender Advanced Threat Protection  <!-- 1455974  -->
Il servizio Windows Defender Advanced Threat Protection (WDATP) consente agli amministratori di gestire la frequenza di creazione di report per i dispositivi gestiti. Con la nuova opzione **Accelera la frequenza di creazione di report di telemetria**, WDATP raccoglie i dati e valuta i rischi con maggior frequenza. L'impostazione predefinita per la creazione di report ottimizza velocità e prestazioni. L'aumento della frequenza di creazione di report può essere utile per i dispositivi a rischio elevato. Questa impostazione è disponibile nel profilo **Windows Defender ATP** in **Configurazioni dispositivi**.

#### <a name="audit-updates----1412961---"></a>Aggiornamenti dei controlli <!-- 1412961 -->  
La funzione di controllo di Intune offre un record delle operazioni di modifica correlate a Intune.  Tutte le operazioni di creazione, aggiornamento ed eliminazione e le attività remote vengono acquisite e mantenute per un anno.  Il portale di Azure offre una visualizzazione degli ultimi 30 giorni dei dati di controllo di ogni carico di lavoro a cui è possibile applicare filtri.  Un'API Graph corrispondente consente il recupero dei dati di controllo archiviati dell'ultimo anno.

La funzione di controllo è disponibile nel gruppo **MONITOR**. Viene visualizzata una voce di menu **Log di controllo** per ogni carico di lavoro.




## <a name="week-of-november-20-2017"></a>Settimana del 20 novembre 2017

### <a name="app-management"></a>Gestione delle app

#### <a name="google-play-protect-support-on-android----908720---"></a>Supporto di Google Play Protect in Android <!-- 908720 -->

Con il rilascio di Android Oreo, Google introduce un gruppo di funzionalità di sicurezza denominato Google Play Protect che consente a utenti e organizzazioni di eseguire app e immagini Android sicure. Intune ora supporta le funzionalità di Google Play Protect, inclusa l'attestazione remota SafetyNet. Gli amministratori possono impostare requisiti per i criteri di conformità che richiedono la configurazione e l'integrità di Google Play Protect.
L'**attestazione dispositivo SafetyNet** richiede che il dispositivo si connetta a un servizio Google per verificare che il dispositivo sia integro e non compromesso. Gli amministratori possono anche definire un'impostazione del profilo di configurazione per far sì che Android for Work richieda la verifica delle app installate da parte di Google Play Services. Se un dispositivo non è conforme ai requisiti di Google Play Protect, l'accesso condizionale può impedire agli utenti di accedere alle risorse aziendali.

- Informazioni su [come creare un criterio di conformità del dispositivo per abilitare Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocollo di testo consentito dalle app gestite <!-- 1414050  -->

Le app gestite da Intune App SDK sono in grado di inviare messaggi SMS.

## <a name="week-of-november-13-2017"></a>Settimana del 13 novembre 2017

### <a name="intune-apps"></a>App di Intune
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>L'app Portale aziendale per macOS è ora disponibile <!--1541700-->
L'app Portale aziendale Intune in macOS offre una nuova esperienza utente, ottimizzata in modo da visualizzare correttamente tutte le informazioni e le notifiche di conformità necessarie agli utenti in relazione a tutti i dispositivi che hanno registrato. Dopo aver distribuito l'app Portale aziendale Intune in un dispositivo, Microsoft AutoUpdate per macOS fornirà i necessari aggiornamenti. È possibile scaricare la nuova app Portale aziendale Intune per macOS accedendo al sito Web dell'app Portale aziendale Intune da un dispositivo macOS.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner è ora incluso nell'elenco di app approvate per la gestione delle app mobili <!-- 1248473 -->
L'app Microsoft Planner per iOS e Android fa ora parte delle app approvate in base ai criteri di gestione delle app mobili. L'app può essere configurata tramite il pannello Protezione app di Intune nel portale di Azure di tutti i tenant.
- Altre informazioni sull'[elenco di app approvate per la gestione dei dispositivi mobili](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frequenza di aggiornamento dei requisiti di VPN per app nei dispositivi iOS <!-- 1547061 -->  
Gli amministratori possono ora rimuovere i requisiti di VPN per app relativi alle app installate in dispositivi iOS; i dispositivi interessati verranno aggiornati dopo la successiva archiviazione di Intune, che si verifica in genere entro 15 minuti.  

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Supporto per Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->
È ora disponibile il Management Pack di System Center Operations Manager (SCOM) per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questa funzionalità consente di eseguire il monitoraggio del servizio in diversi modi quando è necessario risolvere un problema.

## <a name="week-of-november-6-2017"></a>Settimana del 6 novembre 2017

### <a name="device-enrollment"></a>Registrazione del dispositivo
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Co-gestione per i dispositivi Windows 10  <!-- 1243445 -->
La co-gestione è una soluzione che rappresenta un ponte tra la gestione tradizionale e quella moderna e consente di effettuare la transizione con un approccio graduale. La co-gestione è fondamentalmente una soluzione in cui i dispositivi Windows 10 vengono gestiti contemporaneamente da Configuration Manager e Microsoft Intune e aggiunti ad Active Directory (AD) e Azure Active Directory (Azure AD).  Questa configurazione offre la possibilità di effettuare una modernizzazione graduale con un ritmo adatto alla propria organizzazione nei casi in cui una transizione immediata non è possibile.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Limitare la registrazione di Windows specificando la versione del sistema operativo<!-- 245498 -->
L'amministratore di Intune può ora specificare una versione minima e massima di Windows 10 per le registrazioni dei dispositivi. È possibile impostare queste limitazioni nel pannello **Configurazioni della piattaforma**.

Intune supporta ancora la registrazione di PC e telefoni Windows 8.1. È però possibile impostare solo le versioni di Windows 10 con limiti minimi e massimi. Per consentire la registrazione di dispositivi 8.1, non specificare il limite minimo.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Avvisi per dispositivi non assegnati Windows AutoPilot <!-- 1631236 -->
Nella pagina **Microsoft Intune** > **Registrazione del dispositivo** > **Panoramica** è disponibile un nuovo avviso per dispositivi non assegnati Windows AutoPilot. In questo avviso viene specificato il numero di dispositivi del programma AutoPilot che non hanno profili di AutoPilot Deployment assegnati. Usare le informazioni contenute nell'avviso per creare i profili e assegnarli ai dispositivi non assegnati. Selezionando l'avviso, verrà visualizzato un elenco completo di dispositivi Windows AutoPilot e le relative informazioni dettagliate. Per altre informazioni, vedere [Registrare dispositivi Windows con il programma Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="refresh-button-for-devices-list-------1333581---"></a>Pulsante Aggiorna per l'elenco di dispositivi<!-- 1333581 -->
Poiché l'elenco dei dispositivi non viene aggiornato automaticamente, è possibile usare il nuovo pulsante Aggiorna per aggiornare i dispositivi contenuti nell'elenco.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Supporto dell'autorità di certificazione Symantec Cloud  <!-- 1333638 -->    
Intune supporta ora la CA Symantec Cloud, che consente al Connettore di certificati di Intune di rilasciare certificati PKCS dalla CA Symantec Cloud a dispositivi gestiti Intune. Se si usa già il Connettore di certificati di Intune con l'autorità di certificazione (CA) Microsoft, è possibile usare la configurazione esistente del Connettore di certificati di Intune per aggiungere il supporto della CA Symantec.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nuovi elementi aggiunti all'inventario dei dispositivi<!--1404455 -->
I nuovi elementi sono ora disponibili nell'[inventario dei dispositivi registrati](device-inventory.md):

- Indirizzo MAC Wi-Fi
- Spazio di archiviazione totale
- Spazio disponibile totale
- MEID
- Gestore telefonico del sottoscrittore


### <a name="app-management"></a>Gestione delle app
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Impostare l'accesso per le app mediante una patch di protezione Android minima nel dispositivo<!-- 1278463 -->   
L'amministratore può definire la patch di protezione Android minima che deve essere installata nel dispositivo per poter accedere a un'applicazione gestita in un account gestito.

> [!Note]  
> Questa funzionalità limita solo le patch di protezione rilasciate da Google nei dispositivi Android 6.0 e versioni successive.

#### <a name="app-conditional-launch-support----1193313---"></a>Supporto di avvio condizionale all'app <!-- 1193313 -->
Gli amministratori IT possono ora impostare un requisito usando il portale di amministrazione di Azure per applicare un passcode anziché un PIN numerico PIN attraverso la gestione delle applicazioni mobili (MAM) all'avvio dell'applicazione. Se il requisito viene configurato, all'utente viene richiesto di impostare e usare un passcode prima di accedere alle applicazioni con supporto MAM. Un passcode è un PIN numerico con almeno un carattere speciale o una lettera maiuscola o minuscola. In questa versione di Intune la funzione è abilitata **solo in iOS**. Il supporto di Intune per i passcode è simile a quello dei PIN numerici: viene impostata una lunghezza minima e sono consentiti caratteri e sequenze ripetuti. Questa funzionalità richiede il supporto delle applicazioni (ovvero di WXP, Outlook, Managed Browser, Yammer) per l'integrazione di Intune App SDK con il codice della funzionalità stessa, in modo che le impostazioni di passcode possano essere applicate nelle applicazioni di destinazione.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Numero di versione delle app line-of-business nel report sullo stato dell'installazione del dispositivo <!-- 1233999 -->
In questa versione il report sullo stato dell'installazione del dispositivo visualizza il numero di versione dell'app per le app line-of-business per iOS e Android. Queste informazioni possono essere usate per la risoluzioni dei problemi delle app o per individuare i dispositivi che eseguono versioni delle app non aggiornate.


### <a name="device-configuration"></a>Configurazione del dispositivo
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Gli amministratori possono ora configurare le impostazioni del firewall in un dispositivo usando un profilo di configurazione del dispositivo <!-- 951708 -->   
Gli amministratori possono attivare il firewall per i dispositivi e anche configurare diversi protocolli per le reti di dominio, private e pubbliche.  Le impostazioni del firewall sono disponibili nel profilo "Endpoint Protection".

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard consente di proteggere i dispositivi dai siti Web non attendibili specificati dall'organizzazione <!-- 958257 -->   
Gli amministratori possono definire i siti come "attendibili" o "aziendali" usando un flusso di lavoro Windows Information Protection o il nuovo profilo "limite di rete" disponibile nelle configurazioni del dispositivo. I siti non elencati nel limite di rete attendibile del dispositivo Windows 10 a 64 bit e visualizzati con Microsoft Edge vengono invece aperti in un browser all'interno di un computer virtuale Hyper-V.

Application Guard è disponibile nei profili di configurazione del dispositivo, nel profilo "Endpoint Protection". Nel profilo gli amministratori possono configurare l'iterazione tra il browser virtualizzato e il computer host, i siti non attendibili e i siti attendibili e l'archiviazione dei dati nel browser virtualizzato. Per usare Application Guard in un dispositivo, è necessario innanzitutto configurare un limite di rete. È importante definire un solo limite di rete per dispositivo.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Il controllo delle applicazioni di Windows Defender in Windows 10 Enterprise consente di considerare attendibili solo le app autorizzate <!-- 1031096 -->    
Considerate le migliaia di nuovi file dannosi creati ogni giorno, l'uso di un sistema di rilevamento antivirus basato su firma per la protezione da software dannoso potrebbe non offrire più una difesa adeguata dai nuovi attacchi. Con il controllo delle applicazioni di Windows Defender in Windows 10 Enterprise è possibile modificare la configurazione del dispositivo passando da una modalità in cui vengono considerate attendibili tutte le app a eccezione di quelle bloccate da un antivirus o da un'altra soluzione di sicurezza a una modalità in cui il sistema operativo considera attendibili solo le app autorizzate dalla propria organizzazione. È possibile impostare le app come attendibili nel controllo delle applicazioni di Windows Defender.

Usando Intune è possibile configurare i criteri di controllo delle applicazioni in modalità "solo controllo" o in modalità di imposizione. In modalità "solo controllo" le app non vengono bloccate. La modalità "solo controllo" registra tutti gli eventi nei log del client locali. È anche possibile specificare se autorizzare l'esecuzione solo dei componenti Windows e delle app di Microsoft Store o anche quella di altre app affidabili in base a quanto definito da Intelligent Security Graph.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender Exploit Guard è un nuovo set di funzionalità di prevenzione intrusioni per Windows 10 <!-- 1063615 -->   
Windows Defender Exploit Guard include regole personalizzate per ridurre la vulnerabilità agli exploit delle applicazioni, evitare le minacce di macro e script, blocca automaticamente le connessioni di rete verso indirizzi IP con reputazione negativa ed è in grado di proteggere i dati da ransomware e minacce sconosciute. Windows Defender Exploit Guard include i componenti seguenti:

- La **Riduzione della superficie di attacco** offre regole che consentono di evitare le minacce di macro, script e posta elettronica.
- L'**Accesso controllato alle cartelle** blocca automaticamente l'accesso al contenuto delle cartelle protette.
- Il **filtro di rete** blocca la connessione in uscita di tutte le app verso indirizzi IP o domini con reputazione negativa
- La **protezione dagli exploit** offre limitazioni di memoria, flusso di controllo e criteri che è possibile usare per proteggere un'applicazione dagli exploit.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gestire gli script di PowerShell in Intune per i dispositivi Windows 10 <!-- 790537 -->

L'estensione di gestione di Intune consente di caricare script di PowerShell in Intune da eseguire in dispositivi Windows 10. L'estensione integra le funzionalità di gestione di dispositivi mobili (MDM, Mobile Device Management) di Windows 10 e rende più semplice il passaggio a una gestione moderna. Per informazioni dettagliate, vedere [Gestire gli script di PowerShell in Intune per i dispositivi Windows 10](intune-management-extension.md).

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nuove impostazioni delle limitazioni del dispositivo per Windows 10      <!-- 1308850 -->
-    Messaggistica (solo dispositivi mobili): disabilitare il test o i messaggi MMS
-    Password: impostazioni per l'abilitazione di FIPS e l'uso dei dispositivi secondari Windows Hello per l'autenticazione 
-    Visualizzazione: impostazioni per attivare o disattivare il ridimensionamento del programma GDI per le app legacy

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Limitazioni del dispositivo per la modalità a tutto schermo per Windows 10 <!-- 1308872 -->   
È possibile impostare una limitazione per la modalità tutto schermo per gli utenti dei dispositivi Windows 10 che limita gli utenti a un set di app predefinite.  A tale scopo, creare un profilo di limitazione del dispositivo Windows 10 e specificare le impostazioni della modalità a tutto schermo.

La modalità a tutto schermo supporta due modalità: la modalità **applicazione singola** che consente all'utente di eseguire una sola app e la modalità **app multiple** che consente l'accesso a più app.  Definire l'account utente e il nome del dispositivo che determinano le app supportate.  Dopo aver eseguito l'accesso, l'utente sarà limitato alle app definite.  Per altre informazioni, vedere [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (Provider del servizio di configurazione AssignedAccess). 

Per la modalità a tutto schermo sono necessari i requisiti seguenti:

- Intune deve essere l'autorità MDM.
- Le app devono essere già installate nel dispositivo di destinazione.
- Il [provisioning](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions) del dispositivo deve essere stato eseguito correttamente.

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuovo profilo di configurazione del dispositivo per la creazione di limiti di rete <!-- 1311967 -->   
Un nuovo profilo di configurazione del dispositivo denominato **Limite di rete** è disponibile con gli altri profili di configurazione. Usare questo profilo per definire le risorse online da considerare aziendali e affidabili. È necessario definire un limite di rete per un dispositivo *prima* di usare funzionalità come Windows Defender Application Guard e Windows Information Protection nel dispositivo. È importante definire un solo limite di rete per dispositivo.

È possibile definire le risorse cloud aziendali, gli intervalli di indirizzi IP e i server proxy interni da considerare attendibili. Il limite di rete definito può essere utilizzato da altre funzionalità, ad esempio Windows Defender Application Guard e Windows Information Protection.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Due impostazioni aggiuntive per Windows Defender Antivirus <!-- 1338409 -->  
**Livello di blocco di file**

| | |
|---|---|
| Non configurato | **Non configurato** usa il livello di blocco predefinito di Windows Defender Antivirus e offre un rilevamento sicuro senza aumentare il rischio di rilevare file legittimi. |
| Alta | **Alto** applica un livello di rilevamento elevato.
| Elevato +  | **Elevato +** offre il livello Alto con misure di protezione aggiuntive che potrebbero influire sulle prestazioni del client.
| Tolleranza zero  | **Tolleranza zero** blocca tutti gli eseguibili sconosciuti. |

Sebbene sia improbabile, l'impostazione su **Alto** potrebbe causare il rilevamento di file legittimi.
È consigliabile impostare il livello di blocco di file sul valore predefinito **Non configurato**.

**Estensione del timeout per l'analisi dei file dal cloud**  

| | |
|--|--|
| Numero di secondi (0-50) | Specificare la quantità massima di tempo per la quale Windows Defender Antivirus deve bloccare un file in attesa di un risultato dal cloud. La quantità predefinita è 10 secondi: il tempo specificato con questa opzione (fino a un massimo di 50 secondi) viene aggiunto ai 10 secondi. Nella maggior parte dei casi l'analisi richiede molto meno tempo rispetto al tempo massimo. L'estensione della quantità di tempo consente al cloud di analizzare nel dettaglio i file sospetti. È consigliabile abilitare questa impostazione e specificare almeno 20 secondi aggiuntivi. |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix aggiunta per i dispositivi Windows 10 <!-- 1512457 -->  
È possibile configurare la VPN Citrix per i dispositivi Windows 10. Durante la configurazione di una VPN per Windows 10 e versioni successive è possibile scegliere la VPN Citrix nell'elenco *Selezionare un tipo di connessione* nel pannello **VPN di base**.

> [!Note]
> Configurazione Citrix per iOS e Android.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Chiavi precondivise supportate da connessioni Wi-Fi in iOS<!-- 1550823 -->
Per usare le chiavi precondivise per le connessioni WPA/WPA2-Personal in dispositivi iOS, è possibile configurare profili Wi-Fi. Questi profili vengono inviati al dispositivo dell'utente quando il dispositivo viene registrato in Intune.

Dopo che il profilo è stato inviato al dispositivo, il passaggio successivo cambia a seconda della configurazione del profilo.  Se è impostato per connettersi automaticamente, la connessione viene eseguita automaticamente quando viene richiesta la rete.  Se il profilo si connette manualmente, la connessione deve essere attivata manualmente dall'utente.  

### <a name="intune-apps"></a>App di Intune

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Accesso ai log di app gestite per iOS<!-- 1469920 -->
Gli utenti finali che hanno installato Managed Browser possono ora visualizzare lo stato di gestione di tutte le app pubblicate Microsoft e inviare i log per la risoluzione dei problemi delle app iOS gestite.

Per altre informazioni su come abilitare la modalità di risoluzione dei problemi in Managed Browser in un dispositivo iOS, vedere [How to access to managed app logs using the Managed Browser on iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios) (Come accedere a log di app gestite tramite Managed Browser in iOS).

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Miglioramenti al flusso di lavoro di configurazione dei dispositivi in Portale aziendale per iOS (versione 2.9.0) <!-- 1417174 -->

Il flusso di lavoro di configurazione dei dispositivi nell'app Portale aziendale per iOS è stato migliorato. Il linguaggio è più semplice e, dove possibile, sono state inserite schermate. Con l'inserimento del nome della società nel testo di configurazione, il linguaggio è più specifico per la società di riferimento. È possibile visualizzare il flusso di lavoro aggiornato nella pagina sulle  [novità nell'interfaccia utente delle app](whats-new-app-ui.md).

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>L'entità User contiene i dati utente più recenti nel modello di dati del data warehouse <!-- 1544273 -->
La prima versione del modello di dati del data Warehouse di Intune contiene solo i dati storici e recenti di Intune. Durante la creazione di report non è possibile acquisire lo stato corrente di un utente. In questo aggiornamento l'**entità User** viene popolata con i dati utente più recenti.


## <a name="notices"></a>Notifiche


### <a name="coming-soon-workflow-updates-to-intune-administration-ui"></a>Presto disponibile: aggiornamenti del flusso di lavoro per l'interfaccia utente di amministrazione di Intune

Intune sta aggiornando l'esperienza di amministrazione nella versione del servizio di marzo. Non è necessario intraprendere alcuna azione, ma è opportuno sapere che l'aggiornamento fa parte dell'impegno di Microsoft per la trasparenza. Quando è abilitata la gestione dei dispositivi Android o Apple, Intune invia informazioni sul dispositivo e l'utente da integrare con i servizi di terze parti per la gestione dei rispettivi dispositivi. Grazie all'ottimizzazione dell'interfaccia utente di amministrazione, che verrà introdotta nel rilascio di marzo del servizio, si avrà una maggiore trasparenza dei dati condivisi. Nessuna delle modifiche dell'interfaccia utente avrà un impatto per l'utente finale.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?

Gli scenari in cui verrà aggiunto un consenso alle finestre di condivisione dei dati includono:
- Abilitazione di Android for Work 
- Abilitazione e caricamento dei certificati per le notifiche push MDM Apple 
- Abilitazione di uno dei servizi Apple, ad esempio Device Enrollment Program, School Manager e Volume Purchasing Program

In ogni caso, il consenso è strettamente correlato all'esecuzione di un servizio di gestione dei dispositivi mobili, ad esempio per confermare che un amministratore IT ha autorizzato la registrazione di dispositivi Google o Apple. La documentazione da consultare per sapere quali informazioni vengono condivise quando vengono pubblicati i nuovi flussi di lavoro è disponibile qui:
- [Dati inviati da Intune a Google](data-intune-sends-to-google.md)
- [Dati inviati da Intune ad Apple](data-intune-sends-to-apple.md)

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica

Non è necessario eseguire alcuna operazione per prepararsi per la modifica, poiché si tratta di aggiornamenti di minore entità dell'interfaccia utente del flusso di lavoro. Per altre informazioni sulla conformità GDPR di Microsoft, accedere al Centro protezione dal collegamento Informazioni aggiuntive.



### <a name="plan-for-change-update-where-you-configure-your-app-protection-policies"></a>Pianificare le modifiche: aggiornare la posizione di configurazione dei criteri di Protezione app

A partire da marzo 2018, verrà eseguito il reindirizzamento temporaneo dal pannello del servizio Protezione app di Intune nel portale di Azure al pannello App per dispositivi mobili in Intune nel portale di Azure. Si noti che tutti i criteri di Protezione app si trovano già nel pannello App per dispositivi mobili in Intune, in Configurazione dell'app. Anziché passare a Protezione app di Intune, si passerà semplicemente a Intune. Nel mese di aprile questo reindirizzamento verrà interrotto e il pannello del servizio Protezione app di Intune verrà completamente rimosso, poiché è un duplicato della funzionalità ora incorporata in Intune. 

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Questa modifica interesserà sia i clienti Intune autonomi che ibridi (clienti Intune con Configuration Manager). Questa integrazione contribuirà alla semplificazione dell'amministrazione della gestione del cloud. Sarà sufficiente un solo pannello in Azure, il pannello Intune, per gestire gruppi, criteri e app, nonché per la gestione di tutti i dispositivi mobili.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Contrassegnare come preferito il pannello Intune anziché il pannello del servizio Protezione app di Intune e assicurarsi di avere dimestichezza con il flusso di lavoro Criterio di protezione dell'app nel pannello App per dispositivi mobili all'interno di Intune. Il reindirizzamento durerà per un breve periodo di tempo e quindi il pannello Protezione app verrà rimosso. Tenere presente che tutti i criteri di Protezione app sono già presenti in Intune ed è possibile modificare tutti i criteri di accesso condizionale seguendo la documentazione disponibile qui: [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Altre informazioni**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="updated-new-security-enhancements-in-the-intune-service-----1637539---"></a>Aggiornamento: nuovi miglioramenti della sicurezza nel servizio Intune <!-- 1637539 -->   

È in corso l'implementazione di nuovi miglioramenti della sicurezza nel servizio Intune. Nell'ambito di questa modifica, con l'aggiornamento di marzo del servizio Intune, nella console di Azure in Intune sarà disponibile un tasto di alternanza per attivare e disattivare questa funzionalità di sicurezza. Quando la funzionalità è attivata, i dispositivi a cui non sono assegnati criteri di conformità verranno contrassegnati come 'non conformi'.

**Clienti ibridi**: al momento questa modifica non verrà introdotta per i clienti ibridi. Non è necessario eseguire alcuna operazione. È tuttavia consigliabile assicurarsi che ai dispositivi sia assegnato almeno un criterio di conformità.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?

Quando verrà avviata l'implementazione di questa modifica, nell'aggiornamento di marzo, questa funzionalità avrà effetti diversi a seconda che siano già stati assegnati criteri di conformità o meno.

- Per i tenant nuovi o esistenti ai cui dispositivi non sono assegnati criteri di conformità, il tasto di alternanza verrà impostato automaticamente su **conforme**. Per impostazione predefinita, la funzionalità sarà disattivata nella console. Non ci sarà alcun impatto per l'utente finale.
- Per i tenant esistenti ai cui dispositivi (uno o più) sono assegnati criteri di conformità, il tasto di alternanza verrà impostato automaticamente su 'non conforme'. Al momento dell'implementazione dell'aggiornamento di marzo, per la funzionalità verrà attivata l'impostazione predefinita. 

Se si usano criteri di conformità con accesso condizionale e la funzionalità è attivata, tutti i dispositivi senza alcun criterio di conformità assegnato verranno bloccati dall'accesso condizionale. Gli utenti finali associati a questi dispositivi e in precedenza autorizzati ad accedere alla posta elettronica perderanno l'accesso, a meno che a tutti i dispositivi non venga assegnato almeno un criterio di conformità.   
 
#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica  

Se si usa l'accesso condizionale, è consigliabile che questa funzionalità venga attivata e che il tasto di alternanza rimanga su **Non conforme**. Per evitare che gli utenti finali perdano l'accesso alla posta elettronica, verificare che a tutti i dispositivi sia assegnato almeno un criterio di conformità. Ecco alcune modifiche in corso che agevoleranno queste operazioni:   

- È stato introdotto un report denominato **Dispositivi senza criteri di conformità** nel portale di Intune, che è possibile usare per identificare tutti i dispositivi all'interno dell'ambiente in uso a cui non sono assegnati criteri di conformità. 
- È presente un'opzione **Tutti gli utenti** per semplificare l'assegnazione di un criterio di conformità a tutti gli utenti.

Se si sceglie di lasciare disattivato il tasto di alternanza, non sono necessari altri interventi.

**Altre informazioni**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Modifiche pianificate: modifica del supporto del plug-in Cordova per Microsoft Intune App SDK
Intune terminerà il supporto per il [plug-in Cordova per Microsoft Intune App SDK](app-sdk-cordova.md) il 1 maggio 2018. È consigliabile usare invece lo strumento di wrapping delle app di Intune per preparare le app basate su Cordova per la gestibilità e la disponibilità in Intune. Quando questa modifica diventerà effettiva, non sarà più eseguita la gestione del plug-in Cordova per Microsoft Intune App SDK né si riceveranno aggiornamenti. Gli sviluppatori di App non potranno usare questo plug-in. Intune intende continuare a supportare le app create con Cordova. Tuttavia, tutte le app create con il plug-in Cordova per Microsoft Intune App SDK subiranno una riduzione delle funzionalità in Intune. Dopo il wrapping con lo strumento di wrapping delle app di Intune, le app possono essere distribuite agli utenti finali nel modo usuale. Per le app Android basate su Cordova rilasciate in Google Play Store:
- Al primo avvio agli utenti finali verranno chieste le credenziali ricevere i criteri di Intune.
- Le app dovranno essere rilasciate nell'App Store destinato agli utenti di Intune, ad esempio "App Contoso per Intune". 

Per altre informazioni sullo strumento di wrapping delle app, vedere [Strumento di wrapping delle app per iOS](app-wrapper-prepare-ios.md) e [Strumento di wrapping delle app per Android](app-wrapper-prepare-android.md). Per problemi o domande, contattare [ msintuneappsdk@microsoft.com ](mailto:msintuneappsdk@microsoft.com). 

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Pianificare per il cambiamento: iniziare a usare Intune in Azure per la gestione MDM <!-- 1227338 -->
Oltre un anno fa è stata annunciata l'[anteprima pubblica di Intune in Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) a cui è seguita, sei mesi fa, la [disponibilità generale della nuova esperienza amministrativa](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) per Intune. A partire dal 2 aprile 2018, la gestione dei dispositivi mobili (MDM, Mobile Device Management) verrà disattivata nella console di Silverlight classica per i clienti che usano la versione autonoma di Intune. Per le esigenze MDM sarà invece possibile usare [Intune in Azure](https://aka.ms/Intune_on_Azure). È consigliabile che i clienti che usano ancora la console classica per MDM inizino ad acquisire familiarità con Intune in Azure. Questo cambiamento non avrà alcun impatto sull'utente finale. La gestione dei PC classica rimarrà in Silverlight. Altre informazioni su questo cambiamento e sui relativi effetti sono disponibili [qui](https://aka.ms/Intune_on_Azure_mdm).


### <a name="plan-for-change-easy-assist-end-of-life----1556480---"></a>Modifica prevista: fine del ciclo di vita di Easy Assist <!-- 1556480 -->
Intune usa Microsoft Easy Assist per l'assistenza remota di gestione dei PC. Potrebbe non essere noto che Microsoft Easy Assist è un componente di Office Live Meeting, un servizio deprecato il 31 dicembre 2017. Per questo motivo, anche il ciclo di vita di Easy Assist di Intune terminerà il 31 dicembre 2017.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gestire i dispositivi Android for Work indipendentemente dai dispositivi Android <!-- 1490731 EEready-->    
**Nota**: la distribuzione di queste modifiche avrà inizio con l'aggiornamento di novembre, ma eseguirla nel proprio account può richiedere tempo. Quando queste modifiche vengono rese effettive per il proprio account, si riceverà una notifica di conferma nel portale di Office 365. Dopo la distribuzione saranno disponibili opzioni aggiuntive per la gestibilità. L'esperienza dell'utente finale non subirà variazioni durante la distribuzione.

Intune supporta la gestione della registrazione di dispositivi Android for Work indipendentemente dalla piattaforma Android. Queste impostazioni vengono gestite in **Registrazione del dispositivo** > **Restrizioni registrazione** > **Restrizioni sul tipo di dispositivi**. In precedenza erano disponibili in **Registrazione del dispositivo** > **Registrazione di Android for Work** > **Impostazioni di registrazione per Android for Work**.

Per impostazione predefinita, le impostazioni dei dispositivi Android for Work corrispondono alle impostazioni dei dispositivi Android. Tuttavia, dopo la modifica delle impostazioni Android for Work questa corrispondenza andrà persa.

Se si blocca la registrazione dei dispositivi Android for Work personali, solo i dispositivi Android aziendali possono essere registrati come Android for Work.

Durante l'uso delle nuove impostazioni, considerare i punti seguenti:

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

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>Deprecazione del supporto per OS X Mavericks 10.10 e versioni precedenti di macOS<!--1489263, plan for change for 1802-->
Nel mese di febbraio 2018 inizierà la deprecazione della registrazione per dispositivi con OS X Yosemite 10.10 e versioni precedenti di macOS. Intune supporta completamente OS X El Capitan 10.11 e versioni più recenti.

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Nuovo percorso per i dispositivi gestiti nell'API Graph <!-- 1586728 -->
Il percorso usato per accedere ai dispositivi gestiti nella versione beta dell'API Graph è in corso di modifica. 

| | |
|--|--|
| Percorso corrente |  https://graph.microsoft.com/beta/managedDevices |
| Nuovo percorso | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

Entrambi i percorsi funzioneranno per l'intero mese di ottobre. Successivamente alla versione di ottobre, sarà possibile usare solo il nuovo percorso.  Se si usa l'API Graph per accedere ai dispositivi gestiti, aggiornare e verificare gli script e le applicazioni con il nuovo percorso. Per altre modifiche, controllare il [log delle modifiche mensile dell'API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog).


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima della registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiedono un'unica migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere al portale di Azure, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Ruoli di amministrazione in corso di sostituzione nel portale di Azure
I ruoli di amministrazione di gestione delle applicazioni per dispositivi mobili (MAM) esistenti (Collaboratore, Proprietario e Sola lettura) usati nel portale classico di Intune (Silverlight) verranno sostituiti con un set completo di nuovi controlli di amministrazione in base al ruolo nel portale di Intune di Azure. Dopo aver completato la migrazione al portale di Azure, sarà necessario riassegnare gli amministratori a questi nuovi ruoli di amministrazione. Per altre informazioni sul controllo degli accessi in base al ruolo e i nuovi ruoli, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo) per Microsoft Intune](/intune/role-based-access-control).

## <a name="whats-coming"></a>Sviluppi futuri

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>Aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS <!--1412866-->

Verrà rilasciato un importante aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS. L'aggiornamento include una riprogettazione grafica completa che conferisce all'app un aspetto moderno, maggiore usabilità e accessibilità. Tutte le attuali funzionalità del Portale aziendale per iOS saranno mantenute.

Tramite il programma Apple TestFlight viene offerta una versione non definitiva dell'app Portale aziendale aggiornata per iOS che l'utente può usare e per la quale può inviare i propri commenti e suggerimenti. Effettuare l'iscrizione in https://aka.ms/intune_ios_cp_testflight per l'accesso a TestFlight.

### <a name="conditional-access-policies-for-intune-will-only-be-available-from-the-azure-portal-----1737088---"></a>I criteri di accesso condizionale per Intune saranno disponibili solo dal portale di Azure <!-- 1737088 -->
È in corso la semplificazione delle posizioni da cui è possibile configurare e gestire l'accesso condizionale. È attualmente possibile gestire l'accesso condizionale dal pannello Protezione app di Intune (MAM) e tramite l'esperienza di Azure AD classica nel [portale di Windows Azure](https://manage.windowsazure.com). A partire da gennaio, sarà possibile configurare e gestire i criteri solo nel [portale di Azure](https://portal.azure.com) da **Azure Active Directory** > **Accesso condizionale**. Per praticità, è possibile accedere a questo pannello anche da Intune nel portale di Azure in **Intune** > **Accesso condizionale**.

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747--"></a>Gestire dispositivi macOS registrati in Jamf con il motore di conformità dei dispositivi di Intune <!--1592747-->
A partire dai primi mesi del 2018, Jamf invierà informazioni sullo stato dei dispositivi macOS a Intune, che ne valuterà la conformità ai criteri definiti nella console di Intune. In base allo stato di conformità dei dispositivi e ad altre condizioni (ad esempio la posizione, il rischio utente e così via), l'accesso condizionale imporrà la conformità ai dispositivi macOS che accedono alle applicazioni cloud e locali connesse ad Azure AD, incluso Office 365.

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Modifiche nel supporto per l'app Portale aziendale per iOS di Intune  <!-- 1164474  -->
Presto verrà resa disponibile una nuova versione dell'app Portale aziendale di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 9.0 o versioni successive. La versione del portale aziendale che supporta iOS 8 sarà comunque disponibile per un breve periodo di tempo. Se tuttavia vengono usate app iOS abilitate per MAM, il sistema iOS 9.0 e le versioni successive sono supportate. È quindi opportuno assicurarsi che gli utenti finali eseguano l'aggiornamento al sistema operativo più recente. 

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Ciò verrà comunicato in anticipo. Sebbene non sia stata ancora definita una data specifica, c'è tuttavia tempo per pianificare l'aggiornamento. Assicurarsi che gli utenti abbiano eseguito l'aggiornamento a iOS 9+ e che eseguano l'aggiornamento all'app Portale aziendale quando viene rilasciata.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Richiedere agli utenti di eseguire l'aggiornamento a iOS 9.0 o versioni successive per poter usare al meglio le nuove funzionalità di Intune.  Richiedere agli utenti di installare la nuova versione del portale aziendale e usufruire delle nuove funzionalità.

Passare a Intune nel portale di Azure, visualizzare Dispositivi > Tutti i dispositivi e filtrare l'elenco in base alla versione di iOS per visualizzare eventuali dispositivi correnti con i sistemi operativi precedenti a iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->
Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS.

Microsoft ha reso disponibile una versione dell'app Portale aziendale per iOS tramite il programma Apple TestFlight che applica i nuovi requisiti ATS. Se si desidera provarla in modo da poterne verificare la conformità con ATS, inviare un messaggio di indirizzo elettronica all'indirizzo <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con nome, cognome, indirizzo di posta elettronica e nome della società. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

## <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md) (Novità nell'interfaccia utente del portale aziendale)
* [Novità dei mesi precedenti](whats-new-archive.md)
