---
title: Risolvere i problemi di Endpoint Protection in Intune - Azure | Microsoft Docs
description: Risolvere i problemi relativi all'uso di Microsoft Intune Endpoint Protection.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1de1722aa635367dac4b586e1333aed163156a83
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836677"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Risoluzione dei problemi di Endpoint Protection in Intune

Usare queste informazioni per la risoluzione dei problemi che si verificano durante l'uso di Endpoint Protection. È anche possibile [esaminare i registri eventi e i codici di errore per risolvere i problemi relativi a Windows Defender AV](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

Se queste informazioni non risultano utili, è anche possibile [richiedere supporto per Microsoft Intune](get-support.md).

### <a name="error-messages"></a>Messaggi di errore
Questa sezione descrive le cause e le soluzioni potenziali per gli errori e gli avvisi seguenti.

|Stato|Possibili cause|Possibili soluzioni|
|---------------|--------------------|-----------------------|
|**Motore Endpoint Protection non disponibile**|Il motore di Endpoint Protection di Intune è danneggiato o è stato eliminato.|Se il motore di Endpoint Protection di Intune è danneggiato, è possibile aggiornare o reinstallare il software.<br /><br />Per forzare un aggiornamento immediato, scegliere **Aggiorna** nel software client di Endpoint Protection (disponibile nella barra delle applicazioni dei computer gestiti).<br /><br />Se il motore non può essere aggiornato, è necessario reinstallare il motore Endpoint Protection.<br /><br />Nel Pannello di controllo del computer gestito trovare l'**agente Microsoft Intune Endpoint Protection** nell'elenco dei programmi installati e disinstallare l'applicazione.<br /><br />Durante la successiva sincronizzazione degli aggiornamenti, il programma mancante verrà rilevato dallo strumento Gestione aggiornamenti di Microsoft Online Management e sarà reinstallato al momento dell'installazione pianificata.|
|**Endpoint Protection disabilitato**|Endpoint Protection di Intune è stato disabilitato da un amministratore tramite un profilo di configurazione o da un utente in un computer gestito.|Abilitare Endpoint Protection. Vedere [Aggiungere le impostazioni di Endpoint Protection in Intune](endpoint-protection-configure.md) oppure [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows).|
|**Protezione in tempo reale disabilitata**|La protezione in tempo reale è stata disabilitata da un amministratore tramite un profilo o da un utente in un computer gestito.|Abilitare Endpoint Protection. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune oppure [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows). |
|**Analisi dei download disabilitata**|L'analisi dei download è stata disabilitata da un amministratore usando un profilo o da un utente in un computer gestito.|Abilitare l'analisi. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune oppure [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows). |
|**Monitoraggio dell'attività di file e programmi disabilitato**|Il monitoraggio dell'attività di programmi e file è stato disabilitato da un amministratore usando un profilo o da un utente in un computer gestito.|Abilitare l'attività di file e programmi. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune oppure [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows). |
|**Monitoraggio del comportamento disabilitato**|Il monitoraggio del comportamento è stato disabilitato da un amministratore usando un profilo o da un utente in un computer gestito.|Abilitare il monitoraggio del comportamento. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune oppure [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows). |
|**Analisi degli script disabilitata**|L'analisi degli script è stata disabilitata da un amministratore usando un profilo oppure da un utente in un computer gestito.|Abilitare l'analisi degli script. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune oppure [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows). |
|**Network Inspection System disabilitato**|Network Inspection System è stato disabilitato da un amministratore usando un profilo o da un utente in un computer gestito.|Abilitare Network Inspection System. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus) in Intune oppure [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows). |
|**Definizioni malware scadute**|Il computer potrebbe essere stato disconnesso da Internet per un periodo di tempo prolungato ed è possibile che le relative definizioni malware non siano state ancora aggiornate. Questo stato viene visualizzato quando le definizioni malware nel computer non vengono aggiornate da almeno 14 giorni.|Se le definizioni malware non sono aggiornate, è possibile aggiornare le definizioni usando [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**Analisi completa scaduta**|L'ultima analisi completa è stata eseguita 14 giorni fa. Il problema può essere causato da un riavvio del computer durante un'analisi completa.|In presenza di un'analisi completa scaduta, è possibile eseguire un'analisi completa occasionale oppure pianificare analisi complete periodiche. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus). |
|**Analisi veloce scaduta**|L'ultima analisi veloce è stata eseguita 14 giorni fa. Il problema può essere causato da un riavvio durante un'analisi veloce.|In presenza di un'analisi veloce scaduta, è possibile eseguire un'analisi veloce occasionale oppure pianificare analisi veloci periodiche. Vedere [Windows Defender Antivirus](device-restrictions-windows-10.md#windows-defender-antivirus).|
|**È in esecuzione un'altra applicazione Endpoint Protection**|È in esecuzione un'altra applicazione Endpoint Protection e il computer è integro.|Per impostazione predefinita, se è installata un'altra applicazione di protezione degli endpoint e Intune rileva tale applicazione, il dispositivo potrebbe diventare instabile.|

### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni non risultano utili, è anche possibile [richiedere supporto per Microsoft Intune](get-support.md).
