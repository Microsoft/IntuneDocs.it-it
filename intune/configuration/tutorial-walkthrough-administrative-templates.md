---
title: Procedura dettagliata - Creare un modello amministrativo in Microsoft Intune - Azure | Microsoft Docs
description: Questa esercitazione o procedura dettagliata usa Microsoft Intune per configurare i modelli ADMX di Office, Windows e Microsoft Edge nei dispositivi con Windows 10 e più recenti.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: ''
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a96f291203e1513ab89196b26a7802856f90e048
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77688090"
---
# <a name="tutorial-use-the-cloud-to-configure-group-policy-on-windows-10-devices-with-admx-templates-and-microsoft-intune"></a>Esercitazione: Usare il cloud per configurare Criteri di gruppo nei dispositivi Windows 10 con modelli ADMX e Microsoft Intune

> [!NOTE]
> Questa esercitazione è stata creata come workshop tecnico per Microsoft Ignite. Include più prerequisiti rispetto alle esercitazioni tipiche, in quanto confronta l'uso e la configurazione di criteri ADMX in Intune e in locale.

I modelli amministrativi di Criteri di gruppo, noti anche come modelli ADMX, includono le impostazioni che è possibile configurare nei dispositivi Windows 10, inclusi i PC. Le impostazioni per i modelli ADMX sono disponibili per diversi servizi. Queste impostazioni vengono usate dai provider di gestione di dispositivi mobili (MDM), tra cui Microsoft Intune. Ad esempio, è possibile attivare Idee per progetti in PowerPoint, impostare una pagina iniziale in Microsoft Edge, bloccare i controlli ActiveX in Internet Explorer e altro ancora.

Sono disponibili modelli ADMX per i servizi seguenti:

