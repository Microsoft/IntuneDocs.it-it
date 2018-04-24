---
title: Come aggiungere app dello Store iOS a Microsoft Intune
titlesuffix: ''
description: Informazioni sull'aggiunta di app dello Store iOS a Microsoft Intune.
keywords: Intune
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4eaa4b279ab98c6fe41482628937e0f2b0dc70a5
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Come aggiungere app dello Store iOS a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere le app dello Store iOS a Microsoft Intune. Le app delle Store iOS sono app installate da Intune in un dispositivo dell'utente. L'utente fa parte della forza lavoro della società. Le app dello Store iOS vengono aggiornate automaticamente.

>[!NOTE]
>Anche se gli utenti dei dispositivi iOS possono rimuovere alcune delle app iOS predefinite, ad esempio Borsa e Mappe, non è possibile usare Intune per ridistribuire tali app. Se gli utenti finali eliminano queste app, devono accedere all'App Store e reinstallarle manualmente.

## <a name="before-you-start"></a>Prima di iniziare

È possibile assegnare le app solo con questo metodo se sono gratuite nell'App Store. Per assegnare app a pagamento con Intune, valutare la possibilità di usare [Volume Purchase Program iOS](vpp-apps-ios.md).

>[!NOTE]
>Chrome e Microsoft Edge sono i browser consigliati per l'utilizzo con Microsoft Intune.

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel pannello **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **App** nella sezione **Gestisci**.
5. Scegliere **Aggiungi** sul lato destro del riquadro **App**.
6. Nell'elenco **Tipo di app** selezionare **iOS** dai tipi di **App Store** disponibili.
7. Scegliere **Cerca in App Store**.
8. Nel pannello **Cerca in App Store** selezionare le impostazioni locali del paese per App Store.
9. Digitare il nome (o una parte del nome) nella casella di ricerca. Intune esegue la ricerca nello Store e restituisce un elenco di risultati pertinenti.
10. Scegliere l'app nell'elenco e fare clic su **Seleziona**.
11. Nel pannello **Aggiungi app** scegliere **Informazioni sull'app** per configurare l'app.
12. Nel pannello **Informazioni sull'app** aggiungere le informazioni sull'app. A seconda dell'app selezionata, è possibile che alcuni valori nel pannello vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, il portale aziendale mostra agli utenti una sola app.
    - **Descrizione**: immettere la descrizione dell'app che gli utenti visualizzano nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
    - **Sistema operativo minimo**: scegliere nell'elenco la versione minima del sistema operativo in cui è possibile installare l'app. L'app non verrà installata su un dispositivo con un sistema operativo precedente.
    - **Tipo di dispositivo applicabile**: scegliere nell'elenco i dispositivi che vengono usati dall'app.
    - **Categoria** (facoltativo). Selezionare uno o più categorie di app predefinite oppure una categoria creata. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: evidenzia l'app nella pagina principale del portale aziendale Intune quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo). Questo campo è visibile solo per gli amministratori e non per gli utenti.
    - **Proprietario**: immettere il nome del proprietario di questa app, ad esempio **Reparto risorse umane** (facoltativo).  Questo campo è visibile solo per gli amministratori e non per gli utenti.
    - **Note**: immettere eventuali note da associare a questa app. Questo campo è visibile solo per gli amministratori e non per gli utenti.
    - **Logo**: caricare un'icona che viene associata all'app. L'icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
13. Al termine, fare clic su **OK** nel pannello **Aggiungi informazioni**.
14. Fare clic su **Aggiungi** nel pannello **Aggiungi app**.

L'app creata viene visualizzata nell'elenco di app e da qui è possibile assegnarla ai gruppi desiderati.

## <a name="next-steps"></a>Passaggi successivi

- [Come assegnare app ai gruppi](apps-deploy.md)
