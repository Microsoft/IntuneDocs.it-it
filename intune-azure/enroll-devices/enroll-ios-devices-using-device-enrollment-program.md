---
title: Registrare i dispositivi iOS - Device Enrollment Program
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni su come registrare i dispositivi iOS di proprietà dell&quot;azienda usando il Device Enrollment Program."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7981a9c0-168e-4c54-9afd-ac51e895042c
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 3e1898441b7576c07793e8b70f3c3f09f1cac534
ms.openlocfilehash: ddeaeb2d532635802c615d09b4625dee0a824919
ms.lasthandoff: 02/23/2017


---

# <a name="enroll-ios-devices-using-device-enrollment-program"></a>Registrare i dispositivi iOS con il Device Enrollment Program

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune può distribuire un profilo di registrazione che registra in modalità wireless i dispositivi iOS acquistati tramite il programma di registrazione dispositivi (DEP). Un profilo contiene le impostazioni di gestione che si desiderano applicare ai dispositivi. Il pacchetto di registrazione può includere opzioni di Assistente configurazione per il dispositivo. La registrazione dei dispositivi registrati tramite DEP non può essere annullata dagli utenti.

>[!NOTE]
>Questo metodo di registrazione non può essere usato con il metodo del [manager di registrazione dispositivi](enroll-devices-using-device-enrollment-manager.md).

Per gestire i dispositivi iOS di proprietà dell'azienda con il programma di registrazione dispositivi (DEP, Device Enrollment Program) di Apple, le organizzazioni devono partecipare al programma DEP di Apple e acquisire i dispositivi attraverso il programma. I dettagli del processo sono disponibili in:  [https://deploy.apple.com](https://deploy.apple.com) I vantaggi del programma includono la configurazione dei dispositivi senza intervento dell'utente e senza dover connettere ogni dispositivo a un computer tramite un cavo USB.

Per registrare i dispositivi iOS di proprietà dell'azienda con DEP, è necessario un [token DEP](get-apple-dep-token.md) di Apple. Questo token consente a Intune di sincronizzare le informazioni sui dispositivi di proprietà dell'azienda che partecipano al programma DEP. Consente inoltre di caricare i profili di registrazione in Apple e assegnare i dispositivi a tali profili.

