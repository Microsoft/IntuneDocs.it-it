---
title: "Novità dei mesi precedenti per Microsoft Intune"
titleSuffix: Intune on Azure
description: "Rileggere gli annunci precedenti dalla pagina delle novità di Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 8/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 98b4d1dd438b352164c697af5f1531a0d79538ad
ms.sourcegitcommit: 4dc5bed94cc965a54eacac2d87fb2d49c9300c3a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2017
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Novità di Microsoft Intune - mesi precedenti

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="july-2017"></a>Luglio 2017

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restrizione della registrazione dei dispositivi Android e iOS in base alla versione del sistema operativo <!--- 1333256,  1245463 --->
Intune ora supporta la restrizione della registrazione di Android e iOS in base al numero di versione del sistema operativo. In **Restrizione dei tipi di dispositivo** l'amministratore IT può ora impostare una configurazione della piattaforma per limitare la registrazione tra un valore minimo e massimo del sistema operativo. Le versioni del sistema operativo Android devono essere specificate come Principale.Secondaria.Build.Rev, dove Secondaria, Build e Rev sono facoltativi. Le versioni di iOS devono essere specificate come Principale.Secondaria.Build, dove Build è facoltativa. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

>[!NOTE]
>Non limitare la registrazione tramite i programmi DEP Apple o Apple Configurator.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Limitare la registrazione dei dispositivi personali Android, iOS e macOS <!--- 1333272,  1333275, 1245709 --->
Intune può limitare la registrazione dei dispositivi personali creando un elenco dei dispositivi aziendali consentiti con i relativi numeri IMEI. Intune ha ora esteso questa funzionalità a iOS, Android e macOS usando i numeri di serie del dispositivo. Caricando i numeri di serie in Intune, è possibile predichiarare i dispositivi come proprietà dell'azienda. Tramite le restrizioni della registrazione, è possibile bloccare i dispositivi personali (BYOD, Bring Your Own Device), consentendo così la registrazione solo per i dispositivi di proprietà dell'azienda. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

Per importare i numeri di serie, passare a **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**, fare clic su **Aggiungi** e quindi caricare un file con estensione csv senza intestazione ma con due colonne per il numero di serie e i dettagli come i numeri IMEI.  Per limitare i dispositivi personali, accedere a **Registrazione del dispositivo** > **Restrizioni registrazione**. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinita** e **Configurazioni della piattaforma**. È possibile scegliere **Consenti** o **Blocca** per i dispositivi personali per iOS, Android e macOS. 


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nuova azione del dispositivo per forzare la sincronizzazione con Intune <!-- 711369 -->
In questa versione è stata aggiunta una nuova azione del dispositivo che forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.
Per informazioni dettagliate, vedere [Sincronizzare il dispositivo](device-sync.md).

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzare i dispositivi iOS supervisionati per installare automaticamente l'aggiornamento software più recente disponibile <!-- 777100 -->
È disponibile un nuovo criterio dall'area di lavoro degli aggiornamenti software, che consente di forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione. Per informazioni dettagliate, vedere [Configurare i criteri di aggiornamento per iOS](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile: nuovo partner di Mobile Threat Defense  <!-- 954651, 1172027 -->
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


### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Dettagli aggiuntivi per la risoluzione dei problemi dell'help desk <!---  Applies to 1263399, 1326964, 1341642 --->
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
In una versione successiva si prevede di aggiungere un metodo più semplice per la selezione e l'assegnazione delle app predefinite dal portale di Intune.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Installazione più semplice delle app di Office 365 <!--- 1121362 --->
Un nuovo tipo di applicazioni **Office 365 ProPlus** semplifica l'assegnazione delle app Office 365 ProPlus 2016 ai dispositivi gestiti che eseguono la versione più recente di Windows 10. È anche possibile installare Microsoft Project e Microsoft Visio, se si hanno le relative licenze. Le app desiderate vengono unite in bundle e visualizzate come un'unica app nell'elenco di app della console di Intune.
Per altre informazioni, vedere [How to add Office 365 apps for Windows 10](apps-add-office365.md) (Come aggiungere app di Office 365 per Windows 10).


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>Supporto per le app offline da Microsoft Store per le aziende <!--- 777044 --->
Le app offline acquistate da Microsoft Store per le aziende verranno ora sincronizzate nel portale di Intune. È possibile quindi distribuire tali app a gruppi di dispositivi o di utenti. Le app offline vengono installate da Intune, non dallo Store.

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
-  Browser Edge

