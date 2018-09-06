---
title: Mobile Threat Defense con Microsoft Intune
titleSuffix: ''
description: Usare Intune Mobile Threat Defense (MTD) con il proprio partner Mobile Threat Defense per proteggere l'accesso alle risorse aziendali in base ai rischi del dispositivo.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6dae7f6973f6259284fc21e5e4b8e98b67517102
ms.sourcegitcommit: 973a06f4a35b74314fece2bae17dd6885b4211c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "42823002"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Che cos'è l'integrazione di Mobile Threat Defense in Intune?


I connettori Mobile Threat Defense di Intune consentono di basare i criteri di conformità e le regole di accesso condizionale sulle informazioni offerte dal fornitore della soluzione Mobile Threat Defense. Ciò consente agli amministratori IT di aggiungere alle risorse aziendali, ad esempio Exchange e Sharepoint, un livello di protezione specifico per i rischi correlati a dispositivi mobili compromessi.

## <a name="what-problem-does-this-solve"></a>Quale problema risolve questa soluzione?

Le aziende hanno l'esigenza di proteggere i dati sensibili da minacce emergenti che includono minacce fisiche, minacce basate su app e sulla rete, oltre a vulnerabilità del sistema operativo.

Da sempre le aziende hanno adottato soluzioni proattive per la protezione dei PC da attacchi esterni, senza monitoraggio e protezione per i dispositivi mobili. Anche se le piattaforme mobili includono misure di protezione predefinite, come l'isolamento delle app e store online controllati per le app dei consumatori, rimangono comunque vulnerabili ad attacchi sofisticati. Oggi, un numero sempre maggiore di dipendenti usa i dispositivi al lavoro e deve accedere a informazioni sensibili. I dispositivi devono essere protetti da attacchi sempre più sofisticati.

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Come funzionano i connettori Mobile Threat Defense di Intune?

Il connettore protegge le risorse aziendali creando un canale di comunicazione tra Intune e il fornitore della soluzione Mobile Threat Defense. I partner Mobile Threat Defense di Intune offrono applicazioni intuitive e facili da distribuire per dispositivi mobili, che analizzano in modo attivo le informazioni sulle minacce da condividere con Intune per segnalazioni e imposizioni. 

Se ad esempio un'app Mobile Threat Defense connessa segnala al fornitore della soluzione Mobile Threat Defense che un telefono in rete è attualmente connesso a una rete vulnerabile ad attacchi Man in the Middle, questa informazione viene condivisa e classificata con il livello di rischio appropriato (basso/medio/alto) e può quindi essere messa a confronto con le impostazioni di livello di rischio configurate in Intune per determinare se revocare l'accesso a determinate risorse mentre il dispositivo è compromesso.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Quali dati raccoglie Intune per Mobile Threat Defense?

Se abilitato, Intune raccoglie le informazioni degli inventari delle app dei dispositivi personali e aziendali e le rende disponibili per i provider del servizio di rilevamento delle minacce per i dispositivi mobili (MTD, Mobile Threat Detection), ad esempio Lookout for Work. Si possono raccogliere gli inventari delle app dagli utenti di dispositivi iOS.

Per l'uso di questo servizio è richiesto il consenso esplicito. Nessuna informazione di inventario di app viene condivisa per impostazione predefinita. Un amministratore di Intune deve abilitare la sincronizzazione delle app per dispositivi iOS nelle impostazioni del servizio prima che vengano condivise informazioni di inventario delle app.

**Inventario delle app**  
Se si abilita la sincronizzazione delle app per dispositivi iOS, gli inventari dei dispositivi iOS aziendali e personali vengono inviati al provider del servizio MTD. I dati dell'inventario delle app includono:

 - ID dell'app
 - Versione dell'app
 - Versione breve dell'app
 - Nome dell'app
 - Dimensione del bundle dell'app
 - Dimensione dinamica dell'app
 - Indicazione se l'app è o meno convalidata
 - Indicazione se l'app è o meno gestita

## <a name="sample-scenarios"></a>Scenari di esempio

Quando un dispositivo è considerato infetto da una soluzione Mobile Threat Defense:

![Immagine che mostra un dispositivo infetto per Mobile Threat Defense](./media/MTD-image-1.png)

L'accesso viene consentito quando i problemi del dispositivo vengono risolti:

![Immagine che mostra l'accesso consentito da Mobile Threat Defense](./media/MTD-image-2.png)

> [!NOTE] 
> L'uso di più fornitori di soluzioni Mobile Threat Defense con Intune non è supportato. Se sono abilitati più strumenti di Mobile Threat Defense, viene forzata l'installazione di tutte le app di Mobile Threat Defense, che effettueranno l'analisi di tutti i dispositivi per il rilevamento di eventuali minacce.

## <a name="mobile-threat-defense-partners"></a>Partner Mobile Threat Defense

Informazioni sulla protezione dell'accesso alle risorse aziendali in base al rischio di dispositivi, reti e applicazioni con:

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
