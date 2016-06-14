---
# required metadata

title: Impostazioni dei criteri di configurazione di Android e Samsung KNOX | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 71cc39cf-e726-40fd-8d08-78776e099a4b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Impostazioni dei criteri di Android e Samsung KNOX in Microsoft Intune

## Criteri di configurazione generale

Usare i **criteri di configurazione generali di Android** di Microsoft Intune per configurare le impostazioni di:

-   **Impostazioni di sicurezza del dispositivo mobile** : scegliere da un elenco di impostazioni predefinite che permettono di controllare una gamma di funzionalità e caratteristiche nel dispositivo.

-   **Modalità tutto schermo** (solo per dispositivi Samsung KNOX): bloccare un dispositivo per consentire solo il funzionamento di determinate funzionalità. Ad esempio, è possibile consentire a un dispositivo di eseguire solo un'app gestita specificata o disabilitare i pulsanti del volume in un dispositivo. Queste impostazioni potrebbero essere usate per un modello demo di un dispositivo o per un dispositivo dedicato all'esecuzione di una sola funzione, ad esempio un dispositivo POS.

-   **App conformi e non conformi**: specificare un elenco di app conformi oppure non conformi nella società. Nei dispositivi Android e iOS è possibile usare il **Report app non conformi** per visualizzare la conformità delle app specificate nell'elenco rispetto a quelle installate dagli utenti (ma senza impedire effettivamente l'installazione dell'app).

> [!TIP]
> È possibile configurare i termini e le condizioni per essere sicuri che gli utenti siano informati del fatto che le app installate nel dispositivo, incluse quelle personali, verranno valutate e che le app non conformi verranno bloccate o segnalate come non conformi. Gli utenti dovranno quindi accettare questi termini e condizioni prima di poter registrare il dispositivo e usare il Portale aziendale per ottenere le app. Per altre informazioni sull'uso di termini e condizioni, vedere [Terms and condition policy settings in Microsoft Intune](terms-and-condition-policy-settings-in-microsoft-intune.md) (Impostazioni dei criteri relativi a termini e condizioni in Microsoft Intune).

Se l'impostazione che si sta cercando non viene visualizzata nell'argomento, è possibile crearla con un criterio personalizzato Android che consenta di usare le impostazioni URI OMA per controllare il dispositivo. Per altre informazioni, vedere **Impostazioni di criteri personalizzati** più avanti in questo argomento.

### Impostazioni della password

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|-|----------------|----------------|
|**Richiedi una password per sbloccare i dispositivi mobili**|Richiede una password nei dispositivi supportati.|Sì|Sì|
|**Lunghezza minima password**|La lunghezza minima della password.|Sì|Sì|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Cancella il dispositivo se questo numero di tentativi di accesso ha esito negativo.|Sì|Sì|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica il numero di minuti prima dello spegnimento dello schermo del dispositivo.|Sì|Sì|
|**Scadenza password (giorni)**|Il numero di giorni prima che sia necessario modificare una password.|Sì|Sì|
|**Ricorda cronologia password**|Ricorda le password usate in precedenza.|Sì|Sì|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Impedisce il riutilizzo delle password usate in precedenza.|Sì|Sì|
|**Qualità password**|Selezionare il livello di complessità delle password necessario e indicare se possono essere usati anche dispositivi biometrici.|Sì|Sì|
|**Consenti sblocco delle impronte digitali**|Consente di sbloccare il dispositivo con un'impronta digitale.|No|Sì|

### Impostazioni di crittografia

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Richiedi crittografia sui dispositivi mobili**|Richiede la crittografia dei file sul dispositivo mobile.|Sì|Sì|
|**Richiedi crittografia sulle schede di memoria**|Specifica se la scheda di memoria del dispositivo deve essere crittografata.|No|Sì|

### Impostazioni di sistema

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Consenti acquisizione schermo**|Consente all'utente di acquisire il contenuto della schermata come immagine.|No|Sì|
|**Consenti invio dati di diagnostica**|Consente al dispositivo di inviare informazioni di diagnostica a Google.|No|Sì|
|**Consenti ripristino impostazioni predefinite**|Consente all'utente di eseguire il ripristino delle impostazioni di fabbrica del dispositivo.|No|Sì|

### Impostazioni cloud - Documenti e dati

|Nome impostazione|Dettagli|Android e Samsung KNOX|Android 4.0+|
|----------------|----------------------------|----------------|
|**Consenti backup di Google**|Consente l'uso del backup di Google.|No|Sì|

### Impostazioni cloud - Account e sincronizzazione

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Consenti sincronizzazione automatica dell'account Google**|Consente la sincronizzazione automatica delle impostazioni dell'account Google.|No|Sì|

