---
# required metadata

title: Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d3aa6c74-6b5d-4b50-aa66-a040ec44393e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: joglocke
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Monitorare i criteri di gestione delle app per dispositivi mobili con Microsoft Intune
Dopo aver configurato un criterio MAM e averlo applicato agli utenti, è possibile monitorare lo stato di conformità nel [portale di Azure](https://portal.azure.com). Il portale di Azure include informazioni sugli utenti interessati dai criteri, sullo stato di conformità e su eventuali problemi che potrebbero riscontrare gli utenti finali.
## Visualizzazione di riepilogo
Nel pannello **Gestione di applicazioni mobili di Intune** è possibile visualizzare un riepilogo dello stato di conformità, come descritto di seguito:


![Riquadro Riepilogo del pannello Gestione di applicazioni mobili di Intune](../media/mam-azure-portal-user-status-summary.png)

-   **UTENTI:** numero totale di utenti dell'azienda che usano le app associate ai criteri.

-   **CRITERI GESTITO DA:** numero di utenti che hanno usato almeno una delle app nel contesto aziendale.

-   **NESSUN CRITERIO:** numero di utenti che usano le app associate ai criteri, ma non sono interessati dai criteri.  È consigliabile aggiungere questi utenti ai criteri.

- **Utenti contrassegnati:** numero di utenti che riscontrano problemi. Al momento in **Utenti contrassegnati** appaiono solo gli utenti con dispositivi jailbroken.


## Visualizzazione dettagliata
Per accedere alla visualizzazione dettagliata del riepilogo, fare clic sul riquadro **Stato utente** e quindi sul riquadro **Utenti contrassegnati**.

### Stato utente
È possibile eseguire la ricerca di un singolo utente e controllare il relativo stato di conformità. Il pannello **Segnalazione app** visualizza le informazioni seguenti per un utente selezionato:
- Dispositivi associati all'account utente
- App con criteri MAM sul dispositivo
- Stato:

  Se l'app è contrassegnata come **archiviata**, significa che il criterio è stato distribuito all'utente e che l'app è stata usata almeno una volta nel contesto aziendale.

  Se l'app è contrassegnata come **non archiviata**, significa che il criterio è stato distribuito all'utente e che l'app a partire da quel momento non è mai stata usata nel contesto aziendale.

Per visualizzare i report generati per un utente, seguire questa procedura:

**Passaggio 1:**  per selezionare un utente, fare clic sul riquadro Riepilogo o scegliere l'opzione **SEGNALAZIONE APP PER UTENTE** nel pannello **Impostazioni** come illustrato di seguito:

![Opzione Segnalazione app nel pannello delle impostazioni](../media/mam-azure-portal-app-reporting-by-user-settings-blade.png)

**Passaggio 2:** viene aperto il pannello **Segnalazione app**. Scegliere **Seleziona utente** per cercare un utente di Azure Active Directory.

![Opzione di selezione utente nel pannello Segnalazione app](../media/mam-azure-portal-app-reporting-select-user.png)

**Passaggio 3:** dopo aver selezionato l'utente dall'elenco, vengono visualizzati i dettagli dello stato di conformità per l'utente.

![Dettagli di Segnalazione app](../media/mam-azure-portal-app-reporting-by-user.png)
### Utenti contrassegnati
Nella visualizzazione dettagliata sono indicati il messaggio di errore, l'app a cui si è eseguito l'accesso quando si è verificato l'errore, la piattaforma del dispositivo e un timestamp.  

### Vedere anche
[Gestire il trasferimento di dati tra app iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md)

[Esperienza utente finale con app con MAM abilitato](end-user-experience-for-mam-enabled-apps-with-microsoft-intune.md)


<!--HONumber=Jun16_HO2-->


