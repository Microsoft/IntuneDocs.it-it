---
title: Impostazioni personalizzate di Intune per dispositivi Android
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: ff3d3b1596f58213bed2509b1bfd5ae81c63f440
ms.contentlocale: it-it
ms.lasthandoff: 05/23/2017


---

# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Impostazioni personalizzate per dispositivi Android in Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Usare il profilo **Personalizzato** Android di Microsoft Intune per assegnare le impostazioni OMA-URI da usare per controllare le funzionalità nei dispositivi Android. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di assegnare le impostazioni Android non configurabili con i criteri di Intune.

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

