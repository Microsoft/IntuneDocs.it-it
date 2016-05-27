---
# required metadata

title: Impostazioni dei criteri di Windows 10 in Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Impostazioni dei criteri di Windows 10 in Microsoft Intune

Usare le impostazioni dei criteri indicate nell'argomento come aiuto per configurare le impostazioni per dispositivi registrati Windows 10 Desktop e Windows 10 Mobile.

## Impostazioni dei criteri di configurazione generale

Usare i **criteri di configurazione generale** di Microsoft per Windows 10 per configurare le impostazioni generali per dispositivi registrati Windows 10 Desktop e Windows 10 Mobile:


### Password

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Richiedi una password per sbloccare i dispositivi**|Richiede una password nei dispositivi supportati.|Sì|Sì|
|**Tipo di password richiesto**|Specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico|sì|sì|
|**Tipo di password richiesto** - **Numero minimo di set di caratteri**|Sono disponibili quattro set di caratteri, lettere minuscole, lettere maiuscole, numeri e simboli. L'impostazione specifica quanti set di caratteri diversi è necessario includere nella password.|Sì|Sì|
|**Lunghezza minima password**|Specifica il numero minimo di caratteri che la password del dispositivo deve contenere.|No|Sì|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Cancella il dispositivo se questo numero di tentativi di accesso ha esito negativo.|Sì|Sì|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica per quanto tempo il dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.|sì|Sì|
|**Scadenza password (giorni)**|Specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo.|sì|Sì|
|**Ricorda cronologia password**|Specifica se si vuole impedire all'utente finale di creare password già usate in precedenza.|Sì|Sì|
|**Ricorda cronologia password** - **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare.|Sì|Sì|
|**Consenti password grafica e PIN**|Consente di usare movimenti semplici su un'immagine o un semplice PIN per effettuare l'accesso.|Sì|No|
|**Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività**|Se abilitata, l'utente deve inserire una password per sbloccare il dispositivo dallo stato inattivo.|No|Sì|

### Crittografia

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Richiedi crittografia sui dispositivi mobili**|Abilita la crittografia sui dispositivi di destinazione.|No|Sì|

### Sistema

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Consenti acquisizione schermo**|Consente all'utente di acquisire la schermata del dispositivo come immagine.|No|Sì|
|**Consenti l'annullamento della registrazione manuale**|Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.|Sì|Sì|
|**Consenti installazione manuale del certificato radice**|Specifica se l'utente può installare manualmente i certificati radice.|No|Sì|
|**Consenti l'invio di dati di utilizzo e di diagnostica a Microsoft**|Determina la quantità di dati diagnostici e di utilizzo che vengono inviati a Microsoft dai dispositivi.<br>**No** - Non vengono inviati dati a Microsoft<br>**Base** - Il dispositivo invia solo informazioni limitate a Microsoft<br>**Avanzati** -Invia dati di diagnostica avanzati a Microsoft<br>**Completi (scelta consigliata)** -Invia gli stessi dati di **Avanzati**, più dati aggiuntivi sullo stato del dispositivo|Sì|Sì|


### Account e sincronizzazione

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Consenti account Microsoft**|Consente all'utente di associare un account Microsoft con il dispositivo.|Sì|Sì|
|**Consenti aggiunta manuale di account non Microsoft**|Consente all'utente di aggiungere account di posta elettronica al dispositivo che non sono associati con un account Microsoft.|sì|Sì|
|**Consenti sincronizzazione delle impostazioni per gli account Microsoft**|Consente che le impostazioni del dispositivo e delle app associate con un account Microsoft vengano sincronizzate fra i dispositivi.|sì|Sì|

### Impostazioni di posta elettronica

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Rendi l'account Microsoft facoltativo nell'applicazione Windows Mail**|Configura l'opzione in modo da rimuovere il requisito per un account Microsoft in Windows Mail.|sì|No|



