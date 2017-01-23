---
title: Monitoraggio delle distribuzioni di app | Documentazione Microsoft
description: Informazioni su come monitorare le app distribuite con Intune.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5daad56d-71c8-455b-8a55-f8b33e279a8a
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: ee0d10f9b86b1122d0f16568b71b087c341e88df


---


# <a name="monitor-app-deployments-in-microsoft-intune"></a>Monitoraggio delle distribuzioni di app in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="monitor-an-app-deployment"></a>Monitorare la distribuzione di un'app
È possibile visualizzare le app gestite e lo stato di tutte le distribuzioni nella console di amministrazione di Intune. <!---App status is displayed in real-time. You don't have to wait for the device to check-in before you can see this.--->

### <a name="to-view-apps-that-you-manage-and-their-status"></a>Per visualizzare le app gestite e il relativo stato
Nell'area di lavoro **App** selezionare il nodo **App**, quindi scegliere **App**.

Viene visualizzato l'elenco di app gestite. È possibile scegliere una qualsiasi app per visualizzare lo stato di installazione nel riquadro inferiore delle finestre della console. Per visualizzare altri dettagli, scegliere questo stato. Ad esempio, se lo stato è **1 utente dispone di questo software**, si può fare clic sul messaggio per visualizzare il nome dell'utente.

> [!TIP]
> È possibile usare l'elenco a discesa **Filtri** per visualizzare solo le app che soddisfano i criteri specificati, ad esempio le app la cui installazione non è riuscita o quelle distribuite correttamente.
>
> ![Esempio di filtri per app](./media/app-filters.png)

Inoltre, l'area di lavoro **Dashboard** include anche una panoramica dello stato delle app. Se si fa clic su un punto qualsiasi della panoramica, verrà visualizzato l'elenco di app.

## <a name="to-view-more-detailed-information-about-an-app"></a>Per visualizzare informazioni più dettagliate su un'app
Nell'elenco di app selezionare un'app e quindi scegliere **Visualizza proprietà**.

Nella pagina **Proprietà software** dell'app scegliere una di queste schede: **Generale**, che contiene informazioni generali sull'app e sul relativo stato di installazione, **Dispositivi**, che indica i dispositivi su cui è installata una distribuzione di destinazione dell'app e **Utenti**, che indica gli utenti che hanno eseguito correttamente l'installazione di una distribuzione di destinazione dell'app nei propri dispositivi.

Come illustrato in precedenza, è possibile usare l'elenco a discesa **Filtri** per configurare i valori mostrati in ogni scheda.



<!--HONumber=Dec16_HO2-->


