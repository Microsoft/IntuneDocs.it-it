---
title: "Configurare le impostazioni relative alle funzionalità dei dispositivi in Intune"
titleSuffix: Azure portal
description: "Informazioni su come usare Intune per configurare le funzionalità nei dispositivi gestiti.\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 12/7/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 42f9b104-c1f6-4dfc-8aa4-1d33e1eaf61f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ea280ac6858485aa4e3d64d11835f002c5bb35ca
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="how-to-configure-device-feature-settings-in-microsoft-intune"></a>Come configurare le impostazioni relative alle funzionalità dei dispositivi in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Funzionalità del dispositivo consente di controllare le funzionalità dei dispositivi iOS e macOS come AirPrint, le notifiche e le configurazioni dei dispositivi condivisi.

Usare le informazioni in questo argomento per apprendere le nozioni di base sulla configurazione dei profili delle funzionalità dei dispositivi e quindi leggere altri argomenti relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle restrizioni del dispositivo

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Configurazione del dispositivo**.
2. Nel pannello **Configurazione del dispositivo** scegliere **Gestisci** > **Profili**.
3. Nel pannello dei profili scegliere **Crea profilo**.
4. Nel pannello **Crea profilo** immettere i valori di **Nome** e **Descrizione** per il profilo delle funzionalità dei dispositivi.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma per dispositivi a cui applicare le impostazioni. È attualmente possibile scegliere una delle piattaforme seguenti per le funzionalità dei dispositivi:
    - **iOS**
    - **macOS**
6. Nell'elenco a discesa **Tipo di profilo** scegliere **Funzionalità del dispositivo**. 
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
    - [AirPrint settings for iOS and macOS devices](air-print-settings-ios-macos.md) (Impostazioni di AirPrint per i dispositivi iOS e MacOS)
    - [Intune AirPlay settings for iOS devices](airplay-settings-ios.md) (Impostazioni di Intune AirPlay per i dispositivi iOS)
    - [Intune Home screen layout settings for iOS devices](home-screen-settings-ios.md) (Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS)
    - [Intune app notifications settings for IOS devices](app-notification-settings-ios.md) (Impostazioni di notifica delle app di Intune per i dispositivi iOS)
    - [Shared device configuration settings for iOS](shared-device-settings-ios.md) (Impostazioni di configurazione dei dispositivi condivisi per iOS)
    - [Configurare Intune per l'accesso Single Sign-On al dispositivo iOS](sso-ios.md)
    - [Web content filter settings for iOS](web-content-filter-settings-ios.md) (Impostazioni di filtraggio del contenuto Web per iOS)

8. Al termine tornare al pannello **Crea profilo** e fare clic su **Crea**.

Il profilo viene creato e visualizzato nel pannello dell'elenco dei profili.
Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).



