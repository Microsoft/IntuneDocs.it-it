---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601544"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>In fase di sviluppo per Microsoft Intune - Ottobre 2019

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

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>Applicare la modalità scura in iOS Portale aziendale <!-- 4911422  -->
La modalità scura è pianificata per iOS Portale aziendale. Potrai scaricare le app aziendali, gestire i tuoi dispositivi e ottenere supporto IT nella combinazione di colori che preferisci. Per altre informazioni sul Portale aziendale iOS, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](../apps/company-portal-app.md).

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Eseguire app Win32 in dispositivi in modalità Windows 10 S <!-- 3747604  --> 
Sarà possibile installare ed eseguire app Win32 in dispositivi gestiti in modalità Windows 10. Creare uno o più criteri aggiuntivi per la modalità S usando gli strumenti di PowerShell per il controllo delle applicazioni di Windows Defender (WDAC). Usare il portale di firma di Device Guard per firmare i criteri aggiuntivi. Quindi caricare e distribuire i criteri tramite Intune. 

In Intune è possibile trovare questa funzionalità selezionando **app Client**  > **i criteri aggiuntivi di Windows 10**. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>Impostare la disponibilità delle app in base a una data e un'ora <!-- 3510685  -->
In qualità di amministratore, sarà possibile configurare l'ora di inizio e la scadenza di un'app richiesta. All'ora di inizio, l'estensione di gestione di Intune scaricherà il contenuto dell'app e lo memorizza nella cache. L'app verrà installata alla data di scadenza. Per le app disponibili, l'ora di inizio indicherà quando l'app è visibile in Portale aziendale. 

Per impostare la disponibilità delle app in base a data e ora:

1. In Intune selezionare **App client** > **App**. 
1. Selezionare un'app dall'elenco o aggiungerne una nuova selezionando **Aggiungi**. 
1. Nel pannello dell'app selezionare **assegnazioni** > **Aggiungi gruppo**. 
1. Impostare **tipo di assegnazione** su **richiesto** , quindi selezionare **gruppi inclusi**. 
1. Impostare **rendere questa app obbligatoria per tutti gli utenti** su **Sì**. 
1. Selezionare **modifica** per modificare le opzioni relative all' **esperienza utente finale** . 
1. Nel pannello **esperienza utente finale** impostare il **tempo disponibile software** in base alle esigenze. 

Per altre informazioni, vedere [Aggiungere app a Microsoft Intune](../apps/apps-add.md).

### <a name="require-win32-apps-to-restart----3136567----"></a>Richiedi riavvio delle app Win32 <!-- 3136567  -->
Sarà possibile richiedere il riavvio di un'app Win32 dopo una corretta installazione. È possibile scegliere la quantità di tempo (periodo di tolleranza) prima del riavvio.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Visualizzare le notifiche per l'app Portale aziendale in Windows <!-- 1808082  -->
L'app Portale aziendale nei dispositivi Windows verrà aggiornata per visualizzare le notifiche di tipo avviso popup agli utenti, anche quando l'applicazione viene chiusa. L'aggiornamento mostrerà le notifiche per le app disponibili solo quando lo stato dell'installazione è completato o non riuscito. L'app Portale aziendale non visualizzerà le notifiche per le applicazioni obbligatorie.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>Visualizzare i messaggi di stato dell'installazione per l'app Portale aziendale <!-- 2514416  -->
L'app Portale aziendale visualizzerà messaggi di stato di installazione dell'app aggiuntivi per gli utenti finali. Alle nuove funzionalità di dipendenza Win32 verranno applicate le condizioni seguenti:
- Non è stato possibile installare l'app. Le dipendenze definite dall'amministratore non sono state soddisfatte.
- L'app è stata installata correttamente, ma è necessario un riavvio.
- È in corso l'installazione dell'app, ma è necessario riavviare per continuare.

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>Assegnare la versione beta di Microsoft Edge per macOS <!-- 4678761  -->
Sarà possibile aggiungere e assegnare la versione più recente di Microsoft Edge beta a Intune per i dispositivi macOS. 

Per assegnare la versione beta di Microsoft Edge per i dispositivi macOS:
1. In Intune selezionare app **Client** ** >  app**  > **Aggiungi app**  > **Microsoft Edge-MacOS**. 
1. Assegnare la versione beta di Microsoft Edge ai gruppi desiderati. Microsoft AutoUpdate (MAU) mantiene aggiornato Microsoft Edge. 
 
