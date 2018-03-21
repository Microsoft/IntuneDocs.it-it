---
title: Reimpostare i dispositivi Windows 10 con Microsoft Intune - Azure | Microsoft Docs
description: "Usare Fresh Start per rimuovere o disinstallare app nei PC Windows 10 con Microsoft Intune, incluse le app preinstallate da OEM. È anche possibile mantenere il contenuto della home directory tramite l'impostazione if user data is retained."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d17c9dc11791f32f0c2c1e7faa88966c112fc6a5
ms.sourcegitcommit: 9cf05d3cb8099e4a238dae9b561920801ad5cdc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2018
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Usare Fresh Start per ripristinare i dispositivi Windows 10 con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Fresh Start** rimuove le eventuali app installate nei PC con Windows 10 Creators Update e quindi aggiorna automaticamente il PC alla versione più recente di Windows.

Questa azione consente di rimuovere le app (OEM) preinstallate in genere in un nuovo PC. Per mantenere il contenuto della home directory dell'utente e rimuovere solo le app e le impostazioni, usare l'impostazione `if user data is retained`.

> [!IMPORTANT]
> Fresh Start annulla la registrazione del dispositivo da Intune, ma il dispositivo è ancora aggiunto ad Azure Active Directory.

## <a name="use-fresh-start"></a>Usare Fresh Start

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti scegliere un dispositivo desktop Windows 10 e quindi selezionare **Fresh Start**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato di questa azione, selezionare **Azioni del dispositivo** (**Microsoft Intune** > **Dispositivi**).