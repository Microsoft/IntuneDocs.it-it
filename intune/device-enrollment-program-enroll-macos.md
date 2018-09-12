---
title: Registrare i dispositivi macOS - Device Enrollment Program
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi macOS di proprietà dell'azienda usando Device Enrollment Program.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 18b4ab35627e1ccb694104f3f5800e5fb07dd1c7
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313427"
---
# <a name="automatically-enroll-macos-devices-with-apples-device-enrollment-program"></a>Registrare automaticamente i dispositivi macOS nel programma Device Enrollment Program di Apple

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo include informazioni utili per configurare la registrazione dei dispositivi macOS acquistati tramite [Device Enrollment Program (DEP)](https://deploy.apple.com) di Apple. È possibile configurare la registrazione DEP per un numero elevato di dispositivi senza interventi diretti. È possibile fornire i dispositivi macOS direttamente agli utenti. Quando l'utente attiva il dispositivo, l'Assistente configurazione viene eseguito con impostazioni preconfigurate e il dispositivo viene registrato nella gestione di Intune.

Per configurare la registrazione DEP, si usano i portali di Intune e DEP di Apple. Si creano profili di registrazione DEP contenenti le impostazioni da applicare ai dispositivi durante la registrazione.

La registrazione DEP non funziona con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

<!--
**Steps to enable enrollment programs from Apple**
1. [Get an Apple DEP token and assign devices](#get-the-apple-dep-token)
2. [Create an enrollment profile](#create-an-apple-enrollment-profile)
3. [Synchronize DEP-managed devices](#sync-managed-device)
4. [Assign DEP profile to devices](#assign-an-enrollment-profile-to-devices)
5. [Distribute devices to users](#end-user-experience-with-managed-devices)
-->
## <a name="prerequisites"></a>Prerequisiti
- Dispositivi acquistati tramite il programma [Device Enrollment Program di Apple](http://deploy.apple.com)
- Un elenco di numeri di serie o un numero di ordine di acquisto. 
- [Autorità di gestione dei dispositivi mobili](mdm-authority-set.md)
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Ottenere un token DEP Apple

Per registrare i dispositivi macOS in DEP, è necessario un file di token DEP (con estensione p7m) da Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi DEP di proprietà dell'azienda. Consente anche a Intune di caricare profili di registrazione in Apple e di assegnare questi profili ai dispositivi.

Per creare un token DEP si usa il portale DEP di Apple. È anche possibile usare il portale DEP per assegnare i dispositivi a Intune per la gestione.

> [!NOTE]
> Se si elimina il token dal portale classico di Intune prima della migrazione ad Azure, è possibile che Intune ripristini il token DEP Apple eliminato. È possibile eliminare nuovamente il token DEP dal portale di Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare il token.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > **Aggiungi**.

    ![Ottenere un token del programma di registrazione.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Concedere a Microsoft l'autorizzazione per l'invio di informazioni su utenti e dispositivi ad Apple selezionando **Accetto**.

   ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/device-enrollment-program-enroll-ios-newui/add-enrollment-program-token-pane.png)

3. Scegliere **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Passaggio 2: Usare la chiave per scaricare un token da Apple.

1. Scegliere **Creare un token tramite Apple Device Enrollment Program** per aprire il portale del programma di distribuzione Apple e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token DEP.
2.  Nel [portale dei programmi di distribuzione](https://deploy.apple.com) di Apple scegliere **Inizia** per **Device Enrollment Program**.

3. Nella pagina **Gestisci server** scegliere **Aggiungi server MDM**.
4. Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.

5. Viene visualizzata la finestra di dialogo **Aggiungi &lt;NomeServer&gt;** che richiede di **caricare la chiave pubblica**. Fare clic su **Scegli file** per caricare il file PEM e scegliere **Avanti**.

6. Passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Gestione dei dispositivi**.
7. Nella sezione **Scegliere dispositivi per** specificare come vengono identificati i dispositivi:
    - **Numero di serie**
    - **Numero di ordine**
    - **Carica file CSV**.

   ![Schermata in cui viene specificata la scelta dei dispositivi in base al numero di serie, viene impostata l'azione di selezione su Assegna a server e viene selezionato il nome del server.](./media/enrollment-program-token-specify-serial.png)

8. In **Scegliere un'azione** scegliere **Assegna al server,** scegliere il &lt;nome del serve&gt;r specificato per Microsoft Intune e quindi scegliere **OK**. Il portale Apple assegna i dispositivi specificati al server di Intune per la gestione e quindi visualizza il messaggio **Assegnazione completata**.

   Nel portale Apple passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Visualizza cronologia di assegnazione** per visualizzare un elenco di dispositivi con la rispettiva assegnazione di server MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passaggio 3. Salvare l'ID Apple usato per creare il token.

Nel portale di Azure in Intune specificare l'ID Apple per riferimenti futuri.

![Screenshot della specifica dell'ID Apple usato per creare il token DEP e passare al token DEP.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Passaggio 4. Caricare il token.
Nella casella **Token Apple** passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi scegliere **Crea**. Con il certificato push, Intune può registrare e gestire i dispositivi macOS eseguendo il push dei criteri nei dispositivi registrati. Intune si sincronizza automaticamente con Apple per verificare l'account DEP.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple

Ora che è stato installato il token, è possibile creare un profilo di registrazione per i dispositivi DEP. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nel portale di Azure in Intune scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione**.
2. Selezionare un token, scegliere **Profili** e quindi scegliere **Crea profilo**.

    ![Screenshot di Crea profilo.](./media/device-enrollment-program-enroll-ios/image04.png)

3. In **Crea profilo** immettere un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti. È possibile usare questo campo **Nome** per creare un gruppo dinamico in Azure Active Directory. Usare il nome del profilo per definire il parametro enrollmentProfileName per assegnare i dispositivi con questo profilo di registrazione. Altre informazioni sui [gruppi dinamici di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nome e descrizione del profilo.](./media/device-enrollment-program-enroll-macos/createprofile.png)

4. Per **Piattaforma** scegliere **macOS**.

5. In **Affinità utente** scegliere se i dispositivi con questo profilo devono essere o meno registrati con o senza un utente assegnato.
    - **Registra con affinità utente**: scegliere questa opzione per i dispositivi che appartengono a utenti e che vogliono usare l'app Portale aziendale per servizi come l'installazione di app. Se si usa ADFS, per l'affinità utente è richiesto un [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint). L'autenticazione a più fattori non è supportata per i dispositivi DEP macOS con affinità utente.

    - **Registra senza affinità utente**: scegliere questa opzione per un dispositivo non associato a un singolo utente. Usare questa opzione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app come l'app Portale aziendale non funzionano.

6. Scegliere **Impostazioni di gestione dei dispositivi** e specificare se si vuole o meno usare la registrazione bloccata per i dispositivi con questo profilo. La **registrazione bloccata** disabilita le impostazioni di macOS che consentono la rimozione del profilo di gestione dal menu **Preferenze del Sistema** o tramite il **Terminale**. Dopo la registrazione del dispositivo, non è possibile modificare questa impostazione senza cancellare il dispositivo.

    ![Screenshot di Impostazioni di gestione dei dispositivi.](./media/device-enrollment-program-enroll-macos/devicemanagementsettingsblade-macos.png)
 
7. Scegliere **OK**.

8. Scegliere **Impostazioni dell'Assistente configurazione** per configurare le impostazioni di profilo seguenti: ![Personalizzazione dell'Assistente configurazione.](./media/device-enrollment-program-enroll-macos/setupassistantcustom-macos.png)

    | Impostazioni di reparto | Descrizione |
    |---|---|
    | <strong>Nome reparto</strong> | Viene visualizzata quando gli utenti toccano <strong>Informazioni configurazione</strong> durante l'attivazione. |
    | <strong>Telefono del reparto</strong> | Viene visualizzata quando l'utente fa clic sul pulsante <strong>Richiesta di assistenza</strong> durante l'attivazione. |

  È possibile scegliere di visualizzare o nascondere varie schermate dell'Assistente configurazione nel dispositivo quando l'utente lo configura.
  - Se si sceglie **Nascondi**, la schermata non verrà visualizzata durante la configurazione. Dopo aver configurato il dispositivo, l'utente può comunque ancora usare il menu **Impostazioni** menu per configurare la funzionalità.
  - Se si sceglie **Mostra**, la schermata verrà visualizzata durante la configurazione. L'utente può a volte ignorare la schermata senza eseguire azioni. Ma, in un secondo momento, può usare il menu **Impostazioni** del dispositivo per configurare la funzionalità. 


    | Impostazioni delle schermate dell'Assistente configurazione | Se si sceglie **Mostra**, durante la configurazione il dispositivo... |
    |------------------------------------------|------------------------------------------|
    | <strong>Passcode</strong> | Richiederà un passcode all'utente. Richiedere sempre un passcode, a meno che il dispositivo non sia protetto o l'accesso al dispositivo non venga controllato in un altro modo, ad esempio con la modalità tutto schermo, che limita l'uso del dispositivo a una sola app. |
    | <strong>Servizi di posizione</strong> | Richiederà la posizione all'utente. |
    | <strong>Recupera</strong> | Visualizzerà la schermata **App e dati**. Questa schermata offre all'utente la possibilità di ripristinare o trasferire i dati da iCloud Backup durante la configurazione del dispositivo. |
    | <strong>ID iCloud e Apple</strong> | Offrirà all'utente la possibilità di accedere con l'**ID Apple** e di usare **iCloud**.                         |
    | <strong>Termini e condizioni</strong> | Richiederà all'utente di accettare i termini e le condizioni Apple. |
    | <strong>Touch ID</strong> | Offrirà all'utente la possibilità di impostare l'identificazione con impronta digitale per il dispositivo. |
    | <strong>Apple Pay</strong> | Offrirà all'utente la possibilità di configurare Apple Pay nel dispositivo. |
    | <strong>Zoom</strong> | Offrirà all'utente la possibilità di ingrandire la visualizzazione durante la configurazione del dispositivo. |
    | <strong>Siri</strong> | Offrirà all'utente la possibilità di configurare Siri. |
    | <strong>Dati di diagnostica</strong> | Visualizzerà la schermata **Diagnostica** all'utente. Questa schermata offre all'utente la possibilità di inviare dati di diagnostica ad Apple. |
    | <strong>FileVault</strong> | Offrirà all'utente la possibilità di configurare la crittografia FileVault. |
    | <strong>Diagnostica iCloud</strong> | Offrirà all'utente la possibilità di inviare dati di diagnostica iCloud ad Apple. |
    | <strong>Registrazione</strong>| Richiederà all'utente di registrare il dispositivo. |

   

10. Scegliere **OK**.

11. Per salvare il profilo, scegliere **Crea**.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti
Adesso che Intune ha le autorizzazioni per gestire i dispositivi, è possibile sincronizzare Intune con Apple per visualizzare i dispositivi gestiti nel portale di Azure in Intune.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token nell'elenco > **Dispositivi** > **Sincronizza**. ![Schermata del nodo Enrollment Program Devices selezionato e con il collegamento Sincronizza selezionato.](./media/device-enrollment-program-enroll-ios/image06.png)

   Per soddisfare le condizioni Apple per un traffico DEP accettabile, Intune impone le seguenti restrizioni:
   - Una sincronizzazione completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune recupera l'elenco aggiornato completo dei numeri di serie assegnati al server MDM di Apple connesso a Intune. Se un dispositivo del Device Enrollment Program viene eliminato dal portale di Intune senza che ne sia stata annullata l'assegnazione dal server Apple MDM nel portale DEP, il dispositivo non potrà essere reimportato in Intune fino a quando non viene eseguita la sincronizzazione completa.   
   - La sincronizzazione viene eseguita automaticamente ogni 24 ore. È anche possibile eseguire la sincronizzazione facendo clic sul pulsante **Sincronizza** (non più di una volta ogni 15 minuti). Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Il pulsante **Sincronizza** rimane disabilitato finché non viene completata la sincronizzazione. La sincronizzazione aggiorna lo stato dei dispositivi esistenti e importa i nuovi dispositivi assegnati al server MDM di Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Assegnare un profilo DEP ai dispositivi
Prima della registrazione è necessario assegnare ai dispositivi un profilo DEP.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo**  >  **Registrazione Apple**  >  **Token del programma di registrazione** > scegliere un token nell'elenco.
2. Scegliere **Dispositivi** > scegliere i dispositivi nell'elenco > **Assegna profilo**.
3. In **Assegna profilo** scegliere un profilo per i dispositivi > **Assegna**.

### <a name="assign-a-default-profile"></a>Assegnare un profilo predefinito

È possibile selezionare un profilo predefinito macOS e iOS da applicare a tutti i dispositivi da registrare con un token specifico. 

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token nell'elenco.
2. Scegliere **Imposta profilo predefinito**, scegliere un profilo nell'elenco a discesa e quindi scegliere **Salva**. Questo profilo verrà applicato a tutti i dispositivi registrati con il token.

## <a name="distribute-devices"></a>Distribuire i dispositivi
Fino a questo punto sono state abilitate la gestione e la sincronizzazione tra Apple e Intune ed è stato assegnato un profilo per consentire la registrazione dei dispositivi DEP. È ora possibile distribuire i dispositivi agli utenti. I dispositivi con affinità utente richiedono che a ogni utente sia assegnata una licenza di Intune. Per i dispositivi senza affinità utente è necessaria una licenza dispositivo. Un dispositivo attivato non può applicare un profilo di registrazione fino a quando non viene cancellato il dispositivo.

## <a name="renew-a-dep-token"></a>Rinnovare un token DEP  
1. Passare a deploy.apple.com.  
2. In **Gestisci i server** scegliere il server MDM associato al file di token da rinnovare.
3. Scegliere **Genera nuovo token**.

    ![Screenshot della generazione di un nuovo token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Scegliere **Token del server**.  
5. In [Intune nel portale di Azure](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere il token.
    ![Screenshot dei token del programma di registrazione.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Scegliere **Rinnova il token** e immettere l'ID Apple usato per creare il token originale.  
    ![Screenshot della generazione di un nuovo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Caricare il token appena scaricato.  
9. Scegliere **Rinnova il token**. Viene visualizzata la conferma che il token è stato rinnovato.   
    ![Screenshot della conferma.](./media/device-enrollment-program-enroll-ios/confirmation.png)

## <a name="next-steps"></a>Passaggi successivi

Dopo la registrazione dei dispositivi macOS è possibile iniziare a [gestirli](device-management.md).