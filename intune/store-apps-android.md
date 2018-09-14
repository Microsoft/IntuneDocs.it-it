---
title: Aggiungere app di Android Store a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app di Android Store a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2677009921a9c498f988bdc674db6342613a05d6
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347730"
---
# <a name="add-android-store-apps-to-microsoft-intune"></a>Aggiungere app di Android Store a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Prima di assegnare un'app a un dispositivo o a un gruppo di utenti, è necessario aggiungere l'app a Microsoft Intune. Seguire questa procedura per aggiungere un'app di Android Store a Intune dal portale di Azure:

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**.  
    Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Gestisci** selezionare **App**.
5. Selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app** selezionare **Android** nell'elenco dei tipi disponibili in **App Store**.
7. Per configurare le informazioni sull'app, selezionare **Configura** e specificare le informazioni seguenti. Per le app Android, passare a [Google Play Store](https://play.google.com/store) e cercare l'app da distribuire. Selezionare l'app e annotare i dettagli dell'app. A seconda dell'app scelta, è possibile che alcuni valori vengano compilati automaticamente.
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale. Assicurarsi che il nome dell'app usato sia univoco. Se il nome dell'app è duplicato, nel portale aziendale sarà visualizzato un solo nome.
    - **Descrizione**: immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
    - **Sistema operativo minimo**: scegliere nell'elenco la versione meno recente del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria**: facoltativamente, selezionare una o più categorie di app predefinite oppure una categoria creata. Questa operazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, *Reparto risorse umane* (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
    - **Logo**: caricare un'icona da associare all'app (facoltativo). Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
1. Selezionare **OK**.
2. Selezionare **Aggiungi**.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. 

## <a name="next-steps"></a>Passaggi successivi

- [Assegnare app ai gruppi](apps-deploy.md)
