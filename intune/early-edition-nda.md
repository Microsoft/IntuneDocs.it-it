---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 609e142551344a1ce39761280031463c8e34f1f0
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2018
ms.locfileid: "37906023"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Edizione anticipata per Microsoft Intune - luglio 2018

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

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Reimpostare i passcode dei dispositivi dall'app del portale aziendale per Windows 10 <!-- 2101282 --> 
I dipendenti potranno presto reimpostare il PIN o passcode del proprio dispositivo direttamente dall'app del portale aziendale per Windows 10. Questa funzionalità sarà disponibile nei dispositivi gestiti da Intune remoti e locali che supportano la reimpostazione di passcode. A seconda del tipo di dispositivo, una richiesta effettuata per un dispositivo remoto rimuove il passcode corrente del dispositivo oppure crea un passcode temporaneo. Gli utenti che richiedono una reimpostazione per un dispositivo locale vengono reindirizzati all'app Impostazioni del dispositivo.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Nuove esperienze di esplorazione nell'app Portale aziendale per Windows <!-- 2317227 -->  
Durante l'esplorazione o la ricerca di app nell'app Portale aziendale per Windows è possibile passare dalla visualizzazione **Riquadri** alla nuova visualizzazione **Dettagli** e viceversa. La nuova visualizzazione elenca i dettagli dell'applicazione, ad esempio il nome, l'editore, la data di pubblicazione e lo stato di installazione.  

La pagina **App** introdurrà una visualizzazione **Installata** che consente di visualizzare i dettagli sulle installazioni completate e in corso. Per condividere commenti e suggerimenti o opinioni sulle modifiche apportate, inviare il proprio feedback nell'app Portale aziendale.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Esperienza dell'app Portale aziendale migliorata per gli utenti del manager di registrazione dispositivi <!-- 675800 -->
Quando un manager di registrazione dispositivi accede all'app Portale aziendale per Windows, l'app elenca solo il dispositivo in esecuzione corrente. Questo miglioramento ridurrà i timeout che in precedenza si verificavano quando l'app tentava di caricare tutti i dispositivi registrati nel manager di registrazione dispositivi.  

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Usare S/MIME per crittografare e firmare più dispositivi di un utente  <!-- 1333642 -->
Un aggiornamento futuro includerà una crittografia di posta elettronica S/MIME con un nuovo profilo di certificato importato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > selezionare la piattaforma > tipo di profilo **Certificato PKCS importato**). In Intune è possibile importare i certificati nel formato PFX. Intune può quindi distribuire i certificati a più dispositivi registrati da un singolo utente. Inoltre:

- Il profilo di posta elettronica iOS nativo supporta l'abilitazione della crittografia S/MIME mediante certificati importati in formato PFX.
- L'app di posta elettronica nativa nei dispositivi Windows Phone 10 usa automaticamente il certificato S/MIME.
- I certificati privati possono essere recapitati su più piattaforme. Tuttavia, non tutte le app di posta elettronica supportano S/MIME.
- In altre piattaforme potrebbe essere necessario configurare manualmente l'app di posta elettronica per abilitare S/MIME.  
- È possibile che le app di posta elettronica che supportano la crittografia S/MIME gestiscano il recupero dei certificati per la crittografia della posta elettronica S/MIME in un modo non supportato dal software MDM, ad esempio basandosi sull'archivio certificati del server di pubblicazione.

