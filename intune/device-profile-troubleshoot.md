---
title: Risolvere i problemi relativi ai profili di dispositivo in Microsoft Intune
titlesuffix: Azure portal
description: "Se si è rimasti bloccati, usare questo argomento per risolvere i problemi relativi ai profili di dispositivo Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ff950ce35c491ca576dc9cc77ab561e2cfef0381
ms.sourcegitcommit: 1df625330f4e8f7f661b5f2b9f16b5590971838d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2017
---
# <a name="troubleshooting-device-profiles-in-microsoft-intune"></a>Risolvere i problemi relativi ai profili di dispositivo in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare le informazioni contenute in questo argomento per risolvere i problemi comuni relativi ai profili di dispositivo in Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Perché un utente non ottiene un nuovo profilo quando modifica una password o una passphrase in un profilo Wi-Fi esistente? 
Quando si crea un profilo Wi-Fi aziendale, si distribuisce il profilo a un gruppo, si modifica la password e si salva il profilo, ci si aspetta che l'utente ottenga il nuovo profilo. Può tuttavia succedere che l'utente non ottenga il nuovo profilo. 

Per evitare questo problema, verificare di avere un'impostazione Wi-Fi guest in modo che l'utente esegua il fallback al Wi-Fi guest se il Wi-Fi aziendale non riesce. L'impostazione di connessione automatica deve essere abilitata. Questo profilo Wi-Fi guest deve essere distribuito a tutti gli utenti.

Esistono alcune procedure consigliate aggiuntive che è possibile eseguire:
- Poiché la rete Wi-Fi alla quale ci si connette richiede una password o passphrase, verificare che sia possibile connettersi direttamente al router Wi-Fi. È possibile eseguire il test con un dispositivo iOS.
- Dopo aver stabilito correttamente la connessione all'endpoint Wi-Fi (router Wi-Fi), prendere nota dell'identificatore SSID e delle credenziali usate, cioè della password o passphrase.
- Immettere l'identificatore SSID e le credenziali (password o passphrase) nel campo Chiave precondivisa. 
- Distribuire un gruppo di test con un numero limitato di utenti, preferibilmente solo il team IT. 
- Sincronizzare il proprio dispositivo iOS con Intune. Se non lo si è ancora fatto, procedere alla registrazione. 
- Provare a connettersi nuovamente allo stesso endpoint Wi-Fi (come indicato nel primo passaggio).
- Eseguire la distribuzione a gruppi di dimensioni maggiori e infine a tutti gli utenti previsti nell'organizzazione. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Quanto tempo è necessario ai dispositivi mobili per ottenere criteri o app dopo l'assegnazione?
Quando viene assegnato un criterio o un'app, Intune prova immediatamente a inviare una notifica al dispositivo perché questo contatti il servizio Intune per controllare la disponibilità di aggiornamenti. Questa operazione richiede in genere meno di 5 minuti.

Se dopo l'invio della prima notifica il dispositivo non contatta il servizio per ottenere il criterio, Intune esegue altri tre tentativi.  Se il dispositivo è offline, ad esempio è spento o non è connesso a una rete, può non ricevere le notifiche. In questo caso, il dispositivo otterrà il criterio al successivo controllo pianificato con il servizio Intune, come indicato di seguito:

- iOS e macOS: ogni 6 ore.
- Android: ogni 8 ore.
- Windows Phone: ogni 8 ore.
- PC Windows 8.1 e Windows 10 registrati come dispositivi: ogni 8 ore.

Se il dispositivo è stato appena registrato, la frequenza di controllo sarà maggiore, come indicato di seguito:

- iOS e macOS: ogni 15 minuti per 6 ore e successivamente ogni 6 ore.
- Android: ogni 3 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore.
- Windows Phone: ogni 5 minuti per 15 minuti, quindi ogni 15 minuti per 2 ore e infine ogni 8 ore.
- PC Windows registrati come dispositivi: ogni 3 minuti per 30 minuti e quindi ogni 8 ore.

In qualsiasi momento gli utenti possono anche aprire l'app Portale aziendale e sincronizzare il dispositivo per controllare immediatamente la disponibilità di criteri.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quali azioni fanno sì che Intune invii immediatamente una notifica a un dispositivo?
I dispositivi contattano Intune quando ricevono una notifica che lo richiede o durante un controllo regolarmente pianificato.  Quando si destina un'azione specifica a un dispositivo o a un utente, ad esempio la cancellazione di dati, il blocco, la reimpostazione del passcode, l'assegnazione di app, l'assegnazione del profilo (Wi-Fi, VPN, posta elettronica e così via) o l'assegnazione di criteri, Intune prova immediatamente a inviare una notifica al dispositivo perché questo contatti il servizio Intune per ricevere gli aggiornamenti.

