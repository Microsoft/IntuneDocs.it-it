---
title: Impostazioni dei criteri di sicurezza dei dispositivi mobili
description: "Usare Intune per configurare una vasta gamma di impostazioni che è possibile distribuire in dispositivi gestiti nell'organizzazione."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 15b56f822557d80d0088467099c5c1232848bf82
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="mobile-device-security-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di sicurezza dei dispositivi mobili in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

> [!IMPORTANT]
> Microsoft Intune include ora criteri di configurazione distinti per ogni piattaforma del dispositivo. Tali criteri comprendono le impostazioni più aggiornate che è possibile usare. È possibile continuare a usare i criteri di sicurezza del dispositivo mobile. Tutte le distribuzioni esistenti continueranno a funzionare. È tuttavia consigliabile pianificare la migrazione ai nuovi criteri di configurazione non appena possibile, poiché i criteri di sicurezza del dispositivo verranno rimossi in futuro.

I criteri di sicurezza per i dispositivi mobili di Intune consentono di configurare una vasta gamma di impostazioni che è possibile distribuire in computer gestiti dell'organizzazione. Queste impostazioni vengono usate per controllare le funzionalità e la sicurezza dei dispositivi.

È possibile creare e distribuire criteri di sicurezza dei dispositivi mobili per i seguenti tipi di dispositivo:

-   Windows RT 8.1 e dispositivi Windows 8.1 registrati

-   Windows RT

-   Windows Phone 8 e Windows Phone 8.1

-   iOS

-   Android e Samsung KNOX Standard

> [!NOTE]
> Alcune impostazioni non sono valide per alcuni dispositivi. Vedere le tabelle seguenti per un elenco completo delle impostazioni che è possibile configurare.
> A partire da ottobre 2016, il supporto di Microsoft Intune per le app del portale aziendale di Windows 8 verrà deprecato. Verrà anche deprecato il supporto di Microsoft Intune per le piattaforme Windows Phone 8 e WinRT. Di conseguenza, non sarà possibile registrare o aggiornare dispositivi Windows Phone 8 o WinRT. È possibile continuare a gestire i dispositivi Windows Phone 8, WinRT e Windows 8 che sono già registrati. Aggiornare i dispositivi Windows Phone 8 e Windows 8 a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi senza interruzioni.

## <a name="security-settings"></a>Impostazioni di sicurezza

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi una password per sbloccare i dispositivi mobili**|No|No|Sì|Sì|sì|
|**Tipo di password richiesto**<br /><br />Questa impostazione specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.|sì|Sì|Sì|Sì|No|
|**Tipo di password richiesto - Numero minimo di set di caratteri**<br /><br />Sono disponibili quattro set di caratteri, lettere minuscole, lettere maiuscole, numeri e simboli. L'impostazione specifica quanti set di caratteri diversi è necessario includere nella password. Per i dispositivi iOS specifica invece il numero di simboli che è necessario includere nella password.|sì|Sì|Sì|Sì|No|
|**Lunghezza minima password**|sì|Sì|Sì|Sì|sì|
|**Consenti password semplici**<br /><br />Le password semplici includono "0000" e "1234".|No|No|Sì|Sì|No|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|sì|Sì|Sì|Sì|sì|
|**Minuti di inattività prima dello spegnimento dello schermo**<sup>1</sup>|sì|Sì|Sì|Sì|sì|
|**Scadenza password (giorni)**|sì|Sì|Sì|Sì|sì|
|**Ricorda cronologia password**|sì|Sì|Sì|Sì|Sì|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|sì|Sì|Sì|Sì|sì|
|**Qualità password**|No|No|No|No|sì|
|**Consenti password grafica e PIN**|sì|Sì|No|No|No|
|**Minuti di inattività prima che venga richiesta la password**|No|No|No|Sì|No|
|**Consenti sblocco tramite impronta digitale**|No|No|No|iOS 7 e versioni successive|No|
<sup>1</sup>Nei dispositivi iOS, se le impostazioni **Minuti di inattività prima dello spegnimento dello schermo** e **Minuti di inattività prima che venga richiesta la password** sono configurate, vengono applicate in sequenza. Ad esempio, se si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo 5 minuti e il dispositivo viene bloccato dopo altri 5 minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio, il dispositivo viene bloccato 5 minuti dopo che l'utente spegne lo schermo.

Quando si distribuisce un criterio relativo alla lunghezza della password per dispositivi che eseguono Windows RT, gli utenti saranno costretti a reimpostare la password, anche se la password corrente è conforme ai requisiti dei criteri.

