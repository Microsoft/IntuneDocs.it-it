---
# required metadata

title: Impostazioni dei criteri di Windows | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 6982a2bc-aafa-475a-9236-4840b709e5a1

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Impostazioni dei criteri di Windows in Microsoft Intune
Usare i **criteri di configurazione generale di Windows (Windows 8.1 e versioni successive)** di Microsoft Intune per configurare le impostazioni per i dispositivi Windows 8 e Windows 8.1 registrati:

## Impostazioni di applicabilità

|Nome impostazione|Dettagli|
|----------------|----------------------------------|
|**Applica tutte le configurazioni a Windows 10**|Consente di applicare le impostazioni di questi criteri ai dispositivi Windows 10, oltre ai dispositivi Windows 8 e Windows 8.1.|

## Impostazioni di sicurezza

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Tipo di password richiesto**|Specifica il tipo di password che verrà richiesto, ad esempio solo numerico o alfanumerico.|Sì|Sì|
|**Tipo di password richiesto - Numero minimo di set di caratteri**|Sono disponibili quattro set di caratteri, lettere minuscole, lettere maiuscole, numeri e simboli. L'impostazione specifica quanti set di caratteri diversi è necessario includere nella password. Per i dispositivi iOS specifica invece il numero di simboli che è necessario includere nella password.|sì|sì|
|**Lunghezza minima password**<sup>1</sup>|Configura la lunghezza minima richiesta (in caratteri) per la password nei dispositivi.|Sì|Sì|
|**Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo**|Cancella il dispositivo se l'accesso non riesce per il numero di volte indicato.|Sì|Sì|
|**Minuti di inattività prima dello spegnimento dello schermo**|Scegliere il numero di minuti per cui un dispositivo deve rimanere inattivo prima che sia necessaria una password per sbloccarlo.| Sì|Sì|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.|Sì|Sì|
|**Ricorda cronologia password**|Specifica se l'utente può configurare password usate in precedenza.|Sì|Sì|
|**Ricorda cronologia password** – **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che il dispositivo deve ricordare.|Sì|Sì|
|**Consenti password grafica e PIN**|Consente l'uso di una password grafica e PIN nel dispositivo. Una password grafica consente all'utente di eseguire l'accesso mediante movimenti su un'immagine. Un PIN consente all'utente di eseguire l'accesso velocemente con un codice di 4 cifre.|Sì|Sì|
<sup>1</sup> Quando si imposta la distribuzione di un criterio relativo alla lunghezza della password per dispositivi che eseguono Windows RT, gli utenti saranno costretti a reimpostare la password, anche se la password corrente è conforme ai requisiti dei criteri.

## Impostazioni di crittografia

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Richiedi crittografia sui dispositivi mobili**<sup>1</sup>|Richiede la crittografia dei file nel dispositivo.<br>Per i dispositivi Windows Phone 8, è necessario impostare su **Sì**.|Sì|No|
<sup>1</sup> Informazioni aggiuntive per i dispositivi che eseguono Windows 8.1

