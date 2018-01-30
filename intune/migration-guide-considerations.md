---
title: Considerazioni speciali sulla migrazione
description: Questo articolo fornisce considerazioni speciali sulla migrazione prima di avviare una campagna di migrazione.
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.openlocfilehash: 86f3f7f2c8066e1b7b50dfc5931184c394d4f15b
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="special-migration-considerations"></a>Considerazioni speciali sulla migrazione

Esistono alcune considerazioni speciali sulla migrazione che potrebbero essere applicabili a seconda dell'ambiente del provider MDM esistente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Ripristino delle impostazioni predefinite per il programma DEP (Device Enrollment Program) Apple

Il programma DEP (Device Enrollment Program) Apple consente di impostare configurazioni dei dispositivi che non possono essere rimosse dall'utente finale. Per mantenere le funzionalità di gestione avanzate del programma DEP, il dispositivo deve essere riportato allo stato originale (nuovo) tramite un ripristino delle impostazioni predefinite per la registrazione in Intune.

Per continuare a usare DEP per gestire i dispositivi in Intune, [impostare la registrazione dei dispositivi iOS con Device Enrollment Program](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Passaggi successivi

[Fase 2: Campagna di migrazione](migration-guide-campaign.md)