### Microsoft Edge

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Consenti browser Web**|Consente l'uso del browser Web Edge sul dispositivo.|No|Sì|
|**Consenti suggerimenti di ricerca nella barra degli indirizzi**|Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca.|sì|Sì|
|**Consenti l'invio di traffico Intranet a Internet Explorer**|Consente agli utenti di aprire siti Web sulla Intranet in Internet Explorer.|Sì|No|
|**Consenti Do Not Track**|Configura il browser Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti.|Sì|Sì|
|**Attiva SmartScreen**|Abilita l'impostazione SmartScreen del browser sui dispositivi.|Sì|Sì|
|**Consenti scripting**|Consente di eseguire script, ad esempio JavaScript, nel browser Edge.|sì|Sì|
|**Consenti popup**|Attiva o disattiva il blocco popup del browser.|Sì|No|
|**Consenti cookie**|Consente o disattiva i cookie.|Sì|Sì|
|**Consenti riempimento automatico**|Consente all'utente di modificare le impostazioni di completamento automatico nel browser.|Sì|No|
|**Consenti strumento per la gestione delle password**|Abilita o disabilita la funzione di gestione password di Edge.|Sì|Sì|
|**Posizione elenco siti modalità Enterprise**|Specifica dove trovare l'elenco di siti Web che verranno aperti in modalità Enterprise. L'elenco non è modificabile dagli utenti.|Sì|No|

### App

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Consenti archivio applicazioni**|Consente all'utente di accedere all'App Store sul dispositivo.|No|Sì|



### Cellulare

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Consenti dati in roaming**|Consente il roaming tra reti quando si accede a dati.|Sì|Sì|
|**Consenti VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è collegato a una rete cellulare.|Sì|Sì|
|**Consenti roaming VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è in roaming su una rete cellulare.|Sì|Sì|

### Hardware

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Consenti dispositivo foto/video**|Specifica se è consentito l'uso della fotocamera del dispositivo.|Sì|Sì|
|**Consenti archivi rimovibili**|Specifica se è possibile usare dispositivi di archiviazione esterni come le schede SD con il dispositivo.|sì|Sì|
|**Consenti Wi-Fi**|Consente l'uso delle funzionalità Wi-Fi dei dispositivi.|No|Sì|
|**Consenti Internet condiviso**|Consente l'uso della condivisione della connessione Internet sul dispositivo.|Sì|Sì|
|**Consenti configurazione Wi-Fi manuale**|Controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi.|No|Sì|
|**Consenti connessione automatica agli hotspot Wi-Fi gratuiti**|Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione.|Sì|Sì|
|**Consenti georilevazione**|Specifica se il dispositivo può usare le informazioni dei servizi di posizione.|Sì|Sì|
|**Consenti NFC**|Consente al dispositivo di usare le sue capacità NFC (Near Field Communication).|sì|Sì|
|**Consenti Bluetooth**|Consente l'uso delle capacità Bluetooth sul dispositivo.|sì|Sì|
|**Consenti modalità individuabile Bluetooth**|Consente che il dispositivo sia scoperto da altri dispositivi con la funzione Bluetooth attivata.|Sì|Sì|
|**Consenti annunci con Bluetooth**|Consente ai dispositivi di ricevere annunci tramite Bluetooth.|Sì|sì|
|**Consenti modalità di connessione Bluetooth** **Importante:** |Questa impostazione non è più supportata in Windows 10 e verrà rimossa in futuro.|Sì|Sì|
|**Consenti ripristino del telefono**|Controlla se l'utente può ripristinare le impostazioni predefinite nel dispositivo.|Sì|Sì|
|**Consenti connessione USB**|Controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni mediante una connessione USB.|Sì|Sì|
|**Consenti modalità AntiTheft**|Consente di configurare l'abilitazione della modalità Antitheft di Windows.|Sì|Sì|

### Caratteristiche

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|----------------------|---------------------|
|**Consenti copia e incolla**|Abilita o disabilita l'uso del copia e incolla sul dispositivo.|No|Sì|
|**Consenti registrazione vocale**|Abilita o disabilita la funzione di registrazione locale sul dispositivo.|No|Sì|
|**Consenti Cortana**|Abilita o disabilita l'assistente vocale Cortana.|Sì|Sì|
|**Consenti notifiche del Centro operativo**|Abilita o disabilita le notifiche del Centro operativo sulla schermata di blocco del dispositivo.|No|sì|