## <a name="encryption-settings"></a>Impostazioni di crittografia

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi crittografia sul dispositivo mobile**<sup>1</sup><br /><br />Per i dispositivi Windows Phone 8, è necessario impostare su **Sì**.<br /><br />Per abilitare la crittografia su dispositivi iOS, abilitare l'impostazione **richiedono una password per sbloccare i dispositivi mobili**.|Sì|No|Sì|No|sì|
|**Richiedi crittografia sulle schede di memoria**<br /><br />Questa impostazione si applica ai dispositivi che sono gestiti anche da Exchange ActiveSync.|n/d|n/d|n/d <br />Le app e i dati associati vengono crittografati automaticamente.|n/d|sì|
<sup>1</sup>Altre informazioni per i dispositivi che eseguono Windows 8.1:

-   Per applicare la crittografia su dispositivi che eseguono Windows 8.1, è necessario installare il [dicembre 2014 MDM aggiornamento del client per Windows](http://support.microsoft.com/kb/3013816) su ogni dispositivo.

-   Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un account Microsoft.

-   Per la crittografia funzioni, il dispositivo deve soddisfare Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) requisiti di certificazione hardware.

-   Quando si applica la crittografia in un dispositivo, è possibile visualizzare la chiave di ripristino solo dall'account Microsoft dell'utente, a cui è possibile accedere dall'account OneDrive di quest'ultimo. È possibile ripristinare la chiave per conto dell'utente.

## <a name="malware-settings"></a>Impostazioni per il malware

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi firewall di rete**|sì|No|No|No|No|
|**Attiva SmartScreen**|sì|No|No|No|No|

## <a name="system-settings"></a>Impostazioni di sistema

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi aggiornamenti automatici**|sì|No|No|No|No|
|**Richiedi aggiornamenti automatici: classificazione minima degli aggiornamenti per l'installazione automatica**<br /><br />Scegliere la classificazione degli aggiornamenti verrà installato automaticamente:<br /><br />- **Importante**. Installa tutti gli aggiornamenti classificati come importanti.<br /><br />- **Consigliati**. Installa tutti gli aggiornamenti classificati come importanti o consigliati.|sì|No|No|No|No|
|**Consenti acquisizione schermo**|No|No|Solo Windows Phone 8.1|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti centro di controllo nella schermata di blocco**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti visualizzazione notifiche nella schermata di blocco**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti visualizzazione Oggi nella schermata di blocco**|No|No|No|iOS 7 e versioni successive|No|
|**Controllo dell'account utente**|sì|No|No|No|No|
|**Consenti invio dati di diagnostica**|sì|No|Solo Windows Phone 8.1|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti certificati TLS (Transport Layer Security) non attendibili**|No|No|No|Sì|No|
|**Consenti software di portafoglio personale quando il dispositivo è bloccato**|No|No|No|Sì|No|
|**Consenti ripristino impostazioni predefinite**|No|No|No|No|Sì (solo Samsung KNOX Standard)|


## <a name="cloud-settings--documents-and-data"></a>Impostazioni cloud - Documenti e dati

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti backup su iCloud**|No|No|No|Sì|No|
|**Consenti sincronizzazione documenti in iCloud**|No|No|No|Sì|No|
|**Consenti sincronizzazione streaming foto in iCloud**|No|No|No|Sì|No|
|**Richiedi backup crittografato**|No|No|No|Sì|No|
|**URL cartelle di lavoro**<br /><br />Questa impostazione specifica l'URL della cartella di lavoro per consentire la sincronizzazione dei documenti tra i dispositivi.|sì|No|No|No|No|
|**Consenti backup di Google**|No|No|No|No|Sì (solo Samsung KNOX Standard)|

## <a name="cloud-settings--accounts-and-synchronization"></a>Impostazioni cloud - Account e sincronizzazione

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti account Microsoft**|No|No|Solo Windows Phone 8.1|No|No|
|**Consenti sincronizzazione automatica dell'account Google**|No|No|No|No|Sì (solo Samsung KNOX Standard)|

## <a name="email-settings"></a>Impostazioni di posta elettronica

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti agli utenti di eseguire il download degli allegati di posta elettronica**<sup>1</sup>|n/d|n/d|n/d|n/d|n/d|
|**Periodo di sincronizzazione della posta elettronica** <br /><br />Questa impostazione si applica ai dispositivi che sono gestiti anche da Exchange ActiveSync.|n/d|n/d|n/d|n/d|n/d|
|**Consente ai dispositivi mobili che non supportano completamente queste impostazioni di eseguire la sincronizzazione con Exchange (Exchange ActiveSync)** <br /><br />Questa impostazione si applica ai dispositivi che sono gestiti anche da Exchange ActiveSync.|n/d|n/d|n/d|n/d|n/d|
|**Rendi l'account Microsoft facoltativo nell'applicazione Windows Mail**|sì|No|No|No|No|
|**Consenti account di posta elettronica personalizzati**|No|No|Solo Windows Phone 8.1|No|No|

