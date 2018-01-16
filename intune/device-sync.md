---
title: Sincronizzare i dispositivi con Intune
titlesuffix: Azure portal
description: "Informazioni su come sincronizzare i dispositivi con Intune per ottenere i criteri e le azioni più recenti.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8a8bb4729314819b23d69f0ccf6f6c093f29801f
ms.sourcegitcommit: 22ab1c6a6bfeb4fef9850d12b29829c3fecbbeed
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>Sincronizzare i dispositivi con Intune per ottenere i criteri e le azioni più recenti


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

L'azione del dispositivo **Sincronizza** forza il dispositivo selezionato a eseguire immediatamente l'archiviazione in Intune. Quando un dispositivo esegue l'archiviazione, riceve immediatamente le azioni in sospeso o i criteri assegnati.  Questa azione consente di convalidare e risolvere i problemi di criteri assegnati immediatamente, senza attendere la successiva archiviazione pianificata.

## <a name="supported-platforms"></a>Piattaforme supportate

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="how-to-sync-a-device"></a>Come sincronizzare un dispositivo

1. Accedere al portale di Azure.
2. Scegliere **Altri servizi** > **Monitoraggio e gestione** > **Intune**.
3. Nel pannello **Intune** scegliere **Dispositivi**.
4. Nel pannello **Dispositivi e gruppi** scegliere **Tutti i dispositivi**.
5. Nell'elenco dei dispositivi gestiti scegliere un dispositivo e quindi scegliere l'azione remota **Sincronizza**.
7. Scegliere **Sì** per confermare l'azione.


## <a name="retriable-error-codes"></a>Codici di errore con possibilità di ritentare

Quando un amministratore esegue l'azione **Sincronizzazione** per il dispositivo, le app iOS e Android per le quali l'azione non è riuscita e che hanno generato un codice di errore con possibilità di ritentare risultano disponibili per il dispositivo. Invece le app che hanno generato un codice di errore senza possibilità di ritentare vengono rese disponibili al dispositivo dopo sette giorni.


| Codice di errore  | Descrizione suggerita                                                                                                                  | Con possibilità di ritentare |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 2016330898 | Si è verificato un errore sconosciuto.                                                                                                             | No        |
| 2016330897 | Si è verificato il timeout della connessione a Intune. Reimpostare la connessione.                                                                             | Sì       |
| 2016330896 | La connessione a Internet è stata persa. Reimpostare la connessione.                                                                            | Sì       |
| 2016330895 | La connessione a Internet è stata persa. Reimpostare la connessione.                                                                            | Sì       |
| 2016330894 | La connessione a Internet è stata persa. Reimpostare la connessione.                                                                            | Sì       |
| 2016330893 | La connessione a Internet è stata persa. Reimpostare la connessione.                                                                            | Sì       |
| 2016330892 | Il roaming internazionale è disabilitato.                                                                                                     | No        |
| 2016330891 | Non è possibile accedere alla connessione alla rete cellulare per questo dispositivo durante l'effettuazione di una telefonata. Attendere il completamento della telefonata. | Sì       |
| 2016330890 | Non è stato possibile usare la rete cellulare per questo dispositivo/questi dispositivi. Non è stato possibile usare i dispositivi.                                                   | No        |
| 2016330889 | La connessione sicura non è riuscita. Reimpostare la connessione.                                                                                   | Sì       |
| 2016330888 | Non è stato possibile valutare il server trust.                                                                                                | No        |

## <a name="next-steps"></a>Passaggi successivi

Scegliere **Azioni del dispositivo** per visualizzare lo stato dell'azione di sincronizzazione. 
