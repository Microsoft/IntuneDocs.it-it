---
title: Impostazioni dei criteri di Windows | Documentazione Microsoft
description: Usare i criteri di configurazione generale di Windows (Windows 8.1 e versioni successive) di Intune per configurare le impostazioni per i dispositivi Windows 8 e Windows 8.1 registrati.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 53ac1c31cf2a2054080e43716b30c50c73961759


---

# <a name="windows-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di Windows in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Usare i **criteri di configurazione generale di Windows (Windows 8.1 e versione successiva)** di Microsoft Intune per configurare le impostazioni seguenti per i dispositivi Windows 8, Windows 8.1 e Windows RT 8.1 registrati:

## <a name="applicability-settings"></a>Impostazioni di applicabilità

|Nome impostazione|Dettagli|
|----------------|----------------------------------|
|**Applica tutte le configurazioni a Windows 10**|Consente di applicare le impostazioni di questi criteri ai dispositivi Windows 10, oltre ai dispositivi Windows 8 e Windows 8.1.|

## <a name="security-settings"></a>Impostazioni di sicurezza

|Nome impostazione|Dettagli|
|----------------|------|
|**Tipo di password richiesto**|Specifica il tipo di password richiesto, ad esempio alfanumerico o solo numerico.|
|**Tipo di password richiesto - Numero minimo di set di caratteri**|Specifica quanti set di caratteri diversi è necessario includere nella password. Sono disponibili quattro set di caratteri, lettere minuscole, lettere maiuscole, numeri e simboli. Per i dispositivi iOS, questa impostazione specifica invece il numero di simboli che è necessario includere nella password.|
|**Lunghezza minima password**|Configura la lunghezza minima richiesta (in caratteri) della password.|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Cancella il dispositivo dopo il numero di tentativi di accesso non riusciti specificato.|
|**Minuti di inattività prima dello spegnimento dello schermo**|Specifica il numero di minuti per cui un dispositivo deve rimanere inattivo prima che sia necessaria una password per sbloccarlo.|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.|
|**Ricorda cronologia password**|Specifica se l'utente può configurare password usate in precedenza.|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare.|
|**Consenti password grafica e PIN**|Consente l'uso di una password grafica e del PIN. Una password grafica consente all'utente di accedere mediante movimenti su un'immagine. Un PIN consente all'utente di eseguire velocemente l'accesso con un codice di 4 cifre.|

## <a name="encryption-settings"></a>Impostazioni di crittografia

|Nome impostazione|Dettagli|
|----------------|-----|
|**Richiedi crittografia sul dispositivo mobile**<sup>1</sup>|Richiede la crittografia dei file nel dispositivo.|
<sup>1</sup> Altre informazioni per i dispositivi che eseguono Windows 8.1

-   Per applicare la crittografia su dispositivi che eseguono Windows 8.1, è necessario installare il [dicembre 2014 MDM aggiornamento del client per Windows](http://support.microsoft.com/kb/3013816) su ogni dispositivo.

-   Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un account Microsoft.

-   Per la crittografia funzioni, il dispositivo deve soddisfare Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) requisiti di certificazione hardware.

-   Quando si applica la crittografia in un dispositivo, è possibile visualizzare la chiave di ripristino solo dall'account Microsoft dell'utente, a cui è possibile accedere dall'account OneDrive di quest'ultimo. È possibile ripristinare la chiave per conto dell'utente.

## <a name="malware-settings"></a>Impostazioni per il malware

|Nome impostazione|Dettagli|
|----------------|-----|
|**Richiedi firewall di rete**|È necessario che Windows Firewall sia attivato.|
|**Attiva SmartScreen**|Richiede l'uso di Windows SmartScreen nei dispositivi.|

## <a name="system-settings"></a>Impostazioni di sistema

|Nome impostazione|Dettagli|
|----------------|-------|
|**Richiedi aggiornamenti automatici**|Attiva l'impostazione per gli aggiornamenti automatici nei dispositivi.|
|**Richiedi aggiornamenti automatici: classificazione minima degli aggiornamenti per l'installazione automatica**|Consente di scegliere la classificazione degli aggiornamenti che verranno installati automaticamente:<br /><br />-   **Importante**: installa tutti gli aggiornamenti classificati come importanti.<br />-   **Consigliato**: installa tutti gli aggiornamenti classificati come importanti o consigliati.|
|**Controllo dell'account utente**|Richiede l'uso di Controllo dell'account utente nei dispositivi.|
|**Consenti invio dati di diagnostica**|Consente al dispositivo di inviare informazioni di diagnostica a Microsoft.|


## <a name="cloud-settings--documents-and-data"></a>Impostazioni cloud - Documenti e dati

|Nome impostazione|Dettagli|
|----------------|------|
|**URL cartelle di lavoro**|Imposta l'URL della cartella di lavoro per consentire la sincronizzazione dei documenti tra i dispositivi.|

## <a name="email-settings"></a>Impostazioni di posta elettronica

|Nome impostazione|Dettagli|
|----------------|-----|
|**Rendi l'account Microsoft facoltativo nell'applicazione Windows Mail**|Consente di accedere all'applicazione Windows Mail senza disporre di un account Microsoft.|

## <a name="application-settings---browser"></a>Impostazioni dell'applicazione - Browser

|Nome impostazione|Dettagli|
|----------------|-----|
|**Consenti riempimento automatico**|Consente agli utenti di modificare le impostazioni di completamento automatico nel browser.|
|**Consenti blocco popup**|Attiva o disattiva il blocco popup del browser.|
|**Consenti plug-in**|Consente agli utenti di aggiungere plug-in a Internet Explorer.|
|**Consenti scripting**|Consente al browser di eseguire script, ad esempio script di Active X.|
|**Consenti avviso illeciti**|Attiva o disattiva gli avvisi di potenziali siti Web fraudolenti.|
|**Consenti immissione di una singola parola nel sito Intranet**|Consente l'uso di una singola parola per reindirizzare Internet Explorer e un sito Web, ad esempio Bing.|
|**Consenti rilevamento automatico della rete Intranet**|Aiuta a configurare la sicurezza dei siti Intranet in Internet Explorer.|
|**Livello di protezione per Internet**|Consente di impostare il livello di sicurezza di Internet Explorer per i siti Internet.|
|**Livello di protezione per Intranet**|Consente di impostare il livello di sicurezza di Internet Explorer per i siti Intranet.|
|**Livello di protezione per siti attendibili**|Configura il livello di sicurezza per l'area siti attendibili.|
|**Livello di protezione per siti con restrizioni**|Configura il livello di sicurezza per l'area siti con restrizioni.|
|**Invia l'intestazione DNT (Do Not Track)**|Invia un'intestazione DNT (Do Not Track) ai siti visitati in Internet Explorer.|
|**Consenti l'accesso dal menu di modalità Enterprise**|Consente agli utenti di accedere alle opzioni di menu della modalità Enterprise da Internet Explorer.<br>Se si seleziona questa opzione, è possibile anche specificare una **Posizione report di registrazione** contenente un URL a un report che mostra i siti Web per cui gli utenti hanno attivato l'accesso in modalità Enterprise.|
|**Posizione elenco siti modalità Enterprise**|Specifica il percorso dell'elenco di siti Web che useranno la modalità Enterprise quando è attiva.|

## <a name="device-capabilities-settings---cellular"></a>Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Dettagli|
|----------------|----|
|**Consenti roaming dei dati**|Abilita il roaming dati quando il dispositivo si trova in una rete cellulare.|



### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Dec16_HO2-->


