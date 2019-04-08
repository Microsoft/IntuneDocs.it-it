---
title: Confrontare le opzioni per la gestione di PC Windows
titleSuffix: Microsoft Intune
description: Registrazione di dispositivi iOS di proprietà dell'azienda usando il programma Device Enrollment Program (DEP) di Apple o Apple Configurator.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0dbd89a2a281f3a4d80737c284fb1a1ca5004616
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799423"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Confrontare la gestione dei PC Windows come computer o come dispositivi mobili

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Le organizzazioni possono usare Microsoft Intune per gestire i PC Windows come dispositivi mobili con la soluzione di gestione dei dispositivi mobili (MDM) o come computer con il software client di Intune.  Si consiglia ai clienti di usare la soluzione di gestione MDM laddove possibile. Per comprendere meglio le differenze tra queste opzioni, tuttavia, il grafico seguente confronta le due opzioni di gestione.

|**Capacità / Scenario** |**Windows come computer**<br>Client software di Intune | **Windows come dispositivo mobile**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**Sistemi operativi** |Windows 10, Windows 8+, Windows 7, Windows Vista | Windows 10+ |
|**Supporto del portale di Intune** |[Console Silverlight](https://manage.microsoft.com)|[Portale di Azure](https://portal.azure.com) |
|**Accesso condizionale**|Non disponibile|Disponibile <br>[Che cos'è l'accesso condizionale?](conditional-access.md)|
|**Registrazione in blocco**|Non disponibile|Disponibile <br>[Registrazione in blocco per dispositivi Windows](windows-bulk-enroll.md)|
|**Profili di dispositivo**|Non disponibile|Disponibile <br>[Informazioni sui profili di dispositivo in Microsoft Intune](device-profiles.md)|
|**Registrazione senza agente**|Non disponibile |Disponibile<br>[Registrare i dispositivi Windows](windows-enroll.md)|
|**Gestione aggiornamenti software**| Aggiornamenti di Windows e aggiornamenti delle app Microsoft<br>[Mantenere i PC Windows aggiornati con gli aggiornamenti software](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|Microsoft Store per le aziende per gli aggiornamenti di Windows 10 e delle app Microsoft<br> [Configurare le impostazioni di Windows Update for Business](windows-update-for-business-configure.md) |
|**Gestione delle licenze software**|Disponibile <br>[Gestire i contratti di licenza del software per PC Windows](manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)|Microsoft Store per le aziende (solo app .appx)<br>[Gestire le app acquistate da Microsoft Store per le aziende](windows-store-for-business.md)|
|**Inventario**|Disponibile <br>[Visualizzare l'inventario software e hardware per PC Windows](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md)|Disponibile <br>[Come monitorare le informazioni sulle app](apps-monitor.md)<br>[Che cos'è la gestione dei dispositivi?](device-management.md)|
|**Criteri di Windows Firewall**|Disponibile <br>[Proteggere i PC Windows con criteri di Windows Firewall](help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md) |Disponibile <br>[Windows Defender Firewall](endpoint-protection-windows-10.md#windows-defender-firewall)|
|**Protezione antimalware**|Endpoint Protection<br>[Proteggere i PC Windows con Endpoint Protection](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|Windows Defender<br>[Abilitare Windows Defender](advanced-threat-protection.md)|
|**Assistenza remota** |TeamViewer<br>[Richiedere e fornire assistenza remota per i PC Windows](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md)|TeamViewer<br> [Usare TeamViewer per l'amministrazione remota dei dispositivi di Intune](device-profile-android-teamviewer.md) |
|**Distribuzione di app** | Non disponibile per Microsoft Store per le aziende,<br>solo .exe, .appx e .msi con più file<br>[Aggiungere app per i PC Windows che eseguono il software client di Intune](add-apps-for-windows-pcs-in-microsoft-intune.md)|Disponibile per le app di Microsoft Store e le app line-of-business<br>[Come aggiungere app di Windows Store](store-apps-windows.md)<br>[Come aggiungere app line-of-business Windows](lob-apps-windows.md)|
|**Protezione delle app**|Non disponibile|Disponibile <br>[Che cosa sono i criteri di protezione delle app?](app-protection-policy.md)|
|**Attestazione dell'integrità**|Non disponibile|Disponibile|


### <a name="advantages-of-mdm-windows-pc-management"></a>Vantaggi della gestione MDM di PC Windows
La gestione dei PC Windows con le funzionalità moderne di gestione dei dispositivi mobili offre i vantaggi seguenti:
- **Scalabilità** - La gestione MDM viene ridimensionata in base alla gestione del cloud di Intune. Il software client di Intune è limitato a 7000 PC.
- **Semplicità** - Usa le funzionalità di gestione moderne incluse nel sistema operativo senza basarsi su un client software scaricato
- **Coerenza** - I PC Windows vengono gestiti come tutti gli altri dispositivi mobili nell'organizzazione
<!-- - **Cloud optimization** - -->
