---
title: Edizione anticipata
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b6ca8108924c6c062da0d0ef56ab5b68635dd9ca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="the-early-edition-for-microsoft-intune---april-2018"></a>Edizione anticipata per Microsoft Intune - Aprile 2018

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

<!-- 1804 start -->

### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802--"></a>Nuove impostazioni di Windows Defender Credential Guard aggiunte alle impostazioni di Endpoint Protection <!--1102252 --><!--from 1802-->

Nuove impostazioni [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) verranno aggiunte a **Configurazione del dispositivo** > **Profili** > **Endpoint Protection**. Verranno aggiunte le impostazioni seguenti:

- Livello di sicurezza della piattaforma: specificare se abilitare il livello di sicurezza della piattaforma al successivo riavvio. La sicurezza basata sulla virtualizzazione richiede l'avvio protetto. La sicurezza basata sulla virtualizzazione può essere abilitata facoltativamente con l'uso di protezioni di accesso diretto alla memoria (DMA). Le protezioni DMA richiedono supporto hardware e verranno abilitate solo nei dispositivi configurati correttamente.
- Sicurezza basata sulla virtualizzazione: specificare se abilitare la sicurezza basata sulla virtualizzazione al successivo riavvio.
- Windows Defender Credential Guard: attivare Credential Guard con la sicurezza basata sulla virtualizzazione per proteggere le credenziali al successivo riavvio quando sono abilitati il livello di sicurezza della piattaforma con avvio protetto e la sicurezza basata sulla virtualizzazione. Le opzioni disponibili sono **Disabilitato**, **Abilitato con blocco UEFI**, **Abilitato senza blocco** e **Non configurato**.
  - L'opzione "Disabilitato" disattiva Credential Guard in modalità remota se attivato precedentemente tramite l'opzione "Abilitato senza blocco".

  - L'opzione "Abilitato con blocco UEFI" garantisce che Credential Guard non possa essere disabilitato con una chiave del Registro di sistema o tramite Criteri di gruppo. Per disabilitare Credential Guard dopo aver usato questa impostazione, è necessario impostare Criteri di gruppo su "Disabilitato" e rimuovere la funzionalità di sicurezza da ogni computer, con un utente fisicamente presente, per cancellare la configurazione mantenuta in UEFI. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

  - L'opzione "Abilitato senza blocco" consente di rimuovere Credential Guard in modalità remota tramite Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 (versione 1511 o successiva).

  - L'opzione "Non configurato" consente di non definire l'impostazione dei criteri. Poiché l'impostazione del criterio non viene scritta nel Registro di sistema, non influisce in alcun modo su computer o utenti. Se è presente un'impostazione corrente nel Registro di sistema, l'impostazione non verrà modificata.

### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Supporto di passcode per PIN MAM in Android<!-- 1438086 -->

Gli amministratori di Intune potranno impostare un requisito di avvio delle applicazioni per imporre un passcode anziché un PIN MAM numerico. Se il requisito viene configurato, all'utente viene richiesto di impostare e usare un passcode prima di accedere alle applicazioni con supporto MAM. Un passcode è un PIN numerico con almeno un carattere speciale o una lettera maiuscola o minuscola. Il supporto di Intune per i passcode è simile a quello esistente per il PIN numerico, con la possibilità di impostare una lunghezza minima e consentendo la ripetizione di caratteri e sequenze tramite la console di amministrazione. Questa funzionalità richiede la versione più recente di Portale aziendale in Android. Questa funzionalità è già disponibile per iOS.

###  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Bloccare la fotocamera e le acquisizioni di schermate in Android for Work <!-- 1098977 eeready-->
Saranno disponibili due nuove proprietà di blocco utilizzabili durante la configurazione delle restrizioni per i dispositivi Android: 
- Fotocamera: blocca l'accesso a tutte le fotocamere del dispositivo
- Acquisizione schermo: blocca l'acquisizione di schermate e impedisce anche la visualizzazione del contenuto nei dispositivi di visualizzazione privi di output video protetto

Si applica ad Android for Work.

### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Supporto di app line-of-business (LOB) per macOS <!-- 1473977 -->
Microsoft Intune offrirà la possibilità di installare app LOB (line-of-business) macOS dal portale di Azure. Sarà possibile aggiungere un'app LOB macOS a Intune dopo una pre-elaborazione effettuata dallo strumento disponibile in GitHub. Nel portale di Azure scegliere **App per dispositivi mobili** dal pannello **Intune**. Nel pannello **App per dispositivi mobili** scegliere **App** > **Aggiungi**. Nel pannello **Aggiungi app** selezionare **App line-of-business**. 

