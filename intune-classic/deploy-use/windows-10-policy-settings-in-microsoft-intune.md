---
title: Impostazioni dei criteri di Windows 10 | Documentazione Microsoft
description: Usare le impostazioni dei criteri indicate nell&quot;argomento per configurare le impostazioni personalizzate integrate per dispositivi registrati Windows 10 Desktop e Windows 10 Mobile.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/03/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: dd81102eb768ab8ad5f9ee1d2f122f15a8e17b89
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Impostazioni dei criteri di Intune per i dispositivi Windows 10 in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Questo argomento contiene informazioni che consentono di comprendere le impostazioni dei criteri di Intune che è possibile usare per gestire i dispositivi Windows 10. Leggere questo argomento e le procedure descritte nell'articolo [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](/intune-classic/get-started/windows-pc-management-capabilities-in-microsoft-intune).

È possibile scegliere tra due tipi di criteri:

- **Criteri personalizzati**: usare i **criteri personalizzati** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi. Windows 10 rende disponibili molte impostazioni CSP (Configuration Service Provider, provider di servizi di configurazione), ad esempio il [provider di servizi di configurazione dei criteri](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers).
- **Criteri di configurazione generali**: usare questo tipo di criteri quando si vogliono selezionare le impostazioni dall'elenco predefinito fornito con Microsoft Intune.

## <a name="custom-policy-settings"></a>Impostazioni di criteri personalizzati

Specificare le impostazioni seguenti in un criterio personalizzato.

### <a name="general-settings"></a>Impostazioni generali

Immettere un nome e una descrizione facoltativa per i criteri che consenta di identificarli nella console di Intune.

### <a name="oma-uri-settings"></a>Impostazioni OMA-URI

Per ogni impostazione URI OMA che si vuole aggiungere, immettere le informazioni seguenti. Usare il [riferimento alle impostazioni URI di Windows 10](/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings) in questo argomento per informazioni sulle impostazioni che è possibile usare:

- **Nome impostazione**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
- **Descrizione impostazione**: immettere facoltativamente una descrizione per l'impostazione.
- **Tipo di dati**: scegliere tra i tipi di dati seguenti:
    - **Stringa**
    - **Stringa (XML)**
    - **Data e ora**
    - **Intero**
    - **A virgola mobile**
    - **Booleano**
- **URI OMA (maiuscole/minuscole)**: specificare l'URI OMA per cui si vuole fornire un'impostazione.
- **Valore**: specificare il valore da associare all'URI OMA immesso.

### <a name="example"></a>Esempio
Nella schermata seguente è stata abilitata l'impostazione **Connectivity/AllowVPNOverCellular**. Ciò consente a un dispositivo Windows 10 di aprire una connessione VPN quando si trova in una rete cellulare.

> ![Esempio di criterio personalizzato contenente le impostazioni VPN](./media/custom-policy-example.png)

### <a name="how-to-find-the-policies-you-can-configure"></a>Come trovare i criteri che è possibile configurare

Per un elenco completo di tutti i provider di servizi di configurazione (CSP) supportati da Windows 10, vedere [Configuration service provider reference](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/configuration-service-provider-reference) (Informazioni di riferimento sui provider di servizi di configurazione) nella raccolta di documentazione di Windows.

Non tutte le impostazioni sono compatibili con tutte le versioni di Windows 10. La tabella nell'argomento di Windows indica quali versioni sono supportate per ogni CSP.

Intune inoltre non supporta tutte le impostazioni elencate nell'argomento. Per verificare se Intune supporta l'impostazione desiderata, aprire l'argomento relativo all'impostazione. Ogni pagina relativa a un'impostazione mostra le operazioni supportate. Per usare Intune, l'impostazione deve supportare l'operazione **Add** o **Replace**.

## <a name="general-configuration-policy-settings"></a>Impostazioni dei criteri di configurazione generali

Usare i **criteri di configurazione generale** di Microsoft Intune per Windows 10 per configurare le impostazioni predefinite per dispositivi registrati Windows 10 Desktop e Mobile.

