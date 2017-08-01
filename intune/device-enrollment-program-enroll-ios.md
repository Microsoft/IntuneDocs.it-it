---
title: Registrare i dispositivi iOS - Device Enrollment Program
titleSuffix: Intune on Azure
description: "Informazioni su come registrare i dispositivi iOS di proprietà dell'azienda usando Device Enrollment Program.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 654a19dd6f1e5f4fd2bda771b0df95b87944db75
ms.sourcegitcommit: 2a6ad3c233d15a9fb441362105f64b2bdd550c34
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/13/2017
---
# <a name="set-up-ios-device-enrollment-with-device-enrollment-program"></a>Configurare la registrazione per i dispositivi iOS con Device Enrollment Program

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento offre agli amministratori IT informazioni utili per abilitare la registrazione dei dispositivi iOS acquistati tramite [Device Enrollment Program (DEP)](https://deploy.apple.com) di Apple. Microsoft Intune può distribuire un profilo di registrazione "wireless" a dispositivi acquistati tramite DEP. L'amministratore non deve mai intervenire su ciascun dispositivo gestito. Un profilo DEP contiene le impostazioni di gestione che vengono applicate ai dispositivi durante la registrazione, incluse le opzioni di Assistente configurazione.

Per abilitare la registrazione DEP, si usano i portali di Intune e DEP di Apple. È necessario specificare anche un elenco di ID o un numero di ordine di acquisto da assegnare a Intune per la gestione nel portale Apple.

>[!NOTE]
>La registrazione tramite DEP non può essere usata con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

**Passaggi per abilitare i programmi di registrazione Apple**
1. [Ottenere un token DEP Apple e assegnare i dispositivi](#get-the-apple-dep-token)
2. [Creare un profilo di registrazione](#create-an-apple-enrollment-profile)
3. [Sincronizzare i dispositivi gestiti tramite DEP](#sync-managed-device)
4. [Assegnare un profilo DEP ai dispositivi](#assign-an-enrollment-profile-to-devices)
5. [Distribuire i dispositivi agli utenti](#end-user-experience-with-managed-devices)

## <a name="get-the-apple-dep-token"></a>Ottenere il token DEP Apple

Per registrare i dispositivi iOS di proprietà dell'azienda con Device Enrollment Program (DEP) di Apple, è necessario un file di token DEP (con estensione p7m) di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi di proprietà dell'azienda che partecipano al programma DEP. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

> [!NOTE]
> Se si elimina il token dalla console classica di Intune prima della migrazione ad Azure, è possibile che Intune ripristini il token DEP Apple eliminato. È possibile eliminare nuovamente il token DEP dal portale di Azure. È possibile eliminare nuovamente il token DEP dal portale di Azure.

**Prerequisiti**
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- Registrazione per il [Device Enrollment Program di Apple](http://deploy.apple.com)

**Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare un token DEP Apple.**<br>
1. Nel portale di Intune scegliere **Registrazione del dispositivo**, scegliere **Registrazione Apple** e quindi **Token DEP**.

  ![Screenshot del riquadro Token DEP nell'area di lavoro dei certificati Apple.](./media/enrollment-program-token-add.png)

2. Selezionare **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.

  ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/enrollment-program-token-download.png)

**Passaggio 2: Creare e scaricare un token DEP Apple.**<br>
1. Selezionare **Creare un token tramite Apple Device Enrollment Program** per aprire il portale del programma di distribuzione Apple e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token DEP.

  ![Screenshot del riquadro Token DEP nell'area di lavoro dei certificati Apple.](./media/enrollment-program-token-create.png)

  ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/enrollment-program-token-sign.png)
2.  Nel [portale dei programmi di distribuzione](https://deploy.apple.com) di Apple selezionare **Inizia** per **Device Enrollment Program**.

   ![Screenshot del programma di registrazione e selezione di Inizia per Device Enrollment Program.](./media/enrollment-program-token-started.png)

3. Nella pagina **Gestisci server** scegliere **Aggiungi server MDM**.
4. Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.

   ![Schermata dell'aggiunta di un nome server MDM per DEP e selezione di Avanti.](./media/enrollment-program-token-add-server.png)

5. Viene visualizzata la finestra di dialogo **Aggiungi &lt;NomeServer&gt;** che richiede di **caricare la chiave pubblica**. Fare clic su **Scegli file** per caricare il file PEM e scegliere **Avanti**.

   ![Screenshot della scelta del pulsante File chiave pubblica e successiva selezione di Avanti.](./media/enrollment-program-token-choose-file.png)
6.  La finestra di dialogo **Aggiungi &lt;Nome Server&gt;** include un collegamento al **Token del server**. Scaricare il file token del server (con estensione p7m) nel computer e fare clic su **Fine**.
   ![Schermata della scelta del pulsante File chiave pubblica e selezione di Avanti.](./media/enrollment-program-token-your-token.png)
7. Passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Gestione dei dispositivi**.
8. Nella sezione **Scegliere dispositivi per** specificare come vengono identificati i dispositivi:
    - **Numero di serie**
    - **Numero di ordine**
    - **Carica file CSV**.

   ![Schermata in cui viene specificata la scelta dei dispositivi in base al numero di serie, viene impostata l'azione di selezione su Assegna a server e viene selezionato il nome del server.](./media/enrollment-program-token-specify-serial.png)

9. In **Scegliere azione** selezionare **Assegna al server**, selezionare il &lt;NomeServer&gt; specificato per Microsoft Intune e quindi scegliere **OK**. Il portale Apple assegna i dispositivi specificati al server di Intune per la gestione e quindi visualizza il messaggio **Assegnazione completata**.

   Nel portale Apple passare a **Programmi di distribuzione** &gt; **Device Enrollment Program** &gt; **Visualizza cronologia di assegnazione** per visualizzare un elenco di dispositivi con la rispettiva assegnazione di server MDM.

**Passaggio 3: Immettere l'ID Apple usato per creare il token DEP.**<br>Nel portale di Intune specificare l'ID Apple per riferimenti futuri. Usare questo ID per rinnovare il token DEP per evitare la necessità di dover registrare di nuovo tutti i dispositivi.

![Screenshot della specifica dell'ID Apple usato per creare il token DEP e passare al token DEP.](./media/enrollment-program-token-apple-id.png)

**Passaggio 4: Passare al token DEP da caricare.**<br>
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati. Intune si sincronizza automaticamente con Apple per verificare l'account DEP.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple

Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nel portale di Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
2. In **Apple DEP** selezionare **Profili DEP** e quindi selezionare **Crea** nel pannello **Profili DEP**.

  ![Screenshot della scelta del collegamento Crea per creare un nuovo profilo DEP.](./media/enrollment-program-profile-create.png)

3. Nel pannello **Crea un profilo di registrazione** specificare un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti.

  ![Schermata in cui si specifica la descrizione del nome e si sceglie Registra con affinità utente per un nuovo profilo DEP.](./media/enrollment-program-profile-name.png)
Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza affinità utente.

 - **Registra con affinità utente**: gli utenti vengono associati con i dispositivi durante la configurazione e quindi hanno l'autorizzazione di accedere ai dati aziendali e alla posta elettronica. Scegliere l'**affinità dell'utente** per i dispositivi che appartengono a utenti e che devono usare il portale aziendale per i servizi, quale l'installazione di app.

 > [!NOTE]
 > L'autenticazione a più fattori (MFA) non funziona durante la registrazione nei dispositivi DEP con affinità utente. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto in questi dispositivi. Ai nuovi utenti a cui è richiesto di modificare la password al primo accesso non è possibile richiedere la password durante la registrazione nei dispositivi DEP. Inoltre, agli utenti con password scadute non verrà richiesto di reimpostare la password durante la registrazione e devono reimpostarla da un altro dispositivo.

 >[!NOTE]
 >La gestione DEP con affinità utente richiede che sia abilitato l'[endopoint Username/Mixed di WS-Trust 1.3 ](https://technet.microsoft.com/library/adfs2-help-endpoints) per richiedere un token utente. [Altre informazioni su WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Registra senza affinità utente**: il dispositivo non è associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

4. Selezionare **Impostazioni di gestione dei dispositivi** per configurare le impostazioni di profilo seguenti:

  ![Screenshot della scelta della modalità di gestione. Le impostazioni del dispositivo sono le seguenti: Supervisione eseguita, Registrazione bloccata, Consenti associazione impostato su Rifiuta tutto. Per un nuovo profilo DEP, l'opzione Certificati di Apple Configurator è disattivata.](./media/enrollment-program-profile-mode.png)
    - **Supervisione eseguita**: modalità di gestione che attiva altre opzioni di gestione e disattiva il blocco attivazione per impostazione predefinita. Se si lascia vuota la casella di controllo, le funzionalità di gestione saranno limitate.

    - **Registrazione bloccata**: richiede Modalità di gestione = Supervisione eseguita. Disattiva le impostazioni iOS che potrebbero permettere la rimozione del profilo di gestione. Lasciando vuota la casella di controllo, si consente la rimozione del profilo di gestione dal menu Impostazioni. Dopo la registrazione del dispositivo, non è possibile modificare questa impostazione senza ripristinare le impostazioni predefinite del dispositivo.

    - **Consenti associazione**: specifica se i dispositivi iOS possono sincronizzarsi con i computer. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

    - **Certificati di Apple Configurator**: se si è scelto **Consenti Apple Configurator per certificato**  in **Consenti associazione**, selezionare un certificato di Apple Configurator da importare.

  Scegliere **Salva**.

5. Selezionare **Impostazioni dell'Assistente configurazione** per configurare le impostazioni di profilo seguenti:

  ![Screenshot della scelta delle impostazioni di configurazione con le impostazioni disponibili per un nuovo profilo DEP.](./media/enrollment-program-profile-settings.png)
    - **Nome del reparto**: viene visualizzata quando gli utenti toccano **Informazioni configurazione** durante l'attivazione.

    - **Telefono del reparto**: viene visualizzata quando l'utente fa clic sul pulsante **Richiesta di assistenza** durante l'attivazione.
    - **Opzioni dell'assistente di configurazione**: queste impostazioni facoltative possono essere configurate in un secondo momento nel menu **Impostazioni** di iOS.
        - **Passcode**: consente di richiedere un passcode durante l'attivazione. Richiedere sempre un passcode, a meno che il dispositivo non sia protetto o l'accesso al dispositivo non venga controllato in un altro modo. La modalità tutto schermo, ad esempio, limita l'uso del dispositivo a una sola app.
        - **Servizi di posizione**: se l'opzione è abilitata, Assistente configurazione richiede il servizio al momento dell'attivazione.
        - **Ripristina**: se l'opzione è abilitata, Assistente configurazione richiede il backup in iCloud durante l'attivazione.
        - **ID Apple**: se l'opzione è abilitata, iOS richiede agli utenti un ID Apple quando Intune prova a installare un'app senza ID. È necessario un ID Apple per il download delle app da iOS App Store, incluse le app installate da Intune.
        - **Terms and Conditions** (Termini e condizioni): se l'opzione è abilitata, Assistente configurazione richiede di accettare i termini e condizioni Apple durante l'attivazione.
        - **ID tocco**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Apple Pay**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Zoom**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Siri**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Dati di diagnostica**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.

    Scegliere **Salva**.
9. Per salvare le impostazioni del profilo, selezionare **Crea** nel pannello **Crea un profilo di registrazione**. Il profilo di registrazione viene visualizzato nell'elenco dei profili DEP Apple.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti
Adesso che Intune ha le autorizzazioni per gestire i dispositivi, è possibile sincronizzare Intune con Apple per visualizzare i dispositivi gestiti nel portale di Intune.

1. Nel portale di Intune scegliere **Registrazione del dispositivo** &gt;  **Registrazione Apple** &gt; **Dispositivi DEP**.
2. In **Dispositivi DEP** selezionare **Sincronizza**. Viene visualizzato il pannello **Sincronizzazione**.

  ![Screenshot del nodo Dispositivi DEP selezionato e della scelta del collegamento Sincronizza.](./media/enrollment-program-device-sync.png)
3. Nel pannello **Sincronizzazione** selezionare **Richiedi la sincronizzazione**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.

  ![Screenshot del pannello Sincronizza con la scelta del collegamento Richiedi la sincronizzazione.](./media/enrollment-program-device-request-sync.png)

  Per soddisfare le condizioni Apple per un traffico DEP accettabile, Intune impone le seguenti restrizioni:
     -  Una sincronizzazione completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna ogni numero di serie Apple assegnato a Intune. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
     -  Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.
     - Intune sincronizza con Apple i dispositivi nuovi e rimossi ogni 24 ore.
     
4. Nell'area di lavoro DEP, scegliere **Aggiorna** per visualizzare i dispositivi.

## <a name="assign-an-enrollment-profile-to-devices"></a>Assegnare un profilo DEP ai dispositivi
Prima della registrazione è necessario assegnare ai dispositivi un profilo DEP.

>[!NOTE]
>È anche possibile assegnare i numeri di serie ai profili nel pannello **Numeri di serie Apple**.

1. Nel portale di Intune scegliere **Registrazione del dispositivo** > **Registrazione Apple** e quindi selezionare **Profili DEP**.
2. Nell'elenco **Profili DEP** selezionare il profilo che si vuole assegnare ai dispositivi e quindi selezionare **Assegna dispositivi**.

 ![Screenshot del pannello Sincronizza con la scelta del collegamento Richiedi la sincronizzazione.](./media/enrollment-program-device-assign.png)

3. Selezionare **Assegna** e quindi selezionare i dispositivi a cui si vuole assegnare il profilo. È possibile applicare un filtro per visualizzare i dispositivi disponibili:
  - **non assegnato**
  - **qualsiasi**
  - **&lt;nome profilo&gt;**
4. Selezionare i dispositivi che si vuole assegnare. La casella di controllo sopra la colonna consente di selezionare fino a 1000 dispositivi elencati. Fare quindi clic su **Assegna**. Per registrare più di 1000 dispositivi, ripetere i passaggi di assegnazione fino a quando non è stato assegnato un profilo di registrazione a tutti i dispositivi.

  ![Schermata del pulsante Assegna per assegnare il profilo DEP nel portale di Intune](media/dep-profile-assignment.png)

## <a name="end-user-experience-with-managed-devices"></a>Esperienza dell'utente finale con i dispositivi gestiti

È ora possibile distribuire i dispositivi agli utenti. I dispositivi con affinità utente richiedono che a ogni utente sia assegnata una licenza di Intune. Un dispositivo attivato non può applicare un profilo di registrazione se non vengono ripristinate le impostazioni predefinite del dispositivo. Quando il dispositivo iOS gestito da DEP viene acceso, vengono visualizzate nel dispositivo le opzioni seguenti:  

1. **Set Up iOS device** (Configura dispositivo iOS): è possibile scegliere una delle opzioni seguenti:
  - **Set Up as New device** (Configura come nuovo dispositivo)
  - **Restore from iCloud Backup** (Ripristina da iCloud Backup)
  - **Restore from iTunes Backup** (Ripristina da iTunes Backup)
2. Agli utenti viene visualizzato il messaggio **&lt;Your Organization&gt; will automatically configure your device** (<Organizzazione> configurerà automaticamente il dispositivo). Sono disponibili anche i dettagli di configurazione aggiuntivi seguenti:

  **Configuration allows &lt;Your Organization&gt; to manage this device over the air** (La configurazione consente a <organizzazione> di gestire il dispositivo in modalità wireless).

  **An administrator can help you set up email and network accounts, install and configure apps, and manage settings remotely.** (Un amministratore può consentire di configurare gli account di posta elettronica e di rete, installare e configurare le app e gestire le impostazioni in modalità remota).

  **An administrator may disable features, install and remove apps, monitor and restrict your Internet traffic and remotely erase this device.** (Un amministratore può disattivare le funzionalità, installare e rimuovere app, monitorare e limitare il traffico Internet e cancellare in remoto il dispositivo).

  **Configuration is provided by:<br> &lt;organizzazione&gt; iOS Team<br> &lt;Address&gt;** (La configurazione è specificata da: <indirizzo> team iOS <organizzazione>).

3. Agli utenti viene richiesto il nome utente e la password aziendale o dell'istituto di istruzione.
4. Agli utenti vengono richiesti i rispettivi ID Apple. Per installare l'app Portale aziendale di Intune e altre app è necessario un ID Apple. Dopo aver specificato le credenziali, il dispositivo installa un profilo di gestione che non può essere rimosso. Il profilo di gestione di Intune viene visualizzato in **Impostazioni** > **Generale** > **Gestione dispositivi** nel dispositivo.

Gli utenti possono ora completare la configurazione del dispositivo aziendale tramite il portale aziendale di Intune o l'Assistente configurazione di Apple.
