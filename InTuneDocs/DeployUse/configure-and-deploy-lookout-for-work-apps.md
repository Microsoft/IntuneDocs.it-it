---
title: Distribuire l'app Lookout for Work | Microsoft Intune
description: Configurare e distribuire l'app Lookout for Work per Android.
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: c43104ff199e1800bfded35154d2be0cfd0c40f3


---

# Configurare e distribuire l'app Lookout for Work
In questa versione è supportata l'app Lookout for Work nei dispositivi Android che eseguono la versione 4.1 e successiva.
## Android
Questa sezione illustra come configurare e distribuire l'app Lookout for Work per i dispositivi Android registrati in Intune.  
* Passaggio 1: nella [console di amministrazione Microsoft Intune](https://manage.microsoft.com) passare ad **App** e scegliere **App**.   
* Passaggio 2: nella pagina **Installazione software** dell'autore scegliere **Collegamento esterno** e specificare l'URL seguente: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Non fare clic sulla casella per richiedere un browser gestito.

* Passaggio 3: nella pagina **Descrizione software** compilare le informazioni seguenti:
  * **Autore:** Lookout Mobile Security
  * **Nome:** Lookout for Work
  * **Descrizione:** Lookout offre una protezione ottimale dalle minacce per dispositivi mobili per mantenere protetti i dispositivi. Con l'installazione dell'app Lookout il dispositivo viene protetto dalle minacce e l'app segnalerà le eventuali minacce rilevate all'utente e all'amministratore dell'azienda.
  * **Categoria:** Gestione computer
* Passaggio 4: al termine viene visualizzato il messaggio **Caricamento dei dati in Microsoft Intune completato**.

Quando si fa clic su **App** nella console Intune, l'elenco includerà a questo punto l'app Lookout for Work ![screenshot della pagina App della console di amministrazione Intune che mostra l'app Lookout for Work nell'elenco](../media/mtp/lookout-app-listed-intune-console.png)

Passaggio 5: a questo punto Intune sa come distribuire l'app Lookout for Work per Android.   Per distribuire l'app agli utenti, è possibile selezionare l'app Lookout for Work nella schermata precedente e selezionare **Gestisci distribuzione**.

È necessario selezionare gli stessi utenti aggiunti tramite l'opzione Enrollment Management (Gestione della registrazione) nella console di Lookout MTP.  Vedere il passaggio 3 nella sezione [Configurare la sottoscrizione con Lookout MTP](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) per informazioni sull'aggiunta di gruppi di utenti a Lookout MTP.
>[!IMPORTANT]
> La procedura guidata per la distribuzione di app di Intune non riconosce i gruppi di utenti di Azure AD e usa invece i gruppi di utenti di Intune. È quindi necessario creare un gruppo di utenti di Intune in base al gruppo di utenti di Azure AD registrato nella console di Lookout MTP, come descritto in [questo](plan-your-user-and-device-groups.md)argomento.

Passaggio 6: scegliere l'opzione **Installazione richiesta** per richiedere l'installazione dell'app Lookout nel dispositivo dell'utente.

### Attivazione del dispositivo
Selezionando l'opzione **Installazione richiesta** per la distribuzione, Intune effettuerà il push dell'app Lookout for Work nel dispositivo.   

Quando l'utente apre Lookout for Work nel dispositivo viene richiesto di attivare l'app e di scegliere l'opzione Sign in with Azure Active Directory (Accedi con Azure Active Directory). Negli argomenti seguenti è disponibile una procedura dettagliata con il flusso per l'utente finale:

* [Viene richiesto di installare Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [È necessario risolvere una minaccia rilevata da Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Passaggi successivi
* [Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO2-->


