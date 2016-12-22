---
title: "Novità | Microsoft Intune"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 12/08/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9fd309a10d9eb020795c5ce46df124b13dc1a006
ms.openlocfilehash: d117c929fbde4dd0a39503b8da695aa9c9ea91ad


---
# <a name="whats-new-in-microsoft-intune---december-2016"></a>Novità di Microsoft Intune - Dicembre 2016
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

> [!Note]
> Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/en-us/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="public-preview-of-the-new-intune-admin-experience-on-azure--736542--"></a>Anteprima pubblica della nuova esperienza di amministrazione di Intune in Azure<!--736542-->
All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile usando le API Graph. Prima della disponibilità generale di questo portale per tutti i tenant di Intune, siamo lieti di annunciare che verrà introdotta un'anteprima di questa nuova esperienza di amministrazione in seguito durante il mese a tenant selezionati.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, per scoprire cosa abbiamo in serbo per Microsoft Intune nel portale di Azure, vedere la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

Per qualsiasi domanda in merito alla tempistica per la migrazione del tenant, contattare il team Microsoft responsabile della migrazione all'indirizzo [intunegrps@microsoft.com](mailto:intunegrps@microsoft.com).

### <a name="telecom-expense-management-integration-in-public-preview-of-azure-portal--747605--"></a>Integrazione della gestione delle spese di telecomunicazione nell'anteprima pubblica del portale di Azure<!--747605-->
Stiamo iniziando a presentare in anteprima l'integrazione con i servizi di gestione delle spese di telecomunicazione di terze parti nel portale di Azure. È possibile usare Intune per imporre limiti al consumo dei dati sia nazionale che in roaming. Queste integrazioni iniziano con [Saaswedo](http://www.saaswedo.com).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="multi-factor-authentication-across-all-platforms---747590--"></a>Autenticazione a più fattori su tutte le piattaforme <!--747590-->
È ora possibile imporre l'autenticazione a più fattori (MFA) per un gruppo selezionato di utenti durante la registrazione di un dispositivo iOS, Android, Windows 8.1+ o Windows Phone 8.1+ dal portale di gestione di Azure configurando MFA nell'applicazione di registrazione di Microsoft Intune in Azure Active Directory.

