---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows 10
titleSuffix: Intune Azure preview
description: "Anteprima di Intune Azure: informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo con Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 43c2c517dffbb6b2e7b654c5ca8a0ad9062683eb
ms.lasthandoff: 04/19/2017


---

# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows 10 e versioni successive in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Generale
-     **Acquisizione di schermata (solo dispositivi mobili)**: consente all'utente di acquisire la schermata del dispositivo come immagine.
-     **Copia e incolla (solo dispositivi mobili)** - Consente le azioni di copia e incolla tra app sul dispositivo.
-     **Annullamento manuale della registrazione** - Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.
-     **Installazione manuale del certificato radice (solo per dispositivi mobili)**: impedisce all'utente di installare manualmente i certificati radice e i certificati intermedi CAP.
-     **Invio dati di diagnostica** - I valori possibili sono:
    -         **No** Non vengono inviati dati a Microsoft
    -         **Di base** Vengono inviate a Microsoft informazioni limitate
    -         **Avanzati** Vengono inviati a Microsoft dati di diagnostica avanzati
    -         **Completi** Invia gli stessi dati di Avanzati, più dati aggiuntivi sullo stato del dispositivo
-     **Fotocamera** - Consente o blocca l'uso della fotocamera sul dispositivo.
-     **Sincronizzazione dei file di OneDrive**: impedisce al dispositivo di sincronizzare i file in OneDrive.
-     **Archivi rimovibili** - Specifica se è possibile usare dispositivi di archiviazione esterni, come le schede SD, con il dispositivo.
-     **Georilevazione** - Specifica se il dispositivo può usare le informazioni dei servizi di posizione.
-     **Internet condiviso** - Consente l'uso della condivisione della connessione Internet sul dispositivo.
-     **Ripristino del telefono** - Controlla se l'utente può eseguire un ripristino delle impostazioni predefinite nel dispositivo.
-     **Connessione USB (solo per dispositivi mobili)**: controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni tramite una connessione USB.
-     **Modalità antifurto (solo per dispositivi mobili)**: configura l'attivazione della modalità antifurto di Windows.
-     **Notifiche del centro notifiche (solo per dispositivi mobili)**: abilita o disabilita le notifiche del centro notifiche visualizzate sullo schermo di blocco del dispositivo (solo in Windows 10 Mobile).
-     **Cortana** - Abilita o disabilita l'assistente vocale Cortana.
-     **Registrazione vocale (solo per dispositivi mobili)**: consente o impedisce l'uso del registratore vocale del dispositivo.
-     **Modifica delle impostazioni di risparmio energia e sospensione (solo desktop)**: impedisce all'utente finale di modificare le impostazioni di risparmio energia e sospensione del dispositivo.
-     **Modifica delle impostazioni dell'area (solo desktop)**: impedisce all'utente finale di modificare le impostazioni dell'area del dispositivo.
-     **Modifiche alle impostazioni della lingua (solo desktop)**: impedisce all'utente finale di modificare le impostazioni della lingua del dispositivo.
-     **Modifica dell'ora di sistema**: impedisce all'utente finale di modificare la data e l'ora del dispositivo.
-     **Modifica del nome del dispositivo**: impedisce all'utente finale di modificare il nome del dispositivo.
-     **Aggiungi pacchetti di provisioning**: blocca l'agente di configurazione di runtime che installa pacchetti di provisioning.
-     **Rimuovi i pacchetti di provisioning**: blocca l'agente di configurazione di runtime che rimuove pacchetti di provisioning.
-     **Individuazione dei dispositivi**: blocca l'individuazione di un dispositivo da parte di altri dispositivi.
-     **Cambio modalità per l'attività (solo dispositivi mobili)**: blocca il cambio modalità per l'attività nel dispositivo.
-     **Finestra di dialogo di errore per la scheda SIM (solo dispositivi mobili)**: blocca la visualizzazione di un messaggio di errore nel dispositivo se non viene rilevata alcuna scheda SIM.


