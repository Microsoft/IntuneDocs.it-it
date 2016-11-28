---
title: Scegliere come registrare i dispositivi mobili | Microsoft Intune
description: Decidere come registrare i dispositivi mobili in Intune rispondendo ad alcune semplici domande
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cac62b64-3f8b-47ae-aa66-970c7ba15466
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: a563105aafb447c6e009cca09645e630709ff72d
ms.openlocfilehash: 143f77bde09648a233ff09e9740668191a50cb1e


---

# <a name="choose-how-to-enroll-mobile-devices"></a>Scegliere come registrare i dispositivi mobili

Le risposte alle domande seguenti consentono di determinare il metodo migliore di registrazione per i dispositivi gestiti.

## <a name="do-employees-bring-their-own-devices-or-are-devices-provided-by-your-organization"></a>**I dipendenti portano al lavoro i propri dispositivi o usano quelli dell'organizzazione?**

  - **Dispositivi di proprietà degli utenti** - Registrazione BYOD (Bring your own device)
  - **Dispositivi di proprietà dell'azienda** -Registrazione COD

> [!div class="button"]
[Registrazione BYOD >](#what-byod-devices-can-your-users-enroll)   
> [!div class="button"]
[Registrazione COD >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## <a name="what-byod-devices-can-your-users-enroll"></a>**Quali dispositivi BYOD possono essere registrati dagli utenti?**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile e Windows Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [PC Windows](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## <a name="are-your-company-owned-devices-shared-or-do-they-have-dedicated-users"></a>**I dispositivi di proprietà della società sono condivisi o sono usati da utenti dedicati?**

> [!div class="button"]
[Condiviso >](#what-operating-system-are-your-shared-devices-running)   [Dedicato >](#how-will-you-manage-dedicated-ios-devices)


## <a name="what-operating-system-are-your-shared-devices-running"></a>**Quale sistema operativo viene eseguito dai dispositivi condivisi?**

> [!div class="button"]
[Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## <a name="how-will-you-manage-shared-ios-devices"></a>**Come vengono gestiti i dispositivi iOS condivisi?**

> [!div class="button"]
[Registrazione Programma di registrazione dispositivi iOS >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Registrazione diretta iOS >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune) [Registrazione Manager di registrazione dispositivi >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con il programma DEP possono essere associati a un profilo di registrazione. Quando un utente avvia il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con quel profilo.

  - **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Se è possibile ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare l'opzione Registrazione di Assistente configurazione. Se non si vuole ripristinare le impostazioni di fabbrica dei dispositivi, usare l'opzione Registrazione diretta.

  - **Manager di registrazione dispositivi (Intune)**: DEM (Device Enrollment Manager, Manager di registrazione dispositivi) di Intune consente a un manager o a un amministratore di registrare vari dispositivi mobili con un account utente singolo. Questi dispositivi non possono avere utenti dedicati (affinità utente) e devono registrarsi installando e accedendo tramite l'app Portale aziendale.

## <a name="how-will-you-manage-dedicated-ios-devices"></a>**Come vengono gestiti i dispositivi iOS dedicati?**

> [!div class="button"]
[DEP iOS](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Assistente configurazione di iOS](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Tag con IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  È possibile registrare i dispositivi di proprietà dell'azienda con utenti dedicati nei modi seguenti:

  - **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con il programma DEP possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con Intune.

  - **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Se è possibile ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare l'opzione Registrazione di Assistente configurazione.

  - **Tag con codice IMEI**: importando i codici IMEI (International Mobile Equipment Identity) dei dispositivi di proprietà dell'azienda è possibile contrassegnarli come dispositivi di proprietà dell'azienda in Intune. Gli utenti possono registrare i propri dispositivi come dispositivi personali installando il portale aziendale per accedere a risorse aziendali, ad esempio posta elettronica, app e dati.



<!--HONumber=Nov16_HO4-->


