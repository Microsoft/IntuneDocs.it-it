---
title: Mobile Threat Defense con Microsoft Intune
titleSuffix: Microsoft Intune
description: Usare Intune Mobile Threat Defense (MTD) con il proprio partner Mobile Threat Defense per proteggere l'accesso alle risorse aziendali in base ai rischi del dispositivo.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b67e3b14fd94376fb6dacad88fa58ddc460a6bc5
ms.sourcegitcommit: 807ab3e35f4d9ffa18655410b7d61e5e772ab348
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2019
ms.locfileid: "73057572"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Integrazione di Mobile Threat Defense in Intune

Intune può integrare dati da un fornitore di soluzioni MTD (Mobile Threat Defense) come origine delle informazioni per i criteri di conformità dei dispositivi e le regole di accesso condizionale dei dispositivi. È possibile usare queste informazioni per semplificare la protezione di risorse aziendali come Exchange e SharePoint, bloccando l'accesso da dispositivi mobili compromessi.

Intune può usare questi stessi dati come origine per i dispositivi non registrati usando i criteri di protezione delle app di Intune. Di conseguenza, gli amministratori possono usare queste informazioni per proteggere i dati aziendali all'interno di un'[app protetta da Microsoft Intune](~/apps/apps-supported-intune-apps.md) ed eseguire un blocco o una cancellazione selettiva.

## <a name="protect-corporate-resources"></a>Proteggere le risorse aziendali

L'integrazione delle informazioni provenienti da fornitori di soluzioni MTD consente di proteggere le risorse aziendali da minacce in grado di colpire le piattaforme mobili.  

Da sempre le aziende adottano soluzioni proattive per la protezione dei PC da vulnerabilità e attacchi, mentre i dispositivi mobili sono spesso non monitorati e non protetti. Anche se le piattaforme mobili includono misure di protezione predefinite come l'isolamento delle app e store di app dei consumatori controllati, queste piattaforme restano vulnerabili ad attacchi sofisticati. Con l'aumentare dei dipendenti che usano dispositivi per il lavoro e per accedere a dati sensibili, le informazioni provenienti da fornitori di soluzioni MTD consentono di proteggere i dispositivi e le risorse da attacchi sempre più sofisticati.

## <a name="intune-mobile-threat-defense-connectors"></a>Connettori Mobile Threat Defense di Intune

Intune usa un connettore di Mobile Threat Defense per creare un canale di comunicazione tra Intune e il fornitore di soluzioni MTD scelto. I partner MTD di Intune offrono applicazioni intuitive e facili da distribuire per i dispositivi mobili. Queste applicazioni analizzano attivamente le informazioni sulle minacce da condividere con Intune. Intune può usare i dati per scopi di creazione di report o applicazione.

Ad esempio: Un'app MTD connessa, ad esempio, segnala al fornitore di soluzioni MTD che un telefono nella rete è connesso a una rete vulnerabile ad attacchi man-in-the-middle. Queste informazioni vengono suddivise in categorie in base a un livello di rischio appropriato: basso, medio o elevato. Questo livello di rischio viene quindi confrontato con il livello di rischio massimo impostato in Intune. In base a questo confronto, l'accesso a determinate risorse desiderate può essere revocato quando il dispositivo è compromesso.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Dati raccolti da Intune per Mobile Threat Defense

Se abilitato, Intune raccoglie le informazioni degli inventari delle app dei dispositivi personali e aziendali e le rende disponibili per i provider MTD, ad esempio Lookout for Work. Si possono raccogliere gli inventari delle app dagli utenti di dispositivi iOS.

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
> È possibile usare più fornitori MTD con un unico tenant di Intune. Se tuttavia due o più fornitori sono configurati per l'uso nella stessa piattaforma, tutti i dispositivi che eseguono tale piattaforma devono installare le app MTD di tutti i fornitori e verificare la presenza di minacce. Il mancato invio dell'analisi con una qualsiasi delle app configurate comporta l'identificazione del dispositivo come non conforme. 

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
