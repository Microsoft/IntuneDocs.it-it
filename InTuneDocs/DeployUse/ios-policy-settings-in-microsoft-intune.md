---
title: Impostazioni dei criteri di iOS | Microsoft Intune
description: "Creare criteri per il controllo delle impostazioni e delle funzionalità dei dispositivi iOS gestiti con Intune."
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab46be6c-ab73-4c99-8492-66d1dd418293
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f9a492a16605130743b943f6aa49d1d633eb97d4
ms.openlocfilehash: 3292df922eeb53108f2b34d4113b0b6c5a114564


---

# Impostazioni dei criteri di iOS in Microsoft Intune

Intune offre una gamma di impostazioni generali incorporate che è possibile configurare nei dispositivi iOS. È anche possibile usare lo strumento Apple Configurator per creare impostazioni personalizzate non disponibili in Intune.

## Impostazioni dei criteri di configurazione generali

Usare i **criteri di configurazione generali iOS** di Microsoft Intune per configurare:

-   **Impostazioni generali e di sicurezza del dispositivo**: scegliere da un elenco di impostazioni predefinite che consentono di controllare una gamma di funzionalità e caratteristiche nel dispositivo.

-   **Modalità tutto schermo**: bloccare un dispositivo per consentire solo l'uso di determinate funzionalità. Ad esempio, è possibile consentire a un dispositivo di eseguire solo un'app gestita specificata o disabilitare i pulsanti del volume in un dispositivo. Queste impostazioni potrebbero essere usate per un modello demo di un dispositivo o per un dispositivo dedicato all'esecuzione di una sola funzione, ad esempio un dispositivo POS.

-   **App conformi e non conformi**: specificare un elenco di app conformi oppure non conformi nella società. Nei dispositivi Android e iOS è possibile usare il **Report app non conformi** per visualizzare la conformità delle app specificate nell'elenco rispetto a quelle installate dagli utenti (ma senza impedire effettivamente l'installazione dell'app).

> [!TIP]
> È possibile configurare i termini e le condizioni per essere sicuri che gli utenti siano informati del fatto che le app installate nel dispositivo, incluse quelle personali, verranno valutate e che le app non conformi verranno bloccate o segnalate come non conformi. Gli utenti dovranno quindi accettare questi termini e condizioni prima di poter registrare il dispositivo e usare il Portale aziendale per ottenere le app. Per altre informazioni sull'uso di termini e condizioni, vedere [Impostazioni dei criteri relativi a termini e condizioni in Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md).

Se l'impostazione desiderata non viene visualizzata in questo argomento, è possibile crearla usando i criteri personalizzati iOS che consentono di importare le impostazioni create tramite lo [strumento Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12). Per altre informazioni, vedere **Impostazioni dei criteri personalizzati** più avanti in questo argomento.

### Impostazioni di sicurezza

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Richiedi una password per sbloccare i dispositivi mobili**|Specifica se gli utenti devono inserire una password per accedere ai loro dispositivi.|Sì|
|**Tipo di password richiesto**|Specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.|sì|
|**Tipo di password richiesto - Numero minimo di set di caratteri**|Specifica il numero di simboli, ad esempio **#** o **@**, che è necessario includere nella password.|sì|
|**Lunghezza minima password**|Specifica il numero minimo di caratteri per la password.|sì|
|**Consenti password semplici**|Consente l'uso di password semplici come "0000" e "1234".|sì|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Cancella il dispositivo se questo numero di tentativi di accesso ha esito negativo.|sì|
|**Minuti di inattività prima dello spegnimento dello schermo**<sup>1</sup>|Specifica il numero di minuti prima dello spegnimento dello schermo del dispositivo.|Sì|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.|Sì|
|**Ricorda cronologia password**|Specifica se l'utente può adottare password già usate in precedenza.|Sì|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare.|Sì|
|**Minuti di inattività prima che venga richiesta la password**<sup>1</sup>|Specifica il tempo per cui il dispositivo può rimanere inattivo prima che l'utente debba immettere di nuovo la password.|sì|
|**Consenti sblocco delle impronte digitali**|Consente di sbloccare il dispositivo con un'impronta digitale.|iOS 7.1 e versioni successive|
<sup>1</sup> Nei dispositivi iOS, se le impostazioni **Minuti di inattività prima dello spegnimento dello schermo** e **Minuti di inattività prima che venga richiesta la password** sono configurate, vengono applicate in sequenza. Ad esempio, se si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo 5 minuti e il dispositivo viene bloccato dopo altri 5 minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio, il dispositivo viene bloccato 5 minuti dopo che l'utente spegne lo schermo.

