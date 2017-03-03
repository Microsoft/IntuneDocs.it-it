---
title: Impostazioni relative alle restrizioni del dispositivo di Intune per Android | Anteprima di Intune Azure | Documentazione Microsoft
description: "Anteprima di Intune Azure: informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo con Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: a003b2b16e05c2d071bb7dbaaf564e24d0cf5823
ms.lasthandoff: 02/16/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Android e Samsung KNOX Standard in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

## <a name="general"></a>Generale
-     **Fotocamera** - Consente l'uso della fotocamera del dispositivo.
-     **Copia e incolla** - Consente le funzioni Copia e Incolla nel dispositivo.
-     **Condivisione degli Appunti tra app** - Consente l'uso degli Appunti per copiare e incollare tra app (solo Samsung KNOX Standard).
-     **Invio dati di diagnostica** - Impedisce all'utente di inviare dati di diagnostica dal dispositivo.    
-     **Ripristino impostazioni predefinite** - Consente all'utente di eseguire il ripristino delle impostazioni di fabbrica del dispositivo.
-     **Georilevazione** - Consente al dispositivo di usare le informazioni sul percorso (solo Samsung KNOX Standard).
-     **Spegnimento** - Consente all'utente di spegnere il dispositivo.<br>Se questa impostazione è disabilitata, l'impostazione **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** per i dispositivi Samsung KNOX Standard non funziona.
-     **Acquisizione schermo** - Consente all'utente di acquisire il contenuto della schermata come immagine.
-     **Assistente vocale** - Consente di usare software di assistenza vocale sul dispositivo (solo Samsung KNOX Standard).
-     **YouTube** - Consente l'uso dell'app YouTube nel dispositivo (solo Samsung KNOX Standard).

## <a name="password"></a>Password
-     **Password necessaria** - Richiede all'utente finale di immettere una password per accedere al dispositivo.
-     **Lunghezza minima password** - Immettere la lunghezza minima della password che l'utente deve configurare, da 4 a 16 caratteri.
-     **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il numero di minuti di inattività prima dello spegnimento dello schermo del dispositivo.
-     **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Specifica il numero di errori di accesso consentiti prima della cancellazione del dispositivo.
-     **Scadenza password (giorni)** - Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.
-     **Tipo di password richiesto** - Specifica il livello richiesto di complessità delle password e indica se è possibile usare dispositivi biometrici.
-     **Impedisci riutilizzo delle password precedenti** - Impedisce all'utente finale di creare una password che è già stata usata in precedenza.
-     **Impronta digitale sbloccata** - Consente di usare un'impronta digitale per sbloccare i dispositivi supportati.
-     **Smart Lock e altri agenti di attendibilità** - Consente di controllare la funzionalità Smart Lock su dispositivi Android compatibili (Samsung KNOX Standard 5.0 e versioni successive). Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se quest'ultimo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire agli utenti di configurare Smart Lock.
-     **Crittografia** - Richiede la crittografia dei file nel dispositivo.

## <a name="google-play-store"></a>Google Play Store

-     **Google Play Store** - Consente all'utente di accedere a Google Play Store sul dispositivo (solo Samsung KNOX Standard).

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

Un elenco **App non consentite** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire.
Un elenco **App approvate** - Elenca le app che gli utenti sono autorizzati a installare. Per garantire la conformità, non installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite.
I profili dispositivo che contengono impostazioni per app con restrizioni devono essere distribuiti ai gruppi di utenti.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL di app nell'elenco di app conformi e non conformi, seguire questa procedura:

Nella [sezione delle app di Google Play](https://play.google.com/store/apps), cercare l'app da usare.

Aprire la pagina di installazione relativa all'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app conformi e non conformi.

Esempio: Cercare Microsoft Office Mobile in Google Play. L'URL usato sarà **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app con restrizioni nello stesso formato.        

## <a name="browser"></a>Browser
-     **Browser Web** - Specifica se è consentito l'uso del browser Web predefinito nel dispositivo.
-     **Riempimento automatico** - Consente di usare la funzione di riempimento automatico del browser Web.
-     **Cookie** - Consente l'uso dei cookie nel browser Web del dispositivo.
-     **JavaScript** - Consente al browser Web del dispositivo di eseguire gli script JavaScript.
-     **Popup** - Consente di usare un blocco popup nel Web browser.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
-     **Backup di Google** - Consente l'uso del backup di Google.
-     **Sincronizzazione automatica dell'account Google** - Consente la sincronizzazione automatica delle impostazioni dell'account Google.
-     **Archivi rimovibili** - Consente al dispositivo di usare archivi rimovibili, ad esempio una scheda SD (solo Samsung KNOX Standard).
-     **Crittografia sulle schede di memoria** - Specifica se la scheda di memoria del dispositivo deve essere crittografata.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività
-     **Roaming dati** - Consente il roaming dati quando il dispositivo si trova in una rete cellulare (solo Samsung KNOX Standard).
-     **Messaggi SMS/MMS** - Consente l'uso dei messaggi SMS e MMS sul dispositivo (solo Samsung KNOX Standard).
-     **Chiamata vocale** - Abilita o disabilita la funzionalità di composizione vocale sul dispositivo (solo Samsung KNOX Standard).
-     **Roaming vocale** - Consente il roaming vocale quando il dispositivo si trova in una rete cellulare (solo Samsung KNOX Standard).
-     **Bluetooth** - Consente l'uso di Bluetooth nel dispositivo (solo Samsung KNOX Standard).
-     **NFC** - Consente l'uso della tecnologia NFC (Near Field Communication) se il dispositivo la supporta (solo Samsung KNOX Standard).
-     **Wi-Fi** - Consente l'uso delle funzionalità Wi-Fi nel dispositivo (solo Samsung KNOX Standard).
-     **Tethering Wi-Fi** - Consente di usare il tethering Wi-Fi nel dispositivo (solo Samsung KNOX Standard).

## <a name="kiosk"></a>Modalità tutto schermo
-     **Selezionare un'app gestita** - Individuare e selezionare l'app gestita che può essere eseguita quando il dispositivo è in modalità tutto schermo. Le app specificate come collegamento allo store non sono attualmente supportate. Non sarà possibile eseguire altre applicazioni nel dispositivo.
-     **Pulsante Sospensione schermo** - Abilita o disabilita il pulsante di sospensione dello schermo del dispositivo.
-     **Pulsanti volume**: abilita o disabilita l'uso dei pulsanti del volume del dispositivo.

