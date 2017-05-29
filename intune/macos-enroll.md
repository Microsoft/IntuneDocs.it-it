---
title: Registrare i dispositivi macOS in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come registrare i dispositivi macOS nell&quot;anteprima di Intune in Azure.'
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c10a28a51e9f6bed99a657cd940b00f3114e4588
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Registrare i dispositivi macOS nell'anteprima di Intune in Azure

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune consente di gestire i dispositivi macOS. Per abilitare la gestione dei dispositivi, gli utenti devono registrare i dispositivi nel [sito Web del portale aziendale](http://portal.manage.microsoft.com) e seguire le istruzioni. Dopo aver registrato per la gestione i dispositivi macOS, è possibile [creare impostazioni personalizzate per i dispositivi macOS](custom settings-macos.md). Altre funzionalità saranno disponibili a breve.

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di impostare la registrazione di dispositivi macOS:

- [Configurare i domini](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Impostare l'autorità MDM](mdm-authority-set.md)
- [Creare i gruppi](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurare il Portale aziendale](company-portal-app.md)
- Assegnare licenze utente nel [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="set-up-macos-enrollment"></a>Configurare la registrazione di macOS

Per impostazione predefinita, Intune consente già la registrazione dei dispositivi macOS.

Per bloccare la registrazione dei i dispositivi macOS, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md#set-device-type-restrictions).

Per impostare il numero massimo di dispositivi che un utente può registrare, vedere [Impostare le restrizioni sul limite dei dispositivi](enrollment-restrictions-set.md#set-device-limit-restrictions).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali

È necessario richiedere agli utenti di visitare il [sito Web del portale aziendale](http://portal.manage.microsoft.com) e di seguire le istruzioni per registrare i propri dispositivi. È anche possibile inviare agli utenti un collegamento alla procedura di registrazione online: [Registrare il dispositivo macOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](https://docs.microsoft.com/intune-classic/deploy-use/how-to-educate-your-end-users-about-microsoft-intune)
- [Uso del dispositivo iOS o macOS con Intune](https://docs.microsoft.com/intune-user-help/using-your-ios-or-mac-os-x-device-with-intune)

