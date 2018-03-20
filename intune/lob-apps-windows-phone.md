---
title: Come aggiungere app line-of-business per Windows Phone in Microsoft Intune
titlesuffix: 
description: Informazioni sull'aggiunta di app line-of-business (LOB) per Windows Phone in Intune.
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a097b7b2-d01d-454b-954c-da4f3cd0ae86
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8466a77929620ef9ef7c1559dae62990730d0acd
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-windows-phone-line-of-business-lob-apps-to-microsoft-intune"></a>Come aggiungere app line-of-business (LOB) per Windows Phone in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare le informazioni di questo articolo per aggiungere le app line-of-business per Windows Phone in Microsoft Intune. Un'app line-of-business (LOB) è un'app che viene aggiunta in Intune dal file di installazione di un'app. Questi tipi di app vengono in genere sviluppati internamente. Intune installa l'app line-of-business nel dispositivo dell'utente. 

## <a name="step-1---specify-the-software-setup-file"></a>Passaggio 1: specificare il file di installazione del software

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nel riquadro **Intune** scegliere **App per dispositivi mobili**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel riquadro **Aggiungi app** scegliere **App line-of-business**.

## <a name="step-2---configure-the-app-package-file"></a>Passaggio 2: configurare il file del pacchetto dell'app

1. Nel riquadro **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel riquadro **File del pacchetto dell'app** scegliere il pulsante Sfoglia e selezionare un file di installazione Windows Phone con estensione **xap**.
3. Al termine, scegliere **OK**.


## <a name="step-3---configure-app-information"></a>Passaggio 3: configurare le informazioni sull'app

1. Nel riquadro **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel riquadro **Informazioni sull'app** configurare le informazioni sull'app. A seconda dell'app scelta, è possibile che alcuni valori nel riquadro vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che viene visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Ignora la versione dell'app**: impostare su **Sì** se l'app viene aggiornata automaticamente dallo sviluppatore.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. L'uso delle categorie consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che viene associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
3. Al termine, scegliere **OK**.

## <a name="step-4---finish-up"></a>Passaggio 4: completare l'operazione

1. Nel riquadro **Aggiungi app** verificare di aver configurato correttamente le informazioni.
2. Scegliere **Aggiungi** per caricare l'app in Intune.

## <a name="next-steps"></a>Passaggi successivi

- L'app creata viene visualizzata nell'elenco di app. È ora possibile assegnarla ai gruppi scelti. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).

- Altre informazioni sulle modalità in cui è possibile monitorare le proprietà e l'assegnazione dell'app. Per altre informazioni, vedere [Come monitorare le informazioni sulle app e le assegnazioni](apps-monitor.md).

- Altre informazioni sul contesto dell'app in Intune. Per altre informazioni, vedere [Panoramica dei cicli di vita del dispositivo e dell'app](introduction-device-app-lifecycles.md)
