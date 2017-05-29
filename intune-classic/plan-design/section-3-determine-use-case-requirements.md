---
title: Determinare i requisiti degli scenari dei casi d&quot;uso per Intune | Documentazione Microsoft
description: Questo articolo aiuta a determinare i requisiti degli scenari dei casi d&quot;uso e dei casi d&quot;uso secondari per un&quot;implementazione di Microsoft Intune in configurazione solo cloud.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: a56b683e57997171053f35414289d5b782c8fc2d
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="determine-intune-use-case-scenario-requirements"></a>Determinare i requisiti degli scenari dei casi d'uso per Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

In questa sezione verranno determinati i requisiti per ogni gruppo dell'organizzazione in ciascuno scenario dei casi d'uso. Questo processo consente di migliorare la preparazione per le altre aree della pianificazione della distribuzione di Intune, come architettura e progettazione, onboarding e implementazione. Può inoltre consentire di identificare potenziali gap e problemi correlati al progetto di distribuzione di Intune.

È possibile avere diversi set di requisiti per ognuno degli scenari dei casi d'uso e dei casi d'uso secondari, i gruppi dell'organizzazione associati e le piattaforme per dispositivi mobili. Ad esempio, i requisiti dello scenario relativo al caso d'uso aziendale potrebbero richiedere la registrazione dei dispositivi in Intune con un set di impostazioni più restrittivo (ad esempio, PIN di 6 caratteri e disabilitazione del backup cloud) rispetto al caso d'uso BYOD (Bring Your Own Device), che richiede impostazioni meno restrittive (ad esempio, PIN di 4 caratteri e abilitazione del backup cloud).

Possono anche essere presenti gruppi dell'organizzazione per lo scenario relativo al caso d'uso aziendale con set di requisiti diversi, ad esempio per le impostazioni del PIN, il profilo Wi-Fi o VPN e le app distribuite. Inoltre, i requisiti potrebbero essere determinati dalle funzionalità della piattaforma per dispositivi mobili (ad esempio, lettore di impronte digitali, profilo di posta elettronica).

Di seguito sono riportati alcuni esempi di requisiti per i casi d'uso di un'organizzazione, con diversi set di requisiti per ogni caso d'uso o caso d'uso secondario, gruppo dell'organizzazione e piattaforma per dispositivi mobili. È anche possibile usare la tabella seguente per immettere i requisiti per i casi d'uso della propria organizzazione:

| **Casi d'uso** | **Casi d'uso secondari** | **Gruppi** | **Piattaforme per i sistemi operativi dei dispositivi** | **Requirements** |
|:---:|:---:|:---:|:---:|:---:|
| Aziendale | Information Worker | HR, finanza | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |                                                          
| Aziendale | Dirigenti | HR, finanza | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |                                                         
| Aziendale | Modalità tutto schermo | Vendita al dettaglio | Android | Impostazioni del dispositivo, profili, app |
| BYOD | Information Worker | Marketing, vendite | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |                                                         
| BYOD | Dirigenti | Marketing, vendite | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |

## <a name="examples-of-requirements"></a>Esempi di requisiti

Di seguito sono riportati alcuni esempi aggiuntivi che possono essere usati nella colonna "Requisiti" della tabella precedente:

- **Posta elettronica sicura**
    - Accesso condizionale per Exchange Online/locale
    - Criteri di protezione delle app di Outlook
<br></br>
- **Impostazioni del dispositivo**
    - Impostazione del PIN con quattro, sei caratteri
    - Limitazione del backup cloud
<br></br>
- **Profili**
    - Wi-Fi
    - VPN
    - Posta elettronica (Windows 10 Mobile)
<br></br>
- **App**
    - Office 365 con criteri di protezione delle app
    - Line-of-business criteri di protezione delle app

## <a name="next-section"></a>Sezione successiva

Nella sezione successiva vengono fornite indicazioni su [come elaborare un piano di implementazione di Intune](section-4-develop-a-rollout-plan.md).

