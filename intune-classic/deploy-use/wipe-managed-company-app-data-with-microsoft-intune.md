---
title: Cancellare i dati dell'app aziendale gestita
description: "Informazioni su come è possibile rimuovere selettivamente i dati aziendali dai dispositivi in modalità remota."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2742e1d5-d2d5-42cd-b719-665dd6e0a0e9
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d7f89d79edcc52892e2988e4b2f152cb68d80070
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="wipe-company-app-data-with-intune-mam"></a>Cancellare i dati delle app aziendali con MAM di Intune.

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Quando un dispositivo viene smarrito o rubato, o se il dipendente lascia l'azienda, è necessario assicurarsi di rimuovere dal dispositivo i dati delle app aziendali. Ma potrebbe essere necessario non rimuovere i dati personali sul dispositivo, soprattutto se si tratta di un dispositivo di proprietà del dipendente.

Per rimuovere selettivamente i dati delle app aziendali, creare una richiesta di cancellazione attenendosi alla procedura descritta in questo argomento. Al termine della richiesta, i dati aziendali verranno rimossi dall'app alla successiva esecuzione dell'app nel dispositivo.

>[!IMPORTANT]
> I contatti sincronizzati direttamente dall'app alla Rubrica nativa vengono rimossi. Tutti i contatti sincronizzati dalla Rubrica nativa a un'altra origine esterna non possono essere cancellati. Attualmente questa opzione è disponibile solo per l'app Microsoft Outlook.

## <a name="create-a-wipe-request"></a>Creare una richiesta di cancellazione

1.  Accedere al [portale di Azure](https://portal.azure.com).

2.  Scegliere **Altri servizi**, digitare **Intune** nella casella di testo filtro e selezionare **Protezione app di Intune**. Si apre il pannello Gestione di applicazioni mobili di Intune.

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/AppManagement/wipe-request-mam-main-blade.png)

2.  Nel pannello **Impostazioni** scegliere **Richieste di cancellazione dati**.

3.  Scegliere **Nuova richiesta di cancellazione dati**. Si apre il pannello **Nuova richiesta di cancellazione dati**.

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/AppManagement/AzurePortal_MAM_NewWipeRequest.png)

4.  Scegliere **Utente** per aprire il pannello **Utente** e selezionare l'utente di cui cancellare i dati dell'app.

5.  Scegliere **Dispositivo**. Si apre il pannello **Dispositivo**, che elenca tutti i dispositivi associati all'utente selezionato e fornisce anche due colonne: nome del dispositivo, che è un nome descrittivo definito dall'utente, e tipo di dispositivo, che specifica la piattaforma del dispositivo. Selezionare il dispositivo da cancellare.

6.  Verrà visualizzato nuovamente il riquadro **Nuova richiesta di cancellazione dati**. Scegliere **OK** per eseguire una richiesta di cancellazione. 

Il servizio crea e tiene traccia di una richiesta di cancellazione dati separata per ogni app protetta nel dispositivo e dell'utente associato alla richiesta di cancellazione dati.

>[!NOTE]
> È possibile anche creare **Richieste di cancellazione dati** facendo clic sul **riquadro Richiesta di cancellazione dati** dal pannello di gestione delle applicazioni mobili di Intune.

## <a name="monitor-your-wipe-requests"></a>Monitorare le richieste di cancellazione dati

È possibile avere un report di riepilogo che mostra lo stato generale della richiesta di cancellazione dati e indica il numero di richieste in sospeso ed errori. Per ottenere ulteriori dettagli, seguire questa procedura:

1.  Nel pannello di gestione delle applicazioni mobili di Intune fare clic sul riquadro **Richieste di cancellazione dati**.

2.  Nel pannello **Richiesta di cancellazione dati** scegliere il riquadro **Richiesta di cancellazione dati** per aprire il pannello **Richiesta di cancellazione dati**.

3.  Nel pannello **Richiesta di cancellazione dati** è possibile visualizzare l'elenco delle richieste raggruppate in base agli utenti. Dal momento che il sistema crea una richiesta di cancellazione dati per ciascuna applicazione protetta in esecuzione nel dispositivo, è possibile visualizzare più richieste per un utente. Lo stato indica se una richiesta di cancellazione dati è **in sospeso**, **non riuscita** o **completata**.

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/AppManagement/wipe-request-status-1.png)

Sarà anche possibile visualizzare nome del dispositivo e tipo di dispositivo, utili durante la lettura dei report.

>[!IMPORTANT]
> L'utente deve aprire l'app affinché venga eseguita la cancellazione dati e l'operazione può richiedere fino a 30 minuti dopo la richiesta.

## <a name="delete-a-wipe-request"></a>Eliminare una richiesta di cancellazione dati

Le cancellazioni dati con stato in sospeso rimangono visualizzate fino all'eliminazione manuale.  Per eliminare manualmente una richiesta di cancellazione dati

1.  Nel pannello di gestione delle applicazioni mobili di Intune fare clic sul riquadro **Richieste di cancellazione dati**.

2.  Nel pannello **Richiesta di cancellazione dati** scegliere il riquadro **Richiesta di cancellazione dati** per aprire il pannello **Richiesta di cancellazione dati**.

3.  Fare clic con il pulsante destro del mouse sulla richiesta di cancellazione dati da eliminare, quindi scegliere **Delete wipe request** (Elimina richiesta di cancellazione dati).

    ![Schermata del pannello Nuova richiesta di cancellazione dati](../media/AppManagement/delete-wipe-request.png)

4.  Viene chiesto di confermare l'eliminazione, scegliere **Sì** o **No**, quindi fare clic su **OK**.


### <a name="see-also"></a>Vedere anche
[Proteggere i dati delle app usando i criteri di gestione delle app mobili](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)

[Uso del portale di Azure](azure-portal-for-microsoft-intune-mam-policies.md)
