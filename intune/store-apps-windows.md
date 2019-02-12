---
title: Aggiungere app di Microsoft Store a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app Microsoft Store (Windows Store) a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98f25ec1dce7b07fdd6271cea965b9d44b137221
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845755"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Aggiungere app di Microsoft Store a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. 

## <a name="add-an-app-to-intune"></a>Aggiungere un'app in Intune
È possibile aggiungere un'app dello Store Microsoft in Intune seguendo questa procedura:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**.  
    Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Gestisci** selezionare **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app** selezionare il **Tipo di app** **Windows** e scegliere **Informazioni sull'app**.
7. Nel riquadro **Informazioni sull'app** aggiungere le informazioni sull'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che deve essere visualizzato nel portale aziendale. Assicurarsi che il nome dell'app usato sia univoco. Se il nome dell'app è duplicato, nel portale aziendale sarà visualizzato un solo nome.
    - **Description**: Immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **URL di App Store**: digitare l'URL dell'App Store per l'app da creare.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa operazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio *Reparto risorse umane* (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
    - **Logo**: caricare un'icona da associare all'app (facoltativo). Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
8. Selezionare **OK**.
9. Selezionare **Aggiungi**.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. Le app di Microsoft Store possono essere assegnate ai gruppi solo con il tipo di assegnazione in cui l'app è **disponibile per i dispositivi registrati** (gli utenti installano l'app dall'app del portale aziendale o dal sito Web).

## <a name="next-steps"></a>Passaggi successivi
- [Assegnare app ai gruppi](apps-deploy.md)
