---
title: Configurare la registrazione al programma Apple School Manager per i dispositivi iOS
titlesuffix: Azure portal
description: "Informazioni su come configurare la registrazione al programma Apple School Manager per i dispositivi iOS di proprietà dell'azienda con Intune\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6b3ecc9af91d1a78f84dd6d4b8f47f0bf3e8c742
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Abilitare la registrazione di dispositivi iOS con Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento offre informazioni utili per abilitare la registrazione dei dispositivi iOS acquistati tramite il programma [Apple School Manager](https://school.apple.com/). Con Intune e Apple School Manager, è possibile registrare un numero elevato di dispositivi iOS senza interventi diretti. Quando uno studente o un insegnante accende il dispositivo, l'Assistente configurazione viene eseguito con impostazioni preconfigurate e il dispositivo viene registrato nella gestione.

Per abilitare la registrazione di Apple School Manager, si usano entrambi i portali di Intune e Apple School Manager. È necessario un elenco di numeri di serie o un numero di ordine di acquisto per poter assegnare i dispositivi a Intune per la gestione. Si creano profili di registrazione DEP contenenti le impostazioni da applicare ai dispositivi durante la registrazione.

La registrazione di Apple School Manager non può essere usata con il [programma Device Enrollment Program di Apple](device-enrollment-program-enroll-ios.md) o con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

**Prerequisiti**
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- [Autorità di gestione dei dispositivi mobili](mdm-authority-set.md)
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- Per l'affinità utente è richiesto [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).
- Dispositivi acquistati dal programma [Apple School Management](http://school.apple.com)

**Passaggi per la registrazione di Apple School Manager**
1. [Ottenere un token di Apple School Manager e assegnare i dispositivi](#get-the-apple-token-and-assign-devices)
2. [Creare un profilo di registrazione](#create-an-apple-enrollment-profile)
3. [Connettere School Data Sync](#connect-school-data-sync) (facoltativo)
4. [Sincronizzare i dispositivi gestiti da Apple School Manager](#sync-managed-devices)
5. [Assegnare un profilo di Apple School Manager ai dispositivi](#assign-a-profile-to-devices)
6. [Distribuire i dispositivi agli utenti](#distribute-devices-to-users)

>[!NOTE]
>L'autenticazione a più fattori non funziona durante la registrazione nei dispositivi Apple School Manager con affinità utente. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto in questi dispositivi. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto nei dispositivi. I dispositivi non possono richiedere agli utenti di modificare la password al primo accesso. Inoltre, agli utenti con password scadute non viene richiesto di reimpostare la password durante la registrazione e devono reimpostarla da un altro dispositivo.


## <a name="get-the-apple-token-and-assign-devices"></a>Ottenere il token Apple e assegnare i dispositivi

Per registrare i dispositivi iOS di proprietà dell'azienda in Apple School Manager, è necessario un file di token (con estensione p7m) di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi che partecipano al programma Apple School Manager. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili. Nel portale Apple è inoltre possibile assegnare i numeri di serie dei dispositivi da gestire.

**Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare un token Apple.**<br>
1. Nel [portale di Azure in Intune](https://aka.ms/intuneportal) scegliere **Registrazione del dispositivo** e quindi scegliere **Token DEP**.

  ![Schermata del pannello Token DEP nell'area di lavoro dei certificati Apple per scaricare la chiave pubblica.](./media/enrollment-program-token-download.png)

2. Nel pannello **Token DEP** scegliere **Scarica la chiave pubblica** per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale Apple School Manager.

**Passaggio 2: Scaricare un token e assegnare i dispositivi.**<br>
1. Scegliere **Crea un token tramite Apple School Manager** e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token di Apple School Manager.
2.  Nel [portale di Apple School Manager](https://school.apple.com) passare a **Server MDM** e quindi scegliere **Aggiungi server MDM** (in alto a destra).
3.  Immettere il **nome del server MDM**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.
   ![Screenshot del portale di Apple School Manager con l'opzione del numero di serie selezionata](./media/asm-server-assignment.png)

4.  Scegliere **Carica file** nel portale Apple, selezionare il file con estensione pem e quindi scegliere **Salva server MDM** (in basso a destra).
5.  Scegliere **Ottieni token** e quindi scaricare il file token del server (con estensione p7m) nel computer.
6. Passare ad **Assegnazioni di dispositivi** e **scegliere il dispositivo** inserendo manualmente i **numeri di serie**, il **numero di ordine** o **caricando un file CSV**.
     ![Screenshot del portale di Apple School Manager con l'opzione del numero di serie selezionata](./media/asm-device-assignment.png)
7.  Scegliere l'azione **Assegna al server ** e scegliere il **server MDM** creato.
8. Specificare come **scegliere i dispositivi** e quindi fornire dettagli e informazioni sul dispositivo.
9. Scegliere **Assegna al server**, selezionare il &lt;nome del server&gt; specificato per Microsoft Intune e fare clic su **OK**.

**Passaggio 3: Immettere l'ID Apple usato per creare il token di Apple School Manager.**<br>Questo ID deve essere usato per rinnovare il token di Apple School Manager e viene archiviato per riferimento futuro.

![Screenshot della specifica dell'ID Apple usato per creare il token DEP e passare al token DEP.](./media/enrollment-program-token-apple-id.png)

**Passaggio 4: Individuare e caricare il token.**<br>
Passare al file del certificato (con estensione p7m), scegliere **Apri** e quindi selezionare **Carica**. Intune sincronizzerà automaticamente i dispositivi Apple School Manager da Apple.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple
Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nel portale di Azure in Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
2. In **Programma di registrazione ** scegliere **Profili DEP**.
3. Nel pannello **Profili DEP** scegliere **Crea**.
4. Nel pannello **Crea un profilo di registrazione** immettere un **nome** e una **descrizione** per il profilo visualizzato in Intune.
5. Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza affinità utente.

 - **Registra con affinità utente**: il dispositivo viene affiliato a un utente durante l'installazione.

  La modalità iPad condiviso di Apple School Manager richiede la registrazione dell'utente senza affinità utente.

 - **Registra senza affinità utente**: scegliere questa opzione per un dispositivo non associato a un singolo utente, come i dispositivi condivisi. Usare questa impostazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app come l'app Portale aziendale non funzionano.

6. Scegliere **Impostazioni di gestione dei dispositivi**. Questi elementi vengono impostati durante l'attivazione e richiedono il ripristino delle impostazioni predefinite per la modifica. Configurare le impostazioni del profilo seguenti e quindi scegliere **Salva**:

  ![Screenshot della scelta della modalità di gestione. Le impostazioni del dispositivo sono le seguenti: Supervisione eseguita, Registrazione bloccata, Consenti associazione impostato su Rifiuta tutto. Per un nuovo profilo DEP, l'opzione Certificati di Apple Configurator è disattivata.](./media/enrollment-program-profile-mode.png)

    - **Supervisione eseguita**: modalità di gestione che attiva altre opzioni di gestione e disattiva il blocco attivazione per impostazione predefinita. Se si lascia vuota la casella di controllo, le funzionalità di gestione saranno limitate.

     - **Registrazione bloccata**: richiede Modalità di gestione = Supervisione eseguita. Disattiva le impostazioni iOS che potrebbero permettere la rimozione del profilo di gestione. Lasciando vuota la casella di controllo, si consente la rimozione del profilo di gestione dal menu Impostazioni.
   - **iPad condiviso**: richiede le modalità **Registra senza affinità utente** e **Supervisione eseguita**. Consente a più utenti di eseguire l'accesso agli iPad registrati usando un ID Apple gestito. Gli ID Apple gestiti sono creati nel portale Apple School Manager. Altre informazioni sull'[iPad condiviso](education-settings-configure-ios-shared.md).
   >[!NOTE]
   >Se **Affinità utente** è impostata su **Con affinità utente** o la modalità **Supervisione eseguita** è impostata su **Disattivato**, la modalità iPad condiviso è disabilitata per il profilo di registrazione.

        - **Maximum Cached Users** - (Requires **Shared iPad** = **Yes**) Creates a partition on the device for each user. The recommended value is the number of students likely to use the device over a period of time. For example, if six students use the device regularly during the week, set this number to six.  

    - **Consenti associazione**: specifica se i dispositivi iOS possono sincronizzarsi con i computer. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

      - **Certificati di Apple Configurator**: se si è scelto **Consenti Apple Configurator per certificato ** in **Consenti associazione**, scegliere un certificato di Apple Configurator da importare.

7. Scegliere **Impostazioni dell'Assistente configurazione**, configurare le impostazioni del profilo seguenti e quindi scegliere **Salva**:

    - **Nome del reparto**: viene visualizzata quando gli utenti toccano **Informazioni configurazione** durante l'attivazione.

    - **Telefono del reparto**: viene visualizzata quando l'utente fa clic sul pulsante Richiesta di assistenza durante l'attivazione.
    - **Opzioni dell'assistente di configurazione**: se escluse dalle opzioni di Assistente configurazione, queste impostazioni possono essere configurate in un secondo momento nel menu **Impostazioni** di iOS.
        - **Passcode**: consente di richiedere un passcode durante l'attivazione. Richiedere sempre un passcode, a meno che il dispositivo non sia protetto o l'accesso al dispositivo non venga controllato in un altro modo, ad esempio con la modalità tutto schermo, che limita l'uso del dispositivo a una sola app.
        - **Servizi di posizione**: se l'opzione è abilitata, Assistente configurazione richiede il servizio al momento dell'attivazione.
        - **Ripristina**: se l'opzione è abilitata, Assistente configurazione richiede il backup in iCloud durante l'attivazione.
        - **ID Apple**: se l'opzione è abilitata, iOS richiede agli utenti un ID Apple quando Intune prova a installare un'app senza ID. È necessario un ID Apple per il download delle app da iOS App Store, incluse le app installate da Intune.
        - **Terms and Conditions** (Termini e condizioni): se l'opzione è abilitata, Assistente configurazione richiede di accettare i termini e condizioni Apple durante l'attivazione.
        - **ID tocco**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Apple Pay**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Zoom**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Siri**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Dati di diagnostica**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.

8. Per salvare le impostazioni del profilo, scegliere **Crea** nel pannello **Crea un profilo di registrazione**.

## <a name="connect-school-data-sync"></a>Connettere School Data Sync
(Facoltativo) Apple School Manager supporta la sincronizzazione dei dati dell'elenco di classi in Azure Active Directory (AD) tramite Microsoft School Data Sync (SDS). Completare i passaggi seguenti per usare SDS per sincronizzare i dati dell'istituto di istruzione.

1. Nel pannello **Token DEP** scegliere il banner informativo di colore blu oppure **Connetti SDS**.
2. Scegliere **Consenti a Microsoft School Data Sync di usare questo token**, impostando **Consenti**. Questa impostazione consente a Intune di connettersi con SDS in Office 365.
3. Per abilitare una connessione tra Apple School Manager e Azure AD, scegliere **Configura Microsoft School Data Sync**. Altre informazioni su [come configurare School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Fare clic su **OK** per salvare e continuare.

## <a name="sync-managed-devices"></a>Sincronizzare i dispositivi gestiti
Dopo aver assegnato le autorizzazioni per gestire i dispositivi Apple School Manager a Intune, è possibile sincronizzare Intune con il servizio Apple per visualizzare i dispositivi gestiti in Intune.

1. Nel portale di Azure in Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
2. In **Dispositivi DEP** scegliere **Sincronizza**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.
3. Nel pannello **Sincronizzazione** scegliere **Richiedi la sincronizzazione**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.

  ![Screenshot del pannello Sincronizza con la scelta del collegamento Richiedi la sincronizzazione.](./media/enrollment-program-device-request-sync.png)

  Per soddisfare i requisiti Apple per il traffico accettabile, Intune impone le seguenti limitazioni:
   -    Una sincronizzazione completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna tutti i numeri di serie che Apple ha assegnato a Intune, anche se sono già stati sincronizzati in precedenza. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
   -    Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.

>[!NOTE]
>È anche possibile assegnare i numeri di serie di Apple School Manager ai profili dal pannello **Dispositivi DEP**.

## <a name="assign-a-profile-to-devices"></a>Assegnare un profilo ai dispositivi
Ai dispositivi Apple School Manager gestiti da Intune deve essere assegnato un profilo di registrazione prima di registrarli.

1. Nel portale di Azure in Intune scegliere **Registrazione del dispositivo** > **Registrazione Apple** e quindi scegliere **Profili DEP**.
2. Nell'elenco **Profili DEP** scegliere il profilo che si vuole assegnare ai dispositivi e quindi scegliere **Device Assignments** (Assegnazioni dispositivi).

 ![Screenshot delle assegnazioni dei dispositivi con Assegna selezionato.](./media/enrollment-program-device-assign.png)

3. Scegliere **Assegna** e quindi scegliere i dispositivi Apple School Manager a cui si vuole assegnare il profilo. È possibile applicare un filtro per visualizzare i dispositivi disponibili:
  - **non assegnato**
  - **qualsiasi**
  - **&lt;nome profilo&gt;**
4. Scegliere i dispositivi che si vuole assegnare. La casella di controllo sopra la colonna consente di selezionare fino a 1000 dispositivi elencati. Fare clic su **Assegna**. Per registrare più di 1000 dispositivi, ripetere i passaggi di assegnazione fino a quando non è stato assegnato un profilo di registrazione a tutti i dispositivi.

  ![Screenshot del pulsante Assegna per assegnare il profilo DEP in Intune](media/dep-profile-assignment.png)

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

Ora è possibile distribuire i dispositivi di proprietà dell'azienda agli utenti. Quando un dispositivo Apple School Manager iOS viene attivato, viene registrato per la gestione con Intune. Se il dispositivo è stato attivato ed è in uso, il profilo potrà essere applicato solo dopo il ripristino delle impostazioni predefinite del dispositivo.
