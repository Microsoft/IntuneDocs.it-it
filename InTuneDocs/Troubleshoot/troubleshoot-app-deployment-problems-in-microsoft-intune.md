---
title: Risorse che consentono di risolvere i problemi di distribuzione dell'app in Microsoft Intune | Microsoft Intune
description: Questo argomento consente di risolvere i problemi di distribuzione dell'app in Microsoft Intune.
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa96cf3a1909e3ea2187a3beb0aede3228894504
ms.openlocfilehash: 9f4b91bd523c82665bcac54902b2e8cc9c72ef75


---

# Risorse che consentono di risolvere i problemi di distribuzione dell'app in Microsoft Intune
Se si verificano problemi durante la distribuzione e la gestione di app con Intune, iniziare da qui. Questo argomento descrive alcuni problemi comuni e le relative soluzioni.

## Problemi comuni relativi alla distribuzione delle app

### Le informazioni di Contatta l'IT non sono presenti nel portale aziendale

1.  Nella console di amministrazione di Intune fare clic su **Amministrazione** &gt; **Portale aziendale**.

2.  Impostare i dettagli di **Contatta l'IT** .

### Se non sono visualizzate app specifiche nell'elenco

1.  Verificare di stare controllando l'elenco delle app di un utente o un dispositivo a cui è stata distribuita l'app.

2.  Verificare che il dispositivo soddisfi i requisiti per l'app.

### Se viene visualizzato un errore durante il download di un'app

1.  Verificare che non siano in esecuzione download simultanei per ogni utente. Ogni utente può scaricare un'app alla volta.

2.  Assicurarsi che non vi siano troppi download simultanei per ogni account. Attendere qualche minuto e riprovare.

3.  Se si riceve un messaggio nativo di iOS che afferma che non è possibile eseguire l'installazione, che l'installazione è stata annullata o che è necessario riprovare, ciò può essere causato da una condizione di traffico elevato. Attendere qualche minuto e riprovare.

4.  Se l'indicatore di stato del download dell'app per iOS indica che l'operazione è completata ma l'installazione non riesce, è possibile che l'errore sia nei file dell'app specificati.


### Se l'app è bloccata sullo stato "in corso" durante il caricamento

1.  Durante il caricamento di un'app, vengono aggiunti prima i metadati, seguiti dal pacchetto dell'app. Una volta caricati i metadati, l'app verrà visualizzata con stato "in corso". Se l'app rimane "in corso" per un periodo insolitamente lungo, eliminare l'app e caricarla di nuovo.

2.  Assicurarsi di non gestire la distribuzione dell'app mentre lo stato è "in corso".

### Se si verifica un errore durante l'installazione di un'app per iOS

1.  Assicurarsi che il firewall dell'organizzazione consenta l'accesso ai siti Web di provisioning e certificazione Apple.

2.  Per altre informazioni, consultare la documentazione per sviluppatori di Apple.

### Se le app gestite non inviano informazioni sullo stato di installazione

Lo stato di installazione non viene raccolto per le installazioni delle app gestite prima dell'aggiornamento del servizio Microsoft Intune di novembre 2014. Per i dispositivi con app gestite installate prima di questo aggiornamento del servizio aggiornare ogni distribuzione dell'app associata con l'azione di distribuzione appropriata, ad esempio **Installazione disponibile**. Ogni dispositivo aggiornerà l'app durante il controllo automatico per le app disponibili. Per altre informazioni, vedere [Update apps using Microsoft Intune](/intune/deploy-use/update-apps-using-microsoft-intune) (Aggiornare le app con Microsoft Intune).

## <a name="BKMK_SoftDistErrorCodes"></a>Codici di errore di distribuzione dell'app
Nella tabella seguente sono elencati gli errori più comuni che possono verificarsi durante la distribuzione dell'app Intune, oltre alle cause più probabili e alle possibili soluzioni.

|Codice errore|Possibile problema|Soluzione suggerita|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (errore del client)|Per installare questa app, è necessario disporre di un sistema abilitato per il sideload.|Assicurarsi che il pacchetto dell'app sia firmato con una firma attendibile e installato in un dispositivo aggiunto al dominio per il quale è abilitato il criterio AllowAllTrustedApps oppure in un dispositivo che dispone di una licenza per la funzionalità di sideload di Windows e per il quale è abilitato il criterio AllowAllTrustedApps (applicato quando si registra un dispositivo Windows RT).|
|0x80073CF0|Non è stato possibile aprire il pacchetto.|Cause possibili:<br /><br />-   Il pacchetto non è firmato.<br />-   Il nome dell'autore non corrisponde al soggetto del certificato di firma.<br /><br />Per altre informazioni, consultare il registro eventi di AppxPackagingOM.|
|0x80073CF3|Non è stato possibile completare la convalida dell'aggiornamento, delle dipendenze o dei conflitti per il pacchetto|Cause possibili:<br /><br />-   Il pacchetto in arrivo è in conflitto con un pacchetto installato.<br />-   Non è possibile trovare una dipendenza pacchetto specificata.<br />-   Il pacchetto non supporta l'architettura del processore corretta.<br /><br />Per altre informazioni, consultare il registro eventi di AppXDeployment-Server.|
|0x80073CFB|Il pacchetto fornito è già installato, pertanto la reinstallazione del pacchetto è stata bloccata|Questo errore può verificarsi se si installa un pacchetto che non è identico al pacchetto già installato. Verificare che anche la firma digitale faccia parte del pacchetto. Quando un pacchetto viene ricompilato o firmato di nuovo, nel confronto bit per bit tale pacchetto non è più identico a quello installato in precedenza. Per questo problema sono disponibili due soluzioni:<br /><br />-   Incrementare il numero di versione dell'app, quindi ricompilare e firmare nuovamente il pacchetto.<br />-   Rimuovere il pacchetto precedente per ogni utente del sistema prima di installare quello nuovo.|
|0x87D1041C|L'installazione dell'applicazione è stata completata ma non viene rilevata l'applicazione.|- L'app è stata distribuita da Intune e successivamente disinstallata (possibilmente dall'utente finale). Chiedere all'utente di reinstallare l'app dal portale aziendale. Le app necessarie verranno reinstallate automaticamente al successivo accesso del dispositivo.|

### Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Come ottenere supporto per Microsoft Intune).



<!--HONumber=Aug16_HO5-->


