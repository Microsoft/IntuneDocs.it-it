---
title: Aggiungere app predefinite nei dispositivi mobili con Microsoft Intune
titleSuffix: ''
description: Informazioni su come usare Intune per rendere più semplice l'installazione di app predefinite nei dispositivi mobili.
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
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e299601f69a7052ea52f9da2537306cb8556982b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755375"
---
# <a name="add-built-in-apps-to-microsoft-intune"></a>Aggiungere app predefinite in Microsoft Intune

Il tipo di app *predefinito* semplifica l'assegnazione di app gestite dedicate, ad esempio le app di Office 365, ai dispositivi iOS e Android. È possibile assegnare app specifiche per questo tipo di app, come Excel, OneDrive, Outlook, Skype e altre ancora. Dopo aver aggiunto un'app, viene visualizzato il tipo di app, ovvero *App iOS predefinita* o *App Android predefinita*. Con il tipo di app predefinito, è possibile scegliere quali di queste app pubblicare nei dispositivi degli utenti.

Nelle versioni precedenti della console di Intune, Intune forniva diverse app di Office 365 gestite predefinite, ad esempio Outlook e OneDrive. I tipi di app per queste app gestite erano contrassegnati come *App dello Store iOS gestita* o *App di Android Store gestita*. Invece di usare questi tipi di app, è consigliabile usare il tipo di app predefinito. Il tipo di app predefinito offre una maggiore flessibilità per modificare ed eliminare le app di Office 365.

>[!NOTE]
>Le app di Office 365 predefinite contrassegnate come *App dello Store iOS gestita* e *App di Android Store gestita* verranno rimosse dall'elenco di app quando verranno eliminate tutte le assegnazioni.

## <a name="add-a-built-in-app"></a>Aggiungere un'app predefinita

Per aggiungere un'app predefinita alle app disponibili in Microsoft Intune, seguire questa procedura:
1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Dai tipi disponibili in **App dello Store** nel riquadro **Seleziona il tipo di app** selezionare **App predefinita**.
4. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi app**.
5. Nella pagina **Selezionare le app predefinite** fare clic su **Seleziona app** per selezionare le app da includere.
6. Selezionare le app predefinite da includere. 
7. Dopo aver selezionato le app, fare clic su **Seleziona** nel riquadro **Selezionare le app predefinite**.
8. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.
9. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per l'app. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti](~/fundamentals/scope-tags.md).
10. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.
11. Selezionare le assegnazioni a gruppi per l'app. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md). 
12. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. Verificare i valori e le impostazioni immessi per l'app.
13. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

    Verrà visualizzato il pannello **Panoramica** dell'app creata.

## <a name="configure-app-information"></a>Configurare le informazioni sull'app

È possibile modificare le informazioni sull'app predefinita. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovare l'app nel portale aziendale.
1. Selezionare **App** > **Tutte le app** e selezionare l'app predefinita da modificare.  
   Viene visualizzato un riquadro per l'app predefinita.
2. Selezionare **Proprietà**.
3. Selezionare **Modifica** accanto a **Informazioni sull'app**.
4. Nel riquadro **Informazioni sull'app** è possibile modificare le informazioni seguenti:
    - **Nome**: immettere il nome dell'app predefinita che viene visualizzato nel portale aziendale. Verificare che tutti i nomi usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione**: Immettere una descrizione per l'app. 
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **Categoria**: facoltativamente, selezionare una o più categorie dell'app predefinita. L'impostazione di questa opzione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: Visualizzare chiaramente l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: facoltativamente, immettere un nome per il proprietario dell'app, ad esempio *Reparto risorse umane*.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Carica l'icona**: caricare un'icona visualizzata con l'app quando gli utenti esplorano il portale aziendale.
5. Fare clic su **Verifica e salva** per visualizzare la pagina **Rivedi e crea**. Verificare i valori e le impostazioni immessi per l'app.
13. Al termine, fare clic su **Salva** per aggiornare l'app in Intune.

    Verrà visualizzato il pannello **Panoramica** dell'app creata.

## <a name="next-steps"></a>Passaggi successivi

- È ora possibile assegnare le app ai gruppi scelti. Per altre informazioni, vedere [Assegnare app ai gruppi](apps-deploy.md).
