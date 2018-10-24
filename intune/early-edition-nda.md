---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 72585982cd27962981f581a99f0ea361642df0ee
ms.sourcegitcommit: ba0699cc351954960b222223c60c4ecd50edc829
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49652139"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Edizione anticipata per Microsoft Intune - Ottobre 2018

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Usare le impostazioni consigliate da Microsoft con le baseline di sicurezza <!-- 2055484 -->
Intune si integra con altri servizi specifici per la sicurezza, inclusi Windows Defender ATP e Office 365 ATP. I clienti manifestano l'esigenza di una strategia comune e di un set integrato di flussi di lavoro di sicurezza end-to-end nei servizi di Microsoft 365. L'obiettivo è l'allineamento delle strategie per creare soluzioni in grado di conciliare le operazioni di sicurezza e le comuni attività degli amministratori. Per realizzare questo obiettivo in Intune, è stato pubblicato un set di "baseline di sicurezza" consigliate da Microsoft (**Intune** > **Baseline di sicurezza**).  Un amministratore potrà creare criteri di sicurezza direttamente da queste baseline e quindi distribuirle agli utenti. Può anche personalizzare le indicazioni sulle procedure consigliate per soddisfare le esigenze dell'organizzazione. Intune verifica che i dispositivi rimangano conformi a queste baseline e invia agli amministratori una notifica sugli utenti e i dispositivi non conformi.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>Supporto di Autopilot per i dispositivi ibridi aggiunti ad Azure Active Directory <!-- 1048100 -->
Sarà possibile configurare i dispositivi ibridi aggiunti ad Azure Active Directory usando Autopilot. I dispositivi devono essere aggiunti alla rete dell'organizzazione per usare la funzionalità ibrida di Autopilot.

### <a name="scope-tags-for-apps---1081941---"></a>Tag di ambito per le app <!--1081941 -->
Sarà possibile creare tag di ambito per limitare l'accesso alle risorse di Intune. Aggiungere un tag di ambito a un'assegnazione di ruolo e quindi aggiungere il tag di ambito a un profilo di configurazione. Il ruolo potrà accedere solo alle risorse con profili di configurazione con tag di ambito corrispondenti (o nessun tag di ambito).
Per creare un tag di ambito, scegliere **Ruoli di Intune** > **Ambito (tag)** > **Crea**.
Per aggiungere un tag di ambito a un'assegnazione di ruolo, scegliere **Ruoli di Intune** > **Tutti i ruoli** > **Policy and Profile Manager (Gestione criteri e profili)** > **Assegnazioni** > **Ambito (tag)**.
Per aggiungere un tag di ambito a un profilo di configurazione, scegliere **Configurazione del dispositivo** > **Profili** > scegliere un profilo > **Proprietà** > **Ambito (tag)**.

