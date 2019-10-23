---
title: Registrare i dispositivi Android in Intune
titleSuffix: Microsoft Intune
description: Informazioni su come registrare i dispositivi Android in Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 7/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f276d98c-b077-452a-8835-41919d674db5
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ff005ddded4178801e7e334f604280ef4408aaff
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505670"
---
# <a name="enroll-android-devices"></a>Registrare dispositivi Android

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'amministratore di Intune può registrare i dispositivi Android nei modi seguenti:
- Android Enterprise (offre un set di opzioni di registrazione che offrono agli utenti le funzionalità più aggiornate e sicure):
    - [**Profilo di lavoro di Android Enterprise**](android-work-profile-enroll.md): Per i dispositivi personali con autorizzazione ad accedere ai dati aziendali. Gli amministratori possono gestire gli account aziendali, le app e i dati. I dati personali nel dispositivo vengono tenuti separati dai dati di lavoro e gli amministratori non controllano le impostazioni o i dati personali. 
    - [**Android Enterprise dedicato**](android-kiosk-enroll.md): Per i dispositivi a uso singolo di proprietà dell'azienda, ad esempio per insegna digitale, stampa di biglietti o gestione dell'inventario. Gli amministratori bloccano l'utilizzo di un dispositivo per un set limitato di app e collegamenti Web. Viene anche impedito agli utenti di aggiungere altre app o eseguire altre azioni sul dispositivo.
    - [**Android Enterprise completamente gestito**](android-fully-managed-enroll.md): Per i dispositivi con utente singolo di proprietà dell'azienda, usati esclusivamente per lavoro e non per uso personale. Gli amministratori possono gestire interamente tali dispositivi e applicare controlli di criteri non disponibili nei profili di lavoro. 
- [**Amministratore di dispositivo Android**](android-enroll-device-administrator.md), inclusi i dispositivi Samsung Knox Standard e [Zebra](../configuration/android-zebra-mx-overview.md). 

## <a name="prerequisites"></a>Prerequisiti

Per preparare la gestione dei dispositivi mobili è necessario impostare l'autorità per la gestione dei dispositivi mobili su **Microsoft Intune**. Vedere [Impostare l'autorità MDM](../fundamentals/mdm-authority-set.md) per le istruzioni. Questo elemento viene impostato una sola volta quando si configura Intune per la gestione dei dispositivi mobili per la prima volta.

Per i dispositivi prodotti da Zebra Technologies, potrebbe essere necessario concedere al portale aziendale autorizzazioni aggiuntive a seconda delle funzionalità del dispositivo specifico. Per altri dettagli, vedere [Estensioni di mobilità nei dispositivi Zebra](../configuration/android-zebra-mx-overview.md).

Per i dispositivi Samsung Knox Standard, sono richiesti [ulteriori prerequisiti](android-samsung-knox-mobile-enroll.md).

## <a name="next-steps"></a>Passaggi successivi

- [Configurare la registrazione dei dispositivi del profilo di lavoro Android Enterprise](android-work-profile-enroll.md)
- [Configurare la registrazione in Intune di dispositivi Android Enterprise dedicati](android-kiosk-enroll.md)
- [Configurare la registrazione in Intune per dispositivi Android Enterprise completamente gestiti](android-fully-managed-enroll.md)
- [Configurare la registrazione di tipo amministratore di dispositivi Android](android-enroll-device-administrator.md)

