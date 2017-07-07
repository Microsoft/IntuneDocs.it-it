---
title: Configurare la registrazione al programma Apple School Manager per i dispositivi iOS
titleSuffix: Intune on Azure
description: "Informazioni su come configurare la registrazione al programma Apple School Manager per i dispositivi iOS di proprietà dell'azienda con Intune\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 73556209c88759ffe0747d9927cbcbb49600e0c0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="enable-ios-device-enrollment-with-apple-school-manager"></a>Abilitare la registrazione di dispositivi iOS con Apple School Manager

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento offre agli amministratori IT informazioni utili per abilitare la registrazione dei dispositivi iOS acquistati tramite il programma [Apple School Manager (ASM)](https://school.apple.com/). Microsoft Intune può distribuire un profilo di registrazione in modalità wireless che registra i dispositivi ASM nella gestione. L'amministratore non deve mai intervenire su ciascun dispositivo gestito. Un profilo ASM contiene le impostazioni di gestione che vengono applicate ai dispositivi durante la registrazione, incluse le opzioni di Assistente configurazione.

**Procedura di registrazione tramite ASM**
1. [Ottenere un token ASM e assegnare i dispositivi](#get-the-asm-token-and-assign-devices)
2. [Creare un profilo di registrazione](#create-an-apple-enrollment-profile)
3. [Connettere School Data Sync](#connect-school-data-sync) (facoltativo)
4. [Sincronizzare i dispositivi gestiti tramite ASM](#sync-asm-managed-devices)
5. [Assegnare il profilo ai dispositivi ASM](#assign-an-asm-profile-to-devices)
6. [Distribuire i dispositivi agli utenti](#distribute-devices-to-users)

>[!NOTE]
>La registrazione ASM non può essere usata con [Device Enrollment Program (DEP)](device-enrollment-program-enroll-ios.md) di Apple o con l'account del [manager di registrazione dispositivi](device-enrollment-manager-enroll.md) di Intune.

## <a name="get-the-apple-asm-token-and-assign-devices"></a>Ottenere un token ASM Apple e assegnare i dispositivi

Per registrare i dispositivi iOS di proprietà dell'azienda con Apple School Manager (ASM), è necessario un file di token ASM (con estensione p7m) di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi che partecipano al programma ASM. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili. Nel portale Apple è inoltre possibile assegnare i numeri di serie dei dispositivi da gestire.

**Prerequisiti**
- [Certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- Registrazione per [Apple School Management](http://school.apple.com)

**Passaggio 1. Scaricare il certificato di chiave pubblica di Intune necessario per creare un token ASM Apple.**<br>
1. Nel [portale di Intune ](https://aka.ms/intuneportal) in Azure scegliere **Registrazione del dispositivo** e quindi selezionare **Token DEP**.
2. Nel pannello **Token DEP** selezionare **Scarica la chiave pubblica** per scaricare e salvare il file della chiave di crittografia (con estensione pem) in locale. Il file PEM viene usato per richiedere un certificato di relazione di trust dal portale Apple School Manager.

**Passaggio 2: Scaricare un token ASM e assegnare i dispositivi.**<br>
Selezionare **Crea un token tramite Apple School Manager** e accedere con l'ID Apple aziendale. Lo stesso ID Apple può essere usato per rinnovare il token ASM.

   1.  Nel [portale Apple School Manager](https://school.apple.com) passare a **Server MDM** e quindi selezionare **Aggiungi server MDM** (in alto a destra).
   2.  Immettere il **nome del server MDM**. Il nome del server viene immesso come riferimento per identificare il server MDM (Mobile Device Management, Gestione dei dispositivi mobili). Non è il nome o l'URL del server di Microsoft Intune.
   3.  Selezionare **Carica file** nel portale Apple, selezionare il file con estensione pem e quindi selezionare **Salva server MDM** (in basso a destra).
   4.  Selezionare **Ottieni token** e quindi scaricare il file token del server (con estensione p7m) nel computer.
   5. Passare ad **Assegnazioni di dispositivi** e **scegliere il dispositivo** inserendo manualmente i **numeri di serie**, il **numero di ordine** o **caricando un file CSV**.
   6.   Scegliere l'azione **Assegna al server**  e selezionare il **server MDM** creato.
   7. Specificare come **scegliere i dispositivi**, fornire le informazioni sul dispositivo e specificare i dettagli in base al **Numero di serie** del dispositivo, al **Numero dell'ordine**o **caricando un file CSV**.
   8. Scegliere **Assegna al server**, selezionare il &lt;nome del server&gt; specificato per Microsoft Intune e fare clic su **OK**.

**Passaggio 3: Immettere l'ID Apple usato per creare il token ASM.**<br>Questo ID deve essere usato per rinnovare il token ASM Apple e viene archiviato per riferimento futuro.

**Passaggio 4: Individuare e caricare il token.**<br>
Passare al file del certificato (con estensione p7m), scegliere **Apri** e quindi selezionare **Carica**. Intune sincronizzerà automaticamente i dispositivi ASM da Apple.

## <a name="create-an-apple-enrollment-profile"></a>Creare un profilo di registrazione di Apple
Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi durante la registrazione.

1. Nel portale di Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
2. In **Programma di registrazione**  selezionare **Profili DEP**.
3. Nel pannello **Profili DEP** selezionare **Crea**.
4. Nel pannello **Crea un profilo di registrazione** immettere un **nome** e una **descrizione** per il profilo visualizzato nel portale Intune.
5. Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza affinità utente.

 - **Registra con affinità utente**: il dispositivo deve essere associato a un utente durante la configurazione iniziale e può quindi accedere ai dati aziendali e alla posta elettronica. Scegliere l'affinità utente per i dispositivi gestiti tramite ASM a cui gli utenti accedono con l'ID Apple gestito.

 >[!NOTE]
 >L'autenticazione a più fattori non funziona durante la registrazione nei dispositivi ASM con affinità utente. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto in questi dispositivi.

  La modalità iPad condiviso di Apple School Manager richiede la registrazione dell'utente con l'affinità utente.

 >[!NOTE]
    >ASM con affinità utente richiede l'abilitazione di un [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints) per richiedere il token utente. [Altre informazioni su WS-Trust 1.3](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

 - **Registra senza affinità utente**: il dispositivo non è associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'affinità utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

6. Selezionare **Impostazioni di gestione dei dispositivi**. Questi elementi vengono impostati durante l'attivazione e richiedono il ripristino delle impostazioni predefinite per la modifica. Configurare le impostazioni del profilo seguenti e quindi selezionare **Salva**:

    - **Supervisione eseguita**: modalità di gestione che attiva altre opzioni di gestione e disattiva il blocco attivazione per impostazione predefinita. Se si lascia vuota la casella di controllo, le funzionalità di gestione saranno limitate.

    - **Registrazione bloccata**: richiede Modalità di gestione = Supervisione eseguita. Disattiva le impostazioni iOS che potrebbero permettere la rimozione del profilo di gestione. Lasciando vuota la casella di controllo, si consente la rimozione del profilo di gestione dal menu Impostazioni.

  - **iPad condiviso**: richiede le modalità **Registra con affinità utente** e **Supervisione eseguita**. Consente a più utenti di eseguire l'accesso agli iPad registrati usando un ID Apple gestito. Gli ID Apple gestiti sono creati nel portale Apple School Manager.

  >[!NOTE]
  >Se la modalità **iPad condiviso** è abilitata in un profilo e la modalità **Affinità utente** o **Supervisione eseguita** è impostata su **Disattivato**, la modalità iPad condiviso è disabilitata per il profilo di registrazione.

  - **Numero massimo di utenti memorizzati nella cache**: richiede **iPad condiviso** = **Sì**. Crea una partizione nel dispositivo per ogni utente. Il valore consigliato è il numero di studenti che potrebbero usare il dispositivo in un determinato periodo di tempo. Se ad esempio il dispositivo viene usato regolarmente da sei studenti nel corso della settimana, impostare questo numero su sei.  

    - **Consenti associazione**: specifica se i dispositivi iOS possono sincronizzarsi con i computer. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

    - **Certificati di Apple Configurator**: se si è scelto **Consenti Apple Configurator per certificato**  in **Consenti associazione**, selezionare un certificato di Apple Configurator da importare.

7. Selezionare **Impostazioni dell'Assistente configurazione**, configurare le impostazioni del profilo seguenti e quindi selezionare **Salva**:

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

8. Per salvare le impostazioni del profilo, selezionare **Crea** nel pannello **Crea un profilo di registrazione**.

## <a name="connect-school-data-sync"></a>Connettere School Data Sync
(Facoltativo) ASM supporta la sincronizzazione dei dati dell'elenco di classi in Azure Active Directory (AD) tramite Microsoft School Data Sync (SDS). Completare i passaggi seguenti per usare SDS per sincronizzare i dati dell'istituto di istruzione.

1. Nel pannello **Token DEP** selezionare il banner informativo di colore blu oppure **Connetti SDS**.
2. Selezionare **Consenti a Microsoft School Data Sync di usare questo token**, impostando **Consenti**. Questa impostazione consente a Intune di connettersi con SDS in Office 365.
3. Per abilitare una connessione tra ASM e Azure AD, selezionare **Configura Microsoft School Data Sync**. Altre informazioni su [come configurare School Data Sync](https://support.office.com/article/Install-the-School-Data-Sync-Toolkit-8e27426c-8c46-416e-b0df-c29b5f3f62e1).
4. Fare clic su **OK** per salvare e continuare.

## <a name="sync-asm-managed-devices"></a>Sincronizzare i dispositivi gestiti tramite ASM
Dopo aver assegnato le autorizzazioni per gestire i dispositivi ASM a Intune, è possibile sincronizzare Intune con il servizio ASM per visualizzare i dispositivi gestiti nel portale di Intune.

1. Nel portale di Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
2. In **Dispositivi DEP** selezionare **Sincronizza**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.

    Per soddisfare i requisiti Apple per volumi di traffico ASM accettabili, Intune impone le seguenti limitazioni:
     -  Una sincronizzazione ASM completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna tutti i numeri di serie che Apple ha assegnato a Intune, anche se sono già stati sincronizzati in precedenza. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
     -  Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 15 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.

>[!NOTE]
>È inoltre possibile assegnare i numeri di serie ASM ai profili dal pannello **Dispositivi DEP**.

## <a name="assign-an-asm-profile-to-devices"></a>Assegnare un profilo ASM ai dispositivi
Ai dispositivi ASM gestiti da Intune deve essere assegnato un profilo ASM prima della registrazione.

1. Nel portale di Intune scegliere **Registrazione del dispositivo** > **Registrazione Apple** e quindi selezionare **Profili DEP**.
2. Nell'elenco **Profili DEP** selezionare il profilo che si vuole assegnare ai dispositivi e quindi selezionare **Assegnazioni di dispositivi**.
3. Selezionare **Assegna** e quindi selezionare i dispositivi ASM a cui si vuole assegnare il profilo. È possibile filtrare per visualizzare i dispositivi ASM disponibili:
  - **non assegnato**
  - **qualsiasi**
  - **&lt;Nome del profilo ASM&gt;**
4. Selezionare i dispositivi che si vuole assegnare. La casella di controllo sopra la colonna consente di selezionare fino a 1000 dispositivi elencati. Fare clic su **Assegna**. Per registrare più di 1000 dispositivi, ripetere i passaggi di assegnazione fino ad assegnare un profilo ASM a tutti i dispositivi.

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

Ora è possibile distribuire i dispositivi di proprietà dell'azienda agli utenti. Quando un dispositivo ASM iOS viene attivato, viene registrato per la gestione con Intune. Se il dispositivo è stato attivato ed è in uso, il profilo potrà essere applicato solo dopo il ripristino delle impostazioni predefinite del dispositivo.

### <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>In che modo gli utenti installano e usano il portale aziendale sui dispositivi

I dispositivi configurati con affinità utente possono installare ed eseguire l'app del portale aziendale per scaricare le app e gestire i dispositivi. Dopo che gli utenti ricevono i dispositivi, devono eseguire l'Assistente configurazione e installare l'app Portale aziendale.
