---
title: Installare Office 365 nei dispositivi macOS con Microsoft Intune
titleSuffix: ''
description: Informazioni su come usare Microsoft Intune per installare le app di Office 365 nei dispositivi macOS.
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
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3cf4c2abb5506f297af8a4e77145abea5360381b
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755358"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Assegnare Office 365 a dispositivi macOS con Microsoft Intune

Questo tipo di app semplifica l'assegnazione di app di Office 365 2016 ai dispositivi macOS. Tramite questo tipo di app è possibile installare Word, Excel, PowerPoint, Outlook e OneNote. Per mantenere più sicure e aggiornate le app, queste includono anche Microsoft AutoUpdate (MAU). Le app desiderate vengono visualizzate come un'unica app nell'elenco delle app nella console di Intune.


## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare ad aggiungere Office 365 nei dispositivi macOS, tenere presente quanto segue:

- È necessario che i dispositivi in cui vengono distribuite le app eseguano macOS 10.10 o versioni successive.
- Intune supporta solo l'aggiunta delle app di Office incluse nella suite Office 2016 per Mac.
- Se sono aperte app di Office quando Intune installa l'insieme di app, è possibile che gli utenti perdano i dati dei file non salvati.

## <a name="select-the-office-365-suite-app-type"></a>Selezionare il tipo di app Famiglia di prodotti Office 365

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Selezionare **macOs** nella sezione **Famiglia di prodotti Office 365** del riquadro **Seleziona il tipo di app**.
4. Fare clic su **Seleziona**. Verrà visualizzata la procedura **Aggiungi la famiglia di prodotti Office 365**.

## <a name="step-1---app-suite-information"></a>Passaggio 1: informazioni sulla famiglia di prodotti dell'app

In questo passaggio si specificano le informazioni sulla suite di app. Queste informazioni consentono di identificare la suite di app in Intune e semplificano la ricerca della suite di app da parte degli utenti nel portale aziendale.

1. Nella pagina **Informazioni sulla famiglia di prodotti dell'app** è possibile confermare o modificare i valori predefiniti:
    - **Nome della suite**: immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione della suite** : immettere una descrizione per la suite di app. Ad esempio, è possibile elencare le app selezionate da includere.
    - **Autore**: come editore viene visualizzato Microsoft.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa impostazione consente agli utenti di trovare più facilmente il gruppo di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: come sviluppatore viene visualizzato Microsoft.
    - **Proprietario**: come proprietario viene visualizzato Microsoft.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: quando gli utenti visitano il portale aziendale, il logo Office 365 viene visualizzato insieme all'app.
2. Fare clic su **Avanti** per visualizzare la pagina **Tag di ambito**.

## <a name="step-2---select-scope-tags-optional"></a>Passaggio 2: selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere [Use role-based access control and scope tags for distributed IT](../fundamentals/scope-tags.md) (Usare il controllo degli accessi in base al ruolo e i tag di ambito per l'IT distribuito).

1. Fare clic su **Selezionare i tag di ambito** per aggiungere facoltativamente tag di ambito per la famiglia di prodotti dell'app. 
2. Fare clic su **Avanti** per visualizzare la pagina **Assegnazioni**.

## <a name="step-3---assignments"></a>Passaggio 3: assegnazioni

1. Per l'assegnazione della famiglia di prodotti dell'app a gruppi, selezionare **Obbligatoria** o **Disponibile per i dispositivi registrati**. Per altre informazioni, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](~/fundamentals/groups-add.md) e [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Non è possibile disinstallare la famiglia di prodotti dell'app Office 365 per macOS tramite Intune.

2. Fare clic su **Avanti** per visualizzare la pagina **Rivedi e crea**. 

## <a name="step-4---review--create"></a>Passaggio 4 - Verifica e creazione

1. Verificare i valori e le impostazioni immessi per la famiglia di prodotti dell'app.
2. Al termine, fare clic su **Crea** per aggiungere l'app a Intune.

    Verrà visualizzato il pannello **Panoramica** della famiglia di prodotti dell'app Office 365 per Window 10 creata. La suite viene visualizzata nell'elenco delle app come singola voce.

## <a name="next-steps"></a>Passaggi successivi

- Per informazioni sull'aggiunta di app di Office 365 in un dispositivo Windows 10, vedere [Assegnare le app di Office 365 ProPlus 2016 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).
- Per informazioni su come includere ed escludere le assegnazioni delle app nei gruppi di utenti, vedere [Includere ed escludere assegnazioni di app](apps-inc-exl-assignments.md).
