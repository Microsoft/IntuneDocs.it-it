---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2f9849b2c327397c0b8945ee42d9fca7f9f46250
ms.sourcegitcommit: 58cddb08b64bd60f041eff46ff215e83e13db4e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2018
ms.locfileid: "40001911"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Edizione anticipata per Microsoft Intune - Agosto 2018

> [!Note]
> Notifica accordo di riservatezza: le seguenti modifiche di Intune sono in fase di sviluppo. Queste informazioni sono condivise con accordo di riservatezza su base estremamente limitata. Non pubblicare queste informazioni nei social network o in siti Web pubblici, come Twitter, UserVoice, Reddit e così via. 

L'**edizione anticipata** fornisce un elenco di funzionalità, condivise con accordo di riservatezza, che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non inviare tweet, pubblicare in UserVoice o condividere in altro modo queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello avrà come destinazione utenti e dispositivi <!-- 1106609 -->
Quando si crea un criterio di [Windows Hello for Business](windows-hello.md), questo viene applicato a tutti gli utenti dell'organizzazione (a livello di tenant). Con questo aggiornamento, il criterio può essere applicato anche a utenti specifici o a dispositivi specifici usando un criterio di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Identity Protection** > **Windows Hello for Business**).

In Intune nel portale di Azure la configurazione e le impostazioni di Windows Hello esisteranno sia in **Registrazione del dispositivo** che in **Configurazione del dispositivo**. **Registrazione del dispositivo** è associato all'intera organizzazione (a livello di tenant) e supporta Windows AutoPilot (Configurazione guidata). **Configurazione del dispositivo** è associato a dispositivi e utenti tramite un criterio applicato durante l'archiviazione.

