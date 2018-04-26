---
title: Impostare un servizio di gestione delle spese per telecomunicazioni
titleSuffix: Microsoft Intune
description: Integrare Intune con il servizio di gestione delle spese per telecomunicazioni Saaswedo.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ca0c0151bd90051d287c76f5d264030112b85cfd
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configurare un servizio di gestione delle spese per telecomunicazioni in Intune
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune consente di gestire le spese per telecomunicazioni associate all'uso di dati nei dispositivi mobili di proprietà dell'azienda. Per abilitare questa funzionalità Intune è integrato con la soluzione di gestione delle spese per telecomunicazioni Datalert, creata dallo sviluppatore software di terze parti Saaswedo. Datalert è un software per la gestione delle spese per telecomunicazioni in tempo reale che consente di gestire l'uso dei dati delle telecomunicazioni. Consente di evitare eccedenze costose e impreviste di dati e roaming nei dispositivi gestiti da Intune.

L'integrazione di Intune con Datalert consente di impostare centralmente, monitorare e limitare il consumo dei dati, sia nazionale che in roaming. Gli avvisi automatizzati vengono attivati quando i limiti superano le soglie definite. È possibile configurare il servizio per applicare azioni diverse a singoli utenti o gruppi di utenti finali, inclusa la disabilitazione del roaming, in caso di superamento della soglia. I report che forniscono il consumo dei dati e le informazioni di monitoraggio sono disponibili dalla console di gestione Datalert.

