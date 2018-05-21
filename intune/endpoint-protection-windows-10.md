---
title: Aggiungere Endpoint Protection su Windows 10 in Microsoft Intune - Azure | Documenti Microsoft
description: Nei dispositivi Windows 10 usare o configurare le impostazioni di Endpoint Protection per abilitare le funzionalità di Windows Defender, che includono Application Guard, Firewall, SmartScreen, crittografia e Bitlocker, Exploit Guard, Application Control, Centro sicurezza e protezione dei dispositivi locali in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 069f71d75c0a9c7cec083a929f89a2b39bb4aac5
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-intune"></a>Impostazioni di Endpoint Protection per Windows 10 e versioni successive in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Il profilo di Endpoint Protection consente di controllare le funzionalità di sicurezza nei dispositivi Windows 10, ad esempio BitLocker e Windows Defender.

Usare le informazioni di questo articolo per creare profili di Endpoint Protection. Per configurare Windows Defender Antivirus, vedere [Restrizione dei dispositivi per Windows 10](device-restrictions-windows-10.md#windows-defender-antivirus). 

> [!NOTE]
> Queste impostazioni non sono supportate nelle edizioni di Windows 10 Home e Professional.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Quando si usa Microsoft Edge, Windows Defender Application Guard protegge l'ambiente dai siti che non sono considerati attendibili dall'organizzazione. Quando gli utenti visitano siti non elencati nei limiti della rete isolata, tali siti vengono aperti in una sessione del browser virtuale in Hyper-V. I siti attendibili vengono definiti da un limite di rete, che può essere configurato in Configurazioni dei dispositivi. 

Application Guard è disponibile solo per i dispositivi Windows 10 a 64 bit. Quando si usa questo profilo viene installato un componente Win32 per attivare Application Guard.

- **Application Guard**: consente di aprire siti non approvati in un contenitore del browser virtuale di Hyper-V.
- **Comportamento degli Appunti**: consente di scegliere le azioni di copia/incolla consentite tra il computer locale e il browser virtuale di Application Guard.
- **Contenuto esterno nei siti aziendali**: consente di bloccare il caricamento del contenuto dei siti Web non approvati.
- **Stampa dal browser virtuale**: consente alle stampanti PDF, XPS, locali e/o di rete di stampare contenuto dal browser virtuale.
- **Raccogli registri**: consente di raccogliere i registri degli eventi che si verificano in una sessione del browser di Application Guard.
- **Conserva i dati del browser generati dall'utente**: salva i dati utente, ad esempio password, Preferiti e cookie, creati durante una sessione del browser virtuale di Application Guard.
- **Accelerazione grafica**: consente di caricare più rapidamente i siti Web con molti elementi grafici quando si lavora all'interno della sessione del browser virtuale di Application Guard. I siti si caricano più rapidamente quando si abilita l'accesso a un'unità di elaborazione grafica virtuale.
- **Scarica i file nel file system dell'host**: consente agli utenti di scaricare i file dal browser virtualizzato al sistema operativo host.

## <a name="windows-defender-firewall"></a>Windows Defender Firewall

### <a name="global-settings"></a>Impostazioni globali

Queste impostazioni sono applicabili a tutti i tipi di rete.

- **File Transfer Protocol**: consente di bloccare il protocollo FTP con stato.
- **Tempo di inattività delle associazioni di sicurezza prima dell'eliminazione**: le associazioni di sicurezza vengono eliminate dopo che per *n* secondi non è stato rilevato traffico.
- **Codifica delle chiavi precondivise**: consente di codificare le chiavi già condivise usando il formato UTF-8.
- **Esenzioni IPSec**: consente di configurare traffico specifico da esentare da IPSec, tra cui **Codici di tipo ICMP IPv6 per Neighbor Discover**, **ICMP**, **Codici di tipo ICMP IPv6 per Router Discover** e **Traffico DHCP IPv4 e IPv6**.
- **Verifica dell'elenco di revoche di certificati**: consente di impostare un valore per la modalità di applicazione della verifica dell'elenco di revoche di certificati, tra cui **Disabilita la verifica dell'elenco di revoche di certificati**, **Esito negativo della verifica dell'elenco di revoche di certificati solo in caso di certificato revocato** e **Esito negativo della verifica dell'elenco di revoche di certificati per ogni errore rilevato**.
- **Corrispondenza opportunistica del set di autenticazione per ogni modulo per le chiavi**: consente di impostare i moduli di impostazione chiavi in modo da ignorare l'intero set di autenticazione nel caso in cui non supportino tutte le famiglie di prodotti di autenticazione in tale set.
- **Accodamento di pacchetti**: consente di immettere la modalità di abilitazione del ridimensionamento del software sul lato ricezione per la ricezione di testo crittografato e l'inoltro di testo normale per lo scenario relativo a gateway con tunnel IPSec, assicurando il mantenimento dell'ordine dei pacchetti.

### <a name="network-settings"></a>Impostazioni di rete

Queste impostazioni sono applicabili a tipi di rete specifici, tra cui **Rete di dominio (aziendale)**, **Rete privata (individuabile)** e **Rete pubblica (non individuabile)**.

#### <a name="general-settings"></a>Impostazioni generali

- **Windows Defender Firewall**: abilitare questa impostazione per bloccare il traffico di rete.
- **Modalità mascheramento**: consente di bloccare il funzionamento del firewall in modalità mascheramento. Il blocco della modalità mascheramento consente di bloccare anche **Esenzione di pacchetti protetti da IPsec**.
- **Schermata**: l'abilitazione di questa impostazione e di quella relativa al firewall determina il blocco di tutto il traffico in ingresso.
- **Risposte unicast a broadcast multicast**: consente di bloccare le risposte unicast ai broadcast multicast. In genere, si preferisce non ricevere risposte unicast a messaggi trasmessi o multicast. Queste risposte possono indicare un attacco Denial of Service (DoS) o il tentativo da parte di un utente malintenzionato di rilevare la presenza di un computer attivo noto.
- **Notifiche in ingresso**: consente di impedire la visualizzazione delle notifiche agli utenti quando un'applicazione non è autorizzata all'ascolto su una porta.
- **Azione predefinita per le connessioni in ingresso**: consente di bloccare l'azione predefinita eseguita dal firewall sulle connessioni in ingresso.

#### <a name="rule-merging"></a>Unione delle regole

- **Regole di Windows Defender Firewall per le applicazioni autorizzate dall'archivio locale**: consente di applicare le regole autorizzate del firewall nell'archivio locale per il riconoscimento e l'applicazione.
- **Regole di Windows Defender Firewall per porte globali dall'archivio locale**: consente di applicare le regole del firewall per le porte globali nell'archivio locale per il riconoscimento e l'applicazione.
- **Regole di Windows Defender Firewall dall'archivio locale**: consente di applicare le regole globali del firewall nell'archivio locale per il riconoscimento e l'applicazione.
- **Regole IPSec dall'archivio locale**: consente di applicare le regole di sicurezza della connessione dall'archivio locale, indipendentemente dallo schema o dalle versioni delle regole di sicurezza della connessione.

## <a name="windows-defender-smartscreen-settings"></a>Impostazioni di Windows Defender SmartScreen

- **SmartScreen per app e file**: consente di abilitare Windows SmartScreen per l'esecuzione di file e per le app in esecuzione.
- **Esecuzione di file non verificati**: consente di impedire all'utente finale di eseguire file non verificati da Windows SmartScreen.

## <a name="windows-encryption"></a>Crittografia di Windows

### <a name="windows-settings"></a>Impostazioni Windows

Le due impostazioni seguenti si applicano a tutte le versioni di Windows 10:

- **Crittografa i dispositivi**: se abilitata, agli utenti viene chiesto di abilitare la crittografia del dispositivo. e di confermare che non è abilitata la crittografia di alcun altro provider. Se la crittografia di Windows è attivata mentre è attivo un altro metodo di crittografia, il dispositivo potrebbe diventare instabile.
- **Crittografa la scheda di memoria**: abilitare questa impostazione per crittografare le eventuali schede di memoria rimovibili usate dal dispositivo.


### <a name="bitlocker-base-settings"></a>Impostazioni di base di BitLocker

Le impostazioni di base sono impostazioni BitLocker universali per tutti i tipi di unità dati. Le impostazioni di Criteri di gruppo BitLocker gestiscono le attività di crittografia delle unità o le opzioni di configurazione che gli utenti finali possono modificare in tutti i tipi di unità dati.

- **Avviso per la crittografia dischi di altro tipo**: disabilita la richiesta di avviso per la crittografia dischi di altro tipo nei computer degli utenti finali.
- **Configura i metodi di crittografia**: abilitare questa impostazione per configurare gli algoritmi di crittografia per il sistema operativo, i dati e le unità rimovibili.
  - **Crittografia per le unità del sistema operativo**: scegliere il metodo di crittografia per le unità del sistema operativo. È consigliabile usare l'algoritmo XTS-AES.
  - **Crittografia per unità dati fisse**: scegliere il metodo di crittografia per le unità dati fisse (predefinite). È consigliabile usare l'algoritmo XTS-AES.
  - **Crittografia per unità dati rimovibili**: scegliere il metodo di crittografia per le unità dati rimovibili (predefinite). Se l'unità rimovibile viene usata con dispositivi che non eseguono Windows 10, è consigliabile usare l'algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Impostazioni delle unità del sistema operativo di BitLocker

Queste impostazioni si applicano in modo specifico alle unità dati del sistema operativo.

- **Autenticazione aggiuntiva all'avvio**: consente di configurare i requisiti di autenticazione per l'avvio dei computer, incluso l'uso di Trusted Platform Module (TPM).
  - **BitLocker con chip TPM non compatibile**
  - **Avvio TPM compatibile**: scegliere di consentire, non consentire o rendere obbligatorio il chip TPM.
  - **PIN di avvio TPM compatibile**: scegliere di consentire, non consentire o rendere obbligatorio l'uso di un PIN di avvio con il chip TPM.
  - **Chiave di avvio TPM compatibile**: scegliere di consentire, non consentire o rendere obbligatorio l'uso di una chiave di avvio con il chip TPM.
  - **Chiave di avvio e PIN TPM compatibile**: scegliere di consentire, non consentire o rendere obbligatorio l'uso di una chiave di avvio e di un PIN con il chip TPM.
- **Lunghezza minima del PIN**: abilitare questa impostazione per configurare la lunghezza minima del PIN di avvio del chip TPM.
  - **Numero minimo di caratteri**: immettere il numero di caratteri obbligatorio per il PIN di avvio, **4**-**20**.
- **Ripristino delle unità del sistema operativo**: abilitare questa impostazione per controllare la modalità di ripristino delle unità del sistema operativo protette da BitLocker se le informazioni necessarie all'avvio non sono disponibili.
  - **Agente di recupero dati basato su certificati**: abilitare questa impostazione se si vuole che sia possibile usare gli agenti di recupero dati con unità del sistema operativo protette da BitLocker.
  - **Creazione della password di ripristino da parte dell'utente**: scegliere se per gli utenti è consentito, obbligatorio o non consentito generare una password di ripristino di 48 cifre.
  - **Creazione della chiave di ripristino da parte dell'utente**: scegliere se per gli utenti è consentito, obbligatorio o non consentito generare una chiave di ripristino a 256 bit.
  - **Opzioni di ripristino nell'installazione guidata di BitLocker**: abilitare questa impostazione per impedire agli utenti di visualizzare o modificare le opzioni di ripristino se BitLocker è attivato.
  - **Salva le informazioni di ripristino di BitLocker in AD DS**: consente l'archiviazione delle informazioni di ripristino di BitLocker in Active Directory.
  - **Informazioni di ripristino di BitLocker archiviate in AD DS**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Active Directory. Scegliere tra:
    - **Backup delle password di ripristino e dei pacchetti di chiavi**
    - **Backup solo delle password di ripristino**
  - **Archivia le informazioni di ripristino in AD DS prima di abilitare BitLocker**: abilitare questa impostazione per consentire agli utenti di attivare BitLocker solo se il dispositivo è stato aggiunto al dominio e le informazioni di ripristino di BitLocker sono state archiviate in Active Directory.
- **URL e messaggio di ripristino prima dell'avvio**: abilitare questa impostazione per configurare il messaggio e l'URL visualizzati nella schermata di recupero della chiave prima dell'avvio.
  - **Messaggio di ripristino prima dell'avvio**: consente di configurare la modalità di visualizzazione del messaggio di ripristino. Scegliere tra:
    - **Usa URL e messaggio di ripristino predefiniti**
    - **Usa un messaggio di ripristino e un URL vuoti**
    - **Usa messaggio di ripristino personalizzato**
    - **Usa URL di ripristino personalizzato**

### <a name="bitlocker-fixed-data-drive-settings"></a>Impostazioni delle unità dati fisse BitLocker

- **Accesso in scrittura alle unità dati fisse non protette da BitLocker**: se questa impostazione è abilitata, è necessario abilitare la protezione BitLocker per tutte le unità dati fisse o predefinite perché sia possibile scrivere all'interno di esse.
- **Ripristino delle unità fisse**: abilitare questa impostazione per controllare la modalità di ripristino delle unità fisse protette da BitLocker se le informazioni necessarie all'avvio non sono disponibili.
  - **Agente di recupero dati**: abilitare questa impostazione se si vogliono usare gli agenti di recupero dati con unità fisse protette da BitLocker.
  - **Creazione della password di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una password di ripristino di 48 cifre.  
  - **Creazione della chiave di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una chiave di ripristino a 256 bit.
  - **Opzioni di ripristino nell'installazione guidata di BitLocker**: abilitare questa impostazione per impedire agli utenti di visualizzare o modificare le opzioni di ripristino se BitLocker è attivato.
  - **Salva le informazioni di ripristino di BitLocker in AD DS**: consente l'archiviazione delle informazioni di ripristino di BitLocker in Active Directory.
  - **Informazioni di ripristino di BitLocker in AD DS**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Active Directory. Scegliere tra:
    - **Backup delle password di ripristino e dei pacchetti di chiavi**
    - **Backup solo delle password di ripristino**
  - **Archivia le informazioni di ripristino in AD DS prima di abilitare BitLocker**: abilitare questa impostazione per consentire agli utenti di attivare BitLocker solo se il dispositivo è stato aggiunto al dominio e le informazioni di ripristino di BitLocker sono state archiviate in Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Impostazioni delle unità dati rimovibili BitLocker

- **Accesso in scrittura alle unità dati rimovibili non protette da BitLocker**: consente di specificare se la crittografia BitLocker è obbligatoria per le unità di archiviazione rimovibili.
  - **Accesso in scrittura ai dispositivi configurati in un'altra organizzazione**: consente di specificare se è possibile scrivere nelle unità dati rimovibili che appartengono a un'altra organizzazione.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Usare [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) per gestire e ridurre la superficie di attacco delle app usate dai dipendenti.

### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco

- **Contrassegna il furto di credenziali dal sottosistema dell'autorità di protezione locale Windows**

[Evitare azioni e app](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) che generalmente vengono usate dal malware per infettare i computer.

#### <a name="rules-to-prevent-office-macro-threats"></a>Regole per impedire le minacce relative alle macro di Office

Impedire alle app di Office di eseguire le azioni seguenti:

- **Inserimento delle app di Office in altri processi (nessuna eccezione)**
- **Creazione di contenuto eseguibile in app/macro di Office**
- **Avvio di processi figlio per le app di Office**
- **Importazioni Win32 da codice delle macro in Office**

#### <a name="rules-to-prevent-script-threats"></a>Regole per impedire le minacce relative agli script

Bloccare i seguenti elementi per contrastare le minacce basate su script:

- **Codice js/vbs/ps/macro offuscato**
- **Esecuzione in js/vbs di payload scaricato da Internet (nessuna eccezione)**
- **Creazione di processi da comandi PSExec e WMI**
- **Processi non attendibili e non firmati eseguiti da USB**
- **File eseguibili che non rispettano criteri di prevalenza, di validità o dell'elenco di elementi attendibili**

#### <a name="rules-to-prevent-email-threats"></a>Regole per impedire le minacce tramite posta elettronica

Bloccare gli elementi seguenti per contrastare le minacce tramite posta elettronica:

- **Esecuzione del contenuto eseguibile (file con estensione exe, dll, ps, js, vbs e così via) non elaborato dalla posta elettronica (webmail/mail client) (nessuna eccezione)**

#### <a name="rules-to-protect-against-ransomware"></a>Regole per proteggersi dal ransomware
- **Protezione ransomware avanzata**

> [!TIP]
> [Ridurre le superfici di attacco con Windows Defender Exploit Guard](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) offre più dettagli su queste regole.

#### <a name="attack-surface-reduction-exceptions"></a>Eccezioni della riduzione della superficie di attacco

- **File e cartelle da escludere dalle regole di riduzione della superficie di attacco**: importare/aggiungere un elenco di percorsi da escludere dalle regole configurate.

### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

È possibile proteggere i dati importanti da app e minacce dannose, ad esempio il ransomware.

- **Protezione delle cartelle**: consente di proteggere file e cartelle dalle modifiche indesiderate di app dannose. È possibile importare un **elenco di app con accesso alle cartelle protette** o aggiungerle manualmente. È anche possibile aggiungere un **elenco di cartelle aggiuntive da proteggere** con un'operazione di caricamento o aggiungendole manualmente.

### <a name="network-filtering"></a>Filtri di rete

È possibile bloccare le connessioni in uscita da qualsiasi app verso indirizzi IP/domini con reputazione negativa.

### <a name="exploit-protection"></a>Protezione dagli exploit

Bloccare la **modifica dell'interfaccia di protezione dagli exploit da parte degli utenti** caricando un file XML che consente di configurare limitazioni di memoria, flusso di controllo e criteri. Le impostazioni nel file XML possono essere usate per proteggere un'applicazione dagli exploit.

Per abilitare la protezione dagli exploit creare un file XML che rappresenta le impostazioni di mitigazione scelte per il sistema e le applicazioni. A questo scopo, è possibile usare uno dei due metodi seguenti:

 1. PowerShell: usare uno o più cmdlet Get-ProcessMitigation, Set-ProcessMitigation e ConvertTo-ProcessMitigationPolicy di PowerShell. I cmdlet configurano le impostazioni di mitigazione ed esportano la relativa rappresentazione XML.

 2. Interfaccia utente di Windows Defender Security Center: in Windows Defender Security Center fare clic su Controllo app e browser e quindi scorrere fino alla parte inferiore della schermata visualizzata per trovare Protezione dagli exploit. Usare prima di tutto le schede Impostazioni di sistema e Impostazioni programmi per configurare le impostazioni di mitigazione. Trovare quindi il collegamento Esporta impostazioni nella parte inferiore della schermata per esportare la relativa rappresentazione XML.

## <a name="windows-defender-application-control"></a>Controllo di applicazioni di Windows Defender

Usare i **criteri relativi all'integrità del codice di controllo dell'applicazione** per scegliere altre app che devono essere controllate o possono essere ritenute attendibili per l'esecuzione da parte del Controllo di applicazioni di Windows Defender. I componenti Windows e tutte le app di Windows Store sono ritenuti automaticamente attendibili per l'esecuzione.

In modalità **Solo controllo** le applicazioni non vengono bloccate. La modalità **Solo controllo** registra tutti gli eventi nei log del client locali.

Una volta abilitato, il controllo delle applicazioni può essere disabilitato solo passando dalla modalità **Imponi** alla modalità **Solo controllo**. Il passaggio dalla modalità **Imponi** alla modalità **Non configurato** fa sì che il controllo delle applicazioni continui a essere applicato nei dispositivi assegnati.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard
Windows Defender Credential Guard protegge contro attacchi relativi al furto di credenziali. Isola i segreti in modo che possa accedervi solo il software di sistema con privilegi.

Le impostazioni **Credential Guard** includono:

- **Disabilitato**: disattiva Credential Guard in modalità remota, se attivato precedentemente con l'opzione **Abilita senza blocco UEFI**.
- **Abilita con blocco UEFI**: garantisce che Credential Guard non possa essere disabilitato in modalità remota usando una chiave del Registro di sistema o Criteri di gruppo.

    > [!NOTE]
    > Se si usa questa impostazione e in seguito si vuole disabilitare Credential Guard, è necessario impostare Criteri di gruppo su **Disabilitato**. e cancellare fisicamente le informazioni di configurazione UEFI da ogni computer. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

- **Abilita senza blocco UEFI**: consente di rimuovere Credential Guard in modalità remota usando Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 versione 1511 e successive.

Quando si abilita Credential Guard, vengono abilitate anche le funzionalità obbligatorie seguenti:

- **Sicurezza basata sulla virtualizzazione**: viene attivata durante il riavvio successivo. La sicurezza basata sulla virtualizzazione usa Windows Hypervisor per offrire il supporto per i servizi di sicurezza.
- **Avvio protetto con Direct Memory Access**: attiva la sicurezza basata sulla virtualizzazione con Avvio protetto e le protezioni di Direct Memory Access (DMA). Le protezioni DMA richiedono supporto hardware e vengono abilitate solo nei dispositivi configurati correttamente.

## <a name="windows-defender-security-center"></a>Windows Defender Security Center

L'app Windows Defender Security Center funziona come un'app o un processo separato da ognuna delle singole funzionalità. Visualizza le notifiche tramite il centro notifiche. Funge da agente di raccolta o unica posizione per visualizzare lo stato ed eseguire alcune attività di configurazione per ogni funzionalità. Per altre informazioni, vedere la documentazione di [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>App e notifiche di Windows Defender Security Center

È possibile bloccare l'accesso degli utenti finali alle diverse aree dell'app Windows Defender Security Center. Se si nasconde una sezione, verranno bloccate anche le notifiche correlate.

- **Protezione da virus e minacce**
- **Prestazioni e integrità del dispositivo**
- **Protezione firewall e della rete**
- **Controllo delle app e del browser**
- **Opzioni famiglia**
- **Notifiche dalle aree visualizzate dell'app**: consente di scegliere le notifiche da visualizzare agli utenti finali. Le notifiche non critiche includono riepiloghi dell'attività di Windows Defender Antivirus, comprese le notifiche relative al completamento delle analisi. Tutte le altre notifiche sono considerate critiche.

#### <a name="it-contact-information"></a>Informazioni di contatto del reparto IT

Specificare le informazioni di contatto del reparto IT da visualizzare nell'app Windows Defender Security Center e nelle relative notifiche. È possibile scegliere **Visualizza nell'app e nelle notifiche**, **Visualizza solo nell'app**, **Visualizza solo nelle notifiche** o **Non visualizzare**. È necessario immettere il **nome dell'organizzazione IT** e almeno una delle opzioni di contatto seguenti:

- **Numero di telefono del reparto IT o ID Skype**
- **Indirizzo di posta elettronica del reparto IT**
- **URL del sito Web del supporto tecnico IT**

## <a name="local-device-security-options"></a>Opzioni di sicurezza dei dispositivi locali

Usare queste opzioni per configurare le impostazioni di sicurezza locali nei dispositivi Windows 10.

### <a name="accounts"></a>Account

- **Aggiungi nuovi account Microsoft**: impedisce l'aggiunta di nuovi account Microsoft nel computer.
- **Accesso remoto senza password**: consente agli account locali non protetti da password di accedere da posizioni diverse dal dispositivo fisico.

#### <a name="admin"></a>Amministratore

- **Account amministratore locale**: determina se l'account amministratore locale è abilitato o disabilitato.
- **Rinomina l'account amministratore**: definisce un nome account diverso da associare all'ID di sicurezza (SID) per l'account amministratore.

#### <a name="guest"></a>Guest

- **Account Guest**: determina se l'account Guest è abilitato o disabilitato.
- **Rinomina l'account Guest**: definisce un nome account diverso da associare all'ID di sicurezza (SID) per l'account Guest.

### <a name="devices"></a>Dispositivi

- **Disancora il dispositivo senza accesso**: impedisce di disancorare un computer portatile senza dover eseguire l'accesso.
- **Installa i driver della stampante per le stampanti condivise**: limita ai soli amministratori l'installazione dei driver della stampante durante la connessione a una stampante condivisa.
- **Limita l'accesso al CD-ROM solo all'utente attivo locale**: se si abilita questa impostazione, si consente solo agli utenti che hanno eseguito l'accesso in modo interattivo di accedere ai supporti CD-ROM
- **Formatta e rimuovi supporti rimovibili**: consente di determinare chi è autorizzato a formattare e rimuovere i supporti rimovibili NTFS:
  - **Non configurato**
  - **Amministratori e utenti esperti**
  - **Amministratori e utenti interattivi**

### <a name="interactive-logon"></a>Accesso interattivo

- **Minuti di inattività della schermata di blocco prima dell'attivazione dello screen saver**: consente di definire il numero massimo di minuti di inattività nella schermata di accesso del desktop interattivo prima dell'attivazione dello screen saver.
- **Richiedi CTRL+ALT+CANC per accedere**: consente di richiedere la selezione di CTRL+ALT+CANC prima che un utente possa eseguire l'accesso.
- **Comportamento in caso di rimozione della smart card**: determina le azioni che vengono eseguite quando la smart card per un utente connesso viene rimossa dal lettore di smart card.
Per informazioni più dettagliate, vedere [LocalPoliciesSecurity options](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) (Opzioni di LocalPoliciesSecurity).

#### <a name="display"></a>Schermo

- **Informazioni utente nella schermata di blocco**: Consente di configurare le informazioni utente visualizzate quando la sessione è bloccata. Se questa opzione non viene configurata, vengono mostrati il nome visualizzato dell'utente, il dominio e il nome utente.
  - **Solo nome visualizzato dell'utente**
  - **Non visualizzare le informazioni utente**
  - **Non configurato**: nome visualizzato dell'utente, dominio e nome utente
- **Nascondi l'ultimo utente connesso**: consente di non visualizzare il nome utente dell'ultima persona che ha eseguito l'accesso a questo dispositivo.
- **Nascondi il nome utente all'accesso**: consente di non visualizzare il nome utente della persona che accede a questo dispositivo dopo l'immissione di credenziali e prima della visualizzazione del desktop del dispositivo.
- **Titolo del messaggio di accesso**: impostare il titolo del messaggio per gli utenti che tentano l'accesso.
- **Testo del messaggio di accesso**: impostare il testo del messaggio per gli utenti che tentano l'accesso.

### <a name="network-access-and-security"></a>Accesso alla rete e sicurezza

- **Accesso anonimo alle named pipe e alle condivisioni**: limita l'accesso anonimo alle impostazioni per condivisioni e named pipe. Si applica alle impostazioni a cui è possibile accedere anonimamente.
- **Enumerazione anonima degli account SAM**: consente agli utenti anonimi di enumerare gli account SAM. Windows consente agli utenti anonimi di enumerare i nomi degli account di dominio e delle condivisioni di rete.
- **Enumerazione anonima di account e condivisioni SAM**: consente di bloccare l'enumerazione anonima degli account e delle condivisioni SAM. Windows consente agli utenti anonimi di enumerare i nomi degli account di dominio e delle condivisioni di rete.
- **Valore hash di LAN Manager archiviato alla modifica della password**: alla successiva modifica della password, scegliere se archiviare il valore hash di LAN Manager (LM) per la nuova password. Non viene archiviato per impostazione predefinita.
- **Richieste di autenticazione PKU2U**: consente di impedire alle richieste di autenticazione PKU2U per questo dispositivo di usare le identità online.
- **Limita le connessioni RPC remote a SAM**: modificare la stringa SDDL (Security Descriptor Definition Language) per consentire o impedire a utenti e gruppi di effettuare chiamate remote a SAM.
- **Descrittore di sicurezza**

### <a name="recovery-console-and-shutdown"></a>Console di ripristino di emergenza e arresto

- **Cancella il file di paging della memoria virtuale all'arresto**: consente di cancellare il file di paging della memoria virtuale quando il dispositivo viene spento.
- **Arresta senza accesso**: Consente di bloccare l'opzione per l'arresto del computer dalla schermata di accesso di Windows. In questo caso gli utenti devono poter accedere correttamente al computer prima di eseguire l'arresto del sistema.

### <a name="user-account-control"></a>Controllo dell'account utente

- **Integrità UIA senza posizione sicura**: consente l'esecuzione delle app da posizioni non sicure nel file system con livello di integrità UIAccess.
- **Virtualizza gli errori di scrittura nel file e nel Registro di sistema in percorsi specifici per ogni utente**: determina se gli errori di scrittura delle app devono essere reindirizzati su percorsi definiti sia nel Registro di sistema che nel file system. In caso contrario, provocano l'errore dell'app.
- **Esegui con privilegi elevati solo i file eseguibili firmati e convalidati**: impone la convalida del percorso di certificazione PKI di un determinato file eseguibile prima che ne sia consentita l'esecuzione.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Impostazioni del comportamento della richiesta di elevazione dei privilegi UIA

- **Richiesta di elevazione dei privilegi per amministratori**: definisce il comportamento della richiesta di elevazione dei privilegi per gli amministratori in modalità Approvazione amministratore:
  - **Esegui con privilegi elevati senza chiedere conferma**
  - **Richiedi credenziali sul desktop sicuro**
  - **Richiedi consenso sul desktop sicuro**
  - **Richiedi credenziali**
  - **Richiedi consenso**
  - **Non configurato**: richiede il consenso per file binari non Windows
- **Richiesta di elevazione dei privilegi per utenti standard**: definisce il comportamento della richiesta di elevazione dei privilegi per gli utenti standard:
  - **Nega automaticamente richieste di elevazione**
  - **Richiedi credenziali sul desktop sicuro**
  - **Non configurato**: richiesta di credenziali
- **Indirizza le richieste di elevazione dei privilegi al desktop interattivo dell'utente**: Consente a tutte le richieste di elevazione dei privilegi di passare al desktop interattivo dell'utente invece che a desktop protetto. Per gli amministratori e gli utenti standard vengono usate le impostazioni dei criteri di comportamento della richiesta.
- **Prompt con privilegi elevati per installazioni di app**: le installazioni di app che necessitano di privilegi elevati richiederanno le credenziali di amministratore.
- **Richiesta di elevazione dei privilegi UIA senza desktop protetto**: consente alle app con accesso all'interfaccia utente di richiedere l'elevazione senza usare il desktop sicuro.

#### <a name="admin-approval-mode-settings"></a>Impostazioni della modalità Approvazione amministratore

- **Modalità Approvazione amministratore per l'amministratore predefinito**: definisce se l'account amministratore predefinito usa la modalità Approvazione amministratore o esegue tutte le app con privilegi di amministratore completi.
- **Esegui tutti gli amministratori in modalità Approvazione amministratore**: consente di definire se la modalità Approvazione amministratore e tutte le impostazioni dei criteri UAC sono abilitate.

### <a name="microsoft-network-client"></a>Client di rete Microsoft

- **Firma digitalmente le comunicazioni (se il server lo consente)**: determina se il client SMB può provare a negoziare la firma dei pacchetti SMB. Se abilitato (impostazione predefinita), il client di rete Microsoft richiede al server di eseguire la firma dei pacchetti SMB durante la configurazione della sessione. Se la firma dei pacchetti è stata abilitata sul server, la firma dei pacchetti sarà negoziata. Se questo criterio è disabilitato, il client SMB non negozierà mai la firma dei pacchetti SMB.
- **Invia password non crittografate a server SMB di terze parti**: se abilitato, il redirector SMB (Server Message Block) è autorizzato a inviare password in testo non crittografato a server SMB non Microsoft che non supportano la crittografia della password durante l'autenticazione.

### <a name="microsoft-network-server"></a>Server di rete Microsoft

- **Firma digitalmente le comunicazioni (se il client lo consente)**: determina se il server SMB negozierà la firma dei pacchetti SMB con i client che la richiedono. Se abilitato, il server di rete Microsoft negozierà la firma dei pacchetti SMB in base a quanto richiesto dal client, ovvero se la firma dei pacchetti è abilitata sul client, la firma dei pacchetti sarà negoziata. Se disabilitato (impostazione predefinita), il client SMB non negozierà mai la firma dei pacchetti SMB.
- **Firma digitalmente le comunicazioni (sempre)**: determina se la firma dei pacchetti è richiesta dal componente server SMB. Se abilitato, il server di rete Microsoft comunica con un client di rete Microsoft solo se tale client accetta l'esecuzione della firma dei pacchetti SMB. Se disabilitato (impostazione predefinita), la firma dei pacchetti SMB viene negoziata tra il client e il server.

## <a name="next-steps"></a>Passaggi successivi

Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
