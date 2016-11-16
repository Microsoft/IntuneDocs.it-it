---
title: "Archivio novità | Microsoft Intune"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 861b5ea3bb0772d2853942e2b3f11f607dad3774
ms.openlocfilehash: 25128cfe93280e38a03779a7e6f38ddeb3c15612


---
# <a name="whats-new-archive"></a>Archivio delle novità

Questa pagina è un archivio degli annunci recenti pubblicati in [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).

## <a name="september-2016"></a>Settembre 2016
### <a name="new-features-announcements-and-information"></a>Nuove funzionalità, annunci e informazioni
* [Accesso condizionale di Windows](#windows-conditional-access)
* [Supporto di iOS 10](#ios-10-support)
* [Lo strumento di wrapping delle app supporta MAM senza registrazione del dispositivo per Android e iOS](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [I gruppi di Intune inizieranno la transizione in Azure Active Directory a settembre](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Integrazione di Lookout per proteggere i dispositivi Android](#lookout-integration-to-protect-android-devices)
* [Aggiornamenti del portale aziendale per Android, iOS e Windows](#company-portal-updates)
* [Glossario di Intune](#intune-glossary)
* [Sviluppi futuri](#whats-coming)

### <a name="windows-conditional-access"></a>Accesso condizionale di Windows
È ora possibile creare criteri di accesso condizionale tramite la console di amministrazione di Intune per impedire l'accesso a Exchange Online e SharePoint Online ai PC Windows. È inoltre possibile creare criteri di accesso condizionale per bloccare l'accesso alle applicazioni universali e desktop di Office.

### <a name="ios-10-support"></a>Supporto di iOS 10
Gli scenari MDM e MAM Intune esistenti sono compatibili con iOS 10. Per suggerimenti, consultare il [Blog del Team di supporto Intune](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

### <a name="app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios"></a>Lo strumento di wrapping delle app supporta MAM senza registrazione del dispositivo per Android e iOS
Lo strumento di wrapping delle app Intune è uno strumento da riga di comando usato per abilitare le app line-of-business (LOB) MAM Intune per iOS e Android. È il modo più semplice per incorporare dell'SDK per MAM Intune nell'app, in modo che l'app possa applicare i criteri MAM distribuiti attraverso Intune. Usando i criteri MAM, è possibile:

1. Crittografare i dati dell'app.
2. Richiedere all'information worker di immettere un PIN quando si avvia l'app.
3. Consentire all'app di trasferire i dati solo ad altre app gestite.
4. Impedire all'app di eseguire il backup dei dati in Android, iTunes e iCloud.
5. Consentire solo Taglia, Copia e Incolla in e da altre app gestite.

L'anteprima pubblica dello strumento di wrapping delle app di Intune supporta ora MAM senza registrazione dei dispositivi nelle app LOB interne in iOS e Android. Ciò significa che gli utenti finali non devono registrare i propri dispositivi con Intune per usare le app LOB abilitate per MAM.

Chiunque può testare il software in anteprima pubblica e leggere l'utile documentazione, che si trova in GitHub ai seguenti indirizzi:

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

<p style="margin-left: 40px">http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Prima di installare e usare la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS è necessario:

* Esaminare le condizioni di licenza Microsoft per la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS
* Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android si accettano tali condizioni di licenza. Qualora l'utente non le accetti, non potrà usare il software.
<!---TFS 1235607--->

### <a name="intune-groups-begin-transitioning-to-azure-active-directory-in-september"></a>I gruppi di Intune inizieranno la transizione in Azure Active Directory a settembre
Alcuni nuovi account di Intune useranno i gruppi di sicurezza di Azure Active Directory anziché i gruppi di utenti di Intune. Sarà possibile sapere che si lavora con i gruppi di sicurezza perché la pagina dei gruppi del portale Intune avrà un collegamento che indirizza al portale di gestione di Azure.

### <a name="lookout-integration-to-protect-android-devices"></a>Integrazione di Lookout per proteggere i dispositivi Android
Microsoft sta integrando la soluzione di protezione dalle minacce per dispositivi mobili Lookout per proteggere i dispositivi mobili Android grazie al rilevamento di malware, app rischiose e altro ancora. La soluzione Lookout consente di determinare il livello di minaccia, che è configurabile. È possibile creare una regola dei criteri di conformità in Intune per determinare la conformità del dispositivo in base alla valutazione del rischio da parte di Lookout. Con i criteri di accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali in base allo stato di conformità del dispositivo.

Agli utenti finali dei dispositivi non conformi verrà richiesto di eseguire la registrazione e sarà necessario installare l'applicazione Lookout for Work nei dispositivi Android, attivare l'app e correggere le minacce segnalate nell'applicazione Lookout for Work per ottenere l'accesso. Per altre informazioni, vedere [Limitare l'accesso in base al rischio per dispositivi, rete e applicazioni](restrict-access-based-on-device-network-app-risk.md).


### <a name="company-portal-updates"></a>Aggiornamenti del portale aziendale

__Android__

<p style="margin-left: 40px">**Aggiunta di "Notifiche" al portale aziendale per Android**<br/>
<p style="margin-left: 40px">È stata aggiunta una nuova icona Notifiche al portale aziendale per Android nella home page. Toccando l'icona si accede alla pagina Notifiche in cui gli utenti finali possono visualizzare tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. L'app del portale aziendale iOS dispone già di questa funzionalità delle notifiche. Con la nuova pagina Notifiche, all'utente non verrà visualizzata la pagina Configurazione dell'accesso aziendale ogni volta che avvia o riprende l'esecuzione del portale aziendale, a condizione che il dispositivo sia già registrato. Se si crea una propria guida per l'utente, aggiornare la documentazione per riportare questa modifica. Gli screenshot aggiornati sono disponibili [qui](https://aka.ms/androidcpupdate).  

__iOS__
<p style="margin-left: 40px">**Modifiche al supporto dell'app Portale aziendale per iOS**<br/>
<p style="margin-left: 40px">Tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS devono ora usare la versione più recente dell'app. I nuovi utenti possono scaricare solo la versione più recente e gli utenti attuali devono aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, quindi gli utenti dei dispositivi che eseguono versioni precedenti di iOS non potranno usare il portale aziendale o eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.
<!---TFS 1283165--->

<p style="margin-left: 40px">**Miglioramenti della modalità di recupero delle app per gli utenti finali di iOS**<br/>
<p style="margin-left: 40px">Le modifiche seguenti sono state apportate ai riquadri delle app nell'app Portale aziendale in modo che iOS indirizzi gli utenti con visualizzazioni diverse per tutte le app in un'unica posizione, il sito Web del portale aziendale. Le restrizioni di Apple impediscono alle app dell'app store line-of-business e gestite di essere elencate nell'app Portale aziendale e richiedono agli utenti di visitare visualizzazioni diverse per trovare le proprie app.

<p style="margin-left: 40px">Il riquadro **App aziendali** indirizzava in precedenza a un elenco di tutte le app nella scheda TUTTE del sito Web del portale aziendale e continuerà a funzionare allo stesso modo. Il nome del riquadro è diventato **Tutte le app**.

<p style="margin-left: 40px">Il riquadro **Altre app** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca tutte le app che Apple consente di visualizzare all'app Portale aziendale. Il nome del riquadro è diventato **App in evidenza** e toccandolo gli utenti verranno indirizzati alla scheda IN EVIDENZA del sito Web del portale aziendale.

<p style="margin-left: 40px">Il riquadro **Categorie** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca le categorie di app. Il nome del riquadro non è cambiato, ma ora punta alla scheda CATEGORIE del sito Web del portale aziendale. È possibile trovare [qui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186) le schermate aggiornate.
  <!---TFS 1317133--->

<p style="margin-left: 40px">**Chiedere conferma per installare l'app Managed Browser per iOS se i professionisti IT impostano tale requisito per un'app**<br/>
<p style="margin-left: 40px">Se è stata configurata l'apertura di una clip Web solo nell'app Managed Browser e questa non è installata in un dispositivo, l'app Portale aziendale sul dispositivo chiederà all'utente di installare il browser gestito prima di poter installare la clip Web.
  <!---TFS 1228570--->

__Windows__
<p style="margin-left: 40px">**È stato aggiunto un pulsante Feedback all'app Portale aziendale per Windows Phone 8.1**<br/>
<p style="margin-left: 40px">L'app del portale aziendale di Windows Phone 8.1 consente agli utenti di inviare feedback relativi all'app con il nuovo pulsante Invia il feedback. Per visualizzare il pulsante, gli utenti toccano il menu "tre punti" nella parte inferiore destra della schermata dell'app del portale aziendale e quindi toccano **Invia il feedback**. I feedback raccolti in modo anonimo consentiranno a Microsoft di migliorare l'esperienza dell'app del portale aziendale per gli utenti.
<!---TFS 1317806--->

### <a name="intune-glossarybr"></a>Glossario di Intune</br>
È stato aggiunto un nuovo [argomento glossario](https://docs.microsoft.com/intune/understand-explore/intune-glossary) alla libreria per consentire una migliore comprensione di alcuni dei termini usati nel prodotto Intune.

### <a name="see-also"></a>Vedere anche
Per informazioni dettagliate sugli ultimi sviluppi, vedere [Novità di Microsoft Intune](whats-new-in-microsoft-intune.md).



<!--HONumber=Nov16_HO2-->


