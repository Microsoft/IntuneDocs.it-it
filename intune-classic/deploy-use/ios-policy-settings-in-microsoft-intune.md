---
title: Impostazioni dei criteri di iOS
description: Creare criteri per il controllo delle impostazioni e delle funzionalità dei dispositivi iOS gestiti con Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 11/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9785078341c8e3469067042a3f3e8588f29c3a3b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="ios-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di iOS in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune offre una gamma di impostazioni generali predefinite che è possibile configurare nei dispositivi iOS. È anche possibile usare lo strumento Apple Configurator per creare impostazioni personalizzate non disponibili in Intune.

## <a name="general-configuration-policy-settings"></a>Impostazioni dei criteri di configurazione generali

Usare i **criteri di configurazione generali iOS** di Microsoft Intune per configurare:

-   **Impostazioni generali e di sicurezza del dispositivo**. Scegliere da un elenco di impostazioni predefinite che consentono di controllare una gamma di funzionalità e caratteristiche nel dispositivo.

-   **Modalità tutto schermo**. Bloccare un dispositivo per consentire solo l'uso di determinate funzionalità. Ad esempio, è possibile consentire a un dispositivo di eseguire solo un'app gestita specificata o disabilitare i pulsanti del volume in un dispositivo. Queste impostazioni potrebbero essere usate per un modello demo di un dispositivo o per un dispositivo dedicato all'esecuzione di una sola funzione, ad esempio un dispositivo POS.

-   **App conformi e non conformi**. Specificare un elenco di app conformi o non conformi rispetto ai requisiti aziendali. Nei dispositivi Android e iOS è possibile usare il **Report app non conformi** per visualizzare la conformità delle app specificate nell'elenco rispetto a quelle installate dagli utenti, senza impedire l'effettiva installazione dell'app.

