---
title: Introduzione alle connessioni dati eSIM in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o usare eSIM per ottenere l'accesso a Internet e ai dati usando piani di dati diversi. In Intune è possibile aggiungere o importare i codici di attivazione, quindi assegnare questi codici usando un profilo di configurazione. È anche possibile monitorare i profili eSIM e controllare lo stato dei dispositivi in cui è attiva la connessione eSIM.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0ef42e301efe2c323ea98265272ba71596a8083
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206398"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>Configurare i profili cellulare eSIM in Intune - Anteprima pubblica

eSIM è un chip SIM incorporato, che consente di accedere a Internet su una connessione alla rete cellulare in un dispositivo che supporta la tecnologia eSIM, ad esempio [Surface LTE Pro](https://www.microsoft.com/surface/business/surface-pro). Con un eSIM, non è necessario ottenere una scheda SIM dall'operatore di telefonia mobile. Chi viaggia in tutto il mondo può anche passare da un operatore di telefonia mobile a un altro e da un piano dati a un altro per rimanere sempre connesso.

Ad esempio è possibile avere un piano di rete dati per il lavoro e un altro piano con un altro operatore per uso personale. Mentre si è in viaggio, è possibile ottenere l'accesso a Internet cercando operatori di telefonia mobile con piani dati nell'area in cui ci si trova.

In Intune è possibile importare un file contenente i codici di attivazione monouso resi disponibili dall'operatore di telefonia mobile. Per configurare i piani di rete dati nel modulo eSIM, distribuire tali codici di attivazione nei dispositivi che supportano eSIM. Quando Intune installa il codice di attivazione, il modulo hardware eSIM usa i dati del codice di attivazione per contattare l'operatore di telefonia mobile. Al termine dell'operazione, il profilo eSIM viene scaricato sul dispositivo e configurato per l'attivazione del cellulare.

Per distribuire eSIM ai dispositivi mediante Intune sono necessari gli elementi seguenti:

- **Dispositivi abilitati per eSIM**, ad esempio Surface LTE: Verificare se [il dispositivo supporta eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). In alternativa, vedere un elenco di [dispositivi noti con supporto eSIM](#esim-capable-devices) (in questo articolo).
- **Windows 10 Fall Creators Update PC** (versione 1709 o successiva) che viene registrato e gestito da MDM in Intune
- **Codici di attivazione** resi disponibili dall'operatore di telefonia mobile. Questi codici di attivazione monouso vengono aggiunti a Intune e distribuiti ai dispositivi che supportano eSIM. Contattare l'operatore di telefonia mobile per ottenere i codici di attivazione eSIM.

## <a name="deploy-esim-to-devices---overview"></a>Distribuire eSIM ai dispositivi - Panoramica

Per distribuire eSIM ai dispositivi, un amministratore completa le attività seguenti:

1. Importare i codici di attivazione resi disponibili dall'operatore di telefonia mobile
2. Creare un gruppo di dispositivi Azure Active Directory (Azure AD) che include i dispositivi che supportano eSIM
3. Assegnare il gruppo di Azure AD al pool di sottoscrizioni importato
4. Monitorare la distribuzione

Questo articolo illustra tali procedure.

## <a name="esim-capable-devices"></a>Dispositivi che supportano eSIM

I dispositivi seguenti sono indicati come provvisti di supporto eSIM o sono attualmente in commercio. Verificare anche se [il dispositivo supporta eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

- Acer Swift 7
- Asus NovoGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP Elitebook G5
- HP Envy x2
- HP Probook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre Folio 13
- Lenovo Yoga C630

## <a name="step-1-add-cellular-activation-codes"></a>Passaggio 1: Aggiungere i codici di attivazione del cellulare

I codici di attivazione del cellulare vengono resi disponibili dall'operatore di telefonia mobile in un file di testo delimitato da virgole (file con estensione csv). Quando è presente questo file, aggiungerlo a Intune con la procedura seguente:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili cellulare eSIM** > **Aggiungi**.
3. Selezionare il file con estensione csv contenente i codici di attivazione.
4. Selezionare **OK** per salvare le modifiche.

### <a name="csv-file-requirements"></a>Requisiti del file con estensione csv

Quando si usa il file con estensione csv con i codici di attivazione, assicurarsi o richiedere all'operatore di telefonia mobile che siano soddisfatti i requisiti seguenti:

- Il file deve essere in formato csv (nomefile.csv).
- La struttura del file deve rispettare un formato preciso. In caso contrario l'importazione avrà esito negativo. Il file viene controllato in Intune durante l'importazione; se vengono rilevati errori l'operazione non riesce.
- I codici di attivazione devono essere usati una sola volta. Si sconsiglia di importare codici di attivazione già importati in precedenza. Questa operazione può creare problemi al momento della distribuzione nello stesso dispositivo o in un altro dispositivo.
- Ogni file deve essere specifico per un singolo operatore di telefonia mobile e tutti i codici di attivazione devono corrispondere allo stesso piano di fatturazione. Intune distribuisce in modo casuale i codici di attivazione ai dispositivi di destinazione. Non è possibile determinare quale dispositivo ottiene un codice di attivazione specifico.
- È possibile importare un massimo di 1000 codici di attivazione in un singolo file con estensione csv.

### <a name="csv-file-example"></a>Esempio di file con estensione csv

1. La prima riga e la prima cella del file con estensione csv specificano l'URL del servizio di attivazione eSIM dell'operatore di telefonia mobile, denominato SM-DP+ (server Subscription Manager Data Preparation). L'URL deve essere un nome di dominio completo (FQDN) senza virgole.
2. La seconda riga e tutte le righe successive sono codici di attivazione univoci monouso che includono due valori:

    1. La prima colonna contiene il codice univoco ICCID (l'identificatore del chip SIM)
    2. La seconda colonna è l'ID di abbinamento. I valori sono separati solo da virgole (nessuna virgola alla fine). Vedere l'esempio seguente:

        ![File csv di esempio con codici di attivazione dell'operatore di telefonia mobile](./media/esim-device-configuration/url-activation-code-examples.png)

3. Il nome del file con estensione csv diventa il nome del pool di sottoscrizione cellulare nell'interfaccia di amministrazione di Endpoint Manager. Nell'immagine precedente il nome file è `UnlimitedDataSkynet.csv`. Pertanto il nome del pool di sottoscrizione in Intune è `UnlimitedDataSkynet.csv`:

    ![Il nome del pool di sottoscrizione cellulare è basato sul nome del file con estensione csv dei codici di attivazione](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>Passaggio 2: Creare un gruppo di dispositivi Azure AD

Creare un gruppo che include i dispositivi che supportano eSIM. La procedura è illustrata in [Aggiungere gruppi](../fundamentals/groups-add.md).

> [!NOTE]
> - La procedura riguarda i dispositivi e non gli utenti.
> - È consigliabile creare un gruppo di dispositivi Azure AD statico che include i dispositivi eSIM. L'uso di un gruppo conferma che la destinazione è costituita solo da dispositivi eSIM.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>Passaggio 3: Assegnare codici di attivazione eSIM ai dispositivi

Assegnare il profilo al gruppo di Azure AD che include i dispositivi eSIM.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili cellulare eSIM**.
3. Nell'elenco dei profili selezionare il pool di sottoscrizione cellulare eSIM che si vuole assegnare e quindi scegliere **Assegnazioni**.
4. Scegliere **Includi** o **Escludi**, quindi selezionare i gruppi da includere o escludere.

    ![Includere il gruppo di dispositivi per assegnare il profilo](./media/esim-device-configuration/include-exclude-groups.png)

5. Quando si selezionano i gruppi, si sceglie un gruppo di Azure AD. Per selezionare più gruppi premere **CTRL** e selezionare i gruppi.
6. Al termine scegliere **Salva** per salvare le modifiche.

I codici di attivazione eSIM devono essere usati una sola volta. Dopo che Intune installa un codice di attivazione in un dispositivo, il modulo eSIM contatta l'operatore di telefonia mobile per scaricare il profilo cellulare. Il contatto completa la registrazione del dispositivo nella rete dell'operatore di telefonia mobile.

## <a name="step-4-monitor-deployment"></a>Passaggio 4: Monitorare la distribuzione

### <a name="review-the-deployment-status"></a>Esaminare lo stato della distribuzione

Dopo aver assegnato il profilo, è possibile monitorare lo stato della distribuzione di un pool di sottoscrizioni.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Dispositivi** > **Profili cellulare eSIM**. Vengono elencati tutti i pool di sottoscrizione cellulare eSIM esistenti.
3. Selezionare una sottoscrizione ed esaminare **Stato distribuzione**.

### <a name="check-the-profile-status"></a>Verificare lo stato del profilo

Dopo avere creato il profilo del dispositivo, Intune fornisce i grafici. Questi grafici visualizzano lo stato di un profilo, ad esempio che è correttamente assegnato ai dispositivi oppure se il profilo mostra un conflitto.

1. Selezionare **Dispositivi** > **Profili cellulare eSIM** > selezionare una sottoscrizione esistente.
2. Nella scheda **Panoramica**, il grafico in alto visualizza il numero di dispositivi assegnati alla distribuzione del pool sottoscrizione cellulare eSIM specifica.

    Visualizza anche il numero di dispositivi per le altre piattaforme a cui è assegnato lo stesso profilo di dispositivo.

    Intune visualizza lo stato di distribuzione e installazione del codice di attivazione destinato ai dispositivi.

    - **Il dispositivo non è sincronizzato**: il dispositivo di destinazione non ha contattato Intune da quando sono stati creati i criteri di distribuzione eSIM
    - **Attivazione in sospeso**: stato intermedio in cui Intune sta installando il codice di attivazione nel dispositivo
    - **Attivo**: l'installazione del codice di attivazione è riuscita
    - **Attivazione non riuscita**: l'installazione del codice di attivazione non è riuscita. Vedere la Guida alla risoluzione dei problemi.

#### <a name="view-the-detailed-device-status"></a>Visualizzare lo stato dettagliato del dispositivo

È possibile monitorare e visualizzare un elenco dettagliato dei dispositivi in Stato del dispositivo.**

1. Selezionare **Dispositivi** > **Profili cellulare eSIM** > selezionare una sottoscrizione esistente.
2. Selezionare **Stato del dispositivo**. Intune visualizza dettagli aggiuntivi sul dispositivo:

    - **Nome dispositivo**: nome del dispositivo di destinazione
    - **Utente**: utente del dispositivo registrato
    - **ICCID**: codice univoco reso disponibile dall'operatore di telefonia mobile e incluso nel codice di attivazione installato nel dispositivo
    - **Stato attivazione**: stato di distribuzione e installazione Intune del codice di attivazione nel dispositivo
    - **Stato della rete cellulare**: stato specificato dall'operatore di telefonia mobile. Per la risoluzione dei problemi, contattare l'operatore di telefonia mobile.
    - **Ultima sincronizzazione**: data dell'ultima comunicazione tra il dispositivo e Intune

### <a name="monitor-esim-profile-details-on-the-actual-device"></a>Monitorare i dettagli del profilo eSIM sul dispositivo

1. Nel dispositivo selezionare **Impostazioni** > **Rete e Internet**.
2. Selezionare **Cellulare** > **Manage eSIM profiles** (Gestisci profili eSIM)
3. Vengono elencati i profili eSIM:

    ![Visualizzare i profili eSIM nelle impostazioni del dispositivo](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>Rimuovere il profilo eSIM dal dispositivo

Quando si rimuove il dispositivo dal gruppo di Azure AD, viene rimosso anche il profilo eSIM. Assicurarsi di:

1. Verificare che si sta usando il gruppo Azure AD dei dispositivi eSIM.
2. Passare al gruppo di Azure AD e rimuovere il dispositivo dal gruppo.
3. Quando il dispositivo rimosso contatta Intune, vengono valutati i criteri aggiornati e il profilo eSIM viene rimosso.

Il profilo di eSIM viene rimosso anche quando il dispositivo viene [disattivato](../remote-actions/devices-wipe.md#retire) o la sua iscrizione annullata dall'utente oppure quando nel dispositivo viene eseguita [l'azione remota Reimposta dispositivo](../remote-actions/devices-wipe.md#wipe).

> [!NOTE]
> È possibile che la rimozione del profilo non interrompa la fatturazione. Per controllare lo stato della fatturazione per il dispositivo, contattare l'operatore di telefonia mobile.

## <a name="best-practices--troubleshooting"></a>Procedure consigliate e risoluzione dei problemi

- Assicurarsi che il file con estensione csv sia formattato correttamente. Verificare che il file non includa codici duplicati, più operatori di telefonia mobile o piani dati diversi. Tenere presente che ogni file deve essere univoco per un operatore di telefonia mobile e un piano di rete dati.
- Creare un gruppo di dispositivi Azure AD statico che includa solo i dispositivi eSIM di destinazione.
- Se si verifica un problema con lo stato della distribuzione, verificare quanto segue:
  - **File format not proper** (Formato file non corretto): Vedere **Passaggio 1: Aggiungere i codici di attivazione del cellulare** in questo articolo per informazioni su come formattare il file correttamente.
  - **Cellular activation failure, contact mobile operator** (Errore di attivazione cellulare, contattare l'operatore): È possibile che il codice di attivazione non sia attivato nella rete. In alternativa, è possibile che il download del profilo e l'attivazione del cellulare non sia riuscita.

## <a name="next-steps"></a>Passaggi successivi
[Configurare i profili di dispositivo](../device-profiles.md)