## <a name="password"></a>Password
-     **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.
    -     **Tipo di password richiesto** - Consente di specificare se la password deve essere solo numerica o alfanumerica.
    -     **Lunghezza minima password** Si applica solo a Windows 10 Mobile.
    -     **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Per i dispositivi che eseguono Windows 10: se nel dispositivo è abilitato BitLocker, viene attivata la modalità di ripristino BitLocker se l'accesso ha esito negativo per il numero di volte specificato. Se nel dispositivo non è abilitato BitLocker, questa impostazione non si applica.
Per i dispositivi che eseguono Windows 10 Mobile: se l'accesso ha esito negativo per il numero di volte specificato, il dispositivo viene cancellato.
    -     **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il periodo di tempo per cui un dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.
    -     **Scadenza password (giorni)** - Specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo.
    -     **Impedisci riutilizzo delle password precedenti** - Specifica il numero di password utilizzate in precedenza che il dispositivo deve ricordare.
    -     **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività** - Specifica che l'utente deve inserire una password per sbloccare il dispositivo (solo Windows 10 Mobile).
-     **Crittografia** - Abilita la crittografia sui dispositivi di destinazione (solo Windows 10 Mobile).

## <a name="personalization"></a>Personalization

-     **URL dell'immagine di sfondo del desktop (solo desktop)**: specifica l'URL di un'immagine in formato JPEG, PNG o JPG che verrà usata come sfondo del desktop di Windows. Gli utenti non potranno modificare questa impostazione.

## <a name="locked-screen-experience"></a>Esperienza della schermata bloccata

-     **URL dell'immagine della schermata bloccata (solo desktop)**: specifica l'URL di un'immagine in formato JPEG, PNG o JPG che verrà usata come sfondo della schermata bloccata di Windows. Gli utenti non potranno modificare questa impostazione.


## <a name="app-store"></a>App Store

-     **App Store (solo dispositivi mobili)** - Consente o blocca l'uso dell'App Store nei dispositivi Windows 10 Mobile.
-     **Aggiorna automaticamente le app dallo Store**: consente l'aggiornamento automatico delle app installate da Windows Store.
-     **Installazione di app attendibile**: consente il trasferimento locale delle app con certificato attendibile.
-     **Sblocco dallo sviluppatore**: consente la modifica delle impostazioni da parte degli sviluppatori Windows, ad esempio consentire all'utente finale di modificare le app trasferite localmente.
-     **Dati app utente condivisi**: consente alle app di condividere dati tra utenti diversi dello stesso dispositivo.
-     **Usa solo lo Store privato**: consente agli utenti finali di scaricare app da uno Store privato.
-     **Avvio di app originate dallo Store**: disabilita tutte le app preinstallate nel dispositivo o scaricate da Windows Store.
-     **Installa i dati dell'app nel volume di sistema**: impedisce alle app di archiviare dati nel volume di sistema del dispositivo.
-     **Installa le app nell'unità di sistema**: impedisce alle app di archiviare dati nell'unità di sistema del dispositivo.
-     **Game DVR (solo desktop)**: configura se la registrazione e la trasmissione dei giochi sono consentite.



