---
title: 'Esercitazione: Proteggere la posta elettronica di Exchange Online nei dispositivi non gestiti'
titleSuffix: Microsoft Intune
description: Informazioni su come proteggere Office 365 Exchange Online con i criteri di protezione delle app di Intune e l'accesso condizionale di Azure AD.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6224a0dae7c0aa3d80d4e64331a668953220f65
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798785"
---
# <a name="tutorial-protect-exchange-online-email-on-unmanaged-devices"></a>Esercitazione: Proteggere la posta elettronica di Exchange Online nei dispositivi non gestiti

Informazioni sull'uso di criteri di protezione delle app con accesso condizionale per proteggere Exchange Online, anche quando i dispositivi non sono registrati in una specifica soluzione di gestione dei dispositivi come Intune. In questa esercitazione si apprenderà come: 

> [!div class="checklist"]
> * Creare criteri di protezione delle app di Intune per l'app Outlook. Si imposteranno limiti relativi alle operazioni che l'utente può eseguire con i dati dell'app, impedendo l'esecuzione del comando "Salva con nome" e limitando le operazioni Taglia, Copia e Incolla. 
> * Creare criteri di accesso condizionale di Azure Active Directory (Azure AD) che consentono solo all'app Outlook di accedere alla posta elettronica aziendale in Exchange Online. Si richiederà inoltre l'autenticazione a più fattori (MFA) per i client con autenticazione moderna, come Outlook per iOS e Android.

