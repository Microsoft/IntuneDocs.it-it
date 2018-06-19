---
title: Risorse che consentono di risolvere i problemi di distribuzione dell'app
description: Questo argomento consente di risolvere i problemi di distribuzione dell'app in Microsoft Intune.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 09/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: df00293335b23d8924887bdd7b70838f9bddfb65
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31014028"
---
# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Risorse che consentono di risolvere i problemi di distribuzione dell'app in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Se si verificano problemi durante la distribuzione e la gestione di app con Intune, iniziare da qui. Questo argomento descrive alcuni problemi comuni e le relative soluzioni.

## <a name="common-app-deployment-error-codes"></a>Codici di errore di distribuzione dell'app comuni

|Codice errore|Possibile problema|Soluzione suggerita|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (errore del client)|Per installare questa app, è necessario disporre di un sistema abilitato per il sideload.|Assicurarsi che il pacchetto dell'app sia firmato con una firma attendibile e installato in un dispositivo aggiunto al dominio per il quale è abilitato il criterio AllowAllTrustedApps oppure in un dispositivo che dispone di una licenza per la funzionalità di sideload di Windows e per il quale è abilitato il criterio AllowAllTrustedApps.|
|0x80073CF0|Non è stato possibile aprire il pacchetto.|Cause possibili:<br /><br />-   Il pacchetto non è firmato.<br />-   Il nome dell'autore non corrisponde al soggetto del certificato di firma.<br /><br />Per altre informazioni, consultare il registro eventi di AppxPackagingOM.|
|0x80073CF3|Non è stato possibile completare la convalida dell'aggiornamento, delle dipendenze o dei conflitti per il pacchetto|Cause possibili:<br /><br />-   Il pacchetto in arrivo è in conflitto con un pacchetto installato.<br />-   Non è possibile trovare una dipendenza pacchetto specificata.<br />-   Il pacchetto non supporta l'architettura del processore corretta.<br /><br />Per altre informazioni, consultare il registro eventi di AppXDeployment-Server.|
|0x80073CFB|Il pacchetto fornito è già installato, pertanto la reinstallazione del pacchetto è stata bloccata|Questo errore può verificarsi se si installa un pacchetto che non è identico al pacchetto già installato. Verificare che anche la firma digitale faccia parte del pacchetto. Quando un pacchetto viene ricompilato o firmato di nuovo, nel confronto bit per bit tale pacchetto non è più identico a quello installato in precedenza. Per questo problema sono disponibili due soluzioni:<br /><br />-   Incrementare il numero di versione dell'app, quindi ricompilare e firmare nuovamente il pacchetto.<br />-   Rimuovere il pacchetto precedente per ogni utente del sistema prima di installare quello nuovo.|
|0x87D1041C|L'installazione dell'applicazione è stata completata ma non viene rilevata l'applicazione.|- L'app è stata distribuita da Intune e successivamente disinstallata (possibilmente dall'utente finale). Chiedere all'utente di reinstallare l'app dal portale aziendale. Le app necessarie verranno reinstallate automaticamente al successivo accesso del dispositivo.|

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Risoluzione dei problemi delle app da Microsoft Store

Le informazioni nell'argomento [Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (Risoluzione dei problemi relativi a pacchetti, distribuzioni e query delle app di Microsoft Store) consentono di risolvere i problemi comuni riscontrabili durante l'installazione di app da Microsoft Store, tramite Intune o altri mezzi.

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>Risoluzione dei problemi relativi alla distribuzione di app a PC gestiti dal client software di Intune
Per risolvere i problemi relativi alla distribuzione di app a PC gestiti dal client software di Intune, è possibile esaminare i file di log seguenti:
- %ProgramFiles%\Microsoft\OnlineManagement\Logs folder
- %ProgramFiles%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

Inoltre, se è necessario aprire un caso di supporto per Intune, può essere utile anche inviare questi log a Microsoft.


### <a name="next-steps"></a>Passaggi successivi
Se queste informazioni per la risoluzione dei problemi non sono utili, contattare il supporto Microsoft come descritto in [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Come ottenere supporto per Microsoft Intune).
