---
title: "Novità | Microsoft Docs"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: 2a602b351cf7f345bd56f20394943ea25f2d2060
ms.lasthandoff: 03/15/2017


---
# <a name="whats-new-in-microsoft-intune---march-2017"></a>Novità di Microsoft Intune - Marzo 2017
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

> [!Note]
> Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://docs.microsoft.com/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management).

## <a name="new-capabilities"></a>Nuove funzionalità

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622-->

L'interfaccia utente dell'app Portale aziendale per Android verrà aggiornata per offrire un aspetto più moderno e una migliore esperienza utente. Di seguito sono illustrati gli aggiornamenti più significativi:

- Colori: le intestazioni delle schede dell'app Portale aziendale possono avere un colore personalizzato definito dal personale IT.
- App: nella scheda **App** i pulsanti **App in evidenza** e **Tutte le app** sono stati aggiornati.
- Ricerca: nella scheda **App** il pulsante **Cerca** è un pulsante di azione mobile.
- Navigazione tra le app: in **Tutte le app** è disponibile una visualizzazione a schede di **In evidenza**, **Tutte** e **Categorie** per una navigazione più semplice.
- Supporto: le schede **Dispositivi personali** e **Contatta l'IT** sono state aggiornate per migliorare la leggibilità.

Per altre informazioni su queste modifiche, vedere [Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune](whats-new-in-intune-app-ui.md).

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>I dispositivi non gestiti possono accedere alle app assegnate <!--664691-->

Nell'ambito delle modifiche di progettazione nel sito Web del portale aziendale, gli utenti iOS e Android potranno installare le app assegnate come "disponibili senza registrazione" nei dispositivi non gestiti. Usando le credenziali di Intune, gli utenti potranno accedere al sito Web del portale aziendale e visualizzare l'elenco delle app assegnate. È possibile eseguire il download di pacchetti di app "disponibili senza registrazione" dal sito Web del portale aziendale. Le app che richiedono la registrazione per poter essere installate non sono interessate da questa modifica poiché agli utenti viene richiesto di registrare il dispositivo per installare le app.

### <a name="signing-script-for-windows-10-company-portal---941642--"></a>Script di firma per l'app Portale aziendale di Windows 10<!--941642-->

