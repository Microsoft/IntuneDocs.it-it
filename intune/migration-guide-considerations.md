---
title: Considerazioni speciali sulla migrazione
titlesuffix: Microsoft Intune
description: Questo articolo offre considerazioni speciali sulla migrazione, utili prima di avviare una campagna di migrazione a Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: 039b3dc4d45b340a7d7f8ed0314661a2505a779b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52179817"
---
# <a name="special-migration-considerations"></a>Considerazioni speciali sulla migrazione

Esistono alcune considerazioni speciali sulla migrazione che potrebbero essere applicabili a seconda dell'ambiente del provider MDM esistente.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Cancellare Device Enrollment Program (DEP) di Apple

Il programma DEP (Device Enrollment Program) Apple consente di impostare configurazioni dei dispositivi che non possono essere rimosse dall'utente finale. Per mantenere le funzionalità di gestione avanzate del programma DEP, il dispositivo deve essere riportato allo stato originale (nuovo) tramite un ripristino per la registrazione in Intune.

Per continuare a usare DEP per gestire i dispositivi in Intune, [impostare la registrazione dei dispositivi iOS con Device Enrollment Program](device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Passaggi successivi

[Fase 2: Campagna di migrazione](migration-guide-campaign.md)
