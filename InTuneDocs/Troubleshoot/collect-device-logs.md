---
title: Raccogliere i log dei dispositivi | Microsoft Intune
description: 
keywords: 
author: Nbigman
manager: angrobe
ms.date: 06/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb0aeac2f94dfde50d9398b09c6b21c7ae40624
ms.openlocfilehash: fb4bc718212480b9e44dc964b432dc2e37b3e531


---

# Log dei dispositivi

Nell'ambito delle attività di risoluzione dei problemi è necessario raccogliere i log dai dispositivi degli utenti. Le istruzioni per la raccolta dei log sono descritte qui. In genere è necessario accedere ai dispositivi o chiedere agli utenti di raccogliere il log e inviarlo.

### Posizione del log per Android
I log di Android si trovano in *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. L'utente può inviare i file di log anche in un messaggio di posta elettronica, come descritto in [Send diagnostic data logs to your IT administrator using email](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) (Inviare i log dei dati Android di diagnostica all'amministratore IT tramite posta elettronica).

### Log iOS

L'utente può inviare gli errori di registrazione come descritto in [Send iOS enrollment errors to your IT administrator](/intune/enduser/send-errors-to-your-it-admin-ios) (Inviare gli errori di registrazione iOS all'amministratore IT)

### Dispositivi Mac OS X

1. Aprire l'app **Console**.
2. In **FILE** scegliere **system.log**.
3. Nella barra dei menu nella parte superiore scegliere **File** > **Salva una copia con nome** e salvare il file.

### Windows Phone

Nel **portale aziendale di Windows Phone**, l'utente deve scegliere **...** per accedere al menu, quindi deve scegliere **Invia log**. Questa opzione è disponibile sia prima che dopo l'accesso al portale.

### Windows

Per il portale aziendale di Windows i log si trovano in *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Aug16_HO1-->


