---
title: Aggiungere app dello Store iOS a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app dello Store iOS a Microsoft Intune. È possibile assegnare le app con questo metodo se sono gratuite nell'App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68976c9a71ab1c1886fd5f975df563acb44dc731
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724490"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Aggiungere app dello Store iOS a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere le app dello Store iOS a Microsoft Intune. Le app dello Store iOS sono app installate da Intune nei dispositivi degli utenti. Un utente fa parte della forza lavoro della società. Le app dello Store iOS vengono aggiornate automaticamente.

>[!NOTE]
>Anche se gli utenti dei dispositivi iOS possono rimuovere alcune app iOS predefinite, ad esempio Borsa e Mappe, non è possibile usare Intune per ridistribuire tali app. Se gli utenti eliminano queste app, devono accedere all'App Store e reinstallarle manualmente.

## <a name="before-you-start"></a>Prima di iniziare

È possibile assegnare le app con questo metodo solo se sono gratuite nell'App Store. Per assegnare app a pagamento con Intune, valutare la possibilità di usare [Volume Purchase Program iOS](vpp-apps-ios.md).

>[!NOTE]
>Quando si lavora con Microsoft Intune, è consigliabile usare il browser Microsoft Edge o Google Chrome.

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Gestisci** selezionare **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nell'elenco **Tipo di app** selezionare **iOS** dai tipi di **app dello Store** disponibili.
7. Selezionare **Cerca in App Store**.
8. Nel riquadro **Cerca in App Store** selezionare le impostazioni locali del paese o dell'area geografica per App Store.
9. Nella casella **Cerca** digitare il nome (o una parte del nome) dell'app.  
    Intune esegue la ricerca nello Store e restituisce un elenco di risultati pertinenti.
10. Nell'elenco risultati selezionare l'app desiderata e quindi selezionare **Seleziona**.
11. Nel riquadro **Aggiungi app** selezionare **Informazioni sull'app** per configurare l'app.
12. Nel riquadro **Informazioni sull'app** aggiungere le informazioni sull'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che deve essere visualizzato nel portale aziendale. Assicurarsi che il nome dell'app usato sia univoco. Se il nome dell'app è duplicato, nel portale aziendale sarà visualizzato un solo nome.
    - **Description**: Immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **URL di App Store**: digitare l'URL dell'App Store per l'app da creare.
    - **Sistema operativo minimo**: selezionare dall'elenco la versione meno recente del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Tipo di dispositivo applicabile**: selezionare dall'elenco i dispositivi che vengono usati dall'app.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa operazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo). Questo campo è visibile solo per gli amministratori e non è visibile per gli utenti.
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio *Reparto risorse umane* (facoltativo). Questo campo è visibile solo per gli amministratori e non è visibile per gli utenti.
    - **Note**: immettere eventuali note da associare a questa app (facoltativo). Questo campo è visibile solo per gli amministratori e non per gli utenti.
    - **Logo**: caricare un'icona da associare all'app (facoltativo). Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
13. Selezionare **OK**.
14. Selezionare **Aggiungi**.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)
