---
title: Impostazioni dei criteri di sicurezza dei dispositivi mobili | Microsoft Intune
description: "Usare Intune per configurare una vasta gamma di impostazioni che è possibile distribuire in dispositivi gestiti nell'organizzazione."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e5ab3b76-08af-4893-b294-fb6627fdc4c6
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 388426657c5fa96289f5e14a85e8c299e4b50037
ms.openlocfilehash: ac19128499f078b4fe7d16713f18c78b248d38db



---

# Impostazioni dei criteri di sicurezza dei dispositivi mobili in Microsoft Intune
> [!IMPORTANT]
> Microsoft Intune include ora criteri di configurazione distinti per ogni piattaforma del dispositivo. Tali criteri comprendono le impostazioni più aggiornate che è possibile usare. È possibile continuare a usare i criteri di sicurezza del dispositivo mobile. Tutte le distribuzioni esistenti continueranno a funzionare. È tuttavia consigliabile pianificare la migrazione ai nuovi criteri di configurazione non appena possibile, poiché i criteri di sicurezza del dispositivo verranno rimossi in futuro.

I criteri di sicurezza per i dispositivi mobili di Intune consentono di configurare una vasta gamma di impostazioni che è possibile distribuire in computer gestiti dell'organizzazione. Queste impostazioni vengono usate per controllare le funzionalità e la sicurezza dei dispositivi.

È possibile creare e distribuire criteri di sicurezza dei dispositivi mobili per i seguenti tipi di dispositivo:

-   Windows RT 8.1 e dispositivi Windows 8.1 registrati

-   Windows RT

-   Windows Phone 8 e Windows Phone 8.1

-   iOS

-   Android e Samsung KNOX

> [!NOTE]
> Alcune impostazioni non sono valide per alcuni dispositivi. Vedere le tabelle seguenti per un elenco completo delle impostazioni che è possibile configurare.

## Impostazioni di sicurezza

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi una password per sbloccare i dispositivi mobili**|No|No|Sì|Sì|Sì|
|**Tipo di password richiesto**<br /><br />Questa impostazione specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.|sì|Sì|Sì|Sì|No|
|**Tipo di password richiesto - Numero minimo di set di caratteri**<br /><br />Sono disponibili quattro set di caratteri: lettere minuscole, lettere maiuscole, numeri e simboli. L'impostazione specifica quanti set di caratteri diversi è necessario includere nella password. Per i dispositivi iOS specifica invece il numero di simboli che è necessario includere nella password.|sì|Sì|Sì|Sì|No|
|**Lunghezza minima password**|Sì|Sì|Sì|Sì|Sì|
|**Consenti password semplici**<br /><br />Le password semplici includono "0000" e "1234".|No|No|Sì|Sì|No|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Sì|Sì|Sì|Sì|sì|
|**Minuti di inattività prima dello spegnimento dello schermo**<sup>1</sup>|sì|Sì|Sì|Sì|Sì|
|**Scadenza password (giorni)**|Sì|Sì|Sì|Sì|Sì|
|**Ricorda cronologia password**|Sì|Sì|Sì|Sì|Sì|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|sì|Sì|Sì|Sì|Sì|
|**Qualità password**|No|No|No|No|Sì|
|**Consenti password grafica e PIN**|Sì|Sì|No|No|No|
|**Minuti di inattività prima che venga richiesta la password**|No|No|No|Sì|No|
|**Consenti sblocco delle impronte digitali**|No|No|No|iOS 7 e versioni successive|No|
<sup>1</sup> Nei dispositivi iOS, se le impostazioni **Minuti di inattività prima dello spegnimento dello schermo** e **Minuti di inattività prima che venga richiesta la password** sono configurate, vengono applicate in sequenza. Ad esempio, se si imposta il valore di entrambe le impostazioni su **5** minuti, lo schermo si spegne automaticamente dopo 5 minuti e il dispositivo viene bloccato dopo altri 5 minuti. Tuttavia, se l'utente spegne manualmente lo schermo, la seconda impostazione viene applicata immediatamente. Nello stesso esempio, il dispositivo viene bloccato 5 minuti dopo che l'utente spegne lo schermo.

Quando si distribuisce un criterio relativo alla lunghezza della password per dispositivi che eseguono Windows RT, gli utenti saranno costretti a reimpostare la password, anche se la password corrente è conforme ai requisiti dei criteri.

## Impostazioni di crittografia

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi crittografia sul dispositivo mobile**<sup>1</sup><br /><br />Per i dispositivi Windows Phone 8, è necessario impostare su **Sì**.<br /><br />Per abilitare la crittografia su dispositivi iOS, abilitare l'impostazione **richiedono una password per sbloccare i dispositivi mobili**.|Sì|No|Sì|No|Sì|
|**Richiedi crittografia sulle schede di memoria**<br /><br />Questa impostazione si applica ai dispositivi che sono gestiti anche da Exchange ActiveSync.|n/d|n/d|n/d <br />Le app e i dati associati vengono crittografati automaticamente.|n/d|sì|
<sup>1</sup> Altre informazioni per i dispositivi che eseguono Windows 8.1:

