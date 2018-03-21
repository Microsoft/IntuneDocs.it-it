---
title: Reimpostare i passcode dei dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Rimuovere o reimpostare il passcode tramite l'azione Rimuovi il passcode nei dispositivi gestiti o monitorati con Intune.
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f23a79bbe72d12750ef642226aefd1e11dcac24
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Reimpostare o rimuovere il passcode di un dispositivo in Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Per creare un nuovo passcode per un dispositivo, usare l'azione **Rimuovi il passcode**.

## <a name="supported-platforms"></a>Piattaforme supportate

- Da Windows Phone 8.1 a Windows 10 Creators Update non aggiunti ad Azure AD e Windows 10 Creators Update e versioni successive
- iOS
- Le versioni di Android precedenti alla 7

Questa funzionalità **non** è supportata per i sistemi seguenti:

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>Reimpostare un passcode

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti selezionare un dispositivo, scegliere **Altro** e quindi scegliere l'azione remota del dispositivo **Rimuovi il passcode**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** in **Dispositivi**.
