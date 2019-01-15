---
title: Che cosa sono i criteri di protezione delle app
titleSuffix: Microsoft Intune
description: In questo articolo viene descritto come i criteri di protezione delle app di Microsoft Intune consentono di proteggere i dati aziendali ed evitare la perdita di dati.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/11/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: b6ebc3db81b969d83bc22034057ab4217e90931f
ms.sourcegitcommit: e9ba1280b95565a5c5674b825881655d0303e688
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2019
ms.locfileid: "54297282"
---
# <a name="what-are-app-protection-policies"></a>Che cosa sono i criteri di protezione delle app?


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

I criteri di protezione delle app di Microsoft Intune consentono di proteggere i dati aziendali ed evitare la perdita di dati.

## <a name="how-you-can-protect-app-data"></a>Protezione dei dati delle app
I dipendenti usano dispositivi mobili per le attività personali e aziendali. Se da una parte è necessario assicurarsi che i dipendenti possano essere produttivi, dall'altra è indispensabile prevenire la perdita di dati, sia intenzionale sia non intenzionale. È anche opportuno proteggere i dati aziendali a cui si accede da dispositivi non gestiti dall'amministratore.

È possibile usare i criteri di protezione delle app di Intune **in modo indipendente da qualsiasi soluzione di gestione di dispositivi mobili (MDM)**. Questa indipendenza consente di proteggere i dati aziendali con o senza registrazione dei dispositivi in una soluzione di gestione di dispositivi. Implementando i **criteri a livello di app** è possibile limitare l'accesso alle risorse aziendali e mantenere i dati all'interno del reparto IT.

I criteri di protezione delle app possono essere configurati per app in esecuzione su dispositivi con le caratteristiche seguenti:

- **Registrati in Microsoft Intune:** questi dispositivi sono in genere di proprietà aziendale.

- **Registrati in una soluzione di gestione di dispositivi mobili (MDM) di terze parti:** questi dispositivi sono in genere di proprietà aziendale.

  > [!NOTE]
  > I criteri di gestione delle app per dispositivi mobili non devono essere usati con soluzioni di gestione delle app per dispositivi mobili o di contenitore protetto di terze parti.

- **Non registrati in alcuna soluzione di gestione di dispositivi mobili:** questi dispositivi sono in genere dispositivi di proprietà dei dipendenti non gestiti o registrati in Intune o in altre soluzioni MDM.

> [!IMPORTANT]
> È possibile creare criteri di gestione delle app per dispositivi mobili per le app di Office per dispositivi mobili che si connettono ai servizi di Office 365. È anche possibile proteggere l'accesso alle cassette postali locali di Exchange creando i criteri di protezione delle app di Intune per Outlook per iOS e Android abilitati con l'autenticazione moderna ibrida. Prima di usare questa funzionalità, assicurarsi che siano soddisfatti i [requisiti di Outlook per iOS e Android](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx). I criteri di protezione delle app non sono supportati per le altre app che si connettono ai servizi locali di Exchange o SharePoint.

**I vantaggi più rilevanti dell'uso dei criteri di protezione delle app sono i seguenti:**

-   Proteggere i dati aziendali a livello di app. Dal momento che la gestione delle app per dispositivi mobili non richiede la gestione dei dispositivi, è possibile proteggere i dati aziendali su dispositivi sia gestiti sia non gestiti. La gestione dei dati è incentrata sull'identità dell'utente che elimina il requisito della gestione dei dispositivi.

-   Non vi sono effetti sulla produttività degli utenti finali e i criteri non si applicano quando si usa l'app in un contesto personale. I criteri vengono applicati solo in un contesto aziendale, offrendo così la possibilità di proteggere i dati aziendali senza modificare i dati personali.

L'uso di soluzioni MDM con criteri di protezione delle app comporta vantaggi aggiuntivi e le aziende possono usare contemporaneamente criteri di protezione delle app con o senza soluzioni MDM. Si consideri ad esempio un dipendente che usa sia un telefono assegnato dall'azienda che il tablet personale. Il telefono aziendale è registrato in MDM e protetto dai criteri di protezione delle app, mentre il dispositivo personale è protetto solo dai criteri di protezione delle app.

