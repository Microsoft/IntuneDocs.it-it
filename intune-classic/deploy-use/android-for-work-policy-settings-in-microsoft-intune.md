---
title: Impostazioni dei criteri di Android for Work
description: "Creare criteri per il controllo delle impostazioni e delle funzionalità dei dispositivi Android for Work gestiti con Intune."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 35a53076-74d6-486d-b201-e0da2e170008
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 8e2a02676a129f3861c84c606610a20929275be5
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="android-for-work-policy-settings-in-microsoft-intune"></a>Impostazioni dei criteri di Android for Work in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune offre una gamma di impostazioni generali predefinite che è possibile configurare nei [dispositivi Android for Work](android-for-work.md).

## <a name="general-configuration-policy"></a>Criteri di configurazione generale

Usare i **criteri di configurazione generale di Android for Work** di Intune per configurare le impostazioni dei profili di sicurezza e di lavoro per i dispositivi Android for Work.

Se l'impostazione che si sta cercando non viene visualizzata nell'argomento, è possibile crearla con un criterio personalizzato Android che consenta di usare le impostazioni URI OMA per controllare il dispositivo. Per altre informazioni, vedere [Impostazioni dei criteri personalizzati](#custom-policy-settings) più avanti in questo argomento.

> [!TIP]
> I dispositivi vengono crittografati automaticamente quando si esegue il provisioning di un profilo di lavoro. Questa impostazione non può essere modificata.

### <a name="password-settings"></a>Impostazioni della password

|Nome impostazione|Dettagli|
|----------------|-|
|**Richiedi una password per sbloccare i dispositivi mobili**|Specifica se è necessaria una password nei dispositivi gestiti. È possibile scegliere tra:<br><br>- **Complessa**: deve includere almeno una lettera, un numero e un simbolo<br>- **Alfanumerica**: deve includere almeno un numero e un carattere alfabetico<br>- **Alfabetica**: deve includere almeno lettere o simboli<br>- **Complessa numerica**: deve includere caratteri numerici non ripetuti o consecutivi<br>- **Numerica**<br><br>Se questa impostazione non è abilitata, non sono previsti requisiti di complessità.|
|**Lunghezza minima password**|Specifica il numero minimo di caratteri o numeri della password.|
|**Minuti di inattività prima che lo schermo del dispositivo venga bloccato**|Specifica il numero di minuti di inattività dell'utente prima del blocco automatico del dispositivo.|
|**Consenti Smart Lock e altri agenti di attendibilità**<br>(Android 6.0+)|Consente di controllare la funzionalità Smart Lock nei dispositivi Android compatibili. Questa funzionalità del telefono, talvolta nota anche come agente di attendibilità, consente di disabilitare o ignorare la password della schermata di blocco del dispositivo se quest'ultimo si trova in una posizione attendibile, ad esempio quando è connesso a un dispositivo Bluetooth specifico oppure quando è nelle vicinanze di un tag NFC. È possibile usare questa impostazione per impedire agli utenti di configurare Smart Lock.|
|**Numero di errori di accesso ripetuti consentiti prima della rimozione del profilo di lavoro**|Specifica il numero di errori di accesso consentiti prima della rimozione del profilo di lavoro dal dispositivo. Non viene eseguita una cancellazione completa dei dati del dispositivo.|
|**Ricorda cronologia password**|Impedisce il riutilizzo di password usate in precedenza.|
|**Ricorda cronologia password** - **Impedisci riutilizzo delle password precedenti**|Specifica il numero di password usate in precedenza che è necessario ricordare.|
|**Scadenza password (giorni)**|Specifica il numero di giorni prima che sia necessario modificare la password del dispositivo.|
|**Consenti sblocco tramite impronta digitale**<br>(Android 6.0+)|Consente di usare un'impronta digitale per sbloccare i dispositivi con questa funzionalità.|


### <a name="work-profile-settings"></a>Impostazioni del profilo di lavoro

|Nome impostazione|Dettagli|
|----------------|-|
|**Consenti la condivisione dei dati tra i profili di lavoro e personali**|Consente alle app del profilo di lavoro di condividere i dati con le app del profilo personale degli utenti. È possibile scegliere tra:<br><br>- **Impedisci qualsiasi condivisione tra i limiti**<br>- **Le app nel profilo di lavoro possono gestire una richiesta di condivisione dal profilo personale**<br>- **Nessuna restrizione sulla condivisione**|
|**Nascondi le notifiche del profilo di lavoro quando il dispositivo è bloccato**<br>(Android 6.0+)|Controllare se visualizzare le notifiche dal profilo di lavoro quando il dispositivo è bloccato.|
|**Imposta i criteri di autorizzazione predefiniti delle app**<br>(Android 6.0+)|Imposta i criteri di autorizzazione predefiniti per tutte le app del profilo di lavoro. A partire da Android 6, alcune autorizzazioni necessarie per le app vengono richieste all'utente finale in fase di esecuzione.  Questa impostazione di criteri consente al personale IT di decidere come o se richiedere agli utenti di concedere autorizzazioni per le app nel profilo di lavoro. <br/><br/>Ad esempio, il personale IT può eseguire il push nel profilo di lavoro di un'app che richiede l'accesso alla posizione.  In genere viene visualizzata una finestra di dialogo per chiedere all'utente se vuole concedere all'app l'accesso alla posizione e l'utente può approvare o rifiutare questa richiesta.  Questa impostazione di criteri consente al personale IT di decidere se tutte le autorizzazioni devono essere concesse o rifiutate automaticamente senza visualizzare un messaggio di richiesta oppure se lasciare la libertà di scelta all'utente.|


## <a name="custom-policy-settings"></a>Impostazioni di criteri personalizzati
Usare i **criteri di configurazione personalizzati Android for Work** di Microsoft Intune per distribuire le impostazioni OMA-URI che è possibile usare per controllare le funzionalità nei dispositivi Android for Work. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni Android non configurabili con i criteri di Intune.
Intune supporta attualmente un numero limitato di criteri personalizzati Android. Vedere gli esempi in questo argomento per scoprire quali criteri è possibile configurare.

### <a name="general-settings"></a>Impostazioni generali

|Nome impostazione|Dettagli|
    |----------------|--------------------|
    |**Nome**|Immettere un nome univoco per il criterio personalizzato Android che consenta di identificarlo nella console di Intune.|
    |**Descrizione**|Fornire una descrizione di carattere generale sul criterio personalizzato Android e altre informazioni rilevanti per consentirne l'individuazione.|

### <a name="oma-uri-settings"></a>Impostazioni OMA-URI

   |Nome impostazione|Dettagli|
    |--------|--------------------|
    |**Nome dell'impostazione**|Immettere un nome univoco per l'impostazione OMA URI per identificarla nell'elenco delle impostazioni.|
    |**Descrizione dell'impostazione**|Fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.|
    |**Tipo di dati**|Selezionare il tipo di dati in cui verrà specificata questa impostazione OMA URI. Scegliere tra **Stringa, Stringa (XML), Data e ora, Intero, Virgola mobile** o **Booleano**.|
    |**OMA-URI (maiuscole/minuscole)**|Specificare l'impostazione OMA-URI per cui si desidera fornire un'impostazione.|
    |**Valore**|Specificare il valore da associare all'impostazione OMA-URI specificata in precedenza.|

### <a name="examples"></a>Esempi

- [Creare un profilo Wi-Fi con una chiave precondivisa](pre-shared-key-wi-fi-profile.md)
- [Usare criteri personalizzati per creare un profilo VPN per app per dispositivi Android](per-app-vpn-for-android-pulse-secure.md)

### <a name="see-also"></a>Vedere anche
[Gestire impostazioni e funzionalità nei dispositivi con i criteri di Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)
