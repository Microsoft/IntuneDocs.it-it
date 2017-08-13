---
title: Edizione anticipata
description: 
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 8/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 5861c999752bfef05b8a33161d0bf75a6d4daf59
ms.sourcegitcommit: 18cdbdc226f64368de892a8c5cff157c37986c57
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="the-early-edition-for-microsoft-intune---august-2017"></a>Edizione anticipata per Microsoft Intune - Agosto 2017

L'**edizione anticipata** fornisce un elenco di funzionalità che saranno disponibili nelle prossime versioni di Microsoft Intune. Queste informazioni sono fornite su base limitata e sono soggette a modifiche. Non condividere queste informazioni all'esterno dell'azienda. Alcune funzionalità elencate di seguito potrebbero non essere disponibili entro la data stabilita e potrebbero essere rimandate a una versione futura. Altre funzionalità sono in fase di test in una versione pilota (anteprima) in modo da perfezionarle per l'utente finale. In caso di domande o dubbi, rivolgersi al contatto per il gruppo di prodotti Microsoft.

Questa pagina viene aggiornata periodicamente. Consultarla a intervalli regolari per ulteriori aggiornamenti.

> [!Note]
>Le seguenti modifiche di Intune sono in fase di sviluppo. Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

<!--

## What's coming to Intune on the Azure portal  
## What's coming to Intune apps
## Notices

-->



## <a name="intune-on-the-azure-portal"></a>Intune nel portale di Azure




### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nuova azione del dispositivo per forzare la sincronizzazione con Intune <!-- 711369 -->    
Verrà aggiunta una nuova azione del dispositivo che forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri ad esso assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.

### <a name="actions-for-non-compliance----730266--"></a>Azioni per la non conformità <!--730266-->     
Le *azioni per la mancata conformità* sono una nuova funzionalità dei criteri di conformità che consente di intervenire sui dispositivi non conformi. È possibile specificare una o più azioni e il periodo di tempo in cui devono essere eseguite tali azioni. Ad esempio, è possibile segnalare immediatamente agli utenti i dispositivi non conformi non appena diventano non conformi, tramite posta elettronica, oppure è possibile impedire ai dispositivi non conformi di accedere alle risorse aziendali dopo un periodo di tolleranza di 3 giorni tramite l'accesso condizionale.


### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restrizione della registrazione dei dispositivi Android e iOS in base alla versione del sistema operativo <!--- 1333256,  1245463 --->  
Intune ora supporta la restrizione della registrazione di Android e iOS in base al numero di versione del sistema operativo. In **Intune** > **Restrizioni registrazione** > **Restrizione dei tipi di dispositivo** > **Predefinita** > **Restrizioni della piattaforma** l'amministratore IT può impostare una configurazione della piattaforma per limitare la registrazione tra un valore minimo e massimo del sistema operativo. Le versioni del sistema operativo Android devono essere specificate come Major.Minor.Build.Rev, dove Build e Rev sono facoltative. Le versioni di iOS devono essere specificate come Major.Minor.Build, dove Build è facoltativa.

>[!NOTE]
>Questa impostazione non limita la registrazione tramite i programmi di registrazione di Apple, tra cui il programma di registrazione del dispositivo mobile di Apple e Apple School Manager, o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Limitare la registrazione dei dispositivi personali Android, iOS e macOS <!--- 1333272,  1333275, 1245709 --->
Intune ora supporta la restrizione della registrazione dei dispositivi personali per iOS, Android e macOS tramite i numeri di serie dei dispositivi. Alcuni dispositivi non indicano i numeri di serie. Per i dettagli, contattare i produttori dei dispositivi. Caricando i numeri di serie in Intune, è possibile predichiarare i dispositivi come proprietà dell'azienda. Tramite le restrizioni della registrazione, è possibile bloccare i dispositivi personali (BYOD, Bring Your Own Device), consentendo così la registrazione solo per i dispositivi di proprietà dell'azienda.

