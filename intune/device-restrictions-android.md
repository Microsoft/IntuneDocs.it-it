---
title: Impostazioni relative alle restrizioni dei dispositivi per Android in Microsoft Intune
titlesuffix: ''
description: Informazioni sulle opzioni di Intune per il controllo di impostazioni e funzionalità nei dispositivi Android.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ayesham, chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 77942ef6a5f25708ce43910cde94133e174b4731
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-android-and-samsung-knox-standard-device-restriction-settings"></a>Impostazioni relative alle restrizioni dei dispositivi Android e Samsung Knox Standard in Microsoft Intune 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo illustra tutte le impostazioni di restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi che eseguono Android.

>[!TIP]
>Se le impostazioni desiderate non sono disponibili, per la configurazione dei dispositivi si potrebbe usare un [profilo personalizzato](custom-settings-android.md).

## <a name="general"></a>Generale

- **Fotocamera** - Consente l'uso della fotocamera del dispositivo.
- **Copia e incolla (solo Samsung Knox)** - Consente le funzioni Copia e Incolla nel dispositivo.
- **Condivisione degli Appunti tra app (solo Samsung Knox)** - Consente l'uso degli Appunti per copiare e incollare tra app.
- **Invio dati di diagnostica (solo Samsung Knox)** - Impedisce all'utente di inviare dati di diagnostica dal dispositivo.
- **Ripristino impostazioni predefinite (solo Samsung Knox)** - Consente all'utente di eseguire il ripristino delle impostazioni predefinite del dispositivo.
- **Georilevazione (solo Samsung Knox)** - Consente al dispositivo di usare le informazioni sulla posizione.
- **Spegnimento (solo Samsung Knox)** - Consente all'utente di spegnere il dispositivo.<br>Se disabilitata, non è possibile impostare **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**.
- **Acquisizione schermo (solo Samsung Knox)** - Consente all'utente di acquisire il contenuto dello schermo come immagine.
- **Assistente vocale (solo Samsung Knox)** - Consente di usare software di assistenza vocale nel dispositivo.
- **YouTube (solo Samsung Knox)** - Consente l'uso dell'app YouTube nel dispositivo.
- **Dispositivi condivisi (solo Samsung Knox)** - Consente di configurare un dispositivo Samsung Knox Standard gestito come dispositivo condiviso. In questa modalità, gli utenti finali possono accedere e disconnettersi dal dispositivo con le credenziali di Azure AD e il dispositivo rimane gestito indipendentemente dal fatto che sia o meno in uso.<br>Quando usata in combinazione con un profilo certificato SCEP, questa funzionalità consente agli utenti di condividere un dispositivo con lo stesso set di app per tutti gli utenti, ma con il proprio certificato utente SCEP.  Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.  Questa funzionalità è limitata alle app LOB.
- **Impedisci modifiche a data e ora (Samsung Knox)** - Consente di impedire all'utente di modificare le impostazioni di data e ora nel dispositivo. 

## <a name="password"></a>Password

- **Password**: richiede all'utente finale di immettere una password per accedere al dispositivo.|Sì|Sì|
- **Lunghezza minima password** - Immettere la lunghezza minima della password che l'utente deve configurare (da 4 a 16 caratteri).
- **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il numero di minuti di inattività prima dello spegnimento dello schermo del dispositivo.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Specifica il numero di errori di accesso consentiti prima della cancellazione del dispositivo.
- **Scadenza password (giorni)** - Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.
-  **Tipo di password richiesto** - Specifica il livello richiesto di complessità delle password e indica se è possibile usare dispositivi biometrici. Scegliere tra:
    - **Impostazione predefinita dispositivo**
    - **Protezione biometrica bassa**
    - **Almeno numerico**
    - **Complessa numerica** - Non sono consentiti numeri consecutivi o ripetuti, ad esempio "1111" o "1234"<sup>1</sup>
    - **Almeno alfabetico**
    - **Almeno alfanumerico**
    - **Almeno alfanumerico con simboli**
- **Impedisci riutilizzo delle password precedenti** - Impedisce all'utente finale di creare una password che è già stata usata in precedenza.
- **Impronta digitale sbloccata (solo Samsung Knox)** - Consente di usare un'impronta digitale per sbloccare i dispositivi supportati.
- **Smart Lock e altri agenti di attendibilità** - Consente di controllare la funzionalità Smart Lock su dispositivi Android compatibili (Samsung Knox Standard 5.0 e versioni successive). Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se il dispositivo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire agli utenti di configurare Smart Lock.
- **Crittografia** - Richiede la crittografia dei file nel dispositivo.

<sup>1</sup> Prima di assegnare questa impostazione ai dispositivi, assicurarsi di aggiornare l'app Portale aziendale alla versione più recente in tali dispositivi.

Se viene configurata l'impostazione **Complessa numerica** e viene assegnata a un dispositivo che esegue una versione di Android precedente alla versione 5.0, si applica il comportamento seguente.
- Se l'app Portale aziendale esegue una versione precedente alla 1704, non vengono applicati criteri PIN al dispositivo e viene visualizzato un errore nel portale di Azure.
- Se l'app Portale aziendale esegue la versione 1704 o versioni successive, è possibile applicare solo un PIN semplice. Le versioni di Android precedenti alla versione 5.0 non supportano questa impostazione. Nessun errore viene visualizzato nel portale di Azure.


## <a name="google-play-store"></a>Google Play Store

- **Google Play Store (solo Samsung Knox)** - Consente all'utente di accedere a Google Play Store nel dispositivo.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti sia per dispositivi Android che Samsung Knox Standard:

