---
title: Che cosa sono i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: In questo articolo viene descritto come i criteri di protezione delle app di Microsoft Intune consentono di proteggere i dati aziendali ed evitare la perdita di dati.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 01/19/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f59bd4e0f795b73d830e41d47262c10c24d9398b
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31834279"
---
# <a name="what-are-app-protection-policies"></a>Che cosa sono i criteri di protezione delle app?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di protezione delle app di Microsoft Intune consentono di proteggere i dati aziendali ed evitare la perdita di dati.

## <a name="how-you-can-protect-app-data"></a>Protezione dei dati delle app
I dipendenti usano dispositivi mobili per le attività personali e aziendali.  Pur assicurandosi della produttività dei dipendenti, è auspicabile prevenire anche la perdita di dati, sia intenzionale sia non intenzionale.  Inoltre, può essere utile proteggere i dati aziendali accessibili con dispositivi anche nel caso in cui vengano gestiti dall'utente.

Per proteggere i dati aziendali, è possibile usare i criteri di protezione delle app di Intune. Dal momento che i criteri di protezione delle app di Intune possono essere usati **in modo indipendente da qualsiasi soluzione di gestione di dispositivi mobili (MDM)**, è possibile usarli per proteggere i dati aziendali con o senza la registrazione di dispositivi in una soluzione di gestione dei dispositivi. Implementando i **criteri a livello di app** è possibile limitare l'accesso alle risorse aziendali e mantenere i dati all'interno del reparto IT.

I criteri di protezione delle app possono essere configurati per app in esecuzione su dispositivi con le caratteristiche seguenti:

- **Registrati in Microsoft Intune:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dell'azienda.

- **Registrati in una soluzione di gestione di dispositivi mobili di terze parti:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dell'azienda.

  > [!NOTE]
  > I criteri di gestione delle app per dispositivi mobili non devono essere usati con soluzioni di gestione delle app per dispositivi mobili o di contenitore protetto di terze parti.

- **Non registrati in alcuna soluzione di gestione di dispositivi mobili:** i dispositivi appartenenti a questa categoria sono in genere dispositivi di proprietà dei dipendenti non gestiti o registrati in Intune o altre soluzioni MDM.

> [!IMPORTANT]
> È possibile creare criteri di gestione delle app per dispositivi mobili per le app di Office per dispositivi mobili che si connettono ai servizi di Office 365. I criteri di protezione delle app non sono supportati per le app che si connettono ai servizi locali di Exchange o SharePoint.

**I vantaggi più rilevanti dell'uso dei criteri di protezione delle app sono i seguenti:**

-   Proteggere i dati aziendali a livello di app.  Dal momento che la gestione delle app per dispositivi mobili non richiede la gestione dei dispositivi, è possibile proteggere dati aziendali su dispositivi sia gestiti che non gestiti. La gestione dei dati è incentrata sull'identità dell'utente che elimina il requisito della gestione dei dispositivi.

-   La produttività dell'utente finale non è compromessa e i criteri non vengono applicati quando si usa l'app in un contesto personale.  I criteri vengono applicati solo in un contesto aziendale, offrendo così la possibilità di proteggere i dati aziendali senza modificare i dati personali.

L'uso di soluzioni MDM con criteri di protezione delle app comporta vantaggi aggiuntivi e le aziende possono usare contemporaneamente criteri di protezione delle app con o senza soluzioni MDM. Ad esempio, un dipendente può usare un telefono rilasciato dall'azienda oltre a un tablet personale.  In questo caso, il telefono aziendale è registrato in MDM e protetto dai criteri di protezione delle app e il dispositivo personale è protetto solo dai criteri di protezione delle app.

- **MDM verifica che il dispositivo sia protetto**.  Ad esempio, è possibile richiedere un PIN per accedere al dispositivo oppure distribuire le app gestite al dispositivo. È anche possibile distribuire app per dispositivi con la soluzione MDM, per fornire maggiore controllo sulla gestione di app.

- **I criteri di protezione delle app garantiscono che le misure di sicurezza a livello di app siano presenti**. Ad esempio, è possibile richiedere un PIN per aprire un'app in un contesto aziendale, o per condividere i dati tra app o per impedire che i dati dell'app aziendale vengano salvati in un percorso di archiviazione personale.


