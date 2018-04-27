---
title: Monitorare i criteri di conformità dei dispositivi di Microsoft Intune
titlesuffix: ''
description: Usare il dashboard di conformità dei dispositivi per monitorare la conformità generale dei dispositivi, visualizzare i report e visualizzare la conformità dei dispositivi in base ai singoli criteri e alle singole impostazioni.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 557018264da5c21459e47e3e139ddd327a4a5ea6
ms.sourcegitcommit: c3ae3c3dc46b62d9191813d25a196874ba4927be
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2018
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorare i criteri di conformità dei dispositivi di Intune

I report di conformità consentono agli amministratori di analizzare il comportamento di conformità dei dispositivi nell'organizzazione e di risolvere rapidamente i problemi correlati alla conformità riscontrati dagli utenti all'interno dell'organizzazione. È possibile visualizzare le informazioni sullo stato generale di conformità dei dispositivi e sullo stato di conformità per una singola impostazione o un singolo criterio e anche eseguire il drill-down in un singolo dispositivo per visualizzare le impostazioni e i criteri specifici che interessano tale dispositivo.

> [!NOTE]
> Nel mese di marzo sono stati introdotti alcuni miglioramenti alla sicurezza, suggeriti dai commenti degli utenti, nel servizio Intune. A seconda della configurazione dei criteri di conformità, potrebbe essere necessario intervenire per evitare la perdita di accesso alla posta elettronica per gli utenti finali. Per informazioni dettagliate, vedere [Upcoming security enhancements](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/) (Miglioramenti alla sicurezza in arrivo).

## <a name="before-you-begin"></a>Prima di iniziare

Seguire questa procedura per trovare il **dashboard della conformità dei dispositivi di Intune** nel portale di Azure:

1.  Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune.

2.  Scegliere **Tutti i servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3.  Scegliere **Intune** &gt; **Conformità del dispositivo** &gt; **Panoramica**. Verrà visualizzato il **dashboard della conformità dei dispositivi**.

> [!IMPORTANT]
> Per ricevere i criteri di conformità, i dispositivi devono essere registrati in Intune.

## <a name="device-compliance-dashboard"></a>Dashboard della conformità dei dispositivi

Nel **dashboard della conformità dei dispositivi** è possibile monitorare gli stati dei criteri di conformità dei dispositivi visualizzando all'interno di riquadri i vari report relativi al comportamento di conformità dei dispositivi nell'organizzazione. È possibile visualizzare i report seguenti:

-   Aggregazione dei dati di conformità per tutti i dispositivi

-   Conformità dei dispositivi in base ai criteri

-   Conformità dei dispositivi in base alle impostazioni

![Immagine che mostra il dashboard della conformità dei dispositivi](./media/idc-1.png)

È inoltre possibile visualizzare impostazioni e criteri di conformità specifici per un singolo dispositivo e lo stato di conformità finale per ogni impostazione sul dispositivo.

### <a name="overall-device-compliance-aggregate-report"></a>Report di aggregazione dei dati di conformità per tutti i dispositivi

È un grafico ad anello che mostra lo stato di conformità aggregato per tutti i dispositivi registrati in Intune. Gli stati di conformità dei dispositivi vengono mantenuti in due diversi database, Intune e Azure Active Directory. Ecco altri dettagli sugli stati dei criteri di conformità dei dispositivi:

-   **Conforme**: il dispositivo rispetta una o più impostazioni di criteri di conformità definite dall'amministratore.

-   **Non conforme**: il dispositivo non rispetta una o più impostazioni di criteri di conformità definite dall'amministratore o l'utente non si è adeguato ai criteri definiti dall'amministratore.

-   **Periodo di tolleranza**: per il dispositivo l'amministratore ha definito una o più impostazioni di criteri di conformità, ma l'utente non ha ancora applicato tali criteri. In altre parole, il dispositivo non è conforme, ma si trova nel periodo di tolleranza definito dall'amministratore.

    -   Altre informazioni sulle azioni per i dispositivi non conformi.

-   **Dispositivo non sincronizzato**: il dispositivo non è riuscito a segnalare lo stato dei criteri di conformità per uno dei motivi seguenti:

    -   **Sconosciuto**: il dispositivo è offline o non è riuscito a comunicare con Intune o Azure AD per altri motivi.

    -   **Errore**: il dispositivo non è riuscito a comunicare con Intune e Azure AD e ha ricevuto un messaggio di errore con la spiegazione del motivo.

> [!IMPORTANT]
> I dispositivi che sono registrati in Intune, ma non sono interessati da alcun criterio di conformità, vengono inclusi in questo report all'interno del bucket **Conforme**.

#### <a name="drill-down-option"></a>Opzione di drill-down

Nel **dashboard della conformità dei dispositivi**, se si fa clic sul riquadro Conformità del dispositivo, è possibile eseguire il drill-down in uno specifico **stato di conformità**, **alias di posta elettronica dell'utente**, **modello** e **posizione** per ogni dispositivo interessato dai criteri di conformità dei dispositivi.

![Immagine che mostra il drill-down nel dashboard della conformità dei dispositivi](./media/idc-2.png)

Per altri dettagli su un utente specifico, è possibile filtrare il report grafico Conformità del dispositivo digitando l'alias di posta elettronica dell'utente.

