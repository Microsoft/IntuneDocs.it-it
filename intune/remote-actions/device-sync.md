---
title: Sincronizzare i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: Sincronizzare i dispositivi registrati o gestiti con Microsoft Intune per ottenere i criteri e le azioni più recenti. Include i passaggi per eseguire la sincronizzazione usando il portale di Azure e i codici di errore che è possibile ritentare.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21167b226556100e7e9920f31f859d6d6ce2a7bb
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415537"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>Sincronizzare i dispositivi per ottenere i criteri e le azioni più recenti con Intune


L'azione del dispositivo **Sincronizza** forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati. Questa funzionalità consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Sincronizzare un dispositivo

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). 
3. Selezionare **Dispositivi** > **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti selezionare un dispositivo per aprire il relativo riquadro *Panoramica*, quindi selezionare **Sincronizza**.
5. Selezionare **Sì** per confermare.

Per visualizzare lo stato dell'azione di sincronizzazione, scegliere **Dispositivi** > **Azioni del dispositivo**.

Le frequenze di controllo standard dei criteri di Intune sono disponibili in [Frequenza dei cicli di aggiornamento](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

## <a name="retryable-error-codes"></a>Codici di errori non irreversibili

Quando un amministratore esegue l'azione del dispositivo **Sincronizza**, le app iOS/iPadOS e Android per le quali l'azione non è riuscita e che hanno generato un codice di errore non irreversibile sono ancora disponibili per il dispositivo. Le app che hanno generato un codice di errore irreversibile, invece, vengono rese disponibili per il dispositivo dopo sette giorni.


| Codice errore  | Descrizione suggerita | Non irreversibile |
|---|---|---|
| 2016330898 | Si è verificato un errore sconosciuto. | No |
| 2016330897 | Si è verificato il timeout della connessione a Intune. Reimpostare la connessione. | Sì |
| 2016330896 | La connessione a Internet è stata persa. Reimpostare la connessione. | Sì |
| 2016330895 | La connessione a Internet è stata persa. Reimpostare la connessione. | Sì |
| 2016330894 | La connessione a Internet è stata persa. Reimpostare la connessione. | Sì |
| 2016330893 | La connessione a Internet è stata persa. Reimpostare la connessione. | Sì|
| 2016330892 | Il roaming internazionale è disabilitato. | No|
| 2016330891 | Non è possibile accedere alla connessione alla rete cellulare per questo dispositivo durante l'effettuazione di una telefonata. Attendere il completamento della telefonata. | Sì|
| 2016330890 | Non è stato possibile usare la rete cellulare per questo dispositivo/questi dispositivi. Non è stato possibile usare i dispositivi. | No|
| 2016330889 | La connessione sicura non è riuscita. Reimpostare la connessione. | Sì|
| 2016330888 | Non è stato possibile valutare il server trust. | No|

## <a name="next-steps"></a>Passaggi successivi

È possibile [controllare i dettagli](device-inventory.md) del dispositivo.
 
