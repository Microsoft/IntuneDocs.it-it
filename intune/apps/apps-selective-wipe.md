---
title: Come cancellare solo i dati aziendali dalle app
titleSuffix: Microsoft Intune
description: Informazioni su come cancellare in modo selettivo i dati aziendali dalle app gestite da Intune con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e827075b56d1751e837c25d85c304201bcafa01
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/22/2019
ms.locfileid: "74390401"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Come cancellare solo i dati aziendali dalle app gestite da Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Quando un dispositivo viene smarrito o rubato, o se il dipendente lascia l'azienda, è necessario assicurarsi di rimuovere dal dispositivo i dati delle app aziendali. Ma potrebbe essere necessario mantenere i dati personali sul dispositivo, soprattutto se si tratta di un dispositivo di proprietà del dipendente.

>[!NOTE]
> Le piattaforme iOS, Android e Windows 10 sono le uniche piattaforme attualmente supportate per la cancellazione dei dati aziendali da app gestite da Intune. Le app gestite da Intune sono applicazioni che includono Intune APP SDK e dispongono di un account utente con licenza per l’organizzazione. La distribuzione dei criteri di protezione dell'applicazione non è necessaria per abilitare la cancellazione selettiva delle app.

Per rimuovere selettivamente i dati delle app aziendali, creare una richiesta di cancellazione attenendosi alla procedura descritta in questo argomento. Al termine della richiesta, i dati aziendali verranno rimossi dall'app alla successiva esecuzione dell'app nel dispositivo. Oltre alla creazione di una richiesta di cancellazione, è possibile configurare una cancellazione selettiva dei dati dell'organizzazione come nuova azione quando non sono soddisfatte le condizioni delle impostazioni di accesso previste dai criteri di protezione delle applicazioni. Questa funzionalità consente di proteggere e rimuovere automaticamente dalle applicazioni i dati sensibili dell'organizzazione in base a criteri configurati in precedenza.

>[!IMPORTANT]
> I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook.

## <a name="deployed-wip-policies-without-user-enrollment"></a>Criteri WIP distribuiti senza registrazione dell'utente
I criteri di Windows Information Protection (WIP) possono essere distribuiti senza richiedere agli utenti MDM di registrare il dispositivo Windows 10. Questa configurazione non solo consente alle società di proteggere i documenti aziendali in base alla configurazione WIP, ma permette anche agli utenti di continuare a gestire i dispositivi Windows. Quando i documenti sono protetti da un criterio WIP, i dati protetti possono essere cancellati in modo selettivo da un amministratore di Intune. Selezionando l'utente e il dispositivo e inviando una richiesta di cancellazione, tutti i dati protetti tramite i criteri WIP non saranno più utilizzabili. Da Intune nel portale di Azure selezionare **App client** > **Cancellazione selettiva di app**. Per altre informazioni, vedere [Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune](windows-information-protection-policy-create.md).

## <a name="create-a-wipe-request"></a>Creare una richiesta di cancellazione

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Nel riquadro Intune selezionare **App client** > **Cancellazione selettiva di app** > **Crea una richiesta di cancellazione dati**.<br>
   Viene visualizzato il riquadro **Crea una richiesta di cancellazione dati**.
3. Fare clic su **Selezionare l'utente**, scegliere l'utente per cui si vogliono cancellare i dati dell'app e fare clic su **Seleziona** nella parte inferiore del riquadro **Selezionare l'utente**.

    ![Screenshot del riquadro "Selezionare l'utente"](./media/apps-selective-wipe/apps-selective-wipe-01.png)

4. Fare clic su **Selezionare il dispositivo**, scegliere il dispositivo e fare clic su **Seleziona** nella parte inferiore del riquadro **Seleziona dispositivo**.

    ![Screenshot del riquadro "Crea una richiesta di cancellazione dati" in cui selezionare il dispositivo](./media/apps-selective-wipe/apps-selective-wipe-02.png)

5. Fare clic su **Crea** per generare una richiesta di cancellazione.

Il servizio crea e tiene traccia di una richiesta di cancellazione dati separata per ogni app protetta nel dispositivo e dell'utente associato alla richiesta di cancellazione dati.

   ![Screenshot del riquadro "App client - Cancellazione selettiva di app"](./media/apps-selective-wipe/apps-selective-wipe-03.png)

## <a name="monitor-your-wipe-requests"></a>Monitorare le richieste di cancellazione dati

È possibile avere un report di riepilogo che mostra lo stato generale della richiesta di cancellazione dati e indica il numero di richieste in sospeso ed errori. Per ottenere ulteriori dettagli, seguire questa procedura:

1. Nel riquadro **App client** > **Cancellazione selettiva di app** è possibile visualizzare l'elenco delle richieste raggruppate in base agli utenti. Dal momento che il sistema crea una richiesta di cancellazione dati per ciascuna applicazione protetta in esecuzione nel dispositivo, è possibile visualizzare più richieste per un utente. Lo stato indica se una richiesta di cancellazione dati è **in sospeso**, **non riuscita** o **completata**.

    ![Screenshot dello stato della richiesta di cancellazione dati nel pannello Cancellazione selettiva di app](./media/apps-selective-wipe/wipe-request-status-1.png)

Sarà anche possibile visualizzare il nome e il tipo del dispositivo, utili durante la lettura dei report.

>[!IMPORTANT]
> L'utente deve aprire l'app affinché venga eseguita la cancellazione dati e l'operazione può richiedere fino a 30 minuti dopo la richiesta.

## <a name="delete-a-wipe-request"></a>Eliminare una richiesta di cancellazione dati

Le cancellazioni dati con stato in sospeso rimangono visualizzate fino all'eliminazione manuale. Per eliminare manualmente una richiesta di cancellazione dati:

1. Nel riquadro **App client - Cancellazione selettiva di app**.

2. Nell'elenco fare clic con il pulsante destro del mouse sulla richiesta di cancellazione dati da eliminare e quindi scegliere **Elimina richiesta di cancellazione dati**.

    ![Screenshot dell'elenco di richieste di cancellazione dati nel riquadro Cancellazione selettiva di app](./media/apps-selective-wipe/delete-wipe-request.png)

3. Viene chiesto di confermare l'eliminazione, scegliere **Sì** o **No**, quindi fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
[Che cos'è un criterio di protezione delle app?](app-protection-policy.md)

[Che cos'è la gestione delle app?](app-management.md)