Per importare i numeri di serie nel portale di Intune, passare a **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**, fare clic su **Aggiungi** e caricare un file CSV. Il file non deve contenere alcuna intestazione e deve essere composto da due colonne, una per il numero di serie e una per i dettagli come i numeri IMEI.  Per limitare i dispositivi personali, accedere a **Registrazione del dispositivo** > **Restrizioni registrazione**. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinita** e **Configurazioni della piattaforma**. È possibile scegliere **Consenti** o **Blocca** per i dispositivi personali per iOS, Android e macOS. 

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzare i dispositivi iOS supervisionati per installare automaticamente l'aggiornamento software più recente disponibile <!-- 777100 -->   
Un nuovo criterio sarà disponibile dall'area di lavoro degli aggiornamenti software in cui è possibile forzare i dispositivi iOS supervisionati per installare automaticamente l'aggiornamento software più recente disponibile. Sarà anche possibile visualizzare un nuovo report che elenca i dispositivi iOS con le versioni precedenti e un riepilogo dei motivi per cui non sono aggiornate.

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>Nuovo report che elenca i dispositivi iOS con versioni precedenti di iOS <!-- 1352223 -->
Il report **Out-of-date iOS Devices** (Dispositivi iOS non aggiornati) sarà disponibile dall'area di lavoro **Aggiornamenti software**. Nel report è possibile visualizzare un elenco di dispositivi iOS con supervisione a cui è destinato un criterio di aggiornamento di iOS e con aggiornamenti disponibili. Per ogni dispositivo, è possibile visualizzare lo stato del motivo per cui il dispositivo non è stato aggiornato automaticamente. 

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices-----822899--1305423--"></a>Nuove impostazioni per consentire e bloccare le app nei dispositivi Samsung KNOX Standard <!-- 822899,  1305423-->   
Vengono aggiunte nuove [impostazioni di restrizione dei dispositivi](device-restrictions-android.md) che consentono di specificare gli elenchi di app seguenti:
  - App che gli utenti sono autorizzati a installare
  - App che gli utenti non possono eseguire
  - App che sono nascoste all'utente nel dispositivo  

È possibile specificare l'app in base all'URL, al nome del pacchetto o dall'elenco di app che si gestiscono.

### <a name="new-settings-for-windows-10-device-restriction-profile"></a>Nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10
<!--- 978575, 1308849, 1308850 -->
Sono state aggiunte nuove impostazioni per il profilo di restrizione dei dispositivi Windows 10 nella categoria Windows Defender SmartScreen.

Per informazioni dettagliate sul profilo di restrizione dei dispositivi Windows 10, vedere [Windows 10 and later device restriction settings]( device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).

### <a name="new-device-restriction-settings-for-windows-10------1063965---"></a>Nuove impostazioni relative alle restrizioni dei dispositivi per Windows 10 <!-- 1063965 -->
Sono state aggiunte nuove impostazioni per il [profilo di restrizione dei dispositivi Windows 10](/intune/device-restrictions-windows-10) nelle categorie seguenti:
- Windows Defender SmartScreen
- App Store


### <a name="android-for-work-support-for-lookout----1087312---"></a>Supporto di Android for Work per Lookout <!-- 1087312 -->   
Il connettore di Intune con Lookout supporterà i dispositivi Android for Work quando si usa l'app Lookout for Work. È possibile distribuire l'app Lookout all'interno o all'esterno del contenitore.


### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Protezione app di Intune e strumenti di sviluppo MDX Citrix <!-- 709185 -->
È possibile gestire i dispositivi e le app usando in combinazione Citrix XenMobile MDX e Microsoft Intune. Ciò consente di gestire le app con i criteri di protezione delle app di Intune usando allo stesso tempo la tecnologia mVPN di Citrix.

È disponibile un repository di codice che contiene lo strumento di wrapping delle app di Intune e Intune App SDK per iOS e Android, per l'integrazione con la tecnologia mVPN MDX di Citrix.


### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium: nuovo partner di Mobile Threat Defense  <!-- 954681 -->
È ora possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Zimperium, una soluzione di Mobile Threat Defense integrata in Microsoft Intune.

#### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Zimperium. È possibile configurare criteri di accesso condizionale EMS in base alla valutazione dei rischi di Zimperium abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

