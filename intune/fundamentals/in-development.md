---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d71ae3c15dddedd5d9ebfaf06fcae25af89f6b82
ms.sourcegitcommit: c46b0c2d4507be6a2786a4ea06009b2d5aafef85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2020
ms.locfileid: "76912633"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>In fase di sviluppo per Microsoft Intune - Gennaio 2020

Per supportare gli utenti nella preparazione e pianificazione, questa pagina illustra gli aggiornamenti e le funzionalità dell'interfaccia utente di Intune che sono in fase di sviluppo ma non ancora rilasciati. Oltre alle informazioni contenute in questa pagina: 

- Se sono previste azioni prima di una modifica, verrà pubblicato un post complementare nel Centro messaggi di Office.
- Quando una funzionalità entra in produzione, sia in versione anteprima sia disponibile a livello generale, la descrizione della funzionalità viene spostata da questa pagina alla [pagina delle novità](whats-new.md).
- Questa pagina e la [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere la [roadmap di Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per informazioni sulle sequenze temporali e i risultati finali strategici.

> [!NOTE]
> Questa pagina riflette le attuali aspettative sulle funzionalità di Intune che verranno introdotte in una versione futura. Le date e le singole funzionalità potrebbero cambiare. Questa pagina non descrive tutte le funzionalità in fase di sviluppo.

**Feed RSS**: è possibile sapere quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestione delle app

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Visualizzare le notifiche per l'app Portale aziendale in Windows<!-- 1808082  -->
L'app Portale aziendale nei dispositivi Windows verrà aggiornata in modo da visualizzare le notifiche di tipo avviso popup agli utenti, anche quando l'applicazione è chiusa. L'aggiornamento mostrerà le notifiche per le app disponibili solo quando lo stato dell'installazione è completato o non riuscito. L'app Portale aziendale non mostrerà le notifiche relative alle applicazioni richieste. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visualizzare i messaggi di stato dell'installazione per l'app Portale aziendale<!-- 2514416  -->
L'app Portale aziendale mostrerà i messaggi aggiuntivi sullo stato dell'installazione dell'app per gli utenti finali. Alle nuove funzionalità di dipendenza Win32 verranno applicate le condizioni seguenti:
- Non è stato possibile installare l'app. Le dipendenze definite dall'amministratore non sono state soddisfatte.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>Ridestinare le clip Web a Microsoft Edge nei dispositivi iOS<!-- 5455276 -->
Le clip Web, che fungono da app Web bloccate sui dispositivi iOS, dovranno essere aggiornate. Le clip Web appena distribuite verranno aperte in Microsoft Edge anziché in Intune Managed Browser, se devono essere aperte in un browser protetto. È necessario ridestinare le clip Web preesistenti per assicurarsi che per l'apertura venga usato Microsoft Edge invece di Managed Browser. 


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profili di configurazione della rete cablata per i dispositivi macOS<!-- 3508686  -->
Sarà disponibile un nuovo profilo di configurazione del dispositivo macOS che configura le reti cablate (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **MacOS** per la piattaforma > **Rete cablata** per il tipo di profilo). Usare questa funzionalità per creare profili 802.1x per gestire le reti cablate e distribuire tali reti nei dispositivi macOS.

Si applica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>I profili VPN con connessioni VPN IKEv2 possono usare Always On con i dispositivi iOS <!-- 1947932 idready -->
Nei dispositivi iOS è possibile creare un profilo VPN che usa una connessione IKEv2 (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **VPN** per il tipo di profilo). In un aggiornamento futuro sarà possibile configurare Always On con IKEv2. Quando sono configurati, i profili VPN IKEv2 si connettono automaticamente e rimangono connessi (o si riconnettono rapidamente) alla rete VPN. Rimangono connessi anche quando si passa da una rete a un'altra o si riavviano i dispositivi.

In iOS la VPN Always On è limitata ai profili IKEv2.

Per visualizzare le impostazioni IKEv2 correnti che è possibile configurare, vedere [Aggiungere impostazioni VPN in dispositivi iOS in Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Si applica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Esperienza migliorata dell'interfaccia utente per la creazione dei profili di configurazione nei dispositivi iOS e macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
L'esperienza per la creazione di un profilo per i dispositivi iOS o macOS nell'interfaccia di amministrazione di Endpoint Manager verrà aggiornata. Questa modifica ha effetto sui profili di configurazione dei dispositivi elencati di seguito (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **iOS** o **macOS** per la piattaforma):

- Personalizzato: iOS, macOS
- Funzionalità del dispositivo: iOS, macOS
- Limitazioni del dispositivo: iOS, macOS
- Endpoint Protection: macOS
- Estensioni: macOS
- File delle preferenze: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Esperienza migliorata dell'interfaccia utente per la creazione dei profili di configurazione OEMConfig nei dispositivi Android Enterprise<!-- 5568645 idready  -->
L'esperienza per la creazione o la modifica di un profilo OEMConfig per i dispositivi Android Enterprise nell'interfaccia di amministrazione di Endpoint Manager verrà aggiornata. Nell'esperienza aggiornata sarà disponibile una panoramica di riepilogo delle impostazioni configurate. Questa modifica ha effetto sul profilo di configurazione del dispositivo di OEMConfig (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **Android Enterprise** per la piattaforma > **OEMConfig** per il tipo di profilo).

Questa funzionalità si applica a:
- Android Enterprise 

<!-- ***********************************************-->
<!--## Device enrollment-->



<!-- ***********************************************-->
<!--## Device management-->



<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Modifiche all'interfaccia utente dei ruoli di Intune presto disponibili<!--5801612 idready-->
L'esperienza utente per [Interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Amministrazione del tenant** > **Ruoli** sarà più semplice e intuitiva. La nuova esperienza fornisce le stesse impostazioni e gli stessi dettagli attualmente presenti, ma consentirà di visualizzare e definire i ruoli tramite un processo simile a una procedura guidata.


<!-- ***********************************************-->
## <a name="security"></a>Sicurezza

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Supporto di credenziali derivate nei dispositivi Android COBO<!--4839592-->
Sarà possibile usare credenziali derivate nei dispositivi Android Enterprise completamente gestiti. Verrà incluso il supporto per il recupero di una credenziale derivata per Entrust Datacard, Intercede e DISA Purebred. Sarà possibile usare una credenziale derivata per l'autenticazione di app, Wi-Fi, VPN o la firma S/MIME e/o la crittografia, se supportata dalle app. 

<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


