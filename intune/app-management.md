---
title: "Che cos'è la gestione delle app"
titlesuffix: Azure portal
description: Usare questo argomento per apprendere le nozioni fondamentali sulla gestione delle app con Microsoft Intune."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 01/08/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0ea0c9a406d6ddb78cd016a7b594d077d7181952
ms.sourcegitcommit: 12b2111839e648f85374c1c0db4288f08e0ef85d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="what-is-microsoft-intune-app-management"></a>Informazioni sulla gestione delle app in Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Gli amministratori IT hanno la responsabilità di accertarsi che gli utenti finali abbiano accesso alle app di cui hanno bisogno per svolgere il proprio lavoro. Non sempre questo compito risulta semplice da svolgere, perché:
- Esiste una vasta gamma di piattaforme per dispositivi e tipi di applicazione.
- Potrebbe essere necessario gestire le app sia nei dispositivi aziendali che nei dispositivi personali degli utenti.
- Occorre assicurarsi che rete e dati rimangano protetti.

In aggiunta, potrebbe essere necessario assegnare e gestire le app su dispositivi non registrati in Intune.

Intune offre un'ampia gamma di funzionalità che consente di usare le app necessarie nei dispositivi desiderati.

## <a name="app-management-capabilities-by-platform"></a>Funzionalità di gestione delle app per piattaforma

||||||
|-|-|-|-|-|
|&nbsp; |Android|iOS|Windows Phone 8.1|Windows 10|
|Aggiunta e assegnazione delle applicazioni a utenti e dispositivi|Sì|Sì|Sì|Sì|
|Assegnazione delle applicazioni a dispositivi non registrati con Intune|Sì|Sì|No|No|
|Uso dei criteri di configurazione dell'applicazione per controllare il comportamento di avvio delle applicazioni|No|Sì|No|No|
|Uso dei criteri di provisioning delle app per dispositivi mobili per rinnovare app scadute|No|Sì|No|No|
|Protezione dei dati aziendali nelle applicazioni con criteri di protezione delle app|Sì|Sì|No|No<sup>1</sup>|
|Rimozione solo dei dati aziendali da un'applicazione installata (Cancellazione selettiva di app)|Sì|Sì|Sì|Sì|
|Monitoraggio delle assegnazioni di app|Sì|Sì|Sì|Sì|
|Assegnazione e monitoraggio delle app acquistate con Volume Purchase Program da un App Store|No|No|No|Sì|
|Installazione obbligatoria delle applicazioni sui dispositivi (obbligatorio)<sup>2</sup>|Sì|Sì|Sì|Sì|
|Installazione facoltativa di dispositivi dal Portale aziendale (installazione disponibile)|Sì|Sì|Sì|Sì|
|Installazione di combinazione di tasti per un'applicazione sul Web (clip Web)|Sì|Sì|Sì|Sì|
|App interne (line-of-business)|Sì|Sì|No|No|
|App da uno Store|Sì|Sì|Sì|Sì|
|Aggiornare le app|Sì|Sì|Sì|Sì|

<sup>1</sup> Considerare l'uso di [Windows Information Protection](windows-information-protection-configure.md) per proteggere le applicazioni sui dispositivi che eseguono Windows 10.

<sup>2</sup> Si applica solo ai dispositivi gestiti da Intune.

## <a name="how-to-get-started"></a>Come iniziare

Il carico di lavoro **App per dispositivi mobili** contiene numerose informazioni sulle app ed è accessibile come indicato di seguito:

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.

    ![Carico di lavoro App per dispositivi mobili](./media/apps-workload.png)

### <a name="manage"></a>Gestire
- **App**: questo è il nodo in cui la maggior parte delle app viene aggiunta, assegnata e monitorata.
    - [Aggiungere app](apps-add.md)
    - [Assegnare le app](apps-deploy.md)
    - [Monitoraggio le applicazioni](apps-monitor.md)