-   Per applicare la crittografia su dispositivi che eseguono Windows 8.1, è necessario installare il [dicembre 2014 MDM aggiornamento del client per Windows](http://support.microsoft.com/kb/3013816) su ogni dispositivo.

-   Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un Account Microsoft.

-   Per la crittografia funzioni, il dispositivo deve soddisfare Microsoft [InstantGo](http://blogs.windows.com/bloggingwindows/2014/06/19/instantgo-a-better-way-to-sleep/) requisiti di certificazione hardware.

-   Quando si applica la crittografia in un dispositivo, la chiave di ripristino è accessibile solo da utenti Account Microsoft, accessibili dal proprio account OneDrive. È possibile ripristinare la chiave per conto dell'utente.

## Impostazioni per il malware

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Richiedi firewall di rete**|Richiedere che Windows Firewall sia attivato.|Sì|No|
|**Attiva SmartScreen**|Richiedere l'uso di Windows SmartScreen nei dispositivi.|Sì|No|

## Impostazioni di sistema

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Richiedi aggiornamenti automatici**|Attivare l'impostazione per gli aggiornamenti automatici nei dispositivi.|Sì|No|
|**Richiedi aggiornamenti automatici: classificazione minima degli aggiornamenti per l'installazione automatico.**|Scegliere la classificazione degli aggiornamenti verrà installato automaticamente:<br /><br />-   **Importante**: installa tutti gli aggiornamenti classificati come importanti.<br />-   **Consigliato**: installa tutti gli aggiornamenti classificati come importanti o consigliati.|Sì|No|
|**Controllo dell'account utente**|Richiedere l'uso di Controllo dell'account utente nei dispositivi.|Sì|No|
|**Consenti invio dati di diagnostica**|Consentire al dispositivo di inviare informazioni di diagnostica a Microsoft.|Sì|No|


## Impostazioni cloud - Documenti e dati

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**URL cartelle di lavoro**|Imposta l'URL della cartella di lavoro per consentire la sincronizzazione dei documenti tra i dispositivi|Sì|No|

## Impostazioni di posta elettronica

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Rendi l'account Microsoft facoltativo nell'applicazione Windows Mail**|Consente di accedere all'applicazione Windows Mail senza disporre di un account Microsoft.|Sì|No|

## Impostazioni dell'applicazione - Browser

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Consenti riempimento automatico**|L’utente può modificare le impostazioni di completamento automatico nel browser.|Sì|No|
|**Consenti blocco popup**|Attiva o disattiva il blocco popup del browser.|Sì|No|
|**Consenti plug-in**|L’utente può aggiungere plug-in a Internet Explorer.|sì|No|
|**Consenti scripting**|Il browser può eseguire script, ad esempio gli script ActiveX.|Sì|No|
|**Consenti avviso illeciti**|Attiva o disattiva gli avvisi di potenziali siti Web fraudolenti.|Sì|No|
|**Consenti immissione di una singola parola nel sito Intranet**|Consente l'uso di una singola parola per reindirizzare Internet Explorer e un sito Web, ad esempio Bing.|Sì|No|
|**Consenti rilevamento automatico della rete Intranet**|Aiuta a configurare la sicurezza dei siti Intranet in Internet Explorer.|sì|No|
|**Livello di protezione per Internet**|Impostare il livello di protezione di Internet Explorer per i siti Internet.|Sì|No|
|**Livello di protezione per Intranet**|Impostare il livello di protezione di Internet Explorer per i siti Intranet.|sì|No|
|**Livello di protezione per siti attendibili**|Configurare il livello di protezione per l'area siti attendibili.|Sì|No|
|**Livello di protezione per siti con restrizioni**|Configurare il livello di protezione per l'area siti con restrizioni.|sì|No|
|**Invia l'intestazione DNT (Do Not Track)**|In Internet Explorer inviare un'intestazione DNT (Do Not Track) ai siti visitati.|Sì|No|
|**Consenti accesso menu modalità Enterprise**|Consente agli utenti di accedere alle opzioni di menu della modalità Enterprise da Internet Explorer.<br>Se l'opzione è selezionata, è possibile anche specificare una **Posizione report di registrazione** contenente un URL a un report che mostra i siti Web per cui gli utenti hanno attivato l'accesso in modalità Enterprise.|sì|No|
|**Posizione elenco siti modalità Enterprise**|Specificare il percorso dell'elenco di siti Web che useranno la modalità Enterprise quando è attiva.|Sì|No|

## Impostazioni delle funzionalità del dispositivo - Cellulare

|Nome impostazione|Dettagli|Windows 8.1 e Windows RT 8.1|Windows RT|
|----------------|----------------------------------|--------------|
|**Consenti dati in roaming**|Consentire il roaming dei dati quando il dispositivo si trova su una rete cellulare.|Sì|No|



### Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->


