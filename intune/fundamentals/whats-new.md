---
title: Novità di Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Informazioni sulle novità nel portale di Intune di Azure
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2bb9d921f30e343b309be60438f5318d7c66518
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692251"
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre ad [avvisi importanti](#notices), [versioni precedenti](whats-new-archive.md) e informazioni su [come vengono rilasciati gli aggiornamenti del servizio Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728). 

> [!Note]
> La distribuzione di ogni [aggiornamento mensile](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728), che può impiegare fino a tre giorni, avviene nell'ordine seguente:
>
> - Giorno 1: Asia Pacifico
> - Giorno 2: Europa, Medio Oriente, Africa
> - Giorno 3: America del Nord
>
> Alcune funzionalità possono essere implementate in diverse settimane e durante la prima è possibile che non siano disponibili per tutti i clienti.
>
> Per un elenco delle funzionalità che verranno rilasciate prossimamente, vedere la [pagina delle funzionalità in fase di sviluppo](in-development.md).

**Feed RSS**: è possibile ricevere una notifica quando questa pagina viene aggiornata copiando e incollando l'URL seguente nel lettore di feed: `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>Settimana del 6 gennaio 2020

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>Supporto S/MIME per Microsoft Outlook per iOS<!-- 2669398 -->
Intune supporta l'emissione di certificati di firma e crittografia S/MIME che possono essere usati con Outlook per iOS nei dispositivi iOS. Per altre informazioni, vedere [Etichette di riservatezza e protezione in Outlook per iOS e Android](https://aka.ms/omsmime).

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>Settimana del 30 dicembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>Recuperare la chiave di ripristino personale dai dispositivi macOS crittografati MEM<!-- 4851745 -->
Gli utenti finali possono recuperare la propria chiave di ripristino personale (chiave di FileVault) usando l'app Portale aziendale iOS. Il dispositivo con la chiave di ripristino personale deve essere registrato in Intune e crittografato con FileVault in Intune. Usando l'app Portale aziendale iOS, un utente finale può recuperare la chiave di ripristino personale nel dispositivo macOS crittografato facendo clic su **Ottieni la chiave di ripristino**. La chiave di ripristino può essere recuperata anche da Intune selezionando **Dispositivi** > *il dispositivo macOS crittografato e registrato* > **Ottieni la chiave di ripristino**. Per altre informazioni su FileVault, vedere [Crittografia FileVault per macOS](~/protect/encrypt-devices.md#filevault-encryption-for-macos).

#### <a name="ios-user-licensed-vpp-apps---5619268---"></a>App VPP con licenza utente iOS<!-- 5619268 -->
Per i dispositivi iOS registrati dall'utente, agli utenti finali non verranno più presentate le applicazioni VPP con licenza dispositivo distribuite come disponibili. Gli utenti finali continueranno tuttavia a visualizzare tutte le app VPP con licenza utente all'interno del Portale aziendale. Per altre informazioni sulle app VPP, vedere [Procedura per la gestione delle app iOS e macOS acquistate tramite Volume Purchase Program di Apple con Microsoft Intune](~/apps/vpp-apps-ios.md).

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>Settimana del 23 dicembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>Avviso: scadenza del supporto per Windows 10 1703 (RS2) <!-- 5026679 -->
A partire dal 9 ottobre 2018, non è più previsto il supporto della piattaforma Microsoft per le edizioni Home, Pro e Pro for Workstations di Windows 10 1703 (RS2). Per le edizioni Enterprise ed Education di Windows 10, il supporto della piattaforma per Windows 10 1703 (RS2) è scaduto l'8 ottobre 2019. A partire dal 26 dicembre 2019, la versione minima dell'applicazione Portale aziendale Windows verrà aggiornata a Windows 10 1709 (RS3). I computer che eseguono versioni precedenti alla 1709 non riceveranno più le versioni aggiornate per l'applicazione dal Microsoft Store. Questa modifica è stata già comunicata ai clienti che gestiscono le versioni precedenti di Windows 10 attraverso il centro messaggi. Per altre informazioni, vedere [Date importanti nel ciclo di vita di Windows](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>Settimana del 16 dicembre 2019

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Aggiornamenti di Modelli amministrativi per i dispositivi Windows 10 <!-- 5941568 -->

È possibile usare i modelli ADMX in Microsoft Intune per controllare e gestire le impostazioni per Microsoft Edge, Office e Windows. In Modelli amministrativi di Intune sono ha effettuati i seguenti aggiornamenti delle impostazioni dei criteri:

- Aggiunto il supporto per Microsoft Edge versioni 78 e 79.
- Include i file ADMX dell'11 novembre 2019 nei [file dei modelli amministrativi (ADMX/ADML) e in Strumento di personalizzazione di Office per Office 365 ProPlus, Office 2019 e Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).

Per altre informazioni sui modelli ADMX di Intune, vedere [Usare i modelli di Windows 10 per configurare le impostazioni di criteri di gruppo in Microsoft Intune](../configuration/administrative-templates-windows.md).

Si applica a:

- Windows 10 e versioni successive

## <a name="week-of-december-9-2019-1912-service-release"></a>Settimana del 9 novembre 2019 (versione del servizio 1912)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>Migrazione a Microsoft Edge per gli scenari di esplorazione gestita<!-- 5173762 -->
Con l'approssimarsi del ritiro di Intune Managed Browser, sono state apportate modifiche ai criteri di protezione delle app per semplificare i passaggi necessari per spostare gli utenti in Edge. Sono state aggiornate le opzioni per l'impostazione dei criteri di protezione delle app **Limita il trasferimento di contenuto Web con altre app**, ovvero una delle seguenti:

- Qualsiasi app
- Intune Managed Browser
- Microsoft Edge
- Browser non gestito 

Quando si seleziona **Microsoft Edge**, gli utenti finali visualizzeranno un messaggio di accesso condizionale che informa che per gli scenari di esplorazione gestita è richiesto Microsoft Edge. Verrà richiesto di scaricare e accedere a Microsoft Edge con i propri account AAD, se non lo hanno già fatto.  Questa operazione equivale ad aver impostato su **true** l'impostazione di configurazione delle app `com.microsoft.intune.useEdge` per le app abilitate per MAM. Per i criteri di protezione delle app esistenti che usavano l'impostazione **Browser gestiti da criteri** sarà ora selezionato **Intune Managed Browser** e non sarà visibile alcuna modifica nel comportamento. Questo significa che gli utenti vedranno il messaggio che richiede l'uso di Microsoft Edge se l'impostazione di configurazione dell'app **useEdge** è stata impostata su **True**. Microsoft invita tutti i clienti che sfruttano gli scenari di esplorazione gestita ad aggiornare i criteri di protezione delle app con **Limita il trasferimento di contenuto Web con altre app** per assicurarsi che gli utenti visualizzino le linee guida appropriate per la transizione a Microsoft Edge, indipendentemente dall'app da cui vengono avviati i collegamenti. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>Configurare il contenuto delle notifiche dell'app per gli account dell'organizzazione<!-- 2576686  -->
I criteri di protezione delle app di Intune nei dispositivi Android e iOS consentono di controllare il contenuto delle notifiche dell'app per gli account dell'organizzazione. È possibile selezionare un'opzione (Consenti, Blocca i dati dell'organizzazione o Bloccato) per specificare in che modo vengono visualizzate le notifiche per gli account dell'organizzazione per l'app selezionata. Questa funzionalità richiede il supporto delle applicazioni e può non essere disponibile per tutte le applicazioni abilitate per i criteri di protezione delle app. Outlook per iOS versione 4.15.0 (o successive) e Outlook per Android 4.83.0 (o versione successiva) supporteranno questa impostazione. L'impostazione è disponibile nella console, ma la funzionalità inizierà a essere applicata dopo il 16 dicembre 2019. Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md).

#### <a name="microsoft-app-icons-update--4677605----"></a>Aggiornamento delle icone delle app Microsoft<!--4677605  -->
Le icone usate per le app Microsoft nel riquadro di destinazione app per i criteri di protezione delle app e i criteri di configurazione delle app sono state aggiornate.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Richiedere l'uso di tastiere approvate in Android<!--4761794  -->
Come parte di un criterio di protezione delle app, è possibile specificare l'impostazione [**Tastiere approvate**](../apps/app-protection-policy-settings-android.md#data-protection) per gestire le tastiere Android che possono essere usate con le app Android gestite. Quando un utente apre l'app gestita e non usa ancora una tastiera approvata per l'app, riceve un messaggio che richiede di passare a una delle tastiere approvate già installate nel dispositivo. Se necessario, viene visualizzato un collegamento per scaricare dal Google Play Store una tastiera approvata che l'utente potrà installare e configurare. L'utente può modificare i campi di testo in un'app gestita solo se la tastiera attiva non è una delle tastiere approvate.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>Aggiornamento dell'esperienza Single Sign-On per app e siti Web nei dispositivi iOS, iPadOS e macOS<!-- 4999578  -->
Intune ha aggiunto altre impostazioni di Single Sign-On (SSO) per i dispositivi iOS, iPadOS e macOS. È ora possibile configurare le estensioni delle app per l'accesso SSO con reindirizzamento scritte dall'organizzazione o dal provider di identità. Usare queste impostazioni per configurare un'esperienza Single Sign-On senza problemi per le app e i siti Web che usano i metodi di autenticazione moderni, ad esempio OAuth e SAML2. 

Queste nuove impostazioni ampliano le impostazioni precedenti per le estensioni delle app per l'accesso SSO e l'estensione Kerberos incorporata di Apple (**Dispositivi** > **Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** o **macOS** per il tipo di piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). 

Per visualizzare l'intera gamma di impostazioni delle estensioni delle app per l'accesso SSO che è possibile configurare, andare a [SSO in iOS](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) e [SSO in macOS](../configuration/macos-device-features-settings.md#single-sign-on-app-extension).

Si applica a:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352-wnready-----"></a>Aggiornate due impostazioni relative alle restrizioni per i dispositivi iOS e iPadOS per correggerne il comportamento<!-- 5701352 WNReady   -->
Per i dispositivi iOS, è possibile creare profili di restrizione del dispositivo che **consentono gli aggiornamenti PKI in modalità wireless** e **bloccano la modalità USB con restrizioni** (**Dispositivi** > **Configurazione del dispositivo**  > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Prima di questa versione, le impostazioni e le descrizioni dell'interfaccia utente per le impostazioni seguenti non erano esatte e ora sono state corrette. A partire da questa versione, il comportamento delle impostazioni è il seguente:

**Blocca gli aggiornamenti PKI in modalità wireless**: **Blocca** impedisce agli utenti di ricevere gli aggiornamenti software a meno che il dispositivo non sia connesso a un computer. **Non configurato** (impostazione predefinita): consente a un dispositivo di ricevere gli aggiornamenti software senza essere connesso a un computer.
- In precedenza, questa impostazione poteva essere configurata come segue: **Consenti**, per consentire agli utenti di ricevere gli aggiornamenti software senza connettere i propri dispositivi a un computer.
**Consenti gli accessori USB durante il blocco del dispositivo**: Selezionando **Consenti** gli accessori USB sono autorizzati a scambiare dati con un dispositivo che è rimasto bloccato per più di un'ora. **Non configurato** (impostazione predefinita): la modalità con restrizioni USB non viene aggiornata nel dispositivo e agli accessori USB verrà impedito di trasferire i dati dal dispositivo se rimane bloccato per più di un'ora.
- In precedenza, questa impostazione poteva essere configurata come segue: **Blocca**, per disabilitare la modalità USB con restrizioni nei dispositivi con supervisione.

Per altre informazioni sulle impostazioni configurabili, vedere [Impostazioni dei dispositivi iOS e iPadOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Questa funzionalità si applica a:

- iOS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>Profili di configurazione della rete cablata per i dispositivi macOS<!-- 3508686  -->
   > [!NOTE]
   > Questa funzionalità è stata posticipata, ma verrà presto rilasciata.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Impedisce agli utenti di configurare le credenziali del certificato nell'archivio chiavi gestito nei dispositivi Android Enterprise con proprietario del dispositivo<!-- 3311998 -->
Nei dispositivi Android Enterprise con proprietario del dispositivo è possibile configurare una nuova impostazione che impedisce agli utenti di configurare le proprie credenziali del certificato nell'archivio chiavi gestito (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo > **Utenti e account**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="protected-wipe-action-now-available--51150000---"></a>Azione di cancellazione protetta ora disponibile<!--51150000 -->
Ora si ha la possibilità di usare l'azione Cancella dispositivo per eseguire una cancellazione protetta dei dati da un dispositivo. Le cancellazioni protette sono identiche a quelle standard, tranne per il fatto che non possono essere eluse spegnendo il dispositivo. Una cancellazione dei dati protetta continuerà a provare a reimpostare il dispositivo fino a quando non riesce. In alcune configurazioni questa azione potrebbe impedire il riavvio del dispositivo. Per altre informazioni, vedere [Ritirare o cancellare i dispositivi](../remote-actions/devices-wipe.md).

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>Indirizzo MAC Ethernet del dispositivo aggiunto alla pagina Panoramica del dispositivo<!--5562275 -->
È ora possibile visualizzare l'indirizzo MAC Ethernet del dispositivo nella relativa pagina dei dettagli (**Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Panoramica**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>Ottimizzata l'esperienza in un dispositivo condiviso quando sono abilitati i criteri di accesso condizionale basato su dispositivi<!-- 1734096  -->
È stata migliorata l'esperienza in un dispositivo condiviso con più utenti a cui sono applicati criteri di accesso condizionale basato su dispositivi controllando la valutazione di conformità più recente per l'utente quando si applicano i criteri. Per altre informazioni, vedere gli articoli sui seguenti argomenti:
- [Panoramica di Azure per l'accesso condizionale](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Panoramica della conformità dei dispositivi in Intune](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>Usare i profili certificato PKCS per eseguire il provisioning dei dispositivi con certificati<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
È ora possibile usare i profili certificato PKCS per emettere certificati per i *dispositivi* che eseguono Android for Work, iOS e Windows, se associati a profili come quelli per Wi-Fi e VPN. In precedenza queste tre piattaforme supportavano solo certificati basati sull'utente, con il supporto basato sul dispositivo limitato a macOS.

Per usare un certificato basato sul dispositivo, durante la [creazione di un profilo certificato PKCS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) per le piattaforme supportate, selezionare **Impostazioni**. Sarà possibile visualizzare l'impostazione per il **tipo di certificato**, che supporta le opzioni per il dispositivo o l'utente.



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="centralized-audit-logs--5603185-5697164---"></a>Log di controllo centralizzati<!--5603185, 5697164 -->
Con la nuova gestione centralizzata dei log di controllo ora è possibile riunire i log di controllo di tutte le categorie in un'unica pagina. È possibile filtrare i log per ottenere i dati che si stanno cercando. Per visualizzare i log di controllo, passare ad **Amministrazione del tenant** > **Log di controllo**. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>Informazioni sui tag di ambito incluse nei dettagli attività del log di controllo<!--5763534 -->
I dettagli attività del log di controllo ora includono informazioni sui tag di ambito (per gli oggetti Intune che supportano i tag di ambito). Per altre informazioni sui log di controllo, vedere [Usare i log di controllo per tenere traccia degli eventi e monitorarli](monitor-audit-logs.md).


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>Settimana del 2 dicembre 2019

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>Nuove licenze di co-gestione di Microsoft Endpoint Configuration Manager<!--5027281-->
È ora disponibile una nuova licenza che consente ai clienti di Configuration Manager con Software Assurance di ottenere i diritti di co-gestione di Intune per 10 PC Windows senza dover acquistare una licenza di Intune aggiuntiva per la co-gestione. I clienti non devono più assegnare singole licenze Intune/EMS ai propri utenti finali per la co-gestione di Windows 10.
- I dispositivi gestiti da Configuration Manager e registrati per la co-gestione hanno quasi gli stessi diritti di un PC con gestione MDM autonoma di Intune. Tuttavia, dopo la reimpostazione non è possibile eseguire di nuovo il provisioning tramite Autopilot.
- I dispositivi Windows 10 registrati in Intune con altri mezzi richiedono licenze di Intune complete.
- Per i dispositivi in altre piattaforme sono ancora richieste licenze di Intune complete.

Per altre informazioni, vedere [Condizioni di licenza](https://www.microsoft.com/en-us/Licensing/product-licensing/products).


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>Settimana del 18 novembre 2019 (versione di servizio 1911)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>Aggiornamento dell'interfaccia utente quando si cancellano selettivamente i dati delle app<!-- 4102028 -->
L'interfaccia utente per la cancellazione selettiva dei dati delle app in Intune è stata aggiornata. Le modifiche dell'interfaccia utente includono:
- Un'esperienza semplificata con un formato di tipo procedura guidata condensata in un unico riquadro.
- Aggiornamento del flusso di creazione per includere le assegnazioni.
- Una pagina di riepilogo di tutti gli elementi impostati durante la visualizzazione delle proprietà, prima della creazione di un nuovo criterio o quando si modifica una proprietà. Al momento della modifica delle proprietà, inoltre, il riepilogo visualizzerà solo un elenco di elementi all'interno della categoria di proprietà in corso di modifica.

Per altre informazioni, vedere [Come cancellare solo i dati aziendali dalle app gestite da Intune](~/apps/apps-selective-wipe.md).

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>Supporto per le tastiere di terze parti per iOS e iPadOS<!-- 4922950 -->
Nel marzo 2019 è stata annunciata la rimozione del supporto per l'impostazione dei criteri di protezione delle app iOS "Tastiere di terze parti". La funzionalità è di nuovo disponibile in Intune con supporto sia per iOS che per iPadOS. Per abilitare questa impostazione, visitare la scheda **Protezione dati** di un criterio di protezione nuovo o esistente per le app iOS/iPadOS e trovare l'impostazione **Tastiere di terze parti** in **Trasferimento di dati**.

Il comportamento di questa impostazione dei criteri è leggermente diverso rispetto all'implementazione precedente. Nelle app con più identità che usano l'SDK versione 12.0.16 e successive, soggette a criteri di protezione delle app con questa impostazione configurata su **Blocco**, gli utenti finali non saranno in grado di scegliere le tastiere di terze parti sia nell'organizzazione che negli account personali. Le app che usano le versioni 12.0.12 e precedenti dell'SDK continueranno a presentare il comportamento illustrato nel post di blog relativo ai [problemi dovuti all'assenza del blocco delle tastiere di terze parti in iOS per gli account personali](https://aka.ms/3rdparty_iOS_Intune).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Definire come destinazione gruppi di utenti macOS per richiedere la gestione Jamf<!-- 4061739  --> 
È possibile definire come destinazione gruppi di utenti specifici i cui [dispositivi macOS verranno gestiti da Jamf](../protect/conditional-access-integrate-jamf.md). Ciò consente di applicare l'integrazione di conformità Jamf a un subset di dispositivi macOS mentre altri dispositivi sono gestiti da Intune. Se si sta già usando l'integrazione Jamf, per impostazione predefinita tutti gli utenti verranno definiti come destinazione per l'integrazione.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>Nuove impostazioni di Exchange ActiveSync durante la creazione di un profilo di configurazione del dispositivo di posta elettronica nei dispositivi iOS<!-- 4892824   --> 
Nei dispositivi iOS/iPadOS è possibile configurare la connettività di posta elettronica in un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Posta elettronica** per il tipo di profilo). 

Sono disponibili nuove impostazioni di Exchange ActiveSync, tra cui:
- **Dati di Exchange da sincronizzare**: Scegliere i servizi di Exchange da sincronizzare (o di cui bloccare la sincronizzazione) per calendario, contatti, promemoria, note e posta elettronica.
- **Consenti agli utenti di modificare le impostazioni di sincronizzazione**: Consentire, o impedire, agli utenti di modificare le impostazioni di sincronizzazione per questi servizi nei propri dispositivi.  

Per altre informazioni su questa impostazione, vedere le [impostazioni del profilo di posta elettronica per i dispositivi iOS in Intune](../configuration/email-settings-ios.md). 

Si applica a:

- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>Impedire agli utenti di aggiungere account Google personali a dispositivi Android Enterprise completamente gestiti e dedicati<!-- 5353228   -->
Nei dispositivi Android Enterprise completamente gestiti e dedicati è disponibile una nuova impostazione che impedisce agli utenti di creare account Google personali (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo > **impostazioni Utenti e account** > **Account Google personale**).

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:

- Dispositivi completamente gestiti Android Enterprise
- Dispositivi dedicati Android Enterprise

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>La registrazione lato server per l'impostazione dei comandi Siri viene rimossa nel profilo Limitazioni del dispositivo iOS/iPadOS <!-- 5468501   -->
Nei dispositivi iOS e iPadOS l'impostazione della **registrazione lato server per i comandi Siri** viene rimossa dalla console di amministrazione di Microsoft Endpoint Manager (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App predefinite**). 

Questa impostazione non ha alcun effetto sui dispositivi. Per rimuovere l'impostazione dai profili esistenti, aprire il profilo, apportare le modifiche e quindi salvare il profilo. Il profilo viene aggiornato e l'impostazione viene eliminata dai dispositivi.

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi iOS e iPadOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Aggiornamenti delle funzionalità di Windows 10 (anteprima pubblica)<!-- 2384877 -->
È ora possibile distribuire gli [aggiornamenti delle funzionalità di Windows 10](../protect/windows-update-for-business-configure.md#windows-10-feature-updates) ai dispositivi Windows 10. Gli aggiornamenti delle funzionalità di Windows 10 sono nuovi criteri di aggiornamento software che impostano la versione di Windows 10 che si vuole venga installata e mantenuta nei dispositivi. È possibile usare questo nuovo tipo di criteri insieme agli anelli di aggiornamento di Windows 10 esistenti.

I dispositivi che ricevono i criteri di aggiornamento delle funzionalità di Windows 10 installeranno la versione specificata di Windows e rimarranno con tale versione fino a quando i criteri non verranno modificati o rimossi. I dispositivi che eseguono una versione successiva di Windows rimangono alla versione corrente. I dispositivi che mantengono una versione specifica di Windows possono comunque installare gli aggiornamenti di qualità e sicurezza per tale versione dagli anelli di aggiornamento di Windows 10.

Questo nuovo tipo di criteri viene implementato nei tenant a partire da questa settimana. Se questi criteri non sono ancora disponibili per il proprio tenant, lo saranno presto.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>Aggiungere e modificare le informazioni fondamentali nei file PLIST per le applicazioni macOS<!-- 4736278 -->
Nei dispositivi macOS è ora possibile creare un profilo di configurazione del dispositivo che carica un file di elenco di proprietà (PLIST) associato a un'app o al dispositivo (**Dispositivi** > **Profili di configurazione** > **Crea profilo** > **macOS** per la piattaforma > **File delle preferenze** per il tipo di profilo).

Solo alcune app supportano le preferenze gestite e queste app potrebbero non consentire la gestione di tutte le impostazioni. Assicurarsi di caricare un file di elenco di proprietà che configuri le impostazioni dei canali del dispositivo e non le impostazioni dei canali degli utenti.

Per altre informazioni su questa funzionalità, vedere [Aggiungere un file elenco di proprietà ai dispositivi macOS usando Microsoft Intune](../configuration/preference-file-settings-macos.md).

Si applica a:

- Dispositivi macOS che eseguono la versione 10.7 e successive

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Modificare il valore del nome dispositivo per i dispositivi Autopilot<!-- 2640074 -->
È possibile modificare il valore Nome dispositivo per i dispositivi Autopilot aggiunti ad Azure AD.  Per altre informazioni, vedere la sezione sulla [modifica degli attributi dei dispositivi Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Modificare il valore del tag di gruppo per i dispositivi Autopilot<!-- 4816775   -->
È possibile modificare il valore Tag di gruppo per i dispositivi Autopilot. Per altre informazioni, vedere la sezione sulla [modifica degli attributi dei dispositivi Autopilot](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="updated-support-experience---5012398---"></a>Esperienza di supporto tecnico aggiornata<!-- 5012398 -->

A partire da ora, viene implementata nei tenant un'esperienza nella console aggiornata e semplificata per [accedere a Guida e supporto tecnico per Intune](get-support.md). Se questo tipo di esperienza non è ancora disponibile per il proprio tenant, lo sarà presto.

Sono stati migliorati la ricerca e il feedback nella console per i problemi comuni nonché il flusso di lavoro usato per contattare il supporto tecnico. Quando si apre una richiesta di assistenza, vengono visualizzate stime in tempo reale dei tempi previsti per la risposta via telefono o posta elettronica e i clienti Premier e Unified Support hanno la possibilità di indicare la gravità del problema per ricevere più rapidamente assistenza.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>Ottimizzazione dell'esperienza di creazione di report di Intune (anteprima pubblica) <!-- 3791418 -->
Intune offre ora un'esperienza ottimizzata per la creazione dei report, inclusi i nuovi tipi, una migliore organizzazione dei report, visualizzazioni più mirate, funzionalità avanzate per i report, nonché dati più coerenti e tempestivi. I nuovi tipi di report sono incentrati sugli elementi seguenti:
- **Operativo**: contiene record aggiornati concentrati sugli stati negativi dell'integrità. 
- **Organizzativo**: offre un riepilogo più ampio dello stato generale.
- **Cronologico**: offre modelli e tendenze nell'arco di un determinato periodo di tempo.
- **Specialistico**: consente di usare i dati non elaborati per creare i propri report personalizzati.

Il primo set di nuovi report è incentrato sulla conformità del dispositivo. Per altre informazioni, vedere il [post di blog sul framework di reporting di Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) e [Report di Intune](~/fundamentals/reports.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>Duplicare ruoli personalizzati o predefiniti <!-- 1081938   -->
È ora possibile copiare i ruoli predefiniti e personalizzati. Per altre informazioni, vedere l'articolo relativo alla [copia di un ruolo](../fundamentals/create-custom-role.md#copy-a-role).

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>Nuove autorizzazioni per il ruolo di amministratore di istituto di istruzione <!-- 5621805  -->  
Sono state aggiunte due nuove autorizzazioni, **Assegnare il profilo** e **Dispositivo sincronizzato**, al ruolo di amministratore di istituto di istruzione > **Autorizzazioni** > **Programmi di registrazione**. L'autorizzazione del profilo di sincronizzazione consente agli amministratori dei gruppi di sincronizzare i dispositivi di Windows Autopilot. L'autorizzazione Assegnare il profilo consente di eliminare i profili di registrazione Apple avviati dall'utente. Consente inoltre di gestire le assegnazioni dei dispositivi Autopilot e le assegnazioni dei profili di distribuzione Autopilot. Per un elenco di tutte le autorizzazioni per l'amministratore del gruppo o dell'istituto di istruzione, vedere [Assegnare amministratori ai gruppi](https://docs.microsoft.com/intune-education/group-admin-delegate). 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>Sicurezza

#### <a name="bitlocker-key-rotation---2564951----"></a>Rotazione delle chiavi BitLocker<!-- 2564951  -->
È possibile usare un'azione del dispositivo Intune per [ruotare le chiavi di ripristino di BitLocker](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys) in modalità remota per i dispositivi gestiti che eseguono Windows versione 1909 o successiva. Per essere idonei alla rotazione delle chiavi di ripristino, i dispositivi devono essere configurati in modo da supportare tale rotazione.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>Aggiornamenti alla registrazione di dispositivi dedicati per supportare la distribuzione del certificato dispositivo SCEP <!-- 5198878  -->
Intune ora supporta la distribuzione del certificato dispositivo SCEP ai dispositivi Android Enterprise dedicati per l'accesso basato su certificati ai profili Wi-Fi. Per il corretto funzionamento della distribuzione, è necessario che l'app Microsoft Intune sia presente nel dispositivo. Di conseguenza, l'esperienza di registrazione per i dispositivi Android Enterprise dedicati è stata aggiornata. Le nuove registrazioni iniziano ancora allo stesso modo (con QR, NFC, Zero Touch o identificatore del dispositivo) ma ora hanno un passaggio che richiede agli utenti di installare l'app di Intune. I dispositivi esistenti inizieranno progressivamente a installare automaticamente l'app.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>Log di controllo di Intune per la collaborazione business-to-business<!--5670211 -->
La collaborazione business-to-business (B2B) consente di condividere in modo sicuro le applicazioni e i servizi dell'azienda con gli utenti guest di qualsiasi altra organizzazione, mantenendo al tempo stesso il controllo sui propri dati aziendali. Intune ora supporta i log di controllo per gli utenti guest B2B. Ad esempio, quando gli utenti guest apportano modifiche, Intune sarà in grado di acquisire i dati usando i log di controllo. Per altre informazioni, vedere [Che cos'è l'accesso utente guest in Azure Active Directory B2B?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>Settimana del 11 novembre 2019  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>Esperienza di registrazione macOS migliorata in Portale aziendale <!-- 5074349  -->  
Il Portale aziendale per l'esperienza di registrazione di macOS prevede un processo di registrazione più semplice che si allinea maggiormente al Portale aziendale per l'esperienza di registrazione di iOS. Gli utenti dei dispositivi ora possono visualizzare:  

* Un'interfaccia utente più accattivante.  
* Un elenco di controllo per la registrazione migliorato.  
* Istruzioni più chiare su come registrare i dispositivi.  
* Opzioni di risoluzione dei problemi migliorate.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>App Web avviate dall'app Windows Portale aziendale<!-- 5030972 -->
Gli utenti finali possono ora avviare app Web direttamente dall'app Windows Portale aziendale. Gli utenti finali possono selezionare l'app Web e quindi scegliere l'opzione **Apri nel browser**. L'URL Web pubblicato viene aperto direttamente in un Web browser. Questa funzionalità verrà implementata nel corso della prossima settimana. Per altre informazioni sull'aggiunta di app Web, vedere [Aggiungere app Web in Microsoft Intune](~/apps/web-app.md).  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Nuova colonna Tipo di assegnazione in Portale aziendale per Windows 10 <!-- 5459950  -->
La colonna Portale aziendale > **App installate** > **Tipo di assegnazione** è stata rinominata **Richiesta dall'organizzazione**.  In tale colonna verrà visualizzato **Sì** o **No** per indicare se un'app è obbligatoria o facoltativa per l'organizzazione. Queste modifiche sono state apportate perché gli utenti dei dispositivi erano confusi in merito al concetto di app disponibili. Per altre informazioni sull'installazione di app nel Portale aziendale, vedere [Installare e condividere app nel dispositivo](/intune-user-help/install-apps-cpapp-windows). Per altre informazioni sulla configurazione dell'app Portale aziendale per gli utenti, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>Settimana del 4 novembre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>Le baseline di sicurezza sono supportate in Microsoft Azure per enti pubblici<!-- 4062552 -->

Le istanze di Intune ospitate in *Microsoft Azure per enti pubblici* ora possono usare le [baseline di sicurezza](../protect/security-baselines.md) per la protezione degli utenti e dei dispositivi.

<!-- ########################## -->
## <a name="week-of-october-28-2019"></a>Settimana del 28 ottobre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Progettazione dell'elenco di controllo migliorata nell'app Portale aziendale per Android<!-- 5550857 -->  
L'elenco di controllo della configurazione nell'app Portale aziendale per Android è stato aggiornato con una progettazione semplificata e nuove icone. Le modifiche sono in linea con gli aggiornamenti recenti dell'app Portale aziendale per iOS. Per un confronto affiancato delle modifiche, vedere [Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune](whats-new-app-ui.md). Per informazioni sulla procedura di registrazione aggiornata, vedere [Registrare un dispositivo con profilo di lavoro Android](/intune-user-help/enroll-device-android-work-profile) e [Registrare il dispositivo in Portale aziendale](/intune-user-help/enroll-device-android-company-portal).  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>App Win32 in dispositivi in modalità Windows 10 S<!-- 3747604 --> 
È possibile installare ed eseguire app Win32 in dispositivi gestiti in modalità Windows 10 S. A tale scopo, è possibile creare uno o più criteri aggiuntivi per la modalità S usando gli strumenti di PowerShell del Controllo delle applicazioni di Windows Defender. Firmare i criteri supplementari con il portale per la firma di Device Guard e quindi caricare e distribuire i criteri tramite Intune. In Intune è possibile trovare questa funzionalità selezionando **App client** > **Criteri supplementari di Windows 10S**. Per altre informazioni, vedere [Abilitare le app Win32 in dispositivi in modalità S](~/apps/apps-win32-s-mode.md).

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>Impostare la disponibilità delle app Win32 in base a una data e un'ora<!-- 3510685 -->
In qualità di amministratore è possibile configurare l'ora di inizio e l'ora di scadenza per un'app Win32 richiesta. All'ora di inizio, l'estensione di gestione di Intune avvia il download del contenuto dell'app e lo memorizza nella cache. L'app viene installata all'ora di scadenza. Per le app disponibili, l'ora di inizio stabilisce quando l'app è visibile nel Portale aziendale. Per altre informazioni, vedere [Gestione di app Win32](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications).

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Richiedere il riavvio del dispositivo in base al periodo di tolleranza dopo l'installazione dell'app Win32<!-- 3136567 -->
È possibile richiedere che un dispositivo venga riavviato dopo il completamento dell'installazione di un'app Win32. Per altre informazioni, vedere [Gestione di app Win32 - Configurare i dettagli di installazione dell'app](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details).

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>Modalità scura per il portale aziendale iOS<!-- 4911422 -->
La modalità scura è disponibile per il portale aziendale iOS. Gli utenti possono scaricare le app aziendali, gestire i propri dispositivi e ottenere supporto tecnico nella combinazione di colori scelta in base alle impostazioni del dispositivo. Il portale aziendale iOS adatterà automaticamente le impostazioni del dispositivo dell'utente finale per la modalità scura o chiara. Per altre informazioni, vedere l'[introduzione alla modalità scura nell'app Portale aziendale di Microsoft Intune per iOS](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453). Per altre informazioni sul Portale aziendale iOS, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](~/apps/company-portal-app.md).

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Versione minima dell'app applicata per il Portale aziendale Android<!-- 2378776 -->
Usando l'impostazione **Versione minima del Portale aziendale** di un criterio di protezione dell'app è possibile indicare una versione minima definita specifica del Portale aziendale da applicare a un dispositivo di un utente finale. Questa impostazione di avvio condizionale consente di impostare il **blocco dell'accesso**, la **cancellazione dei dati** e l'**avviso** come azioni possibili quando il valore non è soddisfatto. I formati possibili per questo valore seguono il criterio *[Major].[Minor]* , *[Major].[Minor].[Build]* o *[Major].[Minor].[Build].[Revision]* .

L'impostazione **Versione minima del Portale aziendale**, se configurata, influisce su tutti gli utenti finali che ottengono la versione 5.0.4560.0 e le versioni future del Portale aziendale. Questa impostazione non influisce sugli utenti che usano una versione del Portale aziendale precedente alla versione con la quale questa funzionalità viene rilasciata. Gli utenti finali che usano gli aggiornamenti automatici delle app nel proprio dispositivo probabilmente non visualizzeranno alcuna finestra di dialogo di questa funzionalità, dal momento che probabilmente avranno la versione del Portale aziendale più recente. Questa impostazione è presente solo in Android con la protezione delle app per i dispositivi registrati e non registrati. Per altre informazioni, vedere [Impostazioni dei criteri di protezione delle app per Android - Avvio condizionale](~/apps/app-protection-policy-settings-android.md#conditional-launch).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Gestione dei dispositivi per Microsoft 365

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Introduzione al nodo Endpoint Security in Gestione dei dispositivi per Microsoft 365<!-- 5630102 -->

Il nodo **Endpoint Security** è ora disponibile a livello generale nell'area di lavoro specializzata di Gestione dei dispositivi per Microsoft 365 in https://devicemanagement.microsoft.com, che raggruppa le funzionalità di protezione degli endpoint, ad esempio:

- Baseline di sicurezza:  Gruppo preconfigurato di impostazioni che consentono di applicare il gruppo noto di impostazioni e valori predefiniti consigliati da Microsoft.

- Attività relative alla sicurezza: Possibilità di usufruire della gestione delle minacce e delle vulnerabilità di Microsoft Defender ATP e di usare Intune per correggere i punti deboli degli endpoint.

- Microsoft Defender ATP: Microsoft Defender Advanced Threat Protection è una funzionalità integrata che consente di prevenire le violazioni della sicurezza.

Queste impostazioni continueranno a essere accessibili da altri nodi applicabili, ad esempio i dispositivi, e lo stato attuale configurato sarà lo stesso a prescindere dal punto in cui si accede e si abilitano le funzionalità.

Per altre informazioni su questi miglioramenti, vedere il [post di blog Intune Customer Success](https://aka.ms/Endpoint_security_node) sul sito Web della community IT di Microsoft.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune supporta iOS 11 e versioni successive<!-- 4665324  -->

L'iscrizione e il Portale aziendale di Intune supportano ora le versioni 11 e successive di iOS. Le versioni precedenti non sono supportate.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Baseline di Microsoft Edge (anteprima)<!--  3787164  -->

È stata aggiunta un'anteprima della baseline di sicurezza per le [impostazioni di Microsoft Edge](../protect/security-baseline-settings-edge.md). 

<!-- ########################## -->
## <a name="week-of-october-21-2019-1910-service-release"></a>Settimana del 21 ottobre 2019 (versione del servizio 1910)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Gestione dei dispositivi per Microsoft 365

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Esperienza di amministrazione migliorata in Gestione dei dispositivi per Microsoft 365<!-- 5551239 -->

Un'esperienza di amministrazione semplificata e aggiornata è ora disponibile a livello generale nell'area di lavoro specializzata di Gestione dei dispositivi per Microsoft 365 all'indirizzo[https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com) e include:

- **Navigazione aggiornata**: Disponibilità di una navigazione di primo livello semplificata che raggruppa logicamente le funzionalità.
- **Nuovi filtri della piattaforma**: È possibile selezionare una singola piattaforma, per visualizzare solo i criteri e le app relativi alla piattaforma selezionata, nelle pagine Dispositivi e App.
- **Nuova home page**: È possibile visualizzare rapidamente l'integrità del servizio, lo stato del tenant, le notizie e così via nella nuova home page.

Per altre informazioni su questi miglioramenti, vedere il [post di blog Enterprise Mobility + Security](https://go.microsoft.com/fwlink/?linkid=2109094) sul sito Web della community IT di Microsoft.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>Aggiungere app Mobile Threat Defense a dispositivi non registrati<!-- 3005337 -->
È possibile creare criteri di protezione delle app di Intune per bloccare o cancellare in modo selettivo i dati aziendali degli utenti in base all'integrità di un dispositivo. L'integrità del dispositivo viene determinata usando una soluzione Mobile Threat Defense. Questa funzionalità esiste oggi con i dispositivi registrati in Intune come impostazione di conformità del dispositivo. Grazie a questa nuova funzionalità, il rilevamento delle minacce viene esteso da un fornitore di Mobile Threat Defense in modo da funzionare sui dispositivi non registrati. In Android questa funzionalità richiede il portale aziendale più recente nel dispositivo. In iOS questa funzionalità sarà disponibile per l'uso con l'integrazione delle app nella versione più recente di Intune SDK (successiva alla 12.0.15). L'argomento Novità verrà aggiornato quando la prima app adotta la versione più recente di Intune SDK. Le altre app diventeranno disponibili progressivamente. Per altre informazioni, vedere [Creare criteri di protezione delle app Mobile Threat Defense con Intune](~/protect/mtd-app-protection-policy.md).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Nuovo profilo di interfaccia di configurazione del firmware del dispositivo per dispositivi Windows 10 e versioni successive (anteprima pubblica)<!-- 2266073  -->

In Windows 10 e versioni successive è possibile creare un profilo di configurazione del dispositivo per controllare le impostazioni e le funzionalità (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma). In questo aggiornamento è disponibile un nuovo tipo di profilo dell'interfaccia di configurazione del firmware del dispositivo che consente a Intune di gestire le impostazioni UEFI (BIOS).

Per altre informazioni su questa funzionalità, vedere [Usare profili DFCI nei dispositivi Windows in Microsoft Intune](../configuration/device-firmware-configuration-interface-windows.md).

Si applica a:

- Windows 10 RS5 (1809) e versioni successive nel firmware supportato

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>Elemento di attivazione/disattivazione che consente di visualizzare solo la pagina Stato registrazione per i dispositivi sottoposti a provisioning dalla Configurazione guidata<!--3959566-->
È ora possibile scegliere di visualizzare solo la pagina Stato registrazione per i dispositivi sottoposti a provisioning dalla Configurazione guidata di Autopilot.

Per visualizzare il nuovo elemento di attivazione/disattivazione, scegliere **Intune** > **Registrazione del dispositivo** > **Registrazione di Windows** > **Pagina Stato registrazione** > **Crea profilo** > **Impostazioni**  > **Mostra la pagina solo ai dispositivi sottoposti a provisioning dalla Configurazione guidata**.


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>Settimana del 14 ottobre 2019

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Creazione di report per le app disponibili in Google Play per i profili di lavoro Android<!-- 3041956   -->
Per le installazioni di app disponibili nei dispositivi con profilo di lavoro Android Enterprise dedicati e completamenti gestiti è possibile visualizzare lo stato di installazione delle app, nonché la versione installata delle app gestite in Google Play. Per altre informazioni, vedere [Come monitorare i criteri di protezione delle app](~/apps/app-protection-policies-monitor.md), [Gestire i dispositivi con profilo di lavoro Android con Intune](~/enrollment/android-enterprise-overview.md) e [Tipo di app Google Play gestite](~/apps/apps-add-android-for-work.md#managed-google-play-app-types).

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Microsoft Edge versione 77 e successive per Windows 10 e macOS (anteprima pubblica)<!-- 3872025, 4678761  -->
Microsoft Edge versione 77 e successive sarà disponibile per la distribuzione nei PC che eseguono Windows 10 e macOS. 

L'anteprima pubblica offre i canali **Sviluppo** e **Beta** per Windows 10 e un canale **Beta** per macOS. La distribuzione è solo in lingua inglese (EN), ma gli utenti finali possono modificare la lingua di visualizzazione nel browser in **Impostazioni** > **Lingue**. Microsoft Edge è un'app Win32 installata nel contesto di sistema e in architetture corrispondenti (app x86 in un sistema operativo x86 e app x64 in un sistema operativo x64). Inoltre, gli aggiornamenti automatici de browser sono **attivi** per impostazione predefinita e non è possibile disinstallare Microsoft Edge. Per altre informazioni, vedere [Aggiungere Microsoft Edge per Windows 10 a Microsoft Intune](~/apps/apps-windows-edge.md) e la [documentazione di Microsoft Edge](https://go.microsoft.com/fwlink/?linkid=2103823).

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>Aggiornamento dell'interfaccia utente per la protezione delle app e dell'interfaccia utente per il provisioning delle app iOS<!-- 4102027, 4102029   -->
L'interfaccia utente per creare e modificare i criteri di protezione delle app e i profili di provisioning delle app iOS in Intune è stata aggiornata. Le modifiche dell'interfaccia utente includono:
- Un'esperienza semplificata con un formato di tipo procedura guidata condensata in un unico pannello. 
- Aggiornamento del flusso di creazione per includere le assegnazioni.
- Una pagina di riepilogo di tutti gli elementi impostati durante la visualizzazione delle proprietà, prima della creazione di un nuovo criterio o quando si modifica una proprietà. Al momento della modifica delle proprietà, inoltre, il riepilogo visualizzerà solo un elenco di elementi all'interno della categoria di proprietà in corso di modifica.

Per altre informazioni, vedere [Come creare e assegnare criteri di protezione delle app](~/apps/app-protection-policies.md) e [Usare i profili di provisioning delle app iOS](~/apps/app-provisioning-profile-ios.md).

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Scenari guidati di Intune<!-- 4850318, 4831296, 3610611  -->
Intune offre ora scenari guidati che consentono di completare un'attività specifica o un set di attività specifico all'interno di Intune. Uno scenario guidato è costituito da una serie personalizzata di passaggi (flusso di lavoro) incentrati su un caso d'uso end-to-end. Gli scenari comuni sono definiti in base al ruolo svolto da un amministratore, un utente o un dispositivo nell'organizzazione. Questi flussi di lavoro richiedono in genere una raccolta di profili, impostazioni, applicazioni e controlli di sicurezza orchestrati con attenzione per offrire livelli ottimali di esperienza utente e sicurezza. I nuovi scenari guidati includono:
- [Distribuisci Microsoft Edge per dispositivi mobili](~/fundamentals/guided-scenarios-edge.md)
- [Proteggi le app di Office per dispositivi mobili](~/fundamentals/guided-scenarios-office-mobile.md) 
- [Desktop moderno gestito da cloud](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

Per altre informazioni, vedere [Panoramica degli scenari guidati di Intune](guided-scenarios-overview.md).

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>Disponibilità di una variabile di configurazione delle app aggiuntiva<!-- 4969237   -->
Quando si creano criteri di configurazione delle app, è possibile includere la variabile di configurazione `AAD Device ID` come parte delle impostazioni di configurazione. In Intune selezionare **App client** > **Criteri di configurazione dell'app** > **Aggiungi**. Immettere i dettagli dei criteri di configurazione e selezionare **Impostazioni di configurazione** per visualizzare il pannello **Impostazioni di configurazione**. Per altre informazioni, vedere [Aggiungere criteri di configurazione delle app per i dispositivi Android Enterprise gestiti - Usare la finestra di progettazione di configurazione ](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer).


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>Creare gruppi di oggetti di gestione denominati set di criteri<!-- 3762880  -->
I set di criteri consentono di creare aggregazioni di riferimenti a entità di gestione già esistenti che devono essere identificate, selezionate e monitorate come una singola unità concettuale. I set di criteri non sostituiscono concetti o oggetti esistenti. È possibile continuare ad assegnare singoli oggetti in Intune ed è possibile fare riferimento a singoli oggetti come parte di un set di criteri. Pertanto, tutte le modifiche apportate ai singoli oggetti verranno rispecchiate nel set di criteri.  In Intune è possibile selezionare **Set di criteri** > **Crea** per creare un nuovo set di criteri. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Aggiornamento dell'interfaccia utente per la creazione e la modifica di anelli di aggiornamento di Windows 10<!-- 4099089         -->
È stata aggiornata l'esperienza dell'interfaccia utente per la [creazione e la modifica degli anelli di aggiornamento di Windows 10](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings) per Intune. Le modifiche all'interfaccia utente includono:  
- Un formato di tipo procedura guidata condensato in un singolo pannello della console, che elimina i tanti pannelli visualizzati in precedenza durante la configurazione degli anelli di aggiornamento.   
- Il flusso di lavoro modificato include le assegnazioni, prima di completare la configurazione iniziale dell'anello.
- È possibile usare una pagina di riepilogo per verificare tutte le configurazioni effettuate, prima di salvare e distribuire un nuovo anello di aggiornamento. Quando si modifica un anello di aggiornamento, il riepilogo mostra solo l'elenco di elementi impostati all'interno della categoria delle proprietà modificate.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>Aggiornamento dell'interfaccia utente per la creazione e la modifica dei criteri di aggiornamento software iOS<!-- 4099090       --> 
È stata aggiornata l'esperienza dell'interfaccia utente per la [creazione](../protect/software-updates-ios.md#configure-the-policy) e la [modifica](../protect/software-updates-ios.md#edit-a-policy) dei criteri di aggiornamento software iOS per Intune.  Le modifiche all'interfaccia utente includono:  
- Un formato di tipo procedura guidata condensato in un singolo pannello della console, che elimina i tanti pannelli visualizzati in precedenza durante la configurazione degli criteri di aggiornamento.   
- Il flusso di lavoro modificato include le assegnazioni, prima di completare la configurazione iniziale dei criteri.
- È possibile usare una pagina di riepilogo per verificare tutte le configurazioni effettuate, prima di salvare e distribuire un nuovo criterio. Quando si modifica un criterio, il riepilogo mostra solo l'elenco di elementi impostati all'interno della categoria delle proprietà modificate.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404--------"></a>Le impostazioni di riavvio in caso di occupato sono state rimosse dagli anelli di aggiornamento di Windows<!--  4464404      -->
Come annunciato in precedenza, gli anelli di aggiornamento di Windows 10 di Intune ora [supportano impostazioni per le scadenze](../protect/windows-update-settings.md) e non supportano più il *riavvio in caso di occupato*. Le impostazioni per il *riavvio in caso di occupato* non sono più disponibili quando si configurano o gestiscono gli anelli di aggiornamento in Intune.  

Questa modifica è in linea con le [modifiche di manutenzione di Windows](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing) recenti e nei dispositivi che eseguono Windows 10 1903 o versione successiva le *scadenze* sostituiscono le configurazioni per il *riavvio in caso di occupato*.

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Impedire l'installazione di app da origini sconosciute nei dispositivi con profilo di lavoro Android Enterprise<!-- 4760025   -->
Nei dispositivi con profilo di lavoro Android Enterprise gli utenti non possono mai installare app da origini sconosciute. In questo aggiornamento è disponibile una nuova impostazione: **Impedisci le installazioni di app da origini sconosciute nel profilo personale**. Per impostazione predefinita, questa impostazione impedisce agli utenti di effettuare il sideload delle app da origini sconosciute nel profilo personale del dispositivo.

Per visualizzare l'impostazione configurabile, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:

- Profilo di lavoro di Android Enterprise

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Creare un proxy HTTP globale nei dispositivi Android Enterprise con proprietario del dispositivo<!-- 4816339   -->
Nei dispositivi Android Enterprise è possibile configurare un proxy HTTP globale per soddisfare gli standard di esplorazione Web dell'organizzazione (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma> **Proprietario del dispositivo > Limitazioni del dispositivo** per il tipo di profilo > **Connettività**). Eseguita la configurazione, tutto il traffico HTTP userà questo proxy.

Per configurare questa funzionalità e visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:

- Proprietario del dispositivo Android Enterprise

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>L'impostazione per la connessione automatica viene rimossa nei profili Wi-Fi per l'amministratore di dispositivi Android e in Android Enterprise<!-- 5021055   -->
Nei dispositivi di tipo amministratore di dispositivi Android e Android Enterprise è possibile creare un profilo Wi-Fi per configurare diverse impostazioni (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Amministratore di dispositivi Android** o **Android Enterprise** per la piattaforma> **Wi-Fi** per il tipo di profilo). In questo aggiornamento l'impostazione **Connetti automaticamente** viene rimossa, in quanto [non è supportata da Android](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29). 

Se si usa questa impostazione in un profilo Wi-Fi, è possibile notare che **Connetti automaticamente** non funziona. Non è necessario eseguire alcuna azione, ma è necessario tenere presente che questa impostazione è stata rimossa nell'interfaccia utente di Intune.

Per visualizzare le impostazioni correnti, passare a [Impostazioni Wi-Fi Android](../configuration/wi-fi-settings-android.md) o [Impostazioni Wi-Fi Android Enterprise](../configuration/wi-fi-settings-android-enterprise.md).

Si applica a:

- Amministratore dispositivo Android 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>Nuove impostazioni di configurazione del dispositivo per dispositivi iOS e iPadOS con supervisione<!-- 5199328   -->
Nei dispositivi iOS e iPadOS è possibile creare un profilo per limitare le funzionalità e le impostazioni nei dispositivi (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS/iPadOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). In questo aggiornamento sono disponibili nuove impostazioni che è possibile controllare: 
- Accesso all'unità di rete nell'app File  
- Accesso all'unità USB nell'app File 
- Wi-Fi sempre attivato 

Per visualizzare queste impostazioni, andare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:

- iOS 13.0 e versioni successive
- iPadOS 13.0 e versioni successive

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>Specificare le versioni del sistema operativo del dispositivo Android registrate con il profilo di lavoro o la registrazione dell'amministratore di dispositivi<!-- 4350697   -->
Usando le limitazioni del tipo di dispositivo di Intune, è possibile usare la versione del sistema operativo del dispositivo per specificare quali dispositivi utente useranno la registrazione del profilo di lavoro di Android Enterprise o la registrazione dell'amministratore di dispositivi Android.  Per altre informazioni, vedere [Impostare le restrizioni di registrazione](../enrollment/enrollment-restrictions-set.md).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Nuove restrizioni per la ridenominazione dei dispositivi Windows<!-- 3478938  -->
Quando si rinomina un dispositivo Windows è necessario seguire nuove regole:
- Massimo 15 caratteri (deve essere minore o uguale a 63 byte, escluso il valore NULL finale)
- Non è Null o una stringa vuota
- Caratteri ASCII consentiti: lettere (a-z, A-Z), numeri (0-9) e segni meno
- Caratteri Unicode consentiti: >= 0x80, devono essere caratteri UTF8 validi, devono essere mappabili a IDN (ovvero RtlIdnToNameprepUnicode ha esito positivo; vedere RFC 3492)
- I nomi non possono essere composti esclusivamente da numeri
- Non sono consentiti spazi nel nome
- Caratteri non consentiti: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 Per altre informazioni, vedere [Rinominare un dispositivo in Intune](../remote-actions/device-rename.md).

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>Nuovo report Android nella pagina di panoramica dei dispositivi<!-- 4924364 -->
Un nuovo report nella pagina di panoramica dei dispositivi visualizza il numero di dispositivi Android registrati in ogni soluzione di gestione dei dispositivi. Questo grafico mostra il numero di dispositivi registrati con profilo di lavoro, completamente gestiti, dedicati e con registrazione di tipo amministratore di dispositivi. Per visualizzare il report, scegliere **Intune**  > **Dispositivi**  > **Panoramica**.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>Certificati PKCS per macOS<!-- 1333650       -->
È ora possibile [usare certificati PKCS con macOS](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile). È possibile selezionare il certificato PKCS come tipo di profilo per macOS e distribuire i certificati utente e dispositivo che hanno [campi personalizzati per il soggetto e il nome alternativo del soggetto](../protect/certficates-pfx-configure.md#subject-name-format).  

Il certificato PKCS per macOS supporta anche una nuova impostazione: _Consenti a tutte le app l'accesso alla chiave privata_. Con questa impostazione è possibile consentire a tutte le app associate di accedere alla chiave privata del certificato.  Per altre informazioni su questa impostazione, vedere questo documento di Apple: https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>Credenziali derivate per il provisioning di dispositivi mobili iOS con certificati<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune supporta l'uso di [credenziali derivate](../protect/derived-credentials.md) come metodo di autenticazione e per la firma e la crittografia S/MIME per i dispositivi iOS. Le credenziali derivate sono un'implementazione dello standard *NIST (National Institute of Standards and Technology) 800-157* per la distribuzione dei certificati nei dispositivi.  

Le credenziali derivate si basano sull'uso della verifica dell'identità personale (PIV) o di una scheda (CAC, Common Access Card), ad esempio una smart card. Per ottenere le credenziali derivate per il dispositivo mobile, gli utenti partono dall'app Portale aziendale e seguono un flusso di lavoro di registrazione specifico per il provider usato.  È comune a tutti i provider la necessità di usare una smart card in un computer per l'autenticazione presso il provider delle credenziali derivate. Il provider rilascia quindi un certificato al dispositivo derivato dalla smart card dell'utente.  

Intune supporta i provider di credenziali derivate seguenti:
- DISA Purebred
- Entrust Datacard
- Intercede

Usare le credenziali derivate come metodo di autenticazione per i profili di configurazione dei dispositivi per VPN, Wi-Fi e posta elettronica. È anche possibile usarle per l'autenticazione delle app e per la firma e la crittografia S/MIME.  

Per altre informazioni sullo standard, vedere [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) (Credenziali PIV derivate) nel sito www.nccoe.nist.gov.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Usare API Graph per specificare un nome dell'entità utente locale come variabile per i certificati SCEP<!--  5437939        -->  
Quando si usa l'[API Graph di Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0), è possibile specificare onPremisesUserPrincipalName come variabile per il nome alternativo del soggetto (SAN) per i certificati SCEP.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>Settimana del 23 settembre 2019

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>Registrazione utenti iOS in anteprima<!-- 4817900 -->
La versione di Apple iOS 13.1 include la registrazione utenti, un nuovo modulo di gestione semplificata per i dispositivi iOS. Può essere usato al posto della registrazione dei dispositivi o della registrazione automatica dei dispositivi (in precedenza Device Enrollment Program) per i dispositivi di proprietà personale. L'anteprima di Intune supporta questo set di funzionalità consentendo di:

- Riservare la registrazione utenti ai gruppi di utenti.
- Offrire agli utenti finali la possibilità di scegliere tra la registrazione utenti semplificata o la registrazione dei dispositivi avanzata quando registrano i loro dispositivi.

A partire dal 24/9/2019, con il rilascio di iOS 13.1, il processo di implementazione di questi aggiornamenti è in corso per tutti gli utenti e dovrebbe essere completato entro la fine della settimana prossima.

Si applica a:

- iOS 13.1 e versioni successive

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>Supporto di Intune per dispositivi iPadOS e iOS 13.1<!--5439574-->
Attualmente Intune supporta la gestione dei dispositivi sia iPadOS che iOS 13.1. Per altre informazioni, vedere [questo post di blog](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094).

<!-- ########################## -->

## <a name="week-of-september-16-2019-1909-service-release"></a>Settimana del 16 settembre 2019 (versione del servizio 1909)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>Gestione delle app 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>App line-of-business private in Google Play gestito<!-- 1464182  -->
Intune consente ora agli amministratori IT di pubblicare app line-of-business Android private in Google Play gestito tramite un iFrame incorporato nella console di Intune.  In precedenza gli amministratori IT dovevano pubblicare le app line-of-business direttamente nella console di pubblicazione di Google Play, operazione che richiedeva diversi passaggi ed era molto dispendiosa in termini di tempo. Questa nuova funzionalità consente di pubblicare facilmente app line-of-business con una serie di passaggi minimi, senza dover lasciare la console di Intune.  Gli amministratori non dovranno più eseguire manualmente la registrazione come sviluppatori in Google e pagare i 25 dollari di registrazione.  Tutti gli scenari di gestione con Android Enterprise che usano Google Play gestito possono trarre vantaggio da questa funzionalità: dispositivi con profilo di lavoro, dedicati, completamente gestiti e non registrati. Da Intune, selezionare **App client** > **App** > **Aggiungi**. Selezionare quindi **Google Play gestito** dall'elenco **Tipo di app**. Per altre informazioni su Google Play gestito vedere [Aggiungere app di Google Play gestito a dispositivi Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Uso del Portale aziendale Windows<!-- 1473353, 3598357 -->
Il Portale aziendale Windows è in fase di aggiornamento. Al suo interno sarà possibile usare più filtri nella pagina delle app. Anche la pagina dei dettagli dei dispositivi è in fase di aggiornamento con un'esperienza utente migliorata. Il processo di implementazione di questi aggiornamenti è attualmente in corso per tutti gli utenti e dovrebbe essere completato entro la fine della settimana prossima.

#### <a name="macos-support-for-web-apps---3174427---"></a>Supporto macOS per le app Web<!-- 3174427 -->
Le app Web, che consentono di aggiungere un collegamento a un URL sul Web, possono essere installate nel Dock usando il portale aziendale macOS. Gli utenti finali possono accedere all'azione **Installa** dalla pagina dei dettagli delle app Web nel Portale aziendale macOS. Per altre informazioni sul tipo di app **Collegamento Web**, vedere [Aggiungere app in Microsoft Intune](../apps/apps-add.md) e [Aggiungere app Web a Microsoft Intune](../apps/web-app.md).

#### <a name="macos-support-for-vpp-apps---3173501----"></a>Supporto macOS per app VPP<!-- 3173501  -->
Le app macOS, acquistate con Apple Business Manager, vengono visualizzate nella console quando vengono sincronizzati i token VPP Apple in Intune. È possibile assegnare, revocare e riassegnare le licenze basate su utenti e dispositivi per i gruppi usando la console di Intune. Microsoft Intune consente di gestire le app VPP acquistate per l'uso aziendale eseguendo le operazioni seguenti:

- Segnalazione delle informazioni di licenza dall'App Store.
- Verifica del numero di licenze usate.
- Blocco dell'installazione di un numero di copie dell'app superiore al numero di copie acquistate.

Per altre informazioni su Intune e VPP, vedere [Gestire le app e i libri acquistati con Volume Purchase Program con Microsoft Intune](../apps/vpp-apps.md).

#### <a name="managed-google-play-iframe-support---2871756----"></a>Supporto dell'iFrame di Google Play gestito<!-- 2871756  -->
Intune offre ora il supporto per l'aggiunta e la gestione di collegamenti Web direttamente nella console di Intune tramite l'iFrame di Google Play gestito.  In questo modo gli amministratori IT possono inviare un URL e una grafica di icona e quindi distribuire i collegamenti ai dispositivi come le normali app Android. Tutti gli scenari di gestione con Android Enterprise che usano Google Play gestito possono trarre vantaggio da questa funzionalità: dispositivi con profilo di lavoro, dedicati, completamente gestiti e non registrati. Da Intune, selezionare **App client** > **App** > **Aggiungi**. Selezionare quindi **Google Play gestito** dall'elenco **Tipo di app**. Per altre informazioni su Google Play gestito vedere [Aggiungere app di Google Play gestito a dispositivi Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Installare automaticamente app line-of-business Android in dispositivi Zebra<!-- 4252734  -->
Quando si installano app line-of-business Android in [dispositivi Zebra](../configuration/android-zebra-mx-overview.md) invece di richiedere di scaricare e installare l'app line-of-business, il sistema consente di installarle automaticamente. In Intune selezionare **App client** > **App** > **Aggiungi**. Nel riquadro **Aggiungi app** selezionare **App line-of-business**. Per altre informazioni vedere [Aggiungere un'app line-of-business Android a Microsoft Intune](../apps/lob-apps-android.md).

Attualmente, dopo il download dell'app line-of-business, viene visualizzata sul dispositivo dell'utente una notifica di **download completato**. La notifica può essere eliminata solo toccando **Deseleziona tutto** nella sfumatura della notifica. Questo problema di notifica verrà risolto in una versione successiva e l'installazione sarà completamente automatica, senza indicatori visivi.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Operazioni di lettura e scrittura API Graph per app di Intune<!-- 5031704  -->
Le applicazioni possono chiamare le API Graph di Intune con operazioni di lettura e scrittura usando l'identità dell'app senza le credenziali utente. Per altre informazioni sull'accesso all'API Microsoft Graph per Intune, vedere [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) (Usare Intune in Microsoft Graph).

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>Condivisione e crittografia dei dati protetti per Intune App SDK per iOS<!-- 3586942  -->
Intune App SDK per iOS userà le chiavi di crittografia a 256 bit quando la crittografia è abilitata dai criteri di protezione delle app. Tutte le app dovranno avere un SDK versione 8.1.1 per consentire la condivisione protetta dei dati.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>Supporto per i profili VPN IKEv2 per iOS<!-- 1943438   -->
In questo aggiornamento è possibile creare profili VPN per il client VPN nativo di iOS tramite il protocollo IKEv2. IKEv2 è un nuovo tipo di connessione in **Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS**  per la piattaforma > **VPN** per il tipo di profilo > **Tipo di connessione**.

Questi profili VPN configurano il client VPN nativo, quindi nei dispositivi gestiti non viene installata alcuna app client VPN e non ne viene eseguito il push. Questa funzionalità richiede che i dispositivi siano registrati in Intune (registrazione MDM).

Per visualizzare le impostazioni VPN correnti che è possibile configurare, vedere [Configurare le impostazioni VPN nei dispositivi iOS in Microsoft Intune](../configuration/vpn-settings-ios.md).

Si applica a:

- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>Le funzionalità e le restrizioni dei dispositivi e i profili di estensione per le impostazioni di iOS e macOS vengono visualizzate per tipo di registrazione<!-- 4886161   -->

In Intune è possibile creare profili per dispositivi iOS e macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Funzionalità del dispositivo**, **Limitazioni del dispositivo**, o **Estensioni** per il tipo di profilo). 

In questo aggiornamento le impostazioni disponibili nel portale di Intune sono classificate in base al tipo di registrazione a cui si applicano:

- iOS
  - Registrazione utenti
  - Registrazione del dispositivo
  - Registrazione automatica dei dispositivi (supervisione)
  - Tutti i tipi di registrazione

- macOS
  - Approvata da utente
  - Registrazione del dispositivo
  - Registrazione automatica dei dispositivi
  - Tutti i tipi di registrazione

Si applica a:

- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>Nuove impostazioni di controllo vocale per i dispositivi iOS con supervisione in esecuzione in modalità tutto schermo<!-- 4892835   -->
In Intune è possibile creare criteri per l'esecuzione di dispositivi iOS supervisionati in modalità tutto schermo o dispositivo dedicato (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Modalità tutto schermo**).

In questo aggiornamento sono disponibili nuove impostazioni che è possibile controllare:
- **Controllo vocale**: abilita il controllo vocale nel dispositivo in modalità tutto schermo.
- **Modifica del controllo vocale**: consente agli utenti di modificare l'impostazione del controllo vocale nel dispositivo in modalità tutto schermo.

Per visualizzare le impostazioni correnti, vedere le [impostazioni iOS in modalità tutto schermo](../configuration/device-restrictions-ios.md#kiosk).

Si applica a:

- iOS 13.0 e versioni successive

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>Usare Single Sign-On per app e siti Web nei dispositivi iOS e macOS<!-- 4893175   -->
In questo aggiornamento sono presenti nuove impostazioni Single Sign-On per dispositivi iOS e macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo).

Usare queste impostazioni per configurare Single Sign-On, in particolare per le app e i siti Web che usano l'autenticazione Kerberos. È possibile scegliere tra un'estensione dell'app Single Sign-On con credenziali generiche e un'estensione Kerberos predefinita di Apple.

Per visualizzare le funzionalità del dispositivo correnti che è possibile configurare, passare a [Funzionalità dei dispositivi iOS](../configuration/ios-device-features-settings.md) e [Funzionalità dei dispositivi macOS](../configuration/macos-device-features-settings.md).

Si applica a:

- iOS 13.0 e versioni successive
- macOS 10.15 e versioni successive

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>Associare i domini alle app nei dispositivi macOS 10.15 o versione successiva<!-- 4898079   -->
Nei dispositivi macOS è possibile configurare funzionalità diverse ed effettuare il push di queste funzionalità nei dispositivi usando criteri (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). In questo aggiornamento è possibile associare i domini alle app. Questa funzionalità consente di condividere le credenziali con i siti Web correlati all'app e può essere usata con l'estensione Single Sign-On di Apple, i collegamenti universali e il riempimento automatico delle password. 

Per visualizzare le funzionalità correnti che è possibile configurare passare alle [impostazioni delle funzionalità dei dispositivi macOS in Intune](../configuration/macos-device-features-settings.md).

Si applica a:

- macOS 10.15 e versioni successive

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>Usare "iTunes" e "apps" nell'URL dell'App Store di iTunes quando si visualizzano o nascondono le app nei dispositivi iOS con supervisione<!-- 4928474   --> 
In Intune è possibile creare criteri per visualizzare o nascondere le app nei dispositivi iOS supervisionati (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Mostra o nascondi le app**). 

È possibile immettere l'URL dell'App Store di iTunes, ad esempio `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`. In questo aggiornamento è possibile usare sia `apps` che `itunes` nell'URL, ad esempio:
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

Per altre informazioni su queste impostazioni vedere [Visualizzare o nascondere le app](../configuration/device-restrictions-ios.md#show-or-hide-apps).

Si applica a:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>I valori di tipo password dei criteri di conformità di Windows 10 sono più chiari e corrispondono a CSP<!-- 5138985 -->
Nei dispositivi Windows 10 è possibile creare criteri di conformità che richiedono funzionalità specifiche per le password (**Configurazione del dispositivo** > **Criteri** > **Crea criterio** > **Windows 10 e versioni successive** per la piattaforma > **Sicurezza del sistema**). In questo aggiornamento:
- I valori **Tipo di password** sono più chiari e aggiornati in modo da corrispondere ai [criteri CSP DeviceLock/AlphanumericDevicePasswordRequired](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired).
- L'impostazione **Scadenza password (giorni)**  è stata aggiornata per consentire i valori da 1 a 730 giorni. 

Per altre informazioni sulle impostazioni di conformità di Windows 10, vedere [Impostazioni di Windows 10 e versioni successive per contrassegnare un dispositivo come conforme o non conforme](../protect/compliance-policy-create-windows.md). 

Si applica a:
- Windows 10 e versioni successive

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Interfaccia utente aggiornata per la configurazione dell'accesso locale a Microsoft Exchange<!-- 4092920 -->  
È stata aggiornata la console in cui si [esegue la configurazione per l'accesso locale a Microsoft Exchange](../protect/conditional-access-exchange-create.md). Tutte le configurazioni per l'accesso locale a Exchange sono ora disponibili nello stesso riquadro della console in cui *viene abilitato il controllo dell'accesso locale a Exchange*.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Consentire o limitare l'aggiunta di widget di app alla schermata iniziale nei dispositivi del profilo di lavoro Android Enterprise<!-- 1109650  --> 
Nei dispositivi Android Enterprise è possibile configurare le funzionalità nel profilo di lavoro (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo profilo di lavoro > Limitazioni del dispositivo** per il tipo di profilo). In questo aggiornamento è possibile consentire agli utenti di aggiungere widget esposti dalle app del profilo di lavoro alla schermata iniziale del dispositivo.

Per visualizzare tutte le impostazioni configurabili, vedere [Impostazioni dei dispositivi Android Enterprise per consentire o limitare funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md).

Si applica a:
- Profilo di lavoro di Android Enterprise

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Per impostazione predefinita i nuovi tenant non vengono gestiti dagli amministratori dei dispositivi Android<!-- 4869790   -->
Le funzionalità di amministratore dei dispositivi Android sono state sostituite da Android Enterprise. È quindi consigliabile usare Android Enterprise per le nuove registrazioni. In un aggiornamento futuro i nuovi tenant dovranno completare la procedura seguente come prerequisito per la registrazione in Android perché i dispositivi siano gestiti dagli amministratori: Accedere a **Intune** > **Registrazione dispositivi** > **Registrazione Android** > **Dispositivi personali e di proprietà aziendale con privilegi di amministratore di dispositivi** > **Usa l'amministratore di dispositivi per gestire i dispositivi**.

Gli ambienti dei tenant esistenti non subiranno alcuna modifica.

Per altre informazioni sull'amministratore di dispositivi Android in Intune, vedere [Registrazione di tipo amministratore di dispositivi Android](https://docs.microsoft.com/intune/android-enroll-device-administrator).

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>Elenco di dispositivi DEP associati a un profilo<!-- 5012045 idmiss -->
È ora possibile visualizzare un elenco di pagine di dispositivi Apple Device Enrollment Program (DEP) associati a un profilo. È possibile eseguire ricerche nell'elenco da qualsiasi pagina. Per visualizzare l'elenco, passare a **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token > **Profili** > scegliere un profilo > **Dispositivi assegnati** (in **Monitoraggio**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>Supporto aumentato per dispositivi Android completamente gestiti<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
È stato aggiunto il supporto seguente per i dispositivi Android completamente gestiti:

- I certificati SCEP per dispositivi Android completamente gestiti sono disponibili per l'autenticazione del certificato nei dispositivi gestiti come proprietario del dispositivo. I certificati SCEP sono già supportati nei dispositivi del profilo di lavoro.  Con i certificati SCEP per il proprietario del dispositivo, è possibile: <!-- 5227935 -->
    - creare il profilo SCEP nella sezione Proprietario dispositivo di Android Enterprise
    - collegare i certificati SCEP al profilo Wi-Fi Proprietario dispositivo per l'autenticazione
    - collegare i certificati SCEP ai profili VPN Proprietario dispositivo per l'autenticazione
    - collegare i certificati SCEP ai profili di posta elettronica Proprietario dispositivo per l'autenticazione (tramite AppConfig)
- Le app di sistema sono supportate nei dispositivi Android Enterprise. In Intune aggiungere un'app di sistema Android Enterprise selezionando **App client** > **App** > **Aggiungi**. Nell'elenco **Tipo di app** selezionare **App del sistema Android Enterprise**. Per altre informazioni, vedere [Aggiungere app di sistema Android Enterprise a Microsoft Intune](../apps/apps-ae-system.md). <!-- 4062195 -->
- In **Conformità del dispositivo** > **Android Enterprise** > **Proprietario dispositivo** è possibile creare criteri di conformità che impostino il livello di attestazione Google SafetyNet.   <!-- 4631425 -->
- Nei dispositivi Android Enterprise completamente gestiti sono supportati i provider Mobile Threat Defense. In **Conformità del dispositivo** > **Android Enterprise** > **Proprietario dispositivo** è possibile scegliere un livello di minaccia accettabile. <!-- 4631440 --> [Impostazioni di Android Enterprise per contrassegnare un dispositivo come conforme o non conforme in Intune](../protect/compliance-policy-create-android-for-work.md#device-owner) elenca le impostazioni attuali.
- Nei dispositivi Android Enterprise completamente gestiti l'app Microsoft Launcher può ora essere configurata tramite i criteri di configurazione delle app per consentire un'esperienza utente finale standardizzata nel dispositivo completamente gestito. L'app Microsoft Launcher può essere usata per personalizzare il dispositivo Android. Usando l'app insieme con un account Microsoft oppure con un account aziendale o dell'istituto di istruzione, è possibile accedere al calendario, ai documenti e alle attività recenti nel feed personalizzato. <!-- 5334044 -->

Con questo aggiornamento il supporto di Intune per i dispositivi Android Enterprise completamente gestiti è ora disponibile a livello generale.

Si applica a:

- Dispositivi completamente gestiti Android Enterprise

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>Inviare notifiche personalizzate a un singolo dispositivo<!-- 4928910 -->
È ora possibile selezionare un singolo dispositivo e quindi usare un'azione del dispositivo remoto per [inviare una notifica personalizzata solo a quel dispositivo](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>Non sono disponibili le azioni di cancellazione e reimpostazione passcode per i dispositivi iOS registrati tramite la registrazione utente<!-- 4950491 -->
La registrazione utente è un nuovo tipo di registrazione dei dispositivi Apple. Quando si registrano i dispositivi con la registrazione utente, le azioni remote di cancellazione e reimpostazione del passcode non sono disponibili per tali dispositivi.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>Supporto di Intune per i dispositivi iOS 13 e macOS Catalina<!-- 4665317 -->
Intune ora supporta la gestione di dispositivi iOS 13 e macOS Catalina.
Per altre informazioni vedere il [post del blog sul supporto di Microsoft Intune per iOS 13 e iPadOS](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>Supporto di BitLocker per la rotazione delle password di ripristino basata su client<!--  3444125 -->
Usare le impostazioni di Endpoint Protection di Intune per configurare la [rotazione delle password di ripristino basata su client](../protect/endpoint-protection-windows-10.md#windows-encryption) per BitLocker nei dispositivi che eseguono Windows versione 1909 o successiva.

Questa impostazione avvia l'aggiornamento delle password di ripristino basate su client dopo il ripristino di un'unità del sistema operativo, eseguito con bootmgr o WinRE, e lo sblocco delle password di ripristino in un'unità dati fissa. Questa impostazione consente di aggiornare la password di ripristino specifica che è stata usata mentre le altre password inutilizzate nel volume rimangono invariate. Per altre informazioni vedere la documentazione di BitLocker CSP per [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Protezione antimanomissione per Windows Defender Antivirus<!-- 4705448        -->
Usare Intune per gestire la *protezione antimanomissione* per Windows Defender Antivirus. Quando si usano i profili di configurazione dei dispositivi per Windows 10 Endpoint Protection, è possibile trovare l'[impostazione per la protezione antimanomissione](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center) nel gruppo Microsoft Defender Security Center. È possibile impostare la protezione antimanomissione su *Attivata* per attivare le limitazioni per la protezione antimanomissione, impostare *Disabilitata* per disabilitarle o impostare *Non configurate* per lasciare la configurazione corrente dei dispositivi.  

Per altre informazioni sulla protezione antimanomissione [Bloccare le modifiche alle impostazioni di sicurezza con la protezione antimanomissione](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) nella documentazione di Windows.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Impostazioni avanzate per Windows Defender Firewall ora disponibili a livello generale<!--  5317392       -->  
Le [regole del firewall personalizzate per Windows Defender per Endpoint Protection](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices), che è possibile configurare come parte di un profilo di configurazione del dispositivo, ora sono disponibili in anteprima pubblica e a livello generale.  È possibile usare tali regole per specificare il comportamento in entrata e in uscita di applicazioni, indirizzi di rete e porte. Queste regole sono state rilasciate a luglio come anteprima pubblica. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>I tag di ambito ora supportano i criteri delle condizioni per l'utilizzo<!-- 2358863 idmiss -->
È ora possibile assegnare i [tag di ambito](scope-tags.md) ai criteri delle condizioni per l'utilizzo. A tale scopo, passare a **Intune** > **Registrazione del dispositivo** > **Termini e condizioni** > scegliere una voce nell'elenco > **Proprietà** > **Tag di ambito** > scegliere un tag di ambito.

## <a name="week-of-september-9-2019"></a>Settimana del 9 settembre 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Aggiornamenti all'app Microsoft Intune<!-- 4997846 -->
L'app Microsoft Intune per Android è stata aggiornata con i miglioramenti seguenti:
- Il layout è stato aggiornato e migliorato per includere lo spostamento inferiore per le azioni più importanti.
- È stata aggiunta un'altra pagina per il profilo dell'utente.
- È stata aggiunta la visualizzazione delle notifiche interattive nell'app per l'utente, ad esempio la necessità di aggiornare le impostazioni del dispositivo.
- È stata aggiunta la visualizzazione di notifiche push personalizzate, allineando l'app al supporto aggiunto di recente nell'app Portale aziendale per iOS e Android. Per altre informazioni, vedere [Inviare notifiche personalizzate in Intune](../remote-actions/custom-notifications.md).

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>Per i dispositivi iOS, personalizzare la schermata relativa alla privacy del processo di registrazione del portale aziendale<!-- 4394993 -->
Usando Markdown è possibile personalizzare la schermata relativa alla privacy del portale aziendale visualizzata dagli utenti finali durante la registrazione iOS. In particolare, è possibile personalizzare l'elenco di elementi che l'organizzazione non può visualizzare o eseguire sul dispositivo. Per altre informazioni, vedere [Come configurare l'app Portale aziendale Intune](../apps/company-portal-app.md#privacy-statement-customization).


## <a name="week-of-september-2-2019"></a>Settimana del 2 settembre 2019

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Aggiornamento dell'interfaccia utente di Intune: dashboard Stato del tenant<!-- 5273210  -->
È stata aggiornata l'interfaccia utente per il dashboard Stato del tenant per allinearsi agli stili dell'interfaccia utente di Azure. Per altre informazioni, vedere [Stato tenant](../tenant-status.md).

## <a name="week-of-august-26-2019"></a>Settimana del 26 agosto 2019

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Configurare le impostazioni di Microsoft Edge usando i modelli amministrativi per Windows 10 e versioni successive<!-- 5228061 -->

Nei dispositivi Windows 10 e versioni successive è possibile creare modelli amministrativi per configurare le impostazioni di Criteri di gruppo in Intune. In questo aggiornamento è possibile configurare le impostazioni che si applicano a Microsoft Edge versione 77 e successive.

Per altre informazioni sui modelli amministrativi, vedere [Usare i modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune](../configuration/administrative-templates-windows.md).

Si applica a:

- Windows 10 e versioni successive (Windows RS4+)

## <a name="week-of-august-12-2019-1908-service-release"></a>Settimana del 12 agosto 2019 (versione del servizio 1908)

### <a name="app-management"></a>Gestione delle app

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>Controllare il comportamento di disinstallazione delle app iOS durante l'annullamento della registrazione del dispositivo<!-- 3504144   -->
Gli amministratori possono gestire la rimozione o il mantenimento di un'app in un dispositivo quando viene annullata la registrazione del dispositivo a livello di utente o di gruppo di dispositivi. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>Categorizzare le app di Microsoft Store per le aziende<!-- 3926922 -->
È possibile categorizzare le app di Microsoft Store per le aziende. A tale scopo, scegliere **app** > c**lient** diIntune > **app**>selezionareun'appMicrosoftStoreforbusinessapp> **Categoria** > **informazioni**. Nel menu a discesa assegnare una categoria.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Notifiche personalizzate per gli utenti dell'app Microsoft Intune<!-- 4843354  -->
L'app Microsoft Intune per Android supporta ora la visualizzazione di notifiche push personalizzate, in linea con il supporto aggiunto di recente nelle app Portale aziendale per iOS e Android. Per altre informazioni, vedere [Inviare notifiche personalizzate in Intune](../remote-actions/custom-notifications.md).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>Nuove funzionalità per dispositivi Android Enterprise dedicati in modalità per più app<!-- 3755304 3041943 3041946   -->

In Intune è possibile controllare le funzionalità e le impostazioni in un'esperienza di tipo chiosco multimediale per i dispositivi dedicati Android Enterprise (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **Solo proprietario del dispositivo, Limitazioni del dispositivo** per il tipo di profilo).

In questo aggiornamento sono state aggiunte le funzionalità seguenti:

- **Dispositivi dedicati** > **Più app**: è possibile visualizzare il **pulsante Pagina iniziale virtuale** scorrendo verso l'alto nel dispositivo oppure rendendolo mobile sullo schermo in modo che gli utenti possano spostarlo.
- **Dispositivi dedicati** > **Più app**: **Accesso a Flashlight** consente agli utenti di usare la torcia. 
- **Dispositivi dedicati** > **Più app**: **Controllo volume dei file multimediali** consente agli utenti di controllare il volume dei file multimediali del dispositivo usando un dispositivo di scorrimento. 
- **Dispositivi dedicati** > **Più app**:  **Abilitare uno screen saver**, caricare un'immagine personalizzata e controllare quando viene visualizzato lo screen saver.

Per visualizzare le impostazioni correnti, passare alle [impostazioni dei dispositivi Android Enterprise per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings).

Si applica a:

- Dispositivi dedicati Android Enterprise

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Nuovi profili di app e configurazione per i dispositivi Android Enterprise completamente gestiti<!-- 3574215 3574238 3574235 3574232   -->
Usando i profili è possibile configurare le impostazioni che applicano le impostazioni per VPN, posta elettronica e Wi-Fi ai dispositivi (completamenti gestiti) del proprietario del dispositivo Android Enterprise. In questo aggiornamento è possibile:

- Usare i [criteri di configurazione delle app](../apps/app-configuration-policies-use-android.md) per distribuire le impostazioni di posta elettronica di Outlook, Gmail e Nine Work.
- Usare i profili di configurazione dei dispositivi per distribuire le [impostazioni dei certificati radice trusted](../protect/certificates-configure.md).
- Usare i profili di configurazione dei dispositivi per distribuire le impostazioni [VPN](../configuration/vpn-settings-android-enterprise.md) e [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md).

> [!IMPORTANT]
> Con questa funzionalità gli utenti eseguono l'autenticazione con il nome utente e la password per i profili VPN, Wi-Fi e di posta elettronica. Attualmente, l'autenticazione basata sui certificati non è disponibile.

Si applica a:  
- Proprietario del dispositivo Android Enterprise (completamente gestito)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>Controllare le app, i file, i documenti e le cartelle che si aprono quando gli utenti accedono ai dispositivi macOS<!--3914202   -->
È possibile abilitare e configurare le funzionalità per i dispositivi macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Funzionalità del dispositivo** per il tipo di profilo). 

In questo aggiornamento è disponibile una nuova impostazione Elementi di accesso per controllare quali app, file, documenti e cartelle si aprono quando un utente accede al dispositivo registrato. 

Per visualizzare le impostazioni correnti, passare alle [impostazioni delle funzionalità dei dispositivi macOS in Intune](../configuration/macos-device-features-settings.md).

Si applica a:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Le scadenze sostituiscono le impostazioni di riavvio in caso di occupato per gli anelli di Windows Update<!-- 4464404        -->
Per allinearsi alle recenti [modifiche per la manutenzione di Windows](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing), gli anelli di Windows 10 Update di Intune [supportano ora impostazioni per le scadenze](../protect/windows-update-settings.md). Le *scadenze* determinano quando un dispositivo installa gli aggiornamenti della funzionalità e della sicurezza.  Nei dispositivi che eseguono Windows 10 1903 o versioni successive, le *scadenze* sostituiscono le configurazioni per il *riavvio in caso di occupato*.  In futuro, le *scadenze* sostituiranno il *riavvio in caso di occupato* anche nelle versioni precedenti di Windows 10.  

Quando non si configurano le *scadenze*, i dispositivi continuano a usare le impostazioni di *riavvio in caso di occupato*. Tuttavia, in Intune il supporto per le impostazioni di riavvio in caso di occupato saranno deprecate in un aggiornamento futuro.  

Pianificare l'uso delle *scadenze* per tutti i dispositivi Windows 10. Dopo aver applicato le impostazioni per le *scadenze*, è possibile modificare le configurazioni di Intune per il *riavvio in caso di occupato* su Non configurato. Con l'impostazione Non configurato Intune interrompe la gestione di tali impostazioni nei dispositivi, ma non rimuove le ultime configurazioni per l'impostazione dal dispositivo. Pertanto, le ultime configurazioni impostate per il *riavvio in caso di occupato* rimangono attive e in uso nei dispositivi fino a quando tali impostazioni non vengono modificate da un metodo diverso da Intune. In seguito, in caso di modifiche alla versione di Windows dei dispositivi o quando il supporto delle *scadenze* di Intune verrà esteso alla versione di Windows dei dispositivi, il dispositivo inizierà a usare le nuove impostazioni che sono già presenti.

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>Supporto per più connettori di certificati di Microsoft Intune<!--   4704642      -->
Intune supporta ora l'installazione e l'uso di più [connettori di certificati di Microsoft Intune per le operazioni PKCS](../protect/certficates-pfx-configure.md). Questa modifica supporta il bilanciamento del carico e la disponibilità elevata del connettore. Ogni istanza del connettore può elaborare le richieste di certificati da Intune.  Se un connettore non è disponibile, gli altri connettori continuano a elaborare le richieste.

Per usare più connettori, non è necessario eseguire l'aggiornamento alla versione più recente del software del connettore.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>Nuove impostazioni e modifiche alle impostazioni esistenti per limitare le funzionalità nei dispositivi iOS e macOS<!-- 4867699 4867709   -->
È possibile creare profili per limitare le impostazioni nei dispositivi che eseguono iOS e macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Limitazioni del dispositivo**). Questo aggiornamento include le funzionalità seguenti:

- In **macOS** > **Limitazioni del dispositivo** > **Cloud e risorse di archiviazione** usare la nuova impostazione **Handoff** per impedire agli utenti di iniziare a lavorare su un dispositivo macOS e continuare a usare un altro dispositivo macOS o iOS.

  Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-macos.md).

- In **iOS** > **Limitazioni del dispositivo** sono presenti alcune modifiche:

  - **App predefinite** > **Trova il mio iPhone (solo con supervisione)** : nuova impostazione che blocca questa funzionalità nella funzionalità dell'app Trova il mio. 
  - **App predefinite** > **Trova amici (solo con supervisione)** : nuova impostazione che blocca questa funzionalità nella funzionalità dell'app Trova il mio. 
  - **Wireless** > **Modifica dello stato del Wi-Fi (solo con supervisione)** : nuova impostazione che impedisce agli utenti di attivare o disattivare il Wi-Fi nel dispositivo.
  - **Tastiera e dizionario** > **QuickPath (solo con supervisione)** : nuova impostazione che blocca la funzionalità QuickPath.
  - **Cloud e risorse di archiviazione**: l'impostazione **Continuazione dell'attività** è stata rinominata **Handoff**.

  Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:  
- macOS 10.15 e versioni successive
- iOS 13 e versioni successive

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>Alcune limitazioni per i dispositivi iOS senza supervisione diventeranno solo con supervisione con la versione iOS 13.0<!-- 4867809   -->
In questo aggiornamento, alcune impostazioni si applicano ai dispositivi solo con supervisione con la versione iOS 13.0. Se queste impostazioni vengono configurate e assegnate a dispositivi senza supervisione prima della versione iOS 13.0, le impostazioni vengono comunque applicate a tali dispositivi senza supervisione. Sono comunque valide anche dopo l'aggiornamento dei dispositivi a iOS 13.0. Queste limitazioni vengono rimosse nei dispositivi senza supervisione di cui viene eseguito il backup e il ripristino.

Queste impostazioni includono:

- App Store, visualizzazione documenti, giochi
  - App Store
  - Musica di iTunes, podcast o notizie con contenuti espliciti
  - Aggiunta di amici al Game Center
  - Gioco multiplayer
- App predefinite
  - Fotocamera
    - FaceTime
  - Safari
    - Riempimento automatico
- Cloud e risorse di archiviazione
  - Backup in iCloud
  - Blocca la sincronizzazione dei documenti di iCloud
  - Blocca la sincronizzazione Keychain con iCloud

Per visualizzare le impostazioni correnti, vedere [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md).

Si applica a:  
- iOS 13.0 e versioni successive

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>Stato del dispositivo migliorato per la crittografia macOS FileVault<!-- 4944983         -->
Sono stati aggiornati diversi [messaggi di stato del dispositivo](../protect/encryption-monitor.md#device-encryption-status) per la crittografia FileVault nei dispositivi macOS.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>Alcune impostazioni di analisi di Windows Defender Antivirus nei report mostrano uno stato di errore<!-- 5119229 -->
In Intune è possibile creare criteri per usare Windows Defender Antivirus per analizzare i dispositivi Windows 10 (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Windows Defender Antivirus**). Le impostazioni di report **Ora di esecuzione di un'analisi veloce giornaliera** e **Tipo di analisi di sistema da eseguire** mostrano uno stato di errore, quando si tratta effettivamente di uno stato di operazione riuscita. 

Questo comportamento è stato corretto in questo aggiornamento. Le impostazioni di report **Ora di esecuzione di un'analisi veloce giornaliera** e **Tipo di analisi di sistema da eseguire** mostrano quindi uno stato di operazione riuscita quando le analisi vengono completate correttamente e uno stato di errore quando non è possibile applicare le impostazioni.

Per altre informazioni sulle impostazioni di Windows Defender Antivirus, vedere [Impostazioni dei dispositivi Windows 10 (e versioni successive) per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="default-scope-tags---3702875----"></a>Tag di ambito predefinito<!-- 3702875  -->
È ora disponibile un nuovo tag di ambito predefinito incorporato. A tutti gli oggetti di Intune senza tag che supportano i tag di ambito viene assegnato automaticamente il tag di ambito predefinito. Il tag di ambito **Predefinito** viene aggiunto a tutte le assegnazioni di ruolo esistenti per mantenere la parità con l'esperienza di amministrazione attuale. Se non si vuole che un amministratore visualizzi gli oggetti di Intune con il tag di ambito predefinito, rimuovere il tag di ambito predefinito dall'assegnazione di ruolo. Questa funzionalità è simile alla funzionalità degli ambiti di sicurezza di Configuration Manager. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito](scope-tags.md).

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Supporto per l'amministratore del dispositivo per la registrazione Android<!-- 4869749   -->
È stata aggiunta l'opzione per la registrazione dell'amministratore di dispositivi Android alla pagina di registrazione Android (**Intune** > **Registrazione del dispositivo** > **Registrazione Android**). L'amministratore del dispositivo Android sarà ancora abilitato per impostazione predefinita per tutti i tenant.  Per altre informazioni, vedere [Registrazione di tipo amministratore di dispositivi Android](../enrollment/android-enroll-device-administrator.md).

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>Ignorare altre schermate in Assistente configurazione <!--4877451  -->
È possibile impostare i profili DEP (Device Enrollment Program) in modo da ignorare le schermate di Assistente configurazione seguenti:
- Per iOS
    - Aspetto
    - Express Language (Lingua rapida)
    - Lingua preferita
    - Device to Device Migration (Migrazione da dispositivo a dispositivo)
- Per macOS
    - Orario schermo
    - Touch ID Setup (Configurazione ID tocco)

Per altre informazioni sulla personalizzazione di Assistente configurazione, vedere [Creare un profilo di registrazione di Apple per iOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile) e [Creare un profilo di registrazione di Apple per macOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile).

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Aggiungere una colonna utente al processo di caricamento CSV del dispositivo Autopilot<!-- 3823054 -->
È ora possibile aggiungere una colonna utente al caricamento CSV per i dispositivi Autopilot. Ciò consente di assegnare in blocco gli utenti al momento dell'importazione del file CSV. Per altre informazioni, vedere [Registrare dispositivi Windows in Intune con Windows Autopilot](../enrollment/enrollment-autopilot.md).


### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>Configurare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni<!--4231059  -->
È possibile impostare il limite di tempo di pulizia automatico del dispositivo fino a 30 giorni, anziché il limite precedente di 90 giorni, dall'ultimo accesso. A tale scopo, passare a **Intune** > **Dispositivi** > **Configurazione** > **Regole per la pulizia del dispositivo**.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Numero di build incluso nella pagina Hardware del dispositivo Android<!-- 4461910   -->
Una nuova voce nella pagina Hardware per ogni dispositivo Android include il numero di build del sistema operativo del dispositivo. Per altre informazioni, vedere [Visualizzare i dettagli del dispositivo in Intune](../remote-actions/device-inventory.md).


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>Settimana del 5 agosto 2019

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies è un OEM supportato per OEMConfig nei dispositivi Android Enterprise<!-- 4843713 -->

In Intune è possibile creare un profilo di configurazione del dispositivo e applicare le impostazioni ai dispositivi Android Enterprise usando OEMConfig (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **Android Enterprise** per la piattaforma > **OEMConfig** per il tipo di profilo).

In questo aggiornamento, Zebra Technologies è un OEM (Original Equipment Manufacturer) supportato per OEMConfig. Per altre informazioni su OEMConfig, vedere [Usare e gestire i dispositivi Android Enterprise con OEMConfig](../configuration/android-oem-configuration-overview.md).

Si applica a:  
- Android Enterprise

<!-- ########################## -->

## <a name="week-of-july-22-2019-1907-service-release"></a>Settimana del 22 luglio 2019 (versione del servizio 1907)

### <a name="app-management"></a>Gestione delle app

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>Notifiche personalizzate per utenti e gruppi<!-- 16766574          -->
È possibile inviare notifiche push personalizzate dall'applicazione Portale aziendale agli utenti di dispositivi iOS e Android gestiti con Intune. Queste notifiche push per dispositivi mobili sono personalizzabili con testo libero e possono essere usate per qualsiasi scopo. È possibile destinarle a diversi gruppi di utenti dell'organizzazione. Per altre informazioni, vedere l'argomento sulle [notifiche personalizzate](../remote-actions/custom-notifications.md).

#### <a name="googles-device-policy-controller-app---3041950----"></a>App controller delle norme relative ai dispositivi di Google<!-- 3041950  -->
L'app di schermata iniziale gestita ora consente l'accesso a Google Apps Device Policy per Android. L'app di schermata iniziale gestita è un'utilità di avvio personalizzata usata per i dispositivi registrati in Intune come dispositivi dedicati Android Enterprise (AE) che usano la modalità tutto schermo per più app. È possibile accedere all'app Android Device Policy o guidare gli utenti all'app Android Device Policy per fini di supporto e debug. Questa funzionalità di avvio è disponibile nel momento in cui il dispositivo viene registrato e bloccato nella schermata iniziale gestita. Per usare questa funzionalità non è necessaria alcuna installazione aggiuntiva.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>Impostazioni di protezione di Outlook per dispositivi iOS e Android<!-- 3212619 -->
È ora possibile configurare le impostazioni generali di configurazione dei dati e delle app per Outlook per iOS e Android usando i semplici controlli di amministrazione di Intune senza registrazione del dispositivo. Le impostazioni generali di configurazione delle app forniscono la parità con le impostazioni che gli amministratori possono abilitare in caso di gestione di Outlook per iOS e Android su dispositivi registrati. Per altre informazioni sulle impostazioni di Outlook, vedere [Deploying Outlook for iOS and Android app configuration settings](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) (Distribuzione di impostazioni di configurazione per Outlook per iOS e Android).

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready------"></a>Usare le "regole di applicabilità" durante la creazione dei profili di configurazione dispositivo Windows 10 <!-- 2549910 eeready    -->

È possibile creare profili di configurazione dispositivo Windows 10 (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **Windows 10** per la piattaforma > **Regole di applicabilità**). In questo aggiornamento è possibile creare una **regola di applicabilità** in modo che il profilo si applichi solo a un'edizione o versione specifica. Creare ad esempio un profilo che consente alcune impostazioni di BitLocker. Dopo aver aggiunto il profilo, usare una regola di applicabilità in modo che il profilo si applichi solo ai dispositivi che eseguono Windows 10 Enterprise.

Per aggiungere una regola di applicabilità, vedere l'[apposito argomento](../configuration/device-profile-create.md#applicability-rules).

Si applica a: Windows 10 e versioni successive

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>Usare i token per aggiungere informazioni specifiche del dispositivo nei profili personalizzati per i dispositivi iOS e macOS<!-- 3330008  -->
È possibile usare profili personalizzati nei dispositivi iOS e macOS per configurare le impostazioni e le funzionalità non predefinite in Intune (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS** o **macOS** per la piattaforma > **Personalizza** per il tipo di profilo). In questo aggiornamento è possibile aggiungere token ai file `.mobileconfig` per aggiungere informazioni specifiche del dispositivo. È ad esempio possibile aggiungere `Serial Number: {{serialnumber}}` al file di configurazione per mostrare il numero di serie del dispositivo.

Per creare un profilo personalizzato, vedere l'argomento relativo alle [impostazioni personalizzate per iOS ](../configuration/custom-settings-ios.md) o alle [impostazioni personalizzate per macOS](../configuration/custom-settings-macos.md).

Si applica a:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Nuova finestra di progettazione della configurazione quando si crea un profilo OEMConfig per Android Enterprise<!-- 3712769   -->
In Intune è possibile creare un profilo di configurazione dispositivo che usa un'app OEMConfig (Configurazione dispositivo > Profili > Crea profilo > Android Enterprise per la piattaforma > OEMConfig per il tipo di profilo). In tal caso, viene aperto un editor JSON con un modello e valori che è possibile modificare. 

Questo aggiornamento include una finestra di progettazione della configurazione con un'esperienza utente migliorata che mostra i dettagli incorporati nell'app, inclusi i titoli, le descrizioni e altro ancora. L'editor JSON è ancora disponibile e mostra tutte le modifiche apportate nella finestra di progettazione della configurazione.

Per visualizzare le impostazioni correnti, passare a [Use and manage Android Enterprise devices with OEMConfig](../configuration/android-oem-configuration-overview.md) (Usare e gestire dispositivi Android Enterprise con OEMConfig).

Si applica a: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Aggiornamento dell'interfaccia utente per la configurazione di Windows Hello<!-- 4089576            -->
È stata aggiornata la console in cui si [configura Intune per l'uso di Windows Hello for Business](../protect/windows-hello.md). Tutte le impostazioni di configurazione sono ora disponibili nello stesso riquadro della console in cui si abilita il supporto per Windows Hello.

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
Intune PowerShell SDK, che fornisce il supporto per l'API di Intune tramite Microsoft Graph, è stato aggiornato alla versione 6.1907.1.0. L'SDK supporta ora quanto segue:
- Automazione di Azure.
- Operazioni di lettura autenticazioni per sole app. 
- Nomi descrittivi abbreviati come alias.
- Convenzioni di denominazione di PowerShell. In particolare, il parametro `PSCredential` (nel cmdlet `Connect-MSGraph`) è stato rinominato in `Credential`.
- La specifica manuale del valore dell'intestazione `Content-Type` quando si usa il cmdlet `Invoke-MSGraphRequest`.

Per altre informazioni, vedere la pagina relativa a [PowerShell SDK per l'API Graph per Microsoft Intune](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune).


### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>Aggiornamenti per le restrizioni della registrazione<!-- 2871968 -->
Le restrizioni della registrazione per i nuovi tenant sono state aggiornate in modo che i profili di lavoro di Android Enterprise siano consentiti per impostazione predefinita. I tenant esistenti non subiscono alcuna modifica. Per usare i profili di lavoro di Android Enterprise, è comunque necessario [connettere l'account Intune all'account Google Play gestito](../enrollment/connect-intune-android-enterprise.md).

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Aggiornamenti dell'interfaccia utente per la registrazione Apple e le restrizioni della registrazione<!--4089575, 4089579  -->
Entrambi i processi seguenti usano un'interfaccia utente in stile procedura guidata:
- Registrazione di dispositivi Apple. Per altre informazioni, vedere [Registrare automaticamente i dispositivi iOS nel programma Device Enrollment Program di Apple](../enrollment/device-enrollment-program-enroll-ios.md).
- Creazione di restrizioni della registrazione. Per altre informazioni, vedere [Impostare le restrizioni di registrazione](../enrollment/enrollment-restrictions-set.md).

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Gestione della preconfigurazione degli identificatori dei dispositivi aziendali per i dispositivi Android Q<!-- 4711509  idmiss -->
In Android Q (versione 10) Google eliminerà la possibilità per gli agenti MDM nei dispositivi Android gestiti legacy (amministratore del dispositivo) di raccogliere informazioni sugli identificatori dei dispositivi.  Intune dispone di una funzionalità che consente agli amministratori IT di [preconfigurare un elenco di numeri di serie del dispositivo o IMEI](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number) per contrassegnare automaticamente tali dispositivi come di proprietà dell'azienda. Questa funzionalità non è supportata sui dispositivi Android Q gestiti dall'amministratore del dispositivo.  Indipendentemente dal fatto che venga caricato il numero di serie o IMEI per il dispositivo, la proprietà sarà sempre considerata come personale durante la registrazione di Intune.  È possibile impostare manualmente la proprietà come aziendale dopo la registrazione.  Ciò ha impatto solo sulle nuove registrazioni, non sui dispositivi registrati esistenti.  Tale modifica non ha impatto sui dispositivi Android gestiti con profili di lavoro, che continueranno a funzionare come di consueto.  I dispositivi Android Q registrati come amministratore del dispositivo non saranno inoltre più in grado di segnalare il numero di serie o IMEI nella console di Intune come proprietà del dispositivo.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Sono state modificate le icone per le registrazioni di Android Enterprise (profilo di lavoro, dispositivi dedicati e dispositivi completamente gestiti)<!-- 4977730 -->
Le icone per i profili di registrazione di Android Enterprise sono state modificate. Per visualizzare le nuove icone, andare a **Intune** > **Registrazione** > **Registrazione Android** > vedere in **Profili di registrazione**.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Modifica alla raccolta dei dati di diagnostica di Windows<!-- 4113859 -->
Il valore predefinito per la raccolta dei dati di diagnostica è stato modificato per i dispositivi che eseguono Windows 10, versione 1903 e successive. A partire da Windows 10, versione 1903, la raccolta dei dati di diagnostica è abilitata per impostazione predefinita. I dati di diagnostica di Windows sono dati tecnici essenziali dei dispositivi Windows relativi al dispositivo e alle prestazioni di Windows e del software correlato. Per altre informazioni, vedere [Configure Windows diagnostic data in your organization](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization) (Configurare i dati di diagnostica di Windows nell'organizzazione). Nei dispositivi Autopilot viene inoltre dato il consenso esplicito per la raccolta dei dati di telemetria "Full", a meno che non vengano impostati diversamente nel profilo di Autopilot con [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="improve-device-location---3855417----"></a>Migliorare l'individuazione del dispositivo<!-- 3855417  -->
È possibile fare lo zoom avanti sulle coordinate esatte di un dispositivo usando l'azione **Individua il dispositivo**. Per altre informazioni sull'individuazione dei dispositivi iOS persi, vedere [Individuare dispositivi iOS persi](../remote-actions/device-locate.md).

### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Impostazioni avanzate per Windows Defender Firewall (anteprima pubblica)<!--  1311949     -->  
È possibile usare Intune per gestire [regole del firewall personalizzate come parte di un profilo di configurazione del dispositivo](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) per Endpoint Protection in Windows 10. Le regole possono specificare il comportamento in entrata e in uscita di applicazioni, indirizzi di rete e porte. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>Aggiornamento dell'interfaccia utente per la gestione delle baseline di sicurezza<!-- 4091125     -->
È stata aggiornata l'[esperienza di creazione e modifica](../protect/security-baselines.md#create-the-profile) nella console di Intune per le baseline di sicurezza. Le modifiche includono:

Un formato più semplice in stile procedura guidata che è stato ridotto in un singolo pannello. all'interno di un pannello. Questo nuovo design non implica lo spostamento tra pannelli che richiede ai professionisti IT di eseguire il drill-down in diversi riquadri distinti.  
È ora possibile creare assegnazioni come parte dell'esperienza di creazione e modifica, anziché dover tornare in seguito per assegnare baseline. È stato aggiunto un riepilogo delle impostazioni che è possibile visualizzare prima di creare una nuova baseline e quando se ne modifica una esistente. Al momento della modifica, il riepilogo mostra solo l'elenco di elementi impostati all'interno di una categoria di proprietà da modificare.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>Settimana del 15 luglio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Icone dell'app di schermata iniziale gestita e impostazioni gestite<!-- 4918107 -->
L'icona dell'app di schermata iniziale gestita e l'icona di **impostazioni gestite** sono state aggiornate. L'app di schermata iniziale gestita è usata solo per i dispositivi registrati in Intune come dispositivi dedicati Android Enterprise (AE) eseguiti in modalità tutto schermo per più app. Per altre informazioni sull'app di schermata iniziale gestita, vedere [Configurare l'app Microsoft Managed Home Screen per Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Device Policy su dispositivi dedicati Android Enterprise<!-- 4918136 -->
È possibile accedere all'app Android Device Policy dalla schermata di debug dell'app di schermata iniziale gestita. L'app di schermata iniziale gestita è usata solo per i dispositivi registrati in Intune come dispositivi dedicati Android Enterprise (AE) eseguiti in modalità tutto schermo per più app. Per altre informazioni, vedere [Configurare l'app Microsoft Managed Home Screen per Android Enterprise](../apps/app-configuration-managed-home-screen-app.md).

#### <a name="ios-company-portal-updates---3902931---"></a>Aggiornamenti del Portale aziendale iOS<!-- 3902931 -->
Il nome della società nelle richieste di gestione delle app iOS sostituirà il testo "i.manage.microsoft.com" corrente. Gli utenti visualizzeranno ad esempio il nome della società anziché "i.manage.microsoft.com" quando tentano di installare un'app iOS da Portale aziendale o quando consentono la gestione dell'app. Questa funzionalità verrà implementata per tutti i clienti nei prossimi giorni.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>Gestire FileVault per macOS<!--  3858502 + 4557986 + 1210104  -->
È possibile usare Intune per [gestire la crittografia delle chiavi FileVault](../protect/encrypt-devices.md) per i dispositivi macOS. Per crittografare i dispositivi, usare un profilo di configurazione dei dispositivi di Endpoint Protection.

Il supporto per FileVault include la crittografia dei dispositivi non crittografati, il deposito di una chiave di ripristino personale dei dispositivi, la rotazione automatica o manuale delle chiavi di crittografia personali e il recupero delle chiavi per i dispositivi aziendali. Gli utenti finali possono anche usare il sito Web Portale aziendale per ottenere la chiave di ripristino personale per i dispositivi crittografati.

È stato inoltre espanso il report di crittografia per includere [informazioni su FileVault](../protect/encryption-monitor.md) e informazioni su BitLocker, in modo da poter visualizzare tutti i dettagli della crittografia dei dispositivi in un'unica posizione.

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>La reimpostazione di Windows Autopilot rimuove l'utente primario del dispositivo<!-- 4156123 -->
Quando si usa la reimpostazione di Autopilot in un dispositivo, l'utente primario del dispositivo viene rimosso. L'utente successivo che accede dopo la reimpostazione verrà impostato come utente primario. Questa funzionalità verrà implementata per tutti i clienti nei prossimi giorni.

## <a name="week-of-july-8-2019"></a>Settimana dell'8 luglio 2019

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Nuove impostazioni di Office, Windows e OneDrive nei modelli amministrativi di Windows 10 <!-- 3510695 -->

È possibile creare modelli amministrativi in Intune che simulano la gestione di Criteri di gruppo locali (**Gestione dispositivi** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Modello amministrativo** per il tipo di profilo).

Questo aggiornamento include altre impostazioni di Office, Windows e OneDrive che è possibile aggiungere ai modelli. Con queste nuove impostazioni è ora possibile configurare oltre 2500 impostazioni completamente basate sul cloud.

Per altre informazioni su questa funzionalità, vedere [Usare i modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Microsoft Intune](../configuration/administrative-templates-windows.md).

Si applica a: Windows 10 e versioni successive

## <a name="week-of-july-1-2019"></a>Settimana dell'1 luglio 2019 

### <a name="app-management"></a>Gestione delle app

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>AAD e APP in dispositivi Android Enterprise<!-- 3574267 -->
Quando si esegue l'onboarding di dispositivi Android Enterprise completamente gestiti, gli utenti si registrano ora con Azure Active Directory (AAD) al momento della configurazione iniziale del dispositivo nuovo o con ripristino delle impostazioni predefinite. In precedenza, per un dispositivo completamente gestito, al termine dell'installazione l'utente doveva avviare manualmente l'app Microsoft Intune per iniziare la registrazione di AAD. Attualmente, quando l'utente accede alla pagina iniziale del dispositivo dopo la configurazione iniziale, il dispositivo risulta iscritto e registrato.

Oltre agli aggiornamenti di AAD, nei dispositivi Android Enterprise completamente gestiti sono ora supportati anche i criteri di Protezione app di Intune. Questa funzionalità diventerà disponibile al momento della relativa implementazione. Per altre informazioni, vedere [Aggiungere app di Google Play gestite a dispositivi Android Enterprise con Intune](../apps/apps-add-android-for-work.md).

## <a name="week-of-june-24-2019-1906-service-release"></a>Settimana del 24 giugno 2019 (versione del servizio 1906)

### <a name="app-management"></a>Gestione delle app

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>Configurare il browser collegabile ai dati dell'organizzazione<!-- 3145939 -->
I criteri di Protezione app di Intune nei dispositivi Android e iOS consentono ora di trasferire i collegamenti Web dell'organizzazione in un browser specifico diverso da Intune Managed Browser o Microsoft Edge.  Per altre informazioni, vedere [Che cosa sono i criteri di protezione delle app?](../apps/app-protection-policy.md).

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>La pagina Tutte le app identifica le app di Microsoft Store per le aziende online/offline<!--4089647 -->
La pagina **Tutte le app** include ora l'assegnazione di etichette per identificare le app di Microsoft Store per le aziende come app online o offline. Ogni app di Microsoft Store per le aziende include ora un suffisso **Online** o **Offline**. La pagina dei dettagli dell'app include anche informazioni relative a **tipo di licenza** e **supporto dell'installazione per contesto di dispositivo** (solo app con licenza offline).

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>App Portale aziendale nei dispositivi condivisi Windows<!--4393553 -->
Gli utenti possono ora accedere all'app Portale aziendale nei dispositivi condivisi Windows. Gli utenti finali visualizzeranno un'etichetta **Condiviso** nel riquadro del dispositivo. Questa funzionalità si applica all'app Portale aziendale di Windows, versione 10.3.45609.0 e successive.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>Visualizzare tutte le app installate dalla nuova pagina Web del portale aziendale<!-- 4224326 -->
Nella nuova pagina **App installate** del sito Web del portale aziendale sono elencate tutte le app gestite, sia obbligatorie che disponibili, installate nei dispositivi di un utente. Oltre al tipo di assegnazione, gli utenti possono visualizzare l'editore, la data di pubblicazione o lo stato di installazione corrente dell'app. Se non sono state impostate app obbligatorie o disponibili per gli utenti, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Per visualizzare la nuova pagina sul Web, passare al [sito Web del portale aziendale](https://portal.manage.microsoft.com) e fare clic su **App installate**.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>Una nuova visualizzazione consente agli utenti di vedere tutte le app gestite installate nel dispositivo<!-- 2352913 -->  
L'app Portale aziendale per Windows elenca ora tutte le app gestite, sia obbligatorie che disponibili, installate nel dispositivo dell'utente. Gli utenti possono anche visualizzare le installazioni di app tentate e in sospeso e i rispettivi stati correnti. Se non sono state impostate app obbligatorie o disponibili per gli utenti, verrà visualizzato un messaggio che indica che non è stata installata alcuna app aziendale. Per accedere alla nuova visualizzazione, passare al riquadro di spostamento dell'app Portale aziendale e selezionare **App** > **App installate**.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>Configurare le impostazioni per le estensioni del kernel nei dispositivi macOS<!-- 2043024 -->
Nei dispositivi macOS è possibile creare un profilo di configurazione del dispositivo (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > scegliere **macOS** per la piattaforma). Questo aggiornamento include un nuovo gruppo di impostazioni che consentono di configurare e usare le estensioni del kernel nei dispositivi. È possibile aggiungere estensioni specifiche o consentire l'uso di tutte le estensioni di un partner o uno sviluppatore specifico.

Per altre informazioni su questa funzionalità, vedere gli argomenti relativi alla [panoramica delle estensioni del kernel](../configuration/kernel-extensions-overview-macos.md) e alle [impostazioni delle estensioni del kernel](../configuration/kernel-extensions-settings-macos.md).

Si applica a: macOS 10.13.2 e versioni successive

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>L'impostazione app solo dallo store per i dispositivi Windows 10 include altre opzioni di configurazione<!-- 2697002 -->
Quando si crea un profilo di limitazione del dispositivo per i dispositivi Windows è possibile usare l'impostazione **Apps from the store only** (App solo dallo store) in modo che gli utenti installino app solo dall'archivio applicazioni di Windows (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **Windows 10 e versioni successive** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). In questo aggiornamento questa impostazione viene estesa per supportare altre opzioni.

Per visualizzare la nuova impostazione, andare a [Impostazioni dei dispositivi Windows 10 (e versioni successive) per consentire o limitare l'uso delle funzionalità](../configuration/device-restrictions-windows-10.md#app-store).

Si applica a: Windows 10 e versioni successive

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>Distribuire più profili di dispositivo per estensioni della mobilità Zebra in un dispositivo, in un gruppo di utenti o in un gruppo di dispositivi<!-- 4089955 -->
In Intune è possibile usare estensioni di mobilità Zebra (MX) in un profilo di configurazione del dispositivo per personalizzare le impostazioni dei dispositivi Zebra non predefinite in Intune. Attualmente è possibile distribuire un profilo per un dispositivo singolo. Questo aggiornamento consente di distribuire più profili in:
- Un gruppo di utenti
- Un gruppo di dispositivi
- Un dispositivo singolo

Per informazioni su come usare MX in Intune, vedere [Usare e gestire i dispositivi Zebra con Mobility Extensions di Zebra in Microsoft Intune](../configuration/android-zebra-mx-overview.md).

Si applica a: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>Alcune impostazioni della modalità tutto schermo nei dispositivi iOS vengono impostate usando "Blocca" che sostituisce "Consenti"<!-- 4404075  -->
Quando si crea un profilo di limitazione del dispositivo in dispositivi iOS (**Configurazione dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Modalità tutto schermo**), si impostano **Blocco automatico**, **Commutatore suoneria**, **Rotazione schermo**, **Pulsante Sospensione schermo** e **Pulsanti volume**.

In questo aggiornamento i valori sono **Blocca** (blocca la funzionalità) o **Non configurate** (consente la funzionalità). Per visualizzare le impostazioni, andare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità](../configuration/device-restrictions-ios.md#kiosk).

Si applica a: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>Usare Face ID per l'autenticazione della password nei dispositivi iOS<!-- 4490704 -->
Quando si crea un profilo di limitazione per i dispositivi iOS, è possibile usare l'impronta digitale come password. In questo aggiornamento le impostazioni della password tramite impronta digitale consentiranno anche il riconoscimento facciale (**Configurazione dispositivo** > **Profili** > **Crea profilo**  > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **Password**). Di conseguenza, le impostazioni seguenti sono modificate:

- **Sblocco con impronta digitale** ora è **Sblocco di Touch ID e Face ID**.
- **Modifica dell'impronta digitale (solo con supervisione)** ora è **Modifica di Touch ID e Face ID (solo con supervisione)** .

Face ID è disponibile in iOS 11.0 e versioni successive. Per visualizzare le impostazioni, andare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md#password).

Si applica a: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>La limitazione di giochi e funzionalità dell'App Store nei dispositivi iOS è ora dipendente dall'area classificazioni<!-- 4593948 -->
Nei dispositivi iOS è possibile consentire o limitare le funzionalità relative a giochi, App Store e visualizzazione dei documenti (**Configurazione dispositivo** > **Profili** > **Crea profilo**  > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi**). È anche possibile scegliere l'area classificazioni, ad esempio Stati Uniti.

In questo aggiornamento la funzionalità **App** è stata impostata come un elemento figlio di **Area classificazioni** e dipende da **Area classificazioni**. Per visualizzare le impostazioni, andare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Si applica a: iOS

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>Supporto di Windows Autopilot per Aggiunta ad Azure AD ibrido<!-- 4809146-->
Windows Autopilot per i dispositivi esistenti supporta ora Aggiunta ad Azure AD ibrido (oltre al supporto di Aggiunta di Azure AD esistente). Si applica ai dispositivi con Windows 10, versione 1809 e successive. Per altre informazioni, vedere [Windows Autopilot per dispositivi esistenti](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Visualizzare il livello della patch di protezione per i dispositivi Android<!-- 4461911 -->
È ora possibile visualizzare il livello della patch di protezione per i dispositivi Android. A tale scopo, scegliere **Intune** > **Dispositivi** > **Tutti i dispositivi** > scegliere un dispositivo > **Hardware**.
Il livello di patch è elencato nella sezione **Sistema operativo**.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>Assegnare i tag di ambito a tutti i dispositivi gestiti in un gruppo di sicurezza<!-- 3173810 -->
È ora possibile assegnare i tag di ambito a un gruppo di sicurezza. Anche tutti i dispositivi del gruppo di sicurezza saranno associati a tali tag di ambito. Il tag di ambito verrà assegnato anche a tutti i dispositivi appartenenti ai gruppi. I tag di ambito impostati con questa funzionalità sovrascriveranno quelli impostati con il flusso di tag di ambito del dispositivo corrente. Per altre informazioni, vedere [Use RBAC and scope tags for distributed IT](scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

### <a name="device-security"></a>Sicurezza del dispositivo

#### <a name="use-keyword-search-with-security-baselines------"></a>Usare la ricerca di parole chiave con le baseline di sicurezza<!--  -->
Quando si creano o si modificano i [profili della baseline di sicurezza](../protect/security-baselines.md#create-the-profile), è possibile specificare parole chiave nella nuova barra di *ricerca* per filtrare i gruppi di impostazioni disponibili in base a quelli che contengono i criteri di ricerca.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>La funzionalità Baseline di sicurezza è ora disponibile a livello generale<!-- 3785395 -->
La funzionalità **Baseline di sicurezza** non è più in fase di anteprima ed è ora disponibile a livello generale.  Tale funzionalità è pertanto pronta per l'uso nell'ambiente di produzione. I singoli modelli di baseline possono tuttavia rimanere disponibili in anteprima e vengono valutati e rilasciati a livello generale con le proprie pianificazioni.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>Il modello Baseline della sicurezza MDM è ora disponibile a livello generale<!-- 3794072, 4217151,  3534649 -->
Il modello Baseline della sicurezza MDM non è più in fase di anteprima ed è ora disponibile a livello generale. Il modello disponibile a livello generale viene identificato come **Baseline della sicurezza MDM per maggio 2019**.  Si tratta di un nuovo modello, non di un aggiornamento dalla versione di anteprima.  È pertanto necessario rivedere le [impostazioni in esso contenute](../protect/security-baseline-settings-mdm.md) e creare quindi nuovi profili per distribuire il modello nel dispositivo in uso. Altri modelli di baseline di sicurezza possono rimanere in anteprima. Per un elenco delle baseline disponibili, vedere [Baseline di sicurezza disponibili](../protect/security-baselines.md#available-security-baselines).  

Il modello *Baseline della sicurezza MDM per maggio 2019*, oltre a essere nuovo, include le due impostazioni annunciate di recente nell'articolo relativo alle funzionalità in fase di sviluppo:  
- AboveLock. Attiva tramite voce le app dalla schermata di blocco  
- DeviceGuard. Usa la sicurezza basata sulla virtualizzazione al riavvio successivo dei dispositivi.  

*Baseline della sicurezza MDM per maggio 2019* include anche l'aggiunta di numerose nuove impostazioni, la rimozione di altre e una revisione del valore predefinito di un'impostazione. Per un elenco dettagliato delle modifiche tra versione di anteprima e versione disponibile a livello generale, vedere **What's changed in the new template** (Cosa è cambiato nel nuovo modello).

#### <a name="security-baseline-versioning---3194322---"></a>Controllo delle versioni delle baseline di sicurezza<!-- 3194322 -->
Le baseline di sicurezza per Intune supportano il controllo delle versioni. Al rilascio di nuove versioni di ogni baseline di sicurezza, è dunque possibile aggiornare i profili delle baseline di sicurezza esistenti in modo che usino la versione di baseline più recente, senza dover ricreare e distribuire una nuova baseline. Nella console di Intune è inoltre possibile visualizzare informazioni su ogni baseline, ad esempio il numero di profili individuali che usano la baseline, quante diverse versioni di baseline vengono usate dai profili e la versione più recente di una specifica baseline di sicurezza.  Per altre informazioni, vedere **Baseline di sicurezza**.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>Spostamento dell'impostazione Usa le chiavi di sicurezza per l'accesso<!-- 4501151 -->
L'impostazione di configurazione del dispositivo per la protezione delle identità denominata **Usa le chiavi di sicurezza per l'accesso** non è più disponibile come un'impostazione secondaria di *Configura Windows Hello for Business*. È ora un'impostazione di livello superiore sempre disponibile, anche quando non si abilita l'uso di Windows Hello for Business. Per altre informazioni, vedere [Protezione dell'identità](../protect/identity-protection-windows-settings.md).

### <a name="role-based-access-control"></a>Controllo di accesso in base ai ruoli

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>Nuove autorizzazioni per gli amministratori di gruppi assegnati<!-- 4504437   -->
Il ruolo di amministratore dell'istituto di istruzione predefinito di Intune dispone ora di autorizzazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD) per le app gestite. Grazie a questo aggiornamento, un utente a cui è assegnato il ruolo di amministratore di gruppo in Intune per Education potrà creare, visualizzare, aggiornare ed eliminare il certificato per le notifiche push MDM iOS, i token del server MDM iOS e i token VPP iOS, oltre a [tutte le autorizzazioni esistenti di cui dispone](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions). Per eseguire una di queste azioni, andare a **Impostazioni del tenant** > **Gestione dei dispositivi iOS**.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>Le applicazioni possono usare l'API Graph per chiamare le operazioni di lettura senza credenziali utente<!-- 4655885 -->
Le applicazioni possono chiamare le operazioni di lettura dell'API Graph per Intune con l'identità dell'app senza le credenziali utente. Per altre informazioni sull'accesso all'API Microsoft Graph per Intune, vedere [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) (Usare Intune in Microsoft Graph).

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>Applicare tag di ambito alle app di Microsoft Store per le aziende<!-- 4392555 -->
È ora possibile applicare tag di ambito alle app di Microsoft Store per le aziende. Per altre informazioni sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

## <a name="week-of-june-17-2019"></a>Settimana del 17 giugno 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="new-features-in-microsoft-intune-app"></a>Nuove funzionalità dell'app Microsoft Intune
Sono state aggiunte nuove funzionalità all'app Microsoft Intune (anteprima) per Android. Ora gli utenti di dispositivi Android completamente gestiti possono:  

* Visualizzare e gestire i dispositivi che hanno registrato tramite il Portale aziendale Intune o l'app Microsoft Intune.
* Contattare l'organizzazione per richiedere supporto.
* Inviare feedback a Microsoft.
* Visualizzare termini e condizioni, se impostati dall'organizzazione.

## <a name="week-of-june-10-2019"></a>Settimana del 10 giugno 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>Nuove app di esempio che mostrano l'integrazione di Intune SDK disponibile su GitHub<!-- 2653471 -->
L'account msintuneappsdk di GitHub ha aggiunto nuove applicazioni di esempio per iOS (Swift), Android, Xamarin.iOS, Xamarin Forms e Xamarin.Android. Lo scopo di queste app è completare la documentazione esistente e fornire dimostrazioni su come integrare Intune App SDK nelle proprie app per dispositivi mobili. Gli sviluppatori di app che hanno bisogno di altre indicazioni di Intune SDK possono vedere i collegamenti agli esempi seguenti:
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App): app di messaggistica istantanea nativa di iOS (Swift) che usa Azure Active Directory Authentication Library (ADAL) per l'autenticazione negoziata.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App): app di elenco attività nativa di Android che usa ADAL per l'autenticazione negoziata.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps): app di elenco attività di Xamarin.Android che usa ADAL per l'autenticazione negoziata. Questo repository contiene anche l'app Xamarin.Forms.
- [App di esempio di Xamarin.iOS](https://github.com/msintuneappsdk/sample-intune-xamarin-ios): app di esempio di base per Xamarin.iOS.

## <a name="week-of-may-27-2019"></a>Settimana del 27 maggio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Creazione di report per app potenzialmente dannose nei dispositivi Android<!-- 4223162 -->
Intune ora offre ulteriori informazioni di report sulle app potenzialmente dannose nei dispositivi Android. 

## <a name="week-of-may-20-2019"></a>Settimana del 20 maggio 2019

### <a name="app-management"></a>Gestione delle app

#### <a name="windows-company-portal-app---3316993---"></a>App Portale aziendale Windows<!-- 3316993 -->
L'app Portale aziendale di Windows ora ha una nuova pagina con l'etichetta **Dispositivi**. La pagina **Dispositivi** visualizza per gli utenti finali tutti i loro dispositivi registrati. Gli utenti visualizzano questa modifica nel Portale aziendale quando usano la versione 10.3.4291.0 e le versioni successive. Per informazioni sulla configurazione del Portale aziendale, vedere [Come configurare l'app Portale aziendale di Microsoft Intune](../apps/company-portal-app.md).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Nome dell'attributo OrderID dei dispositivi Autopilot modificato in Tag di gruppo <!-- 4659453 -->

Il nome dell'attributo **OrderID** nei dispositivi Autopilot è stato modificato in **Tag di gruppo** per renderlo più intuitivo. Quando si usano file con estensione csv per caricare informazioni sui dispositivi Autopilot, è necessario usare come intestazione colonna Tag di gruppo e non OrderID.  

## <a name="week-of-may-13-2019-1905-service-release"></a>Settimana del 13 maggio 2019 (versione del servizio 1905)

### <a name="app-management"></a>Gestione delle app

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Aggiornamento del metodo di autenticazione e dell'installazione dell'app Portale aziendale per i criteri di Intune<!-- 1927359  -->
Nei dispositivi già registrati tramite l'Assistente configurazione con uno dei metodi di registrazione dei dispositivi aziendali di Apple, Intune non supporterà più l'app Portale aziendale se installata manualmente dagli utenti finali dall'App Store. Questa modifica è rilevante solo quando si esegue l'autenticazione con Apple Setup Assistant durante la registrazione. Questa modifica riguarda inoltre solo i dispositivi iOS registrati tramite:  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple Device Enrollment Program (DEP)

Gli utenti riceveranno un errore se installano l'app Portale aziendale dall'App Store e quindi provano a registrare i dispositivi tramite tale app. È previsto che questi dispositivi usino l'app Portale aziendale solo quando ne è stato eseguito il push automaticamente da Intune durante la registrazione. I profili di registrazione in Intune nel portale di Azure verranno aggiornati in modo che sia possibile specificare come devono eseguire l'autenticazione i dispositivi e se ricevono l'app Portale aziendale. Se si vuole che gli utenti dei dispositivi DEP dispongano dell'app Portale aziendale, è necessario specificare le preferenze in un profilo di registrazione. 

Inoltre, la schermata **Identifica il dispositivo** nel Portale aziendale iOS è in fase di rimozione. Di conseguenza, gli amministratori che vogliono abilitare l'accesso condizionale o distribuire le app aziendali devono aggiornare il profilo di registrazione DEP. Questo requisito si applica solo se la registrazione DEP viene autenticata con Assistente configurazione. In tal caso, è necessario eseguire il push del Portale aziendale nel dispositivo. A tale scopo, scegliere **Intune** > **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token > **Profili** > scegliere un profilo > **Proprietà** > impostare **Installa il Portale aziendale** su **Sì**.

Per installare il Portale aziendale nei dispositivi DEP già registrati, si dovrà passare a Intune > App client ed eseguirne il push come app gestita con i criteri di configurazione delle app. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>Configurare come gli utenti finali aggiornano un'app line-of-business usando i criteri di protezione delle app<!-- 3568384 -->
È ora possibile configurare dove gli utenti finali possono ottenere una versione aggiornata di un'app line-of-business. Gli utenti finali visualizzeranno questa funzionalità nella finestra di dialogo di avvio condizionale **Versione minima dell'app**, in cui verrà chiesto loro di eseguire l'aggiornamento a una versione minima dell'app line-of-business. È necessario fornire queste informazioni dettagliate relative all'aggiornamento come parte dei criteri di protezione dell'app line-of-business (APP). Questa funzionalità è disponibile per iOS e Android. In iOS questa funzionalità richiede che l'app venga integrata (o sottoposta a wrapping tramite lo strumento di wrapping) con Intune SDK per iOS 10.0.7 o versioni successive. In Android questa funzionalità richiede la versione del Portale aziendale più recente. Per configurare il modo in cui un utente finale aggiorna un'app line-of-business, l'app necessita che venga inviato un criterio di configurazione dell'app gestita con la chiave `com.microsoft.intune.myappstore`. Il valore inviato definirà da quale archivio l'utente finale scaricherà l'app. Se l'app viene distribuita tramite il portale aziendale, il valore deve essere `CompanyPortal`. Per qualsiasi altro archivio, è necessario immettere un URL completo.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Script di PowerShell per l'estensione di gestione di Intune<!-- 3734186  -->
È possibile configurare gli script di PowerShell per l'esecuzione con privilegi di amministratore dell'utente nel dispositivo. Per altre informazioni, vedere [Usare gli script di PowerShell nei dispositivi Windows 10 in Intune](../apps/intune-management-extension.md) e [Gestione delle app Win32](../apps/app-management.md).

#### <a name="android-enterprise-app-management---4459905---"></a>Gestione delle app Android Enterprise<!-- 4459905 -->
Per facilitare la configurazione e l'uso delle funzionalità di gestione di Android Enterprise per gli amministratori IT, Intune aggiungerà automaticamente quattro app comuni correlate a Android Enterprise alla console di amministrazione di Intune. Le quattro app per Android Enterprise sono le seguenti:

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Usata per gli scenari di Android Enterprise completamente gestiti.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - Consente di accedere agli account se si usa la verifica a due fattori.
- **[Portale aziendale di Intune](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - Usare per gli scenari con criteri di protezione app e profili di lavoro di Android Enterprise.
- [Schermata iniziale gestita](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - Usata per gli scenari di Android Enterprise dedicati/in modalità a schermo intero.

In precedenza, gli amministratori IT dovevano trovare e approvare manualmente queste app in [Google Play Store gestito](https://play.google.com/store/apps) durante l'installazione. Questa modifica rimuove i passaggi manuali precedenti per consentire ai clienti di usare più facilmente e velocemente le funzionalità di gestione di Android Enterprise.

Gli amministratori IT noteranno che queste quattro app vengono aggiunte automaticamente all'elenco di app di Intune in occasione della prima connessione del tenant di Intune a Google Play gestito. Per altre informazioni, vedere [Connettere l'account di Intune all'account di Google Play gestito](../enrollment/connect-intune-android-enterprise.md). Per i tenant già connessi o che usano già Android Enterprise, gli amministratori non devono eseguire alcuna operazione. Queste quattro app diventeranno disponibili automaticamente entro 7 giorni dal completamento dell'implementazione del servizio di maggio 2019.

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>Connettore di certificati PFX per Microsoft Intune aggiornato<!-- 1533038 -->
È stato rilasciato un aggiornamento per il [Connettore del certificato PFX per Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) che risolve un problema a causa del quale i certificati PFX esistenti continuano a essere rielaborati e di conseguenza il connettore smette di elaborare le nuove richieste.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Attività di sicurezza di Intune per Defender ATP (in anteprima pubblica)<!-- 3208597 -->
Nella fase di anteprima pubblica, è possibile usare Intune per gestire le [attività di sicurezza per Microsoft Defender Advanced Threat Protection (ATP)](../protect/atp-manage-vulnerabilities.md). L'integrazione con ATP aggiunge un approccio basato sui rischi per individuare, classificare e correggere gli errori di configurazione e le vulnerabilità degli endpoint, riducendo il tempo tra l'individuazione e la mitigazione.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671-----"></a>Verificare la presenza di un chipset TPM in un criterio di conformità del dispositivo Windows 10<!-- 3617671   -->
Molti dispositivi Windows 10 e versioni successive hanno chipset Trusted Platform Module (TPM). Questo aggiornamento include una nuova impostazione di conformità che controlla la versione del chip TPM del dispositivo.

Questa impostazione è descritta in [Impostazioni dei criteri di conformità per i dispositivi Windows 10 e versioni successive](../protect/compliance-policy-create-windows.md#device-security).

Si applica a: Windows 10 e versioni successive

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>Impedire agli utenti finali di modificare l'hotspot personale e disabilitare la registrazione nel server Siri nei dispositivi iOS<!-- 4097904   -->  
Creare un profilo di limitazioni del dispositivo nel dispositivo iOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni, che è possibile configurare:

- **App predefinite**: Registrazione lato server per i comandi di Siri
- **Wireless**: Modifica dell'utente dell'hotspot personale (solo con supervisione)

Per visualizzare queste impostazioni, passare alle [impostazioni predefinite dell'app per iOS](../configuration/device-restrictions-ios.md#built-in-apps) e alle [impostazioni wireless per iOS](../configuration/device-restrictions-ios.md#wireless).

Si applica a: iOS 12.2 e versioni successive

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>Nuove impostazioni di limitazione del dispositivo per l'app Classroom per i dispositivi macOS<!-- 4097905   --> 
È possibile creare un profilo di configurazione del dispositivo per i dispositivi macOS (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **macOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo). Questo aggiornamento include nuove impostazioni dell'app Classroom, la possibilità di bloccare gli screenshot e la possibilità di disabilitare la Libreria foto di iCloud.

Per visualizzare le impostazioni correnti, passare a [Impostazioni dei dispositivi iOS per consentire o limitare l'uso delle funzionalità tramite Intune](../configuration/device-restrictions-macos.md).

Si applica a: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>L'impostazione della password iOS per l'accesso all'App Store è stata rinominata<!-- 4557891  -->
L'impostazione **Password per l'accesso all'App Store** è stata rinominata in **Require iTunes Store password for all purchases** (Richiedere password iTunes Store per tutti gli acquisti) (**Configurazione del dispositivo** > **Profili** > **Crea profilo** > **iOS** per la piattaforma > **Limitazioni del dispositivo** per il tipo di profilo > **App Store, visualizzazione documenti, giochi**).

Per visualizzare le impostazioni disponibili, passare alle [impostazioni iOS di App Store, visualizzazione documenti, giochi](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming).

Si applica a: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Baseline di Microsoft Defender Advanced Threat Protection (anteprima)<!--  3754134 -->
È stata aggiunta un'anteprima della baseline di sicurezza per le impostazioni di [Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md). Questa baseline è disponibile quando l'ambiente soddisfa i prerequisiti per l'uso di [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites).

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>La pagina relativa allo stato della registrazione di Windows è ora disponibile a livello generale<!-- 3605348 -->
La pagina relativa allo stato della registrazione non è più in fase di anteprima. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](../enrollment/windows-enrollment-status.md).


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Aggiornamento dell'interfaccia utente di Intune - Creazione del profilo di registrazione Autopilot<!-- 4593669 -->
L'interfaccia utente per la creazione di un profilo di registrazione Autopilot è stata aggiornata per allinearsi agli stili dell'interfaccia utente di Azure. Per altre informazioni, vedere [Creare un profilo di distribuzione Autopilot](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile). Più avanti, altri scenari di Intune verranno aggiornati a questo nuovo stile dell'interfaccia utente.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>Abilitare Reimpostazione di AutoPilot per tutti i dispositivi Windows<!-- 4225665 -->
Reimpostazione di AutoPilot ora funziona per tutti i dispositivi Windows, anche quelli non configurati per l'uso della pagina relativa allo stato della registrazione. Se durante la registrazione iniziale del dispositivo non è stata configurata una pagina relativa allo stato della registrazione per il dispositivo, il dispositivo passerà direttamente al desktop dopo l'accesso. Potrebbero essere necessarie fino a otto ore per la sincronizzazione e la visualizzazione come conforme in Intune. Per altre informazioni, vedere [Reimpostare i dispositivi con Reimpostazione di Windows Autopilot remota](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote).

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>Formato IMEI esatto non richiesto durante la ricerca in tutti i dispositivi<!--30407680 -->
Non è necessario includere spazi nei numeri IMEI quando si esegue una ricerca in **Tutti i dispositivi**.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>L'eliminazione di un dispositivo nel portale Apple si rifletterà nel portale di Intune<!--2489996 -->
Se un dispositivo viene eliminato dai portali di Device Enrollment Program di Apple o Apple Business Manager, il dispositivo verrà automaticamente eliminato da Intune durante la sincronizzazione successiva.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>La pagina di stato della registrazione ora tiene traccia delle app Win32<!-- 2714451 -->
Ciò si applica solo ai dispositivi che eseguono Windows 10 versione 1903 e successive. Per altre informazioni, vedere [Configurare la pagina dello stato della registrazione](../enrollment/windows-enrollment-status.md).

### <a name="device-management"></a>Gestione dei dispositivi

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Reimpostare e cancellare i dispositivi in blocco usando l'API Graph<!-- 3295288 -->
È ora possibile reimpostare e cancellare un massimo di 100 dispositivi in blocco tramite l'API Graph.

### <a name="monitor-and-troubleshoot"></a>Monitorare e risolvere i problemi

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>Il report di crittografia non è più disponibile come anteprima pubblica<!-- 4587546      -->
Il [report per BitLocker e la crittografia dei dispositivi](../protect/encryption-monitor.md) è ora disponibile a livello generale e non più come anteprima pubblica.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>Impostazioni biometriche e della firma di Outlook per dispositivi iOS e Android<!-- 4050557 -->
È ora possibile specificare se la firma predefinita è abilitata in Outlook nei dispositivi iOS e Android. Inoltre, è possibile scegliere se consentire agli utenti di modificare l'impostazione biometrica in Outlook in iOS.

## <a name="week-of-may-6-2019"></a>Settimana del 6 maggio 2019

### <a name="device-configuration"></a>Configurazione del dispositivo

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>Supporto del controllo di accesso alla rete per F5 Access per dispositivi iOS<!-- 4500808 -->

F5 ha rilasciato un aggiornamento di BIG-IP 13 che abilita la funzionalità di controllo di accesso alla rete per F5 Access su iOS in Intune. Per usare questa funzionalità:

- Aggiornare BIG-IP alla versione 13.1.1.5. BIG-IP 14 non è supportata.
- Integrare BIG-IP con Intune per il controllo di accesso alla rete. Vedere la procedura in [Overview: Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html).
- Controllare l'impostazione di **Abilita il controllo accesso alla rete** nel profilo VPN in Intune.

Per vedere l'impostazione disponibile, passare a [Configurare le impostazioni VPN nei dispositivi iOS](../configuration/vpn-settings-ios.md).

Si applica a: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>Connettore di certificati PFX per Microsoft Intune aggiornato<!-- doc-vso 1521237  -->  
È stato rilasciato un aggiornamento del [connettore di certificati PFX per Microsoft Intune](../protect/certficates-pfx-configure.md#whats-new-for-connectors) in cui l'intervallo di polling è stato ridotto da 5 minuti a 30 secondi.




## <a name="notices"></a>Notifiche

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
