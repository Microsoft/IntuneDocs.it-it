---
title: Impostazioni delle baseline di sicurezza Windows per Intune
titleSuffix: Microsoft Intune
description: Impostazioni della baseline di sicurezza Windows supportate da Intune
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/05/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 67938f8697002f94f275f953510d1b0f4864a3fa
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566727"
---
# <a name="windows-security-baseline-settings-for-intune"></a>Impostazioni della baseline di sicurezza Windows per Intune  

Vedere le [impostazioni delle baseline di sicurezza di Windows](security-baselines.md) supportate da Microsoft Intune.  

> [!NOTE]  
> Le impostazioni della baseline di sicurezza di Windows sono in anteprima. Nella fase di anteprima, l'elenco delle impostazioni disponibili e l'ordine di presentazione di tali impostazioni in questo contenuto varieranno in base a quanto disponibile nel portale.  
>  
> Al termine della fase di anteprima, questo contenuto verrà aggiornato con l'elenco definitivo delle impostazioni della baseline di sicurezza supportate da Intune.  

## <a name="above-lock"></a>Notifiche sulla schermata di blocco  
Per altre informazioni, vedere [Policy CSP - AboveLock](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock) (Provider di servizi di configurazione dei criteri - AboveLock) nella documentazione di Windows.  

- **Bloccare la visualizzazione delle notifiche di tipo avviso popup**  
  L'impostazione di questo criterio consente di impedire la visualizzazione delle notifiche dell'app nella schermata di blocco. Se si abilita l'impostazione di questo criterio, le notifiche dell'app non vengono visualizzate nella schermata di blocco. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti possono scegliere quali app visualizzano le notifiche nella schermata di blocco.
  
  **Default**: Sì  

## <a name="app-runtime"></a>Runtime app    
Per altre informazioni, vedere [Policy CSP - AppRuntime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-appruntime
) (Provider di servizi di configurazione dei criteri - AppRuntime) nella documentazione di Windows.  

- **Account Microsoft facoltativi per le app di 
  Microsoft Store**  
L'impostazione di questo criterio consente di controllare se gli account Microsoft sono facoltativi per le app di Microsoft Store che richiedono un account per l'accesso. Questo criterio influisce solo sulle app di Microsoft Store che lo supportano. Se si abilita l'impostazione di questo criterio, le app di Microsoft Store che in genere richiedono un account Microsoft per l'accesso consentiranno agli utenti di accedere invece con un account aziendale. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti devono eseguire l'accesso con un account Microsoft.  
  
  **Impostazione predefinita**: Abilitato  

## <a name="application-management"></a>Gestione applicazioni   
Per altre informazioni, vedere [Policy CSP - ApplicationManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement) (Provider di servizi di configurazione dei criteri - ApplicationManagement) nella documentazione di Windows.  

- **Bloccare Game DVR (solo desktop)**  
  consente di specificare se la registrazione e la trasmissione dei giochi sono consentite.
  
  **Default**: Sì  

## <a name="auto-play"></a>Riproduzione automatica   
Per altre informazioni, vedere [Policy CSP - Autoplay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-autoplay) (Provider di servizi di configurazione dei criteri - Autoplay) nella documentazione di Windows.  

- **Comportamento di esecuzione automatica predefinito per la riproduzione automatica**  
  Questa impostazione influisce sul comportamento predefinito per i comandi di esecuzione automatica. I comandi di esecuzione automatica sono archiviati all'interno di file autorun.inf e sono in grado di avviare programmi di installazione e altre routine. Se *Abilitato*, gli amministratori possono modificare il comportamento di esecuzione automatica predefinito in un dispositivo che esegue Windows Vista o versioni successive. Il comportamento può essere impostato in modo da: a) disabilitare completamente i comandi di esecuzione automatica oppure b) ripristinare il comportamento delle versioni precedenti a Windows Vista che prevede l'esecuzione automatica del comando. Se impostato su *Disabilitato* o *Non configurato*, nei dispositivi con Windows Vista o versioni successive viene chiesto all'utente di confermare se eseguire o meno un comando di esecuzione automatica.
  
  **Default**: non eseguire  
  
