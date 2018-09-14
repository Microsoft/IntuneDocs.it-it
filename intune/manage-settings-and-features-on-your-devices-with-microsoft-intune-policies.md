---
title: Criteri dispositivo, profili e domande e risposte per Intune - Azure | Microsoft Docs
description: Informazioni su diversi criteri e profili che è possibile usare in Microsoft Intune, inclusi i criteri per configurare i dispositivi, ottenere accesso alle risorse aziendali, abilitare l'accesso condizionale e registrare i dispositivi aziendali. Inoltre, risposte alle domande più frequenti.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8a7a7405fe40d3568e736c244d9fcb308350709
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43318015"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>Gestire impostazioni e funzionalità nei dispositivi con i criteri di Intune

I *criteri* di Microsoft Intune sono gruppi di impostazioni che controllano le funzionalità nei dispositivi mobili e nei computer. Per creare criteri si usano modelli che includono impostazioni consigliate o personalizzate. Quindi, si procede alla loro distribuzione ai gruppi di utenti o di dispositivi.

## <a name="types-of-policies"></a>Tipi di criteri

I criteri di Intune rientrano nelle seguenti categorie. La categoria usata influisce sulla modalità di creazione e di distribuzione dei criteri.

- **Criteri di configurazione:** usati comunemente per gestire le impostazioni di sicurezza e le funzionalità dei dispositivi, incluso l'accesso alle risorse aziendali. Introduzione a [Profili di dispositivo in Intune](device-profiles.md).
- **Criteri di conformità dei dispositivi**: definiscono le regole e le impostazioni che un dispositivo deve avere per essere considerato conforme ai criteri di accesso condizionale. È anche possibile usare questi criteri per monitorare e correggere la conformità dei dispositivi indipendentemente dall'accesso condizionale. Introduzione a [Criteri di conformità dei dispositivi](device-compliance-get-started.md).
- **Criteri di accesso condizionale:** consentono di proteggere la posta elettronica e altri servizi in base alle condizioni immesse dall'utente. [Che cos'è l'accesso condizionale](conditional-access.md) e [Modi comuni per usare l'accesso condizionale](conditional-access-intune-common-ways-use.md) sono risorse utili per iniziare.
- **Criteri di registrazione dei dispositivi aziendali**: per informazioni sui criteri di registrazione dei dispositivi aziendali, vedere [Registrare i dispositivi iOS](ios-enroll.md).

## <a name="frequently-asked-questions-about-intune-policies"></a>Domande frequenti sui criteri Intune

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>Quanto tempo è necessario ai dispositivi mobili per ottenere i criteri o le app dopo la distribuzione?
Quando viene distribuito un criterio o un'app, Intune invia immediatamente una notifica al dispositivo perché questo contatti il servizio Intune. Questa operazione richiede in genere meno di 5 minuti.

Se dopo l'invio della prima notifica il dispositivo non contatta il servizio per ottenere il criterio, Intune esegue altri tre tentativi.  Se il dispositivo è offline, ad esempio è spento o non è connesso a una rete, è possibile che non riceva le notifiche. In questo caso, il dispositivo ottiene il criterio al successivo controllo pianificato con il servizio Intune, come indicato di seguito:

| Piattaforma | Frequenza di controllo |
| --- | --- |
| iOS | Ogni 6 ore | 
| Mac OS X | Ogni 6 ore |
| Android | Ogni 8 ore | 
| Windows Phone | Ogni 8 ore | 
| Windows 8.1  | Ogni 8 ore |  
| PC Windows 10 registrati come dispositivi | Ogni 8 ore | 

Se il dispositivo è stato registrato di recente, la frequenza di controllo è maggiore, come indicato di seguito:

| Piattaforma | Frequenza |
| --- | --- |
| iOS | Ogni 15 minuti per 6 ore e quindi ogni 6 ore |  
| Mac OS X | Ogni 15 minuti per 6 ore e quindi ogni 6 ore | 
| Android | Ogni 3 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 
| Windows Phone | Ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore | 
| PC Windows registrati come dispositivi | Ogni 3 minuti per 30 minuti e quindi ogni 8 ore | 

In qualsiasi momento gli utenti possono anche aprire l'app Portale aziendale e sincronizzare il dispositivo per controllare immediatamente la disponibilità di criteri.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quali azioni fanno sì che Intune invii immediatamente una notifica a un dispositivo?
I dispositivi contattano Intune quando ricevono una notifica che lo richiede o durante un controllo regolarmente pianificato.  Quando a un dispositivo o a un utente viene destinata un'azione di cancellazione dati, blocco, reimpostazione del passcode, distribuzione di app, distribuzione del profilo (Wi-Fi, VPN, posta elettronica) o distribuzione di criteri, Intune prova immediatamente a inviare una notifica al dispositivo per avvisarlo di contattare il servizio Intune.

