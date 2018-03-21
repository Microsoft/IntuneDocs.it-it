---
title: Trovare i dispositivi persi iOS con Microsoft Intune - Azure | Microsoft Docs
description: "Trovare o localizzare i dispositivi iOS smarriti o rubati con la funzionalità Individua il dispositivo in Microsoft Intune e ottenere informazioni dettagliate sulla sicurezza e la privacy quando si usa l'azione Individua il dispositivo."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4bc51ef7f9af9cc97fd4c11408a1857679aee665
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Individuare dispositivi iOS persi o rubati con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Per ottenere la posizione di un dispositivo iOS rubato o smarrito su una mappa, usare l'azione del dispositivo **Individua il dispositivo**. Il dispositivo deve essere un dispositivo iOS di proprietà dell'azienda, registrato con DEP (Device Enrollment Program) e in modalità con supervisione. Prima di usare questa azione, assicurarsi che il dispositivo sia in [modalità di dispositivo perso](device-lost-mode.md).

## <a name="supported-platforms"></a>Piattaforme supportate

- iOS 9.3 e versioni successive

Questa funzionalità **non** è supportata per i sistemi seguenti: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>Individuare un dispositivo perso o rubato

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS, scegliere **Altro** e quindi scegliere l'azione remota **Individua il dispositivo**.
5. Dopo la localizzazione del dispositivo, la posizione viene visualizzata in **Individua il dispositivo**.
    ![Individuare un dispositivo con Intune in Azure](./media/locate-device.png)

>[!NOTE]
>Per motivi di privacy, la distanza di zoom nella mappa è limitata.

## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>Informazioni su privacy e sicurezza per le azioni Modalità di dispositivo perso e Individua il dispositivo
- Non vengono inviate informazioni sulla posizione del dispositivo a Intune finché non si attiva questa azione.
- Quando si usa l'azione Individua il dispositivo, le coordinate di latitudine e longitudine del dispositivo vengono inviate a Intune e visualizzate nel portale di Azure.
- I dati vengono archiviati per 24 ore e quindi rimossi. Non è possibile rimuoverli manualmente.
- I dati relativi alla posizione sono crittografati, sia durante il periodo di archiviazione sia quando vengono trasmessi.
- Quando si configura la modalità di dispositivo perso, è possibile personalizzare un messaggio che viene visualizzato nella schermata di blocco. In questo messaggio, per agevolare la persona che trova il dispositivo, assicurarsi di includere dettagli specifici per la restituzione del dispositivo perso.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato di abilitazione di Individua il dispositivo, aprire **Dispositivi** e selezionare **Azioni del dispositivo**.
