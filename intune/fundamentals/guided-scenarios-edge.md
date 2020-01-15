---
title: Scenario guidato - Distribuisci Microsoft Edge per dispositivi mobili
titleSuffix: Microsoft Intune
description: Informazioni sullo scenario guidato per distribuire Microsoft Edge per dispositivi mobili dal portale di gestione dei dispositivi per Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 88beb8f4791c127b0a225878f5bc43b6dd9b4025
ms.sourcegitcommit: 637375a390b6e34f9c4415c77b99fe2980bbf554
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75839367"
---
# <a name="guided-scenario---deploy-microsoft-edge-for-mobile"></a>Scenario guidato - Distribuisci Microsoft Edge per dispositivi mobili 

Seguendo questo [scenario guidato](~/fundamentals/guided-scenarios-overview.md) è possibile assegnare l'app Microsoft Edge agli utenti che usano dispositivi iOS o Android all'interno dell'organizzazione. L'assegnazione di questa app consentirà agli utenti di esplorare facilmente il contenuto usando i dispositivi aziendali. 

Microsoft Edge consente agli utenti di evitare la confusione del Web con funzionalità predefinite utili per consolidare, organizzare e gestire il contenuto aziendale. Gli utenti di dispositivi iOS e Android che eseguono l'accesso con gli account aziendali di Azure AD nell'applicazione Microsoft Edge troveranno il browser precaricato con i **Preferiti** aziendali e i filtri dei siti Web definiti dall'amministratore.

> [!NOTE]
> Se agli utenti non è consentita la registrazione di dispositivi iOS o Android, questo scenario non consentirà la registrazione e gli utenti dovranno installare Edge autonomamente.
Le funzionalità aziendali di Microsoft Edge abilitate dai criteri di Intune includono: 

- **Doppia identità**: gli utenti possono aggiungere sia un account aziendale che un account personale per l'esplorazione. Le due identità sono completamente separate, in modo analogo all'architettura e all'esperienza utente di Office 365 e Outlook. Gli amministratori di Intune potranno impostare i criteri desiderati per un'esperienza di esplorazione protetta nell'account aziendale. 
- **Integrazione dei criteri di protezione delle app di Intune**: ora gli amministratori possono applicare i criteri di protezione delle app a Microsoft Edge, tra cui controllare le operazioni Taglia, Copia e Incolla, impedire le acquisizioni di schermata e assicurare che i collegamenti selezionati dagli utenti si aprano solo in altre app gestite.
- **Integrazione con il proxy di applicazione di Azure**: gli amministratori possono controllare l'accesso alle app SaaS e alle app Web, per assicurare che le app basate su browser vengano eseguite solo nel browser Microsoft Edge sicuro, sia che gli utenti finali si connettano dalla rete aziendale o da Internet. 
- **Collegamenti a Preferiti gestiti e alla home page**: per facilitare l'accesso, gli amministratori possono impostare gli URL in modo che vengano visualizzati nei preferiti quando gli utenti finali si trovano nel proprio contesto aziendale. Possono impostare un collegamento alla home page che viene visualizzato come collegamento principale quando un utente aziendale apre una nuova pagina o una nuova scheda in Microsoft Edge.

## <a name="prerequisites"></a>Prerequisiti

