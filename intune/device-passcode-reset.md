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
ms.openlocfilehash: a233c62b76901d9bad00aa6d8b2a8a4dd45dea96
ms.sourcegitcommit: 024cce10a99b12a13f32d3995b69c290743cafb8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2018
ms.locfileid: "39039302"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Reimpostare o rimuovere il passcode di un dispositivo in Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Per creare un nuovo passcode per un dispositivo, usare l'azione **Rimuovi il passcode**. Questa azione richiede la reimpostazione del PIN per il solo profilo di lavoro. Il ripristino del PIN del dispositivo non è supportato per i profili di lavoro Android.

## <a name="work-profile-pin-reset-supported-platforms"></a>Piattaforme supportate per la reimpostazione del PIN del profilo di lavoro

- Dispositivi Android registrati con un profilo di lavoro, versione 8.0 e successive 
- Dispositivi Android versione 6.0 o precedenti
- Dispositivi in modalità tutto schermo di Android Enterprise
- iOS 
     
## <a name="unsupported-platforms"></a>Piattaforme non supportate

- Dispositivi Android registrati con un profilo di lavoro, versione 7.0 e precedenti
- Dispositivi Android versione 7.0 o successive
- macOS
- Windows

## <a name="reset-a-passcode"></a>Reimpostare un passcode

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e quindi selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti selezionare un dispositivo e scegliere **...Altre informazioni**. Quindi scegliere l'azione remota del dispositivo **Rimuovi il passcode**.

## <a name="resetting-android-work-profile-passcodes"></a>Reimpostazione dei passcode dei profili di lavoro Android

I dispositivi con profili di lavoro Android supportati ricevono una nuova password per lo sblocco del profilo gestito o una richiesta di profilo gestito per l'utente finale. 

Per i dispositivi con profilo di lavoro Android 8.0, gli utenti finali ricevono una notifica per l'attivazione dei passcode reimpostati subito dopo il completamento della registrazione. La notifica viene visualizzata se la password di un profilo di lavoro è necessaria e impostata. Dopo l'immissione del passcode, la notifica viene chiusa.

## <a name="resetting-ios-passcodes"></a>Reimpostazione dei passcode iOS

I passcode vengono rimossi dai dispositivi iOS. Se è impostato un criterio di conformità passcode, il dispositivo richiede all'utente di definire un nuovo passcode nelle impostazioni. 

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato dell'azione appena eseguita, scegliere **Azioni del dispositivo** in **Dispositivi**.
