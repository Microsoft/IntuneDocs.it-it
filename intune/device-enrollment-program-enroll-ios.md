---
title: Registrare i dispositivi iOS - Device Enrollment Program
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni su come registrare i dispositivi iOS di proprietà dell&quot;azienda usando il Device Enrollment Program."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 5144b9e7c17a3323667b9ca68cb47829d69866c3
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Registrare i dispositivi iOS con il Device Enrollment Program

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Questo argomento offre agli amministratori IT informazioni utili per registrare i dispositivi iOS di proprietà dell'azienda acquistati tramite [Apple Device Enrollment Program (DEP)](https://deploy.apple.com). Microsoft Intune consente di distribuire un profilo di registrazione per la registrazione tramite DEP "in modalità wireless", in modo che l'amministratore non debba interagire direttamente con ogni dispositivo gestito. Un profilo DEP contiene le impostazioni di gestione da applicare ai dispositivi durante la registrazione. Il pacchetto di registrazione può includere opzioni di Assistente configurazione per il dispositivo.

>[!NOTE]
>La registrazione tramite DEP non può essere usata con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).
>Inoltre, se gli utenti registrano i propri dispositivi iOS tramite l'app Portale aziendale e i numeri di serie di tali dispositivi vengono poi importati con corrispondente assegnazione di un profilo DEP, la registrazione del dispositivo in Intune verrà annullata.

