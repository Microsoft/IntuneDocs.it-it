---
title: Come aggiungere app di Windows Phone 8.1 Store a Microsoft Intune
titleSuffix: 
description: Informazioni sull'aggiunta di app dello Store per Windows Phone 8.1 in Microsoft Intune.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e4c3935c8dc263ceef9981a9fc9c47ace6f77d86
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-windows-phone-81-store-apps-to-microsoft-intune"></a>Come aggiungere app di Windows Phone 8.1 Store a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Prima di assegnare un'app a un dispositivo o a un gruppo di utenti, è necessario aggiungere l'app a Microsoft Intune. I passaggi seguenti permettono di aggiungere un'app dello Store per Windows Phone 8.1 in Intune dal portale di Azure.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi app** scegliere il **Tipo di app** **Windows Phone 8.1** e scegliere **Informazioni sull'app**.
7. Nel riquadro **Informazioni sull'app** configurare le informazioni seguenti. Al termine, fare clic su **OK**. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
    - **Categoria (facoltativo)**: selezionare una o più categorie di app predefinite oppure una categoria creata. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
8. Al termine, nel riquadro **Aggiungi app** scegliere **Aggiungi**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

## <a name="next-steps"></a>Passaggi successivi

- [Come assegnare app ai gruppi](apps-deploy.md)