---
title: Configurare i criteri di protezione delle app durante una migrazione a Intune
titlesuffix: Microsoft Intune
description: Questo articolo descrive i passaggi necessari per configurare i criteri di protezione delle app durante una migrazione a Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 93cda587-bf56-4d41-b123-9fe203fad788
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: fa9df81c363099cc487497fdd4503df8c91ea4a5
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55837034"
---
# <a name="configure-app-protection-policies-optional"></a>Configurare i criteri di protezione delle app (facoltativo)


I criteri di protezione delle app consentono di:
* Crittografare le app
* Definire un PIN quando viene effettuato l'accesso all'app
* Bloccare l'esecuzione delle app su dispositivi jailbroken o rooted e applicare molte altre protezioni.

In caso di smarrimento o furto del telefono di un utente, è possibile cancellare selettivamente i dati aziendali da remoto mantenendo intatti i dati personali.

I criteri di protezione delle app consentono di imporre la sicurezza a livello di app e non richiedono la registrazione dei dispositivi, quindi è possibile usarli nei dispositivi indipendentemente dal fatto che siano registrati in Intune. È anche possibile applicarli a dispositivi registrati in un provider MDM di terze parti.

## <a name="app-protection-policies-with-lob-apps"></a>Criteri di protezione delle app con app LOB

I criteri di protezione delle app per dispositivi mobili possono anche essere estesi alle app line-of-business (LOB) usando [Microsoft Intune App SDK](app-sdk-get-started.md) o lo strumento di wrapping delle app di Microsoft Intune per entrambe le piattaforme iOS e Android. Per altre informazioni, vedere [Strumento di wrapping delle app per iOS](app-wrapper-prepare-ios.md) e [Strumento di wrapping delle app per Android](app-wrapper-prepare-android.md). Vedere anche [Preparare app line-of-business per la protezione delle app](apps-prepare-mobile-application-management.md).

## <a name="how-do-app-protection-policies-help-during-migration"></a>Utilità dei criteri di protezione delle app durante la migrazione

In una migrazione è necessario rimuovere i dispositivi dal provider MDM precedente e registrarli in Intune. È necessario pianificare questo passaggio e invitare gli utenti finali a lasciare il vecchio provider MDM e registrarsi immediatamente in Intune. È tuttavia possibile che, durante la migrazione, alcuni utenti ritardino il processo di registrazione e che i loro dispositivi rimangano non gestiti da alcun provider MDM.

Durante questo periodo l'organizzazione può essere più vulnerabile per il furto dei dispositivi e la perdita dei dati aziendali, se è ancora consentito l'accesso alle risorse aziendali. Potrebbe anche essere soggetta a una riduzione della produttività degli utenti se l'accesso alle risorse aziendali è bloccato.

Intune può offrire misure di protezione dei dati aziendali durante la migrazione, in modo da poter contare ancora su una copertura per la sicurezza dei dati aziendali anche se non è presente una soluzione di gestione a livello di dispositivi.

Dopo aver disabilitato l'accesso condizionale nel provider MDM precedente, gli utenti possono rimanere produttivi durante il processo di onboarding in Intune.

## <a name="task-list-for-app-protection-policies"></a>Elenco di attività per i criteri di protezione delle app

1. [Creare un criterio di protezione delle app](app-protection-policies.md#create-an-app-protection-policy)
2. [Distribuire un criterio](app-protection-policies.md#deploy-a-policy-to-users)


## <a name="next-steps"></a>Passaggi successivi

[Considerazioni speciali sulla migrazione](migration-guide-considerations.md)
