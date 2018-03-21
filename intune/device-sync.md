---
title: Sincronizzare i dispositivi con Microsoft Intune - Azure | Microsoft Docs
description: "Sincronizzare i dispositivi registrati o gestiti con Microsoft Intune per ottenere i criteri e le azioni più recenti. Include i passaggi per eseguire la sincronizzazione tramite il portale di Azure e vengono elencati i codici di errore che è possibile ritentare."
keywords: 
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d2d13ce2ed06549a6cd09fd766a0072b15fcd067
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions---intune"></a>Sincronizzare i dispositivi per ottenere i criteri e le azioni più recenti - Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Sincronizza** forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati. Questa funzionalità consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>Sincronizzare un dispositivo

1. Accedere al [portale Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**. 
3. In **Intune** selezionare **Dispositivi** e quindi selezionare **Tutti i dispositivi**.
4. Nell'elenco dei dispositivi gestiti scegliere un dispositivo, scegliere **Altro** e quindi scegliere l'azione **Sincronizza**.
5. Selezionare **Sì** per confermare.


## <a name="retryable-error-codes"></a>Codici di errori non irreversibili

Quando un amministratore esegue l'azione del dispositivo **Sincronizza**, le app iOS e Android per le quali l'azione non è riuscita e che hanno generato un codice di errore non irreversibile sono ancora disponibili per il dispositivo. Le app che hanno generato un codice di errore irreversibile, invece, vengono rese disponibili per il dispositivo dopo sette giorni.


| Codice di errore  | Descrizione suggerita | Non irreversibile |
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

## <a name="next-step"></a>Passaggio successivo

Scegliere **Azioni del dispositivo** per visualizzare lo stato dell'azione di sincronizzazione. 
