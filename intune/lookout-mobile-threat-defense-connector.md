---
title: Connettore Lookout Mobile Threat Defense con Intune
titlesuffix: Azure portal
description: Configurare il connettore Lookout Mobile Threat Defense con Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 06/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 41270fb217c87880e67c1c5e0adf319576031126
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Connettore Lookout Mobile Threat Defense con Intune

È possibile controllare l'accesso dai dispositivi mobili alle risorse aziendali in base alla valutazione dei rischi condotta da Lookout, una soluzione di protezione dalle minacce per dispositivi mobili integrata in Microsoft Intune. La valutazione dei rischi viene effettuata in base ai dati di telemetria raccolti dai dispositivi dal servizio Lookout, che includono:
- Vulnerabilità del sistema operativo
- Installazione di app dannose
- Profili di rete dannosi

È possibile configurare criteri di accesso condizionale basati sulla valutazione dei rischi di Lookout e abilitati tramite i criteri di conformità di Intune. Le impostazioni consentono di autorizzare o bloccare i dispositivi non conformi in base alle minacce rilevate.

## <a name="how-do-intune-and-lookout-mobile-threat-defense-help-protect-company-resources"></a>In che modo Intune e Lookout Mobile Threat Defense possono proteggere le risorse aziendali?
L'app per dispositivi mobili di Lookout, **Lookout for Work**, viene installata ed eseguita nei dispositivi mobili. Questa app consente di acquisire dati di telemetria per il file system, lo stack di rete, il dispositivo e le applicazioni (se disponibili) e di inviarli al servizio cloud Lookout per la valutazione del livello di rischio per le minacce per dispositivi mobili. È possibile modificare le classificazioni del livello di rischio per le minacce nella console di Lookout in base alle proprie esigenze.  

I criteri di conformità in Intune includono una regola per Lookout Mobile Threat Defense, basata sulla valutazione dei rischi di Lookout. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati.

Se il dispositivo risulta non conforme, è possibile bloccare l'accesso a risorse come Exchange Online e SharePoint Online. Gli utenti di dispositivi bloccati riceveranno istruzioni per risolvere il problema e riottenere l'accesso. Queste istruzioni vengono fornite dall'app Lookout for Work.

## <a name="supported-platforms"></a>Piattaforme supportate
Lookout supporta le piattaforme seguenti per i dispositivi registrati in Intune:
* **Android 4.1 e versioni successive**
* **iOS 8 e versioni successive** Per altre informazioni sulle piattaforme e le lingue supportate, visitare il [sito Web di Lookout](https://personal.support.lookout.com/hc/articles/114094140253).

## <a name="prerequisites"></a>Prerequisiti
* Sottoscrizione di Microsoft Intune
* Azure Active Directory
* Sottoscrizione aziendale a Lookout Mobile EndPoint Security  

Per altre informazioni, vedere [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Scenari di esempio

Ecco gli scenari comuni per l'uso di Lookout Mobile Threat Defense con Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose
Se nei dispositivi vengono rilevate app dannose, come malware, è possibile impedire ai dispositivi di eseguire le operazioni seguenti fino alla risoluzione della condizione di minaccia:
* Connessione alla posta elettronica aziendale
* Sincronizzazione di file aziendali tramite l'app OneDrive for Work
* Accesso alle app aziendali

**Bloccare quando vengono rilevate app dannose:**

![diagramma che illustra i criteri di accesso condizionale che bloccano l'accesso quando il dispositivo viene indicato come non conforme a causa della presenza di app dannose su di esso](./media/malicious-apps-blocked.png)

**Accesso concesso dopo la correzione:**

![diagramma che mostra i criteri di accesso condizionale che concedono l'accesso quando il dispositivo risulta conforme dopo la correzione](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete
Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle e proteggere l'accesso a reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**

![diagramma che illustra i criteri di accesso condizionale che bloccano l'accesso alla rete Wi-Fi in base alle minacce per la rete](./media/network-wifi-blocked.png)

**Accesso concesso dopo la correzione:**

![diagramma che mostra l'accesso condizionale che consente l'accesso dopo la risoluzione della condizione di minaccia](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Diagramma che mostra l'accesso condizionale che blocca l'accesso del dispositivo a SharePoint Online in base al rilevamento di minacce](./media/network-spo-blocked.png)


**Accesso concesso dopo la correzione:**

![Diagramma che mostra l'accesso condizionale che consente l'accesso dopo la risoluzione della condizione di minaccia per la rete](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>Passaggi successivi
Ecco i passaggi principali per l'implementazione di questa soluzione:
1.  [Configurare l'integrazione di Lookout](lookout-mtd-connector-integration.md)
2.  [Abilitare Lookout Mobile Threat Defense in Intune](mtd-connector-enable.md)
3.  [Aggiungere e assegnare l'app Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Configurare i criteri di conformità dei dispositivi di Lookout](mtd-device-compliance-policy-create.md)
