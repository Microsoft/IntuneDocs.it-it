---
title: Come aggiungere app line-of-business per Android in Microsoft Intune
titlesuffix: ''
description: Informazioni su come aggiungere app line-of-business (LOB) per Android in Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a5b09f855b6da65edf3c560725b339528f2bcfaa
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Come aggiungere app line-of-business (LOB) per Android in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Un'app line-of-business (LOB) è un'app che viene aggiunta in Intune dal file di installazione di un'app. Questi tipi di app vengono in genere sviluppati internamente. Intune installa l'app line-of-business nel dispositivo dell'utente. 

> [!Note]
> Per altre informazioni sulle app line-of-business (LOB) dello store Google Play for Work, vedere [Working with a line-of-business app from the Google Play for Work store](apps-add-android-for-work.md?#working-with-a-line-of-business-app-from-the-google-play-for-work-store) (Uso di un'app line-of-business dello store Google Play for Work). 

## <a name="step-1---specify-the-software-setup-file"></a>Passaggio 1: specificare il file di installazione del software

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi app** scegliere **App line-of-business**.

## <a name="step-2---configure-the-app-package-file"></a>Passaggio 2: configurare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel riquadro **File del pacchetto dell'app** scegliere il pulsante Sfoglia e selezionare un file di installazione Android con estensione **apk**.
3. Al termine, scegliere **OK**.


## <a name="step-3---configure-app-information"></a>Passaggio 3: configurare le informazioni sull'app

1. Nel riquadro **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel riquadro **Informazioni sull'app** aggiungere i dettagli relativi all'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app da visualizzare nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**: immettere la descrizione dell'app che gli utenti visualizzeranno nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Sistema operativo minimo**: nell'elenco scegliere la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Ignora la versione dell'app**: impostare su **Sì** se l'app viene aggiornata automaticamente dallo sviluppatore.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. L'uso delle categorie consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa è l'icona visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
3. Al termine, scegliere **OK**.

## <a name="step-4---finish-up"></a>Passaggio 4: completare l'operazione

1. Nel riquadro **Aggiungi app** verificare i dettagli dell'app.
2. Scegliere **Aggiungi** per caricare l'app in Intune.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

## <a name="step-5---update-a-line-of-business-app"></a>Passaggio 5: aggiornare un'app line-of-business

[!INCLUDE[shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!Note]
> Per consentire al servizio Intune di distribuire correttamente un nuovo file APK nel dispositivo, è necessario incrementare la stringa android:versionCode nel file AndroidManifest.xml del pacchetto APK.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Per altre informazioni, vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Per altre informazioni, vedere [Panoramica dei cicli di vita del dispositivo e dell'app](introduction-device-app-lifecycles.md)
