---
title: Impostazioni di conformità di macOS in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi macOS in Microsoft Intune. Richiedere la protezione dell'integrità del sistema di Apple, impostare le restrizioni relative alla password, richiedere un firewall, consentire un gatekeeper e così via.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813509"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di macOS per contrassegnare un dispositivo come conforme o non conforme in Intune

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi macOS in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per impostare una versione minima o massima del sistema operativo, impostare la scadenza delle password e così via.

Questa funzionalità si applica a:

- macOS

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). Per **Piattaforma**, selezionare **macOS**.

## <a name="device-health"></a>Integrità del dispositivo

- **Richiedi protezione dell'integrità del sistema**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
  - **Richiedi** : Richiedi ai dispositivi MacOS la [protezione dell'integrità del sistema](https://support.apple.com/HT204899) (apre il sito Web di Apple) abilitata.  

## <a name="device-properties"></a>Proprietà dispositivo

- **Versione minima richiesta del sistema operativo**:  
  Quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente del dispositivo può scegliere di aggiornare il dispositivo. In seguito, potrà accedere alle risorse dell'organizzazione.

- **Versione massima consentita del sistema operativo**:  
  Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella della regola, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente del dispositivo viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché una regola non viene modificata in modo da consentire la versione del sistema operativo.

- **Versione minima della build del sistema operativo**:  
  quando Apple pubblica aggiornamenti della sicurezza, in genere viene aggiornato il numero di build e non la versione del sistema operativo. Usare questa funzionalità per immettere un numero di build minimo consentito nel dispositivo.

- **Versione massima della build del sistema operativo**:  
  quando Apple pubblica aggiornamenti della sicurezza, in genere viene aggiornato il numero di build e non la versione del sistema operativo. Usare questa funzionalità per immettere un numero di build massimo consentito nel dispositivo.

## <a name="system-security-settings"></a>Impostazioni di sicurezza del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**:  
  - **Non configurato** (*impostazione predefinita*)
  - **Rendi obbligatorio**: gli utenti devono immettere una password prima di accedere al dispositivo.

- **Password semplici**:  
  - **Non configurato** (*impostazione predefinita*): gli utenti possono creare password semplici come **1234** o **1111**.
  - **Blocca**: impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**.

- **Lunghezza minima password**:  
  immettere il numero minimo di cifre o caratteri che la password deve avere.

- **Tipo di password**: scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).

- **Numero di caratteri non alfanumerici nella password**:  
  immettere il numero minimo di caratteri speciali, ad esempio `&`, `#`, `%`, `!` e così via, che è necessario includere nella password.

  Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa.

- **Numero massimo di minuti di inattività prima che venga richiesta la password**:  
  immettere il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni)** :  
  selezionare il numero di giorni che mancano alla scadenza della password attuale, quando l'utente deve creare una nuova password.

- **Numero di password precedenti di cui impedire il riutilizzo**:  
  immettere il numero di password usate in precedenza che non è possibile usare.
> [!IMPORTANT]
> Quando si modificano i requisiti per le password in un dispositivo macOS, le nuove impostazioni diventano effettive alla successiva modifica della password da parte dell'utente. Ad esempio, se si imposta il limite di lunghezza della password su otto cifre e il dispositivo macOS usa attualmente una password a sei cifre, il dispositivo resta conforme fino a quando l'utente non aggiorna la password nel dispositivo.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**:  
  - **Non configurato** (*impostazione predefinita*)
  - **Rendi obbligatorio**: usare *Rendi obbligatorio* per crittografare l'archivio dati nei dispositivi.

### <a name="device-security"></a>Sicurezza del dispositivo

L'impostazione Firewall protegge i dispositivi da accessi alla rete non autorizzati. È possibile usare Firewall per controllare le connessioni applicazione per applicazione. 

- **Firewall**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione lascia disattivato il firewall e consente il traffico di rete (non bloccato).
  - **Abilita**: usare *Abilita* per proteggere i dispositivi da accessi non autorizzati. Abilitando questa funzionalità è possibile gestire le connessioni Internet in ingresso e usare la modalità mascheramento. 

- **Connessioni in ingresso**:  
  - **Non configurato** (*impostazione predefinita*): consente le connessioni in ingresso e i servizi di condivisione.
  - **Blocca**: bloccare tutte le connessioni di rete in ingresso tranne le connessioni necessarie per i servizi Internet base, ad esempio DHCP, Bonjour e IPSec. Questa impostazione blocca anche tutti i servizi di condivisione, inclusi la condivisione dello schermo, l'accesso remoto e il servizio di condivisione di musica di iTunes e così via.  

- **Modalità mascheramento**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione lascia la modalità Stealth disabilitata.
  - **Abilita**: abilitare la modalità mascheramento per impedire che i dispositivi rispondano alle richieste di probe, che possono avere origine da utenti malintenzionati. Se l'impostazione è abilitata, il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate.  

### <a name="gatekeeper"></a>Gatekeeper

Per altre informazioni, vedere [Gatekeeper in macOS](https://support.apple.com/HT202491). Si aprirà il sito Web di Apple.

**Consenti le app scaricate da queste posizioni**: consente l'installazione nei dispositivi delle applicazioni supportate da posizioni diverse. Opzioni relative alla posizione:

- **Non configurato** (*impostazione predefinita*): l'opzione Gatekeeper non ha alcun effetto sulla conformità o la non conformità.  
- **Mac App Store**: consente di installare app solo da Mac App Store. Non è possibile installare app da terze parti o sviluppatori identificati. Se si imposta Gatekeeper per l'installazione di app al di fuori di Mac App Store, il dispositivo viene considerato non conforme.
- **Mac App Store e sviluppatori identificati**: consente di installare app da Mac App Store e sviluppatori identificati. macOS controlla l'identità degli sviluppatori ed esegue alcuni altri controlli per verificare l'integrità dell'app. Se si imposta Gatekeeper per l'installazione di app al di fuori di queste opzioni, il dispositivo viene considerato non conforme.
- **Ovunque**: consente di installare le app da qualsiasi posizione e sviluppatore. Questa opzione è la meno sicura.
 

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](../fundamentals/scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi iOS](compliance-policy-create-ios.md).