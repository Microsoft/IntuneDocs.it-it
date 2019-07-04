---
title: Novità di Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Informazioni sulle novità nel portale di Intune di Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 756fafc02a6d64b1495a838ab8eee4130ee77361
ms.sourcegitcommit: a63b9eaa59867ab2b0a6aa415c19d9fff4fda874
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389345"
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre ad [avvisi importanti](#notices), [versioni precedenti](whats-new-archive.md) e informazioni su [come vengono rilasciati gli aggiornamenti del servizio Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> La distribuzione di ogni [aggiornamento mensile](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728), che può impiegare fino a tre giorni, avviene nell'ordine seguente:
> - Giorno 1: Asia Pacifico
> - Giorno 2: Europa, Medio Oriente, Africa
> - Giorno 3: America del Nord
> 
> Alcune funzionalità potrebbero essere implementate nel corso di settimane e potrebbero non essere disponibili a tutti i clienti nella prima settimana.
>
> Per un elenco delle funzionalità che verranno rilasciate prossimamente, vedere la [pagina delle funzionalità in fase di sviluppo](in-development.md).

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-june-17-2019"></a>Settimana del 17 giugno 2019   

### <a name="app-management"></a>Gestione delle app

#### <a name="new-features-in-microsoft-intune-app"></a>Nuove funzionalità dell'app Microsoft Intune
Sono state aggiunte nuove funzionalità all'app Microsoft Intune (anteprima) per Android. Ora gli utenti di dispositivi Android completamente gestiti possono:  

* Visualizzare e gestire i dispositivi che hanno registrato tramite il Portale aziendale Intune o l'app Microsoft Intune.    
* Contattare l'organizzazione per richiedere supporto.    
* Inviare feedback a Microsoft.    
* Visualizzare termini e condizioni, se impostati dall'organizzazione.  

## <a name="week-of-june-10-2019"></a>Settimana del 10 giugno 2019 

### <a name="app-management"></a>Gestione delle app  

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>Nuove app di esempio che mostrano l'integrazione di Intune SDK disponibile su GitHub <!-- 2653471 -->
L'account msintuneappsdk di GitHub ha aggiunto nuove applicazioni di esempio per iOS (Swift), Android, Xamarin.iOS, Xamarin Forms e Xamarin.Android. Lo scopo di queste app è completare la documentazione esistente e fornire dimostrazioni su come integrare Intune App SDK nelle proprie app per dispositivi mobili. Gli sviluppatori di app che hanno bisogno di altre indicazioni di Intune SDK possono vedere i collegamenti agli esempi seguenti:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App): app di messaggistica istantanea nativa di iOS (Swift) che usa Azure Active Directory Authentication Library (ADAL) per l'autenticazione negoziata.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App): app di elenco attività nativa di Android che usa ADAL per l'autenticazione negoziata.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps): app di elenco attività di Xamarin.Android che usa ADAL per l'autenticazione negoziata. Questo repository contiene anche l'app Xamarin.Forms.
- [App di esempio di Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios): app di esempio di base per Xamarin.iOS.

## <a name="week-of-may-27-2019"></a>Settimana del 27 maggio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Creazione di report per app potenzialmente dannose nei dispositivi Android <!-- 4223162 -->
Intune ora offre ulteriori informazioni di report sulle app potenzialmente dannose nei dispositivi Android. 

## <a name="week-of-may-20-2019"></a>Settimana del 20 maggio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="windows-company-portal-app----3316993---"></a>App Portale aziendale Windows <!-- 3316993 -->
L'app Portale aziendale di Windows ora ha una nuova pagina con l'etichetta **Dispositivi**. La pagina **Dispositivi** visualizza per gli utenti finali tutti i loro dispositivi registrati. Gli utenti visualizzano questa modifica nel Portale aziendale quando usano la versione 10.3.4291.0 e le versioni successive. Per informazioni sulla configurazione del Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nome dell'attributo OrderID dei dispositivi Autopilot modificato in Tag di gruppo <!-- 4659453 -->

Il nome dell'attributo **OrderID** nei dispositivi Autopilot è stato modificato in **Tag di gruppo** per renderlo più intuitivo. Quando si usano file con estensione csv per caricare informazioni sui dispositivi Autopilot, è necessario usare come intestazione colonna Tag di gruppo e non OrderID.  

## <a name="week-of-may-13-2019"></a>Settimana del 13 maggio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Aggiornamento del metodo di autenticazione e dell'installazione dell'app Portale aziendale per i criteri di Intune  <!-- 1927359 idready wnready-->
Nei dispositivi già registrati tramite l'Assistente configurazione con uno dei metodi di registrazione dei dispositivi aziendali di Apple, Intune non supporterà più l'app Portale aziendale se installata manualmente dagli utenti finali dall'App Store. Questa modifica è rilevante solo quando si esegue l'autenticazione con Apple Setup Assistant durante la registrazione. Questa modifica riguarda inoltre solo i dispositivi iOS registrati tramite:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

Gli utenti riceveranno un errore se installano l'app Portale aziendale dall'App Store e quindi provano a registrare i dispositivi tramite tale app. È previsto che questi dispositivi usino l'app Portale aziendale solo quando ne è stato eseguito il push automaticamente da Intune durante la registrazione. I profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Se si vuole che gli utenti dei dispositivi DEP dispongano dell'app Portale aziendale, è necessario specificare le preferenze in un profilo di registrazione. 

Inoltre, la schermata **Identifica il dispositivo** nel Portale aziendale iOS è in fase di rimozione. Di conseguenza, gli amministratori che vogliono abilitare l'accesso condizionale o distribuire le app aziendali devono aggiornare il profilo di registrazione DEP. Questo requisito si applica solo se la registrazione DEP viene autenticata con Assistente configurazione. In tal caso, è necessario eseguire il push del Portale aziendale nel dispositivo. A tale scopo, scegliere **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token > **Profili** > scegliere un profilo > **Proprietà** > impostare **Installa il Portale aziendale** su **Sì**.

Per installare il Portale aziendale nei dispositivi DEP già registrati, si dovrà passare a Intune > App client ed eseguirne il push come app gestita con i criteri di configurazione delle app. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>Configurare come gli utenti finali aggiornano un'app line-of-business usando i criteri di protezione delle app <!-- 3568384 -->
È ora possibile configurare dove gli utenti finali possono ottenere una versione aggiornata di un'app line-of-business. Gli utenti finali visualizzeranno questa funzionalità nella finestra di dialogo di avvio condizionale **Versione minima dell'app**, in cui verrà chiesto loro di eseguire l'aggiornamento a una versione minima dell'app line-of-business. È necessario fornire queste informazioni dettagliate relative all'aggiornamento come parte dei criteri di protezione dell'app line-of-business (APP). Questa funzionalità è disponibile per iOS e Android. In iOS questa funzionalità richiede che l'app venga integrata (o sottoposta a wrapping tramite lo strumento di wrapping) con Intune SDK per iOS 10.0.7 o versioni successive. In Android questa funzionalità richiede la versione del Portale aziendale più recente. Per configurare il modo in cui un utente finale aggiorna un'app line-of-business, l'app necessita che venga inviato un criterio di configurazione dell'app gestita con la chiave `com.microsoft.intune.myappstore`. Il valore inviato definirà da quale archivio l'utente finale scaricherà l'app. Se l'app viene distribuita tramite il portale aziendale, il valore deve essere `CompanyPortal`. Per qualsiasi altro archivio, è necessario immettere un URL completo.

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>Script di PowerShell per l'estensione di gestione di Intune  <!-- 3734186 idready -->
È possibile configurare gli script di PowerShell per l'esecuzione con privilegi di amministratore dell'utente nel dispositivo. Per altre informazioni, vedere [Usare gli script di PowerShell nei dispositivi Windows 10 in Intune](intune-management-extension.md) e [Gestione delle app Win32](apps-win32-app-management.md).

