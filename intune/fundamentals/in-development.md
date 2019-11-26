---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 796439581ca0ae91e788a91ab0bc2ef8f6019626
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199347"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>In fase di sviluppo per Microsoft Intune - Dicembre 2019

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

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>app VPP con licenza utente iOS<!-- 5619268 idready -->
Per i dispositivi iOS per la registrazione utente, gli utenti finali non verranno più presentati con le applicazioni VPP con licenza dispositivo distribuite come disponibili. Tuttavia, gli utenti finali continueranno a vedere tutte le app VPP con licenza utente all'interno del Portale aziendale. Per altre informazioni sulle app VPP, vedere [Procedura per la gestione delle app iOS e macOS acquistate tramite Volume Purchase Program di Apple con Microsoft Intune](~/apps/vpp-apps-ios.md).

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>Recuperare la chiave di ripristino personale dai dispositivi macOS crittografati di MEM<!-- 4851745 idready -->
Gli utenti finali saranno in grado di recuperare la chiave di ripristino personale (chiave FileVault) usando l'app Portale aziendale iOS. Il dispositivo con la chiave di ripristino personale deve essere registrato in Intune e crittografato con FileVault tramite Intune. Usando l'app Portale aziendale iOS, un utente finale può aprire la visualizzazione Web di Safari e recuperare la chiave di ripristino personale. In Intune selezionare **dispositivi** > *dispositivo MacOS crittografato e registrato* > ottenere la chiave di **ripristino**. Per altre informazioni su FileVault, vedere [crittografia FileVault per MacOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

### <a name="microsoft-app-icons-update--4677605--"></a>Aggiornamento delle icone delle app Microsoft<!--4677605-->
Verranno aggiornate le icone usate per le app Microsoft nel riquadro destinazione app per i criteri di protezione delle app e i criteri di configurazione delle app.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Supporto di S/MIME per Microsoft Outlook Mobile<!-- 2669398  -->
Intune supporterà la distribuzione di certificati S/MIME per la firma e la crittografia che possono essere usati con Outlook Mobile in iOS e Android. Per informazioni correlate, vedere [impostazioni di posta elettronica per i dispositivi iOS](~/configuration/email-settings-ios.md) e [le impostazioni di posta elettronica per i dispositivi Android](~/configuration/email-settings-android.md).

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>Supporto delle impostazioni personalizzate per le applicazioni macOS<!-- 4736278  -->
Intune supporterà le impostazioni personalizzate, consentendo di aggiungere chiavi e valori specifici a un file di elenco delle proprietà delle preferenze (con estensione plist) esistente per configurare le app macOS e il dispositivo. Non tutte le app supportano le preferenze gestite e in alcuni casi è possibile gestire solo impostazioni specifiche. Le impostazioni vengono distribuite solo tramite il canale del dispositivo. È consigliabile caricare solo file di elenco delle proprietà o file XML destinati alle impostazioni del canale del dispositivo.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Visualizzare le notifiche per l'app Portale aziendale in Windows<!-- 1808082  -->
L'app Portale aziendale nei dispositivi Windows verrà aggiornata per visualizzare le notifiche di tipo avviso popup agli utenti, anche quando l'applicazione viene chiusa. L'aggiornamento mostrerà le notifiche per le app disponibili solo quando lo stato dell'installazione è completato o non riuscito. L'app Portale aziendale non visualizzerà le notifiche per le applicazioni obbligatorie.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>Visualizzare i messaggi di stato dell'installazione per l'app Portale aziendale<!-- 2514416  -->
L'app Portale aziendale visualizzerà messaggi di stato di installazione dell'app aggiuntivi per gli utenti finali. Alle nuove funzionalità di dipendenza Win32 verranno applicate le condizioni seguenti:
- Non è stato possibile installare l'app. Le dipendenze definite dall'amministratore non sono state soddisfatte.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>Configurare il contenuto della notifica dell'app per gli account dell'organizzazione<!-- 2576686 -->
L'APP Intune nei dispositivi Android e iOS consente di controllare il contenuto della notifica dell'app per gli account dell'organizzazione. Questa funzionalità richiede il supporto delle applicazioni e potrebbe non essere disponibile per tutte le applicazioni abilitate per le APP. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md)

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>Impedisce agli utenti di configurare le credenziali del certificato nell'archivio chiavi gestito nei dispositivi Android Enterprise Owner<!-- 3311998 idready -->
Nei dispositivi Android Enterprise Owner, sarà disponibile una nuova impostazione che impedisce agli utenti di configurare le credenziali del certificato nell'archivio chiavi gestito (**configurazione del dispositivo** > **profili** > **creare un profilo** > **Android Enterprise** per la piattaforma > **proprietario del dispositivo > restrizioni del dispositivo** per il tipo di profilo > utenti e **account**).

Per visualizzare le impostazioni correnti, passare alle [impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:
- Proprietario del dispositivo Android Enterprise, inclusi i dispositivi dedicati e completamente gestiti

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>Profili di configurazione dei dispositivi di rete cablata per i dispositivi macOS<!-- 3508686 idready -->
Nei dispositivi macOS, un aggiornamento futuro includerà un nuovo profilo di configurazione del dispositivo che configura le reti cablate (**configurazione del dispositivo** > **profili** > **creare il profilo** > **MacOS** per la piattaforma > **rete cablata** per il tipo di profilo). Usare questa funzionalità per creare profili 802.1 x per gestire le reti cablate e distribuire le reti cablate nei dispositivi macOS.

Si applica a:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Aggiungere le impostazioni proxy automatiche ai profili Wi-Fi per i profili di lavoro Android Enterprise<!-- 4490822 idready -->
Nei dispositivi del profilo di lavoro Android Enterprise è possibile creare profili Wi-Fi. Quando si sceglie il tipo di organizzazione Wi-Fi, è anche possibile immettere il tipo EAP (Extensible Authentication Protocol) usato nella rete Wi-Fi.

In un aggiornamento futuro, quando si sceglie il tipo Enterprise, sarà possibile immettere le impostazioni automatiche del proxy, incluso un URL del server proxy, ad esempio `proxy.contoso.com`.

Per visualizzare le impostazioni Wi-Fi correnti che è possibile configurare, vedere [aggiungere impostazioni Wi-Fi per i dispositivi che eseguono Android Enterprise e Android Kiosk in Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Si applica a:
- Profilo di lavoro di Android Enterprise

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>Abilitare il controllo di accesso alla rete (NAC) con la VPN Cisco AnyConnect nei dispositivi iOS<!-- 4860111 idready -->
Nei dispositivi iOS è possibile creare un profilo VPN e usare diversi tipi di connessione, tra cui Cisco AnyConnect (**configurazione del dispositivo** > **profili** > **creare un profilo** > **iOS** per la piattaforma > **VPN** per il tipo di profilo > **Cisco AnyConnect** per il tipo di connessione). 

In un aggiornamento futuro sarà possibile abilitare il controllo di accesso alla rete (NAC) con Cisco AnyConnect. Per usare questa funzionalità:

1. Nella [Guida dell'amministratore del motore Cisco Identity Services](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html), seguire la procedura descritta in **configurazione di Microsoft INTUNE come server MDM** per configurare Cisco Identity Services Engine (ISE) in Azure.
2. Nel profilo di configurazione del dispositivo Intune selezionare l'impostazione **Abilita controllo di accesso alla rete (NAC)** .

Per visualizzare tutte le impostazioni VPN disponibili, passare a [configurare le impostazioni VPN nei dispositivi iOS](../configuration/vpn-settings-ios.md).

Si applica a:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>Esperienza Single Sign-On aggiornata per app e siti Web nei dispositivi iOS, iPados e macOS<!-- 4999578 idready -->
Intune aggiunge altre impostazioni Single Sign-On per i dispositivi iOS, iPados e macOS. Attualmente, è possibile configurare le estensioni dell'app SSO per le credenziali e l'estensione Kerberos predefinita di Apple in Intune. In un aggiornamento futuro sarà possibile configurare le estensioni dell'app di reindirizzamento SSO scritte dall'organizzazione o dal provider di identità. 

Usare queste impostazioni per configurare un'esperienza di Single Sign-On trasparente per app e siti Web che usano metodi di autenticazione moderni, ad esempio OAuth e SAML2. 

Per visualizzare le impostazioni dell'estensione dell'app SSO che è possibile configurare, passare a [SSO in iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) e [SSO in MacOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Si applica a:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Richiedi l'uso di tastiere approvate in Android<!--4761794 IDready -->
È possibile specificare un elenco di tastiere approvate da usare nelle app Android gestite. Dall'app gestita, all'utente verrà richiesto di passare a una delle tastiere approvate già installate nel dispositivo o, se necessario, verranno indirizzate al Google Play Store per scaricare e configurare una delle tastiere approvate. L'utente sarà in grado di modificare i campi di testo in un'app gestita solo se la tastiera attiva è una delle tastiere approvate.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Usare i certificati PKCS con profili Wi-Fi in dispositivi Windows 10 e versioni successive<!-- 3246388  -->
Attualmente, è possibile autenticare i profili Wi-Fi di Windows con certificati SCEP (**Configurazione dispositivo** > **profili** > **creare un profilo** > **Windows 10 e versioni successive** per la piattaforma > **Wi-Fi** per tipo di profilo > tipo di > **EAP** **aziendale** ). Sarà possibile usare i certificati PKCS con i profili Wi-Fi di Windows. Questa funzionalità consente agli utenti di autenticare i profili Wi-Fi usando profili certificato PKCS nuovi o esistenti nel tenant. 

Per altre informazioni sui profili Wi-Fi, vedere [aggiungere impostazioni Wi-Fi per i dispositivi Windows 10 e versioni successive in Intune](../configuration/wi-fi-settings-windows.md).

Si applica a:
- Windows 10 e versioni successive

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>Nuove impostazioni di ExchangeActiveSync durante la creazione di un profilo di configurazione del dispositivo di posta elettronica nei dispositivi iOS<!-- 4892824  --> 
Nei dispositivi iOS/iPados è possibile configurare la connettività della posta elettronica in un profilo di configurazione del dispositivo (**configurazione del dispositivo** > **profili** > **creare un profilo** > **iOS/Ipados** per la piattaforma > **posta elettronica** per il tipo di profilo). 

Saranno disponibili nuove impostazioni ExchangeActiveSync, tra cui:
- Scegliere i servizi da sincronizzare o bloccare la sincronizzazione, ad esempio posta elettronica, calendario e contatti.
- Consente o blocca gli utenti di modificare le impostazioni di sincronizzazione per questi servizi nei dispositivi. 

Per visualizzare le impostazioni correnti, passare a [impostazioni del profilo di posta elettronica per i dispositivi iOS in Intune](../configuration/email-settings-ios.md).

Si applica a:
- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>Impedisci agli utenti di aggiungere account Google personali a dispositivi Android Enterprise Owner e Dedicated Device<!-- 5353228  -->
Potrai impedire agli utenti di creare account Google personali in dispositivi Android Enterprise Owner e Dedicated Devices (**Device configuration** > **profiles** > **create profile** > **Android Enterprise** per la piattaforma > **proprietario del dispositivo > solo le restrizioni del dispositivo** per il tipo di profilo > **Impostazioni utenti e account**).

Per visualizzare le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:
- Proprietario del dispositivo Android Enterprise
- Dispositivi dedicati Android Enterprise

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>La registrazione lato server per l'impostazione dei comandi Siri è stata rimossa nel profilo restrizioni dispositivo iOS<!-- 5468501  -->
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

1. Selezionare **Intune** > **registrazione del dispositivo** > **registrazione Windows** > **dispositivi** **Windows Autopilot** > .
1. Scegliere il dispositivo.
1. Modificare il valore del **tag di gruppo** nel riquadro a destra.
1. Selezionare **Salva**.

### <a name="target-macos-user-groups-to-require-jamf-management---4061739---"></a>Gruppi di utenti macOS di destinazione per richiedere la gestione JAMF<!-- 4061739 -->
Sarà possibile indirizzare gruppi di utenti specifici per richiedere che i dispositivi macOS siano gestiti da JAMF. Questa impostazione consente di applicare l'integrazione della conformità JAMF a un subset di dispositivi macOS mentre altri dispositivi continuano a essere gestiti da Intune. Il targeting consente inoltre di eseguire gradualmente la migrazione dei dispositivi degli utenti da un sistema di gestione di dispositivi mobili (MDM) all'altro.

<!-- ***********************************************-->
## <a name="intune-apps"></a>App di Intune

### <a name="improved-macos-enrollment-experience-in-company-portal---5074349----"></a>Esperienza di registrazione macOS migliorata in Portale aziendale<!-- 5074349  -->
Il Portale aziendale per l'esperienza di registrazione di macOS avrà un processo di registrazione più semplice che sarà allineato più strettamente con la Portale aziendale per l'esperienza di registrazione di iOS. Gli utenti del dispositivo vedranno:  

* Interfaccia utente più accattivante.  
* Elenco di controllo migliorato per la registrazione.  
* Istruzioni più chiare su come registrare i propri dispositivi.  
* Opzioni di risoluzione dei problemi migliorate.  

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>Monitoraggio e risoluzione dei problemi

### <a name="centralized-audit-logs--5603185-5697164--"></a>Log di controllo centralizzati<!--5603185, 5697164-->
Una nuova esperienza di log di controllo centralizzato raccoglierà i log di controllo per tutte le categorie in un'unica pagina. Dovrai è in grado di filtrare i log per ottenere i dati che si stanno cercando. Per visualizzare i log di controllo, passare a **Amministrazione Tenant** > **log di controllo**. Per altre informazioni, vedere la pagina relativa [alle modifiche imminenti ai log di controllo in Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858).

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

### <a name="duplicate-custom-or-built-in-roles---1081938---"></a>Ruoli personalizzati o predefiniti duplicati<!-- 1081938 -->
Sarà possibile copiare ruoli predefiniti e personalizzati. A tale scopo, passare a **Intune** > **roles** > **tutti i ruoli** > scegliere un ruolo nell'elenco > **duplicato**. Assicurarsi di immettere un nuovo nome univoco.

<!-- ***********************************************-->

## <a name="security"></a>Sicurezza

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>Usare i profili certificato PKCS per eseguire il provisioning dei dispositivi con certificati<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
Potrai usare un profilo certificato PKCS per rilasciare certificati ai dispositivi, espandendo il supporto corrente per i certificati basati sull'utente. I certificati basati su dispositivo saranno supportati dalle piattaforme Android, iOS e Windows e potranno essere usati per i profili Wi-Fi e VPN.

<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


