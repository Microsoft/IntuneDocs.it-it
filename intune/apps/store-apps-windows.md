---
title: Aggiungere app di Microsoft Store a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app Microsoft Store (Windows Store) a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8743af2a05f6daebca5e1394ba5b7b8f13fcf7e3
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754899"
---
# <a name="add-microsoft-store-apps-to-microsoft-intune"></a>Aggiungere app di Microsoft Store a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Prima di poter assegnare, monitorare, configurare o proteggere le app è necessario aggiungerle a Intune. 

## <a name="add-an-app-to-intune"></a>Aggiungere un'app in Intune
È possibile aggiungere un'app dello Store Microsoft in Intune seguendo questa procedura:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Dai tipi disponibili in **App dello Store** nel riquadro **Seleziona il tipo di app** selezionare **App di Windows Store**.
4. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi app**.
5. Per configurare le **Informazioni sull'app** per le app di Windows Store, passare a [Microsoft Store](https://www.microsoft.com/store/apps) e cercare l'app che si vuole distribuire. Visualizzare la pagina dell'app e prendere nota dei dettagli dell'app. 
6. Nella pagina **Informazioni sull'app** aggiungere i dettagli relativi all'app:
    - **Nome**: immettere il nome dell'app che deve essere visualizzato nel portale aziendale. Assicurarsi che il nome dell'app usato sia univoco. Se il nome dell'app è duplicato, nel portale aziendale sarà visualizzato un solo nome.
    - **Descrizione**: Immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **URL di App Store**: digitare l'URL dell'App Store per l'app da creare. È possibile trovare l'URL eseguendo una ricerca dell'app desiderata in [Microsoft Store](https://www.microsoft.com/store/apps). Usare l'URL dalla barra degli indirizzi del browser.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa operazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio *Reparto risorse umane* (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
    - **Logo**: caricare un'icona da associare all'app (facoltativo). Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
7. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.
8. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per l'app. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti](~/fundamentals/scope-tags.md).
9. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.
10. Selezionare le assegnazioni a gruppi per l'app. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md). 
11. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. Verificare i valori e le impostazioni immesse per l'app.
12. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

Verrà visualizzato il pannello **Panoramica** dell'app creata.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati.

> [!IMPORTANT]
> Le app di Microsoft Store possono essere assegnate ai gruppi solo con il tipo di assegnazione in cui l'app è **disponibile per i dispositivi registrati** (gli utenti installano l'app dall'app del portale aziendale o dal sito Web).

## <a name="next-steps"></a>Passaggi successivi
- [Assegnare app ai gruppi](apps-deploy.md)
