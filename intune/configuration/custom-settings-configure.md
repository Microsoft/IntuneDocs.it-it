---
title: Usare dispositivi personalizzati in Microsoft Intune - Azure | Microsoft Docs
description: Aggiungere o creare un profilo per usare le impostazioni personalizzate per i dispositivi Windows Phone, Windows 8.1, Windows 10 e versioni successive, Android, Android Enterprise, macOS e iOS tramite Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87c35fdaddec591b57b9b7c28f94560ff52a93b0
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506946"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Creare un profilo con impostazioni personalizzate in Intune

## <a name="what-are-custom-profiles"></a>Informazioni sui profili personalizzati

Microsoft Intune include molte impostazioni predefinite per controllare diverse funzionalità in un dispositivo. È anche possibile creare profili personalizzati. I profili personalizzati sono particolarmente utili quando si vuole usare impostazioni del dispositivo e funzionalità non incluse in Intune. Questi profili includono funzionalità e impostazioni che è possibile controllare nei dispositivi dell'organizzazione. Ad esempio, è possibile creare un profilo personalizzato che imposta la stessa funzionalità per tutti i dispositivi iOS.

Per altre informazioni sui profili di configurazione, vedere [Informazioni sui profili di dispositivo in Microsoft Intune](device-profiles.md). 

Questo articolo include i collegamenti per creare profili personalizzati per Android, Android Enterprise, iOS, macOS e Windows.

## <a name="available-platforms"></a>Piattaforme disponibili

Le impostazioni personalizzate sono configurate in modo diverso per ogni piattaforma. Ad esempio, per controllare le funzionalità nei dispositivi Android e Windows, è possibile specificare valori Open Mobile Alliance Uniform Resource Identifier (URI OMA). Per i dispositivi Apple è possibile importare un file creato con [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) o [Apple Profile Manager](https://support.apple.com/profile-manager).

I profili personalizzati vengono creati allo stesso modo dei profili predefiniti e sono disponibili nelle piattaforme seguenti:

- [Android](../custom-settings-android.md)
- [Android Enterprise](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>Passaggi successivi

Scegliere la piattaforma e iniziare a usare:

- [Android](../custom-settings-android.md)
- [Android Enterprise](../custom-settings-android-for-work.md)
- [iOS/iPadOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
