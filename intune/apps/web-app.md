---
title: Aggiungere app Web a Microsoft Intune
titleSuffix: ''
description: Informazioni sull'aggiunta di app Web (applicazioni client-server) a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6600c75ce3e6120143b17fb863670b2eb423a09f
ms.sourcegitcommit: ae6f2e7812e7fd36f2393b8f4b6cd8de63777b2c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2019
ms.locfileid: "73592048"
---
# <a name="add-web-apps-to-microsoft-intune"></a>Aggiungere app Web a Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune supporta un'ampia gamma di tipi di app, incluse le app Web. Un'app Web è un'applicazione client-server. Il server fornisce l'app Web che include interfaccia utente, contenuto e funzionalità. Le moderne piattaforme di hosting Web in genere offrono anche sicurezza, bilanciamento del carico e altri vantaggi. Un'app Web viene gestita separatamente nel Web. Usare Microsoft Intune per puntare a questo tipo di app. Assegnare anche i gruppi di utenti autorizzati ad accedere all'app. 

Prima di poter gestire e assegnare un'app per gli utenti, è necessario aggiungerla in Intune. 

Intune crea un collegamento all'app Web nel dispositivo dell'utente. Per i dispositivi iOS, viene aggiunto un collegamento all'app Web nella schermata iniziale. Per i dispositivi Android, viene aggiunto un collegamento all'app Web nel widget del portale aziendale di Intune e il widget deve essere aggiunto manualmente dall'utente. Per i dispositivi Windows, viene aggiunto un collegamento all'app Web nel menu Start.

> [!Note]
> Per avviare app Web, è necessario che nel dispositivo dell'utente sia installato un browser.

## <a name="add-a-web-app-to-intune"></a>Aggiungere un'app Web a Intune
Per aggiungere un'app a Intune come collegamento a un'app nel Web, eseguire le operazioni seguenti:

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Nel riquadro **Intune** selezionare **App client**.
4. Nel riquadro del carico di lavoro **App client** in **Gestisci** selezionare **App**.
5. Nel riquadro **App** selezionare **Aggiungi**.
6. Nell'elenco a discesa **Tipo di app** del riquadro **Aggiungi app** selezionare il tipo **Collegamento Web**.
7. Selezionare **Configura**.
8. Nel riquadro **Informazioni sull'app** aggiungere le informazioni seguenti:
    - **Nome**:  immettere il nome dell'app che deve essere visualizzato nel portale aziendale. 

        > [!NOTE]
        > Se si modifica il nome dell'app tramite il portale di Azure di Intune dopo avere distribuito e installato l'app, l'app non potrà più essere usata come destinazione usando i comandi.

    - **Description**: Immettere una descrizione per l'app. Questa descrizione viene visualizzata dagli utenti nel portale aziendale.
    - **Autore**: immettere il nome dell'autore dell'app.
    - **URL app**: immettere l'URL del sito Web che ospita l'app da assegnare.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa operazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano la suite di app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **Richiedi un browser gestito per l'apertura del collegamento**: selezionare questa opzione per assegnare agli utenti un collegamento a un sito Web o a un'app Web che possono aprire in Intune Managed Browser. Questo browser deve essere installato nel dispositivo.
    - **Logo**: Caricare un'icona che verrà associata all'app. Questa icona viene visualizzata con l'app quando gli utenti visitano il portale aziendale.
9. Selezionare **OK**.
10. Selezionare **Aggiungi** nel riquadro **Aggiungi app**.

> [!Note]
> Gli utenti devono aggiungere il widget di Intune nella schermata iniziale per visualizzare le app Web che sono state assegnate a dispositivi Android.
>
> Attualmente, la distribuzione di app Web di Intune in dispositivi iOS è associata al profilo di gestione e non può essere rimossa manualmente. È possibile modificare il tipo di distribuzione impostando **Disinstalla** nel portale di Intune e in questo modo l'app Web può essere rimossa automaticamente. Tuttavia, se si rimuove la distribuzione prima di modificare la finalità dell'assegnazione di app in **Disinstalla**, l'app Web rimarrà in modo permanente nel dispositivo fino a quando non si annulla la registrazione del dispositivo da Intune.

## <a name="next-steps"></a>Passaggi successivi

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. Per altre informazioni, vedere [Assegnare app ai gruppi](apps-deploy.md). 
