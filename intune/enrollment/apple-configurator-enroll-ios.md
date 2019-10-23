---
title: Registrazione di dispositivi iOS - Apple Configurator - Assistente configurazione
titleSuffix: Microsoft Intune
description: Informazioni su come usare lo strumento Apple Configurator per registrare i dispositivi iOS di proprietà dell'azienda con Assistente configurazione.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/04/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 671e4d76-0c61-11e8-ba89-0ed5f89f718b
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21ee59af8c6d24a42ce3f8c9fefedd0e5dba7ba7
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503314"
---
# <a name="set-up-ios-device-enrollment-with-apple-configurator"></a>Configurare la registrazione di dispositivi iOS con Apple Configurator

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune supporta la registrazione di dispositivi iOS con lo strumento [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344) in esecuzione in un computer Mac. La registrazione con Apple Configurator richiede la connessione USB di ogni dispositivo iOS a un computer Mac per configurare la registrazione aziendale. È possibile registrare i dispositivi in Intune con Apple Configurator in due modi:
- **Registrazione con Assistente configurazione**: cancella le impostazioni predefinite del dispositivo e lo prepara per la registrazione durante Assistente configurazione.
- **Registrazione diretta**: non cancella le impostazioni predefinite del dispositivo e lo registra tramite le impostazioni iOS. Questo metodo supporta solo i dispositivi **senza affinità utente**.

