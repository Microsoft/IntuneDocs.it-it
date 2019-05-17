---
title: Impostazioni dei dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
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
ms.openlocfilehash: 5feec66e791da4038bd069cdad69a7ba573f27f3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798378"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Impostazioni dei dispositivi macOS per consentire o limitare l'uso delle funzionalità tramite Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi macOS. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, impostare regole per le password, consentire o limitare l'uso di app specifiche e altro ancora.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi macOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione delle restrizioni del dispositivo](device-restrictions-configure.md#create-the-profile).

## <a name="general"></a>Generale

- **Blocca la ricerca della definizione**: **Blocca** impedisce all'utente di evidenziare una parola e quindi di cercarne la definizione nel dispositivo. **Non configurato** (impostazione predefinita) consente l'accesso alla funzionalità di ricerca della definizione.
- **Block Dictation** (Blocca dettatura): **Blocca** impedisce all'utente di immettere testo con l'input vocale. **Non configurato** (impostazione predefinita) consente all'utente di usare l'input con dettatura.
- **Blocca la memorizzazione del contenuto nella cache**: scegliere **Non configurato** (impostazione predefinita) per abilitare la memorizzazione del contenuto nella cache. La memorizzazione del contenuto nella cache consente di archiviare i dati di app e Web browser, download e altro ancora localmente nel dispositivo. Selezionare **Blocca** per impedire che questi dati siano archiviati nella cache.

  Per altre informazioni sulla memorizzazione del contenuto nella cache in macOS, vedere [Gestire la cache dei contenuti sul Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (viene aperto un altro sito Web).

  Questa funzionalità si applica a:  
  - macOS 10.13 e versioni successive

- **Posticipa gli aggiornamenti software**: se impostato su **Non configurato** (impostazione predefinita), gli aggiornamenti software vengono visualizzati nel dispositivo non appena rilasciati da Apple. Ad esempio, se un aggiornamento macOS viene rilasciato da Apple in una data specifica, questo viene normalmente visualizzato nel dispositivo in prossimità della data di rilascio. Gli aggiornamenti della seed build sono consentiti senza posticipazioni.

  **Abilita** consente di posticipare la visualizzazione degli aggiornamenti software nei dispositivi, da 0 a 90 giorni. Questa impostazione non controlla quando gli aggiornamenti vengono installati o meno. 

  - **Posticipa la visibilità degli aggiornamenti software**: immettere un valore compreso tra 0 e 90 giorni. Quando l'intervallo di ritardo scade, gli utenti ricevono una notifica per l'aggiornamento alla versione del sistema operativo meno recente disponibile quando è stato attivato il ritardo.

    Ad esempio, se un aggiornamento di macOS è disponibile il **1° gennaio** e **Posticipa la visibilità** è impostato su **5 giorni**, l'aggiornamento non viene visualizzato come disponibile nei dispositivi. Il **sesto giorno** dopo il rilascio, l'aggiornamento sarà disponibile e gli utenti finali possono installarlo.

    Questa funzionalità si applica a:  
    - macOS 10.13.4 e versioni successive

## <a name="password"></a>Password

- **Password**: impostare **Rendi obbligatorio** per richiedere all'utente finale di immettere una password per accedere al dispositivo. **Non configurato** (impostazione predefinita) non richiede una password e non impone alcuna restrizione, ad esempio il blocco delle password semplici o l'impostazione di una lunghezza minima.
  - **Tipo di password richiesto**: specifica se la password può essere solo numerica o se deve essere di tipo alfanumerico, ovvero contenere lettere e numeri. Questa impostazione è supportata solo su Mac OS X 10.10.3 e versioni successive.
  - **Numero di caratteri non alfanumerici nella password**: specifica il numero di caratteri complessi che è necessario includere nella password (da **0** a **4**).<br>Un carattere complesso è un simbolo, ad esempio "**?**".
  - **Lunghezza minima password**: immettere la lunghezza minima della password che l'utente deve configurare, da **4** a **16** caratteri.
  - **Password semplici**: consente l'uso di password semplici come **0000** o **1234**.
  - **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**: specifica quanto tempo il computer deve rimanere inattivo prima che sia necessario inserire la password per sbloccarlo.
  - **Numero massimo di minuti di inattività fino al blocco dello schermo**: specifica il periodo di tempo per cui il computer deve rimanere inattivo prima che lo schermo venga bloccato.
  - **Scadenza password (giorni)**: specifica quanti giorni devono trascorrere prima che l'utente sia obbligato a cambiare la password, da **1** a **255** giorni.
  - **Impedisci riutilizzo delle password precedenti**: immettere il numero di password usate in precedenza che non possono essere riutilizzate, da **1** a **24**.

- **Block User from Modifying Passcode** (Impedisci all'utente di modificare il passcode): scegliere **Blocca** per impedire la modifica, l'aggiunta o la rimozione del passcode. **Non configurato** (impostazione predefinita) consente l'aggiunta, la modifica o la rimozione dei passcode.
- **Impedisci lo sblocco tramite impronta digitale**: scegliere **Blocca** per impedire l'uso di un'impronta digitale per sbloccare il dispositivo. **Non configurato** (impostazione predefinita) consente all'utente di sbloccare il dispositivo tramite impronta digitale.

- **Blocca il riempimento automatico delle password**: scegliere **Blocca** per impedire l'uso della funzionalità di riempimento automatico delle password in macOS. La scelta di **Blocca** comporta anche le conseguenze seguenti:

  - Agli utenti non viene richiesto di usare una password salvata in Safari o in qualsiasi app.
  - Le password complesse automatiche sono disabilitate e non vengono consigliate password complesse agli utenti.

  **Non configurato** (impostazione predefinita) consente queste funzionalità.

- **Blocca le richieste di prossimità password**: scegliere **Blocca** in modo che il dispositivo di un utente non richieda password dai dispositivi nelle vicinanze. **Non configurato** (impostazione predefinita) consente queste richieste di password.

- **Blocca la condivisione delle password**: **Blocca** impedisce la condivisione delle password tra i dispositivi tramite AirDrop. **Non configurato** (impostazione predefinita) consente di condividere le password.

## <a name="built-in-apps"></a>App predefinite

- **Block Safari AutoFill** (Blocca riempimento automatico in Safari): **Blocca** disabilita la funzionalità di riempimento automatico in Safari nel dispositivo. **Non configurato** (impostazione predefinita) consente agli utenti di modificare le impostazioni di completamento automatico nel Web browser.
- **Blocca la fotocamera**: scegliere **Blocca** per impedire l'accesso alla fotocamera nel dispositivo. **Non configurato** (impostazione predefinita) consente l'accesso alla fotocamera del dispositivo.
- **Blocca Apple Music**: **Blocca** ripristina la modalità classica per l'app Music e disabilita il servizio Music. **Non configurato** (impostazione predefinita) consente l'uso dell'app Apple Music.
- **Impedisci a Spotlight di restituire i risultati della ricerca Internet**: **Blocca** impedisce a Spotlight di restituire risultati da una ricerca in Internet. **Non configurato** (impostazione predefinita) consente alla ricerca Spotlight di connettersi a Internet per fornire i risultati della ricerca.
- **Block File Transfer using iTunes** (Blocca il trasferimento di file tramite iTunes): **Blocca** disabilita i servizi di condivisione file dell'applicazione. Disponibile in macOS 10.13 e versioni successive. **Non configurato** (impostazione predefinita) consente i servizi di condivisione file dell'applicazione.

## <a name="restricted-apps"></a>App con restrizioni

Nell'elenco delle app con restrizioni è possibile configurare uno degli elenchi seguenti:

- Un elenco **App non consentite**: elenca le app non gestite da Intune che gli utenti non sono autorizzati a installare ed eseguire. Agli utenti non viene impedito di installare un'app non consentita, ma se lo fanno, l'azione viene segnalata all'amministratore.
- Un elenco **App approvate**: elenca le app che gli utenti sono autorizzati a installare. Gli utenti non devono installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite. Agli utenti non viene impedito di installare un'app non inclusa nell'elenco approvato. Tuttavia, se lo fanno, l'azione viene segnalata all'amministratore.

Per configurare un elenco, fare clic su **Aggiungi** e quindi specificare il nome, facoltativamente l'autore dell'app e l'ID pacchetto dell'app (ad esempio *com.apple.calculator*).

## <a name="connected-devices"></a>Dispositivi connessi

- **Blocca AirDrop**: **Blocca** impedisce l'uso di AirDrop nel dispositivo. **Non configurato** (impostazione predefinita) consente l'uso della funzionalità AirDrop per scambiare contenuti con dispositivi vicini.
- **Block Apple Watch Auto Unlock** (Impedisci lo sblocco automatico con Apple Watch): **Blocca** impedisce agli utenti di sbloccare il proprio dispositivo macOS con Apple Watch. **Non configurato** (impostazione predefinita) consente agli utenti di sbloccare il proprio dispositivo macOS con Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione

- **Blocca la sincronizzazione Keychain con iCloud**: scegliere **Blocca** per disabilitare la sincronizzazione delle credenziali archiviate in Keychain su iCloud. **Non configurato** (impostazione predefinita) consente agli utenti di sincronizzare queste credenziali.
- **Block iCloud Document Sync** (Blocca la sincronizzazione di documenti in iCloud): **Blocca** impedisce a iCloud di sincronizzare documenti e dati. **Non configurato** (impostazione predefinita) consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.
- **Block iCloud Mail Backup** (Blocca il backup di Mail di iCloud): **Blocca** impedisce a iCloud di sincronizzarsi con l'app Mail di macOS. **Non configurato** (impostazione predefinita) consente la sincronizzazione della posta con iCloud.
- **Block iCloud Contact Backup** (Blocca il backup di Contatti di iCloud): **Blocca** impedisce a iCloud di sincronizzare i contatti del dispositivo. **Non configurato** (impostazione predefinita) consente la sincronizzazione dei contatti tramite iCloud.
- **Block iCloud Calendar Backup** (Blocca il backup di Calendario di iCloud): **Blocca** impedisce a iCloud di sincronizzarsi con l'app Calendario di macOS. **Non configurato** (impostazione predefinita) consente la sincronizzazione del calendario con iCloud.
- **Block iCloud Reminder Backup** (Blocca il backup di Promemoria di iCloud): **Blocca** impedisce a iCloud di sincronizzarsi con l'app Promemoria di macOS. **Non configurato** (impostazione predefinita) consente la sincronizzazione dei promemoria con iCloud.
- **Block iCloud Bookmark Backup** (Blocca il backup di Preferiti di iCloud): **Blocca** impedisce a iCloud di sincronizzare i preferiti del dispositivo. **Non configurato** (impostazione predefinita) consente la sincronizzazione dei preferiti con iCloud.
- **Block iCloud Notes Backup** (Blocca il backup di Note di iCloud): **Blocca** impedisce a iCloud di sincronizzare le note del dispositivo. **Non configurato** (impostazione predefinita) consente la sincronizzazione delle note con iCloud.

## <a name="domains"></a>Domains

- **URL del dominio di posta elettronica**: aggiungere uno o più URL all'elenco. Quando gli utenti ricevono un messaggio di posta elettronica da un dominio diverso da quello configurato, il messaggio di posta elettronica viene contrassegnato come non attendibile nell'app di posta in MacOS.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

È possibile limitare funzionalità e impostazioni anche in dispositivi [iOS](device-restrictions-ios.md).
