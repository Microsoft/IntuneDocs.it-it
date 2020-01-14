---
title: Configurare la registrazione per i dispositivi macOS
titleSuffix: Microsoft Intune
description: Informazioni su come impostare la registrazione per i dispositivi macOS in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 46429114-2e26-4ba7-aa21-b2b1a5643e01
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cddb9b74d9132ace07c17a3156e61148b720d66
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207180"
---
# <a name="set-up-enrollment-for-macos-devices-in-intune"></a>Configurare la registrazione per i dispositivi macOS in Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune consente di gestire i dispositivi macOS per consentire agli utenti di accedere alle app e alla posta elettronica aziendali.

Gli amministratori di Intune possono configurare la registrazione per i dispositivi macOS di proprietà dell'azienda e per i dispositivi macOS di proprietà personale ("bring your own device" o BYOD). 

## <a name="prerequisites"></a>Prerequisiti

Completare i prerequisiti seguenti prima di impostare la registrazione di dispositivi macOS:

- [Verificare che il dispositivo sia idoneo per la registrazione dei dispositivi Apple](https://support.apple.com/en-us/HT204142#eligibility).
- [Configurare i domini](../fundamentals/custom-domain-name-configure.md)
- [Impostare l'autorità MDM](../fundamentals/mdm-authority-set.md)
- [Creare i gruppi](../fundamentals/groups-add.md)
- [Configurare il Portale aziendale](../apps/company-portal-app.md)
- Assegnare licenze utente nell'[interfaccia di amministrazione di Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Ottenere un certificato push MDM Apple](../enrollment/apple-mdm-push-certificate-get.md)

## <a name="user-owned-macos-devices-byod"></a>Dispositivi macOS di proprietà dell'utente (BYOD)

È possibile consentire agli utenti di registrare i dispositivi personali nella gestione di Intune. Questa operazione è nota come "Bring Your Own Device" o BYOD. Dopo aver completato i prerequisiti e aver assegnato le licenze agli utenti, gli utenti possono registrare i dispositivi nei modi seguenti:
- accedendo al [sito Web del portale aziendale](https://portal.manage.microsoft.com) oppure
- Scaricando l'app Portale aziendale per Mac in [aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac).

È anche possibile inviare agli utenti un collegamento alla procedura di registrazione online: [Registrare il dispositivo macOS in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos).

Per informazioni su altre attività dell'utente finale, vedere gli articoli seguenti:

- [Informazioni sull'uso di Microsoft Intune per gli utenti finali](../fundamentals/end-user-educate.md)
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

Per Parallels Desktop, è necessario impostare il tipo di hardware e il numero di serie delle macchine virtuali in modo che Intune possa riconoscerle. Seguire le istruzioni di Parallels per impostare il tipo di hardware e il [numero di serie](http://kb.parallels.com/123455) per configurare le impostazioni necessarie per i test. È consigliabile che il tipo di hardware del dispositivo che esegue le macchine virtuali corrisponda al tipo di hardware delle macchine virtuali da creare. Il tipo di hardware è indicato in **menu Apple** > **Informazioni su questo Mac** > **Resoconto di sistema** > **Identificatore modello**. 

Per VMware Fusion, è necessario [modificare il file con estensione vmx](https://kb.vmware.com/s/article/1014782) per impostare il modello hardware e il numero di serie della macchina virtuale. È consigliabile che il tipo di hardware del dispositivo che esegue le macchine virtuali corrisponda al tipo di hardware delle macchine virtuali da creare. Il tipo di hardware è indicato in **menu Apple** > **Informazioni su questo Mac** > **Resoconto di sistema** > **Identificatore modello**. 

## <a name="user-approved-enrollment"></a>Registrazione approvata dall'utente
La registrazione MDM approvata dall'utente è un tipo di registrazione macOS che è possibile usare per gestire alcune impostazioni basate sulla sicurezza. Per altre informazioni, vedere la [documentazione del supporto Apple](https://support.apple.com/HT208019).  
 
Durante il processo di registrazione BYOD, all'utente verrà richiesto di approvare manualmente il profilo di gestione Apple. Le istruzioni sono disponibili nell'app Portale aziendale per macOS. Anche se non è necessaria l'approvazione del profilo di gestione per completare la registrazione, Intune consiglia registrazioni approvate dall'utente. Se l'utente non approva il profilo durante l'iscrizione, può passare a **Preferenze di sistema** > **Profili**, scegliere il profilo di gestione e selezionare **Approva**.    

### <a name="find-out-if-a-device-is-user-approved"></a>Determinare se un dispositivo è approvato dall'utente
1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo > **Hardware**.
3. Controllare il campo **Registrazione approvata dall'utente**.


## <a name="next-steps"></a>Passaggi successivi

Dopo aver registrato i dispositivi macOS, è possibile [creare impostazioni personalizzate per i dispositivi macOS](../configuration/custom-settings-macos.md).
