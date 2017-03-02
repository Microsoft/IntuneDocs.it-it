---
title: Impostazioni personalizzate di Intune per dispositivi macOS | Anteprima di Intune in Azure | Documentazione Microsoft
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni che è possibile usare in un profilo personalizzato macOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 68100ea5-7d9b-4c0b-8df7-b9a24b2442c8
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: 13648aa35057201ac7420e2f1d334aee206605fe
ms.lasthandoff: 02/16/2017


---

# <a name="custom-settings-for-macos-devices-in-microsoft-intune"></a>Impostazioni personalizzate per i dispositivi macOS in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare il profilo personalizzato macOS di Microsoft Intune per distribuire le impostazioni create con lo [strumento Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) nei dispositivi macOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione nel profilo personalizzato macOS di Intune e assegnare le impostazioni a utenti e dispositivi nell'organizzazione.

Questa funzionalità consente di distribuire le impostazioni di macOS che non possono essere configurate con gli altri tipi di profilo di Intune.


1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](how-to-configure-custom-settings.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** specificare quanto segue:

- **Nome del profilo di configurazione personalizzato**: specificare un nome per il criterio con cui verrà visualizzato nel dispositivo e lo stato di Intune.
- **File del profilo di configurazione**: cercare il profilo di configurazione creato usando lo strumento Apple Configurator.
Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di macOS sui dispositivi su cui vengono distribuiti i criteri personalizzati macOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

Il file importato viene visualizzato nell'area **Contenuti del file** del pannello.

