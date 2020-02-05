---
title: Configurare Wandera Mobile Security con Intune
titleSuffix: Intune on Azure
description: Come configurare Wandera Mobile Security con Microsoft Intune per controllare l'accesso dei dispositivi mobili alle risorse aziendali.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ee253b50ea525f7d156c77a83f486cf990da030
ms.sourcegitcommit: af384c46ec8d8def6aa32c3b89947748dc6fd28f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2020
ms.locfileid: "76517457"
---
# <a name="wandera-mobile-threat-defense-connector-with-intune"></a>Connettore Wandera Mobile Threat Defense con Intune  

Controllare l'accesso dai dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi eseguita da Wandera. Wandera è una soluzione MTD (Mobile Threat Defense) che si integra con Microsoft Intune.  La valutazione dei rischi viene effettuata in base ai dati di telemetria raccolti dai dispositivi dal servizio Wandera, che includono:
- Vulnerabilità del sistema operativo
- Installazione di app dannose
- Profili di rete dannosi
- Cryptojacking

È possibile configurare criteri di *accesso condizionale* basati sulla valutazione dei rischi di Wandera e abilitati usando i criteri di conformità dei dispositivi di Intune. I criteri di valutazione dei rischi possono consentire o bloccare l'accesso alle risorse aziendali dai dispositivi non conformi in base alle minacce rilevate.  


## <a name="how-do-intune-and-wandera-mobile-threat-defense-help-protect-your-company-resources"></a>In che modo Intune e Wandera Mobile Threat Defense possono proteggere le risorse aziendali?  

L'pp per dispositivi mobili di Wandera viene installata con facilità usando Microsoft Intune. Questa app acquisisce dati di telemetria per file system, stack di rete, dispositivi e applicazioni, se disponibili. Queste informazioni vengono sincronizzate con il servizio cloud Wandera per valutare il livello di rischio per le minacce per dispositivi mobili. Queste classificazioni del livello di rischio sono configurabili in base alle esigenze nella console di Wandera, RADAR.

I criteri di conformità in Intune includono una regola per la valutazione dei rischi MTD basata su Wandera. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati.

Per i dispositivi non conformi, può essere bloccato l'accesso alle risorse, ad esempio Office 365. Gli utenti di dispositivi bloccati riceveranno istruzioni dall'app Wandera per risolvere il problema e ottenere nuovamente l'accesso.

## <a name="supported-platforms"></a>Piattaforme supportate  

Wandera supporta le piattaforme seguenti per i dispositivi registrati in Intune:

- Android 5.0 e versioni successive  
- iOS 10.2 e versioni successive  

Per altre informazioni sulla piattaforma e il dispositivo, vedere il [sito Web Wandera](https://www.wandera.com/mobile-threat-defense/).

## <a name="prerequisites"></a>Prerequisiti  

- Sottoscrizione di Microsoft Intune  
- Azure Active Directory  
- Wandera Mobile Threat Defense (in precedenza Wandera Secure)  

Per altre informazioni, vedere [Wandera Mobile Security](https://www.wandera.com/mobile-security/).
 
## <a name="sample-scenarios"></a>Scenari di esempio

Ecco gli scenari comuni per l'uso di Wandera MTD con Intune.

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose  

Se nei dispositivi vengono rilevate app dannose, come malware, è possibile bloccare l'uso di strumenti comuni nei dispositivi fino alla risoluzione della condizione di minaccia. I blocchi comuni includono:  
- Connessione alla posta elettronica aziendale  
- Sincronizzazione di file aziendali tramite l'app OneDrive for Work  
- Accesso alle app aziendali  

**Bloccare quando vengono rilevate app dannose**:

![Immagine concettuale del rilevamento di app dannose](./media/wandera-mtd-connector/wandera-malicious-apps-blocked.png)  

**Accesso concesso dopo la correzione**: 

![Immagine concettuale dell'accesso concesso dopo la correzione](./media/wandera-mtd-connector/wandera-malicious-apps-unblocked.png)


### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce per la rete  

Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle e proteggere l'accesso a reti Wi-Fi in base al livello di rischio del dispositivo.  

**Bloccare l'accesso alla rete tramite Wi-Fi**:  

![Bloccare l'accesso alla rete tramite Wi-Fi](./media/wandera-mtd-connector/wandera-network-wifi-blocked.png)

**Accesso concesso dopo la correzione**:  

![Accesso concesso dopo la correzione](./media/wandera-mtd-connector/wandera-network-wifi-unblocked.png)  

## <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare le minacce alla rete, ad esempio attacchi di tipo man-in-the-middle, e impedire la sincronizzazione dei file aziendali in base al rischio per il dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete**:  

![Bloccare SharePoint Online quando vengono rilevate minacce per la rete](./media/wandera-mtd-connector/wandera-network-spo-blocked.png)  


**Accesso concesso dopo la correzione**:  

![Esempio di accesso concesso dopo la risoluzione per SharePoint](./media/wandera-mtd-connector/wandera-network-spo-unblocked.png)  

## <a name="next-steps"></a>Passaggi successivi

- [Integrare Wandera con Intune](wandera-mtd-connector-integration.md)
- [Configurare le app di Wandera](mtd-apps-ios-app-configuration-policy-add-assign.md)
- [Creare criteri di conformità dei dispositivi per Wandera](mtd-device-compliance-policy-create.md)
- [Abilitare il connettore MTD Wandera](mtd-connector-enable.md)
