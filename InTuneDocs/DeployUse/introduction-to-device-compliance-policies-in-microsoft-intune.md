---
title: "Criteri di conformità dei dispositivi | Microsoft Intune"
description: "Questo argomento illustra i concetti necessari per comprendere cosa sono e come funzionano i criteri di conformità del dispositivo."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 550fbbf94f46eee23e77ebf7f9177148882f28e2
ms.openlocfilehash: a853eb4de5528b3ca219ca844a9df4f3b5ad9224


---

# Criteri di conformità dei dispositivi in Microsoft Intune
## Cos'è un criterio di conformità?
Per proteggere i dati aziendali è necessario assicurarsi che i dispositivi usati per accedere alle app e ai dati rispettino alcune regole, come l'uso di un PIN per l'accesso al dispositivo e la crittografia dei dati archiviati nel dispositivo stesso. Un set di regole di questo tipo è detto criterio di conformità.

## Come usare i criteri di conformità
È possibile usare i criteri di conformità con i criteri di accesso condizionale per consentire l'accesso soltanto ai dispositivi che soddisfano le regole dei criteri di conformità per l'accesso alla posta elettronica e ad altri servizi. Per informazioni su come usare insieme i due tipi di criteri, vedere l'articolo [Restrict access to email and O365 services (Limitare l'accesso alla posta elettronica e ai servizi di Office 365)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).

È anche possibile usare i criteri di conformità indipendentemente dall'accesso condizionale. In tal caso i dispositivi vengono valutati e segnalati in base allo stato di conformità. Ad esempio può risultare utile segnalare il numero di dispositivi non crittografati o i dispositivi jailbroken o rooted. Tuttavia, quando i criteri di conformità vengono usati in modo indipendente, non vengono applicate limitazioni per l'accesso alle risorse aziendali.

I criteri di conformità vengono distribuiti agli utenti. Quando un criterio di conformità viene distribuito a un utente, la conformità viene controllata sui dispositivi dell’utente.
Per informazioni sul tempo necessario ai dispositivi mobili per ottenere un criterio dopo la distribuzione, vedere [Gestire impostazioni e funzionalità nei dispositivi](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies).

Nella tabella seguente sono elencati i tipi di dispositivi supportati dai criteri di conformità e il modo in cui le impostazioni di non conformità vengono gestite quando i criteri vengono usati con i criteri di accesso condizionale.

-----------------------------

|Impostazione di criteri| Windows 8.1 e versioni successive| Windows Phone 8.1 e versioni successive| iOS 8.0 e versioni successive|Android 4.0 e versioni successive<br/>Samsung KNOX Standard 4.0 e versioni successive|
|-----|----|----|----|----|
|**Configurazione di PIN o password** |Corretto|Corretto|Corretto|In quarantena|
|**Crittografia dispositivo**|N/D|Corretto|Corretto (impostando il PIN)|In quarantena|
|**Dispositivo jailbroken o rooted**|N/D|N/D|In quarantena (non è un'impostazione)|In quarantena (non è un'impostazione)|
|**Profilo di posta elettronica**|N/D|N/D|In quarantena|N/D|
|**Versione minima del sistema operativo**|In quarantena|In quarantena|In quarantena|In quarantena|
|**Versione massima del sistema operativo**|In quarantena| In quarantena| In quarantena| In quarantena|
|**Attestazione dell'integrità di Windows**|Windows 10 e Windows 10 Mobile vengono messi in quarantena.<br /><br />L'impostazione non è applicabile a Windows 8.1|N/D|N/D|N/D|

------------------------------

**Corretto** = la conformità viene forzata dal sistema operativo del dispositivo (ad esempio, l'utente è obbligato a impostare un PIN).  Non si presenta mai un caso in cui l'impostazione non è conforme.

**In quarantena** = il sistema operativo del dispositivo non forza la conformità (ad esempio, i dispositivi Android non impongono la crittografia del dispositivo all'utente). Quando il dispositivo non è compatibile, vengono eseguite le azioni seguenti:

-   Il dispositivo viene bloccato se l'utente è la destinazione di un criterio di accesso condizionale.

-   Il portale aziendale informa l'utente di eventuali problemi di conformità.

## Passaggi successivi
[Creare criteri di conformità dei dispositivi](create-a-device-compliance-policy-in-microsoft-intune.md)

[Deploy and monitor a device compliance policy (Distribuire e monitorare i criteri di conformità dei dispositivi)](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Vedere anche
[Restrict access to email and O365 services (Limitare l'accesso alla posta elettronica e ai servizi di Office 365)](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)



<!--HONumber=Sep16_HO4-->


