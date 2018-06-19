---
title: Usare le app gestite nel dispositivo Android | Documentazione Microsoft
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/24/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ed10a62c-b026-4ad3-ac41-641933522df2
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ebb79bc3405e9ea0dd38c24b86a4c9020760c895
ms.sourcegitcommit: 2773f388f50654366197a95a6838306f70fc18b8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
ms.locfileid: "31442476"
---
# <a name="use-managed-apps-on-your-android-device"></a>Usare le app gestite nel dispositivo Android

Le app gestite sono app che il supporto tecnico dell'azienda può configurare per proteggere i dati aziendali ai quali è possibile accedere dall'app stessa. Quando si accede ai dati aziendali da un'app gestita in un dispositivo Android, è possibile notare che il funzionamento dell'app è leggermente diverso rispetto a quello previsto. Ad esempio, potrebbero non essere consentite le operazioni di copia e incolla dei dati aziendali protetti oppure il salvataggio dei dati in determinati percorsi.

Diverse app gestite possono anche interagire tra loro nel dispositivo per consentire di eseguire le attività giornaliere mantenendo protetti i dati aziendali. Ad esempio, se si apre un file aziendale in un'app gestita che richiede un'altra app gestita per visualizzare il file, questa seconda app viene aperta automaticamente. Se un'app necessaria non è disponibile, alcune azioni, come l'apertura di un documento o l'accesso a un collegamento Web in un documento gestito, potrebbero non essere disponibili.

Quando si accede ai dati aziendali in un'app gestita, viene visualizzato un messaggio simile a quello riportato di seguito, che indica che l'app che si sta aprendo è gestita.

![Aprire-gestite-app-messaggio](./media/managed-apps-message.png)

## <a name="how-do-i-get-managed-apps"></a>Come si ottengono le app gestite?
Le app gestite possono essere installate in due modi:

-   Quando il dispositivo viene registrato in Microsoft Intune, è possibile installare l'app dall'app Portale aziendale o dal sito Web del portale aziendale oppure l'installazione nel dispositivo può essere eseguita dal supporto tecnico dell'azienda. Per altre informazioni sulla registrazione, vedere [Registrare il dispositivo in Intune](enroll-your-device-in-Intune-android.md).

-   L'app viene installata da Play Store e quindi l'utente accede con l'account utente aziendale gestito da Intune.

## <a name="what-can-my-company-support-manage-in-an-app"></a>Che cosa può gestire il supporto tecnico dell'azienda in un'app?
Di seguito sono riportati alcuni esempi di opzioni che il supporto tecnico dell'azienda può gestire in un'app e che possono influire sulle interazioni con i dati aziendali nel dispositivo:

-   Accesso a specifici siti Web

-   Trasferimenti di dati tra applicazioni

-   Salvataggio di file

-   Operazioni di copia e incolla

-   Requisiti di accesso PIN

-   Account di accesso con le credenziali aziendali

-   Possibilità di eseguire il backup nel cloud

-   Possibilità di acquisire screenshot

-   Requisiti di crittografia dati

Di seguito sono riportate alcune app comuni che il reparto IT potrebbe gestire:

-   Intune Managed Browser

-   Visualizzatore Microsoft Azure Information Protection

-   Microsoft Word, Excel e PowerPoint

Per altre informazioni sulle applicazioni gestite nel dispositivo, contattare il supporto tecnico dell'azienda. Per informazioni sul contatto vedere il [sito Web del portale aziendale](https://portal.manage.microsoft.com#HelpDeskDialog).