- [Impostare l'autorità MDM su Intune](mdm-authority-set.md#set-mdm-authority-to-intune) - L'impostazione dell'autorità di gestione dei dispositivi mobili (MDM) determina la modalità di gestione dei dispositivi. L'amministratore IT deve impostare un'autorità MDM prima che gli utenti possano registrare i dispositivi per la gestione.
- Autorizzazioni necessarie per l'amministratore di Intune:
    - App gestite: Lettura, Creazione, Eliminazione e Assegnazione
    - App per dispositivi mobili: Lettura, Creazione e Assegnazione
    - Set di criteri: Lettura, Creazione e Assegnazione
    - Organizzazione: Lettura e Aggiornamento

## <a name="step-1---introduction"></a>Passaggio 1 - Introduzione

Seguendo lo scenario guidato **Distribuisci Microsoft Edge per dispositivi mobili** sarà possibile configurare una distribuzione di base di Microsoft Edge per un gruppo selezionato di utenti iOS e Android. Questa distribuzione implementerà le funzionalità **doppia identità** e **preferiti gestiti e collegamenti alla pagina iniziale**. Inoltre, nei dispositivi registrati dagli utenti selezionati verrà installata automaticamente l'app Microsoft Edge da Intune. Questa installazione automatica verrà eseguita per tutti i tipi di registrazione definiti dall'utente, che includono: 
- Registrazione iOS tramite l'app Portale aziendale 
- Registrazione dell'affinità utente iOS tramite Apple Business Manager 
- Registrazione Android legacy tramite l'app Portale aziendale 

Questo scenario guidato abiliterà automaticamente la visualizzazione di **MyApps** nei Preferiti di Microsoft Edge e configurerà le stesse informazioni di personalizzazione impostate per l'app Portale aziendale di Intune. 

### <a name="what-you-will-need-to-continue"></a>Cosa serve per continuare
Verranno richiesti i Preferiti aziendali necessari per gli utenti degli utenti e i filtri richiesti per l'esplorazione del Web. Prima di continuare, assicurarsi di completare le attività seguenti:

- Aggiungere gli utenti ai gruppi di Azure AD. Per altre informazioni, vedere [Creare un gruppo di base e aggiungere membri con Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=2102458).
- Registrare i dispositivi iOS e Android in Intune. Per altre informazioni, vedere [Registrazione dei dispositivi](https://go.microsoft.com/fwlink/?linkid=2102547).
- Raccogliere un elenco dei Preferiti aziendali da aggiungere in Microsoft Edge.
- Raccogliere un elenco dei filtri per i siti Web da applicare in Microsoft Edge.

## <a name="step-2---basics"></a>Passaggio 2 - Informazioni di base

In questo passaggio è necessario immettere un nome e una descrizione per i nuovi criteri di Microsoft Edge. È possibile fare riferimento a questi criteri in un secondo momento se è necessario modificare le assegnazioni e le configurazioni. Lo scenario guidato prevede l'aggiunta e l'assegnazione di un'app Microsoft Edge per iOS per i dispositivi iOS e di un'app Microsoft Edge per Android per i dispositivi Android. Questo passaggio creerà anche i criteri di configurazione per queste app.

## <a name="step-3---configuration"></a>Passaggio 3 - Configurazione

In questo passaggio lo scenario guidato configurerà Microsoft Edge per mostrare tutte le altre app assegnate agli utenti tramite Intune e condividerà le stesse informazioni di personalizzazione dell'app Portale aziendale di Microsoft Intune. È possibile configurare ulteriormente Microsoft Edge con un **URL di collegamento alla pagina iniziale**, un elenco di **segnalibri gestiti** e un elenco di **URL bloccati**. L'**URL di collegamento alla pagina iniziale** verrà visualizzato come prima icona sotto la barra di ricerca quando gli utenti aprono una nuova scheda in Microsoft Edge nel loro dispositivo. I **segnalibri gestiti** sono un elenco di URL preferiti per gli utenti disponibili quando usano Microsoft Edge nel contesto aziendale. Gli **URL bloccati** specificano i siti bloccati per gli utenti nel contesto aziendale. Tutti gli altri siti saranno consentiti. 

## <a name="step-4---assignments"></a>Passaggio 4 - Assegnazioni

In questo passaggio è possibile scegliere i gruppi di utenti che si vuole includere per la configurazione di Microsoft Edge per dispositivi mobili per le attività aziendali. Microsoft Edge verrà installato anche in tutti i dispositivi iOS e Android registrati da tali utenti.

## <a name="step-5---review--create"></a>Passaggio 5 - Verifica e creazione

Il passaggio finale consente di esaminare un riepilogo delle impostazioni configurate. Dopo aver verificato le scelte, fare clic su **Crea** per completare lo scenario guidato. 

> [!NOTE]
> Per la ricezione della configurazione, Edge potrebbe richiedere fino a 12 ore. Per altre informazioni, vedere [Criteri di configurazione delle app per Microsoft Intune](~/apps/app-configuration-policies-overview.md).

> [!IMPORTANT]
> Una volta completato lo scenario guidato, verrà visualizzato un riepilogo. È possibile modificare le risorse elencate nel riepilogo in un secondo momento, ma la tabella che visualizza queste risorse non verrà salvata.

## <a name="next-steps"></a>Passaggi successivi

- Migliorare la sicurezza dell'uso di Microsoft Edge configurando l'integrazione dei criteri di protezione delle app di Intune. Per altre informazioni, vedere [Criteri di protezione delle applicazioni per Microsoft Edge ](~/apps/manage-microsoft-edge.md#application-protection-policies-for-microsoft-edge).
- Se è necessario includere siti Intranet esistenti, esplorare la protezione dell'accesso con l'integrazione di Azure Application Proxy. Per altre informazioni, vedere [Configurare le impostazioni di Application Proxy per Microsoft Edge](~/apps/manage-microsoft-edge.md#configure-application-proxy-settings-for-microsoft-edge).

