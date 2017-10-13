---
title: "Novità di Microsoft Intune"
titlesuffix: Azure portal
description: "Informazioni sulle novità nel portale di Intune di Azure"
keywords: 
author: brenduns
ms.author: brenduns
manager: angrobe
ms.date: 10/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b2817537cd9bc5ec6b8e9f5800f0c8f87cfde189
ms.sourcegitcommit: 53a1f5226d1e1172f013a1b192321dde610b2d6c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/06/2017
---
# <a name="whats-new-in-microsoft-intune"></a>Novità di Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Informazioni sulle novità di Microsoft Intune ogni settimana, oltre a indicazioni sulle [modifiche previste](#whats-coming), [notifiche importanti](#notices) sul servizio e informazioni sulle [versioni precedenti](whats-new-archive.md).

> [!Note]
> Molte di queste funzionalità saranno supportate per le distribuzioni ibride con Configuration Manager. Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-october-2-2017"></a>Settimana del 2 ottobre 2017

### <a name="intune-apps"></a>App di Intune

#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>Miglioramenti del flusso di lavoro dell'installazione dei dispositivi nel Portale aziendale <!--1490692-->
È stato migliorato il flusso di lavoro dell'installazione dei dispositivi nell'app Portale aziendale per Android. Il linguaggio è più semplice e specifico per l'azienda e sono state inserite schermate dove possibile. È possibile visualizzare i miglioramenti nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md#week-of-october-2-2017).

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Miglioramento delle linee guida per la richiesta di accesso ai contatti nei dispositivi Android <!--1484985-->

L'app Portale aziendale per Android richiede spesso all'utente finale di accettare l'autorizzazione per i contatti. Se un utente finale rifiuta l'accesso, ora viene visualizzata una notifica in-app che avvisa dell'autorizzazione per l'accesso condizionale. 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Correzione dell'avvio sicuro per Android <!--1490712-->

Gli utenti finali con dispositivi Android potranno selezionare il motivo di non conformità nell'app Portale aziendale. In questo modo, se possibile, accederanno direttamente al percorso corretto nell'applicazione di installazione per risolvere il problema. 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-o---1475932---"></a>Notifiche push aggiuntive per gli utenti finali dell'app Portale aziendale per Android O<!---1475932--->

Gli utenti finali visualizzeranno notifiche aggiuntive che indicheranno loro quando l'app Portale aziendale per Android O sta eseguendo attività in background, ad esempio il recupero di criteri dal servizio di Intune. Gli utenti finali possono così sapere in modo più trasparente quando l'app Portale aziendale ha in esecuzione attività amministrative nel dispositivo. È uno degli aspetti dell'intera [ottimizzazione dell'interfaccia utente del portale aziendale](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) per l'app Portale aziendale per Android O. 

Sono disponibili altre ottimizzazioni per i nuovi elementi dell'interfaccia utente abilitati in Android O. Quando il Portale aziendale sta eseguendo attività in background, ad esempio il recupero dei criteri dal servizio Intune, gli utenti finali visualizzeranno altre notifiche.  In questo modo per gli utenti finali sarà più chiaro quando l'app Portale aziendale sta eseguendo attività amministrative nel dispositivo.

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Nuovi comportamenti dell'app del portale aziendale per Android con i profili di lavoro <!---1485783--->

Quando si registra un dispositivo Android for Work con un profilo di lavoro, è l'app del portale aziendale nel profilo di lavoro a eseguire attività di gestione nel dispositivo. 

A meno che non si usi un'app abilitata per MAM nel profilo personale, l'app del portale aziendale per Android non è più utile. Per migliorare l'esperienza con i profili di lavoro, Intune nasconderà automaticamente l'app del portale aziendale personale dopo la registrazione del profilo di lavoro.

L'app del portale aziendale per Android può essere abilitata in qualsiasi momento nel profilo personale passando al [portale aziendale in Play Store](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) e selezionando **Abilita**.

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Passaggio del portale aziendale per Windows 8.1 e Windows Phone 8.1 alla modalità di mantenimento <!--1428681-->

A partire da ottobre 2017, le app del portale aziendale per Windows 8.1 e Windows Phone 8.1 passeranno alla modalità di mantenimento. Le app e gli scenari esistenti, ad esempio la registrazione e la conformità, continueranno a essere supportati per queste piattaforme. Queste app rimarranno disponibili per il download tramite i canali di rilascio esistenti, ad esempio Microsoft Store. 

