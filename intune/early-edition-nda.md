---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0f6447f4a5cfb2638278a59414e83f744adb8c81
ms.sourcegitcommit: ed97b68f08c1a8469f0b45bc1c839a0b5f5c71e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2018
ms.locfileid: "45978264"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Edizione anticipata per Microsoft Intune - Settembre 2018

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>Accesso agli account utente delle app di Intune nei dispositivi gestiti iOS e Android <!-- ! 1248496  -->

L'amministratore di Microsoft Intune sarà in grado di controllare gli account utente che vengono aggiunti alle applicazioni di Microsoft Office nei dispositivi gestiti. Potrà limitare l'accesso agli account utente consentiti dell'organizzazione e bloccare gli account personali nei dispositivi registrati. 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>Creare suffissi DNS nei profili di configurazione VPN per i dispositivi che eseguono Windows 10 <!-- 1333668 -->
Quando si crea un profilo di configurazione del dispositivo VPN (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo**VPN**) è necessario immettere alcune impostazioni DNS. Sarà anche possibile immettere più **suffissi DNS** in Intune. Quando si usano i suffissi DNS, è possibile cercare una risorsa di rete utilizzando il relativo nome breve anziché il nome di dominio completo (FQDN). Questo aggiornamento consente inoltre di modificare l'ordine dei suffissi DNS in Intune.
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md#dns-settings) sono elencate le impostazioni DNS correnti.
Si applica ai dispositivi Windows 10

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Supporto dei profili di lavoro per le connessioni VPN sempre attive in Android Enterprise <!-- 1333705 -->
È possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise con profili di lavoro gestiti. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
L'impostazione VPN sempre attiva sarà in **Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Android Enterprise** > **Limitazioni del dispositivo** in **Work Profiles Only (Solo profili di lavoro)** per il tipo di profilo > **Connettività**. 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>Criteri di configurazione delle app di Outlook for iOS e Android <!--1828527 -->
Sarà possibile creare un criterio di configurazione per iOS per le app di Outlook for iOS e Android. Ulteriori impostazioni di configurazione verranno aggiunte non appena attivate per Outlook per iOS e Android.