### Defender

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|-|-|
|**Consenti monitoraggio in tempo reale**|Abilita l'analisi in tempo reale per malware, spyware e altro software indesiderato.|Sì|No|
|**Consenti monitoraggio comportamento**|Consente a Defender di individuare determinati modelli di attività sospette nei dispositivi.|sì|No
|**Abilita Network Inspection System**|Network Inspection System (NIS) contribuisce a proteggere i dispositivi dagli exploit basati sulla rete usando le firme di vulnerabilità note di Microsoft Endpoint Protection Center per contribuire a rilevare e bloccare il traffico dannoso.|Sì|No
|**Analizza tutti i download**|Controlla se Defender deve analizzare tutti i file scaricati da Internet.|Sì|No
|**Consenti analisi script**|Consente a Defender di analizzare gli script usati in Internet Explorer.|Sì|No
|**Monitora l'attività di file e programmi**|Abilitare questa impostazione per consentire a Defender di monitorare l'attività di file e programmi nei dispositivi.|Sì|No
|**Giorni di rilevamento del malware risolto**|Consente a Defender di continuare a monitorare il malware risolto per il numero di giorni specificato, in modo che sia possibile controllare manualmente i dispositivi colpiti in precedenza. Se si imposta il numero di giorni su **0**, il malware rimane nella cartella della quarantena e non viene rimosso automaticamente. |sì|No
|**Consenti accesso all'interfaccia utente client**|Controlla se l'interfaccia utente di Windows Defender è nascosta agli utenti finali.<br>Quando questa impostazione viene modificata, ha effetto dal successivo avvio del PC da parte dell'utente finale.|Sì|No
|**Pianifica analisi veloce giornaliera**|Consente di pianificare un'analisi veloce che viene eseguita giornalmente all'ora selezionata.|Sì|No
|**Pianifica analisi del sistema**|Consente di pianificare un'analisi completa o veloce del sistema che si verifica regolarmente il giorno e all'ora selezionati.|Sì|No
|**Limita utilizzo CPU durante un'analisi a**|Consente di limitare la quantità di CPU che le analisi possono usare (da **1** a **100**)|Sì|No
|**Analizza file di archivio**|Consente a Defender di analizzare i file archiviati come i file Zip o Cab.|Sì|No
|**Analisi dei messaggi di posta elettronica**|Consente a Defender di analizzare i messaggi di posta elettronica non appena arrivano sul dispositivo.|Sì|No
|**Analizza unità rimovibili**|Consente a Defender di analizzare le unità removibili come le chiavette le USB.|Sì|No
|**Analizza unità di rete mappate**|Consente a Defender di analizzare i file nelle unità di rete mappate.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|Sì|No
|**Analizza file aperti da cartelle di rete condivise**|Consente a Defender di analizzare i file sulle unità di rete condivise, ad esempio quelli a cui si accede da un percorso UNC.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|sì|No
|**Intervallo di aggiornamento della firma**|Specifica l'intervallo secondo il quale Defender controllerà i nuovi file di firma.|sì|No
|**Consenti protezione cloud**|Consente o blocca la ricezione di informazioni sull'attività del malware da parte di Microsoft Active Protection Service dai dispositivi gestiti. Queste informazioni vengono usate per migliorare il servizio in futuro.|Sì|No
|**Richiedi invio dei campioni agli utenti**|Controlla se i file che potrebbero richiedere ulteriore analisi da parte di Microsoft per determinare se sono dannosi vengono inviati automaticamente a Microsoft.|sì|No
|**File e cartelle da escludere quando si esegue un'analisi o si usa la protezione in tempo reale**|Aggiungere uno o più file e cartelle come **C:\Percorso** o **%ProgramFiles%\Percorso\nomefile.exe** all'elenco delle estensioni. Questi file e cartelle non saranno inclusi nelle analisi in tempo reale o pianificate.|Sì|No
|**Estensioni di file da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiungere uno o più estensioni di file come **jpg** o **txt** all'elenco delle esclusioni. I file con queste estensioni non saranno inclusi nelle analisi in tempo reale o pianificate.|Sì|No
|**Processi da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiungere uno o più processi del tipo **.exe**, **.com** o **.scr** all'elenco delle esclusioni. Questi processi non saranno inclusi nelle analisi in tempo reale o pianificate.|Sì|No| 


