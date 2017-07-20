---
title: Confrontare le opzioni per la gestione di PC Windows
description: "Registrazione di dispositivi iOS di proprietà dell'azienda usando il programma di registrazione dispositivi di Apple o Apple Configurator"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 05/11/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 560ce922fa58e759157358c6b7348fe0388ce408
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2017
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Confrontare la gestione dei PC Windows come computer o come dispositivi mobili

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Le organizzazioni possono usare Microsoft Intune per gestire i PC Windows come dispositivi mobili con la soluzione di gestione dei dispositivi mobili (MDM) o come computer con il software client di Intune.  Si consiglia ai clienti di usare la soluzione di gestione MDM laddove possibile. Per comprendere meglio le differenze tra queste opzioni, tuttavia, il grafico seguente confronta le due opzioni di gestione.

|**Capacità / Scenario** |**Windows come computer**<br>Client software di Intune | **Windows come dispositivo mobile**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Sistemi operativi** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Supporto del portale di Intune** |[Console Silverlight](https://manage.microsoft.com)|[Portale di Azure](https://portal.azure.com) |
|**Accesso condizionale**|Non disponibile|Disponibile <br>[Che cos'è l'accesso condizionale?](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**Registrazione in blocco**|Non disponibile|Disponibile <br>[Registrazione in blocco per dispositivi Windows](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**Profili di dispositivo**|Non disponibile|Disponibile <br>[Informazioni sui profili di dispositivo in Microsoft Intune](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**Registrazione senza agente**|Non disponibile |Disponibile<br>[Registrare i dispositivi Windows](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**Gestione aggiornamenti software**| Aggiornamenti di Windows e aggiornamenti delle app Microsoft<br>[Mantenere i PC Windows aggiornati con gli aggiornamenti software](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Microsoft Store per le aziende per gli aggiornamenti di Windows 10 e delle app Microsoft<br> [Configurare le impostazioni di Windows Update for Business](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**Gestione delle licenze software**|Disponibile <br>[Gestire i contratti di licenza del software per PC Windows](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|Microsoft Store per le aziende (solo app .appx)<br>[Gestire le app acquistate da Windows Store per le aziende](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**Inventario**|Disponibile <br>[Visualizzare l'inventario software e hardware per PC Windows](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|Disponibile <br>[Come monitorare le informazioni sulle app](https://docs.microsoft.com/intune/apps-monitor)<br>[Che cos'è la gestione dei dispositivi?](https://docs.microsoft.com/intune/device-management)|
|**Criteri di Windows Firewall**|Disponibile <br>[Proteggere i PC Windows con criteri di Windows Firewall](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |Non disponibile|
|**Protezione antimalware**|Endpoint Protection<br>[Proteggere i PC Windows con Endpoint Protection](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Impostazioni di Windows Defender](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**Assistenza remota** |TeamViewer<br>[Richiedere e fornire assistenza remota per i PC Windows](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|Non disponibile |
|**Distribuzione di app** | Non disponibile per Microsoft Store per le aziende,<br>solo .exe, .appx e .msi con più file<br>[Aggiungere app per i PC Windows che eseguono il software client di Intune](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|Disponibile per le app di Microsoft Store e le app line-of-business<br>[Come aggiungere app di Windows Store](https://docs.microsoft.com/intune-azure/manage-apps/windows-store-app)<br>Distribuzione di app Microsoft e app Win32 presto disponibili |
|**Protezione delle app**|Non disponibile|Disponibile <br>[Che cosa sono i criteri di protezione delle app?](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|


### <a name="advantages-of-mdm-windows-pc-management"></a>Vantaggi della gestione MDM di PC Windows
La gestione dei PC Windows con le funzionalità moderne di gestione dei dispositivi mobili offre i vantaggi seguenti:
- **Scalabilità** - La gestione MDM viene ridimensionata in base alla gestione del cloud di Intune. Il software client di Intune è limitato a 7000 PC.
- **Semplicità** - Usa le funzionalità di gestione moderne incluse nel sistema operativo senza basarsi su un client software scaricato
- **Coerenza** - I PC Windows vengono gestiti come tutti gli altri dispositivi mobili nell'organizzazione
<!-- - **Cloud optimization** - -->
