---
title: Prepararsi alla configurazione dei criteri di protezione delle app per Windows 10
titlesuffix: Azure portal
description: Configurare il provider di gestione di applicazioni mobili (MAM) in Azure AD
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5514ea423f67e5bc824b4ee947f630c7f1b43d8f
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2018
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Prepararsi alla configurazione dei criteri di protezione delle app per Windows 10

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Abilitare la gestione di applicazioni mobili (MAM) per Windows 10, impostando il provider MAM in Azure AD. L'impostazione di un provider MAM in Azure AD consente di definire lo stato di registrazione quando si crea un nuovo criterio di Windows Information Protection (WIP) con Intune. Lo stato di registrazione può essere MAM o gestione dei dispositivi mobili (MDM).

> [!NOTE]
> I dispositivi con stato di registrazione MAM devono essere stati aggiunti ad Azure AD.

## <a name="to-configure-the-mam-provider"></a>Per configurare il provider MAM

1. Accedere al portale di Azure e scegliere **Azure Active Directory**.

2. Scegliere **Servizi Mobility (MDM e MAM)** nel gruppo **Gestisci**.

3. Fare clic su **Microsoft Intune**.

4. Configurare le impostazioni nel gruppo **Ripristina URL MAM predefiniti** nel pannello **Configura**.

   **Ambito utente MAM**  
   Usare la registrazione automatica MAM per gestire i dati aziendali nei dispositivi Windows dei dipendenti. La registrazione automatica MAM verrà configurata per gli scenari Bring Your Own Device (BYOD).<ul><li>**Nessuno**<br>Selezionare questa opzione se tutti gli utenti possono essere registrati in MAM.</li><li>**Alcuni**<br>Selezionare i gruppi di Azure AD che contengono utenti che verranno registrati in MAM.</li><li>**Tutti**<br>Selezionare questa opzione se tutti gli utenti possono essere registrati in MAM.</li></ul>

   **URL delle condizioni per l'utilizzo di MAM**  
   L'URL delle condizioni per l'utilizzo di MAM non è supportato per Microsoft Intune. Per applicare i criteri di protezione è necessario che questa casella di input sia lasciata vuota.

   **URL individuazione MAM**  
   URL dell'endpoint di registrazione del servizio MAM. L'endpoint di registrazione viene usato per registrare i dispositivi per la gestione con il servizio MAM.

   **URL conformità MAM**  
   L'URL di conformità MAM non è supportato per Microsoft Intune. Per applicare i criteri di protezione è necessario che questa casella di input sia lasciata vuota. 

5.  Fare clic su **Save**.

## <a name="next-steps"></a>Passaggi successivi

[Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune](windows-information-protection-policy-create.md)
