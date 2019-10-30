---
title: Mobile Threat Defense con Microsoft Intune
titleSuffix: Microsoft Intune
description: Usare Intune Mobile Threat Defense (MTD) con il proprio partner Mobile Threat Defense per proteggere l'accesso alle risorse aziendali in base ai rischi del dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4abc35b625b9aa072e38c02d2fc4160faa916fb3
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2019
ms.locfileid: "72785750"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Che cos'è l'integrazione di Mobile Threat Defense in Intune?
Intune può integrare dati da un fornitore di soluzioni Mobile Threat Defense come origine delle informazioni per i criteri di conformità dei dispositivi e le regole di accesso condizionale dei dispositivi. È possibile usare queste informazioni per semplificare la protezione di risorse aziendali come Exchange e SharePoint, bloccando l'accesso da dispositivi mobili compromessi.

Intune può usare questi stessi dati come origine per i dispositivi non registrati usando i criteri di protezione delle app di Intune. Di conseguenza, gli amministratori possono usare queste informazioni per proteggere i dati aziendali all'interno di un'[app protetta da Microsoft Intune](~/apps/apps-supported-intune-apps.md) ed eseguire un blocco o una cancellazione selettiva.

## <a name="what-problem-does-this-solve"></a>Quale problema risolve questa soluzione?
L'integrazione delle informazioni da un fornitore di soluzioni Mobile Threat Defense permette di proteggere le risorse aziendali da minacce in grado di colpire le piattaforme mobili.  

Da sempre le aziende adottano soluzioni proattive per la protezione dei PC da vulnerabilità e attacchi, mentre i dispositivi mobili sono spesso non monitorati e non protetti. Anche se le piattaforme mobili includono misure di protezione predefinite come l'isolamento delle app e store di app dei consumatori controllati, queste piattaforme restano vulnerabili ad attacchi sofisticati. Con l'aumentare dei dipendenti che usano dispositivi per il lavoro e per accedere a dati sensibili, le informazioni dal fornitore di soluzioni Mobile Threat Defense permettono di proteggere i dispositivi e le risorse da attacchi sempre più sofisticati.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Come funzionano i connettori Mobile Threat Defense di Intune?

Intune usa un connettore di Mobile Threat Defense per creare un canale di comunicazione tra Intune e il fornitore di soluzioni Mobile Threat Defense. I partner Mobile Threat Defense di Intune offrono applicazioni intuitive e facili da distribuire per i dispositivi mobili. Queste applicazioni analizzano attivamente le informazioni sulle minacce da condividere con Intune. Intune può usare i dati per scopi di creazione di report o applicazione.  

Ad esempio: Un'app Mobile Threat Defense connessa, ad esempio, segnala al fornitore di soluzioni Mobile Threat Defense che un telefono nella rete è attualmente connesso a una rete vulnerabile ad attacchi "man-in-the-middle". Queste informazioni vengono suddivise in categorie in base a un livello di rischio appropriato: basso, medio o elevato. Questo livello di rischio viene quindi confrontato con il livello di rischio massimo impostato in Intune. In base a questo confronto, l'accesso a determinate risorse desiderate può essere revocato quando il dispositivo è compromesso.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Quali dati raccoglie Intune per Mobile Threat Defense?

Se abilitato, Intune raccoglie le informazioni degli inventari delle app dei dispositivi personali e aziendali e le rende disponibili per i provider del servizio di rilevamento delle minacce per i dispositivi mobili (MTD, Mobile Threat Detection), ad esempio Lookout for Work. Si possono raccogliere gli inventari delle app dagli utenti di dispositivi iOS.

Per l'uso di questo servizio è richiesto il consenso esplicito. Nessuna informazione di inventario di app viene condivisa per impostazione predefinita. Un amministratore di Intune deve abilitare la **sincronizzazione delle app per dispositivi iOS** nelle impostazioni del connettore Mobile Threat Defense prima che vengano condivise informazioni di inventario delle app.

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

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>Scenari di esempio per i dispositivi registrati con i criteri di conformità dei dispositivi

Quando un dispositivo è considerato infetto da una soluzione Mobile Threat Defense:

![Immagine che mostra un dispositivo infetto per Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-1.png)

L'accesso viene consentito quando i problemi del dispositivo vengono risolti:

![Immagine che mostra l'accesso consentito da Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Scenari di esempio per i dispositivi non registrati con i criteri di protezione delle app di Intune

Quando un dispositivo è considerato infetto da una soluzione Mobile Threat Defense:<br>
![Immagine che mostra un dispositivo infetto per Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-3.png)

L'accesso viene consentito quando i problemi del dispositivo vengono risolti:<br>
![Immagine che mostra l'accesso consentito da Mobile Threat Defense](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE] 
> L'uso di più fornitori di soluzioni Mobile Threat Defense con Intune non è supportato. Se sono abilitati più connettori MTD, viene forzata l'installazione di tutte le app MTD, che effettueranno l'analisi di tutti i dispositivi per il rilevamento di eventuali minacce.

## <a name="mobile-threat-defense-partners"></a>Partner Mobile Threat Defense

Informazioni sulla protezione dell'accesso alle risorse aziendali in base al rischio di dispositivi, reti e applicazioni con:

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [Better Mobile](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
