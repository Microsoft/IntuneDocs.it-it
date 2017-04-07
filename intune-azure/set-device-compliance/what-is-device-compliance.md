---
title: "Conformità del dispositivo"
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: usare questo argomento per informazioni sulla conformità del dispositivo in Microsoft Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: f316b332c3f1b80b9d6af488943298fcfea13741
ms.openlocfilehash: 8cc5e12308871a3b023bed49e9647b888971f849
ms.lasthandoff: 03/30/2017


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>Che cos'è la conformità dei dispositivi nell'anteprima di Intune in Azure?

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

I criteri di conformità dei dispositivi in Intune definiscono le regole e le impostazioni a cui un dispositivo deve adeguarsi per essere considerato conforme in base ai criteri di accesso condizionale di Intune ed EMS. È anche possibile usare questi criteri per monitorare e correggere i problemi di conformità dei dispositivi. 

Sono incluse le regole seguenti:

- Uso di una password per l'accesso ai dispositivi
- Crittografia
- Dispositivo non manomesso con jailbreak o root
- Versione minima richiesta del sistema operativo
- Versione massima consentita del sistema operativo
- Dispositivo non al di sopra del livello di Mobile Threat Defense

<!---##  Concepts
Following are some terms and concepts that are useful to understanding how to use compliance policies.

### Device compliance requirements
Compliance requirements are essentially rules like requiring a device PIN or encryption that you can specify as required or not required for a compliance policy.

### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be non-compliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

##  <a name="how-should-i-use-a-device-compliance-policy"></a>Come usare i criteri di conformità dei dispositivi?

### <a name="using-ems-conditional-access"></a>Con l'accesso condizionale EMS
È possibile usare i criteri di conformità con l'accesso condizionale EMS per consentire l'accesso alla posta elettronica e ad altre risorse aziendali solo ai dispositivi che soddisfano una o più regole dei criteri di conformità.

### <a name="not-using-ems-conditional-access"></a>Senza l'accesso condizionale EMS
È anche possibile usare i criteri di conformità dei dispositivi indipendentemente dall'accesso condizionale EMS.
In tal caso, i dispositivi vengono valutati e segnalati in base allo stato di conformità. Può ad esempio essere utile segnalare quanti dispositivi non sono crittografati o quali dispositivi sono stati manomessi con jailbreak o root. Tuttavia, quando i criteri di conformità vengono usati in modo indipendente, non vengono applicate limitazioni per l'accesso alle risorse aziendali.

I criteri di conformità vengono distribuiti agli utenti. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata sui dispositivi dell’utente. Per informazioni sul tempo necessario ai dispositivi mobili per ottenere un criterio dopo la distribuzione, vedere Gestire impostazioni e funzionalità nei dispositivi.

##  <a name="intune-classic-admin-console-vs-intune-azure-preview-portal"></a>Confronto tra la console di amministrazione classica di Intune e il portale di anteprima di Intune in Azure

Se si è usata la console di amministrazione classica di Intune, è opportuno tenere presenti le differenze seguenti per facilitare la transizione al nuovo flusso di lavoro dei criteri di conformità dei dispositivi nel portale di Azure:

-   Nel portale di Azure i criteri di conformità vengono creati separatamente per ogni piattaforma supportata. Nella console di amministrazione di Intune un criterio di conformità è comune a tutte le piattaforme supportate.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migration-from-intune-classic-console-to-intune-azure-preview-portal"></a>Migrazione dalla console classica di Intune al portale di anteprima di Intune di Azure

I criteri di conformità dei dispositivi creati nella [console classica di Intune](https://manage.microsoft.com) non verranno visualizzati nel nuovo [portale di Intune di Azure](https://portal.azure.com). Tali criteri saranno comunque ancora destinati agli utenti e gestibili tramite la console classica di Intune.

Per sfruttare le nuove funzionalità correlate alle conformità dei dispositivi nel portale di Intune di Azure, sarà necessario creare nuovi criteri di conformità dei dispositivi nel portale stesso. Se si assegna un nuovo criterio di conformità dei dispositivi nel portale di Intune di Azure a un utente, al quale è stato assegnato a un criterio di conformità dei dispositivi anche dal portale classico di Intune, i criteri di conformità dei dispositivi dal portale di Intune di Azure hanno la precedenza rispetto a quelli creati nella console classica di Intune.

##  <a name="next-steps"></a>Passaggi successivi

[Introduzione ai criteri conformità dei dispositivi](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->

