---
title: Novità dei mesi precedenti in Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Rileggere gli annunci precedenti dalla pagina delle novità di Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 73be6facab5deb8a09462dc03c4683af3d34c027
ms.sourcegitcommit: b93db06ba435555f5b126f97890931484372fcfb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2018
ms.locfileid: "52829233"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novità di Microsoft Intune - mesi precedenti

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="march-2018"></a>Marzo 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Avvisi per le app line-of-business (LOB) iOS per Microsoft Intune <!-- 748789 -->

Intune segnala nel portale di Azure le app line-of-business iOS che stanno per scadere. Dopo che una nuova versione dell'app line-of-business iOS è stata caricata, Intune rimuove la notifica di scadenza dall'elenco delle app. La notifica di scadenza sarà attiva solo per le app line-of-business iOS caricate di recente. Viene visualizzato un avviso 30 giorni prima della scadenza del profilo di provisioning dell'app line-of-business iOS. Dopo la scadenza, l'avviso viene sostituito dall'indicazione Scaduto.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalizzare i temi del portale aziendale con codici esadecimali <!--1049561 -->

È possibile personalizzare il colore del tema nelle app Portale aziendale usando codici esadecimali. Quando si immette il codice esadecimale, Intune determina il colore del testo che offre il livello di contrasto massimo tra colore del testo e colore di sfondo. È possibile visualizzare in anteprima un confronto tra il colore del testo e il logo della società e il colore in **App client** > **Portale aziendale**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusione ed esclusione dell'assegnazione delle app in base ai gruppi per Android Enterprise <!-- 1813081 -->

Android Enterprise (denominato in precedenza Android for Work) supporta l'inclusione e l'esclusione di gruppi, ma non supporta i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi**. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestione dei dispositivi

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome----2258071---"></a>Esportare tutti i dispositivi in file CSV in Internet Explorer, Microsoft Edge o Chrome <!-- 2258071 -->
In **Dispositivi** > **Tutti i dispositivi** è possibile **esportare** i dispositivi in un elenco in formato CSV. Gli utenti di Internet Explorer (IE) con più di 10.000 dispositivi possono esportare i propri dispositivi in più file. Ogni file include fino a 10.000 dispositivi.

Gli utenti di Microsoft Edge e Chrome con più di 30.000 dispositivi possono esportare i propri dispositivi in più file. Ogni file include fino a 30.000 dispositivi.

[Gestire dispositivi](device-management.md) offre ulteriori dettagli sulle operazioni eseguibili con i dispositivi gestiti.

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Nuovi miglioramenti della sicurezza nel servizio Intune <!-- 1637539 -->   

È stato introdotto un tasto di alternanza in Intune in Azure che i clienti autonomi di Intune possono usare per gestire i dispositivi senza criteri assegnati come **conformi** (funzionalità di sicurezza disattivata) o **non conformi** (funzionalità di sicurezza attivata). Ciò garantirà l'accesso alle risorse solo dopo la valutazione della conformità del dispositivo.

Questa funzionalità ha effetti diversi a seconda che siano già stati assegnati o meno i criteri di conformità.

- Per gli account nuovi o esistenti in cui non sono assegnati criteri di conformità ai dispositivi, il tasto di alternanza è impostato automaticamente su **Conforme**. La funzionalità è disattivata nella console per impostazione predefinita. Non c'è alcun impatto sull'utente finale.
- Per gli account esistenti in cui sono assegnati criteri di conformità ai dispositivi, il tasto di alternanza è impostato automaticamente su **Non conforme**. La funzionalità è attivata per impostazione predefinita, a partire dall'implementazione dell'aggiornamento di marzo.

Se si usano criteri di conformità con accesso condizionale e la funzionalità è attivata, tutti i dispositivi senza alcun criterio di conformità assegnato vengono bloccati dall'accesso condizionale. Gli utenti finali associati a questi dispositivi e in precedenza autorizzati ad accedere alla posta elettronica perdono l'accesso, a meno che a tutti i dispositivi non venga assegnato almeno un criterio di conformità.   

Si noti che sebbene lo stato del tasto di alternanza predefinito venga visualizzato immediatamente nell'interfaccia utente con gli aggiornamenti di marzo del servizio Intune, lo stato non viene applicato immediatamente. Eventuali modifiche apportate al tasto di alternanza non influiscono sulla conformità del dispositivo fino a quando non viene distribuito in anteprima un tasto di alternanza funzionante per l'account. Al termine della distribuzione in anteprima, verrà inviata una comunicazione tramite il Centro messaggi. L'operazione potrebbe richiedere alcuni giorni dopo l'aggiornamento di marzo del servizio Intune.

**Informazioni aggiuntive**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>Rilevamento ottimizzato per jailbreak <!-- 846515 -->

Il rilevamento ottimizzato per jailbreak è una nuova impostazione di conformità che migliora la valutazione dei dispositivi jailbroken da parte di Intune. L'impostazione usa i servizi di posizione per attivare con maggiore frequenza l'archiviazione del dispositivo con Intune. Ciò può influire sull'utilizzo della batteria.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Reimpostare le password per i dispositivi Android O <!-- 1238299 -->
Sarà possibile reimpostare le password per i dispositivi Android 8.0 registrati con profili di lavoro. Quando si invia una richiesta "Reimposta password" a un dispositivo Android 8.0, viene impostata una nuova password di sblocco del dispositivo o una nuova richiesta di verifica del profilo gestito per l'utente corrente. La password o la richiesta viene inviata e diventa immediatamente effettiva.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>Assegnazione dei criteri di conformità a dispositivi in gruppi di dispositivi <!--1307012 -->

È possibile assegnare i criteri di conformità agli utenti in gruppi utenti. Con questo aggiornamento è possibile assegnare i criteri di conformità ai dispositivi in gruppi di dispositivi. I dispositivi inclusi in gruppi di dispositivi non riceveranno azioni di conformità.

#### <a name="new-management-name-column----1333586---"></a>Nuova colonna Nome di gestione <!-- 1333586 -->
 Una nuova colonna denominata **Nome di gestione** è disponibile nel pannello Dispositivi. Si tratta di un nome generato automaticamente e non modificabile assegnato a ogni dispositivo, in base alla formula seguente:
- Nome predefinito per tutti i dispositivi: <username><em><devicetype></em><enrollmenttimestamp>
- Per i dispositivi aggiunti in blocco: < PackageId/ProfileId ><em><DeviceType></em><EnrollmentTime>

Questa colonna è facoltativa nel pannello Dispositivi. Non è disponibile per impostazione predefinita ed è possibile accedervi solo tramite il selettore di colonna. Il nome del dispositivo non è interessato da questa nuova colonna.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>Ai dispositivi iOS viene richiesto un codice PIN ogni 15 minuti <!--1550837 -->
Dopo l'applicazione di criteri di conformità o configurazione a un dispositivo iOS, agli utenti viene richiesto di impostare un PIN ogni 15 minuti. La richiesta verrà visualizzata continuamente fino a quando non verrà impostato un PIN.

#### <a name="schedule-your-automatic-updates---1805514---"></a>Pianificare gli aggiornamenti automatici <!--1805514 -->
Intune offre un controllo sull'installazione di aggiornamenti automatici mediante [le impostazioni degli anelli di Windows Update](windows-update-for-business-configure.md). Dopo questo aggiornamento sarà possibile pianificare gli aggiornamenti ricorrenti, nonché la settimana, il giorno e l'ora.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>Usare il nome distinto completo come soggetto per il certificato SCEP <!--2221763 -->
Quando si crea un profilo certificato SCEP, immettere il nome del soggetto. Dopo questo argomento, sarà possibile usare il nome distinto completo come soggetto. Per **Nome soggetto**, selezionare **Personalizzato** e immettere `CN={{OnPrem_Distinguished_Name}}`. Usare la variabile `{{OnPrem_Distinguished_Name}}`, assicurarsi di sincronizzare l'attributo utente `onpremisesdistingishedname` usando [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con Azure AD.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Attivare la condivisione dei contatti Bluetooth - Android for Work <!--1098983 -->
Per impostazione predefinita, Android non consente la sincronizzazione dei contatti nel profilo di lavoro con i dispositivi Bluetooth. Di conseguenza, i contatti del profilo di lavoro non vengono visualizzati nell'ID chiamante per i dispositivi Bluetooth.

Dopo questo aggiornamento, sarà presente una nuova impostazione in **Android for Work** > **Limitazioni del dispositivo** > **Impostazioni del profilo di lavoro**:
- Contact sharing via Bluetooth (Contatto condivisione tramite Bluetooth)

L'amministratore di Intune può configurare queste impostazioni per abilitare la condivisione. Ciò è utile quando si associa un dispositivo a un dispositivo Bluetooth da usare in macchina che visualizza l'ID chiamante per l'uso del viva voce. Quando l'impostazione è abilitata, i contatti del profilo di lavoro vengono visualizzati. Quando l'impostazione non è abilitata, i contatti del profilo di lavoro non vengono visualizzati.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>Configurare Gatekeeper per controllare l'origine del download delle app macOS <!-- 1690459 -->

È possibile configurare Gatekeeper per la protezione dei dispositivi controllando da dove possono essere scaricate le app. È possibile configurare le origini di download seguenti: **Mac App Store**, **Mac App Store e sviluppatori identificati** o **Ovunque**. È anche possibile specificare se gli utenti possono installare un'app usando CTRL+clic per eseguire l'override di questi controlli di Gatekeeper.

Queste impostazioni sono disponibili in **Configurazione del dispositivo** -> **Crea profilo** -> **macOS** -> **Endpoint protection**.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Configurare il firewall dell'applicazione Mac <!-- 1690461 -->

È possibile configurare il firewall dell'applicazione Mac. Usare questa impostazione per controllare le connessioni in base all'applicazione, anziché in base alla porta. Questo rende più semplice ottenere i vantaggi della protezione con firewall e contribuisce a impedire che app indesiderate assumano il controllo delle porte di rete aperte per app legittime.

Questa funzione è disponibile in **Configurazione del dispositivo** -> **Crea profilo** -> **macOS** -> **Endpoint protection**.

Dopo aver abilitato l'impostazione del firewall, configurare il firewall utilizzando una delle due strategie seguenti:

- Bloccare tutte le connessioni in ingresso

   Vengono bloccate tutte le connessioni in ingresso per i dispositivi di destinazione. Se si sceglie questa opzione, le connessioni in ingresso vengono bloccate per tutte le app.

- Consentire o bloccare app specifiche

   È possibile consentire o bloccare la ricezione di connessioni in ingresso per app specifiche. È inoltre possibile abilitare la modalità mascheramento per impedire l'invio di risposte alle richieste di probe.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>Messaggi e codici di errore dettagliati <!-- 1376342 -->

Nella configurazione del dispositivo sono disponibili per la visualizzazione più messaggi di errore e codici di errore dettagliati. Con questo miglioramento della creazione di report, vengono visualizzati le impostazioni, lo stato delle impostazioni e i dettagli sulla risoluzione dei problemi.

##### <a name="more-information"></a>Altre informazioni

- Bloccare tutte le connessioni in ingresso

   Con questa opzione si impedisce a tutti i servizi di condivisione, ad esempio Condivisione file e Condivisione schermo, di ricevere le connessioni in ingresso. I servizi di sistema che rimangono autorizzati a ricevere connessioni in ingresso sono:
  - configd: implementa DHCP e altri servizi di configurazione di rete
  - mDNSResponder: implementa Bonjour
  - racoon: implementa IPSec

    Per utilizzare i servizi di condivisione, assicurarsi che **Connessioni in ingresso** sia impostata su **Non configurato** e non **Blocca**.

- Modalità mascheramento

   Abilitare questa modalità per impedire che il computer risponde alle richieste di probe. Il computer risponde comunque alle richieste in ingresso provenienti da app autorizzate. Le richieste impreviste, ad esempio le richieste ICMP (ping), vengono ignorate.

#### <a name="disable-checks-on-device-restart---1805490---"></a>Disabilitare i controlli al riavvio del dispositivo <!--1805490 -->
Intune consente di controllare [manage software updates]](windows-update-for-business-configure.md). Con questo aggiornamento, la proprietà <strong>Verifiche al riavvio</strong> è disponibile e abilitata per impostazione predefinita. Per ignorare i controlli che vengono eseguiti generalmente quando si riavvia un dispositivo, come ad esempio gli utenti attivi, i livelli di batteria e così via, selezionare <strong>Ignora</strong>.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>Nuovi canali Windows 10 Insider Preview disponibili per gli anelli di distribuzione <!-- 1746293 -->
Durante la creazione di un anello di distribuzione Windows 10 è ora possibile selezionare i canali di servizio Windows 10 Insider Preview seguenti:
- Build di Windows Insider &#8208; Veloce
- Build di Windows Insider &#8208; Lenta
- Versione della build di Windows Insider 

