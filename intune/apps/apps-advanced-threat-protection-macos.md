---
title: Aggiungere Microsoft Defender ATP ai dispositivi macOS usando Microsoft Intune
titleSuffix: ''
description: Informazioni su come aggiungere Microsoft Defender ATP ai dispositivi macOS usando Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
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
ms.openlocfilehash: 6ae6e8a621b10ec969fa3fcfb2dfeabb8d5a7bdd
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569560"
---
# <a name="add-microsoft-defender-atp-to-macos-devices-using-microsoft-intune"></a>Aggiungere Microsoft Defender ATP ai dispositivi macOS usando Microsoft Intune

Prima di poter distribuire, configurare, monitorare o proteggere le app è necessario aggiungerle a Intune. Uno dei [tipi di app](~/apps/apps-add.md#app-types-in-microsoft-intune) disponibili è Microsoft Defender Advanced Threat Protection (ATP). Selezionando questo tipo di app in Intune, è possibile assegnare e installare Microsoft Defender ATP nei dispositivi gestiti che eseguono macOS. Questo tipo di app semplifica l'assegnazione di Microsoft Defender ATP ai dispositivi macOS senza che sia necessario usare lo strumento di wrapping delle app macOS. Per mantenere più sicure e aggiornate le app, queste includono anche Microsoft AutoUpdate (MAU).

## <a name="prerequisites"></a>Prerequisiti
- Il dispositivo macOS deve eseguire macOS 10.13 o versioni successive.
- Il dispositivo macOS deve avere almeno 650 MB di spazio su disco.
- Distribuire l'estensione del kernel in Intune. Per altre informazioni, vedere [Aggiungere le estensioni del kernel macOS in Intune](~/configuration/kernel-extensions-overview-macos.md).

> [!IMPORTANT]
> L'estensione del kernel può essere approvata automaticamente solo se è presente nel dispositivo prima dell'installazione dell'app Microsoft Defender ATP. In caso contrario, gli utenti visualizzeranno un messaggio relativo al "blocco dell'estensione di sistema" nei computer Mac e dovranno approvare l'estensione passando a **Preferenze di protezione** o **Preferenze di sistema** > **Sicurezza e privacy** e quindi selezionando **Consenti**. Per altre informazioni, vedere [Risolvere i problemi dell'estensione del kernel in Microsoft Defender ATP per Mac](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-support-kext).

## <a name="add-microsoft-defender-atp-to-intune"></a>Aggiungere Microsoft Defender ATP a Intune
È possibile aggiungere Microsoft Defender ATP a Intune seguendo questa procedura:

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **App** > **Tutte le app** > **Aggiungi**.
3. Nell'elenco **Tipo di app** in **Microsoft Defender ATP** selezionare **macOS**.

## <a name="configure-app-information"></a>Configurare le informazioni sull'app
In questo passaggio verranno specificate le informazioni su questa distribuzione di app. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovarla nel portale aziendale.

1. Fare clic su **Informazioni sull'app** per visualizzare il riquadro **Informazioni sull'app**.
2. Nel riquadro **Informazioni sull'app** specificare le informazioni su questa distribuzione di app. Queste informazioni consentono di identificare l'app in Intune e permettono agli utenti di trovarla nel portale aziendale.
    - **Nome**: Immettere il nome dell'app che verrà visualizzato nel portale aziendale. Assicurarsi che tutti i nomi siano univoci. Se il nome di un'app è usato due volte, solo una delle due app viene visualizzata dagli utenti nel portale aziendale.
    - **Descrizione**: Immettere una descrizione per l'app. Ad esempio, è possibile elencare gli utenti di destinazione nella descrizione.
    - **Autore**: come editore viene visualizzato Microsoft.
    - **Categoria**: selezionare una o più categorie di app predefinite o una categoria creata dall'utente (facoltativo). Questa impostazione consente agli utenti di trovare più facilmente l'app nel portale aziendale.
    - **Visualizza come app in primo piano nel portale aziendale**: selezionare questa opzione per visualizzare in primo piano l'app nella pagina principale del portale aziendale quando gli utenti cercano le app.
    - **URL di informazioni**: Immettere l'URL di un sito Web che include informazioni sull'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **URL privacy**: Immettere l'URL di un sito Web che include informazioni sulla privacy per l'app (facoltativo). L'URL viene visualizzato dagli utenti nel portale aziendale.
    - **Sviluppatore**: come sviluppatore viene visualizzato Microsoft.
    - **Proprietario**: come proprietario viene visualizzato Microsoft.
    - **Note**: immettere eventuali note da associare a questa app (facoltativo).
3. Selezionare **OK**.

## <a name="select-scope-tags-optional"></a>Selezionare i tag di ambito (facoltativo)
È possibile usare i tag di ambito per determinare chi può visualizzare le informazioni sull'app client in Intune. Per informazioni dettagliate complete sui tag di ambito, vedere Usare il controllo degli accessi in base al ruolo e i tag di ambito per ambienti IT distribuiti.
1.  Selezionare **Ambito (tag)** > **Aggiungi**.
2.  Usare la casella **Seleziona** per cercare i tag di ambito.
3.  Selezionare la casella di controllo accanto ai tag di ambito da assegnare a questa app.
4.  Fare clic su **Seleziona** > **OK**.

## <a name="add-the-app"></a>Aggiungere l'app
Al termine della configurazione, selezionare **Aggiungi** nel riquadro **Aggiungi app**. 

L'app creata viene visualizzata nell'elenco di app, in cui è possibile assegnarla ai gruppi selezionati. 

> [!NOTE]
> Attualmente Apple non consente a Intune di disinstallare Microsoft Defender ATP nei dispositivi macOS.

## <a name="next-steps"></a>Passaggi successivi
- Per informazioni su come configurare Microsoft Defender ATP nei dispositivi macOS, vedere [Configurare Microsoft Defender ATP nei dispositivi macOS](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/mac-preferences).
- Per informazioni su come includere ed escludere le assegnazioni delle app nei gruppi di utenti, vedere [Includere ed escludere assegnazioni di app](~/apps/apps-inc-exl-assignments.md).
- [Assegnare app ai gruppi](~/apps/apps-deploy.md)

