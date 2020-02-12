---
title: Registrare i dispositivi iOS - Device Enrollment Program
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi iOS di proprietà dell'azienda usando Device Enrollment Program.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 7ddbf360-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3fe6d1e2a0dcdeafad56d3facccb96f5d0721e4
ms.sourcegitcommit: 2b905913840d4133a7964fe4f54a58ea6e421e12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2020
ms.locfileid: "77074666"
---
# <a name="automatically-enroll-ios-devices-with-apples-device-enrollment-program"></a>Registrare automaticamente i dispositivi iOS nel programma Device Enrollment Program di Apple

È possibile configurare la registrazione di Intune per i dispositivi iOS acquistati tramite il programma [Device Enrollment Program (DEP)](https://deploy.apple.com) di Apple. DEP consente di registrare un numero elevato di dispositivi senza interventi diretti. Dispositivi come iPhone, iPad e MacBook possono essere spediti direttamente agli utenti. Quando l'utente accende il dispositivo, Assistente configurazione, che include la tipica esperienza di configurazione guidata per i prodotti Apple, viene eseguito con impostazioni preconfigurate e il dispositivo viene registrato nella gestione.

Per abilitare la registrazione DEP, si usano sia il portale di Intune che il portale di Apple Business Manager (ABM) o Apple School Manager (ASM). È necessario un elenco di numeri di serie o un numero di ordine di acquisto per poter assegnare i dispositivi a Intune per la gestione in ABM/ASM. Si creano profili di registrazione DEP in Intune contenenti le impostazioni da applicare ai dispositivi durante la registrazione. Si noti che la registrazione DEP non può essere usata con un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

> [!NOTE]
> DEP imposta le configurazioni del dispositivo che non possono essere necessariamente rimosse dall'utente finale. Per questa ragione, prima di eseguire la [migrazione in DEP](../fundamentals/migration-guide-considerations.md), è necessario cancellare i dati del dispositivo per ripristinare lo stato predefinito.

## <a name="dep-and-the-company-portal"></a>DEP e l'app Portale aziendale

Le registrazioni DEP non sono compatibili con la versione di App Store dell'app Portale aziendale. È possibile concedere agli utenti l'accesso all'app Portale aziendale in un dispositivo DEP. È possibile fornire questo accesso per consentire agli utenti di scegliere le app aziendali che vogliono usare nel dispositivo o di usare l'autenticazione moderna per completare il processo di registrazione. 

Per abilitare l'autenticazione moderna durante la registrazione, eseguire il push dell'app al dispositivo usando **Installa il Portale aziendale con VPP** (Volume Purchase Program) nel profilo DEP. Per altre informazioni, vedere [Registrare automaticamente i dispositivi iOS nel programma Device Enrollment Program di Apple](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile).

Per consentire l'aggiornamento automatico del Portale aziendale e fornire l'app Portale aziendale nei dispositivi già registrati in DEP, distribuire l'app Portale aziendale tramite Intune come app Volume Purchase Program (VPP) obbligatoria con un [criterio di configurazione dell'applicazione](../apps/app-configuration-policies-use-ios.md) applicato.

## <a name="what-is-supervised-mode"></a>Che cos'è la modalità con supervisione?

Apple ha introdotto la modalità con supervisione in iOS 5. Un dispositivo iOS nella modalità con supervisione può essere gestito con più controlli, ad esempio Blocca acquisizione schermo e Blocca l'installazione di app con App Store. Questa modalità è quindi particolarmente utile per dispositivi di proprietà dell'azienda. Intune supporta la configurazione di dispositivi per la modalità con supervisione nell'ambito del programma Apple Device Enrollment Program (DEP).

Il supporto per i dispositivi DEP senza supervisione è stato deprecato in iOS 11. In iOS 11 e versioni successive, i dispositivi DEP configurati devono essere sempre con supervisione. Il flag is_supervised DEP verrà ignorato in una versione futura di iOS.

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
- [Autorità di gestione dei dispositivi mobili (MDM)](../fundamentals/mdm-authority-set.md)
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="get-an-apple-dep-token"></a>Ottenere un token DEP Apple

Per registrare i dispositivi iOS in DEP, è necessario un file di token DEP (con estensione p7m) da Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi DEP di proprietà dell'azienda. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Per creare un token, è possibile usare il portale Apple Business Manager o Apple School Manager. Il portale ABM/ASM viene usato anche per assegnare i dispositivi a Intune per la gestione.

