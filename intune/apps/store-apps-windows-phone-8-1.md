---
title: Aggiungere app dello Store per Windows Phone 8.1 in Microsoft Intune
titleSuffix: ''
description: Questo argomento descrive come aggiungere app dello Store per Windows Phone 8.1 a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3168d517ebbb59dc9d6fe5a9c262ad8e1c909619
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563814"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Aggiungere app dello Store per Windows Phone 8.1 in Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Prima di assegnare un'app a un dispositivo o a un gruppo di utenti, è necessario aggiungere l'app a Microsoft Intune. 

## <a name="add-an-app-to-intune"></a>Aggiungere un'app in Intune
Seguire questa procedura per aggiungere un'app dello Store per Windows Phone 8.1 in Intune dal portale di Azure:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Nel riquadro **Aggiungi app** selezionare il **Tipo di app** **Windows Phone 8.1** e scegliere **Informazioni sull'app**.
4. Nel riquadro **Informazioni sull'app** aggiungere le informazioni sull'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
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
5. Selezionare **OK**.
6. Selezionare **Aggiungi**.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)
