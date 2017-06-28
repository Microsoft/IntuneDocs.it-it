---
title: Scaricare i criteri di configurazione delle app iOS Skycure
description: Scaricare i criteri di configurazione da usare con l&quot;app iOS Skycure distribuita agli utenti finali.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d211b876-4d3a-473c-999f-843c0a16cd22
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 3159985bfbaec40899dd58766e214daa672ee6d4
ms.contentlocale: it-it
ms.lasthandoff: 06/08/2017


---

# <a name="download-skycure-ios-app-configuration-policy"></a>Scaricare i criteri di configurazione delle app iOS Skycure

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

##<a name="before-you-begin"></a>Prima di iniziare

Per eseguire i passaggi seguenti è necessario accedere alla console di gestione di Skycure.

> [!TIP] 
> Se si usa Microsoft Internet Explorer 11 o Microsoft Edge, può essere necessario aprire la console di gestione di Skycure usando la modalità anonima.

## <a name="to-download-the-ios-app-configuration-policy"></a>Per scaricare i criteri di configurazione delle app iOS

1.  Passare alla [console di gestione di Skycure](https://aad.skycure.com).

2.  Immettere le **credenziali di amministratore di Skycure** e quindi fare clic su **Continue** (Continua).

    ![Accesso alla console di gestione di Skycure](../media/mtp/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Il nome utente amministratore di Skycure è un account di posta elettronica che deve corrispondere a un account utente valido in Azure Active Directory, altrimenti il tentativo di accesso non riesce. Skycure usa Azure Active Directory per autenticare il nome utente amministratore tramite Single Sign-On (SSO).

3.  Scegliere **Settings** (Impostazioni) &gt; **Device Management Integrations** (Integrazioni di gestione dei dispositivi) &gt; **EMM Integration Selection** (Selezione integrazione EMM), quindi scegliere **Microsoft Intune** e infine salvare la selezione.

2.  Fare clic sul collegamento **Integration setup files** (File di installazione dell'integrazione) e salvare il file \*.zip generato. Il file con estensione zip contiene il file **skycure\_configuration.plist** che verrà usato per creare i criteri di configurazione delle app iOS nella console classica di Intune.

![File di installazione dell'integrazione Skycure](../media/mtp/skycure-ios-app-2.png)

## <a name="next-steps"></a>Passaggi successivi

[Aggiungere app Skycure, l'app Microsoft Authenticator e i criteri di configurazione iOS](/intune-classic/deploy-use/add-skycure-apps-microsoft-authenticator-and-ios-app-configuration-policy)

