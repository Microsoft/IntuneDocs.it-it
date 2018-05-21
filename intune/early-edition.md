---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/09/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f3cbfad85e4a7a97d9bbf98e2ad239fda7cc29e4
ms.sourcegitcommit: d40bfb6af66f2ce7026c0151ace98ec23f1cf76e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="the-early-edition-for-microsoft-intune---may-2018"></a>Edizione anticipata per Microsoft Intune - Maggio 2018

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

<!-- 1805 start -->

### <a name="set-compliance-by-device-location----851881----"></a>Impostare la conformità in base al percorso del dispositivo <!-- 851881 ! -->
In alcuni casi, potrebbe essere necessario limitare l'accesso alle risorse aziendali a un percorso specifico, definito da una connessione di rete. Sarà possibile creare un criterio di conformità (**Conformità del dispositivo** > **Percorsi**) in base all'indirizzo IP del dispositivo. Se il dispositivo non è più compreso nell'intervallo di IP, non può accedere alle risorse aziendali.

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Miglioramento della risoluzione dei problemi di installazione delle app <!-- 928990 -->
Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. È in corso la distribuzione di un'anteprima pubblica delle funzionalità di risoluzione dei problemi delle app. Sotto ogni singolo dispositivo si noterà un nuovo nodo denominato **App gestite**, che elenca le app distribuite tramite MDM di Intune. Nel nodo è visibile un elenco di stati di installazione delle app. Se si seleziona una singola app, si noterà la visualizzazione relativa alla risoluzione dei problemi per l'app specifica. In tale visualizzazione è presente il ciclo di vita end-to-end dell'app, ad esempio quando l'app è stata creata, modificata, specificata come destinazione e distribuita in un dispositivo. Se l'installazione dell'app non è riuscita, saranno anche disponibili il codice di errore e un messaggio sulla causa dell'errore. 

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
Presto sarà possibile configurare i criteri di protezione delle app per cancellare i dati in modo esplicito, bloccare o segnalare i dispositivi non conformi. La nuova azione di *cancellazione* rimuove i dati aziendali da un dispositivo. Se si verifica una cancellazione, all'utente del dispositivo vengono notificati sia il motivo della cancellazione che la procedura di correzione. Per alcune impostazioni, come la versione minima del sistema operativo, sarà possibile applicare più azioni, ad esempio il blocco e la cancellazione.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Nuove informazioni di inventario per i dispositivi Windows <!-- 1333569 eeready -->

