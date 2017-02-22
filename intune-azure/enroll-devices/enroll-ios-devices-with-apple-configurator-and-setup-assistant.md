---
title: Registrare dispositivi iOS - Apple Configurator e Assistente configurazione | Anteprima di Intune in Azure | Documentazione Microsoft
description: "Anteprima di Intune in Azure: informazioni su come usare lo strumento Apple Configurator per registrare i dispositivi iOS di proprietà dell&quot;azienda con Assistente configurazione."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: adb2fd27d7f2b3f0ef4dce6b26fcb20d74b69a00
ms.openlocfilehash: 8c6c92e6e7bd375063f2f19308fe19f6e44962ac


---

# <a name="enroll-ios-devices-with-apple-configurator-and-setup-assistant"></a>Registrare dispositivi iOS con Apple Configurator e Assistente configurazione 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda con lo strumento [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) in esecuzione in un computer Mac. Questo processo ripristina le impostazioni predefinite del dispositivo e lo prepara per l'esecuzione di Assistente configurazione, installando i criteri della società per il nuovo utente del dispositivo.

>[!NOTE]
>Questo metodo di registrazione non può essere usato con il metodo del [manager di registrazione dispositivi](enroll-devices-using-device-enrollment-manager.md).

Con Apple Configurator è possibile ripristinare le impostazioni predefinite dei dispositivi iOS in modo da prepararli per poter essere configurati per il nuovo utente del dispositivo. Per questo metodo è necessario connettere il dispositivo iOS a un computer Mac tramite USB per configurare la registrazione aziendale e si presuppone l'uso di Apple Configurator 2.0. La maggior parte degli scenari richiede che i criteri applicati al dispositivo iOS includano l'affinità utente per abilitare l'app Portale aziendale di Intune.

Altri metodi per la registrazione di dispositivi iOS sono descritti in [Choose how to enroll iOS devices in Intune](choose-ios-enrollment-method.md) (Scegliere la modalità di registrazione dei dispositivi iOS in Intune).

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di configurare la registrazione di dispositivi iOS:

