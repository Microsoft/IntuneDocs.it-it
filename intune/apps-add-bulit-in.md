---
title: Aggiungere app predefinite nei dispositivi mobili con Intune
titlesuffix: Azure portal
description: "Informazioni su come usare Intune per rendere più semplice l'installazione di app predefinite nei dispositivi mobili."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0ec8de66-5a0f-4c8d-afbf-c2becc7d6eec
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 90bec6442084e46f499c57cf128e6ef57fe1ce9c
ms.sourcegitcommit: 0a5f424a8f683daa919b13b5c363173040d561c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-add-built-in-apps-to-microsoft-intune"></a>Come aggiungere app predefinite in Microsoft Intune

Il tipo di app **predefinito** semplifica l'assegnazione di app gestite dedicate, ad esempio le app di Office 365, ai dispositivi iOS e Android. È possibile assegnare app specifiche per questo tipo di app, ad esempio Excel, Power BI, SharePoint, Teams, OneDrive, Outlook, Skype e altre. Dopo aver aggiunto un'app, verrà visualizzato il tipo di app, ovvero **App iOS predefinita** o **App Android predefinita**. Con il tipo di app predefinito, è possibile scegliere quali di queste app specifiche pubblicare nei dispositivi degli utenti.

 Nelle versioni precedenti della console di Intune, Intune forniva diverse app di Office 365 gestite predefinite, ad esempio Outlook e OneDrive. Il tipo di app per queste app gestite era contrassegnato come "App dello Store iOS gestita" o "App Android gestita". È consigliabile usare i tipi di app predefiniti anziché "App dello Store iOS gestita" o "App Android gestita" perché il tipo di app predefinito offre una maggiore flessibilità per modificare ed eliminare le app di Office 365.

>[!NOTE]
>Le app di Office 365 predefinite contrassegnate come "App dello Store iOS gestita" o "App Android gestita" verranno rimosse dall'elenco di app quando verranno eliminate tutte le assegnazioni per questa app.

## <a name="add-built-in-app"></a>Aggiungere un'app predefinita

I passaggi seguenti consentono di aggiungere un'app predefinita alle app disponibili in Microsoft Intune.
1.  Accedere al portale di Azure.
2.  Visualizzare il pannello di Microsoft Intune scegliendo **Altri servizi** > **Monitoraggio + Gestione** > **Intune**.
3.  Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4.  Nel pannello **App per dispositivi mobili** scegliere **App** nel gruppo **Gestisci**.
5.  Scegliere **Aggiungi** per aggiungere una nuova app.
6.  Nel pannello **Aggiungi** app scegliere **App predefinita** dall'elenco **Tipo di app**.
7.  Fare clic su **Seleziona app** per scegliere le app predefinite da includere.
8.  Nel pannello App predefinita selezionare le app da includere.
9.  Nel pannello **Aggiungi app** fare clic su **Aggiungi** per includere le app.


## <a name="configure-app-information"></a>Configurare le informazioni sull'app

È possibile modificare le informazioni sull'app predefinita. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovare l'app nel Portale aziendale.
1.  Nel pannello **App per dispositivi mobili - App** scegliere l'app predefinita da modificare. Viene visualizzato un pannello per l'app predefinita.
2.  Selezionare l'opzione **Proprietà** nel gruppo **Gestisci**.
3.  Selezionare l'opzione **Configura** per modificare le informazioni sull'app predefinita.
4.  Nel pannello **Informazioni sull'app** è possibile modificare le informazioni seguenti:
    -   **Nome**: immettere il nome dell'app predefinita che viene visualizzato nel portale aziendale. Verificare che tutti i nomi usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    -   **Descrizione**: immettere una descrizione per l'app. 
    -   **Autore**: immettere il nome dell'autore dell'app.
    -   **Categoria**: selezionare una o più categorie dell'app predefinita (facoltativo). L'impostazione di questa opzione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    -   **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    -   **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    -   **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    -   **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    -   **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio reparto risorse umane (facoltativo).
    -   **Note**: immettere eventuali note da associare a questa app.
    -   **Carica icona**: caricare un'icona visualizzata con l'app dagli utenti nel portale aziendale.
3.  Al termine, fare clic su **OK** nel pannello **Informazioni sull'app**.
4.  Fare clic su **Salva** nel pannello **Proprietà**.

## <a name="next-steps"></a>Passaggi successivi

È ora possibile assegnare le app ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).
