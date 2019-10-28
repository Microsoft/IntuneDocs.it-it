---
title: Impostazioni dei dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Aggiungere, configurare o creare le impostazioni nei dispositivi macOS per limitare l'uso delle funzionalità, tra cui impostare i requisiti per le password, controllare la schermata di blocco, usare le app predefinite, aggiungere app con restrizioni o approvate, gestire i dispositivi Bluetooth, connettersi al cloud per backup e archiviazione, abilitare la modalità tutto schermo, aggiungere domini e controllare il modo in cui gli utenti interagiscono con il Web browser Safari in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b2efdc04414d29fc1d8d200525cb3a4a880ec01
ms.sourcegitcommit: e9cf372711ff186ed468b01a9204631a139bd8e5
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776873"
---
# <a name="macos-device-settings-to-allow-or-restrict-features-using-intune"></a>Impostazioni dei dispositivi macOS per consentire o limitare l'uso delle funzionalità tramite Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Questo articolo descrive le diverse impostazioni che è possibile controllare nei dispositivi macOS. Usare queste impostazioni nella propria soluzione di gestione di dispositivi mobili (MDM) per abilitare o disabilitare funzionalità, impostare regole per le password, consentire o limitare l'uso di app specifiche e altro ancora.

Queste impostazioni vengono aggiunte a un profilo di configurazione del dispositivo in Intune e quindi assegnate o distribuite ai dispositivi macOS.

## <a name="before-you-begin"></a>Prima di iniziare

[Creare un profilo di configurazione delle restrizioni del dispositivo](../device-restrictions-configure.md).

> [!NOTE]
> Queste impostazioni si applicano a diversi tipi di registrazione. Per ulteriori informazioni sui diversi tipi di registrazione, vedere la pagina relativa alla [registrazione MacOS](../macos-enroll.md).

## <a name="general"></a>Generale

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

