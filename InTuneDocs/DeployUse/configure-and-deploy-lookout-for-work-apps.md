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
ms.sourcegitcommit: ceaeba74f8671caf4125252fce02fd06752c3fe8
ms.openlocfilehash: 46a6b836e344c9cf876d633f868753a49c0cd440


---

# Configurare e distribuire l'app Lookout for Work
Questo articolo descrive come configurare e distribuire l'app Lookout for Work per i dispositivi registrati e che eseguono Android 4.1 o versione successiva.

* **Passaggio 1:**   nella [console di amministrazione di Microsoft Intune](https://manage.microsoft.com) passare ad **App** e scegliere **Aggiungi app**.   
* **Passaggio 2:**   nella pagina **Installazione software** dell'autore scegliere **Collegamento esterno** e specificare l'URL seguente: https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>Non fare clic sulla casella per richiedere un browser gestito.

* **Passaggio 3:**   nella pagina **Descrizione software** immettere le informazioni seguenti:
  * **Autore:** Lookout Mobile Security
  * **Nome:** Lookout for Work
  * **Descrizione:** Lookout offre una protezione ottimale dalle minacce per dispositivi mobili per mantenere protetti i dispositivi. Con l'installazione dell'app Lookout il dispositivo viene protetto dalle minacce e l'app segnalerà le eventuali minacce rilevate all'utente e all'amministratore dell'azienda.
  * **Categoria:** Gestione computer
* **Passaggio 4:**  al termine viene visualizzato il messaggio **Caricamento dei dati in Microsoft Intune completato**.

Quando si fa clic su **App** nella console di amministrazione di Intune, l'elenco includerà a questo punto l'app Lookout for Work ![screenshot della pagina delle app della console di amministrazione di Intune che mostra l'app Lookout for Work nell'elenco](../media/mtp/lookout-app-listed-intune-console.png)

**Per distribuire l'app agli utenti**, è possibile selezionare l'app Lookout for Work nella schermata precedente e fare clic su **Gestisci distribuzione**.

È necessario selezionare gli stessi utenti aggiunti tramite l'opzione Enrollment Management (Gestione della registrazione) nella console di Lookout.  Per informazioni sull'aggiunta di gruppi di utenti a Lookout MTP, vedere il passaggio 3 nella sezione [Configurare la sottoscrizione con la protezione dalle minacce per il dispositivo di Lookout](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp).
>[!IMPORTANT]
> La procedura guidata per la distribuzione dell'app di Intune non riconosce i gruppi utenti di Azure AD e usa i gruppi utenti di Intune. È quindi necessario creare un gruppo utenti di Intune basato sul gruppo utenti di Azure AD registrato nella console di Lookout, come descritto in [questo](plan-your-user-and-device-groups.md) argomento.

Scegliere l'opzione **Installazione richiesta** per richiedere l'installazione dell'app Lookout nel dispositivo dell'utente.


Selezionando l'opzione **Installazione richiesta** per la distribuzione, Intune effettuerà il push dell'app Lookout for Work nel dispositivo.   

Quando l'utente apre Lookout for Work nel dispositivo viene richiesto di attivare l'app e di scegliere l'opzione Sign in with Azure Active Directory (Accedi con Azure Active Directory). Negli argomenti seguenti è disponibile una procedura dettagliata con il flusso per l'utente finale:

* [Viene richiesto di installare Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [È necessario risolvere una minaccia rilevata da Lookout for Work nel dispositivo Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## Passaggi successivi
* [Abilitare la regola di protezione dalle minacce per i dispositivi nei criteri di conformità](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO4-->


