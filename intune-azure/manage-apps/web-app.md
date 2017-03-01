---
title: Come aggiungere app Web a Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni sull&quot;aggiunta di app Web a Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: c2e54d3e57a4b02ba277b88cc672d5587c449281
ms.lasthandoff: 02/18/2017

---

# <a name="how-to-add-web-apps-to-microsoft-intune"></a>Come aggiungere app Web a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **Informazioni sull'app**.
7. Nel pannello **Modifica l'app** configurare le informazioni seguenti. Al termine, fare clic su **Aggiungi**:
    - **URL app**: immettere l'URL del sito Web che ospita l'app da distribuire.
    - **Nome app**: immettere il nome dell'app che verrà visualizzato nel portale aziendale.
    - **Descrizione app**: immettere una descrizione per l'app. La descrizione verrà visualizzata dagli utenti finali nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Categoria (facoltativo)**: selezionare una o più categorie di app predefinite oppure una categoria creata. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: mette in evidenza l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **Richiedi un browser gestito per l'apertura del collegamento**: quando si distribuisce un collegamento a un'app Web o a un sito Web, gli utenti potranno aprirlo solo in Intune Managed Browser. Questo browser deve essere installato nel dispositivo.
    - **Carica l'icona**: caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
8. Al termine, nel pannello **Aggiungi app** scegliere **Salva**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](/intune-azure/manage-apps/deploy-apps).
