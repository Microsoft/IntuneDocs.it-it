---
title: Impostazioni delle baseline di sicurezza di Intune per Windows 10
titleSuffix: Microsoft Intune
description: Esaminare i valori predefiniti e le impostazioni disponibili presenti nella baseline di sicurezza di Windows MDM per i dispositivi Windows 10 gestiti con Intune.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/03/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ROBOTS: NOINDEX
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff7d3b39dc7675a00c5fba204609848f28a64dab
ms.sourcegitcommit: 24487f078349795922dc497c952e8358cf767a1a
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977836"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Impostazioni della baseline di sicurezza MDM per Intune  

Visualizzare le impostazioni della baseline di sicurezza MDM supportate da Microsoft Intune per i dispositivi che eseguono Windows 10 o versioni successive. I valori predefiniti per le impostazioni in questa baseline rappresentano la configurazione consigliata per i dispositivi applicabili e potrebbero non corrispondere alle impostazioni predefinite di altre baseline di sicurezza.  

La versione della baseline più recente è la **Baseline della sicurezza MDM per maggio 2019**  

Per informazioni sulle modifiche apportate nella versione più recente di questa baseline, vedere [Modifiche apportate al nuovo modello](#whats-changed-in-the-new-template).  

> [!NOTE]  
> Nel giugno del 2019 la baseline di sicurezza MDM di anteprima è stata sostituita dalla versione del modello *Baseline della sicurezza MDM per maggio 2019*, disponibile a livello generale (non in anteprima). I profili creati prima della disponibilità della *Baseline della sicurezza MDM per maggio 2019* non verranno aggiornati in modo da riflettere le impostazioni e i valori presenti nella baseline di sicurezza MDM per maggio 2019.  Sebbene non sia possibile creare nuovi profili in base al modello di anteprima, è possibile modificare e continuare a usare i profili creati in precedenza basati sul modello di anteprima. 
  
Per informazioni sull'uso delle baseline di sicurezza con Intune, vedere [Usare le baseline di sicurezza](security-baselines.md).  

## <a name="above-lock"></a>Notifiche sulla schermata di blocco  
Per altre informazioni, vedere [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) (Provider di servizi di configurazione dei criteri - AboveLock) nella documentazione di Windows.  

- **Bloccare la visualizzazione delle notifiche di tipo avviso popup**  
  L'impostazione di questo criterio consente di impedire la visualizzazione delle notifiche dell'app nella schermata di blocco. Se si abilita l'impostazione di questo criterio, le notifiche dell'app non vengono visualizzate nella schermata di blocco. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti possono scegliere quali app visualizzano le notifiche nella schermata di blocco.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Impostazione predefinita**: Sì  

- **Attiva tramite voce le app dalla schermata di blocco**  

  **Impostazione predefinita**: Disabilitato

## <a name="app-runtime"></a>Runtime app    
Per altre informazioni, vedere [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) (Provider di servizi di configurazione dei criteri - AppRuntime) nella documentazione di Windows.  

- **Account Microsoft facoltativi per le app di 
  Microsoft Store**  
  L'impostazione di questo criterio consente di controllare se gli account Microsoft sono facoltativi per le app di Microsoft Store che richiedono un account per l'accesso. Questo criterio influisce solo sulle app di Microsoft Store che lo supportano. Se si abilita l'impostazione di questo criterio, le app di Microsoft Store che in genere richiedono un account Microsoft per l'accesso consentiranno agli utenti di accedere invece con un account aziendale. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti devono eseguire l'accesso con un account Microsoft.  
[Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067104)  
  
  **Impostazione predefinita**: Abilitato  

## <a name="application-management"></a>Gestione delle applicazioni   
Per altre informazioni, vedere [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) (Provider di servizi di configurazione dei criteri - ApplicationManagement) nella documentazione di Windows.  

- **Impedisci il controllo utente sulle installazioni**  
  Questa impostazione di criteri consente agli utenti di modificare le opzioni di installazione accessibili in genere solo agli amministratori di sistema. Se si abilita questa impostazione di criteri, alcune delle funzionalità di sicurezza di Windows Installer verranno ignorate. Consente di completare le installazioni che altrimenti verrebbero interrotte a causa di violazioni della sicurezza. Se questa impostazione viene disabilitata o non viene configurata, le funzionalità di sicurezza di Windows Installer impediscono agli utenti di modificare le opzioni di installazione generalmente riservate agli amministratori di sistema, ad esempio l'impostazione della directory in cui vengono installati i file. Se Windows Installer rileva che un pacchetto di installazione ha consentito all'utente di modificare un'opzione protetta, l'installazione viene arrestata e viene visualizzato un messaggio. Queste funzionalità di sicurezza funzionano solo quando il programma di installazione viene eseguito in un contesto di sicurezza con privilegi e ha accesso alle directory negate all'utente. Questa impostazione dei criteri è progettata per ambienti meno restrittivi. Può essere usata per evitare gli errori in un programma di installazione che impedisce l'installazione di software.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Impostazione predefinita**: Sì

- **Impedisci le installazioni di app con privilegi elevati**  
  Questa impostazione dei criteri indica a Windows Installer di usare le autorizzazioni elevate per installare qualsiasi programma nel sistema.  
  - *Se si abilita questa impostazione di criteri*, i privilegi vengono estesi a tutti i programmi. In genere, questi privilegi sono riservati ai programmi assegnati all'utente (offerti sul desktop), assegnati al computer (installati automaticamente) o resi disponibili in Installazione applicazioni nel Pannello di controllo. Questa impostazione del profilo consente agli utenti di installare programmi che richiedono l'accesso a directory per le quali l'utente potrebbe non avere le autorizzazioni per la visualizzazione o la modifica, incluse le directory in computer con restrizioni elevate.
  - *Se questa impostazione di criteri viene disabilitata o non configurata*, il sistema applica le autorizzazioni dell'utente corrente durante l'installazione di programmi che non vengono distribuiti o offerti da un amministratore di sistema. Nota: questa impostazione di criteri è presente in entrambe le cartelle Configurazione computer e Configurazione utente. Per rendere effettiva questa impostazione di criteri, è necessario abilitarla in entrambe le cartelle. Attenzione: gli utenti esperti possono sfruttare le autorizzazioni concesse da questa impostazione di criteri per modificare i loro privilegi e ottenere l'accesso permanente a file e cartelle con restrizioni. Si noti che non è garantita la sicurezza della versione di Configurazione utente di questa impostazione di criteri.  
  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067134)    

  **Impostazione predefinita**: Sì

- **Bloccare Game DVR (solo desktop)**  
  consente di specificare se la registrazione e la trasmissione dei giochi sono consentite.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067056)  
  
  **Impostazione predefinita**: Sì  

## <a name="auto-play"></a>Riproduzione automatica   
Per altre informazioni, vedere [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) (Provider di servizi di configurazione dei criteri - Autoplay) nella documentazione di Windows.  

- **Comportamento di esecuzione automatica predefinito per la riproduzione automatica**  
  Questa impostazione influisce sul comportamento predefinito per i comandi di esecuzione automatica. I comandi di esecuzione automatica sono archiviati all'interno di file autorun.inf e sono in grado di avviare programmi di installazione e altre routine. Se *Abilitato*, gli amministratori possono modificare il comportamento di esecuzione automatica predefinito in un dispositivo che esegue Windows Vista o versioni successive. Il comportamento può essere impostato in modo da: a) disabilitare completamente i comandi di esecuzione automatica oppure b) ripristinare il comportamento delle versioni precedenti a Windows Vista che prevede l'esecuzione automatica del comando. Se impostato su *Disabilitato* o *Non configurato*, nei dispositivi con Windows Vista o versioni successive viene chiesto all'utente di confermare se eseguire o meno un comando di esecuzione automatica.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067133)       
  
  **Impostazione predefinita**: Non eseguire  
  
- **Modalità di riproduzione automatica**  
  L'impostazione di questo criterio consente di disattivare la funzionalità AutoPlay. AutoPlay inizia a leggere il contenuto di un'unità non appena il supporto viene inserito nell'unità. Di conseguenza, il file di installazione dei programmi e la musica presente nel supporto audio vengono immediatamente avviati. Nelle versioni precedenti a Windows XP SP2, AutoPlay è disabilitato per impostazione predefinita nelle unità rimovibili, ad esempio l'unità floppy (ma non l'unità CD-ROM), e nelle unità di rete. A partire da Windows XP SP2, AutoPlay è abilitato anche per le unità rimovibili, tra cui le unità Zip e alcuni dispositivi di archiviazione di massa USB. Se si abilita l'impostazione di questo criterio, AutoPlay viene disabilitato nelle unità CD-ROM e per supporti rimovibili oppure viene disabilitato in tutte le unità. L'impostazione di questo criterio disabilita AutoPlay in tipi di unità aggiuntivi. Non è possibile usare questa impostazione per abilitare AutoPlay nelle unità in cui è disabilitato per impostazione predefinita. Se si disabilita o non si configura l'impostazione di questo criterio, AutoPlay è abilitato. Nota: l'impostazione di questo criterio è presente in entrambe le cartelle Configurazione computer e Configurazione utente. Se le impostazioni del criterio sono in conflitto, l'impostazione del criterio in Configurazione computer ha la precedenza su quella in Configurazione utente.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2066793)  
  
  **Impostazione predefinita**: Disabilitato

- **Bloccare la riproduzione automatica per i dispositivi non di volume**  
  L'impostazione di questo criterio non consente la funzionalità AutoPlay per i dispositivi MTP come fotocamere o telefoni. Se si abilita l'impostazione di questo criterio, la funzionalità AutoPlay non sarà consentita per i dispositivi MTP come fotocamere o telefoni. Se si disabilita o non si configura l'impostazione di questo criterio, la funzionalità AutoPlay è abilitata per i dispositivi non di volume.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067106)    
  
  **Impostazione predefinita**: Abilitato  

## <a name="bitlocker"></a>BitLocker    
Per altre informazioni, vedere [CSP dei criteri - BitLocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) nella documentazione di Windows.  

- **BitLocker - Impostazioni dell'unità rimovibile**  
  L'impostazione di questo criterio viene usata per controllare il metodo di crittografia e il livello di codifica. I valori di questo criterio determinano il livello di codifica usato da BitLocker per la crittografia. Per una maggiore sicurezza, le aziende potrebbero voler controllare il livello di crittografia (AES-256 è un algoritmo più avanzato rispetto a AES-128). Se si abilita questa impostazione, sarà possibile configurare individualmente un algoritmo di crittografia e un livello di codifica per unità dati fisse, unità del sistema operativo e unità dati rimovibili. Per le unità fisse e del sistema operativo è consigliabile usare l'algoritmo XTS-AES. Per le unità rimovibili è consigliabile usare AES-CBC a 128 bit o AES-CBC a 256 bit se l'unità viene usata in altri dispositivi che non eseguono Windows 10 versione 1511 o successiva. La modifica del metodo di crittografia non produce alcun effetto se l'unità è già crittografata o se la crittografia è in corso. In questi casi, l'impostazione di questo criterio viene ignorata.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Per i criteri di un'unità rimovibile BitLocker, configurare l'impostazione seguente:

  - **Richiedere la crittografia per l'accesso in scrittura**  
    **Impostazione predefinita**: Sì  
  

## <a name="browser"></a>Browser  
Per altre informazioni, vedere [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) (Provider di servizi di configurazione dei criteri - Browser) nella documentazione di Windows.  

- **Richiedere SmartScreen per Microsoft Edge**  
  Per impostazione predefinita, Microsoft Edge usa Microsoft Defender SmartScreen (attivato) per proteggere gli utenti da potenziali tentativi di phishing e software dannoso. Per impostazione predefinita, gli utenti non possono disabilitare (disattivare) Microsoft Defender SmartScreen. L'abilitazione di questo criterio determina la disattivazione di Microsoft Defender SmartScreen e ne impedisce l'attivazione da parte degli utenti. Non configurare questo criterio in modo da consentire agli utenti di scegliere di attivare o disattivare Microsoft Defender SmartScreen.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Impostazione predefinita**: Sì  
  
- **Bloccare l'accesso a siti dannosi**  
  Per impostazione predefinita, Microsoft Edge consente agli utenti di ignorare gli avvisi di Microsoft Defender SmartScreen relativi a siti potenzialmente dannosi, in modo che sia possibile visitare il sito. Con questo criterio, tuttavia, è possibile configurare Microsoft Edge per impedire agli utenti di ignorare gli avvisi, non consentendo di visitare il sito.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Impostazione predefinita**: Sì  
  
- **Bloccare il download di file non verificati**  
  Per impostazione predefinita, Microsoft Edge consente agli utenti di ignorare gli avvisi di Microsoft Defender SmartScreen relativi a file potenzialmente dannosi, in modo da continuare a scaricare i file non verificati. L'abilitazione di questo criterio impedisce agli utenti di ignorare gli avvisi, bloccando il download dei file non verificati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067023)  
  
  **Impostazione predefinita**: Sì  
  
- **Bloccare lo strumento per la gestione delle password**  
  Per impostazione predefinita, Microsoft Edge usa automaticamente lo strumento per la gestione delle password, consentendo agli utenti di gestire le password localmente. La disabilitazione di questo criterio impedisce a Microsoft Edge di usare lo strumento per la gestione delle password. Non configurare questo criterio se si vuole consentire agli utenti di scegliere di salvare e gestire localmente le password tramite lo strumento per la gestione delle password.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067128)  
  
  **Impostazione predefinita**: Sì  
  
- **Impedire di ignorare gli errori di certificato**  
  L'impostazione di questo criterio impedisce all'utente di ignorare gli errori di certificato Secure Sockets Layer/Transport Layer Security (SSL/TLS) che interrompono l'esplorazione in Internet Explorer, ad esempio errori relativi a certificati "scaduti", "revocati" o con "nomi non corrispondenti". Se si abilita l'impostazione di questo criterio, l'utente non può continuare l'esplorazione. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente può scegliere di ignorare gli errori di certificato e continuare l'esplorazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067126)  
  
  **Impostazione predefinita**: Sì  

## <a name="connectivity"></a>Connettività  
Per altre informazioni, vedere [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) (Provider di servizi di configurazione dei criteri - Connectivity) nella documentazione di Windows.  

- **Bloccare il download Internet per la Pubblicazione guidata sul Web e l'Ordinazione guidata via Internet**  
  L'impostazione di questo criterio specifica se Windows deve scaricare un elenco di provider per la Pubblicazione guidata sul Web e l'Ordinazione guidata via Internet. Queste procedure guidate consentono la selezione da un elenco di aziende che offrono servizi quali l'archiviazione online e la stampa di fotografie. Per impostazione predefinita, Windows visualizza i provider scaricati da un sito Web Windows oltre a quelli specificati nel Registro di sistema. Se si abilita l'impostazione di questo criterio, Windows non scarica provider e vengono visualizzati solo i provider di servizi memorizzati nella cache del Registro di sistema locale. Se si disabilita o non si configura l'impostazione di questo criterio, verrà scaricato un elenco di provider quando l'utente usa la Pubblicazione guidata sul Web o l'Ordinazione guidata via Internet. Per altre informazioni che includono i dettagli su come specificare i provider di servizi nel Registro di sistema, vedere la documentazione relativa alla Pubblicazione guidata sul Web e all'Ordinazione guidata via Internet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067136)  
  
  **Impostazione predefinita**: Abilitato  

- **Configura l'accesso sicuro ai percorsi UNC**  
  Questa impostazione di criteri consente di configurare l'accesso sicuro ai percorsi UNC. Se si abilita questo criterio, Windows consente solo l'accesso ai percorsi UNC specificati dopo il superamento dei requisiti di sicurezza aggiuntivi.
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067243) 

  **Impostazione predefinita**: Configura Windows per consentire l'accesso solo ai percorsi UNC specificati dopo il superamento dei requisiti di sicurezza aggiuntivi
  
  Quando si seleziona *Configura Windows per consentire l'accesso solo ai percorsi UNC specificati dopo il superamento dei requisiti di sicurezza aggiuntivi*, è possibile configurare l'elenco di percorsi UNC con protezione avanzata.
  - **Elenco di percorsi UNC con protezione avanzata**  
    Selezionare **Aggiungi** per specificare i flag di sicurezza e i percorsi del server aggiuntivi.  

- **Bloccare il download di driver di stampa su HTTP**  
  L'impostazione di questo criterio specifica se consentire al client di scaricare pacchetti di driver di stampa su HTTP. Per configurare la stampa su HTTP è necessario scaricare su HTTP i driver non inclusi nel prodotto. Nota: l'impostazione di questo criterio non impedisce al client di eseguire la stampa su stampanti nella rete Intranet o su Internet tramite HTTP. Viene solo impedito il download di driver non installati in locale. Se si abilita l'impostazione di questo criterio, non sarà possibile scaricare i driver di stampa su HTTP. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti possono scaricare i driver di stampa su HTTP.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067141)  
  
  **Impostazione predefinita**: Abilitato  

## <a name="credentials-delegation"></a>Delega di credenziali  
Per altre informazioni, vedere [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) (Provider di servizi di configurazione dei criteri - CredentialsDelegation) nella documentazione di Windows.  

- **Delega di credenziali non esportabili con l'host remoto**  
  L'host remoto consente la delega delle credenziali non esportabili. Quando si usa la delega delle credenziali, i dispositivi forniscono una versione delle credenziali che possono essere esportate nell'host remoto, esponendo in tal modo gli utenti al rischio di furto da parte di malintenzionati nell'host remoto. Se si abilita l'impostazione di questo criterio, l'host supporta la modalità di amministrazione limitata o la modalità Remote Credential Guard. Se si disabilita o non si configura l'impostazione di questo criterio, le modalità di amministrazione limitata e Remote Credential Guard non sono supportate. Gli utenti dovranno sempre passare le proprie credenziali all'host.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067103)   
  
  **Impostazione predefinita**: Abilitato  

## <a name="credentials-ui"></a>Interfaccia utente per le credenziali  
Per altre informazioni, vedere [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) (Provider di servizi di configurazione dei criteri - CredentialsUI) nella documentazione di Windows.  

- **Enumera gli amministratori** L'impostazione di questo criterio determina la visualizzazione o meno degli account amministratore quando un utente prova a elevare i privilegi di un'applicazione in esecuzione. Per impostazione predefinita, gli account amministratore non vengono visualizzati quando l'utente prova a elevare i privilegi di un'applicazione in esecuzione. Se si abilita l'impostazione di questo criterio, vengono visualizzati tutti gli account amministratore locali del PC e l'utente potrà sceglierne uno e immettere la password corretta. Se si disabilita l'impostazione di questo criterio, per l'elevazione dei privilegi sarà sempre necessario digitare un nome utente e una password.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067021)

  
  **Impostazione predefinita**: Disabilitato  

## <a name="data-protection"></a>Protezione dati  
Per altre informazioni, vedere [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) (Provider di servizi di configurazione dei criteri - DataProtection) nella documentazione di Windows.  

- **Blocca l'accesso diretto alla memoria**  
  L'impostazione di questo criterio consente di bloccare l'accesso diretto alla memoria (Direct Memory Access, DMA) per tutte le porte downstream PCI collegabili a sistema acceso finché un utente non accede a Windows. Dopo l'accesso di un utente, Windows enumererà i dispositivi PCI connessi alle porte PCI collegabili a sistema acceso. Ogni volta che l'utente blocca il computer, l'accesso diretto alla memoria viene bloccato sulle porte PCI collegabili a sistema acceso senza dispositivi figlio finché l'utente non accede di nuovo. I dispositivi già enumerati quando il computer era sbloccato continueranno a funzionare fino a quando non saranno scollegati. L'impostazione di questo criterio viene applicata solo quando è abilitato BitLocker o la crittografia del dispositivo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067031)     
  
  **Impostazione predefinita**: Sì  

## <a name="device-guard"></a>Device Guard  
Per altre informazioni, vedere [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) (Provider di servizi di configurazione dei criteri - DeviceGuard) nella documentazione di Windows.  

- **Credential Guard**  
  Questa impostazione consente agli utenti di attivare Credential Guard con la sicurezza basata sulla virtualizzazione per proteggere le credenziali al riavvio successivo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067044)
   
  **Impostazione predefinita**: Abilita con blocco UEFI 

