---
title: "Configurare le impostazioni relative alle funzionalità dei dispositivi in Intune"
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni su come usare Intune per configurare le funzionalità nei dispositivi gestiti."
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
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: e1bc6388ec1927693bac676a20a18935cdbf894e
ms.lasthandoff: 04/19/2017


---

# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Come configurare le impostazioni relative alle funzionalità dei dispositivi in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Funzionalità del dispositivo consente di controllare le funzionalità dei dispositivi iOS e macOS come AirPrint, le notifiche e le configurazioni dei dispositivi condivisi.

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione dei profili delle funzionalità dei dispositivi e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Altro** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere i valori di **Nome** e **Descrizione** per il profilo delle funzionalità dei dispositivi.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma per dispositivi a cui applicare le impostazioni. È attualmente possibile scegliere una delle piattaforme seguenti per le funzionalità dei dispositivi:
    - **iOS**
    - **macOS**
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Funzionalità del dispositivo**. 
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [AirPrint settings for iOS and macOS devices](air-print-settings-for-ios-and-macos.md) (Impostazioni di AirPrint per i dispositivi iOS e MacOS)
     - [Intune AirPlay settings for iOS devices](airplay-settings-for-ios-devices.md) (Impostazioni di Intune AirPlay per i dispositivi iOS)
    - [Intune Home screen layout settings for iOS devices](home-screen-settings-for-ios.md) (Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS)
    - [Intune app notifications settings for IOS devices](app-notification-settings-for-ios.md) (Impostazioni di notifica delle app di Intune per i dispositivi iOS)
    - [Shared device configuration settings for iOS](shared-device-settings-for-ios.md) (Impostazioni di configurazione dei dispositivi condivisi per iOS)
    - [Web content filter settings for iOS](web-content-filter-settings-for-ios.md) (Impostazioni di filtraggio del contenuto Web per iOS)

8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](how-to-assign-device-profiles.md).




