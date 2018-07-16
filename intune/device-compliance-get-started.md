---
title: Criteri di conformità dei dispositivi iOS in Microsoft Intune - Azure | Microsoft Docs
description: Requisiti per l'utilizzo dei criteri di conformità, panoramica dei livelli di stato e gravità, utilizzo dello stato InGracePeriod, utilizzo dell'accesso condizionale, gestione dei dispositivi senza un criterio assegnato e differenze di conformità tra il portale di Azure e il portale classico in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb81e070542248f585717564f0a609a512389ae2
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905071"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Introduzione ai criteri di conformità dei dispositivi in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I requisiti di conformità sono essenzialmente delle regole, ad esempio richiedere un PIN del dispositivo o richiedere la crittografia. I criteri di conformità dei dispositivi definiscono tali regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme. Queste regole includono:

- Uso di una password per l'accesso ai dispositivi

- Crittografia

- Dispositivo non manomesso con jailbreak o root

- Versione minima richiesta del sistema operativo

- Versione massima consentita del sistema operativo

- Dispositivo non al di sopra del livello di Mobile Threat Defense

È anche possibile usare questi criteri per monitorare lo stato di conformità nei dispositivi.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>Prerequisiti
Per usare i criteri di conformità dei dispositivi, devono essere soddisfatti i requisiti seguenti:

- Uso delle sottoscrizioni seguenti:

  - Intune
  - Azure Active Directory (AD) Premium

- Uso di una piattaforma supportata:

  - Android
  - iOS
  - macOS (anteprima)
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- Per segnalare il proprio stato di conformità, i dispositivi devono essere registrati in Intune

- Sono supportati i dispositivi registrati per un utente o i dispositivi senza utente primario. Più contesti utente non sono supportati.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Funzionamento dei criteri di conformità Intune con Azure AD

Al momento della registrazione in Intune viene avviato il processo di registrazione di Azure AD durante il quale gli attributi del dispositivo vengono aggiornati in Azure AD. Un'informazione chiave è lo stato di conformità del dispositivo. Lo stato di conformità che viene usato dai criteri di accesso condizionale per bloccare o consentire l'accesso alla posta elettronica e ad altre risorse aziendali.

In [processo di registrazione di AD Azure](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction) vengono fornite ulteriori informazioni.

### <a name="assign-a-resulting-device-configuration-profile-status"></a>Assegnare uno stato del profilo di configurazione del dispositivo risultante

Se un dispositivo ha più profili di configurazione e il dispositivo presenta stati di conformità diversi per due o più dei profili di configurazione assegnati, sarà necessario assegnare un unico stato di conformità risultante. Questa assegnazione si basa su un livello di gravità concettuale assegnato a ogni stato di conformità. I livelli di gravità di ogni stato di conformità sono i seguenti:

|Stato  |Gravità  |
|---------|---------|
|Pending     |1|
|Operazione completata     |2|
|Operazione non riuscita     |3|
|Errore     |4|

Quando un dispositivo ha più profili di configurazione, viene assegnato il livello di gravità massimo di tutti i profili per quel dispositivo.

Si osservi ad esempio il caso di un dispositivo con tre profili: uno nello stato in sospeso (gravità = 1), uno nello stato completato (gravità = 2) e uno nello stato di errore (gravità = 4). Lo stato di errore ha il livello di gravità più alto quindi, a tutti e tre i profili viene assegnato Errore come stato di conformità.

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

Si osservi ad esempio il caso di un dispositivo con tre criteri di conformità: uno con stato sconosciuto (gravità = 1), uno con stato conforme (gravità = 3) e uno con stato periodo di tolleranza (gravità = 4). Lo stato InGracePeriod ha il livello di gravità più alto quindi, a tutti e tre i criteri viene assegnato lo stato di conformità InGracePeriod.

## <a name="ways-to-use-device-compliance-policies"></a>Modi per usare i criteri di conformità del dispositivo

#### <a name="with-conditional-access"></a>Con l'accesso condizionale
Ai dispositivi conformi alle regole dei criteri è possibile consentire l'accesso alla posta elettronica e ad altre risorse aziendali. Se non sono conformi alle regole dei criteri, i dispositivi non ricevono l'accesso alle risorse aziendali. Questo è l'accesso condizionale.

#### <a name="without-conditional-access"></a>Senza l'accesso condizionale
È anche possibile usare i criteri di conformità dei dispositivi senza accesso condizionale. In tal caso, i dispositivi vengono valutati e segnalati in base allo stato di conformità. Può ad esempio essere utile segnalare quanti dispositivi non sono crittografati o quali dispositivi sono stati manomessi con jailbreak o root. Quando si usano i criteri di conformità senza accesso condizionale, non vengono applicate limitazioni per l'accesso alle risorse aziendali.

