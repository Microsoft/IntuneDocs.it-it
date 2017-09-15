---
title: Scaricare i criteri di configurazione delle app iOS Skycure da usare con Intune
titlesuffix: Azure portal
description: Scaricare i criteri di configurazione delle app iOS Skycure da usare con Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1bdc2ecf-32d0-4b6a-80b4-dbcdb9909010
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 296d5545530e8001c0648bafac3101b94f45529d
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2017
---
# <a name="download-skycure-ios-app-configuration-policy"></a>Scaricare i criteri di configurazione delle app iOS Skycure

## <a name="before-you-begin"></a>Prima di iniziare

Per eseguire i passaggi seguenti è necessario accedere alla console di gestione di Skycure.

> [!TIP] 
> Se si usa Microsoft Internet Explorer 11 o Edge, può essere necessario aprire la console di gestione di Skycure usando la modalità anonima.

## <a name="to-download-the-ios-app-configuration-policy"></a>Per scaricare i criteri di configurazione delle app iOS

1.  Passare alla [console di gestione di Skycure](https://aad.skycure.com).

2.  Immettere le **credenziali di amministratore di Skycure** e quindi fare clic su **Continue** (Continua).

    ![Accesso alla console di gestione di Skycure](./media/skycure-ios-app-1.png)

    > [!IMPORTANT] 
    > Il nome utente amministratore di Skycure è un account di posta elettronica che deve corrispondere a un account utente valido in Azure Active Directory, altrimenti il tentativo di accesso non riesce. Skycure usa Azure Active Directory per autenticare il nome utente amministratore tramite Single Sign-On (SSO).

3.  Scegliere **Settings** (Impostazioni) &gt; **Device Management Integrations** (Integrazioni di gestione dei dispositivi) &gt; **EMM Integration Selection** (Selezione integrazione EMM), quindi scegliere **Microsoft Intune** e infine salvare la selezione.

4.  Fare clic sul collegamento **Integration setup files** (File di installazione dell'integrazione) e salvare il file \*.zip generato. Il file con estensione zip contiene il file **skycure\_configuration.plist** che verrà usato per creare i criteri di configurazione delle app iOS nel portale classico di Intune.

![File di installazione dell'integrazione Skycure](./media/skycure-ios-app-2.png)

## <a name="next-steps"></a>Passaggi successivi

[Add and assign Skycure apps, Microsoft Authenticator app and the iOS configuration policy](mtd-apps-ios-app-configuration-policy-add-assign.md) (Aggiungere e assegnare app Skycure e Microsoft Authenticator e criteri di configurazione delle app iOS)
