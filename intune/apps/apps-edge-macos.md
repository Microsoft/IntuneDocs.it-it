---
title: Aggiungere Microsoft Edge ai dispositivi macOS usando Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere Microsoft Edge ai dispositivi macOS usando Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c31dd652022ae0d394ab2229a0c25b362ad8574d
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563579"
---
# <a name="add-microsoft-edge-to-macos-devices-using-microsoft-intune"></a>Aggiungere Microsoft Edge ai dispositivi macOS usando Microsoft Intune

Prima di poter distribuire, configurare, monitorare o proteggere le app è necessario aggiungerle a Intune. Uno dei tipi di [app disponibili](~/apps/apps-add.md#app-types-in-microsoft-intune) è Microsoft Edge *versione 77 e successive*. Selezionando questo tipo di app in Intune, è possibile assegnare e installare Microsoft Edge *versione 77 e successive* nei dispositivi gestiti che eseguono macOS. Questo tipo di app semplifica l'assegnazione di Microsoft Edge ai dispositivi macOS senza che sia necessario usare lo strumento di wrapping delle app macOS. Per mantenere più sicure e aggiornate le app, queste includono anche Microsoft AutoUpdate (MAU).

> [!IMPORTANT]
> Questo tipo di app è disponibile in **anteprima pubblica** e viene offerta nei canali per sviluppatori e beta per macOS. La distribuzione è solo in lingua inglese (EN), ma gli utenti finali possono modificare la lingua di visualizzazione nel browser in **Impostazioni** > **Lingue**. 

> [!NOTE]
> Microsoft Edge *versione 77 e successive* è disponibile anche per Windows 10.

## <a name="prerequisites"></a>Prerequisiti
- Prima di installare Microsoft Edge, il dispositivo macOS deve eseguire macOS 10.12 o versione successiva.

## <a name="add-microsoft-edge-to-intune"></a>Aggiungere Microsoft Edge a Intune
È possibile aggiungere Microsoft Edge versione 77 e successive seguendo questa procedura:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Nell'elenco **Tipo di app** in **Microsoft Edge versione 77 e successive** selezionare **macOS**.

## <a name="configure-app-information"></a>Configurare le informazioni sull'app
In questo passaggio verranno specificate le informazioni su questa distribuzione di app. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovarla nel portale aziendale.

1. Fare clic su **Informazioni sull'app** per visualizzare il riquadro **Informazioni sull'app**.
2. Nel riquadro **Informazioni sull'app** specificare le informazioni su questa distribuzione di app. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovarla nel portale aziendale.
    - **Nome**: Immettere il nome dell'app che verrà visualizzato nel portale aziendale. Assicurarsi che tutti i nomi siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    - **Description**: Immettere una descrizione per l'app. Ad esempio, è possibile elencare gli utenti di destinazione nella descrizione.
    - **Autore**: come editore viene visualizzato Microsoft.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa impostazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: come sviluppatore viene visualizzato Microsoft.
    - **Proprietario**: come proprietario viene visualizzato Microsoft.
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
3. Selezionare **OK**.

## <a name="configure-microsoft-edge-settings"></a>Configurare le impostazioni di Microsoft Edge
In questo passaggio configurare le opzioni di installazione per l'app.

1. Nel riquadro **Aggiungi app** selezionare **Impostazioni dell'app**.
2. Nel riquadro **Impostazioni app** il canale **Beta** viene selezionato automaticamente e non può essere modificato.
    - Il canale **Beta** corrisponde all'esperienza di anteprima di Microsoft Edge più stabile ed è la scelta migliore per un progetto pilota completo all'interno dell'organizzazione. Con aggiornamenti principali ogni sei settimane.

    > [!NOTE]
    > Il logo del browser Microsoft Edge viene visualizzato insieme all'app quando gli utenti visitano il portale aziendale.
3.  Selezionare **OK**.

## <a name="select-scope-tags-optional"></a>Selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti.
1.  Selezionare **Ambito (tag)**  > **Aggiungi**.
2.  Usare la casella **Seleziona** per cercare i tag di ambito.
3.  Selezionare la casella di controllo accanto ai tag di ambito da assegnare a questa app.
4.  Fare clic su **Seleziona** > **OK**.

## <a name="add-the-app"></a>Aggiungere l'app
Al termine della configurazione, selezionare **Aggiungi** nel riquadro **Aggiungi app**. 

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. 

> [!NOTE]
> Attualmente Apple non consente a Intune di disinstallare Microsoft Edge nei dispositivi macOS.

## <a name="next-steps"></a>Passaggi successivi
- Per informazioni su come configurare Microsoft Edge nei dispositivi macOS, vedere [Configurare Microsoft Edge nei dispositivi macOS](https://docs.microsoft.com/deployedge/configure-microsoft-edge-on-mac).
- Per informazioni su come includere ed escludere le assegnazioni delle app nei gruppi di utenti, vedere [Includere ed escludere assegnazioni di app](~/apps/apps-inc-exl-assignments.md).
- [Assegnare app ai gruppi](~/apps/apps-deploy.md)