## <a name="application-settings---browser"></a>Impostazioni dell'applicazione - Browser

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti Web browser**|No|No|Solo Windows Phone 8.1|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti riempimento automatico**|sì|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti blocco popup**|sì|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti cookie**|No|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti plug-in**|sì|No|No|No|No|
|**Consenti scripting**|sì|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti avviso illeciti**|sì|No|No|Sì|No|
|**Consenti immissione di una singola parola nel sito Intranet**<br /><br />Questa impostazione consente l'uso di una singola parola per reindirizzare Internet Explorer e un sito Web, ad esempio "Bing".|sì|No|No|No|No|
|**Consenti rilevamento automatico della rete Intranet**|sì|No|No|No|No|
|**Livello di protezione per Internet**|sì|No|No|No|No|
|**Livello di protezione per Intranet**|sì|No|No|No|No|
|**Livello di protezione per siti attendibili**|sì|No|No|No|No|
|**Livello di protezione per siti con restrizioni**|sì|No|No|No|No|
|**Invia l'intestazione DNT (Do Not Track)**|sì|No|No|No|No|
|**Consenti l'accesso dal menu di modalità Enterprise**|sì|No|No|No|No|
|**Posizione elenco siti modalità Enterprise**|sì|No|No|No|No|

## <a name="application-settings---apps"></a>Impostazioni dell'applicazione - App

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti archivio applicazioni**|No|No|Solo Windows Phone 8.1|sì|Sì (solo Samsung KNOX Standard)|
|**Richiedi una password per accedere all'archivio applicazioni**|No|No|No|Sì|No|
|**Consenti acquisti in-app**|No|No|No|Sì|No|
|**Consenti documenti gestiti in altre app non gestite**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti documenti non gestiti in altre app gestite**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti videoconferenza**|No|No|No|Sì|No|
|**Consenti contenuti per adulti nell'archivio multimediale**|No|No|No|Sì|No|
|**Consenti installazione app**|No|No|No|iOS 6 e versioni successive|No|

## <a name="application-settings---gaming"></a>Impostazioni dell'applicazione - Giochi

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti gli amici in Game Center**|No|No|No|Sì|No|
|**Consenti la modalità di gioco multiplayer**|No|No|No|Sì|No|

## <a name="device-capabilities-settings---hardware"></a>Impostazioni delle funzionalità del dispositivo - Hardware

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti la fotocamera**|No|No|Solo Windows Phone 8.1|Sì|sì|
|**Consenti archivi rimovibili**|No|No|Sì|No|Sì (solo Samsung KNOX Standard)|
|**Consenti Wi-Fi**|No|No|Solo Windows Phone 8.1|No|Sì (solo Samsung KNOX Standard)|
|**Consenti tethering Wi-Fi**|No|No|Solo Windows Phone 8.1|No|Sì (solo Samsung KNOX Standard)|
|**Consenti connessione automatica agli hotspot Wi-Fi gratuiti**|No|No|Solo Windows Phone 8.1|No|No|
|**Consenti creazione report degli hotspot Wi-Fi**<br /><br />Questa impostazione invia informazioni sulle connessioni Wi-Fi per individuare connessioni nelle vicinanze.|No|No|Solo Windows Phone 8.1|No|No|
|**Consenti georilevazione**<br /><br />Questa impostazione consente al dispositivo di utilizzare le informazioni sul percorso.|No|No|Solo Windows Phone 8.1|No|Sì (solo Samsung KNOX Standard)|
|**Consenti NFC**<br /><br />Questa impostazione consente operazioni che usano NFC (Near Field Communication).|No|No|Solo Windows Phone 8.1|No|Sì (solo Samsung KNOX Standard)|
|**Consenti Bluetooth**|No|No|Solo Windows Phone 8.1|No|Sì (solo Samsung KNOX Standard)|
|**Consenti lo spegnimento**<br>Se questa impostazione è disabilitata, l'impostazione **Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo** per i dispositivi Samsung KNOX Standard non funziona.|No|No|No|No|Sì (solo Samsung KNOX Standard)|

## <a name="device-capabilities-settings---cellular"></a>Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti roaming vocale**|No|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti roaming dei dati**|sì|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti sincronizzazione automatica durante il roaming**|No|No|No|Sì|No|
|**Consenti i messaggi SMS/MMS**|No|No|No|No|Sì (solo Samsung KNOX Standard)|

## <a name="device-capabilities-settings---features"></a>Impostazioni delle funzionalità del dispositivo - Funzionalità

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX Standard|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti l'assistente vocale**|No|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti assistente vocale quando il dispositivo è bloccato**|No|No|No|Sì|No|
|**Consenti la composizione vocale**|No|No|No|sì|Sì (solo Samsung KNOX Standard)|
|**Consenti copia e incolla**|No|No|Solo Windows Phone 8.1|No|Sì (solo Samsung KNOX Standard)|
|**Consenti la condivisione degli Appunti tra le applicazioni**|No|No|No|No|Sì (solo Samsung KNOX Standard)|
|**Consenti YouTube**|No|No|No|No|Sì (solo Samsung KNOX Standard)|

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
