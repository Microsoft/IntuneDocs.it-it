---
title: Aggiungere un'app line-of-business per iOS a Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere un'app line-of-business (LOB) per iOS in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/15/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 099101e8-4b22-40ac-ba19-82ba5c71944c
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c9b11e8968426a39c3bfc3d13a0a42c97a04f27
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72497804"
---
# <a name="add-an-ios-line-of-business-app-to-microsoft-intune"></a>Aggiungere un'app line-of-business per iOS a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere un'app line-of-business per iOS in Microsoft Intune. Un'app line-of-business (LOB) è un'app che viene aggiunta in Intune dal file di installazione di un'app IPA. Questo tipo di app viene in genere scritto internamente. Per prima cosa è necessario entrare nel programma iOS Developer Enterprise Program. Per altre informazioni su come eseguire questa operazione, vedere [il sito Web Apple](https://developer.apple.com/programs/ios/enterprise/).

>[!NOTE]
>Gli utenti dei dispositivi iOS possono rimuovere alcune delle app iOS predefinite, ad esempio Borsa e Mappe. Non è possibile usare Intune per ridistribuire queste app. Se gli utenti eliminano queste app, devono accedere all'App Store e reinstallarle manualmente.
>
>Le app line-of-business iOS hanno un limite massimo di dimensioni di 4 GB per app.

## <a name="step-1-specify-the-software-setup-file"></a>Passaggio 1: Specificare il file di installazione del software

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel carico di lavoro **App client** selezionare **Gestisci** > **App**.
5. Sopra l'elenco delle app selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app** selezionare **App line-of-business**.

## <a name="step-2-configure-the-app-package-file"></a>Passaggio 2: Configurare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** selezionare **File del pacchetto dell'app**.
2. Nel riquadro **File del pacchetto dell'app** selezionare il pulsante Sfoglia. Selezionare quindi un file di installazione iOS con l'estensione **ipa**.
3. Al termine, fare clic su **OK**.


## <a name="step-3-configure-app-information"></a>Passaggio 3: Configurare le informazioni sull'app

1. Nel riquadro **Aggiungi app** selezionare **Informazioni sull'app**.
2. Nel riquadro **Informazioni sull'app** aggiungere i dettagli relativi all'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente.
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata nel portale aziendale.
    - **Description**: Immettere una descrizione per l'app. La descrizione viene visualizzata nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **Sistema operativo minimo**: selezionare dall'elenco la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: Visualizzare chiaramente l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario dell'app (facoltativo). Un esempio è **Reparto risorse umane**.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3. Al termine, fare clic su **OK**.

## <a name="step-4-finish-up"></a>Passaggio 4: Terminare

1. Nel riquadro **Aggiungi app** verificare che i dettagli dell'app siano corretti.
2. Selezionare **Aggiungi** per caricare l'app in Intune.

L'app creata viene ora visualizzata nell'elenco di app. Dall'elenco è possibile assegnare le app ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

> [!NOTE]
> I profili di provisioning per le app line-of-business iOS hanno un preavviso di 30 giorni prima di scadere.

## <a name="step-5-update-a-line-of-business-app"></a>Passaggio 5: Aggiornare un'app line-of-business

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

L'aggiornamento dell'app line-of-business verrà installato automaticamente.

> [!NOTE]
> Per consentire al servizio Intune di distribuire correttamente un nuovo file IPA nel dispositivo, è necessario incrementare la stringa `CFBundleVersion` nel file Info.plist nel pacchetto IPA.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Vedere [Panoramica dei cicli di vita del dispositivo e dell'app](../fundamentals/device-lifecycle.md).
