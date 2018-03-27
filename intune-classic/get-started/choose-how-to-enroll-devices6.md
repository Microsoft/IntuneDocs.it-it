---
title: Scegliere come registrare i dispositivi mobili
description: Decidere come registrare i dispositivi mobili in Intune rispondendo ad alcune semplici domande
keywords: ''
author: NathBarn
ms.author: nathbarn
manager: dougeby
ms.date: 03/27/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 40262e47-1ab4-437d-8ca5-c89b5022f91f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.openlocfilehash: fd09126b8226828ccb60f30e0daa6135643303e2
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2018
---
# <a name="choose-how-to-enroll-mobile-devices"></a>Scegliere come registrare i dispositivi mobili

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Le risposte alla serie di domande seguente consentono di determinare il metodo di registrazione migliore per i dispositivi gestiti.

## <a name="how-will-you-manage-dedicated-corporate-owned-devices"></a>**Come vengono gestiti i dispositivi dedicati di proprietà dell'azienda?**

  > [!div class="button"]
[Programma di registrazione dispositivi iOS >](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)  
> [!div class="button"]
[Assistente configurazione iOS >](/intune-classic/deploy-use/ios-setup-assistant-enrollment-in-microsoft-intune)
> [!div class="button"]
[Tag con IMEI >](/intune-classic/deploy-use/specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers)

  È possibile registrare i dispositivi di proprietà dell'azienda con utenti dedicati nei modi seguenti:

  - **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con questo programma possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con Intune.

  - **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare la registrazione di Assistente configurazione.

  - **Contrassegno con codice IMEI**: importando i codici IMEI (International Mobile Equipment Identity) dei dispositivi di proprietà dell'azienda è possibile contrassegnarli come dispositivi di proprietà dell'azienda in Intune. Questo è l'unico modo per identificare come di proprietà dell'azienda i dispositivi Windows e Android ("utente singolo") dedicati. I dispositivi iOS che non devono essere registrati con il programma di registrazione dispositivi di Apple o con Apple Configurator possono essere contrassegnati anche con un numero IMEI. Dopo aver dichiarato preventivamente il dispositivo in modo che venga contrassegnato come "aziendale", è possibile distribuire i dispositivi agli utenti. Gli utenti possono quindi registrare i propri dispositivi come dispositivi dedicati installando il portale aziendale per accedere a risorse aziendali come posta elettronica, app e dati.

> [!div class="button"]
[< Indietro](choose-how-to-enroll-devices3.md)
