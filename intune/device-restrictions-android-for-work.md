---
title: Impostazioni delle restrizioni di Microsoft Intune nei dispositivi Android for Work
titlesuffix: 
description: "Informazioni sulle opzioni di Intune per il controllo di impostazioni e funzionalità nei dispositivi Android for Work."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d4d8089d7ae57c4bf95038e5f9dc88f4949f069e
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="microsoft-intune-android-for-work-device-restriction-settings"></a>Impostazioni delle restrizioni di Microsoft Intune nei dispositivi Android for Work

Questo articolo illustra tutte le impostazioni di restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi che eseguono Android for Work.

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Impostazioni del profilo di lavoro

### <a name="general-settings"></a>Impostazioni generali

-   **Copia e incolla tra il profilo di lavoro e il profilo personale**: controlla le operazioni di copia e incolla tra app aziendali e personali. Scegliere **Blocca** per abilitare il blocco. Scegliere **Non configurato** per disabilitare il blocco.
- **Condivisione dei dati tra i profili di lavoro e personali**: usare questa impostazione per controllare se le app nel profilo di lavoro possono condividere dati con le app nel profilo personale. Questa impostazione controlla le azioni di condivisione all'interno delle applicazioni (ad esempio, l'opzione **Condividi...** nell'app browser Chrome) e non si applica al comportamento Copia/Incolla degli Appunti. Diversamente dalle [impostazioni dei criteri di protezione delle app](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), le impostazioni di restrizione dei dispositivi sono gestite dal portale di Intune e usano la partizione del profilo di lavoro di Android for Work per isolare le applicazioni gestite. È possibile scegliere tra:
    - **Restrizioni predefinite per la condivisione**: questa impostazione è il comportamento di condivisione predefinito del dispositivo che varia a seconda della versione di Android in esecuzione. Per impostazione predefinita, la condivisione dal profilo personale al profilo di lavoro è consentita. Per impostazione predefinita, la condivisione dal profilo di lavoro al profilo personale è bloccata. Questa impostazione impedisce la condivisione di dati dal profilo di lavoro al profilo personale. Google non offre un modo per bloccare la condivisione dal profilo personale al profilo di lavoro nei dispositivi che eseguono la versione 6.0 e versioni successive.   
    - **Le app nel profilo di lavoro possono gestire una richiesta di condivisione dal profilo personale**: usare questa opzione per abilitare la funzionalità Android predefinita che consente la condivisione dal profilo personale al profilo di lavoro. Quando questa opzione è abilitata, una richiesta di condivisione da un'app nel profilo personale supporta la condivisione con app nel profilo di lavoro. Questa impostazione rappresenta il comportamento predefinito per i dispositivi Android che eseguono versioni precedenti alla 6.0.
    - **Consenti la condivisione tra limiti**: abilita la condivisione tra i limiti del profilo di lavoro in entrambe le direzioni. Quando si seleziona questa impostazione, le app nel profilo di lavoro possono condividere dati con app senza badge nel profilo personale. Usare questa impostazione con cautela perché consente la condivisione tra le app gestite nel profilo di lavoro e le app nella parte non gestita del dispositivo.

