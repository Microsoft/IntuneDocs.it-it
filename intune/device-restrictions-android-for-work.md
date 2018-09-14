---
title: Restrizioni dei dispositivi del profilo di lavoro Android in Microsoft Intune - Azure | Microsoft Docs
description: Nei dispositivi del profilo di lavoro Android è possibile limitare alcune impostazioni del dispositivo, tra cui copia e incolla, visualizzazione delle notifiche, autorizzazioni delle app, condivisione dei dati, lunghezza della password, errori di accesso, uso dell'impronta digitale per sbloccare, riutilizzo delle password e abilitazione della condivisione dei contatti di lavoro con Bluetooth.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 4/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 51e52e26357143d214c4bcf7856dfdb75a68653c
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329770"
---
# <a name="work-device-restriction-settings-in-intune"></a>Impostazioni relative alle restrizioni dei dispositivi Android for Work in Intune

Questo articolo illustra le impostazioni delle restrizioni dei dispositivi di Microsoft Intune configurabili per i dispositivi del profilo di lavoro Android.

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="work-profile-settings"></a>Impostazioni del profilo di lavoro

### <a name="general-settings"></a>Impostazioni generali

- **Copia e incolla tra il profilo di lavoro e il profilo personale**: controlla le operazioni di copia e incolla tra app aziendali e personali. Scegliere **Blocca** per abilitare il blocco. Scegliere **Non configurato** per disabilitare il blocco.
- **Condivisione dei dati tra i profili di lavoro e personali**: controlla se le app nel profilo di lavoro possono condividere dati con le app nel profilo personale. Questa impostazione controlla le azioni di condivisione all'interno delle applicazioni (ad esempio, l'opzione **Condividi...** nell'app browser Chrome) e non si applica al comportamento Copia/Incolla degli Appunti. Diversamente dalle [impostazioni dei criteri di protezione delle app](https://docs.microsoft.com/intune-classic/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), le impostazioni di restrizione dei dispositivi sono gestite dal portale di Intune e usano la partizione del profilo di lavoro Android per isolare le applicazioni gestite. Scegliere tra:
  - **Restrizioni predefinite per la condivisione**: comportamento di condivisione predefinito del dispositivo che varia in base alla versione di Android. Per impostazione predefinita, la condivisione dal profilo personale al profilo di lavoro è consentita. Per impostazione predefinita, la condivisione dal profilo di lavoro al profilo personale è bloccata. Questa impostazione impedisce la condivisione di dati dal profilo di lavoro al profilo personale. Google non offre un modo per bloccare la condivisione dal profilo personale al profilo di lavoro nei dispositivi che eseguono la versione 6.0 e versioni successive.
  - **Le app nel profilo di lavoro possono gestire una richiesta di condivisione dal profilo personale**: questa opzione abilita la funzionalità Android predefinita che consente la condivisione dal profilo personale al profilo di lavoro. Quando questa opzione è abilitata, una richiesta di condivisione da un'app nel profilo personale supporta la condivisione con app nel profilo di lavoro. Questa impostazione rappresenta il comportamento predefinito per i dispositivi Android che eseguono versioni precedenti alla 6.0.
  - **Consenti la condivisione tra limiti**: abilita la condivisione tra i limiti del profilo di lavoro in entrambe le direzioni. Quando si seleziona questa impostazione, le app nel profilo di lavoro possono condividere dati con app senza badge nel profilo personale. Usare questa impostazione con cautela perché consente la condivisione tra le app gestite nel profilo di lavoro e le app nella parte non gestita del dispositivo.

- **Notifiche del profilo di lavoro durante il blocco del dispositivo**: controlla se le app del profilo di lavoro possono visualizzare notifiche quando il dispositivo è bloccato.
- **Autorizzazioni delle app predefinite**: imposta i criteri di autorizzazione predefiniti per tutte le app del profilo di lavoro. A partire da Android 6, all'utente viene richiesto di concedere alcune autorizzazioni richieste dalle app, all'avvio dell'app. Questa impostazione dei criteri consente di decidere se richiedere agli utenti di concedere autorizzazioni per tutte le app nel profilo di lavoro. Ad esempio, si può assegnare al profilo di lavoro un'app che richiede l'accesso alla posizione. In genere, un'app di questo tipo richiede all'utente di concedere o negare l'accesso alla posizione all'app. Questi criteri consentono di decidere se tutte le autorizzazioni devono essere concesse o rifiutate automaticamente senza visualizzare un messaggio di richiesta oppure se lasciare la scelta all'utente finale. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Messaggio di richiesta**
  - **Concedi automaticamente**
  - **Nega automaticamente**

    Lo stato di concessione per le autorizzazioni può essere definito ulteriormente per app specifiche usando un criterio di configurazione delle app per una singola app in **App client** > **Criteri di configurazione dell'app**.

- **Aggiungi o rimuovi account**

   Impedisce agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro.

   Ad esempio, quando si distribuisce l'app Gmail in un profilo di lavoro Android, è possibile impedire agli utenti finali di aggiungere o rimuovere account in questo profilo di lavoro.

