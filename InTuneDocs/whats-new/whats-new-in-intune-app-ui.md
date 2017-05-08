---
title: Aggiornamenti dell&quot;interfaccia utente per le applicazioni degli utenti finali in Intune | Microsoft Docs
description: "Cosa è cambiato nell&quot;interfaccia utente per le applicazioni usate nei dispositivi degli utenti finali con Intune."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/26/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 84c6c9ddeeff3570d0b00364063e43105141de0f
ms.contentlocale: it-it
ms.lasthandoff: 04/27/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Aggiornamenti dell'interfaccia utente per le applicazioni degli utenti finali in Intune
Informazioni su quali aggiornamenti sono stati apportati all'interfaccia utente per le app che gli utenti finali vedranno in questa versione di Microsoft Intune. Queste informazioni sono utili ai fini delle comunicazioni agli utenti e nell'aggiornamento della documentazione a supporto della distribuzione. Possono essere anche di aiuto per capire come risolvere al meglio eventuali problemi che riscontrano gli utenti e indicare loro se richiedere assistenza tramite il portale aziendale.

> [!Note]
> Si noti che le immagini seguenti sono anteprime e che il prodotto annunciato potrebbe differire dalle versioni presentate.

## <a name="april-2017"></a>Aprile 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Migliorata l'esperienza di accesso nelle app del portale aziendale per tutte le piattaforme <!--User Story 1132123-->

Microsoft sta migliorando l'esperienza di accesso per le app del portale aziendale di Intune per Android, iOS e Windows.  Non appena questa modifica viene apportata con Azure AD, la nuova esperienza utente apparirà automaticamente su tutte le piattaforme per l'app del portale aziendale. Ora gli utenti possono anche accedere al portale aziendale da un altro dispositivo con un codice generato monouso. Ciò è particolarmente utile nei casi in cui gli utenti devono accedere senza credenziali.  

Di seguito sono illustrate l'esperienza di accesso precedente, la nuova esperienza di accesso con credenziali e la nuova esperienza di accesso da un altro dispositivo.

__Esperienza di accesso precedente__

![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Dopo aver toccato Accedi, l'utente immette le proprie credenziali in questa pagina, che richiede l'indirizzo di posta elettronica e la password dell'utente e offre diversi modi per risolvere gli errori relativi alle password.](./media/cp_ios_aad_signin_before_1704_002.png)

![Dopo aver specificato la password, l'app portale aziendale esegue l'accesso, operazione indicata da una barra di caricamento.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nuova esperienza di accesso__

![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![Viene chiesto all'utente di indicare solo l'indirizzo di posta elettronica anziché l'indirizzo di posta elettronica e la password nella stessa schermata.](./media/cp_ios_aad_signin_after_1704_002.png)

![La password verrà richiesta all'utente dopo che l'indirizzo di posta elettronica è stato accettato.](./media/cp_ios_aad_signin_after_1704_003.png)

__Nuova esperienza di accesso con accesso da un altro dispositivo__

![La pagina di accesso del portale aziendale, con un'icona di una persona davanti a una rappresentazione grafica di un sito Web. Sotto è visibile il pulsante "Accedi". Un collegamento nella parte inferiore porta alle informazioni sulla privacy e sui cookie di Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Toccare il collegamento __Accesso da un altro dispositivo__.

![Viene chiesto all'utente di indicare solo l'indirizzo di posta elettronica anziché l'indirizzo di posta elettronica e la password nella stessa schermata. Il collegamento sotto il campo dell'indirizzo di posta elettronica indica "Accesso da un altro dispositivo".](./media/cp_ios_aad_signin_from_another_device_after_1704_002.png)

![Viene indicato come passare alla pagina aka.ms/devicelogin con un passcode univoco dal computer di lavoro, quindi come usare il codice per l'accesso.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Avviare un browser e passare a [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Un'immagine del browser dell'utente nel computer di lavoro anziché nell'app portale aziendale. Nella pagina "Accesso dispositivo" visualizzata viene chiesto all'utente di immettere il codice ricevuto nell'app portale aziendale.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Immettere il codice visto nell'app portale aziendale. Quando si seleziona __Continua__ sarà possibile eseguire l'autenticazione usando qualsiasi metodo supportato dall'azienda, ad esempio una smart card.

![L'utente ha immesso il codice univoco nel campo e il sito "Accesso dispositivo" ha chiesto di confermare che il portale aziendale di Intune è l'app corretta per la ricezione dell'autorizzazione ad accedere.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Una pagina di conferma indica che l'utente ha eseguito l'accesso all'app portale aziendale sul proprio dispositivo e che questa pagina può essere chiusa.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

L'app portale aziendale avvia la procedura di accesso.

![Terminato il processo di autenticazione, l'app portale aziendale esegue l'accesso, visualizzando una barra di caricamento.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Nuove icone per Managed Browser e il portale aziendale <!--918433, 918431-->

Managed Browser disporrà di icone aggiornate per le versioni Android e iOS dell'app. La nuova icona conterrà il logo di Intune aggiornato, in modo da renderla più coerente con le altre app in Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
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
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Stato di installazione delle app migliorato per l'app Portale aziendale di Windows 10 <!--676495-->
Nell'app Portale aziendale di Windows 10 è ora disponibile un indicatore di stato per tutte le installazioni di app moderne avviate dal portale aziendale.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_win10_install_status_before_1704.png" alt="An image of the previous version of the loading screen, where the status simply said 'installing.'" width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_win10_install_status_after_1704.png" alt="An image of the updated version of the loading screen, which now shows an install progress bar." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

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
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Gennaio 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Aggiornamento del sito Web del portale aziendale <!--753980, announced 1701-->
A partire da febbraio, il sito Web del portale aziendale supporterà le app destinate agli utenti che non hanno dispositivi gestiti. Il sito Web verrà allineato agli altri prodotti e servizi Microsoft con una nuova combinazione colori a contrasto, illustrazioni dinamiche e un "hamburger menu". ![Immagine dell'"hamburger menu" aggiunto nell'angolo superiore sinistro del sito Web del portale aziendale](./media/CP_hamburger_menu.png) che conterrà i dettagli di contatto del supporto tecnico e informazioni sui dispositivi gestiti esistenti. La pagina di destinazione verrà riorganizzata per evidenziare le applicazioni disponibili per gli utenti, con sequenze video per le app in primo piano e aggiornate di recente.

![L'immagine a sinistra rappresenta la versione corrente del sito Web del portale aziendale con le versioni precedenti delle visualizzazioni App, Dispositivi personali In primo piano e Categorie. L'immagine a destra rappresenta la versione aggiornata del sito Web del portale aziendale con una presentazione delle app aggiornata, l'elenco delle app pubblicate di recente e la visualizzazione Categorie aggiornata.](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>Vedere anche
* [Blog di Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Guida di orientamento a Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novità dell'anteprima di Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Archivio delle novità](whats-new-archive.md)