### <a name="password"></a>Password

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Richiedi una password per sbloccare i dispositivi**|-|
|**Tipo di password richiesto**|Specifica se la password deve essere alfanumerica o solo numerica|
|**Tipo di password richiesto** - **Numero minimo di set di caratteri**| Specifica quanti set di caratteri (lettere minuscole, lettere maiuscole, numeri e simboli) devono essere inclusi nella password|
|**Lunghezza minima password**|Si applica solo a Windows 10 Mobile|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**.|Per i dispositivi che eseguono Windows 10: se nel dispositivo è abilitato BitLocker, viene inserita la modalità di ripristino di BitLocker se l'accesso non riesce per il numero di volte specificato. Se nel dispositivo non è abilitato BitLocker, questa impostazione non si applica.<br>Per i dispositivi che eseguono Windows 10 Mobile: se l'accesso non riesce per il numero di volte specificato, il dispositivo viene cancellato.|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica per quanto tempo il dispositivo deve rimanere inattivo prima che lo schermo venga bloccato|
|**Scadenza password (giorni)**|Specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo|
|**Ricorda cronologia password**|Specifica se impedire all'utente di creare password già usate in precedenza|
|**Ricorda cronologia password** - **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare|
|**Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività**|Specifica che l'utente deve inserire una password per sbloccare il dispositivo (solo Windows 10 Mobile)|

### <a name="encryption"></a>Crittografia

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Richiedi crittografia sui dispositivi mobili**|Abilita la crittografia sui dispositivi di destinazione<br>(Solo Windows 10 Mobile)|

### <a name="system"></a>Sistema

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Consenti acquisizione schermo**|Consente all'utente di acquisire la schermata del dispositivo come immagine (solo Windows 10 Mobile).|
|**Consenti l'annullamento della registrazione manuale**|Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.|
|**Consenti installazione manuale del certificato radice**|Si applica a Windows 10 Mobile|
|**Consenti l'invio di dati di utilizzo e di diagnostica a Microsoft**|I valori possibili sono:<br><br>**No** - Non vengono inviati dati a Microsoft<br>**Di base**: vengono inviate a Microsoft informazioni limitate<br>**Avanzati**: vengono inviati a Microsoft dati di diagnostica avanzati<br>**Completi (scelta consigliata)** -Invia gli stessi dati di **Avanzati**, più dati aggiuntivi sullo stato del dispositivo|


### <a name="account-and-synchronization"></a>Account e sincronizzazione

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti account Microsoft**|Consente all'utente di associare un account Microsoft con il dispositivo|
|**Consenti aggiunta manuale di account non Microsoft**|Consente all'utente di aggiungere account di posta elettronica al dispositivo che non sono associati con un account Microsoft|
|**Consenti sincronizzazione delle impostazioni per gli account Microsoft**|Consente che le impostazioni del dispositivo e delle app associate con un account Microsoft vengano sincronizzate fra i dispositivi|

### <a name="microsoft-edge"></a>Microsoft Edge

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Consenti Web browser**|Consente l'uso del Web browser Microsoft Edge sul dispositivo<br>(Solo Windows 10 Mobile)|
|**Consenti suggerimenti di ricerca nella barra degli indirizzi**|Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca|
|**Consenti l'invio di traffico Intranet a Internet Explorer**|Consente agli utenti di aprire siti Web sulla Intranet in Internet Explorer<br>(Solo Windows 10 Desktop)|
|**Consenti Do Not Track**|Configura il browser Microsoft Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti|
|**Attiva SmartScreen**||
|**Consenti scripting**|Consente di eseguire script come Javascript nel browser Microsoft Edge|
|**Consenti popup**|Si applica solo a Windows 10 Desktop|
|**Consenti cookie**||
|**Allow Autofill**|Consente agli utenti di modificare le impostazioni di completamento automatico nel browser<br>(Solo Windows 10 Desktop)|
|**Consenti strumento per la gestione delle password**|Abilita o disabilita la funzione di gestione password di Microsoft Edge|
|**Posizione elenco siti modalità Enterprise**|Specifica dove trovare l'elenco di siti Web che si aprono in modalità Enterprise. L'elenco non è modificabile dagli utenti.<br>(Solo Windows 10 Desktop)|

