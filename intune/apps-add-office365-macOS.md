---
title: Installare Office 365 nei dispositivi macOS con Microsoft Intune
titlesuffix: 
description: Informazioni su come usare Microsoft Intune per installare le app di Office 365 nei dispositivi macOS.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8de14184c4d23adc79d5b519fdcf272f0d7f6804
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Come assegnare Office 365 a dispositivi macOS con Microsoft Intune

Il tipo **App Store** consente di assegnare in modo semplice app di Office 365 ai dispositivi macOS. Questo tipo di app consente di installare Word, Excel, PowerPoint, Outlook e OneNote. Queste app includono anche Microsoft AutoUpdate (MAU), per mantenere più sicure e aggiornate le app. Le app desiderate vengono visualizzate come un'unica app nell'elenco delle app nella console di Intune.


## <a name="before-you-start"></a>Prima di iniziare

Prima di iniziare ad aggiungere Office 365 nei dispositivi macOS, tenere presente quanto segue:

- È necessario che i dispositivi in cui vengono distribuite le app eseguano macOS 10.10 o versioni successive.
- Intune supporta solo l'aggiunta di app di Office incluse nella suite Office 2016 per Mac.
- Se sono aperte app di Office quando Intune installa la suite di app, è possibile che gli utenti finali perdano i dati dei file non salvati.

## <a name="create-and-configure-the-app-suite"></a>Creare e configurare la suite di app

Aggiungere Office 365 usando il pannello **App**.
1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Monitoraggio e gestione** > **Intune**.
3. Scegliere **App per dispositivi mobili** dal pannello **Intune**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **App** nella sezione **Gestisci**. 
5. Scegliere **Aggiungi** per visualizzare il pannello **Aggiungi app**.
6. Nell'elenco **Tipo di app** selezionare **macOS** nel gruppo **Office 365 Suite**.
7. Selezionare **Informazioni sulla suite di app** per specificare informazioni sulla suite di app. Queste informazioni consentono di identificare la suite di app in Intune e semplificano la ricerca della suite da parte degli utenti nell'app Portale aziendale.
8.  Specificare le informazioni seguenti:
    - **Suite Name** (Nome suite): immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Suite Description** (Descrizione suite): immettere una descrizione per la suite di app.
    - **Editore** -Microsoft viene visualizzato come editore.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Questa impostazione consente agli utenti di trovare più facilmente il gruppo di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: questa impostazione visualizza in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che contiene informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che contiene informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore** -Microsoft viene visualizzato come sviluppatore.
    - **Proprietario** -Microsoft viene visualizzato come proprietario.
    - **Note**: immettere tutte le note da associare a questa app (facoltativo).
    - **Logo**: il logo Office 365 è visualizzato insieme all'app quando gli utenti visitano il portale aziendale.
9.  Fare clic su **OK** nel pannello **Informazioni sull'app**.
10. Fare clic su **Aggiungi** nel pannello **Aggiungi app**.
    La suite viene visualizzata nell'elenco delle app come singola voce.

## <a name="configure-app-assignments"></a>Configurare le assegnazioni di app

In questo passaggio configurare le assegnazioni per la suite di app. 

1. Selezionare la suite di app **Office 365** nell'elenco delle app per visualizzare il pannello della panoramica **Office 365**.
2. Fare clic su **Assegnazioni** nel pannello **Office 365**.
3. Fare clic su **Aggiungi gruppo** per aggiungere un gruppo per l'utilizzo della suite di app. Viene visualizzato il pannello **Aggiungi gruppo**.
3. Impostare il **Tipo di assegnazione** su **Obbligatoria**.
4. Assegnare la suite ai gruppi scelti. Per altre informazioni, vedere [How to assign apps to groups with Microsoft Intune](apps-deploy.md) (Come assegnare app ai gruppi con Microsoft Intune).

    >[!Note]
    > Per tutti i gruppi per cui si richiede la suite di app Office 365, non è possibile disinstallarla tramite Microsoft Intune.

5. Selezionare **OK** nel pannello **Assegna**.
6. Selezionare **OK** nel pannello **Aggiungi gruppo**.
7. Selezionare **Salva** per confermare le assegnazioni.

## <a name="next-steps"></a>Passaggi successivi

- Per informazioni sull'aggiunta di app di Office 365 in un dispositivo Windows 10, vedere [Come assegnare le app di Office 365 ProPlus 2016 ai dispositivi Windows 10 con Microsoft Intune](apps-add-office365.md).
- Per informazioni su come includere ed escludere le assegnazioni delle app nei gruppi di utenti, vedere [Includere ed escludere assegnazioni di app](apps-inc-exl-assignments.md).
