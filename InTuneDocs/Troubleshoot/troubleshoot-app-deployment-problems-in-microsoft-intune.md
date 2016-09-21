---
title: Risorse che consentono di risolvere i problemi di distribuzione dell'app in Microsoft Intune | Microsoft Intune
description: Questo argomento consente di risolvere i problemi di distribuzione dell'app in Microsoft Intune.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a5256d4decfcd14de2d50a32a0906b6894639010
ms.openlocfilehash: 552514971a64b16f88a7d83a0f7d66a0c00b61b0


---

# Risorse che consentono di risolvere i problemi di distribuzione dell'app in Microsoft Intune
Se si verificano problemi durante la distribuzione e la gestione di app con Intune, iniziare da qui. Questo argomento descrive alcuni problemi comuni e le relative soluzioni.

## Codici di errore di distribuzione dell'app comuni

|Codice errore|Possibile problema|Soluzione suggerita|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (errore del client)|Per installare questa app, è necessario disporre di un sistema abilitato per il sideload.|Assicurarsi che il pacchetto dell'app sia firmato con una firma attendibile e installato in un dispositivo aggiunto al dominio per il quale è abilitato il criterio AllowAllTrustedApps oppure in un dispositivo che dispone di una licenza per la funzionalità di sideload di Windows e per il quale è abilitato il criterio AllowAllTrustedApps (applicato quando si registra un dispositivo Windows RT).|
|0x80073CF0|Non è stato possibile aprire il pacchetto.|Cause possibili:<br /><br />-   Il pacchetto non è firmato.<br />-   Il nome dell'autore non corrisponde al soggetto del certificato di firma.<br /><br />Per altre informazioni, consultare il registro eventi di AppxPackagingOM.|
|0x80073CF3|Non è stato possibile completare la convalida dell'aggiornamento, delle dipendenze o dei conflitti per il pacchetto|Cause possibili:<br /><br />-   Il pacchetto in arrivo è in conflitto con un pacchetto installato.<br />-   Non è possibile trovare una dipendenza pacchetto specificata.<br />-   Il pacchetto non supporta l'architettura del processore corretta.<br /><br />Per altre informazioni, consultare il registro eventi di AppXDeployment-Server.|
|0x80073CFB|Il pacchetto fornito è già installato, pertanto la reinstallazione del pacchetto è stata bloccata|Questo errore può verificarsi se si installa un pacchetto che non è identico al pacchetto già installato. Verificare che anche la firma digitale faccia parte del pacchetto. Quando un pacchetto viene ricompilato o firmato di nuovo, nel confronto bit per bit tale pacchetto non è più identico a quello installato in precedenza. Per questo problema sono disponibili due soluzioni:<br /><br />-   Incrementare il numero di versione dell'app, quindi ricompilare e firmare nuovamente il pacchetto.<br />-   Rimuovere il pacchetto precedente per ogni utente del sistema prima di installare quello nuovo.|
|0x87D1041C|L'installazione dell'applicazione è stata completata ma non viene rilevata l'applicazione.|- L'app è stata distribuita da Intune e successivamente disinstallata (possibilmente dall'utente finale). Chiedere all'utente di reinstallare l'app dal portale aziendale. Le app necessarie verranno reinstallate automaticamente al successivo accesso del dispositivo.|

### Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Come ottenere supporto per Microsoft Intune).



<!--HONumber=Sep16_HO1-->