I metodi di registrazione con Apple Configurator non possono essere usati con il [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="prerequisites"></a>Prerequisiti

- Accesso fisico ai dispositivi iOS
- [Imposta autorità MDM](../fundamentals/mdm-authority-set.md)
- [Un certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- Numeri di serie dei dispositivi (solo Registrazione con Assistente configurazione)
- Cavi di connessione USB
- Computer macOS che esegue [Apple Configurator 2.0](https://itunes.apple.com/app/apple-configurator-2/id1037126344)

## <a name="create-an-apple-configurator-profile-for-devices"></a>Creare un profilo di Apple Configurator per i dispositivi

Un profilo di registrazione dispositivi consente di definire le impostazioni applicate durante la registrazione. Queste impostazioni vengono applicate una sola volta. Seguire questi passaggi per creare un profilo di registrazione per registrare i dispositivi iOS con Apple Configurator.

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione dispositivo** > **Registrazione Apple** > **Apple Configurator** > **Profili** > **Crea**.

    ![Creare un profilo per Apple Configurator](./media/apple-configurator-enroll-ios/apple-config-create-profile.png)

2. In **Crea un profilo di registrazione** digitare un **nome** e una **descrizione** per il profilo per scopi amministrativi. Questi dettagli non vengono visualizzati agli utenti. È possibile usare questo campo Nome per creare un gruppo dinamico in Azure Active Directory. Usare il nome del profilo per definire il parametro enrollmentProfileName per assegnare i dispositivi con questo profilo di registrazione. Altre informazioni sui gruppi dinamici di Azure Active Directory.

    ![Screenshot della schermata di creazione del profilo con l'opzione Registra con affinità utente selezionata](./media/apple-configurator-enroll-ios/apple-configurator-profile-create.png)

3. In **Affinità utente** scegliere se i dispositivi con questo profilo devono essere registrati con o senza un utente assegnato.

    - **Registra con affinità utente**: scegliere questa opzione per i dispositivi che appartengono a utenti e che vogliono usare il portale aziendale per servizi come l'installazione di app. Il dispositivo deve essere associato a un utente con Assistente configurazione e può quindi accedere ai dati aziendali e alla posta elettronica. È supportata solo per la registrazione con Assistente configurazione. Per l'affinità utente è richiesto [endpoint misto/nome utente WS-Trust 1.3](https://technet.microsoft.com/library/adfs2-help-endpoints). [Altre informazioni](https://technet.microsoft.com/itpro/powershell/windows/adfs/get-adfsendpoint).

    - **Registra senza affinità utente**: scegliere questa opzione per i dispositivi non associati a un singolo utente. Usare questa opzione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno. Obbligatorio per la registrazione diretta.

     > [!NOTE]
     > Quando si seleziona **Registra con affinità utente** , assicurarsi che il dispositivo venga associato a un utente con Assistente configurazione entro le prime 24 ore di registrazione del dispositivo. In caso contrario, la registrazione potrebbe non riuscire e sarà necessario il ripristino delle impostazioni predefinite per registrare il dispositivo.

4. Se si sceglie **Registra con affinità utente**, è possibile consentire agli utenti di eseguire l'autenticazione con il portale aziendale invece di Assistente configurazione Apple.

    > [!NOTE]
    > Se si vuole eseguire una delle operazioni seguenti, impostare **Authenticate with Company Portal instead of Setup Assistant** (Autenticazione con il portale aziendale invece di Assistente configurazione) su **Sì**.
    >    - Usare l'autenticazione a più fattori
    >    - Richiedere agli utenti di modificare la password al primo accesso
    >    - Richiedere agli utenti di reimpostare le password scadute durante la registrazione
    >
    > Non sono supportate durante l'autenticazione con l'Assistente configurazione di Apple.


6. Scegliere **Crea** per salvare il profilo.

## <a name="setup-assistant-enrollment"></a>Registrazione con Assistente configurazione

### <a name="add-apple-configurator-serial-numbers"></a>Aggiungere i numeri di serie di Apple Configurator

1. Creare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere i numeri di serie nella colonna sinistra e i dettagli nella colonna destra. Il limite massimo corrente per l'elenco è di 5.000 righe. In un editor di testo l'elenco con estensione csv è simile al seguente:

    F7TLWCLBX196, dettagli del dispositivo</br>
    DLXQPCWVGHMJ, dettagli del dispositivo

   Informazioni su [come trovare il numero di serie di un dispositivo iOS](https://support.apple.com/HT204073).
2. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione dispositivo** > **Registrazione Apple** > **Apple Configurator** > **Dispositivi** > **Aggiungi**.

5. Selezionare un **Profilo di registrazione** da applicare ai numeri di serie che si stanno importando. Se si vuole che i dettagli del nuovo numero di serie sovrascrivano i dettagli esistenti, scegliere **Sovrascrivere i dettagli per gli identificatori esistenti**.
6. In **Importa dispositivi** individuare il file con estensione CSV dei numeri di serie e selezionare **Aggiungi**.

### <a name="reassign-a-profile-to-device-serial-numbers"></a>Riassegnare un profilo a numeri di serie dei dispositivi

È possibile assegnare un profilo di registrazione quando si importano i numeri di serie iOS per la registrazione con Apple Configurator. È anche possibile assegnare i profili da due diverse posizioni nel portale di Azure:
- **Dispositivi di Apple Configurator**
- **Profili AC**

#### <a name="assign-from-apple-configurator-devices"></a>Eseguire l'assegnazione da dispositivi di Apple Configurator
1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione dispositivo** > **Registrazione Apple** > **Apple Configurator** > **Dispositivi** > scegliere i numeri di serie > **Assegna profilo**.
2. In **Assegna profilo** scegliere il **Nuovo profilo** da assegnare e quindi scegliere **Assegna**.

#### <a name="assign-from-profiles"></a>Eseguire l'assegnazione dai profili
1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione dispositivo** > **Registrazione Apple** > **Apple Configurator** > **Profili** >scegliere un profilo.
2. Nel profilo scegliere **Dispositivi assegnati** e quindi scegliere **Assegna**.
3. Applicare un filtro per trovare i numeri di serie dei dispositivi da assegnare al profilo, selezionare i dispositivi e quindi scegliere **Assegna**.

### <a name="export-the-profile"></a>Esportare il profilo
Dopo aver creato il profilo e assegnato i numeri di serie, è necessario esportare il profilo da Intune come URL. Il profilo dovrà poi essere importato in Apple Configurator in un Mac per la distribuzione ai dispositivi.

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione dispositivo** > **Registrazione Apple** > **Apple Configurator** > **Profili** >scegliere il profilo da esportare.
2. Nel profilo selezionare **Esporta il profilo**.
3. Copiare l'**URL del profilo**. È quindi possibile aggiungerlo in Apple Configurator per definire il profilo di Intune usato dai dispositivi iOS.

   A questo punto è necessario importare questo profilo in Apple Configurator come descritto nella procedura seguente per definire il profilo di Intune usato dai dispositivi iOS.

### <a name="enroll-devices-with-setup-assistant"></a>Registrare i dispositivi con Assistente configurazione

1. In un computer Mac aprire **Apple Configurator 2**. Nella barra dei menu scegliere **Apple Configurator 2** e quindi scegliere **Preferences** (Preferenze).
    > [!WARNING]
    > Durante il processo di registrazione vengono ripristinate le impostazioni predefinite dei dispositivi. Come procedura consigliata, reimpostare il dispositivo e accenderlo. I dispositivi dovrebbero trovarsi nella schermata **Hello** quando si connette il dispositivo.
    > Se il dispositivo è già stato registrato con l'account ID Apple, deve essere eliminato da Apple iCloud prima di avviare il processo di registrazione. Viene visualizzato il messaggio di errore "Impossibile attivare [nome dispositivo]".

2. Nel riquadro **Preferences** (Preferenze) selezionare **Servers** (Server) e fare clic sul segno più (+) per avviare la procedura guidata per il server MDM. Scegliere **Avanti**.
3. Immettere il **nome o l'URL dell'host** e l'**URL di registrazione** per il server MDM in Registrazione di Assistente configurazione per i dispositivi iOS con Microsoft Intune. Per l'URL di registrazione immettere l'URL del profilo di registrazione esportato da Intune. Scegliere **Avanti**.  
    È possibile ignorare tranquillamente un avviso in cui è indicato che l'URL del server non è verificato. Per continuare, fare clic su **Next** (Avanti) fino a completare la procedura guidata.
4. Connettere i dispositivi mobili iOS al computer Mac con un adattatore USB.
5. Selezionare i dispositivi iOS da gestire e scegliere **Prepare** (Prepara). Nel riquadro **Prepare iOS Device** (Prepara dispositivo iOS) selezionare **Manual** (Manuale) e quindi scegliere **Next** (Avanti).
6. Nel riquadro **Enroll in MDM Server** (Registra su server MDM) selezionare il nome del server creato e quindi scegliere **Next** (Avanti).
7. Nel riquadro **Supervise Devices** (Supervisione dispositivi) selezionare il livello di supervisione e quindi scegliere **Next** (Avanti).
8. Nel riquadro **Create an Organization** (Crea un'organizzazione) scegliere un'organizzazione in **Organization** (Organizzazione) oppure crearne una nuova e quindi scegliere **Next** (Avanti).
9. Nel riquadro **Configure iOS Setup Assistant** (Configura Assistente configurazione di iOS) scegliere i passaggi da presentare all'utente e quindi fare clic su **Prepare** (Prepara). Se richiesto, eseguire l'autenticazione per aggiornare le impostazioni di attendibilità.  
10. Al termine della preparazione del dispositivo iOS, disconnettere il cavo USB.  

### <a name="distribute-devices"></a>Distribuire i dispositivi
I dispositivi sono ora pronti per la registrazione aziendale. Spegnere i dispositivi e distribuirli agli utenti. All'accensione dei dispositivi viene avviato l'Assistente configurazione.

Dopo che gli utenti ricevono i dispositivi, devono completare i passaggi richiesti dall'Assistente configurazione. I dispositivi configurati con affinità utente possono installare ed eseguire l'app Portale aziendale per scaricare le app e gestire i dispositivi.

## <a name="direct-enrollment"></a>Registrazione diretta
Durante la registrazione diretta dei dispositivi iOS con Apple Configurator, è possibile registrare un dispositivo senza acquisire il numero di serie del dispositivo. È anche possibile denominare il dispositivo per scopi di identificazione prima che Intune acquisisca il nome del dispositivo durante la registrazione. L'app Portale aziendale non è supportata per i dispositivi con registrazione diretta. Questo metodo non cancella il dispositivo.

Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non possono essere installate.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Esportare il profilo come file con estensione mobileconfig per i dispositivi iOS

1. In [Intune](https://aka.ms/intuneportal) scegliere **Registrazione dispositivo** > **Registrazione Apple** > **Apple Configurator** > **Profili** >scegliere il profilo da esportare > **Esporta profilo**.
2. In **Registrazione diretta** scegliere **Scarica profilo** e salvare il file. Un file del profilo di registrazione è valido solo per due settimane, dopodiché è necessario crearlo di nuovo.
3. Trasferire il file in un computer Mac che esegue [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) per effettuare il push direttamente come profilo di gestione per i dispositivi iOS.
4. Preparare il dispositivo con Apple Configurator usando la procedura seguente:
    1. In un computer Mac aprire Apple Configurator 2.0.
    2. Connettere il dispositivo iOS al computer Mac con un cavo USB. Chiudere Photos, iTunes e altre app che vengono aperte quando viene rilevato il dispositivo.
    3. In Apple Configurator selezionare il dispositivo iOS connesso e scegliere **Aggiungi**. Nell'elenco a discesa vengono visualizzate le opzioni che possono essere aggiunte al dispositivo. Scegliere **Profili**.

        ![Schermata Esporta il profilo per la registrazione con Assistente installazione con l'URL del profilo evidenziato](./media/apple-configurator-enroll-ios/ios-apple-configurator-add-profile.png)

    4. Usare il selettore file per selezionare il file con estensione mobileconfig esportato da Intune e scegliere **Aggiungi**. Il profilo viene aggiunto al dispositivo. Se per il dispositivo è indicato Supervisione non eseguita, l'installazione richiede l'accettazione sul dispositivo.
5. Usare la procedura seguente per installare il profilo nel dispositivo iOS. Il dispositivo deve aver già completato l'Assistente configurazione ed essere pronto per l'uso. Se la registrazione comporta distribuzioni di app, il dispositivo deve avere un ID Apple configurato perché, per la distribuzione di app, è necessario l'accesso all'App Store con un ID Apple.
    1. Sbloccare il dispositivo iOS.
    2. Nella finestra di dialogo **Installa profilo** del **profilo di gestione** scegliere **Installa**.
    3. Indicare il passcode del dispositivo o l'ID Apple, se necessario.
    4. Accettare l'**avviso** e scegliere **Installa**.
    5. Accettare l'**avviso remoto** e scegliere **Attendibile**.
    6. Quando la casella **Profilo installato** conferma che il profilo è Installato, scegliere **Fine**.

6. Nel dispositivo iOS aprire la finestra **Impostazioni** e passare a **Generale**  >  **Gestione dei dispositivi**  >  **Profilo di gestione**. Verificare che l'installazione del profilo è inclusa nell'elenco e controllare le restrizioni dei criteri iOS e le app installate. La visualizzazione delle restrizioni dei criteri e delle app nel dispositivo può impiegare fino a 10 minuti.

7. Distribuire i dispositivi. Il dispositivo iOS è ora registrato in Intune e gestito.





