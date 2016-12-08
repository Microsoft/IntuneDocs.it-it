---

title: Impostazioni dei criteri di Android e Samsung KNOX Standard | Microsoft Intune
description: "Creare criteri per il controllo delle impostazioni e delle funzionalità dei dispositivi Android gestiti con Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 08ec9963bf00d81f080c0cf4f26e23a3104763ea


---

# <a name="android-and-samsung-knox-standard-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di Android e Samsung KNOX Standard in Microsoft Intune

Intune offre una gamma di impostazioni generali integrate che è possibile configurare nei dispositivi Android. È anche possibile specificare i valori OMA-URI (Open Mobile Alliance Uniform Resource Identifier) per creare impostazioni personalizzate non disponibili in Intune.

## <a name="general-configuration-policy"></a>Criteri di configurazione generale

Usare i **criteri di configurazione generale Android** di Intune per configurare le impostazioni per quanto indicato di seguito:

-   **Impostazioni di sicurezza del dispositivo mobile**: scegliere da un elenco di impostazioni predefinite che consentono di controllare una gamma di funzionalità e caratteristiche nel dispositivo.

-   **Modalità tutto schermo** (solo per dispositivi Samsung KNOX Standard): bloccare un dispositivo per consentire solo il funzionamento di determinate funzionalità. Ad esempio, è possibile consentire a un dispositivo di eseguire solo un'app gestita specificata o disabilitare i pulsanti del volume in un dispositivo. Queste impostazioni potrebbero essere usate per un modello demo di un dispositivo o per un dispositivo dedicato all'esecuzione di una sola funzione, ad esempio un dispositivo POS.

-   **App conformi e non conformi**: specificare un elenco di app conformi oppure non conformi nella società. Nei dispositivi Android e iOS è possibile usare il **Report app non conformi** per visualizzare la conformità delle app specificate nell'elenco rispetto a quelle installate dagli utenti. Il report non può impedire effettivamente l'installazione dell'applicazione.

> [!TIP]
> È possibile configurare i termini e le condizioni in modo da assicurare agli utenti che tutte le app installate nei loro dispositivi, incluse quelle personali, verranno valutate e che le app non conformi verranno bloccate o segnalate come non conformi. Gli utenti dovranno quindi accettare questi termini e condizioni prima di poter registrare il dispositivo e usare il Portale aziendale per ottenere le app. Per altre informazioni sull'uso di termini e condizioni, vedere [Terms and condition policy settings in Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md) (Impostazioni dei criteri relativi a termini e condizioni in Microsoft Intune).

