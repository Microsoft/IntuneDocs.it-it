---
title: Impostazioni dei criteri di Windows | Microsoft Intune
description: Usare i criteri di configurazione generale di Windows (Windows 8.1 e versioni successive) di Intune per configurare le impostazioni per i dispositivi Windows 8 e Windows 8.1 registrati.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 073e3df63a5de9cf92c739c1ced858e21a9ac351
ms.openlocfilehash: 6b2d805561067d2dc0de70d93c45622a951e5981


---

# Impostazioni dei criteri di Windows in Microsoft Intune
Usare i **criteri di configurazione generale di Windows (Windows 8.1 e versione successiva)** di Microsoft Intune per configurare le impostazioni seguenti per i dispositivi Windows 8 e Windows 8.1 registrati:

## Impostazioni di applicabilità

|Nome impostazione|Dettagli|
|----------------|----------------------------------|
|**Applica tutte le configurazioni a Windows 10**|Consente di applicare le impostazioni di questi criteri ai dispositivi Windows 10, oltre ai dispositivi Windows 8 e Windows 8.1.|

## Impostazioni di sicurezza

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**Tipo di password richiesto**|Specifica il tipo di password richiesto, ad esempio alfanumerico o solo numerico.|sì|Sì|
|**Tipo di password richiesto - Numero minimo di set di caratteri**|Specifica quanti set di caratteri diversi è necessario includere nella password. Sono disponibili quattro set di caratteri, lettere minuscole, lettere maiuscole, numeri e simboli. Per i dispositivi iOS, questa impostazione specifica invece il numero di simboli che è necessario includere nella password.|sì|sì|
|**Lunghezza minima password**<sup>1</sup>|Configura la lunghezza minima richiesta (in caratteri) della password.|sì|Sì|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Cancella il dispositivo dopo il numero di tentativi di accesso non riusciti specificato.|sì|Sì|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica il numero di minuti per cui un dispositivo deve rimanere inattivo prima che sia necessaria una password per sbloccarlo.| sì|Sì|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.|Sì|Sì|
|**Ricorda cronologia password**|Specifica se l'utente può configurare password usate in precedenza.|Sì|Sì|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare.|Sì|Sì|
|**Consenti password grafica e PIN**|Consente l'uso di una password grafica e del PIN. Una password grafica consente all'utente di accedere mediante movimenti su un'immagine. Un PIN consente all'utente di eseguire velocemente l'accesso con un codice di 4 cifre.|sì|sì|
<sup>1</sup> Quando si distribuisce un criterio relativo alla lunghezza della password per dispositivi che eseguono Windows RT, gli utenti saranno costretti a reimpostare la password, anche se la password corrente è conforme ai requisiti dei criteri.

## Impostazioni di crittografia

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Richiedi crittografia sui dispositivi mobili**<sup>1</sup>|Richiede la crittografia dei file nel dispositivo.<br>Per i dispositivi Windows Phone 8, è necessario impostare su **Sì**.|Sì|No|
<sup>1</sup> Informazioni aggiuntive per i dispositivi che eseguono Windows 8.1

-   Per applicare la crittografia su dispositivi che eseguono Windows 8.1, è necessario installare il [dicembre 2014 MDM aggiornamento del client per Windows](http://support.microsoft.com/kb/3013816) su ogni dispositivo.

-   Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un account Microsoft.

-   Per la crittografia funzioni, il dispositivo deve soddisfare Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) requisiti di certificazione hardware.

-   Quando si applica la crittografia in un dispositivo, è possibile visualizzare la chiave di ripristino solo dall'account Microsoft dell'utente, a cui è possibile accedere dall'account OneDrive di quest'ultimo. È possibile ripristinare la chiave per conto dell'utente.

## Impostazioni per il malware

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Richiedi firewall di rete**|È necessario che Windows Firewall sia attivato.|sì|No|
|**Attiva SmartScreen**|Richiede l'uso di Windows SmartScreen nei dispositivi.|sì|No|

