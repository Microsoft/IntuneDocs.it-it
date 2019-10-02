---
title: Criteri di protezione delle app per le estensioni
titleSuffix: Microsoft Intune
description: Questo argomento descrive i criteri di protezione delle app per le estensioni.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f38f22d7aaf03f278fad86061aa8198c8e37f31f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725491"
---
# <a name="protecting-application-extensions"></a>Protezione delle estensioni delle applicazioni

Questo articolo descrive i criteri di protezione delle app per le estensioni in Microsoft Intune.

## <a name="add-ins-for-outlook-app"></a>Componenti aggiuntivi per l'app Outlook

I componenti aggiuntivi di Outlook consentono di integrare app comuni con il client di posta elettronica. I componenti aggiuntivi per Outlook sono disponibili per Outlook per Android e iOS, sul Web e per Windows e Mac. Intune App SDK e i criteri di protezione app di Intune non includono il supporto per la gestione dei componenti aggiuntivi per Outlook, ma esistono altri modi per limitare il loro uso. Poiché i componenti aggiuntivi vengono gestiti tramite Microsoft Exchange, gli utenti saranno in grado di condividere i dati e i messaggi in Outlook e le applicazioni aggiuntive non gestite a meno che i componenti aggiuntivi non vengano disattivati per l'utente dall'istanza di Exchange.

Per impedire agli utenti finali di accedere e installare componenti aggiuntivi di Outlook con effetto su tutti i client Outlook, assicurarsi di applicare le seguenti modifiche ai ruoli nell'interfaccia di amministrazione di Exchange:

- Per impedire agli utenti di installare componenti aggiuntivi di Office Store, rimuovere il ruolo di Marketplace personale.
- Per impedire agli utenti il sideload di componenti aggiuntivi, rimuovere il ruolo di app personalizzate.
- Per impedire agli utenti di installare tutti i componenti aggiuntivi, rimuovere i ruoli di app personalizzate e di Marketplace personale.

Queste istruzioni si applicano a Office 365, Exchange 2016, Exchange 2013 in Outlook sul Web, per dispositivi mobili, Windows e Mac.

- Altre informazioni sui [componenti aggiuntivi per Outlook](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx).
- Altre informazioni su [come specificare gli amministratori e gli utenti che possono installare e gestire i componenti aggiuntivi per l'app Outlook](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx).

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Connessioni all'account LinkedIn per le app Microsoft

Le connessioni all'account LinkedIn consentono agli utenti di visualizzare le informazioni del profilo LinkedIn pubblico all'interno di determinate app Microsoft. Per impostazione predefinita, gli utenti possono scegliere di connettere i propri account LinkedIn e Microsoft aziendale o dell'istituto di istruzione per visualizzare ulteriori informazioni del profilo LinkedIn. 

> [!NOTE]
> L'integrazione di LinkedIn non è attualmente disponibile per i clienti del governo degli Stati Uniti e per le organizzazioni con cassette postali di Exchange Online ospitate in Australia, Canada, Cina, Francia, Germania, India, Corea del Sud, Regno Unito, Giappone e Sudafrica.

Intune SDK e i criteri di protezione delle app di Intune non includono il supporto per la gestione delle connessioni all'account LinkedIn. Esistono tuttavia altri modi per gestirle. È possibile disabilitare le connessioni all'account LinkedIn per l'intera organizzazione, oppure abilitare le connessioni all'account LinkedIn per gruppi di utenti selezionati all'interno dell'organizzazione. Queste impostazioni interessano le connessioni LinkedIn nelle app di Office 365 in tutte le piattaforme (web, dispositivi mobili e desktop). È possibile scegliere le opzioni seguenti:

- Abilitare o disabilitare le connessioni all'account LinkedIn per il tenant nel portale di Azure. 
- Abilitare o disabilitare le connessioni all'account LinkedIn per le app di Office 2016 dell'organizzazione tramite criteri di gruppo.

Se l'integrazione di LinkedIn è abilitata per il tenant, quando gli utenti dell'organizzazione connettono i propri account LinkedIn e Microsoft aziendale o dell'istituto di istruzione, sono disponibili due opzioni: 

- Possono concedere l'autorizzazione di condividere i dati tra i due account. Questo significa che concedono l'autorizzazione all'account LinkedIn di condividere dati con l'account aziendale o dell'istituto di istruzione Microsoft, nonché all'account aziendale o dell'istituto di istruzione Microsoft di condividere dati con l'account LinkedIn. I dati condivisi con LinkedIn lasciano i servizi online. 
- Possono concedere l'autorizzazione di condividere i dati solo dall'account LinkedIn all'account aziendale o dell'istituto di istruzione Microsoft

Se un utente autorizza la condivisione dei dati tra gli account, come accade per i componenti aggiuntivi di Office, l'integrazione LinkedIn utilizza le API Microsoft Graph esistenti. L'integrazione LinkedIn utilizza solo un subset delle API disponibili per i componenti aggiuntivi di Office e supporta varie esclusioni.


|Autorizzazioni per Microsoft Graph  |Descrizione  |
|---------|---------|
|Autorizzazioni di lettura per [Persone](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)     |Consente all'app di leggere un elenco con punteggio delle persone rilevanti per l'utente connesso. L'elenco può includere contatti locali, i contatti dei social network o della directory dell'organizzazione e persone con cui si è comunicato di recente, ad esempio tramite posta elettronica o Skype.         |
|Autorizzazioni di lettura per [Calendari](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)     |Consente all'app di leggere gli eventi nei calendari dell'utente. Include le riunioni nei calendari degli utenti connessi, gli orari, i luoghi e i partecipanti.         |
|Autorizzazioni di lettura per [Profilo utente](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)     |Consente agli utenti di accedere all'app e a quest'ultima di leggere il profilo degli utenti connessi. Consente inoltre all'app di leggere informazioni di base aziendali per gli utenti connessi.         |
|Subscriptions     |Questo ambito non è disponibile e non è ancora in uso. Include le sottoscrizioni alle app e ai servizi Microsoft, ad esempio Office 365, offerte dall'organizzazione dell'utente.         |
|Informazioni dettagliate     |Questo ambito non è disponibile e non è ancora in uso. Include gli interessi associati all'account dell'utente connesso in base al suo utilizzo dei servizi Microsoft.         |

### <a name="learn-more"></a>Altre informazioni

- Altre informazioni su [LinkedIn information and features in your Microsoft apps](https://go.microsoft.com/fwlink/?linkid=850740) (Informazioni e funzionalità di LinkedIn nelle app Microsoft).
- Informazioni sul rilascio delle connessioni all'account LinkedIn nella pagina [Roadmap di Office 365](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc). 
- Informazioni su [Configuring LinkedIn account connections](https://docs.microsoft.com/azure/active-directory/linkedin-integration) (Configurazione delle connessioni all'account LinkedIn).
- Per ulteriori informazioni sui dati condivisi tra l'account LinkedIn e l'account Microsoft aziendale o dell'istituto di istruzione, vedere [LinkedIn in Microsoft applications at your work or school](https://www.linkedin.com/help/linkedin/answer/84077) (LinkedIn nelle app Microsoft aziendali o dell'istituto di istruzione).

