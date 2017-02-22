---
title: Come cancellare solo i dati aziendali dalle app | Anteprima di Intune in Azure | Documentazione Microsoft
description: "Anteprima di Intune in Azure: informazioni sulle modalità di cancellazione selettiva delle app con Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 02/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42605e6e-5b84-44ff-b86e-346ea123b53e
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 44aefa68761236b946f5ab1db678ecc4aa81e92b
ms.openlocfilehash: ab2f9d065a1c4b0e0a016ff6195742cd09965191

---

# <a name="how-to-wipe-only-corporate-data-from-intune-managed-apps"></a>Come cancellare solo i dati aziendali dalle app gestite da Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Quando un dispositivo viene smarrito o rubato, o se il dipendente lascia l'azienda, è necessario assicurarsi di rimuovere dal dispositivo i dati delle app aziendali. Ma potrebbe essere necessario non rimuovere i dati personali sul dispositivo, soprattutto se si tratta di un dispositivo di proprietà del dipendente.

Per rimuovere selettivamente i dati delle app aziendali, creare una richiesta di cancellazione attenendosi alla procedura descritta in questo argomento. Al termine della richiesta, i dati aziendali verranno rimossi dall'app alla successiva esecuzione dell'app nel dispositivo.

>[!IMPORTANT]
> I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Creare una richiesta di cancellazione

1.  Accedere al [portale di Azure](https://portal.azure.com).

2.  Scegliere **Altri servizi**, digitare **Intune** nella casella di testo filtro e selezionare **Intune**. Si apre il pannello di anteprima di Intune, scegliere il pannello **Gestisci le app**.

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/intune-azure-preview-blade.png)

3.  Nel **pannello App per dispositivi mobili** scegliere **Nuova richiesta di cancellazione dati**. Si apre il pannello **Nuova richiesta di cancellazione dati**.

4.  Scegliere **Nuova richiesta di cancellazione dati**. Si apre il pannello **Nuova richiesta di cancellazione dati**.

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/AzurePortal_MAM_NewWipeRequest.png)

5.  Scegliere **Utente** per aprire il pannello **Utente** e selezionare l'utente di cui cancellare i dati dell'app.

6.  Scegliere **Dispositivo**. Si apre il pannello **Dispositivo**, che elenca tutti i dispositivi associati all'utente selezionato e fornisce anche due colonne: nome del dispositivo, che è un nome descrittivo definito dall'utente, e tipo di dispositivo, che specifica la piattaforma del dispositivo. Selezionare il dispositivo da cancellare.

7.  Verrà visualizzato nuovamente il riquadro **Nuova richiesta di cancellazione dati**. Scegliere **OK** per eseguire una richiesta di cancellazione. 

Il servizio crea e tiene traccia di una richiesta di cancellazione dati separata per ogni app protetta nel dispositivo e dell'utente associato alla richiesta di cancellazione dati.

## <a name="monitor-your-wipe-requests"></a>Monitorare le richieste di cancellazione dati

È possibile avere un report di riepilogo che mostra lo stato generale della richiesta di cancellazione dati e indica il numero di richieste in sospeso ed errori. Per ottenere ulteriori dettagli, seguire questa procedura:

1.  Nel pannello **Mobile Apps - App Selective Wipe** (App per dispositivi mobili - Cancellazione selettiva di app) è possibile visualizzare l'elenco delle richieste raggruppate in base agli utenti. Dal momento che il sistema crea una richiesta di cancellazione dati per ciascuna applicazione protetta in esecuzione nel dispositivo, è possibile visualizzare più richieste per un utente. Lo stato indica se una richiesta di cancellazione dati è **in sospeso**, **non riuscita** o **completata**.

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/wipe-request-status-1.png)

Sarà anche possibile visualizzare nome del dispositivo e tipo di dispositivo, utili durante la lettura dei report.

>[!IMPORTANT]
> L'utente deve aprire l'app affinché venga eseguita la cancellazione dati e l'operazione può richiedere fino a 30 minuti dopo la richiesta.

## <a name="delete-a-wipe-request"></a>Eliminare una richiesta di cancellazione dati

Le cancellazioni dati con stato in sospeso rimangono visualizzate fino all'eliminazione manuale.  Per eliminare manualmente una richiesta di cancellazione dati:

1.  Nel pannello **Richiesta di cancellazione dati** scegliere il riquadro **Richiesta di cancellazione dati** per aprire il pannello **Richiesta di cancellazione dati**.

2.  Fare clic con il pulsante destro del mouse sulla richiesta di cancellazione dati da eliminare, quindi scegliere **Delete wipe request** (Elimina richiesta di cancellazione dati).

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/delete-wipe-request.png)

3.  Viene chiesto di confermare l'eliminazione, scegliere **Sì** o **No**, quindi fare clic su **OK**.

### <a name="see-also"></a>Vedere anche
[Che cos'è un criterio di protezione delle app?](what-is-app-protection-policy.md)

[Che cos'è la gestione delle app?](what-is-app-management.md)


<!--HONumber=Feb17_HO2-->


