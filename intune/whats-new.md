---
title: Novità di Microsoft Intune - Azure | Microsoft Docs
titlesuffix: ''
description: Informazioni sulle novità nel portale di Intune di Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 996b4d85da41b480d73d7a79011e2bbd732ea334
ms.sourcegitcommit: dde9e1e1d15c412751a186410c2a04974ff1b102
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690836"
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre a indicazioni su modifiche previste, [notifiche importanti](#notices) e informazioni su [versioni precedenti](whats-new-archive.md). 

> [!Note]
> Alcune funzionalità potrebbero essere implementate nel corso di settimane e potrebbero non essere disponibili a tutti i clienti nella prima settimana.
>
> Per informazioni sulle nuove funzionalità di gestione dei dispositivi mobili (MDM) ibrida, vedere la [pagina Novità della gestione di dispositivi mobili ibrida](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->     
## <a name="week-of-february-4-2019"></a>Settimana del 4 febbraio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-macos-company-portal-dark-mode----3300524-eeready---"></a>Modalità scura del portale aziendale Intune per macOS <!-- 3300524 eeready -->
Il portale aziendale Intune ora supporta la modalità scura per macOS. Quando si abilita la modalità scura in un dispositivo macOS 10.14 o versione successiva, il Portale aziendale regola i colori in modo da riflettere tale modalità.

## <a name="week-of-january-21-2019"></a>Settimana del 21 gennaio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Notifiche di tipo avviso popup per app Win32 <!-- 3136566   -->
È possibile eliminare la visualizzazione delle notifiche di tipo avviso popup degli utenti finali per ogni assegnazione di app. In Intune selezionare **App client** > **App** > selezionare l'app > **Assegnazioni** > **Includi gruppi**. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Aggiornamento dell'interfaccia utente dei criteri di protezione delle app di Intune <!-- 3251427  -->
Sono state modificate le etichette per le impostazioni e i pulsanti per la protezione delle app di Intune per rendere tutto più comprensibile. Alcune delle modifiche includono:  
- I controlli sono cambiati da **sì** / **no** principalmente a **blocca** / **consenti** e **disabilita** / **abilita**. Anche le etichette sono state aggiornate.  
- Le impostazioni sono state riformattate, in modo che l'impostazione e la relativa etichetta siano affiancate nel controllo, consentendo spostamenti più efficienti.   

Le impostazioni predefinite e il numero di impostazioni rimangono uguali, ma questa modifica consente all'utente di comprendere, esplorare e utilizzare le impostazioni più facilmente per applicare i criteri di protezione delle app selezionati. Per informazioni, vedere le [impostazioni iOS](app-protection-policy-settings-ios.md) e le [impostazioni Android](app-protection-policy-settings-android.md).

#### <a name="additional-settings-for-outlook----3301182----"></a>Impostazioni aggiuntive per Outlook<!-- 3301182  -->
Ora è possibile configurare le impostazioni aggiuntive seguenti per Outlook per iOS e Android usando Intune:
- Consentire solo agli account aziendali o dell'istituto di istruzione di essere usati in Outlook su iOS o Android
- Distribuire gli account locali dell'autenticazione moderna per Office 365 e dell'autenticazione moderna ibrida
- Usare `SAMAccountName` per il campo nome utente nel profilo di posta elettronica quando è selezionata l'autenticazione di base

Le impostazioni seguenti sono ancora in corso di implementazione graduale e saranno presto disponibili nella console:
- Consentire di salvare i contatti
- Configurare i suggerimenti di posta elettronica per i destinatari esterni
- Configurare **Posta in arrivo evidenziata**
- Richiedere alla biometria di accedere a Outlook per iOS

L'impostazione seguente viene visualizzata nella console di Intune, ma una volta configurata non funzionerà come previsto. Questo problema verrà risolto a breve:
- Bloccare le immagini esterne

> [!NOTE]
> Se si usano i criteri di protezione delle app di Intune per gestire l'accesso per le identità aziendali, non abilitare **Richiedi biometria**. Per altre informazioni, vedere **Richiedi credenziali aziendali per l'accesso** per le [impostazioni di accesso iOS](app-protection-policy-settings-ios.md#access-requirements) e le [impostazioni di accesso Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="delete-android-enterprise-apps----1352553---"></a>Eliminare app Android Enterprise <!-- 1352553 -->
È possibile eliminare da Microsoft Intune le app di Google Play gestite. Per eliminare un'app di Google Play gestita, aprire Microsoft Intune nel portale di Azure e selezionare **App client** > **App**. Nell'elenco di app selezionare i puntini di sospensione (...) a destra dell'app di Google Play gestita e quindi selezionare **Elimina** nell'elenco visualizzato. Quando si elimina un'app di Google Play gestita dall'elenco di app, l'app risulta automaticamente non approvata.

#### <a name="managed-google-play-app-type----1352580---"></a>Tipo di app Google Play gestito <!-- 1352580 -->
Il tipo di app **Google Play gestito** consentirà di aggiungere in modo specifico [app Google Play gestite](https://play.google.com/work/search?q=microsoft&c=apps) a Intune. Un amministratore di Intune può ora esplorare, cercare, approvare, sincronizzare e assegnare in Intune app di Google Play gestite approvate.  Non sarà più necessario passare alla console di Google Play separatamente e rieseguire l'autenticazione.  In Intune selezionare **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di App** selezionare **Google Play gestito** come tipo di app.

### <a name="default-android-pin-keyboard----3802457---"></a>Tastiera PIN predefinita in Android <!-- 3802457 -->
Gli utenti finali che hanno impostato un PIN di tipo 'Numerico' dei criteri di protezione delle app in Intune sui loro dispositivi Android visualizzeranno ora la tastiera Android predefinita invece dell'interfaccia utente della tastiera Android fissa progettata in precedenza. Questa modifica è stata apportata per coerenza quando si usano tastiere predefinite in Android e iOS, per entrambi i tipi PIN di 'Numerico' e/o 'Passcode'. Per altre informazioni sulle impostazioni di accesso degli utenti finali in Android, ad esempio il PIN dei criteri di protezione delle app, vedere la sezione relativa ai [requisiti di accesso Android](app-protection-policy-settings-android.md#access-requirements).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>Usare le impostazioni consigliate da Microsoft con le baseline di sicurezza (anteprima pubblica) <!-- 2055484   -->

Intune si integra con altri servizi specifici per la sicurezza, inclusi Windows Defender ATP e Office 365 ATP. I clienti manifestano l'esigenza di una strategia comune e di un set integrato di flussi di lavoro di sicurezza end-to-end nei servizi di Microsoft 365. L'obiettivo è l'allineamento delle strategie per creare soluzioni in grado di conciliare le operazioni di sicurezza e le comuni attività degli amministratori. Per realizzare questo obiettivo in Intune, è stato pubblicato un set di "baseline di sicurezza" consigliate da Microsoft (**Intune** > **Baseline di sicurezza**).  Un amministratore può creare criteri di sicurezza direttamente da queste baseline e quindi distribuirle agli utenti. È anche possibile personalizzare le raccomandazioni per le procedure consigliate in modo soddisfare le specifiche esigenze dell'organizzazione. Intune verifica che i dispositivi rimangano conformi a queste baseline e invia agli amministratori una notifica sugli utenti e i dispositivi non conformi.

Questa funzionalità è disponibile in anteprima pubblica, perciò i profili di nuova creazione non verranno spostati nei modelli di baseline di sicurezza disponibili a livello generale. Non è consigliabile usare questi modelli di anteprima nell'ambiente di produzione.

Per altre informazioni sulle baseline di sicurezza, vedere [Creare una baseline di sicurezza di Windows 10 in Intune](security-baselines-monitor.md).

Questa funzionalità si applica a: Windows 10 e versioni successive

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>I non amministratori possono abilitare BitLocker nei dispositivi Windows 10 aggiunti ad Azure AD<!-- 2147379   -->
Quando si abilitano le impostazioni di BitLocker nei dispositivi Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo**  >  **Windows 10 e versioni successive** per la piattaforma > **Endpoint Protection** per il tipo di profilo > **Crittografia Windows**), si aggiungono impostazioni BitLocker. 

Questo aggiornamento include una nuova impostazione di BitLocker per consentire agli utenti standard (non amministratori) di abilitare la crittografia. 

Per visualizzare queste impostazioni, vedere [Impostazioni di Endpoint Protection per Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Verificare la conformità di Configuration Manager <!-- 2192052  eepublished  -->
Questo aggiornamento include una nuova impostazione di conformità di System Center Configuration Manager (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10 e versioni successive** > **Conformità di Configuration Manager**). Configuration Manager invia segnali per la conformità di Intune. Usando questa impostazione è possibile richiedere che tutti i segnali Configuration Manager restituiscano "conforme".

È possibile ad esempio richiedere che vengano installati nei dispositivi tutti gli aggiornamenti software. In Configuration Manager questo requisito ha lo stato "Installato". Se uno o più programmi nel dispositivo hanno uno stato sconosciuto, il dispositivo sarà non conforme in Intune.

Questa impostazione è descritta in [Conformità di Configuration Manager](compliance-policy-create-windows.md#configuration-manager-compliance).

Si applica a: Windows 10 e versioni successive

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>Personalizzare lo sfondo nei dispositivi iOS con supervisione con un profilo di configurazione del dispositivo <!-- 2809324   -->
Quando si crea un profilo di configurazione del dispositivo per i dispositivi iOS, è possibile personalizzare alcune funzionalità (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni di **Sfondo** che consentono a un amministratore di usare un'immagine PNG, JPG o JPEG nella schermata iniziale o nella schermata di blocco. Queste impostazioni dello sfondo si applicano solo ai dispositivi con supervisione. 

Per un elenco di queste impostazioni, vedere [Impostazioni relative alle funzionalità dei dispositivi iOS in Intune](ios-device-features-settings.md).

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Modalità a tutto schermo di Windows 10 disponibile a livello generale <!-- 3594661  -->
In questo aggiornamento, la funzionalità Modalità tutto schermo in Windows 10 e versioni successive è disponibile a livello generale. Per informazioni su tutte le impostazioni che è possibile aggiungere e configurare, vedere le [impostazioni della modalità tutto schermo per Windows 10 (e versioni successive)](kiosk-settings.md).

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>La Condivisione dei contatti tramite Bluetooth viene rimossa in Limitazioni del dispositivo > Proprietario dispositivo per Android Enterprise <!-- 3598396   -->
Quando si crea un profilo di limitazione per i dispositivi Android Enterprise, è disponibile un'impostazione **Condivisione dei contatti tramite Bluetooth**. In questo aggiornamento viene rimossa l'impostazione **Condivisione dei contatti tramite Bluetooth** (**Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo > Proprietario dispositivo** per il tipo di profilo > **Generale**). 

L'impostazione **Condivisione contatti tramite Bluetooth** non è supportata per la gestione dei proprietari di dispositivi Android Enterprise. Pertanto, la rimozione di questa impostazione non influisce su alcun dispositivo o tenant, anche se l'impostazione è abilitata e configurata nell'ambiente in uso.

Per un elenco delle impostazioni attualmente disponibili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

Si applica a: Proprietario dispositivo Android Enterprise

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>Supporto di cancellazione selettiva per dispositivi WIP senza registrazione <!-- 1434452 -->
Windows Information Protection senza registrazione (WIP-WE, Windows Information Protection Without Enrollment) consente ai clienti di proteggere i dati aziendali nei dispositivi Windows 10 senza la necessità di una registrazione MDM (Mobile Device Management, gestione di dispositivi mobili) completa. Quando i documenti sono protetti da criteri WIP-WE, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, si rendono inutilizzabili tutti i dati protetti tramite criteri WIP-WE. Da Intune nel portale di Azure selezionare **App per dispositivi mobili** > **Cancellazione selettiva di app**.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>Nuovi log operativi e la possibilità di inviare i log ai servizi di Monitoraggio di Azure <!-- 3762211  -->
Intune include una funzionalità di registrazione di controllo predefinita che consente di tenere traccia degli eventi quando vengono apportate modifiche. Questo aggiornamento include nuove funzionalità di registrazione, tra cui: 
- Log operativi (anteprima) che mostrano informazioni dettagliate su utenti e dispositivi registrati, tra cui operazioni riuscite e non riuscite.
- I log di controllo e i log operativi possono essere inviati a Monitoraggio di Azure, inclusi account di archiviazione, hub eventi e Log Analytics. Questi servizi consentono di archiviare, usare funzionalità di analisi come QRadar e Splunk, nonché ottenere visualizzazioni dei dati di registrazione.

In [Inviare i dati dei log alla risorsa di archiviazione, agli hub eventi o a Log Analytics in Intune (anteprima)](review-logs-using-azure-monitor.md) sono disponibili altre informazioni su questa funzionalità.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>Ignorare altre schermate di Assistente configurazione in un dispositivo DEP iOS <!-- 2687509  -->
Oltre alle schermate che è attualmente possibile ignorare, è possibile impostare i dispositivi DEP iOS in modo che ignorino le schermate seguenti nell'Assistente configurazione quando un utente registra il dispositivo: Segnale schermo, Privacy, Migrazione di Android, Pulsante Pagina iniziale, iMessage e FaceTime, Onboarding, Migrazione di Watch, Aspetto, Orario schermo, Aggiornamento software, Configurazione SIM.
Per scegliere le schermate da ignorare, passare a **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP** > scegliere un token > **Profili** > scegliere un profilo > **Proprietà** > **Personalizzazione dell'Assistente configurazione** > scegliere **Nascondi** per tutte le schermate che si vuole ignorare > **OK**.
Se si crea un nuovo profilo o si modifica un profilo, le schermate da ignorare selezionate devono essere sincronizzate con il server MDM di Apple. Gli utenti possono eseguire una sincronizzazione manuale dei dispositivi in modo da evitare ritardi nell'aggiornamento delle modifiche del profilo.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Distribuzione di app Android Enterprise APP-WE <!-- 1171203 -->
Per i dispositivi Android in uno scenario di distribuzione APP-WE (App Protection Policy Without Enrollment) non registrato, è ora possibile usare Google Play gestito per distribuire app dello Store e app LOB agli utenti. In particolare, è possibile offrire agli utenti finali un catalogo di app e un'esperienza di installazione che non richiede più agli utenti finali di ridurre il comportamento di sicurezza dei propri dispositivi consentendo installazioni da origini sconosciute. Inoltre, questo scenario di distribuzione fornirà un'esperienza migliorata per gli utenti finali.

## <a name="week-of-january-14-2019"></a>Settimana del 14 gennaio 2019

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Anteprima del supporto per i dispositivi aziendali Android completamente gestiti <!-- 1574342  -->
Intune ora supporta i dispositivi Android completamente gestiti, ovvero uno scenario con dispositivi di proprietà aziendale gestiti rigorosamente dal reparto IT e associati a singoli utenti. Ciò consente agli amministratori di gestire l'intero dispositivo, imporre un'ampia gamma di controlli dei criteri non disponibili per i profili di lavoro e limitare gli utenti all'installazione di app solo da Google Play gestito. Per altre informazioni, vedere [Set up Intune enrollment of Android fully managed devices](android-fully-managed-enroll.md) (Configurare la registrazione in Intune dei dispositivi Android completamente gestiti) ed [Enroll your dedicated devices or fully managed devices](android-dedicated-devices-fully-managed-enroll.md) (Registrare i dispositivi dedicati o i dispositivi completamente gestiti).  Si noti che questa funzionalità è disponibile in anteprima. Alcune funzionalità di Intune, come ad esempio i certificati, la conformità e l'accesso condizionale, non sono attualmente disponibili con i dispositivi utente Android completamente gestiti.

## <a name="week-of-january-7-2019"></a>Settimana del 7 gennaio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-app-pin----2298397---"></a>PIN dell'app Intune <!-- 2298397 -->
Ora l'amministratore IT può configurare il numero di giorni di attesa per un utente finale prima che debba modificare il PIN dell'app Intune. La nuova impostazione è *PIN reset after number of days* (Reimpostazione PIN dopo numero di giorni) ed è disponibile nel portale di Azure selezionando **Intune** > **App client** > **Criteri di protezione delle app** > **Crea criterio** > **Impostazioni** > **Requisiti di accesso**. Disponibile per dispositivi [iOS](app-protection-policy-settings-ios.md) e [Android](app-protection-policy-settings-android.md), questa funzionalità supporta un numero intero positivo.


#### <a name="intune-device-reporting-fields----2748738---"></a>Campi per i report relativi ai dispositivi di Intune <!-- 2748738 -->
Intune offre campi aggiuntivi per i report relativi ai dispositivi, tra cui ID di registrazione app, produttore Android, modello e versione della patch di sicurezza, oltre al modello iOS. In Intune questi campi sono disponibili selezionando **App client** > **Stato protezione app** e scegliendo **Report sulla protezione dell'app: iOS, Android**. Inoltre, questi parametri consentiranno di configurare l'elenco **Consenti** per il produttore del dispositivo (Android), l'elenco **Consenti** per il modello di dispositivo (Android e iOS) e l'impostazione della versione minima della patch di sicurezza Android. 


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>I modelli amministrativi sono disponibili in anteprima pubblica e sono stati spostati nel profilo di configurazione corrispondente <!-- 3322847 -->

I modelli amministrativi in Intune (**Configurazione del dispositivo** > **Modelli amministrativi**) sono attualmente in anteprima privata. Con questo aggiornamento:

- i modelli amministrativi includono circa 300 impostazioni che possono essere gestite in Intune. In precedenza, queste impostazioni erano disponibili solo in Editor Criteri di gruppo.
- I modelli amministrativi sono disponibili in anteprima pubblica.
- I modelli amministrativi vengono spostati da **Configurazione del dispositivo** > **Modelli amministrativi** a **Configurazione del dispositivo** > **Profili** > **Crea profilo** > in **Piattaforma** scegliere  **Windows 10 e versioni successive** > in **Tipo di profilo** scegliere **Modelli amministrativi**.
- La creazione di report è abilitata

Per altre informazioni su questa funzionalità, vedere [Modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune](administrative-templates-windows.md).

Si applica a: Windows 10 e versioni successive

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>Usare S/MIME per crittografare e firmare più dispositivi per un utente <!-- 1333642 -->
Questo aggiornamento include una crittografia di posta elettronica S/MIME con un nuovo profilo di certificato importato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > selezionare la piattaforma > tipo di profilo **Certificato PKCS importato**). In Intune è possibile importare i certificati nel formato PFX. Intune può quindi distribuire i certificati a più dispositivi registrati da un singolo utente. Inoltre:
- Il profilo di posta elettronica iOS nativo supporta l'abilitazione della crittografia S/MIME mediante certificati importati in formato PFX.
- L'app di posta elettronica nativa nei dispositivi Windows Phone 10 usa automaticamente il certificato S/MIME.
- I certificati privati possono essere recapitati su più piattaforme. Tuttavia, non tutte le app di posta elettronica supportano S/MIME.
- In altre piattaforme potrebbe essere necessario configurare manualmente l'app di posta elettronica per abilitare S/MIME.  
- È possibile che le app di posta elettronica che supportano la crittografia S/MIME gestiscano il recupero dei certificati per la crittografia della posta elettronica S/MIME in un modo non supportato dal software MDM, ad esempio basandosi sull'archivio certificati del server di pubblicazione.
Per altre informazioni su questa funzionalità, vedere [Firma e crittografia S/MIME della posta elettronica in Intune](certificates-s-mime-encryption-sign.md).
Supportato in: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Nuove opzioni per la connessione automatica e per rendere persistenti le regole quando si usano le impostazioni DNS in dispositivi con Windows 10 e versioni successive <!-- 1333665, 2999078 -->
Nei dispositivi con Windows 10 e versioni successive è possibile creare un profilo di configurazione VPN che include un elenco dei server DNS per risolvere i domini, ad esempio contoso.com. Questo aggiornamento include nuove impostazioni per la risoluzione dei nomi (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **Windows 10 e versioni successive** per la piattaforma > scegliere **VPN** per il tipo di profilo > **Impostazioni DNS** >**Aggiungi**): 
- **Connetti automaticamente**: con l'impostazione **Abilitato**, il dispositivo si connette automaticamente alla rete VPN quando un dispositivo contatta un dominio immesso, ad esempio contoso.com.
- **Persistente**: per impostazione predefinita, tutte le regole della tabella dei criteri di risoluzione dei nomi di criteri (NRPT) sono attive, purché il dispositivo sia connesso con questo profilo VPN. Quando questa impostazione è **Abilitata** per una regola NRPT, la regola rimane attiva nel dispositivo, anche in caso di disconnessione della rete VPN. La regola rimane fino alla rimozione del profilo VPN o fino alla rimozione manuale della regola, che può essere eseguita tramite PowerShell.
[Impostazioni VPN di Windows 10](vpn-settings-windows-10.md) descrive le impostazioni. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Usare il rilevamento delle reti attendibili per i profili VPN nei dispositivi Windows 10 <!-- 1500165 -->
Quando si usa il rilevamento delle reti attendibili, è possibile impedire ai profili VPN di creare automaticamente una connessione VPN quando l'utente è già in una rete attendibile. Con questo aggiornamento è possibile aggiungere suffissi DNS per abilitare il rilevamento delle reti attendibili nei dispositivi che eseguono Windows 10 e versioni successive (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **VPN** per il tipo di profilo).
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md) sono elencate le impostazioni VPN correnti.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>Gestione di dispositivi Windows Holographic for Business usati da più utenti <!-- 1907917, 1063203 -->
Attualmente è possibile configurare le impostazioni del PC condiviso nei dispositivi Windows 10 e Windows Holographic for Business usando un'impostazione OMA-URI personalizzata. Con questo aggiornamento viene aggiunto un nuovo profilo per configurare le impostazioni del PC condiviso: **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** > **Dispositivo multiutente condiviso**.
Per altre informazioni su questa funzionalità, vedere [Controllare l'accesso, gli account e le funzionalità di risparmio energia nei PC condivisi o nei dispositivi multiutente con Intune](shared-user-device-settings.md).
Si applica a: Windows 10 e versioni successive, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>Nuove impostazioni per gli aggiornamenti di Windows 10 <!--2626030  2512994  -->
Per gli [anelli di aggiornamento Windows 10](windows-update-for-business-configure.md) è possibile configurare:
- **Comportamento di aggiornamento automatico**: usare la nuova opzione *Ripristina impostazione predefinita* per ripristinare le impostazioni di aggiornamento automatico originali nei computer Windows 10 che eseguono l'*aggiornamento di ottobre 2018*
- *Impedisci all'utente di sospendere gli aggiornamenti Windows*: consente di configurare una nuova impostazione per gli aggiornamenti software che impedisce o permette agli utenti di sospendere l'installazione degli aggiornamenti da **Impostazioni** nei loro computer. 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>I profili di posta elettronica iOS possono usare firma e crittogafia S/MIME <!-- 2662949 -->
È possibile creare un profilo di posta elettronica che include impostazioni diverse. Questo aggiornamento include le impostazioni di S/MIME che possono essere usate per firmare e crittografare le comunicazioni tramite posta elettronica nei dispositivi iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **iOS** per la piattaforma > **Posta elettronica** per il tipo di profilo).
Le impostazioni sono elencate in [Impostazioni del profilo di posta elettronica per dispositivi iOS](email-settings-ios.md).

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>Alcune impostazioni di BitLocker supportano l'edizione Windows 10 Pro<!-- 2727036 -->
È possibile creare un profilo di configurazione che imposta le impostazioni di Endpoint Protection nei dispositivi Windows 10, incluso BitLocker. Questo aggiornamento aggiunge il supporto per l'edizione Windows 10 Professional per alcune impostazioni di BitLocker. Per visualizzare queste impostazioni, vedere [Impostazioni di Endpoint Protection per Windows 10](endpoint-protection-windows-10.md#windows-encryption).

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>L'impostazione "Configurazione del dispositivo condiviso" è stata rinominata "Messaggio della schermata di blocco" per i dispositivi iOS nel portale di Azure <!-- 2809362 -->
Quando si crea un profilo di configurazione per i dispositivi iOS, è possibile aggiungere le impostazioni **Configurazione del dispositivo condiviso** per visualizzare testo specifico nella schermata di blocco. Questo aggiornamento include le modifiche seguenti: 
- L'impostazione **Configurazione del dispositivo condiviso** nel portale di Azure è stata rinominata "Lock Screen Message (supervised only)" (Messaggio della schermata di blocco - solo con supervisione): **Configurazione del dispositivo** > **Profili**  >  **Crea profilo** > scegliere **iOS** per la piattaforma > scegliere **Funzionalità del dispositivo** per il tipo di profilo > **Lock Screen Message** (Messaggio della schermata di blocco).
- Quando si aggiungono messaggi della schermata di blocco, è possibile inserire un numero di serie, un nome di dispositivo o un altro valore specifico del dispositivo come variabile in **Informazioni sui tag asset** e **Nota a piè di pagina della schermata di blocco**. Ad esempio, è possibile immettere `Device name: {{devicename}}` o `Serial number is {{serialnumber}}` usando parentesi graffe. In [Token iOS](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list) sono elencati i token disponibili che possono essere usati.
Le impostazioni sono elencate in [Aggiungere messaggi personalizzati alla schermata di blocco e alla finestra di accesso nei dispositivi iOS con Microsoft Intune](shared-device-settings-ios.md).

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>Nuove impostazioni di limitazione dei dispositivi "App Store, visualizzazione documenti, giochi" aggiunte ai dispositivi iOS <!-- 2827760-->
In **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi** sono state aggiunte le impostazioni seguenti: Allow managed apps to write contacts to unmanaged contacts accounts (Consenti alle app gestite di scrivere contatti in account di contatti non gestiti), Allow unmanaged apps to read from managed contacts accounts (Consenti alle app non gestite di leggere da account di contatti gestiti). Per vedere queste impostazioni, consultare le [limitazioni per i dispositivi iOS](device-restrictions-ios.md#app-store-doc-viewing-gaming).

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Nuove impostazioni di notifica, hint e protezione della tastiera per i dispositivi Android Enterprise in modalità proprietario del dispositivo <!-- 3201839 3201843 -->
Questo aggiornamento include numerose nuove funzionalità per i dispositivi aziendali Android quando vengono eseguiti come proprietario del dispositivo. Per usare queste funzionalità, passare a **Configurazione del dispositivo** > **Profili** > **Crea profilo** > in **Piattaforma**, scegliere **Android Enterprise** > in **Tipo di profilo**, scegliere **Solo proprietario del dispositivo** > **Limitazioni del dispositivo**.
Le nuove funzionalità includono: 
- Disabilitare la visualizzazione delle notifiche di sistema, incluse chiamate in ingresso, avvisi di sistema, errori di sistema e altro
- Suggerimenti per ignorare le esercitazioni e i consigli iniziali per le app aperte per la prima volta
- Disabilitare le impostazioni avanzate di protezione della tastiera, come fotocamera, notifiche, sblocco tramite impronta digitale e altre. Per visualizzare queste impostazioni, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>I dispositivi Android Enterprise in modalità proprietario del dispositivo possono usare le connessioni VPN sempre attive <!-- 3202194 -->
In questo aggiornamento è possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise in modalità proprietario del dispositivo. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
È possibile abilitare le connessioni VPN sempre attive in **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Limitazioni del dispositivo** per Solo proprietario del dispositivo > **Connettività**. Per visualizzare le impostazioni, passare a [Impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](device-restrictions-android-for-work.md).

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Nuova impostazione per terminare i processi in Gestione attività nei dispositivi Windows 10 <!-- 3285177 --> 
Questo aggiornamento include una nuova impostazione per terminare i processi usando Gestione attività nei dispositivi Windows 10. Scegliere se consentire o non consentire questa impostazione usando un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > In **Piattaforma**  scegliere **Windows 10** > in **Tipo di profilo** scegliere **Limitazioni del dispositivo** > **Generale**).
Per visualizzare queste impostazioni, vedere [Impostazioni relative alle limitazioni per i dispositivi Windows 10 e versioni successive in Microsoft Intune](device-restrictions-windows-10.md).
Si applica a: Windows 10 e versioni successive


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>Messaggi di errori più dettagliati per le restrizioni di registrazione <!-- 3111564 -->
Sono disponibili messaggi di errore più dettagliati quando non vengono soddisfatte le restrizioni di registrazione. Per visualizzare questi messaggi, passare a **Intune** > **Risoluzione dei problemi** e selezionare la tabella Errori di registrazione. Per altre informazioni, vedere l'[elenco degli errori di registrazione](help-desk-operators.md#configuration-policies-reference).



### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="tenant-status-dashboard-----1124854---"></a>Dashboard Stato del tenant <!-- 1124854 -->
La nuova pagina [Stato del tenant](tenant-status.md) offre una posizione centralizzata in cui visualizzare lo stato del tenant e le informazioni dettagliate correlate.  Il dashboard è suddiviso in quattro aree:
- **Dettagli del tenant**: visualizza informazioni su nome e posizione del tenant, autorità MDM, totale dei dispositivi registrati nel tenant e numero di licenze. Questa sezione indica anche la versione corrente del servizio per il tenant.
- **Stato del connettore**: visualizza informazioni sui connettori disponibili configurati e può elencare anche quelli non ancora abilitati.  
   In base allo stato corrente di ogni connettore, i connettori vengono contrassegnati come Integro, Avviso o Non integro. Selezionare un connettore per eseguire il drill-through e visualizzarne i dettagli oppure per configurare informazioni aggiuntive.
-  **Integrità del servizio Intune**: visualizza informazioni dettagliate sugli eventi imprevisti attivi o le interruzioni del tenant. Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office.
-  **Novità su Intune**: visualizza i messaggi attivi per il tenant, ad esempio le notifiche inviate quando il tenant riceve le funzionalità di Intune più recenti.  Le informazioni di questa sezione vengono recuperate direttamente dal Centro messaggi di Office.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Nuova esperienza di Guida e supporto tecnico nel Portale aziendale per Windows 10 <!-- 1488939-->
La nuova pagina Guida e supporto del Portale aziendale aiuta gli utenti a risolvere i problemi e a richiedere assistenza in merito ai problemi di accesso e relativi alle app. Da questa nuova pagina gli utenti possono inviare tramite posta elettronica i dettagli dei log degli errori e di diagnostica e possono trovare le informazioni dettagliate sul supporto tecnico della loro organizzazione. Troveranno anche una sezione di domande frequenti con collegamenti alla documentazione di Intune pertinente. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Nuova esperienza di Guida e supporto tecnico per Intune <!-- #3307080 -->
Nei prossimi giorni la nuova esperienza di Guida e supporto tecnico verrà distribuita in tutti i tenant. Questa nuova esperienza è disponibile per Intune ed è accessibile dai pannelli di Intune nel [portale di Azure](https://portal.azure.com/).
La nuova esperienza consente di descrivere il problema con parole proprie e di ricevere informazioni dettagliate per la risoluzione dei problemi e contenuti Web per la correzione. Queste soluzioni sono offerte tramite un algoritmo di apprendimento automatico basato su regole, creato in base alle indagini condotte tra gli utenti. Oltre alle indicazioni specifiche per il problema, è possibile usare il nuovo flusso di lavoro di creazione di un caso per aprire un caso di supporto tramite posta elettronica o telefono. Questa nuova esperienza sostituisce l'esperienza di Guida e supporto tecnico precedente basata su un set statico di opzioni preselezionate a seconda dell'area della console in cui ci si trova quando si apre Guida e supporto. Per altre informazioni, vedere [Come ottenere supporto per Microsoft Intune](get-support.md).

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-for-apps----1081941---"></a>Tag di ambito per le app <!-- 1081941 -->
È possibile creare tag di ambito per limitare l'accesso per ruoli e app. È possibile aggiungere un tag di ambito a un'app in modo che solo le persone al cui ruolo è già assegnato tale tag abbiano accesso all'app. Alle app acquistate con il Volume Purchase Program (VPP) di Apple non è possibile assegnare i tag di ambito.  Per altre informazioni, vedere [Usare i tag di ambito per filtrare i criteri](scope-tags.md).



## <a name="week-of-december-10-2018"></a>Settimana del 10 dicembre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="updates-for-application-transport-security----748318---"></a>Aggiornamenti per Application Transport Security <!-- 748318 -->

Microsoft Intune supporta Transport Layer Security (TLS) 1.2+ per offrire la migliore crittografia, per garantire una maggiore sicurezza per Intune per impostazione predefinita e per allinearsi agli altri servizi Microsoft, ad esempio Microsoft Office 365. Per poter soddisfare questo requisito, i portali aziendali iOS e macOS applicheranno i requisiti di Application Transport Security (ATS) aggiornati di Apple per cui è obbligatorio l'uso di TLS 1.2+. Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale iOS e macOS. Per altre informazioni, vedere il [blog del supporto tecnico di Intune](https://aka.ms/compportalats).

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK supporterà le chiavi di crittografia a 256 bit <!-- 1832174 -->
Intune App SDK per Android usa ora le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. L'SDK continuerà a supportare le chiavi a 128 bit per garantire la compatibilità con il contenuto e le app che usano versioni precedenti dell'SDK.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>Microsoft Auto Update versione 4.5.0 obbligatorio per i dispositivi macOS <!-- 3503442 -->
Per continuare a ricevere gli aggiornamenti per il portale aziendale e le altre applicazioni di Office, è necessario aggiornare i dispositivi macOS gestiti da Intune a Microsoft Auto Update 4.5.0. Gli utenti potrebbero avere già questa versione per le app di Office.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune richiede macOS 10.12 o versione successiva <!-- 2827778 -->
Intune richiede ora macOS versione 10.12 o successiva. I dispositivi che usano versioni precedenti di macOS non possono usare il portale aziendale per la registrazione in Intune. Per ricevere assistenza e nuove funzionalità, gli utenti devono aggiornare il dispositivo a macOS 10.12 o versione successiva e aggiornare l'app Portale aziendale alla versione più recente.

## <a name="week-of-november-26-2018"></a>Settimana del 26 novembre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>Disinstallazione di app in dispositivi iOS con supervisione di proprietà dell'azienda <!-- 1281677 -->

È possibile rimuovere qualsiasi app nei dispositivi iOS con supervisione di proprietà dell'azienda. È possibile rimuovere qualsiasi app specificando come destinazione gruppi di utenti o dispositivi con un tipo di assegnazione **Disinstalla**. Per i dispositivi iOS personali o senza supervisione, sarà ancora possibile rimuovere solo le app installate usando Intune.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Download del contenuto di app di Intune Win32 <!-- 2617320 -->
I client Windows 10 RS3 e versioni successive scaricheranno contenuto dell'app Win32 Intune mediante un componente Ottimizzazione recapito nel client Windows 10. Ottimizzazione recapito offre funzionalità peer-to-peer attivate per impostazione predefinita. È possibile configurare Ottimizzazione recapito tramite Criteri di gruppo e in futuro tramite Intune MDM. Per altre informazioni, vedere [Ottimizzazione recapito per Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu di scelta rapida per dispositivi e app per l'utente finale <!-- 2771453 -->
Gli utenti finali possono ora usare il menu di scelta rapida nel dispositivo e nelle app per attivare azioni comuni come la ridenominazione di un dispositivo o il controllo della conformità.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>Impostare lo sfondo personalizzato nell'app di schermata iniziale gestita <!-- 3041945 -->
Verrà aggiunta un'impostazione che consente di personalizzare l'aspetto dello sfondo dell'app di schermata iniziale gestita nei dispositivi Android Enterprise in modalità tutto schermo per più app.  Per configurare lo **sfondo personalizzato per l'URL**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>Salvataggio e applicazione dell'assegnazione dei criteri di protezione dell'app <!-- 3104570 -->
È disponibile un maggiore controllo sulle [assegnazioni dei criteri di protezione dell'app](app-protection-policies.md#deploy-a-policy-to-users). Quando si seleziona *Assegnazioni* per impostare o modificare le assegnazioni dei criteri, è necessario scegliere **Salva** per salvare la configurazione prima che la modifica venga applicata. Usare **Annulla** per cancellare tutte le modifiche apportate senza salvare le modifiche agli elenchi di inclusione o esclusione.  Con la scelta obbligatoria di Salva o Annulla, i criteri di protezione delle app vengono assegnati solo agli utenti previsti.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Nuove impostazioni del browser Microsoft Edge per Windows 10 e versioni successive <!-- 3174639 -->
Questo aggiornamento include nuove impostazioni per controllare e gestire il browser Microsoft Edge nei dispositivi. Per un elenco di queste impostazioni correnti, vedere [Restrizione dei dispositivi per Windows 10 (e versioni successive)](device-restrictions-windows-10.md#microsoft-edge-browser).

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>Supporto di nuove app con criteri di protezione delle app <!-- 3330037 -->
È ora possibile gestire le app seguenti con i [criteri di protezione delle app di Intune](app-protection-policies.md):
- Stream (iOS)
- To DO (Android, iOS)
- PowerApps (Android, iOS)
- Flow (Android, iOS)

Usare i criteri di protezione delle app per proteggere i dati aziendali e controllare il trasferimento dei dati per queste app, come per le altre app gestite dai criteri di Intune. Nota: se Flow non è ancora visibile nella console, è possibile aggiungere Flow quando si creano o modificano i criteri di protezione delle app. A tale scopo, usare l'opzione **+ Altre app** e quindi specificare l'*ID app* per Flow nel campo di input. Per Android usare *com.microsoft.flow* e per iOS usare *com.microsoft.procsimo*.


### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>Vengono visualizzati i numeri di versione e di build di iOS e macOS <!-- 1892471 -->
In **Conformità del dispositivo** > **Conformità del dispositivo** vengono visualizzate le versioni del sistema operativo iOS e macOS che possono essere usate nei criteri di conformità. Questo aggiornamento include il numero di build configurabile per entrambe le piattaforme.
Quando vengono rilasciati aggiornamenti della sicurezza, Apple lascia in genere il numero di versione invariato, ma aggiorna il numero di build. Il numero di build nei criteri di conformità consente di verificare facilmente se è installato l'aggiornamento di una vulnerabilità.
Per usare questa funzionalità, vedere i criteri di conformità di [iOS](compliance-policy-create-ios.md#device-health) e [macOS](compliance-policy-create-mac-os.md#device-properties).

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>Gli anelli di aggiornamento verranno sostituiti con le impostazioni di Ottimizzazione recapito per Windows 10 e versioni successive <!-- 2753807 -->
Ottimizzazione recapito è un nuovo profilo di configurazione per Windows 10 e versioni successive. Questa funzionalità offre un'esperienza semplificata per recapitare gli aggiornamenti software ai dispositivi nell'organizzazione. Questo aggiornamento consente anche di distribuire le impostazioni in anelli di aggiornamento nuovi ed esistenti tramite un profilo di configurazione.
Per configurare un profilo di configurazione di ottimizzazione recapito, vedere [Windows 10 (and newer) delivery optimization settings](delivery-optimization-windows.md).(Impostazioni di ottimizzazione recapito di Windows 10 e versioni successive).

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>Nuove impostazioni relative alle limitazioni dei dispositivi aggiunte ai dispositivi iOS e macOS <!-- 2827760 -->
Questo aggiornamento include nuove impostazioni per i dispositivi iOS e macOS che vengono rilasciati con iOS 12:

**Impostazioni iOS**: 
- Generali: Blocca la rimozione di app (solo con supervisione)
- Generali: Blocca la modalità USB con restrizioni (solo con supervisione)
- Generali: Imponi data e ora automatiche (solo con supervisione)
- Password: Blocca il riempimento automatico delle password (solo con supervisione)
- Password: Blocca le richieste di prossimità password (solo con supervisione)
- Password: Blocca la condivisione delle password (solo con supervisione)

**Impostazioni macOS**: 
- Password: Blocca il riempimento automatico delle password
- Password: Blocca le richieste di prossimità password
- Password: Blocca la condivisione delle password

Per altre informazioni su queste impostazioni, vedere le impostazioni relative alle limitazioni dei dispositivi [iOS](device-restrictions-ios.md) e [macOS](device-restrictions-macos.md).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>Selezionare le app registrate nella pagina Stato di registrazione<!-- 2531007 -->
È possibile scegliere le app di cui tenere traccia nella pagina Stato di registrazione. Fino a quando non vengono installate queste app, l'utente non può usare il dispositivo. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>Cercare dispositivi Autopilot in base al numero di serie <!--2595788 -->
È ora possibile cercare i dispositivi Autopilot in base al numero di serie. A tale scopo, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Dispositivi** > digitare un numero di serie nella casella **Cerca per numero di serie** > premere INVIO.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Tenere traccia dell'installazione di Office ProPlus <!--2620217 -->
Gli utenti possono tenere traccia dello stato dell'installazione di [Office ProPlus](apps-add-office365.md) tramite la pagina [Stato di registrazione](windows-enrollment-status.md). Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](windows-enrollment-status.md).

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Avvisi per i token VPP in scadenza o un numero insufficiente di licenze del portale aziendale <!-- 2237572 -->
Se si usa Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante la registrazione DEP, Intune invierà un avviso in prossimità della scadenza del token VPP e in caso di un numero insufficiente di licenze per il portale aziendale.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Supporto di Device Enrollment Program di macOS per gli account Apple School Manager <!--3006133 -->
Intune supporta ora l'uso di Device Enrollment Program nei dispositivi macOS per gli account Apple School Manager.  Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS con Device Enrollment Program o Apple School Manager](device-enrollment-program-enroll-macos.md).

### <a name="new-intune-device-subscription-sku---3312071--"></a>Nuovo SKU per la sottoscrizione del dispositivo Intune <!--3312071-->
È ora disponibile un nuovo SKU per la sottoscrizione basato sul dispositivo che consente alle organizzazioni di ridurre i costi di gestione dei dispositivi. Questo SKU per dispositivo Intune viene concesso in licenza per ogni dispositivo su base mensile. Il prezzo varia in base al programma di licenza. È disponibile direttamente tramite il portale di amministrazione di Office e tramite il [Contratto Enterprise](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2), il [Contratto per i Prodotti e i Servizi Microsoft](https://www.microsoft.com/licensing/mpsa/default), i [contratti Microsoft Open](https://partner.microsoft.com/licensing/licensing-agreements) e [Cloud Solution Provider](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Sospendere temporaneamente la modalità tutto schermo sui dispositivi Android per apportare modifiche <!-- 3041935 -->
Quando si usano dispositivi Android in modalità tutto schermo per più app, un amministratore IT potrebbe aver bisogno di apportare modifiche al dispositivo. Questo aggiornamento include nuove impostazioni della modalità tutto schermo per più app che consentono a un amministratore IT di sospendere temporaneamente la modalità tutto schermo tramite un PIN e di ottenere l'accesso all'intero dispositivo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Abilitare il pulsante Pagina iniziale virtuale nei dispositivi in modalità tutto schermo di Android Enterprise <!-- 3042021 -->
Una nuova impostazione consentirà agli utenti di toccare un pulsante softkey nel dispositivo per passare dall'app di schermata iniziale gestita alle altre app assegnate nel dispositivo in modalità tutto schermo per più app. Questa impostazione è particolarmente utile negli scenari in cui l'app in modalità tutto schermo di un utente non risponde in modo corretto al pulsante "Indietro". Sarà possibile configurare questa impostazione per i dispositivi Android monouso di proprietà dell'azienda. Per abilitare o disabilitare il **pulsante Pagina iniziale virtuale**, passare a Intune nel portale di Azure > Configurazione del dispositivo. Selezionare un profilo di configurazione del dispositivo corrente o crearne uno nuovo per modificarne le impostazioni della modalità tutto schermo.
Per visualizzare le impostazioni della modalità tutto schermo, vedere [Restrizioni dei dispositivi Android Enterprise](device-restrictions-android-for-work.md).

## <a name="week-of-november-12-2018"></a>Settimana del 12 novembre 2018

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>Supporto del controllo accesso alla rete per Citrix SSO per iOS <!-- 3259404 -->

Citrix ha rilasciato un aggiornamento di Citrix Gateway per supportare il controllo accesso alla rete per Citrix SSO per iOS in Intune. È possibile acconsentire esplicitamente per includere un ID dispositivo all'interno di un profilo VPN in Intune e quindi eseguire il push del profilo nei dispositivi iOS. Sarà necessario installare l'aggiornamento più recente di Citrix Gateway per usare questa funzionalità.

In [Configurare le impostazioni VPN nei dispositivi iOS](vpn-settings-ios.md#base-vpn-settings) sono disponibili altre informazioni sull'uso del controllo accesso alla rete, tra cui alcuni requisiti aggiuntivi. 

## <a name="week-of-november-5-2018"></a>Settimana del 05 novembre 2018

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>Supporto per iOS 12 OAuth nei profili di posta elettronica iOS <!--2155106 -->

I profili di posta elettronica iOS di Intune supportano iOS 12 Open Authorization (OAuth). Per visualizzare questa funzionalità, creare un nuovo profilo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Posta elettronica** per il tipo di profilo), oppure aggiornare un profilo di posta elettronica iOS esistente. Se la funzionalità OAuth viene abilitata in un profilo che è già stato distribuito, agli utenti verrà richiesto di ripetere l'autenticazione e di scaricare nuovamente il messaggio di posta elettronica.

Nella pagina sui [profili di posta elettronica iOS](email-settings-ios.md) sono disponibili altre informazioni sull'uso di OAuth in un profilo di posta elettronica.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>Supporto di Autopilot per i dispositivi ibridi aggiunti ad Azure Active Directory (anteprima) <!-- 1048100-->
È ora possibile configurare i dispositivi ibridi aggiunti ad Azure Active Directory usando Autopilot. I dispositivi devono essere aggiunti alla rete dell'organizzazione per usare la funzionalità ibrida di Autopilot. Per altre informazioni, vedere [Distribuire dispositivi aggiunti ad Azure AD ibrido con Intune e Windows Autopilot](windows-autopilot-hybrid.md).
Questa funzionalità verrà implementata nella base di utenti nei prossimi giorni. Di conseguenza, sarà possibile seguire questa procedura solo dopo l'implementazione nel proprio account.

## <a name="week-of-october-29-2018"></a>Settimana del 29 ottobre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>Richiedere un PIN non biometrico dopo un timeout specificato <!-- 1506985 -->
Se si richiede un PIN non biometrico dopo un timeout specificato dall'amministratore, Intune offre una maggiore protezione per le app abilitate per la gestione delle applicazioni mobili (MAM, Mobile Application Management) limitando l'uso dell'identificazione biometrica per l'accesso ai dati aziendali. Le impostazioni interessano gli utenti che usano Touch ID (iOS), Face ID (iOS), Android Biometric o altri metodi di autenticazione biometrica futuri per accedere alle applicazioni abilitate per APP/MAM. Queste impostazioni offrono agli amministratori di Intune un controllo più granulare sull'accesso degli utenti, eliminando i casi in cui un dispositivo con più impronte digitali o altri metodi di accesso biometrico possono rivelare dati aziendali all'utente sbagliato. Nel portale di Azure aprire **Microsoft Intune**. Selezionare **App client** > **Criteri di protezione delle app** > **Aggiungi criteri** > **Impostazioni**. Individuare la sezione di **accesso** per le impostazioni specifiche. Per informazioni sulle impostazioni di accesso, vedere [Impostazioni iOS](app-protection-policy-settings-ios.md#access-requirements) e [Impostazioni Android](app-protection-policy-settings-android.md#access-requirements).

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM <!-- 2244713 -->
È possibile separare il controllo delle impostazioni per il trasferimento dei dati delle app di Intune nei dispositivi iOS registrati in MDM dall'impostazione dell'identità dell'utente registrato, nota anche come nome dell'entità utente (UPN). Gli amministratori che non usano IntuneMAMUPN non noteranno alcuna variazione di comportamento. Quando questa funzionalità è disponibile, gli amministratori che usano IntuneMAMUPN per controllare il trasferimento dei dati nei dispositivi registrati dovranno esaminare le nuove impostazioni e aggiornare le impostazioni dell'app di conseguenza.

#### <a name="windows-10-win32-apps----2617325---"></a>App Win32 di Windows 10 <!-- 2617325 -->
È possibile configurare le app Win32 in modo che vengano installate nel contesto utente per i singoli utenti oppure per tutti gli utenti del dispositivo.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>App Win32 di Windows e script di PowerShell <!-- 2617330 -->
Gli utenti finali non devono più eseguire l'accesso al dispositivo per installare le app Win32 o eseguire gli script di PowerShell. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>Risoluzione dei problemi di installazione delle app client <!-- 1363711 -->
È possibile risolvere i problemi relativi all'installazione delle app client esaminando la colonna con l'etichetta **Installazione dell'app** nel pannello **Risoluzione dei problemi**. Per visualizzare il pannello **Risoluzione dei problemi**, nel portale di Intune selezionare **Risoluzione dei problemi** in **Guida e supporto tecnico**.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>Supporto del controllo di accesso alla rete nei client VPN iOS <!-- 1333693 -->
Con questo aggiornamento, è disponibile una nuova impostazione per abilitare il controllo di accesso alla rete quando si crea un profilo di configurazione VPN per Cisco AnyConnect, F5 Access e Citrix SSO per iOS. Questa impostazione consente di includere l'ID controllo di accesso alla rete del dispositivo nel profilo VPN. Non sono attualmente disponibili client VPN o soluzioni partner di controllo di accesso alla rete che supportano questo nuovo ID di controllo di accesso alla rete, ma quando lo saranno, verrà comunicato tramite il [post di blog del supporto](ttps://aka.ms/iOS12_and_vpn).

Per usare il controllo di accesso alla rete, sarà necessario:
1. Acconsentire esplicitamente per permettere a Intune di includere gli ID dei dispositivi nei profili VPN
2. Aggiornare il firmware/software del provider del controllo di accesso alla rete, usando le indicazioni del provider del controllo di accesso alla rete

Per informazioni su questa impostazione in un profilo VPN iOS, vedere [Aggiungere le impostazioni VPN sui dispositivi iOS in Microsoft Intune](vpn-settings-ios.md). Per altre informazioni sul controllo di accesso alla rete, vedere [Integrazione del controllo di accesso alla rete (NAC) con Intune](network-access-control-integrate.md). 

Si applica a: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>Rimuovere un profilo di posta elettronica da un dispositivo, anche se è disponibile un solo profilo di posta elettronica <!-- 1818139 -->
In precedenza non era possibile rimuovere un profilo di posta elettronica da un dispositivo *se* era l'unico profilo disponibile. Con questo aggiornamento, il comportamento cambia. Ora è possibile rimuovere un profilo di posta elettronica anche se è l'unico profilo di posta elettronica presente nel dispositivo. Per i dettagli, vedere [Add email settings to devices using Intune](email-settings-configure.md) (Aggiungere impostazioni di posta elettronica ai dispositivi con Intune).

#### <a name="powershell-scripts-and-aad----2309469---"></a>Script di PowerShell e AAD <!-- 2309469 -->
Gli script di PowerShell in Intune possono essere destinati ai gruppi di sicurezza dei dispositivi AAD.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Nuova impostazione predefinita "Tipo di password richiesto" per Android, Android Enterprise<!-- 2649963 -->
Quando si crea un nuovo criterio di conformità (**Intune** > **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android** o **Android Enterprise** per Piattaforma > Sicurezza del sistema),il valore predefinito di **Tipo di password richiesto** viene modificato:

Da: Impostazione predefinita dispositivo A: Almeno numerico

Si applica a: Android, Android Enterprise

Per visualizzare queste impostazioni, vedere [Android](compliance-policy-create-android.md) e [Android Enterprise](compliance-policy-create-android-for-work.md).

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Usare una chiave precondivisa in un profilo Wi-Fi di Windows 10 <!-- 2662938 -->
Con questo aggiornamento, è possibile usare una chiave precondivisa con il protocollo di sicurezza WPA/WPA2-Personal per autenticare un profilo di configurazione Wi-Fi per Windows 10. È anche possibile specificare la configurazione dei costi per una rete a consumo per i dispositivi nell'aggiornamento di Windows 10 di ottobre 2018.

Attualmente, per poter usare una chiave precondivisa è necessario importare un profilo Wi-Fi o creare un profilo personalizzato. In [Impostazioni Wi-Fi per Windows 10](wi-fi-settings-windows.md) sono elencate le impostazioni correnti. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>Rimuovere i certificati PKCS e SCEP dai dispositivi <!-- 3218390 -->
In alcuni scenari i certificati PKCS e SCEP rimangono nei dispositivi, anche quando si rimuove un criterio da un gruppo, si elimina una distribuzione di configurazione o conformità o un amministratore aggiorna un profilo SCEP o PKCS esistente. Questo aggiornamento modifica il comportamento. Esistono alcuni scenari in cui i certificati PKCS e SCEP vengono rimossi dai dispositivi e alcuni scenari in cui i certificati rimangono nel dispositivo. Per informazioni su questi scenari, vedere [Rimuovere i certificati SCEP e PKCS in Microsoft Intune](remove-certificates.md).

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>Usare Gatekeeper nei dispositivi macOS per la conformità <!-- 2504381 -->
Questo aggiornamento include macOS Gatekeeper per valutare la conformità dei dispositivi. Per impostare la proprietà di Gatekeeper, [aggiungere criteri di conformità per i dispositivi macOS](compliance-policy-create-mac-os.md).


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="enrollment-abandonment-report----1382924---"></a>Report sull'abbandono delle registrazioni <!-- 1382924 -->
Un nuovo report con i dettagli sulle registrazioni abbandonate è disponibile in **Registrazione del dispositivo** > **Monitoraggio**. Per altre informazioni, vedere [Report Abbandono del portale aziendale](enrollment-report-company-portal-abandon.md).

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>Nuova funzionalità Condizioni per l'utilizzo di Azure Active Directory <!-- 2870393 -->
Azure Active Directory ha una funzionalità Condizioni per l'utilizzo che è possibile usare al posto delle condizioni di Intune esistenti. La funzionalità Condizioni per l'utilizzo di Azure AD offre maggiore flessibilità sule condizioni da visualizzare e su quando visualizzarle, un migliore supporto della localizzazione, maggiore controllo sul rendering delle condizioni e creazione di report migliorata. La funzionalità Condizioni per l'utilizzo di Azure AD richiede Azure Active Directory Premium P1 che fa parte della suite Enterprise Mobility + Security E3. Per altre informazioni, vedere l'articolo [Gestire termini e condizioni aziendali per l'accesso degli utenti](terms-and-conditions-create.md).

#### <a name="android-device-owner-mode-support---3188762--"></a>Supporto della modalità Proprietario dispositivo Android <!--3188762-->
Per Samsung Knox Mobile Enrollment, Intune supporta ora la registrazione dei dispositivi nella modalità di gestione Proprietario dispositivo Android. Gli utenti connessi a reti Wi-Fi o cellulari possono eseguire la registrazione con pochi tocchi quando accendono il dispositivo per la prima volta. Per altre informazioni, vedere [Automatically enroll Android devices by using Samsung's Knox Mobile Enrollment](android-samsung-knox-mobile-enroll.md) (Registrare automaticamente i dispositivi Android usando Samsung Knox Mobile Enrollment).

### <a name="device-management"></a>Gestione dei dispositivi
#### <a name="new-settings-for-software-updates------1907869---"></a>Nuove impostazioni per gli aggiornamenti software   <!-- 1907869 -->  
- È ora possibile configurare alcune notifiche per avvisare gli utenti finali della necessità di un riavvio per completare l'installazione degli aggiornamenti software più recenti.   
- È ora possibile configurare una richiesta di avviso per i riavvii che vengono eseguiti al di fuori dell'orario di lavoro. Tali richieste supportano gli scenari BYOD.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>Raggruppare i dispositivi registrati con Windows Autopilot per ID correlatore <!-- 2075110 -->
Intune supporta ora il raggruppamento dei dispositivi Windows per ID correlatore quando vengono registrati usando [Autopilot per i dispositivi esistenti](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) tramite Configuration Manager. L'ID correlatore è un parametro del file di configurazione di Autopilot. Intune imposterà automaticamente l'[attributo del dispositivo Azure AD enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) su "OfflineAutopilotprofile-<correlator ID>. In questo modo sarà possibile creare gruppi dinamici di Azure AD arbitrari in base all'ID correlatore tramite l'attributo enrollmentprofileName per le registrazioni di Autopilot offline. Per altre informazioni, vedere [Windows Autopilot per dispositivi esistenti](enrollment-autopilot.md#windows-autopilot-for-existing-devices).

#### <a name="intune-app-protection-policies----2984657---"></a>Criteri di protezione delle app di Intune <!-- 2984657 -->
I criteri di protezione delle app di Intune consentono di configurare varie impostazioni di protezione dei dati per le app protette da Intune, ad esempio Microsoft Outlook e Microsoft Word. È stato modificato l'aspetto di queste impostazioni sia per [iOS](app-protection-policy-settings-ios.md) che per [Android](app-protection-policy-settings-android.md) in modo che sia più facile trovare le singole impostazioni. Sono tre le categorie di impostazioni dei criteri:
- **Rilocazione dei dati**: questo gruppo include i controlli di prevenzione della perdita dei dati, ad esempio le restrizioni relative alle operazioni Taglia, Copia, Incolla e Salva con nome. Queste impostazioni determinano la modalità con cui gli utenti interagiscono con i dati nelle app.
- **Requisiti di accesso**: questo gruppo contiene le opzioni PIN per ogni app che determinano in che modo l'utente finale accede alle app in un contesto aziendale.  
- **Avvio condizionale**: questo gruppo contiene impostazioni come le impostazioni minime del sistema operativo, il rilevamento di jailbreak e dispositivi rooted e i periodi di prova offline.  
  
La funzionalità delle impostazioni non cambia, ma sarà più semplice trovarle quando si usa il flusso di creazione dei criteri.

### <a name="intune-apps"></a>App di Intune

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune supporterà una dimensione massima dei pacchetti pari a 8 GB per le app line-of-business <!-- 1727158 -->
Intune ha aumentato le dimensioni massime consentite per i pacchetti a 8 GB per le app line-of-business. Per altre informazioni, vedere [Aggiungere app a Microsoft Intune](apps-add.md).

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>Aggiungere l'immagine del marchio personalizzata per l'app Portale aziendale <!-- 1916266 -->
Gli amministratori di Microsoft Intune possono caricare un'immagine del marchio personalizzata da visualizzare come sfondo nella pagina del profilo utente nell'app Portale aziendale di iOS. Per altre informazioni sulla configurazione dell'app Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](company-portal-app.md).

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune manterrà la lingua localizzata di Office durante gli aggiornamenti di Office nei computer degli utenti finali <!-- 2971030 -->
Quando Intune installa Office nei computer dell'utente finale, i Language Pack sono gli stessi usati nelle precedenti installazioni di Office MSI. Per altre informazioni, vedere [Assegnare le app di Office 365 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Nuova esperienza di supporto di Intune nel portale di Gestione dei dispositivi per Microsoft 365 <!-- 3076965 -->
Verrà implementata una nuova esperienza di Guida e supporto tecnico per Intune nel [portale di Gestione dei dispositivi per Microsoft 365]( http://devicemanagement.microsoft.com). La nuova esperienza consente di descrivere il problema con parole proprie e di ricevere informazioni dettagliate per la risoluzione dei problemi e contenuti Web per la correzione. Queste soluzioni sono offerte tramite un algoritmo di apprendimento automatico basato su regole, creato in base alle indagini condotte tra gli utenti.  

Oltre alle indicazioni specifiche per il problema, è anche possibile usare il nuovo flusso di lavoro di creazione di un caso per aprire un caso di supporto tramite posta elettronica o telefono.  

Per i clienti che fanno parte dell'implementazione, questa nuova esperienza sostituisce l'esperienza di Guida e supporto tecnico corrente basata su un set statico di opzioni preselezionate a seconda dell'area della console usata quando si apre Guida e supporto tecnico.  

*Questa nuova esperienza di Guida e supporto tecnico verrà implementata solo in alcuni tenant ed è disponibile nel portale di gestione dei dispositivi. I partecipanti a questa nuova esperienza vengono selezionati casualmente tra i tenant di Intune disponibili. Con l'espansione dell'implementazione, verranno aggiunti nuovi tenant.*  

Per altre informazioni, vedere [Nuova esperienza di Guida e supporto tecnico](get-support.md#help-and-support-experience) in Come ottenere supporto per Microsoft Intune.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Modulo di PowerShell per Intune: anteprima disponibile <!-- 951068 -->
Un nuovo modulo di PowerShell, che offre il supporto per l'API di Intune attraverso Microsoft Graph, è ora disponibile in anteprima in [GitHub]( https://aka.ms/intunepowershell). Per informazioni dettagliate sull'uso di questo modulo, vedere il file Leggimi in tale percorso. 


## <a name="week-of-october-15-2018"></a>Settimana del 15 ottobre 2018

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>Richiesta del PIN quando si modificano le impronte digitali o l'ID del viso in un dispositivo iOS <!-- 2637704  -->
Agli utenti viene ora richiesto un PIN dopo aver apportato modifiche biometriche nel dispositivo iOS. Sono incluse le modifiche per le impronte digitali registrate o l'ID viso. La tempistica della richiesta dipende dalla configurazione del timeout per *Controlla di nuovo i requisiti di accesso dopo (minuti)*.  Se non è impostato alcun PIN, all'utente viene richiesto di configurarne uno. 
 
Questa funzionalità è disponibile solo per iOS e richiede la partecipazione delle applicazioni che integrano Intune APP SDK per iOS, versione 9.0.1 o successive. L'integrazione dell'SDK è necessaria in modo che il comportamento possa essere applicato nelle applicazioni di destinazione. Questa integrazione avviene sistematicamente e dipende dai team delle applicazioni specifiche. Tra le app partecipanti sono inclusi WXP, Outlook, Managed Browser e Yammer.


## <a name="week-of-october-1-2018"></a>Settimana dell'1 ottobre 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>Accedere alle proprietà principali del profilo usando l'app Portale aziendale <!-- 772203 -->
Gli utenti finali possono ora accedere alle proprietà e alle azioni principali per l'account, come la reimpostazione della password, dall'app Portale aziendale. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Le tastiere di terze parti possono essere bloccate dalle impostazioni APP in iOS <!-- 1248481 -->
Nei dispositivi iOS gli amministratori di Intune possono impedire l'uso di tastiere di terze parti quando si accede ai dati dell'organizzazione nelle app protette da criteri. Quando i criteri di protezione delle applicazioni (APP, Application Protection Policy) sono impostati in modo da bloccare le tastiere di terze parti, l'utente del dispositivo visualizza un messaggio la prima volta che interagisce con i dati aziendali usando una tastiera di terze parti. Tutte le opzioni, eccetto la tastiera nativa, vengono bloccate e non saranno visibili agli utenti dei dispositivi. Gli utenti visualizzano la finestra di dialogo del messaggio una sola volta. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>Accesso agli account utente delle app di Intune nei dispositivi gestiti iOS e Android <!-- 1248496 -->
L'amministratore di Microsoft Intune può controllare gli account utente che vengono aggiunti alle applicazioni di Microsoft Office nei dispositivi gestiti. Può limitare l'accesso agli account utente consentiti dell'organizzazione e bloccare gli account personali nei dispositivi registrati. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Criteri di configurazione delle app di Outlook iOS e Android <!--1828527 -->
È ora possibile creare criteri di configurazione delle app per Outlook per iOS e Android per gli utenti locali che usano l'autenticazione di base con il protocollo ActiveSync. Ulteriori impostazioni di configurazione verranno aggiunte non appena abilitate per Outlook per iOS e Android.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Language Pack di Office 365 Pro Plus <!-- 1833450 -->
In qualità di amministratore di Intune, l'utente potrà distribuire sarà possibile distribuire altre lingue per le app di Office 365 Pro Plus gestite con Intune. L'elenco delle lingue disponibili include il **tipo** di Language Pack (core, parziale e correzione). Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** del pannello **Aggiungi app** selezionare **Windows 10** in **Famiglia di prodotti Office 365**. Selezionare **Lingue** nel pannello **Impostazioni della suite di app**.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Estensioni file delle app line-of-business (LOB) di Windows <!-- 1884873 -->
Le estensioni file delle app line-of-business di Windows ora includono *msi*, *appx*, *appxbundle*, *msix* e *msixbundle*. È possibile aggiungere un'app in Microsoft Intune selezionando **App client** > **App** > **Aggiungi**. Viene visualizzato il riquadro **Aggiungi app** che consente di selezionare il **Tipo di app**. Per le app line-of-business di Windows, selezionare il tipo di app **App line-of-business**, selezionare il **File del pacchetto dell'app** e quindi specificare un file di installazione con l'estensione appropriata.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Distribuzione di app di Windows 10 con Intune <!-- 2309001 -->
Basandosi sul supporto esistente per le app line-of-business e le app di Microsoft Store per le aziende, gli amministratori possono usare Intune per distribuire la maggior parte delle applicazioni esistenti dell'organizzazione per gli utenti finali in dispositivi Windows 10. Gli amministratori possono aggiungere, installare e disinstallare le applicazioni per gli utenti di Windows 10 in una vasta gamma di formati, ad esempio MSI, Setup.exe o MSP. Intune valuterà le regole dei requisiti prima del download e dell'installazione, notificando agli utenti finali lo stato o i requisiti di riavvio tramite il centro notifiche di Windows 10. Questa funzionalità sbloccherà di fatto le organizzazioni interessate a spostare questo carico di lavoro in Intune e nel cloud. Questa funzionalità è attualmente disponibile in anteprima pubblica e si prevede che verranno aggiunte nuove importanti funzioni nei prossimi mesi. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>Menu di scelta rapida per dispositivi e app per l'utente finale <!-- 2771453 -->
Gli utenti finali possono ora usare il menu di scelta rapida in un dispositivo e nelle app per attivare azioni comuni come la ridenominazione di un dispositivo o la verifica della conformità. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Tasti di scelta rapida del portale aziendale di Windows <!-- 2771518 -->
Gli utenti finali possono usare tasti di scelta rapida per eseguire azioni sulle app e sui dispositivi nell'app Portale aziendale di Windows.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Creare suffissi DNS nei profili di configurazione VPN per i dispositivi che eseguono Windows 10<!-- 1333668 -->
Quando si crea un profilo di configurazione del dispositivo VPN (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo**VPN**) è necessario immettere alcune impostazioni DNS. Con questo aggiornamento, è anche possibile immettere più **suffissi DNS** in Intune. Quando si usano i suffissi DNS, è possibile cercare una risorsa di rete usando il relativo nome breve anziché il nome di dominio completo (FQDN). Questo aggiornamento consente inoltre di modificare l'ordine dei suffissi DNS in Intune.
In [Impostazioni VPN di Windows 10](vpn-settings-windows-10.md#dns-settings) sono elencate le impostazioni DNS correnti.
Si applica a: Dispositivi Windows 10

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Supporto dei profili di lavoro per le connessioni VPN sempre attive in Android Enterprise <!-- 1333705 -->
In questo aggiornamento è possibile usare le connessioni VPN sempre attive nei dispositivi Android Enterprise con profili di lavoro gestiti. Le connessioni VPN sempre attive rimangono connesse o si riconnettono immediatamente quando l'utente sblocca il dispositivo, quando il dispositivo viene riavviato o quando la rete wireless viene modificata. La modalità "blocco" della connessione consente di bloccare tutto il traffico di rete in attesa che la connessione VPN torni attiva.
È possibile abilitare la VPN sempre attiva in **Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Android Enterprise** > **Limitazioni del dispositivo** > **Connettività**.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emettere certificati SCEP per i dispositivi senza utenti <!-- 1744554 -->
Attualmente, i certificati vengono rilasciati agli utenti. Con questo aggiornamento, è possibile emettere certificati SCEP per i dispositivi, anche i dispositivi senza utente, come quelli con modalità tutto schermo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **Windows 10 e versioni successive** > profilo **Certificato SCEP**). Altri aggiornamenti includono:
- La proprietà **Oggetto** di un profilo SCEP è ora una casella di testo personalizzata e può includere nuove variabili. 
- La proprietà **Nome alternativo del soggetto** di un profilo SCEP è ora un formato di tabella e può includere nuove variabili. Nella tabella un amministratore può aggiungere un attributo e inserire il valore in una casella di testo personalizzata. Nome alternativo del soggetto supporterà gli attributi seguenti: 
  - DNS
  - Indirizzo di posta elettronica
  - UPN

  Queste nuove variabili possono essere aggiunte con testo statico in una casella di testo personalizzata. Ad esempio, l'attributo DNS può essere aggiunto come `DNS = {{AzureADDeviceId}}.domain.com`.

  > [!NOTE]
  > Le parentesi graffe, il punto e virgola e la barra verticale "{} ; |" non funzioneranno nel testo statico di Nome alternativo del soggetto. Per essere accettate per `Subject` o `Subject alternative name`, le parentesi graffe devono racchiudere solo una delle nuove variabili del certificato dispositivo. 

Nuove variabili del certificato dispositivo:  

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

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>Bloccare in remoto i dispositivi non conformi <!-- 2064495 -->
È possibile creare un'azione nei criteri di conformità che blocca in modalità remota il dispositivo non conforme. In Intune > **Conformità del dispositivo** creare un nuovo criterio o selezionare un criterio esistente > **Proprietà**. Selezionare **Azioni per la non conformità** > **Aggiungi** e scegliere di bloccare in remoto il dispositivo.
Supportato in: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e versioni successive 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Miglioramenti del profilo per modalità tutto schermo per Windows 10 e versioni successive nel portale di Azure <!-- 2748224 -->
Questo aggiornamento include i miglioramenti seguenti per il profilo di configurazione del dispositivo per modalità tutto schermo per Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma**Windows 10 e versioni successive** > tipo di profilo **Modalità tutto schermo (anteprima)**): 
- Attualmente, è possibile creare più profili per modalità tutto schermo sullo stesso dispositivo. Con questo aggiornamento, Intune supporterà un solo un profilo per modalità tutto schermo per ogni dispositivo. Se servono più profili per modalità tutto schermo in un singolo dispositivo, usare un URI personalizzato.
- In un profilo **Più app in modalità tutto schermo** è possibile selezionare le dimensioni del riquadro dell'applicazione e l'ordine del **layout del menu Start** nella griglia dell'applicazione. Se si desidera un maggiore livello di personalizzazione, è possibile continuare a caricare un file XML.
- Le impostazioni del browser in modalità tutto schermo sono state spostate in **Modalità tutto schermo**. Attualmente, le impostazioni **Web browser in modalità tutto schermo** dispongono di una propria categoria nel portale di Azure.
Si applica a: Windows 10 e versioni successive




### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Applicare il profilo Autopilot ai dispositivi Windows 10 iscritti ma non ancora registrati per Autopilot <!-- 1558983 -->
È possibile applicare il profilo Autopilot ai dispositivi Windows 10 iscritti che non sono stati ancora registrati per Autopilot. Nel profilo di Autopilot, scegliere l'opzione **Converti tutti i dispositivi interessati in Autopilot** per registrare automaticamente i dispositivi non Autopilot con il servizio di distribuzione Autopilot. L'elaborazione della registrazione può richiedere fino a 48 ore. Quando la registrazione viene annullata e il dispositivo viene reimpostato, Autopilot eseguirà il provisioning.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>Creare e assegnare vari profili di pagina relativa allo stato della registrazione ai gruppi di Azure AD <!-- 2526564 -->
È ora possibile [creare e assegnare](windows-enrollment-status.md) vari profili di pagina relativa allo stato della registrazione ai gruppi di Azure AD.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Migrazione da Device Enrollment Program ad Apple Business Manager in Intune <!--2748613-->
Apple Business Manager (ABM) funziona in Intune ed è possibile aggiornare l'account da Device Enrollment Program (DEP) ad ABM. Il processo in Intune è lo stesso. Per aggiornare l'account Apple da DEP ad ABM, passare a [ https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817).

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>Schede per gli avvisi e lo stato di registrazione nella pagina di panoramica di registrazione del dispositivo <!--2748656-->
Gli avvisi e gli errori di registrazione vengono ora visualizzati in schede separate nella pagina di panoramica di registrazione del dispositivo.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Limitare le app e bloccare l'accesso alle risorse aziendali nei dispositivi Android <!-- 2451462  -->  
In **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Android** > **Sicurezza del sistema** è presente una nuova impostazione nella sezione *Sicurezza dei dispositivi*, denominata **App con restrizioni**. L'impostazione **App con restrizioni** usa un criterio di conformità per impedire l'accesso alle risorse aziendali se determinate app vengono installate nel dispositivo. Il dispositivo è considerato non conforme fino a quando non vengono rimosse le app con restrizioni dal dispositivo.
Si applica a: 
- Android




## <a name="week-of-september-24-2018"></a>Settimana del 24 settembre 2018

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Interfaccia di amministrazione di Gestione di dispositivi Microsoft 365 <!-- 3078424 -->
Tra le promesse di Microsoft 365 c'è quella di semplificare l'amministrazione pertanto, nel corso degli anni, i servizi di Microsoft 365 back-end sono stati integrati per offrire scenari end-to-end, ad esempio l'accesso condizionale di Intune e Azure AD. La nuova [interfaccia di amministrazione di Microsoft 365](http://devicemanagement.microsoft.com) è il centro in cui consolidare, semplificare e integrare l'esperienza di amministrazione. Quest'area di lavoro specializzata per la gestione dei dispositivi consente di accedere facilmente a tutte le informazioni e attività per la gestione dei dispositivi e delle app che servono all'organizzazione. Prevediamo che diventerà l'area di lavoro cloud principale per i team informatici degli utenti finali.

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>Supporto per un maggior numero di autorità di certificazione di terze parti <!-- 3093107 -->
Utilizzando il Simple Certificate Enrollment Protocol (SCEP), è ora possibile rilasciare nuovi certificati e rinnovare i certificati esistenti su dispositivi mobili con Windows, iOS, Android e macOS.

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune supporta iOS 10 e versioni successive <!-- 2454656 -->  
Il servizio di registrazione di Intune, l'app Portale aziendale e Managed Browser ora supportano solo dispositivi iOS che eseguono iOS 10 e versioni successive. Per cercare i dispositivi o gli utenti interessati nell'organizzazione, passare a Intune nel portale di Azure > **Dispositivi** > **Tutti i dispositivi**. Filtrare in base al sistema operativo e quindi fare clic su **Colonne** per visualizzare i dettagli della versione del sistema operativo. Chiedere a questi utenti di aggiornare i dispositivi a una versione supportata del sistema operativo.  

Con i dispositivi inclusi nell'elenco seguente o se si vuole registrare un dispositivo tra quelli elencati, tenere presente che questi supportano solo iOS 9 e versioni precedenti.  Per continuare ad accedere al Portale aziendale Intune, è necessario aggiornare questi dispositivi a dispositivi che supportano iOS 10 o versioni successive:  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (terza generazione) 
* iPad Mini (prima generazione)  

## <a name="week-of-september-17-2018"></a>Settimana del 17 settembre 2018

### <a name="app-management"></a>Gestione delle app

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>Rimuovere la duplicazione dei riquadri Stato di protezione dell'app <!-- 3083391 -->
I riquadri **Stato utente per iOS** e **Stato utente per Android** erano presenti nella pagina **App client - Panoramica** e anche nella pagina **App client - Stato di protezione dell'app**. I riquadri dello stato sono stati rimossi dalla pagina **App client - Panoramica** per evitare la duplicazione. 

## <a name="week-of-august-27-2018"></a>Settimana del 27 agosto 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>Supporto del tunnel di pacchetti per profili VPN per app iOS per i tipi di connessione personalizzata e Pulse Secure <!-- 1520957 -->
Quando si usano i profili VPN per app iOS, è possibile usare il tunneling a livello di app (proxy delle app) o il tunneling a livello di pacchetto (tunnel di pacchetti). Queste opzioni sono disponibili con i tipi di connessione seguenti:
- VPN personalizzata
- Pulse Secure Se non si conosce il valore da usare, consultare la documentazione del provider VPN.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>Ritardo quando vengono visualizzati gli aggiornamenti del software iOS sul dispositivo <!-- 1949583 -->
In Intune > **Aggiornamenti software** > **Criteri di aggiornamento per iOS** è possibile configurare i giorni e gli orari in cui i dispositivi non devono installare aggiornamenti. In un aggiornamento futuro sarà possibile rimandare il momento in cui visualizzare un aggiornamento software sul dispositivo, da 1 a 90 giorni. 
Per le impostazioni correnti, vedere [Configurare i criteri di aggiornamento per iOS in Microsoft Intune](software-updates-ios.md).

#### <a name="office-365-proplus-version----2213968---"></a>Versione di Office 365 ProPlus <!-- 2213968 -->
Durante l'assegnazione delle app di Office 365 ProPlus ai dispositivi Windows 10 con Intune, sarà possibile selezionare la versione di Office. Nel portale di Azure selezionare **Microsoft Intune** > **App** > **Aggiungi app**. Selezionare quindi **Office 365 ProPlus Suite (Windows 10)** nell'elenco a discesa **Tipo**. Selezionare **Impostazioni della suite di app** per visualizzare il pannello associato. Impostare **Canale di aggiornamento** su un valore, ad esempio **Ogni mese**. Rimuovere facoltativamente l'altra versione di Office (MSI) dai dispositivi degli utenti finali selezionando **Sì**. Selezionare **Specifica** per installare una versione specifica di Office per il canale selezionato nei dispositivi degli utenti finali. A questo punto, è possibile selezionare la **versione specifica** di Office da usare. Le versioni disponibili cambieranno nel corso del tempo. Quando si crea una nuova distribuzione, le versioni disponibili potrebbero quindi essere più recenti e alcune versioni precedenti potrebbero non essere disponibili. Le distribuzioni correnti continueranno a distribuire la versione precedente, ma l'elenco delle versioni verrà continuamente aggiornato per ogni canale. Per altre informazioni, vedere [Panoramica dei canali di aggiornamento per Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus).

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Supporto per l'impostazione di registrazione DNS per VPN di Windows 10 <!-- 2282852 -->
Con questo aggiornamento sarà possibile configurare i profili VPN di Windows 10 per registrare in modo dinamico gli indirizzi IP assegnati all'interfaccia VPN con il DNS interno, senza dover usare profili personalizzati.
Per informazioni sulle impostazioni dei profili VPN disponibili, vedere [Impostazioni VPN di Windows 10 in Intune](vpn-settings-windows-10.md). 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>Il programma di installazione di Portale aziendale di macOS ora include il numero di versione nel nome del file del programma di installazione <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>Aggiornamenti dell'app iOS automatici <!-- 2729759 -->
Gli aggiornamenti automatici delle app funzionano sia per le app con licenza per dispositivo che per utente per iOS versione 11.0 e versioni successive.




### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello avrà come destinazione utenti e dispositivi <!-- 1106609 -->
Quando si crea un criterio di [Windows Hello for Business](windows-hello.md), questo viene applicato a tutti gli utenti dell'organizzazione (a livello di tenant). Con questo aggiornamento, il criterio può essere applicato anche a utenti specifici o a dispositivi specifici usando un criterio di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Identity Protection** > **Windows Hello for Business**).
In Intune nel portale di Azure la configurazione e le impostazioni di Windows Hello ora esistono sia in **Registrazione del dispositivo** che in **Configurazione del dispositivo**. **Registrazione del dispositivo** è associato all'intera organizzazione (a livello di tenant) e supporta Windows AutoPilot (Configurazione guidata). **Configurazione del dispositivo** è associato a dispositivi e utenti tramite un criterio applicato durante l'archiviazione.
Questa funzionalità si applica a:  
- Windows 10 e versioni successive
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler è una connessione disponibile per i profili VPN in iOS <!-- 1769858 -->
Quando si crea un profilo di configurazione del dispositivo VPN iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** >  piattaforma **iOS** > tipo di profilo **VPN**), sono disponibili diversi tipi di connessione, inclusi Cisco, Citrix e altri. Questo aggiornamento aggiunge Zscaler come tipo di connessione. 
Per i tipi di connessione disponibili, vedere [Impostazioni VPN per i dispositivi che eseguono iOS](vpn-settings-ios.md).

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Modalità FIPS per i profili Wi-Fi aziendale per Windows 10 <!-- 1879077 -->
È ora possibile abilitare la modalità Federal Information Processing Standards (FIPS) per i profili Wi-Fi aziendale per Windows 10 nel portale di Intune di Azure. Assicurarsi che la modalità FIPS sia abilitata nell'infrastruttura Wi-Fi se è necessario attivarla nei profili Wi-Fi.
Vedere [Impostazioni Wi-Fi per dispositivi Windows 10 e versioni successive in Intune](wi-fi-settings-windows.md) per informazioni su come creare un profilo Wi-Fi.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Controllare la modalità S in dispositivi Windows 10 e versioni successive - anteprima pubblica <!-- 1958649 -->
Con questo aggiornamento di funzionalità è possibile creare un profilo di configurazione del dispositivo per disattivare la modalità S in un dispositivo Windows 10 o impedire agli utenti di disattivare la modalità S nel dispositivo. Questa funzionalità è disponibile in Intune > **Configurazione del dispositivo** > **Profili** >  **Windows 10 e versioni successive** > **Edition upgrade and mode switch** (Aggiornamento edizione e cambio modalità).
Per altre informazioni sulla modalità S, vedere [Ti presentiamo Windows 10 in modalità S](https://www.microsoft.com/windows/s-mode).
Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Pacchetto di configurazione Windows Defender ATP aggiunto automaticamente al profilo di configurazione <!-- 2144658 -->
Quando vengono usati [Advanced Threat Protection e l'onboarding](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) in Intune, è necessario prima eseguire il download di un pacchetto di configurazione da aggiungere al profilo di configurazione. Con questo aggiornamento Intune ottiene il pacchetto automaticamente da Windows Defender Security Center e lo aggiunge al profilo.
Si applica a Windows 10 e versioni successive.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>Richiedere agli utenti di connettersi durante la configurazione del dispositivo <!--2311457-->
Ora è possibile configurare i profili del dispositivo in modo da richiedere che il dispositivo si connetta a una rete prima di passare oltre la pagina Rete durante la configurazione di Windows 10. Quando questa funzionalità è disponibile in anteprima, è necessaria una build 1809 o successiva di Windows Insider per usare questa impostazione.
Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>Limitare le app e bloccare l'accesso alle risorse aziendali nei dispositivi iOS e Android Enterprise<!-- 2451462 -->
In **Conformità del dispositivo** > **Criteri** > **Crea criterio** > **iOS** > **Sicurezza del sistema** è disponibile una nuova impostazione **Restricted applications** (Applicazioni con restrizioni). Questa nuova impostazione usa un criterio di conformità per impedire l'accesso alle risorse aziendali se determinate app vengono installate nel dispositivo. Il dispositivo è considerato non conforme fino a quando non vengono rimosse le app con restrizioni dal dispositivo.
Si applica a: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>Aggiornamenti del supporto della VPN moderna per iOS <!-- 2459928, 1819876, and 2650856 -->
L'aggiornamento aggiunge il supporto per i client VPN iOS seguenti: 
- F5 Access (versione 3.0.1 e successive)
- Citrix SSO
- Palo Alto Networks GlobalProtect (versione 5.0 e successive) Sempre in questo aggiornamento:
- Il tipo di connessione esistente **F5 Access** è stato rinominato **F5 Access Legacy** per iOS.
- Il tipo di connessione **Palo Alto Networks GlobalProtect** esistente è stato rinominato **Palo Alto Networks GlobalProtect (legacy)** per iOS.
I profili esistenti con questi tipi di connessione continuano a funzionare con il client VPN legacy relativo. Se si usa Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN o Palo Alto Networks GlobalProtect versione 4.1 e versioni precedenti con iOS, è consigliabile passare alle nuove app. Effettuare questo passaggio il prima possibile per assicurarsi che l'accesso VPN sia disponibile per i dispositivi iOS quando viene eseguito l'aggiornamento a iOS 12.
Per altre informazioni su iOS 12 e i profili VPN, vedere il [blog del team di supporto di Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2013806).

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Esportare i criteri di conformità dal portale di Azure classico per ricrearli nel portale di Intune di Azure <!-- 2469637 -->
I criteri di conformità creati nel portale di Azure classico saranno deprecati. È possibile rivedere ed eliminare i criteri di conformità esistenti ma non aggiornarli. Se è necessario eseguire la migrazione di criteri di conformità al portale di Intune di Azure, è possibile esportare i criteri come file con valori delimitati da virgole (file con estensione *csv*). In seguito, usare i dettagli del file per ricreare i criteri nel portale di Intune di Azure.

> [!IMPORTANT]
> Quando il portale di Azure classico verrà ritirato, non sarà più possibile accedere ai criteri di conformità né visualizzarli. Assicurarsi quindi di esportarli e crearli nel portale di Azure prima che il portale di Azure classico venga ritirato.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile: un nuovo partner di Mobile Threat Defense <!-- 22662717 -->
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi condotta da Better Mobile, una soluzione Mobile Threat Defense integrata in Microsoft Intune.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>Bloccare il portale aziendale nella modalità app singola fino all'accesso dell'utente <!--1067692 --> 
Ora è possibile eseguire Portale aziendale in modalità app singola se si autentica un utente tramite Portale aziendale invece che tramite Assistente configurazione durante la registrazione DEP. Questa opzione blocca il dispositivo immediatamente dopo il completamento di Assistente configurazione così che un utente deve effettuare l'accesso per accedere al dispositivo. Questo processo assicura che il dispositivo completi l'onboarding e non rimanga orfano in uno stato senza utenti associati.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Assegnare un utente e un nome descrittivo a un dispositivo di Autopilot <!--1346521 -->
Ora è possibile [assegnare un utente a un dispositivo Autopilot singolo](enrollment-autopilot.md). Gli amministratori potranno anche assegnare nomi descrittivi per rivolgersi all'utente quando configura il dispositivo con Autopilot.
Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Usare le licenze di dispositivo VPP per effettuare il provisioning anticipato del portale aziendale durante la registrazione DEP <!-- 1608345 -->
È ora possibile usare le licenze di dispositivo Volume Purchase Program (VPP) per eseguire il provisioning anticipato del portale aziendale durante le registrazioni DEP (Device Enrollment Program). A tale scopo, quando si [crea o si modifica un profilo di registrazione](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile), specificare il token VPP che si vuole usare per installare il portale aziendale. Assicurarsi che il token non abbia una scadenza e di avere un numero sufficiente di licenze per l'app del portale aziendale. Se il token ha una scadenza o se il numero di licenze è insufficiente, Intune esegue il push del portale aziendale dell'App Store (che richiederà l'immissione di un ID Apple).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Conferma richieste per l'eliminazione del token VPP usato per il provisioning anticipato del portale aziendale <!-- 2237634 -->
Viene ora richiesta la conferma dell'eliminazione di un token VPP (Volume Purchase Program) se il token viene usato per il provisioning anticipato del Portale aziendale durante la registrazione DEP.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Bloccare le registrazioni dei dispositivi personali Windows <!-- 1849498 -->
È possibile [bloccare la registrazione di dispositivi personali Windows](windows-enroll.md) con la [gestione di dispositivi mobili](enrollment-restrictions-set.md#set-device-type-restrictions) in Intune. I dispositivi registrati con l'[agente del computer di Intune](manage-windows-pcs-with-microsoft-intune.md) non possono essere bloccati con questa funzionalità. Questa funzionalità verrà implementata nelle prossime due settimane e potrebbe non apparire immediatamente nell'interfaccia utente.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Specificare i modelli di nome computer in un profilo di Autopilot <!--1849855-->
È possibile [specificare un modello di nome computer](enrollment-autopilot.md#create-an-autopilot-deployment-profile) per generare e impostare il [nome computer](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) durante la registrazione di Autopilot. Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Per i profili di Windows Autopilot, nascondere le opzioni per cambiare l'account nella pagina di accesso aziendale e nella pagina degli errori di dominio <!--1901669 -->
Sono disponibili [nuove opzioni del profilo di Windows Autopilot](enrollment-autopilot.md#create-an-autopilot-deployment-profile) che consentono agli amministratori di nascondere le opzioni per cambiare l'account nelle pagine di accesso aziendale e degli errori di dominio. Per nascondere queste opzioni, è necessario configurare le informazioni personalizzate distintive dell'azienda in Azure Active Directory. Si applica alla build [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) più recente (durante l'anteprima).



### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="delete-jamf-devices----2653306--"></a>Eliminare i dispositivi Jamf <!-- 2653306-->
È possibile eliminare i dispositivi gestiti da JAMF tramite **Dispositivi** > scegliere il dispositivo Jamf > **Elimina**.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>Modifica delle terminologia in "ritirare" e "cancellare" <!-- 2175759 -->
Per garantire la coerenza con l'API Graph, nell'interfaccia utente e nella documentazione di Intune sono stati modificati i termini seguenti:
- **Rimuovi i dati aziendali** viene modificato in "ritirare"
- **Ripristino delle impostazioni predefinite** verrà cambiato in **cancellare**

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>Finestra di dialogo di conferma se l'amministratore tenta di eliminare un certificato push MDM <!-- 297909500-->
Se si tenta di eliminare un certificato push MDM di Apple, viene visualizzata una finestra di dialogo di conferma con il numero dei dispositivi iOS e macOS correlati. Se il certificato viene eliminato, i dispositivi dovranno essere registrati nuovamente.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Impostazioni di protezione aggiuntive per Windows Installer <!-- 2282430 -->
Gli utenti possono controllare l'installazione delle app. Se l'opzione è abilitata, le installazioni che a causa di una violazione della protezione verrebbero arrestate possono precedere. È possibile indicare a Windows Installer di usare privilegi elevati durante l'installazione di un qualsiasi programma in un sistema. È anche possibile indicizzare gli elementi Windows Information Protection e archiviare i relativi metadati in una posizione non crittografata. Quando i criteri sono disabilitati, gli elementi protetti da WIP non vengono indicizzati e non appaiono nei risultati di Cortana o Esplora file. Le funzionalità per queste opzioni sono disabilitate per impostazione predefinita. 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>Nuova esperienza utente per il sito Web del portale aziendale <!--2000968 -->
Sono state aggiunte nuove funzionalità, in base ai suggerimenti dei clienti, al sito Web Portale aziendale. Si noterà un miglioramento significativo delle funzionalità esistenti e dell'usabilità dei dispositivi. Diverse aree del sito, come ad esempio i dettagli del dispositivo, i commenti e suggerimenti, il supporto e la panoramica del dispositivo, presentano una nuova progettazione, moderna e reattiva. Saranno inoltre disponibili:

- Flussi di lavoro semplificati in tutte le piattaforme per dispositivi
- Flussi di identificazione e registrazione dei dispositivi ottimizzati
- Messaggi di errore più utili
- Linguaggio più semplice con meno gergo tecnico
- Possibilità di condividere collegamenti diretti alle app
- Miglioramento delle prestazioni per i cataloghi di app di grandi dimensioni
- Maggiore accessibilità per tutti gli utenti  

La [documentazione di sito Web Portale aziendale di Intune](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website) è stata aggiornata per riflettere tali modifiche. Per visualizzare un esempio dei miglioramenti apportati alle app, vedere [Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune](whats-new-app-ui.md).  

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>Rilevamento delle manomissioni con jailbreak migliorato nel report sulla conformità<!-- 2198738 -->
Gli stati delle impostazioni del rilevamento delle manomissioni con jailbreak migliorato ora vengono visualizzati nel report di conformità nella console di amministrazione.

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-for-policies---1081974---"></a>Tag di ambito per i criteri <!--1081974 -->
È possibile [creare tag di ambito](scope-tags.md) per limitare l'accesso alle risorse di Intune. Aggiungere un tag di ambito a un'assegnazione di ruolo e quindi aggiungere il tag di ambito a un profilo di configurazione. Il ruolo potrà accedere solo alle risorse con profili di configurazione con tag di ambito corrispondenti (o nessun tag di ambito).

## <a name="week-of-august-14-2018"></a>Settimana del 14 agosto 2018

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Supporto macOS per il Device Enrollment Program di Apple<!-- 747651 -->
Intune supporta ora la registrazione dei dispositivi macOS nel Device Enrollment Program (DEP) di Apple. Per altre informazioni, vedere [Registrare automaticamente i dispositivi macOS nel programma Device Enrollment Program di Apple](device-enrollment-program-enroll-macos.md).

## <a name="week-of-july-23-2018"></a>Settimana del 23 luglio 2018

### <a name="app-management"></a>Gestione delle app

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>Supporto di app line-of-business (LOB) per macOS <!-- 1895847 -->
Microsoft Intune consente la distribuzione di app line-of-business per macOS come app **obbligatorie** o **disponibili con registrazione**. Gli utenti finali possono ottenere le app distribuite come app **disponibili** tramite il Portale aziendale per macOS o il [sito Web del Portale aziendale](https://portal.manage.microsoft.com).

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>Supporto app integrato di iOS per modalità tutto schermo <!-- 2051098 -->
Oltre alle App Store e App gestite, è ora possibile selezionare un'App predefinita, ad esempio, Safari, da eseguire in modalità tutto schermo in un dispositivo iOS.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Modificare le distribuzioni delle app di Office 365 Pro Plus <!-- 2150145 -->
Per l'amministratore di Microsoft Intune è più facile modificare le distribuzioni delle app di Office 365 Pro Plus. Inoltre, non è più necessario eliminare le distribuzioni per modificare le proprietà del gruppo. Nel portale di Azure selezionare **Microsoft Intune** > **App client** > **App**. Selezionare la famiglia di prodotti Office 365 Pro Plus dall'elenco delle applicazioni.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>È ora disponibile una versione aggiornata di Intune App SDK per Android<!-- 2744271-->

È disponibile una versione aggiornata di Intune App SDK per Android per il supporto della versione Android P. Gli sviluppatori di app che usano Intune SDK per Android devono installare la versione aggiornata di Intune App SDK per garantire che le funzionalità di Intune nelle app Android continuino a funzionare come previsto nei dispositivi Android P. Questa versione di Intune App SDK offre un plug-in predefinito che esegue gli aggiornamenti dell'SDK. Non occorre riscrivere il codice esistente integrato. Per informazioni dettagliate, vedere [Intune SDK per Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android). Se si usa il vecchio stile con lo scudo per Intune, è consigliabile usare l'icona a forma di valigetta. Per informazioni dettagliate sulla personalizzazione, vedere [questo repository GitHub](https://github.com/msintuneappsdk/intune-app-partner-badge).


### <a name="device-configuration"></a>Configurazione del dispositivo

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

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Modalità tutto schermo obsoleta appare disattivata e non può essere modificata <!-- 2149998 -->
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

Nei dispositivi degli utenti finali il client Intune esegue un'azione basata su una semplice corrispondenza delle stringhe specificate nel pannello Intune per i criteri di protezione delle applicazioni. Ciò dipende completamente dal valore segnalato dal dispositivo. Di conseguenza, è opportuno che l'amministratore IT si assicuri che il comportamento previsto sia accurato. A tale scopo, è possibile testare questa impostazione con svariati produttori di dispositivi e modelli destinati a un piccolo gruppo di utenti. In Microsoft Intune selezionare **App client** > **Criteri di protezione delle app** per visualizzare e aggiungere criteri di protezione delle app. Per altre informazioni sui criteri di protezione delle app, vedere [Che cosa sono i criteri di protezione delle app?](app-protection-policy.md) e [Cancellare i dati in modo selettivo usando le azioni di accesso per i criteri di protezione delle app in Intune](app-protection-policies-access-actions.md).

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
Se è stato abilitato il [mapping del gruppo di dispositivi](https://docs.microsoft.com/intune/device-group-mapping), agli utenti di Windows 10 sarà ora richiesto di selezionare una categoria di dispositivi dopo la registrazione usando il pulsante **Connetti** in **Impostazioni** > **Account** > **Accedi all'azienda o all'istituto di istruzione**. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Usare sAMAccountName come nome utente dell'account per i profili di posta elettronica <!-- 1500307 -->
È possibile usare l'oggetto **sAMAccountName** locale come nome utente dell'account per i profili di posta elettronica per Android, iOS e Windows 10. È anche possibile ottenere il dominio dall'attributo `domain` o `ntdomain` in Azure Active Directory (Azure AD). In alternativa, immettere un dominio personalizzato statico.

Per usare questa funzionalità, è necessario sincronizzare l'attributo `sAMAccountName` dell'ambiente Active Directory locale con Azure AD.

Si applica a: [Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 e versioni successive](email-settings-windows-10.md)

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
Quando si crea un criterio di conformità del dispositivo (**Conformità del dispositivo** > **Criteri** > **Crea criterio** > **Piattaforma: Windows 10 e versioni successive** > **Impostazioni** > **Sicurezza del sistema**), sono disponibili nuove opzioni per **[Sicurezza dei dispositivi](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)**: 
- **Antivirus**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando le soluzioni antivirus registrate nel Centro sicurezza PC Windows, ad esempio Symantec e Windows Defender. 
- **AntiSpyware**: se impostata come **obbligatoria**, l'opzione consente di verificare la conformità usando le soluzioni antispyware registrate nel Centro sicurezza PC Windows, ad esempio Symantec e Windows Defender. 

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

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Supporto di Microsoft Edge in dispositivi mobili per i criteri di protezione delle app di Intune <!-- 1817882 -->

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

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Supporto per i profili VPN di Palo Alto Networks GlobalProtect <!-- 1333680 ! -->
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

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>Supporto per la registrazione di Windows Autopilot senza l'autenticazione utente <!-- 1165118 -->
Intune ora supporta la registrazione di Windows Autopilot senza l'autenticazione utente. Si tratta della nuova opzione del profilo di distribuzione di Windows Autopilot "Modalità di distribuzione Autopilot" che viene impostata sulla distribuzione automatica.  Il dispositivo deve eseguire Windows 10 Insider Preview Build 17672 o versione successiva e possedere un chip TPM 2.0 per completare questo tipo di registrazione. Poiché non è necessaria l'autenticazione utente, è consigliabile assegnare questa opzione solo ai dispositivi su cui si ha controllo fisico.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Nuova impostazione per lingua/area quando si configura la Configurazione guidata per Autopilot <!-- 1821766 -->
È disponibile una nuova impostazione di configurazione per impostare la lingua e l'area dei profili di Autopilot durante la Configurazione guidata. Per visualizzare questa nuova impostazione, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo** > **Modalità di distribuzione** = **Self-deploying (Distribuzione automatica)** > **Impostazioni predefinite configurate**.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>Nuova impostazione per configurare la tastiera del dispositivo <!-- 1821768 -->
Sarà disponibile una nuova impostazione per configurare la tastiera per i profili di Autopilot durante la Configurazione guidata. Per visualizzare questa nuova impostazione, scegliere **Registrazione del dispositivo** > **Registrazione Windows** > **Profili di distribuzione** > **Crea profilo** > **Modalità di distribuzione** = **Self-deploying (Distribuzione automatica)** > **Impostazioni predefinite configurate**.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Spostamento dei profili AutoPilot nei gruppi di destinazione <!-- 1877935 -->
I profili di distribuzione di AutoPilot possono essere assegnati ai gruppi di Azure AD contenenti dispositivi AutoPilot.

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="set-compliance-by-device-location----851881----"></a>Impostare la conformità in base al percorso del dispositivo <!-- 851881 ! -->
In alcuni casi, potrebbe essere necessario limitare l'accesso alle risorse aziendali a un percorso specifico, definito da una connessione di rete. È ora possibile creare un criterio di conformità (**Conformità del dispositivo** > **Percorsi**) basato sull'indirizzo IP del dispositivo. Se il dispositivo non è più compreso nell'intervallo di IP, non può accedere alle risorse aziendali.

Si applica a: Dispositivi Android 6.0 e versioni successive, con l'app Portale aziendale aggiornata

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Evitare app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot<!-- 1621980 -->
Sarà possibile impedire l'installazione di app ed esperienze consumer nei dispositivi Windows 10 Enterprise RS4 AutoPilot. Per vedere questa funzionalità, passare a **Intune** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Piattaforma** = **Windows 10 o versione successiva** > **Tipo di profilo** = **Limitazioni del dispositivo** > **Configura** > **Windows Spotlight** > **Funzionalità consumer**. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Disinstallare gli aggiornamenti più recenti dagli aggiornamenti software di Windows 10 <!-- 1732948 -->
Se si rileva un problema di rilievo nei computer Windows 10, è possibile scegliere di disinstallare l'ultimo aggiornamento delle funzionalità oppure l'ultimo aggiornamento qualitativo ripristinando lo stato precedente. La disinstallazione di un aggiornamento delle funzionalità o di un aggiornamento qualitativo è disponibile solo per il canale di manutenzione su cui è attivo il dispositivo. La disinstallazione attiverà un criterio per il ripristino dell'aggiornamento precedente nei computer Windows 10. In particolare per gli aggiornamenti delle funzionalità, è possibile limitare a un intervallo di giorni compreso tra 2 e 60 la disinstallazione dell'ultima versione. Per impostare le opzioni di disinstallazione dell'aggiornamento software, selezionare **Aggiornamenti software** dal pannello **Microsoft Intune** nel portale di Azure. Nel pannello **Aggiornamenti software** selezionare **Anelli di aggiornamento di Windows 10**. A questo punto è possibile scegliere l'opzione **Disinstalla** dalla sezione **Panoramica**.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>Cercare tutti i dispositivi IMEI e il numero di serie <!-- 1793685 -->
Nel pannello Tutti i dispositivi è ora possibile cercare codici IMEI e numeri di serie (sono ancora disponibili posta elettronica, UPN, nome del dispositivo e nome di gestione). In Intune scegliere **Dispositivi** > **Tutti i dispositivi** > e immettere la ricerca nella casella di ricerca.

#### <a name="management-name-field-will-be-editable----1875989---"></a>Il campo Nome di gestione sarà modificabile <!-- 1875989 -->
È ora possibile modificare il campo Nome di gestione nel pannello **Proprietà** di un dispositivo. Per modificare questo campo, scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Proprietà**. È possibile usare il campo Nome di gestione per identificare in modo univoco un dispositivo.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>Nuovo filtro Tutti i dispositivi: Categoria del dispositivo <!-- 1878520 -->
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

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>Informazioni UDID ora incluse per dispositivi iOS e macOS<!-- 2219806 -->
Per visualizzare le informazioni UDID (Unique Device Identifier) per i dispositivi iOS e macOS, passare a **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Hardware**. Le informazioni UDID sono disponibili solo per i dispositivi aziendali (come impostato in **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Proprietà** > **Proprietà del dispositivo**).

### <a name="intune-apps"></a>App di Intune

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Miglioramento della risoluzione dei problemi di installazione delle app <!-- 928990 -->
Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. È in corso la distribuzione di un'anteprima pubblica delle funzionalità di risoluzione dei problemi delle app. Sotto ogni singolo dispositivo si noterà un nuovo nodo denominato **App gestite**, che elenca le app distribuite tramite MDM di Intune. Nel nodo è visibile un elenco di stati di installazione delle app. Se si seleziona una singola app, si noterà la visualizzazione relativa alla risoluzione dei problemi per l'app specifica. In tale visualizzazione è presente il ciclo di vita end-to-end dell'app, ad esempio quando l'app è stata creata, modificata, specificata come destinazione e distribuita in un dispositivo. Se l'installazione dell'app non è riuscita, saranno anche disponibili il codice di errore e un messaggio sulla causa dell'errore. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Criteri di protezione delle app di Intune e Microsoft Edge <!-- 1818968 -->
Il browser Microsoft Edge per dispositivi mobili (iOS e Android) ora supporta i criteri di protezione delle app di Microsoft Intune. Gli utenti di dispositivi iOS e Android che accedono con gli account Azure AD aziendali nell'applicazione Edge saranno protetti da Intune. Nei dispositivi iOS il criterio **Require managed browser for web content** (Richiedi Managed Browser per contenuti Web) consentirà agli utenti di aprire i collegamenti in Microsoft Edge quando è gestito.

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
Microsoft Intune offrirà la possibilità di installare app LOB (line-of-business) macOS dal portale di Azure. Sarà possibile aggiungere un'app LOB macOS a Intune dopo una pre-elaborazione effettuata dallo strumento disponibile in GitHub. Nel portale di Azure scegliere **App client** dal pannello **Intune**. Nel pannello **App client** scegliere **App** > **Aggiungi**. Nel pannello **Aggiungi app** selezionare **App line-of-business**. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Gruppi predefiniti Tutti gli utenti e Tutti i dispositivi per l'assegnazione di app del profilo di lavoro di Android Enterprise <!-- 1813073 -->
È possibile usare i gruppi predefiniti **Tutti gli utenti** e **Tutti i dispositivi** per l'assegnazione di app del profilo di lavoro di Android Enterprise. Per altre informazioni, vedere [Includere ed escludere assegnazioni di app in Microsoft Intune](apps-inc-exl-assignments.md).

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune reinstallerà le app richieste disinstallate dagli utenti <!-- 1947010 -->
Se un utente finale disinstalla un'app richiesta, Intune reinstalla automaticamente l'app entro 24 ore invece di attendere il ciclo di rivalutazione di 7 giorni.

### <a name="device-configuration"></a>Configurazione del dispositivo

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>Visualizzazione di tutti i dispositivi di un gruppo nel grafico dei profili e nell'elenco dello stato dei dispositivi <!-- 1449153 -->
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

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>Visualizzare l'ID chiamante nel profilo personale - Profilo di lavoro di Android Enterprise <!--1098984 -->
Quando si usa un profilo personale in un dispositivo, è possibile che gli utenti finali non visualizzino i dettagli dell'ID del chiamante da un contatto di lavoro. 

Dopo questo aggiornamento, sarà presente una nuova impostazione in **Android Enterprise** > **Limitazioni del dispositivo** > **Impostazioni del profilo di lavoro**:
- Visualizzare l'ID chiamante del contatto di lavoro nel profilo personale

Se abilitati (non configurati), i dettagli del chiamante del contatto di lavoro vengono visualizzati nel profilo personale. Se bloccato, il numero del chiamante del contatto di lavoro non viene visualizzato nel profilo personale. 

Si applica a: dispositivi di profilo di lavoro Android in sistemi operativi Android 6.0 e versioni successive

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>Nuove impostazioni di Windows Defender Credential Guard aggiunte alle impostazioni di Endpoint Protection <!--1102252 --><!--from 1802 and 1804-->

Con questo aggiornamento, [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) (**Configurazione del dispositivo** > **Profili** > **Endpoint Protection**) include le impostazioni seguenti: 

- **Windows Defender Credential Guard**: attiva Credential Guard con la sicurezza basata su virtualizzazione. Questa funzionalità, se abilitata, consente di proteggere le credenziali al riavvio successivo quando il **livello di sicurezza della piattaforma con avvio protetto** e la **sicurezza basata sulla virtualizzazione** sono entrambi abilitati. Le opzioni includono:
  - **Disabilitato**: se Credential Guard è stato attivato in precedenza con l'opzione **Abilitato senza blocco**, disattiva Credential Guard in modalità remota.

  - **Abilitato con blocco UEFI**: garantisce che Credential Guard non possa essere disabilitato con una chiave del Registro di sistema o con Criteri di gruppo. Per disabilitare Credential Guard dopo avere usato questa impostazione, è necessario impostare Criteri di gruppo su "Disabilitato", quindi rimuovere la funzionalità di sicurezza da ogni computer, con un utente fisicamente presente. Questi passaggi cancellano la configurazione permanente in UEFI. Credential Guard rimane abilitato fino a quando è presente la configurazione UEFI.

  - **Abilitato senza blocco**: consente di rimuovere Credential Guard in modalità remota usando Criteri di gruppo. È necessario che i dispositivi che usano questa impostazione eseguano Windows 10 (versione 1511 o successiva).

Quando si configura Credential Guard vengono automaticamente abilitate le tecnologie dipendenti seguenti: 

  - **Abilita la sicurezza basata su virtualizzazione**: attiva la sicurezza basata su virtualizzazione al riavvio successivo. La sicurezza basata sulla virtualizzazione usa Windows Hypervisor per offrire il supporto per i servizi di sicurezza e richiede Avvio protetto.
  - **Secure Boot with Direct Memory Access (DMA)** (Avvio protetto con Direct Memory Access): attiva VBS con Avvio protetto e Direct Memory Access. La protezione DMA richiede supporto hardware e viene abilitata solo nei dispositivi configurati correttamente. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>Usare un nome oggetto personalizzato sul certificato SCEP <!-- 2064190 -->
È possibile usare **OnPremisesSamAccountName**, il nome comune in un oggetto personalizzato in un profilo certificato SCEP. È ad esempio possibile usare `CN={OnPremisesSamAccountName})`.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Bloccare la fotocamera e l'acquisizione di schermate nei profili di lavoro di Android Enterprise <!-- 1098977 -->
Sono disponibili due nuove proprietà di blocco utilizzabili durante la configurazione delle restrizioni per i dispositivi Android: 
- Fotocamera: blocca l'accesso a tutte le fotocamere del dispositivo
- Acquisizione schermo: blocca l'acquisizione di schermate e impedisce anche la visualizzazione del contenuto nei dispositivi di visualizzazione privi di output video protetto

Si applica ai profili di lavoro di Android Enterprise.


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>Nuovi passaggi di registrazione degli utenti per i dispositivi con macOS High Sierra 10.13.2 e versioni successive <!--1734567 -->
macOS high Sierra 10.13.2 ha introdotto il concetto di registrazione MDM "approvata dall'utente". Le registrazioni approvate consentono a Intune di gestire alcune impostazioni relative alla sicurezza. Per altre informazioni, vedere la documentazione del supporto Apple all'indirizzo https://support.apple.com/HT208019.

I dispositivi registrati tramite il portale aziendale macOS vengono considerati "approvati dall'utente" solo se l'utente finale apre Preferenze di Sistema e dichiara l'approvazione manualmente. A tal fine, il portale aziendale macOS ora indica agli utenti che usano macOS 10.13.2 e versioni successive di approvare manualmente la registrazione al termine dell'esecuzione di questa. La console di amministrazione di Intune indicherà se un dispositivo registrato è approvato dall'utente.



### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>Advanced Threat Protection (ATP) e Intune sono completamente integrati <!-- 1629303 -->

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

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune si adatta a Fluent Design System nell'app Portale aziendale per Windows 10 <!-- 1195010 -->
L'app Portale aziendale Intune per Windows 10 è stata aggiornata con la [visualizzazione della navigazione di Fluent Design System](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics). A lato dell'app si noterà un elenco verticale statico di tutte le pagine di primo livello. Fare clic su un collegamento per visualizzare rapidamente tutte le pagine e passare da una all'altra. Questo è il primo di molti aggiornamenti che saranno resi disponibili come parte del continuo impegno per creare un'esperienza più adattiva, empatica e familiare in Intune. Per visualizzare l'aspetto aggiornato, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

## <a name="week-of-april-16-2018"></a>Settimana del 16 aprile 2018

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>Usare il client Cisco AnyConnect per iOS <!-- 1333708 -->

Quando si crea un nuovo profilo VPN per iOS, sono disponibili ora due opzioni: **Cisco AnyConnect** e **Cisco Legacy AnyConnect**. I profili di Cisco AnyConnect supportano le versioni 4.0.7x e successive. I profili VPN di Cisco AnyConnect per iOS esistenti vengono contrassegnati con la dicitura **Cisco Legacy AnyConnect** e continuano a funzionare con Cisco AnyConnect 4.0.5x e versioni precedenti come accade oggi.

> [!NOTE]
> Questa modifica si applica solo a iOS. Continua a esistere una sola opzione Cisco AnyConnect per la piattaforma Android, i profili di lavoro di Android Enterprise e per la piattaforma macOS.

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
È ora possibile usare i criteri di protezione delle app e l'accesso condizionale di Intune per proteggere l'accesso ai dati di Exchange locali con Outlook Mobile. Per aggiungere o modificare i criteri di protezione delle app nel portale di Azure, selezionare **Microsoft Intune** > **App client** > **Criteri di protezione delle app**. Prima di usare questa funzionalità, assicurarsi che siano soddisfatti i [requisiti di Outlook per iOS e Android](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx).

## <a name="notices"></a>Notifiche

### <a name="upcoming-password-enforcement-change-for-macos-10142-in-intune---1873216--"></a>Imminente modifica dell'applicazione delle password per macOS 10.14.2 in Intune <!--1873216-->
Come annunciato in MC145129 nel luglio scorso, è prevista l'integrazione in Intune dell'impostazione di Apple rilasciata di recente, "Change Password at Next Auth" (Cambia password all'autenticazione successiva), per i dispositivi che eseguono macOS versioni 10.13 e successive. Attualmente si prevede di distribuire questa impostazione nel mese di febbraio per macOS 10.14.2 e versioni successive. 

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
La modifica influisce se si usa o si prevede di usare dispositivi che eseguono macOS 10.14.2 e versioni successive. Ora che Apple ha introdotto l'impostazione "Change Password at New Auth" (Cambia password all'autenticazione successiva), Intune può imporre agli utenti di aggiornare la password impostandone una conforme quando viene eseguito il push dei criteri password. Gli utenti di macOS riceveranno una richiesta di aggiornamento della password quando questa nuova funzionalità di Apple verrà integrata, anche se la password è già conforme. Si noti che se una password è già conforme e non si dispone di un requisito per la ripetizione delle password, gli utenti finali potranno eseguire l'aggiornamento alla propria password esistente. Gli utenti finali vedranno una richiesta di aggiornamento della password solo se provano a eseguire l'autenticazione o l'accesso al proprio dispositivo. Se si bloccano le risorse aziendali finché il dispositivo non viene contrassegnato come conforme, tenere presente che agli utenti finali con dispositivi con macOS 10.14.2 può essere impedito l'accesso alle risorse aziendali, ad esempio la posta elettronica o i siti di SharePoint, finché non reimpostano la password. In futuro, tutti gli aggiornamenti ai criteri password di configurazione e conformità imporranno agli utenti di destinazione di aggiornare le password. Una ricerca effettuata tra i clienti prima dell'implementazione di questa modifica ha indicato che la maggior parte dei clienti non sarà interessata dalla modifica, poiché gli utenti finali in genere aggiornano la password dopo aver ricevuto una richiesta di registrazione con password o aver reimpostato la password per garantire la conformità

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
È possibile informare il supporto tecnico. Questa pagina delle novità verrà aggiornata al momento dell'implementazione della modifica. Se non si vuole applicare questo criterio password del dispositivo macOS, è consigliabile annullare l'assegnazione del criterio macOS esistente o eliminarlo.

###<a name="plan-for-change-update-to-ios-setting-for-supervised-devices-in-the-intune-console"></a>Modifica prevista: aggiornamento dell'impostazione di iOS per i dispositivi con supervisione nella console di Intune  
Con l'aggiornamento di febbraio al servizio Intune, l'impostazione 'Abilitazione delle restrizioni nelle impostazioni del dispositivo' per i dispositivi iOS con supervisione viene rinominata in "Orario schermo (solo con supervisione)". Dopo questa modifica, l'esperienza utente finale cambierà in base alle versione di iOS.

####<a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Dopo che l'impostazione per "Abilitazione delle restrizioni nelle impostazioni del dispositivo (solo con supervisione)" è stata rinominata in "Orario schermo (solo con supervisione)", l'esperienza per i dispositivi con supervisione (dispositivi registrati con i programmi di registrazione Apple) è la seguente: 

Per i dispositivi in iOS 11.4 e versioni precedenti: questa impostazione può essere usata per impedire agli utenti di modificare le restrizioni dei dispositivi come avveniva in precedenza. Gli utenti finali non osserveranno alcuna modifica nell'esperienza.
 
Per i dispositivi in iOS 12 e versioni successive: Gli utenti finali non visualizzeranno più la scheda Restrizioni in Impostazioni > Generale > Gestione dispositivo > Management Profile (Profilo di gestione) > Restrizioni.
Questa scheda sarà invece inclusa in Impostazioni > Generale > Orario schermo. Se questa impostazione viene configurata su "Blocca", gli utenti non potranno cambiare le impostazioni di Orario schermo sui propri dispositivi, incluse le restrizioni a livello di contenuto e privacy.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Aggiornare le indicazioni per gli utenti finali in modo da segnalare il cambiamento nell'esperienza utente per i dispositivi aggiornati a iOS 12 e versioni successive.


###<a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Modifica prevista: modifiche del flusso di lavoro per la registrazione di iOS 12 in Intune
Apple ha annunciato alcune modifiche relative alla registrazione dei dispositivi iOS nei servizi di gestione di dispositivi mobili (MDM). La modifica sarà probabilmente presente nella versione di iOS della primavera 2019 e in tutte le versioni future di iOS.

####<a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Se gli utenti finali eseguono l'aggiornamento dei propri dispositivi a questa nuova versione di iOS 12 in primavera, ricordare che è presente un flusso di lavoro modificato ed è necessario eseguire passaggi aggiuntivi per completare la registrazione in Intune. Quando Apple introdurrà queste modifiche, gli utenti finali dovranno: •            Iniziare il processo di registrazione nell'app Portale aziendale per scaricare un profilo di gestione •            Andare a Impostazioni > Generale > Profili •            Selezionare il profilo corretto e fare clic fino a selezionare Installa •            Ritornare al Portale aziendale per completare la registrazione 

Questa operazione non interessa i dispositivi già registrati e aggiornati alla nuova versione di iOS, a meno che non si tratti di dispositivi non registrati e che quindi richiedono una registrazione da zero.
L'esperienza di registrazione nei dispositivi che eseguono iOS 12.1 o versione precedente non verrà modificata con questa nuova versione da Apple.

####<a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
È consigliabile aggiornare la documentazione e le indicazioni per gli utenti finali. È anche consigliabile informare il supporto tecnico di queste modifiche. Vi informeremo tramite il Centro messaggi e la pagina delle novità quando questa modifica verrà resa disponibile.

Fare clic su Informazioni aggiuntive per un post di blog del supporto tecnico con screenshot e un video del flusso di registrazione previsto.

####<a name="additional-information"></a>Informazioni aggiuntive
https://aka.ms/iOS_enrollment_changes

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Modifica prevista: Aggiornamento dell'esperienza utente all'app Portale aziendale per iOS
Siamo lieti di annunciare che Intune presto rilascerà un importante aggiornamento dell'esperienza utente all'app Portale aziendale per iOS. L'aggiornamento offrirà una riprogettazione visuale della home page con filtri avanzati e un accesso più rapido ad applicazioni e libri.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
L'aggiornamento dell'esperienza utente, pur conservando le attuali funzionalità del portale aziendale per iOS, conterrà quanto segue:
- Una home page con aspetto di iOS nativo 
- Funzionalità di filtro per gli elenchi di contenuti e ricerca, tra cui la possibilità di filtrare in base al tipo di contenuto (app o eBook) e alla disponibilità (gestione dei dispositivi obbligatoria o disponibile senza registrazione)
- Possibilità di cercare gli eBook
- Cronologia delle ricerche di app ed eBook Se si fa parte del programma Apple TestFlight, si riceverà una notifica sulla versione non definitiva dell'app Portale aziendale per iOS aggiornata di Intune quando diventa disponibile. Se non si fa parte del programma Apple TestFlight, si è ancora in tempo per registrarsi. La registrazione consente di usare l'app Portale aziendale aggiornata prima che sia disponibile per gli utenti finali. Si avrà anche l'opportunità di inviare commenti e suggerimenti direttamente al team di Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?
Non è necessario intraprendere alcuna azione. Queste modifiche verranno rilasciate in una versione imminente dell'app Portale aziendale per iOS. 

#### <a name="additional-information"></a>Informazioni aggiuntive
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>Modifica prevista: il connettore di Exchange Online per Intune non sarà disponibile in Intune <!-- 3105122 -->
Per semplificare l'esperienza con Exchange Online e l'accesso condizionale, verrà disabilitato il connettore 'da servizio a servizio' di Exchange Online per Intune.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Questo messaggio verrà ricevuto dai clienti che risultano usare la funzionalità del connettore 'da servizio a servizio' nel loro ambiente. Il connettore 'da servizio a servizio' supporta solo la gestione di Intune dei dispositivi Exchange Active Sync per Exchange Online e non supporta l'infrastruttura locale. Questo connettore, a causa del modo in cui è visualizzato nella console, sembra necessario per l'accesso condizionale, ma in realtà non è richiesto. Con l'aggiornamento di febbraio al servizio Intune, per chiarire questa situazione nella console verrà disabilitato il pulsante per configurare i nuovi connettori. A marzo 2019, tutti i connettori esistenti di Exchange Online per Intune verranno disabilitati.

Se si usano questi connettori nel proprio ambiente, non sarà possibile monitorare o cancellare i dispositivi Exchange Active Sync in Intune dopo la disabilitazione dei connettori in marzo. Durante questa modifica non è previsto alcun impatto per gli utenti finali.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>Come prepararsi a questo cambiamento?

Se è stato configurato il connettore da servizio a servizio e l'ambiente include dispositivi Exchange Active Sync, passare ad altri metodi per la gestione dei dispositivi. Sono disponibili le seguenti opzioni:

- Registrare i dispositivi nella gestione dei dispositivi mobili (MDM)
- Usare i criteri di Protezione app di Intune per gestire i dispositivi
- Usare i controlli di Exchange come descritto nella documentazione di seguito. 

#### <a name="additional-information"></a>Informazioni aggiuntive
[Configurare il connettore del servizio Exchange per Intune ed Exchange Online](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>Modifica prevista: aggiornamenti delle prestazioni in Microsoft Intune per Education <!--1750215-->
È in corso l'aggiornamento di Microsoft Intune per Education al fine di incrementare la velocità e l'affidabilità durante l'assegnazione delle impostazioni a utenti o dispositivi. Verso la fine del mese, è anche previsto lo spostamento dei criteri o l'assegnazione delle impostazioni a nuovi gruppi.

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?

Per i clienti di Microsoft Intune per Education saranno disponibili due gruppi di Azure Active Directory (Azure AD) dinamici: "Tutti gli utenti" e "Tutti i dispositivi". In seguito a questi aggiornamenti, i gruppi di Azure AD "Tutti gli utenti" e "Tutti i dispositivi" non saranno visibili nella console di Microsoft Intune per Education. Lo saranno invece in Intune nella console di Azure e verranno rinominati "Tutti gli utenti (obsoleto, non usare)" e "Tutti i dispositivi (obsoleto, non usare)".

Dopo la distribuzione degli aggiornamenti, non sarà più necessario usare i gruppi di Azure AD per assegnare le app e le impostazioni in Intune. Le assegnazioni delle impostazioni verranno invece spostate in nuovi gruppi nella console di Microsoft Intune per Education e verranno creati e visualizzati nuovamente con il nome "Tutti gli utenti" e "Tutti i dispositivi". Queste modifiche vengono eseguite nel back-end. Non si noteranno quindi variazioni nella console di Microsoft Intune per Education. Non è previsto alcun impatto sugli utenti finali o sui dispositivi registrati. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Durante lo spostamento delle assegnazioni dei criteri, non è richiesto l'intervento dell'utente. Se attualmente si assegnano i criteri in Microsoft Intune per Education, si può continuare a farlo.

Se attualmente si assegnano i criteri ai gruppi di Azure AD indicati in precedenza in Intune in Azure, ora è invece necessario assegnarli ai gruppi Tutti gli utenti e Tutti i dispositivi nella console di Microsoft Intune per Education. Quando si nota che i gruppi di Azure AD sono stati rinominati e definiti obsoleti nella console, interrompere l'assegnazione dei criteri in Azure AD. Se attualmente non vi sono motivi per usare i gruppi rinominati, eliminarli.


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>Intervieni: aggiornare le impostazioni delle password per i criteri di limitazione o di conformità dei dispositivi Android in Intune
Intune rimuoverà il tipo di password disponibile "Impostazione predefinita dispositivo" per i dispositivi Android 4.4 e versioni successive. A causa delle differenze tra le piattaforme Android e le impostazioni predefinite dei dispositivi, questo criterio viene spesso considerato facoltativo dal dispositivo. Per evitare confusione per l'applicazione di questa impostazione in Android, questa impostazione verrà rimossa dall'interfaccia utente in una versione futura. 
#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
- Se lo scopo è richiedere una password per i dispositivi, invece di usare "Impostazione predefinita dispositivo" è consigliabile modificare i profili di piattaforma Android per specificare chiaramente il tipo di password richiesto.
- Se lo scopo è consentire all'utente finale di decidere se creare una password, selezionare il pulsante "Non configurato". Quando questa impostazione verrà rimossa dall'interfaccia utente, se è ancora impostata verrà richiesto di scegliere un valore diverso da "Impostazione predefinita dispositivo" in occasione della modifica successiva del profilo.
Operazioni di preparazione alla modifica
Rivedere le impostazioni per le password nei criteri di limitazione e di conformità per i dispositivi aziendali Android. Queste impostazioni sono disponibili in Sicurezza di sistema per Criteri di conformità e in Password per il dispositivo o nelle impostazioni del profilo di lavoro per Limitazioni del dispositivo. Nella sezione Informazioni aggiuntive è disponibile un collegamento ad altre informazioni e screenshot per le posizioni in cui vengono configurate queste impostazioni.
#### <a name="additional-information"></a>Informazioni aggiuntive
https://aka.ms/PasswordSettings 