<!--VSO 679339, awaiting chrisgre for go-live--><!--### Conditional access for MAM with SharePoint Online
È possibile impedire l'accesso a SharePoint Online alle app non supportate dai criteri di gestione delle app mobili (MAM) di Intune.  È possibile iniziare a usare le funzionalità di gestione delle app mobili di Intune nel portale di Azure. Individuare la sezione __Accesso condizionale__ nel pannello __Impostazioni__ che includerà l'opzione per SharePoint Online. Questa funzionalità verrà fornita separatamente rispetto al resto del rilascio del servizio. Altre informazioni su questa nuova funzionalità sono disponibili [qui](https://docs.microsoft.com/intune/deploy-use/mam-ca-for-sharepoint-online).-->

### <a name="ability-to-restrict-mobile-device-enrollment--747596--"></a>Possibilità di limitare la registrazione di dispositivi mobili<!--747596-->
Intune aggiunge nuove limitazioni di registrazione che consentono di controllare quali piattaforme per dispositivi mobili sono autorizzate alla registrazione. Intune separa le piattaforme per dispositivi mobili iOS, macOS, Android, Windows e Windows Mobile.
* La limitazione della registrazione di dispositivi mobili non limita la registrazione di client PC.
* Solo per iOS: è disponibile un'altra opzione che consente di bloccare la registrazione dei dispositivi personali.

Intune contrassegna tutti i nuovi dispositivi come personali, a meno che l'amministratore IT non esegua un'operazione per contrassegnarli come aziendali, come spiegato in [questo articolo](https://docs.microsoft.com/en-us/intune/deploy-use/manage-corporate-owned-devices).


## <a name="notices"></a>Notifiche

### <a name="multi-factor-authentication-on-enrollment-moving-to-the-azure-portal---vso-750545--"></a>Trasferimento di Multi-Factor Authentication per la registrazione nel portale di Azure <!--VSO 750545-->
Per impostare MFA per le registrazioni in Intune, gli amministratori dovevano usare in precedenza la console di Intune o Configuration Manager (prima della versione di ottobre 2016). Con questa funzionalità aggiornata è ora possibile accedere al [portale di Microsoft Azure](https://manage.windowsazure.com) con le credenziali di Intune e configurare le impostazioni di MFA tramite Azure AD. Per altre informazioni a questo proposito, vedere [qui](https://aka.ms/mfa_ad).

### <a name="company-portal-app-for-android-now-available-in-china--vso-658093--"></a>L'app Portale aziendale per Android è ora disponibile in Cina <!--VSO 658093-->
L'app Portale aziendale per Android sta per essere pubblicata per il download in Cina. A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere l'app dai marketplace di app cinesi. L'app Portale aziendale per Android sarà disponibile per il download negli store seguenti:
* [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
* [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
* [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
* [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
* [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

L'app Portale aziendale per Android usa i servizi Google Play per comunicare con il servizio Microsoft Intune. Dato che i servizi Google Play non sono ancora disponibili in Cina, per completare qualsiasi attività tra le seguenti possono essere richieste fino a 8 ore. 

|Console di amministrazione di Intune| App Portale aziendale di Intune per Android |Sito Web del portale aziendale di Intune|   
|---|---|---|
|Cancellazione completa| Rimozione di un dispositivo remoto| Rimozione di un dispositivo (locale e remoto)|
|Cancellazione selettiva| Reimpostazione del dispositivo| Reimpostazione del dispositivo|
|Distribuzioni di app nuove o aggiornate| Installazione delle app line-of-business disponibili| Reimpostazione del passcode del dispositivo|
|Blocco remoto|||
|Reimpostazione del passcode|||

## <a name="deprecations"></a>Elementi deprecati

### <a name="firefox-to-no-longer-support-silverlight--vso-tba--"></a>Firefox non supporterà più Silverlight<!--VSO TBA-->
Mozilla sta per rimuovere il supporto per Silverlight nella versione 52 del [browser Firefox](https://www.mozilla.org/firefox), a partire da marzo 2017. Di conseguenza, non sarà più possibile accedere alla console di Intune esistente usando versioni di Firefox superiori alla 51. Si consiglia di usare Internet Explorer 10 o 11 per accedere alla console di amministrazione o una [versione di Firefox precedente alla versione 52](https://ftp.mozilla.org/pub/firefox/releases/). La transizione di Intune al portale di Azure consentirà di supportare una serie di [browser moderni](https://docs.microsoft.com/en-us/azure/azure-preview-portal-supported-browsers-devices) che non dipendono da Silverlight.

### <a name="removal-of-exchange-online-mobile-inbox-policies---770687--"></a>Rimozione del criteri per le cassette postali per dispositivi portatili di Exchange Online <!--770687-->
A partire da dicembre, gli amministratori non potranno più visualizzare o configurare i criteri per le cassette postali per dispositivi portatili di Exchange Online (EAS) all'interno della console di Intune. Questa modifica verrà distribuita in tutti i tenant di Intune nel corso di dicembre e gennaio. La configurazione di tutti i criteri esistenti rimarrà invariata. Per la configurazione dei nuovi criteri, usare Exchange Management Shell. Altre informazioni sono disponibili [qui](https://technet.microsoft.com/en-us/library/bb123783%28v=exchg.150%29.aspx).

### <a name="intune-av-player-image-viewer-and-pdf-viewer-apps-are-no-longer-supported-on-android---747553--"></a>Le app Intune AV Player, Image Viewer e PDF Viewer non sono più supportate in Android <!--747553-->
A partire dalla metà di dicembre 2016, gli utenti non potranno più usare le app Intune AV Player, Image Viewer e PDF Viewer. Queste app sono state sostituite dall'app Azure Information Protection. È possibile trovare altre informazioni sull'app Azure Information Protection [qui](https://docs.microsoft.com/information-protection/rms-client/mobile-app-faq).

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versioni precedenti di Intune](whats-new-archive.md)



<!--HONumber=Dec16_HO2-->


