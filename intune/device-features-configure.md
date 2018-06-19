---
title: Creare profili di dispositivo iOS o macOS in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo di dispositivo iOS o macOS e quindi configurare le impostazioni per AirPrint, AirPlay, layout della schermata iniziale, notifiche delle app, dispositivi condivisi, Single Sign-On e filtro del contenuto Web in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d823a7f8d3478c0ff6c0049a6bbaa76bb4247479
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022034"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Aggiungere impostazioni relative alle funzionalità dei dispositivi iOS e macOS in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Le funzionalità dei dispositivi consentono di controllare una gamma di impostazioni e funzionalità nei dispositivi iOS e macOS, ad esempio:

- Impostazioni di AirPrint e AirPlay
- Layout della schermata iniziale
- Notifiche dalle app
- Configurazione dei dispositivi condivisi
- Configurazione dell'accesso Single Sign-On
- Filtro del contenuto Web

Questo articolo illustra i concetti di base della configurazione di profili di funzionalità dei dispositivi iOS. È quindi possibile procedere con ulteriori articoli per configurare le impostazioni specifiche della piattaforma per i dispositivi.

## <a name="create-a-device-profile"></a>Creare un profilo del dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
4. Immettere le seguenti proprietà:

   - **Nome**: immettere un nome descrittivo per il nuovo profilo.
   - **Descrizione:** immettere una descrizione per il profilo. Facoltativa, ma consigliata.
   - **Piattaforma**: selezionare il tipo di piattaforma:
     - **iOS**
     - **macOS**
   - **Tipo di profilo**: selezionare **Funzionalità del dispositivo**.
   - **Impostazioni**: le impostazioni variano a seconda della piattaforma scelta. Gli articoli seguenti descrivono le impostazioni per ogni tipo di profilo:

     - [AirPrint settings for iOS and macOS devices](air-print-settings-ios-macos.md) (Impostazioni di AirPrint per i dispositivi iOS e MacOS)
     - [Intune AirPlay settings for iOS devices](airplay-settings-ios.md) (Impostazioni di Intune AirPlay per i dispositivi iOS)
     - [Intune Home screen layout settings for iOS devices](home-screen-settings-ios.md) (Impostazioni di layout della schermata iniziale di Intune per i dispositivi iOS)
     - [Intune app notifications settings for IOS devices](app-notification-settings-ios.md) (Impostazioni di notifica delle app di Intune per i dispositivi iOS)
     - [Shared device configuration settings for iOS](shared-device-settings-ios.md) (Impostazioni di configurazione dei dispositivi condivisi per iOS)
     - [Configurare Intune per l'accesso Single Sign-On al dispositivo iOS](sso-ios.md)
     - [Web content filter settings for iOS](web-content-filter-settings-ios.md) (Impostazioni di filtraggio del contenuto Web per iOS)

5. Al termine, selezionare **OK** e quindi scegliere **Crea** per salvare le modifiche.

Il profilo viene creato e quindi visualizzato nell'elenco.

## <a name="next-step"></a>Passaggio successivo

Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).