### Impostazioni relative agli aggiornamenti

|Nome impostazione|Dettagli|Windows 10 Desktop|Windows 10 Mobile|
|----------------|---------------|----------------------|---------------------|
|**Consenti aggiornamenti automatici**|Abilitare questa impostazione per consentire gli aggiornamenti automatici, quindi configurare una delle impostazioni seguenti per controllare il comportamento di aggiornamento:<br /><br />**Notifica download**<br /><br />**Installa automaticamente durante la manutenzione**<br /><br />**Installa e riavvia automaticamente durante la manutenzione**<br /><br />**Installa e riavvia automaticamente all'ora pianificata** **Nota:** quando questa opzione è selezionata, è possibile configurare anche le seguenti impostazioni: **Elimina le notifiche per l'utente finale** e **Definisci il giorno di installazione per gli aggiornamenti pianificati**.|Sì|No|

## Impostazioni di criteri personalizzati
Usare i **criteri di configurazione personalizzati** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire le impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi Windows 10 e Windows 10 Mobile. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni di Windows 10 che non possono essere configurate con i criteri di configurazione generale di Intune. Per informazioni sulle impostazioni che è possibile configurare con questi criteri, vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Per un elenco delle impostazioni URI OMA che è possibile configurare nei dispositivi Windows 10 registrati, vedere Impostazioni URI personalizzate per i dispositivi Windows 10, più avanti in questo argomento.

### Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio di conformità e altre informazioni rilevanti per consentirne l'individuazione.|

### Impostazioni OMA-URI

|Nome impostazione|Dettagli|
    |--------|--------------------|
    |**Nome impostazione**|Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.|
    |**Descrizione dell'impostazione**|Fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.|
    |**Tipo di dati**|Selezionare il tipo di data in cui si specificherà questa impostazione OMA URI. È possibile scegliere tra:<br /><br />-   **String**<br />-   **String (XML)**<br />-   **Data e ora**<br />-   **Integer**<br />-   **A virgola mobile**<br />-   **Boolean**|
    |**OMA-URI (con distinzione tra maiuscole e minuscole)**|Specificare l'impostazione OMA-URI per cui si desidera fornire un'impostazione.|
    |**Valore**|Specificare il valore da associare all'impostazione OMA-URI specificata in precedenza.|


## Impostazioni URI personalizzate per i dispositivi Windows 10
In questo argomento sono elencate le impostazioni che è possibile configurare per i dispositivi Windows 10 e Windows 10 Mobile nei **criteri personalizzati di Windows 10**..


> [!NOTE]
> Nella colonna **Supporta** della tabella seguente vengono usati i valori seguenti:
> 
> -   **Desktop**: l'impostazione supporta computer Windows 10 Professional ed Enterprise registrati solo con Intune.
> -   **Mobile** : l'impostazione supporta solo per dispositivi Windows Mobile di 10.
> -   **Entrambi** : l'impostazione supporta dispositivi mobili e desktop.
> 
> Tutti i dispositivi devono essere registrati con Intune per poter usare i criteri URI personalizzati di Windows.

### Criteri

