---
title: Connettore Lookout Mobile Threat Defense | Microsoft Docs
description: Proteggere l&quot;accesso alle risorse aziendali in base al rischio di dispositivi, reti e applicazioni con il connettore Lookout Mobile Threat Defense e Intune.
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6f78150b6c3821f6e9822ccfa905ac367bd359ad
ms.openlocfilehash: 9e00e60472c8ba9f10a6071c42a53f58dcc00a08
ms.lasthandoff: 03/02/2017


---

# <a name="lookout-mobile-threat-defense-connector-with-intune"></a>Connettore Lookout Mobile Threat Defense con Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

È possibile controllare l'accesso dai dispositivi mobili alle risorse aziendali in base alla valutazione dei rischi condotta da Lookout, una soluzione di protezione dalle minacce per i dispositivi integrata in Microsoft Intune. La valutazione dei rischi viene effettuata in base ai dati di telemetria raccolti dai dispositivi dal servizio Lookout, che includono:
- Vulnerabilità del sistema operativo
- Installazione di app dannose
- Profili di rete dannosi

È possibile configurare criteri di accesso condizionale basati sulla valutazione dei rischi di Lookout e abilitati tramite i criteri di conformità di Intune. Le impostazioni consentono di autorizzare o bloccare i dispositivi non conformi in base alle minacce rilevate.

## <a name="how-do-intune-and-lookout-device-threat-protection-help-protect-company-resources"></a>In che modo la protezione dalle minacce per il dispositivo di Intune e Lookout può tutelare le risorse aziendali?
L'app per dispositivi mobili di Lookout, **Lookout for Work**, viene installata ed eseguita nei dispositivi mobili. Questa app consente di acquisire dati di telemetria per il file system, lo stack di rete, il dispositivo e le applicazioni (se disponibili) e di inviarli al servizio cloud Lookout per la valutazione del livello di rischio per le minacce per dispositivi mobili. È possibile modificare le classificazioni del livello di rischio per le minacce nella console di Lookout in base alle proprie esigenze.  

I criteri di conformità in Intune includono una regola per la protezione dalle minacce per dispositivi mobili di Lookout, basata sulla valutazione dei rischi di Lookout. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati.

Se il dispositivo risulta non conforme, è possibile bloccare l'accesso a risorse come Exchange Online e SharePoint Online. Gli utenti di dispositivi bloccati riceveranno istruzioni per risolvere il problema e riottenere l'accesso. Queste istruzioni vengono fornite dall'app Lookout for Work.

## <a name="supported-platforms"></a>Piattaforme supportate:
Lookout supporta le piattaforme seguenti per i dispositivi registrati in Intune:
* **Android 4.1 e versioni successive**
* **iOS 8 e versioni successive** Per altre informazioni sulle piattaforme e le lingue supportate, visitare il [sito Web di Lookout](https://personal.support.lookout.com/hc/en-us/articles/114094140253).

## <a name="prerequisites"></a>Prerequisiti:
* Sottoscrizione di Microsoft Intune
* Azure Active Directory
* Sottoscrizione aziendale a Lookout Mobile EndPoint Security  

Per altre informazioni, vedere [Lookout Mobile EndPoint Security](https://www.lookout.com/products/mobile-endpoint-security)

## <a name="sample-scenarios"></a>Scenari di esempio
Questi sono alcuni degli scenari comuni:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose
Se nei dispositivi vengono rilevate app dannose, come malware, è possibile impedire ai dispositivi di eseguire le operazioni seguenti fino alla risoluzione della condizione di minaccia:
* Connessione alla posta elettronica aziendale
* Sincronizzazione di file aziendali tramite l'app OneDrive for Work
* Accesso alle app aziendali

**Bloccare l'accesso quando vengono rilevate app dannose:**
![diagramma che mostra i criteri di accesso condizionale che bloccano l'accesso quando il dispositivo viene determinato come non conforme a causa della presenza di app dannose](../media/mtp/malicious-apps-blocked.png)

**Accesso concesso dopo la risoluzione:**

![diagramma che mostra i criteri di accesso condizionale che concedono l'accesso quando il dispositivo risulta conforme dopo la correzione](../media/mtp/malicious-apps-unblocked.png)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete
Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle e proteggere l'accesso a reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**
![diagramma che mostra l'accesso condizionale che blocca l'accesso tramite Wi-Fi in presenza di minacce di rete](../media/mtp/network-wifi-blocked.png)

**Accesso concesso dopo la risoluzione:**

![diagramma che mostra l'accesso condizionale che consente l'accesso dopo la risoluzione della condizione di minaccia](../media/mtp/network-wifi-unblocked.png)
### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare le minacce per la rete, ad esempio attacchi man-in-the-middle, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Diagramma che mostra l'accesso condizionale che blocca l'accesso del dispositivo a SharePoint Online in base al rilevamento di minacce](../media/mtp/network-spo-blocked.png)


**Accesso concesso dopo la risoluzione:**

![Diagramma che mostra l'accesso condizionale che consente l'accesso dopo la risoluzione della condizione di minaccia per la rete](../media/mtp/network-spo-unblocked.png)

## <a name="next-steps"></a>Passaggi successivi
Ecco i passaggi principali per l'implementazione di questa soluzione:
1.    [Set up your subscription with device threat protection](device-threat-protection-subscription-setup.md) (Configurare la sottoscrizione per la protezione dalle minacce)
2.    [Enable device threat protection connection in Intune](device-threat-protection-enable.md) (Abilitare la protezione dalle minacce in Intune)
3.  [Configure and deploy the device threat protection app](device-threat-protection-apps.md) (Configurare e distribuire l'app per la protezione dalle minacce per i dispositivi)
4.    [Configure device threat protection compliance policy](device-threat-protection-policy.md) (Configurare i criteri di conformità della protezione dalle minacce per i dispositivi)
5.    [Troubleshoot device threat protection integration](http://docs.microsoft.com/intune/troubleshoot/device-threat-protection-troubleshooting) (Risolvere i problemi di integrazione della protezione dalle minacce per i dispositivi)

