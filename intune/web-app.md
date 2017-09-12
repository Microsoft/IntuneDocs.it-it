---
title: Come aggiungere app Web a Intune
titleSuffix: Azure portal
description: Informazioni sull'aggiunta di app Web a Intune."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e60fd4575ce1f8d95600b3510cfd3c5fb7bc0f12
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Come aggiungere app Web a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **Informazioni sull'app**.
7. Nel pannello **Modifica l'app** configurare le informazioni seguenti. Al termine, fare clic su **Aggiungi**:
    - **URL app**: immettere l'URL del sito Web che ospita l'app da assegnare.
    - **Nome app**: immettere il nome dell'app che verrà visualizzato nel portale aziendale.
    - **Descrizione app**: immettere una descrizione per l'app. La descrizione verrà visualizzata dagli utenti finali nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Categoria (facoltativo)**: selezionare una o più categorie di app predefinite oppure una categoria creata. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **Richiedi un browser gestito per l'apertura del collegamento**: quando si assegna un collegamento a un'app Web o a un sito Web, gli utenti potranno aprirlo solo in Intune Managed Browser. Questo browser deve essere installato nel dispositivo.
    - **Carica l'icona**: caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
8. Al termine, nel pannello **Aggiungi app** scegliere **Salva**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).