### Impostazioni dell'applicazione - Browser

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Consenti browser Web**|Specifica se è consentito l'uso del Web browser nel dispositivo.|No|Sì|
|**Consenti riempimento automatico**|Consente di usare la funzione di riempimento automatico del Web browser.|No|Sì|
|**Consenti blocco popup**|Consente di usare un blocco popup nel Web browser.|No|Sì|
|**Consenti cookie**|Consente l'uso dei cookie nel Web browser del dispositivo.|No|Sì|
|**Consenti scripting**|Consente l'uso dello scripting nel Web browser del dispositivo.|No|Sì|

### Impostazioni dell'applicazione - App

|Nome impostazione|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Consenti archivio Google Play**|Consente all'utente di accedere a Google Play Store sul dispositivo.|No|Sì|

### Impostazioni delle funzionalità del dispositivo - Hardware

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Consenti dispositivo foto/video**|Consente l'uso della fotocamera del dispositivo.|Sì|Sì|
|**Consenti archivi rimovibili**|Consente al dispositivo di usare archivi rimovibili, ad esempio una scheda SD.|No|Sì|
|**Consenti Wi-Fi**|Consente di usare le funzionalità Wi-Fi del dispositivo.|No|Sì|
|**Consenti tethering Wi-Fi**|Consente di usare il tethering Wi-Fi nel dispositivo.|No|Sì|
|**Consenti georilevazione**|Consente al dispositivo usare le informazioni sul percorso.|No|Sì|
|**Consenti NFC**|Consente l'uso della tecnologia NFC (Near Field Communication) se il dispositivo la supporta.|No|Sì|
|**Consenti Bluetooth**|Consente di usare il Bluetooth nel dispositivo.|No|Sì|
|**Consenti power off**|Consente all'utente di spegnere il dispositivo.<br /><br />Se questa impostazione è disabilitata, l'impostazione **Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo** per i dispositivi Samsung KNOX non funziona.|No|Sì|

### Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Consenti roaming vocale**|Consente il roaming vocale quando il dispositivo è su una rete cellulare.|No|Sì|
|**Consenti dati in roaming**|Consentire il roaming dei dati quando il dispositivo si trova su una rete cellulare.|No|Sì|
|**Consenti messaggi SMS/MMS**|Consente di usare messaggi SMS e MMS sul dispositivo.|No|Sì|

### Impostazioni delle funzionalità del dispositivo - Funzionalità

|Nome impostazione|Dettagli|Android 4.0+|Samsung KNOX|
|----------------|----------------|----------------|
|**Consenti assistente vocale**|Consente di usare il software di Assistente vocale sul dispositivo.|No|Sì|
|**Consenti composizione vocale**|Attiva o disattiva la funzionalità di composizione vocale sul dispositivo.|No|Sì|
|**Consenti copia e incolla**|Consente le funzionalità copia e incolla nel dispositivo.|No|Sì|
|**Consenti condivisione degli Appunti tra applicazioni**|Usare gli Appunti per copiare e incollare tra app.|No|Sì|
|**Consenti YouTube**|Consente di usare YouTube nel dispositivo.|No|Sì|

### Impostazioni per le app conformi e non conformi
Nell'elenco **app conformi &amp; e non conformi** specificare un elenco di app conformi o non conformi usando le informazioni seguenti:

> [!NOTE]
> Un singolo criterio può contenere solo un elenco di app conformi o non conformi. Non è possibile specificare entrambi nello stesso criterio.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Segnala la mancata conformità quando gli utenti installano le app elencate**|Elenca le app che non sono gestite da Intune e che gli utenti non sono autorizzati a installare ed eseguire.|
|**Non segnalare la mancata conformità quando gli utenti installano le app elencate**|Elenca le app che gli utenti sono autorizzati a installare. Per garantire la conformità, non installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite.|
|**Aggiunta**|Aggiunge un'app all'elenco selezionato. Specificare un nome desiderato, facoltativamente l'autore dell'app e l'URL dell'app nell'App Store.<br /><br />Per informazioni, vedere Come specificare gli URL negli App Store, più avanti in questo argomento.|
|**Importa app**|Importa un elenco di app specificate in un file con valori delimitati da virgole. Per il file usare il formato nome applicazione, autore, URL.|
|**Modifica**|Consente di modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Elimina l'app selezionata dall'elenco.|

### Impostazioni della modalità tutto schermo
Specificare le impostazioni seguenti per i **dispositivi Samsung KNOX**:

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Selezionare un'app gestita che potrà essere eseguita quando il dispositivo è in modalità tutto schermo**|Fare clic su **Sfoglia**, quindi selezionare l'app gestita di cui consentire l'esecuzione quando il dispositivo è in modalità tutto schermo. Le app specificate come collegamento allo store non sono attualmente supportate. Non sarà possibile eseguire altre applicazioni nel dispositivo.|
|**Consenti pulsanti volume**|Abilita o disabilita l'uso dei pulsanti del volume nel dispositivo.|
|**Consenti pulsante riattivazione sospensione schermo**|Abilita o disabilita il pulsante di riattivazione sospensione dello schermo del dispositivo.|

