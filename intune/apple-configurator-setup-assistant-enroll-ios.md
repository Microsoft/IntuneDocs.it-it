---
title: Registrare i dispositivi iOS - Apple Configurator-Assistente configurazione
titleSuffix: Intune on Azure
description: "Informazioni su come usare lo strumento Apple Configurator per registrare i dispositivi iOS di proprietà dell'azienda con Assistente configurazione.\""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6d384cd0-b662-41e7-94f5-0c96790ab20a
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1d74fbcebfe89bbafc545d11dd6316cb602db8ee
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="enroll-ios-devices-with-apple-configurator"></a>Registrare i dispositivi iOS con Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune supporta la registrazione di dispositivi iOS di proprietà dell'azienda con lo strumento [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) in esecuzione in un computer Mac. La registrazione con Apple Configurator richiede la connessione USB di ogni dispositivo iOS a un computer Mac per configurare la registrazione aziendale. È possibile registrare i dispositivi in Intune con Apple Configurator in due modi:
- **Registrazione di Assistente configurazione** - Ripristina le impostazioni predefinite del dispositivo e lo prepara per l'esecuzione di Assistente configurazione, installando i criteri della società per il nuovo utente del dispositivo. La maggior parte degli scenari richiede che i criteri applicati al dispositivo iOS includano l'affinità utente per abilitare l'app Portale aziendale di Intune.
- **Registrazione diretta** - Non ripristina le impostazioni predefinite del dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi **senza affinità utente**.

