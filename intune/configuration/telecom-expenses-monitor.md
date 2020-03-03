---
title: Configurare un servizio di gestione delle spese per telecomunicazioni in Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: Integrare Microsoft Intune con il servizio di gestione delle spese per telecomunicazioni Saaswedo per monitorare il consumo dei dati e impostare soglie o limiti nei dispositivi Android, iOS e iPadOS.
keywords: Saaswedo
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e6c4d08d1010654a16e13981a0d3353b2418524a
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512875"
---
# <a name="set-up-a-telecom-expense-management-service-in-intune"></a>Configurare un servizio di gestione delle spese per telecomunicazioni in Intune

Con Intune è possibile gestire le spese per telecomunicazioni relative al consumo dei dati nei dispositivi mobili di proprietà dell'organizzazione. Intune si integra con la [gestione delle spese per telecomunicazioni Datalert](http://datalert.biz/get-started) di Saaswedo. Datalert è una soluzione di gestione delle spese per telecomunicazioni in tempo reale che gestisce il consumo dei dati delle telecomunicazioni. Aiuta a evitare addebiti onerosi e imprevisti relativi al consumo di dati e al roaming per i dispositivi gestiti da Intune.

L'integrazione con Datalert consente di impostare, monitorare e applicare limiti al consumo di dati a livello nazionale e in roaming. Quando i limiti superano le soglie definite, vengono automaticamente attivati gli avvisi. È anche possibile configurare il servizio in modo da applicare azioni diverse, ad esempio la disabilitazione del roaming o il superamento della soglia, a singoli utenti o gruppi. La console di gestione di Datalert include report con il consumo dei dati e le informazioni di monitoraggio.

