---
title: Come aggiungere app line-of-business per Windows in Microsoft Intune
titlesuffix: ''
description: Informazioni su come aggiungere app line-of-business (LOB) per Windows in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f81c5f82-5cfa-4b97-9f73-d6cf77c06896
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f975f2018d2ce1d7affded3c3386c479e6877388
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-add-windows-line-of-business-lob-apps-to-microsoft-intune"></a>Come aggiungere app line-of-business (LOB) per Windows in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Un'app line-of-business è un'app che viene aggiunta da un apposito file di installazione. Questi tipi di app vengono in genere sviluppati internamente. I passaggi seguenti forniscono istruzioni per l'aggiunta di un'app LOB per Windows a Microsoft Intune.

## <a name="step-1---specify-the-software-setup-file"></a>Passaggio 1: specificare il file di installazione del software

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi app** scegliere **App line-of-business**.

## <a name="step-2---configure-the-app-package-file"></a>Passaggio 2: configurare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel riquadro **File del pacchetto dell'app** scegliere il pulsante Sfoglia e selezionare un file di installazione Windows con estensione **msi**, **appx** o **appxbundle**.
3. Al termine, scegliere **OK**.


## <a name="step-3---configure-app-information"></a>Passaggio 3: configurare le informazioni sull'app

1. Nel riquadro **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel riquadro **Informazioni sull'app** configurare le informazioni seguenti (alcuni valori del riquadro potrebbero essere compilati automaticamente):
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Ignora la versione dell'app**: impostare su **Sì** se l'app viene aggiornata automaticamente dallo sviluppatore.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. La categorizzazione delle app consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Argomenti della riga di comando**: immettere facoltativamente gli argomenti della riga di comando da applicare per l'esecuzione del file con estensione msi, ad esempio **/q**.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. L'icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3. Al termine, scegliere **OK**.

## <a name="step-4---finish-up"></a>Passaggio 4: completare l'operazione

1. Nel riquadro **Aggiungi app** verificare di aver configurato correttamente le informazioni sull'app.
2. Scegliere **Aggiungi** per caricare l'app in Intune.

## <a name="step-5---update-a-line-of-business-app"></a>Passaggio 5: aggiornare un'app line-of-business

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

## <a name="configuring-a-self-updating-mobile-msi-app-to-ignore-the-version-check-process"></a>Configurazione di un'app MSI per dispositivi mobili con aggiornamento automatico per ignorare il processo di controllo delle versioni

È possibile configurare un'app MSI per dispositivi mobili con aggiornamento automatico nota, per ignorare il processo di controllo delle versioni. Alcune app basate sul programma di installazione MSI vengono aggiornate automaticamente dallo sviluppatore. Per queste app MSI con aggiornamento automatico, è possibile configurare l'impostazione **Ignora la versione dell'app** nel pannello **Informazioni sull'app**. Se questa impostazione viene cambiata in **Sì**, Microsoft Intune non imporrà la versione dell'app installata nel client Windows. Questa funzionalità consente di evitare una race condition. Ad esempio, questo tipo di race condition può verificarsi quando l'app viene aggiornata automaticamente dallo sviluppatore di app e anche da Intune. In entrambi i casi è possibile che si tenti di imporre una versione dell'app in un client di Windows creando un conflitto.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Per altre informazioni, vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Per altre informazioni, vedere [Panoramica dei cicli di vita del dispositivo e dell'app](introduction-device-app-lifecycles.md)
