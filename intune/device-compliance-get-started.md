---
title: "Criteri di conformità dei dispositivi in Microsoft Intune"
titleSuffix: 
description: "Informazioni sulla conformità dei dispositivi in Microsoft Intune"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb3ec168844708d80c83909ab6c58a52ca62e53c
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="get-started-with-microsoft-intune-device-compliance-policies"></a>Introduzione ai criteri di conformità dei dispositivi in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

I criteri di conformità dei dispositivi di Intune definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme da Intune.

Sono incluse le regole seguenti:

- Uso di una password per l'accesso ai dispositivi

- Crittografia

- Dispositivo non manomesso con jailbreak o root

- Versione minima richiesta del sistema operativo

- Versione massima consentita del sistema operativo

- Dispositivo non al di sopra del livello di Mobile Threat Defense

È anche possibile usare questi criteri per monitorare lo stato di conformità nei dispositivi.

## <a name="device-compliance-requirements"></a>Requisiti di conformità del dispositivo

I requisiti di conformità sono essenzialmente regole quali la richiesta di un PIN per il dispositivo o la crittografia che è possibile specificare come obbligatoria o non obbligatoria in base ai criteri di conformità.

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

##  <a name="pre-requisites"></a>Prerequisiti

È necessario avere le seguenti sottoscrizioni per usare i criteri di conformità dei dispositivi con Intune:

- Intune

- Azure AD Premium

###  <a name="supported-platforms"></a>Piattaforme supportate:

-   Android

-   iOS

-   macOS (anteprima)

-   Windows 8.1

-   Windows Phone 8.1

-   Windows 10

> [!IMPORTANT]
> Per segnalare lo stato di conformità, i dispositivi devono essere registrati in Intune.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Funzionamento dei criteri di conformità Intune con Azure AD

Al momento della registrazione in Intune viene avviato il processo di registrazione di Azure AD durante il quale gli attributi del dispositivo vengono aggiornati con altre informazioni in Azure AD. Un'informazione importante è lo stato di conformità del dispositivo che viene usato dai criteri di accesso condizionale per bloccare o consentire l'accesso alla posta elettronica e ad altre risorse aziendali.

- Altre informazioni sul [processo di registrazione di Azure AD](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction).

### <a name="assigning-a-resulting-device-configuration-profile-status"></a>Assegnazione di uno stato del profilo di configurazione del dispositivo risultante

Se a un dispositivo sono stati assegnati più profili di configurazione e il dispositivo presenta stati di conformità diversi per due o più dei profili di configurazione assegnati, sarà necessario assegnare un unico stato di conformità risultante. Questa assegnazione si basa su un livello di gravità concettuale assegnato a ogni stato di conformità. I livelli di gravità di ogni stato di conformità sono i seguenti:


|Stato  |Gravità  |
|---------|---------|
|Pending     |1|
|Operazione completata     |2|
|Operazione non riuscita     |3|
|Errore     |4|

Uno stato risultante di due o più profili di configurazione viene quindi assegnato selezionando il livello di gravità più alto di tutti i profili assegnati a un dispositivo.

Si osservi ad esempio il caso di un dispositivo con tre profili: uno nello stato in sospeso (gravità = 1), uno nello stato completato (gravità = 2) e uno nello stato di errore (gravità = 4). Lo stato di errore ha il livello di gravità più alto e viene quindi assegnato come stato di conformità risultante per tutti e tre i profili.

### <a name="assigning-an-ingraceperiod-status-for-an-assigned-compliance-policy"></a>Assegnazione di uno stato InGracePeriod per un criterio di conformità assegnato

Lo stato InGracePeriod per un criterio di conformità è un valore determinato considerando la combinazione del periodo di tolleranza e dello stato attuale di un dispositivo per il criterio di conformità assegnato. 

In particolare, se un dispositivo presenta uno stato NonCompliant per un criterio di conformità assegnato e:

- al dispositivo non è stato assegnato alcun periodo di tolleranza, il valore assegnato per il criterio di conformità è NonCompliant.
- il dispositivo ha un periodo di tolleranza scaduto, il valore assegnato per il criterio di conformità è NonCompliant.
- il dispositivo ha un periodo di tolleranza futuro, il valore assegnato per il criterio di conformità è InGracePeriod.

Nella tabella seguente sono riepilogati i punti precedenti:


|Stato di conformità attuale|Valore del periodo di tolleranza assegnato|Stato di conformità effettivo|
|---------|---------|---------|
|NonCompliant |Nessun periodo di tolleranza assegnato |NonCompliant |
|NonCompliant |Data trascorsa|NonCompliant|
|NonCompliant |Data futura|InGracePeriod|

Per altre informazioni sul monitoraggio dei criteri di conformità dei dispositivi, vedere [Monitorare i criteri di conformità dei dispositivi di Intune](compliance-policy-monitor.md).