- **Abilitare la sicurezza basata sulla virtualizzazione**   
  Attiva la sicurezza basata sulla virtualizzazione al riavvio successivo. La sicurezza basata sulla virtualizzazione usa Windows Hypervisor per offrire il supporto per i servizi di sicurezza.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067066)  
  
  **Impostazione predefinita**: Sì  


- **Avvia Protezione del sistema**    
  **Impostazione predefinita**: Abilitato  

## <a name="device-installation"></a>Installazione di dispositivi  
Per altre informazioni, vedere [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) (Provider di servizi di configurazione dei criteri - DeviceInstallation) nella documentazione di Windows.  

- **Installazione di dispositivi hardware per identificatori di dispositivo**  
  L'impostazione di questo criterio consente di specificare un elenco di ID hardware Plug and Play e ID compatibili per i dispositivi la cui installazione non è consentita in Windows. L'impostazione di questo criterio ha la precedenza su qualsiasi altra impostazione di criteri che consente a Windows di installare un dispositivo. Se si abilita l'impostazione di questo criterio, viene impedito a Windows di installare i dispositivi il cui ID hardware o ID compatibile sia presente nell'elenco creato. Se si abilita l'impostazione di questo criterio in un server desktop remoto, l'impostazione del criterio influirà sul reindirizzamento dei dispositivi specificati da un client desktop remoto al server desktop remoto. Se si disabilita o non si configura l'impostazione di questo criterio, è possibile installare e aggiornare i dispositivi in base a quanto consentito o impedito da altre impostazioni di criteri.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2066794)  
  
  **Impostazione predefinita**: Bloccare l'installazione del dispositivo hardware  

  Quando l'opzione *Blocca l'installazione del dispositivo hardware* è selezionata, sono disponibili le impostazioni seguenti.

  - **Rimuovi i dispositivi hardware corrispondenti**   
    Questa impostazione è disponibile solo quando l'*installazione di dispositivi hardware per identificatori di dispositivo* è impostata su *Bloccare l'installazione del dispositivo hardware*.
    
    **Impostazione predefinita**: Sì

  - **Identificatori di dispositivo hardware bloccati**  
    Questa impostazione è disponibile solo quando l'*installazione di dispositivi hardware per identificatori di dispositivo* è impostata su *Bloccare l'installazione del dispositivo hardware*.
    
    **Impostazione predefinita**: Sì  
  
- **Installazione di dispositivi hardware per classi di installazione**  
  L'impostazione di questo criterio consente di specificare un elenco di identificatori univoci globali (GUID) della classe di installazione del dispositivo per i driver di dispositivo la cui installazione non è consentita in Windows. L'impostazione di questo criterio ha la precedenza su qualsiasi altra impostazione di criteri che consente a Windows di installare un dispositivo. Se si abilita l'impostazione di questo criterio, viene impedito a Windows di installare o aggiornare i driver di dispositivo il cui GUID della classe di installazione del dispositivo sia presente nell'elenco creato. Se si abilita l'impostazione di questo criterio in un server desktop remoto, l'impostazione del criterio influirà sul reindirizzamento dei dispositivi specificati da un client desktop remoto al server desktop remoto. Se si disabilita o non si configura l'impostazione di questo criterio, Windows potrà installare e aggiornare i dispositivi in base a quanto consentito o impedito da altre impostazioni di criteri.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067048)  
  
  **Impostazione predefinita**: Bloccare l'installazione del dispositivo hardware  

  Quando l'opzione *Blocca l'installazione del dispositivo hardware* è selezionata, sono disponibili le impostazioni seguenti.
  - **Rimuovi i dispositivi hardware corrispondenti**    
    Questa impostazione è disponibile solo quando l'*installazione di dispositivi hardware per classi di installazione* è impostata su *Bloccare l'installazione del dispositivo hardware*.  

    **Impostazione predefinita**: *Nessuna configurazione predefinita*  

  - **Identificatori di dispositivo hardware bloccati**  
    Questa impostazione è disponibile solo quando l'*installazione di dispositivi hardware per classi di installazione* è impostata su *Bloccare l'installazione del dispositivo hardware*.
    
    **Impostazione predefinita**: *Nessuna configurazione predefinita*  

## <a name="device-lock"></a>Blocco del dispositivo  
Per altre informazioni, vedere [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) (Provider di servizi di configurazione dei criteri - DeviceLock) nella documentazione di Windows.  

- **Impedire l'uso della fotocamera**  
  Disabilita l'interruttore Attiva/Disattiva per la fotocamera nella schermata di blocco in Impostazioni PC e impedisce di richiamare una fotocamera nella schermata di blocco. Per impostazione predefinita, gli utenti possono abilitare la chiamata di una fotocamera disponibile nella schermata di blocco. Se si abilita questa impostazione, gli utenti non potranno più abilitare o disabilitare l'accesso alla fotocamera nella schermata di blocco in Impostazioni PC e la fotocamera non potrà essere richiamata nella schermata di blocco.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067052)
  
  **Impostazione predefinita**: Abilitato  

- **Richiedere la password**  
  Specifica se il blocco del dispositivo è abilitato.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067049)  
  
  **Impostazione predefinita**: Sì  
  
  Quando *Richiedi password* è impostata su *Yes*, sono disponibili le impostazioni seguenti.

  - **Conteggio set di caratteri minimo password**  
    Numero di tipi di elementi complessi (lettere maiuscole e minuscole, numeri e punteggiatura) richiesto per un PIN o una password complessa. Il PIN applica il comportamento seguente per i dispositivi desktop e mobili: 1 - Solo cifre 2 - Cifre e lettere minuscole obbligatorie 3 - Cifre, lettere minuscole e lettere maiuscole obbligatorie. Non supportato negli account Microsoft desktop e negli account di dominio. 4 - Cifre, lettere minuscole, lettere maiuscole e caratteri speciali obbligatori. Non supportato nei dispositivi desktop. Il valore predefinito è 1.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067055)  
    
    **Impostazione predefinita**: 3  

  - **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**  
    Numero di errori di autenticazione consentiti prima che il dispositivo venga cancellato. Il valore 0 disabilita la funzionalità di cancellazione del dispositivo.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067030)  
      
    **Impostazione predefinita**: 10  

  - **Scadenza password (giorni)**  
    L'impostazione del criterio Validità massima password specifica per quanto tempo (giorni) è possibile usare una password prima che il sistema richieda all'utente di modificarla. È possibile impostare la scadenza delle password dopo un numero di giorni compreso tra 1 e 999 oppure è possibile specificare che le password non hanno scadenza impostando il numero di giorni su 0. Se la Validità massima password è compresa tra 1 e 999 giorni, la Validità minima password deve essere inferiore della validità massima password. Se la Validità massima password è impostata su 0, la Validità minima password può essere qualsiasi valore compreso tra 0 e 998 giorni.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067028)  
    
    **Impostazione predefinita**: 60  

  - **Tipo di password richiesto**  
    Determina il tipo di PIN o password obbligatorio.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067027)  
    
    **Impostazione predefinita**: Alfanumerico  

  - **Lunghezza minima password**  
    L'impostazione del criterio Lunghezza minima password determina il numero minimo di caratteri della password di un account utente. È possibile impostare un valore compreso tra 1 e 14 caratteri oppure è possibile specificare che non è richiesta alcuna password impostando il numero di caratteri su 0.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067024)  
    
    **Impostazione predefinita**: 8  

  - **Bloccare le password semplici**  
    Specifica se sono consentiti PIN o password come "1111" o "1234". Per il desktop, controlla anche l'uso di password grafiche.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067127) 
    
    **Impostazione predefinita**: Sì  
      *L'impostazione Sì impedisce l'uso di password semplici.* 

  - **Impedisci riutilizzo delle password precedenti**  
    Specifica il numero di password che possono essere archiviate nella cronologia che non possono essere usate. Il valore include la password corrente dell'utente. Con un'impostazione di *1*, ad esempio, l'utente non può usare nuovamente la password corrente quando sceglie una nuova password. Un'impostazione di *5* significa che un utente non può definire la nuova password uguale alla password corrente o a una qualsiasi delle quattro precedenti.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2066795)  
    
    **Impostazione predefinita**: 24  

- **Impedire la presentazione**  
  Disabilita le impostazioni per la presentazione nella schermata di blocco in Impostazioni PC e impedisce l'esecuzione di una presentazione nella schermata di blocco. Per impostazione predefinita, gli utenti possono abilitare una presentazione da eseguire dopo il blocco del computer. Se si abilita questa impostazione, gli utenti non possono modificare le impostazioni di presentazione nel PC né avviare alcuna presentazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067105) 
  
  **Impostazione predefinita**: Abilitato  
  *L'impostazione Abilitato impedisce l'esecuzione delle presentazioni.* 

- **Validità minima password in giorni**  
  L'impostazione del criterio Validità minima password specifica il periodo di tempo (in giorni) per cui è necessario usare una password prima che l'utente possa modificarla. È possibile impostare un valore compreso tra 1 e 998 giorni oppure è possibile consentire la modifica della password immediatamente impostando il numero di giorni su 0. La Validità minima password deve essere minore della Validità massima password, a meno che la Validità massima password non sia impostata su 0 che indica che le password non hanno scadenza. Se la Validità massima password è impostata su 0, la Validità minima password può essere impostata su qualsiasi valore compreso tra 0 e 998 giorni.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067022) 
  
  **Impostazione predefinita**: 1  

## <a name="dma-guard"></a>DMA Guard  
Per altre informazioni, vedere [Provider di servizi di configurazione dei criteri - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) nella documentazione di Windows.
- **Enumerazione di dispositivi esterni non compatibili con la protezione DMA del kernel**  
  Questo criterio ha lo scopo di fornire sicurezza aggiuntiva nei confronti dei dispositivi compatibili con DMA esterni. Consente inoltre maggiore controllo sull'enumerazione di dispositivi esterni idonei per DMA non compatibili con il remapping e/o l'isolamento e il sandboxing della memoria del dispositivo. Questo criterio viene applicato solo quando la protezione DMA del kernel è supportata e abilitata dal firmware del sistema. La protezione DMA del kernel è una funzionalità della piattaforma che non può essere controllata tramite criteri o dall'utente finale. Deve essere supportata dal sistema in fase di produzione. Per verificare se il sistema supporta la protezione DMA del kernel, controllare il campo della protezione DMA del kernel nella pagina di riepilogo di MSINFO32.exe.  
  [Altre informazioni](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)

  **Impostazione predefinita**: Blocca tutto   

## <a name="event-log-service"></a>Servizio Registro eventi  
Per altre informazioni, vedere [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) (Provider di servizi di configurazione dei criteri - EventLogService) nella documentazione di Windows.  

- **Dimensioni massime del file registro di protezione in KB**  
  L'impostazione di questo criterio specifica le dimensioni massime del file di registro espressa in KB. Se si abilita l'impostazione di questo criterio, è possibile configurare le dimensioni massime del file di registro in modo che siano comprese tra 1 MB (1024 KB) e 2 TB (2147483647 KB) in base a incrementi in KB. Se si disabilita o non si configura l'impostazione di questo criterio, le dimensioni massime del file di registro vengono impostate sul valore configurato in locale. Questo valore può essere modificato dall'amministratore locale usando la finestra di dialogo Proprietà registro e l'impostazione predefinita è 20 MB.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067042)  
  
   **Impostazione predefinita**: 196608  

- **Dimensioni massime del file registro di sistema in KB**  
  L'impostazione di questo criterio specifica le dimensioni massime del file di registro espressa in KB. Se si abilita l'impostazione di questo criterio, è possibile configurare le dimensioni massime del file di registro in modo che siano comprese tra 1 MB (1024 KB) e 2 TB (2147483647 KB) in base a incrementi in KB. Se si disabilita o non si configura l'impostazione di questo criterio, le dimensioni massime del file di registro vengono impostate sul valore configurato in locale. Questo valore può essere modificato dall'amministratore locale usando la finestra di dialogo Proprietà registro e l'impostazione predefinita è 20 MB.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2066798)  
  
  **Impostazione predefinita**: 32768  

- **Dimensioni massime del file registro applicazioni in KB**  
  L'impostazione di questo criterio specifica le dimensioni massime del file di registro espressa in KB. Se si abilita l'impostazione di questo criterio, è possibile configurare le dimensioni massime del file di registro in modo che siano comprese tra 1 MB (1024 KB) e 2 TB (2147483647 KB) in base a incrementi in KB. Se si disabilita o non si configura l'impostazione di questo criterio, le dimensioni massime del file di registro vengono impostate sul valore configurato in locale. Questo valore può essere modificato dall'amministratore locale usando la finestra di dialogo Proprietà registro e l'impostazione predefinita è 20 MB.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067125)  
  
  **Impostazione predefinita**: 32768  

## <a name="experience"></a>Esperienza  
Per altre informazioni, vedere [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (Provider di servizi di configurazione dei criteri - Experience) nella documentazione di Windows.  

- **Bloccare Contenuti in evidenza di Windows**  
  Consente agli amministratori IT di disattivare tutte le funzionalità di Contenuti in evidenza di Windows, Contenuti in evidenza di Windows nella schermata di blocco, Suggerimenti di Windows, le funzionalità per gli utenti consumer Microsoft e altre funzionalità correlate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067037)  
  
  **Impostazione predefinita**: Sì  

  Quando *Blocca Windows Spotlight* è impostata su *Sì*, sono disponibili le impostazioni seguenti.
  
  - **Bloccare i suggerimenti di terze parti in Contenuti in evidenza di Windows**  
    Specifica se consentire o meno i suggerimenti su app e contenuto di autori o distributori di software di terze parti nelle funzionalità di Contenuti in evidenza di Windows come Contenuti in evidenza di Windows nella schermata di blocco, le app suggerite nel menu Start e Suggerimenti di Windows. Gli utenti possono comunque visualizzare i suggerimenti per le funzionalità, le app e i servizi Microsoft.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067045)  
      
    **Impostazione predefinita**: Sì  
  - **Bloccare le funzionalità specifiche per i consumer**  
    Consente agli amministratori IT di attivare le esperienze solitamente riservate ai consumer, ad esempio i suggerimenti del menu Start, le notifiche sull'appartenenza, l'installazione di app post-OOBE e i riquadri di reindirizzamento.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067054)  
     
    **Impostazione predefinita**: Sì  

## <a name="exploit-guard"></a>Exploit Guard  
Per altre informazioni, vedere [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) (Provider di servizi di configurazione dei criteri - ExploitGuard) nella documentazione di Windows.  

- **XML di Protezione dagli exploit**  
  Consente all'amministratore IT di distribuire una configurazione che rappresenta il sistema desiderato e le opzioni di mitigazione delle applicazioni a tutti i dispositivi nell'organizzazione. La configurazione è rappresentata da un XML. La Protezione dagli exploit consente di proteggere i dispositivi da malware che usa gli exploit per la diffusione e l'infezione. Usare l'app Sicurezza di Windows o PowerShell per creare un set di mitigazioni, chiamato configurazione. È quindi possibile esportare la configurazione come file XML e condividerla con più computer in rete in modo che abbiano lo stesso set di impostazioni di mitigazione. È anche possibile convertire e importare un file XML di configurazione EMET esistente in un file XML di configurazione di protezione dagli exploit.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067035)  
  
  **Impostazione predefinita**: *È disponibile un file XML di esempio* 
 
## <a name="file-explorer"></a>Esplora file  
Per altre informazioni, vedere [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) (Provider di servizi di configurazione dei criteri - FileExplorer) nella documentazione di Windows.  

- **Bloccare Protezione esecuzione programmi**  
  La disattivazione di Protezione esecuzione programmi può consentire ad alcune applicazioni plug-in legacy di funzionare senza terminare Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067043)  
  
  **Impostazione predefinita**: Disabilitato  
   
- **Bloccare la terminazione heap in caso di danneggiamento**  
  Disabilitando la terminazione dell'heap in caso di danneggiamento, è possibile consentire il funzionamento di determinate applicazioni plug-in legacy senza terminare immediatamente Esplora risorse, sebbene quest'ultimo possa terminare in maniera imprevista in un secondo momento.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067107)  
  
  **Impostazione predefinita**: Disabilitato  
    

## <a name="internet-explorer"></a>Internet Explorer  
Per altre informazioni, vedere [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) (Provider di servizi di configurazione dei criteri - InternetExplorer) nella documentazione di Windows.  

- **Internet Explorer - Area con restrizioni - Aggiornamenti alla barra di stato tramite script**  
  L'impostazione di questo criterio consente di gestire gli aggiornamenti della barra di stato tramite gli script all'interno dell'area. 
  - *Se si abilita l'impostazione di questo criterio*, lo script potrà aggiornare la barra di stato.
  - *Se si disabilita o non si configura l'impostazione di questo criterio*, lo script non potrà aggiornare la barra di stato.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067074)  

  **Impostazione predefinita**: Disabilitato

- **Internet Explorer - Area Internet - Trascinare o copiare e incollare file**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte degli utenti di operazioni di trascinamento o di copia e incolla di file da un'origine appartenente all'area. Se si abilita l'impostazione di questo criterio, gli utenti potranno automaticamente trascinare o copiare e incollare file dall'area. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire il trascinamento o la copia di file dall'area. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno trascinare o copiare e incollare file dall'area. Se non si configura l'impostazione di questo criterio, gli utenti potranno automaticamente trascinare o copiare e incollare file dall'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067076)  

  **Impostazione predefinita**: Disabilitato

- **Internet Explorer - Area con restrizioni - Componenti basati su .NET Framework**    
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte di Internet Explorer di componenti .NET Framework senza firma Authenticode. Fra questi componenti sono inclusi i controlli gestiti a cui fa riferimento un tag oggetto e gli eseguibili gestiti a cui fa riferimento un collegamento. Se si abilita l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti senza firma. Se si seleziona Chiedi conferma nella casella a discesa, Internet Explorer chiederà all'utente di scegliere se consentire l'esecuzione di componenti gestiti senza firma. Se si disabilita l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti senza firma. Se non si configura l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti senza firma.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067077)

  **Impostazione predefinita**: Disabilitato


- **Internet Explorer - Area computer locale - Non eseguire programmi antimalware su controlli ActiveX**  
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067152)

  **Impostazione predefinita**: Disabilitato

- **Accesso dell'area Internet di Internet Explorer alle origini dati**  
  L'impostazione di questo criterio consente di gestire l'accesso da parte di Internet Explorer a dati appartenenti a un'altra area di sicurezza usando Microsoft XML Parser (MSXML) o ActiveX Data Objects (ADO). Se si abilita l'impostazione di questo criterio, gli utenti potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire il caricamento di una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se non si configura l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067078)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Trascinare contenuto da domini diversi all'interno delle finestre**  
  Questa impostazione di criteri consente di impostare le opzioni per trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Se si abilita questa impostazione e si fa clic su Abilita, gli utenti possono trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione nella finestra di dialogo Opzioni Internet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067079)  
  
  **Impostazione predefinita**: Disabilitato
  
