---
title: "Criteri di conformità dei dispositivi Intune"
titleSuffix: Intune on Azure
description: "Usare questo argomento per informazioni sulla conformità dei dispositivi in Microsoft Intune\""
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a916fa0d-890d-4efb-941c-7c3c05f8fe7c
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9723e5a8b001068e8b7c9994723e6c7111e7a80d
ms.sourcegitcommit: abd8f9f62751e098f3f16b5b7de7eb006b7510e4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2017
---
# <a name="get-started-with-intune-device-compliance-policies"></a>Introduzione ai criteri conformità dei dispositivi Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="what-is-device-compliance-in-intune"></a>Che cos'è la conformità dei dispositivi in Intune?

I criteri di conformità dei dispositivi Intune definiscono le regole e le impostazioni che un dispositivo deve soddisfare per essere considerato conforme da Intune.

Sono incluse le regole seguenti:

- Uso di una password per l'accesso ai dispositivi

- Crittografia

- Dispositivo non manomesso con jailbreak o root

- Versione minima richiesta del sistema operativo

- Versione massima consentita del sistema operativo

- Dispositivo non al di sopra del livello di Mobile Threat Defense

È anche possibile usare questi criteri per monitorare lo stato di conformità nei dispositivi.

### <a name="device-compliance-requirements"></a>Requisiti di conformità del dispositivo

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

##  <a name="pre-requisites"></a>Prerequisiti

È necessario avere le seguenti sottoscrizioni per usare i criteri di conformità dei dispositivi con Intune:

- Intune EMS

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

Quando un dispositivo viene registrato in Intune, si verifica il processo di registrazione di Azure AD, che aggiorna gli attributi del dispositivo con altre informazioni in Azure AD. Una delle informazioni chiave sul dispositivo è lo stato di conformità del dispositivo, usato dai criteri di accesso condizionale per consentire o bloccare l'accesso alla posta elettronica e altre risorse aziendali.

- Altre informazioni sul [processo di registrazione di Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-device-registration-overview).

##  <a name="ways-to-use-device-compliance-policies"></a>Modi per usare i criteri di conformità del dispositivo

### <a name="with-conditional-access"></a>Con l'accesso condizionale
È possibile usare i criteri di conformità con l'accesso condizionale per consentire l'accesso alla posta elettronica e ad altre risorse aziendali solo ai dispositivi che soddisfano una o più regole dei criteri di conformità.

### <a name="without-conditional-access"></a>Senza l'accesso condizionale
È anche possibile usare i criteri di conformità dei dispositivi indipendentemente dall'accesso condizionale. In tal caso, i dispositivi vengono valutati e segnalati in base allo stato di conformità. Può ad esempio essere utile segnalare quanti dispositivi non sono crittografati o quali dispositivi sono stati manomessi con jailbreak o root. Tuttavia, quando i criteri di conformità vengono usati in modo indipendente, non vengono applicate limitazioni per l'accesso alle risorse aziendali.

I criteri di conformità vengono distribuiti agli utenti. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata sui dispositivi dell’utente. Per informazioni sul tempo necessario ai dispositivi mobili per ottenere un criterio dopo la distribuzione, vedere Gestire impostazioni e funzionalità nei dispositivi.

##  <a name="using-device-compliance-policies-in-the-intune-classic-portal-vs-azure-portal"></a>Uso dei criteri di conformità nel portale di Intune classico e nel Portale di Azure

Si notino le differenze principali per eseguire la transizione al nuovo flusso di lavoro dei criteri di conformità del dispositivo nel portale di Azure.

- Nel portale di Azure i criteri di conformità vengono creati separatamente per ogni piattaforma supportata.
- Nel portale di Intune classico un criterio di conformità è comune a tutte le piattaforme supportate.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

##  <a name="migrate-device-compliance-policies-from-the-intune-classic-portal-to-the-azure-portal"></a>Eseguire la migrazione dei criteri di conformità dei dispositivi dal portale di Intune classico al portale di Azure

I criteri di conformità dei dispositivi creati nel [portale di Intune classico](https://manage.microsoft.com) non verranno visualizzati nel nuovo [portale di Intune di Azure](https://portal.azure.com). Tali criteri saranno tuttavia ancora destinati agli utenti e gestibili tramite il portale di Intune classico.

Per sfruttare le nuove funzionalità correlate alla conformità dei dispositivi nel portale di Azure, sarà necessario creare nuovi criteri di conformità dei dispositivi nel portale stesso. Se si assegna un nuovo criterio di conformità dei dispositivi nel portale di Azure a un utente al quale è stato assegnato un criterio di conformità dei dispositivi anche dal portale di Intune classico, i criteri di conformità dei dispositivi dal portale di Intune di Azure hanno la precedenza rispetto a quelli creati nel portale di Intune classico.

##  <a name="next-steps"></a>Passaggi successivi

Creare criteri di conformità dei dispositivi per le piattaforme seguenti:

- [Android](compliance-policy-create-android.md)
- [Android for work](compliance-policy-create-android-for-work.md)
- [iOS](compliance-policy-create-ios.md)
- [macOS](compliance-policy-create-mac-os.md)
- [Windows](compliance-policy-create-windows.md)