Per altre informazioni su questi canali, vedere [Gestire le build Insider Preview](https://insider.windows.com/for-business-organization-admin/).   
Per altre informazioni sulla creazione di canali di distribuzione in Intune, vedere [Gestire gli aggiornamenti software](windows-update-for-business-configure.md).

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>Nuove impostazioni di Windows Defender Exploit Guard <!-- 1631893 -->

Sono ora disponibili sei nuove impostazioni di <strong>Riduzione della superficie di attacco</strong> e funzionalità <strong>Accesso controllato alle cartelle: Protezione delle cartelle</strong> avanzate. Queste impostazioni sono disponibili in: Configurazione del dispositivo\Profili\
Crea profilo\Endpoint Protection\Windows Defender Exploit Guard.

#### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco

|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Protezione ransomware avanzata|Abilitato, Controllo, Non configurato|Usare una protezione ransomware aggressiva.|
|Flag della sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows|Abilitato, Controllo, Non configurato|Impostare flag per la sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows (lsass.exe).|
|Creazione di processi dai comandi PSExec e WMI|Blocca, Controllo, Non configurato|Bloccare le creazioni di processi originate dai comandi PSExec e WMI.|
|Processi non attendibili e non firmati eseguiti da USB|Blocca, Controllo, Non configurato|Bloccare i processi non attendibili e non firmati eseguiti da USB.|
|File eseguibili che non soddisfano i criteri di prevalenza, età o elenco attendibile|Blocca, Controllo, Non configurato|Bloccare l'esecuzione dei file eseguibili se non soddisfano i criteri di prevalenza, età o elenco attendibile.|

#### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

|              Nome impostazione               |                                                              Opzioni di impostazione                                                              | Descrizione |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protezione delle cartelle (già implementata) | Non configurato, Abilita, Solo controllo (già implementata)<br><br> <strong>Nuove</strong><br>Blocco della modifica del disco, controllo della modifica del disco |             |

Proteggere file e cartelle da modifiche non autorizzate eseguite da applicazioni non compatibili.<br><br>**Abilitare**: impedire alle app non attendibili di modificare o eliminare file nelle cartelle protette e di scrivere nei settori del disco.<br><br>
**Bloccare solo la modifica del disco**:<br>Impedire alle app non attendibili di scrivere nei settori del disco. Le app non attendibili possono ancora modificare o eliminare i file nelle cartelle protette.|

### <a name="intune-apps"></a>App di Intune

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->

Tramite Azure Active Directory (Azure AD) è ora possibile limitare l'accesso ai siti Web nei dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure. Per altre informazioni, vedere [Controlli di accesso nell'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Aggiornamenti di elementi visivi nell'app Portale aziendale per Android <!--976944 -->

L'app Portale aziendale per Android è stata aggiornata e resa conforme alle linee guida di Android [Material Design](https://material.io/). È possibile visualizzare le immagini delle nuove icone nell'articolo [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>Registrazione con il portale aziendale migliorata <!-- 1874230 eeready-->
Gli utenti che registrano un dispositivo tramite il portale aziendale in Windows 10 build 1703 e successive possono ora completare il primo passaggio della registrazione senza uscire dall'app.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens e Surface Hub vengono ora visualizzati nell'elenco dei dispositivi <!--1725868 -->
È stato aggiunto il supporto per la visualizzazione dei dispositivi HoloLens e Surface Hub registrati in Intune nell'app del portale aziendale per Android.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>Categorie libro personalizzate per eBook di Volume Purchase Program (VPP) <!-- 1488911 -->
È possibile creare categorie eBook personalizzate a cui assegnare eBook VPP. Gli utenti finali potranno vedere le categorie eBook appena create e i libri a esse assegnati. Per altre informazioni, vedere [Gestire le app e i libri acquistati con Volume Purchase Program con Microsoft Intune](vpp-apps.md).  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Modifiche al supporto per l'app Portale aziendale per l'opzione di invio di commenti e suggerimenti di Windows <!-- 2070166 -->
A partire dal 30 aprile 2018, l'opzione **Invia commenti e suggerimenti** nell'app Portale aziendale per Windows funziona solo per i dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 (1607) e versioni successive. L'opzione Invia commenti e suggerimenti non è più supportata se si usa l'app Portale aziendale per Windows con:  
- Windows 10, versione 1507  
- Windows 10, versione 1511  
- Windows Phone 8.1 

Se il dispositivo esegue Windows 10 RS1 o versione successiva, scaricare la versione più recente dell'app Portale aziendale di Windows dallo Store. Se si esegue una versione non supportata, è possibile continuare a inviare commenti e suggerimenti tramite i canali seguenti: 
- App hub di commenti e suggerimenti in Windows 10
- Posta elettronica: WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>Nuove impostazioni di Windows Defender Application Guard <!-- 1631890 -->

- **Abilitare l'accelerazione grafica**: gli amministratori possono attivare un processore di grafica virtuale per Windows Defender Application Guard. Questa impostazione consente alla CPU di passare il rendering della grafica alla vGPU. Ciò può migliorare le prestazioni durante l'uso di siti Web con molta grafica o la riproduzione di video all'interno del contenitore.

- **Salvare i file su host**: gli amministratori possono consentire il passaggio dei file da Microsoft Edge in esecuzione nel contenitore al file system dell'host. L'attivazione di questa impostazione consente agli utenti di scaricare i file da Microsoft Edge nel contenitore nel file system dell'host.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>Criteri di protezione MAM assegnati in base allo stato di gestione <!-- 1665993 -->
È possibile assegnare i criteri MAM in base allo stato di gestione del dispositivo:
- **Dispositivi Android**: è possibile includere i dispositivi non gestiti, i dispositivi gestiti da Intune e i profili Android Enterprise gestiti da Intune (in precedenza denominato Android for Work).
- **Dispositivi iOS**: è possibile includere i dispositivi non gestiti (solo MAM) o i dispositivi gestiti da Intune.

    > [!NOTE]
    > - Il supporto iOS per questa funzionalità verrà implementato in aprile 2018.

Per altre informazioni, vedere [Target app protection policies based on device management state](app-protection-policies.md) (Assegnare i criteri di protezione delle app in base allo stato di gestione del dispositivo).

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Miglioramenti del linguaggio dell'app del portale aziendale per Windows <!-- 1683758 -->
È stato migliorato il linguaggio del Portale aziendale per Windows 10 per risultare più intuitivo e specifico per l'azienda. Per visualizzare alcune immagini delle novità, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>Nuove aggiunte alla documentazione sulla privacy dell'utente <!-- 1440709 -->
Per offrire agli utenti finali un maggior controllo sui dati e sulla privacy, sono stati pubblicati aggiornamenti alla documentazione che descrivono come visualizzare e rimuovere i dati archiviati in locale dalle app del portale aziendale. Questi aggiornamenti sono disponibili in:

- **Android**: [Come annullare la registrazione del dispositivo Android da Intune](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **Android, se l'utente ha rifiutato le condizioni per l'utilizzo**: [Annullare la registrazione del dispositivo se sono state rifiutate le Condizioni per l'utilizzo](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Annullare la registrazione del dispositivo iOS da Intune](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Annullare la registrazione del dispositivo Windows da Intune](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="february-2018"></a>Febbraio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 -->

Intune supporta ora la registrazione di dispositivi da un massimo di 100 account [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) o [Apple School Manager](apple-school-manager-set-up-ios.md) diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Visualizzare le restrizioni di registrazione per i singoli utenti <!-- 1634444 eeready wnready -->
Nel pannello **Risoluzione dei problemi** è ora possibile visualizzare le [restrizioni di registrazione](enrollment-restrictions-set.md) applicate per ogni utente selezionando **Restrizioni registrazione** nell'elenco **Assegnazioni**.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Nuova opzione per l'autenticazione utente per la registrazione in blocco Apple <!-- 747625 eeready -->

> [!NOTE]
> I nuovi tenant la vedono immediatamente. Per i tenant esistenti, questa funzionalità verrà implementata nel corso del mese di aprile. Fino al termine dell'implementazione, non è possibile accedere a queste nuove funzionalità.

Intune offre ora la possibilità di autenticare i dispositivi con l'app Portale aziendale per i metodi di registrazione seguenti:

- Programma di registrazione del dispositivo mobile di Apple
- Apple School Manager
- Registrazione di Apple Configurator

Quando si usa l'opzione Portale aziendale, l'autenticazione a più fattori di Azure Active Directory può essere applicata senza bloccare questi metodi di registrazione.

Quando si usa l'opzione Portale aziendale, Intune ignora l'autenticazione utente nell'Assistente configurazione di iOS per la registrazione dell'affinità utente. Questo significa che il dispositivo viene inizialmente registrato come dispositivo senza utente e pertanto non riceve le configurazioni o i criteri dei gruppi utenti, ma solo le configurazioni e i criteri per i gruppi di dispositivi. Tuttavia, Intune installerà automaticamente l'app Portale aziendale nel dispositivo. Il primo utente che avvia l'app Portale aziendale e vi accede verrà associato al dispositivo in Intune. A questo punto, l'utente riceverà le configurazioni e i criteri dei gruppi utenti. L'associazione dell'utente non può essere modificata senza eseguire di nuovo la registrazione.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 eeready -->

Intune supporta ora la registrazione di dispositivi da un massimo di 100 account Apple Device Enrollment Program (DEP) o Apple School Manager diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>Stampa remota su una rete protetta <!-- 1709994  -->
Le soluzioni di stampa mobile wireless di PrinterOn consentiranno agli utenti di eseguire stampe in modalità remota da qualsiasi posizione e in qualsiasi momento tramite una rete protetta. PrinterOn verrà integrato in Intune APP SDK sia per iOS che per Android. Sarà possibile assegnare i criteri di protezione delle app a questa app tramite il pannello **Criteri di protezione delle app** di Intune nella console di amministrazione. Gli utenti finali potranno scaricare l'app 'PrinterOn per Microsoft' tramite Play Store o iTunes da usare all'interno del loro ecosistema di Intune.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>Supporto del portale aziendale macOS per le registrazioni che usano il manager di registrazione dispositivi <!-- 1352411 -->

Gli utenti ora possono usare il manager di registrazione dispositivi durante la registrazione con il portale aziendale macOS.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Report sullo stato integrità e lo stato minacce di Windows Defender <!--854704 -->

Per gestire i PC Windows è di fondamentale importanza comprendere l'integrità e lo stato di Windows Defender.  Con questo aggiornamento Intune aggiunge nuovi report e azioni per lo stato e l'integrità dell'agente Windows Defender. Usando un report di rollup dello stato nel [carico di lavoro Conformità del dispositivo](compliance-policy-monitor.md) è possibile visualizzare i dispositivi per i quali è necessario:
- un aggiornamento della firma
- Riavvia
- un intervento manuale
- un'analisi completa
- un intervento per altri stati dell'agente

Un report di analisi per ogni categoria di stato elenca i singoli PC che richiedono attenzione o quelli per i quali è indicato **Pulisci**.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>Nuove impostazioni di privacy per le restrizioni dei dispositivi <!--1308926 -->
Sono ora disponibili [due nuove impostazioni di privacy](device-restrictions-windows-10.md#privacy) per i dispositivi:
- **Pubblica le attività utente**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità per l'attività.
- **Solo attività locali**: impostare l'opzione su **Blocca** per impedire le esperienze condivise e l'individuazione delle ultime risorse usate nel cambio modalità solo per l'attività locale.

#### <a name="new-settings-for-the-microsoft-edge-browser---1469166---"></a>Nuove impostazioni per il browser Microsoft Edge <!--1469166 -->
Sono ora disponibili [due nuove impostazioni](device-restrictions-windows-10.md#microsoft-edge-browser) per il **percorso del file dei Preferiti** e le **modifiche a Preferiti** per i dispositivi con browser Microsoft Edge.

### <a name="app-management"></a>Gestione delle app

#### <a name="protocol-exceptions-for-applications---1035509---"></a>Eccezioni di protocollo per le applicazioni <!--1035509 -->

Ora è possibile creare eccezioni ai criteri di trasferimento dati della gestione di applicazioni mobili (MAM) di Intune per aprire specifiche applicazioni non gestite. Le applicazioni devono essere considerate attendibile da IT. A differenza delle eccezioni create, il trasferimento dati rimane limitato alle applicazioni gestire da Intune quando i criteri di trasferimento dati sono impostati **solo per le app gestite**. È possibile creare le restrizioni tramite protocolli (iOS) o pacchetti (Android).

Ad esempio, è possibile aggiungere il pacchetto Webex come eccezione ai criteri di trasferimento dati MAM. In questo modo i collegamenti Webex in un messaggio di posta elettronica di Outlook gestito possono essere aperti direttamente nell'applicazione Webex. Il trasferimento dati rimarrà limitato nelle altre applicazioni non gestite. Per altre informazioni, vedere [Eccezioni dei criteri di trasferimento dei dati per le app](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dati crittografati di Windows Information Protection (WIP) nei risultati di ricerca di Windows <!-- 1469193 -->
Un'impostazione nei criteri di Windows Information Protection (WIP) consente ora di controllare se i dati crittografati WIP vengono inclusi nei risultati di ricerca di Windows. Impostare questa opzione dei criteri di protezione dell'app selezionando l'impostazione che **consente all'indicizzatore di Ricerca di Windows di cercare gli elementi crittografati** nelle **impostazioni avanzate** dei criteri di Windows Information Protection. I criteri di protezione dell'app devono essere impostati sulla piattaforma *Windows 10* e lo **stato di registrazione** dei criteri dell'app deve essere impostato su **Con registrazione**. Per altre informazioni, vedere [Consentire all'indicizzatore di Ricerca di Windows di cercare elementi crittografati](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurazione di un'app MSI per dispositivi mobili con aggiornamento automatico <!-- 1740840 -->
È possibile configurare un'app MSI per dispositivi mobili con aggiornamento automatico nota in modo che ignori il processo di controllo delle versioni. Questa funzionalità consente di evitare una race condition. Ad esempio, questo tipo di race condition può verificarsi quando l'app viene aggiornata automaticamente dallo sviluppatore di app e anche da Intune. In entrambi i casi è possibile che si tenti di imporre una versione dell'app in un client di Windows creando un conflitto. Per queste app MSI con aggiornamento automatico, è possibile configurare l'impostazione **Ignora la versione dell'app** nel pannello **Informazioni sull'app**. Se questa impostazione viene cambiata in **Sì**, Microsoft Intune ignorerà la versione dell'app installata nel client Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Insiemi correlati di licenze per le app supportati in Intune <!-- 1864117 -->
Intune nel portale di Azure ora supporta gli insiemi correlati di licenze per le app come elemento app singolo nell'interfaccia utente. Inoltre, tutte le app con licenza offline sincronizzate da Microsoft Store per le aziende verranno consolidate in una singola voce di app e verrà eseguita la migrazione di tutti i dettagli di distribuzione dei singoli pacchetti nella singola voce. Per visualizzare gli insiemi correlati di licenze per le app nel portale di Azure, selezionare **App licenses** (Licenze app) dal pannello **App client**.

### <a name="device-configuration"></a>Configurazione del dispositivo
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>Estensioni di file di Windows Information Protection (WIP) per la crittografia automatica <!-- 1463582 -->
Un'impostazione nei criteri di Windows Information Protection (WIP) ora consente di specificare le estensioni di file che vengono automaticamente crittografate quando si esegue la copia da una condivisione di Server Message Block (SMB) all'interno dell'azienda, come definito nei criteri di WIP.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Configurare le impostazioni dell'account della risorsa per i dispositivi Surface Hub

Ora è possibile configurare in modalità remota le impostazioni dell'account della risorsa per i dispositivi Surface Hub.

L'account della risorsa viene usato dal dispositivo Surface Hub per l'autenticazione con Skype/Exchange per poter partecipare a una riunione.
Creare un account della risorsa univoco in modo che il dispositivo Surface Hub compaia nella riunione come sala riunioni.
Ad esempio, l'account della risorsa potrebbe essere visualizzato come **Sala riunioni B41/6233**.

> [!NOTE]
> - Se non si specifica alcun valore nei campi, gli attributi configurati in precedenza sul dispositivo verranno sostituiti.
>
> - Le proprietà dell'account della risorsa possono essere modificate dinamicamente nel dispositivo Surface Hub. Ad esempio, nel caso in cui sia attivata la rotazione delle password. Di conseguenza, è possibile che i valori nella console di Azure non riflettano immediatamente la realtà del dispositivo.
>
>   Per individuare la configurazione corrente nel dispositivo Surface Hub, i dati dell'account della risorsa possono essere inclusi nell'inventario hardware (per il quale è già impostato un intervallo di 7 giorni) o come proprietà di sola lettura. Per una maggior precisione dopo l'esecuzione dell'azione remota, è possibile ottenere lo stato dei parametri subito dopo l'esecuzione dell'azione per aggiornare l'account e i parametri nel dispositivo Surface Hub.

##### <a name="attack-surface-reduction"></a>Riduzione della superficie di attacco

|Nome impostazione  |Opzioni di impostazione  |Descrizione  |
|---------|---------|---------|
|Esecuzione dalla posta elettronica del contenuto eseguibile protetto da password|Blocca, Controllo, Non configurato|Evitare l'esecuzione dei file eseguibili protetti da password scaricati usando la posta elettronica.|
|Protezione ransomware avanzata|Abilitato, Controllo, Non configurato|Usare una protezione ransomware aggressiva.|
|Flag della sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows|Abilitato, Controllo, Non configurato|Impostare flag per la sottrazione delle credenziali dal sottosistema dell'autorità di protezione locale Windows (lsass.exe).|
|Creazione di processi dai comandi PSExec e WMI|Blocca, Controllo, Non configurato|Bloccare le creazioni di processi originate dai comandi PSExec e WMI.|
|Processi non attendibili e non firmati eseguiti da USB|Blocca, Controllo, Non configurato|Bloccare i processi non attendibili e non firmati eseguiti da USB.|
|File eseguibili che non soddisfano i criteri di prevalenza, età o elenco attendibile|Blocca, Controllo, Non configurato|Bloccare l'esecuzione dei file eseguibili se non soddisfano i criteri di prevalenza, età o elenco attendibile.|

##### <a name="controlled-folder-access"></a>Accesso controllato alle cartelle

|              Nome impostazione               |                                                              Opzioni di impostazione                                                              | Descrizione |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| Protezione delle cartelle (già implementata) | Non configurato, Abilita, Solo controllo (già implementata)<br><br> <strong>Nuove</strong><br>Blocco della modifica del disco, controllo della modifica del disco |             |

Proteggere file e cartelle da modifiche non autorizzate eseguite da applicazioni non compatibili.<br><br>**Abilitare**: impedire alle app non attendibili di modificare o eliminare file nelle cartelle protette e di scrivere nei settori del disco.<br><br>
**Bloccare solo la modifica del disco**:<br>Impedire alle app non attendibili di scrivere nei settori del disco. Le app non attendibili possono ancora modificare o eliminare i file nelle cartelle protette.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Nuove impostazioni di sicurezza del sistema per Windows 10 e nuovi criteri di conformità <!--1704133-->

Sono ora disponibili nuove impostazioni di conformità di Windows 10, inclusa la richiesta di Firewall e Windows Defender Antivirus.

### <a name="intune-apps"></a>App di Intune

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Supporto per le app offline da Microsoft Store per le aziende <!--1222672-->
Le app offline acquistate da Microsoft Store per le aziende ora vengono sincronizzate nel portale di Azure. È quindi possibile distribuire le app ai gruppi di dispositivi o ai gruppi di utenti. Le app offline vengono installate da Intune, non dallo Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro <!-- 1728700 -->

Quando si distribuisce l'app Gmail in un profilo Android for Work, è ora possibile impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro usando l'impostazione **Aggiungi o rimuovi account** nel profilo delle restrizioni per dispositivi Android for Work.


## <a name="january-2018"></a>Gennaio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>Avvisi per i token scaduti e i token che scadranno a breve <!-- 1639263 -->
Nella pagina di panoramica vengono visualizzati ora avvisi per i token scaduti e i token che scadranno a breve. Facendo clic su un avviso per un singolo token si passerà alla pagina dei dettagli del token.  Se si fa clic su un avviso con più token, verrà visualizzato un elenco di tutti i token con il relativo stato. Gli amministratori devono rinnovare i relativi token prima della scadenza.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>Supporto del comando di cancellazione remoto per dispositivi macOS <!-- 1438084 -->

Gli amministratori possono eseguire un comando di cancellazione in remoto da dispositivi macOS.

> [!IMPORTANT]
> Il comando di cancellazione non può essere annullato e deve essere usato con cautela.

Il comando di cancellazione rimuove tutti i dati, incluso il sistema operativo, da un dispositivo. Rimuove anche il dispositivo dalla gestione di Intune. Non viene visualizzato alcun avviso all'utente e la cancellazione viene eseguita immediatamente.

È necessario configurare un PIN di ripristino di 6 cifre. Questo PIN può essere usato per sbloccare il dispositivo cancellato e a quel punto verrà avviata la reinstallazione del sistema operativo. Dopo l'avvio della cancellazione, il PIN viene visualizzato in una barra di stato nel pannello della panoramica del dispositivo in Intune. Il PIN verrà mantenuto per tutta la durata del processo di cancellazione. Dopo il completamento della cancellazione, il dispositivo scompare del tutto dalla gestione di Intune. Assicurarsi di registrare il PIN di ripristino in modo che possa essere usato da chiunque esegua il ripristino del dispositivo.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>Revocare le licenze per un token Volume Purchasing Program iOS <!-- 820870 -->
È possibile revocare la licenza di tutte le app Volume Purchasing Program (VPP) iOS per un determinato token VPP.

### <a name="app-management"></a>Gestione delle app

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>Revoca delle app Volume Purchase Program iOS <!-- 820863 -->
Per un dispositivo specifico con una o più app Volume Purchase Program (VPP) iOS, è possibile revocare la licenza per app basata su dispositivo associata al dispositivo stesso. La revoca di una licenza per app non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. Per altre informazioni, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>Assegnare le app per dispositivi mobili Office 365 a dispositivi iOS e Android usando il tipo di app predefinito <!-- 1332318 -->
Il tipo di app **Predefinito** consente di creare e assegnare in modo semplice le app Office 365 a dispositivi iOS e Android gestiti. Le app includono le app 0365 come Word, Excel, PowerPoint e OneDrive. È possibile assegnare app specifiche al tipo di app e modificare la configurazione delle informazioni sull'app.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>Inclusione ed esclusione per l'assegnazione di app in base ai gruppi <!-- 1406920 -->

Durante l'assegnazione di app e dopo aver selezionato un tipo di assegnazione, è possibile selezionare i gruppi da includere, così come i gruppi da escludere.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>È possibile assegnare un criterio di configurazione dell'applicazione ai gruppi includendo ed escludendo le assegnazioni  <!-- 1480316 -->

È possibile assegnare un criterio di configurazione dell'applicazione a un gruppo di utenti e dispositivi tramite una combinazione di assegnazioni di inclusione ed esclusione. È possibile scegliere le assegnazioni come selezione personalizzata di gruppi o come gruppo virtuale. Un gruppo virtuale può includere **Tutti gli utenti**, **Tutti i dispositivi** o **Tutti gli utenti + Tutti i dispositivi**.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Supporto dei criteri di aggiornamento edizione di Windows 10 <!-- 903672(archived), 1119689 -->  
È possibile creare criteri di aggiornamento edizione di Windows 10 per l'aggiornamento di dispositivi Windows 10 a Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education e Windows 10 Professional Education N. Per informazioni dettagliate sugli aggiornamenti edizione di Windows 10, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>I criteri di accesso condizionale per Intune sono disponibili solo dal portale di Azure <!-- 1737088 1634311 -->

A partire da questa versione, è necessario configurare e gestire i criteri di accesso condizionale nel [portale di Azure](https://portal.azure.com) da **Azure Active Directory** > **Accesso condizionale**. Per praticità, è possibile accedere a questo pannello anche da Intune nel portale di Azure in **Intune** > **Accesso condizionale**.

#### <a name="updates-to-compliance-emails---1637547---"></a>Aggiornamenti per i messaggi di posta elettronica di conformità <!--1637547 -->

Quando viene inviato un messaggio di posta elettronica per segnalare un dispositivo non conforme, vengono inclusi dettagli sul dispositivo non conforme.

### <a name="intune-apps"></a>App di Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nuove funzionalità per l'azione "Risolvi" per i dispositivi Android <!--1583480-->

L'app Portale aziendale per Android sta estendendo l'azione "Risolvi" di **Aggiorna impostazioni del dispositivo** in modo da risolvere i [problemi di crittografia del dispositivo](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Blocco remoto disponibile nell'app Portale aziendale per Windows 10 <!--676506-->
Gli utenti possono ora bloccare i dispositivi in modalità remota dall'app Portale aziendale per Windows 10. L'opzione non verrà visualizzata per il dispositivo locale in uso.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Risoluzione dei problemi di conformità più facile per l'app Portale aziendale per Windows 10 <!--676546-->
Gli utenti finali con dispositivi Windows potranno toccare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema.

## <a name="december-2017"></a>Dicembre 2017

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="new-automatic-redeployment-setting----1469168---"></a>Nuova impostazione per la ridistribuzione automatica <!-- 1469168 -->
L'impostazione **Ridistribuzione automatica** consente agli utenti con diritti amministrativi di eliminare tutti i dati utente e tutte le impostazioni utente usando **CTRL+tasto WINDOWS+R** nella schermata di blocco del dispositivo. Il dispositivo viene automaticamente riconfigurato e registrato di nuovo nella gestione. Questa impostazione è disponibile in Windows 10 > Limitazioni del dispositivo > Generale > Ridistribuzione automatica. Per i dettagli, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10](device-restrictions-windows-10.md#general).

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Supporto di edizioni di origine aggiuntivi nei criteri di aggiornamento dell'edizione di Windows 10 <!-- 903672,  1119689 -->
È ora possibile usare i criteri di aggiornamento dell'edizione di Windows 10 per l'aggiornamento da altre edizioni di Windows 10 (Windows 10 Pro, Windows 10 Pro Education, Windows 10 Cloud e così via). Prima di questa versione, i percorsi di aggiornamento delle edizioni supportati erano più limitati. Per altri dettagli, vedere [Come configurare gli aggiornamenti edizione di Windows 10](edition-upgrade-configure-windows-10.md).

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>Nuove impostazioni per il profilo di configurazione del dispositivo Windows Defender Security Center (WDSC)<!-- 1335507 -->

Intune aggiunge una nuova sezione alle impostazioni per il profilo di configurazione del dispositivo in Endpoint Protection denominata **Windows Defender Security Center**. Gli amministratori IT possono configurare gli elementi chiave dell'app Windows Defender Security Center accessibili per gli utenti finali. Se un amministratore IT nasconde un elemento chiave nell'app Windows Defender Security Center, tutte le notifiche correlate all'elemento nascosto non vengono visualizzate nel dispositivo dell'utente.

Questi sono gli elementi chiave che gli amministratori possono nascondere dalle impostazioni del profilo di configurazione del dispositivo per Windows Defender Security Center:
- Protezione da virus e minacce
- Prestazioni e integrità del dispositivo
- Protezione firewall e della rete
- Controllo delle app e del browser
- Opzioni famiglia

Gli amministratori IT possono anche personalizzare le notifiche ricevute dagli utenti. Ad esempio, è possibile specificare se gli utenti ricevono tutte le notifiche generate dagli elementi chiave visibili in WDSC o solo le notifiche critiche. Le notifiche non critiche includono riepiloghi periodici delle attività di Windows Defender Antivirus e notifiche per il completamento delle analisi. Tutte le altre notifiche sono considerate critiche. È inoltre possibile personalizzare il contenuto della notifica, ad esempio specificare informazioni di contatto IT da incorporare nelle notifiche visualizzate sui dispositivi degli utenti.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>Supporto di più connettori per la gestione dei certificati SCEP e PFX <!-- 1361755 -->

I clienti che usano NDES Connector in locale per il recapito dei certificati ai dispositivi possono ora configurare più connettori in un singolo tenant.

Questa nuova funzionalità supporta lo scenario seguente:

- **Disponibilità elevata**

Ogni istanza di NDES Connector esegue il pull delle richieste di certificato da Intune.  Se un'istanza di NDES Connector risulta offline, l'altro connettore può continuare a elaborare le richieste.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>Per il nome soggetto del cliente è possibile usare la variabile AAD_DEVICE_ID <!-- 1468599 -->

Quando si crea un profilo certificato SCEP in Intune, è ora possibile usare la variabile AAD_DEVICE_ID quando si compila il nome soggetto personalizzato.   Quando viene richiesto il certificato con questo profilo SCEP, la variabile viene sostituita con l'ID del dispositivo AAD del dispositivo che effettua la richiesta di certificato.


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Gestire dispositivi macOS registrati in Jamf con il motore di conformità dei dispositivi di Intune <!-- 1592747 -->
È ora possibile usare Jampf per inviare informazioni sullo stato dei dispositivi macOS a Intune, che ne valuterà la conformità ai criteri definiti nella console di Intune. In base allo stato di conformità dei dispositivi e ad altre condizioni (ad esempio la posizione, il rischio utente e così via), l'accesso condizionale imporrà la conformità ai dispositivi macOS che accedono alle applicazioni cloud e locali connesse ad Azure AD, incluso Office 365. Altre informazioni sulla [configurazione dell'integrazione Jamf](conditional-access-integrate-jamf.md) e l'[applicazione della conformità per i dispositivi gestiti Jamf](conditional-access-assign-jamf.md).

#### <a name="new-ios-device-action------1424701---"></a>Nuova azione per dispositivi iOS <!-- 1424701 -->

È ora possibile arrestare i dispositivi iOS 10.3 con supervisione. Questa azione arresta il dispositivo immediatamente senza avviso all'utente finale. L'azione **Shut down (supervised only)** (Arresta - solo con supervisione) è disponibile nelle proprietà del dispositivo quando si seleziona un dispositivo nel carico di lavoro **Dispositivo**.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Impedire modifiche di data/ora nei dispositivi Samsung Knox <!-- 1468103 -->

È stata aggiunta a una nuova funzionalità che consente di bloccare le modifiche di data e ora nei dispositivi Samsung Knox. Questa impostazione è disponibile in **Profili di configurazione dei dispositivi** > **Limitazioni del dispositivo (Android)** > **Generale**.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Supporto dell'account della risorsa per Surface Hub <!-- 1566442  -->

È stata aggiunta una nuova azione del dispositivo in modo gli amministratori possano definire e aggiornare l'account della risorsa associato a un dispositivo Surface Hub.

L'account della risorsa viene usato da Surface Hub per l'autenticazione con Skype/Exchange in modo da poter partecipare a una riunione. È possibile creare un account della risorsa univoco in modo che il dispositivo Surface Hub compaia nella riunione come sala riunioni. Ad esempio, l'account della risorsa potrebbe essere visualizzato come *Sala riunioni B41/6233*. L'account della risorsa (noto come account del dispositivo) per Surface Hub in genere deve essere configurato per la posizione della sala riunione e quando occorre modificare altri parametri dell'account della risorsa.

Quando gli amministratori vogliono aggiornare l'account della risorsa in un dispositivo, devono specificare le credenziali correnti di Active Directory o Azure Active Directory associate al dispositivo. Se la rotazione delle password è attivata per il dispositivo, gli amministratori devono passare ad Azure Active Directory per trovare la password.

> [!NOTE]
> Tutti i campi vengano inviati in blocco e sovrascrivono tutti i campi configurati in precedenza. Anche i campi vuoti sovrascrivono i campi esistenti.

L'elenco seguente include le impostazioni configurabili dagli amministratori:

- **Account della risorsa**
   - **Utente di Active Directory**

      NomeDominio\NomeUtente o nome dell'entità utente (UPN): user@domainname.com

   - **Password**

- **Parametri facoltativi per l'account della risorsa** (devono essere impostati tramite l'account della risorsa specificato)

   - **Periodo di rotazione delle password**

     Assicura che la password dell'account venga aggiornata automaticamente da Surface Hub ogni settimana per motivi di sicurezza. Per configurare eventuali parametri dopo aver abilitato questo account, è prima di tutto necessario reimpostare la password dell'account in Azure Active Directory.

   - **Indirizzo SIP (Session Initiation Protocol)**

     Usato solo quando l'individuazione automatica ha esito negativo.

   - **Posta elettronica**

     Indirizzo di posta elettronica di dispositivo/account della risorsa.

   - **Exchange Server**

     Necessario solo quando l'individuazione automatica ha esito negativo.

   - **Sincronizzazione calendario**

     Specifica se sono abilitati la sincronizzazione del calendario e altri servizi di Exchange Server. Ad esempio, la sincronizzazione delle riunioni.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>Installare app di Office in dispositivi macOS <!-- 1494311 -->
È ora possibile installare app di Office nei dispositivi macOS. Questo nuovo tipo di app consentirà di installare Word, Excel, PowerPoint, Outlook e OneNote. Queste app includono anche Microsoft AutoUpdater (MAU), per mantenere più facilmente sicure e aggiornate le app.

### <a name="app-management"></a>Gestione delle app

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>Eliminare un token Volume Purchasing Program iOS <!-- 820879 -->
È possibile eliminare il token Volume Purchasing Program (VPP) iOS tramite la console. Ciò potrebbe risultare necessario in presenza di istanze duplicate di un token VPP.

### <a name="intune-apps"></a>App di Intune


### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>Una nuova raccolta di entità denominata Current User è limitata ai dati degli utenti attualmente attivi <!-- 1667026 -->

La raccolta di entità **Users** contiene tutti gli utenti di Azure Active Directory (Azure AD) con licenze assegnate nell'organizzazione. Nel corso dell'ultimo mese, ad esempio, è possibile che un utente sia stato aggiunto e rimosso da Intune. Pertanto, se anche l'utente non è presente al momento del report, l'utente e lo stato sono comunque presenti nei dati. In questo caso, è possibile creare un report che mostri la durata della presenza storica dell'utente nei dati.

La nuova raccolta di entità **Current User**, invece, contiene solo gli utenti che non sono stati rimossi. La raccolta di entità **Current User**, quindi, è limitata agli utenti attualmente attivi. Per informazioni sulla raccolta di entità **Current User**, vedere [Informazioni di riferimento per l'entità User corrente](reports-ref-current-user.md).


### <a name="updated-graph-apis----1736360---"></a>API Graph aggiornate <!-- 1736360 -->

In questa versione sono state aggiornate alcune delle API Graph per Intune in versione beta. Vedere il [log delle modifiche delle API Graph](https://developer.microsoft.com/graph/docs/concepts/changelog) mensile per altre informazioni.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune supporta le app non consentite di Windows Information Protection (WIP) <!-- 1479103 -->
È possibile specificare app non consentite in Intune. Le app non consentite non possono accedere alle informazioni aziendali e si tratta in effetti della condizione opposta alle app incluse nell'elenco delle app consentite. Per altre informazioni, vedere la [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Elenco consigliato delle app non consentite per Windows Information Protection).


## <a name="november-2017"></a>Novembre 2017

### <a name="troubleshoot-enrollment-issues-----746324---"></a>Risolvere i problemi di registrazione  <!-- 746324 -->

L'area di lavoro **Risoluzione dei problemi** ora visualizza i problemi di registrazione dell'utente. Informazioni dettagliate sul problema e i passaggi suggeriti per la correzione possono essere utili ad amministratori e operatori di help desk per la risoluzione dei problemi. Alcuni problemi di registrazione non vengono rilevati ed è possibile che per alcuni errori non siano disponibili suggerimenti per la correzione.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>Restrizioni di registrazione assegnate ai gruppi <!-- 747598 -->

L'amministratore di Intune ora può [creare restrizioni di registrazione Tipo di dispositivo e Limite di dispositivi personalizzate per i gruppi di utenti](enrollment-restrictions-set.md).

Il portale di Azure di Intune consente di creare fino a 25 istanze di ogni tipo di restrizione, che possono essere successivamente assegnate ai gruppi di utenti. Le restrizioni assegnate ai gruppi sostituiscono le restrizioni predefinite.

Tutte le istanze di un tipo di restrizione vengono mantenute in un elenco nell'ordine. L'ordine definisce un valore di priorità per la risoluzione dei conflitti. Un utente interessato da più istanze di restrizione viene limitato solo dall'istanza con il valore di priorità più alto. È possibile modificare la priorità di un'istanza specifica trascinandola in una posizione diversa nell'elenco.

Questa funzionalità verrà rilasciata con la migrazione delle impostazioni di Android for Work dal menu di registrazione di Android for Work al menu Restrizioni registrazione. Poiché la migrazione può richiedere diversi giorni, è possibile che l'account venga aggiornato per altre parti del rilascio di novembre prima che l'assegnazione dei gruppi risulti abilitata per le restrizioni di registrazione.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>Supporto di più connettori del servizio Registrazione dispositivi di rete <!-- 1528104 -->

Il servizio Registrazione dispositivi di rete (NDES, Network Device Enrollment Service) consente ai dispositivi mobili in esecuzione senza credenziali di dominio di ottenere certificati basati sul protocollo SCEP (Simple Certificate Enrollment Protocol).
Con questo aggiornamento, sono supportati più connettori del servizio Registrazione dispositivi di rete.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Gestire i dispositivi Android for Work indipendentemente dai dispositivi Android <!-- 1490731 EEready-->

Intune supporta la gestione della registrazione di dispositivi Android for Work indipendentemente dalla piattaforma Android. Queste impostazioni vengono gestite in **Registrazione del dispositivo** > **Restrizioni registrazione** > **Restrizioni sul tipo di dispositivi**. In precedenza erano disponibili in **Registrazione del dispositivo** > **Registrazione di Android for Work** > **Impostazioni di registrazione per Android for Work**.

Per impostazione predefinita, le impostazioni dei dispositivi Android for Work corrispondono alle impostazioni dei dispositivi Android. Tuttavia, dopo la modifica delle impostazioni Android for Work questa corrispondenza andrà persa.

Se si blocca la registrazione dei dispositivi Android for Work personali, solo i dispositivi Android aziendali possono essere registrati come Android for Work.

Durante l'uso delle nuove impostazioni, considerare i punti seguenti:

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work non è mai stata caricata in precedenza

La nuova piattaforma Android for Work è bloccata nelle Restrizioni sul tipo di dispositivi predefinite. Dopo aver caricato la funzionalità, è possibile consentire la registrazione dei dispositivi con Android for Work. A tale scopo, modificare il valore predefinito o creare una nuova restrizione dei tipi di dispositivo per sostituire la restrizione predefinita.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>Se la registrazione di Android for Work è stata caricata

Se la registrazione è stata caricata in precedenza, la situazione varia a seconda dell'impostazione selezionata:

| Impostazione | Stato di Android for Work nella restrizione dei tipi di dispositivo predefinita | Note |
| --- | --- | --- |
| **Gestisci tutti i dispositivi come Android** | Bloccato | Tutti i dispositivi Android devono essere registrati senza Android for Work. |
| **Gestisci i dispositivi supportati come Android for Work** | Consentito | Tutti i dispositivi Android che supportano Android for Work devono essere registrati con Android for Work. |
| **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work** | Bloccato | Per sostituire l'impostazione predefinita è stato creato un criterio Restrizione dei tipi di dispositivo separato. Questo criterio definisce i gruppi precedentemente selezionati per consentire la registrazione di Android for Work. Gli utenti inclusi nei gruppi selezionati continueranno a essere autorizzati a registrare i loro dispositivi Android for Work. A tutti gli altri utenti non è consentita la registrazione con Android for Work. |

In tutti i casi, viene mantenuto il regolamento previsto. Per mantenere l'autorizzazione globale o per i singoli gruppi di Android for Work nel proprio ambiente non è necessario eseguire alcuna operazione.

### <a name="google-play-protect-support-on-android----908720---"></a>Supporto di Google Play Protect in Android <!-- 908720 -->

Con il rilascio di Android Oreo, Google introduce un gruppo di funzionalità di sicurezza denominato Google Play Protect che consente a utenti e organizzazioni di eseguire app e immagini Android sicure. Intune ora supporta le funzionalità di Google Play Protect, inclusa l'attestazione remota SafetyNet. Gli amministratori possono impostare requisiti per i criteri di conformità che richiedono la configurazione e l'integrità di Google Play Protect.
L'**attestazione dispositivo SafetyNet** richiede che il dispositivo si connetta a un servizio Google per verificare che il dispositivo sia integro e non compromesso. Gli amministratori possono anche definire un'impostazione del profilo di configurazione per far sì che Android for Work richieda la verifica delle app installate da parte di Google Play Services. Se un dispositivo non è conforme ai requisiti di Google Play Protect, l'accesso condizionale può impedire agli utenti di accedere alle risorse aziendali.

- Informazioni su [come creare un criterio di conformità del dispositivo per abilitare Google Play Protect](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect).

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>Protocollo di testo consentito dalle app gestite <!-- 1414050  -->

Le app gestite da Intune App SDK sono in grado di inviare messaggi SMS.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>Report sull'installazione delle app aggiornato per includere lo stato Installazione in sospeso <!-- 1249446 -->  

Il report **Stato di installazione dell'app**, accessibile per ogni app attraverso l'elenco **App** nel carico di lavoro **App client** ora contiene il conteggio **L'installazione è in sospeso** per utenti e dispositivi.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>API di inventario delle app iOS 11 per il rilevamento delle minacce per i dispositivi mobili<!-- 1391759 -->

Intune raccoglie le informazioni degli inventari delle app dei dispositivi personali e aziendali e le rende disponibili per i provider del servizio di rilevamento delle minacce per i dispositivi mobili (MTD, Mobile Threat Detection), ad esempio Lookout for Work. Si possono raccogliere gli inventari delle app dagli utenti di dispositivi iOS 11 e versioni successive.

**Inventario delle app**  
Gli inventari dei dispositivi aziendali e personali iOS 11 e versioni successive vengono inviati al provider del servizio MTD. I dati dell'inventario delle app includono:

 - ID dell'app
 - Versione dell'app
 - Versione breve dell'app
 - Nome dell'app
 - Dimensione del bundle dell'app
 - Dimensione dinamica dell'app
 - Indicazione sulla convalida dell'app
 - Indicazione sulla gestione dell'app

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>Eseguire la migrazione di dispositivi e utenti dalla soluzione MDM ibrida alla versione autonoma di Intune <!-- 1463747 wnready -->
Sono ora disponibili nuovi strumenti e processi per lo spostamento di utenti e dei relativi dispositivi dalla soluzione MDM ibrida a Intune nel portale di Azure, che consentono di eseguire le attività seguenti:
- Copiare criteri e profili dalla console di Configuration Manager a Intune nel portale di Azure
- Spostare un sottoinsieme di utenti a Intune nel portale di Azure, mantenendo il resto nella soluzione MDM ibrida
- Eseguire la migrazione di dispositivi a Intune nel portale di Azure senza la necessità di registrarli nuovamente

Per informazioni dettagliate, vedere [Eseguire la migrazione di dispositivi e utenti dalla soluzione MDM ibrida alla versione autonoma di Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale<!-- 676614 -->
Dopo che Exchange Connector crea una connessione a Exchange usando il CAS specificato, il connettore è ora in grado di individuare altri CAS. Se il CAS principale diventa non disponibile, il connettore eseguirà il failover a un altro CAS, se disponibile, fino a quando non diventa disponibile il CAS principale. Per altri dettagli, vedere [Supporto a disponibilità elevata di Exchange Connector locale](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support).

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>Riavvio remoto del dispositivo iOS (solo supervisionato) <!-- 1424595 -->

È ora possibile riavviare un dispositivo iOS 10.3 e versioni successive supervisionato usando un'azione del dispositivo. Per altre informazioni sull'uso dell'azione di riavvio del dispositivo, vedere [Riavviare i dispositivi in remoto con Intune](device-restart.md).

> [!Note]
> Per eseguire questo comando sono necessari un dispositivo supervisionato e il diritto di accesso **Device Lock** (Blocco dispositivo). Il dispositivo viene riavviato immediatamente. I dispositivi iOS bloccati con passcode non si ricollegano a una rete Wi-Fi dopo il riavvio. È possibile che dopo il riavvio non siano in grado di comunicare con il server.

### <a name="single-sign-on-support-for-ios----1333645---"></a>Supporto Single Sign-On per iOS <!-- 1333645 -->  

È possibile usare Single Sign-On per gli utenti iOS. Le app iOS codificate per la ricerca delle credenziali dell'utente nel payload Single Sign-on funzionano con questo aggiornamento della configurazione del payload. È anche possibile usare l'UPN e l'ID dispositivo di Intune per configurare il nome dell'entità e l'area di autenticazione. Per informazioni dettagliate, vedere [Configurare Intune per l'accesso Single Sign-On al dispositivo iOS](sso-ios.md).

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>Aggiungere "Trova il mio iPhone" per i dispositivi personali <!--1427287-->
È ora possibile verificare se i dispositivi iOS hanno il Blocco attivazione attivato. Questa funzionalità era disponibile in precedenza nel portale classico di Intune.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Bloccare in remoto un dispositivo macOS gestito con Intune <!-- 1437691 -->

È possibile bloccare un dispositivo macOS smarrito e impostare un PIN di ripristino di 6 cifre. Quando il dispositivo è bloccato, il pannello **Device overview** (Panoramica dispositivo) visualizza il PIN fino a quando non viene inviata un'altra azione del dispositivo.

Per altre informazioni, vedere [Bloccare in remoto i dispositivi gestiti con Intune](device-remote-lock.md).

### <a name="new-scep-profile-details-supported----1559808---"></a>Nuovi dettagli del profilo SCEP supportati <!-- 1559808 -->

Gli amministratori ora possono configurare impostazioni aggiuntive durante la creazione di un profilo SCEP nelle piattaforme Windows, iOS, macOS e Android.  Gli amministratori possono impostare IMEI, numero di serie o nome comune, inclusa la posta elettronica nel formato del nome soggetto.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>Mantenere i dati durante il ripristino delle impostazioni predefinite  <!--1588489 -->
Quando si reimposta Windows 10 versione 1709 e successive ripristinando le impostazioni predefinite, è disponibile una nuova funzionalità. Gli amministratori possono specificare se la registrazione del dispositivo e altri dati di provisioning vengono mantenuti nel dispositivo quando viene eseguito il ripristino delle impostazioni predefinite.

Quando viene eseguito il ripristino delle impostazioni predefinite vengono mantenuti i dati seguenti:
- Account utente associati al dispositivo
- Stato del computer (aggiunto a un dominio, aggiunto ad Azure Active Directory)
- Registrazione MDM
- App installate OEM (app dello Store e Win32)
- Profilo utente
- Dati utente esterni al profilo utente
- Accesso automatico dell'utente

I dati seguenti non vengono mantenuti:
- File dell'utente
- App installate dell'utente (app dello Store e Win32)
- Impostazioni del dispositivo non predefinite


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Assegnazioni degli anelli di aggiornamento di Windows 10 visualizzate <!-- 1621837 -->
Durante la **Risoluzione dei problemi** per l'utente visualizzato le assegnazioni degli anelli di aggiornamento di Windows 10 sono visibili.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Impostazioni della frequenza di creazione di report di Windows Defender Advanced Threat Protection  <!-- 1455974  -->
Il servizio Windows Defender Advanced Threat Protection (WDATP) consente agli amministratori di gestire la frequenza di creazione di report per i dispositivi gestiti. Con la nuova opzione **Accelera la frequenza di creazione di report di telemetria**, WDATP raccoglie i dati e valuta i rischi con maggior frequenza. L'impostazione predefinita per la creazione di report ottimizza velocità e prestazioni. L'aumento della frequenza di creazione di report può essere utile per i dispositivi a rischio elevato. Questa impostazione è disponibile nel profilo **Windows Defender ATP** in **Configurazioni dispositivi**.

### <a name="audit-updates----1412961---"></a>Aggiornamenti dei controlli <!-- 1412961 -->  
La funzione di controllo di Intune offre un record delle operazioni di modifica correlate a Intune.  Tutte le operazioni di creazione, aggiornamento ed eliminazione e le attività remote vengono acquisite e mantenute per un anno.  Il portale di Azure offre una visualizzazione degli ultimi 30 giorni dei dati di controllo di ogni carico di lavoro a cui è possibile applicare filtri.  Un'API Graph corrispondente consente il recupero dei dati di controllo archiviati dell'ultimo anno.

La funzione di controllo è disponibile nel gruppo **MONITOR**. Viene visualizzata una voce di menu **Log di controllo** per ogni carico di lavoro.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>L'app Portale aziendale per macOS è ora disponibile <!--1541700-->
L'app Portale aziendale Intune in macOS offre una nuova esperienza utente, ottimizzata in modo da visualizzare correttamente tutte le informazioni e le notifiche di conformità necessarie agli utenti in relazione a tutti i dispositivi che hanno registrato. Dopo aver distribuito l'app Portale aziendale Intune in un dispositivo, Microsoft AutoUpdate per macOS fornirà i necessari aggiornamenti. È possibile scaricare la nuova app Portale aziendale Intune per macOS accedendo al sito Web dell'app Portale aziendale Intune da un dispositivo macOS.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner è ora incluso nell'elenco di app approvate per la gestione delle app mobili <!-- 1248473 -->
L'app Microsoft Planner per iOS e Android fa ora parte delle app approvate in base ai criteri di gestione delle app mobili. L'app può essere configurata tramite il pannello Protezione app di Intune nel portale di Azure di tutti i tenant.
- Altre informazioni sull'[elenco di app approvate per la gestione dei dispositivi mobili](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>Frequenza di aggiornamento dei requisiti di VPN per app nei dispositivi iOS <!-- 1547061 -->  
Gli amministratori possono ora rimuovere i requisiti di VPN per app relativi alle app installate in dispositivi iOS; i dispositivi interessati verranno aggiornati dopo la successiva archiviazione di Intune, che si verifica in genere entro 15 minuti.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Supporto per Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->
È ora disponibile il Management Pack di System Center Operations Manager (SCOM) per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questa funzionalità consente di eseguire il monitoraggio del servizio in diversi modi quando è necessario risolvere un problema.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Co-gestione per i dispositivi Windows 10  <!-- 1243445 -->
La co-gestione è una soluzione che rappresenta un ponte tra la gestione tradizionale e quella moderna e consente di effettuare la transizione con un approccio graduale. La co-gestione è fondamentalmente una soluzione in cui i dispositivi Windows 10 vengono gestiti contemporaneamente da Configuration Manager e Microsoft Intune e aggiunti ad Active Directory (AD) e Azure Active Directory (Azure AD).  Questa configurazione offre la possibilità di effettuare una modernizzazione graduale con un ritmo adatto alla propria organizzazione nei casi in cui una transizione immediata non è possibile.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>Limitare la registrazione di Windows specificando la versione del sistema operativo<!-- 245498 -->
L'amministratore di Intune può ora specificare una versione minima e massima di Windows 10 per le registrazioni dei dispositivi. È possibile impostare queste limitazioni nel pannello **Configurazioni della piattaforma**.

Intune supporta ancora la registrazione di PC e telefoni Windows 8.1. È però possibile impostare solo le versioni di Windows 10 con limiti minimi e massimi. Per consentire la registrazione di dispositivi 8.1, non specificare il limite minimo.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Avvisi per dispositivi non assegnati Windows AutoPilot <!-- 1631236 -->
Nella pagina **Microsoft Intune** > **Registrazione del dispositivo** > **Panoramica** è disponibile un nuovo avviso per dispositivi non assegnati Windows AutoPilot. In questo avviso viene specificato il numero di dispositivi del programma AutoPilot che non hanno profili di AutoPilot Deployment assegnati. Usare le informazioni contenute nell'avviso per creare i profili e assegnarli ai dispositivi non assegnati. Selezionando l'avviso, verrà visualizzato un elenco completo di dispositivi Windows AutoPilot e le relative informazioni dettagliate. Per altre informazioni, vedere [Registrare dispositivi Windows con il programma Windows AutoPilot Deployment](https://docs.microsoft.com/intune/enrollment-autopilot).


### <a name="refresh-button-for-devices-list-------1333581---"></a>Pulsante Aggiorna per l'elenco di dispositivi<!-- 1333581 -->
Poiché l'elenco dei dispositivi non viene aggiornato automaticamente, è possibile usare il nuovo pulsante Aggiorna per aggiornare i dispositivi contenuti nell'elenco.

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Supporto dell'autorità di certificazione Symantec Cloud  <!-- 1333638 -->    
Intune supporta ora la CA Symantec Cloud, che consente al Connettore di certificati di Intune di rilasciare certificati PKCS dalla CA Symantec Cloud a dispositivi gestiti Intune. Se si usa già il Connettore di certificati di Intune con l'autorità di certificazione (CA) Microsoft, è possibile usare la configurazione esistente del Connettore di certificati di Intune per aggiungere il supporto della CA Symantec.

### <a name="new-items-added-to-device-inventory-----1404455---"></a>Nuovi elementi aggiunti all'inventario dei dispositivi<!--1404455 -->
I nuovi elementi sono ora disponibili nell'[inventario dei dispositivi registrati](device-inventory.md):

- Indirizzo MAC Wi-Fi
- Spazio di archiviazione totale
- Spazio disponibile totale
- MEID
- Gestore telefonico del sottoscrittore

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>Impostare l'accesso per le app mediante una patch di protezione Android minima nel dispositivo<!-- 1278463 -->   
L'amministratore può definire la patch di protezione Android minima che deve essere installata nel dispositivo per poter accedere a un'applicazione gestita in un account gestito.

> [!Note]  
> Questa funzionalità limita solo le patch di protezione rilasciate da Google nei dispositivi Android 6.0 e versioni successive.

### <a name="app-conditional-launch-support----1193313---"></a>Supporto di avvio condizionale all'app <!-- 1193313 -->
Gli amministratori IT possono ora impostare un requisito usando il portale di amministrazione di Azure per applicare un passcode anziché un PIN numerico PIN attraverso la gestione delle applicazioni mobili (MAM) all'avvio dell'applicazione. Se il requisito viene configurato, all'utente viene richiesto di impostare e usare un passcode prima di accedere alle applicazioni con supporto MAM. Un passcode è un PIN numerico con almeno un carattere speciale o una lettera maiuscola o minuscola. In questa versione di Intune la funzione è abilitata **solo in iOS**. Il supporto di Intune per i passcode è simile a quello dei PIN numerici: viene impostata una lunghezza minima e sono consentiti caratteri e sequenze ripetuti. Questa funzionalità richiede il supporto delle applicazioni (ovvero di WXP, Outlook, Managed Browser, Yammer) per l'integrazione di Intune App SDK con il codice della funzionalità stessa, in modo che le impostazioni di passcode possano essere applicate nelle applicazioni di destinazione.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>Numero di versione delle app line-of-business nel report sullo stato dell'installazione del dispositivo <!-- 1233999 -->
In questa versione il report sullo stato dell'installazione del dispositivo visualizza il numero di versione dell'app per le app line-of-business per iOS e Android. Queste informazioni possono essere usate per la risoluzioni dei problemi delle app o per individuare i dispositivi che eseguono versioni delle app non aggiornate.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>Gli amministratori possono ora configurare le impostazioni del firewall in un dispositivo usando un profilo di configurazione del dispositivo <!-- 951708 -->   
Gli amministratori possono attivare il firewall per i dispositivi e anche configurare diversi protocolli per le reti di dominio, private e pubbliche.  Le impostazioni del firewall sono disponibili nel profilo "Endpoint Protection".

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard consente di proteggere i dispositivi dai siti Web non attendibili specificati dall'organizzazione <!-- 958257 -->   
Gli amministratori possono definire i siti come "attendibili" o "aziendali" usando un flusso di lavoro Windows Information Protection o il nuovo profilo "limite di rete" disponibile nelle configurazioni del dispositivo. I siti non elencati nel limite di rete attendibile del dispositivo Windows 10 a 64 bit e visualizzati con Microsoft Edge vengono invece aperti in un browser all'interno di un computer virtuale Hyper-V.

Application Guard è disponibile nei profili di configurazione del dispositivo, nel profilo "Endpoint Protection". Nel profilo gli amministratori possono configurare l'iterazione tra il browser virtualizzato e il computer host, i siti non attendibili e i siti attendibili e l'archiviazione dei dati nel browser virtualizzato. Per usare Application Guard in un dispositivo, è necessario innanzitutto configurare un limite di rete. È importante definire un solo limite di rete per dispositivo.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Il controllo delle applicazioni di Windows Defender in Windows 10 Enterprise consente di considerare attendibili solo le app autorizzate <!-- 1031096 -->    
Considerate le migliaia di nuovi file dannosi creati ogni giorno, l'uso di un sistema di rilevamento antivirus basato su firma per la protezione da software dannoso potrebbe non offrire più una difesa adeguata dai nuovi attacchi. Con il controllo delle applicazioni di Windows Defender in Windows 10 Enterprise è possibile modificare la configurazione del dispositivo passando da una modalità in cui vengono considerate attendibili tutte le app a eccezione di quelle bloccate da un antivirus o da un'altra soluzione di sicurezza a una modalità in cui il sistema operativo considera attendibili solo le app autorizzate dalla propria organizzazione. È possibile impostare le app come attendibili nel controllo delle applicazioni di Windows Defender.

Usando Intune è possibile configurare i criteri di controllo delle applicazioni in modalità "solo controllo" o in modalità di imposizione. In modalità "solo controllo" le app non vengono bloccate. La modalità "solo controllo" registra tutti gli eventi nei log del client locali. È anche possibile specificare se autorizzare l'esecuzione solo dei componenti Windows e delle app di Microsoft Store o anche quella di altre app affidabili in base a quanto definito da Intelligent Security Graph.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Windows Defender Exploit Guard è un nuovo set di funzionalità di prevenzione intrusioni per Windows 10 <!-- 1063615 -->   
Windows Defender Exploit Guard include regole personalizzate per ridurre la vulnerabilità agli exploit delle applicazioni, evitare le minacce di macro e script, blocca automaticamente le connessioni di rete verso indirizzi IP con reputazione negativa ed è in grado di proteggere i dati da ransomware e minacce sconosciute. Windows Defender Exploit Guard include i componenti seguenti:

- La **Riduzione della superficie di attacco** offre regole che consentono di evitare le minacce di macro, script e posta elettronica.
- L'**Accesso controllato alle cartelle** blocca automaticamente l'accesso al contenuto delle cartelle protette.
- Il **filtro di rete** blocca la connessione in uscita di tutte le app verso indirizzi IP o domini con reputazione negativa
- La **protezione dagli exploit** offre limitazioni di memoria, flusso di controllo e criteri che è possibile usare per proteggere un'applicazione dagli exploit.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Gestire gli script di PowerShell in Intune per i dispositivi Windows 10 <!-- 790537 -->

L'estensione di gestione di Intune consente di caricare script di PowerShell in Intune da eseguire in dispositivi Windows 10. L'estensione integra le funzionalità di gestione di dispositivi mobili (MDM, Mobile Device Management) di Windows 10 e rende più semplice il passaggio a una gestione moderna. Per informazioni dettagliate, vedere [Gestire gli script di PowerShell in Intune per i dispositivi Windows 10](intune-management-extension.md).

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Nuove impostazioni delle limitazioni del dispositivo per Windows 10      <!-- 1308850 -->
-    Messaggistica (solo dispositivi mobili): disabilitare il test o i messaggi MMS
-    Password: impostazioni per l'abilitazione di FIPS e l'uso dei dispositivi secondari Windows Hello per l'autenticazione 
-    Visualizzazione: impostazioni per attivare o disattivare il ridimensionamento del programma GDI per le app legacy

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Limitazioni del dispositivo per la modalità a tutto schermo per Windows 10 <!-- 1308872 -->   
È possibile impostare una limitazione per la modalità tutto schermo per gli utenti dei dispositivi Windows 10 che limita gli utenti a un set di app predefinite.  A tale scopo, creare un profilo di limitazione del dispositivo Windows 10 e specificare le impostazioni della modalità a tutto schermo.

La modalità a tutto schermo supporta due modalità: la modalità **applicazione singola** che consente all'utente di eseguire una sola app e la modalità **app multiple** che consente l'accesso a più app.  Definire l'account utente e il nome del dispositivo che determinano le app supportate.  Dopo aver eseguito l'accesso, l'utente sarà limitato alle app definite.  Per altre informazioni, vedere [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp) (Provider del servizio di configurazione AssignedAccess). 

Per la modalità a tutto schermo sono necessari i requisiti seguenti:

- Intune deve essere l'autorità MDM.
- Le app devono essere già installate nel dispositivo di destinazione.
- Il [provisioning](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions) del dispositivo deve essere stato eseguito correttamente.

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>Nuovo profilo di configurazione del dispositivo per la creazione di limiti di rete <!-- 1311967 -->   
Un nuovo profilo di configurazione del dispositivo denominato **Limite di rete** è disponibile con gli altri profili di configurazione. Usare questo profilo per definire le risorse online da considerare aziendali e affidabili. È necessario definire un limite di rete per un dispositivo *prima* di usare funzionalità come Windows Defender Application Guard e Windows Information Protection nel dispositivo. È importante definire un solo limite di rete per dispositivo.

È possibile definire le risorse cloud aziendali, gli intervalli di indirizzi IP e i server proxy interni da considerare attendibili. Il limite di rete definito può essere utilizzato da altre funzionalità, ad esempio Windows Defender Application Guard e Windows Information Protection.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Due impostazioni aggiuntive per Windows Defender Antivirus <!-- 1338409 -->  
**Livello di blocco di file**

| | |
|---|---|
| Non configurato | **Non configurato** usa il livello di blocco predefinito di Windows Defender Antivirus e offre un rilevamento sicuro senza aumentare il rischio di rilevare file legittimi. |
| Alta | **Alto** applica un livello di rilevamento elevato.
| Elevato +  | **Elevato +** offre il livello Alto con misure di protezione aggiuntive che potrebbero influire sulle prestazioni del client.
| Tolleranza zero  | **Tolleranza zero** blocca tutti gli eseguibili sconosciuti. |

Sebbene sia improbabile, l'impostazione su **Alto** potrebbe causare il rilevamento di file legittimi.
È consigliabile impostare il livello di blocco di file sul valore predefinito **Non configurato**.

**Estensione del timeout per l'analisi dei file dal cloud**  

| | |
|--|--|
| Numero di secondi (0-50) | Specificare la quantità massima di tempo per la quale Windows Defender Antivirus deve bloccare un file in attesa di un risultato dal cloud. La quantità predefinita è 10 secondi: il tempo specificato con questa opzione (fino a un massimo di 50 secondi) viene aggiunto ai 10 secondi. Nella maggior parte dei casi l'analisi richiede molto meno tempo rispetto al tempo massimo. L'estensione della quantità di tempo consente al cloud di analizzare nel dettaglio i file sospetti. È consigliabile abilitare questa impostazione e specificare almeno 20 secondi aggiuntivi. |

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>VPN Citrix aggiunta per i dispositivi Windows 10 <!-- 1512457 -->  
È possibile configurare la VPN Citrix per i dispositivi Windows 10. Durante la configurazione di una VPN per Windows 10 e versioni successive è possibile scegliere la VPN Citrix nell'elenco *Selezionare un tipo di connessione* nel pannello **VPN di base**.

> [!Note]
> Configurazione Citrix per iOS e Android.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Chiavi precondivise supportate da connessioni Wi-Fi in iOS<!-- 1550823 -->
Per usare le chiavi precondivise per le connessioni WPA/WPA2-Personal in dispositivi iOS, è possibile configurare profili Wi-Fi. Questi profili vengono inviati al dispositivo dell'utente quando il dispositivo viene registrato in Intune.

Dopo che il profilo è stato inviato al dispositivo, il passaggio successivo cambia a seconda della configurazione del profilo.  Se è impostato per connettersi automaticamente, la connessione viene eseguita automaticamente quando viene richiesta la rete.  Se il profilo si connette manualmente, la connessione deve essere attivata manualmente dall'utente.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>Accesso ai log di app gestite per iOS<!-- 1469920 -->
Gli utenti finali che hanno installato Managed Browser possono ora visualizzare lo stato di gestione di tutte le app pubblicate Microsoft e inviare i log per la risoluzione dei problemi delle app iOS gestite.

Per altre informazioni su come abilitare la modalità di risoluzione dei problemi in Managed Browser in un dispositivo iOS, vedere [How to access to managed app logs using the Managed Browser on iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios) (Come accedere a log di app gestite tramite Managed Browser in iOS).

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>Miglioramenti al flusso di lavoro di configurazione dei dispositivi in Portale aziendale per iOS (versione 2.9.0) <!-- 1417174 -->

Il flusso di lavoro di configurazione dei dispositivi nell'app Portale aziendale per iOS è stato migliorato. Il linguaggio è più semplice e, dove possibile, sono state inserite schermate. Con l'inserimento del nome della società nel testo di configurazione, il linguaggio è più specifico per la società di riferimento. È possibile visualizzare il flusso di lavoro aggiornato nella pagina sulle  [novità nell'interfaccia utente delle app](whats-new-app-ui.md).


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>L'entità User contiene i dati utente più recenti nel modello di dati del data warehouse <!-- 1544273 -->
La prima versione del modello di dati del data Warehouse di Intune contiene solo i dati storici e recenti di Intune. Durante la creazione di report non è possibile acquisire lo stato corrente di un utente. In questo aggiornamento l'**entità User** viene popolata con i dati utente più recenti.


## <a name="october-2017"></a>Ottobre 2017

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>Il numero di versione delle app line-of-business iOS e Android è visibile <!-- 1380712 -->

Nelle app in Intune viene ora visualizzato il numero di versione per le app line-of-business iOS e Android. Il numero viene visualizzato nel portale di Azure nell'elenco delle app e nel pannello della panoramica dell'app. Gli utenti finali possono visualizzare il numero dell'app nell'app Portale aziendale e nel portale Web.

__Numero di versione completo__ Il numero di versione completo identifica una versione specifica dell'app. Il numero viene visualizzato come _Versione_(_Build_). Ad esempio, 2.2(2.2.17560800)

Il numero di versione completo include due componenti:

 - **Versione**  
   Il numero di versione è il numero di versione leggibile dell'app. Viene usato dagli utenti finali per identificare diverse versioni dell'app.

 - **Numero di build**  
    Il numero di build è un numero interno che può essere usato nel rilevamento delle app e per gestire l'app a livello di codice. Il numero di build si riferisce a un'iterazione dell'app che fa riferimento alle modifiche nel codice.

Per altre informazioni sui numeri di versione e lo sviluppo di app line-of-business, vedere [Introduzione a Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers).

### <a name="device-and-app-management-integration----677972---"></a>Integrazione della gestione delle applicazioni e dei dispositivi <!-- 677972 -->   
Ora che la gestione di dispositivi mobili (MDM) e la gestione di applicazioni mobili (MAM) di Intune sono entrambe accessibili dal portale di Azure, in Intune è stata iniziata l'integrazione dell'esperienza di amministrazione IT nella gestione delle applicazioni e dei dispositivi. Queste modifiche hanno lo scopo di rendere più semplice l'esperienza di gestione dei dispositivi e delle app.

Per altre informazioni sulle modifiche MDM e MAM annunciate, vedere il [blog del team di supporto di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/).

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Nuovi avvisi di registrazione per i dispositivi Apple <!-- 1471790 -->
Nella pagina di panoramica per la registrazione verranno visualizzati avvisi utili per gli amministratori IT riguardanti la gestione dei dispositivi Apple. Gli avvisi verranno visualizzati nella pagina Panoramica quando il certificato per le notifiche push MDM Apple sta per scadere o è già scaduto, quando il token di Device Enrollment Program sta per scadere o è già scaduto e quando vi sono dispositivi non assegnati in Device Enrollment Program.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>Sostituzione dei token di supporto per la configurazione di app senza registrazione del dispositivo <!-- 1080364 -->

È possibile usare i token per i valori dinamici nelle configurazioni di app per le app nei dispositivi che non sono registrati. Per altre informazioni, vedere [Add app configuration policies for managed apps without device enrollment](app-configuration-policies-managed-app.md) (Aggiungere criteri di configurazione delle app per le app gestite senza registrazione dei dispositivi).

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Aggiornamenti all'app Portale aziendale per Windows 10 <!--1299474-->
La pagina Impostazioni dell'app Portale aziendale per Windows 10 è stata aggiornata in modo da rendere più coerenti le impostazioni e le azioni previste dall'utente sui vari tipi di impostazioni. Ne è stato aggiornato anche il layout per uniformarlo a quello delle altre app Windows. È possibile trovare le immagini "Prima/Dopo" nella pagina sulle [novità nell'interfaccia utente delle app](whats-new-app-ui.md).

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Comunicare agli utenti finali quali informazioni possono essere visualizzate per i dispositivi Windows 10 <!--1337920-->
È stata aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo nell'app Portale aziendale per Windows 10. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente da questa pagina dalla documentazione di Intune per gli utenti finali. Potranno accedere a queste informazioni anche dalla schermata **Informazioni**.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Richiesta di commenti e suggerimenti per l'app Portale aziendale per Android <!--1165249-->
L'app Portale aziendale per Android richiede ora commenti e suggerimenti da parte degli utenti finali. I commenti vengono inviati direttamente a Microsoft e offrono agli utenti finali la possibilità di valutare l'app nello store pubblico Google Play. L'invio di commenti e suggerimenti non è comunque obbligatorio e può essere facilmente ignorato per continuare a usare regolarmente l'app.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Consentire agli utenti di usare l'app del portale aziendale per Android <!-- 1573324, 1573150, 1558616, 1564878 -->

L'app Portale aziendale per Android include ora istruzioni per gli utenti finali per consentire di comprendere e, dove possibile, risolvere autonomamente nuovi casi d'uso.
- Gli utenti finali verranno indirizzati al [portale di Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) per rimuovere un dispositivo se è stato raggiunto il numero massimo di dispositivi che sono autorizzati ad aggiungere.
- Agli utenti finali verranno indicati i passaggi da eseguire per [correggere gli errori di attivazione sui dispositivi Samsung Knox](https://go.microsoft.com/fwlink/?linkid=859718) o per [disattivare la modalità di risparmio energia](/intune-user-help/power-saving-mode-android). Se nessuna delle soluzioni proposte corregge il problema, verrà descritto come [inviare i log a Microsoft](/intune-user-help/send-logs-to-microsoft-android).

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Nuova azione 'Risolvi' disponibile per i dispositivi Android <!-- 1583480 -->

L'app del portale aziendale per Android include ora una nuova azione 'Risolvi' nella pagina _Aggiorna impostazioni del dispositivo_. La selezione di questa opzione indirizza l'utente finale direttamente all'impostazione che rende il dispositivo non conforme. L'app del portale aziendale per Android supporta attualmente questa opzione per le impostazioni di [passcode del dispositivo](/intune-user-help/set-your-pin-or-password-android), [debug USB](/intune-user-help/you-need-to-turn-off-usb-debugging-android) e [origini sconosciute](/intune-user-help/you-need-to-turn-off-unknown-sources-android).

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Indicatore dello stato di avanzamento della configurazione del dispositivo in Portale aziendale Android <!-- 1565657 -->
Quando un utente registra un dispositivo, nell'app Portale aziendale per Android viene visualizzato un indicatore dello stato di avanzamento del processo di configurazione del dispositivo. L'indicatore elenca i nuovi stati nell'ordine seguente: "Configurazione del dispositivo...", "Registrazione del dispositivo...", "Completamento della registrazione del dispositivo..." e "Completamento della configurazione del dispositivo...".

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>Supporto dell'autenticazione basata sui certificati nel portale aziendale per iOS <!--1029830-->
È stato aggiunto il supporto dell'autenticazione basata sui certificati (CBA) nell'app del portale aziendale per iOS. Gli utenti con autenticazione basata sui certificati immettono il nome utente e quindi toccano il collegamento "Sign in with a certificate" (Accedi con un certificato). L'autenticazione basata sui certificati è già supportata nelle app del portale aziendale per Android e Windows. Altre informazioni sono disponibili nella pagina di [accesso all'app del portale aziendale](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal).

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>Le app disponibili con o senza registrazione possono essere ora installate senza richiesta di registrazione. <!-- 1334712 -->

Le app aziendali rese disponibili con o senza registrazione nell'app Portale aziendale Android possono essere ora installate senza richiesta di registrazione.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617---"></a>Supporto del programma Windows AutoPilot Deployment in Microsoft Intune  <!-- 747617  -->
Ora è possibile usare Microsoft Intune con il programma AutoPilot Deployment di Windows per consentire agli utenti di attivare e gestire i dispositivi aziendali senza interventi del personale IT. È possibile personalizzare la Configurazione guidata con informazioni che consentono agli utenti di aggiungere il dispositivo ad Azure AD e di registrarlo in Intune. Microsoft Intune e AutoPilot di Windows eseguiti insieme eliminano la necessità di distribuire, gestire e aggiornare le immagini del sistema operativo. Per informazioni dettagliate, vedere [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot) (Registrare dispositivi Windows con il programma AutoPilot Deployment).

### <a name="quick-start-for-device-enrollment----1425655---"></a>Avvio rapido per la registrazione del dispositivo  <!-- 1425655 --> 
In **Registrazione del dispositivo** ora è disponibile una sezione di avvio rapido che include una tabella di riferimenti per la gestione delle piattaforme e la configurazione del processo di registrazione. L'esecuzione delle fasi iniziali della registrazione è facilitata mediante una breve descrizione di ciascun elemento e collegamenti ad argomenti di documentazione con procedure dettagliate.

### <a name="device-categorization----1427491---"></a>Categorizzazione dei dispositivi <!-- 1427491 -->
Il grafico della piattaforma dei dispositivi registrati nella scheda **Dispositivi > Panoramica** organizza i dispositivi per piattaforma e include Android, iOS, macOS, Windows e Windows Mobile.  I dispositivi che eseguono altri sistemi operativi vengono inclusi in "Altro".  Questa categoria include i dispositivi prodotti da Blackberry, NOKIA e altri produttori.  

Per informazioni sui dispositivi interessati nel tenant, scegliere **Gestisci > Tutti i dispositivi** e quindi usare **Filtra** per limitare il campo **Sistema operativo**.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium: nuovo partner di Mobile Threat Defense   <!-- 954681 -->  
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi condotta da Zimperium, una soluzione Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Zimperium. È possibile configurare criteri di accesso condizionale EMS in base alla valutazione dei rischi di Zimperium abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10  <!--- 978575, 1308849, -->  
Sono state aggiunte nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 nella categoria Windows Defender SmartScreen.

Per informazioni dettagliate sul profilo di restrizione dei dispositivi Windows 10, vedere [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Supporto remoto per dispositivi Windows e Windows Mobile  <!-- 1070473 -->  
Intune ora supporta l'uso del software [TeamViewer](https://www.teamviewer.com), acquistabile separatamente, per l'assistenza remota agli utenti con dispositivi Windows e Windows Mobile.

### <a name="scan-devices-with-windows-defender----1280988-1280990---"></a>Analizzare dispositivi con Windows Defender <!-- 1280988  1280990   -->
Ora è possibile eseguire un'**analisi veloce**, un'**analisi completa** e l'**aggiornamento delle firme** con Windows Defender Antivirus nei dispositivi Windows 10 gestiti. Dal pannello della panoramica del dispositivo, scegliere l'azione da eseguire nel dispositivo. Verrà chiesto di confermare l'azione prima che il comando venga inviato al dispositivo. 

**Analisi veloce**: l'analisi veloce analizza i percorsi in cui il malware si registra per l'avvio, ad esempio le chiavi del Registro di sistema e le cartelle di avvio di Windows note. L'analisi veloce richiede in media cinque minuti. Unita all'impostazione della **protezione in tempo reale Always On** che analizza i file quando vengono aperti, chiusi e ogni volta che un utente passa a una cartella, l'analisi veloce consente di fornire protezione da software dannoso che potrebbe trovarsi nel sistema o nel kernel. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Analisi completa**: l'analisi completa può essere utile nei dispositivi in cui sono state riscontrate minacce malware per identificare se sono presenti componenti inattivi che richiedono una pulizia più approfondita ed è utile per l'esecuzione di analisi su richiesta. L'analisi completa può richiedere un'ora. Al termine dell'analisi, gli utenti visualizzano i risultati sui dispositivi. 

**Aggiornare le firme**: il comando di aggiornamento delle firme aggiorna le definizioni e le firme malware di Windows Defender Antivirus, garantendo l'efficacia nel rilevamento di malware. Questa funzionalità è applicabile solo ai dispositivi Windows 10 con connettività Internet. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Il pulsante Abilita/Disabilita viene rimosso dalla pagina Autorità di certificazione nel portale di Intune di Azure  <!-- 1400455 -->
 È stato eliminato un passaggio aggiuntivo nella configurazione del Connettore di certificati di Intune. Attualmente è necessario scaricare il Connettore di certificati e quindi abilitarlo nella console di Intune. Se tuttavia si disattiva il connettore nella console di Intune, questo continua a emettere certificati.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
A partire da ottobre, il pulsante Abilita/Disabilita non viene più visualizzato nella pagina Autorità di certificazione del portale di Azure. La funzionalità del connettore resta invariata. I certificati vengono ancora distribuiti ai dispositivi registrati in Intune. È possibile continuare a scaricare e installare il Connettore di certificati. Per interrompere l'emissione di certificati ora è necessario disinstallare il Connettore di certificati anziché disattivarlo.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Se il Connettore di certificati è disattivato, è necessario disinstallarlo.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team   <!--- 1308838 -->
In questa versione vengono aggiunte molte nuove impostazioni per il profilo di restrizione dei dispositivi di Windows 10 Team per la gestione dei dispositivi Surface Hub.

Per altre informazioni su questo profilo, vedere [Impostazioni relative alle restrizioni dei dispositivi Windows 10 Team](device-restrictions-windows-10-teams.md).

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo  <!-- 1333292 -->
È possibile usare [criteri personalizzati per dispositivi Android](custom-settings-android.md) per impedire agli utenti dei dispositivi Android di modificare la data e ora del dispositivo.

A tale scopo, configurare criteri personalizzati di Android impostando l'URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange su **TRUE** e quindi assegnarli ai gruppi necessari.

### <a name="bitlocker-device-configuration---1397398---"></a>Configurazione di BitLocker per il dispositivo <!-- 1397398 -->
**Crittografia di Windows > Impostazioni di base** include la nuova impostazione **Avviso per la crittografia dischi di altro tipo** che consente di disabilitare il [prompt di avviso](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption) per crittografie dischi di altro tipo eventualmente in uso nel dispositivo dell'utente.  Il prompt di avviso richiede il consenso dell'utente finale prima di configurare BitLocker nel dispositivo e blocca la configurazione di BitLocker fino alla conferma dell'utente finale.  La nuova impostazione disabilita l'avviso per l'utente finale.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Le app Volume Purchase Program per le aziende ora vengono sincronizzate con il tenant Intune <!-- 800882 -->  
Gli sviluppatori di terze parti possono distribuire privatamente le app ai membri del Volume Purchase Program di Apple per le aziende indicati in iTunes Connect. I membri VPP per le aziende possono accedere a Volume Purchase Program App Store e acquistare le app.

A partire dalla versione corrente le app VPP per le aziende acquistate dall'utente finale vengono sincronizzate con il rispettivo tenant Intune.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Selezionare l'Apple Store del paese per la sincronizzazione delle app VPP <!-- 1332311 -->  
È possibile configurare lo Store del paese per il Volume Purchase Program (VPP) quando si carica il token VPP. Intune sincronizza le app VPP per tutte le impostazioni locali dello Store del paese VPP specificato.

> [!NOTE]  
> Attualmente Intune sincronizza solo le app VPP dello Store VPP del paese corrispondenti all'impostazione locale di Intune in cui è stato creato il tenant di Intune.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Bloccare la funzionalità di copia e incolla tra i profili di lavoro e i profili personali in Android for Work <!-- 1098994 -->
Con questa versione è possibile configurare il profilo di lavoro di Android for Work per bloccare l'operazione di copia e incolla tra le app di lavoro e le app personali. Questa nuova impostazione è disponibile nel profilo **Limitazioni del dispositivo** per la piattaforma **Android for Work** in **Impostazioni del profilo di lavoro**.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>Creare app iOS limitate ad Apple App Store di aree specifiche<!-- 1281692 -->
Sarà possibile specificare le impostazioni locali del paese durante la creazione di un'app gestita da Apple App Store.

> [!Note]  
> Attualmente è possibile creare solo app gestite di Apple App Store disponibili nello Store degli Stati Uniti.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>Aggiornare le app VPP iOS concesse in licenza a utenti e dispositivi <!-- 1305564 -->  
Sarà possibile configurare il token VPP iOS per aggiornare tutte le app acquistate per tale token tramite il servizio Intune. Intune rileverà gli aggiornamenti delle app VPP nell'App Store e li invierà automaticamente al dispositivo quando questo si connette.

Per la descrizione dettagliata dell'impostazione di un token VPP e dell'attivazione degli aggiornamenti automatici, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune] (/intune/vpp-app-ios).


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Raccolta di entità di associazione dei dispositivi degli utenti aggiunta al modello di dati di Data Warehouse di Intune<!-- 1187917 -->
Ora è possibile creare report e visualizzazioni di dati usando le informazioni sull'associazione dei dispositivi degli utenti che associano raccolte di entità di utenti e dispositivi. Il modello di dati è accessibile tramite il file di Power BI (PBIX) recuperato dalla pagina Data warehouse di Intune, tramite l'endpoint OData oppure sviluppando un client personalizzato.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Esaminare la conformità ai criteri per gli anelli di aggiornamento di Windows 10 <!-- 1067886 -->
È possibile esaminare un report sui criteri per gli anelli di aggiornamento di Windows 10 in Aggiornamenti software > Stato di distribuzione per ogni anello di aggiornamento. Il report sui criteri include lo stato di distribuzione degli anelli di aggiornamento configurati. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions----1352223---"></a>Nuovo report che elenca i dispositivi iOS con versioni precedenti di iOS   <!-- 1352223 -->
Il report **Dispositivi iOS non aggiornati** è disponibile nell'area di lavoro **Aggiornamenti software**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento di iOS e con aggiornamenti disponibili. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>Visualizzare le assegnazioni dei criteri di protezione delle app per la risoluzione dei problemi <!--  1475003 -->
In questa versione futura verrà aggiunta un'opzione per i **criteri di protezione delle app** all'elenco a discesa **Assegnazioni** disponibile nel pannello della risoluzione dei problemi. Sarà ora possibile selezionare Criteri di protezione delle app per visualizzare i criteri assegnati agli utenti selezionati.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Miglioramenti del flusso di lavoro di installazione dei dispositivi nel Portale aziendale <!--1490692-->
È stato migliorato il flusso di lavoro di installazione dei dispositivi nell'app Portale aziendale per Android. Il linguaggio è più semplice e specifico per l'azienda e sono state inserite schermate dove possibile. È possibile visualizzare i miglioramenti nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md#week-of-october-2-2017).

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Miglioramento delle linee guida per la richiesta di accesso ai contatti nei dispositivi Android <!--1484985-->

L'app Portale aziendale per Android richiede spesso all'utente finale di accettare l'autorizzazione per i contatti. Se un utente finale rifiuta l'accesso, ora viene visualizzata una notifica in-app che avvisa dell'autorizzazione per l'accesso condizionale. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Correzione dell'avvio sicuro per Android <!--1490712-->

Gli utenti finali con dispositivi Android potranno selezionare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Notifiche push aggiuntive per gli utenti finali dell'app Portale aziendale per Android Oreo <!--1475932-->

Gli utenti visualizzeranno notifiche aggiuntive che indicano quando l'app Portale aziendale per Android Oreo sta eseguendo attività in background, ad esempio il recupero di criteri dal servizio Intune. Questa funzionalità aumenta la trasparenza per gli utenti finali, che sapranno quando sono in corso attività amministrative del Portale aziendale nei loro dispositivi, È uno degli aspetti dell'intera [ottimizzazione dell'interfaccia utente del portale aziendale](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) per l'app Portale aziendale per Android Oreo. 

Sono disponibili altre ottimizzazioni per i nuovi elementi dell'interfaccia utente che sono abilitate in Android Oreo.  Gli utenti finali visualizzeranno notifiche aggiuntive che indicheranno loro quando l'app Portale aziendale sta eseguendo attività in background, ad esempio il recupero di criteri dal servizio di Intune.  In questo modo per gli utenti finali sarà più chiaro quando l'app Portale aziendale sta eseguendo attività amministrative nel dispositivo.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuovi comportamenti dell'app del portale aziendale per Android con i profili di lavoro <!-- 1485783 -->

Quando si registra un dispositivo Android for Work con un profilo di lavoro, è l'app del portale aziendale nel profilo di lavoro a eseguire attività di gestione nel dispositivo. 

A meno che non si usi un'app abilitata per MAM nel profilo personale, l'app del portale aziendale per Android non è più utile. Per migliorare l'esperienza con i profili di lavoro, Intune nasconderà automaticamente l'app del portale aziendale personale dopo la registrazione del profilo di lavoro.

L'app del portale aziendale per Android può essere abilitata in qualsiasi momento nel profilo personale passando al [portale aziendale in Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e selezionando **Abilita**.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Passaggio del portale aziendale per Windows 8.1 e Windows Phone 8.1 alla modalità di mantenimento <!--1428681-->

A partire da ottobre 2017, le app del portale aziendale per Windows 8.1 e Windows Phone 8.1 passeranno alla modalità di mantenimento. Le app e gli scenari esistenti, ad esempio la registrazione e la conformità, continueranno a essere supportati per queste piattaforme. Queste app rimarranno disponibili per il download tramite i canali di rilascio esistenti, ad esempio Microsoft Store. 

Nella modalità di mantenimento, queste app ricevono solo aggiornamenti della sicurezza critici. Non verranno rilasciati altri aggiornamenti o funzionalità per queste app. Per le nuove funzionalità è consigliabile aggiornare i dispositivi a Windows 10 o Windows 10 Mobile. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>Bloccare la registrazione di dispositivi Samsung Knox non supportati  <!-- 1490695 -->

L'app Portale aziendale tenta di registrare solo i dispositivi Samsung Knox supportati. Per evitare errori di attivazione Knox che impediscono la registrazione MDM, la registrazione del dispositivo viene eseguita solo se il dispositivo viene visualizzato nell'[elenco di dispositivi pubblicato da Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). I dispositivi Samsung possono avere numeri di modello che supportano Knox oppure no. Verificare la compatibilità Knox con il rivenditore del dispositivo prima dell'acquisto e della distribuzione. È possibile trovare l'elenco completo dei dispositivi verificati nelle [impostazioni dei criteri Android e Samsung Knox Standard](/intune/supported-devices-browsers.md#intune-supported-web-browsers).

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Fine del supporto per Android 4.3 e versioni precedenti <!-- 1171126, 1326920 -->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate nei dispositivi registrati <!--1165314-->
Verrà aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo in tutte le app Portale aziendale. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente dall'articolo [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Questa opzione verrà presto implementata in tutte le app Portale aziendale. Per iOS, l'annuncio è stato fatto a [settembre](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017).

## <a name="september-2017"></a>Settembre 2017

### <a name="intune-supports-ios-11---1428975--"></a>Intune supporta iOS 11 <!--1428975-->
Intune supporta iOS 11. Annuncio precedentemente fatto nel [blog del supporto tecnico di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fine del supporto per iOS 8.0 <!-- 1164477 -->
Le app gestite e l'app Portale aziendale per iOS richiederanno iOS 9.0 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati entro settembre non potranno accedere al Portale aziendale o a tali app. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Azione di aggiornamento aggiunta all'app del portale aziendale per Windows 10 <!--1132468-->
L'app Portale aziendale per Windows 10 consente agli utenti di aggiornare i dati nell'app trascinando verso il basso per aggiornare o, nei desktop, premendo F5.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate per iOS<!--739894-->

È stata aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo nell'app Portale aziendale per iOS. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente da questa pagina dalla documentazione di Intune per gli utenti finali. Potranno accedere a queste informazioni anche nella schermata Informazioni su.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Consentire agli utenti di accedere all'app Portale aziendale per Android senza registrazione <!---1169910--->

Gli utenti finali potranno presto non avere l'obbligo di registrare il dispositivo per accedere all'app Portale aziendale per Android. Agli utenti finali di organizzazioni che usano criteri di protezione delle app non verrà più richiesto di registrare il dispositivo quando aprono l'app Portale aziendale. Gli utenti finali potranno anche installare app dal Portale aziendale senza registrare il dispositivo. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Testo più comprensibile per l'app Portale aziendale per Android <!---1396349--->  

Il processo di registrazione per l'app del portale aziendale per Android è ora più semplice per gli utenti finali, grazie all'uso di un nuovo testo più comprensibile. Se si usa una documentazione personalizzata per la registrazione, è consigliabile aggiornarla sulla base delle nuove schermate. È possibile trovare immagini di esempio nella pagina [Aggiornamenti dell'interfaccia utente per le app degli utenti finali in Intune](whats-new-app-ui.md#week-of-september-11-2017).

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>App del portale aziendale di Windows 10 aggiunta ai criteri per il consenso di Windows Information Protection<!-- 677129 -->

L'app Portale aziendale di Windows 10 è stata aggiornata per supportare Windows Information Protection (WIP). L'app può essere aggiunta ai criteri Consenti di WIP. Con questa modifica non è più necessario aggiungere l'app all'elenco **Esente**.


## <a name="august-2017"></a>Agosto 2017

### <a name="improvements-to-device-overview----1404453---"></a>Miglioramenti alla panoramica del dispositivo <!-- 1404453 -->  
In seguito ai miglioramenti, la panoramica del dispositivo ora visualizza i dispositivi registrati ma esclude i dispositivi gestiti da Exchange ActiveSync. I dispositivi Exchange ActiveSync non hanno le stesse opzioni di gestione dei dispositivi registrati. Per visualizzare il numero di dispositivi registrati e il numero di dispositivi registrati per piattaforma in Intune nel portale di Azure, scegliere **Dispositivi** > **Panoramica**.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Miglioramenti dell'inventario dei dispositivi gestito da Intune
<!-- 961134, 1104426, 1281327, 1333543 --> In questa versione sono stati apportati i miglioramenti seguenti alle informazioni di inventario raccolte dai dispositivi gestiti dall'utente:
 
-   Per i dispositivi Android ora è possibile aggiungere all'inventario dei dispositivi una colonna che mostra il livello di patch più recente per ogni dispositivo. Aggiungere la colonna **Security patch level** (Livello patch di protezione) all'elenco di dispositivi per visualizzare il risultato.
-   Quando si applica un filtro alla visualizzazione dei dispositivi ora è possibile filtrare i dispositivi per data di registrazione. Ad esempio, è possibile visualizzare solo i dispositivi registrati dopo una data specificata.
-   Sono stati apportati miglioramenti al filtro usato per l'elemento **Last Check-in Date** (Data ultima archiviazione).
-   Nell'elenco dei dispositivi ora è possibile visualizzare il numero di telefono dei dispositivi di proprietà dell'azienda.
È inoltre possibile usare il riquadro del filtro per cercare i dispositivi in base al numero di telefono.

Per altri dettagli sull'inventario dei dispositivi, vedere [Come visualizzare l'inventario dei dispositivi di Intune](device-inventory.md).

### <a name="conditional-access-support-for-macos-devices"></a>Supporto dell'accesso condizionale per dispositivi macOS 
<!-- 720172 --> Ora è possibile impostare un criterio di accesso condizionale che richiede che i dispositivi Mac vengano registrati in Intune e siano conformi ai relativi criteri di conformità dei dispositivi. Ad esempio, gli utenti possono scaricare l'app Portale aziendale Intune per macOS e registrare i propri dispositivi Mac in Intune. Intune valuta se il dispositivo Mac è conforme a requisiti come PIN, crittografia, versione del sistema operativo e integrità del sistema.

- Altre informazioni sul [supporto dell'accesso condizionale per dispositivi macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>L'app Portale aziendale per macOS è disponibile in anteprima pubblica <!---1484796--->
L'app Portale aziendale per macOS è ora disponibile come parte dell'anteprima pubblica dell'accesso condizionale in Enterprise Mobility + Security. Questa versione supporta macOS 10.11 e versioni successive. È disponibile in [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


### <a name="new-device-restriction-settings-for-windows-10"></a>Nuove impostazioni per le restrizioni dei dispositivi per Windows 10    
<!--1063965, 1308850  --> In questa versione sono state aggiunte nuove impostazioni per il [profilo di restrizione dei dispositivi Windows 10](/intune/device-restrictions-windows-10) nelle categorie seguenti:

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Aggiornamenti delle impostazioni del profilo dispositivo Endpoint Protection di Windows 10 per BitLocker
<!--1459533 -->     In questa versione sono stati apportati i miglioramenti seguenti al funzionamento delle impostazioni di BitLocker in un profilo di dispositivo Endpoint Protection di Windows 10:
 
-   In **Impostazioni dell'unità del sistema operativo BitLocker** per l'impostazione **BitLocker con chip TPM non compatibile**, quando in precedenza si selezionava **Blocca** in realtà BitLocker veniva autorizzato. Questo problema è stato risolto e ora quando si seleziona questa opzione BitLocker viene bloccato.
-   In **Impostazioni dell'unità del sistema operativo BitLocker**, per l'impostazione **Agente di recupero dati basato su certificati** ora è possibile bloccare in modo esplicito l'agente di recupero dati basato su certificati. Per impostazione predefinita l'agente è consentito.
-   In **Impostazioni delle unità dati fisse BitLocker**, per l'impostazione **Agente di recupero dati** ora è possibile bloccare in modo esplicito l'agente di recupero dati.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive).


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nuova esperienza di accesso per gli utenti dell'app Portale aziendale per Android e gli utenti dei criteri di protezione delle app <!-- 621669 -->
Gli utenti finali possono ora visualizzare le app, gestire i dispositivi e accedere a informazioni sui contatti IT tramite l'app Portale aziendale Android senza registrare i dispositivi Android personali. Inoltre, se un utente finale usa già un'app protetta tramite i criteri di protezione app di Intune e avvia l'app Portale aziendale per Android, l'utente finale non riceve più la richiesta di registrare il dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nuova impostazione nell'app Portale aziendale per Android per attivare/disattivare l'ottimizzazione della memoria <!--1405990-->
La pagina **Impostazioni** nell'app Portale aziendale per Android include una nuova impostazione che consente agli utenti di disattivare facilmente l'ottimizzazione della batteria per le app Portale aziendale e Microsoft Authenticator. Il nome dell'app visualizzato nell'impostazione varia a seconda dell'app usata per gestire l'account aziendale. È consigliabile che gli utenti disattivino l'ottimizzazione della batteria per migliorare le prestazioni delle app aziendali che sincronizzano posta elettronica e dati. 

### <a name="multi-identity-support-for-onenote-for-ios----1234281---"></a>Supporto di più identità per OneNote per iOS      <!-- 1234281 -->
Ora gli utenti finali possono usare account diversi (aziendali e personali) con Microsoft OneNote per iOS. I criteri di protezione app possono essere applicati ai dati aziendali nei notebook di lavoro senza influire sul notebook personale dell'utente. Ad esempio un criterio può consentire a un utente di trovare informazioni nei notebook aziendali, ma impedirà all'utente di copiare e incollare dati aziendali dal notebook aziendale a un notebook personale.
 
- Altre informazioni sulle app che supportano la [protezione delle app e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nuove impostazioni per consentire e bloccare app nei dispositivi Samsung Knox Standard
<!-- 1305423 822899-->  
In questa versione vengono aggiunte nuove [impostazioni di restrizione dei dispositivi](device-restrictions-android.md) che consentono di specificare gli elenchi di app seguenti:
 
- App che gli utenti sono autorizzati a installare
- App che gli utenti non possono eseguire
- App che sono nascoste all'utente nel dispositivo  
È possibile specificare l'app in base all'URL, al nome del pacchetto o dall'elenco di app che si gestiscono.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nuovo collegamento da Intune all'interfaccia utente per i criteri di accesso condizionale basati su app di Azure AD
<!-- 1016201 --> Ora gli amministratori IT possono impostare criteri condizionali basati su app tramite la nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Azure AD. Per ora l'accesso condizionale basato su app disponibile nella sezione Protezione app di Intune del portale Azure resta in tale posizione e viene applicato in affiancamento. Per comodità è anche disponibile un collegamento alla nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Intune.

- Altre informazioni sull'[accesso condizionale basato su app in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).



## <a name="july-2017"></a>Luglio 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256-1245463----"></a>Restrizione della registrazione dei dispositivi Android e iOS in base alla versione del sistema operativo  <!--- 1333256,  1245463 --->
Intune ora supporta la restrizione della registrazione di Android e iOS in base al numero di versione del sistema operativo. In **Restrizione dei tipi di dispositivo** l'amministratore IT può ora impostare una configurazione della piattaforma per limitare la registrazione tra un valore minimo e massimo del sistema operativo. Le versioni del sistema operativo Android devono essere specificate come Principale.Secondaria.Build.Rev, dove Secondaria, Build e Rev sono facoltativi. Le versioni di iOS devono essere specificate come Principale.Secondaria.Build, dove Build è facoltativa. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

>[!NOTE]
>Non limitare la registrazione tramite i programmi DEP Apple o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272-1333275-1245709---"></a>Limitare la registrazione dei dispositivi personali Android, iOS e macOS  <!--- 1333272,  1333275, 1245709 --->
Intune può limitare la registrazione dei dispositivi personali creando un elenco dei dispositivi aziendali consentiti con i relativi numeri IMEI. Intune ha ora esteso questa funzionalità a iOS, Android e macOS usando i numeri di serie del dispositivo. Caricando i numeri di serie in Intune, è possibile predichiarare i dispositivi come proprietà dell'azienda. Usando le restrizioni della registrazione, è possibile bloccare i dispositivi personali (BYOD, Bring Your Own Device), consentendo la registrazione solo per i dispositivi di proprietà dell'azienda. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

Per importare i numeri di serie, passare a **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**, fare clic su **Aggiungi** e quindi caricare un file con estensione csv senza intestazione ma con due colonne per il numero di serie e i dettagli come i numeri IMEI. Per limitare i dispositivi personali, accedere a **Registrazione del dispositivo** > **Restrizioni registrazione**. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinita** e **Configurazioni della piattaforma**. È possibile scegliere **Consenti** o **Blocca** per i dispositivi personali per iOS, Android e macOS.


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nuova azione del dispositivo per forzare la sincronizzazione con Intune <!-- 711369 -->
In questa versione è stata aggiunta una nuova azione del dispositivo che forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.
Per informazioni dettagliate, vedere [Sincronizzare il dispositivo](device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzare i dispositivi iOS supervisionati per installare automaticamente l'aggiornamento software più recente disponibile <!-- 777100 -->
È disponibile un nuovo criterio dall'area di lavoro degli aggiornamenti software, che consente di forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione. Per informazioni dettagliate, vedere [Configurare i criteri di aggiornamento per iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile: nuovo partner di Mobile Threat Defense  <!-- 954651, 1172027 -->
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Checkpoint SandBlast Mobile, una soluzione di Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Checkpoint SandBlast Mobile. È possibile configurare criteri di accesso condizionale EMS basati sulla valutazione dei rischi di Checkpoint SandBlast Mobile e abilitati tramite i criteri di conformità dei dispositivi di Intune. È possibile consentire o bloccare l'accesso alle risorse aziendali ai dispositivi non conformi in base alle minacce rilevate.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Distribuire un'app come disponibile in Microsoft Store per le aziende <!-- 748101 -->
Con questa versione, gli amministratori possono ora assegnare Microsoft Store per le aziende come disponibile. Con questa impostazione, gli utenti finali possono installare l'app dall'app Portale aziendale o dal sito Web del portale aziendale senza essere reindirizzati a Microsoft Store.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Aggiornamenti dell'interfaccia utente del sito Web del portale aziendale <!--1313244 part 1-->
Sono stati introdotti vari aggiornamento all'interfaccia utente del [sito Web portale aziendale](https://portal.manage.microsoft.com) per migliorare l'esperienza per gli utenti finali.

- __Miglioramenti per i riquadri delle app__: le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente in base al colore dominante dell'icona, se rilevabile. Se applicabile, questo sfondo sostituisce il bordo grigio precedentemente visibile nei riquadri delle app.

    In una versione futura è previsto che il sito Web del portale aziendale visualizzi le icone grandi ogniqualvolta possibile. È consigliabile che gli amministratori IT pubblichino app con icone ad alta risoluzione di dimensioni minime pari a 120x120 pixel. 

- __Modifiche alla struttura di spostamento__: gli elementi della barra di spostamento sono stati spostati nel menu hamburger in alto a sinistra. La pagina delle categorie è stata rimossa. Gli utenti possono ora filtrare il contenuto in base alla categoria durante l'esplorazione.

- __Aggiornamenti per le app in primo piano__: è stata aggiunta una pagina dedicata nel sito, nella quale gli utenti possono visualizzare le app che hanno scelto di mettere in primo piano e sono state apportate alcune modifiche all'interfaccia utente della sezione In primo piano nella home page.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Supporto di iBooks per il sito Web del portale aziendale <!--1231841-->
È stata aggiunta una pagina dedicata al sito Web del portale aziendale che consente agli utenti di visualizzare e scaricare iBooks. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>Dettagli aggiuntivi per la risoluzione dei problemi dell'help desk <!---  Applies to 1263399, 1326964, 1341642 --->
Intune ha aggiornato la visualizzazione della risoluzione dei problemi e aggiunto le informazioni che fornisce agli amministratori e al personale dell'help desk. È ora disponibile una tabella **Assegnazioni** che fornisce un riepilogo di tutte le assegnazioni dell'utente in base all'appartenenza a gruppi. L'elenco include:
- App per dispositivi mobili
- Criteri di conformità
- Profili di configurazione

Inoltre, la tabella **Dispositivi** ora include le colonne **Tipo di join per Azure AD** e **Conforme con Azure AD**. Per altre informazioni, vedere [Aiutare gli utenti nella risoluzione dei problemi](help-desk-operators.md).



### <a name="intune-data-warehouse-public-preview"></a>Data warehouse di Intune (anteprima pubblica)
Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologica dell'ambiente. È possibile accedere ai dati tramite un file di Power BI (PBIX), un collegamento OData compatibile con molti strumenti di analisi oppure interagendo con l'API REST. Per altre informazioni, vedere [Usare il data warehouse di Intune](reports-nav-create-intune-reports.md).


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modalità chiara e modalità scura disponibili per l'app Portale aziendale per Windows 10 <!---676547--->
Gli utenti finali potranno personalizzare la modalità di colore per l'app Portale aziendale per Windows 10. L'utente potrà apportare la modifica nella sezione delle impostazioni dell'app Portale aziendale. La modifica verrà visualizzata dopo che l'utente avrà riavviato l'app. Per Windows 10 versione 1607 e successive, la modalità dell'app predefinita sarà l'impostazione di sistema. Per Windows 10 versione 1511 e precedenti, la modalità dell'app predefinita sarà la modalità chiara.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Consentire agli utenti finali di contrassegnare il gruppo di dispositivi nell'app Portale aziendale per Windows 10 <!---807046-->
Gli utenti finali possono ora selezionare il gruppo a cui appartiene il dispositivo contrassegnandolo direttamente dall'app Portale aziendale per Windows 10.



## <a name="june-2017"></a>Giugno 2017

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Nuovo accesso di amministrazione basato su ruoli per gli amministratori di Intune  <!-- 1099990 -->  
È stato aggiunto un nuovo ruolo di amministrazione dell'accesso condizionale per visualizzare, creare, modificare ed eliminare i criteri di accesso condizionale di Azure AD. In precedenza, solo gli amministratori globali e gli amministratori della sicurezza disponevano di questa autorizzazione. È possibile concedere l'autorizzazione di questo ruolo agli amministratori di Intune, in modo che possano accedere ai criteri di accesso condizionale.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>Contrassegno dei dispositivi di proprietà dell'azienda con i numeri di serie <!-- 1215070 -->  
Intune supporta ora il caricamento di numeri di serie iOS, macOS e Android come identificatori dei dispositivi aziendali. Attualmente non è possibile usare i numeri di serie per bloccare la registrazione dei dispositivi personali, perché i numeri di serie non vengono verificati durante la registrazione. La funzionalità di blocco dei dispositivi personali in base al numero di serie sarà disponibile a breve.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>Nuove azioni remote per i dispositivi iOS <!-- 854689 -->
In questa versione sono state aggiunte due nuove azioni remote dei dispositivi per i dispositivi iPad condivisi che gestiscono l'app Classroom Apple:

-   [Disconnetti l'utente corrente](device-logout-user.md): disconnette l'utente corrente di un dispositivo iOS selezionato.
-   [Rimuovi utente](device-remove-user.md): elimina un utente selezionato dalla cache locale di un dispositivo iOS.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>Supporto per gli iPad condivisi con l'app Classroom iOS <!-- 1044681 -->
In questa versione è stato esteso il supporto per la gestione dell'app Classroom per iOS per includere gli studenti che accedono agli iPad condivisi usando il proprio ID Apple gestito.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Modifiche alle app Intune predefinite <!-- 1332306 -->
Intune conteneva in precedenza un numero di app predefinite che era possibile assegnare rapidamente. In base ai commenti e suggerimenti ricevuti, abbiamo rimosso l'elenco e le app predefinite non verranno più visualizzate.
Tuttavia, se sono già state assegnate app predefinite, le app assegnate saranno ancora visibili nell'elenco delle app. È possibile continuare ad assegnare queste app in base alle proprie esigenze.
In una versione successiva si prevede di aggiungere un metodo più semplice per la selezione e l'assegnazione delle app predefinite dal portale di Azure.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Installazione più semplice delle app di Office 365 <!--- 1121362 --->
Un nuovo tipo di applicazioni **Office 365 ProPlus** semplifica l'assegnazione delle app Office 365 ProPlus 2016 ai dispositivi gestiti che eseguono la versione più recente di Windows 10. È anche possibile installare Microsoft Project e Microsoft Visio, se si hanno le relative licenze. Le app desiderate vengono unite in bundle e visualizzate come un'unica app nell'elenco di app della console di Intune.
Per altre informazioni, vedere [How to add Office 365 apps for Windows 10](apps-add-office365.md) (Come aggiungere app di Office 365 per Windows 10).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Supporto per le app offline da Microsoft Store per le aziende <!--- 777044 --->
Le app offline acquistate da Microsoft Store per le aziende verranno ora sincronizzate nel portale di Azure. È possibile quindi distribuire tali app a gruppi di dispositivi o di utenti. Le app offline vengono installate da Intune, non dallo Store.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>L'app Microsoft Teams è ora inclusa nell'elenco CA basato su app delle app approvate   <!-- 1257019 -->
L'app Microsoft Teams per iOS e Android fa ora parte delle app approvate per i criteri di accesso condizionale basati su app per Exchange e SharePoint Online. L'app può essere configurata tramite il pannello Protezione app di Intune nel portale di Azure di tutti i tenant che usano attualmente l'accesso condizionale basato su app.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Integrazione di Managed Browser e del proxy di applicazione <!-- 1287310 -->
Intune Managed Browser può essere ora integrato con il servizio proxy di applicazione di Azure AD per consentire agli utenti di accedere ai siti Web interni, anche quando lavorano in remoto. Gli utenti del browser immettono l'URL nel modo consueto e Managed Browser instrada la richiesta attraverso il gateway Web del proxy di applicazione. Per altre informazioni, vedere [Manage Internet access using Managed browser policies](app-configuration-managed-browser.md) (Gestire l'accesso a Internet usando i criteri di Managed Browser).

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Nuove impostazioni di configurazione dell'app per Intune Managed Browser<!-- 682951 -->
In questa versione sono state aggiunte altre configurazioni per l'app Intune Managed Browser per iOS e Android. È possibile ora usare i criteri di configurazione delle app per configurare la home page predefinita e i segnalibri del browser.
Per altre informazioni, vedere [Manage Internet access using managed browser policies](app-configuration-managed-browser.md) (Gestire l'accesso a Internet usando i criteri di Managed Browser).

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Impostazioni BitLocker per Windows 10  <!-- 951707 -->
È ora possibile configurare le impostazioni BitLocker per i dispositivi Windows 10 con un nuovo profilo di dispositivo di Intune. Ad esempio, è possibile richiedere che i dispositivi vengano crittografati e anche configurare altre impostazioni che vengono applicate quando BitLocker è attivato.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive).

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
In questa versione sono stati aggiunte nuove impostazioni per il profilo di restrizione del dispositivo Windows 10, nelle categorie seguenti:

-  Windows Defender
-  Rete cellulare e connettività
-  Esperienza della schermata bloccata
-  Privacy
-  Cerca
-  Contenuti in evidenza di Windows
-  Browser Microsoft Edge

Per altre informazioni sulle impostazioni di Windows 10, vedere [Windows 10 and later device restriction settings](device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>L'app Portale aziendale per Android ora include una nuova esperienza utente finale per i criteri di protezione delle app <!--1305217-->
In base ai suggerimenti dei clienti, l'app Portale aziendale per Android è stata modificata e ora include un pulsante **Accesso al contenuto aziendale**. Lo scopo è impedire che gli utenti finali eseguano inutilmente il processo di registrazione quando hanno solo necessità di accedere alle app che supportano i criteri di protezione delle app, una funzionalità di gestione delle applicazioni mobili di Intune. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nuova azione di menu per rimuovere facilmente Portale aziendale <!--1164569-->
In risposta al feedback degli utenti, per l'app Portale aziendale per Android è stata aggiunta una nuova azione di menu per eseguire la rimozione di Portale aziendale dal dispositivo. Questa azione rimuove il dispositivo dalla gestione di Intune in modo che l'utente possa rimuovere l'app dal dispositivo. È possibile visualizzare queste modifiche nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md) e nella [documentazione per gli utenti finali di Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Miglioramenti alla sincronizzazione di app con Windows 10 Creators Update <!--676505-->
L'app Portale aziendale per Windows 10 avvierà ora automaticamente una sincronizzazione per le richieste di installazione di app per dispositivi con Windows 10 Creators Update (1703). Ciò consente di limitare il problema di installazione di app quando lo stato è "In attesa di sincronizzazione". Inoltre, gli utenti saranno in grado di avviare manualmente la sincronizzazione all'interno dell'app. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nuova esperienza guidata per il portale aziendale di Windows 10 <!---1058938--->
L'app Portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate che guidano l'utente nella procedura di registrazione in Azure Active Directory (obbligatoria per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale. Gli utenti possono continuare a usare l'app se non completano la registrazione, ma le funzionalità saranno limitate.

Questo aggiornamento è visibile solo nei dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 (build 1607) o versioni successive. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Disponibilità generale delle console di amministrazione di Microsoft Intune e dell'accesso condizionale
Questo è l'annuncio della disponibilità generale sia della nuova console di amministrazione di Intune nel portale di Azure che della nuova console di amministrazione dell'accesso condizionale. Con Intune nel portale di Azure è ora possibile gestire tutte le funzionalità MAM e MDM di Intune con un'esperienza di amministrazione consolidata, sfruttando allo stesso tempo le funzioni di raggruppamento e targeting di Azure AD. L'accesso condizionale in Azure offre funzionalità avanzate per Azure AD e Intune in un'unica console unificata. Per quanto riguarda l'esperienza di amministrazione, inoltre, il passaggio alla piattaforma Azure consente di usare browser moderni.

Intune è ora visibile senza l'etichetta di **anteprima** nel portale di Azure all'indirizzo portal.azure.com.

Al momento non è richiesto alcun intervento da parte dei clienti esistenti, a meno che non si riceva uno di una serie di messaggi nel centro messaggi che richiede di intervenire in modo da consentire a Microsoft di eseguire la migrazione dei gruppi. È anche possibile che si riceva una notifica nel centro messaggi che informa che la migrazione richiede più tempo a causa di errori di Microsoft. Stiamo continuando a lavorare con impegno per completare la migrazione di tutti i clienti interessati.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Miglioramenti dei riquadri dell'app Portale aziendale per iOS
È stata aggiornata la progettazione dei riquadri dell'app nella home page in modo che rispecchino il colore personalizzato impostato per Portale aziendale. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Selezione account ora disponibile per l'app Portale aziendale per iOS
Gli utenti di dispositivi iOS potrebbero ora visualizzare la nuova selezione account quando accedono al Portale aziendale se usano l'account aziendale o dell'istituto di istruzione per accedere ad altre app Microsoft. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

## <a name="may-2017"></a>Maggio 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Modifica dell'autorità MDM senza annullare la registrazione dei dispositivi gestiti <!--1103950-->
È ora possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Nella console di Configuration Manager è possibile [modificare l'autorità MDM](/sccm/mdm/deploy-use/change-mdm-authority) da Imposta su Configuration Manager (ibrida) a Microsoft Intune (autonoma) o viceversa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notifica migliorata per i PIN di avvio Samsung Knox <!--1087143-->
Quando gli utenti finali devono impostare un PIN di avvio su dispositivi Samsung Knox per garantire la conformità alla crittografia, toccando la notifica visualizzata, gli utenti finali verranno indirizzati alla posizione esatta nell'app Impostazioni.  In precedenza, la notifica rimandava gli utenti finali alla schermata di modifica della password.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>Supporto di Apple School Manager (ASM) con iPad condiviso <!-- 748864, 770395-->

Intune supporta ora l'uso di Apple School Manager (ASM) al posto di Apple Device Enrollment Program per fornire funzionalità di registrazione pronte all'uso per i dispositivi iOS. L'onboarding di ASM è necessario usare l'app Classroom per iPad condivisi e per consentire la sincronizzazione dei dati da ASM ad Azure Active Directory tramite Microsoft School Data Sync (SDS). Per altre informazioni, vedere [Abilitare la registrazione di dispositivi iOS con Apple School Manager](apple-school-manager-set-up-ios.md).

> [!NOTE]
> La configurazione di iPad condivisi per l'uso dell'app Classroom richiede configurazioni di iOS Education in Azure non ancora disponibili.  Questa funzionalità verrà aggiunta presto.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>Fornire assistenza remota ai dispositivi Android con TeamViewer <!-- 675418 -->

Intune può ora usare il software [TeamViewer](https://www.teamviewer.com), acquistato separatamente, per consentire agli amministratori di offrire assistenza remota agli utenti che eseguono dispositivi Android. Per altre informazioni, vedere [Fornire assistenza remota per i dispositivi Android gestiti da Intune](device-profile-android-teamviewer.md).

### <a name="app-management"></a>Gestione delle app

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>Nuove condizioni dei criteri di protezione delle app per MAM <!-- 679864 -->

È ora possibile impostare un requisito per MAM senza registrare gli utenti, che consente di applicare i criteri seguenti:

- Versione minima dell'applicazione
- Versione minima del sistema operativo
- Versione minima di Intune App SDK per l'applicazione di destinazione (solo iOS)

Questa funzionalità è disponibile sia per Android che per iOS. Intune supporta l'imposizione della versione minima per le versioni delle piattaforme del sistema operativo, per le versioni delle applicazioni e per Intune App SDK. In iOS applicazioni con SDK integrato possono anche imporre la versione minima a livello di SDK. L'utente non potrà accedere all'applicazione di destinazione se i requisiti minimi definiti tramite i criteri di protezione delle app non vengono soddisfatti ai tre diversi livelli definiti in precedenza. A questo punto, l'utente può rimuovere l'account (per le applicazioni con identità multiple), chiudere l'applicazione o aggiornare la versione del sistema operativo o dell'applicazione.

È anche possibile configurare impostazioni aggiuntive per fornire una notifica che non causa blocchi per consigliare un aggiornamento del sistema operativo o dell'applicazione. Questa notifica può essere chiusa e l'applicazione può essere usata normalmente.

Per altre informazioni, vedere [Impostazioni dei criteri di protezione delle app per iOS](app-protection-policy-settings-ios.md) e [Impostazioni dei criteri di protezione delle app per Android](app-protection-policy-settings-android.md).

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Configurare le configurazioni delle app per Android for Work <!-- 621621 -->
Alcune app Android dallo store supportano opzioni di configurazione gestite che consentono a un amministratore IT di controllare l'esecuzione di un'app nel profilo di lavoro. Con Intune è ora possibile visualizzare le configurazioni supportate da un'app e definirle dal portale di Azure con una finestra di progettazione della configurazione o un editor JSON. Per altre informazioni, vedere [Usare configurazioni di app per Android for Work](app-configuration-policies-use-android.md).

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>Nuove funzionalità di configurazione delle app per MAM senza registrazione <!-- 677969 -->
È ora possibile creare criteri di configurazione delle app tramite MAM senza canale di registrazione. Questa funzionalità equivale ai criteri di configurazione delle app disponibili per la configurazione delle app di gestione di dispositivi mobili (MDM). Per un esempio di configurazione di app con MAM senza registrazione, vedere [Gestire l'accesso a Internet usando criteri di Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Configurare elenchi di URL consentiti e bloccati per Managed Browser <!-- 682960 -->
È ora possibile configurare un elenco di domini e URL consentiti o bloccati per Managed Browser con le impostazioni di configurazione delle app nel portale di Azure. Queste impostazioni possono essere configurate indipendentemente dal fatto che questa soluzione venga usata in un dispositivo gestito o non gestito. Per altre informazioni, vedere [Gestire l'accesso a Internet usando i criteri di Managed Browser con Microsoft Intune](app-configuration-managed-browser.md).

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>Visualizzazione per il supporto tecnico dei criteri di protezione delle app <!-- 1069473 -->
Gli utenti del supporto tecnico IT possono ora controllare lo stato delle licenze utente e lo stato delle app con criteri di protezione delle app assegnati agli utenti nel pannello Risoluzione dei problemi. Per informazioni dettagliate, vedere [Risoluzione dei problemi](./help-desk-operators.md).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="control-website-visits-on-ios-devices----723832---"></a>Controllare le visite ai siti Web nei dispositivi iOS<!-- 723832 -->
È ora possibile controllare i siti Web che gli utenti di dispositivi iOS possono visitare tramite uno dei due metodi seguenti:

- Aggiungere URL consentiti e bloccati tramite il filtro predefinito dei contenuti Web di Apple.

- Consentire l'accesso dal browser Safari solo ai siti Web specificati. Per ogni sito specificato viene creato il segnalibro corrispondente in Safari.

Per altre informazioni, vedere [Impostazioni di filtraggio del contenuto Web di Intune per i dispositivi iOS](web-content-filter-settings-ios.md).

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Preconfigurazione delle autorizzazioni dei dispositivi per le app Android for Work <!-- 621614 -->
Per le app distribuite in profili di lavoro di dispositivi Android For Work, è ora possibile configurare lo stato delle autorizzazioni per le singole app.  Per impostazione predefinita, le app Android che richiedono autorizzazioni del dispositivo, ad esempio l'accesso alla posizione o alla fotocamera del dispositivo, chiederanno agli utenti di accettare o rifiutare le autorizzazioni.  Se ad esempio un'app usa il microfono del dispositivo, all'utente finale viene chiesto di concedere all'app l'autorizzazione per l'uso del microfono. Questa funzionalità consente di definire le autorizzazioni per conto dell'utente finale.  È possibile configurare le autorizzazioni per a) negare automaticamente senza avvisare l'utente, b) approvare automaticamente senza avvisare l'utente o c) richiedere all'utente di accettare o negare. Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune](device-restrictions-android-for-work.md).

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Definizione del PIN specifico dell'app per i dispositivi Android for Work <!-- 728976, 1102534 -->
I dispositivi Android 7.0 e versioni successive con un profilo di lavoro gestito come dispositivo Android for Work consentono all'amministratore di definire criteri di passcode applicabili solo alle app nel profilo di lavoro.  Le opzioni includono:

- Definire solo criteri di passcode a livello di dispositivo: si tratta del passcode che l'utente deve usare per sbloccare l'intero dispositivo.
- Definire solo criteri di passcode del profilo di lavoro: agli utenti finali viene chiesto di immettere un passcode ogni volta che viene aperta un'app nel profilo di lavoro.
- Definire criteri sia del dispositivo che del profilo di lavoro: l'amministratore IT può scegliere di definire sia criteri di passcode del dispositivo che criteri di passcode del profilo di lavoro con complessità diverse (ad esempio, un PIN di 4 cifre per sbloccare il dispositivo, ma un PIN di 6 cifre per aprire un'app di lavoro).

Per altre informazioni, vedere [Impostazioni delle restrizioni dei dispositivi Android for Work in Microsoft Intune](device-restrictions-android-for-work.md).

> [!NOTE]
> Questa funzionalità è disponibile solo in Android 7.0 e versioni successive.  Per impostazione predefinita, l'utente finale può usare i due PIN definiti separatamente oppure scegliere di combinare i due PIN definiti in quello più complesso.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Nuove impostazioni per i dispositivi Windows 10 <!-- 978585 -->
Sono state aggiunte nuove [impostazioni di restrizione dei dispositivi Windows](device-restrictions-windows-10.md) che controllano funzionalità come schermi wireless, individuazione dei dispositivi, passaggio da un'attività a un'altra e messaggi di errore della scheda SIM.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>Aggiornamenti della configurazione del certificato <!-- 918991 and 823198 -->
Per la creazione di un profilo di certificato SCEP, l'opzione <strong>Personalizzato</strong> per <strong>Formato nome soggetto</strong> è disponibile per i dispositivi iOS, Android e Windows. Prima dell'aggiornamento, il campo <strong>Personalizzato</strong> era disponibile solo per i dispositivi iOS. Per altre informazioni, vedere [Come creare un profilo certificato SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile).

Per la creazione di un profilo di certificato PKCS, è disponibile l'opzione **Custom Azure AD attribute** (Attributo Azure AD personalizzato) per **Nome alternativo soggetto**. È disponibile l'opzione **Reparto** quando si seleziona **Custom Azure AD attribute** (Attributo Azure AD personalizzato). Per altre informazioni, vedere [Creare un profilo certificato SCEP](certficates-pfx-configure.md#create-a-pkcs-certificate-profile).

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Configurare più app che possono essere eseguite quando un dispositivo Android è in modalità tutto schermo<!-- 662059 -->
Quando un dispositivo Android è in modalità tutto schermo, in precedenza era possibile configurare una sola app per consentirne l'esecuzione. È ora possibile configurare più app usando l'ID, l'URL dello store oppure selezionando un'app Android già gestita. Per altre informazioni vedere [Impostazioni della modalità tutto schermo](device-restrictions-android.md#kiosk).



## <a name="april-2017"></a>Aprile 2017

### <a name="support-for-managing-the-apple-classroom-app"></a>Supporto per la gestione dell'app Classroom Apple
È ora possibile gestire l'app Classroom iOS nei dispositivi iPad. Configurare l'app Classroom nell'iPad degli insegnanti con la classe e i dati sugli studenti corretti, quindi configurare gli iPad degli studenti registrati in una classe, in modo da poterli controllare tramite l'app.
Per altri dettagli, vedere [Configurare le impostazioni di iOS relative alla formazione](education-settings-configure-ios.md).

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Supporto per le opzioni di configurazione gestita per le app Android <!-- 621621 -->
Le app Android nel Play Store che supportano le opzioni di configurazione gestita ora possono essere configurate da Intune.  Questa funzionalità consente ai responsabili IT di visualizzare l'elenco dei valori di configurazione supportati da un'app e fornisce un'interfaccia utente guidata avanzata per consentire la configurazione di tali valori.

### <a name="new-android-policy-for-complex-pins----722069---"></a>Nuovi criteri Android per PIN complessi <!-- 722069 -->
È ora possibile impostare una [password](device-restrictions-android.md#password) obbligatoria di tipo Complessa numerica in un profilo di dispositivo Android per i dispositivi che eseguono Android 5.0 e versioni successive.  Usare questa impostazione per impedire agli utenti dei dispositivi di creare un PIN contenente numeri ripetuti o consecutivi, ad esempio 1111 o 1234.

### <a name="additional-support-for-android-for-work-devices"></a>Supporto aggiuntivo per i dispositivi Android for Work
- **Gestire le impostazioni delle password e dei profili di lavoro** <!-- 612808 -->

  Questo nuovo criterio di restrizione dei dispositivi Android for Work ora consente di gestire le impostazioni delle password e dei profili di lavoro nei dispositivi Android for Work gestiti.

- **Consentire la condivisione dei dati tra i profili di lavoro e personali** <!-- 1045102 -->

Questo profilo di restrizione dei dispositivi Android for Work ora offre nuove opzioni che consentono di configurare la condivisione dei dati tra i profili di lavoro e quelli personali.

- **Limitare il copia e incolla tra i profili di lavoro e personali** <!-- 1046094 -->

  Un nuovo profilo di dispositivo personalizzato per i dispositivi Android for Work consente ora di limitare le operazioni di copia e incolla tra app di lavoro e personali.

Per altre informazioni, vedere l'articolo sulle [restrizioni dei dispositivi per Android for Work](device-restrictions-android-for-work.md).

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>Assegnazione di app LOB a dispositivi iOS e Android <!-- 1057568 -->
È ora possibile assegnare a utenti o dispositivi app line-of-business (LOB) per [iOS](lob-apps-ios.md) (file con estensione ipa) e per [Android](lob-apps-android.md) (file con estensione apk).


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>Nuovi criteri dei dispositivi per iOS <!-- 723774, 723815, 723826, 723830 -->
- **App nella schermata iniziale**: stabilisce quali sono le app visualizzate dagli utenti nella [schermata iniziale dei loro dispositivi iOS](home-screen-settings-ios.md). Questo criterio modifica il layout della schermata iniziale ma non distribuisce nessuna app.

- **Connessioni ai dispositivi AirPrint**: specifica i [dispositivi AirPrint](air-print-settings-ios-macos.md) (stampanti di rete) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Connessioni ai dispositivi AirPlay**: specifica i [dispositivi AirPlay](airplay-settings-ios.md) (come Apple TV) a cui possono connettersi gli utenti finali del dispositivo iOS.

- **Messaggio personalizzato della schermata di blocco**: consente di configurare un messaggio personalizzato che gli utenti visualizzeranno nella schermata di blocco del loro dispositivo iOS, in sostituzione del messaggio della schermata di blocco predefinito. Per altre informazioni, vedere [Attivare la modalità di dispositivo perso nei dispositivi iOS](device-lost-mode.md).

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>Limitazione delle notifiche push per le app per iOS <!-- 723767 -->
In un profilo di restrizione del dispositivo di Intune è possibile configurare le [impostazioni di notifica](app-notification-settings-ios.md) seguenti per i dispositivi iOS:

- Attivare o disattivare completamente la notifica per un'app specificata.
- Attivare o disattivare la notifica nel Centro notifiche per un'app specificata.
- Specificare il tipo di avviso, ovvero **Nessuno**, **Banner** o **Modal Alert** (Avviso modale).
- Specificare se sono consentite le notifiche per questa app.
- Specificare se sono consentite le notifiche audio.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>Configurazione delle app per iOS per l'esecuzione in modo autonomo in Modalità applicazione singola <!-- 737837 -->
È possibile usare un profilo di dispositivo di Intune per configurare i dispositivi iOS per l'esecuzione delle applicazioni specificate in [Modalità applicazione singola autonoma](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only). Quando questa modalità è configurata e l'app è in esecuzione, il dispositivo è bloccato in modo che possa eseguire solo quell'app. Un esempio è quando si configura un'app che consente agli utenti di eseguire un test nel dispositivo. Quando le operazioni dell'app sono state completate o si rimuove questo criterio, il dispositivo torna allo stato normale.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>Configurazione di domini trusted per posta elettronica ed esplorazione Web nei dispositivi iOS <!-- 723765 -->
Da un profilo di restrizione del dispositivo iOS è ora possibile configurare le [impostazioni di dominio](device-restrictions-ios.md#domains) seguenti:

- **Domini di posta elettronica non contrassegnati**: i messaggi inviati o ricevuti dall'utente che non corrispondono ai domini specificati qui verranno contrassegnati come non attendibili.

- **Domini Web gestiti**: i documenti scaricati dagli URL specificati qui verranno considerati gestiti (solo Safari).  

- **Domini con riempimento automatico della password di Safari**: gli utenti possono salvare le password in Safari solo dagli URL corrispondenti ai modelli specificati qui. Per usare questa impostazione, il dispositivo deve essere in modalità con supervisione e non deve essere configurato per più utenti (iOS 9.3 e versioni successive).


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>App VPP disponibili nel portale aziendale iOS <!-- 748782 -->
È ora possibile assegnare app per iOS acquistate con Volume Purchase Program (VPP) come installazioni **disponibili** per gli utenti finali. Gli utenti finali avranno bisogno di un account Apple Store per installare l'app.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Sincronizzazione di eBook dallo Store VPP di Apple <!-- 800878 -->
È ora possibile [sincronizzare i libri](vpp-apps-ios.md) acquistati nello store Apple Volume Purchase Program con Intune e assegnarli agli utenti.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestione di più utenti per i dispositivi Samsung Knox Standard <!-- 971988 -->
I dispositivi che eseguono Samsung Knox Standard sono ora supportati per la [gestione multiutente](android-enroll.md) in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure Active Directory e il dispositivo è gestito centralmente indipendentemente dal fatto che sia o meno in uso.  Dopo aver eseguito l'accesso gli utenti finali possono accedere alle app e implementare i criteri loro assegnati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

### <a name="additional-windows-device-restriction-settings----818566---"></a>Altre impostazioni relative alle restrizioni dei dispositivi per Windows <!-- 818566 -->
Sono ora supportate altre [impostazioni di restrizione dei dispositivi per Windows](device-restrictions-windows-10.md) come maggiore supporto per il browser Edge, personalizzazione della schermata di blocco del dispositivo, personalizzazioni del menu Start, sfondo per la ricerca Windows Spotlight e impostazione del proxy.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Supporto multiutente per Windows 10 Creators Update <!-- 822547 -->
È stato aggiunto il supporto per la [gestione multiutente](windows-enroll.md) per i dispositivi che eseguono Windows 10 Creators Update e sono aggiunti al dominio di Azure Active Directory. Ciò significa che quando utenti standard diversi accedono al dispositivo con le credenziali di Azure AD ricevono tutte le app e i criteri assegnati al loro nome utente. Gli utenti non possono attualmente usare il portale aziendale per scenari self-service, ad esempio l'installazione di app.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Fresh Start per i PC Windows 10<!-- 1004830 -->
È ora disponibile una nuova [azione del dispositivo Fresh Start](device-fresh-start.md) per i PC Windows 10.  Quando si esegue questa azione, vengono rimosse tutte le app precedentemente installate nel PC e il computer è aggiornato automaticamente alla versione più recente di Windows. Questa funzionalità può essere usata per rimuovere le app OEM che spesso sono preinstallate in un nuovo PC. È possibile configurare se i dati utente devono essere conservati quando si esegue questa azione del dispositivo.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>Percorsi di aggiornamento aggiuntivi per Windows 10 <!-- 903672 -->
È ora possibile creare [criteri di aggiornamento dell'edizione per aggiornare i dispositivi](edition-upgrade-configure-windows-10.md) alle seguenti edizioni aggiuntive di Windows 10:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Registrazione in blocco di dispositivi Windows 10 <!-- 747607 -->
È ora possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune con Windows Configuration Designer (WCD). Per abilitare la [registrazione MDM in blocco](windows-bulk-enroll.md) del tenant di Azure AD, creare un pacchetto di provisioning che aggiunga i dispositivi al tenant di Azure AD usando Windows Configuration Designer e applicare il pacchetto ai dispositivi di proprietà dell'azienda che si vuole registrare e gestire in blocco. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento gli scenari di tipo self-service o portale aziendale non sono supportati.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>Nuove impostazioni MAM per PIN e percorsi di archiviazione gestita <!-- 581122, 736644 -->
Sono ora disponibili due nuove impostazioni dell'app per semplificare gli scenari di gestione di applicazioni mobili (MAM):

- **Disabilitare il PIN dell'app quando il PIN del dispositivo è gestito**: consente di rilevare se nel dispositivo registrato è presente un PIN del dispositivo e, in tal caso, di ignorare il PIN dell'app attivato dai criteri di protezione delle app. Questa impostazione consentirà di ridurre il numero di volte in cui gli utenti visualizzeranno un prompt di richiesta del PIN all'apertura di un'applicazione abilitata per MAM in un dispositivo registrato. Questa funzionalità è disponibile per sia per Android che per iOS.

- **Selezionare i servizi di archiviazione in cui è possibile salvare i dati aziendali**: consente di specificare i percorsi di archiviazione in cui salvare i dati aziendali. Gli utenti possono eseguire il salvataggio nei servizi di posizione di archiviazione selezionati, il che significa che tutti gli altri servizi di posizione di archiviazione non elencati verranno bloccati.

  I servizi di posizione di archiviazione supportati sono i seguenti:

  - OneDrive
  - Business SharePoint Online
  - Archiviazione locale

### <a name="help-desk-troubleshooting-portal----907448---"></a>Portale del Supporto tecnico per la risoluzione dei problemi <!-- 907448 -->
Il nuovo [portale per la risoluzione dei problemi](help-desk-operators.md) consente agli operatori del supporto tecnico e agli amministratori di Intune di visualizzare utenti e dispositivi e di eseguire attività per la risoluzione dei problemi tecnici di Intune.

## <a name="march-2017"></a>Marzo 2017

### <a name="support-for-ios-lost-mode---431695--"></a>Supporto per la modalità di dispositivo perso di iOS <!--431695-->
Per i dispositivi iOS 9.3 e versioni successive, Intune ha aggiunto il supporto per la **modalità di dispositivo perso**. È ora possibile bloccare un dispositivo per impedirne l'uso e visualizzare un messaggio e un numero di telefono di contatto nella schermata di blocco del dispositivo.

L'utente finale non sarà in grado di sbloccare il dispositivo finché la modalità di dispositivo perso non verrà disabilitata da un amministratore. Quando la modalità di dispositivo perso è abilitata, è possibile usare l'azione **Individua il dispositivo** per visualizzare la posizione geografica del dispositivo su una mappa nella console di Intune.

Deve trattarsi di un dispositivo iOS di proprietà dell'azienda, registrato con DEP, in cui sia attiva la modalità con supervisione.

Per altre informazioni, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).

### <a name="improvements-to-device-actions-report---677150--"></a>Miglioramenti al report Azioni del dispositivo <!--677150-->
Le prestazioni del report Azioni del dispositivo sono state migliorate. È inoltre possibile filtrare il report in base allo stato. Si possono ad esempio mostrare solo le azioni del dispositivo che sono state completate.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>Assegnare app line-of-business agli utenti con dispositivi non registrati <!--748823-->
Ora è possibile assegnare app line-of-business dallo store agli utenti anche se i dispositivi degli utenti non sono registrati in Intune. Se il dispositivo dell'utente non è registrato in Intune, l'utente dovrà usare il sito Web del portale aziendale per installare l'app assegnata, anziché l'app Portale aziendale.

### <a name="new-compliance-reports---846671--"></a>Nuovi report di conformità <!--846671-->
Sono ora disponibili report di conformità che definiscono il comportamento di conformità dei dispositivi in ambito aziendale e consentono di risolvere rapidamente i problemi correlati alla conformità riscontrati dagli utenti. È possibile visualizzare le informazioni seguenti:

- Stato di conformità generale dei dispositivi
- Stato di conformità per una singola impostazione
- Stato di conformità per singoli criteri

È anche possibile usare questi report per eseguire il drill-down in un singolo dispositivo e visualizzare le impostazioni e i criteri specifici che hanno effetto su tale dispositivo.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima della registrazione di Apple era accessibile solo dai collegamenti nel portale di Azure. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.


## <a name="february-2017"></a>Febbraio 2017

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>Possibilità di limitare la registrazione di dispositivi mobili <!--747600, 795782-->
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.

* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.  
* Solo per iOS e Android è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/intune-classic/deploy-use/manage-corporate-owned-devices).

### <a name="view-all-actions-on-managed-devices---677150--"></a>Visualizzare tutte le azioni nei dispositivi gestiti <!--677150-->
Il nuovo report __Azioni del dispositivo__ mostra gli utenti che hanno eseguito azioni remote come il ripristino delle impostazioni predefinite nei dispositivi e lo stato dell'azione. Vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->
Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

### <a name="custom-app-categories---748805--"></a>Categorie di app personalizzate <!--748805-->
È ora possibile creare, modificare e assegnare categorie per le app aggiunte a Intune. Attualmente, le categorie possono essere specificate solo in inglese.
Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="display-device-categories---814654--"></a>Visualizzare le categorie di dispositivi <!--814654-->
È ora possibile visualizzare la categoria dei dispositivi come colonna dell'elenco dei dispositivi. È inoltre possibile modificare la categoria nella sezione delle proprietà del pannello delle proprietà del dispositivo. Vedere [How to add an app to Intune](apps-add.md) (Come aggiungere un'app in Intune).

### <a name="configure-windows-update-for-business-settings---776716--"></a>Configurare le impostazioni di Windows Update for Business <!--776716-->

Windows as a Service è il nuovo modo per distribuire gli aggiornamenti per Windows 10. A partire da Windows 10, i nuovi aggiornamenti qualitativi e delle funzionalità includeranno il contenuto di tutti gli aggiornamenti precedenti. Ciò significa che, una volta installato l'aggiornamento più recente, si ha la sicurezza che i dispositivi Windows 10 sono perfettamente aggiornati. A differenza di quanto accadeva per le versioni precedenti di Windows, è ora necessario installare l'intero aggiornamento anziché una sola parte.

Usando Windows Update for Business, è possibile semplificare l'esperienza di gestione degli aggiornamenti in modo da non dover approvare singoli aggiornamenti per gruppi di dispositivi. È comunque possibile gestire i rischi nei propri ambienti configurando una strategia di implementazione degli aggiornamenti. In questo modo, Windows Update verificherà che gli aggiornamenti vengano installati al momento opportuno. Microsoft Intune offre la possibilità di configurare le impostazioni di aggiornamento sui dispositivi e di posticipare l'installazione degli aggiornamenti. Intune non archivia gli aggiornamenti, ma solo l'assegnazione dei criteri di aggiornamento. Per gli aggiornamenti i dispositivi accedono direttamente a Windows Update. Usare Intune per configurare e gestire gli **anelli di aggiornamento di Windows 10**. Un anello di aggiornamento contiene un gruppo di impostazioni che definiscono quando e come vengono installati gli aggiornamenti di Windows 10. Per informazioni dettagliate, vedere [Configurare le impostazioni di Windows Update for Business](windows-update-for-business-configure.md).