-   **Notifiche del profilo di lavoro durante il blocco del dispositivo**: controlla se le app del profilo di lavoro possono visualizzare notifiche quando il dispositivo è bloccato.
-   **Autorizzazioni delle app predefinite**: imposta i criteri di autorizzazione predefiniti per tutte le app del profilo di lavoro. A partire da Android 6, all'utente viene richiesto di concedere alcune autorizzazioni richieste dalle app, all'avvio dell'app. Questa impostazione dei criteri consente di decidere se richiedere agli utenti di concedere autorizzazioni per tutte le app nel profilo di lavoro. Ad esempio, si può assegnare al profilo di lavoro un'app che richiede l'accesso alla posizione. In genere, un'app di questo tipo richiede all'utente di concedere o negare l'accesso alla posizione all'app. Questi criteri consentono di decidere se tutte le autorizzazioni devono essere concesse o rifiutate automaticamente senza visualizzare un messaggio di richiesta oppure se lasciare la scelta all'utente finale. È possibile scegliere tra:
    -   **Impostazione predefinita dispositivo**
    -   **Messaggio di richiesta**
    -   **Concedi automaticamente**
    -   **Nega automaticamente**

    Lo stato di concessione per le autorizzazioni può essere definito ulteriormente per app specifiche mediante la definizione di un criterio di configurazione delle app per una singola app (in **App per dispositivi mobili** > **Criteri di configurazione dell'app**).

- **Aggiungi o rimuovi account**

   Impedisce agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro.

   Ad esempio, quando si distribuisce l'app Gmail in un profilo Android for Work, è possibile impedire agli utenti finali di aggiungere o rimuovere account in questo profilo di lavoro.

### <a name="work-profile-password"></a>Password del profilo di lavoro
- **Richiedi la password del profilo di lavoro**: (Android 7.0 e versioni successive con il profilo di lavoro abilitato) definire un criterio per il passcode che si applica solo alle app nel profilo di lavoro. Per impostazione predefinita, l'utente finale ha la possibilità di usare i due PIN definiti separatamente oppure di scegliere di combinarli in quello più complesso.
- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono contenere (da **4**-**16**)
- **Numero massimo di minuti di inattività fino al blocco del profilo di lavoro**: selezionare la quantità di tempo che deve trascorrere prima che il profilo di lavoro si blocchi. L'utente deve quindi immettere le credenziali per riottenere l'accesso.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che il profilo di lavoro venga cancellato dal dispositivo.
- **Scadenza password (giorni)**: immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**) .
- **Tipo di password richiesto**: selezionare il tipo di password che deve essere impostato nel dispositivo. È possibile scegliere tra:
    - **Impostazione predefinita dispositivo**
    - **Protezione biometrica bassa**
    - **Richiesto**
    - **Almeno numerico**
    - **Complessa numerica**: (numeri consecutivi o ripetuti, ad esempio "1111" o "1234", non sono consentiti)
    - **Almeno alfabetico**
    - **Almeno alfanumerico**
    - **Almeno alfanumerico con simboli**
- **Impedisci il riutilizzo delle password precedenti**: immettere il numero di password nuove da usare prima che una password precedente possa essere usata di nuovo (da **1**-**24**).
- **Sblocco con impronta digitale**: impedisce a un utente finale di usare lo scanner di impronta digitale del dispositivo per sbloccarlo.
- **Smart Lock e altri agenti di attendibilità**: consente di controllare la funzionalità Smart Lock su dispositivi compatibili. Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password del profilo di lavoro se il dispositivo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire agli utenti di configurare Smart Lock.

## <a name="device-password"></a>Password del dispositivo

- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono contenere (da **4**-**14**)
- **Numero massimo di minuti di inattività fino al blocco dello schermo**: selezionare la quantità di tempo che deve trascorrere prima che un dispositivo inattivo si blocchi automaticamente.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che i dati vengano cancellati dal dispositivo.
- **Scadenza password (giorni)**: immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**) .
- **Tipo di password richiesto**: selezionare il tipo di password che deve essere impostato nel dispositivo. È possibile scegliere tra:
    - **Impostazione predefinita dispositivo**
    - **Protezione biometrica bassa**
    - **Richiesto**
    - **Almeno numerico**
    - **Complessa numerica**: (numeri consecutivi o ripetuti, ad esempio "1111" o "1234", non sono consentiti)
    - **Almeno alfabetico**
    - **Almeno alfanumerico**
    - **Almeno alfanumerico con simboli**
- **Impedisci il riutilizzo delle password precedenti**: immettere il numero di password nuove da usare prima che una password precedente possa essere usata di nuovo (da **1**-**24**).
- **Sblocco con impronta digitale**: impedisce a un utente finale di usare lo scanner di impronta digitale del dispositivo per sbloccarlo.
- **Smart Lock e altri agenti di attendibilità**: consente di controllare la funzionalità Smart Lock su dispositivi compatibili. Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se quest'ultimo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire agli utenti di configurare Smart Lock.

## <a name="system-security"></a>Protezione del sistema

 - **Analisi delle minacce nelle app**: impone l'attivazione dell'impostazione **Verifica app** per i profili di lavoro e personali.

   > [!Note]  
   > Questa impostazione funziona solo per i dispositivi Android O e versioni successive. 

## <a name="next-steps"></a>Passaggi successivi

Usare le informazioni contenute in [Come configurare le impostazioni delle restrizioni dei dispositivi](device-restrictions-configure.md) per salvare e assegnare il profilo a utenti e dispositivi.
