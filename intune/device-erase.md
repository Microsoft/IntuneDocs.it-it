---
title: Cancellare un dispositivo macOS
titlesuffix: Azure portal
description: Informazioni su come cancellare tutti i dati, incluso il sistema operativo, da un dispositivo macOS".
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81f328004863e812b706174e74a9b74d0bdf80b6
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a name="erase-all-data-from-a-macos-device"></a>Cancellare tutti i dati da un dispositivo macOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

È possibile cancellare tutti i dati da un dispositivo macOS, incluso il sistema operativo. Il dispositivo verrà rimosso anche dalla gestione di Intune. Nessun avviso verrà visualizzato dall'utente finale.

1. In [Intune nel portale di Azure](https://aka.ms/intuneportal) scegliere **Dispositivi** > **Tutti i dispositivi** e quindi scegliere il dispositivo da cancellare.
![Screenshot](./media/device-erase/choosedevice.png)
2. Fare clic su **Altro** > **Cancella** e quindi specificare un numero di 6 cifre per il **PIN di ripristino**. Questo è il PIN che è necessario dare all'utente per poter reinstallare il sistema operativo nel dispositivo. Assicurarsi di prendere nota di questo PIN perché non sarà visibile una volta completata l'azione di cancellazione.
![Screenshot](./media/device-erase/providepin.png)
3. Fare clic su **OK** per cancellare il dispositivo.