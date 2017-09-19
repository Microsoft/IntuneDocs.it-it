---
title: Impostazioni dei criteri di Windows Phone 8.1
description: "Intune offre una gamma di impostazioni generali incorporate che è possibile configurare nei dispositivi Windows Phone 8.1. È anche possibile specificare i valori OMA-URI per creare impostazioni personalizzate non disponibili in Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 83f7469c-272e-43f2-8139-b0d7bc34f43f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95de34806ebd9faed761b0e64df8c4dc596083c8
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/15/2017
---
# <a name="windows-phone-81-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di Windows Phone 8.1 in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune offre una gamma di impostazioni generali incorporate che è possibile configurare nei dispositivi Windows Phone 8.1. È anche possibile specificare i valori OMA-URI (Open Mobile Alliance Uniform Resource Identifier) per creare impostazioni personalizzate non disponibili in Intune.

## <a name="general-configuration-settings"></a>Impostazioni di configurazione generale

Usare i **criteri di configurazione generale per Windows Phone (Windows Phone 8.1 e versioni successive)** di Microsoft Intune per configurare le impostazioni seguenti per i dispositivi Windows Phone 8.1:

-   **Impostazioni di sicurezza del dispositivo mobile** : scegliere da un elenco di impostazioni predefinite che permettono di controllare una gamma di funzionalità e caratteristiche nel dispositivo.

-   **App conformi e non conformi**: specificare un elenco di app conformi oppure non conformi nella società. I dispositivi Windows Phone possono bloccare o consentire l'installazione di queste applicazioni.

### <a name="applicability-settings"></a>Impostazioni di applicabilità

|Nome impostazione|Dettagli|
|----------------|----------------------------------|
|**Applica tutte le configurazioni a Windows 10**|Consente di applicare le impostazioni di questi criteri ai dispositivi Windows 10 Mobile, oltre ai dispositivi Windows Phone 8.1.|

### <a name="password-settings"></a>Impostazioni della password

|Nome impostazione|Dettagli|
|----------------|------|
|**Richiedi una password per sbloccare i dispositivi mobili**|Specifica se gli utenti devono inserire una password per accedere ai loro dispositivi.|
|**Tipo di password richiesto**|Specifica il tipo di password che verrà richiesto, ad esempio alfanumerico o solo numerico.|
|**Tipo di password richiesto - Numero minimo di set di caratteri**|Specifica quanti set di caratteri diversi è necessario includere nella password. Sono disponibili quattro set di caratteri: lettere minuscole, lettere maiuscole, numeri e simboli. Per i dispositivi iOS specifica invece il numero di simboli che è necessario includere nella password.|
|**Lunghezza minima password**|Specifica il numero minimo di caratteri complessi richiesti per la password.|
|**Consenti password semplici**|Specifica la possibilità di usare password semplici, ad esempio '0000' e '1234'.|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Specifica il numero di tentativi di immissione di una password errata ripetuti prima che il dispositivo venga cancellato.|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica per quanto tempo un dispositivo deve rimanere inattivo prima che lo schermo venga bloccato automaticamente.|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.|Sì|sì|
|**Ricorda cronologia password**|Specifica se vengono ricordate le password precedenti per impedire che l'utente le usi di nuovo.|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specifica quante password utilizzate in precedenza vengono ricordate.|

### <a name="encryption-settings"></a>Impostazioni di crittografia

|Nome impostazione|Dettagli|
|----------------|------|
|**Richiedi crittografia sui dispositivi mobili**|Richiede che i dati presenti nei dispositivi mobili supportati siano crittografati.|

### <a name="system-settings"></a>Impostazioni di sistema

|Nome impostazione|Dettagli|
|----------------|-----|
|**Consenti acquisizione schermo**|Consente all'utente di acquisire il contenuto della schermata come file di immagine.|
|**Consenti invio dati di diagnostica**|Consente al dispositivo di inviare informazioni di diagnostica a Microsoft.|

### <a name="cloud-settings--accounts-and-synchronization"></a>Impostazioni cloud - Account e sincronizzazione

|Nome impostazione|Dettagli|
|----------------|------|
|**Consenti account Microsoft**|Consente il collegamento di un account Microsoft al dispositivo.|

### <a name="email-settings"></a>Impostazioni di posta elettronica

|Nome impostazione|Dettagli|
|----------------|-----|
|**Consenti account di posta elettronica personalizzati**|Consente al dispositivo di connettersi ad account di posta elettronica non Microsoft.|

### <a name="application-settings---browser"></a>Impostazioni dell'applicazione - Browser

|Nome impostazione|Dettagli|
|----------------|-----|
|**Consenti Web browser**|Abilita o blocca il Web browser incorporato nei dispositivi.|

### <a name="application-settings---apps"></a>Impostazioni dell'applicazione - App

|Nome impostazione|Dettagli|
|----------------|-----|
|**Consenti archivio applicazioni**|Consente all'utente di connettersi all'App Store dal dispositivo.|

### <a name="device-capabilities-settings---hardware"></a>Impostazioni delle funzionalità del dispositivo - Hardware