###  <a name="windows-line-of-business-lob-app-file-extensions----1884873---"></a>Estensioni file delle app line-of-business (LOB) di Windows <!-- 1884873 -->
Le estensioni file delle app line-of-business di Windows includeranno *msi*, *appx*, *appxbundle*, *msix* e *msixbundle*. Sarà possibile aggiungere un'app in Microsoft Intune selezionando **App client** > **App** > **Aggiungi**. Verrà visualizzato il riquadro **Aggiungi app** che consente di selezionare il **Tipo di app**. Per le app line-of-business di Windows, selezionare il tipo di app **line-of-business**, selezionare il **File del pacchetto dell'app** e quindi specificare un file di installazione con l'estensione appropriata.

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>Bloccare in remoto i dispositivi non conformi <!-- 2064495 -->
Sarà possibile creare un'azione nei criteri di conformità che blocca in modalità remota il dispositivo non conforme. In Intune > **Conformità del dispositivo** creare un nuovo criterio o selezionare un criterio esistente. Selezionare **Azioni per la non conformità** > **Aggiungi** e scegliere di bloccare in remoto il dispositivo.
Supportato in: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e versioni successive 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM <!-- 2244713 -->
Sarà possibile separare il controllo delle impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM dall'impostazione dell'identità dell'utente registrato. Gli amministratori che non usano IntuneMAMUPN non noteranno alcuna variazione di comportamento. Quando questa funzionalità è disponibile, gli amministratori che usano IntuneMAMUPN per controllare il trasferimento dei dati nei dispositivi registrati dovranno esaminare le nuove impostazioni e aggiornare le impostazioni dell'app di conseguenza.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usare una chiave precondivisa in un profilo Wi-Fi di Windows 10 <!-- 2662938 -->
Sarà possibile usare una chiave precondivisa con il protocollo di protezione WPA/WPA2-Personal per autenticare un profilo di configurazione Wi-Fi per Windows 10.
Attualmente, per poter usare una chiave precondivisa è necessario importare un profilo Wi-Fi o creare un profilo personalizzato. In [Impostazioni Wi-Fi per Windows 10](wi-fi-settings-windows.md) sono elencate le impostazioni correnti. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995-eeready---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 eeready -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Frequenza di sincronizzazione dei dispositivi AutoPilot aumentata a ogni 12 ore <!-- 2753673 -->
I dispositivi AutoPilot verranno sincronizzati ogni 12 ore anziché ogni 24 ore.

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Applicare il profilo Autopilot ai dispositivi Windows 10 iscritti ma non ancora registrati per Autopilot <!-- 1558983 -->
È possibile applicare il profilo Autopilot ai dispositivi Windows 10 iscritti che non sono stati ancora registrati per Autopilot. Nel profilo di Autopilot, scegliere l'opzione **Converti tutti i dispositivi interessati in Autopilot** per registrare automaticamente i dispositivi non Autopilot con il servizio di distribuzione Autopilot. L'elaborazione della registrazione può richiedere fino a 48 ore. Quando la registrazione viene annullata e il dispositivo viene reimpostato, Autopilot eseguirà il provisioning. 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>Creare e assegnare vari profili di pagina relativa allo stato della registrazione ai gruppi di Azure AD <!-- 2526564-->
Sarà possibile creare e assegnare vari profili di pagina relativa allo stato della registrazione ai gruppi di utenti di Azure AAD.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Aggiornamenti della pagina di intestazione e ridenominazione del nodo in Intune <!--2867309 -->
Gli aggiornamenti alla pagina di destinazione di Intune includeranno l'aggiunta di nuovi riquadri di monitoraggio e grafici e la modifica di quelli esistenti allo scopo di migliore la visualizzazione dei dati. Il modo **App per dispositivi mobili** diventerà **App client**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Maggiore accesso per gli utenti finali che usano l'app Portale aziendale <!-- 772203 -->
Gli utenti finali potranno accedere ad azioni chiave per l'account, ad esempio la reimpostazione della password e al proprio profilo AAD, nell'app Portale aziendale.

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emettere certificati SCEP per i dispositivi senza utenti <!-- 1744554 -->
Attualmente, i certificati vengono rilasciati agli utenti. Sarà possibile emettere certificati SCEP per i dispositivi, anche i dispositivi senza utente, come quelli con modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Windows 10 e versioni successive** > profilo **Certificato SCEP**). Gli altri aggiornamenti includeranno:
- La proprietà **Oggetto** di un profilo SCEP è ora una casella di testo personalizzata e può includere nuove variabili. 
- La proprietà **Nome alternativo del soggetto** di un profilo SCEP è ora un formato di tabella e può includere nuove variabili. Nella tabella un amministratore può aggiungere un attributo e inserire il valore in una casella di testo personalizzata. Nome alternativo del soggetto supporterà gli attributi seguenti: 
  - DNS
  - Indirizzo di posta elettronica
  - UPN Queste nuove variabili possono essere aggiunte con testo statico in una casella di testo personalizzata. Ad esempio, l'attributo DNS può essere aggiunto come `DNS = {{AzureADDeviceId}}.domain.com`.
  > [!NOTE]
  > Le parentesi graffe, il punto e virgola e la barra verticale "{} ; |" non funzioneranno nel testo statico di Nome alternativo del soggetto. Per essere accettate per `Subject` o `Subject alternative name`, le parentesi graffe devono racchiudere solo una delle nuove variabili del certificato dispositivo. Nuove variabili del certificato dispositivo:  
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

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Miglioramenti del profilo per modalità tutto schermo per Windows 10 e versioni successive nel portale di Azure <!-- 2748224 eeready -->
Il profilo di configurazione del dispositivo per modalità tutto schermo per Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo **Modalità tutto schermo (anteprima)**) verrà migliorato: 
- Attualmente, è possibile creare più profili per modalità tutto schermo sullo stesso dispositivo. Con questo aggiornamento, Intune supporterà un solo un profilo per modalità tutto schermo per ogni dispositivo. Se servono più profili per modalità tutto schermo in un singolo dispositivo, usare un URI personalizzato.
-In un profilo **Più app in modalità tutto schermo** è possibile selezionare le dimensioni del riquadro dell'applicazione e l'ordine del **layout del menu Start** nella griglia dell'applicazione. Se si desidera un maggiore livello di personalizzazione, è possibile continuare a caricare un file XML.
- Le impostazioni del browser in modalità tutto schermo sono state spostate in **Modalità tutto schermo**. Attualmente, le impostazioni **Web browser in modalità tutto schermo** dispongono di una propria categoria nel portale di Azure.
Si applica a: Windows 10 e versioni successive

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Esperienza dell'app Portale aziendale migliorata per gli utenti del manager di registrazione dispositivi <!-- 675800 -->
Quando un manager di registrazione dispositivi accede all'app Portale aziendale per Windows, l'app elenca solo il dispositivo in esecuzione corrente. Questo miglioramento ridurrà i timeout che in precedenza si verificavano quando l'app tentava di caricare tutti i dispositivi registrati nel manager di registrazione dispositivi.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificare la conformità di Configuration Manager <!-- 2192052 -->
Un aggiornamento futuro includerà una nuova impostazione di conformità System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10**). Configuration Manager invia segnali per la conformità di Intune. Usando l'impostazione di Intune è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Si applica a Windows 10 e versioni successive

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invia un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Impostazioni di protezione aggiuntive per Windows Installer <!-- 2282430 -->
Sarà possibile consentire agli utenti di controllare l'installazione delle app. Se l'opzione è abilitata, le installazioni che a causa di una violazione della protezione verrebbero arrestate possono precedere. Sarà possibile indicare a Windows Installer di usare privilegi elevati durante l'installazione di un qualsiasi programma in un sistema. Sarà anche possibile abilitare l'indicizzazione degli elementi Windows Information Protection e l'archiviazione dei relativi metadati in una posizione non crittografata. Quando i criteri sono disabilitati, gli elementi protetti da Windows Information Protection non vengono indicizzati e non appaiono nei risultati di Cortana o Esplora file. Le funzionalità di queste opzioni sono disabilitate per impostazione predefinita. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune potranno impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non sono visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App per dispositivi mobili** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

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