Per ogni dispositivo Windows, nella scheda **Hardware** (**Gruppi** > **Tutti i dispositivi mobili** > **Dispositivi** > scegliere il dispositivo dell'utente > **Visualizza proprietà** > **Hardware**) saranno disponibili le informazioni di inventario seguenti:
- TPM
- Antivirus
- Antispyware
- Firewall
- UAC
- Batteria
- Nome dominio

Per altre informazioni su come questi dati vengono recuperati dal provider CSP, vedere le voci relative a DeviceGuard nell'articolo [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) (CSP DeviceStatus).

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
Sarà possibile assegnare tutti gli utenti, tutti i dispositivi e tutti gli utenti e tutti i dispositivi nei gruppi ambito.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Spostamento dei profili AutoPilot nei gruppi di destinazione <!-- 1877935 -->
I profili di distribuzione AutoPilot possono attualmente essere assegnati a dispositivi selezionati. Dopo il rilascio di questa funzionalità, per assegnare i profili, sarà necessario eseguire queste operazioni:
- Creare gruppi (Azure AD) contenenti dispositivi AutoPilot
- Assegnare i profili desiderati a un gruppo di Azure AD. Il profilo AutoPilot verrà assegnato ai dispositivi AutoPilot presenti in tale gruppo.

### <a name="management-name-field-will-be-editable----1875989---"></a>Il campo Nome di gestione sarà modificabile <!-- 1875989 -->
Sarà possibile modificare il campo Nome di gestione nel pannello **Proprietà** di un dispositivo. Per modificare questo campo, scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Proprietà**. È possibile usare il campo Nome di gestione per identificare in modo univoco un dispositivo.

<!-- 1804 start -->


### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Aggiunte alle impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1403702 -->
Sarà possibile configurare impostazioni aggiuntive per le opzioni di sicurezza dei dispositivi locali Windows 10. Le impostazioni aggiuntive saranno disponibili per le aree relative ai client di rete Microsoft, ai server di rete Microsoft, all'accesso e alla sicurezza di rete e all'accesso interattivo. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Richiedere l'installazione di criteri, app e profili certificato e di rete <!-- 1553555 -->
Gli amministratori saranno in grado di impedire agli utenti finali di accedere al desktop di Windows 10 RS4 finché Intune non avrà installato criteri, app e profili di certificato e di rete durante il provisioning di dispositivi AutoPilot.

### <a name="rules-for-removing-devices----1609459---"></a>Regole di rimozione dei dispositivi <!-- 1609459 -->
Saranno disponibili nuove regole che consentiranno di rimuovere automaticamente i dispositivi che non si sono connessi per un numero di giorni specificato. Per visualizzare la nuova regola, passare al riquadro **Intune**, selezionare **Dispositivi**e selezionare **Device removal rules** (Regole rimozione dispositivi).

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitare app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot<!-- 1621980 -->
Sarà possibile impedire l'installazione di app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot. Per visualizzare questa funzionalità, passare a **Intune** > **Registrazione del dispositivo** > **Registrazione Windows** > **Windows AutoPilot profiles** (Profili Windows AutoPilot)  > **Crea nuovo** > **Impostazioni di registrazione**. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>Supporto di Exchange Connector multipli <!-- 2070451 -->

Non è più previsto il limite di un Microsoft Intune Exchange Connector per tenant. Intune supporta Exchange Connector multipli per consentire la configurazione dell'accesso condizionale in Intune per più organizzazioni di Exchange locali.

Con un On-premises Exchange Connector di Intune è possibile gestire l'accesso dei dispositivi alle cassette postali di Exchange locali in base al fatto che i dispositivi siano registrati o meno in Intune e siano conformi ai criteri di conformità dei dispositivi di Intune. Per configurare un connettore, scaricare l'On-premises Exchange Connector di Intune dal portale di Azure e installarlo in un server dell'organizzazione di Exchange. Nel dashboard di Microsoft Intune scegliere **Accesso locale**, quindi nella sezione **Installazione**, scegliere **Connettore per Exchange ActiveSync**. Scaricare l'On-premises Exchange Connector e installarlo in un server della propria organizzazione di Exchange. Ora che non vige più il limite di Exchange Connector per tenant, gli utenti che hanno più organizzazioni di Exchange possono seguire lo stesso processo per scaricare e installare un connettore per ogni organizzazione di Exchange aggiuntiva.

### <a name="support-coming-for-new-cisco-anyconnect-client-for-ios----1333708---"></a>Supporto previsto per i nuovi client Cisco AnyConnect per iOS <!-- 1333708 -->

I nuovi profili VPN creati per Cisco AnyConnect per IOS funzioneranno con Cisco AnyConnect 4.0.7 e versioni successive. I profili VPN di Cisco AnyConnect per iOS esistenti verranno contrassegnati con la dicitura **Cisco Legacy AnyConnect** e continueranno a funzionare con Cisco AnyConnect 4.0.5x come accade oggi.

> [!NOTE]
> Questa modifica riguarda solo iOS perché continuerà ad esistere una sola opzione Cisco AnyConnect per Android, Android for Work e macOS.

#### <a name="more-information"></a>Altre informazioni

Per supportare la nuova app è necessario creare un nuovo profilo VPN di Cisco AnyConnect per iOS perché la nuova app Cisco AnyConnect e l'app Cisco Legacy AnyConnect sono due app distinte. Se il client AnyConnect viene gestito nell'ambiente in uso, è necessario distribuire anche la nuova app Cisco AnyConnect. Per completare un aggiornamento, è inoltre necessario eliminare il profilo VPN di Cisco Legacy AnyConnect e rimuovere l'app Cisco Legacy AnyConnect.

Nella versione iniziale, l'integrazione del controllo di accesso alla rete (NAC) per i nuovi client AnyConnect non funziona. È in corso un'operazione congiunta con Cisco per attivare l'integrazione NAC in una futura versione di Intune.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacità di distribuire le app line-of-business (LOB) necessarie a tutti gli utenti nei dispositivi Windows 10 Desktop <!-- 1627835 RS4 -->
I clienti saranno in grado di distribuire le app line-of-business di Windows 10 da installare in contesti di dispositivo. In questo modo le app saranno disponibili per tutti gli utenti del dispositivo. Questa opzione è disponibile solo per i dispositivi Windows 10 Desktop.

### <a name="company-portal-enrollment-improved----1874230--"></a>Registrazione con il portale aziendale migliorata <!-- 1874230-->
Gli utenti che registrano un dispositivo tramite il portale aziendale in Windows 10 build 1703 e successive riusciranno a completare il primo passaggio della registrazione senza uscire dall'app.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Aggiornamento dell'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android <!--1631531 -->

L'esperienza Guida e commenti e suggerimenti nell'app Portale aziendale per Android verrà aggiornata e adattata alle procedure consigliate per le app Android. L'aggiornamento dell'app Portale aziendale per Android che avverrà nei prossimi mesi consisterà nella suddivisione della voce di menu **Guida e commenti e suggerimenti** in due distinte voci di menu **Guida** e **Invia commenti e suggerimenti**. La pagina **Guida** conterrà una sezione **Domande frequenti** e il pulsante **Supporto e-mail** per invitare gli utenti a caricare log in Microsoft e a inviare e-mail al supporto aziendale per descrivere i problemi incontrati. **Invia commenti e suggerimenti** guiderà l'utente nella procedura standard Microsoft per l'invio di commenti e suggerimenti che richiederà all'utente di indicare una preferenza, una mancanza di preferenza o un'idea.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Criteri di protezione delle app <!-- 679615 -->
I criteri di Protezione app di Intune offrono la possibilità di creare criteri predefiniti globali per attivare rapidamente la protezione per tutti gli utenti nell'intero tenant.

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->   
Usando Azure Active Directory (Azure AD) è possibile limitare l'accesso ai siti Web su dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure.


## <a name="notices"></a>Notifiche

Non sono disponibili notifiche attive.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
