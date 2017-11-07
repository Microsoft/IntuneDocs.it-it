---
title: Scegliere come registrare i dispositivi Windows in Intune
titlesuffix: Azure portal
description: Informazioni su come impostare la registrazione dei dispositivi Windows in Microsoft Intune."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 307f4b8d5ba27ce8136569e0c58711f9b1364d93
ms.sourcegitcommit: 94d3d86f8ae9f82a9872384bbaae53580036a4ff
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/01/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Registrare i dispositivi iOS in Intune

Intune consente la gestione di dispositivi mobili (MDM, Mobile Device Management) per iPad e iPhone e offre agli utenti l'accesso alla posta elettronica e alle app aziendali.

Come amministratore di Intune, è possibile abilitare la registrazione per i dispositivi iOS. È possibile consentire agli utenti di registrare dispositivi di proprietà personale, tramite la registrazione di tipo "bring your own device" (BYOD). È anche possibile abilitare la registrazione di dispositivi di proprietà dell'azienda.

## <a name="prerequisites-for-ios-enrollment"></a>Prerequisiti per la registrazione iOS
Prima di abilitare i dispositivi iOS, completare i passaggi seguenti:
- [Configurare Intune](setup-steps.md): questi passaggi consentono di impostare l'infrastruttura Intune. In particolare, per la registrazione del dispositivo è necessario [impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md).
- [Ottenere un certificato push MDM di Apple](apple-mdm-push-certificate-get.md): Apple richiede un certificato per abilitare la gestione dei dispositivi iOS e macOS.

## <a name="user-owned-ios-devices-byod"></a>Dispositivi iOS di proprietà dell'utente (BYOD)

È possibile consentire agli utenti di registrare i dispositivi personali per la gestione di Intune, una funzionalità nota come BYOD (Bring Your Own Device, Usa dispositivo personale). Dopo aver completato i prerequisiti e assegnato le licenze, gli utenti possono scaricare l'app Portale aziendale iOS dall'App Store e seguire le istruzioni di registrazione nell'app.

## <a name="company-owned-ios-devices"></a>Dispositivi iOS di proprietà dell'azienda
Per le organizzazioni che acquistano dispositivi per i propri utenti, Intune supporta i seguenti metodi di registrazione dei dispositivi iOS di proprietà dell'azienda:

- Device Enrollment Program (DEP) di Apple
- Apple School Manager
- Registrazione con Assistente configurazione e Apple Configurator
- Registrazione diretta con Apple Configurator

È anche possibile registrare i dispositivi iOS di proprietà dell'azienda con un account [Manager di registrazione dispositivi](device-enrollment-manager-enroll.md).

## <a name="device-enrollment-program"></a>Programma di registrazione dispositivi
Le organizzazioni possono ora acquistare i dispositivi iOS tramite Device Enrollment Program (DEP) di Apple. DEP consente di distribuire un profilo di registrazione in modalità wireless per portare i dispositivi nella gestione. Altre informazioni su [Device Enrollment Program](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager è un programma di acquisto e registrazione dei dispositivi per le scuole. Analogamente a DEP, consente di distribuire un profilo per registrare i dispositivi nella gestione. Altre informazioni su [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
È possibile registrare i dispositivi iOS con Apple Configurator in esecuzione su un computer Mac. Per preparare i dispositivi, connetterli tramite USB e installare un profilo di registrazione. È possibile registrare i dispositivi con Apple Configurator in due modi:
- Registrazione di Assistente configurazione: ripristina le impostazioni predefinite del dispositivo e lo prepara per l'esecuzione di Assistente configurazione, installando i criteri della società per il nuovo utente del dispositivo.
- Registrazione diretta: non ripristina le impostazioni predefinite del dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi senza affinità utente.

Altre informazioni sulla [Registrazione con Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