Per altre informazioni su Microsoft Edge, vedere [gestire l'accesso Web tramite Microsoft Edge con Microsoft Intune](../apps/manage-microsoft-edge.md).

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurare il contenuto della notifica dell'app per gli account dell'organizzazione <!-- 2576686 -->
L'APP Intune nei dispositivi Android e iOS consente di controllare il contenuto della notifica dell'app per gli account dell'organizzazione. Questa funzionalità richiede il supporto delle applicazioni e potrebbe non essere disponibile per tutte le applicazioni abilitate per le APP. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Nuovo profilo di interfaccia di configurazione del firmware del dispositivo per i dispositivi che eseguono Windows 10 e versioni successive <!-- 2266073  -->
In Windows 10 e versioni successive è possibile creare un profilo di configurazione del dispositivo per controllare le impostazioni e le funzionalità: 

1. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
1. Per la piattaforma, selezionare **Windows 10 e versioni successive**. 
 
Un nuovo tipo di profilo interfaccia di configurazione firmware del dispositivo consentirà a Intune di gestire le impostazioni del BIOS (UEFI).

Per informazioni sulle impostazioni correnti che è possibile configurare, vedere [applicare le funzionalità e le impostazioni nei dispositivi usando i profili di dispositivo in Microsoft Intune](../configuration/device-profiles.md).

Questa funzionalità si applica a Windows 10 RS5 (1809) e versioni successive in selezionare i dispositivi.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>Registrazione del dispositivo

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>Per i dispositivi iOS, personalizzare la finestra della privacy di registrazione di Portale aziendale <!-- 4394993  -->
Con Markdown è possibile personalizzare la finestra relativa alla privacy del Portale aziendale visualizzata dagli utenti finali durante la registrazione iOS. In particolare, è possibile personalizzare l'elenco degli elementi che l'organizzazione non può visualizzare o eseguire sul dispositivo.

<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Modificare il valore del tag di gruppo per i dispositivi Autopilot<!-- 4816775 -->
Sarà possibile modificare il valore del **tag di gruppo** per i dispositivi Autopilot:

1. Selezionare **Intune**  > **registrazione del dispositivo**  > **registrazione Windows**  > **dispositivi** **Windows Autopilot**  > .
1. Scegliere il dispositivo.
1. Modificare il valore del **tag di gruppo** nel riquadro a destra.
1. Selezionare **Salva**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Gruppi di utenti macOS di destinazione per richiedere la gestione JAMF <!-- 4061739 -->
Sarà possibile indirizzare gruppi di utenti specifici per richiedere che i dispositivi macOS siano gestiti da JAMF. Questa impostazione consente di applicare l'integrazione della conformità JAMF a un subset di dispositivi macOS mentre altri dispositivi continuano a essere gestiti da Intune. Il targeting consente inoltre di eseguire gradualmente la migrazione dei dispositivi degli utenti da un sistema di gestione di dispositivi mobili (MDM) all'altro.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>Distribuire gli aggiornamenti software nei dispositivi macOS <!-- 3194876 -->
Sarà possibile distribuire gli aggiornamenti software a gruppi di dispositivi macOS. Questa funzionalità include l'errore critico, il firmware, il file di configurazione e altri aggiornamenti. È possibile inviare aggiornamenti alla successiva archiviazione del dispositivo. In alternativa, è possibile selezionare una pianificazione settimanale per distribuire gli aggiornamenti in o fuori periodi impostati. 

Questa funzionalità è utile quando si desidera aggiornare i dispositivi al di fuori delle ore di lavoro standard o al di fuori delle ore quando il help desk è completamente personale. Si otterrà anche un report dettagliato di tutti i dispositivi macOS con aggiornamenti distribuiti. È possibile esaminare il report in base al dispositivo per visualizzare lo stato di un particolare aggiornamento.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoraggio e risoluzione dei problemi

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>Report Android nella pagina Panoramica dispositivi <!-- 2984353  -->
Verrà aggiunto un nuovo report alla pagina **Panoramica dispositivi** . Il report Visualizza il numero di dispositivi Android registrati in ogni soluzione di gestione dei dispositivi. Il grafico mostra i conteggi dei dispositivi per il profilo di lavoro, completamente gestito, dedicato e amministratore del dispositivo registrato. 

Per visualizzare il report, scegliere **Intune** > **Devices** > **Overview**.

### <a name="updated-support-experience-------5012398------"></a>Esperienza di supporto aggiornata   <!--  5012398    -->
Nell'ambito dei miglioramenti continui, l'esperienza di supporto nella console per Intune verrà aggiornata.  Verranno migliorati la ricerca e il feedback nella console per i problemi comuni e verrà semplificato il flusso di lavoro per contattare il supporto tecnico.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
