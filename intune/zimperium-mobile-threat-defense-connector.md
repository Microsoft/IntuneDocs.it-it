---
title: Connettore Zimperium MTD con Intune
titleSuffix: Intune on Azure
description: Integrazione del connettore Zimperium con Intune
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 09/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 975d8d84-792a-41ad-925a-4a7f1ae4dcaf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 78214293a66784d4bc05e441c2c1cdbf718b0a9a
ms.sourcegitcommit: d434dfab7ef7a6c4082d675717fa22d5581b4f51
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2017
---
# <a name="zimperium-mobile-threat-defense-connector-with-intune"></a>Connettore Zimperium Mobile Threat Defense con Intune

È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi condotta da Zimperium, una soluzione MTD (Mobile Threat Defense) integrata in Microsoft Intune. La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono l'app Zimperium.

È possibile configurare criteri di accesso condizionale basati sulla valutazione dei rischi di Zimperium abilitata con i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

## <a name="how-do-intune-and-zimperium-help-protect-your-company-resources"></a>In che modo Intune e Zimperium consentono di proteggere le risorse aziendali?

L'app Zimperium per Android e iOS acquisisce i dati di telemetria, se disponibili, relativi al file system, allo stack di rete, al dispositivo e alle applicazioni e li invia al servizio cloud Zimperium per la valutazione del livello di rischio delle minacce per dispositivi mobili.

I criteri di conformità dei dispositivi di Intune includono una regola per Zimperium Mobile Threat Defense basata sulla valutazione dei rischi eseguita da Zimperium. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati. Se il dispositivo risulta non conforme, l'accesso degli utenti a risorse aziendali come Exchange Online e SharePoint Online viene bloccato. Gli utenti ricevono inoltre istruzioni dall'app Zimperium installata nei relativi dispositivi per risolvere il problema e ottenere nuovamente l'accesso alle risorse aziendali.

## <a name="sample-scenarios"></a>Scenari di esempio

Di seguito sono riportati alcuni scenari in cui Zimperium viene integrato in Intune:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose

Se nei dispositivi vengono rilevate app dannose, come malware, è possibile bloccare i dispositivi finché la condizione di minaccia non viene risolta:

-   Connessione alla posta elettronica aziendale

-   Sincronizzazione di file aziendali tramite l'app OneDrive for Work

-   Accesso alle app aziendali

**Bloccare quando vengono rilevate app dannose:**

![App dannose rilevate](./media/Maliciousapps_blocked_Zimperium.png)

**Accesso concesso dopo la risoluzione:**

![App dannose rilevate e accesso consentito](./media/maliciousapps_unblocked_Zimperium.png)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete

Rilevare minacce nella rete, come attacchi di tipo **Man-in-the-middle**, e proteggere l'accesso alle reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**

![Bloccare l'accesso alla rete tramite Wi-Fi](./media/network_wifi_blocked_Zimperium.png)

**Accesso concesso dopo la risoluzione:**

![Accesso concesso dopo la risoluzione](./media/network_wifi_unblocked_Zimperium.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare minacce nella rete, come attacchi di tipo **Man-in-the-middle**, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Bloccare SharePoint Online quando vengono rilevate minacce per la rete](./media/network_spo_blocked_Zimperium.png)

**Accesso concesso dopo la risoluzione:**

![Accesso concesso dopo la risoluzione per l'esempio di SharePoint](./media/network_spo_unblocked_Zimperium.png)

## <a name="supported-platforms"></a>Piattaforme supportate

-   **Android 4.1 e versioni successive**

-   **iOS 8 e versioni successive**

## <a name="prerequisites"></a>Prerequisiti

-   Azure Active Directory Premium

-   Sottoscrizione di Microsoft Intune

-   Sottoscrizione di Zimperium Mobile Threat Defense

    -   Vedere il [sito Web di Zimperium](https://www.zimperium.com/zips-mobile-ips) per altre informazioni.

## <a name="next-steps"></a>Passaggi successivi

- [Integrare Zimperium con Intune](zimperium-mtd-connector-integration.md)

- [Configurare le app di Zimperium](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Creare criteri di conformità dei dispositivi di Zimperium](mtd-device-compliance-policy-create.md)

- [Abilitare il connettore Zimperium MTD](mtd-connector-enable.md)