Nella modalità di mantenimento, queste app riceveranno solo aggiornamenti della sicurezza critici. Non verranno rilasciati altri aggiornamenti o funzionalità per queste app. Per le nuove funzionalità è consigliabile aggiornare i dispositivi a Windows 10 o Windows 10 Mobile. 

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="block-unsupported-samsung-knox-device-enrollment------1490695----"></a>Bloccare la registrazione di dispositivi Samsung Knox non supportata <!--- 1490695 --->

L'app Portale aziendale tenta di registrare solo i dispositivi Samsung Knox supportati. Per evitare errori di attivazione KNOX che impediscono la registrazione MDM, la registrazione del dispositivo viene eseguita solo se il dispositivo viene visualizzato nell'[elenco di dispositivi pubblicato da Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). I dispositivi Samsung possono avere numeri di modello che supportano KNOX oppure no. Verificare la compatibilità Knox con il rivenditore del dispositivo prima dell'acquisto e della distribuzione. È possibile trovare l'elenco completo dei dispositivi verificati nelle [impostazioni dei criteri Android e Samsung KNOX Standard](/intune-classic/android-policy-settings-in-microsoft-intune.md#supported-samsung-knox-standard-devices).

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920----"></a>Fine del supporto per Android 4.3 e versioni precedenti <!---1171126, 1326920 --->
Le app gestite e l'app Portale aziendale per Android richiederanno Android 4.4 e versioni successive per l'accesso alle risorse aziendali. A dicembre, a tutti i dispositivi registrati verrà imposto il ritiro, con conseguente perdita dell'accesso alle risorse aziendali. Se si usano criteri di protezione delle app senza MDM, le app non riceveranno gli aggiornamenti e la qualità delle loro prestazioni diminuirà nel tempo.

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate nei dispositivi registrati <!--1165314-->
Verrà aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo in tutte le app Portale aziendale. In questo modo gli utenti possono ottenere altre informazioni sulla privacy direttamente dall'articolo [Quali sono le informazioni visibili per l'azienda quando si registra il dispositivo?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune). Questa opzione verrà presto implementata in tutte le app Portale aziendale. Per iOS, l'annuncio è stato fatto a [settembre](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017). 


## <a name="week-of-september-25-2017"></a>Settimana del 25 settembre 2017

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="intune-supports-ios-11---1428975--"></a>Intune supporta iOS 11 <!--1428975-->
Intune supporta iOS 11. Annuncio precedentemente fatto nel [blog del supporto tecnico di Intune](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/).

### <a name="end-of-support-for-ios-80----1164477---"></a>Fine del supporto per iOS 8.0 <!---1164477--->
Le app gestite e l'app Portale aziendale per iOS richiederanno iOS 9.0 e versioni successive per l'accesso alle risorse aziendali. I dispositivi che non verranno aggiornati entro settembre non potranno accedere al Portale aziendale o a tali app. 

### <a name="intune-apps"></a>App di Intune

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Azione di aggiornamento aggiunta all'app del portale aziendale per Windows 10 <!--1132468-->

L'app Portale aziendale per Windows 10 consente agli utenti di aggiornare i dati nell'app trascinando verso il basso per aggiornare o, nei desktop, premendo F5.

## <a name="week-of-september-11-2017"></a>Settimana dell'11 settembre 2017

### <a name="device-enrollment"></a>Registrazione del dispositivo

#### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>Comunicare agli utenti finali quali informazioni sui dispositivi possono essere visualizzate per iOS<!--739894-->

È stata aggiunta l'opzione **Tipo di proprietà** nella schermata Dettagli dispositivo nell'app Portale aziendale per iOS. In questo modo gli utenti potranno ottenere maggiori informazioni sulla privacy direttamente da questa pagina dai documenti per gli utenti finali di Intune. Potranno accedere a queste informazioni anche nella schermata Informazioni su.

#### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>Consentire agli utenti di accedere all'app Portale aziendale per Android senza registrazione <!---1169910--->

Gli utenti finali potranno presto non avere l'obbligo di registrare il dispositivo per accedere all'app Portale aziendale per Android. Agli utenti finali di organizzazioni che usano criteri di protezione delle app non verrà più richiesto di registrare il dispositivo quando aprono l'app Portale aziendale. Gli utenti finali potranno anche installare app dal Portale aziendale senza registrare il dispositivo. 


#### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Testo più comprensibile per l'app Portale aziendale per Android <!---1396349--->  

