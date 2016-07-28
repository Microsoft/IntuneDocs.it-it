---
title: Impostazioni dei criteri di Windows 10 | Microsoft Intune
description: Usare le impostazioni dei criteri indicate nell'argomento come aiuto per configurare le impostazioni personalizzate integrate per dispositivi registrati Windows 10 Desktop e Windows 10 Mobile.
keywords: 
author: robstackmsft
manager: arob98
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 01356d08257cf381d1a981f749702800c173de33
ms.openlocfilehash: 08336c56f4e099c8cd0a0152364824455cae0f03


---

# Impostazioni dei criteri di Windows 10 in Microsoft Intune

Usare le impostazioni dei criteri indicate nell'argomento per configurare le impostazioni personalizzate integrate per dispositivi registrati Windows 10 Desktop e Windows 10 Mobile.

> [!IMPORTANT]
> È possibile gestire i PC Windows 10 in due modi: registrandoli o installando il software client per PC di Intune. Ciascun metodo offre diverse funzionalità. Per altre informazioni, vedere [Scegliere come gestire i dispositivi](/intune/get-started/choose-how-to-manage-devices).
> Quando si gestiscono i PC Windows 10 con il software client per PC di Intune, non è possibile usare i criteri e le impostazioni descritte in questo argomento. Per applicare queste impostazioni, i dispositivi Windows 10 devono essere registrati con Intune.

## Impostazioni dei criteri di configurazione generali

Usare i **criteri di configurazione generale** di Microsoft Intune per Windows 10 per configurare le impostazioni generali per dispositivi registrati Windows 10 Desktop e Mobile. 


### Password

|Nome impostazione|Dettagli|
|----------------|----------------------|
|**Richiedi una password per sbloccare i dispositivi**|Richiede una password nei dispositivi supportati.|
|**Tipo di password richiesto**|Specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico|
|**Tipo di password richiesto** - **Numero minimo di set di caratteri**|Sono disponibili quattro set di caratteri, lettere minuscole, lettere maiuscole, numeri e simboli. L'impostazione specifica quanti set di caratteri diversi è necessario includere nella password.|
|**Lunghezza minima password**|Specifica il numero minimo di caratteri che la password del dispositivo deve contenere.<br>(Solo Windows 10 Mobile)|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Cancella il dispositivo se questo numero di tentativi di accesso ha esito negativo.|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica per quanto tempo il dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.|
|**Scadenza password (giorni)**|Specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo.|
|**Ricorda cronologia password**|Specifica se si vuole impedire all'utente finale di creare password già usate in precedenza.|
|**Ricorda cronologia password** - **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare.|
|**Consenti password grafica e PIN**|Consente di usare movimenti semplici su un'immagine o un semplice PIN per effettuare l'accesso.<br>(Solo Windows 10 Desktop)|
|**Richiedi una password quando il dispositivo torna attivo dopo uno stato di inattività**|Se abilitata, l'utente deve inserire una password per sbloccare il dispositivo dallo stato inattivo.<br>(Solo Windows 10 Mobile)|

### Crittografia

|Nome impostazione|Dettagli|
|----------------|----------------------|
|**Richiedi crittografia sui dispositivi mobili**|Abilita la crittografia sui dispositivi di destinazione.<br>(Solo Windows 10 Mobile)|

### Sistema

|Nome impostazione|Dettagli|
|----------------|----------------------|
|**Consenti acquisizione schermo**|Consente all'utente di acquisire la schermata del dispositivo come immagine.<br>(Solo Windows 10 Mobile)|
|**Consenti l'annullamento della registrazione manuale**|Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.|
|**Consenti installazione manuale del certificato radice**|Specifica se l'utente può installare manualmente i certificati radice.<br>(Solo Windows 10 Mobile)|
|**Consenti l'invio di dati di utilizzo e di diagnostica a Microsoft**|Determina la quantità di dati diagnostici e di utilizzo che vengono inviati a Microsoft dai dispositivi.<br><br>**No** - Non vengono inviati dati a Microsoft<br>**Base** - Il dispositivo invia solo informazioni limitate a Microsoft<br>**Avanzati** -Invia dati di diagnostica avanzati a Microsoft<br>**Completi (scelta consigliata)** -Invia gli stessi dati di **Avanzati**, più dati aggiuntivi sullo stato del dispositivo|