Un elenco **App non consentite**: elenca le app non gestite da Intune che vengono segnalate se gli utenti le installano e le eseguono.
Un elenco **App approvate** - Elenca le app che gli utenti sono autorizzati a installare. Per garantire la conformità, gli utenti non devono installare altre app. Le app gestite da Intune sono automaticamente consentite.
I profili dispositivo che contengono impostazioni per app con restrizioni devono essere assegnati ai gruppi di utenti.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.

### <a name="how-to-specify-the-url-to-an-app-in-the-store"></a>Come specificare l'URL di un'app nello store

Per specificare un URL di app nell'elenco di app conformi e non conformi, seguire questa procedura:

Nella [sezione delle app di Google Play](https://play.google.com/store/apps), cercare l'app da usare.

Aprire la pagina di installazione relativa all'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app conformi e non conformi.

Esempio: cercare **Microsoft Planner** nella [sezione delle app di Google Play](https://play.google.com/store/apps). Usare l'URL: **https://play.google.com/store/apps/details?id=com.microsoft.planner**.

### <a name="additional-options"></a>Opzioni aggiuntive

È anche possibile fare clic su **Importa** per ottenere l'elenco da un file CSV. Usare il formato <*url app*>, <*nome app*>, <*autore app*> o fare clic su **Esporta** nel file CSV contenente il contenuto dell'elenco delle app con restrizioni nello stesso formato.      

## <a name="browser"></a>Browser

- **Web browser (solo Samsung Knox)** - Specifica se è consentito l'uso del Web browser predefinito del dispositivo.
- **Riempimento automatico (solo Samsung Knox)** - Consente di usare la funzione di riempimento automatico del Web browser.
- **Cookie (solo Samsung Knox)** - Consente l'uso dei cookie nel Web browser del dispositivo.
- **JavaScript (solo Samsung Knox)** - Consente al Web browser del dispositivo di eseguire gli script JavaScript.
- **Popup (solo Samsung Knox)** - Consente di usare il blocco popup nel Web browser.

## <a name="allow-or-block-apps"></a>Consentire o bloccare le app

È possibile usare queste impostazioni per specificare le app che possono essere installate o avviate solo su dispositivi che eseguono Samsung Knox Standard.
È anche possibile specificare le app installate che vengono nascoste all'utente del dispositivo. Gli utenti non possono eseguire queste app.

- **App di cui è consentita l'installazione (solo Samsung Knox Standard)**
- **App di cui non è consentito l'avvio (solo Samsung Knox Standard)**
- **App nascoste all'utente (solo Samsung Knox Standard)**

Per ogni impostazione, configurare un elenco di app usando una delle opzioni seguenti:

- **Aggiungi app per nome del pacchetto**: usata principalmente per le app line-of-business. Immettere il nome dell'app e il nome del pacchetto dell'app.
- **Aggiungi app per URL**: immettere il nome e l'URL dell'app in Google Play Store.
- **Aggiungi app gestite**: nell'elenco di app gestite con Intune selezionare l'app necessaria.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione

- **Backup di Google (solo Samsung Knox)** - Consente l'uso del backup di Google.
- **Sincronizzazione automatica dell'account Google (solo Samsung Knox)** - Consente la sincronizzazione automatica delle impostazioni dell'account Google.
- **Archivi rimovibili (solo Samsung Knox)** - Consente al dispositivo di usare archivi rimovibili, ad esempio una scheda SD.
- **Crittografia sulle schede di memoria (solo Samsung Knox)** - Specifica se la scheda di memoria del dispositivo deve essere crittografata.

## <a name="cellular-and-connectivity"></a>Rete cellulare e connettività

- **Roaming dati (solo Samsung Knox)** - Consente il roaming dati quando il dispositivo si trova in una rete cellulare.
- **Messaggi SMS/MMS (solo Samsung Knox)** - Consente l'uso dei messaggi SMS e MMS nel dispositivo.
- **Chiamata vocale (solo Samsung Knox)** - Abilita o disabilita la funzionalità di composizione vocale nel dispositivo.
- **Roaming vocale (solo Samsung Knox)** - Consente il roaming vocale quando il dispositivo si trova in una rete cellulare.
- **Bluetooth (solo Samsung Knox)** - Consente l'uso di Bluetooth nel dispositivo.
- **NFC (solo Samsung Knox)** - Consente l'uso della tecnologia NFC (Near Field Communication) nei dispositivi supportati.
- **Wi-Fi (solo Samsung Knox)** - Consente l'uso delle funzionalità Wi-Fi nel dispositivo.
- **Tethering Wi-Fi (solo Samsung Knox)** - Consente di usare il tethering Wi-Fi nel dispositivo.

## <a name="kiosk"></a>Modalità tutto schermo

Le impostazioni della modalità tutto schermo si applicano solo ai dispositivi Samsung Knox Standard e solo alle app gestite con Intune.

- **Selezionare un'app gestita**: scegliere una delle opzioni seguenti per aggiungere una o più app gestite che possono essere eseguite quando il dispositivo è in modalità tutto schermo. Non sarà possibile eseguire altre app nel dispositivo. I browser preinstallati non possono essere definiti come app che può essere eseguita mentre il dispositivo è in modalità tutto schermo. Se è richiesto un browser, è consigliabile usare [Managed Browser](app-configuration-managed-browser.md).
    - **Aggiungi app per nome del pacchetto**
    - **Aggiungi app per URL**
    - **Aggiungi app gestite**.
- **Pulsante Sospensione schermo** - Abilita o disabilita il pulsante di sospensione dello schermo del dispositivo.
- **Pulsanti volume**: abilita o disabilita l'uso dei pulsanti del volume del dispositivo.


## <a name="next-steps"></a>Passaggi successivi

Continuare con le istruzioni in [Come configurare le impostazioni relative alle restrizioni dei dispositivi](device-restrictions-configure.md) per creare e quindi assegnare il profilo di restrizione del dispositivo.
