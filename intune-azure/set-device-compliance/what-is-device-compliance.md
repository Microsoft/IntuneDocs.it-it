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
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: b245dac28f88e7eab70dfa9d759b15e155f8a7df


---

# <a name="what-is-device-compliance-in-intune-azure-preview"></a>Che cos'è la conformità del dispositivo nell'anteprima di Intune in Azure?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Per proteggere i dati aziendali, è necessario assicurarsi che i dispositivi usati per accedere alle app e ai dati aziendali rispettino alcune regole, come l'uso di un PIN per l'accesso ai dispositivi e la crittografia dei dati archiviati nei dispositivi. Un set di regole di questo tipo è definito **criteri di conformità**.

##  <a name="how-should-i-use-a-device-compliance-policy"></a>Come usare i criteri di conformità del dispositivo?
È possibile usare i criteri di conformità con l'accesso condizionale per consentire l'accesso soltanto ai dispositivi che soddisfano le regole dei criteri di conformità per l'accesso alla posta elettronica e ad altri servizi.

È anche possibile usare i criteri di conformità indipendentemente dall'accesso condizionale.
In tal caso, i dispositivi vengono valutati e segnalati in base allo stato di conformità. Ad esempio può risultare utile segnalare il numero di dispositivi non crittografati o i dispositivi jailbroken o rooted. Tuttavia, quando i criteri di conformità vengono usati in modo indipendente, non vengono applicate limitazioni per l'accesso alle risorse aziendali.

I criteri di conformità vengono distribuiti agli utenti. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata sui dispositivi dell’utente. Per informazioni sul tempo necessario ai dispositivi mobili per ottenere un criterio dopo la distribuzione, vedere Gestire impostazioni e funzionalità nei dispositivi.

##  <a name="concepts"></a>Concetti
Di seguito sono riportati alcuni termini e concetti utili per comprendere come usare i criteri di conformità.

### <a name="compliance-requirements"></a>Requisiti di conformità
I requisiti di conformità sono essenzialmente regole quali la richiesta di un PIN per il dispositivo o la crittografia che è possibile specificare come obbligatoria o non obbligatoria in base ai criteri di conformità.

<!---### Actions for noncompliance

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

##  <a name="differences-between-the-classic-intune-admin-console-and-intune-in-the-azure-portal"></a>Differenze tra la console di amministrazione di Intune classica e Intune nel portale di Azure


Se in precedenza si è usata la console di amministrazione di Intune classica, è opportuno tenere presente le differenze seguenti per la transizione al nuovo flusso di lavoro per la conformità dei dispositivi nel portale di Azure:


-   Nel portale di Azure i criteri di conformità vengono creati separatamente per ogni piattaforma supportata. Nella console di amministrazione di Intune un criterio di conformità è comune a tutte le piattaforme supportate.


<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="next-steps"></a>Passaggi successivi

[Introduzione ai criteri di conformità](get-started-with-device-compliance.md)


<!---### See also

Conditional access--->



<!--HONumber=Feb17_HO3-->


