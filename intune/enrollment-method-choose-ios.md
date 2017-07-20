---
title: Scegliere come registrare i dispositivi iOS in Intune
titleSuffix: Intune on Azure
description: Informazioni su come impostare la registrazione dei dispositivi iOS in Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 092f582cf30210858bd8cdd3879edfa873523ccb
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="choose-how-to-enroll-ios-and-macos-devices"></a>Scegliere come registrare i dispositivi iOS e macOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Questo argomento descrive i metodi che un amministratore IT può usare per abilitare la registrazione dei dispositivi iOS in Intune.

Usare le informazioni seguenti per scegliere il metodo di registrazione dei dispositivi iOS. Tutti i metodi seguenti, ad eccezione di BYOD, sono adatti alla registrazione dei dispositivi di proprietà dell'azienda.

**Prerequisito:** un [certificato per Apple Push Notification Service](apple-mdm-push-certificate-get.md).

## <a name="user-owned-ios-devices-byod"></a>Dispositivi iOS di proprietà dell'utente (BYOD)

Se gli utenti desiderano registrare i dispositivi personali BYOD (Bring Your Own Device), possono scaricare l'app Portale aziendale per iOS dall'App Store e quindi seguire le istruzioni per la registrazione all'interno dell'app. Una volta eseguita la registrazione, gli utenti possono connettersi alla rete aziendale, aggiungersi al dominio o ad Azure Active Directory e ottenere l'accesso alle risorse aziendali. Per abilitare BYOD, l'unico requisito è un [certificato per Apple Push Notification Service](apple-mdm-push-certificate-get.md). È inoltre possibile bloccare la registrazione di dispositivi iOS di proprietà personale. Per istruzioni, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md).

## <a name="user-owned-macos-devices-byod"></a>Dispositivi macOS di proprietà dell'utente (BYOD)

È possibile abilitare la registrazione dei dispositivi macOS. Per abilitare la registrazione dei dispositivi macOS, l'unico requisito è un [certificato per Apple Push Notification Service](apple-mdm-push-certificate-get.md). Per altre informazioni, vedere [Registrare i dispositivi macOS](./macos-enroll.md)

## <a name="enrollment-program-with-apple"></a>Programma di registrazione con Apple
Apple offre programmi per l'acquisto di dispositivi che includono la registrazione del dispositivo e l'infrastruttura di gestione. I dispositivi acquistati tramite uno di questi programmi possono essere registrati in blocco in modalità wireless assegnando i numeri di serie dei dispositivi alla gestione di Intune.

- **Device Enrollment Program (DEM)** - Programma di registrazione dei dispositivi di Apple per le aziende e le organizzazioni. Per altre informazioni, vedere [Enroll iOS devices using Device Enrollment Program](device-enrollment-program-enroll-ios.md) (Registrare dispositivi iOS con il programma di registrazione dispositivi).
- **Apple School Manager** - Programma di registrazione dei dispositivi Apple per le scuole. Per altre informazioni, vedere [Abilitare la registrazione di dispositivi iOS con Apple School Manager](apple-school-manager-set-up-ios.md)

## <a name="apple-configurator"></a>Apple Configurator

È possibile registrare i dispositivi iOS esportando un profilo di registrazione aziendale e collegando tali dispositivi mobili a un Mac che esegue Apple Configurator. Apple Configurator supporta due forme di registrazione:

- **Registrazione di Assistente configurazione**: esegue il ripristino delle impostazioni predefinite del dispositivo e lo prepara per consentire al nuovo utente del dispositivo di installarlo. Questo metodo prevede che l'amministratore connetta il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione Apple Configurator per preconfigurare la registrazione. I dispositivi vengono quindi distribuiti agli utenti, che eseguono Assistente configurazione al primo avvio del dispositivo. Questo processo consente di configurare il dispositivo con le credenziali aziendali dell'utente o dell'istituto di istruzione e di completare la registrazione. Per altre informazioni, vedere [Enroll iOS devices using Apple Configurator and Setup Assistant](apple-configurator-setup-assistant-enroll-ios.md) (Registrare dispositivi iOS con Apple Configurator e Assistente configurazione).

- **Registrazione diretta**: crea un file compatibile con Apple Configurator da usare durante la preparazione dei dispositivi. Non viene eseguito il ripristino delle impostazioni di fabbrica del dispositivo, che risulta però non associato a un utente. Per registrare i dispositivi, l'amministratore deve connettere il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione Apple Configurator. Per altre informazioni, vedere [Enroll iOS devices using Apple Configurator Direct Enrollment](apple-configurator-direct-enroll-ios.md) (Registrare dispositivi iOS con Apple Configurator e Registrazione diretta).

## <a name="use-the-device-enrollment-program-dep"></a>Usare il programma di registrazione dispositivi

Il programma di registrazione dispositivi distribuisce un profilo di registrazione ai dispositivi acquistati tramite il programma di registrazione dispositivi. Quando un utente esegue Assistente configurazione al primo avvio del dispositivo, il dispositivo viene registrato in Intune. Per altre informazioni, vedere [Enroll iOS devices using Device Enrollment Program](device-enrollment-program-enroll-ios.md) (Registrare dispositivi iOS con il programma di registrazione dispositivi).

## <a name="use-the-device-enrollment-manager-dem"></a>Usare un manager di registrazione dispositivi (DEM)
Il manager di registrazione dispositivi è un account utente generico che consente di registrare e gestire fino a 1.000 dispositivi. I dispositivi gestiti tramite DEM non possono avere affinità utente, pertanto il dispositivo non ha un proprietario. È possibile assegnare a un utente di Intune le autorizzazioni DEM per offrire queste funzionalità. Ogni dispositivo registrato dall'utente DEM usa una licenza Intune. Per altre informazioni, vedere [Enroll devices using device enrollment manager](device-enrollment-manager-enroll.md) (Registrare dispositivi con il manager di registrazione dispositivi).
