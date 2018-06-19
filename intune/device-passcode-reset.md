---
title: Reimpostare i passcode dei dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Rimuovere o reimpostare il passcode tramite l'azione di rimozione del passcode nei dispositivi gestiti o monitorati con Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5783558a768e1d58087168f81ad27e5acf9aae09
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34216310"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Reimpostare o rimuovere il passcode di un dispositivo in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Per creare un nuovo passcode per un dispositivo, usare l'azione **Rimuovi il passcode**.

## <a name="supported-platforms"></a>Piattaforme supportate

- Dispositivi Android registrati con un profilo di lavoro, versione 7.0 e successive
- Dispositivi Android versione 6.0 o precedenti
- iOS 
     
## <a name="unsupported-platforms"></a>Piattaforme non supportate

- Dispositivi Android registrati con un profilo di lavoro, versione 6.0 e precedenti
- Dispositivi Android versione 7.0 o successive
- macOS
- Windows

## <a name="reset-a-passcode"></a>Reimpostare un passcode

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti selezionare un dispositivo e scegliere **...Altre informazioni**. Quindi scegliere l'azione remota del dispositivo **Rimuovi il passcode**.

## <a name="resetting-android-for-work-passcodes"></a>Reimpostazione dei passcode di Android for Work

I dispositivi Android for Work supportati ricevono una nuova password per lo sblocco del profilo gestito o una richiesta di profilo gestito per l'utente finale. Gli utenti finali di dispositivi Android 7.0 o versioni successive con profili di lavoro ricevono notifiche per attivare il token di reimpostazione passcode immediatamente dopo il completamento della registrazione. La notifica viene visualizzata se la password di un profilo di lavoro è necessaria e impostata. Dopo l'immissione del passcode, la notifica viene chiusa.

## <a name="resetting-ios-passcodes"></a>Reimpostazione dei passcode iOS

I passcode vengono rimossi dai dispositivi iOS. Se è impostato un criterio di conformità passcode, il dispositivo richiederà all'utente di impostare un nuovo passcode nelle impostazioni. 

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** in **Dispositivi**.
