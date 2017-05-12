---
title: Come aggiungere app Android dello store a Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni sull&quot;aggiunta di app Android dello store a Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4433000a-23e9-4cad-a818-48c28eedc1f5
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 3758df744311392528be01c826527c2a9d879975
ms.openlocfilehash: fe0c54356454f92ed7de79a5857c8473d0421656
ms.contentlocale: it-it
ms.lasthandoff: 05/10/2017

---

# <a name="how-to-add-android-store-apps-to-microsoft-intune"></a>Come aggiungere app di Android Store a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello Intune, scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **Informazioni sull'app**.
7. Nel pannello **Modifica l'app** configurare le informazioni seguenti. Al termine, fare clic su **Aggiungi**. A seconda dell'app selezionata, è possibile che alcuni valori nel pannello vengano compilati automaticamente:
    - **Nome app**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione app**: immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
    - **Sistema operativo minimo**: nell'elenco scegliere la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria (facoltativo)**: selezionare una o più categorie di app predefinite oppure una categoria creata. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Carica l'icona**: Caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
8. Al termine, nel pannello **Aggiungi app** scegliere **Salva**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](deploy-apps.md).