-   Per applicare la crittografia su dispositivi che eseguono Windows 8.1, è necessario installare il [dicembre 2014 MDM aggiornamento del client per Windows](http://support.microsoft.com/kb/3013816) su ogni dispositivo.

-   Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un account Microsoft.

-   Per la crittografia funzioni, il dispositivo deve soddisfare Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) requisiti di certificazione hardware.

-   Quando si applica la crittografia in un dispositivo, è possibile visualizzare la chiave di ripristino solo dall'account Microsoft dell'utente, a cui è possibile accedere dall'account OneDrive di quest'ultimo. È possibile ripristinare la chiave per conto dell'utente.

## Impostazioni per il malware

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi firewall di rete**|Sì|No|No|No|No|
|**Attiva SmartScreen**|Sì|No|No|No|No|

## Impostazioni di sistema

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Richiedi aggiornamenti automatici**|Sì|No|No|No|No|
|**Richiedi aggiornamenti automatici: classificazione minima degli aggiornamenti per l'installazione automatico.**<br /><br />Scegliere la classificazione degli aggiornamenti verrà installato automaticamente:<br /><br />- **Importante**. Installa tutti gli aggiornamenti classificati come importanti.<br /><br />- **Consigliato**. Installa tutti gli aggiornamenti classificati come importanti o consigliati.|sì|No|No|No|No|
|**Consenti acquisizione schermo**|No|No|Solo Windows Phone 8.1|Sì|Sì (solo per Samsung KNOX)|
|**Consenti centro di controllo nella schermata di blocco**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti visualizzazione notifiche nella schermata di blocco**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti visualizzazione Oggi nella schermata di blocco**|No|No|No|iOS 7 e versioni successive|No|
|**Controllo dell'account utente**|Sì|No|No|No|No|
|**Consenti invio dati di diagnostica**|Sì|No|Solo Windows Phone 8.1|Sì|Sì (solo per Samsung KNOX)|
|**Consenti certificati TLS (Transport Layer Security) non attendibili**|No|No|No|Sì|No|
|**Consenti software di portafoglio personale quando il dispositivo è bloccato**|No|No|No|Sì|No|
|**Consenti ripristino impostazioni predefinite**|No|No|No|No|Sì (solo per Samsung KNOX)|


## Impostazioni cloud - Documenti e dati

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti backup su iCloud**|No|No|No|Sì|No|
|**Consenti sincronizzazione documenti su iCloud**|No|No|No|Sì|No|
|**Consenti sincronizzazione streaming foto su iCloud**|No|No|No|Sì|No|
|**Richiedi backup crittografato**|No|No|No|Sì|No|
|**URL cartelle di lavoro**<br /><br />Questa impostazione specifica l'URL della cartella di lavoro per consentire la sincronizzazione dei documenti tra i dispositivi.|sì|No|No|No|No|
|**Consenti backup di Google**|No|No|No|No|Sì (solo per Samsung KNOX)|

## Impostazioni cloud - Account e sincronizzazione

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti account Microsoft**|No|No|Solo Windows Phone 8.1|No|No|
|**Consenti sincronizzazione automatica dell'account Google**|No|No|No|No|Sì (solo per Samsung KNOX)|

## Impostazioni di posta elettronica

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti agli utenti di eseguire il download degli allegati di posta elettronica**<sup>1</sup>|n/d|n/d|n/d|n/d|n/d|
|**Periodo di sincronizzazione della posta elettronica.** <br /><br />Questa impostazione si applica ai dispositivi che sono gestiti anche da Exchange ActiveSync.|n/d|n/d|n/d|n/d|n/d|
|**Consente ai dispositivi mobili che non supportano completamente queste impostazioni di eseguire la sincronizzazione con Exchange (Exchange ActiveSync).** <br /><br />Questa impostazione si applica ai dispositivi che sono gestiti anche da Exchange ActiveSync.|n/d|n/d|n/d|n/d|n/d|
|**Rendi l'account Microsoft facoltativo nell'applicazione Windows Mail**|Sì|No|No|No|No|
|**Consenti account di posta elettronica personalizzati**|No|No|Solo Windows Phone 8.1|No|No|