## <a name="prerequisites"></a>Prerequisiti
  - Per questa esercitazione sarà necessario un tenant di test con le sottoscrizioni seguenti:
    - Azure Active Directory Premium ([versione di valutazione gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
    - Sottoscrizione di Intune ([versione di valutazione gratuita](free-trial-sign-up.md))
    - Abbonamento a Office 365 Business che include Exchange ([versione di valutazione gratuita](https://go.microsoft.com/fwlink/p/?LinkID=510938))

## <a name="sign-in-to-intune"></a>Accedere a Intune

Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune. Si accede a Intune nel portale di Azure scegliendo **Tutti i servizi** > **Intune**.

## <a name="create-the-app-protection-policy"></a>Creare criteri di protezione delle app
Per questa esercitazione, si imposteranno criteri di protezione delle app di Intune per l'app Outlook in modo da applicare meccanismi di protezione a livello di app. Si richiederà un PIN per aprire l'app in un contesto aziendale. Si limiterà inoltre la condivisione dei dati tra app e si impedirà che i dati aziendali vengano salvati in un percorso personale.

1.  In Intune selezionare **App client** > **Criteri di protezione delle app** > **Aggiungi criteri**.
2.  In **Nome** immettere **Test criteri per app Outlook**.
3.  In **Descrizione** immettere **Test criteri per app Outlook**.
4.  Selezionare **App**. Nell'elenco delle app selezionare **Outlook** e quindi scegliere **Seleziona**.
5.  Selezionare **Impostazioni**. 
6.  In **Rilocazione dati**, per questa esercitazione, selezionare le impostazioni seguenti:

    - Per **Consenti all'app di trasferire i dati ad altre app**, selezionare **Nessuna**.
    - Per **Consenti all'app di ricevere i dati da altre app**, selezionare **Nessuna**.
    - Per **Impedisci "Salva con nome"**, selezionare **Sì**.
    - Per **Limita le operazioni taglia, copia e incolla con le altre app**, selezionare **Bloccato**.
   
     ![Selezionare le impostazioni di rilocazione dei dati per i criteri di protezione delle app per Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-data-relocation.png)
    
7.  In **Azioni di accesso**, per questa esercitazione, selezionare le impostazioni seguenti:

    - Per **Richiedi PIN per l'accesso**, selezionare **Sì**.
    - Per **Richiedi credenziali aziendali per l'accesso**, selezionare **Sì**.
    - Lasciare i valori predefiniti per tutte le altre impostazioni.
 
     ![Selezionare le azioni di accesso per i criteri di protezione delle app per Outlook](media/tutorial-protect-email-on-unmanaged-devices/outlook-app-access-actions.png)

9.  Selezionare **OK**.
10. Selezionare **Crea**.

La creazione dei criteri di protezione delle app per Outlook è completata. È ora possibile configurare l'accesso condizionale per richiedere ai dispositivi di usare l'app Outlook.

## <a name="create-conditional-access-policies"></a>Creare criteri di accesso condizionale
Si definiranno ora due impostazioni di criteri di accesso condizionale in modo da supportare tutte le piattaforme per dispositivi. Con la prima impostazione si richiederà ai client con autenticazione moderna, come Outlook per iOS e Outlook per Android, di usare l'autenticazione a più fattori e l'app Outlook approvata. Con la seconda impostazione si richiederà ai client di Exchange ActiveSync di usare l'app Outlook approvata. Attualmente, Exchange ActiveSync non supporta condizioni diverse dalla piattaforma per dispositivi. È possibile configurare i criteri di accesso condizionale nel portale di Azure AD o in quello di Intune. Dato che finora è stato usato il portale di Intune, i criteri verranno creati in questo portale.
### <a name="create-an-mfa-policy-for-modern-authentication-clients"></a>Creare criteri di autenticazione a più fattori per i client con autenticazione moderna
1.  In Intune selezionare **Accesso condizionale** > **Criteri** > **Nuovi criteri**.
1.  In **Nome** immettere **Criteri di test per client con autenticazione moderna**. 
3.  In **Assegnazioni** selezionare **Utenti e gruppi**. Nella scheda **Includi** selezionare **Tutti gli utenti** e quindi selezionare **Fine**.

4.  In **Assegnazioni** selezionare **App cloud**. Dato che si vuole proteggere la posta elettronica di Office 365 Exchange Online, si selezionerà questa app tramite la procedura seguente:
     
    1. Nella scheda **Includi** scegliere **Selezionare le app**.
    2. Scegliere **Seleziona**. 
    3. Nell'elenco delle applicazioni selezionare **Office 365 Exchange Online** e quindi scegliere **Seleziona**. 
    4. Seleziona **Chiudi**.
  
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-cloud-apps.png)

5.  In **Assegnazioni** selezionare **Condizioni** > **Piattaforme del dispositivo**.
     
    1. In **Configura** selezionare **Sì**.
    2. Nella scheda **Includi** selezionare **Qualsiasi dispositivo**.
    1. Seleziona **Chiudi**.
   
6.  Nel riquadro **Condizioni** selezionare **App client**.
     
    1. In **Configura** selezionare **Sì**.
    2. Selezionare **App per dispositivi mobili e client desktop** e **Client con autenticazione moderna**.
    3. Deselezionare le altre caselle di controllo.
    4. Selezionare **Fine** e quindi di nuovo **Fine**.
    
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-client-apps.png)

7.  In **Controlli di accesso** selezionare **Concedi**. 
     
    1. Nel riquadro **Concedi** selezionare **Concedi accesso**.
    2. Selezionare **Richiedi autenticazione a più fattori** .
    4. Selezionare **Richiedi app client approvata**.
    5. In **Per più controlli** selezionare **Richiedi tutti i controlli selezionati**. Questa impostazione garantisce che entrambi i requisiti selezionati vengano applicati quando un dispositivo tenta di accedere alla posta elettronica.
    6. Scegliere **Seleziona**.
     
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/modern-auth-policy-mfa.png)

8.  In **Abilita criterio** selezionare **Sì**.
     
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/enable-policy.png)

9.  Selezionare **Crea**.

La creazione dei criteri di accesso condizionale per i client con autenticazione moderna è completata. È ora possibile creare i criteri per i client di Exchange ActiveSync.

### <a name="create-a-policy-for-exchange-active-sync-clients"></a>Creare criteri per i client di Exchange ActiveSync
1.  In Intune selezionare **Accesso condizionale** > **Criteri** > **Nuovi criteri**.
2.  In **Nome** immettere **Criteri di test per client EAS**. 
3.  In **Assegnazioni** selezionare **Utenti e gruppi**. Nella scheda **Includi** selezionare **Tutti gli utenti** e quindi selezionare **Fine**.

4.  In **Assegnazioni** selezionare **App cloud**. Selezionare la posta elettronica di Office 365 Exchange Online seguendo questa procedura:
     
    1. Nella scheda **Includi** scegliere **Selezionare le app**.
    2. Scegliere **Seleziona**. 
    3. Nell'elenco delle applicazioni selezionare **Office 365 Exchange Online** e quindi scegliere **Seleziona**. 
    4. Seleziona **Chiudi**.