### <a name="apps"></a>App

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti archivio applicazioni**|Si applica solo a Windows 10 Mobile|



### <a name="cellular"></a>Cellulare

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti roaming dei dati**|Consente il roaming tra reti quando si accede ai dati|
|**Consenti VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è collegato a una rete cellulare|
|**Consenti roaming VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è in roaming su una rete cellulare|

### <a name="hardware"></a>Hardware

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|
|**Consenti la fotocamera**|-|
|**Consenti archivi rimovibili**|Specifica se è possibile usare dispositivi di archiviazione esterni come le schede SD con il dispositivo|
|**Consenti Wi-Fi**|Si applica solo a Windows 10 Mobile|
|**Consenti Internet condiviso**|Consente l'uso della condivisione della connessione Internet sul dispositivo|
|**Consenti configurazione Wi-Fi manuale**|Controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi<br>(Solo Windows 10 Mobile)|
|**Consenti connessione automatica agli hotspot Wi-Fi gratuiti**|Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione|
|**Consenti georilevazione**|Specifica se il dispositivo può usare le informazioni dei servizi di posizione|
|**Consenti NFC**|Consente al dispositivo di usare le sue capacità NFC (Near Field Communication)|
|**Consenti Bluetooth**|-|
|**Consenti modalità individuabile Bluetooth**|Consente che il dispositivo sia scoperto da altri dispositivi con la funzione Bluetooth attivata|
|**Consenti annunci con Bluetooth**|Consente ai dispositivi di ricevere annunci tramite Bluetooth|
|**Consenti ripristino del telefono**|Controlla se l'utente può eseguire un ripristino delle impostazioni predefinite nel dispositivo|
|**Consenti connessione USB**|Controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni mediante una connessione USB|
|**Consenti modalità AntiTheft**|Configura se la modalità Antitheft di Windows è abilitata|

### <a name="features"></a>Caratteristiche

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti copia e incolla**|Si applica solo a Windows 10 Mobile|
|**Consenti registrazione vocale**|Si applica solo a Windows 10 Mobile|
|**Consenti Cortana**|Abilita o disabilita l'assistente vocale Cortana|
|**Consenti notifiche del Centro operativo**|Abilita o disabilita le notifiche del Centro operativo sulla schermata di blocco del dispositivo<br>(Solo Windows 10 Mobile)|

### <a name="windows-defender"></a>Windows Defender