- **Microsoft Edge**: scaricare il [file dei criteri di Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/enterprise).
- **Office**: scaricare in [Office 365 ProPlus, Office 2019 e Office 2016](https://www.microsoft.com/download/details.aspx?id=49030).
- **Windows**: inclusi nel sistema operativo Windows 10.

Per altre informazioni sui criteri ADMX, vedere [Informazioni sui criteri supportati da ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies).

In Microsoft Intune, questi modelli sono inclusi nel servizio Intune e sono disponibili come profili di tipo **Modelli amministrativi**. In questo profilo vengono configurate le impostazioni da includere e quindi il profilo viene assegnato ai dispositivi.

In questa esercitazione:

> [!div class="checklist"]
> * Introduzione all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
> * Creare gruppi di utenti e creare gruppi di dispositivi.
> * Confrontare le impostazioni in Intune con le impostazioni ADMX locali.
> * Creare modelli amministrativi diversi e configurare le impostazioni destinate ai diversi gruppi.

Al termine di questo lab saranno disponibili le competenze per iniziare a usare Intune e Microsoft 365 per gestire gli utenti e distribuire modelli amministrativi.

Questa funzionalità si applica a:

- Windows 10 versione 1703 e successive

## <a name="prerequisites"></a>Prerequisiti

- Una sottoscrizione Microsoft 365 E3 o E5, che include Intune e Azure Active Directory (AD) Premium. Se non si ha una sottoscrizione E3 o E5, provare la [versione di valutazione gratuita](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365?view=o365-worldwide).

  Per altre informazioni su ciò che si ottiene con le diverse licenze di Microsoft 365, vedere [Trasforma la tua azienda con Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans).

- Microsoft Intune viene configurato come **autorità MDM Intune**. Per altre informazioni, vedere [Impostare l'autorità di gestione dei dispositivi mobili](../fundamentals/mdm-authority-set.md).

  > [!div class="mx-imgBorder"]
  > ![Impostare l'autorità MDM su Microsoft Intune nello stato del tenant](./media/tutorial-walkthrough-administrative-templates/tenant-status.png)

- In un controller di dominio di Active Directory locale (DC):

  1. Copiare i modelli di Office e Microsoft Edge seguenti nell'[archivio centrale (cartella SYSVOL)](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra):

      - [Modelli amministrativi di Office](https://www.microsoft.com/download/details.aspx?id=49030)
      - [Modelli amministrativi di Microsoft Edge > File dei criteri](https://www.microsoftedgeinsider.com/en-us/enterprise)

  2. Creare Criteri di gruppo per eseguire il push di questi modelli in un computer amministratore di Windows 10 Enterprise nello stesso dominio del controller di dominio. In questa esercitazione:

      - I Criteri di gruppo creati con questi modelli sono denominati **OfficeandEdge**. Questo sarà il nome visualizzato nelle immagini.
      - Il computer amministratore di Windows 10 Enterprise usato è denominato **computer Admin**.

      In alcune organizzazioni, un amministratore di dominio ha due account, un account di lavoro di dominio tipico e un account amministratore di dominio diverso usato solo per le attività di amministratore di dominio, ad esempio Criteri di gruppo.

      Lo scopo di questo **computer Admin** è consentire agli amministratori di eseguire l'accesso con il proprio account amministratore di dominio e accedere agli strumenti progettati per la gestione di Criteri di gruppo.

- In questo **computer Admin**:

  - Accedere con un account amministratore di dominio.

  - Installare **Strumenti di amministrazione remota del server: Strumenti per Gestione Criteri di gruppo**:

    1. Aprire l'app **Impostazioni** > **App** > **Funzionalità facoltative** > **Aggiungi una funzionalità**.
    2. Selezionare **Strumenti di amministrazione remota del server: Strumenti per Gestione Criteri di gruppo** > **Installa**.

        Attendere mentre Windows installa la funzionalità. Al termine, la funzionalità sarà visualizzata nell'app **Strumenti di amministrazione di Windows**.

        > [!div class="mx-imgBorder"]
        > ![App Strumenti di amministrazione di Windows, tra cui l'app Gestione Criteri di gruppo](./media/tutorial-walkthrough-administrative-templates/windows-administrative-tools-app.png)

  - Assicurarsi di avere accesso a Internet e i diritti di amministratore per la sottoscrizione di Microsoft 365, che include l'interfaccia di amministrazione di Endpoint Manager.

## <a name="open-the-endpoint-manager-admin-center"></a>Aprire l'interfaccia di amministrazione di Microsoft Endpoint Manager

1. Aprire un Web browser Chromium, ad esempio Microsoft Edge versione 77 e successive.
2. Passare all'[interfaccia di amministrazione di Microsoft Endpoint Manage](https://go.microsoft.com/fwlink/?linkid=2109431) (https://devicemanagement.microsoft.com). Accedere con l'account seguente:

    **Utente**: immettere l'account amministratore della sottoscrizione tenant di Microsoft 365.  
    **Password**: immettere la password.

Questa interfaccia di amministrazione è dedicata alla gestione dei dispositivi e include i servizi di Azure, come Azure AD e Intune. Anche se non vengono visualizzati i nomi **Azure Active Directory** e **Intune**, questi servizi sono in effetti in uso.

È anche possibile aprire l'interfaccia di amministrazione di Endpoint Manager dall'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com):

1. Passare a [https://admin.microsoft.com](https://admin.microsoft.com).
2. Accedere con l'account amministratore della sottoscrizione tenant di Microsoft 365.
3. In **Interfacce di amministrazione** selezionare **Tutte le interfacce di amministrazione** > **Endpoint management** (Gestione endpoint). Verrà aperta l'interfaccia di amministrazione di Endpoint Manager.

    > [!div class="mx-imgBorder"]
    > ![Vedere tutte le interfacce di amministrazione nell'interfaccia di amministrazione di Microsoft 365](./media/tutorial-walkthrough-administrative-templates/microsoft365-admin-centers.png)

## <a name="create-groups-and-add-users"></a>Creare gruppi e aggiungere utenti

I criteri locali vengono applicati nell'ordine LSDOU: locale, sito, dominio e unità organizzativa (OU). In questa gerarchia, i criteri delle unità organizzative sovrascrivono i criteri locali, i criteri di dominio sovrascrivono i criteri del sito e così via.

In Intune i criteri vengono applicati agli utenti e ai gruppi creati. Non esiste una gerarchia. Se due criteri aggiornano la stessa impostazione, l'impostazione viene visualizzata come conflitto. Se due criteri di conformità sono in conflitto, viene applicato il criterio più restrittivo. Se due profili di configurazione sono in conflitto, l'impostazione non viene applicata. Per altre informazioni, vedere [Domande frequenti, problemi e soluzioni con i criteri e i profili dei dispositivi](device-profile-troubleshoot.md#if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied).

Nei passaggi successivi verranno creati gruppi di sicurezza e verranno aggiunti utenti ai gruppi. È possibile aggiungere un utente a più gruppi. Ad esempio, è normale per un utente avere più dispositivi, ad esempio Surface Pro per il lavoro e un dispositivo mobile Android per uso personale. È anche normale che un utente acceda alle risorse aziendali da più dispositivi.

1. Nell'interfaccia di amministrazione di Endpoint Manager selezionare **Gruppi** > **Nuovo gruppo**.

2. Immettere le impostazioni seguenti:

    - **Tipo di gruppo**: selezionare **Sicurezza**.
    - **Nome gruppo**: immettere **Tutti i dispositivi Windows 10 per studenti**.
    - **Tipo di appartenenza**: selezionare **Assegnati**.

3. Selezionare **Membri** e aggiungere alcuni dispositivi.

    L'aggiunta di dispositivi è facoltativa. L'obiettivo è quello di fare pratica con la creazione dei gruppi e imparare la procedura per aggiungere i dispositivi. Se si usa questa esercitazione in un ambiente di produzione, eseguire le operazioni con la dovuta attenzione.

4. **Seleziona** > **Crea** per salvare le modifiche.

    Il gruppo non viene visualizzato? Selezionare **Aggiorna**.

5. Selezionare **Nuovo gruppo** e immettere le impostazioni seguenti:

    - **Tipo di gruppo**: selezionare **Sicurezza**.
    - **Nome gruppo**: immettere **Tutti i dispositivi Windows**.
    - **Tipo di appartenenza**: selezionare **Dispositivo dinamico**.
    - **Membri dispositivo dinamico**: configurare la query:

        - **Proprietà**: selezionare **deviceOSType**.
        - **Operator** (Operatore): selezionare **Uguale a**.
        - **Valore**: immettere **Windows**.

        1. Selezionare **Aggiungi espressione**. L'espressione viene visualizzata in **Sintassi delle regole**:

            > [!div class="mx-imgBorder"]
            > ![Creare una query dinamica e aggiungere un'espressione in un modello amministrativo di Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/dynamic-group-query.png)

            Quando gli utenti o i dispositivi soddisfano i criteri immessi, vengono aggiunti automaticamente ai gruppi dinamici. In questo esempio, i dispositivi vengono aggiunti automaticamente a questo gruppo quando il sistema operativo è Windows. Se si usa questa esercitazione in un ambiente di produzione, prestare attenzione. L'obiettivo è fare pratica con la creazione di gruppi dinamici.

        2. **Salva** > **Crea** per salvare le modifiche.

6. Creare il gruppo **Tutti i docenti** con le impostazioni seguenti:

    - **Tipo di gruppo**: selezionare **Sicurezza**.
    - **Nome gruppo**: immettere **Tutti i docenti**.
    - **Tipo di appartenenza**: selezionare **Utente dinamico**.
    - **Membri utente dinamico**: configurare la query:

      - **Proprietà**: Selezionare **department**.
      - **Operator** (Operatore): selezionare **Uguale a**.
      - **Valore**: Immettere **Docenti**.

        1. Selezionare **Aggiungi espressione**. L'espressione viene visualizzata in **Sintassi delle regole**.

            Quando gli utenti o i dispositivi soddisfano i criteri immessi, vengono aggiunti automaticamente ai gruppi dinamici. In questo esempio gli utenti vengono aggiunti automaticamente a questo gruppo quando il reparto è Docenti. È possibile immettere il reparto e altre proprietà quando gli utenti vengono aggiunti alla propria organizzazione. Se si usa questa esercitazione in un ambiente di produzione, prestare attenzione. L'obiettivo è fare pratica con la creazione di gruppi dinamici.

        2. **Salva** > **Crea** per salvare le modifiche.

### <a name="talking-points"></a>Informazioni aggiuntive importanti

- I gruppi dinamici sono una funzionalità di Azure AD Premium. Se non si ha Azure AD Premium, la licenza consente di creare solo gruppi assegnati. Per altre informazioni sui gruppi dinamici, vedere:

  - [Appartenenza dinamica ai gruppi in Azure Active Directory (parte 1)](https://blogs.technet.microsoft.com/pauljones/2017/08/28/dynamic-group-membership-in-azure-active-directory-part-1/)
  - [Appartenenza dinamica ai gruppi in Azure Active Directory (parte 2)](https://blogs.technet.microsoft.com/pauljones/2017/08/29/dynamic-group-membership-in-azure-active-directory-part-2/)

- Azure AD Premium include altri servizi comunemente usati per la gestione di app e dispositivi, tra cui [autenticazione a più fattori (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks) e [accesso condizionale](https://docs.microsoft.com/azure/active-directory/conditional-access/overview).

- Molti amministratori chiedono di chiarire quando usare i gruppi di utenti e quando usare i gruppi di dispositivi. Per alcune linee guida, vedere [Gruppi di utenti e gruppi di dispositivi](device-profile-assign.md#user-groups-vs-device-groups).

- Tenere presente che un utente può appartenere a più gruppi. Prendere in considerazione alcuni degli altri gruppi di utenti e dispositivi dinamici che è possibile creare, ad esempio:

  - Tutti gli studenti
  - Tutti i dispositivi Android
  - Tutti i dispositivi iOS/iPadOS
  - Marketing
  - Risorse umane
  - Tutti i dipendenti di Charlotte
  - Tutti i dipendenti di Redmond
  - Amministratori IT della costa occidentale
  - Amministratori IT della costa orientale

Gli utenti e i gruppi creati possono essere visualizzati anche nell'[interfaccia di amministrazione di Microsoft 365](https://admin.microsoft.com), in Azure AD nel portale di Azure e in [Microsoft Intune nel portale di Azure](https://go.microsoft.com/fwlink/?linkid=2090973). È possibile creare e gestire i gruppi in tutte queste aree per la sottoscrizione tenant. **Se l'obiettivo è la gestione dei dispositivi, usare l'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)** .

### <a name="review-group-membership"></a>Verificare l'appartenenza ai gruppi

1. Nell'interfaccia di amministrazione di Endpoint Manager selezionare **Utenti** > selezionare il nome di un utente esistente.

    > [!div class="mx-imgBorder"]
    > ![Nell'interfaccia di amministrazione di Endpoint Manager selezionare Utenti](./media/tutorial-walkthrough-administrative-templates/select-users-endpoint-manager-admin-center.png)

2. Esaminare alcune delle informazioni che è possibile aggiungere o modificare. Ad esempio, vedere le proprietà che è possibile configurare, ad esempio Posizione professionale, Reparto, Città, Indirizzo ufficio e così via. È possibile usare queste proprietà nelle query dinamiche quando si creano gruppi dinamici.
3. Selezionare **Gruppi** per visualizzare l'appartenenza dell'utente. È anche possibile rimuovere l'utente da un gruppo.
4. Selezionare alcune delle altre opzioni per visualizzare altre informazioni e le operazioni possibili. Ad esempio, esaminare la licenza assegnata, i dispositivi dell'utente e altro ancora.

### <a name="what-did-i-just-do"></a>Riepilogo delle operazioni eseguite

Nell'interfaccia di amministrazione di Endpoint Manager sono stati creati nuovi gruppi di sicurezza e sono stati aggiunti utenti e dispositivi esistenti a questi gruppi. Questi gruppi verranno usati nei passaggi successivi di questa esercitazione.

## <a name="create-a-template-in-intune"></a>Creare un modello in Intune

In questa sezione viene creato un modello amministrativo in Intune, vengono esaminate alcune delle impostazioni in **Gestione Criteri di gruppo** e si confrontano le stesse impostazioni in Intune. L'obiettivo è illustrare la stessa impostazione in Criteri di gruppo e in Intune.

1. Nell'interfaccia di amministrazione di Endpoint Manager selezionare **Dispositivi** > **Profili di configurazione** > **Crea profilo**.
2. Immettere le proprietà seguenti:

    - **Nome**: immettere un nome descrittivo per il profilo. Assegnare ai profili nomi che possano essere identificati facilmente in un secondo momento. Ad esempio, immettere **Modello amministrativo - Dispositivi Windows 10 per studenti**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
    - **Tipo di profilo**: selezionare **Modelli amministrativi**.

3. Selezionare **Crea**. Nell'elenco a discesa **Selezionare una categoria** selezionare **Tutti i prodotti**. Verranno visualizzate tutte le impostazioni. In queste impostazioni si notino le proprietà seguenti:

    - Il valore **Percorso** per il criterio è lo stesso di Gestione Criteri di gruppo o GPEdit.
    - L'impostazione si applica a utenti o dispositivi.

### <a name="open-group-policy-management"></a>Aprire Gestione Criteri di gruppo

In questa sezione viene illustrato un criterio in Intune e il criterio corrispondente in Editor Gestione Criteri di gruppo.

#### <a name="compare-a-device-policy"></a>Confrontare criteri del dispositivo

1. Nel **computer Admin** aprire l'app **Gestione Criteri di gruppo**.

    Questa app viene installata con **Strumenti di amministrazione remota del server: Strumenti per Gestione Criteri di gruppo**, ovvero una funzionalità facoltativa installata in Windows. In [Prerequisiti](#prerequisites) (in questo articolo) viene descritta la procedura per installare questa funzionalità.

2. Espandere **Domini** > selezionare il dominio. Ad esempio, selezionare **contoso.net**.
3. Fare clic con il pulsante destro del mouse sul criterio **OfficeandEdge** > **Modifica**. Verrà aperta l'app Editor Gestione Criteri di gruppo.

    > [!div class="mx-imgBorder"]
    > ![Fare clic con il pulsante destro del mouse sui Criteri di gruppo ADMX di Office e Edge e scegliere Modifica](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management.png)

    **OfficeandEdge** sono Criteri di gruppo che includono i modelli ADMX di Office e Microsoft Edge. Questi criteri sono descritti in [Prerequisiti](#prerequisites) (in questo articolo).

4. Espandere **Configurazione computer** > **Criteri** > **Modelli amministrativi** > **Pannello di controllo** > **Personalizzazione**. Notare le impostazioni disponibili.

    > [!div class="mx-imgBorder"]
    > ![Espandere Configurazione computer in Editor Gestione Criteri di gruppo e passare a Personalizzazione](./media/tutorial-walkthrough-administrative-templates/open-group-policy-management-editor-admx-policy.png)

    Fare doppio clic su **Impedisci abilitazione della fotocamera nella schermata di blocco** e visualizzare le opzioni disponibili:

    > [!div class="mx-imgBorder"]
    > ![Vedere le opzioni delle impostazioni Configurazione computer in Criteri di gruppo](./media/tutorial-walkthrough-administrative-templates/prevent-enabling-lock-screen-camera-admx-policy.png)

5. Nell'interfaccia di amministrazione di gestione dei dispositivi passare al modello **Modello amministrativo - Dispositivi Windows 10 per studenti**.
6. Selezionare **Tutti i prodotti** nell'elenco a discesa e cercare **Personalizzazione**:

    > [!div class="mx-imgBorder"]
    > ![Cercare Personalizzazione nel modello amministrativo in Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/search-personalization-administrative-template.png)

    Notare le impostazioni disponibili.

    Il tipo di impostazione è **Dispositivo** e il percorso è **\Pannello di controllo\Personalizzazione**. Questo percorso è simile a quello appena visto in Editor Gestione Criteri di gruppo. Aprendo l'impostazione si vedranno le stesse opzioni **Non configurata**, **Attivata** e **Disattivata** disponibili in Editor Gestione Criteri di gruppo.

#### <a name="compare-a-user-policy"></a>Confrontare un criterio utente

1. Nel modello amministrativo cercare **inprivate browsing**. Si noti il percorso e che l'impostazione si applica a utenti e dispositivi.

2. In **Editor Gestione Criteri di gruppo** trovare le impostazioni utente e dispositivo corrispondenti:

    - Dispositivo: espandere **Configurazione computer** > **Criteri** > **Modelli amministrativi** > **Componenti di Windows** > **Internet Explorer** > **Privacy** > **Disattiva InPrivate Browsing**.
    - Utente: espandere **Configurazione utente** > **Criteri** > **Modelli amministrativi** > **Componenti di Windows** > **Internet Explorer** > **Privacy** > **Disattiva InPrivate Browsing**.

    > [!div class="mx-imgBorder"]
    > ![Disattivare InPrivate Browsing in Internet Explorer tramite il modello ADMX](./media/tutorial-walkthrough-administrative-templates/group-policy-turn-off-inprivate-browsing.png)

> [!TIP]
> Per visualizzare i criteri predefiniti di Windows, è anche possibile usare GPEdit (app **Modifica Criteri di gruppo**).

#### <a name="compare-an-edge-policy"></a>Confrontare un criterio di Edge

1. Nell'interfaccia di amministrazione di gestione dei dispositivi passare al modello **Modello amministrativo - Dispositivi Windows 10 per studenti**.
2. Selezionare **Edge versione 77 e successive** nell'elenco a discesa.
3. Cercare **avvio**. Notare le impostazioni disponibili.
4. In Editor Gestione Criteri di gruppo individuare le impostazioni seguenti:

    - Dispositivo: espandere **Configurazione computer** > **Criteri** > **Modelli amministrativi** > **Microsoft Edge** > **Startup, homepage and new tab page** (Avvio, pagina iniziale e pagina nuova scheda).
    - Utente: espandere **Configurazione utente** > **Criteri** > **Modelli amministrativi** > **Microsoft Edge** > **Startup, homepage and new tab page** (Avvio, pagina iniziale e pagina nuova scheda).

### <a name="what-did-i-just-do"></a>Riepilogo delle operazioni eseguite

È stato creato un modello amministrativo in Intune. In questo modello sono state esaminate alcune impostazioni ADMX e sono state esaminate le stesse impostazioni ADMX in Gestione Criteri di gruppo.

## <a name="add-settings-to-the-students-admin-template"></a>Aggiungere impostazioni al modello amministrativo Studenti

In questo modello vengono configurate alcune impostazioni di Internet Explorer per bloccare i dispositivi condivisi da più studenti.

1. In **Modello amministrativo - Dispositivi Windows 10 per studenti** cercare **Disattiva InPrivate Browsing** e selezionare il criterio per i dispositivi:

    > [!div class="mx-imgBorder"]
    > ![Criterio per i dispositivi Disattiva InPrivate Browsing in un modello amministrativo in Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/turn-off-inprivate-browsing-administrative-template.png)

2. In questa finestra notare la descrizione e i valori che è possibile impostare. Queste opzioni sono simili a quelle visualizzate in Criteri di gruppo.
3. Selezionare **Abilitata** > **OK** per salvare le modifiche.
4. Configurare anche le impostazioni di Internet Explorer seguenti. Assicurarsi di selezionare **OK** per salvare le modifiche.

    - **Consenti Trascina o Copia e Incolla file**
      - **Tipo**: Dispositivo
      - **Percorso**: Componenti di Windows\Internet Explorer\Pannello di controllo Internet\Scheda Sicurezza\Area Internet
      - **Valore**: Disabilitato

    - **Imponi verifica errori dei certificati**
      - **Tipo**: Dispositivo
      - **Percorso**: Componenti di Windows\Internet Explorer\Pannello di controllo Internet
      - **Valore**: Abilitato

    - **Impedisci la modifica delle impostazioni relative alla pagina iniziale**
      - **Tipo**: Utente
      - **Percorso**: \Componenti di Windows\Internet Explorer
      - **Valore**: Abilitato
      - **Pagina iniziale**: immettere un URL, ad esempio `contoso.com`.

5. Cancellare il filtro di ricerca. Si noti che le impostazioni configurate sono elencate per prime:

    > [!div class="mx-imgBorder"]
    > ![Le impostazioni configurate sono elencate per prime in Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/configured-settings-administrative-template.png)

### <a name="assign-your-template"></a>Assegnare il modello

1. Nel modello selezionare **Assegnazioni**. Potrebbe essere necessario chiudere il modello e quindi selezionarlo nell'elenco **Dispositivi - Profili di configurazione**:

    > [!div class="mx-imgBorder"]
    > ![Selezionare il profilo del modello amministrativo nell'elenco dei profili di configurazione del dispositivo in Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/filter-administrative-template-device-configuration-profiles-list.png)

2. Scegliere **Selezionare i gruppi da includere**. Viene visualizzato un elenco di utenti e gruppi esistenti.
3. Selezionare il gruppo **Tutti i dispositivi Windows 10 per studenti** creato in precedenza > **Seleziona**.

    Se si usa questa esercitazione in un ambiente di produzione, valutare la possibilità di aggiungere gruppi vuoti. L'obiettivo è quello di fare pratica con l'assegnazione del modello.

4. **Salvare** le modifiche.

Subito dopo il salvataggio, il profilo viene applicato ai dispositivi quando vengono sincronizzati con Intune. Se i dispositivi sono connessi a Internet, è possibile che ciò avvenga immediatamente. Per altre informazioni sui tempi di aggiornamento dei criteri, vedere [Quanto tempo è necessario ai dispositivi per ottenere criteri, un profilo o un'app dopo l'assegnazione?](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Quando si assegnano criteri e profili rigorosi o restrittivi, fare attenzione a non rimanere bloccati. Valutare la possibilità di creare un gruppo escluso dai criteri e dai profili. Lo scopo è quello di mantenere l'accesso per eventuali attività di risoluzione dei problemi. Monitorare questo gruppo per verificare che venga usato come previsto.

### <a name="what-did-i-just-do"></a>Riepilogo delle operazioni eseguite

Nell'interfaccia di amministrazione di Endpoint Manager è stato creato un profilo di configurazione del dispositivo con modello amministrativo e il profilo è stato assegnato a un gruppo creato appositamente.

## <a name="create-a-onedrive-template"></a>Creare un modello di OneDrive

In questa sezione viene creato un modello amministrativo di OneDrive in Intune per controllare alcune impostazioni. Queste impostazioni specifiche vengono scelte perché sono comunemente usate dalle organizzazioni.

1. Creare un altro profilo (**Dispositivi** > **Profili di configurazione** > **Crea profilo**).

2. Immettere le proprietà seguenti:

    - **Nome**: immettere **Modello amministrativo - Criteri di OneDrive applicabili a tutti gli utenti di Windows 10**.
    - **Descrizione**: Immettere una descrizione del profilo. Questa impostazione è facoltativa ma consigliata.
    - **Piattaforma**: selezionare **Windows 10 e versioni successive**.
    - **Tipo di profilo**: selezionare **Modelli amministrativi**.

3. Selezionare **Crea**.
4. Selezionare **Office** nell'elenco a discesa.
5. **Abilitare** le impostazioni seguenti. Assicurarsi di selezionare **OK** per salvare le modifiche.

    - **Consenti l'accesso automatico degli utenti al client di sincronizzazione di OneDrive con le proprie credenziali di Windows**
    - **Usa File di OneDrive su richiesta**
    - **Impedisci agli utenti di sincronizzare gli account personali di OneDrive**

Al termine, le impostazioni saranno simili alle seguenti:

> [!div class="mx-imgBorder"]
> ![Creare un modello amministrativo di OneDrive in Microsoft Intune](./media/tutorial-walkthrough-administrative-templates/one-drive-administrative-template.png)

Per altre informazioni sulle impostazioni client di OneDrive, vedere [Usare Criteri di gruppo per controllare le impostazioni di sincronizzazione di OneDrive](https://docs.microsoft.com/onedrive/use-group-policy).

### <a name="assign-your-template"></a>Assegnare il modello

1. Nel modello selezionare **Assegnazioni**.
2. Scegliere **Selezionare i gruppi da includere**. Viene visualizzato un elenco di utenti e gruppi esistenti.
3. Selezionare il gruppo **Tutti i dispositivi Windows** creato in precedenza > **Seleziona**.

    Se si usa questa esercitazione in un ambiente di produzione, valutare la possibilità di aggiungere gruppi vuoti. L'obiettivo è quello di fare pratica con l'assegnazione del modello.

4. **Salvare** le modifiche.

A questo punto sono stati creati alcuni modelli amministrativi che sono stati assegnati ai gruppi creati. Il passaggio successivo consiste nel creare un modello amministrativo usando Windows PowerShell e l'API Microsoft Graph per Intune.

## <a name="optional-create-a-policy-using-powershell-and-graph-api"></a>Facoltativo: Creare un criterio usando PowerShell e l'API Graph

Questa sezione usa le risorse seguenti. Queste risorse verranno installate in questa sezione.

- [Intune PowerShell SDK](https://github.com/microsoft/Intune-PowerShell-SDK)
- [API Microsoft Graph per Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)

1. Nel **computer Admin** aprire **Windows PowerShell** come amministratore:

    1. Nella barra di ricerca immettere **powershell**.
    2. Fare clic con il pulsante destro del mouse su **Windows PowerShell** > **Esegui come amministratore**.

    > [!div class="mx-imgBorder"]
    > ![Eseguire Windows PowerShell come amministratore](./media/tutorial-walkthrough-administrative-templates/run-windows-powershell-administrator.png)

2. Ottenere e impostare i criteri di esecuzione.

    1. Immettere: `get-ExecutionPolicy`

        Prendere nota dell'impostazione, che potrebbe essere **Restricted** (Con restrizioni). Al termine dell'esercitazione, reimpostare il valore originale.

    2. Immettere: `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`

    3. Immettere `Y` per modificarlo.

    I criteri di esecuzione di PowerShell consentono di impedire l'esecuzione di script dannosi. Per altre informazioni, vedere [Informazioni sui criteri di esecuzione](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).

3. Immettere: `Install-Module -Name Microsoft.Graph.Intune`

    Immettere `Y` se:

    - Viene richiesto di installare il provider NuGet
    - Viene richiesto di installare i moduli da un repository non attendibile

    L'operazione può richiede alcuni minuti. Al termine, viene visualizzato un prompt simile al seguente:

    > [!div class="mx-imgBorder"]
    > ![Prompt di Windows PowerShell dopo l'installazione di un modulo](./media/tutorial-walkthrough-administrative-templates/powershell-prompt.png)

4. Nel Web browser passare a [https://github.com/Microsoft/Intune-PowerShell-SDK/releases](https://github.com/Microsoft/Intune-PowerShell-SDK/releases) e selezionare il file **Intune-PowerShell-SDK_v6.1907.00921.0001.zip**.

    1. Selezionare **Salva come** e selezionare una cartella facile da ricordare. `c:\psscripts` è una buona scelta.
    2. Aprire la cartella, fare clic con il pulsante destro del mouse sul file ZIP > **Estrai tutto** > **Estrai**. La struttura di cartelle è simile alla seguente:

        > [!div class="mx-imgBorder"]
        > ![Struttura di cartelle di Intune PowerShell SDK dopo l'estrazione](./media/tutorial-walkthrough-administrative-templates/psscripts-directory.png)

5. Nella scheda **Visualizza** selezionare **Estensioni nomi file**:

    > [!div class="mx-imgBorder"]
    > ![Selezionare Estensioni nomi file nella scheda Visualizza in Esplora risorse](./media/tutorial-walkthrough-administrative-templates/file-names-extension.png)

6. Nella cartella passare a `c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471`. Fare clic con il pulsante destro del mouse su ogni file con estensione dll > **Proprietà** > **Sblocca**.

    > [!div class="mx-imgBorder"]
    > ![Sbloccare le DLL](./media/tutorial-walkthrough-administrative-templates/unblock-dll.png)

7. Nell'app **Windows PowerShell** immettere:

    ```powershell
    Import-Module c:\psscripts\Intune-PowerShell-SDK_v6.1907.00921.0001\drop\outputs\build\Release\net471\Microsoft.Graph.Intune.psd1
    ```

    Immettere `R` se viene richiesta l'esecuzione dal server di pubblicazione non attendibile.

8. I modelli amministrativi di Intune usano la versione beta di Graph:

    1. Immettere: `Update-MSGraphEnvironment -SchemaVersion 'beta'`

    2. Immettere: `Connect-MSGraph -AdminConsent`

    3. Quando richiesto, accedere con lo stesso account di amministratore di Microsoft 365. Questi cmdlet creano i criteri nell'organizzazione tenant.

        **Utente**: immettere l'account amministratore della sottoscrizione tenant di Microsoft 365.  
        **Password**: immettere la password.

    4. Selezionare **Accetta**.

9. Creare il profilo di configurazione **Configurazione di test**. Immettere:

    ```powershell
    $configuration = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations -Content '{"displayName":"Test Configuration","description":"A test configuration created through PS"}' -HttpMethod POST
    ```

    Quando questi cmdlet hanno esito positivo, viene creato il profilo. Per confermare, passare all'interfaccia di amministrazione di Endpoint Manager > **Profili di configurazione**. Il profilo **Configurazione di test** dovrebbe essere elencato.

10. Ottenere tutti i valori SettingDefinitions. Immettere:

    ```powershell
    $settingDefinitions = Invoke-MSGraphRequest -Url https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions -HttpMethod GET
    ```

11. Trovare l'ID della definizione usando il nome visualizzato dell'impostazione. Immettere:

    ```powershell
    $desiredSettingDefinition = $settingDefinitions.value | ? {$_.DisplayName -Match "Silently sign in users to the OneDrive sync client with their Windows credentials"}
    ```

12. Configurare un'impostazione. Immettere:

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues" -Content ("{""enabled"":""true"",""configurationType"":""policy"",""definition@odata.bind"":""https://graph.microsoft.com/beta/deviceManagement/groupPolicyDefinitions('$($desiredSettingDefinition.id)')""}") -HttpMethod POST
    ```

    ```powershell
    Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -Content ("{""enabled"":""false""}") -HttpMethod PATCH
    ```

    ```powershell
    $configuredSetting = Invoke-MSGraphRequest -Url "https://graph.microsoft.com/beta/deviceManagement/groupPolicyConfigurations('$($configuration.id)')/definitionValues('$($configuredSetting.id)')" -HttpMethod GET
    ```

### <a name="see-your-policy"></a>Vedere il criterio

1. Nell'interfaccia di amministrazione di Endpoint Manager > **Profili di configurazione** > **Aggiorna**.
2. Selezionare il profilo **Configurazione di test** > **Impostazioni**.
3. Nell'elenco a discesa selezionare **Tutti i prodotti**.

Si vedrà l'impostazione **Consenti l'accesso automatico degli utenti al client di sincronizzazione di OneDrive con le proprie credenziali di Windows** configurata.

## <a name="policy-best-practices"></a>Procedure consigliate per i criteri

Quando si creano criteri e profili in Intune, è opportuno tenere conto di alcune raccomandazioni e procedure consigliate. Per altre informazioni, vedere le [procedure consigliate per criteri e profili](device-profile-create.md#recommendations).

## <a name="clean-up-resources"></a>Pulizia delle risorse

Quando non servono più, è possibile:

- Eliminare i gruppi creati:

  - **Tutti i dispositivi Windows 10 per studenti**
  - **Tutti i dispositivi Windows**
  - **Tutti i docenti**

- Eliminare i modelli amministrativi creati:

  - **Modello amministrativo - Dispositivi Windows 10 per studenti**
  - **Modello amministrativo - Criteri di OneDrive applicabili a tutti gli utenti di Windows 10**
  - **Configurazione di test**

- Reimpostare il valore originale per i criteri di esecuzione di Windows PowerShell. Nell'esempio seguente i criteri di esecuzione vengono impostati su Restricted:

  ```powershell
  Set-ExecutionPolicy -ExecutionPolicy Restricted
  ```

## <a name="next-steps"></a>Passaggi successivi

In questa esercitazione si è acquisita familiarità con l'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), è stato usato il generatore di query per creare gruppi dinamici e sono stati creati modelli amministrativi in Intune per configurare le [impostazioni di ADMX](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies). Sono stati anche confrontati i modelli ADMX in locale e nel cloud con Intune. Si è visto inoltre come usare i cmdlet di PowerShell per creare un modello amministrativo.

Per altre informazioni sui modelli amministrativi in Intune, vedere:

> [!div class="nextstepaction"]
> [Usare i modelli di Windows 10 per configurare le impostazioni di Criteri di gruppo in Intune](administrative-templates-windows.md)
