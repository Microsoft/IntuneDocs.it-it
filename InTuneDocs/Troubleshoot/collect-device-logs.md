---
title: Raccogliere i log dei dispositivi | Microsoft Intune
description: Informazioni su come raccogliere registri da dispositivi gestiti.
keywords: 
author: staciebarker
ms.author: staciebarker
manager: angrobe
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 19b0b502d2c8c261947c461f27a0e8153df5b186
ms.openlocfilehash: 1e65c1fa25e273ba03218f79ebeff611138e8013


---

# <a name="device-logs"></a>Log dei dispositivi

Nell'ambito delle attività di risoluzione dei problemi è necessario raccogliere i log dai dispositivi degli utenti. Le istruzioni per la raccolta dei log sono descritte qui. In genere è necessario accedere ai dispositivi o chiedere agli utenti di raccogliere il log e inviarlo.

### <a name="android-logs"></a>Log di Android
I log di Android si trovano in *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*. 

Talvolta i file non vengono visualizzati, specialmente nei dispositivi Android più recenti. In questo caso, chiedere agli utenti finali di aprire l'app Portale aziendale per Android e quindi di passare a **Impostazioni**, scegliere **Copia log** e quindi riavviare il dispositivo. 

Per altre informazioni su come gli utenti possono inviare i log di dati, vedere gli articoli seguenti:

- [Usare la registrazione dettagliata per aiutare l'amministratore IT a risolvere i problemi dei dispositivi](/intune/enduser/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) - Descrive la procedura per attivare la registrazione dettagliata, che consente l'invio automatico di tutti i log di dati degli utenti all'amministratore. La registrazione dettagliata è attivata per impostazione predefinita.

- [Inviare i log dei dati di diagnostica di Android all'amministratore IT tramite posta elettronica](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-email-android) 

- [Inviare i log dei dati di diagnostica all'amministratore IT tramite un cavo USB](/intune/enduser/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Log iOS

L'utente può inviare gli errori di registrazione come descritto in [Send iOS enrollment errors to your IT administrator](/intune/enduser/send-errors-to-your-it-admin-ios) (Inviare gli errori di registrazione iOS all'amministratore IT).

### <a name="mac-os-x-logs"></a>Log di Mac OS X

1. Aprire l'app **Console**.
2. In **FILE** scegliere **system.log**.
3. Nella barra dei menu nella parte superiore scegliere **File** > **Salva una copia con nome** e salvare il file.

### <a name="windows-phone"></a>Windows Phone

Nell'app Portale aziendale di Windows Phone l'utente deve scegliere **…** per accedere al menu, quindi deve scegliere **Invia log**. Questa opzione è disponibile sia prima che dopo l'accesso all'app Portale aziendale.

### <a name="windows"></a>Windows

Per il portale aziendale di Windows i log si trovano in *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.



<!--HONumber=Nov16_HO2-->


