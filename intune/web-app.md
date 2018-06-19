---
title: Aggiungere app Web a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app Web in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0d62341e35bf851bb429b15a582183bec62a9d4a
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223391"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Aggiungere app Web a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune supporta un'ampia gamma di tipi di app, incluse le app Web. Un'app Web è un'applicazione client-server. Il server fornisce l'app Web che include interfaccia utente, contenuto e funzionalità. Le moderne piattaforme di hosting Web in genere offrono anche sicurezza, bilanciamento del carico e altri vantaggi. Un'app Web viene gestita separatamente nel Web. Usare Microsoft Intune per puntare a questo tipo di app. Assegnare anche i gruppi di utenti autorizzati ad accedere all'app. 

Prima di poter gestire e assegnare un'app per gli utenti, è necessario aggiungerla in Intune. Intune crea un collegamento all'app Web nella schermata iniziale del dispositivo dell'utente.

> [!Note]
> Le app Web non sono supportate nei dispositivi Android for Work e macOS.

## <a name="add-a-web-app-to-intune"></a>Aggiungere un'app Web a Intune
Per aggiungere un'app a Intune come collegamento a un'app nel Web, eseguire le operazioni seguenti:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**.  
    Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App per dispositivi mobili**.
4. Nel riquadro del carico di lavoro **App per dispositivi mobili**, in **Gestisci** selezionare **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nell'elenco a discesa **Tipo di app** del riquadro **Aggiungi app** selezionare il tipo **Collegamento Web**.
7. Selezionare **Configura**.
8. Nel riquadro **Informazioni sull'app** aggiungere le informazioni seguenti:
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL app**: immettere l'URL del sito Web che ospita l'app da assegnare.
    - **Categoria**: facoltativamente, selezionare una o più categorie di app predefinite oppure una categoria creata dall'utente. Questa operazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **Richiedi un browser gestito per l'apertura del collegamento**: selezionare questa opzione per assegnare agli utenti un collegamento a un sito Web o a un'app Web che gli utenti possono aprire in Intune Managed Browser. Questo browser deve essere installato nel dispositivo.
    - **Logo**: caricare un'icona che verrà associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
9. Selezionare **OK**.
10. Selezionare **Aggiungi** nel riquadro **Aggiungi app**.

> [!Note]
> Gli utenti devono aggiungere il widget di Intune nella schermata iniziale per visualizzare le app Web che sono state assegnate a dispositivi Android.

## <a name="next-steps"></a>Passaggi successivi

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Assegnare app ai gruppi](apps-deploy.md). 
