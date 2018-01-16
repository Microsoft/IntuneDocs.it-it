---
title: Impostazioni personalizzate di Intune per dispositivi Android
titleSuffix: Azure portal
description: "Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Android.\""
keywords: 
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b1ccb3b0b7b2ce024ff6a09d7f9d8366896fb67
ms.sourcegitcommit: 5004b9564915712b41860df20324f39fac3dc27d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/03/2018
---
# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Impostazioni personalizzate per dispositivi Android in Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare il profilo **Personalizzato** Android di Microsoft Intune per assegnare le impostazioni OMA-URI da usare per controllare le funzionalità nei dispositivi Android. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di assegnare le impostazioni Android seguenti che non sono configurabili con i criteri di Intune:

- [Usare un profilo di dispositivo personalizzato di Microsoft Intune per la creazione di un profilo Wi-Fi con una chiave precondivisa](/intune/wi-fi-profile-shared-key)
- [Usare un profilo personalizzato di Microsoft Intune per creare un profilo VPN per ogni app per dispositivi Android](/intune/android-pulse-secure-per-app-vpn)
- [Usare criteri personalizzati per consentire e bloccare app per dispositivi Samsung Knox Standard in Microsoft Intune](/intune/samsung-knox-apps-allow-block)

>[!IMPORTANT]
>Solo le impostazioni elencate in precedenza possono essere attualmente configurate da questo tipo di profilo. I dispositivi Android non espongono un elenco completo di impostazioni URI OMA configurabili. Se si vogliono visualizzare altre impostazioni aggiunte, richiederle sul [sito UserVoice di Intune](https://microsoftintune.uservoice.com/forums/291681-ideas).

## <a name="custom-profile-settings-for-android-devices"></a>Impostazioni del profilo personalizzate per dispositivi Android

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** scegliere **Impostazioni** per aggiungere una o più impostazioni URI OMA.
3. Nel pannello **Modifica riga** configurare per ogni impostazione i valori seguenti:
    - **Nome**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.
    - **Tipo di dati**: selezionare il tipo di dati in cui verrà specificata questa impostazione URI OMA. Scegliere tra **Stringa**, **Stringa (XML)**, **Data e ora**, **Intero**, **Virgola mobile** o **Booleano**.
    - **URI OMA**: specificare l'URI OMA per cui si desidera fornire un'impostazione.
    - **Valore**: immettere il valore da associare all'impostazione URI OMA immessa.
4. Al termine fare clic su **OK**, quindi continuare ad aggiungere altre impostazioni secondo le esigenze.

## <a name="next-steps"></a>Passaggi successivi

Dopo aver completo le impostazioni, il profilo verrà creato e visualizzato nel pannello dell'elenco dei profili. Se si desidera proseguire e assegnare il profilo ai gruppi, vedere [Come assegnare i profili di dispositivo](device-profile-assign.md).




