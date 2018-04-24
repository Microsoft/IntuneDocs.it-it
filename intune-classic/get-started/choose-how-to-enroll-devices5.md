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
ms.assetid: ed9250aa-e894-4eac-92b8-5f1a3748e255
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: dagerrit
ms.custom: intune-classic EXPIERIMENT
ms.openlocfilehash: c7e750d308c4167dd6e99f503ed52d3a96ea630b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="choose-how-to-enroll-mobile-devices"></a>Scegliere come registrare i dispositivi mobili

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Le risposte alla serie di domande seguente consentono di determinare il metodo di registrazione migliore per i dispositivi gestiti.

## <a name="how-will-you-manage-shared-ios-devices"></a>**Come vengono gestiti i dispositivi iOS condivisi?**

> [!div class="button"]
> [Registrazione Programma di registrazione dispositivi iOS >](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune)
> [!div class="button"]
> [Registrazione diretta iOS >](/intune-classic/deploy-use/ios-direct-enrollment-in-microsoft-intune)
> [!div class="button"]
> [Registrazione DEM >](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)

  - **Programma di registrazione dispositivi (DEP) di Apple**: i dispositivi iOS acquistati o gestiti con questo programma possono essere associati a un profilo di registrazione. Quando un utente accende il proprio dispositivo per la prima volta, il dispositivo scarica il profilo DEP ed esegue la registrazione con quel profilo.

  - **Apple Configurator in un Mac**: Apple Configurator è un'applicazione di Apple che viene eseguita in un computer Mac. È possibile collegare un dispositivo iOS al Mac con un cavo USB per installare un profilo di registrazione nel dispositivo. Per ripristinare le impostazioni di fabbrica dei dispositivi per registrarli, usare la registrazione di Assistente configurazione. Se non si vuole riportare i dispositivi alle impostazioni di fabbrica, usare la registrazione diretta.

  - **Manager di registrazione dispositivi**: il manager di registrazione dispositivi di Intune consente a un manager o a un amministratore di registrare diversi dispositivi mobili con un unico account utente. Questi dispositivi non possono avere l'affinità utente, ad esempio utenti dedicati, e devono essere registrati installando e accedendo all'app Portale aziendale.

> [!div class="button"]
> [< Indietro](choose-how-to-enroll-devices3.md)
