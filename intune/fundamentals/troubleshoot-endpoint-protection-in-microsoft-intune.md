---
title: Messaggi comuni di Endpoint Protection in Microsoft Intune - Azure | Microsoft Docs
description: Descrizione dei messaggi comuni e delle possibili soluzioni durante l'utilizzo e la risoluzione dei problemi di Endpoint Protection e Microsoft Defender in Microsoft Intune.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 819586a923f5c0f3a81a6d59c4a3895898182f6b
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059166"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Problemi di Endpoint Protection e possibili soluzioni in Microsoft Intune

Questo articolo elenca e descrive le possibili cause di alcuni errori e avvisi e le relative soluzioni. Usare queste informazioni per la risoluzione dei problemi che si verificano durante l'uso di Endpoint Protection.

## <a name="microsoft-defender-error-codes"></a>Codici di errore di Microsoft Defender

Esaminare i log eventi e i codici di errore per [risolvere i problemi relativi a Antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus).

## <a name="common-intune-errors-and-possible-resolutions"></a>Errori comuni di Intune e possibili soluzioni

### <a name="endpoint-protection-engine-unavailable"></a>Motore Endpoint Protection non disponibile

**Possibile causa**: il motore di Intune Endpoint Protection è danneggiato o è stato eliminato.

**Possibili soluzioni**:

- Se Endpoint Protection è danneggiato o non viene aggiornato, aggiornare o reinstallare il programma.
- Forzare un aggiornamento immediato. Nell'applicazione client Endpoint Protection (probabilmente nella barra delle applicazioni) scegliere **Aggiorna**.
- In Pannello di controllo > Programmi selezionare **Agente di Microsoft Intune Endpoint Protection**. Disinstallare l'applicazione.
- Durante la successiva sincronizzazione degli aggiornamenti, il programma mancante verrà rilevato dallo strumento Gestione aggiornamenti di Microsoft Online Management e sarà reinstallato al momento dell'installazione pianificata.

### <a name="features-are-disabled"></a>Funzionalità disabilitate

Potrebbe essere visualizzato un messaggio che informa che alcune funzionalità sono disabilitate. Messaggi di questo tipo possono essere visualizzati se Intune Endpoint Protection o Microsoft Defender sono stati disabilitati da un amministratore tramite un profilo di configurazione oppure se è stato disabilitato da un utente finale sul dispositivo. Ecco alcun messaggi possibili:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**Possibili soluzioni**: abilitare queste funzionalità. Per istruzioni, vedere:

- [Aggiungere le impostazioni di Endpoint Protection in Intune](../protect/endpoint-protection-configure.md)
- [Microsoft Defender Antivirus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [Abilitare Windows Defender per accedere alle risorse aziendali](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>Definizioni malware scadute

Questo stato viene visualizzato quando le definizioni malware nel dispositivo non vengono aggiornate da almeno 14 giorni. Ad esempio, il messaggio potrebbe essere visualizzato se il dispositivo è disconnesso da Internet o se le definizioni malware non sono aggiornate.

**Possibili soluzioni**: se le definizioni malware non sono aggiornate, aggiornarle usando [Antivirus Microsoft Defender](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>Analisi completa scaduta o Analisi veloce scaduta

Non viene completata un'analisi completa o un'analisi veloce da 14 giorni. Questa situazione può verificarsi se il dispositivo viene riavviato durante un'analisi completa.

**Possibili soluzioni**: in presenza di un'analisi scaduta, è possibile eseguire un'analisi occasionale oppure pianificare analisi periodiche. Vedere [Microsoft Defender Antivirus](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus).

### <a name="another-endpoint-protection-application-running"></a>È in esecuzione un'altra applicazione Endpoint Protection

È in esecuzione un'altra applicazione Endpoint Protection e il dispositivo è integro.

**Possibili soluzioni**: per impostazione predefinita, se è installata un'altra applicazione Endpoint Protection e Intune rileva tale applicazione, il dispositivo potrebbe diventare instabile.

## <a name="next-steps"></a>Passaggi successivi

Ottenere [supporto da Microsoft](get-support.md) o usare i [forum della community](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
