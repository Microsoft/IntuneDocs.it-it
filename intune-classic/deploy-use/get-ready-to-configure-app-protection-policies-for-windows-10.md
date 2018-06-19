---
title: Prepararsi alla configurazione dei criteri di protezione delle app per Windows 10
description: Configurare il provider di gestione di applicazioni mobili (MAM) in Azure AD
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 04/18/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ebc7cfc8-40b9-47c2-8357-d392ebbb27c8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9b91d3740ead5815974d7ffee67c15b7769b0210
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025553"
---
# <a name="get-ready-to-configure-app-protection-policies-for-windows-10"></a>Prepararsi alla configurazione dei criteri di protezione delle app per Windows 10

[!INCLUDE [note for both-portals](../includes/note-for-both-portals.md)]

Prima di creare un criterio di protezione delle app per Windows 10, è necessario abilitare la gestione di applicazioni mobili (MAM) per Windows 10 configurando il provider MAM in Azure AD. Questa configurazione consente di definire lo stato di registrazione quando si crea un nuovo criterio di Windows Information Protection (WIP) con Intune.

> [!NOTE]
> Lo stato di registrazione può essere MAM o gestione dei dispositivi mobili (MDM).

## <a name="to-configure-the-mam-provider"></a>Per configurare il provider MAM

1.  Andare nel [portale di Azure](https://portal.azure.com/) e accedere con le credenziali di Intune.

2.  Dal menu a sinistra scegliere **Azure Active Directory**.

    ![Configurazione del provider MAM](../media/AppManagement/mam-provider-sc-1.png)

3.  Verrà aperto il pannello **Azure AD**. Scegliere **Servizi Mobility (MDM e MAM)** e quindi fare clic su **Microsoft Intune**.

    ![Servizi Mobility (MDM e MAM)](../media/AppManagement/mam-provider-sc-2.png)

4.  Verrà aperto il pannello di configurazione. Scegliere prima di tutto **Ripristina URL MAM predefiniti** e quindi configurare quanto segue:

    a.  Ambito utente MAM: è possibile usare MAM per proteggere i dati aziendali per un gruppo specifico di utenti che usano i dispositivi Windows 10 o per tutti gli utenti.

    b.  URL delle condizioni per l'utilizzo di MAM: URL dell'endpoint delle condizioni per l'utilizzo del servizio MAM. Questo URL viene usato per visualizzare le condizioni per l'utilizzo del servizio MAM agli utenti finali.

    c.  URL individuazione MAM: questo è l'URL che cercano i dispositivi quando devono applicare i criteri di protezione delle app.

    d.  URL conformità MAM:

5.  Dopo aver configurato queste impostazioni scegliere **Salva**.

## <a name="next-steps"></a>Passaggi successivi

[Creare e distribuire criteri di protezione delle app Windows Information Protection (WIP) con Intune](/intune-classic/deploy-use/create-windows-information-protection-policy-with-intune)
