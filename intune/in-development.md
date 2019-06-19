---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1c8a7be6646c0035eaefed6d61d749c8469c8a4e
ms.sourcegitcommit: 119962948045079022aa48f968dde3e961d7cd0c
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031657"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>In fase di sviluppo per Microsoft Intune - Giugno 2019

Per supportare gli utenti nella preparazione e pianificazione, questa pagina illustra gli aggiornamenti e le funzionalità dell'interfaccia utente di Intune che sono in fase di sviluppo ma non ancora rilasciati. Inoltre:

- Se sono previste azioni prima di una modifica, verrà pubblicato un post complementare nel Centro messaggi di Office.
- Quando una funzionalità viene avviata nell'ambiente di produzione, sia in versione anteprima sia disponibile a livello generale, la descrizione della funzionalità verrà spostata da questa pagina alla [pagina delle novità](whats-new.md).
- Questa pagina e la [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere la [Roadmap di Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per informazioni sulle sequenze temporali e i risultati finali strategici.

> [!Note]
> Questi elementi riflettono le aspettative correnti di Microsoft sulle funzionalità di Intune introdotte in una versione futura. Le date e le singole funzionalità possono cambiare. Questa pagina non include una descrizione della funzione per tutti gli elementi in fase di sviluppo.

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- ***********************************************-->
### <a name="app-management"></a>Gestione delle app

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gli utenti dei dispositivi potranno visualizzare tutte le app gestite che hanno installato o tentato di installare <!-- 2352913 -->
Nel Portale aziendale per Windows saranno elencate tutte le app gestite, sia obbligatorie che disponibili, installate nel dispositivo dell'utente. Gli utenti potranno visualizzare le installazioni di app tentate e in sospeso e i rispettivi stati correnti. Se l'organizzazione non rende le app obbligatorie o disponibili, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Gli utenti potranno anche ordinare o filtrare le app in base allo stato di installazione.

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>Configurare il browser collegabile ai dati dell'organizzazione <!-- 3145939 -->
I criteri di Protezione app di Intune nei dispositivi Android e iOS consentiranno di trasferire i collegamenti Web dell'organizzazione in un browser specifico diverso da Intune Managed Browser o Microsoft Edge.  Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md).

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>Pagina delle app installate nel sito Web Portale aziendale  <!-- 4224326 -->
Il [sito Web Portale aziendale](https://portal.manage.microsoft.com/) includerà una nuova pagina in modo che gli utenti possano visualizzare tutte le app che sono state installate nel dispositivo. Questo elenco include sia le app disponibili che le app obbligatorie per l'organizzazione. In questa pagina gli utenti potranno visualizzare lo stato dell'installazione e dei requisiti delle app nel dispositivo. Per altre informazioni sul sito Web Portale aziendale, vedere [Uso del sito Web Portale aziendale](/intune-user-help/using-the-intune-company-portal-website) e [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md).

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>Chiamare le operazioni di lettura dell'API Graph da un'applicazione senza le credenziali utente <!-- 4655885 -->
Le applicazioni potranno chiamare le operazioni di lettura dell'API Graph di Intune con l'identità dell'app senza le credenziali utente. Per altre informazioni, vedere [Ottenere l'accesso senza credenziali utente](https://docs.microsoft.com/graph/auth-v2-service).

<!-- ***********************************************-->
### <a name="device-configuration"></a>Configurazione del dispositivo


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Supporto per i profili VPN IKEv2 per iOS <!-- 1943438 -->
È possibile creare profili VPN per il client VPN nativo di iOS tramite il protocollo IKEv2. IKEv2 è un nuovo tipo di connessione in **Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS**  per la piattaforma > **VPN** per il tipo di profilo > **Impostazioni**.

Questi profili VPN configurano il client VPN nativo. Pertanto, non viene installata alcuna app del client VPN, e non ne viene eseguito il push, nei dispositivi gestiti. Questa funzionalità richiede che i dispositivi siano registrati in Intune (registrazione MDM).

Per visualizzare le impostazioni VPN correnti che è possibile configurare, vedere [Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune](vpn-settings-ios.md).

Si applica a: iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>Configurare le impostazioni per le estensioni del kernel nei dispositivi macOS <!-- 20430240 -->
Nei dispositivi macOS è possibile creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **macOS** per la piattaforma). Un aggiornamento successivo includerà un nuovo gruppo di impostazioni che consentiranno di configurare e usare le estensioni del kernel nei dispositivi.

Si applica a: macOS 10.13.2 e versioni successive

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Supporto di base per la ricerca con parole chiave  <!-- 3082036         -->
Durante la creazione o la modifica di un profilo di base di sicurezza sarà presto possibile usare la *ricerca* per filtrare le impostazioni visualizzate nella console.   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Usare le "regole di applicabilità" durante la creazione dei profili di configurazione dispositivo Windows 10 <!-- 2549910 -->
Creare profili di configurazione dispositivo Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** per la piattaforma). Sarà possibile creare una **regola di applicabilità** in modo che il profilo si applichi solo a un'edizione o versione specifica. Creare ad esempio un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applichi solo ai dispositivi che eseguono Windows 10 Enterprise.

Si applica a: 
- Windows 10 e versioni successive

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>L'impostazione app solo dallo store per i dispositivi Windows 10 include altre opzioni di configurazione <!-- 2697002  -->

Quando si crea un profilo di limitazione del dispositivo per i dispositivi Windows è possibile usare l'impostazione **Apps from the store only** (App solo dallo store) in modo che gli utenti installino app solo dall'archivio applicazioni di Windows (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). In un aggiornamento futuro questa impostazione verrà estesa per supportare altre opzioni. 

Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi Windows 10 (o più recenti) per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-windows-10.md#app-store).

Si applica a: Windows 10 e versioni successive

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>Distribuire più profili di dispositivo per estensioni della mobilità Zebra in un dispositivo, in un gruppo di utenti o in un gruppo di dispositivi <!-- 4089955 -->
In Intune è possibile usare estensioni di mobilità Zebra (MX) in un profilo di configurazione del dispositivo per personalizzare o aggiungere le impostazioni non predefinite in Intune. Attualmente è possibile distribuire un profilo per un dispositivo singolo. In un aggiornamento futuro sarà possibile distribuire più profili per:

- Un gruppo di utenti
- Un gruppo di dispositivi
- Un dispositivo singolo

Per informazioni su come usare MX in Intune, vedere [Usare e gestire i dispositivi Zebra con Mobility Extensions di Zebra in Microsoft Intune](android-zebra-mx-overview.md).

Si applica a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>Alcune impostazioni della modalità tutto schermo nei dispositivi iOS vengono impostate usando "Blocca" che sostituisce "Consenti" <!-- 4404075  -->
Quando si crea un profilo di limitazione del dispositivo in dispositivi iOS (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Modalità tutto schermo**), si impostano **Blocco automatico**, **Commutatore suoneria**, **Rotazione schermo**, **Pulsante Sospensione schermo** e **Pulsanti volume**. 

Attualmente, queste impostazioni vengono configurate usando **Consenti** (blocca la funzionalità) o **Non configurate** (consente la funzionalità). In un aggiornamento futuro, i valori saranno **Blocca** (blocca la funzionalità) o **Non configurate** (consente la funzionalità).

Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità](device-restrictions-ios.md). 

