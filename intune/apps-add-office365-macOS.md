---
title: Installare Office 365 nei dispositivi macOS con Microsoft Intune
titlesuffix: ''
description: Informazioni su come usare Microsoft Intune per installare le app di Office 365 nei dispositivi macOS.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78158afeb9c12e8056f42066be78c37f962b4462
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34223612"
---
# <a name="assign-office-365-to-macos-devices-with-microsoft-intune"></a>Assegnare Office 365 a dispositivi macOS con Microsoft Intune

Il tipo *App Store* consente di assegnare in modo semplice app di Office 365 ai dispositivi macOS. Tramite questo tipo di app è possibile installare Word, Excel, PowerPoint, Outlook e OneNote. Per mantenere più sicure e aggiornate le app, queste includono anche Microsoft AutoUpdate (MAU). Le app desiderate vengono visualizzate come un'unica app nell'elenco delle app nella console di Intune.


## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare ad aggiungere Office 365 nei dispositivi macOS, tenere presente quanto segue:

- È necessario che i dispositivi in cui vengono distribuite le app eseguano macOS 10.10 o versioni successive.
- Intune supporta solo l'aggiunta delle app di Office incluse nella suite Office 2016 per Mac.
- Se sono aperte app di Office quando Intune installa l'insieme di app, è possibile che gli utenti perdano i dati dei file non salvati.

## <a name="create-and-configure-the-app-suite"></a>Creare e configurare la suite di app

Aggiungere Office 365 dal riquadro **App**.
1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel riquadro **Intune** selezionare **App per dispositivi mobili**.
4. Nel riquadro del carico di lavoro **App per dispositivi mobili**, in **Gestisci** selezionare **App**. 
5. Selezionare **Aggiungi**.
6. Nell'elenco **Tipo di app** selezionare **macOS** nel gruppo **Office 365 Suite**.
7. Per ottenere informazioni sulla suite di app, selezionare **Informazioni sulla suite di app**.  
    Queste informazioni consentono di identificare la suite di app in Intune e semplificano la ricerca della suite di app da parte degli utenti nel portale aziendale.
8. Immettere le seguenti informazioni:
    - **Nome della suite**: immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione della suite**: immettere una descrizione per la suite di app.
    - **Editore**: Microsoft viene visualizzato come editore.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Questa impostazione consente agli utenti di trovare più facilmente il gruppo di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: Microsoft viene visualizzato come sviluppatore.
    - **Proprietario**: Microsoft viene visualizzato come proprietario.
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
    - **Logo**: il logo Office 365 è visualizzato insieme all'app quando gli utenti visitano il portale aziendale.
9. Selezionare **OK**.
10. Selezionare **Aggiungi** nel riquadro **Aggiungi app**.  
    La suite viene visualizzata nell'elenco delle app come singola voce.

## <a name="configure-app-assignments"></a>Configurare le assegnazioni di app

In questo passaggio configurare le assegnazioni per la suite di app. 

1. Nell'elenco delle app selezionare la suite di app **Office 365** per visualizzare il riquadro di panoramica **Office 365**.
2. Nel riquadro **Office 365** selezionare **Assegnazioni**.
3. Per aggiungere un gruppo che userà il gruppo di app, selezionare **Aggiungi gruppo**.  
    Verrà visualizzato il riquadro **Aggiungi gruppo**.
4. Impostare **Tipo di assegnazione** su **Obbligatoria**.
5. Assegnare la suite ai gruppi selezionati. Per altre informazioni, vedere [Assegnare app ai gruppi con Microsoft Intune](apps-deploy.md).

    >[!Note]
    > Non è possibile disinstallare la suite di app Office 365 tramite Intune.

5. Nel riquadro **Assegna** selezionare **OK**.
6. Nel riquadro **Aggiungi gruppo** selezionare **OK**.
7. Per confermare le assegnazioni, selezionare **Salva**.

## <a name="next-steps"></a>Passaggi successivi

- Per informazioni sull'aggiunta di app di Office 365 in un dispositivo Windows 10, vedere [Assegnare le app di Office 365 ProPlus 2016 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).
- Per informazioni su come includere ed escludere le assegnazioni delle app nei gruppi di utenti, vedere [Includere ed escludere assegnazioni di app](apps-inc-exl-assignments.md).
