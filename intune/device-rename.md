---
title: Rinominare un dispositivo Windows con Microsoft Intune - Azure | Microsoft Docs
description: Rinominare un dispositivo Windows usando Microsoft Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567101"
---
# <a name="rename-a-windows-device-in-intune"></a>Rinominare un dispositivo Windows in Intune


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

L'azione **Rinomina dispositivo** consente di rinominare un dispositivo Windows di proprietà dell'azienda registrato in Intune. Il nome del dispositivo viene cambiato in Intune e nel dispositivo. 

Questa funzionalità non supporta attualmente la ridenominazione di dispositivi Windows di Azure AD ibridi.

## <a name="rename-a-device"></a>Rinominare un dispositivo

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Scegliere **Tutti i servizi**, filtrare per **Intune** e scegliere **Microsoft Intune**.
3. Scegliere **Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo Windows > **Altro** > **Rinomina dispositivo**.
4. Nel pannello **Rinomina dispositivo** digitare il nuovo nome nella casella di testo. È possibile usare lettere, numeri e trattini. Il nome deve contenere almeno una lettera o un trattino.
5. Se si vuole riavviare il dispositivo dopo averlo rinominato, scegliere **Sì** accanto a **Riavvia dopo la ridenominazione**.
6. Scegliere **Rinomina**.



## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione **Rinomina dispositivo**, controllare la pagina **Panoramica** del dispositivo.