Si applica a:  
- Windows 10 e versioni successive
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Controllare la modalità S in dispositivi Windows 10 e versioni successive - anteprima pubblica <!-- 1958649 -->
Sarà possibile creare un profilo di configurazione del dispositivo per disattivare la modalità S in un dispositivo Windows 10 o impedire agli utenti di disattivare la modalità S nel dispositivo. Questa funzionalità sarà in Intune > **Configurazione del dispositivo** > **Profili** >  **Windows 10 e versioni successive** > **Edition upgrade and mode switch** (Aggiornamento edizione e cambio modalità).
Per altre informazioni sulla modalità S, vedere [Ti presentiamo Windows 10 in modalità S](https://www.microsoft.com/windows/s-mode).
Si applica a: Windows 10 e versioni successive (1809 e versioni successive)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Aggiornamenti del supporto della VPN moderna per iOS <!-- 2459928, 1819876, and 2650856 -->
Un aggiornamento futuro offrirà supporto per i client VPN iOS seguenti: 
- F5 Access (versione 3.0.1 e successive)
- Citrix SSO
- Palo Alto Networks GlobalProtect (versione 5.0 e successive) Sempre in un aggiornamento futuro:
- I tipi di connessione **F5 Access** esistenti verranno rinominati **F5 Access Legacy** (per gli aggiornamenti della personalizzazione F5)
- I tipi di connessione **Palo Alto Networks GlobalProtect** esistenti verranno rinominati **Legacy Palo Alto Networks GlobalProtect** (per gli aggiornamenti della personalizzazione Palo Alto). 

I profili esistenti con questi tipi di connessione continuano a funzionare con il client VPN legacy. Se si usa Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN o Legacy Palo Alto Networks GlobalProtect con iOS, è consigliabile passare alle nuove app. Effettuare questo passaggio il prima possibile per assicurarsi che l'accesso VPN sia disponibile per i dispositivi iOS quando viene eseguito l'aggiornamento a iOS 12.

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloccare il portale aziendale nella modalità app singola fino all'accesso dell'utente <!--1067692 --> 
Sarà possibile eseguire il portale aziendale in modalità app singola se si autentica un utente tramite il portale aziendale invece che tramite Assistente configurazione durante la registrazione DEP. Questa opzione blocca il dispositivo immediatamente dopo il completamento di Assistente configurazione così che un utente deve effettuare l'accesso per accedere al dispositivo. Questo processo assicura che il dispositivo completi l'onboarding e non rimanga orfano in uno stato senza utenti associati.

### <a name="scope-tags-for-policies---1081974-eeready--"></a>Tag di ambito per i criteri <!--1081974 eeready-->

Sarà possibile creare tag di ambito per limitare l'accesso alle risorse di Intune. Aggiungere un tag di ambito a un'assegnazione di ruolo e quindi aggiungere il tag di ambito a un profilo di configurazione. Il ruolo potrà accedere solo alle risorse con profili di configurazione con tag di ambito corrispondenti (o nessun tag di ambito).
Per creare un tag di ambito, scegliere **Ruoli di Intune** > **Ambito (tag)** > **Crea**.
Per aggiungere un tag di ambito a un'assegnazione di ruolo, scegliere **Ruoli di Intune** > **Tutti i ruoli** > **Policy and Profile Manager (Gestione criteri e profili)** > **Assegnazioni** > **Ambito (tag)**.
Per aggiungere un tag di ambito a un profilo di configurazione, scegliere **Configurazione del dispositivo** > **Profili** > scegliere un profilo > **Proprietà** > **Ambito (tag)**.

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Assegnare un utente e un nome descrittivo a un dispositivo di Autopilot <!--1346521 -->
Una futura anteprima pubblica consentirà agli amministratori di assegnare un utente a un singolo dispositivo di Autopilot.  Gli amministratori potranno anche assegnare nomi descrittivi per rivolgersi all'utente quando configura il dispositivo con Autopilot.

Si applica a: Windows Insider build 1809 o successiva (durante l'anteprima).

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP Apple usato da un altro software MDM <!-- 1488946 -->
Intune rileverà e visualizzerà i dettagli se un token VPP (Volume Purchase Program) Apple viene usato sia da Intune che da un altro software MDM.

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Supporto del tunnel di pacchetti per profili VPN per app iOS per i tipi di connessione personalizzata e Pulse Secure <!-- 1520957 -->
Quando si usano i profili VPN per app iOS, sarà possibile usare il tunneling a livello di app (proxy delle app) o il tunneling a livello di pacchetto (tunnel di pacchetti). Queste opzioni saranno disponibili con i tipi di connessione seguenti:
- VPN personalizzata
- Pulse Secure Se non si conosce il valore da usare, consultare la documentazione del provider VPN.
Si applica a: iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler è una connessione disponibile per i profili VPN in iOS <!-- 1769858 eeready -->
Quando si crea un profilo di configurazione del dispositivo VPN iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **iOS** > tipo di profilo **VPN**), sono disponibili diversi tipi di connessione, inclusi Cisco, Citrix e altri. Un aggiornamento futuro aggiunge Zscaler come tipo di connessione. 
Per i tipi di connessione disponibili, vedere [Impostazioni VPN per i dispositivi che eseguono iOS](vpn-settings-ios.md).

### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloccare le registrazioni dei dispositivi personali Windows <!-- 1849498 -->
Sarà possibile impedire ai dispositivi personali Windows la registrazione con la [gestione di dispositivi mobili](windows-enroll.md) in Intune. I dispositivi registrati con l'[agente del computer di Intune](manage-windows-pcs-with-microsoft-intune.md) non possono essere bloccati con questa funzionalità.
Per visualizzare questa funzionalità, scegliere **Registrazione del dispositivo** > **Limitazioni del dispositivo**.
L'attivazione di questa limitazione non ha effetto sui dispositivi già registrati.
Dopo l'attivazione di una restrizione, Intune verificherà che ogni nuova richiesta di registrazione Windows sia stata autorizzata come registrazione aziendale. I metodi seguenti si qualificano per essere autorizzati come registrazione aziendale:
- L'utente che esegue la registrazione usa un [account del manager di registrazione dispositivi]( device-enrollment-manager-enroll.md).
- Il dispositivo viene registrato tramite [Windows Autopilot](enrollment-autopilot.md).
- Il numero IMEI del dispositivo viene elencato in **Registrazione del dispositivo** > **[Identificatori dei dispositivi aziendali]( corporate-identifiers-add.md)**).
- Il dispositivo viene registrato tramite un [pacchetto di provisioning in blocco](windows-bulk-enroll.md).
- Il dispositivo viene registrato tramite la [registrazione automatica da SCCM per la co-gestione](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management).

