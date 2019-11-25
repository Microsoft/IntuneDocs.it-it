---
title: Creare i criteri di conformità dei dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Creare i criteri di conformità, panoramica dei livelli di stato e gravità, utilizzo dello stato InGracePeriod, utilizzo dell'accesso condizionale, gestione dei dispositivi senza un criterio assegnato e differenze di conformità tra il portale di Azure e il portale classico in Microsoft Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8452f9b56032864380ec703bfd444dc85ef129b
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188271"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Creare criteri di conformità in Microsoft Intune

I criteri di conformità dei dispositivi sono una funzionalità fondamentale quando si usa Intune per proteggere le risorse dell'organizzazione. In Intune è possibile creare regole e impostazioni che i dispositivi devono soddisfare per essere considerati conformi, ad esempio la versione minima del sistema operativo. Se il dispositivo non è conforme, è possibile bloccare l'accesso ai dati e alle risorse tramite l'[accesso condizionale](conditional-access.md).

È anche possibile eseguire azioni specifiche in caso di mancata conformità, ad esempio inviare una notifica tramite posta elettronica all'utente. Per una panoramica degli effetti dei criteri di conformità e delle modalità di utilizzo, vedere [Introduzione ai criteri di conformità dei dispositivi in Intune](device-compliance-get-started.md).

Questo articolo:

- Illustra i prerequisiti e i passaggi da eseguire per creare criteri di conformità.
- Illustra come assegnare i criteri ai gruppi di utenti e di dispositivi.
- Descrive altre funzionalità, tra cui i tag di ambito per "filtrare" i criteri e le operazioni che è possibile eseguire sui dispositivi non conformi.
- Elenca la frequenza dei cicli di aggiornamento quando i dispositivi ricevono aggiornamenti dei criteri.

## <a name="before-you-begin"></a>Prima di iniziare

Per usare criteri di conformità del dispositivo, attenersi a quanto segue:

- Uso delle sottoscrizioni seguenti:

  - Intune
  - Se si usa l'accesso condizionale è necessario Azure Active Directory (AD) Premium. La pagina [Prezzi di Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/) spiega cosa si ottiene con le diverse edizioni. Azure AD non è necessario per la conformità di Intune.

- Uso di una piattaforma supportata:

  - Amministratore dispositivo Android
  - Android Enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Registrazione dei dispositivi in Intune (necessaria per visualizzarne lo stato di conformità)

- Registrazione dei dispositivi per un solo utente o senza un utente primario. Non sono supportati dispositivi registrati per più utenti.

## <a name="create-the-policy"></a>Creare i criteri

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Dispositivi** > **Criteri di conformità** > **Crea criterio**.

3. Specificare le proprietà seguenti:

   - **Nome**: immettere un nome descrittivo per il criterio. Assegnare ai criteri nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, un buon nome di criterio è **Dispositivi iOS jailbroken di Marco non conformi**.

   - **Description**: immettere una descrizione del criterio. Questa impostazione è facoltativa ma consigliata.

   - **Piattaforma**: scegliere la piattaforma dei dispositivi. Le opzioni disponibili sono:
     - **Amministratore di dispositivi Android**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 e versioni successive**
     - **Windows 10 e versioni successive**

     Per *Android Enterprise* è necessario selezionare un **tipo di profilo**:
     - **Proprietario del dispositivo**
     - **Profilo di lavoro**

   - **Impostazioni**: gli articoli seguenti elencano e descrivono le impostazioni per ogni piattaforma:
     - [Amministratore di dispositivi Android](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 versioni successive](compliance-policy-create-windows-8-1.md)
     - [Windows 10 e versioni successive](compliance-policy-create-windows.md)  

   - **Percorsi** *(Amministratore di dispositivi Android)* : Nei criteri è possibile forzare la conformità in base al percorso del dispositivo. Scegliere un percorso esistente. Se non si ha ancora una posizione, Vedere [Usare percorsi (limite della rete)](use-network-locations.md) in Intune per alcuni indicazioni.  

   - **Azioni per la mancata conformità**: Per i dispositivi che non soddisfano i criteri di conformità, è possibile aggiungere una sequenza di azioni da applicare automaticamente. Se il dispositivo è contrassegnato come non conforme, è possibile modificare la pianificazione, ad esempio dopo un giorno. È anche possibile configurare una seconda azione con cui inviare un messaggio di posta elettronica all'utente se il dispositivo risulta non conforme.

     [Aggiungere azioni per dispositivi non conformi](actions-for-noncompliance.md) offre altre informazioni, tra cui come creare un messaggio di posta elettronica di notifica per gli utenti.

     Si supponga, ad esempio, di usare la funzionalità Percorsi e di aggiungere un percorso in un criterio di conformità. L'azione predefinita per la mancata conformità viene applicata quando si seleziona almeno un percorso. Se il dispositivo non è connesso ai percorsi selezionati, viene immediatamente considerato non conforme. È possibile concedere agli utenti un periodo di tolleranza, ad esempio un giorno.

   - **Ambito (tag)** : I tag di ambito sono un metodo molto efficiente per assegnare e filtrare criteri a gruppi specifici, ad esempio ai reparti Vendite o Risorse umane, ai dipendenti di una filiale e così via. Dopo aver aggiunto le impostazioni, si può anche aggiungere un tag di ambito ai criteri di conformità. Per altre informazioni, vedere [Filtrare i criteri con tag di ambito](../fundamentals/scope-tags.md).