## Impostazioni di sistema

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-------|---------------------------|--------------|
|**Richiedi aggiornamenti automatici**|Attiva l'impostazione per gli aggiornamenti automatici nei dispositivi.|sì|No|
|**Richiedi aggiornamenti automatici: classificazione minima degli aggiornamenti per l'installazione automatico.**|Consente di scegliere la classificazione degli aggiornamenti che verranno installati automaticamente:<br /><br />-   **Importante**: installa tutti gli aggiornamenti classificati come importanti.<br />-   **Consigliato**: installa tutti gli aggiornamenti classificati come importanti o consigliati.|sì|No|
|**Controllo dell'account utente**|Richiede l'uso di Controllo dell'account utente nei dispositivi.|sì|No|
|**Consenti invio dati di diagnostica**|Consente al dispositivo di inviare informazioni di diagnostica a Microsoft.|sì|No|


## Impostazioni cloud - Documenti e dati

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|------|----------------------------|--------------|
|**URL cartelle di lavoro**|Imposta l'URL della cartella di lavoro per consentire la sincronizzazione dei documenti tra i dispositivi.|sì|No|

## Impostazioni di posta elettronica

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Rendi l'account Microsoft facoltativo nell'applicazione Windows Mail**|Consente di accedere all'applicazione Windows Mail senza disporre di un account Microsoft.|sì|No|

## Impostazioni dell'applicazione - Browser

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|-----|-----------------------------|--------------|
|**Consenti riempimento automatico**|Consente agli utenti di modificare le impostazioni di completamento automatico nel browser.|sì|No|
|**Consenti blocco popup**|Attiva o disattiva il blocco popup del browser.|Sì|No|
|**Consenti plug-in**|Consente agli utenti di aggiungere plug-in a Internet Explorer.|sì|No|
|**Consenti scripting**|Consente al browser di eseguire script, ad esempio script di Active X.|sì|No|
|**Consenti avviso illeciti**|Attiva o disattiva gli avvisi di potenziali siti Web fraudolenti.|sì|No|
|**Consenti immissione di una singola parola nel sito Intranet**|Consente l'uso di una singola parola per reindirizzare Internet Explorer e un sito Web, ad esempio Bing.|sì|No|
|**Consenti rilevamento automatico della rete Intranet**|Aiuta a configurare la sicurezza dei siti Intranet in Internet Explorer.|sì|No|
|**Livello di protezione per Internet**|Consente di impostare il livello di sicurezza di Internet Explorer per i siti Internet.|sì|No|
|**Livello di protezione per Intranet**|Consente di impostare il livello di sicurezza di Internet Explorer per i siti Intranet.|sì|No|
|**Livello di protezione per siti attendibili**|Configura il livello di sicurezza per l'area siti attendibili.|sì|No|
|**Livello di protezione per siti con restrizioni**|Configura il livello di sicurezza per l'area siti con restrizioni.|sì|No|
|**Invia l'intestazione DNT (Do Not Track)**|Invia un'intestazione DNT (Do Not Track) ai siti visitati in Internet Explorer.|sì|No|
|**Consenti accesso menu modalità Enterprise**|Consente agli utenti di accedere alle opzioni di menu della modalità Enterprise da Internet Explorer.<br>Se si seleziona questa opzione, è possibile anche specificare una **Posizione report di registrazione** contenente un URL a un report che mostra i siti Web per cui gli utenti hanno attivato l'accesso in modalità Enterprise.|sì|No|
|**Posizione elenco siti modalità Enterprise**|Specifica il percorso dell'elenco di siti Web che useranno la modalità Enterprise quando è attiva.|sì|No|

## Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----|------------------------------|--------------|
|**Consenti dati in roaming**|Abilita il roaming dati quando il dispositivo si trova in una rete cellulare.|sì|No|



### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Sep16_HO2-->


