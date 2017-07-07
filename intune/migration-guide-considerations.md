---
title: Considerazioni speciali sulla migrazione
description: "Lo scopo di questo articolo è presentare ai clienti alcune considerazioni speciali sulla migrazione di cui tenere conto prima di avviare una campagna di migrazione."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bc39ffd3a4f11a4c2b32f75dc5befcd8ce42f43e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="special-migration-considerations"></a>Considerazioni speciali sulla migrazione

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

Esistono alcune considerazioni speciali sulla migrazione che potrebbero essere applicabili a seconda dell'ambiente del provider MDM esistente.

## <a name="factory-reset-for-apples-device-enrollment-program-dep"></a>Ripristino delle impostazioni predefinite per il programma DEP (Device Enrollment Program) Apple

Il programma DEP (Device Enrollment Program) Apple consente di impostare configurazioni dei dispositivi che non possono essere rimosse dall'utente finale. Per mantenere le funzionalità di gestione avanzate del programma DEP, il dispositivo deve essere riportato allo stato originale (nuovo) tramite il ripristino delle impostazioni predefinite per la registrazione in Intune.

Per continuare a usare DEP per gestire i dispositivi in Intune, [impostare la registrazione dei dispositivi iOS con Device Enrollment Program](/intune/device-enrollment-program-enroll-ios).


## <a name="next-steps"></a>Passaggi successivi 

[Fase 2: Campagna di migrazione](migration-guide-campaign.md)
