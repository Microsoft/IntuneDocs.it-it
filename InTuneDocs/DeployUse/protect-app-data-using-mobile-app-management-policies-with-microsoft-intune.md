---
title: Proteggere i dati delle app usando i criteri MAM | Microsoft Intune
description: Questo argomento illustra in che modo i criteri di gestione di app mobili consentono di proteggere i dati aziendali, impedire la perdita di dati e mantenere separate le informazioni personali e di lavoro.
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: e751619f6d65e10099d1f8ff5a2342185181af69


---

# Proteggere i dati delle app usando i criteri di gestione delle app mobili con Microsoft Intune

## Protezione dei dati delle app
I dipendenti usano dispositivi mobili per le attività personali e aziendali.  Pur assicurandosi della produttività dei dipendenti, è auspicabile prevenire anche la perdita di dati, sia intenzionale sia non intenzionale.  Inoltre, può essere utile proteggere i dati aziendali accessibili con dispositivi anche nel caso in cui vengano gestiti dall'utente.

Per proteggere i dati aziendali, è possibile usare i criteri di gestione delle app per dispositivi mobili (MAM) di Intune. Dal momento che i criteri MAM di Intune possono essere usati **in modo indipendente da qualsiasi soluzione di gestione di dispositivi mobili (MDM)**, è possibile usarli per proteggere i dati aziendali con o senza la registrazione di dispositivi in una soluzione di gestione dei dispositivi. Implementando i **criteri a livello di app** è possibile limitare l'accesso alle risorse aziendali e mantenere i dati all'interno del reparto IT.

I criteri MAM possono essere configurati per app in esecuzione su dispositivi con le caratteristiche seguenti:

- **Registrati in Microsoft Intune:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dell'azienda.

-   **Registrati in una soluzione di gestione di dispositivi mobili di terze parti:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dell'azienda.

  > [!NOTE]
  > I criteri di gestione delle app per dispositivi mobili non devono essere usati con soluzioni di gestione delle app per dispositivi mobili o di contenitore protetto di terze parti.

-   **Non registrati in alcuna soluzione di gestione di dispositivi mobili:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dei dipendenti non gestiti o registrati in Intune o altre soluzioni MDM.

> [!IMPORTANT]
> È possibile creare criteri di gestione delle app per dispositivi mobili per le app di Office per dispositivi mobili che si connettono ai servizi di Office 365. I criteri MAM non sono supportati per le app che si connettono ai servizi locali di Exchange, Skype for Business o SharePoint.

**I vantaggi più rilevanti dell'uso dei criteri MAM sono i seguenti:**

-   Proteggere i dati aziendali a livello di app.  Dal momento che la gestione delle app per dispositivi mobili non richiede la gestione dei dispositivi, è possibile proteggere dati aziendali su dispositivi sia gestiti che non gestiti. La gestione dei dati è incentrata sull'identità dell'utente che elimina il requisito della gestione dei dispositivi.

-   La produttività dell'utente finale non è compromessa e i criteri non vengono applicati quando si usa l'app in un contesto personale.  I criteri vengono applicati solo in un contesto aziendale, offrendo così la possibilità di proteggere i dati aziendali senza modificare i dati personali.

L'uso di soluzioni MDM con criteri MAM comporta vantaggi aggiuntivi e le aziende possono usarli contemporaneamente con o senza soluzioni MDM. Ad esempio, un dipendente può usare un telefono rilasciato dall'azienda oltre a un tablet personale.  In questo caso, il telefono aziendale è registrato in MDM e protetto dai criteri MAM e il dispositivo personale è protetto solo dai criteri MAM.

- **MDM verifica che il dispositivo sia protetto**.  Ad esempio, è possibile richiedere un PIN per accedere al dispositivo oppure distribuire le app gestite al dispositivo. È anche possibile distribuire app per dispositivi con la soluzione MDM, per fornire maggiore controllo sulla gestione di app.

- **I criteri MAM garantiscono che le misure di sicurezza a livello di app siano presenti**. Ad esempio, è possibile richiedere un PIN per aprire un'app in un contesto aziendale, o per condividere i dati tra app o per impedire che i dati dell'app aziendale vengano salvati in un percorso di archiviazione personale.


