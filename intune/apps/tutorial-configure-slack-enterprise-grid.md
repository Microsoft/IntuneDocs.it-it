---
title: Esercitazione - Configurare Slack per l'uso di Intune per EMM e la configurazione delle app
titleSuffix: Microsoft Intune
description: In questa esercitazione si apprenderà come configurare Slack per l'uso di Intune per EMM e la configurazione delle app.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/09/2019
ms.topic: tutorial
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 55db37c5-0da7-4d9c-8027-525afb1c6349
Customer intent: As an Intune admin, I want to learn how to configure Slack to use Intune for EMM and app configuration..
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a210e45ddb181da4db1c1cff1e63a5d9b9ea2343
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724464"
---
# <a name="tutorial-configure-slack-to-use-intune-for-emm-and-app-configuration"></a>Esercitazione: Configurare Slack per l'uso di Intune per EMM e la configurazione delle app

Slack è un'app di collaborazione che può essere usata con Microsoft Intune.   

In questa esercitazione:
> [!div class="checklist"]
> - Impostare Intune come provider di Enterprise Mobility Management (EMM) in Slack Enterprise Grid. Si potrà limitare ai dispositivi gestiti di Intune l'accesso alle aree di lavoro del piano Grid.
> - Creare criteri di configurazione delle app per gestire l'app Slack per EMM in iOS e l'app Slack per i dispositivi del profilo di lavoro Android.
> - Creare criteri di conformità per i dispositivi Intune per impostare le condizioni che i dispositivi Android e iOS devono soddisfare per essere considerati conformi.

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](../fundamentals/free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
Per questa esercitazione sarà necessario un tenant di test con le sottoscrizioni seguenti:
- Azure Active Directory Premium ([versione di valutazione gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F))
- Sottoscrizione di Intune ([versione di valutazione gratuita](../fundamentals/free-trial-sign-up.md))

Sarà necessario anche un piano di [Slack Enterprise Grid](https://get.slack.help/hc/articles/360004150931-What-is-Slack-Enterprise-Grid-).

## <a name="configure-your-slack-enterprise-grid-plan"></a>Configurare il piano Slack Enterprise Grid
Attivare EMM per il piano Slack Enterprise Grid seguendo le [istruzioni di Slack](https://get.slack.help/hc/articles/115002579426-Enable-Enterprise-Mobility-Management-for-your-org#step-2:-turn-on-emm) e [connettere Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/slack-tutorial) come provider di identità (IdP) del piano Grid.

## <a name="sign-in-to-intune"></a>Accedere a Intune
Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) come amministratore globale o come amministratore del servizio Intune. Se è stata creata una sottoscrizione della versione di valutazione di Intune, l'account creato con tale sottoscrizione sarà un amministratore globale.

## <a name="set-up-slack-for-emm-on-ios-devices"></a>Configurare Slack per EMM nei dispositivi iOS
Aggiungere l'app iOS Slack per EMM al tenant di Intune e creare un criterio di configurazione dell'app per consentire agli utenti iOS dell'organizzazione di accedere a Slack con Intune come provider EMM.

### <a name="add-slack-for-emm-to-intune"></a>Aggiungere Slack per EMM a Intune
Aggiungere Slack per EMM come app iOS gestita in Intune e assegnare gli utenti di Slack. Le app sono specifiche della piattaforma, quindi è necessario aggiungere un'app di Intune separata per gli utenti di Slack nei dispositivi Android.
1. In Intune selezionare **App client** > **App** > **Aggiungi**.
2. In Tipo di applicazione selezionare **App dello Store - iOS**.
3. Selezionare **Cerca in App Store**. Immettere il termine di ricerca "Slack per EMM" e selezionare l'app.
4. Selezionare **Informazioni sull'app** e configurare le eventuali modifiche necessarie.
5. Selezionare **Aggiungi**.
6. Nella barra di ricerca immettere "Slack per EMM" e selezionare l'app appena aggiunta.
7. In Gestisci selezionare **Assegnazioni**.
8. Selezionare **Aggiungi gruppi**. A seconda degli utenti interessati dall'attivazione di EMM per Slack, in **Tipo di assegnazione** è possibile selezionare:
    - **Disponibile per i dispositivi registrati** se si è scelto "All members (including guests)" (Tutti i membri inclusi i guest) OPPURE
    - **Disponibile con o senza registrazione** se si è scelto "All members (excluding guests)" (Tutti i membri esclusi i guest) o "Facoltativo".
9. Selezionare **Gruppi inclusi** e quindi in Rendi questa app disponibile per tutti gli utenti selezionare **Sì**.
10. Fare clic su **OK** e di nuovo su **OK**.
11. Fare clic su **Save**.

### <a name="add-an-app-configuration-policy-for-slack-for-emm"></a>Aggiungere un criterio di configurazione dell'app per Slack per EMM
Aggiungere un criterio di configurazione dell'app per Slack per EMM su iOS. I criteri di configurazione dell'app per i dispositivi gestiti sono specifici della piattaforma, quindi è necessario aggiungere un criterio separato per gli utenti di Slack su dispositivi Android.
1. In Intune selezionare **App client** > **Criteri di configurazione dell'app** > **Aggiungi**.
2. In Nome immettere Test criteri di configurazione dell'app Slack.
3. In Tipo di registrazione del dispositivo selezionare **Dispositivi gestiti**.
4. In Piattaforma selezionare **iOS**.
5. Selezionare **App associata**.
6. Nella barra di ricerca immettere "Slack per EMM" e selezionare l'app.
7. Fare clic su **OK** e selezionare **Impostazioni di configurazione**. 
8. Scegliere **OK** e quindi **Aggiungi**.
9. Nella barra di ricerca immettere "Test criteri di configurazione dell'app Slack" e selezionare il criterio appena aggiunto.
10. In Gestisci selezionare **Assegnazioni**.
11. In Assegna a selezionare **Tutti gli utenti e tutti i dispositivi**.
12. Fare clic su **Save**.

### <a name="optional-create-an-ios-device-compliance-policy"></a>(Facoltativo) Creare un criterio di conformità per i dispositivi iOS
Configurare i criteri di conformità del dispositivo di Intune per impostare le condizioni che deve soddisfare un dispositivo per essere considerato conforme. Per questa esercitazione verranno creati criteri di conformità per i dispositivi iOS. I criteri di conformità sono specifici della piattaforma, quindi è necessario creare un criterio separato per gli utenti di Slack su dispositivi Android.
1. In Intune selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
2. In Nome immettere "Test criteri di conformità iOS".
3. In Descrizione immettere "Test criteri di conformità iOS".
4. In Piattaforma selezionare **iOS**.
5. Selezionare **Integrità del dispositivo**. Accanto a Dispositivi Jailbroken selezionare **Blocca** e quindi scegliere **OK**.
6. Selezionare **Sicurezza del sistema** e immettere le impostazioni della password. Per questa esercitazione, selezionare le seguenti impostazioni consigliate:
    - Per Richiedi una password per sbloccare i dispositivi mobili selezionare **Rendi obbligatorio**.
    - Per Password semplici selezionare **Blocca**.
    - Per Lunghezza minima password immettere 4.
    - Per Tipo di password richiesto scegliere **Alfanumerico**.
    - Per Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password scegliere **Immediatamente**.
    - Per Scadenza password (giorni) immettere 41.
    - Per Numero di password precedenti di cui impedire il riutilizzo immettere 5.
7. Fare clic su **OK** e quindi di nuovo su **OK**.
8. Scegliere **Crea**.

## <a name="set-up-slack-on-android-work-profile-devices"></a>Configurare Slack nei dispositivi del profilo di lavoro Android
Aggiungere l'app Slack di Google Play gestita al tenant di Intune e creare un criterio di configurazione dell'app per consentire agli utenti Android dell'organizzazione di accedere a Slack con Intune come provider EMM.

### <a name="add-slack-to-intune"></a>Aggiungere Slack a Intune
Aggiungere Slack come app di Google Play gestita in Intune e assegnare gli utenti di Slack. Le app sono specifiche della piattaforma, quindi è necessario aggiungere un'app di Intune separata per gli utenti di Slack nei dispositivi iOS.
1. In Intune selezionare **App client** > **App** > **Aggiungi**.
2. In Tipo di app selezionare **App dello Store - Google Play gestito**.
3. Selezionare **Google Play gestito - Approva**. Immettere il termine di ricerca "Slack per EMM" e selezionare l'app.
4. Selezionare **Approva**.
5. Nella barra di ricerca immettere "Slack" e selezionare l'app appena aggiunta.
6. In Gestisci selezionare **Assegnazioni**.
7. Selezionare **Aggiungi gruppi**. A seconda degli utenti interessati dall'attivazione di EMM per Slack, in **Tipo di assegnazione** è possibile selezionare:
    - **Disponibile per i dispositivi registrati** se si è scelto "All members (including guests)" (Tutti i membri inclusi i guest) OPPURE
    - **Disponibile con o senza registrazione** se si è scelto "All members (excluding guests)" (Tutti i membri esclusi i guest) o "Facoltativo".
8. Selezionare Gruppi inclusi e quindi in Rendi questa app disponibile per tutti gli utenti selezionare **Sì**.
9. Fare clic su **OK** e di nuovo su **OK**.
10. Fare clic su **Save**.

### <a name="add-an-app-configuration-policy-for-slack"></a>Aggiungere un criterio di configurazione dell'app per Slack
Aggiungere un criterio di configurazione dell'app per Slack. I criteri di configurazione dell'app per i dispositivi gestiti sono specifici della piattaforma, quindi è necessario aggiungere un criterio separato per gli utenti di Slack su dispositivi iOS.
1. In Intune selezionare **App client** > **Criteri di configurazione dell'app** > **Aggiungi**.
2. In Nome immettere Test criteri di configurazione dell'app Slack.
3. In Tipo di registrazione del dispositivo selezionare **Dispositivi gestiti**.
4. In Piattaforma selezionare **Android**.
5. Selezionare **App associata**.
6. Nella barra di ricerca immettere "Slack" e selezionare l'app.
7. Scegliere **OK** e selezionare **Impostazioni di configurazione**.
    - Per informazioni sulle chiavi di configurazione e i relativi valori, consultare la documentazione nella scheda "Technical" (Informazioni tecniche) della [pagina Web AppConfig di Slack](https://www.appconfig.org/company/slack/).
8. Fare clic su **OK** e quindi selezionare **Aggiungi**.
9. Nella barra di ricerca immettere "Test criteri di configurazione dell'app Slack" e selezionare il criterio appena aggiunto.
10. In Gestisci selezionare **Assegnazioni**.
11. In Assegna a selezionare **Tutti gli utenti e tutti i dispositivi**.
12. Fare clic su **Save**.

### <a name="optional-create-an-android-device-compliance-policy"></a>(Facoltativo) Creare un criterio di conformità per i dispositivi Android
Configurare i criteri di conformità del dispositivo di Intune per impostare le condizioni che deve soddisfare un dispositivo per essere considerato conforme. Per questa esercitazione verrà creato un criterio di conformità per i dispositivi Android. I criteri di conformità sono specifici della piattaforma, quindi è necessario creare un criterio separato per gli utenti di Slack su dispositivi iOS.
1. In Intune selezionare **Conformità del dispositivo** > **Criteri** > **Crea criterio**.
2. In Nome immettere "Test criteri di conformità Android".
3. In Descrizione immettere "Test criteri di conformità Android".
4. In Piattaforma selezionare **Android Enterprise**.
5. In Tipo di profilo selezionare **Profilo di lavoro**.
6. Selezionare **Integrità del dispositivo**. Accanto a Dispositivi rooted selezionare **Blocca** e quindi scegliere **OK**.
7. Selezionare **Sicurezza del sistema** e immettere le **Impostazioni della password**. Per questa esercitazione, selezionare le seguenti impostazioni consigliate:
    - Per Richiedi una password per sbloccare i dispositivi mobili selezionare **Rendi obbligatorio**.
    - In Tipo di password richiesto selezionare **Almeno numerico**.
    - Per Lunghezza minima password immettere 4.
    - Per Numero massimo di minuti dopo il blocco dello schermo prima che venga richiesta una password scegliere **15 minuti**.
    - Per Scadenza password (giorni) immettere 41.
    - Per Numero di password precedenti di cui impedire il riutilizzo immettere 5.
8. Fare clic su **OK** e di nuovo su **OK**.
9. Scegliere **Crea**.

## <a name="launch-slack"></a>Avviare Slack

Con i criteri appena creati, i dispositivi del profilo di lavoro Android o iOS che cercano di accedere a una delle aree di lavoro dovranno essere registrati con Intune. Per testare questo scenario, provare ad avviare Slack per EMM in un dispositivo iOS registrato con Intune o ad avviare Slack in un dispositivo del profilo di lavoro Android registrato con Intune. 

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione:
- Si è impostato Intune come provider di Enterprise Mobility Management (EMM) in Slack Enterprise Grid. 
- Sono stati creati criteri di configurazione delle app per gestire l'app Slack per EMM in iOS e l'app Slack per i dispositivi del profilo di lavoro Android.
- Sono stati creati criteri di conformità per i dispositivi Intune per impostare le condizioni che i dispositivi Android e iOS devono soddisfare per essere considerati conformi.

Per altre informazioni sui criteri di configurazione delle app, vedere [Criteri di configurazione delle app per Microsoft Intune](app-configuration-policies-overview.md). Per altre informazioni sui criteri di conformità dei dispositivi, vedere [Impostare regole sui dispositivi per consentire l'accesso alle risorse dell'organizzazione tramite Intune](../protect/device-compliance-get-started.md).
