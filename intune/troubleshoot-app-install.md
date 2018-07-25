---
title: Risolvere i problemi di installazione delle app
titlesuffix: Microsoft Intune
description: Usare il riquadro Risoluzione dei problemi di Microsoft Intune per facilitare la risoluzione dei problemi di installazione delle app.
keywords: ''
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 07/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
ms.custom: intune-azure
ms.openlocfilehash: c1c2a37103f8fedc09a70b4387aae3f472dfb636
ms.sourcegitcommit: dc8b6f802cca7895a19ec38bec283d4b3150d213
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39138680"
---
# <a name="troubleshoot-app-installation-issues"></a>Risolvere i problemi di installazione delle app

Nei dispositivi gestiti da MDM di Microsoft Intune le installazioni di applicazioni in alcuni casi possono non riuscire. Quando le installazioni di queste app hanno esito negativo, può essere difficile capire il motivo dell'errore o risolvere il problema. Microsoft Intune offre dettagli sugli errori di installazione delle app che consentono agli operatori di help desk e agli amministratori di Intune di visualizzare informazioni sulle app in per rispondere alle richieste degli utenti. Il riquadro di risoluzione dei problemi all'interno di Intune fornisce dettagli sull'errore, incluse informazioni dettagliate sulle app gestite nel dispositivo dell'utente. Per ogni singolo dispositivo sono disponibili informazioni dettagliate sul ciclo di vita completo di un'app nel riquadro **App gestite**. È possibile visualizzare i problemi di installazione, ad esempio quando l'app è stato creata, modificata, assegnata e recapitata a un dispositivo. 

## <a name="to-review-app-troubleshooting-details"></a>Per esaminare le informazioni dettagliate per la risoluzione dei problemi delle app

Intune offre informazioni dettagliate per la risoluzione dei problemi delle app in base alle app installate nel dispositivo di un utente specifico.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **Risoluzione dei problemi**.
4. Fare clic su **Seleziona utente** per selezionare un utente per risolvere i problemi. Verrà visualizzato il riquadro **Seleziona utenti**.
5. Selezionare un utente digitando il nome o l'indirizzo di posta elettronica. Fare clic su **Seleziona** nella parte inferiore del riquadro. Le informazioni di risoluzione dei problemi per l'utente vengono visualizzate nel riquadro **Risoluzione dei problemi**. 
6. Selezionare il dispositivo per cui si vuole eseguire la risoluzione dei problemi nell'elenco **Dispositivi**.
    ![Riquadro Risoluzione dei problemi di Intune.](media/troubleshoot-app-install-01.png)
7. Selezionare **App gestite** nel riquadro del dispositivo selezionato. Verrà visualizzato un elenco delle app gestite.
    ![Dettagli di un dispositivo specifico gestito da Intune.](media/troubleshoot-app-install-02.png)
8. Selezionare un'app nell'elenco per cui **Stato dell'installazione** indica un errore.
    ![App selezionata che mostra informazioni dettagliate sull'errore di installazione.](media/troubleshoot-app-install-03.png)

    > [!Note]  
    > La stessa app potrebbe essere assegnata a più gruppi, ma con diverse azioni previste (finalità) per l'app. Ad esempio, la finalità risolta per un'app indicherà **esclusa** se l'app viene esclusa per un utente durante l'assegnazione di app. Per altre informazioni, vedere [Modalità di risoluzione dei conflitti tra finalità di app](apps-deploy.md#how-conflicts-between-app-intents-are-resolved).<br><br>
    > Attualmente Intune non esclude le app in base alla piattaforma del sistema operativo.

I dettagli dell'errore di installazione dell'app indicheranno il problema. È possibile usare questi dettagli per determinare l'azione migliore da intraprendere per risolvere il problema. Per altre informazioni sulla risoluzione dei problemi di installazione delle app, vedere [Error Codes For Troubleshooting App Installation Issues](https://blogs.technet.microsoft.com/intunesupport/2018/05/15/error-codes-for-troubleshooting-app-installation-issues) (Codici di errore per la risoluzione dei problemi di installazione delle app).

> [!Note]  
> È anche possibile accedere al riquadro **Risoluzione dei problemi** digitando nel browser l'indirizzo seguente: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="next-steps"></a>Passaggi successivi

- Per altre informazioni sulla risoluzione dei problemi di Intune, vedere [Usare il portale per la risoluzione dei problemi per offrire assistenza agli utenti aziendali](help-desk-operators.md). 
- È possibile ottenere informazioni sui problemi noti in Microsoft Intune. Per altre informazioni, vedere [Problemi noti in Microsoft Intune](known-issues.md).
- È possibile ottenere altre informazioni. Vedere [Come ottenere supporto per Microsoft Intune](get-support.md).
