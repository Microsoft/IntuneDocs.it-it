---
title: Aggiungere un'app line-of-business per Windows a Microsoft Intune
titlesuffix: ''
description: Informazioni su come aggiungere un'app line-of-business (LOB) per Windows usando Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 96b1bc23189faaad8aa8dd279352ef74c0b36e4b
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845432"
---
# <a name="add-a-windows-line-of-business-app-to-microsoft-intune"></a>Aggiungere un'app line-of-business per Windows a Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Un'app line-of-business è un'app che viene aggiunta da un apposito file di installazione. Questo tipo di app viene in genere scritto internamente. I passaggi seguenti forniscono istruzioni per l'aggiunta di un'app LOB per Windows a Microsoft Intune.

## <a name="step-1-specify-the-software-setup-file"></a>Passaggio 1: Specificare il file di installazione del software

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel carico di lavoro **App client** selezionare **Gestisci** > **App**.
5. Sopra l'elenco delle app selezionare **Aggiungi**.
6. Nel riquadro **Aggiungi app** selezionare **App line-of-business**.

## <a name="step-2-configure-the-app-package-file"></a>Passaggio 2: Configurare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** selezionare **File del pacchetto dell'app**.
2. Nel riquadro **File del pacchetto dell'app** selezionare il pulsante Sfoglia. Selezionare quindi un file di installazione di Windows con l'estensione **msi**, **appx** o **appxbundle**.

    > [!NOTE]
    > Le estensioni file per le app di Windows ora includono **msi**, **appx**, **appxbundle**, **msix** e **msixbundle**.  

1. Al termine, fare clic su **OK**.


## <a name="step-3-configure-app-information"></a>Passaggio 3: Configurare le informazioni sull'app

1. Nel riquadro **Aggiungi app** selezionare **Informazioni sull'app**.
2. Nel riquadro **Informazioni sull'app** configurare le informazioni seguenti. Alcuni dei valori in questo riquadro potrebbero venire inseriti automaticamente.
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata nel portale aziendale.
    - **Description**: Immettere una descrizione per l'app. La descrizione viene visualizzata nel portale aziendale.
    - **Autore**: Immettere il nome dell'autore dell'app.
    - **Ignora la versione dell'app**: impostare su **Sì** se lo sviluppatore dell'app aggiorna automaticamente l'app. Questa opzione si applica solo alle app MSI per dispositivi mobili.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Le categorie consentono agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: Visualizzare chiaramente l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato nel portale aziendale.
    - **Argomenti della riga di comando**: immettere gli argomenti della riga di comando da applicare per l'esecuzione del file con estensione msi (facoltativo). Un esempio è **/q**.
    - **Sviluppatore**: immettere il nome dello sviluppatore dell'app (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario dell'app (facoltativo). Un esempio è **Reparto risorse umane**.
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. L'icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3. Al termine, fare clic su **OK**.

## <a name="step-4-finish-up"></a>Passaggio 4: Terminare

1. Nel riquadro **Aggiungi app** verificare di aver configurato correttamente le informazioni sull'app.
2. Selezionare **Aggiungi** per caricare l'app in Intune.

## <a name="step-5-update-a-line-of-business-app"></a>Passaggio 5: Aggiornare un'app line-of-business

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configure-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurare un'app MSI per dispositivi mobili con aggiornamento automatico per ignorare il processo di controllo delle versioni

È possibile configurare un'app MSI per dispositivi mobili con aggiornamento automatico nota in modo che ignori il processo di controllo delle versioni. 

Alcune app basate sul programma di installazione MSI vengono aggiornate automaticamente dallo sviluppatore. Per queste app MSI con aggiornamento automatico, è possibile configurare l'impostazione **Ignora la versione dell'app** nel riquadro **Informazioni sull'app**. Se si cambia questa impostazione in **Sì**, Microsoft Intune non imporrà la versione dell'app installata nel client Windows. 

Questa funzionalità consente di evitare una race condition. Ad esempio, può verificarsi una race condition quando l'app viene aggiornata automaticamente dallo sviluppatore dell'app e viene aggiornata da Intune. In entrambi i casi è possibile che si provi a imporre una versione dell'app in un client di Windows creando un conflitto.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Vedere [Panoramica dei cicli di vita del dispositivo e dell'app](introduction-device-app-lifecycles.md).
