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
ms.reviewer: lancecra
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 665f57a4cdb25c1e9f2bef7f1c25f284589df16f
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="wipe-for-exchange-managed-mobile-devices"></a>Cancellazione dei dispositivi mobili gestiti da Exchange

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune consente di cancellare o ripristinare i dispositivi mobili gestiti usando Exchange ActiveSync (EAS) con Intune Exchange Connector. Nella tabella seguente sono descritte le funzionalità di cancellazione disponibili tramite Exchange ActiveSync:

|Tipo di cancellazione|Windows 8.1 e Windows RT 8.1|iOS|Android|
|----------------|----------------------------------|--------------|-------------------|-------|-----------|
|Cancellazione completa|Rimuove l'account di posta elettronica e i messaggi di posta elettronica memorizzati nella cache.|Ripristino delle impostazioni predefinite.|Ripristino delle impostazioni predefinite.|
|Cancellazione selettiva/posta elettronica|Rimuove l'account di posta elettronica.|Non supportata.|Non supportata.|
|Cancellazione selettiva/criteri|L'applicazione dei criteri viene rimossa, ma non vengono modificate le impostazioni|L'applicazione dei criteri viene rimossa, ma non vengono modificate le impostazioni.|L'applicazione dei criteri viene rimossa, ma le impostazioni non vengono modificate.|
