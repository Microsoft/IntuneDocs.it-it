---
title: Configurare la registrazione per i dispositivi macOS
titlesuffix: Microsoft Intune
description: Informazioni su come impostare la registrazione per i dispositivi macOS in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 7a54a72afb6052ed11566c2d2ada596ebde2159b
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112409"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configurare la registrazione per i dispositivi macOS in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune consente di gestire i dispositivi macOS per consentire agli utenti di accedere alle app e alla posta elettronica aziendali.

Gli amministratori di Intune possono configurare la registrazione per i dispositivi macOS di proprietà dell'azienda e per i dispositivi macOS di proprietà personale ("bring your own device" o BYOD). 

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di impostare la registrazione di dispositivi macOS:

- [Configurare i domini](custom-domain-name-configure.md)
- [Impostare l'autorità MDM](mdm-authority-set.md)
- [Creare i gruppi](groups-add.md)
- [Configurare il Portale aziendale](company-portal-app.md)
- Assegnare licenze utente nel [portale di Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Dispositivi macOS di proprietà dell'utente (BYOD)

È possibile consentire agli utenti di registrare i dispositivi personali per la gestione di Intune, una funzionalità nota come BYOD (Bring Your Own Device, Usa dispositivo personale). Dopo aver completato i prerequisiti e assegnato le licenze agli utenti, gli utenti possono registrare i dispositivi nei modi seguenti:
- accedendo al [sito Web del portale aziendale](https://portal.manage.microsoft.com) oppure
- scaricando l'app Portale aziendale.
È anche possibile inviare agli utenti un collegamento alla procedura di registrazione online: [Registrare il dispositivo macOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](end-user-educate.md)
- [Uso del dispositivo macOS con Intune](/intune-user-help/using-your-macos-device-with-intune)

## <a name="company-owned-macos-devices"></a>Dispositivi macOS di proprietà dell'azienda
Per le organizzazioni che acquistano dispositivi per i propri utenti, Intune supporta i seguenti metodi di registrazione dei dispositivi macOS di proprietà dell'azienda:
- [Device Enrollment Program (DEP) di Apple](device-enrollment-program-enroll-macos.md): le organizzazioni possono ora acquistare i dispositivi macOS tramite Device Enrollment Program (DEP) di Apple. DEP consente di distribuire un profilo di registrazione in modalità wireless per portare i dispositivi nella gestione.
- [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md): è possibile usare un account del manager di registrazione dispositivi per registrare fino a 1.000 dispositivi.

## <a name="block-macos-enrollment"></a>Bloccare la registrazione di macOS
Per impostazione predefinita, Intune consente la registrazione dei dispositivi macOS. Per bloccare la registrazione dei i dispositivi macOS, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).

## <a name="enroll-virtual-macos-machines-for-testing"></a>Registrare le macchine virtuali macOS per i test

> [!NOTE]
> Le macchine virtuali macOS sono supportate solo per i test. Non usare le macchine virtuali macOS come dispositivi di produzione per gli utenti finali. 

È possibile registrare le macchine virtuali macOS per i test tramite Parallels Desktop o VMware Fusion. 

Per Parallels Desktop, è necessario impostare il tipo di hardware e il numero di serie delle macchine virtuali in modo che Intune possa riconoscerle. Seguire le istruzioni di Parallels per l'[impostazione del tipo di hardware](http://kb.parallels.com/123594) e del [numero di serie](http://kb.parallels.com/123455) per configurare le impostazioni necessarie per i test. È consigliabile che il tipo di hardware del dispositivo che esegue le macchine virtuali corrisponda al tipo di hardware delle macchine virtuali da creare. Il tipo di hardware è indicato in **menu Apple** > **Informazioni su questo Mac** > **Resoconto di sistema** > **Identificatore modello**. 

Per VMware Fusion, è necessario [modificare il file con estensione vmx](https://kb.vmware.com/s/article/1014782) per impostare il modello hardware e il numero di serie della macchina virtuale. È consigliabile che il tipo di hardware del dispositivo che esegue le macchine virtuali corrisponda al tipo di hardware delle macchine virtuali da creare. Il tipo di hardware è indicato in **menu Apple** > **Informazioni su questo Mac** > **Resoconto di sistema** > **Identificatore modello**. 

## <a name="user-approved-enrollment"></a>Registrazione approvata dall'utente

La registrazione MDM approvata dall'utente è un tipo di registrazione macOS che è possibile usare per gestire alcune impostazioni basate sulla sicurezza. Per altre informazioni, vedere la [documentazione del supporto Apple](https://support.apple.com/HT208019).

Per essere approvata dall'utente, dopo la registrazione tramite il portale aziendale di macOS, l'utente finale deve fornire manualmente l'approvazione usando Preferenze di Sistema. Le istruzioni per eseguire questa operazione sono disponibili nel portale aziendale di macOS per gli utenti di macOS 10.13.2 e versioni successive.

Per sapere se un dispositivo è approvato dall'utente, andare al portale di Intune e quindi scegliere **Dispositivi** > **Tutti i dispositivi**> scegliere il dispositivo > **Hardware**. Controllare il campo **User Approved** (Approvato dall'utente).

## <a name="next-steps"></a>Passaggi successivi

Dopo aver registrato i dispositivi macOS, è possibile [creare impostazioni personalizzate per i dispositivi macOS](custom-settings-macos.md).