> [!TIP]
> È possibile configurare i termini e le condizioni per essere sicuri che gli utenti siano informati del fatto che le app installate nel dispositivo, incluse quelle personali, verranno valutate e che le app non conformi verranno bloccate o segnalate come non conformi. Gli utenti dovranno quindi accettare questi termini e condizioni prima di poter registrare il dispositivo e usare il Portale aziendale per ottenere le app. Per altre informazioni sull'uso di termini e condizioni, vedere [Impostazioni dei criteri relativi a termini e condizioni in Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se l'impostazione che si sta cercando non viene visualizzata in questo argomento, è possibile crearla usando i criteri personalizzati iOS che consentono di importare le impostazioni create usando lo [strumento Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Per altre informazioni, vedere "Impostazioni di criteri personalizzati" più avanti in questo argomento.

### <a name="security-settings"></a>Impostazioni di sicurezza
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.


|                                           Nome impostazione                                            |                                                            Dettagli                                                             |
|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
|                   <strong>Richiedi una password per sbloccare i dispositivi mobili</strong>                    |                        Specificare se l'utente deve inserire una password per accedere al proprio dispositivo.                        |
|                              <strong>Tipo di password richiesto</strong>                              |                   Specificare il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.                    |
|                <strong>Numero di caratteri complessi richiesti nella password</strong>                 | Specificare il numero di simboli, ad esempio <strong>#</strong> o <strong>@</strong>, che è necessario includere nella password. |
|                             <strong>Lunghezza minima password</strong>                              |                                   Specificare il numero minimo di caratteri per la password.                                    |
|                              <strong>Consenti password semplici</strong>                              |                          Consentire l'uso di password semplici come <strong>0000</strong> e <strong>1234</strong>.                          |
|     <strong>Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo</strong>      |                       Specificare il numero di tentativi di accesso non riusciti prima che questa impostazione cancelli il dispositivo.                        |
|          <strong>Minuti di inattività prima che venga richiesta la password</strong><sup>1</sup>           |                   Specificare per quanto tempo il dispositivo può rimanere inattivo prima che l'utente debba immettere di nuovo la password.                    |
|                            <strong>Scadenza password (giorni)</strong>                            |                             Specificare il numero di giorni prima che sia necessario modificare la password del dispositivo.                             |
|                            <strong>Ricorda cronologia password</strong>                             |                           Specificare se l'utente può scegliere password già usate in precedenza.                           |
| <strong>Ricorda cronologia password</strong> – <strong>Impedisci riutilizzo delle password precedenti</strong> |                           Specificare il numero di password usate in precedenza che il dispositivo deve ricordare.                           |
|            <strong>Minuti di inattività prima dello spegnimento dello schermo</strong><sup>1</sup>             |                             Specifica il numero di minuti prima dello spegnimento dello schermo del dispositivo.                             |
|                             <strong>Consenti sblocco tramite impronta digitale</strong>                             |                                        Consente di sbloccare il dispositivo con un'impronta digitale.                                         |

<sup>1</sup> Nei dispositivi iOS, se le impostazioni **Minuti di inattività prima dello spegnimento dello schermo** e **Minuti di inattività prima che venga richiesta la password** sono configurate, vengono applicate in sequenza. Ad esempio, se si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo 5 minuti e il dispositivo viene bloccato dopo altri 5 minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio, il dispositivo viene bloccato 5 minuti dopo che l'utente spegne lo schermo.

### <a name="system-settings"></a>Impostazioni di sistema
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti screenshot**|Consentire all'utente di acquisire il contenuto della schermata come immagine.|
|**Consenti centro di controllo nella schermata di blocco**|Consentire all'utente di accedere all'app centro di controllo mentre il dispositivo è bloccato.|
|**Consenti visualizzazione notifiche nella schermata di blocco**|Consente all'utente di accedere alla visualizzazione delle notifiche senza sbloccare il dispositivo.|
|**Consenti visualizzazione Oggi nella schermata di blocco**|Consentire all'utente di visualizzare le notifiche quando il dispositivo è bloccato.|
|**Consenti certificati TLS (Transport Layer Security) non attendibili**|Consente l'uso di certificati TLS non attendibili nel dispositivo.|
|**Consenti invio dati di diagnostica**|Consente o blocca l'invio di dati di diagnostica ad Apple dal dispositivo.|
|**Consenti passbook durante il blocco**|Consente all'utente di accedere all'app Passbook mentre il dispositivo è bloccato.|

### <a name="cloud-settings-for-documents-and-data"></a>Impostazioni cloud per documenti e dati
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti backup su iCloud**|Consentire all'utente di eseguire il backup del dispositivo su iCloud.|
|**Consenti sincronizzazione documenti in iCloud**|Consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.|
|**Consenti sincronizzazione streaming foto in iCloud**|Consente agli utenti di abilitare la funzionalità **Il mio streaming foto** nel dispositivo, che consente di sincronizzare le foto su iCloud in modo che siano disponibili in tutti i dispositivi degli utenti.|
|**Richiedi backup crittografato**|Richiede la crittografia di tutti i backup del dispositivo.|
|**Consenti alle app gestite di sincronizzare i dati in iCloud**|Consentire alle app gestite con Intune di sincronizzare i dati con l'account iCloud dell'utente.|
|**Consenti a Handoff di continuare le attività in un altro dispositivo**|Consentire all'utente di proseguire il lavoro iniziato in un dispositivo iOS in un altro dispositivo iOS o Mac OS X.|
|**Consenti la condivisione di foto con iCloud**|Impostare su **No** per disabilitare **Condivisione foto di iCloud** nel dispositivo.|
|**Consenti la raccolta di foto con iCloud**|Se impostata su **No**, disabilita l'uso della libreria foto di iCloud che consente agli utenti di archiviare foto e video nel cloud.   Eventuali foto non scaricate completamente dalla Libreria foto di iCloud nel dispositivo verranno rimosse dal dispositivo se questa opzione è impostata su **No**.|

### <a name="application-settings-for-the-browser"></a>Impostazioni dell'applicazione per il browser
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti Safari**|Specifica se il browser Safari può essere usato nel dispositivo.|
|**Consenti riempimento automatico**|Consentire all'utente di modificare le impostazioni di completamento automatico nel browser.|
|**Consenti blocco popup**|Attiva o disattiva il blocco dei popup del browser.|
|**Consenti cookie**|Consentire l'uso dei cookie nel browser.|
|**Consenti scripting Java**|Consente l'esecuzione di script Java nel browser.|
|**Consenti avviso illeciti**|Consentire gli avvisi di illeciti nel browser.|

### <a name="application-settings-for-apps"></a>Impostazioni dell'applicazione per le app
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti l'installazione di app**|Consentire al dispositivo di accedere all'App Store e installare le app.|
|**Richiedi una password per accedere all'archivio applicazioni**|Richiedere all'utente di immettere la password prima di visitare l'App Store.|
|**Consenti acquisti in-app**|Consente gli acquisti online dall'interno di un'app in esecuzione.|
|**Consenti documenti gestiti in altre app non gestite**|Consente di visualizzare documenti aziendali in qualsiasi app.<br>**Esempio:** si vuole impedire agli utenti il salvataggio di file dall'app OneDrive a Dropbox. Disabilitare questa impostazione. Dopo aver ricevuto i criteri, ad esempio dopo un riavvio, il dispositivo non consentirà più il salvataggio.|
|**Consenti documenti non gestiti in altre app gestite**|Consente di visualizzare qualsiasi documento nelle app aziendali gestite.|
|**Consenti videoconferenza**|Consentire l'uso di applicazioni di videoconferenza come Facetime sul dispositivo.|
|**Consenti all'utente di considerare attendibili nuovi autori di app aziendali**|Consentire all'utente di scegliere di considerare attendibili le app che non sono state scaricate dall'App Store.|


### <a name="application-settings-for-games"></a>Impostazioni dell'applicazione per i giochi
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti l'aggiunta di amici al Game Center**|Consente all'utente di aggiungere amici in Game Center.|
|**Consenti la modalità di gioco multiplayer**|Consente all'utente di partecipare a giochi multiplayer sul dispositivo.|

### <a name="application-settings-for-media-content"></a>Impostazioni dell'applicazione per i contenuti multimediali
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Area classificazioni**|Selezionare un'area, quindi selezionare la classificazione massima che gli utenti possono scaricare per **film**, **show televisivi** e **app**.|
|**Consenti contenuti per adulti nell'archivio multimediale**|Consente al dispositivo di accedere ai contenuti dell'archivio classificati come per adulti.|
|**Consenti all'utente di scaricare contenuti da iBook Store contrassegnati come 'Erotici'**|Consentire all'utente di scaricare libri della categoria "Erotici".|


### <a name="device-capabilities-settings-for-hardware"></a>Impostazioni delle funzionalità del dispositivo per l'hardware
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti la fotocamera**|Specificare se è consentito l'uso della fotocamera del dispositivo.|
|**Forza gli Apple Watch associati a usare il rilevamento del polso**|Se abilitata, l'Apple Watch non visualizza notifiche se non è indossato.|
|**Richiedi una password di associazione per le richieste AirPlay in uscita**|Richiedere una password di associazione quando l'utente usa AirPlay per trasmettere i contenuti ad altri dispositivi di Apple.|

### <a name="device-capabilities-settings-for-cellular"></a>Impostazioni delle funzionalità del dispositivo per il cellulare
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti roaming vocale**|Consente il roaming vocale quando il dispositivo è su una rete cellulare.|
|**Consenti roaming dei dati**|Consentire il roaming dei dati quando il dispositivo si trova su una rete cellulare.|
|**Consenti recupero in background globale durante il roaming**|Consente al dispositivo di recuperare dati come la posta elettronica durante il roaming su una rete cellulare.|

### <a name="device-capabilities-settings-for-features"></a>Impostazioni delle funzionalità del dispositivo per le funzionalità
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|-------|
|**Consenti Siri**|Consente l'uso dell'assistente vocale Siri sul dispositivo.|
|**Consenti Siri quando il dispositivo è bloccato**|Consente l'uso dell'assistente vocale Siri quando il dispositivo è bloccato.|
|**Consenti la composizione vocale**|Consente l'uso della funzionalità di composizione vocale sul dispositivo.|
|**Non consentire AirDrop dalle app gestite**|Impedisce alle app gestite di inviare dati tramite AirDrop.|


### <a name="settings-for-compliant-and-noncompliant-apps"></a>Impostazioni per le app conformi e non conformi
Nell'elenco **App conformi &amp; non conformi** specificare un elenco di app conformi o non conformi usando le informazioni seguenti.

> [!NOTE]
> Un singolo criterio può contenere solo un elenco di app conformi o non conformi. Non è possibile specificare entrambi nello stesso criterio.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Segnala la mancata conformità quando gli utenti installano le app elencate**|Elencare le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire.|
|**Segnala la mancata conformità quando gli utenti installano app non elencate**|Elencare le app che gli utenti sono autorizzati a installare. Per garantire la conformità, non installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite.|
|**Aggiungi**|Aggiungere un'app all'elenco selezionato. Specificare un nome desiderato, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store. Per altre informazioni, vedere "Come specificare gli URL negli App Store" più avanti in questo argomento.|
|**Importa app**|Importare un elenco di app specificate in un file con valori delimitati da virgole. Nel file usare il formato: nome dell'applicazione, autore, URL dell'app.|
|**Modifica**|Modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Eliminare l'app selezionata dall'elenco.|

I criteri contenenti le impostazioni per le app conformi e non conformi devono essere distribuiti ai gruppi di utenti.

### <a name="kiosk-mode-settings"></a>Impostazioni della modalità tutto schermo

|                                            Nome impostazione                                            |                                                                                                                                      Dettagli                                                                                                                                       |
|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo</strong> | Scegliere <strong>Sfoglia</strong>, quindi specificare l'app gestita o un'app di uno Store che potrà essere eseguita quando il dispositivo è in modalità tutto schermo. Non sarà possibile eseguire altre applicazioni nel dispositivo. Per informazioni, vedere "Come specificare gli URL negli App Store" più avanti in questo argomento. |
|                                    <strong>Consenti tocco</strong>                                    |                                                                                                                  Abilitare o disabilitare il touchscreen nel dispositivo.                                                                                                                  |
|                               <strong>Consenti rotazione schermo</strong>                               |                                                                                                Abilitare o disabilitare la modifica dell'orientamento dello schermo quando si ruota il dispositivo.                                                                                                 |
|                               <strong>Consenti pulsanti volume</strong>                                |                                                                                                           Abilitare o disabilitare l'uso dei pulsanti del volume nel dispositivo.                                                                                                           |
|                                <strong>Consenti commutatore suoneria</strong>                                |                                                                                                             Abilitare o disabilitare la suoneria nel dispositivo.                                                                                                              |
|                          <strong>Consenti pulsante riattivazione sospensione schermo</strong>                           |                                                                                                           Abilitare o disabilitare il pulsante di riattivazione sospensione dello schermo del dispositivo.                                                                                                            |
|                                  <strong>Consenti blocco automatico</strong>                                  |                                                                                                                 Abilitare o disabilitare il blocco automatico del dispositivo.                                                                                                                 |
|                                 <strong>Abilita audio mono</strong>                                 |                                                                                                      Abilitare o disabilitare l'impostazione di accessibilità <strong>Audio mono</strong>.                                                                                                      |
|                                 <strong>Abilita voice over</strong>                                 |                                                                               Abilitare o disabilitare l'impostazione di <strong>Voice over</strong> per la lettura a voce alta del testo sullo schermo del dispositivo.                                                                                |
|                           <strong>Abilita regolazioni voice over</strong>                           |                                                                  Abilitare o disabilitare le regolazioni di voice over che consentono di modificare la funzione Voice over, ad esempio la velocità con cui viene letto il testo visualizzato sullo schermo.                                                                   |
|                                    <strong>Abilita zoom</strong>                                    |                                                                         Abilitare o disabilitare l'impostazione di accessibilità <strong>Zoom</strong> che consente di usare le funzionalità di tocco per ingrandire la visualizzazione del dispositivo.                                                                         |
|                              <strong>Abilita regolazioni zoom</strong>                              |                                                                                                  Abilitare o disabilitare le regolazioni dello zoom che consentono di modificare la funzione di zoom.                                                                                                  |
|                               <strong>Abilita inversione colori</strong>                                |                                                                    Abilitare o disabilitare l'impostazione di accessibilità <strong>Inverti colori</strong> che consente di regolare la visualizzazione per gli utenti con problemi visivi.                                                                    |
|                         <strong>Abilita regolazioni inversione colori</strong>                          |                                                                                         Abilitare o disabilitare le regolazioni dell'inversione colori che consentono di modificare la funzione Inverti colori.                                                                                         |
|                              <strong>Abilita tocco per l'accesso facilitato</strong>                               |                                                     Abilitare o disabilitare l'impostazione di accessibilità <strong>Tocco per l'accesso facilitato</strong> che aiuta l'utente a eseguire sullo schermo movimenti che altrimenti risulterebbero difficili da eseguire.                                                     |
|                        <strong>Abilita regolazioni del tocco per l'accesso facilitato</strong>                         |                                                                                       Abilitare o disabilitare le regolazioni del tocco per l'accesso facilitato che consentono all'utente di modificare la funzione Tocco per l'accesso facilitato.                                                                                       |
|                              <strong>Abilita selezione comandi vocali</strong>                              |                                                                        Abilitare o disabilitare l'impostazione di accessibilità <strong>Abilita selezione comandi vocali</strong> che consente di leggere a voce alta il testo selezionato.                                                                         |

> [!NOTE]
> Le note seguenti sono valide per le impostazioni della modalità tutto schermo per i dispositivi iOS:
>
> -   Prima di poter configurare un dispositivo iOS per la modalità tutto schermo, è necessario usare lo [strumento Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) o il [programma di registrazione dispositivi di Apple](ios-device-enrollment-program-in-microsoft-intune.md) per inserire il dispositivo in modalità di supervisione. Per altre informazioni sullo strumento Apple Configurator, vedere la documentazione di Apple.
> -   Se l'app per iOS specificata viene installata dopo aver distribuito i criteri di configurazione, il dispositivo non passerà alla modalità tutto schermo finché non viene riavviato.

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Informazioni di riferimento per le app conformi e non conformi

Usare **Report app non conformi** per visualizzare la conformità delle app consentite e bloccate.

##### <a name="to-run-the-noncompliant-apps-report"></a>Per eseguire il report app non conformi

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Report** &gt; **Report app non conformi**.

2.  Selezionare i gruppi di dispositivi da controllare, scegliere se verificare la presenza di app conformi, di app non conformi o di entrambi i tipi di app, quindi scegliere **Visualizza report**.

#### <a name="how-to-specify-urls-to-app-stores"></a>Come specificare gli URL negli App Store
Per specificare un URL dell'app nell'elenco delle app conformi e non conformi o nell'opzione **Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo** (solo iOS), usare uno dei formati seguenti:

1. Usando un motore di ricerca, trovare l'app da usare nell'App Store iTunes e aprire la pagina per l'app.

2. Copiare l'URL della pagina e usarlo per la configurazione dell'elenco delle app conformi o non conformi o dell'app da eseguire in modalità tutto schermo.

**Esempio:** cercare **Microsoft Word per iPad**. L'URL usato sarà **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> È possibile usare anche il software iTunes per trovare l'app e il comando **Copia collegamento** per ottenere l'URL dell'app.

### <a name="enrollment-settings"></a>Impostazioni di registrazione
Tutte le impostazioni si applicano a iOS 8.0 e versioni successive.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti blocco attivazione quando il dispositivo è in modalità di supervisione**|Abilitare il blocco attivazione su dispositivi iOS con supervisione.|

### <a name="supervised-mode-settings"></a>Impostazioni della modalità di supervisione
Nei dispositivi che eseguono iOS 8.0 e versioni successive in modalità di supervisione possono essere configurate le impostazioni seguenti.

### <a name="supervised-mode-settings-for-device-restrictions"></a>Impostazioni della modalità di supervisione per restrizioni del dispositivo

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti la modifica dell'account**|Consente all'utente di modificare le impostazioni dell'account, ad esempio le configurazioni di posta elettronica.|
|**Consenti le modifiche alle impostazioni dell'utilizzo della rete dati dell'app**|Consente all'utente di controllare le app che possono usare la rete dati.|
|**Consenti l'uso dell'opzione di cancellazione di tutti i contenuti e tutte le impostazioni sul dispositivo**|Consentire all'utente di usare l'opzione per cancellare tutti i contenuti e tutte le impostazioni sul dispositivo.|
|**Consenti all'utente di abilitare restrizioni nelle impostazioni del dispositivo**|Consentire all'utente di configurare restrizioni, come il controllo genitori, sul dispositivo.|
|**Consenti l'associazione di host per controllare i dispositivi a cui può essere associato un dispositivo iOS**|Consentire l'associazione di host in modo che l'amministratore possa controllare a quali dispositivi può essere associato un dispositivo iOS.|
|**Consente all'utente di installare profili di configurazione e certificati.**|Consente all'utente di installare profili di configurazione e certificati.|
|**Consenti la modifica del nome dispositivo**|Consentire all'utente di modificare il nome del dispositivo.|
|**Consenti la modifica del passcode**|Consentire l'aggiunta, la modifica o la rimozione della password del dispositivo.|
|**Consenti l'associazione di Apple Watch**|Consentire al dispositivo di associare un Apple Watch.|
|**Consenti la modifica delle impostazioni di notifica**|Consentire all'utente di modificare le impostazioni di notifica del dispositivo.|
|**Consenti la modifica dello sfondo**|Consentire all'utente di modificare lo sfondo del dispositivo.|

### <a name="supervised-mode-settings-for-feature-restrictions"></a>Impostazioni della modalità supervisione per restrizioni delle funzionalità

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti AirDrop**|Consentire l'uso della funzionalità AirDrop per scambiare contenuti con i dispositivi presenti nelle vicinanze.|
|**Consenti a Siri di eseguire query sul contenuto generato dall'utente da Internet**|Consentire a Siri di accedere ai siti Web per rispondere alle domande.|
|**Usa il filtro di Siri per le espressioni volgari**|Impedire a Siri di usare espressioni volgari.|
|**Consenti alla ricerca Spotlight di restituire risultati da Internet**|Consentire alla ricerca Spotlight di connettersi a Internet per visualizzare altri risultati.|
|**Consenti la ricerca della definizione delle parole**|Consentire la funzionalità di iOS che permette di evidenziare una parola e cercarne la definizione.|
|**Consenti le tastiere predittive**|Consentire l'uso di tastiere predittive che suggeriscono all'utente i termini desiderati.|
|**Consenti la correzione automatica**|Consentire al dispositivo di correggere automaticamente le parole errate.|
|**Consenti il controllo ortografico tastiera**|Consentire al dispositivo di eseguire il controllo ortografico.|
|**Consenti tasti di scelta rapida**|Consentire l'uso dei tasti di scelta rapida.|

### <a name="supervised-mode-settings-for-app-restrictions"></a>Impostazioni della modalità supervisione per restrizioni dell'app

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Consenti la modifica delle impostazioni di attendibilità delle app aziendali**|Consente agli utenti di modificare le impostazioni di attendibilità per le app aziendali.|
|**Consentire l'installazione di app esclusivamente con la configurazione di Apple e iTunes**|Abilita o disabilita App Store dalla schermata iniziale del dispositivo. Gli utenti possono comunque usare iTunes o lo strumento Apple Configurator per installare e aggiornare le app.|
|**Consenti i download automatici delle app**|Consente di scaricare automaticamente nel dispositivo le app acquistate in altri dispositivi. Questa impostazione non influisce sugli aggiornamenti delle app.|
|**Consenti modifiche alle impostazioni dell'app Find My Friends**|Consente all'utente di modificare le impostazioni dell'app Find My Friend.|
|**Consenti l'accesso all'iBooks Store**|Consente all'utente di selezionare e acquistare libri all'iBooks Store.|
|**Consenti l'uso dell'app Messages sul dispositivo**|Consenti l'uso dell'app Messages per inviare messaggi di testo.|
|**Consenti l'uso di podcast**|Consentire l'uso delle app di podcast.|
|**Consenti l'uso del servizio Music**|Consentire l'uso dell'app Music di Apple.|
|**Consenti il servizio iTunes Radio**|Consentire l'uso dell'app iTunes Radio.|
|**Consenti Apple News**|Consentire l'uso dell'app Apple News.|
|**Consenti Game Center**|Consente l'uso dell'app Game Center.|


### <a name="show-or-hide-apps"></a>Mostrare o nascondere app

Usare **Elenco di app nascoste e mostrate** per controllare quanto riportato di seguito su dispositivi supervisionati che eseguono iOS 9.3 o versione successiva:

- Specificare un elenco di app nascoste agli utenti. Gli utenti non possono visualizzare o avviare queste app.
- Specificare un elenco di app che gli utenti possono visualizzare e avviare. Non è possibile visualizzare o avviare altre app.


#### <a name="how-to-create-a-hidden-or-shown-app-list"></a>Come creare un elenco di app nascoste o mostrate

Specificare le impostazioni seguenti:

|Nome impostazione|Dettagli|
|-|-|
|**Elenco di app nascoste e mostrate**|Abilitare questa impostazione se si vuole creare un elenco di app nascoste o mostrate.|
|**Nascondi le app elencate dagli utenti**|Selezionare questa opzione se si vuole creare un elenco di app che verranno nascoste agli utenti.<br>Quando si crea questo tipo di elenco, tutte le app, ad eccezione di **Impostazioni** e **Telefono** (per iPhone), possono essere nascoste.|
|**Mostra solo le app elencate agli utenti**|Selezionare questa opzione se si vuole creare un elenco di app visualizzate agli utenti.<br>Quando si crea questo tipo di elenco, tutte le altre app, ad eccezione di **Impostazioni** e **Telefono** (per iPhone), vengono nascoste.<br>È inoltre necessario aggiungere all'elenco il portale aziendale e qualsiasi app distribuita e gestita con Intune.|
|**Aggiungi**|Aggiunge un'app all'elenco selezionato.<br>Per quanto riguarda l'elenco delle app nascoste, è necessario specificare **Nome**, **Autore** e **URL app o ID bundle** di ciascuna app che si vuole nascondere.<br>Per quanto riguarda l'elenco delle app mostrate, è possibile scegliere l'opzione **Selezionare un'app gestita**, che fornisce un elenco delle app gestite con Intune, oppure scegliere l'opzione Selezionare un'app dello Store. È quindi necessario specificare **Nome**, **Autore** e **URL app o ID bundle** di ciascuna app che si vuole visualizzare.|
|**Importa app**|Importa un elenco di app specificate in un file con valori delimitati da virgole. Per il file usare il formato nome applicazione, autore, URL.|
|**Modifica**|Consente di modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Elimina l'app selezionata dall'elenco.|

#### <a name="app-information-for-built-in-ios-apps"></a>Informazioni per app iOS incorporate

Usare le informazioni riportate in questo elenco per identificare il nome, l'autore e l'ID bundle delle app iOS incorporate che si vogliono mostrare o nascondere. Se si vogliono mostrare o nascondere tutte le app dell'elenco, è possibile copiare i dati riportati di seguito in un file di testo con estensione **csv** e quindi usare l'opzione **Importa app** per importare tutte le app contemporaneamente.

```
,com.apple.AppStore,App Store,Apple
,com.apple.calculator,Calculator,Apple
,com.apple.mobilecal,Calendar,Apple
,com.apple.camera,Camera,Apple
,com.apple.mobiletimer,Clock,Apple
,com.apple.compass,Compass,Apple
,com.apple.MobileAddressBook,Contacts,Apple
,com.apple.facetime,FaceTime,Apple
,com.apple.mobileme.fmf1,Find Friends,Apple
,com.apple.mobileme.fmip1,Find iPhone,Apple
,com.apple.gamecenter,Game Center,Apple
,com.apple.mobilegarageband,GarageBand,Apple
,com.apple.Health,Health,Apple
,com.apple.iBooks,iBooks,Apple
,com.apple.MobileStore,iTunes Store,Apple
,com.apple.itunesu,iTunes U,Apple
,com.apple.Keynote,Keynote,Apple
,com.apple.mobilemail,Mail,Apple
,com.apple.MapsMaps,Apple
,com.apple.MobileSMS,Messages,Apple
,com.apple.Music,Music,Apple
,com.apple.news,News,Apple
,com.apple.mobilenotes,Notes,Apple
,com.apple.Numbers,Numbers,Apple
,com.apple.Pages,Pages,Apple
,com.apple.Photo-Booth,Photo Booth,Apple
,com.apple.mobileslideshow,Photos,Apple
,com.apple.podcasts,Podcasts,Apple
,com.apple.reminders,Reminders,Apple
,com.apple.MobileSafari,Safari,Apple
,com.apple.Preferences,Settings,Apple
,com.apple.stocks,Stocks,Apple
,com.apple.tips,Tips,Apple
,com.apple.videos,Videos,Apple
,com.apple.VoiceMemos,VoiceMemos,Apple
,com.apple.Passbook,Wallet,Apple
,com.apple.Bridge,Watch,Apple
,com.apple.weather,Weather,Apple
```




## <a name="custom-policy-settings"></a>Impostazioni di criteri personalizzati

Usare i **criteri di configurazione personalizzati iOS** di Microsoft Intune per distribuire le impostazioni create con lo strumento [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) nei dispositivi iOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione in un criterio personalizzato iOS di Intune e distribuire le impostazioni a utenti e dispositivi nella propria organizzazione.

Questa funzionalità consente di distribuire le impostazioni di iOS che non possono essere configurate con i criteri di configurazione generali di Intune.

### <a name="prerequisites"></a>Prerequisiti
Prima di iniziare, è necessario aver installato lo strumento Apple Configurator e creato un file di configurazione contenente le impostazioni da distribuire a utenti o dispositivi. È possibile scaricare e acquisire informazioni su Apple Configurator da [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12).

> [!NOTE]
> Intune non segnala la conformità delle singole impostazioni in un criterio personalizzato iOS. Tuttavia, viene segnalata la conformità generale del criterio.

### <a name="general-settings"></a>Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio personalizzato iOS, che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio personalizzato iOS e altre informazioni rilevanti per consentirne l'individuazione.|

### <a name="custom-settings"></a>Impostazioni personalizzate

|Nome impostazione|Dettagli|
    |----------------|--------------------|
|**Nome del profilo di configurazione personalizzato (visualizzato agli utenti)**|Specificare il nome con cui il criterio verrà visualizzato nel dispositivo e nei report dei criteri di Intune.|
|**File del profilo di configurazione**|Scegliere **Importa**, quindi selezionare il profilo di configurazione creato usando lo strumento Apple Configurator. **Nota:** Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di iOS sui dispositivi su cui vengono distribuiti i criteri personalizzati iOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).|
    |**Dettagli del profilo di configurazione**|Visualizzare il codice XML per il profilo di configurazione importato.|

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
