---
title: Impostare un servizio di gestione delle spese per telecomunicazioni
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: configurare il servizio di gestione delle spese per telecomunicazioni Saaswedo per l&quot;integrazione con Intune.'
keywords: Saaswedo
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: a981b0253f56d66292ce77639faf4beba8832a9e
ms.openlocfilehash: b0d0ad102942c65ac3988ea4659b34b397289126
ms.lasthandoff: 04/19/2017

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>Impostare un servizio di gestione delle spese per telecomunicazioni nell'anteprima di Intune in Azure
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Intune consente di gestire le spese per telecomunicazioni associate all'uso di dati nei dispositivi mobili di proprietà dell'azienda. Per abilitare questa funzionalità Intune è integrato con la soluzione di gestione delle spese per telecomunicazioni Datalert, creata dallo sviluppatore software di terze parti Saaswedo. Datalert è un software di gestione delle spese per telecomunicazioni in tempo reale, che consente di gestire il consumo dei dati per le telecomunicazioni e di evitare eccedenze impreviste e costose relative a dati e roaming per i dispositivi gestiti da Intune.

L'integrazione di Intune con Datalert consente di impostare centralmente, monitorare e limitare il consumo dei dati, sia nazionale che in roaming, tramite avvisi automatizzati generati ogni volta che i limiti superano le soglie definite. È possibile configurare il servizio per applicare azioni diverse a utenti individuali o gruppi di utenti finali, inclusa la disabilitazione del roaming, in caso di superamento della soglia. I report che forniscono il consumo dei dati e le informazioni di monitoraggio sono disponibili dalla console di gestione Datalert.

