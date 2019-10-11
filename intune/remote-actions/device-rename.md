---
title: Rinominare un dispositivo con Microsoft Intune - Azure | Microsoft Docs
description: Rinominare un dispositivo usando Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 35fae5ea1b3294772db4f4db51179892e08ed5d1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728507"
---
# <a name="rename-a-device-in-intune"></a>Rinominare un dispositivo in Intune


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

L'azione **Rinomina dispositivo** consente di rinominare un dispositivo registrato in Intune. Il nome del dispositivo viene cambiato in Intune e nel dispositivo.

È possibile creare i tipi di dispositivo seguenti:
- Windows di proprietà dell'azienda 
- iOS con supervisione
- macOS 10 di proprietà dell'azienda

Questa funzionalità non supporta attualmente la ridenominazione di dispositivi Windows di Azure AD ibridi.

## <a name="rename-a-device"></a>Rinominare un dispositivo

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. Scegliere **Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo > **Altro** > **Rinomina dispositivo**.
4. Nel pannello **Rinomina dispositivo** digitare il nuovo nome nella casella di testo. È possibile usare lettere, numeri e trattini. Il nome deve contenere almeno una lettera o un trattino.
5. Se si vuole riavviare il dispositivo dopo averlo rinominato, scegliere **Sì** accanto a **Riavvia dopo la ridenominazione**.
6. Scegliere **Rinomina**.



## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione **Rinomina dispositivo**, controllare la pagina **Panoramica** del dispositivo.
