---
title: Impostazioni personalizzate di Microsoft Intune per dispositivi macOS
titleSuffix: ''
description: Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato macOS in Microsoft Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 66a935b96b802a05831118cd9dc0adbc62bb4bae
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-macos"></a>Impostazioni personalizzate di Microsoft Intune per dispositivi che eseguono macOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare il profilo personalizzato macOS di Microsoft Intune per assegnare le impostazioni create con lo [strumento Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) nei dispositivi macOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione nel profilo personalizzato macOS di Intune e assegnare le impostazioni a utenti e dispositivi nell'organizzazione.

Questa funzionalità consente di assegnare le impostazioni di macOS che non possono essere configurate con gli altri tipi di profilo di Intune.


1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel riquadro **Profilo di configurazione personalizzato** configurare le impostazioni seguenti:

- **Nome del profilo di configurazione personalizzato**: specificare un nome per i criteri con cui questi verranno visualizzati nel dispositivo e nello stato di Intune.
- **File del profilo di configurazione**: cercare il profilo di configurazione creato usando lo strumento Apple Configurator.
Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di macOS nei dispositivi a cui vengono assegnati i criteri personalizzati macOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

Il file importato viene visualizzato nell'area **Contenuti del file** del riquadro.
