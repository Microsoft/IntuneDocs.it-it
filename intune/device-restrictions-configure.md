---
title: Configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere un profilo del dispositivo per limitare le funzionalità dei dispositivi Android, macOS, iOS, Windows Phone e Windows 10 in Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e040743975a482c702e0c0168a4fd6315a2dac8
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61505744"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune

Le restrizioni dei dispositivi consentono di controllare una vasta gamma di impostazioni e funzionalità relative a numerose categorie tra cui:
- Sicurezza
- Browser
- Hardware
- Impostazioni di condivisione dei dati

Ad esempio, è possibile creare un profilo di restrizioni dei dispositivi che impedisce agli utenti di dispositivi iOS di accedere alla fotocamera.

Nozioni di base sul profilo di restrizioni dei dispositivi e articoli per le singole piattaforme, con informazioni specifiche relative ai singoli dispositivi.

## <a name="create-the-profile"></a>Creare il profilo

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
6. Le impostazioni configurabili variano in base alla piattaforma scelta. Scegliere la piattaforma per le impostazioni dettagliate:

    - [Impostazioni Android](device-restrictions-android.md)
    - [Impostazioni Android Enterprise](device-restrictions-android-for-work.md)
    - [Impostazioni iOS](device-restrictions-ios.md)
    - [Impostazioni macOS](device-restrictions-macos.md)
    - [Impostazioni Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Impostazioni Windows 10](device-restrictions-windows-10.md)
    - [Impostazioni Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Impostazioni di Windows Holographic for Business](device-restrictions-windows-holographic.md)

7. Al termine, selezionare **OK** > **Crea** per salvare le modifiche.

Il profilo viene creato e visualizzato nell'elenco dei profili.

## <a name="next-steps"></a>Passaggi successivi

Dopo averlo creato, il profilo è pronto per l'assegnazione. [Assegnare il profilo](device-profile-assign.md) e [monitorarne lo stato](device-profile-monitor.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