- **Internet Explorer - Avviso di indirizzo di certificato non corrispondente**  
  L'impostazione di questo criterio consente di attivare l'avviso di sicurezza in caso di indirizzi di certificati non corrispondenti. Quando l'impostazione di questo criterio è abilitata, l'utente riceverà un avviso quando visita siti Web HTTP protetti (HTTPS) che contengono certificati emessi per un sito Web con un altro indirizzo. Questo avviso aiuta a prevenire attacchi di spoofing. Se si abilita l'impostazione di questo criterio, l'avviso di mancata corrispondenza negli indirizzi dei certificati verrà sempre visualizzato. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà scegliere se visualizzare o meno l'avviso di mancata corrispondenza negli indirizzi dei certificati usando la pagina Avanzate nel Pannello di controllo Internet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067153)  
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area con restrizioni - Siti con privilegi inferiori**  
  L'impostazione di questo criterio consente di gestire l'esplorazione dell'area da parte di siti Web appartenenti ad aree con privilegi inferiori, ad esempio i siti Internet. Se si abilita l'impostazione di questo criterio, i siti Web appartenenti ad aree con privilegi inferiori possono aprire nuove finestre all'interno dell'area o esplorarla. L'area sarà priva del livello di sicurezza aggiuntivo offerto dalla funzionalità di sicurezza Protezione da elevazione privilegi dell'area. Se si seleziona Chiedi conferma nella casella a discesa, viene visualizzato un avviso che informa l'utente dei potenziali rischi dell'esplorazione. Se si disabilita l'impostazione di questo criterio, un'esplorazione potenzialmente dannosa non sarà consentita. Questa funzionalità di sicurezza di Internet Explorer viene abilitata per l'area, come specificato dall'impostazione del controllo della funzionalità Protezione da elevazione privilegi dell'area. Se non si configura l'impostazione di questo criterio, le esplorazioni potenzialmente dannose non saranno consentite. Questa funzionalità di sicurezza di Internet Explorer viene abilitata per l'area, come specificato dall'impostazione del controllo della funzionalità Protezione da elevazione privilegi dell'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067148)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Richiesta automatica per il download di file**  
  L'impostazione di questo criterio determina se viene visualizzata una richiesta di conferma per i download di file non originati dall'utente. Per i download di file originati dall'utente, verranno visualizzate le apposite finestre di dialogo indipendentemente da questa impostazione. Se si abilita questa impostazione, verrà visualizzata una finestra di dialogo per i tentativi automatici di download di file. Se si disabilita o non si configura questa impostazione, i download di file non originati dall'utente vengono bloccati e verrà visualizzata la barra di notifica anziché la finestra di dialogo per il download di file. Gli utenti potranno quindi fare clic sulla barra di notifica per confermare il download del file.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067150)  
  
  **Impostazione predefinita**: Disabilitato
  
- **Internet Explorer - Area Internet - Componenti basati su .NET Framework**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte di Internet Explorer dei componenti .NET Framework non firmati con Authenticode. Fra questi componenti sono inclusi i controlli gestiti a cui fa riferimento un tag oggetto e gli eseguibili gestiti a cui fa riferimento un collegamento. Se si abilita l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti senza firma. Se si seleziona Chiedi conferma nella casella a discesa, Internet Explorer chiederà all'utente di scegliere se consentire l'esecuzione di componenti gestiti senza firma. Se si disabilita l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti senza firma. Se non si configura l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti senza firma.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067073)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Consentire solo ai domini approvati di usare i controlli ActiveX TDC**  
  Questa impostazione dei criteri controlla se l'utente può eseguire il controllo ActiveX TDC nei siti Web. Se si abilita l'impostazione di questo criterio, il controllo ActiveX TDC non verrà eseguito dai siti Web in quest'area. Se si disabilita l'impostazione di questo criterio, il controllo ActiveX TDC verrà eseguito da tutti i siti Web in quest'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067151)
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area con restrizioni - Finestre aperte da script**  
  L'impostazione di questo criterio consente di gestire le restrizioni nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato. Se si abilita l'impostazione di questo criterio, la funzionalità di sicurezza relativa alle restrizioni per Windows non verrà applicata nell'area. L'area di sicurezza verrà eseguita senza il livello di sicurezza aggiuntivo offerto da questa funzionalità. Se si disabilita l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo. Se non si configura l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067075)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Includere percorso locale nel caricamento di file sul server**  
  L'impostazione di questo criterio consente di specificare se inviare le informazioni sul percorso locale quando l'utente carica un file tramite un modulo HTML. Se le informazioni sul percorso locale vengono inviate, alcune di esse potrebbero essere rese note al server accidentalmente. I file inviati dal desktop di un utente, ad esempio, potrebbero contenere il nome utente come parte del percorso. Se si abilita l'impostazione di questo criterio, le informazioni sul percorso locale verranno inviate quando l'utente carica un file tramite un modulo HTML. Se si disabilita l'impostazione di questo criterio, le informazioni sul percorso verranno rimosse quando l'utente carica un file tramite un modulo HTML. Se non si configura l'impostazione di questo criterio, l'utente potrà scegliere se inviare le informazioni sul percorso quando carica un file tramite un modulo HTML. Per impostazione predefinita, le informazioni sul percorso vengono inviate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067072)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Disabilitare i processi in modalità protetta avanzata**  
  L'impostazione di questo criterio determina se Internet Explorer 11 usa i processi a 64 bit (per maggiore sicurezza) o a 32 bit (per maggiore compatibilità) durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Importante: Alcuni controlli ActiveX e alcune barre degli strumenti potrebbero non essere disponibili quando vengono usati processi a 64 bit. Se si abilita l'impostazione di questo criterio, Internet Explorer 11 userà processi schede a 64 bit durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Se si disabilita l'impostazione di questo criterio, Internet Explorer 11 userà processi schede a 32 bit durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Se non si configura l'impostazione di questo criterio, gli utenti possono attivare o disattivare questa funzionalità tramite le impostazioni di Internet Explorer. Questa funzionalità è disattivata per impostazione predefinita.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067149)  
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Ignorare gli errori di certificato**  
  L'impostazione di questo criterio impedisce all'utente di ignorare gli errori di certificato Secure Sockets Layer/Transport Layer Security (SSL/TLS) che interrompono l'esplorazione in Internet Explorer, ad esempio errori relativi a certificati "scaduti", "revocati" o con "nomi non corrispondenti". Se si abilita l'impostazione di questo criterio, l'utente non può continuare l'esplorazione. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente può scegliere di ignorare gli errori di certificato e continuare l'esplorazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067071)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Caricamento di file XAML**  
  L'impostazione di questo criterio consente di gestire il caricamento di file XAML (Extensible Application Markup Language). XAML è un linguaggio di markup dichiarativo basato su XML usato spesso per la creazione di grafica e interfacce utente avanzate che sfruttano la piattaforma Windows Presentation Foundation. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file XAML vengono caricati automaticamente in Internet Explorer. L'utente non può modificare questo comportamento. Se nella casella a discesa è selezionata Chiedi conferma, prima del caricamento dei file XAML viene chiesta conferma all'utente. Se si disabilita l'impostazione di questo criterio, i file XAML non vengono caricati in Internet Explorer. L'utente non può modificare questo comportamento. Se non si configura l'impostazione di questo criterio, l'utente può decidere se caricare i file XAML in Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067147)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Richiesta automatica per il download di file**  
  L'impostazione di questo criterio determina se viene visualizzata una richiesta di conferma per i download di file non originati dall'utente. Per i download di file originati dall'utente, verranno visualizzate le apposite finestre di dialogo indipendentemente da questa impostazione. Se si abilita questa impostazione, verrà visualizzata una finestra di dialogo per i tentativi automatici di download di file. Se si disabilita o non si configura questa impostazione, i download di file non originati dall'utente vengono bloccati e verrà visualizzata la barra di notifica anziché la finestra di dialogo per il download di file. Gli utenti potranno quindi fare clic sulla barra di notifica per confermare il download del file.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067117)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Avviso di sicurezza per file potenzialmente dannosi**  
  L'impostazione di questo criterio consente di controllare la visualizzazione dell'avviso "Apri file - Avviso di sicurezza" quando l'utente prova ad aprire file eseguibili o altri file potenzialmente non sicuri, ad esempio da una condivisione file Intranet usando Esplora file. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file verranno aperti senza visualizzare l'avviso di sicurezza. Se nella casella a discesa è selezionata Chiedi conferma, prima dell'apertura dei file viene visualizzato un avviso di sicurezza. Se si disabilita l'impostazione di questo criterio, i file non verranno aperti. Se non si configura l'impostazione di questo criterio, l'utente può configurare la modalità di gestione di questi file. Per impostazione predefinita, questi file vengono bloccati nell'area con restrizioni, abilitati nell'area Intranet e del computer locale e impostati su Chiedi conferma nelle aree attendibili e Internet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2066797)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Filtro XSS**  
  Questo criterio consente di specificare se il filtro XSS rileverà e impedirà gli attacchi tramite script da altri siti nei siti Web in quest'area. Se si abilita l'impostazione di questo criterio, il filtro XSS è attivato per i siti in quest'area e prova a bloccare gli attacchi tramite script da altri siti. Se si disabilita l'impostazione di questo criterio, il filtro XSS è disabilitato per i siti in quest'area e Internet Explorer non impedirà gli attacchi tramite script da altri siti.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067053) 
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Fallback in SSL3**  
  L'impostazione di questo criterio consente di bloccare un fallback non sicuro in SSL 3.0. Quando questo criterio è abilitato, Internet Explorer tenterà di connettersi ai siti che usano SSL 3.0 o versione precedente quando non viene stabilita la connessione tramite TLS 1.0 o versione successiva. È consigliabile non consentire il fallback non sicuro per evitare attacchi man-in-the-middle. Questo criterio non influisce sui protocolli di sicurezza abilitati. Se si disabilita questo criterio, vengono usate le impostazioni predefinite di sistema.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067118)  
  
  **Impostazione predefinita**: Nessun sito  

- **Internet Explorer - Supporto della crittografia**  
  Questa impostazione di criteri consente di disattivare il supporto per Transport Layer Security (TLS) 1.0, TLS 1.1, TLS 1.2, Secure Sockets Layer (SSL) 2.0 o SSL 3.0 nel browser. TLS e SSL sono protocolli che consentono di proteggere le comunicazioni tra il browser e il server di destinazione. Quando il browser tenta di configurare una comunicazione protetta con il server di destinazione, il browser e il server negoziano il protocollo e la versione da usare. Il browser e il server tentano di trovare una corrispondenza nel rispettivo elenco di protocolli e versioni supportati e selezionano la corrispondenza preferita. Se si abilita questa impostazione di criteri, il browser negozia o non negozia un tunnel di crittografia usando i metodi di crittografia selezionati nell'elenco a discesa. Se questa impostazione di criteri viene disabilitata o non viene configurata, l'utente può selezionare il metodo di crittografia supportato dal browser.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Impostazione predefinita**: 2 elementi: TLS v1.1 e TLS v1.2  
  *Selezionare la freccia rivolta verso il basso per visualizzare le opzioni che è possibile selezionare per questa impostazione.*
  
- **Internet Explorer - Area Internet bloccata - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: In Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067059)  
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area con restrizioni - Avviare programmi e file in un IFRAME**  
  L'impostazione di questo criterio consente di gestire l'esecuzione di applicazioni e il download di file da un riferimento IFRAME nel codice HTML delle pagine appartenenti all'area. Se si abilita l'impostazione di questo criterio, è possibile eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area senza intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di applicazioni e il download di file da IFRAME nelle pagine dell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non possono eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area. Se non si configura l'impostazione di questo criterio, gli utenti non possono eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067061)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Ignora avvisi di SmartScreen relativi a file non comuni**  
  L'impostazione di questo criterio determina se l'utente può ignorare gli avvisi del filtro SmartScreen. Il filtro SmartScreen segnala i file eseguibili che gli utenti di Internet Explorer non scaricano spesso da Internet. Se si abilita l'impostazione di questo criterio, gli avvisi del filtro SmartScreen bloccheranno l'utente. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà ignorare gli avvisi del filtro SmartScreen.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067068)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Blocco popup**  
  L'impostazione di questo criterio consente di gestire la visualizzazione di finestre popup indesiderate. Le finestre popup visualizzate quando l'utente finale fa clic su un collegamento non vengono bloccate. Se si abilita l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup indesiderate. Se si disabilita l'impostazione di questo criterio, non viene impedita la visualizzazione delle finestre popup. Se non si configura l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067069)  
  
  **Impostazione predefinita**: Abilitare  
  
- **Gestione MIME coerente dei processi di Internet Explorer**  
  Internet Explorer contiene comportamenti binari dinamici, ovvero componenti che incapsulano funzionalità specifiche per gli elementi HTML a cui sono associati. L'impostazione di questo criterio determina se l'impostazione Restrizione di sicurezza comportamenti binari è consentita o meno. Se si abilita l'impostazione di questo criterio, i comportamenti binari non saranno consentiti per i processi di Esplora file e Internet Explorer. Se si disabilita l'impostazione di questo criterio, i comportamenti binari saranno consentiti per i processi di Esplora file e Internet Explorer. Se non si configura l'impostazione di questo criterio, i comportamenti binari non saranno consentiti per i processi di Esplora file e Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Autorizzazioni Java per area con restrizioni**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Impostazione predefinita**: Disabilitare Java  
    
  
- **Internet Explorer - Controlli Active X in modalità protetta**  
  Questa impostazione di criteri impedisce l'esecuzione dei controlli ActiveX in modalità protetta quando è abilitata la modalità protetta avanzata. Se un utente ha un controllo ActiveX installato non compatibile con la modalità protetta avanzata e un sito Web prova a caricare il controllo, Internet Explorer visualizza una notifica e offre la possibilità all'utente di eseguire il sito Web in modalità protetta normale. Questa impostazione di criteri disabilita la notifica e impone l'esecuzione di tutti i siti Web in modalità protetta avanzata. La modalità protetta avanzata offre protezione aggiuntiva contro i siti Web dannosi usando processi a 64 bit nelle versioni di Windows a 64 bit. Per i computer che eseguono almeno Windows 8, la modalità protetta avanzata limita anche i percorsi leggibili da Internet Explorer nel Registro di sistema e nel file system. Quando è abilitata la modalità protetta avanzata e un utente visita un sito Web che prova a caricare un controllo ActiveX non compatibile con la modalità protetta avanzata, Internet Explorer visualizza una notifica e offre la possibilità all'utente di disabilitare la modalità protetta avanzata per tale sito Web specifico. Se si abilita questa impostazione, Internet Explorer non offre all'utente la possibilità di disabilitare la modalità protetta avanzata. Tutti i siti Web in modalità protetta vengono eseguiti in modalità protetta avanzata. Se l'impostazione viene disabilitata o non configurata, Internet Explorer visualizza una notifica per gli utenti e offre la possibilità di eseguire i siti Web con controlli ActiveX non compatibili in modalità protetta normale.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067145)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Caricamento di file XAML**  
  L'impostazione di questo criterio consente di gestire il caricamento di file XAML (Extensible Application Markup Language). XAML è un linguaggio di markup dichiarativo basato su XML usato spesso per la creazione di grafica e interfacce utente avanzate che sfruttano la piattaforma Windows Presentation Foundation. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file XAML vengono caricati automaticamente in Internet Explorer. L'utente non può modificare questo comportamento. Se nella casella a discesa è selezionata Chiedi conferma, prima del caricamento dei file XAML viene chiesta conferma all'utente. Se si disabilita l'impostazione di questo criterio, i file XAML non vengono caricati in Internet Explorer. L'utente non può modificare questo comportamento. Se non si configura l'impostazione di questo criterio, l'utente può decidere se caricare i file XAML in Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067070)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Processi - Restrizioni di sicurezza finestre controllate da script**  
  Internet Explorer consente agli script di aprire, ridimensionare e riposizionare a livello di programmazione finestre di vari tipi. La funzionalità di sicurezza relativa alle restrizioni per le finestre consente di impostare restrizioni per le finestre popup e di impedire agli script di visualizzare finestre in cui la barra del titolo e la barra di stato non sono visibili all'utente o coprono la barra del titolo e la barra di stato di altre finestre. Se si abilita l'impostazione di questo criterio, vengono impostate restrizioni sulle finestre controllate da script per tutti i processi. Se si disabilita o non si configura l'impostazione di questo criterio, non viene impostata alcuna restrizione per le finestre controllate da script.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067146)  
  
  **Impostazione predefinita**: Abilitato   
  
- **Internet Explorer - Area con restrizioni - Eseguire controlli ActiveX e plug-in**  
  L'impostazione di questo criterio consente di stabilire se possono essere eseguiti controlli ActiveX e plug-in nelle pagine dell'area specificata. Se si abilita l'impostazione di questo criterio, controlli e plug-in possono essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma dalla casella a discesa, viene richiesto agli utenti di scegliere se consentire l'esecuzione di controlli e plug-in. Se si disabilita l'impostazione di questo criterio, l'esecuzione di controlli e plug-in non sarà consentita. Se non si configura l'impostazione di questo criterio, l'esecuzione di controlli e plug-in non è consentita.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067114) 
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Eseguire script di controlli ActiveX contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire l'interazione con uno script da parte di un controllo ActiveX contrassegnato come sicuro. Se si abilita l'impostazione di questo criterio, l'interazione con gli script può avvenire automaticamente senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'interazione con gli script. Se si disabilita l'impostazione di questo criterio, l'interazione con gli script non è consentita. Se non si configura l'impostazione di questo criterio, l'interazione con gli script non è consentita.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067062)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Opzioni di accesso**  
  L'impostazione di questo criterio consente di gestire le impostazioni per le opzioni di accesso. Se si abilita l'impostazione di questo criterio, è possibile scegliere tra le opzioni di accesso seguenti. 
  - *Anonimo*: usare l'accesso anonimo per disabilitare l'autenticazione HTTP e usare l'account Guest solo per il protocollo Common Internet File System (CIFS). 
  - *Chiedi conferma*: usare la richiesta di nome utente e password per richiedere l'immissione degli ID utente e delle password da parte degli utenti. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. 
  - *Accesso automatico solo nell'area Intranet* - Usare questa opzione per richiedere agli utenti ID e password in altre aree. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. 
  - *Accesso automatico con nome utente e password correnti* - Usare questa opzione per provare a eseguire l'accesso tramite Windows NT Challenge Response (noto anche come autenticazione NTLM). Se il server supporta Windows NT Challenge Response, l'accesso utilizza il nome utente e la password validi nella rete. Se il server non supporta Windows NT Challenge Response, viene richiesto all'utente di specificare il nome utente e la password. 

  Se si disabilita l'impostazione di questo criterio, viene impostata l'opzione *Accesso automatico solo nell'area Intranet*. Se non si configura l'impostazione di questo criterio, viene impostata l'opzione di accesso *Chiedi conferma* per nome utente e password.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067110)  
  
  **Impostazione predefinita**: Anonima  
  
- **Internet Explorer - Area attendibile - Inizializzare ed eseguire script di controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067137)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Verificare la revoca certificati del server**  
  L'impostazione di questo criterio consente di gestire la verifica da parte di Internet Explorer dello stato di revoca dei certificati del server. I certificati vengono revocati quando sono compromessi oppure non sono più validi. Questa opzione protegge gli utenti dall'invio di dati riservati a un sito che potrebbe essere fraudolento o non protetto. Se si abilita l'impostazione di questo criterio, Internet Explorer verificherà se i certificati del server sono stati revocati. Se si disabilita l'impostazione di questo criterio, Internet Explorer non verificherà se i certificati del server sono stati revocati. Se non si configura l'impostazione di questo criterio, Internet Explorer non verificherà se i certificati del server sono stati revocati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067046)  
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area Internet - Siti con privilegi inferiori**  
  L'impostazione di questo criterio consente di gestire l'esplorazione dell'area da parte di siti Web appartenenti ad aree con privilegi inferiori, ad esempio l'area Siti con restrizioni. Se si abilita l'impostazione di questo criterio, i siti Web appartenenti ad aree con privilegi inferiori possono aprire nuove finestre all'interno dell'area o esplorarla. L'area sarà priva del livello di sicurezza aggiuntivo offerto dalla funzionalità di sicurezza Protezione da elevazione privilegi dell'area. Se si seleziona Chiedi conferma nella casella a discesa, viene visualizzato un avviso che informa l'utente dei potenziali rischi dell'esplorazione. Se si disabilita l'impostazione di questo criterio, le esplorazioni potenzialmente dannose non saranno consentite. Questa funzionalità di sicurezza di Internet Explorer viene abilitata per l'area, come specificato dall'impostazione del controllo della funzionalità Protezione da elevazione privilegi dell'area. Se non si configura l'impostazione di questo criterio, i siti Web appartenenti ad aree con privilegi inferiori possono aprire nuove finestre all'interno dell'area o esplorarla.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067109)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Download di file**  
  L'impostazione di questo criterio consente di determinare se i download dei file dall'area sono consentiti. Questa opzione viene determinata dall'area della pagina contenente il collegamento che provoca il download e non dall'area da cui viene inviato il file. Se si abilita l'impostazione di questo criterio, è possibile scaricare file dall'area. Se si disabilita l'impostazione di questo criterio, non è possibile scaricare file dall'area. Se non si configura l'impostazione di questo criterio, non è possibile scaricare file dall'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067038)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Eseguire componenti basati su .NET Framework firmati con Authenticode**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte di Internet Explorer di componenti .NET Framework con firma Authenticode. Fra questi componenti sono inclusi i controlli gestiti a cui fa riferimento un tag oggetto e gli eseguibili gestiti a cui fa riferimento un collegamento. Se si abilita l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti con firma. Se si seleziona Chiedi conferma nella casella a discesa, Internet Explorer chiederà all'utente di scegliere se consentire l'esecuzione di componenti gestiti con firma. Se si disabilita l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati. Se non si configura l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067033)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Impedire l'installazione per singolo utente dei controlli ActiveX**  
  L'impostazione di questo criterio consente di impedire l'installazione per singolo utente dei controlli ActiveX. Se si abilita l'impostazione di questo criterio, i controlli ActiveX non possono essere installati per singolo utente. Se si disabilita o non si configura l'impostazione di questo criterio, i controlli ActiveX possono essere installati per singolo utente.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067058)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Impedire la gestione del filtro SmartScreen**  
  L'impostazione di questo criterio impedisce all'utente di gestire il filtro SmartScreen, che avvisa l'utente se il sito Web visitato è noto per aver eseguito tentativi fraudolenti di raccogliere informazioni personali attraverso il "phishing" o per contenere malware. Se si abilita questa impostazione, all'utente non viene richiesto di attivare il filtro SmartScreen. Tutti gli indirizzi di siti Web non inclusi nell'elenco di quelli consentiti vengono inviati automaticamente a Microsoft senza richiedere conferma all'utente. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente può scegliere se attivare il filtro SmartScreen alla prima esecuzione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067135)  
  
  **Impostazione predefinita**: Abilitare  
  
