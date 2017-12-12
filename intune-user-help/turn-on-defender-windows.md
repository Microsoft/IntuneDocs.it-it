---
title: Abilitare Windows Defender | Microsoft Docs
description: Informazioni su come abilitare Windows Defender per accedere alle risorse aziendali.
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/08/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d16dd2de-3ed5-474f-a04b-36dcd350162c
searchScope: User help
ROBOTS: 
ms.reviewer: shburbid
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: d2a7cd5cc4c201a73570f73892563463cb0bdcc7
ms.sourcegitcommit: f2f147a1177d1cf5bbc8001701eb8f44dd833b7d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="turn-on-windows-defender-to-access-company-resources"></a>Abilitare Windows Defender per accedere alle risorse aziendali

L'azienda o l'istituto di istruzione vuole assicurarsi che i dispositivi che accedono alle proprie risorse siano protetti. Esistono modi diversi, tra cui [Windows Defender](https://www.microsoft.com/safety/pc-security/windows-defender.aspx), una tecnologia di protezione integrata di Windows che difende da software dannoso.

È possibile che sia necessario modificare alcune impostazioni di Windows Defender per risolvere i problemi di accesso. Per eseguire questa procedura può essere necessario accedere a punti diversi del computer.

## <a name="turn-on-windows-defender"></a>Abilitare Windows Defender

1. Aprire **Pannello di controllo** da **Start**.
2. Aprire **Strumenti di amministrazione** > **Modifica Criteri di gruppo**. Si aprirà l'**Editor Criteri di gruppo locali** in una nuova finestra.
3. Aprire **Configurazione computer** > **Modelli amministrativi** > **Componenti di Windows** > **Windows Defender Antivirus**. L'impostazione **Disabilita Windows Defender Antivirus** si trova sotto le cartelle di altre impostazioni. 
4. Aprire **Disabilita Windows Defender Antivirus** e verificare che sia impostata l'opzione **Disabilitato** o **Non configurato**.

## <a name="turn-on-real-time-protection"></a>Abilitare la protezione in tempo reale

Verificare che la protezione in tempo reale sia abilitata selezionando **Start** e cercando **Windows Defender Security Center**. Selezionare **Impostazioni di Protezione da virus e minacce** e verificare che sia **Protezione in tempo reale** che **Protezione fornita dal cloud** siano su **Attivato**. Se queste opzioni non sono visualizzate, precedere come segue per abilitarle:

1. Aprire **Pannello di controllo** da **Start**.
2. Aprire **Strumenti di amministrazione** > **Modifica Criteri di gruppo**. Si aprirà l'**Editor Criteri di gruppo locali** in una nuova finestra.
3. Aprire **Configurazione computer** > **Modelli amministrativi** > **Componenti di Windows** > **Windows Defender Security Center** > **Protezione da virus e minacce**.
4. Aprire l'impostazione **Protezione da virus e minacce** e impostarla su **Disattivata**.

## <a name="update-your-antivirus-definitions"></a>Aggiornare le definizioni di antivirus

Verificare che le definizioni di antivirus siano aggiornate selezionando **Start** e cercando **Windows Defender Security Center**. Selezionare **Aggiornamenti della protezione** e **Verifica se sono disponibili aggiornamenti:** per assicurarsi che il dispositivo abbia una protezione aggiornata da virus. Se questa opzione non viene visualizzata, seguire la procedura in [Abilitare la protezione in tempo reale](turn-on-defender-windows.md#turn-on-real-time-protection)

Serve ancora assistenza? Contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
