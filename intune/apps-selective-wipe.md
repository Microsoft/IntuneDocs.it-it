---
title: Come cancellare solo i dati aziendali dalle app
titleSuffix: Microsoft Intune
description: Informazioni sulla cancellazione selettiva di app in Microsoft Intune.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dfd1b37c1b944a545234b93b44d651ead8f0f486
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Come cancellare solo i dati aziendali dalle app gestite da Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Quando un dispositivo viene smarrito o rubato, o se il dipendente lascia l'azienda, è necessario assicurarsi di rimuovere dal dispositivo i dati delle app aziendali. Ma potrebbe essere necessario mantenere i dati personali sul dispositivo, soprattutto se si tratta di un dispositivo di proprietà del dipendente.

>[!NOTE]
> Le piattaforme iOS e Android sono le due piattaforme attualmente supportate per la cancellazione dei dati aziendali da app gestite da Intune.

Per rimuovere selettivamente i dati delle app aziendali, creare una richiesta di cancellazione attenendosi alla procedura descritta in questo argomento. Al termine della richiesta, i dati aziendali verranno rimossi dall'app alla successiva esecuzione dell'app nel dispositivo.

>[!IMPORTANT]
> I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Creare una richiesta di cancellazione

1.  Accedere al [portale di Azure](https://portal.azure.com).

2.  Scegliere **Altri servizi**, digitare **Intune** nella casella di testo filtro e selezionare **Intune**. Viene aperto il pannello di Intune. Scegliere **App per dispositivi mobili**.

    ![Screenshot del pannello di Microsoft Intune](./media/apps-selective-wipe01.png)

3.  Nel **pannello App per dispositivi mobili** scegliere **Cancellazione selettiva di app**.

4.  Scegliere **Nuova richiesta di cancellazione dati**. Si apre il riquadro **Nuova richiesta di cancellazione dati**.

    ![Schermata del riquadro Nuova richiesta di cancellazione dati](./media/AzurePortal_MAM_NewWipeRequest.png)

5.  Scegliere **Utente** per aprire il pannello **Utente** e selezionare l'utente di cui cancellare i dati dell'app.

6.  Scegliere quindi **Dispositivo** dal pannello **Nuova richiesta di cancellazione dati**. In seguito a questa azione viene aperto il pannello **Selezionare un dispositivo**. Nel pannello vengono elencati tutti i dispositivi associati all'utente selezionato. Vengono anche specificati il nome del dispositivo, ovvero un nome descrittivo definito dall'utente, e il tipo di dispositivo, che ne specifica la piattaforma. 

7. Selezionare dall'elenco il dispositivo da cui cancellare i dati.

8.  Verrà visualizzato nuovamente il riquadro **Nuova richiesta di cancellazione dati**. Scegliere **OK** per eseguire una richiesta di cancellazione.

Il servizio crea e tiene traccia di una richiesta di cancellazione dati separata per ogni app protetta nel dispositivo e dell'utente associato alla richiesta di cancellazione dati.

## <a name="monitor-your-wipe-requests"></a>Monitorare le richieste di cancellazione dati

È possibile avere un report di riepilogo che mostra lo stato generale della richiesta di cancellazione dati e indica il numero di richieste in sospeso ed errori. Per ottenere ulteriori dettagli, seguire questa procedura:

1.  Nel pannello **App per dispositivi mobili - Cancellazione selettiva di app** è possibile visualizzare l'elenco delle richieste raggruppate in base agli utenti. Dal momento che il sistema crea una richiesta di cancellazione dati per ciascuna applicazione protetta in esecuzione nel dispositivo, è possibile visualizzare più richieste per un utente. Lo stato indica se una richiesta di cancellazione dati è **in sospeso**, **non riuscita** o **completata**.

    ![Screenshot dello stato della richiesta di cancellazione dati nel pannello Cancellazione selettiva di app](./media/wipe-request-status-1.png)

Sarà anche possibile visualizzare il nome e il tipo del dispositivo, utili durante la lettura dei report.

>[!IMPORTANT]
> L'utente deve aprire l'app affinché venga eseguita la cancellazione dati e l'operazione può richiedere fino a 30 minuti dopo la richiesta.

## <a name="delete-a-wipe-request"></a>Eliminare una richiesta di cancellazione dati

Le cancellazioni dati con stato in sospeso rimangono visualizzate fino all'eliminazione manuale. Per eliminare manualmente una richiesta di cancellazione dati:

1.  Aprire il pannello **App per dispositivi mobili - Cancellazione selettiva di app**.

2.  Nell'elenco fare clic con il pulsante destro del mouse sulla richiesta di cancellazione dati da eliminare e quindi scegliere **Elimina richiesta di cancellazione dati**.

    ![Screenshot dell'elenco di richieste di cancellazione dati nel riquadro Cancellazione selettiva di app](./media/delete-wipe-request.png)

3.  Viene chiesto di confermare l'eliminazione, scegliere **Sì** o **No**, quindi fare clic su **OK**.

### <a name="see-also"></a>Vedere anche
[Che cos'è un criterio di protezione delle app?](app-protection-policy.md)

[Che cos'è la gestione delle app?](app-management.md)
