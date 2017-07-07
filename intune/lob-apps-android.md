---
title: Come aggiungere app line-of-business per Android in Intune
titleSuffix: Intune on Azure
description: Informazioni sull'aggiunta di app line-of-business per Android a Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 061d793c-c724-4cd9-9240-adb0cbda5661
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 52a762e0d8990ab96053f5d3a092b3731ee00ca0
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-add-android-line-of-business-lob-apps-to-microsoft-intune"></a>Come aggiungere app line-of-business (LOB) per Android in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


## <a name="step-1---specify-the-software-setup-file"></a>Passaggio 1: specificare il file di installazione del software

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Gestisci le app**.
4. Nel carico di lavoro **App per dispositivi mobili** scegliere **Gestisci** > **App**.
5. In alto all'elenco delle applicazioni scegliere **Aggiungi**.
6. Nel pannello **Aggiungi app** scegliere **App line-of-business**.

## <a name="step-2---configure-the-app-package-file"></a>Passaggio 2: configurare il file del pacchetto dell'app

1. Nel pannello **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel pannello **File del pacchetto dell'app** scegliere il pulsante Sfoglia e selezionare un file di installazione Android con estensione **.apk**.
3. Al termine scegliere **OK**.


## <a name="step-3---configure-app-information"></a>Passaggio 3: configurare le informazioni sull'app

1. Nel pannello **Aggiungi app** scegliere **File del pacchetto dell'app**.
2. Nel pannello **Informazioni sull'app** configurare le informazioni seguenti. A seconda dell'app selezionata, è possibile che alcuni valori nel pannello vengano compilati automaticamente:
    - **Nome**: immettere il nome dell'app che verrà visualizzato nel portale aziendale. Verificare che tutti i nomi di app usati siano univoci. Se il nome di un'app è usato due volte, solo una delle due app verrà visualizzata agli utenti nel portale aziendale.
    - **Descrizione**: immettere una descrizione per l'app. La descrizione verrà visualizzata agli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **Sistema operativo minimo**: nell'elenco scegliere la versione minima del sistema operativo in cui è possibile installare l'app. L'installazione non verrà eseguita se si assegna l'app a un dispositivo con un sistema operativo precedente.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente. Ciò consentirà agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: visualizza chiaramente l'app nella pagina principale del portale aziendale quando gli utenti sfogliano le app.
    - **URL di informazioni**: immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **URL privacy**: immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL verrà visualizzato agli utenti nel portale aziendale.
    - **Developer**: immettere il nome dello sviluppatore dell'applicazione (facoltativo).
    - **Proprietario**: immettere un nome per il proprietario di questa app, ad esempio, **reparto risorse umane** (facoltativo).
    - **Note**: immettere eventuali note da associare a questa app.
    - **Logo**: caricare un'icona che verrà associata all'app. Questa icona verrà visualizzata insieme all'app quando gli utenti visitano il portale aziendale.
3. Al termine scegliere **OK**.

## <a name="step-4---finish-up"></a>Passaggio 4: completare l'operazione

1. Nel pannello **Aggiungi app** verificare che le informazioni configurate siano corrette.
2. Scegliere **Aggiungi** per caricare l'app in Intune.

L'app creata verrà visualizzata nell'elenco di app da cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Come assegnare app ai gruppi](apps-deploy.md).