- **Ricerca della definizione**: **Blocca** impedisce all'utente di evidenziare una parola e quindi di cercarne la definizione nel dispositivo. **Non configurato** (impostazione predefinita) consente l'accesso alla funzionalità di ricerca della definizione.
- **Blocca la dettatura**: **Blocca** impedisce all'utente di immettere testo con l'input vocale. **Non configurato** (impostazione predefinita) consente all'utente di usare l'input con dettatura.
- **Memorizzazione nella cache dei contenuti**: scegliere **Non configurato** (impostazione predefinita) per abilitare la memorizzazione dei contenuti nella cache. La memorizzazione del contenuto nella cache consente di archiviare i dati di app e Web browser, download e altro ancora localmente nel dispositivo. Selezionare **Blocca** per impedire che questi dati siano archiviati nella cache.

  Per altre informazioni sulla memorizzazione del contenuto nella cache in macOS, vedere [Gestire la cache dei contenuti sul Mac](https://support.apple.com/guide/mac-help/manage-content-caching-on-mac-mchl3b6c3720/mac) (viene aperto un altro sito Web).

  Questa funzionalità si applica a:  
  - macOS 10.13 e versioni successive

- **Posticipa gli aggiornamenti software**: se impostato su **Non configurato** (impostazione predefinita), gli aggiornamenti software vengono visualizzati nel dispositivo non appena rilasciati da Apple. Ad esempio, se un aggiornamento macOS viene rilasciato da Apple in una data specifica, questo viene normalmente visualizzato nel dispositivo in prossimità della data di rilascio. Gli aggiornamenti della seed build sono consentiti senza posticipazioni.

  **Abilita** consente di posticipare la visualizzazione degli aggiornamenti software nei dispositivi, da 0 a 90 giorni. Questa impostazione non controlla quando gli aggiornamenti vengono installati o meno. 

  - **Posticipa la visibilità degli aggiornamenti software**: immettere un valore compreso tra 0 e 90 giorni. Quando l'intervallo di ritardo scade, gli utenti ricevono una notifica per l'aggiornamento alla versione del sistema operativo meno recente disponibile quando è stato attivato il ritardo.

    Ad esempio, se un aggiornamento di macOS è disponibile il **1° gennaio** e **Posticipa la visibilità** è impostato su **5 giorni**, l'aggiornamento non viene visualizzato come disponibile. Il **sesto giorno** dopo il rilascio, l'aggiornamento sarà disponibile e gli utenti finali possono installarlo.

    Questa funzionalità si applica a:  
    - macOS 10.13.4 e versioni successive

- **Schermate**: il dispositivo deve essere registrato nella registrazione automatica dei dispositivi (DEP) di Apple. Quando è impostato su **blocca**, gli utenti non possono salvare una schermata dello schermo. Impedisce anche all'app per le aule di osservare le schermate remote. **Non configurato** (impostazione predefinita) consente agli utenti di acquisire schermate e consente all'app per le classi di visualizzare le schermate remote.

### <a name="settings-apply-to-automated-device-enrollment"></a>Impostazioni applicabili a: registrazione automatica del dispositivo

- **Osservazione dello schermo remoto tramite l'app**per le aule: **Disabilita** impedisce agli insegnanti di usare l'app per le aule per visualizzare gli schermi degli studenti. **Non configurato** (impostazione predefinita) consente agli insegnanti di visualizzare le schermate degli studenti.

  Per usare questa impostazione, impostare l'impostazione **screenshot** su **non configurato** (sono consentite schermate).

- **Osservazione dello schermo non richiesta da parte dell'app per le classi**: **Allow** consente agli insegnanti di visualizzare le schermate degli studenti senza richiedere che lo studente accetti. **Non configurato** (impostazione predefinita) richiede che lo studente accetti prima che l'insegnante possa visualizzare le schermate.

  Per usare questa impostazione, impostare l'impostazione **screenshot** su **non configurato** (sono consentite schermate).

- **Gli studenti devono richiedere l'autorizzazione per lasciare la classe della classe**: **richiedere** forza agli studenti iscritti a un corso della classe non gestita per ottenere l'approvazione del docente per uscire dal corso. **Non configurato** (impostazione predefinita) consente agli studenti di uscire dal corso ogni volta che lo studente sceglie.

- Gli **insegnanti possono bloccare automaticamente i dispositivi o le app nell'app per le aule**: **Allow** consente agli insegnanti di bloccare il dispositivo o l'app di uno studente senza l'approvazione dello studente. **Non configurato** (impostazione predefinita) richiede che lo studente accetti prima che l'insegnante possa bloccare il dispositivo o l'app.

- **Gli studenti possono partecipare automaticamente alla classe class**: **Allow** consente agli studenti di partecipare a una classe senza richiedere l'insegnante. **Non configurato** (impostazione predefinita) richiede l'approvazione del docente per l'aggiunta a una classe.

## <a name="password"></a>Password

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

- **Password**: impostare **Rendi obbligatorio** per richiedere all'utente finale di immettere una password per accedere al dispositivo. **Non configurato** (impostazione predefinita) non richiede una password. Non impone inoltre alcuna restrizione, ad esempio il blocco di password semplici o l'impostazione di una lunghezza minima.
  - **Tipo di password richiesto**: specifica se la password può essere solo numerica o se deve essere di tipo alfanumerico, ovvero contenere lettere e numeri.

    Questa funzionalità si applica a:  
    - macOS 10.10.3 e versioni successive

  - **Numero di caratteri non alfanumerici nella password**: specifica il numero di caratteri complessi che è necessario includere nella password (da **0** a **4**).<br>Un carattere complesso è un simbolo, ad esempio " **?** ".
  - **Lunghezza minima password**: immettere la lunghezza minima della password che l'utente deve configurare, da **4** a **16** caratteri.
  - **Password semplici**: consente l'uso di password semplici come **0000** o **1234**.
  - **Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password**: specifica quanto tempo il computer deve rimanere inattivo prima che sia necessario inserire la password per sbloccarlo.
  - **Numero massimo di minuti di inattività fino al blocco dello schermo**: specifica il periodo di tempo per cui il computer deve rimanere inattivo prima che lo schermo venga bloccato.
  - **Scadenza password (giorni)** : specifica quanti giorni devono trascorrere prima che l'utente sia obbligato a cambiare la password, da **1** a **255** giorni.
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

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

- **Block Safari AutoFill** (Blocca riempimento automatico in Safari): **Blocca** disabilita la funzionalità di riempimento automatico in Safari nel dispositivo. **Non configurato** (impostazione predefinita) consente agli utenti di modificare le impostazioni di completamento automatico nel Web browser.
- **Blocca la fotocamera**: scegliere **Blocca** per impedire l'accesso alla fotocamera nel dispositivo. **Non configurato** (impostazione predefinita) consente l'accesso alla fotocamera del dispositivo.
- **Blocca Apple Music**: **Blocca** ripristina la modalità classica per l'app Music e disabilita il servizio Music. **Non configurato** (impostazione predefinita) consente l'uso dell'app Apple Music.
- **Impedisci a Spotlight di restituire i risultati della ricerca Internet**: **Blocca** impedisce a Spotlight di restituire risultati da una ricerca in Internet. **Non configurato** (impostazione predefinita) consente alla ricerca Spotlight di connettersi a Internet per fornire i risultati della ricerca.
- **Block File Transfer using iTunes** (Blocca il trasferimento di file tramite iTunes): **Blocca** disabilita i servizi di condivisione file dell'applicazione. **Non configurato** (impostazione predefinita) consente i servizi di condivisione file dell'applicazione.

  Questa funzionalità si applica a:  
  - macOS 10.13 e versioni successive

## <a name="restricted-apps"></a>App con restrizioni

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

- **Tipo di elenco di app con restrizioni**: creare un elenco di app che gli utenti non sono autorizzati a installare o usare. Le opzioni disponibili sono:

  - **Non configurato** (impostazione predefinita): nessuna restrizione da Intune. Gli utenti hanno accesso alle app assegnate e alle app predefinite.
  - **App non consentite**: app non gestite da Intune di cui si vuole evitare l'installazione nel dispositivo. Agli utenti non viene impedito di installare un'app vietata. Tuttavia, se un utente installa un'app da questo elenco, viene segnalata in Intune.
  - **App approvate**: app che gli utenti sono autorizzati a installare. Gli utenti non devono installare app che non sono elencate. Le app gestite da Intune sono automaticamente consentite. Agli utenti non viene impedito di installare un'app non inclusa nell'elenco approvato. Tuttavia, in caso affermativo, viene segnalato in Intune.
- **ID bundle dell'app**: immettere l'[ID bundle](bundle-ids-built-in-ios-apps.md) dell'app desiderata. È possibile mostrare o nascondere le app predefinite e le app line-of-business. Il sito Web di Apple include un elenco di [app Apple predefinite](https://support.apple.com/HT208094).
- **Nome app**: immettere il nome dell'app desiderata. È possibile mostrare o nascondere le app predefinite e le app line-of-business. Il sito Web di Apple include un elenco di [app Apple predefinite](https://support.apple.com/HT208094).
- **Autore**: immettere l'autore dell'app desiderata.

Per aggiungere app a questi elenchi, è possibile:

- **Aggiungi**: selezionare questa pagina per creare un elenco di app.
- Scegliere **Importa** per importare un file CSV con i dettagli sull'app, incluso l'URL. Usare il formato `<app bundle ID>, <app name>, <app publisher>`. In alternativa, **Esporta** per creare un elenco di app aggiunte, nello stesso formato.

## <a name="connected-devices"></a>Dispositivi connessi

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

- **Blocca AirDrop**: **Blocca** impedisce l'uso di AirDrop nel dispositivo. **Non configurato** (impostazione predefinita) consente l'uso della funzionalità AirDrop per scambiare contenuti con dispositivi vicini.
- **Block Apple Watch Auto Unlock** (Impedisci lo sblocco automatico con Apple Watch): **Blocca** impedisce agli utenti di sbloccare il proprio dispositivo macOS con Apple Watch. **Non configurato** (impostazione predefinita) consente agli utenti di sbloccare il proprio dispositivo macOS con Apple Watch.

## <a name="cloud-and-storage"></a>Cloud e risorse di archiviazione

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

- **Blocca la sincronizzazione Keychain con iCloud**: scegliere **Blocca** per disabilitare la sincronizzazione delle credenziali archiviate in Keychain su iCloud. **Non configurato** (impostazione predefinita) consente agli utenti di sincronizzare queste credenziali.
- **Block iCloud Document Sync** (Blocca la sincronizzazione di documenti in iCloud): **Blocca** impedisce a iCloud di sincronizzare documenti e dati. **Non configurato** (impostazione predefinita) consente la sincronizzazione di documenti e coppie chiave-valore nello spazio di archiviazione iCloud.
- **Block iCloud Mail Backup** (Blocca il backup di Mail di iCloud): **Blocca** impedisce a iCloud di sincronizzarsi con l'app Mail di macOS. **Non configurato** (impostazione predefinita) consente la sincronizzazione della posta con iCloud.
- **Block iCloud Contact Backup** (Blocca il backup di Contatti di iCloud): **Blocca** impedisce a iCloud di sincronizzare i contatti del dispositivo. **Non configurato** (impostazione predefinita) consente la sincronizzazione dei contatti tramite iCloud.
- **Block iCloud Calendar Backup** (Blocca il backup di Calendario di iCloud): **Blocca** impedisce a iCloud di sincronizzarsi con l'app Calendario di macOS. **Non configurato** (impostazione predefinita) consente la sincronizzazione del calendario con iCloud.
- **Block iCloud Reminder Backup** (Blocca il backup di Promemoria di iCloud): **Blocca** impedisce a iCloud di sincronizzarsi con l'app Promemoria di macOS. **Non configurato** (impostazione predefinita) consente la sincronizzazione dei promemoria con iCloud.
- **Block iCloud Bookmark Backup** (Blocca il backup di Preferiti di iCloud): **Blocca** impedisce a iCloud di sincronizzare i preferiti del dispositivo. **Non configurato** (impostazione predefinita) consente la sincronizzazione dei preferiti con iCloud.
- **Block iCloud Notes Backup** (Blocca il backup di Note di iCloud): **Blocca** impedisce a iCloud di sincronizzare le note del dispositivo. **Non configurato** (impostazione predefinita) consente la sincronizzazione delle note con iCloud.
- **Blocca la libreria foto iCloud**: il **blocco** Disabilita la libreria foto iCloud e impedisce a iCloud di sincronizzare le foto dei dispositivi. Eventuali foto non scaricate completamente dalla Libreria foto di iCloud vengono rimosse dall'archivio locale nel dispositivo. **Non configurato** (impostazione predefinita) consente di sincronizzare le foto tra il dispositivo e la libreria foto iCloud.
- **Consegna**: **non configurata** (impostazione predefinita) consente agli utenti di avviare il lavoro in un dispositivo MacOS e quindi continuare il lavoro avviato in un altro dispositivo iOS o MacOS. **Blocca** impedisce la funzionalità di continuità sul dispositivo. 

  Questa funzionalità si applica a:  
  - macOS 10.15 e versioni successive

## <a name="domains"></a>Domains

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>Le impostazioni si applicano a: registrazione del dispositivo e registrazione automatica dei dispositivi

- **URL del dominio di posta elettronica**: **Aggiungi** consente di aggiungere uno o più URL all'elenco. Quando gli utenti ricevono un messaggio di posta elettronica da un dominio diverso da quello configurato, il messaggio di posta elettronica viene contrassegnato come non attendibile nell'app di posta in macOS.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare il profilo](../device-profile-assign.md) e [monitorarne lo stato](../device-profile-monitor.md).

È possibile limitare funzionalità e impostazioni anche in dispositivi [iOS](../device-restrictions-ios.md).
