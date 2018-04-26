---
title: Come aggiungere app di Microsoft Store a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app Microsoft Store (Windows Store) a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 511cf2e01a2f5db93f0e0db9dbe2a32326c17723
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Aggiungere app di Microsoft Store a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. I passaggi seguenti consentono di aggiungere un'app di Microsoft Store a Microsoft Intune.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi app** scegliere il **Tipo di app** **Windows** e scegliere **Informazioni sull'app**.
7. Nel riquadro **Informazioni sull'app** configurare le informazioni seguenti. Al termine, fare clic su **OK**. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**: immettere la descrizione dell'app che gli utenti visualizzeranno nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
    - **Categoria (facoltativo)**: selezionare una o più categorie di app predefinite oppure una categoria personalizzata per consentire agli utenti di trovare più facilmente l'app quando esplorano il portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona da associare all'app. Questa è l'icona che viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
8. Al termine, nel riquadro **Aggiungi app** scegliere **Aggiungi**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. 

## <a name="next-steps"></a>Passaggi successivi
- [Come assegnare app ai gruppi](apps-deploy.md)