4. Al termine, selezionare **OK** > **Crea** per salvare le modifiche. Il criterio viene creato e visualizzato nell'elenco. Assegnare quindi il criterio ai gruppi.

## <a name="assign-the-policy"></a>Assegnare i criteri

Una volta creato un criterio, il passaggio successivo consiste nell'assegnarlo ai propri gruppi:

1. Scegliere un criterio precedentemente creato. I criteri esistenti sono in **Dispositivi** > **Criteri di conformità** > **Criteri**.

2. Selezionare il *criterio* > **Assegnazioni**. È possibile includere o escludere i gruppi di sicurezza di Azure Active Directory (AD).

3. Scegliere **Gruppi selezionati** per visualizzare i gruppi di sicurezza di Azure AD. Selezionare i gruppi a cui si vogliono applicare questi criteri > Scegliere **Salva** per distribuire i criteri.

Gli utenti o i dispositivi ai quali sono applicati i criteri vengono valutati per la conformità durante la sincronizzazione con Intune.

### <a name="evaluate-how-many-users-are-targeted"></a>Valutare il numero di utenti interessati

Quando si assegna il criterio, è anche possibile usare la funzionalità **Valuta** per calcolare il numero di utenti interessati. Questa funzionalità calcola gli utenti, non i dispositivi.

1. In Intune selezionare **Dispositivi** > **Criteri di conformità** > **Criteri**.

2. Selezionare un *criterio* > **Assegnazioni** > **Valuta**. Viene visualizzato un messaggio che indica il numero di utenti interessati da questo criterio.

Se il pulsante **Valuta** è disattivato, verificare che il criterio sia assegnato a uno o più gruppi.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>Frequenza dei cicli di aggiornamento

Intune usa diversi cicli di aggiornamento per verificare la disponibilità di aggiornamenti per i criteri di conformità. Se il dispositivo è stato registrato di recente, il controllo viene eseguito con maggiore frequenza. [Cicli di aggiornamento di criteri e profili](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned) elenca i tempi di aggiornamento stimati.

Gli utenti possono aprire in qualsiasi momento l'app Portale aziendale e sincronizzare il dispositivo, per verificare in tempo reale la disponibilità di aggiornamenti dei criteri.

### <a name="assign-an-ingraceperiod-status"></a>Assegnare uno stato InGracePeriod

Lo stato InGracePeriod è un valore dei criteri di conformità. Questo valore è determinato dalla combinazione del periodo di tolleranza del dispositivo e dello stato effettivo del dispositivo per tale criterio di conformità.

In particolare, se un dispositivo presenta uno stato NonCompliant per un criterio di conformità assegnato e:

- al dispositivo non è stato assegnato alcun periodo di tolleranza, quindi il valore assegnato per il criterio di conformità è NonCompliant
- il dispositivo ha un periodo di tolleranza scaduto, quindi il valore assegnato per il criterio di conformità è NonCompliant
- il dispositivo ha un periodo di tolleranza futuro, quindi il valore assegnato per il criterio di conformità è InGracePeriod

Nella tabella seguente sono riassunte le varie situazioni:

|Stato di conformità attuale|Valore del periodo di tolleranza assegnato|Stato di conformità effettivo|
|---------|---------|---------|
|NonCompliant |Nessun periodo di tolleranza assegnato |NonCompliant |
|NonCompliant |Data trascorsa|NonCompliant|
|NonCompliant |Data futura|InGracePeriod|

Per altre informazioni sul monitoraggio dei criteri di conformità dei dispositivi, vedere [Monitorare i criteri di conformità dei dispositivi di Intune](compliance-policy-monitor.md).

### <a name="assign-a-resulting-compliance-policy-status"></a>Assegnare uno stato dei criteri di conformità risultante

Se un dispositivo ha più criteri di conformità e il dispositivo presenta stati di conformità diversi per due o più dei criteri di conformità assegnati, verrà assegnato un unico stato di conformità risultante. Questa assegnazione si basa su un livello di gravità concettuale assegnato a ogni stato di conformità. I livelli di gravità di ogni stato di conformità sono i seguenti:

|Stato  |Gravità  |
|---------|---------|
|Sconosciuto     |1|
|NotApplicable     |2|
|Conforme|3|
|InGracePeriod|4|
|NonCompliant|5|
|Errore|6|

Quando un dispositivo ha più criteri di conformità, viene assegnato il livello di gravità massimo di tutti i criteri per quel dispositivo.

Ad esempio, un dispositivo ha tre criteri di conformità: uno con stato Sconosciuto (gravità = 1), uno con stato Conforme (gravità = 3) e uno con stato Periodo di tolleranza (gravità = 4). Lo stato Periodo di tolleranza ha il livello di gravità più alto. Tutti e tre i criteri hanno quindi lo stato di conformità Periodo di tolleranza.

## <a name="next-steps"></a>Passaggi successivi

[Monitorare i criteri](compliance-policy-monitor.md).
