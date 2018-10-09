---
title: Connettore Better Mobile Threat Defense con Intune
titleSuffix: Intune on Azure
description: Configurare il connettore Better Mobile Threat Defense con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 7/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.openlocfilehash: ae1c45d6449f7ad3661c89cb514524fb13c9a3fb
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2018
ms.locfileid: "48231560"
---
# <a name="better-mobile-threat-defense-connector-with-intune"></a>Connettore Better Mobile Threat Defense con Intune

È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi condotta da Better Mobile, una soluzione MTD (Mobile Threat Defense) integrata in Microsoft Intune. La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono l'app Better Mobile.

È possibile configurare criteri di accesso condizionale in base alla valutazione dei rischi di Better Mobile abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

## <a name="how-do-intune-and-better-mobile-help-protect-your-company-resources"></a>In che modo Intune e Better Mobile consentono di proteggere le risorse aziendali?

L'app Better Mobile viene installata ed eseguita nei dispositivi mobili. Questa app consente di acquisire dati di telemetria per il file system, lo stack di rete, il dispositivo e le applicazioni (se disponibili) e di inviarli al servizio cloud Better Mobile per la valutazione del livello di rischio per le minacce per dispositivi mobili.

I criteri di conformità dei dispositivi di Intune includono una regola per Mobile Threat Defense, basata sulla valutazione dei rischi eseguita da Better Mobile. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati. Se il dispositivo risulta non conforme, l'accesso degli utenti a risorse aziendali come Exchange Online e SharePoint Online viene bloccato. Gli utenti ricevono inoltre istruzioni dall'app Better Mobile installata nei relativi dispositivi per risolvere il problema e ottenere nuovamente l'accesso alle risorse aziendali.

## <a name="sample-scenarios"></a>Scenari di esempio

Ecco alcuni scenari comuni.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose

Se nei dispositivi vengono rilevate app dannose, come malware, è possibile impedire ai dispositivi di eseguire le azioni seguenti fino alla risoluzione della condizione di minaccia:

-   Connessione alla posta elettronica aziendale

-   Sincronizzazione di file aziendali tramite l'app OneDrive for Work

-   Accesso alle app aziendali

**Bloccare quando vengono rilevate app dannose:**

![App dannose rilevate](./media/better_mobile_maliciousapps_blocked.png)

**Accesso concesso dopo la correzione:**

![App dannose rilevate e accesso consentito](./media/better_mobile_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete

Rilevare le minacce per la rete, ad esempio attacchi **Man-in-the-middle** e proteggere l'accesso alle reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**

![Bloccare l'accesso alla rete tramite Wi-Fi](./media/better_mobile_network_wifi_blocked.png)

**Accesso concesso dopo la correzione:**

![Accesso concesso dopo la risoluzione](./media/better_mobile_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare le minacce per la rete, ad esempio attacchi **Man-in-the-middle**, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Bloccare SharePoint Online quando vengono rilevate minacce per la rete](./media/better_mobile_network_spo_blocked.png)

**Accesso concesso dopo la correzione:**

![Accesso concesso dopo la risoluzione per l'esempio di SharePoint](./media/better_mobile_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Piattaforme supportate

-   **Android 4.1 e versioni successive**

-   **iOS 8.0 e versioni successive**

## <a name="prerequisites"></a>Prerequisiti

-   Azure Active Directory Premium

-   Sottoscrizione di Microsoft Intune

-   Sottoscrizione di Better Mobile Threat Defense

    -   Per altre informazioni, vedere il [sito Web Better Mobile](https://www.better.mobi/).

## <a name="next-steps"></a>Passaggi successivi

- [Integrare Better Mobile con Intune](better-mobile-mtd-connector-integration.md)

- [Configurare le app di Better Mobile](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Creare criteri di conformità dei dispositivi Better Mobile](mtd-device-compliance-policy-create.md)

- [Abilitare il connettore Better Mobile MTD](mtd-connector-enable.md)