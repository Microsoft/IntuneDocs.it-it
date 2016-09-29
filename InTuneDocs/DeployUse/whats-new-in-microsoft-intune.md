---
title: "Novità | Microsoft Intune"
description: "Questo articolo presenta le novità di questo mese e delle versioni precedenti di Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 03a5dd14b854fedf7e2cb5b949580960a0eab9de
ms.openlocfilehash: 1d09e5a0adb3ecfa8f2d64f668ea7ff16bdf31fa


---

# Novità di Microsoft Intune - Settembre
Di seguito sono illustrate le novità di questa versione di Microsoft Intune, oltre alle prossime modifiche che si consiglia di pianificare e a informazioni sulle versioni precedenti.

Tutte queste funzionalità saranno supportate per le distribuzioni ibride dei clienti (Configuration Manager con Intune). Per altre informazioni sulle nuove funzionalità ibride, vedere la [pagina Novità per le funzionalità ibride](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT]
>Post di blog: Ensuring mobile devices are up to date using Microsoft Intune (Verifica dell'aggiornamento dei dispositivi mobili con Microsoft Intune)<br>
>Dopo le recenti infezioni da malware "Trident" sui dispositivi iOS, è stato pubblicato un nuovo post di blog, [Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) (Verifica dell'aggiornamento dei dispositivi mobili con Microsoft Intune) che descrive come usare Intune per la protezione e l'aggiornamento dei dispositivi.

## Supporto di iOS 10
Gli scenari MDM e MAM Intune esistenti sono compatibili con iOS 10. Per suggerimenti, consultare il [Blog del Team di supporto Intune](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

## Lo strumento di wrapping delle app supporta MAM senza registrazione del dispositivo per Android e iOS
Lo strumento di wrapping delle app Intune è uno strumento da riga di comando usato per abilitare le app line-of-business (LOB) MAM Intune per iOS e Android. È il modo più semplice per incorporare dell'SDK per MAM Intune nell'app, in modo che l'app possa applicare i criteri MAM distribuiti attraverso Intune. Usando i criteri MAM, è possibile:

1. Crittografare i dati dell'app.
2. Richiedere all'information worker di immettere un PIN quando si avvia l'app.
3. Consentire all'app di trasferire i dati solo ad altre app gestite.
4. Impedire all'app di eseguire il backup dei dati in Android, iTunes e iCloud.
5. Consentire solo Taglia, Copia e Incolla in e da altre app gestite.

L'anteprima pubblica dello strumento di wrapping delle app di Intune supporta ora MAM senza registrazione dei dispositivi nelle app LOB interne in iOS e Android. Ciò significa che gli utenti finali non devono registrare i propri dispositivi con Intune per usare le app LOB abilitate per MAM.

Chiunque può testare il software in anteprima pubblica e leggere l'utile documentazione, che si trova in GitHub ai seguenti indirizzi:

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Prima di installare e usare la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS è necessario:

* Esaminare le condizioni di licenza Microsoft per la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android e iOS
* Stampare e conservare una copia delle condizioni di licenza. Scaricando e usando la versione non definitiva dello strumento di wrapping delle app di Microsoft Intune per Android si accettano tali condizioni di licenza. Qualora l'utente non le accetti, non potrà usare il software.
<!---TFS 1235607--->

## I gruppi di Intune inizieranno la transizione in Azure Active Directory a settembre
Alcuni nuovi account di Intune useranno i gruppi di sicurezza di Azure Active Directory anziché i gruppi di utenti di Intune. Sarà possibile sapere che si lavora con i gruppi di sicurezza perché la pagina dei gruppi del portale Intune avrà un collegamento che indirizza al portale di gestione di Azure.

## Integrazione di Lookout per proteggere i dispositivi Android
Microsoft sta integrando la soluzione di protezione dalle minacce per dispositivi mobili Lookout per proteggere i dispositivi mobili Android grazie al rilevamento di malware, app rischiose e altro ancora. La soluzione Lookout consente di determinare il livello di minaccia, che è configurabile. È possibile creare una regola dei criteri di conformità in Intune per determinare la conformità del dispositivo in base alla valutazione del rischio da parte di Lookout. Con i criteri di accesso condizionale è possibile consentire o bloccare l'accesso alle risorse aziendali in base allo stato di conformità del dispositivo.

Agli utenti finali dei dispositivi non conformi verrà richiesto di eseguire la registrazione e sarà necessario installare l'applicazione Lookout for Work nei dispositivi Android, attivare l'app e correggere le minacce segnalate nell'applicazione Lookout for Work per ottenere l'accesso. Per altre informazioni, vedere [Limitare l'accesso in base al rischio per dispositivi, rete e applicazioni](restrict-access-based-on-device-network-app-risk.md).


## Aggiornamenti del portale aziendale

### Android

**Aggiunta di "Notifiche" al portale aziendale per Android**<br/>
È stata aggiunta una nuova icona Notifiche al portale aziendale per Android nella home page. Toccando l'icona si accede alla pagina Notifiche in cui gli utenti finali possono visualizzare tutti gli elementi che richiedono attenzione nell'app Portale aziendale, ad esempio la non conformità del dispositivo, l'aggiornamento della registrazione e l'attivazione della registrazione. L'app del portale aziendale iOS dispone già di questa funzionalità delle notifiche. Con la nuova pagina Notifiche, all'utente non verrà visualizzata la pagina Configurazione dell'accesso aziendale ogni volta che avvia o riprende l'esecuzione del portale aziendale, a condizione che il dispositivo sia già registrato. Se si crea una propria guida per l'utente, aggiornare la documentazione per riportare questa modifica. Gli screenshot aggiornati sono disponibili [qui](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->


### iOS
**Modifiche al supporto per l'app Portale aziendale per iOS**<br/>
Tutti gli utenti dell'app del portale aziendale di Microsoft Intune per iOS devono ora usare la versione più recente dell'app. I nuovi utenti possono scaricare solo la versione più recente e gli utenti attuali devono aggiornarla. La versione più recente richiede iOS 8.0 o versioni successive, quindi gli utenti dei dispositivi che eseguono versioni precedenti di iOS non potranno usare il portale aziendale o eseguire la registrazione finché non aggiornano i dispositivi a iOS 8.0 o versione successiva e aggiornano l'app del portale aziendale alla versione più recente. I dispositivi registrati che eseguono versioni di iOS precedenti a 8.0 continueranno a essere gestiti ed elencati nella Console di amministrazione di Intune.
<!---TFS 1283165--->

**Miglioramenti della modalità di recupero delle app per gli utenti finali di iOS**<br/>
Le modifiche seguenti sono state apportate ai riquadri delle app nell'app Portale aziendale in modo che iOS indirizzi gli utenti con visualizzazioni diverse per tutte le app in un'unica posizione, il sito Web del portale aziendale. Le restrizioni di Apple impediscono alle app dell'app store line-of-business e gestite di essere elencate nell'app Portale aziendale e richiedono agli utenti di visitare visualizzazioni diverse per trovare le proprie app.

- Il riquadro **App aziendali** indirizzava in precedenza a un elenco di tutte le app nella scheda TUTTE del sito Web del portale aziendale e continuerà a funzionare allo stesso modo. Il nome del riquadro è diventato **Tutte le app**.
- Il riquadro **Altre app** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca tutte le app che Apple consente di visualizzare all'app Portale aziendale. Il nome del riquadro è diventato **App in evidenza** e toccandolo gli utenti verranno indirizzati alla scheda IN EVIDENZA del sito Web del portale aziendale.
-  Il riquadro **Categorie** indirizzava in precedenza a una visualizzazione, all'interno dell'app Portale aziendale, che elenca le categorie di app. Il nome del riquadro non è cambiato, ma ora punta alla scheda CATEGORIE del sito Web del portale aziendale.
È possibile trovare [qui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186) le schermate aggiornate.
<!---TFS 1317133--->

**Chiedere conferma per installare l'app Managed Browser per iOS se i professionisti IT impostano tale requisito per un'app**<br/>
Se è stata configurata l'apertura di una clip Web solo nell'app Managed Browser e questa non è installata in un dispositivo, l'app Portale aziendale sul dispositivo chiederà all'utente di installare il browser gestito prima di poter installare la clip Web. 
<!---TFS 1228570--->

### Windows
**È stato aggiunto un pulsante Feedback all'app del portale aziendale di Windows Phone 8.1**<br/>
L'app del portale aziendale di Windows Phone 8.1 consente agli utenti di inviare feedback relativi all'app con il nuovo pulsante Invia il feedback. Per visualizzare il pulsante, gli utenti toccano il menu "tre punti" nella parte inferiore destra della schermata dell'app del portale aziendale e quindi toccano **Invia il feedback**. I feedback raccolti in modo anonimo consentiranno a Microsoft di migliorare l'esperienza dell'app del portale aziendale per gli utenti.
<!---TFS 1317806--->


## Sviluppi futuri

### Transizione dai gruppi di Intune ai gruppi di Azure Active Directory
Intune sta creando una nuova esperienza di gestione dei gruppi che usa i gruppi di sicurezza di Azure Active Directory (AAD) come gruppi di utenti e dispositivi in Intune. Questi gruppi verranno usati per la gestione dei gruppi, la distribuzione dei criteri e la distribuzione dei profili **con l'introduzione del nuovo portale di amministrazione di Intune basato su Azure**.

Questa nuova esperienza consentirà di evitare di duplicare i gruppi tra i servizi, **garantirà l'accesso ad alcune nuove funzionalità dei gruppi di Azure Active Directory Premium (AADP)** e offrirà estendibilità tramite PowerShell e Graph. Consentirà inoltre di unificare l'esperienza di gestione dei gruppi per tutta la gestione della mobilità aziendale.

Per abilitare il passaggio ai gruppi di sicurezza, la **console di amministrazione corrente** verrà sottoposta ad alcune modifiche. **Queste modifiche e l'uso dei gruppi di sicurezza di AAD saranno indicati nella documentazione di Intune**.

I clienti che non hanno familiarità con Intune visualizzeranno **alcune delle modifiche ai gruppi di sicurezza prima di dei tenant correnti**.

Oltre alle modifiche apportate alla gestione dei gruppi, **verranno deprecate le funzionalità seguenti**:
- Esclusione di membri o gruppi durante la creazione di un nuovo gruppo
- Gruppi **Utenti non raggruppati** e **Dispositivi non raggruppati**
- **Gestisci gruppi** nel ruolo di amministratore del servizio
- Avvisi personalizzati in base al gruppo per le regole di notifica
- Calcolo pivot per gruppi nei report
<!--- TFS 1295329--->

### Nuovi criteri di accesso condizionale per le app per Exchange Online e SharePoint Online
Sarà possibile limitare l'accesso a Exchange Online e SharePoint Online in modo che l'accesso possa provenire solo da app per dispositivi mobili Office quali Outlook, Word, Excel e OneDrive. Questa nuova funzionalità si abbina perfettamente con i criteri di gestione delle app per dispositivi mobili (MAM) di Intune perché è possibile bloccare l'accesso ai client di posta predefiniti o ad altre app che non sono state configurate con i criteri MAM Intune. In questo modo gli utenti accedono ai dati dell'organizzazione con app che possono essere protette con MAM Intune. Per un'introduzione alla gestione delle app per dispositivi mobili Intune, visitare il portale di Azure. Cercare la nuova sezione Accesso condizionale nel pannello "Impostazioni".



### Deprecazione del servizio

- **Le app del portale aziendale per Windows 8 e Windows Phone 8 verranno deprecate** <br/>
A partire da ottobre 2016, il supporto di Microsoft Intune per le app del portale aziendale di Windows Phone 8 e Windows 8 verrà deprecato. Verrà anche deprecato il supporto di Microsoft Intune per la piattaforma Windows Phone 8. Di conseguenza, non sarà possibile registrare o aggiornare i dispositivi Windows Phone 8. È possibile continuare a gestire i dispositivi Windows Phone 8 e Windows 8 che sono già registrati. Aggiornare i dispositivi Windows Phone 8 e Windows 8 a Windows 8.1 e Windows Phone 8.1 e usare le app del portale aziendale per Windows Phone 8.1 e Windows 8.1 corrispondenti per continuare a distribuire le app a tali dispositivi senza interruzioni.



### Guida di orientamento per il cloud
Per ottenere informazioni sugli sviluppi futuri per Intune, vedere la [guida di orientamento Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).


## Versioni precedenti di Intune
Per vedere cosa è stato rilasciato in Intune negli ultimi sei mesi, leggere l'articolo [Versioni precedenti di Intune](previous-intune-releases.md).

### Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Sep16_HO3-->