Il diagramma seguente visualizza l'integrazione tra Intune e Datalert.

  ![Diagramma dell'integrazione tra Intune e Datalert](../media/tem-datalert-intune-solution-diagram.png)

Prima di poter usare il servizio Datalert con Intune, è necessario configurare le impostazioni nella console di Datalert e in Intune. La connessione deve essere attivata per il servizio Datalert e per Intune. Se è abilitato il lato Datalert della connessione, ma non il lato Intune, Intune riceve la comunicazione, ma la ignora.

## <a name="supported-platforms"></a>Piattaforme supportate

- Samsung KNOX
- iOS 8.0 e versioni successive

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione a Microsoft Intune e accesso al portale di Azure, che attualmente è disponibile in anteprima pubblica.
- Disporre di una sottoscrizione al servizio di gestione delle spese per telecomunicazioni Datalert.

## <a name="list-of-telecom-expense-management-providers"></a>Elenco di provider di gestione delle spese per telecomunicazioni

Intune attualmente si integra con i provider di gestione delle spese per telecomunicazioni seguenti:

[Servizio di gestione delle spese per telecomunicazioni Saaswedo Datalert](http://www.datalert.biz/)

## <a name="deploy-the-intune-and-datalert-integrated-solution"></a>Distribuire la soluzione integrata Intune e Datalert

Prima di iniziare, assicurarsi di avere già una sottoscrizione a Intune e al servizio di gestione delle spese per telecomunicazioni Datalert.

### <a name="step-1-connect-the-datalert-service-to-microsoft-intune"></a>Passaggio 1: Connettere il servizio Datalert a Microsoft Intune

1. Accedere alla console di gestione Datalert con le credenziali di amministratore.

2. Nella console di gestione Datalert, accedere alla scheda **Settings** (Impostazioni), quindi alla sezione **MDM configuration** (Configurazione MDM).

3. Selezionare **Unblock** (Sblocca) per immettere le impostazioni nella pagina.

4. Per **Server MDM** (MDM del server) scegliere **Microsoft Intune**.

5. Per **Azure AD domain** (Dominio di Azure AD) immettere l'ID tenant di Azure e quindi selezionare il pulsante **Connection** (Connessione).

    Quando si seleziona **Connessione**, il servizio Datalert esegue un controllo con Intune per garantire che non siano presenti connessioni Datalert preesistenti con Intune. Dopo alcuni secondi, viene visualizzata una pagina di accesso Microsoft, seguita dalla pagina di autenticazione Datalert per Azure.

6. Nella pagina di autenticazione Microsoft selezionare **Accetta**. Si viene reindirizzati a una pagina di ringraziamento Datalert, che si chiude dopo pochi secondi. Datalert convalida la connessione e visualizza segni di spunta verdi accanto all'elenco di elementi convalidati. Se la convalida ha esito negativo, viene visualizzato un messaggio in rosso. In questo caso, contattare il supporto Datalert per assistenza.

    La schermata seguente visualizza i segni di spunta verdi che appaiono quando la connessione ha esito positivo.

  ![Pagina Datalert con connessione riuscita](../media/tem-mdm-configuration-mdm-server-page.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Passaggio 2: Verificare che la funzionalità di gestione delle spese per telecomunicazioni sia attiva in Intune

Dopo il completamento del passaggio 1 sopra descritto, la connessione deve essere abilitata automaticamente e nel portale di Azure lo stato della connessione deve essere **Attiva**. Questa procedura visualizza come verificare che lo stato sia **Attiva**.

1. Accedere al portale di Azure.

2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.

3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.

4. Nel pannello **Configurazione del dispositivo** scegliere **Installazione** > **Gestione delle spese per telecomunicazioni**.

   Trovare l'impostazione **Attiva** per lo stato della connessione nella parte superiore della pagina.

  ![Portale di Azure con stato Attiva per la connessione Datalert](../media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Passaggio 3: Distribuire l'app Datalert nei dispositivi aziendali registrati

Per garantire che venga registrato solo l'uso di dati delle linee di proprietà dell'azienda è necessario creare categorie di dispositivi in Intune, quindi configurare l'app Datalert solo per i telefoni aziendali. Completare i passaggi delle seguenti sottosezioni.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Definire categorie di dispositivi e gruppi di dispositivi mappati alle categorie

A seconda delle esigenze sarà necessario creare almeno due categorie di dispositivi (ad esempio Aziendale e Personale) e creare gruppi di dispositivi dinamici per ogni categoria. È possibile creare altre categorie per l'organizzazione, in base alle esigenze.

Queste categorie verranno visualizzate dagli utenti durante la registrazione. A seconda della categoria scelta dall'utente, il dispositivo verrà associato al gruppo di dispositivi corrispondente. Per la procedura di creazione di categorie di dispositivi, vedere [Eseguire il mapping di dispositivi a gruppi](https://docs.microsoft.com/intune-azure/enroll-devices/how-to-use-device-group-mapping).

  ![Schermata del pannello Aggiungi criteri](../media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Creare l'app Datalert in Intune

Seguire questa procedura per creare l'app Datalert in Intune per ogni piattaforma. Gli esempi della procedura usano il sistema operativo iOS.

1. Nel pannello **Intune** del portale di Azure scegliere **Gestisci le app**.

2. Nel pannello **Gestisci le app** scegliere **Gestisci** > **App**.

3. Selezionare **Aggiungi** per aggiungere un'app.

4. Selezionare il tipo di app. Ad esempio, per iOS selezionare **App Store iOS**.

5. In **Cerca in App Store** cercare l'app Datalert digitando **Datalert** nella finestra di ricerca.

6. Selezionare l'app **Datalert** e selezionare **OK**.

  ![Schermata del pannello Aggiungi criteri](../media/tem-select-app-from-apple-app-store.png)

7. Completare i passaggi rimanenti per creare un'app per iOS.

  ![Schermata del pannello Aggiungi criteri](../media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Assegnare l'app Datalert al gruppo dei dispositivi aziendali

1. Selezionare l'app iOS Datalert creata nel passaggio precedente.

2. Nel pannello **App** andare a **Gestisci** > **Assegnazioni**.

3. Scegliere **Selezionare i gruppi** e seguire i passaggi per selezionare il gruppo dei dispositivi aziendali.

4. Scegliere se l'installazione dell'app sarà obbligatoria o facoltativa per il gruppo. La schermata di esempio seguente visualizza l'installazione impostata come obbligatoria: dopo la registrazione del dispositivo, gli utenti devono installare l'app Datalert.

  ![Schermata del pannello Aggiungi criteri](../media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Passaggio 4: Aggiungere linee telefoniche aziendali a pagamento nella console Datalert

È stata completata la configurazione delle comunicazioni tra i servizi Intune e Datalert. Ora è necessario aggiungere linee telefoniche aziendali a pagamento alla console Datalert e definire soglie e azioni in caso di violazione dei limiti d'uso del cellulare o del roaming. È possibile aggiungere linee telefoniche aziendali a pagamento alla console Datalert manualmente oppure impostare l'aggiunta automatica delle linee dopo la registrazione del dispositivo in Intune.

Per impostare questi elementi, accedere alla [pagina di configurazione di Datalert per Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (http://www.datalert.fr/microsoft-intune/intune-setup) ed eseguire i passaggi della configurazione guidata elencati nella scheda **Settings** (Impostazioni).

  ![Schermata del pannello Aggiungi criteri](../media/tem-add-phone-lines-to-datalert-console.png)


Il servizio Datalert è ora attivo e avvia il monitoraggio del consumo dei dati e la disattivazione di dati cellulare e roaming sui dispositivi che superano i limiti di utilizzo configurati.

## <a name="client-enrollment-experience"></a>Esperienza di registrazione client
Per l'esperienza di registrazione client vedere quanto segue:
-    [Registrare il dispositivo iOS nella gestione delle spese per telecomunicazioni](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-    [Registrare il dispositivo Android nella gestione delle spese per telecomunicazioni](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Disattivazione del servizio Datalert

Se si disabilita il servizio Datalert nel portale di Azure:

- Tutte le azioni che sono state applicate ai dispositivi, a causa di precedenti violazioni dei limiti di utilizzo, vengono annullate.
- Agli utenti non vengono più impediti l'accesso ai dati e il roaming.
- Intune riceve ancora i segnali provenienti dal servizio, ma li ignora.

**Per disattivare il servizio**

1. Nel pannello **Gestione delle spese per telecomunicazioni** nel portale di Azure selezionare **Disabilita**.

2. Selezionare **Salva**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Visualizzazione del consumo dei dati e dei report di roaming

A questo punto, il reporting del consumo dei dati è disponibile solo nella console di gestione Datalert di Saaswedo.

Le istruzioni che gli utenti finali devono seguire per installare l'app Datalert verranno aggiunte quanto prima.