> [!NOTE]
> Se si elimina il token dal portale classico di Intune prima della migrazione ad Azure, è possibile che Intune ripristini il token DEP Apple eliminato. È possibile eliminare nuovamente il token DEP dal portale di Azure.

### <a name="step-1-download-the-intune-public-key-certificate-required-to-create-the-token"></a>Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare il token.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivo** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > **Aggiungi**.

    ![Ottenere un token del programma di registrazione.](./media/device-enrollment-program-enroll-ios/image01.png)

2. Concedere a Microsoft l'autorizzazione per l'invio di informazioni su utenti e dispositivi ad Apple selezionando **Accetto**.

   ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/device-enrollment-program-enroll-ios/add-enrollment-program-token-pane.png)

3. Scegliere **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.


### <a name="step-2-use-your-key-to-download-a-token-from-apple"></a>Passaggio 2: Usare la chiave per scaricare un token da Apple.

1. Scegliere **Creare un token tramite Apple Device Enrollment Program** per aprire il portale del programma di distribuzione Apple e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token DEP.
2. Nel [portale dei programmi di distribuzione](https://deploy.apple.com) di Apple scegliere **Inizia** per **Device Enrollment Program**.

3. Nella pagina **Gestisci server** scegliere **Aggiungi server MDM**.
4. Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non corrisponde al nome o all'URL del server di Microsoft Intune.

5. Viene visualizzata la finestra di dialogo **Aggiungi &lt;NomeServer&gt;** che richiede di **caricare la chiave pubblica**. Selezionare **Scegli file**. per caricare il file PEM e scegliere **Avanti**.

6. Passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Gestione dei dispositivi**.
7. Nella sezione **Scegliere dispositivi per** specificare come vengono identificati i dispositivi:
    - **Numero di serie**
    - **Numero di ordine**
    - **Carica file CSV**.

   ![Schermata in cui viene specificata la scelta dei dispositivi in base al numero di serie, viene impostata l'azione di selezione su Assegna a server e viene selezionato il nome del server.](./media/device-enrollment-program-enroll-ios/enrollment-program-token-specify-serial.png)

8. In **Scegliere un'azione** scegliere **Assegna al server,** scegliere il &lt;nome del serve&gt;r specificato per Microsoft Intune e quindi scegliere **OK**. Il portale Apple assegna i dispositivi specificati al server di Intune per la gestione e quindi visualizza il messaggio **Assegnazione completata**.

   Nel portale Apple passare a **Deployment Programs** (Programmi di distribuzione) &gt; **Device Enrollment Program** &gt; **View Assignment History** (Visualizza cronologia di assegnazione) per visualizzare un elenco di dispositivi con la rispettiva assegnazione di server MDM.

### <a name="step-3-save-the-apple-id-used-to-create-this-token"></a>Passaggio 3. Salvare l'ID Apple usato per creare il token.

Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) specificare l'ID Apple per riferimento futuro.

![Screenshot della specifica dell'ID Apple usato per creare il token DEP e passare al token DEP.](./media/device-enrollment-program-enroll-ios/image03.png)

### <a name="step-4-upload-your-token-and-choose-scope-tags"></a>Passaggio 4. Caricare il token e scegliere i tag di ambito.

1. Nella casella **Token Apple** passare al file del certificato (con estensione pem) e scegliere **Apri**.
2. Per applicare [tag di ambito](../fundamentals/scope-tags.md) a questo token DEP, scegliere **Ambito (tag)** e selezionare i tag di ambito desiderati. I tag di ambito applicati a un token verranno ereditati dai profili e dai dispositivi aggiunti a questo token.
3. Scegliere **Crea**.

Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati. Intune si sincronizza automaticamente con Apple per verificare l'account DEP.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple

Ora che è stato installato il token, è possibile creare un profilo di registrazione per i dispositivi DEP. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione. È previsto un limite di 100 profili di registrazione per ogni token DEP.

> [!NOTE]
> I dispositivi verranno bloccati se non sono disponibili licenze del portale aziendale sufficienti per un token VPP o se il token è scaduto. Intune visualizza un avviso quando un token sta per scadere o le licenze sono quasi esaurite.
 

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivo** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione**.
2. Selezionare un token, scegliere **Profili** > **Crea profilo** > **iOS**.

    ![Screenshot di Crea profilo.](./media/device-enrollment-program-enroll-ios/image04.png)

3. Nella pagina **Informazioni di base** immettere un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti. È possibile usare questo campo **Nome** per creare un gruppo dinamico in Azure Active Directory. Usare il nome del profilo per definire il parametro enrollmentProfileName per assegnare i dispositivi con questo profilo di registrazione. Altre informazioni sui [gruppi dinamici di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).

    ![Nome e descrizione del profilo.](./media/device-enrollment-program-enroll-ios/image05.png)

4. Selezionare **Passaggio successivo: Impostazioni di gestione dei dispositivi**.

5. In **Affinità utente** scegliere se i dispositivi con questo profilo devono essere registrati con o senza un utente assegnato.
    - **Registra con affinità utente**: scegliere questa opzione per i dispositivi che appartengono a utenti che vogliono usare il portale aziendale per servizi come l'installazione di app. Se si usa ADFS e per il profilo di registrazione l'opzione **Authenticate with Company Portal instead of Setup Assistant** (Autenticazione con il portale aziendale invece di Assistente configurazione) è impostata su **No**, è richiesto un [endpoint nome utente/misto WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) [ Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Registra senza affinità utente**: scegliere questa opzione per un dispositivo non associato a un singolo utente. Usare questa opzione per i dispositivi che non accedono ai dati utente locali. Le app come l'app Portale aziendale non funzionano.

5. Se si sceglie **Registra con affinità utente**, è possibile consentire agli utenti di eseguire l'autenticazione con il portale aziendale invece di Assistente configurazione Apple.

    ![Autenticazione con il portale aziendale.](./media/device-enrollment-program-enroll-ios/authenticatewithcompanyportal.png)

    > [!NOTE]
    > Se si vuole eseguire una delle operazioni seguenti, impostare **Selezione della posizione per l'autenticazione degli utenti** su **Portale aziendale**.
    >    - Usare l'autenticazione a più fattori
    >    - Richiedere agli utenti di modificare la password al primo accesso
    >    - Richiedere agli utenti di reimpostare le password scadute durante la registrazione
    >
    > Non sono supportate durante l'autenticazione con l'Assistente configurazione di Apple.

6. Se si sceglie **Portale aziendale** per **Selezione della posizione per l'autenticazione degli utenti**, è possibile usare un token VPP per installare automaticamente il portale aziendale nel dispositivo. In questo caso, l'utente non deve specificare un ID Apple. Per installare il portale aziendale con un token VPP, scegliere un token in **Install Company Portal with VPP** (Installa il portale aziendale con VPP). Richiede che il portale aziendale sia già stato aggiunto al token VPP. Per assicurarsi che l'app Portale aziendale continui a essere aggiornata dopo la registrazione, assicurarsi di aver configurato una distribuzione delle app in Intune (Intune>App client). Affinché non sia obbligatoria l'interazione dell'utente, l'app Portale aziendale sarà probabilmente un'app VPP iOS, sarà impostata come app obbligatoria e sarà necessario usare le licenze del dispositivo per l'assegnazione. Assicurarsi che il token non abbia una scadenza e di avere un numero sufficiente di licenze dei dispositivi per l'app Portale aziendale. Se il token ha una scadenza o se il numero di licenze è insufficiente, Intune installa invece l'app Portale aziendale dall'App Store e richiede un ID Apple. 

    > [!NOTE]
    > Quando l'opzione **Selezione della posizione per l'autenticazione degli utenti** è impostata su **Portale aziendale**, assicurarsi che il processo di registrazione del dispositivo venga eseguito nelle prime 24 ore dal download dell'app Portale aziendale nel dispositivo DEP. In caso contrario, la registrazione potrebbe non riuscire e sarà necessario il ripristino delle impostazioni predefinite per registrare il dispositivo.
    
    ![Screenshot dell'installazione del portale aziendale con VPP.](./media/device-enrollment-program-enroll-ios/install-cp-with-vpp.png)

7. Se si sceglie **Assistente configurazione** per **Selezione della posizione per l'autenticazione degli utenti**, ma si vuole anche usare l'accesso condizionale o distribuire le app aziendali nei dispositivi, è necessario installare il portale aziendale nel dispositivi. A tale scopo, scegliere **Sì** per **Installa il Portale aziendale**.  Se si vuole che gli utenti ricevano l'app Portale aziendale senza dover eseguire l'autenticazione in App Store, scegliere **Installa il Portale aziendale con VPP** e selezionare un token VPP. Per la corretta distribuzione, assicurarsi che il token non abbia una scadenza e di avere un numero sufficiente di licenze dei dispositivi per l'app Portale aziendale.

8. Se si era scelto un token per **Installa il Portale aziendale con VPP**, è possibile bloccare il dispositivo in modalità applicazione singola (in particolare, l'app Portale aziendale), subito dopo il completamento dell'Assistente configurazione. Scegliere **Sì** per **Run Company Portal in Single App Mode until authentication** (Esegui il portale aziendale in modalità app singola fino all'autenticazione) per impostare l'opzione. Per poter usare il dispositivo, l'utente deve prima autenticarsi effettuando l'accesso tramite il portale aziendale.

    L'autenticazione a più fattori non è supportata per un singolo dispositivo bloccato in modalità app singola. Questa limitazione esiste perché il dispositivo non può passare a un'altra app per completare il secondo fattore di autenticazione. Pertanto, se si vuole usare l'autenticazione a più fattori in un singolo dispositivo in modalità app singola, il secondo fattore deve trovarsi in un dispositivo diverso.

    Questa funzionalità è supportata solo per iOS 11.3.1 e versioni successive.

   ![Screenshot della modalità applicazione singola.](./media/device-enrollment-program-enroll-ios/single-app-mode.png)

9. Se si vuole che i dispositivi che usano questo profilo siano inclusi nella supervisione, scegliere **Sì** per **Supervisione eseguita**.

    ![Screenshot di Impostazioni di gestione dei dispositivi.](./media/device-enrollment-program-enroll-ios/supervisedmode.png)

    I dispositivi **con supervisione** offrono più opzioni di gestione e il blocco attivazione viene disabilitato per impostazione predefinita. È consigliabile usare il programma DEP come meccanismo per l'abilitazione della modalità con supervisione, soprattutto per la distribuzione di un numero elevato di dispositivi iOS.

    Gli utenti vengono informati che i dispositivi sono inclusi nella supervisione in due modi:

   - Nella schermata di blocco viene visualizzata l'indicazione: "This iPhone is managed by Contoso" (Questo iPhone è gestito da Contoso).
   - Nella schermata **Settings** (Impostazioni)  > **General** (Generale)  > **About** (Informazioni) viene visualizzato l'avviso: "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device." (Questo iPhone è soggetto a supervisione. Contoso può monitorare il traffico Internet e individuare il dispositivo)

     > [!NOTE]
     > Per reimpostare un dispositivo registrato senza supervisione in modo da includerlo nella supervisione, è possibile usare solo Apple Configurator. Per reimpostare il dispositivo in questo modo, è necessario connettere un dispositivo iOS a un computer Mac con un cavo USB. Per altre informazioni vedere la [documentazione di Apple Configurator](http://help.apple.com/configurator/mac/2.3).

10. Scegliere se usare la registrazione bloccata per i dispositivi con questo profilo. La **registrazione bloccata** disabilita le impostazioni di iOS che consentono la rimozione del profilo di gestione dal menu **Impostazioni**. Dopo la registrazione del dispositivo, non è possibile modificare questa impostazione senza cancellare il dispositivo. Per tali dispositivi, la modalità di gestione **Supervisione eseguita** deve essere impostata su *Sì*. 

11. Scegliere se si vuole che i dispositivi con questo profilo possano **eseguire la sincronizzazione con i computer**. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

12. Se si sceglie **Consenti Apple Configurator per certificato** nel passaggio precedente, scegliere un certificato di Apple Configurator da importare.

13. È possibile specificare un formato di denominazione per i dispositivi che viene applicato automaticamente alla registrazione e per ogni archiviazione successiva. Per creare un modello di denominazione, selezionare **Sì** in **Applica il modello di nome di dispositivo**. Nella casella **Modello del nome del dispositivo** immettere quindi il modello da usare per i nomi che usano questo profilo. È possibile specificare un formato modello che include il tipo di dispositivo e il numero di serie. 

14. Scegliere **Avanti: Personalizzazione dell'Assistente configurazione**.

15. Nella pagina **Personalizzazione dell'Assistente configurazione** configurare le impostazioni di profilo seguenti: ![Personalizzazione dell'Assistente configurazione.](./media/device-enrollment-program-enroll-ios/setupassistantcustom.png)


    | Impostazioni di reparto | Descrizione |
    |---|---|
    | <strong>Nome reparto</strong> | Viene visualizzata quando gli utenti toccano <strong>Informazioni configurazione</strong> durante l'attivazione. |
    |    <strong>Telefono del reparto</strong>     | Viene visualizzata quando l'utente fa clic sul pulsante <strong>Richiesta di assistenza</strong> durante l'attivazione. |

    È possibile scegliere di nascondere le schermate di Assistente configurazione nel dispositivo durante la configurazione.
    - Se si sceglie **Nascondi**, la schermata non verrà visualizzata durante la configurazione. Dopo aver configurato il dispositivo, l'utente può comunque ancora usare il menu **Impostazioni** menu per configurare la funzionalità.
    - Se si sceglie **Mostra**, la schermata verrà visualizzata durante la configurazione. L'utente può a volte ignorare la schermata senza eseguire azioni. Ma, in un secondo momento, può usare il menu **Impostazioni** del dispositivo per configurare la funzionalità. 


    | Impostazioni delle schermate dell'Assistente configurazione | Se si sceglie **Mostra**, durante la configurazione il dispositivo... |
    |------------------------------------------|------------------------------------------|
    | <strong>Passcode</strong> | Richiederà un passcode all'utente. Richiedere sempre un passcode per i dispositivi non protetti, a meno che l'accesso non venga controllato in un altro modo (ad esempio, la modalità tutto schermo che limita il dispositivo a una sola app). |
    | <strong>Servizi di posizione</strong> | Richiederà la posizione all'utente. |
    | <strong>Recupera</strong> | Visualizzerà la schermata App e dati. Questa schermata offre all'utente la possibilità di ripristinare o trasferire i dati da iCloud Backup durante la configurazione del dispositivo. |
    | <strong>ID iCloud e Apple</strong> | Offrirà all'utente la possibilità di accedere con l'ID Apple e di usare iCloud.                         |
    | <strong>Termini e condizioni</strong> | Richiederà all'utente di accettare i termini e le condizioni Apple. |
    | <strong>Touch ID</strong> | Offrirà all'utente la possibilità di impostare l'identificazione con impronta digitale per il dispositivo. |
    | <strong>Apple Pay</strong> | Offrirà all'utente la possibilità di configurare Apple Pay nel dispositivo. |
    | <strong>Zoom</strong> | Offrirà all'utente la possibilità di ingrandire la visualizzazione durante la configurazione del dispositivo. |
    | <strong>Siri</strong> | Offrirà all'utente la possibilità di configurare Siri. |
    | <strong>Dati di diagnostica</strong> | Visualizzerà la schermata Diagnostica all'utente. Questa schermata offre all'utente la possibilità di inviare dati di diagnostica ad Apple. |
    | <strong>Segnale schermo</strong> | Offrirà all'utente la possibilità di attivare il segnale schermo. |
    | <strong>Privacy</strong> | Visualizzerà la schermata Privacy all'utente. |
    | <strong>Migrazione Android</strong> | Offrirà all'utente la possibilità di eseguire la migrazione dei dati da un dispositivo Android. |
    | <strong>iMessage e FaceTime</strong> | Offrirà all'utente la possibilità di configurare iMessage e FaceTime. |
    | <strong>Onboarding</strong> | Visualizzerà le schermate con le informazioni di onboarding per la formazione dell'utente, ad esempio Copertina e Multitasking e centro di controllo. |
    | <strong>Migrazione di Watch</strong> | Offrirà all'utente la possibilità di eseguire la migrazione dei dati da un dispositivo Watch. |
    | <strong>Orario schermo</strong> | Visualizzerà la schermata Orario schermo. |
    | <strong>Aggiornamento software</strong> | Visualizzerà la schermata degli aggiornamenti software obbligatori. |
    | <strong>Configurazione SIM</strong> | Offrirà all'utente la possibilità di aggiungere un piano dati cellulare. |
    | <strong>Aspetto</strong> | Visualizzerà la schermata Aspetto all'utente. |
    | <strong>Express Language</strong> (Lingua rapida)| Visualizzerà la schermata Express Language (Lingua rapida) all'utente. |
    | <strong>Lingua preferita</strong> | Offrirà all'utente la possibilità di scegliere la **Lingua preferita**. |
    | <strong>Device to Device Migration</strong> (Migrazione da dispositivo a dispositivo) | Offrirà all'utente la possibilità di eseguire la migrazione dei dati dal dispositivo precedente a questo dispositivo.|
    

16. Scegliere **Avanti** per passare alla pagina **Rivedi e crea**.

17. Per salvare il profilo, scegliere **Crea**.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti
Adesso che Intune ha le autorizzazioni per gestire i dispositivi, è possibile sincronizzare Intune con Apple per visualizzare i dispositivi gestiti nel portale di Azure in Intune.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > scegliere un token dall'elenco > **Dispositivi** > **Sincronizza**. ![Screenshot del nodo Dispositivi DEP e del collegamento Sincronizza.](./media/device-enrollment-program-enroll-ios/image06.png)

   Per rispettare le condizioni Apple per un traffico DEP accettabile, Intune impone le restrizioni seguenti:
   - Una sincronizzazione completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune recupera l'elenco aggiornato completo dei numeri di serie assegnati al server MDM di Apple connesso a Intune. Se un dispositivo DEP viene eliminato dal portale di Intune, è necessario rimuoverne l'assegnazione dal server MDM Apple nel portale DEP. Se non è assegnato, non verrà reimportato in Intune fino all'esecuzione della sincronizzazione completa.   
   - La sincronizzazione viene eseguita automaticamente ogni 24 ore. È anche possibile eseguire la sincronizzazione facendo clic sul pulsante **Sincronizza** (non più di una volta ogni 15 minuti). Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Il pulsante **Sincronizza** rimane disabilitato finché non viene completata la sincronizzazione. La sincronizzazione aggiorna lo stato dei dispositivi esistenti e importa i nuovi dispositivi assegnati al server MDM di Apple.   


## <a name="assign-an-enrollment-profile-to-devices"></a>Assegnare un profilo DEP ai dispositivi
Prima della registrazione è necessario assegnare ai dispositivi un profilo DEP.

>[!NOTE]
>È anche possibile assegnare i numeri di serie ai profili nel pannello **Numeri di serie Apple**.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > scegliere un token nell'elenco.
2. Scegliere **Dispositivi** > scegliere i dispositivi nell'elenco > **Assegna profilo**.
3. In **Assegna profilo** scegliere un profilo per i dispositivi > **Assegna**.

### <a name="assign-a-default-profile"></a>Assegnare un profilo predefinito

È possibile selezionare un profilo predefinito da applicare a tutti i dispositivi da registrare con un token specifico.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > scegliere un token nell'elenco.
2. Scegliere **Imposta profilo predefinito**, scegliere un profilo nell'elenco a discesa e quindi scegliere **Salva**. Questo profilo verrà applicato a tutti i dispositivi registrati con il token.

## <a name="distribute-devices"></a>Distribuire i dispositivi
Fino a questo punto sono state abilitate la gestione e la sincronizzazione tra Apple e Intune ed è stato assegnato un profilo per consentire la registrazione dei dispositivi DEP. È ora possibile distribuire i dispositivi agli utenti. I dispositivi con affinità utente richiedono che a ogni utente sia assegnata una licenza di Intune. Per i dispositivi senza affinità utente è necessaria una licenza dispositivo. Un dispositivo attivato non può applicare un profilo di registrazione fino a quando non viene cancellato.

Vedere [Registrare il dispositivo iOS in Intune con Device Enrollment Program](/intune-user-help/enroll-your-device-dep-ios).

## <a name="renew-a-dep-token"></a>Rinnovare un token DEP  
1. Passare a deploy.apple.com.  
2. In **Gestisci i server** scegliere il server MDM associato al file di token da rinnovare.
3. Scegliere **Genera nuovo token**.

    ![Screenshot della generazione di un nuovo token.](./media/device-enrollment-program-enroll-ios/generatenewtoken.png)

4. Scegliere **Token del server**.  
5. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivo** > **iOS** > **Registrazione di iOS** > **Token del programma di registrazione** > scegliere il token.
    ![Screenshot dei token del programma di registrazione.](./media/device-enrollment-program-enroll-ios/enrollmentprogramtokens.png)

6. Scegliere **Rinnova il token** e immettere l'ID Apple usato per creare il token originale.  
    ![Screenshot della generazione di un nuovo token.](./media/device-enrollment-program-enroll-ios/renewtoken.png)

8. Caricare il token appena scaricato.  
9. Scegliere **Rinnova il token**. Viene visualizzata la conferma che il token è stato rinnovato.   
    ![Screenshot della conferma.](./media/device-enrollment-program-enroll-ios/confirmation.png)