#### <a name="android-enterprise-app-management----4459905---"></a>Gestione delle app Android Enterprise <!-- 4459905 -->
Per facilitare la configurazione e l'uso delle funzionalità di gestione di Android Enterprise per gli amministratori IT, Intune aggiungerà automaticamente quattro app comuni correlate a Android Enterprise alla console di amministrazione di Intune. Le quattro app per Android Enterprise sono le seguenti:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usata per gli scenari di Android Enterprise completamente gestiti.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)**  - Consente di accedere agli account se si usa la verifica a due fattori.
- **[Portale aziendale di Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usare per gli scenari con criteri di protezione app e profili di lavoro di Android Enterprise.
- [Schermata iniziale gestita](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Usata per gli scenari di Android Enterprise dedicati/in modalità a schermo intero.

In precedenza, gli amministratori IT dovevano trovare e approvare manualmente queste app in [Google Play Store gestito](https://play.google.com/store/apps) durante l'installazione. Questa modifica rimuove i passaggi manuali precedenti per consentire ai clienti di usare più facilmente e velocemente le funzionalità di gestione di Android Enterprise.

Gli amministratori IT noteranno che queste quattro app vengono aggiunte automaticamente all'elenco di app di Intune in occasione della prima connessione del tenant di Intune a Google Play gestito. Per altre informazioni, vedere [Connettere l'account di Intune all'account di Google Play gestito](connect-intune-android-enterprise.md). Per i tenant già connessi o che usano già Android Enterprise, gli amministratori non devono eseguire alcuna operazione. Queste quattro app diventeranno disponibili automaticamente entro 7 giorni del completamento della distribuzione dell'aggiornamento del servizio di maggio 2019.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>Connettore di certificati PFX per Microsoft Intune aggiornato  <!-- 1533038 -->
È stato rilasciato un aggiornamento per il [Connettore del certificato PFX per Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) che risolve un problema a causa del quale i certificati PFX esistenti continuano a essere rielaborati e di conseguenza il connettore smette di elaborare le nuove richieste.

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Attività di sicurezza di Intune per Defender ATP (in anteprima pubblica)     <!-- 3208597 -->
Nella fase di anteprima pubblica, è possibile usare Intune per gestire le [attività di sicurezza per Microsoft Defender Advanced Threat Protection (ATP)](atp-manage-vulnerabilities.md). L'integrazione con ATP aggiunge un approccio basato sui rischi per individuare, classificare e correggere gli errori di configurazione e le vulnerabilità degli endpoint, riducendo il tempo tra l'individuazione e la mitigazione.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10 <!-- 3617671   idstaged-->
Molti dispositivi Windows 10 e versioni successive hanno chipset Trusted Platform Module (TPM). Questo aggiornamento include una nuova impostazione di conformità che controlla la versione del chip TPM del dispositivo. 

Questa impostazione è descritta in [Impostazioni dei criteri di conformità per i dispositivi Windows 10 e versioni successive](compliance-policy-create-windows.md#device-security).

Si applica a: Windows 10 e versioni successive

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>Impedire agli utenti finali di modificare l'hotspot personale e disabilitare la registrazione nel server Siri nei dispositivi iOS <!-- 4097904   -->  
Creare un profilo di limitazioni del dispositivo nel dispositivo iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni, che è possibile configurare:

- **App predefinite**: Registrazione lato server per i comandi di Siri
- **Wireless**: Modifica dell'utente dell'hotspot personale (solo con supervisione)

Per visualizzare queste impostazioni, passare alle [impostazioni predefinite dell'app per iOS](device-restrictions-ios.md#built-in-apps) e alle [impostazioni wireless per iOS](device-restrictions-ios.md#wireless).

Si applica a: iOS 12.2 e versioni successive

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>Nuove impostazioni di limitazione del dispositivo per l'app Classroom per i dispositivi macOS <!-- 4097905   --> 
È possibile creare un profilo di configurazione del dispositivo per i dispositivi macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni dell'app Classroom, la possibilità di bloccare gli screenshot e la possibilità di disabilitare la Libreria foto di iCloud.

Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-macos.md).

Si applica a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>L'impostazione della password iOS per l'accesso all'App Store è stata rinominata<!-- 4557891  -->
L'impostazione **Password per l'accesso all'App Store** è stata rinominata in **Require iTunes Store password for all purchases** (Richiedere password iTunes Store per tutti gli acquisti) (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi**).

Per visualizzare le impostazioni disponibili, passare alle [impostazioni iOS di App Store, visualizzazione documenti, giochi](device-restrictions-ios.md#app-store-doc-viewing-gaming).

Si applica a: iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Baseline di Microsoft Defender Advanced Threat Protection (anteprima)  <!--  3754134 -->
È stata aggiunta un'anteprima della baseline di sicurezza per le impostazioni di [Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md). Questa baseline è disponibile quando l'ambiente soddisfa i prerequisiti per l'uso di [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>La pagina relativa allo stato della registrazione di Windows è ora disponibile a livello generale <!-- 3605348 -->
La pagina relativa allo stato della registrazione non è più in fase di anteprima. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Aggiornamento dell'interfaccia utente di Intune - Creazione del profilo di registrazione Autopilot  <!-- 4593669 -->
L'interfaccia utente per la creazione di un profilo di registrazione Autopilot è stata aggiornata per allinearsi agli stili dell'interfaccia utente di Azure. Per altre informazioni, vedere [Create an Autopilot enrollment profile](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile) (Creare un profilo di registrazione Autopilot). Più avanti, altri scenari di Intune verranno aggiornati a questo nuovo stile dell'interfaccia utente.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>Abilitare Reimpostazione di AutoPilot per tutti i dispositivi Windows <!-- 4225665 -->
Reimpostazione di AutoPilot ora funziona per tutti i dispositivi Windows, anche quelli non configurati per l'uso della pagina relativa allo stato della registrazione. Se durante la registrazione iniziale del dispositivo non è stata configurata una pagina relativa allo stato della registrazione per il dispositivo, il dispositivo passerà direttamente al desktop dopo l'accesso. Potrebbero essere necessarie fino a otto ore per la sincronizzazione e la visualizzazione come conforme in Intune. Per altre informazioni, vedere [Reimpostare i dispositivi con Reimpostazione di Windows Autopilot remota](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>Formato IMEI esatto non richiesto durante la ricerca in tutti i dispositivi <!--30407680 -->
Non è necessario includere spazi nei numeri IMEI quando si esegue una ricerca in **Tutti i dispositivi**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>L'eliminazione di un dispositivo nel portale Apple si rifletterà nel portale di Intune <!--2489996 -->
Se un dispositivo viene eliminato dai portali di Device Enrollment Program di Apple o Apple Business Manager, il dispositivo verrà automaticamente eliminato da Intune durante la sincronizzazione successiva.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>La pagina di stato della registrazione ora tiene traccia delle app Win32 <!-- 2714451 -->
Ciò si applica solo ai dispositivi che eseguono Windows 10 versione 1903 e successive. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Reimpostare e cancellare i dispositivi in blocco usando l'API Graph <!-- 3295288 -->
È ora possibile reimpostare e cancellare un massimo di 100 dispositivi in blocco tramite l'API Graph.


### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>Il report di crittografia non è più disponibile come anteprima pubblica   <!-- 4587546      -->
Il [report per BitLocker e la crittografia dei dispositivi](encryption-monitor.md) è ora disponibile a livello generale e non più come anteprima pubblica. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>Impostazioni biometriche e della firma di Outlook per dispositivi iOS e Android <!-- 4050557 -->
È ora possibile specificare se la firma predefinita è abilitata in Outlook nei dispositivi iOS e Android. Inoltre, è possibile scegliere se consentire agli utenti di modificare l'impostazione biometrica in Outlook in iOS.

## <a name="week-of-may-6-2019"></a>Settimana del 6 maggio 2019 

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>Supporto del controllo di accesso alla rete per F5 Access per dispositivi iOS <!-- 4500808 -->

F5 ha rilasciato un aggiornamento di BIG-IP 13 che abilita la funzionalità di controllo di accesso alla rete per F5 Access su iOS in Intune. Per usare questa funzionalità:

- Aggiornare BIG-IP alla versione 13.1.1.5. BIG-IP 14 non è supportata.
- Integrare BIG-IP con Intune per il controllo di accesso alla rete. Vedere la procedura in [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Controllare l'impostazione di **Abilita il controllo accesso alla rete** nel profilo VPN in Intune.

Per vedere l'impostazione disponibile, passare a [Configurare le impostazioni VPN nei dispositivi iOS](vpn-settings-ios.md).

Si applica a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>Connettore di certificati PFX per Microsoft Intune aggiornato <!-- doc-vso 1521237  -->  
È stato rilasciato un aggiornamento del [connettore di certificati PFX per Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors) in cui l'intervallo di polling è stato ridotto da 5 minuti a 30 secondi.

## <a name="week-of-april-22-2019"></a>Settimana del 22 aprile 2019

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Usare Compliance Manager per creare valutazioni per Microsoft Intune<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager) (apre un altro sito Microsoft) è uno strumento di valutazione dei rischi basato su flussi di lavoro disponibile in Microsoft Service Trust Portal. Consente di tenere traccia, assegnare e verificare le attività di conformità alle normative dell'organizzazione relativamente ai servizi Microsoft. È possibile creare una valutazione personalizzata della conformità con Office 365, Azure, Dynamics, Servizi professionali e Intune. Intune include due valutazioni: FFIEC e GDPR.

Compliance Manager consente di concentrare l'attenzione analizzando in dettaglio i controlli, sia quelli gestiti da Microsoft che quelli gestiti dall'organizzazione. È possibile completare le valutazioni per poi esportarle e stamparle.

La conformità alle normative [FFIEC (Federal Financial Institutions Examination Council)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (apre un altro sito Microsoft) prevede un set di standard per l'online banking emanati da FFIEC. È la valutazione più richiesta per gli istituti finanziari che usano Intune. Interpreta in che modo Intune consente di soddisfare le linee guida per la sicurezza informatica FFIEC relative ai carichi di lavoro del cloud pubblico. La valutazione FFIEC di Intune è la seconda valutazione FFIEC in Compliance Manager.

Nell'esempio seguente è possibile visualizzare i controlli FFIEC in dettaglio. Microsoft copre 64 controlli. L'organizzazione è responsabile dei 12 controlli rimanenti.

![Esempio di valutazione di Intune per FFIEC, che include le azioni dei clienti e le azioni di Microsoft](./media/intune-ffiec-assessment-status.png)

Il [Regolamento generale sulla protezione dei dati (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (apre un altro sito Microsoft) è una normativa dell'Unione Europea (UE) che tutela i diritti dei singoli utenti e i relativi dati personali. Il GDPR è la valutazione più richiesta per garantire la conformità con le normative sulla privacy. 

Nell'esempio seguente sono illustrati i controlli GDPR in dettaglio. Microsoft copre 49 controlli. L'organizzazione è responsabile dei 66 controlli rimanenti.

![Esempio di valutazione di Intune per il GDPR, che include le azioni dei clienti e le azioni di Microsoft](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>Settimana del 15 aprile 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Crittografia OpenSSL per i criteri di protezione delle app per Android <!-- 3747362 -->
I criteri di Protezione app di Intune nei dispositivi Android usano ora una libreria di crittografia OpenSSL compatibile con FIPS 140-2. Per altre informazioni, vedere la sezione [Crittografia](app-protection-policy-settings-android.md#encryption) di [Impostazioni dei criteri di protezione delle app di Android in Microsoft Intune](app-protection-policy-settings-android.md).

#### <a name="enable-win32-app-dependencies----2617348----"></a>Abilitare le dipendenze delle app Win32 <!-- 2617348  -->
Gli amministratori possono richiedere che vengano installate altre app come dipendenze prima di installare l'app Win32. In particolare, il dispositivo deve installare le app dipendenti prima di installare l'app Win32. In Intune selezionare **App client** > **App** > **Aggiungi** per visualizzare il pannello **Aggiungi app**. Selezionare **App di Windows (Win32)** come **Tipo di app**. Dopo aver aggiunto l'app, è possibile selezionare **Dipendenze** per aggiungere le app dipendenti che devono essere installate prima di poter installare l'app Win32. Per altre informazioni, vedere [Intune autonomo - Gestione di app Win32](apps-win32-app-management.md). 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>Informazioni di installazione sulla versione delle app per le app di Microsoft Store per le aziende <!-- 3537391   -->
I report di installazione delle app includono informazioni sulla versione delle app per le app di Microsoft Store per le aziende. In Intune selezionare **App client** > **App**. Selezionare un'**app di Microsoft Store per le aziende** e quindi selezionare **Stato dell'installazione del dispositivo** nella sezione **Monitoraggio**.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Aggiunte alle regole relative ai requisiti delle app Win32 <!-- 3676883   -->
È possibile creare regole relative ai requisiti basate su script di PowerShell, valori del Registro di sistema e informazioni del file system. In Intune selezionare **App client** > **App** > **Aggiungi**. Quindi selezionare **App di Windows (Win32)** come **Tipo di App** nel pannello **Aggiungi app**.  Selezionare **Requisiti** > **Aggiungi** per configurare regole aggiuntive relative ai requisiti. Selezionare quindi **Tipo di file**, **Registro** o **Script** come **Tipo di requisito**. Per altre informazioni, vedere [Gestione di app Win32](apps-win32-app-management.md).

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Configurare le app Win32 da installare in dispositivi aggiunti ad Azure AD registrati in Intune <!-- 3695227  -->
È possibile assegnare le app Win32 da installare in dispositivi aggiunti ad Azure AD registrati in Intune. Per altre informazioni sulle app Win32 in Intune, vedere [Gestione di app Win32](apps-win32-app-management.md).

#### <a name="device-overview-shows-primary-user---794259----"></a>La panoramica del dispositivo mostra l'utente primario <!--794259  -->
Nella pagina Panoramica del dispositivo verrà visualizzato l'utente primario, detto anche utente affinità utente-dispositivo. Per visualizzare l'utente primario per un dispositivo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo. L'utente primario verrà visualizzato nella parte superiore della pagina **Panoramica**.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Segnalazione app Google Play gestite per dispositivi del profilo di lavoro Android Enterprise <!-- 4105925  -->
Per le app Google Play gestite distribuite nei dispositivi del profilo di lavoro Android Enterprise, è possibile visualizzare il numero di versione specifico dell'app installata in un dispositivo. Questo vale solo per le app richieste.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>Tastiere di terze parti iOS <!-- 4111843   -->
Il supporto per i criteri di protezione app di Intune per l'impostazione delle **tastiere di terze parti** per iOS non è più disponibile a causa di una modifica della piattaforma iOS. Non sarà possibile configurare questa impostazione nella console di amministrazione di Intune e non verrà applicata nel client in Intune App SDK.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>Configurare le impostazioni di accesso e controllare le opzioni di riavvio nei dispositivi macOS <!-- 1210083  -->
Nei dispositivi macOS è possibile creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni della finestra di accesso, ad esempio per la visualizzazione di un banner personalizzato, la scelta della modalità di accesso di un utente, la possibilità di visualizzare o nascondere le impostazioni di risparmio energia e altro ancora.

Per visualizzare queste impostazioni, vedere [Impostazioni relative alle funzionalità dei dispositivi macOS in Intune](macos-device-features-settings.md).

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>Configurare le impostazioni Wi-Fi nei dispositivi dedicati del proprietario del dispositivo Android Enterprise in esecuzione in modalità tutto schermo con più app <!--3041940  -->
È possibile abilitare le impostazioni per il proprietario del dispositivo Android Enterprise in caso di esecuzione come dispositivo dedicato in modalità tutto schermo con più app. In questo aggiornamento è possibile consentire agli utenti di configurare e connettersi alle reti Wi-Fi (**Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo > **Dispositivi dedicati** > **Modalità tutto schermo**: **Più app** > **Configurazione Wi-Fi**). 

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

Si applica a: Dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>Configurare le impostazioni Bluetooth e l'associazione nei dispositivi dedicati del proprietario del dispositivo Android Enterprise in esecuzione in modalità tutto schermo con più app <!-- 3041941  -->
È possibile abilitare le impostazioni per il proprietario del dispositivo Android Enterprise in caso di esecuzione come dispositivo dedicato in modalità tutto schermo con più app. In questo aggiornamento è possibile consentire agli utenti finali di abilitare il Bluetooth e associare dispositivi tramite Bluetooth (**Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo > **Dispositivi dedicati** > **Modalità tutto schermo**: **Multi-app** > **Configurazione Bluetooth**). 

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

Si applica a: Dispositivi dedicati Android Enterprise in esecuzione in modalità tutto schermo con più app

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Creare e usare profili di configurazione dei dispositivi OEMConfig in Intune <!-- 3305883  -->
In questo aggiornamento Intune supporta la configurazione di dispositivi Android Enterprise con OEMConfig. In particolare, è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android Enterprise usando OEMConfig (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma).

Il supporto per gli OEM è attualmente su base per OEM. Se una specifica app OEMConfig non è disponibile nell'elenco delle app OEMConfig, contattare `IntuneOEMConfig@microsoft.com`.

Per altre informazioni su questa funzionalità, passare a [Use and manage Android Enterprise devices with OEMConfig in Microsoft Intune](android-oem-configuration-overview.md) (Usare e gestire i dispositivi Android Enterprise con OEMConfig in Microsoft Intune).

Si applica a: Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Notifiche di Windows Update  <!-- 3316758, 3316782  -->
Sono state aggiunte due *impostazioni dell'esperienza utente* alle configurazioni degli anelli di Windows Update che è possibile gestire dalla console di Intune. È ora possibile:
- Impedire o consentire agli utenti di [verificare la disponibilità di aggiornamenti per Windows](windows-update-settings.md#block-user-from-scanning-for-windows-updates).
- Gestire il [livello di notifica di Windows Update](windows-update-settings.md#windows-update-notification-level) visibile agli utenti.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Nuove impostazioni relative alle restrizioni dei dispositivi per il proprietario del dispositivo Android Enterprise <!-- 3574254  -->
Nei dispositivi Android Enterprise è possibile creare un profilo di restrizione dei dispositivi per consentire o limitare le funzionalità, impostare regole per le password e altro ancora (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo). 

Questo aggiornamento include nuove impostazioni delle password, consente l'accesso completo alle app in Google Play Store per i dispositivi completamente gestiti e altro ancora. Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md). 

Si applica a: Dispositivi completamente gestiti Android Enterprise

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10 <!-- 3617671 -->

Questa funzionalità è in ritardo ed è pianificata per essere rilasciata più avanti.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Modifiche all'interfaccia utente aggiornate per il browser Microsoft Edge in dispositivi Windows 10 e versioni successive <!-- 3775833   -->
Quando si crea un profilo di configurazione del dispositivo, è possibile consentire o limitare l'uso delle funzionalità di Microsoft Edge in dispositivi Windows 10 e versioni successive (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma, > **Limitazioni del dispositivo** per il tipo di profilo > **Browser Microsoft Edge**). In questo aggiornamento le impostazioni di Microsoft Edge sono più descrittive e più semplici da comprendere. 

Per visualizzare queste funzionalità, passare alle [impostazioni relative alle restrizioni per i dispositivi per il browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser).

Si applica a: Windows 10 e versioni successive

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Supporto esteso per i dispositivi Android Enterprise completamente gestiti (anteprima)  <!--   3903241, 3903244, 3903246   -->
Ancora in anteprima pubblica, il supporto per i dispositivi Android Enterprise completamente gestiti ([annunciato nel gennaio 2019](whats-new.md#week-of-january-14-2019)) è stato esteso per includere le funzionalità seguenti: 

- Nei dispositivi dedicati e completamente gestiti è possibile creare [criteri di conformità](compliance-policy-create-android-for-work.md) per includere regole per le password e requisiti del sistema operativo (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android Enterprise** per la piattaforma > **Proprietario del dispositivo** per il tipo di profilo). 

  Nei dispositivi dedicati il dispositivo potrebbe essere visualizzato come **Non conforme**. L'accesso condizionale non è disponibile nei dispositivi dedicati. Assicurarsi di completare qualsiasi attività o operazione per garantire che i dispositivi dedicati siano conformi con i criteri assegnati.

- [Accesso condizionale](conditional-access.md): i criteri di accesso condizionale che si applicano ad Android sono applicabili anche ai dispositivi Android Enterprise completamente gestiti. Gli utenti possono ora registrare i propri dispositivi completamente gestiti in Azure Active Directory tramite l'**app Microsoft Intune**. Quindi, visualizzare e risolvere eventuali problemi di conformità per accedere alle risorse aziendali.

- Nuova app per l'utente finale (app Microsoft Intune): è disponibile una nuova app per l'utente finale per i dispositivi Android completamente gestiti chiamata **Microsoft Intune**. La nuova app è leggera e moderna e offre funzionalità simili a quelle dell'app Portale aziendale, ma per i dispositivi completamente gestiti. Per altre informazioni, vedere l'[app Microsoft Intune in Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune).

Per configurare dispositivi Android completamente gestiti, passare a **Registrazione del dispositivo** > **Registrazione Android** > **Dispositivi utente completamente gestiti di proprietà aziendale**. Il supporto per i dispositivi Android completamente gestiti rimane disponibile in anteprima e alcune funzionalità di Intune potrebbero non essere completamente funzionali.  

Per altre informazioni su questa anteprima, vedere il blog [Microsoft Intune announces Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged) (Microsoft Intune annuncia la versione Preview 2 per i dispositivi Android Enterprise completamente gestiti).


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>Configurare il profilo per ignorare alcune schermate durante l'esecuzione di Assistente configurazione <!-- 2276470  wnstaged-->
Quando si crea un profilo di registrazione macOS, è possibile configurarlo per ignorare tutte le schermate seguenti quando un utente esegue Assistente configurazione:
- Aspetto
- Display Tone (Tono schermo)
- iCloudStorage Se si crea un nuovo profilo o si modifica un profilo, le schermate da ignorare selezionate devono essere sincronizzate con il server MDM di Apple.  Gli utenti possono eseguire una sincronizzazione manuale dei dispositivi in modo da evitare ritardi nell'aggiornamento delle modifiche del profilo.
Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS con Device Enrollment Program o Apple School Manager](device-enrollment-program-enroll-macos.md).

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>Denominazione in blocco dei dispositivi durante la registrazione di dispositivi iOS aziendali<!--3566569  -->
Quando si usa uno dei metodi di registrazione aziendali di Apple (DEP/ABM/ASM), è possibile impostare un formato del nome del dispositivo in modo da denominare automaticamente i dispositivi iOS in ingresso. È possibile specificare un formato che include il tipo di dispositivo e il numero di serie nel modello. A tale scopo, scegliere **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > **Selezionare un token** >**Crea profilo** > **Device naming format (Formato di denominazione dispositivi)** . È possibile modificare i profili esistenti, ma il nome sarà applicato solo ai dispositivi appena sincronizzati.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>Messaggio di timeout predefinito aggiornato nella pagina Stato della registrazione <!-- 3959331 -->
È stato aggiornato il messaggio di timeout predefinito che gli utenti vedono quando la pagina Stato della registrazione (ESP) supera il valore di timeout specificato nel profilo ESP. Il nuovo messaggio predefinito è quello che gli utenti vedono e consente di comprendere le azioni successive da eseguire durante la distribuzione ESP.  

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="retire-noncompliant-devices-----1827291-----"></a>Ritirare i dispositivi non conformi  <!-- 1827291   -->
Questa funzionalità è stata posticipata ed è pianificata per una versione futura.


### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Le modifiche al data warehouse di Intune V1.0 si riflettono nella versione beta <!-- 4403765 -->
Quando V1.0 è stato introdotto per la prima volta nella versione 1808, c'erano delle differenze sostanziali rispetto alla versione beta dell'API. Nella versione 1903 queste modifiche si rifletteranno nella versione beta dell'API. Se si dispone di report importanti che usano la versione beta dell'API, è consigliabile passare tali report a V1.0 per evitare modifiche significative. Per altre informazioni, vedere [Registro modifiche per l'API data warehouse di Intune](reports-changelog.md#1903-part-2).

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>Monitorare lo stato della baseline di sicurezza (anteprima pubblica) <!-- 3082047 --> 
È stata aggiunta una [visualizzazione per categoria](security-baselines-monitor.md#per-category-view) per il monitoraggio delle baseline di sicurezza (le baseline di sicurezza rimangono in anteprima). La visualizzazione per categoria consente di visualizzare ogni categoria dalla baseline con la percentuale di dispositivi che rientrano in ogni gruppo di stato per tale categoria. È ora possibile visualizzare quanti dispositivi non corrispondono alle singole categorie, non sono configurati correttamente o non sono applicabili.

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Tag di ambito per i token VPP Apple <!--2371886  -->
È ora possibile aggiungere tag di ambito per i token VPP Apple. Solo gli utenti assegnati con lo stesso tag di ambito avranno accesso al token VPP Apple con tale tag. Le app VPP e gli eBook acquistati con tale token ereditano i tag di ambito. Per altre informazioni sui tag di ambito, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito](scope-tags.md).







## <a name="week-of-april-1-2019"></a>Settimana del 1 aprile 2019

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>Connettori di certificati aggiornati  <!-- ICM 113304612 -->
Sono stati rilasciati aggiornamenti per il [connettore di certificati di Intune e il connettore di certificati PFX per Microsoft Intune](certficates-pfx-configure.md#whats-new-for-connectors). Le nuove versioni consentono di risolvere diversi problemi noti.  

### <a name="app-management"></a>Gestione delle app

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>Aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS <!-- 2536024 -->
La home page dell'app Portale aziendale per i dispositivi iOS è stata riprogettata. Con questa modifica, la home page seguirà meglio i modelli dell'interfaccia utente iOS, oltre a garantire un'individuabilità migliorata per le app e gli eBook.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Modifiche alla registrazione nel Portale aziendale per gli utenti dei dispositivi iOS 12 <!--3448635 -->  
Le schermate e i passaggi per la registrazione nel Portale aziendale per iOS sono stati aggiornati per un miglior allineamento con le modifiche della registrazione MDM rilasciate in Apple iOS 12.2. Il flusso di lavoro aggiornato richiede agli utenti di:  

* Consentire a Safari di aprire il sito Web del Portale aziendale e scaricare il profilo di gestione prima di tornare all'app Portale aziendale.  
* Aprire l'app Impostazioni per installare il profilo di gestione nel dispositivo in uso.
* Tornare all'app Portale aziendale per completare la registrazione.  

Per le schermate e i passaggi per la registrazione aggiornati, vedere [Registrare il dispositivo iOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios).  

## <a name="week-of-march-25-2019"></a>Settimana del 25 marzo 2019

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Supporto per l'app di conformità di Power BI dal pannello Data warehouse in Microsoft Intune <!-- 4260871 -->
In precedenza, il collegamento **Scarica il file di Power BI** nel pannello **Data warehouse di Intune** consentiva di scaricare un report Data warehouse di Intune (file con estensione pbix). Questo report è stato sostituito con l'app di conformità di Power BI. L'app di conformità di Power BI non richiederà uno speciale caricamento o installazione. Verrà aperta direttamente nel portale online di Power BI e visualizzerà i dati per il tenant di Intune in base alle credenziali specificate. In Intune selezionare il collegamento **Configura il data warehouse di Intune** sul lato destro del pannello di Intune. Quindi, fare clic su **Scarica l'app Power BI**. Per altre informazioni, vedere [Connettersi al data warehouse con Power BI](reports-proc-get-a-link-powerbi.md).

## <a name="week-of-march-18-2019"></a>Settimana del 18 marzo 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Distribuire Microsoft Visio e Microsoft Project <!-- 3725386  -->
È ora possibile distribuire Microsoft Visio Pro for Office 365 e il client desktop di Microsoft Project Online come app indipendenti in dispositivi Windows 10 usando Microsoft Intune, se si dispone delle licenze per queste app. Da Intune selezionare **App client** > **App** > **Aggiungi** per visualizzare il pannello **Aggiungi app**. Nel pannello **Aggiungi app** selezionare **Windows 10** come **Tipo di app**. Quindi, selezionare **Configura la suite di app** per selezionare le app da installare. Per altre informazioni sulle app di Office 365 per i dispositivi Windows 10, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 per la modifica del nome del prodotto <!-- 3593653  -->
**Microsoft Visio Pro for Office 365** sarà ora noto come **Microsoft Visio Online Piano 2**.  Per altre informazioni su Microsoft Visio, vedere [Visio Online Piano 2](https://products.office.com/visio/visio-online-plan-2). Per altre informazioni sulle app di Office 365 per i dispositivi Windows 10, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Impostazione del limite di caratteri per i criteri di Protezione app di Intune <!-- 3291302  -->
Gli amministratori di Intune possono specificare un'eccezione per l'impostazione del criterio **Limita le operazioni taglia, copia e incolla con le altre app** dell'app Intune.  L'amministratore può specificare il numero di caratteri che è possibile tagliare o copiare da un'app gestita. Questa impostazione consente la condivisione del numero specificato di caratteri in qualsiasi app, indipendentemente dall'impostazione "Limita le operazioni taglia, copia e incolla con le altre app". Si noti che la versione dell'app Portale aziendale Intune per Android richiede la versione 5.0.4364.0 o successive. Per altre informazioni, vedere le sezioni sulla [protezione dei dati iOS](app-protection-policy-settings-ios.md#data-protection) e sulla [protezione dei dati Android](app-protection-policy-settings-android.md#data-protection) ed [Esaminare i log di protezione delle app client](app-protection-policy-settings-log.md#app-protection-policy-settings).

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Strumento di distribuzione di Office (ODT) XML per la distribuzione di Office ProPlus <!-- 3192477   -->
Sarà possibile includere lo Strumento di distribuzione di Office (ODT) XML quando si crea un'istanza di Office Pro Plus nella console di amministrazione di Intune. In questo modo si garantirà una maggiore possibilità di personalizzazione se le opzioni dell'interfaccia utente di Intune esistenti non soddisfano le proprie esigenze. Per altre informazioni, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](https://docs.microsoft.com/intune/apps-add-office365) e [Opzioni di configurazione per lo Strumento di distribuzione di Office](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool).

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>Le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente <!-- 1429026  -->
Nell'app Portale aziendale Windows le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente in base al colore dominante dell'icona, se rilevabile. Se applicabile, questo sfondo sostituirà il bordo grigio precedentemente visibile nei riquadri delle app. Gli utenti visualizzeranno questa modifica nelle versioni del Portale aziendale successive alla 10.3.3451.0.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Installare le app disponibili tramite l'app Portale aziendale dopo la registrazione in blocco di Windows <!-- 2751523   -->
I dispositivi Windows registrati in Intune tramite la [registrazione in blocco di Windows](windows-bulk-enroll.md) (pacchetti di provisioning) potranno usare l'app Portale aziendale per installare le app disponibili. Per altre informazioni sull'app Portale aziendale, vedere [Aggiungere manualmente l'app Portale aziendale di Windows 10](store-apps-company-portal-app.md) e [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md).

> [!Note]
> Questa funzionalità non è ancora completamente distribuita per tutti i clienti. Se non si riesce a usare il Portale aziendale nei dispositivi registrati in blocco, potrebbe essere necessario attendere fino a quando questa modifica non sarà implementata per il proprio account.

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>L'app Microsoft Teams può essere selezionata nell'ambito della suite di app Office <!-- 3828932  -->
L'app Microsoft Teams può essere inclusa o esclusa nell'ambito dell'installazione della suite di app Office Pro Plus. Questa funzionalità può essere usata per Office Pro Plus numero di build 16.0.11328.20116+. L'utente deve disconnettersi e quindi accedere al dispositivo per completare l'installazione. In Intune selezionare **App client** > **App** > **Aggiungi**. Selezionare uno dei tipi di app **Famiglia di prodotti Office 365** e quindi selezionare **Configura la suite di app**.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Avviare automaticamente un'app durante l'esecuzione di più app in modalità tutto schermo nei dispositivi Windows 10 e versioni successive <!-- 2351390 -->

Nei dispositivi Windows 10 e versioni successive è possibile eseguire un dispositivo in modalità tutto schermo ed eseguire molte app. In questo aggiornamento è disponibile un'impostazione **Avvio automatico** (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Modalità tutto schermo** per il tipo di profilo > **Più app in modalità tutto schermo**). Usare questa impostazione per avviare automaticamente un'app quando l'utente accede al dispositivo.

Per visualizzare un elenco e una descrizione di tutte le impostazioni della modalità tutto schermo, vedere [Impostazioni dei dispositivi Windows 10 e versioni successive per l'esecuzione in modalità tutto schermo in Intune](kiosk-settings-windows.md).

Si applica a: Windows 10 e versioni successive

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>I log operativi mostrano anche i dettagli dei dispositivi non conformi <!-- 4063755  -->
Quando si effettua il routing dei log di Intune alle funzionalità di monitoraggio di Azure, è anche possibile indirizzare i log operativi. In questo aggiornamento i log operativi forniscono anche informazioni sui dispositivi non conformi. 

Per altre informazioni su questa funzionalità, vedere [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics in Intune](review-logs-using-azure-monitor.md).

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>Indirizzare i log a Monitoraggio di Azure in altri carichi di lavoro di Intune <!-- 3804627 -->
In Intune è possibile indirizzare i log operativi e di controllo agli hub eventi, alla risorsa di archiviazione e a Log Analytics in Monitoraggio di Azure (**Intune** > **Monitoraggio** > **Impostazioni di diagnostica**). In questo aggiornamento è possibile indirizzare questi log in altri carichi di lavoro di Intune, tra cui conformità, configurazioni, app client e altro ancora. 

Per altre informazioni sul routing dei log a Monitoraggio di Azure, vedere [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics](review-logs-using-azure-monitor.md).

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Creare e usare estensioni di mobilità nei dispositivi Android Zebra in Intune <!-- 3305880   -->
In questo aggiornamento Intune supporta la configurazione di dispositivi Android Zebra. In particolare, è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android Zebra usando i profili delle estensioni di mobilità (MX) generati da StageNow (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android** per la piattaforma > **Profilo MX (solo Zebra)** per il tipo di profilo).

Per altre informazioni su questa funzionalità, vedere [Usare e gestire i dispositivi Zebra con le estensioni di mobilità in Intune](android-zebra-mx-overview.md).

Si applica a: Android

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Report di crittografia per i dispositivi Windows 10 (in anteprima pubblica)<!-- 2351538 -->  
Usare il nuovo [report di crittografia (anteprima)](encryption-monitor.md) per visualizzare informazioni dettagliate sullo stato della crittografia dei dispositivi Windows 10. I dettagli disponibili includono una versione TPM dei dispositivi, conformità e stato della crittografia, segnalazione errori e altro ancora.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Accedere alle chiavi di ripristino di BitLocker dal portale di Intune (in anteprima pubblica) <!-- 2351547   -->  
È ora possibile usare Intune per [visualizzare informazioni dettagliate](encryption-monitor.md) sull'ID chiave BitLocker e le chiavi di ripristino di BitLocker da Azure Active Directory.

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Supporto Microsoft Edge per gli scenari di Intune nei dispositivi iOS e Android <!-- 3411007 -->
Microsoft Edge supporterà tutti gli stessi scenari di gestione di Intune Managed Browser con l'aggiunta di miglioramenti all'esperienza utente finale. Le funzionalità aziendali di Microsoft Edge che vengono abilitate dai criteri di Intune includono doppia identità, integrazione dei criteri di protezione delle app, integrazione del proxy di applicazione di Azure e collegamenti gestiti ai Preferiti e alla home page. Per altre informazioni, vedere la sezione relativa al [supporto Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Supporto deprecato di Exchange Online/Intune Connector per i dispositivi solo EAS <!--3105122  -->
La console di Intune non supporta più la visualizzazione e la gestione dei dispositivi solo EAS connessi a Exchange Online con Intune Connector. In alternativa, sono disponibili le opzioni seguenti:
- Registrare i dispositivi nella gestione dei dispositivi mobili (MDM)
- Usare i criteri di Protezione app di Intune per gestire i dispositivi
- Usare i controlli di Exchange, come descritto in [Client e dispositivi mobili in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>Cercare un dispositivo specifico nella pagina Tutti i dispositivi tramite [nome] <!--4254930 -->
È ora possibile cercare un nome dispositivo esatto. Passare a **Intune** > **Dispositivi** > **Tutti i dispositivi** > nella casella di ricerca racchiudere il nome dispositivo con {} per cercare una corrispondenza esatta. Ad esempio, **{Dispositivo12345}** .

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>Supporto per connettori aggiuntivi nella pagina Stato tenant <!-- 3617202  -->
La [pagina Stato tenant](tenant-status.md) visualizza ora le informazioni sullo stato per altri connettori, tra cui *Windows Defender Advanced Threat Protection* (ATP) e altri connettori Mobile Threat Defense.

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Concedere l'accesso in sola lettura a Intune ad alcuni ruoli di Azure Active Directory <!-- 3637917  -->
È stato concesso l'accesso in sola lettura a Intune ai ruoli di Azure AD seguenti. Le autorizzazioni concesse con i ruoli di Azure AD sostituiscono quelle concesse con il controllo degli accessi in base al ruolo di Intune.

Accesso in sola lettura ai dati di controllo di Intune:

- Amministratore di conformità
- Amministratore dati di conformità

Accesso in sola lettura a tutti i dati di Intune:

- Amministratore della protezione
- Operatore di sicurezza
- Ruolo con autorizzazioni di lettura per la sicurezza

Per altre informazioni, vedere [Controllo degli accessi in base al ruolo](role-based-access-control.md).

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>Tag di ambito per i profili di provisioning delle app iOS <!--2934430   -->
È possibile aggiungere un tag di ambito a un profilo di provisioning di un'app iOS in modo che solo gli utenti al cui ruolo è già assegnato tale tag abbiano accesso al profilo di provisioning dell'app iOS. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito](scope-tags.md).

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>Tag di ambito per i criteri di configurazione delle app <!--2371891   -->
È possibile aggiungere un tag di ambito a un criterio di configurazione di un'app in modo che solo gli utenti al cui ruolo è già assegnato tale tag abbiano accesso al profilo di configurazione dell'app. I criteri di configurazione delle app possono solo essere destinati o associati alle app a cui è stato assegnato lo stesso tag di ambito. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo (RBAC) e i tag di ambito](scope-tags.md).

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>Supporto Microsoft Edge per gli scenari di Intune nei dispositivi iOS e Android <!-- 3411007 -->
Microsoft Edge supporterà tutti gli stessi scenari di gestione di Intune Managed Browser con l'aggiunta di miglioramenti all'esperienza utente finale. Le funzionalità aziendali di Microsoft Edge che vengono abilitate dai criteri di Intune includono doppia identità, integrazione dei criteri di protezione delle app, integrazione del proxy di applicazione di Azure e collegamenti gestiti ai Preferiti e alla home page. Per altre informazioni, vedere la sezione relativa al [supporto Microsoft Edge](app-configuration-managed-browser.md#microsoft-edge-support).

## <a name="week-of-february-25-2019"></a>Settimana del 25 febbraio 2019

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="intune-powershell-module----951068----"></a>Modulo PowerShell di Intune <!-- 951068  -->
Il modulo PowerShell di Intune, che offre il supporto per l'API di Intune attraverso Microsoft Graph, è ora disponibile in [Microsoft PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10).

- [Informazioni dettagliate sull'uso del modulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [Esempi di scenari per l'uso del modulo](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>Supporto migliorato per l'ottimizzazione recapito  <!--3183757  -->
È stato esteso il supporto in Intune per la configurazione dell'ottimizzazione recapito. È ora possibile configurare un elenco esteso di [impostazioni di Ottimizzazione recapito](delivery-optimization-settings.md) per i dispositivi in uso direttamente dalla console di Intune.


## <a name="week-of-february-18-2019"></a>Settimana del 18 febbraio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune userà le API di Google Play Protect nei dispositivi Android <!-- 2577355   -->
Alcuni amministratori IT devono affrontare un panorama BYOD in cui gli utenti finali possono finire per manomettere con jailbreak o root il proprio telefono cellulare. Questo comportamento, anche se non malintenzionato, comporta la disabilitazione di molti criteri di Intune impostati per proteggere i dati dell'organizzazione nei dispositivi degli utenti finali. Intune offre quindi il rilevamento per root e jailbreak sia per i dispositivi registrati, sia per quelli non registrati. Con questa versione, Intune introduce l'uso delle API di Google Play Protect per potenziare i controlli di rilevamento per root esistenti per i dispositivi non registrati. Anche se Google non condivide la totalità dei controlli di rilevamento per root eseguiti, queste API dovrebbero essere in grado di rilevare gli utenti che, per qualsiasi motivo, hanno manomesso con root i proprio dispositivi. I motivi possono spaziare dalla personalizzazione del dispositivo alla possibilità di ricevere i nuovi aggiornamenti del sistema operativo in dispositivi meno recenti. Sarà quindi possibile impedire a questi utenti di accedere ai dati aziendali oppure cancellare i relativi account aziendali dalle app abilitate da criteri. Per un valore aggiunto, l'amministratore IT può ora contare su diversi aggiornamenti dei report all'interno del pannello Protezione app di Intune: il report "Utenti contrassegnati" visualizza gli utenti rilevati tramite l'analisi dell'API SafetyNet di Google Play Protect e il report "Potentially Harmful Apps" (App potenzialmente dannose) visualizza le app rilevate tramite l'analisi dell'API Verify Apps di Google. Questa funzionalità è disponibile per Android.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>Informazioni sulle app Win32 disponibili nel pannello Risoluzione dei problemi <!-- 2617342   -->
Nel pannello **Risoluzione dei problemi** dell'app Intune è ora possibile raccogliere i file di log di eventuali errori di installazione di un'app Win32. Per altre informazioni sulla risoluzione dei problemi di installazione delle app, vedere [Risolvere i problemi di installazione delle app](troubleshoot-app-install.md) e [Risolvere i problemi delle app Win32](apps-win32-app-management.md#troubleshoot-win32-app-issues).

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>Dettagli sullo stato dell'app per le app iOS <!-- 3761235   -->
Sono disponibili nuovi messaggi di errore di installazione delle app relativi alle situazioni seguenti:
- Errore per le app VPP durante l'installazione in iPad condiviso
- Errore quando l'App Store è disabilitato
- Licenza VPP per l'app non trovata
- Errore di installazione delle app di sistema con il provider MDM
- Errore di installazione delle app quando il dispositivo è in modalità di dispositivo perso o in modalità tutto schermo
- Errore di installazione dell'app quando l'utente non è connesso all'App Store

In Intune selezionare **App client** > **App** > "Nome app" > **Stato dell'installazione del dispositivo**. I nuovi messaggi di errore saranno disponibili nella colonna **Dettagli stato**.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Nuova schermata Categorie di app nell'app Portale aziendale per Windows 10<!-- 3834780  -->
È stata aggiunta una nuova schermata denominata **Categorie di app** per migliorare l'esperienza di esplorazione e selezione delle app nel Portale aziendale per Windows 10. Gli utenti vedranno ora le proprie app ordinate in categorie, ad esempio **In evidenza**, **Istruzione** e **Produttività**. Questa modifica viene visualizzata nelle versioni del Portale aziendale 10.3.3451.0 e versioni successive. Per visualizzare la nuova schermata, vedere [Novità dell'interfaccia utente dell'app](https://docs.microsoft.com/intune/whats-new-app-ui). Per altre informazioni sulle app nel Portale aziendale, vedere [Installare e condividere app nel dispositivo](/intune-user-help/install-apps-cpapp-windows).  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>App di conformità di Power BI <!-- 1455231 doc-work-item -->
Accedere al data warehouse di Intune in Power BI Online usando l'app di [conformità di Intune (Data warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp). Con questa app di Power BI, è ora possibile accedere ai report creati in precedenza e condividerli senza alcuna configurazione e senza uscire dal Web browser. Per altre informazioni, vedere [Registro modifiche - App di conformità di Power BI](reports-changelog.md#power-bi-compliance-app).


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>Gli script di PowerShell possono essere eseguiti in un host a 64 bit in dispositivi a 64 bit <!-- 1862675   -->
Quando uno script di PowerShell viene aggiunto al profilo di configurazione di un dispositivo, lo script viene sempre eseguito in modalità 32 bit, anche in sistemi operativi a 64 bit. Con questo aggiornamento, un amministratore può eseguire lo script in un host di PowerShell a 64 bit in dispositivi a 64 bit (**Configurazione del dispositivo** > **Script di PowerShell** > **Aggiungi** > **Configura** > **Esegui lo script in un host di PowerShell a 64 bit**).

Per altri dettagli sull'uso di PowerShell, vedere [Script di PowerShell in Intune](intune-management-extension.md).

Si applica a: Windows 10 e versioni successive

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>Agli utenti macOS viene chiesto di aggiornare la password <!-- 1873216 -->
Intune applica l'impostazione **ChangeAtNextAuth** nei dispositivi macOS. Questa impostazione interessa gli utenti finali e i dispositivi che hanno criteri password di conformità o profili password di restrizione dei dispositivi. Agli utenti finali viene chiesto una volta di aggiornare la password. Questo prompt viene visualizzato ogni volta che un utente esegue per la prima volta un'attività che richiede l'autenticazione, ad esempio l'accesso al dispositivo. Agli utenti può essere chiesto di aggiornare la password anche quando eseguono operazioni che richiedono privilegi amministrativi, ad esempio quando si richiede l'accesso a Keychain. 

Eventuali modifiche ai criteri password nuovi o esistenti da parte dell'amministratore comportano una nuova richiesta agli utenti finali per l'aggiornamento della password.

Si applica a:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>Assegnare certificati SCEP a un dispositivo macOS senza utente  <!-- 2340521  -->
È possibile assegnare certificati Simple Certificate Enrollment Protocol (SCEP) usando gli attributi del dispositivo ai dispositivi macOS, inclusi quelli senza affinità utente, e associare il profilo del certificato con profili Wi-Fi o VPN. Questa funzionalità estende il supporto già disponibile per l'[assegnazione di certificati SCEP ai dispositivi con e senza affinità utente](certificates-scep-configure.md#create-a-scep-certificate-profile) che eseguono Windows, iOS e Android.  Questo aggiornamento aggiunge l'opzione per selezionare un certificato di tipo *Dispositivo* quando si configura un profilo del certificato SCEP per macOS.

Si applica a: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Aggiornamento dell'interfaccia utente per l'accesso condizionale di Intune   <!-- 2432313   -->
Sono stati apportati miglioramenti all'interfaccia utente per l'accesso condizionale nella console di Intune, tra cui:
-  Sostituzione del pannello *Accesso condizionale* di Intune con il pannello di Azure Active Directory. Ciò consente di accedere alla gamma completa di impostazioni e configurazioni per l'[accesso condizionale](conditional-access.md) (che rimane una tecnologia di Azure AD) direttamente dalla console di Intune. 
- Ridenominazione del pannello *Accesso locale* in *Accesso ad Exchange* e ricollocamento della configurazione del *connettore del servizio Exchange* in questo pannello rinominato.  Questa modifica consolida l'area in cui si [configurano e monitorano i dettagli relativi a Exchange Online e locale](exchange-connector-install.md).  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Le app browser in modalità tutto schermo e browser Microsoft Edge possono essere eseguite nei dispositivi Windows 10 in modalità tutto schermo <!-- 2935135   -->
È possibile usare dispositivi Windows 10 in modalità tutto schermo per eseguire una o più app. Questo aggiornamento include diverse modifiche all'uso delle app browser in modalità tutto schermo, tra cui:

- Aggiunta del browser Microsoft Edge o del browser in modalità tutto schermo per l'esecuzione come app nel dispositivo in modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **Windows 10 e versioni successive** per la piattaforma > **Modalità tutto schermo** per il tipo di profilo).
- Sono disponibili nuove funzionalità e impostazioni che è possibile consentire o limitare (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo), tra cui:

  - Browser Microsoft Edge:
  - Usa la modalità tutto schermo di Microsoft Edge
  - Aggiorna il browser dopo il tempo di inattività

 - Preferiti e ricerca:
  - Consenti modifiche al motore di ricerca

Per un elenco di queste impostazioni, vedere:

- [Impostazioni dei dispositivi Windows 10 e versioni successive per l'esecuzione in modalità tutto schermo](kiosk-settings-windows.md)
- [Limitazioni del dispositivo per il browser Microsoft Edge](device-restrictions-windows-10.md#microsoft-edge-browser)
- [Limitazioni del dispositivo per Preferiti e ricerca](device-restrictions-windows-10.md##favorites-and-search)

Si applica a: Windows 10 e versioni successive

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>Nuove impostazioni relative alle restrizioni dei dispositivi per dispositivi iOS e macOS <!-- 3448774   -->
Nei dispositivi che eseguono iOS e macOS è possibile limitare alcune impostazioni e funzionalità (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** o **macOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento aggiunge altre funzionalità e impostazioni che è possibile controllare, tra cui l'impostazione dell'orario dello schermo, la modifica delle impostazioni dell'eSIM e dei piani per telefoni cellulari e altro ancora nei dispositivi iOS. Sono inoltre disponibili le funzionalità di ritardo della visibilità degli aggiornamenti software da parte dell'utente e di blocco della memorizzazione di contenuti nella cache nei dispositivi macOS. 

Per conoscere le funzionalità e le impostazioni che è possibile limitare, vedere:

- [Impostazioni relative alle restrizioni per i dispositivi iOS](device-restrictions-ios.md)
- [Impostazioni relative alle restrizioni per i dispositivi macOS](device-restrictions-macos.md)

Si applica a:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>I dispositivi "in modalità tutto schermo" sono ora chiamati "dispositivi dedicati" nei dispositivi Android Enterprise <!-- 3598402   -->
Per allinearsi con la terminologia di Android, la definizione **in modalità tutto schermo** viene cambiata in **dispositivi dedicati** per i dispositivi Android Enterprise (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > ** Android Enterprise per la piattaforma > **Solo proprietario del dispositivo** > **Limitazioni del dispositivo** > **Dispositivi dedicati**).

Per visualizzare le impostazioni disponibili, passare a [Impostazioni dei dispositivi per consentire o limitare l'uso delle funzionalità](device-restrictions-android-for-work.md#dedicated-device-settings).

Si applica a:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Le impostazioni iOS per Safari e il ritardo della visibilità degli aggiornamenti software per l'utente passano all'interfaccia utente di Intune <!-- 3640850, 3803313   -->
Per i dispositivi iOS è possibile configurare le impostazioni di Safari e gli aggiornamenti software. In questo aggiornamento le impostazioni sono state spostate in diverse parti dell'interfaccia utente di Intune:

- Le impostazioni di Safari sono passate da **Safari** (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo) in **[App predefinite](device-restrictions-ios.md#built-in-apps)** .
- L'impostazione relativa al **ritardo della visibilità degli aggiornamenti software per l'utente per i dispositivi iOS con supervisione** (**Aggiornamenti software** > **Criteri di aggiornamento per iOS**) passa in **Limitazioni del dispositivo** >  **[Generale](device-restrictions-ios.md#general)** .  Per informazioni dettagliate sull'impatto sui criteri esistenti, vedere l'articolo sugli [aggiornamenti software iOS](software-updates-ios.md#configure-the-policy). 

Per un elenco di impostazioni, vedere:

- [Restrizioni dei dispositivi iOS](device-restrictions-ios.md) 
- [Aggiornamenti software iOS](software-updates-ios.md)

Questa funzionalità si applica a: 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>L'abilitazione delle restrizioni nelle impostazioni del dispositivo è stata rinominata in Orario schermo nei dispositivi iOS <!-- 3699164   -->
È possibile configurare **Abilitazione delle restrizioni nelle impostazioni del dispositivo** nei dispositivi iOS con supervisione (**Configurazione del dispositivo** > **Profili** > **Nuovo profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Generale**). In questo aggiornamento l'impostazione è stata rinominata in **Orario schermo (solo con supervisione)** . 

Il comportamento è lo stesso. In particolare: 

- iOS 11.4.1 e versioni precedenti: **Blocca** impedisce agli utenti finali di impostare le proprie restrizioni nelle impostazioni del dispositivo. 
- iOS 12.0 e versioni successive: **Blocca** impedisce agli utenti finali di impostare il proprio **Orario schermo** nelle impostazioni del dispositivo, incluse le restrizioni relative al contenuto e alla privacy. Nei dispositivi aggiornati a iOS 12.0 la scheda Restrizioni non sarà più visibile nelle impostazioni del dispositivo. Queste impostazioni sono in **Orario schermo**. 

Per un elenco delle impostazioni, vedere l'articolo sulle [restrizioni dei dispositivi iOS](device-restrictions-ios.md#general).

Si applica a: 
- iOS


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>Rinominare un dispositivo Windows registrato <!-- 1911112  -->
È ora possibile rinominare un dispositivo Windows 10 (RS4 o versione successiva) registrato. A tale scopo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Rinomina dispositivo**. Questa funzionalità non supporta attualmente la ridenominazione di dispositivi Windows di Azure AD ibridi.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>Assegnare automaticamente tag di ambito alle risorse create da un amministratore con quell'ambito <!-- 3173823  -->
Quando un amministratore crea una risorsa, i tag di ambito assegnati all'amministratore verranno automaticamente assegnati alle nuove risorse.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>Il report delle registrazioni non riuscite passa al pannello Registrazione del dispositivo <!-- 3560202  -->
Il report delle **registrazioni non riuscite** è passato alla sezione **Monitoraggio** del pannello **Registrazione del dispositivo**. Sono state aggiunte due nuove colonne: Metodo di registrazione e Versione sistema operativo.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>Il report Abbandono del Portale aziendale è stato rinominato Registrazioni utente incomplete <!--3815076 eemiss -->
Il report **Abbandono del Portale aziendale** è stato rinominato **Registrazioni utente incomplete**.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>Settimana del 4 febbraio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Modalità scura del Portale aziendale Intune per macOS <!-- 3300524  -->
Il portale aziendale Intune ora supporta la modalità scura per macOS. Quando si abilita la modalità scura in un dispositivo macOS 10.14 o versione successiva, il Portale aziendale regola i colori in modo da riflettere tale modalità.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>Settimana del 21 gennaio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifiche di tipo avviso popup per app Win32 <!-- 3136566   -->
È possibile eliminare la visualizzazione delle notifiche di tipo avviso popup degli utenti finali per ogni assegnazione di app. In Intune selezionare **App client** > **App** > selezionare l'app > **Assegnazioni** > **Includi gruppi**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Aggiornamento dell'interfaccia utente dei criteri di Protezione app di Intune <!-- 3251427  -->
Sono state modificate le etichette per le impostazioni e i pulsanti per la protezione delle app di Intune per rendere tutto più comprensibile. Alcune delle modifiche includono:  
- I controlli sono cambiati da **sì** / **no** principalmente a **blocca** / **consenti** e **disabilita** / **abilita**. Anche le etichette sono state aggiornate.  
- Le impostazioni sono state riformattate, in modo che l'impostazione e la relativa etichetta siano affiancate nel controllo, consentendo spostamenti più efficienti.   

Le impostazioni predefinite e il numero di impostazioni rimangono uguali, ma questa modifica consente all'utente di comprendere, esplorare e utilizzare le impostazioni più facilmente per applicare i criteri di protezione delle app selezionati. Per informazioni, vedere le [impostazioni iOS](app-protection-policy-settings-ios.md) e le [impostazioni Android](app-protection-policy-settings-android.md).

### <a name="additional-settings-for-outlook----3301182----"></a>Impostazioni aggiuntive per Outlook <!-- 3301182  -->
Ora è possibile configurare le impostazioni aggiuntive seguenti per Outlook per iOS e Android usando Intune:

- Consentire solo agli account aziendali o dell'istituto di istruzione di essere usati in Outlook su iOS o Android
- Distribuire gli account locali dell'autenticazione moderna per Office 365 e dell'autenticazione moderna ibrida
- Usare `SAMAccountName` per il campo nome utente nel profilo di posta elettronica quando è selezionata l'autenticazione di base
- Consentire di salvare i contatti
- Configurare i suggerimenti di posta elettronica per i destinatari esterni
- Configurare **Posta in arrivo evidenziata**
- Richiedere alla biometria di accedere a Outlook per iOS
- Bloccare le immagini esterne

> [!NOTE]
> Se si usano i criteri di protezione delle app di Intune per gestire l'accesso per le identità aziendali, non abilitare **Richiedi biometria**. Per altre informazioni, vedere **Richiedi credenziali aziendali per l'accesso** per le [impostazioni di accesso iOS](app-protection-policy-settings-ios.md#access-requirements) e le [impostazioni di accesso Android](app-protection-policy-settings-android.md#access-requirements).

Per altre informazioni, vedere [Impostazioni di configurazione di Microsoft Outlook](app-configuration-policies-outlook.md).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Eliminare app Android Enterprise <!-- 1352553 -->
È possibile eliminare da Microsoft Intune le app di Google Play gestite. Per eliminare un'app di Google Play gestita, aprire Microsoft Intune nel portale di Azure e selezionare **App client** > **App**. Nell'elenco di app selezionare i puntini di sospensione (...) a destra dell'app di Google Play gestita e quindi selezionare **Elimina** nell'elenco visualizzato. Quando si elimina un'app di Google Play gestita dall'elenco di app, l'app risulta automaticamente non approvata.

#### <a name="managed-google-play-app-type----1352580---"></a>Tipo di app Google Play gestito <!-- 1352580 -->
Il tipo di app **Google Play gestito** consentirà di aggiungere in modo specifico [app Google Play gestite](https://play.google.com/work/search?q=microsoft&c=apps) a Intune. Un amministratore di Intune può ora esplorare, cercare, approvare, sincronizzare e assegnare in Intune app di Google Play gestite approvate.  Non sarà più necessario passare alla console di Google Play separatamente e rieseguire l'autenticazione.  In Intune selezionare **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di App** selezionare **Google Play gestito** come tipo di app.

### <a name="default-android-pin-keyboard----3802457---"></a>Tastiera PIN predefinita in Android <!-- 3802457 -->
Gli utenti finali che hanno impostato un PIN di tipo 'Numerico' dei criteri di protezione delle app in Intune sui loro dispositivi Android visualizzeranno ora la tastiera Android predefinita invece dell'interfaccia utente della tastiera Android fissa progettata in precedenza. Questa modifica è stata apportata per coerenza quando si usano tastiere predefinite in Android e iOS, per entrambi i tipi PIN di 'Numerico' e/o 'Passcode'. Per altre informazioni sulle impostazioni di accesso degli utenti finali in Android, ad esempio il PIN dei criteri di protezione delle app, vedere la sezione relativa ai [requisiti di accesso Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Usare le impostazioni consigliate da Microsoft con le baseline di sicurezza (anteprima pubblica) <!-- 2055484   -->

Intune si integra con altri servizi specifici per la sicurezza, inclusi Windows Defender ATP e Office 365 ATP. I clienti manifestano l'esigenza di una strategia comune e di un set integrato di flussi di lavoro di sicurezza end-to-end nei servizi di Microsoft 365. L'obiettivo è l'allineamento delle strategie per creare soluzioni in grado di conciliare le operazioni di sicurezza e le comuni attività degli amministratori. Per realizzare questo obiettivo in Intune, è stato pubblicato un set di "baseline di sicurezza" consigliate da Microsoft (**Intune** > **Baseline di sicurezza**).  Un amministratore può creare criteri di sicurezza direttamente da queste baseline e quindi distribuirle agli utenti. È anche possibile personalizzare le raccomandazioni per le procedure consigliate in modo soddisfare le specifiche esigenze dell'organizzazione. Intune verifica che i dispositivi rimangano conformi a queste baseline e invia agli amministratori una notifica sugli utenti e i dispositivi non conformi.

Questa funzionalità è disponibile in anteprima pubblica, perciò i profili di nuova creazione non verranno spostati nei modelli di baseline di sicurezza disponibili a livello generale. Non è consigliabile usare questi modelli di anteprima nell'ambiente di produzione.

Per altre informazioni sulle baseline di sicurezza, vedere [Creare una baseline di sicurezza di Windows 10 in Intune](security-baselines-monitor.md).

Questa funzionalità si applica a: Windows 10 e versioni successive

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>I non amministratori possono abilitare BitLocker nei dispositivi Windows 10 aggiunti ad Azure AD<!-- 2147379   -->
Quando si abilitano le impostazioni di BitLocker nei dispositivi Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo**  >  **Windows 10 e versioni successive** per la piattaforma > **Endpoint Protection** per il tipo di profilo > **Crittografia Windows**), si aggiungono impostazioni BitLocker. 

Questo aggiornamento include una nuova impostazione di BitLocker per consentire agli utenti standard (non amministratori) di abilitare la crittografia. 

Per visualizzare queste impostazioni, vedere [Impostazioni di Endpoint Protection per Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Verificare la conformità di Configuration Manager <!-- 2192052  eepublished  -->
Questo aggiornamento include una nuova impostazione di conformità di System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10 e versioni successive** > **Conformità di Configuration Manager**). Configuration Manager invia segnali per la conformità di Intune. Usando questa impostazione è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Questa impostazione è descritta in [Conformità di Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance).

Si applica a: Windows 10 e versioni successive

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalizzare lo sfondo nei dispositivi iOS con supervisione con un profilo di configurazione del dispositivo <!-- 2809324   -->
Quando si crea un profilo di configurazione del dispositivo per i dispositivi iOS, è possibile personalizzare alcune funzionalità (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni di **Sfondo** che consentono a un amministratore di usare un'immagine PNG, JPG o JPEG nella schermata iniziale o nella schermata di blocco. Queste impostazioni dello sfondo si applicano solo ai dispositivi con supervisione. 

Per un elenco di queste impostazioni, vedere [Impostazioni relative alle funzionalità dei dispositivi iOS in Intune](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Modalità a tutto schermo di Windows 10 disponibile a livello generale <!-- 3594661  -->
In questo aggiornamento, la funzionalità Modalità tutto schermo in Windows 10 e versioni successive è disponibile a livello generale. Per informazioni su tutte le impostazioni che è possibile aggiungere e configurare, vedere le [impostazioni della modalità tutto schermo per Windows 10 (e versioni successive)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>La Condivisione dei contatti tramite Bluetooth viene rimossa in Limitazioni del dispositivo > Proprietario dispositivo per Android Enterprise <!-- 3598396   -->
Quando si crea un profilo di limitazione per i dispositivi Android Enterprise, è disponibile un'impostazione **Condivisione dei contatti tramite Bluetooth**. In questo aggiornamento viene rimossa l'impostazione **Condivisione dei contatti tramite Bluetooth** (**Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo > Proprietario dispositivo** per il tipo di profilo > **Generale**). 

L'impostazione **Condivisione contatti tramite Bluetooth** non è supportata per la gestione dei proprietari di dispositivi Android Enterprise. Pertanto, la rimozione di questa impostazione non influisce su alcun dispositivo o tenant, anche se l'impostazione è abilitata e configurata nell'ambiente in uso.

Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

Si applica a: Proprietario dispositivo Android Enterprise

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Supporto di cancellazione selettiva per dispositivi WIP senza registrazione <!-- 1434452 -->
Windows Information Protection senza registrazione (WIP-WE, Windows Information Protection Without Enrollment) consente ai clienti di proteggere i dati aziendali nei dispositivi Windows 10 senza la necessità di una registrazione MDM (Mobile Device Management, gestione di dispositivi mobili) completa. Quando i documenti sono protetti da criteri WIP-WE, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, si rendono inutilizzabili tutti i dati protetti tramite criteri WIP-WE. Da Intune nel portale di Azure selezionare **App per dispositivi mobili** > **Cancellazione selettiva di app**.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nuovi log operativi e possibilità di inviare i log ai servizi di Monitoraggio di Azure <!-- 3762211  -->
Intune include una funzionalità di registrazione di controllo predefinita che consente di tenere traccia degli eventi quando vengono apportate modifiche. Questo aggiornamento include nuove funzionalità di registrazione, tra cui: 
- Log operativi (anteprima) che mostrano informazioni dettagliate su utenti e dispositivi registrati, tra cui operazioni riuscite e non riuscite.
- I log di controllo e i log operativi possono essere inviati a Monitoraggio di Azure, inclusi account di archiviazione, hub eventi e Log Analytics. Questi servizi consentono di archiviare, usare funzionalità di analisi come QRadar e Splunk, nonché ottenere visualizzazioni dei dati di registrazione.

In [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics in Intune (anteprima)](review-logs-using-azure-monitor.md) sono disponibili altre informazioni su questa funzionalità.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorare altre schermate di Assistente configurazione in un dispositivo DEP iOS <!-- 2687509  -->
Oltre alle schermate che è attualmente possibile ignorare, è possibile impostare i dispositivi DEP iOS in modo che ignorino le schermate seguenti nell'Assistente configurazione quando un utente registra il dispositivo: Segnale schermo, Privacy, Migrazione di Android, Pulsante Pagina iniziale, iMessage e FaceTime, Onboarding, Migrazione di Watch, Aspetto, Orario schermo, Aggiornamento software, Configurazione SIM.
Per scegliere le schermate da ignorare, passare a **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > scegliere un token > **Profili** > scegliere un profilo > **Proprietà** > **Personalizzazione dell'Assistente configurazione** > scegliere **Nascondi** per tutte le schermate che si vuole ignorare > **OK**.
Se si crea un nuovo profilo o si modifica un profilo, le schermate da ignorare selezionate devono essere sincronizzate con il server MDM di Apple. Gli utenti possono eseguire una sincronizzazione manuale dei dispositivi in modo da evitare ritardi nell'aggiornamento delle modifiche del profilo.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Distribuzione di app Android Enterprise APP-WE <!-- 1171203 -->
Per i dispositivi Android in uno scenario di distribuzione APP-WE (App Protection Policy Without Enrollment) non registrato, è ora possibile usare Google Play gestito per distribuire app dello Store e app LOB agli utenti. In particolare, è possibile offrire agli utenti finali un catalogo di app e un'esperienza di installazione che non richiede più agli utenti finali di ridurre il comportamento di sicurezza dei propri dispositivi consentendo installazioni da origini sconosciute. Inoltre, questo scenario di distribuzione fornirà un'esperienza migliorata per gli utenti finali.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>Settimana del 14 gennaio 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Anteprima del supporto per i dispositivi aziendali Android completamente gestiti <!-- 1574342  -->
Intune ora supporta i dispositivi Android completamente gestiti, ovvero uno scenario con dispositivi di proprietà aziendale gestiti rigorosamente dal reparto IT e associati a singoli utenti. Ciò consente agli amministratori di gestire l'intero dispositivo, imporre un'ampia gamma di controlli dei criteri non disponibili per i profili di lavoro e limitare gli utenti all'installazione di app solo da Google Play gestito. Per altre informazioni, vedere [Set up Intune enrollment of Android fully managed devices](android-fully-managed-enroll.md) (Configurare la registrazione in Intune dei dispositivi Android completamente gestiti) ed [Enroll your dedicated devices or fully managed devices](android-dedicated-devices-fully-managed-enroll.md) (Registrare i dispositivi dedicati o i dispositivi completamente gestiti).  Si noti che questa funzionalità è disponibile in anteprima. Alcune funzionalità di Intune, come ad esempio i certificati, la conformità e l'accesso condizionale, non sono attualmente disponibili con i dispositivi utente Android completamente gestiti.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>Settimana del 7 gennaio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-app-pin----2298397---"></a>PIN dell'app Intune <!-- 2298397 -->
Ora l'amministratore IT può configurare il numero di giorni di attesa per un utente finale prima che debba modificare il PIN dell'app Intune. La nuova impostazione è *PIN reset after number of days* (Reimpostazione PIN dopo numero di giorni) ed è disponibile nel portale di Azure selezionando **Intune** > **App client** > **Criteri di protezione delle app** > **Crea criterio** > **Impostazioni** > **Requisiti di accesso**. Disponibile per dispositivi [iOS](app-protection-policy-settings-ios.md) e [Android](app-protection-policy-settings-android.md), questa funzionalità supporta un numero intero positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campi per i report relativi ai dispositivi di Intune <!-- 2748738 -->
Intune offre campi aggiuntivi per i report relativi ai dispositivi, tra cui ID di registrazione app, produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. In Intune questi campi sono disponibili selezionando **App client** > **Stato protezione app** e scegliendo **Report sulla protezione dell'app: iOS, Android**. Inoltre, questi parametri consentiranno di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della versione minima della patch di sicurezza Android. 


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>I modelli amministrativi sono disponibili in anteprima pubblica e sono stati spostati nel profilo di configurazione corrispondente <!-- 3322847 -->

I modelli amministrativi in Intune (**Configurazione del dispositivo** > **Modelli amministrativi**) sono attualmente disponibili in anteprima pubblica. Con questo aggiornamento:

- i modelli amministrativi includono circa 300 impostazioni che possono essere gestite in Intune. In precedenza, queste impostazioni erano disponibili solo in Editor Criteri di gruppo.
- I modelli amministrativi sono disponibili in anteprima pubblica.
- I modelli amministrativi vengono spostati da **Configurazione del dispositivo** > **Modelli amministrativi** a **Configurazione del dispositivo** > **Profili** > **Crea profilo** > in **Piattaforma** scegliere  **Windows 10 e versioni successive** > in **Tipo di profilo** scegliere **Modelli amministrativi**.
- La creazione di report è abilitata

Per altre informazioni su questa funzionalità, vedere [Modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune](administrative-templates-windows.md).

Si applica a: Windows 10 e versioni successive

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Usare S/MIME per crittografare e firmare più dispositivi per un utente  <!-- 1333642 -->
Questo aggiornamento include una crittografia di posta elettronica S/MIME con un nuovo profilo di certificato importato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > selezionare la piattaforma > tipo di profilo **Certificato PKCS importato**). In Intune è possibile importare i certificati nel formato PFX. Intune può quindi distribuire i certificati a più dispositivi registrati da un singolo utente. Inoltre:
- Il profilo di posta elettronica iOS nativo supporta l'abilitazione della crittografia S/MIME mediante certificati importati in formato PFX.
- L'app di posta elettronica nativa nei dispositivi Windows Phone 10 usa automaticamente il certificato S/MIME.
- I certificati privati possono essere recapitati su più piattaforme. Tuttavia, non tutte le app di posta elettronica supportano S/MIME.
- In altre piattaforme potrebbe essere necessario configurare manualmente l'app di posta elettronica per abilitare S/MIME.  
- È possibile che le app di posta elettronica che supportano la crittografia S/MIME gestiscano il recupero dei certificati per la crittografia della posta elettronica S/MIME in un modo non supportato dal software MDM, ad esempio basandosi sull'archivio certificati del server di pubblicazione.
Per altre informazioni su questa funzionalità, vedere [Firma e crittografia S/MIME della posta elettronica in Intune](certificates-s-mime-encryption-sign.md).
Supportato in: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nuove opzioni per la connessione automatica e per rendere persistenti le regole quando si usano le impostazioni DNS in dispositivi con Windows 10 e versioni successive <!-- 1333665, 2999078 -->
Nei dispositivi con Windows 10 e versioni successive è possibile creare un profilo di configurazione VPN che include un elenco dei server DNS per risolvere i domini, ad esempio contoso.com. Questo aggiornamento include nuove impostazioni per la risoluzione dei nomi (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Windows 10 e versioni successive** per la piattaforma > scegliere **VPN** per il tipo di profilo > **Impostazioni DNS** >**Aggiungi**): 
- **Connetti automaticamente**: con l'impostazione **Abilitato**, il dispositivo si connette automaticamente alla rete VPN quando un dispositivo contatta un dominio immesso, ad esempio contoso.com.
- **Persistente**: per impostazione predefinita, tutte le regole della tabella dei criteri di risoluzione dei nomi di criteri (NRPT) sono attive, purché il dispositivo sia connesso con questo profilo VPN. Quando questa impostazione è **Abilitata** per una regola NRPT, la regola rimane attiva nel dispositivo, anche in caso di disconnessione della rete VPN. La regola rimane fino alla rimozione del profilo VPN o fino alla rimozione manuale della regola, che può essere eseguita tramite PowerShell.
[Impostazioni VPN di Windows 10](vpn-settings-windows-10.md) descrive le impostazioni. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Usare il rilevamento delle reti attendibili per i profili VPN nei dispositivi Windows 10 <!-- 1500165 -->
Quando si usa il rilevamento delle reti attendibili, è possibile impedire ai profili VPN di creare automaticamente una connessione VPN quando l'utente è già in una rete attendibile. Con questo aggiornamento è possibile aggiungere suffissi DNS per abilitare il rilevamento delle reti attendibili nei dispositivi che eseguono Windows 10 e versioni successive (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **VPN** per il tipo di profilo).
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md) sono elencate le impostazioni VPN correnti.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gestione di dispositivi Windows Holographic for Business usati da più utenti <!-- 1907917, 1063203 -->
Attualmente è possibile configurare le impostazioni del PC condiviso nei dispositivi Windows 10 e Windows Holographic for Business usando un'impostazione OMA-URI personalizzata. Con questo aggiornamento viene aggiunto un nuovo profilo per configurare le impostazioni del PC condiviso: **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Dispositivo multiutente condiviso**.
Per altre informazioni su questa funzionalità, vedere [Controllare l'accesso, gli account e le funzionalità di risparmio energia nei PC condivisi o nei dispositivi multiutente con Intune](shared-user-device-settings.md).
Si applica a: Windows 10 e versioni successive, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nuove impostazioni per gli aggiornamenti di Windows 10 <!--2626030  2512994  -->
Per gli [anelli di aggiornamento Windows 10](windows-update-for-business-configure.md) è possibile configurare:
- **Comportamento di aggiornamento automatico**: usare la nuova opzione *Ripristina impostazione predefinita* per ripristinare le impostazioni di aggiornamento automatico originali nei computer Windows 10 che eseguono l'*aggiornamento di ottobre 2018*
- *Impedisci all'utente di sospendere gli aggiornamenti Windows*: consente di configurare una nuova impostazione per gli aggiornamenti software che impedisce o permette agli utenti di sospendere l'installazione degli aggiornamenti da **Impostazioni** nei loro computer. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>I profili di posta elettronica iOS possono usare firma e crittografia S/MIME <!-- 2662949 -->
È possibile creare un profilo di posta elettronica che include impostazioni diverse. Questo aggiornamento include le impostazioni di S/MIME che possono essere usate per firmare e crittografare le comunicazioni tramite posta elettronica nei dispositivi iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **iOS** per la piattaforma > **Posta elettronica** per il tipo di profilo).
Le impostazioni sono elencate in [Impostazioni del profilo di posta elettronica per dispositivi iOS](email-settings-ios.md).

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Alcune impostazioni di BitLocker supportano l'edizione Windows 10 Pro<!-- 2727036 -->
È possibile creare un profilo di configurazione che imposta le impostazioni di Endpoint Protection nei dispositivi Windows 10, incluso BitLocker. Questo aggiornamento aggiunge il supporto per l'edizione Windows 10 Professional per alcune impostazioni di BitLocker. Per visualizzare queste impostazioni, vedere [Impostazioni di Endpoint Protection per Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>L'impostazione Configurazione del dispositivo condiviso è stata rinominata Messaggio della schermata di blocco per i dispositivi iOS nel portale di Azure<!-- 2809362 -->
Quando si crea un profilo di configurazione per i dispositivi iOS, è possibile aggiungere le impostazioni **Configurazione del dispositivo condiviso** per visualizzare testo specifico nella schermata di blocco. Questo aggiornamento include le modifiche seguenti: 
- L'impostazione **Configurazione del dispositivo condiviso** nel portale di Azure è stata rinominata "Lock Screen Message (supervised only)" (Messaggio della schermata di blocco - solo con supervisione): **Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > scegliere **iOS** per la piattaforma > scegliere **Funzionalità del dispositivo** per il tipo di profilo > **Lock Screen Message** (Messaggio della schermata di blocco).
- Quando si aggiungono messaggi della schermata di blocco, è possibile inserire un numero di serie, un nome di dispositivo o un altro valore specifico del dispositivo come variabile in **Informazioni sui tag asset** e **Nota a piè di pagina della schermata di blocco**. Ad esempio, è possibile immettere `Device name: {{devicename}}` o `Serial number is {{serialnumber}}` usando parentesi graffe. In [Token iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) sono elencati i token disponibili che possono essere usati.
Le impostazioni sono elencate in [Aggiungere messaggi personalizzati alla schermata di blocco e alla finestra di accesso nei dispositivi iOS con Microsoft Intune](shared-device-settings-ios.md).

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nuove impostazioni di limitazione dei dispositivi App Store, visualizzazione documenti, giochi aggiunte ai dispositivi iOS <!-- 2827760-->
In **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi** sono state aggiunte le impostazioni seguenti: Allow managed apps to write contacts to unmanaged contacts accounts (Consenti alle app gestite di scrivere contatti in account di contatti non gestiti), Allow unmanaged apps to read from managed contacts accounts (Consenti alle app non gestite di leggere da account di contatti gestiti). Per vedere queste impostazioni, consultare le [limitazioni per i dispositivi iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nuove impostazioni di notifica, hint e protezione della tastiera per i dispositivi Android Enterprise in modalità proprietario del dispositivo <!-- 3201839 3201843 -->
Questo aggiornamento include numerose nuove funzionalità per i dispositivi aziendali Android quando vengono eseguiti come proprietario del dispositivo. Per usare queste funzionalità, passare a **Configurazione del dispositivo** > **Profili** > **Crea profilo** > in **Piattaforma**, scegliere **Android Enterprise** > in **Tipo di profilo**, scegliere **Solo proprietario del dispositivo** > **Limitazioni del dispositivo**.

Le nuove funzionalità includono: 

- Disabilitare la visualizzazione delle notifiche di sistema, incluse chiamate in ingresso, avvisi di sistema, errori di sistema e altro.
- Suggerimenti per ignorare le esercitazioni e i consigli iniziali per le app aperte per la prima volta.
- Disabilitare le impostazioni avanzate di protezione della tastiera, ad esempio fotocamera, notifiche, sblocco tramite impronta digitale e altro.


Per visualizzare le impostazioni, passare a [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>I dispositivi Android Enterprise in modalità proprietario del dispositivo possono usare le connessioni VPN sempre attive <!-- 3202194 -->
In questo aggiornamento è possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise in modalità proprietario del dispositivo. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
È possibile abilitare le connessioni VPN sempre attive in **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo** per Solo proprietario del dispositivo > **Connettività**. Per visualizzare le impostazioni, passare a [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nuova impostazione per terminare i processi in Gestione attività nei dispositivi Windows 10 <!-- 3285177 --> 
Questo aggiornamento include una nuova impostazione per terminare i processi usando Gestione attività nei dispositivi Windows 10. Scegliere se consentire o non consentire questa impostazione usando un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > In **Piattaforma** scegliere **Windows 10** > in **Tipo di profilo** scegliere **Limitazioni del dispositivo** > **Generale**).
Per visualizzare queste impostazioni, vedere [Impostazioni relative alle limitazioni per i dispositivi Windows 10 e versioni successive in Microsoft Intune](device-restrictions-windows-10.md).
Si applica a: Windows 10 e versioni successive


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Messaggi di errore più dettagliati per le restrizioni di registrazione <!-- 3111564 -->
Sono disponibili messaggi di errore più dettagliati quando non vengono soddisfatte le restrizioni di registrazione. Per visualizzare questi messaggi, passare a **Intune** > **Risoluzione dei problemi** e selezionare la tabella Errori di registrazione. Per altre informazioni, vedere l'[elenco degli errori di registrazione](help-desk-operators.md#enrollment-failure-reference).

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="tenant-status-dashboard-----1124854---"></a>Dashboard Stato del tenant  <!-- 1124854 -->
La nuova pagina [Stato del tenant](tenant-status.md) offre una posizione centralizzata in cui visualizzare lo stato del tenant e le informazioni dettagliate correlate.  Il dashboard è suddiviso in quattro aree:
- **Dettagli del tenant**: visualizza informazioni su nome e posizione del tenant, autorità MDM, totale dei dispositivi registrati nel tenant e numero di licenze. Questa sezione indica anche la versione corrente del servizio per il tenant.
- **Stato del connettore**: visualizza informazioni sui connettori disponibili configurati e può elencare anche quelli non ancora abilitati.  
   In base allo stato corrente di ogni connettore, i connettori vengono contrassegnati come Integro, Avviso o Non integro. Selezionare un connettore per eseguire il drill-through e visualizzarne i dettagli oppure per configurare informazioni aggiuntive.
-  **Integrità del servizio Intune**: visualizza informazioni dettagliate sugli eventi imprevisti attivi o le interruzioni del tenant. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office.
-  **Novità su Intune**: visualizza i messaggi attivi per il tenant, ad esempio le notifiche inviate quando il tenant riceve le funzionalità di Intune più recenti.  Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nuova esperienza di Guida e supporto tecnico nel Portale aziendale per Windows 10 <!-- 1488939-->
La nuova pagina Guida e supporto del Portale aziendale aiuta gli utenti a risolvere i problemi e a richiedere assistenza in merito ai problemi di accesso e relativi alle app. Da questa nuova pagina gli utenti possono inviare tramite posta elettronica i dettagli dei log degli errori e di diagnostica e possono trovare le informazioni dettagliate sul supporto tecnico della loro organizzazione. Troveranno anche una sezione di domande frequenti con collegamenti alla documentazione di Intune pertinente. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nuova esperienza di Guida e supporto tecnico per Intune   <!-- #3307080 -->
Nei prossimi giorni la nuova esperienza di Guida e supporto tecnico verrà distribuita in tutti i tenant. Questa nuova esperienza è disponibile per Intune ed è accessibile dai pannelli di Intune nel [portale di Azure](https://portal.azure.com/).
La nuova esperienza consente di descrivere il problema con parole proprie e di ricevere informazioni dettagliate per la risoluzione dei problemi e contenuti Web per la correzione. Queste soluzioni sono offerte tramite un algoritmo di apprendimento automatico basato su regole, creato in base alle indagini condotte tra gli utenti. Oltre alle indicazioni specifiche per il problema, è possibile usare il nuovo flusso di lavoro di creazione di un caso per aprire un caso di supporto tramite posta elettronica o telefono. Questa nuova esperienza sostituisce l'esperienza di Guida e supporto tecnico precedente basata su un set statico di opzioni preselezionate a seconda dell'area della console in cui ci si trova quando si apre Guida e supporto. Per altre informazioni, vedere [Come ottenere supporto per Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-for-apps----1081941---"></a>Tag di ambito per le app <!-- 1081941 -->
È possibile creare tag di ambito per limitare l'accesso per ruoli e app. È possibile aggiungere un tag di ambito a un'app in modo che solo le persone al cui ruolo è già assegnato tale tag abbiano accesso all'app. Al momento non è possibile assegnare i tag di ambito alle app aggiunte a Intune da Google Play gestito o alle app acquistate tramite Volume Purchase Program di Apple, ma questo supporto è previsto per il futuro. Per altre informazioni, vedere [Usare i tag di ambito per filtrare i criteri](scope-tags.md).

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>Settimana del 10 dicembre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="updates-for-application-transport-security----748318---"></a>Aggiornamenti per Application Transport Security <!-- 748318 -->

Microsoft Intune supporta Transport Layer Security (TLS) 1.2+ per offrire la migliore crittografia, per garantire una maggiore sicurezza per Intune per impostazione predefinita e per allinearsi agli altri servizi Microsoft, ad esempio Microsoft Office 365. Per poter soddisfare questo requisito, i portali aziendali iOS e macOS applicheranno i requisiti di Application Transport Security (ATS) aggiornati di Apple per cui è obbligatorio l'uso di TLS 1.2+. Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale iOS e macOS. Per altre informazioni, vedere il [blog del supporto tecnico di Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK supporterà le chiavi di crittografia a 256 bit <!-- 1832174 -->
Intune App SDK per Android usa ora le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. L'SDK continuerà a supportare le chiavi a 128 bit per garantire la compatibilità con il contenuto e le app che usano versioni precedenti dell'SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Microsoft Auto Update versione 4.5.0 obbligatorio per i dispositivi macOS <!-- 3503442 -->
Per continuare a ricevere gli aggiornamenti per il portale aziendale e le altre applicazioni di Office, è necessario aggiornare i dispositivi macOS gestiti da Intune a Microsoft Auto Update 4.5.0. Gli utenti potrebbero avere già questa versione per le app di Office.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune richiede macOS 10.12 o versione successiva <!-- 2827778 -->
Intune richiede ora macOS versione 10.12 o successiva. I dispositivi che usano versioni precedenti di macOS non possono usare il portale aziendale per la registrazione in Intune. Per ricevere assistenza e nuove funzionalità, gli utenti devono aggiornare il dispositivo a macOS 10.12 o versione successiva e aggiornare l'app Portale aziendale alla versione più recente.

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>Settimana del 26 novembre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Disinstallazione di app in dispositivi iOS con supervisione di proprietà dell'azienda <!-- 1281677 -->

È possibile rimuovere qualsiasi app nei dispositivi iOS con supervisione di proprietà dell'azienda. È possibile rimuovere qualsiasi app specificando come destinazione gruppi di utenti o dispositivi con un tipo di assegnazione **Disinstalla**. Per i dispositivi iOS personali o senza supervisione, sarà ancora possibile rimuovere solo le app installate usando Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Download del contenuto dell'app Win32 Intune <!-- 2617320 -->
I client Windows 10 RS3 e versioni successive scaricheranno contenuto dell'app Win32 Intune mediante un componente Ottimizzazione recapito nel client Windows 10. Ottimizzazione recapito offre funzionalità peer-to-peer attivate per impostazione predefinita. Attualmente è possibile configurare Ottimizzazione recapito tramite Criteri di gruppo. Per altre informazioni, vedere [Ottimizzazione recapito per Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Dispositivo dell'utente finale e menu di scelta rapida delle app <!-- 2771453 -->
Gli utenti finali possono ora usare il menu di scelta rapida nel dispositivo e nelle app per attivare azioni comuni come la ridenominazione di un dispositivo o il controllo della conformità.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Impostare lo sfondo personalizzato nell'app di schermata iniziale gestita  <!-- 3041945 -->
Verrà aggiunta un'impostazione che consente di personalizzare l'aspetto dello sfondo dell'app di schermata iniziale gestita nei dispositivi Android Enterprise in modalità tutto schermo per più app.  Per configurare lo **sfondo personalizzato per l'URL**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Salvataggio e applicazione dell'assegnazione dei criteri di protezione dell'app <!-- 3104570 -->
È disponibile un maggiore controllo sulle [assegnazioni dei criteri di protezione dell'app](app-protection-policies.md#deploy-a-policy-to-users). Quando si seleziona *Assegnazioni* per impostare o modificare le assegnazioni dei criteri, è necessario scegliere **Salva** per salvare la configurazione prima che la modifica venga applicata. Usare **Annulla** per cancellare tutte le modifiche apportate senza salvare le modifiche agli elenchi di inclusione o esclusione.  Con la scelta obbligatoria di Salva o Annulla, i criteri di protezione delle app vengono assegnati solo agli utenti previsti.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nuove impostazioni del browser Microsoft Edge per Windows 10 e versioni successive <!-- 3174639 -->
Questo aggiornamento include nuove impostazioni per controllare e gestire il browser Microsoft Edge nei dispositivi. Per un elenco di queste impostazioni correnti, vedere [Restrizione dei dispositivi per Windows 10 (e versioni successive)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Supporto di nuove app con criteri di protezione delle app <!-- 3330037 -->
È ora possibile gestire le app seguenti con i [criteri di protezione delle app di Intune](app-protection-policies.md):
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Usare i criteri di protezione delle app per proteggere i dati aziendali e controllare il trasferimento dei dati per queste app, come per le altre app gestite dai criteri di Intune. Nota: se Flow non è ancora visibile nella console, è possibile aggiungere Flow quando si creano o modificano i criteri di protezione delle app. A tale scopo, usare l'opzione **+ Altre app** e quindi specificare l'*ID app* per Flow nel campo di input. Per Android usare *com.microsoft.flow* e per iOS usare *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Vengono visualizzati i numeri di versione e di build di iOS e macOS <!-- 1892471 -->
In **Conformità del dispositivo** > **Conformità del dispositivo** vengono visualizzate le versioni del sistema operativo iOS e macOS che possono essere usate nei criteri di conformità. Questo aggiornamento include il numero di build configurabile per entrambe le piattaforme.
Quando vengono rilasciati aggiornamenti della sicurezza, Apple lascia in genere il numero di versione invariato, ma aggiorna il numero di build. Il numero di build nei criteri di conformità consente di verificare facilmente se è installato l'aggiornamento di una vulnerabilità.
Per usare questa funzionalità, vedere i criteri di conformità di [iOS](compliance-policy-create-ios.md#device-health) e [macOS](compliance-policy-create-mac-os.md#device-properties).

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Gli anelli di aggiornamento verranno sostituiti con le impostazioni di Ottimizzazione recapito per Windows 10 e versioni successive <!-- 2753807 -->
Ottimizzazione recapito è un nuovo profilo di configurazione per Windows 10 e versioni successive. Questa funzionalità offre un'esperienza semplificata per recapitare gli aggiornamenti software ai dispositivi nell'organizzazione. Questo aggiornamento consente anche di distribuire le impostazioni in anelli di aggiornamento nuovi ed esistenti tramite un profilo di configurazione.
Per configurare un profilo di configurazione di ottimizzazione recapito, vedere [Windows 10 (and newer) delivery optimization settings](delivery-optimization-windows.md).(Impostazioni di ottimizzazione recapito di Windows 10 e versioni successive).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Nuove impostazioni relative alle limitazioni dei dispositivi aggiunte ai dispositivi iOS e macOS <!-- 2827760 -->
Questo aggiornamento include nuove impostazioni per i dispositivi iOS e macOS che vengono rilasciati con iOS 12:

**Impostazioni iOS**: 
- Generali: Blocca la rimozione di app (solo con supervisione)
- Generali: Blocca la modalità USB con restrizioni (solo con supervisione)
- Generali: Imponi data e ora automatiche (solo con supervisione)
- Password: Blocca il riempimento automatico delle password (solo con supervisione)
- Password: Blocca le richieste di prossimità password (solo con supervisione)
- Password: Blocca la condivisione delle password (solo con supervisione)

**Impostazioni macOS**: 
- Password: Blocca il riempimento automatico delle password
- Password: Blocca le richieste di prossimità password
- Password: Blocca la condivisione delle password

Per altre informazioni su queste impostazioni, vedere le impostazioni relative alle limitazioni dei dispositivi [iOS](device-restrictions-ios.md) e [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selezionare le app registrate nella pagina Stato di registrazione<!-- 2531007 -->
È possibile scegliere le app di cui tenere traccia nella pagina Stato di registrazione. Fino a quando non vengono installate queste app, l'utente non può usare il dispositivo. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Cercare dispositivi Autopilot in base al numero di serie <!--2595788 -->
È ora possibile cercare i dispositivi Autopilot in base al numero di serie. A tale scopo, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > digitare un numero di serie nella casella **Cerca per numero di serie** > premere INVIO.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Tenere traccia dell'installazione di Office ProPlus <!--2620217 -->
Gli utenti possono tenere traccia dello stato dell'installazione di [Office ProPlus](apps-add-office365.md) tramite la pagina [Stato di registrazione](windows-enrollment-status.md). Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invierà un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Supporto di Device Enrollment Program di macOS per gli account Apple School Manager <!--3006133 -->
Intune supporta ora l'uso di Device Enrollment Program nei dispositivi macOS per gli account Apple School Manager.  Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS con Device Enrollment Program o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nuovo SKU per la sottoscrizione del dispositivo Intune <!--3312071-->
È ora disponibile un nuovo SKU per la sottoscrizione basato sul dispositivo che consente alle organizzazioni di ridurre i costi di gestione dei dispositivi. Questo SKU per dispositivo Intune viene concesso in licenza per ogni dispositivo su base mensile. Il prezzo varia in base al programma di licenza. È disponibile direttamente tramite l'interfaccia di amministrazione di Microsoft 365 e tramite il [Contratto Enterprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2), il [Contratto per i Prodotti e i Servizi Microsoft](https://www.microsoft.com/licensing/mpsa/default), i [contratti Microsoft Open](https://partner.microsoft.com/licensing/licensing-agreements) e [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Sospendere temporaneamente la modalità tutto schermo nei dispositivi Android per apportare modifiche <!-- 3041935 -->
Quando si usano dispositivi Android in modalità tutto schermo per più app, un amministratore IT potrebbe aver bisogno di apportare modifiche al dispositivo. Questo aggiornamento include nuove impostazioni della modalità tutto schermo per più app che consentono a un amministratore IT di sospendere temporaneamente la modalità tutto schermo tramite un PIN e di ottenere l'accesso all'intero dispositivo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Abilitare il pulsante Pagina iniziale virtuale nei dispositivi in modalità tutto schermo di Android Enterprise  <!-- 3042021 -->
Una nuova impostazione consentirà agli utenti di toccare un pulsante softkey nel dispositivo per passare dall'app di schermata iniziale gestita alle altre app assegnate nel dispositivo in modalità tutto schermo per più app. Questa impostazione è particolarmente utile negli scenari in cui l'app in modalità tutto schermo di un utente non risponde in modo corretto al pulsante "Indietro". Sarà possibile configurare questa impostazione per i dispositivi Android monouso di proprietà dell'azienda. Per abilitare o disabilitare il **pulsante Pagina iniziale virtuale**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>Settimana del 12 novembre 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Supporto del controllo accesso alla rete per Citrix SSO per iOS <!-- 3259404 -->

Citrix ha rilasciato un aggiornamento di Citrix Gateway per supportare il controllo accesso alla rete per Citrix SSO per iOS in Intune. È possibile acconsentire esplicitamente per includere un ID dispositivo all'interno di un profilo VPN in Intune e quindi eseguire il push del profilo nei dispositivi iOS. Sarà necessario installare l'aggiornamento più recente di Citrix Gateway per usare questa funzionalità.

In [Configurare le impostazioni VPN nei dispositivi iOS](vpn-settings-ios.md#base-vpn-settings) sono disponibili altre informazioni sull'uso del controllo accesso alla rete, tra cui alcuni requisiti aggiuntivi. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>Settimana del 05 novembre 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Supporto per iOS 12 OAuth nei profili di posta elettronica iOS <!--2155106 -->

I profili di posta elettronica iOS di Intune supportano iOS 12 Open Authorization (OAuth). Per visualizzare questa funzionalità, creare un nuovo profilo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Posta elettronica** per il tipo di profilo), oppure aggiornare un profilo di posta elettronica iOS esistente. Se la funzionalità OAuth viene abilitata in un profilo che è già stato distribuito, agli utenti verrà richiesto di ripetere l'autenticazione e di scaricare nuovamente il messaggio di posta elettronica.

Nella pagina sui [profili di posta elettronica iOS](email-settings-ios.md) sono disponibili altre informazioni sull'uso di OAuth in un profilo di posta elettronica.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Supporto di Autopilot per i dispositivi ibridi aggiunti ad Azure Active Directory (anteprima) <!-- 1048100-->
È ora possibile configurare i dispositivi ibridi aggiunti ad Azure Active Directory usando Autopilot. I dispositivi devono essere aggiunti alla rete dell'organizzazione per usare la funzionalità ibrida di Autopilot. Per altre informazioni, vedere [Distribuire dispositivi aggiunti ad Azure AD ibrido con Intune e Windows Autopilot](windows-autopilot-hybrid.md).
Questa funzionalità verrà implementata nella base di utenti nei prossimi giorni. Di conseguenza, sarà possibile seguire questa procedura solo dopo l'implementazione nel proprio account.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>Settimana del 29 ottobre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Richiedere un PIN non biometrico dopo un timeout specificato <!-- 1506985 -->
Se si richiede un PIN non biometrico dopo un timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App client** > **Criteri di protezione delle app** > **Aggiungi criteri** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche. Per informazioni sulle impostazioni di accesso, vedere [Impostazioni iOS](app-protection-policy-settings-ios.md#access-requirements) e [Impostazioni Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Impostazioni per il trasferimento dei dati delle app Intune nei dispositivi iOS registrati in MDM <!-- 2244713 -->
È possibile separare il controllo delle impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM dall'impostazione dell'identità dell'utente registrato, nota anche come nome dell'entità utente (UPN). Gli amministratori che non usano IntuneMAMUPN non noteranno alcuna variazione di comportamento. Quando questa funzionalità è disponibile, gli amministratori che usano IntuneMAMUPN per controllare il trasferimento dei dati nei dispositivi registrati dovranno esaminare le nuove impostazioni e aggiornare le impostazioni dell'app di conseguenza.

#### <a name="windows-10-win32-apps----2617325---"></a>App Win32 di Windows 10 <!-- 2617325 -->
È possibile configurare le app Win32 in modo che vengano installate nel contesto utente per i singoli utenti oppure per tutti gli utenti del dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>App Win32 di Windows e script di PowerShell <!-- 2617330 -->
Gli utenti finali non devono più eseguire l'accesso al dispositivo per installare le app Win32 o eseguire gli script di PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Risoluzione dei problemi di installazione delle app client <!-- 1363711 -->
È possibile risolvere i problemi relativi all'installazione delle app client esaminando la colonna con l'etichetta **Installazione dell'app** nel pannello **Risoluzione dei problemi**. Per visualizzare il pannello **Risoluzione dei problemi**, nel portale di Intune selezionare **Risoluzione dei problemi** in **Guida e supporto tecnico**.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Supporto del controllo di accesso alla rete nei client VPN iOS <!-- 1333693 -->
Con questo aggiornamento, è disponibile una nuova impostazione per abilitare il controllo di accesso alla rete quando si crea un profilo di configurazione VPN per Cisco AnyConnect, F5 Access e Citrix SSO per iOS. Questa impostazione consente di includere l'ID controllo di accesso alla rete del dispositivo nel profilo VPN. Non sono attualmente disponibili client VPN o soluzioni partner di controllo di accesso alla rete che supportano questo nuovo ID di controllo di accesso alla rete, ma quando lo saranno, verrà comunicato tramite il [post di blog del supporto](ttps://aka.ms/iOS12_and_vpn).

Per usare il controllo di accesso alla rete, sarà necessario:
1. Acconsentire esplicitamente per permettere a Intune di includere gli ID dei dispositivi nei profili VPN
2. Aggiornare il firmware/software del provider del controllo di accesso alla rete, usando le indicazioni del provider del controllo di accesso alla rete

Per informazioni su questa impostazione in un profilo VPN iOS, vedere [Aggiungere le impostazioni VPN sui dispositivi iOS in Microsoft Intune](vpn-settings-ios.md). Per altre informazioni sul controllo di accesso alla rete, vedere [Integrazione del controllo di accesso alla rete (NAC) con Intune](network-access-control-integrate.md). 

Si applica a: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Rimuovere un profilo di posta elettronica da un dispositivo, anche quando è presente un solo profilo di posta elettronica <!-- 1818139 -->
In precedenza non era possibile rimuovere un profilo di posta elettronica da un dispositivo *se* era l'unico profilo disponibile. Con questo aggiornamento, il comportamento cambia. Ora è possibile rimuovere un profilo di posta elettronica anche se è l'unico profilo di posta elettronica presente nel dispositivo. Per i dettagli, vedere [Add email settings to devices using Intune](email-settings-configure.md) (Aggiungere impostazioni di posta elettronica ai dispositivi con Intune).

#### <a name="powershell-scripts-and-aad----2309469---"></a>Script di PowerShell e AAD <!-- 2309469 -->
Gli script di PowerShell in Intune possono essere destinati ai gruppi di sicurezza dei dispositivi AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nuova impostazione predefinita "Tipo di password richiesto" per Android, Android Enterprise<!-- 2649963 -->
Quando si crea un nuovo criterio di conformità (**Intune** > **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android** o **Android Enterprise** per Piattaforma > Sicurezza del sistema),il valore predefinito di **Tipo di password richiesto** viene modificato:

Da: Impostazione predefinita dispositivo A: Almeno numerico

Si applica a: Android, Android Enterprise

Per visualizzare queste impostazioni, vedere [Android](compliance-policy-create-android.md) e [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usare una chiave precondivisa in un profilo Wi-Fi di Windows 10 <!-- 2662938 -->
Con questo aggiornamento, è possibile usare una chiave precondivisa con il protocollo di sicurezza WPA/WPA2-Personal per autenticare un profilo di configurazione Wi-Fi per Windows 10. È anche possibile specificare la configurazione dei costi per una rete a consumo per i dispositivi nell'aggiornamento di Windows 10 di ottobre 2018.

Attualmente, per poter usare una chiave precondivisa è necessario importare un profilo Wi-Fi o creare un profilo personalizzato. In [Impostazioni Wi-Fi per Windows 10](wi-fi-settings-windows.md) sono elencate le impostazioni correnti. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Rimuovere i certificati PKCS e SCEP dai dispositivi <!-- 3218390 -->
In alcuni scenari i certificati PKCS e SCEP rimangono nei dispositivi, anche quando si rimuove un criterio da un gruppo, si elimina una distribuzione di configurazione o conformità o un amministratore aggiorna un profilo SCEP o PKCS esistente. Questo aggiornamento modifica il comportamento. Esistono alcuni scenari in cui i certificati PKCS e SCEP vengono rimossi dai dispositivi e alcuni scenari in cui i certificati rimangono nel dispositivo. Per informazioni su questi scenari, vedere [Rimuovere i certificati SCEP e PKCS in Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Usare Gatekeeper nei dispositivi macOS per la conformità <!-- 2504381 -->
Questo aggiornamento include macOS Gatekeeper per valutare la conformità dei dispositivi. Per impostare la proprietà di Gatekeeper, [aggiungere criteri di conformità per i dispositivi macOS](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="enrollment-abandonment-report----1382924---"></a>Report sull'abbandono delle registrazioni <!-- 1382924 -->
Un nuovo report con i dettagli sulle registrazioni abbandonate è disponibile in **Registrazione del dispositivo** > **Monitoraggio**. Per altre informazioni, vedere [Report Abbandono del portale aziendale](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nuova funzionalità Condizioni per l'utilizzo di Azure Active Directory <!-- 2870393 -->
Azure Active Directory ha una funzionalità Condizioni per l'utilizzo che è possibile usare al posto delle condizioni di Intune esistenti. La funzionalità Condizioni per l'utilizzo di Azure AD offre maggiore flessibilità sule condizioni da visualizzare e su quando visualizzarle, un migliore supporto della localizzazione, maggiore controllo sul rendering delle condizioni e creazione di report migliorata. La funzionalità Condizioni per l'utilizzo di Azure AD richiede Azure Active Directory Premium P1 che fa parte della suite Enterprise Mobility + Security E3. Per altre informazioni, vedere l'articolo [Gestire termini e condizioni aziendali per l'accesso degli utenti](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Supporto della modalità Proprietario dispositivo Android <!--3188762-->
Per Samsung Knox Mobile Enrollment, Intune supporta ora la registrazione dei dispositivi nella modalità di gestione Proprietario dispositivo Android. Gli utenti connessi a reti Wi-Fi o cellulari possono eseguire la registrazione con pochi tocchi quando accendono il dispositivo per la prima volta. Per altre informazioni, vedere [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Registrare automaticamente i dispositivi Android usando Samsung Knox Mobile Enrollment).

### <a name="device-management"></a>Gestione dei dispositivi
#### <a name="new-settings-for-software-updates------1907869---"></a>Nuove impostazioni per gli aggiornamenti software   <!-- 1907869 -->  
- È ora possibile configurare alcune notifiche per avvisare gli utenti finali della necessità di un riavvio per completare l'installazione degli aggiornamenti software più recenti.   
- È ora possibile configurare una richiesta di avviso per i riavvii che vengono eseguiti al di fuori dell'orario di lavoro. Tali richieste supportano gli scenari BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Raggruppare i dispositivi registrati con Windows Autopilot per ID correlatore <!-- 2075110 -->
Intune supporta ora il raggruppamento dei dispositivi Windows per ID correlatore quando vengono registrati usando [Autopilot per i dispositivi esistenti](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) tramite Configuration Manager. L'ID correlatore è un parametro del file di configurazione di Autopilot. Intune imposterà automaticamente l'[attributo del dispositivo Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) su "OfflineAutopilotprofile-<correlator ID>. In questo modo sarà possibile creare gruppi dinamici di Azure AD arbitrari in base all'ID correlatore tramite l'attributo enrollmentprofileName per le registrazioni di Autopilot offline. Per altre informazioni, vedere [Windows Autopilot per dispositivi esistenti](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Criteri di Protezione app di Intune <!-- 2984657 -->
I criteri di protezione delle app di Intune consentono di configurare varie impostazioni di protezione dei dati per le app protette da Intune, ad esempio Microsoft Outlook e Microsoft Word. È stato modificato l'aspetto di queste impostazioni sia per [iOS](app-protection-policy-settings-ios.md) che per [Android](app-protection-policy-settings-android.md) in modo che sia più facile trovare le singole impostazioni. Sono tre le categorie di impostazioni dei criteri:
- **Rilocazione dei dati**: questo gruppo include i controlli di prevenzione della perdita dei dati, ad esempio le restrizioni relative alle operazioni Taglia, Copia, Incolla e Salva con nome. Queste impostazioni determinano la modalità con cui gli utenti interagiscono con i dati nelle app.
- **Requisiti di accesso**: questo gruppo contiene le opzioni PIN per ogni app che determinano in che modo l'utente finale accede alle app in un contesto aziendale.  
- **Avvio condizionale**: questo gruppo contiene impostazioni come le impostazioni minime del sistema operativo, il rilevamento di jailbreak e dispositivi rooted e i periodi di prova offline.  
  
La funzionalità delle impostazioni non cambia, ma sarà più semplice trovarle quando si usa il flusso di creazione dei criteri.

### <a name="intune-apps"></a>App di Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune supporterà una dimensione massima dei pacchetti pari a 8 GB per le app line-of-business <!-- 1727158 -->
Intune ha aumentato le dimensioni massime consentite per i pacchetti a 8 GB per le app line-of-business. Per altre informazioni, vedere [Aggiungere app a Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Aggiungere l'immagine del marchio personalizzata per l'app Portale aziendale <!-- 1916266 -->
Gli amministratori di Microsoft Intune possono caricare un'immagine del marchio personalizzata da visualizzare come sfondo nella pagina del profilo utente nell'app Portale aziendale di iOS. Per altre informazioni sulla configurazione dell'app Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune manterrà la lingua localizzata di Office durante gli aggiornamenti di Office nei computer degli utenti finali <!-- 2971030 -->
Quando Intune installa Office nei computer dell'utente finale, i Language Pack sono gli stessi usati nelle precedenti installazioni di Office MSI. Per altre informazioni, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nuova esperienza di supporto di Intune nel portale di Gestione dei dispositivi per Microsoft 365 <!-- 3076965 -->
Verrà implementata una nuova esperienza di Guida e supporto tecnico per Intune nel [portale di Gestione dei dispositivi per Microsoft 365]( http://devicemanagement.microsoft.com). La nuova esperienza consente di descrivere il problema con parole proprie e di ricevere informazioni dettagliate per la risoluzione dei problemi e contenuti Web per la correzione. Queste soluzioni sono offerte tramite un algoritmo di apprendimento automatico basato su regole, creato in base alle indagini condotte tra gli utenti.  

Oltre alle indicazioni specifiche per il problema, è anche possibile usare il nuovo flusso di lavoro di creazione di un caso per aprire un caso di supporto tramite posta elettronica o telefono.  

Per i clienti che fanno parte dell'implementazione, questa nuova esperienza sostituisce l'esperienza di Guida e supporto tecnico corrente basata su un set statico di opzioni preselezionate a seconda dell'area della console usata quando si apre Guida e supporto tecnico.  

*Questa nuova esperienza di Guida e supporto tecnico verrà implementata solo in alcuni tenant ed è disponibile nel portale di gestione dei dispositivi. I partecipanti a questa nuova esperienza vengono selezionati casualmente tra i tenant di Intune disponibili. Con l'espansione dell'implementazione, verranno aggiunti nuovi tenant.*  

Per altre informazioni, vedere [Nuova esperienza di Guida e supporto tecnico](get-support.md#help-and-support-experience) in Come ottenere supporto per Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Modulo di PowerShell per Intune: anteprima disponibile <!-- 951068 -->
Un nuovo modulo di PowerShell, che offre il supporto per l'API di Intune attraverso Microsoft Graph, è ora disponibile in anteprima in [GitHub]( https://aka.ms/intunepowershell). Per informazioni dettagliate sull'uso di questo modulo, vedere il file Leggimi in tale percorso. 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>Settimana del 15 ottobre 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Richiesta del PIN quando si modificano le impronte digitali o l'ID del viso in un dispositivo iOS  <!-- 2637704  -->
Agli utenti viene ora richiesto un PIN dopo la modifica dei dati biometrici nel proprio dispositivo iOS. Sono incluse le modifiche per le impronte digitali registrate o l'ID viso. La tempistica della richiesta dipende dalla configurazione del timeout per *Controlla di nuovo i requisiti di accesso dopo (minuti)* .  Se non è impostato alcun PIN, all'utente viene richiesto di configurarne uno. 
 
Questa funzionalità è disponibile solo per iOS e richiede la partecipazione delle applicazioni che integrano Intune APP SDK per iOS, versione 9.0.1 o successive. L'integrazione dell'SDK è necessaria in modo che il comportamento possa essere applicato nelle applicazioni di destinazione. Questa integrazione avviene sistematicamente e dipende dai team delle applicazioni specifiche. Tra le app partecipanti sono inclusi WXP, Outlook, Managed Browser e Yammer.


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>Settimana dell'1 ottobre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Accedere alle proprietà principali del profilo tramite l'app Portale aziendale <!-- 772203 -->
Gli utenti finali possono ora accedere alle proprietà e alle azioni principali per l'account, come la reimpostazione della password, dall'app Portale aziendale. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune possono impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non saranno visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Accesso agli account utente delle app Intune nei dispositivi gestiti iOS e Android <!-- 1248496 -->
L'amministratore di Microsoft Intune può controllare gli account utente che vengono aggiunti alle applicazioni di Microsoft Office nei dispositivi gestiti. Può limitare l'accesso agli account utente consentiti dell'organizzazione e bloccare gli account personali nei dispositivi registrati. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Criteri di configurazione delle app di Outlook iOS e Android <!--1828527 -->
È ora possibile creare criteri di configurazione delle app per Outlook per iOS e Android per gli utenti locali che usano l'autenticazione di base con il protocollo ActiveSync. Ulteriori impostazioni di configurazione verranno aggiunte non appena abilitate per Outlook per iOS e Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire sarà possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Estensioni file delle app line-of-business (LOB) di Windows <!-- 1884873 -->
Le estensioni file delle app line-of-business di Windows ora includono *msi*, *appx*, *appxbundle*, *msix* e *msixbundle*. È possibile aggiungere un'app in Microsoft Intune selezionando **App client** > **App** > **Aggiungi**. Viene visualizzato il riquadro **Aggiungi app** che consente di selezionare il **Tipo di app**. Per le app line-of-business di Windows, selezionare il tipo di app **App line-of-business**, selezionare il **File del pacchetto dell'app** e quindi specificare un file di installazione con l'estensione appropriata.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Distribuzione di app di Windows 10 con Intune <!-- 2309001 -->
Basandosi sul supporto esistente per le app line-of-business e le app di Microsoft Store per le aziende, gli amministratori possono usare Intune per distribuire la maggior parte delle applicazioni esistenti dell'organizzazione per gli utenti finali in dispositivi Windows 10. Gli amministratori possono aggiungere, installare e disinstallare le applicazioni per gli utenti di Windows 10 in una vasta gamma di formati, ad esempio MSI, Setup.exe o MSP. Intune valuterà le regole dei requisiti prima del download e dell'installazione, notificando agli utenti finali lo stato o i requisiti di riavvio tramite il centro notifiche di Windows 10. Questa funzionalità sbloccherà di fatto le organizzazioni interessate a spostare questo carico di lavoro in Intune e nel cloud. Questa funzionalità è attualmente disponibile in anteprima pubblica e si prevede che verranno aggiunte nuove importanti funzioni nei prossimi mesi. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Dispositivo dell'utente finale e menu di scelta rapida delle app <!-- 2771453 -->
Gli utenti finali possono ora usare il menu di scelta rapida in un dispositivo e nelle app per attivare azioni comuni come la ridenominazione di un dispositivo o la verifica della conformità. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Tasti di scelta rapida del portale aziendale di Windows <!-- 2771518 -->
Gli utenti finali possono usare tasti di scelta rapida per eseguire azioni sulle app e sui dispositivi nell'app Portale aziendale di Windows.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Creare suffissi DNS nei profili di configurazione VPN per i dispositivi che eseguono Windows 10<!-- 1333668 -->
Quando si crea un profilo di configurazione del dispositivo VPN (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo**VPN**) è necessario immettere alcune impostazioni DNS. Con questo aggiornamento, è anche possibile immettere più **suffissi DNS** in Intune. Quando si usano i suffissi DNS, è possibile cercare una risorsa di rete usando il relativo nome breve anziché il nome di dominio completo (FQDN). Questo aggiornamento consente inoltre di modificare l'ordine dei suffissi DNS in Intune.
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md#dns-settings) sono elencate le impostazioni DNS correnti.
Si applica a: Dispositivi Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Supporto dei profili di lavoro per le connessioni VPN sempre attive in Android Enterprise <!-- 1333705 -->
In questo aggiornamento è possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise con profili di lavoro gestiti. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
È possibile abilitare la VPN sempre attiva in **Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Android Enterprise** > **Limitazioni del dispositivo** > **Connettività**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emettere certificati SCEP per i dispositivi senza utenti <!-- 1744554 -->
Attualmente, i certificati vengono rilasciati agli utenti. Con questo aggiornamento, è possibile emettere certificati SCEP per i dispositivi, anche i dispositivi senza utente, come quelli con modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Windows 10 e versioni successive** > profilo **Certificato SCEP**). Altri aggiornamenti includono:
- La proprietà **Oggetto** di un profilo SCEP è ora una casella di testo personalizzata e può includere nuove variabili. 
- La proprietà **Nome alternativo del soggetto** di un profilo SCEP è ora un formato di tabella e può includere nuove variabili. Nella tabella un amministratore può aggiungere un attributo e inserire il valore in una casella di testo personalizzata. Nome alternativo del soggetto supporterà gli attributi seguenti: 
  - DNS
  - Indirizzo di posta elettronica
  - UPN

  Queste nuove variabili possono essere aggiunte con testo statico in una casella di testo personalizzata. Ad esempio, l'attributo DNS può essere aggiunto come `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Le parentesi graffe, il punto e virgola e la barra verticale "{} ; |" non funzioneranno nel testo statico di Nome alternativo del soggetto. Per essere accettate per `Subject` o `Subject alternative name`, le parentesi graffe devono racchiudere solo una delle nuove variabili del certificato dispositivo. 

Nuove variabili del certificato dispositivo:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` funziona solo per i dispositivi Windows e aggiunti a un dominio. 
>  -  Quando si specificano proprietà del dispositivo, ad esempio IMEI, numero di serie e nome di dominio completo, nell'oggetto o nel nome alternativo del soggetto per un certificato del dispositivo, tenere presente che queste proprietà possono essere falsificate da una persona con accesso al dispositivo. 

In [Creare un profilo certificato SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) sono elencate le variabili correnti per la creazione di un profilo di configurazione SCEP. 

Si applica a: Windows 10 e versioni successive e iOS, è supportato per Wi-Fi

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Bloccare in remoto i dispositivi non conformi <!-- 2064495 -->
È possibile creare un'azione nei criteri di conformità che blocca in modalità remota il dispositivo non conforme. In Intune > **Conformità del dispositivo** creare un nuovo criterio o selezionare un criterio esistente > **Proprietà**. Selezionare **Azioni per la non conformità** > **Aggiungi** e scegliere di bloccare in remoto il dispositivo.
Supportato in: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e versioni successive 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Miglioramenti del profilo per la modalità tutto schermo per Windows 10 e versioni successive nel portale di Azure <!-- 2748224 -->
Questo aggiornamento include i miglioramenti seguenti per il profilo di configurazione del dispositivo per modalità tutto schermo per Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo**Modalità tutto schermo (anteprima)** ): 
- Attualmente, è possibile creare più profili per modalità tutto schermo sullo stesso dispositivo. Con questo aggiornamento, Intune supporterà un solo un profilo per modalità tutto schermo per ogni dispositivo. Se servono più profili per modalità tutto schermo in un singolo dispositivo, usare un URI personalizzato.
- In un profilo **Più app in modalità tutto schermo** è possibile selezionare le dimensioni del riquadro dell'applicazione e l'ordine del **layout del menu Start** nella griglia dell'applicazione. Se si desidera un maggiore livello di personalizzazione, è possibile continuare a caricare un file XML.
- Le impostazioni del browser in modalità tutto schermo sono state spostate in **Modalità tutto schermo**. Attualmente, le impostazioni **Web browser in modalità tutto schermo** dispongono di una propria categoria nel portale di Azure.
Si applica a: Windows 10 e versioni successive




### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Applicare il profilo Autopilot ai dispositivi Windows 10 iscritti ma non ancora registrati per Autopilot <!-- 1558983 -->
È possibile applicare il profilo Autopilot ai dispositivi Windows 10 iscritti che non sono stati ancora registrati per Autopilot. Nel profilo di Autopilot, scegliere l'opzione **Converti tutti i dispositivi interessati in Autopilot** per registrare automaticamente i dispositivi non Autopilot con il servizio di distribuzione Autopilot. L'elaborazione della registrazione può richiedere fino a 48 ore. Quando la registrazione viene annullata e il dispositivo viene reimpostato, Autopilot eseguirà il provisioning.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Creare e assegnare vari profili della pagina Stato registrazione ai gruppi di Azure AD <!-- 2526564 -->
È ora possibile [creare e assegnare](windows-enrollment-status.md) vari profili di pagina relativa allo stato della registrazione ai gruppi di Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migrazione da Device Enrollment Program ad Apple Business Manager in Intune <!--2748613-->
Apple Business Manager (ABM) funziona in Intune ed è possibile aggiornare l'account da Device Enrollment Program (DEP) ad ABM. Il processo in Intune è lo stesso. Per aggiornare l'account Apple da DEP ad ABM, passare a [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Schede per gli avvisi e lo stato di registrazione nella pagina di panoramica di registrazione del dispositivo <!--2748656-->
Gli avvisi e gli errori di registrazione vengono ora visualizzati in schede separate nella pagina di panoramica di registrazione del dispositivo.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Limitare le app e bloccare l'accesso alle risorse aziendali nei dispositivi Android <!-- 2451462  -->  
In **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android** > **Sicurezza del sistema** è presente una nuova impostazione nella sezione *Sicurezza dei dispositivi*, denominata **App con restrizioni**. L'impostazione **App con restrizioni** usa un criterio di conformità per impedire l'accesso alle risorse aziendali se determinate app vengono installate nel dispositivo. Il dispositivo è considerato non conforme fino a quando non vengono rimosse le app con restrizioni dal dispositivo.
Si applica a: 
- Android

<!-- ########################### -->
## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