Supportato in: Windows, Windows Phone 10, macOS, iOS, Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Usare le licenze di dispositivo VPP per effettuare il provisioning anticipato del portale aziendale durante la registrazione DEP <!-- 1608345 -->
È possibile usare le licenze di dispositivo Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante le registrazioni DEP (Device Enrollment Program). A tale scopo, quando si crea o si modifica un profilo di registrazione, specificare il token VPP che si vuole usare per installare il portale aziendale. Assicurarsi che il token non abbia una scadenza e di avere un numero sufficiente di licenze per l'app del portale aziendale. Se il token ha una scadenza o se il numero di licenze è insufficiente, Intune esegue il push del portale aziendale dell'App Store (che richiederà l'immissione di un ID Apple).

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminare in blocco i dispositivi nel pannello Dispositivi <!-- 1793693 -->
È possibile eliminare più dispositivi contemporaneamente nel pannello Dispositivi. Scegliere **Dispositivi** > **Tutti i dispositivi** > selezionare i dispositivi da eliminare > **Elimina**. Per i dispositivi che non possono essere eliminati, viene visualizzato un avviso.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nuovo profilo di configurazione del dispositivo Wi-Fi per Windows 10 e versioni successive <!-- 1879077 -->
Attualmente, è possibile importare ed esportare i profili Wi-Fi usando i file XML. Sarà possibile creare un profilo di configurazione del dispositivo Wi-Fi direttamente in Intune, come in alcune altre piattaforme.

Per creare il profilo, aprire **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Wi-Fi**. 

Si applica a Windows 10 e versioni successive.

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Ridenominazione delle estensioni file delle app line-of-business (LOB) di Windows <!-- 1884873 -->
Le estensioni file delle app line-of-business di Windows LOB *appx* e *appxbundle* verranno rinominate in *msix* e *msixbundle*. È possibile aggiungere un'app in Microsoft Intune selezionando **App per dispositivi mobili** > **App** > **Aggiungi**. Viene visualizzato il riquadro **Aggiungi app** che consente di selezionare il **Tipo di app**. Per le app line-of-business di Windows, selezionare il tipo di app **App line-of-business**, selezionare il **File del pacchetto dell'app** e quindi specificare un file di installazione con l'estensione appropriata.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Pacchetto di configurazione Windows Defender ATP aggiunto automaticamente al profilo di configurazione <!-- 2144658 -->
Quando vengono usati [Advanced Threat Protection e dispositivi onboarding](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) in Intune, viene eseguito il download di un pacchetto di configurazione che viene aggiunto al profilo di configurazione. In un aggiornamento futuro Intune otterrà automaticamente il pacchetto da Windows Defender Security Center e lo aggiungerà al profilo.

Si applica a Windows 10 e versioni successive.

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Modalità tutto schermo obsoleta appare disattivata e non può essere modificata <!-- 2149998 -->
La [funzionalità Modalità tutto schermo](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Limitazioni del dispositivo**) sarà obsoleta e sostituita dalle [impostazioni di modalità tutto schermo per Windows 10 e versioni successive](kiosk-settings.md). La funzionalità **Modalità tutto schermo obsoleta** apparirà disattivata e l'interfaccia utente non potrà essere modificata o aggiornata. 

Per abilitare la modalità tutto schermo, vedere [Impostazioni relative alla modalità tutto schermo per Windows 10 e versioni successive](kiosk-settings.md).

Si applica a Windows 10 e versioni successive, Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API per l'uso delle autorità di certificazione di terze parti <!-- 2184013 -->
Sarà disponibile un'API Java che consente l'integrazione delle autorità di certificazione di terze parti con Intune e SCEP. Gli utenti potranno quindi aggiungere il certificato SCEP a un profilo e applicarlo ai dispositivi usando il software MDM.

Attualmente Intune supporta [le richieste SCEP con Servizi certificati Active Directory](certificates-scep-configure.md).

### <a name="check-for-sccm-compliance----2192052---"></a>Controllare la conformità SCCM <!-- 2192052 -->
Un aggiornamento futuro includerà una nuova impostazione di conformità SSCM (System Center Configuration Manager) (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10**). SCCM invia segnali per la conformità di Intune. Usando l'impostazione di Intune è possibile richiedere che tutti i segnali SCCM restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In SCCM questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Si applica a Windows 10 e versioni successive

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invia un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Conferma richieste per l'eliminazione del token VPP usato per il provisioning anticipato del portale aziendale <!-- 2237634 -->
Viene richiesta la conferma dell'eliminazione di un token VPP (Volume Purchase Program) se il token viene usato per il provisioning anticipato del portale aziendale durante la registrazione DEP.

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Contrassegnare automaticamente i dispositivi Android registrati usando Samsung Knox Mobile Enrollment come "aziendali" <!-- 2404851 -->
Per impostazione predefinita, i dispositivi Android registrati usando Samsung Knox Mobile Enrollment vengono contrassegnati come **Aziendale** in **Proprietà del dispositivo**. Non sarà necessario identificare manualmente i dispositivi aziendali utilizzando i numeri IMEI o seriali prima della registrazione mediante Knox Mobile Enrollment.

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Visualizzare o nascondere il pulsante Termina sessione in un browser in modalità tutto schermo <!-- 2455253 -->
Sarà possibile specificare se visualizzare o nascondere il pulsante Termina sessione nei browser in modalità tutto schermo. Il controllo è disponibile in **Configurazione del dispositivo** > **Modalità tutto schermo (anteprima)** > **Web browser in modalità tutto schermo**. Se è abilitato, quando un utente fa clic sul pulsante, l'app richiede di confermare se terminare la sessione. Se si conferma, il browser cancella tutti i dati di navigazione e torna all'URL predefinito.

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Creare un profilo di configurazione cellulare eSIM <!-- 2564077 -->
In **Configurazione del dispositivo** è possibile creare un profilo cellulare eSIM. È possibile importare un file contenente i codici di attivazione cellulare forniti dall'operatore di telefonia mobile. È quindi possibile distribuire i profili nei dispositivi Windows 10 con eSIM LTE, ad esempio Surface Pro LTE e altri dispositivi che supportano eSIM.

Verificare se i [dispositivi supportano i profili eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Si applica a Windows 10 e versioni successive. 




<!-- 1806 start -->


### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune potranno impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non sono visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Creare criteri di conformità dei dispositivi usando le impostazioni del firewall nei dispositivi macOS <!-- 1497640 -->
Quando si creano nuovi criteri di conformità per macOS, in **Conformità del dispositivo** > **Criteri** > **Crea criteri** > **Piattaforma: macOS** > **Protezione del sistema**, saranno disponibili alcune nuove impostazioni del **firewall**: 
- **Firewall**: configurare in che modo le connessioni in ingresso devono essere gestite nell'ambiente in uso.
- **Connessioni in ingresso**: **bloccare** tutte le connessioni in ingresso tranne quelle necessarie per i servizi Internet di base, ad esempio DHCP, Bonjour e IPSec. Questa impostazione consente inoltre di bloccare tutti i servizi di condivisione.
- **Modalità mascheramento**: **abilitare** questa modalità per impedire che il dispositivo risponda alle richieste di probe. Il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate.

Si applica a: macOS 10.12 e versioni successive

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Richiedere un passcode non biometrico per l'avvio e il timeout dell'app <!-- 1506985 -->

Se si richiede un passcode non biometrico all'avvio dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** > **Aggiungi criterio** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire sarà possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App per dispositivi mobili** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Anteprima di una nuova esperienza utente per il sito Web del portale aziendale <!--2000968 -->
Attualmente vengono aggiunte nuove funzionalità, in base ai suggerimenti dei clienti, al sito Web del portale aziendale/catalogo delle app iOS. Si noterà un miglioramento significativo delle funzionalità esistenti e dell'usabilità dei dispositivi Android, iOS e Windows. Diverse aree del sito, ad esempio i dettagli del dispositivo, i commenti e suggerimenti, il supporto e la panoramica del dispositivo, presentano una nuova progettazione, moderna e reattiva. L'aggiornamento include anche:

- Flussi di lavoro semplificati in tutte le piattaforme per dispositivi
- Flussi di identificazione e registrazione dei dispositivi ottimizzati
- Messaggi di errore più utili
- Linguaggio più intuitivo, con meno gergo tecnico
- Possibilità di condividere collegamenti diretti alle app
- Miglioramento delle prestazioni per i cataloghi di app di grandi dimensioni
- Maggiore accessibilità per tutti gli utenti

L'aggiornamento è attualmente in anteprima. È possibile registrarsi per partecipare all'anteprima all'indirizzo http://aka.ms/webcpflighting


### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modificare le distribuzioni delle app di Office 365 Pro Plus <!-- 2150145 -->
Per l'amministratore di Microsoft Intune sarà più facile modificare le distribuzioni delle app di Office 365 Pro Plus. Nel portale di Azure selezionare **Microsoft Intune** > **App per dispositivi mobili** > **App**. Selezionare la famiglia di prodotti Office 365 Pro Plus dall'elenco delle applicazioni.  

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Richiedere un passcode non biometrico per l'avvio a freddo e il timeout dell'app <!-- 1506985 --> 

Se si richiede un passcode non biometrico all'avvio a freddo dell'app e dopo il timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** > **Aggiungi criterio** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloccare l'accesso dell'app in base ai fornitori e ai modelli non approvati del dispositivo <!-- 1425689 ! -->
L'amministratore IT di Intune potrà applicare un elenco specificato di produttori Android e/o di modelli iOS tramite i criteri di Protezione app di Intune. L'amministratore IT può fornire un elenco delimitato da punto e virgola di produttori per i criteri Android e di modelli di dispositivo per i criteri iOS. I criteri di Protezione app di Intune sono solo per Android e iOS. Sarà possibile eseguire due azioni distinte su questo elenco specificato:
- Blocco dell'accesso delle app nei dispositivi non specificati.
- Cancellazione selettiva dei dati aziendali nei dispositivi non specificati. 

L'utente non potrà accedere all'applicazione di destinazione se non vengono soddisfatti i requisiti definiti tramite i criteri. In base alle impostazioni, è possibile che l'utente venga bloccato o che i dati aziendali nell'app vengano cancellati in modo selettivo. Nei dispositivi iOS questa funzionalità richiede il supporto delle applicazioni (WXP, Outlook, Managed Browser, Yammer) per l'integrazione di Intune APP SDK, in modo che le impostazioni relative alla versione minima possano essere applicate per le applicazioni di destinazione. Questa integrazione avviene progressivamente e dipende dai team delle applicazioni specifiche. In Android questa funzionalità richiede il portale aziendale più recente. 

Nei dispositivi degli utenti finali il client Intune eseguirà un'azione in base a una semplice corrispondenza delle stringhe specificate nel pannello Intune per i criteri di protezione delle applicazioni. Ciò dipende completamente dal valore segnalato dal dispositivo. Di conseguenza, è opportuno che l'amministratore IT si assicuri che il comportamento previsto sia accurato. A tale scopo, è possibile testare questa impostazione con svariati produttori di dispositivi e modelli destinati a un piccolo gruppo di utenti. In Microsoft Intune selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** per visualizzare e aggiungere i criteri di protezione delle app. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app](app-protection-policy.md).


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
