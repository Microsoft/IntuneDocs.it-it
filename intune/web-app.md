---
title: Come aggiungere app Web a Intune
titleSuffix: Azure portal
description: Informazioni sull'aggiunta di app Web a Intune."
keywords: 
author: erikre
ms.author: erikre
manager: angrobe
ms.date: 12/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6da1441b16a43b5e22bedd9e87970f3388b11b9e
ms.sourcegitcommit: a3a744ea55f38a360ca9f788c77a5b3018d1add5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/30/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Come aggiungere app Web a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Prima di poter gestire e assegnare un'app per gli utenti, è necessario aggiungerla in Intune. Intune supporta un'ampia gamma di tipi di app, incluse le app Web.

> [!Note]
> Le app Web non sono supportate nei dispositivi Android for Work.

Seguire questa procedure per aggiungere un'app a Intune come collegamento a un'app sul Web:

1. Accedere al portale di Azure.
2. Usare **Altre risorse** per cercare e selezionare **Intune**.
3. Nel pannello **Microsoft Intune** selezionare **App per dispositivi mobili**.
4. Nel pannello **App per dispositivi mobili** selezionare **App**.
5. Sopra l'elenco delle app selezionare **Aggiungi**. Viene visualizzato il pannello **Aggiungi app**.
6. Nel pannello **Aggiungi app** selezionare il tipo **App Web** nell'elenco a discesa **Tipo di app**.
7. Selezionare l'opzione **Configura** per visualizzare il pannello **Informazioni sull'app**.
8. Nel pannello **Informazioni sull'app** aggiungere le informazioni seguenti:
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione viene visualizzata dagli utenti finali nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL app**: immettere l'URL del sito Web che ospita l'app da assegnare.
    - **Categoria (facoltativo)**: selezionare una o più categorie di app predefinite oppure una categoria creata. Questa selezione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **Richiedi un browser gestito per l'apertura del collegamento**: quando si assegna un collegamento a un'app Web o a un sito Web, gli utenti possono aprirlo in Intune Managed Browser. Questo browser deve essere installato nel dispositivo.
    - **Logo**: caricare un logo associato all'app. Questo è il logo visualizzato insieme all'app quando gli utenti visitano il portale aziendale.
9. Al termine, selezionare **OK** nel pannello **Aggiungi informazioni**.
10. Selezionare quindi **Aggiungi** nel pannello **Aggiungi app**.

L'app creata viene visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).