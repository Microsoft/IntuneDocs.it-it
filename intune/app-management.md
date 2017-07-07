---
title: "Che cos'è la gestione delle app"
titleSuffix: Intune on Azure
description: Usare questo argomento per apprendere le nozioni fondamentali sulla gestione delle app con Microsoft Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/16/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 515d4e2b089d077ec708fc1dea1e1747169a60ae
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="what-is-microsoft-intune-app-management"></a>Informazioni sulla gestione delle app in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Gli amministratori IT hanno la responsabilità di accertarsi che gli utenti finali abbiano accesso alle app di cui hanno bisogno per svolgere il proprio lavoro. Non sempre questo compito risulta semplice da svolgere, perché:
- Esiste una vasta gamma di piattaforme per dispositivi e tipi di applicazione.
- Potrebbe essere necessario gestire le app nei dispositivi aziendali e nei dispositivi personali degli utenti.
- Occorre assicurarsi che rete e dati rimangano protetti.

In aggiunta, potrebbe essere necessario assegnare e gestire le applicazioni su dispositivi che non sono registrati con Intune.

Intune offre un'ampia gamma di funzionalità che consente di usare le app necessarie sui dispositivi desiderati.

## <a name="app-management-capabilities-by-platform"></a>Funzionalità di gestione delle app per piattaforma

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|Aggiunta e assegnazione delle applicazioni a utenti e dispositivi|sì|Sì|Sì|sì|
|Assegnazione delle applicazioni a dispositivi non registrati con Intune|sì|Sì|No|No|
|Uso dei criteri di configurazione dell'applicazione per controllare il comportamento di avvio delle applicazioni|No|Sì|No|No|
|Uso dei criteri di provisioning delle app per dispositivi mobili per rinnovare app scadute|No|Sì|No|No|
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

<sup>1</sup> Considerare l'uso di [Windows Information Protection]windows-information-protection-configure.md) per proteggere le app in dispositivi che eseguono Windows 10.

<sup>2</sup> Si applica solo ai dispositivi gestiti da Intune.

## <a name="how-to-get-started"></a>Come iniziare

Il carico di lavoro **App per dispositivi mobili** contiene numerose informazioni sulle app ed è accessibile come indicato di seguito:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.

    ![Carico di lavoro App per dispositivi mobili](./media/apps-workload.png)

### <a name="manage"></a>Gestire
- **App**: questo è il nodo in cui la maggior parte delle app viene aggiunta, assegnata e monitorata.
    - [Aggiungere app](apps-add.md)
    - [Assegnare le app](apps-deploy.md)
    - [Eseguire il monitoraggio delle app](apps-monitor.md)
- **Criteri di configurazione dell'app**: consentono di specificare le impostazioni che potrebbero essere necessarie quando l'utente esegue un'app.
    - [Criteri di configurazione delle app iOS](app-configuration-policies-use-ios.md)
    - [Criteri di configurazione delle app Android](app-configuration-policies-use-android.md)
- **Criteri di protezione delle app**: consentono di associare le impostazioni a un'app per proteggere i dati aziendali da essa usati. Ad esempio, si potrebbero limitare le funzionalità di comunicazione di un'applicazione con altre applicazioni o richiedere all'utente di immettere un PIN per accedere a un'app aziendale.
    - [App protection policies](app-protection-policies.md) (Criteri di protezione delle app)
- **Cancellazione selettiva di app**: consente di rimuovere solo i dati aziendali da un dispositivo utente selezionato.
    - [App selective wipe](apps-selective-wipe.md) (Cancellazione selettiva di app)
- **Profili di provisioning iOS**: le app iOS includono un profilo di provisioning e codice firmato da un certificato. Quando il certificato scade, l'app non può più essere eseguita. Intune offre gli strumenti per assegnare in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza.
    - [Profili di provisioning delle app iOS](app-provisioning-profile-ios.md)

### <a name="monitor"></a>Monitoraggio
- **App con licenza**: consente di visualizzare, assegnare e monitorare le app acquistate con Volume Purchase Program dagli App Store.
    - [Applicazioni acquistate con Volume Purchase Program da Windows Store per le aziende](windows-store-for-business.md)
- **Discovered Apps** (App individuate): mostra tutte le applicazioni assegnate da Intune e installate su un dispositivo.
- **App Install Status** (Stato installazione app): mostra lo stato di un'assegnazione di un'app creata.
- **Stato protezione app**: mostra lo stato dei criteri di protezione delle app per un utente selezionato.

Per informazioni dettagliate, vedere [Eseguire il monitoraggio delle app](apps-monitor.md).

### <a name="setup"></a>Installazione
<!--- **iOS VPP Tokens**
    - [iOS volume-purchased apps](vpp-apps-ios.md) --->
- **Windows Store per le aziende**: consente di configurare l'integrazione di Windows Store per le aziende. In seguito è possibile sincronizzare le applicazioni acquistate con Intune, assegnarle e monitorare l'uso delle licenze.
    - [Applicazioni acquistate con Volume Purchase Program da Windows Store per le aziende](windows-store-for-business.md)
- **Personalizzazione del portale aziendale**: consente di personalizzare il portale aziendale con il marchio della società.
    - [Company portal configuration](company-portal-app.md) (Configurazione del Portale aziendale)