- **Internet Explorer - Processi - Funzionalità di protezione analisi MIME**  
  L'impostazione di questo criterio determina se l'analisi MIME di Internet Explorer impedisce l'innalzamento di livello di un file di un certo tipo a un tipo di file più pericoloso. Se si abilita l'impostazione di questo criterio, l'analisi MIME non innalzerà mai di livello un file di un certo tipo a un tipo di file più pericoloso. Se si disabilita l'impostazione di questo criterio, i processi di Internet Explorer consentiranno all'analisi MIME di innalzare di livello un file di un certo tipo a un tipo di file più pericoloso. Se non si configura l'impostazione di questo criterio, l'analisi MIME non innalzerà mai di livello un file di un certo tipo a un tipo di file più pericoloso.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067124)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Download di controlli Active X firmati**  
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX firmati da una pagina appartenente all'area. Se si abilita l'impostazione di questo criterio, i controlli firmati possono essere scaricati senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente. Se si disabilita l'impostazione di questo criterio, i controlli firmati non possono essere scaricati. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067120) 
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Completamento automatico**  
  La funzionalità Completamento automatico è in grado di ricordare e suggerire nomi utente e password nei moduli. Se si abilita questa impostazione, l'utente non può modificare le opzioni "Nome utente e password sui moduli" e "Richiedi salvataggio password". La funzionalità Completamento automatico per l'immissione di nomi utente e password nei moduli viene attivata. L'amministratore deve scegliere se selezionare l'opzione "Richiedi salvataggio password". Se si disabilita questa impostazione, l'utente non può modificare le opzioni "Nome utente e password sui moduli" e "Richiedi salvataggio password". La funzionalità Completamento automatico per l'immissione di nomi utente e password nei moduli viene disabilitata. L'utente inoltre non può scegliere di richiedere il salvataggio delle password. Se non si configura questa impostazione, l'utente può scegliere di attivare Completamento automatico per nomi utente e password nei moduli e l'opzione per richiedere il salvataggio delle password. Per accedere a questa opzione è necessario visualizzare la finestra di dialogo Opzioni Internet, fare clic sulla scheda Contenuto e quindi sul pulsante Impostazioni.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067122)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Autorizzare l'esecuzione di VBscript**  
  L'impostazione di questo criterio consente di decidere se VBScript può essere eseguito nelle pagine in zone specifiche di Internet Explorer. Le opzioni includono: 
  - *Abilita*: VBScript viene eseguito nelle pagine in zone specifiche, senza nessuna interazione. 
  - *Chiedi conferma*: viene richiesto ai dipendenti se consentono l'esecuzione di VBScript nella zona. 
  - *Disabilita*: viene impedita l'esecuzione di VBScript nella zona. Se si disabilita o non si configura l'impostazione di questo criterio, VBScript viene eseguito senza alcuna interazione nella zona specificata.    

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067119)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Consentire solo ai domini approvati di usare i controlli ActiveX TDC**  
  Questa impostazione dei criteri controlla se l'utente può eseguire il controllo ActiveX TDC nei siti Web. Se si abilita l'impostazione di questo criterio, il controllo ActiveX TDC non verrà eseguito dai siti Web in quest'area. Se si disabilita l'impostazione di questo criterio, il controllo ActiveX TDC verrà eseguito da tutti i siti Web in quest'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067032)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Non eseguire antimalware sui controlli ActiveX per l'area attendibile**  
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067115)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area computer locale - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione media.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067113)  
  
  **Impostazione predefinita**: Disabilita Java 
  
- **Internet Explorer - Area intranet - Non eseguire programmi antimalware su controlli ActiveX**  
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067138)  
  
  **Impostazione predefinita**: Disabilitato  

- **Internet Explorer - Area con restrizioni - Scriptlet**  
  L'impostazione di questo criterio consente di specificare se l'utente può eseguire scriptlet. Se si abilita l'impostazione di questo criterio, l'utente potrà eseguire gli scriptlet. Se si disabilita l'impostazione di questo criterio, l'utente non potrà eseguire gli scriptlet. Se non si configura l'impostazione di questo criterio, l'utente potrà abilitare o disabilitare gli scriptlet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067112)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Processi - Barra di notifica**  
  L'impostazione di questo criterio consente di gestire la visualizzazione della barra di notifica per i processi di Internet Explorer quando le installazioni di file o di codice sono soggette a restrizioni. Per impostazione predefinita, la barra di notifica è visualizzata per i processi di Internet Explorer. Se si abilita l'impostazione di questo criterio, la barra di notifica viene visualizzata per i processi di Internet Explorer. Se si disabilita l'impostazione di questo criterio, la barra di notifica non verrà visualizzata per i processi di Internet Explorer. Se non si configura l'impostazione di questo criterio, la barra di notifica non viene visualizzata per i processi di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067139)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area Internet - Scaricare controlli ActiveX firmati**  
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX firmati da una pagina appartenente all'area. Se si abilita l'impostazione di questo criterio, i controlli firmati possono essere scaricati senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente. Se si disabilita l'impostazione di questo criterio, i controlli firmati non possono essere scaricati. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067064)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: In Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067034)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Rimuovere il pulsante Esegui questa volta per i controlli ActiveX obsoleti**  
  L'impostazione di questo criterio consente di evitare la visualizzazione del pulsante "Esegui questa volta" e l'esecuzione di specifici controlli ActiveX obsoleti in Internet Explorer. Se si abilita l'impostazione di questo criterio, gli utenti non vedranno il pulsante "Esegui questa volta" nel messaggio di avviso visualizzato quando Internet Explorer blocca un controllo ActiveX obsoleto. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti vedranno il pulsante "Esegui questa volta" nel messaggio di avviso visualizzato quando Internet Explorer blocca un controllo ActiveX obsoleto. Facendo clic su questo pulsante l'utente può eseguire il controllo ActiveX obsoleto una volta. Per altre informazioni, vedere l'argomento relativo ai controlli ActiveX obsoleti nella libreria TechNet di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067123)  
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area Internet - Avviare programmi e file in un IFRAME**  
  L'impostazione di questo criterio consente di gestire l'esecuzione di applicazioni e il download di file da un riferimento IFRAME nel codice HTML delle pagine appartenenti all'area. Se si abilita l'impostazione di questo criterio, è possibile eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area senza intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di applicazioni e il download di file da IFRAME nelle pagine dell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non possono eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire l'esecuzione di applicazioni e il download di file da IFRAME presenti nelle pagine dell'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067020)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area con restrizioni - Esplorare finestre e frame in domini diversi**  
  Questa impostazione di criteri consente di impostare le opzioni per trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Abilita, gli utenti possono trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: In Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067047)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area attendibile bloccata - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067142)  
  
  
  **Impostazione predefinita**: Disabilitare Java 
  
- **Internet Explorer - Verificare le firme nei programmi scaricati**  
  L'impostazione di questo criterio consente di gestire la verifica da parte di Internet Explorer delle firme digitali, che ha lo scopo di identificare l'autore di software firmato e di controllare che tale software non sia stato modificato o manomesso, nei computer degli utenti prima del download di programmi eseguibili. Se si abilita l'impostazione di questo criterio, Internet Explorer verificherà le firme digitali dei programmi eseguibili e visualizzerà le relative identità prima del download nei computer degli utenti. Se si disabilita l'impostazione di questo criterio, Internet Explorer non verificherà le firme digitali dei programmi eseguibili né visualizzerà le relative identità prima del download nei computer degli utenti. Se non si configura l'impostazione di questo criterio, Internet Explorer non verificherà le firme digitali dei programmi eseguibili né visualizzerà le relative identità prima del download nei computer degli utenti.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067051)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Eseguire script di controlli WebBrowser**  
  L'impostazione di questo criterio determina se una pagina può gestire i controlli WebBrowser incorporati tramite uno script. Se si abilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser è consentito. Se si disabilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser non è consentito. Se non si configura l'impostazione di questo criterio, l'utente può abilitare o disabilitare l'accesso tramite script ai controlli WebBrowser. Per impostazione predefinita, l'accesso tramite script ai controlli WebBrowser è consentito solo nelle aree Intranet e del computer locale.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067098)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Filtro XSS**  
  Questo criterio consente di specificare se il filtro XSS rileverà e impedirà gli attacchi tramite script da altri siti nei siti Web in quest'area. Se si abilita l'impostazione di questo criterio, il filtro XSS è attivato per i siti in quest'area e prova a bloccare gli attacchi tramite script da altri siti. Se si disabilita l'impostazione di questo criterio, il filtro XSS è disabilitato per i siti in quest'area e Internet Explorer non impedirà gli attacchi tramite script da altri siti.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067178)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Comportamenti file binari e script**  
  L'impostazione di questo criterio consente di gestire comportamenti binari dinamici e di script, ovvero componenti che incapsulano funzionalità specifiche per gli elementi HTML a cui sono stati associati. Se si abilita l'impostazione di questo criterio, i comportamenti binari e di script sono disponibili. Se si seleziona Autorizzazione amministratore nella casella a discesa sono disponibili solo i comportamenti specificati nell'elenco Comportamenti autorizzati da amministratori del criterio Restrizione di sicurezza comportamenti binari. Se si disabilita l'impostazione di questo criterio, i comportamenti binari e di script non sono disponibili, a meno che nelle applicazioni non sia stato implementato un gestore della sicurezza personalizzato. Se non si configura l'impostazione di questo criterio, i comportamenti binari e di script non sono disponibili, a meno che nelle applicazioni non sia stato implementato un gestore della sicurezza personalizzato.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067224)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Verifica delle impostazioni di sicurezza**  
  L'impostazione di questo criterio consente di disattivare la funzionalità di verifica delle impostazioni di sicurezza che controlla le impostazioni di sicurezza di Internet Explorer per determinare quando comportano rischi per Internet Explorer. Se si abilita l'impostazione di questo criterio, la funzionalità viene disattivata. Se si disabilita o non si configura l'impostazione di questo criterio, la funzionalità viene attivata.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067182)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area Internet - Avviso di sicurezza per file potenzialmente dannosi**  
  L'impostazione di questo criterio consente di controllare la visualizzazione dell'avviso "Apri file - Avviso di sicurezza" quando l'utente prova ad aprire file eseguibili o altri file potenzialmente non sicuri, ad esempio da una condivisione file Intranet usando Esplora file. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file verranno aperti senza visualizzare l'avviso di sicurezza. Se nella casella a discesa è selezionata Chiedi conferma, prima dell'apertura dei file viene visualizzato un avviso di sicurezza. Se si disabilita l'impostazione di questo criterio, i file non verranno aperti. Se non si configura l'impostazione di questo criterio, l'utente può configurare la modalità di gestione di questi file. Per impostazione predefinita, questi file vengono bloccati nell'area con restrizioni, abilitati nell'area Intranet e del computer locale e impostati su Chiedi conferma nelle aree attendibili e Internet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067204)  
  
  **Impostazione predefinita**: Prompt  
  
- **Internet Explorer - Area Intranet - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione media.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067206)  
  
  **Impostazione predefinita**: Protezione alta 
  
- **Internet Explorer - Bloccare i controlli ActiveX obsoleti**   
  L'impostazione di questo criterio determina se Internet Explorer blocca specifici controlli ActiveX obsoleti. I controlli ActiveX obsoleti non vengono mai bloccati nell'area Intranet. Se si abilita l'impostazione di questo criterio, Internet Explorer sospende il blocco dei controlli ActiveX obsoleti. Se si disabilita o non si configura l'impostazione di questo criterio, Internet Explorer continua a bloccare specifici controlli ActiveX obsoleti. Per altre informazioni, vedere l'argomento relativo ai controlli ActiveX obsoleti nella libreria TechNet di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067203)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Blocco popup**  
  L'impostazione di questo criterio consente di gestire la visualizzazione di finestre popup indesiderate. Le finestre popup visualizzate quando l'utente finale fa clic su un collegamento non vengono bloccate. Se si abilita l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup indesiderate. Se si disabilita l'impostazione di questo criterio, non viene impedita la visualizzazione delle finestre popup. Se non si configura l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067180)  
  
  **Impostazione predefinita**: Abilitare  
  
- **Internet Explorer - Processi - Limitare il protocollo di sicurezza MK**  
  L'impostazione del criterio Limitazione protocollo di sicurezza MK riduce la superficie di attacco in quanto disabilita il protocollo MK. Le risorse ospitate nel protocollo MK non funzioneranno. Se si abilita l'impostazione di questo criterio, il protocollo MK viene disabilitato per Esplora file e Internet Explorer e le risorse ospitate nel protocollo MK non funzioneranno. Se si disabilita l'impostazione di questo criterio, le applicazioni possono usare l'API del protocollo MK. Le risorse ospitate nel protocollo MK funzioneranno per i processi di Esplora file e Internet Explorer. Se non si configura l'impostazione di questo criterio, il protocollo MK viene disabilitato per Esplora file e Internet Explorer e le risorse ospitate nel protocollo MK non funzioneranno.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067179)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area attendibile - Autorizzazioni Java**   
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione bassa.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067200)  
  
  **Impostazione predefinita**: Protezione alta  
  
- **Internet Explorer - Area con restrizioni - Eseguire script delle applet Java**  
  L'impostazione di questo criterio consente di gestire l'accessibilità delle applet da parte degli script all'interno dell'area. Se si abilita l'impostazione di questo criterio, l'accesso degli script alle applet può avvenire automaticamente senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'accesso degli script alle applet. Se si disabilita l'impostazione di questo criterio, l'accesso degli script alle applet non viene consentito. Se non si configura l'impostazione di questo criterio, l'accesso degli script alle applet non viene consentito.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067202)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Bloccare le autorizzazioni Java**   
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067181)  
  
  **Impostazione predefinita**: Disabilitare Java 
  
- **Internet Explorer - Area Internet - Consentire solo ai domini approvati di usare i controlli ActiveX**   
  L'impostazione di questo criterio consente di specificare se agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX su siti Web diversi da quello che ha installato il controllo ActiveX. Se si abilita l'impostazione di questo criterio, agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX da siti Web in quest'area. L'utente può scegliere di autorizzare l'esecuzione del controllo dal sito corrente o da tutti i siti. Se si disabilita l'impostazione di questo criterio, l'utente non vede il prompt di ActiveX per ogni sito e i controlli ActiveX possono essere eseguiti da tutti i siti in quest'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067091)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Includere tutti i percorsi di rete**  
  Internet Explorer - Includere tutti i percorsi di rete.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067090)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Modalità protetta**  
  L'impostazione di questo criterio consente di attivare la modalità protetta. La modalità protetta consente di proteggere Internet Explorer da attacchi correlati ai rischi di sicurezza attraverso una riduzione delle posizioni in cui Internet Explorer può scrivere all'interno del Registro di sistema e del file system. Se si abilita l'impostazione di questo criterio, la modalità protetta viene attivata. L'utente non può disattivare la modalità protetta. Se si disabilita l'impostazione di questo criterio, la modalità protetta viene disattivata. L'utente non può attivare la modalità protetta. Se non si configura l'impostazione di questo criterio, l'utente può attivare o disattivare la modalità protetta.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067171)  
  
  **Impostazione predefinita**: Abilitare 
  
- **Internet Explorer - Area Internet - Inizializzare ed eseguire script controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area con restrizioni - Blocco SmartScreen**   
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: In Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067092)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Rilevamento degli arresti anomali**  
  L'impostazione di questo criterio consente di gestire la funzionalità di rilevamento degli arresti anomali di Gestione componenti aggiuntivi. Se si abilita l'impostazione di questo criterio, gli arresti anomali che si verificano in Internet Explorer determineranno le operazioni previste in Windows XP Professional Service Pack 1 e versioni precedenti, ovvero la chiamata di Segnalazione errori Windows. Tutte le impostazioni del criterio Segnalazione errori Windows continuano a essere applicate. Se si disabilita o non si configura l'impostazione di questo criterio, la funzionalità di rilevamento degli arresti anomali per la gestione dei componenti aggiuntivi viene abilitata.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067094)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione alta.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067174)  
  
  **Impostazione predefinita**: Disabilitare Java  
  
- **Internet Explorer - Area con restrizioni - Esecuzione di script attiva**  
  L'impostazione di questo criterio consente di gestire l'esecuzione di codice script nelle pagine appartenenti all'area. Se si abilita l'impostazione di questo criterio, il codice script nelle pagine dell'area può essere eseguito automaticamente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di codice script nelle pagine dell'area. Se si disabilita l'impostazione di questo criterio, viene impedita l'esecuzione di codice script nelle pagine dell'area. Se non si configura l'impostazione di questo criterio, viene impedita l'esecuzione di codice script nelle pagine dell'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067172)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Opzioni di accesso**  
  L'impostazione di questo criterio consente di gestire le impostazioni per le opzioni di accesso. Se si abilita l'impostazione di questo criterio, è possibile scegliere tra le opzioni di accesso seguenti. Accesso anonimo consente di disabilitare l'autenticazione HTTP e di usare l'account Guest solo per il protocollo Common Internet File System (CIFS). Richiedi nome utente e password consente di richiedere l'immissione degli ID utente e delle password da parte degli utenti. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. Accesso automatico solo nell'area Intranet consente di richiedere l'immissione degli ID utente e delle password da parte degli utenti in altre aree. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. Accesso automatico con nome utente e password correnti consente di provare a eseguire l'accesso tramite Windows NT Challenge Response, noto anche come autenticazione NTLM. Se il server supporta Windows NT Challenge Response, l'accesso utilizza il nome utente e la password validi nella rete. Se il server non supporta Windows NT Challenge Response, viene richiesto all'utente di specificare il nome utente e la password. Se si disabilita l'impostazione di questo criterio, viene impostata l'opzione Accesso automatico solo nell'area Intranet. Se si disabilita l'impostazione di questo criterio, viene impostata l'opzione Accesso automatico solo nell'area Intranet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067194)  
  
  **Impostazione predefinita**: Prompt  
  
