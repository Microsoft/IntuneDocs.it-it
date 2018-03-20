---
title: Impostazioni relative alle restrizioni dei dispositivi per i dispositivi che eseguono Windows 8.1 in Microsoft Intune
titleSuffix: 
description: "Informazioni relative alle opzioni di Intune per il controllo delle impostazioni e funzionalità nei dispositivi che eseguono Windows 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8cfaad3c35a0035546e5ebb7a55b9978da8025d8
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-windows-81-and-later-device-restriction-settings"></a>Impostazioni relative alle restrizioni dei dispositivi per Windows 8.1 e versioni successive in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo articolo illustra le impostazioni relative alle restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi che eseguono Windows 8.1 e versioni successive.


## <a name="general"></a>Generale

-   **Invio dati di diagnostica** - Consente al dispositivo di inviare informazioni di diagnostica a Microsoft.
-   **Firewall** - È necessario che Windows Firewall sia attivato.
-   **Controllo dell'account utente** -Richiede l'uso di Controllo dell'account utente nei dispositivi.

## <a name="password"></a>Password
-   **Tipo di password richiesto** - Richiede all'utente finale di immettere una password per accedere al dispositivo.
-   **Lunghezza minima password** - Configura la lunghezza minima richiesta, in caratteri, per la password.
-   **Numero di errori di accesso prima della cancellazione dei dati del dispositivo** - Cancella il dispositivo se viene raggiunto questo numero di tentativi di accesso non riusciti.
-   **Numero massimo di minuti di inattività fino al blocco dello schermo** - Specifica il numero di minuti per cui un dispositivo deve rimanere inattivo prima che sia necessaria una password per sbloccarlo.
-   **Scadenza password (giorni)** - Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.
-   **Impedisci riutilizzo delle password precedenti** - Specifica se l'utente può configurare password utilizzate in precedenza.
-   **Password grafica e PIN** - Consente l'uso di una password grafica e del PIN. Una password grafica consente all'utente di accedere mediante movimenti su un'immagine. Un PIN consente all'utente di eseguire velocemente l'accesso con un codice di 4 cifre.
-   **Crittografia** - Richiede la crittografia dei file nel dispositivo.<br>Per applicare la crittografia su dispositivi che eseguono Windows 8.1, è necessario installare il [dicembre 2014 MDM aggiornamento del client per Windows](https://support.microsoft.com/kb/3013816) su ogni dispositivo.
Se si abilita questa impostazione per i dispositivi Windows 8.1, tutti gli utenti del dispositivo devono avere un account Microsoft.
Perché la crittografia funzioni, il dispositivo deve soddisfare i requisiti di certificazione hardware di [Microsoft InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97).
Quando si applica la crittografia in un dispositivo, è possibile visualizzare la chiave di ripristino solo dall'account Microsoft dell'utente, a cui è possibile accedere dall'account OneDrive di quest'ultimo. È possibile ripristinare la chiave per conto dell'utente.     



## <a name="browser"></a>Browser
-   **Riempimento automatico** - Consente agli utenti di modificare le impostazioni di completamento automatico nel browser.
-   **Avvisi illeciti** - Attiva o disattiva gli avvisi di potenziali siti Web fraudolenti.
-   **SmartScreen** - Abilita o disabilita SmartScreen che blocca i siti Web fraudolenti.
-   **JavaScript** - Consente al browser di eseguire gli script, ad esempio script JavaScript.
-   **Popup** - Attiva o disattiva il blocco popup del browser.
-   **Invia intestazioni DNT (Do Not Track)** - Invia un'intestazione DNT (Do Not Track) ai siti visitati in Internet Explorer.
-   **Plug-in** - Consente agli utenti di aggiungere plug-in a Internet Explorer.
-   **Immissione di una singola parola nel sito Intranet** - Consente l'uso di una singola parola per reindirizzare Internet Explorer e un sito Web, ad esempio Bing.
-   **Rilevamento automatico del sito Intranet** - Aiuta a configurare la sicurezza dei siti intranet in Internet Explorer.
-   **Livello di sicurezza Internet** - Consente di impostare il livello di sicurezza di Internet Explorer per i siti Internet.
-   **Livello di sicurezza Intranet** - Consente di impostare il livello di sicurezza di Internet Explorer per i siti Intranet.
-   **Livello di sicurezza dei siti attendibili** - Configura il livello di sicurezza per l'area siti attendibili.
-   **Sicurezza elevata per siti con restrizioni** - Configura il livello di sicurezza per l'area siti con restrizioni.
-   **Accesso al menu di modalità Enterprise** - Consente agli utenti di accedere alle opzioni di menu della modalità Enterprise da Internet Explorer.
Se si seleziona questa opzione, è possibile anche specificare una **Posizione report di registrazione** contenente un URL a un report che mostra i siti Web per cui gli utenti hanno attivato l'accesso in modalità Enterprise.
-   **Posizione dell'elenco di siti con modalità Enterprise** - Specifica la posizione dell'elenco di siti Web che usano la modalità Enterprise quando è attiva.

## <a name="cellular"></a>Cellulare
-   **Roaming dati** - Abilita il roaming dati quando il dispositivo si trova in una rete cellulare.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione
-   **URL cartelle di lavoro** - Imposta l'URL della cartella di lavoro per consentire la sincronizzazione dei documenti tra i dispositivi.
-   **Accedi all'app Windows Mail senza un account Microsoft** - Consente di accedere all'applicazione Windows Mail senza un account Microsoft.    