### <a name="tenant-health-dashboard----1124854---"></a>Dashboard sull'integrità del tenant <!-- 1124854 -->
La pagina Stato del tenant in Intune fornirà in un'unica posizione le informazioni sullo stato del tenant. La pagina è suddivisa in 4 sezioni:  
- **Dettagli del tenant**: contiene informazioni, ad esempio l'autorità MDM, il totale dei dispositivi registrati nel tenant e i conteggi delle licenze. Questa sezione indica anche la versione corrente del servizio per il tenant.
- **Stato del connettore**: contiene informazioni sui connettori configurati, ad esempio Apple VPP, Windows Store for Business e connettori di certificati. In base allo stato corrente, i connettori vengono contrassegnati come *Integro*, *Avviso* o *Non integro*.
- **Integrità del servizio Intune**: contiene gli eventi imprevisti attivi o le interruzioni del tenant. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office ([https://portal.office.com](https://portal.office.com)).
- **Novità su Intune**: contiene i messaggi attivi sul tenant, ad esempio le notifiche che informano che il tenant ha ricevuto le funzionalità di Intune più recenti. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office ([https://portal.office.com](https://portal.office.com)).

### <a name="enrollment-abandonment-report----1382924---"></a>Report sull'abbandono delle registrazioni <!-- 1382924 -->
Un nuovo report con i dettagli sulle registrazioni abbandonate sarà disponibile in **Registrazione del dispositivo** > **Monitoraggio**.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>Criteri WIP distribuiti senza registrazione dell'utente <!-- 1434452 -->
I criteri di Windows Information Protection (WIP) potranno essere distribuiti senza richiedere agli utenti MDM di registrare il dispositivo Windows 10. Questa configurazione non solo consente alle società di proteggere i documenti aziendali in base alla configurazione WIP, ma permette anche agli utenti di continuare a gestire i dispositivi Windows. Quando i documenti sono protetti da un criterio WIP, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, tutti i dati protetti tramite i criteri WIP non saranno più utilizzabili. Da Intune nel portale di Azure selezionare **App per dispositivi mobili** > **Cancellazione selettiva di app**.


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Aggiungere l'immagine del marchio personalizzata per l'app Portale aziendale <!-- 1916266 -->
Gli amministratori di Microsoft Intune potranno caricare un'immagine del marchio personalizzata da visualizzare come sfondo nella pagina del profilo utente nell'app Portale aziendale. Per altre informazioni sulla configurazione dell'app Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md).

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Raggruppare i dispositivi registrati con Windows Autopilot per ID correlatore <!-- 2075110 -->
Intune supporterà il raggruppamento dei dispositivi Windows per ID correlatore quando vengono registrati usando [Autopilot per i dispositivi esistenti](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) tramite Configuration Manager. L'ID correlatore è un parametro del file di configurazione di Autopilot. Intune imposterà automaticamente l'[attributo del dispositivo Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) su "OfflineAutopilotprofile-\<ID correlatore\>". In questo modo sarà possibile creare gruppi dinamici di Azure AD arbitrari in base all'ID correlatore tramite l'attributo enrollmentprofileName per le registrazioni di Autopilot offline. 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Supporto per iOS 12 OAuth nei profili di posta elettronica iOS <!--2155106 -->
I profili di posta elettronica iOS di Intune supporteranno iOS 12 OAuth. Per visualizzare questa funzionalità, scegliere **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **OAuth**. Se questa impostazione viene attivata, verranno eseguite due operazioni:
1. Verrà rilasciato un nuovo profilo ai dispositivi già specificati come destinazione.
2. Agli utenti verrà chiesto di fornire nuovamente le credenziali.

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nuova impostazione predefinita "Tipo di password richiesto" per Android, Android Enterprise<!-- 2649963 -->
Quando si crea un nuovo criterio di conformità (**Intune** > **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android** o **Android Enterprise** per Piattaforma > Sicurezza del sistema),il valore predefinito di **Tipo di password richiesto** viene modificato: Valore predefinito corrente: Impostazione predefinita dispositivo Nuovo valore predefinito: Almeno numerico Si applica a: Android, Android Enterprise

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Assegnare profili di Autopilot al gruppo virtuale Tutti i dispositivi <!--2715522 -->
Sarà possibile assegnare profili di Autopilot al gruppo virtuale Tutti i dispositivi. A questo scopo, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > scegliere un profilo > **Assegnazioni** > in **Assegna a** scegliere **Tutti i dispositivi**.

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nuova funzionalità Condizioni per l'utilizzo di Azure Active Directory <!-- 2870393 -->
Azure Active Directory avrà una funzionalità Condizioni per l'utilizzo che sarà possibile usare al posto delle condizioni di Intune esistenti. La funzionalità Condizioni per l'utilizzo di Azure AD offre maggiore flessibilità sule condizioni da visualizzare e su quando visualizzarle, un migliore supporto della localizzazione, maggiore controllo sul rendering delle condizioni e creazione di report migliorata. La funzionalità Condizioni per l'utilizzo di Azure AD richiede Azure Active Directory Premium P1 che fa parte della suite Enterprise Mobility + Security E3.


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune manterrà la lingua localizzata di Office durante gli aggiornamenti di Office nei computer degli utenti finali <!-- 2971030 -->
Quando Intune installa Office nei computer dell'utente finale, i Language Pack saranno gli stessi usati nelle precedenti installazioni di Office MSI. 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM <!-- 2244713 -->
Sarà possibile separare il controllo delle impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM dall'impostazione dell'identità dell'utente registrato. Gli amministratori che non usano IntuneMAMUPN non noteranno alcuna variazione di comportamento. Quando questa funzionalità è disponibile, gli amministratori che usano IntuneMAMUPN per controllare il trasferimento dei dati nei dispositivi registrati dovranno esaminare le nuove impostazioni e aggiornare le impostazioni dell'app di conseguenza.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usare una chiave precondivisa in un profilo Wi-Fi di Windows 10 <!-- 2662938 -->
Sarà possibile usare una chiave precondivisa con il protocollo di protezione WPA/WPA2-Personal per autenticare un profilo di configurazione Wi-Fi per Windows 10.
Attualmente, per poter usare una chiave precondivisa è necessario importare un profilo Wi-Fi o creare un profilo personalizzato. In [Impostazioni Wi-Fi per Windows 10](wi-fi-settings-windows.md) sono elencate le impostazioni correnti. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Frequenza di sincronizzazione dei dispositivi AutoPilot aumentata a ogni 12 ore <!-- 2753673 -->
I dispositivi AutoPilot verranno sincronizzati ogni 12 ore anziché ogni 24 ore.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Aggiornamenti della pagina di intestazione e ridenominazione del nodo in Intune <!--2867309 -->
Gli aggiornamenti alla pagina di destinazione di Intune includeranno l'aggiunta di nuovi riquadri di monitoraggio e grafici e la modifica di quelli esistenti allo scopo di migliore la visualizzazione dei dati. Il modo **App per dispositivi mobili** diventerà **App client**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Maggiore accesso per gli utenti finali che usano l'app Portale aziendale <!-- 772203 -->
Gli utenti finali potranno accedere ad azioni chiave per l'account, ad esempio la reimpostazione della password e al proprio profilo AAD, nell'app Portale aziendale.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP Apple usato da un altro software MDM <!-- 1488946 -->
Intune rileverà e visualizzerà i dettagli se un token VPP (Volume Purchase Program) Apple viene usato sia da Intune che da un altro software MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Vengono visualizzati il numero di versione e il numero di build di iOS <!-- 1892471 -->
In **Conformità del dispositivo** > **Conformità del dispositivo** viene visualizzata la versione del sistema operativo iOS. In un aggiornamento futuro verrà anche visualizzato il numero di build.
Quando vengono rilasciati aggiornamenti della sicurezza, Apple lascia in genere il numero di versione invariato, ma aggiorna il numero di build. Visualizzando il numero di build, è possibile verificare facilmente se è installato un aggiornamento di una vulnerabilità.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivi ritirati nel dashboard della conformità dei dispositivi <!-- 1981119 -->
In un aggiornamento futuro i dispositivi ritirati verranno rimossi dal dashboard della conformità dei dispositivi. Questa operazione modificherà i numeri di conformità.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Modifica nel processo di aggiornamento per i connettori locali <!-- 2277554 -->
In base al feedback dei clienti, cambierà il modo in cui gli aggiornamenti vengono eseguiti nei connettori locali. Dopo aver installato un connettore locale, gli aggiornamenti verranno eseguiti automaticamente. Questa modifica inizierà con il nuovo connettore di certificati PFX per Microsoft Intune e successivamente verrà applicata ad altri tipi di connettori locali. 

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Esperienza dell'app Portale aziendale migliorata per gli utenti del manager di registrazione dispositivi <!-- 675800 -->
Quando un manager di registrazione dispositivi accede all'app Portale aziendale per Windows, l'app elenca solo il dispositivo in esecuzione corrente. Questo miglioramento ridurrà i timeout che in precedenza si verificavano quando l'app tentava di caricare tutti i dispositivi registrati nel manager di registrazione dispositivi.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificare la conformità di Configuration Manager <!-- 2192052 -->
Un aggiornamento futuro includerà una nuova impostazione di conformità System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10**). Configuration Manager invia segnali per la conformità di Intune. Usando l'impostazione di Intune è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Si applica a Windows 10 e versioni successive

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invia un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune potranno impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non sono visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>Richiedere un PIN non biometrico dopo il timeout specificato <!-- 1506985 --> 

Se si richiede un PIN non biometrico dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** > **Aggiungi criterio** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aggiornamento dell'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android <!--1631531 -->

L'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android verrà aggiornata e adattata alle procedure consigliate per le app Android. L'app Portale aziendale per Android verrà aggiornata nei prossimi mesi in modo da suddividere la voce di menu **Guida e commenti e suggerimenti** in due voci distinte, **Guida** e **Invia commenti e suggerimenti**. La pagina **Guida** conterrà una sezione **Domande frequenti** e il pulsante **Supporto e-mail** per invitare gli utenti a caricare log in Microsoft e a inviare e-mail al supporto aziendale per descrivere i problemi incontrati. **Invia commenti e suggerimenti** guiderà l'utente nella procedura standard Microsoft per l'invio di commenti e suggerimenti che richiederà all'utente di indicare una preferenza, una mancanza di preferenza o un'idea.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).



