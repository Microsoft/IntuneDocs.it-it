---
title: Registrare dispositivi Android in Intune | Microsoft Docs
titlesuffix: Azure portal
description: Informazioni su come registrare i dispositivi Android in Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: be998ba3282665d4aff7873b16bb1187edce7693
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2017
---
# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Un amministratore di Intune può gestire i dispositivi Android, inclusi i dispositivi Samsung Knox Standard. È anche possibile gestire il profilo di lavoro in [dispositivi Android for Work](#enable-enrollment-of-android-for-work-devices).

I dispositivi che eseguono Samsung KNOX Standard sono supportati per la gestione multiutente in Intune. Questo vuol dire che gli utenti finali possono accedere e disconnettersi dal dispositivo con le loro credenziali di Azure AD e il dispositivo viene gestito centralmente e indipendentemente dal fatto che sia o meno in uso. Quando gli utenti finali eseguono l'accesso, possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

## <a name="prerequisite"></a>Prerequisito

È necessario impostare l'autorità MDM su **Microsoft Intune** per preparare la gestione dei dispositivi mobili. Vedere [Impostare l'autorità MDM](mdm-authority-set.md) per le istruzioni. Questo elemento viene impostato una sola volta quando si configura Intune per la gestione dei dispositivi mobili per la prima volta.

## <a name="set-up-android-enrollment"></a>Configurare la registrazione di Android

Per impostazione predefinita, Intune permette la registrazione di dispositivi Android e Samsung Knox Standard.

Per bloccare la registrazione dei dispositivi Android o la registrazione dei soli dispositivi Android di proprietà personale, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).

Per abilitare la gestione dei dispositivi gli utenti devono registrarli scaricando l'app Portale aziendale di Intune, disponibile in Google Play, quindi aprire l'app e seguire le istruzioni per la registrazione. Dopo aver gestito i dispositivi Android, è possibile [assegnare criteri di conformità](compliance-policy-create-android.md), [gestire le app](app-management.md) e altro ancora.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Abilitare la registrazione di dispositivi Android for Work

Per abilitare la gestione del profilo di lavoro nei dispositivi che [supportano Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), è necessario aggiungere un'associazione di Android for Work a Intune. Per registrare dispositivi che supportano Android for Work ma che in precedenza sono stati registrati come dispositivi Android regolari, è necessario annullare la registrazione dei dispositivi e quindi rieseguirla.

## <a name="add-android-for-work-binding-for-intune"></a>Aggiungere un'associazione Android for Work a Intune

1. **Configurare la gestione dei dispositivi mobili di Intune**<br>
Se non è stato ancora fatto, preparare la gestione dei dispositivi mobili [impostando l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md) come **Microsoft Intune**.
2. **Configurare l'associazione Android for Work**<br>
    Come amministratore di Intune, nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

    1. Nel pannello **Intune** scegliere **Registrazione del dispositivo** > **Registrazione di Android for Work** e quindi fare clic su **Configura** per aprire il sito Web Android for Work di Google Play. Questo sito verrà aperto in una nuova scheda del browser.
  ![Screenshot che mostra il collegamento per configurare l'associazione di Android for Work](./media/android-work-bind.png)

    2. **Accedere a Google**<br>
   Nella pagina di accesso di Google immettere le credenziali dell'account Google che verrà associato a tutte le attività di gestione di Android for Work per questo tenant. Si tratta dell'account Google condiviso tra gli amministratori IT dall'organizzazione e usato per gestire e pubblicare le app nella console di Play for Work.

    3. **Specificare i dettagli sull'organizzazione**<br>
   Specificare il nome della società in **Nome organizzazione**. Come **provider della gestione della mobilità aziendale** deve essere visualizzato *Microsoft Intune*. Accettare il contratto di Android for Work e quindi fare clic su **Conferma**. La richiesta verrà elaborata.

## <a name="specify-android-for-work-enrollment-settings"></a>Specificare le impostazioni di registrazione a Android for Work
   Android for Work è supportato solo da dispositivi Android specifici. Vedere i [requisiti di Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") di Google. Qualsiasi dispositivo che supporta Android for Work supporta anche la gestione di Android convenzionale.  Intune consente di specificare la modalità di gestione dei dispositivi che supportano Android for Work:

   - **Gestisci tutti i dispositivi come Android**: tutti i dispositivi Android, inclusi quelli che supportano Android for Work, vengono registrati come dispositivi Android convenzionali.
   - **Gestisci i dispositivi supportati come Android for Work**: tutti i dispositivi che supportano Android for Work vengono registrati come dispositivi Android for Work. Tutti i dispositivi che non supportano Android for Work vengono registrati come dispositivi Android convenzionali.
   - **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work**: consente di limitare la gestione di Android for Work a un set specifico di utenti. Solo i membri dei gruppi selezionati che registrano un dispositivo che supporta Android for Work vengono registrati come dispositivi Android for Work. Tutti gli altri vengono registrati come dispositivi Android. Questa modalità risulta utile durante le distribuzioni pilota di Android for Work.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali

È necessario indicare agli utenti di accedere a Google Play, scaricare l'app Portale aziendale di Intune e aprire l'app, quindi seguire le istruzioni per la registrazione del dispositivo. L'app indica agli utenti le operazioni da eseguire per la registrazione, spiegando cosa possono aspettarsi e quali dati del dispositivo saranno visibili o meno agli amministratori IT.

È anche possibile inviare loro un collegamento alla procedura di registrazione online: [Registrare il dispositivo Android in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](end-user-educate.md)
- [Uso del dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbinding-your-android-for-work-administrative-account"></a>Annullare l'associazione dell'account amministrativo Android for Work

È possibile disattivare la registrazione e la gestione di Android for Work. Se si fa clic su **Disassocia** nella Console di amministrazione di Intune la registrazione di tutti i dispositivi Android for Work viene annullata e la relazione tra l'account Android for Work e Intune viene eliminata.

### <a name="how-to-unbind-an-android-for-work-account"></a>Come disassociare un account Android for Work

1. **Annullare l'associazione ad Android for Work**<br>
    Come amministratore di Intune, nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.  Nel pannello **Intune** scegliere **Registrazione del dispositivo** > **Registrazione di Android for Work** e quindi fare clic su **Dissocia**.

2. **Confermare l'eliminazione dell'associazione di Android for Work**<br>
  Fare clic su **Sì** per eliminare l'associazione e annullare la registrazione di tutti i dispositivi Android for Work da Intune.
