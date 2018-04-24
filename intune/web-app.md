---
title: Come aggiungere app Web a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app Web in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45253e061039198aee4aa49b2bf879a1b9929e35
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Come aggiungere app Web a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune supporta un'ampia gamma di tipi di app, incluse le app Web. Un'app Web è un'applicazione client-server. Il server fornisce l'app Web che include interfaccia utente, contenuto e funzionalità. Le moderne piattaforme di hosting Web in genere offrono inoltre sicurezza, bilanciamento del carico e altri vantaggi. Un'app Web viene gestita separatamente sul Web. Usare Microsoft Intune per puntare a questo tipo di app. Assegnare anche i gruppi di utenti autorizzati ad accedere all'app. 

Prima di poter gestire e assegnare un'app per gli utenti, è necessario aggiungerla in Intune. Intune crea un collegamento all'app Web nella schermata iniziale del dispositivo dell'utente.

> [!Note]
> Le app Web non sono supportate nei dispositivi Android for Work e macOS.

Seguire questa procedure per aggiungere un'app a Intune come collegamento a un'app sul Web:

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Microsoft Intune** selezionare **App per dispositivi mobili**.
4. Nel riquadro **App per dispositivi mobili** selezionare **App**.
5. Sopra l'elenco delle app selezionare **Aggiungi**. Viene visualizzato il riquadro **Aggiungi app**.
6. Nel riquadro **Aggiungi app** selezionare il tipo **Collegamento Web** nell'elenco a discesa **Tipo di app**.
7. Selezionare l'opzione **Configura** per visualizzare il riquadro **Informazioni sull'app**.
8. Nel riquadro **Informazioni sull'app** aggiungere le informazioni seguenti:
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione viene visualizzata dagli utenti finali nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL app**: immettere l'URL del sito Web che ospita l'app da assegnare.
    - **Categoria (facoltativo)**: selezionare una o più categorie di app predefinite oppure una categoria creata. Questa selezione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **Richiedi un browser gestito per l'apertura del collegamento**: quando si assegna un collegamento a un'app Web o a un sito Web, gli utenti possono aprirlo in Intune Managed Browser. Questo browser deve essere installato nel dispositivo.
    - **Logo**: caricare un logo associato all'app. Questo è il logo visualizzato insieme all'app quando gli utenti visitano il portale aziendale.
9. Al termine, selezionare **OK** nel riquadro **Aggiungi informazioni**.
10. Selezionare quindi **Aggiungi** nel riquadro **Aggiungi app**.

> [!Note]
> Gli utenti devono aggiungere il widget di Intune nella schermata iniziale per visualizzare le app Web che sono state assegnate ai dispositivi Android.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).