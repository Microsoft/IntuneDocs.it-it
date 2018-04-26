---
title: Impostazioni personalizzate di Microsoft Intune per dispositivi iOS
titleSuffix: ''
description: Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato iOS in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0ae4e757264465043ee6992033710c5a81d7157
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>Impostazioni personalizzate di Microsoft Intune per dispositivi che eseguono iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Usare il profilo di configurazione personalizzato iOS di Microsoft Intune per assegnare le impostazioni create con lo [strumento Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) nei dispositivi iOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione nel profilo personalizzato iOS di Intune e assegnare le impostazioni a utenti e dispositivi nell'organizzazione.

Questa funzionalità consente di assegnare le impostazioni iOS che non possono essere configurate con gli altri tipi di profilo di Intune.


1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel riquadro **Profilo di configurazione personalizzato** configurare le impostazioni seguenti:

- **Nome del profilo di configurazione personalizzato**: specificare un nome per i criteri con cui questi verranno visualizzati nel dispositivo e nello stato di Intune.
- **File del profilo di configurazione**: cercare il profilo di configurazione creato usando lo strumento Apple Configurator.
Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di iOS nei dispositivi a cui vengono assegnati i criteri personalizzati iOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

Il file importato viene visualizzato nell'area **Contenuti del file** del riquadro.
