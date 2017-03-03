---
title: Impostazioni personalizzate di Intune per dispositivi Windows Phone 8.1 | Anteprima di Intune in Azure | Documentazione Microsoft
description: "Anteprima di Intune in Azure: informazioni sulle impostazioni che è possibile usare in un profilo personalizzato Windows Phone 8.1."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 21c55041-3821-4a62-9f85-855b97dba269
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: ab1ad9852b8f9145f405bb71cf52bfcb00e078f6
ms.lasthandoff: 02/16/2017


---

# <a name="custom-settings-for-windows-phone-81-devices-in-microsoft-intune"></a>Impostazioni personalizzate per i dispositivi Windows Phone 8.1 in Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Usare il profilo **personalizzato** Windows Phone 8.1 di Microsoft Intune per distribuire le impostazioni URI OMA che è possibile usare per controllare le funzionalità nei dispositivi Windows Phone 8.1. Si tratta di impostazioni standard che molti produttori di dispositivi mobili usano per controllare le funzionalità del dispositivo.

Questa funzionalità consente di distribuire le impostazioni non configurabili con gli altri criteri di Intune.

## <a name="custom-policy-settings-for-windows-phone-81-devices"></a>Impostazioni dei criteri personalizzati per i dispositivi Windows Phone 8.1

1. Per iniziare, usare le istruzioni riportate in [How to configure custom device settings in Microsoft Intune](how-to-configure-custom-settings.md)(Come configurare le impostazioni dei dispositivi personalizzate in Microsoft Intune).
2. Nel pannello **Crea profilo** scegliere **Impostazioni** per aggiungere una o più impostazioni URI OMA.
3. Nel pannello **Aggiungi riga** configurare per ogni impostazione i valori seguenti:
    - **Nome**: immettere un nome univoco per l'impostazione URI OMA per identificarla nell'elenco delle impostazioni.
    - **Descrizione**: fornire una descrizione che offra una panoramica dell'impostazione e altre informazioni rilevanti per individuarla.
    - **URI OMA**: specificare l'URI OMA per cui si desidera fornire un'impostazione.
    - **Tipo di dati**: selezionare il tipo di dati in cui verrà specificata questa impostazione URI OMA. Scegliere tra **Stringa**, **Data e ora**, **Intero**, **Virgola mobile** o **Booleano**.
    - **Valore**: immettere il valore da associare all'impostazione URI OMA immessa.

4. Al termine fare clic su **OK**, quindi continuare ad aggiungere altre impostazioni secondo le esigenze.

