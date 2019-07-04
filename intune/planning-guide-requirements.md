---
title: Determinare i requisiti degli scenari per i casi d'uso
titleSuffix: Microsoft Intune
description: Questo articolo aiuta a determinare i requisiti degli scenari dei casi d'uso e dei casi d'uso secondari per un'implementazione di Microsoft Intune in configurazione solo cloud.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98441f03ae2ac9ef23e84de8d06198335da69198
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044323"
---
# <a name="determine-use-case-scenario-requirements"></a>Determinare i requisiti degli scenari per i casi d'uso

In questa sezione vengono determinati i requisiti per ogni gruppo dell'organizzazione in ciascuno scenario dei casi d'uso. Questo processo agevola la preparazione per le altre aree della pianificazione della distribuzione di Intune, come architettura e progettazione, onboarding e implementazione. Può inoltre consentire di identificare potenziali gap e problemi correlati al progetto di distribuzione di Intune.

È possibile avere diversi set di requisiti per ognuno degli scenari dei casi d'uso e dei casi d'uso secondari, i gruppi dell'organizzazione associati e le piattaforme per dispositivi mobili. Ad esempio, i requisiti dello scenario relativo al caso d'uso aziendale potrebbero richiedere la registrazione dei dispositivi in Intune con un set di impostazioni più restrittivo, ad esempio un PIN di 6 caratteri o la disabilitazione del backup cloud. Lo scenario relativo al caso d'uso BYOD (Bring Your Own Device) potrebbe essere meno restrittivo, consentendo un PIN di 4 caratteri e il backup cloud.

Possono anche essere presenti gruppi dell'organizzazione per lo scenario relativo al caso d'uso aziendale con set di requisiti diversi, ad esempio per le impostazioni del PIN, il profilo Wi-Fi o VPN e le app distribuite. I requisiti possono anche essere determinati dalle funzionalità della piattaforma per dispositivi mobili (ad esempio, lettore di impronte digitali, profilo di posta elettronica).

Di seguito sono riportati alcuni esempi di requisiti per i casi d'uso di un'organizzazione, con diversi set di requisiti per ogni caso d'uso e caso d'uso secondario, gruppo dell'organizzazione e piattaforma per dispositivi mobili. È anche possibile usare la tabella seguente per immettere i requisiti per i casi d'uso della propria organizzazione:

| **Casi d'uso** | **Casi d'uso secondari** | **Gruppi** | **Piattaforme per i dispositivi** | **Requisiti** |
|:---:|:---:|:---:|:---:|:---:|
| Aziendale | Information Worker | HR, finanza | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |                                                          
| Aziendale | Dirigenti | HR, finanza | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |                                                         
| Aziendale | Modalità tutto schermo | Vendita al dettaglio | Android | Impostazioni del dispositivo, profili, app |
| BYOD | Information Worker | Marketing, vendite | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |                                                         
| BYOD | Dirigenti | Marketing, vendite | iOS | Posta elettronica sicura, impostazioni del dispositivo, profili, app |

È anche possibile [scaricare un modello della tabella precedente](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) per immettere i requisiti dei casi d'uso e dei casi d'uso secondari della propria organizzazione.


## <a name="examples-of-requirements"></a>Esempi di requisiti

Di seguito sono riportati alcuni esempi aggiuntivi che possono essere usati nella colonna "Requisiti":

- **Posta elettronica sicura**
    - Accesso condizionale per Exchange Online/locale
    - Criteri di protezione delle app di Outlook

- **Impostazioni del dispositivo**
    - Impostazione del PIN con quattro, sei caratteri
    - Limitazione del backup cloud

- **Profili**
    - Wi-Fi
    - VPN
    - Posta elettronica (Windows 10 Mobile)

- **App**
    - Office 365 con criteri di protezione delle app
    - Line-of-business criteri di protezione delle app

## <a name="next-steps"></a>Passaggi successivi

Nella sezione successiva vengono fornite indicazioni su [come elaborare un piano di implementazione di Intune](planning-guide-rollout-plan.md).
