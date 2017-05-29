---
title: Considerazioni speciali sulla migrazione | Microsoft Docs
description: "Lo scopo di questo articolo è presentare ai clienti alcune considerazioni speciali sulla migrazione di cui tenere conto prima di avviare una campagna di migrazione."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7e0adb862d8c60805b3b34406e193df5a93be381
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-special-migration-considerations"></a>Fase 1: Considerazioni speciali sulla migrazione

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Esistono alcune considerazioni speciali sulla migrazione che potrebbero essere applicabili a seconda dell'ambiente del provider MDM esistente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Ripristino delle impostazioni predefinite per il programma DEP (Device Enrollment Program) Apple

Il programma DEP (Device Enrollment Program) Apple consente di impostare configurazioni dei dispositivi che non possono essere rimosse dall'utente finale. Per mantenere le funzionalità di gestione avanzate del programma DEP, il dispositivo deve essere riportato allo stato originale (nuovo) tramite il ripristino delle impostazioni predefinite per la registrazione in Intune.

Per continuare a usare DEP per gestire i dispositivi in Intune:

1.  Eseguire l'onboarding di [DEP in Intune](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune).

2.  Passare all'account DEP Apple e [riassegnare i numeri di serie del dispositivo DEP](https://help.apple.com/deployment/business/#/tesf9562af26) dal provider MDM esistente a Intune.

3.  [Sincronizzare](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) l'account DEP con Intune.

4.  [Creare e assegnare](/intune-classic/deploy-use/ios-device-enrollment-program-in-microsoft-intune) i profili di registrazione DEP appropriati ai numeri di serie in Intune.

5.  Ripristinare le impostazioni predefinite dei dispositivi (in modalità remota tramite il provider MDM corrente o manualmente in ogni dispositivo).

6.  Distribuire i dispositivi agli utenti finali.

## <a name="next-steps"></a>Passaggi successivi 

[Fase 2: Campagna di migrazione](/intune-classic/plan-design/migration-phase2-migration-campaign)

