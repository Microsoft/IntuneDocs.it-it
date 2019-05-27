---
title: Configurare le impostazioni di Endpoint Protection in Microsoft Intune - Azure | Microsoft Docs
description: Creare le impostazioni di Endpoint Protection quando si crea un profilo del dispositivo macOS o Windows 10 in Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 5/17/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: c13c5d71d1ff631d7a3c84cd3f62037569757917
ms.sourcegitcommit: bc5e4dff18f5f9b79077a888f8a58dcc490708c0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975771"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Aggiungere le impostazioni di Endpoint Protection in Intune

Con Intune, è possibile usare profili di configurazione dei dispositivi per la gestione delle comuni funzionalità di sicurezza di Endpoint Protection nei dispositivi, tra cui:
- Firewall 
- BitLocker
- App consentite e bloccate  
- Windows Defender e crittografia

Ad esempio, è possibile creare un profilo di Endpoint Protection che consente solo agli utenti macOS di installare le app dal Mac App Store. In alternativa, abilitare Windows SmartScreen durante l'esecuzione di app nei dispositivi Windows 10.

Prima di creare un profilo, rivedere gli articoli seguenti che illustrano in dettaglio le impostazioni di Endpoint Protection che Intune può gestire per ogni piattaforma supportata: 
   - [Impostazioni macOS](endpoint-protection-macos.md)
   - [Impostazioni Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Creare un profilo del dispositivo contenente le impostazioni di Endpoint Protection

1. Accedere a [Intune](https://go.microsoft.com/fwlink/?linkid=20909).
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
4. Inserire un **Nome** e una **Descrizione** per il profilo di Endpoint Protection.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni personalizzate. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:
   - **macOS**
   - **Windows 10 e versioni successive**
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Endpoint Protection**. 
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Per altre informazioni, vedere gli argomenti indicati di seguito.
   - [Impostazioni macOS](endpoint-protection-macos.md)
   - [Impostazioni Windows 10](endpoint-protection-windows-10.md)  

8. Dopo aver configurato le impostazioni applicabili, selezionare **Crea** nella pagina **Crea profilo**.

   Il profilo viene creato e visualizzato nella pagina dell'elenco dei profili. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).


## <a name="next-steps"></a>Passaggi successivi  

Per assegnare un profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