### <a name="supported-platforms-for-app-protection-polices"></a>Piattaforme supportate per i criteri di protezione delle app
Il supporto della piattaforma dei criteri di protezione delle app di Intune è allineato al supporto della piattaforma delle applicazioni di Office. Per informazioni, vedere [Requisiti di sistema per Office](https://products.office.com/en-US/office-system-requirements).

I dispositivi Windows non sono attualmente supportati. Tuttavia, quando si registrano i dispositivi di Windows 10 con Intune, è possibile usare Windows Information Protection, che offre funzionalità simili. Per altre informazioni, vedere [Proteggere i dati aziendali con Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
##  <a name="how-app-protection-policies-protect-app-data"></a>Come i criteri di protezione delle app proteggono i dati dell'app

####  <a name="apps-without-app-protection-policies"></a>App senza criteri di protezione delle app

![Immagine che mostra lo spostamento dei dati tra le app quando non sono presenti criteri di protezione delle app](./media/apps-without-protection-policies.png)

Quando le app vengono usate senza restrizioni, può crearsi una commistione di dati aziendali e personali.  I dati aziendali potrebbero finire in percorsi come l'archivio personale o essere trasferiti alle app esterne al proprio ambito, causando la perdita di dati. Le frecce nel diagramma indicano lo spostamento senza restrizioni dei dati tra le app (aziendali e personali) e i percorsi di archiviazione.


### <a name="data-protection-with-app-protection-policies"></a>Protezione dei dati con i criteri di protezione delle app

![Immagine che mostra in che modo i dati aziendali vengono protetti tramite l'applicazione di criteri di protezione delle app ](./media/apps-with-protection-policies.png)


È possibile usare i criteri di protezione delle app per impedire il salvataggio dei dati aziendali nell'archiviazione locale del dispositivo e limitare lo spostamento dei dati in altre app non protette dai criteri di protezione delle app. Le impostazioni dei criteri di protezione delle app includono:
- Criteri di rilocazione dei dati, ad esempio **Impedisci Salva con nome** e **Limita le operazioni taglia, copia e incolla**.
- Impostazioni dei criteri di accesso, ad esempio **Richiedi PIN semplice per l'accesso**, **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mdm-solution"></a>Protezione dei dati con criteri di protezione delle app nei dispositivi gestiti da una soluzione MDM

![Immagine che mostra il funzionamento dei criteri di protezione delle app sui dispositivi BYOD](./media/app-protection-policies-with-mdm.png)

**Per i dispositivi registrati in una soluzione MDM**-

L'immagine precedente mostra i livelli di protezione offerti dalla soluzione MDM e dai criteri di protezione delle app.

La soluzione MDM:

-   Registra il dispositivo

-   Distribuisce le app al dispositivo

-   Permette la conformità e la gestione continua del dispositivo

**I criteri di protezione delle app aggiungono valore perché:**

-   Aiutano a proteggere i dati aziendali dalla divulgazione alle app e ai servizi consumer

-   Applicano restrizioni (salvataggio con nome, Appunti, PIN e così via) alle app per dispositivi mobili

-   Cancellano i dati aziendali dalle app senza rimuoverle dal dispositivo


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Protezione dei dati con i criteri di protezione delle app per dispositivi senza registrazione

![Immagine che mostra il funzionamento dei criteri di protezione delle app sui dispositivi gestiti](./media/app-protection-policies-without-mdm.png)

L'immagine precedente illustra il funzionamento dei criteri di protezione dei dati a livello di app senza MDM.

Per i dispositivi BYOD non registrati in alcuna soluzione MDM, i criteri di protezione delle app possono aiutare a proteggere i dati aziendali a livello di app.
Esistono tuttavia alcune limitazioni da tenere in considerazione, ad esempio:

-   Non è possibile distribuire le app al dispositivo.  L'utente finale deve ottenere le app dall'archivio.

-   Non è possibile eseguire il provisioning dei profili certificato in questi dispositivi.

-   Non è possibile eseguire il provisioning delle impostazioni Wi-FI e VPN aziendali in questi dispositivi.


## <a name="multi-identity"></a>Supporto per identità multiple

Le app che supportano identità multiple consentono di usare account differenti, aziendale e personale, per accedere alle stesse app, mentre i criteri di protezione delle app vengono applicati solo quando le app vengono usate nel contesto aziendale.

Ad esempio, quando un utente avvia l'app OneDrive usando il proprio account aziendale, non può spostare i file in un percorso di archiviazione personale. Tuttavia, quando tale utente usa OneDrive con il proprio account personale, può copiare e spostare i dati da OneDrive senza restrizioni.

- Altre informazioni sulle app che supportano [MAM e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

##  <a name="next-steps"></a>Passaggi successivi

[Come creare e distribuire i criteri di protezione delle app con Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Vedere anche
Le app di terze parti, ad esempio l'app per dispositivi mobili Salesforce, interagiscono con Intune in modi specifici per proteggere i dati aziendali. Per altre informazioni sul funzionamento dell'app Salesforce con Intune (incluse le impostazioni di configurazione delle app MDM), vedere [Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) (App Salesforce e Microsoft Intune).
