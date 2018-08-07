---
title: Novità di Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Informazioni sulle novità nel portale di Intune di Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: 53be8456b09c7775a4de827eb09680f47e8d62d7
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321561"
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre a indicazioni sulle [modifiche previste](#whats-coming), [notifiche importanti](#notices) sul servizio e informazioni sulle [versioni precedenti](whats-new-archive.md). Alcune funzionalità potrebbero essere implementate nel corso di settimane e potrebbero non essere disponibili a tutti i clienti nella prima settimana.

> [!Note]
> Per informazioni sulle nuove funzionalità di gestione dei dispositivi mobili (MDM) ibrida, vedere la [pagina Novità della gestione di dispositivi mobili ibrida](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-july-23-2018"></a>Settimana del 23 luglio 2018

### <a name="app-management"></a>Gestione delle app

####  <a name="windows-apps-file-extensions----1884873---"></a>Estensioni file delle app di Windows <!-- 1884873 -->
Le estensioni file delle app di Windows ora includono *msi*, *appx*, *appxbundle*, *msix* e *msixbundle*. È possibile aggiungere un'app in Microsoft Intune selezionando **App per dispositivi mobili** > **App** > **Aggiungi**. Viene visualizzato il riquadro **Aggiungi app** che consente di selezionare il **Tipo di app**. Selezionare un tipo di app che consenta di caricare un file di pacchetto dell'app, selezionare il **File del pacchetto dell'app** e quindi specificare un file di installazione con l'estensione appropriata.

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Supporto di app line-of-business (LOB) per macOS <!-- 1895847 -->
Microsoft Intune consente la distribuzione di app line-of-business per macOS come app **obbligatorie** o **disponibili con registrazione**. Gli utenti finali possono ottenere le app distribuite come app **disponibili** tramite il Portale aziendale per macOS o il [sito Web del Portale aziendale](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Supporto app integrato di iOS per modalità tutto schermo <!-- 2051098 -->
Oltre alle App Store e App gestite, è ora possibile selezionare un'App predefinita, ad esempio, Safari, da eseguire in modalità tutto schermo in un dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modificare le distribuzioni delle app di Office 365 Pro Plus <!-- 2150145 -->
Per l'amministratore di Microsoft Intune è più facile modificare le distribuzioni delle app di Office 365 Pro Plus. Inoltre, non è più necessario eliminare le distribuzioni per modificare le proprietà del gruppo. Nel portale di Azure selezionare **Microsoft Intune** > **App per dispositivi mobili** > **App**. Selezionare la famiglia di prodotti Office 365 Pro Plus dall'elenco delle applicazioni.  


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Usare S/MIME per crittografare e firmare più dispositivi di un utente  <!-- 1333642 -->
Questo aggiornamento include una crittografia di posta elettronica S/MIME con un nuovo profilo di certificato importato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > selezionare la piattaforma > tipo di profilo **Certificato PKCS importato**). In Intune è possibile importare i certificati nel formato PFX. Intune può quindi distribuire i certificati a più dispositivi registrati da un singolo utente. Inoltre:

- Il profilo di posta elettronica iOS nativo supporta l'abilitazione della crittografia S/MIME mediante certificati importati in formato PFX.
- L'app di posta elettronica nativa nei dispositivi Windows Phone 10 usa automaticamente il certificato S/MIME.
- I certificati privati possono essere recapitati su più piattaforme. Tuttavia, non tutte le app di posta elettronica supportano S/MIME.
- In altre piattaforme potrebbe essere necessario configurare manualmente l'app di posta elettronica per abilitare S/MIME.  
- È possibile che le app di posta elettronica che supportano la crittografia S/MIME gestiscano il recupero dei certificati per la crittografia della posta elettronica S/MIME in un modo non supportato dal software MDM, ad esempio basandosi sull'archivio certificati del server di pubblicazione.

Supportato in: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Creare criteri di conformità dei dispositivi usando le impostazioni del firewall nei dispositivi macOS <!-- 1497640 -->
Quando si creano nuovi criteri di conformità per macOS, in **Conformità del dispositivo** > **Criteri** > **Crea criteri** > **Piattaforma: macOS** > **Protezione del sistema**, sono disponibili alcune nuove impostazioni del **firewall**: 

- **Firewall**: configurare in che modo le connessioni in ingresso devono essere gestite nell'ambiente in uso.
- **Connessioni in ingresso**: **bloccare** tutte le connessioni in ingresso tranne quelle necessarie per i servizi Internet di base, ad esempio DHCP, Bonjour e IPSec. Questa impostazione consente inoltre di bloccare tutti i servizi di condivisione.
- **Modalità mascheramento**: **abilitare** questa modalità per impedire che il dispositivo risponda alle richieste di probe. Il dispositivo continua a rispondere alle richieste in ingresso provenienti da applicazioni autorizzate.

Si applica a: macOS 10.12 e versioni successive

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Nuovo profilo di configurazione del dispositivo Wi-Fi per Windows 10 e versioni successive <!-- 1879077 -->
Attualmente, è possibile importare ed esportare i profili Wi-Fi usando i file XML. In questo aggiornamento è possibile creare un profilo di configurazione del dispositivo Wi-Fi direttamente in Intune, come in alcune altre piattaforme.

Per creare il profilo, aprire **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Wi-Fi**. 

Si applica a Windows 10 e versioni successive.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>Modalità tutto schermo obsoleta appare disattivata e non può essere modificata <!-- 2149998 eeready -->
La [funzionalità Modalità tutto schermo](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Limitazioni del dispositivo**) è obsoleta e sostituita dalle [impostazioni di modalità tutto schermo per Windows 10 e versioni successive](kiosk-settings.md). In questo aggiornamento la funzionalità **Modalità tutto schermo obsoleta** appare disattivata e l'interfaccia utente non potrà essere modificata o aggiornata. 

Per abilitare la modalità tutto schermo, vedere [Impostazioni relative alla modalità tutto schermo per Windows 10 e versioni successive](kiosk-settings.md).

Si applica a Windows 10 e versioni successive, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>API per l'uso delle autorità di certificazione di terze parti <!-- 2184013 -->
In questo aggiornamento è disponibile un'API Java che consente l'integrazione delle autorità di certificazione di terze parti con Intune e SCEP. Gli utenti potranno quindi aggiungere il certificato SCEP a un profilo e applicarlo ai dispositivi usando il software MDM.

Attualmente Intune supporta [le richieste SCEP con Servizi certificati Active Directory](certificates-scep-configure.md).

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Visualizzare o nascondere il pulsante Termina sessione in un browser in modalità tutto schermo <!-- 2455253 -->
Ora è possibile specificare se visualizzare o nascondere il pulsante Termina sessione nei browser in modalità tutto schermo. Il controllo è disponibile in **Configurazione del dispositivo** > **Modalità tutto schermo (anteprima)** > **Web browser in modalità tutto schermo**. Se è abilitato, quando un utente fa clic sul pulsante, l'app richiede di confermare se terminare la sessione. Se si conferma, il browser cancella tutti i dati di navigazione e torna all'URL predefinito.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Creare un profilo di configurazione cellulare eSIM <!-- 2564077 -->
In **Configurazione del dispositivo** è possibile creare un profilo cellulare eSIM. È possibile importare un file contenente i codici di attivazione cellulare forniti dall'operatore di telefonia mobile. È quindi possibile distribuire i profili nei dispositivi Windows 10 con eSIM LTE, ad esempio Surface Pro LTE e altri dispositivi che supportano eSIM.

Verificare se i [dispositivi supportano i profili eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Si applica a Windows 10 e versioni successive. 




### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Contrassegnare automaticamente i dispositivi Android registrati usando Samsung Knox Mobile Enrollment come "aziendali". <!-- 2404851 -->
Per impostazione predefinita, ora i dispositivi Android registrati usando Samsung Knox Mobile Enrollment vengono contrassegnati come **Aziendale** in **Proprietà del dispositivo**. Non è necessario identificare manualmente i dispositivi aziendali utilizzando i numeri IMEI o seriali prima della registrazione mediante Knox Mobile Enrollment.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminare in blocco i dispositivi nel pannello Dispositivi <!-- 1793693 -->

È possibile eliminare più dispositivi contemporaneamente nel pannello Dispositivi. Scegliere **Dispositivi** > **Tutti i dispositivi** > selezionare i dispositivi da eliminare > **Elimina**. Per i dispositivi che non possono essere eliminati, viene visualizzato un avviso.

## <a name="week-of-july-16-2018"></a>Settimana del 16 luglio 2018  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Più opportunità di sincronizzazione nell'app Portale aziendale per Windows  
L'app Portale aziendale per Windows ora consente di avviare la sincronizzazione direttamente dalla barra delle applicazioni Windows e dal menu Start. Questa funzionalità è particolarmente utile se l'unica attività eseguita è sincronizzare i dispositivi e ottenere l'accesso alle risorse aziendali. Per accedere alla nuova funzionalità, fare clic sull'icona del portale aziendale che è stata aggiunta alla barra delle applicazioni o al menu Start. Nelle opzioni di menu, elemento detto anche jump list, selezionare **Sync this device** (Sincronizzare il dispositivo). Verrà aperta la pagina **Impostazioni** del portale aziendale e inizierà la sincronizzazione. Per esaminare le nuove funzionalità, vedere [Novità dell'interfaccia utente](whats-new-app-ui.md).   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Nuove esperienze di esplorazione nell'app Portale aziendale per Windows  

Durante l'esplorazione o la ricerca di app nell'app Portale aziendale per Windows, ora è possibile passare dalla visualizzazione **Riquadri** alla nuova visualizzazione **Dettagli** e viceversa. La nuova visualizzazione elenca i dettagli dell'applicazione, ad esempio il nome, l'editore, la data di pubblicazione e lo stato di installazione.  

La visualizzazione **Installata** della pagina **App** consente di visualizzare i dettagli sulle installazioni completate e in corso. Per vedere come appare la nuova vista, vedere [Novità dell'interfaccia utente](whats-new-app-ui.md).  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>Esperienza dell'app Portale aziendale migliorata per gli utenti del manager di registrazione dispositivi  
Quando un manager di registrazione dispositivi accede all'app Portale aziendale per Windows, ora l'app elenca solo il dispositivo in esecuzione corrente. Questo miglioramento ridurrà i timeout che in precedenza si verificavano quando l'app tentava di mostrare tutti i dispositivi registrati nel manager di registrazione dispositivi.  


## <a name="week-of-july-9-2018"></a>Settimana del 9 luglio 2018

### <a name="app-management"></a>Gestione delle app

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloccare l'accesso dell'app in base ai fornitori e ai modelli non approvati del dispositivo <!-- 1425689 ! -->
L'amministratore IT di Intune può applicare un elenco specifico di produttori Android e/o di modelli iOS tramite i criteri di Protezione app di Intune. L'amministratore IT può fornire un elenco delimitato da punto e virgola di produttori per i criteri Android e di modelli di dispositivo per i criteri iOS. I criteri di Protezione app di Intune sono solo per Android e iOS. Su questo elenco specifico è possibile eseguire due azioni distinte:
- Blocco dell'accesso delle app nei dispositivi non specificati.
- Cancellazione selettiva dei dati aziendali nei dispositivi non specificati. 

L'utente non potrà accedere all'applicazione di destinazione se non vengono soddisfatti i requisiti definiti tramite i criteri. In base alle impostazioni, è possibile che l'utente venga bloccato o che i dati aziendali nell'app vengano cancellati in modo selettivo. Nei dispositivi iOS è necessario integrare Intune APP SDK tramite applicazioni specifiche (ad esempio WXP, Outlook, Managed Browser, Yammer) perché sia possibile applicare questa funzionalità con le applicazioni di destinazione. Questa integrazione avviene progressivamente e dipende dai team delle applicazioni specifiche. In Android questa funzionalità richiede il portale aziendale più recente. 

Nei dispositivi degli utenti finali il client Intune esegue un'azione basata su una semplice corrispondenza delle stringhe specificate nel pannello Intune per i criteri di protezione delle applicazioni. Ciò dipende completamente dal valore segnalato dal dispositivo. Di conseguenza, è opportuno che l'amministratore IT si assicuri che il comportamento previsto sia accurato. A tale scopo, è possibile testare questa impostazione con svariati produttori di dispositivi e modelli destinati a un piccolo gruppo di utenti. In Microsoft Intune selezionare **App per dispositivi mobili** > **Criteri di protezione delle app** per visualizzare e aggiungere i criteri di protezione delle app. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md) e [Cancellare i dati in modo selettivo usando le azioni di accesso per i criteri di protezione delle app in Intune](app-protection-policies-access-actions.md).

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>Accesso alla build in versione non definitiva del portale aziendale macOS<!-- 1734766 -->
Con Microsoft AutoUpdate è possibile iscriversi e ricevere le build anticipatamente partecipando al programma Insider. L'iscrizione consente di usare il portale aziendale aggiornato prima che sia disponibile per gli utenti finali. Per altre informazioni, vedere il [blog su Microsoft Intune](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/).

## <a name="week-of-july-2-2018"></a>Settimana del 2 luglio 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>Monitorare lo stato di configurazione delle app iOS per ogni dispositivo <!-- 880037 -->
L'amministratore di Microsoft Intune può monitorare lo stato di configurazione delle app iOS per ogni dispositivo gestito. Da **Microsoft Intune** nel portale di Azure selezionare **Dispositivi** > **Tutti i dispositivi**. Dall'elenco dei dispositivi gestiti selezionare un dispositivo specifico per visualizzare il relativo pannello. Nel pannello del dispositivo selezionare **Configurazione dell'app**.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>Azioni di accesso per i criteri di protezione delle app <!-- 1483510 -->
È possibile configurare i criteri di protezione delle app per cancellare i dati in modo esplicito, bloccare o segnalare i dispositivi non conformi. L'azione di *cancellazione* rimuove i dati aziendali da un dispositivo. In caso di cancellazione, all'utente del dispositivo vengono notificati sia il motivo della cancellazione sia la procedura di correzione. Per alcune impostazioni, come la versione minima del sistema operativo, sarà possibile applicare più azioni, ad esempio il blocco e la cancellazione. Si noti che queste azioni vengono attivate all'avvio dell'app.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Cancellazione selettiva dei dati delle app dell'organizzazione <!-- 1507030 -->
Gli amministratori ora possono configurare una cancellazione selettiva dei dati dell'organizzazione come nuova azione quando non sono soddisfatte le condizioni delle impostazioni di accesso previste dai criteri di protezione delle applicazioni.  Questa funzionalità consente agli amministratori di proteggere e rimuovere automaticamente i dati sensibili dell'organizzazione nelle applicazioni in base a criteri configurati in precedenza.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revoca di un'app iOS acquistata usando VPP <!-- 1777384 -->
L'amministratore di Microsoft Intune può revocare tutte le licenze per un'app iOS selezionata, acquistata tramite Volume Purchase Program (VPP). È possibile informare gli utenti quando un'app concessa in licenza non è più assegnata a loro. La revoca di una licenza per app non comporterà la disinstallazione dell'app VPP correlata dal dispositivo. Per disinstallare un'app VPP, è necessario modificare l'azione di assegnazione specificando **Disinstalla**. Il conteggio delle licenze recuperate è indicato nel nodo **App con licenza** nel carico di lavoro **App** di Intune. Per altre informazioni relative alle app iOS VPP, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Aggiornamenti per i messaggi di mancata conformità nell'app Portale aziendale <!-- 1832222 -->
È stata ultimata la revisione dei messaggi visualizzati dagli utenti dei dispositivi quando un dispositivo risulta non conforme. I messaggi mantegono il significato originale, ma sono stati aggiornati con un linguaggio più descrittivo e un minor uso di terminologia tecnica. Sono stati aggiornati anche i collegamenti alla documentazione e alla procedura di correzione per tenerli aggiornati.
L'esempio seguente di prima e dopo illustra i miglioramenti per i messaggi che verranno introdotti:
- **Prima**: *questo dispositivo non ha contattato il servizio Intune nel periodo di tempo specificato e richiesto dall'amministratore IT. Per risolvere questo problema, aprire l'app Portale aziendale nel dispositivo e fare clic sul pulsante Controlla conformità.*
- **Dopo**: *il dispositivo non ha ultimamente contattato l'organizzazione. Per ristabilire una connessione, aprire l'app Portale aziendale nel dispositivo e toccare Verifica le impostazioni per il dispositivo.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revocare la licenza di un'app iOS VPP <!-- 1863797 -->
L'amministratore può recuperare la licenza di un'app iOS VPP assegnata a un utente o dispositivo. La disinstallazione di un'app iOS VPP consente inoltre di recuperare la licenza dell'app. Prima di disinstallare l'app, è necessario rimuovere l'utente o il dispositivo dal gruppo a cui l'app è destinata. Rimuovere l'utente o il dispositivo dal gruppo per evitare la reinstallazione dell'app. Dopo aver completato questa procedura, è possibile scegliere di assegnare la licenza dell'app a un altro utente o dispositivo. Per altre informazioni sulle licenze delle app iOS VPP, vedere [Procedura per la gestione delle app iOS acquistate tramite Volume Purchase Program con Microsoft Intune](vpp-apps-ios.md).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>Selezionare le categorie di dispositivi usando le impostazioni Accedi all'azienda o all'istituto di istruzione <!-- 1058963 eenotready --> 
Se è stato abilitato il [mapping del gruppo di dispositivi](https://docs.microsoft.com/en-us/intune/device-group-mapping), agli utenti di Windows 10 sarà ora richiesto di selezionare una categoria di dispositivi dopo la registrazione usando il pulsante **Connetti** in **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usare sAMAccountName come nome utente dell'account per i profili di posta elettronica <!-- 1500307 -->
È possibile usare l'oggetto **sAMAccountName** locale come nome utente dell'account per i profili di posta elettronica per Android, iOS e Windows 10. È anche possibile ottenere il dominio dall'attributo `domain` o `ntdomain` in Azure Active Directory (Azure AD). In alternativa, immettere un dominio personalizzato statico.

Per usare questa funzionalità, è necessario sincronizzare l'attributo `sAMAccountName` dell'ambiente Active Directory locale con Azure AD.

Si applica a: [Andoid](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 e versioni successive](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Visualizzare i profili di configurazione del dispositivo in conflitto <!-- 1556983 -->
In **Configurazione del dispositivo** viene visualizzato un elenco dei profili esistenti. Con questo aggiornamento viene aggiunta una nuova colonna che fornisce informazioni dettagliate sui profili con un conflitto. È possibile selezionare una riga di conflitto per visualizzare l'impostazione e il profilo che presenta il conflitto. 

Altre informazioni sulla [gestione dei profili di configurazione ](device-profile-monitor.md#view-conflicts).

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Nuovo stato per i dispositivi nella conformità del dispositivo <!-- 2308882 -->
In **Conformità del dispositivo** > **Criteri** > selezionare un criterio > **Panoramica**. Verranno aggiunti i nuovi stati seguenti:
- riuscito
- Errore
- conflitto
- in sospeso
- non applicabile Viene visualizzata anche un'immagine che illustra il conteggio dei dispositivi di un'altra piattaforma. Ad esempio, se si sta consultando un profilo iOS, il nuovo riquadro indica il numero di dispositivi non iOS assegnati a questo profilo. Vedere [Criteri di conformità dei dispositivi](compliance-policy-monitor.md#view-status-of-device-policies).

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>La conformità del dispositivo supporta soluzioni antivirus di terze parti <!-- 2325484 -->
Quando si creano criteri di conformità del dispositivo in **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Piattaforma: Windows 10 e versioni successive** > **Impostazioni** > **Sicurezza del sistema** sono disponibili nuove opzioni in **[Sicurezza del dispositivo](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)**: 
- **Antivirus**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando soluzioni antivirus registrate nel Centro sicurezza PC Windows, ad esempio Symantec e Windows Defender. 
- **Antispyware**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando le soluzioni antispyware registrate nel Centro sicurezza PC Windows, ad esempio Symantec e Windows Defender. 

Si applica a: Windows 10 e versioni successive 

### <a name="device-enrollment"></a>Registrazione del dispositivo

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>Dispositivi senza la colonna relativa ai profili nell'elenco di token DEP <!-- 1853904 -->
Nell'elenco di token DEP è disponibile una nuova colonna in cui viene indicato il numero di dispositivi che non hanno un profilo assegnato. Gli amministratori possono così assegnare un profilo a tali dispositivi prima di consegnarli agli utenti. Per visualizzare la nuova colonna, passare a **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP**.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Modifiche del nome Google per Android for Work e Play for Work <!--842873 -->
Intune ha aggiornato la terminologia di "Android for Work" in modo da riflettere le modifiche di personalizzazione di Google. I termini "Android for Work" e "Play for Work" non vengono più usati. Viene usata un'altra terminologia in base al contesto:
- "Android Enterprise" si riferisce allo stack di gestione per Android moderno nel suo insieme.
- "Profilo di lavoro" o "Proprietario del profilo" fa riferimento ai dispositivi BYOD gestiti con i profili di lavoro.
- "Google Play gestito" si riferisce al Google Play Store.

#### <a name="rules-for-removing-devices----1609459---"></a>Regole di rimozione dei dispositivi <!-- 1609459 -->
Sono disponibili nuove regole che consentono di rimuovere automaticamente i dispositivi che non si sono connessi per un numero di giorni specificato. Per visualizzare la nuova regola, passare al riquadro **Intune**, selezionare **Dispositivi** e selezionare **Regole di pulizia del dispositivo**.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Supporto monouso di proprietà dell'azienda per i dispositivi Android <!-- 1630973 -->

Intune ora supporta i dispositivi Android con gestione avanzata, bloccati e in modalità tutto schermo. Questo consente agli amministratori di limitare ulteriormente l'uso di un dispositivo a una sola app o un piccolo gruppo di app e impedire agli utenti di abilitare altre app o eseguire altre azioni nel dispositivo. Per impostare la modalità tutto schermo Android, passare a Intune > **Registrazione del dispositivo** > **Registrazione Android**  > **Registrazioni dei dispositivi per uso in modalità tutto schermo e per attività**. Per altre informazioni, vedere [Set up enrollment of Android enterprise kiosk devices](android-kiosk-enroll.md) (Configurare la registrazione dei dispositivi Android per modalità tutto schermo).

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>Revisione riga per riga degli identificatori duplicati caricati per i dispositivi aziendali <!-- 2203794-->
Quando si caricano gli ID aziendali, Intune ora presenta un elenco di tutti i duplicati e offre la possibilità di sostituire o mantengono le informazioni esistenti. Viene visualizzato un report se sono presenti duplicati dopo che sono state scelte le opzioni **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi identificatori**. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Aggiungere manualmente gli identificatori dei dispositivi aziendali <!-- 2203803 -->
È ora possibile aggiungere manualmente gli ID dei dispositivi aziendali. Scegliere **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali** > **Aggiungi**. 

## <a name="week-of-june-25-2018"></a>Settimana del 25 giugno 2018

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo: nuovo partner di Mobile Threat Defense <!-- 1169249 -->

È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Pradeo, una soluzione di protezione dalle minacce per dispositivi mobili (MTD, Mobile Threat Defense) integrata in Microsoft Intune.

## <a name="week-of-june-18-2018"></a>Settimana del 18 giugno 2018

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Supporto di Edge in dispositivi mobili per i criteri di protezione delle app di Intune <!-- 1817882 -->

Il browser Microsoft Edge per i dispositivi mobili supporta ora i criteri di protezione delle app definiti in Intune.

## <a name="week-of-june-11-2018"></a>Settimana del 11 giugno 2018

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>Usare la modalità FIPS con NDES Connector per i certificati <!-- 1333688 -->
Quando si installa NDES Connector per i certificati in un computer con la modalità FIPS (Federal informazioni Processing Standard) abilitata, l'emissione e la revoca dei certificati non funzionano come previsto. Con questo aggiornamento, il supporto per FIPS è incluso con NDES Connector per i certificati. 

Questo aggiornamento include anche:

- NDES Connector per i certificati richiede .NET Framework 4.5, incluso automaticamente in Windows Server 2016 e Windows Server 2012 R2. In precedenza, la versione minima richiesta era.NET Framework 3.5.
- Il supporto di TLS 1.2 è incluso con NDES Connector per i certificati. Pertanto, se il server in cui è installato NDES Connector per i certificati supporta TLS 1.2, viene usato TLS 1.2. Se il server non supporta TLS 1.2, viene usato TLS 1.1. Attualmente, TLS 1.1 viene usato per l'autenticazione tra i dispositivi e il server.

Per altre informazioni, vedere [Configurare e usare i certificati SCEP con Intune](certificates-scep-configure.md) e [Configurare e usare i certificati PKCS con Intune](certficates-pfx-configure.md).

## <a name="week-of-june-4-2018"></a>Settimana del 4 giugno 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>Recuperare l'ID modello utente dell'app associato per le app di Microsoft Store per le aziende in modalità tutto schermo <!-- 1560077 ! -->
Intune può ora recuperare gli ID modello utente dell'app per le app di Microsoft Store per le aziende per offrire una configurazione ottimizzata del profilo in modalità tutto schermo.

Per altre informazioni sulle app di Microsoft Store per le aziende, vedere [Gestire le app di Microsoft Store per le aziende](windows-store-for-business.md).

#### <a name="new-company-portal-branding-page----1916370---"></a>Nuova pagina di personalizzazione del Portale aziendale <!-- 1916370 -->
La pagina di personalizzazione del Portale aziendale ha layout, messaggi e descrizioni comandi nuovi.


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Supporto per i profili VPN di Palo Alto Networks GlobalProtect <!-- 1333680 eeready ! -->
Con questo aggiornamento, è possibile scegliere Palo Alto Networks GlobalProtect come tipo di connessione VPN per i profili VPN in Intune (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Tipo di profilo** > **VPN**). In questa versione sono supportate le piattaforme seguenti: 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>Aggiunte alle impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1403702 -->
È ora possibile configurare impostazioni aggiuntive per le opzioni di sicurezza dei dispositivi locali Windows 10. Le impostazioni aggiuntive sono disponibili per le aree relative ai client di rete Microsoft, ai server di rete Microsoft, all'accesso e alla sicurezza di rete e all'accesso interattivo. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Abilitare la modalità tutto schermo nei dispositivi Windows 10 <!-- 1560072 ! -->
Nei dispositivi Windows 10 è possibile creare un profilo di configurazione e abilitare la modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10** > **Restrizioni del dispositivo** > **Modalità tutto schermo**). In questo aggiornamento l'impostazione **Modalità tutto schermo (anteprima)** viene rinominata **Chiosco multimediale (obsoleto)**. Non è più consigliabile usare **Chiosco multimediale (obsoleto)**, che tuttavia continuerà a funzionare fino all'aggiornamento di luglio. **Chiosco multimediale (obsoleto)** viene sostituito dal nuovo tipo di profilo **Modalità tutto schermo** (**Crea profilo** > **Windows 10** > **Modalità tutto schermo (anteprima)**), che conterrà le impostazioni per configurare le modalità tutto schermo in Windows 10 RS4 e versioni successive.

Si applica a Windows 10 e versioni successive.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>Grafico utente del profilo del dispositivo nuovamente disponibile <!-- 2160133 -->
Durante il miglioramento dei conteggi numerici visualizzati nel grafico del profilo del dispositivo (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**), il grafico utente è stato temporaneamente rimosso.

Con questo aggiornamento, il grafico utente è di nuovo disponibile e visibile nel portale di Azure.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>Supporto per la registrazione di Windows Autopilot senza l'autenticazione utente <!-- 1165118 wnready -->
Intune ora supporta la registrazione di Windows Autopilot senza l'autenticazione utente. Si tratta della nuova opzione del profilo di distribuzione di Windows Autopilot "Modalità di distribuzione Autopilot" che viene impostata sulla distribuzione automatica.  Il dispositivo deve eseguire Windows 10 Insider Preview Build 17672 o versione successiva e possedere un chip TPM 2.0 per completare questo tipo di registrazione. Poiché non è necessaria l'autenticazione utente, è consigliabile assegnare questa opzione solo ai dispositivi su cui si ha controllo fisico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Nuova impostazione per lingua/area quando si configura la Configurazione guidata per Autopilot <!-- 1821766 eeready -->
È disponibile una nuova impostazione di configurazione per impostare la lingua e l'area dei profili di Autopilot durante la Configurazione guidata. Per visualizzare questa nuova impostazione, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo** > **Modalità di distribuzione** = **Self-deploying (Distribuzione automatica)** > **Impostazioni predefinite configurate**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuova impostazione per configurare la tastiera del dispositivo <!-- 1821768 -->
Sarà disponibile una nuova impostazione per configurare la tastiera per i profili di Autopilot durante la Configurazione guidata. Per visualizzare questa nuova impostazione, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo** > **Modalità di distribuzione** = **Self-deploying (Distribuzione automatica)** > **Impostazioni predefinite configurate**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Spostamento dei profili AutoPilot nei gruppi di destinazione <!-- 1877935 -->
I profili di distribuzione di AutoPilot possono essere assegnati ai gruppi di Azure AD contenenti dispositivi AutoPilot.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="set-compliance-by-device-location----851881----"></a>Impostare la conformità in base al percorso del dispositivo <!-- 851881 ! -->
In alcuni casi, potrebbe essere necessario limitare l'accesso alle risorse aziendali a un percorso specifico, definito da una connessione di rete. È ora possibile creare un criterio di conformità (**Conformità del dispositivo** > **Percorsi**) basato sull'indirizzo IP del dispositivo. Se il dispositivo non è più compreso nell'intervallo di IP, non può accedere alle risorse aziendali.

Si applica a: dispositivi Android 6.0 e versioni successive, con l'app Portale aziendale aggiornata

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitare app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot<!-- 1621980 -->
Sarà possibile impedire l'installazione di app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot. Per vedere questa funzionalità, passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Piattaforma** = **Windows 10 o versione successiva** > **Tipo di profilo** = **Limitazioni del dispositivo** > **Configura** > **Windows Spotlight** > **Funzionalità consumer**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Disinstallare gli aggiornamenti più recenti dagli aggiornamenti software di Windows 10 <!-- 1732948 eeready -->
Se si rileva un problema di rilievo nei computer Windows 10, è possibile scegliere di disinstallare l'ultimo aggiornamento delle funzionalità oppure l'ultimo aggiornamento qualitativo ripristinando lo stato precedente. La disinstallazione di un aggiornamento delle funzionalità o di un aggiornamento qualitativo è disponibile solo per il canale di manutenzione su cui è attivo il dispositivo. La disinstallazione attiverà un criterio per il ripristino dell'aggiornamento precedente nei computer Windows 10. In particolare per gli aggiornamenti delle funzionalità, è possibile limitare a un intervallo di giorni compreso tra 2 e 60 la disinstallazione dell'ultima versione. Per impostare le opzioni di disinstallazione dell'aggiornamento software, selezionare **Aggiornamenti software** dal pannello **Microsoft Intune** nel portale di Azure. Nel pannello **Aggiornamenti software** selezionare **Anelli di aggiornamento di Windows 10**. A questo punto è possibile scegliere l'opzione **Disinstalla** dalla sezione **Panoramica**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Cercare tutti i dispositivi IMEI e il numero di serie <!-- 1793685 -->
Nel pannello Tutti i dispositivi è ora possibile cercare codici IMEI e numeri di serie (sono ancora disponibili posta elettronica, UPN, nome del dispositivo e nome di gestione). In Intune scegliere **Dispositivi** > **Tutti i dispositivi** > e immettere la ricerca nella casella di ricerca.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Il campo Nome di gestione sarà modificabile <!-- 1875989 -->
È ora possibile modificare il campo Nome di gestione nel pannello **Proprietà** di un dispositivo. Per modificare questo campo, scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Proprietà**. È possibile usare il campo Nome di gestione per identificare in modo univoco un dispositivo.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nuovo filtro per Tutti i dispositivi: Categoria del dispositivo <!-- 1878520 -->
È ora possibile filtrare l'elenco **Tutti i dispositivi** per categoria di dispositivi. A tale scopo, scegliere **Dispositivi** > **Tutti i dispositivi** > **Filtro** > **Categoria del dispositivo**.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>Usare TeamViewer per condividere lo schermo dei dispositivi iOS e MacOS <!-- 1985547 -->
Gli amministratori ora possono connettersi a [TeamViewer](device-profile-android-teamviewer.md) e avviare un sessione di condivisione dello schermo con i dispositivi iOS e macOS. Gli utenti di iPhone, iPad e macOS possono condividere gli schermi in tempo reale con altri dispositivi mobili o desktop. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>Supporto di Exchange Connector multipli <!-- 2070451 -->
Non è più previsto il limite di un Microsoft Intune Exchange Connector per tenant. Intune ora supporta Exchange Connector multipli per consentire la configurazione dell'accesso condizionale in Intune per più organizzazioni di Exchange locali.

Con un On-premises Exchange Connector di Intune è possibile gestire l'accesso dei dispositivi alle cassette postali di Exchange locali in base al fatto che i dispositivi siano registrati o meno in Intune e siano conformi ai criteri di conformità dei dispositivi di Intune. Per configurare un connettore, scaricare l'On-premises Exchange Connector di Intune dal portale di Azure e installarlo in un server dell'organizzazione di Exchange. Nel dashboard di Microsoft Intune scegliere **Accesso locale**, quindi nella sezione **Installazione**, scegliere **Connettore per Exchange ActiveSync**. Scaricare l'On-premises Exchange Connector e installarlo in un server della propria organizzazione di Exchange. Ora che non vige più il limite di Exchange Connector per tenant, gli utenti che hanno più organizzazioni di Exchange possono seguire lo stesso processo per scaricare e installare un connettore per ogni organizzazione di Exchange aggiuntiva.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>Nuovo dettaglio hardware del dispositivo: CCID <!-- 2156657 -->
Sono ora disponibili per ogni dispositivo informazioni CCID (Chip Card Interface Device). Per visualizzare queste informazioni, scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Hardware**> controllare le informazioni in **Dettagli di rete**>

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>Assegnare tutti gli utenti e tutti i dispositivi come gruppi ambito <!-- 2196803 -->
È ora possibile assegnare tutti gli utenti, tutti i dispositivi, tutti gli utenti e tutti i dispositivi nei gruppi ambito. A tale scopo, scegliere **Ruoli di Intune** > **Tutti i ruoli** > **Policy and Profile Manager** >  (Gestione criteri e profili) **Assegnazioni** > scegliere un'assegnazione **Ambito (gruppi)**.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>Informazioni UDID ora incluse per dispositivi iOS e macOS<!-- 2219806 wnready-->
Per visualizzare le informazioni UDID (Unique Device Identifier) per i dispositivi iOS e macOS, passare a **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Hardware**. Le informazioni UDID sono disponibili solo per i dispositivi aziendali (come impostato in **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Proprietà** > **Proprietà del dispositivo**).

### <a name="intune-apps"></a>App di Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Miglioramento della risoluzione dei problemi di installazione delle app <!-- 928990 -->
Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. È in corso la distribuzione di un'anteprima pubblica delle funzionalità di risoluzione dei problemi delle app. Sotto ogni singolo dispositivo si noterà un nuovo nodo denominato **App gestite**, che elenca le app distribuite tramite MDM di Intune. Nel nodo è visibile un elenco di stati di installazione delle app. Se si seleziona una singola app, si noterà la visualizzazione relativa alla risoluzione dei problemi per l'app specifica. In tale visualizzazione è presente il ciclo di vita end-to-end dell'app, ad esempio quando l'app è stata creata, modificata, specificata come destinazione e distribuita in un dispositivo. Se l'installazione dell'app non è riuscita, saranno anche disponibili il codice di errore e un messaggio sulla causa dell'errore. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Criteri di protezione delle app di Intune e Microsoft Edge <!-- 1818968 -->
Il browser Microsoft Edge per dispositivi mobili (iOS e Android) ora supporta i criteri di protezione delle app di Microsoft Intune. Gli utenti di dispositivi iOS e Android che accedono con gli account Azure AD aziendali nell'applicazione Edge saranno protetti da Intune. Nei dispositivi iOS il criterio **Require managed browser for web content** (Richiedi Managed Browser per contenuti Web) consentirà agli utenti di aprire i collegamenti in Edge quando è gestito.

## <a name="week-of-may-14-2018"></a>Settimana del 14 maggio 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>Richiedere l'installazione di criteri, app e profili certificato e di rete <!-- 1553555 -->

Gli amministratori possono impedire agli utenti finali di accedere al desktop di Windows 10 RS4 finché Intune non avrà installato criteri, app e profili di certificato e di rete durante il provisioning dei dispositivi AutoPilot. Per altre informazioni, vedere [Configurare la registrazione dei dispositivi Windows](windows-enrollment-status.md).

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>Configurazione dei criteri di protezione delle app <!-- 2144597 Part 2 -->

Nel portale di Azure anziché passare al pannello del servizio Protezione app di Intune ora è possibile accedere a Intune. Ora è disponibile un solo percorso per i criteri di protezione delle app in Intune. Si noti che tutti i criteri di protezione delle app si trovano nel pannello **App per dispositivi mobili** in Intune in **Criteri di protezione delle app**. Questa integrazione contribuisce alla semplificazione dell'amministrazione della gestione del cloud. Tenere presente che tutti i criteri di protezione delle app sono già presenti in Intune ed è possibile modificare tutti i criteri configurati in precedenza. I criteri di protezione delle app e per l'accesso condizionale di Intune ora sono in **Accesso condizionale**, che si trova nella sezione **Gestisci** del pannello **Microsoft Intune** o nella sezione **Sicurezza** del pannello **Azure Active Directory**. Per altre informazioni sulla modifica dei criteri di accesso condizionale, vedere [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>Settimana del 7 maggio 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Supporto della registrazione per dispositivi mobili Samsung Knox <!--1112863-->

Quando si usa Intune con Samsung Knox Mobile Enrollment (KME), è possibile registrare un numero elevato di dispositivi Android di proprietà della società. Gli utenti connessi a reti Wi-Fi o cellulari possono eseguire la registrazione con pochi tocchi quando accendono il dispositivo per la prima volta. Quando si usa l'app Knox Deployment, è possibile registrare i dispositivi tramite Bluetooth o NFC. Per altre informazioni, vedere [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Registrare automaticamente i dispositivi Android usando Samsung Knox Mobile Enrollment).

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Richiesta di assistenza in Portale aziendale per Windows 10 <!-- 1874137 -->

Portale aziendale per Windows 10 invia ora i log delle app direttamente a Microsoft quando l'utente avvia il flusso di lavoro per visualizzare la Guida per un problema. In questo modo sarà più semplice risolvere i problemi inoltrati a Microsoft.

## <a name="week-of-april-23-2018"></a>Settimana del 23 aprile 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Supporto di passcode per PIN MAM in Android<!-- 1438086 -->

Gli amministratori di Intune possono impostare un requisito di avvio delle applicazioni per imporre un passcode anziché un PIN MAM numerico. Se il requisito viene configurato, all'utente viene richiesto di impostare e usare un passcode prima di accedere alle applicazioni con supporto MAM. Un passcode è un PIN numerico con almeno un carattere speciale o una lettera maiuscola o minuscola. Il supporto di Intune per i passcode è simile a quello esistente per il PIN numerico, con la possibilità di impostare una lunghezza minima e consentendo la ripetizione di caratteri e sequenze tramite la console di amministrazione. Questa funzionalità richiede la versione più recente di Portale aziendale in Android. Questa funzionalità è già disponibile per iOS.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>Supporto di app line-of-business (LOB) per macOS <!-- 1473977 -->
Microsoft Intune offrirà la possibilità di installare app LOB (line-of-business) macOS dal portale di Azure. Sarà possibile aggiungere un'app LOB macOS a Intune dopo una pre-elaborazione effettuata dallo strumento disponibile in GitHub. Nel portale di Azure scegliere **App per dispositivi mobili** dal pannello **Intune**. Nel pannello **App per dispositivi mobili** scegliere **App** > **Aggiungi**. Nel pannello **Aggiungi app** selezionare **App line-of-business**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>Gruppi predefiniti Tutti gli utenti e Tutti i dispositivi per l'assegnazione di app Android for Work <!-- 1813073 -->
È possibile sfruttare i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi** per l'assegnazione di app Android for Work. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune reinstallerà le app richieste disinstallate dagli utenti <!-- 1947010 -->
Se un utente finale disinstalla un'app richiesta, Intune reinstalla automaticamente l'app entro 24 ore invece di attendere il ciclo di rivalutazione di 7 giorni.

### <a name="device-configuration"></a>Configurazione del dispositivo

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>Visualizzazione di tutti i dispositivi di un gruppo nel grafico dei profili e nell'elenco dello stato dei dispositivi <!-- 1449153 eeready -->
Quando si configura il profilo di un dispositivo (**Configurazione del dispositivo** > **Profili**), si sceglie il profilo del dispositivo, ad esempio iOS. Il profilo viene assegnato a un gruppo che include dispositivi iOS e non iOS. Il conteggio del grafico indica che il profilo viene applicato ai dispositivi iOS *e* non iOS (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**). Quando si seleziona il grafico nella scheda **Panoramica**, **Stato dispositivo** elenca tutti i dispositivi del gruppo, anziché solo i dispositivi iOS. 

Con questo aggiornamento, il grafico (**Configurazione del dispositivo** > **Profili** > selezionare un profilo esistente > **Panoramica**) visualizza solo il conteggio relativo al profilo dispositivo specifico. Se ad esempio il profilo di configurazione si applica ai dispositivi iOS, il grafico elencherà solo il conteggio dei dispositivi iOS. Selezionando il grafico e aprendo **Stato dispositivo** si vedranno elencati solo i dispositivi iOS.

In attesa di questo aggiornamento, il grafico utente è stato temporaneamente rimosso. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>VPN Always On per Windows 10 <!--1333666 -->

Attualmente, è possibile usare [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on) nei dispositivi Windows 10 tramite un profilo di rete privata virtuale (VPN, Virtual Private Network) personalizzato creato con un URI OMA.

Con questo aggiornamento, gli amministratori possono abilitare profili VPN Always On per Windows 10 direttamente in Intune nel portale di Azure. I profili VPN Always On si connetteranno automaticamente quando:

- Gli utenti accedono ai propri dispositivi
- La rete del dispositivo cambia
- Lo schermo del dispositivo si riattiva dopo essere stato disattivato

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>Nuove impostazioni della stampante per i profili di formazione <!-- 1308900 -->

Per i profili di formazione, le nuove impostazioni sono disponibili nella categoria **Stampanti**: **Stampanti**, **Stampante predefinita**, **Aggiungi nuove stampanti**.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>Visualizzare l'ID del chiamante nel profilo personale - Android for Work <!--1098984 -->
Quando si usa un profilo personale in un dispositivo, è possibile che gli utenti finali non visualizzino i dettagli dell'ID del chiamante da un contatto di lavoro. 

Dopo questo aggiornamento, sarà presente una nuova impostazione in **Android for Work** > **Limitazioni del dispositivo** > **Impostazioni del profilo di lavoro**:
- Visualizzare l'ID chiamante del contatto di lavoro nel profilo personale

Se abilitati (non configurati), i dettagli del chiamante del contatto di lavoro vengono visualizzati nel profilo personale. Se bloccato, il numero del chiamante del contatto di lavoro non viene visualizzato nel profilo personale. 

Si applica a: dispositivi di profilo di lavoro Android in sistemi operativi Android 6.0 e versioni successive

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nuove impostazioni di Windows Defender Credential Guard aggiunte alle impostazioni di Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Con questo aggiornamento, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configurazione del dispositivo** > **Profili** > **Endpoint Protection**) include le impostazioni seguenti: 

- **Windows Defender Credential Guard**: attiva Credential Guard con la sicurezza basata su virtualizzazione. Questa funzionalità, se abilitata, consente di proteggere le credenziali al riavvio successivo quando il **livello di sicurezza della piattaforma con avvio protetto** e la **sicurezza basata sulla virtualizzazione** sono entrambi abilitati. Le opzioni includono:
  - **Disabilitato**: se Credential Guard è stato attivato in precedenza con l'opzione **Abilitato senza blocco**, disattiva Credential Guard in modalità remota.

  - **Abilita con blocco UEFI**: garantisce che Credential Guard non possa essere disabilitato con una chiave del Registro di sistema o con Criteri di gruppo. Per disabilitare Credential Guard dopo avere usato questa impostazione, è necessario impostare Criteri di gruppo su "Disabilitato", quindi rimuovere la funzionalità di sicurezza da ogni computer, con un utente fisicamente presente. Questi passaggi cancellano la configurazione permanente in UEFI. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

  - **Abilita senza blocco**: consente di rimuovere Credential Guard in modalità remota usando Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 (versione 1511 o successiva).

Quando si configura Credential Guard vengono automaticamente abilitate le tecnologie dipendenti seguenti: 

  - **Abilita la sicurezza basata su virtualizzazione**: attiva la sicurezza basata su virtualizzazione al riavvio successivo. La sicurezza basata sulla virtualizzazione usa Windows Hypervisor per offrire il supporto per i servizi di sicurezza e richiede Avvio protetto.
  - **Avvio protetto con Direct Memory Access (DMA)**: attiva la sicurezza basata sulla virtualizzazione con Avvio protetto e Direct Memory Access. La protezione DMA richiede supporto hardware e viene abilitata solo nei dispositivi configurati correttamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Usare un nome oggetto personalizzato sul certificato SCEP <!-- 2064190 -->
È possibile usare **OnPremisesSamAccountName**, il nome comune in un oggetto personalizzato in un profilo certificato SCEP. È ad esempio possibile usare `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Bloccare la fotocamera e le acquisizioni di schermate in Android for Work <!-- 1098977 eeready-->
Sono disponibili due nuove proprietà di blocco utilizzabili durante la configurazione delle restrizioni per i dispositivi Android: 
- Fotocamera: blocca l'accesso a tutte le fotocamere del dispositivo
- Acquisizione schermo: blocca l'acquisizione di schermate e impedisce anche la visualizzazione del contenuto nei dispositivi di visualizzazione privi di output video protetto

Si applica ad Android for Work.


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nuovi passaggi di registrazione degli utenti per i dispositivi con macOS High Sierra 10.13.2 e versioni successive <!--1734567 -->
macOS high Sierra 10.13.2 ha introdotto il concetto di registrazione MDM "approvata dall'utente". Le registrazioni approvate consentono a Intune di gestire alcune impostazioni relative alla sicurezza. Per altre informazioni, vedere la documentazione del supporto Apple all'indirizzo https://support.apple.com/HT208019.

I dispositivi registrati tramite il portale aziendale macOS vengono considerati "approvati dall'utente" solo se l'utente finale apre Preferenze di Sistema e dichiara l'approvazione manualmente. A tal fine, il portale aziendale macOS ora indica agli utenti che usano macOS 10.13.2 e versioni successive di approvare manualmente la registrazione al termine dell'esecuzione di questa. La console di amministrazione di Intune indicherà se un dispositivo registrato è approvato dall'utente.



### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>Advanced Threat Protection (ATP) e Intune sono completamente integrati <!-- EEready 1629303 -->

[Advanced Threat Protection (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) indica il livello di rischio dei dispositivi Windows 10. In Windows Defender Security Center (portale ATP) è possibile creare una connessione a Microsoft Intune. Dopo averla creata, vengono usati i criteri di conformità di Intune per determinare un livello di minaccia accettabile. Se il livello di minaccia viene superato, i criteri di accesso condizionale di Azure Active Directory (AD) possono bloccare l'accesso a diverse app all'interno dell'organizzazione.

Questa funzionalità consente ad ATP di analizzare i file, rilevare le minacce e segnalare eventuali rischi nei dispositivi Windows 10.

Vedere [Abilitare ATP con l'accesso condizionale in Intune](advanced-threat-protection.md).

#### <a name="support-for-user-less-devices----1637553---"></a>Supporto per dispositivi senza utente associato <!-- 1637553 -->
Intune supporta la possibilità di valutare la conformità nei dispositivi senza utente associato, ad esempio Microsoft Surface Hub. I criteri di conformità potranno avere come destinazione dispositivi specifici. Sarà quindi possibile determinare la conformità (e la mancata conformità) dei dispositivi senza un utente associato.

#### <a name="delete-autopilot-devices----1713650---"></a>Eliminare dispositivi AutoPilot <!-- 1713650 -->
Gli amministratori di Intune possono [eliminare i dispositivi AutoPilot](enrollment-autopilot.md#delete-autopilot-devices).

#### <a name="improved-device-deletion-experience---1832333---"></a>Miglioramento dell'esperienza di eliminazione di dispositivi <!--1832333 -->
Non è più necessario rimuovere i dati aziendali o eseguire il ripristino delle impostazioni predefinite in un dispositivo prima di [eliminare quest'ultimo da Intune](devices-wipe.md#delete-devices-from-the-intune-portal).

Per visualizzare la nuova esperienza, accedere a Intune e selezionare **Dispositivi** > **Tutti i dispositivi** > nome del dispositivo > **Elimina**.

Se si vuole comunque la conferma di cancellazione/ritiro, è possibile usare il percorso standard del ciclo di vita del dispositivo tramite i comandi **Rimuovi i dati aziendali** e **Ripristino delle impostazioni predefinite** prima di **Elimina**. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>Riprodurre suoni in iOS in modalità di dispositivo perso <!-- 1947769 -->
Quando un dispositivo iOS sotto supervisione si trova in [Modalità di dispositivo perso](device-lost-mode.md) della gestione di dispositivi mobili (MDM), è possibile [riprodurre un suono](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) (**Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo iOS > **Panoramica** > **Altro**). Il suono continua finché la modalità di dispositivo perso non viene cambiata o un utente non disabilita il suono dal dispositivo. Si applica ai dispositivi iOS 9.3 e successivi.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Bloccare o consentire i risultati Web nelle ricerche eseguite in un dispositivo Intune <!--1972804-->

Gli amministratori ora possono bloccare i risultati Web dalle ricerche eseguite in un dispositivo.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Miglioramento della messaggistica per gli errori di caricamento del certificato push MDM Apple <!-- 2172331 -->

Il messaggio di errore spiega che per rinnovare un certificato MDM esistente è necessario usare lo stesso ID Apple.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>Testare il portale aziendale per macOS nelle macchine virtuali <!-- 2216679 -->

Sono state pubblicate indicazioni per consentire agli amministratori IT di testare l'app Portale aziendale per macOS su macchine virtuali in Parallels Desktop e VMware Fusion. Per altre informazioni, vedere [Registrare le macchine virtuali macOS per i test](macos-enroll.md#enroll-virtual-macos-machines-for-testing).


### <a name="user-interface"></a>Interfaccia utente

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Sono stati migliorati i riquadri del dispositivo nel portale aziendale di Windows 10 <!--2213364 -->

I riquadri sono stati aggiornati per essere più accessibili agli utenti con problemi di ipovisione e per offrire prestazioni migliori per gli strumenti di lettura dello schermo.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>Inviare report di diagnostica nell'app Portale aziendale per macOS <!-- 2216677 -->
L'app Portale aziendale per i dispositivi macOS è stata aggiornata per migliorare la modalità di segnalazione degli errori correlati a Intune. Dall'app Portale aziendale gli utenti possono:

- Caricare i report di diagnostica direttamente al team di sviluppo Microsoft.
- Inviare tramite posta elettronica l'ID evento imprevisto al team di supporto IT della società.

Per altre informazioni, vedere [Inviare gli errori per macOS](/intune-user-help/send-errors-macos).

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Intune si adatta a Fluent Design System nell'app Portale aziendale per Windows 10 <!-- 1195010 WNready -->
L'app Portale aziendale Intune per Windows 10 è stata aggiornata con la [visualizzazione della navigazione di Fluent Design System](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics). A lato dell'app si noterà un elenco verticale statico di tutte le pagine di primo livello. Fare clic su un collegamento per visualizzare rapidamente tutte le pagine e passare da una all'altra. Questo è il primo di molti aggiornamenti che saranno resi disponibili come parte del continuo impegno per creare un'esperienza più adattiva, empatica e familiare in Intune. Per visualizzare l'aspetto aggiornato, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Settimana del 16 aprile 2018

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>Usare il client Cisco AnyConnect per iOS <!-- EEready 1333708 -->

Quando si crea un nuovo profilo VPN per iOS, ora sono disponibili due opzioni: **Cisco AnyConnect** e **Cisco Legacy AnyConnect**. I profili di Cisco AnyConnect supportano le versioni 4.0.7x e successive. I profili VPN di Cisco AnyConnect per iOS esistenti vengono contrassegnati con la dicitura **Cisco Legacy AnyConnect** e continuano a funzionare con Cisco AnyConnect 4.0.5x e versioni precedenti come accade oggi.

> [!NOTE]
> Questa modifica si applica solo a iOS. Continua a esistere una sola opzione Cisco AnyConnect per le piattaforme Android, Android for Work e macOS.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>I dispositivi macOS registrati in Jamf ora possono essere registrati con Intune <!-- 2370684 -->

Le versioni 1.3 e 1.4 del portale aziendale di macOS non registravano correttamente i dispositivi Jamf con Intune. Questo problema è stato risolto con la versione 1.4.2 del portale di macOS.


## <a name="week-of-april-9-2018"></a>Settimana del 9 aprile 2018  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Esperienza Guida aggiornata nell'app Portale aziendale per Android <!-- 1631531 -->

L'esperienza Guida nell'app Portale aziendale per Android è stata aggiornata e adattata alle procedure consigliate per la piattaforma Android. Ora quando si verifica un problema nell'app, gli utenti possono toccare **Menu** > **Guida** e:
- Caricare i log di diagnostica in Microsoft.
- Inviare un messaggio di posta elettronica con la descrizione del problema e l'ID evento imprevisto a un addetto del supporto aziendale.  

Per provare l'esperienza Guida aggiornata, vedere [Inviare i log tramite posta elettronica](/intune-user-help/send-logs-to-your-it-admin-by-email-android) e [Inviare gli errori a Microsoft](/intune-user-help/send-logs-to-microsoft-android).


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>Nuovo grafico di tendenza degli errori di registrazione e tabella dei motivi degli errori <!-- 1471783 -->

Nella pagina di panoramica delle registrazioni è possibile visualizzare la tendenza degli errori di registrazione e le prime cinque cause di errore. Facendo clic sul grafico o sulla tabella è possibile espandere i dettagli per trovare consigli sulla risoluzione dei problemi e suggerimenti per la correzione.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>Aggiornare la posizione di configurazione dei criteri di protezione delle app <!-- 2144597 -->

Nel portale di Azure all'interno del servizio Microsoft Intune verrà eseguito un reindirizzamento temporaneo dal pannello del servizio **Protezione app di Intune** al pannello **App per dispositivi mobili**. Si noti che tutti i criteri di protezione delle app sono già nel pannello **App per dispositivi mobili** in Intune sotto la configurazione delle app. Invece di andare a Protezione app di Intune, si passerà a Intune. Ad aprile 2018 il reindirizzamento verrà arrestato e il pannello del servizio **Protezione app di Intune** verrà completamente rimosso. All'interno di Intune sarà quindi disponibile una sola posizione per i criteri di protezione delle app. 

**Quali sono le conseguenze di questa modifica?**
Questa modifica avrà effetto sia sui clienti di Intune autonomi che sui clienti ibridi (Intune con Configuration Manager). Questa integrazione consentirà di semplificare l'amministrazione della gestione del cloud.

**Operazioni di preparazione alla modifica**
Contrassegnare come preferito **Intune** anziché il pannello del servizio **Protezione app di Intune** e assicurarsi di avere dimestichezza con il flusso di lavoro Criterio di protezione dell'app nel pannello **App per dispositivi mobili** all'interno di Intune. Il reindirizzamento durerà per un breve periodo di tempo e quindi il pannello **Protezione app** verrà rimosso. Tenere presente che tutti i criteri di protezione delle app sono già presenti in Intune ed è possibile modificare tutti i criteri di accesso condizionale. Per altre informazioni sulla modifica dei criteri di accesso condizionale, vedere [Accesso condizionale in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>Settimana del 2 aprile 2018

### <a name="intune-apps"></a>App di Intune

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>Aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS <!--1412866 -->
È stato rilasciato un importante aggiornamento dell'esperienza utente per l'app Portale aziendale per iOS. L'aggiornamento prevede una riprogettazione visiva completa che include un aspetto visivo e una modalità di interazione più moderni. È stata mantenuta la funzionalità dell'app aumentando la facilità di utilizzo e l'accessibilità.  

Saranno inoltre disponibili:
- Supporto per iPhone X.
- Avvio delle app e caricamento più veloci per consentire agli utenti di risparmiare tempo.
- Indicatori di stato aggiuntivi per offrire agli utenti le informazioni sullo stato più aggiornate.
- Miglioramenti della modalità di caricamento dei log. Se si verificano problemi, è più semplice segnalarlo.  

Per visualizzare l'aspetto aggiornato, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Proteggere i dati di Exchange locali usando i criteri di protezione delle app e l'accesso condizionale di Intune <!-- 1056954 -->
È ora possibile usare i criteri di protezione delle app e l'accesso condizionale di Intune per proteggere l'accesso ai dati di Exchange locali con Outlook Mobile. Per aggiungere o modificare i criteri di protezione delle app nel portale di Azure, selezionare **Microsoft Intune** > **App per dispositivi mobili** > **Criteri di protezione delle app**. Prima di usare questa funzionalità, assicurarsi che siano soddisfatti i [requisiti di Outlook per iOS e Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="week-of-march-26-2018"></a>Settimana del 26 marzo 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Avvisi per le app line-of-business (LOB) iOS per Microsoft Intune <!-- 748789 -->

Intune segnala nel portale di Azure le app line-of-business iOS che stanno per scadere. Dopo che una nuova versione dell'app line-of-business iOS è stata caricata, Intune rimuove la notifica di scadenza dall'elenco delle app. La notifica di scadenza sarà attiva solo per le app line-of-business iOS caricate di recente. Viene visualizzato un avviso 30 giorni prima della scadenza del profilo di provisioning dell'app line-of-business iOS. Dopo la scadenza, l'avviso viene sostituito dall'indicazione Scaduto.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>Personalizzare i temi del portale aziendale con codici esadecimali <!--1049561 -->

È possibile personalizzare il colore del tema nelle app Portale aziendale usando codici esadecimali. Quando si immette il codice esadecimale, Intune determina il colore del testo che offre il livello di contrasto massimo tra colore del testo e colore di sfondo. È possibile visualizzare in anteprima un confronto tra il colore del testo e il logo della società e il colore in **App per dispositivi mobili** > **Portale aziendale**.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Inclusione ed esclusione dell'assegnazione delle app in base ai gruppi per Android Enterprise <!-- 1813081 -->

Android Enterprise (denominato in precedenza Android for Work) supporta l'inclusione e l'esclusione di gruppi, ma non supporta i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi**. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).


### <a name="device-management"></a>Gestione dei dispositivi

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

Per altre informazioni su questi canali, vedere [Gestire le build Insider Preview](https://insider.windows.com/en-us/for-business-organization-admin/).   
Per altre informazioni sulla creazione di canali di distribuzione in Intune, vedere [Gestire gli aggiornamenti software](windows-update-for-business-configure.md).

### <a name="intune-apps"></a>App di Intune

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

## <a name="week-of-march-19-2018"></a>Settimana del 19 marzo 2018

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>Esportare tutti i dispositivi in file CSV in Internet Explorer, Edge o Chrome <!-- 2258071 -->
In **Dispositivi** > **Tutti i dispositivi** è possibile **esportare** i dispositivi in un elenco in formato CSV. Gli utenti di Internet Explorer (IE) con più di 10.000 dispositivi possono esportare i propri dispositivi in più file. Ogni file include fino a 10.000 dispositivi.

Gli utenti di Edge e Chrome con più di 30.000 dispositivi possono esportare i propri dispositivi in più file. Ogni file include fino a 30.000 dispositivi.

[Gestire dispositivi](device-management.md) offre ulteriori dettagli sulle operazioni eseguibili con i dispositivi gestiti.

## <a name="week-of-march-12-2018"></a>Settimana del 12 marzo 2018

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>I siti Web di Azure Active Directory possono richiedere l'app Intune Managed Browser e supportano Single Sign-On per Managed Browser (anteprima pubblica) <!-- 710595 -->

Tramite Azure Active Directory (Azure AD) è ora possibile limitare l'accesso ai siti Web nei dispositivi mobili all'app Intune Managed Browser. In Managed Browser i dati dei siti Web rimangono protetti e separati dai dati personali dell'utente finale. Inoltre, Managed Browser supporta le funzionalità Single Sign-On per i siti protetti da Azure AD. L'accesso a Managed Browser o l'uso di Managed Browser in un dispositivo con un'altra app gestita da Intune consente a Managed Browser di accedere ai siti aziendali protetti da Azure AD senza richiedere l'immissione delle credenziali da parte dell'utente. Questa funzionalità si applica a siti come Outlook Web Access (OWA) e SharePoint Online e ad altri siti aziendali come le risorse Intranet a cui si ha accesso tramite il proxy app di Azure. Per altre informazioni, vedere [Controlli di accesso nell'accesso condizionale di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls).

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Aggiornamenti di elementi visivi nell'app Portale aziendale per Android <!--976944 -->

L'app Portale aziendale per Android è stata aggiornata e resa conforme alle linee guida di Android [Material Design](https://material.io/). È possibile visualizzare le immagini delle nuove icone nell'articolo [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

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

## <a name="week-of-february-19-2018"></a>Settimana del 19 febbraio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Supporto di Intune per più account DEP Apple/Apple School Manager <!-- 747685 -->

Intune supporta ora la registrazione di dispositivi da un massimo di 100 account [Apple Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) o [Apple School Manager](apple-school-manager-set-up-ios.md) diversi. Ogni token caricato può essere gestito separatamente per i profili di registrazione e i dispositivi. Un profilo di registrazione diverso può essere assegnato automaticamente a ogni token DEP/School Manager caricato. Se vengono caricati più token School Manager, solo uno alla volta può essere condiviso con Microsoft School Data Sync.

Dopo la migrazione, le API Graph beta e gli script pubblicati per la gestione di Apple DEP o ASM tramite Graph non funzioneranno. Sono in corso di sviluppo nuove API Graph beta, che verranno rilasciate dopo la migrazione.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>Visualizzare le restrizioni di registrazione per i singoli utenti <!-- 1634444 eeready wnready -->
Nel pannello **Risoluzione dei problemi** è ora possibile visualizzare le [restrizioni di registrazione](enrollment-restrictions-set.md) applicate per ogni utente selezionando **Restrizioni registrazione** nell'elenco **Assegnazioni**.

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

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Nuove impostazioni per il browser Microsoft Edge <!--1469166 -->
Sono ora disponibili [due nuove impostazioni](device-restrictions-windows-10.md#edge-browser) per il **percorso del file dei Preferiti** e le **modifiche a Preferiti** per i dispositivi con browser Microsoft Edge.

### <a name="app-management"></a>Gestione delle app
#### <a name="protocol-exceptions-for-applications---1035509---"></a>Eccezioni di protocollo per le applicazioni <!--1035509 -->

Ora è possibile creare eccezioni ai criteri di trasferimento dati della gestione di applicazioni mobili (MAM) di Intune per aprire specifiche applicazioni non gestite. Le applicazioni devono essere considerate attendibile da IT. A differenza delle eccezioni create, il trasferimento dati rimane limitato alle applicazioni gestire da Intune quando i criteri di trasferimento dati sono impostati **solo per le app gestite**. È possibile creare le restrizioni tramite protocolli (iOS) o pacchetti (Android).

Ad esempio, è possibile aggiungere il pacchetto Webex come eccezione ai criteri di trasferimento dati MAM. In questo modo i collegamenti Webex in un messaggio di posta elettronica di Outlook gestito possono essere aperti direttamente nell'applicazione Webex. Il trasferimento dati rimarrà limitato nelle altre applicazioni non gestite. Per altre informazioni, vedere [Eccezioni dei criteri di trasferimento dei dati per le app](app-protection-policies-exception.md).

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Dati crittografati di Windows Information Protection (WIP) nei risultati di ricerca di Windows <!-- 1469193 -->
Un'impostazione nei criteri di Windows Information Protection (WIP) consente ora di controllare se i dati crittografati WIP vengono inclusi nei risultati di ricerca di Windows. Impostare questa opzione dei criteri di protezione dell'app selezionando l'impostazione che **consente all'indicizzatore di Ricerca di Windows di cercare gli elementi crittografati** nelle **impostazioni avanzate** dei criteri di Windows Information Protection. I criteri di protezione dell'app devono essere impostati sulla piattaforma *Windows 10* e lo **stato di registrazione** dei criteri dell'app deve essere impostato su **Con registrazione**. Per altre informazioni, vedere [Consentire all'indicizzatore di Ricerca di Windows di cercare elementi crittografati](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items).

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>Configurazione di un'app MSI per dispositivi mobili con aggiornamento automatico <!-- 1740840 -->
È possibile configurare un'app MSI per dispositivi mobili con aggiornamento automatico nota in modo che ignori il processo di controllo delle versioni. Questa funzionalità consente di evitare una race condition. Ad esempio, questo tipo di race condition può verificarsi quando l'app viene aggiornata automaticamente dallo sviluppatore di app e anche da Intune. In entrambi i casi è possibile che si tenti di imporre una versione dell'app in un client di Windows creando un conflitto. Per queste app MSI con aggiornamento automatico, è possibile configurare l'impostazione **Ignora la versione dell'app** nel pannello **Informazioni sull'app**. Se questa impostazione viene cambiata in **Sì**, Microsoft Intune ignorerà la versione dell'app installata nel client Windows.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Insiemi correlati di licenze per le app supportati in Intune <!-- 1864117 -->
Intune nel portale di Azure ora supporta gli insiemi correlati di licenze per le app come elemento app singolo nell'interfaccia utente. Inoltre, tutte le app con licenza offline sincronizzate da Microsoft Store per le aziende verranno consolidate in una singola voce di app e verrà eseguita la migrazione di tutti i dettagli di distribuzione dei singoli pacchetti nella singola voce. Per visualizzare gli insiemi correlati di licenze per le app nel portale di Azure, selezionare **Licenze dell'app** dal pannello **App per dispositivi mobili**.

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


### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli
### <a name="intune-apps"></a>App di Intune
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>Supporto per le app offline da Microsoft Store per le aziende <!--1222672-->
Le app offline acquistate da Microsoft Store per le aziende ora vengono sincronizzate nel portale di Azure. È quindi possibile distribuire le app ai gruppi di dispositivi o ai gruppi di utenti. Le app offline vengono installate da Intune, non dallo Store.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>Impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro <!-- 1728700 -->

Quando si distribuisce l'app Gmail in un profilo Android for Work, è ora possibile impedire agli utenti finali di aggiungere o rimuovere manualmente account nel profilo di lavoro usando l'impostazione **Aggiungi o rimuovi account** nel profilo delle restrizioni per dispositivi Android for Work.

## <a name="week-of-february-5-2018"></a>Settimana del 5 febbraio 2018

### <a name="device-enrollment"></a>Registrazione del dispositivo

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

## <a name="week-of-january-29-2018"></a>Settimana del 29 gennaio 2018

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


## <a name="week-of-january-22-2018"></a>Settimana del 22 gennaio 2018

### <a name="intune-apps"></a>App di Intune

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Nuove funzionalità per l'azione "Risolvi" per i dispositivi Android <!--1583480-->

L'app Portale aziendale per Android sta estendendo l'azione "Risolvi" di **Aggiorna impostazioni del dispositivo** in modo da risolvere i [problemi di crittografia del dispositivo](/intune-user-help/encrypt-your-device-android).

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Blocco remoto disponibile nell'app Portale aziendale per Windows 10 <!--676506-->
Gli utenti possono ora bloccare i dispositivi in modalità remota dall'app Portale aziendale per Windows 10. L'opzione non verrà visualizzata per il dispositivo locale in uso.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Risoluzione dei problemi di conformità più facile per l'app Portale aziendale per Windows 10 <!--676546-->
Gli utenti finali con dispositivi Windows potranno toccare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema.

## <a name="week-of-december-11-2017"></a>Settimana del 11 dicembre 2017

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

## <a name="week-of-december-4-2017"></a>Settimana del 4 dicembre 2017

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune supporta le app non consentite di Windows Information Protection (WIP) <!-- 1479103 -->
È possibile specificare app non consentite in Intune. Le app non consentite non possono accedere alle informazioni aziendali e si tratta in effetti della condizione opposta alle app incluse nell'elenco delle app consentite. Per altre informazioni, vedere la [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Elenco consigliato delle app non consentite per Windows Information Protection).



## <a name="notices"></a>Notifiche

### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>Modifiche pianificate: Intune supporterà iOS 10 e versioni successive a settembre <!-- 2454656 -->
Nel mese di settembre è previsto il rilascio di iOS 12 di Apple. Poco dopo il rilascio, verrà effettuata la transizione del servizio di registrazione di Intune, dell'app Portale aziendale e di Managed Browser per il supporto di iOS 10 e versioni successive.  

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?  
Le app per dispositivi mobili di Office 365 sono supportate in iOS 10 e versioni successive, quindi è probabile che il sistema operativo o i dispositivi siano già stati aggiornati. In questo caso, questa transizione non avrà alcun impatto.  

Tuttavia, con i dispositivi inclusi nell'elenco seguente o se si vuole registrare un dispositivo tra quelli elencati, tenere presente che questi supportano solo iOS 9 e versioni precedenti.  Per continuare ad accedere al Portale aziendale Intune, è necessario aggiornare questi dispositivi entro settembre a dispositivi che supportano iOS 10 o versioni successive:  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad (terza generazione)  
* iPad Mini (prima generazione)  

A partire da luglio, nei dispositivi registrati in MDM con iOS 9 e il Portale aziendale verrà visualizzato un messaggio di avviso per l'aggiornamento del sistema operativo o del dispositivo. Se si usano criteri di protezione delle app, è anche possibile impostare l'impostazione di accesso "Richiedi un sistema operativo iOS minimo (solo avviso)".  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica   
Verificare se nell'organizzazione sono presenti dispositivi o utenti interessati. In Intune nel portale di Azure passare a Dispositivi > Tutti i dispositivi e filtrare in base al sistema operativo.  Fare clic su Colonne per visualizzare i dettagli, ad esempio la versione del sistema operativo. Richiedere agli utenti di aggiornare i dispositivi a una versione supportata del sistema operativo prima di settembre.  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>Modifica prevista: passaggio di Intune a TLS 1.2
A partire dal 31 ottobre 2018, Intune supporterà la versione 1.2 del protocollo Transport Layer Security (TLS) per fornire la crittografia migliore, assicurarsi che il servizio sia più sicuro per impostazione predefinita e allinearsi ad altri servizi Microsoft, come Microsoft Office 365. Office ha comunicato questa modifica in MC128929.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
A partire dal 31 ottobre 2018, Intune non supporterà più le versioni 1.0 o 1.1 del protocollo TLS. Tutte le combinazioni di client-server e browser-server devono usare TLS versione 1.2 per garantire una connessione senza problemi a Intune. Si noti che questa modifica influirà sui dispositivi degli utenti finali non più supportati da Intune, ma che ancora ricevono criteri tramite Intune, e che non possono usare TLS versione 1.2. Ad esempio, sono inclusi i dispositivi che eseguono Android 4.3 e versioni precedenti. Per un elenco di dispositivi e browser, vedere Informazioni aggiuntive più avanti.

Dopo il 31 ottobre 2018, se si riscontra un problema relativo all'uso di una versione TLS precedente, verrà richiesto di eseguire l'aggiornamento a TLS 1.2 o a un dispositivo che supporti TLS 1.2 come parte della risoluzione.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
È consigliabile rimuovere in modo proattivo le dipendenze da TLS 1.0 e 1.1 negli ambienti e disabilitare TLS 1.0 e 1.1 a livello di sistema operativo, laddove possibile. Iniziare al più presto a pianificare la migrazione a TLS 1.2. Controllare il post di blog di supporto di seguito per l'elenco dei dispositivi che non sono attualmente supportati da Intune, ma che potrebbero comunque ricevere criteri e quindi non saranno in grado di comunicare tramite TLS versione 1.2. Potrebbe essere necessario segnalare a questi utenti finali che perderanno l'accesso alle risorse aziendali.

**Informazioni aggiuntive**: [Passaggio di Intune a TLS 1.2 per la crittografia](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>Piano di modifica: Nuova impostazione di Windows 10 per la configurazione della modalità a tutto schermo in Intune <!-- 1560072 -->
Verrà modificata la modalità e la posizione in cui configurare i desktop Windows 10 versione 1709 e successive (RS3 e successive) nel portale di Azure di Intune.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica? 
I dati registrati indicano che si sta usando l'impostazione Windows 10 > Limitazioni del dispositivo > Modalità tutto schermo (anteprima). In maggio l'impostazione verrà rinominata Windows 10 > Limitazioni del dispositivo > Modalità tutto schermo (obsoleto) nell'interfaccia utente a indicare che non ne è più consigliato l'utilizzo. L'impostazione continuerà tuttavia a funzionare fino all'aggiornamento di luglio di Intune. Quindi, verrà resa obsoleta nel back-end e non funzionerà più. In alternativa, verrà rilasciato in maggio un nuovo profilo di configurazione dei dispositivi: Windows 10 > Modalità tutto schermo contenente le impostazioni per la configurazione delle modalità a tutto schermo in Windows 10 RS4 e versioni successive.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica  
Quando Intune rilascerà l'aggiornamento del servizio alla fine del mese di maggio, verranno rese disponibili le istruzioni per testare e verificare la possibilità di eseguire la migrazione della configurazione della modalità a tutto schermo da Windows 10 RS3 a Windows 10 RS4. Usare queste istruzioni per configurare i dispositivi usando il nuovo profilo di configurazione dei dispositivi per le modalità a tutto schermo.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Questa modifica interesserà sia i clienti Intune autonomi che ibridi (clienti Intune con Configuration Manager). Questa integrazione contribuirà alla semplificazione dell'amministrazione della gestione del cloud. Sarà sufficiente un solo pannello in Azure, il pannello Intune, per gestire gruppi, criteri e app, nonché per la gestione di tutti i dispositivi mobili.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Contrassegnare come preferito il pannello Intune anziché il pannello del servizio Protezione app di Intune e assicurarsi di avere dimestichezza con il flusso di lavoro Criterio di protezione dell'app nel pannello App per dispositivi mobili all'interno di Intune. Il reindirizzamento durerà per un breve periodo di tempo e quindi il pannello Protezione app verrà rimosso. Tenere presente che tutti i criteri di protezione delle app sono già presenti in Intune ed è possibile modificare tutti i criteri di accesso condizionale seguendo la documentazione disponibile qui: [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca).

**Informazioni aggiuntive**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>Modifiche pianificate: modifica del supporto del plug-in Cordova per Microsoft Intune App SDK
Intune terminerà il supporto per il [plug-in Cordova per Microsoft Intune App SDK](app-sdk-cordova.md) il 1 maggio 2018. È consigliabile usare invece lo strumento di wrapping delle app di Intune per preparare le app basate su Cordova per la gestibilità e la disponibilità in Intune. Quando questa modifica diventerà effettiva, non sarà più eseguita la gestione del plug-in Cordova per Microsoft Intune App SDK né si riceveranno aggiornamenti. Gli sviluppatori di App non potranno usare questo plug-in. Intune intende continuare a supportare le app create con Cordova. Tuttavia, tutte le app create con il plug-in Cordova per Microsoft Intune App SDK subiranno una riduzione delle funzionalità in Intune. Dopo il wrapping con lo strumento di wrapping delle app di Intune, le app possono essere distribuite agli utenti finali nel modo usuale. Per le app Android basate su Cordova rilasciate in Google Play Store:
- Al primo avvio agli utenti finali verranno chieste le credenziali ricevere i criteri di Intune.
- Le app dovranno essere rilasciate nell'App Store destinato agli utenti di Intune, ad esempio "App Contoso per Intune".

Per altre informazioni sullo strumento di wrapping delle app, vedere [Strumento di wrapping delle app per iOS](app-wrapper-prepare-ios.md) e [Strumento di wrapping delle app per Android](app-wrapper-prepare-android.md). Per problemi o domande, contattare [ msintuneappsdk@microsoft.com ](mailto:msintuneappsdk@microsoft.com).

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>Pianificare per il cambiamento: iniziare a usare Intune in Azure per la gestione MDM <!-- 1227338 -->
Oltre un anno fa è stata annunciata l'[anteprima pubblica di Intune in Azure](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/) a cui è seguita, sei mesi fa, la [disponibilità generale della nuova esperienza amministrativa](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/) per Intune. A partire dal 31 agosto 2018, la gestione dei dispositivi mobili (MDM, Mobile Device Management) verrà disattivata nella console di Silverlight classica per i clienti che usano la versione autonoma di Intune. Per le esigenze MDM sarà invece possibile usare [Intune in Azure](https://aka.ms/Intune_on_Azure). È consigliabile che i clienti che usano ancora la console classica per MDM inizino ad acquisire familiarità con Intune in Azure. Questo cambiamento non avrà alcun impatto sull'utente finale. La gestione dei PC classica rimarrà in Silverlight. Altre informazioni su questo cambiamento e sui relativi effetti sono disponibili [qui](https://aka.ms/Intune_on_Azure_mdm).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima della registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiedono un'unica migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere al portale di Azure, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

## <a name="whats-coming"></a>Sviluppi futuri

### <a name="local-device-security-option-settings----1251887---"></a>Impostazioni delle opzioni di sicurezza dei dispositivi locali <!-- 1251887 -->
Sarà possibile abilitare le impostazioni di sicurezza sui dispositivi Windows 10 usando le nuove impostazioni delle opzioni di sicurezza dei dispositivi locali. Queste impostazioni sono disponibili nella categoria Endpoint Protection durante la creazione dei criteri di configurazione dei dispositivi Windows 10.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>Nuova esperienza utente per il sito Web del portale aziendale <!--2000968-->

A partire da agosto verrà introdotta una nuova esperienza per il sito Web del portale aziendale, con aggiornamenti dell'interfaccia utente, flussi di lavoro semplificati e miglioramenti all'accessibilità. La nuova esperienza includerà miglioramenti proposti dai clienti, come la condivisione delle app e prestazioni migliorate in generale per offrire un'esperienza più semplice.
Sono state aggiunte alcune nuove funzionalità, in base ai suggerimenti dei clienti, ad esempio, che miglioreranno significativamente l'usabilità e le funzionalità esistenti:

* Miglioramenti dell'interfaccia utente in tutto il sito Web
* Possibilità di condividere collegamenti diretti alle app
* Miglioramento delle prestazioni per i cataloghi di app di grandi dimensioni

Non è necessario eseguire alcuna azione per prepararsi per queste modifiche. Si riceverà una notifica quando il sito Web del portale aziendale aggiornato diventa disponibile. Tuttavia, potrebbe essere eventualmente necessario aggiornare la documentazione per gli utenti finali con screenshot aggiornati. Si noti che potrebbe anche essere necessario aggiornare la documentazione per l'app Portale aziendale in iOS, perché il sito Web è alla base della sezione **App** dell'app iOS. È possibile visualizzare un'immagine di esempio nelle [novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->
Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. I dettagli saranno disponibili nel [blog del supporto di Intune](https://aka.ms/compportalats).



## <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](https://www.microsoft.com/cloud-platform/roadmap)
* [What's new in the Company Portal UI](whats-new-app-ui.md) (Novità nell'interfaccia utente del portale aziendale)
* [Novità dei mesi precedenti](whats-new-archive.md)
