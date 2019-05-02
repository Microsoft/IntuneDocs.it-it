---
title: Monitorare i criteri di conformità dei dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Usare il dashboard di conformità dei dispositivi per monitorare la conformità generale dei dispositivi, visualizzare i report e visualizzare la conformità dei dispositivi in base ai singoli criteri e alle singole impostazioni.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 654d5b86a8a2df8eaddc8ea626b55390d2d32920
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61509071"
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorare i criteri di conformità dei dispositivi di Intune

I report sulla conformità consentono di verificare la conformità dei dispositivi e risolvere i problemi correlati alla conformità nell'organizzazione. L'uso di questi report consente di visualizzare informazioni su:

- Stato di conformità generale dei dispositivi
- Stato di conformità per una singola impostazione
- Stato di conformità per un singolo criterio
- Drill-down nei singoli dispositivi per visualizzare impostazioni e i criteri specifici che influiscono sul dispositivo

## <a name="open-the-compliance-dashboard"></a>Apertura del dashboard della conformità

Aprire il **dashboard della conformità dei dispositivi di Intune**:

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.

2. Selezionare **Conformità del dispositivo** > **Panoramica**. Verrà aperto il **dashboard della conformità dei dispositivi**.

> [!IMPORTANT]
> Per ricevere i criteri di conformità, i dispositivi devono essere registrati in Intune.

## <a name="dashboard-overview"></a>Informazioni generali sul dashboard

Quando si apre il dashboard, si ottiene una panoramica con tutti i report di conformità. In questi report è possibile visualizzare e verificare:

- Conformità complessiva del dispositivo
- Conformità dei dispositivi in base ai criteri
- Conformità dei dispositivi in base alle impostazioni
- Stato di protezione del dispositivo
- Stato dell'agente delle minacce

![Immagine del dashboard che illustra il dashboard della conformità del dispositivo e i vari report](./media/compliance-policy-monitor/idc-1.png)

Se si esaminano in dettaglio questi report, si possono vedere anche tutte le impostazioni e i criteri di conformità specifici validi per un dispositivo specifico, incluso lo stato di conformità per ogni impostazione.

### <a name="device-compliance-status-report"></a>Report sullo stato di conformità del dispositivo

Il grafico illustra gli stati di conformità per tutti i dispositivi registrati in Intune. Gli stati di conformità dei dispositivi vengono mantenuti in due diversi database: Intune e Azure Active Directory. 

