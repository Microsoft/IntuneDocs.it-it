---
title: Reimpostare e rimuovere i passcode del dispositivo con Intune
titlesuffix: Azure portal
description: Informazioni su come reimpostare e rimuovere il passcode nei dispositivi gestiti con Intune.
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dfa94d11f978bbe4d23b6672423c849e1f061986
ms.sourcegitcommit: 474a24ba67f6bf4f00268bf9e4eba52331a6b82d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2017
---
# <a name="reset-and-remove-the-passcode-on-intune-managed-devices"></a>Reimpostare e rimuovere il passcode nei dispositivi gestiti con Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

In questo articolo, i termini *rimuovere* e *reimpostare* vengono usati in modo intercambiabile.

L'azione **Rimuovi il passcode** genera un nuovo passcode per il dispositivo che viene visualizzato nel pannello **Panoramica** di <*nome dispositivo*> .

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows: funzionalità non supportata
- Windows Phone: funzionalità supportata da Windows Phone 8.1 a Windows 10 Creators Update (non aggiunto ad Azure AD), Windows 10 Creators Update e versioni successive
- iOS: funzionalità supportata
- macOS: funzionalità non supportata
- Android: funzionalità supportata nelle versioni precedenti ad Android 7. Android for Work non è supportato.

## <a name="how-to-reset-a-passcode"></a>Come reimpostare un passcode

1. Accedere al portale Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota del dispositivo **Rimuovi il passcode**.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** nel pannello **Dispositivi e gruppi**.