- **Condivisione dei contatti tramite Bluetooth**: abilita l'accesso ai contatti di lavoro da un altro dispositivo, ad esempio un'automobile, che viene associato tramite Bluetooth. Per impostazione predefinita, questa impostazione non è configurata e i contatti dei profili di lavoro non sono visualizzati. Selezionare **Abilita** per consentire la condivisione e visualizzare i contatti dei profili di lavoro. Questa impostazione si applica ai dispositivi dei profili di lavoro Android in sistemi operativi Android 6.0 e versioni successive. L'abilitazione di questa impostazione può consentire a determinati dispositivi Bluetooth di memorizzare nella cache i contatti di lavoro al momento della prima connessione. Se si disabilita questo criterio dopo un'associazione/sincronizzazione iniziale, i contatti di lavoro potrebbero non essere rimossi da un dispositivo Bluetooth.

- **Acquisizione schermo**: blocca l'acquisizione di schermate nel dispositivo nel profilo di lavoro. Impedisce anche la visualizzazione del contenuto nei dispositivi di visualizzazione privi di output video protetto.

- **Visualizzare l'ID chiamante del contatto di lavoro nel profilo personale**: se abilitati (non configurati), i dettagli del chiamante del contatto di lavoro vengono visualizzati nel profilo personale. Se bloccato, il numero del chiamante del contatto di lavoro non viene visualizzato nel profilo personale. Si applica ai sistemi operativi Android 6.0 e versioni successive.

- **Fotocamera**: blocca la fotocamera del dispositivo nel profilo di lavoro. Questa impostazione non interessa la fotocamera nel profilo personale.

### <a name="work-profile-password"></a>Password del profilo di lavoro

- **Richiedi la password del profilo di lavoro**: si applica ad Android 7.0 e versioni successive con il profilo di lavoro abilitato. Definire criteri di passcode validi solo per le app nel profilo di lavoro. Per impostazione predefinita, l'utente finale può usare i due PIN definiti separatamente oppure scegliere di combinarli nel PIN più complesso.
- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono contenere (da **4**-**16**)
- **Numero massimo di minuti di inattività fino al blocco del profilo di lavoro**: selezionare la quantità di tempo che deve trascorrere prima che il profilo di lavoro si blocchi. L'utente deve quindi immettere le credenziali per riottenere l'accesso.
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che il profilo di lavoro venga cancellato dal dispositivo.
- **Scadenza password (giorni)**: immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**) .
- **Tipo di password richiesto**: selezionare il tipo di password che deve essere impostato nel dispositivo. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Richiesto**
  - **Almeno numerico**
  - **Complessa numerica**: i numeri consecutivi o ripetuti, ad esempio "1111" o "1234", non sono consentiti
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**
- **Impedisci il riutilizzo delle password precedenti**: immettere il numero di nuove password da usare prima che una password precedente possa essere usata di nuovo (da **1**-**24**).
- **Sblocco con impronta digitale**: impedisce a un utente finale di usare lo scanner di impronta digitale del dispositivo per sbloccarlo
- **Smart Lock e altri agenti di attendibilità**: controlla la funzionalità Smart Lock su dispositivi compatibili. Questa funzionalità del telefono, nota anche come agente di attendibilità, consente di disabilitare o ignorare la password del profilo di lavoro se il dispositivo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. Usare questa impostazione per impedire agli utenti di configurare Smart Lock.

## <a name="device-password"></a>Password del dispositivo

- **Lunghezza minima password**: immettere il numero minimo di caratteri che le password utente devono contenere (da **4**-**14**)
- **Numero massimo di minuti di inattività fino al blocco dello schermo**: selezionare il periodo di tempo che deve trascorrere prima che un dispositivo inattivo si blocchi automaticamente
- **Numero di errori di accesso prima della cancellazione dei dati del dispositivo**: specificare il numero di tentativi di immissione di una password errata prima che i dati vengano cancellati dal dispositivo
- **Scadenza password (giorni)**: immettere il numero di giorni di validità della password prima che sia necessario modificarla (da **1**-**255**)
- **Tipo di password richiesto**: selezionare il tipo di password che deve essere impostato nel dispositivo. Scegliere tra:
  - **Impostazione predefinita dispositivo**
  - **Protezione biometrica bassa**
  - **Richiesto**
  - **Almeno numerico**
  - **Complessa numerica**: i numeri consecutivi o ripetuti, ad esempio "1111" o "1234", non sono consentiti
  - **Almeno alfabetico**
  - **Almeno alfanumerico**
  - **Almeno alfanumerico con simboli**
- **Impedisci il riutilizzo delle password precedenti**: immettere il numero di nuove password da usare prima che una password precedente possa essere usata di nuovo (da **1**-**24**).
- **Sblocco con impronta digitale**: impedisce a un utente finale di usare lo scanner di impronta digitale del dispositivo per sbloccarlo
- **Smart Lock e altri agenti di attendibilità**: controlla la funzionalità Smart Lock su dispositivi compatibili. Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se il dispositivo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. Usare questa impostazione per impedire agli utenti di configurare Smart Lock.

## <a name="system-security"></a>Protezione del sistema

- **Analisi delle minacce nelle app**: impone l'attivazione dell'impostazione **Verifica app** per i profili di lavoro e personali.

   > [!Note]
   > Questa impostazione funziona solo per i dispositivi Android O e versioni successive.

## <a name="next-step"></a>Passaggio successivo

Per salvare e assegnare il profilo a utenti e dispositivi, vedere [Configurare le impostazioni relative alle restrizioni dei dispositivi](device-restrictions-configure.md).
