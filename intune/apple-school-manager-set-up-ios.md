---
title: Configurare la registrazione al programma Apple School Manager per i dispositivi iOS
titleSuffix: Microsoft Intune
description: Informazioni su come configurare la registrazione al programma Apple School Manager per i dispositivi iOS di proprietà dell'azienda con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c35a23e-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2d099d049892d71c36e4b01fb1a8af6f7ad25df1
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313410"
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Abilitare la registrazione di dispositivi iOS con Apple School Manager

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Questo articolo offre informazioni utili per abilitare la registrazione dei dispositivi iOS acquistati tramite il programma [Apple School Manager](https://school.apple.com/). Con Intune e Apple School Manager, è possibile registrare un numero elevato di dispositivi iOS senza interventi diretti. Quando uno studente o un insegnante accende il dispositivo, l'Assistente configurazione viene eseguito con impostazioni preconfigurate e il dispositivo viene registrato nella gestione.

Per abilitare la registrazione di Apple School Manager, si usano entrambi i portali di Intune e Apple School Manager. È necessario un elenco di numeri di serie o un numero di ordine di acquisto per poter assegnare i dispositivi a Intune per la gestione. Si creano profili di registrazione DEP contenenti le impostazioni da applicare ai dispositivi durante la registrazione.

La registrazione di Apple School Manager non può essere usata con il [programma Device Enrollment Program di Apple](device-enrollment-program-enroll-ios.md) o con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

**Prerequisiti**
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- [Autorità di gestione dei dispositivi mobili](mdm-authority-set.md)
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- Se si usa ADFS, per l'affinità utente è richiesto un [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Dispositivi acquistati dal programma [Apple School Management](http://school.apple.com)

## <a name="get-an-apple-token-and-assign-devices"></a>Ottenere un token Apple e assegnare i dispositivi

Per registrare i dispositivi iOS di proprietà dell'azienda in Apple School Manager, è necessario un file di token (con estensione p7m) di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi che partecipano al programma Apple School Manager. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili. Nel portale Apple è inoltre possibile assegnare i numeri di serie dei dispositivi da gestire.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-an-apple-token"></a>Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare un token Apple

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > **Aggiungi**.

   ![Ottenere un token del programma di registrazione.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Nel pannello **Token DEP** scegliere **Scarica la chiave pubblica** per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale Apple School Manager.
     ![Pannello Token DEP.](./media/device-enrollment-program-enroll-ios/image02.png)

### <a name="step-2-download-a-token-and-assign-devices"></a>Passaggio 2: Scaricare un token e assegnare i dispositivi
1. Scegliere **Crea un token tramite Apple School Manager** e accedere ad Apple School con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token di Apple School Manager.
2.  Nel [portale di Apple School Manager](https://school.apple.com) passare a **Server MDM** e quindi scegliere **Aggiungi server MDM** (in alto a destra).
3.  Immettere il **nome del server MDM**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.
   ![Screenshot del portale di Apple School Manager con l'opzione del numero di serie selezionata](./media/asm-server-assignment.png)

4.  Scegliere **Carica file** nel portale Apple, selezionare il file con estensione pem e quindi scegliere **Salva server MDM** (in basso a destra).
5.  Scegliere **Ottieni token** e quindi scaricare il file token del server (con estensione p7m) nel computer.
6. Passare ad **Assegnazioni di dispositivi** e **scegliere il dispositivo** inserendo manualmente i **numeri di serie**, il **numero di ordine** o **caricando un file CSV**.
     ![Screenshot del portale di Apple School Manager con l'opzione del numero di serie selezionata](./media/asm-device-assignment.png)
7.  Scegliere l'azione **Assegna al server**  e scegliere il **server MDM** creato.
8. Specificare come **scegliere i dispositivi** e quindi fornire dettagli e informazioni sul dispositivo.
9. Scegliere **Assegna al server**, selezionare il &lt;nome del server&gt; specificato per Microsoft Intune e fare clic su **OK**.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passaggio 3. Salvare l'ID Apple usato per creare questo token

Nel portale di Azure in Intune specificare l'ID Apple per riferimenti futuri.

![Screenshot della specifica dell'ID Apple usato per creare il token DEP e passare al token DEP.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token"></a>Passaggio 4. Caricare il token
Nella casella **Token Apple** passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi scegliere **Crea**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati. Intune sincronizza automaticamente i dispositivi Apple School Manager da Apple.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple
Ora che è stato installato il token, è possibile creare un profilo di registrazione per i dispositivi Apple School. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione**.
2. Selezionare un token, scegliere **Profili** e quindi scegliere **Crea profilo**.

3. In **Crea profilo** immettere un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti. È possibile usare questo campo **Nome** per creare un gruppo dinamico in Azure Active Directory. Usare il nome del profilo per definire il parametro enrollmentProfileName per assegnare i dispositivi con questo profilo di registrazione. Altre informazioni sui [gruppi dinamici di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

    ![Nome e descrizione del profilo.](./media/device-enrollment-program-enroll-ios/image05.png)

4. In **Affinità utente** scegliere se i dispositivi con questo profilo devono essere registrati con o senza un utente assegnato.
    - **Registra con affinità utente**: scegliere questa opzione per i dispositivi che appartengono a utenti e che vogliono usare il portale aziendale per servizi come l'installazione di app. Questa opzione consente anche agli utenti di autenticare i dispositivi tramite il portale aziendale. Se si usa ADFS, per l'affinità utente è richiesto un [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).   La modalità iPad condiviso di Apple School Manager richiede la registrazione dell'utente senza affinità utente.

    - **Registra senza affinità utente**: scegliere questa opzione per i dispositivi non associati a un singolo utente, come un dispositivo condiviso. Usare questa opzione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app come l'app Portale aziendale non funzionano.

5. Se si sceglie **Registra con affinità utente**, è possibile consentire agli utenti di eseguire l'autenticazione con il portale aziendale invece di Assistente configurazione Apple.

    ![Autenticazione con il portale aziendale.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Se si vuole eseguire una delle operazioni seguenti, impostare **Authenticate with Company Portal instead of Setup Assistant** (Autenticazione con il portale aziendale invece di Assistente configurazione) su **Sì**.
    >    - Usare l'autenticazione a più fattori
    >    - Richiedere agli utenti di modificare la password al primo accesso
    >    - Richiedere agli utenti di reimpostare le password scadute durante la registrazione
    >
    > Non sono supportate durante l'autenticazione con l'Assistente configurazione di Apple.

6. Scegliere **Impostazioni di gestione dei dispositivi** e specificare se si vogliono includere i dispositivi con questo profilo nella supervisione.
    I dispositivi **con supervisione** offrono più opzioni di gestione e il blocco attivazione viene disabilitato per impostazione predefinita. È consigliabile usare il programma DEP come meccanismo per l'abilitazione della modalità con supervisione, soprattutto per le organizzazioni che distribuiscono un numero elevato di dispositivi iOS.

    Gli utenti vengono informati che i dispositivi sono inclusi nella supervisione in due modi:

   - Nella schermata di blocco viene visualizzata l'indicazione: "This iPhone is managed by Contoso." (Questo iPhone è gestito da Contoso)
   - Nella schermata **Impostazioni** > **Generale** > **Informazioni su** viene visualizzata l'indicazione: "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device." (Questo iPhone è soggetto a supervisione. Contoso può monitorare il traffico Internet e individuare il dispositivo)

     > [!NOTE]
     > Per reimpostare un dispositivo registrato senza supervisione in modo da includerlo nella supervisione, è possibile usare solo Apple Configurator. Per reimpostare il dispositivo in questo modo, è necessario connettere un dispositivo iOS a un computer Mac con un cavo USB. Per altre informazioni vedere la [documentazione di Apple Configurator](http://help.apple.com/configurator/mac/2.3).

7. Scegliere se usare o meno la registrazione bloccata per i dispositivi con questo profilo. La **registrazione bloccata** disabilita le impostazioni di iOS che consentono la rimozione del profilo di gestione dal menu **Impostazioni**. Dopo la registrazione del dispositivo, non sarà possibile modificare questa impostazione senza cancellare il dispositivo. Per tali dispositivi, la modalità di gestione **Supervisione eseguita** deve essere impostata su *Sì*. 

8. Se si vuole consentire a più utenti l'accesso agli iPad registrati tramite un ID Apple gestito, scegliere **Sì** in **iPad condiviso** (questa opzione richiede l'impostazione di **Registra senza affinità utente** e della modalità **Supervisione eseguita** su **Sì**.) Gli ID Apple gestiti sono creati nel portale Apple School Manager. Altre informazioni sull'[iPad condiviso](education-settings-configure-ios-shared.md) e i [requisiti per l'iPad condiviso di Apple](https://help.apple.com/classroom/ipad/2.0/#/cad7e2e0cf56).

9. Scegliere se si vuole o meno che i dispositivi con questo profilo possano **eseguire la sincronizzazione con i computer**. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

10. Se si sceglie **Consenti Apple Configurator per certificato** nel passaggio precedente, scegliere un certificato di Apple Configurator da importare.

11. Scegliere **OK**.

12. Scegliere **Impostazioni dell'Assistente configurazione** per configurare le impostazioni di profilo seguenti: ![Personalizzazione dell'Assistente configurazione.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    |                 Impostazione                  |                                                                                               Descrizione                                                                                               |
    |------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    |     <strong>Nome reparto</strong>     |                                                             Viene visualizzata quando gli utenti toccano <strong>Informazioni configurazione</strong> durante l'attivazione.                                                              |
    |    <strong>Telefono del reparto</strong>     |                                                          Viene visualizzata quando l'utente fa clic sul pulsante <strong>Richiesta di assistenza</strong> durante l'attivazione.                                                          |
    | <strong>Opzioni di Assistente configurazione</strong> |                                                     Le impostazioni facoltative seguenti possono essere configurate in un secondo momento nel menu <strong>Impostazioni</strong> di iOS.                                                      |
    |        <strong>Passcode</strong>         | Richiedere un passcode durante l'attivazione. Richiedere sempre un passcode, a meno che il dispositivo non sia protetto o l'accesso al dispositivo non venga controllato in un altro modo, ad esempio con la modalità tutto schermo, che limita l'uso del dispositivo a una sola app. |
    |    <strong>Servizi di posizione</strong>    |                                                                 Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.                                                                  |
    |         <strong>Recupera</strong>         |                                                                Se l'opzione è abilitata, Assistente configurazione richiede il backup in iCloud durante l'attivazione.                                                                 |
    |   <strong>ID iCloud e Apple</strong>   |                         Se l'opzione è abilitata, Assistente configurazione richiede all'utente di accedere a un ID Apple e la schermata App e dati consentirà il ripristino del dispositivo dal backup in iCloud.                         |
    |  <strong>Termini e condizioni</strong>   |                                                   Se l'opzione è abilitata, Assistente configurazione richiede di accettare i termini e condizioni Apple durante l'attivazione.                                                   |
    |        <strong>Touch ID</strong>         |                                                                 Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.                                                                 |
    |        <strong>Apple Pay</strong>        |                                                                 Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.                                                                 |
    |          <strong>Zoom</strong>           |                                                                 Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.                                                                 |
    |          <strong>Siri</strong>           |                                                                 Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.                                                                 |
    |     <strong>Dati di diagnostica</strong>     |                                                                 Se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.                                                                 |


13. Scegliere **OK**.

14. Per salvare il profilo, scegliere **Crea**.

## <a name="connect-school-data-sync"></a>Connettere School Data Sync
(Facoltativo) Apple School Manager supporta la sincronizzazione dei dati dell'elenco di classi in Azure Active Directory (AD) tramite Microsoft School Data Sync (SDS). È possibile sincronizzare solo un token con SDS. Se si configura un altro token con School Data Sync, SDS verrà rimosso dal token assegnato in precedenza. Una nuova connessione sostituirà il token corrente. Completare i passaggi seguenti per usare SDS per sincronizzare i dati dell'istituto di istruzione.

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione**.
2. Selezionare un token di Apple School Manager e quindi scegliere **School Data Sync**.
3. In **School Data Sync** scegliere **Consenti**. Questa impostazione consente a Intune di connettersi con SDS in Office 365.
4. Per abilitare una connessione tra Apple School Manager e Azure AD, scegliere **Configura Microsoft School Data Sync**. Altre informazioni su [come configurare School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
5. Fare clic su **Salva** > **OK**.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti

Dopo l'assegnazione delle autorizzazioni per gestire i dispositivi Apple School Manager da Intune, è possibile sincronizzare Intune con il servizio Apple per visualizzare i dispositivi gestiti in Intune.

In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token nell'elenco > **Dispositivi** > **Sincronizza**. ![Schermata del nodo Enrollment Program Devices selezionato e con il collegamento Sincronizza selezionato.](./media/device-enrollment-program-enroll-ios/image06.png)

  Per soddisfare le condizioni Apple per un traffico DEP accettabile, Intune impone le seguenti restrizioni:
  - Una sincronizzazione completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna ogni numero di serie Apple assegnato a Intune. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
  - Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.
  - Intune sincronizza con Apple i dispositivi nuovi e rimossi ogni 24 ore.

>[!NOTE]
>È anche possibile assegnare i numeri di serie di Apple School Manager ai profili dal pannello **Dispositivi DEP**.

## <a name="assign-a-profile-to-devices"></a>Assegnare un profilo ai dispositivi
Ai dispositivi Apple School Manager gestiti da Intune deve essere assegnato un profilo di registrazione prima di registrarli.

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token del programma di registrazione** > scegliere un token nell'elenco.
2. Scegliere **Dispositivi** > scegliere i dispositivi nell'elenco > **Assegna profilo**.
3. In **Assegna profilo** scegliere un profilo per i dispositivi e quindi scegliere **Assegna**.

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

Fino a questo punto sono state abilitate la gestione e la sincronizzazione tra Apple e Intune ed è stato assegnato un profilo per consentire la registrazione dei dispositivi Apple School. È ora possibile distribuire i dispositivi agli utenti. Quando un dispositivo Apple School Manager iOS viene attivato, viene registrato per la gestione con Intune. Se il dispositivo è stato attivato ed è in uso, il profilo potrà essere applicato solo dopo la cancellazione del dispositivo.