**Procedura di registrazione tramite DEP**
1. [Ottenere un token DEP Apple](#get-the-apple-dep-certificate)
2. [Creare un profilo DEP](#create-an-apple-dep-profile)
3. [Assegnare i numeri di serie DEP Apple al server Intune](#assign-apple-dep-serial-numbers-to-your-mdm-server)
4. [Sincronizzare i dispositivi gestiti tramite DEP](#synchronize-dep-managed-devices)
5. [Assegnare un profilo DEP ai dispositivi](#assign-a-dep-profile-to-devices)
6. [Distribuire i dispositivi agli utenti](#distribute-devices-to-users)

## <a name="get-the-apple-dep-certificate"></a>Ottenere il certificato DEP Apple
Per registrare i dispositivi iOS di proprietà dell'azienda con Apple Device Enrollment Program (DEP), è necessario un file di certificato DEP di Apple (con estensione p7m). Questo token consente a Intune di sincronizzare le informazioni sui dispositivi di proprietà dell'azienda che partecipano al programma DEP. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Per gestire i dispositivi iOS di proprietà dell'azienda con DEP, le organizzazioni devono aderire al programma DEP di Apple e acquisire i dispositivi attraverso il programma. I dettagli del processo sono disponibili all'indirizzo: https://deploy.apple.com. I vantaggi del programma includono la configurazione dei dispositivi senza intervento dell'utente e senza dover connettere ogni dispositivo a un computer tramite un cavo USB.

> [!NOTE]
> Se è stata effettuata la migrazione del tenant Intune dalla console classica di Intune al portale di Azure e durante il periodo di migrazione è stato eliminato un token DEP Apple dalla console di amministrazione di Intune, il token DEP potrebbe essere stato ripristinato nell'account di Intune. È possibile eliminare nuovamente il token DEP dal portale di Azure.

**Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare un token DEP Apple.**<br>
1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**. Nel pannello Intune scegliere **Registrazione del dispositivo** > **Token DEP Apple**.
2. Selezionare **Download your public key** (Scarica la chiave pubblica) per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale del programma di registrazione dispositivi di Apple.

**Passaggio 2: Scaricare un token DEP Apple dal sito Web Apple appropriato.**<br>
Selezionare [Creare un token DEP tramite i programmi di distribuzione Apple](https://deploy.apple.com) (https://deploy.apple.com) e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token DEP.

   1.  Nel [portale di Apple Device Enrollment Program](https://deploy.apple.com) passare a **Programma di registrazione dei dispositivi** &gt; **Gestisci server** e quindi scegliere **Aggiungi server MDM**.
   2.  Immettere il **nome del server MDM** e scegliere **Avanti**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.
   3.  Si apre la finestra di dialogo **Aggiungi &lt;NomeServer&gt;**. Fare clic su **Scegli file** per caricare il file PEM e scegliere **Avanti**.
   4.  La finestra di dialogo **Aggiungi &lt;Nome Server&gt;** include un collegamento al **Token del server**. Scaricare il file token del server (con estensione p7m) nel computer e fare clic su **Fine**.

**Passaggio 3: Immettere l'ID Apple usato per creare il token DEP Apple. Questo ID può essere usato per rinnovare il token.**

**Passaggio 4: Passare al token DEP Apple da caricare. Intune eseguirà automaticamente la sincronizzazione con l'account DEP.**<br>
Passare al file (con estensione pem) del certificato, scegliere **Apri** e quindi selezionare **Carica**. Con il certificato push, Intune può registrare e gestire i dispositivi iOS eseguendo il push dei criteri nei dispositivi mobili registrati.

## <a name="create-an-apple-dep-profile"></a>Creare un profilo DEP Apple

Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi. La procedura seguente mostra come creare un profilo di registrazione per i dispositivi iOS registrati tramite DEP.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
2. Nel pannello Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
3. In **Gestisci le impostazioni del Device Enrollment Program (DEP)** selezionare **Profili DEP**.
4. Nel pannello **Apple DEP Profiles** (Profili DEP Apple) selezionare **Crea**.
5. Nel pannello **Crea un profilo di registrazione** immettere un nome e una descrizione per il profilo.
6. Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza affinità utente.

 - **Registra con affinità utente**: il dispositivo deve essere associato a un utente durante la configurazione iniziale e può quindi accedere ai dati aziendali e alla posta elettronica. Scegliere l'affinità dell'utente per i dispositivi gestiti tramite DEP che appartengono a utenti e che devono usare il portale aziendale per servizi come l'installazione di app. Si noti che l'autenticazione a più fattori non funziona durante la registrazione nei dispositivi DEP con affinità utente. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto in questi dispositivi. Per i nuovi utenti a cui è richiesto di modificare la password al primo accesso non è possibile richiedere la password durante la registrazione nei dispositivi DEP. Agli utenti con password scadute, inoltre, non verrà richiesto di reimpostare la password durante la registrazione DEP e devono reimpostarla da un dispositivo diverso.

    >[!NOTE]
    >DEP con affinità utente richiede un [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/en-us/library/adfs2-help-endpoints) per essere abilitato a richiedere token utente. [Altre informazioni su WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Registra senza affinità utente**: il dispositivo non è associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

7. Selezionare **Impostazioni di gestione dei dispositivi**, configurare le impostazioni del profilo seguenti e quindi selezionare **Salva**:

    - **Supervisione eseguita**: modalità di gestione che attiva altre opzioni di gestione e disattiva il blocco attivazione per impostazione predefinita. Se si lascia vuota la casella di controllo, le funzionalità di gestione saranno limitate.

    - **Registrazione bloccata**: richiede Modalità di gestione = Supervisione eseguita. Disattiva le impostazioni iOS che potrebbero permettere la rimozione del profilo di gestione. Lasciando vuota la casella di controllo, si consente la rimozione del profilo di gestione dal menu Impostazioni. Questa voce viene configurata durante l'attivazione e può essere modificata solo ripristinando le impostazioni predefinite.

    - **Consenti associazione**: specifica se i dispositivi iOS possono sincronizzarsi con i computer. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

    - **Certificati di Apple Configurator**: se si è scelto **Consenti Apple Configurator per certificato**  in **Consenti associazione**, selezionare un certificato di Apple Configurator da importare.

8. Selezionare **Impostazioni dell'Assistente configurazione**, configurare le impostazioni del profilo seguenti e quindi selezionare **Salva**:

    - **Nome del reparto**: viene visualizzata quando gli utenti toccano **Informazioni configurazione** durante l'attivazione.

    - **Telefono del reparto**: viene visualizzata quando l'utente fa clic sul pulsante Richiesta di assistenza durante l'attivazione.
    - **Opzioni dell'assistente di configurazione**: queste impostazioni facoltative possono essere configurate in un secondo momento nel menu **Impostazioni** di iOS.
        - **Passcode**: consente di richiedere un passcode durante l'attivazione. Richiedere sempre un passcode, a meno che il dispositivo non sia protetto o l'accesso al dispositivo non venga controllato in un altro modo (ad esempio, con la modalità tutto schermo, che limita l'uso del dispositivo a una sola app).
        - **Servizi di posizione**: se l'opzione è abilitata, Assistente configurazione richiede il servizio al momento dell'attivazione.
        - **Ripristina**: se l'opzione è abilitata, Assistente configurazione richiede il backup in iCloud durante l'attivazione.
        - **ID Apple**: se l'opzione è abilitata, iOS richiede agli utenti un ID Apple quando Intune prova a installare un'applicazione senza ID. È necessario un ID Apple per il download delle app da iOS App Store, incluse le app installate da Intune.
        - **Terms and Conditions** (Termini e condizioni): se l'opzione è abilitata, Assistente configurazione richiede di accettare i termini e condizioni Apple durante l'attivazione.
        - **ID tocco**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Apple Pay**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Zoom**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Siri**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.
        - **Dati di diagnostica**: se l'opzione è abilitata, Assistente configurazione richiede questo servizio durante l'attivazione.

9. Per salvare le impostazioni del profilo, selezionare **Crea** nel pannello **Crea un profilo di registrazione**.

## <a name="assign-apple-dep-serial-numbers-to-your-mdm-server"></a>Assegnare i numeri di serie DEP Apple al server MDM
I numeri di serie del dispositivo deve essere assegnati al server MDM Intune nel portale web DEP di Apple per consentire a Intune di gestire tali dispositivi.

1. Accedere al [portale del programma di registrazione dispositivi](https://deploy.apple.com) (https://deploy.apple.com) e accedere con l'ID Apple aziendale.

2. Passare a **Programma di distribuzione** &gt; **Programma di registrazione dispositivi** &gt; **Gestione dei dispositivi**.

3. Specificare come **scegliere i dispositivi**, fornire le informazioni sul dispositivo e specificare i dettagli in base al **Numero di serie** del dispositivo, al **Numero dell'ordine**o **caricando un file CSV**.

4. Scegliere **Assegna al server**, selezionare il &lt;nome del server&gt; specificato per Microsoft Intune e fare clic su **OK**.

## <a name="synchronize-dep-managed-devices"></a>Sincronizzare i dispositivi gestiti tramite DEP
Dopo aver assegnato le autorizzazioni per gestire i dispositivi DEP a Intune, è possibile sincronizzare Intune con il servizio DEP per visualizzare i dispositivi gestiti nel portale di Intune.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune del portale di Azure scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.

3. In **Gestisci le impostazioni del Device Enrollment Program (DEP)** selezionare **Numeri di serie DEP** .

4. Nel panello **Numeri di serie DEP Apple** selezionare **Sincronizzazione**.

5. Nel pannello **Sincronizzazione** selezionare **Richiedi la sincronizzazione**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.

    Per soddisfare i requisiti Apple per volumi di traffico DEP accettabili, Intune impone le seguenti limitazioni:
     -    Una sincronizzazione DEP completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna tutti i numeri di serie che Apple ha assegnato a Intune, anche se sono già stati sincronizzati in precedenza. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
     -    Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 10 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.

>[!NOTE]
>È inoltre possibile assegnare i numeri di serie DEP ai profili dal pannello **Numeri di serie DEP Apple**.

## <a name="assign-a-dep-profile-to-devices"></a>Assegnare un profilo DEP ai dispositivi
Ai dispositivi DEP gestiti da Intune deve essere assegnato un profilo DEP prima della registrazione.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune del portale di Azure scegliere **Registrazione del dispositivo** > **Registrazione Apple** e quindi selezionare **Profili DEP**.

3. Nell'elenco **Profili di registrazione DEP Apple** selezionare il profilo che si vuole assegnare ai dispositivi e quindi selezionare **Assegnazioni di dispositivi**.

4. Selezionare **Assegna** e quindi selezionare i dispositivi DEP a cui si vuole assegnare il profilo. È possibile filtrare per visualizzare i dispositivi DEP disponibili:
  - **non assegnato**
  - **qualsiasi**
  - **&lt;Nome del profilo DEP&gt;**

  ![Screenshot del pulsante Assegna per l'assegnazione di un profilo DEP nel portale di Intune](media/dep-profile-assignment.png)

5. Selezionare i dispositivi che si vuole assegnare. La casella di controllo sopra la colonna consentirà di selezionare fino a 1000 dispositivi elencati. Fare quindi clic su **Assegna**. Per registrare più di 1000 dispositivi, ripetere i passaggi di assegnazione fino ad assegnare un profilo DEP a tutti i dispositivi.

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

Ora è possibile distribuire i dispositivi di proprietà dell'azienda agli utenti. Quando un dispositivo DEP iOS viene attivato, viene registrato per la gestione con Intune. Se il dispositivo è stato attivato ed è in uso, il profilo potrà essere applicato solo dopo il ripristino delle impostazioni predefinite del dispositivo.

Vedere [Come informare gli utenti finali su Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune). È anche possibile indicare agli utenti finali di [usare il dispositivo iOS o macOS con Intune](https://docs.microsoft.com/intune/deploy-use/how-to-educate-your-end-users-about-microsoft-intune) 

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>In che modo gli utenti installano e usano il portale aziendale sui dispositivi

I dispositivi configurati con affinità utente possono installare ed eseguire l'app del portale aziendale per scaricare le app e gestire i dispositivi. Dopo aver ricevuto i dispositivi, gli utenti devono eseguire alcuni passaggi supplementari descritti di seguito per completare l'Assistente configurazione e installare l'app Portale aziendale.

