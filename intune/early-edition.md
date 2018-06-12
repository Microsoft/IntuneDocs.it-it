---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745044"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Edizione anticipata per Microsoft Intune - Giugno 2018

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non condividere queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
>Le seguenti modifiche di Intune sono in fase di sviluppo. Per altre informazioni sulle nuove funzionalità ibride, vedere la pagina delle [Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune nel portale di Azure

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>Supporto monouso di proprietà dell'azienda per i dispositivi Android <!-- 1630973 -->

Intune supporta i dispositivi Android con gestione avanzata, bloccati e in modalità tutto schermo. Questo consente agli amministratori di limitare ulteriormente l'uso di un dispositivo a una sola app o un piccolo gruppo di app e impedire agli utenti di abilitare altre app o eseguire altre azioni nel dispositivo.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Supporto macOS per il Device Enrollment Program di Apple<!-- 747651 -->

Intune supporta la registrazione dei dispositivi macOS nel Device Enrollment Program (DEP) di Apple. A tale scopo, procedere nel seguente modo:

1. Su deploy.apple.com assegnare i numeri di serie macOS a un server MDM.
2. Importare i numeri di serie in Intune.
3. Creare un profilo DEP specifico per i dispositivi macOS.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Modifiche del nome Google per Android for Work e Play for Work <!--842873 -->
Intune aggiornerà la terminologia di "Android for Work" in modo da riflettere le modifiche di personalizzazione di Google.  I termini "Android for Work" e "Play for Work" non verranno più usati. Verrà usata un'altra terminologia in base al contesto:

- "Android Enterprise" si riferisce allo stack di gestione per Android moderno nel suo insieme.
- "Profilo di lavoro" o "Profilo proprietario" fa riferimento ai dispositivi BYOD gestiti con i profili di lavoro.
- "Google Play gestito" si riferisce al Google Play Store.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Monitorare lo stato di configurazione delle app iOS per ogni dispositivo <!-- 880037 eeready eestaged -->

L'amministratore di Microsoft Intune può monitorare lo stato di configurazione delle app iOS per ogni dispositivo gestito. Da **Microsoft Intune** nel portale di Azure selezionare **Dispositivi** > **Tutti i dispositivi**. Dall'elenco dei dispositivi gestiti selezionare un dispositivo specifico per visualizzare il relativo pannello. Nel pannello del dispositivo selezionare **Configurazione dell'app**.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune potranno impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non sono visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Creare criteri di conformità dei dispositivi usando le impostazioni del firewall nei dispositivi macOS <!-- 1497640 -->
Quando si creano nuovi criteri di conformità per macOS, in **Conformità del dispositivo** > **Criteri** > **Crea criteri** > **Piattaforma: macOS** > **Protezione del sistema**, saranno disponibili alcune nuove impostazioni del **firewall**: 
- **Firewall**: configurare in che modo le connessioni in ingresso devono essere gestite nell'ambiente in uso.
- **Connessioni in ingresso**: **bloccare** tutte le connessioni in ingresso tranne quelle necessarie per i servizi Internet di base, ad esempio DHCP, Bonjour e IPSec. Questa impostazione consente inoltre di bloccare tutti i servizi di condivisione.
- **Modalità mascheramento**: **abilitare** questa modalità per impedire che il dispositivo risponda alle richieste di probe. Il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate.

Si applica a: macOS 10.12 e versioni successive

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usare sAMAccountName come nome utente dell'account per i profili di posta elettronica <!-- 1500307 -->

Sarà possibile usare l'oggetto **sAMAccountName** locale come nome utente dell'account per i profili di posta elettronica per Android, iOS e Windows 10. Sarà anche possibile ottenere il dominio dall'attributo `domain` o `ntdomain` in Azure Active Directory (Azure AD). In alternativa, immettere un dominio personalizzato statico.

Per usare questa funzionalità, è necessario sincronizzare l'attributo `sAMAccountName` dell'ambiente Active Directory locale con Azure AD.

Si applica a: Android, iOS, Windows 10 e versioni successive

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Richiedere un passcode non biometrico per l'avvio e il timeout dell'app <!-- 1506985 -->

Se si richiede un passcode non biometrico all'avvio dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** > **Aggiungi criterio** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Cancellazione selettiva dei dati delle app dell'organizzazione <!-- 1507030 -->
Gli amministratori potranno configurare una cancellazione selettiva dei dati dell'organizzazione come nuova azione quando non sono soddisfatte le condizioni delle impostazioni di accesso previste dai criteri di protezione delle applicazioni.  Questa funzionalità consente agli amministratori di proteggere e rimuovere automaticamente i dati sensibili dell'organizzazione nelle applicazioni in base a criteri configurati in precedenza.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revoca di un'app iOS acquistata usando VPP <!-- 1777384 -->
L'amministratore di Microsoft Intune potrà revocare la licenza per un'app iOS selezionata acquistata attraverso Volume Purchase Program (VPP). È possibile informare gli utenti quando un'app non è più assegnata a loro. La revoca di una licenza per app non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. Il conteggio delle licenze recuperate è indicato nel nodo **App con licenza** nel carico di lavoro **App** di Intune. Per altre informazioni relative alle app iOS VPP, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire sarà possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App per dispositivi mobili** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revocare la licenza di un'app iOS VPP <!-- 1863797 -->
L'amministratore può recuperare la licenza di un'app iOS VPP assegnata a un utente o dispositivo. La disinstallazione di un'app iOS VPP consente inoltre di recuperare la licenza dell'app. Quindi, è possibile scegliere di assegnare la licenza dell'app a un altro utente o dispositivo. Per altre informazioni sulle licenze delle app iOS VPP, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nuova esperienza utente per il sito Web del portale aziendale <!--2000968 -->
Attualmente vengono aggiunte nuove funzionalità, in base ai suggerimenti dei clienti, al sito Web del portale aziendale. Si noterà un miglioramento significativo delle funzionalità esistenti e dell'usabilità dei dispositivi Android, iOS e Windows. Diverse aree del sito, ad esempio i dettagli del dispositivo, i commenti e suggerimenti, il supporto e la panoramica del dispositivo, presentano una nuova progettazione, moderna e reattiva. Saranno inoltre disponibili:

- Flussi di lavoro semplificati in tutte le piattaforme per dispositivi
- Flussi di identificazione e registrazione dei dispositivi ottimizzati
- Messaggi di errore più utili
- Linguaggio più intuitivo, con meno gergo tecnico
- Possibilità di condividere collegamenti diretti alle app
- Miglioramento delle prestazioni per i cataloghi di app di grandi dimensioni
- Maggiore accessibilità per tutti gli utenti

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modificare le distribuzioni delle app di Office 365 Pro Plus <!-- 2150145 -->
Per l'amministratore di Microsoft Intune sarà più facile modificare le distribuzioni delle app di Office 365 Pro Plus. Nel portale di Azure selezionare **Microsoft Intune** > **App per dispositivi mobili** > **App**. Selezionare la famiglia di prodotti Office 365 Pro Plus dall'elenco delle applicazioni.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Revisione riga per riga degli identificatori duplicati caricati per i dispositivi aziendali <!-- 2203794 -->
Quando si caricano gli ID aziendali, Intune presenta un elenco di tutti i duplicati e offre la possibilità di sostituire o mantenere le informazioni esistenti. Viene visualizzato un report se sono presenti duplicati dopo che sono state scelte le opzioni **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi identificatori**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Aggiungere manualmente gli identificatori dei dispositivi aziendali <!-- 2203803 -->
Gli ID dei dispositivi aziendali potranno essere aggiunti manualmente. Scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi**.

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>Nuovo stato per i dispositivi nella configurazione del dispositivo <!-- 2308882 -->
In **Configurazione del dispositivo** > **Panoramica** vengono aggiunti alcuni nuovi stati:
- riuscito
- Errore
- conflitto
- in sospeso
- non applicabile Viene visualizzata anche un'immagine che illustra il conteggio dei dispositivi di un'altra piattaforma. Ad esempio, se si sta consultando un profilo iOS, il nuovo riquadro indica il numero di dispositivi non iOS assegnati a questo profilo. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>La conformità del dispositivo supporta soluzioni antivirus di terze parti <!-- 2325484 -->
Quando si creano criteri di conformità del dispositivo, in **Conformità del dispositivo** > **Criteri** > **Crea criteri** > **Piattaforma: Windows 10 e versioni successive** > **Impostazioni** > **Protezione del sistema**, saranno disponibili alcune nuove opzioni per la **protezione del dispositivo**: 
- **Antivirus**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando soluzioni antivirus registrate nel Centro sicurezza PC Windows, ad esempio Symantec. 
- **Antispyware**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando soluzioni antispyware registrate nel Centro sicurezza PC Windows, ad esempio Symantec. 

Si applica a: Windows 10 e versioni successive 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Supporto per i profili VPN di Palo Alto Networks GlobalProtect <!-- 1333680 eeready ! -->

Con questo aggiornamento, è possibile scegliere Palo Alto Networks GlobalProtect come tipo di connessione VPN per i profili VPN in Intune (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Tipo di profilo** > **VPN**). In questa versione sono supportate le piattaforme seguenti: 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>Impostare la conformità in base al percorso del dispositivo <!-- 851881 ! -->
In alcuni casi, potrebbe essere necessario limitare l'accesso alle risorse aziendali a un percorso specifico, definito da una connessione di rete. Sarà possibile creare un criterio di conformità (**Conformità del dispositivo** > **Percorsi**) in base all'indirizzo IP del dispositivo. Se il dispositivo non è più compreso nell'intervallo di IP, non può accedere alle risorse aziendali.

Si applica a: dispositivi Android 6.0 e versioni successive, con l'app Portale aziendale aggiornata

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Miglioramento della risoluzione dei problemi di installazione delle app <!-- 928990 -->
Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. È in corso la distribuzione di un'anteprima pubblica delle funzionalità di risoluzione dei problemi delle app. Sotto ogni singolo dispositivo si noterà un nuovo nodo denominato **App gestite**, che elenca le app distribuite tramite MDM di Intune. Nel nodo è visibile un elenco di stati di installazione delle app. Se si seleziona una singola app, si noterà la visualizzazione relativa alla risoluzione dei problemi per l'app specifica. In tale visualizzazione è presente il ciclo di vita end-to-end dell'app, ad esempio quando l'app è stata creata, modificata, specificata come destinazione e distribuita in un dispositivo. Se l'installazione dell'app non è riuscita, saranno anche disponibili il codice di errore e un messaggio sulla causa dell'errore.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Richiedere un passcode non biometrico per l'avvio a freddo e il timeout dell'app <!-- 1506985 --> 

Se si richiede un passcode non biometrico all'avvio a freddo dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** > **Aggiungi criterio** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloccare l'accesso dell'app in base ai fornitori e ai modelli non approvati del dispositivo <!-- 1425689 ! -->
L'amministratore IT di Intune potrà applicare un elenco specificato di produttori Android e/o di modelli iOS tramite i criteri di Protezione app di Intune. L'amministratore IT può fornire un elenco delimitato da punto e virgola di produttori per i criteri Android e di modelli di dispositivo per i criteri iOS. I criteri di Protezione app di Intune sono solo per Android e iOS. Sarà possibile eseguire due azioni distinte su questo elenco specificato:
- Blocco dell'accesso delle app nei dispositivi non specificati.
- Cancellazione selettiva dei dati aziendali nei dispositivi non specificati. 

L'utente non potrà accedere all'applicazione di destinazione se non vengono soddisfatti i requisiti definiti tramite i criteri. In base alle impostazioni, è possibile che l'utente venga bloccato o che i dati aziendali nell'app vengano cancellati in modo selettivo. Nei dispositivi iOS questa funzionalità richiede il supporto delle applicazioni (WXP, Outlook, Managed Browser, Yammer) per l'integrazione di Intune APP SDK, in modo che le impostazioni relative alla versione minima possano essere applicate per le applicazioni di destinazione. Questa integrazione avviene progressivamente e dipende dai team delle applicazioni specifiche. In Android questa funzionalità richiede il portale aziendale più recente. 

Nei dispositivi degli utenti finali il client Intune eseguirà un'azione in base a una semplice corrispondenza delle stringhe specificate nel pannello Intune per i criteri di protezione delle applicazioni. Ciò dipende completamente dal valore segnalato dal dispositivo. Di conseguenza, è opportuno che l'amministratore IT si assicuri che il comportamento previsto sia accurato. A tale scopo, è possibile testare questa impostazione con svariati produttori di dispositivi e modelli destinati a un piccolo gruppo di utenti. In Microsoft Intune selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** per visualizzare e aggiungere i criteri di protezione delle app. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app](app-protection-policy.md).

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Abilitare la modalità tutto schermo nei dispositivi Windows 10 <!-- 1560072 ! -->
Nei dispositivi Windows 10 è possibile creare un profilo di configurazione e abilitare la modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** > **Restrizioni del dispositivo** > **Modalità tutto schermo**). In questo aggiornamento l'impostazione **Modalità tutto schermo (anteprima)** viene rinominata **Chiosco multimediale (obsoleto)**. Non è più consigliabile usare **Chiosco multimediale (obsoleto)**, che tuttavia continuerà a funzionare fino all'aggiornamento di luglio. **Chiosco multimediale (obsoleto)** viene sostituito dal nuovo tipo di profilo **Modalità tutto schermo** (**Crea profilo** > **Windows 10** > **Modalità tutto schermo (anteprima)**), che conterrà le impostazioni per configurare le modalità tutto schermo in Windows 10 RS4 e versioni successive.

