---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6cc33bc6e03d2e0370c9e2c2dd9d3462296710e6
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329685"
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



### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token VPP Apple usato da un altro software MDM <!-- 1488946 -->
Intune rileverà e visualizzerà i dettagli se un token VPP (Volume Purchase Program) Apple viene usato sia da Intune che da un altro software MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>Vengono visualizzati il numero di versione e il numero di build di iOS <!-- 1892471 -->
In **Conformità del dispositivo** > **Conformità del dispositivo** viene visualizzata la versione del sistema operativo iOS. In un aggiornamento futuro verrà anche visualizzato il numero di build.
Quando vengono rilasciati aggiornamenti della sicurezza, Apple lascia in genere il numero di versione invariato, ma aggiorna il numero di build. Visualizzando il numero di build, è possibile verificare facilmente se è installato un aggiornamento di una vulnerabilità.

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

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>Configurare il profilo per ignorare alcune schermate durante l'esecuzione di Assistente configurazione <!-- 2276470 -->
Quando si crea un profilo di registrazione macOS, sarà possibile configurarlo per ignorare qualsiasi schermata seguente quando un utente esegue Assistente configurazione:
- Android Migration (Migrazione Android)
- Display Tone (Tono schermo)
- Privacy
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Modifica nel processo di aggiornamento per i connettori locali <!-- 2277554 -->
In base al feedback dei clienti, cambierà il modo in cui gli aggiornamenti vengono eseguiti nei connettori locali. Dopo aver installato un connettore locale, gli aggiornamenti verranno eseguiti automaticamente. Questa modifica inizierà con il nuovo connettore di certificati PFX per Microsoft Intune e successivamente verrà applicata ad altri tipi di connettori locali. 



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

Se si richiede un passcode non biometrico all'avvio dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App client** > **Criteri di protezione delle app** > **Aggiungi criteri** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire sarà possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

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

Se si richiede un passcode non biometrico all'avvio a freddo dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App client** > **Criteri di protezione delle app** > **Aggiungi criteri** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

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



