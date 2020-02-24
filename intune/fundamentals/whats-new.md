---
title: Novità di Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Informazioni sulle novità nel portale di Intune di Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7018e2ab4290219c752f44b4b391822438461e8e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415073"
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre ad [avvisi importanti](#notices), [versioni precedenti](whats-new-archive.md) e informazioni su [come vengono rilasciati gli aggiornamenti del servizio Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> La distribuzione di ogni [aggiornamento mensile](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728), che può impiegare fino a tre giorni, avviene nell'ordine seguente:
>
> - Giorno 1: Asia Pacifico
> - Giorno 2: Europa, Medio Oriente, Africa
> - Giorno 3: America del Nord
> - Giorno 4+: Intune per enti governativi
>
> Alcune funzionalità possono essere implementate in diverse settimane e durante la prima è possibile che non siano disponibili per tutti i clienti.
>
> Per un elenco delle funzionalità che verranno rilasciate prossimamente, vedere la [pagina delle funzionalità in fase di sviluppo](in-development.md).

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-february-10-2020"></a>Settimana del 10 febbraio 2020

### <a name="windows-7-ends-extended-support---3042987--"></a>Fine del supporto esteso di Windows 7 <!--3042987-->
Windows 7 ha raggiunto la fine del supporto esteso il 14 gennaio 2020. Contemporaneamente, è stato deprecato il supporto di Intune per i dispositivi che eseguono Windows 7. L'assistenza tecnica e gli aggiornamenti automatici che consentono di proteggere il PC non sono più disponibili. È consigliabile eseguire l'aggiornamento a Windows 10. Per altre informazioni, vedere il [post del blog relativo al piano di modifica](https://aka.ms/Windows7_Intune).


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>Microsoft Edge versione 77 e versioni successive nei dispositivi Windows 10<!-- 5843584 -->
Intune supporta ora la disinstallazione di Microsoft Edge versione 77 e successive nei dispositivi Windows 10. Per altre informazioni, vedere [Aggiungere Microsoft Edge per Windows 10 a Microsoft Intune](~/apps/apps-windows-edge.md).

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>Schermata rimossa da Portale aziendale, registrazione del profilo di lavoro Android<!--6103987 -->
La schermata **Passaggi successivi** è stata rimossa dal flusso di registrazione del profilo di lavoro Android in Portale aziendale per semplificare l'esperienza utente. Passare a [Eseguire la registrazione con il profilo di lavoro Android](/intune-user-help/enroll-device-android-work-profile) per visualizzare il flusso di registrazione del profilo di lavoro Android aggiornato.  

#### <a name="company-portal-app-improved-performance---6178652---"></a>Miglioramento delle prestazioni dell'app Portale aziendale<!-- 6178652 -->
L'app Portale aziendale è stata aggiornata per supportare prestazioni migliorate per i dispositivi che usano processori ARM64, ad esempio Surface Pro X. In precedenza l'app Portale aziendale funzionava in modalità ARM32 emulata. Nella versione 10.4.7080.0 e successive l'app Portale aziendale è ora compilata in modo nativo per ARM64. Per altre informazioni sull'app Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>Settimana del 27 gennaio 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>Supporto di Intune per il canale di distribuzione aggiuntivo Microsoft Edge versione 77 per macOS<!-- 5983950  -->
Microsoft Intune ora supporta il canale di distribuzione aggiuntivo **Stabile** per l'app Microsoft Edge per macOS. Il canale **Stabile** è il canale consigliato per la distribuzione su larga scala di Microsoft Edge negli ambienti aziendali. Viene aggiornato ogni sei settimane e ogni versione include miglioramenti derivanti dal canale **Beta**. Oltre ai canali **Stabile** e **Beta**, Intune supporta il canale **Dev**. L'anteprima pubblica offre i canali Stabile e Dev per Microsoft Edge 77 e versioni successive per macOS. Per impostazione predefinita, gli aggiornamenti automatici del browser sono attivati. Per altre informazioni, vedere [Aggiungere Microsoft Edge ai dispositivi macOS usando Microsoft Intune](~/apps/apps-edge-macos.md).

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Ritiro di Intune Managed Browser<!--5728447 -->
Intune Managed Browser verrà ritirato. Usare Microsoft Edge per un'esperienza protetta del browser di Intune. Per altre informazioni, vedere la voce "[Azione: Usare Microsoft Edge per l'esperienza protetta del browser di Intune](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience)" nella sezione [Notifiche](~/fundamentals/whats-new.md#notices) più avanti nell'articolo.

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>Settimana del 20 gennaio 2020 (versione del servizio 2001)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Modifica dell'esperienza utente durante l'aggiunta di app a Intune<!-- 4705829   -->
Quando si aggiungono app a Intune, viene visualizzata una nuova esperienza utente. La nuova esperienza rende disponibili le stesse impostazioni e gli stessi dettagli di prima, ma per aggiungere un'app a Intune ora è necessario eseguire un processo simile a una procedura guidata. Questa nuova esperienza mette a disposizione anche una pagina di revisione prima dell'aggiunta dell'app. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **App** > **Tutte le app** > **Aggiungi**. Per altre informazioni, vedere [Aggiungere app a Microsoft Intune](~/apps/apps-add.md).

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Richiedere il riavvio delle app Win32 <!-- 5622282   -->
È possibile richiedere che un'app Win32 venga riavviata dopo il completamento dell'installazione. È anche possibile scegliere la quantità di tempo, ovvero il periodo di tolleranza, prima che il riavvio venga eseguito.

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Modifica dell'esperienza utente durante la configurazione delle app in Intune<!-- 4207990   -->
Verrà visualizzata una nuova esperienza utente durante la creazione di criteri di configurazione delle app in Intune. La nuova esperienza rende disponibili le stesse impostazioni e gli stessi dettagli di prima, ma per aggiungere criteri a Intune ora è necessario eseguire un processo simile a una procedura guidata. Dall'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **App** > **Criteri di configurazione dell'app** > **Aggiungi**. Per altre informazioni, vedere [Criteri di configurazione delle app per Microsoft Intune](~/apps/app-configuration-policies-overview.md). 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>Supporto di Intune per il canale di distribuzione aggiuntivo Microsoft Edge per Windows 10<!-- 5861774 -->
Microsoft Intune ora supporta il canale di distribuzione aggiuntivo **Stabile** per Microsoft Edge 77 e versioni successive per le app Windows 10. Il canale **Stabile** è il canale consigliato per la distribuzione su larga scala di Microsoft Edge per Windows 10 negli ambienti aziendali. Viene aggiornato ogni sei settimane e ogni versione include miglioramenti derivanti dal canale **Beta**. Oltre ai canali **Stabile** e **Beta**, Intune supporta il canale **Dev**. Per altre informazioni, vedere [Microsoft Edge per Windows 10 - Configurare le impostazioni dell'app](~/apps/apps-windows-edge.md#configure-app-settings).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Esperienza dell'interfaccia utente migliorata quando si configura l'interfaccia utente del connettore locale di Exchange ActiveSync<!-- 5695492   -->
L'esperienza dell'interfaccia utente per la [configurazione del connettore locale di Exchange ActiveSync](../protect/exchange-connector-install.md) è stata migliorata. L'esperienza aggiornata usa un unico riquadro per configurare, modificare e riepilogare i dettagli dei connettori locali. 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Aggiungere le impostazioni proxy automatiche ai profili Wi-Fi per i profili di lavoro Android Enterprise<!-- 4490822   -->
Nei dispositivi con profilo di lavoro Android Enterprise è possibile creare profili Wi-Fi. Quando si sceglie il tipo di Wi-Fi Enterprise, è anche possibile immettere il tipo EAP (Extensible Authentication Protocol) usato nella rete Wi-Fi.

A questo punto, quando si sceglie il tipo Enterprise, è anche possibile immettere le impostazioni automatiche del proxy, incluso un URL del server proxy, come ad esempio `proxy.contoso.com`.

Per visualizzare le impostazioni del Wi-Fi correnti che è possibile configurare, vedere [Aggiungere le impostazioni Wi-Fi per i dispositivi che eseguono Android Enterprise e Android in modalità tutto schermo in Microsoft Intune](../configuration/wi-fi-settings-android-enterprise.md).

Si applica a:
- Profilo di lavoro di Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>Bloccare le registrazioni di dispositivi Android per produttore di dispositivi<!--5197392  -->
È possibile bloccare la registrazione dei dispositivi in base al produttore. Ciò si applica ai dispositivi con profilo di lavoro amministratore di dispositivi Android e Android Enterprise. Per visualizzare le limitazioni della registrazione, accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Dispositivi** > **Restrizioni registrazione**.

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>Miglioramenti all'interfaccia utente Crea il profilo del tipo di registrazione per iOS/iPadOS<!-- 6055005 -->
Per la registrazione utente iOS/iPadOS la pagina **Crea il profilo del tipo di registrazione** **Impostazioni** è stata semplificata per migliorare il processo di scelta di **Tipo di registrazione** mantenendo la stessa funzionalità. Per visualizzare la nuova interfaccia utente, passare all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) > **Dispositivi** > **iOS** > **Registrazione iOS** > **Tipi di registrazione** > **Crea profilo** > **Impostazioni**. Per altre informazioni, vedere [Creare un profilo di registrazione utente in Intune](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="new-information-in-device-details---4471759-5604099----"></a>Nuove informazioni nei dettagli del dispositivo<!-- 4471759 5604099  -->
Le informazioni seguenti sono ora presenti nella pagina **Panoramica** per i dispositivi:
- Capacità di memoria (quantità di memoria fisica nel dispositivo)
- Capacità di archiviazione (quantità di risorsa di archiviazione fisica nel dispositivo) 
- Architettura della CPU


#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>Azione remota Bypass del blocco attivazione di iOS rinominata Disabilita il blocco attivazione <!--5904591  -->
L'azione remota **Bypass del blocco attivazione** è stata rinominata **Disabilita il blocco attivazione**. Per altre informazioni, vedere [Disabilitare il blocco attivazione di iOS in Intune](../remote-actions/device-activation-lock-bypass.md).

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Supporto per la distribuzione degli aggiornamenti delle funzionalità di Windows 10 per i dispositivi Autopilot<!-- 5948137   -->
Intune supporta ora i dispositivi registrati con Autopilot usando le [distribuzioni di aggiornamenti delle funzionalità di Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates).

I criteri di aggiornamento delle funzionalità di Windows 10 non possono essere applicati durante la configurazione guidata di Autopilot e verranno applicati solo alla prima analisi di Windows Update dopo il completamento del provisioning di un dispositivo, che richiede in genere un giorno.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Report di distribuzione di Windows Autopilot (anteprima) <!-- 3856172   -->
Un nuovo report presenta informazioni dettagliate su ogni dispositivo distribuito tramite Windows Autopilot. Per altre informazioni, vedere [Report di distribuzione Autopilot](../enrollment/enrollment-autopilot.md#autopilot-deployments-report).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>Nuovo ruolo predefinito Endpoint Security Manager in Intune<!--4253397   -->
È disponibile un nuovo ruolo predefinito di Intune, ovvero Endpoint Security Manager. Questo nuovo ruolo offre agli amministratori l'accesso completo al nodo Endpoint Manager in Intune e l'accesso in sola lettura ad altre aree. Il ruolo è un'espansione del ruolo "amministratore della sicurezza" in Azure AD. Se al momento l'unico ruolo disponibile è Amministratori globali, non sono necessarie modifiche. Se si usano i ruoli e si vuole disporre della granularità offerta da Endpoint Security Manager (Gestore sicurezza endpoint), assegnare tale ruolo quando diventa disponibile. Per altre informazioni sui ruoli predefiniti, vedere [Controllo degli accessi in base al ruolo](role-based-access-control.md).

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>Settimana del 6 gennaio 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>Supporto S/MIME per Microsoft Outlook per iOS<!-- 2669398 -->
Intune supporta l'emissione di certificati di firma e crittografia S/MIME che possono essere usati con Outlook per iOS nei dispositivi iOS. Per altre informazioni, vedere [Etichette di riservatezza e protezione in Outlook per iOS e Android](https://aka.ms/omsmime).

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Memorizzare nella cache il contenuto dell'app Win32 usando il server Microsoft Connected Cache<!-- 6030314 -->
È possibile installare un server Microsoft Connected Cache nei punti di distribuzione di Configuration Manager per memorizzare nella cache il contenuto dell'app Win32 di Intune. Per altre informazioni, vedere [Microsoft Connected Cache in Configuration Manager - Supporto per le app Win32 di Intune](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>I profili dei modelli amministrativi (ADMX) di Windows 10 ora supportano i tag di ambito <!--5137390 -->
Ora è possibile assegnare tag di ambito ai profili dei modelli amministrativi (ADMX). Per fare ciò passare a **Intune** > **Dispositivi** > **Profili di configurazione** > scegliere un profilo dei modelli amministrativi nell'elenco > **Proprietà** > **Tag di ambito**. Per altre informazioni sui tag di ambito, vedere [Assegnare i tag di ambito ad altri oggetti](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects).

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>Settimana del 30 dicembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Recuperare la chiave di ripristino personale dai dispositivi macOS crittografati MEM<!-- 4851745 -->
Gli utenti finali possono recuperare la propria chiave di ripristino personale (chiave di FileVault) usando l'app Portale aziendale iOS. Il dispositivo con la chiave di ripristino personale deve essere registrato in Intune e crittografato con FileVault in Intune. Usando l'app Portale aziendale iOS, un utente finale può recuperare la chiave di ripristino personale nel dispositivo macOS crittografato facendo clic su **Ottieni la chiave di ripristino**. La chiave di ripristino può essere recuperata anche da Intune selezionando **Dispositivi** > *il dispositivo macOS crittografato e registrato* > **Ottieni la chiave di ripristino**. Per altre informazioni su FileVault, vedere [Crittografia FileVault per macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>App VPP con licenza utente iOS e iPadOS<!-- 5619268 -->
Per i dispositivi iOS e iPadOS registrati dall'utente, agli utenti finali non verranno più presentate le nuove applicazioni VPP con licenza dispositivo distribuite come disponibili. Gli utenti finali continueranno tuttavia a visualizzare tutte le app VPP con licenza utente all'interno del Portale aziendale. Per altre informazioni sulle app VPP, vedere [Procedura per la gestione delle app iOS e macOS acquistate tramite Volume Purchase Program di Apple con Microsoft Intune](~/apps/vpp-apps-ios.md).

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>Settimana del 23 dicembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>Avviso: scadenza del supporto per Windows 10 1703 (RS2) <!-- 5026679 -->
A partire dal 9 ottobre 2018, non è più previsto il supporto della piattaforma Microsoft per le edizioni Home, Pro e Pro for Workstations di Windows 10 1703 (RS2). Per le edizioni Enterprise ed Education di Windows 10, il supporto della piattaforma per Windows 10 1703 (RS2) è scaduto l'8 ottobre 2019. A partire dal 26 dicembre 2019, la versione minima dell'applicazione Portale aziendale Windows verrà aggiornata a Windows 10 1709 (RS3). I computer che eseguono versioni precedenti alla 1709 non riceveranno più le versioni aggiornate per l'applicazione dal Microsoft Store. Questa modifica è stata già comunicata ai clienti che gestiscono le versioni precedenti di Windows 10 attraverso il centro messaggi. Per altre informazioni, vedere [Date importanti nel ciclo di vita di Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>Settimana del 16 dicembre 2019

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Aggiornamenti di Modelli amministrativi per i dispositivi Windows 10 <!-- 5941568 -->

È possibile usare i modelli ADMX in Microsoft Intune per controllare e gestire le impostazioni per Microsoft Edge, Office e Windows. In Modelli amministrativi di Intune sono ha effettuati i seguenti aggiornamenti delle impostazioni dei criteri:

- Aggiunto il supporto per Microsoft Edge versioni 78 e 79.
- Include i file ADMX dell'11 novembre 2019 nei [file dei modelli amministrativi (ADMX/ADML) e in Strumento di personalizzazione di Office per Office 365 ProPlus, Office 2019 e Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

Per altre informazioni sui modelli ADMX di Intune, vedere [Usare i modelli di Windows 10 per configurare le impostazioni di criteri di gruppo in Microsoft Intune](../configuration/administrative-templates-windows.md).

Si applica a:

- Windows 10 e versioni successive

## <a name="week-of-december-9-2019-1912-service-release"></a>Settimana del 9 novembre 2019 (versione del servizio 1912)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migrazione a Microsoft Edge per gli scenari di esplorazione gestita<!-- 5173762 -->
Con l'approssimarsi del ritiro di Intune Managed Browser, sono state apportate modifiche ai criteri di protezione delle app per semplificare i passaggi necessari per spostare gli utenti in Edge. Sono state aggiornate le opzioni per l'impostazione dei criteri di protezione delle app **Limita il trasferimento di contenuto Web con altre app**, ovvero una delle seguenti:

- Qualsiasi app
- Intune Managed Browser
- Microsoft Edge
- Browser non gestito 

Quando si seleziona **Microsoft Edge**, gli utenti finali visualizzeranno un messaggio di accesso condizionale che informa che per gli scenari di esplorazione gestita è richiesto Microsoft Edge. Verrà richiesto di scaricare e accedere a Microsoft Edge con i propri account AAD, se non lo hanno già fatto.  Questa operazione equivale ad aver impostato su **true** l'impostazione di configurazione delle app `com.microsoft.intune.useEdge` per le app abilitate per MAM. Per i criteri di protezione delle app esistenti che usavano l'impostazione **Browser gestiti da criteri** sarà ora selezionato **Intune Managed Browser** e non sarà visibile alcuna modifica nel comportamento. Questo significa che gli utenti vedranno il messaggio che richiede l'uso di Microsoft Edge se l'impostazione di configurazione dell'app **useEdge** è stata impostata su **True**. Microsoft invita tutti i clienti che sfruttano gli scenari di esplorazione gestita ad aggiornare i criteri di protezione delle app con **Limita il trasferimento di contenuto Web con altre app** per assicurarsi che gli utenti visualizzino le linee guida appropriate per la transizione a Microsoft Edge, indipendentemente dall'app da cui vengono avviati i collegamenti. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>Configurare il contenuto delle notifiche dell'app per gli account dell'organizzazione<!-- 2576686  -->
I criteri di protezione delle app di Intune nei dispositivi Android e iOS consentono di controllare il contenuto delle notifiche dell'app per gli account dell'organizzazione. È possibile selezionare un'opzione (Consenti, Blocca i dati dell'organizzazione o Bloccato) per specificare in che modo vengono visualizzate le notifiche per gli account dell'organizzazione per l'app selezionata. Questa funzionalità richiede il supporto delle applicazioni e può non essere disponibile per tutte le applicazioni abilitate per i criteri di protezione delle app. Outlook per iOS versione 4.15.0 (o successive) e Outlook per Android 4.83.0 (o versione successiva) supporteranno questa impostazione. L'impostazione è disponibile nella console, ma la funzionalità inizierà a essere applicata dopo il 16 dicembre 2019. Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md).

#### <a name="microsoft-app-icons-update--4677605----"></a>Aggiornamento delle icone delle app Microsoft<!--4677605  -->
Le icone usate per le app Microsoft nel riquadro di destinazione app per i criteri di protezione delle app e i criteri di configurazione delle app sono state aggiornate.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Richiedere l'uso di tastiere approvate in Android<!--4761794  -->
Come parte di un criterio di protezione delle app, è possibile specificare l'impostazione [**Tastiere approvate**](../apps/app-protection-policy-settings-android.md#data-protection) per gestire le tastiere Android che possono essere usate con le app Android gestite. Quando un utente apre l'app gestita e non usa ancora una tastiera approvata per l'app, riceve un messaggio che richiede di passare a una delle tastiere approvate già installate nel dispositivo. Se necessario, viene visualizzato un collegamento per scaricare dal Google Play Store una tastiera approvata che l'utente potrà installare e configurare. L'utente può modificare i campi di testo in un'app gestita solo se la tastiera attiva non è una delle tastiere approvate.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>Aggiornamento dell'esperienza Single Sign-On per app e siti Web nei dispositivi iOS, iPadOS e macOS<!-- 4999578  -->
Intune ha aggiunto altre impostazioni di Single Sign-On (SSO) per i dispositivi iOS, iPadOS e macOS. È ora possibile configurare le estensioni delle app per l'accesso SSO con reindirizzamento scritte dall'organizzazione o dal provider di identità. Usare queste impostazioni per configurare un'esperienza Single Sign-On senza problemi per le app e i siti Web che usano i metodi di autenticazione moderni, ad esempio OAuth e SAML2. 

Queste nuove impostazioni ampliano le impostazioni precedenti per le estensioni delle app per l'accesso SSO e l'estensione Kerberos incorporata di Apple (**Dispositivi** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** o **macOS** per il tipo di piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). 

Per visualizzare l'intera gamma di impostazioni delle estensioni delle app per l'accesso SSO che è possibile configurare, andare a [SSO in iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) e [SSO in macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Si applica a:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>Aggiornate due impostazioni relative alle restrizioni per i dispositivi iOS e iPadOS per correggerne il comportamento<!-- 5701352    -->
Per i dispositivi iOS, è possibile creare profili di restrizione del dispositivo che **consentono gli aggiornamenti PKI in modalità wireless** e **bloccano la modalità USB con restrizioni** (**Dispositivi** > **Configurazione del dispositivo**  > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Prima di questa versione, le impostazioni e le descrizioni dell'interfaccia utente per le impostazioni seguenti non erano esatte e ora sono state corrette. A partire da questa versione, il comportamento delle impostazioni è il seguente:

**Blocca gli aggiornamenti PKI in modalità wireless**: **Blocca** impedisce agli utenti di ricevere gli aggiornamenti software a meno che il dispositivo non sia connesso a un computer. **Non configurato** (impostazione predefinita): consente a un dispositivo di ricevere gli aggiornamenti software senza essere connesso a un computer.
- In precedenza, questa impostazione poteva essere configurata come segue: **Consenti**, per consentire agli utenti di ricevere gli aggiornamenti software senza connettere i propri dispositivi a un computer.
**Consenti gli accessori USB durante il blocco del dispositivo**: Selezionando **Consenti** gli accessori USB sono autorizzati a scambiare dati con un dispositivo che è rimasto bloccato per più di un'ora. **Non configurato** (impostazione predefinita): la modalità con restrizioni USB non viene aggiornata nel dispositivo e agli accessori USB verrà impedito di trasferire i dati dal dispositivo se rimane bloccato per più di un'ora.
- In precedenza, questa impostazione poteva essere configurata come segue: **Blocca**, per disabilitare la modalità USB con restrizioni nei dispositivi con supervisione.

Per altre informazioni sulle impostazioni configurabili, vedere [Impostazioni dei dispositivi iOS e iPadOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Questa funzionalità si applica a:

- iOS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profili di configurazione della rete cablata per i dispositivi macOS<!-- 3508686  -->
   > [!NOTE]
   > Questa funzionalità è stata posticipata, ma verrà presto rilasciata.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Impedisce agli utenti di configurare le credenziali del certificato nell'archivio chiavi gestito nei dispositivi Android Enterprise con proprietario del dispositivo<!-- 3311998 -->
Nei dispositivi Android Enterprise con proprietario del dispositivo è possibile configurare una nuova impostazione che impedisce agli utenti di configurare le proprie credenziali del certificato nell'archivio chiavi gestito (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo > **Utenti e account**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="protected-wipe-action-now-available--51150000---"></a>Azione di cancellazione protetta ora disponibile<!--51150000 -->
Ora si ha la possibilità di usare l'azione Cancella dispositivo per eseguire una cancellazione protetta dei dati da un dispositivo. Le cancellazioni protette sono identiche a quelle standard, tranne per il fatto che non possono essere eluse spegnendo il dispositivo. Una cancellazione dei dati protetta continuerà a provare a reimpostare il dispositivo fino a quando non riesce. In alcune configurazioni questa azione potrebbe impedire il riavvio del dispositivo. Per altre informazioni, vedere [Ritirare o cancellare i dispositivi](../remote-actions/devices-wipe.md).

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>Indirizzo MAC Ethernet del dispositivo aggiunto alla pagina Panoramica del dispositivo<!--5562275 -->
È ora possibile visualizzare l'indirizzo MAC Ethernet del dispositivo nella relativa pagina dei dettagli (**Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Panoramica**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>Ottimizzata l'esperienza in un dispositivo condiviso quando sono abilitati i criteri di accesso condizionale basato su dispositivi<!-- 1734096  -->
È stata migliorata l'esperienza in un dispositivo condiviso con più utenti a cui sono applicati criteri di accesso condizionale basato su dispositivi controllando la valutazione di conformità più recente per l'utente quando si applicano i criteri. Per altre informazioni, vedere gli articoli sui seguenti argomenti:
- [Panoramica di Azure per l'accesso condizionale](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Panoramica della conformità dei dispositivi in Intune](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>Usare i profili certificato PKCS per eseguire il provisioning dei dispositivi con certificati<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
È ora possibile usare i profili certificato PKCS per emettere certificati per i *dispositivi* che eseguono Android for Work, iOS e Windows, se associati a profili come quelli per Wi-Fi e VPN. In precedenza queste tre piattaforme supportavano solo certificati basati sull'utente, con il supporto basato sul dispositivo limitato a macOS.

> [!NOTE]
> I profili di certificato PKCS non sono supportati con i profili Wi-Fi. Usare invece i profili certificato SCEP quando si usa un [tipo EAP](../configuration/wi-fi-settings-windows.md#enterprise-profile).

Per usare un certificato basato sul dispositivo, durante la [creazione di un profilo certificato PKCS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) per le piattaforme supportate, selezionare **Impostazioni**. Sarà possibile visualizzare l'impostazione per il **tipo di certificato**, che supporta le opzioni per il dispositivo o l'utente.



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="centralized-audit-logs--5603185-5697164---"></a>Log di controllo centralizzati<!--5603185, 5697164 -->
Con la nuova gestione centralizzata dei log di controllo ora è possibile riunire i log di controllo di tutte le categorie in un'unica pagina. È possibile filtrare i log per ottenere i dati che si stanno cercando. Per visualizzare i log di controllo, passare ad **Amministrazione del tenant** > **Log di controllo**. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>Informazioni sui tag di ambito incluse nei dettagli attività del log di controllo<!--5763534 -->
I dettagli attività del log di controllo ora includono informazioni sui tag di ambito (per gli oggetti Intune che supportano i tag di ambito). Per altre informazioni sui log di controllo, vedere [Usare i log di controllo per tenere traccia degli eventi e monitorarli](monitor-audit-logs.md).


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>Settimana del 2 dicembre 2019

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Nuove licenze di co-gestione di Microsoft Endpoint Configuration Manager<!--5027281-->
I clienti di Configuration Manager con Software Assurance possono ottenere i diritti di co-gestione di Intune per PC Windows 10 senza dover acquistare una licenza di Intune aggiuntiva per la co-gestione. I clienti non devono più assegnare singole licenze Intune/EMS ai propri utenti finali per la co-gestione di Windows 10.
- I dispositivi gestiti da Configuration Manager e registrati per la co-gestione hanno quasi gli stessi diritti di un PC con gestione MDM autonoma di Intune. Tuttavia, dopo la reimpostazione non è possibile eseguire di nuovo il provisioning tramite Autopilot.
- I dispositivi Windows 10 registrati in Intune con altri mezzi richiedono licenze di Intune complete.
- Per i dispositivi in altre piattaforme sono ancora richieste licenze di Intune complete.

Per altre informazioni, vedere [Condizioni di licenza](https://www.microsoft.com/en-us/Licensing/product-licensing/products).


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>Settimana del 18 novembre 2019 (versione di servizio 1911)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Aggiornamento dell'interfaccia utente quando si cancellano selettivamente i dati delle app<!-- 4102028 -->
L'interfaccia utente per la cancellazione selettiva dei dati delle app in Intune è stata aggiornata. Le modifiche dell'interfaccia utente includono:
- Un'esperienza semplificata con un formato di tipo procedura guidata condensata in un unico riquadro.
- Aggiornamento del flusso di creazione per includere le assegnazioni.
- Una pagina di riepilogo di tutti gli elementi impostati durante la visualizzazione delle proprietà, prima della creazione di un nuovo criterio o quando si modifica una proprietà. Al momento della modifica delle proprietà, inoltre, il riepilogo visualizzerà solo un elenco di elementi all'interno della categoria di proprietà in corso di modifica.

Per altre informazioni, vedere [Come cancellare solo i dati aziendali dalle app gestite da Intune](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>Supporto per le tastiere di terze parti per iOS e iPadOS<!-- 4922950 -->
Nel marzo 2019 è stata annunciata la rimozione del supporto per l'impostazione dei criteri di protezione delle app iOS "Tastiere di terze parti". La funzionalità è di nuovo disponibile in Intune con supporto sia per iOS che per iPadOS. Per abilitare questa impostazione, visitare la scheda **Protezione dati** di un criterio di protezione nuovo o esistente per le app iOS/iPadOS e trovare l'impostazione **Tastiere di terze parti** in **Trasferimento di dati**.

Il comportamento di questa impostazione dei criteri è leggermente diverso rispetto all'implementazione precedente. Nelle app con più identità che usano l'SDK versione 12.0.16 e successive, soggette a criteri di protezione delle app con questa impostazione configurata su **Blocco**, gli utenti finali non saranno in grado di scegliere le tastiere di terze parti sia nell'organizzazione che negli account personali. Le app che usano le versioni 12.0.12 e precedenti dell'SDK continueranno a presentare il comportamento illustrato nel post di blog relativo ai [problemi dovuti all'assenza del blocco delle tastiere di terze parti in iOS per gli account personali](https://aka.ms/3rdparty_iOS_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Definire come destinazione gruppi di utenti macOS per richiedere la gestione Jamf<!-- 4061739  --> 
È possibile definire come destinazione gruppi di utenti specifici i cui [dispositivi macOS verranno gestiti da Jamf](../protect/conditional-access-integrate-jamf.md). Ciò consente di applicare l'integrazione di conformità Jamf a un subset di dispositivi macOS mentre altri dispositivi sono gestiti da Intune. Se si sta già usando l'integrazione Jamf, per impostazione predefinita tutti gli utenti verranno definiti come destinazione per l'integrazione.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>Nuove impostazioni di Exchange ActiveSync durante la creazione di un profilo di configurazione del dispositivo di posta elettronica nei dispositivi iOS<!-- 4892824   --> 
Nei dispositivi iOS/iPadOS è possibile configurare la connettività di posta elettronica in un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Posta elettronica** per il tipo di profilo). 

Sono disponibili nuove impostazioni di Exchange ActiveSync, tra cui:
- **Dati di Exchange da sincronizzare**: Scegliere i servizi di Exchange da sincronizzare (o di cui bloccare la sincronizzazione) per calendario, contatti, promemoria, note e posta elettronica.
- **Consenti agli utenti di modificare le impostazioni di sincronizzazione**: Consentire, o impedire, agli utenti di modificare le impostazioni di sincronizzazione per questi servizi nei propri dispositivi.  

Per altre informazioni su questa impostazione, vedere le [impostazioni del profilo di posta elettronica per i dispositivi iOS in Intune](../configuration/email-settings-ios.md). 

Si applica a:

- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Impedire agli utenti di aggiungere account Google personali a dispositivi Android Enterprise completamente gestiti e dedicati<!-- 5353228   -->
Nei dispositivi Android Enterprise completamente gestiti e dedicati è disponibile una nuova impostazione che impedisce agli utenti di creare account Google personali (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo > **impostazioni Utenti e account** > **Account Google personale**).

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:

- Dispositivi completamente gestiti Android Enterprise
- Dispositivi dedicati Android Enterprise

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>La registrazione lato server per l'impostazione dei comandi Siri viene rimossa nel profilo Limitazioni del dispositivo iOS/iPadOS <!-- 5468501   -->
Nei dispositivi iOS e iPadOS l'impostazione della **registrazione lato server per i comandi Siri** viene rimossa dalla console di amministrazione di Microsoft Endpoint Manager (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App predefinite**). 

Questa impostazione non ha alcun effetto sui dispositivi. Per rimuovere l'impostazione dai profili esistenti, aprire il profilo, apportare le modifiche e quindi salvare il profilo. Il profilo viene aggiornato e l'impostazione viene eliminata dai dispositivi.

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi iOS e iPadOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Aggiornamenti delle funzionalità di Windows 10 (anteprima pubblica)<!-- 2384877 -->
È ora possibile distribuire gli [aggiornamenti delle funzionalità di Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) ai dispositivi Windows 10. Gli aggiornamenti delle funzionalità di Windows 10 sono nuovi criteri di aggiornamento software che impostano la versione di Windows 10 che si vuole venga installata e mantenuta nei dispositivi. È possibile usare questo nuovo tipo di criteri insieme agli anelli di aggiornamento di Windows 10 esistenti.

I dispositivi che ricevono i criteri di aggiornamento delle funzionalità di Windows 10 installeranno la versione specificata di Windows e rimarranno con tale versione fino a quando i criteri non verranno modificati o rimossi. I dispositivi che eseguono una versione successiva di Windows rimangono alla versione corrente. I dispositivi che mantengono una versione specifica di Windows possono comunque installare gli aggiornamenti di qualità e sicurezza per tale versione dagli anelli di aggiornamento di Windows 10.

Questo nuovo tipo di criteri viene implementato nei tenant a partire da questa settimana. Se questi criteri non sono ancora disponibili per il proprio tenant, lo saranno presto.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Aggiungere e modificare le informazioni fondamentali nei file PLIST per le applicazioni macOS<!-- 4736278 -->
Nei dispositivi macOS è ora possibile creare un profilo di configurazione del dispositivo che carica un file di elenco di proprietà (PLIST) associato a un'app o al dispositivo (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **macOS** per la piattaforma > **File delle preferenze** per il tipo di profilo).

Solo alcune app supportano le preferenze gestite e queste app potrebbero non consentire la gestione di tutte le impostazioni. Assicurarsi di caricare un file di elenco di proprietà che configuri le impostazioni dei canali del dispositivo e non le impostazioni dei canali degli utenti.

Per altre informazioni su questa funzionalità, vedere [Aggiungere un file elenco di proprietà ai dispositivi macOS usando Microsoft Intune](../configuration/preference-file-settings-macos.md).

Si applica a:

- Dispositivi macOS che eseguono la versione 10.7 e successive

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Modificare il valore del nome dispositivo per i dispositivi Autopilot<!-- 2640074 -->
È possibile modificare il valore Nome dispositivo per i dispositivi Autopilot aggiunti ad Azure AD.  Per altre informazioni, vedere la sezione sulla [modifica degli attributi dei dispositivi Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Modificare il valore del tag di gruppo per i dispositivi Autopilot<!-- 4816775   -->
È possibile modificare il valore Tag di gruppo per i dispositivi Autopilot. Per altre informazioni, vedere la sezione sulla [modifica degli attributi dei dispositivi Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="updated-support-experience---5012398---"></a>Esperienza di supporto tecnico aggiornata<!-- 5012398 -->

A partire da ora, viene implementata nei tenant un'esperienza nella console aggiornata e semplificata per [accedere a Guida e supporto tecnico per Intune](get-support.md). Se questo tipo di esperienza non è ancora disponibile per il proprio tenant, lo sarà presto.

Sono stati migliorati la ricerca e il feedback nella console per i problemi comuni nonché il flusso di lavoro usato per contattare il supporto tecnico. Quando si apre una richiesta di assistenza, vengono visualizzate stime in tempo reale dei tempi previsti per la risposta via telefono o posta elettronica e i clienti Premier e Unified Support hanno la possibilità di indicare la gravità del problema per ricevere più rapidamente assistenza.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Ottimizzazione dell'esperienza di creazione di report di Intune (anteprima pubblica) <!-- 3791418 -->
Intune offre ora un'esperienza ottimizzata per la creazione dei report, inclusi i nuovi tipi, una migliore organizzazione dei report, visualizzazioni più mirate, funzionalità avanzate per i report, nonché dati più coerenti e tempestivi. I nuovi tipi di report sono incentrati sugli elementi seguenti:
- **Operativo**: contiene record aggiornati concentrati sugli stati negativi dell'integrità. 
- **Organizzativo**: offre un riepilogo più ampio dello stato generale.
- **Cronologico**: offre modelli e tendenze nell'arco di un determinato periodo di tempo.
- **Specialistico**: consente di usare i dati non elaborati per creare i propri report personalizzati.

Il primo set di nuovi report è incentrato sulla conformità del dispositivo. Per altre informazioni, vedere il [post di blog sul framework di reporting di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) e [Report di Intune](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Duplicare ruoli personalizzati o predefiniti <!-- 1081938   -->
È ora possibile copiare i ruoli predefiniti e personalizzati. Per altre informazioni, vedere l'articolo relativo alla [copia di un ruolo](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>Nuove autorizzazioni per il ruolo di amministratore di istituto di istruzione <!-- 5621805  -->  
Sono state aggiunte due nuove autorizzazioni, **Assegnare il profilo** e **Dispositivo sincronizzato**, al ruolo di amministratore di istituto di istruzione > **Autorizzazioni** > **Programmi di registrazione**. L'autorizzazione del profilo di sincronizzazione consente agli amministratori dei gruppi di sincronizzare i dispositivi di Windows Autopilot. L'autorizzazione Assegnare il profilo consente di eliminare i profili di registrazione Apple avviati dall'utente. Consente inoltre di gestire le assegnazioni dei dispositivi Autopilot e le assegnazioni dei profili di distribuzione Autopilot. Per un elenco di tutte le autorizzazioni per l'amministratore del gruppo o dell'istituto di istruzione, vedere [Assegnare amministratori ai gruppi](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Sicurezza

#### <a name="bitlocker-key-rotation---2564951----"></a>Rotazione delle chiavi BitLocker<!-- 2564951  -->
È possibile usare un'azione del dispositivo Intune per [ruotare le chiavi di ripristino di BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) in modalità remota per i dispositivi gestiti che eseguono Windows versione 1909 o successiva. Per essere idonei alla rotazione delle chiavi di ripristino, i dispositivi devono essere configurati in modo da supportare tale rotazione.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>Aggiornamenti alla registrazione di dispositivi dedicati per supportare la distribuzione del certificato dispositivo SCEP <!-- 5198878  -->
Intune ora supporta la distribuzione del certificato dispositivo SCEP ai dispositivi Android Enterprise dedicati per l'accesso basato su certificati ai profili Wi-Fi. Per il corretto funzionamento della distribuzione, è necessario che l'app Microsoft Intune sia presente nel dispositivo. Di conseguenza, l'esperienza di registrazione per i dispositivi Android Enterprise dedicati è stata aggiornata. Le nuove registrazioni iniziano ancora allo stesso modo (con QR, NFC, Zero Touch o identificatore del dispositivo) ma ora hanno un passaggio che richiede agli utenti di installare l'app di Intune. I dispositivi esistenti inizieranno progressivamente a installare automaticamente l'app.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>Log di controllo di Intune per la collaborazione business-to-business<!--5670211 -->
La collaborazione business-to-business (B2B) consente di condividere in modo sicuro le applicazioni e i servizi dell'azienda con gli utenti guest di qualsiasi altra organizzazione, mantenendo al tempo stesso il controllo sui propri dati aziendali. Intune ora supporta i log di controllo per gli utenti guest B2B. Ad esempio, quando gli utenti guest apportano modifiche, Intune sarà in grado di acquisire i dati usando i log di controllo. Per altre informazioni, vedere [Che cos'è l'accesso utente guest in Azure Active Directory B2B?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>Settimana del 11 novembre 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Esperienza di registrazione macOS migliorata in Portale aziendale <!-- 5074349  -->  
Il Portale aziendale per l'esperienza di registrazione di macOS prevede un processo di registrazione più semplice che si allinea maggiormente al Portale aziendale per l'esperienza di registrazione di iOS. Gli utenti dei dispositivi ora possono visualizzare:  

* Un'interfaccia utente più accattivante.  
* Un elenco di controllo per la registrazione migliorato.  
* Istruzioni più chiare su come registrare i dispositivi.  
* Opzioni di risoluzione dei problemi migliorate.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>App Web avviate dall'app Windows Portale aziendale<!-- 5030972 -->
Gli utenti finali possono ora avviare app Web direttamente dall'app Windows Portale aziendale. Gli utenti finali possono selezionare l'app Web e quindi scegliere l'opzione **Apri nel browser**. L'URL Web pubblicato viene aperto direttamente in un Web browser. Questa funzionalità verrà implementata nel corso della prossima settimana. Per altre informazioni sull'aggiunta di app Web, vedere [Aggiungere app Web in Microsoft Intune](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Nuova colonna Tipo di assegnazione in Portale aziendale per Windows 10 <!-- 5459950  -->
La colonna Portale aziendale > **App installate** > **Tipo di assegnazione** è stata rinominata **Richiesta dall'organizzazione**.  In tale colonna verrà visualizzato **Sì** o **No** per indicare se un'app è obbligatoria o facoltativa per l'organizzazione. Queste modifiche sono state apportate perché gli utenti dei dispositivi erano confusi in merito al concetto di app disponibili. Per altre informazioni sull'installazione di app nel Portale aziendale, vedere [Installare e condividere app nel dispositivo](/intune-user-help/install-apps-cpapp-windows). Per altre informazioni sulla configurazione dell'app Portale aziendale per gli utenti, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Settimana del 4 novembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Le baseline di sicurezza sono supportate in Microsoft Azure per enti pubblici<!-- 4062552 -->

Le istanze di Intune ospitate in *Microsoft Azure per enti pubblici* ora possono usare le [baseline di sicurezza](../protect/security-baselines.md) per la protezione degli utenti e dei dispositivi.

## <a name="whats-new-archive"></a>Archivio delle novità
Per i mesi precedenti, vedere [Novità di Microsoft Intune - Mesi precedenti](whats-new-archive.md).

## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