- **Internet Explorer - Area con restrizioni - Autorizzare l'esecuzione di VBscript**   
  L'impostazione di questo criterio consente di stabilire se possono essere eseguiti VBScript nelle pagine dell'area specificata in Internet Explorer. Se è stato selezionato Abilita nella casella a discesa, VBScript viene eseguito senza richiedere l'intervento dell'utente. Se è stato selezionato Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di VBScript. Se è stato selezionato Disabilita nella casella a discesa, viene impedita l'esecuzione di VBScript. Se si disabilita o non si configura l'impostazione di questo criterio, viene impedita l'esecuzione di VBScript.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Trascinare contenuto da domini diversi tra finestre**  
  Questa impostazione di criteri consente di impostare le opzioni per trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Abilita, gli utenti possono trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067093)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Intranet - Inizializzare ed eseguire script di controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067175)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Scaricare allegati**  
  L'impostazione di questo criterio impedisce all'utente di scaricare file allegati da un feed nel computer dell'utente. Se si abilita l'impostazione di questo criterio, l'utente non potrà impostare il modulo di sincronizzazione dei feed per scaricare un allegato tramite la pagina delle proprietà Feed. Gli sviluppatori non possono modificare l'impostazione del download usando le interfacce API per i feed. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà impostare il modulo di sincronizzazione dei feed per scaricare un allegato tramite la pagina delle proprietà Feed. Gli sviluppatori possono modificare l'impostazione del download usando le interfacce API per i feed.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067245)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Download di controlli Active X senza firma**  
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX senza firma dall'area. Il codice di questo tipo può essere dannoso, soprattutto se proviene da un'area non attendibile. Se si abilita l'impostazione di questo criterio, i controlli non firmati potranno essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione del controllo non firmato. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati. Se non si configura l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067177)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Trascinare contenuto da domini diversi all'interno di finestre**  
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX non firmati dall'area. Il codice di questo tipo può essere dannoso, soprattutto se proviene da un'area non attendibile. Se si abilita l'impostazione di questo criterio, i controlli non firmati potranno essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione del controllo non firmato. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati. Se non si configura l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067095)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Processi - Limitare l'installazione di ActiveX**   
  L'impostazione di questo criterio consente alle applicazioni che ospitano il Controllo Web Browser di bloccare la richiesta di conferma automatica dell'installazione di controlli ActiveX. Se si abilita l'impostazione di questo criterio, il Controllo Web Browser bloccherà la richiesta di conferma automatica dell'installazione di controlli ActiveX per tutti i processi. Se si disabilita o non si configura l'impostazione di questo criterio, il controllo WebBrowser non bloccherà la richiesta di conferma automatica dell'installazione di controlli ActiveX per tutti i processi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067250)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Scriptlet per l'area Internet**  
  L'impostazione di questo criterio consente di specificare se l'utente può eseguire scriptlet. Se si abilita l'impostazione di questo criterio, l'utente potrà eseguire gli scriptlet. Se si disabilita l'impostazione di questo criterio, l'utente non potrà eseguire gli scriptlet. Se non si configura l'impostazione di questo criterio, l'utente potrà abilitare o disabilitare gli scriptlet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067176)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Trascinare o copiare e incollare file**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte degli utenti di operazioni di trascinamento o di copia e incolla di file da un'origine appartenente all'area. Se si abilita l'impostazione di questo criterio, gli utenti potranno automaticamente trascinare o copiare e incollare file dall'area. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire il trascinamento o la copia di file dall'area. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno trascinare o copiare e incollare file dall'area. Se non si configura l'impostazione di questo criterio, agli utenti verrà chiesto di scegliere se consentire il trascinamento o la copia di file dall'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067096)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Software - Firma non valida**  
  L'impostazione di questo criterio consente di gestire l'installazione o l'esecuzione di software, ad esempio controlli ActiveX e download di file, anche nel caso in cui la firma non sia valida. Una firma non valida potrebbe indicare un tentativo di manomissione del file. Se si abilita l'impostazione di questo criterio, prima dell'installazione o dell'esecuzione di file con una firma non valida viene visualizzata una richiesta di conferma. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire né installare file con una firma non valida. Se non si configura l'impostazione di questo criterio, gli utenti potranno scegliere di eseguire o installare file con una firma non valida.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067201)
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Copiare e incollare tramite script**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte degli script di operazioni con gli Appunti, ad esempio operazioni di taglia, copia e incolla, in un'area specificata. Se si abilita l'impostazione di questo criterio, gli script potranno eseguire operazioni con gli Appunti. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire l'esecuzione di operazioni con gli Appunti. Se si disabilita l'impostazione di questo criterio, gli script non potranno eseguire operazioni con gli Appunti. Se non si configura l'impostazione di questo criterio, gli script non potranno eseguire operazioni con gli Appunti.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067165)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Trascinare contenuto da domini diversi tra finestre**  
  Questa impostazione di criteri consente di impostare le opzioni per trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Abilita, gli utenti possono trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Aggiunta di siti da parte degli utenti**  
  Impedisce agli utenti di aggiungere o eliminare siti nelle aree di sicurezza. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, le impostazioni di gestione dei siti per le aree di sicurezza verranno disabilitate. (Per visualizzare le impostazioni di gestione dei siti per le aree di sicurezza, nella finestra di dialogo Opzioni Internet fare clic sulla scheda Sicurezza e quindi sul pulsante Siti). Se si disabilita o non si configura questo criterio, gli utenti potranno aggiungere o eliminare siti Web nelle aree Siti attendibili e Siti con restrizioni nonché modificare le impostazioni relative all'area Intranet locale. Questo criterio impedisce agli utenti di modificare le impostazioni di gestione dei siti per le aree di sicurezza configurate dall'amministratore. Nota: Il criterio "Disabilita la scheda Sicurezza", disponibile in Configurazione utente\Modelli amministrativi\Componenti di Windows\Internet Explorer\Pannello di controllo Internet, che rimuove la scheda Sicurezza dall'interfaccia, ha priorità rispetto al criterio appena descritto. Se il criterio "Disabilita la scheda Programmi" è abilitato, questo criterio verrà ignorato. Vedere anche il criterio "Aree di sicurezza: Usare solo le impostazioni del computer".  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067167)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Finestre aperte da script**  
  L'impostazione di questo criterio consente di gestire le restrizioni nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato. Se si abilita l'impostazione di questo criterio, la funzionalità di sicurezza relativa alle restrizioni per Windows non verrà applicata nell'area. L'area di sicurezza verrà eseguita senza il livello di sicurezza aggiuntivo offerto da questa funzionalità. Se si disabilita l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo. Se non si configura l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067088)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Aree di sicurezza - Usare solo le impostazioni del computer**  
  Applica le informazioni relative alle aree di sicurezza per tutti gli utenti di uno stesso computer. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, le modifiche apportate da un utente a un'area di sicurezza verranno applicate a tutti gli utenti del computer. Se si disabilita o non si configura questo criterio, gli utenti di uno stesso computer potranno configurare impostazioni personalizzate per le aree di sicurezza. Usare questo criterio per applicare impostazioni uniformi per le aree di sicurezza in uno stesso computer e per impedire che le impostazioni cambino da un utente all'altro. Vedere anche il criterio "Aree di sicurezza: non consentire agli utenti di cambiare i criteri".  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067086)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area computer locale bloccata - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067253) 
  
  **Impostazione predefinita**: Disabilitare Java 
  
- **Internet Explorer - Area con restrizioni - Non eseguire programmi antimalware su controlli ActiveX**   
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067089)
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Eseguire componenti basati su .NET Framework firmati con Authenticode**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte di Internet Explorer dei componenti .NET Framework firmati con Authenticode. Fra questi componenti sono inclusi i controlli gestiti a cui fa riferimento un tag oggetto e gli eseguibili gestiti a cui fa riferimento un collegamento. Se si abilita l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti con firma. Se si seleziona Chiedi conferma nella casella a discesa, Internet Explorer chiederà all'utente di scegliere se consentire l'esecuzione di componenti gestiti con firma. Se si disabilita l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati. Se non si configura l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067169)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Accedere alle origini dati**  
  L'impostazione di questo criterio consente di gestire l'accesso da parte di Internet Explorer a dati appartenenti a un'altra area di sicurezza usando Microsoft XML Parser (MSXML) o ActiveX Data Objects (ADO). Se si abilita l'impostazione di questo criterio, gli utenti potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire il caricamento di una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se non si configura l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067161)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Non eseguire antimalware sui controlli ActiveX per l'area Internet**  
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067162)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Copiare e incollare tramite script**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte degli script di operazioni con gli Appunti, ad esempio operazioni di taglia, copia e incolla, in un'area specificata. Se si abilita l'impostazione di questo criterio, gli script potranno eseguire operazioni con gli Appunti. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire l'esecuzione di operazioni con gli Appunti. Se si disabilita l'impostazione di questo criterio, gli script non potranno eseguire operazioni con gli Appunti. Se non si configura l'impostazione di questo criterio, gli script potranno eseguire operazioni con gli Appunti.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067084)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Usare il servizio di installazione di Active X**  
  L'impostazione di questo criterio consente di specificare la modalità di installazione dei controlli ActiveX. Se si abilita l'impostazione di questo criterio, i controlli ActiveX verranno installati solo se il servizio ActiveX Installer è presente ed è stato configurato per consentire l'installazione di controlli ActiveX. Se si disabilita o non si configura l'impostazione di questo criterio, i controlli ActiveX, inclusi i controlli per singolo utente, verranno installati usando la procedura di installazione standard.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067163)
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Protezione dei processi da elevazione privilegi dell'area**  
  Internet Explorer applica restrizioni a ogni pagina Web aperta. Le restrizioni dipendono dalla posizione della pagina Web (area Internet, Intranet, Computer locale e così via). Le pagine Web nel computer locale, ad esempio, sono soggette al minor numero di restrizioni di sicurezza e appartengono all'area Computer locale. Di conseguenza, l'area di sicurezza Computer locale è uno dei bersagli preferiti degli utenti malintenzionati. Se si abilita l'impostazione di questo criterio, sarà possibile proteggere qualsiasi area contro l'elevazione dei privilegi per tutti i processi. Se si disabilita o non si configura l'impostazione di questo criterio, i processi non di Internet Explorer o non specificati nell'Elenco processi non usufruiranno di tale protezione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067160)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area Internet - Scaricare controlli ActiveX non firmati**   
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX non firmati dall'area. Il codice di questo tipo può essere dannoso, soprattutto se proviene da un'area non attendibile. Se si abilita l'impostazione di questo criterio, i controlli non firmati potranno essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione del controllo non firmato. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati. Se non si configura l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067325)
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Esplorare finestre e frame in domini diversi**   
  L'impostazione di questo criterio consente di gestire l'apertura di finestre e frame ed accedere alle applicazioni in domini diversi. Se si abilita l'impostazione di questo criterio, gli utenti potranno aprire finestre e frame e accedere ad applicazioni da altri domini. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire l'apertura di finestre e frame o l'accesso ad applicazioni in altri domini. Se si disabilita questa impostazione, gli utenti non potranno aprire finestre o frame né accedere ad applicazioni in altri domini. Se non si configura questa impostazione, gli utenti potranno aprire finestre e frame e accedere ad applicazioni in altri domini.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067083)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Aggiornamenti alla barra di stato tramite script**  
  L'impostazione di questo criterio consente di gestire gli aggiornamenti della barra di stato tramite uno script all'interno dell'area. Se si abilita questa impostazione, gli script possono aggiornare la barra di stato. Se si disabilita o non si configura l'impostazione di questo criterio, lo script non potrà aggiornare la barra di stato.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067087)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Includere percorso locale nel caricamento di file sul server**  
  L'impostazione di questo criterio consente di specificare se inviare le informazioni sul percorso locale quando l'utente carica un file tramite un modulo HTML. Se le informazioni sul percorso locale vengono inviate, alcune di esse potrebbero essere rese note al server accidentalmente. I file inviati dal desktop di un utente, ad esempio, potrebbero contenere il nome utente come parte del percorso. Se si abilita l'impostazione di questo criterio, le informazioni sul percorso locale verranno inviate quando l'utente carica un file tramite un modulo HTML. Se si disabilita l'impostazione di questo criterio, le informazioni sul percorso verranno rimosse quando l'utente carica un file tramite un modulo HTML. Se non si configura l'impostazione di questo criterio, l'utente potrà scegliere se inviare le informazioni sul percorso quando carica un file tramite un modulo HTML. Per impostazione predefinita, le informazioni sul percorso vengono inviate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067085)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Processi - Limitare il download dei file**   
  L'impostazione di questo criterio consente alle applicazioni che ospitano il controllo WebBrowser di bloccare la richiesta di conferma automatica dei download di file non originati dall'utente. Se si abilita l'impostazione di questo criterio, il controllo WebBrowser bloccherà la richiesta di conferma automatica dei download di file non originati dall'utente per tutti i processi. Se si disabilita l'impostazione di questo criterio, il controllo WebBrowser bloccherà la richiesta di conferma automatica dei download di file non originati dall'utente per tutti i processi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067164)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Consentire solo ai domini approvati di usare i controlli ActiveX**   
  L'impostazione di questo criterio consente di specificare se agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX su siti Web diversi da quello che ha installato il controllo ActiveX. Se si abilita l'impostazione di questo criterio, agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX da siti Web in quest'area. L'utente può scegliere di autorizzare l'esecuzione del controllo dal sito corrente o da tutti i siti. Se si disabilita l'impostazione di questo criterio, l'utente non vede il prompt di ActiveX per ogni sito e i controlli ActiveX possono essere eseguiti da tutti i siti in quest'area.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067233)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Inizializzare ed eseguire script di controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067097)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Modifica dei criteri da parte degli utenti**  
  Impedisce agli utenti di modificare le impostazioni dell'area di sicurezza. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, il pulsante Livello personalizzato e il cursore del livello di sicurezza nella scheda Sicurezza della finestra di dialogo Opzioni Internet sono disabilitati. Se si disabilita questo criterio o non lo si configura, gli utenti possono modificare le impostazioni delle aree di sicurezza. Questo criterio impedisce agli utenti di modificare le impostazioni dell'area di sicurezza stabilite dall'amministratore. Nota: Il criterio "Disabilita la scheda Sicurezza", disponibile in Configurazione utente\Modelli amministrativi\Componenti di Windows\Internet Explorer\Pannello di controllo Internet, che rimuove la scheda Sicurezza da Internet Explorer nel Pannello di controllo, ha priorità rispetto al criterio appena descritto. Se il criterio "Disabilita la scheda Programmi" è abilitato, questo criterio verrà ignorato. Vedere anche il criterio "Aree di sicurezza: Usare solo le impostazioni del computer".  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Modalità protetta**  
  L'impostazione di questo criterio consente di attivare la modalità protetta. La modalità protetta consente di proteggere Internet Explorer da attacchi correlati ai rischi di sicurezza attraverso una riduzione delle posizioni in cui Internet Explorer può scrivere all'interno del Registro di sistema e del file system. Se si abilita l'impostazione di questo criterio, la modalità protetta viene attivata. L'utente non può disattivare la modalità protetta. Se si disabilita l'impostazione di questo criterio, la modalità protetta viene disattivata. L'utente non può attivare la modalità protetta. Se non si configura l'impostazione di questo criterio, l'utente può attivare o disattivare la modalità protetta.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Impostazione predefinita**: Abilitare  
  
- **Internet Explorer - Area Internet - Persistenza dei dati utente**  
  L'impostazione di questo criterio consente di gestire il mantenimento di informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Quando un utente apre una pagina salvata localmente, se l'impostazione di questo criterio è stata configurata in modo appropriato sarà possibile ripristinare lo stato della pagina. Se si abilita questa impostazione, gli utenti potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se si disabilita questa impostazione, gli utenti non potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se non si configura l'impostazione di questo criterio, gli utenti potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067156)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Eseguire script di controlli WebBrowser**  
 
  L'impostazione di questo criterio determina se una pagina può gestire i controlli WebBrowser incorporati tramite uno script. Se si abilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser è consentito. Se si disabilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser non è consentito. Se non si configura l'impostazione di questo criterio, l'utente può abilitare o disabilitare l'accesso tramite script ai controlli WebBrowser. Per impostazione predefinita, l'accesso tramite script ai controlli WebBrowser è consentito solo nelle aree Intranet e del computer locale.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067157)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Persistenza dei dati utente**  
  L'impostazione di questo criterio consente di gestire il mantenimento di informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Quando un utente apre una pagina salvata localmente, se l'impostazione di questo criterio è stata configurata in modo appropriato sarà possibile ripristinare lo stato della pagina. Se si abilita questa impostazione, gli utenti potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se si disabilita questa impostazione, gli utenti non potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se non si configura l'impostazione di questo criterio, gli utenti non potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067081)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Intranet - Bloccare le autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067082)  
  
  **Impostazione predefinita**: Disabilitare Java  
  
- **Modalità protetta avanzata in Internet Explorer**  
  La modalità protetta avanzata offre protezione aggiuntiva contro i siti Web dannosi usando processi a 64 bit nelle versioni di Windows a 64 bit. Per i computer che eseguono almeno Windows 8, la modalità protetta avanzata limita anche i percorsi leggibili da Internet Explorer nel Registro di sistema e nel file system. Se si abilita questa impostazione, viene attivata la modalità protetta avanzata. Per qualsiasi area in cui è abilitata la modalità protetta verrà usata la modalità protetta avanzata. Gli utenti non potranno disattivare la modalità protetta avanzata. Se si disabilita questa impostazione, viene disattivata la modalità protetta avanzata. Qualsiasi area in cui è abilitata la modalità protetta userà la versione della modalità protetta introdotta in Internet Explorer 7 per Windows Vista. Se questa impostazione non viene configurata, gli utenti possono attivare o disattivare la modalità protetta avanzata nella scheda Avanzate della finestra di dialogo Opzioni Internet.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067158)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Ignorare gli avvisi del filtro SmartScreen**  
  L'impostazione di questo criterio determina se l'utente può ignorare gli avvisi del filtro SmartScreen. Il filtro SmartScreen segnala i file eseguibili che gli utenti di Internet Explorer non scaricano spesso da Internet. Se si abilita l'impostazione di questo criterio, gli avvisi del filtro SmartScreen bloccheranno l'utente. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà ignorare gli avvisi del filtro SmartScreen.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067159)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - META REFRESH**  
  L'impostazione di questo criterio consente di gestire il reindirizzamento del browser di un utente a un'altra pagina Web nel caso in cui l'autore della pagina Web usi l'impostazione (tag) META REFRESH per il reindirizzamento dei browser a un'altra pagina Web. Se si abilita l'impostazione di questo criterio, quando il browser di un utente carica una pagina contenente un'impostazione META REFRESH attiva potrà essere reindirizzato a un'altra pagina Web. Se si disabilita l'impostazione di questo criterio, quando il browser di un utente carica una pagina contenente un'impostazione META REFRESH attiva, non potrà essere reindirizzato a un'altra pagina Web. Se non si configura l'impostazione di questo criterio, quando il browser di un utente carica una pagina contenente un'impostazione META REFRESH attiva, non potrà essere reindirizzato a un'altra pagina Web.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067154)  
  
  **Impostazione predefinita**: Disabilitato  
  
## <a name="local-policies-security-options"></a>Opzioni di sicurezza dei criteri locali
Per altre informazioni, vedere [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) (Provider di servizi di configurazione dei criteri - LocalPoliciesSecurityOptions) nella documentazione di Windows. 

- **Limitare l'accesso anonimo a named pipe e condivisioni**  
  Se abilitata, questa impostazione di sicurezza limita l'accesso anonimo alle condivisioni e alle named pipe specificate per le impostazioni: (1) named pipe a cui è possibile accedere in modo anonimo (2) condivisioni alle quali è possibile accedere in modo anonimo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Impostazione predefinita**: Sì  
  
- **Sicurezza sessione minima per server basati su NTLM SSP**  
  Questa impostazione di sicurezza consente ai server di richiedere la negoziazione della crittografia a 128 bit e/o della sicurezza di sessione NTLMv2. Tali valori dipendono dal valore dell'impostazione di sicurezza Livello di autenticazione di LAN Manager. Le opzioni disponibili sono: Richiedi sicurezza sessione NTLMv2: se l'integrità del messaggio non viene negoziata, la connessione non riesce. Richiedi crittografia a 128 bit. Se la crittografia avanzata (a 128 bit) non viene negoziata, la connessione non riesce.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Impostazione predefinita**: Richiedi NTLM V2 e crittografia a 128 bit  
  
