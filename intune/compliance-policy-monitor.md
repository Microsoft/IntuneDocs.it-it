---
title: "Monitorare i criteri di conformità dei dispositivi di Intune"
titlesuffix: Azure portal
description: "Informazioni su come monitorare i criteri di conformità dei dispositivi"
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 2/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2f80d46e3e7c25c2b2e7a7c1af9604de1257a21e
ms.sourcegitcommit: a55c009a2ab223f79dc7439539937b284aee0626
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="monitor-intune-device-compliance-policies"></a>Monitorare i criteri di conformità dei dispositivi di Intune

I report di conformità consentono agli amministratori di analizzare il comportamento di conformità dei dispositivi nell'organizzazione e di risolvere rapidamente i problemi correlati alla conformità riscontrati dagli utenti all'interno dell'organizzazione. È possibile visualizzare le informazioni sullo stato generale di conformità dei dispositivi e sullo stato di conformità per una singola impostazione o un singolo criterio e anche eseguire il drill-down in un singolo dispositivo per visualizzare le impostazioni e i criteri specifici che interessano tale dispositivo.

## <a name="before-you-begin"></a>Prima di iniziare

Usare questa procedura per trovare il **dashboard della conformità dei dispositivi di Intune** nel portale di Azure:

1.  Andare nel [portale di Azure](https://portal.azure.com) e accedere con le credenziali di Intune.

2.  Scegliere **Altri servizi** dal menu a sinistra e quindi digitare **Intune** nel filtro della casella di testo.

3.  Scegliere **Intune** &gt; **Conformità del dispositivo** &gt; **Panoramica**. Verrà visualizzato il **dashboard della conformità dei dispositivi**.

> [!IMPORTANT] 
> Per ricevere i criteri di conformità, i dispositivi devono essere registrati in Intune.

## <a name="device-compliance-dashboard"></a>Dashboard della conformità dei dispositivi

Nel **dashboard della conformità dei dispositivi** è possibile monitorare gli stati dei criteri di conformità dei dispositivi visualizzando all'interno di riquadri i vari report relativi al comportamento di conformità dei dispositivi nell'organizzazione. È possibile visualizzare i report seguenti:

-   Aggregazione dei dati di conformità per tutti i dispositivi

-   Conformità dei dispositivi in base ai criteri

-   Conformità dei dispositivi in base alle impostazioni

![Dashboard della conformità dei dispositivi](./media/idc-1.png)

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

![Drill-down nel dashboard della conformità dei dispositivi](./media/idc-2.png)

Per altri dettagli su un utente specifico, è possibile filtrare il report grafico Conformità del dispositivo digitando l'alias di posta elettronica dell'utente.

![Utente specifico del dashboard della conformità dei dispositivi](./media/idc-3.png)

È anche possibile fare clic su un diverso stato di conformità nel grafico Conformità del dispositivo per visualizzare altri dettagli sugli stati dei criteri di conformità dei dispositivi dell'utente.

![Stati diversi nel dashboard della conformità dei dispositivi](./media/idc-4.png)

#### <a name="filter"></a>Filtra

Se si fa clic sul pulsante **Filtra**, viene visualizzata l'area a comparsa del filtro con le opzioni seguenti:

-   Modello

    -   Casella di testo in cui immettere qualsiasi stringa di ricerca
<br></br>
-   Piattaforma

    -   Android

    -   iOS

    -   Mac OS

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

Se si fa clic su un dispositivo, viene aperto il **pannello dei dispositivi** con il dispositivo selezionato. È così possibile visualizzare altri dettagli sull'impostazione di criterio di conformità applicata al dispositivo.

![Dashboard della conformità dei dispositivi](./media/idc-6.png)

Quando si fa clic sull'impostazione stessa, è possibile visualizzare il nome del criterio di conformità risultante dall'impostazione definita dall'amministratore.

![Nome dell'impostazione di conformità dei dispositivi](./media/idc-7.png)

## <a name="policy-compliance-report"></a>Report di conformità ai criteri

Questo report offre una visualizzazione in base ai criteri di conformità e indica il numero totale di dispositivi in ogni stato di conformità. Il riquadro **Conformità dei criteri** è accessibile dal **dashboard della conformità dei dispositivi** e mostra tutti i criteri creati in precedenza dall'amministratore, le piattaforme in cui è applicato il criterio, il numero di dispositivi conformi e quello di dispositivi non conformi.

![Report di conformità dei dispositivi in base ai criteri](./media/idc-8.png)

Quando si fa clic sul riquadro Conformità dei criteri e quindi su uno dei criteri di conformità dei dispositivi, è possibile vedere lo **stato di conformità**, l'**alias di posta elettronica dell'utente**, il **modello** e la **posizione** per ogni dispositivo interessato dai criteri di conformità dei dispositivi.

![Riquadro Conformità dei criteri](./media/idc-9.png)

## <a name="setting-compliance-report"></a>Report di conformità dell'impostazione

Questo report consente di visualizzare, per ogni singola impostazione di conformità, il numero totale di dispositivi in ogni stato di conformità. Il riquadro **Conformità dell'impostazione** è accessibile dal **dashboard della conformità dei dispositivi** e mostra tutte le impostazioni relative a tutti i criteri di conformità dei dispositivi creati dall'amministratore, le piattaforme a cui sono state applicate le impostazioni dei criteri e il numero di dispositivi non conformi.

![Report di conformità dei dispositivi in base alle impostazioni](./media/idc-10.png)

Quando si fa clic sul riquadro Conformità dell'impostazione e quindi su una delle impostazioni dei criteri di conformità dei dispositivi, è possibile vedere lo **stato di conformità**, l'**alias di posta elettronica dell'utente**, il **modello** e la **posizione** per ogni dispositivo interessato dall'impostazione dei criteri di conformità dei dispositivi.

![Riquadro Conformità dell'impostazione](./media/idc-11.png)

## <a name="threat-agent-status-report"></a>Report dello stato dell'agente delle minacce

Questo report consente di visualizzare lo stato e l'integrità dell'agente di Windows Defender. Usando un report di rollup dello stato in **Conformità del dispositivo** è possibile visualizzare i dispositivi per i quali è necessaria una delle azioni seguenti:
- Aggiornamento della firma
- Riavvio
- Intervento manuale
- Analisi completa
- Intervento per altri stati dell'agente

Un report di analisi per ogni categoria di stato elenca i singoli PC che richiedono attenzione e quelli per i quali è indicato **Pulisci**.
