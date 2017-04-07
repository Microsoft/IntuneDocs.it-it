---
title: Impostazioni relative alle restrizioni dei dispositivi per Windows 10
titleSuffix: Intune Azure preview
description: "Anteprima di Intune Azure: informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo con Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 89f2d806-2e97-430c-a9a1-70688269627f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 74f99d5e2d4eef8d42ccd2c7bc34e0ed7b6f0d51
ms.lasthandoff: 02/18/2017


---

# <a name="windows-10-and-later-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Windows 10 e versioni successive in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Generale
-     **Acquisizione schermo** - Consente all'utente di acquisire la schermata del dispositivo come immagine. (Solo Windows 10 Mobile)
-     **Copia e incolla (solo dispositivi mobili)** - Consente le azioni di copia e incolla tra app sul dispositivo.
-     **Annullamento manuale della registrazione** - Consente all'utente di eliminare manualmente l'account aziendale dal dispositivo.
-     **Installazione manuale del certificato radice** -     
-     **Invio dati di diagnostica** - I valori possibili sono:
    -         **No** Non vengono inviati dati a Microsoft
    -         **Di base** Vengono inviate a Microsoft informazioni limitate
    -         **Avanzati** Vengono inviati a Microsoft dati di diagnostica avanzati
    -         **Completi** Invia gli stessi dati di Avanzati, più dati aggiuntivi sullo stato del dispositivo
-     **Fotocamera** - Consente o blocca l'uso della fotocamera sul dispositivo.
-     **Archivi rimovibili** - Specifica se è possibile usare dispositivi di archiviazione esterni, come le schede SD, con il dispositivo.
-     **Georilevazione** - Specifica se il dispositivo può usare le informazioni dei servizi di posizione.
-     **Internet condiviso** - Consente l'uso della condivisione della connessione Internet sul dispositivo.
-     **Ripristino del telefono** - Controlla se l'utente può eseguire un ripristino delle impostazioni predefinite nel dispositivo.
-     **Connessione USB** - Controlla se i dispositivi possono accedere a dispositivi di archiviazione esterni mediante una connessione USB.
-     **Modalità AntiTheft** - Determina se la modalità Antitheft di Windows è abilitata.
-     **Notifiche del centro notifiche** - Abilita o disabilita le notifiche del centro notifiche sullo schermo di blocco del dispositivo (solo Windows 10 Mobile).
-     **Cortana** - Abilita o disabilita l'assistente vocale Cortana.
-     **Registrazione vocale** - Consente o blocca l'uso del registratore vocale del dispositivo.

## <a name="password"></a>Password
-     **Password necessaria** - Richiede all'utente finale di immettere una password per accedere al dispositivo.
-     **Tipo di password richiesto** - Consente di specificare se la password deve essere solo numerica o alfanumerica.
-     **Lunghezza minima password** Si applica solo a Windows 10 Mobile.
-     **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Per i dispositivi che eseguono Windows 10: se nel dispositivo è abilitato BitLocker, viene attivata la modalità di ripristino BitLocker se l'accesso ha esito negativo per il numero di volte specificato. Se nel dispositivo non è abilitato BitLocker, questa impostazione non si applica.
Per i dispositivi che eseguono Windows 10 Mobile: se l'accesso ha esito negativo per il numero di volte specificato, il dispositivo viene cancellato.
-     **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il periodo di tempo per cui un dispositivo deve rimanere inattivo prima che lo schermo venga bloccato.
-     **Scadenza password (giorni)** - Specifica l'intervallo di tempo dopo il quale è necessario modificare la password del dispositivo.
-     **Impedisci riutilizzo delle password precedenti** - Specifica il numero di password utilizzate in precedenza che il dispositivo deve ricordare.
-     **Richiedi la password quando il dispositivo torna attivo dopo uno stato di inattività** - Specifica che l'utente deve inserire una password per sbloccare il dispositivo (solo Windows 10 Mobile).
-     **Crittografia** - Abilita la crittografia sui dispositivi di destinazione (solo Windows 10 Mobile).
## <a name="app-store"></a>App Store

-     **App Store (solo dispositivi mobili)** - Consente o blocca l'uso dell'App Store nei dispositivi Windows 10 Mobile.
## <a name="edge-browser"></a>Browser Edge
-     **Browser Microsoft Edge (solo dispositivi mobili)** - Consente l'uso del browser Web Edge sul dispositivo.
-     **SmartScreen** - Abilita o disabilita SmartScreen che blocca i siti Web fraudolenti.
-     **Invia intestazioni DNT (Do Not Track)** - Configura il browser Microsoft Edge in modo che invii intestazioni Do Not Track ai siti Web visitati dagli utenti.
-     **Cookie** - Consente al browser di salvare i cookie di Internet per il dispositivo.
-     **JavaScript** - Consente di eseguire script, ad esempio Javascript, nel browser Microsoft Edge.
-     **Popup** - Blocca le finestre popup nel browser.<br>Si applica solo a Windows 10 Desktop.
-     **Suggerimenti per la ricerca** - Consente al motore di ricerca di suggerire siti mentre si digita la frase di ricerca.
-     **Invia traffico Intranet a Internet Explorer** - Consente agli utenti di aprire i siti Web della intranet in Internet Explorer. <br>Solo Windows 10 Desktop.
-     **Riempimento automatico** - Consente all'utente di modificare le impostazioni di completamento automatico nel browser.<br>(Solo Windows 10 Desktop)
-     **Strumento per la gestione delle password** - Abilita o disabilita la funzione di gestione password di Microsoft Edge.
-     **Posizione elenco siti modalità Enterprise** - Specifica dove trovare l'elenco dei siti Web che si aprono in modalità Enterprise. L'elenco non è modificabile dagli utenti.<br>Solo Windows 10 Desktop.
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
-     **NFC** - Consente all'utente di attivare e configurare funzionalità Near Field Communications sul dispositivo.
-     **Wi-Fi** - Consente all'utente di attivare e configurare le funzionalità Wi-Fi del dispositivo (solo Windows 10 Mobile).
-     **Connetti automaticamente a hotspot Wi-Fi** - Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente termini e condizioni per la connessione.
-     **Configurazione Wi-Fi manuale** - Controlla se l'utente può configurare le proprie connessioni Wi-Fi o se può usare solo le connessioni configurate da un profilo Wi-Fi (solo Windows 10 Mobile).
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