5.  In **Assegnazioni** selezionare **Condizioni** > **Piattaforme del dispositivo**.
     
    1. In **Configura** selezionare **Sì**.
    2. Nella scheda **Includi** selezionare **Qualsiasi dispositivo** e quindi selezionare **Fine**. 
    3. Selezionare di nuovo **Fine**.

6.  Nel riquadro **Condizioni** selezionare **App client**.
     
    1. In **Configura** selezionare **Sì**.
    2. Selezionare **App per dispositivi mobili e client desktop**.
    3. Selezionare **Client Exchange ActiveSync** e **Applica i criteri solo alle piattaforme supportate**. 
    4. Deselezionare tutte le altre caselle di controllo.
    5. Selezionare **Fine** e quindi di nuovo **Fine**.
    
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-client-apps.png)

7.  In **Controlli di accesso** selezionare **Concedi**. 
     
    1. Nel riquadro **Concedi** selezionare **Concedi accesso**.
    4. Selezionare **Richiedi app client approvata**. Deselezionare tutte le altre caselle di controllo.
    6. Scegliere **Seleziona**.
     
    ![Selezionare l'app Office 365 Exchange Online](media/tutorial-protect-email-on-unmanaged-devices/eas-grant-access.png)

8.  In **Abilita criterio** selezionare **Sì**.

9.  Selezionare **Crea**.

I criteri di protezione delle app e l'accesso condizionale sono ora configurati e pronti per il test. 

## <a name="try-it-out"></a>Procedura
Con i criteri creati, i dispositivi dovranno essere registrati in Intune e usare l'app Outlook per dispositivi mobili per accedere alla posta elettronica di Office 365. Per testare questo scenario in un dispositivo iOS, provare ad accedere a Exchange Online usando le credenziali di un utente nel tenant di test.
1. Per testare in un iPhone, passare a **Impostazioni** > **Password e account** > **Aggiungi account** > **Exchange**.
2. Immettere l'indirizzo di posta elettronica per un utente nel tenant e quindi premere **Avanti**.
3. Premere **Accedi**.
4. Immettere la password dell'utente di test e premere **Accedi**.
5. Verrà visualizzato un messaggio per segnalare che **sono necessarie altre informazioni**, ovvero che è necessario configurare l'autenticazione a più fattori. Proseguire e configurare un metodo di verifica aggiuntivo.
6. Verrà quindi visualizzato un messaggio per segnalare che si sta provando ad aprire la risorsa con un'app che non è stata approvata dal reparto IT. Ciò significa che non si è autorizzati a usare l'app di posta elettronica nativa. Annullare l'accesso.
7.  Aprire l'app Outlook e selezionare **Impostazioni** > **Aggiungi account** > **Aggiungi account di posta elettronica**.
8. Immettere l'indirizzo di posta elettronica per un utente nel tenant e quindi premere **Avanti**.
9. Scegliere **Accedi a Office 365** . Verrà chiesto di eseguire operazioni di autenticazione e registrazione aggiuntive. Dopo aver eseguito l'accesso, è possibile testare le azioni, ad esempio le operazioni Taglia, Copia, Incolla e "Salva con nome".

## <a name="clean-up-resources"></a>Pulizia delle risorse
Quando i criteri di test non sono più necessari, è possibile rimuoverli.
1. Accedere a [Intune](https://aka.ms/intuneportal) come amministratore globale o come amministratore del servizio Intune.
2. Selezionare **Conformità del dispositivo** > **Criteri**.
3. Nell'elenco **Nome criteri** selezionare il menu di scelta rapida (**...**) per i criteri di test e quindi selezionare **Elimina**. Selezionare **OK** per confermare.
4. Selezionare **Accesso condizionale** > **Criteri**.
5. Nell'elenco **Nome criteri** selezionare il menu di scelta rapida (**...**) per ciascuno dei criteri di test e quindi selezionare **Elimina**. Selezionare **Sì** per confermare.

 ## <a name="next-steps"></a>Passaggi successivi 
In questa esercitazione sono stati creati criteri di protezione delle app, per limitare le operazioni che gli utenti possono eseguire con l'app Outlook, e criteri di accesso condizionale, per richiedere l'uso dell'app Outlook e dell'autenticazione a più fattori per i client con autenticazione moderna. Per informazioni sull'uso di Intune con l'accesso condizionale per proteggere altri servizi e app, vedere [Configurare l'accesso condizionale](conditional-access.md).
