---
title: Registrare i dispositivi iOS - Device Enrollment Program
titlesuffix: Azure portal
description: "Informazioni su come registrare i dispositivi iOS di proprietà dell'azienda usando Device Enrollment Program (nuova interfaccia utente).\""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b97da0c8ca0a1e3891a64508b565749dec06de93
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Registrare automaticamente i dispositivi iOS nel programma Device Enrollment Program di Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Differenze di interfaccia utente temporanee
> Le interfacce utente per le funzionalità descritte in questa pagina sono in corso di aggiornamento. Questi aggiornamenti verranno distribuiti a tutti gli account utente entro la fine di aprile.
>
> Se la pagina **Registrazione del dispositivo** è simile all'immagine seguente, sono disponibili le interfacce utente aggiornate ed è possibile usare questa pagina della Guida.
>
> ![Nuova interfaccia utente](./media/appleenroll-newui.png)
>
> In caso contrario, se la pagina **Registrazione del dispositivo** è simile all'immagine seguente, l'account non è ancora stato aggiornato alla nuova interfaccia utente. Passare a [questa pagina della Guida](device-enrollment-program-enroll-ios.md).
>
> ![Interfaccia utente precedente](./media/appleenroll-oldui.png)

Questo argomento offre informazioni utili per abilitare la registrazione dei dispositivi iOS acquistati tramite [Device Enrollment Program (DEP)](https://deploy.apple.com) di Apple. È possibile abilitare la registrazione DEP per un numero elevato di dispositivi senza interventi diretti. Si possono fornire i dispositivi iPhone e iPad direttamente agli utenti e quando l'utente attiva il dispositivo, l'Assistente configurazione viene eseguito con impostazioni preconfigurate e il dispositivo viene registrato nella gestione.

Per abilitare la registrazione DEP, si usano i portali di Intune e DEP di Apple. È necessario un elenco di numeri di serie o un numero di ordine di acquisto per poter assegnare i dispositivi a Intune per la gestione. Si creano profili di registrazione DEP contenenti le impostazioni da applicare ai dispositivi durante la registrazione.

La registrazione DEP non funziona con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="what-is-supervised-mode"></a>Che cos'è la modalità con supervisione?
Apple ha introdotto la modalità con supervisione in iOS 5. Un dispositivo iOS in modalità con supervisione può essere gestito con un numero maggiore di controlli. Questa modalità è quindi particolarmente utile per dispositivi di proprietà dell'azienda. Intune supporta la configurazione di dispositivi per la modalità con supervisione nell'ambito del programma Apple Device Enrollment Program (DEP). 

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
- [Autorità di gestione dei dispositivi mobili](mdm-authority-set.md)
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Ottenere un token DEP Apple

Per registrare i dispositivi iOS in DEP, è necessario un file di token DEP (con estensione p7m) da Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi DEP di proprietà dell'azienda. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Per creare un token DEP si usa il portale DEP di Apple. È anche possibile usare il portale DEP per assegnare i dispositivi a Intune per la gestione.

> [!NOTE]
> Se si elimina il token dal portale classico di Intune prima della migrazione ad Azure, è possibile che Intune ripristini il token DEP Apple eliminato. È possibile eliminare nuovamente il token DEP dal portale di Azure. È possibile eliminare nuovamente il token DEP dal portale di Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare il token.

1. Nel portale di Azure in Intune scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > **Aggiungi**.

    ![Ottenere un token del programma di registrazione.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Scegliere **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.
  ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/device-enrollment-program-enroll-ios/image02.png)

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
Nella casella **Token Apple** passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi scegliere **Crea**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati. Intune si sincronizza automaticamente con Apple per verificare l'account DEP.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple

Ora che è stato installato il token, è possibile creare un profilo di registrazione per i dispositivi DEP. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nel portale di Azure in Intune scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione**.
2. Selezionare un token, scegliere **Profili** e quindi scegliere **Crea profilo**.
    ![Screenshot di Crea profilo.](./media/device-enrollment-program-enroll-ios/image04.png)
3. In **Crea profilo** immettere un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti. È possibile usare questo campo **Nome** per creare un gruppo dinamico in Azure Active Directory. Usare il nome del profilo per definire il parametro enrollmentProfileName per assegnare i dispositivi con questo profilo di registrazione. Altre informazioni sui [gruppi dinamici di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).
    ![Nome e descrizione del profilo.](./media/device-enrollment-program-enroll-ios/image05.png)

4. In **Affinità utente** scegliere se i dispositivi con questo profilo devono essere registrati con o senza un utente assegnato.
    - **Registra con affinità utente**: scegliere questa opzione per i dispositivi che appartengono a utenti e che vogliono usare il portale aziendale per servizi come l'installazione di app. Questa opzione consente anche agli utenti di autenticare i dispositivi tramite il portale aziendale. Per l'affinità utente è richiesto [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Registra senza affinità utente**: scegliere questa opzione per un dispositivo non associato a un singolo utente. Usare questa opzione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app come l'app Portale aziendale non funzionano.

5. Se si sceglie **Registra con affinità utente**, è possibile consentire agli utenti di eseguire l'autenticazione con il portale aziendale invece di Assistente configurazione Apple.

    ![Autenticazione con il portale aziendale.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > L'autenticazione a più fattori (MFA) non funziona durante la registrazione DEP in presenza di proprietà del profilo impostate su **Registra con affinità utente** e se non si usa un portale aziendale. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto nei dispositivi. I dispositivi non possono richiedere agli utenti di modificare la password al primo accesso. Inoltre, agli utenti con password scadute non viene richiesto di reimpostare la password durante la registrazione e devono reimpostarla da un altro dispositivo.

6. Scegliere **Impostazioni di gestione dei dispositivi** e specificare se si vogliono includere i dispositivi con questo profilo nella supervisione.
    I dispositivi **con supervisione** offrono più opzioni di gestione e il blocco attivazione viene disabilitato per impostazione predefinita. È consigliabile usare il programma DEP come meccanismo per l'abilitazione della modalità con supervisione, soprattutto per le organizzazioni che distribuiscono un numero elevato di dispositivi iOS.

    Gli utenti vengono informati che i dispositivi sono inclusi nella supervisione in due modi:

    - Nella schermata di blocco viene visualizzata l'indicazione: "This iPhone is managed by Contoso." (Questo iPhone è gestito da Contoso)
    - Nella schermata **Impostazioni** > **Generale** > **Informazioni su** viene visualizzata l'indicazione: "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device." (Questo iPhone è soggetto a supervisione. Contoso può monitorare il traffico Internet e individuare il dispositivo)

     > [!NOTE]
     > Per reimpostare un dispositivo registrato senza supervisione in modo da includerlo nella supervisione, è possibile usare solo Apple Configurator. Per reimpostare il dispositivo in questo modo, è necessario connettere un dispositivo iOS a un computer Mac con un cavo USB. Per altre informazioni vedere la [documentazione di Apple Configurator](http://help.apple.com/configurator/mac/2.3).
     
7. Scegliere se usare o meno la registrazione bloccata per i dispositivi con questo profilo. La **registrazione bloccata** disabilita le impostazioni di iOS che consentono la rimozione del profilo di gestione dal menu **Impostazioni**. Dopo la registrazione del dispositivo, non è possibile modificare questa impostazione senza ripristinare le impostazioni predefinite del dispositivo. Per tali dispositivi, la modalità di gestione **Supervisione eseguita** deve essere impostata su *Sì*. 

8. Scegliere se si vuole o meno che i dispositivi con questo profilo possano **eseguire la sincronizzazione con i computer**. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

9. Se si sceglie **Consenti Apple Configurator per certificato** nel passaggio precedente, scegliere un certificato di Apple Configurator da importare.

10. Scegliere **OK**.

11. Scegliere **Impostazioni dell'Assistente configurazione** per configurare le impostazioni di profilo seguenti: ![Personalizzazione dell'Assistente configurazione.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)

    | Impostazione | Descrizione |
    | --- | --- |
    | **Nome reparto** | Viene visualizzata quando gli utenti toccano **Informazioni configurazione** durante l'attivazione. |
    | **Telefono del reparto** | Viene visualizzata quando l'utente fa clic sul pulsante **Richiesta di assistenza** durante l'attivazione. |
    | **Opzioni di Assistente configurazione** | Le impostazioni facoltative seguenti possono essere configurate in un secondo momento nel menu **Impostazioni** di iOS. |
    | **Passcode** | Richiedere un passcode durante l'attivazione. Richiedere sempre un passcode, a meno che il dispositivo non sia protetto o l'accesso al dispositivo non venga controllato in un altro modo, ad esempio con la modalità tutto schermo, che limita l'uso del dispositivo a una sola app. |
    | **Servizi di posizione** | Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione. |
    | **Recupera** | Se l'opzione è abilitata, Assistente configurazione richiede il backup in iCloud durante l'attivazione. |
    | **ID iCloud e Apple** | Se l'opzione è abilitata, Assistente configurazione richiede all'utente di accedere a un ID Apple e la schermata App e dati consentirà il ripristino del dispositivo dal backup in iCloud. |
    | **Termini e condizioni** | Se l'opzione è abilitata, Assistente configurazione richiede di accettare i termini e condizioni Apple durante l'attivazione. |
    | **Touch ID** | Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione. |
    | **Apple Pay** | Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione. |
    | **Zoom** | Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione. |
    | **Siri** | Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione. |
    | **Dati di diagnostica** | Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione. |

12. Scegliere **OK**.

13. Per salvare il profilo, scegliere **Crea**.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti
Adesso che Intune ha le autorizzazioni per gestire i dispositivi, è possibile sincronizzare Intune con Apple per visualizzare i dispositivi gestiti nel portale di Azure in Intune.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token nell'elenco > **Dispositivi** > **Sincronizza**. ![Schermata del nodo Enrollment Program Devices selezionato e con il collegamento Sincronizza selezionato.](./media/device-enrollment-program-enroll-ios/image06.png)
  
  Per soddisfare le condizioni Apple per un traffico DEP accettabile, Intune impone le seguenti restrizioni:
  - Una sincronizzazione completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna ogni numero di serie Apple assegnato a Intune. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
  - Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.
  - Intune sincronizza con Apple i dispositivi nuovi e rimossi ogni 24 ore.

## <a name="assign-an-enrollment-profile-to-devices"></a>Assegnare un profilo DEP ai dispositivi
Prima della registrazione è necessario assegnare ai dispositivi un profilo DEP.

>[!NOTE]
>È anche possibile assegnare i numeri di serie ai profili nel pannello **Numeri di serie Apple**.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo**  >  **Registrazione Apple**  >  **Token del programma di registrazione** > scegliere un token nell'elenco.
2. Scegliere **Dispositivi** > scegliere i dispositivi nell'elenco > **Assegna profilo**.
3. In **Assegna profilo** scegliere un profilo per i dispositivi e quindi scegliere **Assegna**.

### <a name="assign-a-default-profile"></a>Assegnare un profilo predefinito

È possibile selezionare un profilo predefinito da applicare a tutti i dispositivi da registrare con un token specifico.

1. In Intune nel portale di Azure scegliere **Registrazione del dispositivo**  >  **Registrazione Apple**  >  **Token del programma di registrazione** > scegliere un token nell'elenco.
2. Scegliere **Imposta profilo predefinito**, scegliere un profilo nell'elenco a discesa e quindi scegliere **Salva**. Questo profilo verrà applicato a tutti i dispositivi registrati con il token.

## <a name="distribute-devices"></a>Distribuire i dispositivi
Fino a questo punto sono state abilitate la gestione e la sincronizzazione tra Apple e Intune ed è stato assegnato un profilo per consentire la registrazione dei dispositivi DEP. È ora possibile distribuire i dispositivi agli utenti. I dispositivi con affinità utente richiedono che a ogni utente sia assegnata una licenza di Intune. Per i dispositivi senza affinità utente è necessaria una licenza dispositivo. Un dispositivo attivato non può applicare un profilo di registrazione se non vengono ripristinate le impostazioni predefinite del dispositivo.

Vedere [Registrare il dispositivo iOS in Intune con Device Enrollment Program](/intune-user-help/enroll-your-device-dep-ios).