>[!NOTE]
>Questo metodo di registrazione non può essere usato con il metodo del [manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

Altri metodi per la registrazione di dispositivi iOS sono descritti in [Choose how to enroll iOS devices in Intune](enrollment-method-choose-ios.md) (Scegliere la modalità di registrazione dei dispositivi iOS in Intune).

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di configurare la registrazione di dispositivi iOS:

- [Un certificato push MDM Apple](apple-mdm-push-certificate-get.md)
- Accesso fisico ai dispositivi iOS
- Numeri di serie del dispositivo (vedere [Come ottenere un numero di serie iOS](https://support.apple.com//HT204308))
- Cavi di connessione USB
- Computer Mac con [Apple Configurator 2.0](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)
- [Aggiungere numeri di serie di Apple Configurator](apple-configurator-serial-numbers-add.md)

## <a name="setup-assistant-enrollment"></a>Registrazione con Assistente configurazione

### <a name="create-an-apple-configurator-profile-for-devices"></a>Creare un profilo di Apple Configurator per i dispositivi

Un profilo di registrazione dispositivi consente di definire le impostazioni applicate a un gruppo di dispositivi. La procedura seguente mostra come creare un profilo di registrazione dispositivi per i dispositivi iOS registrati tramite Apple Configurator.

1. Nel portale di Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
2. In **Gestisci le impostazioni di registrazione di Apple Configurator** selezionare **Profili AC**.
3. Nel pannello **Profili di registrazione di Apple Configurator** selezionare **Crea**.
4. Nel pannello **Crea un profilo di registrazione** immettere un nome e una descrizione per il profilo.
5. Per **Affinità utente**, scegliere se i dispositivi con questo profilo verranno registrati con o senza affinità utente.

   - **Registra con affinità utente**: il dispositivo deve essere associato a un utente durante la configurazione iniziale e può quindi accedere ai dati aziendali e alla posta elettronica. L'affinità utente deve essere configurata per i dispositivi gestiti appartenenti a utenti che devono usare il portale aziendale per servizi come l'installazione di app.
   - **Registra senza affinità utente**: il dispositivo non è associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.

6. Selezionare **Crea** per salvare il profilo.

### <a name="add-apple-configurator-serial-numbers"></a>Aggiungere i numeri di serie di Apple Configurator

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare la procedura seguente per aggiungere i numeri di serie a Intune quando si vuole [registrare dispositivi iOS di proprietà dell'azienda con Apple Configurator e Assistente configurazione](apple-configurator-setup-assistant-enroll-ios.md). È possibile aggiungere i numeri di serie uno alla volta o caricare un file di testo in formato CSV con i numeri di serie. Dopo aver aggiunto i numeri di serie, è possibile assegnare a questi un profilo. Il profilo contiene le impostazioni di gestione specifiche che si desiderano applicare ai dispositivi.

Altri metodi per la registrazione di dispositivi iOS sono descritti in [Choose how to enroll iOS devices in Intune](enrollment-method-choose-ios.md) (Scegliere la modalità di registrazione dei dispositivi iOS in Intune).

**Per aggiungere numeri di serie di Apple Configurator a Intune**

1. Creare un elenco di valori a due colonne, delimitato da virgole (file con estensione CSV) senza intestazione. Aggiungere l'identificatore IMEI nella colonna a sinistra e i dettagli nella colonna destra. Il limite massimo corrente per l'elenco è di 500 righe. In un editor di testo, l'elenco CSV è simile al seguente:

    F7TLWCLBX196, dettagli del dispositivo</br>
    DLXQPCWVGHMJ, dettagli del dispositivo

2. Nel portale di Azure scegliere **Registra i dispositivi** e quindi scegliere **Registrazione Apple**.
3. In **Gestisci le impostazioni di registrazione di Apple Configurator** selezionare **Numeri di serie di Apple Configurator**.
4. Nel panello **Numeri di serie di Apple Configurator** selezionare **Aggiungi**.
5. Nel pannello **Aggiungi i numeri di serie** selezionare un profilo da applicare ai numeri di serie che si stanno importando. Se si sta importando un file con nuovi dettagli che sovrascriveranno quelli esistenti, selezionare "Sovrascrivere i dettagli per gli identificatori esistenti." per sostituire i dettagli esistenti con i nuovi.
6. Localizzare il file con estensione CSV dei numeri di serie e selezionare **Aggiungi**.

### <a name="assign-a-profile-to-specific-serial-numbers"></a>Assegnare un profilo a numeri di serie specifici

Intune consente di assegnare i profili da due diverse posizioni nel portale di Azure. È possibile eseguire l'assegnazione tramite il profilo di Apple Configurator oppure tramite i dispositivi.

#### <a name="assign-by-devices"></a>Eseguire l'assegnazione tramite i dispositivi
1. Nel portale di Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
3. Nel pannello **Dispositivi di Apple Configurator** selezionare i numeri di serie a cui assegnare un profilo, quindi scegliere **Assegna profilo**.
4. Nel pannello **Assegna profilo** selezionare il profilo che si desidera assegnare e quindi scegliere **Assegna**.

#### <a name="assign-by-profiles"></a>Eseguire l'assegnazione tramite i profili
1. Nel portale di Intune scegliere **Registrazione del dispositivo** e quindi scegliere **Registrazione Apple**.
2. Scegliere **Profili AC** e selezionare il profilo a cui assegnare i numeri di serie.
3. Nel pannello denominato per il profilo selezionare **Numeri di serie** > **Assegna**.
4. Selezionare i numeri di serie da assegnare al profilo e quindi selezionare il pulsante **Assegna**.

### <a name="export-the-profile-to-ios-devices"></a>Esportare il profilo da distribuire ai dispositivi iOS
Dopo aver creato il profilo e assegnato i numeri di serie, è necessario esportare il profilo da Intune, come un URL o un file nel formato descritto di seguito. Viene quindi importato manualmente nel programma Apple Configurator su un Mac, che successivamente lo distribuisce ai dispositivi.

1. Nel portale di Intune scegliere il pannello **Profili di registrazione di Apple Configurator**, quindi selezionare il profilo da esportare.
2. Nel pannello per il profilo selezionare **Esporta il profilo**.
3. Copiare l'URL del profilo in [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) con il dispositivo iOS collegato. Verrà caricato in Apple Configurator in un secondo momento per definire il profilo di Intune usato dai dispositivi iOS.

  È necessario caricare l'URL del profilo nel servizio Apple usando Apple Configurator nella procedura seguente per definire il profilo di Intune usato dai dispositivi iOS.
4. Caricare l'URL del profilo nel servizio Apple usando Apple Configurator per definire il profilo di Intune usato dai dispositivi iOS.
 1.  In un computer Mac aprire **Apple Configurator 2**. Nella barra dei menu scegliere **Apple Configurator 2** e quindi scegliere **Preferences** (Preferenze).
  > [!WARNING]
  > Le impostazioni predefinite dei dispositivi verranno ripristinate durante il processo di registrazione. Come procedura consigliata, reimpostare il dispositivo e accenderlo. I dispositivi dovrebbero trovarsi nella schermata **Hello** quando si connette il dispositivo.
  2. Nel riquadro **Preferences** (Preferenze) selezionare **Servers** (Server) e fare clic sul segno più (+) per avviare la procedura guidata per il server MDM. Scegliere **Avanti**.
  3. Immettere il **nome o l'URL dell'host** e l'**URL di registrazione** per il server MDM in Registrazione di Assistente configurazione per i dispositivi iOS con Microsoft Intune. Per l'URL di registrazione immettere l'URL del profilo di registrazione esportato da Intune. Scegliere **Avanti**.  

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
6.  **Distribuire i dispositivi**.
    I dispositivi sono ora pronti per la registrazione aziendale. Spegnere i dispositivi e distribuirli agli utenti. All'accensione dei dispositivi verrà avviato l'Assistente configurazione.

## <a name="direct-enrollment"></a>Registrazione diretta
Durante la registrazione diretta dei dispositivi iOS con Apple Configurator, è possibile registrare un dispositivo senza acquisire il numero di serie del dispositivo. È anche possibile denominare il dispositivo per scopi di identificazione prima che Intune acquisisca il nome del dispositivo durante la registrazione. L'app Portale aziendale non è supportata per i dispositivi con registrazione diretta. In queste istruzioni si presuppone l'uso di Apple Configurator 2.0 in un computer Mac.

1. Nel portale di Intune scegliere **Registrazione del dispositivo**, **Registrazione Apple** e quindi selezionare **Profili AC**.
2. Nel pannello **Profili di registrazione di Apple Configurator** selezionare **Crea**.
3. Nel pannello **Crea un profilo di registrazione** immettere un nome e una descrizione per il profilo.
4. Per **Affinità utente** scegliere **Registra senza affinità utente** per accertarsi che il dispositivo non sia associato a un utente. Usare questa associazione per i dispositivi che eseguono attività senza accedere ai dati utente locali. Le app che richiedono l'associazione utente, inclusa l'app Portale aziendale usata per installare le app line-of-business, non funzioneranno.
5. Selezionare **Crea** per salvare il profilo.

### <a name="export-the-profile-as-mobileconfig-to-ios-devices"></a>Esportare il profilo come file con estensione mobileconfig per i dispositivi iOS

1. Nel pannello **Esporta il profilo** scaricare il profilo di registrazione in [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) per inviarlo direttamente come profilo di gestione a un dispositivo iOS connesso. Non è necessario alcun ripristino delle impostazioni predefinite.
2. Preparare il dispositivo con Apple Configurator usando la procedura seguente.
  1. In un computer Mac aprire Apple Configurator 2.0.
  2. Connettere il dispositivo iOS al computer Mac con un cavo USB. Chiudere Photos, iTunes e altre app che vengono aperte quando viene rilevato il dispositivo.
  3. In Apple Configurator selezionare il dispositivo iOS connesso e scegliere **Aggiungi**. Nell'elenco a discesa vengono visualizzate le opzioni che possono essere aggiunte al dispositivo. Scegliere **Profili**.
  4. Usare il selettore file per selezionare il file con estensione mobileconfig esportato da Intune e scegliere **Aggiungi**. Il profilo viene aggiunto al dispositivo. Se per il dispositivo è indicato Supervisione non eseguita, l'installazione richiederà l'accettazione sul dispositivo.
3. Usare la procedura seguente per installare il profilo nel dispositivo iOS. Il dispositivo deve aver già completato l'Assistente configurazione ed essere pronto per l'uso. Se la registrazione comporta distribuzioni dell'app, il dispositivo deve avere un ID Apple configurato perché le distribuzioni di app richiederanno l'accesso all'App Store con un ID Apple.
   1. Sbloccare il dispositivo iOS.
   2. Nella finestra di dialogo **Installa profilo** del **profilo di gestione** scegliere **Installa**.
   3. Indicare il passcode del dispositivo o l'ID Apple, se necessario.
   4. Accettare l'**avviso** e scegliere **Installa**.
   5. Accettare l'**avviso remoto** e scegliere **Attendibile**.
   6. Quando la casella **Profilo installato** conferma che il profilo è Installato, scegliere **Fine**.

    4. Nel dispositivo iOS aprire la finestra **Impostazioni** e passare a **Generale**  >  **Gestione dei dispositivi**  >  **Profilo di gestione**. Verificare che l'installazione del profilo è inclusa nell'elenco e controllare le restrizioni dei criteri iOS e le app installate. La visualizzazione delle restrizioni dei criteri e delle app nel dispositivo può impiegare fino a 10 minuti.

    5. Distribuire i dispositivi. Il dispositivo iOS viene ora registrato con Intune e gestito.


## <a name="how-users-install-and-use-the-company-portal-on-their-devices"></a>In che modo gli utenti installano e usano il portale aziendale sui dispositivi

I dispositivi configurati con affinità utente possono installare ed eseguire l'app del portale aziendale per scaricare le app e gestire i dispositivi. Dopo aver ricevuto i dispositivi, gli utenti devono eseguire alcuni passaggi supplementari descritti di seguito per completare l'Assistente configurazione e installare l'app Portale aziendale.
