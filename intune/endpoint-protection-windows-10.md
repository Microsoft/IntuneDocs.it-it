---
title: Impostazioni di Microsoft Intune Endpoint Protection per Windows 10
titlesuffix: 
description: "Informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni di Endpoint Protection, ad esempio BitLocker nei dispositivi Windows 10."
keywords: 
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 02a32f678b40b2b40535984e17b41e0a864d8fdf
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="create-endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Creare impostazioni di Endpoint Protection per Windows 10 e versioni successive in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Il profilo di Endpoint Protection consente di controllare le funzionalità di sicurezza nei dispositivi Windows 10, ad esempio BitLocker e Windows Defender.

Usare le informazioni di questo articolo per apprendere come creare profili di Endpoint Protection.

> [!Note]
> Queste impostazioni non sono supportate nelle edizioni di Windows 10 Home e Professional.

## <a name="create-an-endpoint-protection-profile"></a>Creare un profilo di Endpoint Protection

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere i valori di **Nome** e **Descrizione** per il profilo delle funzionalità del dispositivo.
5. Dall'elenco a discesa **Piattaforma** selezionare **Windows 10 e versioni successive**.
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Endpoint Protection**.
7. Configurare le impostazioni desiderate. I dettagli in questo articolo consentono di comprendere la funzione di ogni impostazione. Al termine, scegliere **OK**.
8. Tornare al pannello **Crea profilo** e scegliere **Crea**.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.

## <a name="windows-defender-application-guard"></a>Windows Defender Application Guard

Application Guard è disponibile solo per i dispositivi Windows 10 a 64 bit. Quando si usa questo profilo viene installato un componente Win32 per attivare Application Guard.

- **Application Guard**: consente di aprire siti non approvati in un contenitore del browser virtuale di Hyper-V.
- **Comportamento degli Appunti**: consente di scegliere le azioni di copia/incolla consentite tra il computer locale e il browser virtuale di Application Guard.
- **Contenuto esterno nei siti aziendali**: consente di bloccare il caricamento del contenuto dei siti Web non approvati.
- **Stampa dal browser virtuale**: consente alle stampanti PDF, XPS, locali e/o di rete di stampare contenuto dal browser virtuale.
- **Raccogli registri**: consente di raccogliere i registri degli eventi che si verificano in una sessione del browser di Application Guard.
- **Conserva i dati del browser generati dall'utente**: consente di salvare i dati utente, ad esempio password, Preferiti e cookie, creati durante una sessione del browser virtuale di Application Guard.
- **Accelerazione grafica**: consente di caricare più rapidamente i siti Web con molti elementi grafici quando si lavora all'interno della sessione del browser virtuale di Application Guard e si consente l'accesso a un'unità di elaborazione grafica virtuale.


## <a name="windows-defender-firewall"></a>Windows Defender Firewall

### <a name="global-settings"></a>Impostazioni globali

Queste impostazioni sono applicabili a tutti i tipi di rete.

- **File Transfer Protocol**: consente di bloccare il protocollo FTP con stato.
- **Tempo di inattività delle associazioni di sicurezza prima dell'eliminazione**: le associazioni di sicurezza vengono eliminate dopo che per *n* secondi non è stato rilevato traffico.
- **Codifica delle chiavi precondivise**: consente di codificare le chiavi già condivise usando il formato UTF-8.
- **Esenzioni IPSec**: consente di configurare traffico specifico da esentare da IPsec, tra cui **Codici di tipo ICMP IPv6 per Neighbor Discover**, **ICMP**, **Codici di tipo ICMP IPv6 per Router Discover** e **Traffico DHCP IPv4 e IPv6**.
- **Verifica dell'elenco di revoche di certificati**: consente di impostare un valore per la modalità di applicazione della verifica dell'elenco di revoche di certificati, tra cui **Disabilita la verifica dell'elenco di revoche di certificati**, **Esito negativo della verifica dell'elenco di revoche di certificati solo in caso di certificato revocato** e **Esito negativo della verifica dell'elenco di revoche di certificati per ogni errore rilevato**.
- **Corrispondenza opportunistica del set di autenticazione per ogni modulo per le chiavi**: consente di impostare i moduli di impostazione chiavi in modo da ignorare l'intero set di autenticazione nel caso in cui non supportino tutte le famiglie di prodotti di autenticazione in tale set.
- **Accodamento di pacchetti**: consente di specificare la modalità di abilitazione del ridimensionamento per il software sul lato ricezione per la ricezione di testo crittografato e l'inoltro di testo normale per lo scenario relativo a gateway con tunnel IPsec, assicurando il mantenimento dell'ordine dei pacchetti.

