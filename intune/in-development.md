---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ee62213c9ef23302de7fa7342569e1903514699
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341354"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>In fase di sviluppo per Microsoft Intune - Luglio 2019

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

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>Gestione delle app


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>Notifiche personalizzate per utenti e gruppi    <!-- 16766574   -->
Sarà presto possibile inviare notifiche push ad hoc personalizzate dall'applicazione Portale aziendale agli utenti di dispositivi iOS e Android gestiti con Intune. Queste notifiche personalizzate non sono associate a specifiche funzionalità di Intune e possono essere usate per qualsiasi scopo, incluse le notifiche generali da inviare ad alcuni o a tutti i dipendenti.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>Configurare il contenuto della notifica dell'app per gli account dell'organizzazione <!-- 2576686 -->
I criteri di protezione delle app di Intune (APP) nei dispositivi Android e iOS consentiranno di controllare il contenuto delle notifiche dell'app per gli account dell'organizzazione. Questa funzionalità richiede il supporto delle applicazioni e potrebbe non essere disponibile per tutte le applicazioni abilitate per l'APP. Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md).

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Creazione di report per le app disponibili in Google Play per i profili di lavoro Android <!-- 3041956  -->
Per le installazioni di app disponibili nei dispositivi con profilo di lavoro Android, è possibile visualizzare lo stato di installazione delle app, nonché la versione installata delle app gestite in Google Play. Per altre informazioni, vedere [Come monitorare i criteri di protezione delle app](app-protection-policies-monitor.md), [Gestire i dispositivi con profilo di lavoro Android con Intune](android-enterprise-overview.md) e [Tipo di app Google Play gestite](apps-add-android-for-work.md#managed-google-play-app-type).

<!-- ***********************************************-->
## <a name="device-configuration"></a>Configurazione del dispositivo


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>Supporto per i profili VPN IKEv2 per iOS <!-- 1943438 -->
È possibile creare profili VPN per il client VPN nativo di iOS tramite il protocollo IKEv2. IKEv2 è un nuovo tipo di connessione in **Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS**  per la piattaforma > **VPN** per il tipo di profilo > **Impostazioni**.

Questi profili VPN configurano il client VPN nativo. Pertanto, non viene installata alcuna app del client VPN, e non ne viene eseguito il push, nei dispositivi gestiti. Questa funzionalità richiede che i dispositivi siano registrati in Intune (registrazione MDM).

Per visualizzare le impostazioni VPN correnti che è possibile configurare, vedere [Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune](vpn-settings-ios.md).

Si applica a: iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Usare le "regole di applicabilità" durante la creazione dei profili di configurazione dispositivo Windows 10 <!-- 2549910 -->
Creare profili di configurazione dispositivo Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** per la piattaforma). Sarà possibile creare una **regola di applicabilità** in modo che il profilo si applichi solo a un'edizione o versione specifica. Creare ad esempio un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applichi solo ai dispositivi che eseguono Windows 10 Enterprise.

Si applica a: 
- Windows 10 e versioni successive

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Impostazioni avanzate per Windows Defender Firewall   <!--  1311949     -->
Trattandosi di un'anteprima pubblica, a breve sarà possibile usare Intune per gestire le regole firewall personalizzate nei client per Windows Defender.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Nuova finestra di progettazione della configurazione quando si crea un profilo OEMConfig per Android Enterprise <!-- 3712769  -->
In Intune è possibile creare un profilo di configurazione del dispositivo che usa un'app OEMConfig (configurazione del dispositivo > profili > creare un profilo > Android Enterprise per la piattaforma > OEMConfig per il tipo di profilo). Quando si esegue questa operazione, viene aperto un editor JSON con un modello e i valori che è possibile modificare. Questo aggiornamento include una finestra di progettazione di configurazione con un'esperienza utente migliorata che mostra i dettagli incorporati nell'app, inclusi i titoli, le descrizioni e altro ancora. L'editor JSON è ancora disponibile e Mostra tutte le modifiche apportate nella finestra di progettazione di configurazione.

Per visualizzare le impostazioni correnti, passare a [usare e gestire i dispositivi Android Enterprise con OEMConfig](android-oem-configuration-overview.md).

Si applica a: Android Enterprise


<!-- ***********************************************-->
## <a name="device-management"></a>Gestione dei dispositivi

### <a name="improve-device-location---3855417---"></a>Migliorare il percorso del dispositivo<!-- 3855417 -->
Sarà possibile ingrandire le coordinate esatte di un dispositivo usando l'azione **individua dispositivo** . Per ulteriori informazioni sull'individuazione dei dispositivi iOS persi, vedere la pagina relativa alla [ricerca di dispositivi iOS persi](device-locate.md).

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>Configurare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni <!--4231059  -->
È possibile impostare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni (anziché il limite corrente di 90 giorni) dopo l'ultimo accesso. A tale scopo, passare a**dispositivi** >  **Intune** > **installazione** > **regole di pulizia del dispositivo**.


<!-- ***********************************************-->
## <a name="security"></a>Sicurezza

### <a name="import-and-export-security-baselines------3408610------------"></a>Importare ed esportare le linee di base di sicurezza    <!--3408610          -->  
È stata aggiunta la funzionalità per esportare e importare le linee di base di sicurezza, in modo da poter eseguire le personalizzazioni e condividerle tra gli ambienti Intune.



<!-- ***********************************************-->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


