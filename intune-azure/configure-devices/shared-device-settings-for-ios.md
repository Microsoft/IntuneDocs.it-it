---
title: Impostazioni di configurazione dei dispositivi di Intune condivisi per iOS
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni sulle impostazioni di Intune che consentono di visualizzare informazioni sulla schermata di blocco del dispositivo iOS.'
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 4/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 2bc107054f438d5ed72de87dec85900f871c0acc
ms.lasthandoff: 04/19/2017


---

# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>Impostazioni di configurazione del dispositivo condiviso per la visualizzazione di messaggi nella schermata di blocco del dispositivo iOS

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Le impostazioni di configurazione del dispositivo condiviso consentono di specificare testo facoltativo visualizzabile nella finestra di accesso e nella schermata di blocco, ad esempio un messaggio di tipo "In caso di ritrovamento, restituire a" e informazioni sui tag asset. 

>[!IMPORTANT]
> Questa funzionalità è supportata sui dispositivi con supervisione che eseguono iOS 9.3 e versioni successive.

1. Nel pannello **Funzionalità de dispositivo** scegliere **Configurazione del dispositivo condiviso (solo con supervisione)**.
2. Nel pannello **Configurazione del dispositivo condiviso (solo con supervisione)** configurare le seguenti opzioni:
    - **Informazioni sui tag asset**: immettere informazioni sul tag asset del dispositivo. Ad esempio: **Proprietà di Contoso Corp**. Le informazioni immesse vengono applicate a tutti i dispositivi ai quali viene assegnato questo profilo.
    - **Nota a piè di pagina della schermata di blocco**: immettere una nota che può contribuire alla restituzione del dispositivo in caso di furto o smarrimento. Ad esempio: **In caso di ritrovamento, chiamare il "numero"**.
3. Al termine, fare clic su **OK** fino a tornare al pannello **Crea profilo**, quindi scegliere **Crea**. 