## <a name="ways-to-deploy-device-compliance-policies"></a>Modi per distribuire i criteri di conformità dei dispositivi
È possibile distribuire i criteri di conformità a utenti in gruppi di utenti o a dispositivi in gruppi di dispositivi. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata su tutti i dispositivi dell'utente.

La sezione **Impostazioni dei criteri di conformità** (portale di Azure > Conformità del dispositivo) include:

- **Contrassegna i dispositivi senza criteri di conformità assegnati come**: questa proprietà ha due valori:

  - **Conforme**: la funzione di sicurezza non è attiva
  - **Non conforme** (impostazione predefinita): la funzione di sicurezza è attiva

  Un dispositivo a cui non è stato assegnato un criterio di conformità è considerato come non conforme. Per impostazione predefinita, i dispositivi sono contrassegnati come **Conforme**. Se si usa l'accesso condizionale, è consigliabile modificare l'impostazione su **Non conforme**. Se un utente finale non è conforme perché non è stato assegnato un criterio, nel Portale aziendale viene indicato `No compliance policies have been assigned`.

- **Rilevamento ottimizzato per jailbreak**: se abilitata, questa impostazione attiva un'archiviazione più frequente dei dispositivi iOS con Intune. L'abilitazione di questa proprietà usa i servizi di posizione del dispositivo e influisce sull'utilizzo della batteria. I dati relativi alla posizione dell'utente non vengono archiviati da Intune.

  Per l'abilitazione di questa impostazione è necessario che:
  - Nei dispositivi siano abilitati i servizi di posizione a livello di sistema operativo
  - I dispositivi consentano al portale aziendale di utilizzare servizi di posizione
  - I dispositivi valutino e segnalino il proprio stato jailbreak a Intune almeno una volta ogni 72 ore. In caso contrario, il dispositivo è contrassegnato come non conforme.

- **Periodo di validità dello stato di conformità (giorni)**: immettere il periodo di tempo di cui dispongono i dispositivi per segnalare lo stato di tutti i criteri di conformità ricevuti. I dispositivi che non restituiscono lo stato entro il periodo indicato vengono considerati non conformi. Il valore predefinito è 30 giorni.

Tutti i dispositivi dispongono di **Criteri di conformità del dispositivo predefiniti** (portale di Azure > Conformità del dispositivo > Conformità dei criteri). Usare questo criterio predefinito per monitorare queste impostazioni.

Per informazioni sul tempo necessario ai dispositivi mobili per ottenere un criterio dopo la distribuzione, vedere [Risolvere i problemi relativi ai profili dei dispositivi](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

I report di conformità sono un ottimo modo per controllare lo stato dei dispositivi. Vedere [Monitorare i criteri di conformità](compliance-policy-monitor.md) per informazioni aggiuntive.

### <a name="actions-for-noncompliance"></a>Azioni per la mancata conformità
È possibile configurare una sequenza temporale di azioni da applicare ai dispositivi che non soddisfano i criteri di conformità. Queste azioni per la non conformità possono essere automatizzate, come descritto in [Automatizzare azioni per la non conformità](actions-for-noncompliance.md).

## <a name="azure-classic-portal-vs-azure-portal"></a>Differenze tra portale di Azure classico e Portale di Azure

La differenza principale rispetto all'uso dei criteri di conformità dei dispositivi nel portale di Azure:

- Nel portale di Azure i criteri di conformità vengono creati separatamente per ogni piattaforma supportata
- Nel portale di Azure classico un criterio di conformità è comune a tutte le piattaforme supportate

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>Criteri di conformità dei dispositivi nel portale classico e nel portale di Azure

I criteri di conformità dei dispositivi creati nel [portale classico](https://manage.microsoft.com) non compaiono nel [portale di Azure](https://portal.azure.com). Tali criteri sono tuttavia destinati agli utenti e gestibili tramite il portale di classico.

Per usare le funzionalità relative alla conformità dei dispositivi nel portale di Azure, è necessario creare nuovi criteri di conformità dei dispositivi nel portale stesso. Se si assegna un criterio di conformità dei dispositivi nel portale di Azure a un utente al quale è assegnato un criterio di conformità dei dispositivi anche dal portale classico, i criteri di conformità dei dispositivi dal portale di Azure avranno la precedenza rispetto a quelli creati nel portale classico.

## <a name="next-steps"></a>Passaggi successivi

- Creare criteri di conformità dei dispositivi per le piattaforme seguenti:

  - [Android](compliance-policy-create-android.md)
  - [Profilo di lavoro Android](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Per informazioni sulle entità del criterio Data warehouse di Intune, vedere [Informazioni di riferimento per le entità della categoria Policy](reports-ref-policy.md).
