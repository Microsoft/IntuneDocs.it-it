---
title: Impostazioni personalizzate di Microsoft Intune per dispositivi Windows Phone 8.1
titleSuffix: 
description: "Informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Windows Phone 8.1."
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f45b2dd9cab0ccfd912d1f1348d90264bf8906b8
ms.sourcegitcommit: 4db0498342364f8a7c28995b15ce32759e920b99
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-windows-phone-81"></a>Impostazioni dei dispositivi personalizzate di Microsoft Intune per dispositivi che eseguono Windows Phone 8.1

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Usare il profilo **personalizzato** Windows Phone 8.1 di Microsoft Intune per assegnare le impostazioni URI OMA che è possibile usare per controllare le funzionalità nei dispositivi Windows Phone 8.1. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di assegnare le impostazioni non configurabili con gli altri criteri di Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Impostazioni dei criteri personalizzati per i dispositivi Windows Phone 8.1

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](custom-settings-configure.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel riquadro **Impostazioni OMA URI personalizzate** scegliere **Aggiungi** per aggiungere una o più impostazioni URI OMA.
3. Nel riquadro **Aggiungi riga** configurare i valori seguenti per ogni impostazione:
    - **Nome**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.
    - **URI OMA**: specificare l'URI OMA per cui si desidera fornire un'impostazione.
    - **Tipo di dati**: selezionare il tipo di dati in cui verrà specificata l'impostazione URI OMA. Scegliere tra **Stringa**, **Stringa (XML)**, **Data e ora**, **Intero**, **Virgola mobile**, **Booleano** o **Base64**.
    - **Valore**: immettere il valore o il file da associare all'impostazione URI OMA immessa.

4. Al termine fare clic su **OK**, quindi continuare ad aggiungere altre impostazioni secondo le esigenze.
