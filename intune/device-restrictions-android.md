---
title: Impostazioni relative alle restrizioni dei dispositivi per Android
titleSuffix: Intune Azure preview
description: "Anteprima di Intune Azure: informazioni sulle opzioni di Intune che è possibile usare per controllare le impostazioni e le funzionalità del dispositivo con Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6bdf714a-5d93-485c-8b52-513635c60cb6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 3627b28b60908c225ce1797968123ce854a70a8b
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="android-and-samsung-knox-standard-device-restriction-settings-in-microsoft-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Android e Samsung KNOX Standard in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

## <a name="general"></a>Generale

|||||
|-|-|-|-|
|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|**Fotocamera**|Consente l'uso della fotocamera del dispositivo.|Sì|sì|
|**Copia e Incolla**|Consente le funzioni Copia e Incolla nel dispositivo.|No|sì|
|**Condivisione degli Appunti tra app**|Consente l'uso degli Appunti per copiare e incollare dati tra app.|No|sì|
|**Invio dati diagnostici**|Impedisce all'utente di inviare dati di diagnostica dal dispositivo.|No|sì|
|**Ripristino impostazioni predefinite**|Consente all'utente di eseguire il ripristino delle impostazioni di fabbrica del dispositivo.|No|sì|
|**Georilevazione**|Consente al dispositivo di usare le informazioni sulla posizione (solo Samsung KNOX Standard).|No|sì|
|**Spegnimento**|Consente all'utente di spegnere il dispositivo.<br>Se questa impostazione è disabilitata, l'impostazione **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** per i dispositivi Samsung KNOX Standard non funziona.|No|sì|
|**Acquisizione schermo**|Consente all'utente di acquisire il contenuto della schermata come immagine.|No|sì|
|**Assistente vocale**|Consente di usare il software di Assistente vocale sul dispositivo.|No|sì|
|**YouTube**|Consente l'uso dell'app YouTube nel dispositivo.|No|sì|
|**Dispositivi condivisi**|Configurare un dispositivo Samsung KNOX Standard gestito come dispositivo condiviso. In questo modo, gli utenti finali possono accedere e disconnettersi dal dispositivo con le credenziali di Azure AD e il dispositivo viene gestito centralmente e indipendentemente dal fatto che sia o meno in uso.<br>Quando gli utenti finali eseguono l'accesso, possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.|No|sì|

## <a name="password"></a>Password

|||||
|-|-|-|-|
|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|**Password**|Richiede all'utente finale di immettere una password per accedere al dispositivo.|sì|sì|
|**Lunghezza minima password**|Immettere la lunghezza minima della password che l'utente deve configurare, da 4 a 16 caratteri.|sì|sì|
|**Numero massimo di minuti di inattività fino al blocco dello schermo**|Specifica il numero di minuti di inattività prima dello spegnimento dello schermo del dispositivo.|sì|sì|
|**Numero di errori di accesso prima della cancellazione dei dati del dispositivo**|Specifica il numero di errori di accesso consentiti prima della cancellazione del dispositivo.|sì|sì|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.|Sì|sì|
|**Tipo di password richiesto**|Specifica il livello richiesto di complessità delle password e indica se è possibile usare dispositivi biometrici. È possibile scegliere tra:<br><br>    -     **Impostazione predefinita dispositivo**<br>-     **Protezione biometrica bassa**<br>    -     **Almeno numerico**<br>    -     **Complessa numerica**: (numeri consecutivi o ripetuti, ad esempio "1111" o "1234" non sono consentiti)<sup>1</sup><br>    -     **Almeno alfabetico**<br>    -     **Almeno alfanumerico**<br>    -     **Almeno alfanumerico con simboli**|sì|sì|
|**Impedisci riutilizzo delle password precedenti**|Impedisce all'utente finale di creare una password che è già stata usata in precedenza.|sì|sì|
|**Sblocco con impronta digitale**|Consente di usare un'impronta digitale per sbloccare i dispositivi supportati.|No|sì|
|**Smart Lock e altri agenti di attendibilità**|Consente di controllare la funzionalità Smart Lock su dispositivi Android compatibili (Samsung KNOX Standard 5.0 e versioni successive). Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se quest'ultimo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire agli utenti di configurare Smart Lock.|Sì (5.0 e versioni successive)|sì|
|**Crittografia**|Richiede la crittografia dei file nel dispositivo.|sì|sì|

<sup>1</sup>Prima di assegnare questa impostazione ai dispositivi, assicurarsi che l'app Portale aziendale sia stata aggiornata alla versione più recente nei dispositivi di destinazione.

