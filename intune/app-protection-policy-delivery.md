---
title: Informazioni sui tempi e sul recapito dei criteri di protezione delle app
titleSuffix: Microsoft Intune
description: Informazioni sulle diverse finestre di distribuzione per i criteri di protezione delle app, per comprendere quando vengono applicate modifiche nei dispositivi degli utenti finali.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 14b4af7145e09e1af3d2a6d3a2fd3ef17319be35
ms.sourcegitcommit: 1b7ee2164ac9490df4efa83c5479344622c181b5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/08/2019
ms.locfileid: "67649015"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>Informazioni sui tempi di recapito dei criteri di protezione delle app

Informazioni sulle diverse finestre di distribuzione per i criteri di protezione delle app, per comprendere quando vengono applicate modifiche nei dispositivi degli utenti finali.

## <a name="delivery-timing-summary"></a>Riepilogo dei tempi di recapito

Il recapito dei criteri di protezione delle applicazioni varia a seconda dello stato della licenza e della registrazione del servizio Intune per gli utenti.  

|    Stato utente    |    Comportamento di protezione delle app     |    Intervallo tra tentativi (vedere la nota)    |    Perché si verifica questo comportamento?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    Onboarding del tenant non eseguito    |    Viene atteso il successivo intervallo tra tentativi.  La protezione delle app non è attiva per l'utente.    |    24 ore    |    Si verifica quando non è stato configurato il tenant per Intune.    |
|    Utente senza licenza     |    Viene atteso il successivo intervallo tra tentativi.  La protezione delle app non è attiva per l'utente.     |    12 ore. Nei dispositivi Android, tuttavia, questo intervallo richiede Intune App SDK versione 5.6.0 o successiva. In caso contrario, per i dispositivi Android l'intervallo è 24 ore.   |    Si verifica quando non è stata concessa all'utente la licenza per Intune.    |
|    Criteri di protezione delle app non assegnati all'utente    |    Viene atteso il successivo intervallo tra tentativi.  La protezione delle app non è attiva per l'utente.    |    12 ore        |    Si verifica quando all'utente non sono state assegnate impostazioni delle app.    |
|    Registrazione del software MAM di Intune per l'utente eseguita correttamente    |    La protezione delle app viene applicata in base ai criteri di protezione delle app.    Gli aggiornamenti vengono eseguiti in base all'intervallo tra tentativi    |    Valore definito dal servizio Intune in base al carico utente.    In genere, 30 minuti.     |    Si verifica quando è stata eseguita correttamente la registrazione dell'utente nel servizio Intune per la configurazione MAM.    |

> [!NOTE]
> Gli intervalli tra tentativi possono richiedere l'uso attivo dell'app, ovvero che l'app venga avviata e sia in uso.  Se l'intervallo tra tentativi è di 24 ore e l'utente attende 48 ore per avviare l'app, il client di protezione dell'applicazione eseguirà un nuovo tentativo dopo 48 ore.

## <a name="handling-network-connectivity-issues"></a>Gestione dei problemi di connettività di rete

Quando la registrazione di un utente non riesce a causa di problemi di connettività di rete, viene usato un intervallo tra tentativi accelerato.  Il client di protezione dell'applicazione eseguirà i nuovi tentativi a intervalli sempre più lunghi, più fino a quando l'intervallo non raggiunge 60 minuti o non viene stabilita una connessione.  Il client continuerà quindi a ripetere i tentativi a intervalli di 60 minuti fino a quando non viene stabilita una connessione. Il client tornerà quindi all'intervallo tra tentativi standard basato sullo stato utente.

## <a name="next-steps"></a>Passaggi successivi

[Assegnare licenze agli utenti in modo che possano registrare i dispositivi in Intune](licenses-assign.md)