### Account e sincronizzazione

|Nome impostazione|Dettagli|
|----------------|----------------------|---------------------|
|**Consenti account Microsoft**|Consente all'utente di associare un account Microsoft con il dispositivo.|
|**Consenti aggiunta manuale di account non Microsoft**|Consente all'utente di aggiungere account di posta elettronica al dispositivo che non sono associati con un account Microsoft.|
|**Consenti sincronizzazione delle impostazioni per gli account Microsoft**|Consente che le impostazioni del dispositivo e delle app associate con un account Microsoft vengano sincronizzate fra i dispositivi.|

### Impostazioni di posta elettronica

|Nome impostazione|Dettagli|
|----------------|----------------------|---------------------|
|**Rendi l'account Microsoft facoltativo nell'applicazione Windows Mail**|Configura l'opzione in modo da rimuovere il requisito per un account Microsoft in Windows Mail.<br>Solo Windows 10 Desktop|



### Microsoft Edge

|Nome impostazione|Dettagli|
|----------------|----------------------|
|**Consenti browser Web**|Consente l'uso del browser Web Edge sul dispositivo.<br>(Solo Windows 10 Mobile)|
|**Consenti suggerimenti di ricerca nella barra degli indirizzi**|Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca.|
|**Consenti l'invio di traffico Intranet a Internet Explorer**|Consente agli utenti di aprire siti Web sulla Intranet in Internet Explorer.<br>(Solo Windows 10 Desktop)|
|**Consenti Do Not Track**|Configura il browser Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti.|
|**Attiva SmartScreen**|Abilita l'impostazione SmartScreen del browser sui dispositivi.|
|**Consenti scripting**|Consente di eseguire script, ad esempio JavaScript, nel browser Edge.|
|**Consenti popup**|Attiva o disattiva il blocco popup del browser.<br>(Solo Windows 10 Desktop)|
|**Consenti cookie**|Consente o disattiva i cookie.|
|**Consenti riempimento automatico**|Consente all'utente di modificare le impostazioni di completamento automatico nel browser.<br>(Solo Windows 10 Desktop)|
|**Consenti strumento per la gestione delle password**|Abilita o disabilita la funzione di gestione password di Edge.|
|**Posizione elenco siti modalità Enterprise**|Specifica dove trovare l'elenco di siti Web che verranno aperti in modalità Enterprise. L'elenco non è modificabile dagli utenti.<br>(Solo Windows 10 Desktop)|

### App

|Nome impostazione|Dettagli|
|----------------|----------------------|---------------------|
|**Consenti archivio applicazioni**|Consente all'utente di accedere all'App Store sul dispositivo.<br>(Solo Windows 10 Mobile)|



### Cellulare

|Nome impostazione|Dettagli|
|----------------|----------------------|---------------------|
|**Consenti dati in roaming**|Consente il roaming tra reti quando si accede a dati.|
|**Consenti VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è collegato a una rete cellulare.|
|**Consenti roaming VPN su rete cellulare**|Controlla se il dispositivo può accedere a connessioni VPN quando è in roaming su una rete cellulare.|

### Hardware