## <a name="edge-browser"></a>Browser Edge
-     **Browser Microsoft Edge (solo dispositivi mobili)** - Consente l'uso del browser Web Edge sul dispositivo.
-     **SmartScreen** - Abilita o disabilita SmartScreen che blocca i siti Web fraudolenti.
-     **Invia intestazioni DNT (Do Not Track)** - Configura il browser Microsoft Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti.
-     **Cookie** - Consente al browser di salvare i cookie di Internet per il dispositivo.
-     **JavaScript** - Consente di eseguire script, ad esempio Javascript, nel browser Microsoft Edge.
-     **Pop-up**: blocca le finestra popup del browser (si applica solo a Windows 10 Desktop).
-     **Suggerimenti per la ricerca** - Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca.
-     **Invia traffico Intranet a Internet Explorer**: consente agli utenti di aprire siti Web della Intranet in Internet Explorer (solo per Windows 10 Desktop).
-     **Riempimento automatico**: consente agli utenti di modificare le impostazioni di completamento automatico nel browser (solo per Windows 10 Desktop).
-     **Strumento per la gestione delle password** - Abilita o disabilita la funzione di gestione password di Microsoft Edge.
-     **Posizione elenco siti modalità Enterprise** - Specifica dove trovare l'elenco dei siti Web che si aprono in modalità Enterprise. L'elenco non è modificabile dagli utenti.<br>Solo Windows 10 Desktop.
-     **Strumenti di sviluppo**: impedisce all'utente finale di aprire gli strumenti di sviluppo Edge.
-     **Estensioni**: consente all'utente finale di installare le estensioni Edge nel dispositivo.
-     **InPrivate Browsing**: impedisce all'utente finale di aprire sessioni InPrivate Browsing.
-     **URL della prima esecuzione**: immettere l'URL che il browser Edge apre alla prima esecuzione (solo in dispositivi mobili).
-     **Home page**: aggiunge un elenco di siti che verranno usati come home page nel browser Edge (solo desktop).
-     **Blocca l'accesso ai flag Informazioni su**: impedisce all'utente finale di accedere alla pagina di "flag Informazioni su" in Edge che contiene impostazioni sperimentali e di sviluppo.
-     **Override della richiesta di conferma SmartScreen**: consente all'utente finale di ignorare gli avvisi del filtro SmartScreen su siti Web potenzialmente dannosi.
-     **Override della richiesta di conferma SmartScreen per i file**: consente all'utente finale di ignorare gli avvisi del filtro SmartScreen durante il download di file potenzialmente dannosi.
-     **Indirizzo IP localhost WebRtc**: blocca la visualizzazione dell'indirizzo IP localhost IP quando si effettuano telefonate tramite il protocollo RTC Web.
-     **Motore di ricerca predefinito**: specifica il motore di ricerca predefinito da usare. Gli utenti finali possono modificare questo valore in qualsiasi momento.

## <a name="search"></a>Cerca
- **Ricerca sicura (solo dispositivi mobili)**: controlla come Cortana filtra il contenuto per adulti nei risultati della ricerca. È possibile selezionare **Strict**, **Moderate** o consentire all'utente finale di scegliere le proprie impostazioni.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
-     **Account Microsoft** - Consente all'utente di associare un account Microsoft con il dispositivo.
-     **Account non Microsoft** - Consente all'utente di aggiungere account di posta elettronica al dispositivo che non sono associati con un account Microsoft.
-     **Sincronizzazione delle impostazioni per l'account Microsoft** - Consente che le impostazioni del dispositivo e delle app associate con un account Microsoft vengano sincronizzate fra i dispositivi.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività
-     **Roaming dati** - Consente il roaming tra reti quando si accede ai dati.
-     **VPN nella rete cellulare** - Controlla se il dispositivo può accedere a connessioni VPN quando è collegato a una rete cellulare.
-     **Roaming VPN nella rete cellulare** - Controlla se il dispositivo può accedere a connessioni VPN quando è in roaming su una rete cellulare.
-     **Bluetooth** - Controlla se l'utente può abilitare e configurare Bluetooth nel dispositivo.
-     **Individuabilità di Bluetooth** - Consente che il dispositivo sia scoperto da altri dispositivi con la funzione Bluetooth attivata.
-     **Annunci con Bluetooth** - Consente al dispositivo di ricevere annunci tramite Bluetooth.
-     **Nome di Bluetooth del dispositivo**: consente di specificare il nome di Bluetooth per il dispositivo.
-     **NFC** - Consente all'utente di attivare e configurare funzionalità Near Field Communications sul dispositivo.
-     **Wi-Fi** - Consente all'utente di attivare e configurare le funzionalità Wi-Fi del dispositivo (solo Windows 10 Mobile).
-     **Connetti automaticamente a hotspot Wi-Fi** - Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione.
-     **Configurazione Wi-Fi manuale** - Controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi (solo Windows 10 Mobile).
-     **Intervallo di analisi Wi-Fi**: specifica la frequenza con cui i dispositivi ricercano reti Wi-Fi.

## <a name="control-panel-and-settings"></a>Pannello di controllo e impostazioni

