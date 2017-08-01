---
title: Scegliere come registrare i dispositivi Windows in Intune
titleSuffix: Intune on Azure
description: Informazioni su come impostare la registrazione dei dispositivi Windows in Microsoft Intune."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 439c33a6-e80c-4da9-ba09-a51fc36f62ad
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 61bdbc7ca68995e23295cf099ce73dfdcaeba37c
ms.sourcegitcommit: 5eb209ae48173ddfdbbab131f12f3ac3498dcd87
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/18/2017
---
# <a name="enroll-ios-devices-in-intune"></a>Registrare i dispositivi iOS in Intune

Intune consente la gestione di dispositivi mobili (MDM, Mobile Device Management) per iPad e iPhone e offre agli utenti l'accesso alla posta elettronica e alle app aziendali.

Come amministratore di Intune, è possibile abilitare la registrazione per i dispositivi iOS. È possibile consentire agli utenti di registrare dispositivi di proprietà personale, tramite la registrazione di tipo "bring your own device" (BYOD). È anche possibile abilitare la registrazione di dispositivi di proprietà dell'azienda.

## <a name="prerequisites-for-ios-enrollment"></a>Prerequisiti per la registrazione iOS
Prima di abilitare i dispositivi iOS, completare i passaggi seguenti:
- [Configurare Intune](setup-steps.md): questi passaggi consentono di impostare l'infrastruttura Intune. In particolare, per la registrazione del dispositivo è necessario [impostare l'autorità di gestione dei dispositivi mobili](mdm-authority-set.md).
- [Ottenere un certificato push MDM di Apple](apple-mdm-push-certificate-get.md): Apple richiede un certificato per abilitare la gestione dei dispositivi iOS e macOS.

Dopo aver completato i prerequisiti, gli utenti possono installare l'app Portale aziendale per registrare i propri dispositivi iOS personali. In alternativa, l'amministratore può configurare la gestione dei dispositivi iOS di proprietà dell'azienda. Gli amministratori possono anche assegnare [manager di registrazione dispositivi](device-enrollment-manager-enroll.md) che possono registrare più dispositivi con un account di gestione singolo. Intune supporta i metodi di registrazione dei dispositivi iOS di proprietà dell'azienda seguenti:

## <a name="device-enrollment-program"></a>Programma di registrazione dispositivi
Le organizzazioni possono ora acquistare i dispositivi iOS tramite Device Enrollment Program (DEP) di Apple. DEP consente di distribuire un profilo di registrazione in modalità wireless per portare i dispositivi nella gestione. Altre informazioni su [Device Enrollment Program](device-enrollment-program-enroll-ios.md).

## <a name="apple-school-manager"></a>Apple School Manager
Apple School Manager è un programma di acquisto e registrazione dei dispositivi per le scuole. Analogamente a DEP, consente di distribuire un profilo per registrare i dispositivi nella gestione. Altre informazioni su [Apple School Manager](apple-school-manager-set-up-ios.md).

## <a name="apple-configurator"></a>Apple Configurator
È possibile registrare i dispositivi iOS con Apple Configurator in esecuzione su un computer Mac. Per preparare i dispositivi, connetterli tramite USB e installare un profilo di registrazione. È possibile registrare i dispositivi con Apple Configurator in due modi:
- Registrazione di Assistente configurazione: ripristina le impostazioni predefinite del dispositivo e lo prepara per l'esecuzione di Assistente configurazione, installando i criteri della società per il nuovo utente del dispositivo.
- Registrazione diretta: non ripristina le impostazioni predefinite del dispositivo e lo registra con un criterio predefinito. Questo metodo è destinato ai dispositivi senza affinità utente.

Altre informazioni sulla [Registrazione con Apple Configurator](apple-configurator-setup-assistant-enroll-ios.md).