L'immagine seguente illustra l'integrazione tra Intune e Datalert:

  ![Diagramma dell'integrazione tra Intune e Datalert](./media/telecom-expenses-monitor/tem-datalert-intune-solution-diagram.png)

Per usare il servizio Datalert con Intune, sono disponibili alcune impostazioni di configurazione in Datalert e Intune. Questo articolo illustra come:

- Configurare le impostazioni nella console di Datalert per connettere il servizio Datalert a Intune.
- Verificare che la connessione sia attiva e abilitata in Intune.
- Usare Intune per aggiungere l'app Datalert ai dispositivi.
- Disattivare il servizio Datalert in Intune (facoltativo).

## <a name="supported-platforms"></a>Piattaforme supportate

- Android 4.4 e dispositivi più recenti che supportano Knox (Samsung)

  Le [versioni di Android che supportano Knox](https://seap.samsung.com/faq/what-versions-android-support-knox-standard-and-knox-premium-sdks-0) (viene aperto il sito Web Samsung) includono l'elenco delle versioni supportate di Knox.

- iOS 8.0 e versioni successive
- iPadOS 13.0 e versioni successive

## <a name="prerequisites"></a>Prerequisiti

- Sottoscrizione a Microsoft Intune e accesso all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)
- Sottoscrizione a [Datalert](http://www.datalert.biz/) (viene aperto il sito Web di Datalert)

## <a name="telecom-expense-management-providers"></a>Provider di gestione delle spese per telecomunicazioni

Intune si integra con i provider di gestione delle spese per telecomunicazioni seguenti:

- [Servizio di gestione delle spese per telecomunicazioni Saaswedo Datalert](http://www.datalert.biz/) (viene aperto il sito Web di Datalert)

## <a name="deploy-the-intune-and-datalert-solution"></a>Distribuire la soluzione Intune e Datalert

### <a name="step-1-connect-the-datalert-service-to-intune"></a>Passaggio 1: Connettere il servizio Datalert a Intune

1. Accedere alla console di gestione di Datalert con credenziali di amministratore.

2. Nella console passare alla scheda **Settings** (Impostazioni) > **MDM configuration** (Configurazione MDM).

3. Selezionare **Unblock** (Sblocca). **Unblock** consente di modificare o aggiornare le impostazioni disponibili nella pagina.

4. In **Intune / Datalert Connection** (Intune/Connessione Datalert) > **Server MDM** selezionare **Microsoft Intune**.

5. Per **Azure AD domain** (Dominio di Azure AD) immettere l'ID tenant di Azure. Selezionare **Connection** (Connessione).

    Quando si seleziona **Connection** (Connessione), il servizio Datalert si connette a Intune. Verifica che non siano presenti altre connessioni Datalert. Dopo qualche istante viene visualizzata una pagina di accesso Microsoft seguita dall'autenticazione di Azure per Datalert.

6. Nella pagina di autenticazione Microsoft selezionare **Accetta**.

    Si verrà reindirizzati a una pagina di **ringraziamento** di Datalert che si chiude dopo qualche istante. Datalert convalida la connessione e visualizza segni di spunta verdi accanto agli elementi convalidati. Se la convalida ha esito negativo, viene visualizzato un messaggio in rosso. Contattare il supporto Datalert per assistenza.

    L'immagine seguente illustra i segni di spunta verdi visualizzati quando la connessione viene stabilita correttamente:

      ![Pagina Datalert con connessione riuscita](./media/telecom-expenses-monitor/tem-datalert-connection.png)

7. In **Datalert App / ADAL Consent** (App Datalert/Consenso ADAL) impostare l'opzione su **On**. Nella pagina di autenticazione Microsoft selezionare **Accetta**.

    Si verrà reindirizzati a una pagina di **ringraziamento** di Datalert che si chiude dopo qualche istante. Datalert convalida la connessione e visualizza segni di spunta verdi accanto agli elementi convalidati. Se la convalida ha esito negativo, viene visualizzato un messaggio in rosso. Contattare il supporto Datalert per assistenza.

    L'immagine seguente illustra i segni di spunta verdi visualizzati quando la connessione viene stabilita correttamente:

      ![Pagina Datalert con connessione riuscita](./media/telecom-expenses-monitor/tem-datalert-adal-consent.png)

8. In **MDM Profiles management (optional)** (Gestione profili MDM, facoltativa) impostare l'opzione su **On**. Questa impostazione consente a Datalert di leggere i profili disponibili in Intune per facilitare la configurazione dei criteri. 

    Nella pagina di autenticazione Microsoft selezionare **Accetta**.

    Si verrà reindirizzati a una pagina di **ringraziamento** di Datalert che si chiude dopo qualche istante. Datalert convalida la connessione e visualizza segni di spunta verdi accanto agli elementi convalidati. Se la convalida ha esito negativo, viene visualizzato un messaggio in rosso. Contattare il supporto Datalert per assistenza.

    L'immagine seguente illustra i segni di spunta verdi visualizzati quando la connessione viene stabilita correttamente:

   ![Pagina Datalert con connessione riuscita](./media/telecom-expenses-monitor/tem-datalert-mdm-profiles.png)

### <a name="step-2-confirm-telecom-expense-management-is-active-in-intune"></a>Passaggio 2: Verificare che la gestione delle spese per telecomunicazioni sia attiva in Intune

Dopo il completamento del passaggio 1, la connessione è automaticamente abilitata. In Intune lo stato della connessione indica **Attiva**. Per verificare che lo stato sia attivo, seguire questa procedura:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selezionare **Amministrazione del tenant** > **Connettori e token** > **Gestione delle spese per telecomunicazioni**. Individuare lo stato di connessione **Attiva**:

   ![Pagina di Intune con stato Attiva per la connessione Datalert](./media/telecom-expenses-monitor/tem-azure-portal-enable-service.png)

### <a name="step-3-deploy-the-datalert-app-to-devices"></a>Passaggio 3: Distribuire l'app Datalert ai dispositivi

Per garantire che venga raccolto il consumo dei dati relativo soltanto alle linee di proprietà dell'organizzazione, assicurarsi di:

- Creare categorie di dispositivi in Intune.
- Assegnare l'app Datalert solo ai telefoni dell'organizzazione.

Questa sezione elenca questi passaggi.

#### <a name="create-device-categories-and-device-groups-mapped-to-your-categories"></a>Creare categorie di dispositivi e gruppi di dispositivi mappati alle categorie

In base alle esigenze dell'organizzazione, creare almeno due categorie di dispositivi, ad esempio Aziendale e Personale. Quindi, creare gruppi di dispositivi dinamici per ogni categoria. È possibile creare altre categorie per l'organizzazione, in base alle esigenze.

Per creare categorie di dispositivi in Intune, vedere [Eseguire il mapping a gruppi](../enrollment/device-group-mapping.md).

Gli utenti visualizzano queste categorie durante la registrazione ([Registrare dispositivi Android](../enrollment/android-enroll.md)). A seconda della categoria scelta dall'utente, il dispositivo registrato viene aggiunto al gruppo di dispositivi corrispondente.

  ![Schermata del riquadro Aggiungi criteri](./media/telecom-expenses-monitor/tem-dynamic-membership-rules.png)

#### <a name="add-the-datalert-app-to-intune"></a>Aggiungere l'app Datalert a Intune

La procedura descritta di seguito consente di aggiungere l'app Datalert. Viene usato come esempio iOS/iPadOS. [Aggiungere app](../apps/apps-add.md) e [Usare i tag di ambito](../fundamentals/scope-tags.md) includono informazioni più specifiche su questi passaggi.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **App** > **Tutte le app** > **Aggiungi**.

2. Selezionare un valore nel campo **Tipo di app**. Per iOS/iPadOS, ad esempio, selezionare **App dello Store - iOS/iPadOS**.

3. In **Cerca in App Store** digitare **Datalert** per trovare l'app Datalert.

4. Scegliere l'app **Datalert** > **Seleziona**:

   ![Aggiungere l'app Datalert dall'App Store alle app client di Intune](./media/telecom-expenses-monitor/tem-select-app-from-apple-app-store.png)

5. Immettere eventuali proprietà aggiuntive, ad esempio informazioni sull'app e tag di ambito:

   ![Immettere le proprietà dell'app, ad esempio il nome e la descrizione, scegliere il sistema operativo e altre impostazioni per l'app in Intune](./media/telecom-expenses-monitor/tem-steps-to-create-the-app.png)

6. Selezionare **OK** > **Aggiungi** per salvare le modifiche. L'app Datalert viene visualizzata nell'elenco.

#### <a name="assign-the-datalert-app-to-the-corporate-device-group"></a>Assegnare l'app Datalert al gruppo dei dispositivi aziendali

1. In **App** > **Tutte le app** selezionare l'app Datalert aggiunta nel passaggio precedente.

2. Selezionare **Assegnazioni** > **Aggiungi gruppo**. Scegliere come viene assegnata l'app. [Assegnare app ai gruppi in Intune](../apps/apps-deploy.md) include altri dettagli relativi a queste impostazioni.

    In questi passaggi si sceglierà se l'installazione dell'app sarà obbligatoria o facoltativa per il gruppo. Nell'esempio riportato di seguito l'installazione è obbligatoria. Se obbligatoria, gli utenti devono installare l'app Datalert dopo la registrazione del dispositivo.

   ![Schermata del riquadro Aggiungi criteri](./media/telecom-expenses-monitor/tem-assign-datalert-app-to-device-group.png)

### <a name="step-4-add-organization-phone-lines-to-the-datalert-console"></a>Passaggio 4: Aggiungere le linee telefoniche dell'organizzazione alla console di Datalert

La comunicazione tra i servizi Intune e Datalert è stata ora configurata. A questo punto, aggiungere le linee telefoniche a pagamento dell'organizzazione alla console di Datalert. Immettere inoltre soglie e azioni per eventuali violazioni di utilizzo della rete dati o del roaming. È possibile aggiungere manualmente le linee telefoniche aziendali a pagamento alla console di Datalert oppure aggiungerle automaticamente dopo la registrazione del dispositivo in Intune.

Per impostare questi elementi, visitare [Datalert setup for Microsoft Intune](http://www.datalert.fr/microsoft-intune/intune-setup) (Configurazione di Datalert per Microsoft Intune) nel sito Web di Datalert. Nella scheda **Settings** (Impostazioni) seguire i passaggi della configurazione guidata.

  ![Schermata del riquadro Aggiungi criteri](./media/telecom-expenses-monitor/tem-add-phone-lines-to-datalert-console.png)

Il servizio Datalert è ora attivo. Avvia il monitoraggio del consumo dei dati e la disabilitazione della rete dati e del roaming dei dati nei dispositivi che superano i limiti di utilizzo configurati.

## <a name="end-user-enrollment"></a>Registrazione dell'utente finale

Per l'esperienza utente finale possono risultare utili gli articoli seguenti:

- [Registrare il dispositivo iOS/iPadOS nella gestione delle spese per telecomunicazioni](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-ios)
- [Registrare il dispositivo Android nella gestione delle spese per telecomunicazioni](https://docs.microsoft.com/intune-user-help/enroll-your-device-with-telecom-expense-management-android)

## <a name="turn-off-the-datalert-service"></a>Disattivare il servizio Datalert

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) selezionare **Amministrazione del tenant** > **Connettori e token** > **Gestione delle spese per telecomunicazioni**.
2. Impostare **Abilita il servizio di gestione delle spese per telecomunicazioni e blocca la rete dati o il roaming dei dati nei dispositivi che hanno superato le quote di utilizzo configurate** su **Disabilita**.
3. **Salvare** le modifiche.

> [!IMPORTANT]
> Se si disabilita il servizio Datalert in Intune:
>
> - Tutte le azioni applicate ai dispositivi a causa di precedenti violazioni dei limiti di utilizzo vengono annullate.
> - Agli utenti non vengono più impediti l'accesso ai dati e il roaming.
> - Intune continua a ricevere i segnali provenienti dal servizio, ma questi vengono ignorati da Intune.

## <a name="next-steps"></a>Passaggi successivi

La creazione di report relativi al consumo di dati è disponibile nella console di gestione di Saaswedo Datalert.
