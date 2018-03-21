---
title: "Attivare la modalità di dispositivo perso iOS con Microsoft Intune - Azure | Microsoft Docs"
description: "Usare Microsoft Intune per attivare o avviare la modalità di dispositivo perso per personalizzare un messaggio da visualizzare nella schermata di blocco di un dispositivo iOS smarrito o rubato. Ottenere inoltre informazioni dettagliate sulla sicurezza e la privacy quando si usa l'azione Modalità di dispositivo perso."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 126a7489-fe3e-43fd-a681-defb2fe0bb66
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 47d6314dfaed546e5b4cff7f93a5540ba512bde9
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="enable-lost-mode-on-ios-devices-with-intune"></a>Abilitare la modalità di dispositivo perso nei dispositivi iOS con Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Modalità di dispositivo perso** consente di abilitare la modalità di dispositivo perso nei dispositivi iOS smarriti o rubati. Questa modalità consente di immettere un messaggio e un numero di telefono da visualizzare nella schermata di blocco del dispositivo. Per usare la modalità di dispositivo perso, il dispositivo deve essere un dispositivo iOS di proprietà dell'azienda in cui è attiva la modalità con supervisione.

## <a name="supported-platforms"></a>Piattaforme supportate

- iOS 9.3 e versioni successive

Questa funzionalità **non** è supportata per le piattaforme seguenti: 
- Windows
- Windows Phone
- macOS
- Android

## <a name="enable-lost-mode"></a>Abilitare la modalità di dispositivo perso

1. Accedere al [portale Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti scegliere un dispositivo iOS, scegliere **Altro** e quindi scegliere l'azione remota **Modalità di dispositivo perso**.
5. In **Modalità di dispositivo perso** abilitare questa funzionalità. Immettere quindi il messaggio da visualizzare e un numero di telefono di contatto.
6. Selezionare **OK** per salvare le modifiche.

Quando si abilita la modalità di dispositivo perso, si blocca qualsiasi uso del dispositivo. L'utente finale non può accedere al dispositivo finché l'amministratore non disabilita questa modalità. Quando la modalità di dispositivo perso è abilitata, è possibile usare l'azione [Individua il dispositivo](device-locate.md) per trovare il dispositivo.

## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informazioni su privacy e sicurezza per le azioni Modalità di dispositivo perso e Individua il dispositivo
- Non vengono inviate informazioni sulla posizione del dispositivo a Intune finché non si attiva questa azione.
- Quando si usa l'azione Individua il dispositivo, le coordinate di latitudine e longitudine del dispositivo vengono inviate a Intune e visualizzate nel portale di Azure.
- I dati vengono archiviati per 24 ore e quindi rimossi. Non è possibile rimuoverli manualmente.
- I dati relativi alla posizione sono crittografati, sia durante il periodo di archiviazione sia quando vengono trasmessi.
- Nel messaggio immesso da visualizzare nella schermata di blocco, assicurarsi di includere dettagli specifici per la restituzione del dispositivo perso.

## <a name="next-steps"></a>Passaggi successivi

Per visualizzare lo stato di abilitazione della modalità di dispositivo perso, aprire **Dispositivi** e selezionare **Azioni del dispositivo**.