---
title: In fase di sviluppo - Microsoft Intune
titlesuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9c377a8558b1f318b4ddad735b6368a291e34516
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57756820"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>In fase di sviluppo per Microsoft Intune - marzo 2019

Per facilitare la conformità e la pianificazione, questa pagina gli elenchi di UI Intune Aggiorna e a funzionalità che in fase di sviluppo ma non ancora rilasciato. Inoltre:

- Se si prevede che è necessario intervenire prima di una modifica, è possibile pubblicare un post di centro messaggi di Office gratuito.
- Quando una funzionalità viene avviata nell'ambiente di produzione, come un'anteprima o disponibili a livello generale, la descrizione della funzionalità passerà oltre questa pagina e al [pagina delle novità](whats-new.md).
- Questa pagina e il [pagina delle novità](whats-new.md) vengono aggiornate periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.
- Vedere il [M365 roadmap](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) per sequenze temporali e gli obiettivi strategici.

> [!Note]
> Questi elementi riflettono le aspettative di corrente di Microsoft sulle funzionalità di Intune introdotte in una versione futura. Le date e le singole funzionalità possono cambiare. Non tutti gli elementi in fase di sviluppo presentano una descrizione delle funzionalità in questa pagina.

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>Report di crittografia  <!-- 2351538 -->
È possibile usare un nuovo report di crittografia per visualizzare i dettagli relativi allo stato di crittografia dei dispositivi. Dettagli disponibili includerà una versione del TPM dispositivi, conformità crittografia e lo stato, segnalazione errori e altro ancora.  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>Chiavi di ripristino di BitLocker di accesso dal portale di Intune  <!-- 2351547  -->
Stiamo aggiungendo un nuovo punto di ingresso in dispositivi, in cui è possibile visualizzare informazioni dettagliate da Azure Active Directory (AAD) sull'ID della chiave di BitLocker e le chiavi di ripristino di BitLocker.

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>Tag di ambito per i criteri di configurazione di app <!--2371891 -->
È possibile aggiungere un tag di ambito per i criteri di configurazione in modo che solo le persone con ruolo assegnato anche il tag di ambito che hanno accesso ai criteri di configurazione app. I criteri di configurazione di app possono solo essere destinati a o associati alle App assegnate lo stesso tag di ambito.

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Assegnare profili di Autopilot al gruppo virtuale Tutti i dispositivi <!--2715522 -->
Sarà possibile assegnare profili di Autopilot al gruppo virtuale Tutti i dispositivi. A questo scopo, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > scegliere un profilo > **Assegnazioni** > in **Assegna a** scegliere **Tutti i dispositivi**. Per altre informazioni sui profili di AutoPilot, vedere [Registrare dispositivi Windows con Windows AutoPilot](enrollment-autopilot.md).

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>Installare le app disponibili tramite l'app portale aziendale dopo la registrazione in blocco Windows <!-- 2751523  -->
I dispositivi Windows registrati in Intune mediante [registrazione in blocco Windows](windows-bulk-enroll.md) (dei pacchetti di provisioning) saranno possibile usare l'app portale aziendale per installare le app disponibili. Per altre informazioni sull'app portale aziendale, vedere [aggiungere manualmente il portale aziendale di Windows 10](store-apps-company-portal-app.md) e [come configurare l'app portale aziendale di Microsoft Intune](company-portal-app.md).

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>Tag di ambito per i profili di provisioning delle app iOS <!--2934430 -->
È possibile aggiungere un tag di ambito di un profilo di provisioning di app iOS in modo che solo le persone con ruolo assegnato anche il tag di ambito che hanno accesso per il profilo di provisioning delle app iOS. 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Office Deployment Tool (ODT) XML per la distribuzione di Office ProPlus <!-- 3192477  -->
Sarà in grado di fornire Office Deployment Tool (ODT) XML durante la creazione di un'istanza di Office Pro Plus nella console di amministrazione di Intune. In questo modo maggiore possibilità di personalizzazione se le opzioni di Intune UI esistenti non soddisfano le proprie esigenze. 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>Impedisce agli utenti di analisi degli aggiornamenti di Windows    <!-- 3316758    -->
Stiamo aggiungendo un nuovo Windows anello di aggiornamento configurazione che è possibile usare che blocca gli utenti dall'analisi per gli aggiornamenti di Windows. Questa impostazione non sarà disponibile in all'interno del portale, ma può essere configurata tramite l'API Graph di Intune.

### <a name="windows-update-notifications-----3316782---"></a>Notifiche di aggiornamento di Windows  <!-- 3316782 -->
Stiamo aggiungendo il supporto per le configurazioni di anello di aggiornamento di Windows in modo sarà possibile configurare le notifiche di aggiornamento di Windows che gli utenti visualizzano. Questa impostazione non sarà disponibile in all'interno del portale, ma può essere configurata tramite l'API Graph di Intune.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Modifiche alla registrazione di portale aziendale per gli utenti dei dispositivi iOS 12 <!--3448635 -->  
Portale aziendale per iOS aggiornerà le schermate di registrazione dell'app e i passaggi per la compatibilità con le modifiche di registrazione MDM rilasciate in Apple iOS 12.2. Il flusso di lavoro aggiornata verrà ora richiesto agli utenti di:

- Consenti Safari aprire il sito Web portale aziendale (tramite Safari) e scaricare il profilo di gestione prima di tornare all'app portale aziendale. 
- Aprire l'app impostazioni e installare il profilo di gestione sul proprio dispositivo.
- Tornare all'app portale aziendale per completare la registrazione.  

Per altre informazioni su come preparare le modifiche, vedere la [post di Microsoft Tech Community](https://techcommunity.microsoft.com/). Nel frattempo, per supportare le nuove registrazioni di iOS nel portale aziendale, sono state aggiornate la procedura descritta in [Enroll iOS device in Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Queste modifiche docs sarà attivate dopo il rilascio di Apple iOS versione 12.2. 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>Supporto per connettori aggiuntivi nella pagina dello stato del Tenant <!-- 3617202     -->
La pagina dello stato del Tenant visualizzerà informazioni sullo stato di altri connettori, inclusi *Windows Defender Advanced Threat Protection* (ATP) e altri connettori Mobile Threat Defense.

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Intune di concedere l'accesso in sola lettura per alcuni ruoli di Azure Active Directory <!-- 3637917 -->
Si sarà concessione che Intune accesso in sola lettura per i seguenti ruoli di Azure AD. Le autorizzazioni concesse ai ruoli di Azure Active Directory sostituiscono le autorizzazioni concesse con controllo di accesso basato sui ruoli di Intune (RBAC).

Accesso in sola lettura ai dati di controllo di Intune:

- Amministratore di conformità
- Amministratore dei dati di conformità

Accesso di sola lettura a tutti i dati di Intune:

- Amministratore della protezione
- Operatore di sicurezza
- Ruolo con autorizzazioni di lettura per la sicurezza
- Lettore globale

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>Semplificare l'accesso alle impostazioni di diagnostica   <!-- 3804627   -->
Stiamo aggiungendo una nuova opzione per la **log di controllo** pannello in ogni in ogni carico di lavoro di Log di controllo nella console di Intune che è possibile usare per aprire direttamente la *le impostazioni di diagnostica* pagina.

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>Creare e usare i profili di configurazione di dispositivo nei dispositivi Android le in Intune <!-- 3895244  -->
Intune supporta i dispositivi Android le configurazione. In particolare, sarà in grado di: 

- Creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android le usando i profili di mobilità delle estensioni (MX) generati da StageNow (**configurazione del dispositivo** > **profili**  >  **Crea profilo** > **Android** per piattaforma).

Si applica a:  
- Android

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Distribuzione di app Microsoft Store per le aziende con licenza online <!-- 1672660  -->
Sarà possibile assegnare le app Microsoft Store per le aziende con licenza online richieste nel contesto del dispositivo. Questo tipo di distribuzione di app Microsoft Store per le aziende consentirà di installare le app per tutti gli utenti nel dispositivo. Questa opzione è disponibile solo per i dispositivi desktop Windows 10 RS4 e versioni successive. L'opzione di installazione nel contesto del dispositivo è disponibile nella pagina di assegnazione di App Client per le app con licenza online MSFB.

## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