|Nome del criterio|Supporta|Dettagli|
|---------------|------------|-----------|
|**​Allow Auto Update**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - **5**<br /><br />**Valore predefinito:** 1|
|**Schedule Install Day**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** - tutti i giorni<br /><br />**1** - domenica<br /><br />**2** - lunedì<br /><br />**3** - martedì<br /><br />**4** - mercoledì<br /><br />**5** - giovedì<br /><br />**6** - venerdì<br /><br />**7** - sabato.<br /><br />**Valore predefinito:** 0|
|**Schedule Install Time**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:ore 0** – **23** (0 corrisponde alla mezzanotte)<br /><br />**Valore predefinito:** 3|
|**DeviceLock/AllowIdleReturnWithoutPassword**|Mobile|**Percorso URI completo:**./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: l'utente non può impostare il timer del periodo di tolleranza della password e il valore è impostato su "ogni ora"<br /><br />**1**: l'utente può impostare il timer del periodo di tolleranza della password<br /><br />**Valore predefinito:** 1|
|**Wi-Fi/AllowWiFi**|Mobile|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: non consente **l'uso della connessione Wi-Fi**.<br /><br />**1**: consente **l'uso della connessione Wi-Fi**.<br /><br />**Valore predefinito:** 1|
|**Wi-Fi/AllowInternetSharing**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consente la condivisione Internet.<br /><br />**1** : consente la condivisione Internet.<br /><br />**Valore predefinito:** 1|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**|Entrambi|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**WiFi/AllowManualWiFiConfiguration**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: non sono consentite connessioni Wi-Fi oltre a quelle con provisioning MDM.<br /><br />**1** : consente l'aggiunta di nuovi SSID di rete oltre quelli con provisioning MDM.<br /><br />**Valore predefinito:** 1|
|**System/AllowLocation**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**System/AllowTelemetry**|Entrambi|**Percorso URI completo:**/Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito (solo impostazione aziendale)<br /><br />**1** : limitato<br /><br />**2** : completo<br /><br />**3**: completo e informazioni sulla diagnostica<br /><br />**Valore predefinito:** 2|
|**System/AllowExperimentation**|Entrambi|**Percorso URI completo:**./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1**: solo le impostazioni<br /><br />**2**: impostazioni e sperimentazione<br /><br />**Valore predefinito:** 1|
|**Security/AntiTheftMode**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: non consente la modalità AntiTheft<br /><br />**1** : preferenza utente<br /><br />**Valore predefinito:** 1|
|**Connectivity/AllowUSBConnection**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**System/AllowUserToResetPhone**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Connectivity/AllowCellularDataRoaming**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Connectivity/AllowVPNOverCellular**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: la VPN non è consentita sulla connessione cellulare<br /><br />**1** : la VPN può usare qualsiasi connessione inclusa quella cellulare.<br /><br />**Valore predefinito:** 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Connectivity/AllowVPNRoamingOverCellular**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Connectivity/AllowBluetooth**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: non consente all'utente di attivare la funzione Bluetooth.<br /><br />**1**: riservato. L'utente può attivare e configurare la funzione Bluetooth (non supportato in Windows Phone 8.1 per MDM, EAS, Windows 10 Desktop o Windows 10 Mobile)<br /><br />**2**: consentito. L'utente può attivare e configurare la funzione Bluetooth.<br /><br />**Valore predefinito:** 2|
|**Experience/AllowScreenCapture**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Experience/AllowTaskSwitcher**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Experience/AllowVoiceRecording**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Experience/AllowSyncMySettings**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentire il roaming<br /><br />**1** : consentire il roaming<br /><br />**Valore predefinito:** 1|
|**Experience/AllowManualMDMUnenrollment**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Accounts/AllowMicrosoftAccountConnection**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Security/AllowManualRootCertificateInstallation**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Security/AllowAddProvisioningPackages**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Search/DisableBackoff**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 0|
|**Search/PreventRemoteQueries**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 1|
|**Search/AllowUsingDiacritics**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 0|
|**Search/AlwaysUseAutoLangDetection**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 0|
|**Search/DisableRemovableDriveIndexing**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 0|
|**Search/PreventIndexingLowDiskSpaceMB**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 1|
|**Search/AllowIndexingEncryptedStoresOrItems**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 0|
|**Security/AllowRemoveProvisioningPackage**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Security/RequireProvisioningPackageSignature**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**<br /><br />**1**<br /><br />**Valore predefinito:** 0|
|**AboveLock/AllowActionCenterNotifications**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**TextInput/AllowIMENetworkAccess**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consente<br /><br />Open Extended Dictionary è disattivato.<br /><br />Un utente non può:<br /><br />Aggiungere un nuovo Open Extended Dictionary<br /><br />Aggiungere un nuovo file di configurazione di integrazione di ricerca<br /><br />Usare la funzionalità per i candidati dal cloud<br /><br />Inviare parole registrate dall'utente<br /><br />Inoltre:<br /><br />Un Open Extended Dictionary aggiunto prima di abilitare questa impostazione di criteri non viene usato per la conversione.<br /><br />Non viene usato un file di configurazione di integrazione di ricerca installato prima di abilitare questa impostazione di criteri.<br /><br />**1**: consenti<br /><br />Open Extended Dictionary può essere aggiunto e usato per impostazione predefinita. Inoltre, la funzione di integrazione ricerca può essere usata per impostazione predefinita.<br /><br />Un utente può:<br /><br />Usare la funzionalità per i candidati dal cloud<br /><br />Inviare parole registrate dall'utente<br /><br />**Valore predefinito:**|
|**TextInput/AllowKoreanExtendedHanja**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowKoreanExtendedHanja<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**TextInput/AllowIMELogging**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: la registrazione di conversioni errate è disabilitata. I dati ottimizzati automaticamente e i dati della cronologia di input non vengono salvati in un file.<br /><br />**1**: la registrazione di conversioni errate è abilitata. I dati ottimizzati automaticamente e i dati della cronologia di input vengono salvati in un file.<br /><br />**Valore predefinito:** 1|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**TextInput/AllowJapaneseIVSCharacters**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**TextInput/AllowJapaneseUserDictionary**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: tutti i caratteri vengono filtrati tranne JIS<br /><br />**1**: nessun carattere viene filtrato<br /><br />**Valore predefinito:** 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: tutti i caratteri vengono filtrati tranne JIS0208<br /><br />**1**: nessun carattere viene filtrato<br /><br />**Valore predefinito:** 1|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: tutti i caratteri vengono filtrati tranne JIS0208 o EUDC<br /><br />**1**: nessun carattere viene filtrato.<br /><br />**Valore predefinito:** 1|
|**TextInput/AllowInputPanel**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Bluetooth/AllowDiscoverableMode**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Bluetooth/AllowAdvertising**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowDataSense**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowVPN**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowWorkplace**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowDateTime**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowLanguage**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowRegion**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowSignInOptions**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowYourAccount**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowPowerSleep**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Settings/AllowAutoPlay**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Experience/AllowCortana**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Search/SafeSearchPermissions**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : rigido, filtro massimo del contenuto per adulti<br /><br />**1** : moderato, filtro moderato del contenuto per adulti (i risultati di ricerca validi non verranno filtrati)<br /><br />**Valore predefinito:** 1|
|**Experience/AllowCopyPaste**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**Force Start Size**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: consente all'utente di modificare le dimensioni<br /><br />**1**: forza la modalità non a schermo non intero<br /><br />**2**: forza la modalità a schermo intero<br /><br />**Valore predefinito:** 0|
|**Update/RequireDeferUpgrade**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: non rinvia l'aggiornamento (rimane nel Current Branch, CB)<br /><br />**1**: abilita il rinvio degli aggiornamenti (il dispositivo segue le regole del Current Branch for Business, CBB)<br /><br />**Valore predefinito:0**<br /><br />Per altre informazioni, vedere:<br /><br />[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Piano per la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpdatePeriod**|Entrambi|**Descrizione:** criterio per rinviare gli aggiornamenti software per un massimo di 4 settimane<br /><br />**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:** 0 - applica gli aggiornamenti immediatamente; 1-4 - numero di settimane di rinvio degli aggiornamenti software.<br /><br />**Valore predefinito:0**<br /><br /><br />Per altre informazioni, vedere:<br /><br />[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Piano per la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/DeferUpgradePeriod**|Entrambi|**Descrizione:** criterio per rinviare gli aggiornamenti delle funzionalità per un massimo di 8 mesi<br /><br />**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:** 0 - applica gli aggiornamenti immediatamente; 1-8 - numero di mesi di rinvio degli aggiornamenti delle funzioni.<br /><br />**Valore predefinito:0**<br /><br />Per altre informazioni, vedere:<br /><br />[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226(v=vs.85).aspx)<br /><br />[Piano per la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241(v=vs.85).aspx)|
|**Update/PauseDeferrals**|Entrambi|**Descrizione:** consente a un computer CBB di non ricevere più gli aggiornamenti per 5 settimane. Usare questo criterio in caso di problemi con un aggiornamento.<br /><br />**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br /><br />**1**: sospendi gli aggiornamenti (scade dopo 5 settimane)<br /><br />**Valore predefinito:0**|

