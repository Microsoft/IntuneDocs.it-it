---
title: Configurare Check Point SandBlast MTD
titleSuffix: Microsoft Intune
description: Informazioni sull'integrazione di Intune con Check Point SandBlast Mobile Threat Defense per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/03/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 053dc104a67c1e76c5316fb0fd77eb6868494e89
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722839"
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Connettore Check Point SandBlast Mobile Threat Defense con Intune

È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Check Point SandBlast Mobile, una soluzione di Mobile Threat Defense integrata in Microsoft Intune. La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono l'app Check Point SandBlast Mobile.

È possibile configurare criteri di accesso condizionale in base alla valutazione dei rischi di Check Point SandBlast Mobile abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>In che modo Intune e Check Point SandBlast Mobile consentono di proteggere le risorse aziendali?

L'app Check Point SandBlast Mobile per Android e iOS acquisisce (se disponibili) i dati di telemetria relativi al file system, allo stack di rete, al dispositivo e alle applicazioni e li invia al servizio cloud Check Point SandBlast per la valutazione del livello di rischio delle minacce per dispositivi mobili.

I criteri di conformità dei dispositivi di Intune includono una regola per Check Point SandBlast Mobile Threat Defense, basata sulla valutazione dei rischi eseguita da Check Point SandBlast. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati. Se il dispositivo risulta non conforme, l'accesso degli utenti a risorse aziendali come Exchange Online e SharePoint Online viene bloccato. Gli utenti ricevono inoltre istruzioni dall'app Check Point SandBlast Mobile installata nei relativi dispositivi per risolvere il problema e ottenere nuovamente l'accesso alle risorse aziendali.

<!-- ## Sample scenarios 
closing syntax for comment above is missing. Please insert closing syntax at intended location. -->

Ecco alcuni scenari comuni:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose

Se nei dispositivi vengono rilevate app dannose, come malware, è possibile bloccare i dispositivi finché la condizione di minaccia non viene risolta:

- Connessione alla posta elettronica aziendale

- Sincronizzazione di file aziendali tramite l'app OneDrive for Work

- Accesso alle app aziendali

**Bloccare quando vengono rilevate app dannose:**

![Blocco di Check Point MTD quando vengono rilevate app dannose](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-2.PNG)

**Accesso concesso dopo la correzione:**

![Accesso a Check Point MTD concesso](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-3.PNG)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete

Rilevare minacce nella rete, come attacchi di tipo **Man-in-the-middle**, e proteggere l'accesso alle reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**

![Blocco di Check Point MTD dell'accesso alla rete Wi-Fi](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-4.PNG)

**Accesso concesso dopo la correzione:**

![Accesso alla rete Wi-Fi Check Point MTD concesso](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-5.PNG)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare minacce nella rete, come attacchi di tipo **Man-in-the-middle**, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Blocco di Check Point MTD dell'accesso di SharePoint Online](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-6.PNG)

**Accesso concesso dopo la correzione:**

![Blocco di Check Point MTD dell'accesso di SharePoint Online concesso](./media/checkpoint-sandblast-mobile-mobile-threat-defense-connector/checkpoint-MTD-7.PNG)

## <a name="supported-platforms"></a>Piattaforme supportate

- **Android 4.1 e versioni successive**

- **iOS 8 e versioni successive**

## <a name="pre-requisites"></a>Prerequisiti

- Azure Active Directory Premium

- Sottoscrizione di Microsoft Intune

- Sottoscrizione di Check Point SandBlast Mobile Threat Defense
  - Vedere il [sito Web di CheckPoint SandBlast](https://www.checkpoint.com/) per altre informazioni.

## <a name="next-steps"></a>Passaggi successivi

- [Integrare Check Point SandBlast con Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

- [Configurare l'app Check Point SandBlast Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Creare criteri di conformità per dispositivi CheckPoint SandBlast Mobile](mtd-device-compliance-policy-create.md)

- [Abilitare il connettore CheckPoint SandBlast Mobile MTD](mtd-connector-enable.md)