### <a name="network-settings"></a>Impostazioni di rete

Queste impostazioni sono applicabili a tipi di rete specifici, tra cui **Rete di dominio (aziendale)**, **Rete privata (individuabile)** e **Rete pubblica (non individuabile)**.

#### <a name="general-settings"></a>Impostazioni generali

- **Windows Defender Firewall**: abilitare questa impostazione per bloccare il traffico di rete.
- **Modalità mascheramento**: consente di bloccare il funzionamento del firewall in modalità mascheramento. Questo tipo di blocco consente di bloccare anche **Esenzione di pacchetti protetti da IPsec**.
- **Schermata**: l'abilitazione di questa impostazione e di quella relativa al firewall determina il blocco di tutto il traffico in ingresso.
- **Risposte unicast a broadcast multicast**: consente di bloccare le risposte unicast ai broadcast multicast. In genere, si preferisce non ricevere risposte unicast ai messaggi multicast o broadcast poiché queste risposte possono indicare un attacco Denial of Service o un utente malintenzionato che tenta di rilevare la presenza di un computer attivo noto.
- **Notifiche in ingresso**: consente di impedire la visualizzazione delle notifiche agli utenti quando un'applicazione non è autorizzata all'ascolto su una porta.
- **Azione predefinita per le connessioni in ingresso**: consente di bloccare l'azione predefinita eseguita dal firewall sulle connessioni in ingresso.

#### <a name="rule-merging"></a>Unione delle regole

- **Regole di Windows Defender Firewall per le applicazioni autorizzate dall'archivio locale**: consente di applicare le regole autorizzate del firewall nell'archivio locale per il riconoscimento e l'applicazione.
- **Regole di Windows Defender Firewall per porte globali dall'archivio locale**: consente di applicare le regole del firewall per le porte globali nell'archivio locale per il riconoscimento e l'applicazione.
- **Regole di Windows Defender Firewall dall'archivio locale**: consente di applicare le regole globali del firewall nell'archivio locale per il riconoscimento e l'applicazione.
- **Regole IPsec dall'archivio locale**: consente di applicare le regole di sicurezza della connessione dall'archivio locale, indipendentemente dallo schema o dalle versioni delle regole di sicurezza della connessione.

## <a name="windows-defender-smartscreen-settings"></a>Impostazioni di Windows Defender SmartScreen

- **SmartScreen per app e file**: consente di abilitare Windows SmartScreen per l'esecuzione di file e per le app in esecuzione.
- **Esecuzione di file non verificati**: consente di impedire all'utente finale di eseguire file non verificati da Windows SmartScreen.

## <a name="windows-encryption"></a>Crittografia di Windows

### <a name="windows-settings"></a>Impostazioni Windows

Queste impostazioni si applicano a tutte le versioni di Windows 10.

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
    - **Avvio TPM compatibile**: consente di indicare se il chip TPM è consentito, non consentito o obbligatorio.
    - **PIN di avvio TPM compatibile**: consente di indicare se l'uso di un PIN di avvio con il chip TPM è consentito, non consentito o obbligatorio.
    - **Chiave di avvio TPM compatibile**: consente di indicare se l'uso di una chiave di avvio con il chip TPM è consentito, non consentito o obbligatorio.
    - **Chiave di avvio e PIN TPM compatibile**: consente di indicare se l'uso di una chiave e di un PIN di avvio con il chip TPM è consentito, non consentito o obbligatorio.
- **Lunghezza minima del PIN**: abilitare questa impostazione per configurare la lunghezza minima del PIN di avvio del chip TPM.
    - **Numero minimo di caratteri**: immettere il numero di caratteri obbligatorio per il PIN di avvio, **4**-**20**.
