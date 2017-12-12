---
title: Profili certificato per l'accesso alle risorse
description: Protezione VPN, Wi-Fi e di accesso alla posta elettronica con un certificato installato su ogni dispositivo dell'utente.
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 02/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8cbb8499-611d-4217-a7b4-e9b864785dd0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 76083268d3c7ed43cea0bc0d9751ae9c37c7227b
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="secure-resource-access-with-certificate-profiles-in-microsoft-intune"></a>Proteggere l'accesso alle risorse con i profili certificato in Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Quando si concede agli utenti l'accesso alle risorse aziendali tramite profili VPN, Wi-Fi o di posta elettronica, è possibile proteggere tale accesso con un certificato installato in ogni dispositivo utente. Ecco come funziona:

1. Assicurarsi che sia implementata l'infrastruttura di certificazione corretta, come descritto in [Configurare l'infrastruttura di certificazione per SCEP](configure-certificate-infrastructure-for-scep.md) e [Configurare l'infrastruttura di certificazione](configure-certificate-infrastructure-for-pfx.md).

2. Installare un certificato radice o un certificato dell'autorità di certificazione (CA) intermedio in ogni dispositivo, in modo che il dispositivo riconosca la legittimità dell'autorità di certificazione. A tale scopo, creare e distribuire un **profilo certificato attendibile**. Quando si distribuisce questo profilo, i dispositivi da gestire con Intune richiederanno e riceveranno il certificato radice. È necessario creare un profilo separato per ogni piattaforma. Il **profilo certificato attendibile** è disponibile per le piattaforme:
 -  iOS 8.0 e versioni successive
 -  Mac OS X 10.9 e versioni successive
 -  Android 4.0 e versioni successive
 -  Android for Work
 -  Windows 8.1 e versioni successive
 -  Windows Phone 8.1 e versioni successive

3. Creare i profili certificato in modo che i dispositivi richiedano un certificato da usare per l'autenticazione dell'accesso a VPN, Wi-Fi e posta elettronica, come descritto in [Configure Intune certificate profiles](configure-intune-certificate-profiles.md) (Configurare i profili certificato di Intune). È possibile creare e distribuire un **profilo certificato PKCS #12 (.PFX)** *o* un **profilo certificato SCEP** per i dispositivi in esecuzione su queste piattaforme:

  -  iOS 8.0 e versioni successive
  -  Android 4.0 e versioni successive
  -  Android for Work
  -  Windows 10 (per dispositivi desktop e mobili) e versioni successive

  Usare un **profilo certificato SCEP** per i dispositivi in esecuzione su queste piattaforme:
    -   Mac OS X 10.9 e versioni successive
    -   Windows Phone 8.1

È necessario creare un profilo separato per ogni piattaforma. Quando si crea il profilo, questo viene associato al **profilo del certificato radice attendibile** già creato.

> [!NOTE]           
> - Se non è presente un'autorità di certificazione globale (enterprise), è necessario crearla.
>- Se, in base alle piattaforme dei dispositivi, si decide di usare il profilo Simplified Certificate Enrollment Protocol (SCEP), è necessario anche configurare un server del servizio Registrazione dispositivi di rete (NDES).
>-  Se si prevede di usare i profili SCEP o PFX, è necessario scaricare e configurare Connettore di certificati di Microsoft Intune.
>-  Per informazioni sulla configurazione di tutti i servizi richiesti, vedere [Configurare l'infrastruttura di certificazione per SCEP](configure-certificate-infrastructure-for-scep.md) o [Configurare l'infrastruttura di certificazione per PFX](configure-certificate-infrastructure-for-pfx.md).

### <a name="next-steps"></a>Passaggi successivi
- [Configurare l'infrastruttura di certificazione per SCEP](configure-certificate-infrastructure-for-scep.md)
- [Configurare l'infrastruttura di certificazione per PFX](configure-certificate-infrastructure-for-pfx.md)
- [Configurare i profili certificato di Intune](configure-intune-certificate-profiles.md)
