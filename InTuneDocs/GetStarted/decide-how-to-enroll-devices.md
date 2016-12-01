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
ms.assetid: 178df739-d3b9-43cb-8440-c5c110b1276b
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: 149f3a3310907d131affeaad4bd372aa60be9206
ms.openlocfilehash: b5cc645ea50e6c4bb521e04371037c3978c9426a


---

# <a name="choose-how-to-enroll-mobile-devices"></a>Scegliere come registrare i dispositivi mobili

La registrazione dei dispositivi mobili è il processo che consente la gestione di smartphone, tablet e PC da parte di Microsoft Intune. L'amministratore ha il compito di determinare qual è il modo migliore per registrare i dispositivi in base ai seguenti elementi:

 -  Proprietà (dispositivi personali e di proprietà della società)
 -  Utilizzo (condiviso o personale)
 -  Piattaforma (iOS, Android, Windows Phone, PC Windows, PC Mac)

Le risposte alle domande seguenti consentono di determinare il metodo di registrazione migliore per i dispositivi gestiti.

## <a name="do-employees-bring-their-own-devices-or-are-devices-provided-by-your-organization"></a>**I dipendenti portano al lavoro i propri dispositivi o usano quelli dell'organizzazione?**

  - **Dispositivi di proprietà degli utenti** (BYOD, Bring your own device): gli utenti possono installare l'app del portale aziendale di Intune sul dispositivo ed eseguire la registrazione, per accedere alle risorse della società come posta elettronica, applicazioni aziendali, dati aziendali e supporto.  

  - **Dispositivi di proprietà della società**: i dispositivi di proprietà della società possono essere registrati in diversi modi, a seconda delle esigenze dell'organizzazione e dei tipi di dispositivi gestiti.

> [!div class="button"]
[Registrazione BYOD >](#what-byod-devices-can-your-users-enroll)   [Registrazione COD >](#are-your-company-owned-devices-shared-or-do-they-have-dedicated-users)

## <a name="what-byod-devices-can-your-users-enroll"></a>**Quali dispositivi BYOD possono essere registrati dagli utenti?**

> [!div class="button"]
[Android](/intune/deploy-use/set-up-android-management-with-microsoft-intune) [iOS e Mac](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) [Windows 10 Mobile e Windows Phone](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune) [PC Windows](/intune/deploy-use/set-up-windows-device-management-with-microsoft-intune)

## <a name="are-your-company-owned-devices-shared-or-do-they-have-dedicated-users"></a>**I dispositivi di proprietà della società sono condivisi o sono usati da utenti dedicati?**

- **Dispositivi di proprietà della società condivisi**: questi dispositivi non hanno un singolo utente e non sono in genere configurati per accedere alla posta elettronica. Gli esempi includono i dispositivi chiosco o orientati alle attività prelevati da un pool in base alle esigenze e quindi restituiti. I metodi di registrazione consigliati dipendono dalla piattaforma dei dispositivi.

- **Utenti dedicati**: i dispositivi di proprietà dell'azienda rilasciati a singoli utenti devono essere registrati come risorse aziendali consentendo allo stesso tempo agli utenti di accedere alla posta elettronica e ai dati come se fossero dispositivi personali. I metodi di registrazione consigliati dipendono dalla piattaforma dei dispositivi.

> [!div class="button"]
[Condiviso >](#what-operating-system-are-your-shared-devices-running)   [Dedicato >](#how-will-you-manage-dedicated-ios-devices)


## <a name="what-operating-system-are-your-shared-devices-running"></a>**Quale sistema operativo viene eseguito dai dispositivi condivisi?**

> [!div class="button"]
[Windows >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [Android >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune) [iOS >](#how-will-you-manage-shared-ios-devices)

## <a name="how-will-you-manage-shared-ios-devices"></a>**Come vengono gestiti i dispositivi iOS condivisi?**

- **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con questo programma possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con quel profilo

- **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare la registrazione di Assistente configurazione. Se non si vuole riportare i dispositivi alle impostazioni di fabbrica, usare la registrazione diretta.

- **Manager di registrazione dispositivi**: il manager di registrazione dispositivi di Intune consente a un manager o a un amministratore di registrare diversi dispositivi mobili con un unico account utente. Questi dispositivi non possono avere l'affinità utente, ad esempio utenti dedicati, e devono essere registrati installando e accedendo all'app Portale aziendale.

  > [!div class="button"]
  [Registrazione Programma di registrazione dispositivi iOS >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Registrazione diretta iOS >](/intune/deploy-use/ios-direct-enrollment-in-microsoft-intune)  [Registrazione Manager di registrazione dispositivi >](/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

## <a name="how-will-you-manage-dedicated-ios-devices"></a>**Come vengono gestiti i dispositivi iOS dedicati?**

È possibile registrare i dispositivi di proprietà dell'azienda con utenti dedicati nei modi seguenti:

- **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con questo programma possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con Intune.

- **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare la registrazione di Assistente configurazione.

- **Contrassegno con codice IMEI**: importando i codici IMEI (International Mobile Equipment Identity) dei dispositivi di proprietà dell'azienda è possibile contrassegnarli come dispositivi di proprietà dell'azienda in Intune. Gli utenti possono quindi registrare i propri dispositivi come dispositivo personali installando il portale aziendale per accedere a risorse aziendali come posta elettronica, applicazioni e dati.

  > [!div class="button"]
  [Tag con IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [Programma di registrazione dispositivi iOS](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Assistente configurazione iOS](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Tag con IMEI](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)



<!--HONumber=Nov16_HO4-->


