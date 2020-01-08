---
title: Risolvere i problemi dei profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Domande e risposte comuni relative ai criteri e ai profili dei dispositivi con Microsoft Intune, tra cui mancata applicazione delle modifiche al profilo a determinati utenti o dispositivi, tempo necessario per la distribuzione di nuovi criteri ai dispositivi, impostazioni applicate quando sono presenti più criteri, conseguenze dell'eliminazione o rimozione di un profilo e altro ancora.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/04/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95186e4d1e54737ffeaa5e4c9728d188c2f867d6
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206636"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Domande e problemi comuni e soluzioni per i criteri e i profili dei dispositivi in Microsoft Intune



Risposte a domande comuni quando si gestiscono i criteri e i profili dei dispositivi in Intune. Questo articolo elenca anche gli intervalli di tempo del controllo, fornisce altre informazioni sui conflitti e altro ancora.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Perché un utente non ottiene un nuovo profilo quando modifica una password o una passphrase in un profilo Wi-Fi esistente?

Si crea un profilo Wi-Fi aziendale, si distribuisce il profilo a un gruppo, si modifica la password e si salva il profilo. Quando il profilo viene modificato, è possibile che alcuni utenti non ricevano il nuovo profilo.

Per evitare questo problema impostare l'accesso Wi-Fi guest. In caso di errori con il Wi-Fi aziendale, gli utenti possono connettersi al sistema Wi-Fi guest. Verificare di abilitare le impostazioni di connessione automatica. Distribuire il profilo Wi-Fi guest a tutti gli utenti.

Suggerimenti aggiuntivi:  

- Se la rete Wi-Fi alla quale ci si connette richiede una password o passphrase, verificare che sia possibile connettersi direttamente al router Wi-Fi. È possibile eseguire il test con un dispositivo iOS.
- Dopo aver stabilito correttamente la connessione all'endpoint Wi-Fi (router Wi-Fi), prendere nota dell'identificatore SSID e delle credenziali usate, che sono la password o passphrase.
- Immettere l'identificatore SSID e le credenziali (password o passphrase) nel campo Chiave precondivisa. 
- Eseguire la distribuzione a un gruppo di test con un numero di utenti limitato, preferibilmente solo al team IT. 
- Sincronizzare il proprio dispositivo iOS con Intune. Se non lo si è ancora fatto, procedere alla registrazione. 
- Provare a connettersi nuovamente allo stesso endpoint Wi-Fi (come indicato nel primo passaggio).
- Eseguire la distribuzione a gruppi di dimensioni maggiori e infine a tutti gli utenti previsti nell'organizzazione. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Quanto tempo è necessario ai dispositivi per ottenere criteri, un profilo o un'app dopo l'assegnazione?

Intune richiede al dispositivo di accedere al servizio Intune. I tempi di notifica variano da pochi secondi ad alcune ore. Questi tempi di notifica variano anche a seconda della piattaforma.

Se un dispositivo non esegue la sincronizzazione per ottenere il criterio o il profilo dopo la prima modifica, Intune esegue altri tre tentativi. Un dispositivo offline, ad esempio spento o non connesso a una rete, potrebbe non ricevere le notifiche. In questo caso, il dispositivo ottiene il criterio o il profilo in occasione della successiva sincronizzazione pianificata con il servizio Intune. Lo stesso vale per verificare la mancata conformità, inclusi i dispositivi che passano da uno stato conforme a uno stato non conforme.

Frequenze **stimate**:

| Piattaforma | Ciclo di aggiornamento|
| --- | --- |
| iOS | Ogni 8 ore circa |
| macOS | Ogni 8 ore circa |
| Android | Ogni 8 ore circa |
| PC Windows 10 registrati come dispositivi | Ogni 8 ore circa |
| Windows Phone | Ogni 8 ore circa |
| Windows 8.1 | Ogni 8 ore circa |

Se il dispositivo è stato registrato di recente, il controllo della conformità, della non conformità e della configurazione viene eseguito con maggiore frequenza, con i tempi **stimati** seguenti:

| Piattaforma | Frequenza |
| --- | --- |
| iOS | Ogni 15 minuti per 1 ora, quindi ogni 8 ore |  
| macOS | Ogni 15 minuti per 1 ora, quindi ogni 8 ore | 
| Android | Ogni 3 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore circa | 
| PC Windows 10 registrati come dispositivi | Ogni 3 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore circa | 
| Windows Phone | Ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore circa | 
| Windows 8.1 | Ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore circa | 

Gli utenti possono aprire in qualsiasi momento l'app Portale aziendale (**Impostazioni** > **Sincronizzazione**) per controllare immediatamente la disponibilità di aggiornamenti dei criteri o del profilo.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quali azioni fanno sì che Intune invii immediatamente una notifica a un dispositivo?

Sono disponibili diverse azioni che attivano una notifica, ad esempio quando un'app, un criterio o un profilo viene assegnato (o non assegnato), aggiornato, eliminato e così via. I tempi di queste azioni variano a seconda delle piattaforme.

I dispositivi contattano Intune quando ricevono una notifica o durante il controllo pianificato. Quando si destina a un dispositivo o a un utente un'azione come ad esempio il blocco, la reimpostazione del passcode o l'assegnazione di un'app, di un profilo o di criteri, Intune invia immediatamente al dispositivo una notifica per contattare il servizio e ricevere gli aggiornamenti.

