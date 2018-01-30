---
title: Connettore Skycure con Intune
titlesuffix: Azure portal
description: Integrazione del connettore Skycure con Intune
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: df4ce3f6-a093-432c-ab86-7a83865e389e
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: df60b45ede53190660733d3879ab6c020e5448b1
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2018
---
# <a name="skycure-mobile-threat-defense-connector"></a>Connettore Skycure Mobile Threat Defense

È possibile controllare l'accesso dei dispositivi mobili alle risorse aziendali usando l'accesso condizionale in base alla valutazione dei rischi condotta da Skycure, una soluzione di protezione dalle minacce per dispositivi mobili integrata in Microsoft Intune. La valutazione dei rischi viene effettuata in base ai dati di telemetria raccolti dai dispositivi che eseguono Skycure, inclusi i seguenti:

-   Difesa fisica

-   Difesa della rete

-   Difesa delle applicazioni

-   Difesa delle vulnerabilità

È possibile configurare criteri di accesso condizionale in base alla valutazione dei rischi di Skycure abilitata tramite i criteri di conformità dei dispositivi di Intune, che possono essere usati per consentire o impedire ai dispositivi non conformi di accedere alle risorse aziendali a seconda delle minacce rilevate.

## <a name="how-do-intune-and-skycure-help-protect-your-company-resources"></a>In che modo Intune e Skycure consentono di proteggere le risorse aziendali?

L'app Skycure per dispositivi mobili Android e iOS acquisisce (se disponibili) i dati di telemetria relativi al file system, allo stack di rete, al dispositivo e alle applicazioni e li invia al servizio cloud Skycure per la valutazione del livello di rischio delle minacce per dispositivi mobili.

I criteri di conformità dei dispositivi di Intune includono una regola per Skycure Mobile Threat Defense, basata sulla valutazione dei rischi eseguita da Skycure. Quando questa regola è abilitata, Intune valuta la conformità del dispositivo in base ai criteri abilitati.

Se il dispositivo risulta non conforme, l'accesso a risorse come Exchange Online e SharePoint Online viene bloccato. Gli utenti di dispositivi bloccati riceveranno istruzioni dall'app Skycure per dispositivi mobili per risolvere il problema e ottenere nuovamente l'accesso alle risorse aziendali.

Intune supporta due modalità di integrazione con Skycure:

-   **Installazione di base**, una modalità di sola lettura che consente la visibilità di Skycure per i dispositivi in Intune.

-   **Integrazione completa**, una modalità che consente a Skycure di segnalare a Intune i dettagli relativi ai rischi dei dispositivi e agli eventi imprevisti per la sicurezza.

## <a name="sample-scenarios"></a>Scenari di esempio

Ecco alcuni scenari comuni:

### <a name="control-access-based-on-threats-from-malicious-apps"></a>Controllare l'accesso in base alle minacce da parte di app dannose

Se nei dispositivi vengono rilevate app dannose, come malware, è possibile bloccare i dispositivi finché la condizione di minaccia non viene risolta:

-   Connessione alla posta elettronica aziendale

-   Sincronizzazione di file aziendali tramite l'app OneDrive for Work

-   Accesso alle app aziendali

**Bloccare quando vengono rilevate app dannose:**

![App dannose rilevate](./media/skycure-arch-1.png)

**Accesso concesso dopo la correzione:**

![App dannose rilevate e accesso consentito](./media/skycure-arch-2.png)

### <a name="control-access-based-on-threat-to-network"></a>Controllare l'accesso in base alle minacce alla rete

Rilevare minacce nella rete, come attacchi di tipo **Man-in-the-middle**, e proteggere l'accesso alle reti Wi-Fi in base al livello di rischio del dispositivo.

**Bloccare l'accesso alla rete tramite Wi-Fi:**

![Bloccare l'accesso alla rete tramite Wi-Fi](./media/skycure-arch-3.png)

**Accesso concesso dopo la correzione:**

![Accesso concesso dopo la risoluzione](./media/skycure-arch-4.png)

### <a name="control-access-to-sharepoint-online-based-on-threat-to-network"></a>Controllare l'accesso a SharePoint Online in base alle minacce alla rete

Rilevare minacce nella rete, come attacchi di tipo **Man-in-the-middle**, e impedire la sincronizzazione dei file aziendali in base al livello di rischio del dispositivo.

**Bloccare SharePoint Online quando vengono rilevate minacce per la rete:**

![Bloccare SharePoint Online quando vengono rilevate minacce per la rete](./media/skycure-arch-5.png)

**Accesso concesso dopo la correzione:**

![Accesso concesso dopo la risoluzione per l'esempio di SharePoint](./media/skycure-arch-6.png)

## <a name="supported-platforms"></a>Piattaforme supportate

-   **Android 4.1 e versioni successive**

-   **iOS 8 e versioni successive**

## <a name="pre-requisites"></a>Prerequisiti

-   Azure Active Directory Premium

-   Sottoscrizione di Microsoft Intune

-   Sottoscrizione di Skycure Mobile Threat Defense

Per altre informazioni, visitare il [sito Web di Skycure](https://www.skycure.com/skycure-microsoft-integration/).

## <a name="next-steps"></a>Passaggi successivi

Questi sono i passaggi da completare per integrare Intune con Skycure:

- [Configurare l'integrazione di Skycure con Intune](skycure-mtd-connector-integration.md)

- [Add and assign Skycure apps, Microsoft Authenticator and iOS app configuration policy](mtd-apps-ios-app-configuration-policy-add-assign.md) (Aggiungere e assegnare app Skycure e Microsoft Authenticator e criteri di configurazione delle app iOS)

- [Creare criteri di conformità dei dispositivi Mobile Threat Defense (MTD) con Intune](mtd-device-compliance-policy-create.md)

- [Abilitare Mobile Threat Defense in Intune](mtd-connector-enable.md)
