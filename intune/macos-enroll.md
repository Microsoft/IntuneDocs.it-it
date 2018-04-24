---
title: Configurare la registrazione per i dispositivi macOS
titlesuffix: Microsoft Intune
description: Informazioni su come impostare la registrazione per i dispositivi macOS in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1e522708879818f644780904c42fe9e6fb19a402
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configurare la registrazione per i dispositivi macOS in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune consente di gestire i dispositivi macOS. Per abilitare la gestione dei dispositivi, gli utenti devono registrare i dispositivi nel [sito Web del portale aziendale](http://portal.manage.microsoft.com) e seguire le istruzioni. Dopo aver registrato per la gestione i dispositivi macOS, è possibile [creare impostazioni personalizzate per i dispositivi macOS](custom-settings-macos.md). Altre funzionalità saranno disponibili a breve.

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di impostare la registrazione di dispositivi macOS:

- [Configurare i domini](custom-domain-name-configure.md)
- [Impostare l'autorità MDM](mdm-authority-set.md)
- [Creare i gruppi](https://docs.microsoft.com/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-5)
- [Configurare il Portale aziendale](company-portal-app.md)
- Assegnare licenze utente nel [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="user-owned-ios-devices-byod"></a>Dispositivi iOS di proprietà dell'utente (BYOD)

È possibile consentire agli utenti di registrare i dispositivi personali per la gestione di Intune, una funzionalità nota come BYOD (Bring Your Own Device, Usa dispositivo personale). Dopo aver completato i prerequisiti e assegnato le licenze, gli utenti possono scaricare l'app Portale aziendale macOS dall'App Store e seguire le istruzioni di registrazione nell'app.

## <a name="company-owned-ios-devices"></a>Dispositivi macOS di proprietà dell'azienda
Per le organizzazioni che acquistano dispositivi per i propri utenti, Intune supporta la registrazione dei dispositivi macOS di proprietà dell'azienda con un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="set-up-macos-enrollment"></a>Configurare la registrazione di macOS

Per impostazione predefinita, Intune consente già la registrazione dei dispositivi macOS.

Per bloccare la registrazione dei i dispositivi macOS, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).

## <a name="tell-your-users-how-to-enroll-their-devices-to-access-company-resources"></a>Indicare agli utenti come registrare i propri dispositivi per accedere alle risorse aziendali

Richiedere agli utenti di visitare il [sito Web del portale aziendale](https://portal.manage.microsoft.com) e di seguire le istruzioni per registrare i propri dispositivi. È anche possibile inviare agli utenti un collegamento alla procedura di registrazione online: [Registrare il dispositivo macOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](end-user-educate.md)
- [Uso del dispositivo macOS con Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="enroll-virtual-macos-machines-for-testing"></a>Registrare le macchine virtuali macOS per i test

> [!NOTE]
> Le macchine virtuali macOS sono supportate solo per i test. Non usare le macchine virtuali macOS come dispositivi di produzione per gli utenti finali. 

È possibile registrare le macchine virtuali macOS per i test tramite Parallels Desktop o VMware Fusion. 

Per Parallels Desktop, è necessario impostare il tipo di hardware e il numero di serie delle macchine virtuali in modo che Intune possa riconoscerle. Seguire le istruzioni di Parallels per l'[impostazione del tipo di hardware](http://kb.parallels.com/123594) e del [numero di serie](http://kb.parallels.com/123455) per configurare le impostazioni necessarie per i test. È consigliabile che il tipo di hardware del dispositivo che esegue le macchine virtuali corrisponda al tipo di hardware delle macchine virtuali da creare. Il tipo di hardware è indicato in **menu Apple** > **Informazioni su questo Mac** > **Resoconto di sistema** > **Identificatore modello**. 

Per VMware Fusion, è necessario [modificare il file con estensione vmx](https://kb.vmware.com/s/article/1014782) per impostare il modello hardware e il numero di serie della macchina virtuale. È consigliabile che il tipo di hardware del dispositivo che esegue le macchine virtuali corrisponda al tipo di hardware delle macchine virtuali da creare. Il tipo di hardware è indicato in **menu Apple** > **Informazioni su questo Mac** > **Resoconto di sistema** > **Identificatore modello**. 
