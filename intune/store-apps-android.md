---
title: Come aggiungere app di Android Store a Microsoft Intune
titleSuffix: 
description: Informazioni sull'aggiunta di app di Android Store a Microsoft Intune.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 87fea551dea1f80ee071fe6b477b84729e000874
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>Come aggiungere app di Android Store a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Prima di assegnare un'app a un dispositivo o a un gruppo di utenti, è necessario aggiungere l'app a Microsoft Intune. I passaggi seguenti permettono di aggiungere un app dello store di Android a Intune dal portale di Azure.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **App** nella sezione **Gestisci**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi app** selezionare **Android** nell'elenco dei tipi disponibili in **App Store**.
7. Selezionare **Configura** per configurare le informazioni sull'app seguenti. A seconda dell'app scelta, alcuni dei valori in questo riquadro potrebbero essere compilati automaticamente:
    - **Nome**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
    - **Sistema operativo minimo**: scegliere nell'elenco la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria** (facoltativo): selezionare una o più categorie di app predefinite oppure una categoria creata. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che contiene informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che contiene informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio **Reparto risorse umane** (facoltativo).
    - **Note**: immettere tutte le note da associare a questa app (facoltativo).
    - **Logo**: caricare un'icona che verrà associata all'app (facoltativo). Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
8. Fare clic su **OK** dopo aver immesso tutte le informazioni sull'app.
9. Fare clic su **Aggiungi** per aggiungere l'app.

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi scelti. 

##<a name="next-steps"></a>Passaggi successivi

- [Come assegnare app ai gruppi](apps-deploy.md)