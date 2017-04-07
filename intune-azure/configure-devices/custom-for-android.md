---
title: Impostazioni personalizzate di Intune per dispositivi Android
titleSuffix: Intune Azure preview
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Android."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 494b3892-916e-4b40-9b67-61adec889bdf
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: d6181b24d94bb151df036241d0a8b6b987f1483d
ms.lasthandoff: 02/18/2017


---

# <a name="custom-settings-for-android-devices-in-microsoft-intune"></a>Impostazioni personalizzate per dispositivi Android in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare il profilo **Personalizzato** Android di Microsoft Intune per distribuire le impostazioni OMA-URI da usare per controllare le funzionalità nei dispositivi Android. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni Android non configurabili con i criteri di Intune.

## <a name="custom-profile-settings-for-android-devices"></a>Impostazioni del profilo personalizzate per dispositivi Android

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](how-to-configure-custom-settings.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** scegliere **Impostazioni** per aggiungere una o più impostazioni URI OMA.
3. Nel pannello **Modifica riga** configurare per ogni impostazione i valori seguenti:
    - **Nome**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.
    - **Tipo di dati**: selezionare il tipo di dati in cui verrà specificata questa impostazione URI OMA. Scegliere tra **Stringa**, **Stringa (XML)**, **Data e ora**, **Intero**, **Virgola mobile** o **Booleano**.
    - **URI OMA**: specificare l'URI OMA per cui si desidera fornire un'impostazione.
    - **Valore**: immettere il valore da associare all'impostazione URI OMA immessa.
4. Al termine fare clic su **OK**, quindi continuare ad aggiungere altre impostazioni secondo le esigenze.