### <a name="new-azure-ad-conditional-access-policy-ui-link-from-intune-----1016201---"></a>Nuovo collegamento all'interfaccia utente per i criteri di accesso condizionale di Azure AD da Intune<!-- 1016201 -->
Gli amministratori IT possono impostare criteri condizionali basati su app tramite la nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Azure AD. I criteri di accesso condizionale basati su app disponibili nella sezione Protezione app di Intune in Azure rimangono in tale posizione per il momento e vengono applicati in affiancamento. Sarà disponibile un altro collegamento per comodità alla nuova interfaccia utente per i criteri di accesso condizionale in Azure AD dal carico di lavoro Intune.


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>Supporto a disponibilità elevata di Exchange Connector locale<!-- 676614 -->   
È possibile avere più ruoli server Accesso client per Exchange Connector locale. Ad esempio, se il server Accesso client principale smette di funzionare, Exchange Connector riceve una query per eseguire il fallback in altri server Accesso client. Questa funzionalità garantisce che il servizio non venga interrotto.

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Management Pack di System Center Operations Manager per Exchange Connector <!-- 885457 -->   
Sarà disponibile il Management Pack di System Center Operations Manager per Exchange Connector per agevolare l'analisi dei log di Exchange Connector. Questo Management Pack consente di eseguire il monitoraggio di Intune in diversi modi quando è necessario risolvere i problemi.

### <a name="conditional-access-support-for-mac-devices-----720172---"></a>Supporto dell'accesso condizionale per dispositivi Mac <!-- 720172 -->   
Sarà presto possibile impostare un criterio di accesso condizionale che richieda che i dispositivi Mac vengano registrati in Intune e siano conformi ai relativi criteri di conformità dei dispositivi. Ad esempio, gli utenti possono scaricare l'app Portale aziendale Intune per macOS e registrare i propri dispositivi Mac in Intune. Intune valuta se il dispositivo Mac è conforme a requisiti come PIN, crittografia, versione del sistema operativo e integrità del sistema.

### <a name="end-of-support-for-ios-80----1164477---"></a>Fine del supporto per iOS 8.0 <!---1164477--->
Le app gestite e l'app Portale aziendale per iOS richiederanno iOS 9.0 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati entro settembre non potranno accedere al Portale aziendale o a tali app. A dicembre, l'accesso alle risorse aziendali, inclusa la posta elettronica, verrà bloccato. 

### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fine del supporto per Android 4.3 e versioni precedenti <!---1171127, 1326920 --->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati prima dell'inizio del mese di ottobre non potranno accedere al Portale aziendale o a tali app. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-will-end-july-11-2017----1327781---"></a>Promemoria di supporto della piattaforma: il supporto Mainstream di Windows Phone 8.1 termina l'11 luglio 2017 <!-- 1327781 -->  
L'11 luglio 2017, termina il supporto Mainstream per la piattaforma di Windows Phone 8.1. Il supporto per PC Windows 8.1 viene mantenuto.

Ciò non ha alcun impatto immediato sui dispositivi Windows Phone 8.1 gestiti dal servizio di Intune. I dispositivi registrati continuano a funzionare regolarmente e tutti i criteri, le configurazioni e le app continuano a funzionare come previsto. Si noti che non sono previsti miglioramenti destinati alla piattaforma Windows Phone 8.1 nel servizio di Intune e all'app Portale aziendale di Windows Phone 8.1.

È consigliabile aggiornare a Windows 10 Mobile i dispositivi Windows Phone 8.1 idonei, appena possibile. 




## <a name="intune-apps"></a>App di Intune

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modalità chiara e modalità scura disponibili per l'app Portale aziendale per Windows 10 <!---676547--->
Gli utenti finali potranno personalizzare la modalità di colore per l'app Portale aziendale per Windows 10. L'utente potrà apportare la modifica nella sezione delle impostazioni dell'app Portale aziendale. La modifica verrà visualizzata dopo che l'utente avrà riavviato l'app. Per Windows 10 versione 1607 e successive, la modalità dell'app predefinita corrisponde all'impostazione di sistema. Per i computer desktop che eseguono Windows 10 versione 1511 e versioni precedenti, la modalità dell'app predefinita sarà la modalità chiara.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Consentire agli utenti di accedere all'app Portale aziendale per Android senza registrazione <!---1169910--->  
Gli utenti finali potranno presto non avere l'obbligo di registrare il dispositivo per accedere all'app Portale aziendale per Android. Agli utenti finali di organizzazioni che usano criteri di protezione delle app non verrà più richiesto di registrare il dispositivo quando aprono l'app Portale aziendale. Gli utenti finali potranno anche installare app dal Portale aziendale senza registrare il dispositivo. 

### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>Messaggio di errore migliorato quando un utente raggiunge il numero massimo di dispositivi di cui è consentita la registrazione <!-- 1270370 -->
Invece di un messaggio di errore generico, gli utenti finali vedranno un messaggio di errore descrittivo e interattivo: "You have enrolled the maximum number of devices allowed by your IT admin. Please remove an enrolled device or get help from your IT admin." (È stato raggiunto il numero massimo di dispositivi consentiti dall'amministratore IT. Rimuovere un dispositivo registrato o richiedere assistenza all'amministratore IT.)

### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nuova esperienza di accesso per gli utenti dell'app Portale aziendale per Android e gli utenti dei criteri di protezione delle app <!-- 621669 -->
Gli utenti finali potranno accedere alle app, gestire i dispositivi e visualizzare le informazioni di contatto IT tramite l'app Portale aziendale per Android senza registrare i dispositivi Android. Inoltre, se un utente finale usa già un'app protetta dai criteri di Protezione app di Intune e avvia l'app Portale aziendale per Android, l'utente finale non riceverà più la richiesta di registrare il dispositivo. 

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate per iOS<!--739894-->
Verrà aggiunta l'opzione **Ownership Type** (Tipo di proprietà) nella schermata Dettagli dispositivo nell'app Portale aziendale per iOS. In questo modo gli utenti possono ottenere ulteriori informazioni sulla privacy direttamente da questa pagina dalla documentazione finale di Intune. Potranno accedere a queste informazioni anche nella schermata Informazioni su.

### <a name="apps-details-pages-display-new-information-for-android-devices---1287476--"></a>Le pagine dei dettagli delle app visualizzano nuove informazioni per i dispositivi Android <!--1287476-->
La pagina dei dettagli dell'app nell'app Portale aziendale per Android visualizzerà le categorie di app definite dall'amministratore IT per l'app.

### <a name="intune-mobile-application-management-mam-dialog-boxes-now-have-a-modern-interface----1199015---"></a>Le finestre di dialogo per la gestione delle applicazioni mobili di Intune hanno ora un'interfaccia moderna <!-- 1199015 -->
Le finestre di dialogo per la gestione delle applicazioni mobili di Intune sono state aggiornate per lo stile moderno. Le finestre di dialogo funzionano nello stesso modo dello stile precedente.

Nei dispositivi Android moderni, le finestre di dialogo di errore o di notifica visualizzate da Intune avranno ora il nuovo aspetto aggiornato.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nuova impostazione nell'app Portale aziendale per Android per attivare/disattivare l'ottimizzazione della memoria <!--1405990-->
La pagina **Impostazioni** nell'app Portale aziendale per Android includerà una nuova impostazione che consente agli utenti di disattivare facilmente l'ottimizzazione della batteria per le app Portale aziendale e Microsoft Authenticator. Il nome dell'app visualizzato nell'impostazione varia a seconda dell'app usata per gestire l'account aziendale. È consigliabile che gli utenti disattivino l'ottimizzazione della batteria per migliorare le prestazioni delle app aziendali che sincronizzano posta elettronica e dati. 




## <a name="notices"></a>Notifiche

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->   
A partire dalla primavera 2017, Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->   
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di anteprima di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="plan-for-change-intune-is-changing-the-intune-partner-portal-experience----1050016---"></a>Modifiche pianificate: Intune ha intenzione di modificare l'esperienza del portale per i partner di Intune <!-- 1050016 -->
A partire dall'aggiornamento del servizio previsto per la metà di maggio 2017, la pagina Intune Partner verrà rimossa dal sito manage.microsoft.com.  

Gli amministratori di partner non saranno più in grado di visualizzare e agire per conto dei clienti dalla pagina Intune Partner, ma dovranno invece effettuare l'accesso a uno degli altri due altri portali Microsoft per i partner.

Il [Centro per i partner Microsoft](https://partnercenter.microsoft.com/) e l'[interfaccia di amministrazione partner di Office 365](https://portal.office.com/) consentiranno entrambi di accedere agli account cliente gestiti. Procedendo come partner, usare uno di questi siti per gestire i clienti.



### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new.md).