- **Ripristino delle unità del sistema operativo**: abilitare questa impostazione per controllare la modalità di ripristino delle unità del sistema operativo protette da BitLocker se le informazioni necessarie all'avvio non sono disponibili.
    - **Agente di recupero dati basato su certificati**: abilitare questa impostazione se si vuole che sia possibile usare gli agenti di recupero dati con unità del sistema operativo protette da BitLocker.
    - **Creazione della password di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una password di ripristino di 48 cifre.
    - **Creazione della chiave di ripristino da parte dell'utente**: configurare se per gli utenti è consentito, obbligatorio o non consentito generare una chiave di ripristino a 256 bit.
    - **Opzioni di ripristino nell'installazione guidata di BitLocker**: abilitare questa impostazione per impedire agli utenti di visualizzare o modificare le opzioni di ripristino se BitLocker è attivato.
    - **Salva le informazioni di ripristino di BitLocker in AD DS**: consente l'archiviazione delle informazioni di ripristino di BitLocker in Active Directory.
    - **Informazioni di ripristino di BitLocker archiviate in AD DS**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Active Directory. È possibile scegliere tra:
        - **Backup delle password di ripristino e dei pacchetti di chiavi**
        - **Backup solo delle password di ripristino**
    - **Archivia le informazioni di ripristino in AD DS prima di abilitare BitLocker**: abilitare questa impostazione per consentire agli utenti di attivare BitLocker solo se il dispositivo è stato aggiunto al dominio e le informazioni di ripristino di BitLocker sono state archiviate in Active Directory.
- **URL e messaggio di ripristino prima dell'avvio**: abilitare questa impostazione per configurare il messaggio e l'URL visualizzati nella schermata di recupero della chiave prima dell'avvio.
    - **Messaggio di ripristino prima dell'avvio**: consente di configurare la modalità di visualizzazione del messaggio di ripristino. È possibile scegliere tra:
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
    - **Informazioni di ripristino di BitLocker in AD DS**: consente di configurare quali parti delle informazioni di ripristino di BitLocker devono essere archiviate in Active Directory. È possibile scegliere tra:
        - **Backup delle password di ripristino e dei pacchetti di chiavi**
        - **Backup solo delle password di ripristino**
    - **Archivia le informazioni di ripristino in AD DS prima di abilitare BitLocker**: abilitare questa impostazione per consentire agli utenti di attivare BitLocker solo se il dispositivo è stato aggiunto al dominio e le informazioni di ripristino di BitLocker sono state archiviate in Active Directory.

### <a name="bitlocker-removable-data-drive-settings"></a>Impostazioni delle unità dati rimovibili BitLocker

- **Accesso in scrittura alle unità dati rimovibili non protette da BitLocker**: consente di specificare se la crittografia BitLocker è obbligatoria per le unità di archiviazione rimovibili.
  - **Accesso in scrittura ai dispositivi configurati in un'altra organizzazione**: consente di specificare se è possibile scrivere nelle unità dati rimovibili che appartengono a un'altra organizzazione.

## <a name="windows-defender-exploit-guard"></a>Windows Defender Exploit Guard

Usare [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard) per gestire e ridurre la superficie di attacco delle app usate dai dipendenti.

### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco

[Evitare azioni e app](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/attack-surface-reduction-exploit-guard) che generalmente vengono usate dal malware per infettare i computer.

#### <a name="rules-to-prevent-office-macro-threats"></a>Regole per impedire le minacce relative alle macro di Office

Impedire alle app di Office di eseguire le azioni seguenti:

- **Inserimento delle app di Office in altri processi (nessuna eccezione)**
- **Creazione di contenuto eseguibile in app/macro di Office**
- **Avvio di processi figlio per le app di Office**
- **Importazioni Win32 da codice delle macro in Office**

#### <a name="rules-to-prevent-script-threats"></a>Regole per impedire le minacce relative agli script

Bloccare questi elementi per contrastare le minacce basate su script:

- **Codice js/vbs/ps/macro offuscato**
- **Esecuzione in js/vbs di payload scaricato da Internet (nessuna eccezione)**

#### <a name="rules-to-prevent-email-threats"></a>Regole per impedire le minacce tramite posta elettronica

Bloccare questa azione per contrastare le minacce tramite posta elettronica:

- **Esecuzione del contenuto eseguibile (file con estensione exe, dll, ps, js, vbs e così via) non elaborato dalla posta elettronica (webmail/mail client) (nessuna eccezione)**

#### <a name="attack-surface-reduction-exceptions"></a>Eccezioni della riduzione della superficie di attacco

- **File e cartelle da escludere dalle regole di riduzione della superficie di attacco**: importare/aggiungere un elenco di percorsi da escludere dalle regole configurate.

### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

È possibile proteggere i dati importanti da app e minacce dannose, ad esempio il ransomware.

- **Protezione delle cartelle**: consente di proteggere file e cartelle dalle modifiche indesiderate di app dannose. È possibile importare un **elenco di app con accesso alle cartelle protette** o aggiungerle manualmente. È anche possibile aggiungere un **elenco di cartelle aggiuntive da proteggere** con un'operazione di caricamento o aggiungendole manualmente.