|Nome impostazione|Dettagli|
|----------------|----------------------|
|**Consenti dispositivo foto/video**|Specifica se è consentito l'uso della fotocamera del dispositivo.|
|**Consenti archivi rimovibili**|Specifica se è possibile usare dispositivi di archiviazione esterni come le schede SD con il dispositivo.|
|**Consenti Wi-Fi**|Consente l'uso delle funzionalità Wi-Fi dei dispositivi.<br>(Solo Windows 10 Mobile)|
|**Consenti Internet condiviso**|Consente l'uso della condivisione della connessione Internet sul dispositivo.|
|**Consenti configurazione Wi-Fi manuale**|Controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi.<br>(Solo Windows 10 Mobile)|
|**Consenti connessione automatica agli hotspot Wi-Fi gratuiti**|Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione.|
|**Consenti georilevazione**|Specifica se il dispositivo può usare le informazioni dei servizi di posizione.|
|**Consenti NFC**|Consente al dispositivo di usare le sue capacità NFC (Near Field Communication).|
|**Consenti Bluetooth**|Consente l'uso delle capacità Bluetooth sul dispositivo.|
|**Consenti modalità individuabile Bluetooth**|Consente che il dispositivo sia scoperto da altri dispositivi con la funzione Bluetooth attivata.|
|**Consenti annunci con Bluetooth**|Consente ai dispositivi di ricevere annunci tramite Bluetooth.|
|**Consenti modalità di connessione Bluetooth**|**Importante:** questa impostazione non è più supportata in Windows 10 e verrà rimossa in futuro.|
|**Consenti ripristino del telefono**|Controlla se l'utente può ripristinare le impostazioni predefinite nel dispositivo.|
|**Consenti connessione USB**|Controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni mediante una connessione USB.|
|**Consenti modalità AntiTheft**|Consente di configurare l'abilitazione della modalità Antitheft di Windows.|

### Caratteristiche

|Nome impostazione|Dettagli|
|----------------|----------------------|---------------------|
|**Consenti copia e incolla**|Abilita o disabilita l'uso del copia e incolla sul dispositivo.<br>(Solo Windows 10 Mobile)|
|**Consenti registrazione vocale**|Abilita o disabilita la funzione di registrazione locale sul dispositivo.<br>(Solo Windows 10 Mobile)|
|**Consenti Cortana**|Abilita o disabilita l'assistente vocale Cortana.|
|**Consenti notifiche del Centro operativo**|Abilita o disabilita le notifiche del Centro operativo sulla schermata di blocco del dispositivo.<br>(Solo Windows 10 Mobile)|

### Defender

Tutte le impostazioni sono solo per Windows 10 Desktop.

