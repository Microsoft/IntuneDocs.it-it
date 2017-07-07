---
title: Usare le app gestite nel dispositivo iOS | Documentazione Microsoft
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e
searchScope: User help
ROBOTS: 
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ee43647190da705581eaa5a266db3712391e06f2
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="use-managed-apps-on-your-ios-device"></a>Usare le app gestite nel dispositivo iOS

Le app gestite sono app che l'amministratore IT può configurare per proteggere i dati aziendali ai quali è possibile accedere dall'app stessa. Quando si accede ai dati aziendali da un'app gestita in un dispositivo iOS, è possibile notare che il funzionamento dell'app è leggermente diverso rispetto a quello previsto. Ad esempio, potrebbero non essere consentite le operazioni di copia e incolla dei dati aziendali protetti oppure il salvataggio dei dati in determinati percorsi.

Diverse app gestite possono anche interagire tra loro nel dispositivo per consentire di eseguire le attività giornaliere mantenendo protetti i dati aziendali. Ad esempio, se si apre un file aziendale in un'app gestita che richiede un'altra app gestita per visualizzare il file, questa seconda app viene aperta automaticamente. Se un'app necessaria non è disponibile, alcune azioni, come l'apertura di un documento o l'accesso a un collegamento Web in un documento gestito, potrebbero non essere disponibili.

Quando si accede ai dati aziendali in un'app gestita, viene visualizzato un messaggio simile a quello riportato di seguito, che indica che l'app che si sta aprendo è gestita.

![gestite-apps-messaggio-ios](./media/managed-apps-message.png)

### <a name="how-do-i-get-managed-apps"></a>Come si ottengono le app gestite?
Le app gestite possono essere installate in due modi:

-   Quando il dispositivo viene registrato in Microsoft Intune, è possibile installare l'app dall'app Portale aziendale o dal sito Web del portale aziendale oppure l'installazione nel dispositivo può essere eseguita dall'amministratore IT. Per informazioni sulla registrazione, vedere [Registrare il dispositivo iOS in Intune](enroll-your-device-in-intune-ios.md) o [Registrare il dispositivo macOS in Intune](enroll-your-device-in-intune-macos.md).

-   L'app viene installata da App Store e quindi l'utente accede con l'account utente aziendale gestito da Intune.

### <a name="what-can-my-it-admin-manage-in-an-app"></a>Cosa può gestire l'amministratore IT in un'app?
Di seguito sono riportati alcuni esempi di opzioni che l'amministratore IT può gestire in un'app e che possono influire sulle interazioni con i dati aziendali nel dispositivo:

-   Accesso a specifici siti Web

-   Trasferimenti di dati tra applicazioni

-   Salvataggio di file

-   Operazioni di copia e incolla

-   Requisiti di accesso PIN

-   Account di accesso con le credenziali aziendali

-   Possibilità di eseguire il backup nel cloud

-   Possibilità di acquisire screenshot

-   Requisiti di crittografia dati

Per altre informazioni sulle app gestite nel dispositivo contattare l'amministratore IT. Per informazioni sul contatto vedere il [sito Web del portale aziendale](http://portal.manage.microsoft.com).
