---
title: Connettore Check Point SandBlast Mobile con Intune
titleSuffix: Intune on Azure
description: Integrazione di Check Point SandBlast con Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 706a4228-9bdf-41e0-b8d1-64c923dd2d2b
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e722411e7eea11a604cdd2c6f7f818053d0ffbb0
ms.sourcegitcommit: 3b21f20108e2bf1cf47c141b36a7bdae609c4ec3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2017
---
# <a name="check-point-sandblast-mobile-threat-defense-connector-with-intune"></a>Connettore Check Point SandBlast Mobile Threat Defense con Intune

È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Check Point SandBlast Mobile, una soluzione di Mobile Threat Defense integrata in Microsoft Intune. La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono l'app Check Point SandBlast Mobile.

È possibile configurare criteri di accesso condizionale in base alla valutazione dei rischi di Check Point SandBlast Mobile abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

## <a name="how-do-intune-and-check-point-sandblast-mobile-help-protect-your-company-resources"></a>In che modo Intune e Check Point SandBlast Mobile consentono di proteggere le risorse aziendali?

L'app Check Point SandBlast Mobile per Android e iOS acquisisce (se disponibili) i dati di telemetria relativi al file system, allo stack di rete, al dispositivo e alle applicazioni e li invia al servizio cloud Check Point SandBlast per la valutazione del livello di rischio delle minacce per dispositivi mobili.

I criteri di conformità dei dispositivi di Intune includono una regola per Check Point SandBlast Mobile Threat Defense, basata sulla valutazione dei rischi eseguita da Check Point SandBlast. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati. Se il dispositivo risulta non conforme, l'accesso degli utenti a risorse aziendali come Exchange Online e SharePoint Online viene bloccato. Gli utenti ricevono inoltre istruzioni dall'app Check Point SandBlast Mobile installata nei relativi dispositivi per risolvere il problema e ottenere nuovamente l'accesso alle risorse aziendali.

<!-- ## Sample scenarios

Here are some common scenarios:

### Control access based on threats from malicious apps

When malicious apps such as malware are detected on devices, you can block devices until the threat is resolved:

-   Connecting to corporate e-mail

-   Syncing corporate files with the OneDrive for Work app

-   Accessing company apps

**Block when malicious apps are detected:**

![Check Point MTD block when malicious apps are detected](./media/checkpoint-MTD-2.PNG)

**Access granted on remediation:**

![Check Point MTD access granted](./media/checkpoint-MTD-3.PNG)

### Control access based on threat to network

Detect threats like **Man-in-the-middle** in network, and protect access to Wi-Fi networks based on the device risk.

**Block network access through Wi-Fi:**

![Check Point MTD block network access through Wi-Fi](./media/checkpoint-MTD-4.PNG)

**Access granted on remediation:**

![Check Point MTD Wi-Fi access granted](./media/checkpoint-MTD-5.PNG)

### Control access to SharePoint Online based on threat to network

Detect threats like **Man-in-the-middle** in network, and prevent synchronization of corporate files based on the device risk.

**Block SharePoint Online when network threats are detected:**

![Check Point MTD block SharePoint Online access](./media/checkpoint-MTD-6.PNG)

**Access granted on remediation:**

![Check Point MTD SharePoint Online access granted](./media/checkpoint-MTD-7.PNG)

## Supported platforms

-   **Android 4.1 and later**

-   **iOS 8 and later**

## Pre-requisites

-   Azure Active Directory Premium

-   Microsoft Intune subscription

-   Check Point SandBlast Mobile Threat Defense subscription
    -   See [CheckPoint SandBlast website](https://www.checkpoint.com/) for more information.

## Next steps

[Set up CheckPoint SandBlast Mobile app](mtd-apps-ios-app-configuration-policy-add-assign.md)

[Integrate CheckPoint SandBlast with Intune](checkpoint-sandblast-mobile-mtd-connector-integration.md)

[Enable CheckPoint SandBlast Mobile MTD connector](mtd-connector-enable.md)

[Create CheckPoint SandBlast Mobile device compliance policy](mtd-device-compliance-policy-create.md)
