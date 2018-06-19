---
title: Risolvere i problemi dei profili di dispositivo in Microsoft Intune - Azure | Microsoft Docs
description: Problemi comuni dei profili di dispositivo con Microsoft Intune nel portale Azure, quali mancata applicazione delle modifiche al profilo a determinati utenti o dispositivi, tempo necessario per la distribuzione di nuovi criteri ai dispositivi, impostazioni applicate quando sono presenti più criteri, conseguenze dell'eliminazione di un profilo e altro ancora
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8ceebe8b306893f9e6362a1aeb6ec119a650b90b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31026874"
---
# <a name="common-issues-and-resolutions-with-device-profiles-in-microsoft-intune"></a>Problemi comuni e soluzioni per i profili di dispositivo in Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Risolvere i problemi comuni usando i profili di dispositivo Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Perché un utente non ottiene un nuovo profilo quando modifica una password o una passphrase in un profilo Wi-Fi esistente? 
Si crea un profilo Wi-Fi aziendale, si distribuisce il profilo a un gruppo, si modifica la password e si salva il profilo. Quando il profilo viene modificato, è possibile che alcuni utenti non ricevano il nuovo profilo.

Per evitare questo problema impostare l'accesso Wi-Fi guest. In caso di errori con il Wi-Fi aziendale, gli utenti possono connettersi al sistema Wi-Fi guest. Verificare di abilitare le impostazioni di connessione automatica. Distribuire il profilo Wi-Fi guest a tutti gli utenti.

Suggerimenti aggiuntivi:  

- Poiché la rete Wi-Fi alla quale ci si connette richiede una password o passphrase, verificare che sia possibile connettersi direttamente al router Wi-Fi. È possibile eseguire il test con un dispositivo iOS.
- Dopo aver stabilito correttamente la connessione all'endpoint Wi-Fi (router Wi-Fi), prendere nota dell'identificatore SSID e delle credenziali usate, che sono la password o passphrase.
- Immettere l'identificatore SSID e le credenziali (password o passphrase) nel campo Chiave precondivisa. 
- Eseguire la distribuzione a un gruppo di test con un numero di utenti limitato, preferibilmente solo al team IT. 
- Sincronizzare il proprio dispositivo iOS con Intune. Se non lo si è ancora fatto, procedere alla registrazione. 
- Provare a connettersi nuovamente allo stesso endpoint Wi-Fi (come indicato nel primo passaggio).
- Eseguire la distribuzione a gruppi di dimensioni maggiori e infine a tutti gli utenti previsti nell'organizzazione. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Quanto tempo è necessario ai dispositivi mobili per ottenere criteri o app dopo l'assegnazione?
Quando viene assegnato un criterio o un'app, Intune invia immediatamente una notifica al dispositivo perché questo contatti il servizio Intune. Questa notifica richiede in genere meno di 5 minuti.

Se dopo l'invio della prima notifica il dispositivo non contatta il servizio per ottenere il criterio, Intune esegue altri tre tentativi. Se il dispositivo è offline, ad esempio è spento o non è connesso a una rete, è possibile che non riceva le notifiche. In questo caso, il dispositivo ottiene il criterio al successivo controllo pianificato con il servizio Intune, come indicato di seguito:

- iOS e macOS: ogni sei ore
- Android: ogni otto ore
- Windows Phone: ogni otto ore
- PC Windows 8.1 e Windows 10 registrati come dispositivi: ogni otto ore

Se il dispositivo è stato registrato di recente, la frequenza di controllo è maggiore, come indicato di seguito:

- iOS e macOS: ogni 15 minuti per sei ore e successivamente ogni sei ore
- Android: ogni tre minuti per 15 minuti, quindi ogni 15 minuti per due ore e poi ogni otto ore
- Windows Phone: ogni cinque minuti per 15 minuti, quindi ogni 15 minuti per due ore e poi ogni otto ore
- PC Windows registrati come dispositivi: ogni tre minuti per 30 minuti e quindi ogni otto ore

Per controllare immediatamente la disponibilità di criteri gli utenti possono anche aprire in qualsiasi momento l'app Portale aziendale e sincronizzare il dispositivo.

Per i dispositivi senza affinità utente, la frequenza di sincronizzazione che segue immediatamente la registrazione può variare da ore a un giorno o più. Intune invia richieste a vari intervalli al dispositivo perché quest'ultimo contatti il servizio. Spetta sempre al dispositivo decidere se eseguire o meno questa operazione. Non è possibile prevedere il tempo necessario per completare questa operazione dopo la registrazione iniziale, poiché ciò dipende dal tipo di registrazione e dai criteri e profili assegnati al dispositivo. Dopo la registrazione e l'applicazione di tutti i criteri iniziali, in genere il dispositivo verifica la disponibilità di nuovi criteri approssimativamente ogni sei ore.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quali azioni fanno sì che Intune invii immediatamente una notifica a un dispositivo?
I dispositivi contattano Intune per controllare la disponibilità di criteri quando ricevono una notifica o durante un controllo regolarmente pianificato. Quando si destina a un dispositivo o a un utente un'azione come ad esempio la cancellazione di dati, il blocco, la reimpostazione del passcode, l'assegnazione di app, l'assegnazione del profilo o l'assegnazione di criteri, Intune richiede immediatamente al dispositivo di contattare il servizio Intune per ricevere gli aggiornamenti.

