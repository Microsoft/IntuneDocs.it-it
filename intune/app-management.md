---
title: Informazioni sulla gestione delle app in Microsoft Intune
titlesuffix: ''
description: Nozioni fondamentali sulla gestione delle app con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/10/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1975a2dc-3a14-4cb9-9afb-e2ba01a1c51b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 25236453f0440978eda34e3a1a8b1b93daf4c6e1
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025169"
---
# <a name="what-is-microsoft-intune-app-management"></a>Informazioni sulla gestione delle app in Microsoft Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Gli amministratori IT possono usare Microsoft Intune per gestire le app client usate dai dipendenti dell'azienda. Questa funzionalità si aggiunge alla gestione dei dispositivi e alla protezione dei dati. Una delle priorità di un amministratore è fare in modo che gli utenti finali abbiano accesso alle app necessarie per lavorare. Non sempre questo obiettivo risulta semplice da raggiungere, perché:
- Esiste una vasta gamma di piattaforme per dispositivi e tipi di applicazione.
- Potrebbe essere necessario gestire le app sia nei dispositivi aziendali che nei dispositivi personali degli utenti.
- Occorre assicurarsi che rete e dati rimangano protetti.

In aggiunta, potrebbe essere necessario assegnare e gestire le app su dispositivi non registrati in Intune.

Intune offre un'ampia gamma di funzionalità che consente di usare le app necessarie nei dispositivi in cui le si vuole eseguire. Nella tabella seguente è disponibile un riepilogo delle funzionalità di gestione delle app: 

## <a name="app-management-capabilities-by-platform"></a>Funzionalità di gestione delle app per piattaforma

|  | Android | iOS | macOS | Windows 10 | Windows Phone 8.1 |
|-------------------------------------------------------------------------------------|---------|-----|-------|------------|-------------------|
| Aggiunta e assegnazione delle app a utenti e dispositivi | Sì | Sì | Sì | Sì | Sì |
| Assegnazione delle app a dispositivi non registrati con Intune | Sì | Sì | No | No | No |
| Uso dei criteri di configurazione delle app per controllare il comportamento di avvio delle app | No | Sì | No | No | No |
| Uso dei criteri di provisioning delle app per dispositivi mobili per rinnovare app scadute | No | Sì | No | No | No |
| Protezione dei dati aziendali in app con criteri di protezione delle app | Sì | Sì | No | No1 | No |
| Rimozione solo dei dati aziendali da un'app installata (cancellazione selettiva di app) | Sì | Sì | No | Sì | Sì |
| Monitoraggio delle assegnazioni di app | Sì | Sì | Sì | Sì | Sì |
| Assegnazione e monitoraggio delle app acquistate con Volume Purchase Program da un App Store | No | No | No | Sì | No |
| Installazione obbligatoria delle app nei dispositivi (obbligatorio)2 | Sì | Sì | Sì | Sì | Sì |
| Installazione facoltativa nei dispositivi dal Portale aziendale (installazione disponibile) | Sì | Sì | Sì | Sì | Sì |
| Installazione di un collegamento a un'app sul Web (collegamento Web) | Sì | Sì | Sì | Sì | Sì |
| App interne (line-of-business) | Sì | Sì | Sì | Sì | No |
| App da uno Store | Sì | Sì | No | Sì | Sì |
| Aggiornare le app | Sì | Sì | No | Sì | Sì |

<sup>1</sup> Considerare l'uso di [Windows Information Protection](windows-information-protection-configure.md) per proteggere le applicazioni sui dispositivi che eseguono Windows 10.

<sup>2</sup> Si applica solo ai dispositivi gestiti da Intune.

## <a name="get-started"></a>Operazioni preliminari

Il carico di lavoro **App client** contiene numerose informazioni sulle app ed è accessibile seguendo questa procedura:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**.  
    Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Microsoft Intune** selezionare **App client**.

    ![Riquadro del carico di lavoro "App client"](./media/apps-workload.png)

Le quattro sezioni successive descrivono le opzioni disponibili nel riquadro **App client**.

### <a name="manage"></a>Gestire
- **App**: selezionare questa opzione per aggiungere, visualizzare, assegnare e monitorare le app usate dai dipendenti. Per altre informazioni, vedere:
    - [Aggiungere app](apps-add.md).
    - [Assegnare le app](apps-deploy.md).
    - [Monitorare le app](apps-monitor.md).
- **Criteri di configurazione dell'app**: selezionare questa opzione per specificare le impostazioni che potrebbero essere necessarie quando un utente esegue un'app. Per altre informazioni, vedere:
    - [Criteri di configurazione delle app per Intune](app-configuration-policies-overview.md).
        - [Criteri di configurazione delle app iOS](app-configuration-policies-use-ios.md).
        - [Criteri di configurazione delle app Android](app-configuration-policies-use-android.md).