> [!IMPORTANT]
> Intune segue la pianificazione in base alla quale il dispositivo contatta il servizio per tutte le valutazioni di conformità sul dispositivo. [Altre informazioni su questa pianificazione](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

Descrizioni dei diversi stati dei criteri di conformità dei dispositivi:

- **Conforme**: il dispositivo rispetta una o più impostazioni dei criteri di conformità dei dispositivi.

- **Periodo di tolleranza**: per il dispositivo sono state definite una o più impostazioni dei criteri di conformità dei dispositivi. Tuttavia, l'utente non ha ancora applicato i criteri. Questo significa che il dispositivo non è conforme, ma si trova nel periodo di tolleranza definito dall'amministratore.

  - Altre informazioni sulle [azioni per i dispositivi non conformi](actions-for-noncompliance.md).

- **Non valutato**: stato iniziale dei dispositivi appena registrati. Di seguito sono elencate altre possibili cause per questo stato:

  - Dispositivi a cui non sono assegnati criteri di conformità e che non hanno un trigger per verificare la conformità
  - Dispositivi che non si sono connessi dall'ultimo aggiornamento dei criteri di conformità
  - Dispositivi non associati a un utente specifico
  - Dispositivi registrati con un account del manager di registrazione dispositivi

- **Non conforme**: il dispositivo non rispetta una o più impostazioni dei criteri di conformità dei dispositivi. Oppure l'utente non è conforme ai criteri.

- **Dispositivo non sincronizzato**: il dispositivo non è riuscito a segnalare lo stato dei criteri di conformità per uno dei motivi seguenti:

  - **Sconosciuto**: il dispositivo è offline o non è riuscito a comunicare con Intune o Azure AD per altri motivi.

  - **Errore**: il dispositivo non è riuscito a comunicare con Intune e Azure AD e ha ricevuto un messaggio di errore con la spiegazione del motivo.

> [!IMPORTANT]
> I dispositivi che sono registrati in Intune, ma non sono interessati da alcun criterio di conformità, vengono inclusi in questo report all'interno del bucket **Conforme**.

#### <a name="drill-down-for-more-details"></a>Eseguire il drill-down per maggiori dettagli

Selezionare uno stato nel grafico dello **stato di conformità del dispositivo**. Ad esempio, selezionare lo stato **Non conforme**:

![Scegliere lo stato non conforme](./media/compliance-policy-monitor/select-not-compliant-status.png)

Vengono visualizzati altri dettagli sui dispositivi in tale stato, tra cui la piattaforma del sistema operativo, la data dell'ultima archiviazione e altro ancora. 

![Immagine del dashboard che visualizza altri dettagli sul dispositivo nello stato specifico](./media/compliance-policy-monitor/drill-down-details.png)

Per visualizzare tutti i dispositivi di proprietà di un utente specifico, è anche possibile filtrare il report grafico digitando l'indirizzo di posta elettronica dell'utente.

#### <a name="filter-and-columns"></a>Filtro e colonne

![Selezionare Filtro e Colonne per modificare i risultati nel grafico](./media/compliance-policy-monitor/filter-columns.png)

Quando si seleziona il pulsante **Filtro**, l'area a comparsa del filtro si apre con altre opzioni, tra cui lo stato di conformità, i dispositivi jailbroken e altro ancora. **Applicare** il filtro per aggiornare i risultati.

Usare la proprietà **Colonne** per aggiungere o rimuovere colonne dall'output grafico. Ad esempio, **Nome entità utente** può indicare l'indirizzo di posta elettronica registrato nel dispositivo. **Applicare** le colonne per aggiornare i risultati.

#### <a name="device-details"></a>Dettagli dispositivo

Nel grafico selezionare un dispositivo specifico e quindi selezionare **Conformità del dispositivo**:

![Scegliere un dispositivo specifico, quindi Conformità del dispositivo per vedere i criteri di conformità applicati](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

È possibile visualizzare altri dettagli sull'impostazione dei criteri di conformità applicati al dispositivo. Quando si seleziona il criterio specifico, vengono visualizzate tutte le impostazioni del criterio.

### <a name="devices-without-compliance-policy"></a>Dispositivi senza criteri di conformità
In **Conformità del dispositivo** > **Panoramica** il report identifica anche i dispositivi a cui non è stato assegnato alcun criterio di conformità:

![Vedere i dispositivi senza criteri di conformità](./media/compliance-policy-monitor/devices-without-policies.png)

Quando si seleziona il riquadro vengono visualizzati tutti i dispositivi senza criteri di conformità. Vengono visualizzati anche l'utente del dispositivo, lo stato della distribuzione dei criteri e il modello del dispositivo.

#### <a name="what-you-need-to-know"></a>Informazioni importanti

- Con l'impostazione di sicurezza **Contrassegna i dispositivi senza criteri di conformità assegnati come** è importante identificare i dispositivi senza criteri di conformità. Sarà quindi possibile assegnare loro almeno un criterio di conformità.

  L'impostazione di sicurezza è configurabile nel portale di Intune. Selezionare **Conformità del dispositivo** > **Impostazioni dei criteri di conformità**. Quindi impostare **Contrassegna i dispositivi senza criteri di conformità assegnati come** su **Conforme** o **Non conforme**. 

  Leggere altre informazioni su questo [miglioramento alla sicurezza nel servizio Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

- Gli utenti a cui è stato assegnato un criterio di conformità di qualsiasi tipo non vengono visualizzati nel report, indipendentemente dalla piattaforma del dispositivo. Ad esempio, se è stato assegnato un criterio di conformità di Windows a un utente con un dispositivo Android, il dispositivo non appare nel report. Tuttavia, Intune considera tale dispositivo Android come non conforme. Per evitare problemi, è consigliabile creare criteri per ogni piattaforma del dispositivo e distribuirli a tutti gli utenti.

### <a name="per-policy-device-compliance-report"></a>Report di conformità dei dispositivi in base ai criteri

Il report **Conformità del dispositivo** > **Conformità dei criteri** indica i criteri e il numero di dispositivi conformi e non conformi. 

![Visualizzare un elenco di criteri e il numero di dispositivi conformi e non conformi per tale criterio](./media/compliance-policy-monitor/idc-8.png)

Quando si seleziona un criterio specifico, è possibile visualizzare lo **stato di conformità**, l'**alias di posta elettronica dell'utente**, il **modello del dispositivo** e la **posizione** per ogni dispositivo interessato da quel criterio di conformità.

## <a name="setting-compliance-report"></a>Report di conformità dell'impostazione

Il report **Conformità del dispositivo** > **Conformità delle impostazioni** consente di visualizzare, per ogni singola impostazione di conformità, il numero totale di dispositivi in ogni stato di conformità. Vengono visualizzate tutte le impostazioni dei criteri di conformità dei dispositivi, le piattaforme a cui vengono applicate le impostazioni dei criteri e il numero di dispositivi non conformi.

![Visualizzare un elenco di tutte le impostazioni nei vari criteri](./media/compliance-policy-monitor/idc-10.png)

Quando si seleziona un'impostazione specifica, è possibile visualizzare lo **stato di conformità**, l'**alias di posta elettronica dell'utente**, il **modello del dispositivo** e la **posizione** per ogni dispositivo a cui viene applicata tale impostazione.

> [!NOTE]
> I dispositivi Windows 10 aggiunti ad Azure AD possono visualizzare l'account di sistema come utente non conforme. Si tratta di un comportamento previsto che non influisce sulla conformità complessiva del dispositivo. 

## <a name="view-status-of-device-policies"></a>Visualizzare lo stato dei criteri dei dispositivi

È possibile controllare i diversi stati dei criteri in base alla piattaforma. Si supponga, ad esempio, di avere un criterio di conformità macOS e di voler visualizzare i dispositivi interessati da questo criterio e verificare la presenza di eventuali conflitti o errori.

Questa funzionalità è inclusa nei report di stato del dispositivo:

1. Selezionare **Conformità del dispositivo** > **Criteri**. Viene visualizzato un elenco di criteri con informazioni sulla piattaforma, sull'assegnazione o meno del criterio e altri dettagli.
2. Selezionare un criterio > **Panoramica**. In questa visualizzazione l'assegnazione del criterio include gli stati seguenti:

    - Operazione completata: i criteri sono stati applicati.
    - Errore: non è stato possibile applicare i criteri. Il messaggio in genere viene visualizzato con un codice di errore collegato a una spiegazione. 
    - Conflitto: due impostazioni sono applicate allo stesso dispositivo e Intune non è in grado di risolvere il conflitto. Un amministratore deve esaminare la situazione.
    - In sospeso: il dispositivo non ha ancora contattato Intune per ricevere i criteri. 
    - Non applicabile: il dispositivo non può ricevere i criteri. Ad esempio, i criteri aggiornano un'impostazione specifica di iOS 11.1, ma il dispositivo usa iOS 10. 

3. Per visualizzare i dettagli sui dispositivi usando questo criterio, selezionare uno stato. Selezionare, ad esempio, **Operazione completata**. La finestra successiva conterrà i dettagli di un dispositivo specifico, tra cui il nome e lo stato di distribuzione.

## <a name="how-intune-resolves-policy-conflicts"></a>Come vengono risolti i conflitti di criteri in Intune
Possono verificarsi conflitti se vengono applicati più criteri di Intune a un dispositivo. Se le impostazioni dei criteri si sovrappongono, Intune risolve eventuali conflitti in base alle regole seguenti:

- Se le impostazioni in conflitto hanno origine da criteri di configurazione di Intune e da criteri di conformità, le impostazioni nei criteri di conformità hanno la precedenza rispetto a quelle dei criteri di configurazione, anche se queste ultime sono più sicure.

- Se sono stati distribuiti più criteri di conformità, Intune usa quelli più sicuri.
