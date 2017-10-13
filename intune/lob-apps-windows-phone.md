---
title: Come aggiungere app line-of-business per Windows Phone in Intune
titlesuffix: Azure portal
description: Informazioni sull'aggiunta di app line-of-business per Windows Phone a Intune."
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 10/3/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 60776df3774d4f9ca7404ef04b1cc94536bcd164
ms.sourcegitcommit: 4b776d1a87c0707244f4ae0122de882e0eef6fa3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2017
---
# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>Come aggiungere app line-of-business (LOB) per Windows Phone in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Passaggio 1: specificare il file di installazione del software

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** + **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **App line-of-business**.

## <a name="step-2---configure-the-app-package-file"></a>Passaggio 2: configurare il file del pacchetto dell'app

1. Nel pannello **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel pannello **File del pacchetto dell'app** scegliere il pulsante Sfoglia e selezionare un file di installazione Windows Phone con estensione **xap**.
3. Al termine scegliere **OK**.


## <a name="step-3---configure-app-information"></a>Passaggio 3: configurare le informazioni sull'app

1. Nel pannello **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel pannello **Informazioni sull'app** configurare le informazioni sull'app. A seconda dell'app selezionata, è possibile che alcuni valori nel pannello vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. L'uso delle categorie consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3. Al termine scegliere **OK**.

## <a name="step-4---finish-up"></a>Passaggio 4: completare l'operazione

1. Nel pannello **Aggiungi app** verificare di aver configurato correttamente le informazioni.
2. Scegliere **Aggiungi** per caricare l'app in Intune.

## <a name="next-steps"></a>Passaggi successivi

L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Per altre informazioni, vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

Altre informazioni sul contesto dell'app in Intune. Per altre informazioni, vedere [Panoramica dei cicli di vita del dispositivo e dell'app](introduction-device-app-lifecycles.md)
