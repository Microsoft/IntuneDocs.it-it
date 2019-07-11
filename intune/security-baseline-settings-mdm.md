---
title: Impostazioni delle baseline di sicurezza di Intune per Windows 10
titleSuffix: Microsoft Intune
description: Impostazioni delle baseline di sicurezza di Intune per la gestione di Windows 10
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30cdb6903caa7e1071a6781db13c761e64f8bd7a
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735776"
---
# <a name="mdm-security-baseline-settings-for-intune"></a>Impostazioni della baseline di sicurezza MDM per Intune  

Visualizzare le impostazioni di base della sicurezza MDM supportate da Microsoft Intune per i dispositivi che eseguono Windows 10 o versioni successive. I valori predefiniti per le impostazioni in questa linea di base rappresentano la configurazione consigliata per i dispositivi applicabili e potrebbero non corrispondere alle impostazioni predefinite di base di altre linee di base di sicurezza.  

La versione di base più recente è la baseline della **sicurezza MDM per l'aggiornamento di Spring 2019 (19H1)**  

Per informazioni sulle modifiche apportate nella versione più recente di questa baseline dalla versione precedente, vedere modifiche apportate al [nuovo modello](#whats-changed-in-the-new-template).  

> [!NOTE]  
> Nel giugno del 2019, la baseline della sicurezza MDM di anteprima è stata sostituita dalla versione di *MDM Security Baseline per il modello Spring 2019 Update (19H1)* , che è disponibile a livello generale (non in anteprima). I profili creati prima della disponibilità della baseline di *sicurezza MDM per l'aggiornamento della primavera 2019 (19H1)* non verranno aggiornati in modo da riflettere le impostazioni e i valori presenti nella baseline di sicurezza MDM per la versione Spring 2019 Update (19H1).  Sebbene non sia possibile creare nuovi profili in base al modello di anteprima, è possibile modificare e continuare a usare i profili creati in precedenza che sono basati sul modello di anteprima.   
  
Per informazioni sull'uso delle linee di base di sicurezza con Intune, vedere [usare le linee di base di sicurezza](security-baselines.md).  


   
## <a name="above-lock"></a>Notifiche sulla schermata di blocco  
Per altre informazioni, vedere [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) (Provider di servizi di configurazione dei criteri - AboveLock) nella documentazione di Windows.  

- **Bloccare la visualizzazione delle notifiche di tipo avviso popup**  
  L'impostazione di questo criterio consente di impedire la visualizzazione delle notifiche dell'app nella schermata di blocco. Se si abilita l'impostazione di questo criterio, le notifiche dell'app non vengono visualizzate nella schermata di blocco. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti possono scegliere quali app visualizzano le notifiche nella schermata di blocco.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067101)  

  **Impostazione predefinita**: Sì  

- **Attivazione vocale delle app dalla schermata bloccata**  

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

- **Blocca il controllo utente sulle installazioni**  
  Questa impostazione di criteri consente agli utenti di modificare le opzioni di installazione che in genere sono disponibili solo per gli amministratori di sistema. Se si abilita questa impostazione di criteri, alcune delle funzionalità di sicurezza di Windows Installer verranno ignorate. Consente di completare le installazioni che altrimenti verrebbero interrotte a causa di una violazione della sicurezza. Se questa impostazione viene disabilitata o non configurata, le funzionalità di sicurezza di Windows Installer impediscono agli utenti di modificare le opzioni di installazione generalmente riservate agli amministratori di sistema, ad esempio specificando la directory in cui vengono installati i file. Se Windows Installer rileva che un pacchetto di installazione ha consentito all'utente di modificare un'opzione protetta, l'installazione viene arrestata e viene visualizzato un messaggio. Queste funzionalità di sicurezza funzionano solo quando il programma di installazione è in esecuzione in un contesto di sicurezza con privilegi in cui ha accesso alle directory negate all'utente. Questa impostazione dei criteri è progettata per ambienti meno restrittivi. Può essere usato per aggirare gli errori in un programma di installazione che impedisce l'installazione del software.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067060)  

  **Impostazione predefinita**: Sì

- **Blocca le installazioni di app MSI con privilegi elevati**  
  Questa impostazione dei criteri indica a Windows Installer di usare le autorizzazioni elevate per installare qualsiasi programma nel sistema.  
  - *Se si abilita questa impostazione di criteri*, i privilegi vengono estesi a tutti i programmi. Questi privilegi sono generalmente riservati ai programmi assegnati all'utente (offerti sul desktop), assegnati al computer (installato automaticamente) f o resi disponibili in Installazione applicazioni nel pannello di controllo. Questa impostazione del profilo consente agli utenti di installare programmi che richiedono l'accesso alle directory che l'utente potrebbe non disporre delle autorizzazioni per la visualizzazione o la modifica, incluse le directory su computer con restrizioni.
  - *Se questa impostazione viene disabilitata o non*configurata, il sistema applica le autorizzazioni dell'utente corrente durante l'installazione di programmi che non vengono distribuiti o offerti da un amministratore di sistema. Nota: l'impostazione di questo criterio è presente in entrambe le cartelle Configurazione computer e Configurazione utente. Per rendere effettiva questa impostazione dei criteri, è necessario abilitarla in entrambe le cartelle. Attenzione: gli utenti esperti possono sfruttare le autorizzazioni concesse da questa impostazione di criteri per modificare i privilegi e ottenere l'accesso permanente a file e cartelle con restrizioni. Si noti che non è garantita la sicurezza della versione di configurazione utente di questa impostazione di criteri.  
  
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

## <a name="bitlocker"></a>Bitlocker    
Per altre informazioni, vedere [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) (Provider di servizi di configurazione dei criteri - Bitlocker) nella documentazione di Windows.  

- **Criterio per le unità rimovibili BitLocker**  
  L'impostazione di questo criterio viene usata per controllare il metodo di crittografia e il livello di codifica. I valori di questo criterio determinano il livello di codifica usato da BitLocker per la crittografia. Per una maggiore sicurezza, le aziende potrebbero voler controllare il livello di crittografia (AES-256 è un algoritmo più avanzato rispetto a AES-128). Se si abilita questa impostazione, sarà possibile configurare individualmente un algoritmo di crittografia e un livello di codifica per unità dati fisse, unità del sistema operativo e unità dati rimovibili. Per le unità fisse e del sistema operativo è consigliabile usare l'algoritmo XTS-AES. Per le unità rimovibili è consigliabile usare AES-CBC a 128 bit o AES-CBC a 256 bit se l'unità viene usata in altri dispositivi che non eseguono Windows 10 versione 1511 o successiva. La modifica del metodo di crittografia non produce alcun effetto se l'unità è già crittografata o se la crittografia è in corso. In questi casi, l'impostazione di questo criterio viene ignorata.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067140) 

  Per i criteri di un'unità rimovibile BitLocker, configurare l'impostazione seguente:

    - **Richiedere la crittografia per l'accesso in scrittura**  
      **Impostazione predefinita**: Sì  
  

## <a name="browser"></a>Browser  
Per altre informazioni, vedere [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) (Provider di servizi di configurazione dei criteri - Browser) nella documentazione di Windows.  

- **Richiedere SmartScreen per Microsoft Edge**  
  Per impostazione predefinita, Microsoft Edge usa Windows Defender SmartScreen (attivato) per proteggere gli utenti da potenziali tentativi di phishing e software dannoso. Inoltre, per impostazione predefinita, gli utenti non possono disabilitare (disattivare) Windows Defender SmartScreen. L'abilitazione di questo criterio determina la disattivazione di Windows Defender SmartScreen e ne impedisce l'attivazione da parte degli utenti. Non configurare questo criterio per consentire agli utenti di scegliere di attivare o disattivare Windows Defender SmartScreen.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067029)   
  
  **Impostazione predefinita**: Sì  
  
- **Bloccare l'accesso a siti dannosi**  
  Per impostazione predefinita, Microsoft Edge consente agli utenti di ignorare gli avvisi di Windows Defender SmartScreen relativi a siti potenzialmente dannosi, consentendo di visitare il sito. Con questo criterio, tuttavia, è possibile configurare Microsoft Edge per impedire agli utenti di ignorare gli avvisi, non consentendo di visitare il sito.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067040)   
  
  **Impostazione predefinita**: Sì  
  
- **Bloccare il download di file non verificati**  
  Per impostazione predefinita, Microsoft Edge consente agli utenti di ignorare gli avvisi di Windows Defender SmartScreen relativi a file potenzialmente dannosi, consentendo di continuare a scaricare i file non verificati. L'abilitazione di questo criterio impedisce agli utenti di ignorare gli avvisi, bloccando il download dei file non verificati.  
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
  
  **Impostazione predefinita**: Blocca l'installazione del dispositivo hardware  

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
  
  **Impostazione predefinita**: Blocca l'installazione del dispositivo hardware  

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
    Numero di tipi di elementi complessi (lettere maiuscole e minuscole, numeri e punteggiatura) richiesto per un PIN o una password complessa. L'utilizzo di un PIN prevede le condizioni seguenti per dispositivi mobili e desktop: 1 - Solo cifre 2 - Cifre e caratteri minuscoli obbligatori 3 - Cifre e caratteri minuscoli e maiuscoli obbligatori. Non supportato negli account Microsoft desktop e negli account di dominio. 4 - Cifre, lettere minuscole, lettere maiuscole e caratteri speciali obbligatori. Non supportato nei dispositivi desktop. Il valore predefinito è 1.  
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
    
    **Impostazione predefinita**: Caratteri alfanumerici  

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

## <a name="dma-guard"></a>Protezione DMA  
Per altre informazioni, vedere [Provider di servizi di configurazione dei criteri - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard) nella documentazione di Windows.
- **Enumerazione di dispositivi esterni non compatibili con la protezione DMA del kernel**  
  Questo criterio ha lo scopo di fornire sicurezza aggiuntiva ai dispositivi compatibili con DMA esterno. Consente inoltre maggiore controllo sull'enumerazione di dispositivi esterni idonei per DMA non compatibili con il remapping e/o l'isolamento e il sandboxing della memoria del dispositivo. Questo criterio viene applicato solo quando la protezione DMA del kernel è supportata e abilitata dal firmware del sistema. Il kernel DMA Protection è una funzionalità della piattaforma che non può essere controllata tramite criteri o dall'utente finale. Deve essere supportata dal sistema in fase di produzione. Per verificare se il sistema supporta la protezione con DMA del kernel, controllare il campo protezione DMA kernel nella pagina di riepilogo di MSINFO32. exe.  
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
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione nella finestra di dialogo Opzioni Internet.  
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
  L'impostazione di questo criterio determina se Internet Explorer 11 usa i processi a 64 bit (per maggiore sicurezza) o a 32 bit (per maggiore compatibilità) durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Importante: alcuni controlli ActiveX e alcune barre degli strumenti potrebbero non essere disponibili quando vengono usati processi a 64 bit. Se si abilita l'impostazione di questo criterio, Internet Explorer 11 userà processi schede a 64 bit durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Se si disabilita l'impostazione di questo criterio, Internet Explorer 11 userà processi schede a 32 bit durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Se non si configura l'impostazione di questo criterio, gli utenti possono attivare o disattivare questa funzionalità tramite le impostazioni di Internet Explorer. Questa funzionalità è disattivata per impostazione predefinita.  
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

- **Supporto per la crittografia di Internet Explorer**  
  Questa impostazione criterio consente di disattivare il supporto per Transport Layer Security (TLS) 1,0, TLS 1,1, TLS 1,2, Secure Sockets Layer (SSL) 2,0 o SSL 3,0 nel browser. TLS e SSL sono protocolli che consentono di proteggere la comunicazione tra il browser e il server di destinazione. Quando il browser tenta di configurare una comunicazione protetta con il server di destinazione, il browser e il server negoziano il protocollo e la versione da usare. Il browser e il server tentano di trovare la corrispondenza con l'elenco di protocolli e versioni supportati e selezionano la corrispondenza più desiderata. Se si abilita questa impostazione di criteri, il browser negozia o non negozia un tunnel di crittografia usando i metodi di crittografia selezionati dall'elenco a discesa. Se questa impostazione viene disabilitata o non configurata, l'utente potrà selezionare il metodo di crittografia supportato dal browser.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067057)

  **Impostazione predefinita**: 2 elementi: TLS v 1.1 e TLS v 1.2  
  *Selezionare la freccia rivolta verso il basso per visualizzare le opzioni che è possibile selezionare per questa impostazione.*
  
- **Internet Explorer - Area Internet bloccata - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
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
  
  **Impostazione predefinita**: Abilita  
  
- **Gestione MIME coerente dei processi di Internet Explorer**  
  Internet Explorer contiene comportamenti binari dinamici, ovvero componenti che incapsulano funzionalità specifiche per gli elementi HTML a cui sono associati. L'impostazione di questo criterio determina se l'impostazione Restrizione di sicurezza comportamenti binari è consentita o meno. Se si abilita l'impostazione di questo criterio, i comportamenti binari non saranno consentiti per i processi di Esplora file e Internet Explorer. Se si disabilita l'impostazione di questo criterio, i comportamenti binari saranno consentiti per i processi di Esplora file e Internet Explorer. Se non si configura l'impostazione di questo criterio, i comportamenti binari non saranno consentiti per i processi di Esplora file e Internet Explorer.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067144)  
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Autorizzazioni Java per area con restrizioni**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067132)  
  
  **Impostazione predefinita**: Disabilitare Java  
    
  
- **Internet Explorer - Controlli Active X in modalità protetta**  
  Questa impostazione consente di impedire l'esecuzione di controlli ActiveX in modalità protetta, quando è attivata la modalità protetta avanzata. Se un utente ha un controllo ActiveX installato non compatibile con la modalità protetta avanzata e un sito Web prova a caricare il controllo, Internet Explorer visualizza una notifica e offre la possibilità all'utente di eseguire il sito Web in modalità protetta normale. Questa impostazione disabilita la notifica e impone l'esecuzione in modalità protetta avanzata per tutti i siti Web. La modalità protetta avanzata offre maggiore protezione da siti Web dannosi utilizzando processi a 64 bit nelle versioni a 64 bit di Windows. Per i computer che eseguono almeno Windows 8, la modalità protetta avanzata limita anche i percorsi leggibili da Internet Explorer nel Registro di sistema e nel file system. Quando è abilitata la modalità protetta avanzata e un utente visita un sito Web che prova a caricare un controllo ActiveX non compatibile con la modalità protetta avanzata, Internet Explorer visualizza una notifica e offre la possibilità all'utente di disabilitare la modalità protetta avanzata per tale sito Web specifico. Se si abilita questa impostazione, Internet Explorer non offre all'utente la possibilità di disabilitare la modalità protetta avanzata. Tutti i siti Web in modalità protetta verranno eseguiti in modalità protetta avanzata. Se l'impostazione viene disabilitata o non configurata, Internet Explorer visualizza una notifica per gli utenti e offre la possibilità di eseguire i siti Web con controlli ActiveX non compatibili in modalità protetta normale.  
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
  
  **Impostazione predefinita**: Anonimo  
  
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
  
  **Impostazione predefinita**: Abilita  
  
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
  
  **Impostazione predefinita**: Disabilitare Java 
  
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
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
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
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067050)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
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
  
  **Impostazione predefinita**: Messaggio di richiesta  
  
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
  
  **Impostazione predefinita**: Abilita  
  
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
  
  **Impostazione predefinita**: Abilita 
  
- **Internet Explorer - Area Internet - Inizializzare ed eseguire script controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067170)  
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area con restrizioni - Blocco SmartScreen**   
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.  
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
  
  **Impostazione predefinita**: Messaggio di richiesta  
  