Tutte le impostazioni sono solo per Windows 10 Desktop.

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|----------------------|---------------------|
|**Consenti monitoraggio in tempo reale**|Abilita l'analisi in tempo reale per malware, spyware e altro software indesiderato|
|**Consenti monitoraggio comportamento**|Consente a Defender di controllare la presenza di modelli noti di attività sospette nei dispositivi|
|**Abilita Network Inspection System**|Network Inspection System (NIS) contribuisce a proteggere i dispositivi dagli exploit basati sulla rete usando le firme di vulnerabilità note di Microsoft Endpoint Protection Center per contribuire a rilevare e bloccare il traffico dannoso|
|**Analizza tutti i download**|Controlla se Defender deve analizzare tutti i file scaricati da Internet|
|**Consenti analisi script**|Consente a Defender di analizzare gli script usati in Internet Explorer|
|**Monitora l'attività di file e programmi**|Consente a Defender di monitorare l'attività di file e programmi nei dispositivi|
|**Giorni di rilevamento del malware risolto**|Consente a Defender di continuare a monitorare il malware risolto per il numero di giorni specificato, in modo che sia possibile controllare manualmente i dispositivi colpiti in precedenza. Se si imposta il numero di giorni su **0**, il malware rimane nella cartella della quarantena e non viene rimosso automaticamente. |
|**Consenti accesso all'interfaccia utente client**|Controlla se l'interfaccia utente di Windows Defender è nascosta agli utenti.<br>Quando questa impostazione viene modificata, ha effetto dal successivo avvio del PC da parte dell'utente.|
|**Pianifica analisi veloce giornaliera**|Consente di pianificare un'analisi veloce che viene eseguita giornalmente all'ora selezionata|
|**Pianifica analisi del sistema**|Consente di pianificare un'analisi completa o veloce del sistema che si verifica regolarmente il giorno e all'ora selezionati|
|**Limita utilizzo CPU durante un'analisi a**|Consente di limitare la quantità di CPU usata per le analisi (da **1** a **100**)|
|**Analizza file di archivio**|Consente a Defender di analizzare i file archiviati come i file con estensione zip o cab.|
|**Analisi dei messaggi di posta elettronica**|Consente a Defender di analizzare i messaggi di posta elettronica non appena arrivano sul dispositivo|
|**Analizza unità rimovibili**|Consente a Defender di analizzare le unità rimovibili, ad esempio le chiavette USB|
|**Analizza unità di rete mappate**|Consente a Defender di analizzare i file nelle unità di rete mappate.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|
|**Analizza file aperti da cartelle di rete condivise**|Consente a Defender di analizzare i file sulle unità di rete condivise, ad esempio quelli a cui si accede da un percorso UNC.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|
|**Intervallo di aggiornamento della firma**|Specifica l'intervallo in base a cui Defender controlla la presenza di nuovi file di firma.|
|**Consenti protezione cloud**|Consente o blocca la ricezione di informazioni sull'attività del malware da parte di Microsoft Active Protection Service dai dispositivi gestiti. Queste informazioni vengono usate per migliorare il servizio in futuro.|
|**Richiedi invio dei campioni agli utenti**|Controlla se i file che potrebbero richiedere ulteriore analisi da parte di Microsoft per determinare se sono dannosi vengono inviati automaticamente a Microsoft|
|**Rilevamento di applicazioni potenzialmente indesiderate**|Protegge i dispositivi desktop Windows registrati da eventuale software in esecuzione classificato da Windows Defender come potenzialmente indesiderato. È possibile ottenere protezione da tali applicazioni in esecuzione o usare la modalità di controllo per rilevare l'installazione di un'applicazione potenzialmente indesiderata.|
|**File e cartelle da escludere quando si esegue un'analisi o si usa la protezione in tempo reale**|Aggiunge uno o più file e cartelle come **C:\Percorso** o **%ProgramFiles%\Percorso\nomefile.exe** all'elenco di esclusione. Questi file e cartelle non sono inclusi nelle analisi in tempo reale o pianificate.|
|**Estensioni di file da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiungere uno o più estensioni di file come **jpg** o **txt** all'elenco delle esclusioni. I file con queste estensioni non sono inclusi nelle analisi in tempo reale o pianificate.|
|**Processi da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiunge uno o più processi del tipo **.exe**, **.com** o **.scr** all'elenco di esclusione. Questi processi non sono inclusi nelle analisi in tempo reale o pianificate.|


### <a name="updates"></a>Updates

|Nome impostazione|Informazioni aggiuntive (se richieste)|
|----------------|---------------|
|**Consenti aggiornamenti automatici**|Consente gli aggiornamenti automatici. Configurare una delle impostazioni seguenti per controllare il comportamento di aggiornamento:<br />**Notifica download**<br />**Installa automaticamente durante la manutenzione**<br />**Installa e riavvia automaticamente durante la manutenzione**<br />**Installa e riavvia automaticamente all'ora pianificata**: tenere presente che quando è selezionata questa opzione è possibile configurare anche le impostazioni seguenti: **Elimina la notifica per l'utente finale** e **Definire il giorno di installazione per gli aggiornamenti pianificati**.<br>(Solo Windows 10 Desktop)|
|**Consenti funzionalità di versioni non definitive**|Consente a Microsoft di distribuire le impostazioni e le funzionalità della versione non definitiva nei dispositivi Windows 10. È possibile consentire l'installazione delle sole impostazioni oppure di tutte le impostazioni e le funzionalità della versione non definitiva.|

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

