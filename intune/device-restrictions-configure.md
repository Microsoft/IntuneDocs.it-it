---
title: Configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune
titleSuffix: 
description: "Informazioni su come usare Microsoft Intune per configurare le impostazioni e le funzionalità nei dispositivi gestiti."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/1/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 62c12cde5ca128a26b10e0e4516e0bbf7e0f0bbb
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Come configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le restrizioni dei dispositivi consentono di controllare una vasta gamma di impostazioni e funzionalità relative a numerose categorie tra cui:
- Sicurezza
- Browser
- Hardware
- Impostazioni di condivisione dei dati

Ad esempio, è possibile creare un profilo di restrizioni dei dispositivi che impedisce agli utenti di dispositivi iOS di accedere alla fotocamera.

Nozioni di base sul profilo di restrizioni dei dispositivi e articoli per le singole piattaforme, con informazioni specifiche relative ai singoli dispositivi.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nella pagina **Intune** scegliere **Configurazione del dispositivo**.
2. Nella pagina **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
3. Nella pagina **Profili** scegliere **Crea profilo**.
4. Nella pagina **Crea profilo** immettere **Nome** e **Descrizione** per il profilo di restrizione del dispositivo.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni personalizzate. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e versioni successive**
    - **Windows 10 e versioni successive**
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Limitazioni del dispositivo**. Se si desidera creare un profilo di restrizione per dispositivi Windows 10 Team come Surface Hub, scegliere **Limitazioni del dispositivo (Windows 10 Team)**.
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [Impostazioni Android](device-restrictions-android.md)
    - [Impostazioni iOS](device-restrictions-ios.md)
    - [Impostazioni macOS](device-restrictions-macos.md)
    - [Impostazioni Windows Phone 8.1](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Impostazioni Windows 10](device-restrictions-windows-10.md)
    - [Impostazioni Windows 10 Team](device-restrictions-windows-10-teams.md)
    - [Impostazioni di Windows Holographic for Business](device-restrictions-windows-holographic.md)
    - [Impostazioni di Android for Work](device-restrictions-android-for-work.md)
8. Al termine tornare alla pagina **Crea profilo** e fare clic su **Crea**.

Il profilo viene creato e visualizzato nella pagina dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->