- **Internet Explorer - Area con restrizioni - Autorizzare l'esecuzione di VBscript**   
  L'impostazione di questo criterio consente di stabilire se possono essere eseguiti VBScript nelle pagine dell'area specificata in Internet Explorer. Se è stato selezionato Abilita nella casella a discesa, VBScript viene eseguito senza richiedere l'intervento dell'utente. Se è stato selezionato Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di VBScript. Se è stato selezionato Disabilita nella casella a discesa, viene impedita l'esecuzione di VBScript. Se si disabilita o non si configura l'impostazione di questo criterio, viene impedita l'esecuzione di VBScript.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067173)  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Trascinare contenuto da domini diversi tra finestre**  
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.  
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
  
- **Internet Explorer gli scriptlet area Internet**  
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
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067166)   

  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Aggiunta di siti da parte degli utenti**  
  Impedisce agli utenti di aggiungere o eliminare siti nelle aree di sicurezza. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, le impostazioni di gestione dei siti per le aree di sicurezza verranno disabilitate. (Per visualizzare le impostazioni di gestione dei siti per le aree di sicurezza, nella finestra di dialogo Opzioni Internet fare clic sulla scheda Sicurezza e quindi sul pulsante Siti). Se si disabilita o non si configura questo criterio, gli utenti potranno aggiungere o eliminare siti Web nelle aree Siti attendibili e Siti con restrizioni nonché modificare le impostazioni relative all'area Intranet locale. Questo criterio impedisce agli utenti di modificare le impostazioni di gestione dei siti per le aree di sicurezza configurate dall'amministratore. Nota: il criterio "Disabilita la scheda Sicurezza", disponibile in Configurazione utente\Modelli amministrativi\Componenti di Windows\Internet Explorer\Pannello di controllo Internet, che rimuove la scheda Sicurezza dall'interfaccia, ha priorità rispetto al criterio appena descritto. Se il criterio "Disabilita la scheda Programmi" è abilitato, questo criterio verrà ignorato. Vedere anche il criterio "Aree di sicurezza: utilizza solo le impostazioni del computer".  
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
  Impedisce agli utenti di modificare le impostazioni dell'area di sicurezza. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, il pulsante Livello personalizzato e il cursore del livello di sicurezza nella scheda Sicurezza della finestra di dialogo Opzioni Internet sono disabilitati. Se si disabilita questo criterio o non lo si configura, gli utenti possono modificare le impostazioni delle aree di sicurezza. Questo criterio impedisce agli utenti di modificare le impostazioni dell'area di sicurezza stabilite dall'amministratore. Nota: il criterio "Disabilita la scheda Sicurezza", disponibile in Configurazione utente\Modelli amministrativi\Componenti di Windows\Internet Explorer\Pannello di controllo Internet, che rimuove la scheda Sicurezza da Internet Explorer nel Pannello di controllo, ha priorità rispetto al criterio appena descritto. Se il criterio "Disabilita la scheda Programmi" è abilitato, questo criterio verrà ignorato. Vedere anche il criterio "Aree di sicurezza: utilizza solo le impostazioni del computer".  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067155)  
    
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Modalità protetta**  
  L'impostazione di questo criterio consente di attivare la modalità protetta. La modalità protetta consente di proteggere Internet Explorer da attacchi correlati ai rischi di sicurezza attraverso una riduzione delle posizioni in cui Internet Explorer può scrivere all'interno del Registro di sistema e del file system. Se si abilita l'impostazione di questo criterio, la modalità protetta viene attivata. L'utente non può disattivare la modalità protetta. Se si disabilita l'impostazione di questo criterio, la modalità protetta viene disattivata. L'utente non può attivare la modalità protetta. Se non si configura l'impostazione di questo criterio, l'utente può attivare o disattivare la modalità protetta.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067080)  
  
  **Impostazione predefinita**: Abilita  
  
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
  La modalità protetta avanzata offre maggiore protezione da siti Web dannosi utilizzando processi a 64 bit nelle versioni a 64 bit di Windows. Per i computer che eseguono almeno Windows 8, la modalità protetta avanzata limita anche i percorsi leggibili da Internet Explorer nel Registro di sistema e nel file system. Se si abilita questa impostazione, viene attivata la modalità protetta avanzata. Qualsiasi area per cui è abilitata la modalità protetta utilizzerà la modalità protetta avanzata. Gli utenti non potranno disattivare la modalità protetta avanzata. Se si disabilita questa impostazione, viene disattivata la modalità protetta avanzata. Qualsiasi area per cui è abilitata la modalità protetta utilizzerà la versione della modalità protetta introdotta in Internet Explorer 7 per Windows Vista. Se questa impostazione non viene configurata, gli utenti possono attivare o disattivare la modalità protetta avanzata nella scheda Avanzate della finestra di dialogo Opzioni Internet.  
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
  Quando abilitata, questa impostazione di sicurezza limita l'accesso anonimo alle condivisioni e alle named pipe alle impostazioni per: (1) named pipe cui è possibile accedere in modo anonimo (2) condivisioni cui è possibile accedere in modo anonimo.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067212)  
  
  **Impostazione predefinita**: Sì  
  
- **Sicurezza sessione minima per server basati su NTLM SSP**  
  Questa impostazione di sicurezza consente ai server di richiedere la negoziazione della crittografia a 128 bit e/o della sicurezza di sessione NTLMv2. Tali valori dipendono dal valore dell'impostazione di sicurezza Livello di autenticazione di LAN Manager. Opzioni disponibili: Richiedi protezione sessione NTLMv2: se l'integrità del messaggio non viene negoziata, la connessione non riesce. Richiedi crittografia a 128 bit. Se la crittografia avanzata (a 128 bit) non viene negoziata, la connessione non riesce.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067246) 
  
  **Impostazione predefinita**: Richiedi NTLM V2 e crittografia a 128 bit  
  
- **Minuti di inattività della schermata di blocco prima dell'attivazione dello screen saver**  
  Il sistema rileva l'inattività di una sessione di accesso e, se il tempo di inattività supera il limite di inattività, verrà eseguito lo screen saver bloccando la sessione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067210)  
  
  **Impostazione predefinita**: 15
  
- **Richiedere al client di aggiungere sempre la firma digitale alle comunicazioni** Questa impostazione di sicurezza determina se tutto il traffico inviato sul canale sicuro dal membro di dominio deve essere firmato o crittografato. Quando si aggiunge un computer a un dominio, viene creato un account computer. All'avvio il sistema usa quindi la password di tale account computer per creare un canale sicuro con un controller di dominio del proprio dominio. Il canale sicuro viene usato per eseguire operazioni come l'autenticazione pass-through NTLM, la ricerca dei nomi SID LSA e altre. Questa impostazione determina se tutto il traffico inviato sul canale sicuro dal membro di dominio soddisfa i requisiti di sicurezza minimi. In particolare, specifica se tutto il traffico inviato sul canale sicuro dal membro di dominio deve essere firmato o crittografato. Se questo criterio è abilitato, il canale sicuro viene creato esclusivamente se la firma o la crittografia di tutto il traffico sul canale sicuro viene negoziata. Se questo criterio è disabilitato, la firma o la crittografia di tutto il traffico sul canale sicuro viene negoziata con il controller di dominio. In tal caso, il livello di firma o crittografia dipende dalla versione del controller di dominio e dalle impostazioni dei due criteri seguenti, ovvero Membro di dominio: aggiunta crittografia o firma digitale ai dati del canale sicuro (quando possibile) e Membro di dominio: aggiunta firma digitale ai dati del canale sicuro (quando possibile).  
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
    - *Richiedi le credenziali nel desktop protetto* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente del desktop protetto dovrà immettere il nome utente e la password di un utente con i privilegi necessari. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio più elevato disponibile. 
    - *Richiedi il consenso nel desktop protetto* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente del desktop protetto dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile. 
    - *Richiedi credenziali* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà inserire un nome utente e una password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente. 
    - *Richiedi il consenso* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile.  
    - *Richiedi il consenso per file binari non Windows* - Quando un'operazione per un'applicazione non Microsoft richiede l'elevazione dei privilegi, sul desktop protetto l'utente dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile. 
  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067215)   
  
  **Impostazione predefinita**: Richiedi il consenso nel desktop sicuro
  
- **Sicurezza sessione minima per client basati su NTLM SSP**  
  Questa impostazione di sicurezza consente ai client di richiedere la negoziazione della crittografia a 128 bit e/o della sicurezza di sessione NTLMv2. Tali valori dipendono dal valore dell'impostazione di sicurezza Livello di autenticazione di LAN Manager. Le opzioni disponibili sono:
  - *Richiedi sicurezza sessione NTLMv2* - Se il protocollo NTLMv2 non viene negoziato, la connessione non riuscirà. 
  - *Richiedi crittografia a 128 bit* Se la crittografia avanzata (a 128 bit) non viene negoziata, la connessione non riesce.
  - *Richiedi NTLM V2 e la crittografia a 128 bit*.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067324)  

  **Impostazione predefinita**: Richiedi NTLM V2 e la crittografia a 128 bit
  
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
  - *Rifiuta automaticamente le richieste di elevazione dei privilegi* - Quando un'operazione richiede l'elevazione dei privilegi, viene visualizzato un messaggio di errore di accesso negato che può essere configurato. In un'organizzazione in cui i desktop vengono eseguiti come account utente standard, questa impostazione può contribuire a ridurre le chiamate al supporto tecnico. 
  - *Richiedi le credenziali nel desktop protetto* - Quando un'operazione richiede l'elevazione dei privilegi, sul desktop protetto l'utente dovrà immettere un nome utente e una password differenti. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente. 
  - *Richiedi credenziali* - Quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà inserire un nome utente e una password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente.  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067183)  
  
  **Impostazione predefinita**: Rifiuta automaticamente le richieste di elevazione dei privilegi
  
- **Richiedere la modalità Approvazione amministratore per gli amministratori**  
  L'impostazione di questo criterio specifica il comportamento di tutte le impostazioni dei criteri di Controllo dell'account utente per il computer. Se questa impostazione viene modificata, è necessario riavviare il computer. Le opzioni disponibili sono:   
  - *Non configurato* - La modalità Approvazione amministratore e i criteri correlati di Controllo dell'account utente sono disattivati. Nota: se questa impostazione è disattivata, Centro sicurezza PC segnala che la sicurezza complessiva del sistema operativo è ridotta. 
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
  - *Sì* - L'account predefinito Administrator usa la modalità Approvazione amministratore. Per impostazione predefinita, per qualunque operazione che richiede l'elevazione dei privilegi l'utente dovrà scegliere se autorizzare o rifiutare l'esecuzione. 
  - *Non configurato* - L'account predefinito Administrator esegue tutte le applicazioni con privilegi amministrativi completi. 

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067186)  

  **Impostazione predefinita**: Sì
  
- **Consentire le applicazioni con accesso all'interfaccia utente per percorsi sicuri**  
  L'impostazione di questo criterio specifica se i programmi con accesso all'interfaccia utente (UIAccess o UIA) possono disabilitare automaticamente il desktop protetto per le richieste di elevazione dei privilegi provenienti da un utente standard. 
  - *Sì* - I programmi con Automazione interfaccia utente, incluso Assistenza remota di Windows, disabilitano automaticamente il desktop protetto per le richieste di elevazione dei privilegi. Se non si disabilita l'impostazione del criterio "Controllo account utente: alla richiesta di elevazione passa al desktop sicuro", le richieste vengono visualizzate sul desktop dell'utente interattivo invece che sul desktop protetto. 
  - *Non configurato* - Il desktop protetto può essere disabilitato solo dall'utente del desktop interattivo oppure disabilitando l'impostazione del criterio "Controllo account utente: alla richiesta di elevazione passa al desktop sicuro".  

  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067185)  

  **Impostazione predefinita**: Sì

- **Rilevare installazioni di applicazioni e richiedere l'elevazione dei privilegi**  
  L'impostazione di questo criterio specifica il comportamento del rilevamento di installazioni di applicazioni nel computer. Le opzioni disponibili sono: 
  - *Abilitato* - Per i pacchetti di installazione delle applicazioni che richiedono l'elevazione dei privilegi, l'utente dovrà immettere nome utente e password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente. 
  - *Disabilitato* - I pacchetti di installazione delle applicazioni non vengono rilevati e non viene richiesta l'elevazione dei privilegi. È consigliabile disattivare questa impostazione nel caso di un'organizzazione che esegue desktop utente standard e utilizza tecnologie di installazione delegata, ad esempio Estensione dell'installazione software basata su Criteri di gruppo o Systems Management Server (SMS), in quanto il rilevamento dei programmi di installazione non è necessario.  
  
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
  Questa impostazione criterio consente di attivare o disattivare l'assistenza remota richiesta (Richiedi) in questo computer. 
  - *Se si abilita questa impostazione*relativa ai criteri, gli utenti di questo computer possono utilizzare la posta elettronica o il trasferimento di file per chiedere assistenza a un utente. Inoltre, gli utenti possono utilizzare i programmi di messaggistica immediata per consentire le connessioni al computer ed è possibile configurare altre impostazioni di assistenza remota. 
  - *Se si disabilita questa impostazione di criteri*, gli utenti di questo computer non potranno utilizzare la posta elettronica o il trasferimento di file per chiedere assistenza. Inoltre, gli utenti non possono utilizzare i programmi di messaggistica immediata per consentire le connessioni a questo computer. 
  - *Se questa impostazione di criteri non viene*configurata, gli utenti possono attivare o disattivare l'assistenza remota richiesta (Richiedi) in proprietà di sistema nel pannello di controllo. Gli utenti possono anche configurare le impostazioni di assistenza remota. 

  Se si abilita questa impostazione di criteri, sono disponibili due modi per consentire agli helper di fornire assistenza remota: "Consenti agli helper di visualizzare solo il computer" o "Consenti agli helper di controllare in remoto il computer". L'impostazione dei criteri "tempo massimo ticket" consente di impostare un limite per il periodo di tempo durante il quale un invito di assistenza remota creato tramite posta elettronica o trasferimento di file può rimanere aperto. L'impostazione "selezionare il metodo per l'invio di inviti tramite posta elettronica" specifica lo standard di posta elettronica da usare per inviare gli inviti di assistenza remota. A seconda del programma di posta elettronica, è possibile usare lo standard mailto (il destinatario dell'invito si connette tramite un collegamento a Internet) o lo standard SMAPI (Simple MAPI) (l'invito è allegato al messaggio di posta elettronica). Questa impostazione dei criteri non è disponibile in Windows Vista, poiché SMAPI è l'unico metodo supportato. Se si abilita questa impostazione di criteri, è necessario abilitare anche le eccezioni appropriate del firewall per consentire le comunicazioni di assistenza remota.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067198)

  **Impostazione predefinita**: Disabilita assistenza remota

  Quando si imposta l'abilitazione dell' *assistenza remota*, configurare le impostazioni aggiuntive seguenti:  
  - **Autorizzazione richiesta assistenza remota**  
    **Impostazione predefinita**: Visualizza  

  - **Valore tempo massimo ticket**  
    **Impostazione predefinita**: *Non configurato*  

  - **Periodo di tempo massimo del ticket**  
    **Impostazione predefinita**: minuti    

  - **Metodo di invito tramite posta elettronica**  
    **Impostazione predefinita**: MAPI semplice

  
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
  - *Autenticato senza eccezioni* consente solo ai client RPC autenticati (in base alla definizione precedente) di connettersi ai server RPC in esecuzione nel computer in cui l'impostazione del criterio viene applicata. Non sono consentite eccezioni. Nota: l'impostazione di questo criterio viene applicata solo dopo il riavvio del sistema.  

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
  
  **Impostazione predefinita**: Validi, sconosciuti e dannosi ma fondamentali


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
  
## <a name="windows-defender"></a>Windows Defender  
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
  Verifica il livello di consenso utente in Windows Defender per l'invio di dati. Se il consenso necessario è già stato concesso, Windows Defender esegue l'invio. In caso contrario, e se l'utente ha specificato di non chiedere mai, viene avviata l'interfaccia utente per la richiesta del consenso utente (se Defender/AllowCloudProtection è consentito) prima dell'invio di dati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067131)  
  
  **Impostazione predefinita**: Invia i campioni sicuri automaticamente 
  