### <a name="assigning-a-resulting-compliance-policy-status"></a>Assegnazione di uno stato dei criteri di conformità risultante

Se a un dispositivo sono stati assegnati più criteri di conformità e il dispositivo presenta stati di conformità diversi per due o più dei criteri di conformità assegnati, sarà necessario assegnare un unico stato di conformità risultante. Questa assegnazione si basa su un livello di gravità concettuale assegnato a ogni stato di conformità. I livelli di gravità di ogni stato di conformità sono i seguenti: 

|Stato  |Gravità  |
|---------|---------|
|Sconosciuto     |1|
|NotApplicable     |2|
|Conforme|3|
|InGracePeriod|4|
|NonCompliant|5|
|Errore|6|

Uno stato risultante di due o più criteri di conformità viene quindi determinato selezionando il livello di gravità più alto di tutti i criteri assegnati a un dispositivo.
 
Si osservi ad esempio il caso di un dispositivo con tre criteri di conformità: uno con stato sconosciuto (gravità = 1), uno con stato conforme (gravità = 3) e uno con stato InGracePeriod (gravità = 4). Lo stato InGracePeriod ha il livello di gravità più alto e viene quindi assegnato come stato di conformità risultante per tutti e tre i profili.  

##  <a name="ways-to-use-device-compliance-policies"></a>Modi per usare i criteri di conformità del dispositivo

### <a name="with-conditional-access"></a>Con l'accesso condizionale
È possibile usare i criteri di conformità con l'accesso condizionale per consentire l'accesso alla posta elettronica e ad altre risorse aziendali solo ai dispositivi che soddisfano una o più regole dei criteri di conformità.

### <a name="without-conditional-access"></a>Senza l'accesso condizionale
È anche possibile usare i criteri di conformità dei dispositivi indipendentemente dall'accesso condizionale. In tal caso, i dispositivi vengono valutati e segnalati in base allo stato di conformità. Può ad esempio essere utile segnalare quanti dispositivi non sono crittografati o quali dispositivi sono stati manomessi con jailbreak o root. Tuttavia, quando i criteri di conformità vengono usati in modo indipendente, non vengono applicate limitazioni per l'accesso alle risorse aziendali.

I criteri di conformità vengono distribuiti agli utenti. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata sui dispositivi dell’utente. Per informazioni sul tempo necessario ai dispositivi mobili per ottenere un criterio dopo la distribuzione, vedere [Risolvere i problemi relativi ai profili di dispositivo in Microsoft Intune](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

#### <a name="actions-for-non-compliance"></a>Azioni per la mancata conformità

Le azioni per la non conformità consentono di configurare una sequenza temporale di azioni da applicare ai dispositivi che non soddisfano i criteri di conformità. Per altre informazioni, vedere [Automatizzare le azioni per la non conformità](actions-for-noncompliance.md).

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Uso dei criteri di conformità nel portale di Intune classico e nel Portale di Azure

Si notino le differenze principali per eseguire la transizione al nuovo flusso di lavoro dei criteri di conformità del dispositivo nel portale di Azure.

- Nel portale di Azure i criteri di conformità vengono creati separatamente per ogni piattaforma supportata.
- Nel portale di Intune classico un criterio di conformità è comune a tutte le piattaforme supportate.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Eseguire la migrazione dei criteri di conformità dei dispositivi dal portale di Intune classico al portale di Azure

I criteri di conformità dei dispositivi creati nel [portale di Intune classico](https://manage.microsoft.com) non sono visualizzati nel nuovo [portale di Intune di Azure](https://portal.azure.com). Tali criteri saranno tuttavia ancora destinati agli utenti e gestibili tramite il portale di Intune classico.

Per sfruttare le nuove funzionalità correlate alla conformità dei dispositivi nel portale di Azure, sarà necessario creare nuovi criteri di conformità dei dispositivi nel portale stesso. Se si assegna un nuovo criterio di conformità dei dispositivi nel portale di Azure a un utente al quale è stato assegnato un criterio di conformità dei dispositivi anche dal portale di Intune classico, i criteri di conformità dei dispositivi dal portale di Intune di Azure hanno la precedenza rispetto a quelli creati nel portale di Intune classico.

##  <a name="next-steps"></a>Passaggi successivi

- Creare criteri di conformità dei dispositivi per le piattaforme seguenti:

   - [Android](compliance-policy-create-android.md)
   - [Android for Work](compliance-policy-create-android-for-work.md)
   - [iOS](compliance-policy-create-ios.md)
   - [macOS](compliance-policy-create-mac-os.md)
   - [Windows](compliance-policy-create-windows.md)

- Per informazioni sulle entità del criterio Data warehouse di Intune, vedere [Informazioni di riferimento per le entità della categoria Policy](reports-ref-policy.md).
