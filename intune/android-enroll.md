---
title: Registrare dispositivi Android in Intune | Microsoft Docs
titlesuffix: Azure portal
description: Informazioni su come registrare i dispositivi Android in Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 12/07/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1c78c41b9883cac41b4506c1c02790008115e210
ms.sourcegitcommit: a7c1e10e615e5c975bb5d52eca986c5cf5287687
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2017
---
# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Un amministratore di Intune può gestire i dispositivi Android, inclusi i dispositivi Samsung Knox Standard. Inoltre può gestire il profilo di lavoro [Tutti i dispositivi Android for Work](#enable-enrollment-of-android-for-work-devices).

I dispositivi che eseguono Samsung Knox Standard sono supportati per la gestione multiutente in Intune. Gli utenti finali possono accedere e disconnettersi da un dispositivo con le credenziali di Azure AD. Il dispositivo è gestito a livello centrale indipendentemente dal fatto che sia o meno in uso. Quando gli utenti eseguono l'accesso possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

## <a name="prerequisite"></a>Prerequisito

Per preparare la gestione dei dispositivi mobili è necessario impostare l'autorità per la gestione dei dispositivi mobili su **Microsoft Intune**. Vedere [Impostare l'autorità MDM](mdm-authority-set.md) per le istruzioni. Questo elemento viene impostato una sola volta quando si configura Intune per la gestione dei dispositivi mobili per la prima volta.

## <a name="set-up-android-enrollment"></a>Configurare la registrazione di Android

Per impostazione predefinita, Intune permette la registrazione di dispositivi Android e Samsung Knox Standard.

Per bloccare la registrazione dei dispositivi Android o la registrazione dei soli dispositivi Android di proprietà personale, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).

Per abilitare la gestione dei dispositivi gli utenti devono registrarli scaricando l'app Portale aziendale di Intune, disponibile in Google Play, quindi aprire l'app e seguire le istruzioni per la registrazione. Una volta impostata la gestione dei dispositivi Android, è possibile [assegnare criteri di conformità](compliance-policy-create-android.md), [gestire le app](app-management.md) e altro ancora.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Abilitare la registrazione di dispositivi Android for Work

Per abilitare la gestione del profilo di lavoro nei dispositivi che [supportano Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), è necessario aggiungere un'associazione di Android for Work a Intune. Per registrare dispositivi che supportano Android for Work ma che in precedenza sono stati registrati come dispositivi Android comuni, è necessario annullare e quindi rieseguire la registrazione dei dispositivi.

Se si stanno registrando dispositivi Android for Work mediante un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md) è possibile registrare un massimo di 10 dispositivi per ogni account.

## <a name="add-android-for-work-binding-for-intune"></a>Aggiungere un'associazione Android for Work a Intune

