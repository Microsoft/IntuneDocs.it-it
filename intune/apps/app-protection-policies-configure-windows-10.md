---
title: Configurare i criteri di protezione delle app per Windows 10
titleSuffix: Microsoft Intune
description: Questo argomento illustra come configurare i criteri di protezione delle app per i dispositivi Windows 10.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 41c08d1912bf9c79507c2a6627205979504f340d
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/27/2019
ms.locfileid: "74564231"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Prepararsi alla configurazione dei criteri di protezione delle app per Windows 10 

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Abilitare la gestione di applicazioni mobili (MAM) per Windows 10, impostando il provider MAM in Azure AD. L'impostazione di un provider MAM in Azure AD consente di definire lo stato di registrazione quando si crea un nuovo criterio di Windows Information Protection (WIP) con Intune. Lo stato di registrazione può essere MAM o gestione dei dispositivi mobili (MDM).

## <a name="to-configure-the-mam-provider"></a>Per configurare il provider MAM

1. Accedere all'[interfaccia di amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selezionare **Tutti i servizi** e scegliere **M365 Azure Active Directory** per passare da un dashboard all'altro.
3. Selezionare **Azure Active Directory**.
4. Scegliere **Servizi Mobility (MDM e MAM)** nel gruppo **Gestisci**.
5. Fare clic su **Microsoft Intune**.
6. Configurare le impostazioni nel gruppo **Ripristina URL MAM predefiniti** nel riquadro **Configura**.

   **Ambito utente MAM**  
   Usare la registrazione automatica MAM per gestire i dati aziendali nei dispositivi Windows dei dipendenti. La registrazione automatica MAM verrà configurata per gli scenari Bring Your Own Device (BYOD).<ul><li>**Nessuno**<br>Selezionare questa opzione se nessun utente può essere registrato in MAM.</li><li>**Alcuni**<br>Selezionare i gruppi di Azure AD che contengono utenti che verranno registrati in MAM.</li><li>**Tutti**<br>Selezionare questa opzione se tutti gli utenti possono essere registrati in MAM.</li></ul>

   **URL delle condizioni per l'utilizzo di MAM**  
   L'URL delle condizioni per l'utilizzo di MAM non è supportato per Microsoft Intune. Per applicare i criteri di protezione è necessario che questa casella di input sia lasciata vuota.

   **URL individuazione MAM**  
   URL dell'endpoint di registrazione del servizio MAM. L'endpoint di registrazione viene usato per registrare i dispositivi per la gestione con il servizio MAM.

   **URL conformità MAM**  
   L'URL di conformità MAM non è supportato per Microsoft Intune. Per applicare i criteri di protezione è necessario che questa casella di input sia lasciata vuota. 

7. Fare clic su **Save**.

## <a name="next-steps"></a>Passaggi successivi

[Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune](windows-information-protection-policy-create.md)