### <a name="support-for-user-less-devices----1637553---"></a>Supporto per dispositivi senza utente associato <!-- 1637553 -->
Intune supporterà la possibilità di valutare la conformità nei dispositivi senza utente associato, ad esempio Microsoft Surface Hub. I criteri di conformità potranno avere come destinazione dispositivi specifici. Sarà quindi possibile determinare la conformità (e la mancata conformità) dei dispositivi senza un utente associato.

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Aggiunte alle impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1403702 -->
Sarà possibile configurare impostazioni aggiuntive per le opzioni di sicurezza dei dispositivi locali Windows 10. Le impostazioni aggiuntive saranno disponibili per le aree relative ai client di rete Microsoft, ai server di rete Microsoft, all'accesso e alla sicurezza di rete e all'accesso interattivo. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Richiedere l'installazione di criteri, app e profili certificato e di rete <!-- 1553555 -->
Gli amministratori saranno in grado di impedire agli utenti finali di accedere al desktop di Windows 10 RS4 finché Intune non avrà installato criteri, app e profili di certificato e di rete durante il provisioning di dispositivi AutoPilot.

### <a name="rules-for-removing-devices----1609459---"></a>Regole di rimozione dei dispositivi <!-- 1609459 -->
Saranno disponibili nuove regole che consentiranno di rimuovere automaticamente i dispositivi che non si sono connessi per un numero di giorni specificato. Per visualizzare la nuova regola, passare al riquadro **Intune**, selezionare **Dispositivi**e selezionare **Device removal rules** (Regole rimozione dispositivi).

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitare app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot<!-- 1621980 -->
Sarà possibile impedire l'installazione di app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot. Per visualizzare questa funzionalità, passare a **Intune** > **Registrazione del dispositivo** > **Registrazione Windows** > **Windows AutoPilot profiles** (Profili Windows AutoPilot)  > **Crea nuovo** > **Impostazioni di registrazione**. 

### <a name="advanced-threat-protection-integrated-with-intune----1629303---"></a>Integrazione di Advanced Threat Protection con Intune <!-- 1629303 -->
[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) indica il livello di rischio dei dispositivi Windows 10. Quando Intune valuta la conformità dei dispositivi Windows 10, include nella valutazione il punteggio di ATP relativo al rischio. È possibile usare ATP con l'accesso condizionale per rafforzare la protezione della rete.

### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nuovi passaggi di registrazione degli utenti per i dispositivi con macOS High Sierra 10.13.2 e versioni successive <!--1734567 -->
macOS high Sierra 10.13.2 ha introdotto il concetto di registrazione MDM "approvata dall'utente". In futuro, le registrazioni approvate consentiranno a Intune di gestire alcune impostazioni relative alla sicurezza. Per altre informazioni, vedere la documentazione del supporto Apple all'indirizzo https://support.apple.com/HT208019.

I dispositivi registrati tramite il portale aziendale macOS verranno considerati "approvati dall'utente" solo se l'utente finale aprirà Preferenze di Sistema e dichiarerà l'approvazione manualmente. A tal fine, il portale aziendale macOS ora indica agli utenti che usano macOS 10.13.2 e versioni successive di approvare manualmente la registrazione al termine dell'esecuzione di questa. La console di amministrazione di Intune indicherà se un dispositivo registrato è approvato dall'utente.

### <a name="delete-autopilot-devices----1713650---"></a>Eliminare dispositivi AutoPilot <!-- 1713650 -->
Gli amministratori di Intune saranno in grado di eliminare i dispositivi AutoPilot.

### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Gruppi predefiniti Tutti gli utenti e Tutti i dispositivi per l'assegnazione di app Android for Work <!-- 1813073 -->
Sarà possibile sfruttare i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi** per l'assegnazione di app Android for Work. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).

### <a name="improved-device-deletion-experience---1832333---"></a>Miglioramento dell'esperienza di eliminazione di dispositivi <!--1832333 -->
Non sarà più necessario rimuovere i dati aziendali o eseguire il ripristino delle impostazioni predefinite in un dispositivo prima di eliminare quest'ultimo da Intune.

