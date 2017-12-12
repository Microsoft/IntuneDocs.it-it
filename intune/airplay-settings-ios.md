---
title: Impostazioni di AirPlay di Intune per dispositivi iOS
titlesuffix: Azure portal
description: Informazioni su come usare Intune per connettere automaticamente i dispositivi iOS a dispositivi compatibili con AirPlay.
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 07/03/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 9a1472d86a0a25e35ef26be1c579ff491437676b
ms.sourcegitcommit: 3b397b1dcb780e2f82a3d8fba693773f1a9fcde1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2017
---
# <a name="intune-airplay-settings-for-ios-devices"></a>Impostazioni di AirPlay di Intune per dispositivi iOS

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare queste impostazioni per connettere i dispositivi iOS gestiti a dispositivi compatibili con AirPlay, ad esempio un Apple TV, in rete.
Questa funzionalità consente di eseguire le operazioni seguenti:

- **Configurare un elenco di dispositivi e password**: per consentire agli utenti di connettersi automaticamente ai dispositivi AirPlay nel campo. Eseguire il provisioning con il nome e la password dei dispositivi AirPlay in modo che non debbano specificarli al momento della connessione.
- **Configurare le destinazioni consentite**: configurare un elenco di dispositivi AirPlay, usando l'ID dispositivo. Gli utenti finali possono visualizzare e connettersi solo ai dispositivi elencati (solo dispositivi con supervisione).

## <a name="get-started"></a>Introduzione

1. Nel pannello **Funzionalità del dispositivo** scegliere **AirPlay**.
2. Nel pannello **AirPlay** scegliere una o entrambe le operazioni seguenti:

## <a name="configure-a-device-and-password-list"></a>Configurare un elenco di dispositivi e password

1. Nel pannello **Password** immettere **Nome dispositivo** e la **Password** di un dispositivo AirPlay, ad esempio **Contoso Apple TV**.
2. Dopo aver immesso le informazioni sul dispositivo, fare clic su **Aggiungi**. Il dispositivo verrà visualizzato nell'elenco **Nome dispositivo**.
3. Aggiungere tutti i dispositivi desiderati. Al termine scegliere **OK**.


## <a name="configure-allowed-destinations"></a>Configurare le destinazioni consentite

1. Nel pannello **Allowed destinations (supervised only)** (Destinazioni consentite (solo con supervisione)) immettere l'**ID dispositivo** di un dispositivo AirPlay, ad esempio 52:46:CD:51:83:4C.
2. Dopo aver immesso l'ID del dispositivo, fare clic su **Aggiungi**. L'ID verrà visualizzato nell'elenco **ID dispositivo**.
3. Aggiungere tutti i dispositivi desiderati. Al termine scegliere **OK**.

È anche possibile importare il dispositivo, le password e le destinazioni consentite da un file con valori delimitati da virgole (csv).


## <a name="next-steps"></a>Passaggi successivi

È ora possibile assegnare il profilo del dispositivo ai gruppi selezionati. Per informazioni dettagliate, vedere [How to assign device profiles](device-profile-assign.md) (Come assegnare profili di dispositivo).