## Impostazioni dell'applicazione - Browser

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti browser Web**|No|No|Solo Windows Phone 8.1|Sì|Sì (solo per Samsung KNOX)|
|**Consenti riempimento automatico**|Sì|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti blocco popup**|Sì|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti cookie**|No|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti plug-in**|Sì|No|No|No|No|
|**Consenti scripting**|Sì|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti avviso illeciti**|Sì|No|No|Sì|No|
|**Consenti immissione di una singola parola nel sito Intranet**<br /><br />Questa impostazione consente l'uso di una singola parola per reindirizzare Internet Explorer e un sito Web, ad esempio "Bing".|sì|No|No|No|No|
|**Consenti rilevamento automatico della rete Intranet**|Sì|No|No|No|No|
|**Livello di protezione per Internet**|Sì|No|No|No|No|
|**Livello di protezione per Intranet**|Sì|No|No|No|No|
|**Livello di protezione per siti attendibili**|Sì|No|No|No|No|
|**Livello di protezione per siti con restrizioni**|Sì|No|No|No|No|
|**Invia l'intestazione DNT (Do Not Track)**|Sì|No|No|No|No|
|**Consenti accesso menu modalità Enterprise**|Sì|No|No|No|No|
|**Posizione elenco siti modalità Enterprise**|Sì|No|No|No|No|

## Impostazioni dell'applicazione - App

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti archivio applicazioni**|No|No|Solo Windows Phone 8.1|Sì|Sì (solo per Samsung KNOX)|
|**Richiedi una password per accedere all'archivio applicazioni**|No|No|No|Sì|No|
|**Consenti acquisti in-app**|No|No|No|Sì|No|
|**Consenti documenti gestiti in altre app non gestite**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti documenti non gestiti in altre app gestite**|No|No|No|iOS 7 e versioni successive|No|
|**Consenti videoconferenza**|No|No|No|Sì|No|
|**Consenti contenuti per adulti nell'archivio multimediale**|No|No|No|Sì|No|
|**Consenti installazione app**|No|No|No|iOS 6 e versioni successive|No|

## Impostazioni dell'applicazione - Giochi

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti amici Game Center**|No|No|No|Sì|No|
|**Consenti modalità di gioco multiplayer**|No|No|No|Sì|No|

## Impostazioni delle funzionalità del dispositivo - Hardware

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti dispositivo foto/video**|No|No|Solo Windows Phone 8.1|Sì|Sì|
|**Consenti archivi rimovibili**|No|No|Sì|No|Sì (solo per Samsung KNOX)|
|**Consenti Wi-Fi**|No|No|Solo Windows Phone 8.1|No|Sì (solo per Samsung KNOX)|
|**Consenti tethering Wi-Fi**|No|No|Solo Windows Phone 8.1|No|Sì (solo per Samsung KNOX)|
|**Consenti connessione automatica agli hotspot Wi-Fi gratuiti**|No|No|Solo Windows Phone 8.1|No|No|
|**Consenti creazione report degli hotspot Wi-Fi**<br /><br />Questa impostazione invia informazioni sulle connessioni Wi-Fi per individuare connessioni nelle vicinanze.|No|No|Solo Windows Phone 8.1|No|No|
|**Consenti georilevazione**<br /><br />Questa impostazione consente al dispositivo di utilizzare le informazioni sul percorso.|No|No|Solo Windows Phone 8.1|No|Sì (solo per Samsung KNOX)|
|**Consenti NFC**<br /><br />Questa impostazione consente operazioni che usano NFC (Near Field Communication).|No|No|Solo Windows Phone 8.1|No|Sì (solo per Samsung KNOX)|
|**Consenti Bluetooth**|No|No|Solo Windows Phone 8.1|No|Sì (solo per Samsung KNOX)|
|**Consenti power off**<br>Se questa impostazione è disabilitata, l'impostazione **Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo** per i dispositivi Samsung KNOX non funziona.|No|No|No|No|Sì (solo per Samsung KNOX)|

## Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti roaming vocale**|No|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti dati in roaming**|Sì|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti sincronizzazione automatica durante il roaming**|No|No|No|Sì|No|
|**Consenti messaggi SMS/MMS**|No|No|No|No|Sì (solo per Samsung KNOX)|

## Impostazioni delle funzionalità del dispositivo - Funzionalità

|Nome impostazione|Windows 8.1 e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|iOS|Android e Samsung KNOX|
|----------------|----------------------------------|--------------|-----------------------------------------|-------|----------------------------|
|**Consenti assistente vocale**|No|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti assistente vocale quando il dispositivo è bloccato**|No|No|No|Sì|No|
|**Consenti composizione vocale**|No|No|No|Sì|Sì (solo per Samsung KNOX)|
|**Consenti copia e incolla**|No|No|Solo Windows Phone 8.1|No|Sì (solo per Samsung KNOX)|
|**Consenti condivisione degli Appunti tra applicazioni**|No|No|No|No|Sì (solo per Samsung KNOX)|
|**Consenti YouTube**|No|No|No|No|Sì (solo per Samsung KNOX)|

### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Aug16_HO3-->