Per visualizzare la nuova esperienza, accedere a Intune e selezionare **Dispositivi** > **Tutti i dispositivi** > nome del dispositivo > **Elimina**.

 Se si vuole comunque la conferma di cancellazione/ritiro, è possibile usare il percorso standard del ciclo di vita del dispositivo tramite i comandi **Rimuovi i dati aziendali** e **Ripristino delle impostazioni predefinite** prima di **Elimina**. 

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Spostamento dei profili AutoPilot nei gruppi di destinazione <!-- 1877935 -->
I profili di distribuzione AutoPilot possono attualmente essere assegnati a dispositivi selezionati. Verso la fine del mese di aprile, ecco come verranno assegnati questi profili:
- Creare gruppi (Azure AD) contenenti dispositivi AutoPilot
- Assegnare i profili desiderati a un gruppo di Azure AD. Il profilo AutoPilot verrà assegnato ai dispositivi AutoPilot presenti in tale gruppo.

### <a name="play-sounds-on-ios-when-in-lost-mode----1629303---"></a>Riprodurre suoni in iOS in modalità di dispositivo perso <!-- 1629303 -->
Quando un dispositivo iOS sotto supervisione si trova nella [modalità di dispositivo perso](device-lost-mode.md) della gestione di dispositivi mobili (MDM, Mobile Device Management), è possibile riprodurre un suono (**Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo iOS > **Panoramica** > **Altro**). Il suono continua finché la modalità di dispositivo perso non viene cambiata o un utente non disabilita il suono dal dispositivo. Si applica ai dispositivi iOS 9.3 e successivi.

### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Usare un nome oggetto personalizzato sul certificato SCEP <!-- 2064190 -->
Sarà possibile usare **OnPremisesSamAccountName**, il nome comune in un oggetto personalizzato in un profilo certificato SCEP. È ad esempio possibile usare `CN={OnPremisesSamAccountName})`.

### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Inviare report di diagnostica nell'app Portale aziendale per macOS <!-- 2216677 -->
L'app Portale aziendale per i dispositivi macOS verrà aggiornata per migliorare la modalità di segnalazione degli errori correlati a Intune. Dall'app Portale aziendale i dipendenti siano in grado di:
- Caricare report di diagnostica direttamente per il team di sviluppo Microsoft.
- Inviare tramite posta elettronica l'ID evento imprevisto al team di supporto IT della società.

### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN Always On per Windows 10 <!--1333666 -->

Attualmente, è possibile usare [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) nei dispositivi Windows 10 tramite un profilo di rete privata virtuale (VPN, Virtual Private Network) personalizzato creato con un URI OMA.

Con questo aggiornamento, gli amministratori potranno abilitare profili VPN Always On per Windows 10 direttamente in Intune nel portale di Azure. I profili VPN Always On si connetteranno automaticamente quando:

- Gli utenti accedono ai propri dispositivi
- La rete del dispositivo cambia
- Lo schermo del dispositivo si riattiva dopo essere stato disattivato

### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Miglioramento della messaggistica per gli errori di caricamento del certificato push MDM Apple <!-- 2172331 -->

Il messaggio di errore spiega che per rinnovare un certificato MDM esistente è necessario usare lo stesso ID Apple.

###  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Visualizzazione di tutti i dispositivi di un gruppo nel grafico dei profili e nell'elenco dello stato dei dispositivi <!-- 1449153 eeready -->
Quando si configura il profilo di un dispositivo (**Configurazione del dispositivo** > **Profili**), si sceglie il profilo del dispositivo, ad esempio iOS. Il profilo viene assegnato a un gruppo che include dispositivi iOS e non iOS. Il conteggio del grafico indica che il profilo viene applicato ai dispositivi iOS *e* non iOS (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**). Quando si seleziona il grafico nella scheda **Panoramica**, **Stato dispositivo** elenca tutti i dispositivi del gruppo, anziché solo i dispositivi iOS. 

Con questo aggiornamento, il grafico (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**) visualizzerà solo il conteggio relativo al profilo dispositivo specifico. Se ad esempio il profilo di configurazione si applica ai dispositivi iOS, il grafico elencherà solo il conteggio dei dispositivi iOS. Selezionando il grafico e aprendo **Stato dispositivo** si vedranno elencati solo i dispositivi iOS.

In attesa di questo aggiornamento, il grafico utente è stato temporaneamente rimosso. 


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

<!-- 1802 start -->

### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nuove impostazioni della stampante per i profili di formazione <!-- 1308900 -->

Per i profili di formazione, le nuove impostazioni saranno disponibili nella categoria **Stampanti**: **Stampanti**, **Stampante predefinita**, **Aggiungi nuove stampanti**.

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


