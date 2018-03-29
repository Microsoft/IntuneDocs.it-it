---
title: Registrare dispositivi iOS con Device Enrollment Program
titlesuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi iOS di proprietà dell'azienda usando Device Enrollment Program."
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 05b03502a27c244dd665363741f70a695f8e945b
ms.sourcegitcommit: a22309174e617e59ab0cdd0a55abde38711a5f35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2018
---
# <a name="automatically-enroll-ios-devices-by-using-apples-device-enrollment-program"></a>Registrare automaticamente i dispositivi iOS usando il programma Device Enrollment Program di Apple

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

> [!NOTE]
> ### <a name="temporary-user-interface-differences"></a>Differenze di interfaccia utente temporanee
>
>Le interfacce utente per le funzionalità descritte in questa pagina sono in corso di aggiornamento. Questi aggiornamenti verranno distribuiti a tutti gli account utente entro la fine di aprile.
>
>Se la pagina **Registrazione del dispositivo** è simile all'immagine seguente, l'account non è ancora stato aggiornato alla nuova interfaccia utente ed è possibile usare questa pagina della Guida.
>
>![Interfaccia utente di Intune precedente](./media/appleenroll-oldui.png)
>
>Se la pagina **Registrazione del dispositivo** è simile all'immagine seguente, sono disponibili le interfacce utente aggiornate.  Passare a [questa pagina della Guida](device-enrollment-program-enroll-ios-newui.md).
>
>![Nuova interfaccia utente di Intune](./media/appleenroll-newui.png)

Questo argomento offre informazioni utili per abilitare la registrazione dei dispositivi iOS acquistati tramite [Device Enrollment Program (DEP)](https://deploy.apple.com) di Apple. È possibile abilitare la registrazione DEP per un numero elevato di dispositivi senza interventi diretti. Si possono fornire i dispositivi iPhone e iPad direttamente agli utenti e quando l'utente attiva il dispositivo, l'Assistente configurazione viene eseguito con impostazioni preconfigurate e il dispositivo viene registrato nella gestione.

Per abilitare la registrazione DEP, si usano i portali di Intune e DEP di Apple. È necessario un elenco di numeri di serie o un numero di ordine di acquisto per poter assegnare i dispositivi a Intune per la gestione. Si creano profili di registrazione DEP contenenti le impostazioni da applicare ai dispositivi durante la registrazione.

La registrazione DEP non funziona con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md). Il programma di registrazione dei dispositivi non è attualmente supportato dai dispositivi macOS.

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

> [!NOTE]
> L'autenticazione a più fattori (MFA) non funziona durante la registrazione DEP configurata per l'affinità utente. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto nei dispositivi. I dispositivi non possono richiedere agli utenti di modificare la password al primo accesso. Inoltre, agli utenti con password scadute non viene richiesto di reimpostare la password durante la registrazione e devono reimpostarla da un altro dispositivo.

## <a name="get-the-apple-dep-token"></a>Ottenere il token DEP Apple

Per registrare i dispositivi iOS in DEP, è necessario un file di token DEP (con estensione p7m) da Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi DEP di proprietà dell'azienda. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Per creare un token DEP si usa il portale DEP di Apple. È anche possibile usare il portale DEP per assegnare i dispositivi a Intune per la gestione.

> [!NOTE]
> Se si elimina il token dal portale classico di Intune prima della migrazione ad Azure, è possibile che Intune ripristini il token DEP Apple eliminato. È possibile eliminare nuovamente il token DEP dal portale di Azure. È possibile eliminare nuovamente il token DEP dal portale di Azure.

**Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare un token DEP Apple.**<br>

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Token DEP**.

  ![Riquadro Token DEP nell'area di lavoro dei certificati Apple](./media/enrollment-program-token-add.png)

2. Scegliere **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.

  ![Pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica](./media/enrollment-program-token-download.png)

**Passaggio 2: Creare e scaricare un token DEP Apple.**<br>
1. Scegliere **Creare un token tramite Apple Device Enrollment Program** per aprire il portale del programma di distribuzione Apple e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token DEP.
2.  Nel [portale dei programmi di distribuzione](https://deploy.apple.com) di Apple scegliere **Inizia** per **Device Enrollment Program**.

3. Nella pagina **Gestisci server** scegliere **Aggiungi server MDM**.
4. Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.

   ![Aggiunta di un nome server MDM per DEP e selezione di Avanti](./media/enrollment-program-token-add-server.png)

5. Viene visualizzata la finestra di dialogo **Aggiungi &lt;NomeServer&gt;** che richiede di **caricare la chiave pubblica**. Fare clic su **Scegli file** per caricare il file PEM e scegliere **Avanti**.  

6. Passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Gestione dei dispositivi**.
7. Nella sezione **Scegliere dispositivi per** specificare come vengono identificati i dispositivi:
    - **Numero di serie**
    - **Numero di ordine**
    - **Carica file CSV**.

   ![Specificazione della scelta dei dispositivi in base al numero di serie, impostazione dell'azione di selezione su Assegna a server e selezione del nome del server](./media/enrollment-program-token-specify-serial.png)

8. In **Scegliere un'azione** scegliere **Assegna al server,** scegliere il &lt;nome del serve&gt;r specificato per Microsoft Intune e quindi scegliere **OK**. Il portale Apple assegna i dispositivi specificati al server di Intune per la gestione e quindi visualizza il messaggio **Assegnazione completata**.

   Nel portale Apple passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Visualizza cronologia di assegnazione** per visualizzare un elenco di dispositivi con la rispettiva assegnazione di server MDM.

**Passaggio 3: Immettere l'ID Apple usato per creare il token DEP.**<br>Nel portale di Azure in Intune specificare l'ID Apple per riferimenti futuri.

![Specificazione dell'ID Apple usato per creare il token DEP e passare al token DEP](./media/enrollment-program-token-apple-id.png)

**Passaggio 4: Passare al token DEP da caricare.**<br>
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati. Intune si sincronizza automaticamente con Apple per verificare l'account DEP.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple

Ora che è stato installato il token, è possibile creare un profilo di registrazione per i dispositivi DEP. Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple**.
2. In **Programma di registrazione per Apple** scegliere **Profili DEP** > **Crea**.
3. In **Crea un profilo di registrazione** immettere un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti. È possibile usare questo campo **Nome** per creare un gruppo dinamico in Azure Active Directory. Usare il nome del profilo per definire il parametro enrollmentProfileName per assegnare i dispositivi con questo profilo di registrazione. Altre informazioni sui [gruppi dinamici di Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#using-attributes-to-create-rules-for-device-objects).

  Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza un utente assegnato.

 - **Registra con affinità utente**: scegliere questa opzione per i dispositivi che appartengono a utenti e che devono usare il portale aziendale per i servizi, come l'installazione di app. Per l'affinità utente è richiesto [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Registra senza affinità utente**: scegliere questa opzione per un dispositivo non associato a un singolo utente. Usare questa impostazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app come l'app Portale aziendale non funzionano.

4. Scegliere **Impostazioni di gestione dei dispositivi** per configurare le impostazioni di profilo seguenti:

  ![Scelta della modalità di gestione](./media/enrollment-program-profile-mode.png)
  - **Supervisione eseguita**: modalità di gestione che attiva altre opzioni di gestione e disattiva il blocco attivazione per impostazione predefinita. Se si lascia vuota la casella di controllo, le funzionalità di gestione saranno limitate. È consigliabile usare il programma DEP come meccanismo per l'abilitazione della modalità con supervisione, soprattutto per le organizzazioni che distribuiscono un numero elevato di dispositivi iOS.

 > [!NOTE]
 > Dopo che un dispositivo è stato registrato non è possibile configurarlo per la modalità con supervisione tramite Intune. Dopo la registrazione, l'unico modo per abilitare la modalità con supervisione è connettere il dispositivo iOS a un computer Mac con un cavo USB e usare Apple Configurator. In questo modo il dispositivo viene reimpostato e configurato in modalità con supervisione. Per altre informazioni vedere la [documentazione di Apple Configurator](http://help.apple.com/configurator/mac/2.3). Un dispositivo con supervisione visualizza "This iPhone is managed by Contoso." (Questo dispositivo è gestito da Contoso) nella schermata di blocco e "This iPhone is supervised. Contoso can monitor your Internet traffic and locate this device." (Questo iPhone è soggetto a supervisione. Contoso può monitorare il traffico Internet e individuare il dispositivo) in **Impostazioni** > **Generali** > **Info**.

  - **Registrazione bloccata**: richiede Modalità di gestione = Supervisione eseguita. Disabilita le impostazioni iOS che possono consentire la rimozione del profilo di gestione. Lasciando vuota la casella di controllo, si consente la rimozione del profilo di gestione dal menu Impostazioni. Dopo la registrazione del dispositivo, non è possibile modificare questa impostazione senza ripristinare le impostazioni predefinite del dispositivo.

  - **Modalità iPad condiviso abilitata**: il programma Device Enrollment Program di Apple non supporta la modalità iPad condiviso.

  - **Consenti associazione**: specifica se i dispositivi iOS possono sincronizzarsi con i computer. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario scegliere un certificato in **Certificati di Apple Configurator**.

  - **Certificati di Apple Configurator**: se si è scelto **Consenti Apple Configurator per certificato**  in **Consenti associazione**, scegliere un certificato di Apple Configurator da importare.

  Scegliere **Salva**.

5. Scegliere **Impostazioni dell'Assistente configurazione** per configurare le impostazioni di profilo seguenti:

  ![Scelta delle impostazioni di configurazione con le impostazioni disponibili per un nuovo profilo DEP](./media/enrollment-program-profile-settings.png)
  - **Nome del reparto**: viene visualizzata quando gli utenti toccano **Informazioni configurazione** durante l'attivazione.

  - **Telefono del reparto**: viene visualizzata quando l'utente fa clic sul pulsante **Richiesta di assistenza** durante l'attivazione.
    - **Opzioni dell'assistente di configurazione**: queste impostazioni facoltative possono essere configurate in un secondo momento nel menu **Impostazioni** di iOS.
        - **Passcode**
        - **Servizi di posizione**
        - **Recupera**
        - **ID Apple**
        - **Termini e condizioni**
        - **Touch ID**
        - **Apple Pay**
        - **Zoom**
        - **Siri**
        - **Dati di diagnostica**

    Scegliere **Salva**.

9. Per salvare le impostazioni del profilo, scegliere **Crea** nel pannello **Crea un profilo di registrazione**. Il profilo di registrazione viene visualizzato nell'elenco dei profili DEP Apple.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti
Adesso che Intune ha le autorizzazioni per gestire i dispositivi, è possibile sincronizzare Intune con Apple per visualizzare i dispositivi gestiti nel portale di Azure in Intune.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** > **Dispositivi DEP** > **Sincronizza**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.

  ![Nodo Dispositivi DEP selezionato e scelta del collegamento Sincronizza](./media/enrollment-program-device-sync.png)

2. Nel pannello **Sincronizzazione** scegliere **Richiedi la sincronizzazione**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.

   ![Pannello Sincronizzazione con il collegamento Richiedi la sincronizzazione selezionato](./media/enrollment-program-device-request-sync.png)

   Per soddisfare le condizioni Apple per un traffico DEP accettabile, Intune impone le seguenti restrizioni:
     -  Una sincronizzazione completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna ogni numero di serie Apple assegnato a Intune. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
     -  Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.
     - Intune sincronizza con Apple i dispositivi nuovi e rimossi ogni 24 ore.

3. Nell'area di lavoro DEP, scegliere **Aggiorna** per visualizzare i dispositivi.

## <a name="assign-an-enrollment-profile-to-devices"></a>Assegnare un profilo DEP ai dispositivi
Prima della registrazione è necessario assegnare ai dispositivi un profilo DEP.

>[!NOTE]
>È anche possibile assegnare i numeri di serie ai profili nel pannello **Numeri di serie Apple**.

1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** > **Registrazione Apple** e quindi scegliere **Profili DEP**.
2. Nell'elenco **Profili DEP** scegliere il profilo che si vuole assegnare ai dispositivi e quindi scegliere **Assegna dispositivi**.

 ![Assegnazioni di dispositivo con l'opzione di assegnazione selezionata](./media/enrollment-program-device-assign.png)

3. Scegliere **Assegna** e quindi selezionare i dispositivi a cui si vuole assegnare il profilo. È possibile applicare un filtro per visualizzare i dispositivi disponibili:
  - **non assegnato**
  - **qualsiasi**
  - **&lt;nome profilo&gt;**
4. Scegliere i dispositivi che si vuole assegnare. La casella di controllo sopra la colonna consente di selezionare fino a 1000 dispositivi elencati. Fare quindi clic su **Assegna**. Per registrare più di 1000 dispositivi, ripetere i passaggi di assegnazione fino a quando non è stato assegnato un profilo di registrazione a tutti i dispositivi.

  ![Pulsante Assegna per assegnare il profilo DEP in Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices"></a>Distribuire i dispositivi
Fino a questo punto sono state abilitate la gestione e la sincronizzazione tra Apple e Intune ed è stato assegnato un profilo per consentire la registrazione dei dispositivi DEP. È ora possibile distribuire i dispositivi agli utenti. I dispositivi con affinità utente richiedono che a ogni utente sia assegnata una licenza di Intune. Per i dispositivi senza affinità utente è necessaria una licenza dispositivo. Un dispositivo attivato non può applicare un profilo di registrazione se non vengono ripristinate le impostazioni predefinite del dispositivo.

Vedere [Registrare il dispositivo iOS in Intune con Device Enrollment Program](/intune-user-help/enroll-your-device-dep-ios).
