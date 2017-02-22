---
title: Registrare i dispositivi macOS in Intune | Anteprima di Intune in Azure | Documentazione Microsoft
description: 'Anteprima di Intune in Azure: informazioni su come registrare i dispositivi macOS nell&quot;anteprima di Intune in Azure.'
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 1/3/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba2affcdbcdfcd690d671c7b20f9d1e14a74f764
ms.openlocfilehash: 171175689adca027181f3da4d05222117de97e13


---

# <a name="enroll-macos-devices-in-intune-azure-preview"></a>Registrare i dispositivi macOS nell'anteprima di Intune in Azure

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

In qualità di amministratore di Intune, è possibile gestire i dispositivi macOS. Per impostazione predefinita, il portale di Azure consente agli utenti di registrare i propri dispositivi macOS. È sufficiente indicare agli utenti di visitare il [sito Web del portale aziendale](http://portal.manage.microsoft.com) e registrare il proprio dispositivo macOS. 

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di impostare la registrazione di dispositivi macOS:

- [Configurare i domini](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-2)
- [Impostare l'autorità MDM](set-mdm-authority.md)
- [Creare i gruppi](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurare il portale aziendale](/intune-azure/manage-apps/company-portal-app.md)
- Assegnare licenze utente nel [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](get-an-apple-mdm-push-certificate.md)

## <a name="set-up-macos-enrollment"></a>Configurare la registrazione di macOS

Per impostazione predefinita, Intune è già configurato per consentire la registrazione dei dispositivi macOS. 

Per visualizzare l'impostazione che consente o blocca la registrazione di dispositivi macOS, passare al pannello Intune nel portale di Azure e scegliere **Registrazione** > **Restrizioni registrazione**. 

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali

Per istruzioni sulla registrazione da parte dell'utente finale, vedere [Registrare il dispositivo macOS in Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-macos). Il processo di registrazione indica agli utenti cosa possono aspettarsi e i dati visibili o meno agli amministratori IT nei propri dispositivi.

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)
- [Uso del dispositivo iOS o macOS con Intune](https://docs.microsoft.com/intune/enduser/using-your-ios-or-mac-os-x-device-with-intune)


<!--HONumber=Feb17_HO1-->


