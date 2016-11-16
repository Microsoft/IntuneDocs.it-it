---
title: Risolvere i problemi di Exchange Connector | Microsoft Intune
description: Risoluzione dei problemi correlati a Intune Exchange Connector.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a4f7a503417938eabb4334757dcf12a63f082fd3
ms.openlocfilehash: f6b673d05e385ddfe6ef3d3e63cf857439b164de


---

# <a name="troubleshoot-the-exchange-connector"></a>Risolvere i problemi di Exchange Connector
Questo argomento descrive come risolvere i problemi che possono essere correlati a Intune Exchange Connector.

## <a name="steps-for-checking-the-connector-configuration"></a>Procedura per verificare la configurazione di Connector 

Controllare la configurazione di Exchange Connector e quindi verificare se il problema è stato risolto.

- Assicurarsi di specificare un account di notifica durante l'installazione iniziale di Exchange Connector.
- L'account del servizio Exchange Connector deve disporre delle autorizzazioni appropriate per eseguire i cmdlet PowerShell usati da Exchange Connector.
- Quando si configura Exchange Connector, specificare un server Accesso client (CAS) che sia più vicino possibile al server che ospita Exchange Connector. La latenza di comunicazione tra il server Accesso client e Exchange Connector potrebbe determinare ritardi nell'individuazione dei dispositivi, specialmente quando si usa Office 365 dedicato.
- Tenere presente che c'è un intervallo di ritardo tra le sincronizzazioni di Exchange Connector e il server Accesso client di Exchange. Una sincronizzazione completa viene eseguita una volta al giorno, mentre una sincronizzazione delta (rapida) viene eseguita ogni due ore. È probabile che un utente con un dispositivo appena registrato possa sperimentare ritardi nell'accesso.
- 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Dispositivo Exchange ActiveSync non individuato da Exchange
Verificare se Exchange Connector esegue la sincronizzazione con il server Exchange. A tale scopo, individuare i log per stabilire se viene eseguita una sincronizzazione completa o una sincronizzazione delta. Vedere la sezione relativa ai log di Exchange Connector. Se dopo l'aggiunta del dispositivo è stata eseguita una sincronizzazione completa o una sincronizzazione delta, questa non può essere considerata la causa del problema. Se non è stata eseguita alcuna sincronizzazione, raccogliere i log di sincronizzazione e allegarli alla richiesta di supporto.

- Se un utente non dispone di una licenza Intune, Exchange Connector non sarà in grado di individuare i suoi dispositivi.
- Se l'indirizzo SMTP primario di un utente è diverso dal relativo UPN in AAD, Exchange Connector non sarà in grado di individuare alcun dispositivo per tale utente di Intune/AAD. Correggere l'indirizzo SMTP primario.
- Se il server Accesso client con cui comunica Exchange Connector durante un ciclo di individuazione è un server di Exchange 2010 e l'utente dispone di server di cassette postali Exchange 2010 e 2013, Exchange Connector non sarà in grado di individuare gli eventuali dispositivi degli utenti di Exchange 2013. Per risolvere questo problema, configurare Exchange Connector in modo che punti al server Accesso client di Exchange 2013.  Nonostante il problema riguardi principalmente le topologie di Office 365 dedicato, è consigliabile comunque puntare a un server Accesso client di Exchange 2013 in altre topologie.
- Per gli ambienti Exchange dedicato (Office 365 dedicato), è necessario puntare Exchange Connector a un server Accesso client di Exchange 2013 (non 2010) durante l'installazione iniziale. Durante l'esecuzione dei cmdlet Powershell, infatti, la comunicazione avverrà soltanto con questo server Accesso client.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Uso di Powershell per ottenere maggiori dati sui problemi relativi a Exchange Connector
- Per visualizzare l'elenco di tutti i dispositivi mobili relativi a una cassetta postale, usare il cmdlet Get-ActiveSyncDeviceStatistics -mailbox mbx.
- Per visualizzare l'elenco di indirizzi SMTP relativi a una cassetta postale, usare Get-Mailbox -Identity user | select emailaddresses | fl.
- Per ottenere informazioni dettagliate sullo stato di accesso di un dispositivo, usare Get-CASMailbox <upn> | fl.

### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [Come ottenere supporto per Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Oct16_HO4-->


