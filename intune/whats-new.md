---
title: "Novità di Microsoft Intune"
titleSuffix: Intune on Azure
description: "Informazioni sulle novità nel portale di Intune di Azure"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 08/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f28ce989b5907f7e7474543c364508424dc0c9cf
ms.sourcegitcommit: 0b164f806165d312acfc88815a60e325e3d02672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre a indicazioni sulle [modifiche previste](#whats-coming), [notifiche importanti](#notices) sul servizio e informazioni sulle [versioni precedenti](whats-new-archive.md).

> [!Note]
> Molte di queste funzionalità saranno supportate per le distribuzioni ibride con Configuration Manager. Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Role-based access control
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Intune apps
-->   


## <a name="week-of-august-21-2017"></a>Settimana del 21 agosto 2017
### <a name="app-management"></a>Gestione delle app
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nuova esperienza di accesso per gli utenti dell'app Portale aziendale per Android e gli utenti dei criteri di protezione delle app <!-- 621669 -->

Gli utenti finali possono ora esplorare le app, gestire i dispositivi e visualizzare le informazioni sul contatto IT tramite l'app Portale aziendale per Android senza registrare i dispositivi Android. Inoltre, se un utente finale usa già un'app protetta tramite i criteri di protezione app di Intune e avvia l'app Portale aziendale per Android, l'utente finale non riceve più la richiesta di registrare il dispositivo.

## <a name="week-of-july-31-2017"></a>Settimana del 31 luglio 2017
### <a name="device-enrollment"></a>Registrazione del dispositivo  

#### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version------1333256--1245463----"></a>Restrizione della registrazione dei dispositivi Android e iOS in base alla versione del sistema operativo <!--- 1333256,  1245463 --->
Intune ora supporta la restrizione della registrazione di Android e iOS in base al numero di versione del sistema operativo. In **Restrizione dei tipi di dispositivo** l'amministratore IT può ora impostare una configurazione della piattaforma per limitare la registrazione tra un valore minimo e massimo del sistema operativo. Le versioni del sistema operativo Android devono essere specificate come Principale.Secondaria.Build.Rev, dove Secondaria, Build e Rev sono facoltativi. Le versioni di iOS devono essere specificate come Principale.Secondaria.Build, dove Build è facoltativa. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

>[!NOTE]
>Non limitare la registrazione tramite i programmi DEP Apple o Apple Configurator.

#### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment------1333272--1333275-1245709----"></a>Limitare la registrazione dei dispositivi personali Android, iOS e macOS <!--- 1333272,  1333275, 1245709 --->
Intune può limitare la registrazione dei dispositivi personali creando un elenco dei dispositivi aziendali consentiti con i relativi numeri IMEI. Intune ha ora esteso questa funzionalità a iOS, Android e macOS usando i numeri di serie del dispositivo. Caricando i numeri di serie in Intune, è possibile predichiarare i dispositivi come proprietà dell'azienda. Tramite le restrizioni della registrazione, è possibile bloccare i dispositivi personali (BYOD, Bring Your Own Device), consentendo così la registrazione solo per i dispositivi di proprietà dell'azienda. Altre informazioni sulle [restrizioni per la registrazione dei dispositivi](enrollment-restrictions-set.md).

Per importare i numeri di serie, passare a **Registrazione del dispositivo** > **Identificatori dei dispositivi aziendali**, fare clic su **Aggiungi** e quindi caricare un file con estensione csv senza intestazione ma con due colonne per il numero di serie e i dettagli come i numeri IMEI.  Per limitare i dispositivi personali, accedere a **Registrazione del dispositivo** > **Restrizioni registrazione**. In **Restrizioni sul tipo di dispositivi** selezionare **Predefinita** e **Configurazioni della piattaforma**. È possibile scegliere **Consenti** o **Blocca** per i dispositivi personali per iOS, Android e macOS. 


### <a name="device-management"></a>Gestione dei dispositivi   

#### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>Nuova azione del dispositivo per forzare la sincronizzazione con Intune <!-- 711369 -->
In questa versione è stata aggiunta una nuova azione del dispositivo che forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri ad esso assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.
Per informazioni dettagliate, vedere [Sincronizzare il dispositivo](device-sync.md).

#### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>Forzare i dispositivi iOS supervisionati per installare automaticamente l'aggiornamento software più recente disponibile <!-- 777100 -->
È disponibile un nuovo criterio dall'area di lavoro degli aggiornamenti software, che consente di forzare l'installazione automatica dell'aggiornamento software più recente disponibile nei dispositivi iOS con supervisione. Per informazioni dettagliate, vedere [Configurare i criteri di aggiornamento per iOS](/intune/software-updates-ios)

#### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner-----954651-1172027---"></a>Check Point SandBlast Mobile: nuovo partner di Mobile Threat Defense  <!-- 954651, 1172027 -->
È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Checkpoint SandBlast Mobile, una soluzione di Mobile Threat Defense integrata in Microsoft Intune.

##### <a name="how-integration-with-intune-works"></a>Funzionamento dell'integrazione con Intune
La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono Checkpoint SandBlast Mobile. È possibile configurare criteri di accesso condizionale EMS basati sulla valutazione dei rischi di Checkpoint SandBlast Mobile e abilitati tramite i criteri di conformità dei dispositivi di Intune. È possibile consentire o bloccare l'accesso alle risorse aziendali ai dispositivi non conformi in base alle minacce rilevate.


### <a name="app-management"></a>Gestione delle app

#### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>Distribuire un'app come disponibile in Microsoft Store per le aziende <!-- 748101 -->
Con questa versione, gli amministratori possono ora assegnare Microsoft Store per le aziende come disponibile. Con questa impostazione, gli utenti finali possono installare l'app dall'app Portale aziendale o dal sito Web del portale aziendale senza essere reindirizzati a Microsoft Store.


### <a name="intune-apps"></a>App di Intune  

#### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>Aggiornamenti dell'interfaccia utente del sito Web del portale aziendale <!--1313244 part 1-->
Sono stati introdotti vari aggiornamento all'interfaccia utente del [sito Web portale aziendale](https://portal.manage.microsoft.com) per migliorare l'esperienza per gli utenti finali.

- __Miglioramenti per i riquadri delle app__: le icone delle app verranno ora visualizzate con uno sfondo generato automaticamente in base al colore dominante dell'icona, se rilevabile. Se applicabile, questo sfondo sostituisce il bordo grigio precedentemente visibile nei riquadri delle app.

    In una versione futura è previsto che il sito Web del portale aziendale visualizzi le icone grandi ogniqualvolta possibile. È consigliabile che gli amministratori IT pubblichino app con icone ad alta risoluzione di dimensioni minime pari a 120x120 pixel. 

- __Modifiche alla struttura di spostamento__: gli elementi della barra di spostamento sono stati spostati nel menu hamburger in alto a sinistra. La pagina delle categorie è stata rimossa. Gli utenti possono ora filtrare il contenuto in base alla categoria durante l'esplorazione.

- __Aggiornamenti per le app in primo piano__: è stata aggiunta una pagina dedicata nel sito, nella quale gli utenti possono visualizzare le app che hanno scelto di mettere in primo piano e sono state apportate alcune modifiche all'interfaccia utente della sezione In primo piano nella home page.

#### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>Supporto di iBooks per il sito Web del portale aziendale <!--1231841-->
È stata aggiunta una pagina dedicata al sito Web del portale aziendale che consente agli utenti di visualizzare e scaricare iBooks. 

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="additional-help-desk-troubleshooting-details------applies-to-1263399-1326964-1341642----"></a>Dettagli aggiuntivi per la risoluzione dei problemi dell'help desk <!---  Applies to 1263399, 1326964, 1341642 --->
 
Intune ha aggiornato la visualizzazione della risoluzione dei problemi e aggiunto le informazioni che fornisce agli amministratori e al personale dell'help desk. È ora disponibile una tabella **Assegnazioni** che fornisce un riepilogo di tutte le assegnazioni dell'utente in base all'appartenenza a gruppi. L'elenco include:
- App per dispositivi mobili
- Criteri di conformità
- Profili di configurazione
 
Inoltre, la tabella **Dispositivi** ora include le colonne **Tipo di join per Azure AD** e **Conforme con Azure AD**. Per altre informazioni, vedere [Aiutare gli utenti nella risoluzione dei problemi](help-desk-operators.md).

### <a name="reporting"></a>Reporting

#### <a name="intune-data-warehouse-public-preview"></a>Data warehouse di Intune (anteprima pubblica)

Il data warehouse di Intune esegue il campionamento giornaliero dei dati per fornire una visualizzazione cronologica dell'ambiente. È possibile accedere ai dati tramite un file di Power BI (PBIX), un collegamento OData compatibile con molti strumenti di analisi oppure interagendo con l'API REST. Per altre informazioni, vedere [Usare il data warehouse di Intune](reports-nav-create-intune-reports.md).

## <a name="week-of-july-23rd-2017"></a>Settimana del 23 luglio 2017

### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Modalità chiara e modalità scura disponibili per l'app Portale aziendale per Windows 10 <!---676547--->
Gli utenti finali potranno personalizzare la modalità di colore per l'app Portale aziendale per Windows 10. L'utente potrà apportare la modifica nella sezione delle impostazioni dell'app Portale aziendale. La modifica verrà visualizzata dopo che l'utente avrà riavviato l'app. Per Windows 10 versione 1607 e successive, la modalità dell'app predefinita sarà l'impostazione di sistema. Per Windows 10 versione 1511 e precedenti, la modalità dell'app predefinita sarà la modalità chiara.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>Consentire agli utenti finali di contrassegnare il gruppo di dispositivi nell'app Portale aziendale per Windows 10 <!---807046-->
Gli utenti finali possono ora selezionare il gruppo a cui appartiene il dispositivo contrassegnandolo direttamente dall'app Portale aziendale per Windows 10.




## <a name="notices"></a>Notifiche

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Aggiornamento degli indirizzi IP per Intune <!-- 1175274 -->
È disponibile un [elenco aggiornato di nomi DNS e indirizzi IP](/intune/network-bandwidth-use) per le impostazioni proxy del firewall.

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Usare Azure Active Directory per l'accesso condizionale <!-- 967947 -->
L'accesso condizionale è disponibile nella sezione di Azure Active Directory della console di Azure e fornisce un framework più potente e flessibile per l'impostazione di criteri per le app cloud come Office 365 Exchange Online e SharePoint Online.  Usare il pannello **Accesso condizionale in Azure Active Directory** per configurare i criteri invece della console di Intune classica. I criteri esistenti nella console di Intune classica devono essere ricreati nella console di Azure. Per altre informazioni, vedere [Creare criteri di accesso condizionale di Azure AD](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima di registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiedono un'unica migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere al portale di Azure, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Ruoli di amministrazione in corso di sostituzione nel portale di Azure
I ruoli di amministrazione di gestione delle applicazioni per dispositivi mobili (MAM) esistenti (Collaboratore, Proprietario e Sola lettura) usati nel portale classico di Intune (Silverlight) verranno sostituiti con un set completo di nuovi controlli di amministrazione in base al ruolo nel portale di Intune di Azure. Dopo aver completato la migrazione al portale di Azure, sarà necessario riassegnare gli amministratori a questi nuovi ruoli di amministrazione. Per altre informazioni sul controllo degli accessi in base al ruolo e i nuovi ruoli, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo) per Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Sviluppi futuri

### <a name="end-of-support-for-ios-80----1164477---"></a>Fine del supporto per iOS 8.0 <!---1164477--->
Le app gestite e l'app Portale aziendale per iOS richiederanno iOS 9.0 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati entro settembre non potranno accedere al Portale aziendale o a tali app. 

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Aggiornamenti dell'interfaccia utente del sito Web del portale aziendale <!--1313244 part 2-->
__Aggiornamenti per le app in primo piano__  
È stata aggiunta una pagina dedicata nel sito, nella quale gli utenti possono visualizzare le app che hanno scelto di mettere in primo piano e sono state apportate alcune modifiche all'interfaccia utente della sezione In primo piano nella home page. È possibile visualizzare queste modifiche nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).


### <a name="end-of-support-for-android-43-and-lower----1171127-1326920----"></a>Fine del supporto per Android 4.3 e versioni precedenti <!---1171127, 1326920 --->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati prima dell'inizio del mese di ottobre non potranno accedere al Portale aziendale o a tali app. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.


### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Promemoria di supporto di piattaforma: il supporto Mainstream di Windows Phone 8.1 è terminato l'11 luglio 2017
<!-- 1327781 -->
La piattaforma Windows Phone 8.1 ha raggiunto la fine del supporto Mainstream l'11 luglio 2017. Il supporto per PC Windows 8.1 viene mantenuto.

Ciò non ha alcun impatto immediato sui dispositivi Windows Phone 8.1 gestiti dal servizio di Intune. I dispositivi registrati continuano a funzionare regolarmente e tutti i criteri, le configurazioni e le app continuano a funzionare come previsto. Si noti che non sono previsti miglioramenti destinati alla piattaforma Windows Phone 8.1 nel servizio di Intune e all'app Portale aziendale di Windows Phone 8.1.

È consigliabile aggiornare a Windows 10 Mobile i dispositivi Windows Phone 8.1 idonei, appena possibile. 

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Modifiche nel supporto per l'app Portale aziendale per iOS di Intune  <!-- 1164474  -->
Presto verrà resa disponibile una nuova versione dell'app Portale aziendale di Microsoft Intune per iOS che supporterà solo i dispositivi che eseguono iOS 9.0 o versioni successive. La versione del portale aziendale che supporta iOS 8 sarà comunque disponibile per un breve periodo di tempo. Tuttavia, tenere presente che se vengono usate le app iOS abilitate per MAM, il sistema iOS 9.0 e le versioni successive sono supportate, quindi è opportuno assicurarsi che gli utenti finali eseguano l'aggiornamento al sistema operativo più recente. 

#### <a name="how-does-this-affect-me"></a>Quali sono le conseguenze di questa modifica?
Ciò verrà comunicato in anticipo. Sebbene non sia stata ancora definita una data specifica, c'è tuttavia tempo per pianificare l'aggiornamento. Assicurarsi che gli utenti abbiano eseguito l'aggiornamento a iOS 9+ e che eseguano l'aggiornamento all'app Portale aziendale quando viene rilasciata.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Operazioni di preparazione alla modifica
Richiedere agli utenti di eseguire l'aggiornamento a iOS 9.0 o versioni successive per poter usare al meglio le nuove funzionalità di Intune.  Richiedere agli utenti di installare la nuova versione del portale aziendale e usufruire delle nuove funzionalità.

Passare a Intune nel portale di Azure, visualizzare Dispositivi > Tutti i dispositivi e filtrare l'elenco con la versione di iOS per visualizzare eventuali dispositivi correnti con i sistemi operativi precedenti a iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->
Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS.

Microsoft ha reso disponibile una versione dell'app Portale aziendale per iOS tramite il programma Apple TestFlight che applica i nuovi requisiti ATS. Se si desidera provarla in modo da poterne verificare la conformità con ATS, inviare un messaggio di indirizzo elettronica all'indirizzo <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con nome, cognome, indirizzo di posta elettronica e nome della società. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md) (Novità nell'interfaccia utente del portale aziendale)
* [Novità dei mesi precedenti](whats-new-archive.md)
