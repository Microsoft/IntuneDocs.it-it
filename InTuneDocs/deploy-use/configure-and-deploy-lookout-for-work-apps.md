---
title: Distribuire l&quot;app Lookout for Work | Microsoft Intune
description: Configurare e distribuire l&quot;app Lookout for Work per Android.
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c59707ba2967b069dc30aee71d2642e91d71b23b
ms.openlocfilehash: 720fe241e7f1205dbad4b64af5cf7f16a80db23e


---

# <a name="configure-and-deploy-lookout-for-work-apps"></a>Configurare e distribuire l'app Lookout for Work
Questo articolo descrive come configurare e distribuire l'app Lookout for Work in dispositivi Android e iOS.

## <a name="android-google-play-store-app"></a>Android (app Google Play Store)

* **Passaggio 1**: nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) passare ad **App** e scegliere **Aggiungi app**.   
* **Passaggio 2**: nella pagina **Installazione software** dell'autore scegliere **Collegamento esterno** e specificare l'URL seguente: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Non fare clic sulla casella per richiedere un browser gestito.

* **Passaggio 3**: nella pagina **Descrizione software** immettere le informazioni seguenti:
  * **Autore:** Lookout Mobile Security
  * **Nome:** Lookout for Work
  * **Descrizione:** Lookout offre una protezione ottimale dalle minacce per dispositivi mobili per mantenere protetti i dispositivi. Con l'installazione dell'app Lookout il dispositivo viene protetto dalle minacce e l'app segnalerà le eventuali minacce rilevate all'utente e all'amministratore dell'azienda.
  * **Categoria:** Gestione computer
* **Passaggio 4**: al termine viene visualizzato il messaggio **Caricamento dei dati in Microsoft Intune completato**.

Quando si fa clic su **App** nella console Intune, l'elenco includerà a questo punto l'app Lookout for Work ![screenshot della pagina delle app della console di amministrazione Intune che mostra l'app Lookout for Work nell'elenco](../media/mtp/lookout-app-listed-intune-console.png)

* **Passaggio 5**: distribuire l'app agli utenti selezionando l'app Lookout for Work e scegliendo **Gestisci distribuzione**.

  È necessario selezionare gli stessi utenti aggiunti tramite l'opzione Enrollment Management (Gestione della registrazione) nella console di Lookout MTP.  Vedere il passaggio 3 nella sezione [Configurare la sottoscrizione con Lookout MTP](set-up-your-subscription-with-lookout-mtp.md#configure-your-subscription-with-lookout-device-threat-protection) per informazioni sull'aggiunta di gruppi di utenti a Lookout MTP.

  >[!IMPORTANT]
  > La procedura guidata per la distribuzione di app di Intune non riconosce i gruppi di utenti di Azure AD e usa invece i gruppi di utenti di Intune. È quindi necessario creare un gruppo di utenti di Intune in base al gruppo di utenti di Azure AD registrato nella console di Lookout MTP, come descritto in [questo](plan-your-user-and-device-groups.md)argomento.

* **Passaggio 6**: scegliere l'opzione **Installazione richiesta** per richiedere l'installazione dell'app Lookout nel dispositivo dell'utente.


## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (versione Enterprise dell'app Lookout)

* **Passaggio 1:** verificare che la **gestione iOS** sia impostata nel dispositivo. Per istruzioni su come configurare il dispositivo per la gestione iOS, vedere [Configurare la gestione dei dispositivi iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md).

* **Passaggio 2:** **firmare di nuovo** l'app Lookout for Work per iOS. Lookout distribuisce l'app Lookout for Work per iOS all'esterno dell'App Store di iOS. **Prima di distribuire l'app**, è necessario firmare di nuovo l'app usando l'apposito iOS Enterprise Developer Certificate. Per istruzioni dettagliate su come firmare di nuovo l'app Lookout for Work per iOS, accedere al sito di Lookout per conoscere il [processo da seguire per firmare di nuovo l'app Lookout for Work per iOS](https://personal.support.lookout.com/hc/en-us/articles/114094038714).


* **Passaggio 3:** consentire l'autenticazione di Azure Active Directory agli utenti iOS seguendo questa procedura:
  1.  Accedere al [portale di gestione di Azure Active Directory](https://manage.windowsazure.com) ed esplorare la pagina dell'applicazione.
  2.  Aggiungere l'**app Lookout for Work per iOS** come **applicazione client nativa**.
  ![screenshot della finestra di dialogo Aggiungi app con l'opzione dell'applicazione client nativa selezionata](../media/mtp/aad-add-app.png)

  3. Sostituire **com.lookout.enterprise.nomesocietà** con l'ID bundle del cliente selezionato durante l'accesso a IPA.
  4.  Aggiungere l'URI di reindirizzamento aggiuntivo: **&lt;portaleaziendale://code/>** seguito da una versione con codifica URL dell'URI di reindirizzamento originale.
  5.  Aggiungere le **autorizzazioni delegate** all'app.

  Per altri dettagli, vedere [Configurare un'applicazione client nativa](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).


* **Passaggio 4:** caricare il file con estensione ipa nuovamente firmato come descritto nell'argomento sull'[aggiunta di app per dispositivi mobili registrati in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune). Impostare la versione iOS minima su iOS 8.0 o versioni successive.

  ![screenshot della pagina delle applicazioni nella console di amministrazione di Intune con l'app Lookout for Work selezionata nell'elenco delle app](../media/mtp/ios-app-uploaded-intune.png)

* **Passaggio 5:** creare i criteri di configurazione dell'app gestita come descritto nell'argomento [Configurare le app iOS con i criteri di configurazione delle app mobili in Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

  ![schermata della creazione guidata di nuovi criteri con l'opzione per i criteri di configurazione di iOS 8.0 e versioni successive selezionata](../media/mtp/ios-app-config.png)

* **Passaggio 6:** **per distribuire l'app agli utenti**, selezionare l'app Lookout for Work e scegliere **Gestisci distribuzione**.

  È necessario selezionare gli stessi utenti aggiunti tramite l'opzione Enrollment Management (Gestione della registrazione) nella console di Lookout.  Per informazioni sull'aggiunta di gruppi di utenti a Lookout MTP, vedere il passaggio 3 nella sezione [Configurare la sottoscrizione con la protezione dalle minacce per il dispositivo di Lookout](set-up-your-subscription-with-lookout-mtp.md#configure-your-subscription-with-lookout-device-threat-protection).

>[!IMPORTANT]
> La procedura guidata per la distribuzione dell'app di Intune non riconosce i gruppi utenti di Azure AD e usa i gruppi utenti di Intune. È quindi necessario creare un gruppo utenti di Intune basato sul gruppo utenti di Azure AD registrato nella console di Lookout, come descritto in [questo](plan-your-user-and-device-groups.md) argomento.

Scegliere l'opzione **Installazione richiesta** per richiedere l'installazione dell'app Lookout nel dispositivo dell'utente.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Cosa accade quando viene aperta l'app distribuita nel dispositivo




Quando l'utente apre Lookout for Work nel dispositivo viene richiesto di attivare l'app e di scegliere l'opzione Sign in with Azure Active Directory (Accedi con Azure Active Directory). Negli argomenti seguenti è disponibile una procedura dettagliata con il flusso per l'utente finale:

* [Viene richiesto di installare Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [È necessario risolvere una minaccia rilevata da Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>Passaggi successivi
* [Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Dec16_HO2-->


