---
title: Installare Office 365 nei dispositivi macOS con Intune
titlesuffix: Azure portal
description: "Informazioni su come usare Intune per renderne più semplice l'installazione delle app di Office 365 nei dispositivi macOS."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 12/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2372332a-7e3a-4a9c-91a9-86654e0fabe2
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1573a6a2ca78489df46c9e08ebbfe9a16b0731c7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-assign-office-365-to-macos-devices-with-microsoft-intune"></a>Come assegnare Office 365 a dispositivi macOS con Microsoft Intune

Con questo tipo di app è semplice assegnare app di Office 365 ai dispositivi macOS. Questo nuovo tipo di app consente di installare Word, Excel, PowerPoint, Outlook e OneNote. Queste app includono anche Microsoft AutoUpdate (MAU), per mantenere più sicure e aggiornate le app. Le app desiderate vengono visualizzate come un'unica app nell'elenco delle app nella console di Intune.


## <a name="before-you-start"></a>Prima di iniziare

- È necessario che i dispositivi in cui vengono distribuite le app eseguano macOS 10.10 o versioni successive.
- Intune supporta solo l'aggiunta di app di Office incluse nella suite Office 2016 per Mac.
- Se sono aperte app di Office quando Intune installa la suite di app, è possibile che gli utenti finali perdano i dati dei file non salvati.


## <a name="get-started"></a>Operazioni preliminari
Aggiungere Office 365 usando il pannello **App**.
1.  Accedere al portale di Azure.
2.  Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3.  Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4.  Nel carico di lavoro **App per dispositivi mobili** scegliere **App** nel gruppo **Gestisci**. Scegliere **Aggiungi**.
5.  Nel pannello **Aggiungi app** scegliere **Office 365** > **macOS**.
6.  Selezionare **Aggiungi**.

## <a name="configure-the-app-suite"></a>Configurare la suite di app

Specificare le informazioni sulla suite di app. Queste informazioni consentono di identificarla in Intune e permettono agli utenti di trovarla nell'app Portale aziendale.

1.  Nel pannello **Aggiungi app** scegliere **App Suite Information** (Informazioni sulla suite di app).
2.  Specificare le informazioni seguenti:
    - **Suite Name** (Nome suite): immettere il nome della suite di app visualizzato nel portale aziendale. Verificare che tutti i nomi di suite usati siano univoci. Se il nome di una suite viene usato due volte, solo una delle due suite viene visualizzata dagli utenti nel portale aziendale.
    - **Suite Description** (Descrizione suite): immettere una descrizione per la suite di app.
    - **Editore** -Microsoft viene visualizzato come editore.
    - **Categoria**: facoltativamente, selezionare una o più categorie di app predefinite oppure una categoria creata. L'uso delle categorie consente agli utenti di trovare più facilmente la suite di app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale** - La suite di app verrà visualizzata in primo piano nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore** -Microsoft viene visualizzato come sviluppatore.
    - **Proprietario** -Microsoft viene visualizzato come proprietario.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Carica icona**: caricare un'icona visualizzata con l'app dagli utenti nel portale aziendale.
3.  Selezionare **OK**. La suite viene visualizzata nell'elenco delle app come singola voce.

## <a name="configure-app-assignments"></a>Configurare le assegnazioni di app

In questo passaggio configurare le assegnazioni per la suite di app. Si noti che il tipo di app disponibili sarà presto disponibile.

1.  Selezionare la suite di app nell'elenco di app e selezionare **Assegnazioni**.
2.  Scegliere **Seleziona gruppi**.
3.  Assegnare la suite ai gruppi scelti. Per altre informazioni, vedere [How to assign apps to groups with Microsoft Intune](/intune/apps-deploy) (Come assegnare app ai gruppi con Microsoft Intune).
4.  Per ogni gruppo, è possibile selezionare **Require Install** (Richiedi installazione).
        >[!Note]
        > You cannot uninstall Office 365 through Intune.

5. Selezionare **Salva** per confermare le assegnazioni.

## <a name="next-steps"></a>Passaggi successivi

Per informazioni sull'aggiunta di app di Office 365 in un dispositivo Windows 10, vedere [Come assegnare le app di Office 365 ProPlus 2016 ai dispositivi Windows 10 con Microsoft Intune](/intune/apps-add-office365).
