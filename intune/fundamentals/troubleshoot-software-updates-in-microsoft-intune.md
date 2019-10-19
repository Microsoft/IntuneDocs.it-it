---
title: Risoluzione dei problemi degli aggiornamenti software in Microsoft Intune - Azure | Microsoft Docs
description: Risolvere i problemi degli aggiornamenti software in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ad8d904f72df169eea136c625a2f44d645cafbc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509764"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Risolvere i problemi degli aggiornamenti software in Microsoft Intune

Agevolare la risoluzione dei problemi degli aggiornamenti software in Microsoft Intune. Per un elenco dei codici di errore e le relative descrizioni, vedere [Software update agent error codes in Microsoft Intune](../protect/software-update-agent-error-codes.md) (Codici di errore dell'agente di aggiornamento software in Microsoft Intune).

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>I dispositivi Windows 7 con molti aggiornamenti sostituiti non inviano più segnalazioni a Intune

I client Microsoft Intune potrebbero riscontrare uno o più dei sintomi seguenti:

- I dispositivi interrompono improvvisamente le segnalazioni a Intune.  
- I dispositivi registrano un uso elevato della CPU.
- L'installazione delle applicazioni tramite Intune è lenta.
- In Microsoft Intune Center è visualizzato l'errore seguente: `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- Nella console di amministrazione di Intune > Gruppi > Tutti i dispositivi > Stato è visualizzato il messaggio seguente: `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

Questo problema può verificarsi se gli aggiornamenti sostituiti (ossia aggiornamenti sostituiti da un altro aggiornamento) non vengono rifiutati da diverso tempo. Durante determinati processi, come l'installazione di un'applicazione, Windows controlla tutti gli aggiornamenti sostituiti in sequenza in modo che gli aggiornamenti e i relativi successori vengano mappati correttamente. Se l'elenco degli aggiornamenti sostituiti aumenta in modo eccessivo, questa attività di controllo può determinare un uso elevato della CPU a causa del carico di elaborazione e del tempo necessario. Questo problema interessa principalmente i dispositivi Windows 7 per via dell'alto numero di aggiornamenti sostituiti disponibili per questo sistema operativo. I sistemi operativi più recenti potrebbero non disporre di altrettanti aggiornamenti sostituiti e, pertanto, non essere soggetti al problema.

**Risoluzione**

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selezionare **Aggiornamenti software**.
3. Rifiutare tutti gli aggiornamenti sostituiti applicabili a Windows 7 o alle applicazioni, come Microsoft Office, che sono state installate nei client interessati.
4. Riavviare i client.

Se si esegue Windows 7, verificare che sia installato l'aggiornamento seguente:[3050265 Windows Update Client for Windows 7: June 2015](https://support.microsoft.com/kb/3050265) (3050265 Client di Windows Update per Windows 7: giugno 2015).

## <a name="next-steps"></a>Passaggi successivi

Ottenere [supporto da Microsoft](get-support.md) o usare i [forum della community](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).