### Impostazioni di sistema

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti screenshot**|Consente all'utente di acquisire il contenuto della schermata come immagine.|Sì|
|**Consenti centro di controllo nella schermata di blocco**|Controlla se l'applicazione di centro di controllo è accessibile quando il dispositivo è bloccato.|iOS 7.1 e versioni successive|
|**Consenti visualizzazione notifiche nella schermata di blocco**|Consente all'utente di accedere alla visualizzazione delle notifiche senza sbloccare il dispositivo.|iOS 7.1 e versioni successive|
|**Consenti visualizzazione Oggi nella schermata di blocco**|Controlla se è possibile visualizzare le notifiche quando il dispositivo è bloccato.|iOS 7.1 e versioni successive|
|**Consenti invio dati di diagnostica**|Consente o blocca l'invio di dati di diagnostica ad Apple dal dispositivo.|sì|
|**Consenti certificati TLS (Transport Layer Security) non attendibili**|Consente l'uso di certificati TLS non attendibili nel dispositivo.|Sì|
|**Consenti passbook durante il blocco**|Consente all'utente di accedere all'app Passbook mentre il dispositivo è bloccato.|sì|

### Impostazioni cloud - Documenti e dati

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti backup su iCloud**|Consente all'utente di eseguire il backup del dispositivo su iCloud.|Sì|
|**Consenti sincronizzazione documenti su iCloud**|Consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.|sì|
|**Consenti sincronizzazione streaming foto su iCloud**|Consente la sincronizzazione delle foto del dispositivo su iCloud.|sì|
|**Richiedi backup crittografato**|Richiede la crittografia di tutti i backup del dispositivo.|sì|

### Impostazioni dell'applicazione - Browser

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti Safari**|Specifica se il browser Safari può essere usato nel dispositivo.|Sì|
|**Consenti riempimento automatico**|L’utente può modificare le impostazioni di completamento automatico nel browser.|Sì|
|**Consenti blocco popup**|Attiva o disattiva il blocco dei popup del browser.|sì|
|**Consenti cookie**|Consente l'uso dei cookie nel Web browser del dispositivo.|Sì|
|**Consenti scripting Java**|Consente l'esecuzione di script Java nel browser.|sì|
|**Consenti avviso illeciti**|Consente gli avvisi di illeciti nel browser del dispositivo.|Sì|

### Impostazioni dell'applicazione - App

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti archivio applicazioni**|Consente al dispositivo di accedere all'App Store.|sì|
|**Richiedi una password per accedere all'archivio applicazioni**|Richiede all'utente di immettere la password prima di visitare l'App Store.|Sì|
|**Consenti acquisti in-app**|Consente gli acquisti online dall'interno di un'app in esecuzione.|Sì|
|**Consenti documenti gestiti in altre app non gestite**|Consente di visualizzare documenti aziendali in qualsiasi app.<br>**Esempio:** si vuole impedire agli utenti il salvataggio di file dall'app OneDrive in Dropbox. Disabilitare questa impostazione. Dopo aver ricevuto i criteri (ad esempio dopo un riavvio), il dispositivo non consentirà più il salvataggio.|iOS 7.1 e versioni successive|
|**Consenti documenti non gestiti in altre app gestite**|Consente di visualizzare qualsiasi documento nelle app aziendali gestite.|iOS 7.1 e versioni successive|
|**Consenti videoconferenza**|Consente l'uso di applicazioni di videoconferenza come Facetime sul dispositivo.|Sì|
|**Consenti contenuti per adulti nell'archivio multimediale**|Consente al dispositivo di accedere ai contenuti dell'archivio classificati come per adulti.|Sì|

### Impostazioni applicazione - Giochi

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti l'aggiunta di amici al Game Center**|Consente all'utente di aggiungere amici in Game Center.|sì|
|**Consenti modalità di gioco multiplayer**|Consente all'utente di partecipare a giochi multiplayer sul dispositivo.|sì|

### Impostazioni delle funzionalità del dispositivo - Hardware

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti dispositivo foto/video**|Specifica se è consentito l'uso della fotocamera del dispositivo.|sì|

### Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti roaming vocale**|Consente il roaming vocale quando il dispositivo è su una rete cellulare.|sì|
|**Consenti dati in roaming**|Consentire il roaming dei dati quando il dispositivo si trova su una rete cellulare.|sì|
|**Consenti recupero in background globale durante il roaming**|Consente al dispositivo di recuperare dati come la posta elettronica durante il roaming su una rete cellulare.|Sì|

### Impostazioni delle funzionalità del dispositivo - Funzionalità

|Nome impostazione|Dettagli|iOS|
|----------------|-------|
|**Consenti Siri**|Consente l'uso dell'assistente vocale Siri sul dispositivo.|Sì|
|**Consenti Siri quando il dispositivo è bloccato**|Consente l'uso dell'assistente vocale Siri quando il dispositivo è bloccato.|sì|
|**Consenti composizione vocale**|Consente l'uso della funzionalità di composizione vocale sul dispositivo.|sì|


### Impostazioni per le app conformi e non conformi
Nell'elenco **app conformi &amp; e non conformi** specificare un elenco di app conformi o non conformi usando le informazioni seguenti:

> [!NOTE]
> Un singolo criterio può contenere solo un elenco di app conformi o non conformi. Non è possibile specificare entrambi nello stesso criterio.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Segnala la mancata conformità quando gli utenti installano le app elencate**|Elenca le app che non sono gestite da Intune e che gli utenti non sono autorizzati a installare ed eseguire.|
|**Non segnalare la mancata conformità quando gli utenti installano le app elencate**|Elenca le app che gli utenti sono autorizzati a installare. Per garantire la conformità, non installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite.|
|**Aggiunta**|Aggiunge un'app all'elenco selezionato. Specificare un nome desiderato, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store. Per altre informazioni, vedere **Come specificare gli URL negli App Store** più avanti in questo argomento.|
|**Importa app**|Importa un elenco di app specificate in un file con valori delimitati da virgole. Per il file usare il formato nome applicazione, autore, URL.|
|**Modifica**|Consente di modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Elimina l'app selezionata dall'elenco.|

### Impostazioni della modalità tutto schermo

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo**|Scegliere **Sfoglia**, quindi specificare l'app gestita o un'app di uno Store che potrà essere eseguita quando il dispositivo è in modalità tutto schermo. Non sarà consentito eseguire altri applicazioni sul dispositivo. Per altre informazioni, vedere **Come specificare gli URL negli App Store** più avanti in questo argomento.|
|**Consenti tocco**|Abilita o disabilita il touchscreen nel dispositivo.|
|**Consenti rotazione schermo**|Abilita o disabilita la modifica dell'orientamento dello schermo quando si ruota il dispositivo.|
|**Consenti pulsanti volume**|Abilita o disabilita l'uso dei pulsanti del volume nel dispositivo.|
|**Consenti commutatore suoneria**|Abilita o disabilita la suoneria nel dispositivo.|
|**Consenti pulsante riattivazione sospensione schermo**|Abilita o disabilita il pulsante di riattivazione sospensione dello schermo del dispositivo.|
|**Consenti blocco automatico**|Abilita o disabilita il blocco automatico del dispositivo.|
|**Abilita audio mono**|Abilita o disabilita l'impostazione di accesso facilitato **Audio mono**.|
|**Abilita voice over**|Abilita o disabilita l'impostazione di accesso facilitato **Voice over** per la lettura a voce alta del testo sullo schermo del dispositivo.|
|**Abilita regolazioni voice over**|Abilita o disabilita le regolazioni del voice over che consentono di modificare la funzione Voice Over, ad esempio la velocità con cui viene letto il testo visualizzato sullo schermo.|
|**Abilita zoom**|Abilita o disabilita l'impostazione di accessibilità **Zoom** che consente di usare le funzionalità di tocco per ingrandire la visualizzazione del dispositivo.|
|**Abilita regolazioni zoom**|Abilita o disabilita le regolazioni dello zoom che consentono di modificare la funzione di zoom.|
|**Abilita inversione colori**|Abilita o disabilita l'impostazione di accessibilità **Inverti colori** che consente di regolare la visualizzazione per gli utenti con problemi visivi.|
|**Abilita regolazioni inversione colori**|Abilita o disabilita le regolazioni dell'inversione colori che consentono di modificare la funzione Inverti colori.|
|**Abilita tocco per l'accesso facilitato**|Abilita o disabilita l'impostazione di accessibilità **Tocco per accesso facilitato** che consente agli utenti di eseguire sullo schermo movimenti che potrebbero essere difficili da eseguire.|
|**Abilita regolazioni del tocco per l'accesso facilitato**|Abilita o disabilita le regolazioni del tocco per l'accesso facilitato che consentono di modificare la funzione Tocco per accesso facilitato.|
|**Abilita selezione comandi vocali**|Abilita o disabilita l'impostazione di accessibilità **Leggi selezione** che consente di leggere a voce alta il testo selezionato.|
> [!NOTE]
> Le note seguenti sono valide per le impostazioni della modalità tutto schermo per i dispositivi iOS:
> 
> -   Prima di poter configurare un dispositivo iOS per la modalità schermo intero, è necessario utilizzare il [strumento Configurator Apple](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) o gestione di registrazione dei dispositivi per inserire il dispositivo in modalità supervisionata. Per ulteriori informazioni sullo strumento Apple dello strumento di configurazione, vedere la documentazione di Apple.
> -   Se l'app per iOS viene installata dopo aver distribuito i criteri di configurazione, il dispositivo non passerà alla modalità tutto schermo finché non viene riavviato.

