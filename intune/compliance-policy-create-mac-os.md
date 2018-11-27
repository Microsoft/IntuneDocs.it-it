---
title: Creare criteri di conformità per i dispositivi macOS in Microsoft Intune - Azure | Microsoft Docs
description: Creare o configurare criteri di conformità per i dispositivi macOS in Microsoft Intune per usare la protezione dell'integrità del sistema, impostare la versione minima e massima del sistema operativo, scegliere i requisiti delle password e crittografare l'archivio dati.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 14588563dd261063071c09c1bbd3b428fb375830
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184183"
---
# <a name="add-a-device-compliance-policy-for-macos-devices-with-intune"></a>Aggiungere criteri di conformità per i dispositivi macOS con Intune

I criteri di conformità per i dispositivi macOS in Intune specificano le regole e le impostazioni che i dispositivi macOS devono soddisfare per essere conformi. Tramite i criteri di conformità del dispositivo con accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali. È anche possibile ottenere i report di dispositivo e intraprendere azioni per la mancata conformità. I criteri di conformità dei dispositivi possono essere creati per ogni piattaforma nel portale di Intune in Azure. Per altre informazioni sui criteri di conformità e sui requisiti, vedere [Introduzione alla conformità dei dispositivi](device-compliance-get-started.md).

La tabella seguente descrive come vengono gestite le impostazioni non conformi quando si usano criteri di conformità con criteri di accesso condizionale:

---------------------------

| Impostazione criterio | macOS 10.11 e versioni successive |
| --- | --- |
| **Configurazione di PIN o password** | Corretto |   
| **Crittografia dispositivo** | Corretto (impostando il PIN) |
| **Profilo di posta elettronica** | In quarantena |
|**Versione minima del sistema operativo** | In quarantena |
| **Versione massima del sistema operativo** | In quarantena |

---------------------------

**Con correzione** = il sistema operativo del dispositivo impone la conformità. Ad esempio, l'utente è obbligato a impostare un PIN.

**In quarantena** = il sistema operativo del dispositivo non impone la conformità. (Ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente.) Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

- Il dispositivo viene bloccato se un criterio di accesso condizionale si applica all'utente.
- Il portale aziendale segnala all'utente eventuali problemi di conformità.

## <a name="create-a-device-compliance-policy"></a>Creare criteri di conformità dei dispositivi

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. Per **Piattaforma**, selezionare **macOS**. Scegliere **Impostazioni Configura** e immettere le impostazioni **Integrità del dispositivo**, **Proprietà del dispositivo** e **Sicurezza del sistema**. Al termine, fare clic su **OK** e su **Crea**.

## <a name="device-health"></a>Integrità del dispositivo

