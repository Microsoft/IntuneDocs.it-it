---
title: Impostazioni di AirPlay di Intune per dispositivi iOS
titleSuffix: Intune Azure preview
description: Informazioni su come usare Intune per connettere automaticamente i dispositivi iOS a dispositivi compatibili con AirPlay.
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ad2f20603261ec0eac4156facd3fd23b2982f517
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="intune-airplay-settings-for-ios-devices"></a>Impostazioni di AirPlay di Intune per dispositivi iOS

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Usare queste impostazioni per connettere i dispositivi iOS gestiti a dispositivi compatibili con AirPlay, ad esempio un Apple TV, in rete.
Questa funzionalità consente di eseguire le operazioni seguenti:

- **Configurare un elenco di dispositivi e password**: effettuare il provisioning dei dispositivi usando il nome e la password dei dispositivi AirPlay in modo che si connettano automaticamente quando disponibili. Se si indica una password, gli utenti finali non dovranno specificarla al momento della connessione.
- **Configurare le destinazioni consentite**: configurare un elenco di dispositivi AirPlay, usando l'ID dispositivo. Gli utenti finali potranno visualizzare e connettersi solo ai dispositivi elencati (solo dispositivi con supervisione).

## <a name="get-started"></a>Operazioni preliminari

1. Nel pannello **Funzionalità del dispositivo** scegliere **AirPlay**.
2. Nel pannello **AirPlay** scegliere una o entrambe le operazioni seguenti:

## <a name="configure-a-device-and-password-list"></a>Configurare un elenco di dispositivi e password

1. Nel pannello **Password** immettere il **Nome dispositivo** e la **Password** di un dispositivo Airplay, ad esempio **Contoso Apple TV**.
2. Dopo aver immesso le informazioni sul dispositivo, fare clic su **Aggiungi**. Il dispositivo verrà visualizzato nell'elenco **Nome dispositivo**.
3. Aggiungere tutti i dispositivi desiderati. Al termine scegliere **OK**.


## <a name="configure-allowed-destinations"></a>Configurare le destinazioni consentite

1. Nel pannello *Allowed destinations (supervised only)* (Destinazioni consentite (solo con supervisione)) immettere l'**ID dispositivo** di un dispositivo Airplay, ad esempio 52:46:CD:51:83:4C.
2. Dopo aver immesso l'ID del dispositivo, fare clic su **Aggiungi**. L'ID verrà visualizzato nell'elenco **ID dispositivo**.
3. Aggiungere tutti i dispositivi desiderati. Al termine scegliere **OK**.

È anche possibile importare il dispositivo, le password e le destinazioni consentite da un file con valori delimitati da virgole (csv).



