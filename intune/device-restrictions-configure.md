---
title: Configurare le impostazioni relative alle restrizioni dei dispositivi di Intune
titleSuffix: Intune on Azure
description: "Informazioni su come usare Intune per configurare le impostazioni e le funzionalità nei dispositivi gestiti.\""
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8652b2b6db340f3b0cddcf538fa418c8774b1d6c
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="how-to-configure-device-restriction-settings-in-microsoft-intune"></a>Come configurare le impostazioni relative alle restrizioni dei dispositivi in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Le restrizioni dei dispositivi consentono di controllare una vasta gamma di impostazioni e funzionalità relative a numerose categorie tra cui sicurezza, browser, hardware e condivisione dei dati. Ad esempio, è possibile creare un profilo di restrizione dei dispositivi che impedisce agli utenti di dispositivi iOS di accedere alla fotocamera.

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione di un profilo di restrizione del dispositivo e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configura i dispositivi**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere un **nome** e una **descrizione** per il profilo di restrizione del dispositivo.
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
    - [Impostazioni di Android for Work](device-restrictions-android-for-work.md)
8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).

## <a name="example-of-device-restriction-settings"></a>Esempio di impostazioni relative alle restrizioni dei dispositivi

In questo esempio generale verrà creato un criterio di restrizione che impedisce l'uso delle app della fotocamera incorporata nei dispositivi Android.

![Come disabilitare la fotocamera su dispositivi Android](./media/disable-android-camera.png)