-     **App Impostazioni**: blocca l'accesso all'app Impostazioni di Windows.
    -     **Sistema**: blocca l'accesso all'area di sistema dell'app Impostazioni.
    -     **Dispositivi**: blocca l'accesso all'area dei dispositivi dell'app Impostazioni.
    -     **Rete Internet**: blocca l'accesso all'area rete e Internet dell'app Impostazioni.
    -     **Personalizzazione**: blocca l'accesso all'area di personalizzazione dell'app Impostazioni.
    -     **Account**: blocca l'accesso all'area degli account dell'app Impostazioni.
    -     **Ora e lingua**: blocca l'accesso all'area dell'ora e della lingua dell'app Impostazioni.
    -     **Accessibilità**: blocca l'accesso all'area accessibilità dell'app Impostazioni.
    -     **Riservatezza**: blocca l'accesso all'area riservatezza dell'app Impostazioni.
    -     **Aggiornamento e sicurezza** : blocca l'accesso all'area di aggiornamento e sicurezza dell'app Impostazioni.

## <a name="defender"></a>Defender

-     **Monitoraggio in tempo reale** - Abilita l'analisi in tempo reale per malware, spyware e altro software indesiderato.
-     **Monitoraggio del comportamento** - Consente a Defender di controllare la presenza di modelli noti di attività sospette nei dispositivi.
-     **Network Inspection System (NIS)** - Network Inspection System (NIS) contribuisce a proteggere i dispositivi dagli exploit basati sulla rete usando le firme di vulnerabilità note di Microsoft Endpoint Protection Center per rilevare e bloccare il traffico dannoso.
-     **Analizza tutti i download** - Controlla se Defender deve analizzare tutti i file scaricati da Internet.
-     **Analizza gli script caricati nei Web browser Microsoft** - Consente a Defender di analizzare gli script utilizzati in Internet Explorer.
-     **Accesso dell'utente finale a Defender** - Determina se l'interfaccia utente di Windows Defender è nascosta agli utenti finali.
Quando questa impostazione viene modificata, ha effetto dal successivo avvio del PC da parte dell'utente finale.
-     **Intervallo di aggiornamento della firma (in ore)** - Specifica l'intervallo secondo il quale Defender controllerà i nuovi file di firma.
-     **Monitora l'attività di file e programmi** - Consente a Defender di monitorare l'attività di file e programmi nei dispositivi.
-     **Giorni di attesa prima dell'eliminazione di malware in quarantena** - Consente a Defender di continuare a monitorare il malware risolto per il numero di giorni specificato, in modo che sia possibile controllare manualmente i dispositivi colpiti in precedenza. Se si imposta il numero di giorni su **0**, il malware rimane nella cartella della quarantena e non viene rimosso automaticamente.
-     **Limite di utilizzo della CPU durante un'analisi** - Consente di limitare la quantità di CPU utilizzata per le analisi (da **1** a **100**).
-     **Analizza file di archivio** - Consente a Defender di analizzare i file archiviati come i file con estensione .zip o .cab.
-     **Analizza i messaggi di posta in arrivo** - Consente a Defender di analizzare i messaggi di posta elettronica non appena arrivano sul dispositivo.
-     **Analizza le unità rimovibili durante un'analisi completa** - Consente a Defender di analizzare le unità rimovibili come le chiavi USB.
-     **Analizza le unità di rete mappate durante un'analisi completa** - Consente a Defender di analizzare i file nelle unità di rete mappate.<br>Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.
-     **Analizza file aperti da cartelle di rete** - Consente a Defender di analizzare i file sulle unità di rete condivise, ad esempio quelli a cui si accede da un percorso UNC.
Se i file sull'unità sono di sola lettura, Defender non sarà in grado di rimuovere il malware che rileva in essi.
-     **Protezione cloud** - Consente o blocca la ricezione di informazioni sull'attività del malware da parte di Microsoft Active Protection Service dai dispositivi gestiti. Queste informazioni vengono usate per migliorare il servizio in futuro.
-     **Richiedi conferma all'utente prima dell'invio di campioni** - Controlla se i file che potrebbero richiedere ulteriore analisi da parte di Microsoft per determinare se sono dannosi vengono inviati automaticamente a Microsoft.
-     **Ora di esecuzione di un'analisi veloce giornaliera** - Consente di pianificare un'analisi veloce che viene eseguita giornalmente all'ora selezionata.
-     **Tipo di analisi di sistema da eseguire** - Consente di specificare il livello di analisi che sarà adottato quando si pianifica un'analisi del sistema.

