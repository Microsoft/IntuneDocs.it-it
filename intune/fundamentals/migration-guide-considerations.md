---
title: Considerazioni speciali sulla migrazione
titleSuffix: Microsoft Intune
description: Questo articolo offre considerazioni speciali sulla migrazione, utili prima di avviare una campagna di migrazione a Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f29d2894-e98b-4f2c-b444-a8ccc1b7efdd
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 936e4836938ddddc8e795d85de5a449ee77edaa4
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515000"
---
# <a name="special-migration-considerations"></a>Considerazioni speciali sulla migrazione

Esistono alcune considerazioni speciali sulla migrazione che potrebbero essere applicabili a seconda dell'ambiente del provider MDM esistente.

## <a name="wipe-for-apples-device-enrollment-program-dep"></a>Cancellare Device Enrollment Program (DEP) di Apple

Il programma DEP (Device Enrollment Program) Apple consente di impostare configurazioni dei dispositivi che non possono essere rimosse dall'utente finale. Per mantenere le funzionalità di gestione avanzate del programma DEP, il dispositivo deve essere riportato allo stato originale (nuovo) tramite un ripristino per la registrazione in Intune.

Per continuare a usare DEP per gestire i dispositivi in Intune, [impostare la registrazione dei dispositivi iOS/iPadOS con Device Enrollment Program](../enrollment/device-enrollment-program-enroll-ios.md).


## <a name="next-steps"></a>Passaggi successivi

[Fase 2: Campagna di migrazione](../migration-guide-campaign.md)
