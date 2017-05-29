---
title: Scegliere come registrare i dispositivi iOS in Intune
titleSuffix: Intune Azure preview
description: 'Anteprima di Intune in Azure: informazioni su come impostare la registrazione dei dispositivi iOS in Microsoft Intune.'
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e6c0a430-1851-4108-812a-87e0fc2623b5
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ee0ecf26a333ec441eb95e79473a9bf405e4120c
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="choose-how-to-enroll-ios-devices"></a>Scegliere come registrare i dispositivi iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Questo argomento descrive i metodi che è possibile usare per registrare i dispositivi iOS e i prerequisiti per la registrazione.

Usare le informazioni seguenti per scegliere il metodo di registrazione dei dispositivi iOS. Tutti i metodi seguenti, ad eccezione di BYOD, sono adatti alla registrazione dei dispositivi di proprietà dell'azienda.

**Prerequisito:** un [certificato per Apple Push Notification Service](apple-mdm-push-certificate-get.md).

## <a name="user-owned-ios-devices-byod"></a>Dispositivi iOS di proprietà dell'utente (BYOD)

Se gli utenti desiderano registrare i dispositivi personali BYOD (Bring Your Own Device), l'unico metodo di registrazione disponibile è il download dell'app Portale aziendale per iOS dall'App Store, all'interno della quale seguire le istruzioni per la registrazione. Una volta eseguita la registrazione, gli utenti possono connettersi alla rete aziendale, aggiungersi al dominio o ad Azure Active Directory e ottenere l'accesso alle risorse aziendali. È possibile bloccare la registrazione di dispositivi iOS di proprietà personale. Per istruzioni, vedere [Impostare le restrizioni sul tipo di dispositivi](enrollment-restrictions-set.md#set-device-type-restrictions).

## <a name="apple-configurator"></a>Apple Configurator

È possibile registrare i dispositivi iOS esportando un profilo di registrazione aziendale e collegando quindi i dispositivi mobili a un Mac dotato di [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017). Apple Configurator supporta due forme di registrazione:

- **Registrazione di Assistente configurazione**: esegue il ripristino delle impostazioni predefinite del dispositivo e lo prepara per consentire al nuovo utente del dispositivo di installarlo. Questo metodo prevede che l'amministratore connetta il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione Apple Configurator per preconfigurare la registrazione. I dispositivi vengono quindi distribuiti agli utenti che eseguono il processo di Assistente configurazione. Questo processo consente di configurare il dispositivo con le credenziali aziendali dell'utente o dell'istituto di istruzione e di completare la registrazione. Per altre informazioni, vedere [Enroll iOS devices using Apple Configurator and Setup Assistant](apple-configurator-setup-assistant-enroll-ios.md) (Registrare dispositivi iOS con Apple Configurator e Assistente configurazione).

- **Registrazione diretta**: crea un file compatibile con Apple Configurator da usare durante la preparazione dei dispositivi. Non viene eseguito il ripristino delle impostazioni di fabbrica del dispositivo, che risulta però non associato a un utente. Per registrare i dispositivi, l'amministratore deve connettere il dispositivo iOS tramite USB a un computer Mac in cui è in esecuzione Apple Configurator. Per altre informazioni, vedere [Enroll iOS devices using Apple Configurator Direct Enrollment](apple-configurator-direct-enroll-ios.md) (Registrare dispositivi iOS con Apple Configurator e Registrazione diretta).

## <a name="use-the-device-enrollment-program-dep"></a>Usare il programma di registrazione dispositivi

Il programma di registrazione dispositivi distribuisce un profilo di registrazione ai dispositivi acquistati tramite il programma di registrazione dispositivi. Quando un utente esegue Assistente configurazione nel dispositivo, il dispositivo viene registrato in Intune. La registrazione dei dispositivi registrati tramite DEP non può essere annullata dagli utenti. Per altre informazioni, vedere [Enroll iOS devices using Device Enrollment Program](device-enrollment-program-enroll-ios.md) (Registrare dispositivi iOS con il programma di registrazione dispositivi).

## <a name="use-the-device-enrollment-manager-dem"></a>Usare un manager di registrazione dispositivi (DEM)
Il manager di registrazione dispositivi è un tipo di account utente che consente di registrare e gestire fino a 1.000 dispositivi. Gli utenti esistenti vengono aggiunti all'account del manager di registrazione dispositivi per rendere disponibili tali funzionalità. Ogni dispositivo registrato dall'utente DEM usa una singola licenza Intune. Per altre informazioni, vedere [Enroll devices using device enrollment manager](device-enrollment-manager-enroll.md) (Registrare dispositivi con il manager di registrazione dispositivi).