## <a name="defender-exclusions"></a>Esclusioni di Defender

-     **File e cartelle da escludere dalle analisi e dalla protezione in tempo reale** - Aggiunge uno o più file e cartelle come **C:\Percorso** o **%ProgramFiles%\Percorso\nomefile.exe** all'elenco delle esclusioni. Questi file e cartelle non sono inclusi nelle analisi in tempo reale o pianificate.
-     **Estensioni di file da escludere dalle analisi e dalla protezione in tempo reale** - Aggiunge una o più estensioni di file come **.jpg** o **.txt** all'elenco delle esclusioni. I file con queste estensioni non sono inclusi nelle analisi in tempo reale o pianificate.
-     **Processi da escludere dalle analisi e dalla protezione in tempo reale** - Aggiunge uno o più processi del tipo **.exe**, **. com** o **. scr** all'elenco delle esclusioni. Questi processi non saranno inclusi nelle analisi in tempo reale o pianificate.


## <a name="network-proxy"></a>Proxy di rete

-     **Rileva automaticamente impostazioni proxy**: se questa opzione è attivata, il dispositivo cercherà il percorso a uno script PAC.
-     **Usa lo script proxy**: selezionare questa opzione se si vuole specificare un percorso a uno script PAC per configurare il server proxy.
    -     **URL dell'indirizzo dello script di installazione**: immettere l'URL di uno script PAC che si vuole usare per configurare il server proxy.
-     **Usa il server proxy manuale**: selezionare questa opzione se si vogliono specificare manualmente le informazioni del server proxy.
    -     **Indirizzo**: immettere il nome o l'indirizzo IP del server proxy.
    -     **Numero porta**: immettere il numero della porta del server proxy.
    -     **Eccezione del proxy**: immettere gli URL che non devono usare il server proxy. Per separare ogni elemento, usare un punto e virgola.
    -     **Ignora il server proxy per l'indirizzo locale**: abilitare questa opzione se non si vuole usare il server proxy per gli indirizzi locali della rete Intranet.


## <a name="windows-spotlight"></a>Contenuti in evidenza di Windows

-     **Contenuti in evidenza di Windows**: consente o blocca Contenuti in evidenza di Windows che offre diverse funzionalità, ad esempio suggerimenti, messaggi nella schermata di blocco di Windows e altro ancora.
    -     **Suggerimenti di Windows**: consente di bloccare la visualizzazione dei suggerimenti popup in Windows.
    -     **Funzionalità consumer**: consente di bloccare le funzionalità consumer, ad esempio i suggerimenti per il menu Start e le notifiche di appartenenza.

## <a name="display"></a>Schermo

- **Input degli utenti da ricevitori di schermo wireless**: blocca l'input degli utenti da ricevitori di schermo wireless.
- **Proiezione per questo computer**: blocca l'individuazione della proiezione di questo computer da parte di altri dispositivi.
- **Richiedi il PIN per l'associazione**: richiede un PIN durante la connessione a un dispositivo di proiezione.

## <a name="start"></a>Avvia

- **Rimuovi le app dalla barra della applicazioni**: impedisce all'utente di rimuovere app dal menu Start.
- **Documenti nel menu Start**: nasconde o mostra la cartella Documenti nel menu Start di Windows.
- **Download nel menu Start**: nasconde o mostra la cartella Download nel menu Start di Windows.
- **Esplora file nel menu Start**: nasconde o mostra l'app Esplora file nel menu Start di Windows.
- **Gruppo Home nel menu Start**: nasconde o mostra la cartella Gruppo Home nel menu Start di Windows.
- **Musica nel menu Start**: nasconde o mostra la cartella Musica nel menu Start di Windows.
- **Rete nel menu Start**: nasconde o mostra la cartella Rete nel menu Start di Windows.
- **Cartella Personale nel menu Start**: nasconde o mostra la cartella Personale nel menu Start di Windows.
- **Immagini nel menu Start**: nasconde o mostra la cartella delle immagini nel menu Start di Windows.
- **Impostazioni nel menu Start**: nasconde o mostra l'app Impostazioni nel menu Start di Windows.
- **Video nel menu Start**: nasconde o mostra la cartella dei video nel menu Start di Windows.
