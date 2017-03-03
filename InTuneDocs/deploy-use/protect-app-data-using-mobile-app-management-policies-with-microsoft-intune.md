---
title: Proteggere i dati delle app usando i criteri di gestione di applicazioni mobili | Documentazione Microsoft
description: Questo argomento illustra in che modo i criteri di gestione di applicazioni mobili consentono di proteggere i dati aziendali, impedire la perdita di dati e mantenere separate le informazioni personali e di lavoro.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab6cd622-b738-4a63-9c91-56044aaafa6d
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: fbb41a8cf6fada76b72213b8cb04fdc0428515e9
ms.openlocfilehash: 651899219458f799e26ed7957ccef97d7ae2af09
ms.lasthandoff: 02/14/2017


---

# <a name="protect-app-data-using-app-protection-policies-with-microsoft-intune"></a>Proteggere i dati delle app usando i criteri di protezione delle app con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="how-you-can-protect-app-data"></a>Protezione dei dati delle app
I dipendenti usano dispositivi mobili per le attività personali e aziendali. Se da una parte è necessario verificare la produttività dei dipendenti, dall'altra è indispensabile prevenire la perdita di dati, sia intenzionale sia non intenzionale.  Può inoltre essere utile proteggere i dati aziendali a cui i dipendenti hanno accesso mediante dispositivi non gestiti direttamente dall'amministratore.

Per proteggere i dati aziendali, è possibile usare i criteri di protezione delle app di Intune. Dal momento che i criteri di protezione delle app di Intune possono essere usati **in modo indipendente da qualsiasi soluzione di gestione di dispositivi mobili (MDM)**, è possibile usare MAM per proteggere i dati aziendali con o senza la registrazione di dispositivi in una soluzione di gestione dei dispositivi. Implementando i **criteri a livello di app** è possibile limitare l'accesso alle risorse aziendali e mantenere i dati all'interno del reparto IT.

È possibile configurare criteri di protezione delle app per app in esecuzione su dispositivi con le caratteristiche seguenti:

-   **Registrati in Microsoft Intune:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dell'azienda.

-   **Registrati in una soluzione di gestione di dispositivi mobili di terze parti:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dell'azienda.

  > [!NOTE]
  > L'uso di criteri di protezione delle app con soluzioni di gestione delle app per dispositivi mobili o di contenitore protetto di terze parti non è consigliato.

-   **Non registrati in alcuna soluzione di gestione di dispositivi mobili:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dei dipendenti non gestiti o registrati in Intune o altre soluzioni MDM.

> [!IMPORTANT]
> È possibile creare criteri di protezione delle app per dispositivi mobili per le app di Office per dispositivi mobili che si connettono ai servizi di Office 365. I criteri di protezione delle app non sono supportati per le app che si connettono ai servizi locali di Exchange, Skype for Business o SharePoint.

## <a name="benefits-of-using-app-protection-policies"></a>Vantaggi dell'uso dei criteri di protezione delle app

-   **Consentono di proteggere i dati aziendali a livello di app.** Dal momento che la gestione delle applicazioni per dispositivi mobili non richiede la gestione dei dispositivi, è possibile proteggere i dati aziendali su dispositivi sia gestiti sia non gestiti. La gestione dei dati è incentrata sull'identità dell'utente che elimina il requisito della gestione dei dispositivi.

-   **La produttività dell'utente non è compromessa e i criteri non vengono applicati quando l'app viene usata in un contesto personale.** I criteri vengono applicati solo in un contesto aziendale, offrendo così la possibilità di proteggere i dati aziendali senza modificare i dati personali.

L'uso di soluzioni MDM con criteri di protezione delle app comporta vantaggi aggiuntivi e le aziende possono usare tali criteri con o senza soluzioni MDM allo stesso tempo. Ad esempio, un dipendente può usare un telefono rilasciato dall'azienda e un tablet personale. In questo caso, il telefono aziendale è registrato in MDM e protetto dai criteri di protezione delle app e il dispositivo personale è protetto solo dai criteri di protezione delle app.

- **MDM verifica che il dispositivo sia protetto.** Ad esempio, è possibile richiedere un PIN per accedere al dispositivo oppure distribuire le app gestite al dispositivo. È anche possibile distribuire app per dispositivi con la soluzione MDM, così da offrire maggiore controllo sulla gestione di app.

- **I criteri di protezione delle app garantiscono che le misure di sicurezza a livello di app siano presenti**. Ad esempio, è possibile impostare un criterio in base a cui viene richiesto un PIN per aprire un'app in un contesto aziendale, viene impedita la condivisione di dati tra app e viene impedito il salvataggio di dati di un'app aziendale in un percorso di archiviazione personale.

## <a name="devices-that-support-mam"></a>Dispositivi che supportano MAM
I criteri di protezione delle app sono attualmente supportati in:
-   iOS 8.1 o versioni successive
-   Android 4 o versioni successive