### I criteri MAM sono attualmente supportati in:
-   iOS 8.1 o versioni successive

-   Android 4 o versioni successive

I dispositivi Windows non sono attualmente supportati.
##  Protezione dei dati delle app con i criteri MAM

####  App senza criteri MAM:

![Immagine che mostra lo spostamento dei dati tra le app quando non sono presenti criteri MAM](../media/Apps_without_MAM_policies.png)

Quando le app vengono usate senza restrizioni, può crearsi una commistione di dati aziendali e personali.  I dati aziendali potrebbero finire in percorsi come l'archivio personale o essere trasferiti alle app esterne al proprio ambito, causando la perdita di dati. Le frecce nel diagramma indicano lo spostamento senza restrizioni dei dati tra le app (aziendali e personali) e i percorsi di archiviazione.

### Protezione dei dati con i criteri MAM:

![Immagine che mostra come proteggere i dati aziendali quando vengono applicati criteri MAM ](../media/Apps_with_mobile_app_policies.png)

È possibile usare i criteri MAM per impedire il salvataggio dei dati aziendali nell'archiviazione locale del dispositivo e limitare lo spostamento dei dati in altre app non protette dai criteri MAM. Le impostazioni dei criteri MAM includono:
- Criteri di rilocazione dei dati, ad esempio **Impedisci Salva con nome** e **Limita le operazioni taglia, copia e incolla**.
- Impostazioni dei criteri di accesso, ad esempio **Richiedi PIN semplice per l'accesso**, **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**.

### Protezione dei dati con criteri MAM nei dispositivi gestiti da una soluzione MDM:

![Immagine che mostra il funzionamento dei criteri MAM sui dispositivi BYOD](../media/MAM_BYOD_November.png)

**Per i dispositivi registrati in una soluzione MDM**-

L'immagine precedente mostra i livelli di protezione offerti dalla soluzione MDM e dai criteri MAM.

La soluzione MDM:

-   Registra il dispositivo

-   Distribuisce le app al dispositivo

-   Permette la conformità e la gestione continua del dispositivo

**I criteri MAM aggiungono valore perché:**

-   Aiutano a proteggere i dati aziendali dalla divulgazione alle app e ai servizi consumer

-   Applicano restrizioni (salvataggio con nome, Appunti, PIN e così via) alle app per dispositivi mobili

-   Cancellano i dati aziendali dalle app senza rimuoverle dal dispositivo


### Protezione dei dati con i criteri MAM per dispositivi senza registrazione

![Immagine che mostra il funzionamento dei criteri MAM nei dispositivi gestiti](../media/MAM_ManagedDevices_November.png)

L'immagine precedente illustra il funzionamento dei criteri di protezione dei dati a livello di app senza MDM.

Per i dispositivi BYOD non registrati in qualsiasi soluzione MDM, i criteri MAM possono aiutare a proteggere i dati aziendali a livello di app.
Esistono tuttavia alcune limitazioni da tenere in considerazione, ad esempio:

-   Non è possibile distribuire le app al dispositivo.  L'utente finale deve ottenere le app dall'archivio.

-   Non è possibile eseguire il provisioning dei profili certificato in questi dispositivi.

-   Non è possibile eseguire il provisioning delle impostazioni Wi-FI e VPN aziendali in questi dispositivi.


## Supporto per identità multiple

Le app che supportano identità multiple offrono la possibilità di usare account differenti, aziendale e personale, per accedere alle stesse app mentre i criteri MAM vengono applicati quando le app vengono usate nel contesto aziendale.  

Ad esempio, quando l'utente finale avvia l'app OneDrive usando il proprio account aziendale, non può spostare i file in un percorso di archiviazione personale. Tuttavia, quando l'utente finale usa OneDrive con il proprio account personale, può copiare e spostare i dati da OneDrive senza restrizioni.  

Tutte le app di Office per dispositivi mobili supportano più identità.

##  Passaggi successivi
[Preparazione alla configurazione dei criteri di gestione delle app per dispositivi mobili](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

[Creare e distribuire i criteri di gestione delle app per dispositivi mobili con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


