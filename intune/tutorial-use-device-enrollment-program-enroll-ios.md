---
title: 'Esercitazione: Usare Device Enrollment Program per registrare i dispositivi iOS in Intune'
titleSuffix: Microsoft Intune
description: In questa esercitazione verrà configurato il programma DEP di Apple per la registrazione dei dispositivi iOS in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up the Device Enrollment Program so that users can automatically enroll in Intune.
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9cd0eec492f5131e4015aa64eccb4c081c663ee
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61515670"
---
# <a name="tutorial-use-the-device-enrollment-program-to-enroll-ios-devices-in-intune"></a>Esercitazione: Usare Device Enrollment Program per registrare i dispositivi iOS in Intune
Device Enrollment Program (DEP) di Apple semplifica la registrazione dei dispositivi. Con Microsoft Intune e DEP, i dispositivi vengono registrati automaticamente la prima volta che l'utente accende il dispositivo. È pertanto possibile spedire i dispositivi a più utenti senza dover configurare ogni singolo dispositivo. 

In questa esercitazione si apprenderà come:
> [!div class="checklist"]
> * Ottenere un token DEP Apple
> * Creare un gruppo di dispositivi Autopilot
> * Creare un profilo di distribuzione Autopilot
> * Assegnare il profilo di distribuzione Autopilot al gruppo di dispositivi
> * Distribuire i dispositivi Windows agli utenti

Se non si dispone di una sottoscrizione Intune, è possibile [iscriversi per ottenere un account di prova gratuito](free-trial-sign-up.md).

## <a name="prerequisites"></a>Prerequisiti
- Dispositivi acquistati tramite il programma [Device Enrollment Program di Apple](http://deploy.apple.com)
- Impostare l'[autorità di gestione di dispositivi mobili](mdm-authority-set.md)
- Ottenere un [certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Ottenere un token DEP Apple
Prima di registrare i dispositivi iOS con DEP, è necessario un file token con estensione pem del programma DEP di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi DEP di proprietà dell'azienda. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Per creare un token DEP si usa il portale DEP di Apple. È anche possibile usare il portale DEP per assegnare i dispositivi a Intune per la gestione.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > **Aggiungi**.

2. Concedere a Microsoft l'autorizzazione per l'invio di informazioni su utenti e dispositivi ad Apple selezionando **Accetto**.

   ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Scegliere **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.

4. Scegliere **Creare un token tramite Apple Device Enrollment Program** per aprire il portale del programma di distribuzione Apple e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token DEP.

5.  Nel [portale dei programmi di distribuzione](https://deploy.apple.com) di Apple scegliere **Inizia** per **Device Enrollment Program**.

4. Nella pagina **Gestisci server** scegliere **Aggiungi server MDM**.

5. Come **nome del server MDM** immettere *TestMDMServer* e quindi scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non corrisponde al nome o all'URL del server di Microsoft Intune.

6. Viene visualizzata la finestra di dialogo **Aggiungi &lt;NomeServer&gt;** che richiede di **caricare la chiave pubblica**. Selezionare **Scegli file**. per caricare il file PEM e scegliere **Avanti**.

6. Passare a **Programma di distribuzione** > **Programma di registrazione dispositivi** > **Gestione dei dispositivi**.
7. In **Scegli dispositivi per** scegliere **Numero di serie**. <!--ask Tiffany about this-->

8. In **Scegliere un'azione** scegliere **Assegna al server,** scegliere il &lt;nome del serve&gt;r specificato per Microsoft Intune e quindi scegliere **OK**. Il portale Apple assegna i dispositivi specificati al server di Intune per la gestione e quindi visualizza il messaggio **Assegnazione completata**.

   Nel portale Apple passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Visualizza cronologia di assegnazione** per visualizzare un elenco di dispositivi con la rispettiva assegnazione di server MDM.

9. Per riferimenti futuri, in Intune nel portale di Azure specificare l'ID Apple usato per creare il token.

    ![Screenshot della specifica dell'ID Apple usato per creare il token DEP e passare al token DEP.](./media/device-enrollment-program-enroll-ios/image03.png)

10. Nella casella **Token Apple** passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi scegliere **Crea**. 

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple
Ora che è stato installato il token, è possibile creare un profilo di registrazione per i dispositivi DEP. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nel portale di Azure in Intune scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione**.

2. Selezionare il token installato, scegliere **Profili** > **Crea profilo**.

3. In **Crea profilo** immettere *TestDEPProfile* per **Nome** e *Test DEP per dispositivi iOS* per **Descrizione**. Questi dettagli non vengono visualizzati agli utenti.

4. Per **Affinità utente** scegliere **Registra con affinità utente**. Questa opzione si applica ai dispositivi che appartengono a utenti che vogliono usare il portale aziendale per servizi come l'installazione di app.

5. Scegliere **No** in **Autenticazione con il Portale aziendale invece di Apple Setup Assistant**.

6. Scegliere **Impostazioni di gestione dei dispositivi** e scegliere **No** in **Supervisione eseguita**. I dispositivi di cui è stata eseguita la supervisione offrono un maggior numero di opzioni di gestione ma non verranno usati in questa esercitazione.

7. Scegliere **OK**.

8. Scegliere **Personalizzazione dell'Assistente configurazione** e immettere *Reparto esercitazione* per **Nome del reparto**. Questa stringa viene visualizzata agli utenti quando toccano **Informazioni sulla configurazione** durante l'attivazione del dispositivo.

9. In **Telefono del reparto** immettere un numero di telefono. Il numero viene visualizzato quando gli utenti toccano il pulsante **Richiesta di assistenza** durante l'attivazione.

10. È possibile scegliere **Mostra** o **Nascondi** per diverse schermate durante l'attivazione del dispositivo. Ai fini di questa esercitazione impostare **Passcode** su **Mostra** e tutte le altre opzioni su **Nascondi**.

11. Scegliere **OK** > **Crea**.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti

È ora possibile visualizzare i dispositivi assegnati al token.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token nell'elenco > **Dispositivi** > **Sincronizza**.

## <a name="assign-an-enrollment-profile-to-ios-devices"></a>Assegnare un profilo di registrazione ai dispositivi iOS

Prima della registrazione è necessario assegnare ai dispositivi un profilo DEP.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere il token nell'elenco.
2. Scegliere **Dispositivi** > scegliere i dispositivi nell'elenco > **Assegna profilo**.
3. In **Assegna profilo** scegliere un profilo per i dispositivi > **Assegna**.

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

È stata configurata la gestione e la sincronizzazione tra Apple e Intune ed è stato assegnato un profilo per consentire la registrazione dei dispositivi DEP. È ora possibile distribuire i dispositivi agli utenti. I dispositivi con affinità utente richiedono che a ogni utente sia assegnata una licenza di Intune.

## <a name="clean-up-resources"></a>Pulizia delle risorse

Se non si vogliono più usare dispositivi Autopilot, è possibile eliminarli.

- Se i dispositivi sono registrati in Intune, è necessario prima [eliminarli dal portale di Azure Active Directory](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal).

<!--ask tiffany how to do this-->

## <a name="next-steps"></a>Passaggi successivi

Sono disponibili altre informazioni sulle opzioni disponibili per la registrazione dei dispositivi iOS.

> [!div class="nextstepaction"]
> [Articolo con dettagli sulla registrazione DEP iOS](device-enrollment-program-enroll-ios.md)