### Windows Defender

|Nome del criterio|Supporta|Dettagli|
|---------------|------------|-----------|
|**AllowRealtimeMonitoring**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**AllowBehaviorMonitoring**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**AllowIntrusionPreventionSystem**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**AllowIOAVProtection**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**AllowScriptScanning**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**AllowOnAccessProtection**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**RealTimeScanDirection**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: esegue il monitoraggio di tutti i file (bidirezionale)<br /><br />**1** : esegue il monitoraggio dei file in ingresso<br /><br />**2** : esegue il monitoraggio dei file in uscita<br /><br />**Valore predefinito:** 0|
|**DaysToRetainCleanedMalware**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - **90**. Indica per quanto tempo il malware verrà conservato<br /><br />**Valore predefinito:** 0. Conserva per sempre il malware nella cartella della quarantena e non lo rimuove automaticamente|
|**AllowUserUIAccess**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**ScanParameter**|Desktop|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**1** : analisi veloce<br /><br />**2**: analisi completa<br /><br />**Valore predefinito:** 1|
|**ScheduleScanDay**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: tutti i giorni<br /><br />**1**: lunedì<br /><br />**2**: martedì<br /><br />**3**: mercoledì<br /><br />**4**: giovedì<br /><br />**5**: venerdì<br /><br />**6**: sabato<br /><br />**7**: domenica<br /><br />**8** : nessuna analisi pianificata<br /><br />**Valore predefinito:** 0|
|**ScheduleScanTime**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** – 12:00<br /><br />**60** – 1:00<br /><br />**120** – 2:00<br /><br />**180** – 3:00<br /><br />**240** – 4:00<br /><br />**300** – 5:00<br /><br />**360** – 6:00<br /><br />**420** – 7:00<br /><br />**480** – 8:00<br /><br />**540** – 9:00<br /><br />**600** – 10:00<br /><br />**660** – 11:00<br /><br />**720** – 12:00<br /><br />**780** – 13:00<br /><br />**840** – 14:00<br /><br />**900** – 15:00<br /><br />**960** – 16:00<br /><br />**1020** – 17:00<br /><br />**1080** – 18:00<br /><br />**1140** – 19:00<br /><br />**1200** – 20:00<br /><br />**1260** – 21:00<br /><br />**1320** – 22:00<br /><br />**1381** -Finestra di manutenzione<br /><br />**Valore predefinito:** 120|
|**ScheduleQuickScanTime**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** – 12:00<br /><br />**60** – 1:00<br /><br />**120** – 2:00<br /><br />**180** – 3:00<br /><br />**240** – 4:00<br /><br />**300** – 5:00<br /><br />**360** – 6:00<br /><br />**420** – 7:00<br /><br />**480** – 8:00<br /><br />**540** – 9:00<br /><br />**600** – 10:00<br /><br />**660** – 11:00<br /><br />**720** – 12:00<br /><br />**780** – 13:00<br /><br />**840** – 14:00<br /><br />**900** – 15:00<br /><br />**960** – 16:00<br /><br />**1020** – 17:00<br /><br />**1080** – 18:00<br /><br />**1140** – 19:00<br /><br />**1200** – 20:00<br /><br />**1260** – 21:00<br /><br />**1320** – 22:00<br /><br />**1380** – 22:00<br /><br />**Valore predefinito:** 120|
|**AVGCPULoadFactor**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - **100**<br /><br />**Valore predefinito:** 50|
|**AllowArchiveScanning**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**AllowEmailScanning**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 0|
|**AllowFullScanRemovableDriveScanning**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 0|
|**AllowFullScanOnMappedNetworkDrives**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**AllowScanningNetworkFiles**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1. Se impostato su consentito, viene eseguito quando RTP è attivo|
|**SignatureUpdateInterval**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non controlla le firme in un intervallo<br /><br />**1**: controlla le firme ogni ora<br /><br />**2** : controlla le firme ogni due ore<br /><br />**24** : controlla le firme ogni giorno<br /><br />**Valore predefinito:** 8. Controlla le firme ogni otto ore|
|**AllowCloudProtection**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : non consentito<br /><br />**1** : consentito<br /><br />**Valore predefinito:** 1|
|**SubmitSamplesConsent**|Desktop|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0** : richiedere sempre<br /><br />**1** : inviare campioni sicuri automaticamente<br /><br />**2** : non inviare mai<br /><br />**3** : inviare tutti i campioni automaticamente<br /><br />**Valore predefinito:** 0|
|**ExcludedExtensions**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:**<br /><br />*&lt;elenco di estensioni separate da punto e virgola&gt;* ad esempio **obj;lib**<br /><br />**Valore predefinito:** nessuna estensione viene esclusa|
|**ExcludedPaths**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:**<br /><br />*&lt;elenco di percorsi separati da punto e virgola&gt;*<br /><br />Esempio: **c:\test;c:\test1.exe**<br /><br />**Valore predefinito:** nessun percorso viene escluso|
|**ExcludedProcesses**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:**<br /><br />*&lt;elenco di percorsi separati da punto e virgola&gt;*<br /><br />Esempio: **c:\test.exe;c:\test1.exe**<br /><br />**Valore predefinito:** nessun processo viene escluso|

