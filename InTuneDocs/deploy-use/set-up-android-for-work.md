---
title: Impostare Android for Work | Microsoft Docs
description: Abilitare la gestione di dispositivi mobili (MDM) per i dispositivi Android for Work con Microsoft Intune.
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 03/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8b2bd3ecba0b597bc742ea08872ffe8fc58155cf
ms.openlocfilehash: 660d0c69fc09c6ec8b82185b3808269ef4bb6852
ms.lasthandoff: 04/24/2017


---

# <a name="enable-enrollment-of-android-for-work-devices"></a>Abilitare la registrazione di dispositivi Android for Work

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Per abilitare la gestione di dispositivi Android for Work è necessario aggiungere un'associazione Android for Work a Intune. Per registrare dispositivi che supportano Android for Work ma che in precedenza sono stati registrati come dispositivi Android regolari, è necessario annullare la registrazione dei dispositivi e quindi rieseguirla.

## <a name="add-android-for-work-binding-for-intune"></a>Aggiungere un'associazione Android for Work a Intune

1. **Configurare Intune**<br>
Se non è stato già fatto, preparare la gestione di dispositivi mobili (MDM) [impostando l'autorità di gestione di dispositivi mobili](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-8#enable-device-enrollment), ad esempio **Microsoft Intune**, e configurando MDM.

2. **Configurare l'associazione Android for Work**<br>
    L'amministratore di Intune può aprire la [console di amministrazione di Microsoft Intune](https://manage.microsoft.com), passare ad **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Android for Work** e fare clic su **Configura** per aprire il sito Web di Android for Work in Google Play. Questo sito verrà aperto in una nuova scheda del browser.

3. **Accedere a Google**<br>
   Nella pagina di accesso di Google immettere le credenziali dell'account Google che verrà associato a tutte le attività di gestione di Android for Work per questo tenant. Si tratta dell'account Google condiviso tra gli amministratori IT dall'organizzazione e usato per gestire e pubblicare le app nella console di Play for Work.

4. **Specificare i dettagli sull'organizzazione**<br>
   Specificare il nome della società in **Nome organizzazione**. Come **provider della gestione della mobilità aziendale** deve essere visualizzato *Microsoft Intune*. Accettare il contratto di Android for Work e quindi fare clic su **Conferma**. La richiesta verrà elaborata.

## <a name="specify-android-for-work-enrollment-settings"></a>Specificare le impostazioni di registrazione a Android for Work
   Android for Work è supportato solo da dispositivi Android specifici. Vedere i [requisiti di Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") di Google.  Qualsiasi dispositivo che supporta Android for Work supporta anche la gestione di Android convenzionale.  Intune consente di specificare la modalità di gestione dei dispositivi che supportano Android for Work:

   - **Gestisci tutti i dispositivi come Android**: tutti i dispositivi Android, inclusi quelli che supportano Android for Work, vengono registrati come dispositivi Android convenzionali.
   - **Gestisci i dispositivi supportati come Android for Work**: tutti i dispositivi che supportano Android for Work vengono registrati come dispositivi Android for Work. Tutti i dispositivi che non supportano Android for Work vengono registrati come dispositivi Android convenzionali.
   - **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work**: consente di limitare la gestione di Android for Work a un set specifico di utenti. Solo i membri dei gruppi selezionati che registrano un dispositivo che supporta Android for Work vengono registrati come dispositivi Android for Work. Tutti gli altri vengono registrati come dispositivi Android. Questa modalità risulta utile durante le distribuzioni pilota di Android for Work.

## <a name="next-steps-for-android-for-work"></a>Passaggi successivi per Android for Work
Dopo avere configurato l'associazione e le impostazioni di Android for Work, è possibile eseguire le operazioni seguenti:
- [Distribuire app Android for Work](android-for-work-apps.md)
- [Aggiungere criteri di configurazione per Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Annullare l'associazione dell'account amministrativo Android for Work

È possibile disattivare la registrazione e la gestione di Android for Work. Se si fa clic su **Disassocia** nella Console di amministrazione di Intune la registrazione di tutti i dispositivi Android for Work viene annullata e la relazione tra l'account Android for Work e Intune viene eliminata.

### <a name="how-to-unbind-an-android-for-work-account"></a>Come disassociare un account Android for Work

1. **Annullare l'associazione ad Android for Work**<br>
    Con un account utente amministratore aprire la [console di amministrazione di Microsoft Intune](https://manage.microsoft.com), passare ad **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Android for Work** e fare clic su **Disassocia**.

2. **Confermare l'eliminazione dell'associazione di Android for Work**<br>
  Fare clic su **Sì** per eliminare l'associazione e annullare la registrazione di tutti i dispositivi Android for Work da Intune.

