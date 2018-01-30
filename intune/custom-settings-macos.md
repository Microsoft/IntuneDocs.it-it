---
title: Impostazioni personalizzate di Intune per dispositivi macOS
titleSuffix: Azure portal
description: "Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato macOS.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 88224849de0727418197fcfdb96cac3b4c2ca0e7
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Impostazioni personalizzate per i dispositivi macOS in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare il profilo personalizzato macOS di Microsoft Intune per assegnare le impostazioni create con lo [strumento Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) nei dispositivi macOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione nel profilo personalizzato macOS di Intune e assegnare le impostazioni a utenti e dispositivi nell'organizzazione.

Questa funzionalità consente di assegnare le impostazioni di macOS che non possono essere configurate con gli altri tipi di profilo di Intune.


1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** specificare quanto segue:

- **Nome del profilo di configurazione personalizzato**: specificare un nome per il criterio con cui verrà visualizzato nel dispositivo e lo stato di Intune.
- **File del profilo di configurazione**: cercare il profilo di configurazione creato usando lo strumento Apple Configurator.
Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di macOS nei dispositivi a cui vengono assegnati i criteri personalizzati macOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

Il file importato viene visualizzato nell'area **Contenuti del file** del pannello.
