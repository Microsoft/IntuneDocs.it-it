---
title: Aggiungere app dello Store iOS a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app dello Store iOS a Microsoft Intune. È possibile assegnare le app con questo metodo se sono gratuite nell'App Store.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f2baf60fed2c6010e5ae0784cda166ac4fabfd57
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511736"
---
# <a name="add-ios-store-apps-to-microsoft-intune"></a>Aggiungere app dello Store iOS a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere le app dello Store iOS a Microsoft Intune. Le app dello Store iOS sono app installate da Intune nei dispositivi degli utenti. Un utente fa parte della forza lavoro della società. Le app dello Store iOS vengono aggiornate automaticamente.

>[!NOTE]
>Anche se gli utenti dei dispositivi iOS/iPadOS possono rimuovere alcune app iOS/iPadOS predefinite, ad esempio Borsa e Mappe, non è possibile usare Intune per ridistribuire tali app. Se gli utenti eliminano queste app, devono accedere all'App Store e reinstallarle manualmente.

## <a name="before-you-start"></a>Prima di iniziare

È possibile assegnare le app con questo metodo solo se sono gratuite nell'App Store. Per assegnare app a pagamento con Intune, valutare la possibilità di usare [Volume Purchase Program per iOS/iPadOS](vpp-apps-ios.md).

>[!NOTE]
>Quando si lavora con Microsoft Intune, è consigliabile usare il browser Microsoft Edge o Google Chrome.

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Dai tipi disponibili in **App dello Store** nel riquadro **Seleziona il tipo di app** selezionare **App Store iOS**.
4. Fare clic su **Seleziona**.<br>
   Verrà visualizzata la procedura **Aggiungi app**.
5. Selezionare **Cerca in App Store**.
6. Nel riquadro **Cerca in App Store** selezionare le impostazioni locali del paese o dell'area geografica per App Store.
7. Nella casella **Cerca** digitare il nome (o una parte del nome) dell'app.  
    Intune esegue la ricerca nello Store e restituisce un elenco di risultati pertinenti.
8. Nell'elenco risultati selezionare l'app desiderata e quindi selezionare **Seleziona**.<br>

   La pagina **Informazioni sull'app** verrà visualizzata nel riquadro **Aggiungi app**. Le informazioni sull'app verranno aggiunte, se possibile, a seconda dell'app selezionata dallo Store.

9. Nella pagina **Informazioni sull'app** aggiungere i dettagli relativi all'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che deve essere visualizzato nel portale aziendale. Assicurarsi che il nome dell'app usato sia univoco. Se il nome dell'app è duplicato, nel portale aziendale sarà visualizzato un solo nome.
    - **Descrizione**: Immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
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
10. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.
11. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per l'app. Per altre informazioni, vedere [Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti](~/fundamentals/scope-tags.md).
12. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.
13. Selezionare le assegnazioni a gruppi per l'app. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md). 
14. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. Verificare i valori e le impostazioni immessi per l'app.
15. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

Verrà visualizzato il pannello **Panoramica** dell'app creata.

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)
