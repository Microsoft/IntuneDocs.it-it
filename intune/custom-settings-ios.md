---
title: Impostazioni personalizzate di Intune per dispositivi iOS
titleSuffix: Azure portal
description: "Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato iOS.\""
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6da8caa8-65c2-4f47-842f-9570dcb1ac22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 761b19de8442e88717a5dcd52f7f0375bace91da
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="microsoft-intune-custom-settings-for-ios-devices"></a>Impostazioni personalizzate di Microsoft Intune per dispositivi iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare il profilo di configurazione personalizzato iOS di Microsoft Intune per assegnare le impostazioni create con lo [strumento Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12) nei dispositivi iOS. Questo strumento consente di creare molte impostazioni che controllano il funzionamento di questi dispositivi e di esportarle in un profilo di configurazione. È quindi possibile importare il profilo di configurazione nel profilo personalizzato iOS di Intune e assegnare le impostazioni a utenti e dispositivi nell'organizzazione.

Questa funzionalità consente di assegnare le impostazioni iOS che non possono essere configurate con gli altri tipi di profilo di Intune.


1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** specificare quanto segue:

- **Nome del profilo di configurazione personalizzato**: specificare un nome per il criterio con cui verrà visualizzato nel dispositivo e lo stato di Intune.
- **File del profilo di configurazione**: cercare il profilo di configurazione creato usando lo strumento Apple Configurator.
Assicurarsi che le impostazioni esportate dallo strumento Apple Configurator siano compatibili con la versione di iOS nei dispositivi a cui vengono assegnati i criteri personalizzati iOS. Per informazioni sulla risoluzione delle impostazioni incompatibili, cercare **Configuration Profile Reference** (Riferimento per il profilo di configurazione) e **Mobile Device Management Protocol Reference** (Riferimento per il protocollo di gestione dei dispositivi mobili) nel sito Web [Apple Developer](https://developer.apple.com/).

Il file importato viene visualizzato nell'area **Contenuti del file** del pannello.