Le registrazioni non autorizzate verranno bloccate. Le registrazioni seguenti sono contrassegnate come aziendali da Intune, ma dal momento che non offrono all'amministratore di Intune il controllo per ogni dispositivo, verranno bloccate:
- [Registrazione MDM automatica](windows-enroll.md#enable-windows-10-automatic-enrollment) con l'[aggiunta ad Azure Active Directory durante la configurazione di Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).
- [Registrazione MDM automatica](windows-enroll.md#enable-windows-10-automatic-enrollment) con [aggiunta ad Azure Active Directory dalla configurazione di Windows](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md).

Verranno bloccati anche i seguenti metodi di registrazione personale:
- [Registrazione MDM automatica](windows-enroll.md#enable-windows-10-automatic-enrollment) con [aggiunta dell'account aziendale dalle impostazioni di Windows](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup).
- Solo l'[opzione di registrazione MDM]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) dalle impostazioni di Windows.

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Specificare i modelli di nome computer in un profilo di Autopilot <!--1849855-->
Sarà possibile specificare un modello di nome computer per generare e impostare il [nome computer](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante la registrazione di Autopilot. Sarà necessario specificarlo nel profilo di Autopilot presente in **Registrazione del dispositivo** > **Registrazione Windows** > **Windows Autopilot Deployment service** (Servizio Windows Autopilot Deployment) > **Profili**. Si possono usare solo caratteri alfanumerici e trattini.
Si applica a: Windows Insider build 1809 o successiva (durante l'anteprima).

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Vengono visualizzati il numero di versione e il numero di build di iOS <!-- 1892471 -->
In **Conformità del dispositivo** > **Conformità del dispositivo** viene visualizzata la versione del sistema operativo iOS. In un aggiornamento futuro verrà anche visualizzato il numero di build.
Quando vengono rilasciati aggiornamenti della sicurezza, Apple lascia in genere il numero di versione invariato, ma aggiorna il numero di build. Visualizzando il numero di build, è possibile verificare facilmente se è installato un aggiornamento di una vulnerabilità.

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Per i profili di Windows Autopilot, nascondere le opzioni per cambiare l'account nella pagina di accesso aziendale e nella pagina degli errori di dominio <!--1901669 -->
Un'anteprima pubblica includerà nuove opzioni del profilo di Windows Autopilot che consentiranno agli amministratori di nascondere le opzioni per cambiare l'account nelle pagine di accesso aziendale e degli errori di dominio. Per nascondere queste opzioni, è necessario configurare le informazioni personalizzate distintive dell'azienda in Azure Active Directory. Si applica a: Windows Insider build 1809 o successiva (durante l'anteprima).

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Ritardo quando vengono visualizzati gli aggiornamenti del software iOS sul dispositivo <!-- 1949583 -->
In Intune > **Aggiornamenti software** > **Criteri di aggiornamento per iOS** è possibile configurare i giorni e gli orari in cui i dispositivi non devono installare aggiornamenti. In un aggiornamento futuro sarà possibile rimandare il momento in cui visualizzare un aggiornamento software sul dispositivo, da 1 a 90 giorni. 
Per le impostazioni correnti, vedere [Configurare i criteri di aggiornamento per iOS in Microsoft Intune](software-updates-ios.md).

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivi ritirati nel dashboard della conformità dei dispositivi <!-- 1981119 -->
In un aggiornamento futuro i dispositivi ritirati verranno rimossi dal dashboard della conformità dei dispositivi. Questa operazione modificherà i numeri di conformità.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nuova esperienza utente per il sito Web del portale aziendale <!--2000968 -->
Verranno aggiunte nuove funzionalità al sito Web del portale aziendale, in base ai suggerimenti dei clienti. Si noterà un miglioramento significativo delle funzionalità esistenti e dell'usabilità dei dispositivi Android, iOS e Windows. Diverse aree del sito, ad esempio i dettagli del dispositivo, i commenti e suggerimenti, il supporto e la panoramica del dispositivo, presentano una nuova progettazione, moderna e reattiva. Saranno inoltre disponibili:
- Flussi di lavoro semplificati in tutte le piattaforme per dispositivi
- Flussi di identificazione e registrazione dei dispositivi ottimizzati
- Messaggi di errore più utili
- Linguaggio più intuitivo, con meno gergo tecnico
- Possibilità di condividere collegamenti diretti alle app
- Miglioramento delle prestazioni per i cataloghi di app di grandi dimensioni
- Maggiore accessibilità per tutti gli utenti

### <a name="office-365-proplus-version----2213968-eeready---"></a>Versione di Office 365 ProPlus <!-- 2213968 eeready -->
Durante l'assegnazione delle app di Office 365 ProPlus ai dispositivi Windows 10 con Intune, sarà possibile selezionare la versione di Office. Nel portale di Azure selezionare **Microsoft Intune** > **App** > **Aggiungi app**. Selezionare quindi **Office 365 ProPlus Suite (Windows 10)** nell'elenco a discesa **Tipo**. Selezionare **Impostazioni della suite di app** per visualizzare il pannello associato. Impostare **Canale di aggiornamento** su un valore, ad esempio **Ogni mese**. Rimuovere facoltativamente l'altra versione di Office (MSI) dai dispositivi degli utenti finali selezionando **Sì**. Selezionare **Specifica** per installare una versione specifica di Office per il canale selezionato nei dispositivi degli utenti finali. A questo punto, è possibile selezionare la **versione specifica** di Office da usare. Le versioni disponibili cambieranno nel corso del tempo. Quando si crea una nuova distribuzione, le versioni disponibili potrebbero quindi essere più recenti e alcune versioni precedenti potrebbero non essere disponibili. Le distribuzioni correnti continueranno a distribuire la versione precedente, ma l'elenco delle versioni verrà continuamente aggiornato per ogni canale. Per altre informazioni, vedere [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurare il profilo per ignorare alcune schermate durante l'esecuzione di Assistente configurazione <!-- 2276470 -->
Quando si crea un profilo di registrazione macOS, sarà possibile configurarlo per ignorare qualsiasi schermata seguente quando un utente esegue Assistente configurazione:
- Android Migration (Migrazione Android)
- Display Tone (Tono schermo)
- Privacy
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Modifica nel processo di aggiornamento per i connettori locali <!-- 2277554 -->
In base al feedback dei clienti, cambierà il modo in cui gli aggiornamenti vengono eseguiti nei connettori locali. Dopo aver installato un connettore locale, gli aggiornamenti verranno eseguiti automaticamente. Questa modifica inizierà con il nuovo connettore di certificati PFX per Microsoft Intune e successivamente verrà applicata ad altri tipi di connettori locali. 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Supporto per l'impostazione di registrazione DNS per VPN di Windows 10 <!-- 2282852 -->
Sarà possibile configurare i profili VPN di Windows 10 per registrare in modo dinamico gli indirizzi IP assegnati all'interfaccia VPN con il DNS interno, senza dover usare profili personalizzati.
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md) sono elencate le impostazioni dei profili VPN correnti disponibili. 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>Limitare le app e bloccare l'accesso alle risorse aziendali nei dispositivi iOS e Android for Work <!-- 2451462 -->
In **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android for Work** > **Sicurezza del sistema** sarà disponibile una nuova impostazione **Restricted applications** (Applicazioni con restrizioni). Questa nuova impostazione usa un criterio di conformità per impedire l'accesso alle risorse aziendali se determinate app vengono installate nel dispositivo. Il dispositivo è considerato non conforme fino a quando non vengono rimosse le app con restrizioni dal dispositivo.
Si applica a: 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>Esportare i criteri di conformità del portale di Azure classico in un file CSV <!-- 2469637 -->
I criteri di conformità creati nel portale di Azure classico saranno deprecati.  In questo caso, sarà possibile esaminare ed eliminare eventuali criteri esistenti, ma non aggiornarli. È possibile esportare i criteri come file con valori delimitati da virgole (CSV), quindi usare i dettagli nel file per ricreare tali criteri nel portale di Intune di Azure.
> [!IMPORTANT]
> Quando il portale di Azure classico viene ritirato, non è possibile accedere ai criteri, neppure per visualizzarli. Assicurarsi quindi di esportarli e di crearli di nuovo nel portale di Azure prima che il portale di Azure classico venga ritirato.

### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Modifica delle terminologia in "ritirare" e "cancellare" <!-- 2175759 -->
Per garantire la coerenza con l'API Graph, nell'interfaccia utente e nella documentazione di Intune verranno cambiati i termini seguenti:
- **Rimuovere i dati aziendali** verrà cambiato in **ritirare**
- **Ripristino delle impostazioni predefinite** verrà cambiato in **cancellare**



<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Più opportunità di sincronizzazione nell'app Portale aziendale per Windows <!-- 2683177 -->
Un'azione di sincronizzazione dei dispositivi sarà aggiunta alla barra delle applicazioni e agli elementi alle Jump List del menu Start nell'app Portale aziendale per Windows. Fare clic sull'azione in una delle due posizioni per sincronizzare velocemente i dispositivi e accedere alle risorse aziendali.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Reimpostare i passcode dei dispositivi dall'app del portale aziendale per Windows 10 <!-- 2101282 --> 
I dipendenti potranno presto reimpostare il PIN o passcode del proprio dispositivo direttamente dall'app del portale aziendale per Windows 10. Questa funzionalità sarà disponibile nei dispositivi gestiti da Intune remoti e locali che supportano la reimpostazione di passcode. A seconda del tipo di dispositivo, una richiesta effettuata per un dispositivo remoto rimuove il passcode corrente del dispositivo oppure crea un passcode temporaneo. Gli utenti che richiedono una reimpostazione per un dispositivo locale vengono reindirizzati all'app Impostazioni del dispositivo.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Nuove esperienze di esplorazione nell'app Portale aziendale per Windows <!-- 2317227 -->  
Durante l'esplorazione o la ricerca di app nell'app Portale aziendale per Windows è possibile passare dalla visualizzazione **Riquadri** alla nuova visualizzazione **Dettagli** e viceversa. La nuova visualizzazione elenca i dettagli dell'applicazione, ad esempio il nome, l'editore, la data di pubblicazione e lo stato di installazione.  

La pagina **App** introdurrà una visualizzazione **Installata** che consente di visualizzare i dettagli sulle installazioni completate e in corso. Per condividere commenti e suggerimenti o opinioni sulle modifiche apportate, inviare il proprio feedback nell'app Portale aziendale.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Esperienza dell'app Portale aziendale migliorata per gli utenti del manager di registrazione dispositivi <!-- 675800 -->
Quando un manager di registrazione dispositivi accede all'app Portale aziendale per Windows, l'app elenca solo il dispositivo in esecuzione corrente. Questo miglioramento ridurrà i timeout che in precedenza si verificavano quando l'app tentava di caricare tutti i dispositivi registrati nel manager di registrazione dispositivi.  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Usare le licenze di dispositivo VPP per effettuare il provisioning anticipato del portale aziendale durante la registrazione DEP <!-- 1608345 -->
È possibile usare le licenze di dispositivo Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante le registrazioni DEP (Device Enrollment Program). A tale scopo, quando si crea o si modifica un profilo di registrazione, specificare il token VPP che si vuole usare per installare il portale aziendale. Assicurarsi che il token non abbia una scadenza e di avere un numero sufficiente di licenze per l'app del portale aziendale. Se il token ha una scadenza o se il numero di licenze è insufficiente, Intune esegue il push del portale aziendale dell'App Store (che richiederà l'immissione di un ID Apple).

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Estensioni file delle app line-of-business (LOB) di Windows <!-- 1884873 -->
Le estensioni file delle app line-of-business di Windows ora includono *msi*, *appx*, *appxbundle*, *msix* e *msixbundle*. È possibile aggiungere un'app in Microsoft Intune selezionando **App per dispositivi mobili** > **App** > **Aggiungi**. Viene visualizzato il riquadro **Aggiungi app** che consente di selezionare il **Tipo di app**. Per le app line-of-business di Windows, selezionare il tipo di app **App line-of-business**, selezionare il **File del pacchetto dell'app** e quindi specificare un file di installazione con l'estensione appropriata.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Pacchetto di configurazione Windows Defender ATP aggiunto automaticamente al profilo di configurazione <!-- 2144658 -->
Quando vengono usati [Advanced Threat Protection e dispositivi onboarding](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) in Intune, viene eseguito il download di un pacchetto di configurazione che viene aggiunto al profilo di configurazione. In un aggiornamento futuro Intune otterrà automaticamente il pacchetto da Windows Defender Security Center e lo aggiungerà al profilo.

Si applica a Windows 10 e versioni successive.

### <a name="check-for-sccm-compliance----2192052---"></a>Controllare la conformità SCCM <!-- 2192052 -->
Un aggiornamento futuro includerà una nuova impostazione di conformità SSCM (System Center Configuration Manager) (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10**). SCCM invia segnali per la conformità di Intune. Usando l'impostazione di Intune è possibile richiedere che tutti i segnali SCCM restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In SCCM questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Si applica a Windows 10 e versioni successive

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invia un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Conferma richieste per l'eliminazione del token VPP usato per il provisioning anticipato del portale aziendale <!-- 2237634 -->
Viene richiesta la conferma dell'eliminazione di un token VPP (Volume Purchase Program) se il token viene usato per il provisioning anticipato del portale aziendale durante la registrazione DEP.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Impostazioni di protezione aggiuntive per Windows Installer <!-- 2282430 -->
Sarà possibile consentire agli utenti di controllare l'installazione delle app. Se l'opzione è abilitata, le installazioni che a causa di una violazione della protezione verrebbero arrestate possono precedere. Sarà possibile indicare a Windows Installer di usare privilegi elevati durante l'installazione di un qualsiasi programma in un sistema. Sarà anche possibile abilitare l'indicizzazione degli elementi Windows Information Protection e l'archiviazione dei relativi metadati in una posizione non crittografata. Quando i criteri sono disabilitati, gli elementi protetti da Windows Information Protection non vengono indicizzati e non appaiono nei risultati di Cortana o Esplora file. Le funzionalità di queste opzioni sono disabilitate per impostazione predefinita. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune potranno impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non sono visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Richiedere un passcode non biometrico per l'avvio e il timeout dell'app <!-- 1506985 -->

Se si richiede un passcode non biometrico all'avvio dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** > **Aggiungi criterio** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire sarà possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App per dispositivi mobili** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Anteprima di una nuova esperienza utente per il sito Web del portale aziendale <!--2000968 -->
Attualmente vengono aggiunte nuove funzionalità, in base ai suggerimenti dei clienti, al sito Web del portale aziendale/catalogo delle app iOS. Si noterà un miglioramento significativo delle funzionalità esistenti e dell'usabilità dei dispositivi Android, iOS e Windows. Diverse aree del sito, ad esempio i dettagli del dispositivo, i commenti e suggerimenti, il supporto e la panoramica del dispositivo, presentano una nuova progettazione, moderna e reattiva. Saranno inoltre disponibili:

- Flussi di lavoro semplificati in tutte le piattaforme per dispositivi
- Flussi di identificazione e registrazione dei dispositivi ottimizzati
- Messaggi di errore più utili
- Linguaggio più intuitivo, con meno gergo tecnico
- Possibilità di condividere collegamenti diretti alle app
- Miglioramento delle prestazioni per i cataloghi di app di grandi dimensioni
- Maggiore accessibilità per tutti gli utenti

L'aggiornamento è attualmente in anteprima. È possibile registrarsi per partecipare all'anteprima all'indirizzo http://aka.ms/webcpflighting

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Richiedere un passcode non biometrico per l'avvio a freddo e il timeout dell'app <!-- 1506985 --> 

Se si richiede un passcode non biometrico all'avvio a freddo dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** > **Aggiungi criterio** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacità di distribuire le app line-of-business (LOB) necessarie a tutti gli utenti nei dispositivi Windows 10 Desktop <!-- 1627835 RS4 -->
I clienti saranno in grado di distribuire le app line-of-business di Windows 10 da installare in contesti di dispositivo. In questo modo le app saranno disponibili per tutti gli utenti del dispositivo. Questa opzione è disponibile solo per i dispositivi Windows 10 Desktop.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aggiornamento dell'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android <!--1631531 -->

L'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android verrà aggiornata e adattata alle procedure consigliate per le app Android. L'app Portale aziendale per Android verrà aggiornata nei prossimi mesi in modo da suddividere la voce di menu **Guida e commenti e suggerimenti** in due voci distinte, **Guida** e **Invia commenti e suggerimenti**. La pagina **Guida** conterrà una sezione **Domande frequenti** e il pulsante **Supporto e-mail** per invitare gli utenti a caricare log in Microsoft e a inviare e-mail al supporto aziendale per descrivere i problemi incontrati. **Invia commenti e suggerimenti** guiderà l'utente nella procedura standard Microsoft per l'invio di commenti e suggerimenti che richiederà all'utente di indicare una preferenza, una mancanza di preferenza o un'idea.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Criteri di protezione delle app <!-- 679615 -->
I criteri di Protezione app di Intune offrono la possibilità di creare criteri predefiniti globali per attivare rapidamente la protezione per tutti gli utenti nell'intero tenant.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).