### Informazioni di riferimento per le app conformi e non conformi

#### Monitorare le app conformi e non conformi
Usare **Report app non conformi** per visualizzare la conformità delle app consentite e bloccate.

##### Per eseguire il report app non conformi

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Report** &gt; **Report app non conformi**.

2.  Selezionare i gruppi di dispositivi da controllare, scegliere se verificare la presenza di app conformi, di app non conformi o di entrambi i tipi di app, quindi scegliere **Visualizza report**.

#### Come specificare gli URL negli App Store
Per specificare un URL dell'app nell'elenco delle app conformi e non conformi o nell'opzione **Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo** (solo iOS), usare uno dei formati seguenti:

Usando un motore di ricerca, individuare l'app da usare nell'App Store iTunes e aprire la pagina per l'app.

Copiare l'URL della pagina e usarlo per la configurazione dell'elenco delle app conformo o non conformi o dell'app da eseguire in modalità a tutto schermo.

**Esempio:** cercare **Microsoft Word per iPad**. L'URL usato sarà **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.

> [!NOTE]
> È possibile usare anche il software iTunes per trovare l'app e il comando **Copia collegamento** per ottenere l'URL dell'app.


## Impostazioni di criteri personalizzati

Usare i **criteri di configurazione personalizzati iOS**di Microsoft Intune per distribuire le impostazioni create con lo strumento [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12) nei dispositivi iOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione in un criterio personalizzato iOS di Intune e distribuire le impostazioni a utenti e dispositivi nella propria organizzazione.

Questa funzionalità consente di distribuire le impostazioni di iOS che non possono essere configurate con i criteri di configurazione generali di Intune.

### Prerequisiti
Prima di iniziare, è necessario aver installato lo strumento Apple Configurator e creato un file di configurazione contenente le impostazioni che si desidera distribuire a utenti o dispositivi. È possibile scaricare e acquisire informazioni su Apple Configurator da [Mac App Store](https://itunes.apple.com/us/app/apple-configurator/id434433123?mt=12)

> [!NOTE]
> Intune non segnala la conformità delle singole impostazioni in un criterio personalizzato iOS. Tuttavia, viene segnalata la conformità generale del criterio.

### Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio personalizzato iOS, che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio personalizzato iOS e altre informazioni rilevanti per consentirne l'individuazione.|

### Impostazioni personalizzate

|Nome impostazione|Dettagli|
    |----------------|--------------------|
|**Nome del profilo di configurazione personalizzato (visualizzato agli utenti)**|Specificare il nome con cui il criterio verrà visualizzato nel dispositivo e nei report dei criteri di Intune.|
|**File del profilo di configurazione**|Scegliere **Importa**, quindi selezionare il profilo di configurazione creato usando lo strumento Apple Configurator. **Nota:** Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di iOS sui dispositivi su cui vengono distribuiti i criteri personalizzati iOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** e **Mobile Device Management Protocol Reference** nel sito Web di [Apple Developer](https://developer.apple.com/).|
    |**Dettagli del profilo di configurazione**|Visualizza il codice XML per il profilo di configurazione importato.|

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)




<!--HONumber=Jun16_HO4-->


