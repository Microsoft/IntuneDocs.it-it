---
title: Mobile Threat Defense di Intune | Microsoft Docs
description: Proteggere l&quot;accesso alle risorse aziendali in base al rischio dei dispositivi.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 56cd18e1a5556178d951ec47c6e894d8fc2e6f86
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="intune-mobile-threat-defense-connectors"></a>Connettori Mobile Threat Defense di Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

I connettori Mobile Threat Defense di Intune consentono di basare i criteri di conformità e le regole di accesso condizionale sulle informazioni offerte dal fornitore della soluzione Mobile Threat Defense. Ciò consente agli amministratori IT di aggiungere un livello di protezione per le risorse aziendali, ad esempio Exchange e Sharepoint, dai rischi specifici di dispositivi mobili compromessi.

## <a name="what-problem-does-this-solve"></a>Quale problema risolve questa soluzione?

Le aziende hanno l'esigenza di proteggere i dati sensibili da minacce emergenti che includono minacce fisiche, minacce basate su app e sulla rete, oltre a vulnerabilità del sistema operativo.
Da sempre le aziende hanno adottato soluzioni proattive per la protezione dei PC da attacchi esterni, senza tuttavia monitorare e proteggere i dispositivi mobili. Anche se le piattaforme mobili includono misure di protezione predefinite, come l'isolamento delle app e store online controllati per le app dei consumatori, rimangono comunque vulnerabili ad attacchi sofisticati. Oggi, un numero sempre maggiore di dipendenti usa i dispositivi al lavoro e deve accedere a informazioni sensibili. I dispositivi devono essere protetti dagli attacchi sempre più sofisticati.

## <a name="how-the-intune-mobile-threat-defense-connectors-work"></a>Come funzionano i connettori Mobile Threat Defense di Intune?

Il connettore protegge le risorse aziendali creando un canale di comunicazione tra Intune e il fornitore della soluzione Mobile Threat Defense. I partner Mobile Threat Defense di Intune offrono applicazioni intuitive e facili da distribuire per dispositivi mobili che analizzano in modo attivo le informazioni sulle minacce da condividere con Intune per segnalazioni e imposizioni. Ad esempio, se un'app Mobile Threat Defense connessa segnala al fornitore della soluzione Mobile Threat Defense che un telefono in rete è attualmente connesso a una rete vulnerabile ad attacchi Man in the Middle, questa informazione viene condivisa e classificata con il livello di rischio appropriato (basso/medio/alto) e può quindi essere messa a confronto con le impostazioni di livello di rischio configurate in Intune per determinare se revocare l'accesso a determinate risorse mentre il dispositivo è compromesso.

## <a name="sample-scenarios"></a>Scenari di esempio

Quando un dispositivo è considerato infetto da una soluzione Mobile Threat Defense:

![Mobile Threat Defense - Dispositivo infetto](../media/mtp/MTD-image-1.png)

L'accesso viene consentito quando i problemi del dispositivo vengono risolti:

![Mobile Threat Defense - Accesso consentito](../media/mtp/MTD-image-2.png)

## <a name="mobile-threat-defense-partners"></a>Partner Mobile Threat Defense

Informazioni sulla protezione dell'accesso alle risorse aziendali in base al rischio di dispositivi, reti e applicazioni con:

- [Lookout](/intune-classic/deploy-use/lookout-mobile-threat-defense-connector)
- [Skycure](/intune-classic/deploy-use/skycure-mobile-threat-defense-connector)