Il diagramma seguente visualizza l'integrazione tra Intune e Datalert.

  ![Diagramma dell'integrazione tra Intune e Datalert](./media/tem-datalert-intune-solution-diagram.png)

Prima di poter usare il servizio Datalert con Intune, è necessario configurare le impostazioni nella console di Datalert e in Intune. La connessione deve essere attivata per il servizio Datalert e per Intune. Se è abilitato il lato Datalert della connessione, ma non il lato Intune, Intune riceve la comunicazione, ma la ignora.

## <a name="supported-platforms"></a>Piattaforme supportate

- Samsung KNOX
- iOS 8.0 e versioni successive

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione a Microsoft Intune e accesso al portale di Azure.
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

6. Nella pagina di autenticazione Microsoft selezionare **Accetta**. Si viene reindirizzati a una pagina di ringraziamento Datalert, che si chiude dopo pochi secondi. Datalert convalida la connessione e visualizza segni di spunta verdi accanto all'elenco di elementi convalidati. Se la convalida non riesce, appare un messaggio in rosso ed è necessario contattare il supporto tecnico Datalert per l'assistenza.

    La schermata seguente visualizza i segni di spunta verdi che appaiono quando la connessione ha esito positivo.

   ![Pagina Datalert con connessione riuscita](./media/tem-mdm-configuration-mdm-server-page.png)

### <a name="step-2-check-that-the-telecom-expense-management-feature-is-active-in-intune"></a>Passaggio 2: Verificare che la funzionalità di gestione delle spese per telecomunicazioni sia attiva in Intune

Dopo il completamento del passaggio 1 sopra descritto, la connessione deve essere abilitata automaticamente e nel portale di Azure lo stato della connessione deve essere **Attiva**. Questa procedura visualizza come verificare che lo stato sia **Attiva**.

1. Accedere al [portale Azure](https://portal.azure.com).

2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.

3. Nel riquadro **Intune** scegliere **Configurazione del dispositivo**.

4. Nel riquadro **Configurazione dispositivo** scegliere **Installazione** > **Gestione delle spese per telecomunicazioni**.

   Trovare l'impostazione **Attiva** per lo stato della connessione nella parte superiore della pagina.

   ![Pagina di Intune con stato Attiva per la connessione Datalert](./media/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-corporate-enrolled-devices"></a>Passaggio 3: Distribuire l'app Datalert nei dispositivi aziendali registrati

Per garantire che vengano raccolte le informazioni sull'uso dei dati solo dalle linee di proprietà dell'azienda, è necessario eseguire due operazioni:
- creare categorie di dispositivi in Intune
- scegliere come destinazione l'app Datalert solo per i telefoni aziendali.

#### <a name="define-device-categories-and-device-groups-mapped-to-the-categories"></a>Definire categorie di dispositivi e gruppi di dispositivi mappati alle categorie

In base alle esigenze dell'organizzazione, creare almeno due categorie di dispositivi, ad esempio Aziendale e Personale. Quindi, creare gruppi di dispositivi dinamici per ogni categoria. È possibile creare altre categorie per l'organizzazione, in base alle esigenze.

Queste categorie verranno visualizzate dagli utenti durante la registrazione. A seconda della categoria scelta dall'utente, il dispositivo verrà associato al gruppo di dispositivi corrispondente. Per la procedura di creazione di categorie di dispositivi, vedere [Eseguire il mapping di dispositivi a gruppi](device-group-mapping.md).

  ![Schermata del riquadro Aggiungi criteri](./media/tem-dynamic-membership-rules.png)

#### <a name="create-the-datalert-app-in-intune"></a>Creare l'app Datalert in Intune

Seguire questa procedura per creare l'app Datalert in Intune per ogni piattaforma. Gli esempi della procedura usano il sistema operativo iOS.

1. Nel riquadro **Intune** del [portale di Azure](https://portal.azure.com) scegliere **App per dispositivi mobili**.

2. Nel riquadro **App per dispositivi mobili** scegliere **Gestisci** > **App**.

3. Selezionare **Aggiungi** per aggiungere un'app.

4. Selezionare il tipo di app. Ad esempio, per iOS selezionare **App Store iOS**.

5. In **Cerca in App Store** cercare l'app Datalert digitando **Datalert** nella finestra di ricerca.

6. Selezionare l'app **Datalert** e scegliere **Seleziona**.

   ![Schermata del riquadro Aggiungi criteri](./media/tem-select-app-from-apple-app-store.png)

7. Completare i passaggi rimanenti per creare un'app per iOS.

   ![Schermata del riquadro Aggiungi criteri](./media/tem-steps-to-create-the-app.png)

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Assegnare l'app Datalert al gruppo dei dispositivi aziendali

1. Dal riquadro **App per dispositivi mobili - App** selezionare l'app iOS Datalert creata nel passaggio precedente.

2. Nel riquadro **App per dispositivi mobili** scegliere **Gestisci** > **Assegnazioni**.

3. Scegliere **Aggiungi gruppo** e seguire i passaggi per selezionare il gruppo di dispositivi aziendali.

4. Scegliere se l'installazione dell'app sarà obbligatoria o facoltativa per il gruppo. La schermata di esempio seguente visualizza l'installazione impostata come obbligatoria: dopo la registrazione del dispositivo, gli utenti devono installare l'app Datalert.

   ![Schermata del riquadro Aggiungi criteri](./media/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-corporate-paid-phone-lines-to-the-datalert-console"></a>Passaggio 4: Aggiungere linee telefoniche aziendali a pagamento nella console Datalert

È stata completata la configurazione delle comunicazioni tra i servizi Intune e Datalert. Ora è necessario aggiungere linee telefoniche aziendali a pagamento alla console Datalert e definire soglie e azioni in caso di violazione dei limiti d'uso del cellulare o del roaming. È possibile aggiungere linee telefoniche aziendali a pagamento alla console Datalert manualmente o fare in modo che vengano aggiunte automaticamente dopo la registrazione del dispositivo in Intune.

Per impostare questi elementi, accedere alla pagina [Datalert setup for Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (Configurazione di Datalert per Microsoft Intune) (http://www.datalert.fr/microsoft-intune/intune-setup) ed eseguire i passaggi della configurazione guidata nella scheda **Settings** (Impostazioni).

  ![Schermata del riquadro Aggiungi criteri](./media/tem-add-phone-lines-to-datalert-console.png)


Il servizio Datalert è ora attivo e avvia il monitoraggio del consumo dei dati e la disattivazione di dati cellulare e roaming sui dispositivi che superano i limiti di utilizzo configurati.

## <a name="client-enrollment-experience"></a>Esperienza di registrazione client
Per l'esperienza di registrazione client vedere quanto segue:
-   [Registrare il dispositivo iOS nella gestione delle spese per telecomunicazioni](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
-   [Registrare il dispositivo Android nella gestione delle spese per telecomunicazioni](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turning-off-the-datalert-service"></a>Disattivazione del servizio Datalert

Se si disabilita il servizio Datalert nel portale di Azure:

- Tutte le azioni che sono state applicate ai dispositivi, a causa di precedenti violazioni dei limiti di utilizzo, vengono annullate.
- Agli utenti non vengono più impediti l'accesso ai dati e il roaming.
- Intune riceve ancora i segnali provenienti dal servizio, ma li ignora.

**Per disattivare il servizio**

1. Nel riquadro **Gestione delle spese per telecomunicazioni** nel portale di Azure selezionare **Disabilita**.

2. Selezionare **Salva**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Visualizzazione del consumo dei dati e dei report di roaming

A questo punto, il reporting del consumo dei dati è disponibile solo nella console di gestione Datalert di Saaswedo.

Le istruzioni che gli utenti finali devono seguire per installare l'app Datalert verranno aggiunte quanto prima.
