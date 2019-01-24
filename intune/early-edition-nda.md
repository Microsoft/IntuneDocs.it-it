---
title: Edizione anticipata - Microsoft Intune
titlesuffix: ''
description: Edizione anticipata di Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/16/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: d1b553d262200e58a4c06dd0f4bcb72ca1398080
ms.sourcegitcommit: 911923e9fe0eed52b1c93e400f776956835e582f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2019
ms.locfileid: "54386981"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Edizione anticipata di Microsoft Intune: gennaio 2019

> [!Note]
> Notifica sull'accordo di riservatezza: Le seguenti modifiche di Intune sono in fase di sviluppo. Queste informazioni sono condivise con accordo di riservatezza su base estremamente limitata. Non pubblicare queste informazioni nei social network o in siti Web pubblici, come Twitter, UserVoice, Reddit e così via. 

L'**edizione anticipata** fornisce un elenco di funzionalità, condivise con accordo di riservatezza, che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non inviare tweet, pubblicare in UserVoice o condividere in altro modo queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>App Android Enterprise <!-- 1352553  -->
Sarà possibile eliminare da Microsoft Intune le app di Google Play gestite. Per eliminare un'app di Google Play gestita, sarà necessario aprire Microsoft Intune nel portale di Azure e selezionare **App Client** > **App**. Dall'elenco di app, sarà necessario selezionare i puntini di sospensione (...) a destra dell'app di Google Play gestita e quindi selezionare **Elimina** dall'elenco visualizzato. Quando si elimina un'app di Google Play gestita dall'elenco di app, l'app risulta automaticamente non approvata.

