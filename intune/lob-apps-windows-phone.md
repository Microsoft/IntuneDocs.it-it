---
title: Aggiungere un'app line-of-business per Windows Phone a Microsoft Intune
titlesuffix: ''
description: Informazioni sull'aggiunta di un'app line-of-business per Windows Phone a Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ccc1f25d137675ba8e5f984a16324f4b0771dc9c
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224988"
---
# <a name="add-a-windows-phone-line-of-business-app-to-microsoft-intune"></a>Aggiungere un'app line-of-business per Windows Phone a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere un'app line-of-business per Windows Phone in Microsoft Intune. Un'app line-of-business è un'app che viene aggiunta in Intune dal file di installazione di un'app. Questo tipo di app viene in genere scritto internamente. Intune installa l'app line-of-business nel dispositivo dell'utente. 

## <a name="step-1-specify-the-software-setup-file"></a>Passaggio 1: Specificare il file di installazione del software

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** selezionare **Gestisci** > **App**.
5. Sopra l'elenco delle app selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app** selezionare **App line-of-business**.

## <a name="step-2-configure-the-app-package-file"></a>Passaggio 2: Configurare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** selezionare **File del pacchetto dell'app**.
2. Nel riquadro **File del pacchetto dell'app** selezionare il pulsante Sfoglia. Selezionare quindi un file di installazione di Windows Phone con l'estensione **xap**.
3. Al termine, fare clic su **OK**.


## <a name="step-3-configure-app-information"></a>Passaggio 3: Configurare le informazioni sull'app

1. Nel riquadro **Aggiungi app** selezionare **Informazioni sull'app**.
2. Nel riquadro **Informazioni sull'app** configurare le informazioni sull'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente.
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione viene visualizzata nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Ignora la versione dell'app**: impostare su **Sì** se lo sviluppatore dell'app aggiorna automaticamente l'app.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app. Un esempio è **Reparto risorse umane**.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3. Al termine, fare clic su **OK**.

## <a name="step-4-finish-up"></a>Passaggio 4: Completare l'operazione

1. Nel riquadro **Aggiungi app** verificare di aver configurato correttamente le informazioni.
2. Selezionare **Aggiungi** per caricare l'app in Intune.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Vedere [Panoramica dei cicli di vita del dispositivo e dell'app](introduction-device-app-lifecycles.md).
