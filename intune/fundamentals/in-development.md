---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182935"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>In fase di sviluppo per Microsoft Intune - Novembre 2019

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Supporto di S/MIME per Microsoft Outlook Mobile <!-- 2669398  -->
Intune supporterà la distribuzione di certificati S/MIME per la firma e la crittografia che possono essere usati con Outlook Mobile in iOS e Android. Per informazioni correlate, vedere [impostazioni di posta elettronica per i dispositivi iOS](~/configuration/email-settings-ios.md) e [le impostazioni di posta elettronica per i dispositivi Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>Supporto delle impostazioni personalizzate per le applicazioni macOS <!-- 4736278  -->
Intune supporterà le impostazioni personalizzate, consentendo di aggiungere chiavi e valori specifici a un file di elenco delle proprietà delle preferenze (con estensione plist) esistente per configurare le app macOS e il dispositivo. Non tutte le app supportano le preferenze gestite e in alcuni casi è possibile gestire solo impostazioni specifiche. Le impostazioni vengono distribuite solo tramite il canale del dispositivo. È consigliabile caricare solo file di elenco delle proprietà o file XML destinati alle impostazioni del canale del dispositivo.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Valore del tipo di assegnazione in Windows Portale aziendale <!-- 5459950  -->
Verrà aggiornata la pagina **app installate** dell'app Windows portale aziendale. La colonna **tipo di assegnazione** della pagina **app installate** è stata aggiornata per essere chiamata "richiesta dall'organizzazione". I valori possibili sono **Yes** o **No** per designare le app richieste e disponibili. Questa modifica viene apportata in risposta a una confusione dell'utente finale. Per altre informazioni sul portale aziendale Windows, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurare il contenuto della notifica dell'app per gli account dell'organizzazione <!-- 2576686 -->
L'APP Intune nei dispositivi Android e iOS consente di controllare il contenuto della notifica dell'app per gli account dell'organizzazione. Questa funzionalità richiede il supporto delle applicazioni e potrebbe non essere disponibile per tutte le applicazioni abilitate per le APP. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md)


<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Usare i certificati PKCS con profili Wi-Fi in dispositivi Windows 10 e versioni successive <!-- 3246388  -->
Attualmente, è possibile autenticare i profili Wi-Fi di Windows con certificati SCEP (**Configurazione dispositivo** > **profili** > **creare un profilo** > **Windows 10 e versioni successive** per la piattaforma > **Wi-Fi** per tipo di profilo > tipo di > **EAP** **aziendale** ). Sarà possibile usare i certificati PKCS con i profili Wi-Fi di Windows. Questa funzionalità consente agli utenti di autenticare i profili Wi-Fi usando profili certificato PKCS nuovi o esistenti nel tenant. 

Per altre informazioni sui profili Wi-Fi, vedere [aggiungere impostazioni Wi-Fi per i dispositivi Windows 10 e versioni successive in Intune](../configuration/wi-fi-settings-windows.md).

Si applica a:
- Windows 10 e versioni successive

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>Nuove impostazioni di ExchangeActiveSync durante la creazione di un profilo di configurazione del dispositivo di posta elettronica nei dispositivi iOS <!-- 4892824  --> 
Nei dispositivi iOS/iPados è possibile configurare la connettività della posta elettronica in un profilo di configurazione del dispositivo (**configurazione del dispositivo** > **profili** > **creare un profilo** > **iOS/Ipados** per la piattaforma > **posta elettronica** per il tipo di profilo). 

Saranno disponibili nuove impostazioni ExchangeActiveSync, tra cui:
- Scegliere i servizi da sincronizzare o bloccare la sincronizzazione, ad esempio posta elettronica, calendario e contatti.
- Consente o blocca gli utenti di modificare le impostazioni di sincronizzazione per questi servizi nei dispositivi. 

Per visualizzare le impostazioni correnti, passare a [impostazioni del profilo di posta elettronica per i dispositivi iOS in Intune](../configuration/email-settings-ios.md).

Si applica a:
- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>Impedisci agli utenti di aggiungere account Google personali a dispositivi Android Enterprise Owner e Dedicated Device <!-- 5353228  -->
Potrai impedire agli utenti di creare account Google personali in dispositivi Android Enterprise Owner e Dedicated Devices (**Device configuration** > **profiles** > **create profile** > **Android Enterprise** per la piattaforma > **proprietario del dispositivo > solo le restrizioni del dispositivo** per il tipo di profilo > **Impostazioni utenti e account**).

Per visualizzare le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:
- Proprietario del dispositivo Android Enterprise
- Dispositivi dedicati Android Enterprise

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>La registrazione lato server per l'impostazione dei comandi Siri è stata rimossa nel profilo restrizioni dispositivo iOS <!-- 5468501  -->
Nei dispositivi iOS è possibile creare un profilo di restrizioni del dispositivo che configura la registrazione lato server per i comandi Siri **(configurazione del dispositivo** > **profili** > **creare il profilo** > **iOS/ipados** per la piattaforma > **Restrizioni del dispositivo** per il tipo di profilo > **app predefinite**). L'impostazione **registrazione lato server per i comandi Siri** verrà rimossa.

Questa impostazione verrà rimossa dalla console di amministrazione di Intune. Questa impostazione non ha alcun effetto sul dispositivo anche se i criteri esistenti con questa impostazione configurata continueranno a mostrare l'impostazione. Se si vuole rimuovere l'impostazione dai criteri esistenti, passare al criterio, apportare una modifica secondaria, salvarla e il criterio verrà aggiornato.

Per visualizzare le impostazioni configurabili, vedere [Impostazioni dei dispositivi iOS e iPadOS per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Modificare il valore del nome dispositivo per i dispositivi Autopilot<!-- 2640074  -->
Sarà possibile modificare il valore del nome dispositivo per Azure AD dispositivi Autopilot aggiunti. A tale scopo, passare a **Intune** > **registrazione del dispositivo** > **registrazione Windows** > **dispositivi** **Windows Autopilot** > > scegliere il dispositivo > modificare il valore del **nome del dispositivo** nel riquadro di destra > **Salva**.


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Modificare il valore del tag di gruppo per i dispositivi Autopilot<!-- 4816775 -->
Sarà possibile modificare il valore del **tag di gruppo** per i dispositivi Autopilot:

1. Selezionare **Intune**  > **registrazione del dispositivo**  > **registrazione Windows**  > **dispositivi** **Windows Autopilot**  > .
1. Scegliere il dispositivo.
1. Modificare il valore del **tag di gruppo** nel riquadro a destra.
1. Selezionare **Salva**.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Gruppi di utenti macOS di destinazione per richiedere la gestione JAMF <!-- 4061739 -->
Sarà possibile indirizzare gruppi di utenti specifici per richiedere che i dispositivi macOS siano gestiti da JAMF. Questa impostazione consente di applicare l'integrazione della conformità JAMF a un subset di dispositivi macOS mentre altri dispositivi continuano a essere gestiti da Intune. Il targeting consente inoltre di eseguire gradualmente la migrazione dei dispositivi degli utenti da un sistema di gestione di dispositivi mobili (MDM) all'altro.

<!-- ***********************************************-->
## <a name="intune-apps"></a>App di Intune

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Esperienza di registrazione macOS migliorata in Portale aziendale <!-- 5074349  -->
Il Portale aziendale per l'esperienza di registrazione di macOS avrà un processo di registrazione più semplice che sarà allineato più strettamente con la Portale aziendale per l'esperienza di registrazione di iOS. Gli utenti del dispositivo vedranno:  

* Interfaccia utente più accattivante.  
* Elenco di controllo migliorato per la registrazione.  
* Istruzioni più chiare su come registrare i propri dispositivi.  
* Opzioni di risoluzione dei problemi migliorate.  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Miglioramento della progettazione dell'elenco di controllo nell'app Portale aziendale per Android<!-- 5550857  -->
L'elenco di controllo dell'installazione nell'app Portale aziendale per Android verrà aggiornato con una progettazione leggera e nuove icone. Le modifiche si allineano con gli aggiornamenti recenti apportati all'app Portale aziendale per iOS.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoraggio e risoluzione dei problemi

### <a name="updated-support-experience-------5012398------"></a>Esperienza di supporto aggiornata   <!--  5012398    -->
Nell'ambito dei miglioramenti continui, l'esperienza di supporto nella console per Intune verrà aggiornata.  Verranno migliorati la ricerca e il feedback nella console per i problemi comuni e verrà semplificato il flusso di lavoro per contattare il supporto tecnico.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>Ruoli personalizzati o predefiniti duplicati <!-- 1081938 -->
Sarà possibile copiare ruoli predefiniti e personalizzati. A tale scopo, passare a **Intune** > **roles** > **tutti i ruoli** > scegliere un ruolo nell'elenco > **duplicato**. Assicurarsi di immettere un nuovo nome univoco.

<!-- ***********************************************-->

## <a name="security"></a>Sicurezza

### <a name="bitlocker-key-rotation--------2564951--------"></a>Rotazione delle chiavi di BitLocker     <!-- 2564951      -->
Sarà possibile usare Intune per ruotare le chiavi di ripristino di BitLocker per i dispositivi gestiti che eseguono Windows versione 1909 o successiva. 

<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
