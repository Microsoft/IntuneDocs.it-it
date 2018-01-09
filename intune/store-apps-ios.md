---
title: Come aggiungere app iOS Store a Intune | Microsoft Docs
titlesuffix: Azure portal
description: Informazioni sull'aggiunta di app dello Store iOS a Intune."
keywords: Intune
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7dcb857127b3c36d2b90208aac9b8ad901e31d89
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Come aggiungere app iOS Store a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


Usare le informazioni di questo argomento per aggiungere le app dello Store iOS a Intune.

>[!NOTE]
>Anche se gli utenti dei dispositivi iOS possono rimuovere alcune delle app iOS predefinite, ad esempio Borsa e Mappe, non è possibile usare Intune per ridistribuire tali app. Se gli utenti finali eliminano queste app, devono accedere all'App Store e reinstallarle manualmente.

## <a name="before-you-start"></a>Prima di iniziare

È possibile assegnare le app solo con questo metodo se sono gratuite nell'App Store. Per assegnare app a pagamento con Intune, valutare la possibilità di usare [Volume Purchase Program iOS](vpp-apps-ios.md).


## <a name="step-1---search-for-the-app-in-the-store"></a>Passaggio 1: cercare l'app nello Store

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro di **App per dispositivi mobili** scegliere **Gestisci** > App.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **Cerca in App Store**.
7. Nel pannello **App Store di Apple** selezionare le impostazioni locali del paese per App Store.
8. Digitare il nome (o una parte del nome) nella casella di ricerca. Intune esegue la ricerca nello Store e restituisce un elenco di risultati pertinenti.
9. Nell'elenco scegliere l'app desiderata, quindi fare clic su **OK**.

## <a name="step-2---configure-app-information"></a>Passaggio 2: configurare le informazioni sull'app

1. Nel pannello **Aggiungi app** scegliere **Informazioni sull'app**.
2. Nel pannello **Modifica l'app** configurare le informazioni relative all'app. Al termine, fare clic su **Aggiungi**. A seconda dell'app selezionata, è possibile che alcuni valori nel pannello vengano compilati automaticamente:
- **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, il portale aziendale mostra agli utenti una sola app.
- **Descrizione**: immettere la descrizione dell'app che gli utenti visualizzano nel portale aziendale.
- **Autore**: immettere il nome dell'autore dell'app.
- **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
- **Store country/region** (Paese/area di App Store): selezionare le impostazioni locali dell'area geografica di App Store.
- **Sistema operativo minimo**: scegliere nell'elenco la versione minima del sistema operativo in cui è possibile installare l'app. L'app non verrà installata su un dispositivo con un sistema operativo precedente.
- **Tipo di dispositivo applicabile**: scegliere nell'elenco i dispositivi che vengono usati dall'app.
- **Categoria** (facoltativo). Selezionare uno o più categorie di app predefinite oppure una categoria creata. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
- **Visualizza come app in primo piano nel portale aziendale**: evidenzia l'app nella pagina principale del portale aziendale Intune quando gli utenti sfogliano le app.
- **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
- **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
- **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo). Questo campo è visibile solo per gli amministratori e non per gli utenti finali.
- **Proprietario**: immettere il nome del proprietario di questa app, ad esempio **Reparto risorse umane** (facoltativo).  Questo campo è visibile solo per gli amministratori e non per gli utenti finali.
- **Note**: immettere eventuali note da associare a questa app. Questo campo è visibile solo per gli amministratori e non per gli utenti finali.
- **Logo**: caricare un'icona che viene associata all'app. L'icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3. Al termine, nel pannello **Aggiungi app** scegliere **OK**.

L'app creata viene visualizzata nell'elenco di app e da qui è possibile assegnarla ai gruppi desiderati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).