- **Minuti di inattività della schermata di blocco prima dell'attivazione dello screen saver**  
  Windows rileva l'inattività di una sessione di accesso e, se il tempo di inattività supera il limite di inattività, verrà eseguito lo screen saver bloccando la sessione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Impostazione predefinita**: 15
  
- **Richiedere al client di aggiungere sempre la firma digitale alle comunicazioni** Questa impostazione di sicurezza determina se tutto il traffico inviato sul canale sicuro dal membro di dominio deve essere firmato o crittografato. Quando si aggiunge un computer a un dominio, viene creato un account computer. All'avvio il sistema usa quindi la password di tale account computer per creare un canale sicuro con un controller di dominio del proprio dominio. Il canale sicuro viene usato per eseguire operazioni come l'autenticazione pass-through NTLM, la ricerca dei nomi SID LSA e altre. Questa impostazione determina se tutto il traffico inviato sul canale sicuro dal membro di dominio soddisfa i requisiti di sicurezza minimi. In particolare, specifica se tutto il traffico inviato sul canale sicuro dal membro di dominio deve essere firmato o crittografato. Se questo criterio è abilitato, il canale sicuro viene creato esclusivamente se la firma o la crittografia di tutto il traffico sul canale sicuro viene negoziata. Se questo criterio è disabilitato, la firma o la crittografia di tutto il traffico sul canale sicuro viene negoziata con il controller di dominio. In tal caso, il livello di firma o crittografia dipende dalla versione del controller di dominio e dalle impostazioni dei due criteri seguenti. Membro di dominio: aggiunta crittografia o firma digitale ai dati del canale sicuro (quando possibile) Membro di dominio: aggiunta firma digitale ai dati del canale sicuro (quando possibile).  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067187) 
  
  **Impostazione predefinita**: Sì
  
- **Livello di autenticazione**  
  Questa impostazione di sicurezza specifica il protocollo di autenticazione Richiesta di verifica/Risposta usato per gli accessi di rete. L'opzione selezionata determina il livello del protocollo di autenticazione usato dai client, il livello della sicurezza di sessione negoziata e il livello di autenticazione accettato dai server. Sono disponibili le opzioni seguenti.  
  - *Invia risposte LM e NTLM* - I client usano l'autenticazione LM e NTLM e non usano mai la sicurezza di sessione NTLMv2. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia LM e NTLM - NTLMv2 se negoziata* - I client usano l'autenticazione LM e NTLM, nonché la sicurezza di sessione NTLMv2 se il server la supporta. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia solo risposta NTLM* - I client usano solo l'autenticazione NTLM e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia solo risposta NTLMv2* - I client usano solo l'autenticazione NTLMv2 e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia solo risposta NTLMv2, rifiuta LM* - I client usano solo l'autenticazione NTLMv2 e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio rifiutano l'autenticazione LM e accettano solo l'autenticazione NTLM e NTLMv2. 
  - *Invia solo risposta NTLMv2, rifiuta LM e NTLM* - I client usano solo l'autenticazione NTLMv2 e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio rifiutano l'autenticazione LM e NTLM e accettano solo l'autenticazione NTLMv2.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067189)   
    
  **Impostazione predefinita**: Invia solo risposta NTLMv2. Rifiuta LM e NTLM
  
- **Impedire ai client di inviare le password non crittografate a server SMB di terze parti**  
  Se questa impostazione di sicurezza è abilitata, durante l'autenticazione il redirector SMB (Server Message Block) può inviare password in formato non crittografato ai server SMB non Microsoft che non supportano la crittografia delle password. L'invio di password non crittografate rappresenta un rischio di sicurezza.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067235)  
  
  **Impostazione predefinita**: Sì
  
- **Richiedere sempre l'aggiunta della firma digitale del server alle comunicazioni**  
  Questa impostazione di sicurezza determina se il client SMB deve tentare di negoziare la firma dei pacchetti SMB. Il protocollo SMB (Server Message Block) costituisce la base delle funzionalità Microsoft per la condivisione di file e stampanti e di molte altre funzionalità di rete, come l'amministrazione remota di Windows. Per impedire gli attacchi man in the middle che modificano i pacchetti SMB durante la trasmissione, il protocollo SMB supporta la firma digitale dei pacchetti SMB. L'impostazione di questo criterio determina se il componente client di SMB deve tentare di negoziare la firma dei pacchetti SMB quando si connette a un server SMB. Se questa impostazione è abilitata, il client di rete Microsoft richiederà al server di eseguire la firma dei pacchetti SMB al momento della configurazione della sessione. Se la firma dei pacchetti è stata abilitata sul server, la firma dei pacchetti sarà negoziata. Se questo criterio è disabilitato, il client SMB non potrà mai negoziare la firma dei pacchetti SMB.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067319)  
  
  **Impostazione predefinita**: Sì
  
- **Comportamento della richiesta di elevazione dei privilegi per gli amministratori**  
  L'impostazione di questo criterio specifica il comportamento della richiesta di elevazione dei privilegi per gli amministratori. Le opzioni disponibili sono: 
  - *Esegui con privilegi elevati senza chiedere conferma* - Consente di eseguire un'operazione che richiede l'elevazione dei privilegi senza richiedere consenso o credenziali. Nota: usare questa opzione solo in ambienti molto vincolati. 
  - *Richiedi le credenziali nel desktop protetto* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente del desktop protetto dovrà immettere il nome utente e la password di un utente con i privilegi necessari. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio massimo disponibile dell'utente. 
  - *Richiedi il consenso nel desktop protetto* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente del desktop protetto dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile. 
  - *Richiedi credenziali* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà inserire un nome utente e una password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio applicabile. 
  - *Richiedi il consenso* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile.  
  - *Richiedi il consenso per file binari non Windows* - Quando un'operazione per un'applicazione non Microsoft richiede l'elevazione dei privilegi, sul desktop protetto l'utente dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile. 
  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Impostazione predefinita**: Richiedi consenso sul desktop sicuro
  
- **Sicurezza sessione minima per client basati su NTLM SSP**  
  Questa impostazione di sicurezza consente ai client di richiedere la negoziazione della crittografia a 128 bit e/o della sicurezza di sessione NTLMv2. Tali valori dipendono dal valore dell'impostazione di sicurezza Livello di autenticazione di LAN Manager. Le opzioni disponibili sono:
  - *Richiedi sicurezza sessione NTLMv2* - Se il protocollo NTLMv2 non viene negoziato, la connessione non riuscirà. 
  - *Richiedi crittografia a 128 bit* Se la crittografia avanzata (a 128 bit) non viene negoziata, la connessione non riesce.
  - *Richiedi NTLM V2 e la crittografia a 128 bit*.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Impostazione predefinita**: Richiedi NTLM V2 e crittografia a 128 bit
  
- **Comportamento in caso di rimozione della smart card**  
  Questa impostazione di sicurezza determina le conseguenze della rimozione della smart card di un utente connesso dal lettore di smart card. Le opzioni disponibili sono:
  - *Nessuna azione*. 
  - *Blocca workstation* - La workstation è bloccata quando la smart card viene rimossa, consentendo agli utenti di uscire dall'area, tenere la smart card e mantenere comunque una sessione protetta.
  - *Imponi disconnessione*: l'utente viene automaticamente disconnesso quando la smart card viene rimossa.
  - *Disconnetti la sessione Desktop remoto*: la rimozione della smart card determina la disconnessione della sessione senza disconnettere l'utente. Questa modalità consente all'utente di inserire la smart card e di riprendere la sessione in seguito oppure di usare un altro terminale dotato di lettore di smart card senza dover effettuare un'altra connessione. Se la sessione è locale, questo criterio funziona in modo identico all'opzione Blocca workstation.
  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067331) 
    
  **Impostazione predefinita**: Blocca workstation
  
- **Bloccare l'enumerazione anonima di account e condivisioni SAM**  
  Questa impostazione di sicurezza determina se consentire l'enumerazione anonima degli account e delle condivisioni SAM. In Windows agli utenti anonimi è consentita l'esecuzione di determinate operazioni, come l'enumerazione dei nomi degli account di dominio e delle condivisioni di rete. Questo è utile ad esempio quando l'amministratore vuole concedere l'accesso agli utenti di un dominio attendibile che non mantiene una relazione di trust reciproca. Se non si intende consentire l'enumerazione anonima degli account e delle condivisioni SAM, impostare questo criterio su *Sì*.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067191)  
  
  **Impostazione predefinita**: Sì
  
- **Bloccare l'accesso remoto con password vuota**  
  Questa impostazione di sicurezza determina se gli account locali non protetti da password possono essere usati per accedere da postazioni diverse dalla console del computer fisico. Se abilitata, gli utenti con account locali non protetti da password devono usare la tastiera del computer per eseguire l'accesso. 

  *Avviso*: per i computer che non si trovano in posizioni fisicamente sicure è consigliabile applicare sempre criteri password complessi a tutti gli account utente locali. In caso contrario, chiunque riesca ad accedere fisicamente al computer può effettuare l'accesso usando un account utente privo di password. Questa misura è particolarmente importante per i computer portatili. 

  Se si applicano questi criteri di sicurezza al gruppo Everyone, nessun utente può eseguire l'accesso tramite Servizi Desktop remoto. Questa impostazione non interessa gli accessi eseguiti usando account di dominio. Le applicazioni che usano accessi interattivi remoti possono eludere questa impostazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067219)  
  
  **Impostazione predefinita**: Sì
  
- **Comportamento della richiesta di elevazione dei privilegi per gli utenti standard**  
  L'impostazione di questo criterio specifica il comportamento della richiesta di elevazione dei privilegi per gli utente standard. 
  - *Rifiuta automaticamente le richieste di elevazione dei privilegi* - Quando un'operazione richiede l'elevazione dei privilegi, viene visualizzato un messaggio di errore di accesso negato che può essere configurato. Un'azienda che esegue i desktop come utente standard può scegliere questa impostazione per ridurre le chiamate all'help desk. 
  - *Richiedi le credenziali nel desktop protetto* - Quando un'operazione richiede l'elevazione dei privilegi, sul desktop protetto l'utente dovrà immettere un nome utente e una password differenti. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio applicabile. 
  - *Richiedi credenziali* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà inserire un nome utente e una password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio applicabile.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Impostazione predefinita**: Nega automaticamente richieste di elevazione dei privilegi
  
- **Richiedere la modalità Approvazione amministratore per gli amministratori**  
  L'impostazione di questo criterio specifica il comportamento di tutte le impostazioni dei criteri di Controllo dell'account utente per il computer. Se si modifica questa impostazione di criteri, è necessario riavviare il computer. Le opzioni disponibili sono:   
  - *Non configurato* - La modalità Approvazione amministratore e i criteri correlati di Controllo dell'account utente sono disattivati. Nota: se questa impostazione viene disabilitata, Centro sicurezza PC segnala che la sicurezza complessiva del sistema operativo è ridotta. 
  - *Sì* - La modalità Approvazione amministratore è abilitata. Perché l'account predefinito Administrator e tutti gli altri utenti membri del gruppo Administrators possano essere eseguiti in modalità Approvazione amministratore, è necessario che questo criterio sia abilitato e che tutti i criteri di Controllo dell'account utente correlati siano impostati in modo appropriato.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067184)  
  
  **Impostazione predefinita**: Sì
  
- **Impedire l'enumerazione anonima degli account SAM**  
  Questa impostazione di sicurezza determina quali autorizzazioni aggiuntive vengono concesse in caso di connessioni anonime al computer. In Windows agli utenti anonimi è consentita l'esecuzione di determinate operazioni, come l'enumerazione dei nomi degli account di dominio e delle condivisioni di rete. Questo è utile ad esempio quando l'amministratore vuole concedere l'accesso agli utenti di un dominio attendibile che non mantiene una relazione di trust reciproca. Questa opzione di sicurezza consente di specificare restrizioni aggiuntive per connessioni anonime, ad esempio: 
  - *Sì* - Non consentire l'enumerazione degli account SAM. Questa opzione sostituisce Everyone con Authenticated Users nelle autorizzazioni di sicurezza per le risorse.
  - *Non configurato* - Nessuna restrizione aggiuntiva. Vengono usate le autorizzazioni predefinite.  
  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067318)  

  **Impostazione predefinita**: Sì
  
- **Consentire chiamate remote al sistema di gestione degli account di sicurezza**  
  L'impostazione di questo criterio consente di limitare le connessioni RPC remote al sistema di gestione degli account di sicurezza. Se il criterio non viene selezionato, viene usato il descrittore di sicurezza predefinito.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067209)  
  
  **Impostazione predefinita**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Usare la modalità Approvazione amministratore**  
  L'impostazione di questo criterio specifica il comportamento della modalità Approvazione amministratore per l'account Administrator predefinito. Le opzioni disponibili sono: 
  - *Sì* - L'account predefinito Administrator usa la modalità Approvazione amministratore. Per impostazione predefinita, per qualunque operazione che richiede l'elevazione dei privilegi verrà richiesta l'approvazione dell'utente. 
  - *Non configurato* - L'account predefinito Administrator esegue tutte le applicazioni con privilegi amministrativi completi. 

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Impostazione predefinita**: Sì
  
- **Consentire le applicazioni con accesso all'interfaccia utente per percorsi sicuri**  
  L'impostazione di questo criterio specifica se i programmi con accesso all'interfaccia utente (UIAccess o UIA) possono disabilitare automaticamente il desktop protetto per le richieste di elevazione dei privilegi provenienti da un utente standard. 
  - *Sì* - I programmi con Automazione interfaccia utente, incluso Assistenza remota di Windows, disabilitano automaticamente il desktop protetto per le richieste di elevazione dei privilegi. Se non si disabilita il criterio "Controllo dell'account utente: alla richiesta di elevazione dei privilegi, passa al desktop protetto", le richieste vengono visualizzate sul desktop interattivo dell'utente invece che sul desktop protetto. 
  - *Non configurato* - Il desktop protetto può essere disabilitato solo dall'utente del desktop interattivo o disabilitando il criterio "Controllo account utente: alla richiesta di elevazione dei privilegi, passa al desktop protetto".  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Impostazione predefinita**: Sì

- **Rilevare installazioni di applicazioni e richiedere l'elevazione dei privilegi**  
  L'impostazione di questo criterio specifica il comportamento del rilevamento di installazioni di applicazioni nel computer. Le opzioni disponibili sono: 
  - *Abilitato* - Per i pacchetti di installazione delle applicazioni che richiedono l'elevazione dei privilegi, l'utente dovrà immettere nome utente e password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio applicabile. 
  - *Disabilitato* - I pacchetti di installazione delle applicazioni non vengono rilevati e non viene richiesta l'elevazione dei privilegi. Le organizzazioni che eseguono desktop utente standard e usano tecnologie di installazione delegata quali Estensione dell'installazione software basata su Criteri di gruppo o Systems Management Server (SMS) devono disabilitare questa impostazione di criteri. In questo caso, il rilevamento del programma di installazione non è necessario.  
  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067208)  

  **Impostazione predefinita**: Sì
  
- **Non archiviare il valore hash di LAN Manager al cambio di password successivo**  
  Questa impostazione di sicurezza specifica se, al cambio di password successivo, deve essere archiviato il valore hash di LAN Manager per la nuova password. Il valore hash di LAN Manager è relativamente vulnerabile e soggetto ad attacchi rispetto all'hash di Windows NT, che è basato su una crittografia più avanzata. Poiché l'hash di LAN Manager è archiviato nel database di sicurezza del computer locale, un eventuale attacco al database di sicurezza può compromettere le password.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067213)  
  
  **Impostazione predefinita**: Sì

- **Virtualizzare gli errori di scrittura nel file e nel Registro di sistema in percorsi specifici per ogni utente**  
  L'impostazione di questo criterio specifica se gli errori di scrittura delle applicazioni vengono reindirizzati in percorsi definiti sia nel Registro di sistema sia nel file system. Questo criterio riduce l'impatto delle applicazioni che vengono eseguite con account amministratore ed eseguono la scrittura dei dati in fase di esecuzione in *%ProgramFiles%* , *%Windir%* , *%Windir%\system32* o *HKLM\Software*.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067321)  
  
  **Impostazione predefinita**: Sì

## <a name="ms-security-guide"></a>Guida alla sicurezza MS  
Per altre informazioni, vedere [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) (Provider di servizi di configurazione dei criteri - MSSecurityGuide) nella documentazione di Windows.  

- **Applicare le restrizioni di Controllo dell'account all'accesso alla rete**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067188)  

  **Impostazione predefinita**: Abilitato
  
- **Configurazione dell'avvio del driver client SMB v1**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067214) 
 
  **Impostazione predefinita**: Driver disabilitato
  
- **Server SMB v1**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067190)  

  **Impostazione predefinita**: Disabilitato
  
- **Autenticazione del digest**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067193) 
 
  **Impostazione predefinita**: Disabilitato
  
- **Proteggere da sovrascrittura la gestione di eccezioni strutturata**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067217)  

  **Impostazione predefinita**: Abilitato
  
## <a name="mss-legacy"></a>MSS Legacy  
Per altre informazioni, vedere [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) (Provider di servizi di configurazione dei criteri - MSSLegacy) nella documentazione di Windows.  

- **Livello di protezione del routing di origine dell'IP di rete**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067220)  
  
  **Impostazione predefinita**: Protezione massima  
  
- **Ignorare le richieste di rilascio nome NetBIOS nella rete, ad eccezione dei server WINS**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067218)  
 
  **Impostazione predefinita**: Abilitato
  
- **Livello di protezione del routing di origine IPv6 di rete**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067216)  

  **Impostazione predefinita**: Protezione massima

- **Eseguire l'override di OSPF generati con reindirizzamenti ICM di rete**  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067326)  

  **Impostazione predefinita**: Disabilitato
  
## <a name="power"></a>Alimentazione  
Per altre informazioni, vedere [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) (Provider di servizi di configurazione dei criteri - Power) nella documentazione di Windows.  

- **Richiedere la password alla riattivazione durante l'alimentazione da rete elettrica**  
  L'impostazione di questo criterio specifica se all'utente viene richiesta una password quando il sistema viene riattivato dopo la sospensione. Se si abilita o non si configura l'impostazione di questo criterio, all'utente viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione. Se si disabilita l'impostazione di questo criterio, all'utente non viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067221)  
  
  **Impostazione predefinita**: Abilitato
  
- **Stati di standby durante la sospensione durante l'alimentazione a batteria**  
  Questa impostazione indica se Windows può usare gli stati di standby quando il computer è in uno stato di sospensione. Se si abilita o non si configura l'impostazione di questo criterio, Windows usa gli stati di standby per impostare lo stato di sospensione del computer. Se si disabilita l'impostazione di questo criterio, gli stati di standby (S1-S3) non sono consentiti.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067195)  
  
  **Impostazione predefinita**: Disabilitato
  
- **Stati di standby durante la sospensione durante l'alimentazione da rete elettrica**  
  Questa impostazione indica se Windows può usare gli stati di standby quando il computer è in uno stato di sospensione. Se si abilita o non si configura l'impostazione di questo criterio, Windows usa gli stati di standby per impostare lo stato di sospensione del computer. Se si disabilita l'impostazione di questo criterio, gli stati di standby (S1-S3) non sono consentiti.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067196)  
  
  **Impostazione predefinita**: Disabilitato
  
- **Richiedere la password alla riattivazione durante l'alimentazione a batteria**  
  L'impostazione di questo criterio specifica se all'utente viene richiesta una password quando il sistema viene riattivato dopo la sospensione. Se si abilita o non si configura l'impostazione di questo criterio, all'utente viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione. Se si disabilita l'impostazione di questo criterio, all'utente non viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067322)  
  
  **Impostazione predefinita**: Abilitato