![Immagine che mostra un utente specifico del dashboard della conformità dei dispositivi](./media/idc-3.png)

È anche possibile fare clic su un diverso stato di conformità nel grafico Conformità del dispositivo per visualizzare altri dettagli sugli stati dei criteri di conformità dei dispositivi dell'utente.

![Immagine che mostra i diversi stati nel dashboard della conformità dei dispositivi](./media/idc-4.png)

#### <a name="filter"></a>Filtra

Se si fa clic sul pulsante **Filtra**, viene visualizzata l'area a comparsa del filtro con le opzioni seguenti:

-   Modello

    -   Casella di testo in cui immettere qualsiasi stringa di ricerca
<br></br>
-   Piattaforma

    -   Android

    -   iOS

    -   macOS

    -   Windows

    -   Windows Phone

-   Stato

    -   Conforme

    -   Non conforme

    -   Periodo di tolleranza

    -   Sconosciuto

    -   Errore

Se si fa clic sul pulsante **Aggiorna**, l'area a comparsa dovrebbe essere chiusa e i risultati dovrebbero essere aggiornati in base ai criteri di filtro selezionati.

##### <a name="device-details"></a>Dettagli dispositivo

Facendo clic su un dispositivo viene visualizzato il **riquadro Dispositivi** con il dispositivo selezionato, che offre maggiori dettagli sull'impostazione dei criteri di conformità dei dispositivi applicati al dispositivo.

Quando si fa clic sull'impostazione stessa, è possibile visualizzare il nome del criterio di conformità risultante dall'impostazione definita dall'amministratore.

### <a name="devices-without-compliance-policy"></a>Dispositivi senza criteri di conformità
Questo report identifica i dispositivi a cui non è stato assegnato alcun criterio di conformità. Con l'introduzione dell'impostazione di sicurezza che contrassegna tutti i dispositivi senza criteri di conformità come "non conformi", è importante essere in grado di identificare tali dispositivi. Sarà quindi possibile assegnare loro almeno un criterio di conformità.

> [!NOTE]
> La nuova impostazione di sicurezza è configurabile nel portale di Intune. Selezionare **Conformità del dispositivo** e in **Installazione** scegliere **Impostazioni dei criteri di conformità**. Quindi usare l'alternanza per impostare **Contrassegna i dispositivi senza criteri di conformità assegnati come** e scegliere tra **Conforme** e **Non conforme**. Leggere altre informazioni su questo [miglioramento alla sicurezza nel servizio Intune](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/).

![Immagine del report dei dispositivi senza di criteri di conformità](./media/idc-12.png)

Il riquadro **Dispositivi senza criteri di conformità** è disponibile nel dashboard Conformità del dispositivo e mostra tutti i dispositivi senza criteri di conformità, l'utente del dispositivo, lo stato di conformità e il modello di dispositivo.

> [!NOTE]
> Gli utenti a cui è stato assegnato un criterio di conformità di qualsiasi tipo non verranno visualizzati nel report, indipendentemente dalla piattaforma del dispositivo. Ad esempio, se è stato assegnato involontariamente un criterio di conformità di Windows a un utente con un dispositivo Android, il dispositivo non apparirà nel report. Tuttavia, Intune considererà tale dispositivo Android come non conforme. Per evitare problemi, è consigliabile creare criteri per ogni piattaforma del dispositivo e distribuirli a tutti gli utenti.

### <a name="per-policy-device-compliance-report"></a>Report di conformità dei dispositivi in base ai criteri

Questo report offre una visualizzazione in base ai criteri di conformità e indica il numero totale di dispositivi in ogni stato di conformità. Il riquadro **Conformità dei criteri** è accessibile dal **dashboard della conformità dei dispositivi** e mostra tutti i criteri creati in precedenza dall'amministratore, le piattaforme in cui è applicato il criterio, il numero di dispositivi conformi e quello di dispositivi non conformi.

![Immagine che mostra il report di conformità dei dispositivi in base ai criteri](./media/idc-8.png)

Quando si fa clic sul riquadro Conformità dei criteri e quindi su uno dei criteri di conformità dei dispositivi, è possibile vedere lo **stato di conformità**, l'**alias di posta elettronica dell'utente**, il **modello** e la **posizione** per ogni dispositivo interessato dai criteri di conformità dei dispositivi.

## <a name="setting-compliance-report"></a>Report di conformità dell'impostazione

Questo report consente di visualizzare, per ogni singola impostazione di conformità, il numero totale di dispositivi in ogni stato di conformità. Il riquadro **Conformità dell'impostazione** è accessibile dal **dashboard della conformità dei dispositivi** e mostra tutte le impostazioni relative a tutti i criteri di conformità dei dispositivi creati dall'amministratore, le piattaforme a cui sono state applicate le impostazioni dei criteri e il numero di dispositivi non conformi.

![Immagine che mostra il report di conformità dei dispositivi in base alle impostazioni](./media/idc-10.png)

Quando si fa clic sul riquadro Conformità dell'impostazione e quindi su una delle impostazioni dei criteri di conformità dei dispositivi, è possibile vedere lo **stato di conformità**, l'**alias di posta elettronica dell'utente**, il **modello** e la **posizione** per ogni dispositivo interessato dall'impostazione dei criteri di conformità dei dispositivi.