|Nome impostazione|Dettagli|
|-|-|
|**Consenti monitoraggio in tempo reale**|Abilita l'analisi in tempo reale per malware, spyware e altro software indesiderato.|
|**Consenti monitoraggio comportamento**|Consente a Defender di individuare determinati modelli di attività sospette nei dispositivi.|
|**Abilita Network Inspection System**|Network Inspection System (NIS) contribuisce a proteggere i dispositivi dagli exploit basati sulla rete usando le firme di vulnerabilità note di Microsoft Endpoint Protection Center per contribuire a rilevare e bloccare il traffico dannoso.|
|**Analizza tutti i download**|Controlla se Defender deve analizzare tutti i file scaricati da Internet.|
|**Consenti analisi script**|Consente a Defender di analizzare gli script usati in Internet Explorer.|
|**Monitora l'attività di file e programmi**|Abilitare questa impostazione per consentire a Defender di monitorare l'attività di file e programmi nei dispositivi.|
|**Giorni di rilevamento del malware risolto**|Consente a Defender di continuare a monitorare il malware risolto per il numero di giorni specificato, in modo che sia possibile controllare manualmente i dispositivi colpiti in precedenza. Se si imposta il numero di giorni su **0**, il malware rimane nella cartella della quarantena e non viene rimosso automaticamente. |
|**Consenti accesso all'interfaccia utente client**|Controlla se l'interfaccia utente di Windows Defender è nascosta agli utenti finali.<br>Quando questa impostazione viene modificata, ha effetto dal successivo avvio del PC da parte dell'utente finale.|
|**Pianifica analisi veloce giornaliera**|Consente di pianificare un'analisi veloce che viene eseguita giornalmente all'ora selezionata.|
|**Pianifica analisi del sistema**|Consente di pianificare un'analisi completa o veloce del sistema che si verifica regolarmente il giorno e all'ora selezionati.|
|**Limita utilizzo CPU durante un'analisi a**|Consente di limitare la quantità di CPU usata per le analisi (da **1** a **100**)|
|**Analizza file di archivio**|Consente a Defender di analizzare i file archiviati come i file Zip o Cab.|
|**Analisi dei messaggi di posta elettronica**|Consente a Defender di analizzare i messaggi di posta elettronica non appena arrivano sul dispositivo.|
|**Analizza unità rimovibili**|Consente a Defender di analizzare le unità removibili come le chiavette le USB.|
|**Analizza unità di rete mappate**|Consente a Defender di analizzare i file nelle unità di rete mappate.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|
|**Analizza file aperti da cartelle di rete condivise**|Consente a Defender di analizzare i file sulle unità di rete condivise, ad esempio quelli a cui si accede da un percorso UNC.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.|
|**Intervallo di aggiornamento della firma**|Specifica l'intervallo secondo il quale Defender controllerà i nuovi file di firma.|
|**Consenti protezione cloud**|Consente o blocca la ricezione di informazioni sull'attività del malware da parte di Microsoft Active Protection Service dai dispositivi gestiti. Queste informazioni vengono usate per migliorare il servizio in futuro.|
|**Richiedi invio dei campioni agli utenti**|Controlla se i file che potrebbero richiedere ulteriore analisi da parte di Microsoft per determinare se sono dannosi vengono inviati automaticamente a Microsoft.|
|**Rilevamento di applicazioni potenzialmente indesiderate**|Questa impostazione può essere usata per proteggere i dispositivi desktop Windows registrati da eventuale software in esecuzione classificato da Windows Defender come potenzialmente indesiderato. È possibile ottenere protezione da tali applicazioni in esecuzione o usare la modalità di controllo per rilevare l'installazione di un'applicazione potenzialmente indesiderata.|
|**File e cartelle da escludere quando si esegue un'analisi o si usa la protezione in tempo reale**|Aggiungere uno o più file e cartelle come **C:\Percorso** o **%ProgramFiles%\Percorso\nomefile.exe** all'elenco delle estensioni. Questi file e cartelle non saranno inclusi nelle analisi in tempo reale o pianificate.|
|**Estensioni di file da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiungere uno o più estensioni di file come **jpg** o **txt** all'elenco delle esclusioni. I file con queste estensioni non saranno inclusi nelle analisi in tempo reale o pianificate.|
|**Processi da escludere durante l'esecuzione di un'analisi o l'utilizzo della protezione in tempo reale**|Aggiungere uno o più processi del tipo **.exe**, **.com** o **.scr** all'elenco delle esclusioni. Questi processi non saranno inclusi nelle analisi in tempo reale o pianificate.| 


### Impostazioni relative agli aggiornamenti

|Nome impostazione|Dettagli|
|----------------|---------------|
|**Consenti aggiornamenti automatici**|Abilitare questa impostazione per consentire gli aggiornamenti automatici, quindi configurare una delle impostazioni seguenti per controllare il comportamento di aggiornamento:<br /><br />**Notifica download**<br /><br />**Installa automaticamente durante la manutenzione**<br /><br />**Installa e riavvia automaticamente durante la manutenzione**<br /><br />**Installa e riavvia automaticamente all'ora pianificata** **Nota:** quando è selezionata questa opzione è possibile configurare anche le impostazioni seguenti: **Elimina la notifica per l'utente finale** e **Definire il giorno di installazione per gli aggiornamenti pianificati**.<br>(Solo Windows 10 Desktop)|

## Impostazioni di criteri personalizzati
Usare i **criteri di configurazione personalizzati** di Microsoft Intune per Windows 10 e Windows 10 Mobile per distribuire le impostazioni URI OMA (Open Mobile Alliance Uniform Resource Identifier) che possono essere usate per controllare le funzionalità nei dispositivi Windows 10 e Windows 10 Mobile. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni di Windows 10 che non possono essere configurate con i criteri di configurazione generale di Intune.



### Impostazioni generali dei criteri personalizzati

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio di conformità e altre informazioni rilevanti per consentirne l'individuazione.|

