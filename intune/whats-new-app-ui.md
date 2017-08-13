---
title: Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune
description: "Cosa è cambiato nell'interfaccia utente per le applicazioni usate nei dispositivi degli utenti finali con Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 948a7d2e4e0ad80088d864708db5733f08db77c5
ms.sourcegitcommit: 79116d4c7f11bafc7c444fc9f5af80fa0b21224e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune
Informazioni su quali aggiornamenti sono stati apportati all'interfaccia utente per le app che gli utenti finali vedranno in questa versione di Microsoft Intune. Queste informazioni sono utili ai fini delle comunicazioni agli utenti e nell'aggiornamento della documentazione a supporto della distribuzione. Possono essere anche di aiuto per capire come risolvere al meglio eventuali problemi che riscontrano gli utenti e indicare loro se richiedere assistenza tramite il portale aziendale.

## <a name="week-of-july-31-2017"></a>Settimana del 31 luglio 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Migliorata l'esperienza di accesso nelle app del portale aziendale per tutte le piattaforme <!--User Story 1132123-->

Microsoft ha annunciato una modifica che verrà introdotta nei prossimi mesi e consentirà di migliorare l'esperienza di accesso per le app Portale aziendale di Intune per Android, iOS e Windows. Non appena questa modifica viene apportata con Azure AD, la nuova esperienza utente apparirà automaticamente su tutte le piattaforme per l'app del portale aziendale. Ora gli utenti possono anche accedere al portale aziendale da un altro dispositivo con un codice generato monouso. Ciò è particolarmente utile nei casi in cui gli utenti devono accedere senza credenziali.  

Di seguito sono illustrate l'esperienza di accesso precedente, la nuova esperienza di accesso con credenziali e la nuova esperienza di accesso da un altro dispositivo.

__Esperienza di accesso precedente__