### <a name="managed-google-play-app-type----1352580---"></a>Tipo di app Google Play gestito <!-- 1352580 -->
Il tipo di app **Google Play gestito** consentirà di aggiungere in modo specifico [app Google Play gestite](https://play.google.com/work/search?q=microsoft&c=apps) a Intune. L'amministratore di Intune potrà esplorare, cercare, approvare, sincronizzare e assegnare in Intune app di Google Play gestite approvate. Non sarà più necessario passare alla console di Google Play separatamente e rieseguire l'autenticazione. In Intune selezionare **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di App** selezionare **Google Play gestito** come tipo di app.

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Distribuzione di app Microsoft Store per le aziende con licenza online <!-- 1672660  -->
Sarà possibile assegnare le app Microsoft Store per le aziende con licenza online richieste nel contesto del dispositivo. Questo tipo di distribuzione di app Microsoft Store per le aziende consentirà di installare le app per tutti gli utenti nel dispositivo. Questa opzione è disponibile solo per i dispositivi desktop Windows 10 RS4 e versioni successive. L'opzione di installazione nel contesto del dispositivo è disponibile nella pagina di assegnazione di App Client per le app con licenza online MSFB.

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>Configurare il profilo per ignorare alcune schermate durante l'esecuzione di Assistente configurazione <!-- 2276470  -->
Quando si crea un profilo di registrazione macOS, sarà possibile configurarlo per ignorare tutte le schermate seguenti quando un utente esegue Assistente configurazione:
- Android Migration (Migrazione Android)
- Display Tone (Tono schermo)
- Privacy
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>Assegnare profili di Autopilot al gruppo virtuale Tutti i dispositivi <!--2715522  -->
Sarà possibile assegnare profili di Autopilot al gruppo virtuale Tutti i dispositivi. A questo scopo, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > scegliere un profilo > **Assegnazioni** > in **Assegna a** scegliere **Tutti i dispositivi**. Per altre informazioni sui profili di AutoPilot, vedere [Registrare dispositivi Windows con Windows AutoPilot](enrollment-autopilot.md).

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>Personalizzare lo sfondo nei dispositivi iOS con supervisione con un profilo di configurazione del dispositivo <!-- 2809324  -->
Quando si crea un profilo di configurazione dispositivo per i dispositivi iOS, sarà possibile consentire o limitare alcune impostazioni selezionando **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per tipo di profilo. Questo aggiornamento include nuove impostazioni **Wallpaper** (Sfondo) che consentono agli amministratori di usare un'immagine con estensione png, jpg o jpeg come sfondo, eseguire l'anteprima dell'immagine e impedire agli utenti di modificare lo sfondo. Le impostazioni dello sfondo si applicano solo ai dispositivi con supervisione. Per un elenco delle impostazioni correnti, vedere [Impostazioni relative alle limitazioni per i dispositivi iOS in Microsoft Intune](device-restrictions-ios.md).

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifiche di tipo avviso popup per app Win32 <!-- 3136566   -->
Sarà possibile eliminare la visualizzazione delle notifiche di tipo avviso popup degli utenti finali per ogni assegnazione di app. Da Intune, selezionare **App Client** > **App** > selezionare l'app > **Assegnazioni** > **Include Groups** (Includi gruppi). 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>La Condivisione dei contatti tramite Bluetooth viene rimossa in Limitazioni del dispositivo > Proprietario dispositivo per Android Enterprise <!-- 3598396 -->
Quando si crea un profilo di limitazione per i dispositivi Android Enterprise, è disponibile un'impostazione **Condivisione dei contatti tramite Bluetooth**. In questo aggiornamento l'impostazione **Condivisione dei contatti tramite Bluetooth** verrà rimossa (**Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo > Proprietario dispositivo** per tipo di profilo > **Generale**). 

L'impostazione **Condivisione contatti tramite Bluetooth** non è supportata per la gestione dei proprietari di dispositivi Android Enterprise. Pertanto, la rimozione di questa impostazione non influisce su alcun dispositivo o tenant, anche se l'impostazione è abilitata e configurata nell'ambiente in uso.

Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

Si applica a: Proprietario dispositivo Android Enterprise

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Distribuzione di app Android Enterprise APP-WE <!-- 1171203 -->
Per i dispositivi Android in uno scenario di distribuzione APP-WE (App Protection Policy Without Enrollment) non registrato, sarà possibile usare Google Play gestito per distribuire app dello Store e app LOB agli utenti. In particolare, il reparto IT può fornire agli utenti finali un catalogo di app e un'esperienza di installazione che non richiede più agli utenti finali di ridurre le condizioni di sicurezza dei propri dispositivi consentendo installazioni da origini sconosciute. Inoltre, questo scenario di distribuzione fornirà un'esperienza migliorata per gli utenti finali.

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK supporterà le chiavi di crittografia a 256 bit <!-- 1832174 -->
Intune App SDK per Android userà le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. L'SDK continuerà a supportare le chiavi a 128 bit per garantire la compatibilità con il contenuto e le app che usano versioni precedenti dell'SDK.


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Aggiornamento del metodo di autenticazione e dell'installazione dell'app Portale aziendale per i criteri di Intune <!-- 1927359 -->
Nei dispositivi già registrati tramite l'Assistente configurazione con uno dei metodi di registrazione dei dispositivi aziendali di Apple, Intune non supporterà più l'app Portale aziendale se installata manualmente dagli utenti finali dall'App Store. Questa modifica è rilevante solo quando si esegue l'autenticazione con Apple Setup Assistant durante la registrazione. Questa modifica riguarda inoltre solo i dispositivi iOS registrati tramite:  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple Device Enrollment Program (DEP)

Gli utenti riceveranno un errore se installano l'app Portale aziendale dall'App Store e quindi provano a registrare i dispositivi tramite tale app. È previsto che questi dispositivi usino l'app Portale aziendale solo quando ne è stato eseguito il push automaticamente da Intune durante la registrazione. I profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Se si vuole che gli utenti dei dispositivi DEP dispongano dell'app Portale aziendale, è necessario specificare le preferenze in un profilo di registrazione. Inoltre, la schermata **Identifica il dispositivo** nell'app Portale aziendale diventerà presto obsoleta.  
Per installare l'app Portale aziendale nei dispositivi DEP già registrati, si dovrà passare a Intune > App client ed eseguirne il push come app gestita con i criteri di configurazione delle app. Informazioni dettagliate su come eseguire questi passaggi saranno disponibili in articoli futuri della documentazione.

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>I non amministratori possono abilitare BitLocker nei dispositivi Windows 10 aggiunti ad Azure AD<!-- 2147379 -->
Quando si abilitano le impostazioni di BitLocker nei dispositivi Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo**  >  **Windows 10 e versioni successive** per la piattaforma > **Endpoint Protection** per il tipo di profilo > **Crittografia Windows**), si aggiungono impostazioni BitLocker. Questo aggiornamento include una nuova impostazione di BitLocker per consentire agli utenti standard (non amministratori) di abilitare la crittografia. Per visualizzare le impostazioni correnti, vedere [Impostazioni di Endpoint Protection per Windows 10](endpoint-protection-windows-10.md#windows-encryption).


### <a name="additional-settings-for-outlook----3301182---"></a>Impostazioni aggiuntive per Outlook<!-- 3301182 -->
Ora è possibile configurare ulteriori impostazioni per Outlook per iOS e Android usando Intune.  Le impostazioni includono:
- Consentire solo agli account aziendali o dell'istituto di istruzione di essere usati in Outlook su iOS o Android
- Distribuire gli account locali dell'autenticazione moderna per Office 365 e dell'autenticazione moderna ibrida
- Usare `SAMAccountName` per il campo nome utente nel profilo di posta elettronica quando è selezionata l'autenticazione di base
- Consentire di salvare i contatti
- Configurare i suggerimenti di posta elettronica per i destinatari esterni
- Configurare **Posta in arrivo evidenziata**
- Richiedere alla biometria di accedere a Outlook per iOS 
- Bloccare le immagini esterne

> [!NOTE]
> Se si usano i criteri di protezione delle app di Intune per gestire l'accesso per le identità aziendali, non abilitare **Richiedi biometria**. Per altre informazioni, vedere **Richiedi credenziali aziendali per l'accesso** per [Requisiti di accesso iOS](app-protection-policy-settings-ios.md#access-settings) e [Requisiti di accesso Android](app-protection-policy-settings-android.md#access-settings).

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>I modelli amministrativi sono disponibili in anteprima pubblica e sono stati spostati nel profilo di configurazione corrispondente <!-- 3322847 -->
I modelli amministrativi in Intune (**Configurazione del dispositivo** > **Modelli amministrativi**) sono attualmente in anteprima privata. Con questo aggiornamento: i modelli amministrativi includono circa 300 impostazioni che possono essere gestite in Intune. In precedenza, queste impostazioni erano disponibili solo in Editor Criteri di gruppo.
I modelli amministrativi sono disponibili in anteprima pubblica. I modelli amministrativi vengono spostati da **Configurazione del dispositivo** > **Modelli amministrativi** a **Configurazione del dispositivo** > **Profili** >**Crea profilo** > in **Piattaforma** scegliere  **Windows 10 e versioni successive**, in **Tipo di profilo** scegliere **Modelli amministrativi**.
La creazione di report è abilitata. Si applica a: Windows 10 e versioni successive

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Modalità scura del portale aziendale Intune per macOS <!-- 3300524 -->
Il portale aziendale Intune ora supporta la modalità scura per macOS. Quando si abilita la modalità scura in un dispositivo macOS 10.14 o versione successiva, il portale aziendale regola i colori in modo da riflettere tale modalità.

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Usare le impostazioni consigliate da Microsoft con le baseline di sicurezza <!-- 2055484 -->
Intune si integra con altri servizi specifici per la sicurezza, inclusi Windows Defender ATP e Office 365 ATP. I clienti manifestano l'esigenza di una strategia comune e di un set integrato di flussi di lavoro di sicurezza end-to-end nei servizi di Microsoft 365. L'obiettivo è l'allineamento delle strategie per creare soluzioni in grado di conciliare le operazioni di sicurezza e le comuni attività degli amministratori. Per realizzare questo obiettivo in Intune, è stato pubblicato un set di "baseline di sicurezza" consigliate da Microsoft (**Intune** > **Baseline di sicurezza**).  Un amministratore potrà creare criteri di sicurezza direttamente da queste baseline e quindi distribuirle agli utenti. Può anche personalizzare le indicazioni sulle procedure consigliate per soddisfare le esigenze dell'organizzazione. Intune verifica che i dispositivi rimangano conformi a queste baseline e invia agli amministratori una notifica sugli utenti e i dispositivi non conformi.

### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Supporto di cancellazione selettiva per dispositivi WIP senza registrazione <!-- 1434452 -->
Windows Information Protection senza registrazione (WIP-WE, Windows Information Protection Without Enrollment) consente ai clienti di proteggere i dati aziendali nei dispositivi Windows 10 senza la necessità di una registrazione MDM (Mobile Device Management, gestione di dispositivi mobili) completa. Quando i documenti sono protetti da criteri WIP-WE, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, si rendono inutilizzabili tutti i dati protetti tramite criteri WIP-WE. Da Intune nel portale di Azure selezionare **App per dispositivi mobili** > **Cancellazione selettiva di app**.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>Impostazioni dei criteri di protezione dell'app per i dati Web <!-- 2662995 -->
Le impostazioni dei criteri di protezione dell'app per il contenuto Web nei dispositivi iOS e Android verranno aggiornate per gestire meglio i collegamenti Web sia http che https, nonché il trasferimento dei dati tramite i collegamenti universali iOS e i collegamenti delle app Android.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP Apple usato da un altro software MDM <!-- 1488946 -->
Intune rileverà e visualizzerà i dettagli se un token VPP (Volume Purchase Program) Apple viene usato sia da Intune che da un altro software MDM.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivi ritirati nel dashboard della conformità dei dispositivi <!-- 1981119 -->
In un aggiornamento futuro i dispositivi ritirati verranno rimossi dal dashboard della conformità dei dispositivi. Questa operazione modificherà i numeri di conformità.



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificare la conformità di Configuration Manager <!-- 2192052 -->
Un aggiornamento futuro includerà una nuova impostazione di conformità System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10**). Configuration Manager invia segnali per la conformità di Intune. Usando l'impostazione di Intune è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Si applica a Windows 10 e versioni successive



## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).