### Impostazioni URI OMA dei criteri personalizzati

|Nome impostazione|Dettagli|
    |--------|--------------------|
    |**Nome impostazione**|Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.|
    |**Descrizione dell'impostazione**|Fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.|
    |**Tipo di dati**|Selezionare il tipo di data in cui si specificherà questa impostazione OMA URI. È possibile scegliere tra:<br /><br />-   **String**<br />-   **String (XML)**<br />-   **Data e ora**<br />-   **Integer**<br />-   **A virgola mobile**<br />-   **Boolean**|
    |**OMA-URI (con distinzione tra maiuscole e minuscole)**|Specificare l'impostazione OMA-URI per cui si desidera fornire un'impostazione.|
    |**Valore**|Specificare il valore da associare all'impostazione OMA-URI specificata in precedenza.|


## Impostazioni URI personalizzate per i dispositivi Windows 10
In questo argomento sono elencate le impostazioni che è possibile configurare per i dispositivi Windows 10 e Windows 10 Mobile nei **criteri personalizzati di Windows 10** di Microsoft Intune.

Tutti i dispositivi devono essere registrati con Intune per poter usare i criteri URI personalizzati di Windows.

### Impostazioni URI dei criteri

|Nome criteri|Dettagli|
|---------------|------------|-----------|
|**​Allow Auto Update**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** - **5** (impostazione predefinita: **1**)|
|**Schedule Install Day**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** - Tutti i giorni (impostazione predefinita)<br>**1** - domenica<br>**2** - lunedì<br>**3** - martedì<br>**4** - mercoledì<br>**5** - giovedì<br>**6** - venerdì<br>**7** - sabato|
|**Schedule Install Time**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** – **23** ore (**0** corrisponde a mezzanotte) (impostazione predefinita: **3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>(solo Mobile)|**Percorso URI completo:**./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: l'utente non può impostare il timer del periodo di tolleranza della password e il valore è impostato su "ogni ora"<br>**1** - l'utente può impostare il timer del periodo di tolleranza della password (impostazione predefinita)|
|**Wi-Fi/AllowWiFi**<br>(solo Mobile)|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non consente **l'uso della connessione Wi-Fi**.<br>**1**: **consente l'uso della connessione Wi-Fi** (impostazione predefinita)|
|**Wi-Fi/AllowInternetSharing**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consente la condivisione Internet.<br>**1**: consente la condivisione Internet (impostazione predefinita)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>(Desktop e Mobile)|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**WiFi/AllowManualWiFiConfiguration**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non sono consentite connessioni Wi-Fi oltre a quelle con provisioning MDM.<br>**1**: consente l'aggiunta di nuovi SSID di rete oltre a quelli con provisioning MDM (impostazione predefinita)|
|**System/AllowLocation**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/System/AllowLocation<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**System/AllowTelemetry**<br>(Desktop e Mobile)|**Percorso URI completo:**/Vendor/MSFT/Policy/Config/System/AllowTelemetry<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito (solo impostazione aziendale)<br>**1** : limitato<br>**2**: completo (impostazione predefinita)<br>**3**: completo e informazioni sulla diagnostica|
|**System/AllowExperimentation**<br>(Desktop e Mobile)|**Percorso URI completo:**./Vendor/MSFT/Policy/Config/System/AllowExperimentation<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: solo impostazioni (impostazione predefinita)<br>**2**: impostazioni e sperimentazione|
|**Security/AntiTheftMode**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AntiTheftMode<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non consente la modalità AntiTheft<br>**1**: preferenza utente (impostazione predefinita)|
|**Connectivity/AllowUSBConnection**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**System/AllowUserToResetPhone**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Connectivity/AllowCellularDataRoaming**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Connectivity/AllowVPNOverCellular**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: la VPN non è consentita sulla connessione cellulare<br>**1**: la VPN può usare qualsiasi connessione, inclusa la connessione cellulare (impostazione predefinita)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Connectivity/AllowBluetooth**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non consente all'utente di attivare la funzione Bluetooth.<br>**1**: riservato. L'utente può attivare e configurare la funzione Bluetooth (non supportato in Windows Phone 8.1 per MDM, EAS, Windows 10 Desktop o Windows 10 Mobile)<br>**2**: consentito. L'utente può attivare e configurare la funzione Bluetooth (impostazione predefinita)|
|**Experience/AllowScreenCapture**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Experience/AllowTaskSwitcher**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Experience/AllowVoiceRecording**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Experience/AllowSyncMySettings**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentire il roaming<br>**1**: consenti il roaming (impostazione predefinita)|
|**Experience/AllowManualMDMUnenrollment**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Accounts/AllowMicrosoftAccountConnection**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Security/AllowManualRootCertificateInstallation**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Security/AllowAddProvisioningPackages**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Search/DisableBackoff**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/DisableBackoff<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** (impostazione predefinita)<br>**1**|
|**Search/PreventRemoteQueries**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**<br>**1** (impostazione predefinita)|
|**Search/AllowUsingDiacritics**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br> **0** (impostazione predefinita)<br>**1**|
|**Search/AlwaysUseAutoLangDetection**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** (impostazione predefinita)<br>**1**|
|**Search/DisableRemovableDriveIndexing**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** (impostazione predefinita)<br>**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**<br>**1** (impostazione predefinita)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** (impostazione predefinita)<br>**1**|
|**Security/AllowRemoveProvisioningPackage**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Security/RequireProvisioningPackageSignature**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** (impostazione predefinita)<br>**1**|
|**AboveLock/AllowActionCenterNotifications**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**TextInput/AllowIMENetworkAccess**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consente<br>Open Extended Dictionary è disattivato.<br>Un utente non può:<br>Aggiungere un nuovo Open Extended Dictionary<br /><br />Aggiungere un nuovo file di configurazione di integrazione di ricerca<br>Usare la funzionalità per i candidati dal cloud<br>Inviare parole registrate dall'utente<br>Inoltre:<br>Un Open Extended Dictionary aggiunto prima di abilitare questa impostazione di criteri non viene usato per la conversione.<br>Non viene usato un file di configurazione di integrazione di ricerca installato prima di abilitare questa impostazione di criteri.<br>**1**: consenti<br>Open Extended Dictionary può essere aggiunto e usato per impostazione predefinita. Inoltre, la funzione di integrazione ricerca può essere usata per impostazione predefinita.<br>Un utente può:<br>Usare la funzionalità per i candidati dal cloud<br>Inviare parole registrate dall'utente.|
|**TextInput/AllowIMELogging**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: la registrazione di conversioni errate è disabilitata. I dati ottimizzati automaticamente e i dati della cronologia di input non vengono salvati in un file.<br>**1**: la registrazione di conversioni errate è abilitata. I dati ottimizzati automaticamente e i dati della cronologia di input vengono salvati in un file (impostazione predefinita)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseIVSCharacters**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseUserDictionary**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri Shift JIS|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br /><br />**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri JIS0208|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: nessun carattere viene filtrato (impostazione predefinita)<br>**1**: tutti i caratteri vengono filtrati, ad eccezione dei caratteri JIS0208 o EUDC|
|**TextInput/AllowInputPanel**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Bluetooth/AllowDiscoverableMode**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Bluetooth/AllowAdvertising**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowDataSense**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowDataSense<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowVPN**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowVPN<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowWorkplace**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowDateTime**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowDateTime<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowLanguage**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowLanguage<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowRegion**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowRegion<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowSignInOptions**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowYourAccount**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowPowerSleep**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Settings/AllowAutoPlay**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Experience/AllowCortana**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowCortana<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Search/SafeSearchPermissions**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : rigido, filtro massimo del contenuto per adulti<br>**1**: moderato, filtro moderato del contenuto per adulti, i risultati di ricerca validi non verranno filtrati (impostazione predefinita)|
|**Experience/AllowCopyPaste**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**Force Start Size**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Start/ForceStartSize<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: consente all'utente di modificare le dimensioni (impostazione predefinita)<br>**1**: forza la modalità non a schermo non intero<br>**2**: forza la modalità a schermo intero|
|**Update/RequireDeferUpgrade**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non rinvia l'aggiornamento, rimane nel Current Branch, CB (impostazione predefinita)<br>**1**: abilita il rinvio degli aggiornamenti (il dispositivo segue le regole del Current Branch for Business, CBB)<br /><br />Per altre informazioni, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Piano per la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>(Desktop e Mobile)|**Descrizione:** criterio per rinviare gli aggiornamenti software per un massimo di 4 settimane<br /><br />**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br> **0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**-**4**: numero di settimane di rinvio degli aggiornamenti software.<br /><br />Per altre informazioni, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Piano per la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>(Desktop e Mobile)|**Descrizione:** criterio per rinviare gli aggiornamenti delle funzionalità per un massimo di 8 mesi<br /><br />**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**-**8**: numero di mesi di rinvio degli aggiornamenti delle funzionalità.<br /><br />Per altre informazioni, vedere:<br>[Introduzione alla manutenzione di Windows 10](https://technet.microsoft.com/library/mt598226.aspx)<br>[Piano per la distribuzione di Windows 10](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>(Desktop e Mobile)|**Descrizione:** consente a un computer CBB di non ricevere più gli aggiornamenti per 5 settimane. Usare questo criterio in caso di problemi con un aggiornamento.<br /><br />**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Update/PauseDeferrals<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: applica immediatamente gli aggiornamenti (impostazione predefinita)<br>**1**: sospendi gli aggiornamenti (scade dopo 5 settimane)|

### Impostazioni URI di Windows Defender

|Nome criteri|Dettagli|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**AllowBehaviorMonitoring**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**AllowIntrusionPreventionSystem**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**AllowIOAVProtection**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**AllowScriptScanning**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**AllowOnAccessProtection**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**RealTimeScanDirection**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: esegue il monitoraggio di tutti i file, bidirezionale (impostazione predefinita)<br>**1** : esegue il monitoraggio dei file in ingresso<br>**2** : esegue il monitoraggio dei file in uscita|
|**DaysToRetainCleanedMalware**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** - **90**: indica il malware conservato e il periodo di conservazione<br>**Valore predefinito:** **0**, conserva per sempre il malware nella cartella di quarantena e non lo rimuove automaticamente|
|**AllowUserUIAccess**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**ScanParameter**<br>(solo Desktop)|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/Defender/ScanParameter<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**1**: analisi veloce (impostazione predefinita)<br>**2**: analisi completa|
|**ScheduleScanDay**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: tutti i giorni (impostazione predefinita)<br>**1**: lunedì<br>**2**: martedì<br>**3**: mercoledì<br>**4**: giovedì<br>**5**: venerdì<br>**6**: sabato<br>**7**: domenica<br>**8** : nessuna analisi pianificata|
|**ScheduleScanTime**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** – 12:00<br>**60** – 1:00<br>**120** – 2:00 (impostazione predefinita)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1381** -Finestra di manutenzione|
|**ScheduleQuickScanTime**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime<br>**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** – 12:00<br>**60** – 1:00<br>**120** – 2:00 (impostazione predefinita)<br>**180** – 3:00<br>**240** – 4:00<br>**300** – 5:00<br>**360** – 6:00<br>**420** – 7:00<br>**480** – 8:00<br>**540** – 9:00<br>**600** – 10:00<br>**660** – 11:00<br>**720** – 12:00<br>**780** – 13:00<br>**840** – 14:00<br>**900** – 15:00<br>**960** – 16:00<br>**1020** – 17:00<br>**1080** – 18:00<br>**1140** – 19:00<br>**1200** – 20:00<br>**1260** – 21:00<br>**1320** – 22:00<br>**1380** – 22:00|
|**AVGCPULoadFactor**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:0** - **100** (impostazione predefinita: **50**)|
|**AllowArchiveScanning**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**AllowEmailScanning**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning<br /><br />**Tipo di dati:** Integer<br>**Valori consentiti:**<br>**0**: non consentito (impostazione predefinita)<br>**1** : consentito|
|**AllowFullScanRemovableDriveScanning**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non consentito (impostazione predefinita)<br>**1** : consentito|
|**AllowFullScanOnMappedNetworkDrives**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**AllowScanningNetworkFiles**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita). Se impostato su consentito, viene eseguito anche quando RTP è attivo|
|**SignatureUpdateInterval**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non controlla le firme in un intervallo<br>**1**: controlla le firme ogni ora<br>**2** : controlla le firme ogni due ore<br>**24** : controlla le firme ogni giorno<br>**Valore predefinito:** 8. Controlla le firme ogni otto ore|
|**AllowCloudProtection**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0** : non consentito<br>**1**: consentito (impostazione predefinita)|
|**SubmitSamplesConsent**<br>(solo Desktop)|**Percorso URI completo** ./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: richiedere sempre (impostazione predefinita)<br>**1** : inviare campioni sicuri automaticamente<br>**2** : non inviare mai<br>**3** : inviare tutti i campioni automaticamente|
|**ExcludedExtensions**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:**<br>*&lt;elenco di estensioni separate da punto e virgola&gt;* ad esempio **obj;lib**<br>**Valore predefinito:** nessuna estensione viene esclusa|
|**ExcludedPaths**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:**<br /><br />*&lt;elenco di percorsi separati da punto e virgola&gt;*<br /><br />Esempio: **c:\test;c:\test1.exe**<br /><br />**Valore predefinito:** nessun percorso viene escluso|
|**ExcludedProcesses**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:**<br>*&lt;elenco di percorsi separati da punto e virgola&gt;*<br>Esempio: **c:\test.exe;c:\test1.exe**<br>**Valore predefinito:** nessun processo viene escluso|

