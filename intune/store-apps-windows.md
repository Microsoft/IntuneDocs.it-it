---
title: Aggiungere app di Microsoft Store a Microsoft Intune
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
ms.openlocfilehash: baa9b20ee8820915f3cdee6ee26ec2429c93d63b
ms.sourcegitcommit: 2b5d88c434bda7f1cdc32d1ccacc6b341a9a399b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Aggiungere app di Microsoft Store a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. 

## <a name="add-an-app-to-intune"></a>Aggiungere un'app in Intune
È possibile aggiungere un'app dello Store Microsoft in Intune seguendo questa procedura:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**.  
    Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App per dispositivi mobili**.
4. Nel riquadro del carico di lavoro **App per dispositivi mobili**, in **Gestisci** selezionare **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app** selezionare il **Tipo di app** **Windows** e scegliere **Informazioni sull'app**.
7. Nel riquadro **Informazioni sull'app** aggiungere le informazioni sull'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale. Assicurarsi che il nome dell'app usato sia univoco. Se il nome dell'app è duplicato, nel portale aziendale sarà visualizzato un solo nome.
    - **Descrizione**: immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: digitare l'URL dell'App Store per l'app che si vuole creare.
    - **Categoria**: facoltativamente, selezionare una o più categorie di app predefinite oppure una categoria creata. Questa operazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, *Reparto risorse umane* (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
    - **Logo**: caricare un'icona da associare all'app (facoltativo). Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
8. Selezionare **OK**.
9. Selezionare **Aggiungi**.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. 

## <a name="next-steps"></a>Passaggi successivi
- [Assegnare app ai gruppi](apps-deploy.md)
