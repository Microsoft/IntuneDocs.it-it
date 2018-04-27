---
title: Registrare i dispositivi Android in Intune
titlesuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi Android in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d74f59f1df0a4a4e1285b58d7ac5b3677d3c5e48
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Un amministratore di Intune può gestire i dispositivi Android, inclusi i dispositivi Samsung Knox Standard. Inoltre può gestire il profilo di lavoro [Tutti i dispositivi Android for Work](#enable-enrollment-of-android-for-work-devices).

I dispositivi che eseguono Samsung Knox Standard sono supportati per la gestione multiutente in Intune. Gli utenti finali possono accedere e disconnettersi da un dispositivo con le credenziali di Azure AD. Il dispositivo è gestito a livello centrale indipendentemente dal fatto che sia o meno in uso. Quando gli utenti eseguono l'accesso possono accedere alle app e ai criteri ad essi applicati. Quando gli utenti si disconnettono, tutti i dati delle app vengono cancellati.

## <a name="prerequisite"></a>Prerequisito

Per preparare la gestione dei dispositivi mobili è necessario impostare l'autorità per la gestione dei dispositivi mobili su **Microsoft Intune**. Vedere [Impostare l'autorità MDM](mdm-authority-set.md) per le istruzioni. Questo elemento viene impostato una sola volta quando si configura Intune per la gestione dei dispositivi mobili per la prima volta.

## <a name="set-up-android-enrollment"></a>Configurare la registrazione di Android

Per impostazione predefinita, Intune permette la registrazione di dispositivi Android e Samsung Knox Standard.

Per bloccare la registrazione dei dispositivi Android o la registrazione dei soli dispositivi Android di proprietà personale, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).

Per abilitare la gestione dei dispositivi gli utenti devono registrarli scaricando l'app Portale aziendale di Intune, disponibile in Google Play, quindi aprire l'app e seguire le istruzioni per la registrazione. Una volta impostata la gestione dei dispositivi Android, è possibile [assegnare criteri di conformità](compliance-policy-create-android.md), [gestire le app](app-management.md) e altro ancora.

## <a name="enable-enrollment-of-android-for-work-devices"></a>Abilitare la registrazione di dispositivi Android for Work

Per abilitare la gestione del profilo di lavoro nei dispositivi che [supportano Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012), è necessario aggiungere un'associazione di Android for Work a Intune. Per registrare in Android for Work dispositivi che sono già stati registrati come normali dispositivi Android, è necessario annullare e quindi rieseguire la registrazione dei dispositivi.

Se si stanno registrando dispositivi Android for Work mediante un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md) è possibile registrare un massimo di 10 dispositivi per ogni account.

Per altre informazioni, vedere [Dati inviati da Intune a Google](data-intune-sends-to-google.md).

## <a name="add-android-for-work-binding-for-intune"></a>Aggiungere un'associazione Android for Work a Intune

> [!NOTE]
> A causa dell'interazione tra i domini Google e Microsoft, per completare correttamente questo passaggio potrebbe essere necessario modificare le impostazioni del browser.  Verificare che "portal.azure.com" e "play.google.com" si trovino nella stessa area di sicurezza del browser.

1. **Configurare la gestione dei dispositivi mobili di Intune**<br>
Se non è stato ancora fatto, preparare la gestione dei dispositivi mobili [impostando l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md) come **Microsoft Intune**.
2. **Configurare l'associazione Android for Work**<br>
    
   a. Accedere a [Intune dal portale di Azure](https://aka.ms/intuneportal), selezionare **Registrazione del dispositivo** > **Registrazione Android** > **Google Play gestito**.
   ![Schermata di registrazione di Android for Work](./media/android-work-bind.png)

   b. Selezionare **Accetto** per concedere a Microsoft l'autorizzazione per [l'invio di informazioni sugli utenti e sui dispositivi a Google](data-intune-sends-to-google.md). 
   
   c. Selezionare **Avviare Google per connettersi subito** per aprire il sito Web Android for Work di Google Play. Il sito Web viene aperto in una nuova scheda del browser.
  
   d. **Accedere a Google**<br>
   Nella pagina di accesso di Google immettere le credenziali dell'account Google che verrà associato a tutte le attività di gestione di Android for Work per questo tenant. Questo sarà l'account Google che verrà condiviso dagli amministratori IT dell'organizzazione per gestire e pubblicare le app nella console Play for Work. È possibile usare un account Google esistente oppure crearne uno nuovo.  L'account scelto non deve essere associato a un dominio G-Suite.

   e. **Specificare i dettagli sull'organizzazione**<br>
   Specificare il nome della società in **Nome organizzazione**. Come **provider della gestione della mobilità aziendale** deve essere visualizzato **Microsoft Intune**. Accettare il contratto di Android for Work e quindi scegliere **Conferma**. La richiesta verrà elaborata.

