---
title: Identificare gli scenari per i casi d'uso
titlesuffix: Microsoft Intune
description: Questo articolo aiuta a identificare gli scenari dei casi d'uso e dei casi d'uso secondari per un'implementazione di Microsoft Intune in configurazione solo cloud.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: de72bc56bf1ec0e7f1555d889ae0684c1162fdb9
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841403"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>Identificare gli scenari dei casi d'uso per la gestione di dispositivi mobili

Identificare gli scenari dei casi d'uso è una parte importante del processo di pianificazione per il successo della distribuzione di Intune. Gli scenari dei casi d'uso sono utili perché consentono di segmentare gli utenti in gruppi gestibili in base al tipo di utente o al ruolo e alla proprietà del dispositivo dell'utente (ad esempio, aziendale o personale).

Esaminiamo alcuni esempi che possono essere utili per aiutare le organizzazioni a identificare gli scenari dei casi d'uso per Intune, nonché i gruppi dell'organizzazione e le piattaforme per dispositivi mobili associate a ogni caso d'uso.

## <a name="device-ownership"></a>Proprietà del dispositivo
È possibile iniziare facendo riferimento agli scopi e agli obiettivi dell'organizzazione per la distribuzione di Intune per identificare gli scenari dei casi d'uso principali per la distribuzione. Nell'ambito del piano di distribuzione di Intune rispondere alle domande seguenti:

-   Si prevede di supportare dispositivi di proprietà dell'azienda?

-   Si prevede di supportare dispositivi personali (BYOD)?

Queste opzioni non si escludono a vicenda. Potrebbe essere necessario supportare entrambe le forme di proprietà del dispositivo per soddisfare gli obiettivi dell'organizzazione. I casi d'uso secondari consentiranno di chiarire dove applicare i diversi criteri di gestione dei dispositivi.

### <a name="user-type-or-device-role"></a>Tipo di utente o ruolo del dispositivo

Determinare se ogni scenario dei casi d'uso include anche casi d'uso secondari. Un'organizzazione potrebbe ad esempio avere identificato i requisiti per supportare uno scenario relativo al caso d'uso aziendale che include casi d'uso secondari aggiuntivi basati sul tipo di utente o sul ruolo del dispositivo, ad esempio:

-   Information Worker

-   Risorse esecutive

-   Modalità tutto schermo

Ecco alcuni esempi di scenari dei casi d'uso e dei casi d'uso secondari:

| **Casi d'uso** | **Casi d'uso secondari** |
|:---:|:---:|
| Aziendale | Information Worker |              
| Aziendale | Dirigenti |           
| Aziendale | Modalità tutto schermo |
| BYOD | Information Worker |           
| BYOD | Dirigenti |

È anche possibile [scaricare un modello della tabella precedente](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) per immettere gli scenari dei casi d'uso e dei casi d'uso secondari della propria organizzazione.

## <a name="organizational-groups-for-your-scenarios"></a>Gruppi dell'organizzazione per gli scenari

A questo punto, è necessario identificare i gruppi dell'organizzazione che sono associati a ogni scenario dei casi d'uso e dei casi d'uso secondari. Ad esempio:

| **Casi d'uso** | **Casi d'uso secondari** | **Gruppi dell'organizzazione** |
|:---:|:---:|:---:|
| Aziendale | Information Worker | HR, finanza |               
| Aziendale | Risorse esecutive | HR, finanza |            
| Aziendale | Modalità tutto schermo | Vendita al dettaglio |
| BYOD | Information Worker | Marketing, vendite |            
| BYOD | Risorse esecutive | Marketing, vendite |


## <a name="mobile-device-platforms-for-your-scenarios"></a>Piattaforme per dispositivi mobili per gli scenari

Il passaggio successivo è identificare le piattaforme per dispositivi mobili associate a ogni scenario dei casi d'uso. Possono essere più di una.

Lo scenario relativo al caso d'uso aziendale può ad esempio supportare le piattaforme per dispositivi iOS e Android Samsung Knox. I criteri BYOD possono includere il supporto per piattaforme per dispositivi mobili aggiuntive, come Android (non Samsung Knox) e Windows 10 Mobile. Sulla base degli esempi precedenti, sono state associate le piattaforme per dispositivi mobili a ogni scenario dei casi d'uso.

| **Casi d'uso** | **Casi d'uso secondari** | **Gruppi** | **Piattaforme per i dispositivi** |   
|:---:|:---:|:---:|:---:|
| Aziendale | Information Worker | HR, finanza | iOS |                                                           
| Aziendale | Dirigenti | HR, finanza | iOS |                                                           
| Aziendale | Modalità tutto schermo | Vendita al dettaglio | Android |
| BYOD | Information Worker | Marketing, vendite | iOS |                                                           
| BYOD | Dirigenti | Marketing, vendite | iOS |

## <a name="next-steps"></a>Passaggi successivi

Nella sezione successiva vengono fornite indicazioni su [come identificare i requisiti di Intune per ogni scenario dei casi d'uso](planning-guide-requirements.md).
