---
title: Configurare la gestione di Android for Work | Microsoft Intune
description: Abilitare la gestione di dispositivi mobili (MDM) per i dispositivi Android for Work con Microsoft Intune.
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b2fdcea9-9ad7-4d73-88e2-854b7a774bb2
translationtype: Human Translation
ms.sourcegitcommit: 519b66c94f3d056e060ed11e1a3d7d6d118a94fb
ms.openlocfilehash: 5f48303dd28627f961f8c2cfd38f8977354e2724


---

# Abilitare la registrazione di dispositivi Android for Work

Per abilitare la gestione di dispositivi Android for Work è necessario aggiungere un'associazione Android for Work a Intune. Per registrare dispositivi che supportano Android for Work ma che in precedenza sono stati registrati come dispositivi Android regolari, è necessario annullare la registrazione dei dispositivi e quindi rieseguirla.

## Aggiungere un'associazione Android for Work a Intune

1. **Configurare Intune**<br>
Se non è stato già fatto, preparare la gestione di dispositivi mobili (MDM) [impostando l'autorità di gestione di dispositivi mobili](prerequisites-for-enrollment.md#set-mobile-device-management-authority), ad esempio **Microsoft Intune**, e configurando MDM.

2. **Configurare l'associazione Android for Work**<br>
    Con un account utente amministratore aprire la [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), passare ad **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Android for Work** e fare clic su **Configura** per aprire il sito Web Android for Work in open Google Play. Questo sito verrà aperto in una nuova scheda del browser.

3. **Accedere a Google**<br>
   Nella pagina di accesso di Google immettere le credenziali dell'account Google che verrà associato a tutte le attività di gestione Android for Work per questo tenant. Potrebbe trattarsi di un account Google condiviso tra gli amministratori che gestiscono Intune. Questo sarà l'account Google usato dall'organizzazione per gestire e pubblicare le app nella console di Play for Work.

4. **Specificare i dettagli dell'organizzazione**<br>
   Specificare il nome della società in **Nome organizzazione**. Come **provider della gestione della mobilità aziendale** deve essere visualizzato *Microsoft Intune*. Accettare il contratto di Android for Work e quindi fare clic su **Conferma**. La richiesta verrà elaborata.

## Specificare le impostazioni di registrazione a Android for Work
   Android for Work è supportato solo da dispositivi Android specifici. Vedere i [requisiti di Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") di Google.  Qualsiasi dispositivo che supporta Android for Work supporta anche la gestione di Android convenzionale.  Intune consente di specificare la modalità di gestione dei dispositivi che supportano Android for Work:

   - **Manage all devices as Android** (Gestisci tutti i dispositivi come dispositivi Android) (disabilitata): tutti i dispositivi Android, inclusi quelli che supportano Android for Work, vengono registrati come dispositivi Android convenzionali.
   - **Manage supported devices as Android for Work** (Gestisci i dispositivi supportati come dispositivi Android for Work) (abilitata): tutti i dispositivi che supportano Android for Work vengono registrati come dispositivi Android for Work. Tutti i dispositivi che non supportano Android for Work vengono registrati come dispositivi Android convenzionali.
   - **Manage supported devices for users only in these user groups as Android for Work** (Gestisci i dispositivi supportati come dispositivi Android for Work solo per gli utenti di questi gruppi) (test): consente di limitare la gestione di Android for Work a un set specifico di utenti. Solo i membri dei gruppi selezionati che registrano un dispositivo che supporta Android for Work vengono registrati come dispositivi Android for Work. Tutti gli altri vengono registrati come dispositivi Android.

## Passaggi successivi per Android for Work
Dopo aver configurato l'associazione e le impostazioni di Android for Work è possibile eseguire le operazioni seguenti:
- [Distribuire app Android for Work](android-for-work-apps.md)
- [Aggiungere criteri di configurazione per Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)

## Annullare l'associazione dell'account amministrativo Android for Work

È possibile disattivare la registrazione e la gestione di Android for Work. Se si fa clic su **Disassocia** la registrazione di tutti i dispositivi Android for Work viene annullata e la relazione tra l'account Android for Work e Intune viene eliminata.

### Come disassociare un account Android for Work

1. **Annullare l'associazione ad Android for Work**<br>
    Con un account utente amministratore aprire la [console di amministrazione di Microsoft Intune](http://manage.microsoft.com), passare ad **Amministrazione** &gt; **Gestione dei dispositivi mobili** &gt; **Android for Work** e fare clic su **Disassocia**.

2. **Confermare l'eliminazione dell'associazione di Android for Work**<br>
  Fare clic su **Sì** per eliminare l'associazione e annullare la registrazione di tutti i dispositivi Android for Work da Intune.



<!--HONumber=Oct16_HO2-->