1. **Configurare la gestione dei dispositivi mobili di Intune**<br>
Se non è stato ancora fatto, preparare la gestione dei dispositivi mobili [impostando l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md) come **Microsoft Intune**.
2. **Configurare l'associazione Android for Work**<br>
    Come amministratore di Intune, nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

   a. Nel pannello **Intune** scegliere **Registrazione del dispositivo** > **Registrazione di Android for Work** e quindi scegliere **Configura** per aprire il sito Web Android for Work di Google Play. Il sito Web viene aperto in una nuova scheda del browser.
   ![Screenshot che mostra il collegamento per configurare l'associazione di Android for Work](./media/android-work-bind.png)

   b. **Accedere a Google**<br>
   Nella pagina di accesso di Google immettere le credenziali dell'account Google che verrà associato a tutte le attività di gestione di Android for Work per questo tenant. Questo sarà l'account Google che verrà condiviso dagli amministratori IT dell'organizzazione per gestire e pubblicare le app nella console Play for Work.

   c. **Specificare i dettagli sull'organizzazione**<br>
   Specificare il nome della società in **Nome organizzazione**. Come **provider della gestione della mobilità aziendale** deve essere visualizzato **Microsoft Intune**. Accettare il contratto di Android for Work e quindi scegliere **Conferma**. La richiesta verrà elaborata.

## <a name="specify-android-for-work-enrollment-settings"></a>Specificare le impostazioni di registrazione a Android for Work
   Android for Work è supportato solo da dispositivi Android specifici. Vedere i [requisiti di Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012 style="target=new_window") di Google. Qualsiasi dispositivo che supporta Android for Work supporta anche la gestione di Android convenzionale. Intune consente di specificare la modalità di gestione dei dispositivi che supportano Android for Work:

   - **Gestisci tutti i dispositivi come Android**. Tutti i dispositivi Android, inclusi i dispositivi che supportano Android for Work, vengono registrati come dispositivi Android convenzionali.
   - **Gestisci i dispositivi supportati come Android for Work**. Tutti i dispositivi che supportano Android for Work vengono registrati come dispositivi Android for Work. Tutti i dispositivi che non supportano Android for Work vengono registrati come dispositivi Android convenzionali.
   - **Gestisci i dispositivi supportati per gli utenti solo in questi gruppi come Android for Work**. Consente di impostare la gestione Android for Work per un insieme limitato di utenti. Solo i membri dei gruppi selezionati che registrano un dispositivo che supporta Android for Work vengono registrati come dispositivi Android for Work. Tutti gli altri vengono registrati come dispositivi Android. Questa modalità risulta utile durante le distribuzioni pilota di Android for Work.

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Approvare l'app Portale aziendale nella versione gestita di Google Play Store
È necessario approvare l'app Portale aziendale per Android nella versione gestita di Google Play Store per assicurarsi che riceva gli aggiornamenti automatici delle app. Se non viene approvata, l'app Portale aziendale diventerà non aggiornata e potrebbe non ricevere correzioni di bug importanti o nuove funzionalità rilasciate da Microsoft.

Seguire questa procedura per approvare l'app Portale aziendale Intune:

1.  Scaricare l'app Portale aziendale dalla [versione gestita di Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Accedere alla versione gestita di Google Play Store con lo stesso account di Google usato per configurare l'associazione per Android for Work.
3.  Fare clic su **Approva**.  Verrà aperta una nuova finestra di dialogo.
4.  Controllare le autorizzazioni in questa finestra di dialogo e quindi fare clic su **Approva**. Questa operazione è necessaria per consentire queste autorizzazioni allo scopo di consentire all'app Portale aziendale di gestire il profilo di lavoro nel dispositivo.
5.  Selezionare **Keep approved when app requests new permissions** (Mantieni approvazione quando l'app richiede nuove autorizzazioni) e quindi fare clic su **Salva**.

<!--  ## Next steps for Android for Work
After configuring the Android for Work binding and settings, you can do the following:
- [Deploy Android for Work apps](android-for-work-apps.md)
- [Add Android for Work configuration policies](android-for-work-policy-settings-in-microsoft-intune.md)  -->

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali

Indicare agli utenti di accedere a Google Play, scaricare l'app Portale aziendale di Intune e aprire l'app, quindi di seguire le istruzioni per la registrazione del dispositivo. L'app indica agli utenti le operazioni da eseguire per la registrazione, spiegando cosa possono aspettarsi e quali dati del dispositivo saranno visibili o meno agli amministratori IT.

È anche possibile inviare loro un collegamento alla procedura di registrazione online: [Registrare il dispositivo Android in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-android).

Per informazioni su altre attività dell'utente, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](end-user-educate.md)
- [Uso del dispositivo Android con Intune](https://docs.microsoft.com/intune-user-help/using-your-android-device-with-intune)

## <a name="unbind-your-android-for-work-administrative-account"></a>Annullare l'associazione dell'account amministrativo Android for Work

È possibile disattivare la registrazione e la gestione di Android for Work. Se si sceglie **Dissocia** nella console di amministrazione di Intune viene annullata la registrazione di tutti i dispositivi Android for Work registrati. Viene rimossa anche la relazione tra l'account Android for Work e Intune.

### <a name="to-unbind-an-android-for-work-account"></a>Per disassociare un account Android for Work

1. **Annullare l'associazione ad Android for Work**<br>
    Come amministratore di Intune, nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.  Nel pannello **Intune** scegliere **Registrazione del dispositivo** > **Registrazione di Android for Work** e quindi scegliere **Dissocia**.

2. **Confermare l'eliminazione dell'associazione di Android for Work**<br>
  Scegliere **Sì** per eliminare l'associazione e annullare la registrazione in Intune di tutti i dispositivi Android for Work.
