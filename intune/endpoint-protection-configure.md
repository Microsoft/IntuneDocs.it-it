---
title: Configurare le impostazioni di Endpoint Protection in Microsoft Intune - Azure | Microsoft Docs
description: Creare le impostazioni di Endpoint Protection quando si crea un profilo del dispositivo macOS o Windows 10 in Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b960b837cef5941fac829eeb878eb520b0274fba
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31022017"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Aggiungere le impostazioni di Endpoint Protection in Intune

Endpoint Protection consente di controllare diverse funzionalità di sicurezza nei dispositivi, incluso firewall, bitlocker, consentire e bloccare le app, Windows Defender, crittografia e altro ancora. È possibile configurare queste impostazioni in Microsoft Intune usando i profili dei dispositivi.

Ad esempio, è possibile creare un profilo di Endpoint Protection che consente solo agli utenti macOS di installare le app dal Mac App Store. In alternativa, abilitare Windows SmartScreen durante l'esecuzione di app nei dispositivi Windows 10.

In questo articolo viene illustrato come creare un profilo. Quindi, selezionare la piattaforma del proprio dispositivo per ulteriori informazioni sulle impostazioni disponibili.

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Creare un profilo del dispositivo contenente le impostazioni di Endpoint Protection

1. Accedere al [portale di Azure](https://portal.azure.com).
2. Selezionare **Tutti i servizi**, filtrare per **Intune** e selezionare **Microsoft Intune**.
3. Selezionare **Configurazione del dispositivo** > **Profili** > **Crea profilo**.
4. Inserire un **Nome** e una **Descrizione** per il profilo di Endpoint Protection.
5. Dall'elenco a discesa **Piattaforma** selezionare la piattaforma del dispositivo a cui si desiderano applicare le impostazioni personalizzate. Attualmente, è possibile scegliere una tra le piattaforme seguenti per le impostazioni delle restrizioni del dispositivo:
   - **macOS**
   - **Windows 10 e versioni successive**
6. Dall'elenco a discesa **Tipo di profilo** scegliere **Endpoint Protection**. 
7. Le impostazioni configurabili variano in base alla piattaforma scelta. Passare a uno degli argomenti seguenti per il dettaglio delle impostazioni di ogni piattaforma:
   - [Impostazioni macOS](endpoint-protection-macos.md)
   - [Impostazioni Windows 10](endpoint-protection-windows-10.md)
8. Al termine tornare alla pagina **Crea profilo** e fare clic su **Crea**.

Il profilo viene creato e visualizzato nella pagina dell'elenco dei profili. Per assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo con Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Passaggi successivi
Per assegnare un profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).