Altri metodi per la registrazione di dispositivi iOS sono descritti in [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (Scegliere la modalità di registrazione dei dispositivi iOS in Intune).

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di configurare la registrazione di dispositivi iOS:

- [Configurare i domini](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Impostare l'autorità MDM](set-mdm-authority.md)
- [Creare i gruppi](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- Assegnare licenze utente nel [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](get-an-apple-mdm-push-certificate.md)
- [Ottenere un token DEP Apple](get-apple-dep-token.md)

## <a name="create-an-apple-dep-profile-for-devices"></a>Creare un profilo DEP Apple per dispositivi

Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi. La procedura seguente mostra come creare un profilo di registrazione per i dispositivi iOS registrati tramite DEP.

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Registrazione Apple**.

3. In **Gestisci le impostazioni del Device Enrollment Program (DEP)** selezionare **Profili DEP**.

4. Nel pannello **Apple DEP Profiles** (Profili DEP Apple) selezionare **Crea**.

5. Nel pannello **Crea un profilo di registrazione** immettere un nome e una descrizione per il profilo.

6. Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza affinità utente.

 - **Registra con affinità utente**: il dispositivo deve essere associato a un utente durante la configurazione iniziale e può quindi accedere ai dati aziendali e alla posta elettronica. Scegliere l'affinità dell'utente per i dispositivi gestiti tramite DEP che appartengono a utenti e che devono usare il portale aziendale per servizi come l'installazione di app. Si noti che l'autenticazione a più fattori non funziona durante la registrazione nei dispositivi DEP con affinità utente. Dopo la registrazione, l'autenticazione a più fattori funziona come previsto in questi dispositivi. Per i nuovi utenti a cui è richiesto di modificare la password al primo accesso non è possibile richiedere la password durante la registrazione nei dispositivi DEP. Agli utenti con password scadute, inoltre, non verrà richiesto di reimpostare la password durante la registrazione DEP e devono reimpostarla da un dispositivo diverso.

    >[!NOTE]
    >DEP con affinità utente richiede un endpoint misto/nome utente WS-Trust 1.3 per essere abilitato a richiedere token utente.

 - **Registra senza affinità utente**: il dispositivo non è associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

7. Selezionare **Impostazioni di gestione dei dispositivi**, configurare le impostazioni del profilo seguenti e quindi selezionare **Salva**:

    - **Supervisione eseguita**: modalità di gestione che attiva altre opzioni di gestione e disattiva il blocco attivazione per impostazione predefinita. Se si lascia vuota la casella di controllo, le funzionalità di gestione saranno limitate.

    - **Registrazione bloccata**: richiede Modalità di gestione = Supervisione eseguita. Disattiva le impostazioni iOS che potrebbero permettere la rimozione del profilo di gestione. Lasciando vuota la casella di controllo, si consente la rimozione del profilo di gestione dal menu Impostazioni. Questa voce viene configurata durante l'attivazione e può essere modificata solo ripristinando le impostazioni predefinite.

    - **Consenti associazione**: specifica se i dispositivi iOS possono sincronizzarsi con i computer. Se si sceglie **Consenti Apple Configurator per certificato**, è necessario selezionare un certificato in **Certificati di Apple Configurator**.

    - **Certificati di Apple Configurator**: se si è scelto **Consenti Apple Configurator per certificato ** in **Consenti associazione**, selezionare un certificato di Apple Configurator da importare.

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

1. Accedere al [portale del programma di registrazione dispositivi](https://deploy.apple.com) (https://deploy.apple.com) e accedere con l'ID Apple aziendale.

2. Passare a **Programma di distribuzione** &gt; **Programma di registrazione dispositivi** &gt; **Gestione dei dispositivi**.

3. Specificare come **scegliere i dispositivi**, fornire le informazioni sul dispositivo e specificare i dettagli in base al **Numero di serie** del dispositivo, al **Numero dell'ordine**o **caricando un file CSV**.

4. Scegliere **Assegna al server**, selezionare il &lt;nome del server&gt; specificato per Microsoft Intune e fare clic su **OK**.

## <a name="synchronize-dep-managed-devices"></a>Sincronizzare dispositivi gestiti da DEP

1. Nel portale di Azure scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

2. Nel pannello Intune del portale di Azure scegliere **Registra i dispositivi** e quindi scegliere **Registrazione Apple**.

3. In **Gestisci le impostazioni del Device Enrollment Program (DEP)** selezionare **Numeri di serie DEP **.

4. Nel panello **Numeri di serie DEP Apple** selezionare **Sincronizzazione**.

5. Nel pannello **Sincronizzazione** selezionare **Richiedi la sincronizzazione**. L'indicatore di stato mostra la quantità di tempo che è necessario attendere prima di richiedere nuovamente la sincronizzazione.

    Per soddisfare i requisiti Apple per volumi di traffico DEP accettabili, Intune impone le seguenti limitazioni:
     -    Una sincronizzazione DEP completa può essere eseguita solo una volta ogni sette giorni. Durante una sincronizzazione completa, Intune aggiorna tutti i numeri di serie che Apple ha assegnato a Intune, anche se sono già stati sincronizzati in precedenza. Se si tenta una sincronizzazione completa prima che trascorra il periodo di sette giorni, Intune aggiorna solo i numeri di serie che non sono ancora elencati in Intune.
     -    Il tempo concesso per il completamento di una richiesta di sincronizzazione è pari a 10 minuti. Durante questo tempo o fino al completamento della richiesta, il pulsante **Sincronizza** è disabilitato.

>[!NOTE]
>È inoltre possibile assegnare i numeri di serie DEP ai profili dal pannello **Numeri di serie DEP Apple**.

## <a name="distribute-devices-to-users"></a>Distribuire i dispositivi agli utenti

Ora è possibile distribuire i dispositivi di proprietà dell'azienda agli utenti. Quando un dispositivo iOS viene attivato, viene registrato per la gestione con Intune.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>In che modo gli utenti installano e usano il portale aziendale sui dispositivi

I dispositivi configurati con affinità utente possono installare ed eseguire l'app del portale aziendale per scaricare le app e gestire i dispositivi. Dopo aver ricevuto i dispositivi, gli utenti devono eseguire alcuni passaggi supplementari descritti di seguito per completare l'Assistente configurazione e installare l'app Portale aziendale.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Come registrare i dispositivi iOS di proprietà dell'azienda con l'affinità utente

1. Quando gli utenti accendono i dispositivi, viene chiesto di completare l'Assistente configurazione. Durante la configurazione, agli utenti viene chiesto di fornire le credenziali. Devono usare le credenziali (nome personale univoco o UPN) associate alla propria sottoscrizione in Intune.

2. Durante la configurazione, agli utenti viene chiesto di fornire un ID Apple. Devono specificare l'ID Apple, per consentire al dispositivo di installare il portale aziendale. Possono inoltre specificare l'ID dal menu delle impostazioni di iOS al termine dell'installazione.

3. Al termine dell'installazione, gli utenti devono installare l'app Portale aziendale dall'App Store.

4. A questo punto gli utenti possono accedere al portale aziendale con l'UPN usato durante la configurazione del dispositivo.

5. Dopo l'accesso, viene chiesto di registrare il dispositivo. Il primo passaggio consiste nell'identificazione del dispositivo. L'app visualizza un elenco di dispositivi iOS già registrati dall'azienda e assegnati all'account di Intune dell'utente. L'utente deve scegliere il dispositivo corrispondente. Se il dispositivo non è registrato dall'azienda, è necessario selezionare un nuovo dispositivo per continuare con il flusso di registrazione standard.

6. Nella schermata successiva gli utenti devono confermare il numero di serie del nuovo dispositivo. A tale scopo, gli utenti selezionano un collegamento che viene visualizzato. Il collegamento consente di avviare l'app Impostazioni, permettendo quindi agli utenti di verificare il numero di serie. Devono quindi immettere gli ultimi quattro caratteri del numero di serie nell'app Portale aziendale.

   Questo passaggio verifica che il dispositivo sia il dispositivo aziendale registrato in Intune. Se il numero di serie sul dispositivo non corrisponde, è stato selezionato il dispositivo errato. L'utente deve tornare alla schermata precedente e selezionare un dispositivo diverso.

7. Dopo aver verificato il numero di serie, l'app del portale aziendale reindirizza al sito Web del portale aziendale per completare la registrazione. A questo punto, il sito Web chiede agli utenti di tornare all'app.

La registrazione è ora completa e gli utenti possono usare il dispositivo con il set completo di funzionalità.

