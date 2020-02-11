---
title: Aggiungere un'app line-of-business per Windows Phone a Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere un'app line-of-business (LOB) per Windows Phone usando Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328bafc2a55191c203263911ceaac9b520eb07f5
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755154"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Aggiungere un'app line-of-business per Windows Phone a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere un'app line-of-business per Windows Phone in Microsoft Intune. Un'app line-of-business è un'app che viene aggiunta in Intune dal file di installazione di un'app. Questo tipo di app viene in genere scritto internamente. Intune installa l'app line-of-business nel dispositivo dell'utente. 

## <a name="select-the-app-type"></a>Selezionare il tipo di app

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Tra i tipi di app in **Altro** nel riquadro **Seleziona il tipo di app** selezionare **App line-of-business**.
4. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi app**.

## <a name="step-1---app-information"></a>Passaggio 1: informazioni sull'app

### <a name="select-the-app-package-file"></a>Selezionare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** fare clic su **Selezionare il file del pacchetto di app**. 
2. Nel riquadro **File del pacchetto dell'app** selezionare il pulsante Sfoglia. Selezionare quindi un file di installazione Windows Phone con estensione **xap**.
   Verranno visualizzati i dettagli dell'app.
3. Al termine, selezionare **OK** nel riquadro **File del pacchetto dell'app** per aggiungere l'app.

### <a name="set-app-information"></a>Impostare le informazioni sull'app

1. Nella pagina **Informazioni sull'app** aggiungere i dettagli relativi all'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente.
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata nel portale aziendale.
    - **Descrizione**: immettere la descrizione dell'app. La descrizione viene visualizzata nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **Sistema operativo minimo**: selezionare dall'elenco la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: Visualizzare chiaramente l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario dell'app (facoltativo). Un esempio è **Reparto risorse umane**.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
2. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.

## <a name="step-2---select-scope-tags-optional"></a>Passaggio 2: selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

1. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per l'app. 
2. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.

## <a name="step-3---assignments"></a>Passaggio 3: assegnazioni

1. Per l'assegnazione dell'app a gruppi, selezionare **Obbligatoria**, **Disponibile per i dispositivi registrati** o **Disinstalla**. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md) e [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).
2. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. 

## <a name="step-4---review--create"></a>Passaggio 4 - Verifica e creazione

1. Verificare i valori e le impostazioni immesse per l'app.
2. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

    Verrà visualizzato il pannello **Panoramica** per l'app line-of-business.

L'app creata viene ora visualizzata nell'elenco di app. Dall'elenco è possibile assegnare le app ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Vedere [Panoramica dei cicli di vita del dispositivo e dell'app](../fundamentals/device-lifecycle.md).
