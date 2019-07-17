---
title: Connettore Mobile Threat Defense Pradeo con Intune
titleSuffix: Intune on Azure
description: Configurare il connettore Mobile Threat Defense Padreo con Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: cde4d389-1770-4226-85a3-a2f3b3fb92a3
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ccfe9ccd186f38a971aa6bac5d58bf61e44450d
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882757"
---
# <a name="pradeo-mobile-threat-defense-connector-with-intune"></a>Connettore Mobile Threat Defense Pradeo con Intune

È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale basato sulla valutazione dei rischi condotta da Pradeo, una soluzione Mobile Threat Defense (MTD) integrata in Microsoft Intune. La valutazione dei rischi viene eseguita in base ai dati di telemetria raccolti dai dispositivi che eseguono l'app Pradeo.

È possibile configurare criteri di accesso condizionale in base alla valutazione dei rischi di Pradeo abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

## <a name="how-do-intune-and-pradeo-help-protect-your-company-resources"></a>In che modo Intune e Pradeo consentono di proteggere le risorse aziendali?

L'app Pradeo per Android e iOS acquisisce i dati di telemetria, se disponibili, relativi al file system, allo stack di rete, al dispositivo e alle applicazioni e li invia al servizio cloud Pradeo per la valutazione del livello di rischio delle minacce per dispositivi mobili.

I criteri di conformità dei dispositivi di Intune includono una regola per Pradeo Mobile Threat Defense, basata sulla valutazione dei rischi eseguita da Pradeo. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati. Se il dispositivo risulta non conforme, l'accesso degli utenti a risorse aziendali come Exchange Online e SharePoint Online viene bloccato. Gli utenti ricevono inoltre istruzioni dall'app Pradeo installata nei relativi dispositivi per risolvere il problema e ottenere nuovamente l'accesso alle risorse aziendali.

## <a name="sample-scenarios"></a>Scenari di esempio

Ecco alcuni scenari comuni.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose

Se nei dispositivi vengono rilevate app dannose, come malware, è possibile impedire ai dispositivi di eseguire le azioni seguenti fino alla risoluzione della condizione di minaccia:

- Connessione alla posta elettronica aziendale

- Sincronizzazione di file aziendali tramite l'app OneDrive for Work

- Accesso alle app aziendali

**Bloccare quando vengono rilevate app dannose:**

![Immagine concettuale del rilevamento di app dannose](./media/pradeo_maliciousapps_blocked.png)

**Accesso concesso dopo la correzione:**

![App dannose rilevate e accesso consentito](./media/pradeo_maliciousapps_unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete

Rilevare le minacce per la rete, ad esempio attacchi **Man-in-the-middle** e proteggere l'accesso alle reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**

![Bloccare l'accesso alla rete tramite Wi-Fi](./media/pradeo_network_wifi_blocked.png)

**Accesso concesso dopo la correzione:**

![Immagine concettuale dell'accesso concesso dopo la correzione](./media/pradeo_network_wifi_unblocked.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare le minacce per la rete, ad esempio attacchi **Man-in-the-middle**, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Bloccare SharePoint Online quando vengono rilevate minacce per la rete](./media/pradeo_network_spo_blocked.png)

**Accesso concesso dopo la correzione:**

![Immagine concettuale dell'accesso concesso dopo la correzione per l'esempio di SharePoint](./media/pradeo_network_spo_unblocked.png)

## <a name="supported-platforms"></a>Piattaforme supportate

- **Android 4.0.3 e versioni successive**

- **iOS 7 e versioni successive**

## <a name="prerequisites"></a>Prerequisiti

- Azure Active Directory Premium

- Sottoscrizione di Microsoft Intune

- Sottoscrizione di Pradeo Security Mobile Threat Defense

  - Per altre informazioni, vedere il [sito Web Pradeo](https://www.pradeo.com/en-US/mobile-threat-protection).

## <a name="next-steps"></a>Passaggi successivi

- [Integrare Pradeo con Intune](pradeo-mtd-connector-integration.md)

- [Configurare app Pradeo](mtd-apps-ios-app-configuration-policy-add-assign.md)

- [Creare criteri di conformità per dispositivi Pradeo](mtd-device-compliance-policy-create.md)

- [Abilitare il connettore MTD Pradeo](mtd-connector-enable.md)