![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Dopo aver toccato Accedi, l'utente immette le proprie credenziali in questa pagina, che richiede l'indirizzo di posta elettronica e la password dell'utente e offre diversi modi per risolvere gli errori relativi alle password.](./media/cp_ios_aad_signin_before_1704_002.png)

![Dopo aver specificato la password, l'app portale aziendale esegue l'accesso, operazione indicata da una barra di caricamento.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nuova esperienza di accesso__

![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![Viene chiesto all'utente di indicare solo l'indirizzo di posta elettronica anziché l'indirizzo di posta elettronica e la password nella stessa schermata.](./media/cp_ios_aad_signin_after_1704_002.png)

![La password verrà richiesta all'utente dopo che l'indirizzo di posta elettronica è stato accettato.](./media/cp_ios_aad_signin_after_1704_003.png)

![Terminato il processo di autenticazione, l'app portale aziendale esegue l'accesso, visualizzando una barra di caricamento.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Nuova esperienza di accesso con accesso da un altro dispositivo__

![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Toccare il collegamento __Accesso da un altro dispositivo__.

![Viene indicato come passare alla pagina aka.ms/devicelogin con un passcode univoco dal computer di lavoro, quindi come usare il codice per l'accesso.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Avviare un browser e passare a [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Un'immagine del browser dell'utente nel computer di lavoro anziché nell'app portale aziendale. Nella pagina "Accesso dispositivo" visualizzata viene chiesto all'utente di immettere il codice ricevuto nell'app portale aziendale.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Immettere il codice visto nell'app portale aziendale. Quando si seleziona __Continua__ sarà possibile eseguire l'autenticazione usando qualsiasi metodo supportato dall'azienda, ad esempio una smart card.

![L'utente ha immesso il codice univoco nel campo e il sito "Accesso dispositivo" ha chiesto di confermare che il portale aziendale di Intune è l'app corretta per la ricezione dell'autorizzazione ad accedere.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Una pagina di conferma indica che l'utente ha eseguito l'accesso all'app portale aziendale sul proprio dispositivo e che questa pagina può essere chiusa.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

L'app portale aziendale avvia la procedura di accesso.

![Terminato il processo di autenticazione, l'app portale aziendale esegue l'accesso, visualizzando una barra di caricamento.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

## <a name="week-of-june-12-2017"></a>Settimana del 12 giugno 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>L'app Portale aziendale per Android ora include una nuova esperienza utente finale per i criteri di protezione delle app <!--1305217-->
In base ai suggerimenti dei clienti, l'app Portale aziendale per Android è stata modificata e ora include un pulsante **Accesso al contenuto aziendale**. Con questa funzionalità gli utenti finali possono evitare il processo di registrazione per accedere solo ad app che supportano i criteri di protezione, una funzionalità di gestione delle applicazioni mobili di Intune.

L'utente può toccare il pulsante **Accesso al contenuto aziendale** anziché iniziare il processo di registrazione del dispositivo.

![Immagine dell'app Portale aziendale per Android che visualizza in caratteri grandi "Accesso al contenuto aziendale" al centro anziché le opzioni per la registrazione immediata (funzionalità standard)](./media/and_access_company_content_after_1706.png)

Viene visualizzato il sito Web Portale aziendale, dove l'utente può specificare le proprie credenziali per ottenere l'autorizzazione all'uso dell'app nel dispositivo.

![Immagine del sito Web Portale aziendale in cui viene confermato l'accesso.](./media/and_iwp_sign_in_auth_page_after_1706.png)

È comunque possibile registrare il dispositivo può per la gestione completa toccando il menu **Azione**.

![Immagine dell'app Portale aziendale per Android che visualizza il menu nell'angolo superiore destro dello schermo, con l'opzione che consente di registrare in ogni caso il dispositivo.](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Miglioramenti alla sincronizzazione di app con Windows 10 Creators Update <!--676505-->

L'app Portale aziendale per Windows 10 avvierà ora automaticamente una sincronizzazione per le richieste di installazione di app per dispositivi con Windows 10 Creators Update (1703). Ciò consente di limitare il problema di installazione di app quando lo stato è "In attesa di sincronizzazione". Gli utenti potranno inoltre avviare manualmente la sincronizzazione dall'app.

![Immagine dell'app Portale aziendale per Windows 10 in cui il download di Microsoft Word dall'app store del portale aziendale è in sospeso.](./media/w10_download_pending_after_1706.png)

![Immagine dell'app Portale aziendale per Windows 10 con il nuovo stato di sincronizzazione automatica e un messaggio di stato indicante che la sincronizzazione del dispositivo e il download dell'app sono in corso.](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nuova esperienza guidata per il portale aziendale di Windows 10 <!---1058938--->
L'app Portale aziendale per Windows 10 includerà un'esperienza guidata di Intune per i dispositivi che non sono stati identificati o registrati. La nuova esperienza fornisce istruzioni dettagliate che guidano l'utente nella procedura di registrazione in Azure Active Directory (obbligatoria per le funzionalità di accesso condizionale) e di registrazione MDM (obbligatoria per le funzionalità di gestione dei dispositivi). L'esperienza guidata sarà accessibile dalla home page del portale aziendale. Gli utenti possono continuare a usare l'app anche se non completano la registrazione, ma avranno a disposizione funzionalità limitate.

Questo aggiornamento è visibile solo nei dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 (build 1607) o versione successiva.

![Immagine della pagina di destinazione dell'app Portale aziendale di Windows 10 con un messaggio di stato al centro dell'elenco "Dispositivi" che indica all'utente che il dispositivo in uso in non è ancora stato configurato per l'uso aziendale e che l'utente deve selezionare il messaggio per avviare la configurazione.](./media/win10_guided_enroll_select_setup_after_1706.png)

![Immagine della pagina di configurazione dell'app Portale aziendale per Windows 10 con un messaggio indicante che per registrare il dispositivo per la gestione è necessario aggiungere un account aziendale al dispositivo.](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![Immagine della pagina Aggiungere un account aziendale a questo dispositivo dell'app Portale aziendale per Windows 10, che segnala all'utente che è necessario aprire l'app Impostazioni e selezionare "Connetti" per completare la registrazione. Dopo questa operazione, un messaggio indica che è necessario tornare all'app Portale aziendale per completare la registrazione.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Immagine della schermata Registra nella gestione dell'app Portale aziendale per Windows 10 che visualizza un messaggio di operazione completata, indicante che il dispositivo dell'utente è registrato e che per continuare è necessario toccare il pulsante "Avanti".](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![Immagine della schermata di completamento dell'app Portale aziendale per Windows 10, che comunica all'utente che il processo è stato completato e che il dispositivo è registrato e provvisto di un account aziendale.](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nuova azione di menu per rimuovere facilmente Portale aziendale <!--1164569-->
In risposta al feedback degli utenti, per l'app Portale aziendale per Android è stata aggiunta una nuova azione di menu per eseguire la rimozione di Portale aziendale dal dispositivo. Questa azione rimuove il dispositivo dalla gestione di Intune in modo che l'app possa essere rimossa dal dispositivo dall'utente.

![Immagine dell'app Portale aziendale per Android, con il menu Azione aperto nell'angolo in alto a destra. La nuova opzione "Remove company portal" (Rimuovi portale aziendale) è disponibile come terza opzione dopo "Profilo personale" e "Impostazioni" e prima di "Termini e condizioni", "Guida e commenti e suggerimenti" e "Informazioni su".](./media/android_remove_cp_menu_action_after_1705.png)

![Immagine della finestra di dialogo di conferma visualizzata dopo aver selezionato la nuova opzione "Remove company portal" (Rimuovi portale aziendale) dal menu Azione. Questa finestra di dialogo informa l'utente che rimuovendo Portale aziendale, il dispositivo non verrà più gestito dall'amministratore IT e potrebbe essere rimosso l'accesso a dati, app o posta elettronica aziendali. Viene quindi richiesto all'utente di confermare la rimozione dell'app Portale aziendale selezionando "Sì".](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="week-of-june-5-2017"></a>Settimana del 5 giugno 2017

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Miglioramenti dei riquadri dell'app Portale aziendale per iOS
È stata aggiornata la progettazione dei riquadri dell'app nella home page in modo che rispecchino il colore personalizzato impostato per Portale aziendale.

**Prima**

![Immagine dell'app Portale aziendale per iOS prima dell'aggiornamento, che mostra le immagini di riempimento predefinite per i riquadri "Tutte le app", "App in evidenza" e "Categorie".](./media/cp_ios_homepage_before_1705.png)

**Dopo**

![Immagine dell'app Portale aziendale per iOS dopo l'aggiornamento, che rispecchia ora la possibilità di selezionare qualsiasi colore appropriato per l'organizzazione.](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Selezione account ora disponibile per l'app Portale aziendale per iOS
Se gli utenti usano l'account aziendale o dell'istituto di istruzione per accedere ad altre app Microsoft nel dispositivo iOS, potrebbero ora visualizzare la nuova selezione account al primo accesso a Portale aziendale.

![Immagine della selezione account che mostra un utente di test "Robin Swanson" che sceglie uno dei suoi due indirizzi di posta elettronica. Sotto i due indirizzi è disponibile un pulsante che consente all'utente di accedere con un account diverso.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>Aprile 2017

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nuove icone per Managed Browser e il portale aziendale <!--918433, 918431-->

Managed Browser disporrà di icone aggiornate per le versioni Android e iOS dell'app. La nuova icona conterrà il logo di Intune aggiornato, in modo da renderla più coerente con le altre app in Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

Il portale aziendale disporrà inoltre di icone aggiornate per le versioni Android, iOS e Windows dell'app, per migliorare la coerenza con le altre app in EM+S. Queste icone verranno rilasciate gradualmente tra le piattaforme da aprile a fine maggio.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicatore di stato dell'accesso nel portale aziendale Android <!--953374-->

Un aggiornamento all'app Portale aziendale Android mostra un indicatore di stato dell'accesso quando l'utente avvia o riprende l'app. L'indicatore indica una progressione attraverso nuovi stati, a partire da "Connessione in corso...", ad "Accesso in corso..." e infine "Verifica dei requisiti di sicurezza in corso..." prima di consentire all'utente di accedere all'app.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Stato di installazione delle app migliorato per l'app Portale aziendale di Windows 10 <!--676495-->
L'app Portale aziendale di Windows 10 include ora una barra di stato dell'installazione nella pagina dei dettagli dell'app. Questa novità è supportata per le app moderne in dispositivi che eseguono l'Aggiornamento dell'anniversario di Windows 10 e versioni successive.

__Prima__ ![Immagine della versione precedente della schermata di caricamento, che indica semplicemente lo stato "Installazione in corso".](./media/cp_win10_install_status_before_1704.png)

__Dopo__ ![Immagine della versione aggiornata della schermata di caricamento, che ora visualizza una barra di stato dell'installazione.](./media/cp_win10_install_status_after_1704.png)

## <a name="february-2017"></a>Febbraio 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Nuova esperienza utente per l'app Portale aziendale per Android <!--621622, announced 1702-->
A partire da marzo, l'app Portale aziendale per Android seguirà le [linee guida di progettazione dei materiali](https://material.io/guidelines/material-design/introduction.html) per creare un aspetto più moderno. La nuova esperienza utente include i seguenti miglioramenti:

* __Colori__: i colori delle intestazioni delle schede possono essere impostati in base alla tavolozza dei colori personalizzata.

![A sinistra, un'immagine dell'app Portale aziendale per Android prima dell'aggiornamento. A destra, un'immagine dell'app Portale aziendale per Android dopo l'aggiornamento. Entrambe le immagini mostrano la scheda Dispositivi selezionata tra le tre schede disponibili App, Dispositivi e Contatta l'IT.](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Interfaccia__:i pulsanti __App in evidenza__ e __Tutte le app__ sono stati aggiornati nella scheda __App__. Il pulsante __Cerca__ è ora un pulsante di azione mobile.

![A sinistra, un'immagine dell'app Portale aziendale per Android prima dell'aggiornamento. A destra, un'immagine dell'app Portale aziendale per Android dopo l'aggiornamento. Entrambe le immagini mostrano la scheda App selezionata tra le tre schede disponibili App, Dispositivi e Contatta l'IT.](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navigazione__: Tutte le app mostra una visualizzazione a schede di __In evidenza__, __Tutte__ e __Categorie__ per una navigazione più semplice. __Contatta l'IT__ è stata semplificata per migliorare la leggibilità.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Gennaio 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Aggiornamento del sito Web del portale aziendale <!--753980, announced 1701-->
A partire da febbraio, il sito Web del portale aziendale supporterà le app destinate agli utenti che non hanno dispositivi gestiti. Il sito Web verrà allineato agli altri prodotti e servizi Microsoft con una nuova combinazione colori a contrasto, illustrazioni dinamiche e un "hamburger menu". ![Immagine dell'"hamburger menu" aggiunto nell'angolo superiore sinistro del sito Web del portale aziendale](./media/CP_hamburger_menu.png) che conterrà i dettagli di contatto del supporto tecnico e informazioni sui dispositivi gestiti esistenti. La pagina di destinazione verrà riorganizzata per evidenziare le applicazioni disponibili per gli utenti, con sequenze video per le app in primo piano e aggiornate di recente.

![L'immagine a sinistra rappresenta la versione corrente del sito Web del portale aziendale con le versioni precedenti delle visualizzazioni App, Dispositivi personali In primo piano e Categorie. L'immagine a destra rappresenta la versione aggiornata del sito Web del portale aziendale con una presentazione delle app aggiornata, l'elenco delle app pubblicate di recente e la visualizzazione Categorie aggiornata.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>Presto disponibile nell'interfaccia utente
Questi sono i piani per i miglioramenti previsti per l'esperienza utente tramite l'aggiornamento dell'interfaccia utente.

> [!Note]
> Si noti che le immagini seguenti potrebbero essere anteprime e che il prodotto annunciato potrebbe differire dalle versioni presentate.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-2--"></a>Aggiornamenti dell'interfaccia utente del sito Web del portale aziendale <!--1313244 part 2-->

__Aggiornamenti per le app in primo piano__ È stata aggiunta una pagina dedicata nel sito, nella quale gli utenti possono visualizzare le app che hanno scelto di mettere in primo piano e sono state apportate alcune modifiche all'interfaccia utente della sezione In primo piano nella home page.

![Riquadri colorati che mostrano le app. Si tratta di grandi quadrati a colori sotto ogni app, per i quali il colore viene derivato dal colore principale nel logo dell'app. La sezione "App in primo piano" è visualizzata lungo la parte superiore dell'app Portale aziendale.](./media/cp_win10_colorful_tiles_after_1708.png)

### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novità in Intune](https://docs.microsoft.com/intune/whats-new)
