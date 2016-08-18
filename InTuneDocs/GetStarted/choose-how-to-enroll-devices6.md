---
title: Scegliere come registrare i dispositivi mobili | Microsoft Intune
description: Decidere come registrare i dispositivi mobili in Intune rispondendo ad alcune semplici domande
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
translationtype: Human Translation
ms.sourcegitcommit: e1fe6b167b7d46f03472833bc1c3c19030f47bce
ms.openlocfilehash: 38dce11fa7df302bc2dffc3a2352d516c873fedb


---
# Scegliere come registrare i dispositivi mobili

Le risposte alla serie di domande seguente consentono di determinare il metodo di registrazione migliore per i dispositivi gestiti.

## **Come vengono gestiti i dispositivi iOS dedicati?**

  > [!div class="button"]
  [Tag con IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers) [Programma di registrazione dispositivi iOS >](/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) [Assistente configurazione iOS >](/intune/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune) [Tag con IMEI >](/intune/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  È possibile registrare i dispositivi di proprietà dell'azienda con utenti dedicati nei modi seguenti:

  - **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con questo programma possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con Intune.

  - **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare la registrazione di Assistente configurazione.

  - **Contrassegno con codice IMEI**: importando i codici IMEI (International Mobile Equipment Identity) dei dispositivi di proprietà dell'azienda è possibile contrassegnarli come dispositivi di proprietà dell'azienda in Intune. Gli utenti possono quindi registrare i propri dispositivi come dispositivo personali installando il portale aziendale per accedere a risorse aziendali come posta elettronica, applicazioni e dati.

  > [!div class="button"]
  [< Indietro](choose-how-to-enroll-devices3.md)



<!--HONumber=Aug16_HO2-->


