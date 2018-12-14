---
title: Configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere un profilo del dispositivo per limitare le funzionalità dei dispositivi Android, macOS, iOS, Windows Phone e Windows 10 in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 11b241a14ed70a2e999fa505449cd12cdd1e025e
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728787"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune

Le restrizioni dei dispositivi consentono di controllare una vasta gamma di impostazioni e funzionalità relative a numerose categorie tra cui:
- Sicurezza
- Browser
- Hardware
- Impostazioni di condivisione dei dati

Ad esempio, è possibile creare un profilo di restrizioni dei dispositivi che impedisce agli utenti di dispositivi iOS di accedere alla fotocamera.

Nozioni di base sul profilo di restrizioni dei dispositivi e articoli per le singole piattaforme, con informazioni specifiche relative ai singoli dispositivi.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo

1. Nel [portale di Azure](https://portal.azure.com) selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Intune**.
2. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
3. Immettere un **Nome** e una **Descrizione** per il profilo di restrizione del dispositivo.
4. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni personalizzate. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:

    - **Android**
    - **Android Enterprise**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**

5. Dall'elenco a discesa **Tipo di profilo** scegliere **Limitazioni del dispositivo**. Per creare un profilo di restrizione per dispositivi Windows 10 Team come Surface Hub, scegliere **Limitazioni del dispositivo (Windows 10 Team)**.
6. Le impostazioni configurabili variano in base alla piattaforma scelta. Scegliere le impostazioni dettagliate per la piattaforma:

    - [Impostazioni Android](device-restrictions-android.md)
    - [Impostazioni Android Enterprise](device-restrictions-android-for-work.md)
    - [Impostazioni iOS](device-restrictions-ios.md)
    - [Impostazioni macOS](device-restrictions-macos.md)
    - [Impostazioni Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Impostazioni Windows 10](device-restrictions-windows-10.md)
    - [Impostazioni Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Impostazioni di Windows Holographic for Business](device-restrictions-windows-holographic.md)

7. Al termine, tornare alla pagina **Crea profilo** e selezionare **Crea**.

Il profilo viene creato e visualizzato nella pagina dell'elenco dei profili. 

## <a name="next-step"></a>Passaggio successivo

Dopo averlo creato, il profilo è pronto per l'assegnazione. Per la procedura, vedere[Assegnare i profili di dispositivo](device-profile-assign.md). 

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
