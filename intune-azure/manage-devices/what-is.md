---
title: Gestire i dispositivi con Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come visualizzare i dispositivi gestiti con Intune ed eseguire diverse operazioni su tali dispositivi.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/14/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: b6c245d60c661c04b4c4d29c9bdcdd752254d978
ms.openlocfilehash: 957192c744bf05cd835dfae60b6bb521b8f8b26b
ms.lasthandoff: 03/15/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>Informazioni sulla gestione dei dispositivi in Microsoft Intune 


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Il carico di lavoro **Dispositivi** offre informazioni dettagliate sui dispositivi gestiti e consente di eseguire attività remote su tali dispositivi. Per accedere al carico di lavoro:

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.

A questo punto, scegliere una delle opzioni seguenti:

- **Panoramica**: ottenere informazioni sui dispositivi registrati e sui sistemi operativi eseguiti da ogni dispositivo.
- **Gestisci**: scegliere **Tutti i dispositivi** per visualizzare un elenco di tutti i dispositivi gestiti.
    Selezionare uno dei dispositivi nell'elenco per aprire il pannello **Panoramica** di <*nome dispositivo*> , in cui è possibile selezionare una delle opzioni seguenti:
    - **Panoramica**: consente di vedere le informazioni generali sul dispositivo, tra cui le informazioni sul nome e sul proprietario, se si tratta di un dispositivo BYOD, quando è stato archiviato per l'ultima volta e altro. 
                
    - **Hardware**: consente di vedere informazioni più dettagliate sul dispositivo, tra cui spazio di archiviazione disponibile, modello, produttore e altro.
    ![Inventario hardware dei dispositivi gestiti](./media/hardware-inventory.png)
    - **Applicazioni rilevate**: consente di visualizzare un elenco di tutte le app installate nel dispositivo trovate da Intune.
    ![Nodo applicazioni rilevate](./media/detected-applications.png)
- **Monitoraggio**: scegliere **Azioni del dispositivo** per visualizzare un elenco delle azioni del dispositivo che sono state eseguite su dispositivi gestiti e lo stato corrente di tali azioni.
![Monitorare le azioni del dispositivo](./media/monitor-device-actions.png)
- **Guida e supporto tecnico**: visualizza i collegamenti alla documentazione di supporto e risoluzione dei problemi.

## <a name="available-device-actions"></a>Azioni del dispositivo disponibili

È possibile anche eseguire le seguenti azioni remote sul dispositivo (non tutte le azioni sono supportate da tutte le piattaforme del dispositivo):

### <a name="remove-company-data"></a>**Rimuovi i dati aziendali**
Rimuove solo i dati aziendali gestiti da Intune. Non rimuove dal dispositivo i dati personali. Il dispositivo non verrà più gestito da Intune e non sarà più in grado di accedere alle risorse aziendali (non supportata per i dispositivi Windows associati a Azure Active Directory).

### <a name="factory-reset"></a>**Ripristino impostazioni predefinite**
Ripristina le impostazioni predefinite del dispositivo. Vengono rimossi sia i dati aziendali sia i dati personali e il dispositivo non verrà più gestito da Intune. Non è possibile annullare questa azione.

### <a name="remote-lock"></a>**Blocco remoto**
Blocca il dispositivo. Per sbloccarlo, il proprietario del dispositivo deve usare il passcode. È possibile bloccare solo in modalità remota un dispositivo che dispone di un PIN o di una password impostati.

### <a name="reset-passcode"></a>**Reimposta passcode**
Genera un nuovo passcode per il dispositivo che verrà visualizzato nel pannello <*nome dispositivo*> **Panoramica**.

### <a name="bypass-activation-lock"></a>**Eseguire il bypass del blocco attivazione**
Rimuove il blocco attivazione da un dispositivo iOS senza richiedere l'Apple ID e la password dell'utente. Se è stato eseguito il bypass del blocco attivazione, il dispositivo attiva nuovamente il blocco attivazione quando si avvia l'app Trova il mio iPhone. Eseguire il bypass del blocco attivazione solo se si ha accesso fisico al dispositivo.

### <a name="lost-mode"></a>**Modalità di dispositivo perso**
Se un dispositivo iOS è stato rubato o smarrito, è possibile abilitare la modalità di dispositivo perso. Questa modalità consente di specificare un messaggio e un numero di telefono che verranno visualizzati nella schermata di blocco del dispositivo. A tale scopo, eseguire questa procedura:
1.    Nel pannello delle proprietà di un dispositivo iOS, scegliere **Altro** > **Modalità di dispositivo perso**.
2.    Nel pannello **Modalità di dispositivo perso** abilitare questa modalità, immettere il messaggio che verrà visualizzato e, facoltativamente, indicare un numero di telefono di contatto.
3.    Fare clic su **OK**.
Quando si abilita la modalità di dispositivo perso, si blocca qualsiasi uso del dispositivo. L'utente finale non può accedere al dispositivo finché l'amministratore non disabilita questa modalità. Quando la modalità di dispositivo perso è abilitata, è possibile usare l'azione **Individua il dispositivo** per scoprire dove si trova il dispositivo.

### <a name="locate-device"></a>**Individua il dispositivo**
Usare questa azione remota per visualizzare su una mappa la posizione di un dispositivo iOS rubato o smarrito. Il dispositivo deve essere un dispositivo iOS di proprietà dell'azienda in cui è attiva la modalità con supervisione. Prima di usare questa azione, è necessario abilitare la modalità di dispositivo perso.
1.    Nel pannello delle proprietà di un dispositivo iOS, scegliere **Altro** > **Individua il dispositivo**.
2.    Dopo che il dispositivo è stato trovato, la relativa posizione viene visualizzata nel pannello **Individua il dispositivo**. 
    ![Pannello Individua il dispositivo](./media/locate-device.png)

### <a name="restart"></a>**Riavvia**
Causa il riavvio del dispositivo. Il proprietario del dispositivo non viene avvisato automaticamente del riavvio, pertanto potrebbe perdere il lavoro.


## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informazioni su privacy e sicurezza per le azioni Modalità di dispositivo perso e Individua il dispositivo
- Non vengono inviate informazioni sulla posizione del dispositivo a Intune finché non si attiva questa azione.
- Quando si usa l'azione Individua il dispositivo, le coordinate di latitudine e longitudine del dispositivo vengono inviate a Intune e visualizzate nel portale di Azure.
- I dati vengono archiviati per 24 ore e quindi rimossi. Non è possibile rimuoverli manualmente.
- I dati relativi alla posizione sono crittografati, sia durante il periodo di archiviazione sia quando vengono trasmessi.
- Quando si configura la modalità di dispositivo perso, nel messaggio da visualizzare nella schermata di blocco è opportuno fornire informazioni riguardo alla possibilità di determinare la posizione del dispositivo.

