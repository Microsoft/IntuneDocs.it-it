---
title: Cancellare un dispositivo macOS
titleSuffix: Microsoft Intune
description: Informazioni su come cancellare tutti i dati, incluso il sistema operativo, da un dispositivo macOS.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.reviewer: coferro
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bc2ba86ddb36355bca8328b9c205047abf1b4ff
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907271"
---
# <a name="erase-all-data-from-a-macos-device"></a>Cancellare tutti i dati da un dispositivo macOS

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

È possibile cancellare tutti i dati da un dispositivo macOS, incluso il sistema operativo. Il dispositivo verrà rimosso anche dalla gestione di Intune. Nessun avviso verrà visualizzato dall'utente finale.

1. Nell'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) scegliere **Dispositivi** > **Tutti i dispositivi** > scegliere il dispositivo che si vuole cancellare.
2. Fare clic su **Altro** > **Cancella** e quindi specificare un numero di 6 cifre per il **PIN di ripristino**. Questo è il PIN che è necessario dare all'utente per poter reinstallare il sistema operativo nel dispositivo. Assicurarsi di prendere nota di questo PIN perché non sarà visibile una volta completata l'azione di cancellazione.
![Screenshot](./media/device-erase/providepin.png)
3. Fare clic su **OK** per cancellare il dispositivo.