- **Richiedi la protezione dell'integrità del sistema**: **rendere obbligatorio** per i dispositivi macOS che la [protezione dell'integrità del sistema](https://support.apple.com/HT204899) sia abilitata.

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima del sistema operativo**: quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente finale può scegliere di aggiornare il dispositivo e quindi ottenere l'accesso alle risorse aziendali.
- **Versione massima del sistema operativo**: quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse aziendali viene bloccato. All'utente viene richiesto di contattare l'amministratore IT. Finché la regola non viene modificata per poter consentire la versione del sistema operativo usata dal dispositivo, quest'ultimo non può accedere alle risorse aziendali.

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**: **richiedere** agli utenti di immettere una password prima di poter accedere al dispositivo.
- **Password semplici**: impostare questa opzione su **Blocca** per impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**. Impostare l'opzione su **Non configurata** per consentire agli utenti di creare password come **1234** o **1111**.
- **Lunghezza minima password**: immettere il numero minimo di cifre o caratteri per la password.
- **Tipo di password**: scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).
- **Numero di caratteri non alfanumerici nella password**: immettere il numero minimo di simboli o caratteri speciali (&, #, %, ! e così via), che è necessario includere nella password.

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**: immettere il tempo di inattività prima che l'utente debba immettere di nuovo la password.
- **Scadenza password (giorni)**: selezionare la durata in giorni della password. Dopo questo periodo di tempo, gli utenti devono crearne una nuova.
- **Numero di password precedenti di cui impedire il riutilizzo**: specificare il numero di password usate in precedenza che non è possibile usare.

    > [!IMPORTANT]
    > Quando si modificano i requisiti per le password in un dispositivo macOS, le nuove impostazioni diventano effettive alla successiva modifica della password da parte dell'utente. Ad esempio, se si imposta il limite di lunghezza della password su otto cifre e il dispositivo macOS usa attualmente una password a sei cifre, il dispositivo resta conforme fino a quando l'utente non aggiorna la password nel dispositivo.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**: scegliere **Rendi obbligatorio** per crittografare l'archivio dati nei dispositivi.

### <a name="device-security"></a>Sicurezza del dispositivo
L'impostazione Firewall protegge i dispositivi da accessi alla rete non autorizzati. È possibile usare Firewall per controllare le connessioni applicazione per applicazione. 

- **Firewall**: selezionare **Abilita** per proteggere i dispositivi da accessi non autorizzati. Abilitando questa funzionalità è possibile gestire le connessioni Internet in ingresso e usare la modalità mascheramento. L'opzione **Non configurato** (impostazione predefinita) lascia disattivato il firewall e consente il traffico di rete (non bloccato).
- **Connessioni in ingresso**: **blocca** tutte le connessioni di rete in ingresso tranne quelle necessarie per i servizi Internet di base, ad esempio DHCP, Bonjour e IPSec. Questa impostazione blocca anche tutti i servizi di condivisione, ad esempio la condivisione dello schermo, l'accesso remoto e il servizio di condivisione di musica di iTunes. L'opzione **Non configurato** (impostazione predefinita) consente le connessioni in ingresso e i servizi di condivisione. 
- **Modalità mascheramento**: selezionare **Abilita** per impedire che il dispositivo risponda alle richieste di probe, che possono avere origine da utenti malintenzionati. Se l'impostazione è abilitata, il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate. L'opzione **Non configurato** (impostazione predefinita) lascia disattivata la modalità mascheramento.

### <a name="gatekeeper"></a>Gatekeeper

**Consenti le app scaricate da queste posizioni**: consente l'installazione nei dispositivi delle applicazioni supportate da posizioni diverse. Opzioni relative alla posizione:

- **Non configurata**: impostazione predefinita. L'opzione Gatekeeper non influisce sulla conformità. 
- **Mac App Store**: consente di installare app solo da Mac App Store. Non è possibile installare app da terze parti o sviluppatori identificati. Se si imposta Gatekeeper per l'installazione di app al di fuori di Mac App Store, il dispositivo viene considerato non conforme.
- **Mac App Store e sviluppatori identificati**: consente di installare app da Mac App Store e sviluppatori identificati. macOS controlla l'identità degli sviluppatori ed esegue alcuni altri controlli per verificare l'integrità dell'app. Se si imposta Gatekeeper per l'installazione di app al di fuori di queste opzioni, il dispositivo viene considerato non conforme.
- **Ovunque**: consente di installare le app da qualsiasi posizione e sviluppatore. Questa opzione è la meno sicura.

Per altri dettagli nella documentazione Apple, vedere [Gatekeeper in macOS](https://support.apple.com/HT202491).

## <a name="assign-user-groups"></a>Assegnare gruppi di utenti

1. Scegliere un criterio configurato. I criteri esistenti sono in **Conformità del dispositivo** > **Criteri**.
2. Selezionare il criterio e scegliere **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).
3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi di utenti a cui si vuole applicare questo criterio e scegliere **Salva** per distribuire il criterio agli utenti.

> [!TIP]
> Per impostazione predefinita, i dispositivi verificano la conformità ogni otto ore, ma gli utenti possono forzare il processo tramite l'app Portale aziendale Intune.

Il criterio è stato applicato agli utenti. I dispositivi usati dagli utenti a cui è destinato il criterio vengono valutati per la conformità.

## <a name="next-steps"></a>Passaggi successivi
[Automatizzare la posta elettronica e aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md)  
[Monitorare i criteri di conformità dei dispositivi Intune](compliance-policy-monitor.md)
