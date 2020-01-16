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
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827820"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>In fase di sviluppo per Microsoft Intune - Gennaio 2020

Per supportare gli utenti nella preparazione e pianificazione, questa pagina illustra gli aggiornamenti e le funzionalità dell'interfaccia utente di Intune che sono in fase di sviluppo ma non ancora rilasciati. Oltre alle informazioni contenute in questa pagina: 

- Se sono previste azioni prima di una modifica, verrà pubblicato un post complementare nel Centro messaggi di Office.
- Quando una funzionalità entra in produzione, se si tratta di un'anteprima o disponibile a livello generale, la descrizione della funzionalità verrà spostata da questa pagina alle [novità](whats-new.md).
- Questa pagina e la [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere la [roadmap di Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per informazioni sulle sequenze temporali e i risultati finali strategici.

> [!NOTE]
> Questa pagina riflette le attuali aspettative sulle funzionalità di Intune in una versione futura. Le date e le singole funzionalità potrebbero cambiare. Questa pagina non descrive tutte le funzionalità in fase di sviluppo.

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
L'app Portale aziendale nei dispositivi Windows verrà aggiornata per visualizzare le notifiche di tipo avviso popup agli utenti, anche quando l'applicazione viene chiusa. L'aggiornamento mostrerà le notifiche per le app disponibili solo quando lo stato dell'installazione è completato o non riuscito. L'app Portale aziendale non visualizzerà le notifiche per le applicazioni obbligatorie. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visualizzare i messaggi di stato dell'installazione per l'app Portale aziendale<!-- 2514416  -->
L'app Portale aziendale visualizzerà messaggi di stato di installazione dell'app aggiuntivi per gli utenti finali. Alle nuove funzionalità di dipendenza Win32 verranno applicate le condizioni seguenti:
- Non è stato possibile installare l'app. Le dipendenze definite dall'amministratore non sono state soddisfatte.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>Ridestinare le clip web a Microsoft Edge nei dispositivi iOS<!-- 5455276 idready -->
Le clip web, che fungono da app Web bloccate sui dispositivi iOS, dovranno essere aggiornate. Le clip web appena distribuite vengono aperte in Microsoft Edge invece che nel Intune Managed Browser se necessario per l'apertura in un browser protetto. È necessario ridestinare i clip web preesistenti per assicurarsi che vengano aperti in Microsoft Edge invece che nel Managed Browser. 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>Modifica dell'esperienza utente durante l'aggiunta di app a Intune<!-- 4705829 idready -->
Quando si aggiungono app tramite Intune, viene visualizzata una nuova esperienza utente. Questa esperienza fornisce le stesse impostazioni e i dettagli usati in precedenza, tuttavia la nuova esperienza segue un processo simile a una procedura guidata prima di aggiungere un'app a Intune. Questa nuova esperienza fornisce anche una pagina di revisione prima di aggiungere l'app. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **App** > **Tutte le app** > **Aggiungi**. Per altre informazioni, vedere [Aggiungere app a Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----3136567--"></a>Richiedi riavvio delle app Win32 <!-- 3136567-->
È possibile richiedere che un'app Win32 venga riavviata dopo una corretta installazione. Inoltre, è possibile scegliere la quantità di tempo (periodo di tolleranza) prima che il riavvio debba essere eseguito.

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Aggiungere le impostazioni proxy automatiche ai profili Wi-Fi per i profili di lavoro Android Enterprise<!-- 4490822 idready -->
Nei dispositivi del profilo di lavoro Android Enterprise è possibile creare profili Wi-Fi. Quando si sceglie il tipo di organizzazione Wi-Fi, è anche possibile immettere il tipo EAP (Extensible Authentication Protocol) usato nella rete Wi-Fi.

In un aggiornamento futuro, quando si sceglie il tipo Enterprise, sarà possibile immettere le impostazioni automatiche del proxy, incluso un URL del server proxy, ad esempio `proxy.contoso.com`.

Per visualizzare le impostazioni Wi-Fi correnti che è possibile configurare, vedere [aggiungere impostazioni Wi-Fi per i dispositivi che eseguono Android Enterprise e Android Kiosk in Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Si applica a:
- Profilo di lavoro di Android Enterprise

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profili di configurazione dei dispositivi di rete cablata per i dispositivi macOS<!-- 3508686  -->
Sarà disponibile un nuovo profilo di configurazione del dispositivo macOS che configura le reti cablate (**configurazione del dispositivo** > **profili** > **creare un profilo** > **MacOS** per la piattaforma > **rete cablata** per il tipo di profilo). Usare questa funzionalità per creare profili 802.1 x per gestire le reti cablate e distribuire le reti cablate nei dispositivi macOS.

Si applica a:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>I profili VPN con connessioni VPN IKEv2 possono usare always on con i dispositivi iOS <!-- 1947932 idready -->
Nei dispositivi iOS è possibile creare un profilo VPN che usa una connessione IKEv2 (**configurazione del dispositivo** > **profili** > **creare un profilo** > **iOS/ipados** per la piattaforma > **VPN** per il tipo di profilo). In un aggiornamento futuro è possibile configurare always on con IKEv2. Quando la configurazione è configurata, i profili VPN IKEv2 si connettono automaticamente e si riconnettono alla VPN. Rimane connesso anche quando si passa da una rete a un'altra o si riavviano i dispositivi.

In iOS la VPN always on è limitata ai profili IKEv2.

Per visualizzare le impostazioni IKEv2 correnti che è possibile configurare, vedere [Aggiungere impostazioni VPN in dispositivi iOS in Microsoft Intune](../configuration/vpn-settings-ios.md#ikev2-settings).

Si applica a:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>Esperienza migliorata dell'interfaccia utente durante la creazione di profili di configurazione nei dispositivi iOS e macOS<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
Quando si crea un profilo per dispositivi iOS o macOS, l'esperienza nell'interfaccia di amministrazione di Gestione endpoint verrà aggiornata. Questa modifica ha effetto sui seguenti profili di configurazione dei**dispositivi (dispositivi** > **profili di configurazione** > **creare un profilo** > **iOS** o **MacOS** per la piattaforma):

- Personalizzata: iOS, macOS
- Funzionalità del dispositivo: iOS, macOS
- Restrizioni del dispositivo: iOS, macOS
- Endpoint Protection: macOS
- Estensioni: macOS
- File di preferenza: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Esperienza migliorata dell'interfaccia utente durante la creazione di profili di configurazione OEMConfig nei dispositivi Android Enterprise<!-- 5568645 idready  -->
Quando si crea o si modifica un profilo OEMConfig per i dispositivi Android Enterprise, viene aggiornata l'esperienza nell'interfaccia di amministrazione di Gestione endpoint. L'esperienza aggiornata fornirà un riepilogo delle impostazioni configurate a colpo d'occhio. Questa modifica ha un effetto sul profilo di configurazione del dispositivo OEMConfig (**dispositivi** > **profili di configurazione** > **creare un profilo** > **Android Enterprise** per la piattaforma > **OEMConfig** per il tipo di profilo).

Questa funzionalità si applica a:
- Android Enterprise 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Registrazione del dispositivo

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>Blocca le registrazioni Android per produttore dispositivo<!--5197392 idready-->
Sarà possibile impedire la registrazione dei dispositivi in base al produttore del dispositivo. Questo vale per i dispositivi Android Device Administrator e Android Enterprise work profile. Per visualizzare le restrizioni di registrazione, passare all'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)> **dispositivi** > **restrizioni di registrazione**.



<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi


### <a name="new-information-in-device-details---4471759-5604099----"></a>Nuove informazioni nei dettagli del dispositivo<!-- 4471759 5604099  -->
Le informazioni seguenti verranno aggiunte alla pagina **Panoramica** per i dispositivi:
- Capacità di memoria (quantità di memoria fisica nel dispositivo)
- Capacità di archiviazione (quantità di spazio di archiviazione fisica nel dispositivo) 
- Tipo e velocità del processore CPU
- Dati RAM e processore

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>Nuovo gestore sicurezza endpoint ruolo predefinito di Intune<!--4253397 idready-->
Sarà disponibile un nuovo ruolo predefinito di Intune, ovvero Endpoint Security Manager. Questo nuovo ruolo offre agli amministratori l'accesso completo al nodo di Gestione endpoint in Intune e l'accesso in sola attesa ad altre aree. Il ruolo è un'espansione del ruolo "amministratore della sicurezza" da Azure AD. Se al momento si dispone solo di amministratori globali come ruoli, non sono necessarie modifiche. Se si utilizzano i ruoli e si desidera la granularità fornita da endpoint Security Manager, assegnare tale ruolo quando è disponibile. Per altre informazioni sui ruoli predefiniti, vedere controllo degli [accessi in base al ruolo](role-based-access-control.md).

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Modifiche all'interfaccia utente dei ruoli di Intune in arrivo<!--5801612 idready-->
L'interfaccia utente per l'interfaccia di amministrazione di [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Amministrazione tenant** > i **ruoli** verranno modificati in una progettazione più semplice e intuitiva. Questa esperienza fornisce le stesse impostazioni e i dettagli usati ora, tuttavia la nuova esperienza impiega un processo simile a una procedura guidata.


<!-- ***********************************************-->
## <a name="security"></a>Sicurezza

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Supporto delle credenziali derivate nei dispositivi Android COBO<!--4839592-->
Sarà possibile usare le credenziali derivate in dispositivi Android Enterprise completamente gestiti. Verrà incluso il supporto per il recupero di una credenziale derivata per Entrust Datacard, intercedi e DISA purosangue. Potrai usare le credenziali derivate per l'autenticazione di app, Wi-Fi, VPN o la firma S/MIME e/o la crittografia con le app che la supportano. 

<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


