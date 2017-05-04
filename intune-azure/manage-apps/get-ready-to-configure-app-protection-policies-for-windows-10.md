---
title: Prepararsi alla configurazione dei criteri di protezione delle app per Windows 10 | Microsoft Docs
titleSuffix: Intune Azure preview
description: Configurare il provider di gestione di applicazioni mobili (MAM) in Azure AD
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 04/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 949fddec-5318-4c9a-957e-ea260e6e05be
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 5f172290d493717308446c4f9e2313a03ba8f3aa
ms.openlocfilehash: 7cd202384eeb17f5ff5a2812fe87a2fffabe6eb0
ms.lasthandoff: 04/27/2017


---

# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Prepararsi alla configurazione dei criteri di protezione delle app per Windows 10

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Prima di creare un criterio di protezione delle app per Windows 10, è necessario abilitare la gestione di applicazioni mobili (MAM) per Windows 10 configurando il provider MAM in Azure AD. Questa configurazione consente di definire lo stato di registrazione quando si crea un nuovo criterio di Windows Information Protection (WIP) con Intune.

> [!NOTE]
> Lo stato di registrazione può essere MAM o gestione dei dispositivi mobili (MDM).

## <a name="to-configure-the-mam-provider"></a>Per configurare il provider MAM

1.  Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le credenziali di Intune.

2.  Dal menu a sinistra scegliere **Azure Active Directory**.

    ![Configurazione del provider MAM](../media/AppManagement/mam-provider-sc-1.png)

3.  Verrà aperto il pannello **Azure AD**. Scegliere **Servizi Mobility (MDM e MAM)** e quindi fare clic su **Microsoft Intune**.

    ![Servizi Mobility (MDM e MAM)](../media/AppManagement/mam-provider-sc-1.png)

4.  Verrà aperto il pannello di configurazione. Scegliere prima di tutto **Ripristina URL MAM predefiniti** e quindi configurare quanto segue:

    a.  Ambito utente MAM: è possibile usare MAM per proteggere i dati aziendali per un gruppo specifico di utenti che usano i dispositivi Windows 10 o per tutti gli utenti.

    b.  URL delle condizioni per l'utilizzo di MAM: URL dell'endpoint delle condizioni per l'utilizzo del servizio MAM. Questo URL viene usato per visualizzare le condizioni per l'utilizzo del servizio MAM agli utenti finali.

    c.  URL individuazione MAM: questo è l'URL che cercano i dispositivi quando devono applicare i criteri di protezione delle app.

    d.  URL conformità MAM:

5.  Dopo aver configurato queste impostazioni scegliere **Salva**.

## <a name="next-steps"></a>Passaggi successivi

[Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune](https://docs.microsoft.com/intune-azure/manage-apps/create-windows-information-protection-policy-with-intune)