Per altre informazioni sulle impostazioni di Windows 10, vedere [Windows 10 and later device restriction settings](device-restrictions-windows-10.md) (Impostazioni di restrizione del dispositivo Windows 10 e versioni successive).


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>L'app Portale aziendale per Android ora include una nuova esperienza utente finale per i criteri di protezione delle app <!--1305217-->
In base ai suggerimenti dei clienti, l'app Portale aziendale per Android è stata modificata e ora include un pulsante **Accesso al contenuto aziendale**. Con questa funzionalità gli utenti finali possono evitare il processo di registrazione per accedere solo ad app che supportano i criteri di protezione, una funzionalità di gestione delle applicazioni mobili di Intune. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nuova azione di menu per rimuovere facilmente Portale aziendale <!--1164569-->
In risposta al feedback degli utenti, per l'app Portale aziendale per Android è stata aggiunta una nuova azione di menu per eseguire la rimozione di Portale aziendale dal dispositivo. Questa azione rimuove il dispositivo dalla gestione di Intune in modo che l'app possa essere rimossa dal dispositivo dall'utente. È possibile visualizzare queste modifiche nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md) e nella [documentazione per gli utenti finali di Android](/intune-user-help/unenroll-your-device-from-intune-android).

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Miglioramenti alla sincronizzazione di app con Windows 10 Creators Update <!--676505-->
L'app Portale aziendale per Windows 10 avvierà ora automaticamente una sincronizzazione per le richieste di installazione di app per dispositivi con Windows 10 Creators Update (1703). Ciò consente di limitare il problema di installazione di app quando lo stato è "In attesa di sincronizzazione". Gli utenti potranno inoltre avviare manualmente la sincronizzazione dall'app. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nuova esperienza guidata per il portale aziendale di Windows 10 <!---1058938--->
L'app Portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate che guidano l'utente nella procedura di registrazione in Azure Active Directory (obbligatoria per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale. Gli utenti possono continuare a usare l'app anche se non completano la registrazione, ma avranno a disposizione funzionalità limitate.

Questo aggiornamento è visibile solo nei dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 (build 1607) o versioni successive. È possibile visualizzare queste modifiche nella pagina [What's new in app UI](whats-new-app-ui.md) (Novità nell'interfaccia utente dell'app).


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Disponibilità generale delle console di amministrazione di Microsoft Intune e dell'accesso condizionale
Questo è l'annuncio della disponibilità generale sia della nuova console di amministrazione di Intune in Azure che della nuova console di amministrazione dell'accesso condizionale. Tramite Intune in Azure è ora possibile gestire tutte le funzionalità MAM e MDM di Intune con un'esperienza di amministrazione consolidata, sfruttando allo stesso tempo le funzioni di raggruppamento e targeting di Azure AD. L'accesso condizionale in Azure offre funzionalità avanzate per Azure AD e Intune in un'unica console unificata. Per quanto riguarda l'esperienza di amministrazione, inoltre, il passaggio alla piattaforma Azure consente di usare browser moderni.

Intune è ora visibile senza l'etichetta di **anteprima** nella console di Azure all'indirizzo portal.azure.com.

Al momento non è richiesto alcun intervento da parte dei clienti esistenti, a meno che non si riceva uno di una serie di messaggi nel centro messaggi che richiede di intervenire in modo da consentire a Microsoft di eseguire la migrazione dei gruppi. È anche possibile che si riceva una notifica nel centro messaggi che informa che la migrazione richiede più tempo a causa di errori di Microsoft. Stiamo continuando a lavorare con impegno per completare la migrazione di tutti i clienti interessati.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Miglioramenti dei riquadri dell'app Portale aziendale per iOS
È stata aggiornata la progettazione dei riquadri dell'app nella home page in modo che rispecchino il colore personalizzato impostato per Portale aziendale. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Selezione account ora disponibile per l'app Portale aziendale per iOS
Gli utenti di dispositivi iOS potrebbero ora visualizzare la nuova selezione account quando accedono al Portale aziendale se usano l'account aziendale o dell'istituto di istruzione per accedere ad altre app Microsoft. Per altre informazioni, vedere [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

## <a name="may-2017"></a>Maggio 2017

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>Modifica dell'autorità MDM senza annullare la registrazione dei dispositivi gestiti <!--1103950-->
È ora possibile modificare l'autorità MDM senza dover contattare il supporto Microsoft e senza che sia necessario annullare la registrazione dei dispositivi gestiti esistenti e quindi eseguirla di nuovo. Nella console di Configuration Manager è possibile [modificare l'autorità MDM](/sccm/mdm/deploy-use/change-mdm-authority) da Imposta su Configuration Manager (ibrida) a Microsoft Intune (autonoma) o viceversa.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Notifica migliorata per i PIN di avvio Samsung KNOX <!--1087143-->
Quando gli utenti finali devono impostare un PIN di avvio su dispositivi Samsung KNOX per garantire la conformità alla crittografia, toccando la notifica visualizzata, gli utenti finali verranno indirizzati alla posizione esatta nell'app Impostazioni.  In precedenza, la notifica rimandava gli utenti finali alla schermata di modifica della password.

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
Alcune app Android dallo store supportano opzioni di configurazione gestite che consentono a un amministratore IT di controllare l'esecuzione di un'app nel profilo di lavoro. Con Intune è ora possibile visualizzare le configurazioni supportate da un'app e configurarle dal portale di Intune con una finestra di progettazione della configurazione o un editor JSON. Per altre informazioni, vedere [Usare configurazioni di app per Android for Work](app-configuration-policies-use-android.md).

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
Per la creazione di un profilo di certificato SCEP, l'opzione **Personalizzato** per **Formato nome soggetto** è disponibile per i dispositivi iOS, Android e Windows. Prima dell'aggiornamento, il campo **Personalizzato** era disponibile solo per i dispositivi iOS. Per altre informazioni, vedere [Come creare un profilo certificato SCEP] (certificates-scep-configure.md#how-to-create-a-scep-certificate-profile).

Per la creazione di un profilo di certificato PKCS, è disponibile l'opzione **Custom Azure AD attribute** (Attributo Azure AD personalizzato) per **Nome alternativo soggetto**. È disponibile l'opzione **Reparto** quando si seleziona **Custom Azure AD attribute** (Attributo Azure AD personalizzato). Per altre informazioni, vedere [Come creare un profilo certificato PKCS] (certficates-pfx-configure.md#how-to-create-a-pkcs-certificate-profile).

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

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Gestione di più utenti per i dispositivi Samsung KNOX Standard <!-- 971988 -->
I dispositivi che eseguono Samsung KNOX Standard sono ora supportati per la [gestione multiutente](android-enroll.md) in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure Active Directory e il dispositivo è gestito centralmente indipendentemente dal fatto che sia o meno in uso.  Dopo aver eseguito l'accesso gli utenti finali possono accedere alle app e implementare i criteri loro assegnati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

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
È ora possibile aggiungere un numero elevato di dispositivi che eseguono Windows 10 Creators Update ad Azure Active Directory e Intune con Windows Configuration Designer (WCD). Per abilitare la [registrazione MDM in blocco](windows-bulk-enroll.md) del tenant di Azure AD, creare un pacchetto di provisioning che aggiunga i dispositivi al tenant di Azure AD usando Windows Configuration Designer e applicare il pacchetto ai dispositivi di proprietà dell'azienda che si vuole registrare e gestire in blocco. Dopo aver applicato il pacchetto, i dispositivi verranno aggiunti ad Azure AD, registrati in Intune e saranno pronti per l'accesso da parte degli utenti di Azure AD.  Gli utenti di Azure AD sono utenti standard di questi dispositivi e ricevono i criteri assegnati e le app necessarie. Al momento gli scenari di tipo self-service o portale aziendale non sono supportati.

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
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiederanno una migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere all'anteprima, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.


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
