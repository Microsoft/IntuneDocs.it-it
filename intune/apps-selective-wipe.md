---
title: Come cancellare solo i dati aziendali dalle app
titleSuffix: Microsoft Intune
description: Informazioni su come cancellare in modo selettivo i dati aziendali dalle app gestite da Intune con Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cd6ac0b1fdb64897a831c0111f7e0a611c85bede
ms.sourcegitcommit: 513c59a23ca5dfa80a3ba6fc84068503a4158757
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54210704"
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Come cancellare solo i dati aziendali dalle app gestite da Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando un dispositivo viene smarrito o rubato, o se il dipendente lascia l'azienda, è necessario assicurarsi di rimuovere dal dispositivo i dati delle app aziendali. Ma potrebbe essere necessario mantenere i dati personali sul dispositivo, soprattutto se si tratta di un dispositivo di proprietà del dipendente.

>[!NOTE]
> Le piattaforme iOS e Android sono le due piattaforme attualmente supportate per la cancellazione dei dati aziendali da app gestite da Intune. Le app gestite da Intune sono applicazioni che includono Intune APP SDK e dispongono di un account utente con licenza per l’organizzazione. La distribuzione dei criteri di protezione dell'applicazione non è necessaria per abilitare la cancellazione selettiva delle app.

Per rimuovere selettivamente i dati delle app aziendali, creare una richiesta di cancellazione attenendosi alla procedura descritta in questo argomento. Al termine della richiesta, i dati aziendali verranno rimossi dall'app alla successiva esecuzione dell'app nel dispositivo. Oltre alla creazione di una richiesta di cancellazione, è possibile configurare una cancellazione selettiva dei dati dell'organizzazione come nuova azione quando non sono soddisfatte le condizioni delle impostazioni di accesso previste dai criteri di protezione delle applicazioni. Questa funzionalità consente di proteggere e rimuovere automaticamente dalle applicazioni i dati sensibili dell'organizzazione in base a criteri configurati in precedenza.

>[!IMPORTANT]
> I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Creare una richiesta di cancellazione

1.  Accedere al [portale di Azure](https://portal.azure.com).

2.  Scegliere **Tutti i servizi**, digitare **Intune** nella casella di testo di filtro e selezionare **Intune**. Viene aperto il riquadro di Intune. Scegliere il riquadro **App client**.

    ![Screenshot del riquadro di Microsoft Intune](./media/apps-selective-wipe01.png)

3.  Nel **riquadro app client** scegliere **Cancellazione selettiva di app**.

4.  Scegliere **Nuova richiesta di cancellazione dati**. Si apre il riquadro **Nuova richiesta di cancellazione dati**.

    ![Schermata del riquadro Nuova richiesta di cancellazione dati](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Scegliere un utente e quindi scegliere **Seleziona** per selezionare l'utente di cui si vogliono cancellare i dati delle app.

6.  Scegliere quindi **Dispositivo** nel riquadro **Nuova richiesta di cancellazione dati**. Verrà aperto il riquadro **Seleziona dispositivo** che elenca tutti i dispositivi associati all'utente selezionato e include anche due colonne, ovvero il nome del dispositivo, che è un nome descrittivo definito dall'utente, e il tipo di dispositivo, che specifica la piattaforma del dispositivo. Selezionare il dispositivo da cancellare.

7.  Verrà visualizzato nuovamente il riquadro **Nuova richiesta di cancellazione dati**. Scegliere **OK** per eseguire una richiesta di cancellazione.

Il servizio crea e tiene traccia di una richiesta di cancellazione dati separata per ogni app protetta nel dispositivo e dell'utente associato alla richiesta di cancellazione dati.

## <a name="monitor-your-wipe-requests"></a>Monitorare le richieste di cancellazione dati

È possibile avere un report di riepilogo che mostra lo stato generale della richiesta di cancellazione dati e indica il numero di richieste in sospeso ed errori. Per ottenere ulteriori dettagli, seguire questa procedura:

1.  Nel riquadro **App client - Cancellazione selettiva di app** è possibile visualizzare l'elenco delle richieste raggruppate in base agli utenti. Dal momento che il sistema crea una richiesta di cancellazione dati per ciascuna applicazione protetta in esecuzione nel dispositivo, è possibile visualizzare più richieste per un utente. Lo stato indica se una richiesta di cancellazione dati è **in sospeso**, **non riuscita** o **completata**.

    ![Screenshot dello stato della richiesta di cancellazione dati nel pannello Cancellazione selettiva di app](./media/wipe-request-status-1.png)

Sarà anche possibile visualizzare il nome e il tipo del dispositivo, utili durante la lettura dei report.

>[!IMPORTANT]
> L'utente deve aprire l'app affinché venga eseguita la cancellazione dati e l'operazione può richiedere fino a 30 minuti dopo la richiesta.

## <a name="delete-a-wipe-request"></a>Eliminare una richiesta di cancellazione dati

Le cancellazioni dati con stato in sospeso rimangono visualizzate fino all'eliminazione manuale. Per eliminare manualmente una richiesta di cancellazione dati:

1.  Nel riquadro **App client - Cancellazione selettiva di app**.

2.  Nell'elenco fare clic con il pulsante destro del mouse sulla richiesta di cancellazione dati da eliminare e quindi scegliere **Elimina richiesta di cancellazione dati**.

    ![Screenshot dell'elenco di richieste di cancellazione dati nel riquadro Cancellazione selettiva di app](./media/delete-wipe-request.png)

3.  Viene chiesto di confermare l'eliminazione, scegliere **Sì** o **No**, quindi fare clic su **OK**.

### <a name="see-also"></a>Vedere anche
[Che cos'è un criterio di protezione delle app?](app-protection-policy.md)

[Che cos'è la gestione delle app?](app-management.md)
