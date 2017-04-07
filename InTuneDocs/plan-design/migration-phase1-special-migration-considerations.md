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
translationtype: Human Translation
ms.sourcegitcommit: ab5aa4e12d951d818c5afb4e1ac5e866b05733fb
ms.openlocfilehash: 634e84312fa1a93eb85bf70e1593ca11359b72ff
ms.lasthandoff: 03/27/2017


---

# <a name="phase-1-special-migration-considerations"></a>Fase 1: Considerazioni speciali sulla migrazione

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Esistono alcune considerazioni speciali sulla migrazione che potrebbero essere applicabili a seconda dell'ambiente del provider MDM esistente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Ripristino delle impostazioni predefinite per il programma DEP (Device Enrollment Program) Apple

Il programma DEP (Device Enrollment Program) Apple consente di impostare configurazioni dei dispositivi che non possono essere rimosse dall'utente finale. Per mantenere le funzionalità di gestione avanzate del programma DEP, il dispositivo deve essere riportato allo stato originale (nuovo) tramite il ripristino delle impostazioni predefinite per la registrazione in Intune.

Per continuare a usare DEP per gestire i dispositivi in Intune:

1.  Eseguire l'onboarding di [DEP in Intune](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune).

2.  Passare all'account DEP Apple e [riassegnare i numeri di serie del dispositivo DEP](https://help.apple.com/deployment/business/#/tesf9562af26) dal provider MDM esistente a Intune.

3.  [Sincronizzare](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) l'account DEP con Intune.

4.  [Creare e assegnare](https://docs.microsoft.com/intune/deploy-use/ios-device-enrollment-program-in-microsoft-intune) i profili di registrazione DEP appropriati ai numeri di serie in Intune.

5.  Ripristinare le impostazioni predefinite dei dispositivi (in modalità remota tramite il provider MDM corrente o manualmente in ogni dispositivo).

6.  Distribuire i dispositivi agli utenti finali.

## <a name="next-steps"></a>Passaggi successivi 

[Fase 2: Campagna di migrazione](https://docs.microsoft.com/intune/plan-design/migration-phase2-migration-campaign)