- **Criteri di protezione delle app**: selezionare questa opzione per associare le impostazioni a un'app e proteggere i dati aziendali da essa usati. Ad esempio, si potrebbero limitare le funzionalità di comunicazione di un'applicazione con altre applicazioni o richiedere all'utente di immettere un PIN per accedere a un'app aziendale. Per altre informazioni, vedere:
    - [Criteri di protezione delle app](app-protection-policies.md).
- **Cancellazione selettiva di app**: selezionare questa opzione per rimuovere solo i dati aziendali dal dispositivo di un utente selezionato. Per altre informazioni, vedere:
    - [Cancellazione selettiva di app](apps-selective-wipe.md).
- **Profili di provisioning delle app iOS**: le app iOS includono un profilo di provisioning e codice firmato da un certificato. Quando il certificato scade, l'app non può più essere eseguita. Intune offre gli strumenti per assegnare in modo proattivo un nuovo criterio del profilo di provisioning ai dispositivi con app prossime alla scadenza. Per altre informazioni, vedere:
    - [Profili di provisioning delle app iOS](app-provisioning-profile-ios.md).

Per altre informazioni su questa sezione, vedere [Gestire le app](app-management.md).

### <a name="monitor"></a>Monitoraggio
- **Licenze dell'app**: consente di visualizzare, assegnare e monitorare le app acquistate con Volume Purchase Program dagli App Store. Per altre informazioni, vedere:
    - [App iOS acquistate tramite Volume Purchase Program ](vpp-apps-ios.md).
    - [App acquistate con Volume Purchase Program da Microsoft Store per le aziende](windows-store-for-business.md).
- **App individuate**: visualizza le app assegnate da Intune o installate in un dispositivo. Per altre informazioni, vedere [Visualizzare i dettagli del dispositivo con Microsoft Intune](device-inventory.md).
- **Stato di installazione dell'app**: visualizza lo stato di un'assegnazione di app creata. Per altre informazioni, vedere [Monitorare le informazioni sulle app e le assegnazioni con Microsoft Intune](apps-monitor.md#device-and-user-status-graphs).
- **Stato protezione app**: visualizza lo stato dei criteri di protezione delle app per un utente selezionato.
- **Log di controllo**: visualizza le attività correlate alle app di Intune di tutti gli amministratori IT.

Per altre informazioni su questa sezione, vedere [Monitorare le app](apps-monitor.md).

### <a name="set-up"></a>Imposta
- **Token VPP iOS**: applicare e visualizzare le licenze Volume Purchase Program (VPP) di iOS. Per altre informazioni, vedere:
    - [App iOS acquistate con Volume Purchase Program](vpp-apps-ios.md)
- **Certificato Windows Enterprise**: applicare o visualizzare lo stato di un certificato di firma del codice usato per distribuire le app line-of-business ai dispositivi Windows gestiti.
- **Certificato Symantec per Windows**: applicare o visualizzare lo stato di un certificato di firma del codice Symantec necessario per distribuire i file con estensione appx XAP e WP8.x ai dispositivi Windows 10 Mobile.
- **Microsoft Store per le aziende**: consente di configurare l'integrazione di Microsoft Store per le aziende. In seguito è possibile sincronizzare le applicazioni acquistate con Intune, assegnarle e monitorare l'uso delle licenze. Per altre informazioni, vedere:
    - [App acquistate con Volume Purchase Program da Microsoft Store per le aziende](windows-store-for-business.md).
- **Chiavi di sideload Windows**: aggiungere una chiave di sideload di Windows che può essere usata per installare un'app direttamente nei dispositivi, invece di pubblicare e scaricare l'app da Windows Store. Per altre informazioni, vedere:
    - [Sideload di un'app di Windows](app-sideload-windows.md).
- **Personalizzazione del portale aziendale**: consente di personalizzare il portale aziendale con il marchio della società. Per altre informazioni, vedere:
    - [Configurazione del Portale aziendale](company-portal-app.md).
- **Categorie di app**: aggiungere ed eliminare nomi di categoria di app.
- **Profilo di lavoro Android**: approvare e sincronizzare le app approvate per l'organizzazione. Per altre informazioni, vedere:
    - [App del profilo di lavoro Android](apps-add-android-for-work.md).

### <a name="help-and-support"></a>Guida e supporto tecnico
- **Guida e supporto tecnico**: consente di risolvere i problemi, richiedere supporto o visualizzare lo stato di Intune. Per altre informazioni, vedere:
    - [Risoluzione dei problemi](help-desk-operators.md).

## <a name="next-steps"></a>Passaggi successivi

- [Aggiungere un'app a Microsoft Intune](apps-add.md)
