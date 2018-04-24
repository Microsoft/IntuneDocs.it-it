---
title: Mobile Threat Defense di Intune
description: Proteggere l'accesso alle risorse aziendali in base al rischio dei dispositivi.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/01/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 08d87906-8158-4d5e-a49d-ad919efef3d1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 97711301422dd86ed0a76375add54987809c07b7
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="intune-mobile-threat-defense-connectors"></a>Connettori Mobile Threat Defense di Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

I connettori Mobile Threat Defense di Intune consentono di basare i criteri di conformità e le regole di accesso condizionale sulle informazioni offerte dal fornitore della soluzione Mobile Threat Defense. Ciò consente agli amministratori IT di aggiungere un livello di protezione per le risorse aziendali, ad esempio Exchange e Sharepoint, dai rischi specifici di dispositivi mobili compromessi.

## <a name="what-problem-does-this-solve"></a>Qual è il problema risolto?

Le aziende hanno l'esigenza di proteggere i dati sensibili da minacce emergenti che includono minacce fisiche, minacce basate su app e sulla rete, oltre a vulnerabilità del sistema operativo.
Da sempre le aziende hanno adottato soluzioni proattive per la protezione dei PC da attacchi esterni, senza tuttavia monitorare e proteggere i dispositivi mobili. Le piattaforme mobili hanno protezioni incorporate, come l'isolamento delle app e il controllo degli app store consumer, ma continuano a essere vulnerabili agli attacchi sofisticati. Oggi, un numero sempre maggiore di dipendenti usa i dispositivi al lavoro e deve accedere a informazioni sensibili. I dispositivi devono essere protetti dagli attacchi sempre più sofisticati.

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
