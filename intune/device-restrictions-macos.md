---
title: Impostazioni dei dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Aggiungere, configurare o creare le impostazioni nei dispositivi macOS per limitare l'uso delle funzionalità, tra cui impostare i requisiti per le password, controllare la schermata di blocco, usare le app predefinite, aggiungere app con restrizioni o approvate, gestire i dispositivi Bluetooth, connettersi al cloud per backup e archiviazione, abilitare la modalità tutto schermo, aggiungere domini e controllare il modo in cui gli utenti interagiscono con il Web browser Safari in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/13/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a59c40a5f1095e832f84c4b21d553e3c5f11ed7
ms.sourcegitcommit: 464cf677e3746eaba46836dedfb94572a75032f9
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58330420"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Impostazioni dei dispositivi macOS per consentire o limitare l'uso delle funzionalità tramite Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi macOS. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, impostare regole per le password, consentire o limitare l'uso di app specifiche e altro ancora.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi macOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione dispositivo restrizioni](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Generale

- **Blocca la ricerca della definizione**: **Blocca** impedisce all'utente di evidenziare una parola e quindi di cercarne la definizione nel dispositivo. **Non configurato** (impostazione predefinita) consente l'accesso alla funzionalità di ricerca della definizione.
- **Block Dictation** (Blocca dettatura): **Blocca** impedisce all'utente di immettere testo con l'input vocale. **Non configurato** (impostazione predefinita) consente all'utente di usare l'input con dettatura.
- **Blocca la memorizzazione nella cache del contenuto**: scegliere **non configurata** (predefinito) per abilitare la memorizzazione nella cache del contenuto. La memorizzazione nella cache contenuto archivia i dati dell'app, i dati del browser web, download e più in locale nel dispositivo. Selezionare **blocco** per impedire che i dati archiviati nella cache.

  Per altre informazioni sulla memorizzazione nella cache del contenuto in macOS, vedere [gestire la memorizzazione nella cache del contenuto in Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (si apre un altro sito Web).

  Questa funzionalità si applica a:  
  - macOS 10.13 e versioni successive

- **Rinvia gli aggiornamenti software**: se impostata su **non configurata** (impostazione predefinita), gli aggiornamenti software vengono visualizzati nel dispositivo non appena vengono rilasciati da Apple. Ad esempio, se un aggiornamento di macOS Ottiene rilasciato da Apple in una data specifica quindi che l'aggiornamento naturalmente viene visualizzato nel dispositivo attorno alla data di rilascio. Valore di inizializzazione compilazione aggiornamenti consentiti senza ritardo.

  **Abilitare** consente all'utente per il ritardo quando vengono visualizzati gli aggiornamenti software nei dispositivi, da 0 a 90 giorni. Questa impostazione non controlla gli aggiornamenti o quando non sono installati. 

  - **Ritardare la visibilità degli aggiornamenti software**: immettere un valore da 0 a 90 giorni. Quando l'intervallo di ritardo scade, gli utenti ricevono una notifica per l'aggiornamento alla versione del sistema operativo meno recente disponibile quando è stato attivato il ritardo.

    Ad esempio, se è disponibile in un aggiornamento di macOS **il 1 ° gennaio**, e **ritardare la visibilità** è impostata su **5 giorni**, quindi l'aggiornamento non viene visualizzato come un aggiornamento disponibile nei dispositivi. Nel **sesto giorno** successivi al rilascio, che è disponibile un aggiornamento e gli utenti finali possono eseguirne l'installazione.

    Questa funzionalità si applica a:  
    - macOS 10.13.4 e versioni successive

## <a name="password"></a>Password

- **Password**: impostare **Rendi obbligatorio** per richiedere all'utente finale di immettere una password per accedere al dispositivo. **Non configurato** (impostazione predefinita) non richiede una password e non impone alcuna restrizione, ad esempio il blocco di password semplici o impostare una lunghezza minima.
  - **Tipo di password richiesto**: specifica se la password può essere solo numerica o se deve essere di tipo alfanumerico, ovvero contenere lettere e numeri. Questa impostazione è supportata solo su Mac OS X 10.10.3 e versioni successive.
  - **Numero di caratteri non alfanumerici nella password**: specifica il numero di caratteri complessi che è necessario includere nella password (da **0** a **4**).<br>Un carattere complesso è un simbolo, ad esempio "**?**".
  - **Lunghezza minima password**: immettere la lunghezza minima della password che l'utente deve configurare, da **4** a **16** caratteri.
  - **Password semplici**: consente l'uso di password semplici come **0000** o **1234**.
  - **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**: specifica quanto tempo il computer deve rimanere inattivo prima che sia necessario inserire la password per sbloccarlo.
  - **Numero massimo di minuti di inattività fino al blocco dello schermo**: specifica il periodo di tempo per cui il computer deve rimanere inattivo prima che lo schermo venga bloccato.
  - **Scadenza password (giorni)**: specifica quanti giorni devono trascorrere prima che l'utente sia obbligato a cambiare la password, da **1** a **255** giorni.
  - **Impedisci riutilizzo delle password precedenti**: immettere il numero di password usate in precedenza che non possono essere riutilizzate, da **1** a **24**.

- **Impedisce all'utente la modifica di Passcode**: scegliere **blocco** per arrestare il passcode da eventuali modifiche, aggiunte o rimosse. **Non configurato** (impostazione predefinita) consente l'aggiunta, la modifica o la rimozione dei passcode.
- **Impedisci lo sblocco tramite impronta digitale**: scegliere **Blocca** per impedire l'uso di un'impronta digitale per sbloccare il dispositivo. **Non configurato** (impostazione predefinita) consente all'utente di sbloccare il dispositivo tramite impronta digitale.

- **Blocca il riempimento automatico delle password**: scegliere **Blocca** per impedire l'uso della funzionalità di riempimento automatico delle password in macOS. Scelta **blocco** anche con le seguenti conseguenze:

  - Agli utenti non viene richiesto di usare una password salvata in Safari o in qualsiasi app.
  - Le password complesse automatiche sono disabilitate e non vengono consigliate password complesse agli utenti.

  **Non configurato** (impostazione predefinita) consente queste funzionalità.

- **Blocca le richieste di prossimità password**: scegliere **Blocca** in modo che il dispositivo di un utente non richieda password dai dispositivi nelle vicinanze. **Non configurato** (impostazione predefinita) consente queste richieste di password.

- **Blocca la condivisione delle password**: **Blocca** impedisce la condivisione delle password tra i dispositivi tramite AirDrop. **Non configurato** (impostazione predefinita) consente di condividere le password.

## <a name="built-in-apps"></a>App predefinite

- **Block Safari AutoFill** (Blocca riempimento automatico in Safari): **Blocca** disabilita la funzionalità di riempimento automatico in Safari nel dispositivo. **Non configurato** (impostazione predefinita) consente agli utenti di modificare le impostazioni di completamento automatico nel Web browser.
- **Blocca la fotocamera**: scegliere **Blocca** per impedire l'accesso alla fotocamera nel dispositivo. **Non configurato** (impostazione predefinita) consente l'accesso alla fotocamera del dispositivo.
- **Blocca Apple Music**: **Blocca** ripristina la modalità classica per l'app Music e disabilita il servizio Music. **Non configurato** (impostazione predefinita) consente l'uso dell'app Apple Music.
- **Risultati della ricerca Internet di blocco in evidenza**: **blocco** arresta Spotlight di restituire risultati da una ricerca in Internet. **Non configurato** (impostazione predefinita) consente alla ricerca Spotlight di connettersi a Internet per fornire i risultati della ricerca.
- **Blocco di File trasferiti tramite iTunes**: **blocco** disabilita i servizi di condivisione file dell'applicazione. Disponibile in macOS 10.13 e versioni successive. **Non configurato** (impostazione predefinita) consente a servizi di condivisione file dell'applicazione.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

- Un elenco **App non consentite**: elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire. Gli utenti non sono impediti di installare un'app non consentita, ma in caso affermativo, viene segnalato all'amministratore.
- Un elenco **App approvate**: elenca le app che gli utenti sono autorizzati a installare. Gli utenti non devono installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite. Gli utenti non sono ha impediti di installare un'app che non è presente nell'elenco approvato. Tuttavia, in caso affermativo, viene segnalato all'amministratore.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'ID pacchetto dell'app (ad esempio *com.apple.calculator*).

## <a name="connected-devices"></a>Dispositivi connessi

- **Blocca AirDrop**: **Blocca** impedisce l'uso di AirDrop nel dispositivo. **Non configurato** (impostazione predefinita) consente l'uso della funzionalità AirDrop per scambiare contenuti con dispositivi vicini.
- **Lo sblocco automatico di blocco Apple Watch**: **blocco** impedisce agli utenti di sbloccare il dispositivo macOS con loro Apple Watch. **Non configurato** (impostazione predefinita) consente agli utenti di sbloccare il dispositivo macOS con loro Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione

- **Blocca la sincronizzazione Keychain con iCloud**: scegliere **Blocca** per disabilitare la sincronizzazione delle credenziali archiviate in Keychain su iCloud. **Non configurato** (impostazione predefinita) consente agli utenti di sincronizzare queste credenziali.
- **Blocco di sincronizzazione dei documenti iCloud**: **blocco** impedisce che la sincronizzazione di documenti e dati iCloud. **Non configurato** (impostazione predefinita) consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.
- **Bloccare iCloud Backup posta**: **blocco** impedisce che la sincronizzazione per l'app di posta elettronica macOS iCloud. **Non configurato** (impostazione predefinita) consente la sincronizzazione di posta elettronica su iCloud.
- **Bloccare iCloud Backup contattare**: **blocco** impedisce a iCloud di sincronizzare i contatti di dispositivi. **Non configurato** (impostazione predefinita) consente la sincronizzazione dei contatti con iCloud.
- **Bloccare iCloud Backup calendario**: **blocco** impedisce che la sincronizzazione per l'app del calendario macOS iCloud. **Non configurato** (impostazione predefinita) consente la sincronizzazione del calendario in iCloud.
- **Bloccare iCloud Backup promemoria**: **blocco** impedisce che la sincronizzazione all'app macOS promemoria iCloud. **Non configurato** (impostazione predefinita) consente la sincronizzazione di promemoria in iCloud.
- **Bloccare iCloud Backup segnalibro**: **blocco** impedisce che la sincronizzazione dei dispositivi segnalibri iCloud. **Non configurato** (impostazione predefinita) consente la sincronizzazione di segnalibro su iCloud.
- **Blocco note di Backup di iCloud**: **blocco** impedisce che la sincronizzazione dei dispositivi note iCloud. **Non configurato** (impostazione predefinita) consente la sincronizzazione di Lotus Notes su iCloud.

## <a name="domains"></a>Domains

- **URL del dominio di posta elettronica**: aggiungere uno o più URL all'elenco. Quando gli utenti ricevono un messaggio di posta elettronica da un dominio diverso da quello configurato, il messaggio di posta elettronica viene contrassegnato come non attendibile nell'app di posta in MacOS.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È inoltre possibile limitare le funzionalità del dispositivo e le impostazioni sul [iOS](device-restrictions-ios.md) dispositivi.