Il processo di registrazione per l'app del portale aziendale per Android è ora più semplice per gli utenti finali, grazie all'uso di un nuovo testo più comprensibile. Se si usa una documentazione personalizzata per la registrazione, è consigliabile aggiornarla sulla base delle nuove schermate. È possibile trovare immagini di esempio nella pagina [Aggiornamenti dell'interfaccia utente per le app degli utenti finali in Intune](whats-new-app-ui.md#week-of-september-11-2017).

#### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>App del portale aziendale di Windows 10 aggiunta ai criteri per il consenso di Windows Information Protection<!-- 677129 -->

L'app Portale aziendale di Windows 10 è stata aggiornata per supportare Windows Information Protection (WIP). L'app può essere aggiunta ai criteri Consenti di WIP. Con questa modifica non è più necessario aggiungere l'app all'elenco **Esente**.


## <a name="week-of-august-21-2017"></a>Settimana del 21 agosto 2017

### <a name="device-enrollment"></a>Registrazione del dispositivo
#### <a name="improvements-to-device-overview----1404453---"></a>Miglioramenti alla panoramica del dispositivo <!-- 1404453 -->  
In seguito ai miglioramenti, la panoramica del dispositivo ora visualizza i dispositivi registrati ma esclude i dispositivi gestiti da Exchange ActiveSync. I dispositivi Exchange ActiveSync non hanno le stesse opzioni di gestione dei dispositivi registrati. Per visualizzare il numero di dispositivi registrati e il numero di dispositivi registrati per piattaforma in Intune nel portale di Azure, scegliere **Dispositivi** > **Panoramica**.

### <a name="device-management"></a>Gestione dei dispositivi
#### <a name="improvements-to-device-inventory-collected-by-intune"></a>Miglioramenti dell'inventario dei dispositivi gestito da Intune
<!-- 961134, 1104426, 1281327, 1333543 -->
In questa versione sono stati apportati i miglioramenti seguenti alle informazioni di inventario raccolte dai dispositivi gestiti dall'utente:
 
-   Per i dispositivi Android ora è possibile aggiungere all'inventario dei dispositivi una colonna che mostra il livello di patch più recente per ogni dispositivo. Aggiungere la colonna **Security patch level** (Livello patch di protezione) all'elenco di dispositivi per visualizzare il risultato.
-   Quando si applica un filtro alla visualizzazione dei dispositivi ora è possibile filtrare i dispositivi per data di registrazione. Ad esempio, è possibile visualizzare solo i dispositivi registrati dopo una data specificata.
-   Sono stati apportati miglioramenti al filtro usato per l'elemento **Last Check-in Date** (Data ultima archiviazione).
-   Nell'elenco dei dispositivi ora è possibile visualizzare il numero di telefono dei dispositivi di proprietà dell'azienda.
È inoltre possibile usare il riquadro del filtro per cercare i dispositivi in base al numero di telefono.
 
Per altri dettagli sull'inventario dei dispositivi, vedere [Come visualizzare l'inventario dei dispositivi di Intune](device-inventory.md).

#### <a name="conditional-access-support-for-macos-devices"></a>Supporto dell'accesso condizionale per dispositivi macOS 
<!-- 720172 -->
Ora è possibile impostare un criterio di accesso condizionale che richiede che i dispositivi Mac vengano registrati in Intune e siano conformi ai relativi criteri di conformità dei dispositivi. Ad esempio, gli utenti possono scaricare l'app Portale aziendale Intune per macOS e registrare i propri dispositivi Mac in Intune. Intune valuta se il dispositivo Mac è conforme a requisiti come PIN, crittografia, versione del sistema operativo e integrità del sistema.

