---
title: Impostazioni di conformità di Windows 8.1 in Microsoft Intune - Azure | Microsoft Docs
description: Visualizzare un elenco di tutte le impostazioni che è possibile usare durante l'impostazione della conformità per i dispositivi Windows 8.1 e Windows Phone 8.1 in Microsoft Intune. Verificare la conformità nella versione minima e massima del sistema operativo, impostare le restrizioni relative alla password e la lunghezza, abilitare la crittografia nell'archiviazione dati e così via.
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
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813221"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Impostazioni di Windows 8.1 per contrassegnare un dispositivo come conforme o non conforme in Intune

Questo articolo elenca e descrive le diverse impostazioni di conformità che è possibile configurare nei dispositivi Windows 8.1 in Intune. Nella soluzione di gestione di dispositivi mobili (MDM), usare queste impostazioni per bloccare le password semplice, impostare una versione minima e massima del sistema operativo e così via.

Questa funzionalità si applica a:

- Windows Phone 8.1
- Windows 8.1 e versioni successive

Come amministratore di Intune, usare queste impostazioni di conformità per proteggere le risorse dell'organizzazione. Per altre informazioni sui criteri di conformità e sul loro funzionamento, vedere [Introduzione ai criteri di conformità dei dispositivi](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Prima di iniziare

[Creare i criteri di conformità](create-compliance-policy.md#create-the-policy). Per **Piattaforma** selezionare **Windows Phone 8.1** o **Windows 8.1 e versioni successive**.

## <a name="device-properties"></a>Proprietà dispositivo

### <a name="operating-system-version"></a>Versione del sistema operativo

**Windows Phone 8.1 e versioni successive**
- **Versione minima del sistema operativo per i dispositivi mobili**:  
  Immettere la versione minima consentita. Quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente del dispositivo può scegliere di aggiornare il dispositivo e quindi ottenere l'accesso alle risorse aziendali.

- **Versione massima del sistema operativo per dispositivi mobili**:  
  Immettere la versione massima consentita. Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente del dispositivo viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché una regola non viene modificata in modo da consentire la versione del sistema operativo.

**Windows 8.1 e versioni successive**
- **Versione minima del sistema operativo**:  
  Immettere la versione minima consentita. Quando un dispositivo non soddisfa il requisito relativo alla versione minima del sistema operativo, viene segnalato come non conforme. Viene visualizzato un collegamento con informazioni su come eseguire l'aggiornamento. L'utente del dispositivo può scegliere di aggiornare il dispositivo e quindi ottenere l'accesso alle risorse aziendali.

- **Versione massima del sistema operativo**:  
  Immettere la versione massima consentita. Quando un dispositivo usa una versione del sistema operativo successiva rispetto a quella specificata nella regola, l'accesso alle risorse dell'organizzazione viene bloccato. All'utente del dispositivo viene chiesto di contattare l'amministratore IT. Il dispositivo non può accedere alle risorse dell'organizzazione finché una regola non viene modificata in modo da consentire la versione del sistema operativo.

I PC Windows 8.1 restituiscono la versione **3**. Se la regola della versione del sistema operativo è impostata su Windows 8.1 per Windows, il dispositivo risulta non conforme anche se il sistema operativo installato è Windows 8.1.

## <a name="system-security"></a>Protezione del sistema

### <a name="password"></a>Password

- **Richiedi una password per sbloccare i dispositivi mobili**:  
  - **Non configurato** (*impostazione predefinita*): questa impostazione non viene valutata per la conformità o la non conformità.
  - **Rendi obbligatorio**: gli utenti devono immettere una password prima di accedere al dispositivo.

- **Password semplici**:  
  - **Non configurato** (*impostazione predefinita*): gli utenti possono creare password semplici, ad esempio **1234** o **1111**.
  - **Blocca**: impedire agli utenti di creare password semplici, ad esempio **1234** o **1111**.  

- **Lunghezza minima password**:  
  immettere il numero minimo di cifre o caratteri che la password deve avere.

  Per i dispositivi che eseguono Windows e a cui si accede con una account Microsoft, i criteri di conformità non eseguono correttamente la valutazione se viene soddisfatta una delle condizioni seguenti:  
  - Se la lunghezza minima della password è maggiore di otto caratteri
  - Se il numero minimo di set di caratteri è maggiore di due

- **Tipo di password**:  
  scegliere se una password deve avere solo caratteri **numerici** oppure una combinazione di numeri e altri caratteri (**alfanumerici**).

  Quando è impostato su *alfanumerico*, è disponibile l'impostazione seguente.  

  - **Numero di caratteri non alfanumerici nella password**:  
    Quando il *tipo di password* è impostato su **alfanumerico**, specificare il numero minimo di set di caratteri che la password deve contenere. Le opzioni includono da **0** a **4** set e il valore predefinito è **1**.
    
    I quattro set di caratteri sono:
    - Lettere minuscole
    - Lettere maiuscole
    - Simboli
    - Numeri

    Se si imposta un numero maggiore, l'utente dovrà creare una password più complessa. Per i dispositivi a cui si accede con una account Microsoft, i criteri di conformità non eseguono correttamente la valutazione se viene soddisfatta una delle condizioni seguenti:

    - Se la lunghezza minima della password è maggiore di otto caratteri
    - Se il numero minimo di set di caratteri è maggiore di due

- **Numero massimo di minuti di inattività prima che venga richiesta la password**:  
  immettere il tempo di inattività prima che l'utente debba immettere nuovamente la password.

- **Scadenza password (giorni)** :  
  selezionare il numero di giorni che mancano alla scadenza della password, quando l'utente deve creare una nuova password.

- **Numero di password precedenti di cui impedire il riutilizzo**:  
  immettere il numero di password usate in precedenza che non è possibile usare.

### <a name="encryption"></a>Crittografia

- **Crittografia dell'archivio dati nel dispositivo**:  
  - **Non configurato** (*impostazione predefinita*)
  - **Rendi obbligatorio**: usare *Rendi obbligatorio* per crittografare l'archivio dati nei dispositivi.


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere azioni per i dispositivi non conformi](actions-for-noncompliance.md) e [Usare i tag di ambito per filtrare i criteri](../fundamentals/scope-tags.md).
- [Monitorare i criteri di conformità](compliance-policy-monitor.md).
- Vedere [Impostazioni dei criteri di conformità per i dispositivi Windows 10 e versioni successive](compliance-policy-create-windows.md).