## <a name="remote-assistance"></a>Assistenza remota
- **Assistenza remota richiesta**  
  Questa impostazione di criteri consente di attivare o disattivare Assistenza remota su richiesta in questo computer. 
  - *Se si abilita questa impostazione di criteri*, gli utenti di questo computer possono usare la posta elettronica o il trasferimento di file per chiedere assistenza a un utente. Gli utenti possono anche usare programmi di messaggistica istantanea per consentire le connessioni al computer ed è possibile configurare altre impostazioni di Assistenza remota. 
  - *Se si disabilita questa impostazione di criteri*, gli utenti di questo computer non possono usare la posta elettronica o il trasferimento di file per chiedere assistenza. Gli utenti non possono neanche usare programmi di messaggistica istantanea per consentire le connessioni a questo computer. 
  - *Se questa impostazione di criteri non viene configurata*, gli utenti possono attivare o disattivare Assistenza remota su richiesta nelle proprietà di sistema nel Pannello di controllo. Gli utenti possono anche configurare le impostazioni di Assistenza remota. 

  Se si abilita questa impostazione di criteri, sono disponibili due modi per consentire ad altri utenti di fornire assistenza remota: "Consenti solo di visualizzare il computer" o "Consenti controllo remoto del computer". L'impostazione di criteri "Durata massima ticket" consente di impostare un limite per il periodo di tempo durante il quale può rimanere aperto un invito di assistenza remota creato tramite posta elettronica o trasferimento di file. L'impostazione "Selezionare il metodo di invio degli inviti via posta elettronica" specifica lo standard di posta elettronica da usare per inviare inviti di Assistenza remota. In base al programma di posta elettronica in uso, è possibile usare lo standard Mailto, nel qual caso il destinatario dell'invito si connetterà tramite un collegamento Internet, o lo standard SMAPI (Simple MAPI), nel qual caso l'invito sarà allegato al messaggio di posta elettronica. Questa impostazione di criteri non è disponibile in Windows Vista perché è supportato solo il metodo SMAPI. Se si abilita questa impostazione di criteri, sarà inoltre necessario abilitare le eccezioni del firewall appropriate per consentire le comunicazioni di Assistenza remota.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Impostazione predefinita**: Disabilita assistenza remota

  Quando si imposta *Abilita Assistenza remota*, configurare le impostazioni aggiuntive seguenti:  
  - **Autorizzazione richiesta da Assistenza remota**  
    **Impostazione predefinita**: Visualizza  

  - **Durata massima ticket (valore)**  
    **Impostazione predefinita**: *Non configurato*  

  - **Maximum ticket time period** (Durata massima ticket)  
    **Impostazione predefinita**: Minuti    

  - **Metodo di invito tramite posta elettronica**  
    **Impostazione predefinita**: Simple MAPI

  
## <a name="remote-desktop-services"></a>Servizi Desktop remoto  
Per altre informazioni, vedere [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) (Provider di servizi di configurazione dei criteri - RemoteDesktopServices) nella documentazione di Windows.  

- **Bloccare il salvataggio delle password**  
  Controlla se è possibile salvare le password nel computer da Connessione Desktop remoto. Se si abilita questa impostazione, la casella di controllo di salvataggio della password in Connessione Desktop remoto viene disabilitata e gli utenti non potranno salvare le password. Quando un utente apre un file RDP tramite Connessione Desktop remoto e salva le proprie impostazioni, qualsiasi password presente in precedenza nel file RDP viene eliminata. Se si disabilita questa impostazione o la si lascia non configurata, l'utente può salvare le password in Connessione Desktop remoto.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067301)  
  
   **Impostazione predefinita**: Abilitato
  
- **Comunicazione RPC protetta**  
  Specifica se un server host sessione Desktop remoto richiede la comunicazione RPC protetta con tutti i client o consente la comunicazione non protetta. È possibile usare questa impostazione per rafforzare la protezione della comunicazione RPC con i client, consentendo solo richieste autenticate e crittografate. Se lo stato è impostato su Abilitato, Servizi Desktop remoto accetta le richieste dai client RPC che supportano richieste protette e non consente la comunicazione non protetta con client non attendibili. Se lo stato è impostato su Disabilitato, Servizi Desktop remoto richiede sempre la protezione per tutto il traffico RPC. La comunicazione non protetta, tuttavia, è consentita per i client RPC che non rispondono alla richiesta. Se lo stato è impostato su Non configurato, la comunicazione non protetta è consentita. Nota: l'interfaccia RPC viene usata per l'amministrazione e la configurazione di Servizi Desktop remoto.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067248)  
  
  **Impostazione predefinita**: Abilitato
  
- **Bloccare il reindirizzamento delle unità**  
  L'impostazione di questo criterio specifica se impedire il mapping delle unità dei client in una sessione di Servizi Desktop remoto (reindirizzamento delle unità). Per impostazione predefinita, un server host sessione Desktop remoto esegue automaticamente il mapping di unità di client al momento della connessione. Le unità mappate vengono visualizzate nell'albero delle cartelle della sessione in Esplora file o in Computer nel formato *\<letteraunità>* in *\<nomecomputer>* . È possibile usare l'impostazione di questo criterio per eseguire l'override di questo comportamento. Se si abilita l'impostazione di questo criterio, il reindirizzamento delle unità dei client non è consentito nelle sessioni di Servizi Desktop remoto e il reindirizzamento della copia dei file degli Appunti non è consentito nei computer che eseguono Windows Server 2003, Windows 8 e Windows XP. Se si disabilita l'impostazione di questo criterio, il reindirizzamento delle unità dei client è sempre consentito. Inoltre, se è consentito il reindirizzamento degli Appunti, il reindirizzamento della copia dei file degli Appunti è sempre consentito. Se non si configura l'impostazione di questo criterio, il reindirizzamento delle unità dei client e il reindirizzamento della copia dei file degli Appunti non sono specificate a livello di Criteri di gruppo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067197)  
  
  **Impostazione predefinita**: Abilitato
  
- **Richiedere la password al momento della connessione**  
  L'impostazione di questo criterio specifica se Servizi Desktop remoto deve sempre richiedere la password al client al momento della connessione. È possibile usare questa impostazione per imporre la richiesta della password agli utenti che accedono a Servizi Desktop remoto, anche se hanno già specificato la password nel client di Connessione Desktop remoto. Per impostazione predefinita, Servizi Desktop remoto consente agli utenti di accedere automaticamente tramite l'immissione di una password nel client di Connessione Desktop remoto. Se si abilita l'impostazione di questo criterio, gli utenti non possono accedere automaticamente a Servizi Desktop remoto specificando la propria password nel client di Connessione Desktop remoto, ma viene loro richiesto di immettere una password per l'accesso. Se si disabilita l'impostazione di questo criterio, gli utenti possono sempre accedere automaticamente a Servizi Desktop remoto specificando la propria password nel client di Connessione Desktop remoto. Se non si configura l'impostazione di questo criterio, l'accesso automatico non è specificato a livello di Criteri di gruppo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067328)  
  
  **Impostazione predefinita**: Abilitato
  
- **Livello di crittografia della connessione client a Servizi Desktop remoto**  
  Specifica se richiedere l'uso di un livello di crittografia specifico per proteggere le comunicazioni tra computer client e server host sessione Desktop remoto durante le connessioni Remote Desktop Protocol (RDP). Questo criterio si applica solo quando si usa la crittografia RDP nativa. La crittografia RDP (in contrapposizione alla crittografia SSL), tuttavia, non è consigliata. Questo criterio non si applica alla crittografia SSL. Se si abilita l'impostazione di questo criterio, tutte le comunicazioni tra client e server host sessione Desktop remoto durante le connessioni remote devono usare il metodo di crittografia specificato in questa impostazione. Per impostazione predefinita, il livello di crittografia è impostato su Alto. Sono disponibili i metodi di crittografia seguenti:  
  - *Alto* - L'impostazione Alto consente di crittografare i dati inviati dal client al server e dal server al client usando la crittografia avanzata a 128 bit. Usare questo livello di crittografia in ambienti che contengono solo client a 128 bit, ad esempio client che eseguono Connessione Desktop remoto. I client che non supportano questo livello di crittografia non possono connettersi a server host sessione Desktop remoto.  
  - *Compatibile con il client* - L'impostazione Compatibile con il client consente di crittografare i dati scambiati tra il client e il server con il livello massimo di complessità della chiave supportato dal client. Usare questo livello di crittografia in ambienti che includono client che non supportano la crittografia a 128 bit.  
  - *Basso* - L'impostazione Basso consente di crittografare solo i dati inviati dal client al server tramite crittografia a 56 bit.  
  
  Se si disabilita o non si configura questa impostazione, il livello di crittografia da usare per le connessioni remote a server host sessione Desktop remoto non viene imposto tramite Criteri di gruppo. Importante: è possibile configurare la conformità FIPS (Federal Information Processing Standard) tramite la crittografia di sistema. Usare algoritmi conformi a FIPS per le impostazioni di crittografia, hash e firma in Criteri di gruppo, in Configurazione computer\Impostazioni di Windows\Impostazioni sicurezza\Criteri locali\Opzioni di sicurezza. L'impostazione conforme a FIPS consente di crittografare e decrittografare i dati inviati dal client al server e dal server al client con gli algoritmi di crittografia Federal informazioni Processing Standard (FIPS) 140 usando i moduli di crittografia Microsoft. Usare questo livello di crittografia quando le comunicazioni tra client e server host sessione Desktop remoto richiedono il massimo livello di crittografia.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067222)  
  
  **Impostazione predefinita**: Alta
  
## <a name="remote-management"></a>Gestione remota  
Per altre informazioni, vedere [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) (Provider di servizi di configurazione dei criteri - RemoteManagement) nella documentazione di Windows.  

- **Bloccare l'archiviazione eseguita come credenziali**  
  Autenticazione client di base.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067300)  
  
  **Impostazione predefinita**: Abilitato
  
- **Autenticazione di base**  
  L'impostazione di questo criterio consente di gestire se il servizio Gestione remota Windows (WinRM) deve accettare l'autenticazione di base da un client remoto. Se si abilita l'impostazione di questo criterio, il servizio Gestione remota Windows accetta l'autenticazione di base da un client remoto. Se si disabilita o non si configura l'impostazione di questo criterio, il servizio Gestione remota Windows non accetta l'autenticazione di base da un client remoto.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067223)  
  
  **Impostazione predefinita**: Disabilitato
  
- **Bloccare l'autenticazione del digest del client**  
  L'impostazione di questo criterio consente di gestire se il client Gestione remota Windows (WinRM) deve usare l'autenticazione del digest. Se si abilita l'impostazione di questo criterio, il client WinRM non usa l'autenticazione del digest. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM usa l'autenticazione del digest.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067302)  
  
  **Impostazione predefinita**: Abilitato
  
- **Traffico non crittografato**  
  L'impostazione di questo criterio consente di gestire se il servizio Gestione remota Windows (WinRM) può inviare e ricevere messaggi non crittografati attraverso la rete. Se si abilita l'impostazione di questo criterio, il client WinRM invia e riceve messaggi non crittografati attraverso la rete. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM invia e riceve attraverso la rete solo messaggi crittografati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067226)  
  
  **Impostazione predefinita**: Disabilitato
  
- **Traffico non crittografato client**  
  L'impostazione di questo criterio consente di gestire se il client Gestione remota Windows (WinRM) può inviare e ricevere messaggi non crittografati attraverso la rete. Se si abilita l'impostazione di questo criterio, il client WinRM invia e riceve messaggi non crittografati attraverso la rete. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM invia e riceve attraverso la rete solo messaggi crittografati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067304)  
  
  **Impostazione predefinita**: Disabilitato
  
- **Autenticazione client di base**  
  L'impostazione di questo criterio consente di gestire se il client Gestione remota Windows (WinRM) usa l'autenticazione di base. Se si abilita l'impostazione di questo criterio, il client WinRM usa l'autenticazione di base. Se il servizio WinRM è configurato per l'uso del trasporto HTTP, il nome utente e password vengono inviati attraverso la rete come testo non crittografato. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM non usa l'autenticazione di base.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067252)  
  
  **Impostazione predefinita**: Disabilitato
  
## <a name="remote-procedure-call"></a>Chiamata di procedura remota  
Per altre informazioni, vedere [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) (Provider di servizi di configurazione dei criteri - RemoteProcedureCall) nella documentazione di Windows.  

- **Opzioni client RPC non autenticati**  
  L'impostazione di questo criterio controlla il modo in cui il runtime del server RPC gestisce i client RPC non autenticati che si connettono a server RPC. L'impostazione di questo criterio influisce su tutte le applicazioni RPC. In un ambiente di dominio usare con cautela l'impostazione di questo criterio perché può influire su una vasta gamma di funzionalità, inclusa l'elaborazione dei Criteri di gruppo stessi. Il ripristino del valore precedente dopo una modifica all'impostazione di questo criterio può richiedere un intervento manuale in ogni computer interessato. L'impostazione di questo criterio non deve mai essere applicata a un controller di dominio. Se si disabilita l'impostazione di questo criterio, il runtime del server RPC usa il valore "Autenticato" in Windows Client e il valore "Nessuno" nelle versioni di Windows Server che supportano questa impostazione. Se non si configura l'impostazione di questo criterio, questa rimane disabilitata. Il runtime del server RPC si comporta come se fosse abilitato con il valore "Autenticato" usato per il client Windows e il valore "Nessuno" usato per gli SKU dei server che supportano questa impostazione. Se si abilita l'impostazione di questo criterio, il runtime del server RPC limita i client RPC non autenticati che si connettono ai server RPC in esecuzione in un computer. Un client viene considerato autenticato se usa una named pipe per comunicare con il server o se usa la sicurezza RPC. Le interfacce RPC che hanno richiesto in modo specifico di essere accessibili per i client non autenticati possono essere esenti da questa limitazione, a seconda del valore selezionato per l'impostazione di questo criterio.  
  - *Nessuno* consente a tutti i client RPC di connettersi ai server RPC in esecuzione nel computer in cui l'impostazione del criterio viene applicata. 
  - *Autenticato* consente solo ai client RPC autenticati (in base alla definizione precedente) di connettersi ai server RPC in esecuzione nel computer in cui l'impostazione del criterio viene applicata. Vengono concesse esenzioni alle interfacce che le hanno richieste. 
  - *Autenticato senza eccezioni* consente solo ai client RPC autenticati (in base alla definizione precedente) di connettersi ai server RPC in esecuzione nel computer in cui l'impostazione del criterio viene applicata. Non sono consentite eccezioni. Nota: questa impostazione di criteri verrà applicata solo dopo il riavvio del sistema.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067225)  

  **Impostazione predefinita**: Autenticato

## <a name="search"></a>Cerca 
Per altre informazioni, vedere [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) (Provider di servizi di configurazione dei criteri - Search) nella documentazione di Windows.  

- **Disabilitare l'indicizzazione di elementi crittografati**  
  Consente o impedisce l'indicizzazione di elementi. Questa opzione è per l'indicizzatore di Ricerca di Windows, che stabilisce se deve essere eseguita l'indicizzazione degli elementi che vengono crittografati, ad esempio i file protetti di Windows Information Protection (WIP). Quando i criteri sono abilitati, gli elementi protetti da WIP vengono indicizzati e i relativi metadati vengono archiviati in un percorso non crittografato. I metadati includono elementi come percorso del file e data di modifica. Quando i criteri sono disabilitati, gli elementi protetti da WIP non vengono indicizzati e non appaiono nei risultati di Cortana o Esplora file. Si può inoltre avere un impatto sulle prestazioni delle app Foto e Groove se nel dispositivo sono presenti molti file multimediali protetti con WIP.  
  [Altre informazioni]( https://go.microsoft.com/fwlink/?linkid=2067303)  
  
  **Impostazione predefinita**: Sì
  
## <a name="smart-screen"></a>SmartScreen  
Per altre informazioni, vedere [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) (Provider di servizi di configurazione dei criteri - SmartScreen) nella documentazione di Windows.  

- **Bloccare l'esecuzione di file non verificati**  
  Impedisce all'utente di eseguire file non verificati. 
  - *Non configurato*: i dipendenti possono ignorare gli avvisi di SmartScreen ed eseguire file dannosi. 
  - *Sì*: i dipendenti non possono ignorare gli avvisi di SmartScreen ed eseguire file dannosi.

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067228)  
  
  **Impostazione predefinita**: Sì

- **Richiedere SmartScreen per app e file**  
  Consente agli amministratori IT di configurare SmartScreen per Windows.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067168)  

  **Impostazione predefinita**: Sì
  
## <a name="system"></a>Sistema  
Per altre informazioni, vedere [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) (Provider di servizi di configurazione dei criteri - System) nella documentazione di Windows.  

- **Inizializzazione del driver di esecuzione avvio del sistema**  
  L'impostazione di questo criterio consente di specificare i driver di esecuzione inizializzati in base a una classificazione determinata da un driver di esecuzione avvio antimalware ad esecuzione anticipata. Il driver di esecuzione avvio antimalware ad esecuzione anticipata può restituire le classificazioni seguenti per ogni driver di esecuzione avvio: 
  - *Valido* - Il driver è stato firmato e non è stato manomesso.  
  - *Bad* (Non valido): il driver è stato identificato come malware. È consigliabile non consentire l'inizializzazione dei driver non validi. 
  - *Bad, but required for boot* (Non valido ma necessario per l'avvio) - Il driver è stato identificato come malware, ma non è possibile avviare correttamente il computer senza caricare questo driver. 
  - *Sconosciuto*: questo driver non ha ricevuto l'attestazione dell'applicazione di rilevamento di malware in uso e non è stato classificato dal driver di esecuzione avvio antimalware ad esecuzione anticipata.  

  Se si abilita l'impostazione di questo criterio, è possibile scegliere quali driver di esecuzione avvio inizializzare all'avvio successivo del computer. Se si disabilita o non si configura l'impostazione di questo criterio, i driver di esecuzione avvio identificati come validi, sconosciuti o non validi ma critici per l'avvio vengono inizializzati, mentre l'inizializzazione dei driver identificati come non validi viene ignorata. Se l'applicazione di rilevamento di malware non include un driver di esecuzione avvio antimalware ad esecuzione anticipata o se quest'ultimo driver è stato disabilitato, questa impostazione non ha alcun effetto e tutti i driver di esecuzione avvio vengono inizializzati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067307)   
  
  **Impostazione predefinita**: Buono, Sconosciuto e Bad critical (Non valido ma critico)


## <a name="wi-fi"></a>Wi-Fi  
Per altre informazioni, vedere [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) (Provider di servizi di configurazione dei criteri - Wifi) nella documentazione di Windows.  

- **Blocca Internet condiviso**  
  Specifica se nel dispositivo è possibile la condivisione Internet.   
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067327)   

  **Impostazione predefinita**: Sì  

- **Bloccare la connessione automatica a hotspot Wi-Fi**  
  Consente o impedisce al dispositivo di connettersi automaticamente agli hotspot Wi-Fi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067320)   

  **Impostazione predefinita**: Sì  
  
## <a name="windows-connection-manager"></a>Gestione connessioni Windows  
Per altre informazioni, vedere [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) (Provider di servizi di configurazione dei criteri - WindowsConnectionManager) nella documentazione di Windows.  

- **Bloccare la connessione a reti non di dominio**  
  L'impostazione di questo criterio impedisce ai computer di connettersi contemporaneamente a una rete basata su dominio e a una rete non basata su dominio. Se l'impostazione di questo criterio è abilitata, il computer risponde ai tentativi di connessione di rete automatica e manuale in base alle circostanze seguenti: 
  - Tentativi di connessione automatici Quando il computer è già connesso a una rete basata su dominio, tutti i tentativi di connessione automatica a reti non di dominio vengono bloccati. Quando il computer è già connesso a una rete non basata su dominio, tutti i tentativi di connessione automatica a reti non basate su dominio vengono bloccati. 
  - Tentativi di connessione manuale Quando il computer è già connesso a una rete non basata su dominio o a una rete basata su dominio attraverso supporti diversi da Ethernet e un utente prova a creare una connessione manuale a una rete aggiuntiva in violazione dell'impostazione di questo criterio, la connessione di rete esistente viene interrotta e la connessione manuale viene consentita. Quando il computer è già connesso a una rete non basata su dominio o a una rete basata su dominio tramite Ethernet e un utente tenta di creare una connessione manuale a una rete aggiuntiva in violazione dell'impostazione di questo criterio, la connessione Ethernet esistente viene interrotta e il tentativo di connessione manuale viene bloccato.  

  Se l'impostazione di questo criterio non è configurata o è disabilitata, i computer sono autorizzati a connettersi contemporaneamente a reti di dominio e non di dominio.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067323)  

  **Impostazione predefinita**: Abilitato
  
