---
title: Connettore Lookout MTD con Microsoft Intune
titleSuffix: Microsoft Intune
description: Informazioni sull'integrazione di Intune con Lookout Mobile Threat Defense (MTD) per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/09/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3a730a5d-2a90-42b0-aa28-aadfc7a18788
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cf507ba470013bddf4809b6ad6ad54b4cb52d9d
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61507243"
---
# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Connettore Lookout Mobile Threat Defense con Intune

È possibile controllare l'accesso dai dispositivi mobili alle risorse aziendali in base alla valutazione dei rischi condotta da Lookout, una soluzione di protezione dalle minacce per dispositivi mobili integrata in Microsoft Intune. La valutazione dei rischi viene effettuata in base ai dati di telemetria raccolti dai dispositivi dal servizio Lookout, che includono:
- Vulnerabilità del sistema operativo
- Installazione di app dannose
- Profili di rete dannosi

È possibile configurare criteri di accesso condizionale basati sulla valutazione dei rischi di Lookout e abilitati tramite i criteri di conformità di Intune. Con le impostazioni disponibili è possibile autorizzare o bloccare i dispositivi non conformi in base alle minacce rilevate.

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

![Immagine concettuale dei criteri che bloccano l'accesso a causa di app dannose](./media/malicious-apps-blocked.png)

**Accesso concesso dopo la correzione:**

![Immagine concettuale in cui l'accesso viene concesso ai dispositivi dopo la correzione](./media/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete
Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle e proteggere l'accesso a reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**

![Immagine che illustra il blocco dell'accesso alla rete Wi-Fi in base alle minacce per la rete](./media/network-wifi-blocked.png)

**Accesso concesso dopo la correzione:**

![Immagine concettuale dell'accesso condizionale che consente l'accesso dopo la correzione](./media/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Immagine concettuale del blocco dell'accesso a SharePoint Online](./media/network-spo-blocked.png)


**Accesso concesso dopo la correzione:**

![Immagine concettuale della concessione dell'accesso dopo la risoluzione della condizione di minaccia per la rete](./media/network-spo-unblocked.png)

## <a name="next-steps"></a>Passaggi successivi
Ecco i passaggi principali per l'implementazione di questa soluzione:
1.  [Configurare l'integrazione di Lookout](lookout-mtd-connector-integration.md)
2.  [Abilitare Lookout Mobile Threat Defense in Intune](mtd-connector-enable.md)
3.  [Aggiungere e assegnare l'app Lookout for Work](mtd-apps-ios-app-configuration-policy-add-assign.md)
4.  [Configurare i criteri di conformità dei dispositivi di Lookout](mtd-device-compliance-policy-create.md)