Altre modifiche, ad esempio un aggiornamento delle informazioni di contatto nel portale aziendale, non comportano una notifica immediata ai dispositivi.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>Se vengono distribuiti più criteri per lo stesso utente o dispositivo, come si fa a sapere quali impostazioni vengono applicate?
Quando vengono distribuiti due o più criteri per lo stesso utente o dispositivo, la valutazione dell'impostazione che verrà applicata si verifica a livello di singola impostazione:

- Le impostazioni dei criteri di conformità hanno sempre la precedenza sulle impostazioni dei criteri di configurazione.

- Viene applicata l'impostazione di un criterio di conformità più restrittivo se valutata rispetto alla stessa impostazione in un criterio di conformità diverso.

- Se un'impostazione di un criterio di configurazione è in conflitto con un'impostazione di un altro criterio di configurazione, il conflitto viene visualizzato in Intune. Risolvere manualmente i conflitti.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>Cosa accade quando i criteri di gestione delle applicazioni mobili sono in conflitto tra loro? Quale viene applicato all'app?
I valori in conflitto sono le impostazioni più restrittive disponibili in un criterio MAM, ad eccezione dei campi di immissione numerici, come il numero di tentativi di immissione del PIN prima della reimpostazione,  che vengono impostati sugli stessi valori configurati durante la creazione di un criterio MAM nella console usando l'opzione delle impostazioni consigliate.

I conflitti si verificano quando due impostazioni dei criteri sono uguali.  Ad esempio, si supponga di aver configurato due criteri MAM identici tranne che per l'impostazione di copia/incolla.  In questo scenario, l'impostazione di copia/incolla viene impostata sul valore più restrittivo, ma il resto delle impostazioni viene applicato come è stato configurato.

Se un criterio viene distribuito nell'app e quindi applicato, e poi viene distribuito un secondo criterio, il primo avrà la precedenza e rimarrà applicato. Il secondo risulterà in conflitto. Se entrambi i criteri vengono applicati contemporaneamente, ovvero non esiste un criterio precedente, saranno entrambi in conflitto. Le impostazioni in conflitto vengono impostate sui valori più restrittivi.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>Cosa accade quando sono in conflitto i criteri personalizzati iOS?
Intune non valuta il payload dei file di configurazione Apple o del criterio personalizzato URI OMA (Open Mobile Alliance Uniform Resource Identifier), ma funge semplicemente da meccanismo di recapito.

Quando si distribuisce un criterio personalizzato, verificare che le impostazioni configurate non siano in conflitto con i criteri di conformità, di configurazione o con altri criteri personalizzati. Se un criterio personalizzato con impostazioni è in conflitto, l'ordine in cui le impostazioni vengono applicate sarà casuale.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>Che cosa accade quando un criterio viene eliminato o non è più applicabile?
Quando si elimina un criterio o si rimuove un dispositivo da un gruppo in cui è stato distribuito un criterio, il criterio e le impostazioni vengono rimossi dal dispositivo in base alle tabelle seguenti.

#### <a name="enrolled-devices"></a>dispositivi registrati

- Profili Wi-Fi, VPN, certificato e posta elettronica: questi profili vengono rimossi da tutti i dispositivi registrati supportati.
- Tutti gli altri tipi di criteri:
  - **Dispositivi Windows e Android**: le impostazioni non vengono rimosse dal dispositivo.
  - **Dispositivi Windows Phone 8.1**: vengono rimosse le impostazioni seguenti:
    - Richiedi una password per sbloccare i dispositivi mobili
    - Consenti password semplici
    - Lunghezza minima password
    - Tipo di password richiesto
    - Scadenza password (giorni)
    - Ricorda cronologia password
    - Numero di errori di accesso ripetuti consentiti prima della cancellazione del dispositivo
    - Minuti di inattività prima che venga richiesta la password
    - Tipo di password richiesto - numero minimo di set di caratteri
    - Consenti dispositivo foto/video
    - Richiedi crittografia sui dispositivi mobili
    - Consenti archivi rimovibili
    - Consenti browser Web
    - Consenti archivio applicazioni
    - Consenti acquisizione schermo
    - Consenti georilevazione
    - Consenti account Microsoft
    - Consenti copia e incolla
    - Consenti tethering Wi-Fi
    - Consenti connessione automatica agli hotspot Wi-Fi gratuiti
    - Consenti creazione report degli hotspot Wi-Fi
    - Consenti cancellazione
    - Consenti Bluetooth
    - Consenti NFC
    - Consenti Wi-Fi

  - **iOS**: vengono rimosse tutte le impostazioni, ad eccezione di:
    - Consenti roaming vocale
    - Consenti dati in roaming
    - Consenti sincronizzazione automatica durante il roaming

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Dove è possibile trovare contenuti sulla risoluzione dei problemi?

Vedere [Risolvere i problemi relativi ai criteri](troubleshoot-policies-in-microsoft-intune.md).
