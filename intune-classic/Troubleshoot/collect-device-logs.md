---
title: Raccogliere i log dei dispositivi
description: Informazioni su come raccogliere registri da dispositivi gestiti.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d97fb610-9d88-40e5-bb06-447eec533630
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f07947a4064cbd6852edb93ea8d6d17e2c6d9101
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025570"
---
# <a name="device-logs"></a>Log dei dispositivi

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Nell'ambito delle attività di risoluzione dei problemi può essere necessario raccogliere i log dei dispositivi degli utenti. Le istruzioni per la raccolta dei log sono descritte qui. In genere è necessario accedere ai dispositivi per ottenere i log o chiedere agli utenti di raccoglierli e inviarli.

### <a name="android-logs"></a>Log di Android
I log di Android si trovano in *<Android Device>\Phone\Android\data\com.microsoft.windowsintune.companyportal\files*.

Talvolta i file non vengono visualizzati, specialmente nei dispositivi Android più recenti. In questo caso, chiedere agli utenti finali di aprire l'app Portale aziendale per Android. Gli utenti devono quindi scegliere **Impostazioni**>**Copia log** e riavviare il dispositivo.

Per altre informazioni su come gli utenti possono inviare i log di dati, vedere gli articoli seguenti:

- [Use Verbose Logging to help your IT admin fix device issues](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) (Usare la registrazione dettagliata per aiutare l'amministratore IT a risolvere i problemi dei dispositivi): descrive la procedura per attivare la registrazione dettagliata, consentendo l'invio automatico di tutti i log di dati degli utenti all'amministratore. La registrazione dettagliata è attivata per impostazione predefinita.

- [Inviare i log dei dati di diagnostica di Android all'amministratore IT tramite posta elettronica](/intune-user-help/send-logs-to-your-it-admin-by-email-android)

- [Inviare i log dei dati di diagnostica all'amministratore IT tramite un cavo USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)

### <a name="ios-logs"></a>Log iOS

L'utente può inviare gli errori di registrazione come descritto in [Send iOS enrollment errors to your IT administrator](/intune-user-help/send-errors-to-your-it-admin-ios) (Inviare gli errori di registrazione iOS all'amministratore IT).

Gli utenti possono inviare i log del dispositivo, come descritto in [Send iOS Device Logs](/intune-user-help/send-logs-to-microsoft-ios) (Inviare i log del dispositivo iOS).

### <a name="mac-os-x-logs"></a>Log di Mac OS X

1. Aprire l'app **Console**.
2. In **FILE** scegliere **system.log**.
3. Nella barra dei menu nella parte superiore scegliere **File** > **Salva una copia con nome**. Salvare quindi il file.

### <a name="windows-phone"></a>Windows Phone

Nell'app Portale aziendale di Windows Phone l'utente deve scegliere i tre puntini (**…**) per accedere al menu e quindi deve scegliere **Invia log**. Questa opzione è disponibile sia prima che dopo l'accesso all'app Portale aziendale.

### <a name="windows"></a>Windows

Per il portale aziendale di Windows i log si trovano in *%localappdata%\Packages\Microsoft.CompanyPortal_8wekyb3d8bbwe\LocalState*.