Altre modifiche, ad esempio un aggiornamento delle informazioni di contatto nel portale aziendale, non comportano una notifica immediata ai dispositivi.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-will-get-applied"></a>Se vengono assegnati più criteri per lo stesso utente o dispositivo, come si determina quali impostazioni verranno applicate?
Quando vengono assegnati due o più criteri per lo stesso utente o dispositivo, la valutazione dell'impostazione che verrà applicata avviene a livello di singola impostazione:

-   Le impostazioni dei criteri di conformità hanno sempre la precedenza sulle impostazioni dei criteri di configurazione.

-   L'impostazione di un criterio di conformità più restrittivo viene applicata se viene valutata rispetto alla stessa impostazione in un criterio di conformità diverso.

-   Se un'impostazione dei criteri di configurazione è in conflitto con un'impostazione di un altro criterio di configurazione, il conflitto viene visualizzato nel portale di Azure. Tali conflitti devono essere risolti manualmente.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-will-be-applied-to-the-app"></a>Che cosa succede quando i criteri di protezione delle app sono in conflitto tra loro? Quale verrà applicato all'app?
I valori in conflitto sono le impostazioni più restrittive disponibili in un criterio di protezione delle app, ad eccezione dei campi di immissione numerici (come il numero di tentativi di immissione del PIN prima della reimpostazione),  che verranno impostati sugli stessi valori configurati durante la creazione di un criterio MAM nella console usando l'opzione delle impostazioni consigliate.

I conflitti si verificano quando due impostazioni del profilo sono uguali.  Ad esempio, si supponga di aver configurato due criteri MAM identici tranne che per l'impostazione di copia/incolla.  In questo scenario, l'impostazione di copia/incolla verrà impostata sul valore più restrittivo, ma il resto delle impostazioni verrà applicato come è stato configurato.

Se dopo l'assegnazione di un profilo all'app e la sua applicazione viene assegnato un secondo profilo, il primo avrà la precedenza e continuerà a essere applicato, mentre il secondo risulterà in conflitto. Se entrambi i profili vengono applicati contemporaneamente, ovvero non esiste un profilo precedente, saranno entrambi in conflitto. Le impostazioni in conflitto verranno impostate sui valori più restrittivi.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>Cosa accade quando sono in conflitto i criteri personalizzati iOS?
Intune non valuta il payload dei file di configurazione Apple o di un profilo personalizzato URI OMA (Open Mobile Alliance Uniform Resource Identifier), ma funge semplicemente da meccanismo di recapito.

Quando si assegna un profilo personalizzato, verificare che le impostazioni configurate non siano in conflitto con criteri di conformità, di configurazione o con altri criteri personalizzati. Nel caso di un profilo personalizzato con impostazioni in conflitto, l'ordine di applicazione delle impostazioni sarà casuale.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>Che cosa succede quando un profilo viene eliminato o non è più valido?
Quando si elimina un profilo o si rimuove un dispositivo da un gruppo cui è stato assegnato un profilo, il profilo e le impostazioni vengono rimossi dal dispositivo in base agli elenchi seguenti.

### <a name="enrolled-devices"></a>dispositivi registrati

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
I dispositivi Windows Phone non consentono che la sicurezza dei criteri di sicurezza impostati tramite MDM o EAS venga ridotta dopo averli configurati. Ad esempio, si imposta un **numero minimo di caratteri per la password** su 8 che poi si tenta di ridurre a 4. Il profilo più restrittivo è già stato applicato al dispositivo.

A seconda della piattaforma del dispositivo, se si vuole modificare il profilo impostando un valore meno sicuro, può essere necessario reimpostare i criteri di sicurezza.
Ad esempio, in Windows, sul desktop scorrere verso destra per aprire la barra **Accessi** e scegliere **Impostazioni** &gt; **Pannello di controllo**.  Selezionare l'applet **Account utente** .
Nella parte inferiore del menu di navigazione a sinistra è disponibile un collegamento **Reimposta criteri di sicurezza** . Selezionare tale collegamento e scegliere il pulsante **Reimposta criteri**.
È possibile che altri dispositivi MDM, ad esempio Android, Windows Phone 8.1 e versione successiva e iOS, debbano essere ritirati e registrati nuovamente nel servizio per permettere all'utente di applicare un profilo meno restrittivo.


### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](get-support.md).