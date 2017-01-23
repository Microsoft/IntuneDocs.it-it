---
title: Monitorare i criteri MAM con Microsoft Intune | Documentazione Microsoft
description: Vedere quanti utenti dispongono di criteri ed eseguire il drill-down per accedere ad altri dettagli.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9e208608d50c9b5f7fe66743de0d3c7e741dbfbd
ms.openlocfilehash: 2a18ad7226c6fc6de0277f1f20443ea64dc8b918


---

# <a name="monitor-mobile-app-management-policies-with-microsoft-intune"></a>Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Dopo aver configurato un criterio di gestione delle app mobili (MAM) e averlo applicato agli utenti, è possibile monitorare lo stato di conformità nel [portale di Azure](https://portal.azure.com). Il portale di Azure include informazioni sugli utenti interessati dai criteri, sullo stato di conformità e su eventuali problemi che potrebbero riscontrare gli utenti.
## <a name="summary-view"></a>Visualizzazione di riepilogo
Nel pannello **Gestione di applicazioni mobili di Intune** è possibile visualizzare un riepilogo dello stato di conformità:


![Riquadro Riepilogo del pannello Gestione di applicazioni mobili di Intune](../media/mam-azure-portal-user-status-summary.png)

-   **Utenti**: numero totale di utenti dell'azienda che usano le app associate ai criteri.

-   **Criteri Gestito da**: numero di utenti che hanno usato almeno una delle app nel contesto aziendale.

-   **Nessun criterio**: numero di utenti che usano le app associate ai criteri, ma non sono interessati dai criteri. È consigliabile aggiungere questi utenti ai criteri.

- **Utenti contrassegnati**: numero di utenti che riscontrano problemi. Al momento, in **Utenti contrassegnati** vengono indicati solo gli utenti con dispositivi jailbroken.


## <a name="detailed-view"></a>Visualizzazione dettagliata
Per accedere alla visualizzazione dettagliata del riepilogo, scegliere il riquadro **Stato utente** e il riquadro **Utenti contrassegnati**.

### <a name="user-status"></a>Stato utente
È possibile eseguire la ricerca di un singolo utente e controllare il relativo stato di conformità. Il pannello **Segnalazione app** mostra le informazioni seguenti per un utente selezionato:
- Dispositivi associati all'account utente

- App con criteri MAM nel dispositivo

- Stato:

  - **Archiviazione eseguita**: il criterio è stato distribuito all'utente e l'app è stata usata almeno una volta nel contesto aziendale.

  - **Archiviazione non eseguita**: il criterio è stato distribuito all'utente, ma l'app non è stata usata nel contesto aziendale da quel momento.

>[!NOTE]
> Se per l'utente cercato non è stato distribuito il criterio MAM, verrà visualizzato un messaggio che informa che l'utente non è assegnato ad alcun criterio dell'app.

Per visualizzare i report generati per un utente, seguire questa procedura:

1.  Per selezionare un utente, scegliere il riquadro **Riepilogo** o scegliere l'opzione **Segnalazione app per utente** nel pannello **Impostazioni**:

    ![Opzione Segnalazione app nel pannello Impostazioni](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

2. Nel pannello **Segnalazione app** che viene aperto scegliere **Seleziona utente** per cercare un utente di Azure Active Directory.

    ![Opzione Selezione utente nel pannello Segnalazione app](../media/mam-azure-portal-app-reporting-select-user.png)

3. Selezionare un utente nell'elenco. Verranno visualizzati i dettagli dello stato di conformità per l'utente.

    ![Dettagli di Segnalazione app](../media/mam-azure-portal-app-reporting-by-user.png)

### <a name="flagged-users"></a>Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del dispositivo e un timestamp.  

### <a name="see-also"></a>Vedere anche
[Gestire il trasferimento di dati tra app iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

* [Aspettative dalla gestione dell'app per Android con criteri MAM](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
* [Aspettative dalla gestione dell'app per iOS con criteri MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)



<!--HONumber=Dec16_HO3-->


