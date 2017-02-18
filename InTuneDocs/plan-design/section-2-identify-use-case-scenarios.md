---
title: Identificare gli scenari dei casi d&quot;uso per Intune | Documentazione Microsoft
description: Questo articolo aiuta a identificare gli scenari dei casi d&quot;uso e dei casi d&quot;uso secondari per un&quot;implementazione di Microsoft Intune in configurazione solo cloud.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f807d6e4b20b98ecf622d1ebdd9db33b132a2e6a
ms.openlocfilehash: c834b0282b8f9b47566ab1da2125d993ba8febdf


---

# <a name="identify-intune-use-case-scenarios"></a>Identificare gli scenari dei casi d'uso per Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

Gli scenari dei casi d'uso per la gestione dei dispositivi mobili descrivono il tipo di utente o il ruolo e la proprietà del dispositivo (ad esempio, aziendale o personale). Gli scenari dei casi d'uso sono utili perché consentono di segmentare gli utenti in gruppi gestibili. Identificare gli scenari dei casi d'uso è una parte importante del processo di pianificazione per il successo della distribuzione di Intune.

Esaminiamo alcuni esempi che possono essere utili per aiutare le organizzazioni a identificare gli scenari dei casi d'uso per Intune, nonché i gruppi dell'organizzazione e le piattaforme per dispositivi mobili associate a ogni caso d'uso.

## <a name="use-case-scenarios"></a>Scenari dei casi d'uso

È possibile iniziare facendo riferimento agli scopi e agli obiettivi dell'organizzazione per la distribuzione di Intune per identificare gli scenari dei casi d'uso principali per la distribuzione. Nell'ambito del piano di distribuzione di Intune sarà necessario rispondere alle domande seguenti:

-   Si prevede di supportare dispositivi di proprietà dell'azienda?

-   Si prevede di supportare dispositivi personali (BYOD)?

### <a name="sub-use-case-scenarios"></a>Scenari dei casi d'uso secondari

Dopo avere identificato gli scenari dei casi d'uso principali, sarà necessario determinare se ogni scenario dei casi d'uso include anche casi d'uso secondari. Un'organizzazione potrebbe ad esempio avere identificato i requisiti per supportare uno scenario relativo al caso d'uso aziendale che include casi d'uso secondari aggiuntivi:

-   Information Worker

-   Dirigenti

-   Modalità tutto schermo

Ecco alcuni esempi di scenari dei casi d'uso e dei casi d'uso secondari. È anche possibile usare la tabella seguente per immettere gli scenari dei casi d'uso e dei casi d'uso secondari della propria organizzazione:

| **Casi d'uso** | **Casi d'uso secondari** |
|:---:|:---:|
| Aziendale | Information Worker |              
| Aziendale | Dirigenti |           
| Aziendale | Modalità tutto schermo |
| BYOD | Information Worker |           
| BYOD | Dirigenti |

## <a name="identify-organizational-groups-associated-with-use-case-scenarios"></a>Identificare i gruppi dell'organizzazione associati ai casi d'uso

A questo punto, è necessario identificare i gruppi dell'organizzazione che sono associati a ogni scenario dei casi d'uso e dei casi d'uso secondari. Di seguito sono riportati alcuni esempi di gruppi dell'organizzazione associati agli scenari dei casi d'uso e dei casi d'uso secondari, che è possibile usare come modello per immettere le informazioni della propria organizzazione:

| **Casi d'uso** | **Casi d'uso secondari** | **Gruppi dell'organizzazione** |
|:---:|:---:|:---:|
| Aziendale | Information Worker | HR, finanza |               
| Aziendale | Risorse esecutive | HR, finanza |            
| Aziendale | Modalità tutto schermo | Vendita al dettaglio |
| BYOD | Information Worker | Marketing, vendite |            
| BYOD | Risorse esecutive | Marketing, vendite |

## <a name="identify-mobile-device-platforms-for-use-case-scenarios"></a>Identificare le piattaforme per dispositivi mobili per gli scenari dei casi d'uso

A questo punto, è possibile identificare le piattaforme per dispositivi mobili associate a ogni scenario dei casi d'uso. Ad esempio, lo scenario relativo al caso d'uso aziendale potrebbe supportare le piattaforme per i dispositivi iOS e Android Samsung KNOX e i criteri BYOD potrebbero includere il supporto per altre piattaforme per dispositivi mobili come Android (NON Samsung KNOX) e Windows 10 Mobile. Ecco un esempio di piattaforme per dispositivi mobili associate a ogni scenario dei casi d'uso. È possibile usare la tabella seguente per immettere le piattaforme per i dispositivi dell'organizzazione associate agli scenari dei casi d'uso:

| **Casi d'uso** | **Casi d'uso secondari** | **Gruppi** | **Piattaforme per i dispositivi** |   
|:---:|:---:|:---:|:---:|
| Aziendale | Information Worker | HR, finanza | iOS |                                                           
| Aziendale | Dirigenti | HR, finanza | iOS |                                                           
| Aziendale | Modalità tutto schermo | Vendita al dettaglio | Android |
| BYOD | Information Worker | Marketing, vendite | iOS |                                                           
| BYOD | Dirigenti | Marketing, vendite | iOS |

## <a name="next-section"></a>Sezione successiva

Nella sezione successiva vengono fornite indicazioni su [come identificare i requisiti di Intune per ogni scenario dei casi d'uso](section-3-determine-use-case-requirements.md).



<!--HONumber=Dec16_HO5-->