Altre modifiche, ad esempio un aggiornamento delle informazioni di contatto nel portale aziendale, non comportano una notifica immediata ai dispositivi.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se vengono assegnati più criteri allo stesso utente o dispositivo, come si determina quali impostazioni vengono applicate?
Se allo stesso utente o dispositivo sono assegnati due o più criteri, le impostazioni vengono applicate a livello di singola opzione:

-   Le impostazioni dei criteri di conformità hanno sempre la precedenza sulle impostazioni dei criteri di configurazione

-   Se i criteri di conformità vengono valutati rispetto alla stessa impostazione in criteri di conformità diversi, vengono applicati i criteri più restrittivi.

-   Se un'impostazione dei criteri di configurazione è in conflitto con un'impostazione di altri criteri di configurazione, il conflitto viene visualizzato nel portale di Azure. In questo scenario è necessario risolvere manualmente i conflitti.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>Che cosa succede quando i criteri di protezione delle app sono in conflitto tra loro? Quale viene applicato all'app?
I valori in conflitto sono le impostazioni più restrittive disponibili in un criterio di protezione delle app, ad eccezione dei campi di immissione numerici (come il numero di tentativi di immissione del PIN prima della reimpostazione), che vengono impostati sugli stessi valori configurati durante la creazione di un criterio MAM nella console usando l'opzione delle impostazioni consigliate.

I conflitti si verificano quando due impostazioni del profilo sono uguali. Ad esempio, si supponga di aver configurato due criteri MAM identici tranne che per l'impostazione di copia/incolla. In questo scenario, l'impostazione di copia/incolla viene impostata sul valore più restrittivo, ma il resto delle impostazioni viene applicato come è stato configurato.

Se dopo l'assegnazione di un profilo all'app e la sua applicazione viene assegnato un secondo profilo, il primo ha la precedenza e continuerà a essere applicato, mentre il secondo risulterà in conflitto. Se entrambi i profili vengono applicati contemporaneamente, ovvero non esiste un profilo precedente, saranno entrambi in conflitto. Le impostazioni in conflitto vengono impostate sui valori più restrittivi.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Cosa accade quando sono in conflitto i criteri personalizzati iOS?
Intune non valuta il payload dei file di configurazione Apple o di un profilo personalizzato URI OMA (Open Mobile Alliance Uniform Resource Identifier), ma funge semplicemente da meccanismo di recapito.

Quando si assegna un profilo personalizzato, verificare che le impostazioni configurate non siano in conflitto con criteri di conformità, di configurazione o con altri criteri personalizzati. Se un profilo personalizzato e le relative impostazioni sono in conflitto, le impostazioni vengono applicate in modo casuale.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Che cosa succede quando un profilo viene eliminato o non è più valido?
Quando si elimina un profilo o si rimuove un dispositivo da un gruppo che include il profilo, il profilo e le impostazioni vengono rimossi dal dispositivo in base agli elenchi seguenti:

- Profili Wi-Fi, VPN, certificato e posta elettronica: questi profili vengono rimossi da tutti i dispositivi registrati supportati.
- Tutti gli altri tipi di profilo:  
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
        - Consenti ripristino impostazioni predefinite
        - Consenti Bluetooth
        - Consenti NFC
        - Consenti Wi-Fi

    - **iOS**: vengono rimosse tutte le impostazioni, ad eccezione di:
        - Consenti roaming vocale
        - Consenti dati in roaming
        - Consenti sincronizzazione automatica durante il roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Dopo aver modificato un profilo di restrizione dei dispositivi, le modifiche non sono state applicate
I dispositivi Windows Phone non consentono che la sicurezza dei criteri di sicurezza impostati tramite MDM o EAS venga ridotta dopo averli configurati. Ad esempio, si imposta un **numero minimo di caratteri per la password** su 8 e poi si prova a ridurlo a 4. Il profilo più restrittivo è già stato applicato al dispositivo.

A seconda della piattaforma del dispositivo, se si vuole modificare il profilo impostando un valore meno sicuro è necessario reimpostare i criteri di sicurezza. Ad esempio nel desktop di Windows scorrere verso destra e selezionare **Impostazioni** > **Pannello di controllo**. Selezionare l'applet **Account utente** .

Nella parte inferiore del menu di spostamento visualizzato a sinistra è disponibile un collegamento **Reimposta criteri di sicurezza**. Selezionarlo e quindi scegliere **Reimposta criteri**. È possibile che altri dispositivi MDM, ad esempio dispositivi Android, Windows Phone 8.1 e versione successiva e iOS, debbano essere ritirati e registrati nuovamente nel servizio per applicare un profilo meno restrittivo.

## <a name="next-steps"></a>Passaggi successivi
È possibile ottenere altre informazioni. Vedere [Come ottenere supporto per Microsoft Intune](get-support.md).