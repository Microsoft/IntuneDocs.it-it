---
title: Attivare la modalità di supervisione di iOS/iPadOS con Microsoft Intune
titleSuffix: ''
description: Informazioni su come attivare la modalità di supervisione di iOS/iPadOS con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d266dbc9fa72b1579e05e7798315e2e718a9797
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413657"
---
# <a name="turn-on-iosipados-supervised-mode"></a>Attivare la modalità con supervisione di iOS/iPadOS


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

La modalità di supervisione di Apple iOS/iPadOS offre agli amministrazioni più opzioni per la gestione dei dispositivi Apple ed è utile per i dispositivi di proprietà dell'azienda distribuiti su vasta scala. Ad esempio, è possibile limitare AirDrop o impedire agli utenti di modificare il nome del dispositivo. Per un elenco di impostazioni che richiedono la modalità di supervisione, vedere [Impostazioni relative alle restrizioni dei dispositivi iOS in Microsoft Intune](../configuration/device-restrictions-ios.md).

Intune supporta la modalità di supervisione nell'ambito del programma [Device Enrollment Program (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) di Apple.

Per un elenco di controlli Apple che richiedono la supervisione, vedere le [informazioni di riferimento sulle impostazioni del payload](http://help.apple.com/configurator/mac/2.4/#/cad5370d089) di Apple.

## <a name="turn-on-supervised-mode-during-enrollment"></a>Attivare la modalità di supervisione durante la registrazione

Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) è possibile attivare la modalità di supervisione per i dispositivi quando si [crea un profilo di registrazione Apple in DEP](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile). In **Impostazioni di gestione dei dispositivi** selezionare la casella **Supervisione eseguita**.

## <a name="turn-on-supervised-mode-after-enrollment"></a>Attivare la modalità di supervisione dopo la registrazione

Dopo la registrazione, l'unico modo per attivare la modalità di supervisione è connettere un dispositivo iOS/iPadOS a un computer Mac e [usare Apple Configurator](../enrollment/apple-configurator-enroll-ios.md), che reimposta il dispositivo. Non è possibile configurare un dispositivo per la modalità di supervisione in Intune dopo la registrazione.

## <a name="identify-a-supervised-device"></a>Identificare un dispositivo supervisionato

Per determinare se un dispositivo è supervisionato, controllare la schermata di blocco o la pagina **Informazioni**:
- Sulla schermata di blocco del dispositivo verrà indicato **Questo iPhone è gestito da: "Nome società"** .
- Nella pagina **Informazioni** del dispositivo, verrà indicato **Questo iPhone è supervisionato. Nome società può monitorare il traffico Internet e localizzare questo dispositivo**.

## <a name="next-steps"></a>Passaggi successivi

Per altre opzioni di gestione dei dispositivi, vedere [Informazioni sulla gestione dei dispositivi in Microsoft Intune](device-management.md)