## <a name="specify-android-for-work-enrollment-settings"></a>Specificare le impostazioni di registrazione a Android for Work
Android for Work è supportato solo da dispositivi Android specifici. Vedere i [requisiti di Android for Work](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012%20style=%22target=new_window%22) di Google. Qualsiasi dispositivo che supporta Android for Work supporta anche la gestione di Android convenzionale. Intune consente di specificare la modalità di gestione dei dispositivi che supportano Android for Work in [Restrizioni registrazione](enrollment-restrictions-set.md).

- **Blocca (impostazione predefinita)**: tutti i dispositivi Android, inclusi i dispositivi che supportano Android for Work, vengono registrati come dispositivi Android convenzionali.
- **Consenti**: tutti i dispositivi che supportano Android for Work vengono registrati come dispositivi Android for Work. Tutti i dispositivi che non supportano Android for Work vengono registrati come dispositivi Android convenzionali.

## <a name="approve-the-company-portal-app-in-the-managed-google-play-store"></a>Approvare l'app Portale aziendale nella versione gestita di Google Play Store
È necessario approvare l'app Portale aziendale per Android nella versione gestita di Google Play Store per assicurarsi che riceva gli aggiornamenti automatici delle app. Se non viene approvata, l'app Portale aziendale diventerà non aggiornata e potrebbe non ricevere correzioni di bug importanti o nuove funzionalità rilasciate da Microsoft.

Seguire questa procedura per approvare l'app Portale aziendale Intune:

1.  Passare all'app Portale aziendale Intune nella [versione gestita di Google Play Store](https://play.google.com/work/apps/details?id=com.microsoft.windowsintune.companyportal).
2.  Accedere alla versione gestita di Google Play Store con lo stesso account di Google usato per configurare l'associazione per Android for Work.
3.  Fare clic su **Approva** e verrà aperta una nuova finestra di dialogo.
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
    Come amministratore di Intune, nel [portale di Azure](https://portal.azure.com) scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**.  Nel riquadro **Intune** scegliere **Registrazione del dispositivo** > **Registrazione di Android for Work** e quindi scegliere **Dissocia**.

2. **Confermare l'eliminazione dell'associazione di Android for Work**<br>
  Scegliere **Sì** per eliminare l'associazione e annullare la registrazione in Intune di tutti i dispositivi Android for Work.

## <a name="end-user-experience-when-enrolling-a-samsung-knox-device"></a>Esperienza utente finale durante la registrazione di un dispositivo Samsung Knox
Esistono diversi punti da considerare durante la registrazione di dispositivi Samsung Knox:
-   Anche se per i criteri non è necessario un PIN, il dispositivo deve avere almeno un PIN di quattro cifre per essere registrato. Se il dispositivo non ha un PIN, l'utente dovrà crearne uno.
-   Non esiste interazione da parte dell'utente per i certificati Workplace Join (WPJ).
-   L'utente deve specificare le informazioni relative alla registrazione del servizio e le operazioni che l'app può eseguire.
-   L'utente deve specificare le informazioni relative alla registrazione Knox e le operazioni che Knox può eseguire.
-   Se viene applicato un criterio di crittografia, gli utenti devono impostare una password complessa di sei caratteri come passcode del dispositivo.
-   Non sono richieste conferme aggiuntive da parte dell'utente per installare i certificati inseriti da un servizio per l'accesso alle risorse aziendali.
- Alcuni dispositivi Knox meno recenti chiederanno all'utente i certificati aggiuntivi usati per l'accesso alle risorse aziendali.
- Se l'installazione di un dispositivo Samsung Mini non riesce a installare WPJ e vengono visualizzati gli errori **Certificate Not Found** (Certificato non trovato) oppure **Unable to Register Device** (Impossibile registrare il dispositivo), installare gli ultimi aggiornamenti del firmware Samsung.