Se viene configurata l'impostazione **Complessa numerica** e viene assegnata a un dispositivo che esegue una versione di Android precedente alla versione 5.0, si applica il comportamento seguente.
- Se l'app Portale aziendale sta eseguendo una versione precedente alla 1704, non verranno applicati criteri PIN al dispositivo e verrà visualizzato un errore nel portale di Intune.
- Se l'app Portale aziendale è stata aggiornata alla versione 1704, verrà applicato solo un PIN semplice. Le versioni di Android precedenti alla versione 5.0 non supportano questa impostazione. Nessun errore viene visualizzato nel portale di Intune.


## <a name="google-play-store"></a>Google Play Store

|||||
|-|-|-|-|
|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|**Google Play Store**|Consente all'utente di accedere a Google Play Store sul dispositivo|No|sì|

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

Un elenco **App non consentite** - Elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire.
Un elenco **App approvate** - Elenca le app che gli utenti sono autorizzati a installare. Per garantire la conformità, non installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite.
I profili dispositivo che contengono impostazioni per app con restrizioni devono essere assegnati ai gruppi di utenti.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL di app nell'elenco di app conformi e non conformi, seguire questa procedura:

Nella [sezione delle app di Google Play](https://play.google.com/store/apps), cercare l'app da usare.

Aprire la pagina di installazione relativa all'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app conformi e non conformi.

Esempio: Cercare Microsoft Office Mobile in Google Play. L'URL usato sarà **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

### <a name="additional-options"></a>Opzioni aggiuntive

È possibile anche fare clic su **Importa** per popolare l'elenco da un file CSV nel formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** per creare un file CSV che abbia come contenuto l'elenco delle app con restrizioni nello stesso formato.        

## <a name="browser"></a>Browser
|||||
|-|-|-|-|
|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|**Web browser**|Specifica se è consentito l'uso del Web browser predefinito nel dispositivo.|No|sì|
|**Riempimento automatico**|Consente di usare la funzione di riempimento automatico del Web browser.|No|sì|
|**Cookie**|Consente l'uso dei cookie nel Web browser del dispositivo.|No|sì|
|**JavaScript**|Consente al Web browser del dispositivo di eseguire gli script JavaScript.|No|sì|
|**Popup**|Consente di usare un blocco popup nel Web browser.|No|sì|

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
|||||
|-|-|-|-|
|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|**Backup di Google**|Consente l'uso del backup di Google.|No|sì|
|**Sincronizzazione automatica dell'account Google**|Consente la sincronizzazione automatica delle impostazioni dell'account Google.|No|sì|
|**Archivi rimovibili**|Consente al dispositivo di usare archivi rimovibili, ad esempio una scheda SD.|No|sì|
|**Crittografia sulle schede di memoria**|Specifica se la scheda di memoria del dispositivo deve essere crittografata.|No|sì|

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività
|||||
|-|-|-|-|
|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|**Roaming dati**|Consente dati in roaming quando il dispositivo si trova in una rete cellulare.|No|sì|
|**Messaggi SMS/MMS**|Consente l'uso di messaggi SMS e MMS sul dispositivo.|No|sì|
|**Chiamata vocale**|Attiva o disattiva la funzionalità di composizione vocale sul dispositivo.|No|sì|
|**Roaming vocale**|Consente il roaming vocale quando il dispositivo si trova in una rete cellulare.|No|sì|
|**Bluetooth**|Consente di usare il Bluetooth nel dispositivo.|No|sì|
|**NFC**|Consente l'uso della tecnologia NFC (Near Field Communication) se il dispositivo la supporta.|No|sì|
|**Wi-Fi**|Consente di usare le funzionalità Wi-Fi del dispositivo.|No|sì|
|**Tethering Wi-Fi**|Consente di usare il tethering Wi-Fi nel dispositivo.|No|sì|

## <a name="kiosk"></a>Modalità tutto schermo
|||||
|-|-|-|-|
|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|**Selezionare un'app gestita**|Individuare e selezionare l'app gestita che può essere eseguita quando il dispositivo è in modalità tutto schermo. Le app specificate come collegamento allo store non sono attualmente supportate. Non sarà possibile eseguire altre applicazioni nel dispositivo.|No|sì|
|**Pulsante Sospensione schermo**|Abilita o disabilita il pulsante di riattivazione sospensione dello schermo del dispositivo.|No|sì|
|**Pulsanti volume**|Abilita o disabilita l'uso dei pulsanti del volume nel dispositivo.|No|Sì|