- **Intervallo di aggiornamento della firma (in ore)**  
  Intervallo di aggiornamento della firma di Defender in ore
  
  **Impostazione predefinita**: 4
  
- **Tipo di esecuzione del payload scaricato tramite script**  
  Tipo di esecuzione del payload scaricato tramite script di Defender
  
  **Impostazione predefinita**: Blocca
  
- **Impedire il tipo di intercettazione delle credenziali**  
  Windows Defender Credential Guard usa la protezione basata su virtualizzazione per isolare i segreti in modo che solo il software di sistema con privilegi possa accedervi. L'accesso non autorizzato a questi segreti può provocare attacchi di furto delle credenziali, ad esempio Pass-the-Hash o Pass-The-Ticket. Windows Defender Credential Guard impedisce questi attacchi proteggendo gli hash delle password NTLM, Kerberos Ticket Granting Tickets e le credenziali archiviate dalle applicazioni come credenziali di dominio.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067065)  
  
  **Impostazione predefinita**: Abilita

- **Tipo di esecuzione del contenuto del messaggio di posta elettronica**  
  Questa regola consente di bloccare l'esecuzione e l'avvio dei tipi di file seguenti da un messaggio di posta elettronica visualizzato in Microsoft Outlook o nella posta sul Web, ad esempio Gmail.com oppure Outlook.com: file eseguibili, ad esempio con estensione exe, dll o scr, file di script, ad esempo file di PowerShell con estensione ps, file di VisualBasic con estensione vbs o file JavaScript con estensione js, e file di archivio di script.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067063)  
  
  **Impostazione predefinita**: Blocca

- **Avvio di Adobe Reader in un processo figlio**  

  **Impostazione predefinita**: Abilita

- **Tipo di protezione di rete**  
  Questo criterio consente di attivare la protezione di rete (Blocca/Controlla) o di disattivarla in Windows Defender Exploit Guard. La protezione di rete è una funzionalità di Windows Defender Exploit Guard che protegge i dipendenti che usano le app dall'accesso a tentativi di phishing, siti che ospitano exploit e contenuti dannosi in Internet. Impedisce anche ai browser di terze parti di connettersi a siti pericolosi. Il tipo di valore è un numero intero. Se si abilita questa impostazione, la protezione di rete verrà attivata e i dipendenti non potranno disattivarla. Il comportamento potrà essere controllato dalle opzioni seguenti: Blocca e Controlla. Se si abilita questo criterio impostando l'opzione "Blocca", gli utenti e le app non possono connettersi a domini dannosi. È possibile visualizzare questa attività in Windows Defender Security Center. Se si abilita questo criterio impostando l'opzione "Controlla", gli utenti e le app non potranno connettersi a domini dannosi. Sarà possibile visualizzare anche questa attività in Windows Defender Security Center. Se si disabilita questo criterio, gli utenti e le app potranno connettersi a domini dannosi. Non sarà possibile visualizzare attività di rete in Windows Defender Security Center. Se non si configura questo criterio, il blocco di rete è disabilitato per impostazione predefinita.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067102)  
  
  **Impostazione predefinita**: Abilita
  
- **Giorno pianificato per l'analisi di Defender**  
  Giorno pianificato per l'analisi di Defender.
  
  **Impostazione predefinita**: Ogni giorno
  
- **Protezione fornita dal cloud**  
  Per proteggere al meglio il PC, Windows Defender invierà a Microsoft informazioni su qualsiasi problema che si verificherà. Le informazioni saranno analizzate, saranno raccolti altri dettagli sui problemi riscontrati dall'utente corrente e dagli altri clienti. Verranno quindi offerte soluzioni migliorate.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067039)
  
  **Impostazione predefinita**: Sì  

- **Azione della Protezione da applicazioni potenzialmente di Defender**  
  La funzionalità Protezione da applicazioni potenzialmente indesiderate in Windows Defender Antivirus consente di identificare e bloccare il download e l'installazione delle applicazioni potenzialmente indesiderate negli endpoint in rete. Queste applicazioni non sono considerate virus, malware o altri tipi di minaccia, ma potrebbero agire su endpoint compromettendo le prestazioni e l'uso. Possono essere considerate applicazioni potenzialmente indesiderate anche le applicazioni di dubbia reputazione. Sono applicazioni potenzialmente indesiderate la creazione di bundle di diversi tipi di software, l'inserimento di annunci nei Web browser, gli strumenti di ottimizzazione per driver e Registro di sistema che rilevano errori e richiedono pagamenti per correggere gli errori, ma rimangono nell'endpoint e non apportano alcuna modifica né alcuna ottimizzazione (noti anche come programmi antivirus non autorizzati). Queste applicazioni possono aumentare il rischio di infezione della rete da parte di malware e incrementare la difficoltà di rilevamento delle infezioni malware e possono causare uno spreco di tempo delle risorse IT per rimuovere il malware dalle applicazioni.  
  [Altre informazioni](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)    
  
  **Impostazione predefinita**: Blocca  

- **Tipo di codice macro offuscato in script**  
  Il malware e altre minacce possono tentare di offuscare o nascondere il codice dannoso in alcuni file di script. Questa regola impedisce l'esecuzione degli script offuscati.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067026)  
  
  **Impostazione predefinita**: Blocca
  
- **Analizzare le unità rimovibili durante un'analisi completa**  
  Consente a Defender di Windows di cercare software dannoso e indesiderato in unità rimovibili, ad esempio in unità flash, durante un'analisi completa. Windows Defender Antivirus analizza tutti i file nei dispositivi USB prima dell'esecuzione.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067036)  
  
  **Impostazione predefinita**: Sì  
  
- **Analizza file di archivio**  
  Analizza file di archivio di Defender.
  
  **Impostazione predefinita**: Sì
  
- **Monitoraggio del comportamento**  
  Consente o impedisce la funzionalità di monitoraggio del comportamento di Windows Defender. Integrati in Windows 10, questi sensori raccolgono ed elaborano i segnali comportamentali dal sistema operativo e inviano i dati dei sensori all'istanza cloud isolata privata di Microsoft Defender ATP.  
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
  
  **Impostazione predefinita**: Blocca
  
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

  **Impostazione predefinita**: Abilita

- **Tipo di contenuto per la creazione o l'avvio di eseguibile nelle app di Office**  
  Questa regola è rivolta ai tipici comportamenti usati da componenti aggiuntivi e script sospetti e dannosi (estensioni) che creano o avviano file eseguibili. Si tratta di una tipica tecnica malware. Le estensioni non possono essere usate dalle app di Office. Queste estensioni usano generalmente Windows Scripting Host (file con estensione wsh) per eseguire script che automatizzano determinate attività oppure aggiungono funzionalità create dall'utente.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067108)  
  
  **Impostazione predefinita**: Blocca

## <a name="windows-defender-firewall"></a>Windows Defender Firewall  
Per ulteriori informazioni, vedere [2.2.2 FW_PROFILE_TYPOE]( https://docs.microsoft.com/openspecs/windows_protocols/ms-fasp/7704e238-174d-4a5e-b809-5f3787dd8acc) nella documentazione relativa ai protocolli di Windows.  

- **Dominio del profilo firewall**  
  Specifica i profili a cui appartiene la regola, ovvero dominio, privato e pubblico. Questo valore rappresenta il profilo per le reti connesse ai domini.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2066796)  

  - **Connessioni in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Connessioni in uscita obbligatorie**  
    **Impostazione predefinita**: Sì 

  - **Notifiche in ingresso bloccate**  
    **Impostazione predefinita**: Sì

  - **Firewall abilitato**  
    **Impostazione predefinita**: Consentito

- **Profilo del firewall pubblico**  
  Specifica i profili a cui appartiene la regola, ovvero dominio, privato e pubblico. Questo valore rappresenta il profilo per le reti pubbliche. Tali reti sono classificate come pubbliche dagli amministratori nell'host del server. La classificazione viene stabilita la prima volta che l'host si connette alla rete. Queste reti sono in genere quelle di aeroporti, bar e altri luoghi pubblici, in cui i peer nella rete o l'amministratore di rete non sono attendibili.  
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