>[!NOTE]
>I dispositivi Windows non sono supportati nello scenario MAM senza registrazione. Tuttavia, quando si registrano i dispositivi di Windows 10 con Intune, è possibile usare Windows Information Protection, che offre funzionalità simili. Per altre informazioni, vedere [Proteggere i dati aziendali con Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


##  <a name="how-app-protection-policies-protect-app-data"></a>Come i criteri di protezione delle app proteggono i dati dell'app

###  <a name="apps-without-app-protection-policies"></a>App senza criteri di protezione delle app

![Immagine che mostra lo spostamento dei dati tra le app quando non sono presenti criteri di protezione delle app](../media/Apps_without_MAM_policies.png)

Quando si usano le app senza restrizioni, può crearsi una commistione di dati aziendali e personali. I dati aziendali possono finire in percorsi come l'archivio personale o essere trasferiti ad app esterne all'ambito dell'utente, con possibile perdita di dati. Le frecce nel diagramma indicano lo spostamento senza restrizioni dei dati tra le app (aziendali e personali) e i percorsi di archiviazione.

### <a name="data-protection-with-app-protection-policies"></a>Protezione dei dati con i criteri di protezione delle app

![Immagine che mostra in che modo i dati aziendali vengono protetti tramite l'applicazione di criteri di protezione delle app](../media/Apps_with_mobile_app_policies.png)

È possibile usare i criteri di protezione delle app per impedire il salvataggio dei dati aziendali nell'archiviazione locale del dispositivo e limitare lo spostamento dei dati in altre app non protette dai criteri di protezione delle app. Le impostazioni dei criteri di protezione delle app includono:
- Criteri di rilocazione dei dati, ad esempio **Impedisci Salva con nome** e **Limita le operazioni taglia, copia e incolla**.
- Impostazioni dei criteri di accesso, ad esempio **Richiedi PIN semplice per l'accesso** e **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**.

### <a name="data-protection-with-app-protection-on-devices-that-are-managed-by-a-mdm-solution"></a>Protezione dei dati con criteri di protezione delle app nei dispositivi gestiti da una soluzione MDM

![Immagine che mostra il funzionamento dei criteri di protezione delle app sui dispositivi BYOD (Bring Your Own Devices)](../media/MAM_BYOD_November.png)

**Per i dispositivi registrati in una soluzione MDM**: l'immagine precedente mostra i livelli di protezione offerti dalla soluzione MDM e dai criteri di protezione delle app.

La soluzione MDM:

-   Registra il dispositivo.

-   Distribuisce le app al dispositivo.

-   Assicura la conformità e la gestione continua del dispositivo.

**I criteri di protezione delle app aggiungono valore perché:**

-   Aiutano a proteggere i dati aziendali dalla divulgazione alle app e ai servizi consumer.

-   Applicano restrizioni (salvataggio con nome, Appunti, PIN e così via) alle app per dispositivi mobili.

-   Cancellano i dati aziendali dalle app senza rimuoverle dal dispositivo.


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Protezione dei dati con i criteri di protezione delle app per dispositivi senza registrazione

![Immagine che mostra il funzionamento dei criteri di protezione delle app sui dispositivi gestiti](../media/MAM_ManagedDevices_November.png)

L'immagine precedente illustra il funzionamento dei criteri di protezione dei dati a livello di app senza MDM.

Per i dispositivi BYOD non registrati in alcuna soluzione MDM, i criteri di protezione delle app possono aiutare a proteggere i dati aziendali a livello di app.

Esistono tuttavia alcune limitazioni da tenere in considerazione, ad esempio:

-   Non è possibile distribuire le app al dispositivo. L'utente finale deve ottenere le app dallo Store.

-   Non è possibile eseguire il provisioning dei profili certificato in questi dispositivi.

-   Non è possibile specificare le impostazioni Wi-FI e VPN aziendali in questi dispositivi.


## <a name="multi-identity"></a>Supporto per identità multiple

Le app che supportano identità multiple consentono di usare account differenti, aziendale e personale, per accedere alle stesse app, mentre i criteri di protezione delle app vengono applicati solo quando le app vengono usate nel contesto aziendale.  

Ad esempio, quando un utente avvia l'app OneDrive usando il proprio account aziendale, non può spostare i file in un percorso di archiviazione personale. Tuttavia, quando tale utente usa OneDrive con il proprio account personale, può copiare e spostare i dati da OneDrive senza restrizioni.  

Tutte le app di Office per dispositivi mobili supportano l'accesso con più identità.

##  <a name="next-steps"></a>Passaggi successivi
- [Prepararsi alla configurazione dei criteri di protezione delle app](get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune.md)

- [Creare e distribuire i criteri di protezione delle app con Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