- [Configurare i domini](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Impostare l'autorità MDM](set-mdm-authority.md)
- [Creare i gruppi](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurare il Portale aziendale](/intune-azure/manage-apps/company-portal-app.md)
- Assegnare licenze utente nel [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](get-an-apple-mdm-push-certificate.md)
- Assicurarsi di avere accesso fisico ai dispositivi iOS
- Ottenere i numeri di serie dei dispositivi (vedere [Come trovare il numero di serie di un prodotto Apple](https://support.apple.com//HT204308))
- Avere a disposizione i cavi di connessione USB
- Assicurarsi di disporre di un computer Mac con [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)
- [Aggiungere numeri di serie di Apple Configurator](add-apple-configurator-serial-numbers.md)


## <a name="create-an-apple-configurator-profile-for-devices"></a>Creare un profilo di Apple Configurator per i dispositivi

Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi. La procedura seguente mostra come creare un profilo di registrazione dispositivi per i dispositivi iOS registrati tramite Apple Configurator.

1. Nel portale di Azure scegliere **Altri servizi**, immettere **Intune** nella casella di testo e quindi scegliere **Altro** > **Intune**.

2. Nel pannello Intune scegliere **Registra i dispositivi** e quindi selezionare **Registrazione Apple**.

3. In **Gestisci le impostazioni di registrazione di Apple Configurator** selezionare **Profili AC**.

4. Nel pannello **Profili di registrazione di Apple Configurator** selezionare **Crea**.

5. Nel pannello **Crea un profilo di registrazione** immettere un nome e una descrizione per il profilo.

6. Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza affinità utente.

   - **Registra con affinità utente**: il dispositivo deve essere associato a un utente durante la configurazione iniziale e può quindi accedere ai dati aziendali e alla posta elettronica. L'affinità dell'utente deve essere configurata per i dispositivi gestiti tramite DEP che appartengono a utenti e che devono usare il portale aziendale per servizi come l'installazione di app.

   - **Registra senza affinità utente**: il dispositivo non è associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

7. Selezionare **Crea** per salvare il profilo.

## <a name="assign-serial-numbers-to-an-apple-configurator-profile"></a>Assegnare i numeri di serie a un profilo di Apple Configurator

Dopo aver creato i profili di Apple Configurator, è possibile assegnare i numeri di serie dei dispositivi ai profili. Per essere in grado di assegnare i numeri di serie, è necessario prima aggiungerli a Intune seguendo i passaggi descritti in [Aggiungere i numeri di serie di Apple Configurator](add-apple-configurator-serial-numbers.md).

### <a name="assign-serial-numbers-to-apple-configurator-profiles"></a>Assegnare i numeri di serie ai profili di Apple Configurator

1. Dal pannello **Profili di registrazione di Apple Configurator** selezionare il profilo a cui assegnare i numeri di serie.

2. Nel pannello denominato per il profilo selezionare **Numeri di serie** > **Assegna**.

3. Selezionare i numeri di serie da assegnare al profilo e quindi selezionare il pulsante **Assegna**.

## <a name="export-the-profile-to-ios-devices"></a>Esportare il profilo da distribuire ai dispositivi iOS

Dopo aver creato il profilo e assegnato i numeri di serie, è necessario esportare il profilo da Intune, come un URL o un file nel formato descritto di seguito. Viene quindi importato manualmente nel programma Apple Configurator su un Mac, che successivamente lo distribuisce ai dispositivi.

### <a name="export-a-profile-using-setup-assistant-enrollment"></a>Esportare un profilo tramite la registrazione di Assistente configurazione

1. Nel pannello **Profili di registrazione di Apple Configurator** selezionare il profilo da esportare.

2. Nel pannello per il profilo selezionare **Esporta il profilo**.

3. Copiare l'URL del profilo in [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) con il dispositivo iOS collegato. Verrà caricato in Apple Configurator in un secondo momento per definire il profilo di Intune usato dai dispositivi iOS.

  Per supportare Apple Configurator 2 è necessario modificare l'URL del profilo 2.0. A tale scopo, sostituire questo codice:
    ```
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=
    ```
    Con questo codice:

    ```
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=
    ```

   L'URL del profilo verrà caricato nel servizio Apple DEP con Apple Configurator nella procedura seguente, per definire il profilo di Intune usato dai dispositivi iOS.

4. Caricare l'URL del profilo nel servizio Apple DEP con Apple Configurator per definire il profilo di Intune usato dai dispositivi iOS.


    1.  In un computer Mac aprire **Apple Configurator 2**. Nella barra dei menu scegliere **Apple Configurator 2** e quindi scegliere **Preferences** (Preferenze).

         > [!WARNING]
         > Le impostazioni predefinite dei dispositivi verranno ripristinate durante il processo di registrazione. Come procedura consigliata, reimpostare il dispositivo e accenderlo. I dispositivi dovrebbero trovarsi nella schermata **Hello** quando si connette il dispositivo.

    2. Nel riquadro delle **preferenze** selezionare **Server** e quindi fare clic sul simbolo più (+) per avviare la procedura guidata per il server MDM. Scegliere **Avanti**.

    3. Immettere **Nome** e **URL di registrazione** per il server MDM dal passaggio 6 in Registrazione di Assistente configurazione per i dispositivi iOS con Microsoft Intune. Per l'URL di registrazione immettere l'URL del profilo di registrazione esportato da Intune. Scegliere **Avanti**.  

       È possibile ignorare tranquillamente un avviso in cui è indicato che l'URL del server non è verificato. Per continuare, fare clic su **Next** (Avanti) fino a completare la procedura guidata.

    4.  Connettere i dispositivi mobili iOS al computer Mac con un adattatore USB.

        > [!WARNING]
        > Le impostazioni predefinite dei dispositivi verranno ripristinate durante il processo di registrazione. Come procedura consigliata, reimpostare il dispositivo e accenderlo. I dispositivi dovrebbero trovarsi nella schermata **Hello** quando si avvia Assistente di configurazione.

    5.  Fare clic su **Prepare** (Prepara). Nel riquadro **Prepare iOS Device** (Prepara dispositivo iOS) selezionare **Manual** (Manuale) e quindi scegliere **Next** (Avanti).

    6. Nel riquadro **Enroll in MDM Server** (Registra su server MDM) selezionare il nome del server creato e quindi scegliere **Next** (Avanti).

    7. Nel riquadro **Supervise Devices** (Supervisione dispositivi) selezionare il livello di supervisione e quindi scegliere **Next** (Avanti).

    8. Nel riquadro **Create an Organization** (Crea un'organizzazione) scegliere un'organizzazione in **Organization** (Organizzazione) oppure crearne una nuova e quindi scegliere **Next** (Avanti).

    9. Nel riquadro **Configure iOS Setup Assistant** (Configura Assistente configurazione di iOS) scegliere i passaggi da presentare all'utente e quindi fare clic su **Prepare** (Prepara). Se richiesto, eseguire l'autenticazione per aggiornare le impostazioni di attendibilità.  

    10. Al termine della preparazione del dispositivo iOS, disconnettere il cavo USB.  

8.  **Distribuire i dispositivi**.
    I dispositivi sono ora pronti per la registrazione aziendale. Spegnere i dispositivi e distribuirli agli utenti. All'accensione dei dispositivi verrà avviato l'Assistente configurazione.

## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>In che modo gli utenti installano e usano il portale aziendale sui dispositivi

I dispositivi configurati con affinità utente possono installare ed eseguire l'app del portale aziendale per scaricare le app e gestire i dispositivi. Dopo aver ricevuto i dispositivi, gli utenti devono eseguire alcuni passaggi supplementari descritti di seguito per completare l'Assistente configurazione e installare l'app Portale aziendale.

### <a name="how-users-enroll-corporate-owned-ios-devices-with-user-affinity"></a>Come registrare i dispositivi iOS di proprietà dell'azienda con l'affinità utente

1. Quando gli utenti accendono i dispositivi, viene chiesto di completare l'Assistente configurazione. Durante la configurazione, agli utenti viene chiesto di fornire le credenziali. Devono usare le credenziali (nome personale univoco o UPN) associate alla propria sottoscrizione in Intune.

2. Durante la configurazione, agli utenti viene chiesto di fornire un ID Apple. Devono specificare l'ID Apple, per consentire al dispositivo di installare il portale aziendale. Possono inoltre specificare l'ID dal menu delle impostazioni di iOS al termine dell'installazione.

3. Al termine dell'installazione, il dispositivo iOS deve installare l'app del portale aziendale dall'App Store.

4. A questo punto l'utente può accedere al portale aziendale con l'UPN usato durante la configurazione del dispositivo.

5. Dopo l'accesso, viene chiesto di registrare il dispositivo. Il primo passaggio consiste nell'identificazione del dispositivo. L'app visualizza un elenco di dispositivi iOS già registrati dall'azienda e assegnati all'account di Intune dell'utente. L'utente deve scegliere il dispositivo corrispondente. Se il dispositivo non è registrato dall'azienda, è necessario selezionare un nuovo dispositivo per continuare con il flusso di registrazione standard.

6. Nella schermata successiva gli utenti devono confermare il numero di serie del nuovo dispositivo. Gli utenti possono toccare il collegamento di conferma del numero di serie per avviare l'app Impostazioni e verificare il numero di serie. Devono quindi immettere gli ultimi quattro caratteri del numero di serie nell'app Portale aziendale.

    Questo passaggio verifica che il dispositivo sia il dispositivo aziendale registrato in Intune. Se il numero di serie sul dispositivo non corrisponde, è stato selezionato il dispositivo errato. L'utente deve tornare alla schermata precedente e selezionare un dispositivo diverso.

7. Dopo aver verificato il numero di serie, l'app del portale aziendale reindirizza al sito Web del portale aziendale per completare la registrazione. A questo punto, il sito Web chiede agli utenti di tornare all'app.

La registrazione è ora completa e gli utenti possono usare il dispositivo con il set completo di funzionalità.



<!--HONumber=Feb17_HO1-->