## <a name="microsoft-defender"></a>Microsoft Defender  
Per altre informazioni, vedere [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (Provider di servizi di configurazione dei criteri - Defender) nella documentazione di Windows.  

- **Analizzare i messaggi di posta in arrivo**  
  Consente o impedisce l'analisi della posta elettronica.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067116)  
  
  **Impostazione predefinita**: Sì  

- **Avviare i processi di tipo figlio per le app di Office**  
  Alle app di Office non verrà consentito di creare processi figlio. Le app includono Word, Excel, PowerPoint, OneNote e Access. Si tratta di un comportamento tipico del malware, in particolare degli attacchi basati su macro che tentano di usare le app di Office per avviare o scaricare file eseguibili dannosi.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067121)  
  
  **Impostazione predefinita**: Blocca
  
- **Tipo di consenso per l'invio di campioni di Defender**  
  Verifica il livello di consenso utente in Microsoft Defender per l'invio di dati. Se il consenso necessario è già stato concesso, Microsoft Defender esegue l'invio. In caso contrario, e se l'utente ha specificato di non chiedere mai, viene avviata l'interfaccia utente per la richiesta del consenso utente (se Defender/AllowCloudProtection è consentito) prima dell'invio di dati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Impostazione predefinita**: Invia automaticamente i campioni sicuri 
  
- **Intervallo di aggiornamento della firma (in ore)**  
  Intervallo di aggiornamento della firma di Defender in ore
  
  **Impostazione predefinita**: 4
  
- **Tipo di esecuzione del payload scaricato tramite script**  
  Tipo di esecuzione del payload scaricato tramite script di Defender
  
  **Impostazione predefinita**: Blocca
  
- **Impedire il tipo di intercettazione delle credenziali**  
  Microsoft Defender Credential Guard usa la sicurezza basata su virtualizzazione per isolare i segreti in modo che solo il software di sistema con privilegi possa accedervi. L'accesso non autorizzato a questi segreti può causare attacchi con furto di credenziali, ad esempio Pass-the-Hash o Pass-The-Ticket. Microsoft Defender Credential Guard impedisce questi attacchi proteggendo gli hash delle password NTLM, i Ticket Granting Ticket Kerberos e le credenziali archiviate dalle applicazioni come credenziali di dominio.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Impostazione predefinita**: Abilitare

- **Tipo di esecuzione del contenuto del messaggio di posta elettronica**  
  Questa regola consente di bloccare l'esecuzione e l'avvio dei tipi di file seguenti da un messaggio di posta elettronica visualizzato in Microsoft Outlook o nella posta sul Web, ad esempio Gmail.com o Outlook.com: file eseguibili, ad esempio file con estensione exe, dll o scr, file di script, ad esempio file PowerShell con estensione ps, file VisualBasic con estensione vbs o file JavaScript con estensione js, e file archivio di script.  
  [Altre informazioni](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#block-executable-content-from-email-client-and-webmail) 
  
  **Impostazione predefinita**: Blocca

- **Avvio di Adobe Reader in un processo figlio**  

  **Impostazione predefinita**: Abilitare

- **Tipo di protezione di rete**  
  Questo criterio consente di attivare la protezione di rete (Blocca/Controlla) o di disattivarla in Microsoft Defender Exploit Guard. La protezione di rete è una funzionalità di Microsoft Defender Exploit Guard che protegge i dipendenti che usano le app dall'accesso a tentativi di phishing, siti che ospitano exploit e contenuti dannosi in Internet. Impedisce anche ai browser di terze parti di connettersi a siti pericolosi. Il tipo di valore è un numero intero. Se si abilita questa impostazione, la protezione di rete verrà attivata e i dipendenti non potranno disattivarla. Il comportamento potrà essere controllato dalle opzioni seguenti: Blocca e Controlla. Se si abilita questo criterio impostando l'opzione "Blocca", gli utenti e le app non possono connettersi a domini dannosi. È possibile visualizzare questa attività in Microsoft Defender Security Center. Se si abilita questo criterio impostando l'opzione "Controlla", gli utenti e le app non potranno connettersi a domini dannosi. Tuttavia, sarà possibile visualizzare comunque questa attività in Microsoft Defender Security Center. Se si disabilita questo criterio, gli utenti e le app potranno connettersi a domini dannosi. Non sarà possibile visualizzare attività di rete in Microsoft Defender Security Center. Se non si configura questo criterio, il blocco di rete è disabilitato per impostazione predefinita.  
  [Altre informazioni](/windows/security/threat-protection/microsoft-defender-atp/enable-network-protection)  
  
  **Impostazione predefinita**: Abilitare
  
- **Giorno pianificato per l'analisi di Defender**  
  Giorno pianificato per l'analisi di Defender.
  
  **Impostazione predefinita**: Ogni giorno
  
- **Protezione fornita dal cloud**  
  Per proteggere al meglio il PC, Microsoft Defender invierà a Microsoft informazioni su qualsiasi problema che si verificherà. Le informazioni saranno analizzate, saranno raccolti altri dettagli sui problemi riscontrati dall'utente corrente e dagli altri clienti. Verranno quindi offerte soluzioni migliorate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Impostazione predefinita**:  Sì  

- **Azione della Protezione da applicazioni potenzialmente di Defender**  
  La funzionalità di protezione da applicazioni potenzialmente indesiderate dell'antivirus Microsoft Defender consente di identificare e bloccare il download e l'installazione delle applicazioni potenzialmente indesiderate negli endpoint di rete. Queste applicazioni non sono considerate virus, malware o altri tipi di minaccia, ma potrebbero agire su endpoint compromettendo le prestazioni e l'uso. Possono essere considerate applicazioni potenzialmente indesiderate anche le applicazioni di dubbia reputazione. Sono applicazioni potenzialmente indesiderate: la creazione di bundle di diversi tipi di software, l'inserimento di annunci nei Web browser, gli strumenti di ottimizzazione per driver e Registro di sistema che rilevano errori e richiedono pagamenti per correggere gli errori, ma rimangono nell'endpoint e non apportano alcuna modifica né alcuna ottimizzazione (noti anche come programmi antivirus non autorizzati). Queste applicazioni possono aumentare il rischio di infezione della rete da parte di malware e incrementare la difficoltà di rilevamento delle infezioni malware e possono causare uno spreco di tempo delle risorse IT per rimuovere il malware dalle applicazioni.  
  [Altre informazioni](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Impostazione predefinita**: Blocca  

- **Tipo di codice macro offuscato in script**  
  Il malware e altre minacce possono tentare di offuscare o nascondere il codice dannoso in alcuni file di script. Questa regola impedisce l'esecuzione degli script offuscati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Impostazione predefinita**: Blocca
  
- **Analizzare le unità rimovibili durante un'analisi completa**  
  Consente a Microsoft Defender di cercare software dannoso e indesiderato in unità rimovibili, ad esempio in unità flash USB, durante un'analisi completa. L'antivirus Microsoft Defender analizza tutti i file nei dispositivi USB prima dell'esecuzione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Impostazione predefinita**: Sì  
  
- **Analizza file di archivio**  
  Analizza file di archivio di Defender.
  
  **Impostazione predefinita**: Sì
  
- **Monitoraggio del comportamento**  
  Consente o impedisce la funzionalità di monitoraggio del comportamento di Microsoft Defender. Integrati in Windows 10, questi sensori raccolgono ed elaborano i segnali comportamentali dal sistema operativo e inviano i dati dei sensori all'istanza cloud isolata privata di Microsoft Defender ATP.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067111)  
  
  **Impostazione predefinita**: Sì

- **Analizzare file aperti da cartelle di rete**  
  Se i file sono di sola lettura, non sarà possibile rimuovere eventuale malware rilevato.
  
  **Impostazione predefinita**: Sì

- **Tipo di processo non attendibile in USB**  
  Questa regola consente agli amministratori di impedire l'esecuzione di file eseguibili non firmati o non attendibili da unità removibili USD, incluse le schede SD.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067100)  
  
  **Impostazione predefinita**: Blocca
  
- **Tipo di inserimento in altri processi per app di Office**  
  Le app di Office, tra cui Word, Excel, PowerPoint e OneNote, non potranno inserire codice in altri processi. Si tratta di un tipico comportamento del malware per eseguire codice malware nel tentativo di nascondere l'attività ai motori di analisi antivirus.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067019)  
  
  **Impostazione predefinita**:  Blocca
  
- **Consentire tipo di importazioni Win32 da codice macro in Office**  
  Il malware può usare il codice della macro in file di Office per importare e caricare le DLL Win32, che possono poi essere usate per eseguire chiamate API e favorire altre infezioni in tutto il sistema. Questa regola tenta di bloccare file di Office che contengono codice della macro che può importare le DLL Win32. Le app incluse sono Word, Excel, PowerPoint e OneNote.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067130)  
  
  **Impostazione predefinita**: Blocca  
  
- **Livello di blocco cloud di Defender**  
  Livello di blocco cloud di Defender.
  
  **Impostazione predefinita**: Non configurato

- **Monitoraggio in tempo reale**  
  Defender richiede il monitoraggio in tempo reale.
  
  **Impostazione predefinita**: Sì
 
- **Avvio di app di comunicazione di Office in un processo figlio**  

  **Impostazione predefinita**:  Abilitare

- **Tipo di contenuto per la creazione o l'avvio di eseguibile nelle app di Office**  
  Questa regola è rivolta ai tipici comportamenti usati da componenti aggiuntivi e script sospetti e dannosi (estensioni) che creano o avviano file eseguibili. Si tratta di una tipica tecnica malware. Le estensioni non possono essere usate dalle app di Office. Queste estensioni usano generalmente Windows Scripting Host (file con estensione wsh) per eseguire script che automatizzano determinate attività oppure aggiungono funzionalità create dall'utente.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Impostazione predefinita**: Blocca

## <a name="microsoft-defender-firewall"></a>Microsoft Defender Firewall  
Per altre informazioni, vedere [2.2.2 FW_PROFILE_TYPE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) nella documentazione relativa ai protocolli di Windows.  

- **Profilo di dominio del firewall**  
  Specifica i profili a cui appartiene la regola: Dominio, Privato o Pubblico. Questo valore rappresenta il profilo per le reti connesse ai domini.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Connessioni in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Connessioni in uscita obbligatorie**  
    **Impostazione predefinita**: Sì 

  - **Notifiche in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Firewall abilitato**  
    **Impostazione predefinita**: Consentito

- **Profilo pubblico del firewall**  
  Specifica i profili a cui appartiene la regola: Dominio, Privato o Pubblico. Questo valore rappresenta il profilo per le reti pubbliche. Tali reti sono classificate come pubbliche dagli amministratori nell'host del server. La classificazione viene stabilita la prima volta che l'host si connette alla rete. Queste reti sono in genere quelle di aeroporti, bar e altri luoghi pubblici, in cui i peer nella rete o l'amministratore di rete non sono attendibili.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067143)  

  - **Connessioni in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Connessioni in uscita obbligatorie**  
    **Impostazione predefinita**: Sì 

  - **Notifiche in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Firewall abilitato**  
    **Impostazione predefinita**: Consentito

  - **Regole di sicurezza connessione da Criteri di gruppo non unite**  
    **Impostazione predefinita**: Sì

  - **Regole dei criteri da Criteri di gruppo non unite**  
    **Impostazione predefinita**: Sì

- **Profilo privato del firewall**  
  Specifica i profili a cui appartiene la regola: Dominio, Privato o Pubblico. Questo valore rappresenta il profilo per le reti private.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067041)  

  - **Connessioni in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Connessioni in uscita obbligatorie**  
    **Impostazione predefinita**: Sì 

  - **Notifiche in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Firewall abilitato**  
    **Impostazione predefinita**: Consentito

## <a name="windows-hello-for-business"></a>Windows Hello for Business  

- **Blocca Windows Hello for Business**  
    Windows Hello for Business è un metodo alternativo per l'accesso a Windows che prevede la sostituzione di password, smart card e smart card virtuali.  
  - Con l'impostazione *Disabilita* i dispositivi eseguono il provisioning di Windows Hello for Business.
  - Con l'impostazione *Non configurato* la baseline non influisce sull'impostazione di criteri del dispositivo. Questo significa che lo stato corrente di Windows Hello for Business in un dispositivo rimane invariato.

  È possibile disabilitare Windows Hello for Business quando si configura la [registrazione di Windows](windows-hello.md) o come parte di un profilo di configurazione del dispositivo per la [protezione delle identità](identity-protection-configure.md).  

  - **Impostazione predefinita**: Abilitato

  Quando questa impostazione è impostata su *Disabilitato*, sono disponibili le impostazioni seguenti.

  - **Consenti l'uso di anti-spoofing avanzato, se disponibile**  
    Con l'impostazione Sì i dispositivi useranno l'anti-spoofing avanzato, se disponibile. Con l'impostazione No l'anti-spoofing verrà bloccato. Con l'impostazione Non configurato verranno rispettate le configurazioni eseguite nel client.  
    [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067192)

    **Impostazione predefinita**: Sì

  - **Lettere minuscole nel PIN**  
    Con l'impostazione *Rendi obbligatorio* il PIN dell'utente deve includere almeno una lettera minuscola.

    **Impostazione predefinita**: Consentito

  - **Caratteri speciali nel PIN**  
    Con l'impostazione *Rendi obbligatorio* il PIN dell'utente deve includere almeno un carattere speciale.

    **Impostazione predefinita**: Consentito

  - **Lunghezza minima del PIN**  
    La lunghezza minima del PIN deve essere compresa tra 4 e 127.

    **Impostazione predefinita**: 6

  - **Lettere maiuscole nel PIN**  
    Con l'impostazione *Rendi obbligatorio* il PIN dell'utente deve includere almeno una lettera maiuscola.

    **Impostazione predefinita**: Consentito


## <a name="windows-ink-workspace"></a>Area Windows Ink  
Per altre informazioni, vedere [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) (Provider del servizio di configurazione dei criteri - WindowsInkWorkspace) nella documentazione di Windows.  

- **Area Ink**  
  Specifica se consentire o meno all'utente di accedere all'area Ink. 
  - *Disabilitato*: l'accesso all'area Ink è disabilitato. La funzionalità è disattivata.
  - *Abilitato*: la funzionalità Area Ink è attivata, ma l'utente non può accedervi sopra la schermata di blocco.
  - *Non configurato*: la funzionalità Area Ink è attivata e l'utente può accedervi sopra la schermata di blocco.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067241)  

  **Impostazione predefinita**: Abilitato
 
## <a name="windows-powershell"></a>Windows PowerShell  
Per altre informazioni, vedere [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) (Provider di servizi di configurazione dei criteri - WindowsPowerShell) nella documentazione di Windows.  

- **Registrazione blocco di script della shell di PowerShell**  
  L'impostazione di questo criterio consente la registrazione di tutti gli input di script di PowerShell nel registro eventi Microsoft-Windows-PowerShell/Operational. Se si abilita l'impostazione di questo criterio, Windows PowerShell registrerà l'elaborazione dei comandi, i blocchi di script, le funzioni e gli script, sia se richiamati in modo interattivo che tramite automazione. Se si disabilita l'impostazione di questo criterio, la registrazione dell'input di script di PowerShell verrà disabilitata. Se si abilita la registrazione delle chiamate di blocchi di script, PowerShell registrerà eventi anche all'avvio o all'interruzione di una chiamata di un comando, un blocco di script, una funzione o uno script. L'abilitazione della registrazione delle chiamate genera un volume elevato di registri eventi. Nota: l'impostazione di questo criterio è presente sia in Configurazione computer che in Configurazione utente nell'Editor Criteri di gruppo. L'impostazione dei criteri in Configurazione computer ha la precedenza sull'impostazione dei criteri in Configurazione utente.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067330)  

  **Impostazione predefinita**: Abilitato

## <a name="whats-changed-in-the-new-template"></a>Modifiche apportate al nuovo modello
Il modello *Baseline della sicurezza MDM per maggio 2019* presenta le modifiche seguenti rispetto al modello di *anteprima*.

### <a name="changes-to-the-baseline-settings"></a>Modifiche alle impostazioni della baseline
Le impostazioni seguenti sono:
- *Nuove* in questa versione più recente della baseline.
- *Rimosse* da questa versione più recente della baseline, ma presenti nella versione precedente.
- *Modificate* in qualche modo rispetto alle impostazioni disponibili nella versione precedente. 

*[Nuova]* [**Sopra la schermata di blocco**](#above-lock):
- **Attiva tramite voce le app dalla schermata di blocco**    

*[Nuova]* [**Gestione applicazioni**](#application-management): 
- **Impedisci il controllo utente sulle installazioni**  
- **Impedisci le installazioni di app MSI con privilegi elevati**  

*[Rimosse]* [**BitLocker**](#bitlocker):  
- BitLocker - Impostazioni dell'unità rimovibile > **Metodo di crittografia**
- **BitLocker - Impostazioni dell'unità fissa** *(tutte le impostazioni)*
- **BitLocker - Impostazioni dell'unità di sistema** *(tutte le impostazioni)*

*[Nuova]* [**Connettività**](#connectivity):
- **Configura l'accesso sicuro ai percorsi UNC**

*[Nuova]* [**Device Guard**](#device-guard):
- **Sicurezza basata sulla virtualizzazione**

*[Nuova]* [**DMA Guard**](#dma-guard):
- **Enumerazione di dispositivi esterni non compatibili con la protezione DMA del kernel**  

*[Nuova]* [**Internet Explorer**](#internet-explorer):
- **Internet Explorer - Area Internet - Aggiornamenti alla barra di stato tramite script**
- **Internet Explorer - Area Internet - Trascinare o copiare e incollare file**  
- **Internet Explorer - Area con restrizioni - Componenti basati su .NET Framework**  
- **Internet Explorer - Area computer locale - Non eseguire programmi antimalware su controlli ActiveX**
- **Internet Explorer - Supporto della crittografia**  

*[Modificata]* [**Internet Explorer**](#internet-explorer):
- **Internet Explorer - Area Internet - Richiesta automatica per il download di file** > il valore predefinito è ora **Disabilitata**. Nell'anteprima l'impostazione predefinita era Abilitata.

*[Nuove]* [**Assistenza remota**](#remote-assistance):  
- **Assistenza remota richiesta** 
  - **Autorizzazione richiesta da Assistenza remota**
  - **Durata massima ticket (valore)**  
  - **Maximum ticket time period** (Durata massima ticket)  
  - **Metodo di invito tramite posta elettronica**


*[Nuova]* [**Microsoft Defender**](#microsoft-defender):
- **Avvio di Adobe Reader in un processo figlio**  
- **Avvio di app di comunicazione di Office in un processo figlio** 

*[Nuove]* [**Microsoft Defender Firewall**](#microsoft-defender-firewall)
- **Profilo di dominio del firewall**  
  - **Connessioni in ingresso bloccate**  
  - **Connessioni in uscita obbligatorie**  
  - **Notifiche in ingresso bloccate**  
  - **Firewall abilitato**  
- **Profilo pubblico del firewall**  
  - **Connessioni in ingresso bloccate**  
  - **Connessioni in uscita obbligatorie**  
  - **Notifiche in ingresso bloccate**  
  - **Firewall abilitato** 
  - **Regole di sicurezza connessione da Criteri di gruppo non unite**   
  - **Regole dei criteri da Criteri di gruppo non unite**  
- **Profilo privato del firewall**  
  - **Connessioni in ingresso bloccate**  
  - **Connessioni in uscita obbligatorie**  
  - **Notifiche in ingresso bloccate**  
  - **Firewall abilitato**  

*[Nuove]* [**Windows Hello for Business**](#windows-hello-for-business):  
- **Blocca Windows Hello for Business**
  - **Consenti l'uso di anti-spoofing avanzato, se disponibile**  
  - **Lettere minuscole nel PIN** 
  - **Caratteri speciali nel PIN** 
  - **Lunghezza minima del PIN**  
  - **Lettere maiuscole nel PIN** 