### Informazioni di riferimento per le app conformi e non conformi

#### Monitorare le app conformi e non conformi
Usare **Report app non conformi** per visualizzare la conformità delle app consentite e bloccate.

###### Per eseguire il report app non conformi

1.  Nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) fare clic su **Report** &gt; **Report app non conformi**.

2.  Selezionare i gruppi di dispositivi da controllare, scegliere se verificare la presenza di app conformi, di app non conformi o di entrambi, quindi fare clic su **Visualizza report**.

#### Come specificare gli URL negli App Store
Per specificare un URL app nell'elenco di applicazioni conformi e non conformi, utilizzare il formato seguente:

Nella [sezione delle app di Google Play](https://play.google.com/store/apps), cercare l'app da usare.

Aprire la pagina di installazione per l'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app conformi e non conformi.

**Esempio**: cercare Microsoft Office Mobile in Google Play. L'URL usato sarà **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.

## Impostazioni di criteri personalizzati
Usare i **Criteri di configurazione personalizzati Android** di Microsoft Intune per distribuire le impostazioni OMA-URI (Open Mobile Alliance Uniform Resource Identifier) che è possibile usare per controllare le funzionalità nei dispositivi Android. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni Android non configurabili con i criteri di Intune. Per informazioni sulle impostazioni che è possibile configurare con questi criteri, vedere [Manage settings and features on your devices with Microsoft Intune policies](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md) (Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune).

> [!NOTE]
> I criteri personalizzati Android attualmente supportano la configurazione di impostazioni Wi-Fi solo per dispositivi Android che includono una chiave precondivisa. Per altre informazioni vedere Configurare un profilo Wi-Fi personalizzato con una chiave precondivisa, più avanti in questo argomento.

### Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio personalizzato Android che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio personalizzato Android e altre informazioni rilevanti per consentirne l'individuazione.|

### Impostazioni OMA-URI

   |Nome impostazione|Dettagli|
    |--------|--------------------|
    |**Nome impostazione**|Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.|
    |**Descrizione dell'impostazione**|Fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.|
    |**Tipo di dati**|Selezionare il tipo di data in cui si specificherà questa impostazione OMA URI. Scegliere tra **Stringa, Stringa (XML), Data e ora, Intero, Virgola mobile** o **Booleano**.|
    |**OMA-URI (con distinzione tra maiuscole e minuscole)**|Specificare l'impostazione OMA-URI per cui si desidera fornire un'impostazione.|
    |**Valore**|Specificare il valore da associare all'impostazione OMA-URI specificata in precedenza.|

### Esempio: Configurare un profilo Wi-Fi personalizzato con una chiave precondivisa
Sebbene Intune supporti profili Wi-Fi per i dispositivi Android, questa funzionalità non supporta attualmente l'inclusione di una chiave precondivisa nella configurazione. In questo esempio, verrà illustrato come creare un criterio personalizzato Android che crea un profilo Wi-Fi con una chiave precondivisa sul dispositivo Android.

#### Per creare un profilo Wi-Fi con una chiave precondivisa

1.  Assicurarsi che gli utenti usino la versione più recente dell'app [Portale aziendale di Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) per Android.

2.  Creare un criterio personalizzato Android e aggiungere le impostazioni seguenti:

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Nome impostazione**|Specificare un nome di preferenza per l'impostazione.|
|**Descrizione dell'impostazione**|Specificare una descrizione per l’impostazione.|
|**Tipo di dati**|Selezionare **Stringa (XML)**.|
|**URI OMA**|Immettere: ./Vendor/MSFT/WiFi/Profile/*&lt;your Wi-Fi profile&gt;*/Settings|

3.  In **Valore** copiare e incollare il codice XML seguente:

    ```
    <!--
    WEP Wifi Profile
                    <Name of wifi profile> = Name of profile 
                    <SSID of wifi profile> = Plain text of SSID. Does not need to be escaped, could be <name>Your Company's Network</name>
                    <WEP password> = Password to connect to the network
    -->
    <WLANProfile 
    xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name><Name of wifi profile></name>
      <SSIDConfig>
        <SSID>
          <name><SSID of wifi profile></name>
        </SSID>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <MSM>
        <security>
          <authEncryption>
            <authentication>open</authentication>
            <encryption>WEP</encryption>
            <useOneX>false</useOneX>
          </authEncryption>
          <sharedKey>
            <keyType>networkKey</keyType>
            <protected>false</protected>
            <keyMaterial><WEP password></keyMaterial>
          </sharedKey>
          <keyIndex>0</keyIndex>
        </security>
      </MSM>
    </WLANProfile>
    ```

4.  Al termine, salvare il criterio e distribuirlo ai dispositivi Android necessari. Nell'elenco di connessioni del dispositivo verrà visualizzato il nuovo profilo Wi-Fi.

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO3-->


