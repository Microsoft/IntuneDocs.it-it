---
title: "Configurare le impostazioni relative alle funzionalità dei dispositivi in Microsoft Intune"
titleSuffix: 
description: "Informazioni su come usare Microsoft Intune per configurare le funzionalità nei dispositivi gestiti."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6cd646976deb1599c4cbc9154b6f2a487029dd79
ms.sourcegitcommit: 7e5c4d43cbd757342cb731bf691ef3891b0792b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2018
---
#<a name="configure-device-feature-settings-in-microsoft-intune"></a>Configurare le impostazioni relative alle funzionalità dei dispositivi in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Funzionalità del dispositivo consente di controllare le funzionalità dei dispositivi iOS e macOS come AirPrint, le notifiche e le configurazioni dei dispositivi condivisi.

Usare le informazioni in questo articolo per apprendere le nozioni di base sulla configurazione dei profili delle funzionalità dei dispositivi e quindi leggere altri articoli relativi a ogni piattaforma per informazioni specifiche sui dispositivi.

## <a name="create-a-device-profile-containing-device-feature-settings"></a>Creare un profilo dispositivo contenente le impostazioni relative alle funzionalità del dispositivo

1. Accedere al [portale Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi** > **Intune**. Intune si trova nella sezione **Monitoraggio e gestione**.
3. Nella pagina **Intune** scegliere **Configurazione del dispositivo**.
2. Nella pagina **Configurazione del dispositivo** trovare la sezione **Gestisci** e scegliere **Profili**.
3. Nella pagina dei profili scegliere **Crea profilo**.
4. Nella pagina **Crea profilo** immettere i valori di **Nome** e **Descrizione** per il profilo delle funzionalità del dispositivo.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma per dispositivi a cui applicare le impostazioni. È attualmente possibile scegliere una delle piattaforme seguenti per le funzionalità dei dispositivi:
    - **iOS**
    - **macOS**
6. Nell'elenco a discesa **Tipo di profilo** scegliere **Funzionalità del dispositivo**. 
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli articoli seguenti per informazioni dettagliate sulle impostazioni per ogni piattaforma:
    - [AirPrint settings for iOS and macOS devices](air-print-settings-ios-macos.md) (Impostazioni di AirPrint per i dispositivi iOS e MacOS)
    - [Intune AirPlay settings for iOS devices](airplay-settings-ios.md) (Impostazioni di Intune AirPlay per i dispositivi iOS)
    - [Intune Home screen layout settings for iOS devices](home-screen-settings-ios.md) (Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS)
    - [Intune app notifications settings for IOS devices](app-notification-settings-ios.md) (Impostazioni di notifica delle app di Intune per i dispositivi iOS)
    - [Shared device configuration settings for iOS](shared-device-settings-ios.md) (Impostazioni di configurazione dei dispositivi condivisi per iOS)
    - [Configurare Intune per l'accesso Single Sign-On al dispositivo iOS](sso-ios.md)
    - [Web content filter settings for iOS](web-content-filter-settings-ios.md) (Impostazioni di filtraggio del contenuto Web per iOS)

8. Al termine scegliere **OK**, tornare alla pagina **Crea profilo** e scegliere **Crea**.

Il profilo viene creato e visualizzato nella pagina dell'elenco dei profili.
## <a name="next-steps"></a>Passaggi successivi

Se si vuole assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).