- **Criteri di configurazione dell'app**: consentono di specificare le impostazioni che potrebbero essere necessarie quando l'utente esegue un'app.
    - [Criteri di configurazione delle app iOS](app-configuration-policies-use-ios.md)
    - [Criteri di configurazione delle app Android](app-configuration-policies-use-android.md)
- **Criteri di protezione delle app**: consentono di associare le impostazioni a un'app per proteggere i dati aziendali da essa usati. Ad esempio, si potrebbero limitare le funzionalità di comunicazione di un'applicazione con altre applicazioni o richiedere all'utente di immettere un PIN per accedere a un'app aziendale.
    - [App protection policies](app-protection-policies.md) (Criteri di protezione delle app)
- **Cancellazione selettiva di app**: consente di rimuovere solo i dati aziendali da un dispositivo utente selezionato.
    - [App selective wipe](apps-selective-wipe.md) (Cancellazione selettiva di app)
- **Profili di provisioning iOS**: le app iOS includono un profilo di provisioning e codice firmato da un certificato. Quando il certificato scade, l'app non può più essere eseguita. Intune offre gli strumenti per assegnare in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza.
    - [Profili di provisioning delle app iOS](app-provisioning-profile-ios.md)

Per altri dettagli, vedere [Manage apps](app-management.md) (Gestire le app).

### <a name="monitor"></a>Monitoraggio
- **Licenze dell'app**: consente di visualizzare, assegnare e monitorare le app acquistate con Volume Purchase Program dagli App Store.
    - [App acquistate con Volume Purchase Program da Microsoft Store per le aziende](windows-store-for-business.md)
- **App individuate**: mostra tutte le app assegnate da Intune e installate in un dispositivo.
- **App Install Status** (Stato installazione app): mostra lo stato di un'assegnazione di un'app creata.
- **Stato protezione app**: mostra lo stato dei criteri di protezione delle app per un utente selezionato.
- **Log di controllo**: mostra le attività correlate alle app di Intune eseguite da tutti gli amministratori IT.

Per altri dettagli, vedere [Eseguire il monitoraggio delle app](apps-monitor.md).

### <a name="setup"></a>Installazione
- **Token VPP iOS**: applicare e visualizzare le licenze Volume Purchase Program (VPP) di iOS.
    - [App iOS acquistate con Volume Purchase Program](vpp-apps-ios.md)
- **Certificato Windows Enterprise**: applicare o visualizzare lo stato di un certificato di firma del codice usato per distribuire le app line-of-business ai dispositivi Windows gestiti. 
- **Certificato Symantec per Windows**: applicare o visualizzare lo stato di un certificato di firma del codice Symantec necessario per distribuire i file appx XAP e WP8.x ai dispositivi Windows 10 Mobile. 
- **Microsoft Store per le aziende**: consente di configurare l'integrazione di Microsoft Store per le aziende. In seguito è possibile sincronizzare le applicazioni acquistate con Intune, assegnarle e monitorare l'uso delle licenze.
    - [App acquistate con Volume Purchase Program da Microsoft Store per le aziende](windows-store-for-business.md)
- **Chiavi di sideload Windows**: è possibile aggiungere una chiave di sideload di Windows che può essere usata per installare un'app direttamente nei dispositivi, anziché pubblicare e scaricare l'app da Windows Store.
    - [Sideload di un'app di Windows](app-sideload-windows.md) 
- **Personalizzazione del portale aziendale**: consente di personalizzare il portale aziendale con il marchio della società.
    - [Company portal configuration](company-portal-app.md) (Configurazione del Portale aziendale)
- **Categorie di app**: aggiungere ed eliminare nomi di categoria di app.
- **Android for Work**: approvare e sincronizzare le app approvate per l'organizzazione.
    - [App Android for Work](apps-add-android-for-work.md) 

### <a name="help-and-support"></a>Guida e supporto tecnico
- **Guida e supporto tecnico**: risolvere i problemi, richiedere supporto o visualizzare lo stato di Intune.
    - [Risoluzione dei problemi](help-desk-operators.md)