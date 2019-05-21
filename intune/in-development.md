---
title: In fase di sviluppo - Microsoft Intune
titleSuffix: ''
description: Funzionalità di Microsoft Intune in fase di sviluppo
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910318"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>In fase di sviluppo per Microsoft Intune - Maggio 2019

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>L'eliminazione di un dispositivo nel portale Apple si rifletterà nel portale di Intune <!--2489996 -->
Se un dispositivo viene eliminato dai portali di Device Enrollment Program di Apple o Apple Business Manager, il dispositivo verrà automaticamente eliminato da Intune durante la sincronizzazione successiva.

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>Supporto di base per la ricerca con parole chiave  <!-- 3082036         -->
Durante la creazione o la modifica di un profilo di base di sicurezza sarà presto possibile usare la *ricerca* per filtrare le impostazioni visualizzate nella console.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Reimpostare e cancellare i dispositivi in blocco usando l'API Graph <!-- 3295288 -->
Sarà possibile reimpostare e cancellare un massimo di 100 dispositivi in blocco tramite l'API Graph.

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10 <!-- 3617671 -->
Molti dispositivi Windows 10 e versioni successive hanno chipset Trusted Platform Module (TPM). Questo aggiornamento include una nuova impostazione di conformità che controlla la versione del chip TPM del dispositivo. 

Questa impostazione è descritta in [Impostazioni dei criteri di conformità per i dispositivi Windows 10 e versioni successive](compliance-policy-create-windows.md#device-security).

Si applica a: Windows 10 e versioni successive

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Script di PowerShell per l'estensione di gestione di Intune  <!-- 3734186    -->
Sarà possibile configurare gli script di PowerShell per l'esecuzione con privilegi di amministratore dell'utente nel dispositivo. Per altre informazioni, vedere [Usare gli script di PowerShell nei dispositivi Windows 10 in Intune](intune-management-extension.md).

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>Impedire agli utenti finali di modificare l'hotspot personale e disabilitare la registrazione nel server Siri nei iOS dispositivi con supervisione <!-- 4097904  --> 
Creare un profilo di limitazioni del dispositivo nel dispositivo iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni, che è possibile configurare:

- Hotspot personale
- Registrazione server Siri

Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità](device-restrictions-ios.md). 

Si applica a: iOS 12.2 e versioni successive

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>Nuove impostazioni di limitazione del dispositivo per l'app Classroom per i dispositivi macOS registrati in DEP <!-- 4097905  --> 
È possibile creare un profilo di configurazione del dispositivo per i dispositivi macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni dell'app Classroom per i dispositivi registrati in DEP e la possibilità di disabilitare la Libreria foto di iCloud.

Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-macos.md).

Si applica a: macOS 10.14.4 e versioni successive

### <a name="android-enterprise-app-management----4459905-idready---"></a>Gestione delle app Android Enterprise <!-- 4459905 idready -->
Per facilitare la configurazione e l'uso delle funzionalità di gestione di Android Enterprise per gli amministratori IT, Intune aggiungerà automaticamente quattro app comuni correlate a Android Enterprise alla console di amministrazione di Intune. Le quattro app per Android Enterprise sono le seguenti:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usata per gli scenari di Android Enterprise completamente gestiti.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)**  - Consente di accedere agli account se si usa la verifica a due fattori.
- **[Portale aziendale di Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usare per gli scenari con criteri di protezione app e profili di lavoro di Android Enterprise.
- [Schermata iniziale gestita](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Usata per gli scenari di Android Enterprise dedicati/in modalità a schermo intero.

In precedenza, gli amministratori IT dovevano trovare e approvare manualmente queste app in [Google Play Store gestito](https://play.google.com/store/apps) durante l'installazione. Questa modifica rimuove i passaggi manuali precedenti per consentire ai clienti di usare più facilmente e velocemente le funzionalità di gestione di Android Enterprise.

Gli amministratori IT noteranno che queste quattro app vengono aggiunte automaticamente all'elenco di app di Intune in occasione della prima connessione del tenant di Intune a Google Play gestito. Per altre informazioni, vedere [Connettere l'account di Intune all'account di Google Play gestito](connect-intune-android-enterprise.md). Per i tenant già connessi o che usano già Android Enterprise, gli amministratori non devono eseguire alcuna operazione. Queste quattro app diventeranno disponibili automaticamente entro 7 giorni del completamento della distribuzione dell'aggiornamento del servizio di maggio 2019.

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Impostazioni avanzate per Windows Defender Firewall <!-- 1311949 -->
A breve sarà possibile usare Intune per gestire le regole firewall personalizzate nei client per Windows Defender. Le regole possono specificare il comportamento in entrata e in uscita di applicazioni, indirizzi di rete e porte. 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>Gli utenti dei dispositivi potranno visualizzare tutte le app gestite che hanno installato o tentato di installare <!-- 2352913 -->
Nel Portale aziendale per Windows saranno ancora elencate tutte le app gestite&ndash; sia obbligatorie che disponibili&ndash; installate nel dispositivo dell'utente. Gli utenti potranno visualizzare le installazioni di app tentate e in sospeso e i rispettivi stati correnti. Se l'organizzazione non rende le app obbligatorie o disponibili, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Gli utenti potranno anche ordinare o filtrare le app in base allo stato di installazione.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Usare le "regole di applicabilità" durante la creazione dei profili di configurazione dispositivo Windows 10 <!-- 2549910 -->
Creare profili di configurazione dispositivo Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** per la piattaforma). Sarà possibile creare una **regola di applicabilità** in modo che il profilo si applichi solo a un'edizione o versione specifica. Creare ad esempio un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applichi solo ai dispositivi che eseguono Windows 10 Enterprise.

Si applica a: 
- Windows 10 e versioni successive

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Attività di sicurezza di Intune per Defender ATP (in anteprima pubblica) <!-- 3208597 -->
In anteprima pubblica, a breve Intune aggiungerà attività di sicurezza per la gestione delle minacce e delle vulnerabilità di Microsoft Defender annunciate di recente.  Con questa integrazione, gli amministratori delle operazioni di sicurezza in Windows Defender ATP (WDATP) potranno comunicare in modo più efficace agli amministratori di Intune le correzioni consigliate per le minacce emergenti. L'integrazione delle attività di sicurezza aggiunge un approccio basato sui rischi per individuare, classificare e correggere gli errori di configurazione e le vulnerabilità di endpoint.

Per altre informazioni sulle attività di sicurezza in Intune, vedere il post di blog sull'[uso delle attività di sicurezza di Intune per estendere la gestione delle minacce e delle vulnerabilità di Microsoft Defender ATP](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857). 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Linea di base di Windows Defender Advanced Threat Protection <!-- 3754134 -->
Verranno aggiunge nuove baseline per aiutare l'utente nella configurazione delle impostazioni di Windows Defender Advanced Threat Protection.



## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).