- Altre informazioni sul [supporto dell'accesso condizionale per dispositivi macOS](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

#### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>L'app Portale aziendale per macOS è disponibile in anteprima pubblica <!---1484796--->
L'app Portale aziendale per macOS è ora disponibile come parte dell'anteprima pubblica dell'accesso condizionale in Enterprise Mobility + Security. Questa versione supporta macOS 10.11 e versioni successive. È possibile ottenerla all'indirizzo [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal). 


#### <a name="new-device-restriction-settings-for-windows-10"></a>Nuove impostazioni per le restrizioni dei dispositivi per Windows 10    
<!--1063965, 1308850  -->
In questa versione sono state aggiunte nuove impostazioni per il [profilo di restrizione dei dispositivi Windows 10](/intune/device-restrictions-windows-10) nelle categorie seguenti:

-   Windows Defender SmartScreen
-   App Store

#### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>Aggiornamenti delle impostazioni del profilo dispositivo Endpoint Protection di Windows 10 per BitLocker
<!--1459533 -->    
In questa versione sono stati apportati i miglioramenti seguenti al funzionamento delle impostazioni BitLocker in un profilo di dispositivo Endpoint Protection di Windows 10:
 
In **Impostazioni dell'unità del sistema operativo BitLocker** per l'impostazione **BitLocker con chip TPM non compatibile**, quando in precedenza si selezionava **Blocca** in realtà BitLocker veniva autorizzato. Questo problema è stato risolto e ora quando si seleziona questa opzione BitLocker viene bloccato.
In **Impostazioni dell'unità del sistema operativo BitLocker**, per l'impostazione **Agente di recupero dati basato su certificati** ora è possibile bloccare in modo esplicito l'agente di recupero dati basato su certificati. Per impostazione predefinita l'agente è consentito.
In **Impostazioni delle unità dati fisse BitLocker**, per l'impostazione **Agente di recupero dati** ora è possibile bloccare in modo esplicito l'agente di recupero dati.
Per altre informazioni, vedere [Endpoint protection settings for Windows 10 and later](endpoint-protection-windows-10.md) (Impostazioni di Endpoint Protection per Windows 10 e versioni successive).


### <a name="app-management"></a>Gestione delle app
#### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Nuova esperienza di accesso per gli utenti dell'app Portale aziendale per Android e gli utenti dei criteri di protezione delle app <!-- 621669 -->
Gli utenti finali possono ora visualizzare le app, gestire i dispositivi e accedere a informazioni sui contatti IT tramite l'app Portale aziendale Android senza registrare i dispositivi Android personali. Inoltre, se un utente finale usa già un'app protetta tramite i criteri di protezione app di Intune e avvia l'app Portale aziendale per Android, l'utente finale non riceve più la richiesta di registrare il dispositivo.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Nuova impostazione nell'app Portale aziendale per Android per attivare/disattivare l'ottimizzazione della memoria <!--1405990-->
La pagina **Impostazioni** nell'app Portale aziendale per Android include una nuova impostazione che consente agli utenti di disattivare facilmente l'ottimizzazione della batteria per le app Portale aziendale e Microsoft Authenticator. Il nome dell'app visualizzato nell'impostazione varia a seconda dell'app usata per gestire l'account aziendale. È consigliabile che gli utenti disattivino l'ottimizzazione della batteria per migliorare le prestazioni delle app aziendali che sincronizzano posta elettronica e dati. 

#### <a name="multi-identity-support-for-onenote-for-ios---------1234281---"></a>Supporto di più identità in OneNote per iOS      <!-- 1234281 -->
Ora gli utenti finali possono usare account diversi (aziendali e personali) con Microsoft OneNote per iOS. I criteri di protezione app possono essere applicati ai dati aziendali nei notebook di lavoro senza influire sul notebook personale dell'utente. Ad esempio un criterio può consentire a un utente di trovare informazioni nei notebook aziendali, ma impedirà all'utente di copiare e incollare dati aziendali dal notebook aziendale a un notebook personale.
 
- Altre informazioni sulle app che supportano la [protezione delle app e identità multiple](https://www.microsoft.com/cloud-platform/microsoft-intune-apps) con Intune.

#### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Nuove impostazioni per consentire e bloccare app nei dispositivi Samsung KNOX Standard
<!-- 1305423 822899-->  
In questa versione vengono aggiunte nuove [impostazioni di restrizione dei dispositivi](device-restrictions-android.md) che consentono di specificare gli elenchi di app seguenti:
 
- App che gli utenti sono autorizzati a installare
- App che gli utenti non possono eseguire
- App che sono nascoste all'utente nel dispositivo
 
È possibile specificare l'app in base all'URL, al nome del pacchetto o dall'elenco di app che si gestiscono.

#### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Nuovo collegamento da Intune all'interfaccia utente per i criteri di accesso condizionale basati su app di Azure AD
<!-- 1016201 -->
Ora gli amministratori IT possono impostare criteri condizionali basati su app tramite la nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Azure AD. Per ora l'accesso condizionale basato su app disponibile nella sezione Protezione app di Intune del portale Azure resta in tale posizione e viene applicato in affiancamento. Per comodità è anche disponibile un collegamento alla nuova interfaccia utente per i criteri di accesso condizionale nel carico di lavoro Intune.

- Altre informazioni sull'[accesso condizionale basato su app in Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference).


## <a name="notices"></a>Notifiche

### <a name="ip-addresses-for-intune-updated----1175274---"></a>Aggiornamento degli indirizzi IP per Intune <!-- 1175274 -->
È disponibile un [elenco aggiornato di nomi DNS e indirizzi IP](/intune/network-bandwidth-use) per le impostazioni proxy del firewall.

### <a name="use-azure-active-directory-for-conditional-access----967947---"></a>Usare Azure Active Directory per l'accesso condizionale <!-- 967947 -->
L'accesso condizionale è disponibile nella sezione di Azure Active Directory del portale di Azure e fornisce un framework più potente e flessibile per l'impostazione di criteri per le app cloud come Office 365 Exchange Online e SharePoint Online.  Usare il pannello **Accesso condizionale in Azure Active Directory** per configurare i criteri invece della console di Intune. I criteri esistenti nella console di Intune devono essere ricreati nel portale di Azure. Per altre informazioni, vedere [Creare criteri di accesso condizionale di Azure AD](/intune/conditional-access-exchange-create.md#create-azure-ad-conditional-access-policies-in-intune-azure-preview).

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Accesso diretto agli scenari di registrazione di Apple <!--951869-->
Per gli account di Intune creati dopo il mese di gennaio 2017, Intune ha abilitato l'accesso diretto agli scenari di registrazione di Apple mediante il carico di lavoro Registra i dispositivi nel portale di Azure. In precedenza, l'anteprima della registrazione di Apple era accessibile solo dai collegamenti nel portale classico di Intune. Gli account di Intune creati prima del mese di gennaio 2017 richiedono un'unica migrazione prima che queste funzionalità siano disponibili in Azure. Il programma per la migrazione non è stato ancora annunciato, ma i dettagli saranno resi disponibili non appena possibile. Se l'account esistente non può accedere al portale di Azure, è fortemente consigliabile creare un account di prova per testare la nuova esperienza.

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Ruoli di amministrazione in corso di sostituzione nel portale di Azure
I ruoli di amministrazione di gestione delle applicazioni per dispositivi mobili (MAM) esistenti (Collaboratore, Proprietario e Sola lettura) usati nel portale classico di Intune (Silverlight) verranno sostituiti con un set completo di nuovi controlli di amministrazione in base al ruolo nel portale di Intune di Azure. Dopo aver completato la migrazione al portale di Azure, sarà necessario riassegnare gli amministratori a questi nuovi ruoli di amministrazione. Per altre informazioni sul controllo degli accessi in base al ruolo e i nuovi ruoli, vedere [Ruoli di Intune (Controllo degli accessi in base al ruolo) per Microsoft Intune](/intune/role-based-access-control).



## <a name="whats-coming"></a>Sviluppi futuri

#### <a name="ios-11-mail-app-will-support-oauth----1196951---"></a>L'app di posta elettronica iOS 11 supporta OAuth <!---1196951--->
L'accesso condizionale con Intune supporta un'autenticazione più sicura sui dispositivi iOS con OAuth. Per il supporto di questa funzionalità il flusso di lavoro nell'app Portale aziendale per iOS è stato modificato, per consentire un'autenticazione più sicura. Quando gli utenti finali tentano di accedere a un nuovo account di Exchange nell'app della posta elettronica, appare una richiesta di visualizzazione Web. Al momento della registrazione in Intune gli utenti visualizzano una richiesta per consentire all'app di posta elettronica nativa l'accesso a un certificato. La maggior parte degli utenti finali non visualizza più i messaggi di posta elettronica di quarantena. Gli account di posta elettronica esistenti continuano a usare il protocollo di autenticazione di base, pertanto gli utenti di questi account ricevono comunque i messaggi di posta elettronica di quarantena. Questa esperienza di accesso per gli utenti finali è simile a quella delle app Office per dispositivi mobili.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Aggiornamenti dell'interfaccia utente del sito Web del portale aziendale <!--1313244 part 2-->
__Aggiornamenti per le app in primo piano__  
È stata aggiunta una pagina dedicata nel sito, nella quale gli utenti possono visualizzare le app che hanno scelto di mettere in primo piano e sono state apportate alcune modifiche all'interfaccia utente della sezione In primo piano nella home page. È possibile visualizzare queste modifiche nella pagina [Novità dell'interfaccia utente dell'app](whats-new-app-ui.md).

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

Passare a Intune nel portale di Azure, visualizzare Dispositivi > Tutti i dispositivi e filtrare l'elenco in base alla versione di iOS per visualizzare eventuali dispositivi correnti con i sistemi operativi precedenti a iOS 9.


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->
Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS.

Microsoft ha reso disponibile una versione dell'app Portale aziendale per iOS tramite il programma Apple TestFlight che applica i nuovi requisiti ATS. Se si desidera provarla in modo da poterne verificare la conformità con ATS, inviare un messaggio di indirizzo elettronica all'indirizzo <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a> con nome, cognome, indirizzo di posta elettronica e nome della società. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [What's new in the Company Portal UI](whats-new-app-ui.md) (Novità nell'interfaccia utente del portale aziendale)
* [Novità dei mesi precedenti](whats-new-archive.md)