### <a name="network-filtering"></a>Filtri di rete

È possibile bloccare le connessioni in uscita da qualsiasi app verso indirizzi IP/domini con reputazione negativa.

### <a name="exploit-protection"></a>Protezione dagli exploit

Bloccare la **modifica dell'interfaccia di protezione dagli exploit da parte degli utenti** caricando un file XML che consente di configurare limitazioni di memoria, flusso di controllo e criteri da usare per proteggere un'applicazione dagli exploit.

Per abilitare la protezione dagli exploit creare un file XML che rappresenta le impostazioni di mitigazione scelte per il sistema e le applicazioni. A questo scopo, è possibile usare uno dei due metodi seguenti:

 1. PowerShell: usare uno o più cmdlet Get-ProcessMitigation, Set-ProcessMitigation e ConvertTo-ProcessMitigationPolicy di PowerShell per configurare le impostazioni di mitigazione ed esportare la relativa rappresentazione XML.

 2. Interfaccia utente di Windows Defender Security Center: in Windows Defender Security Center fare clic su Controllo app e browser e quindi scorrere fino alla parte inferiore della schermata visualizzata per trovare Protezione dagli exploit. Usare prima di tutto le schede Impostazioni di sistema e Impostazioni programmi per configurare le impostazioni di mitigazione. Trovare quindi il collegamento Esporta impostazioni nella parte inferiore della schermata per esportare la relativa rappresentazione XML.

## <a name="windows-defender-application-control"></a>Controllo di applicazioni di Windows Defender

Usare i **criteri relativi all'integrità del codice di controllo dell'applicazione** per scegliere altre app che devono essere controllate o possono essere ritenute attendibili per l'esecuzione da parte del Controllo di applicazioni di Windows Defender. I componenti Windows e tutte le app di Windows Store sono ritenuti automaticamente attendibili per l'esecuzione.

In modalità **Solo controllo** le applicazioni non vengono bloccate. La modalità **Solo controllo** registra tutti gli eventi nei log del client locali.

Una volta abilitato, il controllo delle applicazioni può essere disabilitato solo passando dalla modalità **Imponi** alla modalità **Solo controllo**. Il passaggio dalla modalità **Imponi** alla modalità **Non configurato** fa sì che il controllo delle applicazioni continui a essere applicato nei dispositivi assegnati.

## <a name="windows-defender-security-center"></a>Windows Defender Security Center

L'app Windows Defender Security Center funziona come un'app o un processo separato da ognuna delle singole funzionalità e visualizza le notifiche tramite il centro notifiche. Funge da agente di raccolta o unica posizione per visualizzare lo stato ed eseguire alcune attività di configurazione per ogni funzionalità. Per altre informazioni, vedere la documentazione di [Windows Defender](https://docs.microsoft.com/windows/threat-protection/windows-defender-security-center/windows-defender-security-center).

#### <a name="windows-defender-security-center-app-and-notifications"></a>App e notifiche di Windows Defender Security Center

È possibile bloccare l'accesso degli utenti finali alle diverse aree dell'app Windows Defender Security Center. Se si nasconde una sezione, verranno bloccate anche le notifiche correlate.

- **Protezione da virus e minacce**
- **Prestazioni e integrità del dispositivo**
- **Protezione firewall e della rete**
- **Controllo delle app e del browser**
- **Opzioni famiglia**
- **Notifiche dalle aree visualizzate dell'app**: consente di scegliere le notifiche da visualizzare agli utenti finali. Le notifiche non critiche includono riepiloghi dell'attività di Windows Defender Antivirus, comprese le notifiche relative al completamento delle analisi. Tutte le altre notifiche sono considerate critiche.

#### <a name="it-contact-information"></a>Informazioni di contatto del reparto IT

Specificare le informazioni di contatto del reparto IT da visualizzare nell'app Windows Defender Security Center e nelle relative notifiche. È possibile scegliere **Visualizza nell'app e nelle notifiche**, **Visualizza solo nell'app**, **Visualizza solo nelle notifiche** o **Non visualizzare**. È necessario definire il **nome dell'organizzazione IT** e almeno una delle opzioni di contatto seguenti:

- **Numero di telefono del reparto IT o ID Skype**
- **Indirizzo di posta elettronica del reparto IT**
- **URL del sito Web del supporto tecnico IT**

## <a name="next-steps"></a>Passaggi successivi

Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