|Nome impostazione|Dettagli|
|----------------|-----|
|**Consenti la fotocamera**|Abilita o blocca la fotocamera del dispositivo.|
|**Consenti archivi rimovibili**|Consente al dispositivo di usare unità di archiviazione rimovibili, ad esempio schede SD.|
|**Consenti Wi-Fi**|Abilita o disabilita la funzione Wi-Fi del dispositivo.|
|**Consenti tethering Wi-Fi**|Abilita l'uso del tethering Wi-Fi nel dispositivo.|
|**Consenti connessione automatica agli hotspot Wi-Fi gratuiti**|Consente al dispositivo di connettersi automaticamente agli hotspot Wi-Fi gratuiti e accettare automaticamente le condizioni per l'uso.|
|**Consenti creazione report degli hotspot Wi-Fi**|Invia informazioni sulle connessioni Wi-Fi per individuare connessioni nelle vicinanze.|
|**Consenti georilevazione**|Consente al dispositivo di usare le informazioni sulla posizione geografica.|
|**Consenti NFC**|Consente operazioni che usano NFC (Near Field Communication).|
|**Consenti Bluetooth**|Abilita o disabilita la funzione Bluetooth del dispositivo.|

### <a name="device-capabilities-settings---features"></a>Impostazioni delle funzionalità del dispositivo - Funzionalità

|Nome impostazione|Dettagli|
|----------------|----|
|**Consenti copia e incolla**|Abilita le funzionalità copia e incolla nel dispositivo.|

### <a name="settings-for-allowed-and-blocked-apps"></a>Impostazioni per le app consentite e bloccate
In **Elenco app consentite e bloccate** specificare un elenco di app da consentite o bloccare usando le informazioni seguenti:

> [!NOTE]
> Un singolo criterio può contenere solo un elenco di app consentite o bloccate. Non è possibile specificare entrambi nello stesso criterio.

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Impedisci ai dispositivi di aprire le app nell'elenco**|Elenca le app che non sono gestite da Intune e che gli utenti non sono autorizzati a installare ed eseguire.|
|**Consenti ai dispositivi di installare solo le app nell'elenco**|Elenca le app che gli utenti sono autorizzati a installare. Gli utenti non possono installare nessun altra applicazione. Le app gestite da Intune sono automaticamente consentite.|
|**Aggiungi**|Aggiunge un'app all'elenco selezionato. Specificare un nome, l'URL dell'app nell'App Store e l'autore dell'app (facoltativo). Per informazioni, vedere Come specificare gli URL negli App Store, più avanti in questo argomento.
|**Importa app**|Importa un elenco di app specificate in un file con valori separati da virgola. Nel file usare il formato, il nome dell'applicazione, l'autore e l'URL dell'app.|
|**Modifica**|Consente di modificare il nome, l'autore e l'URL dell'app selezionata.|
|**Eliminazione**|Elimina l'app selezionata dall'elenco.|
> [!IMPORTANT]
> Se si specifica un elenco di app consentite per i dispositivi Windows Phone 8.1, è necessario aggiungere a tale elenco l'app portale aziendale. In caso contrario, l'elenco verrà bloccato.


### <a name="reference-information-for-allowed-and-blocked-apps"></a>Informazioni di riferimento per le app consentite e bloccate

#### <a name="how-to-specify-urls-to-app-stores"></a>Come specificare gli URL negli App Store
Per specificare un URL app nell'elenco di app consentite e bloccate, usare il formato seguente:

Nella pagina [App + giochi per Windows Phone](http://www.windowsphone.com/store/overview) cercare l'applicazione che si vuole usare.

Aprire la pagina dell'app e copiare l'URL negli Appunti. A questo punto l'URL può essere usato in entrambi gli elenchi di app consentite o bloccate.

**Esempio:** Cercare per l'app Skype in Store. L'URL usato sarà **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.

## <a name="custom-policy-settings"></a>Impostazioni di criteri personalizzati
Usare i **Criteri di configurazione personalizzati Windows Phone** di Microsoft Intune per distribuire le impostazioni OMA-URI che è possibile usare per controllare le funzionalità nei **dispositivi Windows Phone 8.1**. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni di Windows Phone che non possono essere configurate con i criteri di configurazione generale di Intune. Per informazioni sulle impostazioni che è possibile configurare con questi criteri, vedere [Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

Per informazioni sulla creazione di impostazioni di OMA URI per i dispositivi Windows Phone, vedere la [documentazione relativa al protocollo Windows Phone 8.1 MDM](http://technet.microsoft.com/library/dn499787.aspx).

### <a name="general-settings"></a>Impostazioni generali

|Nome impostazione|Dettagli|
|----------------|--------------------|
|**Nome**|Immettere un nome univoco per il criterio che consenta di identificarlo nella console di Intune.|
|**Descrizione**|Fornire una descrizione di carattere generale sul criterio di conformità e altre informazioni rilevanti per consentirne l'individuazione.|

### <a name="oma-uri-settings"></a>Impostazioni OMA-URI

Nella sezione **Impostazioni URI OMA** fare clic su **Aggiungi** per aggiungere un'impostazione. È inoltre possibile modificare o eliminare un'impostazione esistente.

Nella finestra di dialogo **Aggiungi o modifica impostazione URI OMA** specificare le informazioni seguenti:

|Nome impostazione|Dettagli|
    |--------|--------------------|
    |**Nome dell'impostazione**|Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.|
    |**Descrizione dell'impostazione**|Fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.|
    |**Tipo di dati**|Selezionare il tipo di dati in cui verrà specificata questa impostazione OMA URI. È possibile scegliere tra:<br /><br />-   **Stringa**<br />-   **Stringa (XML)**<br />-   **Data e ora**<br />-   **Intero**<br />-   **Virgola mobile**<br />-   **Booleano**|
    |**OMA-URI (maiuscole/minuscole)**|Specificare l'opzione OMA-URI per cui si vuole fornire un'impostazione.|
    |**Valore**|Specificare il valore da associare all'impostazione OMA-URI specificata in precedenza.|

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