Si applica a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>Usare Face ID per l'autenticazione della password nei dispositivi iOS <!-- 4490704  -->
Quando si crea un profilo di limitazione per i dispositivi iOS, è possibile usare l'impronta digitale come password. In un aggiornamento futuro le impostazioni della password tramite impronta digitale consentiranno anche il riconoscimento facciale (**Configurazione dispositivo** > **Profili** > **Crea profilo**   >  **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Password**). Di conseguenza, le impostazioni seguenti sono state modificate:

- **Sblocco con impronta digitale** ora è **Sblocco di Touch ID e Face ID**.
- **Modifica dell'impronta digitale (solo con supervisione)** ora è **Modifica di Touch ID e Face ID (solo con supervisione)** .

Face ID è disponibile in iOS 11.0 e versioni successive. Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-ios.md#password).

Si applica a: iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>Le funzionalità delle app dipendono dall'area classificazioni quando si limitano giochi e funzionalità delle app dell'App Store nei dispositivi iOS <!-- 4593948  -->
Nei dispositivi iOS è possibile consentire o limitare le funzionalità relative a giochi, App Store e visualizzazione dei documenti (**Configurazione dispositivo** > **Profili** > **Crea profilo**  > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi**). È anche possibile scegliere l'area classificazioni, ad esempio Stati Uniti. In un aggiornamento futuro la funzionalità **App** diventerà un elemento figlio di **Area classificazioni** e dipenderà da **Area classificazioni**.

Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Si applica a: iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>Modelli amministrativi per Criteri di gruppo     <!--  3510695 -->
Per contribuire a migliorare la sicurezza dei dispositivi nel cloud, verranno rilasciati modelli amministrativi che consentiranno di usare Intune per configurare alcune impostazioni di Criteri di gruppo per i PC Windows.  Questi modelli usano Policy Configuration Service Provider per offrire fino a 2500 impostazioni aggiuntive da Office, Windows e OneDrive.

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Nuove impostazioni della baseline di sicurezza di Windows  <!-- 3534649, 4217151          -->
Sono state aggiunte nuove impostazioni della baseline di sicurezza di Windows. La prima impostazione è per la sicurezza basata sulla virtualizzazione, che richiede Avvio protetto. La seconda impostazione consentirà di gestire l'attivazione vocale delle app di Windows quando lo schermo è bloccato.

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>Le baseline della sicurezza saranno disponibili a livello generale  <!--  3785395       -->
La funzionalità Baseline di sicurezza sarà disponibile a breve in anteprima e a livello generale. 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Il modello della baseline di sicurezza di Windows sarà disponibile a livello generale   <!--  3794072       -->
Il modello della baseline di sicurezza di Windows sarà disponibile a breve in anteprima e a livello generale. La versione di anteprima del modello verrà ritirata e sarà disponibile un nuovo modello.

<!-- ***********************************************-->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>Assegnare i tag di ambito a tutti i dispositivi gestiti in un gruppo di sicurezza <!-- 3173810 -->
Attualmente è possibile assegnare un tag di ambito a un dispositivo accedendo alla pagina **Proprietà** di ogni singolo dispositivo e selezionando il tag di ambito. In un aggiornamento futuro sarà possibile assegnare i tag di ambito a un gruppo di sicurezza e anche tutti i dispositivi del gruppo di sicurezza saranno associati a tali tag di ambito. A tale scopo, scegliere **Intune** > **Ruoli** > **Ambito (tag)**  > **Crea**  >  **Ambito (tag)** > scegliere i gruppi a cui si vuole assegnare il tag di ambito. Il tag di ambito verrà assegnato anche a tutti i dispositivi appartenenti ai gruppi. I tag di ambito impostati con questa funzionalità sovrascriveranno quelli impostati con il flusso di tag di ambito del dispositivo corrente. In un aggiornamento futuro il flusso corrente per assegnare i tag di ambito ai dispositivi sarà di sola lettura.

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Visualizzare il livello della patch di protezione per i dispositivi Android <!-- 4461911  -->
Sarà possibile visualizzare il livello della patch di protezione per i dispositivi Android. A tale scopo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Monitoraggio** > **Hardware**.


<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