### Impostazioni URI del browser Edge

|Nome criteri|Dettagli|
|---------------|------------|-----------|
|**Allow Browser**<br>(solo Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowBrowser<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: l'esplorazione è disattivata<br>**1**: l'esplorazione è attivata (impostazione predefinita)|
|**AllowSearchSuggestionsinAddressBar**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non visualizza i suggerimenti di ricerca<br>**1**: visualizza i suggerimenti di ricerca (impostazione predefinita)|
|**SendIntranetTraffictoInternetExplorer**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: disabilitato, apre i siti Intranet nel browser Edge (impostazione predefinita)<br>**1**: abilitato, apre i siti Intranet in Internet Explorer.|
|**Allow Do Not Track**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: disabilitato, DNT non inviato (impostazione predefinita)<br>**1**: abilitato, DNT inviato|
|**Configure SmartScreen**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non consentito<br>**1**: consentito (impostazione predefinita)|
|**Allow Pop-ups**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowPopups<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: blocca i popup (impostazione predefinita)<br>**1**: consente i popup|
|**Allow Cookies**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Settings/AllowTheme<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: non bloccare. Consente i cookie provenienti da tutti i siti Web (impostazione predefinita)<br>**1**: blocca solo i cookie di terze parti<br>**2**: blocca tutti i cookie|
|**Allow Save Password**<br>(Desktop e Mobile)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: lo strumento per la gestione delle password è disabilitato; <br>**1**: lo strumento per la gestione delle password è abilitato (impostazione predefinita)|
|**Consenti riempimento automatico**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/AllowAutofill<br /><br />**Tipo di dati:** Integer<br /><br />**Valori consentiti:**<br>**0**: disabilitato (impostazione predefinita)<br>**1**: abilitato|
|**Configure Enterprise Site List**<br>(solo Desktop)|**Percorso URI completo:** ./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList<br /><br />**Tipo di dati:** stringa<br /><br />**Valori consentiti:<br>0**, non configurato<br>**1**: se configurato, usa l'elenco dei siti della modalità Enterprise di Internet Explorer (impostazione predefinita)<br>**2**: consente di specificare il percorso dell'elenco dei siti Enterprise|

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jul16_HO3-->