Se l'impostazione che si sta cercando non viene visualizzata nell'argomento, è possibile crearla con un criterio personalizzato Android che consenta di usare le impostazioni URI OMA per controllare il dispositivo. Per altre informazioni, vedere [Impostazioni dei criteri personalizzati](#custom-policy-settings) più avanti in questo argomento.

### <a name="password-settings"></a>Impostazioni della password

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|-|----------------|----------------|
|**Richiedi una password per sbloccare i dispositivi mobili**|Specifica la richiesta di una password nei dispositivi supportati.|sì|sì|
|**Lunghezza minima password**|Specifica la lunghezza minima della password.|sì|sì|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Specifica il numero di errori di accesso consentiti prima della cancellazione del dispositivo.|sì|sì|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica il numero di minuti di inattività prima dello spegnimento dello schermo del dispositivo.|sì|sì|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare una password.|sì|sì|
|**Ricorda cronologia password**|Specifica il numero di password usate in precedenza che è necessario ricordare.|Sì|Sì|
|**Ricorda cronologia password** - **Impedisci riutilizzo delle password precedenti**|Impedisce il riutilizzo delle password precedenti.|sì|sì|
|**Qualità password**|Specifica il livello richiesto di complessità delle password e indica se è possibile usare dispositivi biometrici.|sì|sì|
|**Consenti sblocco tramite impronta digitale**|Consente di sbloccare il dispositivo con un'impronta digitale.|No|sì|
|**Consenti Smart Lock e altri agenti di attendibilità**<br>(Android 5 e versioni successive)|Consente di controllare la funzionalità Smart Lock nei dispositivi Android compatibili. Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se quest'ultimo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire agli utenti di configurare Smart Lock.|sì|No|

### <a name="encryption-settings"></a>Impostazioni di crittografia

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Richiedi crittografia sui dispositivi mobili**|Richiede la crittografia dei file sul dispositivo mobile.|Sì|sì|
|**Richiedi crittografia sulle schede di memoria**|Specifica se la scheda di memoria del dispositivo deve essere crittografata.|No|Sì|

### <a name="system-settings"></a>Impostazioni di sistema

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Consenti acquisizione schermo**|Consente all'utente di acquisire il contenuto della schermata come immagine.|No|sì|
|**Consenti invio dati di diagnostica**|Consente al dispositivo di inviare informazioni di diagnostica a Google.|No|sì|
|**Consenti ripristino impostazioni predefinite**|Consente all'utente di eseguire il ripristino delle impostazioni di fabbrica del dispositivo.|No|sì|

### <a name="cloud-settings---documents-and-data"></a>Impostazioni cloud - Documenti e dati

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------------------|----------------|
|**Consenti backup di Google**|Consente l'uso del backup di Google.|No|Sì|

### <a name="cloud-settings---accounts-and-synchronization"></a>Impostazioni cloud - Account e sincronizzazione

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Consenti sincronizzazione automatica dell'account Google**|Consente la sincronizzazione automatica delle impostazioni dell'account Google.|No|Sì|

### <a name="application-settings---browser"></a>Impostazioni dell'applicazione - Browser

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Consenti Web browser**|Specifica se è consentito l'uso del Web browser predefinito nel dispositivo.|No|sì|
|**Consenti riempimento automatico**|Consente di usare la funzione di riempimento automatico del Web browser.|No|sì|
|**Consenti blocco popup**|Consente di usare un blocco popup nel Web browser.|No|sì|
|**Consenti cookie**|Consente l'uso dei cookie nel Web browser del dispositivo.|No|sì|
|**Consenti scripting**|Consente l'uso dello scripting nel Web browser del dispositivo.|No|Sì|

### <a name="application-settings---apps"></a>Impostazioni dell'applicazione - App

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Consenti Google Play Store**|Consente all'utente di accedere a Google Play Store sul dispositivo.|No|Sì|

### <a name="device-capabilities-settings---hardware"></a>Impostazioni delle funzionalità del dispositivo - Hardware

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|-----|-----------|----------------|
|**Consenti la fotocamera**|Consente l'uso della fotocamera del dispositivo.|Sì|sì|
|**Consenti archivi rimovibili**|Consente al dispositivo di usare archivi rimovibili, ad esempio una scheda SD.|No|sì|
|**Consenti Wi-Fi**|Consente di usare le funzionalità Wi-Fi del dispositivo.|No|sì|
|**Consenti tethering Wi-Fi**|Consente di usare il tethering Wi-Fi nel dispositivo.|No|sì|
|**Consenti georilevazione**|Consente al dispositivo usare le informazioni sul percorso.|No|sì|
|**Consenti NFC**|Consente l'uso della tecnologia NFC (Near Field Communication) se il dispositivo la supporta.|No|sì|
|**Consenti Bluetooth**|Consente di usare il Bluetooth nel dispositivo.|No|sì|
|**Consenti lo spegnimento**|Consente all'utente di spegnere il dispositivo.<br /><br />Se questa impostazione è disabilitata, l'impostazione **Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo** per i dispositivi Samsung KNOX Standard non funziona.|No|Sì|

### <a name="device-capabilities-settings---cellular"></a>Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|---|-------------|----------------|
|**Consenti roaming vocale**|Consente il roaming vocale quando il dispositivo si trova in una rete cellulare.|No|sì|
|**Consenti roaming dei dati**|Consente il roaming dati quando il dispositivo si trova in una rete cellulare.|No|sì|
|**Consenti i messaggi SMS/MMS**|Consente l'uso di messaggi SMS e MMS sul dispositivo.|No|Sì|

### <a name="device-capabilities-settings---features"></a>Impostazioni delle funzionalità del dispositivo - Funzionalità

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX Standard|
|----------------|----|------------|----------------|
|**Consenti l'assistente vocale**|Consente di usare il software di Assistente vocale sul dispositivo.|No|sì|
|**Consenti la composizione vocale**|Attiva o disattiva la funzionalità di composizione vocale sul dispositivo.|No|sì|
|**Consenti copia e incolla**|Consente le funzioni Copia e Incolla nel dispositivo.|No|sì|
|**Consenti la condivisione degli Appunti tra le applicazioni**|Consente l'uso degli Appunti per copiare e incollare dati tra app.|No|sì|
|**Consenti YouTube**|Consente l'uso di YouTube sul dispositivo.|No|Sì|

### <a name="settings-for-compliant-and-noncompliant-apps"></a>Impostazioni per le app conformi e non conformi
Nell'elenco **App conformi &amp; Non conformi** specificare un elenco di app conformi o non conformi usando le informazioni seguenti:

> [!NOTE]
> Un singolo criterio può contenere solo un elenco di app conformi o non conformi. Non è possibile specificare entrambi nello stesso criterio.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Segnala la mancata conformità quando gli utenti installano le app elencate**|Elenca le app che non sono gestite da Intune e che gli utenti non sono autorizzati a installare ed eseguire. Se gli utenti installano una di queste app, tale app verrà registrata nel Report app non conformi.|
|**Non segnalare la mancata conformità quando gli utenti installano le app elencate**|Elenca le app di cui si vuole consentire l'uso. Per garantire la conformità, gli utenti non devono installare app non elencate. Le app gestite da Intune sono automaticamente consentite.|
|**Aggiungi**|Aggiunge un'app all'elenco selezionato. Specificare il nome, l'autore (facoltativo) e l'URL dell'app nell'App Store.<br /><br />Per altre informazioni, vedere [Specificare gli URL negli App Store](#specify-urls-to-app-stores) più avanti in questo argomento.|
|**Importa app**|Importa un elenco di app specificate in un file con valori separati da virgola. Nel file usare il formato, il nome dell'applicazione, l'autore e l'URL dell'app.|
|**Modifica**|Consente di modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Elimina l'app selezionata dall'elenco.|

### <a name="kiosk-mode-settings"></a>Impostazioni della modalità tutto schermo
Specificare le impostazioni seguenti per i **dispositivi Samsung KNOX Standard**:

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo**|Scegliere **Sfoglia** e quindi selezionare l'app gestita che può essere eseguita quando il dispositivo è in modalità tutto schermo. Le app specificate come collegamento allo store non sono attualmente supportate. Non sarà possibile eseguire altre applicazioni nel dispositivo.|
|**Consenti pulsanti volume**|Abilita o disabilita l'uso dei pulsanti del volume nel dispositivo.|
|**Consenti pulsante riattivazione sospensione schermo**|Abilita o disabilita il pulsante di riattivazione sospensione dello schermo del dispositivo.|

### <a name="reference-information-for-compliant-and-noncompliant-apps"></a>Informazioni di riferimento per le app conformi e non conformi

#### <a name="monitor-compliant-and-noncompliant-apps"></a>Monitorare le app conformi e non conformi
Usare **Report app non conformi** per visualizzare la conformità delle app consentite e bloccate.

###### <a name="to-run-the-noncompliant-apps-report"></a>Per eseguire il report app non conformi

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) scegliere **Report** &gt; **Report app non conformi**.

2.  Selezionare i gruppi di dispositivi da controllare. Indicare quindi se si vuole verificare la presenza di app conformi o non conformi oppure di entrambi i tipi. Al termine, scegliere **Visualizza report**.

#### <a name="specify-urls-to-app-stores"></a>Specificare gli URL negli App Store
Per specificare un URL di app nell'elenco di app conformi e non conformi, seguire questa procedura:

Nella [sezione delle app di Google Play](https://play.google.com/store/apps), cercare l'app da usare.

Aprire la pagina di installazione relativa all'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app conformi e non conformi.

Esempio: Cercare Microsoft Office Mobile in Google Play. L'URL usato sarà **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## <a name="custom-policy-settings"></a>Impostazioni di criteri personalizzati
Usare i **Criteri di configurazione personalizzati Android** di Microsoft Intune per distribuire le impostazioni OMA-URI che è possibile usare per controllare le funzionalità nei dispositivi Android. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni Android non configurabili con i criteri di Intune.

> [!NOTE]
> I criteri personalizzati Android attualmente supportano la configurazione di impostazioni Wi-Fi solo per dispositivi Android che includono una chiave precondivisa.

### <a name="general-settings"></a>Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio personalizzato Android che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio personalizzato Android e altre informazioni rilevanti per consentirne l'individuazione.|

### <a name="oma-uri-settings"></a>Impostazioni OMA-URI

   |Nome impostazione|Dettagli|
    |--------|--------------------|
    |**Nome dell'impostazione**|Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.|
    |**Descrizione dell'impostazione**|Fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.|
    |**Tipo di dati**|Selezionare il tipo di dati in cui verrà specificata questa impostazione OMA URI. Scegliere tra **Stringa, Stringa (XML), Data e ora, Intero, Virgola mobile** o **Booleano**.|
    |**OMA-URI (maiuscole/minuscole)**|Specificare l'impostazione OMA-URI per cui si desidera fornire un'impostazione.|
    |**Valore**|Specificare il valore da associare all'impostazione OMA-URI specificata in precedenza.|

### <a name="examples"></a>Esempi

- [Creare un profilo Wi-Fi con una chiave precondivisa](pre-shared-key-wi-fi-profile.md)
- [Usare criteri personalizzati per creare un profilo VPN per app per dispositivi Android](per-app-vpn-for-android-pulse-secure.md)
- [Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung KNOX](custom-policy-to-allow-and-block-samsung-knox-apps.md)

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO1-->