- **MDM verifica che il dispositivo sia protetto**. Ad esempio, è possibile richiedere un PIN per accedere al dispositivo oppure distribuire le app gestite al dispositivo. È anche possibile distribuire app per dispositivi con la soluzione MDM, per fornire maggiore controllo sulla gestione di app.

- **I criteri di protezione delle app garantiscono che le misure di sicurezza a livello di app siano presenti**. Ad esempio, è possibile:
  - Richiedere un PIN per aprire un'app in un contesto aziendale 
  - Controllare la condivisione dei dati tra le app 
  - Impedire il salvataggio dei dati delle app aziendali in un percorso di archiviazione personale


### <a name="supported-platforms-for-app-protection-policies"></a>Piattaforme supportate per i criteri di protezione delle app
Il supporto della piattaforma dei criteri di protezione delle app di Intune è allineato al supporto della piattaforma delle applicazioni per dispositivi mobili di Office per dispositivi Android e iOS. Per informazioni dettagliate, vedere la sezione **App per dispositivi mobili** in [Requisiti di sistema per Office](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg).

I dispositivi Windows non sono attualmente supportati. Tuttavia, è possibile usare Windows Information Protection, che offre funzionalità simili. Per altre informazioni, vedere [Proteggere i dati aziendali con Windows Information Protection (WIP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


## <a name="how-app-protection-policies-protect-app-data"></a>Come i criteri di protezione delle app proteggono i dati dell'app

#### <a name="apps-without-app-protection-policies"></a>App senza criteri di protezione delle app

![Immagine concettuale dello spostamento dati tra app senza criteri attivi](./media/apps-without-protection-policies.png)

Quando le app vengono usate senza restrizioni, può crearsi una commistione di dati aziendali e personali. I dati aziendali possono finire in percorsi come l'archivio personale o essere trasferiti ad app esterne al proprio ambito, causando la perdita di dati. Le frecce nel diagramma precedente indicano lo spostamento senza restrizioni dei dati tra le app sia aziendali che personali e i percorsi di archiviazione.


### <a name="data-protection-with-app-protection-policies"></a>Protezione dei dati con i criteri di protezione delle app

![Immagine concettuale dei dati aziendali protetti da criteri](./media/apps-with-protection-policies.png)


È possibile usare i criteri di protezione delle app per impedire il salvataggio dei dati aziendali nello spazio di archiviazione locale del dispositivo. È anche possibile limitare lo spostamento dei dati ad altre app non protette dai criteri di protezione delle app. Le impostazioni dei criteri di protezione delle app includono:
- Criteri di rilocazione dei dati, ad esempio **Impedisci Salva con nome** e **Limita le operazioni taglia, copia e incolla**.
- Impostazioni dei criteri di accesso, ad esempio **Richiedi PIN semplice per l'accesso** e **Blocca l'esecuzione delle app gestite nei dispositivi jailbroken o rooted**.

### <a name="data-protection-with-app-protection-policies-on-devices-managed-by-a-mobile-device-management-solution"></a>Protezione dei dati con criteri di protezione delle app nei dispositivi gestiti da una soluzione di gestione di dispositivi mobili

![Immagine che mostra il funzionamento dei criteri di protezione delle app sui dispositivi BYOD](./media/app-protection-policies-with-mdm.png)

**Per i dispositivi registrati in una soluzione MDM**-

L'immagine precedente mostra i livelli di protezione offerti insieme da una soluzione MDM e dai criteri di protezione delle app.

La soluzione MDM:

-   Registra il dispositivo

-   Distribuisce le app al dispositivo

-   Permette la conformità e la gestione continua del dispositivo

**I criteri di protezione delle app aggiungono valore perché:**

-   Aiutano a proteggere i dati aziendali dalla divulgazione alle app e ai servizi consumer

-   Applicazione delle restrizioni, ad esempio *Salva con nome*, *Appunti* o *PIN*, alle app client

-   Cancellano i dati aziendali dalle app senza rimuoverle dal dispositivo


### <a name="data-protection-with-app-protection-policies-for-devices-without-enrollment"></a>Protezione dei dati con i criteri di protezione delle app per dispositivi senza registrazione

![Immagine che mostra il funzionamento dei criteri di protezione delle app sui dispositivi gestiti](./media/app-protection-policies-without-mdm.png)

L'immagine precedente illustra il funzionamento dei criteri di protezione dei dati a livello di app senza MDM.

Per i dispositivi BYOD non registrati in alcuna soluzione MDM, i criteri di protezione delle app possono aiutare a proteggere i dati aziendali a livello di app.
Esistono tuttavia alcune limitazioni da tenere in considerazione, ad esempio:

-   Non è possibile distribuire le app al dispositivo. L'utente finale deve ottenere le app dall'archivio.

-   Non è possibile eseguire il provisioning dei profili certificato in questi dispositivi.

-   Non è possibile eseguire il provisioning delle impostazioni Wi-Fi e VPN aziendali in questi dispositivi.

## <a name="app-protection-global-policy"></a>Criteri globali per la protezione delle app

Un amministratore di OneDrive che passa ad **admin.office.com** e seleziona l'accesso **Dispositivo** può impostare i controlli **Gestione di applicazioni mobili** sulle app client di OneDrive e SharePoint. 

Tali impostazioni, rese disponibili nella console di amministrazione di OneDrive, configurano uno speciale criterio di protezione delle app Intune denominato **globale**. Questi criteri globali si applicano a tutti gli utenti del tenant e non è possibile controllarne la destinazione. 

Dopo l'abilitazione, le app OneDrive e SharePoint per iOS e Android vengono protette con le impostazioni selezionate per impostazione predefinita. Un professionista IT può modificare questi criteri nella console di Intune per aggiungere più app di destinazione, oltre che modificare qualsiasi impostazione dei criteri. 

Per impostazione predefinita, può essere presente un solo criterio **globale** per ogni tenant. È comunque possibile usare le [API Graph di Intune](intune-graph-apis.md) per creare criteri globali aggiuntivi per ogni tenant, ma questa operazione non è consigliata. La creazione di criteri globali aggiuntivi non è consigliata perché la risoluzione dei problemi di implementazione di tali criteri può diventare complicata.

Il criterio **globale** si applica a tutti gli utenti del tenant, ma qualsiasi criterio standard di protezione delle app di Intune sostituirà tali impostazioni.


## <a name="multi-identity"></a>Supporto per identità multiple

Le app che supportano identità multiple consentono di usare account differenti (aziendale e personale) per accedere alle stesse app, mentre i criteri di protezione delle app vengono applicati solo quando le app vengono usate nel contesto aziendale.

Per un esempio di contesto personale, si consideri un utente che ha iniziato un nuovo documento di Word. Questo viene considerato di contesto personale e pertanto i criteri di Protezione app di Intune non vengono applicati. Dopo il salvataggio nell'account di OneDrive aziendale, il documento verrà considerato di contesto aziendale e verranno applicati i criteri di Protezione app di Intune.

Per un esempio di contesto aziendale, si consideri ad esempio un utente che avvia l'app OneDrive usando l'account aziendale. Nel contesto di lavoro, non può spostare i file in una posizione di archiviazione personale. Quando in seguito tale utente usa OneDrive con il proprio account personale, può copiare e spostare i dati da OneDrive senza restrizioni.

- Altre informazioni sulle app che supportano [MAM e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

## <a name="next-steps"></a>Passaggi successivi

[Come creare e distribuire i criteri di protezione delle app con Microsoft Intune](app-protection-policies.md)

## <a name="see-also"></a>Vedere anche
Le app di terze parti, ad esempio l'app per dispositivi mobili Salesforce, interagiscono con Intune in modi specifici per proteggere i dati aziendali. Per altre informazioni sul funzionamento dell'app Salesforce con Intune (incluse le impostazioni di configurazione delle app MDM), vedere [Salesforce App and Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) (App Salesforce e Microsoft Intune).
