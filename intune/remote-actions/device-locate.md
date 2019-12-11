---
title: Trovare i dispositivi persi iOS con Microsoft Intune - Azure | Microsoft Docs
description: Individuare i dispositivi iOS persi o rubati usando la funzionalità di individuazione del dispositivo in Microsoft Intune. Ottenere informazioni dettagliate sulla sicurezza e la privacy quando si usa l'azione di individuazione del dispositivo.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 817f46558932c074abc37b45d2885496419a0db0
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73712419"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Individuare dispositivi iOS persi o rubati con Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Per ottenere la posizione di un dispositivo iOS perso o rubato su una mappa, usare l'azione **Individua il dispositivo**. Il dispositivo deve essere in modalità con supervisione. Prima di usare questa azione, assicurarsi che il dispositivo sia in [modalità di dispositivo perso](device-lost-mode.md).

## <a name="supported-platforms"></a>Piattaforme supportate

- iOS 9.3 e versioni successive

Questa funzionalità non è supportata per i sistemi seguenti: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Individuare un dispositivo perso o rubato

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS e quindi **...Altre informazioni**. Scegliere l'azione remota **Individua il dispositivo**.
5. Dopo la localizzazione del dispositivo, la posizione viene visualizzata in **Individua il dispositivo**.
    ![Screenshot di Individua il dispositivo con Intune in Azure](./media/device-locate/locate-device.png)


## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>Attivare l'avviso sonoro relativo alla modalità di dispositivo perso in un dispositivo iOS

Se un utente perde il dispositivo iOS 9.3 o versione successiva, è possibile attivarlo in remoto per riprodurre un avviso sonoro che permetta all'utente di trovarlo. Il dispositivo deve essere in [modalità di dispositivo perso](device-lost-mode.md).

In [Intune nel portale di Azure](https://aka.ms/intuneportal) scegliere **Dispositivi** > **Tutti i dispositivi** > selezionare un dispositivo iOS > **Panoramica** > **Altri** > **Play Lost mode sound (supervise only)** (Riproduci la suoneria della modalità di dispositivo perso - Solo supervisione).

Il suono continuerà finché l'utente non disabiliterà il suono dal dispositivo o la modalità di dispositivo perso non verrà cambiata.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Informazioni su privacy e sicurezza per le azioni Modalità di dispositivo perso e Individua il dispositivo
- Non vengono inviate informazioni sulla posizione del dispositivo a Intune finché non si attiva questa azione.
- Quando si usa l'azione di individuazione del dispositivo, le coordinate di latitudine e longitudine del dispositivo possono essere recuperate tramite l'API Graph.
- I dati vengono archiviati per 24 ore e quindi rimossi. Non è possibile rimuoverli manualmente.
- I dati relativi alla posizione sono crittografati, sia durante il periodo di archiviazione sia quando vengono trasmessi.
- Quando si configura la modalità di dispositivo perso, è possibile personalizzare un messaggio che viene visualizzato nella schermata di blocco. In questo messaggio, per agevolare la persona che trova il dispositivo, assicurarsi di includere dettagli specifici per la restituzione del dispositivo perso.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato di abilitazione dell'individuazione del dispositivo, aprire **Dispositivi** e selezionare **Azioni del dispositivo**.