- **Profilo del firewall privato**  
  Specifica i profili a cui appartiene la regola, ovvero dominio, privato e pubblico. Questo valore rappresenta il profilo per le reti private.  
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
- **Richiedi anti-spoofing avanzato, se disponibile**  
  In caso affermativo, i dispositivi utilizzeranno l'anti-spoofing avanzato, se disponibile. Se no, l'anti-spoofing verrà bloccato. Non configurata rispetta le configurazioni eseguite sul client.  
  [Altre informazioni](https://go.microsoft.com/fwlink/?linkid=2067192)

  **Impostazione predefinita**: Sì

- **Configurare Windows Hello for Business**   
  Windows Hello for Business è un metodo alternativo per l'accesso a Windows che prevede la sostituzione di password, smart card e smart card virtuali. Se si abilita o non si configura questo criterio, il dispositivo esegue il provisioning di Windows Hello for Business. Se si disabilita questo criterio, il dispositivo non effettua il provisioning di Windows Hello for Business per alcun utente.

  **Impostazione predefinita**: Sì

- **Richiedi lettere minuscole nel PIN**  
  Se necessario, il PIN dell'utente deve includere almeno una lettera minuscola.

  **Impostazione predefinita**: Consentito

- **Richiedi caratteri speciali nel PIN**  
  Se necessario, il PIN dell'utente deve includere almeno un carattere speciale.

  **Impostazione predefinita**: Consentito

- **Lunghezza minima del PIN**  
  La lunghezza minima del PIN deve essere compresa tra 4 e 127.

  **Impostazione predefinita**: 6

- **Richiedi lettere maiuscole nel PIN**  
  Se necessario, il PIN dell'utente deve includere almeno una lettera maiuscola.

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
La *baseline di sicurezza MDM per il modello di aggiornamento Spring 2019 (19H1)* presenta le modifiche seguenti rispetto al modello di *Anteprima* .

### <a name="changes-to-the-baseline-settings"></a>Modifiche alle impostazioni di base
Le impostazioni seguenti sono:
- *Nuovo* in questa versione più recente della linea di base.
- *Rimossi* da questa versione di base più recente, ma erano presenti nella versione precedente.
- *Revisione* del modo in cui le impostazioni sono state visualizzate nella versione precedente. 

*[Nuovo]* [**Blocco precedente**](#above-lock):
- **Attivazione vocale delle app dalla schermata bloccata**    

*[Nuovo]* [**Gestione delle applicazioni**](#application-management): 
- **Blocca il controllo utente sulle installazioni**  
- **Blocca le installazioni di app MSI con privilegi elevati**  

*[Rimosso]* [**BitLocker**](#bitlocker):  
- Criteri dell'unità rimovibile di bit Locker > **metodo di crittografia**
- **Criteri di unità fissa del blocco di bit** *(tutte le impostazioni)*
- **Criteri dell'unità di sistema di bit Locker** *(tutte le impostazioni)*

*[Nuovo]* [**Connettività**](#connectivity):
- **Configurare l'accesso sicuro ai percorsi UNC**

*[Nuovo]* [**Device Guard**](#device-guard):
- **Sicurezza basata sulla virtualizzazione**


*[Nuovo]* [**Protezione DMA**](#dma-guard):
- **Enumerazione di dispositivi esterni non compatibili con la protezione DMA del kernel**  

*[Nuovo]* [**Internet Explorer**](#internet-explorer):
- **Internet Explorer - Area Internet - Aggiornamenti alla barra di stato tramite script**
- **Internet Explorer - Area Internet - Trascinare o copiare e incollare file**  
- **Internet Explorer - Area con restrizioni - Componenti basati su .NET Framework**  
- **Internet Explorer - Area computer locale - Non eseguire programmi antimalware su controlli ActiveX**
- **Supporto per la crittografia di Internet Explorer**  

*[Modificato]* [**Internet Explorer**](#internet-explorer):
- La **richiesta automatica dell'area Internet di Internet Explorer per il download dei file** > il valore predefinito è **disabilitata**. In anteprima questa impostazione è stata impostata su abilitato.

*[Nuovo]* [**Assistenza remota**](#remote-assistance):  
- **Assistenza remota richiesta** 
  - **Autorizzazione richiesta assistenza remota**
  - **Valore tempo massimo ticket**  
  - **Periodo di tempo massimo del ticket**  
  - **Metodo di invito tramite posta elettronica**


*[Nuovo]* [**WIndows Defender**](#windows-defender):
- **Avvio di Adobe Reader in un processo figlio**  
- **Avvio di app di comunicazione di Office in un processo figlio** 

*[Nuovo]* [**Windows Defender Firewall**](#windows-defender-firewall)
- **Dominio del profilo firewall**  
  - **Connessioni in ingresso bloccate**  
  - **Connessioni in uscita obbligatorie**  
  - **Notifiche in ingresso bloccate**  
  - **Firewall abilitato**  
- **Profilo del firewall pubblico**  
  - **Connessioni in ingresso bloccate**  
  - **Connessioni in uscita obbligatorie**  
  - **Notifiche in ingresso bloccate**  
  - **Firewall abilitato** 
  - **Regole di sicurezza connessione da Criteri di gruppo non unite**   
  - **Regole dei criteri da Criteri di gruppo non unite**  
- **Profilo del firewall privato**  
  - **Connessioni in ingresso bloccate**  
  - **Connessioni in uscita obbligatorie**  
  - **Notifiche in ingresso bloccate**  
  - **Firewall abilitato**  

*[Nuovo]* [**Windows Hello for Business**](#windows-hello-for-business):  
- **Richiedi anti-spoofing avanzato, se disponibile**  
- **Configurare Windows Hello for Business**  
- **Richiedi lettere minuscole nel PIN** 
- **Richiedi caratteri speciali nel PIN** 
- **Lunghezza minima del PIN**  
- **Richiedi lettere maiuscole nel PIN** 



<!-- The following settings were available in the Preview Baseline.   

   
## Above Lock  
For more information, see [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) in the Windows documentation.  

- **Block display of toast notifications**  
  This policy setting allows you to prevent app notifications from appearing on the lock screen. If you enable this policy setting, no app notifications are displayed on the lock screen. If you disable or don't configure this policy setting, users can choose which apps display notifications on the lock screen.
  
  **Default**: Yes  

## App Runtime    
For more information, see [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) in the Windows documentation.  

- **Microsoft accounts optional for Windows Store apps**  
  This policy setting lets you control whether Microsoft accounts are optional for Windows Store apps that require an account to sign in. This policy only affects Windows Store apps that support it. If you enable this policy setting, Windows Store apps that typically require a Microsoft account to sign in will allow users to sign in with an enterprise account instead. If you disable or don't configure this policy setting, users must sign in with a Microsoft account.  
  
  **Default**: Enabled  

## Application Management   
For more information, see [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) in the Windows documentation.  

- **Block game DVR (desktop only)**  
  Configures whether recording and broadcasting of games is allowed.
  
  **Default**: Yes  

## Auto Play   
For more information, see [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) in the Windows documentation.  

- **Auto play default auto run behavior**  
  This setting affects the default behavior for Autorun commands. Autorun commands are stored in autorun.inf files and can launch installation programs or other routines. When *Enabled*, Administrators can change the default autorun behavior on a device that runs Windows Vista or later. Behavior can be set to: a) completely disable autorun commands, or b) revert back to pre-Windows Vista behavior of automatically executing the autorun command. When set to *Disabled* or *Not Configured*, devices that run Windows Vista or later prompt the user as to whether an autorun command should run.
  
  **Default**: Do not execute  
  
- **Auto play mode**  
  This policy setting allows you to turn off the Autoplay feature. Autoplay begins reading from a drive as soon as you insert media in the drive. As a result, the setup file of programs and the music on audio media start immediately. Prior to Windows XP SP2, Autoplay is disabled by default on removable drives, such as the floppy disk drive (but not the CD-ROM drive), and on network drives. Starting with Windows XP SP2, Autoplay is enabled for removable drives as well, including Zip drives and some USB mass storage devices. If you enable this policy setting, Autoplay is disabled on CD-ROM and removable media drives, or disabled on all drives. This policy setting disables Autoplay on additional types of drives. You can't use this setting to enable Autoplay on drives on which it's disabled by default. If you disable or don't configure this policy setting, AutoPlay is enabled. Note: This policy setting appears in both the Computer Configuration and User Configuration folders. If the policy settings conflict, the policy setting in Computer Configuration takes precedence over the policy setting in User Configuration.
  
  **Default**: Disabled

- **Block auto play for non-volume devices**  
  This policy setting disallows AutoPlay for MTP devices like cameras or phones. If you enable this policy setting, AutoPlay isn't allowed for MTP devices like cameras or phones. If you disable or don't configure this policy setting, AutoPlay is enabled for non-volume devices.
  
  **Default**: Enabled  

## Bitlocker    
For more information, see [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) in the Windows documentation.  

- **Bit locker removable drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you'll be able to configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.

  For Bit locker removable drive policy, configure the following settings:

    - **Require encryption for write access**  
      **Default**: Yes  
  
    - **Encryption method**  
      **Default**: AES 256bit CBC  

- **Bit locker fixed drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  
 
   For Bit locker fixed drive policy, configure the following settings: 
   - **Encryption method**
     **Default**: AES 256bit XTS  

- **Bit locker system drive policy**  
  This policy setting is used to control the encryption method and cipher strength. The values of this policy determine the strength of the cipher that BitLocker uses for encryption. Enterprises may want to control the encryption level for increased security (AES-256 is stronger than AES-128). If you enable this setting, you can configure an encryption algorithm and key cipher strength for fixed data drives, operating system drives, and removable data drives individually. For fixed and operating system drives, we recommend that you use the XTS-AES algorithm. For removable drives, you should use AES-CBC 128-bit or AES-CBC 256-bit if the drive is used in other devices that aren't running Windows 10, version 1511 or later. Changing the encryption method has no effect if the drive is already encrypted or if encryption is in progress. In these cases, this policy setting is ignored.  

   For Bit locker system drive policy, configure the following settings:
  - **Encryption method**  
    **Default**: AES 256bit XTS  

## Browser  
For more information, see [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) in the Windows documentation.  

- **Require SmartScreen for Microsoft Edge**  
  Microsoft Edge uses Windows Defender SmartScreen (turned on) to protect users from potential phishing scams and malicious software by default. Also, by default, users can't disable (turn off) Windows Defender SmartScreen. Enabling this policy turns off Windows Defender SmartScreen and prevent users from turning it on. Don’t configure this policy to let users choose to turn Windows defender SmartScreen on or off.  
  
  **Default**: Yes  
  
- **Block malicious site access**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious sites, allowing them to continue to the site. With this policy though, you can configure Microsoft Edge to prevent users from bypassing the warnings, blocking them from continuing to the site.
  
  **Default**: Yes  
  
- **Block unverified file download**
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes  
  
- **Block Password Manager**  
  By default, Microsoft Edge uses Password Manager automatically, allowing users to manager passwords locally. Disabling this policy restricts Microsoft Edge from using Password Manager. Don’t configure this policy if you want to let users choose to save and manage passwords locally using Password Manager.
  
  **Default**: Yes  
  
- **Prevent certificate error overrides**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Yes  

## Connectivity  
For more information, see [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) in the Windows documentation.  

- **Block Internet download for web publishing and online ordering wizards**  
  This policy setting specifies whether Windows should download a list of providers for the web publishing and online ordering wizards. These wizards allow users to select from a list of companies that provide services such as online storage and photographic printing. By default, Windows displays providers downloaded from a Windows website in addition to providers specified in the registry. If you enable this policy setting, Windows doesn't download providers, and only the service providers that are cached in the local registry display. If you disable or don't configure this policy setting, a list of providers downloads when the user uses the web publishing or online ordering wizards. For more information that includes details on specifying service providers in the registry, see the documentation for the web publishing and online ordering wizards.  
  
  **Default**: Enabled  

- **Block downloading of print drivers over HTTP**  
  This policy setting specifies whether to allow this client to download print driver packages over HTTP. To set up HTTP printing, non-inbox drivers need to be downloaded over HTTP. Note: This policy setting doesn't prevent the client from printing to printers on the Intranet or the Internet over HTTP. It only prohibits downloading drivers that aren't already installed locally. If you enable this policy setting, print drivers can't be downloaded over HTTP. If you disable or don't configure this policy setting, users can download print drivers over HTTP.
  
  **Default**: Enabled  

## Credentials Delegation  
For more information, see [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) in the Windows documentation.  

- **Remote host delegation of non-exportable credentials**  
  Remote host allows delegation of non-exportable credentials. When using credential delegation, devices provide an exportable version of credentials to the remote host, which exposes users to the risk of credential theft from attackers on the remote host. If you enable this policy setting, the host supports Restricted Admin or Remote Credential Guard mode. If you disable or don't configure this policy setting, Restricted Administration and Remote Credential Guard mode aren't supported. User will always need to pass their credentials to the host.  

  
  **Default**: Enabled  

## Credentials UI  
For more information, see [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) in the Windows documentation.  

- **Enumerate administrators** 
  This policy setting controls whether administrator accounts display when a user attempts to elevate a running application. By default, administrator accounts aren't displayed when the user attempts to elevate a running application. If you enable this policy setting, all local administrator accounts on the PC display so the user can choose one and enter the correct password. If you disable this policy setting, users will always be required to type a user name and password to elevate.  

  
  **Default**: Disabled  

## Data Protection  
For more information, see [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) in the Windows documentation.  

- **Block direct memory access**  
  This policy setting allows you to block direct memory access (DMA) for all hot pluggable PCI downstream ports until a user logs into Windows. Once a user logs in, Windows will enumerate the PCI devices connected to the host plug PCI ports. Every time the user locks the machine, DMA is blocked on hot plug PCI ports with no children devices until the user logs in again. Devices that were already enumerated when the machine was unlocked will continue to function until unplugged. This policy setting is only enforced when BitLocker or device encryption is enabled.
  
  
  **Default**: Yes  

## Device Guard  
For more information, see [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) in the Windows documentation.  

- **Credential Guard**  
  This setting lets users turn on Credential Guard with virtualization-based security to help protect credentials at next reboot.
   
  **Default**: Enable with UEFI lock 

- **Enable virtualization based security**   
  Turns on virtualization-based security (VBS) at the next reboot. Virtualization-based security uses the Windows Hypervisor to provide support for security services.
  
  **Default**: Yes  


- **Launch system guard**    
  **Default**: Enabled  

## Device Installation  
For more information, see [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) in the Windows documentation.  

- **Hardware device installation by device identifiers**  
  This policy setting allows you to specify a list of Plug and Play hardware IDs and compatible IDs for devices that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing a device whose hardware ID or compatible ID appears in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, devices can install and update as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
  
    - **Remove matching hardware devices**   
    This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes
  
    - **Hardware device identifiers that are blocked**  
       This setting is available only when *Hardware device installation by device identifiers* is set to *Block hardware device installation*.
      
      **Default**: Yes  
  
- **Hardware device installation by setup classes**  
  This policy setting allows you to specify a list of device setup class globally unique identifiers (GUIDs) for device drivers that Windows is prevented from installing. This policy setting takes precedence over any other policy setting that allows Windows to install a device. If you enable this policy setting, Windows is prevented from installing or updating device drivers whose device setup class GUIDs appear in the list you create. If you enable this policy setting on a remote desktop server, the policy setting affects redirection of the specified devices from a remote desktop client to the remote desktop server. If you disable or don't configure this policy setting, Windows can install and update devices as allowed or prevented by other policy settings.
  
  **Default**: Block hardware device installation  

    When *Block hardware device installation* is selected, the following settings are available.
    - **Remove matching hardware devices**    
    This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.  

      **Default**: *No default configuration*  
  
    - **Hardware device identifiers that are blocked**  
      This setting is available only when *Hardware device installation by setup classes* is set to *Block hardware device installation*.
      
      **Default**: *No default configuration*  

## Device Lock  
For more information, see [Policy CSP - DeviceLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock) in the Windows documentation.  

- **Prevent use of camera**  
  Disables the lock screen camera toggle switch in PC Settings and prevents a camera from being invoked on the lock screen. By default, users can enable invocation of an available camera on the lock screen. If you enable this setting, users will no longer be able to enable or disable lock screen camera access in PC Settings, and the camera can't be invoked on the lock screen. 
  
  **Default**: Enabled  

- **Require password**  
  Specifies whether device lock is enabled.
  
  **Default**: Yes  
  
    When *Require password* is set to *Yes*, the following settings are available.

    - **Password minimum character set count**  
      The number of complex element types (uppercase and lowercase letters, numbers, and punctuation) required for a strong PIN or password. PIN enforces the following behavior for desktop and mobile devices: 1 - Digits only 2 - Digits and lowercase letters are required 3 - Digits, lowercase letters, and uppercase letters are required. Not supported in desktop Microsoft accounts and domain accounts. 4 - Digits, lowercase letters, uppercase letters, and special characters are required. Not supported in desktop. The default value is 1. 
      
      **Default**: 3  
  
    - **Number of sign-in failures before wiping device**  
      The number of authentication failures allowed before the device is wiped. A value of 0 disables device wipe functionality.
        
      **Default**: 10  
  
    - **Password expiration (days)**  
      The Maximum password age policy setting determines how long (in days) that a password can be used before the system requires the user to change it. You can set passwords to expire after a number of days between 1 and 999, or you can specify that passwords never expire by setting the number of days to 0. If Maximum password age is between 1 and 999 days, the minimum password age must be less than the maximum password age. If Maximum password age is set to 0, Minimum password age can be any value between 0 and 998 days.
      
      **Default**: 60  
  
    - **Required password type**  
      Determines the type of PIN or password required.
      
      **Default**: Alphanumeric  
  
    - **Minimum password length**  
      The Minimum password length policy setting determines the least number of characters that can make up a password for a user account. You can set a value of between 1 and 14 characters, or you can establish that no password is required by setting the number of characters to 0.
      
      **Default**: 8  
  
    - **Block simple passwords**  
      Specifies whether PINs or passwords such as "1111" or "1234" are allowed. For the desktop, it also controls the use of picture passwords.
      
      **Default**: Yes  
        *A setting of Yes prevents use of simple passwords.* 

  - **Prevent reuse of previous passwords**  
    Specifies how many passwords can be stored in the history that can’t be used. The value includes the user's current password. For example, with a setting of *1* the user can't reuse their current password when choosing a new password. A setting of *5* means that a user can't set their new password to their current password or any of their previous four passwords.
    
    **Default**: 24  

- **Prevent slide show**  
  Disables the lock screen slide show settings in PC Settings and prevents a slide show from playing on the lock screen. By default, users can enable a slide show that will run after they lock the machine. If you enable this setting, users can't modify slide show settings in PC Settings, and no slide show can start.
  
    **Default**: Enabled  
    *A setting of Enabled prevents slide shows from running.* 

- **Password minimum age in days**  
  The Minimum password age policy setting determines the period of time (in days) that a password must be used before the user can change it. You can set a value between 1 and 998 days, or you can allow password changes immediately by setting the number of days to 0. The minimum password age must be less than the Maximum password age, unless the maximum password age is set to 0, indicating that passwords will never expire. If the maximum password age is set to 0, the minimum password age can be set to any value between 0 and 998.
  
    **Default**: 1  

## Event Log Service  
For more information, see [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) in the Windows documentation.  

- **Security log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
   **Default**: 196608  

- **System log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

- **Application log maximum file size in KB**  
  This policy setting specifies the maximum size of the log file in kilobytes. If you enable this policy setting, you can configure the maximum log file size to be between 1 megabyte (1024 kilobytes) and 2 terabytes (2147483647 kilobytes) in kilobyte increments. If you disable or don't configure this policy setting, the maximum size of the log file is set to the locally configured value. This value can be changed by the local administrator using the Log Properties dialog and it defaults to 20 megabytes.
  
  **Default**: 32768  

## Experience  
For more information, see [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) in the Windows documentation.  

- **Block Windows Spotlight**  
  Allows IT admins to turn off all Windows Spotlight Features - Window spotlight on lock screen, Windows Tips, Microsoft consumer features, and other related features.
  
  **Default**: Yes  

  When *Block Windows Spotlight* is set to *Yes*, the following settings are available.
  
  - **Block third-party suggestions in Windows Spotlight**  
    Specifies whether to allow app and content suggestions from third-party software publishers in Windows spotlight features like lock screen spotlight, suggested apps in the Start menu, and Windows tips. Users may still see suggestions for Microsoft features, apps, and services.
      
    **Default**: Yes  
   - **Block consumer specific features**  
      Allows IT admins to turn on experiences that are typically for consumers only, such as Start suggestions, Membership notifications, Post-OOBE app install, and redirect tiles.
      
     **Default**: Yes  


## Exploit Guard  
For more information, see [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) in the Windows documentation.  

- **Exploit protection XML**  
  Enables the IT admin to push out a configuration that represents the desired system and application mitigation options to all the devices in the organization. The configuration is represented by an XML. Exploit protection helps protect devices from malware that use exploits to spread and infect. You use the Windows Security app or PowerShell to create a set of mitigations (known as a configuration). You can then export this configuration as an XML file and share it with multiple machines on your network so they all have the same set of mitigation settings. You can also convert and import an existing EMET configuration XML file into an exploit protection configuration XML.
  
  **Default**: *Sample xml is provided* 
 
## File Explorer  
For more information, see [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) in the Windows documentation.  

- **Block data execution prevention**  
  Disabling data execution prevention can allow certain legacy plug-in applications to function without terminating Explorer.
  
  **Default**: Disabled  
   
- **Block heap termination on corruption**  
  Disabling heap termination on corruption can allow certain legacy plug-in applications to function without terminating Explorer immediately, although Explorer may still terminate unexpectedly later.
  
  **Default**: Disabled  
    

## Internet Explorer  
For more information, see [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) in the Windows documentation.  


- **Internet Explorer internet zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains within windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in the same window. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in the same window. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy setting or don't configure it, users can drag content from one domain to a different domain when the source and destination are in the same window. Users can't change this setting in the Internet Options dialog.
  
  **Default**: Disabled
  
- **Internet Explorer certificate address mismatch warning**  
  This policy setting allows you to turn on the certificate address mismatch security warning. When this policy setting is turned on, the user is warned when visiting Secure HTTP (HTTPS) websites that present certificates issued for a different website address. This warning helps prevent spoofing attacks. If you enable this policy setting, the certificate address mismatch warning always appears. If you disable or don't configure this policy setting, the user can choose whether the certificate address mismatch warning appears (by using the Advanced page in the Internet Control panel).
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Internet sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, possibly harmful navigation is prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Disabled
  
- **Internet Explorer internet zone .NET Framework reliant components**  
  This policy setting allows you to manage whether .NET Framework components that aren't signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute unsigned managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute unsigned managed components. If you disable this policy setting, Internet Explorer won't execute unsigned managed components. If you don't configure this policy setting, Internet Explorer will execute unsigned managed components.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone allow only approved domains to use tdc ActiveX controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone include local path when uploading files to server**  
  This policy setting controls if local path information gets sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information gets sent when they upload a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled 
  
- **Internet Explorer disable processes in enhanced protected mode**  
  This policy setting determines whether Internet Explorer 11 uses 64-bit processes (for greater security) or 32-bit processes (for greater compatibility) when running in Enhanced Protected Mode on 64-bit versions of Windows. Important: Some ActiveX controls and toolbars may not be available when 64-bit processes are used. If you enable this policy setting, Internet Explorer 11 will use 64-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you disable this policy setting, Internet Explorer 11 will use 32-bit tab processes when running in Enhanced Protected Mode on 64-bit versions of Windows. If you don't configure this policy setting, users can turn this feature on or off using Internet Explorer settings. This feature is turned off by default.
  
  **Default**: Enabled 
  
- **Internet Explorer ignore certificate errors**  
  This policy setting prevents the user from ignoring Secure Sockets Layer/Transport Layer Security (SSL/TLS) certificate errors that interrupt browsing (such as "expired", "revoked", or "name mismatch" errors) in Internet Explorer. If you enable this policy setting, the user can't continue browsing. If you disable or don't configure this policy setting, the user can choose to ignore certificate errors and continue browsing.
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone automatic prompt for file downloads**  
  This policy setting determines whether users are prompted for non user-initiated file downloads. Regardless of this setting, users will receive file download dialogs for user-initiated downloads. If you enable this setting, users will receive a file download dialog for automatic download attempts. If you disable or don't configure this setting, file downloads that aren't user-initiated are blocked, and users will see the Notification bar instead of the file download dialog. Users can then click the Notification bar to allow the file download prompt.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled 
  
- **Internet Explorer fallback to SSL3**  
  This policy setting allows you to block an insecure fallback to SSL 3.0. When this policy is enabled, Internet Explorer will attempt to connect to sites using SSL 3.0 or below when TLS 1.0 or greater fails. We recommend that you don't allow insecure fallback in order to prevent a man-in-the-middle attack. This policy doesn't affect which security protocols are enabled. If you disable this policy, system defaults are used.
  
  **Default**: No sites 
  
- **Internet Explorer locked down internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled 
  
- **Internet Explorer restricted zone launch applications and files in an iFrame**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone.
  
  **Default**: Disable 
  
- **Internet Explorer bypass smart screen warnings about uncommon files**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes consistent MIME handling**  
  Internet Explorer contains dynamic binary behaviors: components that encapsulate specific functionality for the HTML elements to which they're attached. This policy setting controls whether the Binary Behavior Security Restriction setting is prevented or allowed. If you enable this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes. If you disable this policy setting, binary behaviors are allowed for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, binary behaviors are prevented for the File Explorer and Internet Explorer processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
    
  
- **Internet Explorer Active X controls in protected mode**  
  This policy setting prevents ActiveX controls from running in Protected Mode when Enhanced Protected Mode is enabled. When a user has an ActiveX control installed that isn't compatible with Enhanced Protected Mode and a website attempts to load the control, Internet Explorer notifies the user and gives the option to run the website in regular Protected Mode. This policy setting disables this notification and forces all websites to run in Enhanced Protected Mode. Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. When Enhanced Protected Mode is enabled, and a user comes across a website that attempts to load an ActiveX control that isn't compatible with Enhanced Protected Mode, Internet Explorer notifies the user and gives the option to disable Enhanced Protected Mode for that particular website. If you enable this policy setting, Internet Explorer won't give the user the option to disable Enhanced Protected Mode. All Protected Mode websites will run in Enhanced Protected Mode. If you disable or don't configure this policy setting, Internet Explorer notifies users and provides an option to run websites with incompatible ActiveX controls in regular Protected Mode.  
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone loading of XAML files**  
  This policy setting allows you to manage the loading of Extensible Application Markup Language (XAML) files. XAML is an XML-based declarative markup language commonly used for creating rich user interfaces and graphics that take advantage of the Windows Presentation Foundation. If you enable this policy setting and set the drop-down box to Enable, XAML files are automatically loaded inside Internet Explorer. The user can't change this behavior. If you set the drop-down box to Prompt, the user is prompted for loading XAML files. If you disable this policy setting, XAML files aren't loaded inside Internet Explorer. The user can't change this behavior. If you don't configure this policy setting, the user can decide whether to load XAML files inside Internet Explorer.
  
  **Default**: Disable  
  
- **Internet Explorer processes scripted window security restrictions**  
  Internet Explorer allows scripts to programmatically open, resize, and reposition windows of various types. The Window Restrictions security feature restricts popup windows and prohibits scripts from displaying windows in which the title and status bars aren't visible to the user or obfuscate other Windows' title and status bars. If you enable this policy setting, scripted windows are restricted for all processes. If you disable or don't configure this policy setting, scripted windows aren't restricted.
  
  **Default**: Enabled   
  
- **Internet Explorer restricted zone run Active X controls and plugins**  
  This policy setting allows you to manage whether ActiveX controls and plug-ins can run on pages from the specified zone. If you enable this policy setting, controls and plug-ins can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow the controls or plug-in to run. If you disable this policy setting, controls and plug-ins are prevented from running. If you don't configure this policy setting, controls and plug-ins are prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone script Active X controls marked safe for scripting**  
  This policy setting allows you to manage whether an ActiveX control marked safe for scripting can interact with a script. If you enable this policy setting, script interaction can occur automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow script interaction. If you disable this policy setting, script interaction is prevented from occurring. If you don't configure this policy setting, script interaction is prevented from occurring.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. 
  - *Anonymous*  - Use anonymous sign in to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. 
  - *Prompt* - Use prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in only in Intranet zone* - Use this option to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. 
  - *Automatic sign in with current user name and password*- Use this option to attempt sign in using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for sign in. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. 

  If you disable this policy setting, sign-in is set to *Automatic sign in only in Intranet zone*. If you don't configure this policy setting, sign-in is set to *Prompt* for username and password.
  
  **Default**: Anonymous  
  
- **Internet Explorer trusted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, users are queried whether to allow the control to load with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer check server certificate revocation**  
  This policy setting allows you to manage whether Internet Explorer will check revocation status of servers' certificates. Certificates are revoked when they are compromised or no longer valid, and this option protects users from submitting confidential data to a site that may be fraudulent or not secure. If you enable this policy setting, Internet Explorer will check to see if server certificates have been revoked. If you disable this policy setting, Internet Explorer won't check server certificates to see if they have been revoked. If you don't configure this policy setting, Internet Explorer won't check server certificates to see if they have been revoked.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone less privileged sites**  
  This policy setting allows you to manage whether Web sites from less privileged zones, such as Restricted Sites, can navigate into this zone. If you enable this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone. The security zone will run without the added layer of security that is provided by the Protection from Zone Elevation security feature. If you select Prompt in the drop-down box, a warning is issued to the user that potentially risky navigation is about to occur. If you disable this policy setting, the possibly harmful navigations are prevented. The Internet Explorer security feature is on in this zone as set by Protection from Zone Elevation feature control. If you don't configure this policy setting, Web sites from less privileged zones can open new windows in, or navigate into, this zone.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone file downloads**  
  This policy setting allows you to manage whether file downloads are permitted from the zone. This option gets determined by the zone of the page with the link causing the download, not the zone from which the file is delivered. If you enable this policy setting, files can be downloaded from the zone. If you disable this policy setting, files are prevented from being downloaded from the zone. If you don't configure this policy setting, files are prevented from being downloaded from the zone.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone run .NET Framework reliant components signed with Authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer prevent per user installation of Active X controls**  
  This policy setting allows you to prevent the installation of ActiveX controls on a per-user basis. If you enable this policy setting, ActiveX controls can't be installed on a per-user basis. If you disable or don't configure this policy setting, ActiveX controls can be installed on a per-user basis.
  
  **Default**: Enabled  
  
- **Internet Explorer prevent managing smart screen filter**  
  This policy setting prevents the user from managing SmartScreen Filter, which warns the user if the website they visit is known for fraudulent attempts to gather personal information through "phishing," or is known to host malware. If you enable this policy setting, the user isn't prompted to turn on SmartScreen Filter. All website addresses that aren't on the filters allow list are sent automatically to Microsoft without prompting the user. If you disable or don't configure this policy setting, the user gets prompted to decide whether to turn on SmartScreen Filter during the first-run experience.
  
  **Default**: Enable  
  
- **Internet Explorer processes MIME sniffing safety feature**  
  This policy setting determines whether Internet Explorer MIME sniffing will prevent promotion of a file of one type to a more dangerous file type. If you enable this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type. If you disable this policy setting, Internet Explorer processes will allow a MIME sniff promoting a file of one type to a more dangerous file type. If you don't configure this policy setting, MIME sniffing will never promote a file of one type to a more dangerous file type.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone download signed Active X controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer auto complete**  
  This Auto-Complete feature can remember and suggest User names and passwords on Forms. If you enable this setting, the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned on. You have to decide whether to select "prompt me to save passwords". If you disable this setting the user can't change "User name and passwords on forms" or "prompt me to save passwords". The Auto Complete feature for User names and passwords on Forms is turned off. The user also can't opt to be prompted to save passwords. If you don't configure this setting, the user has the freedom of turning on Auto complete for User name and passwords on forms and the option of prompting to save passwords. To display this option, the users open the Internet Options dialog box, click the Contents Tab, and click the Settings button.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone allow VBscript to run**  
  This policy setting lets you decide whether VBScript can run on pages in specific Internet Explorer zones. Options include: 
  - *Enable* - VBScript runs on pages in specific zones, without any interaction. 
  - *Prompt* - Employees are prompted whether to allow VBScript to run in the zone. 
  - *Disable* - VBScript is prevented from running in the zone. If you disable or don’t configure this policy setting, VBScript runs without any interaction in the specified zone. 
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone allow only approved domains to use tdc Active X controls**  
  This policy setting controls if the user can run the TDC ActiveX control on websites. If you enable this policy setting, the TDC ActiveX control won't run from websites in this zone. If you disable this policy setting, the TDC Active X control will run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone don't run antimalware against Active X controls**  
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled 
  
- **Internet Explorer local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: Disable java 
  
- **Internet Explorer intranet zone do not run antimalware against Active X controls**
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  

- **Internet Explorer restricted zone scriptlets**  
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disabled  
  
- **Internet Explorer processes notification bar**  
  This policy setting allows you to manage whether the Notification bar is displayed for Internet Explorer processes when file or code installs are restricted. By default, the Notification bar is displayed for Internet Explorer processes. If you enable this policy setting, the Notification bar displays for the Internet Explorer Processes. If you disable this policy setting, the Notification bar won't be displayed for Internet Explorer processes. If you don't configure this policy setting, the Notification bar doesn't display for Internet Explorer Processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download signed ActiveX controls**  
  This policy setting allows you to manage whether users may download signed ActiveX controls from a page in the zone. If you enable this policy, users can download signed controls without user intervention. If you select Prompt in the drop-down box, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded. If you disable the policy setting, signed controls can't download. If you don't configure this policy setting, users are queried whether to download controls signed by publishers who aren't trusted. Code signed by trusted publishers is silently downloaded.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer remove run this time button for outdated Active X controls**  
  This policy setting allows you to stop users from seeing the "Run this time" button and from running specific outdated ActiveX controls in Internet Explorer. If you enable this policy setting, users won't see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. If you disable or don't configure this policy setting, users will see the "Run this time" button on the warning message that appears when Internet Explorer blocks an outdated ActiveX control. Clicking this button lets the user run the outdated ActiveX control once. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled 
  
- **Internet Explorer internet zone launch applications and files in an iframe**  
  This policy setting allows you to manage whether applications may be run and files may be downloaded from an IFRAME reference in the HTML of the pages in this zone. If you enable this policy setting, users can run applications and download files from IFRAMEs on the pages in this zone without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone. If you disable this policy setting, users are prevented from running applications and downloading files from IFRAMEs on the pages in this zone. If you don't configure this policy setting, users are queried to choose whether to run applications and download files from IFRAMEs on the pages in this zone
  
  **Default**: Disable 
  
- **Internet Explorer restricted zone navigate windows and frames across different domains**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone smart screen**  
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down trusted zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer check signatures on downloaded programs**  
  This policy setting allows you to manage whether Internet Explorer checks for digital signatures (which identifies the publisher of signed software and verifies it hasn't been modified or tampered with) on user computers before downloading executable programs. If you enable this policy setting, Internet Explorer will check the digital signatures of executable programs and display their identities before downloading them to user computers. If you disable this policy setting, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers. If you don't configure this policy, Internet Explorer won't check the digital signatures of executable programs or display their identities before downloading them to user computers.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone scripting of web browser controls**  
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone cross site scripting filter**  
  This policy controls if the Cross-Site Scripting (XSS) Filter will detect and prevent cross-site script injections into websites in this zone. If you enable this policy setting, the XSS Filter is turned on for sites in this zone, and the XSS Filter attempts to block cross-site script injections. If you disable this policy setting, the XSS Filter is turned off for sites in this zone, and Internet Explorer permits cross-site script injections.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone binary and script behaviors**  
  This policy setting allows you to manage dynamic binary and script behaviors: components that encapsulate specific functionality for HTML elements to which they were attached. If you enable this policy setting, binary and script behaviors are available. If you select Administrator approved in the drop-down box, only behaviors listed in the Admin-approved Behaviors under Binary Behaviors Security Restriction policy are available. If you disable this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager. If you don't configure this policy setting, binary and script behaviors aren't available unless applications have implemented a custom security manager.
  
  **Default**: Disable  
  
- **Internet Explorer security settings check**  
  This policy setting turns off the Security Settings Check feature, which checks Internet Explorer security settings to determine when the settings put Internet Explorer at risk. If you enable this policy setting, the feature is turned off. If you disable or don't configure this policy setting, the feature is turned on.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone security warning for potentially unsafe files**  
  This policy setting controls if the "Open File - Security Warning" message appears when the user tries to open executable files or other potentially unsafe files (from an intranet file share by using File Explorer, for example). If you enable this policy setting and set the drop-down box to Enable, these files open without a security warning. If you set the drop-down box to Prompt, a security warning appears before the files open. If you disable this policy setting, these files don't open. If you don't configure this policy setting, the user can configure how the computer handles these files. By default, these files are blocked in the Restricted zone, enabled in the Intranet and Local Computer zones, and set to prompt in the Internet and Trusted zones.
  
  **Default**: Prompt  
  
- **Internet Explorer intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Medium Safety.
  
  **Default**: High safety 
  
- **Internet Explorer block outdated Active X controls**  
  This policy setting determines whether Internet Explorer blocks specific outdated ActiveX controls. Outdated ActiveX controls are never blocked in the Intranet Zone. If you enable this policy setting, Internet Explorer stops blocking outdated ActiveX controls. If you disable or don't configure this policy setting, Internet Explorer continues to block specific outdated ActiveX controls. For more information, see "Outdated ActiveX Controls" in the Internet Explorer TechNet library.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone popup blocker**  
  This policy setting allows you to manage whether unwanted pop-up windows appear. Pop-up windows that are opened when the end user clicks a link aren't blocked. If you enable this policy setting, most unwanted pop-up windows are prevented from appearing. If you disable this policy setting, pop-up windows aren't prevented from appearing. If you don't configure this policy setting, most unwanted pop-up windows are prevented from appearing.
  
  **Default**: Enable  
  
- **Internet Explorer processes MK protocol security restriction**  
  The MK Protocol Security Restriction policy setting reduces attack surface area by preventing the MK protocol. Resources hosted on the MK protocol will fail. If you enable this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail. If you disable this policy setting, applications can use the MK protocol API. Resources hosted on the MK protocol will work for the File Explorer and Internet Explorer processes. If you don't configure this policy setting, the MK Protocol is prevented for File Explorer and Internet Explorer, and resources hosted on the MK protocol will fail.
  
  **Default**: Enabled  
  
- **Internet Explorer trusted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to Low Safety.
  
  **Default**: High safety  
  
- **Internet Explorer restricted zone scripting of java applets**  
  This policy setting allows you to manage whether applets are exposed to scripts within the zone. If you enable this policy setting, scripts can access applets automatically without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow scripts to access applets. If you disable this policy setting, scripts are prevented from accessing applets. If you don't configure this policy setting, scripts are prevented from accessing applets.
  
  **Default**: Disable  
  
- **Internet Explorer locked down restricted zone java permissions**   
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java 
  
- **Internet Explorer internet zone allow only approved domains to use ActiveX controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer include all network paths**  
  Internet Explorer include all network paths
  
  **Default**: Disabled 
  
- **Internet Explorer internet zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable 
  
- **Internet Explorer internet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer locked down restricted zone smart screen**   
  This policy setting controls whether SmartScreen Filter scans pages in this zone for malicious content. If you enable this policy setting, SmartScreen Filter scans pages in this zone for malicious content. If you disable this policy setting, SmartScreen Filter doesn't scan pages in this zone for malicious content. If you don't configure this policy setting, the user can choose whether SmartScreen Filter scans pages in this zone for malicious content. Note: In Internet Explorer 7, this policy setting controls whether Phishing Filter scans pages in this zone for malicious content.
  
  **Default**: Enabled  
  
- **Internet Explorer crash detection**  
  This policy setting allows you to manage the crash detection feature of add-on Management. If you enable this policy setting, a crash in Internet Explorer will exhibit behavior found in Windows XP Professional Service Pack 1 and earlier, namely to invoke Windows Error Reporting. All policy settings for Windows Error Reporting continue to apply. If you disable or don't configure this policy setting, the crash detection feature for add-on management is functional.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, the permission is set to High Safety.
  
  **Default**: Disable java  
  
- **Internet Explorer restricted zone active scripting**  
  This policy setting allows you to manage whether script code on pages in the zone is run. If you enable this policy setting, script code on pages in the zone can run automatically. If you select Prompt in the drop-down box, users are queried to choose whether to allow script code on pages in the zone to run. If you disable this policy setting, script code on pages in the zone is prevented from running. If you don't configure this policy setting, script code on pages in the zone is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone logon options**  
  This policy setting allows you to manage settings for sign in options. If you enable this policy setting, you can choose from the following sign in options. Anonymous log on to disable HTTP authentication and use the guest account only for the Common Internet File System (CIFS) protocol. Prompt for user name and password to query users for user IDs and passwords. After a user is queried, these values can be used silently for the remainder of the session. Automatic log on only in Intranet zone to query users for user IDs and passwords in other zones. After a user is queried, these values can be used silently for the rest of the session. Automatic sign in with current user name and password to attempt log on using Windows NT Challenge Response (also known as NTLM authentication). If the server supports Windows NT Challenge Response, the sign in uses the user's network user name and password for log on. If the server doesn't support Windows NT Challenge Response, the user is queried to provide the user name and password. If you disable this policy setting, sign in is set to Automatic log on only in Intranet zone. If you don't configure this policy setting, sign in is set to Automatic sign in only in Intranet zone.
  
  **Default**: Prompt  
  
- **Internet Explorer restricted zone allow vbscript to run**  
  This policy setting allows you to manage whether VBScript can be run on pages from the specified zone in Internet Explorer. If you selected Enable in the drop-down box, VBScript can run without user intervention. If you selected Prompt in the drop-down box, users are asked to choose whether to allow VBScript to run. If you selected Disable in the drop-down box, VBScript is prevented from running. If you don't configure or disable this policy setting, VBScript is prevented from running.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.
  
  **Default**: Disabled 
  
- **Internet Explorer intranet zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable 
  
- **Internet Explorer download enclosures**  
  This policy setting prevents the user from having enclosures (file attachments) downloaded from a feed to the user's computer. If you enable this policy setting, the user can't set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can't change the download setting through the Feed APIs. If you disable or don't configure this policy setting, the user can set the Feed Sync Engine to download an enclosure through the Feed property page. A developer can change the download setting through the Feed APIs.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone download unsigned Active X controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone drag content from different domains within windows**  
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict Active X install**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of ActiveX control installation. If you enable this policy setting, the Web Browser Control will block automatic prompting of ActiveX control installation for all processes. If you disable or don't configure this policy setting, the Web Browser Control won't block automatic prompting of ActiveX control installation for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone scriptlets**
  This policy setting allows you to manage whether the user can run scriptlets. If you enable this policy setting, the user can run scriptlets. If you disable this policy setting, the user can't run scriptlets. If you don't configure this policy setting, the user can enable or disable scriptlets.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag and drop or copy and paste files**  
  This policy setting allows you to manage whether users can drag files or copy and paste files from a source within the zone. If you enable this policy setting, users can drag files or copy and paste files from this zone automatically. If you select Prompt in the drop-down box, users are queried to choose whether to drag or copy files from this zone. If you disable this policy setting, users are prevented from dragging files or copying and pasting files from this zone. If you don't configure this policy setting, users are queried to choose whether to drag or copy files from this zone.
  
  **Default**: Disable  
  
- **Internet Explorer software when signature is invalid**   
  This policy setting allows you to manage whether software, such as ActiveX controls and file downloads, can be installed or run by the user even though the signature is invalid. An invalid signature might indicate that someone has tampered with the file. If you enable this policy setting, users are prompted to install or run files with an invalid signature. If you disable this policy setting, users can't run or install files with an invalid signature. If you don't configure this policy, users can choose to run or install files with an invalid signature.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone copy and paste via script**   
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can't perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone drag content from different domains across windows**  
  This policy setting allows you to set options for dragging content from one domain to a different domain when the source and destination are in different windows. If you enable this policy setting and click Enable, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting. If you enable this policy setting and click Disable, users can't drag content from one domain to a different domain when both the source and destination are in different windows. Users can't change this setting. In Internet Explorer 10, if you disable this policy setting or don't configure it, users can't drag content from one domain to a different domain when the source and destination are in different windows. Users can change this setting in the Internet Options dialog. In Internet Explorer 9 and earlier versions, if you disable this policy or don't configure it, users can drag content from one domain to a different domain when the source and destination are in different windows. Users can't change this setting.   
  **Default**: Disabled  
  
- **Internet Explorer users adding sites**  
  Prevents users from adding or removing sites from security zones. A security zone is a group of Web sites with the same security level. If you enable this policy, the site management settings for security zones are disabled. (To see the site management settings for security zones, in the Internet Options dialog box, click the Security tab, and then click the Sites button.) If you disable this policy or don't configure it, users can add Web sites to or remove sites from the Trusted Sites and Restricted Sites zones, and alter settings for the Local Intranet zone. This policy prevents users from changing site management settings for security zones established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from the interface, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone script initiated windows**  
  This policy setting allows you to manage restrictions on script-initiated pop-up windows and windows that include the title and status bars. If you enable this policy setting, Windows Restrictions security won't apply in this zone. The security zone runs without the added layer of security provided by this feature. If you disable this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process. If you don't configure this policy setting, the possible harmful actions contained in script-initiated pop-up windows and windows that include the title and status bars can't run. This Internet Explorer security feature is on in this zone as dictated by the Scripted Windows Security Restrictions feature control setting for the process.
  
  **Default**: Disabled  
  
- **Internet Explorer security zones use only machine settings**  
  Applies security zone information to all users of the same computer. A security zone is a group of Web sites with the same security level. If you enable this policy, changes that the user makes to a security zone will apply to all users of that computer. If you disable this policy or don't configure it, users of the same computer can establish their own security zone settings. Use this policy to ensure that security zone settings apply uniformly to the same computer and don't vary from user to user. Also, see the "Security zones: don't allow users to change policies" policy.
  
  **Default**: Enabled  
  
- **Internet Explorer locked down local machine zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled
  
  **Default**: Disable java 
  
- **Internet Explorer restricted zone do not run antimalware against Active X controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone run .NET Framework reliant components signed with authenticode**  
  This policy setting allows you to manage whether .NET Framework components that are signed with Authenticode can be executed from Internet Explorer. These components include managed controls referenced from an object tag and managed executables referenced from a link. If you enable this policy setting, Internet Explorer will execute signed managed components. If you select Prompt in the drop-down box, Internet Explorer will prompt the user to determine whether to execute signed managed components. If you disable this policy setting, Internet Explorer won't execute signed managed components. If you don't configure this policy setting, Internet Explorer won't execute signed managed components.
  
  **Default**: Disable  
  
- **Internet Explorer restricted zone access to data sources**  
  This policy setting allows you to manage whether Internet Explorer can access data from another security zone using the Microsoft XML Parser (MSXML) or ActiveX Data Objects (ADO). If you enable this policy setting, users can load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you select Prompt in the drop-down box, users are queried to choose whether to allow a page to load in the zone that uses MSXML or ADO to access data from another site in the zone. If you disable this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone. If you don't configure this policy setting, users can't load a page in the zone that uses MSXML or ADO to access data from another site in the zone.
  
  **Default**: Disable 
  
- **Internet Explorer internet zone don't run antimalware against ActiveX controls**   
  This policy setting determines whether Internet Explorer runs antimalware programs against ActiveX controls, to check if they're safe to load on pages. If you enable this policy setting, Internet Explorer won't check with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you disable this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. If you don't configure this policy setting, Internet Explorer always checks with your antimalware program to see if it's safe to create an instance of the ActiveX control. Users can turn this behavior on or off, using Internet Explorer Security settings.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone copy and paste via script**  
  This policy setting allows you to manage whether scripts can perform a clipboard operation (for example, cut, copy, and paste) in a specified region. If you enable this policy setting, a script can perform a clipboard operation. If you select Prompt in the drop-down box, users are queried as to whether to perform clipboard operations. If you disable this policy setting, a script can't perform a clipboard operation. If you don't configure this policy setting, a script can perform a clipboard operation.
  
  **Default**: Disable  
  
- **Internet Explorer use Active X installer service**   
  This policy setting allows you to specify how ActiveX controls are installed. If you enable this policy setting, ActiveX controls are installed only if the ActiveX Installer Service is present and has been configured to allow the installation of ActiveX controls. If you disable or don't configure this policy setting, ActiveX controls, including per-user controls, are installed through the standard installation process.
  
  **Default**: Enabled  
  
- **Internet Explorer processes protection from zone elevation**  
  Internet Explorer places restrictions on each Web page it opens. The restrictions are dependent upon the location of the Web page (Internet, Intranet, Local Machine zone, and so on). For example, Web pages on the local computer have the fewest security restrictions and are in the Local Machine zone, making the Local Machine security zone a prime target for malicious users. If you enable this policy setting, any zone can be protected from zone elevation for all processes. If you disable or don't configure this policy setting, processes other than Internet Explorer or those listed in the Process List receive no such protection.
  
  **Default**: Enabled  
  
- **Internet Explorer internet zone download unsigned ActiveX controls**   
  This policy setting allows you to manage whether users may download unsigned ActiveX controls from the zone. Such code is potentially harmful, especially when coming from an untrusted zone. If you enable this policy setting, users can run unsigned controls without user intervention. If you select Prompt in the drop-down box, users are queried to choose whether to allow the unsigned control to run. If you disable this policy setting, users can't run unsigned controls. If you don't configure this policy setting, users can't run unsigned controls.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone navigate windows and frames across different domains**   
  This policy setting allows you to manage the opening of windows and frames and access of applications across different domains. If you enable this policy setting, users can open windows and frames from other domains and access applications from other domains. If you select Prompt in the drop-down box, users are queried whether to allow windows and frames to access applications from other domains. If you disable this policy setting, users can't open windows and frames to access applications from different domains. If you don't configure this policy setting, users can open windows and frames from other domains and access applications from other domains.
  
  **Default**: Disable  
  
- **Internet Explorer internet zone updates to status bar via script**  
  This policy setting allows you to manage whether a script can update the status bar within the zone. If you enable this policy setting, scripts can update the status bar. If you disable or don't configure this policy setting, script isn't allowed to update the status bar.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone include local path when uploading files to server**  
  This policy setting controls if local path information is sent when the user is uploading a file via an HTML form. If the local path information is sent, some information may be unintentionally revealed to the server. For instance, files sent from the user's desktop may contain the user name as a part of the path. If you enable this policy setting, path information is sent when the user is uploading a file via an HTML form. If you disable this policy setting, path information is removed when the user is uploading a file via an HTML form. If you don't configure this policy setting, the user can choose whether path information is sent when they are uploading a file via an HTML form. By default, path information is sent.
  
  **Default**: Disabled  
  
- **Internet Explorer processes restrict file download**   
  This policy setting enables applications hosting the Web Browser Control to block automatic prompting of file downloads that aren't user initiated. If you enable this policy setting, the Web Browser Control will block automatic prompting of file downloads that aren't user initiated for all processes. If you disable this policy setting, the Web Browser Control won't block automatic prompting of file downloads that aren't user initiated for all processes.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone allow only approved domains to use Active X controls**   
  This policy setting controls if the user is prompted to allow ActiveX controls to run on websites other than the website that installed the ActiveX control. If you enable this policy setting, the user is prompted before ActiveX controls can run from websites in this zone. The user can choose to allow the control to run from the current site or from all sites. If you disable this policy setting, the user doesn't see the per-site ActiveX prompt, and ActiveX controls can run from all sites in this zone.
  
  **Default**: Enabled  
  
- **Internet Explorer restricted zone initialize and script Active X controls not marked as safe**  
  This policy setting allows you to manage ActiveX controls not marked as safe. If you enable this policy setting, ActiveX controls run, loaded with parameters, and scripted without setting object safety for untrusted data or scripts. This setting isn't recommended, except for secure and administered zones. This setting causes both unsafe and safe controls to be initialized and scripted, ignoring the Script ActiveX controls marked safe for scripting option. If you enable this policy setting and select Prompt in the drop-down box, users are queried whether to allow the control to load with parameters or scripted. If you disable this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted. If you don't configure this policy setting, ActiveX controls that can't be made safe aren't loaded with parameters or scripted.
  
  **Default**: Disable  
  
- **Internet Explorer users changing policies**  
    Prevents users from changing security zone settings. A security zone is a group of Web sites with the same security level. If you enable this policy, the Custom Level button and security-level slider on the Security tab in the Internet Options dialog box are disabled. If you disable this policy or don't configure it, users can change the settings for security zones. This policy prevents users from changing security zone settings established by the administrator. Note: The "Disable the Security page" policy (located in \User Configuration\Administrative Templates\Windows Components\Internet Explorer\Internet Control Panel), which removes the Security tab from Internet Explorer in Control Panel, takes precedence over this policy. If it's enabled, this policy is ignored. Also, see the "Security zones: Use only machine settings" policy.
    
  **Default**: Disabled  
  
- **Internet Explorer restricted zone protected mode**  
  This policy setting allows you to turn on Protected Mode. Protected Mode helps protect Internet Explorer from exploited vulnerabilities by reducing the locations that Internet Explorer can write to in the registry and the file system. If you enable this policy setting, Protected Mode is turned on. The user can't turn off Protected Mode. If you disable this policy setting, Protected Mode is turned off. The user can't turn on Protected Mode. If you don't configure this policy setting, the user can turn on or turn off Protected Mode.
  
  **Default**: Enable  
  
- **Internet Explorer internet zone user data persistence**  
  This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.
  
  **Default**: Disabled  
  
- **Internet Explorer internet zone scripting of web browser controls**  
 
  This policy setting determines whether a page can control embedded WebBrowser controls via script. If you enable this policy setting, script access to the WebBrowser control is allowed. If you disable this policy setting, script access to the WebBrowser control isn't allowed. If you don't configure this policy setting, the user can enable or disable script access to the WebBrowser control. By default, script access to the WebBrowser control is allowed only in the Local Machine and Intranet zones.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone user data persistence**  
    This policy setting allows you to manage the preservation of information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. When a user returns to a persisted page, the state of the page can be restored if this policy setting is appropriately configured. If you enable this policy setting, users can preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you disable this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk. If you don't configure this policy setting, users can't preserve information in the browser's history, in favorites, in an XML store, or directly within a Web page saved to disk.  
  
  **Default**: Disabled  
  
- **Internet Explorer locked down intranet zone java permissions**  
  This policy setting allows you to manage permissions for Java applets. If you enable this policy setting, you can choose options from the drop-down box. Custom, to control permissions settings individually. Low Safety enables applets to perform all operations. Medium Safety enables applets to run in their sandbox (an area in memory outside of which the program can't make calls), plus capabilities like scratch space (a safe and secure storage area on the client computer) and user-controlled file I/O. High Safety enables applets to run in their sandbox. Disable Java to prevent any applets from running. If you disable this policy setting, Java applets can't run. If you don't configure this policy setting, Java applets are disabled.
  
  **Default**: Disable java  
  
- **Internet Explorer enhanced protected mode**  
  Enhanced Protected Mode provides additional protection against malicious websites by using 64-bit processes on 64-bit versions of Windows. For computers running at least Windows 8, Enhanced Protected Mode also limits the locations Internet Explorer can read from in the registry and the file system. If you enable this policy setting, Enhanced Protected Mode is turned on. Any zone that has Protected Mode enabled will use Enhanced Protected Mode. Users won't be able to disable Enhanced Protected Mode. If you disable this policy setting, Enhanced Protected Mode is turned off. Any zone that has Protected Mode enabled will use the version of Protected Mode introduced in Internet Explorer 7 for Windows Vista. If you don't configure this policy, users can turn on or turn off Enhanced Protected Mode on the Advanced tab of the Internet Options dialog.
  
  **Default**: Enabled  
  
- **Internet Explorer bypass smart screen warnings**  
  This policy setting determines whether the user can bypass warnings from SmartScreen Filter. SmartScreen Filter warns the user about executable files that Internet Explorer users don't commonly download from the Internet. If you enable this policy setting, SmartScreen Filter warnings block the user. If you disable or don't configure this policy setting, the user can bypass SmartScreen Filter warnings.
  
  **Default**: Disabled  
  
- **Internet Explorer restricted zone meta refresh**  
  This policy setting allows you to manage whether a user's browser can be redirected to another Web page if the author of the Web page uses the Meta Refresh setting (tag) to redirect browsers to another Web page. If you enable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can be redirected to another Web page. If you disable this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page. If you don't configure this policy setting, a user's browser that loads a page containing an active Meta Refresh setting can't be redirected to another Web page.
  
  **Default**: Disabled  
  
## Local Policies Security Options
For more information, see [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) in the Windows documentation. 

- **Restrict anonymous access to named pipes and shares**  
  When enabled, this security setting restricts anonymous access to shares and pipes to the settings for: (1) Named pipes that can be accessed anonymously (2) Shares that can be accessed anonymously
  
  **Default**: Yes  
  
- **Minimum session security for NTLM SSP based servers**  
  This security setting allows a server to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are: Require NTLMv2 session security: The connection will fail if message integrity isn't negotiated. Require 128-bit encryption. The connection will fail if strong encryption (128-bit) isn't negotiated.
  
  **Default**: Require NTLM V2 and 128 bit encryption  
  
- **Minutes of lock screen inactivity until screen saver activates**  
  Windows notices inactivity of a logon session, and if the amount of inactive time exceeds the inactivity limit, then the screen saver will run, locking the session.
  
  **Default**: 15
  
- **Require client to always digitally sign communications** 
  This security setting determines whether all secure channel traffic initiated by the domain member must be signed or encrypted. When a computer joins a domain, a computer account is created. After that, when the system starts, it uses the computer account password to create a secure channel with a domain controller for its domain. This secure channel is used to perform operations such as NTLM pass through authentication, LSA SID/name Lookup and more. This setting determines if all secure channel traffic initiated by the domain member meets minimum security requirements. Specifically it determines whether all secure channel traffic started by the domain member must be signed or encrypted. If this policy is enabled, then the secure channel won't be established unless either signing or encryption of all secure channel traffic is negotiated. If this policy is disabled, then encryption and signing of all secure channel traffic is negotiated with the Domain Controller in which case the level of signing and encryption depends on the version of the Domain Controller and the settings of the following two policies: Domain member: Digitally encrypt secure channel data (when possible) Domain member: Digitally sign secure channel data (when possible)
  
  **Default**: Yes
  
- **Authentication level**  
  This security setting determines which challenge/response authentication protocol is used for network logons. This choice affects the level of authentication protocol used by clients, the level of session security negotiated, and the level of authentication accepted by servers as follows:  
  - *Send LM and NTLM responses*: Clients use LM and NTLM authentication and never use NTLMv2 session security; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send LM and NTLM - NTLMv2 if negotiated*: Clients use LM and NTLM authentication and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLM response only*: Clients use NTLM authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers accept LM, NTLM, and NTLMv2 authentication. 
  - *Send NTLMv2 response only. Refuse LM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM (accept only NTLM and NTLMv2 authentication). 
  - *Send NTLMv2 response only. Refuse LM and NTLM*: Clients use NTLMv2 authentication only and use NTLMv2 session security if the server supports it; domain controllers refuse LM and NTLM (accept only NTLMv2 authentication). 
    
  **Default**: Send NTLMv2 response only. Refuse LM and NTLM
  
- **Prevent clients from sending unencrypted passwords to third party SMB servers**  
  If this security setting is enabled, the Server Message Block (SMB) redirector can send plaintext passwords to non-Microsoft SMB servers that don't support password encryption during authentication. Sending unencrypted passwords is a security risk.
  
  **Default**: Yes
  
- **Disable server digitally signing communications always**  
  This security setting determines whether the SMB client attempts to negotiate SMB packet signing. The server message block (SMB) protocol provides the basis for Microsoft file and print sharing and many other networking operations, such as remote Windows administration. To prevent man-in-the-middle attacks that modify SMB packets in transit, the SMB protocol supports the digital signing of SMB packets. This policy setting determines whether the SMB client component attempts to negotiate SMB packet signing when it connects to an SMB server. If this setting is enabled, the Microsoft network client will ask the server to perform SMB packet signing upon session setup. If packet signing has been enabled on the server, packet signing is negotiated. If this policy is disabled, the SMB client will never negotiate SMB packet signing.
  
  **Default**: Yes
  
- **Administrator elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for administrators. The options are: 
    - *Elevate without prompting*: Allows privileged accounts to perform an operation that requires elevation without requiring consent or credentials. Note: Use this option only in the most constrained environments. 
    - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a privileged user name and password. If the user enters valid credentials, the operation continues with the user's highest available privilege. 
    - *Prompt for consent on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege. 
    - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
    - *Prompt for consent*: When an operation requires elevation of privilege, the user is prompted to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.  
    - *Prompt for consent for non-Windows binaries*: When an operation for a non-Microsoft application requires elevation of privilege, the user is prompted on the secure desktop to select either Permit or Deny. If the user selects Permit, the operation continues with the user's highest available privilege.   
  
  **Default**: Prompt for consent on the secure desktop
  
- **Minimum session security for NTLM SSP based clients**  
  This security setting allows a client to require the negotiation of 128-bit encryption and/or NTLMv2 session security. These values are dependent on the LAN Manager Authentication Level security setting value. The options are:
  - Require NTLMv2 session security: The connection will fail if NTLMv2 protocol isn't negotiated. 
  - *Require 128-bit encryption*: The connection will fail if strong encryption (128-bit) isn't negotiated.
  - *Require NTLMv2 and 128-bit encryption*. 

  **Default**: Require NTLM V2 128 encryption
  
- **Smart card removal behavior**  
    This security setting determines what happens when the smart card for a logged-on user is removed from the smart card reader. The options are:
     - *No action*. 
     - *Lock Workstation* - The workstation is locked when the smart card is removed, allowing users to leave the area, take their smart card with them, and still maintain a protected session.
     - *Force Logoff* - the user is automatically logged off when the smart card is removed.
     - *Disconnect Remote Desktop session* - Removal of the smart card disconnects the session without logging the user off. This allows the user to insert the smart card and resume the session later, or at another smart card reader-equipped computer, without having to log on again. If the session is local, this policy functions identically to Lock Workstation.   
    
  **Default**: Lock workstation
  
- **Block anonymous enumeration of SAM accounts and shares**  
  This security setting determines whether to allow anonymous enumeration of SAM accounts and shares. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. If you don't want to allow anonymous enumeration of SAM accounts and shares, then set this policy to *Yes*.
  
  **Default**: Yes
  
- **Block remote logon with blank password**  
  This security setting determines whether local accounts that aren't password protected can be used to log on from locations other than the physical computer console. If enabled, local accounts that aren't password protected must use the computer's keyboard to log on. 

  *Warning*: Computers that aren't in physically secure locations should always enforce strong password policies for all local user accounts. Otherwise, anyone with physical access to the computer can log on by using a user account that doesn't have a password. This is especially important for portable computers. 

  If you apply this security policy to the Everyone group, no one can log on through Remote Desktop Services. This setting doesn't affect logons that use domain accounts. It's possible for applications that use remote interactive logons to bypass this setting.
  
  **Default**: Yes
  
- **Standard user elevation prompt behavior**  
  This policy setting controls the behavior of the elevation prompt for standard users. 
  - *Automatically deny elevation requests*: When an operation requires elevation of privilege, a configurable access denied error message is displayed. An enterprise that is running desktops as standard user may choose this setting to reduce help desk calls. 
  - *Prompt for credentials on the secure desktop*: When an operation requires elevation of privilege, the user is prompted on the secure desktop to enter a different user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Prompt for credentials*: When an operation requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege.  
  
  **Default**: Automatically deny elevation requests
  
- **Require admin approval mode for administrators**  
  This policy setting controls the behavior of all User Account Control (UAC) policy settings for the computer. If you change this policy setting, you must restart your computer. The options are:   
  - *Not configured*: Admin Approval Mode and all related UAC policy settings are disabled. Note: If this policy setting is disabled, the Security Center notifies you that the overall security of the operating system has been reduced. 
  - *Yes*: Admin Approval Mode is enabled. This policy must be enabled and related UAC policy settings must be set appropriately to allow the built-in Administrator account and all other users who are members of the Administrators group to run in Admin Approval Mode.  
  
  **Default**: Yes
  
- **Prevent anonymous enumeration of SAM accounts**  
  This security setting determines what additional permissions are granted for anonymous connections to the computer. Windows allows anonymous users to perform certain activities, such as enumerating the names of domain accounts and network shares. This is convenient, for example, when an administrator wants to grant access to users in a trusted domain that doesn't maintain a reciprocal trust. This security option allows additional restrictions to be placed on anonymous connections as follows: 
  - *Yes*: Don't allow enumeration of SAM accounts. This option replaces Everyone with Authenticated Users in the security permissions for resources.
  - *Not configured*: No additional restrictions. Rely on default permissions.  
  
  **Default**: Yes
  
- **Allow remote calls to security accounts manager**  
  This policy setting allows you to restrict remote rpc connections to SAM. If not selected, the default security descriptor is used.
  
  **Default**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Use admin approval mode**  
  This policy setting controls the behavior of Admin Approval Mode for the built-in Administrator account. The options are: 
  - *Yes*: The built-in Administrator account uses Admin Approval Mode. By default, any operation that requires elevation of privilege will prompt the user to approve the operation. 
  - *Not Configured*: The built-in Administrator account runs all applications with full administrative privilege.  

  **Default**: Yes
  
- **Allow UI access applications for secure locations**  
  This policy setting controls whether User Interface Accessibility (UIAccess or UIA) programs can automatically disable the secure desktop for elevation prompts used by a standard user. 
  - *Yes*: UIA programs, including Windows Remote Assistance, automatically disable the secure desktop for elevation prompts. If you don't disable the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting, the prompts appear on the interactive user's desktop instead of the secure desktop. 
  - *Not Configured*: The secure desktop can be disabled only by the user of the interactive desktop or by disabling the "User Account Control: Switch to the secure desktop when prompting for elevation" policy setting.  

  **Default**: Yes

- **Detect application installations and prompt for elevation**  
  This policy setting controls the behavior of application installation detection for the computer. The options are: 
  - *Enabled*: When an application installation package is detected that requires elevation of privilege, the user is prompted to enter an administrative user name and password. If the user enters valid credentials, the operation continues with the applicable privilege. 
  - *Disabled*: Application installation packages aren't detected and prompted for elevation. Enterprises that are running standard user desktops and use delegated installation technologies such as Group Policy Software Installation or Systems Management Server (SMS) should disable this policy setting. In this case, installer detection is unnecessary.  
  
  **Default**: Yes
  
- **Prevent storing LAN manager hash value on next password change**  
  This security setting determines if, at the next password change, the LAN Manager (LM) hash value for the new password is stored. The LM hash is relatively weak and prone to attack, as compared with the cryptographically stronger Windows NT hash. Since the LM hash is stored on the local computer in the security database the passwords can be compromised if the security database is attacked.
  
  **Default**: Yes

- **Virtualize file and registry write failures to per user locations**  
  This policy setting controls whether application write failures are redirected to defined registry and file system locations. This policy setting mitigates applications that run as administrator and write run-time application data to *%ProgramFiles%*, *%Windir%*, *%Windir%\system32*, or *HKLM\Software*.
  
  **Default**: Yes

## MS Security Guide  
For more information, see [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) in the Windows documentation.  

- **Apply UAC restrictions to local accounts on network logon**  
  **Default**: Enabled
  
- **SMB v1 client driver start configuration**  
  **Default**: Disabled driver
  
- **SMB v1 server**  
  **Default**: Disabled
  
- **Digest authentication**  
  **Default**: Disabled
  
- **Structured exception handling overwrite protection**  
  **Default**: Enabled
  
## MSS Legacy  
For more information, see [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) in the Windows documentation.  

- **Network IP source routing protection level**  
  **Default**: Highest protection  
  
- **Network ignore NetBIOS name release requests except from WINS servers**  
  **Default**: Enabled
  
- **Network IPv6 source routing protection level**  
  **Default**: Highest protection

- **Network ICMP redirects override OSPF generated**  
  **Default**: Disabled
  
## Power  
For more information, see [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) in the Windows documentation.  

- **Require password on wake while plugged in**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
- **Standby states when sleeping while on battery**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Standby states when sleeping while plugged in**  
  This policy setting manages if Windows can use standby states when putting the computer in a sleep state. If you enable or don't configure this policy setting, Windows uses standby states to put the computer in a sleep state. If you disable this policy setting, standby states (S1-S3) aren't allowed.
  
  **Default**: Disabled
  
- **Require password on wake while on battery**  
  This policy setting specifies if the user is prompted for a password when the system resumes from sleep. If you enable or don't configure this policy setting, the user is prompted for a password when the system resumes from sleep. If you disable this policy setting, the user isn't prompted for a password when the system resumes from sleep.
  
  **Default**: Enabled
  
## Remote Desktop Services  
For more information, see [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) in the Windows documentation.  

- **Block password saving**  
  Controls whether passwords can be saved on this computer from Remote Desktop Connection. If you enable this setting the password saving checkbox in Remote Desktop Connection is disabled and users won't be able to save passwords. When a user opens an RDP file using Remote Desktop Connection and saves their settings, any password that previously existed in the RDP file are deleted. If you disable this setting or leave it not configured, the user can save passwords using Remote Desktop Connection.
  
   **Default**: Enabled
  
- **Secure RPC communication**  
  Specifies whether a Remote Desktop Session Host server requires secure RPC communication with all clients or allows unsecured communication. You can use this setting to strengthen the security of RPC communication with clients by allowing only authenticated and encrypted requests. If the status is set to Enabled, Remote Desktop Services accepts requests from RPC clients that support secure requests, and doesn't allow unsecured communication with untrusted clients. If the status is set to Disabled, Remote Desktop Services always requests security for all RPC traffic. However, unsecured communication is allowed for RPC clients that don't respond to the request. If the status is set to Not Configured, unsecured communication is allowed. Note: The RPC interface is used for administering and configuring Remote Desktop Services.
  
  **Default**: Enabled
  
- **Block drive redirection**  
  This policy setting specifies whether to prevent the mapping of client drives in a Remote Desktop Services session (drive redirection). By default, an RD Session Host server maps client drives automatically upon connection. Mapped drives appear in the session folder tree in File Explorer or Computer in the format *\<driveletter>* on *\<computername>*. You can use this policy setting to override this behavior. If you enable this policy setting, client drive redirection isn't allowed in Remote Desktop Services sessions, and Clipboard file copy redirection isn't allowed on computers running Windows Server 2003, Windows 8, and Windows XP. If you disable this policy setting, client drive redirection is always allowed. Also, Clipboard file copy redirection is always allowed if Clipboard redirection is allowed. If you don't configure this policy setting, client drive redirection and Clipboard file copy redirection aren't specified at the Group Policy level.
  
  **Default**: Enabled
  
- **Prompt for password upon connection**  
  This policy setting specifies whether Remote Desktop Services always prompts the client for a password upon connection. You can use this setting to enforce a password prompt for users logging on to Remote Desktop Services, even if they already provided the password in the Remote Desktop Connection client. By default, Remote Desktop Services allows users to automatically log on by entering a password in the Remote Desktop Connection client. If you enable this policy setting, users can't automatically log on to Remote Desktop Services by supplying their passwords in the Remote Desktop Connection client. they're prompted for a password to log on. If you disable this policy setting, users can always log on to Remote Desktop Services automatically by supplying their passwords in the Remote Desktop Connection client. If you don't configure this policy setting, automatic logon isn't specified at the Group Policy level. 
  
  **Default**: Enabled
  
- **Remote desktop services client connection encryption level**  
  Specifies whether to require the use of a specific encryption level to secure communications between client computers and RD Session Host servers during Remote Desktop Protocol (RDP) connections. This policy only applies when you're using native RDP encryption. However, native RDP encryption (as opposed to SSL encryption) isn't recommended. This policy doesn't apply to SSL encryption. If you enable this policy setting, all communications between clients and RD Session Host servers during remote connections must use the encryption method specified in this setting. By default, the encryption level is set to High. The following encryption methods are available:  
  - *High*: The High setting encrypts data sent from the client to the server and from the server to the client by using strong 128-bit encryption. Use this encryption level in environments that contain only 128-bit clients (for example, clients that run Remote Desktop Connection). Clients that don't support this encryption level can't connect to RD Session Host servers.  
  - *Client Compatible*: The Client Compatible setting encrypts data sent between the client and the server at the maximum key strength supported by the client. Use this encryption level in environments that include clients that don't support 128-bit encryption.  
  - *Low*: The Low setting encrypts only data sent from the client to the server by using 56-bit encryption.  
  
  If you disable or don't configure this setting, the encryption level to be used for remote connections to RD Session Host servers isn't enforced through Group Policy. Important FIPS compliance can be configured through the System cryptography. Use FIPS-compliant algorithms for encryption, hashing, and signing settings in Group Policy (under Computer Configuration\Windows Settings\Security Settings\Local Policies\Security Options.) The FIPS-compliant setting encrypts and decrypts data sent from the client to the server and from the server to the client, with the Federal Information Processing Standard (FIPS) 140 encryption algorithms, by using Microsoft cryptographic modules. Use this encryption level when communications between clients and RD Session Host servers requires the highest level of encryption.
  
  **Default**: High
  
## Remote Management  
For more information, see [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) in the Windows documentation.  

- **Block storing run as credentials**  
  Client basic authentication
  
  **Default**: Enabled
  
- **Basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service accepts Basic authentication from a remote client. If you enable this policy setting, the WinRM service accepts Basic authentication from a remote client. If you disable or don't configure this policy setting, the WinRM service doesn't accept Basic authentication from a remote client.
  
  **Default**: Disabled
  
- **Block client digest authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Digest authentication. If you enable this policy setting, the WinRM client doesn't use Digest authentication. If you disable or don't configure this policy setting, the WinRM client uses Digest authentication.
  
  **Default**: Enabled
  
- **Unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) service sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.  
  
  **Default**: Disabled
  
- **Client unencrypted traffic**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client sends and receives unencrypted messages over the network. If you enable this policy setting, the WinRM client sends and receives unencrypted messages over the network. If you disable or don't configure this policy setting, the WinRM client sends or receives only encrypted messages over the network.
  
  **Default**: Disabled
  
- **Client basic authentication**  
  This policy setting allows you to manage whether the Windows Remote Management (WinRM) client uses Basic authentication. If you enable this policy setting, the WinRM client uses Basic authentication. If WinRM is configured to use HTTP transport, the user name and password are sent over the network as clear text. If you disable or don't configure this policy setting, the WinRM client doesn't use Basic authentication.
  
  **Default**: Disabled
  

## Remote Procedure Call  
For more information, see [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) in the Windows documentation.  

- **RPC unauthenticated client options**  
  This policy setting controls how the RPC server runtime handles unauthenticated RPC clients connecting to RPC servers. This policy setting impacts all RPC applications. In a domain environment, use this policy setting with caution as it can impact a wide range of functionality including group policy processing itself. Reverting a change to this policy setting can require manual intervention on each affected machine. This policy setting should never be applied to a domain controller. If you disable this policy setting, the RPC server runtime uses the value of "Authenticated" on Windows Client, and the value of "None" on Windows Server versions that support this policy setting. If you don't configure this policy setting, it remains disabled. The RPC server runtime behaves as though it was enabled with the value of "Authenticated" used for Windows Client and the value of "None" used for Server SKUs that support this policy setting. If you enable this policy setting, it directs the RPC server runtime to restrict unauthenticated RPC clients connecting to RPC servers running on a machine. A client is considered an authenticated client if it uses a named pipe to communicate with the server or if it uses RPC Security. RPC Interfaces that have specifically requested to be accessible by unauthenticated clients may be exempt from this restriction, depending on the selected value for this policy setting.  
  - *None* allows all RPC clients to connect to RPC Servers running on the machine on which the policy setting is applied. 
  - *Authenticated* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. Exemptions are granted to interfaces that have requested them. 
  - *Authenticated without exceptions* allows only authenticated RPC Clients (per the definition above) to connect to RPC Servers running on the machine on which the policy setting is applied. No exceptions are allowed. Note: This policy setting won't be applied until the system is rebooted.  

  **Default**: Authenticated

## Search 
For more information, see [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) in the Windows documentation.  

- **Disable indexing encrypted items**  
  Allows or disallows the indexing of items. This switch is for the Windows Search Indexer, which controls whether it will index items that are encrypted, such as the Windows Information Protection (WIP) protected files. When the policy is enabled, WIP protected items are indexed and the metadata about them are stored in an unencrypted location. The metadata includes things like file path and date modified. When the policy is disabled, the WIP protected items aren't indexed and don't show up in the results in Cortana or file explorer. There may also be a performance impact on photos and Groove apps if there are many WIP protected media files on the device.
  
**Default**: Yes
  
## Smart Screen  
For more information, see [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) in the Windows documentation.  

- **Block execution of unverified files**  
  Block user from running unverified files. 
  - *Not Configured* - Employees can ignore SmartScreen warnings and run malicious files. 
  - *Yes* – Employees can't ignore SmartScreen warnings and run malicious files.

  **Default**: Yes

- **Require SmartScreen for apps and files**  
  Allows IT Admins to configure SmartScreen for Windows.

  **Default**: Yes
  
## System  
For more information, see [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) in the Windows documentation.  

- **System boot start driver initialization**  
  This policy setting allows you to specify which boot-start drivers are initialized based on a classification determined by an Early Launch Antimalware boot-start driver. The Early Launch Antimalware boot-start driver can return the following classifications for each boot-start driver: 
  - *Good*: The driver has been signed and hasn't been tampered with.  
  - *Bad* - The driver has been identified as malware. We recommend that you don't allow known bad drivers to be initialized. 
  - *Bad, but required for boot*: The driver has been identified as malware, but the computer can't successfully boot without loading this driver. 
  - *Unknown* - This driver hasn't been attested to by your malware detection application and hasn't been classified by the Early Launch Antimalware boot-start driver.  

  If you enable this policy setting, you can choose which boot-start drivers to initialize the next time the computer is started. If you disable or don't configure this policy setting, the boot start drivers determined to be Good, Unknown, or Bad but Boot Critical are initialized and the initialization of drivers determined to be Bad is skipped. If your malware detection application doesn't include an Early Launch Antimalware boot-start driver or if your Early Launch Antimalware boot-start driver has been disabled, this setting has no effect and all boot-start drivers are initialized.  
  
  **Default**: Good unknown and bad critical


## Wi-Fi  
For more information, see [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) in the Windows documentation.  

- **Block Internet sharing**  
  Specifies whether internet sharing is possible on the device.  

  **Default**: Yes  

- **Block Automatically connecting to Wi-Fi hotspots**  
  Allow or disallow the device to automatically connect to Wi-Fi hotspots.  

  **Default**: Yes  
  
## Windows Connection Manager  
For more information, see [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) in the Windows documentation.  

- **Block connection to non-domain networks**  
  This policy setting prevents computers from connecting to both a domain-based network and a non-domain based network at the same time. If this policy setting is enabled, the computer responds to automatic and manual network connection attempts based on the following circumstances: 
  - Automatic connection attempts When the computer is already connected to a domain-based network, all automatic connection attempts to non-domain networks are blocked. When the computer is already connected to a non-domain based network, automatic connection attempts to domain-based networks are blocked. 
  - Manual connection attempts When the computer is already connected to either a non-domain based network or a domain-based network over media other than Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing network connection disconnects and the manual connection is allowed. When the computer is already connected to either a non-domain based network or a domain-based network over Ethernet, and a user attempts to create a manual connection to an additional network in violation of this policy setting, the existing Ethernet connection is maintained and the manual connection attempt is blocked.  

  If this policy setting isn't configured or is disabled, computers are allowed to connect simultaneously to both domain and non-domain networks.  

  **Default**: Enabled
  
## Windows Defender  
For more information, see [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) in the Windows documentation.  

- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Yes  

- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Block
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not, (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Send safe samples automatically 
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: 4
  
- **Script downloaded payload execution type**  
  Defender script downloaded payload execution type
  
  **Default**: Block
  
- **Prevent credential stealing type**  
  Windows Defender Credential Guard uses virtualization-based security to isolate secrets so that only privileged system software can access them. Unauthorized access to these secrets can lead to credential theft attacks, such as Pass-the-Hash or Pass-The-Ticket. Windows Defender Credential Guard prevents these attacks by protecting NTLM password hashes, Kerberos Ticket Granting Tickets, and credentials stored by applications as domain credentials.
  
  **Default**: Enable

- **Email content execution type**  
  This rule blocks the following file types from being run or launched from an email seen in either Microsoft Outlook or webmail (such as Gmail.com or Outlook.com): Executable files (such as .exe, .dll, or .scr) Script files (such as a PowerShell .ps, VisualBasic .vbs, or JavaScript .js file) Script archive files.
  
  **Default**: Block
  
- **Network protection type**  
  This policy allows you to turn on network protection (block/audit) or off in Windows Defender Exploit Guard. Network protection is a feature of Windows Defender Exploit Guard that protects employees using any app from accessing phishing scams, exploit-hosting sites, and malicious content on the Internet. This includes preventing third-party browsers from connecting to dangerous sites. Value type is integer. If you enable this setting, network protection is turned on and employees can't turn it off. Its behavior can be controlled by the following options: Block and Audit. If you enable this policy with the "Block" option, users and apps are blocked from connecting to dangerous domains. You can see this activity in Windows Defender Security Center. If you enable this policy with the "Audit" option, users/apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in Windows Defender Security Center. If you disable this policy, users/apps won't be blocked from connecting to dangerous domains. You'll not see any network activity in Windows Defender Security Center. If you don't configure this policy, network blocking is disabled by default.
  
  **Default**: Enable
  
- **Defender schedule scan day**  
  Defender schedule scan day.
  
  **Default**: Everyday
  
- **Cloud-delivered protection**  
  To best protect your PC, Windows Defender will send information to Microsoft about any problems it finds. Microsoft will analyze that information, learn more about problems affecting you and other customers, and offer improved solutions.
  
  **Default**:  Yes  

- **Defender potentially unwanted app action**  
  The potentially unwanted application (PUA) protection feature in Windows Defender Antivirus can identify and block PUAs from downloading and installing on endpoints in your network. These applications aren't considered viruses, malware, or other types of threats, but might perform actions on endpoints that adversely affect their performance or use. PUA can also refer to applications that are considered to have a poor reputation. Typical PUA behavior includes: Various types of software bundling Ad injection into web browsers Driver and registry optimizers that detect issues, request payment to fix the errors, but remain on the endpoint and make no changes or optimizations (also known as "rogue antivirus" programs). These applications can increase the risk of your network being infected with malware, cause malware infections to be harder to identify, and can waste IT resources in cleaning up the applications.  
  
  **Default**: Block  

- **Script obfuscated macro code type**  
  Malware and other threats can attempt to obfuscate or hide their malicious code in some script files. This rule prevents scripts that appear to be obfuscated from running.
  
  **Default**: Block
  
- **Scan removable drives during a full scan**  
  Allows Windows Defender to scan for malicious and unwanted software in removable drives (for example, flash drives) during a full scan. Windows Defender Antivirus scans all files on USB devices before execution.
  
  **Default**: Yes  
  
- **Scan archive files**  
  Defender scan archive files.
  
  **Default**: Yes
  
- **Behavior monitoring**  
  Allows or disallows Windows Defender Behavior Monitoring functionality.Embedded in Windows 10, these sensors collect and process behavioral signals from the operating system and sends this sensor data to your private, isolated, cloud instance of Microsoft Defender ATP.
  
  **Default**: Yes

- **Scan files opened from network folders**  
  If files are read-only, user won't be able to remove any detected malware.
  
  **Default**: Yes

- **Untrusted USB process type**  
  With this rule, admins can prevent unsigned or untrusted executable files from running from USB removable drives, including SD cards.
  
  **Default**: Block
  
- **Office apps other process injection type**  
  Office apps, including Word, Excel, PowerPoint, and OneNote, won't be able to inject code into other processes. This is typically used by malware to run malicious code in an attempt to hide the activity from antivirus scanning engines.
  
  **Default**:  Block
  
- **Office macro code allow Win32 imports type**  
  Malware can use macro code in Office files to import and load Win32 DLLs, which can then be used to make API calls to allow further infection throughout the system. This rule attempts to block Office files that contain macro code that is capable of importing Win32 DLLs. This includes Word, Excel, PowerPoint, and OneNote.
  
  **Default**: Block  
  
- **Defender cloud block level**  
  Defender cloud block level.
  
  **Default**: Not Configured

- **Real-time monitoring**  
  Defender requires real-time monitoring.
  
  **Default**: Yes
  
- **Office apps executable content creation or launch type**  
  This rule targets typical behaviors used by suspicious and malicious add-ons and scripts (extensions) that create or launch executable files. This is a typical malware technique. Extensions are blocked from being used by Office apps. Typically these extensions use the Windows Scripting Host (.wsh files) to run scripts that automate certain tasks or provide user-created add-on features
  
  **Default**: Block

## Windows Ink Workspace  
For more information, see [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) in the Windows documentation.  

- **Ink Workspace**  
  Specifies whether to allow the user to access the ink workspace. 
  - *Disabled* - access to ink workspace is disabled. The feature is turned off.
  - *Enabled* - The Ink Workspace feature is turned on, but the user can't access it above the lock screen.
  - *Not Configured* - The Ink Workspace feature is turned on, and the user can use it above the lock screen.  

  **Default**: Enabled
 
## Windows PowerShell  
For more information, see [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) in the Windows documentation.  

- **Power shell shell script block logging**  
  This policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log. If you enable this policy setting, Windows PowerShell will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation. If you disable this policy setting, logging of PowerShell script input is disabled. If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops. Enabling Invocation Logging generates a high volume of event logs. Note: This policy setting exists under both Computer Configuration and User Configuration in the Group Policy Editor. The Computer Configuration policy setting takes precedence over the User Configuration policy setting.
  
  **Default**: Enabled
 

End of PReview baseilne list  -->