### Browser Edge

|Nome del criterio|Supporta|Dettagli|
|---------------|------------|-----------|
|**Allow Browser**|Mobile|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - l'esplorazione è disattivata; **1** - l'esplorazione è attivata.<br /><br />**Valore predefinito:** 1|
|**AllowSearchSuggestionsinAddressBar**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - non visualizza i suggerimenti di ricerca; **1** - visualizza i suggerimenti di ricerca.<br /><br />**Valore predefinito:** 1|
|**SendIntranetTraffictoInternetExplorer**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - disabilitato (apre i siti Intranet nel browser Edge); **1** - abilitato (apre i siti Intranet in Internet Explorer).<br /><br />**Valore predefinito:** 0|
|**Allow Do Not Track**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - disabilitato (DNT non inviato);  **1** - abilitato (invia DNT)<br /><br />**Valore predefinito:** 0|
|**Configure SmartScreen**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - non consentire;  **1** - consenti<br /><br />**Valore predefinito:** 1|
|**Allow Pop-ups**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - blocca popup; **1** - consenti popup<br /><br />**Valore predefinito:** 0|
|**Allow Cookies**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowTheme<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - non bloccare, consenti i cookie da tutti i siti Web; **1** - blocca solo i cookie di terze parti; **2** - blocca tutti i cookie<br /><br />**Valore predefinito:** 0|
|**Allow Save Password**|Entrambi|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - lo strumento per la gestione delle password è disabilitato; <br />                        **1** - lo strumento per la gestione delle password è abilitato<br /><br />**Valore predefinito:** 1|
|**Consenti riempimento automatico**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - disabilitato; **1** - abilitato<br /><br />**Valore predefinito:** 0|
|**Configure Enterprise Site List**|Desktop|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:0** - non configurato; **1** - usa l'elenco dei siti della modalità Enterprise di IE se è configurato; **2** - consente di specificare il percorso dell'elenco dei siti della modalità Enterprise<br /><br />**Valore predefinito:** 1|

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO1-->