Altre modifiche, ad esempio un aggiornamento delle informazioni di contatto nell'app Portale aziendale, non comportano una notifica immediata ai dispositivi.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se vengono assegnati più criteri allo stesso utente o dispositivo, come si determina quali impostazioni vengono applicate?

Quando due o più criteri vengono assegnati allo stesso utente o dispositivo, l'impostazione viene applicata a livello di singola impostazione:

- Le impostazioni dei criteri di conformità hanno sempre la precedenza sulle impostazioni del profilo di configurazione.

- Se un criterio di conformità viene valutato rispetto alla stessa impostazione in un altro criterio di conformità, viene applicata l'impostazione del criterio di conformità più restrittivo.

- Se un'impostazione di un criterio di configurazione è in conflitto con un'impostazione di un altro criterio di configurazione, il conflitto viene visualizzato in Intune. Risolvere manualmente i conflitti.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Che cosa succede quando i criteri di protezione delle app sono in conflitto tra loro? Quale viene applicato all'app?

I valori in conflitto sono le impostazioni più restrittive disponibili in un criterio di protezione delle app, *ad eccezione* dei campi di immissione numerici, come il numero di tentativi di immissione del PIN prima della reimpostazione. Questi campi vengono impostati sugli stessi valori configurati durante la creazione di un criterio MAM usando l'opzione delle impostazioni consigliate.

I conflitti si verificano quando due impostazioni del profilo sono uguali. Ad esempio, si supponga di aver configurato due criteri MAM identici tranne che per l'impostazione di copia/incolla. In questo scenario, l'impostazione di copia/incolla viene impostata sul valore più restrittivo, ma il resto delle impostazioni viene applicato come è stato configurato.

Un criterio viene distribuito all'app e diventa effettivo. Viene distribuito un secondo criterio. In questo scenario ha la precedenza il primo criterio, che rimane applicato. Il secondo criterio risulta in conflitto. Se entrambi vengono applicati contemporaneamente, ovvero non esiste un criterio precedente, saranno entrambi in conflitto. Le impostazioni in conflitto vengono impostate sui valori più restrittivi.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Cosa accade quando sono in conflitto i criteri personalizzati iOS?

Intune non valuta il payload dei file di configurazione Apple o del criterio personalizzato URI OMA (Open Mobile Alliance Uniform Resource Identifier), ma funge semplicemente da meccanismo di recapito.

Quando si assegna un criterio personalizzato, verificare che le impostazioni configurate non siano in conflitto con i criteri di conformità, di configurazione o con altri criteri personalizzati. Se un criterio personalizzato e le relative impostazioni sono in conflitto, le impostazioni vengono applicate in modo casuale.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Che cosa succede quando un profilo viene eliminato o non è più valido?

Quando si elimina un profilo o si rimuove un dispositivo da un gruppo che include il profilo, il profilo e le impostazioni vengono rimossi dal dispositivo come descritto di seguito:

- Profili Wi-Fi, VPN, certificato e di posta elettronica: questi profili vengono rimossi da tutti i dispositivi registrati supportati.
- Tutti gli altri tipi di profilo:  

  - **Dispositivi Windows e Android**: le impostazioni non vengono rimosse dal dispositivo
  - **Dispositivi Windows Phone 8.1**: Le seguenti impostazioni vengono rimosse:  
  
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

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Dopo aver modificato un profilo di restrizione dei dispositivi, le modifiche non sono state applicate

Una volta configurati, i dispositivi Windows Phone non consentono che la sicurezza dei criteri di sicurezza impostati tramite MDM o EAS venga ridotta. Ad esempio, si imposta un **numero minimo di caratteri per la password** su 8. Si prova quindi a ridurlo a 4. Il profilo più restrittivo è già applicato al dispositivo.

Per modificare il profilo impostando un valore meno sicuro, è necessario reimpostare i criteri di sicurezza. Ad esempio, nel desktop di Windows 8.1 scorrere rapidamente da destra e selezionare **Impostazioni** > **Pannello di controllo**. Selezionare l'applet **Account utente** . Nella parte inferiore del menu di spostamento visualizzato a sinistra è disponibile un collegamento **Reimposta criteri di sicurezza**. Selezionarlo e quindi scegliere **Reimposta criteri**.

È possibile che altri dispositivi MDM, ad esempio dispositivi Android, Windows Phone 8.1 e versione successiva, iOS e Windows 10 debbano essere ritirati e registrati nuovamente in Intune per applicare un profilo meno restrittivo.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Alcune impostazioni in un profilo Windows 10 restituiscono "Non applicabile"

Alcune impostazioni nei dispositivi Windows 10 potrebbero risultare "Non applicabili". In questo caso, quell'impostazione specifica non è supportata nella versione o nell'edizione di Windows in esecuzione nel dispositivo. Questo messaggio può essere visualizzato per i motivi seguenti:

- L'impostazione è disponibile solo per le versioni più recenti di Windows e non per la versione del sistema operativo in esecuzione nel dispositivo.
- L'impostazione è disponibile solo per edizioni specifiche di Windows o per SKU specifici, ad esempio Home, Professional, Enterprise e Education.

Per altre informazioni sui requisiti relativi a versioni e SKU per le diverse impostazioni, vedere [Configuration Service Provider (CSP) reference](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) (Informazioni di riferimento sul provider di servizi di configurazione).

## <a name="next-steps"></a>Passaggi successivi

È possibile ottenere altre informazioni. Vedere [Come ottenere supporto per Microsoft Intune](../fundamentals/get-support.md).