Se è necessario scaricare e trasferire localmente l'app Portale aziendale di Windows 10, è ora disponibile uno script per semplificare e ottimizzare il processo di firma dell'app per l'organizzazione.   Per scaricare lo script e le relative istruzioni d'uso, vedere [Microsoft Intune Signing Script for Windows 10 Company Portal](https://aka.ms/win10cpscript) (Script di firma di Microsoft Intune per l'app Portale aziendale di Windows 10) nella raccolta TechNet. Per altre informazioni su questo annuncio, vedere [Updating your Windows 10 Company Portal app](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) (Aggiornamento dell'app Portale aziendale di Windows 10) nel blog del team di supporto di Intune.


## <a name="notices"></a>Notifiche

### <a name="improved-support-for-android-users-based-in-china---720444--"></a>Supporto migliorato per gli utenti Android in Cina <!--720444-->

A causa dell'assenza di Google Play Store in Cina, i dispositivi Android devono ottenere le app dai marketplace cinesi. L'app Portale aziendale supporterà questo flusso di lavoro reindirizzando gli utenti Android in Cina per scaricare le app Portale aziendale e Outlook dagli app store locali. Ciò consentirà di migliorare l'esperienza utente quando sono abilitati i criteri di accesso condizionale, per la gestione dei dispositivi e delle applicazioni mobili. Le app Portale aziendale e Outlook per Android sono disponibili negli app store cinesi seguenti:

- [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
- [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
- [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
- [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
- [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

### <a name="best-practice-make-sure-your-company-portal-apps-are-up-to-date---879465--"></a>Procedura consigliata: verificare che le app Portale aziendale siano aggiornate <!--879465-->

Nel mese di dicembre 2016 è stato rilasciato un aggiornamento che imponeva l'uso di Multi-Factor Authentication (MFA) a un gruppo di utenti che registrano un dispositivo iOS, Android, Windows 8.1+ o Windows Phone 8.1+. Questa funzionalità non può essere usata senza determinate versioni di base dell'app Portale aziendale per Android (5.0.3419.0+) e iOS (2.1.17+).

Microsoft è costantemente impegnata a migliorare Intune introducendo nuove funzioni sia per la console sia per le app Portale aziendale su tutte le piattaforme supportate. Pertanto, Microsoft rilascia solo le correzioni relative ai problemi rilevati nella versione corrente dell'app Portale aziendale. Per un'esperienza utente ottimale è quindi consigliabile usare le versioni più recenti delle app Portale aziendale.

>[!Tip]
> Chiedere agli utenti di impostare i dispositivi in modo da aggiornare automaticamente le app dallo Store appropriato. Se si è resa disponibile l'app Portale aziendale di Android su una condivisione di rete, è possibile scaricare la versione più recente dall'[Area download Microsoft](https://www.microsoft.com/download/details.aspx?id=49140).

### <a name="microsoft-teams-is-now-enabled-for-mam-on-ios-and-android"></a>Microsoft Teams è ora abilitato per MAM su iOS e Android

Microsoft ha annunciato la disponibilità generale di Microsoft Teams. Nelle app Microsoft Teams aggiornate per iOS e Android sono ora abilitate le funzionalità di gestione delle app mobili (MAM, Mobile App Management) di Intune. È così possibile consentire ai team di passare liberamente da un dispositivo all'altro, garantendo la protezione delle conversazioni e dei dati aziendali a ogni cambio di dispositivo. Per altre informazioni, vedere [l'annuncio relativo a Microsoft Teams](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) nel blog di Enterprise Mobility + Security.


## <a name="whats-new-in-the-public-preview-of-the-intune-admin-experience-on-azure---736542--"></a>Novità dell'anteprima pubblica dell'esperienza di amministrazione di Intune in Azure <!--736542-->

All'inizio del 2017 è prevista la migrazione dell'intera esperienza di amministrazione in Azure e ciò consentirà la gestione efficiente e integrata dei flussi di lavoro principali di EMS su una piattaforma di servizi moderna ed estendibile tramite le API Graph.

I nuovi tenant per la valutazione inizieranno a visualizzare l'anteprima pubblica della nuova esperienza di amministrazione nel portale di Azure già questo mese. Durante il periodo di anteprima, le funzionalità e la parità con la console di Intune esistente verranno fornite in modo iterativo.

L'esperienza di amministrazione nel portale di Azure userà la nuova funzionalità di raggruppamento e targeting già annunciata. Dopo la migrazione di un tenant esistente alla nuova esperienza di raggruppamento verrà eseguita anche la migrazione alla versione di anteprima della nuova esperienza di amministrazione. Nel frattempo, se si vogliono testare o esaminare le nuove funzionalità prima della migrazione del tenant, è possibile iscriversi per richiedere un nuovo account di prova di Intune oppure consultare la [nuova documentazione](https://docs.microsoft.com/intune-azure/introduction/whats-new).

> [!Note]
> È in corso l'implementazione degli aggiornamenti di questo mese per il portale di anteprima di Azure. Queste modifiche, tuttavia, potrebbero non essere disponibili immediatamente a causa della modalità di implementazione del servizio Intune.  Alcuni componenti del servizio devono essere aggiornati in sequenza prima che le nuove funzionalità del portale siano disponibili. Cercare gli aggiornamenti relativi al portale di anteprima di Azure a mano a mano che verranno implementati nel corso del mese. Per l'elenco completo delle modifiche, vedere [Novità dell'anteprima di Microsoft Intune](/intune-azure/introduction/whats-new).

## <a name="whats-coming"></a>Sviluppi futuri

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple richiederà aggiornamenti per Application Transport Security <!--748318-->

A partire dalla primavera 2017, Apple ha annunciato che imporrà requisiti specifici per Application Transport Security (ATS). Questa tecnologia viene usata per applicare criteri di sicurezza più rigorosi a tutte le comunicazioni delle app tramite HTTPS. Questa modifica interessa i clienti di Intune che usano le app del portale aziendale per iOS. Per informazioni più dettagliate, leggere il [blog del supporto di Intune](https://aka.ms/compportalats).

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novità dell'anteprima di Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [What's new in the Company Portal UI](https://docs.microsoft.com/intune/whats-new/whats-new-in-company-portal-ui) (Novità nell'interfaccia utente del portale aziendale)
* [Archivio delle novità](whats-new-archive.md)