- **Modalità di riproduzione automatica**  
  L'impostazione di questo criterio consente di disattivare la funzionalità AutoPlay. AutoPlay inizia a leggere il contenuto di un'unità non appena il supporto viene inserito nell'unità. Di conseguenza, il file di installazione dei programmi e la musica presente nel supporto audio vengono immediatamente avviati. Nelle versioni precedenti a Windows XP SP2, AutoPlay è disabilitato per impostazione predefinita nelle unità rimovibili, ad esempio l'unità floppy (ma non l'unità CD-ROM), e nelle unità di rete. A partire da Windows XP SP2, AutoPlay è abilitato anche per le unità rimovibili, tra cui le unità Zip e alcuni dispositivi di archiviazione di massa USB. Se si abilita l'impostazione di questo criterio, AutoPlay viene disabilitato nelle unità CD-ROM e per supporti rimovibili oppure viene disabilitato in tutte le unità. L'impostazione di questo criterio disabilita AutoPlay in tipi di unità aggiuntivi. Non è possibile usare questa impostazione per abilitare AutoPlay nelle unità in cui è disabilitato per impostazione predefinita. Se si disabilita o non si configura l'impostazione di questo criterio, AutoPlay è abilitato. Nota: l'impostazione di questo criterio è presente in entrambe le cartelle Configurazione computer e Configurazione utente. Se le impostazioni del criterio sono in conflitto, l'impostazione del criterio in Configurazione computer ha la precedenza su quella in Configurazione utente.
  
  **Impostazione predefinita**: Disabilitato

- **Bloccare la riproduzione automatica per i dispositivi non di volume**  
  L'impostazione di questo criterio non consente la funzionalità AutoPlay per i dispositivi MTP come fotocamere o telefoni. Se si abilita l'impostazione di questo criterio, la funzionalità AutoPlay non sarà consentita per i dispositivi MTP come fotocamere o telefoni. Se si disabilita o non si configura l'impostazione di questo criterio, la funzionalità AutoPlay è abilitata per i dispositivi non di volume.
  
  **Impostazione predefinita**: Abilitato  

## <a name="bitlocker"></a>Bitlocker    
Per altre informazioni, vedere [Policy CSP - Bitlocker](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bitlocker
) (Provider di servizi di configurazione dei criteri - Bitlocker) nella documentazione di Windows.  

- **Criterio per le unità rimovibili BitLocker**  
  L'impostazione di questo criterio viene usata per controllare il metodo di crittografia e il livello di codifica. I valori di questo criterio determinano il livello di codifica usato da BitLocker per la crittografia. Per una maggiore sicurezza, le aziende potrebbero voler controllare il livello di crittografia (AES-256 è un algoritmo più avanzato rispetto a AES-128). Se si abilita questa impostazione, sarà possibile configurare individualmente un algoritmo di crittografia e un livello di codifica per unità dati fisse, unità del sistema operativo e unità dati rimovibili. Per le unità fisse e del sistema operativo è consigliabile usare l'algoritmo XTS-AES. Per le unità rimovibili è consigliabile usare AES-CBC a 128 bit o AES-CBC a 256 bit se l'unità viene usata in altri dispositivi che non eseguono Windows 10 versione 1511 o successiva. La modifica del metodo di crittografia non produce alcun effetto se l'unità è già crittografata o se la crittografia è in corso. In questi casi, l'impostazione di questo criterio viene ignorata.

  Per i criteri di un'unità rimovibile locker Bit, configurare le impostazioni seguenti:

    - **Richiedere la crittografia per l'accesso in scrittura**  
      **Default**: Sì  
  
    - **Metodo di crittografia**  
      **Default**: AES a 256 bit CBC  

- **Criterio per le unità fisse BitLocker**  
  L'impostazione di questo criterio viene usata per controllare il metodo di crittografia e il livello di codifica. I valori di questo criterio determinano il livello di codifica usato da BitLocker per la crittografia. Per una maggiore sicurezza, le aziende potrebbero voler controllare il livello di crittografia (AES-256 è un algoritmo più avanzato rispetto a AES-128). Se si abilita questa impostazione, è possibile configurare individualmente un algoritmo di crittografia e un livello di codifica per unità dati fisse, unità del sistema operativo e unità dati rimovibili. Per le unità fisse e del sistema operativo è consigliabile usare l'algoritmo XTS-AES. Per le unità rimovibili è consigliabile usare AES-CBC a 128 bit o AES-CBC a 256 bit se l'unità viene usata in altri dispositivi che non eseguono Windows 10 versione 1511 o successiva. La modifica del metodo di crittografia non produce alcun effetto se l'unità è già crittografata o se la crittografia è in corso. In questi casi, l'impostazione di questo criterio viene ignorata.  
 
   Per la crittografica BitLocker unità criteri fissato, configurare le impostazioni seguenti: 
   - **Metodo di crittografia**
     **predefinito**: AES a 256 bit XTS  

- **Criterio per le unità di sistema BitLocker**  
  L'impostazione di questo criterio viene usata per controllare il metodo di crittografia e il livello di codifica. I valori di questo criterio determinano il livello di codifica usato da BitLocker per la crittografia. Per una maggiore sicurezza, le aziende potrebbero voler controllare il livello di crittografia (AES-256 è un algoritmo più avanzato rispetto a AES-128). Se si abilita questa impostazione, è possibile configurare individualmente un algoritmo di crittografia e un livello di codifica per unità dati fisse, unità del sistema operativo e unità dati rimovibili. Per le unità fisse e del sistema operativo è consigliabile usare l'algoritmo XTS-AES. Per le unità rimovibili è consigliabile usare AES-CBC a 128 bit o AES-CBC a 256 bit se l'unità viene usata in altri dispositivi che non eseguono Windows 10 versione 1511 o successiva. La modifica del metodo di crittografia non produce alcun effetto se l'unità è già crittografata o se la crittografia è in corso. In questi casi, l'impostazione di questo criterio viene ignorata.  

   Per i criteri di unità sistema locker Bit, configurare le impostazioni seguenti:
  - **Metodo di crittografia**  
    **Default**: AES a 256 bit XTS  

## <a name="browser"></a>Browser  
Per altre informazioni, vedere [Policy CSP - Browser](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser) (Provider di servizi di configurazione dei criteri - Browser) nella documentazione di Windows.  

- **Richiedere SmartScreen per Microsoft Edge**  
  Per impostazione predefinita, Microsoft Edge usa Windows Defender SmartScreen (attivato) per proteggere gli utenti da potenziali tentativi di phishing e software dannoso. Inoltre, per impostazione predefinita, gli utenti non possono disabilitare (disattivare) Windows Defender SmartScreen. L'abilitazione di questo criterio determina la disattivazione di Windows Defender SmartScreen e ne impedisce l'attivazione da parte degli utenti. Non configurare questo criterio per consentire agli utenti di scegliere di attivare o disattivare Windows Defender SmartScreen.  
  
  **Default**: Sì  
  
- **Bloccare l'accesso a siti dannosi**  
  Per impostazione predefinita, Microsoft Edge consente agli utenti di ignorare gli avvisi di Windows Defender SmartScreen relativi a siti potenzialmente dannosi, consentendo di visitare il sito. Con questo criterio, tuttavia, è possibile configurare Microsoft Edge per impedire agli utenti di ignorare gli avvisi, non consentendo di visitare il sito.
  
  **Default**: Sì  
  
- **Blocca il download di file non verificati** Per impostazione predefinita, Microsoft Edge consente agli utenti di ignorare gli avvisi di Windows Defender SmartScreen relativi a file potenzialmente dannosi, consentendo di continuare a scaricare i file non verificati. L'abilitazione di questo criterio impedisce agli utenti di ignorare gli avvisi, bloccando il download dei file non verificati.
  
  **Default**: Sì  
  
- **Bloccare lo strumento per la gestione delle password**  
  Per impostazione predefinita, Microsoft Edge usa automaticamente lo strumento per la gestione delle password, consentendo agli utenti di gestire le password localmente. La disabilitazione di questo criterio impedisce a Microsoft Edge di usare lo strumento per la gestione delle password. Non configurare questo criterio se si vuole consentire agli utenti di scegliere di salvare e gestire localmente le password tramite lo strumento per la gestione delle password.
  
  **Default**: Sì  
  
- **Impedire di ignorare gli errori di certificato**  
  L'impostazione di questo criterio impedisce all'utente di ignorare gli errori di certificato Secure Sockets Layer/Transport Layer Security (SSL/TLS) che interrompono l'esplorazione in Internet Explorer, ad esempio errori relativi a certificati "scaduti", "revocati" o con "nomi non corrispondenti". Se si abilita l'impostazione di questo criterio, l'utente non può continuare l'esplorazione. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente può scegliere di ignorare gli errori di certificato e continuare l'esplorazione.
  
  **Default**: Sì  

## <a name="connectivity"></a>Connettività  
Per altre informazioni, vedere [Policy CSP - Connectivity](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) (Provider di servizi di configurazione dei criteri - Connectivity) nella documentazione di Windows.  

- **Bloccare il download Internet per la Pubblicazione guidata sul Web e l'Ordinazione guidata via Internet**  
  L'impostazione di questo criterio specifica se Windows deve scaricare un elenco di provider per la Pubblicazione guidata sul Web e l'Ordinazione guidata via Internet. Queste procedure guidate consentono la selezione da un elenco di aziende che offrono servizi quali l'archiviazione online e la stampa di fotografie. Per impostazione predefinita, Windows visualizza i provider scaricati da un sito Web Windows oltre a quelli specificati nel Registro di sistema. Se si abilita l'impostazione di questo criterio, Windows non scarica provider e vengono visualizzati solo i provider di servizi memorizzati nella cache del Registro di sistema locale. Se si disabilita o non si configura l'impostazione di questo criterio, verrà scaricato un elenco di provider quando l'utente usa la Pubblicazione guidata sul Web o l'Ordinazione guidata via Internet. Per altre informazioni che includono i dettagli su come specificare i provider di servizi nel Registro di sistema, vedere la documentazione relativa alla Pubblicazione guidata sul Web e all'Ordinazione guidata via Internet.  
  
  **Impostazione predefinita**: Abilitato  

- **Bloccare il download di driver di stampa su HTTP**  
  L'impostazione di questo criterio specifica se consentire al client di scaricare pacchetti di driver di stampa su HTTP. Per configurare la stampa su HTTP è necessario scaricare su HTTP i driver non inclusi nel prodotto. Nota: l'impostazione di questo criterio non impedisce al client di eseguire la stampa su stampanti nella rete Intranet o su Internet tramite HTTP. Viene solo impedito il download di driver non installati in locale. Se si abilita l'impostazione di questo criterio, non sarà possibile scaricare i driver di stampa su HTTP. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti possono scaricare i driver di stampa su HTTP.
  
  **Impostazione predefinita**: Abilitato  

## <a name="credentials-delegation"></a>Delega di credenziali  
Per altre informazioni, vedere [Policy CSP - CredentialsDelegation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsdelegation
) (Provider di servizi di configurazione dei criteri - CredentialsDelegation) nella documentazione di Windows.  

- **Delega di credenziali non esportabili con l'host remoto**  
  L'host remoto consente la delega delle credenziali non esportabili. Quando si usa la delega delle credenziali, i dispositivi forniscono una versione di credenziali può essere esportata all'host remoto, che espone gli utenti a rischio di furto delle credenziali da utenti malintenzionati nell'host remoto. Se si abilita l'impostazione di questo criterio, l'host supporta la modalità di amministrazione limitata o la modalità Remote Credential Guard. Se si disabilita o non si configura l'impostazione di questo criterio, le modalità di amministrazione limitata e Remote Credential Guard non sono supportate. Gli utenti dovranno sempre passare le proprie credenziali all'host.  

  
  **Impostazione predefinita**: Abilitato  

## <a name="credentials-ui"></a>Interfaccia utente per le credenziali  
Per altre informazioni, vedere [Policy CSP - CredentialsUI](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-credentialsui) (Provider di servizi di configurazione dei criteri - CredentialsUI) nella documentazione di Windows.  

- **Enumera gli amministratori** L'impostazione di questo criterio determina la visualizzazione o meno degli account amministratore quando un utente prova a elevare i privilegi di un'applicazione in esecuzione. Per impostazione predefinita, gli account amministratore non vengono visualizzati quando l'utente prova a elevare i privilegi di un'applicazione in esecuzione. Se si abilita l'impostazione di questo criterio, vengono visualizzati tutti gli account amministratore locali del PC e l'utente potrà sceglierne uno e immettere la password corretta. Se si disabilita l'impostazione di questo criterio, per l'elevazione dei privilegi sarà sempre necessario digitare un nome utente e una password.  

  
  **Impostazione predefinita**: Disabilitato  

## <a name="data-protection"></a>Protezione dati  
Per altre informazioni, vedere [Policy CSP - DataProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection
) (Provider di servizi di configurazione dei criteri - DataProtection) nella documentazione di Windows.  

- **Blocca l'accesso diretto alla memoria**  
  L'impostazione di questo criterio consente di bloccare l'accesso diretto alla memoria (Direct Memory Access, DMA) per tutte le porte downstream PCI collegabili a sistema acceso finché un utente non accede a Windows. Dopo l'accesso di un utente, Windows enumererà i dispositivi PCI connessi alle porte PCI collegabili a sistema acceso. Ogni volta che l'utente blocca il computer, l'accesso diretto alla memoria viene bloccato sulle porte PCI collegabili a sistema acceso senza dispositivi figlio finché l'utente non accede di nuovo. I dispositivi già enumerati quando il computer era sbloccato continueranno a funzionare fino a quando non saranno scollegati. L'impostazione di questo criterio viene applicata solo quando è abilitato BitLocker o la crittografia del dispositivo.
  
  
  **Default**: Sì  

## <a name="device-guard"></a>Device Guard  
Per altre informazioni, vedere [Policy CSP - DeviceGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceguard
) (Provider di servizi di configurazione dei criteri - DeviceGuard) nella documentazione di Windows.  

- **Credential Guard**  
  Questa impostazione consente agli utenti di attivare Credential Guard con la sicurezza basata sulla virtualizzazione per proteggere le credenziali al riavvio successivo.
   
  **Default**: Abilita con blocco UEFI 

- **Abilitare la sicurezza basata sulla virtualizzazione**  </br>
  Attiva la sicurezza basata sulla virtualizzazione al riavvio successivo. La sicurezza basata sulla virtualizzazione usa Windows Hypervisor per offrire il supporto per i servizi di sicurezza.
  
  **Default**: Sì  

<!-- not yet available 
- **Enable secure boot with DMA**  
  Among the commands that follow, you can choose settings for Secure Boot and Secure Boot with DMA. In most situations, we recommend that you choose Secure Boot. This option provides Secure Boot with as much protection as is supported by a given computer’s hardware. A computer with input/output memory management units (IOMMUs) will have Secure Boot with DMA protection. A computer without IOMMUs will simply have Secure Boot enabled. In contrast, with Secure Boot with DMA, the setting will enable Secure Boot—and VBS itself—only on a computer that supports DMA, that is, a computer with IOMMUs. With this setting, any computer without IOMMUs won't have VBS or HVCI protection, although it can still have WDAC enabled.
  
  
  **Default**: Yes  
  -->
- **Avvia Protezione del sistema**    
  **Impostazione predefinita**: Abilitato  

## <a name="device-installation"></a>Installazione di dispositivi  
Per altre informazioni, vedere [Policy CSP - DeviceInstallation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation) (Provider di servizi di configurazione dei criteri - DeviceInstallation) nella documentazione di Windows.  

- **Installazione di dispositivi hardware per identificatori di dispositivo**  
  L'impostazione di questo criterio consente di specificare un elenco di ID hardware Plug and Play e ID compatibili per i dispositivi la cui installazione non è consentita in Windows. L'impostazione di questo criterio ha la precedenza su qualsiasi altra impostazione di criteri che consente a Windows di installare un dispositivo. Se si abilita l'impostazione di questo criterio, viene impedito a Windows di installare i dispositivi il cui ID hardware o ID compatibile sia presente nell'elenco creato. Se si abilita l'impostazione di questo criterio in un server desktop remoto, l'impostazione del criterio influirà sul reindirizzamento dei dispositivi specificati da un client desktop remoto al server desktop remoto. Se si disabilita o non si configura l'impostazione di questo criterio, è possibile installare e aggiornare i dispositivi in base a quanto consentito o impedito da altre impostazioni di criteri.
  
  **Impostazione predefinita**: Blocca l'installazione del dispositivo hardware  

    Quando *bloccare l'installazione dei dispositivi hardware* è selezionata, le impostazioni seguenti sono disponibili.
  
    - **Rimuovi i dispositivi hardware corrispondenti**   
    Questa impostazione è disponibile solo quando l'*installazione di dispositivi hardware per identificatori di dispositivo* è impostata su *Bloccare l'installazione del dispositivo hardware*.
      
      **Default**: Sì
  
    - **Identificatori di dispositivo hardware bloccati**  
       Questa impostazione è disponibile solo quando l'*installazione di dispositivi hardware per identificatori di dispositivo* è impostata su *Bloccare l'installazione del dispositivo hardware*.
      
      **Default**: Sì  
  
- **Installazione di dispositivi hardware per classi di installazione**  
  L'impostazione di questo criterio consente di specificare un elenco di identificatori univoci globali (GUID) della classe di installazione del dispositivo per i driver di dispositivo la cui installazione non è consentita in Windows. L'impostazione di questo criterio ha la precedenza su qualsiasi altra impostazione di criteri che consente a Windows di installare un dispositivo. Se si abilita l'impostazione di questo criterio, viene impedito a Windows di installare o aggiornare i driver di dispositivo il cui GUID della classe di installazione del dispositivo sia presente nell'elenco creato. Se si abilita l'impostazione di questo criterio in un server desktop remoto, l'impostazione del criterio influirà sul reindirizzamento dei dispositivi specificati da un client desktop remoto al server desktop remoto. Se si disabilita o non si configura l'impostazione di questo criterio, Windows potrà installare e aggiornare i dispositivi in base a quanto consentito o impedito da altre impostazioni di criteri.
  
  **Impostazione predefinita**: Blocca l'installazione del dispositivo hardware  

    Quando *bloccare l'installazione dei dispositivi hardware* è selezionata, le impostazioni seguenti sono disponibili.
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
  
  **Impostazione predefinita**: Abilitato  

- **Richiedere la password**  
  Specifica se il blocco del dispositivo è abilitato.
  
  **Default**: Sì  
  
    Quando *Richiedi password* è impostata su *Yes*, sono disponibili le seguenti impostazioni.

    - **Conteggio set di caratteri minimo password**  
      Numero di tipi di elementi complessi (lettere maiuscole e minuscole, numeri e punteggiatura) richiesto per un PIN o una password complessa. PIN applica il comportamento seguente per dispositivi mobili e desktop: 1 - richiesto 3 - cifre, lettere minuscole, vi sono cifre solo 2 - cifre e lettere minuscole e lettere maiuscole sono obbligatori. Non supportato negli account Microsoft desktop e negli account di dominio. 4 - Cifre, lettere minuscole, lettere maiuscole e caratteri speciali obbligatori. Non supportato nei dispositivi desktop. Il valore predefinito è 1. 
      
      **Impostazione predefinita**: 3  
  
    - **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**  
      Numero di errori di autenticazione consentiti prima che il dispositivo venga cancellato. Il valore 0 disabilita la funzionalità di cancellazione del dispositivo.
        
      **Impostazione predefinita**: 10  
  
    - **Scadenza password (giorni)**  
      L'impostazione del criterio Validità massima password specifica per quanto tempo (giorni) è possibile usare una password prima che il sistema richieda all'utente di modificarla. È possibile impostare la scadenza delle password dopo un numero di giorni compreso tra 1 e 999 oppure è possibile specificare che le password non hanno scadenza impostando il numero di giorni su 0. Se la Validità massima password è compresa tra 1 e 999 giorni, la Validità minima password deve essere inferiore della validità massima password. Se la Validità massima password è impostata su 0, la Validità minima password può essere qualsiasi valore compreso tra 0 e 998 giorni.
      
      **Impostazione predefinita**: 60  
  
    - **Tipo di password richiesto**  
      Determina il tipo di PIN o password obbligatorio.
      
      **Default**: caratteri alfanumerici  
  
    - **Lunghezza minima password**  
      L'impostazione del criterio Lunghezza minima password determina il numero minimo di caratteri della password di un account utente. È possibile impostare un valore compreso tra 1 e 14 caratteri oppure è possibile specificare che non è richiesta alcuna password impostando il numero di caratteri su 0.
      
      **Impostazione predefinita**: 8  
  
    - **Bloccare le password semplici**  
      Specifica se sono consentiti PIN o password come "1111" o "1234". Per il desktop, controlla anche l'uso di password grafiche.
      
      **Default**: Sì  
        *L'impostazione Sì impedisce l'uso di password semplici.* 

  - **Impedisci riutilizzo delle password precedenti**  
    Specifica il numero di password che possono essere archiviate nella cronologia che non possono essere usate. Il valore include la password corrente dell'utente. Ad esempio, con un'impostazione pari *1* l'utente non è possibile riutilizzare la password corrente quando si sceglie una nuova password. Un'impostazione pari *5* significa che un utente non è possibile impostare la nuova password per la password corrente o uno qualsiasi dei quattro password precedente.
    
    **Impostazione predefinita**: 24  

- **Impedire la presentazione**  
  Disabilita le impostazioni per la presentazione nella schermata di blocco in Impostazioni PC e impedisce l'esecuzione di una presentazione nella schermata di blocco. Per impostazione predefinita, gli utenti possono abilitare una presentazione da eseguire dopo il blocco del computer. Se si abilita questa impostazione, gli utenti non possono modificare le impostazioni di presentazione in impostazioni PC e non può avviare alcuna presentazione di diapositive.
  
    **Impostazione predefinita**: Abilitato  
    *L'impostazione Abilitato impedisce l'esecuzione delle presentazioni.* 

- **Validità minima password in giorni**  
  L'impostazione del criterio Validità minima password specifica il periodo di tempo (in giorni) per cui è necessario usare una password prima che l'utente possa modificarla. È possibile impostare un valore compreso tra 1 e 998 giorni oppure è possibile consentire la modifica della password immediatamente impostando il numero di giorni su 0. La Validità minima password deve essere minore della Validità massima password, a meno che la Validità massima password non sia impostata su 0 che indica che le password non hanno scadenza. Se la Validità massima password è impostata su 0, la Validità minima password può essere impostata su qualsiasi valore compreso tra 0 e 998 giorni.
  
    **Impostazione predefinita**: 1  

## <a name="event-log-service"></a>Servizio Registro eventi  
Per altre informazioni, vedere [Policy CSP - EventLogService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-eventlogservice) (Provider di servizi di configurazione dei criteri - EventLogService) nella documentazione di Windows.  

- **Dimensioni massime del file registro di protezione in KB**  
  L'impostazione di questo criterio specifica le dimensioni massime del file di registro espressa in KB. Se si abilita l'impostazione di questo criterio, è possibile configurare le dimensioni massime del file di registro in modo che siano comprese tra 1 MB (1024 KB) e 2 TB (2147483647 KB) in base a incrementi in KB. Se si disabilita o non si configura l'impostazione di questo criterio, le dimensioni massime del file di registro vengono impostate sul valore configurato in locale. Questo valore può essere modificato dall'amministratore locale usando la finestra di dialogo Proprietà registro e l'impostazione predefinita è 20 MB.
  
   **Impostazione predefinita**: 196608  

- **Dimensioni massime del file registro di sistema in KB**  
  L'impostazione di questo criterio specifica le dimensioni massime del file di registro espressa in KB. Se si abilita l'impostazione di questo criterio, è possibile configurare le dimensioni massime del file di registro in modo che siano comprese tra 1 MB (1024 KB) e 2 TB (2147483647 KB) in base a incrementi in KB. Se si disabilita o non si configura l'impostazione di questo criterio, le dimensioni massime del file di registro vengono impostate sul valore configurato in locale. Questo valore può essere modificato dall'amministratore locale usando la finestra di dialogo Proprietà registro e l'impostazione predefinita è 20 MB.
  
  **Impostazione predefinita**: 32768  

- **Dimensioni massime del file registro applicazioni in KB**  
  L'impostazione di questo criterio specifica le dimensioni massime del file di registro espressa in KB. Se si abilita l'impostazione di questo criterio, è possibile configurare le dimensioni massime del file di registro in modo che siano comprese tra 1 MB (1024 KB) e 2 TB (2147483647 KB) in base a incrementi in KB. Se si disabilita o non si configura l'impostazione di questo criterio, le dimensioni massime del file di registro vengono impostate sul valore configurato in locale. Questo valore può essere modificato dall'amministratore locale usando la finestra di dialogo Proprietà registro e l'impostazione predefinita è 20 MB.
  
  **Impostazione predefinita**: 32768  

## <a name="experience"></a>Esperienza  
Per altre informazioni, vedere [Policy CSP - Experience](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience) (Provider di servizi di configurazione dei criteri - Experience) nella documentazione di Windows.  

- **Bloccare Contenuti in evidenza di Windows**  
  Consente agli amministratori IT di disattivare tutte le funzionalità di Contenuti in evidenza di Windows, Contenuti in evidenza di Windows nella schermata di blocco, Suggerimenti di Windows, le funzionalità per gli utenti consumer Microsoft e altre funzionalità correlate.
  
  **Default**: Sì  

  Quando *Blocca Windows Spotlight* è impostata su *Yes*, sono disponibili le seguenti impostazioni.
  
  - **Bloccare i suggerimenti di terze parti in Contenuti in evidenza di Windows**  
    Specifica se consentire o meno i suggerimenti su app e contenuto di autori o distributori di software di terze parti nelle funzionalità di Contenuti in evidenza di Windows come Contenuti in evidenza di Windows nella schermata di blocco, le app suggerite nel menu Start e Suggerimenti di Windows. Gli utenti possono comunque visualizzare i suggerimenti per le funzionalità, le app e i servizi Microsoft.
      
    **Default**: Sì  
   - **Bloccare le funzionalità specifiche per i consumer**  
      Consente agli amministratori IT di attivare le esperienze solitamente riservate ai consumer, ad esempio i suggerimenti del menu Start, le notifiche sull'appartenenza, l'installazione di app post-OOBE e i riquadri di reindirizzamento.
      
     **Default**: Sì  


## <a name="exploit-guard"></a>Exploit Guard  
Per altre informazioni, vedere [Policy CSP - ExploitGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-exploitguard) (Provider di servizi di configurazione dei criteri - ExploitGuard) nella documentazione di Windows.  

- **XML di Protezione dagli exploit**  
  Consente all'amministratore IT di distribuire una configurazione che rappresenta il sistema desiderato e le opzioni di mitigazione delle applicazioni a tutti i dispositivi nell'organizzazione. La configurazione è rappresentata da un XML. La Protezione dagli exploit consente di proteggere i dispositivi da malware che usa gli exploit per la diffusione e l'infezione. Usare l'app Sicurezza di Windows o PowerShell per creare un set di mitigazioni, chiamato configurazione. È quindi possibile esportare la configurazione come file XML e condividerla con più computer in rete in modo che abbiano lo stesso set di impostazioni di mitigazione. È anche possibile convertire e importare un file XML di configurazione EMET esistente in un file XML di configurazione di protezione dagli exploit.
  
  **Default**: *viene fornito xml di esempio* 
 
## <a name="file-explorer"></a>Esplora file  
Per altre informazioni, vedere [Policy CSP - FileExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-fileexplorer) (Provider di servizi di configurazione dei criteri - FileExplorer) nella documentazione di Windows.  

- **Bloccare Protezione esecuzione programmi**  
  La disattivazione di Protezione esecuzione programmi può consentire ad alcune applicazioni plug-in legacy di funzionare senza terminare Explorer.
  
  **Impostazione predefinita**: Disabilitato  
   
- **Bloccare la terminazione heap in caso di danneggiamento**  
  Disabilitando la terminazione dell'heap in caso di danneggiamento, è possibile consentire il funzionamento di determinate applicazioni plug-in legacy senza terminare immediatamente Esplora risorse, sebbene quest'ultimo possa terminare in maniera imprevista in un secondo momento.
  
  **Impostazione predefinita**: Disabilitato  
    

## <a name="internet-explorer"></a>Internet Explorer  
Per altre informazioni, vedere [Policy CSP - InternetExplorer](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-internetexplorer) (Provider di servizi di configurazione dei criteri - InternetExplorer) nella documentazione di Windows.  
<!-- not yet available 
- **Scan incoming mail messages**  
  Allows or disallows scanning of email.
  
  **Default**: Disabled  
  
- **Office apps launch child process type**  
  Office apps won't be allowed to create child processes. This includes Word, Excel, PowerPoint, OneNote, and Access. This is a typical malware behavior, especially for macro-based attacks that attempt to use Office apps to launch or download malicious executables.
  
  **Default**: Disable  
  
- **Defender sample submission consent type**  
  Checks for the user consent level in Windows Defender to send data. If the required consent has already been granted, Windows Defender submits them. If not (and if the user has specified never to ask), the UI is launched to ask for user consent (when Defender/AllowCloudProtection is allowed) before sending data.
  
  **Default**: Disable  
  
- **Signature update interval (in hours)**  
  Defender signature update interval in hours
  
  **Default**: Disabled  
 -->
- **Accesso dell'area Internet di Internet Explorer alle origini dati**  
  L'impostazione di questo criterio consente di gestire l'accesso da parte di Internet Explorer a dati appartenenti a un'altra area di sicurezza usando Microsoft XML Parser (MSXML) o ActiveX Data Objects (ADO). Se si abilita l'impostazione di questo criterio, gli utenti potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire il caricamento di una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se non si configura l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Trascinare contenuto da domini diversi all'interno delle finestre**  
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono nella stessa finestra. Gli utenti non possono modificare questa impostazione nella finestra di dialogo Opzioni Internet.
  
  **Impostazione predefinita**: Disabilitato
  
- **Internet Explorer - Avviso di indirizzo di certificato non corrispondente**  
  L'impostazione di questo criterio consente di attivare l'avviso di sicurezza in caso di indirizzi di certificati non corrispondenti. Quando l'impostazione di questo criterio è abilitata, l'utente riceverà un avviso quando visita siti Web HTTP protetti (HTTPS) che contengono certificati emessi per un sito Web con un altro indirizzo. Questo avviso aiuta a prevenire attacchi di spoofing. Se si abilita l'impostazione di questo criterio, l'avviso di mancata corrispondenza negli indirizzi dei certificati verrà sempre visualizzato. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà scegliere se visualizzare o meno l'avviso di mancata corrispondenza negli indirizzi dei certificati usando la pagina Avanzate nel Pannello di controllo Internet.
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area con restrizioni - Siti con privilegi inferiori**  
  L'impostazione di questo criterio consente di gestire l'esplorazione dell'area da parte di siti Web appartenenti ad aree con privilegi inferiori, ad esempio i siti Internet. Se si abilita l'impostazione di questo criterio, i siti Web appartenenti ad aree con privilegi inferiori possono aprire nuove finestre all'interno dell'area o esplorarla. L'area sarà priva del livello di sicurezza aggiuntivo offerto dalla funzionalità di sicurezza Protezione da elevazione privilegi dell'area. Se si seleziona Chiedi conferma nella casella a discesa, viene visualizzato un avviso che informa l'utente dei potenziali rischi dell'esplorazione. Se si disabilita l'impostazione di questo criterio, un'esplorazione potenzialmente dannosa non sarà consentita. Questa funzionalità di sicurezza di Internet Explorer viene abilitata per l'area, come specificato dall'impostazione del controllo della funzionalità Protezione da elevazione privilegi dell'area. Se non si configura l'impostazione di questo criterio, le esplorazioni potenzialmente dannose non saranno consentite. Questa funzionalità di sicurezza di Internet Explorer viene abilitata per l'area, come specificato dall'impostazione del controllo della funzionalità Protezione da elevazione privilegi dell'area.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Richiesta automatica per il download di file**  
  L'impostazione di questo criterio determina se viene visualizzata una richiesta di conferma per i download di file non originati dall'utente. Per i download di file originati dall'utente, verranno visualizzate le apposite finestre di dialogo indipendentemente da questa impostazione. Se si abilita questa impostazione, verrà visualizzata una finestra di dialogo per i tentativi automatici di download di file. Se si disabilita o non si configura questa impostazione, i download di file non originati dall'utente vengono bloccati e verrà visualizzata la barra di notifica anziché la finestra di dialogo per il download di file. Gli utenti potranno quindi fare clic sulla barra di notifica per confermare il download del file.
  
  **Impostazione predefinita**: Disabilitato
  
- **Internet Explorer - Area Internet - Componenti basati su .NET Framework**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte di Internet Explorer dei componenti .NET Framework non firmati con Authenticode. Fra questi componenti sono inclusi i controlli gestiti a cui fa riferimento un tag oggetto e gli eseguibili gestiti a cui fa riferimento un collegamento. Se si abilita l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti senza firma. Se si seleziona Chiedi conferma nella casella a discesa, Internet Explorer chiederà all'utente di scegliere se consentire l'esecuzione di componenti gestiti senza firma. Se si disabilita l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti senza firma. Se non si configura l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti senza firma.
  
  **Default**: disabilitare 
  
- **Internet Explorer - Area Internet - Consentire solo ai domini approvati di usare i controlli ActiveX TDC**  
  Questa impostazione criterio controlla se l'utente può eseguire il controllo ActiveX TDC nei siti Web. Se si abilita l'impostazione di questo criterio, il controllo ActiveX TDC non verrà eseguito dai siti Web in quest'area. Se si disabilita l'impostazione di questo criterio, il controllo ActiveX TDC verrà eseguito da tutti i siti Web in quest'area.
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area con restrizioni - Finestre aperte da script**  
  L'impostazione di questo criterio consente di gestire le restrizioni nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato. Se si abilita l'impostazione di questo criterio, la funzionalità di sicurezza relativa alle restrizioni per Windows non verrà applicata nell'area. L'area di sicurezza verrà eseguita senza il livello di sicurezza aggiuntivo offerto da questa funzionalità. Se si disabilita l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo. Se non si configura l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo.
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Includere percorso locale nel caricamento di file sul server**  
  L'impostazione di questo criterio consente di specificare se inviare le informazioni sul percorso locale quando l'utente carica un file tramite un modulo HTML. Se le informazioni sul percorso locale vengono inviate, alcune di esse potrebbero essere rese note al server accidentalmente. I file inviati dal desktop di un utente, ad esempio, potrebbero contenere il nome utente come parte del percorso. Se si abilita l'impostazione di questo criterio, le informazioni sul percorso locale verranno inviate quando l'utente carica un file tramite un modulo HTML. Se si disabilita l'impostazione di questo criterio, le informazioni sul percorso verranno rimosse quando l'utente carica un file tramite un modulo HTML. Se non si configura l'impostazione di questo criterio, l'utente potrà scegliere se inviare le informazioni sul percorso quando carica un file tramite un modulo HTML. Per impostazione predefinita, le informazioni sul percorso vengono inviate.
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Disabilitare i processi in modalità protetta avanzata**  
  L'impostazione di questo criterio determina se Internet Explorer 11 usa i processi a 64 bit (per maggiore sicurezza) o a 32 bit (per maggiore compatibilità) durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Importante: alcuni controlli ActiveX e alcune barre degli strumenti potrebbero non essere disponibili quando vengono usati processi a 64 bit. Se si abilita l'impostazione di questo criterio, Internet Explorer 11 userà processi schede a 64 bit durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Se si disabilita l'impostazione di questo criterio, Internet Explorer 11 userà processi schede a 32 bit durante l'esecuzione in modalità protetta avanzata nelle versioni di Windows a 64 bit. Se non si configura l'impostazione di questo criterio, gli utenti possono attivare o disattivare questa funzionalità tramite le impostazioni di Internet Explorer. Questa funzionalità è disattivata per impostazione predefinita.
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Ignorare gli errori di certificato**  
  L'impostazione di questo criterio impedisce all'utente di ignorare gli errori di certificato Secure Sockets Layer/Transport Layer Security (SSL/TLS) che interrompono l'esplorazione in Internet Explorer, ad esempio errori relativi a certificati "scaduti", "revocati" o con "nomi non corrispondenti". Se si abilita l'impostazione di questo criterio, l'utente non può continuare l'esplorazione. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente può scegliere di ignorare gli errori di certificato e continuare l'esplorazione.
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Caricamento di file XAML**  
  L'impostazione di questo criterio consente di gestire il caricamento di file XAML (Extensible Application Markup Language). XAML è un linguaggio di markup dichiarativo basato su XML usato spesso per la creazione di grafica e interfacce utente avanzate che sfruttano la piattaforma Windows Presentation Foundation. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file XAML vengono caricati automaticamente in Internet Explorer. L'utente non può modificare questo comportamento. Se nella casella a discesa è selezionata Chiedi conferma, prima del caricamento dei file XAML viene chiesta conferma all'utente. Se si disabilita l'impostazione di questo criterio, i file XAML non vengono caricati in Internet Explorer. L'utente non può modificare questo comportamento. Se non si configura l'impostazione di questo criterio, l'utente può decidere se caricare i file XAML in Internet Explorer.
  
  **Default**: disabilitare 
  
- **Internet Explorer - Area Internet - Richiesta automatica per il download di file**  
  L'impostazione di questo criterio determina se viene visualizzata una richiesta di conferma per i download di file non originati dall'utente. Per i download di file originati dall'utente, verranno visualizzate le apposite finestre di dialogo indipendentemente da questa impostazione. Se si abilita questa impostazione, verrà visualizzata una finestra di dialogo per i tentativi automatici di download di file. Se si disabilita o non si configura questa impostazione, i download di file non originati dall'utente vengono bloccati e verrà visualizzata la barra di notifica anziché la finestra di dialogo per il download di file. Gli utenti potranno quindi fare clic sulla barra di notifica per confermare il download del file.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Avviso di sicurezza per file potenzialmente dannosi**  
  L'impostazione di questo criterio consente di controllare la visualizzazione dell'avviso "Apri file - Avviso di sicurezza" quando l'utente prova ad aprire file eseguibili o altri file potenzialmente non sicuri, ad esempio da una condivisione file Intranet usando Esplora file. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file verranno aperti senza visualizzare l'avviso di sicurezza. Se nella casella a discesa è selezionata Chiedi conferma, prima dell'apertura dei file viene visualizzato un avviso di sicurezza. Se si disabilita l'impostazione di questo criterio, i file non verranno aperti. Se non si configura l'impostazione di questo criterio, l'utente può configurare la modalità di gestione di questi file. Per impostazione predefinita, questi file vengono bloccati nell'area con restrizioni, abilitati nell'area Intranet e del computer locale e impostati su Chiedi conferma nelle aree attendibili e Internet.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Filtro XSS**  
  Questo criterio consente di specificare se il filtro XSS rileverà e impedirà gli attacchi tramite script da altri siti nei siti Web in quest'area. Se si abilita l'impostazione di questo criterio, il filtro XSS è attivato per i siti in quest'area e prova a bloccare gli attacchi tramite script da altri siti. Se si disabilita l'impostazione di questo criterio, il filtro XSS è disabilitato per i siti in quest'area e Internet Explorer non impedirà gli attacchi tramite script da altri siti.
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Fallback in SSL3**  
  L'impostazione di questo criterio consente di bloccare un fallback non sicuro in SSL 3.0. Quando questo criterio è abilitato, Internet Explorer tenterà di connettersi ai siti che usano SSL 3.0 o versione precedente quando non viene stabilita la connessione tramite TLS 1.0 o versione successiva. È consigliabile non consentire il fallback non sicuro per evitare attacchi man-in-the-middle. Questo criterio non influisce sui protocolli di sicurezza abilitati. Se si disabilita questo criterio, vengono usate le impostazioni predefinite di sistema.
  
  **Default**: nessun sito 
  
- **Internet Explorer - Area Internet bloccata - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area con restrizioni - Avviare programmi e file in un IFRAME**  
  L'impostazione di questo criterio consente di gestire l'esecuzione di applicazioni e il download di file da un riferimento IFRAME nel codice HTML delle pagine appartenenti all'area. Se si abilita l'impostazione di questo criterio, è possibile eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area senza intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di applicazioni e il download di file da IFRAME nelle pagine dell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non possono eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area. Se non si configura l'impostazione di questo criterio, gli utenti non possono eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area.
  
  **Default**: disabilitare 
  
- **Internet Explorer ignorare gli avvisi di SmartScreen relativi file non comuni**  
  L'impostazione di questo criterio determina se l'utente può ignorare gli avvisi del filtro SmartScreen. Il filtro SmartScreen segnala i file eseguibili che gli utenti di Internet Explorer non scaricano spesso da Internet. Se si abilita l'impostazione di questo criterio, gli avvisi del filtro SmartScreen bloccheranno l'utente. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà ignorare gli avvisi del filtro SmartScreen.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Blocco popup**  
  L'impostazione di questo criterio consente di gestire la visualizzazione di finestre popup indesiderate. Le finestre popup visualizzate quando l'utente finale fa clic su un collegamento non vengono bloccate. Se si abilita l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup indesiderate. Se si disabilita l'impostazione di questo criterio, non viene impedita la visualizzazione delle finestre popup. Se non si configura l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup.
  
  **Default**: abilitare  
  
- **Gestione MIME coerente dei processi di Internet Explorer**  
  Internet Explorer contiene comportamenti binari dinamici, ovvero componenti che incapsulano funzionalità specifiche per gli elementi HTML a cui sono associati. L'impostazione di questo criterio determina se l'impostazione Restrizione di sicurezza comportamenti binari è consentita o meno. Se si abilita l'impostazione di questo criterio, i comportamenti binari non saranno consentiti per i processi di Esplora file e Internet Explorer. Se si disabilita l'impostazione di questo criterio, i comportamenti binari saranno consentiti per i processi di Esplora file e Internet Explorer. Se non si configura l'impostazione di questo criterio, i comportamenti binari non saranno consentiti per i processi di Esplora file e Internet Explorer.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer ha le autorizzazioni di java di zona**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.
  
  **Default**: disabilitare java  
    
  
- **Internet Explorer - Controlli Active X in modalità protetta**  
  Questa impostazione consente di impedire l'esecuzione di controlli ActiveX in modalità protetta, quando è attivata la modalità protetta avanzata. Se un utente ha un controllo ActiveX installato non compatibile con la modalità protetta avanzata e un sito Web prova a caricare il controllo, Internet Explorer visualizza una notifica e offre la possibilità all'utente di eseguire il sito Web in modalità protetta normale. Questa impostazione disabilita la notifica e impone l'esecuzione in modalità protetta avanzata per tutti i siti Web. La modalità protetta avanzata offre maggiore protezione da siti Web dannosi utilizzando processi a 64 bit nelle versioni a 64 bit di Windows. Per i computer che eseguono almeno Windows 8, la modalità protetta avanzata limita anche i percorsi leggibili da Internet Explorer nel Registro di sistema e nel file system. Quando è abilitata la modalità protetta avanzata e un utente visita un sito Web che prova a caricare un controllo ActiveX non compatibile con la modalità protetta avanzata, Internet Explorer visualizza una notifica e offre la possibilità all'utente di disabilitare la modalità protetta avanzata per tale sito Web specifico. Se si abilita questa impostazione, Internet Explorer non offre all'utente la possibilità di disabilitare la modalità protetta avanzata. Tutti i siti Web in modalità protetta verranno eseguiti in modalità protetta avanzata. Se l'impostazione viene disabilitata o non configurata, Internet Explorer visualizza una notifica per gli utenti e offre la possibilità di eseguire i siti Web con controlli ActiveX non compatibili in modalità protetta normale.  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Caricamento di file XAML**  
  L'impostazione di questo criterio consente di gestire il caricamento di file XAML (Extensible Application Markup Language). XAML è un linguaggio di markup dichiarativo basato su XML usato spesso per la creazione di grafica e interfacce utente avanzate che sfruttano la piattaforma Windows Presentation Foundation. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file XAML vengono caricati automaticamente in Internet Explorer. L'utente non può modificare questo comportamento. Se nella casella a discesa è selezionata Chiedi conferma, prima del caricamento dei file XAML viene chiesta conferma all'utente. Se si disabilita l'impostazione di questo criterio, i file XAML non vengono caricati in Internet Explorer. L'utente non può modificare questo comportamento. Se non si configura l'impostazione di questo criterio, l'utente può decidere se caricare i file XAML in Internet Explorer.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Processi - Restrizioni di sicurezza finestre controllate da script**  
  Internet Explorer consente agli script di aprire, ridimensionare e riposizionare a livello di programmazione finestre di vari tipi. La funzionalità di sicurezza relativa alle restrizioni per le finestre consente di impostare restrizioni per le finestre popup e di impedire agli script di visualizzare finestre in cui la barra del titolo e la barra di stato non sono visibili all'utente o coprono la barra del titolo e la barra di stato di altre finestre. Se si abilita l'impostazione di questo criterio, vengono impostate restrizioni sulle finestre controllate da script per tutti i processi. Se si disabilita o non si configura l'impostazione di questo criterio, non viene impostata alcuna restrizione per le finestre controllate da script.
  
  **Impostazione predefinita**: Abilitato   
  
- **Internet Explorer - Area con restrizioni - Eseguire controlli ActiveX e plug-in**  
  L'impostazione di questo criterio consente di stabilire se possono essere eseguiti controlli ActiveX e plug-in nelle pagine dell'area specificata. Se si abilita l'impostazione di questo criterio, controlli e plug-in possono essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma dalla casella a discesa, viene richiesto agli utenti di scegliere se consentire l'esecuzione di controlli e plug-in. Se si disabilita l'impostazione di questo criterio, l'esecuzione di controlli e plug-in non sarà consentita. Se non si configura l'impostazione di questo criterio, l'esecuzione di controlli e plug-in non è consentita.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Eseguire script di controlli ActiveX contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire l'interazione con uno script da parte di un controllo ActiveX contrassegnato come sicuro. Se si abilita l'impostazione di questo criterio, l'interazione con gli script può avvenire automaticamente senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'interazione con gli script. Se si disabilita l'impostazione di questo criterio, l'interazione con gli script non è consentita. Se non si configura l'impostazione di questo criterio, l'interazione con gli script non è consentita.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Opzioni di accesso**  
  L'impostazione di questo criterio consente di gestire le impostazioni per le opzioni di accesso. Se si abilita l'impostazione di questo criterio, è possibile scegliere tra le opzioni di accesso seguenti. 
  - *Anonimo*: usare l'accesso anonimo per disabilitare l'autenticazione HTTP e usare l'account Guest solo per il protocollo Common Internet File System (CIFS). 
  - *Chiedi conferma*: usare la richiesta di nome utente e password per richiedere l'immissione degli ID utente e delle password da parte degli utenti. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. 
  - *Accesso automatico solo nell'area Intranet* -usare questa opzione per gli utenti di query per gli ID utente e password in un'altra. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. 
  - *Accesso automatico con il nome dell'utente corrente e la password*-usare questa opzione per tentare di accedere con risposta alla richiesta di Windows NT (noto anche come autenticazione NTLM). Se il server supporta Windows NT Challenge risposta, l'accesso Usa nome utente di rete dell'utente e password per accedere. Se il server non supporta Windows NT Challenge Response, viene richiesto all'utente di specificare il nome utente e la password. 

  Se si disabilita l'impostazione di questo criterio, viene impostata l'opzione *Accesso automatico solo nell'area Intranet*. Se non si configura l'impostazione di questo criterio, viene impostata l'opzione di accesso *Chiedi conferma* per nome utente e password.
  
  **Default**: anonima  
  
- **Internet Explorer - Area attendibile - Inizializzare ed eseguire script di controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Verificare la revoca certificati del server**  
  L'impostazione di questo criterio consente di gestire la verifica da parte di Internet Explorer dello stato di revoca dei certificati del server. I certificati vengono revocati quando sono compromessi oppure non sono più validi. Questa opzione protegge gli utenti dall'invio di dati riservati a un sito che potrebbe essere fraudolento o non protetto. Se si abilita l'impostazione di questo criterio, Internet Explorer verificherà se i certificati del server sono stati revocati. Se si disabilita l'impostazione di questo criterio, Internet Explorer non verificherà se i certificati del server sono stati revocati. Se non si configura l'impostazione di questo criterio, Internet Explorer non verificherà se i certificati del server sono stati revocati.
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area Internet - Siti con privilegi inferiori**  
  L'impostazione di questo criterio consente di gestire l'esplorazione dell'area da parte di siti Web appartenenti ad aree con privilegi inferiori, ad esempio l'area Siti con restrizioni. Se si abilita l'impostazione di questo criterio, i siti Web appartenenti ad aree con privilegi inferiori possono aprire nuove finestre all'interno dell'area o esplorarla. L'area sarà priva del livello di sicurezza aggiuntivo offerto dalla funzionalità di sicurezza Protezione da elevazione privilegi dell'area. Se si seleziona Chiedi conferma nella casella a discesa, viene visualizzato un avviso che informa l'utente dei potenziali rischi dell'esplorazione. Se si disabilita l'impostazione di questo criterio, le esplorazioni potenzialmente dannose non saranno consentite. Questa funzionalità di sicurezza di Internet Explorer viene abilitata per l'area, come specificato dall'impostazione del controllo della funzionalità Protezione da elevazione privilegi dell'area. Se non si configura l'impostazione di questo criterio, i siti Web appartenenti ad aree con privilegi inferiori possono aprire nuove finestre all'interno dell'area o esplorarla.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Download di file**  
  L'impostazione di questo criterio consente di determinare se i download dei file dall'area sono consentiti. Questa opzione viene determinata dall'area della pagina contenente il collegamento che provoca il download e non dall'area da cui viene inviato il file. Se si abilita l'impostazione di questo criterio, è possibile scaricare file dall'area. Se si disabilita l'impostazione di questo criterio, non è possibile scaricare file dall'area. Se non si configura l'impostazione di questo criterio, non è possibile scaricare file dall'area.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Eseguire componenti basati su .NET Framework firmati con Authenticode**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte di Internet Explorer di componenti .NET Framework con firma Authenticode. Fra questi componenti sono inclusi i controlli gestiti a cui fa riferimento un tag oggetto e gli eseguibili gestiti a cui fa riferimento un collegamento. Se si abilita l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti con firma. Se si seleziona Chiedi conferma nella casella a discesa, Internet Explorer chiederà all'utente di scegliere se consentire l'esecuzione di componenti gestiti con firma. Se si disabilita l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati. Se non si configura l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Impedire l'installazione per singolo utente dei controlli ActiveX**  
  L'impostazione di questo criterio consente di impedire l'installazione per singolo utente dei controlli ActiveX. Se si abilita l'impostazione di questo criterio, i controlli ActiveX non possono essere installati per singolo utente. Se si disabilita o non si configura l'impostazione di questo criterio, i controlli ActiveX possono essere installati per singolo utente.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Impedire la gestione del filtro SmartScreen**  
  L'impostazione di questo criterio impedisce all'utente di gestire il filtro SmartScreen, che avvisa l'utente se il sito Web visitato è noto per aver eseguito tentativi fraudolenti di raccogliere informazioni personali attraverso il "phishing" o per contenere malware. Se si abilita questa impostazione, all'utente non viene richiesto di attivare il filtro SmartScreen. Tutti gli indirizzi di siti Web non inclusi nell'elenco di quelli consentiti vengono inviati automaticamente a Microsoft senza richiedere conferma all'utente. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente può scegliere se attivare il filtro SmartScreen alla prima esecuzione.
  
  **Default**: abilitare  
  
- **Internet Explorer - Processi - Funzionalità di protezione analisi MIME**  
  L'impostazione di questo criterio determina se l'analisi MIME di Internet Explorer impedisce l'innalzamento di livello di un file di un certo tipo a un tipo di file più pericoloso. Se si abilita l'impostazione di questo criterio, l'analisi MIME non innalzerà mai di livello un file di un certo tipo a un tipo di file più pericoloso. Se si disabilita l'impostazione di questo criterio, i processi di Internet Explorer consentiranno all'analisi MIME di innalzare di livello un file di un certo tipo a un tipo di file più pericoloso. Se non si configura l'impostazione di questo criterio, l'analisi MIME non innalzerà mai di livello un file di un certo tipo a un tipo di file più pericoloso.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Download di controlli Active X firmati**  
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX firmati da una pagina appartenente all'area. Se si abilita l'impostazione di questo criterio, i controlli firmati possono essere scaricati senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente. Se si disabilita l'impostazione di questo criterio, i controlli firmati non possono essere scaricati. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Completamento automatico**  
  La funzionalità Completamento automatico è in grado di ricordare e suggerire nomi utente e password nei moduli. Se si abilita questa impostazione, l'utente non può modificare le opzioni "Nome utente e password sui moduli" e "Richiedi salvataggio password". La funzionalità Completamento automatico per l'immissione di nomi utente e password nei moduli viene attivata. L'amministratore deve scegliere se selezionare l'opzione "Richiedi salvataggio password". Se si disabilita questa impostazione, l'utente non può modificare le opzioni "Nome utente e password sui moduli" e "Richiedi salvataggio password". La funzionalità Completamento automatico per l'immissione di nomi utente e password nei moduli viene disabilitata. L'utente inoltre non può scegliere di richiedere il salvataggio delle password. Se non si configura questa impostazione, l'utente può scegliere di attivare Completamento automatico per nomi utente e password nei moduli e l'opzione per richiedere il salvataggio delle password. Per accedere a questa opzione è necessario visualizzare la finestra di dialogo Opzioni Internet, fare clic sulla scheda Contenuto e quindi sul pulsante Impostazioni.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Autorizzare l'esecuzione di VBscript**  
  L'impostazione di questo criterio consente di decidere se VBScript può essere eseguito nelle pagine in zone specifiche di Internet Explorer. Le opzioni includono: 
  - *Abilita*: VBScript viene eseguito nelle pagine in zone specifiche, senza nessuna interazione. 
  - *Chiedi conferma*: viene richiesto ai dipendenti se consentono l'esecuzione di VBScript nella zona. 
  - *Disabilita*: viene impedita l'esecuzione di VBScript nella zona. Se si disabilita o non si configura l'impostazione di questo criterio, VBScript viene eseguito senza alcuna interazione nella zona specificata. 
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Consentire solo ai domini approvati di usare i controlli ActiveX TDC**  
  Questa impostazione criterio controlla se l'utente può eseguire il controllo ActiveX TDC nei siti Web. Se si abilita l'impostazione di questo criterio, il controllo ActiveX TDC non verrà eseguito dai siti Web in quest'area. Se si disabilita l'impostazione di questo criterio, il controllo ActiveX TDC verrà eseguito da tutti i siti Web in quest'area.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Non eseguire antimalware sui controlli ActiveX per l'area attendibile**  
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area computer locale - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione media.
  
  **Default**: disabilitare java 
  
- **Internet Explorer intranet zona non vengono eseguite antimalware con i controlli ActiveX** questa impostazione criterio determina se Internet Explorer viene eseguito programmi antimalware da controlli ActiveX, per verificare se siano sicure caricare in pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.
  
  **Impostazione predefinita**: Disabilitato  

- **Internet Explorer - Area con restrizioni - Scriptlet**  
  L'impostazione di questo criterio consente di specificare se l'utente può eseguire scriptlet. Se si abilita l'impostazione di questo criterio, l'utente potrà eseguire gli scriptlet. Se si disabilita l'impostazione di questo criterio, l'utente non potrà eseguire gli scriptlet. Se non si configura l'impostazione di questo criterio, l'utente potrà abilitare o disabilitare gli scriptlet.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Processi - Barra di notifica**  
  L'impostazione di questo criterio consente di gestire la visualizzazione della barra di notifica per i processi di Internet Explorer quando le installazioni di file o di codice sono soggette a restrizioni. Per impostazione predefinita, la barra di notifica è visualizzata per i processi di Internet Explorer. Se si abilita l'impostazione di questo criterio, la barra di notifica viene visualizzata per i processi di Internet Explorer. Se si disabilita l'impostazione di questo criterio, la barra di notifica non verrà visualizzata per i processi di Internet Explorer. Se non si configura l'impostazione di questo criterio, la barra di notifica non viene visualizzata per i processi di Internet Explorer.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area Internet - Scaricare controlli ActiveX firmati**  
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX firmati da una pagina appartenente all'area. Se si abilita l'impostazione di questo criterio, i controlli firmati possono essere scaricati senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente. Se si disabilita l'impostazione di questo criterio, i controlli firmati non possono essere scaricati. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire il download di controlli firmati da autori non considerati attendibili. Il codice firmato da autori considerati attendibili viene scaricato in modo invisibile all'utente.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Rimuovere il pulsante Esegui questa volta per i controlli ActiveX obsoleti**  
  L'impostazione di questo criterio consente di evitare la visualizzazione del pulsante "Esegui questa volta" e l'esecuzione di specifici controlli ActiveX obsoleti in Internet Explorer. Se si abilita l'impostazione di questo criterio, gli utenti non vedranno il pulsante "Esegui questa volta" nel messaggio di avviso visualizzato quando Internet Explorer blocca un controllo ActiveX obsoleto. Se si disabilita o non si configura l'impostazione di questo criterio, gli utenti vedranno il pulsante "Esegui questa volta" nel messaggio di avviso visualizzato quando Internet Explorer blocca un controllo ActiveX obsoleto. Facendo clic su questo pulsante l'utente può eseguire il controllo ActiveX obsoleto una volta. Per altre informazioni, vedere l'argomento relativo ai controlli ActiveX obsoleti nella libreria TechNet di Internet Explorer.
  
  **Impostazione predefinita**: Abilitato 
  
- **Internet Explorer - Area Internet - Avviare programmi e file in un IFRAME**  
  L'impostazione di questo criterio consente di gestire l'esecuzione di applicazioni e il download di file da un riferimento IFRAME nel codice HTML delle pagine appartenenti all'area. Se si abilita l'impostazione di questo criterio, è possibile eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area senza intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di applicazioni e il download di file da IFRAME nelle pagine dell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non possono eseguire applicazioni e scaricare file da IFRAME nelle pagine dell'area. Se non si configura l'impostazione di questo criterio, agli utenti viene chiesto di scegliere se consentire l'esecuzione di applicazioni e il download di file da IFRAME presenti nelle pagine dell'area
  
  **Default**: disabilitare 
  
- **Internet Explorer - Area con restrizioni - Esplorare finestre e frame in domini diversi**  
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - SmartScreen**  
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area attendibile bloccata - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.
  
  **Default**: disabilitare java 
  
- **Internet Explorer - Verificare le firme nei programmi scaricati**  
  L'impostazione di questo criterio consente di gestire la verifica da parte di Internet Explorer delle firme digitali, che ha lo scopo di identificare l'autore di software firmato e di controllare che tale software non sia stato modificato o manomesso, nei computer degli utenti prima del download di programmi eseguibili. Se si abilita l'impostazione di questo criterio, Internet Explorer verificherà le firme digitali dei programmi eseguibili e visualizzerà le relative identità prima del download nei computer degli utenti. Se si disabilita l'impostazione di questo criterio, Internet Explorer non verificherà le firme digitali dei programmi eseguibili né visualizzerà le relative identità prima del download nei computer degli utenti. Se non si configura l'impostazione di questo criterio, Internet Explorer non verificherà le firme digitali dei programmi eseguibili né visualizzerà le relative identità prima del download nei computer degli utenti.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Eseguire script di controlli WebBrowser**  
  L'impostazione di questo criterio determina se una pagina può gestire i controlli WebBrowser incorporati tramite uno script. Se si abilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser è consentito. Se si disabilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser non è consentito. Se non si configura l'impostazione di questo criterio, l'utente può abilitare o disabilitare l'accesso tramite script ai controlli WebBrowser. Per impostazione predefinita, l'accesso tramite script ai controlli WebBrowser è consentito solo nelle aree Intranet e del computer locale.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Filtro XSS**  
  Questo criterio consente di specificare se il filtro XSS rileverà e impedirà gli attacchi tramite script da altri siti nei siti Web in quest'area. Se si abilita l'impostazione di questo criterio, il filtro XSS è attivato per i siti in quest'area e prova a bloccare gli attacchi tramite script da altri siti. Se si disabilita l'impostazione di questo criterio, il filtro XSS è disabilitato per i siti in quest'area e Internet Explorer non impedirà gli attacchi tramite script da altri siti.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Comportamenti file binari e script**  
  L'impostazione di questo criterio consente di gestire comportamenti binari dinamici e di script, ovvero componenti che incapsulano funzionalità specifiche per gli elementi HTML a cui sono stati associati. Se si abilita l'impostazione di questo criterio, i comportamenti binari e di script sono disponibili. Se si seleziona Autorizzazione amministratore nella casella a discesa sono disponibili solo i comportamenti specificati nell'elenco Comportamenti autorizzati da amministratori del criterio Restrizione di sicurezza comportamenti binari. Se si disabilita l'impostazione di questo criterio, i comportamenti binari e di script non sono disponibili, a meno che nelle applicazioni non sia stato implementato un gestore della sicurezza personalizzato. Se non si configura l'impostazione di questo criterio, i comportamenti binari e di script non sono disponibili, a meno che nelle applicazioni non sia stato implementato un gestore della sicurezza personalizzato.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Verifica delle impostazioni di sicurezza**  
  L'impostazione di questo criterio consente di disattivare la funzionalità di verifica delle impostazioni di sicurezza che controlla le impostazioni di sicurezza di Internet Explorer per determinare quando comportano rischi per Internet Explorer. Se si abilita l'impostazione di questo criterio, la funzionalità viene disattivata. Se si disabilita o non si configura l'impostazione di questo criterio, la funzionalità viene attivata.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area Internet - Avviso di sicurezza per file potenzialmente dannosi**  
  L'impostazione di questo criterio consente di controllare la visualizzazione dell'avviso "Apri file - Avviso di sicurezza" quando l'utente prova ad aprire file eseguibili o altri file potenzialmente non sicuri, ad esempio da una condivisione file Intranet usando Esplora file. Se si abilita l'impostazione di questo criterio e nella casella a discesa è selezionata Abilita, i file verranno aperti senza visualizzare l'avviso di sicurezza. Se nella casella a discesa è selezionata Chiedi conferma, prima dell'apertura dei file viene visualizzato un avviso di sicurezza. Se si disabilita l'impostazione di questo criterio, i file non verranno aperti. Se non si configura l'impostazione di questo criterio, l'utente può configurare la modalità di gestione di questi file. Per impostazione predefinita, questi file vengono bloccati nell'area con restrizioni, abilitati nell'area Intranet e del computer locale e impostati su Chiedi conferma nelle aree attendibili e Internet.
  
  **Default**: messaggio di richiesta  
  
- **Internet Explorer - Area Intranet - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione media.
  
  **Default**: protezione elevata 
  
- **Internet Explorer - Bloccare i controlli ActiveX obsoleti**  </br>
  L'impostazione di questo criterio determina se Internet Explorer blocca specifici controlli ActiveX obsoleti. I controlli ActiveX obsoleti non vengono mai bloccati nell'area Intranet. Se si abilita l'impostazione di questo criterio, Internet Explorer sospende il blocco dei controlli ActiveX obsoleti. Se si disabilita o non si configura l'impostazione di questo criterio, Internet Explorer continua a bloccare specifici controlli ActiveX obsoleti. Per altre informazioni, vedere l'argomento relativo ai controlli ActiveX obsoleti nella libreria TechNet di Internet Explorer.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Blocco popup**  
  L'impostazione di questo criterio consente di gestire la visualizzazione di finestre popup indesiderate. Le finestre popup visualizzate quando l'utente finale fa clic su un collegamento non vengono bloccate. Se si abilita l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup indesiderate. Se si disabilita l'impostazione di questo criterio, non viene impedita la visualizzazione delle finestre popup. Se non si configura l'impostazione di questo criterio, viene impedita la visualizzazione della maggior parte delle finestre popup.
  
  **Default**: abilitare  
  
- **Internet Explorer - Processi - Limitare il protocollo di sicurezza MK**  
  L'impostazione del criterio Limitazione protocollo di sicurezza MK riduce la superficie di attacco in quanto disabilita il protocollo MK. Le risorse ospitate nel protocollo MK non funzioneranno. Se si abilita l'impostazione di questo criterio, il protocollo MK viene disabilitato per Esplora file e Internet Explorer e le risorse ospitate nel protocollo MK non funzioneranno. Se si disabilita l'impostazione di questo criterio, le applicazioni possono usare l'API del protocollo MK. Le risorse ospitate nel protocollo MK funzioneranno per i processi di Esplora file e Internet Explorer. Se non si configura l'impostazione di questo criterio, il protocollo MK viene disabilitato per Esplora file e Internet Explorer e le risorse ospitate nel protocollo MK non funzioneranno.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area attendibile - Autorizzazioni Java**  </br>
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione bassa.
  
  **Default**: protezione elevata  
  
- **Internet Explorer - Area con restrizioni - Eseguire script delle applet Java**  
  L'impostazione di questo criterio consente di gestire l'accessibilità delle applet da parte degli script all'interno dell'area. Se si abilita l'impostazione di questo criterio, l'accesso degli script alle applet può avvenire automaticamente senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'accesso degli script alle applet. Se si disabilita l'impostazione di questo criterio, l'accesso degli script alle applet non viene consentito. Se non si configura l'impostazione di questo criterio, l'accesso degli script alle applet non viene consentito.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Bloccare le autorizzazioni Java**  </br>
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.
  
  **Default**: disabilitare java 
  
- **Internet Explorer - Area Internet - Consentire solo ai domini approvati di usare i controlli ActiveX**  </br>
  L'impostazione di questo criterio consente di specificare se agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX su siti Web diversi da quello che ha installato il controllo ActiveX. Se si abilita l'impostazione di questo criterio, agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX da siti Web in quest'area. L'utente può scegliere di autorizzare l'esecuzione del controllo dal sito corrente o da tutti i siti. Se si disabilita l'impostazione di questo criterio, l'utente non vede il prompt di ActiveX per ogni sito e i controlli ActiveX possono essere eseguiti da tutti i siti in quest'area.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Includere tutti i percorsi di rete**  
  Internet Explorer - Includere tutti i percorsi di rete
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Internet - Modalità protetta**  
  L'impostazione di questo criterio consente di attivare la modalità protetta. La modalità protetta consente di proteggere Internet Explorer da attacchi correlati ai rischi di sicurezza attraverso una riduzione delle posizioni in cui Internet Explorer può scrivere all'interno del Registro di sistema e del file system. Se si abilita l'impostazione di questo criterio, la modalità protetta viene attivata. L'utente non può disattivare la modalità protetta. Se si disabilita l'impostazione di questo criterio, la modalità protetta viene disattivata. L'utente non può attivare la modalità protetta. Se non si configura l'impostazione di questo criterio, l'utente può attivare o disattivare la modalità protetta.
  
  **Default**: abilitare 
  
- **Internet Explorer - Area Internet - Inizializzare ed eseguire script controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script.
  
  **Default**: disabilitare 
  
- **Internet Explorer - Area con restrizioni - Blocco SmartScreen**  </br>
  L'impostazione di questo criterio consente di specificare se il filtro SmartScreen analizza le pagine in quest'area per rilevare eventuali contenuti pericolosi. Se si abilita l'impostazione di questo criterio, il filtro SmartScreen analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se si disabilita l'impostazione di questo criterio, il filtro SmartScreen non analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi. Se non si configura l'impostazione di questo criterio, l'utente può scegliere se il filtro SmartScreen analizza le pagine di quest'area e rileva eventuali contenuti pericolosi. Nota: in Internet Explorer 7 l'impostazione di questo criterio consente di specificare se il filtro anti-phishing analizza le pagine di quest'area per rilevare eventuali contenuti pericolosi.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Rilevamento degli arresti anomali**  
  L'impostazione di questo criterio consente di gestire la funzionalità di rilevamento degli arresti anomali di Gestione componenti aggiuntivi. Se si abilita l'impostazione di questo criterio, gli arresti anomali che si verificano in Internet Explorer determineranno le operazioni previste in Windows XP Professional Service Pack 1 e versioni precedenti, ovvero la chiamata di Segnalazione errori Windows. Tutte le impostazioni del criterio Segnalazione errori Windows continuano a essere applicate. Se si disabilita o non si configura l'impostazione di questo criterio, la funzionalità di rilevamento degli arresti anomali per la gestione dei componenti aggiuntivi viene abilitata.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, l'autorizzazione viene impostata su Protezione alta.
  
  **Default**: disabilitare java  
  
- **Internet Explorer - Area con restrizioni - Esecuzione di script attiva**  
  L'impostazione di questo criterio consente di gestire l'esecuzione di codice script nelle pagine appartenenti all'area. Se si abilita l'impostazione di questo criterio, il codice script nelle pagine dell'area può essere eseguito automaticamente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di codice script nelle pagine dell'area. Se si disabilita l'impostazione di questo criterio, viene impedita l'esecuzione di codice script nelle pagine dell'area. Se non si configura l'impostazione di questo criterio, viene impedita l'esecuzione di codice script nelle pagine dell'area.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Opzioni di accesso**  
  L'impostazione di questo criterio consente di gestire le impostazioni per le opzioni di accesso. Se si abilita l'impostazione di questo criterio, è possibile scegliere tra le opzioni di accesso seguenti. Accesso anonimo consente di disabilitare l'autenticazione HTTP e di usare l'account Guest solo per il protocollo Common Internet File System (CIFS). Richiedi nome utente e password consente di richiedere l'immissione degli ID utente e delle password da parte degli utenti. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. Accesso automatico solo nell'area Intranet consente di richiedere l'immissione degli ID utente e delle password da parte degli utenti in altre aree. Dopo l'immissione, questi valori possono essere usati in modo invisibile all'utente per il resto della sessione. Accesso automatico con nome utente e password correnti consente di provare a eseguire l'accesso tramite Windows NT Challenge Response, noto anche come autenticazione NTLM. Se il server supporta Windows NT Challenge risposta, l'accesso di Usa nome utente di rete dell'utente e password per accedere. Se il server non supporta Windows NT Challenge Response, viene richiesto all'utente di specificare il nome utente e la password. Se si disabilita l'impostazione di questo criterio, viene impostata l'opzione Accesso automatico solo nell'area Intranet. Se non si configura questa impostazione dei criteri, accedi sono impostato su accesso automatico solo nell'area Intranet.
  
  **Default**: messaggio di richiesta  
  
- **Internet Explorer - Area con restrizioni - Autorizzare l'esecuzione di VBscript**  </br>  
  L'impostazione di questo criterio consente di stabilire se possono essere eseguiti VBScript nelle pagine dell'area specificata in Internet Explorer. Se è stato selezionato Abilita nella casella a discesa, VBScript viene eseguito senza richiedere l'intervento dell'utente. Se è stato selezionato Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione di VBScript. Se è stato selezionato Disabilita nella casella a discesa, viene impedita l'esecuzione di VBScript. Se si disabilita o non si configura l'impostazione di questo criterio, viene impedita l'esecuzione di VBScript.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Trascinare contenuto da domini diversi tra finestre**  
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.
  
  **Impostazione predefinita**: Disabilitato 
  
- **Internet Explorer - Area Intranet - Inizializzare ed eseguire script di controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script.
  
  **Default**: disabilitare 
  
- **Internet Explorer - Scaricare allegati**  
  L'impostazione di questo criterio impedisce all'utente di scaricare file allegati da un feed nel computer dell'utente. Se si abilita l'impostazione di questo criterio, l'utente non potrà impostare il modulo di sincronizzazione dei feed per scaricare un allegato tramite la pagina delle proprietà Feed. Gli sviluppatori non possono modificare l'impostazione del download usando le interfacce API per i feed. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà impostare il modulo di sincronizzazione dei feed per scaricare un allegato tramite la pagina delle proprietà Feed. Gli sviluppatori possono modificare l'impostazione del download usando le interfacce API per i feed.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Download di controlli Active X senza firma**  </br>
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX senza firma dall'area. Il codice di questo tipo può essere dannoso, soprattutto se proviene da un'area non attendibile. Se si abilita l'impostazione di questo criterio, i controlli non firmati potranno essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione del controllo non firmato. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati. Se non si configura l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Trascinare contenuto da domini diversi all'interno di finestre**  
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX non firmati dall'area. Il codice di questo tipo può essere dannoso, soprattutto se proviene da un'area non attendibile. Se si abilita l'impostazione di questo criterio, i controlli non firmati potranno essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione del controllo non firmato. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati. Se non si configura l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Processi - Limitare l'installazione di Active X**  </br>
  L'impostazione di questo criterio consente alle applicazioni che ospitano il Controllo Web Browser di bloccare la richiesta di conferma automatica dell'installazione di controlli ActiveX. Se si abilita l'impostazione di questo criterio, il Controllo Web Browser bloccherà la richiesta di conferma automatica dell'installazione di controlli ActiveX per tutti i processi. Se si disabilita o non si configura l'impostazione di questo criterio, il controllo WebBrowser non bloccherà la richiesta di conferma automatica dell'installazione di controlli ActiveX per tutti i processi.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area Internet - Scriptlet** L'impostazione di questo criterio consente di specificare se l'utente può eseguire gli scriptlet. Se si abilita l'impostazione di questo criterio, l'utente potrà eseguire gli scriptlet. Se si disabilita l'impostazione di questo criterio, l'utente non potrà eseguire gli scriptlet. Se non si configura l'impostazione di questo criterio, l'utente potrà abilitare o disabilitare gli scriptlet.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Trascinare o copiare e incollare file**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte degli utenti di operazioni di trascinamento o di copia e incolla di file da un'origine appartenente all'area. Se si abilita l'impostazione di questo criterio, gli utenti potranno automaticamente trascinare o copiare e incollare file dall'area. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire il trascinamento o la copia di file dall'area. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno trascinare o copiare e incollare file dall'area. Se non si configura l'impostazione di questo criterio, agli utenti verrà chiesto di scegliere se consentire il trascinamento o la copia di file dall'area.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Software - Firma non valida** </br>
  L'impostazione di questo criterio consente di gestire l'installazione o l'esecuzione di software, ad esempio controlli ActiveX e download di file, anche nel caso in cui la firma non sia valida. Una firma non valida potrebbe indicare un tentativo di manomissione del file. Se si abilita l'impostazione di questo criterio, prima dell'installazione o dell'esecuzione di file con una firma non valida viene visualizzata una richiesta di conferma. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire né installare file con una firma non valida. Se non si configura l'impostazione di questo criterio, gli utenti potranno scegliere di eseguire o installare file con una firma non valida.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Copiare e incollare tramite script** </br> L'impostazione di questo criterio consente di gestire l'esecuzione da parte degli script di operazioni con gli Appunti, ad esempio operazioni di taglia, copia e incolla, in un'area specificata. Se si abilita l'impostazione di questo criterio, gli script potranno eseguire operazioni con gli Appunti. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire l'esecuzione di operazioni con gli Appunti. Se si disabilita l'impostazione di questo criterio, gli script non potranno eseguire operazioni con gli Appunti. Se non si configura l'impostazione di questo criterio, gli script non potranno eseguire operazioni con gli Appunti.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Trascinare contenuto da domini diversi tra finestre**  
  Questa impostazione consente di specificare le opzioni per il trascinamento di contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Se si abilita questa impostazione e si fa clic su Attiva, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. Se si abilita questa impostazione e si fa clic su Disattiva, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione. In Internet Explorer 10, se questa impostazione viene disabilitata o non configurata, gli utenti non potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti possono modificare questa impostazione nella finestra di dialogo Opzioni Internet. In Internet Explorer 9 e versioni precedenti, se questa impostazione viene disabilitata o non configurata, gli utenti potranno trascinare contenuto da un dominio a un dominio diverso, quando l'origine e la destinazione sono in finestre diverse. Gli utenti non possono modificare questa impostazione.  <br><br>
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Aggiunta di siti da parte degli utenti**  
  Impedisce agli utenti di aggiungere o eliminare siti nelle aree di sicurezza. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, le impostazioni di gestione dei siti per le aree di sicurezza verranno disabilitate. (Per visualizzare le impostazioni di gestione dei siti per le aree di sicurezza, nella finestra di dialogo Opzioni Internet fare clic sulla scheda Sicurezza e quindi sul pulsante Siti). Se si disabilita o non si configura questo criterio, gli utenti potranno aggiungere o eliminare siti Web nelle aree Siti attendibili e Siti con restrizioni nonché modificare le impostazioni relative all'area Intranet locale. Questo criterio impedisce agli utenti di modificare le impostazioni di gestione dei siti per le aree di sicurezza configurate dall'amministratore. Nota: il criterio "Disabilita la scheda Sicurezza", disponibile in Configurazione utente\Modelli amministrativi\Componenti di Windows\Internet Explorer\Pannello di controllo Internet, che rimuove la scheda Sicurezza dall'interfaccia, ha priorità rispetto al criterio appena descritto. Se il criterio "Disabilita la scheda Programmi" è abilitato, questo criterio verrà ignorato. Vedere anche il "aree di sicurezza: usare solo le impostazioni del computer" dei criteri.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Finestre aperte da script**  
  L'impostazione di questo criterio consente di gestire le restrizioni nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato. Se si abilita l'impostazione di questo criterio, la funzionalità di sicurezza relativa alle restrizioni per Windows non verrà applicata nell'area. L'area di sicurezza verrà eseguita senza il livello di sicurezza aggiuntivo offerto da questa funzionalità. Se si disabilita l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo. Se non si configura l'impostazione di questo criterio, le azioni potenzialmente dannose contenute nelle finestre popup e nelle finestre aperte da script contenenti barra del titolo e barra di stato non potranno essere eseguite. Questa funzionalità di sicurezza di Internet Explorer viene attivata nell'area, come specificato dall'impostazione del controllo della funzionalità delle restrizioni di sicurezza delle finestre aperte da script per il processo.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Aree di sicurezza - Usare solo le impostazioni del computer**  
  Applica le informazioni relative alle aree di sicurezza per tutti gli utenti di uno stesso computer. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, le modifiche apportate da un utente a un'area di sicurezza verranno applicate a tutti gli utenti del computer. Se si disabilita o non si configura questo criterio, gli utenti di uno stesso computer potranno configurare impostazioni personalizzate per le aree di sicurezza. Usare questo criterio per applicare impostazioni uniformi per le aree di sicurezza in uno stesso computer e per impedire che le impostazioni cambino da un utente all'altro. Vedere anche il "aree di sicurezza: non consentire agli utenti di modificare i criteri" dei criteri.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area computer locale bloccata - Autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate
  
  **Default**: disabilitare java 
  
- **Internet Explorer - Area con restrizioni - Non eseguire programmi antimalware su controlli ActiveX**  </br>
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Eseguire componenti basati su .NET Framework firmati con Authenticode**  
  L'impostazione di questo criterio consente di gestire l'esecuzione da parte di Internet Explorer dei componenti .NET Framework firmati con Authenticode. Fra questi componenti sono inclusi i controlli gestiti a cui fa riferimento un tag oggetto e gli eseguibili gestiti a cui fa riferimento un collegamento. Se si abilita l'impostazione di questo criterio, Internet Explorer eseguirà i componenti gestiti con firma. Se si seleziona Chiedi conferma nella casella a discesa, Internet Explorer chiederà all'utente di scegliere se consentire l'esecuzione di componenti gestiti con firma. Se si disabilita l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati. Se non si configura l'impostazione di questo criterio, Internet Explorer non eseguirà i componenti gestiti firmati.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area con restrizioni - Accedere alle origini dati**  
  L'impostazione di questo criterio consente di gestire l'accesso da parte di Internet Explorer a dati appartenenti a un'altra area di sicurezza usando Microsoft XML Parser (MSXML) o ActiveX Data Objects (ADO). Se si abilita l'impostazione di questo criterio, gli utenti potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire il caricamento di una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area. Se non si configura l'impostazione di questo criterio, gli utenti non potranno caricare una pagina nell'area che usa MSXML o ADO per accedere ai dati di un altro sito nell'area.
  
  **Default**: disabilitare 
  
- **Internet Explorer - Non eseguire antimalware sui controlli ActiveX per l'area Internet**  </br>
  L'impostazione di questo criterio determina se Internet Explorer esegue programmi antimalware sui controlli ActiveX per stabilire se sono sicuri per il caricamento nelle pagine. Se si abilita l'impostazione di questo criterio, Internet Explorer non esegue un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se si disabilita l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Se non si configura l'impostazione di questo criterio, Internet Explorer esegue sempre un controllo con il programma antimalware per stabilire se è sicuro creare un'istanza del controllo ActiveX. Gli utenti possono attivare o disattivare questo comportamento tramite le impostazioni di sicurezza di Internet Explorer.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Copiare e incollare tramite script** </br> L'impostazione di questo criterio consente di gestire l'esecuzione da parte degli script di operazioni con gli Appunti, ad esempio operazioni di taglia, copia e incolla, in un'area specificata. Se si abilita l'impostazione di questo criterio, gli script potranno eseguire operazioni con gli Appunti. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire l'esecuzione di operazioni con gli Appunti. Se si disabilita l'impostazione di questo criterio, gli script non potranno eseguire operazioni con gli Appunti. Se non si configura l'impostazione di questo criterio, gli script potranno eseguire operazioni con gli Appunti.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Usare il servizio di installazione di Active X**  </br>
  L'impostazione di questo criterio consente di specificare la modalità di installazione dei controlli ActiveX. Se si abilita l'impostazione di questo criterio, i controlli ActiveX verranno installati solo se il servizio ActiveX Installer è presente ed è stato configurato per consentire l'installazione di controlli ActiveX. Se si disabilita o non si configura l'impostazione di questo criterio, i controlli ActiveX, inclusi i controlli per singolo utente, verranno installati usando la procedura di installazione standard.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Protezione dei processi da elevazione privilegi dell'area**  
  Internet Explorer applica restrizioni a ogni pagina Web aperta. Le restrizioni dipendono dalla posizione della pagina Web (area Internet, Intranet, Computer locale e così via). Le pagine Web nel computer locale, ad esempio, sono soggette al minor numero di restrizioni di sicurezza e appartengono all'area Computer locale. Di conseguenza, l'area di sicurezza Computer locale è uno dei bersagli preferiti degli utenti malintenzionati. Se si abilita l'impostazione di questo criterio, sarà possibile proteggere qualsiasi area contro l'elevazione dei privilegi per tutti i processi. Se si disabilita o non si configura l'impostazione di questo criterio, i processi non di Internet Explorer o non specificati nell'Elenco processi non usufruiranno di tale protezione.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area Internet - Scaricare controlli ActiveX non firmati**  </br>
  L'impostazione di questo criterio consente di gestire il download da parte degli utenti di controlli ActiveX senza firma elettronica dall'area. Il codice di questo tipo può essere dannoso, soprattutto se proviene da un'area non attendibile. Se si abilita l'impostazione di questo criterio, i controlli non firmati potranno essere eseguiti senza l'intervento dell'utente. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire l'esecuzione del controllo non firmato. Se si disabilita l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati. Se non si configura l'impostazione di questo criterio, gli utenti non potranno eseguire controlli non firmati.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Esplorare finestre e frame in domini diversi**  </br>
  L'impostazione di questo criterio consente di gestire l'apertura di finestre e frame ed accedere alle applicazioni in domini diversi. Se si abilita l'impostazione di questo criterio, gli utenti potranno aprire finestre e frame e accedere ad applicazioni da altri domini. Se si seleziona Chiedi conferma nella casella a discesa, agli utenti verrà chiesto di scegliere se consentire l'apertura di finestre e frame o l'accesso ad applicazioni in altri domini. Se si disabilita questa impostazione, gli utenti non potranno aprire finestre o frame né accedere ad applicazioni in altri domini. Se non si configura questa impostazione, gli utenti potranno aprire finestre e frame e accedere ad applicazioni in altri domini.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Area Internet - Aggiornamenti alla barra di stato tramite script**  
  L'impostazione di questo criterio consente di gestire gli aggiornamenti della barra di stato tramite uno script all'interno dell'area. Se si abilita questa impostazione dei criteri, gli script possono aggiornare la barra di stato. Se si disabilita o non si configura l'impostazione di questo criterio, lo script non potrà aggiornare la barra di stato.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Includere percorso locale nel caricamento di file sul server**  </br> L'impostazione di questo criterio consente di specificare se inviare le informazioni sul percorso locale quando l'utente carica un file tramite un modulo HTML. Se le informazioni sul percorso locale vengono inviate, alcune di esse potrebbero essere rese note al server accidentalmente. I file inviati dal desktop di un utente, ad esempio, potrebbero contenere il nome utente come parte del percorso. Se si abilita l'impostazione di questo criterio, le informazioni sul percorso locale verranno inviate quando l'utente carica un file tramite un modulo HTML. Se si disabilita l'impostazione di questo criterio, le informazioni sul percorso verranno rimosse quando l'utente carica un file tramite un modulo HTML. Se non si configura l'impostazione di questo criterio, l'utente potrà scegliere se inviare le informazioni sul percorso quando carica un file tramite un modulo HTML. Per impostazione predefinita, le informazioni sul percorso vengono inviate.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Processi - Limitare il download dei file**  </br> L'impostazione di questo criterio consente alle applicazioni che ospitano il controllo WebBrowser di bloccare la richiesta di conferma automatica dei download di file non originati dall'utente. Se si abilita l'impostazione di questo criterio, il controllo WebBrowser bloccherà la richiesta di conferma automatica dei download di file non originati dall'utente per tutti i processi. Se si disabilita l'impostazione di questo criterio, il controllo WebBrowser bloccherà la richiesta di conferma automatica dei download di file non originati dall'utente per tutti i processi.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Consentire solo ai domini approvati di usare i controlli ActiveX**  </br>
  L'impostazione di questo criterio consente di specificare se agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX su siti Web diversi da quello che ha installato il controllo ActiveX. Se si abilita l'impostazione di questo criterio, agli utenti viene chiesto di autorizzare l'esecuzione dei controlli ActiveX da siti Web in quest'area. L'utente può scegliere di autorizzare l'esecuzione del controllo dal sito corrente o da tutti i siti. Se si disabilita l'impostazione di questo criterio, l'utente non vede il prompt di ActiveX per ogni sito e i controlli ActiveX possono essere eseguiti da tutti i siti in quest'area.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Area con restrizioni - Inizializzare ed eseguire script di controlli ActiveX non contrassegnati come sicuri**  
  L'impostazione di questo criterio consente di gestire i controlli ActiveX non contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio, i controlli ActiveX vengono eseguiti, caricati con parametri ed eseguiti tramite script senza impostare la protezione degli oggetti per dati o script non considerati attendibili. Questa impostazione è sconsigliata, a meno che non si tratti di aree protette e amministrate. Questa impostazione causa l'inizializzazione e l'esecuzione tramite script di controlli sia sicuri che non sicuri, indipendentemente dall'opzione Esegui script controlli ActiveX contrassegnati come sicuri. Se si abilita l'impostazione di questo criterio e si seleziona Chiedi conferma nella casella a discesa, agli utenti viene chiesto di scegliere se consentire il caricamento con parametri o l'esecuzione tramite script del controllo. Se si disabilita l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script. Se non si configura l'impostazione di questo criterio, i controlli ActiveX che non è possibile rendere sicuri non vengono caricati con parametri o eseguiti tramite script.
  
  **Default**: disabilitare  
  
- **Internet Explorer - Modifica dei criteri da parte degli utenti**  
    Impedisce agli utenti di modificare le impostazioni dell'area di sicurezza. Un'area di sicurezza è un gruppo di siti Web con lo stesso livello di sicurezza. Se si abilita questo criterio, il pulsante Livello personalizzato e il cursore del livello di sicurezza nella scheda Sicurezza della finestra di dialogo Opzioni Internet sono disabilitati. Se si disabilita questo criterio o non lo si configura, gli utenti possono modificare le impostazioni delle aree di sicurezza. Questo criterio impedisce agli utenti di modificare le impostazioni dell'area di sicurezza stabilite dall'amministratore. Nota: il criterio "Disabilita la scheda Sicurezza", disponibile in Configurazione utente\Modelli amministrativi\Componenti di Windows\Internet Explorer\Pannello di controllo Internet, che rimuove la scheda Sicurezza da Internet Explorer nel Pannello di controllo, ha priorità rispetto al criterio appena descritto. Se il criterio "Disabilita la scheda Programmi" è abilitato, questo criterio verrà ignorato. Vedere anche il "aree di sicurezza: usare solo le impostazioni del computer" dei criteri.
    
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Modalità protetta**  
  L'impostazione di questo criterio consente di attivare la modalità protetta. La modalità protetta consente di proteggere Internet Explorer da attacchi correlati ai rischi di sicurezza attraverso una riduzione delle posizioni in cui Internet Explorer può scrivere all'interno del Registro di sistema e del file system. Se si abilita l'impostazione di questo criterio, la modalità protetta viene attivata. L'utente non può disattivare la modalità protetta. Se si disabilita l'impostazione di questo criterio, la modalità protetta viene disattivata. L'utente non può attivare la modalità protetta. Se non si configura l'impostazione di questo criterio, l'utente può attivare o disattivare la modalità protetta.
  
  **Default**: abilitare  
  
- **Internet Explorer - Area Internet - Persistenza dei dati utente**  
  L'impostazione di questo criterio consente di gestire il mantenimento di informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Quando un utente apre una pagina salvata localmente, se l'impostazione di questo criterio è stata configurata in modo appropriato sarà possibile ripristinare lo stato della pagina. Se si abilita questa impostazione, gli utenti potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se si disabilita questa impostazione, gli utenti non potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se non si configura l'impostazione di questo criterio, gli utenti potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Internet - Eseguire script di controlli WebBrowser**  
 
  L'impostazione di questo criterio determina se una pagina può gestire i controlli WebBrowser incorporati tramite uno script. Se si abilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser è consentito. Se si disabilita l'impostazione di questo criterio, l'accesso tramite script ai controlli WebBrowser non è consentito. Se non si configura l'impostazione di questo criterio, l'utente può abilitare o disabilitare l'accesso tramite script ai controlli WebBrowser. Per impostazione predefinita, l'accesso tramite script ai controlli WebBrowser è consentito solo nelle aree Intranet e del computer locale.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - Persistenza dei dati utente**  
    L'impostazione di questo criterio consente di gestire il mantenimento di informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Quando un utente apre una pagina salvata localmente, se l'impostazione di questo criterio è stata configurata in modo appropriato sarà possibile ripristinare lo stato della pagina. Se si abilita questa impostazione, gli utenti potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se si disabilita questa impostazione, gli utenti non potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco. Se non si configura l'impostazione di questo criterio, gli utenti non potranno mantenere informazioni nella cronologia del browser, nei Preferiti, in un archivio XML o direttamente in una pagina Web salvata su disco.  
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area Intranet - Bloccare le autorizzazioni Java**  
  L'impostazione di questo criterio consente di gestire le autorizzazioni per le applet Java. Se si abilita l'impostazione di questo criterio, è possibile scegliere le opzioni dalla casella a discesa. Personalizza consente di controllare le impostazioni delle autorizzazioni singolarmente. Protezione bassa consente alle applet di eseguire tutte le operazioni. Protezione media abilita l'esecuzione delle applet nell'ambiente sandbox (area di memoria all'esterno della quale il programma non può eseguire chiamate) e funzionalità come lo spazio di lavoro (area di archiviazione protetta e sicura nel computer client) e l'I/O di file controllato dall'utente. Protezione alta abilita l'esecuzione delle applet nell'ambiente sandbox. Disabilitare Java per impedire l'esecuzione di tutte le applet. Se si disabilita l'impostazione di questo criterio, le applet Java non potranno essere eseguite. Se non si configura l'impostazione di questo criterio, le applet Java vengono disabilitate.
  
  **Default**: disabilitare java  
  
- **Modalità protetta avanzata in Internet Explorer**  
  La modalità protetta avanzata offre maggiore protezione da siti Web dannosi utilizzando processi a 64 bit nelle versioni a 64 bit di Windows. Per i computer che eseguono almeno Windows 8, la modalità protetta avanzata limita anche i percorsi leggibili da Internet Explorer nel Registro di sistema e nel file system. Se si abilita questa impostazione, viene attivata la modalità protetta avanzata. Qualsiasi area per cui è abilitata la modalità protetta utilizzerà la modalità protetta avanzata. Gli utenti non potranno disattivare la modalità protetta avanzata. Se si disabilita questa impostazione, viene disattivata la modalità protetta avanzata. Qualsiasi area per cui è abilitata la modalità protetta utilizzerà la versione della modalità protetta introdotta in Internet Explorer 7 per Windows Vista. Se questa impostazione non viene configurata, gli utenti possono attivare o disattivare la modalità protetta avanzata nella scheda Avanzate della finestra di dialogo Opzioni Internet.
  
  **Impostazione predefinita**: Abilitato  
  
- **Internet Explorer - Ignorare gli avvisi del filtro SmartScreen**  
  L'impostazione di questo criterio determina se l'utente può ignorare gli avvisi del filtro SmartScreen. Il filtro SmartScreen segnala i file eseguibili che gli utenti di Internet Explorer non scaricano spesso da Internet. Se si abilita l'impostazione di questo criterio, gli avvisi del filtro SmartScreen bloccheranno l'utente. Se si disabilita o non si configura l'impostazione di questo criterio, l'utente potrà ignorare gli avvisi del filtro SmartScreen.
  
  **Impostazione predefinita**: Disabilitato  
  
- **Internet Explorer - Area con restrizioni - META REFRESH**  
  L'impostazione di questo criterio consente di gestire il reindirizzamento del browser di un utente a un'altra pagina Web nel caso in cui l'autore della pagina Web usi l'impostazione (tag) META REFRESH per il reindirizzamento dei browser a un'altra pagina Web. Se si abilita l'impostazione di questo criterio, quando il browser di un utente carica una pagina contenente un'impostazione META REFRESH attiva potrà essere reindirizzato a un'altra pagina Web. Se si disabilita l'impostazione di questo criterio, quando il browser di un utente carica una pagina contenente un'impostazione META REFRESH attiva, non potrà essere reindirizzato a un'altra pagina Web. Se non si configura l'impostazione di questo criterio, quando il browser di un utente carica una pagina contenente un'impostazione META REFRESH attiva, non potrà essere reindirizzato a un'altra pagina Web.
  
  **Impostazione predefinita**: Disabilitato  
  
## <a name="local-policies-security-options"></a>Opzioni di sicurezza dei criteri locali
Per altre informazioni, vedere [Policy CSP - LocalPoliciesSecurityOptions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions) (Provider di servizi di configurazione dei criteri - LocalPoliciesSecurityOptions) nella documentazione di Windows. 

- **Limitare l'accesso anonimo a named pipe e condivisioni**  
  Quando abilitata, questa impostazione di sicurezza limita l'accesso anonimo alle condivisioni e pipe alle impostazioni per: (1) le Named pipe che è possibile accedere in modo anonimo (2) le condivisioni che sono accessibili in modo anonimo
  
  **Default**: Sì  
  
- **Sicurezza sessione minima per server basati su NTLM SSP**  
  Questa impostazione di sicurezza consente ai server di richiedere la negoziazione della crittografia a 128 bit e/o della sicurezza di sessione NTLMv2. Tali valori dipendono dal valore dell'impostazione di sicurezza Livello di autenticazione di LAN Manager. Le opzioni sono: richiedono sicurezza della sessione NTLMv2: la connessione avrà esito negativo se non viene negoziato l'integrità del messaggio. Richiedi crittografia a 128 bit. Se la crittografia avanzata (a 128 bit) non viene negoziata, la connessione non riesce.
  
  **Impostazione predefinita**: Richiedi NTLM V2 e crittografia a 128 bit  
  
- **Minuti di inattività della schermata di blocco prima dell'attivazione dello screen saver**  
  Il sistema rileva l'inattività di una sessione di accesso e, se il tempo di inattività supera il limite di inattività, verrà eseguito lo screen saver bloccando la sessione.
  
  **Impostazione predefinita**: 15
  
- **Richiedere al client di aggiungere sempre la firma digitale alle comunicazioni** Questa impostazione di sicurezza determina se tutto il traffico inviato sul canale sicuro dal membro di dominio deve essere firmato o crittografato. Quando si aggiunge un computer a un dominio, viene creato un account computer. All'avvio il sistema usa quindi la password di tale account computer per creare un canale sicuro con un controller di dominio del proprio dominio. Il canale sicuro viene usato per eseguire operazioni come l'autenticazione pass-through NTLM, la ricerca dei nomi SID LSA e altre. Questa impostazione determina se tutto il traffico inviato sul canale sicuro dal membro di dominio soddisfa i requisiti di sicurezza minimi. In particolare, specifica se tutto il traffico inviato sul canale sicuro dal membro di dominio deve essere firmato o crittografato. Se questo criterio è abilitato, il canale sicuro viene creato esclusivamente se la firma o la crittografia di tutto il traffico sul canale sicuro viene negoziata. Se questo criterio è disabilitato, quindi crittografia e firma di tutto il traffico di un canale protetto viene negoziata con il Controller di dominio nel qual caso il livello di firma e crittografia dipende la versione del Controller di dominio e le impostazioni dei due seguenti i criteri: membro del dominio: digitalmente crittografare i dati del canale sicuro (quando possibile) membro del dominio: firma digitale ai protetto i dati del canale (quando possibile)
  
  **Default**: Sì
  
- **Livello di autenticazione**  
  Questa impostazione di sicurezza specifica il protocollo di autenticazione Richiesta di verifica/Risposta usato per gli accessi di rete. L'opzione selezionata determina il livello del protocollo di autenticazione usato dai client, il livello della sicurezza di sessione negoziata e il livello di autenticazione accettato dai server. Sono disponibili le opzioni seguenti.  
  - *Invia risposte LM e NTLM*: i client usano l'autenticazione LM e NTLM e non usano mai la sicurezza di sessione NTLMv2. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia LM e NTLM - NTLMv2 se negoziata*: i client usano l'autenticazione LM e NTLM, nonché la sicurezza di sessione NTLMv2 se il server la supporta. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia solo risposta NTLM*: i client usano solo l'autenticazione NTLM e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia solo risposta NTLMv2*: i client usano solo l'autenticazione NTLMv2 e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio accettano l'autenticazione LM, NTLM e NTLMv2. 
  - *Invia solo risposta NTLMv2, rifiuta LM*: i client usano solo l'autenticazione NTLMv2 e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio rifiutano l'autenticazione LM e accettano solo l'autenticazione NTLM e NTLMv2. 
  - *Invia solo risposta NTLMv2, rifiuta LM e NTLM*: i client usano solo l'autenticazione NTLMv2 e la sicurezza di sessione NTLMv2, se il server la supporta. I controller di dominio rifiutano l'autenticazione LM e NTLM e accettano solo l'autenticazione NTLMv2. 
    
  **Impostazione predefinita**: Invia solo risposta NTLMv2. Rifiuta LM e NTLM
  
- **Impedire ai client di inviare le password non crittografate a server SMB di terze parti**  
  Se questa impostazione di sicurezza è abilitata, durante l'autenticazione il redirector SMB (Server Message Block) può inviare password in formato non crittografato ai server SMB non Microsoft che non supportano la crittografia delle password. L'invio di password non crittografate rappresenta un rischio di sicurezza.
  
  **Default**: Sì
  
- **Disabilitare sempre l'aggiunta della firma digitale del server alle comunicazioni**  
  Questa impostazione di sicurezza determina se il client SMB deve tentare di negoziare la firma dei pacchetti SMB. Il protocollo SMB (Server Message Block) costituisce la base delle funzionalità Microsoft per la condivisione di file e stampanti e di molte altre funzionalità di rete, come l'amministrazione remota di Windows. Per impedire gli attacchi man in the middle che modificano i pacchetti SMB durante la trasmissione, il protocollo SMB supporta la firma digitale dei pacchetti SMB. L'impostazione di questo criterio determina se il componente client di SMB deve tentare di negoziare la firma dei pacchetti SMB quando si connette a un server SMB. Se questa impostazione è abilitata, il client di rete Microsoft richiederà al server di eseguire la firma dei pacchetti SMB al momento della configurazione della sessione. Se la firma dei pacchetti è stata abilitata sul server, la firma dei pacchetti sarà negoziata. Se questo criterio è disabilitato, il client SMB non potrà mai negoziare la firma dei pacchetti SMB.
  
  **Default**: Sì
  
- **Comportamento della richiesta di elevazione dei privilegi per gli amministratori**  
  L'impostazione di questo criterio specifica il comportamento della richiesta di elevazione dei privilegi per gli amministratori. Le opzioni disponibili sono: 
    - *Esegui con privilegi elevati senza chiedere conferma*: consente di eseguire un'operazione che richiede l'elevazione dei privilegi senza richiedere consenso o credenziali. Nota: usare questa opzione solo in ambienti molto vincolati. 
    - *Richiedi le credenziali nel desktop protetto*: quando un'operazione richiede l'elevazione dei privilegi, l'utente del desktop protetto dovrà immettere il nome utente e la password di un utente con i privilegi necessari. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio più elevato disponibile. 
    - *Richiedi il consenso nel desktop protetto*: quando un'operazione richiede l'elevazione dei privilegi, l'utente del desktop protetto dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile. 
    - *Richiedi credenziali*: quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà inserire un nome utente e una password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente. 
    - *Richiedi il consenso*: quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile.  
    - *Richiedi il consenso per file binari non Windows*: quando un'operazione per un'applicazione non Microsoft richiede l'elevazione dei privilegi, sul desktop protetto l'utente dovrà scegliere tra le opzioni Consenti o Nega. Se l'utente acconsente, l'operazione continuerà con il privilegio più elevato disponibile.   
  
  **Impostazione predefinita**: Richiedi il consenso nel desktop sicuro
  
- **Sicurezza sessione minima per client basati su NTLM SSP**  
  Questa impostazione di sicurezza consente ai client di richiedere la negoziazione della crittografia a 128 bit e/o della sicurezza di sessione NTLMv2. Tali valori dipendono dal valore dell'impostazione di sicurezza Livello di autenticazione di LAN Manager. Le opzioni disponibili sono:
  - Richiedi la protezione di sessione NTLMv2: la connessione avrà esito negativo se non viene negoziato NTLMv2 protocollo. 
  - *Richiedere la crittografia a 128 bit*: la connessione avrà esito negativo se non viene negoziata una crittografia avanzata (128 bit).
  - *Richiedi NTLM V2 e la crittografia a 128 bit*. 

  **Impostazione predefinita**: Richiedi NTLM V2 e la crittografia a 128 bit
  
- **Comportamento in caso di rimozione della smart card**  
    Questa impostazione di sicurezza determina le conseguenze della rimozione della smart card di un utente connesso dal lettore di smart card. Le opzioni disponibili sono:
     - *Nessuna azione*. 
     - *Bloccare una Workstation* -workstation è bloccata quando viene rimossa la smart card, consentendo agli utenti di lasciare l'area, rimuovere la smart card con loro e comunque mantenere una sessione protetta.
     - *Imponi disconnessione*: l'utente viene automaticamente disconnesso quando la smart card viene rimossa.
     - *Disconnetti la sessione Desktop remoto*: la rimozione della smart card determina la disconnessione della sessione senza disconnettere l'utente. Questa modalità consente all'utente di inserire la smart card e di riprendere la sessione in seguito oppure di usare un altro terminale dotato di lettore di smart card senza dover effettuare un'altra connessione. Se la sessione è locale, questo criterio funziona in modo identico all'opzione Blocca workstation.  <br><br>
    
  **Default**: blocca la workstation
  
- **Bloccare l'enumerazione anonima di account e condivisioni SAM**  
  Questa impostazione di sicurezza determina se consentire l'enumerazione anonima degli account e delle condivisioni SAM. In Windows agli utenti anonimi è consentita l'esecuzione di determinate operazioni, come l'enumerazione dei nomi degli account di dominio e delle condivisioni di rete. Questo è utile ad esempio quando l'amministratore vuole concedere l'accesso agli utenti di un dominio attendibile che non mantiene una relazione di trust reciproca. Se non si intende consentire l'enumerazione anonima degli account e delle condivisioni SAM, impostare questo criterio su *Sì*.
  
  **Default**: Sì
  
- **Bloccare l'accesso remoto con password vuota**  
  Questa impostazione di sicurezza determina se gli account locali non protetti da password possono essere usati per accedere da postazioni diverse dalla console del computer fisico. Se abilitata, gli account locali che non sono protette da password devono usare la tastiera del computer per accedere. 

  *Avviso*: per i computer che non si trovano in posizioni fisicamente sicure è consigliabile applicare sempre criteri password complessi a tutti gli account utente locali. In caso contrario, chiunque riesca ad accedere fisicamente al computer può effettuare l'accesso usando un account utente privo di password. Questa misura è particolarmente importante per i computer portatili. 

  Se si applicano questi criteri di sicurezza al gruppo Everyone, nessun utente può eseguire l'accesso tramite Servizi Desktop remoto. Questa impostazione non interessa gli accessi eseguiti usando account di dominio. Le applicazioni che usano accessi interattivi remoti possono eludere questa impostazione.
  
  **Default**: Sì
  
- **Comportamento della richiesta di elevazione dei privilegi per gli utenti standard**  
  L'impostazione di questo criterio specifica il comportamento della richiesta di elevazione dei privilegi per gli utente standard. 
  - *Rifiuta automaticamente le richieste di elevazione dei privilegi*: quando un'operazione richiede l'elevazione dei privilegi, viene visualizzato un messaggio di errore di accesso negato che può essere configurato. In un'organizzazione in cui i desktop vengono eseguiti come account utente standard, questa impostazione può contribuire a ridurre le chiamate al supporto tecnico. 
  - *Richiedi le credenziali nel desktop protetto*: quando un'operazione richiede l'elevazione dei privilegi, sul desktop protetto l'utente dovrà immettere un nome utente e una password differenti. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente. 
  - *Richiedi credenziali*: quando un'operazione richiede l'elevazione dei privilegi, l'utente dovrà inserire un nome utente e una password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente.  
  
  **Impostazione predefinita**: Rifiuta automaticamente le richieste di elevazione dei privilegi
  
- **Richiedere la modalità Approvazione amministratore per gli amministratori**  
  L'impostazione di questo criterio specifica il comportamento di tutte le impostazioni dei criteri di Controllo dell'account utente per il computer. Se questa impostazione viene modificata, è necessario riavviare il computer. Le opzioni disponibili sono:   
  - *Non configurato*: la modalità Approvazione amministratore e i criteri correlati di Controllo dell'account utente sono disattivati. Nota: se questa impostazione è disattivata, Centro sicurezza PC segnala che la sicurezza complessiva del sistema operativo è ridotta. 
  - *Sì*: la modalità Approvazione amministratore è abilitata. Perché l'account predefinito Administrator e tutti gli altri utenti membri del gruppo Administrators possano essere eseguiti in modalità Approvazione amministratore, è necessario che questo criterio sia abilitato e che tutti i criteri di Controllo dell'account utente correlati siano impostati in modo appropriato.  
  
  **Default**: Sì
  
- **Impedire l'enumerazione anonima degli account SAM**  
  Questa impostazione di sicurezza determina quali autorizzazioni aggiuntive vengono concesse in caso di connessioni anonime al computer. In Windows agli utenti anonimi è consentita l'esecuzione di determinate operazioni, come l'enumerazione dei nomi degli account di dominio e delle condivisioni di rete. Questo è utile ad esempio quando l'amministratore vuole concedere l'accesso agli utenti di un dominio attendibile che non mantiene una relazione di trust reciproca. Questa opzione di sicurezza consente di specificare restrizioni aggiuntive per connessioni anonime, ad esempio: 
  - *Sì*: non consentire l'enumerazione degli account SAM. Questa opzione sostituisce Everyone con Authenticated Users nelle autorizzazioni di sicurezza per le risorse.
  - *Non configurato*: nessuna restrizione aggiuntiva. Vengono usate le autorizzazioni predefinite.  
  
  **Default**: Sì
  
- **Consentire chiamate remote al sistema di gestione degli account di sicurezza**  
  L'impostazione di questo criterio consente di limitare le connessioni RPC remote al sistema di gestione degli account di sicurezza. Se il criterio non viene selezionato, viene usato il descrittore di sicurezza predefinito.
  
  **Impostazione predefinita**: *O:BAG:BAD:(A;;RC;;;BA)*

- **Usare la modalità Approvazione amministratore**  
  L'impostazione di questo criterio specifica il comportamento della modalità Approvazione amministratore per l'account Administrator predefinito. Le opzioni disponibili sono: 
  - *Sì*: l'account predefinito Administrator usa la modalità Approvazione amministratore. Per impostazione predefinita, per qualunque operazione che richiede l'elevazione dei privilegi l'utente dovrà scegliere se autorizzare o rifiutare l'esecuzione. 
  - *Non configurato*: l'account predefinito Administrator esegue tutte le applicazioni con privilegi amministrativi completi.  

  **Default**: Sì
  
- **Consentire le applicazioni con accesso all'interfaccia utente per percorsi sicuri**  
  L'impostazione di questo criterio specifica se i programmi con accesso all'interfaccia utente (UIAccess o UIA) possono disabilitare automaticamente il desktop protetto per le richieste di elevazione dei privilegi provenienti da un utente standard. 
  - *Sì*: i programmi con Automazione interfaccia utente, incluso Assistenza remota di Windows, disabilitano automaticamente il desktop protetto per le richieste di elevazione dei privilegi. Se non si disabilita l'impostazione del criterio "Controllo account utente: alla richiesta di elevazione passa al desktop sicuro", le richieste vengono visualizzate sul desktop dell'utente interattivo invece che sul desktop protetto. 
  - *Non configurato*: il desktop protetto può essere disabilitato solo dall'utente del desktop interattivo oppure disabilitando l'impostazione del criterio "Controllo account utente: alla richiesta di elevazione passa al desktop sicuro".  

  **Default**: Sì

- **Rilevare installazioni di applicazioni e richiedere l'elevazione dei privilegi**  
  L'impostazione di questo criterio specifica il comportamento del rilevamento di installazioni di applicazioni nel computer. Le opzioni disponibili sono: 
  - *Abilitato*: per i pacchetti di installazione delle applicazioni che richiedono l'elevazione dei privilegi, l'utente dovrà immettere nome utente e password amministrativi. Se l'utente immette credenziali valide, l'operazione continuerà con il privilegio pertinente. 
  - *Disabilitato*: i pacchetti di installazione delle applicazioni non vengono rilevati e non viene richiesta l'elevazione dei privilegi. È consigliabile disattivare questa impostazione nel caso di un'organizzazione che esegue desktop utente standard e utilizza tecnologie di installazione delegata, ad esempio Estensione dell'installazione software basata su Criteri di gruppo o Systems Management Server (SMS), in quanto il rilevamento dei programmi di installazione non è necessario.  
  
  **Default**: Sì
  
- **Non archiviare il valore hash di LAN Manager al cambio di password successivo**  
  Questa impostazione di sicurezza specifica se, al cambio di password successivo, deve essere archiviato il valore hash di LAN Manager per la nuova password. Il valore hash di LAN Manager è relativamente vulnerabile e soggetto ad attacchi rispetto all'hash di Windows NT, che è basato su una crittografia più avanzata. Poiché l'hash di LAN Manager è archiviato nel database di sicurezza del computer locale, un eventuale attacco al database di sicurezza può compromettere le password.
  
  **Default**: Sì

- **Virtualizzare gli errori di scrittura nel file e nel Registro di sistema in percorsi specifici per ogni utente**  
  L'impostazione di questo criterio specifica se gli errori di scrittura delle applicazioni vengono reindirizzati in percorsi definiti sia nel Registro di sistema sia nel file system. Questo criterio riduce l'impatto delle applicazioni che vengono eseguite con account amministratore ed eseguono la scrittura dei dati in fase di esecuzione in *%ProgramFiles%*, *%Windir%*, *%Windir%\system32* o *HKLM\Software*.
  
  **Default**: Sì

## <a name="ms-security-guide"></a>Guida alla sicurezza MS  
Per altre informazioni, vedere [Policy CSP - MSSecurityGuide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-mssecurityguide) (Provider di servizi di configurazione dei criteri - MSSecurityGuide) nella documentazione di Windows.  

- **Applicare le restrizioni di Controllo dell'account all'accesso alla rete**  
  **Impostazione predefinita**: Abilitato
  
- **Configurazione dell'avvio del driver client SMB v1**  
  **Default**: disabilitata driver
  
- **Server SMB v1**  
  **Impostazione predefinita**: Disabilitato
  
- **Autenticazione del digest**  
  **Impostazione predefinita**: Disabilitato
  
- **Proteggere da sovrascrittura la gestione di eccezioni strutturata**  
  **Impostazione predefinita**: Abilitato
  
## <a name="mss-legacy"></a>MSS Legacy  
Per altre informazioni, vedere [Policy CSP - MSSLegacy](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-msslegacy) (Provider di servizi di configurazione dei criteri - MSSLegacy) nella documentazione di Windows.  

- **Livello di protezione del routing di origine dell'IP di rete**  
  **Default**: protezione più elevata  
  
- **Ignorare le richieste di rilascio nome NetBIOS nella rete, ad eccezione dei server WINS**  
  **Impostazione predefinita**: Abilitato
  
- **Livello di protezione del routing di origine IPv6 di rete**  
  **Default**: protezione più elevata

- **Eseguire l'override di OSPF generati con reindirizzamenti ICM di rete**  
  **Impostazione predefinita**: Disabilitato
  
## <a name="power"></a>Alimentazione  
Per altre informazioni, vedere [Policy CSP - Power](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-power) (Provider di servizi di configurazione dei criteri - Power) nella documentazione di Windows.  

- **Richiedere la password alla riattivazione durante l'alimentazione da rete elettrica**  
  L'impostazione di questo criterio specifica se all'utente viene richiesta una password quando il sistema viene riattivato dopo la sospensione. Se si abilita o non si configura l'impostazione di questo criterio, all'utente viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione. Se si disabilita l'impostazione di questo criterio, all'utente non viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione.
  
  **Impostazione predefinita**: Abilitato
  
- **Stati di standby durante la sospensione durante l'alimentazione a batteria**  
  Questa impostazione criterio consente di gestire se Windows è possibile usare gli stati di standby quando si inserisce il computer in uno stato di sospensione. Se si abilita o non si configura l'impostazione di questo criterio, Windows usa gli stati di standby per impostare lo stato di sospensione del computer. Se si disabilita l'impostazione di questo criterio, gli stati di standby (S1-S3) non sono consentiti.
  
  **Impostazione predefinita**: Disabilitato
  
- **Stati di standby durante la sospensione durante l'alimentazione da rete elettrica**  
  Questa impostazione criterio consente di gestire se Windows è possibile usare gli stati di standby quando si inserisce il computer in uno stato di sospensione. Se si abilita o non si configura l'impostazione di questo criterio, Windows usa gli stati di standby per impostare lo stato di sospensione del computer. Se si disabilita l'impostazione di questo criterio, gli stati di standby (S1-S3) non sono consentiti.
  
  **Impostazione predefinita**: Disabilitato
  
- **Richiedere la password alla riattivazione durante l'alimentazione a batteria**  
  L'impostazione di questo criterio specifica se all'utente viene richiesta una password quando il sistema viene riattivato dopo la sospensione. Se si abilita o non si configura l'impostazione di questo criterio, all'utente viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione. Se si disabilita l'impostazione di questo criterio, all'utente non viene richiesto di immettere una password quando il sistema viene riattivato dopo la sospensione.
  
  **Impostazione predefinita**: Abilitato
  
## <a name="remote-desktop-services"></a>Servizi Desktop remoto  
Per altre informazioni, vedere [Policy CSP - RemoteDesktopServices](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotedesktopservices) (Provider di servizi di configurazione dei criteri - RemoteDesktopServices) nella documentazione di Windows.  

- **Bloccare il salvataggio delle password**  
  Controlla se è possibile salvare le password nel computer da Connessione Desktop remoto. Se si abilita questa impostazione, la casella di controllo di salvataggio della password in Connessione Desktop remoto viene disabilitata e gli utenti non potranno salvare le password. Quando un utente apre un file RDP tramite Connessione Desktop remoto e salva le proprie impostazioni, qualsiasi password presente in precedenza nel file RDP viene eliminata. Se si disabilita questa impostazione o la si lascia non configurata, l'utente può salvare le password in Connessione Desktop remoto.
  
   **Impostazione predefinita**: Abilitato
  
- **Comunicazione RPC protetta**  
  Specifica se un server host sessione Desktop remoto richiede la comunicazione RPC protetta con tutti i client o consente la comunicazione non protetta. È possibile usare questa impostazione per rafforzare la protezione della comunicazione RPC con i client, consentendo solo richieste autenticate e crittografate. Se lo stato è impostato su Abilitato, Servizi Desktop remoto accetta le richieste dai client RPC che supportano richieste protette e non consente la comunicazione non protetta con client non attendibili. Se lo stato è impostato su Disabilitato, Servizi Desktop remoto richiede sempre la protezione per tutto il traffico RPC. La comunicazione non protetta, tuttavia, è consentita per i client RPC che non rispondono alla richiesta. Se lo stato è impostato su Non configurato, la comunicazione non protetta è consentita. Nota: l'interfaccia RPC viene usata per l'amministrazione e la configurazione di Servizi Desktop remoto.
  
  **Impostazione predefinita**: Abilitato
  
- **Bloccare il reindirizzamento delle unità**  
  L'impostazione di questo criterio specifica se impedire il mapping delle unità dei client in una sessione di Servizi Desktop remoto (reindirizzamento delle unità). Per impostazione predefinita, un server host sessione Desktop remoto esegue automaticamente il mapping di unità di client al momento della connessione. Le unità mappate vengono visualizzate nell'albero delle cartelle della sessione in Esplora file o in Computer nel formato *\<letteraunità>* in *\<nomecomputer>*. È possibile usare l'impostazione di questo criterio per eseguire l'override di questo comportamento. Se si abilita l'impostazione di questo criterio, il reindirizzamento delle unità dei client non è consentito nelle sessioni di Servizi Desktop remoto e il reindirizzamento della copia dei file degli Appunti non è consentito nei computer che eseguono Windows Server 2003, Windows 8 e Windows XP. Se si disabilita l'impostazione di questo criterio, il reindirizzamento delle unità dei client è sempre consentito. Inoltre, se è consentito il reindirizzamento degli Appunti, il reindirizzamento della copia dei file degli Appunti è sempre consentito. Se non si configura l'impostazione di questo criterio, il reindirizzamento delle unità dei client e il reindirizzamento della copia dei file degli Appunti non sono specificate a livello di Criteri di gruppo.
  
  **Impostazione predefinita**: Abilitato
  
- **Richiedere la password al momento della connessione**  
  L'impostazione di questo criterio specifica se Servizi Desktop remoto deve sempre richiedere la password al client al momento della connessione. È possibile usare questa impostazione per imporre la richiesta della password agli utenti che accedono a Servizi Desktop remoto, anche se hanno già specificato la password nel client di Connessione Desktop remoto. Per impostazione predefinita, Servizi Desktop remoto consente agli utenti di accedere automaticamente tramite l'immissione di una password nel client di Connessione Desktop remoto. Se si abilita l'impostazione di questo criterio, gli utenti non possono accedere automaticamente a Servizi Desktop remoto specificando la propria password nel client di Connessione Desktop remoto, ma viene loro richiesto di immettere una password per l'accesso. Se si disabilita l'impostazione di questo criterio, gli utenti possono sempre accedere automaticamente a Servizi Desktop remoto specificando la propria password nel client di Connessione Desktop remoto. Se non si configura l'impostazione di questo criterio, l'accesso automatico non è specificato a livello di Criteri di gruppo. 
  
  **Impostazione predefinita**: Abilitato
  
- **Livello di crittografia della connessione client a Servizi Desktop remoto**  
  Specifica se richiedere l'uso di un livello di crittografia specifico per proteggere le comunicazioni tra computer client e server host sessione Desktop remoto durante le connessioni Remote Desktop Protocol (RDP). Questo criterio si applica solo quando si usa la crittografia RDP nativa. La crittografia RDP (in contrapposizione alla crittografia SSL), tuttavia, non è consigliata. Questo criterio non si applica alla crittografia SSL. Se si abilita l'impostazione di questo criterio, tutte le comunicazioni tra client e server host sessione Desktop remoto durante le connessioni remote devono usare il metodo di crittografia specificato in questa impostazione. Per impostazione predefinita, il livello di crittografia è impostato su Alto. Sono disponibili i metodi di crittografia seguenti:  
  - *Alto*: l'impostazione Alto consente di crittografare i dati inviati dal client al server e dal server al client usando la crittografia avanzata a 128 bit. Usare questo livello di crittografia in ambienti che contengono solo client a 128 bit, ad esempio client che eseguono Connessione Desktop remoto. I client che non supportano questo livello di crittografia non possono connettersi a server host sessione Desktop remoto.  
  - *Compatibile con il client*: l'impostazione Compatibile con il client consente di crittografare i dati scambiati tra il client e il server con il livello massimo di complessità della chiave supportato dal client. Usare questo livello di crittografia in ambienti che includono client che non supportano la crittografia a 128 bit.  
  - *Basso*: l'impostazione Basso consente di crittografare solo i dati inviati dal client al server tramite crittografia a 56 bit.  
  
  Se si disabilita o non si configura questa impostazione, il livello di crittografia da usare per le connessioni remote a server host sessione Desktop remoto non viene imposto tramite Criteri di gruppo. Importante: è possibile configurare la conformità FIPS (Federal Information Processing Standard) tramite la crittografia di sistema. Usare algoritmi conformi a FIPS per le impostazioni di crittografia, hash e firma in Criteri di gruppo, in Configurazione computer\Impostazioni di Windows\Impostazioni sicurezza\Criteri locali\Opzioni di sicurezza. L'impostazione conforme a FIPS consente di crittografare e decrittografare i dati inviati dal client al server e dal server al client con gli algoritmi di crittografia Federal informazioni Processing Standard (FIPS) 140 usando i moduli di crittografia Microsoft. Usare questo livello di crittografia quando le comunicazioni tra client e server host sessione Desktop remoto richiedono il massimo livello di crittografia.
  
  **Default**: elevata
  
## <a name="remote-management"></a>Gestione remota  
Per altre informazioni, vedere [Policy CSP - RemoteManagement](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remotemanagement) (Provider di servizi di configurazione dei criteri - RemoteManagement) nella documentazione di Windows.  

- **Bloccare l'archiviazione eseguita come credenziali**  
  Autenticazione client di base
  
  **Impostazione predefinita**: Abilitato
  
- **Autenticazione di base**  
  L'impostazione di questo criterio consente di gestire se il servizio Gestione remota Windows (WinRM) deve accettare l'autenticazione di base da un client remoto. Se si abilita l'impostazione di questo criterio, il servizio Gestione remota Windows accetta l'autenticazione di base da un client remoto. Se si disabilita o non si configura l'impostazione di questo criterio, il servizio Gestione remota Windows non accetta l'autenticazione di base da un client remoto.
  
  **Impostazione predefinita**: Disabilitato
  
- **Bloccare l'autenticazione del digest del client**  
  L'impostazione di questo criterio consente di gestire se il client Gestione remota Windows (WinRM) deve usare l'autenticazione del digest. Se si abilita l'impostazione di questo criterio, il client WinRM non usa l'autenticazione del digest. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM usa l'autenticazione del digest.
  
  **Impostazione predefinita**: Abilitato
  
- **Traffico non crittografato**  
  L'impostazione di questo criterio consente di gestire se il servizio Gestione remota Windows (WinRM) può inviare e ricevere messaggi non crittografati attraverso la rete. Se si abilita l'impostazione di questo criterio, il client WinRM invia e riceve messaggi non crittografati attraverso la rete. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM invia e riceve attraverso la rete solo messaggi crittografati.  
  
  **Impostazione predefinita**: Disabilitato
  
- **Traffico non crittografato client**  
  L'impostazione di questo criterio consente di gestire se il client Gestione remota Windows (WinRM) può inviare e ricevere messaggi non crittografati attraverso la rete. Se si abilita l'impostazione di questo criterio, il client WinRM invia e riceve messaggi non crittografati attraverso la rete. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM invia e riceve attraverso la rete solo messaggi crittografati.
  
  **Impostazione predefinita**: Disabilitato
  
- **Autenticazione client di base**  
  L'impostazione di questo criterio consente di gestire se il client Gestione remota Windows (WinRM) usa l'autenticazione di base. Se si abilita l'impostazione di questo criterio, il client WinRM usa l'autenticazione di base. Se il servizio WinRM è configurato per l'uso del trasporto HTTP, il nome utente e password vengono inviati attraverso la rete come testo non crittografato. Se si disabilita o non si configura l'impostazione di questo criterio, il client WinRM non usa l'autenticazione di base.
  
  **Impostazione predefinita**: Disabilitato
  

## <a name="remote-procedure-call"></a>Chiamata a procedura remota (RPC)  
Per altre informazioni, vedere [Policy CSP - RemoteProcedureCall](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-remoteprocedurecall) (Provider di servizi di configurazione dei criteri - RemoteProcedureCall) nella documentazione di Windows.  

- **Opzioni client RPC non autenticati**  
  L'impostazione di questo criterio controlla il modo in cui il runtime del server RPC gestisce i client RPC non autenticati che si connettono a server RPC. L'impostazione di questo criterio influisce su tutte le applicazioni RPC. In un ambiente di dominio usare con cautela l'impostazione di questo criterio perché può influire su una vasta gamma di funzionalità, inclusa l'elaborazione dei Criteri di gruppo stessi. Il ripristino del valore precedente dopo una modifica all'impostazione di questo criterio può richiedere un intervento manuale in ogni computer interessato. L'impostazione di questo criterio non deve mai essere applicata a un controller di dominio. Se si disabilita l'impostazione di questo criterio, il runtime del server RPC usa il valore "Autenticato" in Windows Client e il valore "Nessuno" nelle versioni di Windows Server che supportano questa impostazione. Se non si configura l'impostazione di questo criterio, questa rimane disabilitata. Il runtime del server RPC si comporta come se fosse abilitato con il valore "Autenticato" usato per il client Windows e il valore "Nessuno" usato per gli SKU dei server che supportano questa impostazione. Se si abilita l'impostazione di questo criterio, il runtime del server RPC limita i client RPC non autenticati che si connettono ai server RPC in esecuzione in un computer. Un client viene considerato autenticato se usa una named pipe per comunicare con il server o se usa la sicurezza RPC. Le interfacce RPC che hanno richiesto in modo specifico di essere accessibili per i client non autenticati possono essere esenti da questa limitazione, a seconda del valore selezionato per l'impostazione di questo criterio.  
  - *Nessuno* consente a tutti i client RPC di connettersi ai server RPC in esecuzione nel computer in cui l'impostazione del criterio viene applicata. 
  - *Autenticato* consente solo ai client RPC autenticati (in base alla definizione precedente) di connettersi ai server RPC in esecuzione nel computer in cui l'impostazione del criterio viene applicata. Vengono concesse esenzioni alle interfacce che le hanno richieste. 
  - *Autenticato senza eccezioni* consente solo ai client RPC autenticati (in base alla definizione precedente) di connettersi ai server RPC in esecuzione nel computer in cui l'impostazione del criterio viene applicata. Non sono consentite eccezioni. Nota: l'impostazione di questo criterio viene applicata solo dopo il riavvio del sistema.  

  **Default**: autenticato

## <a name="search"></a>Cerca 
Per altre informazioni, vedere [Policy CSP - Search](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search) (Provider di servizi di configurazione dei criteri - Search) nella documentazione di Windows.  

- **Disabilitare l'indicizzazione di elementi crittografati**  
  Consente o impedisce l'indicizzazione di elementi. Questa opzione è per l'indicizzatore di Ricerca di Windows, che stabilisce se deve essere eseguita l'indicizzazione degli elementi che vengono crittografati, ad esempio i file protetti di Windows Information Protection (WIP). Quando i criteri sono abilitati, gli elementi protetti da WIP vengono indicizzati e i relativi metadati vengono archiviati in un percorso non crittografato. I metadati includono elementi come percorso del file e data di modifica. Quando i criteri sono disabilitati, gli elementi protetti da WIP non vengono indicizzati e non appaiono nei risultati di Cortana o Esplora file. Si può inoltre avere un impatto sulle prestazioni delle app Foto e Groove se nel dispositivo sono presenti molti file multimediali protetti con WIP.
  
**Default**: Sì
  
## <a name="smart-screen"></a>SmartScreen  
Per altre informazioni, vedere [Policy CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen) (Provider di servizi di configurazione dei criteri - SmartScreen) nella documentazione di Windows.  

- **Bloccare l'esecuzione di file non verificati**  
  Impedisce all'utente di eseguire file non verificati. 
  - *Non configurato*: i dipendenti possono ignorare gli avvisi di SmartScreen ed eseguire file dannosi. 
  - *Sì*: i dipendenti non possono ignorare gli avvisi di SmartScreen ed eseguire file dannosi.

  **Default**: Sì

<!-- Not currently available? - **Block unverified file download**  
  By default, Microsoft Edge allows users to bypass (ignore) the Windows Defender SmartScreen warnings about potentially malicious files, allowing them to continue downloading the unverified file(s). Enabling this policy prevents users from bypassing the warnings, blocking them from downloading of the unverified file(s).
  
  **Default**: Yes
 --> 
- **Richiedere SmartScreen per app e file**  
  Consente agli amministratori IT di configurare SmartScreen per Windows.

  **Default**: Sì
  
## <a name="system"></a>Sistema  
Per altre informazioni, vedere [Policy CSP - System](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system) (Provider di servizi di configurazione dei criteri - System) nella documentazione di Windows.  

- **Inizializzazione del driver di esecuzione avvio del sistema**  
  L'impostazione di questo criterio consente di specificare i driver di esecuzione inizializzati in base a una classificazione determinata da un driver di esecuzione avvio antimalware ad esecuzione anticipata. Il driver di esecuzione avvio antimalware ad esecuzione anticipata può restituire le classificazioni seguenti per ogni driver di esecuzione avvio: 
  - *Valido*: il driver è stato firmato e non è stato manomesso.  
  - *Bad* (Non valido): il driver è stato identificato come malware. È consigliabile non consentire i driver non validi noti da inizializzare. 
  - *Bad, but required for boot* (Non valido ma necessario per l'avvio): il driver è stato identificato come malware, ma non è possibile avviare correttamente il computer senza caricare questo driver. 
  - *Sconosciuto*: questo driver non ha ricevuto l'attestazione dell'applicazione di rilevamento di malware in uso e non è stato classificato dal driver di esecuzione avvio antimalware ad esecuzione anticipata.  

  Se si abilita l'impostazione di questo criterio, è possibile scegliere quali driver di esecuzione avvio inizializzare all'avvio successivo del computer. Se si disabilita o non si configura l'impostazione di questo criterio, i driver di esecuzione avvio identificati come validi, sconosciuti o non validi ma critici per l'avvio vengono inizializzati, mentre l'inizializzazione dei driver identificati come non validi viene ignorata. Se l'applicazione di rilevamento di malware non include un driver di esecuzione avvio antimalware ad esecuzione anticipata o se quest'ultimo driver è stato disabilitato, questa impostazione non ha alcun effetto e tutti i driver di esecuzione avvio vengono inizializzati.  
  
  **Impostazione predefinita**: Validi, sconosciuti e dannosi ma fondamentali


## <a name="wi-fi"></a>Wi-Fi  
Per altre informazioni, vedere [Policy CSP - Wifi](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) (Provider di servizi di configurazione dei criteri - Wifi) nella documentazione di Windows.  

- **Blocca Internet condiviso**  
  Specifica se nel dispositivo è possibile la condivisione Internet.  

  **Default**: Sì  

- **Bloccare la connessione automatica a hotspot Wi-Fi**  
  Consente o impedisce al dispositivo di connettersi automaticamente agli hotspot Wi-Fi.  

  **Default**: Sì  
  
## <a name="windows-connection-manager"></a>Gestione connessioni Windows  
Per altre informazioni, vedere [Policy CSP - WindowsConnectionManager](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsconnectionmanager) (Provider di servizi di configurazione dei criteri - WindowsConnectionManager) nella documentazione di Windows.  

- **Bloccare la connessione a reti non di dominio**  
  L'impostazione di questo criterio impedisce ai computer di connettersi contemporaneamente a una rete basata su dominio e a una rete non basata su dominio. Se l'impostazione di questo criterio è abilitata, il computer risponde ai tentativi di connessione di rete automatica e manuale in base alle circostanze seguenti: 
  - Tentativi di connessione automatici Quando il computer è già connesso a una rete basata su dominio, tutti i tentativi di connessione automatica a reti non di dominio vengono bloccati. Quando il computer è già connesso a una rete non basata su dominio, tutti i tentativi di connessione automatica a reti non basate su dominio vengono bloccati. 
  - Tentativi di connessione manuale Quando il computer è già connesso a una rete non basata su dominio o a una rete basata su dominio attraverso supporti diversi da Ethernet e un utente prova a creare una connessione manuale a una rete aggiuntiva in violazione dell'impostazione di questo criterio, la connessione di rete esistente viene interrotta e la connessione manuale viene consentita. Quando il computer è già connesso a una rete non basata su dominio o a una rete basata su dominio tramite Ethernet e un utente tenta di creare una connessione manuale a una rete aggiuntiva in violazione dell'impostazione di questo criterio, la connessione Ethernet esistente viene interrotta e il tentativo di connessione manuale viene bloccato.  

  Se l'impostazione di questo criterio non è configurata o è disabilitata, i computer sono autorizzati a connettersi contemporaneamente a reti di dominio e non di dominio.  

  **Impostazione predefinita**: Abilitato
  
## <a name="windows-defender"></a>Windows Defender  
Per altre informazioni, vedere [Policy CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender) (Provider di servizi di configurazione dei criteri - Defender) nella documentazione di Windows.  

- **Analizzare i messaggi di posta in arrivo**  
  Consente o impedisce l'analisi della posta elettronica.
  
  **Default**: Sì  

- **Avviare i processi di tipo figlio per le app di Office**  
  Alle app di Office non verrà consentito di creare processi figlio. Le app includono Word, Excel, PowerPoint, OneNote e Access. Si tratta di un comportamento tipico del malware, in particolare degli attacchi basati su macro che tentano di usare le app di Office per avviare o scaricare file eseguibili dannosi.
  
  **Default**: blocco
  
- **Tipo di consenso per l'invio di campioni di Defender**  
  Verifica il livello di consenso utente in Windows Defender per l'invio di dati. Se il consenso necessario è già stato concesso, Windows Defender esegue l'invio. In caso contrario, e se l'utente ha specificato di non chiedere mai, viene avviata l'interfaccia utente per la richiesta del consenso utente (se Defender/AllowCloudProtection è consentito) prima dell'invio di dati.
  
  **Impostazione predefinita**: Invia i campioni sicuri automaticamente 
  
- **Intervallo di aggiornamento della firma (in ore)**  
  Intervallo di aggiornamento della firma di Defender in ore
  
  **Impostazione predefinita**: 4
  
- **Tipo di esecuzione del payload scaricato tramite script**  
  Tipo di esecuzione del payload scaricato tramite script di Defender
  
  **Default**: blocco
  
- **Impedire il tipo di intercettazione delle credenziali**  
  Windows Defender Credential Guard usa la protezione basata su virtualizzazione per isolare i segreti in modo che solo il software di sistema con privilegi possa accedervi. L'accesso non autorizzato a questi segreti può provocare attacchi di furto delle credenziali, ad esempio Pass-the-Hash o Pass-The-Ticket. Windows Defender Credential Guard impedisce questi attacchi proteggendo gli hash delle password NTLM, Kerberos Ticket Granting Tickets e le credenziali archiviate dalle applicazioni come credenziali di dominio.
  
  **Default**: abilitare

- **Tipo di esecuzione del contenuto del messaggio di posta elettronica**  
  Questa regola consente di bloccare i seguenti tipi di file venga eseguito o avviata da un messaggio di posta elettronica visualizzata in Microsoft Outlook o webmail (ad esempio Gmail.com o Outlook.com): file eseguibili (ad esempio .exe, DLL o SCR) i file di Script (ad esempio un PS di PowerShell, vbs, VisualBasic o file JavaScript. js) il file di archivio di Script.
  
  **Default**: blocco
  
- **Tipo di protezione di rete**  
  Questo criterio consente di attivare la protezione di rete (Blocca/Controlla) o di disattivarla in Windows Defender Exploit Guard. La protezione di rete è una funzionalità di Windows Defender Exploit Guard che protegge i dipendenti che usano le app dall'accesso a tentativi di phishing, siti che ospitano exploit e contenuti dannosi in Internet. Impedisce anche ai browser di terze parti di connettersi a siti pericolosi. Il tipo di valore è un numero intero. Se si abilita questa impostazione, la protezione di rete verrà attivata e i dipendenti non potranno disattivarla. Il comportamento potrà essere controllato dalle opzioni seguenti: Blocca e Controlla. Se si abilita questo criterio impostando l'opzione "Blocca", gli utenti e le app non possono connettersi a domini dannosi. È possibile visualizzare questa attività di Windows Defender Security Center. Se si abilita questo criterio impostando l'opzione "Controlla", gli utenti e le app non potranno connettersi a domini dannosi. Sarà possibile visualizzare anche questa attività in Windows Defender Security Center. Se si disabilita questo criterio, gli utenti e le app potranno connettersi a domini dannosi. Non sarà possibile visualizzare attività di rete in Windows Defender Security Center. Se non si configura questo criterio, il blocco di rete è disabilitato per impostazione predefinita.
  
  **Default**: abilitare
  
- **Giorno pianificato per l'analisi di Defender**  
  Giorno pianificato per l'analisi di Defender.
  
  **Default**: ogni giorno
  
- **Protezione fornita dal cloud**  
  Per proteggere al meglio il PC, Windows Defender invierà a Microsoft informazioni su qualsiasi problema che si verificherà. Le informazioni saranno analizzate, saranno raccolti altri dettagli sui problemi riscontrati dall'utente corrente e dagli altri clienti. Verranno quindi offerte soluzioni migliorate.
  
  **Default**: Sì  

- **Azione della Protezione da applicazioni potenzialmente di Defender**  
  La funzionalità Protezione da applicazioni potenzialmente indesiderate in Windows Defender Antivirus consente di identificare e bloccare il download e l'installazione delle applicazioni potenzialmente indesiderate negli endpoint in rete. Queste applicazioni non sono considerate virus, malware o altri tipi di minaccia, ma potrebbero agire su endpoint compromettendo le prestazioni e l'uso. Possono essere considerate applicazioni potenzialmente indesiderate anche le applicazioni di dubbia reputazione. Include il comportamento tipico PUA: vari tipi di software di creazione di bundle inserimento di annunci in web browser Driver e utilità di ottimizzazione del Registro di sistema in cui vengono rilevati problemi, richiesta di pagamento per correggere gli errori, ma rimangono nell'endpoint e una senza modifiche o le ottimizzazioni (noto anche come" programmi antivirus inaffidabili"). Queste applicazioni possono aumentare il rischio della rete essere infettata da malware, invalidare le infezioni da malware essere più difficile identificare e può provocare uno spreco di risorse IT in grado di pulire le applicazioni.  
  
  **Default**: blocco  

- **Tipo di codice macro offuscato in script**  
  Il malware e altre minacce possono tentare di offuscare o nascondere il codice dannoso in alcuni file di script. Questa regola impedisce l'esecuzione degli script offuscati.
  
  **Default**: blocco
  
- **Analizzare le unità rimovibili durante un'analisi completa**  
  Consente a Defender di Windows di cercare software dannoso e indesiderato in unità rimovibili, ad esempio in unità flash, durante un'analisi completa. Windows Defender Antivirus analizza tutti i file nei dispositivi USB prima dell'esecuzione.
  
  **Default**: Sì  
  
- **Analizza file di archivio**  
  Analizza file di archivio di Defender.
  
  **Default**: Sì
  
- **Monitoraggio del comportamento**  
  Abilita o disabilita la funzionalità di monitoraggio del comportamento di Windows Defender. Incorporati in Windows 10, questi sensori raccolgono ed elaborano i segnali del comportamento del sistema operativo e inviano questi dati all'istanza cloud isolata e privata di Windows Defender ATP.
  
  **Default**: Sì

- **Analizzare file aperti da cartelle di rete**  
  Se i file sono di sola lettura, non sarà possibile rimuovere eventuale malware rilevato.
  
  **Default**: Sì

- **Tipo di processo non attendibile in USB**  
  Questa regola consente agli amministratori di impedire l'esecuzione di file eseguibili non firmati o non attendibili da unità removibili USD, incluse le schede SD.
  
  **Default**: blocco
  
- **Tipo di inserimento in altri processi per app di Office**  
  Le app di Office, tra cui Word, Excel, PowerPoint e OneNote, non potranno inserire codice in altri processi. Si tratta di un tipico comportamento del malware per eseguire codice malware nel tentativo di nascondere l'attività ai motori di analisi antivirus.
  
  **Default**: blocco
  
- **Consentire tipo di importazioni Win32 da codice macro in Office**  
  Il malware può usare il codice della macro in file di Office per importare e caricare le DLL Win32, che possono poi essere usate per eseguire chiamate API e favorire altre infezioni in tutto il sistema. Questa regola tenta di bloccare file di Office che contengono codice della macro che può importare le DLL Win32. Le app incluse sono Word, Excel, PowerPoint e OneNote.
  
  **Default**: blocco  
  
- **Livello di blocco cloud di Defender**  
  Livello di blocco cloud di Defender.
  
  **Impostazione predefinita**: Non configurato

- **Monitoraggio in tempo reale**  
  Defender richiede il monitoraggio in tempo reale.
  
  **Default**: Sì
  
- **Tipo di contenuto per la creazione o l'avvio di eseguibile nelle app di Office**  
  Questa regola è rivolta ai tipici comportamenti usati da componenti aggiuntivi e script sospetti e dannosi (estensioni) che creano o avviano file eseguibili. Si tratta di una tipica tecnica malware. Le estensioni non possono essere usate dalle app di Office. Queste estensioni usano generalmente Windows Scripting Host (file con estensione wsh) per eseguire script che automatizzano determinate attività oppure aggiungono funzionalità create dall'utente
  
  **Default**: blocco

## <a name="windows-ink-workspace"></a>Area Windows Ink  
Per altre informazioni, vedere [Policy CSP - WindowsInkWorkspace](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace) (Provider del servizio di configurazione dei criteri - WindowsInkWorkspace) nella documentazione di Windows.  

- **Area Ink**  
  Specifica se consentire o meno all'utente di accedere all'area Ink. 
  - *Disabilitato*: l'accesso all'area Ink è disabilitato. La funzionalità è disattivata.
  - *Abilitato*: la funzionalità Area Ink è attivata, ma l'utente non può accedervi sopra la schermata di blocco.
  - *Non configurato* : l'area Windows Ink è attivato e l'utente può usare la schermata di blocco.  

  **Impostazione predefinita**: Abilitato
 
## <a name="windows-powershell"></a>Windows PowerShell  
Per altre informazioni, vedere [Policy CSP - WindowsPowerShell](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowspowershell) (Provider di servizi di configurazione dei criteri - WindowsPowerShell) nella documentazione di Windows.  

- **Registrazione blocco di script della shell di PowerShell**  
  L'impostazione di questo criterio consente la registrazione di tutti gli input di script di PowerShell nel registro eventi Microsoft-Windows-PowerShell/Operational. Se si abilita l'impostazione di questo criterio, Windows PowerShell registrerà l'elaborazione dei comandi, i blocchi di script, le funzioni e gli script, sia se richiamati in modo interattivo che tramite automazione. Se si disabilita l'impostazione di questo criterio, la registrazione dell'input di script di PowerShell verrà disabilitata. Se si abilita la registrazione delle chiamate di blocchi di script, PowerShell registrerà eventi anche all'avvio o all'interruzione di una chiamata di un comando, un blocco di script, una funzione o uno script. L'abilitazione della registrazione delle chiamate genera un volume elevato di registri eventi. Nota: l'impostazione di questo criterio è presente sia in Configurazione computer che in Configurazione utente nell'Editor Criteri di gruppo. L'impostazione dei criteri in Configurazione computer ha la precedenza sull'impostazione dei criteri in Configurazione utente.
  
  **Impostazione predefinita**: Abilitato
 