Si applica a Windows 10 e versioni successive.

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Recuperare l'ID modello utente dell'app associato per le app di Microsoft Store per le aziende in modalità tutto schermo <!-- 1560077 ! -->
Intune potrà recuperare gli ID modello utente dell'app per le app di Microsoft Store per le aziende per offrire una configurazione ottimizzata del profilo in modalità tutto schermo.

Per altre informazioni sulle app di Microsoft Store per le aziende, vedere [Gestire le app di Microsoft Store per le aziende](windows-store-for-business.md).

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Azioni di accesso per i criteri di protezione delle app <!-- 1483510 EEready -->
Presto sarà possibile configurare i criteri di protezione delle app per cancellare i dati in modo esplicito, bloccare o segnalare i dispositivi non conformi. La nuova azione di *cancellazione* rimuove i dati aziendali da un dispositivo. Se si verifica una cancellazione, all'utente del dispositivo vengono notificati sia il motivo della cancellazione che la procedura di correzione. Per alcune impostazioni, come la versione minima del sistema operativo, sarà possibile applicare più azioni, ad esempio il blocco e la cancellazione. Queste azioni vengono attivate quando viene avviata l'app.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Nuove informazioni di inventario per i dispositivi Windows <!-- 1333569 eeready -->

Per ogni dispositivo Windows, nella scheda **Hardware** (**Gruppi** > **Tutti i dispositivi mobili** > **Dispositivi** > scegliere il dispositivo dell'utente > **Visualizza proprietà** > **Hardware**) saranno disponibili le informazioni di inventario seguenti:
- TPM
- Antivirus
- Antispyware
- Firewall
- UAC
- Batteria
- Nome dominio

Per altre informazioni sul modo in cui questi dati vengono recuperati dal provider del servizio di crittografia, vedere le voci relative a DeviceStatus nell'articolo [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) (CSP DeviceStatus).

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune e il browser Microsoft Edge <!-- 1818969 -->
Il browser Microsoft Edge per i dispositivi mobili (iOS e Android) ora supporta i criteri di protezione delle app di Intune. Gli utenti che accedono con gli account Azure AD aziendali nell'applicazione browser Microsoft Edge saranno protetti da Intune. 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nuova impostazione per lingua/area quando si configura la Configurazione guidata per Autopilot <!-- 1821766 -->
Sarà disponibile una nuova impostazione di configurazione per impostare la lingua e l'area dei profili di Autopilot durante la Configurazione guidata.

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuova impostazione per configurare la tastiera del dispositivo <!-- 1821768 -->
Sarà disponibile una nuova impostazione per configurare la tastiera per i profili di Autopilot durante la Configurazione guidata.

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Usare TeamViewer per condividere lo schermo dei dispositivi iOS e MacOS <!-- 1985547 -->
È attualmente possibile usare TeamViewer per amministrare in remoto i [dispositivi Android e Windows gestiti da Intune](device-profile-android-teamviewer.md).

Gli amministratori potranno connettersi a TeamViewer e avviare un sessione di condivisione dello schermo con i dispositivi iOS e macOS. Gli utenti di iPhone, iPad e macOS possono condividere gli schermi in tempo reale con altri dispositivi mobili o desktop. 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Grafico utente del profilo del dispositivo nuovamente disponibile <!-- 2160133 -->
Durante il miglioramento dei conteggi numerici visualizzati nel grafico del profilo del dispositivo (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**), il grafico utente è stato temporaneamente rimosso.

Con questo aggiornamento, il grafico utente è di nuovo disponibile e visibile nel portale di Azure.

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Assegnare tutti gli utenti e tutti i dispositivi come gruppi ambito <!-- 2196803 -->
Sarà possibile assegnare tutti gli utenti, tutti i dispositivi e tutti gli utenti e tutti i dispositivi nei gruppi ambito. A tale scopo, scegliere **Ruoli di Intune** > **Tutti i ruoli** > **Policy and Profile Manager** >  (Gestione criteri e profili) **Assegnazioni** > scegliere un'assegnazione **Ambito (gruppi)**.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Spostamento dei profili AutoPilot nei gruppi di destinazione <!-- 1877935 -->
I profili di distribuzione AutoPilot possono attualmente essere assegnati a dispositivi selezionati. Dopo il rilascio di questa funzionalità, per assegnare i profili, sarà necessario eseguire queste operazioni:
- Creare gruppi (Azure AD) contenenti dispositivi AutoPilot
- Assegnare i profili desiderati a un gruppo di Azure AD. Il profilo AutoPilot verrà assegnato ai dispositivi AutoPilot presenti in tale gruppo.

### <a name="management-name-field-will-be-editable----1875989---"></a>Il campo Nome di gestione sarà modificabile <!-- 1875989 -->
Sarà possibile modificare il campo Nome di gestione nel pannello **Proprietà** di un dispositivo. Per modificare questo campo, scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Proprietà**. È possibile usare il campo Nome di gestione per identificare in modo univoco un dispositivo.

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Aggiunte alle impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1403702 -->
Sarà possibile configurare impostazioni aggiuntive per le opzioni di sicurezza dei dispositivi locali Windows 10. Le impostazioni aggiuntive saranno disponibili per le aree relative ai client di rete Microsoft, ai server di rete Microsoft, all'accesso e alla sicurezza di rete e all'accesso interattivo. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

### <a name="rules-for-removing-devices----1609459---"></a>Regole di rimozione dei dispositivi <!-- 1609459 -->
Saranno disponibili nuove regole che consentiranno di rimuovere automaticamente i dispositivi che non si sono connessi per un numero di giorni specificato. Per visualizzare la nuova regola, passare al riquadro **Intune**, selezionare **Dispositivi**e selezionare **Device removal rules** (Regole rimozione dispositivi).

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitare app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot<!-- 1621980 -->
Sarà possibile impedire l'installazione di app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot. Per visualizzare questa funzionalità, passare a **Intune** > **Registrazione del dispositivo** > **Registrazione Windows** > **Windows AutoPilot profiles** (Profili Windows AutoPilot)  > **Crea nuovo** > **Impostazioni di registrazione**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Supporto di Exchange Connector multipli <!-- 2070451 -->

Non è più previsto il limite di un Microsoft Intune Exchange Connector per tenant. Intune supporta Exchange Connector multipli per consentire la configurazione dell'accesso condizionale in Intune per più organizzazioni di Exchange locali.

Con un On-premises Exchange Connector di Intune è possibile gestire l'accesso dei dispositivi alle cassette postali di Exchange locali in base al fatto che i dispositivi siano registrati o meno in Intune e siano conformi ai criteri di conformità dei dispositivi di Intune. Per configurare un connettore, scaricare l'On-premises Exchange Connector di Intune dal portale di Azure e installarlo in un server dell'organizzazione di Exchange. Nel dashboard di Microsoft Intune scegliere **Accesso locale**, quindi nella sezione **Installazione**, scegliere **Connettore per Exchange ActiveSync**. Scaricare l'On-premises Exchange Connector e installarlo in un server della propria organizzazione di Exchange. Ora che non vige più il limite di Exchange Connector per tenant, gli utenti che hanno più organizzazioni di Exchange possono seguire lo stesso processo per scaricare e installare un connettore per ogni organizzazione di Exchange aggiuntiva.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacità di distribuire le app line-of-business (LOB) necessarie a tutti gli utenti nei dispositivi Windows 10 Desktop <!-- 1627835 RS4 -->
I clienti saranno in grado di distribuire le app line-of-business di Windows 10 da installare in contesti di dispositivo. In questo modo le app saranno disponibili per tutti gli utenti del dispositivo. Questa opzione è disponibile solo per i dispositivi Windows 10 Desktop.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registrazione con il portale aziendale migliorata <!-- 1874230-->
Gli utenti che registrano un dispositivo tramite il portale aziendale in Windows 10 build 1703 e successive riusciranno a completare il primo passaggio della registrazione senza uscire dall'app.

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



