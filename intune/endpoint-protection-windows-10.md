---
title: Impostazioni di protezione per dispositivi Windows 10 in Microsoft Intune - Azure | Microsoft Docs
description: Nei dispositivi Windows 10 usare o configurare le impostazioni di Endpoint Protection per abilitare le funzionalità di Windows Defender, che includono Application Guard, Firewall, SmartScreen, crittografia e Bitlocker, Exploit Guard, Application Control, Centro sicurezza e protezione dei dispositivi locali in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/23/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f87c2fa5fcb7e76fa8d398018e87ec0b15c05e9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843392"
---
# <a name="windows-10-and-later-settings-to-protect-devices-using-intune"></a>Impostazioni di Windows 10 (e versioni successive) per la protezione dei dispositivi con Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune include diverse impostazioni utili per la protezione dei dispositivi. Questo articolo descrive tutte le impostazioni che è possibile abilitare e configurare nei dispositivi Windows 10 e versioni successive. Queste impostazioni vengono create in un profilo di configurazione di Endpoint Protection in Intune per controllare la sicurezza, inclusi BitLocker e Windows Defender.

Per configurare Windows Defender Antivirus, vedere [Impostazioni dei dispositivi Windows 10 (e versioni successive) per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-windows-10.md#windows-defender-antivirus).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione dispositivi di Endpoint Protection](endpoint-protection-configure.md).

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Supportato nelle edizioni di Windows 10 seguenti:

- Enterprise
- Professional

Quando si usa Microsoft Edge, Windows Defender Application Guard protegge l'ambiente dai siti che non sono considerati attendibili dall'organizzazione. Quando gli utenti visitano siti non elencati nei limiti della rete isolata, tali siti vengono aperti in una sessione del browser virtuale di Hyper-V. I siti attendibili vengono definiti da un limite di rete, configurato in Configurazione del dispositivo.

Application Guard è disponibile solo per i dispositivi Windows 10 a 64 bit. Quando si usa questo profilo viene installato un componente Win32 per attivare Application Guard.

- **Application Guard**: **Abilita** attiva questa funzionalità, che consente di aprire siti non approvati in un contenitore del browser virtuale di Hyper-V. L'impostazione **Non configurata** (predefinita) indica che qualsiasi sito (approvato e non approvato) viene aperto nel dispositivo.
- **Comportamento degli Appunti**: consente di scegliere le azioni di copia/incolla consentite tra il computer locale e il browser virtuale di Application Guard.
- **Contenuto esterno nei siti aziendali**: **Blocca** impedisce il caricamento del contenuto dai siti Web non approvati. L'impostazione **Non configurata** (predefinita) indica che i siti non aziendali possono essere aperti nel dispositivo.
- **Stampa dal browser virtuale**: scegliere **Consenti** per consentire alle stampanti PDF, XPS, locali e/o di rete di stampare contenuto dal browser virtuale. L'impostazione **Non configurata** (predefinita) disabilita tutte le funzionalità di stampa.
- **Raccogli i log**: scegliere **Consenti** per raccogliere i log degli eventi che si verificano in una sessione del browser di Application Guard. L'impostazione **Non configurata** (predefinita) non raccoglie alcun log all'interno della sessione del browser.
- **Conserva i dati del browser generati dall'utente**: **Consenti** salva i dati utente, ad esempio password, Preferiti e cookie, creati durante una sessione del browser virtuale di Application Guard. L'impostazione **Non configurata** (predefinita) elimina i file e i dati scaricati dall'utente al riavvio del dispositivo o quando un utente si disconnette.
- **Accelerazione grafica**: scegliere **Abilita** per caricare i siti Web con utilizzo intensivo di grafica e i video più velocemente ottenendo l'accesso a un'unità di elaborazione grafica virtuale. L'impostazione **Non configurata** (predefinita) usa la CPU del dispositivo per la grafica. Non usa l'unità di elaborazione grafica virtuale.
- **Scarica i file nel file system dell'host**: **Abilita** consente agli utenti di scaricare i file dal browser virtualizzato nel sistema operativo host. L'impostazione **Non configurata** (predefinita) consente di mantenere i file locali nel dispositivo e non scaricare i file nel file system host.

## <a name="windows-defender-firewall"></a>Windows Defender Firewall

Supportato nelle edizioni di Windows 10 seguenti:
- Home
- Professional
- Business
- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise

### <a name="global-settings"></a>Impostazioni globali

Queste impostazioni sono applicabili a tutti i tipi di rete.

- **File Transfer Protocol**: **Blocca** disabilita il protocollo FTP con stato. Con l'impostazione **Non configurata** (predefinita), il firewall applica filtri FTP con stato per consentire connessioni secondarie.
- **Tempo di inattività delle associazioni di sicurezza prima dell'eliminazione**: le associazioni di sicurezza vengono eliminate dopo che per *n* secondi non è stato rilevato traffico di rete. Immettere un tempo di inattività in secondi.
- **Codifica delle chiavi precondivise**: scegliere **Abilita** per usare la codifica delle chiavi precondivise con UTF-8. L'impostazione **Non configurata** (predefinita) usa il valore dell'archivio locale.
- **Esenzioni da IPsec**: configura il traffico specifico da esentare dall'esecuzione di IPsec, tra cui:
  - **Codici di tipo ICMP IPv6 per Neighbor Discover**
  - **ICMP**
  - **Codici di tipo ICMP IPv6 per Router Discover**
  - **Traffico DHCP IPv4 e IPv6**
- **Verifica dell'elenco di revoche di certificati**: consente di scegliere il modo in cui il dispositivo verifica l'elenco di revoche di certificati. Le opzioni includono **Disabilita la verifica dell'elenco di revoche di certificati**, **Esito negativo della verifica dell'elenco di revoche di certificati solo in caso di certificato revocato** e **Esito negativo della verifica dell'elenco di revoche di certificati per ogni errore rilevato**.
- **Corrispondenza opportunistica del set di autenticazione per ogni modulo per le chiavi**: scegliere **Abilita** in modo che i moduli per le chiavi DEBBANO ignorare solo le famiglie di prodotti di autenticazione non supportate. Con l'impostazione **Non configurata**, i moduli per le chiavi DEVONO ignorare l'intera famiglia di prodotti di autenticazione se non supportano tutte le famiglie di prodotti di autenticazione specificate nel set.
- **Accodamento di pacchetti**: immettere la modalità di abilitazione del ridimensionamento del software sul lato ricezione per la ricezione di testo crittografato e l'inoltro di testo normale per lo scenario relativo a gateway con tunnel IPSec, assicurando il mantenimento dell'ordine dei pacchetti.

### <a name="network-settings"></a>Impostazioni di rete

Queste impostazioni sono applicabili a tipi di rete specifici, tra cui **Rete di dominio (aziendale)**, **Rete privata (individuabile)** e **Rete pubblica (non individuabile)**.

#### <a name="general-settings"></a>Impostazioni generali

- **Windows Defender Firewall**: scegliere **Abilita** per attivare il firewall e la sicurezza avanzata. L'impostazione **Non configurata** (predefinita) consente tutto il traffico di rete, indipendentemente dalle eventuali altre impostazioni dei criteri.
- **Modalità mascheramento**: scegliere **Blocca** per impedire il funzionamento del firewall in modalità mascheramento. Il blocco della modalità mascheramento consente di bloccare anche **Esenzione di pacchetti protetti da IPsec**. L'impostazione **Non configurata** (predefinita) consente il funzionamento del firewall in modalità mascheramento, utile per evitare le risposte alle richieste di probe.
- **Schermata**: scegliere **Blocca** per disattivare questa funzionalità. L'impostazione **Non configurata** (predefinita) abilita questa impostazione. Quando questa impostazione e Windows Defender Firewall sono attivati, tutto il traffico in ingresso viene bloccato, indipendentemente dalle eventuali altre impostazioni dei criteri.
- **Risposte unicast a broadcast multicast**: con l'impostazione **Blocca** vengono disabilitate le risposte unicast ai broadcast multicast. In genere, si preferisce non ricevere risposte unicast a messaggi trasmessi o multicast. Queste risposte possono indicare un attacco Denial of Service (DoS) o il tentativo da parte di un utente malintenzionato di rilevare la presenza di un computer attivo noto. L'impostazione **Non configurata** (predefinita) abilita questa impostazione.
- **Notifiche in ingresso**: con l'impostazione **Blocca** vengono nascoste le notifiche agli utenti quando un'app non è autorizzata all'ascolto su una porta. L'impostazione **Non configurata** (predefinita) abilita questa impostazione e potrebbe visualizzare una notifica agli utenti quando un'app non è autorizzata all'ascolto su una porta.
- **Azione predefinita per le connessioni in ingresso**: con l'impostazione **Blocca**, l'azione del firewall predefinita non viene eseguita sulle connessioni in ingresso. Con l'impostazione **Non configurata** (predefinita), l'azione del firewall predefinita viene eseguita sulle connessioni in ingresso.

#### <a name="rule-merging"></a>Unione delle regole

- **Regole di Windows Defender Firewall per le applicazioni autorizzate dall'archivio locale**: scegliere **Abilita** per applicare le regole del firewall nell'archivio locale in modo che vengano riconosciute e applicate. Con l'impostazione **Non configurata** (predefinita), le regole del firewall per le applicazioni autorizzate nell'archivio locale vengono ignorate e non applicate.
- **Regole di Windows Defender Firewall per porte globali dall'archivio locale**: scegliere **Abilita** per applicare le regole del firewall per le porte globali nell'archivio locale in modo che vengano riconosciute e applicate. Con l'impostazione **Non configurata** (predefinita), le regole del firewall per le porte globali nell'archivio locale vengono ignorate e non applicate.
- **Regole di Windows Defender Firewall dall'archivio locale**: scegliere **Abilita** per applicare le regole del firewall nell'archivio locale per il riconoscimento e l'applicazione. Con l'impostazione **Non configurata** (predefinita), le regole del firewall dall'archivio locale vengono ignorate e non applicate.
- **Regole IPsec dall'archivio locale**: scegliere **Abilita** per applicare le regole di sicurezza della connessione dall'archivio locale, indipendentemente dalla versione dello schema o dalla versione delle regole di sicurezza della connessione. Con l'impostazione **Non configurata** (predefinita), le regole di sicurezza della connessione dall'archivio locale vengono ignorate e non applicate, indipendentemente dalla versione dello schema o dalle versione delle regole di sicurezza della connessione.

## <a name="windows-defender-smartscreen-settings"></a>Impostazioni di Windows Defender SmartScreen

Supportato nelle edizioni di Windows 10 seguenti con Microsoft Edge installato:
- Home
- Professional
- Business
- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise

**Impostazioni**:

- **SmartScreen per app e file**: **Abilita** consente di abilitare Windows SmartScreen per l'esecuzione di file e di app. SmartScreen è un componente anti-phishing e anti-malware basato sul cloud. L'impostazione **Non configurata** (predefinita) disabilita SmartScreen.
- **Esecuzione di file non verificati**: scegliere **Blocca** per impedire agli utenti finali di eseguire file non verificati da Windows SmartScreen. L'impostazione **Non configurata** (predefinita) disabilita questa funzionalità e consente agli utenti finali di eseguire i file che non sono stati verificati.

## <a name="windows-encryption"></a>Crittografia di Windows

### <a name="windows-settings"></a>Impostazioni Windows

Supportato nelle edizioni di Windows 10 seguenti:

- Professional
- Business
- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise

**Impostazioni**:

- **Crittografa i dispositivi**: scegliere **Rendi obbligatorio** per richiedere agli utenti di abilitare la crittografia del dispositivo. A seconda dell'edizione di Windows e della configurazione di sistema, è possibile che venga richiesto agli utenti:  
  - Di confermare che non è abilitata la crittografia di un altro fornitore
  - Di disattivare Crittografia unità Bitlocker e quindi di riattivare Bitlocker
    
    Se la crittografia di Windows è attivata mentre è attivo un altro metodo di crittografia, il dispositivo potrebbe diventare instabile. 
- **Crittografa la scheda di memoria (solo dispositivi mobili)**: scegliere **Rendi obbligatorio** per crittografare le eventuali schede di memoria rimovibili usate dal dispositivo. L'impostazione **Non configurata** (predefinita) non richiede la crittografia delle schede di archiviazione e non richiede all'utente di attivarla. Questa impostazione si applica solo ai dispositivi Windows 10 Mobile.

### <a name="bitlocker-base-settings"></a>Impostazioni di base di BitLocker

Supportato nelle edizioni di Windows 10 seguenti:

- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise
- Professional

Le impostazioni di base sono impostazioni BitLocker universali per tutti i tipi di unità dati. Queste impostazioni gestiscono le attività di crittografia delle unità o le opzioni di configurazione che gli utenti finali possono modificare in tutti i tipi di unità dati.

- **Avviso per la crittografia dischi di altro tipo**: selezionare **Blocca** per disabilitare l'avviso se nel dispositivo è presente un altro servizio di crittografia del disco. L'impostazione **Non configurata** (predefinita) consente la visualizzazione di questi avvisi.
    - **Consenti agli utenti standard di abilitare la crittografia durante un'aggiunta ad Azure AD**: se si sceglie **Consenti**, gli utenti standard/non amministratori possono abilitare la crittografia BitLocker dopo l'accesso. Questa impostazione si applica solo a dispositivi aggiunti ad Azure Active Directory (Azure ADJ). **Non configurato** consente solo agli amministratori di abilitare la crittografia BitLocker nel dispositivo.
      
      Questa impostazione si applica solo a dispositivi aggiunti ad Azure Active Directory (Azure ADJ). Richiede anche che l'impostazione **Warning for other disk encryption** (Avviso per altri tipi di crittografia disco) corrisponda a **Blocca**.
- **Configura i metodi di crittografia**: scegliere **Abilita** per configurare gli algoritmi di crittografia per il sistema operativo, i dati e le unità rimovibili. Con l'impostazione **Non configurata** (predefinita), BitLocker usa il metodo di crittografia predefinito XTS-AES 128 bit o il metodo di crittografia specificato da qualsiasi script di configurazione.
  - **Crittografia per le unità del sistema operativo**: scegliere il metodo di crittografia per le unità del sistema operativo. È consigliabile usare l'algoritmo XTS-AES.
  - **Crittografia per unità dati fisse**: scegliere il metodo di crittografia per le unità dati fisse (predefinite). È consigliabile usare l'algoritmo XTS-AES.
  - **Crittografia per unità dati rimovibili**: scegliere il metodo di crittografia per le unità dati rimovibili. Se l'unità rimovibile viene usata con dispositivi che non eseguono Windows 10, è consigliabile usare l'algoritmo AES-CBC.

### <a name="bitlocker-os-drive-settings"></a>Impostazioni delle unità del sistema operativo di BitLocker
Supportato nelle edizioni di Windows 10 seguenti:

- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise
- Professional

Queste impostazioni si applicano in modo specifico alle unità dati del sistema operativo.

- **Autenticazione aggiuntiva all'avvio**: selezionare **Rendi obbligatorio** per configurare i requisiti di autenticazione per l'avvio dei computer, incluso l'uso di Trusted Platform Module (TPM). Selezionare **Non configurata** (impostazione predefinita) per configurare solo le opzioni di base nei dispositivi con TPM.
  - **BitLocker con chip TPM non compatibile**: scegliere **Blocca** per disabilitare l'uso di BitLocker quando un dispositivo non dispone di un chip TPM compatibile. Con l'impostazione **Non configurata** gli utenti possono usare BitLocker senza un chip TPM compatibile. BitLocker può richiedere una password o una chiave di avvio.
  - **Avvio TPM compatibile**: scegliere se consentire, non consentire o rendere obbligatorio il chip TPM.
  - **PIN di avvio TPM compatibile**: scegliere se consentire, non consentire o rendere obbligatorio l'uso di un PIN di avvio con il chip TPM. L'abilitazione di un PIN di avvio richiede l'interazione dell'utente finale. 
  - **Chiave di avvio TPM compatibile**: scegliere se consentire, non consentire o rendere obbligatorio l'uso di una chiave di avvio con il chip TPM. L'abilitazione di una chiave di avvio richiede l'interazione dell'utente finale. 
  - **Chiave di avvio e PIN TPM compatibile**: scegliere se consentire, non consentire o rendere obbligatorio l'uso di una chiave di avvio e di un PIN con il chip TPM. L'abilitazione di chiave di avvio e PIN richiede l'interazione dell'utente finale.
- **Lunghezza minima del PIN**: scegliere **Abilita** per configurare la lunghezza minima del PIN di avvio del TPM. Con l'impostazione **Non configurata** (predefinita), gli utenti possono configurare un PIN di avvio di qualsiasi lunghezza compresa tra 6 e 20 cifre.
  - **Numero minimo di caratteri**: immettere il numero di caratteri obbligatorio per il PIN di avvio, **4**-**20**.
- **Ripristino delle unità del sistema operativo**: scegliere **Abilita** per controllare la modalità di ripristino delle unità del sistema operativo protette da BitLocker se le informazioni necessarie all'avvio non sono disponibili. Con l'impostazione **Non configurata** (predefinita), le opzioni di ripristino predefinite sono supportate per il ripristino di BitLocker. Per impostazione predefinita, è consentito un agente di recupero dati, le opzioni di ripristino vengono scelte dall'utente, incluse la password di ripristino e la chiave di ripristino, e non viene eseguito il backup delle informazioni di ripristino in Active Directory Domain Services.
  - **Agente di recupero dati basato su certificati**: con l'impostazione **Blocca** non è possibile usare l'agente di recupero dati con le unità del sistema operativo protette con BitLocker. Impostare su **Non configurata** (predefinita) per abilitare questa impostazione e consentire l'uso degli agenti di recupero dati con unità del sistema operativo protette da BitLocker.
  - **Creazione della password di ripristino da parte dell'utente**: scegliere se per gli utenti è consentito, obbligatorio o non consentito generare una password di ripristino di 48 cifre.
  - **Creazione della chiave di ripristino da parte dell'utente**: scegliere se per gli utenti è consentito, obbligatorio o non consentito generare una chiave di ripristino a 256 bit.
  - **Opzioni di ripristino nell'installazione guidata di BitLocker**: con l'impostazione **Blocca** gli utenti non possono visualizzare e modificare le opzioni di ripristino. Con l'impostazione **Non configurata** (predefinita) gli utenti possono visualizzare e modificare le opzioni di ripristino dopo l'attivazione di BitLocker.
  - **Salva le informazioni di ripristino di BitLocker in AD DS**: scegliere **Abilita** per archiviare le informazioni di ripristino di BitLocker in Azure Active Directory (AAD). Con l'impostazione **Non configurata** (predefinita) le informazioni di ripristino non vengono archiviate in AAD.
  - **Informazioni di ripristino di BitLocker archiviate in Azure Active Directory**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Azure AD. Scegliere tra:
    - **Backup delle password di ripristino e dei pacchetti di chiavi**
    - **Backup solo delle password di ripristino**
  - **Archivia le informazioni di ripristino in Azure Active Directory prima di abilitare BitLocker**: con l'impostazione **Rendi obbligatorio** gli utenti possono attivare BitLocker solo se le informazioni di ripristino di BitLocker sono state archiviate in Azure Active Directory. L'impostazione **Non configurata** (predefinita) consente agli utenti di attivare BitLocker, anche se le informazioni di ripristino non vengono archiviate correttamente in Azure AD.
- **URL e messaggio di ripristino prima dell'avvio**: scegliere **Abilita** per configurare il messaggio e l'URL visualizzati nella schermata di recupero della chiave prima dell'avvio. L'impostazione **Non configurata** (predefinita) disabilita questa funzionalità.
  - **Messaggio di ripristino prima dell'avvio**: consente di configurare la modalità di visualizzazione del messaggio di ripristino prima dell'avvio. Scegliere tra:
    - **Usa URL e messaggio di ripristino predefiniti**
    - **Usa un messaggio di ripristino e un URL vuoti**
    - **Usa messaggio di ripristino personalizzato**
    - **Usa URL di ripristino personalizzato**

### <a name="bitlocker-fixed-data-drive-settings"></a>Impostazioni delle unità dati fisse BitLocker

Supportato nelle edizioni di Windows 10 seguenti:

- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise
- Professional

**Impostazioni**:

- **Accesso in scrittura alle unità dati fisse non protette da BitLocker**: scegliere **Blocca** per consentire l'accesso in sola lettura alle unità dati non protette da BitLocker. Con l'impostazione **Non configurata** (predefinita) è disponibile l'accesso in lettura e scrittura alle unità dati protette da BitLocker.
- **Ripristino delle unità fisse**: scegliere **Abilita** per controllare la modalità di ripristino delle unità fisse protette da BitLocker se le informazioni necessarie all'avvio non sono disponibili. L'impostazione **Non configurata** (predefinita) disabilita questa funzionalità.
  - **Agente di recupero dati**: scegliere **Blocca** per impedire l'uso di un agente di recupero dati con l'editor dei criteri delle unità fisse protette da BitLocker. L'impostazione **Non configurata** (predefinita) abilita l'uso di agenti di recupero di dati con le unità fisse protette da BitLocker.
  - **Creazione della password di ripristino da parte dell'utente**: consente di specificare se per gli utenti è consentito, obbligatorio o non consentito generare una password di ripristino di 48 cifre.  
  - **Creazione della chiave di ripristino da parte dell'utente**: consente di specificare se per gli utenti è consentito, obbligatorio o non consentito generare una chiave di ripristino a 256 bit.
  - **Opzioni di ripristino nell'installazione guidata di BitLocker**: con l'impostazione **Blocca** gli utenti non possono visualizzare e modificare le opzioni di ripristino. Con l'impostazione **Non configurata** (predefinita) gli utenti possono visualizzare e modificare le opzioni di ripristino dopo l'attivazione di BitLocker.
  - **Salva le informazioni di ripristino di BitLocker in AD DS**: scegliere **Abilita** per archiviare le informazioni di ripristino di BitLocker in Azure Active Directory (Azure AD). Con l'impostazione **Non configurata** (predefinita) le informazioni di ripristino non vengono archiviate in Azure AD.
  - **Informazioni di ripristino di BitLocker in AD DS**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Azure AD. Le opzioni disponibili sono:
    - **Backup delle password di ripristino e dei pacchetti di chiavi**
    - **Backup solo delle password di ripristino**
  - **Archivia le informazioni di ripristino in Azure Active Directory prima di abilitare BitLocker**: con l'impostazione **Rendi obbligatorio** gli utenti possono attivare BitLocker solo se le informazioni di ripristino di BitLocker sono state archiviate in Azure AD. L'impostazione **Non configurata** (predefinita) consente agli utenti di attivare BitLocker anche se le informazioni di ripristino non vengono archiviate correttamente in Azure AD.

### <a name="bitlocker-removable-data-drive-settings"></a>Impostazioni delle unità dati rimovibili BitLocker

Supportato nelle edizioni di Windows 10 seguenti:

- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise
- Professional

**Impostazioni**:

- **Accesso in scrittura alle unità dati rimovibili non protette da BitLocker**: scegliere **Blocca** per consentire l'accesso in sola lettura alle unità dati non protette da BitLocker. Con l'impostazione **Non configurata** (predefinita) è disponibile l'accesso in lettura e scrittura alle unità dati protette da BitLocker.
  - **Accesso in scrittura ai dispositivi configurati in un'altra organizzazione**: l'impostazione **Blocca** consente l'accesso in scrittura ai dispositivi configurati in un'altra organizzazione. L'impostazione **Non configurata** (predefinita) nega l'accesso in scrittura.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Supportato nelle edizioni di Windows 10 seguenti:

- Home
- Professional
- Business
- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise

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

Per usare la protezione dagli exploit, creare un file XML che include le impostazioni di mitigazione desiderate per il sistema e le applicazioni. Sono disponibili due metodi:

 1. PowerShell: usare uno o più cmdlet Get-ProcessMitigation, Set-ProcessMitigation e ConvertTo-ProcessMitigationPolicy di PowerShell. I cmdlet configurano le impostazioni di mitigazione ed esportano la relativa rappresentazione XML.

 2. Interfaccia utente del Centro sicurezza di Windows Defender: nel Centro sicurezza di Windows Defender fare clic su Controllo app e browser e quindi scorrere fino alla parte inferiore della schermata visualizzata per trovare Protezione dagli exploit. Usare prima di tutto le schede Impostazioni di sistema e Impostazioni programmi per configurare le impostazioni di mitigazione. Trovare quindi il collegamento Esporta impostazioni nella parte inferiore della schermata per esportare la relativa rappresentazione XML.

Bloccare la **modifica dell'interfaccia di protezione dagli exploit da parte degli utenti** caricando un file XML che consente di configurare limitazioni di memoria, flusso di controllo e criteri. Le impostazioni nel file XML possono essere usate per proteggere un'applicazione dagli exploit. L'impostazione **Non configurata** (predefinita) non effettua il push di una configurazione personalizzata. 

## <a name="windows-defender-application-control"></a>Controllo di applicazioni di Windows Defender

Supportato nelle edizioni di Windows 10 seguenti:

**Gestione di dispositivi mobili (MDM)**: 
- Professional
- Business
- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise

**Gestione Criteri di gruppo**: 
- Enterprise

Usare i **criteri relativi all'integrità del codice di controllo dell'applicazione** per scegliere altre app che devono essere controllate o possono essere ritenute attendibili per l'esecuzione da parte del Controllo di applicazioni di Windows Defender. I componenti Windows e tutte le app di Windows Store sono ritenuti automaticamente attendibili per l'esecuzione.

In modalità **Solo controllo** le applicazioni non vengono bloccate. La modalità **Solo controllo** registra tutti gli eventi nei log del client locali.

Una volta abilitato, il controllo delle applicazioni può essere disabilitato solo passando dalla modalità **Imponi** alla modalità **Solo controllo**. Il passaggio dalla modalità **Imponi** alla modalità **Non configurato** fa sì che il controllo delle applicazioni continui a essere applicato nei dispositivi assegnati.

## <a name="windows-defender-credential-guard"></a>Windows Defender Credential Guard

Supportato nelle edizioni di Windows 10 seguenti:

- Enterprise

Windows Defender Credential Guard protegge contro attacchi relativi al furto di credenziali. Isola i segreti in modo che possa accedervi solo il software di sistema con privilegi.

Le impostazioni **Credential Guard** includono:

- **Disabilita**: disattiva Credential Guard in modalità remota, se attivato precedentemente con l'opzione **Abilita senza blocco UEFI**.

- **Abilita con blocco UEFI**: Credential Guard non può essere disabilitato in modalità remota usando una chiave del Registro di sistema o Criteri di gruppo.

    > [!NOTE]
    > Se si usa questa impostazione e in seguito si vuole disabilitare Credential Guard, è necessario impostare Criteri di gruppo su **Disabilitato**. e cancellare fisicamente le informazioni di configurazione UEFI da ogni computer. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

- **Abilita senza blocco UEFI**: consente di disabilitare Credential Guard in modalità remota usando Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 versione 1511 e successive.

Quando si abilita Credential Guard, vengono abilitate anche le funzionalità obbligatorie seguenti:

- **Abilita la sicurezza basata su virtualizzazione**: viene attivata al riavvio successivo. La sicurezza basata sulla virtualizzazione usa Windows Hypervisor per offrire il supporto per i servizi di sicurezza.
- **Avvio protetto con accesso diretto alla memoria**: attiva la sicurezza basata su virtualizzazione con l'avvio protetto e l'accesso diretto alla memoria. Le protezioni DMA richiedono supporto hardware e vengono abilitate solo nei dispositivi configurati correttamente.

## <a name="windows-defender-security-center"></a>Windows Defender Security Center

Supportato nelle edizioni di Windows 10 seguenti:

- Home
- Professional
- Business
- Enterprise
- Istruzione
- Mobile
- Mobile Enterprise

Windows Defender Security Center funziona come un'app o un processo separato da ognuna delle singole funzionalità. Visualizza le notifiche tramite il centro notifiche. Funge da agente di raccolta o da posizione centralizzata per visualizzare lo stato ed eseguire alcune attività di configurazione per ogni funzionalità. Per altre informazioni, vedere la documentazione di [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>App e notifiche di Windows Defender Security Center

È possibile bloccare l'accesso degli utenti finali alle diverse aree dell'app Windows Defender Security Center. Se si nasconde una sezione, vengono bloccate anche le notifiche correlate.

- **Protezione da virus e minacce**
- **Prestazioni e integrità del dispositivo**
- **Protezione firewall e della rete**
- **Controllo delle app e del browser**
- **Opzioni famiglia**
- **Notifiche dalle aree visualizzate dell'app**: scegliere le notifiche da visualizzare agli utenti finali. Le notifiche non critiche includono riepiloghi dell'attività di Windows Defender Antivirus, comprese le notifiche relative al completamento delle analisi. Tutte le altre notifiche sono considerate critiche.

#### <a name="it-contact-information"></a>Informazioni di contatto del reparto IT

Specificare le informazioni di contatto del reparto IT da visualizzare nell'app Windows Defender Security Center e nelle relative notifiche. È possibile scegliere **Visualizza nell'app e nelle notifiche**, **Visualizza solo nell'app**, **Visualizza solo nelle notifiche** o **Non visualizzare**. Immettere il **nome dell'organizzazione IT** e almeno una delle opzioni di contatto seguenti:

- **Numero di telefono del reparto IT o ID Skype**
- **Indirizzo di posta elettronica del reparto IT**
- **URL del sito Web del supporto tecnico IT**

## <a name="local-device-security-options"></a>Opzioni di sicurezza dei dispositivi locali

Supportato nelle edizioni di Windows 10 seguenti:
 
- Home
- Professional
- Business
- Enterprise
- Istruzione

Usare queste opzioni per configurare le impostazioni di sicurezza locali nei dispositivi Windows 10.

### <a name="accounts"></a>Account

- **Aggiungi nuovi account Microsoft**: impostare su **Blocca** per impedire agli utenti di aggiungere nuovi account Microsoft nel dispositivo. Con l'impostazione **Non configurata** (predefinita), gli utenti possono usare gli account Microsoft nel dispositivo.
- **Accesso remoto senza password**: **Abilita** consente agli account locali con password vuote di accedere tramite la tastiera del dispositivo. L'impostazione **Non configurata** (predefinita) consente agli account locali con password vuote di eseguire l'accesso da percorsi diversi rispetto al dispositivo fisico.

#### <a name="admin"></a>Amministratore

- **Account amministratore locale**: impostare su **Abilitato** per consentire l'account amministratore locale. L'impostazione **Non configurata** (predefinita) consente di disabilitare l'account amministratore locale.
- **Rinomina l'account amministratore**: consente di definire un nome account diverso da associare all'ID di sicurezza (SID) per l'account amministratore.

#### <a name="guest"></a>Guest

- **Account Guest**: impostare su **Abilitato** per consentire l'account guest locale. L'impostazione **Non configurata** (predefinita) consente di disabilitare l'account guest locale.
- **Rinomina l'account Guest**: consente di definire un nome account diverso da associare all'ID di sicurezza (SID) per l'account Guest.

### <a name="devices"></a>Dispositivi

- **Disancora il dispositivo senza accesso**: impostare su **Blocca** in modo che gli utenti possano premere il pulsante di espulsione fisico del dispositivo portatile inserito nell'alloggiamento di espansione per disinserire in modo sicuro il dispositivo. Con l'impostazione **Non configurata** (predefinita) viene richiesto all'utente di eseguire l'accesso al dispositivo per ricevere l'autorizzazione a disinserire il dispositivo dall'alloggiamento di espansione.
- **Installa i driver della stampante per le stampanti condivise**: con l'impostazione **Abilitata** qualsiasi utente può installare un driver della stampante durante la connessione a una stampante condivisa. Con l'impostazione **Non configurata** (predefinita), solo gli amministratori possono installare un driver della stampante come parte della connessione a una stampante condivisa.
- **Limita l'accesso al CD-ROM solo all'utente attivo locale**: con l'impostazione **Abilitata** solo gli utenti che hanno eseguito l'accesso in modo interattivo possono usare i supporti CD-ROM. Se questo criterio è abilitato e nessun utente è connesso in modo interattivo, l'accesso al CD-ROM avviene attraverso la rete. Con l'impostazione **Non configurata** (predefinita), chiunque può accedere al CD-ROM.
- **Formatta e rimuovi supporti rimovibili**: consente di determinare chi è autorizzato a formattare e rimuovere i supporti rimovibili NTFS:
  - **Non configurato**
  - **Amministratori**
  - **Amministratori e utenti esperti**
  - **Amministratori e utenti interattivi**

### <a name="interactive-logon"></a>Accesso interattivo

- **Minuti di inattività della schermata di blocco prima dell'attivazione dello screen saver**: immettere il numero massimo di minuti di inattività nella schermata di accesso del desktop interattivo prima dell'attivazione dello screen saver.
- **Richiedi CTRL+ALT+CANC per accedere**: impostare su **Abilita** in modo che gli utenti non debbano premere CTRL+ALT+CANC per accedere. Con l'impostazione **Non configurata** (predefinita) agli utenti viene richiesto di premere CTRL+ALT+CANC prima di accedere a Windows.
- **Comportamento in caso di rimozione della smart card**: determina le azioni che vengono eseguite quando la smart card di un utente connesso viene rimossa dal lettore di smart card. Le opzioni disponibili sono:

  - **Blocca la workstation**: quando la smart card viene rimossa, la workstation viene bloccata. Questa opzione consente all'utente di allontanarsi, portare con sé la smart card e mantenere comunque una sessione protetta.
  - **Imponi la disconnessione**: quando la smart card viene rimossa, l'utente viene automaticamente disconnesso.
  - **Disconnetti in caso di sessione dei Servizi Desktop remoto**: la rimozione della smart card determina la disconnessione della sessione senza disconnettere l'utente. Questa opzione consente all'utente di inserire la smart card e riprendere la sessione in un secondo momento oppure in un altro computer dotato di lettore di smart card, senza dover accedere di nuovo. Se la sessione è locale, questo criterio funziona in modo identico all'opzione Blocca workstation.

    Per informazioni più dettagliate, vedere [LocalPoliciesSecurity options](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-interactivelogon-smartcardremovalbehavior) (Opzioni di LocalPoliciesSecurity).

#### <a name="display"></a>Schermo

- **Informazioni utente nella schermata di blocco**: consente di configurare le informazioni utente visualizzate quando la sessione è bloccata. Se questa opzione non viene configurata, vengono mostrati il nome visualizzato dell'utente, il dominio e il nome utente.
  - **Non configurato**
  - **Nome visualizzato dell'utente, dominio e nome utente**
  - **Solo nome visualizzato dell'utente**
  - **Non visualizzare le informazioni utente**
- **Nascondi l'ultimo utente connesso**: con l'impostazione **Abilita** il nome utente viene nascosto. Con l'impostazione **Non configurata** (predefinita) il nome utente viene visualizzato.
- **Nascondi il nome utente all'accesso**: con l'impostazione **Abilita** il nome utente viene nascosto. Con l'impostazione **Non configurata** (predefinita) il nome utente viene visualizzato.
- **Titolo del messaggio di accesso**: imposta il titolo del messaggio per gli utenti che eseguono l'accesso.
- **Testo del messaggio di accesso**: imposta il testo del messaggio per gli utenti che eseguono l'accesso.

### <a name="network-access-and-security"></a>Accesso alla rete e sicurezza

- **Accesso anonimo alle named pipe e alle condivisioni**: **Non configurata** (impostazione predefinita) limita l'accesso anonimo alle impostazioni di condivisioni e named pipe. Si applica alle impostazioni a cui è possibile accedere anonimamente.
- **Enumerazione anonima degli account SAM**: **Consenti** permette agli utenti anonimi di enumerare gli account SAM. Windows consente agli utenti anonimi di enumerare i nomi degli account di dominio e delle condivisioni di rete.
- **Enumerazione anonima di account e condivisioni SAM**: **Non configurata** (impostazione predefinita) consente agli utenti anonimi di enumerare i nomi di account di dominio e condivisioni di rete. Per impedire l'enumerazione anonima di account e condivisioni SAM, impostare l'opzione su **Blocca**.
- **Valore hash di LAN Manager archiviato alla modifica della password**: alla prossima modifica della password, scegliere **Consenti** per consentire a LAN Manager di archiviare il valore hash per la nuova password. Con l'impostazione **Non configurata** (predefinita) il valore hash non viene archiviato.
- **Richieste di autenticazione PKU2U**: **Blocca** impedisce l'uso delle identità online da parte delle richieste di autenticazione PKU2U inviate al dispositivo. **Non configurato** (impostazione predefinita) consente queste richieste.
- **Limita le connessioni RPC remote a SAM**: **Consenti** imposta la stringa SDDL (Security Descriptor Definition Language) predefinita in modo da impedire a utenti e gruppi di effettuare chiamate remote a SAM. **Non configurato** (impostazione predefinita), stringa SDDL (Security Descriptor Definition Language) predefinita per consentire a utenti e gruppi di effettuare chiamate remote a SAM.
  - **Descrittore di sicurezza**

### <a name="recovery-console-and-shutdown"></a>Console di ripristino di emergenza e arresto

- **Cancella il file di paging della memoria virtuale all'arresto**: impostare su **Abilita** per cancellare il file di paging della memoria virtuale quando il dispositivo viene spento. L'impostazione **Non configurata** non cancella la memoria virtuale.
- **Arresta senza accesso**: **Blocca** nasconde l'opzione di arresto del sistema nella schermata di accesso di Windows. Gli utenti devono accedere al dispositivo e quindi arrestarlo. L'impostazione **Non configurata** (predefinita) consente agli utenti di arrestare il dispositivo dalla schermata di accesso di Windows.

### <a name="user-account-control"></a>Controllo dell'account utente

- **Integrità UIA senza posizione sicura**: con l'impostazione **Abilita** le app in una posizione sicura nel file system vengono eseguite solo con l'integrità UIAccess. L'impostazione **Non configurata** (predefinita) consente l'esecuzione delle app con l'integrità UIAccess, anche se le app non sono in una posizione sicura nel file system.
- **Virtualizza gli errori di scrittura nel file e nel Registro di sistema in percorsi specifici per ogni utente**: Con l'impostazione **Blocca** gli errori di scrittura delle applicazioni in fase di esecuzione vengono reindirizzati su percorsi utente definiti per il file system e il Registro di sistema. Con l'impostazione **Non configurata** (predefinita) le applicazioni che eseguono la scrittura dei dati in percorsi protetti genereranno errori.
- **Esegui con privilegi elevati solo i file eseguibili firmati e convalidati**: impostare su **Abilitata** per imporre la convalida del percorso di certificazione PKI di un file eseguibile prima che possa essere eseguito. L'impostazione **Non configurata** (predefinita) non impone la convalida del percorso di certificazione PKI di un file eseguibile prima che possa essere eseguito.

#### <a name="uia-elevation-prompt-behavior-settings"></a>Impostazioni del comportamento della richiesta di elevazione dei privilegi UIA

- **Richiesta di elevazione dei privilegi per amministratori**: consente di definire il comportamento della richiesta di elevazione dei privilegi per gli amministratori in modalità Approvazione amministratore:
  - **Esegui con privilegi elevati senza chiedere conferma**
  - **Richiedi credenziali sul desktop sicuro**
  - **Richiedi consenso sul desktop sicuro**
  - **Richiedi credenziali**
  - **Richiedi consenso**
  - **Non configurata**: Richiedi il consenso per file binari non Windows
- **Richiesta di elevazione dei privilegi per utenti standard**: consente di definire il comportamento della richiesta di elevazione dei privilegi per gli utenti standard:
  - **Nega automaticamente richieste di elevazione**
  - **Richiedi credenziali sul desktop sicuro**
  - **Non configurata**: Richiedi credenziali
- **Indirizza le richieste di elevazione dei privilegi al desktop interattivo dell'utente**: scegliere **Disabilita** in modo che tutte le richieste di elevazione dei privilegi vengano inviate al desktop dell'utente interattivo anziché al desktop protetto. Viene usata qualsiasi impostazione relativa ai criteri sul comportamento delle richieste per amministratori e utenti standard. Con l'impostazione **Non configurata** (predefinita) tutte le richieste di elevazione dei privilegi vengono inviate al desktop sicuro, indipendentemente dalle impostazioni relative ai criteri sul comportamento delle richieste per amministratori e utenti standard.
- **Prompt con privilegi elevati per installazioni di app**: con l'impostazione **Blocca** i pacchetti di installazione dell'applicazione non vengono rilevati o non viene richiesta l'elevazione dei privilegi. Con l'impostazione **Non configurata** (predefinita) all'utente vengono richiesti nome utente e password amministrativi quando un pacchetto di installazione di un'applicazione richiede privilegi elevati.
- **Richiesta di elevazione dei privilegi UIA senza desktop protetto**: **Abilita** consente alle app UIAccess di richiedere l'elevazione dei privilegi senza usare il desktop protetto. Con l'impostazione **Non configurata** (predefinita), le richieste di elevazione dei privilegi usano un desktop protetto.

#### <a name="admin-approval-mode-settings"></a>Impostazioni della modalità Approvazione amministratore

- **Modalità Approvazione amministratore per l'amministratore predefinito**: **Abilitata** consente all'account predefinito Administrator di usare la modalità Approvazione amministratore. Per qualunque operazione che richiede l'elevazione dei privilegi viene richiesta l'approvazione dell'utente. Con l'impostazione **Non configurata** (predefinita) tutte le app vengono eseguite con privilegi di amministratore completi.
- **Esegui tutti gli amministratori in modalità Approvazione amministratore**: impostare su **Blocca** per disabilitare la modalità Approvazione amministratore e tutte le impostazioni relative ai criteri di Controllo dell'account utente correlate. L'impostazione **Non configurata** (predefinita) consente di abilitare la modalità Approvazione amministratore.

### <a name="microsoft-network-client"></a>Client di rete Microsoft

- **Firma digitalmente le comunicazioni (se il server lo consente)**: determina se il client SMB negozia la firma dei pacchetti SMB. Con l'impostazione **Non configurata** o se abilitata (impostazione predefinita), il client di rete Microsoft richiede al server di eseguire la firma dei pacchetti SMB durante la configurazione della sessione. Se la firma dei pacchetti è abilitata nel server, questa verrà negoziata. Con l'impostazione **Disabilita** il client SMB non negozia mai la firma dei pacchetti SMB.
- **Invia password non crittografate a server SMB di terze parti**: con l'impostazione **Abilita** il redirector SMB (Server Message Block) può inviare password in testo non crittografato a server SMB non Microsoft che non supportano la crittografia della password durante l'autenticazione. Con l'impostazione **Non configurata** (predefinita) le password vengono crittografate.

### <a name="microsoft-network-server"></a>Server di rete Microsoft

- **Firma digitalmente le comunicazioni (se il client lo consente)**: determina se il server SMB negozierà la firma dei pacchetti SMB con i client che la richiedono. Con l'impostazione **Abilita** il server di rete Microsoft negozia la firma dei pacchetti SMB in base a quanto richiesto dal client, ovvero se la firma dei pacchetti è abilitata sul client, la firma dei pacchetti sarà negoziata. Se **Non configurato** o disabilitato (impostazione predefinita), il client SMB non negozierà mai la firma dei pacchetti SMB.
- **Firma digitalmente le comunicazioni (sempre)**: determina se la firma dei pacchetti è richiesta dal componente server SMB. Con l'impostazione **Abilita** il server di rete Microsoft comunica con un client di rete Microsoft solo se tale client accetta l'esecuzione della firma dei pacchetti SMB. Con l'impostazione **Non configurata** o se disabilitata (impostazione predefinita) la firma dei pacchetti SMB viene negoziata tra il client e il server.

## <a name="next-steps"></a>Passaggi successivi

Il profilo è stato creato, ma non è ancora operativo. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

Configurare le impostazioni di Endpoint Protection nei dispositivi [macOS](endpoint-protection-macos.md).
