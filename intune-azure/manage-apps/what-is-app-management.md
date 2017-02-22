---
title: "Che cos&quot;è la gestione delle app? | Anteprima di Intune in Azure | Documentazione Microsoft"
description: 'Anteprima di Intune in Azure: usare questo argomento per apprendere le nozioni fondamentali sulla gestione delle app con Microsoft Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 01/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 424fae862592c1ab5b4221fb5ad40a52c39f6760
ms.openlocfilehash: 33bc87d16834cb2950cc7c66ad4887dddb12e811


---

# <a name="what-is-app-management"></a>Che cos'è la gestione delle app?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]


Il compito degli amministratori IT consiste nell'accertarsi che gli utenti finali abbiano accesso alle app di cui hanno bisogno per svolgere il proprio lavoro. Non sempre questo compito risulta semplice da svolgere, perché:
- Esiste una vasta gamma di piattaforme per dispositivi e tipi di applicazione.
- Potrebbe essere necessario gestire le applicazioni sui dispositivi aziendali e sui dispositivi personali degli utenti.
- Queste operazioni devono essere svolte garantendo che rete e dati rimangano protetti. 

In aggiunta, potrebbe essere necessario assegnare e gestire le applicazioni su dispositivi che non sono registrati con Intune.

Intune offre un'ampia gamma di funzionalità che consente di usare le app necessarie sui dispositivi desiderati.

## <a name="app-management-capabilities-by-platform"></a>Funzionalità di gestione delle app per piattaforma

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|Aggiunta e assegnazione delle applicazioni a utenti e dispositivi|sì|Sì|Sì|sì|
|Assegnazione delle applicazioni a dispositivi non registrati con Intune|sì|Sì|No|No|
|Uso dei criteri di configurazione dell'applicazione per controllare il comportamento di avvio delle applicazioni|No|Sì|No|No|
|Protezione dei dati aziendali nelle applicazioni con criteri di protezione delle app|sì|Sì|No|No<sup>1</sup>|
|Rimozione solo dei dati aziendali da un'applicazione installata (Cancellazione selettiva di app)|sì|Sì|Sì|sì|
|Monitoraggio delle assegnazioni di app|sì|Sì|Sì|sì|
|Assegnazione e monitoraggio delle app acquistate con Volume Purchase Program da un App Store|No|No|No|sì|
|Installazione obbligatoria delle applicazioni sui dispositivi (obbligatorio)<sup>2</sup>|sì|Sì|Sì|sì|
|Installazione facoltativa di dispositivi dal Portale aziendale (installazione disponibile)|sì|Sì|Sì|sì|
|Installazione di combinazione di tasti per un'applicazione sul Web (clip Web)|sì|Sì|Sì|sì|
|App interne (line-of-business)|sì|Sì|No|No|
|App da uno Store|sì|Sì|Sì|sì|
|Aggiornare le app|sì|Sì|Sì|sì|

<sup>1</sup> Considerare l'uso di [Windows Information Protection](/intune-azure/configure-devices/how-to-configure-windows-information-protection) per proteggere le applicazioni sui dispositivi che eseguono Windows 10.

<sup>2</sup> Si applica solo ai dispositivi gestiti da Intune.


## <a name="how-to-get-started"></a>Come iniziare

Il carico di lavoro **App per dispositivi mobili** contiene numerose informazioni sulle app ed è accessibile come indicato di seguito:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.

    ![Carico di lavoro App per dispositivi mobili](./media/apps-workload.png)

### <a name="manage"></a>Gestire
- **App**: questo è il punto in cui la maggior parte delle app verrà aggiunta, assegnata e monitorata. 
    - [Aggiungere app](add-apps.md)
    - [Assegnare le app](deploy-apps.md)
    - [Eseguire il monitoraggio delle app](monitor-apps.md)
- **App con licenza**: consente di visualizzare, distribuire e monitorare le app acquistate con Volume Purchase Program dagli App Store.
    - [Applicazioni acquistate con Volume Purchase Program da Windows Store per le aziende](wsfb-apps.md)
- **Criteri di configurazione dell'app**: consentono di specificare le impostazioni che potrebbero essere necessarie quando l'utente esegue un'app. Per informazioni dettagliate, vedere:
    - [App configuration policies](app-configuration-policies.md) (Criteri di configurazione dell'app)
- **Criteri di protezione delle app**: consentono di associare le impostazioni con un'app per proteggere i dati aziendali da essa usati. Ad esempio, si potrebbero limitare le funzionalità di comunicazione di un'applicazione con altre applicazioni o richiedere all'utente di immettere un PIN per accedere a un'app aziendale.
    - [App protection policies](app-protection-policies.md) (Criteri di protezione delle app)
- **Cancellazione selettiva di app**: consente di rimuovere solo i dati aziendali da un dispositivo utente selezionato.
    - [App selective wipe](app-selective-wipe.md) (Cancellazione selettiva di app)

### <a name="monitor"></a>Monitoraggio
- **Discovered Apps** (App individuate): mostra tutte le applicazioni assegnate da Intune e installate su un dispositivo.
- **App Install Status** (Stato installazione app): mostra lo stato di un'assegnazione di un'app creata.
- **App Protection User Status** (Stato utente per la protezione dell'app): mostra lo stato dei criteri di protezione dell'app per un utente selezionato.

Per informazioni dettagliate, vedere [Eseguire il monitoraggio delle app](monitor-apps.md).

### <a name="setup"></a>Installazione
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](ios-vpp-apps.md) --->
- **Windows Store per le aziende**: consente di configurare l'integrazione di Windows Store per le aziende. Al termine dell'operazione, è possibile sincronizzare le applicazioni acquistate con Intune, assegnarle monitorare l'uso delle licenze. 
    - [Applicazioni acquistate con Volume Purchase Program da Windows Store per le aziende](wsfb-apps.md)
- **Company Portal Branding** (Personalizzazione del portale aziendale): consente di personalizzare il portale aziendale con il marchio della società. 
    - [Company portal configuration](company-portal-app.md) (Configurazione del Portale aziendale)



<!--HONumber=Feb17_HO1-->


