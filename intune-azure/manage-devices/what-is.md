---
title: Gestire i dispositivi con Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come visualizzare i dispositivi gestiti con Intune ed eseguire diverse operazioni su di essi.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: d5d7b87f58604b93ba3b65d5d264a0a5e3743d45
ms.lasthandoff: 02/18/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>Informazioni sulla gestione dei dispositivi in Microsoft Intune 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Il carico di lavoro **Dispositivi e gruppi** offre informazioni dettagliate sui dispositivi gestiti e consente di eseguire attività remote su tali dispositivi. Per accedere al carico di lavoro:

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi e gruppi**.

    ![Carico di lavoro Dispositivi e gruppi](./media/devices-and-groups-workload.png)

A questo punto, scegliere una delle opzioni seguenti:

- **Panoramica**: ottenere informazioni sui dispositivi registrati e sui sistemi operativi eseguiti da ogni dispositivo.
- **Gestisci**: scegliere **Tutti i dispositivi** per visualizzare un elenco di tutti i dispositivi gestiti.
    Selezionare uno dei dispositivi nell'elenco per aprire il pannello **Panoramica** di <*nome dispositivo*> , in cui è possibile selezionare una delle opzioni seguenti:
    - **Panoramica**: consente di vedere le informazioni generali sul dispositivo, tra cui le informazioni sul nome e sul proprietario, se si tratta di un dispositivo BYOD, quando è stato archiviato per l'ultima volta e altro. È possibile anche eseguire le seguenti azioni remote sul dispositivo (non tutte le azioni sono supportate da tutte le piattaforme del dispositivo):
        - **Rimuovi i dati aziendali**: consente di rimuovere solo i dati aziendali gestiti da Intune. Non rimuove dal dispositivo i dati personali. Il dispositivo non verrà più gestito da Intune e non sarà più in grado di accedere alle risorse aziendali (non supportata per i dispositivi Windows associati a Azure Active Directory).
        - **Ripristino impostazioni predefinite**: consente di ripristinare le impostazioni predefinite del dispositivo. Vengono rimossi sia i dati aziendali sia i dati personali e il dispositivo non verrà più gestito da Intune. Non è possibile annullare questa azione.
        - **Blocco remoto**: consente di bloccare il dispositivo. Per sbloccarlo, il proprietario del dispositivo deve usare il passcode. È possibile bloccare solo in modalità remota un dispositivo che dispone di un PIN o di una password impostati.
        - **Reimposta passcode**: genera un nuovo passcode per il dispositivo che verrà visualizzato nel pannello **Panoramica** di <*nome dispositivo*> .
        - **Eseguire il bypass del blocco attivazione**: consente di rimuovere il blocco attivazione dai dispositivi iOS senza richiedere Apple ID e password dell'utente. Se è stato eseguito il bypass del blocco attivazione, il dispositivo attiva nuovamente il blocco attivazione quando si avvia l'app Trova il mio iPhone. Eseguire il bypass del blocco attivazione solo se si ha accesso fisico al dispositivo.
        - **Modalità di dispositivo perso**: se un dispositivo è stato rubato, è possibile abilitare la modalità di dispositivo perso. Questa modalità consente di specificare un messaggio e un numero di telefono che verranno visualizzati nella schermata di blocco del dispositivo.
        - **Riavvia**: consente il riavvio del dispositivo. Il proprietario del dispositivo non viene avvisato automaticamente del riavvio, pertanto potrebbe perdere il lavoro.
        ![Panoramica sul dispositivo](http://i.imgur.com/4Rx4VXm.png)
        
    - **Hardware**: consente di vedere informazioni più dettagliate sul dispositivo, tra cui spazio di archiviazione disponibile, modello, produttore e altro.
    ![Inventario hardware dei dispositivi gestiti](./media/hardware-inventory.png)
    - **Applicazioni rilevate**: consente di visualizzare un elenco di tutte le app installate nel dispositivo trovate da Intune.
    ![Nodo applicazioni rilevate](./media/detected-applications.png)
- **Monitoraggio**: scegliere **Azioni del dispositivo** per visualizzare un elenco delle azioni del dispositivo che sono state eseguite su dispositivi gestiti e lo stato corrente di tali azioni.
![Monitorare le azione del dispositivo](./media/monitor-device-actions.png)

