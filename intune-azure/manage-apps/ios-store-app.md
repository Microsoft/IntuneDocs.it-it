---
title: Come aggiungere app dello Store in Microsoft Intune | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: Informazioni sull&quot;aggiunta di app dello Store iOS a Intune.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c59514d7-1256-4576-9380-e7a0b85a0378
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 6026c942aea906e7e730152e6e92797ec5775bc3
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-add-ios-store-apps-to-microsoft-intune"></a>Come aggiungere app iOS Store a Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


## <a name="step-1---search-for-the-app-in-the-store"></a>Passaggio 1: cercare l'app nello Store

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro di **App per dispositivi mobili** scegliere **Gestisci** > App.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **Cerca in App Store**.
7. Nel pannello **App Store di Apple** immettere il nome o una parte del nome nella casella di ricerca. Intune eseguirà una ricerca nello Store e restituirà un elenco di risultati pertinenti.
8. Nell'elenco scegliere l'app desiderata, quindi fare clic su **OK**.

## <a name="step-2---configure-app-information"></a>Passaggio 2: configurare le informazioni sull'app

1. Nel pannello **Aggiungi app** scegliere **Informazioni sull'app**.
2. Nel pannello **Modifica l'app** configurare le informazioni seguenti. Al termine, fare clic su **Aggiungi**. A seconda dell'app selezionata, è possibile che alcuni valori nel pannello vengano compilati automaticamente:
- **Nome app**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione app**: immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
- **Autore**: immettere il nome dell'autore dell'app.
- **URL di App Store**: immettere l'URL dell'App Store per l'app che si vuole creare.
- **Sistema operativo minimo**: nell'elenco scegliere la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
- **Categoria** (facoltativo). Selezionare uno o più categorie di app predefinite oppure una categoria creata. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
- **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
- **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
- **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
- **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
- **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
- **Note**: immettere eventuali note da associare a questa app.
- **Carica l'icona**: Caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
3. Al termine, nel pannello **Aggiungi app** scegliere **Salva**.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](/intune-azure/manage-apps/deploy-apps).
