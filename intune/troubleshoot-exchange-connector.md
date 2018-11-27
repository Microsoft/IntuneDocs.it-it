---
title: Risolvere i problemi di Exchange Connector
description: Risoluzione dei problemi correlati a Intune On-Premises Exchange Connector.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 6/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 85b4764ef5797ad592744e3c519f82f3f1cdd1bb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190054"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Risolvere i problemi di Intune On-Premises Exchange Connector

Questo argomento descrive come risolvere i problemi correlati a Intune On-Premises Exchange Connector.

## <a name="steps-for-checking-the-connector-configuration"></a>Procedura per controllare la configurazione del connettore 

Controllare la [configurazione di Intune On-Premises Exchange Connector](exchange-connector-install.md) per assicurarsi che il connettore sia configurato correttamente. Di seguito sono descritti alcuni problemi comuni. Dopo avere apportato eventuali correzioni, verificare se il problema è risolto.

 - Nella finestra di dialogo di Microsoft Intune Exchange Connector, assicurarsi di avere specificato un account utente con le autorizzazioni appropriate per eseguire i [cmdlet necessari di Windows PowerShell Exchange](exchange-connector-install.md#exchange-cmdlet-requirements).
- Abilitare le notifiche e specificare un account di notifica.
 - Quando si configura Exchange Connector, specificare un server Accesso client (CAS) che sia più vicino possibile al server che ospita Exchange Connector. La latenza di comunicazione tra il server Accesso client ed Exchange Connector potrebbe determinare ritardi nell'individuazione dei dispositivi, specialmente quando si usa Exchange Online dedicato.
 - Un utente con un dispositivo appena registrato potrebbe riscontrare ritardi e ottenere l'accesso solo dopo il completamento della sincronizzazione di Exchange Connector e il server Accesso client di Exchange. Una sincronizzazione completa viene eseguita una volta al giorno, mentre una sincronizzazione delta (rapida) viene eseguita più volte al giorno.  È possibile [forzare manualmente una sincronizzazione rapida o una sincronizzazione completa](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync) per ridurre al minimo i ritardi.
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Dispositivo Exchange ActiveSync non individuato da Exchange
[Monitorare l'attività di Exchange Connector](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support) per verificare se Exchange Connector esegue la sincronizzazione con il server Exchange. Se è stata completata una sincronizzazione completa o una sincronizzazione rapida dopo l'aggiunta del dispositivo, è possibile verificare se sussistono altri problemi possibili, elencati di seguito. Se non è stata eseguita alcuna sincronizzazione, raccogliere i log di sincronizzazione e allegarli a una richiesta di supporto.

 - Assicurarsi che gli utenti abbiano una licenza Intune. In caso contrario, Exchange Connector non sarà in grado di individuare i loro dispositivi.
 - Se l'indirizzo SMTP primario di un utente è diverso dal relativo UPN in Azure Active Directory (Azure AD), Exchange Connector non sarà in grado di individuare alcun dispositivo per tale utente. Risolvere l'indirizzo SMTP primario per risolvere il problema.
 - Se l'ambiente include server di cassette postali sia Exchange 2010 che Exchange 2013, si consiglia di associare Exchange Connector a un server Accesso client di Exchange 2013. In caso contrario, se Exchange Connector è configurato per comunicare con un'autorità di certificazione di Exchange 2010, Exchange Connector non individuerà i dispositivi degli utenti Exchange 2013. 
- Per gli ambienti Exchange Online dedicato, è necessario puntare Exchange Connector a un server Accesso client di Exchange 2013 (non Exchange 2010) nell'ambiente dedicato durante l'installazione iniziale, in modo che il connettore comunichi solo con il server Accesso client quando si eseguono i cmdlet di PowerShell.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Uso di Powershell per ottenere maggiori dati sui problemi relativi a Exchange Connector
- Per visualizzare l'elenco di tutti i dispositivi mobili relativi a una cassetta postale, usare il cmdlet Get-ActiveSyncDeviceStatistics -mailbox mbx
- Per visualizzare l'elenco di indirizzi SMTP relativi a una cassetta postale, usare Get-Mailbox -Identity user | select emailaddresses | fl
- Per ottenere informazioni dettagliate sullo stato di accesso di un dispositivo, usare Get-CASMailbox <upn> | fl

### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni non risultano utili, è anche possibile [ottenere supporto per Microsoft Intune](get-support.md).
