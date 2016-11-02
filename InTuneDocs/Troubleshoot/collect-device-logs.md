---
title: Raccogliere i log dei dispositivi | Microsoft Intune
description: Informazioni su come raccogliere registri da dispositivi gestiti.
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3a081109cd499d3bdda75cb6c8a4dab9d9d28fab
ms.openlocfilehash: ec7d522e8dcff66d1b84fed3c4c0cc708e555e67


---

# <a name="device-logs"></a>Log dei dispositivi

Nell'ambito delle attività di risoluzione dei problemi è necessario raccogliere i log dai dispositivi degli utenti. Le istruzioni per la raccolta dei log sono descritte qui. In genere è necessario accedere ai dispositivi o chiedere agli utenti di raccogliere il log e inviarlo.

### <a name="android-log-location"></a>Posizione del log per Android
I log di Android si trovano in *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. L'utente può inviare i file di log anche in un messaggio di posta elettronica, come descritto in [Send diagnostic data logs to your IT administrator using email](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) (Inviare i log dei dati Android di diagnostica all'amministratore IT tramite posta elettronica).

### <a name="ios-logs"></a>Log iOS

L'utente può inviare gli errori di registrazione come descritto in [Send iOS enrollment errors to your IT administrator](/intune/enduser/send-errors-to-your-it-admin-ios) (Inviare gli errori di registrazione iOS all'amministratore IT)

### <a name="mac-os-x-devices"></a>Dispositivi Mac OS X

1. Aprire l'app **Console**.
2. In **FILE** scegliere **system.log**.
3. Nella barra dei menu nella parte superiore scegliere **File** > **Salva una copia con nome** e salvare il file.

### <a name="windows-phone"></a>Windows Phone

Nel **portale aziendale di Windows Phone**, l'utente deve scegliere **...** per accedere al menu, quindi deve scegliere **Invia log**. Questa opzione è disponibile sia prima che dopo l'accesso al portale.

### <a name="windows"></a>Windows

Per il portale aziendale di Windows i log si trovano in *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Oct16_HO3-->


