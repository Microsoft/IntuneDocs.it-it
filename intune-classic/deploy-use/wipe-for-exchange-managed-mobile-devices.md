---
title: Cancellazione dei dispositivi mobili gestiti da Exchange
description: Microsoft Intune consente di cancellare o ripristinare i dispositivi mobili gestiti usando Exchange ActiveSync (EAS) con Intune Exchange Connector
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 11/14/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e116b620-1e12-4b5c-9905-2f7acf2ae530
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 31c5707424e582c9e86d8a271e4c03d5668c315c
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2017
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Cancellazione dei dispositivi mobili gestiti da Exchange

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune consente di cancellare o ripristinare i dispositivi mobili gestiti usando Exchange ActiveSync (EAS) con Intune Exchange Connector. Nella tabella seguente sono descritte le funzionalità di cancellazione disponibili tramite Exchange ActiveSync:

|Tipo di cancellazione|Windows 8.1 e Windows RT 8.1|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|Cancellazione completa|Rimuove l'account di posta elettronica e i messaggi di posta elettronica memorizzati nella cache.|Ripristino delle impostazioni predefinite.|Ripristino delle impostazioni predefinite.|
|Cancellazione selettiva/posta elettronica|Rimuove l'account di posta elettronica.|Non supportata.|Non supportata.|
|Cancellazione selettiva/criteri|L'applicazione dei criteri viene rimossa, ma non vengono modificate le impostazioni|L'applicazione dei criteri viene rimossa, ma non vengono modificate le impostazioni.|L'applicazione dei criteri viene rimossa, ma le impostazioni non vengono modificate.|
